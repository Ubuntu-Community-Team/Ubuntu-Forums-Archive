---
title: "Can unprivileged software harm the system?"
date: 2009-10-13
forum: Security
---

### Post by xavierpij on 2009-10-13
(Sorry if this is the wrong forum section or it's already posted 8-[)

This is just a question for people that know more about Ubuntu security: If I have an Ubuntu computer, and I let you execute any command you want in it (assuming that you don't know the sudo password, and there are no vulnerabilities), how much harm could you cause?
You could delete my files, yes, but could you do anything else interesting like make a keylogger execute every time I start the computer, or just crash the system?

---

### Post by Rob_H on 2009-10-13
Generally, a user has read-only access to everything outside their home and tmp directories with the exception of removable media devices. So that alone significantly limits what they can do "globally".

---

### Post by rookcifer on 2009-10-13
> **xavierpij said:**
> (Sorry if this is the wrong forum section or it's already posted 8-[)

This is just a question for people that know more about Ubuntu security: If I have an Ubuntu computer, and I let you execute any command you want in it (assuming that you don't know the sudo password, and there are no vulnerabilities), how much harm could you cause?
You could delete my files, yes, but could you do anything else interesting like make a keylogger execute every time I start the computer, or just crash the system?

Assuming no social engineering or privilege escalation vulnerabilities, then all that malware can do is destroy your personal files.  Keyloggers aren't practical because a keylogger would need access to system (root owned) files, which it wouldn't have.  

So, essentially, malware can destroy your files, but not much else.  This is probably one reason we don't see much malware on Linux (it just can't do much).  Criminal hackers don't have much incentive to destroy files, they would rather log keystrokes in order to find CC numbers, etc.  This is not really possible without A) social engineering or B) getting root.

---

### Post by The Cog on 2009-10-14
Assuming no vulnerabilities that allow privilege escalation...

If you give him a separate account, he may be able to read your files, but won't be able to damage them in any way.

If you give him access to your user account, he can read/modify/delete all your files in your home directory. He may also be able to install spyware or other malware that runs whenever you log in, although that would not affect other users. I think he could for instance modify your gnome menu to launch keylogging shim programs for any programs (that were) in your menu.

---

### Post by __p1n__ on 2009-10-14
A keylogger could get installed in your local account presuming that your UID owns your home directory and has 7xx permissions.

---

### Post by undecim on 2009-10-14
If you run it as the same user you use yourself, It can poison some of the userspace methods that you gain root privileges. For example, it can add a bash alias for sudo that would run a program with root privileges when you use the sudo command from the terminal. Remember, after using sudo, you have 15 minutes where you don't need a password. (I did that to a friend of mine once... We had a sort of hacking war between each other for fun.)

Other than that, it can modify and read your personal files (potential identity theft!), and if you don't keep your system up to date, it may be able to gain root access. A flaw that allows this is discovered every once in a while, but keeping up-to-date will help prevent it from happening.

If you absolutely have to run software from an untrusted source, you should be running it in a virtual machine. If that is impossible for one reason or another, you should 1) run it as separate user. 2) set up AppArmor to restrict the program to only what it should be doing.

---

### Post by rookcifer on 2009-10-14
> **__p1n__ said:**
> A keylogger could get installed in your local account presuming that your UID owns your home directory and has 7xx permissions.

The keylogger would need root access in order to install itself and function.  For instance, it would need read access to /dev (which the user doesn't have) or perhaps to /var/log (again takes root access).

All keyloggers I have seen for Linux (and I have looked into a number of them) require root access.  Most of them install themselves as kernel modules.  Perhaps there are methods for keylogging from userspace (without reading any root owned files) but I am not aware of any methods to do this.

---

### Post by __p1n__ on 2009-10-14
> **rookcifer said:**
> The keylogger would need root access in order to install itself and function.  For instance, it would need read access to /dev (which the user doesn't have) or perhaps to /var/log (again takes root access).

All keyloggers I have seen for Linux (and I have looked into a number of them) require root access.  Most of them install themselves as kernel modules.  Perhaps there are methods for keylogging from userspace (without reading any root owned files) but I am not aware of any methods to do this.

Here's one: a keylogger can attach to a running process with the ptrace system call.  If you're running a program (i.e. konqueror or firefox under your local uid) then a ptrace-based keylogger (configured to start when you log in and running under your uid) can attach to those or any other programs that you care to run.

The 'autostart-keylogger-on-login' behavior can be created by an edit to your local uid .profile, .login, .cshrc, etc.

100% execution using your local uid.

---

### Post by xavierpij on 2009-10-14
Cool, thanks for all the replies. (FYI: I don't need to run untrusted software, it was just curiosity)

About the keyloggers: I would find it strange if it was impossible to make a keylogger without being root. After all, the normal programs con read the keyboard, so a keylogger should just run itself before Firefox and capture the events.

And a further question: couldn't a program capture your password when you type it or pose as sudo? Shouldn't that be considered a security bug? :roll:

---

### Post by The Cog on 2009-10-14
> **xavierpij said:**
> And a further question: couldn't a program capture your password when you type it or pose as sudo? Shouldn't that be considered a security bug? :roll:

Yes it could.

I wouldn't regard it as a bug. If an un-trusted program can run under your account then you are in trouble in lots of different ways. Creating an aliases or shims for sudo or firefox etc. and capturing passwords is one fairly obvious way of causing trouble. I'm sure there are more subtle ways too.

---

### Post by doas777 on 2009-10-14
privledge escalation is teh major concern here. if the attacker can gain user access, and use that to gain root, then you're screwed.
I remember some guys on milw0rm published some privledge escalation code (in python) last year. the bug has since been patched, but the original author had had the script for years, and doesn't recall what he wrote it for (or so he claimed).

---

### Post by xavierpij on 2009-10-15
Well, I don't want to be pedantic, but if unprivileged software *can* technically cause harm to the system (and escalate privileges, since you must enter your password every few days to update, and it can read it), they are as dangerous as privileged software. 
So, if you are never going to run potentially harmful software, why bother with passwords? Why not automatically grant programs root access?

Yes, that might sound crazy, but considering Linux is always marketed as "very secure", even a slight problem like this should be considered high-priority.

---

### Post by SuperSonic4 on 2009-10-15
It would damage the home directory but not the root directory. Bear in mind that for the vast majority of users (ie desktop users) ~ is much more important than /

It takes about 20mins to reinstall if something goes wrong but often documents in ~ are irreplaceable

I'd be annoyed if / partition was rendered unusable but it's nothing a reinstall can't cover

---

### Post by doas777 on 2009-10-15
> **xavierpij said:**
> Well, I don't want to be pedantic, but if unprivileged software *can* technically cause harm to the system (and escalate privileges, since you must enter your password every few days to update, and it can read it), they are as dangerous as privileged software. 
So, if you are never going to run potentially harmful software, why bother with passwords? Why not automatically grant programs root access?

Yes, that might sound crazy, but considering Linux is always marketed as "very secure", even a slight problem like this should be considered high-priority.

linux is "very Safe" when compared to other options. I prefer the term safe, because as you have pointed out, absolutely no system is or can ever be secure. 

most hacks on linux servers involve comprimizing restricted users ssh credentials, and then using that account to "get root".

---

### Post by rookcifer on 2009-10-15
> **xavierpij said:**
> Well, I don't want to be pedantic, but if unprivileged software *can* technically cause harm to the system (and escalate privileges, since you must enter your password every few days to update, and it can read it), they are as dangerous as privileged software. 

How is it going to get your password?  As I said before, you need root access to install a keylogger.  You can't just drop a script in a user's /home directory and have it steal passwords (social engineering notwithstanding -- but if you're going to social engineer you would be going after root anyway).

---

### Post by __p1n__ on 2009-10-16
> **rookcifer said:**
> How is it going to get your password?  As I said before, you need root access to install a keylogger.  You can't just drop a script in a user's /home directory and have it steal passwords (social engineering notwithstanding -- but if you're going to social engineer you would be going after root anyway).

What you said before is incorrect, a "keylogger" -type app does not require uid=0 priviledges to monitor i/o (or any memory) of apps running under the same uid (see my earlier post in this thread.)  Similarly, a shim-type script that runs the keylogger can be trivially auto-started at login time.

---

### Post by doas777 on 2009-10-16
this worked fine, until the kernel update last year <Be Warned, Dev is a potty-mouth>:
[http://downloads.securityfocus.com/vulnerabilities/exploits/27704-2.c](http://downloads.securityfocus.com/vulnerabilities/exploits/27704-2.c)


also ask yourself this: if linux is soooooooo secure that no non-admin code could hurt it, why do we need apparmor/sellinux?

---

### Post by rookcifer on 2009-10-16
> **doas777 said:**
> this worked fine, until the kernel update last year <Be Warned, Dev is a potty-mouth>:
[http://downloads.securityfocus.com/vulnerabilities/exploits/27704-2.c](http://downloads.securityfocus.com/vulnerabilities/exploits/27704-2.c)


also ask yourself this: if linux is soooooooo secure that no non-admin code could hurt it, why do we need apparmor/sellinux?

MAC systems are mainly used to sandbox root processes and services.  And the exploit you posted is the infamous "vmsplice" bug of a couple years ago.  It only works if a user has local access to the machine.  It's not a remote root exploit (the kind to be really worried about).

---

### Post by doas777 on 2009-10-16
> **rookcifer said:**
> MAC systems are mainly used to sandbox root processes and services.  And the exploit you posted is the infamous "vmsplice" bug of a couple years ago.  It only works if a user has local access to the machine.  It's not a remote root exploit (the kind to be really worried about).

true, but it is one example of how unprivileged code can allow damage to be done to your system.

---

### Post by update_manager on 2009-10-16
> **xavierpij said:**
> Well, I don't want to be pedantic, but if unprivileged software *can* technically cause harm to the system (and escalate privileges, since you must enter your password every few days to update, and it can read it), they are as dangerous as privileged software. 
So, if you are never going to run potentially harmful software, why bother with passwords? Why not automatically grant programs root access?

Yes, that might sound crazy, but considering Linux is always marketed as "very secure", even a slight problem like this should be considered high-priority.

Not all programs are evil, some are just dangerous. Really dangerous conditions can happen by accident (like filling up a drive with data) and in those cases the root user allows some protection (Ubuntu reserves 5% of the drive for the root user).

Also, user accounts can be configured with very limited access (/etc/security/limits.conf).

---

