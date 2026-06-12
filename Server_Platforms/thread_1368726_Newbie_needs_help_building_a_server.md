---
title: "Newbie needs help building a server"
date: 2009-12-31
forum: Server Platforms
---

### Post by outdoorwiz.com on 2009-12-31
So, after countless days of trying to figure it out on my own here I am asking for help. I am on a mission of building a website which is a great challenge on its own, but it wasn't enough so I thought that I need to host it myself. Not only that but I want build the server myself too. You would probably say that I am crazy, but well even if so it is an appealing challenge to me. I am a so called newbie and I hope I will get some help here. 
I am not asking for help with web design since I am already paying someone, but I am asking for help building a server and hosting it in a professional manner with the Ubuntu platform. 
So, if anyone is up for the challenge I will be more than grateful.
Thank you.

---

### Post by BkkBonanza on 2009-12-31
You're not crazy - people do this all the time. Just try searching the posts here; this topic comes up daily.

> **outdoorwiz.com said:**
> hosting it in a professional manner 


Well, IMHO if you mean this, then just pay a small monthly fee and host it on a server in a data center. A VPS account gives you every you have at home/office and much better connectivity and reliability. You won't save much or any money running it in your own place.

---

### Post by outdoorwiz.com on 2009-12-31
What if I want to do it myself? What would that involve? And do you have any helpful documentation on this forum?

---

### Post by HighCommander540 on 2009-12-31
> **outdoorwiz.com said:**
> So, after countless days of trying to figure it out on my own here I am asking for help. I am on a mission of building a website which is a great challenge on its own, but it wasn't enough so I thought that I need to host it myself. Not only that but I want build the server myself too. You would probably say that I am crazy, but well even if so it is an appealing challenge to me. I am a so called newbie and I hope I will get some help here. 
I am not asking for help with web design since I am already paying someone, but I am asking for help building a server and hosting it in a professional manner with the Ubuntu platform. 
So, if anyone is up for the challenge I will be more than grateful.
Thank you.

I do all of my own hosting myself. This is the exact thing I started with. Its not crazy at all.

> **outdoorwiz.com said:**
> What if I want to do it myself? What would that involve? And do you have any helpful documentation on this forum?

Um, a **** load of money. You would need to get a really good internet connection that has good upload (which you have to pay a lot for). A really good system, because you need to be able to serve up the info properly.

Like everyone else said, its usually cheaper to start with just buying space.

---

### Post by outdoorwiz.com on 2009-12-31
I know it is cheaper and easier and all that but I have the money, I have the time and I want to learn. I would appreciate it if you share with me what kind of hardware I would need in the first place and then all the rest of the good stuff. I am looking to buy a DS 3 Internet connection do you think this will be sufficient.
I want to buy all the components for the server and put them together myself too.
Thank you for the response. :guitar:

---

### Post by volkswagner on 2009-12-31
If you want a professional grade server, things to consider.

Run your severs inside your own VPS, this way you can have separate mail, web, database, file, etc. servers.  With this approach maintenance is easier.  Also failures won't halt the entire system.

Consider failover and redundancy.  Backup internet connection, routers, power supplies, battery backup, etc.

Starting with server case with two power supply's, multi CPU MOBO or multi core cpu, and lot's of Ram for all your VPS's is a great start.

---

### Post by outdoorwiz.com on 2009-12-31
It seems like I have a lot of reading to do. Is there specific documentation that you think will be helpful. I am a but naked newbie :confused: when it comes to this stuff. 
As far as the hardware for the sever, will every hardware component work with ubuntu?
I am working on buying a custom configuration. As soon I am done with it I will post it here to ask for approval.  

Thanks again:guitar:

---

### Post by lightsabersetc on 2010-01-02
nearly every piece of h/w will work with ubuntu. There is no specific documentation that I know of, but here are a few links to ponder on, they helped me out a lot during my setup:

