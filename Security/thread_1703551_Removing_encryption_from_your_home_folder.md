---
title: "Removing encryption from your home folder"
date: 2011-03-09
forum: Security
---

### Post by Dry Lips on 2011-03-09
Hi there!  
 
 I need to do a reinstall (read the details here):
 [http://ubuntuforums.org/showthread.php?t=1703381](http://ubuntuforums.org/showthread.php?t=1703381)
 but I need to be able to access my home directory
 which is encrypted. Is there a way to decrypt my 
home folder, so that I don't get into trouble
 accessing it later on?

---

### Post by bodhi.zazen on 2011-03-09
You can decrypt it from a live CD:

[http://bodhizazen.net/Tutorials/Ecryptfs#Live](http://bodhizazen.net/Tutorials/Ecryptfs#Live)

You can remove the encryption:

[http://rayslinux.blogspot.com/2011/01/caught-out-by-being-overzealous-remove.html](http://rayslinux.blogspot.com/2011/01/caught-out-by-being-overzealous-remove.html)

---

### Post by Dry Lips on 2011-03-09
Hi! Thanks a lot for replying. In the meantime I
found another way around my problem (I think)... 
I just created a new partition and copied the contents
of my home to it. 

I plan to do a reinstall, so the old home will
probably be deleted anyway, but I needed a
backup of my old home directory, and
I haven't got an external HDD...

However, perhaps those two solutions deserves a
a sticky of its own, since I see that this question seems
to be a recurring one? I tried searching the forum,
and those two references you came with seem to be the most
elegant way around this. (I see that there is a reference
to your tutorial in the Ubuntu Security sticky).

I haven't tried to decrypt my home, but I think I'll mark
this thread as solved, though.

---

### Post by bodhi.zazen on 2011-03-09
> **Dry Lips said:**
> Hi! Thanks a lot for replying. In the meantime I
found another way around my problem (I think)... 
I just created a new partition and copied the contents
of my home to it. 

I plan to do a reinstall, so the old home will
probably be deleted anyway, but I needed a
backup of my old home directory, and
I haven't got an external HDD...

However, perhaps those two solutions deserves a
a sticky of its own, since I see that this question seems
to be a recurring one? I tried searching the forum,
and those two references you came with seem to be the most
elegant way around this. (I see that there is a reference
to your tutorial in the Ubuntu Security sticky).

I haven't tried to decrypt my home, but I think I'll mark
this thread as solved, though.

Well, this is the downside of encryption, it makes backups one step more complicated. And then why use encryption if the backups are not encrypted ?

---

### Post by Dry Lips on 2011-03-09
No, wait, I not marking it as solved yet. 
I just found your tutorial on resizing 
encrypted partitions:  
 [http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724)
 That was exactly the next problem I'm  
working on... Do you think it is applicable
 to my problem? I cannot unmount (and
resize) my encrypted partition from Gparted.
 [http://ubuntuforums.org/showthread.php?t=1703381](http://ubuntuforums.org/showthread.php?t=1703381)

---

### Post by Dry Lips on 2011-03-09
> **bodhi.zazen said:**
> Well, this is the downside of encryption, it makes backups one step more complicated. And then why use encryption if the backups are not encrypted ?

The only reason to backup my old home,
was so that I could copy its contents into
the new one... 
But I'm not sure if I'm encrypting my new
home, though... I didn't give it too much
thought when I encrypted my home when
I installed Ubuntu. Perhaps there should be
some information provided about it, in an
installation that is supposed to be idiot-proof...
I am concerned with privacy, but I don't store
state secrets on my HDD. I guess encryption is
most relevant if your computer is stolen? 
I'm sure there are programs around that let
you encrypt a single folder, right?

---

### Post by bodhi.zazen on 2011-03-09
> **Dry Lips said:**
> The only reason to backup my old home,
was so that I could copy its contents into
the new one... 
But I'm not sure if I'm encrypting my new
home, though... I didn't give it too much
thought when I encrypted my home when
I installed Ubuntu. Perhaps there should be
some information provided about it, in an
installation that is supposed to be idiot-proof...
I am concerned with privacy, but I don't store
state secrets on my HDD. I guess encryption is
most relevant if you're computer is stolen? 
I'm sure there are programs around that let
you encrypt a single folder, right?

You might like cryptkeeper, it is in the repos.

---

### Post by Dry Lips on 2011-03-09
> You might like cryptkeeper, it is in the repos. Cheers!
 
 I wrote:
 > I just found your tutorial on resizing 
encrypted partitions: 
[http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724)
That was exactly the next problem I'm 
working on...   I saw your tutorial, but it is probably easier just *deleting* the
 old partitions, since I already have the backup! ;)

---

### Post by bodhi.zazen on 2011-03-09
> **Dry Lips said:**
> Cheers!
 
 I wrote:
   I saw your tutorial, but it is probably easier just *deleting* the
 old partitions, since I already have the backup! ;)

Aye, that tutorial is for LUKS / dm-crypt and does not apply as you are using ecryptfs.

---

### Post by Dry Lips on 2011-03-09
> **bodhi.zazen said:**
> Aye, that tutorial is for LUKS / dm-crypt and does not apply as you are using ecryptfs.
Yeah, I've just found out. Coffeecat had the solution to my problem:
> 
The partition sda2 is not actually mounted but locked because the  logical swap partition inside it is in use by the live CD. Right-click  on sda6, the swap partition, and choose 'swapoff'. Then you will be able  to resize the extended partition sda2.

---

### Post by Dry Lips on 2011-03-10
I was able to resize my partition without any trouble last night.
All the data is intact, but I haven't removed the encryption yet.
I need to think this over, if I really want encryption or not...
However, if I decide to get rid of it, I know which tutorial to 
check out... Now, I'll mark this thread as solved. 

Thank you for your help!

---

