# Automated ADF Pipeline JAR Update

## Overview
This project automates the process of updating JAR files in Azure Data Factory (ADF) pipelines. Previously, updating JAR files involved manual steps such as creating a branch, modifying pipeline configurations, committing changes, and creating a pull request. This solution automates the entire process, reducing manual effort and ensuring consistency across environments.

## Features
- **Automated Branch Creation**: Creates a new branch for pipeline modifications.
- **Pipeline JSON Modification**: Updates the JAR reference in the ADF pipeline JSON.
- **Git Integration**: Fetches the latest repository data and pushes changes.
- **Pull Request Creation**: Automatically generates a PR for review and merging.

## Tech Stack
- **Azure DevOps API**: Used for repository management, branch creation, and PR handling.
- **Python**: Primary language for scripting automation.
- **Databricks**: Executes the automation within a notebook.

## Technical Details
- **Fetching JAR Version**: The script retrieves the latest JAR file version from a predefined storage location or API.
- **Validating Changes**: Before updating, the script checks if the JAR version has changed compared to the existing pipeline configuration.
- **Managing Git Changes**:
  - Fetches the latest repo state.
  - Creates a new branch if it does not exist; otherwise, updates an existing one.
  - Modifies only the relevant JSON file without affecting other configurations.
  - Pushes changes while ensuring conflicts are handled.
- **Pull Request Handling**:
  - Automatically creates a PR from the new branch to the main branch.
  - Fetches the direct PR URL for easy access.
- **Branch Management**:
  - Checks for existing branches to prevent redundant branch creation.
  - Cleans up stale branches where necessary.
- **Utility Functions**:
  - JSON parsing and validation.
  - Error handling for API failures.
  - Logging mechanisms for debugging and monitoring.

## Workflow
1. **Fetch Latest Repository Data**: Retrieves the latest JSON pipeline files from the Azure DevOps repository.
2. **Modify Pipeline JSON**: Updates only the required JAR reference while maintaining the existing structure.
3. **Create a New Branch**: A dedicated branch is created for tracking the changes.
4. **Push Changes**: The modified pipeline JSON is committed and pushed to the new branch.
5. **Create a Pull Request**: A PR is generated, linking the branch to the main repository for review.
6. **Future Integration**: The process will be added to the CD pipeline for seamless updates across environments.


## Impact
This automation streamlines ADF pipeline updates, reducing manual effort and the risk of human errors while ensuring consistency across environments. It improves efficiency and aligns with DevOps best practices.
