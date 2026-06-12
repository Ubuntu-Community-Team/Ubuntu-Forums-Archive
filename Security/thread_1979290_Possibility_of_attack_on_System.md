---
title: "Possibility of attack on System"
date: 2012-05-13
forum: Security
---

### Post by bala150985 on 2012-05-13
Hi I have a host system which has two NIC card, eth0 and eth1.

eth0 is connected to Internet via a router and it does not have an IP assigned to it.  eth1 is connected to Intranet.


The host has a Virutal machine which is configured only to use eth0 in bridge mode to go out to internet via the router.

I use Virtual host to test malwares, with this being the case, Can my Host system which is running Linux ever get attacked over the Internet ?

What if I introduce more system between eth0 and Internet Router, Can I attack the Host system which is hosting the Guest VM ?

If my explanation is not clear kindly refer the diagram.

[IMG]http://img190.imageshack.us/img190/3628/systemwith2nic.png[/IMG]

---

### Post by westie457 on 2012-05-13
Not being an expert at this only repeating some things from various places on the Forum.

Provided you are not sharing folders/files between the machines the malware should be contained within the Guest OS. However there might be a possibility of 'drive by' attacks from risky web-sites.

I think it all comes down to any shared folders to provide a gateway from the Guest to your Host OS.

---

### Post by bala150985 on 2012-05-13
Thanks for the quick response westie457,

I do have a share folder between the guest and the Host that is the only way by which I transfer data between the two.

I believe that just giving a share folder in Read and Write mode to the Guest OS will just enable Guest OS to write to the Share folder correct ?  I could be wrong that is why I am seeking other people advice on the same to prevent any blind mistake on my part.

---

### Post by westie457 on 2012-05-13
Prepare yourself for a lot of reading on security starting with bodhi.zazen's sticky here.

[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

---

### Post by OpSecShellshock on 2012-05-13
I would advise, if possible, only testing malware on a dedicated system, distinct from one that is used for other tasks. Physical separation is always best. A machine that is running something you know to be malware should be physically separated from your internal network.

Having said that, if the malware is not designed for the OS or applications of the host system, there's not much risk. That's just in general, though, since it's hard to say specifically given all the different kinds of malware. The kind made for crime behaves much differently than the kind made for espionage. Some of them will try to break out of a virtual host, some won't even run if they are on a virtual host (to evade testing), and some will try to map the internal network and get a shell or process on another device. If you are deliberately compromising the guest system you can't really trust it to behave ;).

---

### Post by CharlesA on 2012-05-13
> **OpSecShellshock said:**
> I would advise, if possible, only testing malware on a dedicated system, distinct from one that is used for other tasks. Physical separation is always best. A machine that is running something you know to be malware should be physically separated from your internal network.

+1. This is really the best way to do it.

---

