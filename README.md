# Field Attendance App (v3.1.0)

One Android app, one central backend, many companies. Roles: company **Admin**, **Manager**, **Employee**, and the app **Owner**.

* Each company registers inside the app (company details + password). No Google account or sign-in is needed by customers. Each company gets its own sheet and photo folder, kept separate, in the product owner's Google account.
* Employees sign in with Company ID + Employee ID + PIN. Check-in = front-camera photo + GPS (GPS starts while the camera is open). Check-out = GPS only.
* Admin: dashboard, employee/manager management inside the app, Location & Photos with filters, monthly Excel reports, company and subscription details.
* Manager: sees only assigned employees. Owner: companies, status, plan, expiry, employee limit.

## Folders
| Folder | What |
|---|---|
| `apps-script/Code.gs` | Central backend (paste into Apps Script once - see SETUP.md) |
| `www/` | The app (HTML/JS). `excel.js` builds the Excel reports |
| `tests/` | `npm test` - 29 automated tests against simulated Google services and a simulated phone |
| `.github/workflows/build-apk.yml` | Builds the APK (and optionally the Play Store .aab) |

## Run the tests
`npm ci && npm test`

## What the tests do and do NOT prove
They run the real backend code against fake SpreadsheetApp / DriveApp services (which also imitate Sheets' automatic conversion of dates, numbers and formulas) and the real app in a fake phone. They prove our logic: registration, roles, company isolation, licence rules, duplicate protection, reports and the Excel files. They do NOT prove that real Google accepts every call exactly as the fake does, nor camera/GPS on a real phone. First real-world run is the true test - follow SETUP.md section C.

## Not built yet (planned next)
Offline queue (Pending/Synced/Failed), public-holiday calendar, Excel import of employees, data-retention tools, owner-side "register company on behalf of customer".
