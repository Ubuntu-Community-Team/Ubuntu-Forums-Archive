---
title: "Vmware virtual server"
date: 2007-12-12
forum: Windows
---

### Post by Jem00 on 2007-12-12
Hey guys,
I would like to setup a small server at home. I am knew to the whole process. Since I don't have any free boxes I was thinking of making it a virtual server I have Vmware.

How would I set this up?

Thanks.

---

### Post by rickyjones on 2007-12-12
Well, if you have VMWare then you would first wish to create a virtual machine for Ubuntu to be installed on. I am going to assume that you know how to do that already.

When you have the virtual machine ready you have two options for installation. If you have the .iso image on the hard drive then you can mount that from within VMWare if you edit the CDROM hardware item.

Or, if you have the CD, just pop the CD into one of your cd-rom drives.

Now boot the virtual machine. It should auto-detect the CDROM or ISO image and begin the installation process.

From there you should be able to just answer the prompts - I usually accept the defaults (except for username and hostname).

-Richard

---

### Post by slimx3m on 2007-12-12
here it is a good tutorial that you could use.  i used myself and it works perfectly fine.  hope it helps
```

[http://www.howtoforge.com/installing-vmware-server-1.0.4-on-ubuntu-7.10]("http://www.howtoforge.com/installing-vmware-server-1.0.4-on-ubuntu-7.10")

```

---

### Post by Jem00 on 2007-12-12
Hey guys thanks for your replies. 
I am planning to install the vmware virtual server on windows. I was wondering whether I should use Windows server 2003 or Ubuntu 7.10 server?

Which is better?


Thanks again.

---

### Post by Jem00 on 2007-12-12
Hey does any one know what is better to run as a server?
Windows server 2003
OR
Ubuntu 7.10 server?

Which would be easier to run as I am knew to servers.

Thanks.

---

### Post by rickyjones on 2007-12-13
I would use whichever host OS you are the most comfortable with. One thing to remember is that you may get slightly better performance using Linux because you will not be sharing resources with the GUI (assuming you run a server version of Ubuntu). However, if you upgrade the kernel on the Linux server you MUST recompile VMWare otherwise it will not work. This will mean downtime for your guests.

My experience with running production VMWare Server on a Windows Server 2003 Small Business Server has been fantastic! Over three months with Microsoft Patch Tuesday and VMWare still runs solid without a single issue.

-Richard

---

### Post by Jem00 on 2007-12-13
Ok thanks for your replies.... moving on to the next question.

I have decided to go with windows server 2003.
How would I set it up to be a web server?

Thanks.

---

### Post by rickyjones on 2007-12-13
Could you clarify? Do you wish to have Windows Server 2003 be a web server?

---

### Post by Jem00 on 2007-12-13
Yea I would like to have windows 2003 as a web server..is it possible?

---

### Post by rickyjones on 2007-12-13
> **Jem00 said:**
> Yea I would like to have windows 2003 as a web server..is it possible?

Yes. You have several options for making Windows Server 2003 a web server.

1) Install IIS
2) Install Apache
3) Install something like XAMPP that includes Apache, MySQL, Perl, etc...

-Richard

---

