---
title: "Workstation Virtualisation"
date: 2009-05-12
forum: Virtualisation
---

### Post by onno-itmaze on 2009-05-12
I'm a long-time software developer. I have a ThinkPad R52 from August 2005, the last of the IBM's. I'm in need of new hardware. Since upgrading from Ubuntu 7.10 I've been unable to properly virtualize anything (VMware went away). I want to keep running Ubuntu but am fed up with fixing hardware issues. A suggestion made to me was to buy a PowerBook Pro and virtualize my desktop.

The idea is to run a stock standard OS X PowerBook and then run my normal Ubuntu Desktop as a virtual machine. Since I'm also writing software and testing all manner of strange configurations, I can then also simply virtualize all the other things, such as Ubuntu Server installations, various pre-release versions of Ubuntu, specific client configurations, etc.

Most articles I read talk about running Windows on OS X, and I'm really not interested in that - other than to export my accounting data out of MYOB.

My personal experience of VirtualBox under Ubuntu is less than stellar. A virtual machine that crashes *ever* is not an example of a tool that I want to run in production. That's akin to a hardware failure and a cause for the return of said hardware.

I need to be able to run this workstation with an external monitor, have a full monitor view of my workstation, run other tools on the other monitor. There will be times that I expect to run my virtual machine across both monitors.

I expect that the OS X side of things takes care of wired and wireless networking, battery management, sound and bluetooth connectivity, but I don't want to run OS X applications, other than the virtualization tool of my choice. I might even launch terminal once or twice :)

Am I opening up a whole can of worms trying this, or are there people who have gone down this path and come out the other end with a better understanding of what is what?

I should note that there was an initial suggestion that I run Ubuntu natively on the PowerBook hardware, but then I'm back to where I started, dealing with crappy hardware issues, video drivers, wifi chip-sets, sleep and battery issues, screen resolution, dvd drives, etc.

I'm not interested in migrating to OS X, I have more than enough work just keeping abreast of what is happening within Ubuntu and Ubuntu-server.

While my CPU demands are not going to be significant - I don't compile much, I'm also not going to be running a high-volume web-server or a database. I cannot stand editors that take 30 seconds to load or many minutes to search for files, so there is an expectation that disk i/o is snappy and that I'm going to be able to stay with the same virtualisation tool for some time.

The actual tools I use on a daily basis are:
Thunderbird, Firefox, Eclipse, bzr, svn, cvs, mysql, apache, ssh, grep, find

Things I expect to work are:
sound, networking, dvd burner, external usb devices


Any comments, suggestions, recommended reading materials or hardware that I can trial this on?

---

### Post by dmizer on 2009-05-24
Moved to the virtualization forum.

---

### Post by onno-itmaze on 2009-06-01
Is my question so off the wall that no-one dares to respond, or do I need to elaborate on what I wrote?

---

### Post by dmizer on 2009-06-01
Well, I still use VMware, and would suggest it as It should do everything you want and be stable, as long as you use VMware server 1.x (the 2.x implementation leaves a lot lacking).

> **onno-itmaze said:**
> The actual tools I use on a daily basis are:
Thunderbird, Firefox, Eclipse, bzr, svn, cvs, mysql, apache, ssh, grep, find
These should be no problem regardless of VM software choice.

> **onno-itmaze said:**
> Things I expect to work are:
sound, networking, dvd burner, external usb devices
These will be heavily dependent on your virtual software choice, particularly USB.

Since your base platform is supposed to be OSX, perhaps this question is better suited to a Mac support forum? Not saying that you can't get support here, just a suggestion.

---

### Post by onno-itmaze on 2009-06-01
I suppose the underlying question is: Has anyone run their main workstation as a virtual machine?

The fact that I'm planning to use OS X as the host is almost irrelevant to my mind.

---

