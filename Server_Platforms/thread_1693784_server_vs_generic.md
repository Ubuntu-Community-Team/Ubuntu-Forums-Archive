---
title: "server vs generic?"
date: 2011-02-23
forum: Server Platforms
---

### Post by pershaped on 2011-02-23
Hi,

I have just realized that the two dedicated servers my webhost have provided for the website I'm managing is running with generic- instead of server-images (64-bit). Does anyone know how much difference this could make?

TIA

---

### Post by arrrghhh on 2011-02-23
Very little AFAIK.

I think there are some server-related optimizations in the 64-bit edition (which is why 64-bit is recommended for server installations).

If you're concerned about RAM not being accessible, so long as you're running a PAE kernel you should be able to use up to 64gb IIRC.  I wouldn't worry about it too much (there's nothing "wrong" with it), unless you feel like rebuilding the server 64-bit ;).

---

### Post by dtfinch on 2011-02-23
On 32 bit the server kernel is generic-pae.

---

### Post by pershaped on 2011-02-24
Sorry, maybe I wasn't clear enough but the servers are already 64-bit and the local servers I use for development which are installed with the dl'ed iso from ubuntu.com uses the server-image but the live-servers installed by the webhost-company uses the generic-images. (Running 9.10 btw)

From what I've read about the differences the server-version uses a different scheduler ([link]("https://help.ubuntu.com/10.10/serverguide/C/preparing-to-install.html#intro-kernel-diffs")) which_ _if I understand it correctly will affect performance. But before I ask the hosting-company to go for the server-image I still want to confirm that there actually makes a difference. Anyone who has a clue?__[U]
[/U]

---

### Post by tgalati4 on 2011-02-24
I thought that the suspend/sleep stuff was pulled out of the server image and some other process trimming.  There are quite a few less processes running in the server than the desktop version (besides xorg and and the desktop environment).  The desktop adds about a 10% performance penalty and the desktop scheduling is designed for a responsive mouse and keyboard, not to crunch server workloads.

---

### Post by pershaped on 2011-02-24
tgalati4: Do you have any example of processes that should not be found on the server-version that I could have a look for? and is there a way to determine what type of scheduling that is currently in use on a system?

10% performance penalty sounds like enough for me to demand the change of image. Does anyone know of any problems with changing the image-version or should it be 'a walk in the park'?

---

### Post by James78 on 2011-02-25
> **pershaped said:**
> tgalati4: Do you have any example of processes that should not be found on the server-version that I could have a look for? and is there a way to determine what type of scheduling that is currently in use on a system?
Gnome, KDE, xfce, ...
> **pershaped said:**
> 10% performance penalty sounds like enough for me to demand the change  of image. Does anyone know of any problems with changing the  image-version or should it be 'a walk in the park'?
Walk in the park. The only thing you need to do is install and use the Desktop kernel in your server, which is easy since they use the exact same repositories.

---

### Post by pershaped on 2011-02-25
James78: Not sure if you have really understood my question.. I am running a server which has the generic (desktop) image and am trying to sort out if that is a problem.

My server does not have any of the processes you listed (Gnome, KDE, xfce..)

---

### Post by James78 on 2011-02-25
No, it shouldn't be a problem. Your servers are already 64-bit, so you aren't loosing anything by removing a PAE kernel (unneeded in 64-bit).

Gnome, KDE, and Xfce are not processes, but desktop environments. If you do not have them installed, then you don't have them running. Default Desktop Ubuntu comes with Gnome.

Gnome
[http://www.gnome.org/](http://www.gnome.org/)
KDE
[http://www.kde.org/](http://www.kde.org/)
Xfce
[http://www.xfce.org/](http://www.xfce.org/)

---

### Post by pershaped on 2011-02-25
Thanks James78, I have understood that images has less importance when running 64-bit but what I'm still a bit concerned about is the scheduler difference between the server and generic-images.

From what I've read ([link]("https://help.ubuntu.com/10.10/serverguide/C/preparing-to-install.html#intro-kernel-diffs") see Server and Desktop differences), and as tgalatia4 pointed out earlier in this thread, the scheduler used in the Desktop edition (CFQ) "is designed for a responsive mouse and keyboard, not to crunch server workloads". Not really sure if this is the correct way to go but when I have a look at /sys/block/sda/queue/scheduler I get (not sure if sda is where to look for this though):

noop anticipatory deadline [cfq]

I guess the brackets mean that my server uses the CFQ scheduler which is, from what I've read, not the best option for a server. Can anyone confirm this or enlighten me further please?

Then there's also the preemption-bit.. how can I figure out if preemption is enabled or not?

---

### Post by pershaped on 2011-02-25
I think I have answered my own question already but posting my findings for others who are interested:

To find if preemption is enabled I opened up the file /boot/config-2.6.31-22-generic and searched for PREEMPT. The lines of interest was:

# CONFIG_PREEMPT_RCU is not set
# CONFIG_PREEMPT_RCU_TRACE is not set
CONFIG_PREEMPT_NOTIFIERS=y
# CONFIG_PREEMPT_NONE is not set
CONFIG_PREEMPT_VOLUNTARY=y
# CONFIG_PREEMPT is not set

The uncommented lines are presumably the ones that are in use and PREEMPT_VOLUNTARY=y states that preemption is used.

On [this link]("http://lxr.linux.no/#linux+v2.6.37.2/kernel/Kconfig.preempt") the help-section for PREEMPT_VOLUNTARY clearly states that this should be used for desktop systems.

So I guess I have come to the conclusion that using the generic-image on the two live servers I manage is NOT the best way to go. Better would be to use the server-image which not only uses a scheduler (*Deadline* I/O) more optimized for servers but also disables preemption.

I'm still not too sure how much this will help the performance of my servers so I'm still interested in hearing from others who have more knowledge or experience with this.

---

### Post by SeijiSensei on 2011-02-25
I bet any supposed performance differences will be indistinguishable to the naked eye.  Perhaps if you're running a DB server with hundreds of simultaneous clients, or handling thousands of HTTP requests each second, but for ordinary web/mail serving?  I doubt it would make any difference at all.

Performance differences on paper often mean little in real applications.  From the perspective of someone visiting your web host, things like network bandwidth are going to matter far beyond which kernel you're using.

---

### Post by pershaped on 2011-02-25
Thanks for your input SeijiSensei, the fact is that the servers I'm managing are one webserver and one dbserver with quite heavy load from time to time. This is why I have started to investigate how I can improve performance and when I realized that the kernel-image was a generic and not server-image I just had to dig into this to see what difference it could make.

If I go ahead with the change I will post my findings in this thread.

---

