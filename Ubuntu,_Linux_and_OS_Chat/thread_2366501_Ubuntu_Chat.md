---
title: "Ubuntu Chat"
date: 2017-07-18
forum: Ubuntu, Linux and OS Chat
---

### Post by gordie692 on 2017-07-18
Hey guys running Ubuntu 16.04 LTS on my desktop Acer all in one had Windows 10 on it when I bought it but didn't like it so I put Ubuntu on it, I've been using Ubuntu for a number of years and so far everything is great I changed my Ubuntu from the unity to gnome and so its great good guys keep up the good work I even bought a Ubuntu hat from the Ubuntu store for support.

---

### Post by RobGoss on 2017-07-18
Thanks for letting us know how well you like Ubuntu it's a great OS and it just keeps getting better

---

### Post by TheFu on 2017-07-18
Hey Gordie - FYI, nobody here works for Canonical.  This is 99.9999999% volunteers, though Canonical does provide and run the servers for the forums.

---

### Post by Bucky Ball on 2017-07-19
> **TheFu said:**
> Hey Gordie - FYI, nobody here works for Canonical.  This is 99.9999999% volunteers, though Canonical does provide and run the servers for the forums.

+1, but that is 100%. There are NO paid staff/devs on these forums from Canonical. Wholly volunteer staff and users and all here of our own volition. :)

Sure your sentiments would be appreciated if you passed them on to Canonical directly. 

Having said that, as a regular user, I still get as excited about Ubuntu as the OP nearly ten years later! Love it and glad I finally got here after Linux being in my peripheral vision for several years prior to the plunge. :)

---

### Post by gordie692 on 2017-07-19
I knew its a kinda of volunteer with open source but question I live in Canada and would like help but want to learn more on Linux I really like the open source community could I do do this online its hard for me to travel due to I do kidney dailysis but so I would have no problems donating to open source whether then Windows with only stupid malware antivirus crap least with you guys and donating its everything from security to the whole system OS and your time

---

### Post by RobGoss on 2017-07-19
Learning how to use Linux can be done right here on these forums, I would suggest focus on what it is you want to learn and ask as many questions as you need to. The Ubuntu main website has a lot of good reading

You can also visit some of the links in my signature as well

---

### Post by gordie692 on 2017-07-19
Thanks bud I was just wanting to learn basic coding but I heard sudo isn't very secure or is that a rumor

---

### Post by RobGoss on 2017-07-19
> **gordie692 said:**
> Thanks bud I was just wanting to learn basic coding but I heard sudo isn't very secure or is that a rumor

When you say coding I'm assuming you mean using the terminal commands
 correct?

As far as sudo is concerned I use it all the time with out any issues.
This post might clear up a few things about using  sudo when using the terminal [https://ubuntuforums.org/showthread.php?t=921017](https://ubuntuforums.org/showthread.php?t=921017)

---

### Post by miqrojamie on 2017-07-20
sudo is just the root user account which is locked unless you were to run it in a terminal command. It's in no way a programming language or such.

That said, welcome to Ubuntu! I also have an Acer computer, albeit it runs Xubuntu 17.04 (with XFCE of course) and there are no problems with it. Glad you like it so far ;)

---

### Post by QIII on 2017-07-20
"sudo" is not the root user account.  sudo is a command that temporarily raises the privileges of a user who is a member of sudoers to *near-*root privileges.  The user is still the same user.  root is still root.  They are different users.

Members of the sudoers group can act *as root* using commands similar to 

```
sudo su
```

This can be seen by the change in the command prompt.

---

### Post by miqrojamie on 2017-07-20
I need to brush up on Ubuntu before I post untrue things, I guess. :P

---

### Post by vasa1 on 2017-07-20
> **gordie692 said:**
> Thanks bud I was just wanting to learn basic coding but I heard sudo isn't very secure or is that a rumor
You have started quite a few threads related to "security" so far :)

---

### Post by deadflowr on 2017-07-20
> **gordie692 said:**
> Thanks bud I was just wanting to learn basic coding but I heard sudo isn't very secure or is that a rumor

