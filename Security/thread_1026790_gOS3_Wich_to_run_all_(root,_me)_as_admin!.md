---
title: "gOS3: Wich to run all (root, me) as admin!"
date: 2008-12-31
forum: Security
---

### Post by Azvareth on 2008-12-31
Hi...

I am a newbie in Linux: I am using gOS in a WinXP VM. (can't install on real hardware - see [http://ubuntuforums.org/showthread.php?t=1025037](http://ubuntuforums.org/showthread.php?t=1025037))

My Question here is: is it possible to run everything as Admin, root and keep those "you must enter your password to do this dialogs?" away from me?

thank you! Azvareth

---

### Post by cariboo on 2008-12-31
Yes it is possible to run as root all the time, but due to forum rules you will have to look else where to find out how.

There is no need to run as root all the time as anytime you are doing any administration that needs to be root you would use **sudo** this gives you root privileges for about 15 minutes, before you need to enter sudo again. If you need to be root for longer than 15 minutes you can use **sudo -i**.

Have a look [here]("http://help.ubuntu.com/community/RootSudo"), for more info.

Jim

---

### Post by pietjanjaap on 2009-01-01
You do not know what you are asking, like: I want my home door open so i do not have to use a key, and yes everybody can come in, do you want that for your pc.

This is why linux is safer then xp, so it is very stupid.
This is why you do not have to use a firewall or virusscanner in linux and you want to throw it away, very cleaver.

Think if you want it, then go back to xp, and do not install a firewall, virusscanner, anti spyware, and be happy.

You should read more about xp and linux, and what is the difference.

Learn hoe to protect xp, almost nowbody does it the good way, OOO i found spyware in xp, clean and it is ok, yes wenn you come home from work, 10 peolple are drinking your bear, you throw them out, is this all you do, next week you have to throw them out again.
If you finf nothing then it's ok!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Azvareth on 2009-01-01
Yes: I do exactly know what I am asking, the key purpose for me to have Linux at this point is to "learn" it so that I can completely abandon Windows. Problem appears when I going in to some admin settings (network), giving me a "enter a password" dialog - but denies me access, even if I give it my first and only loginname's password - the only one I had told that distro, so there is some other password which I don't know and have control over - that I don't like: I like full control.

no need to be sarcastic...

//Azvareth

> **pietjanjaap said:**
> You do not know what you are asking, like: I want my home door open so i do not have to use a key, and yes everybody can come in, do you want that for your pc.

This is why linux is safer then xp, so it is very stupid.
This is why you do not have to use a firewall or virusscanner in linux and you want to throw it away, very cleaver.

Think if you want it, then go back to xp, and do not install a firewall, virusscanner, anti spyware, and be happy.

You should read more about xp and linux, and what is the difference.

Learn hoe to protect xp, almost nowbody does it the good way, OOO i found spyware in xp, clean and it is ok, yes wenn you come home from work, 10 peolple are drinking your bear, you throw them out, is this all you do, next week you have to throw them out again.
If you finf nothing then it's ok!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Sef on 2009-01-01
> This is why linux is safer then xp, so it is very stupid.

From Ubuntu Code of Conduct (Section 2):

> 

[LIST=1]**When asking for technical support:**

[*]There are no stupid questions. You're not a stupid person simply because you do not know how to do something, or do not have the answer to a question. Everyone was a green user at one point in time. :)
[/LIST]
and 
**         When answering technical support issues:**


[LIST=1]
[*]Be considerate to the person asking the question. We were all a green user at one point. Yes, some users are harder to help than others, but please be respectful to all users.
[/LIST]




>  This is why you do not have to use a firewall or virusscanner in linux and you want to throw it away, very cleaver.

Actually Ubuntu and many other Linux distros come with the IPTables firewall installed.  It is command line, but there is a gui for can be installed.

> I do exactly know what I am asking, the key purpose for me to have Linux at this point is to "learn" it so that I can completely abandon Windows. Problem appears when I going in to some admin settings (network), giving me a "enter a password" dialog - but denies me access, even if I give it my first and only loginname's password

If you entered your password for admin privileges, and it did not work then it would be best to start a thread asking for help with that problem.  

Running as root is not a good security practice; however, if you want to do it that is your choice.  Linux is hackable, but it is harder because root is not enabled.  There are Linux bot networks.

---

### Post by Azvareth on 2009-01-01
Thanks!

I will check out the sudo (-i) command to see if that does the trick.

Perhaps I posted this question in the wrong category, I am sorry for that.

//Azvareth

---

