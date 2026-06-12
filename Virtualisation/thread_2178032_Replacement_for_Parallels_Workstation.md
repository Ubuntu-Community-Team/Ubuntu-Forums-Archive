---
title: "Replacement for Parallels Workstation?"
date: 2013-10-01
forum: Virtualisation
---

### Post by Robertjm on 2013-10-01
Hi all,

OK, so call me late to the party. But, I just found out that Parallels has abandoned us Linux users when they dropped the Parallels Workstation product last March. I guess after I had all sorts of problems with it last October I hadn't tried using it since.

In any event, did any PW6 users find a migration path to another virtual machine product? If so, which did you choose, and how easy was the migration? I've got a handful of Windows-based programs that I still can't walk away from and so need some type of virtualization, ideally which can import my PW6 virtual environments without destroying the data. 

I should have known something was fishy when they dropped the price on PW6 to $9.99 last year!!

Thanks all.

Robert

---

### Post by TheFu on 2013-10-01
Which hostOS and which guestOSes?
Whenever I've needed to migrate between different VM technologies that didn't directly support each other, a backup and restore was the best method possible.

---

### Post by Robertjm on 2013-10-01
Sorry. I guess through my anger at Parallels I wasn't clear.

Host OS is Ubuntu 12.04 LTS trying to run Parallels Workstation 6 for Linux.

Guest OS's are Windows 8 and Windows XP Pro.

Do you mean a backup and restore WITHIN the Guest OS? If so, that's the rub as I cannot get into a stable Guest OS to do much of anything. The screen is not stable and bounces all over the place.

Robert

> **TheFu said:**
> Which hostOS and which guestOSes?
Whenever I've needed to migrate between different VM technologies that didn't directly support each other, a backup and restore was the best method possible.

---

### Post by 1clue on 2013-10-01
I recently tried to migrate a Windows image from Parallels Mac to kvm.  It didn't work very well.

I was going to try to migrate first to VMware, then go to Parallels but lost interest before I got around to it.

I know VMware Converter can do migrations from just about anything, but I think VMware Converter has to run inside the VM.  Maybe not, you might want to look into it.

Interestingly enough, I COULD migrate a Linux install from Parallels Mac to kvm.

FWIW if you want a commercial product you might consider VMware.  They've had fairly decent support for Linux all along, although they also obsolete products every so often too.  They at least provide another application to replace the one they obsoleted.

If you just want a free virtualization machine that will always be on Linux, then KVM can't be beat.  You can install it on a command line system, but I use Xubuntu and virt-manager, which is a gui app very much like the Parallels control panel.  KVM lets you have the machines boot on host boot, unlike most of the other products.

---

### Post by TheFu on 2013-10-02
> **Robertjm said:**
> Sorry. I guess through my anger at Parallels I wasn't clear.

Host OS is Ubuntu 12.04 LTS trying to run Parallels Workstation 6 for Linux.

Guest OS's are Windows 8 and Windows XP Pro.

Do you mean a backup and restore WITHIN the Guest OS? If so, that's the rub as I cannot get into a stable Guest OS to do much of anything. The screen is not stable and bounces all over the place.

Robert

Yes. Inside. If the GUI is the issue, turn it down, use a simpler GUI like LXDE. Avoid Unity, which is good advice for anyone using virtual machines.

However, Windows installs are tied to the hardware and usually do not transfer over well without extreme measures to make the old *real* hardware used migrate into the new "virtual" hardware. Reinstalling is usually easier, IME.  There is also the Windows license issue - I figure you've solved that already and yous is NOT tied to the hardware.  If your current VM hardware is the same as the new VM hardware, you should have an easier time with the backup-move-restore.

Sadly, for desktop-on-desktop virtualization, we don't have many good choices.  Oracle VirtualBox - well - it has "oracle" and that should say enough.  VMware Player/Workstation are good products, but VMware *corporate* has screwed over their customers/users previously.  My company will never use anything from them again after the last debacle where they screwed around with licensing and almost doubled the costs.

As mentioned, there is also KVM - it is best for server-on-server installations. The GUI performance is adequate for office-productivity apps, but not much more.  In theory, Spice can be used to make it perform well enough for audio and video, but I'm never gotten it working that well.  Maybe it is better now.  To make spice work with a Windows client requires installing specific drivers, running a specific KVM and having a spice-client program.

---

### Post by 1clue on 2013-10-02
Regarding TheFu's last post, VMware is obviously in it for a profit.  They continually offer free products, but the product either goes "commercial" or is discontinued and you have to migrate everything over to some other free product they have just released.  As well, they have a limited number of VMs you can put on the free products, at least to have them run continuously.  Google on "VMware tax" and you'll see all sorts of complaints about the hidden costs of VMware.  It's almost as bad as an airline.

