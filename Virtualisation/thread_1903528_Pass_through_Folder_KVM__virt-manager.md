---
title: "Pass through Folder KVM / virt-manager"
date: 2012-01-02
forum: Virtualisation
---

### Post by Antoniya001 on 2012-01-02
I'm trying to get a folder from my host to a guest. I can create the folder in virt-manager and if I update the guest with : 
**apt-get install linux-image-extra-virtual** 
Then I'm able to mount it with : 
**mount -t 9p -otrans=virtio,version=9p2000.L /sharename /local/folder/**
just as described in this post :
[http://ubuntuforums.org/showpost.php?p=11399497&postcount=3](http://ubuntuforums.org/showpost.php?p=11399497&postcount=3)
but I'm unable to get it to become writeable.
 
The apparmor messages in my syslog are there also, but the solution posted in the post does not work for me...
 
Question 1 : Is this the way to do it ? Or can it be done simpler (without doing it very different like using nfs shares)
 
Question 2 : This might work with Ubuntu as guest but how with windows as guest ?
 
I've done some extensive searching online but very little info and few guides actually show you the best way. I could not locate a **best practices for KVM **or anything similar.
 
Arjan

---

### Post by Rebelli0us on 2012-01-08
You can use Vbox "Shared Folders".

---

