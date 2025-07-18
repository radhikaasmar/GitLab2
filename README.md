# GitLab2
Hello!
This is lab 2 exercise.
I am making an edit.






JIL File Generator – Project Documentation
Overview
JIL File Generator is a dynamic form-based Angular application designed to help users create JIL (Job Information Language) files for scheduling jobs. The system is modular, allowing users to build complex job configurations using reusable subforms and a question bank.

Main Features
Dynamic Form Rendering: Forms are generated from JSON templates and a question bank, supporting various field types (text, dropdown, checkbox-group, environments-group, conditions-array, etc.).
Subform Architecture: The main form consists of multiple subforms (e.g., top, box, cmd, fw, cfw), each with its own configuration and fields.
Environment-Specific Fields: Users select environments (DEV, PROD, UAT, COB), and only relevant fields for those environments are shown in subforms.
Conditional Logic: Fields like days_of_week and run_calendar are shown/hidden based on the selected frequency.
Repeatable Groups: Supports repeatable sections (e.g., conditions) using FormArray.
Validation: Validators are defined in JSON and mapped to Angular validators.
Function-Job Mapping: Job types and functions are managed via a JSON mapping file for easy editing.
Read-Only Logic: Certain fields are editable only in the top subform; in other subforms, they are read-only.
Folder Structure
Key Files
question-bank.json: Defines all possible questions/fields.
box-subform.json, fw-subform.json, etc.: Define subform templates by listing question IDs for each section.
function-job-mapping.json: Maps job functions to job types and subform types.
dynamic-form-builder.service.ts: Builds Angular forms from JSON templates.
dynamic-form-viewer.component.ts/html: Renders the dynamic form UI.
dynamic-form-page.component.ts/html: Main page logic, manages subforms and navigation.
How It Works
Form Generation:

The main form is built from subform templates and the question bank.
Each subform is a FormGroup; repeatable sections use FormArray.
Subform Management:

Top subform is always present and editable.
Additional subforms (box, cmd, fw, cfw) can be added via UI (checkboxes/buttons).
"Insert Job Configuration" fields are read-only in subforms except the top.
Environment Logic:

User selects environments in the top subform.
Only environment-specific fields for selected environments are shown in other subforms.
Conditional Fields:

Frequency dropdown controls visibility of days_of_week and run_calendar fields.
Changing frequency clears the value of the hidden field.
Function-Job Mapping:

Job functions and types are loaded from function-job-mapping.json via a service.
This allows easy updates without code changes.
Validation:

Validators are defined in JSON and applied during form building.
Validation errors are shown in the UI.
How to Add/Edit Questions or Subforms
To add a new question:
Edit question-bank.json and add your question definition.
To add/edit a subform:
Edit the relevant subform template JSON (e.g., box-subform.json) and update the questionIds array.
To update job function mappings:
Edit function-job-mapping.json.
How to Make Fields Read-Only in Subforms
In the dynamic form viewer template, use [readonly] or [disabled] bindings for fields.
In the viewer component, implement a method to check if the current subform is not the top subform and return true for those fields.
How to Show/Hide Fields Based on Frequency
Subscribe to the frequency control’s value changes in your component.
Use *ngIf in the template to conditionally show days_of_week or run_calendar.
Clear the value of the hidden field when frequency changes.
How to Run the Project
Install dependencies:
Start the frontend:
Access the app at http://localhost:4200
Extending the Project
Add new field types by updating the question bank and renderer logic.
Add new subform types by creating new subform templates.
Update job function mappings in the JSON file.
Support
For questions or issues, please contact the project maintainer or open an issue in your repository.


---------non tech intro-----------
What is the JIL File Generator?
The JIL File Generator is a tool that helps you create special files (called JIL files) for scheduling jobs. You use a form on the website to fill in details about your jobs, and the tool builds the file for you automatically.

How Does It Work?
Step 1: Fill Out the Form

The website shows you a form with different sections and questions.
Some questions are always shown, and some appear only if you choose certain options (for example, if you pick "Monthly" as the frequency, you’ll see a calendar field).
Step 2: Add Job Sections

The form is divided into smaller parts called “subforms.” The main part is always there, and you can add more sections if your job needs them.
You can also choose which environments (like DEV, PROD, UAT) your job will run in. The form will show only the questions that matter for the environments you pick.
Step 3: Some Fields Are Read-Only

In most sections, some fields (like job type or function) are filled in for you and you can’t change them. Only the main section lets you edit these.
Step 4: Smart Form Behavior

The form changes based on your answers. For example:
If you pick “Daily” or “Weekly,” you’ll be asked which days of the week.
If you pick “Monthly” or “Custom,” you’ll be asked for a calendar name.
Step 5: Save and Download

When you finish, you can save your answers and download the JIL file that the tool creates for you.
Why Is This Useful?
You don’t need to know how to write JIL files yourself.
The tool makes sure you fill in all the right details.
It saves you time and helps avoid mistakes.
How Can You Change the Questions or Options?
The questions and options in the form are stored in files that can be edited easily.
If you want to add a new question or change an option, you just update the file—no need to change the code.
Who Can Use This?
Anyone who needs to create JIL files for job scheduling—no technical knowledge required!
