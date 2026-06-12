---
title: "Disabling GNOME Keyring Daemon"
date: 2009-10-08
forum: Security
---

### Post by end3rkid on 2009-10-08
What will be the disadvantages of disabling GNOME Keyring Daemon?

I just want to stop Ubuntu asking me for a password everytime tht I logon in order to obtain wireless access.

---

### Post by Agent ME on 2009-10-08
Disabling it is the wrong move. It sounds like your personal keyring's password is different than your account password (when they're the same, it doesn't need to ask you it). Go to Applications -> Accessories -> Passwords and Encryption -> Passwords. Right-click the login keyring, hit change password, and set it to be the same as your account's.

---

### Post by end3rkid on 2009-10-08
It didn't worked because I couldn't change the password :-(. I really want to disable any password authentication because when I try to access to a partition from Windows, it ask me the root password too (that never happened on 9.04 btw just in Karmic).

---

### Post by zoey_s on 2009-11-12
I am having the same problem in ubuntu 9.10.  The keyring wants a password to run evolution.  The password is the same as my login password. I tried removing it from startup applications, but that made no difference.  I find the keyring very annoying and I would like to get rid of it.  Is there anyway to do this?

Thanks, zoey

---

### Post by dwn99 on 2009-11-13
> **zoey_s said:**
> I am having the same problem in ubuntu 9.10.  The keyring wants a password to run evolution.  The password is the same as my login password. I tried removing it from startup applications, but that made no difference.  I find the keyring very annoying and I would like to get rid of it.  Is there anyway to do this?

Thanks, zoey

Not sure, but I do know that when you first install ubuntu, and that first time it asks you for a password for your wireless (which I believe is the default keyring password), if you just leave it blank, then it won't ask you for it in the future.  I don't have time to try it myself, but you might try changing the default key ring password to nothing, and see if that does the trick.

Just a thought.  Good luck.

---

### Post by zoey_s on 2009-11-13
> **dwn99 said:**
> Not sure, but I do know that when you first install ubuntu, and that first time it asks you for a password for your wireless (which I believe is the default keyring password), if you just leave it blank, then it won't ask you for it in the future.  I don't have time to try it myself, but you might try changing the default key ring password to nothing, and see if that does the trick.

Just a thought.  Good luck.

Thank you very much!  It looks like that did the trick.  I discovered that I need the keyring to remember my email password, otherwise, I have to put it in every time I open Evolution, which is as annoying as the keyring!

zoey

---

### Post by Bartender on 2009-11-14
Hey, guys -
I just ran into this keyring thing last night at a friend's house. Since I wasn't familiar with the keyring thing, I clicked "Deny" one time and that worked until I re-booted and had to enter WEP again.  Then I tried typing in my (very simple) sudo password, but it wouldn't accept that.
I'm using Ubuntu 9.04.  It's set up to auto-login.    
Attached is a screenshot of the only entry that shows up in any of the "Passwords and Encryption Keys" windows.  

My password is not "default"  ;)

When it says default, what the heck does that mean?  I'm really nervous about changing this as described by Agent ME.  Can I lock myself out of the machine completely?

---

### Post by Pjotr123 on 2009-11-15
Restart with a clean slate: wipe the current keyring and start a new one. Then leave the password blank (simply click OK and agree to unsafe storage).

Wipe the current one as follows:

Locations - Personal Folder

toolbar: View - Show Hidden Files

Double-click the folder .gnome2

Double-click the folder keyrings

Delete the file default.keyring and / or the file login.keyring

Restart your computer.

---

### Post by Bartender on 2009-11-15
OK, Pjotr -
I want to make sure I've got this right!

When you say wipe the current keyring, this isn't changing my sudo password, right?

I'm just freaking out a little bit here and don't want to blow things up.

I get nervous when I run into a problem that has to be really common but can't find several threads all pointing to the same fix...

P.S.  I'd never gone into that corner of the Home Folder.  Printing this out and stashing in the file cabinet!!

---

### Post by Pjotr123 on 2009-11-15
> **Bartender said:**
> OK, Pjotr -
I want to make sure I've got this right!

When you say wipe the current keyring, this isn't changing my sudo password, right?

I'm just freaking out a little bit here and don't want to blow things up.

I get nervous when I run into a problem that has to be really common but can't find several threads all pointing to the same fix...

P.S.  I'd never gone into that corner of the Home Folder.  Printing this out and stashing in the file cabinet!!

No worries, mate... :) Your sudo password itself, won't be affected.

You only lose your current keyring with all that's in it, being the stored keys of the wireless networks that you've used. Which is only a minor inconvenience.

---

### Post by herdivet on 2009-11-15
Okay, the big question - Are you using AUTOLOGON?  If you are, you have to leave the keyring blank.

It appears that's the problem.  I followed Pjotr123's tip and cleared the whole keyring and rebooted.  It asked for the WEP, got that set, then it asked for the keyring password and I left it blank.  It gave me a pretty severe warning about unencrypted passwords, but let me choose to continue.  The system then asked me to log back in to UbuntuOne and I had to add this laptop to UbuntuOne again.  After a reboot, it started the wireless with no questions asked.

I then decided I didn't want it blank, so I changed it to the default password and rebooted.  It went back to the original action, requesting I enter the password to connect the wireless card.  Hmmm...

I then turned off the 'autologon' to see if that helped.  (System, Administration, Login Screen, Unlock and change to Show the screen for choosing who will login)  It still asked for my password, but I noticed a 'Remember default keyring password when this account logs in' and checked that box (was it always there?  I don't think so.)  The next reboot it worked fine, once I logged in.

So - you have to choose.  If you want autologon with no entries to get the system up and running, you have to set the keyring password to blank.

If you want a keyring password, you have to either login (pressing <enter> for the default logon ID and then the password, and you're done, or use autologon and then enter the password when prompted.

I hope that helps anyone having this problem.

All this was done on Karmic 9.10.  Your mileage may vary.

Bill

---

### Post by izak on 2009-11-18
Thank you for the lucid explanation!

I think this thread should be stickied. This is such a common problem that I have struggled to find a definitive answer for before finding this thread.

---

### Post by Blasphemist on 2011-04-05
I seems like to me that starting the keyring all over might be overkill. I to gave the install my wireless router password but when I get the prompt right after login what it accepts is the same as my login password. I notice that my login password is not the default but rather the second line discussed above is. Under that Passwords: default line are my wireless router (2 lines), ubuntu one, my email and desktopcouch (2 lines).

Is it possible that the right click option on the passwords login of setting it as the default would work?

---

