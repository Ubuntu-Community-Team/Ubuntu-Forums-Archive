---
title: "Could not download all repository indexes"
date: 2005-11-12
forum: Repositories &amp; Backports
---

### Post by gravediggers on 2005-11-12
Hi,

Followed instructions for enabling universe ans multiverse then hit reload but got the following messages:
[http://au.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:](http://au.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:) Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg:](http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg:) Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://au.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg:](http://au.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg:) Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out

Obiously synaptic not set up correctly!? Can any one point me the right direction?

---

### Post by Xian on 2005-11-12
You'd better post the contents of your /etc/apt/sources.list

---

### Post by gravediggers on 2005-11-12
Contents are (slightly edited)....

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
 deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy-updates main restricted
 deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
 
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse
 deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.

 deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) breezy universe

Now most of these links redirect to a mirror at [http://mirrors.uwa.edu.au/ubuntu/](http://mirrors.uwa.edu.au/ubuntu/), but the folders main, restricted, etc. are at [http://mirrors.uwa.edu.au/ubuntu/pool/](http://mirrors.uwa.edu.au/ubuntu/pool/) which I guess is why it doesn't work?? Should I edit sources.list to show [http://mirrors.uwa.edu.au/ubuntu/pool/](http://mirrors.uwa.edu.au/ubuntu/pool/) or is there a better source to link to?

---

### Post by gravediggers on 2005-11-14
Guyz, pls i need to update some stuff, but i need the right links!

---

### Post by tassou on 2005-11-14
(...) (1.0.0.0), connection timed out ...

I do not think this IP is the right one :)
Can you go on the internet ? 
Can you ping google or ubuntulinux from the command line ?
If you can, are you behind a proxy ?
If you are, please set it in the options of synaptic.

Paul

---

### Post by linbetwin on 2005-11-14
try removing the "au.".

---

### Post by gravediggers on 2005-11-22
OK. I removed the au. No joy!
Then I tried the following suggested by Ameet on thread
[http://www.ubuntuforums.org/showthread.php?t=83728&highlight=sources](http://www.ubuntuforums.org/showthread.php?t=83728&highlight=sources)
[QUOTE=Ameet]OK, I think I solved my problem.  This may help AllenP and cbg and others as well.

1) I fixed my /etc/apt/sources.list as described by Aysiu in another thread.  The details are at [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

2) I commented out the last line in sources.list which is about retrieving breezy-backports as several vets have said that is not up and active at this time.  Commenting that is done using gedit (like in step 1), and adding "##" at the front of the last line.

3) I trashed the old listings in /var that were confusing apt-get.

```

cd /var/lib/apt
sudo mv lists lists_backup
sudo mkdir lists
sudo mkdir lists/partial
sudo apt-get update

# when the above works error-free, you can do the next line:
sudo rm -r lists_backup

```

After this, I ran Synaptic package manager and it worked like a charm! :D[/QUOTE]

No joy!

Edited all but the following line from sources.list
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
then did sudo apt-get update   and that seemed to work.
included a second line and that worked.
ran Synaptic and it all fell to pieces again!
retried apt-get but errors.
edited sources.list to have only the first line I mentioned above but still fails.

 sudo apt-get update
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Reading package lists... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

Is there some thing else I need to do?

---

### Post by Manny C on 2005-11-22
Are you running a firewall of some sort?

---

### Post by gravediggers on 2005-11-22
Yeah,but not o this box! I don't think the Nortons on the windows machine could affect this one. However, it could be something on my router! Any idea?

---

### Post by aysiu on 2005-11-22
Look at the first link in my sig, especially the bottom portion.

---

### Post by gravediggers on 2005-11-23
Thanks Aysiu,

I had tried what u said b4, but went thru it again just in case. got the following again
 sudo apt-get update
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Reading package lists... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


At this point, what would you suggest? Complete reininstall or is there something else that I an do!

---

### Post by aysiu on 2005-11-23
So even the bottom part did no good? That's the only workaround I know.

---

### Post by Marmaduke on 2005-11-23
Hello Gravediggers,

I have experienced the same problem as you're experiencing. 

It turned out that DNS proxy in my ADSL Modem / Router did not seem to work well with Ubuntu. Once I specified my ISP's DNS servers in my network settings the problem went away.

---

### Post by gravediggers on 2005-11-23
DNS!
Hmmm - somebody hinted at something similar earlier, but I was too busy following the instructions to get the correct sources.list to pay it much attention at the time. I did have dns issues at an earlier point using my router as proxy but it only seemed to affect firefox and i got around it in the firefox config.
I will try sticking my ISPs DNS IPs in resolve.conf, and then try apt-get again!

