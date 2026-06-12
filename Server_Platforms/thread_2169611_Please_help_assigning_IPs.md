---
title: "Please help assigning IPs"
date: 2013-08-22
forum: Server Platforms
---

### Post by cronie2 on 2013-08-22
Hello :)

I am new (2 days) to ubuntu server 13.04. I run a Minecraft server and I am in the process of transferring everything to a dedicated, remote server. I have access via PuTTY and filezilla. I am still pretty unfamiliar with the OS and with its commands.

The dedicated server came with 4 IP addresses assigned to it and right now we are only using the primary one. I would like to assign some of the other IP addresses to tasks (such as a voice chat server, web page, etc.)

Could someone tell me how to do this please, step by step? Forgive me if any of my terminology is incorrect.

Thanks a lot :)

---

### Post by cronie2 on 2013-08-23
pretty please?

---

### Post by rai_shu2 on 2013-08-25
You have a host or do you run your own server?

---

### Post by sandyd on 2013-08-25
> **cronie2 said:**
> Hello :)

I am new (2 days) to ubuntu server 13.04. I run a Minecraft server and I am in the process of transferring everything to a dedicated, remote server. I have access via PuTTY and filezilla. I am still pretty unfamiliar with the OS and with its commands.

The dedicated server came with 4 IP addresses assigned to it and right now we are only using the primary one. I would like to assign some of the other IP addresses to tasks (such as a voice chat server, web page, etc.)

Could someone tell me how to do this please, step by step? Forgive me if any of my terminology is incorrect.

Thanks a lot :)

If you tell us what youd like to want, we can perhaps help you a bit better :)

---

### Post by Kevin_Arnold on 2013-08-25
Are you sure you got 4 external IPs, IPv4 addresses are getting harder to come by so most hosts only give you 1 unless you really need more.

Also, other than for multiple SSL certs, there really isn't a reason to use a different IP for each service. I'd set up a domain name to point to one of the external IP addresses and then use that for everything. Voice chat runs on a different port than HTTP or SMTP, etc. You can use the same IP/Domain Name for all of them and it will be much easier to manage.

For example:

You open a browser and type in "mydomain.com" and it brings up the web page.
Open Mumble and put in "mydomain.com" and the mumble port and it will connect voice chat.
Open putty and put in "mydomain.com" and choose SSH and it will connect to my server.

etc. etc. 

No reason to use different IP addresses in this case.

---

### Post by sandyd on 2013-08-25
> **Kevin_Arnold said:**
> Are you sure you got 4 external IPs, IPv4 addresses are getting harder to come by so most hosts only give you 1 unless you really need more.

Also, other than for multiple SSL certs, there really isn't a reason to use a different IP for each service. I'd set up a domain name to point to one of the external IP addresses and then use that for everything. Voice chat runs on a different port than HTTP or SMTP, etc. You can use the same IP/Domain Name for all of them and it will be much easier to manage.

For example:

You open a browser and type in "mydomain.com" and it brings up the web page.
Open Mumble and put in "mydomain.com" and the mumble port and it will connect voice chat.
Open putty and put in "mydomain.com" and choose SSH and it will connect to my server.

etc. etc. 

No reason to use different IP addresses in this case.
It isnt that hard, I have 2 /28s and 1 /27, and ARIN isnt even complaining... (ive owned them for several years now). Some hosts use a /32 as the main subnet, some give out a /29 by default, it just depends on the host

---

### Post by Kevin_Arnold on 2013-08-25
> **sandyd said:**
> It isnt that hard, I have 2 /28s and 1 /27, and ARIN isnt even complaining... (ive owned them for several years now). Some hosts use a /32 as the main subnet, some give out a /29 by default, it just depends on the host

Right, but I'm sure you knew what you were doing when getting those. I just assumed since this was in the Absolute Beginners section, he may have just done an "ifconfig" and saw 4 things in there and thought that meant he had 4 IPs. I could be wrong, though. He says he has a dedicated server where more IPs are likely. Most VPSs just give out 1, though.

