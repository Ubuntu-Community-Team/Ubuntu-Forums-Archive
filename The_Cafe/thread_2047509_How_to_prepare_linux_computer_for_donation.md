---
title: "How to prepare linux computer for donation?"
date: 2012-08-25
forum: The Cafe
---

### Post by charbo on 2012-08-25
Hi All,

I am interested in donating some of my computers.
What do you suggest I do in preparation?

In particular
- What would be the best way to wipe the HDD contents?
- Would it be best to donate without Linux on, or should I fresh install?
- If it is better to install Linux before donating, what types of users should I create? Any convention? I was thinking "Administrator" or something as the sudoer. What do vendors do when selling a new computer with Linux on?

Any suggestion is highly appreciated.
Thank you very much!

---

### Post by MG&amp;TL on 2012-08-25
> **charbo said:**
> Hi All,

I am interested in donating some of my computers.
What do you suggest I do in preparation?

In particular
- What would be the best way to wipe the HDD contents?
- Would it be best to donate without Linux on, or should I fresh install?
- If it is better to install Linux before donating, what types of users should I create? Any convention? I was thinking "Administrator" or something as the sudoer. What do vendors do when selling a new computer with Linux on?

Any suggestion is highly appreciated.
Thank you very much!

-Give everything inside a (gentle!) clean-out. Don't want it getting too hot for the new owner through too much dust.

-I suggest using Darik's Boot and Nuke (DBAN) for HDD wiping. Obviously, backup your data first.

-Yup, I suggest installing Linux. Make sure you choose one that runs relatively fast and that it's up-to-date, otherwise the user may become frustrated.

-I don't know about users, but system76 I believe do something where it comes with Ubuntu pre-installed, but without a configuration, so at first boot it asks all the stuff it normally does in the install (where you are, username, password, etc.). If you can find out how they do that, that would be good. 

-I would also suggest getting Flash and DVDs working.

Kudos for donating, rather than throwing away.

---

### Post by Linux_junkie on 2012-08-25
The only secure way of removing data from a hard disk that you don't want someone else to have access to is to destroy the disk and insert a brand new disk.  Otherwise, just use dBAN to overwrite the entire disk.

To set up Linux for a new user it is best to set it up as a OEM that way when the new user switches it on for first time it will display an icon on the desktop to setup a user account.

---

### Post by black veils on 2012-08-25
new user install: 

[http://askubuntu.com/a/36673]("http://askubuntu.com/a/36673")


EDIT: 
also this is what you want!  [http://askubuntu.com/a/157821]("http://askubuntu.com/a/157821")

---

### Post by coldraven on 2012-08-25
> **black veils said:**
> new user install: 

[http://askubuntu.com/a/36673](http://askubuntu.com/a/36673)


EDIT: 
also this is what you want!  [http://askubuntu.com/a/157821](http://askubuntu.com/a/157821)

Well like many others, I didn't know about the OEM mode. Thanks

---

### Post by Lars Noodén on 2012-08-25
OEM installation is the way to go.  You'll find it when you first boot the installation CD/DVD and press F4 for Modes.  There you'll see "OEM install (for manufacturers)"  That will let the first user set username, passwords and so on the first time the computer is started.

---

### Post by mastablasta on 2012-08-25
> **Lars Noodén said:**
> OEM installation is the way to go.  You'll find it when you first boot the installation CD/DVD and press F4 for Modes.  There you'll see "OEM install (for manufacturers)"  That will let the first user set username, passwords and so on the first time the computer is started.

can you check if install installed correctly without setting the first password?

i mean you install it and then you need to verify in some way that is all works good and that all necessary things that user might need are installed well (codecs, MS fonts...)

---

### Post by Lars Noodén on 2012-08-25
I don't know of a way to test it without actually logging in as a first-time user.  You may have to walk through the installation a few times before you get it the way you want.

---

### Post by black veils on 2012-08-25
> **mastablasta said:**
> can you check if install installed correctly without setting the first password?

i mean you install it and then you need to verify in some way that is all works good and that all necessary things that user might need are installed well (codecs, MS fonts...)


look at the second link i posted.

---

### Post by mamamia88 on 2012-08-25
> **mastablasta said:**
> can you check if install installed correctly without setting the first password?

i mean you install it and then you need to verify in some way that is all works good and that all necessary things that user might need are installed well (codecs, MS fonts...) you could install mint which has that stuff preinstalled. But, ubuntu makes it super easy to install that stuff if you don't have it.  The first time the user tries to do something that requires a codec it will inform the user then install it.

---

### Post by Buntu Bunny on 2012-08-25
Great question and excellent answers! I'm needing to know this myself.

---

