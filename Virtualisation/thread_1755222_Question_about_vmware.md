---
title: "Question about vmware"
date: 2011-05-10
forum: Virtualisation
---

### Post by ClientAlive on 2011-05-10
Hi,

I've been looking into vmware and was wondering. If I were to install vmware on my system and I installed more than one o/s into it, could I set it up to use all the available system resources for each of those operating systems? I mean, If I were only ever running one at a time then it seems plausible that this would be possible - right?

For instance:

Say I have 1 gig of memory and whatever my hard drive space is (say 40 gig). And say I install two operating systems in it.

Rather than divide that by two in their configuration can I not just give all the resources left to both operating systems. That way whichever one I'm running at the time gets it all?

As a side note, perhaps the resources that vmware itself uses must be taken into account as well. I'm not sure if vmware does this calculation for you or not, but I'm sure it is a factor.

Can anyone offer an answer for this?

Thanks in advance.

---

### Post by garvinrick4 on 2011-05-10
What ever Ram and processor % it takes to run the host and the quest is used. You can
have more than one OS in VMware but minimum used is the host and the open quest OS
The host is always running. You set the amount of Ram to be used in quest.

---

### Post by ClientAlive on 2011-05-11
> **garvinrick4 said:**
> What ever Ram and processor % it takes to run the host and the quest is used. You can
have more than one OS in VMware but minimum used is the host and the open quest OS
The host is always running. You set the amount of Ram to be used in quest.


Well here's where I'm confused then. I thought that what it means to be a 'bare metal' vm is that it 'is' the o/s (or takes the place of it at least). In other words, when you install vmware it would be like doing a fresh install of any other regular o/s. Then you put the o/s you want into it.

Virtual Box (another virtual machine) is not like that. With it you have your host o/s on the machine, virtual box kinda in the middle, than whatever you install into virtual box.

I thought that was what made vmware different. That it is 'bare metal'. I watched a couple videos on you tube about vmware vmxi but it looks like it's designed for servers. Now i'm really confused.

---

