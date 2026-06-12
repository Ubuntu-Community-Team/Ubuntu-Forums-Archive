---
title: "Is Linux root more secure than Windows administrator?"
date: 2006-06-25
forum: The Cafe
---

### Post by digby280 on 2006-06-25
I've read alot of articles and forum posts warning against logging in to Linux as root.  This made me think, considering alot of Windows users only use administrator accounts, is Linux root more or less secure than Windows in administrator mode?

---

### Post by bukwirm on 2006-06-25
You are warned against using root because root can do anything - like deleting the entire filesystem.

---

### Post by Kimm on 2006-06-25
If you login as root, its no more secure than a Windows system in Administrator mode.

Viruses, are, ofcourse still not an issue (or a very small one), but you can still delete any file on the system.

rm -rf /

Ehem... dont try that command as root! :P

Since a Windows Administrator can do the same thing, its pretty much equaly secure (not counting viruses)

---

### Post by curuxz on 2006-06-25
They are both equaly capable of damage, its just we are smart enough to tell our users not to run admin all the damn time, where as windows uses it as the default.

---

### Post by Kimm on 2006-06-25
As far as I know, a normal windows user has higher access to system files than a Linux user anyway.

---

### Post by Harold P on 2006-06-25
[quote=Kimm]As far as I know, a normal windows user has higher access to system files than a Linux user anyway.[/quote]
They have full access to C:\Program Files, which ius definitely a place where things can get screwed up.

---

### Post by prizrak on 2006-06-25
A Windows admin account is actually more secure than a *nix root account. Root has a 100% unrestricted access to the system (s)he is a $DEITY in the system w/e root says the computer does including deleting the kernel at runtime. Windows admin doesn't have full unrestricted rights, the only account that does is the System account. However it has more than enough rights to destroy the system. 

The issue with running an OS with such access is the fact that it is extremely easy to screw something up, be it by the user him/herself or a piece of malware. In *nix users tend to run as a limited account, in Ubuntu for instance you can read(and execute) any file on your system but only have the right to modify files in your home directory. At least by default you can of course change that.

---

### Post by G Morgan on 2006-06-25
[QUOTE=prizrak]A Windows admin account is actually more secure than a *nix root account. Root has a 100% unrestricted access to the system (s)he is a $DEITY in the system w/e root says the computer does including deleting the kernel at runtime. Windows admin doesn't have full unrestricted rights, the only account that does is the System account. However it has more than enough rights to destroy the system. 

The issue with running an OS with such access is the fact that it is extremely easy to screw something up, be it by the user him/herself or a piece of malware. In *nix users tend to run as a limited account, in Ubuntu for instance you can read(and execute) any file on your system but only have the right to modify files in your home directory. At least by default you can of course change that.[/QUOTE]

What can't you do as Windows administrator. I did a destruction test in a VM once and had no problem doing anything destructive as admin including deleting System32 and any number of system files (explorer.exe etc.). Does anyone have an example of what you can't do.

Personally I'd say root is currently more secure than Windows Admin because of the lack of malware. Long term it would be equally dangerous as Windows. People don't target Linux because users are generally clued up and frustrate the virii/malware writters. It is crucial that this mentality of security first is given to new users as they come in.

---

### Post by rai4shu2 on 2006-06-25
In theory a Windows admin account is more secure, but in practice you are actually safer with a Linux root account (relatively speaking, of course). Either way, you're likely going to get hacked if you are visible on the internet.

---

### Post by IYY on 2006-06-25
In theory, it's a bit safer to log in as administrator in Windows than root in Linux. However, there is so little spyware and virii for Linux that logging in as root isn't that insecure.

However, the Linux system makes it very easy for users to use their system without ever logging in as root. This is very difficult in Windows.

---

### Post by prizrak on 2006-06-26
[QUOTE=G Morgan]What can't you do as Windows administrator. I did a destruction test in a VM once and had no problem doing anything destructive as admin including deleting System32 and any number of system files (explorer.exe etc.). Does anyone have an example of what you can't do.

Personally I'd say root is currently more secure than Windows Admin because of the lack of malware. Long term it would be equally dangerous as Windows. People don't target Linux because users are generally clued up and frustrate the virii/malware writters. It is crucial that this mentality of security first is given to new users as they come in.[/QUOTE]
You can't stop or kill alot of system processes. Can't delete files used by the system (sharing violation error), can't turn off certain services. All those can be done with a root account in *nix.

---

### Post by G Morgan on 2006-06-26
[QUOTE=prizrak]You can't stop or kill alot of system processes. Can't delete files used by the system (sharing violation error), can't turn off certain services. All those can be done with a root account in *nix.[/QUOTE]

Again which services, I've killed a few important ones (whats the one theres several iterations of, I haven't used XP in so long) and all it does is popup windows will restart in x secs. Simply open the 'command line' and enter shutdown -a and it forgets all about that nasty reboot. I've managed to delete almost everything I tried in the windows directory.

Certainly it complains when you do silly things but everything can be circumvented.

---

### Post by prizrak on 2006-06-26
[QUOTE=G Morgan]Again which services, I've killed a few important ones (whats the one theres several iterations of, I haven't used XP in so long) and all it does is popup windows will restart in x secs. Simply open the 'command line' and enter shutdown -a and it forgets all about that nasty reboot. I've managed to delete almost everything I tried in the windows directory.

Certainly it complains when you do silly things but everything can be circumvented.[/QUOTE]
I don't remember which services like you I haven't been on XP in a long time. I do remember it not letting me stop some of them. I didn't say you couldn't trick XP into doing things you shouldn't be able to, just saying that user permissions for Windows admin are lower than those of *nix root.

---

### Post by G Morgan on 2006-06-26
Well you could claim that shutdown -a (thats abort shutdown in XP land for those that don't know)  is a normal user privilege so it isn't tricking it more so it being badly designed since one of the privileges counteracts one of the restrictions. I think the process I was thinking of was svchost, I've never been told I can't kill a process only that the computer needs to reboot. You can install pskill and it will give you even more control over processes.

---

### Post by prizrak on 2006-06-26
Yes svchost (I remember it now) is "unkillable". Windows user permission boundaries are pretty crapily enforced and are easy to elevate. Windows' DAC model only works well in domains with a domain controller maintaining the list of users and privileges.

---

### Post by bruce89 on 2006-06-26
Of course, killing apps in vista requires elevated permissions now.

---

### Post by G Morgan on 2006-06-26
[QUOTE=prizrak]Yes svchost (I remember it now) is "unkillable". Windows user permission boundaries are pretty crapily enforced and are easy to elevate. Windows' DAC model only works well in domains with a domain controller maintaining the list of users and privileges.[/QUOTE]

Again its not unkillable its well.. its microsofted I can't think of any term to describe it. They certainly don't have a good system. Why not make 'unkillable' unkillable as opposed to reseting when killed.

---

