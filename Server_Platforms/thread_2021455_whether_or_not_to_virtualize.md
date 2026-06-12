---
title: "whether or not to virtualize?"
date: 2012-07-09
forum: Server Platforms
---

### Post by rcunningham72 on 2012-07-09
Hi all,

I'm pretty new to "virtualization" in general, and I've known about Linux (and that we use it) for about a week now, so please bear with me if I make some mistakes, I shall try and be as clear as I can.

Essentially we are a small event promotion company that uses four PCs (currently 3*mac mini and 1*Dell XPS) that all connect to each other through a HP server which apparently runs Linux. As a small team of four we use these adjacent PCs both as independent work stations and collaboratively on larger projects, using the tower for tasks such as rendering that the Mac Mini's can't handle.

With CS6 out now, and Mountain Lion plus Windows 8 on the way we need to upgrade our hardware, and have been discussing it with our IT Company. I had planned to update the mini's and get a Mac Pro to replace the Dell and carry on as we have. 

However, our IT guy has said we can replace all four computers with one "EVGA" computer (that I can't find on the internet - just bits of one) that would "virtualize" our desktops, and allow any one of us to do intensive tasks like rendering as required, not having to "seat swap" to use the powerful one. This sounds very alien to me, and I'm not sure if we're being lead up a country path on this one.

I spoke to the guy in the Apple store who said that you can't virtualize Lion or Mountain Lion, and that we'd need a Mac Pro plus Mac Mini's to act as "clients" to do this. As I understand the proposed new computer would run Linux and virtualize Mac OS X, and this is the most popular Linux, I figured this was the best place to find out more information about this?

I think I've managed to pick up the basics of virtualization and have been able to follow this guide to virtualizing Ubuntu on my home pc:
[http://www.wikihow.com/Install-Ubuntu-on-VirtualBox](http://www.wikihow.com/Install-Ubuntu-on-VirtualBox)

Would anyone be able to clear things up a bit for me? I'm not very tech-y, but I feel I'd like to know a bit more about this.

---

### Post by CharlesA on 2012-07-09
The IT guy is probably talking about running something like Citrix, where the applications run off a central server and are "pushed" to the clients.

It's not the same as VirtualBox and tbh, I would **not** use VirtualBox in an enterprise environment.

Also, if it is going to be a box running as a renderfarm, using CUDA with multiple video cards can help reduce the time it takes to render, which is probably what they were referring to by using EVGA cards.

---

### Post by rcunningham72 on 2012-07-09
Thank you for your quick reply CharlesA, That sounds a lot more like what i was first told.

I've been scanning wikipedia, it seems a bit clearer! So it's probably best if I describe what I think to see if I've got it down?

So it sounds to me that there are two options; the SaaS option, where this new computer hosts our software such as CS6, etc. And smaller computers (a bit like our current Mac Minis) access that program through the network, but it's actually the new computer doing the work?

Or the other option is that the proposed new computer actually runs a "hypervisor" that allows for guest operating systems on top of a linux host .. and that you run multiple systems at the same time? This confused me a bit; does it mean you all work around one computer with 4 monitors, mice, keyboards and tablets, or does it send those operating systems to clients like the SaaS does with programs?

Also if it's not rude to ask, how does running Linux in business tend to go? I read that a large proportion of servers actually run Linux and related operating systems, but obviously there's no central company to call; you're kind of dependent on the IT company that sets it up?

Sorry for the excess questions, our IT guy comes in on the second Thursday of the month to check our stuff and I just wanted to be a bit better prepared; I trust the guy completely with our business, but I don't always understand his explanations. I know he wants us get some kind of server to streamline what he calls our "mess" of hardware, and his eyes lit up when I mentioned we've been thinking of updating the lot.

---

### Post by spynappels on 2012-07-09
> **rcunningham72 said:**
> Also if it's not rude to ask, how does running Linux in business tend to go? I read that a large proportion of servers actually run Linux and related operating systems, but obviously there's no central company to call; you're kind of dependent on the IT company that sets it up?

Linux servers run many different types of application, as a stable and secure OS, it is the OS of choice in many industries including financial and telecoms (I work in telecoms and we are transitioning to RHEL).

As for support, there are several large companies which support specific distros, so Red Hat support RHEL (Red Hat Enterprise Linux) and Canonical support Ubuntu Server. Local support is cheaper, but obviously does not scale well.

---

### Post by CharlesA on 2012-07-09
> **rcunningham72 said:**
> 
So it sounds to me that there are two options; the SaaS option, where this new computer hosts our software such as CS6, etc. And smaller computers (a bit like our current Mac Minis) access that program through the network, but it's actually the new computer doing the work?

Yes, that is how Citrix works.

> Or the other option is that the proposed new computer actually runs a "hypervisor" that allows for guest operating systems on top of a linux host .. and that you run multiple systems at the same time? This confused me a bit; does it mean you all work around one computer with 4 monitors, mice, keyboards and tablets, or does it send those operating systems to clients like the SaaS does with programs?

If you implement it that way, each virtual machine would by its own machine. Running a hypervisor works best for servers, or things that are not graphically intensive. I wouldn't want to run Photoshop or Blender or Maya off a VM.

If you have a machine hosting virtual machines, you would need to be able to connect to each virtualized machine from your own machine. There would be no box with 4 monitors and whatnot hooked up.

> Also if it's not rude to ask, how does running Linux in business tend to go? I read that a large proportion of servers actually run Linux and related operating systems, but obviously there's no central company to call; you're kind of dependent on the IT company that sets it up?

It depends on the business. At the place I work, we use a *nix box as a backup file server. 90% of the machines we run at work are Windows boxes because that is what the IT guy knows. Give him a *nix box and he looks like a deer in the headlights.

> Sorry for the excess questions, our IT guy comes in on the second Thursday of the month to check our stuff and I just wanted to be a bit better prepared; I trust the guy completely with our business, but I don't always understand his explanations. I know he wants us get some kind of server to streamline what he calls our "mess" of hardware, and his eyes lit up when I mentioned we've been thinking of updating the lot.

Ask them how they intend to implement whatever solution they want to use. Then go from there.

---

### Post by spynappels on 2012-07-09
> **CharlesA said:**
> Yes, that is how Citrix works.


If this is the way it's going, I doubt the server will be running Linux, especially if it's likely to be serving Adobe products.

I could be wrong though, I often am...

---

### Post by CharlesA on 2012-07-09
> **spynappels said:**
> If this is the way it's going, I doubt the server will be running Linux, especially if it's likely to be serving Adobe products.

I could be wrong though, I often am...
That's true. Unless they were using Crossover or Wine, but if you are going to be using Citrix, why bother with that? Just run Windows.

---

