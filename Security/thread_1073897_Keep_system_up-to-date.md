---
title: "Keep system up-to-date"
date: 2009-02-18
forum: Security
---

### Post by ngmachado on 2009-02-18
Hi,

I run a Ubuntu Server 8.04 LTS.

I've always heard that one of the most important things to prevent security breaches is keep the software on our system up-to-date. 

To accomplish this, every week I run the command:

```
sudo apt-get update && sudo apt-get upgrade
```

My question is, am I doing this the 'right' way? Is this enough to keep my system up-to-date? 

Other hints will be greatly appreciated.

---

### Post by bodhi.zazen on 2009-02-18
That is IMO sufficient ;)

---

### Post by listerdl on 2009-02-18
thats interesting to know...thanks for code

---

### Post by tubezninja on 2009-02-18
Just bear in mind that some updates, occasionally, are linux kernel updates.  For those to take effect, a reboot is required.

It's a good idea to [look at the security notices]("http://ubuntu.com/usn") and see if the updates you're applying state they require a reboot to take effect, and decide for yourself whether or not you want to reboot.

---

### Post by itang sanjana on 2009-02-19
doesn't Ubuntu Keep the system up-to-date automatically?
Sometimes I get notified more than once a week.
CMIIW

---

### Post by bodhi.zazen on 2009-02-19
> **itang sanjana said:**
> doesn't Ubuntu Keep the system up-to-date automatically?
Sometimes I get notified more than once a week.
CMIIW

It will notify you if updates are available but will not automatically update unlesss you configure it to do so.

If I configure automatic updates I do security only.

---

### Post by itang sanjana on 2009-02-19
> **bodhi.zazen said:**
> It will notify you if updates are available but will not automatically update unlesss you configure it to do so.

If I configure automatic updates I do security only.

Oh, thank you for the correction
:)

---

### Post by listerdl on 2009-02-19
> **bodhi.zazen said:**
> If I configure automatic updates I do security only.

Why do you only do security?

---

### Post by bodhi.zazen on 2009-02-19
> **listerdl said:**
> Why do you only do security?

Well, you see, it depends.

First security updates are much more important and there is no good reason to delay them.

With the non-security, in general, I like to review the updates first. Although rare, updates may cause breakage and I want to know what happened (knowing what was updated is the first step to solving any problems I may have).

If it is a non-security update, what is the rush, is there a feature I need => update.

If my system is working just fine, no harm done in waiting a few days or once a week or so.

So, lets look at the updates .. Is there a kernel update -> well then I will need to close out what I am doing and reboot. With kernel updates that may affect my nvidia, wireless, virtuabox, and/or vmware kernel modules ...

You get the idea.

If there are many updates, do I need to make a back up first ? Are there any reports on the forums of problems after updating ?

Last is this my stable workstation that I rely on for day to day tasks or is this a test machine running in a VM ? If it is a mission critical server / workstation I take more caution with updates, perhaps update a VM first. If it is a VM, and I am running 9.04 Alpha, updates may break things, such as X ...

---

