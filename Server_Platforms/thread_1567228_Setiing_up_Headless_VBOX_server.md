---
title: "Setiing up Headless VBOX server"
date: 2010-09-03
forum: Server Platforms
---

### Post by carsonrose on 2010-09-03
I have a Windows 2008 R2 Server now... 20 or so users in this office, all desktops running Ubuntu 10.04, RDP to the W2K8 server and operate that way......... terribly slow!

I want to setup an Ubuntu Server with a headless VBOX to emulate windows for a specific CRM to run along with M$oft office. The only reason Im using office is because ACT! is dependent on outlook and word....

I'd like for each user to connect to the server in the back and perhaps have an icon for ACT, which is really just a VBOX session running windows......... Any ideas?

---

### Post by CharlesA on 2010-09-03
You can install Ubuntu Server on the machine and then install Windows Server 2K8 in virtualbox and do it that way.

Is that what you are trying to accomplish?

---

### Post by carsonrose on 2010-09-03
> **CharlesA said:**
> You can install Ubuntu Server on the machine and then install Windows Server 2K8 in virtualbox and do it that way.

Is that what you are trying to accomplish?


Actually yes. Is there a benefit to doing it that way? Will the VBOX W2K8 guest machine startup on its own? Will users be able to seamlessly connect to ACT and use office the same way they do now? Any performance issues?

---

### Post by carsonrose on 2010-09-03
Windows Server is slow, even with 8 gigs of ram and a quad core processor. Im trying to make this network move faster and provide document management... along with tying all this into a separate Asterisk server box.......

---

### Post by CharlesA on 2010-09-03
You would need to start the machine manually the first time, but as long as the machine is up and running, it won't need to be powered back on unless you reboot the main server (if that makes sense?)

I've got a few VMs running that I just "save state" when I need to reboot my main server.

---

### Post by carsonrose on 2010-09-03
> **CharlesA said:**
> You would need to start the machine manually the first time, but as long as the machine is up and running, it won't need to be powered back on unless you reboot the main server (if that makes sense?)

I've got a few VMs running that I just "save state" when I need to reboot my main server.


Cool... thanks for the quick replies. I will be setting this up all weekend, I"ll post any issues that pop up........

---

### Post by de0xyrib0se on 2010-09-03
Use ESXi from vmware, its built to be a hypervisor unlike running vbox on top of Ubuntu.

You can then install both Ubuntu and Windows into separate VMs and allocate resources to them as you please.

Its free and the vSphere client to manage it is free as well.

---

### Post by CharlesA on 2010-09-03
> **de0xyrib0se said:**
> Use ESXi from vmware, its built to be a hypervisor unlike running vbox on top of Ubuntu.

You can then install both Ubuntu and Windows into separate VMs and allocate resources to them as you please.

Its free and the vSphere client to manage it is free as well.

ESXi only runs on specific hardware, if I am not mistaken.

See here: [http://www.vmware.com/resources/compatibility/search.php](http://www.vmware.com/resources/compatibility/search.php)

If you are just running 1 VM, you might as well just use VirtualBox.

---

### Post by de0xyrib0se on 2010-09-03
It runs on anything 32&64 bit we've put it on.

---

### Post by CharlesA on 2010-09-03
Interesting. Thanks!

---

### Post by Jamina1 on 2010-09-03
.

---

### Post by Jamina1 on 2010-09-03
> **de0xyrib0se said:**
> It runs on anything 32&64 bit we've put it on.

I have a 32 bit box I'd love to drop it on once I get some more RAM, but the ESXi site says it only runs on 64-bit. Will it actually run on 32?

---

### Post by CharlesA on 2010-09-03
> **Jamina1 said:**
> I have a 32 bit box I'd love to drop it on once I get some more RAM, but the ESXi site says it only runs on 64-bit. Will it actually run on 32?

You'd need the older version. 3.5 IIRC.

---

### Post by de0xyrib0se on 2010-09-04
Charles is correct, the older version runs on 32bit, latest is geared towards 64 bit.

We run both and cant tell much difference, besides the platform.

---

### Post by carsonrose on 2010-09-04
So I should just setup the Ubuntu server, enable rdp... The users RDP into the server, into their remote session, and start a VBox session? So I would technically have 20 vbox sessions going??

Am I thinking of this correctly? Wouldnt this take a serious toll on system resources?

---

### Post by de0xyrib0se on 2010-09-04
If you are looking to have a remote desktop Windows environment for 20 users and a dedicated voip vm in one box then;

1. Install ESXi (you could do it with Ubuntu EC), appropriate one for your platform.
2. Install Ubuntu into a VM node and whatever tweaks on top of it to have a dedicated voip node.
3. Install Windows Server 2003/2008 into a VM node and purchase 20 terminal service cals, enable terminal services and let your users RDP into the server. Install any applications you want them all to use.

---

### Post by carsonrose on 2010-09-04
> **de0xyrib0se said:**
> If you are looking to have a remote desktop Windows environment for 20 users and a dedicated voip vm in one box then;

1. Install ESXi (you could do it with Ubuntu EC), appropriate one for your platform.
2. Install Ubuntu into a VM node and whatever tweaks on top of it to have a dedicated voip node.
3. Install Windows Server 2003/2008 into a VM node and purchase 20 terminal service cals, enable terminal services and let your users RDP into the server. Install any applications you want them all to use.

I have a separate asterisk server, mySQL, apache and 2 windows servers. I am keeping one up just in case we get into trouble. I already have 20 TS CALs. 

I guess my questions is really this:

If I install VB on the server... the agents will RDP into their desktop session... will they have to open and initiate a VBox session, thereby creating another VBOX session on the server, or will they have access to one already running... and just have to loging under their names?

Am I explaining this correctly?

---

### Post by de0xyrib0se on 2010-09-04
What exactly do you mean by "their deskto psession"? Would you be running one VM per user with say Windows XP as the guest OS?

---

### Post by carsonrose on 2010-09-04
Yes.... The users need to be able to use ACT and OFFICE. Everything else would be on the linux desktop. 

They remote in from their machines in their respective departments, Sales, Collections, Accounting, Etc... Just the way they do now... An Ubuntu login screen apears, they login and they are give a desktop session... Just like Terminal Services does for windows....

When they login, to access the virtual box running XP, they would be able to run that in seamless mode and access ACT and Office. 

I dont want 20 different VM's running on the server........... I want a login screen to appear and everyone login to the same virtual windows server...........

):P

