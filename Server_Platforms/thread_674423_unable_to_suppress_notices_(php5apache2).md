---
title: "unable to suppress notices (php5/apache2)"
date: 2008-01-21
forum: Server Platforms
---

### Post by blun7 on 2008-01-21
In my other experience changing the error reporting level in php.ini does the trick but I've been unable to suppress notices such as this: 

Notice: Undefined index: paths in /home...

This is caused by referencing an array index that does not yet exist. This is common and is not something I want to see.

I edited /etc/php5/apache2/php.ini and set

error_reporting = E_ALL & ~E_NOTICE & ~E_USER_NOTICE

and restarted apache but this does not suppress the notices! It does in other configurations I've used.

The only way I can suppress the notices is by turning display_errors to off but I do want some errors.

:confused:

---

### Post by gnaunited on 2008-01-21
Shouldn't it read something like E_ALL ^ E_NOTICE?

---

### Post by gnaunited on 2008-01-21
Nevermind, that only works inside of a PHP script.

Try restarting Apache so it will reload the conf file.

---

### Post by blun7 on 2008-01-21
> **gnaunited said:**
> Shouldn't it read something like E_ALL ^ E_NOTICE?

I'm not sure when, but the syntax has changed. From my php.ini files
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

```

---

### Post by gnaunited on 2008-01-21
Did you reload apache?

---

### Post by blun7 on 2008-01-21
> **gnaunited said:**
> Did you reload apache?

Yes.

---

### Post by gnaunited on 2008-01-21
Did you try phpinfo(); and see what it says?

---

### Post by conjur3r on 2008-01-22
Edit. Read your post, wrong advice given

---

### Post by blun7 on 2008-01-22
The software I'm trying to use was not meant to be used with php5, it turns out. It seems like the error reporting levels are being overridden at various points. I wish there was a php4 package in the repositories!

---

### Post by deuce868 on 2008-01-22
No point having a php4 package in the repositories at this point:

[http://www.php.net/index.php#2007-07-13-1](http://www.php.net/index.php#2007-07-13-1)

---

