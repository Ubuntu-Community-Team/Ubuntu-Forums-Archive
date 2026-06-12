---
title: "Copy and paste to virtual XP machine"
date: 2009-03-30
forum: Virtualisation
---

### Post by EvilPeppard on 2009-03-30
I am using VMWare 2.0 on Ubuntu 8.10 64 bit. I cannot copy information between my Ubuntu desktop and my virtual Windows XP desktop. Is there something I need to enable or some step I need to follow?

I did a search and found a reference to installing VMware tools on the client VM machine, but the instructions were written like I was running a VM version of Linux, not Windows.

Thank you in advance for any assistance.

---

### Post by Mark20 on 2009-03-31
I'm sure you can copy and paste from a Windows host to a Linux guest (like your instructions suggested) but you can very easily go the other way too.  I'm using Ubuntu 8.10 (32 bit) and I have a Windows XP guest.  All I did was download [VMware tools]("http://www.vmware.com/download/ws/") and install that (on my XP virtual machine).  Once it was installed copy and paste worked no problem.  I don't see why it wouldn't work for 64 bit but I haven't messed around with 64 bit yet...

I downloaded VMware tools as follows:
1) Download VMware Workstation, then extract file (I think it was a zip)
2) Inside the zip file you'll find a file called "Windows.iso".  Either burn it to a CD or mount it.  Find the setup file, and use it to install VMware Tools, AFAIK you cannot download VMware tools separately.

Good luck,
Mark

---

### Post by EvilPeppard on 2009-04-02
> **Mark20 said:**
> I'm sure you can copy and paste from a Windows host to a Linux guest (like your instructions suggested) but you can very easily go the other way too.  I'm using Ubuntu 8.10 (32 bit) and I have a Windows XP guest.  All I did was download [VMware tools]("http://www.vmware.com/download/ws/") and install that (on my XP virtual machine).  Once it was installed copy and paste worked no problem.  I don't see why it wouldn't work for 64 bit but I haven't messed around with 64 bit yet...

I downloaded VMware tools as follows:
1) Download VMware Workstation, then extract file (I think it was a zip)
2) Inside the zip file you'll find a file called "Windows.iso".  Either burn it to a CD or mount it.  Find the setup file, and use it to install VMware Tools, AFAIK you cannot download VMware tools separately.

Good luck,
Mark
Thanks for your response. I found out, to install the VMWare tools to my virtual machine, all I had to do was go to my VM console, highlight the virtual machine I wanted to install the tools on, then click the link on the right "install VMWare tools". :)

I didn't realize it was that simple, but this process successfully installed the VM tools. I can now copy text from my main Ubuntu machine to my virtual host, but I cannot copy text from the VM machine back to my Ubuntu machine. Weird.

---

### Post by Mark20 on 2009-04-02
Ahhh my mistake.  I'm using VMware Player and it's pretty stripped down.  I think they purposely exclude features so that people will buy workstation instead.  I didn't know it was that easy to do with other VMware products.

---

