# E-Pasien SIMKES Khanza - Agent Guidance

## Project Overview
- PHP web application for hospital patient management system (E-Pasien)
- Uses MySQL database with default credentials: localhost/root/(empty)/sik
- XAMPP environment with Asia/Jakarta timezone
- Frontend uses jQuery, Bootstrap, CKEditor, TinyMCE plugins
- Database schema in `sik.sql`

## Key Architecture Notes
- Entry point: `index.php` routes to `indexpengunjung.php` (public) or `indexuser.php` (authenticated)
- Configuration in `conf/command.php` (routing) and `conf/conf.php` (database/security)
- Session-based authentication with patient/user distinction
- Extensive input sanitization functions in `conf.php` (validTeks, antisqlinjection)
- Action-based routing via `?act=` parameter in URLs

## Development Commands
- Start XAMPP Apache and MySQL services
- Import database: `mysql -u root < sik.sql`
- Default web access: `http://localhost/epasien/`
- No build process - direct PHP execution

## Testing & Verification
- Test login flow: public vs authenticated sessions
- Check database connectivity with default credentials
- Verify input sanitization prevents SQL injection
- Test major patient flows: registration, billing, lab results

## Security & Constraints
- Input validation aggressively strips special characters
- Session protection for patient-only pages (see `formProtek()` in command.php)
- Wearable integration files present: `wearable.apk`, `wearable.shortcut`
- No dependency management (Composer/npm) - libraries in `plugins/`

## Common Issues
- Database connection fails if MySQL not running on localhost:3306
- Session handling depends on proper cookie settings
- File uploads may need XAMPP PHP config adjustments
- Indonesian language and date formats throughout