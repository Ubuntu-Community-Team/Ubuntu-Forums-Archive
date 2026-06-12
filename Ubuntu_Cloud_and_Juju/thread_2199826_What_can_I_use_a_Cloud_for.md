---
title: "What can I use a Cloud for"
date: 2014-01-15
forum: Ubuntu Cloud and Juju
---

### Post by ov10fac on 2014-01-15
Ok,

I have owncloud running on a version of nas4free.  Works great but has serious sync issues on my laptop, keeps dying.  But thats another story.  What I am really wondering about is what other uses are there for the cloud.  I have been doing some reading and it looks like a lot of effort is being directed at using KVM to provide web access via remote desktop to web  based operating systems.  So here are my questions.

1.  What is the difference between running a plain old server with KVM and several images.  Why use a cloud instead of this kind of thing.
2.  If I use a cloud or RDP to access an image, I still need some kind of operating system on my laptop to access the image.  What is the advantage of that?  We used to get small boxes that ran an imbedded windows that could use rdp to access a remote windows system. An inexpensive way to provide a lot of OS to people while keeping the cost of the Desktop systems down. Seems to be about the same thing to me and now with Desktops so inexpensive, not really a big advantage.
3.  What is the advantage of running an OS from the cloud vs from your machine.
4.  Can you run different apps from the cloud.  I see there is a version of Libre Office that can be run on a server and accessed via a web browser.  That doesnt seem very practical. Why not just load LibreOffice on your Linux or Windows computere.

I guess in general, I am looking for some good purpose for a cloud other than making data universally available, and I'm not really convinced thats such a good thing to be doing anyway.

Many thanks for any idears you want to share.

---

### Post by tgalati4 on 2014-01-16
For personal use, maybe not the best use case.  If you are running a virtual company that sells virtual products and accepts virtual currency and you want to spin up a lot of machines quickly to satisfy the virtual demand, then The Cloud makes sense.

---

### Post by ov10fac on 2014-01-16
> **tgalati4 said:**
> For personal use, maybe not the best use case.  If you are running a virtual company that sells virtual products and accepts virtual currency and you want to spin up a lot of machines quickly to satisfy the virtual demand, then The Cloud makes sense.

Hmm. Ok.  I'm was thinking more along the lines of a real company with multiple users running Windows and windows based apps.  Or a company running Linux/Ubuntu and Linux based apps.  Thank you for your reply.

---

