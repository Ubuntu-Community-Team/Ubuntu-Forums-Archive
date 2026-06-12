---
title: "Migration of Ubuntu using VMware"
date: 2010-11-05
forum: Virtualisation
---

### Post by jelloso on 2010-11-05
Hi Guys!

I'm new here. I love Ubuntu. I just installed it in a VMware player on my laptop and wow. Lots of good stuff.

I need your help though.

I was planning to learn how to migrate my Ubuntu which is in a VMware player to another VMware player. I heard that this can be done with Qemu or KVM. But I'm not sure where to begin. Maybe one of these two since I am already using a virtual machine.

I would really appreciate the help.

Thanks.

:)

---

### Post by HermanAB on 2010-11-06
Howdy,

Figure out where the VM is, make a tar ball of the whole VM directory, copy it to the other machine using FTP/SSH/DVD/USB and untar it.

You can do all that with a right click in the file browser.

---

### Post by linux-hack on 2010-11-06
A vm is juste files. So if you copy these files you can use it where you want if you have the same program of course.

---

### Post by dcstar on 2010-11-07
> **jelloso said:**
> Hi Guys!

I'm new here. I love Ubuntu. I just installed it in a VMware player on my laptop and wow. Lots of good stuff.

I need your help though.

I was planning to learn how to migrate my Ubuntu which is in a VMware player to another VMware player.
......

As other have stated, just copy the whole VM folder to the new PC.

VMware Server VMs have a different hardware setting that you can change to enable extra Player features:

[http://ubuntuforums.org/showthread.php?t=1447951&highlight=virtualHW.version](http://ubuntuforums.org/showthread.php?t=1447951&highlight=virtualHW.version)

---

### Post by jelloso on 2010-11-10
Thanks for all the replies. But I'm thinking more of live migration set-up. I'm using the virtual machines for simulation purposes.

---

### Post by dcstar on 2010-11-11
> **jelloso said:**
> Thanks for all the replies. But I'm thinking more of live migration set-up. I'm using the virtual machines for simulation purposes.

What are you talking about?, VMware VMs are just a collection of files that you can copy to other VMware installation as much as you like - there is nothing to "migrate" apart from network settings and system configuration (and that is only if you want to run them simultaneously).

If you can clarify what you actually want to achieve then you may get something more useful.

---

### Post by darkhelmetchris on 2010-11-11
Yes, I agree with dcstar.  I have copied VMware machines containing Ubuntu, many times.  It works very well.  Apart from tweaking the .vmx file to give you different hardware settings, it's really just copy/paste the whole folder to a new location.  Such fun!

---

### Post by TJet1.8 on 2010-11-17
> **jelloso said:**
> Thanks for all the replies. But I'm thinking more of live migration set-up. I'm using the virtual machines for simulation purposes.

:lolflag:

Live migrations are not possible with VMware Player and/or Workstation...only ESX/vsphere with appropriate hardware/infrastructure/licensing (to the best of my knowledge).

Someone please correct me if I am wrong.

---

