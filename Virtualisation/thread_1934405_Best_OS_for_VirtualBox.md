---
title: "Best OS for VirtualBox?"
date: 2012-03-02
forum: Virtualisation
---

### Post by helpme222 on 2012-03-02
Hi, I need someone to point me in the direction of a distro that:

1) Runs smoothly in Virtualbox

2) Is updated regularly

3) Uses minimal resources

Thanks!

---

### Post by enjoijesus94 on 2012-03-02
Any OS Right?

It Just Depends On Your Flavors And What You Wanna Do.

My OS's
1.BlackBuntu
2.BackTrack5
3.Ubuntu
4.Linux Mint
5.Slackware
6.Puppy Linux

So It Just Depends On What You Want To Do On That OS.

---

### Post by helpme222 on 2012-03-02
> **enjoijesus94 said:**
> Any OS Right?

It Just Depends On Your Flavors And What You Wanna Do.

My OS's
1.BlackBuntu
2.BackTrack5
3.Ubuntu
4.Linux Mint
5.Slackware
6.Puppy Linux

So It Just Depends On What You Want To Do On That OS.
In my experience most linux distros run terribly in vb, they are jerky and run so slow I can't even use them.

Which of those run the smoothest? And I don't really like puppy because it runs as root.

---

### Post by QIII on 2012-03-02
Really, really light and Ubuntu based:

Bodhi Linux.

But it is very minimal and will take some work.

---

### Post by enjoijesus94 on 2012-03-02
puppy linux I like for gaming because its light weight and same for slackware linux.

Try some of the earlier series of ubuntu.

iv got 10.04 on a virtual machine with no problems.

but iv got 4gbs ram also.

have you tried earlier series of ubuntu?

---

### Post by helpme222 on 2012-03-02
I am going to try bodhi linux, i will tell you how it goes. :)

---

### Post by helpme222 on 2012-03-02
Bodhi linux works GREAT except for this:
[http://ubuntuforums.org/showthread.php?p=11732350#post11732350](http://ubuntuforums.org/showthread.php?p=11732350#post11732350)

---

### Post by nothingspecial on 2012-03-02
*Thread moved to **Virtualization**.*

---

### Post by mastablasta on 2012-03-02
It really depends on how much ram you have.
 
i have 2 GB and winXP on single core CPU. I dedicated 32 MB ram for GPU and 512MB ram for guest System. Xubuntu runs fine. I guess Lubuntu would also be a fast one and maybe less complicated that Bodhi. Bodhi runs on 10.04 LTS. and it really is fast.

---

### Post by enjoijesus94 on 2012-03-02
> **mastablasta said:**
> It really depends on how much ram you have.
 
i have 2 GB and winXP on single core CPU. I dedicated 32 MB ram for GPU and 512MB ram for guest System. Xubuntu runs fine. I guess Lubuntu would also be a fast one and maybe less complicated that Bodhi. Bodhi runs on 10.04 LTS. and it really is fast.

Yea Thats Why I Run Ubuntu 10.04 On A VirtualMachine 
since i have 4gbs.

---

### Post by winh8r on 2012-03-02
A very small (30MB) OS which I use regularly is Slitaz which you can find here: [http://www.slitaz.org/en/]("http://www.slitaz.org/en/")

it is a fast and fully functional OS available as a live cd .iso and is fully installable too.

Boots in seconds, and a full clean hdd install completes in about three minutes.

Very useful tool to have around as it does not seem to have any problems as regards graphics drivers etc.
It is also has a software repository and a package manager to allow you to expand it as required.


Or you could do a minimal Ubuntu install and just build what you need into it on the VM.

Hope this helps you.

---

### Post by haqking on 2012-03-02
bit confused by the OP question really.

There is no best for virtualisation, virtualisation is not something you are required to use or do and therefore no best OS to do it with, if it is required then it would be for the specific reason of running a particular OS as a VM and therefore no "best" comes into it.

You either need another Linux Distro, Windows versions, Unix etc running in a VM and if you do then that is the one that is best for you, how it runs is down to many factors.

Peace

---

### Post by QIII on 2012-03-02
The key is that the OP said "minimal resources".

For the OP --

I'm on my cell phone right now, so it's a bit hard to do much.  Some time within the last 48 hours I helped someone with the guest additions and full screen.  If I can, I'll post back with some instructions and a link to that post.

---

### Post by Paddy Landau on 2012-03-02
I have tried 12.04 in Virtual Box and it ran fine. This is 64-bit with 4Gb RAM on a modern computer.

If you are intending to do more than just play, however, I would go for [Lubuntu]("https://wiki.ubuntu.com/Lubuntu"), which requires far fewer resources (or, as already stated, [Bodhi]("http://bodhilinux.com/")).

If you install the Guest Additions, you can run it as if it were part of your host (I presume you are using Windows?) with the *seamless windows* function.

---

### Post by haqking on 2012-03-02
> **QIII said:**
> The key is that the OP said "minimal resources".

For the OP --

I'm on my cell phone right now, so it's a bit hard to do much.  Some time within the last 48 hours I helped someone with the guest additions and full screen.  If I can, I'll post back with some instructions and a link to that post.

I understand that.

In which case then DOS 6.22 

My point was what is the intended use of the VM.

I cant see unless i have missed something obvious the intention or purpose of running a VM in the first place ?

Perhaps i missed that part, i do get screen eye by this time of day ;-)

---

### Post by jerrrys on 2012-03-02
> **QIII said:**
> I'm on my cell phone right now, so it's a bit hard to do much.  Some time within the last 48 hours I helped someone with the guest additions and full screen.  If I can, I'll post back with some instructions and a link to that post.

Showoff :D

To the OP

I run vBox and find 10o4 to be the best/fastest setup.  This weekend I hope to try it in 12o4.  Running dual core and 3gig of ram.

Also run minimal builds of ubuntu and you can speed things up a little by doing this.  You can use things like fluxbox.  Install ubuntu-desktop without the recommended packages.

---