None of that changes the fact that he probably can do everything he needs off of a single IP addresses.

---

### Post by cronie2 on 2013-08-25
Thank you for your responses.

Basically, right now I am just looking for information. I really don't understand a lot about this and I don't know how to search for it. 

Currently the server is running a Minecraft server and a voice chat server on the main IP. In the future, I might want to set up another minecraft server and I would prefer to use a separate IP so people can use the default ports for both.

I am attaching a screenshot of my server specs to help with any answers. Under "IP allocation" it says I have 4 sequential IPs and currently I am using the first one. How can I use the others? I feel like I may as well use them for something since they are paid for :)

Thanks in advance for any replies

[IMG]http://i1217.photobucket.com/albums/dd391/pookshuman/specs.jpg[/IMG]

---

### Post by Kevin_Arnold on 2013-08-25
I know this isn't what you're looking for but with a server like that, I would have set up a couple virtual machines and ran the minecraft servers on those. You could give each VM it's own external IP address.

I'm sure you can still do it the way you are mentioning, though. I just have never set up a minecraft server so I don't know the specifics on that.

---

### Post by 1clue on 2013-08-25
I don't think you're going to like this, but given the level of expertise you're showing and the deliciousness of this box as some black-hat hacker's remote platform, maybe you should consider a consultant.

Get a contractor, get them to sign a contract and a non-disclosure agreement, and have them configure your server.

Hardware like that is expensive.  I have rented rack space too, I know what you must be paying for this thing.  If you were installing the server first on your home network or office network, experimenting, wiping it off a few times and reinstalling to get this right, then I would continue as you are going with community support.

You're obviously trying to install a commercially viable system, and it's going to get attacked just because that's what black-hats do.  You won't even have to give us a domain name, people will simply see that you're setting up this type of box and wait for a new Minecraft server to come up.  If you've left anything out for security they'll find it.

The time for experimentation is before you own the box.  Trial and error on a dual or quad core desktop with a couple nics on it, as many times as it takes, and then start from scratch on your real public box when you know what to do.

---

### Post by cronie2 on 2013-08-25
It's not a "commercial" server ... we don't make any money off of it. We don't have the money for a consultant. I just do this for fun.  There is not much I can do about black-hats. I am a poor guy who just don't have the expertise or money to deal with them. All I can do is backup my data.

Does anyone know of any tutorials/walkthroughs to do what I am talking about? I know it has something to do with the interfaces config, but I am not having an easy time tracking exactly what.

---

### Post by 1clue on 2013-08-25
Do you have the box on the open internet right now, or is it at somebody's house/office/whatever?

Or, is it something like linode.com or some other cloud server?  In which case you might have an RDP-style terminal in an admin page in case things go south?

What I'm saying is, if you trash all your network interfaces and this thing is a thousand miles away, how do you recover?

---

### Post by cronie2 on 2013-08-25
Probably if something went wrong with the file, I would reload a backup. If that didn't work or I couldn't connect I would call the hosting company and just ask them to do it.

---

### Post by 1clue on 2013-08-25
OK so I'm about to go to bed, but if you could show us the output of **ifconfig** and **netstat -rn** and then alter the first two octets again.

Or better yet, do a replace on xxx.yyy to aaa.bbb where xxx.yyy is the first two octets and aaa.bbb is the literal string.  That way we might detect some of the possible issues.

And why did you get 4 IP addresses?  You seem to only have 1gbps bandwidth, is it some sort of load balancing reason or high availability?  Or what?

---

### Post by 1clue on 2013-08-25
And I assume you've seen this:

