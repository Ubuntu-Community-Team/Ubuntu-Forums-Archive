---
title: "How  to install and update your system offline."
date: 2006-08-02
forum: Repositories &amp; Backports
---

### Post by Ausus on 2006-08-02
Hi All,

I'm currently using the works Internet structure to down load What I require. Then I have to install these files.Then it becomes a problem.

Is their a way that to create a CD image of the Repositories.
That way I can Update my Linux box, offline via CD-image. This way it will be safer than using sudo.
I also want to instal k3b cd r/w software.I down loaded all relavant files to install.
The other problem I have is as follow:
1) "kdelibs-bin" also needs "kdelibs4c2a" to be installed
2) "kdelibs4c2a" also needs "kdelibs-bin" to be installed 
I call it denpendency.
When you are in terminal and use sudo to install these deb packages, you will generate errors because the one is dependant of the other. How can you bypas this error problem.In synoptic manager you will see incomplete packages. 
Most of the time it cant install of missing file structures.

I copied all *.deb files on a CD which I offloaded. This does not work.
It needs a Debian type off structure.

How is the question?.

---

### Post by Jussi Kukkonen on 2006-08-02
It's not easy -- even if you download all the dependencies (which you can see with *apt-cache depends k3b* by the way), those dependencies also have dependencies, which again have dependencies, etc. ... The reason apt/Synaptic system exists is to take care of this mess, and it needs a network connection to do it.

> Is their a way that to create a CD image of the Repositories. That way I can Update my Linux box, offline via CD-image. This way it will be safer than using sudo.
Have to admit that I do not understand what you mean here... There's no security advantage that I can see. 
Creating your own repository is possible, but not trivial. You should also realise that it will be really, really big -- I'd imagine it won't fit on a CD, or even a couple of CDs... See [http://www.debian.org/doc/manuals/repository-howto/repository-howto](http://www.debian.org/doc/manuals/repository-howto/repository-howto) if you really think this is what you want.

Something you could try instead: If you already have some working apt index files (or can get them) and then run *apt-get install k3b*, it should print out *"The following NEW packages will be installed"* -list which you could use to download the  correct packages when you're at work.

---

### Post by Ausus on 2006-08-02
Hi Jussi Kukkonen,

You see i'm new to Linux.
That is why i'm asking how thing can be done.
I can see the logic behind the Synaptic Install Manager.
But I thing their is a lot of people that dont have internet access. How can they be looked after.
Here by us in South-Africa the consumer get ripped-off. That is in all aspects, does not matter what you buy.
If I look at the rest of the world what internet cost, then I would have rather stayed their. That is beside the point.

I looked at certain program's that came with ubuntu, some of them are loaded only with the shell. Now when you want to run them, they need internet access.I cant recall teir name.

I would also like to update the Linux kernel, that will also pose problems. 
My machine is AMD64 +3800 X2 cpu. I dont know how well this kernel does support dual core.My kernel at present 2.6.15.23-amd-generic.I find a loot of desturbing message when running application. Need to shut down or cancel.At time when I try disconnect my USB device I get the same message, device not responding.

I like what I see with Ubuntu Linux, and what they have done.
I like it very much.

At a point I want to use my mobile to gain Internet access.
Then it depends at what speed you can connect an sustain a good speed specialy when you doen load.

Tnx for posting your reply message. I will try it tonight.

Regards](*,)

---

