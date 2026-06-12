---
title: "Should I give up and go back to Windows?"
date: 2021-06-29
forum: Virtualisation
---

### Post by junk.here on 2021-06-29
*Sigh*

VMware removed a feature for Linux guests that I rely on (seamless mode) with the release of Workstation 12 back in 2015. As a result, I've been using Workstation 11 for ages.

Needless to say, each LTS release has been progressively more challenging to install and run than the one before it - 16.04 was still ok and 18.04 required jumping through some minor hoops during installation but otherwise worked well, but 20.04 has given me nothing but pain over the past year.

In recent months, Canonical has been trying to force the 5.8 kernel on me. I've been resisting so far because it breaks VMware Tools (not open-vm-tools - VMware Tools), but to be honest I'm sick of constantly fighting against the flow just to have a working VM. Besides, in the long term 22.04 will definitely require kernel 5.8+ so this looks like the end of the line.

With WSL2 now being a thing in Windows 10 I am wondering if I even need Linux anymore, and dropping Linux entirely would allow me to finally upgrade to Workstation 16, which in turn would get eliminate the hoops I currently have to jump through to get Windows 10 guests up and running.

Sorry for the long rant but at this point I can't help but see Ubuntu as more of a hindrance than a useful tool. Are there any good reasons why I shouldn't just dump Ubuntu entirely and go back to Windows?

---

### Post by scorp123 on 2021-06-29
> **junk.here said:**
>   Are there any good reasons why I shouldn't just dump Ubuntu entirely and go back to Windows?

Unless there's someone holding a gun to your head and forcing you to use Ubuntu: use what works for you.

But I wonder why you never bothered to explore alternatives to your ageing VMware Workstation 11 installation? Virtualbox exists. And it gets updated a lot too (along with the rest of Linux), and it runs nicely on Ubuntu. And it can import + read + run VM's that were once created by VMware. And it has a seamless mode too.

