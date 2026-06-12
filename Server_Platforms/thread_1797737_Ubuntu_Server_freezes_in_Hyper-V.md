---
title: "Ubuntu Server freezes in Hyper-V"
date: 2011-07-05
forum: Server Platforms
---

### Post by yakatz on 2011-07-05
I am running Ubuntu Server 10.04 LTS in Hyper-V (Windows Server 2008 x64). I followed most of [this guide]("http://blogs.msdn.com/b/virtual_pc_guy/archive/2010/10/21/installing-ubuntu-server-10-10-on-hyper-v.aspx") to get it set up.
It ran fine for a while, but recently, every few days, it locks up. I notice that it has locked up when I do not get a logwatch report in the morning. When I look at the console, I see this meesage repeated several times:
> [TIMESTAMP] INFO: task <<TASK NAME>> blocked for more than 120 seconds.
[TIMESTAMP] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message."
TIMESTAMP is similar to 394322.924349 and several of the listed processes include [LIST]
[*]miniserv.pl:943
[*]oickup:5490
[*]jbd2/hda1-8:217
[*]flush-3:0:236
[*]master:809
[/LIST] with several of them repeating.
When I try to log in with SSH, PuTTY says "Connection timed out."
when I try to log in on the console, it shows my last login details and then hangs without showing a prompt.

---

### Post by rubylaser on 2011-07-05
I've had mixed results with Ubuntu in Hyper-V, here's another current [thread]("http://ubuntuforums.org/showthread.php?t=1796881") about it.  I've had much better luck with ESXi or Proxmox for virtualization than Hyper-V.

---

### Post by arrrghhh on 2011-07-05
> **rubylaser said:**
> I've had mixed results with Ubuntu in Hyper-V, here's another current [thread]("http://ubuntuforums.org/showthread.php?t=1796881") about it.  I've had much better luck with ESXi or Proxmox for virtualization than Hyper-V.

I've used ESXi with Ubuntu, and I can also confirm it works great.

If you don't mind the guest/host paradigm, VirtualBox is fantastic.

---

### Post by yakatz on 2011-07-05
Thanks but no thanks for all the "Don't use Hyper-V" comments.

Until recently, one client was an all-Windows shop.
I have been trying to convince them to look at Ubuntu (and Linux in general) to lower costs.
I am running a Ubuntu server test system on the only hardware they have available, so I can't really change the virtualization product they are using.

Anyone know how I might be able to find the root cause of this problem?
Considering that the Hyper-V drivers were merged into the vanilla kernel from 2.6.32 (although I heard talk that they might be removed, they are still there now), if there is a problem with them, it should be reported...

---

### Post by arrrghhh on 2011-07-05
> **yakatz said:**
> Thanks but no thanks for all the "Don't use Hyper-V" comments.

Until recently, one client was an all-Windows shop.
I have been trying to convince them to look at Ubuntu (and Linux in general) to lower costs.
I am running a Ubuntu server test system on the only hardware they have available, so I can't really change the virtualization product they are using.

Anyone know how I might be able to find the root cause of this problem?
Considering that the Hyper-V drivers were merged into the vanilla kernel from 2.6.32 (although I heard talk that they might be removed, they are still there now), if there is a problem with them, it should be reported...

It's Hyper-V's fault Linux isn't supported well under it... honestly if it's an issue, it seems like you should be posting in Hyper-V forums.

Good luck, but from what I've heard from **many** professionals in the field is you do not use Hyper-V for a virtualization platform for Linux... and several have said at all, but this is in comparison to vSphere...

---

### Post by rubylaser on 2011-07-06
Good luck... As, I said we tried it on a number of production machines, and could never get it working consistently for large uptimes, or through package upgrades.  It's not surprising that Hyper-V virtualizes Windows well, but it struggles to work as well with Linux.

You're not going to have much luck troubleshooting this from the Ubuntu side, as the problem is stemming from the hypervisor.  I'd ask around some Hyper-V forums as suggested.  

Also, if they're happy with Windows, and know how to administrate it, and are used to paying for licenses with Windows, I wouldn't try to rock the boat.  Anytime they have a problem in the future, they'll point at that crazy Linux box, that's "never worked right since it was setup" as the root of all their problems.

---

