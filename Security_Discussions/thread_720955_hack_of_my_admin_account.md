---
title: "hack of my admin account"
date: 2008-03-10
forum: Security Discussions
---

### Post by rogermacd@gmail.com on 2008-03-10
Just installed Ubuntu on iMac with OS X, ver 10.5.2, with Win XP, sp2.  There has been a new user account created on the Ubuntu partition that has locked me out.  No one has physical access to the machine (unless the  lock to the room was hacked).  I suspect the system was hacked.  Best part is they didn't wait till I start trading forex and get access to my bank accounts.  What to do?

(As an aside, and for background, I' m a complete newbee to Linux,  the impetus to install was M$ message that my product key was no longer valid due to install of VMware windows partition.  The M$ position is that the VMware install counts as another copy of windows.  More of the same wormy bloat...anyways, am in quest to set up multi-monitor Metatrader forex trading setup with Wine, and from what I've experienced so far, Ubuntu is far faster and more reliable.  Will be purchasing Canonical Desktop support shortly and will be glad to share successes with anyone going in the same direction. Chow for now.)

---

### Post by Go_Bucks on 2008-03-10
This is going to sound like a dumb question, and maybe it is, but are you sure you are using the right username and password to log in? What you are describing seems highly improbable if not impossible. Someone would have had to be viewing your keystrokes to see the root username and password you set up when you installed.

---

### Post by Go_Bucks on 2008-03-10
I just discovered this thread. It looks like it should be helpful:

