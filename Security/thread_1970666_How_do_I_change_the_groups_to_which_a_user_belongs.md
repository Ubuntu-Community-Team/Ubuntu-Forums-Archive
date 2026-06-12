---
title: "How do I change the groups to which a user belongs?"
date: 2012-05-01
forum: Security
---

### Post by Paddy Landau on 2012-05-01
In Natty and previous versions, there was a Users and Groups settings dialogue to let me view and change groups, and the groups to which users belonged.

However, in Precise, there is only a simplified Users settings dialogue.

How do I manipulate groups in Precise?

---

### Post by Morbius1 on 2012-05-01
2 choices:

Old-school:
```
sudo gpasswd -a user-name group-name
```The beloved Gnone2-ish version:
```
sudo apt-get install gnome-system-tools
```It's in that Dash thingy as "Users and Groups"

---

### Post by Paddy Landau on 2012-05-01
Thank you!

---

### Post by cknowles on 2012-05-12
I agree that the original question has been "solved" but I'm very concerned that Ubuntu (canonical?) keeps stripping out functionality and calling it an "improvement".

Yes, we can use the command line tools, or even hand edit /etc/group - But back in the last LTS release, and even a couple after that we still had the defult GUI tools in there to do this.  

CJK

---

### Post by Paddy Landau on 2012-05-12
> **cknowles said:**
> I agree that the original question has been "solved" but I'm very concerned that Ubuntu (canonical?) keeps stripping out functionality and calling it an "improvement".
I don't think Canonical calls it an improvement. I think Canonical has two limitations it is worried about:

[LIST=1]
[*]It needs to keep the image small enough to fit onto a CD, and it is struggling. I believe that lay behind the decision to remove GIMP from the default installation. However, it keeps the packages available on the repositories.
[*]Canonical is trying to aim the system towards the "average" (i.e. not computer-literate) user. The idea is that someone who needs to use the advanced features (such as me) knows how to ask for help.
[/LIST]
I do agree that there may be some controversy about *which* packages to exclude. When CD's go the way of floppies, we can put the images onto DVD. Until then, we will continue to have contention over included packages.

---

### Post by Morbius1 on 2012-05-12
I actually have a different viewpoint - not that anyone's asked :wink:

If I create a new user with Gnome3's "User Accounts" utility and make him a "Standard" user it does just that. It creates a user account, sets up the home directory, and makes the user a member of the following groups:
> ~$ id tester1
uid=1001(tester1) gid=1002(tester1) groups=1002(tester1)If I use the old "Users and Groups" and make him a "Desktop User" it does what "User Accounts" does but it also makes the new user a member of the following groups:
> ~$ id tester1
uid=1001(tester1) gid=1002(tester1) groups=1002(tester1),4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),30(dip),44(video),46(plugdev),104(fuse)One can do a whole lot more than the other. Now maybe you want that to happen so you as the administrator can have more control over exactly what that user can do. But the only tool you've provided the Administrator by default is the terminal.

---

### Post by Paddy Landau on 2012-05-12
> **Morbius1 said:**
> One can do a whole lot more than the other. ... But the only tool you've provided the Administrator by default is the terminal.
You raise a good point. I suppose you can raise this as a regression bug.

---

### Post by Morbius1 on 2012-05-12
I don't think this is a regression. It's a design flaw. It's not Ubuntu's fault it's Gnome's.

I have to admit though that 12.04 is getting me down. And I'm using Xubuntu 12.04 where this particular thing isn't an issue because the old "Users and Groups" is installed by default. There's a bug in Samba ( [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/967410](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/967410) ) that ... Sorry, I digressed :oops:

---

### Post by Paddy Landau on 2012-05-13
> **Morbius1 said:**
> I have to admit though that 12.04 is getting me down...
I must agree that 12.04 has been released with plenty of bugs.

Since installing, I have: raised 8 queries that have been resolved; raised or joined 8 confirmed bugs; submitted 1 unresolved question; and have another 4 as-yet-unraised questions.

A total of 21 issues!

Hmm....

Methinks the quality standards are slipping in the rush to get Ubuntu's Unity, TV and Android out there. I hope from here, Canonical pays more attention to quality and less to innovation, at least for a couple of releases.

---

### Post by cariboo on 2012-05-14
Users & Groups is still available in Precise, it just ins't installed by default. You can install it by installing the gnome-system-tools package, then accessing it from the dash by searching for users. See the screenshot. 

If you want it included in the default installation, I'd suggest you create a feature request bug.

---

### Post by Morbius1 on 2012-05-14
> **cariboo907 said:**
> Users & Groups is still available in Precise, it just ins't installed by default. You can install it by installing the gnome-system-tools package, then accessing it from the dash by searching for users. 
As I said in post#2 :wink:

---

