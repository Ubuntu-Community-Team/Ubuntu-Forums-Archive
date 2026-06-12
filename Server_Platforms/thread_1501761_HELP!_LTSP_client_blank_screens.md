---
title: "HELP! LTSP client blank screens"
date: 2010-06-04
forum: Server Platforms
---

### Post by v4169sgr on 2010-06-04
I am at my wit's end over this one ... A clean ltsp-server-standalone install on Lucid results in blank screens in my thin clients at initialisation.

1. After installation of the base package, I ran ltsp-build-client which completed successfully.

2. I then edited /etc/ltsp/dhcp.conf which now looks like this, and restarted the dhcp server:

```
#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 10.0.0.0 netmask 255.255.255.0 {
    range 10.0.0.20 10.0.0.250;
    option domain-name "example.com";
    option domain-name-servers 10.0.0.138;
    option broadcast-address 10.0.0.255;
    option routers 10.0.0.138;
#    next-server 192.168.0.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}

```

where 10.0.0.138 is my modem / router, and 10.0.0.1 is my workstation / ltsp server.

My thin clients are old Dell GX110 Optiplex machines [PIIIs] with no HDD and an Intel PXE boot ethernet card installed.

All worked well with 8.04 which I have run happily for 2 years, but following my clean install of 10.04 over the top on the workstation, nothing ltsp-wise is working.

I ran

```
sudo dpkg-reconfigure nbd-server
```

with parameters 1, /opt/ltsp/i386 and 2000 just in case there was a problem with the default nbd config not being present.

My clients run fine all the way past DHCP & downloading the kernel, but fail on boot, resulting in a blank screen.

I replaced "quiet splash" with "nomodeset" in /var/lib/tftpboot/ltsp/i386/pxelinux.cfg/default so I could observe where the clients were failing. Here is an approximation of the last few lines on the screen:

```
Begin: mounting root file system
Begin: running /scripts/nfs-top
Done
Hangup
[   6.663989] nbd.; Negotiation size=4kb
bs=1024, sz=4
```

then nothing. This is approximate as I copied this down manually ...

My /var/log/syslog from the time looks like this:

```
Jun  4 21:28:53 aammscott nbd_server[1429]: connect from 10.0.0.20, assigned file is /opt/ltsp/i386
Jun  4 21:28:53 aammscott nbd_server[1429]: Can't open authorization file (null) (Bad address).
Jun  4 21:28:53 aammscott nbd_server[1429]: Authorized client
Jun  4 21:28:53 aammscott nbd_server[26697]: Starting to serve
Jun  4 21:28:53 aammscott nbd_server[26697]: Size of exported file/device is 4096
```

**Please help!** My family are due back tomorrow evening and will be very upset that their thin clients are not working!!!:frown:

Thanks!!!

---

### Post by v4169sgr on 2010-06-05
*bump* with thanks for any helpful suggestions ...

---

### Post by v4169sgr on 2010-06-05
Could it be something to do with video drivers / ldm ???

---

### Post by v4169sgr on 2010-06-05
I have logged in on the 'old' Hardy 8.04 system which is a known good, and copied / compared the lts.conf, pxelinux/default and /etc/ltsp/dhcpd.conf files.

1. There is no default lts.conf set up in my copy of 8.04, so I've made sure there are none in the path on 10.04;

2. The pxelinux/default files are not ***substantially*** different:

8.04:

```
DEFAULT vmlinuz ro initrd=initrd.img quiet splash
```

10.04:

```
default ltsp


label ltsp
kernel vmlinuz
append ro initrd=initrd.img nomodeset nbdport=2000



```

To be sure, I had a go with replacing the 10.04 file with the 8.04 file and giving it a whirl. It had an effect [i.e. the quiet option was back again] but still did not solve the problem - the client blank screens before obtaining the logon screen.

3. The dhcpd.conf files were not substantially different either; just to be sure, I've made mine look like the one I have on 8.04 [and restarted the dhcp server]:


```
#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 10.0.0.0 netmask 255.255.255.0 {
    range 10.0.0.20 10.0.0.250;
    option domain-name "example.com";
    option domain-name-servers 10.0.0.1;
    option broadcast-address 10.10.0.255;
    option routers 10.0.0.1;
#    next-server 192.168.0.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}
```



I am out of ideas at this point. I have the 'old' HDD with 8.04 on it for which ltsp still works, but that is hardly the point, is it?

It looks to me like a **potential regression** as:
* I have not changed the physical layout / set up;
* I have made sure the configs are the same.

Comments welcome please, I still have to solve this problem.

---

