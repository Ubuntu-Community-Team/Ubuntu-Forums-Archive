---
title: "Can't get dhcpd to start. subnet_number():inet.c:53: Addr/mask length mismatch"
date: 2012-06-28
forum: Server Platforms
---

### Post by AlexBooton on 2012-06-28
I originally asked this question in the General Help category which may have been a mistake.  Especially since I've had no answers.

So at the risk of being accused of cross posting, here goes.

Sorry if this is a bit lengthy.  I'm venting a bit about the problems...

I installed isc-dhcp-server6.  

First of all, is this the dhcp server I should be using?  It seems to be buggy.  The first problem I ran into was it was looking for /etc/dhcp/dhcpd[SIZE="4"][COLOR="Red"]6[/COLOR][/SIZE].conf but isc-dhcp-server6 installed /etc/dhcp/dhcpd.conf (i.e. no "6")!

After tearing my hair I finally set up a hard link to make sure I had both conf files.

OK, I got past this hurdle but now, when I try to start to run the server syslog says:>  subnet_number():inet.c:53: Addr/mask length mismatch and does not start.

I have no idea what that means but suspect the problem is in the dhcpd.conf file so here it is (with comments removed):

```
ddns-update-style none;

option domain-name-servers 208.67.222.222, 208.67.220.220;

default-lease-time 600;
max-lease-time 7200;

authoritative;

log-facility local7;

subnet 192.168.0.0 netmask 255.255.255.0 {
  option broadcast-address 192.168.0.255;
  default-lease-time 6000;
  max-lease-time 72000;
  option routers 192.168.0.189;
  option subnet-mask 255.255.255.0;
  range 192.168.0.10 192.168.0.100;
  option ntp-servers 192.168.0.189;
  option netbios-name-servers 192.168.0.189;
  option netbios-node-type 8;
}
```

Any help, suggestions or wags would be greatly appreciated.

AB

---

### Post by Doug S on 2012-06-29
I also saw your posting on the "general" forum. I did search around a bit for information on your problem. I don't really know the answer, but since nobody else has replied...
 
The information on "6" is somewhat confusing. I am wondering if it is expecting IPV6 type addresses or something. I would suggest to try and install the regular one (which I have been running for a couple of year), and as per the ubuntu server guide:```
sudo apt-get install isc-dhcp-server
```
Perhaps get rid of the "6" one first.

---

### Post by AlexBooton on 2012-06-29
Doug,

Thank you so much for your reply!  

I just can't figure out what's going wrong.

I took your advice and uninstalled isc-dhcp-server (which had really installed isc-dhcp-server6).  

At the same time I noticed that dhcp3-server was also installed so I uninstalled that too.

And finally re-installed isc-dhcp-server (which installed isc-dhcp-server6).  

So I guess "6" is the latest version.  And very possibly buggy.

Anyway, it still doesn't work and seems to have with the same issues as before.  Here's a snippet from syslog:

```
Jun 29 12:33:10 mbh dhcpd: Wrote 0 leases to leases file.
Jun 29 12:33:10 mbh dhcpd: subnet_number():inet.c:53: Addr/mask length mismatch.
Jun 29 12:33:10 mbh kernel: [  811.613458] init: isc-dhcp-server6 main process (6329) terminated with status 1
Jun 29 12:33:10 mbh kernel: [  811.613504] init: isc-dhcp-server6 main process ended, respawning
```

It tries to spawn isc-dhcp-server multiple times and then quits.

I've tried to find info on
```
inet.c:53: Addr/mask length mismatch.
```
but can't find anything useful.

The odd thing is I can still run it from a terminal with 
```
dhcpd -f
```
and that seems to work.  

Why it works is a complete mystery.

In total desperation, I'd like to know if I can start dhcpd (not isc-dhcp-server) automatically at startup. 

I tried putting it in rc.local but it didn't work. 

Any ideas on how to fix this would be greatly appreciated.

AB

---

### Post by AlexBooton on 2012-06-29
P.S.  Is there any way to ditch isc-dhcp-server6 and just install isc-dhcp-server (w/o the 6)?

