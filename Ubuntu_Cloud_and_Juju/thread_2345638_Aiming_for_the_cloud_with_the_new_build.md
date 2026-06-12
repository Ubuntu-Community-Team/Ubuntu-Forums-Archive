---
title: "Aiming for the cloud with the new build"
date: 2016-12-06
forum: Ubuntu Cloud and Juju
---

### Post by kc_2 on 2016-12-06
I just posted this...
[https://ubuntuforums.org/showthread.php?t=2345637&p=13579293](https://ubuntuforums.org/showthread.php?t=2345637&p=13579293)
...about multi-purposing my new computer, as server and workstation.

I only want to auto-load server components, but that will include cloud-based services.

I recently found out there's an Ubuntu+OpenStack type variant, I'm very interested in setting up an OpenStack-driven IaaS. However, I might ultimately end up doing it on different hardware, like multiple NUCs. Yet, then again, if I can pull something off with it with the new computer, I'll give it a go. Otherwise, I'm also interested in various other devops-ish apps and services, like docker, chef, vagrant, etc. I have about 10 systems in mind that I'd like to run within their own internal network, although I'll probably have to keep things fairly thin considering I'm only working with a 4-core CPU and 32GB memory. Any input on where to go next would be very helpful. Thanks!

---

### Post by TheFu on 2016-12-06
32G of RAM is enough to run 60+ Linux VMs or 3 Windows VMs (I joke).  Redhat is saying there is a 10:1 ratio of containers to VMs, so that would imply enough RAM to have 600 containers.  Not exactly "thin", IMHO.

I don't understand what you mean by "auto-load server components" - I always only install an ssh-server with a fresh OS install. Then use DevOps/scripts to build the specific machine required.  That I do on a new server: [http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server) , I wrote this as a way to counteract similar articles clearly written by script developers without any admin experience.  I was a programmer for the first decade of my career, then moved in to architecture and administration. Been a systems admin the last 8 yrs, which has altered my view on many things.

OpenStack requires 2 physical nodes to work and 10 physical nodes to be useful. If straight enterprise virtualization knowledge isn't strong, start with getting that knowledge first.  Crawl, walk, jog, run, sprint.  Openstack is sprinting, FWIW.

---

### Post by kc_2 on 2016-12-06
> **TheFu said:**
> 32G of RAM is enough to run 60+ Linux VMs or 3 Windows VMs (I joke).  Redhat is saying there is a 10:1 ratio of containers to VMs, so that would imply enough RAM to have 600 containers.  Not exactly "thin", IMHO.

I think I'll be more limited in CPU than in RAM, but at least it doesn't take much to eat up memory, so it'll probably balance out in the end. I will also only build the separate instances on an as-needed (or really on a "when ready") basis.

> I don't understand what you mean by "auto-load server components" - I always only install an ssh-server with a fresh OS install.

I just meant that, basically, anything that the server will need to operate will load on boot. I went ahead and installed more than just sshd, but a variety of other things, maybe I can stop/disable & remove them.

This may have been the stuff, unless it has changed between system versions:

[IMG]http://i.stack.imgur.com/aSgQs.png[/IMG]

So I might be better off uninstalling some of that, although would hate to leave leftovers / dependencies just sitting around.

> Then use DevOps/scripts to build the specific machine required.

I'm working my way toward that, but it'll be a while yet. I need to actually write them and/or find them.

> That I do on a new server: [http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server) , I wrote this as a way to counteract similar articles clearly written by script developers without any admin experience.

That page has helpful info in it, thank you. I'm curious why you chose Ansible over the others. I'm using Chef with other stuff, so this will be a good chance for me to practice it.

> I was a programmer for the first decade of my career, then moved in to architecture and administration. Been a systems admin the last 8 yrs, which has altered my view on many things.

I'm also interested in the dev side of things, learning Ruby. How has the move from programmer to admin altered your view on things?

> OpenStack requires 2 physical nodes to work and 10 physical nodes to be useful.

That's right, I remember reading somewhere that 2+ nodes are needed. I might go the NUC route when I go all in with OpenStack. I'd love to give it a try on the current build, if there's any way to pull it off. For my main lab server type tasks, I'll focus on spinning up (eventually, a bunch of) systems, will need to figure out how to turn them into their own self-contained IaaS.

> If straight enterprise virtualization knowledge isn't strong, start with getting that knowledge first.  Crawl, walk, jog, run, sprint.  Openstack is sprinting, FWIW.

I'm all for sprinting with it, but am also interested in a variety of other resources, like Docker. Taking advantage of Vagrant. Various apps that can somehow work together as pieces of a puzzle to come together to make a single picture.

Of course, first things first, I installed the Ubuntu Server without a network connection, so it didn't automatically set that up, now I'm without internet on it, so need to get that going.

---

### Post by TheFu on 2016-12-06
>  Crawl, walk, jog, run, sprint

My point was that you are wanting to sprint when you are prepared to be crawling, at least with Ubuntu.
I've never seen Vagrant used on production systems, just for developers.
I signed up for 3 days of Chef training. Walked out after 4 hrs. They use "magic locations" that you are supposed to "know" for things to work.  Plus, chef and puppet and saltstack all require agents on every box.  That's a non-starter for me.  Ansible has minimal server dependencies.  With 14.04, they were all met by a default Ubuntu server + ssh-server install. Nothing else was needed.  With 16.04, there are a few dependencies that need to be installed, but not an entire language! That's just crazy.  Admin tools should be lite and not get in the way.  Attended a full day Puppet rally and heard all the issues from people trying to run puppet. Seemed worse than the problem they were trying to solve with the tool.

Ansible was created by a former puppet-labs guy. He also created Cobbler while at Redhat. For a seasoned admin, getting started and controlling systems takes about 30 minutes with ansible - without any other help.  Can't do that with chef or puppet.  Puppet is the microsoft of devops. There will always be people needing help.

I can't imagine having a server without ssh installed.  Not talking about containers (no ssh for them), but VMs and physical systems all need ssh.  Master ssh.

Crawl my friend. Crawl first.  Install KVM. Use virsh and virt-manager to play around a bit. Use the different storage backends. Get comfortable with NAT and bridging setup, teardown, configuration. Learn more Linux admin stuff.  Stop chasing buzzwords. They will be there when you are ready. Look up kubernetes and atomic.

I did ruby training for 3 yrs - as the Linux guy helping others. Enjoyed the language, hated the biannual complete rework of ruby, then rails, then ruby, then rails.  Broken gems.  Broken apps.  Considering going back to work as a ruby dev with a long term plan of working from anywhere in the world about 20% of my time.  Being an enterprise architect doesn't really fit that goal (too many meetings in the wrong time zones) and neither does being an admin.  

Oh .... and NUCs are $150 too expensive for what you get, IMHO.  Is small-ish size really worth that premium?  Look at Shuttle made PCs. They are mini-desktops, cheap, but still very powerful.  All these tiny, powerful, computers have cooling issues.  If you came from Windows, the idea of a powerful system has been warped.  With Linux, 10x less resources are probably necessary.   Especially if you don't load a full bloated server and only load the minimal dependencies needed for the specific applications to be run.  That is the container best practice.  Basically, a container to be able to do 1 thing and only that thing. No shells. No desktops. No other tools/apps, just the 1 thing the container should be doing.  This is important for security reasons.  Breaking out of a container is getting harder, but it is still possible.  Saw an exploit today using a named pipe, sh, and nc thanks to someone doing continuous integration using a public repo.

Keep moving forward. Keep learning by doing. You've got an amazing machine to play with, but don't get hung up on getting the setup perfect. You won't.  I won't. Things change over time and we learn more.

Devs vs Admins .... devs think they can solve any problem.  Admins want to use proven methods to solve problems. Surprises are daily for a dev, but if your server keeps "surprising you", that means the admin sucks.  Admins want stability and the ability to rebuild what was there quickly. They also don't want calls after 6pm or before 9am.  I was on-call 24/7/365 for 2+ yrs in a govt facility. It ran 24/7/365 with 600+ people working around the clock.  ZERO remote access, so any issue meant I had to drive into the location to help.  Missing every holiday because I was stuck in that town, not allowed to leave, sucked.  I don't like surprises. I don't like unplanned downtime.  I want the appropriate amount of redundancy, but not any more.  I demand daily, automatic, 100% working, backups that can be restored in 45min or less.  I know that it takes at least 3 attempts to get a solid backup technique down and that testing the restores is THE ONLY WAY to know for certain.  I know that HDDs fail. No way to stop it and that the best solution for that is the most recent backup.  RAID is not a backup and only solves 3 problems.  Backups solve 1,000+ problems (and counting).  I'm a huge believer and user of virtualization. I'm not sold about containers yet.  Claims of container security are unproven. They need 5 more years to ferment.  For now, the best practice is to run containers inside a VM, according to Redhat.  I know that storage architecture is a non-trivial thing. Like network architecture, it is the foundation of a stable, solid, secure, computing infrastructure.   I know that SDNs doesn't remove the need to understand networking.  Often, devops people from dev backgrounds forget that c is the law, not just really fast.  It matters.  No networking today supports having the same subnet split over 500 miles apart with the needed latency, regardless of what an SDN allows.  Even 100Gbps networking doesn't. People do try it and it sucks.

And I know that practicing anything makes us better at it.  Doing more server installs is a good thing, even if on the same hardware. ;)

