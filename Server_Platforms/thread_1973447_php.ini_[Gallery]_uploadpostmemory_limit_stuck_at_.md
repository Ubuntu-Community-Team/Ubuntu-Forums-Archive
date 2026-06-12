---
title: "php.ini [Gallery] upload/post/memory limit stuck at 8mb ??"
date: 2012-05-04
forum: Server Platforms
---

### Post by gypsumwolf on 2012-05-04
I have Ubuntu Server installed and gallery 3.3 and drupal 7.x.

I changed the php.ini in /etc/php5/apache2/php.ini AND /etc/php5/cli/php.ini to allow 32MB, but Gallery says there is an 8MB file size limit.

Yes, I did restart apache.

Snip from php.ini
```

;;;;;;;;;;;;;;;;;;;
; Resource Limits ;
;;;;;;;;;;;;;;;;;;;

; Maximum execution time of each script, in seconds
; http://php.net/max-execution-time
; Note: This directive is hardcoded to 0 for the CLI SAPI
max_execution_time = 30

; Maximum amount of time each script may spend parsing request data. It's a good
; idea to limit this time on productions servers in order to eliminate unexpectedly
; long running scripts.
; Note: This directive is hardcoded to -1 for the CLI SAPI
; Default Value: -1 (Unlimited)
; Development Value: 60 (60 seconds)
; Production Value: 60 (60 seconds)
; http://php.net/max-input-time
max_input_time = 60

; Maximum input variable nesting level
; http://php.net/max-input-nesting-level
;max_input_nesting_level = 64

; How many GET/POST/COOKIE input variables may be accepted
; max_input_vars = 1000

; Maximum amount of memory a script may consume (128MB)
; http://php.net/memory-limit
memory_limit = 32M

```

snip of post_max_size from php.ini
```

; Maximum size of POST data that PHP will accept.
; http://php.net/post-max-size
post_max_size = 32M

```

Snip File uploads from php.ini
```

;;;;;;;;;;;;;;;;
; File Uploads ;
;;;;;;;;;;;;;;;;

; Whether to allow HTTP file uploads.
; http://php.net/file-uploads
file_uploads = On

; Temporary directory for HTTP uploaded files (will use system default if not
; specified).
; http://php.net/upload-tmp-dir
;upload_tmp_dir =

; Maximum allowed size for uploaded files.
; http://php.net/upload-max-filesize
upload_max_filesize = 32M

; Maximum number of files that can be uploaded via a single request
max_file_uploads = 25

```

---

