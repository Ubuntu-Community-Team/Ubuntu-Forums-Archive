---
title: "Desperately seeking alternative virtual machines"
date: 2008-02-13
forum: Virtualisation
---

### Post by esj on 2008-02-13
I'm looking for another virtual system that gives me a desktop like VMware workstation and a server facility like VMware server.  I have had it with VMware server. I needed to reboot the machines is morning and yet again the VMware console and the VMware Web interface both failed.  I swear, I bought VMware workstation so I wouldn't have to deal with a bag of parts and could just get on with my work.  Unfortunately, the server product is priced out of my range and I get to work with VMware server which, quite frankly stinks.  VMware server 2.0 looks much nicer but, I have no trust in VMware anymore.

To enumerate my complaints:

[LIST]
[*]VMware console rarely works
[*]VMware Web interface rarely works and I can't find the logs to diagnose
[*]every kernel upgrade is a frustrating experience because more often than not, you will lose ethernet and it's a struggle to get it back.
[*]VMware workstation virtual machines have inconsistent responses to the guest tools.  Even if all the virtual machines are using exactly the same OS base and updates.
[*]Cut and paste fails
[*]automatic resizing of graphics works if it's going to work but other machines it doesn't work for no apparent reason.
[/LIST]


In looking over these forum post, I see many people with the same complaints and it's frustrating.  Posting comments on the VMware forum yield few answers and technical support is theoretically available if you buy a support ticket but you can't buy a ticket on the website for VMware server, you can only buy them for workstation 6.0.

