---
title: "Linux OS protecting windows desktops"
date: 2019-01-07
forum: Ubuntu, Linux and OS Chat
---

### Post by axldavis2012 on 2019-01-07
Hello me n my parents work from home we All use only Linux desktops laptops etc for personal. now for work they will now allow us to install a working anti virus or windows defense it's all disabled and they have their spyware now we got a virus from a rootkit and we got another virus from within the company wide email n one got it first n checked it and that one got the virus n then it traveled through our home network onto all devices windows and our Linux operating systems (Linux was fine couldn't install exe files but downloaded I removed them). We all had to since he removed into our desktops for windows the company if this happens again we are responsible for the computers and the damages done to them and and software and to anyone else's computers (clients and such) since we remote in to theirs and we download files n they upload to use etc. The company said we can not use any antivirus because it blocks their spyware n I can't install due to admin privileges are revoked most of all settings are on all of them. My question is is their away to setup wither my Linux server since it's currently my router also (openSSL). To make it scan all traffic and packages downloaded from the windows computers and protect them from viruses and malware and the spyware all windows PC's are connected into other routers that all lead to the Ubuntu openvpn and openssl server it doesn't have to be Ubuntu it can be any version of Linux I'm well learned in Linux OS with cross platforms if so please help point me in right direction.

---

### Post by 1clue on 2019-01-07
First thing, you need to clean everything up. I can't help with the Windows side of things, and it seems like you most likely didn't get an actual compromise on Linux. Personally every time I have had an issue I feel uncomfortable without completely wiping every system that was touched. It's the only way you can be sure.

Your company is responsible for their viruses, and their equipment.  You can however isolate your equipment from theirs. If you are required  to work on your hardware then insist that they give you a VM installed  the way they want. You can cite the damage they did to your home network  as justification. Have them set it up so the VM dials the company VPN and runs all traffic through their VPN, including the Internet connection. They will like that because it gives them complete control.

You should consider segregating your network, physically. Your work equipment on one network, and nothing else on that network. That equipment can only go through the VPN to your work, and should only use their Internet. Your Linux systems, your TVs, phones, printers, tablets, wifi, whatever else should go through your normal connection.

While you could possibly load something like dd-wrt on your wifi router, I personally have had bad experiences with that OS. For the record though, those experiences were 10+ years ago.

What my scenario requires is a router with:
[LIST=1]
[*]At least 3 network cards (NICs)
[*]Each NIC must be able to be isolated from all others.
[*]One is your WAN (Internet)
[*]Two is your work network
[*]Three is your home network.
[*]You need to be able to set firewall rules between all three networks.
[*]It would be good to have something fast and big enough to handle IDS/IPS. (intrusion decection system/intrusion prevention system)
[*]You need to consider your current and likely future bandwidth.
[*]It may be interesting to you to have a system fast enough to be a VPN endpoint, not for your work but for remote access to your home system. It's unlikely your employer will allow a router-to-router VPN to their network.
[/LIST]

You could take several approaches for router software:
[LIST=1]
[*]A Linux box with Ubuntu Server
[*]A Linux box with pretty much any other distro.
[*]A Linux box with a firewall-specific distro.
[*]pfSense, which is based on FreeBSD and has commercial support.
[/LIST]

Possible hardware:

[LIST=1]
[*]A hardware appliance with Linux or pfSense on it preinstalled, with paid support. (There are many) This would amount to buying a commercial router.
[LIST=1]
[*]Ready to go, plug it in, it works after some amount of configuration.
[*]Commercial support often comes with the system.
[*]Comes with a manual.
[*]Probably has a GUI or web interface to configure.
[*]Costs more than a bare Linux box, unless you consider the time to learn it all.
[/LIST]

[*]A small business router from Cisco or wherever. May not be Linux or FreeBSD.
[LIST=1]
[*]Same as above for features and support.
[*]Costs much more than a bare Linux box.
[/LIST]