---

### Post by carsonrose on 2010-09-04
The reason behind wanting to do this is because I am on a mission to get rid of windows entirely. 

I am replacing ACT with vTiger and Office with Open Office.... Thunderbird for email. Right now, we are still tweaking vTIger........ so we are forced to still use ACT for the time being... within 60 days I want to be using vTiger .........

---

### Post by de0xyrib0se on 2010-09-04
Well unless you install Windows Server there is no way of not having 20 VMs running.

---

### Post by CharlesA on 2010-09-04
Why can't they just RDP onto the Windows server and do all their tasks there?

It seems like a hell of a lot of work to have them RDP into a VM running XP that connects to a Windows server.


EDIT: I think I might be confused - You have desktops running Ubuntu 10.04, that RDP into a windows server now, correct?

There shouldn't be any problem with just virtualizing that server and just leave it set up as it is.

What I'd do would be to use clonezilla to backup the entire server install and then clone it onto a VM and see if that works.

Sidenote: I've never had any problems using RDP to connect to a windows server from Ubuntu (slowness, etc). Maybe I am just lucky.

---

### Post by houndi on 2010-09-05
Windows Server is slow, even with 8 gigs of ram and a quad core processor. Im trying to make this network move faster and provide document management

---

### Post by carsonrose on 2010-09-05
Guess i read this post a little late... doing a full reinstall of W2k8...

---

### Post by CharlesA on 2010-09-06
Are you just installing it in a VM and going from there?

That's probably the easier way to do it, since I haven't had much success going from physical machines to VMs without having to do a reinstall.

---

### Post by sandyeggoboy on 2010-09-30
HI i just read your post with a great deal of interst.... i am pretty much doing this exact same thing right now on my system, only i am using VBoxHeadless to run an installation of WIndows Home Server. I have an AMD Athlon X2 with only about 719 Meg of RAM and a 500-gig SATA drive as my boot drive, and a 300-Gig drive as my host drive foir the WHS. When i first set this thing up i noticed that I could do RDP into it without a problem, and in fact installed  a couple of apps (wordpress, mysql, php5, etc .....) into the IIS. Very handy dandy. the only problem i think is that when one machine hasa problem i dont realy know about it right away..... SO ia m now looking at a copuple of different network monitoring tools .... 

Anyway, thats how i did it, if you need more info please feel free to PM me ...

---

### Post by canonhead311 on 2010-10-07
I am having some major issues installing a headless VBox system... I got Ubuntu Server 10.04 setup with no desktop, only CLI and I am using ssh through a CLI term on my Ubuntu 10.04 laptop. I'm still fairly new to linux so this has been rough on me. I originally install server then added the Gnome Desktop to it and VNCed into it all the time, now I did a fresh install and setup a basic smb server so that I can access all my stuff. Next the first thing I wanted to do was setup a virtual ubuntu server machine so that I could mess that up, by playing with stuff and testing things out and then when it was successful I would set that up on my actual phys server.

I have tried a few approaches. I added the VBox module to webmin and created a virt machine and tried to boot with a iso of Ubuntu server, and it won't start (no errors just doesnt start). Next I installed PHPVirtualBox and managed to set that up as well but when I try to change the settings of the machine to boot from the iso it freezes on my and I have to refresh the page. Then I set it up in CLI and when I go do VBoxHeadless --startvm "Ubuntu Server"   it will start the virt machine but then hangs and I have to ctrl^C to get back to the prompt. If I let it run and check phpvirtualbox it says its running but nothing happens.

I tried this as well on my laptop and got the same issues, just instead of using phpvirtualbox i used vbox ose gui and it says its running. When I start the machine from the GUI it loads and starts the ubuntu server iso install...

Anyways, with all that hopefully someone can give me a good link or so info as to why it wont run through the command line.  Thanks all.

---

### Post by carsonrose on 2011-02-11
I wonder if an xterm CLI wouldnt work out better....... hmmmm

---

