---
title: "Error &quot;Could not load PEM file&quot; (Anki)"
date: 2023-06-12
forum: Security
---

### Post by s1990 on 2023-06-12
Hi all,
I have some problem with a security file while syncing my learning cards with Anki. Since upgrading to Ubuntu 22 I can no longer sync my decks. I installed  the latest version (2.1.64) of Anki. The program itself is working perfectly.  But as soon as I try to log in with my credentials, it crashes. It has  nothing to do with my credentials, because I also tried it with random  entries, which resulted in the same error messages. 
After further investigation in the Anki forum ([https://forums.ankiweb.net/t/sync-error-could-not-load-pem-file/30907](https://forums.ankiweb.net/t/sync-error-could-not-load-pem-file/30907)), I found out that this error has nothing to do with Anki itself. There is a problem with a security certificate "InvalidData, error: “Could not load PEM file  "/usr/lib/ssl/certs/ca-certificates.crt". Although the path/file /usr/lib/ssl/certs/ca-certificates.crt is present
Hopefully you can help me with that error. I also included the error log of Anki below.
Thank you in advance.

 [HR][/HR] Anki starting…
Initial setup…
Running with temporary Qt5 compatibility shims.
Run with DISABLE_QT5_COMPAT=1 to confirm compatibility with Qt6.
Preparing to run…
Qt warning: Could not connect “org.freedesktop.IBus” to globalEngineChanged(QString)
Starting main loop…
mpv not found, reverting to mplayer
thread ‘’ panicked at ‘called Result::unwrap() on an Err  value: reqwest::Error { kind: Builder, source: Custom { kind:  InvalidData, error: “Could not load PEM file  "/usr/lib/ssl/certs/ca-certificates.crt"” } }’,  rslib/src/sync/http_client/mod.rs:44:60
note: run with RUST_BACKTRACE=1 environment variable to display a backtrace
Caught exception:
Traceback (most recent call last):
File “aqt.taskman”, line 122, in _on_closures_pending
File “aqt.taskman”, line 71, in 
File “aqt.taskman”, line 90, in wrapped_done
File “aqt.sync”, line 269, in on_future_done
File “concurrent.futures._base”, line 439, in result
File “concurrent.futures._base”, line 391, in __get_result
File “concurrent.futures.thread”, line 58, in run
File “aqt.sync”, line 287, in 
File “anki.collection”, line 1247, in sync_login
File “anki._backend_generated”, line 763, in sync_login
File “anki._backend”, line 150, in _run_command
pyo3_runtime.PanicException: called Result::unwrap() on an Err  value: reqwest::Error { kind: Builder, source: Custom { kind:  InvalidData, error: “Could not load PEM file  "/usr/lib/ssl/certs/ca-certificates.crt"” } }

 Error in atexit._run_exitfuncs:
Error in atexit._run_exitfuncs:
Traceback (most recent call last):
 [HR][/HR]

---

