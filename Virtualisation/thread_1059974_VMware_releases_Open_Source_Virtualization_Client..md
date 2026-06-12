---
title: "VMware releases Open Source Virtualization Client."
date: 2009-02-04
forum: Virtualisation
---

### Post by albinootje on 2009-02-04
From : [http://ostatic.com/blog/vmware-saw-the-threat-releases-open-source-virtualization-client](http://ostatic.com/blog/vmware-saw-the-threat-releases-open-source-virtualization-client)
> 
Last year, following a crash in its share price and the replacement of its CEO with a seasoned Microsoft executive, I wrote about the perils that virtualization titan VMware faces. The problems come from two trends: 1) open source virtualization offerings; and 2) free virtualization within operating systems. From the free virtualization project Xen to the virtualization that Microsoft, Sun, Red Hat and others offer in operating systems,VMware's proprietary strategy looked mighty shaky. Today, VMware made what I consider the shrewdest move it could: launching an open source client for virtual desktops.

The CEO replacement who entered VMware last year was Paul Maritz, a long-time Microsoft executive with intimate familiarity with how Windows swallowed up entire categories of utility software as it grew up, by simply wrapping free utilities into the operating system. Paul knows about that, and he had to have seen last year the dual threats to VMware of open source virtualization offerings and virtualization on board in operating systems.

The VMware View Open Client allows businesses to host virtualized desktops in the data center, and users can access their desktops from any device. Going with an open source solution like this was VMware's only choice, especially as Microsoft includes Hyper-V virtualization in Windows Server. I'm sure Maritz was very focused on the Microsoft threat, because he used to be behind similar threats. VMware can grab market share with this move, stave off Microsoft dominance, and offer support and services around its open source offering. The company will also get substantial good PR from the decision.

You can get VMware View Open Client here, licensed under the Lesser GPL. It's essentially a bet that customized user desktops are hosted in data centers, and that businesses will take to the idea that they can save money by centralizing custom solutions in data centers for desktop users to take advantage of through virtualization.

I agree with Dana Blankenhorn that this could cause a big shakeup in the software world. "Imagine what the PC world would be like if enterprises are able to slow purchases regardless of head count," he writes. "Imagine what Microsoft revenues might look like in that world." Indeed. 


---

### Post by PilotJLR on 2009-02-04
I've switched to this client already; it works very well. Much better than the Java applet linux users previously had to use.

For those new to View, note that this client is somewhat analogous to a Citrix ICA Client. In itself, it's not a virtualization platform.

---

### Post by HermanAB on 2009-02-04
Why use this at all?  What is wrong with RDP and rdesktop?

Cheers,

Herman

---

### Post by PilotJLR on 2009-02-04
It connects to a View or VDM2 connection broker. RDP actually is used for the presentation protocol.

The connection broker security server is exposed to the internet (assuming that is what IT wants), then the user connects and authenticates using the View client. The View connection broker allocated a session on the Infrastructure and then proxies the connection to the endpoint.

---