[https://help.ubuntu.com/13.04/serverguide/network-configuration.html](https://help.ubuntu.com/13.04/serverguide/network-configuration.html)

---

### Post by cronie2 on 2013-08-26
I am not sure what you mean by "detecting possible issues" .... I haven't tried anything yet, so there are no issues.

The server came bundled with the addresses, we didn't really need them.

I wasn't really planning to do anything with this for a month or so, right now I am just trying to learn how it all works.

Thanks for the link, I will check it out.

---

### Post by sandyd on 2013-08-26
Few things to read now

**Security**
What I would reccomend is taking a read about
a) iptables
b) ssh key authentication
c) openvpn tunneling

Iptables is basically the standard command line firewall.
I reccomend something such as the below as a base to build on, replacing first-ip-here with the first ip address of your server which you ssh to
```

# Generated by iptables-save v1.4.12 on Thu May 16 21:00:15 2013
*mangle
:PREROUTING ACCEPT [112866:164144793]
:INPUT ACCEPT [112866:164144793]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [50184:2980417]
:POSTROUTING ACCEPT [50184:2980417]
COMMIT
# Completed on Thu May 16 21:00:15 2013
# Generated by iptables-save v1.4.12 on Thu May 16 21:00:15 2013
*filter
:INPUT ACCEPT [112866:164144793]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [50184:2980417]
-A INPUT -i lo -j ACCEPT
-A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
-A INPUT -p tcp -m tcp -d first-ip-here --dport 22 -j ACCEPT
-A INPUT -j DROP
COMMIT
```
Save the above as /root/iptables, and run

```

iptables-restore < /root/iptables
```

Now, you have some sort of firewall up, but it still doesn't secure SSH and blocks everything that isnt a connection initiated from your server. We can add rules to unblock ports needed for mumble, .etc .etc later

Ive got some options below on how to secure SSH (which is the easiest way for someone to break in)

**SSH Key Auth**
Passwords are insecure. The easiest way to secure SSH is to enable SSH key auth. See [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys) to read more about it and how to accomplish it. Its extremely secure (RSA/DSA based key). Its hard to copy as the key has tonnes of characters. If your using putty, you probably have to use puttygen to convert it into something putty can use.

**Fail2Ban**
Long story short, it blocks your IP if you get too many bad password retries. See [https://help.ubuntu.com/community/Fail2ban](https://help.ubuntu.com/community/Fail2ban). Doesnt really accomplish anything when the person can guess your password before their number of password retries run out

**OpenVPN**
If you like going nuts about security like me, you probably want openvpn, its probably the most secure out of the three. Basically establishes a encrypted tunnel between your computer and your server. I like it mainly because there are no SSH ports exposed to the internet (if you forget to disable password authentication and such), and because of that, there is no way to hack your SSH server. The only place that SSH is now accessable is through your VPN.
----

Also, about
**IPMI/KVMoIP**
Some providers offer something like IPMI or ILO/Lights-Out or a KVM attachment. Those are password protected as well, and I suggest that you set a strong password (Go to [http://strongpasswordgenerator.com](http://strongpasswordgenerator.com) to generate one), and save it. Mine are 50+ characters in length with symbols, but thats just the paranoia in me (I have them saved even on a YubiKey...). They are not connected by default, so I am not too worried anyways

Im sleepy now, ill update this post tomorow, post if you have any questions

---

### Post by rai_shu2 on 2013-08-26
> **cronie2 said:**
> It's not a "commercial" server ... we don't make any money off of it. We don't have the money for a consultant. I just do this for fun.  There is not much I can do about black-hats. I am a poor guy who just don't have the expertise or money to deal with them. All I can do is backup my data.

Does anyone know of any tutorials/walkthroughs to do what I am talking about? I know it has something to do with the interfaces config, but I am not having an easy time tracking exactly what.

Have you looked at your own spec sheet? You do realize that you could be spending up to $1500 a month just on bandwidth, right? That set up pretty much demands professional consulting, or you could quickly go in the red in five or even six figures. Nobody does that "for fun" unless they're a freaking millionaire.

---

### Post by sandyd on 2013-08-26
> **rai_shu2 said:**
> Have you looked at your own spec sheet? You do realize that you could be spending up to $1500 a month just on bandwidth, right? That set up pretty much demands professional consulting, or you could quickly go in the red in five or even six figures. Nobody does that "for fun" unless they're a freaking millionaire.

Actually, I can quote the setup that he used to around 100-150, or even lower.

---

### Post by Kevin_Arnold on 2013-08-26
> **sandyd said:**
> Actually, I can quote the setup that he used to around 100-150, or even lower.

I think he was just confused about the bandwidth. He gets 10TB of bandwidth for "free" and then is only charged extra after that. I'm guessing rai_shu2[COLOR=#000000] just took 15 cents/GB and added it up for 10TB and came up with the $1500.[/COLOR]

---

### Post by rai_shu2 on 2013-08-26
Right, right. That was the overage rate. Still, $100 a month is more than a hobby, I think. You can get FatCow hosting right now for $50 a year.

---

### Post by sandyd on 2013-08-26
> **rai_shu2 said:**
> Right, right. That was the overage rate. Still, $100 a month is more than a hobby, I think. You can get FatCow hosting right now for $50 a year.

I currently spend around $350-$400 on
a) Colocation
b) 1 Dedicated Server
c) EdgeCast CDN.
d) AnyCast DNS
Its a hobby still :)

