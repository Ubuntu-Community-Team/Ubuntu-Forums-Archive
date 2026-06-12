---
title: "ubuntu 7.04 server does not run on vmware"
date: 2007-04-20
forum: Server Platforms
---

### Post by jlist on 2007-04-20
I installed 7.04 server on vmware workstation 5.5.1 It installs ok. At the end, when it reboots, vmware workstation pops up an error dialog "The CPU has been disabled by the guest operating system. You will need to power off or reset the machine at this point." I tried power off and on, and reset, and I keep getting the same error message from vmware (not from the guest OS.)

This happens when the guest OS screen shows "Starting up ..." after "Press Escape to enter the menu"

I ran an older version of ubuntu server on the same vmware workstation and it worked fine. Ubuntu 7.04 desktop works fine as a vm guest OS, too, on the same machine.

btw, this is a Windows XP host OS.

---

### Post by jimwillsher on 2007-04-20
I can't really answer your question, but 7.04 runs run on Virtual PC 2007, which is a free download.

Might be another option for you....



Jim

---

### Post by jlist on 2007-04-20
Thanks for the tip. Since I have some images for vmware, I'd really like to stick to vmware :)
BTW, I remember VPC 5 requires IIS, which annoys me. Is it still the case with VPC 2007?

---

### Post by jimwillsher on 2007-04-21
There was no VPC5.

VPC 2004 didn't require IIS and nor does VPC 2007. Perhaps you're thinking of Virtual Server 2005, which does require IIS.

---

### Post by jlist on 2007-04-21
Ah. You are probably right. It was a while ago. Anyway, I just took your advice and installed VPC 2007. When starting the ubuntu server install CD, after I selected install, the screen switched from VGA mode to text mode. However, the VPC window only displayed the upper half of the text mode screen...and the window can not be resized. Any idea what is happening? This is my first time using VPC 2007 though.

---

### Post by hinsdale on 2007-04-21
> **jimwillsher said:**
> I can't really answer your question, but 7.04 runs run on Virtual PC 2007, which is a free download.

Jim -

Were you able to get the 7.04 VPC 2007 session to capture your mouse pointer?  I upgraded my 6.10 VPC 2007 image to 7.04 this morning.  Everything runs fine except for mouse support -- which is kinda critical to run the GUI.  There are a number of threads in the forum asking about the mouse problem, so I wanted to see if you somehow got your mouse to work.

Regards,
Mark

---

### Post by BillJohnson on 2007-04-21
Upgrade to 5.5.3 (it's a free upgrade from 5.5.x - just download and install). I am running 7.04 Server on it with no problems (other than I need to figure out how to get telnetd installed, but that's not a vmware issue).

---

### Post by georgema on 2007-04-22
Hmm....

My first install of Ubuntu 7.04 Server and I'm getting the same issue as jlist. I'm installing on VMWare Workstation 6.0 RC2. As a first attempt I took the easy option of guided partioning with LVM and an 8GB SCSI drive on the LSI adapter.

Install all went fine followed by a reboot where it then barfed with the CPU disabled message. I run several other VM clients (Windows and Linux) on 6.o without any issues and don't really want to get into Virtual PC/Server at this point I'll have another go at this later and post something on the VMWare beta forums and see if anyone else has come across this.

Cheers,

---

### Post by _Mungo_ on 2007-04-22
> Upgrade to 5.5.3 (it's a free upgrade from 5.5.x - just download and install). I am running 7.04 Server on it with no problems (other than I need to figure out how to get telnetd installed, but that's not a vmware issue).

I upgraded to VMware 5.5.3 but same behaviour as described in the initial post.....

Ubunto 7.04 Server does not run on my XP SP 2 with VMware 5.5.3....

