---
title: "truecrypt vs. dm-crypt"
date: 2008-07-19
forum: Security
---

### Post by TheGurke on 2008-07-19
[SIZE="3"]
I have been using Truecrypt for over two years now, mostly for encrypting entire partitions. I started while I was still using windows, and switching to Ubuntu was easy for me since the software is cross-platform.

My trouble started when Truecrypt 5 came out. I thought - yeah, finally a GUI! - and upgraded. However, with version 5 they changed the way Truecrypt used the command line, so I had to rewrite all my scripts. Some time later, I encountered some strange lags with my external hard drive, and after a while I managed to track down the problem to Truecrypt. I do not know the specifics of this bug, but after a downgrade (and another alteration of my scripts) the problem was gone.

So long until April when Hardy Heron came out. After upgrading I realised that there was no version 4 compiled for this release (as of that time). Since I generally do not like compiling from source and all the hassle that is associated with it, I had no choice but to stick to version 5. Luckily 5.1a was out and my former bug was fixed.

And what is the deal anyway with the Truecrypt people failing to provide a license that is recognized by the FSF as free and open source software? This way I am unable to install it via the repositories and have to download every version by hand whenever I reinstall.

Plus, when you use a Truecrypt volume as a home drive, it does not unmount cleanly (even with Truecrypt running), it just gets killed on every shutdown, so the last thing you see is a bunch of journaling error messages. But since ext3 is a pretty solid file system, I never had any problem with that. Nevertheless, not very nice behaviour.

So I was living with the software again for some time until for some weird reason it destroyed my external hard drive: After copying more than 100GB of data I decided to run a backup, which caused my computer to throw all kinds of strange error messages and finally crash. After a reboot the drive was unmountable, my suspicions were an overwritten Truecrypt header. My fault for not making a header backup.

Still that kind of pissed me off, but since I can't reproduce the error or prove that it was Truecrypt's fault I can't file a bug report or anything. At that point I seriously considered moving to dm-crypt, which I have been planning for a while now.

I have always had a problem whenever I copied files, my system practically froze until it was finished. The hard disk light showed me constant hard disk access, while 7GB of a few files took more than 20 minutes to copy from an unencrypted external drive. First I though that it was a bug in gnome and was looking forward to the new copying backend in Hardy. However, nothing changed.

As of this month, after moving to dm-crypt everything works flawlessly, plus copying is about 5 times faster now, even from an encrypted drive to another encrypted one. And the journaling errors are gone as well.

Maybe this helps anyone, who considers Truecrypt as a possibility for disk encryption under Linux. Yes, it has a GUI and dm-crypt does not (which is just a matter of time until someone will write one), but for Linux the Truecrypt GUI sucks as well as there is no good integration into the desktop and more importantly, you can't create ext3-formatted drives. So my recommendation is to avoid Truecrypt at all costs. Dm-crypt works very nicely, is better integrated with Linux and a lot faster, it supposedly even has a windows implementation.
[/SIZE]

---

### Post by kevdog on 2008-07-19
The size of your font in the above thread kind of P***ed me off!  Other than that your information seems to be a valid testimonial.

---

### Post by sonicb00m on 2008-07-20
I've also used Truecrypt because it was cross platform and had a lot of trouble with it too.

However, the latest version 6 seems to be a major improvement. The only thing I haven't tested is shutting down the pc with the volumes still mounted since it always ended up making errors on the drive, something older versions never used to do.

I will take a look at this DM crypt if TC continues to piss me off but so far so good.

It's fairly easy to make a tc container ext3 but obvioulsy not from the GUI. I wish they would take their linux version more seriously though.

---

### Post by hyper_ch on 2008-07-20
TC works really nice on usb thumb stick...

---

