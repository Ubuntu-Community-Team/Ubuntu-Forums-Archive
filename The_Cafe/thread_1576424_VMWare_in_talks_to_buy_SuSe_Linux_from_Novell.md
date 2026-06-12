---
title: "VMWare in talks to buy SuSe Linux from Novell"
date: 2010-09-17
forum: The Cafe
---

### Post by Sporkman on 2010-09-17
> Novell (NOVL) is in “advanced talks” to sell its SuSE :Linux business to VMware (VMW), the Wall Street Journal reports...

[http://blogs.barrons.com/techtraderdaily/2010/09/16/novell-in-talks-with-vmware-on-suse-linux-unit-wsj-says/?mod=yahoobarrons](http://blogs.barrons.com/techtraderdaily/2010/09/16/novell-in-talks-with-vmware-on-suse-linux-unit-wsj-says/?mod=yahoobarrons)

---

### Post by Naiki Muliaina on 2010-09-17
What sort of company are VMWare? Good guys, bad guys, something in between? Play things straight or crooked?

---

### Post by forrestcupp on 2010-09-17
That's kind of disappointing.

> **Naiki Muliaina said:**
> What sort of company are VMWare? Good guys, bad guys, something in between? Play things straight or crooked?

They seem to play things straight, but about all of their main software is proprietary.  I don't have a problem with proprietary software, but on the other hand, I don't necessarily think a company that is almost completely proprietary is a good one to run a popular Linux distribution.

---

### Post by Paqman on 2010-09-17
> **forrestcupp said:**
> 
They seem to play things straight, but about all of their main software is proprietary.  I don't have a problem with proprietary software, but on the other hand, I don't necessarily think a company that is almost completely proprietary is a good one to run a popular Linux distribution.

VMWare's distinguishing characteristic isn't what licence they release software under, it's the fact that they're massive in servers. Buying into Linux development is a pretty reasonable move if you're in the server biz. Their virtualisation products will be running on Linux a lot after all.

---

### Post by beew on 2010-09-17
At least it is not Oracle.

---

### Post by koenn on 2010-09-17
> **Paqman said:**
>  Their virtualisation products will be running on Linux a lot after all.
They use Linux **in** their virtualization products -- the cli management console inside ESX is a shell on a linux kernel, and that linux kernel also serves as boot loader for the ESX's actual vmkernel. 

Maybe that's why they'd like to acquire their own linux ...

There's also a market for Linux as OS in VMware Virtual Appliances - maybe they want more influence there as well.

---

### Post by koenn on 2010-09-17
> **Naiki Muliaina said:**
> What sort of company are VMWare? Good guys, bad guys, something in between? Play things straight or crooked?
They're a business.
If "Open Source" tells them it offers quality software that they can modify to suit their needs, they might just take that offer.

---

### Post by Paqman on 2010-09-17
> **koenn said:**
> They use Linux **in** their virtualization products -- the cli management console inside ESX is a shell on a linux kernel, and that linux kernel also serves as boot loader for the ESX's actual vmkernel. 


Interesting. So when they say that ESX doesn't require an OS, that's because it's a sort of Frankenstein mishmash or an app and an OS itself?

> 
There's also a market for Linux as OS in VMware Virtual Appliances - maybe they want more influence there as well.

That's what I was figuring. Will be interesting to see though.

---

### Post by koenn on 2010-09-17
> **Paqman said:**
> Interesting. So when they say that ESX doesn't require an OS, that's because it's a sort of Frankenstein mishmash or an app and an OS itself?

technically, it's an OS, but not a general purpose OS.
It runs on bare metal and abstracts the hardware to the "applications" - applications in this context meaning the process(es) that constitute the guest operating system(s). In contrast, VMware Server (or, say, Virtualbox) is an application that requires a _host_ operating system  

the linux kernel is
a/ a boot loader for the actual OS (vmkernel)
b/ just another process that offers an interface to the VMware OS (it offers ssh for remote administration and a shell that can process system administration commands)
wikipedia has quite a good description : [http://en.wikipedia.org/wiki/VMware_ESX](http://en.wikipedia.org/wiki/VMware_ESX)

---

### Post by conundrumx on 2010-09-17
This actually doesn't make sense for them to do, as ESX is targeted for deprecation.  ESXi is the new hotness for VMware, it's much lighter and is written entirely by them instead of the current CentOS/Redhat based OS ESX runs on top of.

---

### Post by KiwiNZ on 2010-09-17
VM Ware is a good company to deal with.

---

### Post by koenn on 2010-09-17
> **conundrumx said:**
> This actually doesn't make sense for them to do, as ESX is targeted for deprecation.  ESXi is the new hotness for VMware, it's much lighter and is written entirely by them instead of the current CentOS/Redhat based OS ESX runs on top of.


hm, yeah. 
And I also never got what they wanted Zimbra for.

They must be up to something

---

### Post by kevin11951 on 2010-09-17
<conspiracy>

Aren't these all Microsoft's biggest competitors?  Zimbra, SUSE Linux, etc...

</conspiracy>

---

### Post by kevin11951 on 2010-09-18
> **kevin11951 said:**
> <conspiracy>

Aren't these all Microsoft's biggest competitors?  Zimbra, SUSE Linux, etc...

</conspiracy>

</thread>?

---

### Post by Dustin2128 on 2010-09-18
I tried SUSE, didn't like it. Therefore: I care not.

---