Sorry for ranting a little.  I also know that there is always a bunch of people who know more than I.

---

### Post by kc_2 on 2016-12-07
> **TheFu said:**
> My point was that you are wanting to sprint when you are prepared to be crawling, at least with Ubuntu.

I'm not sure I said I want to crawl, if I gave the impression that I am not prepared to sprint then I was unclear. Maintaining a security approach toward what I say to the open world of the internet, I'll just note that I am exposed to an environment where everyday is a sprint, including learning new technologies.

> I've never seen Vagrant used on production systems, just for developers.

My intention for vagrant is specifically dev/test purposes, that's all.

> I signed up for 3 days of Chef training. Walked out after 4 hrs.

Chef is a powerful tool. I'm always learning more, and Ansible is on the list. It sounds like a handy, lightweight tool.

> I can't imagine having a server without ssh installed.

Likewise. I reinstalled the system, opted out of the bloaty apps that I don't need on the host server, those will go on the VMs, and included sshd. I almost opted to do the manual install option, to just go through the list and select minimal, even fewer, but decided to just go with the generic base install without adding the bloat. I checked the list of default/base install, it is very light.

> Not talking about containers (no ssh for them), but VMs and physical systems all need ssh. Master ssh.

What you do mean no ssh for containers? What type of containers are you talking about?