[https://docs.oracle.com/en/virtualization/virtualbox/6.0/user/seamlesswindows.html]("https://docs.oracle.com/en/virtualization/virtualbox/6.0/user/seamlesswindows.html")

Then there are the other alternatives such as KVM, "virt-machine" manager, GNOME's "boxes", and so on. You never looked at any of them and instead tortured yourself with VMware Workstation 11? Oh well. I'm in no position to tell you how you are supposed to do your work. But why keep using something that obviously does no longer work and not look at an alternative that might work better?

Ultimately nobody can decide for you. Use what works for you.

---

### Post by MAFoElffen on 2021-06-29
LOL. VMware Workstation Pro or Workstation Player? You held onto version 11... And the current version is "16".

Right now, i put you in the category of some Architects and Engineers that held on to Windows 2000, because AutoCAD Licensing went from being Licensed to Subscriptions. To keep the Licensed version, they had to continue to stay on Windows 2000. Some went to Windows ME and Windows XP, but with Patches that allowed them to use those old version of AutoCAD. There is still some to this day that still do that that... I am still supporting some of those.

Technology changes every day. The Linux kernel changes from upstream. That is not an Ubuntu thing. Just as the Windows kernel changes. They have to to keep up with whatever the hardware advances are, and to add new capabilities. To me, after 33 years of Technical Support and such, keeping up with Technology, that is just life. That is no matter what platform you are on. Desktops and versions change, no matter what platform you are on.

64bit processors nowadays have hardware virtualization within them. Linux Kernel incorporates using that at the kernel level. So does Windows kernel... (but I will discuss that below.) To me, my choice is to use KVM on Linux. Small footprint, very fast VM guests, and very adaptable to running a whole lot of guests platforms. But that is me. VirtualBox is an option, but is software virtualization, which adds a layer of translations and a bigger footprint on top of the system and resources. On Linux, a lot of things are just free to do, and to do as you want.

VirtualBox and VMware Workstation are on either platform...

Microsoft is all about money and licensing. If you want to use the hardware virtualization features in their kernel, you have to upgrade to to a Pro (or higher) license, to be able to turn on Hyper-V. If you want to use VMware Workstation on Windows, what do you really gain? The differrences are between the Free and Pro versions, not really much between the platforms.

Microsoft Windows has shielded users, more and more, from being able to customize, tune, and change things... progressively, since version 3.0. That is not a bad thing. But a reality. Linux, you can still do things as you like. Not always good, but you can. LOL

Not saying to not use Windows. I have both, and support both to my customers. Just saying your reasoning, that you have said so far, "*something is missing*". What features do you need and what is it that you really "need to do"? That is the question, immaterial of starting out with a a platform discussion. Right? The goal is for to do your job, or to be able to do something, right?

---

### Post by junk.here on 2021-06-30
If I am to replace VMware, I would require something that can replace both client (Workstation) and server (ESXi), as I am constantly moving my VMs between them. If the choice were between dropping the easy client-server integration that VMware provides and dropping Linux, I would drop Linux every single time.

Unfortunately, none of the above listed solutions offer much in terms of integration between the 2 domains - unlike VMware, most companies do one or the other, not both - even Hyper-V is really a server product that's been crammed into a consumer OS. I think Citrix/Xen was the other company who used to offer both client and server solutions, but AFAIK they pulled out of the client space years ago.

Then again, this is all tangential to the issue at hand, really... Which is why I didn't go into a deep dive on the infrastructure of my home lab in the first place.

---

### Post by scorp123 on 2021-06-30
> **junk.here said:**
> If I am to replace VMware, I would require something that can replace both client (Workstation) and server (ESXi), as I am constantly moving my VMs between them. 

I do that too. But with Virtualbox. Both products can read VM's that the other one saved for as long as you save in the open OVF 1.0 format. So you can work on a VM in ESXi, export to OVF 1.0, import in Virtualbox... continue tweaking the VM, export to OVF 1.0 again, import into ESXi again, continue working on the VM there ...

> **junk.here said:**
>  Unfortunately, none of the above listed solutions offer much in terms of integration between the 2 domains

Also not true. 

As I said: you didn't even bother to look, right? You really should.

---

### Post by monkeybrain20122 on 2021-07-03
Not sure about your question. If you have been using Ubuntu as a VM guest in Windows all this time then you have never left Windows land in the first place, so it makes no sense to ask if you should "go back". To avoid all the problems may be as MAFo suggests how about running Windows as a VM instead?

---

### Post by CharlesA on 2021-07-03
> **junk.here said:**
> 
Unfortunately, none of the above listed solutions offer much in terms of integration between the 2 domains - unlike VMware, most companies do one or the other, not both - even Hyper-V is really a server product that's been crammed into a consumer OS.


You can run Hyper-V on Windows 10 as well as the various Windows Server version that are out there. It is built into the OS and you'll have to do the same type of configuration you need to do with VMWare or Virtualbox (especially in regards to creating the network switch and other things).

This is probably not your use case but I have been running desktop VMs off Hyper-V for a couple years now while my server VM (DNS, Gitlab, Plex, etc) are running off LXC or KVM on a couple Proxmox hosts.

I can't move desktop VMs to Proxmox though, without doing a conversion.

---

### Post by MAFoElffen on 2021-07-04
> **CharlesA said:**
> This is [COLOR=#ff0000]probably not your use case[/COLOR] but...
That is the whole issue... And why I have stayed out of this.

This is not a rant or criticism. At this point, I think we need to backup and clarify a few things, to be more productive.

The OP started with a blanket statement, creating a thread, with a very generic 1st post, without much details at all. The title asking if he should switch his host OS to Windows. The content saying (in very general terms) that he lost an integration feature in an outdated version of VMware... I and others cannot read the OP's mind. I'm just not ever going to be a very good "California Psychic."

If the OP could, instead maybe mention what he want's to do... What he needs to do... The feature he lost and misses is what? I mean, he held back 5 versions because he couldn't do "something". That "something" is still specifically unnamed and unexplained at this point.

I mean, there's 100's of ways to do the same thing, no matter what platform. With no direction or guidance from the OP, he's going to get hundreds of answers. If he would mention what he wants to do, maybe people could give him the ideas related to that. Instead, when people try to guess what he might mean, he criticizes their guess... Maybe because it's frustrating him(?)

My suggestion: Start over. Clean slate. 

What do you want to do? And what platform do you "hope" to do it on? This could clear up some of this confusion, frustration, and maybe guide this into a productive solution for you.

---

### Post by scorp123 on 2021-07-04
> **MAFoElffen said:**
>  The feature he lost and misses is what? 

"Seamless mode", apparently. Mentioned in post #2.  My issue with this thread is that alternatives with this feature do exist, OP just never bothered to take a look. They are fixated on continuing to use VMware Workstation 11, and I doubt that this will yield any positive results in the long run, aka "beating a dead horse with a stick".

At least that's my interpretation. Apologies if I'm wrong. No insults or grievances intended here, these are just my observations.

---

### Post by MAFoElffen on 2021-07-04
LOL. I "hated" that VMware trademarked feature! Just like Virt's SDL Front End, where it said to press <Cntrl><L> to get out... Which ended up really being <Left-Cntrl><Right-Alt>...

That mode, when it went wrong, was like Rage-In-A-Cage Death Match SandBox H*ll... That ended up with the only way to escape was by rebooting the machine, because you couldn't even regain enough control to kill the process. Sorry (::shivers:: ). PTSD moment. LOL

---

### Post by junk.here on 2021-07-07
> **scorp123 said:**
> I do that too. But with Virtualbox. Both products can read VM's that the other one saved for as long as you save in the open OVF 1.0 format. So you can work on a VM in ESXi, export to OVF 1.0, import in Virtualbox... continue tweaking the VM, export to OVF 1.0 again, import into ESXi again, continue working on the VM there ...



Also not true. 

As I said: you didn't even bother to look, right? You really should.

Contrary to what you seem to believe, I'm not a happy VMware customer. In fact, I've tried what you describe several times over the years, most recently in 2018.

I am willing to accept the time it takes to import/export from OVF, but the bigger problem is that it doesn't support/map every setting that every hypervisor has. So when you do OVF import/export what you get is a very barebones VM with just CPU/RAM/HDD and maybe networking (I can't recall if the MAC address is retained) and then you have to go in and reconfigure the VM each time before use. This gets tedious real quick when doing it for several VMs a day, possibly multiple times for each VM, versus a single vendor solution where a VM can be started up on system B the moment it's powered down on system A.

I know I'm repeating myself here, but just to be extra clear since I wasn't clear enough in my previous post: being able to power down a VM on one host and then start it up on another host (with the guest sitting on shared storage, of course) without any tedious work on my behalf is the level of client-server integration I need, although more (meaning live migration across hardware with different specs) is always welcome. That said, it's possible that OVF has gotten much better over the past 3 years and I'm just not aware of it, as I indeed have not looked since 2018.

But that's just for Linux guests. Windows guests have the additional problem of activation issues due to differences in virtual hardware each hypervisor exposes. I suppose it might be theoretically possible to have VirtualBox and VMware running at the same time, but that's something I haven't tested at all.

> **monkeybrain20122 said:**
> Not sure about your question. If you have been using Ubuntu as a VM guest in Windows all this time then you have never left Windows land in the first place, so it makes no sense to ask if you should "go back". To avoid all the problems may be as MAFo suggests how about running Windows as a VM instead?

Nvidia Linux drivers and Windows DirectX games make that a no-go, sadly.

I touched on this briefly in my original post, but years ago I tried running XenClient on my PC and XenServer on my server. Had it worked out then this would be fine since I could just pass my GPU through to a Windows VM for gaming purposes, but unfortunately Citrix announced the retirement of XenClient while that project was still in the planning stages.

> **CharlesA said:**
> You can run Hyper-V on Windows 10 as well as the various Windows Server version that are out there. It is built into the OS and you'll have to do the same type of configuration you need to do with VMWare or Virtualbox (especially in regards to creating the network switch and other things).

This is probably not your use case but I have been running desktop VMs off Hyper-V for a couple years now while my server VM (DNS, Gitlab, Plex, etc) are running off LXC or KVM on a couple Proxmox hosts.

I can't move desktop VMs to Proxmox though, without doing a conversion.

At least on Windows 10 1909, the 2 ways to access a VM that I know of are via the Hyper-V console and via RDP, and neither provided a seamless mode. If anything, the Hyper-V console is geared towards VM management and administration rather than day to day use by end users and RDP is by design intended for a client to connect to a server, which is why I called Hyper-V on Windows 10 "a server product that's been crammed into a consumer OS" to begin with.

If Microsoft added a seamless mode to Hyper-V in newer versions of Windows 10, I'm all ears. I've liked Hyper-V (far more than VMware, at least) since Microsoft added proper VT-d passthrough in Windows Server 2016, so at this point the lack of seamless mode is the only thing holding me back from switching.

---

### Post by cryptearth on 2021-07-11
> **junk.here said:**
> [...] when doing it for several VMs a day, possibly multiple times for each VM, versus a single vendor solution where a VM can be started up on system B the moment it's powered down on system A. [...]
Although I do get you may like the "live migration" feature - as I'm not so into it may I ask: WHY?

As you mentioned gaming, windows and nvidia: I do use KVM with GPU passthrough to play some games on a win10 guest which I wasn't able to get running using steams proton (although I'm still new to it - I may have to read some tutorials about how to use that). Ok, maybe my setup is way simpler: I have both the gpu as well as the storage local so I can hook up the required hardware directly - but as you talk about gaming: If what I asume is correct, that your vm runs on  a remote server which has the harwdare in it / attached to it, then this sounds like a bad idea to me.
If you want to game - do it locally, it's the way simpler option than try to play around with remote hardware and vm and try to rebuild what's basically like googles stadia or such - although it's a nice weekend project for personal research.

