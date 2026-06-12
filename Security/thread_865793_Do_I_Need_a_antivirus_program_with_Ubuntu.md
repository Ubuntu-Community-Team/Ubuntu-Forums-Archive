---
title: "Do I Need a antivirus program with Ubuntu?"
date: 2008-07-21
forum: Security
---

### Post by Julia Dawn Mason on 2008-07-21
I am a new user of Ubuntu and I would like to know if I need an anti virus program. I have installed the firewall called Firestarter from the Applications list. If I do need anti virus, where can I find one that will work with Ubuntu?

---

### Post by perlluver on 2008-07-21
You don't really need anti virus, but Clam AV is available in Synaptic Package Manger, or Add/Remove Programs.

---

### Post by ad_267 on 2008-07-21
You don't need one unless you want to share a lot of files with Windows users and scan them for windows viruses. You also don't really need firestarter, which allows you to configure the firewall which is installed by default.

---

### Post by Julia Dawn Mason on 2008-07-21
I looked in the Add/Remove Program lists for the Clam AV and it is not in there. I then used the Synaptic Package Manager and found two packets that I marked for installing. I then installed but it does not show up any where that I can find it. There is no desktop icon for it or listed in the Documents folder .

---

### Post by perlluver on 2008-07-21
I'm not sure where it is, I am not in Ubuntu, I hope someone else can answer this.

Did you install the GUI for it?

---

