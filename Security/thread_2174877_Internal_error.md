---
title: "Internal error"
date: 2013-09-16
forum: Security
---

### Post by Rick St. George on 2013-09-16
Question;  It seems that the below Error may be a security risk. It keeps coming up on every startup / logon.
Any ideas suggestions? I've already run Update.


------------------  BEGIN REPORT  ---------------------

Ubuntu 12.04 Experienced an Internal Error

 

 Title
    accounts-daemon crashed with SIGSEGV in dbus_connection_send()
 

 ProcCmdline
    /usr/lib/accountsservice/accounts-daemon
 

 Package
    accountsservice 0.6.15-2ubuntu9.6
 

 Dependencies  (partial list)
    adduser

    base-passwd
    busybox-initramfs
 

 MarkForUpload
    True
 

 ProcStatus
    State:  S (sleeping)
 

 SegvReason
    reading NULL VMA
 

 UnreportableReason
     You have some obsolete package versions installed.  

     Please upgrade the following packages and check if the problem still occurs.
 

     Dbus, initramfs-tools, initramfs-tools-bin, tzdata
 

 UpgradeStatus
     Upgraded to Precise on 2012-05-07
 

 -------------------------------  END Report  ------------------

Also, I get a Pop-up Window after Logging on, "RUN PROGRAM" with no specific program identified. Wherefore, I simply close the window, not knowing what it is all about.
Any help would be appreciated.
Thanks!

Rick

---

### Post by Rick St. George on 2013-09-17
Is this in the Right Category?  It was closed in UbuntuStudio (thats what I'm running) but did not know how to delete it once posted. (suggestion ?)

Thanks for your consideration, any help is appreciated.

Rick

---

### Post by cariboo on 2013-09-17
Did you do as the error message suggested and update:

[LIST]
[*]Dbus
[*]initramfs-tools
[*]initramfs-tools-bin
[*]tzdata
[/LIST]

and if so do you still get the error?

---

### Post by Rick St. George on 2013-09-17
YES - hence "Already Ran Update", and I specifically ran those updates ! ! !

---

### Post by cariboo on 2013-09-17
> **Rick St. George said:**
> YES - hence "Already Ran Update", and I specifically ran those updates ! ! !

You weren't to clear on whether you just updated those specific packages only, or if you ran a general update.

Also the way you formatted the error message makes it a bit hard to understand. When posting error messages, a straight copy/paste works the best and makes it easier for everyone to see what the problem is.

---

### Post by Rick St. George on 2013-12-26
Still getting this CRASH REPORT regarding ACCOUNTSERVICES, and of course it asks for my password every time. Sounds like a security risk to me, as it never gets fixed not matter what updates are available. Perhaps if I REMOVE / UNINSTALL this ACCOUNTSERVICE pkg. Is it necessary? Don't remember it before updates addeded it some months ago. Now EVERY STARTUP I get a CRASH REPORT and send it.

Anyone know whats going on???

Rick

---

### Post by cariboo on 2013-12-26
You can try removing accountservice using:

```
apt-get --purge accountservice
```

but due to dependencies, you may not be able to remove it. I'd suggest you try reinstalling the package to see if it makes any difference:

```
apt-get --reinstall accountservice
```

---

### Post by Rick St. George on 2014-02-11
That computer is trash now ... tossed it aside.
May work on it later, and will have to WIPE the HD, and install a higher / newer version.

Thanks
Rick

---

### Post by cariboo on 2014-02-11
> **Rick St. George said:**
> That computer is trash now ... tossed it aside.
May work on it later, and will have to WIPE the HD, and install a higher / newer version.

Thanks
Rick

That action seems a bit drastic, :) A new installation, which should only take from 20 - 30 minutes will reformat your hard drive.

---

### Post by mlnease on 2014-02-24
> **cariboo907 said:**
> You can try removing accountservice using:

```
apt-get --purge accountservice
```

but due to dependencies, you may not be able to remove it. I'd suggest you try reinstalling the package to see if it makes any difference:

```
apt-get --reinstall accountservice
```

Thanks cariboo.  Accountservice was crashing every tme I logged on.  ```
sudo apt-get --reinstall accountservice
``` returned ```
E: Invalid operation accountservice
```; but I reinstalled accountservice via Synaptic and it seems to have solved my problem.

Thanks again.

---