_Mungo_:(

---

### Post by jlist on 2007-04-23
> **_Mungo_ said:**
> I upgraded to VMware 5.5.3 but same behaviour as described in the initial post.....

Ubunto 7.04 Server does not run on my XP SP 2 with VMware 5.5.3....

_Mungo_:(

Same here. Upgrading to 5.5.3 didn't solve the problem. Ubuntu 7.04 runs ok on VPC 2007, if you can manage to install it :) Installation is tricky. I had to choose the screen resolution before installation starts, otherwise the text install screens only show upper half.

---

### Post by hinsdale on 2007-04-23
> **jlist said:**
> Same here. Upgrading to 5.5.3 didn't solve the problem. Ubuntu 7.04 runs ok on VPC 2007, if you can manage to install it :) Installation is tricky. I had to choose the screen resolution before installation starts, otherwise the text install screens only show upper half.

7.04 runs for me on VPC 2007, except that it won't capture the mouse in the virtual PC window.  Makes it kinda tough to run the GUI...

---

### Post by jimwillsher on 2007-04-23
This is what I've followed to get the screen issue overcome: [http://songhaysystem.com/document.php?kbDoc=unix_2076071762](http://songhaysystem.com/document.php?kbDoc=unix_2076071762)


Jim

---

### Post by jlist on 2007-04-23
> **hinsdale said:**
> 7.04 runs for me on VPC 2007, except that it won't capture the mouse in the virtual PC window.  Makes it kinda tough to run the GUI...

Hmmm. That's how I have been running all ubuntu guest OS in vmware. RedHat vmware tools worked for me but I wasn't able to make vmware tools work in any ubuntu guest.

Automatic mouse capture does not even work in command line mode (server installation) with vmware, which is kind of annoying. Command line mode mouse capture works in VPC 2007 w/o customization.

---

### Post by hampshirebrit on 2007-05-11
The problem applies to VMWare Workstation.  Ubuntu 7.04 runs fine on VMWare Server, which is free to license from VMWare.

---

### Post by [Neurotic] on 2007-05-29
I have the same issue running on Ubuntu 7.04, with VMware workstation 6..

The only information I could find was: [http://tinyurl.com/yuu4v2]("http://tinyurl.com/yuu4v2")

I really don't want to step outside vmware if I can.. but I'm a bit stuck?

---

### Post by mwexler on 2007-05-30
I posted on my blog about how I solved a similar problem for VirtualPC.  Try it, it may work for you.

[http://www.nettakeaway.com/tp/article/294/ubuntu-704-and-no-mouse-on-virtual-pc]("http://www.nettakeaway.com/tp/article/294/ubuntu-704-and-no-mouse-on-virtual-pc")

a workaround from [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87262]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87262") points to [https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=223606]("https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=223606") which say to include the kernel parameter i8042.noloop on the boot. This can be done manually each time on the liveCD (Press “f6” for additional options at the boot screen, and hand type it in) or if you install it, you can manually add this to the boot config file. On my tests with VirtualPC, this allowed the mouse to work as expected!

(For whatever reason, links are not showing properly.  Details at my blog at [http://tinyurl.com/2l4gl2](http://tinyurl.com/2l4gl2))

---

### Post by tjbearman on 2007-06-10
I have the same problem, using ubuntu 7.04Server as the guest OS
 and winXP/SP2 as host using VMWare 5.5.4
The install goes fine, grub loads the kernel and initrd, then the boot stops/fails completely
with no additional messages.
The same setup with ubuntu 7.04Desktop is perfect!
I've also tried parallels VM and I have the same problem with ubuntu 7.04Server
and the same success with ubuntu 7.04Desktop.
Seems like a ubuntu 7.04server issue...with grub, initrd?
Any help would be greatly appreciated.

TJ

---

### Post by seamuso on 2007-06-10
I'll add a little confusion for you .. running 7.04 desktop, vmware server installed (most current available from vmware), 7.04 server installs and runs perfectly.

[http://info.bluefrogcs.com/images/Screenshot.png](http://info.bluefrogcs.com/images/Screenshot.png)

---

### Post by jodie on 2007-06-11
After losing a harddrive on my XP workstion I upgrade to MS Vista.. VMWare 6x workstation upgrade was required. Ubuntu Server and Desktop installed with out any problems.. Every thing seems to be working except the above mentioned mouse problem.. 

Think my problem is not having the VMWare tools installed. Tried using the Install tools option in VMWare but nothing happens..

---

### Post by maxdom on 2007-07-07
I have the same problem with 7.04 server running as guest on a laptop Pentium M Win XP SP2 system using VMWare Workstation 5.5.1.
The same VM runs just fine on a stationary Intel Core2 Win XP MCE system.

SIW reports that the laptop CPU supports Intel SpeedStep, but I couldn't find a way to disable this as explained on the VMWare KB pages. (Neither Bios nor PowerOptions.) I tried setting the PowerOptions setting to MaxBattery, but no go. :(

Any other suggestions out there?

---

