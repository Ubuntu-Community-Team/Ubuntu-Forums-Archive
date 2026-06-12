---
title: "Virtualbox gurus"
date: 2012-06-09
forum: Virtualisation
---

### Post by ExSuSEusr on 2012-06-09
Ok VB gurus... I need some assistance here.

I LOVE Virtualbox. It's an amazing free program, but I am having issues.

I have it running with XP.  I use it for things like iTunes, et al because I just don't want the headache.

Well, World of Warcraft is screwed for Mac/Linux downloads - talking about the downloader here.

So I thought I'd be slick and download it through VB and then just copy and paste the file to my .wine directory... but noooooo... of course it couldn't be that easy.

Looked in my /home.virtualbox  and my Virtualbox directories - of course there aren't directories within (as with wine).

So, I figured that I would just install CD Maker on the virtual machine and just burn a couple of DVDs with the files.... nope.... VB doesn't list my CD ROM in the settings menu.

What do I do?

I want to copy the WoW fold from the VB and paste it in my .wine directory.

---

### Post by QuiGonJinn130 on 2012-06-09
Get Samba going on your Linux box, share the drive on the (V)Windows box, mount the Windows shared drive on your Linux box, and just copy the Dir to Wine.

---

### Post by QuiGonJinn130 on 2012-06-09
Installing Samba:

Step 1
sudo apt-get install smbfs

Step 2
sudo apt-get install smbclient

Step 3
mkdir /media/test

Step 4
sudo mount -t smbfs -o username=myusername //192.168.0.10/sharename /media/test

---

### Post by CharlesA on 2012-06-09
It would be easier to just set up shared folders on the guest.

[https://www.virtualbox.org/manual/ch03.html#idp19152752](https://www.virtualbox.org/manual/ch03.html#idp19152752)

---

### Post by wilee-nilee on 2012-06-09
> **charlesa said:**
> it would be easier to just set up shared folders on the guest.

[https://www.virtualbox.org/manual/ch03.html#idp19152752](https://www.virtualbox.org/manual/ch03.html#idp19152752)

+1

---

### Post by ExSuSEusr on 2012-06-09
Sweet thanks all.... Ubuntu community rocks.

---

