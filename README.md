# 📊 Intune App Assignments & Relations Report

Welcome to the **Intune App Assignments & Relations Report** project! This PowerShell script generates two comprehensive HTML reports from your Microsoft Intune environment:

- **App Assignments Report**: See all Entra ID group assignments for Intune apps, with advanced filtering and impact analysis.
- **Application Relationships Report**: Visualize app supersedence and dependencies, including automatic detection of problematic detection rules in superseded apps.

---

## 📦 PowerShell Module Requirements

Before running the script, ensure you have the following PowerShell modules installed:

- `Microsoft.Graph.Authentication`
- `Microsoft.Graph.Groups`
- `Microsoft.Graph.Beta.Devices.CorporateManagement`

Install all required modules with:
```powershell
Install-Module Microsoft.Graph.Authentication -Scope CurrentUser
Install-Module Microsoft.Graph.Groups -Scope CurrentUser
Install-Module Microsoft.Graph.Beta.Devices.CorporateManagement -Scope CurrentUser
Install-Module Microsoft.Graph.Beta.DeviceManagement -Scope CurrentUser
```

> **Note:** You may need to update modules if you have older versions installed. Administrator rights may be required for system-wide installation.

---

## 🚀 Features

- **Unified view of app assignments**: See which Entra ID groups are assigned to each app, and vice versa.
- **Impact analysis**: View device and user counts for assignment groups.
- **Advanced filtering & search**: Filter by OS, app type, assignment group, and more. Free text search included.
- **Interactive HTML report**: Sort by any column, hover for details, and access direct links to Intune objects.
- **Export options**: Save results as CSV, JSON, or copy-paste to Excel.
- **Offline cache support**: Generate reports from cached data for faster results.
- **Customizable output**: Choose to include IDs, base64 images, or exclude app icons.
- **Application Relationships Report**: Visualize app supersedence and dependencies, with:
  - Automatic detection of problematic detection rules in superseded apps (shows if old and new app versions could be detected at the same time, which can cause issues for Intune Management Extension Agent).
  - Easy identification of update chains and dependency issues.

---

## 📦 Installation

- **Install the required PowerShell modules** (see above).

1. **Download the script:** [Click here](https://github.com/petripaavola/Get-IntuneAppAssignmentsAndRelationsReport/blob/main/Get-IntuneAppAssignmentsAndRelationsReport.ps1)

## 📝 Usage

Run the script to generate both reports:
```powershell
./Get-IntuneAppAssignmentsAndRelationsReport.ps1
```

This will create two HTML files in the current directory:
- `Intune_Application_Assignments_report.html` (App Assignments)
- `Intune_Application_Relationship_report.html` (Supersedence & Dependency)

### Microsoft Graph API Permissions

The script will prompt you to authenticate with Microsoft Graph and requires the following delegated permissions:

- `DeviceManagementApps.Read.All`
- `Group.Read.All`
- `Directory.Read.All`

Ensure your account has sufficient rights in your tenant to access Intune and Entra ID group data.

### Optional Parameters

| Parameter                        | Description                                                                                   |
|----------------------------------|-----------------------------------------------------------------------------------------------|
| `-ExportCSV`                     | Export report as a CSV file.                                                                  |
| `-ExportJSON`                    | Export report as a JSON file.                                                                 |
| `-ExportToExcelCopyPaste`        | Export report to clipboard for easy pasting into Excel.                                       |
| `-UseOfflineCache`               | Use cached data for report generation.                                                        |
| `-DoNotOpenReportAutomatically`  | Prevent automatic opening of the HTML report.                                                 |
| `-UpdateIconsCache`              | Update the app icon cache.                                                                    |
| `-IncludeAppsWithoutAssignments` | Include apps without assignments in the report.                                               |
| `-DoNotDownloadAppIcons`         | Skip downloading application icons.                                                           |
| `-IncludeIdsInReport`            | Include application IDs in the report.                                                        |
| `-IncludeBase64ImagesInReport`   | Embed app icons as base64 images in the HTML file.                                            |

### Example Commands
```powershell
./Get-IntuneAppAssignmentsAndRelationsReport.ps1 -ExportCSV -ExportJSON
./Get-IntuneAppAssignmentsAndRelationsReport.ps1 -UseOfflineCache
./Get-IntuneAppAssignmentsAndRelationsReport.ps1 -IncludeAppsWithoutAssignments
```

---

## 📷 Screenshots

![Report Overview](https://github.com/petripaavola/Intune/blob/master/Reports/pics/IntuneApplicationAssignmentReport.png)
![Apps Assigned to EntraID Group](https://github.com/petripaavola/Intune/blob/master/Reports/pics/IntuneApplicationAssignmentReportSortByAssignmentGroup.png)

---

## ❓ FAQ & Support

- **Why use this script?**
  - Intune UI does not provide a consolidated view of app assignments, relationships, or detection rule issues. These reports save time and effort.
- **Need help or want to contribute?**
  - Open an issue or pull request on GitHub!

---

## 🏷️ License

This project is licensed under the MIT License.

---

## 👤 Author

Created by [Petri Paavola](https://github.com/petripaavola)

---

Enjoy better visibility into your Intune app assignments and relationships! ✨
