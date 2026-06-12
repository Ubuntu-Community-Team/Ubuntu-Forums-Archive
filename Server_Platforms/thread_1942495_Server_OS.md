---
title: "Server OS"
date: 2012-03-17
forum: Server Platforms
---

### Post by bubylou on 2012-03-17
I have used Ubuntu for my servers OS for while now and haven't had any big problems with it. I wanted to check out what other Linux distros would have to offer. More specifically if i should make the big change to a RHEL based distro like Cent OS. I also wanted to see if there were any other Debian based distros that might be a better choice or maybe just use Debian. Mainly looking for personal experiences, knowledge, preference, and someone to help me make an educated choice of which distro is best for use on a server.

Some Questions
Big Difference between Debian and Red Hat distros
Reason to pick either Ubuntu or Debian
Which is the most used distro for both personal and enterprise

---

### Post by bubylou on 2012-03-18
bump for discussion

---

### Post by nathan.the.sane on 2012-03-18
Why not install some other options in Virtualbox and try them out? That's the best way to find out about something, rather than taking someone else's word for it. They may have an entirely different set of needs/preferences than you.

Personally, I use CentOS on my server. You can kinda sorta think of it as Fedora, of course, so expect yum instead of apt-get and selinux etc.The biggest difference from Ubuntu I noticed is that it is slightly more secure/paranoid by default. For example, it has a firewall enabled by default that blocks ALL http traffic from ANYWHERE, even the LAN. Took me a couple hours to figure out why I couldn't get the Apache test page to display in my laptop's browser when I could ssh just fine. :oops: Yeah, I'm not a professional sysadmin, just a curious amateur! Maybe someday...

Edit: Of course, that turned out to be a positive learning experience in the end, because now I know a heckuva lot more about using iptables :P

---

### Post by CharlesA on 2012-03-18
The CentOS firewall blocks a lot of stuff by default. I think the only thing that isn't blocked is SSH and (maybe) SMTP.

An OS is only as secure as you make it. Ubuntu/Debian/RH/CentOS are pretty secure by default but you can lock them down more if you so desire.

---

### Post by Holdolin on 2012-03-18
> **CharlesA said:**
> An OS is only as secure as you make it. Ubuntu/Debian/RH/CentOS are pretty secure by default but you can lock them down more if you so desire.

This.

As far as use, the last report I read listed Debian as the top used Linux web server.  It uses older, more tried and tested codebase.  Ubuntu uses a newer codbase (based off of Debian unstable) and has a longer support cycle for it's LTS's.  CENT also has a long support cycle if you wish to make uses of it.

Personally, I think Debian and Ubuntu have a more active, supporting community, hence why I'm here.  That however is just one person's opinion.  If you have the means, try nathan's idea.  Try them all out.  Find the one that works best for YOU, as you're the one using it :)

---

### Post by bubylou on 2012-03-18
i actually just freed up a server so i may try centos out on it rather than use a virtual one. I especially like the idea of having a very secure system at start then open things as you go rather than vice verse As far as debian goes is its stability really worth it, i havent had any crash with ubuntu and love the community thus far. Any other big reasons to pick red hat over debian distros.

---

### Post by CharlesA on 2012-03-18
Having a firewall set to not allow connections to a port by default when there is nothing listening on that port is pretty much the same as having the firewall set to allow connections to a port that has nothing listening on it.

There is nothing to connect to in both cases.

In any case, you should tailor the firewall to your specific needs instead of using one that blocks or allows everything.

---

### Post by bubylou on 2012-03-18
Well i definitely try centos soon but can anyone else say why centos would be a better choice over Ubuntu. More specifically big reasons and not personal preference. Also Debian or Ubuntu. Any input would be immensely helpful.

---

### Post by nathan.the.sane on 2012-03-18
> **bubylou said:**
> Well i definitely try centos soon but can anyone else say why centos would be a better choice over Ubuntu. More specifically big reasons and not personal preference. Also Debian or Ubuntu. Any input would be immensely helpful.

