---
title: "Linux equivalent for MS ISA Server?"
date: 2007-06-20
forum: Server Platforms
---

### Post by ehull82 on 2007-06-20
My current employer is looking into purchasing a new server for the purpose of running an MS ISA Server.  We currently don't have licenses for an ISA Server or another copy of Windows Server 2003 and the costs of everything looks like it is going to exceed our budget.

What would be the linux equivalent to an ISA Server?  Its probably more than one software package which is fine but is there software that when combined would roughly equal MS ISA?

---

### Post by Betelgeuse on 2007-06-20
> **ehull82 said:**
> My current employer is looking into purchasing a new server for the purpose of running an MS ISA Server.  We currently don't have licenses for an ISA Server or another copy of Windows Server 2003 and the costs of everything looks like it is going to exceed our budget.

What would be the linux equivalent to an ISA Server?  Its probably more than one software package which is fine but is there software that when combined would roughly equal MS ISA?

My advice woud be ipcop linux distribution. it's a distro for using as a firewall and I'm using it on my office without problems. I'm new to linux, only using it for 6 months but I'm using ipcop for 2 years. it has a web based admin interface to configure everything and as a linux newbie, it's a good thing. it has lots of addons, you just have to select what add on you need and run it. I'm using ipcop in a vmware-server virtual machine with advanced proxy and url filter add on and I'm using qos-ng addon for traffic shaping. 
ipcop is a tiny linux distro, you can run it on an old machine with 2 network interfaces and with only 64 MB of ram. 128MB of ram is an overkill for that machine. and you'll need only 1GB of disk space if you use web proxy. if you do not use web proxy, 100MB disk space is more than enogh. have a look at [www.ipcop.org](www.ipcop.org) and there is a ready to use vmware-server image on vmwarez.com, I'm using that images and I added qos addon that I find on ipcop web site...

---

### Post by ehull82 on 2007-06-25
Thanks for the response.

After discussing IPCop with my boss I was informed that they don't plan on using the Firewall or VPN features of ISA.  We currently have a Cisco Pix firewall for both of those functions.  They are primarily looking at using ISA as a proxy server and to filter websites and block users from accessing unwanted sites like MySpace or YouTube, etc.

I've read that Squid-Cache is highly recommended as a proxy server, but what about web filtering?  One site I found recommends [dansguardian]("http://dansguardian.org").  Also I've found [SquidGuard]("http://www.squidguard.org"), does anyone have experience with either of these?

---

### Post by amlucent23 on 2007-06-27
not sure about IPCop but Smoothwall has plugins for Dansgaurdian, ClamAV, and advance squid functionality.

IPCop is a early fork of Smoothwall (smooothwall.org) I have never used IPCop but I have heard great things but I can tell you that smoothwall will easily do what you require. I believe that IPCop has this feature as well but with smoothwall if you just enable a check box the proxy will become transparent to the users and they wont even realize that a proxy is whats blocking them from accessing youtube. You can set it to filter individual sites or even keywords. Snort is built in to keep intrusion detection logs. Really nice. Oh and they run on old as dirt hardware excellent!

Truthfully, I like Smoothwall over ISA server 2k4 (haven't tried 2k6)

If you do choose Smoothwall I can advise you to get the Superkernel iso.. its maintained by a few of the devs.. its full of a bunch of features that are not in express version by default.
[http://sourceforge.net/project/showfiles.php?group_id=114890&package_id=195958]("http://sourceforge.net/project/showfiles.php?group_id=114890&package_id=195958")


also a few others that you might look into...

ClarkConnect
MonoWall (like smoothwall but its BSD based not all the features but you dont appear to need them all)
Novell also has a linux network security program... dont know how much it is

---

### Post by hackbox on 2007-06-27
May be you can take a look at Endian Firewall too...   [http://www.endian.com/en/community/about/](http://www.endian.com/en/community/about/)

I was using smoothwall before but now I prefer EndianFW and there's plenty of option to do the tasks you want

---

