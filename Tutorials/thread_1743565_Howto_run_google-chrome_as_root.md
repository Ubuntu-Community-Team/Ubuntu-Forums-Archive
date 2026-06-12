---
title: "Howto run google-chrome as root"
date: 2011-04-29
forum: Tutorials
---

### Post by WitchCraft on 2011-04-29
**[COLOR=Red]DISCLAIMER/Warning: Running anything as root is risky and you should not run any software as root when you don't have to. If you don't know what you're doing, or are on a system that needs to be secure, leave now.[/COLOR]**


If you have installed google-chrome, you might recently have gotten the message:
google-chrome cannot be run as root.

Very annoying.

Now here's the antidote:

First, switch off Xorg access control:
```

xhost +

```

Now start google chrome as normal user "anonymous"
```

sudo -i -u anonymous /opt/google/chrome/chrome

```

When done browsing, re-enable Xorg access control:
```

xhost -

```

---

### Post by id2578 on 2011-11-28
Just want to add a **permanent solution** to the problem:

1. Open google-chrome located in /usr/bin with 'gedit', 'kate' or your favorite text editor.

```
gedit /usr/bin google-chrome
```

2. Add **"--user-data-dir"** (without the quotes) at the very end of the file. Mine looks like this:

***exec -a "$0" "$HERE/chrome" "$@" --user-data-dir***

3. Save, close and voilà, you're done. Enjoy your favorite browser.

---

### Post by haqking on 2011-11-28
> **id2578 said:**
> Just want to add a **permanent solution** to the problem:

1. Open google-chrome located in /usr/bin with 'gedit', 'kate' or your favorite text editor.

```
gedit /usr/bin google-chrome
```

2. Add **"--user-data-dir"** (without the quotes) at the very end of the file. Mine looks like this:

***exec -a "$0" "$HERE/chrome" "$@" --user-data-dir***

3. Save, close and voilà, you're done. Enjoy your favorite browser.

You should never run a web browser as root, certainly not permanently.

If there is a need to run it as root then do it for the given instance not a permanent fixture.

It is ill advised to browse the internet as root.

Cheers

---

### Post by Browncoyote on 2012-03-18
What would be the preferred (safe) way to operate in an environment where root is the only user?

---

### Post by WitchCraft on 2012-03-31
> **Browncoyote said:**
> What would be the preferred (safe) way to operate in an environment where root is the only user?

Quite simple: 
Open the google-chrome binary, located at
```

/opt/google/chrome/chrome 

```
in a hex editor (make a backup-copy before).

Now find the string "geteuid" and replace it with "getppid".
Done ! :)

Make a script for this, and trigger script execution every time google-chrome is updated ;-)

---

### Post by haqking on 2012-03-31
> **WitchCraft said:**
> Quite simple: 
Open the google-chrome binary, located at
```

/opt/google/chrome/chrome 

```
in a hex editor (make a backup-copy before).

Now find the string "geteuid" and replace it with "getppid".
Done ! :)

Make a script for this, and trigger script execution every time google-chrome is updated ;-)

Well as said before it shouldnt be run as root.

However if you need to there is no need to hex edit which wont work for all versions, no need to script or edit config files, you only need to append a command to the launcher.

If you use icons to launch then append the following the to the command in the launcher

```
--user-data-dir
```

or add it to the command from terminal such as 

```
google-chrome --user-data-dir
```

example the properties of the launcher command is as follows

```
/opt/google/chrome/google-chrome %U
```

just change it to be

```
/opt/google/chrome/google-chrome &#8211;user-data-dir %U
```

and thats it.

Cheers

---

### Post by WitchCraft on 2012-03-31
> **haqking said:**
> Well as said before it shouldnt be run as root.

However if you need to there is no need to hex edit which wont work for all versions, no need to script or edit config files, you only need to append a command to the launcher.

If you use icons to launch then append the following the to the command in the launcher

```
--user-data-dir
```

or add it to the command from terminal such as 

```
google-chrome --user-data-dir
```

example the properties of the launcher command is as follows

```
/opt/google/chrome/google-chrome %U
```

just change it to be

```
/opt/google/chrome/google-chrome &#8211;user-data-dir %U
```

and thats it.

Cheers

I know that it shouldn't be run as root.
 
But the bottom line is, a normal user just has so few rights, I don't want to bother with that ad infinitum (I'm a programmer, not a sysadmin).

BTW: I have modified the launcher icon a long time ago.

But the problem is, your/this variant doesn't work when you click on a link (e.g. in Thunderbird/E-Mail-Program-Of-Choice) **when google-chrome is the default browser**, etc. Same problem from instant messengers (pidgin), HTML editors, MonoDevelop (when I want to debug/test a web application on Linux), and wxWidgets C-programs that open helpfiles, as well as the Oracle installer (opens html file) etc.

Furthermore, when run as other user (xhost + variant), there is no sound, and you cannot access the download directory in /root/ (no rights).

So modifying the startup script like
```

exec -a "$0" "$HERE/chrome" "$@" --user-data-dir

```
or patching the executable is really the only option (just added that info for information purposes, don't recommend it as it probably has side-effects).


**The problem with the startup-script variant is that that the startup-script gets replaced with the vanilla variant every time the browser is updated** (apt-get dist-upgrade), which is quite often. So you have to replace the new startup script with the old one (dangerous), or parse the new one and add your modifications (also dangerous, not to mention work-intensive), or you can just do a binary search and replace on the first occurrence of "geteuid"  with "getppid" with a C program (simple, fast, very effective).

---

### Post by oliverme03 on 2013-04-21
> **haqking said:**
> Well as said before it shouldnt be run as root.  However if you need to there is no need to hex edit which wont work for all versions, no need to script or edit config files, you only need to append a command to the launcher.  If you use icons to launch then append the following the to the command in the launcher  ```
--user-data-dir
```  or add it to the command from terminal such as   ```
google-chrome --user-data-dir
```  example the properties of the launcher command is as follows  ```
/opt/google/chrome/google-chrome %U
```  just change it to be  ```
/opt/google/chrome/google-chrome &#8211;user-data-dir %U
```  and thats it.  Cheers  This works for me, adding it on launcher command. Thanks! :)

---

### Post by karthikeyaa on 2013-04-25
Thanks.

---

### Post by Sef on 2013-04-25
Closed. Necromancing.

---

