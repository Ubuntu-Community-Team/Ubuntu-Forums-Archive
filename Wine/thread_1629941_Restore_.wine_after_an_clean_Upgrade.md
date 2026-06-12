---
title: "Restore .wine after an clean Upgrade"
date: 2010-11-24
forum: Wine
---

### Post by MSwal2846 on 2010-11-24
I am currently running ubuntu 10.04 and have been playing with going to 10.10.  I've never trusted the upgrade process and utilize a new HD, install from scratch the new ubuntu, then restore my settings, etc from backups of my /home directory.  This has worked pretty well for me in the past.  This technique also allows me to try some new things and test stuff out without risk (I simply put the original HD back in my notebook and off I go).  Also, in the past, I've gotten all of my windoze apps to work in CrossOver and can simply archive and restore those bottles.

The difference this time is that I've got a "mission critical" ms application that I couldn't get to work under CrossOver but works pretty well under wine.  The trouble it that it took alot of effort to get it to work under wine and I now have no clue all of the steps that would be required to recreate this environment in a new install.

I thought that once I'd installed the new Ubuntu, installed wine, ran wine, replace the ".wine" just created with a backed up copy of ".wine" that I would be good.  WRONG!

How would I go about doing this?

---

### Post by bobwyajnr on 2010-11-24
> **MSwal2846 said:**
> 
I thought that once I'd installed the new Ubuntu, installed wine, ran wine, replace the ".wine" just created with a backed up copy of ".wine" that I would be good.  WRONG!

How would I go about doing this?

If you are not using a Wine prefix for the MS application then all the main application data is stored in the *~/.wine/* folder. Some applications will create folders in the equivalent of **My Documents** - which would be your home (~) folder - which you said you backed up anyway (and usually contains nothing too important anyway).

Have you perchance changed the version of Wine you are using?

I can only speculate that **maybe** the application you are running has stale path entries or something similar. I would check the virtual registry (and perhaps .ini/.xml configuration files).

You are a bit vague about the errors or actual problem you are experiencing! A bit more description or some good 'ole console output would certainly help... :popcorn:

Bob

---

### Post by MSwal2846 on 2010-11-25
Hi Bob,

Well, when I run the following and get these results:

```
mswallow-> winecfg
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
Warning: could not find DOS drive for current working directory '/home/mswallow', starting in the Windows directory.
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.
err:wineboot:main Cannot set the dir to L"C:\\windows" (2)
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.
err:module:import_dll Library ole32.dll (which is needed by L"C:\\windows\\system32\\winecfg.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\winecfg.exe" failed, status c0000135
```

Yes, this .wine file works great under my 10.04 system.  Mmmm, I didn't think to check the version of Wine ... let me check on that.

---

### Post by bobwyajnr on 2010-11-25
Looks like a permissions issue. The old **.wine** may have a different user or group set it on it - something like that.

Best on the new system to recursively reset permissions for your user id and grp id on the new system (which will replace the current owner and grp id's on the backed-up **.wine** directory), use: [**chown**]("http://unixhelp.ed.ac.uk/CGI/man-cgi?chown") with **sudo**.

Hope that's clear! :popcorn:

Bob

---

### Post by MSwal2846 on 2010-11-25
Thanks, Bob, for the clue.

I couldn't see any difference between the .wine that I brought in and the .wine that was created for the first time.  So, instead, I copied the "inside" of the original .wine directory into the new .wine directory and it's working just fine.

Again, thanks for you help and quick response!

---

