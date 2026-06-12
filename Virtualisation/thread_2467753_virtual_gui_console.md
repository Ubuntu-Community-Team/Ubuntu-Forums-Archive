---
title: "virtual gui console"
date: 2021-10-07
forum: Virtualisation
---

### Post by Eric_Johansson on 2021-10-07
running Ubuntu desktop on xcp-ng using NX for remote desktop. The problem is that the virtual console of XCP has a limited number of resolutions and since NX provides remote access by replicating the console, the remote desktop is also limited.

Is there any way to create a standalone virtual console that NX could use on what ever resolution it wants?

---

### Post by TheFu on 2021-10-07
Seems like an XCP question, based on my experience with other hypervisors.  I know that KVM/libvirt allows all sorts of funky resolutions.  With x2go, there are 2 halves of the resolution solution.  Having the guest OS say what resolutions it wants and having x2go pick one of those.

With Spice, the integration is much cleaner.  To my knowledge Spice only works on KVM systems. On a LAN, Spice is faster than every other remote session protocol that I've used. Much faster.  [https://wiki.xenproject.org/wiki/SPICE_support_in_Xen](https://wiki.xenproject.org/wiki/SPICE_support_in_Xen) looks like it is in the roadmap.  Spice over ssh is easy and fast, BTW - well - at least using libvirt + virt-viewer.

Sorry I don't have an answer for XCP. We switched from Xen (Xm) around 2011 and have never looked back.  XCP seems to have a pretty web interface, I'll give them that. Seems similar to oVirt on KVM systems.  We just use virt-manager and virt-viewer here to avoid the security problems that webapps always seem to bring.

---

### Post by Eric_Johansson on 2021-10-07
Thanks for the response. I've spoken with the XCP folks about this issue and they referred me to UDS Enterprise as a possible solution. Seems like a bit of overkill for my use case, not to mention expensive. I've also been referred to NoMachine Workstation which allows for up to four virtual consoles. Much easier install and set up but still expensive. Unfortunately, it seems like with authentication systems, the simple solutions have been abandoned in favor of the more complicated and expensive ones that only scale up but don't scale down.

Re-spice and speed, whenever used the spice console in virt-manager, I was never impressed by the performance and as soon as you went overall VPN, performance hit the floor. A pitch for NX is that the quality and speed was good enough that video editors could work from home using their in office machines and running NX over their Comcast cable connections. It was pretty damn impressive.

I understand why you've made the migration to KVM. I'm going the other way. I've used KVM for years and have been frustrated by many of its shortcomings. At one place they went from KVM to VMware because those same frustrations. I was really pleased I discovered that XCP-NG and Xen Orchestra gave me a VMware like experience for a fraction of the cost. It solved many of my pain points in terms of real-time VM migration, integration with different kinds of storage pools, and the ability to group together multiple machines in a single vm host pool, and live backups.

Again thanks for your response. I appreciate your perspective.

---

### Post by MAFoElffen on 2021-10-09
Editted: Content removed to protect the innocent.

---

### Post by MAFoElffen on 2021-10-09
OR...

Like "any" VM Guest... Set the resolution of your VM to what you want., within that Guest OS. Then view it from any myriad of VM Viewers. I say that generically, because of your original, very vague, title and first post... But, when someone tried to answer that, that is where your "tone" changed.

Each VM Host system has it's pro's and con's. I spent years with Xen Server and Citrix, and moved way from it. I have done this for a very long time. Even AWS moved from XEN to KVM... So in market trends and technology wise, going from KVM to XCP, would not seem as you talked down to TheFu about, telling him "he was backwards". Maybe not in those words, but that is how it seemed to come across.  

What you asked about originally has nothing to do with your last post. All of a sudden it was "this is better than that", with "branding". Which has nothing to do with VM Viewers and the resolution of the presentation.

I  do Citrix/XEN, KVM/RHEV/oVirt, vSphere/ESXi, Hyper-V, OpenStack/OVM, OpenShift/OKD, Docker, LXD, EC2, and others. I can  talk about supporting each... Only because I've been exposed to a lot of things over the years. I've had successes and failures... and learned from them.

I do not try to push any brands or specific products. I try to remain unbiased. I try to be courteous and respectful. I try my best to be careful to not  offend and talk down to others. It sounds like you are not open to suggestions or anything that differs from how you think, do things. One would wonder why you asked a question if you did not want to hear what someone said. 

An observation- The person you just "talked down to".. that almost sounded a bit condescending... You have no idea of who he is or how long he has been an SME in his field (professionally). Even then, he has spent years on this forum, helping people with their problems. I feel that your snap judgement, talking to him as if you knew better, shows a lot about you and your intentions towards "others". As if you had an unswaying preconceived opinion before anything was even said. I would hope that first impression is wrong.

I do not know anything about you. And you do not know anything about me, or other's here. Maybe we should start over and play nicely. This should be a safe area for all. To discuss and help each other.

------------------------------
EDIT:
- - - - > Or maybe I misread or misunderstood what you were trying to say... Talking with TheFu, he said I was wrong with that. Hard to read between  the lines sometimes, and I apologize if I read and mistook it that way.

Are you or your users using XenDesktop? Are you talking about what is supported by the Virtual Display Agent (VDA) of the XCP server, and the VDA of the XenDesktop Client? Or are you using Citrix'es ICA protocol for your session?

---

### Post by TheFu on 2021-10-09
MAFoElffen. I didn't read that I was "backwards".  What I saw was that a business had decided to switch from one hypervisor to another for "reasons", which I assumed were good reasons.  Not all solutions work for what it important, in every situation. 

Eric_Johansson, what I saw was two people, with different backgrounds, both extensive, chatting about a technical issue, seeking a solution. I was not offended in the least. Plus, I have a short memory.

I'd actually written a reply, but was letting it soak ... and didn't post after realizing it wasn't going to directly help with the issue. It was more about using commercial tools, getting screwed and setting up clients to be screwed after a corporate change that was going to 2-3x their license costs. Not really connected to the technical questions in this thread.  It was better not being posted.

Back to my weekly systems maintenance tasks ...

---