I'm not the one to judge, but I'm the same opinion as what's already said: It seems you used a specific setup for years now, stuck to it, and not bothered to look behind the curtain what other solutions are may around.
Also: Although you now said what feature in particular you'Re missing - it's still not really clear why in the first place. Moving around live VMs across multiple systems sounds more like a fail-over strategy to me than what should be done all day long for several VMs, let alone doing it for the same VM several times a day. This sounds more like a training excercise to teach someone how it's done in the case it's required - but even running a "home lab" that's something one may tries to do once or twice, maybe a third time to make a YT video. What you describe sounds a bit like you'Re moving around several systems while the still run - but just virtual as they're VMs instead of physical machines.

So, again: WHY you want to do this and why it's a feature you rely so heavily on you stuck back in 2018? Hardware and software evolved quite a lot over the past 2-3 years. There'Re sure other solutions out there. If it's worth paying for them just for your joy (at least that's what I get from the term "home lab") is up to you.

---

### Post by junk.here on 2021-07-19
> **cryptearth said:**
> Although I do get you may like the "live migration" feature - as I'm not so into it may I ask: WHY?

As you mentioned gaming, windows and nvidia: I do use KVM with GPU passthrough to play some games on a win10 guest which I wasn't able to get running using steams proton (although I'm still new to it - I may have to read some tutorials about how to use that). Ok, maybe my setup is way simpler: I have both the gpu as well as the storage local so I can hook up the required hardware directly - but as you talk about gaming: If what I asume is correct, that your vm runs on  a remote server which has the harwdare in it / attached to it, then this sounds like a bad idea to me.
If you want to game - do it locally, it's the way simpler option than try to play around with remote hardware and vm and try to rebuild what's basically like googles stadia or such - although it's a nice weekend project for personal research.