### Post by dmizer on 2009-06-01
Yes, all my PIII laptops connect via wireless to my quad-core vmware host. I use one virtual machine for all clients. This gives me the advantage of (no matter what computer I'm on) centralized settings, plus I get to take advantage of my gigabit network speeds and my FTTH connection speeds. The only downside is that the sound isn't piped to the client, so I use a bluetooth headset and that's not really ideal.

I haven't found a need, but it's also certainly possible to have two virtual guests displayed on two monitors.

Kind of depends on how much effort you want to put into the project really.

---

### Post by onno-itmaze on 2009-06-02
So are there other non-obvious pitfalls I might run headlong into?

One punter pointed out that I'll never have the bare-metal speed that a native installation would provide, but my counter to that is that I'll also never have the bare-metal experience of having to find hardware support for something that was working yesterday.

Sound isn't a deal breaker, but it's good to know.

I'm getting mixed reports about the need to run "guest tools" in whichever environment I end up using. My understanding is that it's useful for "integration" between the host and the guest, things like file-sharing, copy/paste, etc. -- but I specifically don't want any such integration. I'm really not intending to have any permanent data of any kind stored under my host OS.

If I could run a bare metal server install on my laptop, I probably would, so there are no cpu-cycles being spent on running graphics displays that I'll never use.

For me the whole point of this is to disconnect my desktop environment from the hardware it's running on, so I can get on with what I really do for a living -- fix problems for my clients.

If my OS of choice - Ubuntu - had 100% hardware support then I might reconsider this stance, but in running Linux for 10 years, I've yet to find that. Of course abstracting my desktop I also intend to abstract storage by running a tiny (also virtual) Ubuntu LTS server which provides file/print/imap/database storage to my desktop.

So, am I mad?

---

### Post by dmizer on 2009-06-03
No, you're not mad (I assume you mean "not sane"). Yes, you're liable to run into other unforseen pitfalls, just as you would with ANY system under ANY configuration (never forget the venerable [Mr. Murphy](http://www.murphys-laws.com/murphy/murphy-laws.html)).

Disk access speed will be reduced, and possibly network speed, though neither of these issues has made my setup useless or unbearable.

I've been considering a bare-metal hypervisor for a long time, but still not sure if I'm ready to make that leap or not. Mostly because I'm doing research on how to maintain performance but host a multi-terebyte file server. Also, there's hardware limitations/requirements involved in bare-metal hypervisors as well.

I highly suggest running guest tools. There's no reason not to, as they cost no overhead while making life significantly easier, including (but not limited to) accurate guest timekeeping.

With a virtual machine, there's absolutely zero reason not to try what you want to do. VMware-server can be installed on Windows or Linux (I don't see a VMware-server download for Mac), install an Ubuntu guest and try it. If it works, you can copy that guest over to any machine you like. If it doesn't work the way you need, then you've lost nothing other than the time it took to install the guest.

If it doesn't work, then stick with the [LTS](https://wiki.ubuntu.com/LTS) releases like Hardy. That way, you only have to deal with potentially broken hardware drivers every 3 years or so. Sure, by the time that 3 years is up, your software base will be a bit out of date, but still perfectly useful and stable. If you need current tools, use an LTS release as your base, and run the bleeding edge release in a virtual machine.

Edit:
I hinted at it before, but I wanted to make an explicit point this time. Your biggest hardware problem with a virtual machine will likely be USB peripherals like printers, scanners, and such. Though ... some of those problems can be alleviated by sharing them over the network from the guest. Something like a USB thumbdrive connected to the host may or may not be available in the guest (for example).

---

### Post by onno-itmaze on 2009-11-23
I've now been running a virtual environment since about the 17th of June 2009. In that time I suffered a hardware failure, which was resolved by copying the Virtual Machines folder to an external drive, replacing the hardware, copying the folder back and being back in service within a few hours (the time it took to copy the data out and back) In fact, I ran from an external drive while replacement hardware was being shipped - so I didn't loose a continuous chunk of time.

I also suffered from two VMware crashes which took a week of data both times. That's more data that I've lost in that fortnight than in the previous 30 years!

We've not yet gotten to the bottom of the cause, but backups are now twice daily as a result - using a Sparsebundle Drive, Time Machine, identically named external drives under the host OS, OSX 10.5.8

Apart from the data loss, which was traumatic, my experience with a virtualised desktop has been mainly uneventful. Things I hadn't counted on include strange OSX keyboard mappings (mostly since there are no Home/End/PgUp/PgDn keys on a MacBook Pro.

The only word of caution, which I think I've now resolved is that a snapshot under VMware doesn't work as you'd expect, that is, it's not a snapshot as such, it's a point to which you can revert, but all the changes are stored with that snapshot, so if you have multiple snapshots, it all goes to pot, since they are all being updated. After clearing out all snapshots and making an automatic snapshot every hour and only storing 1 (something which you can automate in VMware Fusion 2.0.6) the usability issue that resulted from this update - you couldn't use the VM for up to 90 seconds during the automatic snapshot has now been brought back to around 8 seconds every hour, which I use to remember that it makes a backup every hour.

Speed wise the whole thing has been a non-event, Compatibility wise, it's been fine also. From a usability perspective, it's everything I hoped it would be. Creating a new virtual machine is trivial and separating out client development environments or creating an instance of a client installation makes life soooo much easier.

I have a little user data stored under the host OS - mainly due to the crash, but I'm working on getting that all back to virtual storage.

I played with Unity View for about 2 minutes under Ubuntu. It hides the Ubuntu desktop and displays Ubuntu windows within OSX. Minimised applications show up in the dock and if you have multiple monitors, the Ubuntu menubar shows up on one window, the OSX menubar on the other. It's very freaky and while it looked cool, I found myself having issues with keyboard shortcuts (under Ubuntu Copy is Control-C, under OSX it's Command-C. Wile you can map Control and Command to eachother under VMware Fusion, it still doesn't quite work as you expect, since Command-Q is still Quit - for Fusion, not the application that's running - or perhaps it is, depending on where your mouse pointer is at the time --- not good.

---

### Post by memilanuk on 2009-11-23
Thanks for your perserverance on this matter, and for posting back on it.  

I have an older Sony Vaio laptop that I'd picked up for use playing around in Linux; sadly I've about came to the conclusion that between various hardware issues it may be not worth the continued efforts to get/keep the thing running.  So... I was starting to think about other options, and your thread reminded me that I *do* have Virtualbox installed on my Intel-powered MacBook (circa 2005 or 2006), with a VDI of Backtrack 4 installed.  I believe I just may pop in a Ubuntu install CD and give it a go!

Thanks,

Monte

---

