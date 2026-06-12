---
title: "usb key w/ firefox passwords"
date: 2008-03-28
forum: Security Discussions
---

### Post by derailed1 on 2008-03-28
I am not sure if this is in the right forum but I wanted to know if its possible to have a pam- usb to store firefox passwords.  I already have the pam-usb logging in for me so that is set.

How cool would it be to make strong passwords and have them stored on a secur e usb.  You want to access email, bank accounts, whatever, and all you have to do is plug in a usb.  Once you are done, you pull out the usb and everything is safe.  Id theft is ramped nowadays so every one please be careful.  

So if anyone can direct me in the proper direction I would be more than grateful.  Also, another thing, anyone know how to disable sudo in pam-usb.  I want to log in with the usb key but not hava access to sudo.

---

### Post by derailed1 on 2008-03-31
nobody?  hmmmm can someone tell me if I'm on the right track?

How cool would it be.  You convince your school district to change to open source because they can totally customize computer access for all students with a 5$ usb key stick.  All kids than can have an easy way to transport homework and school related news can be set out with the key further eliminating paper waste.

---

### Post by cdenley on 2008-03-31
I don't think firefox can use pam modules for websites. As you probably know, firefox can remember passwords. I don't think there is a way to change where it saves the passwords, though. It must save them in your profile (~/.mozilla/firefox). What you can do is have your firefox profile physically located on your usb drive. Probably the best way to do this would be something like
```

mv ~/.mozilla/firefox /media/disk/firefox
ln -s /media/disk/firefox ~/.mozilla/firefox

```
You should probably create a static mount point for your usb drive first by editing /etc/fstab, though. I'm not sure what would happen if your usb drive wasn't mounted, since firefox would try to find/create a profile but find a dead link.

---

### Post by netlogic on 2008-04-01
firefox password manager is incredibly weak. many people can crack it by stealing a mozilla profile and do an offline attack. i recommend against it. why don't you use something like keepassX? It supports Twofish and AES.

---

### Post by derailed1 on 2008-04-25
Thanks netlogic.  I will play around with that program.  It looks great.  Now one question, will I be able to save the key information on a usb key and use it from computer to computer?

---

### Post by netlogic on 2008-04-25
> **derailed1 said:**
> Thanks netlogic.  I will play around with that program.  It looks great.  Now one question, will I be able to save the key information on a usb key and use it from computer to computer?

Yes, long as this app is installed on systems you will be using. You can also install the Windows version to your USB key and use it under WINE.

---

### Post by derailed1 on 2008-04-26
Sounds good ;)

Does the autofill function work on all websites?  For example I couldn't get it to log into ubuntuforums.org but I got it work with my ebay account.

Also, to make things clear, the database and key are 2 different files?  I've read the forum at sourceforge but it did not say anything specific.

If this is true than, can I keep those 2 files on a usb flash drive and whenever I need to access bank information I can just plug it in the computer, run keepass that is already installed, and run the files from the usb?  

I think this is fantastic!

---

