---
title: "I need a web based KVM/LXC frontend...need advice"
date: 2015-04-19
forum: Virtualisation
---

### Post by pepsifx357 on 2015-04-19
I'm have a desktop that's using KVM and want to get into LXC, but I'm lazy....aren't we all....and want a nice web based front end like proxmox.  I've used Proxmox and I like it a lot, but I have a custom kernel and any installation of proxmox is going to replace that, so I'm looking for other options.

Right now I'm using Virt-Manager, which is fine, It works and it's really easy to use, but I also have another server set up at another location that only has Windows desktops to manage from. That's a problem.

I've tried OpenNode and it was a bit immature and needs some time to be usable.  Then I tried OpenNebula.  I felt that OpenNebula had a very complicated way of doing things that I really didn't like.  I didn't like that I was forced to use SSH with keys and couldn't really use the VNC interface like I wanted.  I also couldn't figure out how to create my own templates, or add data stores where I needed them.  It was just too complicated.  I also attempted to install OpenStack.  Holy $###, I got to the part where you install MAAS and create nodes and then forgot what it was that I was trying to accomplish in the first place.  There are just too many components that need setting up and virtual machines to node and get working.  I never got it to fully work and I never understood what juju had to do with OpenStack, I just need an easy to use interface for virtual machine control, not a full blown cloud with MAAS, although that is cool.  I wish there was a way to just install OpenStack by itself to act as a front end for KVM.

Anybody have any suggestions?

---

### Post by TheFu on 2015-04-20
> Right now I'm using Virt-Manager, which is fine, It works and it's really easy to use, but I also have another server set up at another location that only has Windows desktops to manage from. That's a problem.
If you have ssh access to the remote location, you can use virt-manager with key-based auth.  I wouldn't use the built-in VNC as a console - I'd use ssh for all management work.  virt-manager works find for creating, starting, stopping VMs from anywhere in the world.  If you really must have a remote desktop, load x2go-server on the remote machine and use that for remote desktop access. It feels 2-3x more efficient than VNC/RDP and NX includes ssh tunneling in the protocol. No added port to open - if you have ssh working already, both virt-manager and x2go use that same port and authentication.

BTW, if you aren't using ssh-keys for authentication, expect to be hacked. Passwords are a flawed remote access method, IMHO.  Whenever you setup ssh, also setup fail2ban or denyhosts or at least a throttling iptables ruleset to block brute force attacks.  Why wouldn't you use ssh-keys for authentication?  It hardly ever happens that something MORE secure is actually MORE CONVENIENT to use too.  Passwords are so, so, so, 1992.

As to web interfaces - I think proxmox really is the only answer for easy setup. Redhat as something, but it is enterprisy - bloated - with lots of java server crap.  If you get over the ssh-key stuff, you'll be much happier with virt-manager from anywhere in the world ... as long as you don't use it as an interface for remote desktop.

---

### Post by pepsifx357 on 2015-04-20
I agree with you on Virt-Manager, but the problem is, the remote system is at a private residence on an ever changing IP address, along with a bad DSL connection.  I don't have a laptop or anything with Virt-Manager when I'm over there to administer it.  I tried setting up no-ip on the server, which is a Fedora 21 server, but I couldn't get it to work.   The situation is kinda complicated, but if I have to do something, I have to email the owner and have them send me their IP address every time so I can use Virt-Manager.  There are plans in the works to get something like ClearOS on it, which would solve a few problems such as the IP, but that's going to take some time.

---

### Post by TheFu on 2015-04-20
Do you expect a web interface to fix any of those issues?  If  ssh doesn't work, nothing else will work any better.
[http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh](http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh)

Many home routers have built-in support for no-ip, dyndns and a few other services - dd-wrt does, I think tomato and openwrt do as well.  There is a no-ip package in the repos too - run it on the kvm host.  Anyway if  that doesn't work, setup an hourly curl crontab to hit a random text file buried deep on a web server you control (if the filename is unique and doesn't exist, the error will be easy to find.  Then just grep for that non-page to get the last public IP for the KVM box.  Over the internet, it isn't really safe to trust DNS anyway - use IP addresses and your ~/.ssh/config file.

When you are in the house, boot off a thumb drive with something like tinycore that has virt-manager pre-installed ... or use virsh ... or install a tiny linux VM with a GUI and use that.  Guess it really depends on whether the KVM host is a pure server or you've loaded any GUI crap.

