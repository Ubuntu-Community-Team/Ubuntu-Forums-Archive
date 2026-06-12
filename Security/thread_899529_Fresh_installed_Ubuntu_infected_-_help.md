---
title: "Fresh installed Ubuntu infected - help"
date: 2008-08-24
forum: Security
---

### Post by ekh on 2008-08-24
I have had my Hardy server infected, and my whole network.

Now I basically just try to get one clean Ubuntu machine for building it al bottom up again.

But making a fresh non-infected Ubuntu install seems very difficult.

Let me say that I have a suspicion, that someone ultimately wants to hit my computers. Why should I suddenly get so much trouble.

I have used Linux for 4 years, had an Ubuntu server for 2 years, and I have not seen any problems.

Then the day the internet DNS error was published, I could not ssh my server: Man in the middle attack. No damage to user files.

The computers on my net was able to access the net, but if I plugged the server internet plug into a non-infected Ubuntu machine, no network connection, I know the machine was OK.

If I took a computer from my network, they could not access the net neither as they used to be able to, only net access through my server.

So now I don't use computers from the infected network to access the net, I have backups and they seen normal, I took a portable to make a basis for repairing/reinstalling, and for mail and surfing the net.

I corrected my Linksys WRT54GL, original 1.1 firmware to use opendns as nameserver, and then I got access to the net. Later I found out there was 3 DNS servers, I only inserted 2. And the 3 only visible from the status page, not the setup page with only the 2 I inserted.

I then installed DD-WRT on the router, and that helped, but I still suspected something wrong.

I had problems under updates, I could not read the security updates, only the non security updates. 

A shift of server to Ubuntu main server did not help, but a French server gave access to the security updates.

Still something was wrong, lots of net traffic, then I cleared the few cookies I had and reinstalled Firefox, That helped a lot, but still something was wrong.

In /etc/hosts was an entry I did not insert and that I have never seen before, probably an intruding server.

Although the alien reference was deleted, it reappeared.

I now chose to reinstall yesterday.

Did the basic installs and the updates. The alien host in /etc/hosts was still there.

I deleted the host, and installed Firefox with some basic security add-ons. 

I then downloaded osssec-hids, but the checksum was wrong. I went in and out of tor and downloaded once more. This time the checksums was OK.

I installed ossec-hids and after some hours still with something not right, I tried to setup a fixed IP address. I had 3 failing unlock attempts before I succeeded to unlock (I think I know my long password very well now), I inserted the static IP address but it did not work, see hids log below:
 

Aug 24 17:39:00 t41n NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))


