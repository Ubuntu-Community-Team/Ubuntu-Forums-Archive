---
title: "[SOLVED] Change UMASK Permanently"
date: 2008-03-28
forum: Security Discussions
---

### Post by astabi on 2008-03-28
Hi, I would like to change the UMASK settings for all users permanently.

I read that the Systemwide setting is in /etc/profile, per user settings is in ~/.bash_profile

I also have seen the best place to change this was to use the libpam-umask module, but I don't know how to do this. I installed it but can't find any documentation.

Any help would be appreciated, for now I'm going to experiment with /etc/profile.

Thank You,
Alan

---

### Post by bswilson on 2008-03-29
If you look in the /etc/login.defs file, you'll see why globally setting the umask in that file is not good:

> UMASK usage is discouraged because it catches only some classes of user entries to system, in fact only those made through login(1), while setting umask in shell rc file will catch also logins through su, cron, ssh etc.

I think what you want to do is install **libpam-umask**, which isn't on your system by default.  It's in the universe repository, so make sure you have that configured correctly.  The purpose of this module is to set the umask for **all** successfully authenticated sessions.  The umask that you configure will affect the permissions assigned to newly created files by default.  The main benefit is that unlike setting the umask in /etc/login.defs or in each **and** every user's shell rc file (so that more than just login will be changed), it'll account for all user sessions (and not just login).

---

### Post by astabi on 2008-04-02
Hi, Thank you for your reply! 

So what you're saying is that just by installing **libpam-umask** your umask settings will be remembered if you change it?

I have installed this module but still can't change my umask permanently. Where would I change it with this module installed?

---

### Post by astabi on 2008-04-02
UPDATE:

Well, after some digging I found I need to edit **/etc/pam.d/common-session** and add the line 
[COLOR="Red"]session    optional     pam_umask.so umask=002[/COLOR] where umask=002 is an available option.

Here is a reference:
[http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/sag-pam_umask.html]("http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/sag-pam_umask.html")

Only problem is, It still isn't working!

For instance, I want users with the same group to be able to read and write to the same files & directories. I use the umask=002 option in the line above, I then type in at the prompt "umask" and it returns 0022, not 0002 as I would expect.

Maybe it's working as it should and I just don't know it. Any more help is appreciated!

---

### Post by astabi on 2008-04-04
PAM isn't working as it should. The best solution I can come up with, and it seems to work fine, is to edit** /etc/profile**. I used  a UMASK of 0002. This file changes all users, and a umask of 0002 lets users of the same group edit files.

This gives: DIRECTORY: drwxrwxr-w and FILE: -rw-rw-r--

I used Samba, set up a share with permissions of:create mask = 0774 and directory mask = 0775

I then use write list to give the web authors usernames access.

This allows the me to write a web page, another in my group to edit it. Anyone to view it with a web browser.

If anyone sees something that could have been done better or errors, please say so.

if anyone needs help with setting up a webserver with multiple users writing documents, just ask!

---

### Post by ACGarland on 2008-04-07
Could it be that the PAM module was configuring umask to 0002 as you intended, but then the entry in /etc/profile was overriding the value reverting it to 0022 which you were seeing?  I bet if you commented out the assignment in /etc/profile then the value set via PAM would apply.  Just a hunch.

In any event, if your users will always enter the system in such a way that /etc/profile is executed, then editing the value there will probably serve your purpose.

---

### Post by astabi on 2008-04-07
Hi ! Thanks for the reply. I will try out your suggestion tomorrow.  I'm not sure what ways the users could get around executing /etc/profile though, that's why i'd rather use the PAM module. And for completeness :)

---

### Post by astabi on 2008-04-10
Hey ACGarland, you were right on, it worked just like you said.

I commented out the /etc/profile entry and rebooted, now I see what my umask is and it stays at 0002.

Thanks for your help!

---

