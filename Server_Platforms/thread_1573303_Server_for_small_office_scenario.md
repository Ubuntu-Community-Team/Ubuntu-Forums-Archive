---
title: "Server for small office scenario"
date: 2010-09-12
forum: Server Platforms
---

### Post by woodchipper on 2010-09-12
We have a small office with 4-5 computers and would like to set up a machine to act primarily as a file server. Most of the desktops are using windows.

What would I need in terms of a computer to handle file server capability and would we be able to also host our web site from that same machine?

Thanks.

---

### Post by hictio on 2010-09-12
> **woodchipper said:**
> We have a small office with 4-5 computers and would like to set up a machine to act primarily as a file server. Most of the desktops are using windows.

What would I need in terms of a computer to handle file server capability and would we be able to also host our web site from that same machine?

Thanks.

Samba, I guess will be enough, for the file server.
For the webserver, you'll need Apache, the web server.
Are you planning on hosting what type of web site on the box, say, a public website of you company, or it'll be an internal website, accessible only from within you office?

---

### Post by woodchipper on 2010-09-12
It would be a public website. 

Recommendations on hardware?

---

### Post by hictio on 2010-09-12
Leaving the hardware aside, at least for the moment, I wouldn't mix those two services on the same box.
Think that the files'll be on the same box that it is accessible over the internet.

---

### Post by lykwydchykyn on 2010-09-12
> **woodchipper said:**
> It would be a public website. 

Recommendations on hardware?

You don't need powerful hardware for something like this, though it depends some on how much traffic you get on the website.

The biggest thing is having a reliable piece of hardware with some redundant systems and RAID.  What's your budget?

---

### Post by v1ad on 2010-09-13
yes think of the budget, if its only a network area storage, look into NAT's and the file server you can just host off bluehost or something for 4 bucks a mo

---

### Post by HermanAB on 2010-09-13
A simple website doesn't take much resources.  You can do everything on one machine, but it can become a maintenance head-ache. 

So I would suggest that you install Virtualbox or VMware Player and make a virtual machine for the web server, another VM for Email and a third one for Samba, just to keep things separated.  The other advantage is that when things grow and you need more computing power, it is easy to move a VM to another machine.

If you are really lazy, then you can download preconfigured VMs from the VMware web site for all of these.

---

### Post by waloshin on 2010-09-13
> **v1ad said:**
> yes think of the budget, if its only a network area storage, look into NAT's and the file server you can just host off bluehost or something for 4 bucks a mo

I just set up my website a couple of days ago and almost everyday I am getting cpu throttled. 


[IMG]http://i54.tinypic.com/2m6vcqp.png[/IMG]

Also Bluehost has high cpu load too. 

[IMG]http://chart.apis.google.com/chart?chtt=System%C2%A0Load&chs=400x170&cht=bvs&chg=25,25&chd=t:6.25,6.35,6.32&chds=0,8&chbh=a&chxt=x,y&chxl=0:|1min|5min|15min|1:|0|8&chm=N,000000,0,-1,10&chco=0000FF&chf=bg,s,F9F9F9[/IMG]

And it seems mysql is using 96.4% cpu time.

---

### Post by v1ad on 2010-09-13
o that i didn't know, thats terrible, then i would go with HermanAB's advice.

---

### Post by zaphod777 on 2010-09-13
> **HermanAB said:**
> A simple website doesn't take much resources.  You can do everything on one machine, but it can become a maintenance head-ache. 

So I would suggest that you install Virtualbox or VMware Player and make a virtual machine for the web server, another VM for Email and a third one for Samba, just to keep things separated.  The other advantage is that when things grow and you need more computing power, it is easy to move a VM to another machine.

If you are really lazy, then you can download preconfigured VMs from the VMware web site for all of these.