### Post by tgalati4 on 2014-01-16
As you have already pointed out, because the cost of desktop machines is so low (how about RaspberryPi's taped under the desk), using cloud services to serve desktops may not make sense.  If you are trying to save Windows license fees, then there may be a use case, but the performance of such a cloud-based infrastructure will have you ask such questions.  Unless you can articulate some specific use cases, you are correct to ask the questions.

Do you have more than one physical location?  Cloud services could support multiple locations with one IT footprint.  Do you have real-time databases (as in transaction processing) that multiple locations need access to?  Cloud servcies could host those database services with backup and surge capability when things get busy.  Only you can answer those questions.

---

### Post by ov10fac on 2014-01-16
> **tgalati4 said:**
> As you have already pointed out, because the cost of desktop machines is so low (how about RaspberryPi's taped under the desk), using cloud services to serve desktops may not make sense.  If you are trying to save Windows license fees, then there may be a use case, but the performance of such a cloud-based infrastructure will have you ask such questions.  Unless you can articulate some specific use cases, you are correct to ask the questions.

Do you have more than one physical location?  Cloud services could support multiple locations with one IT footprint.  Do you have real-time databases (as in transaction processing) that multiple locations need access to?  Cloud servcies could host those database services with backup and surge capability when things get busy.  Only you can answer those questions.

Ok,  Here's what I am looking at.  I have two clients that both need access to a centralized application.  Both have remote facilities.  One currently uses VPN to connect the remote facilities to the home server then RDP to run the app.  At the home location, a simple Client Server arrangement is used.  Second client is all remote access using RDP to connect to a server running the application.  This client uses MS Terminal Services Server.

My Academic Interest in Cloud makes me wonder if the same thing could be done cheaper, or more efficiently using cloud based server located at the home sites.  An academic study right now, but maybe if it proves to be cost effective, maybe a new approach to shared access.

Thanks for the information and reply.

---

### Post by tgalati4 on 2014-01-16
The way to convolute Windows services simply boggles the mind.  I've seen businesses take snapshots of Windows desktop machines and reload them every morning so that the desktop is "fresh".
This presumably reduces the IT staff workload since each desktop's Windows entropy is at most one day old.  

You will have to do some experiments to see if The Cloud makes sense for your clients.

---

### Post by ov10fac on 2014-01-17
Ok,

So I assume the images are virtual machine images.  I would think just reloading the original image woul be the way to go.

Many thanks for the insight.  A lot more research before I figure this all out.

---

### Post by 1clue on 2014-01-17
A cloud is an abstraction.

The idea is that you have a "farm" of VM hosts, either VMware or KVM/Qemu, or whatever.  These hosts are all pretty much the same, and the cloud manager tries to keep them balanced for load by some strategy.

Now you, or the IT staff of the company, get need for a server.  You requisition one from "the cloud" with specs. In a few minutes, there's a VM and it has some sort of operating system on it per your specs.

That server resides on the cloud, but it's no longer an abstract server.  It's configured the way you configure it just like a real box.  You don't know exactly where it is, the cloud manager takes care of that.

The only things you really need to know about a cloud server:
[LIST=1]
[*]What operating system is on it.
[*]How much RAM
[*]Hard disk space (and possibly speed)
[*]Firewall settings
[*]What software is on it.
[*]How heavily it's used.
[/LIST]

Now, what you use it for:  It can be anything, but you need a client or clients to get that information.  You could have a web server, or an application server, or a mail server, or whatever.  You could have some sort of computation application going on it (weather modeling or something) or anything else you can dream up.

The questions you're asking on this thread, it seems you don't see the point for a server, much less a cloud.  That's OK, generally speaking for personal use there isn't one.

A company owner or IT manager would want a cloud so they can:
[LIST=1]
[*]Make full use of hardware they have.
[*]Measure how much of their hardware is used.
[*]Have quantifiable space and capability for expansion
[*]Handle system management in an abstract and consistent way.
[*]Have failover in case one host goes down.
[*]Anticipate need for hardware upgrades
[*]Enable hardware upgrades without loss of service for users.
[/LIST]

Some virtualization schemes can move a server from one host to another without shutting it off.

Now for a server:
You've mentioned a server vs having an office app on each computer.  Some reasons for the centralized approach:
[LIST=1]
[*]If you have software installed on every workstation:
[LIST=1]
[*]You have to make sure the software is installed and working on every computer.
[*]If a disk fails you lost a license, and probably the documents somebody saved on that disk.
[*]You can't really control what each employee sees.
[*]Software version control is problematic.
[*]Your IT staff bounces around from computer to computer to get their work done, at which time the employee who usually sits there is paid to stand there.
[/LIST]

[*]If you use a server (e.g. Microsoft Terminal Services or an equivalent X server setup for Linux):
[LIST=1]
[*]Everyone has the same version of every app.
[*]Their documents all get stored in a specific place
[*]Your IT staff can back up that place every night with a centralized backup.
[*]The clients can be pretty much anything, and don't even need a hard disk.
[*]System changes are done by the IT staff without having to interact much with users.
[/LIST]

[*]A server on a public cloud:
[LIST=1]
[*]You no longer have to support hardware maintenance.
[*]You pay a monthly fee for the server, which is a predictable cost.
[*]Somebody else handles backups
[*]Your employees can work at home or at the office, pretty much the same thing.
[*]Upgrading a server means you specify the upgrade parameters, schedule a time and the server is upgraded.
[*]Duplicating a server means you provision it, and use the first server as a model.  Again, a few minutes and it can be done, depending on how much data is involved.
[/LIST]
[/LIST]

Now, the difference between a public cloud and a private cloud is that with a private cloud you set up your VM hosts as you want, and nobody has access to the hardware except you and your company.  You perform the maintenance, you buy the hardware, your people are on the hot seat if something breaks.  A public cloud, somebody else does all that and there's an extremely good chance that they'll have your information up and running WAY before your personal guys could do it.

---

### Post by 1clue on 2014-01-17
> **tgalati4 said:**
> The way to convolute Windows services simply boggles the mind.  I've seen businesses take snapshots of Windows desktop machines and reload them every morning so that the desktop is "fresh".
This presumably reduces the IT staff workload since each desktop's Windows entropy is at most one day old.  

You will have to do some experiments to see if The Cloud makes sense for your clients.

That's just a network boot.  It makes all sorts of sense, and you can do it with any operating system.

The IT staff separates all the workstations (or routers or whatever, anything that there can be multiples of with the same configuration) into groups.  Usually based on what it is:  CPU, memory, maybe what batch it was bought in.  They build an image for that, test it and then tell the dhcp server that computers with this list of MAC addresses should boot from such-and-such image.

This way you know what updates are applied on each box, you know it works, and everything is consistent.  Again, your approach is to keep your IT staff from hopping from desk to desk applying updates, and keep the person who normally sits in that chair--making you money--sitting in that chair making you money.

It also makes it so whatever virus they got yesterday is no longer so much of a problem today.

---

### Post by ov10fac on 2014-01-19
Ok,  that's a thin client and I've used it many times over the years.  Not too different from the old "Mainframe" environment of many years ago.  Thank you.

I guess my bottom line question would be, other than sharing files, what else can a cloud environment be used for?  I'm looking at uses for clients who are mobile bu need access to programs running on the home network server.  VPN is too slow, and the applications are not suitable for a Terminal Services server.

---

### Post by 1clue on 2014-01-19
Anything you might need a server for.  What apps do you use?

You can't use the cloud as a workstation, and you don't use "the cloud" directly for anything.  The cloud is the group of physical servers which contains the servers (usually virtual servers) you put there.

You can use a public cloud like Linode.com, or a private cloud that you set up in your office IT room, that you manage yourself.

"cloud storage" is the idea of having a file server "out there" somewhere, all that is is file storage.

There's something I don't understand about your question.  I thought I had answered everything in my posts above.  What sort of things do you need to do with your mobile clients?

---

