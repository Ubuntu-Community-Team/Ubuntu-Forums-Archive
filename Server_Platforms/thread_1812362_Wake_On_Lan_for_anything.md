---
title: "Wake On Lan for anything"
date: 2011-07-26
forum: Server Platforms
---

### Post by emdiesse on 2011-07-26
I am looking to set up a few things on my Ubuntu machine such as an apache server, to set up subversion and create an svn I can access from my windows pc using tortoise svn and so on.

I could leave my PC on all the time however I don't want to do this unnecessarily. I am able to wake up my PC on LAN and have successfully set this up. However, I would like the PC to be able to WOL whenever any activity is required from it.

Say I visit the dyndns I set up for it using an ssh client for windows I want my ubuntu machine to boot up to allow me to ssh into it.
Say I visit the dyndns in a web browser I want my machine to boot up so I can see www data
Say I try to commit something to the svn repository and the ubuntu pc is off I want it to boot up to allow incoming connections.

Is there a way to allow this?

Also, a way to turn the PC off once activity has stopped for 1 hour. Ready for the whole process to start again.

---

### Post by jamie_alexander on 2011-07-26
[http://lifehacker.com/348197/access-your-computer-anytime-and-save-energy-with-wake+on+lan](http://lifehacker.com/348197/access-your-computer-anytime-and-save-energy-with-wake+on+lan)

it's not ubuntu specific, but I guess the key thing here is waking up you're PC remotely, the link above should give you a start


then again , more ubuntu specific help can be found here:
[http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)

and isn't google great - that's where I found these links...



:guitar:

---

### Post by emdiesse on 2011-07-26
> **jamie_alexander said:**
> [http://lifehacker.com/348197/access-your-computer-anytime-and-save-energy-with-wake+on+lan](http://lifehacker.com/348197/access-your-computer-anytime-and-save-energy-with-wake+on+lan)

it's not ubuntu specific, but I guess the key thing here is waking up you're PC remotely, the link above should give you a start


then again , more ubuntu specific help can be found here:
[http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)

and isn't google great - that's where I found these links...



:guitar:

Hi,

Thanks for the response I suppose my first message isn't exactly clear. I'm not concerned about setting up WOL, apache, ssh, etc I have done these before.

I am looking for a way to bypass WOL such that if I visit my PC using SSH and it is off it will turn itself on without me having to send a magic packet. If I press commit on tortoise svn on my windows pc it will update my svn on ubuntu, if the pc is off it'll turn on and then update.

Basically I am looking to cut the following processes down from:

Web
1. send magic packet
2. type in ip address
3. see www data

ssh
1. send magic packet
2. connect to ssh
3. etc

to simply

Web
2. type in ip address (PC will turn on if off)
3. see www data

ssh
2. connect to ssh (PC will turn on if off)
3. etc

---

### Post by egpetrich on 2011-07-26
Some network interface devices support wake-on-lan for things other than the "magic packet." The utility "ethtool" allows you to query and set the device configuration. For example, the command "sudo ethtool eth0" on my machine says (in part):

```
Supports Wake-on: g
Wake-on: g
```

So I don't get to ask for anything other than magic-packet wakeup. The "ethtool" man page gives the following additional possibilities:

```
p  Wake on phy activity
u  Wake on unicast messages
m  Wake on multicast messages
b  Wake on broadcast messages
a  Wake on ARP
g  Wake on MagicPacket(tm)
s  Enable SecureOn(tm) password for MagicPacket(tm)
d  Disable (wake on nothing).  This option clears all previous options.
```

Unfortunately, I don't know how the additional options work in practice. Some digging on the net may give you answers.

If your network interface device doesn't support anything but magic packet, you would need to have another always-on device to act as a sleep proxy. A sleep proxy watches the network traffic and either responds on a sleeping machine's behalf or wakes up the machine. In my limited past searches, I haven't been able to find any tool that can meet this need right out of the box. (What would be great is to have this support under DD-WRT or similar router firmware.)

Here's a link to a research paper that you may find interesting:[URL="http://mesl.ucsd.edu/yuvraj/research/documents/Somniloquy-NSDI09-Yuvraj-Agarwal.pdf"]
http://mesl.ucsd.edu/yuvraj/research/documents/Somniloquy-NSDI09-Yuvraj-Agarwal.pdf[/URL]

To suspend your system automatically, the "powernap" tool is the best I can offer. Its functionality is a bit limited, since it depends on what it can see in a "ps" command output. Still, it's very easy to configure so as to keep the machine running so long as you remain logged in over SSH.

---

### Post by rcauston on 2011-10-12
I tried the ethtool -s eth0 wol pg on my Natty server with negativish results. 
 
The home server in question sits in my closet and it's supposed to jump to life when my MacMini automounts it's directories from this servers Samba-shares. 
 
Now previously I was happily running the Hardy on this server and it just worked i.e. the server never slept, but the hardware raid controlled spinned down it's disks happily after 15min. Life was good. 
 
Since then my motherboard died and I ended up doing a reinstall and the long awaited update to Natty server. Then my problems started with these powersaving modes. I can wake the server up by sending a magic packet to it and with a random amount of delay it seems to wake up to network activity after the ethtool trick above (but not quick enough to get up during ssh-timeout nor SMB-mount timeout. 
 
Both of these cases are unacceptable since my wife & kids need to be able to just use their Macs with homedirectories on the fileserver and not know anything about magic packets and WOL. 
 
**So how can I disable powersaving features altogether since WOL doesn't cut it?**
 
(And please advice for console only server config since it doesn't have X installed)

---

