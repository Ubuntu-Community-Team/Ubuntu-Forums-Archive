---
title: "I need help to chose Server for virtualization.."
date: 2011-03-03
forum: Virtualisation
---

### Post by dusundurt on 2011-03-03
Hello guys,
I work in the It department at university in Turkey, and the chief of It department wanted me to investigate servers for virtualization. He told me to look at Sun,Hp and Ibm servers.. I dont really have much knowledge about servers and know nothing about virtualization.. I wanna know what to look for in servers. for virtualization. any info apreciated.. 

Thank you in advance.

---

### Post by An Sanct on 2011-03-03
Welcome to the forums.

If you are looking for "[desktop virtualization]("http://en.wikipedia.org/wiki/Desktop_virtualization")" take a look at the Ubuntu server edition, it has virtualization server capabilities.

---

### Post by Hedgehog1 on 2011-03-03
Virtualization can take many forms.  However, lets look at some basics.

I will start with what we use as servers. You may not need this level of hardware, but it is good to know.

The IBM M3 series offers a wide range of reliable hardware:

[B][http://www-03.ibm.com/systems/x/hardware/rack/x3650m3/]("http://www-03.ibm.com/systems/x/hardware/rack/x3650m3/")
[/B]
This link is for a rack mountable system, but you will find large and small M3 units.

We use Linux as the OS for these servers.

The typical goal of virtualization is to have one powerful server running a number of instances of an OS (perhaps 30 students in a computer lab using low-power computers that are 'remote-desktopped' to the 30 sessions of Windows running on the M3 server).  This allows a more cost effective use of hardware (it is cheaper to setup a powerful server the 30 powerful desktops).

May I suggest that you visit:

**[http://www.virtualbox.org/]("http://www.virtualbox.org/")**

Download the free Virtual Box software.  Then get an ISO from the Ubuntu site:

**[http://www.ubuntu.com/desktop/get-ubuntu/download]("http://www.ubuntu.com/desktop/get-ubuntu/download")**

Use this ISO of Ubuntu to create a virtual machine running on your desktop PC.  Actually running 'VBox' (as we call it) will help you understand the principles.

Then you will know what questions to ask.

If you get stuck, please post here again and we will help you.

***The Hedge***

:KS

EDIT: We posted at the same time.
> If you are looking for **["desktop virtualization"]("http://en.wikipedia.org/wiki/Desktop_virtualization")** take a look at the Ubuntu server edition, it has virtualization server capabilities.

The next step once you get your head around the concept by running your own Vbox of Ubuntu is to follow the above link ans see the already-setup options Ubuntu offers.

---

### Post by dusundurt on 2011-03-04
> **An Sanct said:**
> Welcome to the forums.

 Thank you!

---

### Post by dusundurt on 2011-03-04
> **Hedgehog1 said:**
> Virtualization can take many forms.  However, lets look at some basics.

I will start with what we use as servers. You may not need this level of hardware, but it is good to know.

The IBM M3 series offers a wide range of reliable hardware:

[B][http://www-03.ibm.com/systems/x/hardware/rack/x3650m3/]("http://www-03.ibm.com/systems/x/hardware/rack/x3650m3/")
[/B]
This link is for a rack mountable system, but you will find large and small M3 units.

We use Linux as the OS for these servers.

The typical goal of virtualization is to have one powerful server running a number of instances of an OS (perhaps 30 students in a computer lab using low-power computers that are 'remote-desktopped' to the 30 sessions of Windows running on the M3 server).  This allows a more cost effective use of hardware (it is cheaper to setup a powerful server the 30 powerful desktops).



Thank you very much, for the info...
Firstly I need to chose the Server, I am going to check this  and once i decided on which server to buy, i will go on next steps.

Im really thankful.

---

### Post by Hedgehog1 on 2011-03-04
dusundurt,

If you could a little additional information, it would help us guide you in your search.

The following simple example is one way you can use virtualization in a University setting.

**For Students:** *Allow 150 students computer access with only 30 workstations.*

In this example, picture a classroom with 30 very basic computers (or network appliance devices - cheap disk-less workstations) on the desks.  On the virtualization server, there are 150 'images' of Linux 'systems' on the hard drive.  There are only 31 'real' computers in use. 1 server, 30 simple workstations.

The first class of the day starts, and students with ID's 1001-1030 login to the workstations.  The virtualization server loads and runs 30 Linux 'virtual machines' in its own memory, and the 30 students all appear to have their own PC. In reality, each student is really 'remote desktopping' into the server and seeing their 'virtual machine'.  Each student sees their workstation is just the way it looked the last time they logged in.

The first class completes, and the virtualization server writes the images 30 'virtual machines' to disk and stops processing the 30 'virtual machines'.

Now the second class begins, and students with ID's 1031-1060 login to the workstations. Again, the virtualization server loads and runs 30 Linux 'virtual machines' in its own memory, and the 30 students all appear to have their own PCs, with things left just like they left them last time they were there.

This process repeats for the 5 classes of the day.  The 31 machines have provided what felt like 150 different systems to 150 different students.

Now, after classes the room with the 30 workstations becomes the 'computer lab' for student to use as needed in the evening.  As each student logs in with their ID, the virtualization server reads their Linux image from the disk and runs it, allowing students to take turns at the workstations throughout the evening, and every student always gets 'their' Linux PC image.

The method of workstation sharing offers the best financial savings when doing 'Cloud Computing'.  Because no student needs a workstation all day long, the University can save money here.

Anyway - this is one example of using virtualzation to reduce operations costs, and still provide needed services to students.

Hope this makes sense.

***The Hedge***

:KS

---

### Post by dusundurt on 2011-03-08
Hello Hedge,
first of all, i am really thankful for your interests and help.

In the IT department of our University, we want to virtualize some of our servers (I mean we are going to move these machines as Vms to the machine  we are going to buy ), these servers are ;

1)Terminal Server (Dual Core AMD opteron Processor 1.80GHz, 2 GB Ram, win2003 Server)

   - Aproximately 50 users use this machine via Remote Desktop Connection, They run one of two applications installed on this machine and print reports provied by these applications (Student and personel planning programs). Generally , there are 10-15 users connected to server at the same time.. 

2)Database Server (Dual Core Amd Opteron Processor 2.21 GHz, 2Gb ram, Win2003 Server)

   - Sql Server 2005 installed, there are 2 databases in Sql Db Server.
           personel db : used by personel planning program, database covers information of less than 500 personel working at university.
           student db  : used by student planning program , this db contains information of 7000 students.


3) Web Servers (1-Dual Core Amd Opteron 2.61 Ghz 4 Gb Ram, 2-Dual Core Amd opteron 1.80 Ghz and 4 Gb Ram)

4) Mail Server (Intel Xeon(R) E5440 2.83 Ghz 8 Gb ram, Win 2008)
    - Icewarp Merak mail is installed (Around 300 mail accounts)

