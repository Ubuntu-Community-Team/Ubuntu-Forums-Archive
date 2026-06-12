---
title: "HOWTO dialin PPP server, RAS server"
date: 2006-03-25
forum: Tutorials
---

### Post by al108 on 2006-03-25
First I wanted to say this is not another how to setup your dialup connection to the ISP.:mrgreen: 
This doesn't pretend to be a complete howto but I've seen quiet a few posts on this topic in Ubuntu forums unanswered, and it took me a long time to figure it out myself. I'm not an expert on this but it worked for me and hopefully will work for you or at least will get you started. For those who interested in setting up a callback server this is the first step, you will have to edit some more config files, but you will have to do this first. Links to more info and credits are at the end.

**_Part I _**. The short version:D  on how to get remote access to your Ubuntu box via modem. Install mgetty
```
sudo apt-get install mgetty
```
Add a line at the end of file */etc/inittab*
```
S0:2345:respawn:/sbin/mgetty ttyS0
```
If your modem is on COM1. 
Initialize init by typing
```
sudo init q
```
Now from Win you can use HyperTerminal to connect to your Ubuntu box with your user name/pass.

For those who want more here is a real deal;) 
[U]
**Part II **[/U]

**The problem:** Establish PPP connection to Ubuntu server from a remote location using a modem and to share internet connection.
Laptop modem<> Server modem <> Ethernet Router <> Cable/DSL modem <> Internet

**Assumptions:** drivers for your modems already installed and modem is at ttyS0. I have an external modem attached to COM1 - ttyS0, COM2 will be ttyS1. I didn't have X installed so I was using nano to edit conf files, you can use gedit if you have X installed or any other editor. Make sure your are familiar with the interface of the editor before you start modifying files. Make sure you create backups of the files before you modify them. You will need to use sudo or login as root for most of the tasks. If you don't know how to configure your dial up on your client look for a dial up howto or Ubuntu docs. I also assume that you already have your local nework including routers properly configured and have an access to the Internet from your Ubuntu server. 

_**Part II.a - Dial in configuration**_

1. If not already installed use synaptic or apt-get to install ppp and mgetty packages. ppp should be already installed by default so
```
sudo apt-get install mgetty
```

2. Create a group ppp by adding a line in file */etc/group* ```
ppp:x:1001:
```

3. Create a new user "pppuser" or whatever you will use for your dial in connection and assign a password by using
```
sudo adduser pppuser
```
edit file */etc/passwd* or use ```
sudo vipw
``` to change entry for pppuser to ```
pppuser:x:1001:1001:,,,:/home/pppuser:/usr/sbin/ppplogin
```

4. Add a line to the file */etc/inittab* ```
S0:2345:respawn:/sbin/mgetty ttyS0
``` for modem on ttyS0. Or ```
S1:2345:respawn:/sbin/mgetty ttyS1
``` for modem on ttyS1 That will let mgetty to accept incoming calls

5.Make a new file */usr/sbin/ppplogin* and add the following in there 
```
#!/bin/sh
#/etc/ppp/ppplogin
# PPP login script
mesg n
stty -echo
exec /usr/sbin/pppd -detach modem debug crtscts

```

6. Set access to the *ppplogin* file and *etc/ppp* directory
```
chmod 750 /usr/sbin/ppplogin
chown root:ppp /usr/sbin/ppplogin
chmod 775 /etc/ppp
chown root:root -R /etc/ppp
```

7. Restart init by typing ```
init q
```
If you're use external modem it should be on before that.

8. Open file */etc/mgetty/login.config* Comment out everything in there and add a line 
```
/AutoPPP/ - a_ppp /usr/sbin/pppd file /etc/ppp/options
```

9. Open file */etc/ppp/options* and make sure these lines are uncommented. If anything else is uncommented it probably should be commented.
```

        -detach
	 asyncmap 0
	 modem
	 crtscts
	 proxyarp
	 lock
	 require-pap
	 refuse-chap
	 ms-dns 192.168.1.1 #put your dns server ip here
	 usepeerdns
```
In my case the *ms-dns* entry had an ip of my router, if you using Linksys router it's 192.168.1.1 by default unless you changed it.