The thing with Linux is that you can (in theory) make any particular distribution do anything any other distribution does. The difference in distributions is how close by default they are to what you need in your particular situation. For example (this is completely hypothetical), Ubuntu might come with version 5.6 of OpenSSH with password, public key and PAM authentication enabled, whereas RHEL and CentOS may come with an OpenSSH 5.2 package that has PAM disabled and listens on port 2222 instead of port 22. But there's nothing stopping you from manually downloading and installing OpenSSH 5.6 on your CentOS box and changing sshd_config to enable PAM and listen on port 22, to make it just like Ubuntu. But if you were going to do that then you would have to ask why not use Ubuntu to begin with? It's not really a question of which is 'better'; maybe CentOS's OpenSSH has fewer bugs but Ubuntu's has a new feature that you might need. 


The point is, you need to have some idea of the kinds of things you are wanting to do and the way you like things to be set up, and find something close to that that you can tweak. The best way I can recommend is trying LOTS of things out. I haven't experimented much with server distros (I mainly just used Ubuntu server until giving CentOS a shot, which I really like), but on the desktop side I've used Ubuntu, Debian, Arch, Mandriva, Slackware, Fedora, LFS, OpenSolaris, FreeBSD, Zenwalk and a bunch of others I can't remember right now. Each one has tradeoffs which make it easier to do some things and harder to do others, but in general I've found Ubuntu is the best at giving me close to what I want so I use it. One reason is that Ubuntu's GtkPod package has ALAC and MP3 support compiled in, whereas Debian's (because of their licensing stance) does not. So if I used Debian I would have to get the GtkPod source and compile it myself. That sort of thing is partly why I use Ubuntu instead of Debian, but if all I asked on a forum was "Is Debian better than Ubuntu?", how would the other people know to mention that? Experience is the best teacher.

So just pick one, and if you run into something about it you don't like maybe try something else, which might be fine with that but have a different set of annoyances. Of course, if you're doing this for a production server this might not be the best way to go about it! Hopefully if someone is doing this for anything other than a personal project they have long since found something they're comfortable with and know the ins and outs of.

:popcorn:

---

### Post by bubylou on 2012-03-18
Very well put. I will be trying several Linux ditros as time goes on this post was intended to give e a head start on what to try and what to expect.

---

### Post by bubylou on 2012-03-18
I was somewhat surprised by centos having a GUI installed with it. Is there a valid use for a gui on a server or is it just taking up resources. My current Ubuntu server us headless and i never found a use for a GUI on it. Other than that still looking for a big differences between centos and ubuntu. Think ill try Debian next.

---

### Post by CharlesA on 2012-03-18
You can deselect the GUI during install. IIRC, there is a "basic server" option in the installer.

---

### Post by bubylou on 2012-03-18
Thanks, i knew that had to be a way to get rid of it. Also just rewrote my last post. If somone could explain the reasoning and difference between ubuntu's use of sudo and debian accessible root account. If you understand what im trying to say.

---

### Post by CharlesA on 2012-03-18
See here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bubylou on 2012-03-19
I don't see how well having an accessible root account would be. I use ssh as my main access method as well as using it for SFTP and occasionally i use it outside my network. Are there any good reasons to have a root account. I somewhat like not having to type sudo but i think it might be a security problem.

---

### Post by bubylou on 2012-03-19
Never mind answered my own question. Disable root account for ssh, sign in as normal user on ssh then sign in as root.

---

### Post by SeijiSensei on 2012-03-19
You'll find some major differences in the location of files like RH/CentOS's use of /var/www/html as the default website directory rather than /var/www.  Also there is no equivalent to "/etc/apache2/sites-available/sites-enabled" on an RH-flavored machine, and the Apache daemon runs as user "apache" rather than as user "www-data".

The DNS server runs chrooted by default, so the standard /var/named tree is actually located in /var/named/chroot/var/named.  On RH, it runs as user "named"; on Ubuntu it's user "bind".

There is some software that is better packaged for RH/CentOS than for Debian/Ubuntu.  MailScanner is one of these as is, I believe, Webmin.

I use CentOS on my servers and Ubuntu on the desktop.  I had many years of experience with RH-flavored distros before switching to Ubuntu, so I know my way around both.  One of the biggest differences, how servers are managed, has narrowed since Ubuntu began using Upstart.  Now both distros use "service servicename start/stop/restart" to control server daemons, though you'll find the occasional Ubuntu service which hasn't been fully converted to Upstart.  Even so, there are differences in commands.  The RH command "chkconfig service on/off" is represented on Ubuntu as "update-rc.d service enable/disable".  Differences like these are hardly earth-shattering, but they are annoying.

