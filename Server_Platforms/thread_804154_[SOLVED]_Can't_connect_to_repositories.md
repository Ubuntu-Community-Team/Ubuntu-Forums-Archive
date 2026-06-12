---
title: "[SOLVED] Can't connect to repositories"
date: 2008-05-22
forum: Server Platforms
---

### Post by sparkyjoe34 on 2008-05-22
OK, so I have been following the tutorial on [HowToForge]("http://www.howtoforge.com/the-perfect-spamsnake-ubuntu-8.04-p2")
and I've gotten to the point of updating from the repositories but for some reason when I try to connect I get:
W:Failed to fetch [http://canonical.com/ubuntu/dists/hardy/release.gpg](http://canonical.com/ubuntu/dists/hardy/release.gpg)
could not resolve 'archive.canonical.com'

There are several lines that say this with some slight variances.

In the tutorial it said to Edit /etc/apt/sources.list. Comment out or remove the installation CD from the file and make sure that the universe and multiverse repositories are enabled. It should look like this:

```
vi /etc/apt/sources.list
```

#
# deb cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Release i386 (20080423.2)]/ hardy main restricted

#deb cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Release i386 (20080423.2)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

The thing is there is no difference in the file other than where it says "us" in the address on my file and the one on the site says "de". I tried replacing the "us" in the address with "de" and still a no go. So know I am wondering is my PC even connected to the internet? Is there a way to check from the command line or some other tool? Any help is much appreciated.

---

### Post by camccall on 2008-05-22
The easiest way would be to try pinging a couple of websites.  google.com, yahoo.com are good.

```
ping google.com
```
```
ping yahoo.com
```

And see if that succeeds.  If that does not work check the status of your network adapters using [ifconfig]("http://linux.die.net/man/8/ifconfig").  

If everything is okay there try ```
dig archive.canonical.com
``` to see if you can at least lookup the dns entry for the website.

---

### Post by sparkyjoe34 on 2008-05-22
No that didn't work. It returned:

ping: unknown host google.com

As far as the ipconfig thing I wouldn't know what to do with that. I'm a newb to the command line.

---

### Post by camccall on 2008-05-22
Okay, try running ifconfig and then copy and paste the output here.  All it does it show the status of your network adapters.

I'm guessing you are not hooked up to the network at this point.  Are you trying to connected using wireless or are you using a wired network.

---

### Post by sparkyjoe34 on 2008-05-22
I'm using a wired network.Could there be an issue with my router blocking it?
I ran ifconfig and it returned:


eth1    Link endcap:Ethernet HWaddr 00:b0:d0:06:63:79
        inet addr:192.168.0.100 Bcast192.168.0.255 
        Mask:255.255.255.0 inet6 addr:fe80::2b0:d0ff:fe06:6379/64 Scope:Link
        UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
        RX packets:11 errors:0 dropped:0 overruns:0 frame:0
        TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:4141 (4.0 KB) TX:bytes:1900 (1.9 KB)
        Interrupt:11 Base address:0xec00

lo      Link encap: Local Loopback
        inet addr:127.0.0.1 Mask:255.0.0.0
        inet6 addr: ::1/128 Scope:Host
        UP LOOPBACK RUNNING MTU:16436 Metric:1
        RX packets:8 errors:0 dropped:0 overruns:0 frame:0
        TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:748 (748.0 B) TX bytes:748 (748.0 B)

I have no clue what this all means. :confused:

---

### Post by unutbu on 2008-05-22
What do you get when you type
```

ping -c1 64.233.187.99
```

---

### Post by sparkyjoe34 on 2008-05-23
It returned:
ping: bad number of packets to transmit

---

### Post by kustomjs on 2008-05-23
what kind of router are you using?
if you using linksys you got to log into your router then go to Applications & Gaming then to Port Range Forwarding enter a name of app then go to start port of 80 end port of 80 then enter 192.168.1.X then hit the enable box on stop then at the bottom hit the save then it will reset your router and also go to sudo vi /etc/network interfaces to see if you either got dhcp or static setup then after that is all setup go to sudo vi /etc/hosts to see if you got ur name and ip address set correctly 

or go to sudo vi /etc/apt/sources.list and see this:[IMG]http://linuxloader.com/articlepics/howtos/kubsrv606/server43a.png[/IMG]

and hopefully you get it fix.

---

### Post by sparkyjoe34 on 2008-05-23
It is a linksys router. WRT45G I believe. 
Ok I loged in to the router admin panel, went to Applications & Gaming/Port forwarding and set the following:
Entered a name for App (didn't know if I was supposed to enter something specific here so I typed in server)
Start port:80
End Port: 80
IP address:129.168.1.5
Checked enable box
Clicked "Save settings"
I'm assuming the router reset itself :confused: I probally should have manually reset it just to make sure.
Verified static IP address in /etc/network/interfaces. So the IP address in /etc/network/interfaces has to be the same as the one entered into the port forwarding correct?

> go to sudo vi /etc/hosts to see if you got ur name and ip address set correctly Not really sure what you mean by this?
I had initially went to sudo vi /etc/apt/sources.list and uncommented all the repositories.

---

### Post by unutbu on 2008-05-23
sparkyjoe34, are you trying to set up a dynamic IP address using DHCP or a static IP?
What is the IP address of your router? Is it 192.168.0.1? or 192.168.1.1? or something else?
Please post the output to

```
cat /etc/network/interfaces
route
```

---

### Post by sparkyjoe34 on 2008-05-23
unutbu,

Let me just say first that i am a newb to all this command line and networking stuff so as of right now I would have a better luck trying to learn russian. I am slowly picking it up though. 
Having said that, I am going with a static IP. I read that if you are setting up a server then a static IP is the way to go. Is a static IP better than DHCP? Safer? Is DHCP easier to work with? I could defanitely use easier right now with the way this set-up has been going!

> Now you are setting your ip to 129.168.1.5.
Sorry for the confusion, it should be 192.168.1.5. I was typing that at 5:15 this morning prior to having coffee in my system. I just picked this as a random number for my static IP. Should it be something else or is that ok for my IP?

 
```
eth1 Link endcap:Ethernet HWaddr 00:b0:d0:06:63:79
inet addr:192.168.0.100 Bcast192.168.0.255
Mask:255.255.255.0
```
This information above was from last night. I have since modified my /etc/network/interfaces and as of right now my present IP address should read 192.168.1.5.

---

### Post by sparkyjoe34 on 2008-05-23
unutbu, I'm not at home right now but I believe the router control panel showed that my IP address is 192.168.1.1 and I believe the starting IP address to other PC's on my router is 192.168.1.100. I think that is right. Sorry if I am confusing you.

---

### Post by unutbu on 2008-05-23
I took a look at the guide you reference: [http://www.howtoforge.com/the-perfect-spamsnake-ubuntu-8.04](http://www.howtoforge.com/the-perfect-spamsnake-ubuntu-8.04).
It's quite complicated! The software you'll be installing each has a somewhat steep learning curve, so to take advantage of and maintain that server will take a good bit of knowledge. I don't want to discourage you, but I wonder if this is really what you want and also if there might be a simpler way to reach your goal. 

I don't even understand what a spamsnake is. Do you just want to filter spam from your emails?

---

### Post by sparkyjoe34 on 2008-05-23
> if there might be a simpler way to reach your goal
If you have any suggestions on a simpler way I'm open to suggestion. 


Spamsnake? Is'nt that a food dish from Europe? :)
I was just following(somewhat) that tutorial because I googled it.

---

### Post by kustomjs on 2008-05-23
don't forget to sudo vi /etc/hosts because that also controls your box because when you do this it should look like this:

127.0.0.1 localhost
192.168.1.5 name of the box

after that is done type in :wq to save it then do sudo sudo shutdown -r now to reboot the whole pc.

---

### Post by NateMan on 2008-05-23
The perfect server guide is nice. I highly recommend it. now about your ip address issue. there are three files you need to check, /etc/network/interfaces, /etc/hostname, /etc/resolv.conf. Those all need to match for your static ip address. Go to the perfect server guide and look at the format for setting it all up and try to match it, but replace it with your 192.168.1.5 address. Remember that everything except your subnet mask needs to be 192.168.1.something. DHCP is easier, but it can change with could throw your whole server out of wack. If you can't get it figured out posting those files would be helpful.

---

### Post by sparkyjoe34 on 2008-05-23
kustomjs, 


> after that is done type in :wq to save it then do sudo sudo shutdown -r now to reboot the whole pc.
Can't you just /etc/init.d/networking restart(i think that's the command)? I'm not trying to second guess you I'm just going by what I read in the tutorial that I was following online. Will either one work or is one better than the other?

---

### Post by NateMan on 2008-05-23
yeah networking restart should work just fine, but if it doesn't then a reboot may be necessary. Changing the hostname however won't be restarted by the networking restart command, there is a seperate one for that file.
/etc/init.d/hostname.sh start is the command. It can be found in this guide: [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts) . I would use this guide for a setup, not the spamsnake one. In fact due to the issues you are having, I would recommend going back and setting the whole thing up from the beginning and follow those directions EXACTLY. If you have any questions about what you are actually doing, I'd be glad to help. Seems like your first one went up with some mistakes, and the issues your having now may only be the tip of the iceberg.

---

### Post by sparkyjoe34 on 2008-05-23
NateMan,

> Changing the hostname however won't be restarted by the networking restart command, there is a seperate one for that file
Gotcha! I think I am going to take your advice and start from the begining. A whole new re-install is probably best bet then? 

> If you have any questions about what you are actually doing, I'd be glad to help 
Thanks so much Nateman! I really appreciate your help. I really want to not only be able to set it up but also learn as much as I can about it so that I will be able to(someday) help others the way everyone has helped me. Thank you too kustomjs and unutbu for your help as well. :)

---

### Post by NateMan on 2008-05-23
Yes that sounds like the best idea. Stay away from that spamsnake guide, kinda too specific. Start with a more general install. If you want some sort of gui to config with later, try webmin. Its good for new users and its easy to install. There's a .deb on [www.webmin.com](www.webmin.com). just copy the link location and wget it. Do that last however. Happy serving!

---

### Post by unutbu on 2008-05-23
sparkyjoe34, if you follow the directions at
[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)
you will be installing the server version of Ubuntu 8.04. By default, this version of Ubuntu comes with no graphical user interface. This is meant for people comfortable working from the command line. This does not mean you can not install additional packages to make it more like a desktop, but this is not an appropriate out-of-the-box solution for newbies.

---

### Post by NateMan on 2008-05-23
I don't think he actually wants a full graphical desktop. I am confident he can handle the guide. Its very straight forward. Only like 3 lines have to be changed to your ip address and your hostname. I say let me try to setup a cli server. Some of my fondest computing memories are over cli... Webmin will make everything after he's done easy too. Don't scare off the newbs, let em learn and guide them.

P.S> I was able to do the perfect server guide even while I was quite green. (albeit a much older version, which was worlds harder than the current one.)

---

### Post by unutbu on 2008-05-23
I think the problem here is that the OP has not made clear exactly what he is trying to accomplish. 

Does he want a GUI desktop with a network connection and a spam filter?

Or does he want a server with
```
    * Web Server: Apache 2.2 with PHP 5.2.4 and Ruby
    * Database Server: MySQL 5.0
    * Mail Server: Postfix
    * DNS Server: BIND9
    * FTP Server: proftpd
    * POP3/IMAP: Maildir format and Courier-POP3/Courier-IMAP.
    * Webalizer for web site statistics

```

My warning was not meant to discourage. It was simply to prevent everyone involved from going through a lot of work for an end product which was not what was truly desired by the OP.

---

### Post by sparkyjoe34 on 2008-05-23
Sorry guys, I guess I should have stated what my main goal was here as you have mentioned. 
Here goes: In my spare time I design web sites. I have set up one for my wife and I want to be able to do my own here in the near furure. I want to have a testing server for this purpose. Once I edit those file upload them via FTP to my sites. I know this can be done on a regular desktop with the addition of Apache,php,MySQL,etc.. and I have done that with my laptop before but I hate to use that extra space on my laptop for that purpose. I also want to set it so that I can store all my movies, pics, music, files, etc.. and access them from my laptop without the need to (again) keep them on my laptop. Not to mention the fact that my wife and I both go to college and there you have more files to clutter up and slow down my laptop. I've also heard of people setting up a connection for family members to access those files from wherever they are. 

> Does he want a GUI desktop with a network connection and a spam filter? I'm not sure what this would even be used for as I have never done anything like this before.

Also, I want to have the satisfaction of knowing that I can set up my own server and not pay an arm and a leg for the software(die :mad:windows!). Having spilled my guts, what do you guys think is going to be the best route to take?

---

### Post by NateMan on 2008-05-23
sounds like that would be a good guide. I certainly use mine to setup and test different website ideas. Very simple to do. It didn't appear you were too worried about the spam filtering, besides the perfect server setup includes spamassassin anyway. Good luck with the install.

---

### Post by sparkyjoe34 on 2008-05-23
> It didn't appear you were too worried about the spam filtering
To be perfectly honest with you I dont know what the spam filtering would be for. Would that be used if I were to set up some sort of a Mail Server? I wouldn't think I would need that if I were only using it to run a test server and to allow access fom family members correct? Forgive me, I know these may sound like dumb questions.

---

### Post by NateMan on 2008-05-23
Well there's system mail, but on mine its not on the net. I don't use my servers mail, just to check for errors every now again. That guide will help you setup what you want, but to get to it from the outside world you'll have to forward ports in your router. There are no stupid questions if you don't know. Although I strongly recommend researching it also, as well as ask questions. You will basically be getting a good server base and a webserver for your use.

---

### Post by sparkyjoe34 on 2008-05-23
Ok so when I re-install Ubuntu tonight do I need to do anything like port forwarding with my router in order to access the repositories?

---

### Post by sparkyjoe34 on 2008-05-24
OK so this is where I am with the server set-up since following the  [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts) tutorial. My last step on page 6, step 17 before running into a snag was this:
> Next we install PHP5 and Ruby (both as Apache modules):

```
apt-get install libapache2-mod-php5 libapache2-mod-ruby php5 php5-common php5-curl php5-dev php5-gd php5-idn php-pear php5-imagick php5-imap php5-json php5-mcrypt php5-memcache php5-mhash php5-ming php5-mysql php5-pspell php5-recode php5-snmp php5-sqlite php5-tidy php5-xmlrpc php5-xsl
```

Now the problem that I am running into is after running this command, The screen returns:
> Reading package lists... Done
Building dependency tree 
Reading state information...Done
Package php5-json is a virtual package provided by:
 php5-common 5.2.4-2ubuntu5.1
You should explicitly select one to install.
E: Package php5-json has no installation candidate
I'm not quite sure what to do about this. Any suggestions? Is it saying that I need to apt-get a specific version?

---

