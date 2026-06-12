---
title: "Linux &quot;image&quot;"
date: 2021-05-05
forum: Virtualisation
---

### Post by reuvygroovy on 2021-05-05
We are trying to create a new Ubuntu image for automation purposes, so we can automatically via script deploy new VMs on demand. Are there existing configuration scripts etc. or the like which enable us to do what silently? Or do we have to create a sample VM, and the copy if over and over again?

---

### Post by TheFu on 2021-05-05
The hardware involved will determine much, as will the exact ubuntu release used as the base.

If you are trying to run a VM on ARM, the answer would be very different than running a VM on AMD64. 

Same for the hypervisor used.  Vagrant is used with virtualbox by developers millions of times a day. I've not heard any vagrant users with KVM/libvirt, however.

Some enterprises use a read-only CoW backed file for their hypervisors. Then any local changes are put into a different CoW storage device. So, a single base image gets shared by 1,000 VMs.  When it is time to upgrade the VMs, they create a new read-only CoW storage device and let the VM clients choose to upgrade - which has a reboot and just points to the new CoW file with all the patched stuff.  There are lots of ways to handle this.

Some ideas:
[https://www.unixmen.com/qemu-kvm-using-copy-write-mode/](https://www.unixmen.com/qemu-kvm-using-copy-write-mode/)
[https://libvirt.org/storage.html](https://libvirt.org/storage.html)
[https://www.kernel.org/doc/html/latest/virt/uml/user_mode_linux_howto_v2.html#using-layered-block-devices](https://www.kernel.org/doc/html/latest/virt/uml/user_mode_linux_howto_v2.html#using-layered-block-devices)

---

### Post by scorp123 on 2021-05-06
> **reuvygroovy said:**
> We are trying to create a new Ubuntu image for automation purposes, so we can automatically via script deploy new VMs on demand. Are there existing configuration scripts etc. or the like which enable us to do what silently? Or do we have to create a sample VM, and the copy if over and over again?

At one of my previous employers we used **Cobbler** for this.
[https://cobbler.github.io/]("https://cobbler.github.io/")
[https://en.wikipedia.org/wiki/Cobbler_(software)]("https://en.wikipedia.org/wiki/Cobbler_(software)")

Further customisations were then done with **Ansible** ...
[https://www.ansible.com/]("https://www.ansible.com/")
[https://en.wikipedia.org/wiki/Ansible_(software)]("https://en.wikipedia.org/wiki/Ansible_(software)")

... and/or **Puppet** ...
[https://puppet.com/]("https://puppet.com/")
[https://en.wikipedia.org/wiki/Puppet_(software)]("https://en.wikipedia.org/wiki/Puppet_(software)")

(Usually you wouldn't use or need Ansible *and* Puppet ... either is powerful enough to do all needed customisations. The reasons my team ended up with both was historical: Multiple divisions and groups inside the company were split off and attached to new divisions, new groups. My team ended up getting merged with another team and whatever infrastructure they had. That's how we ended up having to work with both products ... )

We didn't do a single thing manually, not even installing the base OS. Doing anything manually outside of Cobbler, Ansible or Puppet was frowned upon.

There's quite a steep learning curve to all that, yes. But having good knowledge about these products looks fantastic on any CV and will get you bonus points in any future job interview. Totally pays off learning all that. It certainly did for me. :-D

---

### Post by TheFu on 2021-05-06
The cobbler infrastructure to push installations to other systems doesn't work on 20.04 Ubuntu.  A CentOS or RHEL server is needed for that.  I know the Ubuntu devs have a bug open about that support.  Just noticed this a few days ago.  At my current job, we don't create new VMs very often. I have a few servers that started out running Ubuntu Server 8.06 and have been upgraded all this time, LTS to LTS.

I know ansible works from 20.04 just fine.

+1 Ansible.  Cobbler was created before Ansible by the same guy, BTW. I understand he worked at Puppet Labs and decided a much simpler tool was needed before going off to make Ansible.

---

### Post by scorp123 on 2021-05-07
> **TheFu said:**
> The cobbler infrastructure to push installations to other systems doesn't work on 20.04 Ubuntu. 
Oh? Wasn't aware of that. I changed jobs in 2019 (before 20.04 was released) so I wouldn't know that ...

> **TheFu said:**
>  I understand he worked at Puppet Labs and decided a much simpler tool was needed before going off to make Ansible.
Yes, I can imagine. :lolflag:

Don't get me wrong. Puppet is absolutely powerful. And watching a fully configured Puppet environment basically auto-administrating itself + auto-installing software + auto-deploying patches everywhere because your latest "git push" just told it to do so is breathtaking. Almost magical. And scary too. Makes you wonder how long it will take until your colleagues and you get replaced by a few lines of Puppet code too, because it sure does not look like you're needed. 

Watching that same environment automagically burn itself to the ground because your latest "git push" contained a few small but critical semantic errors that gets applied to every class of host is breathtaking too. Been there, done that. :lolflag:  (No, not the reason I changed jobs ... :-D  )

Ansible is soooo much easier to get into, to get stuff done with and achieve pleasing results, and it's so much easier to understand and maintain code that others have written. 

Puppet... yes, wicked powerful. No doubt. But I never ever want to work with it again, no thanks. :lolflag:

---

### Post by TheFu on 2021-05-07
In the puppet training, they asked a room with 200+ people how many had puppet maintaining their entire environment 100%.  3 people, all from the same group, raised their hands.  They'd taken up Puppet like a religion, attending every class available, had on-site puppet installation support guys, everything offered - they had.

Also, that group had left 2 people behind because sometimes bad things happen.

To me, puppet seemed worse than the problem I was trying to solve.  We had custom ssh scripts for managing systems for decades. They grew out of custom rsh scripts for the same purpose, so puppet wasn't really all that magical to us.  What we lacked was the standardization that a popular DevOps tool brings and the ability to hire people with that skill already.  Bash/ksh scripts are fine, but more and more "admins" just don't arrive with even basic scripting knowledge. It really is sad.  

People claiming to be admins are afraid to make a 25 line backup script. So very sad.

The great thing about ansible is yaml.
The terrible thing about ansible is yaml.

---

### Post by scorp123 on 2021-05-07
> **TheFu said:**
>  The great thing about ansible is yaml.
The terrible thing about ansible is yaml.

:lolflag:

---