10. Create a file */etc/ppp/options.ttyS0* for the modem on ttyS0 and add following in there
```
192.168.1.3:192.168.1.201
     noauth
```
Where first address is the address of your server for ppp connection which I think, should be different from your eth ip. The second address is the address that will be assigned to the client when connection is established. It will probably make life easier, unless you know what you doing, if all those addresses on the same subnet   as your other computers on the network. (ip starts with the same 192.168.1.x numbers)
You can substitute ```
noauth
``` for a ```
debug
``` line, this way it will log some info about you connection in a syslog.

11. Edit file */etc/ppp/pap-secrets*
find a line after ```
# Every regular user can use PPP and has to use passwords from /etc/passwd
```
It should look something like that
```
*         hostname     ""      *
```
substitute hostnatname with * so it looks like that
```
*         *     ""      *

```
If you don't do that pap will not authenticate you and you'll be immediately disconnected.

Now you're able to connect using dial-up connection from you laptop or a remote office into your Ubuntu server and use ssh or putty if you're using Win.

**_Part II.b - Accessing internet from a remote client_**

I'm sure there other or better solutions to that, but that was easy enough and it worked for me.
```

sudo apt-get install ipmasq
```

Done. ipmasq automatically senses all your interfaces and initializes IP Masquerade forwarding/firewalling and allows you to connect to the rest of your network and the Internet.

I didn't have to do any more configurations for that.

