---
title: "home directories readable by everybody by default"
date: 2005-05-02
forum: Server Platforms
---

### Post by nutubu on 2005-05-02
If I create accounts for people on my computer, by default, they all will be able to read each others home folder and this include mine, the first user who is supposed to be the administrator in control of the machine.

I was used to Red Hat policy where home folders are protected by default from Peeping Toms.

Any comments on this?

---

### Post by Professor X on 2005-05-02
I'm pretty sure the idea of having world readable home dirs is that it encourages file sharing.  I fail to see how this is much of a security concern.  If it's a privacy concern, then changing file permissions is easy enough.

---

### Post by jdong on 2005-05-02
It's always a good idea to go through your own account by hand and harden it down, both using chmod on current files and by using umask to set permissions on newly created files.

---

### Post by Alexander Kirillov on 2005-05-02
[QUOTE=nutubu]If I create accounts for people on my computer, by default, they all will be able to read each others home folder and this include mine, the first user who is supposed to be the administrator in control of the machine.

I was used to Red Hat policy where home folders are protected by default from Peeping Toms.

Any comments on this?[/QUOTE]
 Yes, this is intentional policy. However, really important files (such as .ssh which cotains your ssh keys) have more restrictive permissions. And, of course, it is easy to change default permissions for your home directory.

---

### Post by nutubu on 2005-05-02
[QUOTE=Professor X]... I fail to see how this is much of a security concern.  If it's a privacy concern, then changing file permissions is easy enough.[/QUOTE]

Well, on my system all those important plain text passwords I've gathered over the years in ~/passwords.txt sure need some privacy! :)

I know changing permission is easy. It's just that after years of working on Red Hat, Unixes and even Windows systems where the home directory is not world readable by default, it was just not my first reflex to go fix this right away. :)

Am I alone to think it's not the best default policy?

---

### Post by HungSquirrel on 2005-05-02
[QUOTE=nutubu]Am I alone to think it's not the best default policy?[/QUOTE]
No.  I agree with you completely.

---

### Post by nutubu on 2005-05-02
Thanks. I was about to fork this whole Ubuntu thing. :)

---

### Post by Professor X on 2005-05-02
> Well, on my system all those important plain text passwords I've gathered over the years in ~/passwords.txt sure need some privacy!  

What's wrong using a chmod on passwords.txt?  In fact, you should do this regardless of the permissions on /home.


> I know changing permission is easy. It's just that after years of working on Red Hat, Unixes and even Windows systems where the home directory is not world readable by default, it was just not my first reflex to go fix this right away. 

The default on Unix as well as BSD has always been world readable home dirs.  Red Hat is an exception to the rule.

---

### Post by crmanski on 2005-05-02
I was surprised by this also.  I've recently changed over 3 of my 4 home machines over to hoary.  Mine runs as more or less in a server role and my kids will save stuff to their home directories (I handle backups).  I was surprised when I could get into any of the home directories when I was in the middle of setting things up when on one of the other machines. I did not expect to be able to read my home directory from a "limited" account.  Besides manually changing this is there a way to change the default bahavior for new users?  I like the way MacOSX has everything locked except the public folder.

---

### Post by nutubu on 2005-05-02
[QUOTE=Professor X]
The default on Unix as well as BSD has always been world readable home dirs.  Red Hat is an exception to the rule.[/QUOTE]

Sorry, I've never been sysadmin on any of the Solaris systems I used to know for sure the default behavior but I remember that in all cases home directories were not world-readable. I guess in each case the sysadmin fixed the default.

Nowadays, having as many layers of security/privacy as possible by default is good. Having to go through a list of things to harden your system after each fresh install is no fun. New users with little or no knowledge must be taken care of. All sound measures to have a top notch system should end up in the defaults.

I guess I am being overzealous. :) Oh, please forgive me :)

---

### Post by Professor X on 2005-05-02
Well I'm glad you brought this up as it is something new users should know about.  Most admins I have known do change the default so that people's home dirs aren't world readable.  I still say that this is a privacy issue, not a security one, and is best solved by going through personal files and changing permissions on files you don't want others to access.  It's all good though.  :)

---

### Post by LordHunter317 on 2005-05-05
[QUOTE=Professor X]I still say that this is a privacy issue, not a security one, and is best solved by going through personal files and changing permissions on files you don't want others to access. It's all good though. :)[/QUOTE]And you'd be absolutely correct.

Users are responsible for their own permissions.  If you don't want something else to be read, make sure there is no group or world access.

In the old days, not everyone had their own group, so you had to do this anyway.

Anyway, to prevent this by default for newly created users, all you should have to do is edit /etc/adduser.conf and set DIR_MODE to 700.

---

### Post by kosmic on 2005-05-07
Just change the Umask from 022 to a more restrictive way and where you goe every acount you create will have the new umask

---

### Post by LordHunter317 on 2005-05-07
What? That doesn't make sense. You could change the system wide umask in /etc/login.defs and in the appropriate shell resource files, but that won't solve the original problem.

---

### Post by Professor X on 2005-05-07
Security for the paranoid...

change the line 'umask 022' in your /etc/profile to 'umask 777'.  Now no one has permission to mess with your new files (including you :grin:).

---

### Post by RastaMahata on 2005-05-07
I guess people should be able to hide their files from other users on the same machine by default. And with the click of a right mouse button, be able to set the permissions of the sub home folders (thats it, "~/.") in an easy way.

And the public folder is a great idea :)

---