---

### Post by gravediggers on 2005-11-24
:D OK! Working at last!
Thanks Aysiu for the good sources and Marmaduke for the prompt about DNS settings. Followed the wiki on StaticDnsWithDhcp [https://wiki.ubuntu.com/StaticDnsWithDhcp?highlight=%28dns%29](https://wiki.ubuntu.com/StaticDnsWithDhcp?highlight=%28dns%29) and all is good now.

---

### Post by Granduke on 2005-11-24
Thanks Aysiu,
I was having same problrem as gravediggers and your soure list was the fix.
This is my second day using linux and I spent half of it trying to figure out was a repository is and way I can't download them.  

Granduke

---

### Post by veehell on 2005-12-20
[QUOTE=Granduke]Thanks Aysiu,
I was having same problrem as gravediggers and your soure list was the fix.
This is my second day using linux and I spent half of it trying to figure out was a repository is and way I can't download them.  

Granduke[/QUOTE]

So enjoy linux ;)) 
btw: be sure about the selection of repositories and what you choose to install.
Sometimes more and last does not mean best and stable ;).

---

### Post by damaenapuros on 2005-12-29
hello, have the same problem BUT

how do i know if i am in a DNS connection? what is that?

i am in a small domestic wireless network, and the main computer is windows, could that be the problem?

(in case you cant tell i am very new to this...)

---

### Post by gravediggers on 2005-12-31
Hi damaenapuros,

First thing is to make sure you follow the instructions for setting up your repository list correctly as posted by Aysiu. If this does not work for you, we then have to determine if it is a DNS problem. 
If you get an error with a line in it similar to ....
[INDENT]Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out[/INDENT]
then you most likely have a DNS problem (as indicated by the ip 1.0.0.0).

How you resolve this depends on how your network is set up! You said the main computer is windows. Is this acting as a server for the internet connection (eg, wireless router connects into windows pc, and only that has a direct connection to the internet), or does the router connect directly to the internet?
Hopefully you have the second setup, 'cos i can help better with this. The easiest way to check if DNS is set up correctly is look first at /etc/resolv.conf. If it says _nameserver 192.168.1.1_ (this is the default router address on most home networks) then you are using the router as a DNS proxy, and if the modem is not setup to perform this service, then you will get the above error. The way I got around this was to setup static DNS (using my ISP's DNS addresses, but you can use any valid DNS server). Follow the link for StaticDnsWithDhcp (in an earlier post of mine on this thread) and that should resolve it!

Good luck!

---

### Post by drfalkor on 2005-12-31
sometimes it helps to:

**1)** plugout the internett cable
**2)** sudo apt-get update
**3)** plugin the internett cable
**4)** dial(connect) up to the internett ( or: sudo dhclient )
**5)** sudo apt-get update

---

### Post by veehell on 2006-01-26
Hi 
i have few machines, with those "repositories" (on second one i add the CZ.ubuntu.* ones). Sometimes, backports, official repositories for local countries are not available (i dont know why, ...maybe due the sync with others) so i usually wait for next "smooth" connection
and i add also SARGE repositories to have DEBian original packages nearby ;)

# VH edited !
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe
deb [http://www.paul.sladen.org/debian](http://www.paul.sladen.org/debian) all skype
# ad skype: i used Automatix 3rd party project to install the client without the bug

---

### Post by teomatteo89 on 2006-01-26
help me! 
i have same problem.. synaptic can't download the packages..

here is my error:
```

W: Impossible to control the list of the packages source http://archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossible to control the list of the packages source http://archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossible to control the list of the packages source http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossible to control the list of the packages source http://archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossible to control the list of the packages source http://archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossible to control the list of the packages source http://archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossible to control the list of the packages source http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossible to control the list of the packages source http://archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossible to control the list of the packages source http://archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossible to control the list of the packages source http://archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossible to control the list of the packages source http://archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossible to control the list of the packages source http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossible to control the list of the packages source http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossible to control the list of the packages source http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
```


this is my /etc/apt/sources.list

```

## Uncomment the following two lines to fetch updated software from the network
deb-src http://au.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.

deb http://archive.ubuntu.com/ubuntu breezy universe main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
deb http://security.ubuntu.com/ubuntu breezy-security universe main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
deb http://archive.ubuntu.com/ubuntu/ breezy universe
```



i tryed to see in the error dir what have i, but i found a file called"lock" and a subdirectory with nothing inside, called "partial".....


can u help me?

---