So this fresh install attempt from a CD downloaded long ago to get a non-infected Ubuntu on my portable, has not succeeded :-(

I am no security expert, I'm just in the beginning of a very necessary learning phase after 4 peaceful years with Linux, security wise.

I have surfed about 16 hours for how to do this, but apparently I don't know enough to prevent those criminals from destroying my install. They obviously don't want to delete all my files, but they control my computer.

How do I download a non-infected install disk ?
How can I be sure to receive non-tapered updates ?

Advice on how to insure a fresh non intercepted Ubuntu 8.04 install will be very welcome.

Thanks in advance.

ekh

---

### Post by rogeriopvl on 2008-08-24
There's something wrong in there. Are you sure that no one has physical access to you machines? Have you checksummed the Ubuntu CD?

That sounds very weird, I think that you missed something or if not, you might have the entire [RBN]("http://en.wikipedia.org/wiki/Russian_Business_Network") after your network.

Maybe now you should stop trying to clean the machine, and just "watch" every weird activity, to get info about who's doing it, what ports uses to access the system, etc. And make sure your backups are really ok.

---

### Post by panhandle on 2008-08-24
> Advice on how to insure a fresh non intercepted Ubuntu 8.04 install will be very welcome.

Why don't you order them directly from Canonical via standard mail? Then there is no chance of interception.

---

### Post by ekh on 2008-08-24
> **rogeriopvl said:**
> There's something wrong in there. Are you sure that no one has physical access to you machines?

My machines are located in my house. I work at home always, but leave the house occasionally. I have not seen any signs of physical intrusion.

I started saving files at midnight and had a fair amount of surfing to do the installation right. I stopped with a finished install 08:30, slept with the portable in my bedroom, and them started again when I woke up.

I don't expect I had "visitors" during this small time window.

> **rogeriopvl said:**
> Have you checksummed the Ubuntu CD?

I always check the md5sum of install CD's. I also did an integrity check on the Ubuntu 8.04 i386 alternative install CD.

> **rogeriopvl said:**
> 
That sounds very weird, I think that you missed something or if not, 

Maybe I have missed something, hard to say. I just know that I have done at least 8 installs the last 6 months without noteworthy problems.

> **rogeriopvl said:**
> you might have the entire [RBN]("http://en.wikipedia.org/wiki/Russian_Business_Network") after your network.

I don't suspect the Russians in this case, but the Americans.

My problems started after joining a yahoo group on alternative energy.
Some of the technology discussed there has been suppressed for over 100 years. Members of the group has had their harddisk wiped, one can access the net except the group. Only using dial-up allowed him to pass the suppessors filters. 

At this stage you may think I'm just crazy. I can tell I am an educated electrical HW and SW engineer, who has worked for 5 large companies for 25 years. Now I have my own small company.

First time I saw something about the alternative energy, I did not believe a word of it like many others. But my curiosity drove me to find university research reports on the subject, telling this was real.

Since I have seen some of this with my own eyes, this is very real !

[http://www.panaceauniversity.org/](http://www.panaceauniversity.org/)
[http://www.rexresearch.com/1index.htm#scitech](http://www.rexresearch.com/1index.htm#scitech)

However I'm not here to convince anyone, I just don't understand why I must be prevented my freedom of information to read "nonsence" of "no importance".


> **rogeriopvl said:**
> Maybe now you should stop trying to clean the machine, and just "watch" every weird activity, to get info about who's doing it, what ports uses to access the system, etc. And make sure your backups are really ok.

I agree, it could be interesting, I don't expect though to be able to match the knowledge of a suppressor team. 

The reality is I have to do ordinary work, and that includes a lot of surfing. Also I have to get my development tools up-to date

I am also very sorry my wonderful Ubuntu development workstation is infected. It is no 2 hour job to make an install with a lot of tools for embedded development.

I don't expect to get off the hook, now they know who I am. The question is if I can employ Ubuntu in the future, or it simply is not sufficiently safe for these high funded criminals. I would not be surprised they have the funds to have a parallel not so nice Ubuntu install disk. If that is the case. How do I know the real stuff from the infected ?

How can I be sure the updates are OK, when certificates are changed during the install, is this right ?

What do you say ?

ekh

---

### Post by ekh on 2008-08-24
> **panhandle said:**
> Why don't you order them directly from Canonical via standard mail? Then there is no chance of interception.

Others from the energy groups has reported ordinary mail intercepting, so how can I be sure the CD really is authentic ?

The reality as I see it, is that the CD I have probably is OK (downloaded it before I caught attention), but the suppressors intercept the updates so my system is infected from first boot up.

ekh

---

### Post by panhandle on 2008-08-24
I suspect that your problems are less conspiratorial than you think.

I assume you have checked your /etc/apt/sources.list?

---

### Post by ekh on 2008-08-24
> **panhandle said:**
> Have you used etherape to observe the routing of your internet activity?

No, as I told I'm no security expert, but I just installed etherape.

There was a server I don't know of, so I tested it with whois

root@t41n:/home/ekh# whois 224.0.0.251
No whois server is known for this kind of object.

As soon as I got the answer the picture disappeared from etherape.

Also hids was stopped, I started it again.

** Alert 1219601522.22312: mail  - syslog,errors,
2008 Aug 24 20:12:02 t41n->/var/log/syslog
Rule: 1002 (level 2) -> 'Unknown problem somewhere in the system.'
Src IP: (none)
User: (none)
Aug 24 20:12:01 t41n gdm[5464]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 

ekh

---

### Post by rogeriopvl on 2008-08-24
wow, this sounds very surreal.

this block of addresses (224.0.0.x) according to RFC 3171  is reserved for special purposes.

check this: [http://www.networksorcery.com/enp/protocol/ip/multicast.htm](http://www.networksorcery.com/enp/protocol/ip/multicast.htm)

---

### Post by wirelessmonkey on 2008-08-24
A quick google of the IP reminded me that 224.0.0/24 addresses are internal local network control addresses, .251 is DNS Multicast...
See [http://www.networksorcery.com/enp/protocol/ip/multicast.htm](http://www.networksorcery.com/enp/protocol/ip/multicast.htm)
If you have a machine or router that is doing internal DNS caching for you, that's probably the source.  

[Here]("http://lists.debian.org/debian-user/2007/08/msg02593.html") is a post on the debian mailing lists about a similar issue.  You may want to stop or restart avahi.


Best of luck.

---

### Post by panhandle on 2008-08-24
224.0.251 is the multicast DNS address used in zeroconf.

---

### Post by rogeriopvl on 2008-08-24
It would good if you could post some logs here, so I can help you. The boot log would be perfect. 
The IP address you just mentioned is used for multicast and is sometimes associated with zeroconf and mDNS/DNS-SD.

Edit: My guess is that maybe your machine is not compromised... just behaving weirdly because of some misconfiguration.

---

### Post by ekh on 2008-08-24
Thank you both for offering help, I really need it...

Now you tell about the multicast, I remember moblock has blocked that address regularly.

It is strange, when I monitor etherape and type "whois" and no more in a terminal window, then the etherape screen is cleared. They obviously monitor my keystrokes. This system is able to communicate on the forum, but apart from surfing it is garbage, I can not trust it.

I have read about hardened kernels, but is this something that is doable without being a kernel expert, and can it actually help me under these circumstances ?

I know I wil be under surveillance, and I can do nothing about it, I just wish I could keep them outside my computer.

I also read about a router running DHCP possibly leaking network adresses.
Could that also be something that makes it more easy to infect me ?

I run DD-WRT 1.24 on my Linksys WRT54GL router.

ekh

---

### Post by ekh on 2008-08-24
> **panhandle said:**
> I suspect that your problems are less conspiratorial than you think.

I assume you have checked your /etc/apt/sources.list?

I wish you are right.

Below are the contents of my /etc/apt/sources.list.

Somewhere in the hids documentation it is stated that the files viewed can not always be trusted, I cant say whether this is the case for me.

I just wonder why I have had problems reading the security updates both from a local country server and also the Ubuntu main server.

ekh

# 
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/](ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/) hardy main restricted
deb-src [ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/](ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/](ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/](ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/](ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/) hardy universe
deb-src [ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/](ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/) hardy universe
deb [ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/](ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/](ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/](ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/) hardy multiverse
deb-src [ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/](ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/) hardy multiverse
deb [ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/](ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/](ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/](ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/](ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/) hardy-security main restricted
deb [ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/](ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/) hardy-security universe
deb-src [ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/](ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/) hardy-security universe
deb [ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/](ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/) hardy-security multiverse
deb-src [ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/](ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/) hardy-security multiverse

---

### Post by ekh on 2008-08-24
> **rogeriopvl said:**
> It would good if you could post some logs here, so I can help you. The boot log would be perfect. 
The IP address you just mentioned is used for multicast and is sometimes associated with zeroconf and mDNS/DNS-SD.

Edit: My guess is that maybe your machine is not compromised... just behaving weirdly because of some misconfiguration.

I consider this a nearly naked install, I wonder what has gone wrong in that case. 

contents of /etc/default/bootlogd

# Run bootlogd at startup ?
BOOTLOGD_ENABLE=yes


contents of /var/log/boot

(Nothing has been logged yet.)

ekh

---

### Post by ekh on 2008-08-24
I just tried to start etherape, got the message:

Error getting device: no suitable device found

The system is beginning to put on pressure like just before I decided to reinstall. How can I post this message if no suitable device is found ?

Below is my response for ifconfig, HW address xxxx by me.

ekh

root@t41n:/home/ekh# ifconfig
eth0      Link encap:Ethernet  HWaddr xxxx 
          inet addr:192.168.10.100  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::211:25ff:fe2d:29d2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2221 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2036 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:2331229 (2.2 MB)  TX bytes:410478 (400.8 KB)
          Base address:0x8000 Memory:c0220000-c0240000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1666 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1666 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:83300 (81.3 KB)  TX bytes:83300 (81.3 KB)

root@t41n:/home/ekh#

---

### Post by rogeriopvl on 2008-08-24
Why are you using .fr repositories if you are from Denmark?

Another thing, you shouldn't use the root account.

---

### Post by ekh on 2008-08-24
> **rogeriopvl said:**
> Why are you using .fr repositories if you are from Denmark?


> **ekh said:**
> 
I had problems under updates, I could not read the security updates, only the non security updates. 

A shift of server to Ubuntu main server did not help, but a French server gave access to the security updates.


Thank you all for offering help.

As you see I did not succeed to get the security updates from neither the Danish server nor the Ubuntu main server. The French server worked.

> **rogeriopvl said:**
> Another thing, you shouldn't use the root account.

This is not my normal practice, but here I monitor log files all the time, and I have a long password. I don't know if this is an additional risk. I dont fear using wrong commands.

I tried to reinstall etherape, but it still gets the error, so no more etherape so far.

ekh

---

### Post by ekh on 2008-08-24
I have just installed once more.

I have been lucky to get an Ubuntu 8.04.1-alternate-i386 install CD.

I did the whole installation without internet.

Then I used the command line:

sudo apt-get update
sudo apt-get upgrade

Then I rebooted

After reboot i repeated

sudo apt-get update
sudo apt-get upgrade

There was no more updates, but... the tool tip of the update icon says 5 updates are available ???

ekh

---

### Post by rogeriopvl on 2008-08-25
Check what those updates are. It may be normal that behavior.

---

### Post by Nepherte on 2008-08-25
Those updates are probably held back. Do:
```
sudo apt-get dist-upgrade
```
and you'll get them. That or you just click on the update notification icon.

---

### Post by ekh on 2008-08-25
> **rogeriopvl said:**
> Check what those updates are. It may be normal that behavior.

Hi again, and thank you for being persistent :-)


ekh@t41n:/dev$ sudo apt-get upgrade
[sudo] password for ekh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  bind9-host dnsutils libbind9-30 libisccfg30
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
ekh@t41n:/dev$ 


The graphical update is ready to update the 4 mentioned above + also

libdns35


I do not understand why the command line and the graphical update does not agree on what is to be updated.

This last install did not require a change of certificates.

I installed the noscript add-onn, and then ossec again.

After some hours with no problems reported by ossec I installed Thunderbird and restored my email db, Still all seems good.

I have now installed vlc also (not run it yet), with no ossec anomaly complaints so far. It is nice to see ossec reports every single package changed, or newly added.

I run the ossec check every 600 seconds.

I use the lvm encryption option with 30+ character passphrase, and my password is now longer than ever, making it a bit annoying, but if thats what it takes, so it be.

Presently all is cool, I don't know whether this is caused by the system being secure, or a pause in the attack pressure. I get a little upset after what I have been through "wasting" two days of work.

I intend to use the system now, slowly adding a few things more to obtain a reduced set of apps to be in business again, internet wise.

Now I have the rest of the machines to fix also. Considering the large amount of time lost due to the attack, my local net will never be on the internet again. I will read into aptonCD to see if that can solve the problem of updating and installing new apps for me.

In the future an usb disk will be the transfer medium.

ekh

---

### Post by Nepherte on 2008-08-25
> **ekh said:**
> I do not understand why the command line and the graphical update does not agree on what is to be updated.
Don't worry. This actually is normal behavior. Check my last post.

---

### Post by ekh on 2008-08-25
> **Nepherte said:**
> Those updates are probably held back. Do:
```
sudo apt-get dist-upgrade
```
and you'll get them. That or you just click on the update notification icon.

Thanks, I just did the dist-upgrade. It resulted in a few more packages, all reported by ossec.

Now the graphical update icon is gone, so now it is consistent.

ekh

---

### Post by ekh on 2008-08-25
I could not deliver boot logs, but I'm not the only one

[http://ph.ubuntuforums.com/showthread.php?t=882219](http://ph.ubuntuforums.com/showthread.php?t=882219)

ekh

---

### Post by rogeriopvl on 2008-08-25
> **ekh said:**
> I could not deliver boot logs, but I'm not the only one

[http://ph.ubuntuforums.com/showthread.php?t=882219](http://ph.ubuntuforums.com/showthread.php?t=882219)

ekh


Yes I forgot that little problem, I constantly use fedora and ubuntu, fedora doesn't have that problem and I forget about it in Ubuntu.

I'm glad you have a stable system now :)

---

### Post by ekh on 2008-08-26
> **rogeriopvl said:**
> Yes I forgot that little problem, I constantly use fedora and Ubuntu, fedora doesn't have that problem and I forget about it in Ubuntu.

I'm glad you have a stable system now :)

Me too :-)

Thank you and thanks to all for helping me. It was really helpful as an infected system is bad, and the first reinstall did not help. 

The forum is a great thing, in the Linux world, the support is near when needed.

To give a little back in return, here is what might have caused the problem.

1. My Ubuntu server was installed with most facilities enabled, although I just used nfs and a dual firewall for allowing my local net access to the internet. I consider to make the next install as an ordinary desktop with nfs server installed, as my local net never again will be connected to the internet. I intend to download the needed repositories to my new "server" and update the local machines this way. Do you think a thin server would be better ?

I have too many embedded tools and programs outside Ubuntu, so I'm already tired by the though of the next reinstalls of the machines on the local net. Do any of you have some tricks on how to do this an automated way ?

2. My first reinstall was with Ubuntu 8.04 which required change of certificates, maybe that was intercepted. The first reinstall was behaving just as bad as the system I decided to reinstall in the first place.

3. For the second reinstall a 8.04.1 install disk was used. As I wasted a lot of time on the first reinstall, I tried my best to to avoid failure once more. I did this:


A. No internet cable connected during the initial install.

B. The encrypted LVM with passphrase "1234" install was interrupted shortly after the partition tables was written, somewhere during format.

C. The power cord and battery was removed, and the power button activated for a minute.

D. Battery and power added again, and normal install with long passphrase. This way I have tried to prevent malicious code from surviving somewhere in ram or on the disk.

E. I then added the internet cable and did:

sudo apt-get update
sudo apt-get upgrade

And as you told me to:

sudo apt-get dist-upgrade
sudo apt-get update

Install noscript add-on for Firefox before any surfing.
Install ossec-hids.
monitor the ossec logs, which this time did not show bad things phew.. :-)
 
I can't tell whether my extra tricks did the job, but the extra stuff was quickly done, and I wanted to do my best to avoid a 3'rd reinstall.

By the way it does not look convincing when Mozilla recommends an add-on and in the next step it says for eg. FoxyProxy (Author not verified).
Could an add-on be the source of trouble ? Any cases seen ?

ekh

---

### Post by cdenley on 2008-08-27
If you are concerned with government conspiracies, keep sensitive data offline. Anything that needs to be online should have no network services running and should be isolated from your private networks. Don't send any sensitive data over the net unless it is encrypted. Don't use SSL certificates that are identified as self-signed when they shouldn't be. If you suspect any security compromises, **change your password**. Don't put an SSH server online unless you know it's not using a weak key.
[http://www.ubuntu.com/usn/usn-612-2](http://www.ubuntu.com/usn/usn-612-2)
Also, OpenBSD is the most secure operating system I know of. Don't use any DNS servers that haven't been patched recently.
[http://www.doxpara.com/](http://www.doxpara.com/)
Always use tor+privoxy when doing web research you don't want the men in black to know about.

---

### Post by ekh on 2008-08-28
> **cdenley said:**
> If you are concerned with government conspiracies, keep sensitive data offline. Anything that needs to be online should have no network services running and should be isolated from your private networks. Don't send any sensitive data over the net unless it is encrypted. Don't use SSL certificates that are identified as self-signed when they shouldn't be. If you suspect any security compromises, **change your password**. Don't put an SSH server online unless you know it's not using a weak key.
[http://www.ubuntu.com/usn/usn-612-2](http://www.ubuntu.com/usn/usn-612-2)
Also, OpenBSD is the most secure operating system I know of. Don't use any DNS servers that haven't been patched recently.
[http://www.doxpara.com/](http://www.doxpara.com/)
Always use tor+privoxy when doing web research you don't want the men in black to know about.

Thank you very much for your advice and links, a bookmark is added :-)

Using Tor-Proxy.Net my problems with

"www.bilsyn.dk uses an invalid security certificate"

described in this thread

[http://ubuntuforums.org/showthread.php?t=902226](http://ubuntuforums.org/showthread.php?t=902226)

"magically" disappeared. Now it works like it should do, and does for every one.

The purpose of the site is to reserve time for a technical inspection of a car. So because of my record in surfing I must be prevented from this "highly confidential" site.

A free citizen in a free country with laws to enforce the freedom of speech ?

The MIB's and the ones ordering their work want power and total control, not civil rights and freedom of speech !

---

### Post by ekh on 2008-08-29
Now my computer is infected again. No direct sign of the infection in Ossec log, except it reports a lot of incidents:

Ossec says:

** Alert 1220028847.7023: mail  - stats,
2008 Aug 29 18:54:07 t41n->/var/log/syslog
Rule: 11 (level 8) -> 'Excessive number of events (above normal).'
Src IP: (none)
User: (none)
The average number of logs between 18:00 and 19:00 is 27. We reached 278.

** Alert 1220039974.7277: mail  - stats,
2008 Aug 29 21:59:34 t41n->/var/log/syslog
Rule: 11 (level 8) -> 'Excessive number of events (above normal).'
Src IP: (none)
User: (none)
The average number of logs between 21:00 and 22:00 is 57. We reached 308.

/var/log/syslog

Aug 29 13:25:18 t41n dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.10.7 port 67
Aug 29 13:25:18 t41n dhclient: DHCPACK of 192.168.10.80 from 192.168.10.7
Aug 29 13:25:18 t41n dhclient: bound to 192.168.10.80 -- renewal in 48 seconds.

and lots of them until

Aug 29 21:57:42 t41n dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.10.7 port 67
Aug 29 21:57:42 t41n dhclient: DHCPACK of 192.168.10.80 from 192.168.10.7
Aug 29 21:57:42 t41n dhclient: bound to 192.168.10.80 -- renewal in 50 seconds.

The weird about this is my computer has the static address 192.168.10.20 while this is going on, and I surfed the net during this period.


My infected computer can access the internet, A non infected portable, which has not been used for months, but is perfectly OK, can not access the net.

But it could ping the router that connects the infected computer to the net. Got it off as soon as I saw that.

What a wonderful world. Now I have not been able to do my ordinary work for a week.

---

### Post by ekh on 2008-08-30
Just to let you know. I'm infected once more.

I have now wasted 8 days with this, after 3 years of no significant problems.

Although I love Ubuntu when it is functional, for this 5'th reinstall I now give it a shot with another operating system.

The ones able to say:

Wow...I, uh, just use ABP and NoScript. LOL

Be happy you are in that position. I can't even access https pages anymore, no matter what, no Yahoo and no ebay, even the new password received during an ebay service chat does not work.

---

### Post by rogeriopvl on 2008-08-30
Man, that is really the weirdest thing I've ever heard. I think you should really try another distro to check if the same happens. Try something like fedora.

You can also try the hardcore OpenBSD, it's a excellent OS, but very limited for desktop use. FreeBSD might be a better option.

As a last resort, you should also try to change ISP...

---

### Post by ekh on 2008-08-31
My conclusions on the security of Ubuntu:

1. If someone skilled in the art want to abuse your system via an internet connection they can in less than 4 hours.
2. The intruders patch the binary files normally invisibly, so everything looks normal.
3. They are in total control of your system, and they can monitor individual keystrokes in real time.
4. If you employ Ossec to try detecting when (not "if" you loose control) they first try to stop Ossec from working.
5. When the stop is countered, then Ossec is "accepted" but permissions are changed, so it gets difficult to access the logs.
6. They prevent the copy of the log files to a removable media. I found a workaround though.
7. They make multiple attempts to configure the WiFi interface, maybe because that could ease their attempt to get non-interrupted access to the system.
8. The initial attack was for surveillance only.
9. But monitoring the attack with Ossec, the attack changed strategy, to stopping me from accessing the net.
10. I do not have the skills to stop the attackers from compromising my system using Ubuntu.
11. If you are too successful detecting the attack, your LUKS password becomes unusable, and the attack evidence definitely hidden, unless great efforts are used. I think I know how the disk contents can be reestablished in less than 2 days, not tested though.

--------------

These conclusions is based on a base installed system 8.04.1
This disk was downloaded long before I got attacked, and the checksum was verified then.

The system, a Lenovo t41 has been installed with no internet connection.
Then /etc/apt/sources.list has been edited to enable the repositories disabled by the initial install without net.
Then the system has been updated via the internet.
Ossec (with correct checksums) has been installed, initialized and started.
Then the system has been used for surfing only + watching logs.

In less than 4 hours the system gets infected. It has now happened 4 times within a week on a reinstalled system.

I have used Linux for more than 4 years, and Ubuntu for more than 2 years, and made more than 25 Ubuntu installs.

I'm an EE, and has worked as an embedded SW developer for 26 years.

As I previously mentioned, I don't consider myself a security expert, although I have been part of a team developing a system not intended for, but anyway well suitable for surveillance. The attacks on my Ubuntu box goes beyond my skills, patience, and resources. One week of heavy reading on security issues has not been successful.

I do not participate in illegal activities, but despite this, I consider my civil rights for privacy important, my thoughts are mine, and mine only, also when stored an a computer.
Whether Ubuntu is constructed with well hidden handles for surveillance, or this is not intended, I can not tell.

Surveillance is not bad in all cases, ie. I'm glad the special police have an incredible success rate at identifying possible terrorists in the western world. To tell how skilled the police is, I can tell there has been 3 big terror cases in Denmark. In the first two, the evidence was weak, and there was problems getting convictions. When a 3'rd case emerged, the police learned the lesson from previous mistakes. They wired and mounted cameras in every room of the suspects apartments, and actually got videos of the suspects producing (the b word, you know what i mean, like London an Madrid ). That is a very strong evidence in court !

This issue however has other solutions not necessarily inflicting civil rights, but possibly the greed of powerful people.

Using a system open for surveillance is not a problem, if no persons exist wishing to harm you in any way.
This can however not be considered true, neither from governments nor ordinary criminals.

Unless any from the Ubuntu community considers this important to follow up trying to improve the system, this is my final post in this thread.

---

### Post by tw33k@ on 2008-09-24
While seaching a solution for a 'problem' I had I came across this thread and the closely related [<<How do I use Ubuntu without Ubuntu>>]("http://ubuntuforums.org/showthread.php?t=912996").

Now I must say that I'm a bit of an anarchist punk at heart but I think we should stay to the purpose of these forums, a technical resource that supports an opensource product.

That brings me to the point that I feel I should make. You (ekh) have stated that you are not a security expert. That describes the majority of the people that use the good old internet, and a fairly large portion of Gnu/Linux users also. Unless you work in the IT&C and security industries there is no need to be an expert.

All you need to do is make an effort to remain up to date with the applications/services that you use. If you need to set up servers such as samba/cups, NIS, NFS, DNS and so on, then you only need to try and be well aquainted with those services and their vulnerabilities. Then disable/uninstall/block anything you don't need (this includes ports aswell as software). That is the reason why properly set up servers have no X windowing, multimedia or such like. Keep it to a bare minimum and know what you need to.

For example my home network consists of only a router, a PPC set up as an SMB file server, my Gnu/Linux box and my housemates' WinXP box. The file server is installed with Gentoo, a hardened kernel I compiled (its easier than most people assume) the very basic utilities for operation/admin, samba and ssh.

Just keep it simple and up to date. No degree or doctorate required for that.

You have so many options available in distributions, configurations and applications. And the benefit of all Gnu/Linux systems is that if you are willing to put a bit of effort into it, you can control everything yourself (not dependent on any one group or company...)

---