---

### Post by rai_shu2 on 2013-08-26
Okay. Well, some people prefer sports cars. Just sayin.

---

### Post by cronie2 on 2013-08-26
anyhoo. :) I already had the firewall enabled and I will look into the other security stuff. Thank you for the links, Any chance I could get pointed towards the original question? setting up alternate IPs?

---

### Post by sandyd on 2013-08-26
> **cronie2 said:**
> anyhoo. :) I already had the firewall enabled and I will look into the other security stuff. Thank you for the links, Any chance I could get pointed towards the original question? setting up alternate IPs?

Make a list of what you want to run, and what you plan to run in the future, and we can work from there :)

---

### Post by cronie2 on 2013-08-26
First order of business will be a secondary minecraft server for a different user. I assume this means I would need to make second instance of the mcmyadmin directory (mcmyadmin is the program for interfacing with minecraft)  The second user would need ftp file access as well. I assume this is just a question of sorting out the permissions for a second user and I think I can figure that part out.

Right now, I log into xxx.xxx.xxx.134 to access the server (various ports for different programs) I would like to set it up so users logging in to xxx.xx.xxx.135 would see the alternate, secondary versions of those programs (mcmyadmin, minecraft, voice chat, etc)  Does this make sense?

---

### Post by 1clue on 2013-08-26
Is there some sort of a minecraft recommended setup you're following?  You're just using network cards because you have them?

If you can set up an admin IP which is only accessible through the VPN, and then change the ports so you have to know something even if you get into the VPN, that would be useful.  For example, make ssh be only available through VPN and only on your admin IP.

Another thing, sometimes one or more ethernet cards is dedicated to fast access to a database server.  Or some other server.  Or it could be failover, but again there you're looking at specialized configuration.

As well, what's this FTP?  Are you talking about one physical box and multiple copies of minecraft? Or is there a companion minecraft binary for a different function?  Or two boxes?  DO NOT open FTP up on the open internet, even authenticated, without knowing EXACTLY what you're doing for security.  DANGER, WILL ROBINSON!

My opinion is, if you don't have something specific to do with one of these network cards, I would not even configure them.  Having an address out there listening just complicates your job for security.

You keep saying "we."  How many "we's" are there?  In rough numbers?  less than 10?  Less than 50?  What is this exactly, are you a non-profit organization, a bunch of guys who know each other personally who collaborated on a server?  A bunch of guys who met on the net and want to collaborate?  I'm asking for a reason.  You need to decide the amount of trust involved and give access accordingly.  Assuming your name is on this server's contract, you need to evaluate your liability and consider security not only for the greater Internet but also with each of your collaborators.

