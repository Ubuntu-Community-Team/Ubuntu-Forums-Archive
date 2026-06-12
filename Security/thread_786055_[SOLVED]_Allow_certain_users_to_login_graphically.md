---
title: "[SOLVED] Allow certain users to login graphically"
date: 2008-05-07
forum: Security
---

### Post by wootah on 2008-05-07
Well I have tried searching for this topic, but I believe I am not using the correct terminology--so let me describe what I would like to do.

I would like the ability to only allow a specific group (say, "gnomeusers") the ability to login graphically, BUT have all users still presented with the GDM. Is this possible?

Thus, if I have three accounts: user1, user2 and user3 where user1 and user2 had their groups set as 'gnomeuser' and user3 had its group set as user3 (the default group), user3 would be unable to login graphically, BUT, would still be able to access the console.

Thanks for any insights!

---

### Post by .rdg on 2008-05-09
> **wootah said:**
> Well I have tried searching for this topic, but I believe I am not using the correct terminology--so let me describe what I would like to do.

I would like the ability to only allow a specific group (say, "gnomeusers") the ability to login graphically, BUT have all users still presented with the GDM. Is this possible?

Thus, if I have three accounts: user1, user2 and user3 where user1 and user2 had their groups set as 'gnomeuser' and user3 had its group set as user3 (the default group), user3 would be unable to login graphically, BUT, would still be able to access the console.

Thanks for any insights!

Word of caution before I begin: do a backup of what you're going to change if you follow my instructions. Also - make sure you are able to boot in recovery mode - just in case you're not allowed to login you're going to need to boot in that mode and make the changes back.

Using PAM might be the solution here. You should edit: /etc/pam.d/gdm, which by default has the following:

#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session required        pam_limits.so
@include common-session
session optional        pam_gnome_keyring.so auto_start
@include common-password

Add a line:

account required        pam_access.so

Just after 3 auth lines. Then edit the file: /etc/security/access.conf. In the end add:

- : ALL EXECEPT gnomeuser : ALL

**VERY VERY VERY IMPORTANT:**
Do leave an empty line after the one I gave just now. Without this it will definitely **NOT WORK**.

This is just me guessing and haven't been able to test it yet. Please report back if it gave you the correct result.

---

### Post by wootah on 2008-05-09
Wow. So we are changing the authentication to PAM? What else is happening here?

Also, will this affect any other security? For example, Samba, ssh, etc..

Plus, if you could, would you be able to post information on where you got this?

I'll be able to give it a try later today hopefully, so unless you get a chance to try it out, I'll let you know how things go :D

---

### Post by .rdg on 2008-05-10
We're actually not changing the authentication - PAM framework was built for that and according to what lies in /etc/pam.d gdm *is* using it for that.

You don't have to worry about making changes to /etc/pam.d/gdm file - it won't affect other programs.

As to where I got this - out of my head ;) simple guessing. I wasn't able to check that stuff out, but will tomorrow. If you're affraid there's no problem - just wait, I'll post the info how it went.

If you think about it security-wise keep in mind you have to make your grub secure as well. Short example:

login with init level 3 (multi-user, but console only), then just start X without gdm - boom, user gets his graphical interface.

Anyways - just short post from me, will check back tomorrow with results.

---

### Post by Oldsoldier2003 on 2008-05-12
> **.rdg said:**
> We're actually not changing the authentication - PAM framework was built for that and according to what lies in /etc/pam.d gdm *is* using it for that.

You don't have to worry about making changes to /etc/pam.d/gdm file - it won't affect other programs.

As to where I got this - out of my head ;) simple guessing. I wasn't able to check that stuff out, but will tomorrow. If you're affraid there's no problem - just wait, I'll post the info how it went.

If you think about it security-wise keep in mind you have to make your grub secure as well. Short example:

login with init level 3 (multi-user, but console only), then just start X without gdm - boom, user gets his graphical interface.

Anyways - just short post from me, will check back tomorrow with results.

just a comment about "securing" grub:
Grub and bios passwords are about as secure as locking your car doors and leaving the windows down. For grub all it takes is a live cd or a person in the sudoers file to edit your menu.lst to bypass that "security" Bios passwords are easily reset with physical access to the machine and a few moments of spare time. If your machine has routine physical access by users that you don't trust you already have severe security issues, these are just steps to give you a "warm fuzzy feeling".

---

### Post by wootah on 2008-05-12
Yes very true, all security is lost with physical access to the machine. The only reason I wanted to do this was purely for the "is it possible?".

I suppose I could put my machine in a sealed vault :)

Btw, .rdg, I didn't get a chance to try it out yet--were you able to?

---

### Post by .rdg on 2008-05-13
Sorry for the delay, but was buried with some other stuff. I tried it just now - did a little change to PAM (almost as I did write in the first post) so it's configured like that: /etc/pam.d/gdm

#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
auth    optional        pam_gnome_keyring.so
account required       pam_access.so
@include common-account
session required        pam_limits.so
@include common-session
session optional        pam_gnome_keyring.so auto_start
@include common-password

Next we have the /etc/security/access.conf which is almost identical to what I wrote in first place (I did use a different group name).

After that my brother wasn't allowed to login - gdm told that this was denied by administrator after correct user/password, while my user was able to login with graphical session. So that'd be solved.

As to securing grub/bios - I am aware of that, but it's good you pointed that out. We can't always assume users are just plain dumb and won't overcome our security layers. It's better to know the weak spots so they can be secured additionally.

---

### Post by wootah on 2008-05-13
Much thanks .rdg! I'v been looking for this answer for awhile now, but just recently I decided to post here.

Thanks!

---

