---
title: "Just updated to 9.10. No internet connection!"
date: 2009-11-13
forum: Ubuntu Christian Edition
---

### Post by wootcat on 2009-11-13
Please help.

I just updated Ubuntu CE to 9.10. Since then, I can't get any web pages to load. Firefox acts as if there is no internet connection. I am able to run the Install Application app just fine and download apps that way.

Please let me know what info I need to provide here to help me solve this.

Thanks!

---

### Post by lidex on 2009-11-13
This could be your problem:
[http://digitizor.com/2009/02/04/how-to-stop-firefox-linux-from-starting-in-offline-mode/]("http://digitizor.com/2009/02/04/how-to-stop-firefox-linux-from-starting-in-offline-mode/")

---

### Post by david_kt on 2009-11-13
> **wootcat said:**
> Please help.

I just updated Ubuntu CE to 9.10. Since then, I can't get any web pages to load. Firefox acts as if there is no internet connection. I am able to run the Install Application app just fine and download apps that way.

Please let me know what info I need to provide here to help me solve this.

Thanks!

It is probably due to dansguardian bugs. I have just uploaded ubuntu ce karmic repository last night, you could help to test it and hopefully solve your problem.

First step is to remove wine:

```

sudo apt-get remove wine
```

And then, if your system is 64 bit:

[HTML]sudo wget http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/karmic_amd.list -O /etc/apt/sources.list.d/ubuntuce.list; sudo apt-get update && sudo apt-get install ubuntu-ce[/HTML]

or if it is i386:

[HTML]sudo wget http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/jaunty_i386.list -O /etc/apt/sources.list.d/ubuntuce.list; sudo apt-get update && sudo apt-get install ubuntu-ce[/HTML]

DK

---

### Post by wootcat on 2009-11-14
> **lidex said:**
> This could be your problem:
[http://digitizor.com/2009/02/04/how-to-stop-firefox-linux-from-starting-in-offline-mode/]("http://digitizor.com/2009/02/04/how-to-stop-firefox-linux-from-starting-in-offline-mode/")

Some more information...

I tried the steps outlined in your link, lidex. The terminal responded with "unrecognized service"

The top right of my screen has, instead of a network connection icon, an icon that looks like a cell phone signal meter with "no bars". The dropdown from that shows Wired Network and underneath that "device not managed". 

In the Network tool I downloaded, when I tried to set up a Wired connection using dhcp, nothing happened there at all.

---

### Post by wootcat on 2009-11-14
> **david_kt said:**
> It is probably due to dansguardian bugs. I have just uploaded ubuntu ce karmic repository last night, you could help to test it and hopefully solve your problem.


I'll give that a try and report back, DK.

---

### Post by david_kt on 2009-11-14
> **wootcat said:**
> Some more information...

I tried the steps outlined in your link, lidex. The terminal responded with "unrecognized service"

The top right of my screen has, instead of a network connection icon, an icon that looks like a cell phone signal meter with "no bars". The dropdown from that shows Wired Network and underneath that "device not managed". 

In the Network tool I downloaded, when I tried to set up a Wired connection using dhcp, nothing happened there at all.

Open terminal and what is the output if this 2 commands:

ifconfig
cat /etc/network/interfaces

DK

---

### Post by wootcat on 2009-11-14
> **david_kt said:**
> Open terminal and what is the output if this 2 commands:

ifconfig
cat /etc/network/interfaces

DK

Unless there's an easy way to cut and paste between rebooting Ubuntu and XP, I won't be able to relate TOO much of that information, but I'll do what I can on my next reboot series ;-)

Okay, I tried what you asked and it appeared to work up until the end. I started to get a lot of "unable to resolve host address 'downloads.sourceforge.net' and 'kent.dl.sourceforge.net' messages.

Near the end, I got some of these messages...

Resolving cdnetworks-us-1.dl.sourceforge.net...
Failed: Connection Time Out
sha256sum.exe: andale32.exe: No such file or directory
andale32.exe: FAILED open or read
sha26sum: WARNING: 1 of 1 listed file could not be read
checksum mismatch for andale32.exe, aborting!

...then something about ttf-mscorefonts_installer and...

E: Sub-process /usr/bin/dpl?? returned an error code (1)

Now here's where it gets odd (from my standpoint): I got a message saying that the bugreport had already been filed, but I should check to see if I could add any information to the bug report. It then automatically launched Firefox and sent me to bugs.launchpad.net for bug #431217 -- and it worked! But only for the bug report. When I tried to load another web page, I got the same errors as before and my menu bar and dropdowns looked the same as I reported above.

---

### Post by david_kt on 2009-11-14
> **wootcat said:**
> It then automatically launched Firefox and sent me to bugs.launchpad.net for bug #431217 -- and it worked! But only for the bug report. When I tried to load another web page, I got the same errors as before and my menu bar and dropdowns looked the same as I reported above.

It seems you have internet connection working properly. Try this simple test:

Launch dansguardian-gui and stop dansguardian. 

After that try to browse internet.

DK

---

### Post by wootcat on 2009-11-14
Back again:

Results from ifconfig:

```

eth0 Link encap: Ethernet HWaddr 00:14:2a:0c:db:20
     inet addr: 192.168.1.78 Bcast: 192.168.1.255 Mask: 255...
     inet6 addr: fe80::214:2aff:fe0c:ab20/64 Scope: Link
     UP BROADCAST RUNNING MULTICAST MTU: 1500 Metric: 1
     Rx packets:23 errors:0 dropped:0 overruns:0 frame:0
     TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:1000
     Rx bytes:5004 (5.0KB) TX bytes:6135 (6.1KB)
     Interrupt:23 Base address: 0x2000

lo   More info, mostly zeroed data
```

Results from the cat command:

```

auto lo
iface lo inet loopback

iface eth0 inet dhcp
auto eth0
```

Rebooting to try the start/stop of dansguardian...

---

### Post by david_kt on 2009-11-14
> **wootcat said:**
> Back again:

Results from ifconfig:

```

eth0 Link encap: Ethernet HWaddr 00:14:2a:0c:db:20
     inet addr: 192.168.1.78 Bcast: 192.168.1.255 Mask: 255...
     inet6 addr: fe80::214:2aff:fe0c:ab20/64 Scope: Link
     UP BROADCAST RUNNING MULTICAST MTU: 1500 Metric: 1
     Rx packets:23 errors:0 dropped:0 overruns:0 frame:0
     TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:1000
     Rx bytes:5004 (5.0KB) TX bytes:6135 (6.1KB)
     Interrupt:23 Base address: 0x2000

lo   More info, mostly zeroed data
```

Results from the cat command:

```

auto lo
iface lo inet loopback

iface eth0 inet dhcp
auto eth0
```

Rebooting to try the start/stop of dansguardian...

I am not sure who edit the /etc/network/interfaces. But to utilize Network Manager, you must remove eth0 from there.:

```
echo auto lo | sudo tee > /etc/network/interfaces
echo iface lo inet loopback | sudo tee >> /etc/network/interfaces
sudo /etc/init.d/networking restart
sudo /etc/init.d/network-manager restart # might not necessary

```

DK

---

### Post by wootcat on 2009-11-14
Woot! Posting from inside UbuntuCE this time!

Starting and stopping Dansguardian appears to have done it, although I had my doubts as it didn't appear that Dansguardian actually started. I got these messages when I tried to start it:

```
mkdir: cannot create directory `/home/rod/.cache': File exists
grep: /usr/lib/firefox-3.5.5/firefox.cfg: No such file or directory
Starting tinyproxy: tinyproxy.
 * Starting Firewall firehol                                                    

WARNING
File '/etc/firehol/RESERVED_IPS' is more than 90 days old.
You should update it to ensure proper operation of your firewall.

Run the supplied get-iana script to generate this file.

                                                                         [ OK ]
        DansGuardian has not been configured!
        Please edit /etc/dansguardian/dansguardian.conf manually then rerun
        this script.
grep: /usr/lib/firefox-3.5.5/firefox.cfg: No such file or directory
```

and then when I stopped it:

```
        DansGuardian has not been configured!
        Please edit /etc/dansguardian/dansguardian.conf manually then rerun
        this script.
 * Stopping Firewall firehol                                                    

WARNING
File '/etc/firehol/RESERVED_IPS' is more than 90 days old.
You should update it to ensure proper operation of your firewall.

Run the supplied get-iana script to generate this file.

                                                                         [ OK ]
Stopping tinyproxy: tinyproxy.
grep: /usr/lib/firefox-3.5.5/firefox.cfg: No such file or directory
```

So I wasn't sure if it actually ran or not. 

Thanks! I'm much happier now than I was a couple hours ago!

Now, can I restart Dansguardian? That was the main reason I choose UbuntuCE, so I will be sad if I can't run it again.

Again, thanks for your incredibly quick responses and assistance!

---

### Post by wootcat on 2009-11-14
When I tried this command:

**echo auto lo | sudo tee > /etc/network/interfaces**

I got bash: /etc/network/interfaces: Permission denied

---

### Post by david_kt on 2009-11-14
> **wootcat said:**
> Woot! Posting from inside UbuntuCE this time!

Starting and stopping Dansguardian appears to have done it, although I had my doubts as it didn't appear that Dansguardian actually started. I got these messages when I tried to start it:

```
mkdir: cannot create directory `/home/rod/.cache': File exists
grep: /usr/lib/firefox-3.5.5/firefox.cfg: No such file or directory
Starting tinyproxy: tinyproxy.
 * Starting Firewall firehol                                                    

WARNING
File '/etc/firehol/RESERVED_IPS' is more than 90 days old.
You should update it to ensure proper operation of your firewall.

Run the supplied get-iana script to generate this file.

                                                                         [ OK ]
        DansGuardian has not been configured!
        Please edit /etc/dansguardian/dansguardian.conf manually then rerun
        this script.
grep: /usr/lib/firefox-3.5.5/firefox.cfg: No such file or directory
```

and then when I stopped it:

```
        DansGuardian has not been configured!
        Please edit /etc/dansguardian/dansguardian.conf manually then rerun
        this script.
 * Stopping Firewall firehol                                                    

WARNING
File '/etc/firehol/RESERVED_IPS' is more than 90 days old.
You should update it to ensure proper operation of your firewall.

Run the supplied get-iana script to generate this file.

                                                                         [ OK ]
Stopping tinyproxy: tinyproxy.
grep: /usr/lib/firefox-3.5.5/firefox.cfg: No such file or directory
```

So I wasn't sure if it actually ran or not. 

Thanks! I'm much happier now than I was a couple hours ago!

Now, can I restart Dansguardian? That was the main reason I choose UbuntuCE, so I will be sad if I can't run it again.

Again, thanks for your incredibly quick responses and assistance!

Yes you can, but follow my previous suggestion to upgrade ubuntu-ce to karmic version first. After that, remove firehol:

```
sudo apt-get remove --purge firehol
```

Launch dansguardian-gui and choose autoconfigure/reset danguardian. Danguardian should on automatically.

DK

---

### Post by david_kt on 2009-11-14
> **wootcat said:**
> When I tried this command:

**echo auto lo | sudo tee > /etc/network/interfaces**

I got bash: /etc/network/interfaces: Permission denied

Sorry my mistake.

```
sudo su
echo auto lo > /etc/network/interfaces
echo iface lo inet loopback >> /etc/network/interfaces
/etc/init.d/networking restart
/etc/init.d/network-manager restart # might not necessary
```

DK

---

### Post by wootcat on 2009-11-14
Is there anything I should do differently this time to avoid getting the errors and timeouts? Or should that be better now that I've started/stopped Dansguardian?

---

### Post by david_kt on 2009-11-14
> **wootcat said:**
> Is there anything I should do differently this time to avoid getting the errors and timeouts? Or should that be better now that I've started/stopped Dansguardian?

Once you have updated to ubuntu-ce karmic, there should not be any issue actually, follow my previous post.

DK

---

### Post by wootcat on 2009-11-14
Cool. Thanks. I think I made most of the changes.

Going to bed now, but had to turn off DG for now...I could load the UbuntuCE site, but the forums wouldn't load...just a blank screen. 

Will play with settings tomorrow, I guess.

Thanks again for the quick help!

Take care and God bless!

---

### Post by david_kt on 2009-11-14
> **wootcat said:**
> Cool. Thanks. I think I made most of the changes.

Going to bed now, but had to turn off DG for now...I could load the UbuntuCE site, but the forums wouldn't load...just a blank screen. 

Will play with settings tomorrow, I guess.

Thanks again for the quick help!

Take care and God bless!

If the forums still blank, that means danguardian is still using the one having bugs, you need to upgrade:

```
sudo apt-get upgrade
```

DK

---

### Post by Viva on 2009-11-14
This is a bug with the network manager in karmic. Are you using DSL?

---

### Post by wootcat on 2009-11-14
> **Viva said:**
> This is a bug with the network manager in karmic. Are you using DSL?

Yes, I have DSL.

I tried updating DG, but I still cannot load forum pages when DG is running. I have to disable it.

Also, I'm seeing several other issues which I'm not sure if I should post here or start new threads.

1. I cannot log out of my account. Everything disappears from my desktop, but the desktop image remains and it just hangs there. I have to reboot.

2. I cannot switch users either. I get returned to the login screen where it's set to my account, asking for password. I can't click on any buttons, but I can Tab to Switch User, but doing that just brings be back to this same screen, so I can only log into my account again. When I reboot, I can log into another account -- and from that account (non-admin), I can switch accounts, but I can't from my (admin) account

---

### Post by Viva on 2009-11-14
I think you better create seperate threads in the main categories for non-CE related problems.

---

### Post by david_kt on 2009-11-14
> **wootcat said:**
> Yes, I have DSL.

I tried updating DG, but I still cannot load forum pages when DG is running. I have to disable it.


What is the out put of:

```
 dansguardian --version
```

DK

---

### Post by wootcat on 2009-11-14
> **david_kt said:**
> What is the out put of:

```
 dansguardian --version
```

DK

DansGuardian 2.10.1.1

Built with:  '--mandir=/usr/share/man/' '--enable-clamav=yes' '--enable-clamd=yes' '--with-proxyuser=dansguardian' '--with-proxygroup=dansguardian' '--prefix=/usr' '--mandir=${prefix}/share/man' '--infodir=${prefix}/share/info' '--sysconfdir=/etc' '--localstatedir=/var' '--enable-icap=yes' '--enable-commandline=yes' '--enable-trickledm=yes' '--enable-email=yes' '--enable-ntlm=yes' 'CXX=g++' 'CXXFLAGS=-g -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions' 'CPPFLAGS=' 'CC=cc' 'CFLAGS=-g -O2'

---

### Post by david_kt on 2009-11-15
> **wootcat said:**
> DansGuardian 2.10.1.1

That is the problem.

Follow my previous post:

```
sudo apt-get remove wine
sudo wget http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/karmic_amd.list -O /etc/apt/sources.list.d/ubuntuce.list; sudo apt-get update && sudo apt-get install ubuntu-ce
sudo apt-get remove --purge firehol
```

Afer that launch dansguardian gui and choose autoconfigure/reset dansguardian.

DK

---

### Post by wootcat on 2009-11-15
> **david_kt said:**
> That is the problem.

Follow my previous post:

```
sudo apt-get remove wine
sudo wget http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/karmic_amd.list -O /etc/apt/sources.list.d/ubuntuce.list; sudo apt-get update && sudo apt-get install ubuntu-ce
sudo apt-get remove --purge firehol
```

Afer that launch dansguardian gui and choose autoconfigure/reset dansguardian.

DK

I've tried that twice now. I guess the update failed both times. Maybe it had something to do with the mscorefont error I described earlier.

I'll try it again tomorrow. Thanks for the help!

---

### Post by wootcat on 2009-11-15
david_kt,

I re-did those instructions. Got what looked like the same error messages as before, and again, when DG is running, forum pages aren't loading.

I saved out the terminal text if you want me to send that to you.

---

### Post by david_kt on 2009-11-15
> **wootcat said:**
> david_kt,

I re-did those instructions. Got what looked like the same error messages as before, and again, when DG is running, forum pages aren't loading.

I saved out the terminal text if you want me to send that to you.

Yes, please let me see the output. In the mean time, try to download and install manually.

If you system is 64 bit, download and install below:

[http://ubuntuce.com/repos/Ubuntu_CE/karmic_amd/dansguardian_2.11.9.7-2ubuntu1_amd64.deb](http://ubuntuce.com/repos/Ubuntu_CE/karmic_amd/dansguardian_2.11.9.7-2ubuntu1_amd64.deb)

If it is 32 bit, download and install below:

[http://ubuntuce.com/repos/Ubuntu_CE/karmic_i386/dansguardian_2.11.9.7-2ubuntu1_i386.deb](http://ubuntuce.com/repos/Ubuntu_CE/karmic_i386/dansguardian_2.11.9.7-2ubuntu1_i386.deb)

After that, upgrade dansguardian-gui as well manually:

[http://ubuntuce.com/repos/Ubuntu_CE/karmic_i386/dansguardian-gui_2.3_all.deb](http://ubuntuce.com/repos/Ubuntu_CE/karmic_i386/dansguardian-gui_2.3_all.deb)

And do autoreconfigure/reset from dansguardian-gui.

DK

---

### Post by wootcat on 2009-11-16
Couple problems...the text is too long to paste and I can't attach files to mail here. Also, I can't find the app needed to install the files.

Figured out the install part...installing now.

---

### Post by wootcat on 2009-11-16
Manual install and update appeared to work. Woot!

---

### Post by provomike on 2010-02-20
I just upgraded from 9.04 to 9.10 and now I have no network connection. I do not have dansguardian installed. My /etc/network/interface is:

auto lo
iface lo inet loopback

iface etho inet dhcp
    address 192.168.0.197
    netmask 255.255.255.0
    gateway 192.168.0.1
    up ip route add 192.168.0.186/24 dev eth0
auto etho

---------------------------------------------------------------
I use this system for doing remote work and am dead in the water. How do I restore networking on this new release!!

Thanks

---

### Post by david_kt on 2010-02-20
> **provomike said:**
> I just upgraded from 9.04 to 9.10 and now I have no network connection. I do not have dansguardian installed. My /etc/network/interface is:

auto lo
iface lo inet loopback

iface etho inet dhcp
    address 192.168.0.197
    netmask 255.255.255.0
    gateway 192.168.0.1
    up ip route add 192.168.0.186/24 dev eth0
auto etho

---------------------------------------------------------------
I use this system for doing remote work and am dead in the water. How do I restore networking on this new release!!

Thanks

Try removing below

```
iface etho inet dhcp
    address 192.168.0.197
    netmask 255.255.255.0
    gateway 192.168.0.1
    up ip route add 192.168.0.186/24 dev eth0
auto etho
```

and restart your computer.

DK

---

