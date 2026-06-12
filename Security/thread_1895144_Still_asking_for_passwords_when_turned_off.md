---
title: "Still asking for passwords when turned off"
date: 2011-12-14
forum: Security
---

### Post by erlendsp on 2011-12-14
Hi, 

I've got an issue here (Oneiric)... On my admin user (the only one I've  set up and intent to keep using) I've gone into the user settings and  opted not to use a password. However, I'm still being asked for a  password every time I try to use a sudo command, install applications or  packages. ...except when I try to enter it my old password doesn't work,  and neither does leaving the field blank. 

Any ideas on how to get past this? I've tried changing it back to using  a password in the user settings, but I need a password just to unlock  the settings for editing and even if I got past that I'm assuming it  would ask me to enter old password to create a new one just to be extra  uncooperative. 

Thanks in advance for any reply!

---

### Post by BC59 on 2011-12-14
> **erlendsp said:**
> Hi, 

I've got an issue here (Oneiric)... On my admin user (the only one I've  set up and intent to keep using) I've gone into the user settings and  opted not to use a password. However, I'm still being asked for a  password every time I try to use a sudo command, install applications or  packages. ...except when I try to enter it my old password doesn't work,  and neither does leaving the field blank. 

Any ideas on how to get past this? I've tried changing it back to using  a password in the user settings, but I need a password just to unlock  the settings for editing and even if I got past that I'm assuming it  would ask me to enter old password to create a new one just to be extra  uncooperative. 

Thanks in advance for any reply!

The change you like to do is a serious security violation.

---

### Post by erlendsp on 2011-12-14
How is that? There's a "user settings" section of the system settings and it has an option for whether to use a password or not. How is that a violation of anything and, moreover, why do everyone here seem so reluctant to tell users how to breach security on their own machine?

Anyway, never mind. I don't care that much about getting rid of my password. If anyone knows why it's still asking for one when I've supposedly turned it off or how I can turn it on again then that's as good as anything really!

Thanks.

---

### Post by jeremywc on 2011-12-14
You came to a security forum and asked for assistance practicing poor security. You're probably not going to get much help. You should be using a password for system administration functions. Otherwise it makes it entirely too easy to compromise your computer.

EDIT: This isn't a Linux or Ubuntu thing, BTW. You shouldn't do this on ANY operating system.

---

### Post by BC59 on 2011-12-14
> **erlendsp said:**
> How is that? There's a "user settings" section of the system settings and it has an option for whether to use a password or not. How is that a violation of anything and, moreover, why do everyone here seem so reluctant to tell users how to breach security on their own machine?

Anyway, never mind. I don't care that much about getting rid of my password. If anyone knows why it's still asking for one when I've supposedly turned it off or how I can turn it on again then that's as good as anything really!

Thanks.

From System Settings-->User Accounts you changed to -Off the Automatic Login, means when booting, there is no login screen prompting for password. There is not existing option for suppressing your root password.

---

### Post by erlendsp on 2011-12-14
Thanks for your replies, but I think you're missing the point here. I take full responsibility for my own system, and I understand that the option I changed was for the login screen (which I was never prompted to enter before I changed the setting either by the way). Sorry if I seem a bit blunt, I may not have expressed my issue properly. My problem is this:

- My previous password no longer works when I try to install software, updates etc.

- I can not put my password back on because I'm prompted to put in my old one... which doesn't work.

These are the problems I'm having. Anyone have any ideas how to fix this?

---

### Post by BC59 on 2011-12-14
In that case try to follow the instructions from here:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

This works only if you can access the Grub screen in the startup.
Usually you can see it if you hold down the shift during boot.

---

### Post by jeremywc on 2011-12-14
Before going that far, have you tried just opening up a terminal window and typing "passwd"? I just created a dummy admin account with no password and was able to assign it one by doing that.

---

### Post by erlendsp on 2011-12-14
jeremywc: you're a genius!

Tried the whole recovery mode thing but it just said "password unchanged", but your trick worked like a charm! Thanks a lot!

Now that I have you here though, is there any way to automatically unlock my keyring upon login? I'm completely fine with using a password to perform admin tasks, but that keyring thing is just slowing down my startup by not showing up until about 30 seconds after I'm already logged in. Any idea?

Edit: Nevermind, found it!

Thanks all!

---