---

### Post by bubylou on 2012-03-19
It seems like Debian and Red Hat are more alike than i assumed. Seems like most of the knowledge is transferable and easy to adjust to each. I may just need to find which OS works best for what im doing rather than the generic this one is better at everything.

---

### Post by arrrghhh on 2012-03-19
> **bubylou said:**
> It seems like Debian and Red Hat are more alike than i assumed. Seems like most of the knowledge is transferable and easy to adjust to each. I may just need to find which OS works best for what im doing rather than the generic this one is better at everything.

Correct - it's still Linux!  The main differences are package management, and file locations.  Most of the rest of it can be transferred effortlessly between distro's... commands, concepts, etc.

I like Debian based systems for the package management.  I used Fedora Core a while ago, and absolutely hated how they did package management.  For me, DEB is the way to go!

---

### Post by bubylou on 2012-03-19
I think ill stick with Debian based distros for now but that still leaves the question of which Debian based distro to use. Persoanlly i like ubuntu so far and im a bit afraid of Debian older packages. If someone could say why they may of picked one over the other. Or maybe there is a 3rd option.

---

### Post by snowpine on 2012-03-19
Hey, it's my new friend bubylou from Debian Forums! Just wanted to say hi over here on Ubuntu forums. :)

---

### Post by snowpine on 2012-03-19
> **bubylou said:**
> I think ill stick with Debian based distros for now but that still leaves the question of which Debian based distro to use. Persoanlly i like ubuntu so far and im a bit afraid of Debian older packages. If someone could say why they may of picked one over the other. Or maybe there is a 3rd option.

It depends on your definition of "older." Debian packages are no more than 2-3 years old, comparable to Ubuntu LTS, Red Hat, CentOS, etc. Some users (such as myself) are perfectly happy to use slightly older software that does the job reliably (especially for server purposes).

Also Debian has Backports/Testing/Unstable/Experimental repos for those that need/desire to use newer software.

Nothing you have said so far (on either forum) leads me to believe that Ubuntu Server is a bad choice for your needs. :)

---

### Post by arrrghhh on 2012-03-19
> **bubylou said:**
> I think ill stick with Debian based distros for now but that still leaves the question of which Debian based distro to use. Persoanlly i like ubuntu so far and im a bit afraid of Debian older packages. If someone could say why they may of picked one over the other. Or maybe there is a 3rd option.

As was previously stated, the packages are older - but that doesn't mean that they won't work!  In fact, that usually means that they'll be much more stable.

With that stability, does come some cost - since the packages are older, if there's new features you HAVE to have, then you'll need to do some legwork to get that package up to the newest version.

I've never run a production Debian server, so I don't know if this would bother me or not.  I'm on Ubuntu LTS, so that OS is at this point 2 years old.  Hasn't caused me any grief, and if the need arises for a manual update I've found repo's that help.  The two packages that have given me grief were PS3MediaServer, and MPD - both of which were easily resolved with an updated repo :D.

---

### Post by bubylou on 2012-03-19
Its not that i don't like Ubuntu. Im just sampling what all Linux has to offer and perhaps if i find a better distro i will make a switch. Just making sure i find the best option for me.

---

### Post by arrrghhh on 2012-03-19
> **bubylou said:**
> Its not that i don't like Ubuntu. Im just sampling what all Linux has to offer and perhaps if i find a better distro i will make a switch. Just making sure i find the best option for me.

Hence why people suggest virtual machines.  You can spool up and destroy them quite easily, which should help accelerate your testing.

---

### Post by bubylou on 2012-03-19
But there is nothing quite like raw hardware. Which i just so happen to have a older desktop to use for testing purposes.

---

### Post by hawkmage on 2012-03-19
For testing proposes unless you are testing specific hardware devices I have not seen a reason to choose physical over virtual.  

Not to mention that I find it easier for testing to deal with VMs instead of old re-purposed hardware because of having run into odd hardware that is not well supported anymore.

---

### Post by arrrghhh on 2012-03-19
> **hawkmage said:**
> For testing proposes unless you are testing specific hardware devices I have not seen a reason to choose physical over virtual.  

Not to mention that I find it easier for testing to deal with VMs instead of old re-purposed hardware because of having run into odd hardware that is not well supported anymore.

