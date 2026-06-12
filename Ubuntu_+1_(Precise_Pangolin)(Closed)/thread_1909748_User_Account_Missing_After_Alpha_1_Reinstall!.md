---
title: "User Account Missing After Alpha 1 Reinstall!"
date: 2012-01-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kevpan815 on 2012-01-15
I just had a very weird Alpha 1 Post Installation Issue! After Finishing The Installation, There Was No User Account Present Except The Guest Account! Just FYI.

---

### Post by kevpan815 on 2012-01-15
> **kevpan815 said:**
> I just had a very weird Alpha 1 Post Installation Issue! After Finishing The Installation, There Was No User Account Present Except The Guest Account! Just FYI.

P.S. Please Do NOT Ask Me Why I Choose 2 Stay @ Alpha 1 With Out Installing Any Updates! It Is Due 2 The Fact That I Am Only Allowed 2 Download 12 GB's From My Verizon Wireless Apple IPhone 4 Per Month Before I Am Hit With A $10 For Every 1 GB That I Go Over 4 That Billing Cycle! I Will Upgrade 2 A Newer Build When Alpha 2 (The Next Mile Stone Release) Comes Out! Just FYI.

---

### Post by effenberg0x0 on 2012-01-15
> **kevpan815 said:**
> I just had a very weird Alpha 1 Post Installation Issue! After Finishing The Installation, There Was No User Account Present Except The Guest Account! Just FYI.

Wow :( I'm actually hoping for a Lightdm problem now... As in the login you created during setup was not shown as an option in Lightdm but it was created.

I imagine you probably created a user/password to be able to use the PC. If you did and now have access to login via gnome-terminal, a VT, recovery, etc, did you check these files?
User: cat /etc/passwd | grep -i UserName
Group: cat /etc/group | grep -i UserName

Regards,
EFfenberg

---

### Post by kevpan815 on 2012-01-16
> **effenberg0x0 said:**
> Wow :( I'm actually hoping for a Lightdm problem now... As in the login you created during setup was not shown as an option in Lightdm but it was created.

I imagine you probably created a user/password to be able to use the PC. If you did and now have access to login via gnome-terminal, a VT, recovery, etc, did you check these files?
User: cat /etc/passwd | grep -i UserName
Group: cat /etc/group | grep -i UserName

Regards,
EFfenberg

I am going 2 have a little bit of trouble trying 2 access the files that you just told me to check because my usual account that I use: My First Name, Space, My Middle Name, Space, My Last Name, is completely missing, meaning the only way that I can login right now is through the guest account (which has very reduced privleges), it will not let me access the files that you told 2 check out, in fact I am completely unable 2 access the /user directory, folder, or whatever else you want 2 call it as.

---

### Post by kaldor on 2012-01-16
> **kevpan815 said:**
> I am going 2 have a little bit of trouble trying 2 access the files that you just told me to check because my usual account that I use: My First Name, Space, My Middle Name, Space, My Last Name, is completely missing, meaning the only way that I can login right now is through the guest account (which has very reduced privleges), it will not let me access the files that you told 2 check out, in fact I am completely unable 2 access the /user directory, folder, or whatever else you want 2 call it as.

Switch to a TTY (ctrl-alt-f1) and see if you can log in there. It's a console, but should give you an idea as to whether it's the login screen's problem or not.

---

### Post by kevpan815 on 2012-01-16
No, the login did not work there either, and by the way TTY1 mode crashed only 30 to 60 seconds after lauching it. I should mention that I am still on plain vanilla Alpha 1 with no updates installed due to my Verizon Wireless 12 giga byte data cap with my Apple IPhone 4, and the fact that my parents do not let me hook up Ubuntu to their Comcast connection, which is weird, because they have no problem with me hooking up my Apple Mac OS X Lion computer to it, but when it comes to Ubuntu, they said that they would throw me out of the house if I ever did again hook it up to the Comcast. :-(

---

### Post by xyzzyman on 2012-01-16
Set your mac up as a wifi hotspot. I've used connectify under Windows 7, and a similiar program for Mac is [http://wlanbook.com/personal-hotspot-for-mac-os-download/](http://wlanbook.com/personal-hotspot-for-mac-os-download/). :) Tada!!!!

---

### Post by fabricator4 on 2012-01-16
> **kevpan815 said:**
> and the fact that my parents do not let me hook up Ubuntu to their Comcast connection, which is weird, because they have no problem with me hooking up my Apple Mac OS X Lion computer to it, but when it comes to Ubuntu, they said that they would throw me out of the house if I ever did again hook it up to the Comcast. :-(

That's just paranoid.

Hook up your Mac and download the entire Mirror to a portable hard drive.  You can then use the portable hard drive as your own personal repository on your Ubuntu machine(s).  That'll learn 'em.

You can then just rsync the differences each day.

;-)

Chris

---

### Post by effenberg0x0 on 2012-01-16
Kevpan, one alternative to fix it is to go into recovery mode and run a couple commands.

In case you are not familiar with it: During boot, holding shift shows you grub boot menu options. The second option is (usually) the recovery one. It will boot and eventually ask you what you want to do. You need to go into a root shell, with or without networing, it doesn't really matter. Also make sure the option to mount the partition read/write is selected, so you can make and save changes.

Using this option, you are root with no password. This means that you can look / change any file, run any command. 

If the default user was created during setup, you would find it in the /etc/passwd file. Run the command 
```
nano /etc/passwd
```
It would be specified in a line like this:
```
username:x:1000:1000:username UserSurname,,,:/home/username:/bin/bash
```
Notice that the default user has a UserID (uid) 1000 and GroupId (gid) 1000.
If you look at /etc/group you should also find a group line like this:
```
UserName:x:1000:username
```
And if you look at the directories under /home, the user should have a default home directory at /home/username
```
ls -la /home
```
If the above command show you that, in fact, no user was created, you can use your root privileges to easily create a new user. So, assuming there's no user with uid 1000 / gid 1000, we can do it like this:
```
groupadd -g 1000 username
useradd -m -d /home/username -u 1000 -g 1000 -G username,adm,cdrom,sudo,plugdev,lpadmin,sambashare -s /bin/bash username
passwd username
(enter a new password for the created user)
```
After these procedures, if you check /etc/passwd, /etc/group, you'll see that you have created the default user (uid/gid=1000) and that it has a home under /home/username. 

If you make any mistake, it's easier to remove the user and start over with the command
```
deluser username
```
If the above commands fail, it means uid/gid1000 is taken, which  would mean that the default user/group was effectively created previously during install and we shouldn't be messing with it anyway. But, at any rate, you can create other user/group uid/gid, like 1001, 1002, etc and use it normally.

Everything should be fixed. At this point you can reboot (sudo reboot now) and login with the newly created user.

Users with uid greater than 1000 are listed at lightdm, you should be able to use it to login to the desktop environment.

OBS: This is the fix for the issue. I'm actually more interested in why the installer didn't create a default user/group.
OBS2: Not letting you use the broadband connection via Ubuntu, but allowing you to use a MAC on it is pure nonsense. Investigate xyzzyman tip posted [here]("http://ubuntuforums.org/showpost.php?p=11614784&postcount=7"). Your parents won't even realise that the Mac is operating as a proxy for your Ubuntu PC.

---