My belief is that the only reasonable course of action is to flee.  The only question is to where.  VMware has huge mind share which means the end solution needs to run VMware virtual machines or at least be able to produce VMware virtual machines as a delivery vehicle for customers.  Xen is interesting about the para-virtualization guest OS changes were even more frustrating than the VMware guest network interface hacks.  I had similar success with upgrading kernels under VMware :-(.  So what other options are there for workstation and server?

My case is a little special.  I need to run workstation on Windows because I need to run speech recognition and that's the only platform that really supports it.  That's changing thanks to wine but, it ain't here yet.

I'm looking forward to your reasoned and enlightening responses.

---eric

---

### Post by magicfab on 2008-02-13
Here is a comparative review of 4 virtualization options in Ubuntu:
[http://www.techthrob.com/tech/linux_virtualization.php](http://www.techthrob.com/tech/linux_virtualization.php)

I hope this helps, come back and let us know what you decide!

---

### Post by fjgaude on 2008-02-13
From what I know the vast majority of VMware product users do not have issues like what you describe.

I've been using the free vmware server for about a year without incident, through all the kernel upgrades, just by running vmware-config.pl which is in /usr/bin.

I guess the issue is you are running Windows as host, and vmware server as guest?

Most of us haven't seen the need to do that.

---

### Post by meanerelk on 2008-02-13
I used VMware for a while, too, but I had many frustrations with it as well. I've switched to VirtualBox, which I like a lot better. Everything seem to be working so far.

---

### Post by esj on 2008-02-16
> **magicfab said:**
> Here is a comparative review of 4 virtualization options in Ubuntu:
[http://www.techthrob.com/tech/linux_virtualization.php](http://www.techthrob.com/tech/linux_virtualization.php)

I hope this helps, come back and let us know what you decide!

because of my requirements (lights off server operation) I'm going to have to stick with VM Ware for the time being.  all of the other virtualization tools are really oriented towards desktop virtualization.

because of the problems I've had with losing ethernet devices on every kernel upgrade,  I've written a small script to automatically rebuild the VM Ware configuration on reboot if the VM Ware ethernet module doesn't exist in the currently running system.  It's a bit risky but, it least I can always get a working ethernet device.

it was nice to see how canonical is storing deb' for the host side of virtualization.  I just wish they had the equivalent for guests.  Oh well, I guess it's back to playing with a bag of parts.  And people wonder why I stick with 6.06 for my servers.  :-)

---

### Post by fjgaude on 2008-02-16
Say, what does the new upgrade 6.06.2 do for you? And are you thinking of going with 8.04 when it is released in April?

---

### Post by popch on 2008-02-16
> **esj said:**
>  I'm going to have to stick with VM Ware for the time being.  all of the other virtualization tools are really oriented towards desktop virtualization.

If this statement is based on the article to linked in an earlier post: have a closer look at VirtualBox's web site. I distinctly remember reading about server side support. It's quite possible that I saw that in the User's Guide.

---

### Post by esj on 2008-02-16
> **fjgaude said:**
> From what I know the vast majority of VMware product users do not have issues like what you describe.

I've been using the free vmware server for about a year without incident, through all the kernel upgrades, just by running vmware-config.pl which is in /usr/bin.

I guess the issue is you are running Windows as host, and vmware server as guest?

Most of us haven't seen the need to do that.

maybe I'm just lucky but I've gotten into a situation where some of my virtual machines do not upgrade kernels and headers at the same time (highly annoying).  unless I'm very much mistaken, you also can't update the tools until you have rebooted and are running the new kernel.and given that VMware console doesn't work (keeps giving me error about mks missing), I need to use VM Ware to get in and install the tools and then reboot again.  Fortunately, this little script stuck in rc.local has saved me more times than I want to know

```

kern=`uname -r`
if [ ! -f "/lib/modules/${kern}/misc/vmxnet.o" ] ; then
    # make sure headers are available
    if [ -d /usr/src/linux-headers-${kern} ] ; then
        cd /home/esj/vmware-tools-distrib
        ./vmware-install.pl -d
        depmod -a
    fi
fi

```

it runs at boot time if the network modules missing and by the time it finishes, I can use my ethernet interface without any problem.  Yes it's kind of risky but, if it saves me pain more than it causes, I am not really caring a whole lot.

As for other users complaining are not, there's two reasons for that.  First is that they are complaining.  This vanishing ethernet problem is a very common source of complaint on the VM Ware forums and the other reason you don't see many complaint is because most virtual machine users do not upgrade their kernels under any circumstances whatsoever.  Once they get a working configuration, nothing changes which is unacceptable from both a security and features standpoint.

one other major complaint I have with VM Ware (and probably with the other virtualization tools) is that they don't keep up with the release cycle of distributions.  I've been there.  I know that a relatively simple change takes a least a month of developer and QA time.  Which says to me, either relinquish control of that component and let the enthusiastic take over its maintenance or get with the program and release your guest tools no more than a month after distribution release.

Yeah, I'm cranky this morning.  :-)

---

### Post by esj on 2008-02-16
> **fjgaude said:**
> Say, what does the new upgrade 6.06.2 do for you? And are you thinking of going with 8.04 when it is released in April?

workstation upgrade doesn't buy me a whole lot.  I'm looking forward to the server 2.0 getting out of beta in about six months because from what I've seen it's really nice.  As for 8.04, I tend to lag releases by about three to six months.  I have a friend to installs the hottest CD of the latest rawest code on her machine and then laughs at herself and it when it fails.  me, I have way too many things to do and so if it works and is stable, I leave it alone.  I do fundamental upgrades for security reasons but that's about it.  Only when I can't do what I want to do do I look seriously at upgrading (hence my trying to go with gutsy for my mail server/mailing list upgrade) I wouldn't mind upgrading my wiki machine either. moinmoin is getting a little long in the tooth.

I will say one nice thing about updating virtual machines to a more current release is that you can just make a copy of the original machine, upgrade and if something screws up, you just put the copy back.  Try that with a hard drive.  ;-)

---

### Post by esj on 2008-02-16
> **popch said:**
> If this statement is based on the article to linked in an earlier post: have a closer look at VirtualBox's web site. I distinctly remember reading about server side support. It's quite possible that I saw that in the User's Guide.

just checked again in both manual and IRC.  It looks like VM Ware and Xen are the only two systems that support servers and given that I'm using salvaged Pentium fours without virtualization support, I'm pretty much stuck with VM Ware unless Ubuntu comes with para virtualized kernels.

---

