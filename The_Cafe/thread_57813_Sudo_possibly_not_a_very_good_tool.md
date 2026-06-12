---
title: "Sudo possibly not a very good tool?"
date: 2005-08-17
forum: The Cafe
---

### Post by Takis on 2005-08-17
Maybe a little too good is what I should say.

I was going a little app-crazy last night installing various little utilities (like a spellchecker for my email composer) when a thought struck me: although it's very difficult to create a virus or backdoor for Linux, it's possible if you get the owner to sudo it in. Now obviously, if you install a program that admits it's going to mess with system settings, you're going to be wary - but I was installing a spellchecker that simply wanted to create an entry in /usr/bin. This needed sudo priviledges - which, if this spellchecker example had some poorly or maliciously written code, could have done anything it wanted to my system - even turn it into a drone. :shock:

The point is that there's a massive amount of trust (yes, you have access to the source code in most cases, but how many amongst us check every time?) amongst the Linux community - this is a good thing, but unfortunately exploitable. Very exploitable.

The point is that user-level applications should not (in most cases) require full priviledges to install - or worse yet, run. I suggest a couple of different ways to try and solve the problem:
[list=1]
[*](difficult to implement, but possibly better long-term) The creation of a lesser root user, which does not have access to system and basic X11 files. All users can type a command similar to 'sudo' to escalate their priviledges. The main point of this is for running installations/scripts that need more priviledges without the chance to corrupt the underlying system.
[*]The modification of apt/dpkg/alien/Synaptic to be able to run as a normal user. All programs installed in user mode will be installed in the user's home directory only - configuration files and all. Obviously, system-level programs will not be available to be installed in user mode.
[/list]
With the increasing popularity of Linux, I think this is a major issue that will definitely be exploited in some form or another in the very near future. Thoughts?

---

### Post by Stormy Eyes on 2005-08-17
[QUOTE=Takis]With the increasing popularity of Linux, I think this is a major issue that will definitely be exploited in some form or another in the very near future. Thoughts?[/QUOTE]

If you run Linux, and you personally install software from an untrusted source that proves to be malware, then you deserve the consequences. Ubuntu users who aren't proficient should not be using Ubuntu-approved repositories or installing apps they just downloaded from some website. Those who do, and ruin their systems as a result, have themselves to blame.

---

### Post by adwait on 2005-08-17
That's a rather elitist method of putting it. AS the popularity of Linux grows, the number of users who aren't very well versed with computers and Linux are certainly going to be increasing. But yes, the users should be safe as long as they use the Ubuntu repositories.

---

### Post by Takis on 2005-08-17
[QUOTE=Stormy Eyes]Ubuntu users who aren't proficient should not be using Ubuntu-approved repositories or installing apps they just downloaded from some website.[/QUOTE]
Should not be, but let's be realistic, people will. An example is the [kaffeine replacement package](http://www.ubuntuforums.org/showthread.php?t=27670) that's found on these forums.
The whole point of having sudo is that even someone who knows what they're doing on their system doesn't run around with priviledges they don't need 24/7. Why shouldn't the same go for applications? Why do I need the same level of priviledges to install a simple program (e.g. lame) as I do to write to the MBR?

---

### Post by nocturn on 2005-08-18
> **Takis]but I was installing a spellchecker that simply wanted to create an entry in /usr/bin. This needed sudo priviledges - which, if this spellchecker example had some poorly or maliciously written code, could have done anything it wanted to my system - even turn it into a drone. :shock:
[/quote]

This is an issue, but not with sudo itself.  
If you download anything, even a tarball, and you run ./configure said:**
> 
The point is that user-level applications should not (in most cases) require full priviledges to install - or worse yet, run. I suggest a couple of different ways to try and solve the problem:


There are very few apps that need root to run.    To install, it is good that they need root, I do not want a user installing an app in /bin that is compromised,  thereby letting all other users run it.

An extra layer of protection can help a bit, but it does not solve the fundamental problem of downloading and installing untrusted software.  The low-level root can still install a trojaned program that is run by all users...

---

### Post by agger on 2005-08-18
[QUOTE=nocturn]
But the problem remains that if you download anything, be it a binary or souce code you put your trust in the integrity of that download.  A good practice is to only download from trusted sources and to check digital signatures if provided (this is already done by apt).
[/QUOTE]
Yes, this is no doubt a good practice but I don't think it will last. As stated earlier in this thread, the more people start  using Linux the greater the need for downloading and installing all kinds of problems from all kinds of sources.

> 
There are very few apps that need root to run.    To install, it is good that they need root, I do not want a user installing an app in /bin that is compromised,  thereby letting all other users run it.

An extra layer of protection can help a bit, but it does not solve the fundamental problem of downloading and installing untrusted software.  The low-level root can still install a trojaned program that is run by all users...

