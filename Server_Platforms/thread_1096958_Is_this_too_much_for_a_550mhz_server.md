---
title: "Is this too much for a 550mhz server?"
date: 2009-03-15
forum: Server Platforms
---

### Post by linuxisevolution on 2009-03-15
The server has 256mb ram and an 8gb hard drive + a 3.2gb hard drive and a 4gb SSD drive. It runs Debian 4. This is the services running:

```

Apache/2.2.3 (Debian) mod_python/3.2.10 Python/2.4.4 PHP/5.2.0-8+etch13 mod_perl/2.0.2 Perl/v5.8.8 squid Server at 98.219.177.90 Port 80

```


Is this too much?

```

01:48:11 up 31 days, 17:27,  1 user,  load average: 0.09, 0.12, 0.09

```

---

### Post by hictio on 2009-03-15
I don't understand your question...
The load is nearly flat... It doesn't seem to be having any problem, load wise.
Why are you asking? Did you find any problem?

---

### Post by linuxisevolution on 2009-03-15
I have no problems, just curious if I should be running mysql,php.apache and mods,ssh, screen, etc, on this older machine. For instance if it fails. Should I be so reliant on such a machine? It hasn't crashed yet...

---

### Post by volkswagner on 2009-03-15
I ran a similar spec server.  For limited email accounts and basic web sites, it was great.  The biggest issue is disk speed, from the controller aspect.

The only issues I had were: [LIST=1]
[*]Trying to run a photo gallery, images load painfully slow.
[*]I had a near lockup while transferring a .zip file near the RAM size.  This was via the webmin file transfer, not sure what protocol it uses.
[/LIST]

See my [thread]("http://ubuntuforums.org/showthread.php?t=1043288") for the above near lockup.

Other than than that, these old boxes make excellent servers.  They use much less electric than a Pent4 box.  My pent2 400MHz with one hard disk, ran under 40 WATTs for the entire machine.  It was my first PC, so I am hanging onto it for dear life.  I will now use it for testing and a backup for when I need to put my Intel Atom down for service/upgrades.

Enjoy

---

### Post by hictio on 2009-03-15
Ohh... I see :D
For starters, I would add more RAM, if possible.

How many hits do you think that your Apache will receive, how much traffic?
What type of content does it serve?

---

### Post by linuxisevolution on 2009-03-15
> **volkswagner said:**
> I ran a similar spec server.  For limited email accounts and basic web sites, it was great.  The biggest issue is disk speed, from the controller aspect.

The only issues I had were: [LIST=1]
[*]Trying to run a photo gallery, images load painfully slow.
[*]I had a near lockup while transferring a .zip file near the RAM size.  This was via the webmin file transfer, not sure what protocol it uses.
[/LIST]

See my [thread]("http://ubuntuforums.org/showthread.php?t=1043288") for the above near lockup.

Other than than that, these old boxes make excellent servers.  They use much less electric than a Pent4 box.  My pent2 400MHz with one hard disk, ran under 40 WATTs for the entire machine.  It was my first PC, so I am hanging onto it for dear life.  I will now use it for testing and a backup for when I need to put my Intel Atom down for service/upgrades.

Enjoy

Thanks. My first pc was too a Pentium 3 450mhz. 128mb ram and Windows 98 :P

I ran win98 until 2007 when I bought Ubuntu from Ebay for $8...(I was looking for winxp).

---

### Post by linuxisevolution on 2009-03-15
> **hictio said:**
> Ohh... I see :D
For starters, I would add more RAM, if possible.

How many hits do you think that your Apache will receive, how much traffic?
What type of content does it serve?

It serves all the sites in my signature. I see mostly people downloading distros from [http://www.thelinuxhowto.co.nr](http://www.thelinuxhowto.co.nr) . I have about 6gb worth of Linux files for download on that page.

EDIT: I almost forgot, this machine is a squid server for about 4 other machines. The 3.1gb hard drive is just for the cache.

---

