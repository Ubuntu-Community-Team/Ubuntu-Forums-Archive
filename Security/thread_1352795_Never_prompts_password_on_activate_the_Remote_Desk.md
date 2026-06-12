---
title: "Never prompts password on activate the Remote Desktop Sharing"
date: 2009-12-12
forum: Security
---

### Post by telefono on 2009-12-12
Hi everyone!

When activates the Remote Desktop, i dont get a password confirmation; anybody with local access can share my desktop :(

How can I configure to prompt password for that?

really thanks!!!

---

### Post by cariboo on 2009-12-12
Go to System-->Preferences-->Remote Desktop, to set things up. I wouldn't advise using it anywhere else but on your local network, as it is one of the easiest ways for a cracker to exploit your computer.

If you have to access the computer remotely use vnc with ssh.

---

### Post by telefono on 2009-12-12
Im not sure if i only has this issue; but when i changes the settings in System-->Preferences-->Remote Desktop; the system dont ask for password (everyone who has local acces to my computer when im logged, can change all the config of the Remote Desktop).

So if any get access to my laptop when is loged in, then can allow the remote access, settup another password, hide the notification area... and never will be prompted for user-password.

how can i prevent this?

---

### Post by ubhi on 2009-12-12
basically this settings for VNC. & select that following option in remote desktop in preferences...

Require the user to enter this password

& enter password

---

### Post by koenn on 2009-12-12
> **telefono said:**
> Im not sure if i only has this issue; but when i changes the settings in System-->Preferences-->Remote Desktop; the system dont ask for password (everyone who has local acces to my computer when im logged, can change all the config of the Remote Desktop).

So if any get access to my laptop when is loged in, then can allow the remote access, settup another password, hide the notification area... and never will be prompted for user-password.

how can i prevent this?

By not letting others use your session or log in with your credentials

---

### Post by telefono on 2009-12-12
> **koenn said:**
> By not letting others use your session or log in with your credentials

I agree but, sometimes for someones, that is an impossible : (

Another way?

---

### Post by Xen042 on 2009-12-12
Well if you don't need the functionality at all then you can...
```
sudo apt-get remove vino vinagre
```

---

### Post by telefono on 2009-12-12
Can i setup a password for certain user actions?

---

### Post by telefono on 2009-12-16
nobody?

---

### Post by koenn on 2009-12-16
you can possibly work something out by setting permissions on the relevant executables, and use the 'sudoers' file to manage them.

There may be other ways, too.

But essentially, these are ugly workarounds.


On a multi user system, give every user his session. 
Easy. Simple. Secure.

---

### Post by telefono on 2009-12-16
Thanks Koenn! 

Is a good way to solve!

Question: im the only who thinks that this is a very important securitie issue? haha really i want to know; to me this is very important. 
Do u never stays your machine logged, because forgotten or another...?
Why the clock settings needs a password confirmation and for Share the Desktop not?

Thanks guys!, and sorry for my #@$@$ english, im very new with this.

---

### Post by koenn on 2009-12-16
> **telefono said:**
> 

Question: im the only who thinks that this is a very important securitie issue? haha really i want to know; to me this is very important. 
It's a non-issue if you don't share your sessions or give out your password

> Do u never stays your machine logged, because forgotten or another...?
Make it a habit to lock your session when you're away from keyboard, so you do it without even thinking about it. And set a screensaver + lock just in case you forget abyway.
 
> Why the clock settings needs a password confirmation and for Share the Desktop not?
clock settings have system-wide impact (file time stamps, cron jobs, some authentication mechanisms such as Kerberos, ...) so only the sysadmin (root) is allowed to change them. The password confirmation is for sudo, which temporarily makes you root.

---

### Post by telefono on 2009-12-16
> **koenn said:**
> It's a non-issue if you don't share your sessions or give out your password


Make it a habit to lock your session when you're away from keyboard, so you do it without even thinking about it. And set a screensaver + lock just in case you forget abyway.
 

clock settings have system-wide impact (file time stamps, cron jobs, some authentication mechanisms such as Kerberos, ...) so only the sysadmin (root) is allowed to change them. The password confirmation is for sudo, which temporarily makes you root.

I agree, and you're right. 

But, test it with your favorite friend of the work-office; first, think in a friend with an screensaver + lock (5 minutes?); then, wait to he goes to the bathroom and rapidly go to him computer. Well, now share him Remote Desktop, disable the notification area; and voilá! now u can see that, wath he does. It sounds chillingly simple.

but, i really thanks to you for the explain! :wink:

---

### Post by koenn on 2009-12-16
> **telefono said:**
> I agree, and you're right. 

But, test it with your favorite friend of the work-office; first, think in a friend with an screensaver + lock (5 minutes?); then, wait to he goes to the bathroom and rapidly go to him computer. Well, now share him Remote Desktop, disable the notification area; and voilá! now u can see that, wath he does. It sounds chillingly simple.

but, i really thanks to you for the explain! :wink:
I'm system administrator, I have sufficient control over his computer to setup remote desktop access without having to wait for him to leave his computer. :)

---

### Post by cariboo on 2009-12-16
Locking the desktop is only meant to stop casual users, if someone has physical access to your computer, and they know what they are doing, all the passwords in the world won't stop them.

---

### Post by telefono on 2009-12-16
How? How would you activate the "Share Desktop" from a computer with physical access? (without knowing the password)

thanks!

---