[http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server](http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server) - DNS, NAT, DHCP, iptables setup
[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588) - PROFTPD server setup
[http://principialabs.com/beginning-ssh-on-ubuntu/](http://principialabs.com/beginning-ssh-on-ubuntu/) - SSH setup
[http://www.linux.com/learn/tutorials/33766-sysstat-howto-a-deployment-and-configuration-guide-for-linux-servers](http://www.linux.com/learn/tutorials/33766-sysstat-howto-a-deployment-and-configuration-guide-for-linux-servers) - system monitoring
[http://www.easy-ubuntu-linux.com/apache-ubuntu-install.html](http://www.easy-ubuntu-linux.com/apache-ubuntu-install.html) - Apache setup
[https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer) - Mail server setup

Setting up a server is a long process and involves a lot of googling.

---

### Post by dinuzz on 2010-01-02
this is where everything gets started.... for a quick start, use an old computer which is not being used anymore.... download ubuntu server and install it and start playing around with it... for now, use apache, mysql, php, samba ftpd etc.... the basic stuff, just to get into the linux world so you see how things work.... use the LAMP option when u install the ubuntu server, that everything you needs, works pretty much out of the box.... administrating a high end IT infrastrucutre can't be learned over night, but with this approach u will enjoy working with linux... any questions u have during this process, this is the right place to get the answers....

good luck

---

### Post by WTF_Shelley on 2010-01-02
you will need a rack type server case, as most datacenters charge by the U high a desktop pc will be a cash sink. quad core, loads of ram, gigabit nic and a raid 1 or 5.  other then that all you will need is an ubuntu cd and about 6 - 8 weeks of hitting the books/google.  Good luck bro when the sites up post us a link

---

### Post by tomdagreek on 2010-01-02
lots of good replys...
i second the opinion of getting a cheap comp,download and burn a ubuntu server disc and get ur feet wet.
ubuntu is a godsend for ppl like u who want to do it urself.
any comp or server will do the job that u need unless u plan on taking the internet by storm:lolflag:

---

### Post by CharlesA on 2010-01-02
You could always run a VPS, those are fairly inexpensive from what I've heard.

Alot easier then renting space in a colo facility too.

---

### Post by Kiwi76 on 2010-01-03
[Here's a similar thread.](http://ubuntuforums.org/showthread.php?t=1352037)

[Here's my response to it (and to yours).](http://ubuntuforums.org/showthread.php?p=8576775#post8576775)

[quote=Kiwi76]I'm running my own website off of a server at home (using the setup in the signature).

My website's existence is actually a response to when the website (community forums) I was running for others (who neglected it) went down, and the community had no place to go. I wanted to continue to run a community, so I had a few choices.

1. Create some "free forum" type community. This is definitely not my cup of tea.

2. Get my own hosting and domain and start my own community forums.

3. Jump into Ubuntu, with little experience (anything I've learned was through trial and error, ala, by messing stuff up, though I suppose that's the best way!) in Ubuntu, domains, running my own server, etc., etc., and have my own website and community forums. I knew stuff in each area, so I wasn't clueless, but I was far from a well versed veteran or professional.

I went with the last, and while it's only been a few weeks since I've done it, I'm totally glad I did.

I have a static IP address (surprisingly, since I am not paying for a business class connection). It has changed only two times since I signed with them, and those changes were because the router/modem was replaced once, and then we moved the second time.

My upload speed is pretty okay, but far from phenomenal from what a server would really need.

[IMG]http://www.speedtest.net/result/666191321.png[/IMG]

These results are apparently twice that (upload and download) of what this ISP averages though. This still has little on the 20+Mbps of some cable companies (although I prefer DSL, and my connection actually is rated at ~20Mbps downstream, but my connection also feeds four televisions and multiple PCs, and also some Xbox360s, so there's alot being split up, as it's AT&T's U-Verse package).

As you cans see, it's pretty average, but the traffic is very low, and I don't foresee it ever going very high, so it works (said low traffic so far gives feedback that the community forums on the server are nearly instant).

I'm using pretty power efficient hardware too (these 45nm Core 2 Duos, especially underclocked, have you seen their low power draw!?). That reminds me, to the one who said Intel's draw alot of power, yeah, in the old days of the Pentium 4/D at high clock speeds. The Core 2 Duo is a completely different matter. I don't know about Core i7s, which apparently use more, but I'm not using one.

Most importantly, I ***wanted*** to do this. After factoring in costs, time spent, power used and electric bulls, upload speeds, managing it yourself, etc., etc., it's often not practical to run your own at home. You'll probably, at best, break even with what it'd take to just buy hosting, but I ***want*** to do this. The box would had just sat otherwise anyway, and I convinced myself the hardware was too good to do that too (and I didn't want to take the loss and sell it).

Site's like the following have been invaluable to me.

[http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/)

[http://www.boutell.com/newfaq/creating/shouldihostmyown.html](http://www.boutell.com/newfaq/creating/shouldihostmyown.html)

That, of course, doesn't include Google for the many searches I did, and the Ubunutu Community itself, among many others.

So, here's my take. If you ***really*** want to try it, then go for it, but if you need reliability for a true production website, don't do it at home unless you're a professional. By the sounds of it, because you're even considering asking to begin with, I'd actually advise you to try it at home if you wanted, but that was if you didn't already have real hosting with a website(s) already going. Since you do, just stick with it and don't risk the existing sites. Maybe try toying around with local sites on an LAN with it? If you get versed enough, who knows, maybe you'd want to move to that.

Just remember, the bottom line is, you won't really save time, money, etc., and it is a risk, but if you want to do it, I say go for it. It's been a huge learning and fun experience for me so far.

Sorry for the long post, but I hope this help anyone who comes across this thread who may be asking themself the same thing.[/quote]Countless servers out there are running on "old and slow" hardware with "normal" internet connections. Go ahead and try if you want. If you use a separate PC and go in ready for and expecting things to go amiss, and have patience to deal the problems that ***will*** crop up, then it can be loads of fun.

---

### Post by outdoorwiz.com on 2010-01-03
Thank you for the information! Does anyone know how a cable internet connection compares to a shared or VPS server connection?
Thank you :guitar:

---

### Post by CharlesA on 2010-01-04
I'm not sure, but I'd figure it would be pretty bad. Especually since most VPS servers are hosted at data centers with pretty decent connections to the backbone.

---

### Post by slooksterpsv on 2010-01-04
Well... some cable is a shared bandwidth in areas:
E.g.
10 people live in the same area (same street block)
5 have cable with the highest speeds - lets say 8Mb
The maximum current bandwidth pipe is - 30Mb

If all 5 are trying to download a large file, someones internet speed will slow down - it sucks - I used to have cable and used to work for a local Telecommunications company that provided DSL - they bought the local cable company as well soon after I started and showed us what cable connections are like for specific areas - in that respect.

When I had cable I had their lowest speed 25.6KB/s and the maximum download speed I could attain was 11KB/s - even with high bandwidth servers like [http://speakeasy.net/speedtest](http://speakeasy.net/speedtest)

As for the server: I ran my own, using Ubuntu it's not as bad as you may think. I ran apache2, mysql, php, streaming music server (via gnump3d), on a 512Kbit upload speed. It worked quite nicely.

---

### Post by outdoorwiz.com on 2010-01-04
How would a T1 or T3/DS3 connection compare then? :confused:

---

### Post by BkkBonanza on 2010-01-04
Well, for starters it would cost a lot more.

T1 1.5 Mbps
T3 44.6 Mbps
Typical good quality VPS account, 10 Mbps or more (shared).

Bandwidth in a data center is always probably going to cost less than having a line dropped at your place.

You seem to be going around in circles here. What you want to do first is figure out how much you need. Maybe explain that here and people can suggest what type of BW you should be looking for. If you're just starting out and don't have a busy site yet then don't even waste your time thinking about this until you have the hands on experience of what your site uses. Otherwise you're just going to be wasting your money.

See here, [http://www.t1shopper.com](http://www.t1shopper.com)

---

### Post by UbuKunubi on 2010-01-04
For what its worth, i also run my own website.

I also had never done this before, and have a budget of £0!
This is how I've done it:
First I installed virtual box ose, and set up a virtual machine with 256 MB of ram with a 4gb virtual drive image, and configured the network connection to host interface (this means no messing around with internal bridges, it simply hooks into the real ethernet card), and then installed ubuntu 8.04 desktop version.

I then made sure that remote desktop was disabled, and then got all the updates.

With that completed I then used google to find how to install apache2.
Luckily my router allows auto updating of dynamic IP address, via dyndns, so thats one headache out of the way.

Using the desktop version means I can jump straight into the virtual server and update my site with open office, text editor or whatever I like. 

The performance hit is very minimal - with all programs shut down except a few python programs that update pages from templates the CPU usage of the vm is around 4%!
I should add that I run this on a 1100Mhz celeron with just over 2gig of ram - far from cutting edge - but I'm still able to play alien arena, etc with no noticeable issues.

To get files in and out of the vm I simply use skype to either send cut and paste selections to transfer files.

While Im on a domestic adsl connection, and the upload speed is around 50kps, my site has around 15 -35 visitors a day and I never notice any dip in internet connection speed, unless someone is uploading a massive image to the site.

you can view my site at [http://fredtechno.dynalias.org/](http://fredtechno.dynalias.org/) which has been up for around 6 weeks and is a constant work in progress, mainly as a hobby, and also to keep in touch with friends and family via my chat room.

If you need more information simply get back to me.

All the best,
Ubu

---

### Post by BkkBonanza on 2010-01-04
@UbuKunubi,
I congratulate you on running your server this way. I use VirtualBox myself for testing sites before I upload them to my real server. It works very well. Though I have to chuckle at using Skype for file xfer.

I'm surprised you would use Host mode networking though as Bridged mode should be easier to use. Your VM would just get an IP from your router the same way as your desktop does and act the same as another machine on the LAN. No port fwds on the desktop or other funky stuff.

If you run that way then you can use Nautilus to copy/move files to your VM just by specifying ssh://vm_ip_or_name in the address bar. I have a bookmark to my server that makes it very easy. This works well even when I access my real server 4000 miles away. 

Another way that works nicely is using sshfs (ssh filesystem) to mount a directory from your VM into your desktop filesystem. Then it can be accessed just like any other directory on the desktop. 

But you are right - you can run your web site in a VM and the only thing limiting it for low traffic sites is the upload speed of your connection.

---

### Post by UbuKunubi on 2010-01-04
> **BkkBonaza said:**
> @UbuKunubi,
I congratulate you on running your server this way. I use VirtualBox myself for testing sites before I upload them to my real server. It works very well. Though I have to chuckle at using Skype for file xfer.

I'm surprised you would use Host mode networking though as Bridged mode should be easier to use. Your VM would just get an IP from your router the same way as your desktop does and act the same as another machine on the LAN. No port fwds on the desktop or other funky stuff.

If you run that way then you can use Nautilus to copy/move files to your VM just by specifying ssh://vm_ip_or_name in the address bar. I have a bookmark to my server that makes it very easy. This works well even when I access my real server 400 miles away. 

Another way that works nicely is using sshfs (ssh filesystem) to mount a directory from your VM into your desktop filesystem. Then it can be accessed just like any other directory on the desktop. 

But you are right - you can run your web site in a VM and the only thing limiting it for low traffic sites is the upload speed of your connection.

The main reason is resilience: once set up how i liked I took a snap shot of the VM disk image, so if anything goes wrong I delete the current snap shot and revert back to the old one - it takes around 7 seconds [note to self:check remote desktop is disbaled!].

Ubu

---

### Post by CharlesA on 2010-01-04
> **UbuKunubi said:**
> The main reason is resilience: once set up how i liked I took a snap shot of the VM disk image, so if anything goes wrong I delete the current snap shot and revert back to the old one - it takes around 7 seconds [note to self:check remote desktop is disbaled!].

Ubu

That's gotta be handy. I used that feature a lot when I was testing a script of mine (one that installs all the crap I use: ssh, samba, etc and configures it)

---

### Post by Mart on 2010-01-04
Start small and work up.  Your cable or dsl connection will work fine for a fledgling site (Provided they permit it). Use a dynamic dns service like dyndns.com that can easily be setup through a router. Setup a simple server as a vitural host or on an old workstation.  There are plenty of howto docs on this at howtoforge.com. Turnkeylinux.net also has virtual servers setup that you would configure for your environment.  

That will get you feet wet then you can look at things like redundancy and increased bandwidth. 

Make many backups because you are going to screw something up it is part of the learning process and the fun of doing it yourself.


Mart

---

