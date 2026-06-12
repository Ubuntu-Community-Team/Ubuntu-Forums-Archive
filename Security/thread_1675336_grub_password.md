---
title: "grub password"
date: 2011-01-25
forum: Security
---

### Post by RegUB on 2011-01-25
Tried in General help but no response so trying here...

I have added the "password --md5 ...." directive before each of the "title" directives in my menu.lst, to prevent unauthorised people from adding/amending parameters on the kernel command line. This works fine.

However, at start-up if I select the first item in the list, it also enforces the password to be entered before it will boot. I have tried changing the order of the entries, and it is always the first one which requires the password.

I know this behaviour can be forced by inclusion of a "lock" directive, but my menu.lst does not have this - so why is it requiring the password before it will boot?

---

### Post by Kirboosy on 2011-01-25
Did you put the password MD5 above the "###BEGIN AUTOMAGIC KERNEL LIST"? 

That should be the only place that line is placed...

Also when you edit anything about GRUB you always need to run
```
sudo update-grub
```

Hope that helps,
Caboose

---

### Post by RegUB on 2011-01-25
thanks, that has fixed it.

---

### Post by Kirboosy on 2011-01-25
Anytime. Glad it was any easy fix.

---

### Post by muralysunam on 2011-07-25
[SIZE=3]I found to two posts of about grub password. But I dont get a good answer for my problem.
I want to block strangers from passing through Grub menu.
My /boot/grub/menu.1st is shown below[/SIZE]

Edit: bodhi.zazen - removed a  lengthy grub.conf


Now the password protection is not working. What should I need to do for  preventing others from accessing grub or OS. I need to ask a password  when we press enter in grub menu. [SIZE=4]_**Please Help. **_[/SIZE]
[SIZE=3]
Thanks for anyone who helps[/SIZE]

---

### Post by bodhi.zazen on 2011-07-25
> **muralysunam said:**
> [SIZE=3]I found to two posts of about grub password. But I dont get a good answer for my problem.
I want to block strangers from passing through Grub menu.
My /boot/grub/menu.1st is shown below[/SIZE]

Edit: bodhi.zazen - removed a  lengthy grub.conf


Now the password protection is not working. What should I need to do for  preventing others from accessing grub or OS. I need to ask a password  when we press enter in grub menu. [SIZE=4]_**Please Help. **_[/SIZE]
[SIZE=3]
Thanks for anyone who helps[/SIZE]

First, please use the default font size and text when posting.

Second, please do not post on other , old threads, start your own.

Third , please do not post long configuration files like that, use attachments or post only the relevant section. As yours looked like the defaults, it did not add much beyond length to your post.

Fourth see ;

[https://help.ubuntu.com/community/Grub2#Preventing%20booting%20via%20Grub%20command-line](https://help.ubuntu.com/community/Grub2#Preventing%20booting%20via%20Grub%20command-line)

[http://ubuntuguide.net/how-to-setup-boot-password-for-grub2-entries](http://ubuntuguide.net/how-to-setup-boot-password-for-grub2-entries)

Or fall back to grub 1 ;)

---

