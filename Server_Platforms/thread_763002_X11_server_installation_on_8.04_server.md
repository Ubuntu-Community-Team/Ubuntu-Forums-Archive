---
title: "X11 server installation on 8.04 server"
date: 2008-04-22
forum: Server Platforms
---

### Post by bigal99 on 2008-04-22
Will it be possible to install the X11 server in a straightforward fashion on the 8.04 server platform?

We will be using this machine as server and workstation.

---

### Post by FakeOutdoorsman on 2008-04-23
> **bigal99 said:**
> Will it be possible to install the X11 server in a straightforward fashion on the 8.04 server platform?
Yes.  Install the xorg package in Synaptic Package Manager or with apt-get/aptitude:
```
sudo apt-get install xorg
```

This will give you only xorg and not a windows manager or desktop environment.  You can install those easily as well: [**Installation / Low Memory Systems**]("https://help.ubuntu.com/community/Installation/LowMemorySystems").

[QUOTE=bigal99]We will be using this machine as server and workstation.[/QUOTE]
I recommend you start with the desktop version of Ubuntu and install server related packages from there.  The server version has a different kernel and isn't suited as well for a graphical system: [**Apache, MySQL, PHP Installation**]("https://help.ubuntu.com/community/ApacheMySQLPHP").

---

### Post by bigal99 on 2008-04-24
Thanks for the tips. Our server will be partly an application server and partly a large data file server and will have a 2.8Tb raid 5 software array formatted in XFS. It will also be used for some graphical work as a workstation.

I was hoping from what I had read that the server kernel may be more efficient at dealing with these data files. However the number of people using the server is not large, so I suspect the point is moot, and that an XFS file sytem on ubuntu desktop will be just fine.

If you have any other ideas from what I have said, I'd appreciate them.

I certainly have done what you suggest in the past, namely adding the server services to a desktop system and found it was fine. I was just curious about what this server kernel would give us.

---

### Post by FakeOutdoorsman on 2008-04-24
> **bigal99 said:**
> Thanks for the tips. Our server will be partly an application server and partly a large data file server and will have a 2.8Tb raid 5 software array formatted in XFS. It will also be used for some graphical work as a workstation.

What type of applications will this server run and how are you planning on using to transfer/manage the data? What type of programs will be running when the machine is being used as a workstation?

[QUOTE=bigal99]I was hoping from what I had read that the server kernel may be more efficient at dealing with these data files. However the number of people using the server is not large, so I suspect the point is moot, and that an XFS file sytem on ubuntu desktop will be just fine.[/quote]
I have very little experience with XFS, so I can't give any opinion on it. Here are some articles going into the differences of the 7.10 server kernel: [_Ubuntu Server: Considering Kernel Configuration_]("http://www.serverwatch.com/tutorials/article.php/3715071") and [_Ubuntu Server: Kernel Comparisons and Implementation Issues_]("http://www.serverwatch.com/tutorials/article.php/3715071"). You can always try out the server kernel on an existing install since it is in the repos. If you have the alternate disc there is probably no need to also download the server disc since you can do a minimal command-line installation and then install the server kernel.

---

### Post by bigal99 on 2008-04-25
I apologize, but my terminology is lacking in accuracy!

This server can be described as a 'compute server', but there will also be lots of transfer of the data to and from the machine.
It will be scientific data, much of it in 'FITS' (Flexible Image Transport System') format. 
They'll be using IDL and their own FORTRAN code to process this data. 
Also they will be using IDL and FORTRAN to generate their own 3-D models.
This model data will get sent to another station running one of those 3-D visualization projectors in which the people use special glasses to see the images in 3-D.

FITS files can be several Mb each. And there are usually lots of them, forming perhaps several hundred giga-bytes when grouped together.

So, I'm not sure whether the server kernel will give any advantages.

BTW, because I would like to use RAID 1 for the system and RAID 5 for the data array, I'll need the appropriate installation CD. In the last version this was provided by the 'Alternate CD'.  Not sure about this version.

---

### Post by bigal99 on 2008-04-29
I see that the Ubuntu linux download page now has a link to the Alternate CD for 8.04. I'll download and see what it has.

So, yes, the Alternate CD has the 'linux raid' partition in the partioning.
However, I'll probably still use the regular desktop CD for installation.

I recall now that 'cfdisk' also provides the 'linux raid' partition type, so that the raid 5 array disks can all be partitioned via 'cfdisk' later on, and then set up as a raid array via 'mdadm'.
It's one of those things where if you don't do it every day, it takes a while to figure out how best to do it.

---