### Post by v4169sgr on 2010-06-05
Just on the offchance that this is something more to do with nbd, here is the contents of /etc/nbd-server/config:

```
[generic]
# If you want to run everything as root rather than the nbd user, you
# may either say "root" in the two following lines, or remove them
# altogether. Do not remove the [generic] section, however.
	user = nbd
	group = nbd

# What follows are export definitions. You may create as much of them as
# you want, but the section header has to be unique.
[export]
	exportname = /opt/ltsp/i386
	port = 2000

```

which was generated by ```
dpkg-reconfigure nbd-server
``` as there was initially no config file with 10.04.

Restarting using ```
sudo /etc/init.d/nbd-server restart
``` gives

```
Restarting the Network Block Device server is pretty harsh on clients still using it.
waiting 5 seconds...You have been warned!
Restarting Network Block Device server: Stopping Network Block Device server: nbd-server.
 nbd-server.
```

**but I see a segfault in the /var/log/syslog!!!**

```
Jun  5 12:17:10 aammscott kernel: [ 2305.224851] nbd-server[2594]: segfault at 0 ip 08049eb1 sp bfdc6740 error 4 in nbd-server[8048000+7000]
Jun  5 12:17:10 aammscott kernel: [ 2305.224985] nbd-server[2330]: segfault at 0 ip 08049eb1 sp bfdc6740 error 4 in nbd-server[8048000+7000]

```

Smoking gun?

---

### Post by v4169sgr on 2010-06-05
Apparently this could be a red herring:

[https://bugs.launchpad.net/ubuntu/+source/nbd/+bug/134572](https://bugs.launchpad.net/ubuntu/+source/nbd/+bug/134572)

as the nbd server is still running:

```
ps aux | grep nbd
nbd       2814  0.0  0.0   2988   696 ?        Ss   12:17   0:00 /bin/nbd-server

```

Here is the version I am running:

```
dpkg -l | grep nbd
ii  nbd-server                            1:2.9.14-2ubuntu1                               Network Block Device protocol - server

```

standard in 10.04.

---

### Post by v4169sgr on 2010-06-05
Interesting that the segfault error only appears when nbd-server is run as user nbd, not when it is run as root.

I've also made certain bind / port already in use errors go away by changing the port to 1043. None of this has helped though :(

I cannot shake the suspicion that there is something do do with video modes ....

---

### Post by v4169sgr on 2010-06-05
Cannot even spawn a shell with ```
SCREEN_02 = shell
```:confused:

---

### Post by v4169sgr on 2010-06-05
The central fact is that 8.04 LTSP thin clients boot, while those in 10.04 with apparently identical configurations [network & boot parameters] do not. To date, I have not come up with a convincing explanation.

Suggestions are most welcome. Please recommend this thread to knowledgeable people you may know. If not solved in a timely fashion this may unfortunately be a deal-breaker for me ...

---

### Post by uOpt on 2010-06-05
Hmm, I still didn't get whether you upgraded the clients, the server, or both.

---

### Post by v4169sgr on 2010-06-05
Thanks for the reply :)

The clients are diskless, so the entire system was replaced from 8.04 to 10.04. The physical system & networking are still the same, but the software has been completely replaced.

---

### Post by uOpt on 2010-06-05
> **v4169sgr said:**
> Thanks for the reply :)

The clients are diskless, so the entire system was replaced from 8.04 to 10.04. The physical system & networking are still the same, but the software has been completely replaced.

Well, I guess you are in for narrowing it down via downgraded one or other :)

This might be related to other PXE boot problems I have seen pop up with 10.04 but I haven't seen anybody go back and proof a regression.

---

### Post by Goodheart on 2010-06-06
I don't know if it is still valid in 10.04, but in 8.04 it was necessairy to regenerate the ssh-keys after changing the ip-address on the server. You would have to look-up the command.

Also, is having the 10.0.0.138 in the dhcp address range a probable cause of conflict?

---

### Post by v4169sgr on 2010-06-06
Hello Goodheart and thanks for the reply ;-)

1. I did try regerating the ssh keys but to no avail.

2. I do agree that having 10.0.0.138 in the DHCP range is odd, however I had the exact same set in 8.04 which worked perfectly. I will change to 20 - 90 instead and see if that makes a difference [not that I am expecting it to, to be honest].

---

### Post by v4169sgr on 2010-06-06
As expected, changing the DHCP range [and restarting the service] did not produce any change in behaviour ...

---

### Post by bobwdn on 2010-06-06
Just an observation. 

The dhcpd.conf file posted within the post #4 is not the same as that posted in post #1.

