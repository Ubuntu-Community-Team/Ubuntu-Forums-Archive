---
title: "How to Launch Remmina from Terminal"
date: 2023-10-17
forum: Ubuntu/Debian BASED
---

### Post by bbs-sysop on 2023-10-17
I am using Pop!_OS 22.04 and I launch Remmina often to Remote Desktop in to other computers. 
I would like to set up a keyboard shortcut for Remmina. In order to do that in PopOS I need to know how to launch Remmina from Terminal. When I type **remmina** in Terminal I get the following: 

**Command 'remmina' not found, but can be installed**

But Remmina *is* installed & I launch it from the GUI app launcher nearly daily.

Form what I can surmise, Remmina is installed but it is not in my $PATH. How can either get Remmina in my $PATH or find it's path so I can launch it from Terminal?

---

### Post by #&amp;thj^% on 2023-10-17
Try this:
```
remmina-file-wrapper %U
```

---

### Post by bbs-sysop on 2023-10-17
> **1fallen said:**
> Try this:
```
remmina-file-wrapper %U
```

Thanks for thew quick reply but no luck. When I try '**remmina-file-wrapper %U**' I get:

**Command 'remmina-file-wrapper' not found, but can be installed with:**

---

### Post by howefield on 2023-10-17
Thread noved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by #&amp;thj^% on 2023-10-17
> **bbs-sysop said:**
> Thanks for thew quick reply but no luck. When I try '**remmina-file-wrapper %U**' I get:

**Command 'remmina-file-wrapper' not found, but can be installed with:**

Thanks  howefield for the proper sub forum
 Try a reinstall then as you can see mine launch's just fine:
```
remmina
** Message: 11:40:18.009: Remmina does not log all output statements. Turn on more verbose output by using "G_MESSAGES_DEBUG=all" as an environment variable.
More info available on the Remmina wiki at:
https://gitlab.com/Remmina/Remmina/-/wikis/Usage/Remmina-debugging
Load modules from /usr/lib/x86_64-linux-gnu/remmina/plugins
Remmina plugin glibsecret (type=Secret) has been registered, but is not yet initialized/activated. The initialization order is 2000.
The glibsecret secret plugin has been initialized and it will be your default secret plugin

(org.remmina.Remmina:20454): Gtk-WARNING **: 11:40:18.147: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem
```
check this:
```
apt policy remmina
remmina:
  Installed: 1.4.31+dfsg-2
  Candidate: 1.4.31+dfsg-2
  Version table:
 *** 1.4.31+dfsg-2 500
        500 http://archive.ubuntu.com/ubuntu mantic/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by bbs-sysop on 2023-10-17
I reinstalled and it seems to be launching from Terminal and Keyboard shortcuts now.
Thanks.

---

### Post by #&amp;thj^% on 2023-10-17
Have Fun.

---

### Post by bbs-sysop on 2023-10-17
Thanks again. You just saved me a little time every day.

For anyone else who uses Remmina to remote desktop into a specific computer often you can also set a keyboard shortcut to launch directly in to that *specific machine* even if you are a noob like me.

You can find the full path to the machine by launching the Remmina app and clicking on the specific computer / server you want to  create a shortcut to. When you click on it, you will see the full path on the bottom of the Remmina window along with the name of the profile. 

Once you have that just type **remmina -c [full path/PROFILE_NAME.remmina]** in Terminal to verify in remotes in to the desktop appropriately.

Once you confirm that the command launches in to the machine properly you just have to copy that command in to your keyboard shortcut app. 

You now can Remote into your most common machines with a keyboard shortcut!

---

