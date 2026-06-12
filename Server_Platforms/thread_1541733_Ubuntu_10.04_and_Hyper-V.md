---
title: "Ubuntu 10.04 and Hyper-V"
date: 2010-07-29
forum: Server Platforms
---

### Post by aesux on 2010-07-29
Hi,

I'm trying to install Ubuntu 10.04 64 bits in a VM under Windows Server 2008 R2

Before I've done the same with debian and Windows Server 2008 R2, all ok

But with Ubuntu I've problems with the VGA, lines are scrolled slowly, it seems a problem with the vga driver, could be? Any Idea?

The second problem is that the install process do not detect a network card. I've been searching but no answer that works in my situation.

Any Idea?

Thanks in advance,

Aesux

---

### Post by arrrghhh on 2010-07-29
I don't think you'll get much Hyper-V help here.  Horrid virtualization product, even Microsoft techs have admitted it.

Use vmware or VirtualBox if you'd like some support here.  Otherwise, talk to Microsoft, we can't really help with Hyper-V.

---

### Post by aesux on 2010-07-30
> **arrrghhh said:**
> I don't think you'll get much Hyper-V help here.  Horrid virtualization product, even Microsoft techs have admitted it.

Use vmware or VirtualBox if you'd like some support here.  Otherwise, talk to Microsoft, we can't really help with Hyper-V.

Thanks this is the kind of help you can give? ;)

I'm not a MS defender, but, ever, is a good idea to test all situations, isn't it? Installing Ubuntu over MS could be a first movement for an enterprise to discard MS in the future.

As I say in the question, Debian works fine in that situacion, Ubuntu no, then, Hyper-V could be as bad as you want but, the problem in that situation isn't MS.

Thanks in advance 

Aesux

---

### Post by arrrghhh on 2010-07-30
> **aesux said:**
> As I say in the question, Debian works fine in that situacion, Ubuntu no, then, Hyper-V could be as bad as you want but, the problem in that situation isn't MS.

Fine, use Debian then.

Hyper-V is not going to help people get rid of M$, it's going to do the exact opposite.  My point being, no body in this forum uses Hyper-V...

I guess I shouldn't say *no body*, I've just never seen anyone post about it... and when Microsoft employees bash their own products at their own training sessions... Just makes me wonder.  I'll never use Hyper-V, Microsoft killed it for me before I ever even tried it hahaha.

With that said, VirtualBox runs under Windows.

---

### Post by aesux on 2010-08-03
> **arrrghhh said:**
> Fine, use Debian then.

Hyper-V is not going to help people get rid of M$, it's going to do the exact opposite.  My point being, no body in this forum uses Hyper-V...

I guess I shouldn't say *no body*, I've just never seen anyone post about it... and when Microsoft employees bash their own products at their own training sessions... Just makes me wonder.  I'll never use Hyper-V, Microsoft killed it for me before I ever even tried it hahaha.

With that said, VirtualBox runs under Windows.

Are you working in a real production environment, does you know what is it? 
When people does no have answers the better way is do no answer.
Thanks for nothing

---

### Post by spynappels on 2010-08-03
I think you should not jump down aarrrghhh's throat. Elsewhere on the forums he has shown that he does understand production environments.

If the virtualisation platform you use is hostile to a specific client platform, you use another one. You say Debian does work, so logically that should be an avenue you explore. I do not use Ubuntu for PBX machines, because it is much more difficult to set up, I use CentOS instead, but for LAMP servers I will use Ubuntu. The point is that you use whatever will work best, rather than trying to force tools to do something they do not do well. This is in a production environment of course, in testing it is often desirable to push the envelope, but you specifically brought up the production environment.

Just my two pence worth...

---

### Post by spynappels on 2010-08-03
Regarding the slow scrolling in the original post, there have been some reports of this on other hardware and platforms too, and it may have something to do with Plymouth. Maybe worth investigating?

---

### Post by panterlo on 2010-10-18
Hi !

I have been working with both Ubuntu and CentOS under Hyper-V R2 and I will not make a judgment on which virtualization platform that will fit your needs but Hyper-V R2 is one choice and I am working with it 24hx7d.

The reason for the slow scrolling in console mode is the framebuffer, just blacklist it and you will get it fix. 

But I strongly don't recommend running Ubuntu 10.04 with the hv_* drivers (kernel modules) due to the "early drivers" in this kernel. It's also missing hv_utils which enabled complete time sync, heartbeath and integrated shutdown. 

You can read my post here on how to get started:
[http://www.panterlo.com/2010/10/10/ubuntu-10-10-and-hyper-v-r2/](http://www.panterlo.com/2010/10/10/ubuntu-10-10-and-hyper-v-r2/)

Please bear in mind that you should install adjtimex package and remove ntpdate. I absolutely crucial to get a good timesync.


Regards,

Jens

---