5 ) DNS Server (Dual Core Amd opteron 2.20 Ghz and 2 Gb Ram , Win 2008)

So, with these information, What kind of server should we buy? 

thank you in advance..

---

### Post by Hedgehog1 on 2011-03-08
> **dusundurt said:**
>  1)Terminal Server (Dual Core AMD opteron Processor 1.80GHz, 2 GB Ram, win2003 Server)
 
2)Database Server (Dual Core Amd Opteron Processor 2.21 GHz, 2Gb ram, Win2003 Server)
 
3) Web Servers (1-Dual Core Amd Opteron 2.61 Ghz 4 Gb Ram, 2-Dual Core Amd opteron 1.80 Ghz and 4 Gb Ram)
 
4) Mail Server (Intel Xeon(R) E5440 2.83 Ghz 8 Gb ram, Win 2003 )
 
5 ) DNS Server (Dual Core Amd opteron 2.20 Ghz and 2 Gb Ram , Win 2003 )
 
dusundurt,
 
Based on the list above, your processig needs are not excessily heavy. This means you could operate on a more reasable cost server.
 
For a basic 'rule of thumb', add together the RAM of the indiviuals systems you wish to virutalize: 2 gigs <Terminal server>) + 2 gigs <database server> + 4 gigs <web server> + 8 gigs <mail server> + 2 gigs <DNS server>. This means your 'guest' machines need 18 gigs of ram.
 
Based on the 18 gigs of RAM, purchase a system with 32 gigs of RAM. This will give you room for your 'host' OS, and growth in your 'guest' OS's over time.
 
Because this system will be sharing Disk I/O with many virutal machines, you wll want a very fast hard drive system. You also want a fault tolerant disk system, becase the University is really counting on this system being realiable. Select a system with hot-swappable RAID. This will allow you to replace a bad hard disk with a replacement hard disk without turning the system off. The users will often not even be aware that the replacement happened.
 
Next, with that level of network traffic, a systemt that has dual network connections (two 1 GB nic cards) is preferred. Both for redundacy, and for daily processing speed. If one fails you can limp by on the other one until the bad one is replaced.
 
