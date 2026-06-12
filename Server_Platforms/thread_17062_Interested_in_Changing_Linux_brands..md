---
title: "Interested in Changing Linux brands."
date: 2005-02-25
forum: Server Platforms
---

### Post by Schitie on 2005-02-25
Good day,

I am currently running Fedora Core 3 for my webhost server and have been directed this way by a friend of mine.  I am interested in changing to Ubuntu, but I have a few questions first.

1.  I am looking at being a web host, I know how to setup Apache2, PHP, MySQL, and FTP.  But the only thing is I have never been able to get email to work properly on multiple domains.  How hard woould it be to set this up, and what would most people recommend for this?

2. I am very new with Linux, and have learnt everything I know on Fedora C3.  I have never used a GUI interface.  Everything I have done has been text.  What would the advantages and disadvantages of going to Ubuntu -vs- FC3? 

3. I am also hoping to be able to setup a DNS Name server with this unit as well.  I do not have a static IP a of yet, but will be getting it soon enough.  How hard would it be to do this and again would people recommend GUI or text for doing this kinda of task?

These are just a few of my many questions I have.  I do not want to take my server down, so I will be building the Ubuntu box in a VMware box to start with, then imaging it off to put it on the actual server.

For those of you interested, the current site on my FC3 box is as follows.

[www.smackmyassandcallmestanley.com](http://www.smackmyassandcallmestanley.com)

Please feel free to register the forums and hang out there with us.

Thanks for your time.

---

### Post by az on 2005-02-25
Why do you want to switch to Ubuntu?

Ubuntu can probably meet all the needs that you mention, and no, you do not need to run a gui for any of the things you mentioned.  Maybe an advantage would be that a custom Ubuntu install is leaner than fedora?

This is just a guess, since I know nothing about what Fedora installs, or if you can just install a non-gui base system with Fedora.


Fedora probably has a more robust set of tools for what you are doing.  Ubuntu can run a web/mail/dns/whatever server, but it is primarily a desktop system.  If you want something more general-purpose, use Debian.

---

### Post by telmo on 2005-02-25
I was also a FC3 user. But only a desktop user. I never used it as a server, but i hear it works better as a server than Ubuntu. I still preffer Ubuntu though... it's lighter and works better in my laptop. And as far as i know it doesn't use the linux community to gain money selling an improved distribution... enough said...

As for server things... i don't know anyting about that. :S

I made the switch... can you? :)

Hey... 'we' give you the cd's for free  :lol:

---

### Post by Rottweiler on 2005-02-25
I recently made the switch to Ubuntu. Before that I was a devoted RH/FC user. I mostly do servers.

Here's why I switched and tend to think you'll be happier too:

1) Ubuntu lends itself to clean, lean server installs. Install minimal and build it from there.

2) The Ubuntu repository is deep and wide. Most everything you will need is as close as 'apt-get'. FC has essentially no real repository behind it.

2a) If you do have to build something from source it'll probably be alot easier than on most other distros.

3) The deb package management system is superior. You'll spend fewer long nights in RPM dependency you-know-where.

4) Upgrades can be done in-place and online. With FC you need to take the box down and load it up from a CD. Downtime. (Many of my servers are remote, so this is a big deal).

5) It's based on Debian and less likely to go off into left field at the whims of a profit-motive entity. Most of us aren't an "Enterprise".

6) Ubuntu is a young distro. If, for some reason, it should turn out to not be long term viable, it's a short trip from here to Debian or some other Debian-based distro.

7) There are desktop distros (e.g. Xandros, MEPIS) and there are server distros (Debian, RHEL) and there are distros that aren't sure what they are (FC). Ubuntu is equally viable both as a desktop and as a server.

There are probably more but that's what comes to mind.

Hope this helps.

BTW, you'll come off as less of a newbie if you refer to switching "distros" instead of "brands".

---

### Post by Schitie on 2005-02-26
Thanks for the replies.  I see a bit of a mixture here, some people saying it's good for servers, others saying goto Debian.  My friend runs Ubuntu for his firewall and loves it. 

I guess a little more background might help out.  I originally started out hosting my site(s) on a win2k Advanced server, shortly after that I was hacked and lost all my sites.  My friend came over and setup a Suse box for hosting, but I had no idea what to do with it.  So I started at that point learning linux (~9 months ago)  I hated how Suse loads and you had WAY to many config files to play with just to make one thing work, so I did some research and got directed to FC3.  I played with FC3 in VMware for about 6 months and got the hang of working in the text inteface and have gotten myself to this point.

Now I am getting told by my friend that this "distro" (Yes I am a complete newbie to linux so don't mind my wording prev.) is the best way for me to go.  I know Debian is pretty start forward to use, but there seems to be a lot more updates and help avaliable here. 

Would someone be able to lay out some pro's and cons as to using this as a server.

The machine I am running the server on is not a powerful machine, it is as follows:

PIII - 600Mhz
640 Megs RAM
80 gig Samsung HD
3Com 905B ethernet card

all managment of this machine it done via putty.

Thanks for in advance.

---

### Post by alastair on 2005-02-26
My advice is to stick with what you have at the moment if it is working for you. Both Fedora and Ubuntu are fine for server (or desktop) use and there is not that much difference. The main point in Ubuntu's favour is the Debian repository system (apt-get etc.) - I think it is easier to use and more easily managed. Your main reason to stick with fedora is that it is installed and working, plus you are a little familiar with it. Ubuntu configuration is similar but file location and setup is slightly different in Debian.

Both are perfectly happy with web, mail, DNS etc. - as is any Linux distro really.

---

### Post by kreawit on 2005-02-26
The main reason for changeing from Fedora to Ubuntu (Debian) for you are your mail-problem and apt-get. With apt-get (or Synaptic) its very easy to change mailserver and test exim, postfix or what ever suit your needs. That was a pain when I still had Red Hat-servers to manage.

I have found Ubuntu to be a very convinient way to install a "debian"-server, I have changed my habit of using CLI and Webmin to GUI/X nowadays. With more bandwith you can use X remote even if your server are located at a serverfarm elseware.

---