### Post by rVan on 2008-07-21
hi actually you don't need antivirus in ubuntu. but as they said above if you want antivirus on ubuntu, you cant get clamav on your ubuntu.
you can get at this site [http://www.clamav.net/](http://www.clamav.net/)

---

### Post by perlluver on 2008-07-21
> **rVan said:**
> hi actually you don't need antivirus in ubuntu. but as they said above if you want antivirus on ubuntu, you cant get clamav on your ubuntu.
you can get at this site [http://www.clamav.net/](http://www.clamav.net/)

Clam AV comes with Ubuntu in the Repositories.  She/He can't find the Interface for it.

---

### Post by hyper_ch on 2008-07-21
(1) no antivirus is needed

(2) firestarter is no firewall

(3) IMHO in most cases you don't even need to worry about a firewall

---

### Post by Dr Small on 2008-07-21
> **hyper_ch said:**
> (1) no antivirus is needed

(2) firestarter is no firewall

(3) IMHO in most cases you don't even need to worry about a firewall
I think we get a thread about once a week that deals with this subject. Isn't that right, hyper_ch ? :D

---

### Post by damis648 on 2008-07-21
> **Dr Small said:**
> I think we get a thread about once a week that deals with this subject. Isn't that right, hyper_ch ? :D

Yep. Do not worry about antivirus. You will probably Never get a virus.

---

### Post by motang on 2008-07-21
> **Julia Dawn Mason said:**
> I am a new user of Ubuntu and I would like to know if I need an anti virus program. I have installed the firewall called Firestarter from the Applications list. If I do need anti virus, where can I find one that will work with Ubuntu?

Well like everyone said you don't unless if you are sharing files with Windows machines. I use AVG free and you get it [here]("http://www.grisoft.com/us.download?prd=avl"). Make sure you download the .deb file. It works fine for me for what I need to do, I scan files.  In order for you to update it you gonna have to run it in root mode, or you can open up the terminal and type in:
> sudo avg-update -o

That should update the virus signature file after you put in the root password.  Hope this helps.

---

### Post by Walter_d on 2008-07-21
Maybe this is a stupid question, but what about all this malware that has been listed on wikipedia ? ([http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware))
Are these worms still affective ? :-?

---

### Post by hyper_ch on 2008-07-21
> **Dr Small said:**
> I think we get a thread about once a week that deals with this subject. Isn't that right, hyper_ch ? :D
More than once a week ;)

> **Walter_d said:**
> Maybe this is a stupid question, but what about all this malware that has been listed on wikipedia ? ([http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware))
Are these worms still affective ? :-?
Well, compare that little list to the 70'000 or more known viruses for Windoze... and to cite from Wikipedia
> here is currently no known malware in the wild that is able to gain root access, without this root access the malware is not even able to register itself to be run on system startup, although may be launched from other userspace processes or a desktop manager.
Some of those may still affect current systems - although I doubt it as normally linux gets patched (while windows doesn't and hence needs antivirus).

---

### Post by aysiu on 2008-07-21
> **damis648 said:**
> Yep. Do not worry about antivirus. You will probably Never get a virus. More importantly, having antivirus installed won't protect you from a new virus anyway, should an effective-against-Linux one actually be developed.

---

### Post by cyclouno on 2008-07-22
woow woow woow !! This is getting way more interesting than I thought it would be. :)

Well I've got hardy on my PC. My parents use it for skype n firefox. Well the first & prime reason to move to Linux (especially ubuntu) was both due to GUI friendly n of course security constrains. They found Ubuntu much more interactive & easy to work with. 

Unless someone foolishly does this --> > su - root there ain't any virus trouble at hand - This is what I learned over time !! So forget anti-virus !!

But someone wise, please tell me if I'll have to do iptables or tcp wrappers for skype / firefox & some services ??

---

### Post by hyper_ch on 2008-07-22
well, if you're not going to install services you don't need to fiddle with iptables / firestarter / ufw... there's not really a point to it.

For firefox the noscript addon might be worth considering.

---

### Post by cyclouno on 2008-07-22
thnx hyper_ch...

her is what I wanna do.. I might have to do remote logins so i'll need sshd / vsftpd / vncviewer for me to do access my pc to troubleshoot problems that they might encounter !!

but > sudo nmap localhostshows quiet a few other services !! 

My real question is this.. let's say i don't have a firewall now.. so will anyone who knows my network ip & my ssh login or root login(& of course their passwords) be able to access my system??

---

### Post by hyper_ch on 2008-07-22
you don't do nmap on localhost ;)

but yes, if they know your ip and login credentials they can login... that's more or less the whole reason to have a ssh server - so that you can login.

What do you want to install ftp server on there if you have ssh server running?

---

### Post by cyclouno on 2008-07-22
ohh ya ur rit man.. jus findin wut n/w service ports r visible tat's all !! 

dude.. I nearly 4got tat I could do secure file transfer with ssh.. scp for secure file copy rit?? got it now.. will chuck vsftpd now!! so now I'll need vncview & ssh runnin... & nothing else !! so now tell me wutz with firewall..

---

### Post by cyclouno on 2008-07-22
I guess the answer is here... UBUNTU needs a firewall for sure & in my case since i'm gonna run daemons, i'll need one for sure !! 

The site below clearly says why ubuntu need a firewall
> [http://news.helpero.com/article/UBUNTU-vs-SUSE-vs-FEDORA_20.html](http://news.helpero.com/article/UBUNTU-vs-SUSE-vs-FEDORA_20.html)

These sites below explains on how to setup a simple yet effective firewall on UBUNTU via apt-get

> [http://www.howtogeek.com/howto/ubuntu/install-the-firestarter-firewall-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/install-the-firestarter-firewall-on-ubuntu-linux/)
[http://www.linux.com/articles/55319](http://www.linux.com/articles/55319)

My final verdict - I ain't offending anyone guys!! You will never need an anti-virus if you are not logging in as ROOT user. But you will need a firewall if you are running network services.

I guess this thread has done it's part (ready to be closed) !! Thanks all guys..

---

### Post by hyper_ch on 2008-07-22
> **cyclouno said:**
> I guess the answer is here... UBUNTU needs a firewall for sure & in my case since i'm gonna run daemons, i'll need one for sure !! 
Why? If you want to run services don't you want them to be accessible? If not, why run services first place?

> **cyclouno said:**
> The site below clearly says why ubuntu need a firewall
Actually that site says nothing as why you could need a firewall.

> **cyclouno said:**
> But you will need a firewall if you are running network services.
Why do you need a firewall if you want to run network services - if you want them to be accessible?

---

### Post by cyclouno on 2008-07-22
> Why? If you want to run services don't you want them to be accessible? If not, why run services first place?

Why do you need a firewall if you want to run network services - if you want them to be accessible?

Actually that site says nothing as why you could need a firewall.


Hmmm... here it is why?? you gotta a mobile number & you pick calls only from people whom you know & block the rest !! The same applies for firewalls... like... I can run services which are accessible by anyone in the world.. but when I want to block access to those services for the entire Internet except MY DOMAIN or IP, then I can use a firewall [iptables] & define the rules.

Skip this if you already are aware of iptables. I've been read a while on iptables & tcp wrappers. It's quiet simple. And you will understand why, from this example. BTW firestarter is just a front-ent GUI to kernel-level-firewall [iptables].

> To give permission for a particular IP
iptables -A INPUT -p tcp -s ! 192.168.0.1 --dport 22 -j REJECT

To give permission for a particular DOMAIN - in this case it's the 192.168.0.0 domain
iptables -A INPUT -p tcp -s ! 192.168.0.0/24 --dport 22 -j REJECT

Here is how it works..
>> -A INPUT - if the packet is coming from outside
>> -p tcp/udp - if the packet is using tcp/udp protocol
>> -s ! 192.168.0.1 - if the source of this packet is NOT 192.168.0.1
>> --dport 22 - if the destination port of this packet in your system is 22 [ which for ssh - you will find it in /etc/services ]
>> -j REJECT - if a packet matches all the above constrains then REJECT it.

[B]So the outcome??
The service is accessible, but only to your IP or domain.[/B]

I hope this effectively answers all your 3 questions & tells exactly why linux OS needs a firewall. Now that you don't even have to look around to find your distro needs a firewall !! 

Thanks for making me read to get these answers!! :)

---

### Post by hyper_ch on 2008-07-22
Well, under teh condition that only you should have access you might want to apply a firewall ;) as said, I never said a firewall has no uses... but we're not in windows where you don't know what's running and phoning home etc.

So you should know why you want setup a firewall ;)

---

### Post by cyclouno on 2008-07-22
> but we're not in windows where you don't know what's running and phoning home etc.

ha haaa. tat is exactly why I went for linux in da 1st place.. mate (atleast myself here) !! 

Your signature tell me a lots !! btw it's got a nice framing... 
> In a world without walls and fences, who needs Windows and Gates?

Alas.. freedom kingdom!! 

also I jus thanked u for letting me dig n stumble for reasons.. thnx again!!

---

### Post by druiseeker on 2008-07-22
I don't know about you guys, but I spend alot of time helping my friends with their computers.  And about half the time it ends up being a virus or some other form of malware on their windows machine which clamav, in my opinion, does a decent job of their viruses

---

### Post by aysiu on 2008-07-22
> **druiseeker said:**
> I don't know about you guys, but I spend alot of time helping my friends with their computers.  And about half the time it ends up being a virus or some other form of malware on their windows machine which clamav, in my opinion, does a decent job of their viruses
Maybe you should set them up with suDown and be proactive about preventing virus infections instead of cleaning up after the fact:
[http://sudown.sourceforge.net/](http://sudown.sourceforge.net/)

---

### Post by SSVegito888 on 2008-07-23
> **Julia Dawn Mason said:**
> I looked in the Add/Remove Program lists for the Clam AV and it is not in there. I then used the Synaptic Package Manager and found two packets that I marked for installing. I then installed but it does not show up any where that I can find it. There is no desktop icon for it or listed in the Documents folder .



Try typing clamAV into the synaptic package manager, instead of clam AV.


Also, the available clamav in synaptic package manager is out of date.  If you want new release try [[COLOR="Blue"]http://clamav.net[/COLOR]]("http://clamav.net") and install from source code.

Come to think of it I tried installing from source but for some reason it didn't work; I am fairly new to linux but have been able to install some other stuff from source.  Also, if you want a GUI for the older version (in synaptic package manager) try either klamav or clamTK.

If you install clamTK, it should install to applications menu, but Klamav for some reason will not.  To execute Klamav either open terminal and type

"klamav" (Without Quotes) or you can create a launcher on the desktop. You may need to use sudo in front of klamav in terminal and with laucher for clamav database to update properly, but I'm not entirely sure.



If you've never used sudo before you will need to create a sudo password.


sudo lets you execute things as root aka administrator.


To create a sudo password use "sudo passwd" (WITHOUT QUOTES)


**USE A DIFFERENT PASSWORD THAN YOUR REGULAR LOGIN!!!!**


[B]
BE VERY CAREFULL WHEN EXECUTING SOMETHING WITH ROOT PRIVILEGES

DO NOT ENABLE LOGIN AS ROOT

AGAIN BE VERY CAREFUL[/B]


If you need a GUI there are ways to enable sudo to work with a GUI.


Refer Here For GUI Commands (look at Second Post):

[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=801404[/COLOR]]("http://ubuntuforums.org/showthread.php?t=801404")



Sorry, I got off on a tangent.

---

### Post by pherber12 on 2008-09-13
good info, thank

---

### Post by lisati on 2008-09-13
The level of protection you put on your computer in addition to installation defaults is up to you, and the need for antivirus seems to be a matter of opinion here in the forums.

I use the free version of AVG antivirus in both Windows & Ubuntu - the catch is that with the Linux version you have to add your user to the "avg" user group for the updates to work properly (it's described in the AVG documentation). On the Linux side, I have the antivirus partly as a courtesy to Windows users with whom I need to interact (accidentally sending out malware isn't a particularly nice thing to do, even if it isn't likely to hurt your Linux installation) and partly as a trouble-shooting aid for the Windows portions of my home network.

Firewalls: again, the level of protection you want in addition to the installation defaults is up to you.

BTW, many routers have some options to help with firewall-style protection.

---

### Post by cj100570 on 2008-09-14
> **Julia Dawn Mason said:**
> I looked in the Add/Remove Program lists for the Clam AV and it is not in there. I then used the Synaptic Package Manager and found two packets that I marked for installing. I then installed but it does not show up any where that I can find it. There is no desktop icon for it or listed in the Documents folder .

It's listed as virus scanner under add/remove

---

### Post by SSVegito888 on 2008-09-14
Is using sudo considered the same thing as logging in as root?


Is it safe to use sudo?

Also, if you have to is it safer to use su or sudo?




Thanks,

SSvegito888

---

