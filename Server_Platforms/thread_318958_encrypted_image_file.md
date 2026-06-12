---
title: "encrypted image file ?"
date: 2006-12-14
forum: Server Platforms
---

### Post by zpro on 2006-12-14
okay, on the Mac, I could make a encrypted image file with AES 256, and enter a password, set the size 2 - 4GB it would create a image file, and would NOT MOUNT it,
until I enter the password correctly, the you could add folder and files.. and whatever
to the image.

--
NOW, is there anything like that for ubuntu.
I work on allot of clients projects, so once I am done, I would unmount the image file.

TKS ++
:-k

Edgy 6.10

---

### Post by joey_joe_joe on 2007-09-29
I am looking for a solution to the same problem.

I found a good tutorial here [http://www.hackszine.com/blog/archive/2007/06/howto_disk_encryption_in_linux.html]("http://www.hackszine.com/blog/archive/2007/06/howto_disk_encryption_in_linux.html"), but when i mount the disk, it is read only. also tried mounting with read-write option, and uid and gid = me, but still cant modify any files.

does anyone have any suggestions on this please?

thanks.

---

### Post by HermanAB on 2007-09-29
There was a system called cryptoloop, which was broken a year or so ago.  It has now been replaced by dm-crypt: [http://www.saout.de/misc/dm-crypt/](http://www.saout.de/misc/dm-crypt/)

Since dm-crypt is somewhat new, there is still a lack of nice wizards for it.

Note that the previous post refers to the broken cryptoloop.  Don't use it.  It is better than nothing, but not much better than nothing, since the crack tools are out there.

Cheers,

Herman

---

### Post by stmurray on 2007-09-30
I have been a fan of Truecrypt ([www.truecrypt,org](www.truecrypt,org)) in the Windows world.  I am new to Ubuntu, but it looks to me Truecrypt is not part of the ubuntu multiverse (Truecrypt is free and open source, but it's licensing may contradict the Ubuntu philosophy in some way...)  I know Truecrypt does support linux and it should do what you are looking for. 

Sean T Murray

---

### Post by HermanAB on 2007-09-30
Talk to this guy, he just got it to work with dm-crypt:
[http://ubuntuforums.org/showthread.php?t=561041](http://ubuntuforums.org/showthread.php?t=561041)

---

