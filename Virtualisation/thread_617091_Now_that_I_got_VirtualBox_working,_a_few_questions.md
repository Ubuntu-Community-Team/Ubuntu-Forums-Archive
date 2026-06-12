---
title: "Now that I got VirtualBox working, a few questions..."
date: 2007-11-19
forum: Virtualisation
---

### Post by timzak on 2007-11-19
Thank you to everyone here who helped me to get VirtualBox working with my Win2k upgrade CD, and for helping me to learn about the guest additions.  This is sweet...

I have a few "curiosity" questions now that it's up and running:

1) Can you have more than one virtualization package installed at the same time?  Like VirtualBox and VMware?  And run the same OS through each?  I'd like to compare VMware to VirtualBox and how each runs Win2k, but not sure if they can be installed, or run, at the same time on the same machine.

2) Should I install antivirus software on the Win2k virtual machine?  I don't know if the guest OS can get infected?  I don't even use email on the guest, I mainly use it for financial software (MS Money), but I do access the internet through it via Firefox.

3) Are antispyware softwares necessary?  I tried installing Spybot Search & Destroy in the guest and after installing all the updates, it would no longer run.  When I'd launch Spybot, it never loads, but shows as a running process.  I have to force quit Spybot via Task Manager.  Is it not compatible with a Virtual OS?

4) Should I still defrag the guest OS?  I've used Win2k's built-in defrag utility, but I'm not sure if it matters in a VM?

Thanks,

---

### Post by Delvien on 2007-11-22
>  
1) Can you have more than one virtualization package installed at the same time?  Like VirtualBox and VMware?  And run the same OS through each?  I'd like to compare VMware to VirtualBox and how each runs Win2k, but not sure if they can be installed, or run, at the same time on the same machine.


Yes you can, in fact I have VirtualBox PUEL and Vmware server installed on my laptop and the same for my desktop i SSH to as a server.


Althought running 2 Virtual machines, unless you have a really nice PC or server, will get a little slow. I suggest running each Virtual machine with 256+ memory for the absolute BEST performance. Run them one at a time, unless you have a nice pc, again.

> 
2) Should I install antivirus software on the Win2k virtual machine?  I don't know if the guest OS can get infected?  I don't even use email on the guest, I mainly use it for financial software (MS Money), but I do access the internet through it via Firefox.

I dont see why it would hurt to install antivirus software (windows viruses dont affect linux hosts/guests, unless you are dumb enough to run stuff with sudo wine, but even then, its highly unlikely it will damage anything in your linux install/host/guest.) 

Check out ClamWin (open source virus scanner, and its free) very low system requirements and it doesnt bog down your virtualmachine.



> 3) Are antispyware softwares necessary?  I tried installing Spybot Search & Destroy in the guest and after installing all the updates, it would no longer run.  When I'd launch Spybot, it never loads, but shows as a running process.  I have to force quit Spybot via Task Manager.  Is it not compatible with a Virtual OS?

I'm not sure why people use spybot, its really not that good. Its slow, bogs down the system and on a Virtual Machine its kinda useless.

Check out Ad-Aware, can get it from Download.com, free for personal use and just run it every now and then when you think you are "infected"

>  4) Should I still defrag the guest OS?  I've used Win2k's built-in defrag utility, but I'm not sure if it matters in a VM?

Its just like a windows install, defrag speeds it up just a bit.

___________________________

Another thing to add:

Backup your VM by copying the VDI (virtualbox) or your VM folder (/home/USER/vmware) (vmware) to a USB or something so if your Virtual Machine gets a virus or spyware or whatever might happen, just copy and paste the file to the VDI folder or VMware folder and boom, you're back and ready for action.

---

### Post by timzak on 2007-11-24
Thank you for your help.

Cheers!

---

