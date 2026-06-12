---
title: "Ubuntu 10.04 linux-image-server and linux-image-generic (PAE)"
date: 2011-12-21
forum: Server Platforms
---

### Post by EgoGratis on 2011-12-21
I decided to install Ubuntu server (PC (Intel x86) server install CD) and all i get is **generic-pae** image. How would i install linux-image-server kernel **without PAE** support? 

I have to install Ubuntu on machine that supports PAE and then migrate HDD to machine that will use it and does not support PAE.

---

### Post by Paddy Landau on 2011-12-21
As I understand, when Ubuntu boots up with changed hardware (as would happen when you migrate your HDD), it automatically reconfigures itself.

You may want to do a test; install Ubuntu, check everything works (without spending much time on it), then migrate the HDD and see what happens.

---

### Post by EgoGratis on 2011-12-21
Kernel itself is "the problem". I don't think it can reconfigure it self to be non PAE and from generic to server?

---

### Post by Paddy Landau on 2011-12-21
Hmm, you may be right. But it's easy enough to test, as it doesn't take long at all to install Ubuntu.

Why can you not install Ubuntu directly on the target hardware rather than what you suggest?

---

### Post by EgoGratis on 2011-12-21
> Hmm, you may be right. But it's easy enough to test, as it doesn't take long at all to install Ubuntu.Yes i did that, but could not get pass Grub. I suspect PAE kernel is the problem because my processor does not support PAE.

> Why can you not install Ubuntu directly on the target hardware rather than what you suggest?It "hangs" at 74%. Maybe "hangs" is not appropriate term. Google suggest it's beacose machine is old and has small amount of memory (memory can't be upgraded). It would probably work if i would left the installer to finish, but installation took from 4 to 11 days on similar machines i found on Google when searching for "installer hangs at 74%". This is not something i am willing to do.

I could try Ubuntu Desktop 10.04 and i would get "non PAE" kernel BUT if i manage to somehow install Ubuntu server 10.04 on this machine i get few years more of support.

But i investigated and i found here:

[https://help.ubuntu.com/community/ServerFaq#Is_a_dedicated_SMP_kernel_available_from_the_Ubuntu_Server_installation_CD.3F](https://help.ubuntu.com/community/ServerFaq#Is_a_dedicated_SMP_kernel_available_from_the_Ubuntu_Server_installation_CD.3F)

For Ubuntu Server my hardware MUST support PAE? Well, i guess i will have to try Desktop Edition (command-line install) on this hardware to see if PAE kernel is the problem i am having right now.

---

### Post by Paddy Landau on 2011-12-22
Sorry. If your system is low on system resources, I wonder whether or not [Lubuntu]("https://wiki.ubuntu.com/Lubuntu") would be of help? Of the Ubuntu family, Lubuntu has the lowest requirements. Unfortunately, you would have to install Lubuntu and then try to install the server.

An alternative would be to look outside the Ubuntu family.

I'm sorry I cannot give you any better advice.

---

### Post by EgoGratis on 2011-12-22
> I'm sorry I cannot give you any better advice.

Thank you for your efforts i appreciate it.

> I wonder whether or not [Lubuntu]("https://wiki.ubuntu.com/Lubuntu") would be of help? Of the Ubuntu family, Lubuntu has the lowest requirements.

I think i doesn't matter much because X and desktop environment will not run on this machine. It has too little resources for that. It will be used only as server and i was planing to use Ubuntu Server that would give me few years more support and "server kernel". 

But because if i understand correctly Ubuntu Server 32 bit edition only has PAE kernel and i think this is why i can't go pass Grub i will try desktop edition and i will do command-line install. Ubuntu 10.04 Desktop Edition has non PAE kernel.

> An alternative would be to look outside the Ubuntu family.

I could but... :)

---