Credits: Part I was inspired by debenham [http://www.ubuntuforums.org/member.php?u=21302](http://www.ubuntuforums.org/member.php?u=21302) in his answer to benson in [http://www.ubuntuforums.org/showthread.php?t=65012](http://www.ubuntuforums.org/showthread.php?t=65012)

Part II and for more information
[http://linuxgazette.net/issue77/sunil.html](http://linuxgazette.net/issue77/sunil.html)  - Setting Up a Linux-based PPP Callback server
and [http://tvilda.stilius.net/callback_en.php](http://tvilda.stilius.net/callback_en.php)  - Debian PPP dialin and callback server
[http://www.aboutdebian.com/](http://www.aboutdebian.com/)   - Some info on networking and other topics
[http://www.debian.org/](http://www.debian.org/)
[http://qref.sourceforge.net/](http://qref.sourceforge.net/)    - Debian reference
Those of you who are interested in setting up a callback server need to read links above. If security is a concern or you're in a business environment you should probably have a different setup.

Good luck
Alex

---

### Post by tommyj27 on 2007-01-27
Thanks for the HOWTO Alex, I wanted to add a couple of remarks here since I had an awful time getting mgetty to work correctly for me, eventually compiling mgetty on Slackware before I figured out what wasn’t working. Maybe it’s modem-specific (I am using a Multitech MT5600ZDX), but my modem would never pick up correctly. The mgetty log files showed the modem returning NO CARRIER instead of the CONNECT string, mgetty would then bail and respawn, here is an excerpt from the log file (/var/log/mgetty/mg_ttyS0.log):

01/25 23:34:29 yS0   waiting for line to clear (VTIME=1), read:
01/25 23:34:29 yS0  send: \dATQ0V1H0[0d]
01/25 23:34:30 yS0  waiting for ``OK''
01/25 23:34:30 yS0   got: ATQ0V1H0[0d]
01/25 23:34:30 yS0    CND: ATQ0V1H0[0d][0a]OK ** found **
[COLOR="RoyalBlue"]01/25 23:34:30 yS0  send: AT[0d][/COLOR]
01/25 23:34:30 yS0  waiting for ``OK''
01/25 23:34:30 yS0   got: [0d]
01/25 23:34:30 yS0    CND: OK[0a]AT[0d]
01/25 23:34:30 yS0    CND: AT[0d][0a]OK ** found **
01/25 23:34:30 yS0   waiting for line to clear (VTIME=3), read: [0d][0a]
01/25 23:34:30 yS0   removing lock file
01/25 23:34:30 yS0  waiting...
01/25 23:35:22 yS0    select returned 1
01/25 23:35:22 yS0   checking lockfiles, locking the line
01/25 23:35:22 yS0   makelock(ttyS0) called
01/25 23:35:22 yS0   do_makelock: lock='/var/lock/LCK..ttyS0'
01/25 23:35:22 yS0   lock made
01/25 23:35:22 yS0  wfr: waiting for ``RING''
01/25 23:35:22 yS0   got: [0d][0a]RING[0d]
01/25 23:35:22 yS0    CND: RING
01/25 23:35:22 yS0   wfr: rc=0, drn=0
01/25 23:35:22 yS0    CND: check no: 'none'
01/25 23:35:22 yS0  send: ATA[0d]
[COLOR="Red"]01/25 23:35:22 yS0  waiting for ``CONNECT''
01/25 23:35:22 yS0   got: [0d]
01/25 23:35:24 yS0    CND: OK[0a]NO CARRIER
01/25 23:35:24 yS0  found action string: ``NO CARRIER''
01/25 23:35:24 ##### failed A_FAIL dev=ttyS0, pid=4661, caller='none', conn='', name=''[/COLOR]

Long story short, what I finally figured out is that mgetty isn’t sending the correct init string to the modem, so it apparently doesn’t know that it is supposed to CONNECT when the phone rings. The problem init line (highlighted in blue) contains only “AT”; to get the modem to pick up I had to make mgetty send “ATS0=0Q0&D3&C1” instead. The default value for this string is hardcoded at compile-time, but we can use the init-chat parameter in /etc/mgetty/mgetty.config to specify the entire init sequence. I replaced the contents of mgetty.config with the following:

data-only YES
init-chat "" \dATQ0V1H0 OK ATS0=0Q0&D3&C1 OK

When I restarted mgetty and dialed in the modem picked up immediately and connected, bringing me straight to a login prompt.

I hope this helps other people who are banging their heads on the wall.

---

### Post by Nerdcentric on 2007-04-04
First, thanks to both of the posters above, this information helped a lot! 

I did run into a problem with Ubuntu 6.10:

> 4. Add a line to the file /etc/inittab 
Code:
S0:2345:respawn:/sbin/mgetty ttyS0

This step threw me since Ubuntu 6.10 no longers has an inittab.  Instead of this step I had to do the following:

1. Add a file named mgetty to /etc/event.d with:
[INDENT]```
start on runlevel-2
start on runlevel-3
start on runlevel-4
start on runlevel-5

stop on shutdown

respawn /sbin/mgetty ttyS0
```[/INDENT]

Once I added that file, I rebooted my machine and the PPP server worked flawlessly.  So I hope this helps someone! :biggrin:

---

### Post by styelz on 2007-04-17
Be carefull if using PPPOE for ADSL with the above settings.

Setting "-detach" in the /etc/ppp/options causes the pppoe_on_boot to stop the boot process.
I resolved this by placing all the options suggested above into the /etc/ppp/options.ttyS0 file instead.

Best of luck.

---

### Post by quiricada on 2007-06-01
thanks for the howto.

running ubuntu 7.04 feisty fawn

followed nerdcentric's post and nothing!

finally got it working with these

1. Add a file named ttyS0 (instead of mgetty) to /etc/event.d with:

```

start on runlevel 2
start on runlevel 3
start on runlevel 4
start on runlevel 5

stop on shutdown

respawn
exec /sbin/mgetty ttyS0

```


note the slight syntax changes vs. nerdcentric's ubuntu 6.10.

---

### Post by virtgrav on 2007-10-28
I have feisty fawn and used the HOWTO dialin PPP server, RAS server.
I an not having any luck initializing the modem. I am using an external modem: BEST DATA 56K on a test sever. I followed all the suggestions in the HOWTO dialin PPP server,but, when I try to dialin from a laptop with a cell phone, the modem dose not pickup. Does anyone have any suggestions?

Thanks,

virtgrav

P.S.
The modem is on ttyS1. When I try the KPPP, it initializes the modem and dials out.

---

### Post by bigdaddyweed on 2007-12-01
> Part II.b - Accessing internet from a remote client

I'm sure there other or better solutions to that, but that was easy enough and it worked for me.

Code:
sudo apt-get install ipmasqDone. ipmasq automatically senses all your interfaces and initializes IP Masquerade forwarding/firewalling and allows you to connect to the rest of your network and the Internet.

I didn't have to do any more configurations for that.


I have "upgrade'd" & "update'd" my linux 6.06 server box, allowed all repositories. But i still get and error when i do "sudo apt-get install ipmasq" 

Everything has worked for my up to this point so i am not sure what is going on.

Any Help??

---

### Post by al108 on 2007-12-12
> **virtgrav said:**
> I have feisty fawn and used the HOWTO dialin PPP server, RAS server.
I an not having any luck initializing the modem. I am using an external modem: BEST DATA 56K on a test sever. I followed all the suggestions in the HOWTO dialin PPP server,but, when I try to dialin from a laptop with a cell phone, the modem dose not pickup. Does anyone have any suggestions?

Thanks,

virtgrav

P.S.
The modem is on ttyS1. When I try the KPPP, it initializes the modem and dials out.

I haven't been using this configuration for a while now, but I do remember a lot of little things could make a difference. Also some modems could require additional configuration commands. Try resetting your modem to factory settings first, look at different AT commands that might enable your modem to answer. It wouldn't matter if it doesn't pick up whether you dial from a laptop with a cellphone or any other phone. I used external US Robotics and it worked fine out of the box.

---

### Post by al108 on 2007-12-12
> **bigdaddyweed said:**
> I have "upgrade'd" & "update'd" my linux 6.06 server box, allowed all repositories. But i still get and error when i do "sudo apt-get install ipmasq" 

Everything has worked for my up to this point so i am not sure what is going on.

Any Help??

Perhaps you can post your error.

---

### Post by jalla2000 on 2008-02-05
Should it be possible to use my cell-phone connected to my server at /dev/ttyUSB0 as the answering internet-sharing modem? That would be very interesting since in norway there are cell-phone subscriptions that allow free calls between selectable numbers. I currently have my Nokia 7250i connected to my ubuntu server (DKU-5 cable). What do you guys think about this?

---

### Post by john_linuxuser on 2008-05-23
> **jalla2000 said:**
> Should it be possible to use my cell-phone connected to my server at /dev/ttyUSB0 as the answering internet-sharing modem? That would be very interesting since in norway there are cell-phone subscriptions that allow free calls between selectable numbers. I currently have my Nokia 7250i connected to my ubuntu server (DKU-5 cable). What do you guys think about this?
Jalla, If you get any response, please let me know. 
I am preparing for the MCSE networking exam and I want to practice dial-in setup.
I live in an area that does not have a land line phone service but I do get cell phone services. I have 2 cell phones.

John

---

### Post by DEVMRS on 2010-04-18
I just want to setup my notebook as a dial-in server for my old Atari Falcon030 using a null modem cable. Is there anything special I have to do?

Thanks!

---

### Post by TheBuzzer on 2011-11-10
Just installed on my Poweredge 1850 server with Ubuntu 11.10 server and I need an update for setting up a dialin PPP server!?

---

### Post by kustomjs on 2011-11-25
I know this topic is about 2-3 years old but I just installed this on a old desktop with 10.04.3lts installed using external 56k modem and having issues with the guide like:

when it ask to create /etc/ppp/options.ttyS0 I get this:

Failed to open /etc/ppp/options.ttyS0  : No such file or directory

the settings are on 777 for permissions.

---

### Post by al108 on 2011-11-30
Yeah it's been a long time. Let me see if I can figure it out:)

---

### Post by al108 on 2011-11-30
I hope you already figured it out. If not let me know - I'm sure we can get it to work. 

Without too much looking in too it are you just having problem creating the file? What exact command did you use to create the file? and what are the 777 permissions for if the file doesn't exist? Creating the file could be done in many different ways - like ```
sudo gedit /etc/ppp/options.ttyS0
``` and type in whatever you need... It just worked for me. Default Ubuntu 11.04 i386 Desktop installation.... 

If I understand  you right - it sounds like the /etc/ppp doesn't exist in your installation for some reason. Try ```
sudo apt-get install ppp
``` and ```
sudo apt-get install pppconfig
```I hope this helps


> **kustomjs said:**
> I know this topic is about 2-3 years old but I just installed this on a old desktop with 10.04.3lts installed using external 56k modem and having issues with the guide like:

when it ask to create /etc/ppp/options.ttyS0 I get this:

Failed to open /etc/ppp/options.ttyS0  : No such file or directory

the settings are on 777 for permissions.

---

### Post by al108 on 2011-12-01
> **TheBuzzer said:**
> Just installed on my Poweredge 1850 server with Ubuntu 11.10 server and I need an update for setting up a dialin PPP server!?


I'm trying to go through the howto again it looks like /etc/inittab doesn't exist anymore. It's been suggested somewhere if you will put one in there Ubuntu will honor it. Others (_[COLOR=Blue][Nerdcentric]("http://ubuntuforums.org/member.php?u=267466")[/COLOR]_ and _[COLOR=black][ quiricada]("http://ubuntuforums.org/member.php?u=193088")[/COLOR] _) have suggested that /etc/event.d/ should be used instead. Looking at [_[COLOR=Blue]SerialConsoleHowto[/COLOR]_ ]("https://help.ubuntu.com/community/SerialConsoleHowto")for newer versions of Ubuntu we have to use ```
/etc/init/ttyS0.conf
```  It seems like this should be appropriate content for it

```
# ttyS0 - mgetty
#
# This service maintains a mgetty on ttyS0 from the point the system is
# started until it is shut down again.
start on stopped rc RUNLEVEL=[2345]
stop on runlevel [!2345]

respawn
exec /sbin/mgetty ttyS0
```I don't see other differences from the guide

---

### Post by TheBuzzer on 2012-01-18
> **al108 said:**
> I'm trying to go through the howto again it looks like /etc/inittab doesn't exist anymore. It's been suggested somewhere if you will put one in there Ubuntu will honor it. Others (_[COLOR=Blue][Nerdcentric]("http://ubuntuforums.org/member.php?u=267466")[/COLOR]_ and _[COLOR=black][ quiricada]("http://ubuntuforums.org/member.php?u=193088")[/COLOR] _) have suggested that /etc/event.d/ should be used instead. Looking at [_[COLOR=Blue]SerialConsoleHowto[/COLOR]_ ]("https://help.ubuntu.com/community/SerialConsoleHowto")for newer versions of Ubuntu we have to use ```
/etc/init/ttyS0.conf
```  It seems like this should be appropriate content for it

```
# ttyS0 - mgetty
#
# This service maintains a mgetty on ttyS0 from the point the system is
# started until it is shut down again.
start on stopped rc RUNLEVEL=[2345]
stop on runlevel [!2345]

respawn
exec /sbin/mgetty ttyS0
```I don't see other differences from the guide


My modem is HSF modem and even doesn't work, so I can't configure the ttyS0 channel! I have "No pre-built modules for: Ubuntu-11.10 linux-3.0.0-14-server x86_64-SMP" error!! The compiler doesn't find smp_lock.h in the include for linux, so how can I find this header??

---

### Post by csnow on 2012-11-19
I would like to setup this linux server with internet share for winxp desktop to dial-in.

I have set up the ppp server for ubuntu v8.10 desktop version for winxp dialup.
I test it, but the winxp cannot get the ip from ppp server.
Any hints for it?

I have tried to hardcode the ip from winxp.
But it make the connection for a very short moment (1sec) and drop off.
The ip ??

Please help. Thank you very much.

---

### Post by al108 on 2012-11-21
Hey, I don't have the setup working anymore but you should be able to get it work.
[LEFT]It would seem that something could be off in /etc/ppp/options/ttyS0 more about it in section 10 of part 2. Also try debug option in it. See if it gives you more info.
[/LEFT]

> **csnow said:**
> I would like to setup this linux server with internet share for winxp desktop to dial-in.

I have set up the ppp server for ubuntu v8.10 desktop version for winxp dialup.
I test it, but the winxp cannot get the ip from ppp server.
Any hints for it?

I have tried to hardcode the ip from winxp.
But it make the connection for a very short moment (1sec) and drop off.
The ip ??

Please help. Thank you very much.

---

### Post by csnow on 2012-11-25
Thanks al108.

I got the connection.

But I found that the winxp side canNOT connect to internet and NOT allow to ping [www.google.com](www.google.com).
Even no internet connection, winxp can ping the server ip and dns service provider ip.

I have input the command "iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE" without problem.
eth1 was connected to the internet.

Please help.

---

### Post by csnow on 2012-11-27
Only allow VPN and remote desktop??

---