This ^^.  10,000x over.  If you're just comparing differences in OSes, there's no point in complicating that testing with various potential hardware problems.

---

### Post by bubylou on 2012-03-19
Sorry about that but what i mean by test is more like full fledged hosting. Its more of trial session.

---

### Post by arrrghhh on 2012-03-19
> **bubylou said:**
> Sorry about that but what i mean by test is more like full fledged hosting. Its more of trial session.

Which you can do on a VM, much easier than a physical machine.  We run 99.9% of our servers in a production environment virtualized (ESX-i, but still).  Not sure why you're scared of virtualization, it really is the future of computing.  Get the full use of your hardware, plus you don't have to worry about idiosyncrasies about hardware (usually).

Do what works best for you, just don't ignore or write off our advice.  We're here to help you.

---

### Post by CharlesA on 2012-03-19
> **arrrghhh said:**
> Which you can do on a VM, much easier than a physical machine.  We run 99.9% of our servers in a production environment virtualized (ESX-i, but still).  Not sure why you're scared of virtualization, it really is the future of computing.  Get the full use of your hardware, plus you don't have to worry about idiosyncrasies about hardware (usually).

Do what works best for you, just don't ignore or write off our advice.  We're here to help you.
+1. I have my web development box virtualized as well as a couple copies of Linux and Windows. Helps with testing and/or running different services on different boxes.

---

### Post by bubylou on 2012-03-19
I currently use virtual box for my VM's and haven't bothered setting up any virtual environment on my actual server. This is more of a hobby/learning experience than something that would utilize a virtual setup. Although i may give it a try in the future to gain a better understanding of visualization. Thank you all for your input but now i think all that's left is for me to continuing exploring.

---

### Post by bubylou on 2012-03-19
Should i really make an attempt at virtualization for my main server? Remeber that both servers are just repurposed desktops. One of them is very old. And if so if you could give me a jumpstart on the project.

Old Server
dual core pentium
1.25gb
75gb

New Server
dual core athlon
4gb
750gb

---

### Post by CharlesA on 2012-03-19
I ran a few VMs on my old server, which was a dual core with 6GB of RAM and a 500GB HDD.

New server is an i7 quad core with 16GB of RAM.

---

### Post by redmk2 on 2012-03-19
> **bubylou said:**
> Should i really make an attempt at virtualization for my main server? Remeber that both servers are just repurposed desktops. One of them is very old. And if so if you could give me a jumpstart on the project.

Old Server
dual core pentium
1.25gb
75gb

New Server
dual core athlon
4gb
750gb

I think one needs to define what the term server really means.  To my way of thinking a server is any host that provides a service (daemon) for other hosts requests (clients).  The physical hardware is important some of the time.  I think of the hosts running OS as either "real" or "virtual" machines.  In other words both types (real (RM) or virtual (VM)) have to deal with hardware, but in different ways.

One good example of this is using a USB connected device with a virtual machine (VM).  Do you need need this?  Can it be done with a hardware solution?   Yes it can/  See Intel's thoughts [**_[COLOR="Blue"]here[/COLOR]_**]("http://software.intel.com/en-us/blogs/2009/06/25/understanding-vt-d-intel-virtualization-technology-for-directed-io/").

---

### Post by arrrghhh on 2012-03-19
> **bubylou said:**
> Should i really make an attempt at virtualization for my main server? Remeber that both servers are just repurposed desktops. One of them is very old. And if so if you could give me a jumpstart on the project.

Old Server
dual core pentium
1.25gb
75gb

New Server
dual core athlon
4gb
750gb

I would say if your processor doesn't support hardware virtualization, then running a lot of VM's is not going to be a pleasant experience.  The new server could probably run a few without breaking a sweat.  Look up the specs on your specific hardware, it'll tell you if it supports it or not (or post more info on the hardware ;))

Also, I run VM's on my headless server - VBoxHeadless is nice.  It allows me to RDP to the VM from another workstation, which is how I access the server anyways.  Works great!

---

### Post by CharlesA on 2012-03-20
> **arrrghhh said:**
> 
Also, I run VM's on my headless server - VBoxHeadless is nice.  It allows me to RDP to the VM from another workstation, which is how I access the server anyways.  Works great!

+1. That is what I am running now. Headless servers are quite handy. ;)

---