post #1 ```
option domain-name-servers 10.0.0.138;

```

post #4 ```
option domain-name-servers 10.0.0.1;

```

Are you 100% sure you copied configurations file the same between versions? One letter or number miss-typed or missing could be an issue.

---

### Post by v4169sgr on 2010-06-06
Hi Bobwdn - thanks for the sharp eyes ;-) You are of course correct BUT this is not the cause of the problem. The DNS option was 10.0.0.1 in the original config which HAS been copied correctly in the new config, and there is no difference in behaviour between these two values. :(

---

### Post by v4169sgr on 2010-06-06
I have burned a CD image of my alternate install ISO for 10.04 and used that to boot up one of the clients in rescue mode, and (re)discovered that there are TWO network interfaces on the machine, eth0 and eth1, only one of which [eth0] is active. That is of course the PXE card which is used to grab the image.

What would happen if on boot the WRONG interface was selected? Would that cause the blank screen?

Is there any way in which to force the boot up sequence on the client to always select eth0?

---

### Post by Goodheart on 2010-06-07
It should be possible to disable one of the networkcards in the BIOS. If the system starts up and displays the Dell logo, there will be at least two function keys mentioned on the bottom line. One for the boot menu and one for entering Setup.

---

### Post by uOpt on 2010-06-07
Until this weekend, I actually had to disable one interface in my kernel config for one dual-ethernet diskless machine.

Debian was too dumb to continue using the right one and the dumb motherboard wouldn't let me use Debian's preference as the lone ethernet chip.

mainboard -> trashcash

---

### Post by v4169sgr on 2010-06-07
Thanks a lot for your replies :)

Unfortunately the BIOS in the Dell Optiplex GX 110 I am using as a test client is not that helpful; there does not appear to be an option to selectively disable LAN cards.

Testing has shown that, when the client displays a blank screen, it is alive and responds to pings, which unfortunately makes it likely that my guess is wide of the mark.

---

### Post by uOpt on 2010-06-07
> **v4169sgr said:**
> Thanks a lot for your replies :)

Unfortunately the BIOS in the Dell Optiplex GX 110 I am using as a test client is not that helpful; there does not appear to be an option to selectively disable LAN cards.

Testing has shown that, when the client displays a blank screen, it is alive and responds to pings, which unfortunately makes it likely that my guess is wide of the mark.

I did it by just not compiling the driver into the kernel (I don't use initrds). So the /etc/rc.d scripts don't have a choice to grab the wrong Ethernet chip. Of course this requires that you have different chips for the two interfaces.

Did you make the test of downgrading clients and servers separately?

---

### Post by v4169sgr on 2010-06-08
Thanks a lot for your reply.

* I do not think that networking is the issue as the client is pingable.

* I do not have the patience to properly test different versions of the image and the host environment, however I have attempted to boot the client as standalone with a 10.04 live CD - *BOOM* no screen. Actually goes into 'power saving mode' - same as when PXE booting 10.04. 8.04 host and image is fine ...

I believe that means I am SOL on 10.04.

What do people make of something like HP T5125 thin clients? How are they supposed to work with 10.04 LTSP?

---

### Post by uOpt on 2010-06-09
> **v4169sgr said:**
> Thanks a lot for your reply.

* I do not think that networking is the issue as the client is pingable.

* I do not have the patience to properly test different versions of the image and the host environment, however I have attempted to boot the client as standalone with a 10.04 live CD - *BOOM* no screen. Actually goes into 'power saving mode' - same as when PXE booting 10.04. 8.04 host and image is fine ...

I believe that means I am SOL on 10.04.

What do people make of something like HP T5125 thin clients? How are they supposed to work with 10.04 LTSP?

Pretty obviously but not certainly they fatfingered something in the diskless boot in 10.04, but we don't know whether it's client or server. I doubt diskless boot is part of their QA so there. Since they drove away people like me from Ubuntu it is up to the ones like you to debug it. It's sad that you decided not to try to narrow it down.

---

### Post by v4169sgr on 2010-06-09
Actually I believe this is less to do with LTSP images in particular and more to do with 10.04 in general not laying nice with some graphics related chipset that I happen to have in my dinosaur PIIIs ...

Really and honestly, there is so much else that is right and good about 10.04 and about the long term support model in general that I am certainly not about to jump ship - just wish I could find some opinions on these HP T5125 thin clients I hear about ...

I've been with Linux since 1991 and Ubuntu is as good as it gets for a general purpose low admin 'just works' desktop distro ...

---

### Post by Aearenda on 2010-06-09
I have 8 Dell GX110s in use as terminals with a 10.04 server that was built from scratch, and they work fine for me, as they did with 8.04 before. The GX110s have Intel 82810E DC-133 rev 3 graphics hardware. I use an lts.conf file as follows:
```
[Default]
# Use LDM - this is a hangover from earlier versions, probably not needed any more
SCREEN_07=ldm

