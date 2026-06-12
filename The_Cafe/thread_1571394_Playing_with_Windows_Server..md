---
title: "Playing with Windows Server."
date: 2010-09-09
forum: The Cafe
---

### Post by uRock on 2010-09-09
Has anyone here tried using Windows Server 2008 for hosting virtual desktop installs?

In the near future I want to build a machine with the capability to Have Multiple VBoxes running, but I would like to throw Server 2008 on it, then install Windows 7 and Ubuntu along with a linux server and have them all running at the same time.

What would be the pros and cons of doing this?

Thanks,
uRock

---

### Post by Dr. C on 2010-09-10
> **uRock said:**
> Has anyone here tried using Windows Server 2008 for hosting virtual desktop installs?

In the near future I want to build a machine with the capability to Have Multiple VBoxes running, but I would like to throw Server 2008 on it, then install Windows 7 and Ubuntu along with a linux server and have them all running at the same time.

What would be the pros and cons of doing this?

Thanks,
uRock

Have done this using Ubuntu as the host, with multiple versions of Windows including Windows Server, GNU / Linux distributions, Hurd etc as guests using both Virtual Box and VMware Server. Have not tried this using Windows Server as the host but fundamentally it should not be that different.

---

### Post by v1ad on 2010-09-10
well, i don't see the point in it, but i would use ubuntu as the server to host the rest off. i ussually get better performance out of the virtual boxes then.

---

### Post by DemonBob on 2010-09-10
I use to do that with Windows Server 2003/2008 and VMWare. It convinced the company i was working for to buy the commercial version of VMWare.

---

### Post by aeiah on 2010-09-10
we're moving over to a windows 2008 host with virtual machines under HyperV. be aware that you have to make sure you select the legacy NIC when installing an ubuntu guest. it also doesn't seem to clone very well.

i cant see the point really. its very convenient from a monitoring and scripting point of view to have linux as the hypervisor, as you can easily manipulate virtual machines on the command line. its also free, of course, so you could use your windows licenses on the virtual machines.

i havent noticed any performance increase with our switch from fedora/KVM to win2008/HyperV. the only real difference is its now a pain in the *** to administer because i have to VPN > Remote desktop > click around the place instead of just ssh.

of course, there are more options than just HyperV for windows, but it still seems like an odd choice.

---

### Post by uRock on 2010-09-10
My reason for wanting a Windows host is for defragging. Running multiple hosts will slowly frag the HDD and from what I have read, there is no way to defrag EXT4, other than formatting and reinstalling.

I also want to put my copy of what businesses are paying big dollars for to use.

I don't see them dropping support for that version any time soon, which means I won't have to upgrade in the next few years.

Thanx for your thoughts,
uRock

---

