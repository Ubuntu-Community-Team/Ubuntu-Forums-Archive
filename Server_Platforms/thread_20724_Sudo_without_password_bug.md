---
title: "Sudo without password bug"
date: 2005-03-18
forum: Server Platforms
---

### Post by reedlaw on 2005-03-18
I had been using sudo like normal for a long while now, when suddenly I boot up today  and discover that sudo is running everything immediately after the command, without asking for the root password.  I am running Hoary and I apply all the synaptic updates everyday.  Even when I open update-manager or synaptic, instead of the usual gksudo pop-up window that promts me for the root password I get no password prompt and the application opens.  I am worried about the security implications of this and am not sure what changed in the updates that I applied to cause this behavior.

---

### Post by reedlaw on 2005-03-21
[QUOTE=reedlaw]I had been using sudo like normal for a long while now, when suddenly I boot up today  and discover that sudo is running everything immediately after the command, without asking for the root password.  I am running Hoary and I apply all the synaptic updates everyday.  Even when I open update-manager or synaptic, instead of the usual gksudo pop-up window that promts me for the root password I get no password prompt and the application opens.  I am worried about the security implications of this and am not sure what changed in the updates that I applied to cause this behavior.[/QUOTE]
 Anyone else get this problem yet?  I still am not asked the root password for any activity.  I can run any command simply by prefixing sudo to it.  I tried logging into the root account with the original root password and it doesn't allow me to.  Do I need to change my root password?  What about this Ubuntu system is making sudo run without a password?

---

### Post by HungSquirrel on 2005-03-21
Does this happen every single time, or does it sometimes ask for a password and sometimes not?  Sudo has a timeout (I believe the default is five minutes) during which time you don't need to re-enter your password every time you do a sudo command; you need only enter it the first time.

Of course, if it's not asking at all, then you have a major problem that needs to be addressed!

---

### Post by Roptaty on 2005-03-22
What is the contents of /etc/sudoers file?

---

### Post by reedlaw on 2005-04-01
[QUOTE=Roptaty]What is the contents of /etc/sudoers file?[/QUOTE]
 here is /etc/sudoers
> # sudoers file.
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets

# User privilege specification
root    ALL=(ALL) ALL

# Added by Ubuntu installer
reed    ALL=NOPASSWD: ALL


Sudo is not asking for a password all the time.  From the moment I log in I can open update-manager, synaptic, etc. all without supplying the superuser password.

Edit: Looking at the file I guessed that removing the NOPASSWD would do the trick and it did.  Thanks for the suggestions.  I still wonder how that got there in the first place.

---

### Post by smarttaz on 2005-04-05
[QUOTE=reedlaw]I had been using sudo like normal for a long while now, when suddenly I boot up today and discover that sudo is running everything immediately after the command, without asking for the root password. I am running Hoary and I apply all the synaptic updates everyday. Even when I open update-manager or synaptic, instead of the usual gksudo pop-up window that promts me for the root password I get no password prompt and the application opens. I am worried about the security implications of this and am not sure what changed in the updates that I applied to cause this behavior.[/QUOTE]
 
