---
title: "Sun sbus systems"
date: 2008-03-03
forum: Sun Sparc Users
---

### Post by tizroc on 2008-03-03
I have worked and gotten ubuntu on Ultra 10 (ide), Ultra 60 & 30 (pci/scsi), and Ultra e450 (pci/scsi) however all installs on any system with the Sun sbus system do not install.

The models that do not work are as follows
E3000 (6 400UII procs, Six Gigs of ram, 10 73gig Ultra SCSI 360 Hdd)
E-2 (Dual 350UII Procs, one gig of ram, 2 73gig Ultra SCSI 360 Hdd)

Each one of these systems does not get past trying to load the drivers for the cdroms. This portion of the install is after the keyboard layout so I know we have booted to the cdroms. Also I have moved the cdroms to the U60, and 30 and they install so it is not the fact that it is a scsi cdrom. This appears to be a defect in detecting the cdrom only when attached to a system with an sbus.

Can anyone help me out here this has become a rather frustrating trial.

Thank you,
Tizroc

---

### Post by netztier on 2008-03-03
> **tizroc said:**
> 
Can anyone help me out here this has become a rather frustrating trial.


Already tried the old trick of changing to another shell at the first step possible, do **modprobe esp** to load the esp module and then jump back to the normal installation process? This was necessary on some of the sbus ultras I ran Ubuntu on.

regards

Marc

---

### Post by ubu_for_umm on 2008-03-27
modeprobe esp didnt work for me. I had the same problem. I went the netboot way instead. It worked fine till it was time to detect the hard drives. They were connected to my E4000 through SCSI and were housed in a Sun StorEdge. They couldnt be detected and thats where I stand now.

---

### Post by mecki on 2008-04-15
Hello 

Which version did you try to install?
I had the problem with the cdrom which was not found with ubuntu 7.10
Then I started to install 6.06 in the package from january or so this year and the whole thing went through without any problem. 

Just that I wanted to change from server edition to a desktop edition for daily work, but 'til now I don't get the x-windows to work.

bye

mecki

---

### Post by tizroc on 2008-04-22
[QUOTE=mecki;4723488]Hello 

Q "Which version did you try to install?"
A I tried 6.04 (I think), and the 7.10 both sparc servers.

"Just that I wanted to change from server edition to a desktop edition for daily work, but 'til now I don't get the x-windows to work."

As for this every server version I have installed did not come with x installed. Which in my opinion is what a server should be like. However I am not 100% sure what you are asking here. Are you now installing Desktop or Server?

-Tizroc
Better a bleeding heart than no heart at all.

---

### Post by mecki on 2008-04-28
> **tizroc said:**
> 
As for this every server version I have installed did not come with x installed. Which in my opinion is what a server should be like. However I am not 100% sure what you are asking here. Are you now installing Desktop or Server?


Hello tizroc

that's what I found out in the meantime, too. I've got a sun enterprise 3000 at home and I wanted to use it as PC. When I downloaded sparc installation iso I always got the server edition. So I installed this and tried to change it to a desktop version but this was not so simple as I've thought especially after I've read somewhere that you have nothing else to do than start xwindow und upgrade to desktop edition.
that's for that.

But still. If you know some simple commands to install x on a sbus system I would appreciate this.

mecki

---

### Post by mecki on 2008-04-28
Hello tizroc

for you're first question, did you manage to install ubuntu?

here is the link I found the working iso

"hi chris,

i used this link:
[http://mirror.cs.umn.edu/ubuntu-releases/6.06/](http://mirror.cs.umn.edu/ubuntu-releases/6.06/)

there i select the SPARC server install CD to download the iso.

im curius to your experience...

Jean-Paul"
Jean-Pauls nicname is jpgeerets

thanks to Jean-Paul

bye mecki

---

