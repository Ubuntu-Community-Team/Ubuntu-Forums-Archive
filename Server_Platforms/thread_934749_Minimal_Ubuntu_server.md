---
title: "Minimal Ubuntu server"
date: 2008-09-30
forum: Server Platforms
---

### Post by yesmat on 2008-09-30
Hi All,

I am trying to build a minimal Ubuntu server that acts as a base server for many applications. I need this server to be not mroe than 200MB after the minimal installation.

Base installation for Ubuntu server still comes up close to 600MB.

I have tried JeOS, but unfortunately this is meant for VMware appliaces only.

I have built a minimal server, from Ubuntu Desktop live CD, using debootstrap and that worked fine but still it was around 310MB.

Is there a way to build a Ubuntu server from the ground up that only has the absolutely necessary packes and then we can add more packages when needed using apt-get?

I am not interested in spliTaz and Archlilnux etc....

Any feedback or pointers are appreciated.

Thanks

---

### Post by iponeverything on 2008-10-01
here is what I would do:

Install the base server.

Use dpkg to removethe packages that you don't need:

this command will sort them by size:

dpkg-query -W --showformat='${Installed-Size;10}\t${Package}\n' | sort -k1,1n

ref: [http://www.pixelbeat.org/docs/packaging.html](http://www.pixelbeat.org/docs/packaging.html)

then clone your disk if you want to install it on other machine:

ref: [http://ask.metafilter.com/69793/How-do-I-transfer-my-current-Ubuntu-system-to-a-new-larger-hard-drive](http://ask.metafilter.com/69793/How-do-I-transfer-my-current-Ubuntu-system-to-a-new-larger-hard-drive)

---

### Post by Krupski on 2008-10-01
> **yesmat said:**
> Hi All,

I am trying to build a minimal Ubuntu server that acts as a base server for many applications. I need this server to be not mroe than 200MB after the minimal installation.

Base installation for Ubuntu server still comes up close to 600MB.

I have tried JeOS, but unfortunately this is meant for VMware appliaces only.

I have built a minimal server, from Ubuntu Desktop live CD, using debootstrap and that worked fine but still it was around 310MB.

Is there a way to build a Ubuntu server from the ground up that only has the absolutely necessary packes and then we can add more packages when needed using apt-get?

I am not interested in spliTaz and Archlilnux etc....

Any feedback or pointers are appreciated.

Thanks

Check out this link:

[http://www.howtoforge.com/minimal-ubuntu-8.04-server-install](http://www.howtoforge.com/minimal-ubuntu-8.04-server-install)

I've done this several times... the instructions work fine.

You will find that there are a few things missing (no NTP, no MAN pages and no SSH for remote admin) - but of course you can always add those later with apt-get install.

You also have to ADD the proper entries to /etc/network/interfaces (specifically, the lines for 'eth0' - highlighted in red).

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

[COLOR="Red"][B]# The primary network interface
auto eth0
iface eth0 inet dhcp[/B][/COLOR]

```

If you install on one machine and move the disk to another, BE SURE to also clear any network entries from '/etc/udev/rules.d/70-persistent-net.rules' so that your eth0 device works. If you install on one machine, that file contains the MAC address for the install machine (linked to eth0). Moved to another machine, it will try to link up the new MAC address to 'eth1" which has no entry and therefore you won't get a network connection.

Good luck!

-- Roger

---

### Post by yesmat on 2008-10-01
Hi Krupski,

This what I did. It works fine but this install comes to 300MB as I mentioned in my post. Any suggestions to have a smaller build? around 100MB?

Thanks

---

### Post by yesmat on 2008-10-01
Hi Iponeverything,

these commands and references are very useful. Many thanks for that. I will try this to see if I can remove some of the packages that i don't need and see what happens.

Once I achieved the ideal size, then clone or use G4L to create an iso that I can repliacate.

Thanks

---

### Post by iponeverything on 2008-10-02
also don't forget to do a "dpkg clean", and to fix your logrotate scripts so that a chatty process does not fill up your partition..

---

### Post by windependence on 2008-10-02
Easy. Set up a FreeBSD server. The footprint will definitely be less than 200MB.

-Tim

---

### Post by iponeverything on 2008-10-02
The only disadvantage that I could see to that is I know my way around linux so well that I can work without a monitor. On FreeBSD I would have spend a fare amount of time looking up how to do things in google.

Admittedly, that would be a small price to pay if FreeBSD was the right tool for the job.

---

### Post by windependence on 2008-10-02
Actually, most of the commands are the same, and the manuals for the *BSDs are very good compared to the Linux man pages. The ports system is a really nice package management system, and easy to learn and use. 

Here are some good resources to get started or check it out before you commit:

Forums (VERY good resource):

daemonforums.org

FreeBSD handbook:

[http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/)

Main site:

[www.freebsd.org](www.freebsd.org)

How To:

[http://freebsdhowtos.com/](http://freebsdhowtos.com/)


Don't be afraid to ask me either. I can help you get started. The thing I like best about the *BSDs is that there is nothing loaded in the OS that you don't need. You build in what YOU want and the footprint is VERY small. It's also more stable than Linux, and of course Linux is pretty darn stable.

-Tim

---

### Post by Krupski on 2008-10-02
> **iponeverything said:**
> this command will sort them by size:

dpkg-query -W --showformat='${Installed-Size;10}\t${Package}\n' | sort -k1,1n

I have a question... from the list resulting from the above command... how does one know what they can safely remove?

I imagine creating a dependency nightmare by removing the wrong file(s)!

---

### Post by yesmat on 2008-10-03
Good point, I was thinking the same thing (which packages I could remove safely?)

But I had the ubuntu server loaded for testig on my VMware server and took an image from it, so that I could back to that image if i managed to rendered my server unusable, which has happened several times. Then i started taking the big size packages first. Some ones are obvious like wireless, laptop support, and wpaxxx.

But it is, in my case, hit and miss.

if some one could point us to some resource that explains these packages would be great.

---

### Post by iponeverything on 2008-10-03
If there is a dependency issue, dpkg will catch it tell you it can't remove the file and it will tell what the dependency is. 

If you don't think that you need packages that it depends on, just add them all to the command line.

Generally it fairly easy to pick out the ones that you don't need.

ref: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by Rich78 on 2008-10-03
What's the purpose behind having such a small footprint and therefore what benefits are you expecting?

Storage space is cheap nowadays so I'm guessing it's not that?

I'm not sure it will perform any quicker if the running processes aren't too dissimilar to a standard build.  These non required processes can be removed but you'll reach a cut off point, and still not have your sub 200MB footprint, so I'm interested to know why the small footprint?

---

### Post by windependence on 2008-10-04
> **Rich78 said:**
> What's the purpose behind having such a small footprint and therefore what benefits are you expecting?

Storage space is cheap nowadays so I'm guessing it's not that?

I'm not sure it will perform any quicker if the running processes aren't too dissimilar to a standard build.  These non required processes can be removed but you'll reach a cut off point, and still not have your sub 200MB footprint, so I'm interested to know why the small footprint?

He may be running this on an ITX system on a flash card or something along those lines.

IMHO Ubuntu is not a great OS to try to slim down and run with a very small footprint. The BSDs are great for this, or you could run something like Damn small Linux.

-Tim

---

### Post by Krupski on 2008-10-04
> **windependence said:**
> He may be running this on an ITX system on a flash card or something along those lines.


I run Ubuntu 64 bit server from a Compact Flash card. I have not removed anything from the base install. In fact, I added NTP, VSFTPD, ZIP, UNZIP, UPX, BEEP, BUILD-ESSENTIAL and several other packages that I can't recall right now.

The whole thing takes up 638M and it's installed in a 2.0 GB partition on the CF card. There's a ton of room to spare.

I, too, see no reason to try to minimize the footprint... but since the OP asked, obviously he has SOME reason and replying with "why do you want it small" would have been pointless.

---

