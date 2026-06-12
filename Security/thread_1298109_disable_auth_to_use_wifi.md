---
title: "disable auth to use wifi"
date: 2009-10-22
forum: Security
---

### Post by confused_user on 2009-10-22
Hi, since enabling auto logon on 9.04 my ubuntu user logs on automatically which is great.

I'm using a netbook you see and want to avoid any unnecessary typing of fiddly passwords and generally speed up the process of using the netbook.

Anyway, my user logs in automatically (my user is an admin) and i still have to enter my password for it to connect to the wireless lan.  Not the WPA password but my users password - keychain presumably.

so i've skipped the need to enter a password to log on but now ihave to enter one to unlock the key chain so that it can log onto the wlan.

hmmph

i'm not bothered about local security on this thing, it takes seconds to reset the passwords if you have phsyical access anyway.

thanks
cf

---

### Post by undecim on 2009-10-22
I think you need to type your password because wireless keys are encrypted on your netbook.

You might consider installing Wicd to replace the default network manager. I've been using it pretty much since I started using Linux and have never found the need to switch. (Installing it is on of the first thing I do to a new Ubuntu installation)

What's great about it is it will start connecting to preferred networks before you even log in, so by the time you can click that Firefox button, you are connected.

Security is the only disadvantage. If someone steals your netbook, its not hard to get your wireless password from it. (So if your netbook ever gets stolen, change your router password--just in case)

---

### Post by confused_user on 2009-10-23
THanks, i'll try that netman replacement.  hope it supports my 3g modem as well.

i'm really not fussed about local security,only remote access security.  I got this netbook second hand off a mate and it had ubuntu already installed.  Since there is no optical drive i couldnt be bothered faffing around with usb drives to do a fresh install.

My friend didnt give me the password so i just booted up into a root shell from grub and used passwd to change the password.  It literally took seconds.

so in the event of my netbook getting nicked i dont thinkany of my data is safe anyway, no matter how the keychain is configured.

i guess this feature is there to hinder basic users efforts to do things that an admin wouldnt want them doing.  since this is a netbook and not part of a corporate network i'm fine to turn this **** off - if onlyicould

the spelling errors and typos in this post should highlight the frustration i feel when having to type passwords inall the time on this damn small keyboard :)

---

### Post by confused_user on 2009-10-23
oki tried wicd but it does not support my gsm / 3g modem so i went back to gnome net man

you can clear the password to the keychain from the apps menu.  work fine now.

probably a huge risk im taking here but i'm ok with that

---