Sometimes proxmox is the best option. I say that as someone who never ran it, but have seen it used at a few small clients. The only issue is proxmox takes over the entire installation. That is a plus and minus.

Or am I missing the point, which is likely.

---

### Post by pepsifx357 on 2015-04-20
All of those are excellent suggestions.  Like I said, it's a complicated situation.  My client is not very tech savvy and only has two computers in the house.  Her PowerPC Mac is for her recording studio and her laptop is Windows 7, which she is always on.  The PPC Mac is what I need to administer from, so I'm kinda stuck with needing a web based solution.  She has two wireless router, neither of them support ddns and getting no-ip to work on Fedora...didn't work for me.  It looks like I should have install ProxMox instead of Fedora.  The server I'm administering is running a virtualized ubuntu, running Airtime for her radio station.  I guess I was thinking that there would be a web based KVM to come along at some point that I could install.  I also didn't anticipate her DSL to be so horrible.  Her phone line running to the house has a splice below the ground, so when it rains she looses connection, which is why it's so hard to remote in.  I just tried Virt-Manager a minute ago and couldn't get past the password prompt.  Hopefully installing ClearOS and getting AT&T to come out and replace her phone line would fix a lot of my problems, but a web based kvm front end would be oh so convenient right now.

I might could try Ubuntu PPC on a flash drive and see if that works.

---

### Post by TheFu on 2015-04-20
What hardware does KVM run on?  Put everything on that box. There is a no-ip package for ubuntu. It works.

Proxmox wants to own all the hardware on a machine - it is an OS replacement, not an addon.
DSL tends to suck. Try to convince her to get DSL2+ or cable.

What does fedora have to do with this? You realize this is an Ubuntu forum, right?
There are other forum threads here about whether ClearOS (or other all-in-one distros) is the best answer. Many of the services provided really need to be on dedicated hardware. Putting too many services, especially things that face the internet is a risk.

You don't have a laptop?  $129 for an intel chromebook seems like a reasonable thing if you are a consulting business being paid. Wipe ChromeOS and put Ubuntu LXDE on it.

---

### Post by pepsifx357 on 2015-04-20
The Server is a Dual Xeon 2.33 quad core with 16GB of ram.  I put Fedora on it simply because I thought since Red Hat is developing KVM, it would work better.  I posted here, because I run Ubuntu and the community here is better IMO.  I should have put Ubuntu on the server, because I'm more familiar with it.  It's a 24/7 system, so I can't change it now unfortunately unless I migrate the VM to another machine whilst I fix my mistake.  I might actually do that in the future.  

I've used Proxmox before, so I'm familiar with it, but at the time I was installing the server I switched over to Virt-Manager.  My desktop has a custom kernel and, like you said, proxmox kinda takes over and would use it's own kernel. 

I wish cable was available out here in the boonies, but we're subject to AT&T's $55 a month 6mbps DSL.  There are no other options.  Sprint had a unlimited wireless internet plan at one point, but now they don't.

I really do need to get a netbook of some kind.  I'm a desktop person and have never liked laptops.  I used to have a Macbook Pro back in 2008 and it was a lemon.  The motherboard was replaced twice during it's warranty and it was about to go again, so I had to get rid of it.  I haven't had anything mobile other than a phone since.

I'll take a look at that chromebook, that might be a good option for me. I was also looking into getting an older white macbook and putting Ubuntu on that.  

Thanks!

---

### Post by TheFu on 2015-04-20
Chromebooks are cheap because the keyboard sucks and RAM is soldered onto the MB. No DEL key and they put the power key where that belongs. Took me 2 months of hitting it 20+ times a day to stop doing that. Every time, it powered off. It was painful.

I agree, laptops suck for most things. Use them mainly as remote desktop access devices using x2go back to a real system.  No laptop, regardless of price, can touch the performance of a $450 desktop.  Of course, video/audio editing doesn't work over a remote desktop, but programming and sys admin stuff does.  I write webapps on my chromebook (still wish I'd gotten the $280 11 inch Dell) and used git to have the current code where I need it. My chromebook had $150 in addons/upgrades before it was useful to me - so - if you are like me, get the Dell laptop, dude.  Any haswell celeron or newer is a pretty awesome CPU for a netbook these days.  Of course, I don't do java on the netbook and don't run gnom3 or unity.

