---
title: "[SOLVED] Does Virtualbox require you to run a command to fix it after every kernel up"
date: 2008-07-12
forum: Virtualisation
---

### Post by diablo75 on 2008-07-12
I recently switched from VMware Server to Virtualbox (not the OSE version).  My experience with it thus far (besides editing 3 config files to get USB to work) has been pretty pleasant.  My biggest complaint with VMware Server (albeit, a very good virtual machine management software) was that you would have to either re-install it with an any-any patch, or run a command in terminal that would effectively do what that patch does after installing a linux kernel update.  Now, for me, that's not a big deal.  But if I were to suggest this software to people who are not as technically savvy, and they discover that certain updates require them to dive into that foreboding terminal window, it's not a pretty picture.

So I tried Virtualbox and liked it.  And I've been through a couple kernel updates and have not had to do a single thing about it as far as Virtualbox is concerned.  It just continues to work.... at least that's my experience thus far, and I've only been using it for about 2 months....

I decided to write a blog about it, pretty much slamming VMware for that python script you have to run every time a kernel update comes down and breaks it, and my not noticing this occurring with Virtualbox.  But one person has placed a comment in reply (I've not approved it just yet) which states the following:

> Sorry mate, you&#8217;re perspective is skewed.

VBox requires you to run a script after every kernel upgrade, just like VMWare.

VMWare&#8217;s time-wasting (as you called it) script does prompt you for anything if you throw on a &#8216;-default&#8217; switch to the command, ie:
$ vmware-config.pl -default

you just spent 3 pages explaining to vbox users how to setup in vbox what vmware does for you automatically.

I recommend you try to get some journalistic research done before you start throwing big opinions around.

Now...  How much journalistic research must I do?  I have my own experience to go off of, as well as at least one other client of mine who depends on a virtual machine to keep things going for him.  And I know VMware also requires you to edit config files to get USB working as well (It's not so "automatic" as he says it is)... I've not heard of a script that needs to be run after a kernel update for Virtualbox, though after googling it, it seems to be the case for a few people (though more so back when 7.04 was the latest version of Ubuntu)...

Anyway, I'm looking for feedback about this comment with the goal of being objective about it.  I'll be happy to write a second follow up blog correcting myself if that's the case.  But in my experience thus far, Virtualbox seems to be the more user friendly, beginner-oriented solution for those who need a virtual machine of some kind and would like to reduce long-term downtime.  But I could be wrong...

---

### Post by sonicb00m on 2008-07-12
When a new kernel comes up you must run the script that VBox provides to make it work with that kernel. For minor kernel updates no script is necessary but for major updates, i.e. 2.6.23 to 2.6.24, you will have to run the script to make it work for that kernal else VBox will not run.

I think it's 

/etc/init.d/vboxdrv setup

This is not optional and it's not for "some users".

I havent used VMware for a long time since it was always much harder to get running and VBox just worked without having to do anything. I can't comment on VMware now because Ive never used it since. VBox does all i need, it's free and it's fast and the seamless windows is awesome.

---

### Post by diablo75 on 2008-07-12
Well I stand corrected then!  :)

---

### Post by MrPage on 2008-07-12
Right,

So it's me, the guy quoted at the top.
I probably came across more hard on you than I should have.

I just thought it was contradictory to say: 'VBox is easy!  Just follow these whatever number of steps that no new user really has any business doing!'

Let me explain my perspective:
I've been using VirtualBox and VMWare Server for over a year now.
They're both awesome and they're both a giant pain in the butt at the same time.
I run both in a 32 bit and a 64 bit environment.
Both require kernel module recompilation on kernel upgrade.
VBox is faster than VMWare server.
VMware Server is more feature rich than VBox.
VBox is capable of alot more if you're willing to frig with it...alot
VMWare Server's config.pl script (if you understand it's questions) will configure all of your defaults, such that when you run it the next time, you can toss a '-default' on then end and you don't have to answer any of the questions that you had to the first time.

My Opinions:
I've used both in a production environment and prefer VMWare since you aren't obligated to leave the window open while the virtual machine is running.
Vbox is a toy
VMWare is a tool

---

### Post by diablo75 on 2008-07-12
That sounds like a more than fair comparison between the two.  Though I still think that with as easy and quick as the recompile for Virtualbox goes, it just seems like the better solution for beginners.  Anyway, to each their own.  :)

---

### Post by sonicb00m on 2008-07-13
> **MrPage said:**
> 
Vbox is a toy
VMWare is a tool

I can't see how you can say it's a toy. It does the job some people need it to do perfectly. I.e. Run windows or linux environments from the comfort of within your current operating system.

I use it to run Visual Studio at the office, which is the only Windows app I require. Hardly the stuff of toys :lolflag:

---

### Post by MrPage on 2008-07-14
In VMWare, you can set a virtual machine to power on when the system boots up.
So let's say your data center loses power for a moment (and your UPS fails too, for argument's sake), you've cunningly set your servers to power up on power connect at the BIOS level.
When power is restored to the data center and all of you servers get power - they all boot up automatically.
If you've chosen VMWare as your platform and set your virtual machines to power on with boot up, all of your VMs will also power on in the data center.
So without the sysadmin even being present, all of your servers (physical and virtual) power on and start there jobs - provided they don't require log on

Systems that require a log on, and run in an application level will require human intervention.  VirtualBox, VMWare Workstation, VMWare Player all require a user to start them.

VMWare Server runs at a service level and doesn't require human intervention to run.  You don't even have to have the window open and all of your virtual machines are running.

As a SysAdmin, this is the path I chose. The above is what I've built at work.  It's highly automated.  I use it as a tool.

That said, having to run a vm in a window on your desktop using Player or VBox that you had to start manually sort of seems Mickey Mouse in comparison.  It requires that your hands be on it for it to work. That's why I called it a toy.  It's something to look at, play with and manually manage.

---

### Post by markba on 2008-10-10
> **MrPage said:**
> In VMWare, you can set a virtual machine to power on when the system boots up.

You are right, saying VBox sessions do not autostart on boot. But, I'm working with VBoxTool (see signature) to get this done.

I'm just curious, but are those sessions suspended automatically when the system is getting a controlled 'down' command?

Note. VBox has indeed a autodown command, comprised in /etc/init.d/vboxdrv, but it does not seem to work relaiable. I have to sort this out.

---

