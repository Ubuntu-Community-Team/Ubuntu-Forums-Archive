---
title: "Keyring Initialization"
date: 2009-01-15
forum: System76 Support
---

### Post by cmnorton on 2009-01-15
At the end of configuring Network Manager in 8.10, I am prompted to enter a password for a keyring. I use my own password, thinking the ring is asking for the sudo password, but that's not it. I tried a blank password, and that did not work.

Is there a way to initialize and use the keyring or not to use it at all? Or, is there a default password if keyring has never been used before?

This is a brand new Ubuntu system.

Edit:
---------------------------------------------------
I Googled this problem. It can be fixed if a .gnome2/keyrings/default.keyring exists, but I did not have one. I have not yet solved the problem, but am continuing to look.

Edit 2:
----------------------------------------------------
By creating a default.keyring in 

Applications --> Accessories --> Passwords and Encryption Keys --> Edit --> Preferences 

and adding a default keyring, fixed this problem. After rebooting, I was prompted for the password, which I had set (above), and then was asked if Network Manager could have access to it. I chose always. 

This is still not solved; I would like the default keyring not to prompt me for a password.

---

### Post by jdb on 2009-01-15
> **cmnorton said:**
> At the end of configuring Network Manager in 8.10, I am prompted to enter a password for a keyring. I use my own password, thinking the ring is asking for the sudo password, but that's not it. I tried a blank password, and that did not work.

Is there a way to initialize and use the keyring or not to use it at all? Or, is there a default password if keyring has never been used before?

This is a brand new Ubuntu system.

Edit:
---------------------------------------------------
I Googled this problem. It can be fixed if a .gnome2/keyrings/default.keyring exists, but I did not have one. I have not yet solved the problem, but am continuing to look.

Edit 2:
----------------------------------------------------
By creating a default.keyring in 

Applications --> Accessories --> Passwords and Encryption Keys --> Edit --> Preferences 

and adding a default keyring, fixed this problem. After rebooting, I was prompted for the password, which I had set (above), and then was asked if Network Manager could have access to it. I chose always. 

This is still not solved; I would like the default keyring not to prompt me for a password.

If you can remove the keyring password & get it to the point where its asks you for a new password the first time just hit the return key.
From then on it will store passwords un-encrypted & not ask you for a keyring password anymore.

jdb

---

### Post by thomasaaron on 2009-01-16
Jeesh. I don't get this keyring junk. I wish they'd just ditch it. I've never heard anybody say: "Wow! I sure love Ubuntu's keyring feature!"

---

### Post by cmnorton on 2009-01-17
> **jdb said:**
> If you can remove the keyring password & get it to the point where its asks you for a new password the first time just hit the return key.
From then on it will store passwords un-encrypted & not ask you for  keyring password anymore.

jdb

Of course you will feel guilty -- even if for a small amount of time -- when it warns you everything will be unencrypted. I don't even mind it's there, as much as it would not work the first time.

Also, you should be able to override it for network stuff.

---

### Post by jdb on 2009-01-17
> **cmnorton said:**
> Of course you will feel guilty -- even if for a small amount of time -- when it warns you everything will be unencrypted. I don't even mind it's there, as much as it would not work the first time.

Also, you should be able to override it for network stuff.

Not many applications really use the keyring, wifi & email passwords are the heavy hitters.

The nice thing about it being unencrypted is you can look & see whats there. The file is 
~/.gnome2/keyrings/default.keyring
.

As long as no one has access to your login it is safe from prying eyes.
The permissions on the file are read/write for user only.
I suppose some sort of malware with your (or roots) ownership could access it, but that's the type of thing you find on windoze, not Linux.

Never let a machine make you feel guilty :P

jdb

---

### Post by Bertybulldog on 2009-05-26
This is really getting on my nerves.

I am having to reinput the x million character long wifi key everytime I start the computer. Surely to god they can fix this crap?

If I don't get it sorted this afternoon I going back to windows.

Why is it that every new iteration of Ubuntu has a (different) deal breaker in it? :mad:

---

### Post by miniyak on 2009-05-26
i think this was addressed in another post but if your having the same issue i was having all you have to do is right click on the network icon, choose "edit connections" go to the wireless tab, select your network, click edit, then finally mark the checkbox in the lower left hand corner that says "allow for all users". enter your password in and you should be good. 

It is unfortunate that ubuntu still has a lot of dumb user space issues when it is supposed to the user friendly distro. regardless i think windows is only really usefull for gamers and luddites. i did spend alot less time fixing stuff in windows, but this is because most of the problems were unfixable. lol (note: keyword being "useful" not to offend any windows users)

---

### Post by earrame on 2009-05-26
Hey! I am a Windows user. At work. The honeymoon starts anew everyday when I get home to my Pangolin.:D

> **thomasaaron said:**
> Jeesh. I don't get this keyring junk. I wish they'd just ditch it. I've never heard anybody say: "Wow! I sure love Ubuntu's keyring feature!"

I don't know what a keyring is or what it does. I ignore it and it hasn't bothered me.

Having to input the wifi key happened to me a few times. After the first time I thought this would get old in a hurry. But it didn't persist and it hasn't happened in many months so I never persued corrective action. I've had it on other wifi networks this year as well and it always remembers how to get back on the home wifi.

---

### Post by Sea Lint on 2009-07-08
> **cmnorton said:**
> 

Edit 2:
----------------------------------------------------
By creating a default.keyring in 

Applications --> Accessories --> Passwords and Encryption Keys --> Edit --> Preferences 

and adding a default keyring, fixed this problem. After rebooting, I was prompted for the password, which I had set (above), and then was asked if Network Manager could have access to it. I chose always. 


For those 9.04, the path is: Applications --> Accessories --> Passwords and Encryption Keys --> File --> New --> Password Keyring

Type "default" for the keyring name. Good Luck!

---

### Post by Derath on 2009-07-08
Here's a how-to that was posted in order to get around this:
[http://ubuntuforums.org/showpost.php?p=2776815&postcount=1]("http://ubuntuforums.org/showpost.php?p=2776815&postcount=1")

---

### Post by rebelxt on 2009-07-21
> **Sea Lint said:**
> For those 9.04, the path is: Applications --> Accessories --> Passwords and Encryption Keys --> File --> New --> Password Keyring

Type "default" for the keyring name. Good Luck!

If the "default" name already exists, right-click>delete it first.

---

### Post by epicmaster on 2010-02-27
try using 'admin' as the password

---

### Post by thomasaaron on 2010-03-01
If you go to your home folder and then click Ctrl-H, it will show you all of your hidden files.

Find and double-click the folder entitled .gnome2

Then click on the folder entitled .keyrings

Then delete everything in that folder.

It will give you a fresh start on your keyrings.

---

### Post by nodnolse1 on 2010-08-17
> **jdb said:**
> If you can remove the keyring password & get it to the point where its asks you for a new password the first time just hit the return key.
From then on it will store passwords un-encrypted & not ask you for a keyring password anymore.

jdb

Done, next time i need to log me at ssh server ill see if it work. at the moment thanks

---