[http://ubuntuforums.org/showthread.php?t=720923]("http://ubuntuforums.org/showthread.php?t=720923")

---

### Post by rogermacd@gmail.com on 2008-03-11
Thanks for the thread. I did the boot into recovery mode, then "passwd {username}"  then system message "password reset successfully", then reboot to normal mode, then the KDE login screen - with my account, and the mystery account: "sabayon user, sabayon-admin", then enter my new password, then get a loop back to the login screen, no system message "login failed", then reboot to recovery mode, repeat "passwd {username}" , then reboot to normal mode, then the same thing, then reboot to recovery mode, then "passwd sabayon-admin", then system message "password reset successfully".....more of the same....in a loop now....

How to delete "sabayon-admin, sabayon user"...

For background, I just moved into a 3 bedroom apt, have TimeWarner cable, and suspect someone has access to the cable box.  One of the roomies is very bright and likes to play games, nasty games at that.

---

### Post by Go_Bucks on 2008-03-11
I don't know this for certain,but it appears those user accounts may be there automatically in KDE. I wasn't clear that you had installed Kubuntu until you just mentioned it... I have never used that.

Check out the following:

[http://search.yahoo.com/search?p=sabayon+user&ei=UTF-8&fr=moz2]("http://search.yahoo.com/search?p=sabayon+user&ei=UTF-8&fr=moz2")

---

### Post by jfinkels on 2008-03-11
Have you or anyone with access to your computer installed or used Sabayon Linux recently?

---

### Post by p_quarles on 2008-03-11
Your system was not compromised. Sabayon is a user management application that you have somehow managed to install. When installed, it automatically creates those accounts.

---

### Post by handydan918 on 2008-03-11
In any case where there is any likelihood of pwnage, reinstall. 
As an aside, this is my beef with the Ubuntu sudo implementation. I like the idea of having a user account with NO sudo privileges for just this reason. Just an additional layer of security, IMO.

---

### Post by Oldsoldier2003 on 2008-03-12
> **handydan918 said:**
> In any case where there is any likelihood of pwnage, reinstall. 
As an aside, this is my beef with the Ubuntu sudo implementation. I like the idea of having a user account with NO sudo privileges for just this reason. Just an additional layer of security, IMO.

thats easily achieved just make the user an unprivileged user. you can also custom tailor sudo rights by group. Really sudo is quite flexible and powerful.

---

### Post by rogermacd@gmail.com on 2008-03-13
Thanks for the input folks.  
Here's the update:
1. did fresh install from ubuntu liveCD.
2. install sabayon from ubuntu install utility.
3. get the same screen with the same problem that I had before...
that is my user account 'roger' will not login, and I can't login with the 
sabayon user account...

What's a newbee to do?  Spent the  last 3hrs on install, gotta go to work now.  Any help for this poor and pitiful newbee is greatly appreciated.

(When i get rich from my Sabayon-Beryl-Ubuntu-Forex-Daytrading setup, I'll make a contribution to your favorite charities)

Chow4Now,
RogerMACD

---

### Post by p_quarles on 2008-03-13
May I ask what you specifically intend to use Sabayon for? I ask only because it sounds as though the package may be broken, and there may be a better/easier way of doing what you are aiming to do. 

In any case, one thing to try here is to reset the password on the primary account. To do this, you would need to boot into "Recovery" mode from the GRUB boot menu (press "esc" right after the BIOS finishes if you don't normally see the menu). Once there, you will have root privileges on the machine. Type:
```
passwd roger
```
You will be prompted to enter a new password for this user. Reboot by typing:
```
shudtown -r now
```
boot as normal, and you should again have access to this account.

---

### Post by jfinkels on 2008-03-14
> **p_quarles said:**
> 
You will be prompted to enter a new password for this user. Reboot by typing:
```
shudtown -r now
```
boot as normal, and you should again have access to this account.

Err,```
shutdown -r now
```

---

### Post by p_quarles on 2008-03-14
> **jfinkels said:**
> Err,```
shutdown -r now
```
Err, yeah. Correctly spelling a command helps quite a bit. ;) Sorry about that.

---

### Post by Dr Small on 2008-03-14
Or simply:
```
reboot
```
:)

---

### Post by rogermacd@gmail.com on 2008-03-14
Thanks again for the input, here's the update:
1. reboot into recovery mode.
2. typed: "passwd roger"
3. typed: "roger"
4. prompted: "password reset successfully"
5. typed: "shutdown -r now"
6. Back to the same screen with the same loop, that is, after entering password, screen returns to the same KDE login screen, with no error message such as: "login failed"

Next thing i may (re)try is the boot from the SabayonLinux-x86-3.4.miniEdition live-cd which i downloaded directly from sabayonlinux.org.  I went with the Ubuntu download because I didn't know what to do with the miniEdition command-line.  Is it possible there is a compatibility issue with Ubuntu and the Ubuntu Sabayon package? 

Any help is appreciated, thanks again.
Rogermacd

---

### Post by p_quarles on 2008-03-14
Sabayon is not the same thing as Sabayon Linux. The first is a user management tool. The second is a Gentoo-based Linux distribution. I think this may be the problem here.

---

### Post by rogermacd@gmail.com on 2008-03-14
Re: what i am attempting to accomplish...
Am setting up forex daytrading platform.  Saw posts that metatrader is running successfully on gentoo and wine.  Saw the compiz and beryl videos on youtube, as well as Chris Pirillo's review of sabayon. And so will try  to set that up.

Don't expect much from Ubuntu forums with forex or daytrading implimentations as there are no posts on forex or daytrading that i could find.  So am shopping for professional support package.  Any suggestions are appreciated.

Thanks again, 
RogerMACD

---

### Post by rogermacd@gmail.com on 2008-03-14
Ok, thanks for the info...how do i disable or remove sabayon user management without wiping the partition, and doing a fresh install?

---

### Post by p_quarles on 2008-03-14
Boot into recovery mode again, and run the following:
```
apt-get remove --auto-remove sabayon
```
You might also need to reset the password again.

---

### Post by rogermacd@gmail.com on 2008-03-16
Thanks for the solution ... "apt-get remove" was able to remove the sabayon user utility so that i could login to ubuntu.


Thanks again,
RogerMACD

---