Most importantly, is there a legally binding contract, or better yet, a non-profit or LLC to which all of "we" is bound, that's protecting you from losing your house?

You don't have to answer any of this legal stuff on the forum, but you certainly better think about it.  Freddie Kruger could show up at my door and I wouldn't run away screaming any faster than the situation you've described so far.

Enough said on that, just saying.

---

### Post by Kevin_Arnold on 2013-08-26
The more I hear what you're doing, the more I think you should just spin up a virtual machine for each minecraft instance.  It will take a lot of custom config to get two versions of all of these servers running under the same os. 

2 vms would be easy as pie.

---

### Post by 1clue on 2013-08-26
I kind of like the VM idea too.  You could link each one to its own IP, and once you get the first one set up all you have to do is copy it and change a few things like IP address and passwords and the second one is set up.

This is also a lot more secure.  You can have your real hardware on its own address with absolutely nothing available outside the VPN, I wouldn't even give it a domain name.

Your hardware is definitely up to running KVM with these two hosts on it.  I don't know what sort of load minecraft gets, or how many end users you intend to support.

---

### Post by cronie2 on 2013-08-26
OK then, so what is involved with 2 vms? Why is it an advantage? What is the down-side? What is the setup?

---

### Post by 1clue on 2013-08-26
The down side is you have slight CPU and resource overhead.  You're running:
[LIST=1]
[*]The main machine operating system, which can be extremely minimal.  It's often a non-gui server install.
[*]VM 1.  You need disk space and RAM to run an entire server as though it were hardware.
[*]VM 2:  You need pretty much the same thing again, for the second install.
[/LIST]

Advantages:
[LIST=1]
[*]The REAL operating system (the host) is not exposed to the same ports as the VMs (guests).
[*]You would give one IP address to the host.
[*]You would give one IP to guest A
[*]You would give one IP to guest B
[*]Only guests A and B are exposed to the Internet as per your firewall.  Someone cracking either VM does not get access to the other VM or to the main host.
[*]You don't need to make special consideration for any other software on the guest.  You set up for only the service you're interested in.
[*]Neither VM needs to have any knowledge of the other.
[*]You can back up the entire virtual disk before trying something risky.
[*]You can duplicate the machine from any backup point simply by copying a file.  For example, you could install Ubuntu Server on the first VM, back it up by copying the stopped machine to a directory, and then at any time have a bare Ubuntu installation for any purpose, just by copying from the backup to a new location and starting it up.  Or, you can install your first minecraft server, back it up, restore it to a new location and change the IP and passwords, and you have a new server.
[*]You can install a basic gui like xubuntu or lubuntu on the host, add virt-manager and have a gui-based virtual machine manager similar to VMware's commercial products.
[/LIST]

Disadvantages:
[LIST=1]
[*]You tie up system resources to the virtual machine.
[*]The faster you want the VM to run the more resources you need to dedicate.
[*]You have duplication of resources.  RAM, disk, cpu cores, etc.
[*]There is a bit of overhead for virtualization, but this is minimal on any modern system of the category you're using.
[/LIST]

Not sure how to rate this, disadvantage or advantage.  It's how VMs work.  If you have two guests, they are sharing resources.  Say you have your two minecraft VMs.  If both are running heavy at the same time, then this is the worst case.  Both are trying for resources from the host at the same time.

But if server A is busy and server B is not, then A gets all the resources of the host, which is a bigger machine than it normally would have.  The bigger the hardware and the more VMs you have, the more this advantage matters.  But the more VMs the more likely everything will even out, unless all the servers are in use simultaneously all the time.

---

### Post by cronie2 on 2013-08-26
That sounds reasonable, I don't think resources will be a problem for the foreseeable future.

So I would have the real server running Ubuntu OS. That would be running a virtual machine. On that virtual machine I would install Ubuntu Server again and run my programs from that? Do I have that correct?

Also, why do I need 2 virtual machines? I already have everything set up on the real machine. Can't I just install 1 VM for the guest and use the main (non-virtual) one for myself?

