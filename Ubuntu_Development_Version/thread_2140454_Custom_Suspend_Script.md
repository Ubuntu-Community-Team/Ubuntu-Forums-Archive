---
title: "Custom Suspend Script"
date: 2013-04-29
forum: Ubuntu Development Version
---

### Post by rednus on 2013-04-29
Hi All, 

I am trying to run a script on-suspend to goto login screen.. so this is what i did

1. created a file called /etc/pm/suspend.d/01_gotologin with code below
```
#!/bin/bash

case "$1" in
    suspend)
        /usr/lib/lightdm/lightdm/gdmflexiserver
        ;;
esac

```
2. Made the file executable "sudo chmod +x "


now when i run the script on its own it works fine.. 

but on suspend i get this error in pm-suspend.log
```

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:


/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/01_gotologin suspend suspend:


/etc/pm/sleep.d/01_gotologin suspend suspend: Returned exit code 1.
Mon Apr 29 21:35:42 BST 2013: Inhibit found, will not perform suspend
Mon Apr 29 21:35:42 BST 2013: Running hooks for resume
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:


```

What am I doing wrong.. please help...

---

### Post by Toz on 2013-04-29
What exactly are you trying to accomplish? 

gdmflexiserver creates a new Xsession on a different virtual console, it doesn't go back to any login screen (it creates a new one). Plus, you're trying to start it when the system is suspending, which doesn't make sense. I have a feeling that this isn't exactly what you want to do.

---

### Post by rednus on 2013-04-29
> **Toz said:**
> What exactly are you trying to accomplish? 

gdmflexiserver creates a new Xsession on a different virtual console, it doesn't go back to any login screen (it creates a new one). Plus, you're trying to start it when the system is suspending, which doesn't make sense. I have a feeling that this isn't exactly what you want to do.


My goal is to go back to login screen after resume.. instead of lock screen.. 

I tried to put the script on both suspend and resume.. did not work on either.. 

Its ok if it creates a new session.. on the login screen, if the user selects a logged in session, it will use the logged in session.. 

thanks
rednus

---

### Post by Toz on 2013-04-29
> **rednus said:**
> My goal is to go back to login screen after resume.. instead of lock screen..
So you want to logout the existing session? What about open files, documents, etc? They will be lost.

> Its ok if it creates a new session.. on the login screen, if the user selects a logged in session, it will use the logged in session.. 
If thats what you want to do, then why not just lock the screen?

Oh wait. Are you looking for an option to start a new session if on resume, the locked account isn't the one that you want to log into?

---

### Post by rednus on 2013-04-29
> **Toz said:**
> So you want to logout the existing session? What about open files, documents, etc? They will be lost.

No I dont want to log out of the session.. I


> **Toz said:**
> If thats what you want to do, then why not just lock the screen?

Oh wait. Are you looking for an option to start a new session if on resume, the locked account isn't the one that you want to log into?

Three in the house, including my kid, use the same laptop, with one user each.. so when i use it and put it to sleep.. and my kid opens it up, its in my lock screen, "then click on the switch user and then choose the new user to log in" - this is what I am trying to avoid..

---

### Post by Toz on 2013-04-29
Ok, gotcha. Sorry for the confusion.

Try this script:
```
#!/bin/bash

case "$1" in
    resume)
        export XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0
        /usr/bin/dm-tool switch-to-greeter
        ;;
esac

```

It includes  few changes:
1. it uses dm-tool instead of gdmflexiserver (AFAIK, dm-tool is a replacement for gdmflexiserver)
2. it exports XDG_SEAT_PATH which is required by dm-tool
3. it runs on resume

One issue that I've noticed is that on resume, if you select an existing user, it will log back into the existing session, but if lock screen is enabled, you will have to enter your password twice. I guess you could disable lock screen in this scenario.

---

### Post by rednus on 2013-05-06
> **Toz said:**
> Ok, gotcha. Sorry for the confusion.

Try this script:
```
#!/bin/bash

case "$1" in
    resume)
        export XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0
        /usr/bin/dm-tool switch-to-greeter
        ;;
esac

```

It includes  few changes:
1. it uses dm-tool instead of gdmflexiserver (AFAIK, dm-tool is a replacement for gdmflexiserver)
2. it exports XDG_SEAT_PATH which is required by dm-tool
3. it runs on resume

One issue that I've noticed is that on resume, if you select an existing user, it will log back into the existing session, but if lock screen is enabled, you will have to enter your password twice. I guess you could disable lock screen in this scenario.

Perfect... thanks a lot Toz.. 

i think ubuntu should make this option default.. or add it to a config option...

btw.. i am not getting the lock screen issue you mentioned..

---

### Post by Frank Siebert on 2013-10-27
Hello Rednus,

I was also eager for this solution, but it has a major flaw, which should not go unnoticed.

If you are in the lock screen and press [ctrl][alt][F7], you are in the session without entering a password.
If you press [ctrl][alt][F8], your are back to the lock screen.

That's not the fault of your solution, but a general fault in the function dm-tool switch-to-greeter.
It obviously opens always a new xsession to show the greeter, also if called from the menu.

I would call this security by obfuscation, but you could call it also insecurity by obfuscation.
I'll go and try out the bug tracker.

Best regards,
Frank

Update: I found the relevant bug-report at launchpad:
[https://bugs.launchpad.net/lightdm/+bug/1060228](https://bugs.launchpad.net/lightdm/+bug/1060228)

---

