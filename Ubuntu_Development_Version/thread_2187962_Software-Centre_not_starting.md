---
title: "Software-Centre not starting"
date: 2013-11-14
forum: Ubuntu Development Version
---

### Post by Hazzabin on 2013-11-14
The 'Ubuntu Software Centre' will not stay open in "Trusty" 

any ideas how to fix this issue

regards
Hazz

---

### Post by cariboo on 2013-11-14
> **Hazzabin said:**
> The 'Ubuntu Software Centre' will not stay open in "Trusty" 

any ideas how to fix this issue

regards
Hazz

Use synaptic :-)

Start the software centre from a terminal, to see what if any error messages you are getting.

```
software-center
```

---

### Post by Hazzabin on 2013-11-14
g'day [COLOR=#000000]cariboo907

this is what came up

"[/COLOR]2013-11-15 09:39:40,100 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'2013-11-15 09:39:40,100 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2013-11-15 09:39:40,183 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()


(software-center:2463): Gdk-ERROR **: The program 'software-center' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
  (Details: serial 2150 error_code 9 request_code 62 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Trace/breakpoint trap"

---

### Post by cariboo on 2013-11-14
Moved to a thread of it's own, as it really isn't that common a problem.

Are you getting any crash reports in /var/crash?

---

### Post by Hazzabin on 2013-11-14
Nope, tho I am getting a 'System Problem' pop-up from time to time after clicking send report it goes away

---

### Post by mc4man on 2013-11-14
More than likely this bug
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1211887](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1211887)

Edit:
if you wanted to use S-c then do this way
Start from terminal on an app, Ex.

software-center gedit

After it opens click on little  arrow to the right of "All Software" icon, from the dropdown pick anything, "Provided by Ubuntu" will do.
After that opens then, if desired, you can click on the "All Software" icon to go to the main page.

---

### Post by Hazzabin on 2013-11-15
> **mc4man said:**
> More than likely this bug
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1211887](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1211887)

Edit:
if you wanted to use S-c then do this way
Start from terminal on an app, Ex.

software-center gedit

After it opens click on little  arrow to the right of "All Software" icon, from the dropdown pick anything, "Provided by Ubuntu" will do.
After that opens then, if desired, you can click on the "All Software" icon to go to the main page.

Sorry to say that didn't work either,S-C shuts down same

Anyway guys thanks for trying to help, I'll live without it for a while

---

### Post by ortermagic on 2013-11-21
I am getting the same problem: where the software center flashes on, then disappears > (software-center:5802): Gdk-ERROR **: The program 'software-center' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
  (Details: serial 2634 error_code 9 request_code 62 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Trace/breakpoint trap (core dumped)
  
So i guess it's not that unusual, I upgraded one of my distros two days ago 12.10-14.04 trusty (I can use synaptic)

---

### Post by ortermagic on 2013-11-21
sorry, this is the full printout ```
ortermagic@russet:~$ software-center
2013-11-21 16:16:26,386 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-11-21 16:16:27,122 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-11-21 16:16:27,127 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2013-11-21 16:16:27,137 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2013-11-21 16:16:27,137 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2013-11-21 16:16:27,184 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2013-11-21 16:16:27,565 - softwarecenter.backend.reviews - WARNING - error creating bsddb: '(22, 'Invalid argument -- BDB0054 illegal flag combination specified to DB_ENV->open')' (corrupted?)
2013-11-21 16:16:27,565 - softwarecenter.backend.reviews - ERROR - trying to repair DB failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 358, in _save_review_stats_cache_blocking
    self._dump_bsddbm_for_unity(outfile, outdir)
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 377, in _dump_bsddbm_for_unity
    0600)
DBInvalidArgError: (22, 'Invalid argument -- BDB0054 illegal flag combination specified to DB_ENV->open')

(software-center:6670): Gdk-ERROR **: The program 'software-center' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
  (Details: serial 2630 error_code 9 request_code 62 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Trace/breakpoint trap (core dumped)
ortermagic@russet:~$ 


```It all seems illogical since the command (software-center) throws up a working software centre, whereas the unity desktop icon throws up software centre for barely two seconds before disappearing

---

