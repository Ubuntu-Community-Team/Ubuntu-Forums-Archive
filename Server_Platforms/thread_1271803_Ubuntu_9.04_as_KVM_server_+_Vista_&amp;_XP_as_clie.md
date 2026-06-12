---
title: "Ubuntu 9.04 as KVM server + Vista &amp; XP as clients"
date: 2009-09-21
forum: Server Platforms
---

### Post by TheNomad on 2009-09-21
This is more of an "is it possible and what are the pitfalls" question. Otherwise I have not tested the configuration yet.

What happened is, my wife's Vista laptop died due to hard disk going belly up. Now that I replaced it, it refuses to boot from the vista DVD to reinstall it. It boots from a CD okay. Something wrong with the alignment of the drive's optical reader I suppose.

My solution is to install Ubuntu 9.04 server platform and run 2 guests on the KVM virtualization. I have the original Vista home prem. DVD, which most probably will be turned into an iso and uploaded to Ubuntu for installation. I also have an old XP home cd that I would like to try installing on the same disk.

I am sure I am not the first dude trying this and would love to hear about your experiences. Did it run successfully ? If not, what do you suggest for virtualization ? 

Thanks in advance.

---

### Post by stlsaint on 2009-09-22
hhmmm...sounds like you are trying use something like vbox and make virtual machines. now im not sure about that working as server edition is cli only (unless you isntall gui) now granted that kvm does support iso imaged im not sure about how the client would come out...server edition is meant to be used as a server...you could easily install say ubuntu desktop and run two vm's that way. Cant really tell you too much about what it is your wanting to do. Go here [UbuntuDocuments]("https://help.ubuntu.com/")

and do a search for KVM...you will see many options to choose from

also i think kvm can run on its own...but double check that.

---

