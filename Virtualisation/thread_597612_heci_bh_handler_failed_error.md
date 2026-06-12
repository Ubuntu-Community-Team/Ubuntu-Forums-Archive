---
title: "heci_bh_handler failed error"
date: 2007-10-30
forum: Virtualisation
---

### Post by bsimmons on 2007-10-30
I am a relative newbie to UBUNTU, though I have some SCO admin experience.

I've installed Gutsy Gibbon and with much help from the various forums have VMWare Server up and running.

I am configuring my first virtual machine and the UBUNTU host machine is displaying this error repeatedly:

Heci: schedule work the heci_bh_handler failed error=0

I've done searches on the VMWARE site and here, as well as some general googling and I can't seem to find anything on what this error is.

If anyone has any pointers for me I'd be most appreciative.

TIA,

bsimmons

---

### Post by pgl on 2008-10-02
> **bsimmons said:**
> I am a relative newbie to UBUNTU, though I have some SCO admin experience.

I've installed Gutsy Gibbon and with much help from the various forums have VMWare Server up and running.

I am configuring my first virtual machine and the UBUNTU host machine is displaying this error repeatedly:

Heci: schedule work the heci_bh_handler failed error=0

I've done searches on the VMWARE site and here, as well as some general googling and I can't seem to find anything on what this error is.

If anyone has any pointers for me I'd be most appreciative.

TIA,

bsimmons

Did you ever figure this out? I'm currently seeing the message show up quite frequently and have no idea what it means. There's not exactly a wealth of information provided with hardy about it:

[FONT="Lucida Console"]```
[COLOR="#8b0000"][mybox:pgl]:~ $ man heci
No manual entry for heci

[mybox:pgl]:~ $ whatis -w '*heci*'
*heci*: nothing appropriate.

[mybox:pgl]:~ $ locate heci
/lib/modules/2.6.24-19-generic/ubuntu/misc/heci
/lib/modules/2.6.24-19-generic/ubuntu/misc/heci/heci.ko
```[/COLOR][/FONT]

This is all I can see in the boot messages:

[FONT="Lucida Console"]```
[COLOR="DarkRed"]Oct  1 16:10:41 mybox ernel: [   46.822432] heci: link layer has been established.
Oct  1 16:10:41 mybox kernel: [   46.850753] Linux agpgart interface[/COLOR]
```[/FONT]

How does something like this get shipped with **** all to explain what it is? I don't get it.

---

### Post by nilgiri on 2009-11-12
I have the same issues.  There is all I found of use so far:
[http://en.wikipedia.org/wiki/HECI](http://en.wikipedia.org/wiki/HECI)

I thinking that newer versions of something (xen kernel maybe?) will have this fixed, but I don't see upgrading xen until 10.04 comes out, assuming Ubuntu supports xen in LTS moving forward.  So, if i get a chance to reboot this machine, I'm going to poke around in the bios and flip some settings related to APCI or anything else that seems like it might be related.

Are you guys running xen?  Some other kind of virtualization?

bsimmons, I see references to VMWare.  Are you getting your errors from the guest or the host?  I'm getting them on the host.

---

