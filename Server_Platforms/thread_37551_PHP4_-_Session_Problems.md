---
title: "PHP4 - Session Problems"
date: 2005-05-27
forum: Server Platforms
---

### Post by danielti on 2005-05-27
I installed PHP4 with apache 2 but i am having problems with sessions. Sessions are not working, session variables are always empty.
The strange thing is that in /var/lib/php4, for each session_start(); command it creates 5 files sess_* files, 4 empty and one with the real data.
The owner of the files is www_data.

Here is my php.ini, session :
[Session]
; Handler used to store/retrieve data.
session.save_handler = files

; Argument passed to save_handler.  In the case of files, this is the path
; where data files are stored. Note: Windows users have to change this 
; variable in order to use PHP's session functions.
; As of PHP 4.0.1, you can define the path as:
;     session.save_path = "N;/path"
; where N is an integer.  Instead of storing all the session files in 
; /path, what this will do is use subdirectories N-levels deep, and 
; store the session data in those directories.  This is useful if you 
; or your OS have problems with lots of files in one directory, and is 
; a more efficient layout for servers that handle lots of sessions.
; NOTE 1: PHP will not create this directory structure automatically.
;         You can use the script in the ext/session dir for that purpose.
; NOTE 2: See the section on garbage collection below if you choose to
;         use subdirectories for session storage
session.save_path = /var/lib/php4
;session.save_path = /tmp

; Whether to use cookies.
session.use_cookies = 1

; This option enables administrators to make their users invulnerable to
; attacks which involve passing session ids in URLs; defaults to 0.
session.use_only_cookies = 0

; Name of the session (used as cookie name).
session.name = PHPSESSID

; Initialize session on request startup.
session.auto_start = 1

; Lifetime in seconds of cookie or, if 0, until browser is restarted.
session.cookie_lifetime = 0

; The path for which the cookie is valid.
session.cookie_path = /tmp

; The domain for which the cookie is valid.
session.cookie_domain = 

; Handler used to serialize data.  php is the standard serializer of PHP.
session.serialize_handler = php

; Define the probability that the 'garbage collection' process is started
; on every session initialization.
; The probability is calculated by using gc_probability/gc_divisor,
; e.g. 1/100 means there is a 1% chance that the GC process starts
; on each request.

; This is disabled in the Debian packages, due to the strict permissions
; on /var/lib/php4.  Instead of setting this here, see the cronjob at
; /etc/cron.d/php4, which uses the session.gc_maxlifetime setting below
;session.gc_probability = 0
session.gc_divisor     = 100

; After this number of seconds, stored data will be seen as 'garbage' and
; cleaned up by the garbage collection process.
session.gc_maxlifetime = 1440

; NOTE: If you are using the subdirectory option for storing session files
;       (see session.save_path above), then garbage collection does *not*
;       happen automatically.  You will need to do your own garbage 
;       collection through a shell script, cron entry, or some other method. 
;       For example, the following script would is the equivalent of
;       setting session.gc_maxlifetime to 1440 (1440 seconds = 24 minutes):
;          cd /path/to/sessions; find -cmin +24 | xargs rm

; PHP 4.2 and less have an undocumented feature/bug that allows you to
; to initialize a session variable in the global scope, albeit register_globals
; is disabled.  PHP 4.3 and later will warn you, if this feature is used.
; You can disable the feature and the warning separately. At this time,
; the warning is only displayed, if bug_compat_42 is enabled.

session.bug_compat_42 = 1
session.bug_compat_warn = 1

; Check HTTP Referer to invalidate externally stored URLs containing ids.
; HTTP_REFERER has to contain this substring for the session to be
; considered as valid.
session.referer_check =

; How many bytes to read from the file.
session.entropy_length = 0

; Specified here to create the session id.
session.entropy_file =

;session.entropy_length = 16

;session.entropy_file = /dev/urandom

; Set to {nocache,private,public,} to determine HTTP caching aspects
; or leave this empty to avoid sending anti-caching headers.
session.cache_limiter = nocache

; Document expires after n minutes.
session.cache_expire = 180

; trans sid support is disabled by default.
; Use of trans sid may risk your users security. 
; Use this option with caution.
; - User may send URL contains active session ID
;   to other person via. email/irc/etc.
; - URL that contains active session ID may be stored
;   in publically accessible computer.
; - User may access your site with the same session ID
;   always using URL stored in browser's history or bookmarks.
session.use_trans_sid = 0

; The URL rewriter will look for URLs in a defined set of HTML tags.
; form/fieldset are special; if you include them here, the rewriter will
; add a hidden <input> field with the info which is otherwise appended
; to URLs.  If you want XHTML conformity, remove the form entry.
; Note that all valid entries require a "=", even if no value follows.
url_rewriter.tags = "a=href,area=href,frame=src,input=src,form=,fieldset="

Please I really need it to work !
Thanks !

---

### Post by jdodson on 2005-05-27
you 

```
session_start();
``` 

starting each page right?  because you are supposed to do that.

so you one page one would do:


```


session_start();

$_SESSION['dasVar'] = "whiggidy whack";

``` 

on the second page you would do:


```


session_start();

print $_SESSION['dasVar'];

``` 

which would display "whiggidy whack"

you are doing something similar?

---

