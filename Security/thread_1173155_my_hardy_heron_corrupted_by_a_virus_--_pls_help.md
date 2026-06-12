---
title: "my hardy heron corrupted by a virus -- pls help"
date: 2009-05-29
forum: Security
---

### Post by lensark on 2009-05-29
i am working on my thesis now, used every resources I could find on the net, got several emails from here and there and just yesterday got a reply and it had a attachment file, opened it and there, my hardy began acting weird.

first i noticed my firefox got corrupted, then next is my xchat(but still working). worst was my shutdown function is no longer available, when i go system->pref->quit the window just freezes.

panicked, i went straight ahead to irc.freenodes.net #ubuntu and asked several ppl in there. one person got me directed to system->preferences-> sessions, but after clicking it just loads but doesn't finish and disappears.....


all help is really appreciated. please help me with this......

---

### Post by lensark on 2009-05-29
by the way i am in #ubuntu irc.freenode.net right now under l3ns nick....

---

### Post by cdenley on 2009-05-29
Could you post the attached file? Assuming you did run something malicious, it probably only corrupted your home folder. Try creating a new user account. Have you simply rebooted?

---

### Post by rookcifer on 2009-05-29
> **lensark said:**
> i am working on my thesis now, used every resources I could find on the net, got several emails from here and there and just yesterday got a reply and it had a attachment file, opened it and there, my hardy began acting weird.

first i noticed my firefox got corrupted, then next is my xchat(but still working). worst was my shutdown function is no longer available, when i go system->pref->quit the window just freezes.

panicked, i went straight ahead to irc.freenodes.net #ubuntu and asked several ppl in there. one person got me directed to system->preferences-> sessions, but after clicking it just loads but doesn't finish and disappears.....


all help is really appreciated. please help me with this......

Not a virus.  Since you opened this "attachment" as a normal user (Ubuntu does not enable a root account), this means even if it were malware (doubtful) it would only affect your home directory.  Try deleting the attachment you downloaded, it has to be in your /home directory somewhere.  It can't go anywhere else (except perhaps /tmp).  If you can't find anything, then just reboot and see if the issue continues.

---

### Post by Keithhed on 2009-05-29
If you suspect a virus.  run a virus scan.  but without root privelages a virus is dead in the water on linux

---

### Post by Chayak on 2009-05-30
I would like to see a copy of this attatched file.  I'm a malware analysist. I've seen malicious scripts and worms but I've yet to see anything that does what you're describing.  It's not impossible to have malware on linux just very unlikely and I've yet to see any of real note.

---

### Post by lensark on 2009-05-30
I got it from email. I now installed vista, and will try to download ubuntu again because downloading function is also corrupted. Every reboot new problem arises so I figured out just install vista asap and get fresh install of ubuntu. I lost my ubuntu cd. 

The file is still in my email. "feedback.vcf" is the name of the file. I got it from this site: [http://mindprod.com/contact/roedy.html](http://mindprod.com/contact/roedy.html)

What do you want me to do with it?

---

### Post by Hyper Tails on 2009-05-30
If you have wine on your ubuntu system, you should have a virus scann for that too because some viruses for windows will run in wine so I recommend clamtk

[http://clamtk.sourceforge.net/](http://clamtk.sourceforge.net/)

---

### Post by lensark on 2009-05-30
I also tried creating a new account and try loggin-in on that account but it did not let me.

---

### Post by nandemonai on 2009-05-30
> **lensark said:**
> I got it from email. I now installed vista, and will try to download ubuntu again because downloading function is also corrupted. Every reboot new problem arises so I figured out just install vista asap and get fresh install of ubuntu. I lost my ubuntu cd. 

The file is still in my email. "feedback.vcf" is the name of the file. I got it from this site: [http://mindprod.com/contact/roedy.html](http://mindprod.com/contact/roedy.html)

What do you want me to do with it?

A .vcf file is a vCard. Essentially a electronic business card. I've never heard of one doing any damage to Windows let alone Linux.

I highly, highly doubt it had anything to do with the issues you were experiencing.

---

