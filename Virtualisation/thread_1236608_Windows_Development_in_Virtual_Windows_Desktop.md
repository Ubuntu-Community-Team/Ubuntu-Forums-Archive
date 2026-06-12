---
title: "Windows Development in Virtual Windows Desktop"
date: 2009-08-10
forum: Virtualisation
---

### Post by jpdk on 2009-08-10
Hi Guys,

I am really tired of my Vista desktop. I have used Ubuntu on several occasions for servers, and set up a few old notebooks for friends. But I have unfortunately been tied to Windows because I do quite a lot of Windows Development for work. 

But now I have had enough. I have recently got myself an Intel i7 machine with 8 gigs of Ram, and it is  running Vista... That worked well for a little while, but now it just sucks. 

So I was wondering if someone would help me out with some recommendations here.

I want to setup my machine with the latest Ubuntu (9.04, 64 bit) and then run my development in a virtual box on that machine. 

I actually need to run a few machines. I need one primary virtual machine, that will be my development machine. I will use this daily and quite a lot. I run Microsoft Visual Studio 2008 on a Vista Ultimate machine.

I also run two virtual machines that are servers I need for client server development, I run one Windows 2003 server with MS SQL Server 2008 and IIS 6, and one Windows 2008 server also with with a MS SQL Server 2008 and IIS 7.

I wouldn't min running a virtual Ubuntu Server as well.

It is absolutely paramount for me that the development virtual machine with MS Visual Studio runs at an acceptable performance level. If it doesn't then it won't take long before I am back to Vista. I really want to go for Ubuntu, but all of my clients request software written in .NET, and I need to be able to work with this all day long.

I have looked at Parallels Desktop (which I know from my girlfriends Mac) and VMWare. I am not really sure what I need from VMWare. There are a lot of different products, and I am not sure which I need. I also know that there are a few Open Source alternatives, but I have not been able to find any good reviews of any of them.

I am willing to pay for my software, I just need to know that I can rely on it. 

What setup would you suggest?

At this point I am leaning towards VMWare, just not sure what setup that would be, and if it works on Ubuntu 9.04.

Is there any virtualization software that allows me to assign a number of cores for my machine and then run multithreaded software on that virtual machine? I know that it won't run very well, but it might give me a chance to develop for multiple cores as well.

Thanks for all input,
Jay Pete

---

### Post by jocampo on 2009-08-10
Gosh! ... long thread ;-)

ok, I'm a SQL dba and Ubuntu lover :-) so I think I can help you (and we have lot of folks here that they can as well)

So... how many machines are we talking about in total (Windows I mean)

You said you have a server, how big the hard disk is on that one. Also, are you planning to run a Windows Cluster?

If you can provide additional information (how big your hard disk is, how many Windows Machines are you planning to use and what is going to be the main function of each one) I can help you more. but initially, if you are serious about Virtualization and use your VMs in an work/company environment maybe VMware is the way to go. 

That said, I've found VirtualBox very powerful and easier to use than VMware; I would say, if you are not planning to use SQL in a cluster or you don't need a Windows cluster, maybe you can use VirtualBox. The way I setup VirtualBox at home (but I'm pushing it to its limits) is mounting an Ubuntu headless server and installing VirtualBox on it (with no GUI, you'll save vital CPU and RAM resources) Once installed, I configure each machine via console and from any laptop, you can connect remotely and play around. For RAM, I suggest between 4 and 8GB, depending of your budget and machine limitations. And a CPU that could handle virtualization instructions would be nice.

I am running an Oracle Instance (Windows 2003 server) and MS-SQL2008 (Windows 2003) with 1gb each and performance is ok. In general terms, for SQL or Oracle, 1gb ram minimum is a must. For Vista, depending of what are you planning to run, 1gb or 512mb, and for any other Winddows desktop machine like XP, 512mb should work.

For company/office environment, RAID is a must, but I don't know what your current configuration is. Mine runs a 7200rpm disk but is a "home server" ...

---

### Post by jpdk on 2009-08-10
Hi jocampo,

Thanks for your reply. Let me see if I can give you ample information.

We are talking three Windows machines. I still have the test and production servers at my office, but it would be ideal for me to virtualize them as well on my own machine. That means one Vista (possibly Windows 7) machine that I will be developing on, and two servers. I will most likely only run one windows server at the time along with my development machine. Most of the time it will only be one virtual machine, which is the development desktop. I am not planning on running a Windows Cluster.

Host machine info:
Dell Studio XPS with two 600 GB Harddrives in a RAID 1 mirror. CPU is Intel i7 quadcore (8 virtual cores). 8 GB RAM. Not sure if the CPU can handle virtualization instructions.

I am very serious about virtualization. If the machine can't run Microsoft Visual Studio 2008, then it will be reverted back to a Vista machine. I am going to use the virtual machines daily, but it will only run my development environment. Everything else I plan to use Ubuntu for. 

I am not going to deploy this in a client/server environment. I only have the one physical machine, so everything has to run on the same machine, but the machine is quite powerful.

Thanks,
Jay

---

### Post by jocampo on 2009-08-10
Hey Jay

So (before giving my advice ;-) ) ... let's summarize ...

VMs

One Windows XP - Let's call it Apple
One Windows 2003 or 2008 Server - Banana
One Windows 2003 or 2008 Server - Cinnamon 


Are you gonna run all of them in a Domain? I mean, are you gonna setup a DC and then join the other 2? ... also, what kind of application are you planning to run on each one? ...

