---
title: "Could I move binaries from a Windows 7 Vbox guest to a Lucid Host via flash drives?"
date: 2010-11-15
forum: Virtualisation
---

### Post by mikodo on 2010-11-15
Hi everyone,

Just musing here. 

One can not share a folder on the guest Os to the host OS using the shared folders in VirtualBox. Could one move binaries or any other kind of file on to a NTFS flash drive, from the Windows guest; then install the files from the flash drive to the host Lucid machine?

Should work right?

Thanks

---

### Post by fjgaude on 2010-11-15
The binaries run under Windows OS, right? Do you think these would run under Linux? I don't think so.

Certainly with Linux as your host, and VBox with Windows installed you should be able to share folders between OSs. I do this with VMware Player.

---

### Post by mikodo on 2010-11-15
> **fjgaude said:**
> The binaries run under Windows OS, right? Do you think these would run under Linux? I don't think so.

Certainly with Linux as your host, and VBox with Windows installed you should be able to share folders between OSs. I do this with VMware Player.

Thanks for the reply.

Alright, I will forget about sharing bianaries between Windows and Linux.

As for using the shared folders feature in VirtualBox; One can only share folders from the host and be read in the guest and not from the guest to the host, according to Perryg in the VirtualBox forums.

 [http://forums.virtualbox.org/search.php?sid=8407db2c0bbbfb5b95d7a5d84e89474e](http://forums.virtualbox.org/search.php?sid=8407db2c0bbbfb5b95d7a5d84e89474e)

I suppose I can move files by utilizing the shared clipboard.

Thanks again.

---

### Post by nerdy_kid on 2010-11-15
It *is* possible to run Windows binaries on Linux but the results are usually less then optimal.
You can move files around that way yeah, but binaries not so much.  
You should be able to set up a shared folder though, I would look more into that for a more elegant solution.

---

### Post by nerdy_kid on 2010-11-15
> **mikodo said:**
> Thanks for the reply.

As for using the shared folders feature in VirtualBox; One can only share folders from the host and be read in the guest and not from the guest to the host, according to Perryg in the VirtualBox forums.

 [http://forums.virtualbox.org/search.php?sid=8407db2c0bbbfb5b95d7a5d84e89474e](http://forums.virtualbox.org/search.php?sid=8407db2c0bbbfb5b95d7a5d84e89474e)



that is just wrong, I have a XP guest on my maverick host and it writes to the shared folder just fine.  You will need to setup the permissions correctly on the host however.

---

### Post by mikodo on 2010-11-15
Thanks Nerdy Kid:

Since you are writing to the shared folder from your XP guest to your Maverick host; I guess I will have to get my hands dirty and see what I can do too!

Thank you for the information.

---

### Post by mikodo on 2010-11-15
Sorry about the above copied link:

[http://forums.virtualbox.org/search....d7a5d84e89474e]("http://forums.virtualbox.org/search.php?sid=8407db2c0bbbfb5b95d7a5d84e89474e")

I found it does not copy to the page on VirtualBox Forums that discusses this topic.

Mike

---

### Post by nerdy_kid on 2010-11-15
> **mikodo said:**
> Thanks Nerdy Kid:

Since you are writing to the shared folder from your XP guest to your Maverick host; I guess I will have to get my hands dirty and see what I can do too!

Thank you for the information.

NP :)

The virtualbox help files has a very nice section on shared folders and how to get them working properly.  Just open up Vbox and hit contents under the help menu.  Hope you get it working!

---

### Post by fjgaude on 2010-11-16
> **mikodo said:**
> Thanks Nerdy Kid:

Since you are writing to the shared folder from your XP guest to your Maverick host; I guess I will have to get my hands dirty and see what I can do too!

Thank you for the information.

I do this all the time. It is data files, not binary executable code. I have a raid5 database that I share between host and guest, reading and writing from both. Notice my signature line. <smile>

---

### Post by mikodo on 2010-11-16
Thanks everyone.

Mike

---