Does the software cost anything?

---

### Post by 1clue on 2013-08-26
Yes, that's the idea.

You can buy commercial virtualization software, but you can use something like KVM for free.  I would recommend virt-manager as well, which is also free.  It is a GUI tool which lets you configure each system (cpu count, memory, etc) by using menus and dialogs rather than a command line.  It means installing a GUI version of Ubuntu, but if you use Xubuntu or Lubuntu it will be pretty small.

Technically you could have one server on the real hardware and another on the VM.  You lose a lot of advantage by doing that though.  Usually what people do is put just enough software on the main VM to handle the guests, and the rest is on each VM.

The main reasons I would do it with multiple VMs:
[LIST=1]
[*]The main machine can have only the software necessary for virtualization and easy management.
[*]That makes the host more reliable, since there is less on it to break.
[*]You have two virtually identical servers to install.
[*]If you install one on the main host and the other on a VM, then you can't just copy one onto the other.
[*]If you need to reboot your main server then you have to reboot the other one too, where having two on VMs means you can update or reboot each separately.
[/LIST]

I would personally reinstall your box with Lubuntu or Xubuntu.  Just wipe it clean and start over.  Or alternately, make a backup partition (or use a backup disk) and save all your data and configuration to that, have a small main distro partition and then set up the rest as LVM so you can resize your VMs as you want, on the fly.

---

