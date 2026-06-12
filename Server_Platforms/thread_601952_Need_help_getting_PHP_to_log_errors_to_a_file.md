---
title: "Need help getting PHP to log errors to a file"
date: 2007-11-03
forum: Server Platforms
---

### Post by eqqfooyoung on 2007-11-03
This is the first web server I am setting up and I'm having a hard time getting PHP to log errors to a file instead of displaying them on the page.  Below are my php.ini settings:

```
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
; Error handling and logging ;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

; error_reporting is a bit-field.  Or each number up to get desired error
; reporting level
; E_ALL             - All errors and warnings (doesn't include E_STRICT)
; E_ERROR           - fatal run-time errors
; E_RECOVERABLE_ERROR  - almost fatal run-time errors
; E_WARNING         - run-time warnings (non-fatal errors)
; E_PARSE           - compile-time parse errors
; E_NOTICE          - run-time notices (these are warnings which often result
;                     from a bug in your code, but it's possible that it was
;                     intentional (e.g., using an uninitialized variable and
;                     relying on the fact it's automatically initialized to an
;                     empty string)
; E_STRICT          - run-time notices, enable to have PHP suggest changes
;                     to your code which will ensure the best interoperability
;                     and forward compatibility of your code
; E_CORE_ERROR      - fatal errors that occur during PHP's initial startup
; E_CORE_WARNING    - warnings (non-fatal errors) that occur during PHP's
;                     initial startup
; E_COMPILE_ERROR   - fatal compile-time errors
; E_COMPILE_WARNING - compile-time warnings (non-fatal errors)
; E_USER_ERROR      - user-generated error message
; E_USER_WARNING    - user-generated warning message
; E_USER_NOTICE     - user-generated notice message
;
; Examples:
;
;   - Show all errors, except for notices and coding standards warnings
;
;error_reporting = E_ALL & ~E_NOTICE
;
;   - Show all errors, except for notices
;
;error_reporting = E_ALL & ~E_NOTICE | E_STRICT
;
;   - Show only errors
;
;error_reporting = E_COMPILE_ERROR|E_RECOVERABLE_ERROR|E_ERROR|E_CORE_ERROR
;
;   - Show all errors except for notices and coding standards warnings
;
error_reporting  =  E_ALL
; Print out errors (as a part of the output).  For production web sites,
; you're strongly encouraged to turn this feature off, and use error logging
; instead (see below).  Keeping display_errors enabled on a production web site
; may reveal security information to end users, such as file paths on your Web
; server, your database schema or other information.
display_errors = On

; Even when display_errors is on, errors that occur during PHP's startup
; sequence are not displayed.  It's strongly recommended to keep
; display_startup_errors off, except for when debugging.
display_startup_errors = Off

; Log errors into a log file (server-specific log, stderr, or error_log (below))
; As stated above, you're strongly advised to use error logging in place of
; error displaying on production web sites.
log_errors = On

; Set maximum length of log_errors. In error_log information about the source is
; added. The default is 1024 and 0 allows to not apply any maximum length at all.
log_errors_max_len = 1024

; Do not log repeated messages. Repeated errors must occur in same file on same
; line until ignore_repeated_source is set true.
ignore_repeated_errors = Off

; Ignore source of message when ignoring repeated messages. When this setting
; is On you will not log errors with repeated messages from different files or
; source lines.
ignore_repeated_source = Off

; If this parameter is set to Off, then memory leaks will not be shown (on
; stdout or in the log). This has only effect in a debug compile, and if
; error reporting includes E_WARNING in the allowed list
report_memleaks = On

;report_zend_debug = 0

; Store the last error/warning message in $php_errormsg (boolean).
track_errors = Off

; Disable the inclusion of HTML tags in error messages.
; Note: Never use this feature for production boxes.
;html_errors = Off

; If html_errors is set On PHP produces clickable error messages that direct
; to a page describing the error or function causing the error in detail.
; You can download a copy of the PHP manual from http://www.php.net/docs.php
; and change docref_root to the base URL of your local copy including the
; leading '/'. You must also specify the file extension being used including
; the dot.
; Note: Never use this feature for production boxes.
;docref_root = "/phpmanual/"
;docref_ext = .html

; String to output before an error message.
;error_prepend_string = "<font color=ff0000>"

; String to output after an error message.
;error_append_string = "</font>"

; Log errors to specified file.
error_log = /home/eqqfooyoung/WebDevelopment/phpErrorLog.log

; Log errors to syslog (Event Log on NT, not valid in Windows 95).
;error_log = syslog
```

I have created an empty file in /home/eqqfooyoung/WebDevelopment/phpErrorLog.log, but it still will not write to the file when I have errors in my code.  

Anyone see what I am doing wrong?

---

### Post by Jasper91 on 2007-11-03
I'm not surtend but maybe you'll have to replace 'error_log = /home/eqqfooyoung/WebDevelopment/phpErrorLog.log' by 'error_log = "/home/eqqfooyoung/WebDevelopment/phpErrorLog.log"'

---

### Post by eqqfooyoung on 2007-11-04
I changed:

error_log = /home/eqqfooyoung/WebDevelopment/phpErrorLog.log

 to:

error_log = "/home/eqqfooyoung/WebDevelopment/phpErrorLog.log"

rebooted, tested, but there was still no change.

---

### Post by eqqfooyoung on 2007-11-04
I just got it working.  I left the quotes in like Jasper recommended and I changed the permissions on my error log file so that others can read and write to it.

[LIST=1]
[*]right clicked the file
[*]selected properties
[*]under the others section, I changed access to read and write
[/LIST]

---

