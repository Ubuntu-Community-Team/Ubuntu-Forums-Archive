---
title: "Which Virtualization software do you prefer?"
date: 2008-06-21
forum: Virtualisation
---

### Post by diablo75 on 2008-06-21
I've been using VMware for a while, but the frequent kernel updates are really getting annoying because I have to recompile the headers over and over (often times for other people who can't do it themselves with confidence).

So I'm trying to find something that's a little more simple; little less dependent on me fixing it because it can't keep in step with kernel updates.

I've looked into Virtual Box, but it's been a while since I last tried it and got a bad impression; I want to give it another chance.

What other ones are out there?

---

### Post by Drakkor on 2008-06-22
I can't say as to other VMs,but I like VirtualBox, I have a dual-boot machine,2 dedicated partitions, one with Vista,the other with Ubuntu, and inside Ubuntu with VB,I have XP,and 2000 Pro.
But there is still the kernel update problem,so after an update,
you have to give permissions.
```
sudo chmod 666 /dev/vboxdrv
```   :)

---

### Post by diablo75 on 2008-06-22
Kernel update issues are something I am hoping to move away from or at least would like to make a little more simple.  So all you have to do after a kernel update with virtualbox is type:  

```
sudo chmod 666 /dev/vboxdrv
```

?

Or is there anything else that I would have to do?

---

### Post by Drakkor on 2008-06-22
That should be it, I've updated my kernel 3X from kernel 2.6.24-16 to kernel 2.6.24-19, and VirtualBox still works ! :)

---

### Post by diablo75 on 2008-06-22
The last time I tried Virtual Box, it was the OSE, and I used Add/Remove to install it.  But it failed to install the proper kernel header package along with it (which kind of made me mad).  Then I ran into a permissions problem shortly after installing the missing package.  Which made me more mad.  I just felt like, "This is Add/Remove... it's just suppose to work!  Dependencies aren't rocket science."

The feedback I got from most people was that they used other methods to install it, but did experience the same problem I did when using the method I tried.

What is the best (easiest, sure-fire) way to install Virtual Box?

---

### Post by Drakkor on 2008-06-22
@diablo
I had mouse capture problems with the Sun version 1.6.2, but as in a previous post it was solved by using the gutsy version of v. 1.5.4
and that can be found here: [http://blog.pixnet.net/copact/post/5289913](http://blog.pixnet.net/copact/post/5289913)
It's a .deb file,so all you gotta do is double-click to install,and it 
is accessed by going to Applications>System Tools>Innoteck VirtualBox :)
Edit: XP running in Ubuntu screenshot

---

### Post by sp0nge on 2008-06-22
I highly recommend VMWare Server. 

This has served me well in the past, allowing multiple machines to be virtualized on one physical machine. The most common uses I've made of it have been testing out other OSs and having one windows machine set up on my Ubuntu box for those times when I need a windows environment for whatever reason.

---

### Post by Virtua-Touch on 2008-06-22
VMware Workstation. But, neither VMware nor VBox is working correctly for me.

---

### Post by dpj23 on 2008-06-22
While everyone maybe working towards the same goal...  vmware products hands down are better than any other available... everyone has a preference but not all are equal...

---

### Post by etu on 2008-06-22
I have used both Vmware and Virtualbox but not for anything serious. What I have tried I have been surprised how well they actually work.

But now I am little worried of Virtualbox:confused:. The download page [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) says: "We [Sun] do request that anyone intending to redistribute the Open Source Edition contact us first." Doesn't that throw Virtualbox out of Ubuntu core (freedom to share):(?

One software that makes Linux to work in Windows Desktop is Ulteo (based on coLinux). Not full virtualization but runs (old) Ubuntu ok.

---

### Post by in0ni on 2008-06-22
i think this link was posted by someone else either in this or the opensuse forum: [http://virt.kernelnewbies.org/TechComparison](http://virt.kernelnewbies.org/TechComparison)


i am looking into vms myself -- first time -- and after the reading i have been doing its between xen, vbox and vmware esx. though i am only basing this on performance. not too sure how they compare with features. for example, i hear vbox has useful features like sharing of files between host and guest out of the box (i think samba could also be used), and keeping the mouse in the same location when switching back and fourth.

i am looking for something to run photoshop, illustrator, indesign working with very large files (adobe apps are a requirment for me).

xen supports it all, and seems to be competition to vmware esx, though i keep on hearing great things about vbox -- but according to this  comparison, vbox does not support smp guest...

also been looking into getting better performance by running vm off bootable partition, though cant find anything saying it actually helps.

---

### Post by Buffalo Soldier on 2008-06-23
KVM for me. Running a few Hardy VM for testing server/network related stuff such as bacula.

---

### Post by Joco on 2008-06-23
I'm running kvm in 8.04.  I have 6 VMs each running Ubuntu JEOS with specific facilities added for specific tasks. KVM is still pretty young but it is coming along nicely.

---

### Post by gtdaqua on 2008-06-23
We use VMWare Server in our production servers. Are VirtualBox/KVM mature enough to be used in enterprise server farms?

---

### Post by seetho on 2008-06-24
Surely in a survey like this you should include the other major players, e.g. Xen, kvm, qemu just to name a few.  It's like conducting a survey in a smoking room to find out how many people are smokers!

---

### Post by diablo75 on 2008-06-24
After installing Virtual Box again, I am very impressed.  I can see why there were many votes cast for it right off the bat.

And to those who were a little mad that I Didn't mention others (.... except for using the word "other" in the survey, because I don't know them by name to be honest)... sorry.

---

### Post by seetho on 2008-06-25
> **diablo75 said:**
> And to those who were a little mad that I Didn't mention others (.... except for using the word "other" in the survey, because I don't know them by name to be honest)... sorry.

I don't think anyone is "mad" about anything here :) - sorry if you misunderstood.  It'll be nice to see exactly how many people are using the different solutions and for what purpose.

I'm using VirtualBox for test purpose and to run WinXP (whenever I need to use it for some specific purpose - which irritates me!).  I can understand why everybody likes it as a first venture into virtualization.  It's rather easy to setup and has a nice UI.  What I don't like is that the OSE version is intentionally crippled by SUN, the networking kills the VMs sometimes, you need GUI to setup and the whole system stalls under heavy usage.

For serious use on my servers I much prefer KVM.  It just works much better than VB and you don't require a GUI to setup.

seetho

---