[*]An old desktop system. But not too old.
[LIST=1]
[*]Possibly lowest startup cost, only a couple NICs
[*]Same as installing Linux or pfSense and learning to configure it.
[*]Probably eats a lot of electricity compared to newer devices.
[*]Possibly noisy and hot compared to newer devices.
[*]Possibly already on the edge of failure due to power surges and wear.
[*]This is my least recommended approach, unless you intend to use it to get an idea what you want before moving on to something else.
[/LIST]

[*]A new low-power solution designed specifically for routing tasks.
[LIST=1]
[*]This is what I did. Costs money and time.
[*]Likely does not have a GUI.
[*]Likely faster and uses less power than a desktop or laptop of any age.
[*]Hardware designed for routing is usually top notch. More on that later.
[*]May not have a way to get a keyboard or monitor attached.
[*]Mine is all-in around USD $1100.00. Mine is likely more than you want.
[/LIST]

[*]A new low-powered desktop system.
[LIST=1]
[*]Probably cheaper than hardware designed for routing.
[*]May be adequate.
[*]Need to be careful about your hardware, as it pertains to routing.
[/LIST]

[*]Your existing wifi router using something like dd-wrt.
[LIST=1]
[*]If you go this way, it will likely be even cheaper than the old pc approach.
[*]You're limited to what the router can do.
[*]They tend to use bargain NICs and CPUs
[*]Extra functionality makes them slower (true for everything, but this system is likely unable to keep up if you get carried away)
[*]If your router has poor support with dd-wrt or whatever, then you are likely stuck with the bugs for years.
[/LIST]
[/LIST]

Comments on hardware in general:
[LIST]
[*]The more things you do with routing, the slower your router is.
[*]With routing, CPU is not as important as latency.
[*]Bargain NICs (e.g. Broadcom, Realtek) handle the bare requirements of Ethernet but usually handle most of the functionality in the driver. Meaning your CPU does it.
[*]A good NIC (e.g. an Intel NIC with the "igb" driver) does almost everything in the network stack by itself. Your CPU handles routing and firewall rules, and almost nothing else.
[*]Don't confuse a router with a switch. Switches have hardware which makes it virtually impossible for non-switch hardware to be as fast.
[*]Real router hardware is designed to have fast throughput from NIC to cpu to NIC. You can't see this in specs but you likely will in benchmarks.
[*]I have a 600w i7 system and a 40w Atom system. The atom is designed for network tasks, but both have been configured as Linux routers. The atom is every bit as fast at networking as the i7.
[*]ECC memory is a good thing. It lets you leave your router on longer without fear of instability without knowing about it.
[/LIST]

Hardware you might find interesting.  I don't work for any of these companies, but I think they're good for clicking around.