Virtual box is ok but I would recommend VMWARE ESXi 
[https://www.vmware.com/tryvmware/index.php?p=esxi&source=hp&q=esxi](https://www.vmware.com/tryvmware/index.php?p=esxi&source=hp&q=esxi)
That way you can upgrade to ESX if needed later. 

I would recommend one virtual server running a standard LAMP (Linux, Apache, MYSQL, PHP), and another one running samba.

---

### Post by syedwasi on 2010-09-13
Hello,

We have small office of 35-40 pc would requires to setup ubuntu server on raid 1 ..
pls recommend hardware and other requirement.

regds
wasi

---

### Post by zaphod777 on 2010-09-13
> **syedwasi said:**
> Hello,

We have small office of 35-40 pc would requires to setup ubuntu server on raid 1 ..
pls recommend hardware and other requirement.

regds
wasi

Well I would recommend a similar setup that I recommended to the original poster. Do you guys already have something like Active Directory setup? If not you may wan't to also configure OpenLDAP.

As far as server hardware I would recommend server class hardware. Something like a HP DL380 running Raid5 rather than raid1. You  will get better performance and better use of the storage.

What kind of network do you already have in place?

---

### Post by v1ad on 2010-09-13
i prefer raid 10 . :o

---

### Post by zaphod777 on 2010-09-13
> **v1ad said:**
> i prefer raid 10 . :o

If the disk trade off is worth it :p

---

### Post by spynappels on 2010-09-13
+1 for ESXi, I have it on a server at my home running 4-5 VMs at any one time, mixture of LAMP, VPN, PBX and storage servers.

---

### Post by beetlejuice321 on 2010-09-20
I agree with v1ad on using a NAT and just hosting your website for $4/mth. Its easier. I also agree with HermanAB suggestions of using VM's for your services.

IMO Ubuntu is good as a desktop OS, but really limited as a server, especially for small businesses. There is virtually no support for small business implementations I am aware of. 

I think your best bet if you want a simple server that's easy to setup is try SME-Linux, EBox (based on Ubuntu), or install a Linux based NAS on the system as a simple file server. You could install any one of these under a virtual server as well. The first two options I suggested will also let you easily install LDAP as well, something that has traditionally been difficult to do on Ubuntu.

---

### Post by zaphod777 on 2010-09-20
> **beetlejuice321 said:**
> I agree with v1ad on using a NAT and just hosting your website for $4/mth. Its easier. I also agree with HermanAB suggestions of using VM's for your services.

IMO Ubuntu is good as a desktop OS, but really limited as a server, especially for small businesses. There is virtually no support for small business implementations I am aware of. 

I think your best bet if you want a simple server that's easy to setup is try SME-Linux, EBox (based on Ubuntu), or install a Linux based NAS on the system as a simple file server. You could install any one of these under a virtual server as well. The first two options I suggested will also let you easily install LDAP as well, something that has traditionally been difficult to do on Ubuntu.

Ubuntu is a great server OS. It is not plug and play but you can configure anything on it that you can on any other Linux OS.

---

### Post by kevin11951 on 2010-09-20
> **zaphod777 said:**
> Virtual box is ok but I would recommend VMWARE ESXi 
[https://www.vmware.com/tryvmware/index.php?p=esxi&source=hp&q=esxi](https://www.vmware.com/tryvmware/index.php?p=esxi&source=hp&q=esxi)
That way you can upgrade to ESX if needed later. 

I would recommend one virtual server running a standard LAMP (Linux, Apache, MYSQL, PHP), and another one running samba.

Except you can't administer an ESXi from within Ubuntu.  Their management software is Windows only (they may also have a mac version too).

However, Proxmox VE, is everything VMWare ESXi wanted to be, and its free/open source.  Plus its build on Debian Lenny/OpenVZ/and KVM.  In other words, its stable because its built on stable parts.

Look into Proxmox VE: [http://pve.proxmox.com/wiki/Main_Page](http://pve.proxmox.com/wiki/Main_Page)

edit:  I should also mention its easy to use, all parts (including the VMs themselves) can be configured from the web gui, and any OpenVZ templates can be used with it.

---

### Post by zaphod777 on 2010-09-20
> **kevin11951 said:**
> Except you can't administer an ESXi from within Ubuntu.  Their management software is Windows only (

VMware is best in class but that is one of my pet peeves too I think you can do some functions via the web url though. I'll need to checkout Proxmox VE unfortunately I don't have server hardware lying around anymore but it looks pretty sweet and you can't beat the price.

---