That said, I've been using virt-manager with kvm and haven't had any trouble with GUI apps.  Although I guess I don't use it for more than productivity apps, if you're using something for gaming or whatever then I don't know of any virtualization engine -- even VMware -- that works worth a darn.

FWIW though, I wouldn't use the console on the VM anyway for everyday use.  SSH over there and use Xnest.  Gives you a whole desktop the Linux way.  Or for Windows just RDP over there.  Linux has a great remote desktop app.

---

### Post by Habitual on 2013-10-02
> **TheFu said:**
> Yes. Inside. If the GUI is the issue, turn it down, use a simpler GUI like LXDE. Avoid Unity, which is good advice for anyone using virtual machines.

However, Windows installs are tied to the hardware and usually do not transfer over well without extreme measures to make the old *real* hardware used migrate into the new "virtual" hardware. Reinstalling is usually easier, IME.  There is also the Windows license issue - I figure you've solved that already and yous is NOT tied to the hardware.  If your current VM hardware is the same as the new VM hardware, you should have an easier time with the backup-move-restore.

Sadly, for desktop-on-desktop virtualization, we don't have many good choices.  Oracle VirtualBox - well - it has "oracle" and that should say enough.  VMware Player/Workstation are good products, but VMware *corporate* has screwed over their customers/users previously.  My company will never use anything from them again after the last debacle where they screwed around with licensing and almost doubled the costs.

As mentioned, there is also KVM - it is best for server-on-server installations. The GUI performance is adequate for office-productivity apps, but not much more.  In theory, Spice can be used to make it perform well enough for audio and video, but I'm never gotten it working that well.  Maybe it is better now.  To make spice work with a Windows client requires installing specific drivers, running a specific KVM and having a spice-client program.

to the OP, excuse my interruption...

TheFu:
[http://blog.jdpfu.com/page/38](http://blog.jdpfu.com/page/38) has "issues" :)
I just spent like 2 hours reading there, (Great Site, btw)
Thanks for the sysusage article. installed and collecting.

Back to the topic.

---

### Post by TheFu on 2013-10-02
> **Habitual said:**
> to the OP, excuse my interruption...

TheFu:
[http://blog.jdpfu.com/page/38](http://blog.jdpfu.com/page/38) has "issues" :)
I just spent like 2 hours reading there, (Great Site, btw)
Thanks for the sysusage article. installed and collecting.

Back to the topic.

Thanks.  Sometimes I rant, but I try to provide the "why" more than the "how-to" - lots of websites provide how-to guides, so I don't need to as well.  The "why" is harder.  Also, /page/38 isn't a very useful link to my blog - it is dependent on your query.  If there isn't an article title in the URL, it will probably change every week.

**I most definitely have issues.**  That is putting it kindly. ;)
If I were deploying sysusage again, I'd setup a central collector. That is very different from the instructions on my blog.

I've been using and deploying virtualization since the late 1990s. Have used most of the tools out there - except Apple-specific things.  These days, I've switched almost 100% to KVM for many reasons. Been burned a few times with other solutions.   KVM is and always will be F/LOSS.  There are some really big companies supporting it. Since 10.04, it is been very stable. Additional features have been added since - some for enterprise use and others for desktop use. I'm more interested in the enterprise use cases like live migrations.

VirtualBox has a place too - usually for desktop-on-desktop virtualization. I've used VBox twice on Ubuntu. Once it went badly - locking up the host completely AND all VMs.  That was enough to make me remove it. It was a long time ago, perhaps 2009?  
With Windows as the hostOS, it was very stable with 4+ weeks of uptime the last time I used it ... about 6 months ago for some testing. I stopped using it daily a few yrs ago, but I used vbox all day, everyday for a few years happily.

Also deployed VBox on Linux for my Mom's system - that was a 12.04 box and it worked extremely well. That should say something - there are trade-offs and vbox is the best solution for certain users.

Ok, back to fighting my internal daemons now. ;)

---

### Post by Habitual on 2013-10-02
> **TheFu said:**
> Thanks.  Sometimes I rant, but I try to provide the "why" more than the "how-to" - lots of websites provide how-to guides, so I don't need to as well.  The "why" is harder.  Also, /page/38 isn't a very useful link to my blog - it is dependent on your query.  If there isn't an article title in the URL, it will probably change every week.

**I most definitely have issues.** 
You and me both.

Peace.

---

