---
title: "Virttualization with KVM on Ubuntu Server 9.04"
date: 2009-10-08
forum: Server Platforms
---

### Post by mdonodeo on 2009-10-08
Hello I’m a newb to Linux, but not to Windows. I want to virtualize three Windows Servers using KVM on Ubuntu 9.04 Server edition. First off is this even possible? I have a HP Prolient DL385G1 4GB RAM, 2 dual core Optron 2.0GHz. Could someone let me know what the specs should be? Or should I even attempt this, and a guide to get me started? :confused:

  Thanks,
  Mike

---

### Post by Lars Noodén on 2009-10-09
Look at the package **qemu-kvm**  

[https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)

You'll want extra RAM in that machine especially if all are to run at the same time.  

If you have two hard drives, the try to ensure that the VM images are on a different physical device than the swap space.

---

### Post by scorp123 on 2009-10-09
> **mdonodeo said:**
>  I want to virtualize three Windows Servers using KVM on Ubuntu 9.04 Server edition. I'd use something else for that.

Some people on these forums here would suggest VMware ESX ... but that one costs money. Then there is the free (but limited in its features) VMware ESXi ... for a bit of server virtualisation it might still be good enough. And then there is Citrix XenServer which has most (if not even all?) features of VMware ESX and which can be downloaded for free as well.

If it really has to be free and it has to be KVM I'd use ProxMox:
[http://www.howtoforge.com/kvm-and-openvz-virtualization-and-cloud-computing-with-proxmox-ve](http://www.howtoforge.com/kvm-and-openvz-virtualization-and-cloud-computing-with-proxmox-ve)

[http://pve.proxmox.com/wiki/Main_Page](http://pve.proxmox.com/wiki/Main_Page)

"ProxMox" is in principle a special Debian-based Linux distro that totally focusses on virtualisation. It can do clustering, live migration of VM's .... and all that for free ("free" as both "gratis" in GNU General Public License). So if those Windows servers are important ("important" as in: they should not go down. Ever) then this might be better suited than e.g. Ubuntu?

Don't get me wrong. I like Ubuntu. But setting up a clustered KVM solution would be a royal pain to setup here. Hence why I'd look at "ProxMox" or --depending on the budget and your preferences-- at other solutions altogether (XenServer, VMware ESX ...)

---

### Post by Lars Noodén on 2009-10-09
VMware used to be better than it is.  I would not recommend anything from Citrix at all, ever.  

If qemu is not attractive enough, then there is virtual box.  qmeu has some features lacking in virtualbox and vice versa.

---

### Post by scorp123 on 2009-10-09
> **Lars Noodén said:**
>  I would not recommend anything from Citrix at all, ever. And why is that? Their XenServer isn't so bad, IMHO. And opposite to the crippled VMware ESXi you at least get a method of moving your VM's via "XenMotion". Is there any particular reason why you don't like Citrix?

---

### Post by Lars Noodén on 2009-10-09
Who said anything about like or dislike?  I said I do not recommend it, ever.  I'm willing to go into more detail about citrix, on the clock, but keep in mind that my rates would be 1500DKK / hour, minimum 4 hours.  

If you need virtualization using linux as a host, your best options are virtualbox or qemu.

---

### Post by scorp123 on 2009-10-09
> **Lars Noodén said:**
>  I said I do not recommend it, ever. Yes, I understood you perfectly. But I was just wondering if there was any objective / technical reason behind this (e.g. missing feature of some sorts? Lack of functionality of some sorts?) or if this was something personal like *"I don't like Ubuntu because it's so brown"* ...

See what I mean?

---

### Post by Lars Noodén on 2009-10-11
@ scorp123   : 1500 DKK / hour, minimum 4 hours.  Show me the money first.

---

### Post by scorp123 on 2009-10-12
> **Lars Noodén said:**
> @ scorp123   : 1500 DKK / hour, minimum 4 hours.  Show me the money first. You can simply answer to a question, yes? You could as well just answer "it's a matter of personal taste" and that's it.

BTW; my hourly rates are considerable higher, LOL ):P

You are in no position to brag about your price tag :lol:

---

### Post by Lars Noodén on 2009-10-12
@ scorp123  : who said anything high or low.  Or bragging.  Show me the money.

---

### Post by scorp123 on 2009-10-12
> **Lars Noodén said:**
> @ scorp123  : who said anything high or low.  Or bragging.   You certainly are bragging with your ridiculous "1500 DKK per hour". LOL. It just isn't working. :lol:

> **Lars Noodén said:**
> Show me the money.

[IMG]http://www.swisster.ch/multimedia/images/img_traitees/2008/03/geld_news_zoom.jpg[/IMG]

):P

But seriously now: You really think that this kind of "peeing contest" that you're inscenating here is helpful to OP or anyone else? You said you "don't recommend Citrix. Ever" --- so again: **Any technical reasons for this?** That is assuming of course that you are capable of formulating your --possibly valid?-- reasons into a short sentence or so, so that OP and others may benefit from your insights?

---

### Post by ricojonah on 2009-10-18
I fully agree. If someone wanted payment for their opinion (or other subjective terms for information), I'd really find a rate like that to be very questionable. For stooping to solicitations for money from a FOSS-based community of individuals, surely a rate like that is open to heavy negotiation! :P

I'm curious about the comparisons too. Does anyone else have any reasons to argue against using a Citrix solution?

---

### Post by Pnuts on 2009-10-19
For what its worth, I ran an Ubuntu 9.04 server that was dedicated to KVM + libvirt for about 4 months. Had 4-6 Ubuntu guests and had no problems with it.

I have however, recently just made the change to VMWare ESXi. Hosting the same 4-6 Ubuntu guests again. So far it appears to be slightly better performance wise, however, I have not done any benchmarks or anything, this is simply my perception. I am also by no means taxing this machine, each individual VM just seems quicker to respond.

Despite ESXi being limited in its features as someone above mentioned, It meets all of my needs and exceeds what was available with KVM + libvirt. There are other KVM options I did not try though that may negate this fact.

The system I am using is a Dell Optiplex 760, 3.0ghz Dual Core with 8gb of RAM, 3x320gb drives in hardware RAID 5, 2nd gigabit NIC added.

-Pnuts

---

### Post by dusundurt on 2011-02-26
> **Lars Noodén said:**
> Who said anything about like or dislike?  I said I do not recommend it, ever.  I'm willing to go into more detail about citrix, on the clock, but keep in mind that my rates would be 1500DKK / hour, minimum 4 hours.  

If you need virtualization using linux as a host, your best options are virtualbox or qemu.

does this help anyone?

---

### Post by jbrown96 on 2011-02-26
What version of Windows Server. 2008R2 is a disk hog and needs quite a bit of memory as well. [http://www.microsoft.com/windowsserver2008/en/us/system-requirements.aspx](http://www.microsoft.com/windowsserver2008/en/us/system-requirements.aspx)

I really like KVM, but I wouldn't use it with Ubuntu. Fedora is a much better distro if you want to use KVM, which is what I use.


Virtualbox is not an appropriate platform for server virtualization. Xen is also good, but I don't have much experience. I can help you with KVM on Fedora, specifically F14.

---