BY the way, you have a good Host machine , it will "fly" with Ubuntu Server on it

Jose.

---

### Post by jpdk on 2009-08-11
Hi jocampo,

OK... the VMs are

One Windows XP - Let's call it Apple
[INDENT]Visual Studio 2008[/INDENT]
One Windows 2003 Server - Banana
[INDENT]IIS 6[/INDENT]
[INDENT]MS SQL 2008[/INDENT]
[INDENT]Basically simple webdevelopment for Umbraco CMS up to more advanced for high end commerce solutions[/INDENT]
One Windows 2008 Server - Cinnamon 
[INDENT]IIS 7[/INDENT]
[INDENT]MS SQL 2008[/INDENT]
[INDENT]Basically simple webdevelopment for Umbraco CMS up to more advanced for high end commerce solutions[/INDENT]

No domain or active directory, just single machines.

Do you think I should install Ubuntu Server? I was planning on installing Ubuntu Desktop, since that is basically what I am going to use it for.

/Jay

---

### Post by jocampo on 2009-08-11
Ok, so ... this is my humble suggestion ...

1st, just because you do not need a domain, a cluster and basically you are going to run one machine at time, VirtualBox should work for you. So, for Virtualization software, VirtualBox should be your choice

Now, for the Host, I suggest Ubuntu Server. Why? the Ubuntu Server kernel has been modified to provide more "power" with same kernel...in other words, some RAM limitation and other kernel tweaks, will allow you to get better performance using same hardware. Another important reason is the GUI. A headless server won't use graphical interface so you will save important resources like RAM, that now you need for your virtual machines. Once your server is up and running, you can connect from any laptop via ssh and start/stop/resume your VMs. You can even use a Window$ machine to run your VirtualMachines and work with them, 'cause you will use remote desktop connection. Of course, your laptop and your server must reside on same network and be able to see each other, via Wifi or Lan.

You have plenty of RAM (8gb total, right?) so you can assign RAM like this:

-1gb for Appple
-2gb for Bananana
-2gb for Cinnamon

That's 5gb total. If at some point you decide to run all that at same time, I doubt you will have problems (you can change that later anyway) but if you are going to run each one separately, Banana and Cinnamon should not "feel" slow or restricted. Important!!! Please use fixed drives during creation; it will improve the disk performance a bit because the VM won't waste CPU and RAM resources when expanding virtual disk.

So, here's the plan

1. Install Ubuntu Server
2. Install VirtualBox on your headless server
3. Configure Apple, Banana and Cinnamon using VirtualBox

I won't cover or I think you will take care of the IIS, Visual Studio, SQL setup, right? :-)  ... but my 2 cents ... when configuring SQL, restrict the RAM so you can keep control over it.

"1" should not be a problem :-) ... "2" is a bit tricky but not too difficult if your server is connected to internet; my advice, do not install latest VirtualBox version, instead, 2.4 or so ... 3.0 gave me issues. BTW, you must add VirtualBox repositories in order to download them. And for "3", please check this thread: [http://ubuntuforums.org/showthread.php?t=616334]("http://ubuntuforums.org/showthread.php?t=616334")

Good luck and let us know ;-)

---

### Post by jpdk on 2009-08-11
Hi jocampo,

Thanks for your reply and suggestion.

I still don't get why I should install a headless Ubuntu Server. I need to use the machine as my desktop. I am not going to be running these virtual machines from another PC or Laptop. 

I am converting my old Vista box into an Ubuntu box, where I can Run the few Windows Apps I need in a virtual machine. I need my Ubuntu Graphical Desktop environment.

There is only ONE physical machine in play here...!

/Jay

---

### Post by jocampo on 2009-08-11
> **jpdk said:**
> Hi jocampo,

Thanks for your reply and suggestion.

I still don't get why I should install a headless Ubuntu Server. I need to use the machine as my desktop. I am not going to be running these virtual machines from another PC or Laptop. 

I am converting my old Vista box into an Ubuntu box, where I can Run the few Windows Apps I need in a virtual machine. I need my Ubuntu Graphical Desktop environment.

There is only ONE physical machine in play here...!

/Jay

Ohhhhh, I see, haahahaha....so, no laptop? the one that has 8gb of RAM is the only machine you have now? ....well, in that case, you can install Ubuntu desktop, but there is an extra step for the PAE switch so your machine can recognize 8gb. If I recall well, x86 processors can't recognize more than 4gb of memory. Anyway, with GUI things are easier...you just need to install VirtualBox on your Ubuntu desktop and later, VirtualBox on it...and finally, setup each of your VMs...

---

### Post by jpdk on 2009-08-12
I am quite sure the 64bit Ubuntu desktop can handle 8 gigs of RAM. So I don't think that it will have any trouble recognizing all of it.

/Jay

---

### Post by Tibuda on 2009-08-12
> **jpdk said:**
> I really want to go for Ubuntu, but all of my clients request software written in .NET, and I need to be able to work with this all day long.

What about cross-platform? See [http://www.mono-project.com/](http://www.mono-project.com/)

---

### Post by jocampo on 2009-08-12
> **jpdk said:**
> I am quite sure the 64bit Ubuntu desktop can handle 8 gigs of RAM. So I don't think that it will have any trouble recognizing all of it.

/Jay

Yeah, you are right about that, 64 bit has no problem with it. Did you setup Ubuntu server already? :P

---