Not sure about very insecure, but sudo's default setup on Ubuntu does have one particular issue that may be considered less than savory.
And that is the fact that it has a timeout of something like 15 minutes per session (session being any logged in terminal or console shell)
The risk in that is that if you were to run something like *sudo apt update* and leave your machine, anyone could then run any command with sudo and it will not require a user password to run.
And it would be that way for up to 15 minutes, or until the session is ended, either exiting  or closing the terminal/console.

By comparison something like pkexec's default setting in Ubuntu are to only allow it to run once per instance, so someone who runs *pkexec apt update* can walk away and know that someone cannot simple invoke a new command as pkexec will require the user password every time.

But that's only a simple comparison of their respective timeout settings as set in default on Ubuntu.
And in no way a suggestion that one can be a full-on replacement for the other, or vice versa.

My only suggestion as to running sudo/root/pkexec is that you should only ever run it if the task at hand really needs it.
(It's quite easy to find out if a command require elevated rights, just run the command without the sudo or as root, and see what happens.
[Programs that actually need root will usually tell you, using terms like Permission Denied]

---

### Post by TheFu on 2017-07-20
> **gordie692 said:**
> Thanks bud I was just wanting to learn basic coding but I heard sudo isn't very secure or is that a rumor

Might want to be more selective about where you get your information. 
sudo should be used only when it is needed.  Many people new to Linux overuse it and that causes more problems, which cause more problems and it becomes a terrible cycle.  In general, sudo should be used for just a few things:
* installing new programs
* updating all programs on the system
* tweaking system settings
* starting or stopping system daemons

User settings. Running 99.9999% of GUI programs, or just simple web surfing do not need elevated privileges. No need for sudo.

Use of sudo shouldn't be common or taken lightly.  Every program brings risks when it is used. sudo has risks mainly due to misuse by the uninformed.

If you want to learn basic coding, chances are that you don't need sudo for it. Though I don't know what "basic coding" means to you.  I was a full-time coder for about 15 yrs.  Google has a free Python programming class that might interest you.

---

### Post by oldos2er on 2017-07-20
> **miqrojamie said:**
> I need to brush up on Ubuntu before I post untrue things, I guess. :P

```
man sudo
``` is right there at your fingertips.   :)

---

### Post by unityforever on 2017-07-24
> **TheFu said:**
> Hey Gordie - FYI, nobody here works for Canonical.  This is 99.9999999% volunteers, though Canonical does provide and run the servers for the forums.

so none of you guys are official staffs to answer the question of people???
so what is the administrator, are they employed?
is any of you get paid?

(please modify my post to correct my grammar error if you like, thanks)

---

### Post by wildmanne39 on 2017-07-24
> **uiduser said:**
> so none of you guys are official staffs to answer the question of people???
so what is the administrator, are they employed?
is any of you get paid?

(please modify my post to correct my grammar error if you like, thanks)

No one here gets paid, we are all volunteers, why does it matter if we get paid or not? we are all here to help that is all that matters in my opinion.

Cheers:)

---

### Post by Bucky Ball on 2017-07-25
> **uiduser said:**
> so none of you guys are official staffs ...

No, as I said in about post #3 and has been reiterated here by wildmanne39, and not all of us are guys, either. Pays to be non-gender specific when addressing forum members as 99% of usernames don't indicate gender one way or the other. ;)

---

### Post by Perfect Storm on 2017-07-25
gender would only be important here if this was a dating site (which is not). :KS

---

### Post by oldos2er on 2017-07-25
> **uiduser said:**
> so none of you guys are official staffs to answer the question of people???
so what is the administrator, are they employed?
is any of you get paid?

(please modify my post to correct my grammar error if you like, thanks)

I'm gainfully employed, and official staff. The two are not related in any way.   :)

---

### Post by QIII on 2017-07-25
The entire Ubuntu Forums community is here to answer questions about Ubuntu if you post in a support sub-forum.  This is a chat area, not a support area.  The Staff members are all "official".  Moderators are selected and approved by the Admins.  Admins are approved by the Ubuntu Community Council.

The Moderators and Admins are all volunteers.  We are not employed by Canonical, Ltd.

I am gainfully and happily employed by a different company.

---

