---
title: "Server Help for Noob"
date: 2011-07-04
forum: Server Platforms
---

### Post by Hank_The_Dog on 2011-07-04
I want to create a network (possibly with a local domain) That has shared storage for the house. I have a bare bone Alienware Server that I got at a thrift store. It is ready to be booted after I installed chip and dhard rive.

Things we would like...


-To be able to access that hard drive conveniently from the other laptops in the house. (Having the option of dragging and dropping onto it without FTP or Putty or something else)

-Possibly being able to access it with the IP address and drag and drop from a browser or something similar from a computer not at the house.

-Basically for work/college/shopping etc it would be nice to have this storage space accessible from wherever we are at.



I have been told to use RedHat. But I have done some reading about Samba.

But main question... Where is a good place to get started?

---

### Post by Dangertux on 2011-07-04
> **Hank_The_Dog said:**
> I want to create a network (possibly with a local domain) That has shared storage for the house. I have a bare bone Alienware Server that I got at a thrift store. It is ready to be booted after I installed chip and dhard rive.

Things we would like...


-To be able to access that hard drive conveniently from the other laptops in the house. (Having the option of dragging and dropping onto it without FTP or Putty or something else)

-Possibly being able to access it with the IP address and drag and drop from a browser or something similar from a computer not at the house.

-Basically for work/college/shopping etc it would be nice to have this storage space accessible from wherever we are at.



I have been told to use RedHat. But I have done some reading about Samba.

But main question... Where is a good place to get started?

Red Hat is nice, but Ubuntu will do just as well for the purpose.

I would recommend Samba or NFS for filesharing. If you are thinking of integrating a domain at some point even if it's not now , I would use Samba for convenience. 

As far as the remote from "work/college/shopping" part, I would recommend using SFTP over SSH , it is secure, easy to set up, and easy to use (it's also really easy to get SSH on mobile devices such as iphones) 

I think that covers all the bases, if you have any other questions feel free to ask.

---

### Post by SeijiSensei on 2011-07-04
Here's a place you might start: [http://www.linuxhomenetworking.com/wiki/index.php](http://www.linuxhomenetworking.com/wiki/index.php)

I've found a number of useful articles there over the past few months.

---