True, I do not want a user to install anything in /bin. But ... a user might install and run an application in his own home directory with only his own privileges, and this application would not be able to do more harm than the user himself might.

Actually, it would be nice with a version of apt-get which would work by installing in the user's home directory (and not require root privileges) but would still automate the installation process.

Then, a "normal" user installation might be like this:

[list]
[*]Have a "normal" user with no root privileges and not in the sudoers list
[*]In order to install things on system level, login to another user which is a sudoer. never run as this user otherwise
[*]Keep the root account disabled.
[/list] 
I don't know how big a problem this is in real life, but this scheme would actually improve security - and yes, if only by adding another level of security.
But I think it's important that users be able to install programs easily without roort privileges - but only in their own home directories.

---

### Post by UbuWu on 2005-08-18
[QUOTE=agger]
True, I do not want a user to install anything in /bin. But ... a user might install and run an application in his own home directory with only his own privileges, and this application would not be able to do more harm than the user himself might.
[/QUOTE]

Which is at worst deleting his and all other peoples home directories!  :??:

---

### Post by poofyhairguy on 2005-08-18
[QUOTE=Takis]
The point is that there's a massive amount of trust (yes, you have access to the source code in most cases, but how many amongst us check every time?) amongst the Linux community - this is a good thing, but unfortunately exploitable. Very exploitable.
[/QUOTE]

Officially if you don't touch anything not from Ubuntu officially you are fine. If you can't trust the main server, you can't trust anything. Third Party packages might always be bad, thats not a sudo problem....thats a computer problem. 

If you install some random deb and its malware....TELL PEOPLE....keep us in the loop. Thats the best defense. Knowledge.

---

### Post by agger on 2005-08-18
[QUOTE=UbuWu]Which is at worst deleting his and all other peoples home directories!  :??:[/QUOTE]

A user can't delete other people's home directories - people should by default only give others read and execute access (if any access at all) to their directories.

And people *will* need to install non-Ubuntu things. I agree with poofyhairguy: If you stumble upon malware, tell people. And, of course, only install programs that you have some reason to trust. 

But I think the idea of giving people an "apt-get" which only works for their own home directory and doesn't need root access would improve security - this would limit the necessity of sudoing.

---

### Post by Takis on 2005-08-18
[QUOTE=poofyhairguy]If you install some random deb and its malware....TELL PEOPLE....keep us in the loop. Thats the best defense. Knowledge.[/QUOTE]
Naturally dude. There were two points I wanted to make though: one was that people (including myself) tend to give root priviledges very easily to installers, the other was more of an open-ended question: why is it that to install a user-level program you require the same kind of access as to wipe the hard-drive? Or see every other user's home drive?

Of course people like me (and hopefully most of the Linux community) will report malicious software when it's found, but I think that this is a security risk that shouldn't exist in the first place.

---

### Post by Kvark on 2005-08-18
Yea... a half-sudo that can do only the most common sudo things might reduce the damage of maleware a bit. But it wouldn't solve the problem.

The real problem here is that most users would install something an unknown guy in a chat room sent to them, that a flashing popup said is fun or that they found on some unknown russian website. This will still be a problem even if you can install those things without real sudo.

You will never get a secure system if there is an admin/root/sudoer person on the system who does not know the common sence of computer security. What really needs to be done is to educate the users. In this case that means make them aware of that they should be very careful with trusting and installing programs from other sources then the official repos.

---

### Post by UbuWu on 2005-08-18
[QUOTE=Kvark]Yea... a half-sudo that can do only the most common sudo things might reduce the damage of maleware a bit. But it wouldn't solve the problem.
[/QUOTE]

A half-sudo is already possible by editing the /etc/sudoers file. You can specify exactly what commands/programs a user can and can't run. But you can't specify what a program that is being run with sudo has access to.

---

### Post by TheDude on 2005-08-18
[QUOTE=Takis]Naturally dude. There were two points I wanted to make though: one was that people (including myself) tend to give root priviledges very easily to installers, the other was more of an open-ended question: why is it that to install a user-level program you require the same kind of access as to wipe the hard-drive? Or see every other user's home drive?[/QUOTE]

Good question. Thats what SE Linux is trying to fix.

---

### Post by Takis on 2005-08-18
[QUOTE=TheDude]Thats what SE Linux is trying to fix.[/QUOTE]
My understanding was that it's centred around process access protection - but yes, it does seem to have some form of ACL. However, we can assume that user X is supposed to have full admin rights on his/her computer (e.g. a desktop machine at home), so I'm not so sure how useful ACLs are here. I think the best way would be to create a dummy 'root' user (let's call it 'node') and chown most of /usr, /etc (maybe even move all system files from /etc (e.g. /etc/passwd) to /srv or something), and parts of /lib (maybe reserve an area in /lib for system files owned by root) to 'node.root' or something. Then it's just a matter of running 'sudo -u node'.

Or, we could have user-mode for the app installers.

---

