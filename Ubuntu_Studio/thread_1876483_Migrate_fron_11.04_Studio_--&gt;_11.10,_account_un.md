---
title: "Migrate fron 11.04 Studio --&gt; 11.10, account unavailable"
date: 2011-11-06
forum: Ubuntu Studio
---

### Post by al1r on 2011-11-06
Hi all,
 
I executed an proposed upgrade from ubuntu 11.04 Studio to the new 11.10.
Update process ran fine and the system rebooted at the end.
It is now impossible to login my account.
When typing my password, i got a message "Failed to load session "Ubuntu" and it comes back to the previous screen asking authentication.
 
I am desesperated, it was working fine before :sad:
What's wrong.
 
PS: Tried other login options
Usually, using Belgian keyboard.
When trying other login option, I saw it was a english keyboard, but typing the password with a english keybord , it won't works anyway.

---

### Post by jejeman on 2011-11-06
Try a different session.

---

### Post by sgx on 2011-11-07
> **al1r said:**
> Hi all,
 
I executed an proposed upgrade from ubuntu 11.04 Studio to the new 11.10.
Update process ran fine and the system rebooted at the end.
It is now impossible to login my account.
When typing my password, i got a message "Failed to load session "Ubuntu" and it comes back to the previous screen asking authentication.
 
I am desesperated, it was working fine before :sad:
What's wrong.
 
PS: Tried other login options
Usually, using Belgian keyboard.
When trying other login option, I saw it was a english keyboard, but typing the password with a english keybord , it won't works anyway.
[http://www.cyberciti.biz/faq/howto-add-new-linux-user-account/](http://www.cyberciti.biz/faq/howto-add-new-linux-user-account/)

this will show how to create a new user account and password.

You can boot into a live cd/dvd and look in your /home/user folder
for .textfiles like .dmrc that have backups next to them, that may have been created by the update, compare, and change them back if it's relevant.

You can log out from the live dvd session, and login again,
but choose from the sessions available, maybe gnome,
kde, lxde, icewm etc When you know what sessions you have
available, you can then find the command to start them from
your main system command prompt
by google search, and looking in /sbin /usr/sbin /usr/bin

/etc/X11/dm/Sessions/   this folder may have sessions icons,
mine has the kde and E17 session icons.

/etc/X11/gdm/custom.conf this file, if it exists in ubuntu,
may need an edit.

If it's all giberish, you can copy desired data by booting
your live dvd, and using a usb harddisk or usb sticks
as copy destinations. Verify the contents of copied folders
that have many nested folders in them. Then do a clean install,
preferably with a separate /home partition, to make things easier
in future installations.
Cheers

---

### Post by al1r on 2011-11-09
Hi folks,
Thanks for your answer.

Jejeman.

I tried, but it exactly the same :(

SGX.
I'll try what you propose...shall come back soon with news.

---

