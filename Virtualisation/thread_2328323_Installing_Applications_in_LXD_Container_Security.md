---
title: "Installing Applications in LXD Container Security"
date: 2016-06-19
forum: Virtualisation
---

### Post by jay116 on 2016-06-19
This might be a basic question but I'm newer to the Linux world. I've been setting up my home server based on Ubuntu Server 16.04 LTS. I setup the SSH server and SAMBA for file sharing on the host. Then I wanted to run some applications. For backup, CrashPlan, and Plex for movie content. I decided to use LXD containers for these solutions but I have struggled to find detailed information. I setup a bridge for my containers to use to my network. I eventually got CrashPlan working on an LXD/LXC container. Though none of the headless solutions for managing CrashPlan worked I ended up using a remote desktop (xrdp) server within the container and the remote desktop application on a remote windows machine. 

The story goes on, but to my question.. I'm concerned that with my limited knowledge that my containers might not be a secure as they should be. should I install and run all applications within the container as root? Or should I install programs as another user or in someway that is more secure. If someone could point me to a guide or give some directions on the correct, secure way to install and run applications inside containers that would be great.

but, everything I've read says the root user in the container is an unprivileged user on the host. So does it even matter? All file systems that are shared with the containers are mounted as read-only as well. Any thoughts on that? 

Thanks, Jay

---

### Post by TheFu on 2016-06-20
Just back from a linux conference where containers were one of the primary topics (security, scaling, management, auditing, and other best practices).  

From what I gathered, containers, at least as far as enterprises are concerned, are meant to run 1 specific task.  The best practices presented were about creating containers and if there was any issue, blowing it away and fixing it in the next generation of container built.  They specifically said NEVER to patch a container and that if you have ssh-server running inside a container, then you are doing it wrong. The containers should have only enough OS to support running the services required inside the container - how little that is, well, that is something I don't know yet. Someone mentioned not having any shells inside their containers. They were striving to have just enough support libraries for the service being provided to run, nothing interactive available.  Containers are meant to be temporary, like a plastic baggy.  Use it until it isn't useful anymore or has any issue, then throw it away and pull out a newer, updated, fixed, container to take over.

Also, in other sessions security was discussed.  From memory, they said 
* know exactly where any container and parts used to build the contain came from.  Be very cautious using pre-built containers from unknown entities you cannot validate are real people or companies which are risking their reputation. Avoid some guy containers using a bogus name ... is "thefu" listed as the creator?  What is he risking by making a pre-built container available?  Nothing.
* Lock down the hostOS. There are ways to break out of containers, so if they do break out, ensure the userid running as root inside the container doesn't have any privileges on the hostOS.  They strongly recommended using ACLs, SELinux, and/or apparmor as protection against this concern.
* Audit the code put into the containers for CVEs and CCEs.  Every week (or month) when you normally patch your production systems, be certain to patch all the supporting libraries that go into whatever makes up the container. There are scanning tools which look at those and compare each with CVEs.  PCAP PSCAP .... something like that is a tool for this.  Lots and lots of programmers have been caught reusing the same old, out-of-date, libraries to build their software over the years. It is an epidemic.  That is how we had that USB issue last year - someone built sample code which was never meant to be used on production systems, but some USB vendor snagged that and included it with their proof-of-concept code downloads and never updated it since 2002.  The source from which they took it, had been updating their code with new features and security fixes for years, but those were never updated by the vendor.  We need to ensure this doesn't happen.  It is really hard.  Let me check my notes ... OpenSCAP is the scanning tool. 
* Use namespaces and limits.
* Use automation to build the containers and deploy them in a systematic way. Kubernetes / OpenShift Origin

Videos from the conference aren't on youtube yet. If last year is any guide, it takes about a month before they will show up.  However, one of the videos "Behind The Scenes of SELF 2016 AV and Networking" was posted already.  [https://www.youtube.com/watch?v=UScuhv21e1M](https://www.youtube.com/watch?v=UScuhv21e1M)  Watch that account for new videos.  

Wish I had more specifics for you.  I haven't played with containers much, though I do always run chromium-browser inside a private firejail.

Anyway, that's a very short summary of what I recall from about 5 different presentation by some people claiming to be experts from a large, commercial, Linux company. Does that have anything to do with your needs?  I don't know.

---

### Post by jay116 on 2016-06-22
That gives me some insight. thank you for posting that.

---

### Post by bmullan2 on 2017-01-24
@thefu

Your reply is NOT  accurate for LXC  or LXD as they are "system" containers and work just like a KVM or VirtualBox VM except without all of the hw virtualization overhead.

Your answer IS correct (re single application/process) IF you are talking ONLY  about Docker or say Rocket.

Don't  confuse the 2 very different types of containers !

Note you can actually run Docker INSIDE an LXD container...

---

### Post by TheFu on 2017-01-24
Oddly, in the last few days I saw some attack methods outlined for docker containers posted: [https://remotephone.github.io/2016/12/28/attacking-yourself-first.html](https://remotephone.github.io/2016/12/28/attacking-yourself-first.html)

That brought a question in a group and I looked up my notes and looked for the videos mentioned above. The videos from last June still have not been posted:

*    Introduction to Container Security by Thomas Cameron
*   Docker @ Scale – can’t find a video – by Darrell Breeden
*  A Security State of Mind: Compliance and Vulnerability Audits for Containers by Chris Van Tuin
*    A DevOps State Of Mind by Chris Van Tuin

```
$ youtube-dl 6rVTEG8u2n0 YANLbj5p4WA qZjMuUfGlTI
``` will grab the videos I could find.

I haven't done anything significant with containers. Just sharing resources.

---

