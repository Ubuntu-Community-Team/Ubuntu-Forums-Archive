---
title: "some advise for a newb?"
date: 2008-03-20
forum: Security Discussions
---

### Post by applehead on 2008-03-20
Hi.
I'm still very much a newb and I've only just started taking security precautions.     (got firestarter, noscript and adblock)
I can't do all the checks like checking binaries etc, one thing I've noticed though is a lot of network activity. There always seems to be a lot of 'Received' action even though I'm not doing anything. I'm not on a home network or anything just a normal home cable connection to the internet.
What am I receiving?
Is this normal?
Is some one doing something with my machine? how do I know?

---

### Post by Dr Small on 2008-03-20
You could check the packets with Wireshark or ettercap to be sure.

---

### Post by applehead on 2008-03-20
Thanks.  I've had a look at wire shark, installed it and had a look at the help pages.  I've made a rough guess that it may be a bit quicker to do a fresh install of ubuntu than figure out how to use it.
I just wonder if my received activity is normal.

I've attached firewall and system monitor screenshots while typing this post.

---

### Post by spudratic on 2008-03-21
ok I'm a new user so take this with a grain of salt.I use to use firestarter but seemed to be getting hit with a lot of activity on my router so I switched to guard dog gui(be warned guard dog locks it down tight and you will not have net access to the web if you do not read the guide at the guarddog web site)Ounce I switched my router activity is back to normal.Now I don't know what the problem was,either the out of the box iptable settings  or firestarter like I said I'm new but guarddog seems much better as far as activity.At least now I don't have packet activity when I lock everything down.Before with firestarter I would still receive packets while the firewall was locked and firestarter it self would show the packet activity along with iptraf.Quick hint for guarddog for your web browser so you can read after install.there are two zones I guess we can call them that local and internet these options should be checked in both.first go to network and check dns then go into file transfer and check http.remember in both local and internet.Also the last tab has a turn off the firewall check box in case you get into trouble and can't connect.like I said I'm new to this but I like guard dog more than firestarter.also one more hint if you torrent make sure you add a udp rule for port 6881besides the two rules you add for the ports you want to open so you can connect to the trackers and also two protocals in file transfer both named bittorrent something can't remember right now but you will see them they are both together and remember both zones must be checked local and internet.Also for your custom port rules you need to check the boxs in use defined at the bottom of the protocol list in local and internet.this is as far as I have gotten with this program but seems to work fine even though I get an error in the terminal when I start it.It ran fine until I had a small crash which set the desktop back to 2 panels instead of 4 rebooted and been getting errors on start up but it works fine.I found a thread that gives the answer to this problem I'm having to bad it's in french and google translation stinks for something like this,but you should not have this problem it was perfect till my little miss hap.well anyway this should get you started so you can do the basics on the web.

---

### Post by applehead on 2008-03-21
Thanks.
I got fed up, I've been having lots of effects problems so I decided to scrap the lot and do a fresh install of feisty, a bit extreme in hind sight.
I've got a stronger password, firestarter, noscript and adblock. Ive visited some port scanners which all say I'm fine and I'm still seeing 'received' activity in my system monitor just like before.  I suppose then,  that this activity was normal and re install was not needed :( 
oh well I'm gonna stay with feisty for a while and see how it does with compiz.

---

### Post by spudratic on 2008-03-21
like I said when I un installed firestarter  and installed guarddog all that activity was greatly reduced.fire starter is permissive when installed unless you lock it down and add your rules.guard dog comes this way and you have to open up what you want it just seems safer to me lol like I know what i'm talking about.I did the same thing you did reinstall the os lol actually I reinstalled it 4 times already lol but an install is easy on this os compared to windows and all the updates.the install comes naturally now and set up of what I want is even easier.


edit almost forgot lol this is the reason I posted a reply find a root kit scanner.I installed 2 from the package manager rkhunter and chkrootkit if you are worried you will need these rootkits scanners.Rootkits are a real pain on any os .these are run from the terminal so read up.

---

### Post by The Cog on 2008-03-22
Sorry you wasted your time reinstalling, applehead. A few points:

If you connect to the internet, you will get a background babble of received stuff. It wil be a mixture of packets addressed to you in error, addressed to the last user of your current IP address (I guess your address is dynamic), but mostly I reckon it will be attempts to hack you. Most of those hack attempts will be bots trying to hack windows computers.

On cable, I think it uses bridging between its customers so you also get all the broadcast packets that other PCs send such as ARP requests, netbios name announcements etc.

If your firewall says it's blocking these packets then don't worry - the firewall is blocking them. Even if you don't run a firewall, Ubuntu is safe (unless you installed a service yourself) because it's not running any public services that can be exploited.

The system monitor applet seems to have an "AGC" type mechanism. It seems to get more sensitive over a minute or two so that any level of traffic however small eventually reads near 100%.

---