[LIST=1]
[*][https://www.supermicro.com/products/motherboard/Atom/X10/A1SRM-LN7F-2758.cfm](https://www.supermicro.com/products/motherboard/Atom/X10/A1SRM-LN7F-2758.cfm)   This is what I bought.
[LIST=1]
[*]This is NOT like an atom from a desktop or laptop. 8 cores, support for encryption and compression in hardware.
[*]Up to 64GB ECC memory, but can take non-ECC too. I have 16GB ECC.
[*]CPU has 20W TDP. System has 100w supply, it uses more like 25-30w under normal circumstances, maybe 40 when I'm working it.
[*]7x Intel NICs.
[*]It has an ASPEED video card, which is a service processor and designed to work from a rack. This system has never had a keyboard or monitor attached, everything including power up, power down, inserting CDs or USB sticks can be done from your desktop system.
[*]People who manage server rooms tend to like service processors, but there is a security concern if you don't know how it works and don't set up for it correctly.
[*]Some Linux people freak because it's a service processor, which has a closed-source ball of code in it, and you can't tell what it's doing from the board itself.
[/LIST]

[*][https://www.supermicro.com/products/motherboard/Atom/](https://www.supermicro.com/products/motherboard/Atom/) is SuperMicro's list of Atom boards. Look at the c3000 series stuff, it's at the top.
[LIST=1]
[*]This is what I was hoping for when I bought my board, but this stuff wasn't out yet.
[*]Support for handing a NIC off to a VM directly without configuring it in the host OS. I really wanted that.
[*]Better support for 10GBPS ethernet.
[*]Up to 16 cores.
[*]More SATA3 ports and USB3.
[*]You might have noticed I like SuperMicro stuff. They have a lot of my money.
[/LIST]

[*][https://www.netgate.com/products/appliances/](https://www.netgate.com/products/appliances/)
[LIST=1]
[*]These are pfSense appliances.
[*]They come with support.
[*]They are tuned specifically for the hardware on the board. So higher performance than you're likely to get if you install something yourself.
[*]They have decent hardware designed for routing.
[*]Be careful if you want something heavy like VPN or IDS/IPS, especially if your connection is fast.
[*]These systems should be able to run Linux fine, but you're paying for pfSense so maybe not economic for Linux.
[/LIST]

[*][https://mikrotik.com/product/](https://mikrotik.com/product/)
[LIST=1]
[*]Never had one and never saw one. But they're cheap with some interesting claims.
[*]Seem to be popular in Europe.
[*]There are only a few outlets in the USA.
[*]They might also run Linux. I don't know.
[/LIST]
[/LIST]


One comment on server hardware: Some server hardware does not support a hibernate function. Supermicro is like that at least with the systems I've seen, but since they're server hardware you don't actually want them to sleep. They go into a low-energy state when the system is idle long enough.

Sorry for the book. Hope it helps.

---

### Post by 1clue on 2019-01-07
Um. I seem to have not responded to the purpose of your post. Linux box protecting Windows desktops.

There's not a lot you can do. 

[LIST=1]
[*]If your mail server is on Linux you can run an antivirus which is designed to catch malware aimed at Windows.
[*]IDS/IPS can help detect attacks on your network or malware striking inside your network and help isolate it. I'm not sure how much, I don't really use it. You can at least know it's happening.
[*]Good firewall rules for both ipv4 and ipv6 can help isolate your network for any ports you have exposed.
[*]If you get a good board with good hardware virtualization support, you can set up two security appliances in a row, say one Linux and one pfSense. Diversity like that tends to stop more intrusion.
[*]You can subscribe to blacklists which alter your firewall to disallow access to known malware sites.
[/LIST]

People go on about Linux being impervious to viruses. That's approximately true, but linux is vulnerable to malware just like any other operating system. There's plenty of Linux malware around, and there are definitely automated applications trying to find exploitable weaknesses in every Linux box on the net.

But what a lot of people don't realize is that much of the malware we get can't really be prevented except by a cautious user.

[LIST]
[*]Malware from a website is often written in a language that Linux browsers know. Meaning they're cross platform.
[*]Malware in a Word document or Excel spreadsheet is usually written in the language inherent to the document type. Linux apps execute that code.
[*]Phishing attacks (e.g. an email sent to you apparently from your bank) are trying to convince you to click on a link and then enter information which the attacker can then use to steal from you.
[/LIST]

The biggest security tool we have is between our ears. There is nothing you can do to prevent somebody who is not paying attention from clicking on a link and typing in their credit card or social security number.

I've been managing Linux systems for decades. Desktops, servers (public and private), VM hosts, VM guests and cloud systems. I have been owned more than once. If you're running a stock Linux distro right on the Internet with no firewall, then you will be attacked and, eventually, owned. If you run a stock Linux distro you may be owned for years and never know it. Most malware these days does not disable your system or initiate a kill-your-network denial of service attack. They may not even be interested in what's on your system. They'll use your system to attack some other system, and they'll do it in a way that won't alert you to their presence.

Running regular updates is important, but it's not enough. You need to learn about security best practices, learn about security tools available on whatever operating system you use, and integrate them into your life. I hate to say it but this is not something you do in an afternoon. It's a moving target. Every time I set up a new system or set of systems, I review the current security best practices again. Because they change. I apply that knowledge to the specific environment and use case I'm installing for, and work from there. There is no black box "antivirus" app to protect you, not even for Windows or Mac OS. Windows is more susceptible to some other system on the network becoming infected, but they are by no means the only OS which is vulnerable.

---

### Post by 1clue on 2019-01-07
Here's the thing I do, that many people find a bit crazy.

[LIST=1]
[*]I configure my firewall assuming everyone wants in. 
[*]I limit outbound packets of unknown type. I assume nobody needs to make a connection from inside my network with an unknown packet type. 
[*]For servers that need to make connections with odd packet types, I'll make a specific rule for that type of packet on that type of server, after I get failures and decide it's important. 
[*]For individual workstations, laptops, TVs, tablets or phones -- or anything else -- is the same thing. 
[*]I configure each device as though it were on the open Internet. So double firewall, one on the device and one on the network.
[LIST=1]
[*]For laptops, tablets and phones (or other mobile devices) this may actually be true. Using the Internet from a public access point is risky. 
[/LIST]
  
[*]All my home appliances (TV, tablet, phone, blu-ray, blah blah) are on a network which is isolated from computers which do real work. They can get to the Internet but they can't get to anything important. 
[*]Computers for normal home use can see the printer and file server but not much else. Wired only.
[*]Every piece of hardware I or my family or friends own which may connect to my network is recognized by mac address by my dhcp server. Unknown mac address means you're on the guest network. 
[*]Computers for work hook up to an ethernet network which can get to printers and file servers and other work hardware, but nothing else can get there. You can't go from wifi to my work hardware. 
[*]The only inbound traffic is by VPN.
[LIST=1]
[*]The VPN is secured the best I know how. 
[*]It's not always enabled. 
[*]It only goes to work hardware. 
[/LIST]
  
[*]Server hardware with an IPMI interface (my SuperMicro atom board for example) has its IPMI interface on a separate network which is only physically attached to one system with direct ethernet. That system is not Internet connected, it only administers server systems. 
[/LIST]


Another thing: I advise that you stay away from hobby board hardware. Raspberry pi and the like are great for making robots or smart homes, but they are extremely bad choices for routers or file servers. I have several, including a stratum 1 time server. They're great, but not for routers.

---

### Post by 1clue on 2019-01-07
I need to also include the required reading:

[https://duckduckgo.com/?q=ubuntu+security+best+practices](https://duckduckgo.com/?q=ubuntu+security+best+practices)

is a good place to start. You can also say 'linux security best practices' or replace 'best practices' with 'checklist.' 

And for Windows and Mac OS you can do the same thing. Probably for android and ios too.

Gentoo and Arch distributions have very good security how-to's. But you'll need to get an idea about vulnerabilities and how they affect your system.

[https://nvd.nist.gov/](https://nvd.nist.gov/)
[https://usn.ubuntu.com/](https://usn.ubuntu.com/)

This is a difficult process for people to grasp sometimes. It's important to remember that Linux is not all one thing. It's a kernel, which is written by various people all over the world. And it's a bunch of software packages written by people from all over the world, usually not the same people although some people develop more than one software product. Each has a level of skill and a level of interest and a level of ... vigor?  How fast they write code, and how fast they correctly diagnose a problem.

CVEs are ... bugs. Vulnerabilities or stability issues. Each software product will have a list of known bugs and that package's developers will address those bugs as time passes. They will also write new code, and you can be certain that each time the code changes there is a significant chance that there will be fresh bugs. Hopefully fewer as the bug fixes come in.

Developers write code. Testers test the code. They catch some of the bugs and report them back. Eventually a new version of the software will be released.  This is all #upstream.

Distro maintainers and groups maintaining other packages depend on the #upstream dependencies. So testing is a gradual process, when it creates a finished product in, say, a library, then all the things depending on that library need to load that version and test.

Distro maintainers have to find a stable version of all the packages they want to support, and compile everything for the hardware the distro supports. Then more testing still.

At any point, CVEs can be discovered, then verified, and then tested by any package. The CVE database will help tell which versions on which distros are vulnerable and which have patches.

You, as a user, need to keep your system updated, but if you're a security person you need to keep in mind that it may be weeks or longer between when a bug is first reported to #upstream or any distro, and the time a patch is available. Much longer sometimes before it's applied to your system, depending on how vigilant you are.

nvd.nist.gov is a United States government database of software bugs.

---