The number of processors/cores is not as important as enought RAM and fast Disk and Network. I/O is the true limit of the system, not the CPUs. As little as one 6 core or two 4 core CPUs (8 total) will function. On board cache on these CPUs is a little more important the the very fastest processor speed. If your budget allows for two 6 core CPUs (12 total); great. But the RAM and fast Disk system are where you should spend your money first.
 
We have talked about the 'guest' OSs, but not the 'host' OS that will run the server.
 
The host can be a windows OS, however there is more overhead with a host Windows OS than a Host Linux based one. You *can* use a windows OS as the host; but you will get better use of the hardware with a Linux host. The real limiting factor is the comfort level you and your team have (or can gain) running Linux.
 
***The Hedge***
 
:KS
 
p.s. If you have not yet done so, please download the free Virutal Box software and the free Ubuntu 10.10 .iso file. Then install Ubuntu as a guest OS on your desktop PC using Virtual Box. It will help you gain a comfort level with using virtual machines, and also ***impress others*** at the office. :D
 
p.p.s. You can (over time) convert the web server and DNS server over to Linux and get faster perforamance if you want. This is not required, it is just a thought.

---

### Post by dusundurt on 2011-03-09
Thank you very much for your help. It s really helpful for me.. 
But wheni read this i wanted to ask another question.. 
What do you think about Xen for host? Or Wmware ESXi? and why would i chose Vbox ?
thank you!

---

### Post by Hedgehog1 on 2011-03-09
> **dusundurt said:**
> Thank you very much for your help. It s really helpful for me.. 
But wheni read this i wanted to ask another question.. 
What do you think about Xen for host? Or Wmware ESXi? and why would i chose Vbox ?
thank you!
 
For your _real_ server, please choose the Virutalzation software that works best for you and that you can get the best support for. At work, we use VMWare for everything. I have not used Xen, so I have no opinion about it. At home, I use Virtual Box because of some Linux 3D video support it offers.
 
For a simple test on your desktop PC, I suggested Virtual Box as a free option you could simply download and play with. There is also the free VMware player, too.
 
I just wanted you to try running a virutal machine on your desktop PC and get a feel for it, that is all. Any VM software you want to use is fine.
 
Please do let us know what hardware and VM software you select for your server. Feel free to ask more questions, too.
 
I look forward to hearing more about your project as it progresses.
 
***The Hedge***

:KS

---

### Post by dusundurt on 2011-03-10
> **Hedgehog1 said:**
> For your _real_ server, please choose the Virutalzation software that works best for you and that you can get the best support for. At work, we use VMWare for everything. I have not used Xen, so I have no opinion about it. At home, I use Virtual Box because of some Linux 3D video support it offers.
 
For a simple test on your desktop PC, I suggested Virtual Box as a free option you could simply download and play with. There is also the free VMware player, too.
 
I just wanted you to try running a virutal machine on your desktop PC and get a feel for it, that is all. Any VM software you want to use is fine.
 
Please do let us know what hardware and VM software you select for your server. Feel free to ask more questions, too.
 
I look forward to hearing more about your project as it progresses.
 
***The Hedge***

:KS

Thank you Hedge,
now, I really understood what you told me already:) So , first of all i need to buy the Server:) then i will select the virtualization software and im gonna be here meanwhile.. thank you for your support:)

Dusundurt

---

### Post by Hedgehog1 on 2011-03-10
dusundurt,

This is just information about my own personal PC.

My primary operating system is Ubuntu 10.10, and I keep two Vbox links on my desktop so I can quickly start up Windows 7 or the new 'Natty' Ubuntu release if I need to:

[IMG]http://img651.imageshack.us/img651/383/vboxiconsinmaverick.png[/IMG]

I also keep a large number of virtual machines on my personal PC, so I can test many OS setups:

[IMG]http://img862.imageshack.us/img862/3982/vboxmanager.png[/IMG]

Just thought you would like to see how powerful virtual machines can be even for a single user desktop computer.  I can test most any OS without having to reboot my PC.

***The Hedge***

:KS

---

### Post by dusundurt on 2011-03-11
> **Hedgehog1 said:**
> dusundurt,

This is just information about my own personal PC.

My primary operating system is Ubuntu 10.10, and I keep two Vbox links on my desktop so I can quickly start up Windows 7 or the new 'Natty' Ubuntu release if I need to:

:KS
Hmm, This is a good idea! I have Ubuntu 10.10 and win7 installed on my machine.. I hardly ever use win7 or actually i never use it unless it is necessary and it s hardly needed. So i can try it like this instead of having it fully installed:) 
Thank you!

---

