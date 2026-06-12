---
title: "Samba does not start on boot-up"
date: 2010-03-22
forum: Server Platforms
---

### Post by alecz20 on 2010-03-22
My problem is that the samba daemon does not start on boot-up anymore on my file-sharing server.
Samba starts flawlessly if start it manually.

If I run:
```

/etc/init.d/samba status

```
I get :
```

 * nmbd is not running.
 * smbd is not running.

```

This started to happen after tried to add a script at start-up using 
```

update-rc.d script defaults 60

```

After running that, I noticed that the file /etc/init.d/samba was GONE !!!

I did a samba purge, and re-install, and the file re-appeared, but the samba daemon does not start automatically.

I restored smb.conf from a back-up, and also tried
```

update-rc.d samba defaults 60

```

I also added
```

(sleep 20 && /etc/init.d/samba restart)&

```
to /etc/rc.local. but to no avail.

Ironically, the script that I wanted to add at startup works, but the samba script doesn't work.

Also, I could not find any log files that could indicate that the samba daemon starts, or fails to start.
The file /var/log/samba/*.log are not helpful at all.

It is extremely frustrating to have a file-server that cannot share the files. Everytime there is a power failure I have to ssh into the machine and start samba manually.

---

### Post by lykwydchykyn on 2010-03-22
update-rc.d just basically creates symlinks in the appropriate /etc/rcX.d folders.

I assume you're booting to runlevel 2, which is Ubuntu default.

If so, just go to /etc/rc2.d and run this:
```

sudo ln -s /etc/init.d/samba S60samba

```

You might want to check /etc/rc2.d for a KXXsamba entry, just to be sure.  If there is a link to samba starting with "K", remove it.

---

### Post by alecz20 on 2010-03-22
I tried your suggestion, and created the link.

Also there was no KXXsamba entry in rc3.d

However it did not help.

Moreover, I realized that the apache2 server does not start at boot-up either.

I have a feeling I will have to re-install EVERYTHING

---

### Post by alecz20 on 2010-03-22
Just to drop a note here.

I do not have winbind in /etc/init.d

also there is not directory named /etc/init

I am running Ubuntu 8.10

Is all this normal?

---

### Post by lykwydchykyn on 2010-03-22
winbind is not strictly required for samba, so it's possible that it's not installed even if samba is.

The lack of a /etc/init folder is troubling.  That would certainly break your init system.  

Is the sysv-rc package installed?

EDIT: ok, I'm running 9.10, and I don't have an 8.10 system handy to compare.  I do know that the whole init system got an overhaul sometime within the last 3-4 versions, so exactly what should or shouldn't be there in 8.10 I cannot say.

---

### Post by alecz20 on 2010-03-23
I upgraded to 9.04 in the hope that the whole init system will be fixed.

It did not help. Neither samba nor apache start at boot.

Also, there is not /etc/init folder either. I have 9.10 on my laptop and I have /etc/init and /etc/init.d folders.

I started the upgrate to 9.10, and will see if the folder appears.

Also, I should mention that I did not delete any directories, and that both samba and apache used to start.

---

### Post by alecz20 on 2010-03-24
After upgrading to 9.10 I get the /etc/init folder, but still

**SAMBA and Apache do not start on boot!**

I am starting to get fed up with this:
- important services for file-sharing and web-serving do not start
- logs do not show anything related to the issue
- everything used to work fine until I added a script to startup
- adding (sleep 30 && /etc/init.d/samba restart)& in /etc/rc.local does not help
- samba and apache start manually without a problem.
- running update-rc.d samba defaults does not help either.

What am I supposed to do now? Re-install and re-configure the whole system every-time this happens?

---

### Post by lykwydchykyn on 2010-03-24
Is the sysv-rc package installed?

You say it was working fine before you installed the script, but are you certain?  How long before that had it been since you rebooted? 

Is it possible you installed or upgraded something that might have removed a critical package?  

Don't get panicky here. The problem here is that we haven't discovered the problem yet.  On a normally functioning system, adding scripts to startup does NOT bork the whole init system.  So clearly something else is wrong here.

---

### Post by alecz20 on 2010-03-24
```

sysv-rc is already the newest version.

```
I had never done any updates on the machine, maybe except critical updates that are done automatically.

Now that you mention it, it might be possible that the problem occurred once before I automated the script, but I am not sure.

I know I wanted make some changes in BIOS so the system will reboot on power failure. To test this, I had to simulate a power failure.

It could also be possible that some file got corrupted during this simulation.

How could I fix this package if it is corrupted?

---

### Post by lykwydchykyn on 2010-03-24
You can try 
```

sudo aptitude reinstall sysv-rc

```

I'm not sure what package sets up /etc/init.  apt-file doesn't seem to show them in any existing package, but they are certainly supposed to be there.

---

### Post by doas777 on 2010-03-24
just out of curisority,  do you have an IP address/net connection at the time samba tries to load? it will exit if it doesn't have one. you can find a trace in the dmesg if that is the case.

---

### Post by stuartsiegler on 2010-03-28
This doesnt seem isolated;  I have the same issue (but with vmware and openvpn, etc).  Some start while others dont....

---

### Post by alecz20 on 2010-03-29
> **doas777 said:**
> just out of curisority,  do you have an IP address/net connection at the time samba tries to load? it will exit if it doesn't have one. you can find a trace in the dmesg if that is the case.

I have studied the issue you are mentioning, and I do not think that my problem is related.

I have looked in dmesg but I found nothing suspicious.

You can have a look if you want; I have attached it.

Also, to respond to lykwydchykyn:

Unfortunately I did not get the chance to reboot the server after the re-installation of sysv-rc. The server was busy and could not be rebooted.

I will update the forum after I test that.

---

### Post by alecz20 on 2010-04-01
Reinstalling the **sysvrc** package did not help.

Neither samba, nor apache start on boot-up.


I don't understand why some lines in rc.local are processed an others are not or if they are why aren't any errors logged?

Any way to increase the verbosity of samba or apache?

---

### Post by capscrew on 2010-04-01
> **alecz20 said:**
> Reinstalling the **sysvrc** package did not help.

Neither samba, nor apache start on boot-up.


I don't understand why some lines in rc.local are processed an others are not or if they are why aren't any errors logged?

Any way to increase the verbosity of samba or apache?

It appears that you are using a DHCP supplied IP address for this host.  Doaz777 touched upon the issue: "just out of curisority, do you have an IP address/net connection at the time samba tries to load? ..."

Samba in particular will not load if the host does not appear to have an IP address.  This is a timing issue. I believe your DHCP supplied address is supplied after you login.

The host should have a static IP address (as in manually configured via the [FONT="Courier New"]/etc/network/interfaces[/FONT] file).  A *reserved *address via DHCP is not the same thing.

---

### Post by alecz20 on 2010-04-04
Just to re-cap, I want to say that this problem did not occur for more than a year. It is true, that I only rebooted the server a couple of times, but samba was always starting.

I followed your suggestion, and I edited the /etc/network/interfaces as follows:
```


iface eth0 static
address 192.168.0.100
netmask 255.255.255.0


```

I also reconfigured the router to allow for static IP's.

The network works, I can ping the computer, but I cannot ssh into it, I get 
```

ssh: connect to host 192.168.0.100 port 22: Connection refused

```

I assume that either I did a mistake in the /etc/network/interfaces or the problem is a different matter, and the modification to this file only made it worse.

Also samba still did not start.

EDIT:

BIG PROBLEM NOW:
```

init: networking main process (777) terminated with status 1

```

Then it hangs.

Now I am in big trouble... I cannot access the file and make it back the way it was because I cannot login. Moreover, this server uses LVM.

---

### Post by capscrew on 2010-04-04
> **alecz20 said:**
> Just to re-cap, I want to say that this problem did not occur for more than a year. It is true, that I only rebooted the server a couple of times, but samba was always starting.

I followed your suggestion, and I edited the /etc/network/interfaces as follows:
```


iface eth0 static
address 192.168.0.100
netmask 255.255.255.0


```

I also reconfigured the router to allow for static IP's.

The network works, I can ping the computer, but I cannot ssh into it, I get 
```

ssh: connect to host 192.168.0.100 port 22: Connection refused

```

I assume that either I did a mistake in the /etc/network/interfaces or the problem is a different matter, and the modification to this file only made it worse.

Also samba still did not start.

You need two more items in your /etc/network/interfaces file.  These are the command to bring up the interface upon booting (see my entry in red) and the default gateway (in blue).

```

[COLOR="Red"]auto eth0[/COLOR]       #this is to activate the interface when booting up
iface eth0 static
address 192.168.0.100
netmask 255.255.255.0
[COLOR="Blue"]gateway 192.168.0.1[/COLOR]    # or whatever the router's nearside interface is

```

---

### Post by alecz20 on 2010-04-04
Thanks for the reply.

Unfortunately, the system now hangs because of the mistakes in /etc/networking/interfaces

I cannot login anymore, and thus I am unable to fix the file.

I tried from a USB-flash drive, but that doesn't boot either. I think I need a LIVE CD and a CD-ROM Drive to get these fixed.

Now my problem is this:
[https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/512253](https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/512253)

---

### Post by capscrew on 2010-04-04
> **alecz20 said:**
> Thanks for the reply.

Unfortunately, the system now hangs because of the mistakes in /etc/networking/interfaces

I cannot login anymore, and thus I am unable to fix the file.

I tried from a USB-flash drive, but that doesn't boot either. I think I need a LIVE CD and a CD-ROM Drive to get these fixed.

Now my problem is this:
[https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/512253](https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/512253)

Wow, that sure screws things up.  I have always configured my interfaces manually with no problems.  I know that Network Manager can cause problems, but I have never heard of this.

My servers are non-gui, so the only way to configure them is manually.

---

### Post by alecz20 on 2010-04-06
I fixed the booting.

Apparently all I had to do was to edit the entry in GRUB. I just added "init=/bin/bash" at the end of the line that had "kernel". then I booted into a bash shell, and I modified the faulty config file. It turned out I typed ```
iface eth0 intet static
``` instead of ```
iface eth0 inet static
```

When I will get some time I will try your suggestion again, but correctly.

---

### Post by huwjenjinn on 2010-04-06
I've not read all of the above posts but just in case this is of use to any newbies on here I had problems getting both Samba and CUPS to start up on boot. Ubuntu 9.10. Both services happily started manually but never on boot.

I traced the problem to my /etc/init.d/rc script which I'd modified some months previously without really understanding what I was doing ;) 

Basically I'd set the CONCURRENCY variable to SHELL from its default NONE, thereby introducing a seemingly random boot sequence for my services and so preventing Samba and CUPS from coming up on boot. Simply changing concurrency back to NONE fixed all of this for me. A little knowledge etc.

---

### Post by n6yga on 2010-04-06
I was under the impression that CONCURRENCY was broken in Karmic. So I've heard...

Meaning it should ALWAYS be set to NONE.

Mark.

---

### Post by alecz20 on 2010-04-08
I checked my /etc/init.d/rc file, and the CONCURRENCY is set to NONE.


I have correctly modified the /etc/network/interfaces file the way CAPSCREW suggested.

There was one error in his suggestion, that he was missing **inet**

Also, if anyone is trying this, I would suggest to run
```

sudo /etc/init.d/networking restart

```
to verify that the file was modified properly.

Now I rebooted my system but samba and apache2 still don't start.

**So... manually assigning an ip to the network card did not fix the problem.**

---

### Post by huwjenjinn on 2010-04-09
> **n6yga said:**
> I was under the impression that CONCURRENCY was broken in Karmic. So I've heard...

Meaning it should ALWAYS be set to NONE.

Mark.

Since I posted that I took a look around at the setting and it seems to be a not entirely uncommon problem ([http://ubuntuforums.org/showthread.php?t=1305226&highlight=concurrency](http://ubuntuforums.org/showthread.php?t=1305226&highlight=concurrency)) with Ubuntu 9.10 and Upstart 0.6.3-11. Others appear to have fixed their systems by backporting to Upstart 0.6.3-10. Either way a combination of Upstart 0.6.3-11 and the CONCURRENCY=SHELL setting seems to be causing confusion and delay, to quote the fat controller.

I don't think I'm about to try the backported 0.6.3-10 Upstart anytime soon, I'm already in the dog house with Mrs Enjinn for spending quite so long on this in the first place ;)

---

### Post by alecz20 on 2010-05-05
I re-installed the system, and now SAMBA boots correctly.

We weren't able to troubleshoot this issue which is a bit concerning. If the OS needs to be re-installed everytime a service fails to start on boot, I am starting to ask myself serious questions.

On the other hand mediatomb service still fails to start with upnp error -117.

---