### Post by 1clue on 2013-08-26
[https://help.ubuntu.com/community/KVM/Installation](https://help.ubuntu.com/community/KVM/Installation)

By the way, using KVM means you can create more VMs in a few minutes.  For example, let's say you want to test an upgrade of one of your servers.

You back up the VM, restore it as a new VM, boot it and change IP address.  Upgrade, test it, and if it works you can either schedule the downtime and upgrade the 'normal' VM or you can keep the backup and switch to the newly upgraded setup.  It depends on how hard it is to configure IPs.

Another thing you could do:
[LIST=1]
[*]Each VM is essentially identical to the other.
[*]Configure each VM as it's supposed to be.  IP addresses, memory settings, server names, whatever.
[*]Script the changes in a directory on your main host.
[*]Now you have something you can use to easily upgrade or restore a VM with.
[/LIST]

You could have a configuration script for each VM, and another for a test VM.

Any broken server is easily restored by copying a good backup over the top of it, rebooting and done.

Each service can run different parameters, a different version of Ubuntu or a different Linux or even Windows if you want to.

---

### Post by cronie2 on 2013-08-26
When I was looking into what OS to use, every place I searched on the web said not to use a GUI OS. They said they were less secure and reliable. Is this true?

I would prefer to have a GUI personally though. I am running Windows, would I need to use an Ubuntu boot disk to run virt-manager or will it work in Win7?

Also, what is the difference between ubuntu and l/xubuntu? and would a newbie such as myself notice a difference?

---

### Post by 1clue on 2013-08-27
Yes, it's true that a GUI operating system is less secure.  If that host is unreachable without a VPN though it's not so bad.  It's definitely better if you can do the whole thing without the GUI.

Most real-world installs of KVM are command line installs.  It can be done, it's just a bit less intuitive.

I am using virt-manager on my personal VM box because it's easier, and it's also a workstation in my office.  However none of these systems (host or guests) is publicly available.  For virtualization for the office, it's non-gui.

My intent was to recommend a minimal GUI on the main host, then whatever you do (no GUI as it turns out) on the publicly available guests.  If the host is only reachable through a VPN then it's easier to secure.  You've got a huge amount of reading to do anyway, I thought I'd make it a little easier for you.

---

### Post by 1clue on 2013-08-27
Reliability:
The more software you have on a system, the less reliable it is just by virtue of its complexity.

This is why most KVM systems are an absolute minimal system, plus the KVM host packages.  KVM is essentially a kernel module for Linux, and a few utility apps to manage it.

If software isn't present then its security holes can't be exploited.  Just because you don't know of an exploit does not mean it doesn't have any.

With virtualization, each host is technically vulnerable, but if you compromise a guest it doesn't compromise any of the other guests or the host.  The host is the biggest issue,  but if it's not available on the Internet then it's less risk.

---

### Post by sandyd on 2013-08-27
If i were you, I would go with proxmox, it has a nice web GUI that can easily be secured using iptables so that it can only be accessed via openvpn. It supports both KVM and OpenVZ virtulization, and doesn't require a special client like ESXi or XenServer. Its based on debian 7.

For lower Overhead and easier setup, use openvz (you can just specify the IP when creating the OpenVZ virtual machine, and it will work). For full virtulization use KVM. OpenVZ shares the kernel with the host, but that is not a problem because you are in control of the host.

---

### Post by cronie2 on 2013-08-27
It's a remote host anyways, so I wouldn't have access to a GUI

---

### Post by 1clue on 2013-08-27
Never tried proxmox but it sounds like a good idea; put it behind the VPN and it's just a web page through a VPN.

BTW you CAN use X across the internet.  I would recommend **ssh -X <remote host>**, log in and run whatever app you want.  It will take longer than usual, you're running a GUI through an external network connection and you're limited severely by the weakest link.

Another thing you can do:  Every port which is not "public" meaning necessary for the service to do it's thing, should be moved to a high port.

For example, ssh might be moved to port 9482.  Most port scanners will only go for low ports.  If you ssh into the box on some port only you know which is above 5000, it's a lot less likely somebody will even find the port, let alone break it.  And add that to the need to log into the VPN and you have some defense in depth.

The management/admin ports being moved to something only a few people know adds a whole lot of security.  Allowing X remotely only through ssh AND the VPN also helps, if you chose to do X on the host.

---

### Post by cronie2 on 2013-08-27
Can you give me a bit more info on that one? "ssh -x ..." What will that do and how would I use it? Right now I am connecting via PuTTY on a windows machine. Would I need to run a copy of ubuntu on my home system for this to work?

I don't know much about ports so I generally leave them alone unless a program needs one.

---

### Post by 1clue on 2013-08-27
Wow.

You know I might be complicating things for you with all this GUI talk.

X is the GUI protocol that Linux uses, and quite a few of the commercial UNIXes.  On top of it you put a window manager like Unity or KDE or XFCE, and you get flavors of desktops out there.

X is a network protocol.  So you can send it across the Internet.  By default it uses at least one network socket per client.  A client is something like firefox or a terminal window.  The client connects to the X server, which is where you are sitting.  It's backwards compared to the normal way you think of client and server, but really Firefox is telling X what to draw, X draws it and gives back any buttons you clicked on.

ssh -X <host> (that's a capital X, not x) tells ssh to forward X traffic through the ssh tunnel instead of having it make its own socket.  I believe that's mostly just openssh, which is the freeware version of ssh.  I know that Mac OS has the feature, but I don't know about putty.

The thing is, you need an X server on your workstation in order for all this to work.  Mac OS has a decent one, it's UNIX after all.  I don't know about Windows.  So you would need an X server and a version of ssh that understands the -X flag.  That would probably be a big enough project all by itself.

Maybe you should forget all I was talking about with GUI clients.

---

### Post by sandyd on 2013-08-27
Also - ask if Datacenter connects KvmOIP on request
A lot of them have a Lantronix Spider Duo which they will connect for a hour or so, so you can restrict SSH to openvpn, and ask them to connect a KVM unit if you are ever locked out.

If you want, I have the iptables rules needed for the latest version of proxmox here as well, and I will post them as soon as I get out of this meeting....


```

# Generated by iptables-save v1.4.12 on Thu May 16 21:00:15 2013
*mangle
:PREROUTING ACCEPT [112866:164144793]
:INPUT ACCEPT [112866:164144793]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [50184:2980417]
:POSTROUTING ACCEPT [50184:2980417]
COMMIT
# Completed on Thu May 16 21:00:15 2013
# Generated by iptables-save v1.4.12 on Thu May 16 21:00:15 2013
*filter
:INPUT ACCEPT [112866:164144793]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [50184:2980417]
-A INPUT -i lo -j ACCEPT
-A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
-A INPUT -p tcp -m tcp -d first-ip-here --dport 22 -j ACCEPT
-A INPUT -s vpn-ip-here -p tcp -m tcp --dport 8006 -j ACCEPT
-A INPUT -s vpn-ip-here -p tcp -m tcp --dport 5990:5999 -j ACCEPT
-A INPUT -j DROP
COMMIT

```

---

### Post by 1clue on 2013-08-27
I've read through the thread again.

Forget all the stuff I said about GUI tools and X.  It unnecessarily complicates things for you, especially since you're using a Windows workstation.

Given the level of knowledge you're showing I'd say just getting this thing up and functional is going to be a huge task for you.  Keep it simple.

Here's the revised list of things I'd do:
[LIST=1]
[*]Re-install the base system or clean it off so that it contains only KVM and VPN software.  And of course firewall tools.  Update it.
[*][s]Set up bridged networking on KVM.  The link I pointed at earlier shows how.  You might need this for the final servers but won't use them right away.  Be careful because there are parts of this where the network is down.[/s]
[*]Configure your VPN.
[*]Configure your firewall to deny all non-vpn access to your administration IP.
[*]Configure your firewall to deny all non-vpn access to your other IPs.
[*]Create a virtual machine for server A.
[*]Install Ubuntu Server on it, configure it for DHCP with a "host-only" network.
[*]Shut it down and copy the VM files to a backup location.  This is now your base for any future VMs you might want which are NOT your game server.
[*]Copy the backup to a new location which will be your first game server.  This leaves the bare install as a bootable system.
[*]Install your game system.  This assumes that you can use the default IP address for the game system and you don't need to hardcode an IP.
[*]Test your game system through the VPN.
[*]If it works, shut it down and copy it to a backup location.  This is now your base game system.
[*]Copy the backup to a new location which will become your second game system.
[*]On each gaming system, while it's shut down, switch to one of the real cards and give it one of your public IPs.  Refer to KVM docs on this.
[*]Test your servers again through the VPN.
[*]Open up the necessary ports to the public Internet for one of the servers.  ONLY the gaming ports!
[*]Test again.
[*]Get your friends to test simultaneously.
[/LIST]

I left proxmox out of this.  I know nothing about it so I'm not giving advice about stuff I know nothing about.

Also keep in mind I have no idea how your gaming software works, I've never played it and I've probably never even seen a video or an ad for it, and I don't really want to.  Call me a clueless old fart.

What I know about is provisioning servers on the Internet which will be available to the public, and getting them to be compliant with various security specs, and collaborating with a third party auditor.  I know about KVM as not-quite-a-novice.  I use them for my job, but I haven't done a setup that lots of people use.  In my KVM scenario (which is internal testing on a completely closed network with physical access), having a GUI does not really hurt things.  In your scenario just getting the GUI is an unnecessary and relatively large complication and a security risk once it's set up.

Big rule:  When you're doing something which is to be publicly accessible, KNOW SOMETHING BEFORE YOU MAKE IT PUBLIC!  The day you open it up is the final exam.  Be ready for it.  Be secure.  Be careful.  Don't do something just because some guy on a forum said so.  Evaluate what people are saying, do the research and decide if it's a good idea or not.

If your gaming software recommends a certain type of security compliance or audit, then seriously consider following it as best you can.

***Edit:**  I took out the bridged networking part.  You don't really need it for this setup, although I haven't ever dedicated a hardware card through KVM I'm positive it can be done and that the instructions are easily available.  It's just one more complexity you don't need.*

---

### Post by wildmanne39 on 2013-08-27
*Thread moved to **Server Platforms**.*

---