### Post by garvinrick4 on 2011-05-11
You download VMware Player and then VMware tools. If it is lets say Ubuntu VMware tools
is a .deb package that installs rather easily from a dropdown menu I believe it was. In fedora 
with rpm's for VMware tools you download a tarball and extract and has a perl script that you run 
and it is a well done script that compiles from source for you I believe and installs. Either OS worked well for 
me and was an easy install. Running my intel based machine with no restricted drivers.
Home network using a Windows Workgroup works well can access all shares from other machines 
on network and printer in Ubuntu. Imagine as a Virtual install is a very nice server install but have not 
tried just the install with GUI as an experiment and turned out very well.
#found a link quickly for reference.
[http://reformedmusings.wordpress.com/2008/08/15/what-does-vmware-tools-do/](http://reformedmusings.wordpress.com/2008/08/15/what-does-vmware-tools-do/)

** Even though I have a dual core it only recognizes one processor and uses 32 bit. Has a list of processors that it will recognize as dual.

---

### Post by Dedoimedo on 2011-05-12
You can overcommit. But remember to run one instance at a time if you do so!

If you have 1gb ram you want to give to your virtual machines, you can split it any way you want as long as no more than 1gb is in use at any given time.

Disk wise, if you do not preallocate disk space, you can have disks as large as you want, but if you fill then with data, the physical disk space will be a limitation. You can save space if you use a single swap file or a single data disk that can be accessed by different virtual machines. However, beware corruptions. For example, sharing swap/data and suspending virtul machines to disk then powering on another instance. You could end up with data overwrites, crashes, etc.

Dedoimedo

---

### Post by ClientAlive on 2011-05-12
Right on. I'm pretty new to this whole virtual machine thing so I guess when I started this thread I had a couple different questions floating around in my head. Add to that, that I have this idea of something I might be able to do with it; and, well, you get the picture.

Sorry if I've kinda jumped around.


> **Dedoimedo said:**
> You can overcommit. But remember to run one instance at a time if you do so!

If you have 1gb ram you want to give to your virtual machines, you can split it any way you want as long as no more than 1gb is in use at any given time.

Disk wise, if you do not preallocate disk space, you can have disks as large as you want, but if you fill then with data, the physical disk space will be a limitation. You can save space if you use a single swap file or a single data disk that can be accessed by different virtual machines. However, beware corruptions. For example, sharing swap/data and suspending virtul machines to disk then powering on another instance. You could end up with data overwrites, crashes, etc.

Dedoimedo

Thanks Dedoimedo.


> **garvinrick4 said:**
> You download VMware Player and then VMware tools. If it is lets say Ubuntu VMware tools
is a .deb package that installs rather easily from a dropdown menu I believe it was. In fedora 
with rpm's for VMware tools you download a tarball and extract and has a perl script that you run 
and it is a well done script that compiles from source for you I believe and installs. Either OS worked well for 
me and was an easy install. Running my intel based machine with no restricted drivers.
Home network using a Windows Workgroup works well can access all shares from other machines 
on network and printer in Ubuntu. Imagine as a Virtual install is a very nice server install but have not 
tried just the install with GUI as an experiment and turned out very well.
#found a link quickly for reference.
[http://reformedmusings.wordpress.com/2008/08/15/what-does-vmware-tools-do/](http://reformedmusings.wordpress.com/2008/08/15/what-does-vmware-tools-do/)

** Even though I have a dual core it only recognizes one processor and uses 32 bit. Has a list of processors that it will recognize as dual.

Thanks gavinrick. I think. It's just that I have an unanswered question that has been confusing me. It's something foundational so then when I read that I find myself still confused. I need to get this other thing sorted out somehow before I can understand the finer details - - -

What it is that I'm unsure about is whether there are a couple different kinds of virtual machines out there.

From the few things I have read I gather that there may be at least two basic types. One type goes by the designation "bare metal;" and, I thought, meant it did not require a host operating system to be installed on the machine. That with that type it took the place of the operating system.

The other type, I don't remember what they call it, seems to be a type where a host o/s is required and the virtual machine is installed on top of it. Oracle VM Virtual Box is of this latter type (the only reason I know this is because it is the one virtual machine I have ever used so far).

Here's the problem:

While I had believe that VMware was of the first type (the 'bare metal' type); when I visit their web site, look at tutorial, or find videos on you tube all I see a this convoluted mass of different products. I have seen videos on you tube that show someone installing VMware (a product called esxi) and appears to be being insalled right onto the computer (no host o/s). The video doesn't exactly say though so there's no way to tell.

To add to the confusion, I am aware that VMware is primarily for companies (or so it seems) and that a lot of their products have to do with servers. I'm on a personal lap top. I don't own a company or run a server.

So the rock bottom of it is this:

Is there some VMware product that actually takes the place of your operating system, or am I mistaken about what 'bare metal' means? If there is, what is it called? Is it free? If I went through with something like that, what could I expect to happen to my poor, poor computer? (That last part is said jokingly but the question is real).

It isn't that I'm lazy or unwilling to do the research - it's that the information about VMware's products is so convoluted and disconnected I fear I may spend a lifetime trying to figure it out. It's at that point that I just ask someone.

Host o/s needed - or - takes the place of the o/s?

:confused:

---

### Post by ClientAlive on 2011-05-18
> **ClientAlive said:**
> Well here's where I'm confused then. I thought that what it means to be a 'bare metal' vm is that it 'is' the o/s (or takes the place of it at least). In other words, when you install vmware it would be like doing a fresh install of any other regular o/s. Then you put the o/s you want into it.

Virtual Box (another virtual machine) is not like that. With it you have your host o/s on the machine, virtual box kinda in the middle, than whatever you install into virtual box.

I thought that was what made vmware different. That it is 'bare metal'. I watched a couple videos on you tube about vmware vmxi but it looks like it's designed for servers. Now i'm really confused.


So I guess no one knows the answer to that?

I've been looking around but haven't found my answer yet.

If anyone knows the answer I'd sure appreciate it.

Thanks

---

### Post by garvinrick4 on 2011-05-18
> It isn't that I'm lazy or unwilling to do the research - it's that the  information about VMware's products is so convoluted and disconnected I  fear I may spend a lifetime trying to figure it out. It's at that point  that I just ask someone. You want VMware player and it is free. Use Ubuntu it is and easy install and very easy to
install VMware tools just hit a button that simple. Can run both at once or either at a time
host and quest. Remember host hast to be booted up and you run quest inside. It is very nice really. 
I have one install of VMware Ubuntu 11.04 32 bit classic Ubuntu running inside a Windows 7 host. 
Printer works, network works, it has all its own drivers it just works. Takes
whole screen if you want. (fedora did not) defaults at 500 meg Ram and a swap also I believe.
Give it a whirl. What is the worst you have to uninstall.

---

### Post by garvinrick4 on 2011-05-18
> I thought that was what made vmware different. That it is 'bare metal'. I  watched a couple videos on you tube about vmware vmxi but it looks like  it's designed for servers. Now i'm really confused.
They sell all kinds of server systems all run inside a host. That is what virtual is. It has the host
fooled that it is not even there. Just takes up a slice of the drive and the virtual thinks it is standalone but not. They are in business to make money it is the VMplayer that is no cost.

---

### Post by ClientAlive on 2011-05-19
> **garvinrick4 said:**
> They sell all kinds of server systems all run inside a host. That is what virtual is. It has the host
fooled that it is not even there. Just takes up a slice of the drive and the virtual thinks it is standalone but not. They are in business to make money it is the VMplayer that is no cost.



Ok, I hear what you're saying. Thanks gavinrick4. But what is this talking about then?

> 
System virtual machines (sometimes called hardware virtual machines) allow the sharing of the underlying physical machine resources between different virtual machines, each running its own operating system. The software layer providing the virtualization is called a virtual machine monitor or hypervisor. A hypervisor can run on bare hardware (Type 1 or native VM) or on top of an operating system (Type 2 or hosted VM).


That's a quote from a wikipedia article on virtual machines. The article can be found here: [http://en.wikipedia.org/wiki/Virtual_machine](http://en.wikipedia.org/wiki/Virtual_machine)

Do you notice the "type 1" that they mention near the end of the paragraph?

> 
A hypervisor can run on **bare hardware** (Type 1 or native VM) . . .


That sounds to me like a virtual machine that does not rely on a host operating system but is installed directly on the bare computer/ hardware.

Am I mistaken about what that is saying?

---

### Post by fjgaude on 2011-05-19
Running **vmware** as the OS means you are to use their ESX. A cut-down version of it is free I think, but the full-up is for money.

So what you are asking, can the host be the software that creates the VMs and then runs them. The answer is: Yes! But it is not free.

VMware Player does a wonderful job for many of us, and it is well supported and free and works out-of-the-box for all late versions of Ubuntu. But, and there aways seems to be a but, your CPU should have the ability to efficiently handle virtuals.

---

### Post by ClientAlive on 2011-05-19
> **fjgaude said:**
> Running **vmware** as the OS means you are to use their ESX. A cut-down version of it is free I think, but the full-up is for money.

So what you are asking, can the host be the software that creates the VMs and then runs them. The answer is: Yes! But it is not free.

VMware Player does a wonderful job for many of us, and it is well supported and free and works out-of-the-box for all late versions of Ubuntu. But, and there aways seems to be a but, your CPU should have the ability to efficiently handle virtuals.


Wow, totally awesome! Thank you. I tried to find this information online at first but the information seemed always to be either too technical for me to understand, didn't really address my questions, or (in the case of VMware's site) so convoluted and cluttered with a million things - that I couldn't make heads nor tails of it.

That's what I was trying to separate out - what you addressed here. Not only was I asking 'what is or which is the free version' but also 'is there one that is a "type 1" (I just learned that term so it still feels funny to use it). Now I understand. I imagine that if it weren't too expensive and it was cool enough that I wanted to mess around with it, I would pay for the non free version. Then again, VMware must have a dozen different paid products so we're back to convoluted again.

This is a great starting point for me. I've been using Virtual Box a little bit and will probably check out he free version of VMware at some point. We'll see what happens from there.

Have a great weekend man. Be blessed.

Sincerely,
Jake

---