I'm not the one to judge, but I'm the same opinion as what's already said: It seems you used a specific setup for years now, stuck to it, and not bothered to look behind the curtain what other solutions are may around.
Also: Although you now said what feature in particular you'Re missing - it's still not really clear why in the first place. Moving around live VMs across multiple systems sounds more like a fail-over strategy to me than what should be done all day long for several VMs, let alone doing it for the same VM several times a day. This sounds more like a training excercise to teach someone how it's done in the case it's required - but even running a "home lab" that's something one may tries to do once or twice, maybe a third time to make a YT video. What you describe sounds a bit like you'Re moving around several systems while the still run - but just virtual as they're VMs instead of physical machines.

So, again: WHY you want to do this and why it's a feature you rely so heavily on you stuck back in 2018? Hardware and software evolved quite a lot over the past 2-3 years. There'Re sure other solutions out there. If it's worth paying for them just for your joy (at least that's what I get from the term "home lab") is up to you.

I can't believe I need to say this, but **none of what I have said in this thread constitutes a full set of requirements**** that would need to be met in order to switch to some other solution**. Because that was never my objective, **nor is it the question that I am asking which is in the title of this thread**. At most, everything I have said in various replies is simply an explanation of which checkboxes a given solution did not tick during the evaluation phase.

To be honest, at this point I'm completely bewildered by how a number of different people have come into this thread to offer advice that has nothing to do with the question being asked. I would kinda understand if it had a "try and retain a Ubuntu user" angle to it, but it doesn't feel like that's the case at all. Rather, I'm getting the sense that this community just has very weak reading comprehension skills and is responding to what they think I am asking as opposed to what I am actually asking, even though the question is, once again, right in the title of the thread.

---

### Post by QIII on 2021-07-19
Then ... yes.  Go back to Windows.

Or ... no.  Don't go back to Windows.

The choice is yours and it depends on what suits your needs.  That much we can't tell you.

Closed.

---

