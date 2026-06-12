---
title: "Problem with xen under Hardy on Thinkpad X30"
date: 2008-05-15
forum: Virtualisation
---

### Post by candlerb on 2008-05-15
Hello,

I have Hardy running on my Thinkpad X30 (which was upgraded from Dapper using update-manager -d)

I am trying to get it to work with Xen.

The problem is that it works only if gdm is disabled in /etc/rc2.d. If gdm is enabled (or if I start gdm from the command line) the screen goes blank, and the machine appears to freeze. Pressing Ctrl-Alt-Fn doesn't switch to a text screen. Pressing Ctrl-Alt-Del causes the caps-lock and scroll-lock LEDs to flash at about 0.5Hz. I have to hard power down.

So I'm left with a laptop without graphics, which isn't very useful :(

Another point of reference. Since the ubuntu-xen-desktop metapackage is apparently broken (*), I had to install the components by hand, as follows:

[I]apt-get install bridge-utils libc6-xen libxen3 python-xen-3.2 xen-docs-3.2 xen-hypervisor-3.2 xen-tools xen-utils-3.2

apt-get install linux-image-xen[/I]

(*) ubuntu-xen-desktop depends on linux-xen, and linux-xen in turn depends on linux-restricted-modules-xen, and that is missing. ubuntu-xen-desktop also depends on xenman, which is also missing.

If I disable xend and xendomains from /etc/rc2.d/ then it doesn't make any difference to the problem starting X. This laptop has an Intel 82830 chipset graphics controller, which is pretty bog standard AFAIK.

A few other things I tried: renaming /lib/tls to /lib/tls.disabled (as suggested by a Xen warning message at startup), and disabling apparmor in rcS.d (as suggested by a howtoforge posting about Xen with Hardy, which made it sound like it was going to be very straightforward)

I also tried nohz=off (no difference).

Unfortunately I can't use KVM, ubuntu's preferred virtualisation mechanism, because my CPU doesn't have VT extensions.

Any other Xen users out there who can give me a clue?

Thanks,

Brian.+

---

### Post by james.wilde on 2008-05-21
Probably a stupid question, Brian...

If you create this xen machine, admittedly without graphics, can you subsequently create any virtual machines?  Can these be, for example, Ubuntu 8.04 and/or Windows, and if so, can you run them with graphics?

I sympathise with your problem, as I, too, would like to test xen and have found the catch 22 problems you mention.  I cannot run KVM either for the same reason as you.  But that's not the point.  I suspect that the linux challenger to vmware and Solaris zones is going to be xen rather than anything else.  I could be wrong, but it is always xen one hears about.

//James

---

### Post by bradmkjr on 2008-05-21
James.Wilde,

You can run a gui virtual machine on a guifree virtual server ie: xen or VMware server. But you need to have a gui machine to load the remote client software. If you have 2 computers, 1 could be a virtual server and then you can connect to the virtual machines from the second computer using VNC, Remote Desktop or Client Software (VMware). If you don't have a local gui you can't load the virtual machine gui locally.

It isn't a stupid question, just one of the most confusing aspects of starting with virtualization.

I recommend starting with Virtual Box or VMware player, inside of GDM as it doesn't require a special kernel. These packages don't require the VT technology in the CPU so you shouldn't have any issue running them.

Good Luck,
Bradford Knowlton
[http://x86Virtualization](http://x86Virtualization)

---

### Post by candlerb on 2008-05-21
> **james.wilde said:**
> Probably a stupid question, Brian...

If you create this xen machine, admittedly without graphics, can you subsequently create any virtual machines?

Well, "xm list" seemed happy enough, but I didn't try installing any VMs.

However I can't test this any further right now. As it happens, my hard drive died yesterday. So... I put in a new drive, and decided to try installing CentOS 5.1 instead of Ubuntu.

The Xen install for this worked straight out of the box. My machine boots into graphics mode, but has full Xen functionality too. Red Hat seem to have done an excellent job of packaging Xen so it "just works" [TM]. This is an older Xen version though (3.0.3)

Admittedly, to make a fair comparison with Ubuntu I'd have to reinstall 8.04 from scratch, because my laptop was originally 6.06 but updated over the net. But I'm not particularly inclined to try that while the Xen metapackages remain broken, i.e. ubuntu-xen-server and ubuntu-xen-desktop.

Incidentally, I _have_ used vmware, and I gave virtualbox a quick try too. What I really like about Xen is the real-time memory reallocation: you can add or subtract memory from a VM and it shows up in the guest OS's "free" output immediately, with the remainder available to dom0. And the paravirtualisation means that it should be much more efficient on my not-particularly-modern processor (1.2GHz P3).

BTW I've not abandoned Ubuntu completely - my desktop still runs 6.06. I'll wait until a bit later to upgrade that to 8.04 though.

Regards,

Brian.

---

### Post by mad bungo on 2008-07-21
I think you have run into this bug.
Using the vesa drivers should fix the problem.

[https://bugs.launchpad.net/xorg-server/+bug/68440](https://bugs.launchpad.net/xorg-server/+bug/68440)

---

