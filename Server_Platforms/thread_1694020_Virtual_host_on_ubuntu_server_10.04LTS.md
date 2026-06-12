---
title: "Virtual host on ubuntu server 10.04LTS"
date: 2011-02-23
forum: Server Platforms
---

### Post by barnesey on 2011-02-23
Hi all,

I am looking into upgradeing my server and change the way i have it setup.

I would like to virtualise with my server, im running an twin AMD 32bit server system, which has an sata controller, scsi, and good old IDE. and 4gb of ram as well. 

What would be the best way of achiveing this as the barremetal vmware and xen didnt seem to work.

Any idea welcome cheers,

---

### Post by YesWeCan on 2011-02-23
Hi.
I am running 10.04LTS 64-bit desktop with AMD 4200+ dual 64 bit uP and only 2GB of RAM (should be 4 - mobo issue).

I have Oracle VirtualBox 4.04 and it works perfectly. I run Windows 7, Ubuntu 10.10, OpenSuSE, Ubuntu 9.04 and fedora as guests.

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)
don't forget to download the Extension Pack

---

### Post by barnesey on 2011-02-24
Well the motherboard is Showing 3900MB of RAM, I have wonderd about putting the desktop version on the server to make things an little easier. I have used virutal box before and it is good, Didnt know there have been version 4 yet. 
However i dont know if Ubuntu 32bit will pick up both processors or not. I know the server version does but in sure of in desktop version. 

The plan is to have Server 2003 if i can get one or an PDC server, an FOG server, proxy Server, Web server, and a few file servers as well.  I i would like to manage it remotely, im planning to leave it in an corner and let it do its work.

---

### Post by SeijiSensei on 2011-02-24
32-bit operating systems cannot address more than 3 GB of memory.  If you have 4 GB or more, you'll want the 64-bit version.

---

### Post by headvampyre@hotmail.co.uk on 2011-02-24
VirtualBox *should* be able to pick up both CPU's, it does on a quad-core 64-bit system, and im pretty sure itll work for 32-bit, just dont overdo it on RAM for the vm. Youll want to pick up the latest version of virtualbox from [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)
Remember - make sure you get the i386 version :)

---

### Post by barnesey on 2011-02-24
Would ubuntu 64 bit work on my system to make use of the 4gb of ram,

3GB should be ebought but if 64 will work it will be an bounus.

---

### Post by barnesey on 2011-02-24
What i ment will the 64 kernal work with the 2 32 bit processors as well,

---

### Post by SeijiSensei on 2011-02-24
The quickest way to answer that question is to try and boot an [Ubuntu CD with a 64-bit image]("http://releases.ubuntu.com/lucid/ubuntu-10.04.2-desktop-amd64.iso").

---

### Post by YesWeCan on 2011-02-24
> **barnesey said:**
> What i ment will the 64 kernal work with the 2 32 bit processors as well,

I would doubt it. Two 32-bit uPs don't make a 64-bit uP!
What is the make and model of your mobo?

---

### Post by barnesey on 2011-02-25
I can seem to find any motherboard numbers on the mother board at the moment.

---

### Post by barnesey on 2011-02-27
Well i have tired the 64 version and it failes. However the 32bit version has pick up 3.5GB of RAM which i think will be more than enougth for an few VM's.

---

### Post by confusedstingray on 2011-02-28
to find the model of your mb most (not all) put some model or version  by th last pci slot or what ever the type of the last slot is can be ver small writing

---

