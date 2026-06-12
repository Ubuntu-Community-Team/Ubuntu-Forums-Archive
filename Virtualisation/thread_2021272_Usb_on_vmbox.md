---
title: "Usb on vmbox"
date: 2012-07-09
forum: Virtualisation
---

### Post by marcmeier on 2012-07-09
Hi, All

I've gone through the posts and am still confused.

Host: Ubuntu 12.04, 64-bit
Guest: XP Pro, SP3, 32-bit
Virtualbox 4.1.12 Ubuntu

USB drives don't work, with an error message re "vboxusers".  I've tried "sudo usermod -a -G vboxusers username", with no luck.  All the other help I've seen refers to other vbox/ubuntu combinations.

Any help will be appreciated

---

### Post by Cheesemill on 2012-07-09
You did replace username with your actual username didn't you?

---

### Post by Habitual on 2012-07-09
> **Cheesemill said:**
> You did replace username with your actual username didn't you?

+1 and don't forget to logout|in...

---

### Post by Cheesemill on 2012-07-09
You also need to install the VirtualBox Extension Pack.

[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

---

### Post by marcmeier on 2012-07-09
@cheesemill and @habitual

Thank you and especially for the basics, as virtualisation is all new to me.

I'll check everything this evening, but:

Yes, replaced "username" in the string with my username.  BTW: I've assumed that the username is the host username (although I've tried both)?

Yes, logged in/out.  Perhaps having been off for a while will help.

Yes, have installed the extension pack- vbox shows it as installed.

I notice that the latest vbox is 4.1.18- should I rather install that version?

I can't find any way in 12.04 to edit vboxusers via a GUI, only via terminal and therefore I don't know whether I've succeeded- am I missing something?

Thanks again- forums are great!

---

