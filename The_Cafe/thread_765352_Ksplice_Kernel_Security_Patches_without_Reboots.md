---
title: "Ksplice: Kernel Security Patches without Reboots"
date: 2008-04-24
forum: The Cafe
---

### Post by toupeiro on 2008-04-24
If anyone reading this thread has any influence as to what may get picked up in future releases of Ubuntu, PLEASE consider this for 8.10.  This is a huge win for Linux, which already is known for not requiring many reboots at all.

[http://web.mit.edu/ksplice/doc/ksplice.pdf](http://web.mit.edu/ksplice/doc/ksplice.pdf)

---

### Post by phrostbyte on 2008-04-24
Put this up on [http://brainstorm.ubuntu.com](http://brainstorm.ubuntu.com) 

I will vote for it.

---

### Post by klange on 2008-04-24
I'd like to see this in Hardy+1. Finally, one step closer to truly never having to restart. (My mother found this while perusing the MIT admissions site before I even read it, lol )

---

### Post by phrostbyte on 2008-04-24
I will put it up on brainstorm.

---

### Post by phrostbyte on 2008-04-24
[[IMG]http://brainstorm.ubuntu.com/idea/7544/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/7544/)

---

### Post by Andrewie on 2008-04-24
Is this going into the Main kernel?

---

### Post by klange on 2008-04-24
> **Andrewie said:**
> Is this going into the Main kernel?

Ksplice requires no kernel changes, it's really just a complex binary patching system designed specifically for use on the Linux kernel. (It is itself a kernel module, though)

---

### Post by toupeiro on 2008-04-24
Thanks for posting this, phrostbyte!  This would be a very powerful addition to ubuntu desktop and server!

---

### Post by Andrewie on 2008-04-24
> **WindowsSucks said:**
> Ksplice requires no kernel changes, it's really just a complex binary patching system designed specifically for use on the Linux kernel. (It is itself a kernel module, though)

thanks for clearing that up

---

### Post by Patsoe on 2009-06-28
Sorry for reviving a very old thread, but this is relevant enough I'd say... [http://linux.slashdot.org/story/09/06/27/2238255/Ksplice-Offers-Rebootless-Updates-For-Ubuntu-Systems](http://linux.slashdot.org/story/09/06/27/2238255/Ksplice-Offers-Rebootless-Updates-For-Ubuntu-Systems) 

"Ksplice has started offering Ksplice Uptrack for Ubuntu Jaunty, a free service that delivers rebootless versions of all the latest Ubuntu kernel security updates. It's currently available for both the 32 and 64-bit generic kernel [...]"

---

### Post by gnomeuser on 2009-06-28
Wow what a remarkably good idea for implementing universal security holes..

---

### Post by Patsoe on 2009-06-28
> **gnomeuser said:**
> Wow what a remarkably good idea for implementing universal security holes..

...because someone with sufficient privileges to live-patch a kernel wouldn't be able to wreak havoc in a million different ways already, anyway? ;)

---

### Post by gnomeuser on 2009-06-28
> **Patsoe said:**
> ...because someone with sufficient privileges to live-patch a kernel wouldn't be able to wreak havoc in a million different ways already, anyway? ;)

Sure but isn't that like saying installing rusty nails in your underwear isn't a problem since anyone with access there could easily hit your nads with an icepick anyways.

It's tempting to do this for the nice ring rebootless updates has but in reality it taints the kernel for a good reason, not only is it an unrequired security hole it is also bound to lead to instability and I can't see upstream merging this into the kernel anytime soon so it's also additional work your vendor have to merge with every update. Finally it does not work for all update, if you change anything non trivial (such as updating a struct), you cannot use ksplice and you still need to reboot.

I would be all in favor of a solution that would work regardless of the update, but that kind of work is much harder and more invasive.

---

### Post by Patsoe on 2009-06-28
> **gnomeuser said:**
> Sure but isn't that like saying installing rusty nails in your underwear isn't a problem since anyone with access there could easily hit your nads with an icepick anyways.

The comparison would remotely make sense if you had a purpose for those rusty nails there... and even then, no. If I was American I'd start inserting links to informal fallacies here ;)

> It's tempting to do this for the nice ring rebootless updates has but in reality it taints the kernel for a good reason, not only is it an unrequired security hole it is also bound to lead to instability [...]

It's not a security hole, it could potentially have security holes... that's different.

> Finally it does not work for all update, if you change anything non trivial (such as updating a struct), you cannot use ksplice and you still need to reboot.

Sure. But if it reduces the number of reboots by a factor of four, do you still think that's not worth it? (How many security patches involve changing definitions of structs?...)  

I would think it's worth it. Even if you risk new security holes (let's face it, more code = more potential for holes, that's just the way it is), if you can significantly reduce the amount of time that admins leave other holes unpatched, that's a netto win.

---

### Post by sim-value on 2009-06-28
Implemented already...
[http://brainstorm.ubuntu.com/idea/7523/](http://brainstorm.ubuntu.com/idea/7523/)

---

### Post by Patsoe on 2009-06-28
> **sim-value said:**
> Implemented already...
[http://brainstorm.ubuntu.com/idea/7523/](http://brainstorm.ubuntu.com/idea/7523/)

[http://linux.slashdot.org/comments.pl?sid=1284489&cid=28501609](http://linux.slashdot.org/comments.pl?sid=1284489&cid=28501609)

---

### Post by gnomeuser on 2009-06-28
> **Patsoe said:**
> [http://linux.slashdot.org/comments.pl?sid=1284489&cid=28501609](http://linux.slashdot.org/comments.pl?sid=1284489&cid=28501609)

I can assure you that Fedora is not doing this like that comment suggests. There might be 3rd party scripts to do it but the project most definitely does not do ksplice.

---

### Post by Patsoe on 2009-06-28
> **Patsoe said:**
> But if it reduces the number of reboots by a factor of four, do you still think that's not worth it? (How many security patches involve changing definitions of structs?...)  


Actually, it turns out it's a lot better than one in four. More like eight out of nine: [http://ksplice.com/cve-evaluation](http://ksplice.com/cve-evaluation)

edit: @gnomeuser: I think that's exactly what that comment says?

---

### Post by Thirtysixway on 2009-06-29
I may be interested in this more if their website said they had support for -server kernels.  I would use it on my ubuntu server (8.04) only because it's a home server and it's not like it has a custom kernel or anything...

Does it only apply patches or does it upgrade the whole kernel (will the version number change?)

---

### Post by scorp123 on 2009-06-30
> **Thirtysixway said:**
> I may be interested in this more if their website said they had support for -server kernels. [http://www.ksplice.com/uptrack/faq](http://www.ksplice.com/uptrack/faq)

> **Q: Which Ubuntu kernel flavors does Ksplice Uptrack support?**

A: We are now supporting all three main Ubuntu kernel flavors: generic, **_server,_** and virtual.

I assume this answers your question?


> **Thirtysixway said:**
>  Does it only apply patches Looks like it. I just tried it on my laptop. It applied six patches.

> **Thirtysixway said:**
>  or does it upgrade the whole kernel (will the version number change?) I still have the same version number like before.

---

### Post by scorp123 on 2009-07-02
This morning the update-manager reported that there was a new "linux-image" available for download ... So I did the usual "sudo apt-get update && sudo apt-get dist-upgrade" ... And still no pop-up telling me to reboot.

So far so good I guess?

---

### Post by nexus9k on 2009-07-02
No, I believe you have a new kernel from ubuntu installed now.  Someone please correct me if I am wrong, but there isn't currently a smooth integration of ksplice and ubuntu kernel updates at this moment.

---

### Post by philcamlin on 2009-07-02
cool i should have got this yesterday !!

i had to reboot for liek the third time in a 2 month peroid :D:popcorn:

---

### Post by scorp123 on 2009-07-02
> **nexus9k said:**
> there isn't currently a smooth integration of ksplice and ubuntu kernel updates at this moment. From the ksplice.com web site:

> **"Running the latest version of Ubuntu? Say goodbye to reboots!"**

Why would they say that if their stuff wasn't smoothly integrated? As I wrote above: So far no reboots, despite new kernel updates.

---

### Post by FuturePilot on 2009-07-02
> **scorp123 said:**
> From the ksplice.com web site:



Why would they say that if their stuff wasn't smoothly integrated? As I wrote above: So far no reboots, despite new kernel updates.

I'm guessing because you have to use a separate tool for it. I'm thinking what people want is nice integration with the existing update tools.

---

### Post by scorp123 on 2009-07-03
> **FuturePilot said:**
>  I'm thinking what people want is nice integration with the existing update tools. Exactly. I am using the Ubuntu update manager. Still no reboots thus far. Despite there having been new "linux-image" and "linux-headers" packages. The other laptop without KSplice immediately reported "Restart required". This one with KSplice didn't say anything about reboots so far.

My kernel version currently is:

```
> uname -a
Linux serenity 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009 i686 GNU/Linux 
```

A look into /boot/grub/menu.lst shows that this is the only kernel that is installed at the moment (I remove old kernel images so they disappear from GRUB too ...)

Either it's supressing the "Restart required!" message or it indeed doesn't need one?

It will be interesting to see what will happen if there is a big kernel update. Right now I'll leave the laptop running, just to see how far I can go without a reboot.

---

### Post by nexus9k on 2009-07-03
Wow, looks like I was wrong.

$uname -rsm
Linux 2.6.28-13-generic x86_64

$uptime
 12:29:23 up 7 days,  2:07,  5 users,  load average: 0.03, 0.07, 0.15

Very cool!

---

### Post by scorp123 on 2009-07-03
I rebooted ... just to see if there would be a difference.

Before reboot (taken from my posting above):
```
> uname -a
Linux serenity 2.6.28-13-generic **[COLOR="Red"]#44[/COLOR]**-Ubuntu SMP [COLOR="Red"]**Tue Jun 2 07:57:31**[/COLOR] UTC 2009 i686 GNU/Linux
```

After manual reboot (freshly typed into my terminal):
```
> uname -a
Linux serenity 2.6.28-13-generic **[COLOR="Red"]#45[/COLOR]**-Ubuntu SMP [COLOR="Red"]**Tue Jun 30 19:49:51**[/COLOR] UTC 2009 i686 GNU/Linux

```

So ... there was in fact a kernel update. And I needed to manually reboot in order to get to the new kernel (2.6.28-13-generic #44 vs. #45).

Given this, I now have doubts about KSplice ... What's the purpose if I in fact still need to reboot to activate the latest kernel that I just pulled via the update manager?

---

### Post by FuturePilot on 2009-07-03
> **scorp123 said:**
> I rebooted ... just to see if there would be a difference.

Before reboot (taken from my posting above):
```
> uname -a
Linux serenity 2.6.28-13-generic **[COLOR="Red"]#44[/COLOR]**-Ubuntu SMP [COLOR="Red"]**Tue Jun 2 07:57:31**[/COLOR] UTC 2009 i686 GNU/Linux
```

After manual reboot (freshly typed into my terminal):
```
> uname -a
Linux serenity 2.6.28-13-generic **[COLOR="Red"]#45[/COLOR]**-Ubuntu SMP [COLOR="Red"]**Tue Jun 30 19:49:51**[/COLOR] UTC 2009 i686 GNU/Linux

```

So ... there was in fact a kernel update. And I needed to manually reboot in order to get to the new kernel (2.6.28-13-generic #44 vs. #45).

Given this, I now have doubts about KSplice ... What's the purpose if I in fact still need to reboot to activate the latest kernel that I just pulled via the update manager?

That is because (someone correct me if I'm wrong, I don't know a whole lot about this program. I'm basing this off the information on their site) you have to apply the kernel updates with the Ksplice update program. You can't use update-manager. (which is what I was getting at with the integration thing.)

---

### Post by nexus9k on 2009-07-06
I'm guessing that ksplice patches your old kernel with the updates deemed necessary by "X" and that when you reboot, you are in fact rebooting with the upgraded kernel you installed through your update manager and not the kernel patched by ksplice.

---

### Post by SuperBaby on 2009-09-02
Ksplice is working fine in my Ubuntu Netbook Remix 9.04. There is one thing I don’t like…. every time when I boot up my netbook, some text will appear showing the loading sequence of Ksplice. It shows up after the usplash screen and the text is annoying. It seems that there is no way to turn it off.

---