> Crawl first.

More like crawl first, remember, then sprint. I didn't explain my background (again for the security), basically I have worked with many of these technologies, when constantly going from one to the next, learning something new all the time, it takes going back to square one to get a refresher like it's the first day of school, then once things kick into gear, reminded of key steps, things jump back into high speed. That might not be the way it works for some people, that's fine.

> Install KVM. Use virsh and virt-manager to play around a bit. Use the different storage backends. Get comfortable with NAT and bridging setup, teardown, configuration. Learn more Linux admin stuff. Stop chasing buzzwords. They will be there when you are ready. Look up kubernetes and atomic.

Part of learning or in some cases relearning content is that what's new is nearly identical to what's not, with exception to being approached from a different angle, which in itself makes it new, while the association with what has already been learned makes it easier to learn. 

> Look at Shuttle made PCs.

I'd have to compare the detailed specs between those and NUCs, at a glance the Shuttles appear to be a better deal.

> 1 thing and only that thing.

That's not an option at present, hence building a multi-purpose computer. I will go for the separate, more individually purposed systems in future.

> Devs vs Admins

In some cases, there is no versus, or very little of it, and it's mostly devops, unified. Of course, that depends on the approach.

> Surprises are daily for a dev

One would hope, and yet there is also stability in the process.

> server keeps "surprising you", that means the admin sucks.

I know someone that fired their boss (by quitting) for that reason.

> I don't like unplanned downtime.

It's going to happen, but at least it can be minimized with enough preemptive effort. Get more 9s, and now it's even possible to hit 100 and maintain, where anything less is due to other factors that at least are on someone else to deal with.

> I'm not sold about containers yet.

What kind?

> And I know that practicing anything makes us better at it. Doing more server installs is a good thing, even if on the same hardware. ;)

Yep! :)

---

### Post by kc_2 on 2016-12-09
I'm used to rhel commands, what's the debian/ubuntu equivalent to chkconfig or similar to see installed applications, along with if they're enabled/disabled started/stopped? I can just set any non-server (just workstation) apps to disabled so they won't load on boot, and only set server-type services to enabled.

---

