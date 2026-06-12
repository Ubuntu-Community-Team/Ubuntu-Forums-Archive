---
title: "ubuntu server 14.04.  apt-get install results in Hash Sum Mismatch"
date: 2014-09-07
forum: Server Platforms
---

### Post by amalgamas on 2014-09-07
I have been trying to correct a «Failed to fetch... Hash Sum Mismatch»-error for the last couple of days.  I have tried every suggestion that I could find in forums and on google, including: 


                         
sudo fuser -vvv /var/lib/dpkg/lock
 sudo rm /var/lib/apt/lists/lock
 sudo cp -arf /var/lib/dpkg /var/lib/dpkg.backup
 sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
 sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
 sudo rm -rf /var/lib/dpkg/updates/*
 sudo rm -rf /var/lib/apt/lists
 sudo rm /var/cache/apt/*.bin
 sudo mkdir /var/lib/apt/lists
 sudo mkdir /var/lib/apt/lists/partial
 LANG=C;sudo apt-get clean
 LANG=C;sudo apt-get autoclean
 LANG=C;sudo apt-get --purge autoremove
 LANG=C;sudo apt-get update -o APT::Cache-Limit=25165824
 sudo dpkg --clear-avail
 sudo dpkg --configure -a
 LANG=C;sudo apt-get -f install
 LANG=C;sudo apt-get --fix-missing install
 LANG=C;sudo apt-get update -o APT::Cache-Limit=25165824 && sudo apt-get dist-upgrade

Nothing helps.  Now what?   Should I give up and reinstall?

Any advice will be appreciated

---

### Post by Bashing-om on 2014-09-07
amalgamas; Hi !

Maybe as a thought, one should focus attention on that single package rather than the system as a whole ?
Could be a lot of trouble, but ?
```

cat /var/lib/dpkg/info/<package_name>.md5sums 

```
list of MD5 hash values for files installed by the package. The installation of debsums enables verification of installed package files against MD5sum values in the this file.
Then one-by-one check the md5sum of each file ?

Unfortunately, I have been unable to complete my thought, as I have not found a means to find the hash value of a given original source file off-system.

Will continue to look for that means as I would think that the md5sum for 'files' would also be available as for the hash value of the complete .iso file.

[INDENT][INDENT]a thought worth putting more time in on[/INDENT][/INDENT]

---

### Post by amalgamas on 2014-09-08
Thank you for your reply!

Of course, if here is a way to find the correct checksum, I could check and manually reinstall single files each time I run into this.

But I wonder: is it worth it.  Reinstall of the complete system is a lot of hassle, may be it is worth it.  But do I have any guarantee that it will be better afterwards?

Best regards

---

### Post by Bashing-om on 2014-09-08
amalgamas; Welp;

I am a firm believer in directly addressing a issue by fixing the cause.
Still looking for a link to the original source md5sums. I would think they are available somehow, someway.
Verifying these md5sums I would think is the place to start. But, my Google-fu is presently failing me.

[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

### Post by amalgamas on 2014-09-29
Ok, so I took the box home from my office, backed up the home directory and reinstalled Ubuntu server 14.04.
 

 Everything worked fine, I updated and upgraded and installed a lot of stuff (LibreOffice, gnote ++) and kept the box at home fer a few days.  The dreaded “hash sum mismatch” error did not show up.
 

 Today I took it back to the office and hooked it into the office network.  After a few network tweaks and installations (cups, gnome-printer service) the error showed up again preventing me from installing further programs. 

 

 I immediately took it home again, hooked it up did an update and was able to install the software without the “hash sum mismatch” error.  I am still testing it at home, no error.
 

 Here are the data I can provide:
 

 Home:
 DHCP, cable network, my home ISP
 

 Work:
 Static ip, cable network, my work ISP (different from home ISP), the DNS nameservers are: #1: Local win 2012 server; #2: ISP nameserver 1
 

 I did not change repos or mirrors.  I also did not delete[FONT=Liberation Serif] /var/lib/apt/lists or do any other of the many suggestions one can find on the web.  [/FONT][FONT=Liberation Serif]The PC was the same in both situastions (DELL Poweredge T110).[/FONT][FONT=Liberation Serif]  In short: I only changed network setup to match the office [/FONT][FONT=Liberation Serif]network[/FONT][FONT=Liberation Serif]or [/FONT][FONT=Liberation Serif]my private network.  [/FONT][FONT=Liberation Serif]The network was set up by editing the /etc/network/interfaces file:[/FONT]
 

 ```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto em1
iface em1 inet dhcp

#iface em1 inet static
#  address 192.168.90.10
#  gateway 192.168.90.1
#  netmask 255.255.255.0
#  network 192.168.90.0
#  broadcast 192.168.90.255
#  dns-nameservers <ip of windows 2012 server>  <dns1 from ISP provider>

``` 
(I commented out line 10 and uncommented lines 12 – 18 for static ip at work)
 

 [FONT=Liberation Serif]and confirmed by inspecting /etc/resolv.conf and pinging external ip addresses.  [/FONT] 
 

 [FONT=Liberation Serif]Something obviously is wrong and I would appreciate suggestions on how to get rid of this.  It prevents my Ubuntu server from being of any use at work.[/FONT]

---

### Post by Bashing-om on 2014-09-29
amalgamas; Well.

above my skill level now, but I would think that the Windows' machine to be acting as a proxy server.
Might try changing "dns-nameservers" in '/etc/network/interfaces' to Google's name server(s) - 8.8.8.8 , 8.8.4.4 and see if you can still get out.

[INDENT][INDENT]there are those things
[INDENT][INDENT][INDENT]I do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by amalgamas on 2014-10-04
Still not solved!
 

 I did what was suggested, kept the server at home, checked everything I could think of, installed some software, ran update – upgrade.  Everything without any error messages.

 

 To day I took the machine back to the office, set it up with google DNS (8.8.8.8 8.8.4.4), but after some time I got the dreaded error message: “Hash Sum Mismatch”.  I disconnected the machine and took it home again, and guess what: no error message (still with google DNS).   
 

 Now I don't really know where to proceed.  I do not know of any problems with our office network.  There is no proxy and all windows PCs work correctly.  Next step will be to take an ubuntu laptop of mine to the office hook it up with the same network configuration as the server and test whether I get the error message with it.   

 

 Any advice will be appreciated, please help!

---

### Post by cariboo on 2014-10-06
It looks to me that the problem originates in your office network, is there any way you can connect it directly to the router, to eliminate the rest of the office network?

---

### Post by CharlesA on 2014-10-06
> **cariboo907 said:**
> It looks to me that the problem originates in your office network, is there any way you can connect it directly to the router, to eliminate the rest of the office network?

That would be the next step tbh.

There could be something on the network that is messing with the files as they are being downloaded too.

---

### Post by amalgamas on 2014-10-06
But, if there is something wrong with the office network, why should that give this error?  What is this "Hash sum mismatch..." thing anyway?

I will test this as soon as possible.  Coming back with results

Edit: I have forgotten to mention that this came after the upgrade to 14.04.  Before this the server ran for two years without any issues under 12.04.  Nothing in the office network has been changed

---

### Post by CharlesA on 2014-10-06
See here: [http://askubuntu.com/questions/41605/trouble-downloading-updates-due-to-a-hash-sum-mismatch-error](http://askubuntu.com/questions/41605/trouble-downloading-updates-due-to-a-hash-sum-mismatch-error)

Try using a different mirror.

---

### Post by amalgamas on 2014-10-06
Just now I ran some tests with my laptop, ubuntu 14.04.  Hooked it up to the office network with the same parameters as the server using network manager. The server was set up with command line parameters.   No errors.  I ran all tests I could think of (installing, removing, reinstalling, update, upgrade...).  Tomorrow I will try some more with the server.

Another mirror? I have tried that.

---

### Post by matt_symes on 2014-10-06
Hi

What caching does your work have ? What caching does your works ISP have ?

Kind regards

---

### Post by amalgamas on 2014-10-23
Update on this: the hash-sum mismatch error turns up from time to time, then disappears and everything works well.  There is probably something wrong in our network, but I have not been able to pin down the error yet. 

Strange thing is that our windows 7 machines do not seem to have any problems with this, all updates seem to work nicely.

---

### Post by cariboo on 2014-10-24
Just out of curiosity, what mirror are you using? If you aren't using one that updates right away, this could be the reason for the error.

---

### Post by amalgamas on 2015-02-04
This is now an old thread.  But I think I have solved the mystery.

My IPS finally agreed to give me a new router that was more configurable.  I set DNS to google's (8.8.8.8 and 8.8.4.4), then set the whole network to use the router as DNS server.

This seems to have solved the problem.  I developed a test (forced reinstall of the Chromium browser) which consistently failed while upgrades failed only on an irregular basis.  Now the Chromium reinstall works.

Thank you for your support, it gives me hope for the future

---

### Post by Bashing-om on 2015-02-04
amalgamas; Great;

No more sweating this one.

Thanks for providing the cause and the solution.
If this matter is now concluded;
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

### Post by amalgamas on 2015-02-05
Marked as solved (even if I wanted to wait for a while just to make sure...)

---

### Post by Bashing-om on 2015-02-05
amalgamas; Hey ;

> **amalgamas said:**
> Marked as solved (even if I wanted to wait for a while just to make sure...)

If there is a continued issue, you can remark this thread. Even as marked 'solved' - If there is a new entry in this thread, I will see it and respond.

[INDENT][INDENT]good things do happen
[/INDENT][/INDENT]

---

### Post by gacb on 2015-02-11
Some kind soul posted this fix on AskUbuntu:

sudo rm -fR /var/lib/apt/lists/*

It will take you to another command prompt and you should be able to run apt-get update normally. It worked for me.

---

### Post by Bashing-om on 2015-02-11
Agreed, the control files can become corrupted, or contain misleading information.
There are those times that removing these files, and rebuilding the data base resolves the situation.

[INDENT][INDENT]always best to know the why
[/INDENT][/INDENT]

---