Fedora was a mistake. Sorry. A centOS release would have been a better choice, if you wanted a RHEL compatible solution. Length of support matters.  It is why Arch makes terrible servers for 99.99999% of the world. No attempt is made to provide a stable platform. The same applies to non-LTS ubuntu dekstops.

I've been in the IT industry for decades. There is no such thing as a 24/7 server even with redundant everything. Software management requires downtime. Sometimes backups require downtime. 

Be certain you get the RTO and RPO to justify the effort you are expending and any hardware additions required to meet their RTO/RPO needs.  That exercise is as much to teach the client and manage their expectations. I didn't look this up, but a single server with no active-active failover gets a 98% annual uptime. No higher. That's about 6 days of **unexpected** downtime annually - don't guaranty higher levels. In the end, it is the client that decides whether a small weekly downtime is better than being hacked or doing forklift upgrades every few years - but WE have to provide them with the data and knowledge. Sure, 100% uptime might happen, but it is unlikely and the statistics don't suggest that will happen. 

Negotiate for 4 hrs a week of downtime now for maintenance stuff provided they fix the remote access problems.  If the network isn't solid - I'd double my support rate to make it painful and add that as a support condition in all future contracts (solid remote access networking). If they don't agree, fire the client; you don't want them.  

Ubuntu Server 14.04 is what I would load - then put everything else into VMs based on risk profiles. The hostOS shouldn't run anything except KVM+libvirt - IMHO.  Every month or so, you'll still need to reboot the hostOS due to kernel patches.  KVM is part of the kernel - it isn't just redhat doing development.

That seems like a bunch of RAM for home KVM server. It could easily run 15 VMs - provided they aren't Windows.

You have some things to consider.

---

### Post by pepsifx357 on 2015-04-20
Very good advice.  

Yeah it's a beast of a server for sure.  My client is a recording artist and she's starting this internet radio station.  Her son had a desktop windows xp computer with sambroadcaster running things.  It was a pain for her, as her studio is upstairs and she had to go up there every morning and program it for the day.  I love playing around with servers and all kinds of server software so I agreed to set her up with something.  The server she has is a used rackable systems server I got off of ebay for $400 a few years back and has been a rock solid system to play around with, so I sold it to her after I replaced the hard drives, installed Fedora and set it up.  It's got a battery backup/surge protector on it right now.  

There's a roadmap of things to come that she hasn't signed off on yet, such as another system running freenas to backup her studio sessions and act as a NAS, another external hard drive to backup the backups, ClearOS as a gateway/general server and OwnCloud for her recordings, so she can go sing somewhere and be able to access her recordings easily.  The radio station VM that's on the server has a cloned instance on standby in case something goes wrong, but it's not enough.  She's slow to move on things, because she's so busy.  Most of the downtime she encounters is due to the internet blacking out when it rains.  

I use Ubuntu 14.04 on most everything now, I wished I had installed it on the server. (facepalm)  She's a typa A personality so it's hard sometimes to get her to understand there will be downtime every once in a while.  She really needs to go with a hosted radio station, but she's also a control freak, so that wasn't going to fly.  lol  As long as i get paid, i have no problem being her IT guy.  Luckily she's only a minute down the road so i don't have to travel far.

---

### Post by bmullan2 on 2015-06-09
For KVM I just use Virt-Manager but last weekend I learned about Kimchi:    [http://kimchi-project.github.io/kimchi/downloads/](http://kimchi-project.github.io/kimchi/downloads/)

I installed it and it seems to work well.

Just follow the instructions on the above page to 
download the .DEB, .RPM etc
install the .DEB etc
run kimchid

then access via a web browser.

---

### Post by bmullan2 on 2015-10-20
Proxmox VE 4.0 (debian)[ https://www.proxmox.com/en/proxmox-ve/features]("https://www.proxmox.com/en/proxmox-ve/features")  was just released and they have switched from OpenVZ to LXC for containers.   They already used KVM for the HW VM's.
I was able to check the LXC capabilities out a bit and they seem to work.   I was able to create/manage LXC containers from within Proxmox VE 4.0 and I was also capable of accessing them by using the various LXC CLI commands.

I also found  that LXC Farm Manager ([http://pymag09.github.io/lxc-ui/](http://pymag09.github.io/lxc-ui/)) works really well,

Brian

---

