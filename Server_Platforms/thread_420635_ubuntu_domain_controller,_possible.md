---
title: "ubuntu domain controller, possible?"
date: 2007-04-23
forum: Server Platforms
---

### Post by umattu on 2007-04-23
I have been reading alot about people getting their ubuntu boxes to join a MS Active Directory. 

Is there a way to do this using absolutely no MS product?
I have a network of ubuntu machines and I have had to go to each individual machine to edit the fstab to get my NFS mounts, this is fine and good but I have other users and I would like them to have the respective directories mount for the user who logs in.

If some one could point out a link or a how to I would much appreciate it.

---

### Post by pparks1 on 2007-04-23
This can be done.   However, you won't be using an Active Directory style domain, but rather an NT 4.0 domain style domain.

The key here is samba and setting up your Ubuntu box to be a domain controller for the MS clients.   I have a doc that I but together for some guys at work...I will post it here in a few minutes.  Need to get to the computer which contains the doc.

---

### Post by umattu on 2007-04-23
I wont be using any windows os's in this network it is 100% ubuntu

Is there a way to do it without SAMBA?

I mean if there is no other way I will definately use this method.

---

### Post by pparks1 on 2007-04-23
Sure, NIS can handle network logons.   Ldap can handle logons.   You should be able to map and share your drives via NFS.

Here is a link on setting up NIS.  [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch30_:_Configuring_NIS](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch30_:_Configuring_NIS)

---

### Post by umattu on 2007-04-23
Sweet do you know of a good how to?

Thank You Much!!!!

---