# Colour depth for GX110s
X_COLOR_DEPTH=24

# Slow terminals
NETWORK_COMPRESSION=FALSE
LDM_DIRECTX=TRUE

```

I had one machine (now no longer used) that would not detect the screen resolution correctly, and for that one I had this extra piece in the lts.conf file:
```
#[00:b0:d0:d3:78:61]
# This GX110 doesn't detect screen properly
X_HORZSYNC=30-81
X_VERTREFRESH=56-76
X_MODE_0=1280x1024

```

I wonder whether your GX110s are different from ours in some way - mine are thin flat ones that sit under the monitor, not tower-style like the one shown on Dell's website. I'm pretty sure ours use old BIOS versions.

EDIT: Our GX110s have PXE enabled on the single ethernet interface on the motherboard. You have to enable this in the BIOS, first by allowing the net interface to use PXE (I think they call it MBA or something like that), then rebooting and going back into the BIOS, and setting the network as first choice in the boot order.

---

### Post by v4169sgr on 2010-06-10
Thanks Aearenda!

Your reply motivated me to have another crack at getting these GX110s to play nice with 10.04. No dice, unfortunately, not even with the screen detection settings [modded for my small displays].

I have the towers [as in the DELL website piccys] into which I have fitted Intel PXE boot cards. They work absolutely fine with 8.04 and always have done without quibble.

---

### Post by Aearenda on 2010-06-10
So your GX110s have no built-in PXE capability? The BIOS on mine calls it something else, but it works, and without the second NIC, there's no confusion. Here's an idea: wire up BOTH NICs to the same network, and see what happens...

PS: Do yours have the same graphics hardware (82810E)?

---

### Post by dalessio on 2010-06-21
I had the same problem.

Changed my /var/lib/tftpboot/ltsp/i386/pxelinux.cfg/default file to have the line 

append ro initrd=initrd.img quiet splash nbdport=2000 acpi=off noacpi noapic nomodeset


and it boots as it did before the upgrade. I also have to add those lines to the live cd boot to be able to install on older machines.

---

### Post by dalessio on 2010-06-23
I should add... 

With the above modification I could not set the graphics card to nvidia or set a default resolution. Upon doing that I boot to a blank screen.

The only successful configuration I can find is a blank lts.conf and the above lines appended to boot.

I'm not an expert but it appears to me that there is a bug in 10.04 with old machines without acpi/acip (always forget which is which). This is tragic for ltsp users because most of our thin clients are archaic. 

The same machine boots with 0 problems with 9.10 and 8.04 with most configurations I throw at it.

---

### Post by dannyfel on 2010-06-24
Any news about this problem?
My thin clients loaded perfectly on 9.10, now get the same splash screen  of Ubuntu with the dots, pressing ESC bringing me to the same screen  (bs=1024, sz=4)
Same also after changing the pxelinux.cfg/default like suggested

when removing quiet splash I'm getting:

[ numbers ] nbd0: hangup
Negotiation: ..size = 4kb
bs=1024, sz=4

and that's it.

---

### Post by dannyfel on 2010-06-24
on slower clients the [ ] nbd0: appears in the end of the output, so  Hangup appears before...
But I have a feeling it's the nbd-server again, as before I was coping  with a problem of: Error: failed to connect to NBD server

---

### Post by crmanski on 2010-08-20
> **dannyfel said:**
> Any news about this problem?
My thin clients loaded perfectly on 9.10, now get the same splash screen  of Ubuntu with the dots, pressing ESC bringing me to the same screen  (bs=1024, sz=4)
Same also after changing the pxelinux.cfg/default like suggested

when removing quiet splash I'm getting:

[ numbers ] nbd0: hangup
Negotiation: ..size = 4kb
bs=1024, sz=4

and that's it.

I'm having the same issues after resolving the ndb server and tftp issues. It seems like the image is to large to load over the network.

---

### Post by mynard on 2010-09-02
Hi There

I'm not sure if you found some more help on this yet but here is my findings on this issue.

with NBD the system exports an image, so this made me think that there might be a reason for having to rebuild your client image every time that something changes. so all I done was to change my export in the /etc/nbd-server/config to the following

[export]
    exportname = /opt/ltsp/images/i386.img


and this solved it for me ..


~M~

---