I suspect the "6" version isn't ready for prime time!

Thanks,

AB

---

### Post by hawkmage on 2012-06-29
How did you install the dhcp server?  Did you build and install it your self of via apt-get?

Also what version of Ubuntu are you running?

If you built/installed it your self the bruit force method to fix it is to edit the startup script and remove the "-6" from the line that starts the dhcpd.

It is not a matter of the IPv6 version not being ready it is more of the fact that the dhcpd process can onle deal with IPv6 or IPv4 not both.  Since you have isc-dhcp-server6 the IPv4 addresses in the config file are considered to be malformed.

---

### Post by AlexBooton on 2012-06-29
Hi hawkmage,

I installed it via synaptic (that's another problem but the Ubuntu Software Center doesn't work for me via a VNC connection; and that's how I manage the server).

I did not build it myself.

This is on a newly installed U12.04 box.

So, what can I do?

1. Is there a way to tell "6" to work on IP4 only?  That's all I want for now.

2. Can I somehow get the non "6" version?

3. Something else?

Many thanks,

AB

---

### Post by hawkmage on 2012-06-30
For #1 I already mentioned that you can edit the isc-dhcp-server6 start up script and remove the "-6" from the command that actually starts the dhcpd process.

For #2 first save a copy of the dhcp config file you created. remove the isc-dhcp-server6 package the way you installed it, using synaptic.  Then look for the "isc-dhcp-server" package in synaptic and install it or if it is not there run the following from the command line:
```
sudo apt-get install isc-dhcp-server
```

I would suggest that if you are going to do remote management of any version of Linux you should get familiar with the command line and not have to rely on a GUI interface.

---

### Post by AlexBooton on 2012-06-30
Hi hawkmage,

Thanks for your help.  I sense you're a bit frustrated with me ;)

But here's the problem.

Installing isc-dhcp-server simply installs version 4.1.ESV-R4-0ubuntu5.1 which is in fact the "6" version.

Once installed (by apt-get install or synaptic) you end up with the "6" version only.  I know.  I just did it.

Once installed, trying to launch isc-dhcp-server simply yeilds an "unknown job" message.  You can only try to launch the "6" version.

Likewise modifying the isc-dhcp-server6 start up script only results in the script trying to launch the NOT "6" version which fails again with the "unknown job" message.  I know.  I just tried it.

So I'm back to square one trying to figure out how to get the dhcp server running.  I'd use a different dhcp server if that would help; but would not know what other server might be workable.

Bottom line is the current version must be working for some people and they can't all be using IPv6.  So why isn't it working for me?

Your help is appreciated!

AB

---

### Post by Doug S on 2012-07-01
Hi: Somehow we must be missing something with our communications via this thread.
On my test server computer, I had an installed extra NIC card, so far unused. I added some stuff to /etc/network/interfaces to make use of it. I installed dhcpd, with the command we have been referring to:```

sudo apt-get install isc-dhcp-server

```As far as I know, I didn't end up with the "6" thing. I edited /etc/dhp/dhcpd.config for the new sub-net on the now enabled NIC card. re-started the computer and, as far as I know, it all worked fine. The only thing I haven't done is actually hooked up a computer on the new subnet to verify that it gets an IP address assigned, as I don't have a spare switch or crossover cable (maybe later I can figure out a way to try it).

---

### Post by AlexBooton on 2012-07-01
> **Doug S said:**
> As far as I know, I didn't end up with the "6" thing. I edited /etc/dhp/dhcpd.config for the new sub-net on the now enabled NIC card. re-started the computer and, as far as I know, it all worked fine. The only thing I haven't done is actually hooked up a computer on the new subnet to verify that it gets an IP address assigned, as I don't have a spare switch or crossover cable (maybe later I can figure out a way to try it).

Hi Doug,

Thanks for your input.

You're absolutely correct!

I've now set up a second U12.04 box which, AFAICS is just the same as the first.  Installed isc-dhcp-server and DID NOT get the "6" version. 

Next I copied my /etc/dhcp/dhcpd.conf from the first box and started the dhcpd server.  It runs fine!

So now I'm trying to figure out why the first system acts differently.

I know something, some setting, somewhere is different and wrong.  But don't have a clue as to what or where.

If anyone can offer some suggestions I'd be very grateful.

AB

UPDATE:  I did an apt-get purge isc-dhcp-server.  I noticed it removed /etc/dhcp/dhcp.conf AND /etc/dhcp/dhcp6.conf.

Then an apt-get install and both conf files came back.  And it still insists on running "6".

Why?

---

### Post by AlexBooton on 2012-07-01
I think I found a workaround.  I won't mark this as solved because I still think there is something wrong and the workaround should not have been necessary.

The fix was to edit the network connections for both eth0 (WAN) and eth1 (LAN) and set IPv6 settings to "Ignore".

Why did I have to do this?  My second, almost identical box has those same settings at "Automatic" and dhcpd worked the first time I ran it.

Why?  :???:

---

### Post by hawkmage on 2012-07-02
I am not frustrated with you.  

In the default Apt repositories in Ubuntu 12.04 I do not see a package isc-dhcp-server6 even using synaptic, what version of Ubuntu are you running?  Also have you added any 3rd party repositories for apt?  

I built a clean VM with Ubuntu 12.04 Server and ran the command I gave you and I have the following:
```
hawkmage@userver:~$ ls -l /etc/dhcp/
total 16
-rw-r--r-- 1 root root 1791 Apr 10 11:08 dhclient.conf
drwxr-xr-x 2 root root 4096 May  1 14:30 dhclient-enter-hooks.d
drwxr-xr-x 2 root root 4096 May  1 14:30 dhclient-exit-hooks.d
-rw-r--r-- 1 root root 3602 Apr 10 11:08 dhcpd.conf
hawkmage@userver:~$ ls -l /etc/init/isc-dhcp*
-rw-r--r-- 1 root root 1684 Apr 10 11:08 /etc/init/isc-dhcp-server6.conf
-rw-r--r-- 1 root root 1673 Apr 10 11:08 /etc/init/isc-dhcp-server.conf
hawkmage@userver:~$ ls -l /etc/init.d/isc-dhcp*
lrwxrwxrwx 1 root root 21 Apr 10 11:09 /etc/init.d/isc-dhcp-server -> /lib/init/upstart-job
lrwxrwxrwx 1 root root 21 Apr 10 11:09 /etc/init.d/isc-dhcp-server6 -> /lib/init/upstart-job
hawkmage@userver:~$ 
```
You will notice that there are the files there for both the IPv4 and IPv6 DHCP daemon.  By default it only puts the shcpd.conf file for the IPv4 dhcpd and not for IPv6.  

The binary for the dhcpd is the same for IPv4 and IPv6, the thing that differentiates how it functions is the command line option "-6" that makes it funciton as an IPv6 dhcp server.

---

### Post by AlexBooton on 2012-07-02
Hi hawkmage,

Please see my prior post re a workaround.  

I know what what you've been describing is how it should be.  It just was not that way for me.

There is clearly something wrong with my installation.

This is not the only issue.  I've posted about others but have not found a sulution.

Thanks for your help,

AB

---

### Post by hawkmage on 2012-07-02
I am trying to get the the bottom of why your installation is not functioning as I would expect.  To allow me to do this please answer the questions I asked in my last post:
> what version of Ubuntu are you  running?  Also have you added any 3rd party repositories for apt?  

After the questions the rest of the post was, as you pointed out, how it should be and I was including it to indicate why I was asking the questions I did.

---

### Post by AlexBooton on 2012-07-02
> **hawkmage said:**
> I am trying to get the the bottom of why your installation is not functioning as I would expect.  To allow me to do this please answer the questions I asked in my last post:


After the questions the rest of the post was, as you pointed out, how it should be and I was including it to indicate why I was asking the questions I did.

Hi hawkmage,

Just to be clear, I never saw a isc-dhcp-server6 package.  I only installed the non-6 package and ended up with 6.

This is a new U 12.04 installation.

I'm not sure which repositories were standard and which I added so here's the entire list (from /etc/apt/sources.list):

```
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# eah 8Jun12 Uncommented next two lines
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

## eah 8Jun12  Added sources for webmin
deb http://download.webmin.com/download/repository sarge contrib deb http://webmin.mirror.somersettechsolutions.co.uk/repository sarge contrib


```

Would you like a list of all packages I've installed?  I'd be happy to provide that but don't know where to find it.

Hope you can identify something,

AB

---

### Post by hawkmage on 2012-07-02
I see one thing that is odd, there is the addition of a repository for Webmin where there are 2 lines that seam to me joined.  Each repository line should begin with "deb" or "deb-src".  Also these repositories are for the "sarge" release of debian which is quite old, release in mid 2005 but I don't know if Webmin has a package repositories for newer version of Debian.  

If you run the following commands what do you get returned:
```
dpkg --get-selections | grep dhcp
apt-cache search isc-dhcp
```

---

### Post by AlexBooton on 2012-07-02
> **hawkmage said:**
> I see one thing that is odd, there is the addition of a repository for Webmin where there are 2 lines that seam to me joined.  Each repository line should begin with "deb" or "deb-src".  Also these repositories are for the "sarge" release of debian which is quite old, release in mid 2005 but I don't know if Webmin has a package repositories for newer version of Debian.  

Yes, I see what you mean.  I think I can simply remove repository for Webmin since the package is already installed.  

> **hawkmage said:**
> If you run the following commands what do you get returned:
```
dpkg --get-selections | grep dhcp
apt-cache search isc-dhcp
```

Here you go:
```
root@mbh:~# dpkg --get-selections | grep dhcp
dhcp3-server                                    deinstall
isc-dhcp-client                                 install
isc-dhcp-common                                 install
isc-dhcp-server                                 install


root@mbh:~# apt-cache search isc-dhcp
isc-dhcp-client - ISC DHCP client
isc-dhcp-client-dbg - ISC DHCP client (debugging symbols)
isc-dhcp-common - common files used by all the isc-dhcp* packages
isc-dhcp-dev - API for accessing and modifying the DHCP server and client state
isc-dhcp-relay-dbg - DHCP relay daemon (debugging symbols)
isc-dhcp-server - ISC DHCP server for automatic IP address assignment
isc-dhcp-server-dbg - ISC DHCP server for automatic IP address assignment (debug)
isc-dhcp-relay - ISC DHCP relay daemon
isc-dhcp-server-ldap - DHCP server able to use LDAP as backend
tcos-configurator - PyGTK tool to configure some needed services to get a TCOS server

```

And thanks again!

AB

---

### Post by hawkmage on 2012-07-02
OK, the packages look OK.  

Are you willing to remove and reinstall DHCP?

If so first save your config file and remove the dhcp6.conf to dhcp.conf link then run:
```
sudo apt-get update
sudo apt-get purge isc-dhcp-server
sudo apt-get install isc-dhcp-server
```
Now put the config file back as dhcp.conf.

---

### Post by AlexBooton on 2012-07-02
> **hawkmage said:**
> OK, the packages look OK.  

Are you willing to remove and reinstall DHCP?

If so first save your config file and remove the dhcp6.conf to dhcp.conf link then run:
```
sudo apt-get update
sudo apt-get purge isc-dhcp-server
sudo apt-get install isc-dhcp-server
```
Now put the config file back as dhcp.conf.

Hi,

I've already done that multiple times. 

It wasn't until I stumbled on my workaround that it finally worked.

For the record, I've done purge and update b4 the re-install.  Never got any different result.

Thanks,

AB

---

### Post by hawkmage on 2012-07-02
That makes no sense.  I am out of ideas on this.

---

### Post by AlexBooton on 2012-07-03
> **hawkmage said:**
> That makes no sense.  I am out of ideas on this.

Thanks for hanging in and trying to help!

AB

---