Read the thread [http://www.ubuntuforums.org/showthread.php?t=23391&highlight=visudo]("http://www.ubuntuforums.org/showthread.php?t=23391&highlight=visudo") for a GOOD answer.
 
Change with visudo in the file /etc/sudoers, the line:
```
Defaults		!lecture,tty_tickets
``` 
with:
```
Defaults		!lecture,tty_tickets,timestamp_timeout=0
``` 
or:
[left]```
Defaults		!lecture,!tty_tickets
```[/left]
 


because of (from the sudoers manpage):
[indent][left]

**timestamp_timeout**
Number of minutes that can elapse before sudo will ask for a passwd again. The default is 5. Set this to 0 to always prompt for a password. If set to a value less than 0 the user's timestamp will never expire. This can be used to allow users to create or delete their own timestamps via sudo -v and sudo -k respectively.

[/left]
[/indent]

---

### Post by rb1235 on 2005-04-09
i have the reverse problem, i need to be root but cannot.

---

### Post by Xgates on 2005-04-11
Yeah its great when you can just type --> 'sudo -s' and hit enter, and then you are at the root prompt without the need for a password, man talk about ---> ZERO SECURITY!

 Tisk Tisk Ubuntu Team ---> [-X

---

### Post by Spudgun on 2005-04-14
You still need a password to do that.

---

### Post by harisund on 2005-12-27
Why does your last line readreed 
ALL=NOPASSWD: ALL
I think that is why you are not asked for a password

---

### Post by az on 2005-12-27
[QUOTE=harisund]Why does your last line readreed 
ALL=NOPASSWD: ALL
I think that is why you are not asked for a password[/QUOTE]


That's exactly the problem.

Is this another Automatix "feature?"

---

### Post by harisund on 2005-12-27
Automatix didn't do anything like that to me !
(Actually I did it myself in my machine .. )

His file actually reads
# Added by Ubuntu installer
reed ALL=NOPASSWD: ALL

Why is that? I mean, what *Ubuntu installer* would have done that??

---

### Post by jb1095 on 2006-01-02
it may be me just guessing here but did you add super user rights to the account you are logging in with?

try creating a new account and leaving the rights default, then try logging in with that account and see if you are asked for a password.  

If I were you, I would add the root user back and then remove all instances of sudo back from the package manager.  Then try to reinstall sudo through the package manager or with apt-get.

please let us know how it turns out.

---

### Post by loon on 2006-01-04
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL
```

Thats on my server and on my workstation at work. I am using breezy.

Also try replacing:
```
reed ALL=NOPASSWD: ALL
```
with
```
reed ALL=(ALL) ALL
```

Good luck.

---

### Post by weird_c00kie on 2006-10-31
> **smarttaz said:**
> 
Change with visudo in the file /etc/sudoers, the line:

newbie question, but... how do you modify the contents of /etc/sudoers?
i tried 
> sudo gedit /etc/sudoers
and it opens it, but still doesn't let me modify it
says something about having to open it with visudo or something, but i don't know what that means or how to use it

it's not a huge issue for me; i just want to reduce the timeout time a bit

---

### Post by sebbe1991 on 2006-10-31
> **weird_c00kie said:**
> newbie question, but... how do you modify the contents of /etc/sudoers?
i tried 

and it opens it, but still doesn't let me modify it
says something about having to open it with visudo or something, but i don't know what that means or how to use it

it's not a huge issue for me; i just want to reduce the timeout time a bit

if you want to edit the sudoers file with gedit you must use 
```

EDITOR=gedit sudo visudo

```

---

### Post by weird_c00kie on 2006-10-31
> **sebbe1991 said:**
> if you want to edit the sudoers file with gedit you must use 
```

EDITOR=gedit sudo visudo

```

awesome, thanks a lot :D

---

### Post by bobstro on 2007-02-19
FWIW: I removed the username from the sudo group, and that has restored having sudo ask for the password appropriately. timestamp_timeout works properly too, so it's not inconvenient.

- Bob

---

### Post by nowshining on 2007-08-30
[QUOTE=Change with visudo in the file /etc/sudoers, the line:
```
Defaults		!lecture,tty_tickets
``` 
with:
```
Defaults		!lecture,tty_tickets,timestamp_timeout=0
``` 
or:
[left]```
Defaults		!lecture,!tty_tickets
```[/left]
 


because of (from the sudoers manpage):
[indent][left]

**timestamp_timeout**
Number of minutes that can elapse before sudo will ask for a passwd again. The default is 5. Set this to 0 to always prompt for a password. If set to a value less than 0 the user's timestamp will never expire. This can be used to allow users to create or delete their own timestamps via sudo -v and sudo -k respectively.

[/left]
[/indent][/QUOTE]


thanks that helped :) I was looking for that BUT

For feisty I just Deleted the # at the beginning and added ,timestamp_timeout=0

to the end and it worked flawlessly even without rebooting.. :)

---

### Post by jaybombalous on 2007-12-17
> newbie question, but... how do you modify the contents of /etc/sudoers?

its because the file sudoers is not a txt file its a binary, u can either use visudo or another program that will edit a binary file. Try nano with the -w switch enabled.

```
sudo nano -w /etc/sudoers
```

then u should also double check the file with the -c switch in visudo.

```
sudo visudo -c
```

this will verify there are no errors in the file. One space in a binary file can completely **** over your system.

edit: nano is easy to use a lot easier then vi.

---

### Post by robert_pectol on 2007-12-17
> **jaybombalous said:**
> ?

its because the file sudoers is not a txt file its a binary, u can either use visudo or another program that will edit a binary file. Try nano with the -w switch enabled.

Nope.  It's an ASCII text file with the permissions set to 440 or read-only.  Visudo is merely a wrapper that does some sanity checks before allowing you to save harmful, unsafe, or erroneous changes to the sudoers file.  Remember, the integrity of your entire system can hinge on the settings in your sudoers file!

> **jaybombalous said:**
> ...One space in a binary file can completely **** over your system...

As mentioned, it's not a binary so this doesn't apply here.  I don't mean any offense.  I just didn't want folks to be misled.  And just to be clear, you **should** definitely use visudo to edit your sudoers file for the reasons I mentioned.

---

