---
title: "HOWTO: Reverse VNC"
date: 2006-11-14
forum: Tutorials
---

### Post by dbott67 on 2006-11-14
[COLOR=Red]Note: As of November 27, 2007 this does not work with the latest version of Ubuntu (Gutsy Gibbon 7.10), however, [dazwin]("http://ubuntuforums.org/member.php?u=92072") has provided a good workaround using xvncviewer in [post #66]("http://ubuntuforums.org/showthread.php?p=3858988#post3858988").
[/COLOR]
VNC is a great tool that can aid in training and troubleshooting, however, with many people running NAT routers (such as D-Link, Linksys, Netgear, etc.) it can be quite difficult to establish a connection.

The problem is that these types of firewalls block ***unsolicited*** inbound traffic, preventing you from establishing a connection.  Many times, the person requiring assistance does not have the technical expertise to configure "port forwarding" on the router, or they do not have access to the device.

As long they can connect to the internet, they could establish a 'reverse VNC' connection to you --- allowing you to view their desktop.  The only caveat is that if you are behind a NAT router or firewall, you must have configured 'port forwarding' on port 5500 to forward to your internal IP address.

**_How To Setup Reverse VNC_**

1. Make sure that you have setup any necessary port-forwarding on ***your router*** to forward TCP port 5500 to ***your internal IP address***.  You may want to consider using a static IP (or static DHCP), so that you always have the same internal IP address.

I also use a dynamic DNS service so that I can just tell people to connect to ***myhost*.dyndns.org**, rather than having to tell them my external IP address.

2. On the "remote" computer (the one that you want to control), you need to install the x11vnc package:
```
sudo apt-get install x11vnc
```3. Before the remote user can "send their desktop", you need to set vncviewer to listen-mode on your computer:
```
vncviewer -listen 0

```4. Lastly, the **remote user** needs to issue the following command:
```
x11vnc -connect your.external.ip.address:5500
``` or
```
x11vnc -connect ***myhost*.dyndns.org:5500**
```**_Addendum:_**

For those that really want to shield the remote user from the command line, you could create a file on the desktop called "Remote_help.sh" and enter the following:
```
#!/bin/bash
x11vnc -connect ***myhost*.dyndns.org:5500**
```Don't forget to change the permissions to 'executable':
```
chmod 755 ~/Desktop/Remote_Help.sh
```Now, they just have to double-click the "Remote_Help.sh" file and select RUN.

If your router is configured correctly, their desktop should appear automatically.

Attached is a screenshot of my desktop showing 2 remote laptops (VNC:Tecra & VNC:Dapper) that have connected using this method.

-Dave

---

### Post by NorthCoast on 2006-11-14
Sweet.  Thanks for the writeup.  Hopefully this can help folks setup support with work or for grandma.  This has saved me from a few long drives.  After the initial setup on the remotes you now have a simple "click so and so and I'll fix it" system.

This is a better solution than an MS centric solution and works just as well and is much more flexible.

I'd add that you might setup the port forwarding so that you activate and deactivate it as needed instead of always being on.  No sense having crackheads beating on your box.  Either via the router controls if it is easy or by running VNC only when needed.

---

### Post by widjajayd on 2006-11-24
thank you for guide 

but I have problem with this.

24/11/2006 13:30:02 The VNC desktop is mywokstation:0
PORT=5900
24/11/2006 13:30:02 Making connection to client on host xxx.dyndns.org port 5500
24/11/2006 13:30:02 connection failed: Connection refused
24/11/2006 13:30:02 reverse_connect: xxx.dyndns.org:5500 failed

any idea how to fix this, thanks.

---

### Post by dbott67 on 2006-11-24
A couple things to verify:

1. Have you enabled 'port forwarding' on your router to the internal IP address of your computer?

2. Are you running a software firewall on your computer (the one that's running 'vncviewer -listen')?

Can you post the following information:

- make & model of router
- type of internet connection (DSL/cable/dialup)
- scenario: i.e. a remote user running Ubuntu 6.06 wants to send his desktop to my computer (running Ubuntu 6.06).  He is connected via cable modem; I am connected to the internet via DSL.

A couple of other caveats:

1. If the remote user is behing a corporate firewall, they may be able to block outbound traffic (my firewall at work blocks ALL outbound traffic unless the port is explicity opened).  Most home cable/DSL routers only block unsolicited INBOUND traffic.

2. Some ISPs block certain ports to prevent their end-users from hosting servers (such as ssh, ftp, telnet, smtp, www, etc.).  They might be blocking the VNC ports (5500, 5800 & 5900).

-Dave

---

### Post by Jose Catre-Vandis on 2006-12-09
I guess the setup is similar with an XP box (the people I often help are windows users as opposed to Ubuntu). So say I have UltraVnC installed on the remote XP computer, how would that work?

---

### Post by dbott67 on 2006-12-09
> **Jose Catre-Vandis said:**
> I guess the setup is similar with an XP box (the people I often help are windows users as opposed to Ubuntu). So say I have UltraVnC installed on the remote XP computer, how would that work?

It depends:

_**1. The Single-Click Way**_

UltraVNC has a 'firewall friendly' application called the '[Single-click]("http://www.uvnc.com/addons/singleclick.html")' applet.  The SC applet contains all of the information in a single, small file that can be run from any Windows PC --- without any additional software.  If you go to the UVNC website, they provide you with the generic text; you just replace their text with your IP (or DynDNS address) and a few other pieces of information.  Upload the file to their site & they will compile it into an executable that you can then host on a website (or e-mail to friends, etc.).

All they have to do is double-click the file and it will try to establish a connection to your computer.

**_2. The Other Way - Have Them Download & Install VNC_**

The full VNC application has the ability to initiate it's own outbound connection (I'll refer specifically to UltraVNC in this case, but I'm sure it's quite similar for Tight, Real and other variants).

With UVNC, you tell them to start the UVNC server and right-click the icon in the task bar and select 'ADD NEW CLIENT'.  They need to add YOUR external IP address (or DynDNS host) and click OK.

You need to be running 'vncviewer -listen' on your Linux computer.  You would also need to forward port 5500 on your router to your internal IP address if you have a NAT firewall.

-Dave

---

### Post by Jose Catre-Vandis on 2006-12-09
Thanks, that's very helpful :)

---

### Post by Jose Catre-Vandis on 2006-12-09
Tested with uvnc on XP and works fine. How do I run vncviewer -listen without having a terminal open all the time, preferbly on boot?

---

### Post by dbott67 on 2006-12-09
You could write a little bash script:

1. Create a script called '**vnc-listen.sh**' in your home directory:
```
gedit ~/vnc-listen.sh
```
2. Add the following lines of text:
```
#!/bin/bash
vncviewer -listen
```
3. Save the file
4. Set the script as executable
```
chmod 755 ~/vnc-listen.sh
```
5. Select **SYSTEM > PREFERENCES > SESSIONS**
6. Select the STARTUP PROGRAMS tab
7. Add the startup command: **~/vnc-listen.sh**
8. Click **OK**.
9. Restart and test.

Let me know how you make out.

-Dave

---

### Post by Jose Catre-Vandis on 2006-12-09
works a treat, sorry, was having a senior moment about setting it up to run without a terminal! Thanks for you help, and its a good howto :)

---

### Post by bodhi.zazen on 2006-12-21
Nice How-to

This thread has been added to the UDSF wiki.

[Reverse_VNC](http://doc.gwos.org/index.php/Reverse_VNC)

---

### Post by Choad on 2006-12-27
i must say this is an awesome guide!

 i set up an account at dyndns.org, and my ip is now pointed to by going to choad.getmyip.com 

i am home for christmas right now, and will be changing the settigns again when i go back to uni... but that doesnt really matter i can change the settings from my end no problem, i just want to make sure my niece's new computer is set up correctly. right now i have 

```
#!/bin/bash
x11vnc -connect 192.168.0.5:5500

```

on her computer. it was running over the lan perfectly. shall i just change that to 

```
#!/bin/bash
x11vnc -connect choad.getmyip.com:5500

```

???

will that be all thats needed from her end?

---

### Post by dbott67 on 2006-12-27
Yep... that's it! :)

Just make sure that if you're running a NAT firewall (or whatever) that you forward traffic on port 5500 to the internal IP address of your computer when you're at university.

-Dave

---

### Post by killerrobot on 2006-12-27
This is insecure.  VNC traffic is unencrypted, so anyone can see what you type.  That includes  root password when you sudo, or your bank password when you enter it in firefox.

tunnel over ssh to encrypt the data.

---

### Post by OMRebel on 2006-12-27
@killerrobot - how do you do that?

---

### Post by dbott67 on 2006-12-27
True, however, this is more for helping provide remote assistance to a user that does not have the technical know-how to setup port forwarding on their router or configure a VNC server, etc.

People should not be using this method to do online banking and if they're really security-conscious they should be changing their password regularly.

-Dave

---

### Post by dbott67 on 2006-12-27
> **OMRebel said:**
> @killerrobot - how do you do that?

[http://www.linuxplanet.com/linuxplanet/tutorials/6155/1/](http://www.linuxplanet.com/linuxplanet/tutorials/6155/1/)

Keep in mind that this does add some overhead and will slow down the session.  The goal of this HOWTO is to provide a firewall-friendly solution that allows someone to provide remote VNC access to their desktop, especially if they do not have access to the NAT router.

Of course, you could use my HOWTO to access their system, then:
1. login to the router
2. set their system to use static ips (or static DHCP/reserved IPs)
3. setup port forwarding on 22, 5500, 5800 & 5900 to their internal IP
4. setup a vnc/ssh tunnel back to your computer
5. provide them with a user account & password to access your computer
6. take 2 tylenol for the headache


-Dave

---

### Post by killerrobot on 2006-12-28
agreed, tunelling does make it a little more difficult.  I agree that unencrypted vnc is fine if you're showing where things are on the computer, etc.  I don't want to hijack this thread and turn it into a security topic, but since it's addressed to vnc newbies, I figured I should point it out.  In my experience, vnc has proven very valuable, and I always use it for more than I intend. 

I use vnc often, as I tend to work from many different machines that don't all have the same software installed.  I open up a vnc session and work away, and my desktop is always the same as I left it.  I generally do this from windows (hehe... windows has evolved into a glorified terminal) and once putty is set up to tunnel it takes about four and half seconds to get the thing going when I first sit down at the computer.  

As for the overhead, yeah it probably does slow it down some, but I'd guess that the network delay is still probably large compared to the additional packet computation.  I don't know how many additional packets are required though...

as for the most secure way of adjusting routers remotely, I'd simply ssh into the computer and use lynx to access the router.

---

### Post by killerrobot on 2006-12-28
oh!  one more thing I thought of - 

when you tunnel, you don't need to forward any ports for vnc.  The tunnel will send all 5900 ports (or whichever port your vnc flavor uses) to the ssh port.  Thus the router doesn't need to know about it.  of course then they have to have an ssh dameon running....    but that does help balance things out :)

---

### Post by krunge on 2007-02-20
Here is some more related information: [http://www.karlrunge.com/x11vnc/faq.html#faq-singleclick]("http://www.karlrunge.com/x11vnc/faq.html#faq-singleclick")
including SSL tunnelling with stunnel.

---

### Post by dbott67 on 2007-02-22
> **krunge said:**
> Here is some more related information: [http://www.karlrunge.com/x11vnc/#faq-singleclick]("http://www.karlrunge.com/x11vnc/#faq-singleclick")
including SSL tunnelling with stunnel.

This is an excellent guide.  Very comprehensive --- I wish I knew about it a long time ago.  Thanks for writing it and posting the link.

-Dave

---

### Post by dbott67 on 2007-02-22
> **widjajayd said:**
> thank you for guide 

but I have problem with this.

24/11/2006 13:30:02 The VNC desktop is mywokstation:0
PORT=5900
24/11/2006 13:30:02 Making connection to client on host xxx.dyndns.org port 5500
24/11/2006 13:30:02 connection failed: Connection refused
24/11/2006 13:30:02 reverse_connect: xxx.dyndns.org:5500 failed

any idea how to fix this, thanks.

As a follow-up to this post, I just noticed that after installing Beryl/XGL I now get this error message when I try to connect.  When I logout and select the 'Gnome' session, the problem goes away, so there may be an issue reverse-VNCing to a computer running Beryl/XGL/AIGLX.

-Dave

---

### Post by krunge on 2007-03-08
> As a follow-up to this post, I just noticed that after installing Beryl/XGL I now get this error message when I try to connect. When I logout and select the 'Gnome' session, the problem goes away, so there may be an issue reverse-VNCing to a computer running Beryl/XGL/AIGLX.

This should be equivalent to typing:```
telnet xxx.dyndns.org 5500
``` in a shell. It's hard to believe a window manager/desktop would affect that--but I'll believe anything these days...

BTW, there are some bugs with Beryl/XGL and XDAMAGE that effect x11vnc: [http://www.karlrunge.com/x11vnc/faq.html#faq-beryl]("http://www.karlrunge.com/x11vnc/faq.html#faq-beryl") that may require the -noxdamage option to be used. I'm not sure how hard folks are working to fix this bug... which is a shame because XDAMAGE use gives a nice improvement in responsiveness and less CPU usage for x11vnc.

---

### Post by fakie_flip on 2007-05-20
Great guide, but you could improve by giving instructions for a secure encrypted connection with ssh rather than an unencrypted one that anyone could sniff and see whats going on.

Is there anyway to do a reverse ssh connection? I was thinking of locking my computer up with a firewall and just having it send a reverse connection to me every hour by the cron daemon, and if I have a client listening, I will get the connection, otherwise nothing happens.

---

### Post by dbott67 on 2007-05-20
@fakie_flip:

True, security is an issue.  Karl Runge has a very comprehensive  guide on x11vnc.  I believe he is the person that developed the application and has provided a link on how-to make a secure reverse connection here:

> **krunge said:**
> Here is some more related information: [http://www.karlrunge.com/x11vnc/#faq-singleclick](http://www.karlrunge.com/x11vnc/#faq-singleclick)
including SSL tunnelling with stunnel.

I have not tried Karl's method, but he does have a recent update as of April '07 that allows user's to specify "-ssl SAVE" to the command instead of using stunnel.  The version in the Feisty repos does not appear to have the version with the -ssl option, so you would need to use the stunnel option or compile from source.  Again, this may prove to be cumbersome for the person requiring the assistance.

There ***may*** also be a noticeable performance hit.  When I used to use VNC over SSH, I found the performance very sluggish.  Now, I use NX machine for remote access to my machine, in addition to the standard SSH & SCP utils.

My main goal for this how-to is providing some remote troubleshooting support for friends and family with minimal effort on the remote side, especially when they don't have the knowledge or capability to setup port-forwarding on their firewall.  My unsecured method may just allow the support person enough access to configure a secure alternative using stunnel or VNC over SSH.

Another option is to SSH to another user's terminal session using 'screen':
[http://ubuntuforums.org/showthread.php?t=299286](http://ubuntuforums.org/showthread.php?t=299286)

Basically, it allows you to "share" a terminal window so that the remote user can see what you're typing.  The downside is that the remote user needs to setup SSH server and possibly forward port 22 to their desktop.

-Dave

---

### Post by dannyboy79 on 2007-05-21
> **dbott67 said:**
>  Now, I use NX machine for remote access to my machine, in addition to the standard SSH & SCP utils.

-Dave

I know this is off topic, but can you please inform me exactly what version of nxserver, nxnode, nxclient you're using and on what os's you've tried the client from. ALso, whether or not you use a custom public/private key pair (meaning NOT the default one) or do you juse use password authentification? Thank you. Then, if you do use a custom key pair, can you maybe start a new thread for me or post in the current Nxserver thread how exactly you did it? I would and I am sur eother users, would really appreciate that.

---

### Post by dbott67 on 2007-05-21
Hi Dannyboy79,

I use the following versions of NX on Feisty:
```
dbott@feisty:~$ ls -all | grep nx
drwxr-xr-x  6 dbott dbott     4096 2007-05-21 09:04 .nx
-rw-r--r--  1 dbott dbott  3492870 2007-04-22 21:07 nxclient_[COLOR=Blue]2.1.0-17_i386.[/COLOR]deb
-rw-r--r--  1 dbott dbott  5144890 2007-04-22 21:06 nxnode_[COLOR=Blue]2.1.0-22_i386[/COLOR].deb
-rw-r--r--  1 dbott dbott  4970714 2007-04-22 21:05 nxserver_[COLOR=Blue]2.1.0-22_i386[/COLOR].deb

```

I just use the SSH authentication:
[quote=From NX Admin Manual]**4. NX Server Authentication**
      Starting from version 1.5.0, NX is configured by default to allow access for any system user, as long as the user provides valid credentials for the SSH login...[/quote]

I'm the only user & SSH runs on a non-standard port, plus I run [DenyHosts]("http://denyhosts.sourceforge.net/") (just in case).

-Dave

---

### Post by dannyboy79 on 2007-05-21
I am assuming that your above statement means you just use password auth correct? meaning you DON'T have a public/private key pair to log into your ssh server nor for your nxclient correct? Which os's have you tried the client on? WinXP, Ubuntu???

---

### Post by dbott67 on 2007-05-21
Correct, just password auth.

I have used nxclient from:

1. my laptop (multiboot: WinXP Pro and Ubuntu 6.10.  I also have Vista Ultimate, Windows 2003 Server and Windows MCE installed, but I've never tried it)
2. my desktop (Ubuntu 7.04)
3. work (Win XP Pro)

I can try it from Vista and/or Windows 2003 for you, if you require some sort of confirmation.

As for the [public/private key for SSH]("http://www-128.ibm.com/developerworks/library/l-keyc.html"), I have found a couple of good documents that explains the pros of using his method, however, they all seem to assume that you'll be using the same machine for remote access.  In my case, I may want to access my home system remotely from an unknown system.   For example, let's say I'm visiting a friend and want to SSH from there so that I can access some files or documents.  

I'm guessing that the public/private keys work best for "known clients" and require some setup (importing of keys & what-not).  Without access to the private key, remote access is impossible.

For this reason, I use password only authentication in conjunction with a non-standard port and DenyHosts.

-Dave

---

### Post by dannyboy79 on 2007-05-21
well, what you do is put the public key on all the remote machines that you'll be accessing (and leave the private key within your ~/.ssh/ folder) so that just means that if you want to access your machine (which now is considered a remote machine), you make sure that your authorized_keys file is your public key and that you have your private key with you, like on a usb key or what have you. I pretty much use putty from most all the remote machines I connnect from since they are mostly winbloz, so I have used puttygen to make a .ppk private key file and I just have it saved on my 1gb usb key and I log into my machine using that. Then if I come across a linux computer, then I just install ssh if it's not installed yet and instead of saving my private key to that machine (very insecure) then I use the -i option and specify where the id_rsa file is located. Per man ssh:

-i identity_file
             Selects a file from which the identity (private key) for RSA or
             DSA authentication is read.  The default is ~/.ssh/identity for
             protocol version 1, and ~/.ssh/id_rsa and ~/.ssh/id_dsa for proâ
             tocol version 2.  Identity files may also be specified on a per-
             host basis in the configuration file.  It is possible to have
             multiple -i options (and multiple identities specified in configâ
             uration files).

So that's pretty much public/private key pairs in a nut shell. The problem arises because you can't have a passphrase for your key pair and have it work with Nxclient for some reason so you need to have a passphraseless key pair which in my miind kind of defeats the purpose. And I also have always had trouble even getting a custom key pair to work with Nxserver but I'll check out the link you provided. THanks for all your help and answers and patience with me. :-)

---

### Post by dbott67 on 2007-05-21
> **dannyboy79 said:**
> ... if you want to access your machine (which now is considered a remote machine), you make sure that your authorized_keys file is your public key and that you have your private key with you, like on a usb key... 

That's pretty much what I figured was required... keep the key on USB.  I've got a 2 GB Titanium SanDisk with [U3]("http://www.u3.com/") (plus all the nice little apps, such as SSH, OpenOffice, Firefox, etc. and a whole slew of archived apps that I might need to install: VNC, AVG, anti-spyware, etc.).  I carry the drive with me when I'm at work, but if I happen to be at my parent's place or at the in-laws and forget the USB drive, I'm out of luck.

> THanks for all your help and answers and patience with me. :-)

You're quite welcome.  Thanks for clarifying the RSA/DSA key stuff.

-Dave

---

### Post by ritterrav on 2007-08-26
Well i tried and on the remote PC everything is good, but its on mine that im having the prob (im the one that wants to take control my GF comp) 

She cant connect to me. Yes i am behind a linksys router. but i am familiar with port forwarding, and i think i opened the right port, tro the right internal IP, but i cant figure out how to see what my internal IP is. it might not just be 192.168.1.100 because i have aPS3 that has its own ip along with other junk. so how do i check that? i also set
```
vncviewer -listen
``` and she just cant connect....

---

### Post by dbott67 on 2007-08-27
The command to show your interface configuration is 'ifconfig'.  It will also indicate your assigned IP.  In my case, I forward port 5500 to the IP address of my 'eth0' interface (192.168.1.106):

```
dbott@feisty:~$ [COLOR=Red]ifconfig[/COLOR] 
[COLOR=Purple]eth0 [/COLOR]     Link encap:Ethernet  HWaddr 00:50:BA:C0:A7:55  
          [COLOR=Purple]inet addr:192.168.1.106[/COLOR]  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:baff:fec0:a755/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:71686 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46585 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:58463480 (55.7 MiB)  TX bytes:7118683 (6.7 MiB)
          Interrupt:17 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.177.1  Bcast:192.168.177.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3583 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.62.1  Bcast:172.16.62.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3584 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

If you're using wireless, your interface may be wlan0, ath0 or something similar.  You may also want to consider assigning a static IP to your computer, or use a "DHCP reservation" so that you computer always has the same IP.  Otherwise, the port-forward rules will fail.

-Dave

---

### Post by Tweepy on 2007-09-15
I made a tuto, which use the Single-click feature, your friend only has to click once.
[http://www.dotmana.com/index.php/?p=336]("http://www.dotmana.com/index.php/?p=336")
Thx for your original tuto.

---

### Post by thatt on 2007-10-11
Hi everyone.

I'm just wondering if it is possible to use SSL with UVNC SC between Windows (server) and Ubuntu. Currently I've been able to setup the unencrypted remote connection between my friend's window's PC with my ubuntu laptop so that I can fix her windows problems remotely. However, since UVNC SC has SSL capability, I thought that I should make use of it for connection security but I haven't been able to find any how-to of people that have been able to implement it. I would prefer not going the SSH tunnel option being that it might over complicate stuff for her.

I'm currently using the X11VNC in universe as the listening server. My question to everyone is:

[LIST=1]
[*]I saw on karlrunge's site that the latest version support SSL. Is this the same version as the one in fiesty's universe?
[*]If the fiesty version doesn't support it, is there any other vnc that supports ssl, tightvnc or others in universe?
[*]how do i generate and setup the RC4 key for the server?
[/LIST]

I would really appreciate any help. Thanks.

---

### Post by krunge on 2007-10-12
> **thatt said:**
> 
I'm currently using the X11VNC in universe as the listening server.

I saw on karlrunge's site that the latest version support SSL. Is this the same version as the one in fiesty's universe?
I don't believe so.  Run "x11vnc -V". The SSL support came out in version 0.8.3 and I believe the debian/ubuntu version is still 0.8.2.  Run x11vnc with the "-ssl" option to test for sure.
> 
If the fiesty version doesn't support it, is there any other vnc that supports ssl, tightvnc or others in universe?

It should be an easy compile, with, say, the x11vnc-0.9.3.tar.gz tarball.  Just make sure you have the libraries' -dev packages installed. 

More info: [http://www.karlrunge.com/x11vnc/#building]("http://www.karlrunge.com/x11vnc/#building") and [http://www.karlrunge.com/x11vnc/faq.html#faq-build]("http://www.karlrunge.com/x11vnc/faq.html#faq-build")  

If you have any problems building just ask me.

There are also some binaries here that might work: [http://www.karlrunge.com/x11vnc/bins/]("http://www.karlrunge.com/x11vnc/bins/")
> 
how do i generate and setup the RC4 key for the server?

Do you mean RC4 key or SSL Certificate?  I think the SC UVNC java viewer is a pure SSL client (which is what you'd be using to connec to the x11vnc server), but I could be wrong.  I tested the SC UVNC SSL java viewer this way:
```

java -cp ./VncViewer.jar VncViewer HOST hostname PORT 5900 USESSL 1 TRUSTALL 1

``` and it works with x11vnc, however this way it does not try to verify the certificate. Maybe I am confused about what you are trying to do, since you mention your friend is running Windows and the VNC server is would be running there...

Anyway, in addition to SC UVNC, there are also a couple SSL Java Viewers distributed in the x11vnc source package (ultravnc and tightvnc ports).  Also, the SSVNC viewer [http://www.karlrunge.com/x11vnc/ssvnc.html]("http://www.karlrunge.com/x11vnc/ssvnc.html") does SSL and certificate verification and management.

---

### Post by amlucent23 on 2007-10-16
Am I also capable of doing this though NX client/server (it is just compressed vnc over ssl -   read about it at [www.nomachine.com](www.nomachine.com)), as it would be compressed and faster than regular vnc? if so, any ideas on setting it up?

---

### Post by seamuso on 2007-10-16
I use the Ultra SC + xtightvncviewer .. it has an easy option that allows for minimal colors (great for remote fixes on client/family members systems) ..

Here's what I use in gutsy ..

xtightvncviewer -listen -bgr233 -encodings "CoRRE"


the options explained (quoted from teh man pages) -

> 
       -bgr233
              Always  use the BGR233 format to encode pixel data. This reduces
              network traffic, but colors may be represented inaccurately. The
              bgr233 format is an 8-bit "true color" format, with 2 bits blue,
              3 bits green, and 3 bits red.


>        -encodings encoding-list
              TightVNC  supports  several  different  compression  methods  to
              encode  screen  updates;  this option specifies a set of them to
              use in order of preference. Encodings  are  specified  separated
              with  spaces,  and  must thus be enclosed in quotes if more than
              one is specified. Available encodings, in default  order  for  a
              remote  connection,  are  "copyrect tight hextile zlib corre rre
              raw". For a local connection (to the same machine), the  default
              order to try is "raw copyrect tight hextile zlib corre rre". Raw
              encoding is always assumed as a last option if no other encoding
              can  be used for some reason. For more information on encodings,
              see the section ENCODINGS below.


tightvncviewer refused everything until I went with the CoRRE encoding option .. listener started fine, everything looked great .. the ultravnc SC wouldn't connect .. took a little to find the answer .. :)

---

### Post by dbott67 on 2007-10-16
> **amlucent23 said:**
> Am I also capable of doing this though NX client/server (it is just compressed vnc over ssl -   read about it at [www.nomachine.com]("http://www.nomachine.com")), as it would be compressed and faster than regular vnc? if so, any ideas on setting it up?

Post #2 of this thread:

[http://ubuntuforums.org/showthread.php?t=437562](http://ubuntuforums.org/showthread.php?t=437562)

I use NoMachine to access my home PC.  The only downside is that NoMachine does not interact with the running desktop.  If you want to be able to interact with a remote user you will need to use VNC.

-Dave

---

### Post by bsalt on 2007-10-29
Does anybody know of a tool where you can type in the remote public IP of a remote location (maybe a router, maybe a computer, mabye a server, or whatever else), and then the local IP of that remote box you want to connect to, and the program would follow the trace to that box?

For example, if there was a command like this:

vnc xxx.xxx.xxx.xxx 192.168.xxx.xxx

or even something like this:

vnc mail.business.com COMPUTERNAME

---

### Post by dbott67 on 2007-10-30
By their very nature, routers would be set to block this sort of behaviour (i.e. unsolicited inbound traffic) without setting up some sort of port-forwarding rule.

There are a few tools available to help, though:

1. Repeater: [http://uvnc.com/addons/repeater.html](http://uvnc.com/addons/repeater.html)

Setup a single PC internally that you can connect to and that PC forwards/repeats the connection to the appropriate internal PC.  This is the closest to what you're asking.

2. Port Forwarding: [http://uvnc.com/addons/routerconf.html](http://uvnc.com/addons/routerconf.html)

This is the traditional way of doing it.  Set up rules to forward external ports to internal machines.

3. Single-click: [http://uvnc.com/addons/singleclick.html](http://uvnc.com/addons/singleclick.html)

This is what my HOWTO above tries to accomplish.

The links above are for UltraVNC (a Windows-based VNC app) so I'm not sure if the equivalent app exists in Linux or if Wine will work.

-Dave

---

### Post by krunge on 2007-10-30
> Does anybody know of a tool where you can type in the remote public IP of a remote location (maybe a router, maybe a computer, mabye a server, or whatever else), and then the local IP of that remote box you want to connect to, and the program would follow the trace to that box?

For example, if there was a command like this:

vnc xxx.xxx.xxx.xxx 192.168.xxx.xxx

In general this won't work unless machine xxx.xxx.xxx.xxx has been configured to do this sort of thing.

The simplest example of such a tool is ssh.  Of course this requires the sshd server configured on xxx.xxx.xxx.xxx, then we are used to doing:
```

ssh -L 5900:192.168.xxx.xxx:5900  myuser@xxx.xxx.xxx.xxx
vncviewer localhost:0

```
but this probably isn't what you were asking for.  Similarly if xxx.xxx.xxx.xxx is a firewall/router that cannot run ssh it needs to be configured to do a port redirection to 192.168.xxx.xxx:5900.

I'm collecting some reverse-vnc tricks here: [http://www.karlrunge.com/x11vnc/faq.html#faq-firewall-out]("http://www.karlrunge.com/x11vnc/faq.html#faq-firewall-out")  
and [http://www.karlrunge.com/x11vnc/faq.html#faq-singleclick]("http://www.karlrunge.com/x11vnc/faq.html#faq-singleclick").  I'd really like to get the CGI trick (vncxfer) working more generally but I am stuck.

---

### Post by lhoydal on 2007-10-30
I think I have tried to do as described, but I'm not able to make a connection.

On my Ubuntu PC i run
vncviewer -listen

On a WinXP PC I have started a UltraVNC SC i have configured, and I then start it.

Nothing happens on my Linux (ubuntu) PC, no screen pops up!

I have set up my linksys router and opened the port 5500, with forwarding to my Linux PC.

Why does it not work?
How can I control that the port forwarding REALLY is working?

I have read something about that UltraVNC SC does not communicate with Linux versions of VNC, is this so?

Are there any other "single click"/ "support versions" of VNC for XP out there which will work towards standard(linux) VNC?

---

### Post by erwall on 2007-10-30
> **lhoydal said:**
> I think I have tried to do as described, but I'm not able to make a connection.

On my Ubuntu PC i run
vncviewer -listen

On a WinXP PC I have started a UltraVNC SC i have configured, and I then start it.

Nothing happens on my Linux (ubuntu) PC, no screen pops up!

I have set up my linksys router and opened the port 5500, with forwarding to my Linux PC.

Why does it not work?
How can I control that the port forwarding REALLY is working?

I have read something about that UltraVNC SC does not communicate with Linux versions of VNC, is this so?

Are there any other "single click"/ "support versions" of VNC for XP out there which will work towards standard(linux) VNC?
It should work, I have Windows machines SC into me all the time using the method you just described.  I would say re-do the setup for the SC exe and make sure it's right, you could have a mistake in there somewhere...

---

### Post by dbott67 on 2007-10-30
> **erwall said:**
> It should work, I have Windows machines SC into me all the time using the method you just described.  I would say re-do the setup for the SC exe and make sure it's right, you could have a mistake in there somewhere...

Ditto.  I also have created a number of SC's and people are able to connect to my Linux PC from Windows XP without issue.

Also, make sure that VNC is 'listening' on port 5500.  Can you post the output of:
```
dbott@feisty:~$ [COLOR=Purple]**netstat -l | grep 5500**[/COLOR]
tcp        0      0 *:5500                  *:*                     LISTEN   
```-Dave

---

### Post by lhoydal on 2007-10-30
Thank you for answering.  And yes, i thought it should work also, bot i have obviously something wrong.

This is how I start the listener:
lhoydal@lhoydal-laptop:~$ vncviewer -listen
VNC viewer version 3.3.7 - built Mar  8 2007 22:21:34
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
vncviewer -listen: Listening on port 5500 (flash port 5400)
vncviewer -listen: Command line errors are not reported until a connection comes in.


And there it just stays..., no reaction when I try to connect via the UltraVNC SC.

This is how it looks regarding the listener:
lhoydal@lhoydal-laptop:~$ netstat -l | grep 5500
tcp        0      0 *:5500                  *:*                     LISTEN     

I did look over the UltraVNC SC configurationa couple of times, but I'll look again!

Thanks:confused:

---

### Post by lhoydal on 2007-10-30
Generated a new UltraVNC SC with just an internal ip (192.168.1.90:5500), and then tested from a PC on same LAN.  And yes, it work like a charm.

I guess then I have two options left:
1. my service provider have somehow blocked for port 5500? - is it possible, and if so, are there any ways around?

2. I have somehow set up the port forwarding wrong, but then I should have had problems with the LAN connection too?

Open for suggestions, but I guess i am mone little step closer?

thanks,

---

### Post by dbott67 on 2007-10-30
> **lhoydal said:**
> Generated a new UltraVNC SC with just an internal ip (192.168.1.90:5500), and then tested from a PC on same LAN.  And yes, it work like a charm.

I guess then I have two options left:
1. my service provider have somehow blocked for port 5500? - is it possible, and if so, are there any ways around?

2. I have somehow set up the port forwarding wrong, but then I should have had problems with the LAN connection too?

Open for suggestions, but I guess i am mone little step closer?

thanks,

_**Question 1:**_

If your service provider has blocked 5500, you could set the SC file to *any* port:
```

[HOST]
Connect to LHoydal
-connect your.public.ip.address:PORT# -noregistry
```Replace PORT# with some arbitrary number (i.e. 1234) and recompile the SC file.  Next, create the following PORT FORWARD rule in your router:

Forward external interface port 1234 to internal IP 192.168.1.90 on port 5500.

_**Question 2:**_

If you are trying from the internal LAN, the traffic does not need to pass through the port-forward filter, so it would not prove or disprove that the port-forward rule is working.

What make & model router do you have?

-Dave

---

### Post by lhoydal on 2007-10-30
Thank you, thank you, thank you!

But I must admit I am very embarrassed.

I am using a Linksys WRT54GL, and as I were setting up an alternative port forwarding, I discovered that I had NOT crossed of for the port forwarding defined for the UltaVNC.  That was it!

This tool will help me a lot.

Very sorry to to have watedt your time.

Now, as I am in- is it any standard/easy way for file transfer (like it would have been in a UltraVNC-UltraVNC session)?

---

### Post by zeroconf on 2007-10-30
[https://help.ubuntu.com/community/x11vnc](https://help.ubuntu.com/community/x11vnc)

---

### Post by dbott67 on 2007-10-30
> **lhoydal said:**
> Thank you, thank you, thank you!

...

Now, as I am in- is it any standard/easy way for file transfer (like it would have been in a UltraVNC-UltraVNC session)?

You're welcome.

I use WinSCP on my Windows machine at work to transfer files between my home computer (Ubuntu 7.04).

[http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)

Of course, this requires SSH installed & running on your Linux server and installing WinSCP on the Windows machine.

So, in a nutshell you'll need to do the following:

1. Install and configure open-ssh server on your Ubuntu computer.

2. Forward port 22 on your router to your Ubuntu computer.  I actually use a different port # (such as 1234) rather than 22, as lots of scanners tend to try brute force dictionary attacks.  Then on my router, I forward the external high number port (i.e. 1234) to port 22 on my Ubuntu box.  You may also want to install "DenyHosts" as per my signature below.

3. Test that you can acutally SSH into your Ubuntu computer.

4. On the remote Windows computer, install WinSCP and set the login settings to your SSH login settings.

Here's a few screenshots of my work computer connecting to my home computer using SSH, WinSCP and NX.

By installing WinSCP on the client machine, you don't need to worry about firewalls & routers, as all the port forwarding is done at your end.

If you wanted to use your Ubuntu computer to SCP the files, you would need to install an SSH server on the Windows computer, forward port 22 to it, etc.  A total pain vs. just installing WinSCP.

-Dave

---

### Post by OffHand on 2007-10-31
I like sftpdrive better as it works like any other network drive but you will have to pay for it. It's developped by a small company and it costs 40 dollar.

[www.sftpdrive.com](www.sftpdrive.com)

---

### Post by lhoydal on 2007-10-31
French keyboards!

OK, then a follow up problem. Hope some of you have been looking at similar problems!

Some of the clients I will support are french, and in France they have a totally different keyboard!

That will be a big problem when I use vncviewer. When I us press a G, I want it to show up as a G, and not a F(or something else) on the remote PC I am controlling.

Is there a way to start vncviewer so it will use MY keyboardsetup at the remote server.  I think that is an option in tsclient.

OR perhaps it is a way to set up tsclient in listen mode?

Anyway, it is a keyboard mapping problem in some countries.

Thanks,

---

### Post by dbott67 on 2007-10-31
> **lhoydal said:**
> French keyboards!

OK, then a follow up problem. Hope some of you have been looking at similar problems!

Some of the clients I will support are french, and in France they have a totally different keyboard!

That will be a big problem when I use vncviewer. When I us press a G, I want it to show up as a G, and not a F(or something else) on the remote PC I am controlling.

Is there a way to start vncviewer so it will use MY keyboardsetup at the remote server.  I think that is an option in tsclient.

OR perhaps it is a way to set up tsclient in listen mode?

Anyway, it is a keyboard mapping problem in some countries.

Thanks,

I think you may need to install support for your keyboard & language on each client that you're working on.  So, depending on the client (Linux, Windows, Mac, etc.) you may need to do do one of the following:

**1. Linux Client: **
    Edit the Xorg.conf file:
> 
From: [http://littlesvr.ca/linux-stuff/articles/keyblangx11/keyblangx11.php](http://littlesvr.ca/linux-stuff/articles/keyblangx11/keyblangx11.php)
**Change Keyboard Language in X11**

 **Posted by: **Andrew Smith
**Poster contact info:  **andrew at littlesvr ca
**Author:  **same as 'Posted by'
**Software: **x11 All

Say you want to use the keyboard both as an english and as a french one. You do not want to log out and select a different language but quickly switch between them.

This is how you do it on any linux machine with x11 or x.org:

Edit your config file, something like /etc/X11/xorg.conf. Find the keyboard section and add to the end of it:
    Option "XkbRules"   "xorg"
    Option "XkbLayout"  "us,ru,ro,fr"
    Option "XKbOptions" "grp:alt_shift_toggle"
The two letter country codes you can guess. The above shows us english, russian, romanian and french. I don't know where to find a list.

The second option tells it you want to use the Alt+Shift key combination to switch the input locale. Again, I don't know what else you can put into there. Being a former windows guy alt+shift is good enough for me :)

Each window manager or desktop environment comes with it's own applet that will show you the currently selected language and let you switch it with a mouse click.

Enjoy. 

I'm not in front of my Ubuntu box at the moment, so I can't verify whether or not you'll also need to go under system preferences and change the input language, keyboard or other related items.

**2. Windows Client: **
    a. Click **START > SETTINGS > CONTROL PANEL > REGIONAL AND LANGUAGE OPTIONS**
    b. Click the **LANGUAGES** tab
    c. Click **DETAILS** button
    d. Add the appropriate **KEYBOARD**
    e. Change the **KEY SETTINGS & LANGUAGE BAR** so that you can quickly switch between them.

Anyhow, hope this gets you going in the right direction.

-Dave

---

### Post by lhoydal on 2007-10-31
Yes, thank you.

i have now tested against a person in France, and i had now problems related to the different keyboard.

Have a nice day!

---

### Post by dbott67 on 2007-10-31
Just for clarity, what exactly did you have to do in order to get it working.

Thanks,
Dave

---

### Post by lhoydal on 2007-10-31
To my surprise, I did not have to do anything!

I just ran standard
vncviewer -listen

When the remote server connected I could use my normal qwerty keyboard as normal, and It worked fine on the French desktop.

I guess the vncviewer send over the ascii codes ore something.  Anyway, this turned out to not be a problem.

The reason I worried, was that i have had problems with this before when I have used PcAnyWhere ore something similar.:KS

---

### Post by erwall on 2007-11-13
Anyone gotten someone to SC into you using vncviewer -listen in Gutsy?  All I get is something like this:
```
 CConn:       Accepted connection from 44.33.22.11::48833
 CConnection: Server supports RFB protocol version 3.16
 CConnection: Using RFB protocol version 3.8
```
and no screen popping up w/the SC user's desktop as it did just fine in Feisty.  I suspect an RFB problem but no idea what that entails.

---

### Post by Corbin D on 2007-11-20
> **erwall said:**
> Anyone gotten someone to SC into you using vncviewer -listen in Gutsy?  All I get is something like this:
```
 CConn:       Accepted connection from 44.33.22.11::48833
 CConnection: Server supports RFB protocol version 3.16
 CConnection: Using RFB protocol version 3.8
```
and no screen popping up w/the SC user's desktop as it did just fine in Feisty.  I suspect an RFB problem but no idea what that entails.
I second this.  I'm on 7.10.

I type into a terminal:
```
vncviewer -listen
```
I then have a user running a SingleClick package on Windows XP, and when they run it, I see the following:
```
 CConn:       Accepted connection from XX.XXX.XXX.109::60881
 CConnection: Server supports RFB protocol version 3.16
 CConnection: Using RFB protocol version 3.8
```
It just sits there.  I don't have any screen popping up, no nothing.

Anyone have some advice for us?

---

### Post by Papulo on 2007-11-23
> **Corbin D said:**
> I second this.  I'm on 7.10.

I type into a terminal:
```
vncviewer -listen
```
I then have a user running a SingleClick package on Windows XP, and when they run it, I see the following:
```
 CConn:       Accepted connection from XX.XXX.XXX.109::60881
 CConnection: Server supports RFB protocol version 3.16
 CConnection: Using RFB protocol version 3.8
```
It just sits there.  I don't have any screen popping up, no nothing.

Anyone have some advice for us?

Hello people, mi first post in an english forums so I have to apologize for my really poor english.

I have the same problem, juts when I updated to 7.10 it started to show me that message but no window appeared.

I'm looking for the solution.

Thank's for all!

---

### Post by mrpurple on 2007-11-23
hi, i had same problem of papulo and corbin, did someone know how to solve it ?
thank you

---

### Post by dazwin on 2007-11-28
I've just opened a bug in launchpad as I have the same problem ([https://bugs.launchpad.net/ubuntu/+source/vnc/+bug/172633](https://bugs.launchpad.net/ubuntu/+source/vnc/+bug/172633))

---

### Post by Corbin D on 2007-11-28
> **dazwin said:**
> I've just opened a bug in launchpad as I have the same problem ([https://bugs.launchpad.net/ubuntu/+source/vnc/+bug/172633](https://bugs.launchpad.net/ubuntu/+source/vnc/+bug/172633))
Thank you for opening that report.  I guess we'll see what happens.

---

### Post by dbott67 on 2007-11-28
Thanks dazwin.
 
I was on Launchpad last night looking to see if there was a bug reported about it.   I wasn't sure if it was a VNC problem or not, as I am able to establish a reverse-VNC connection using the method outlined in [post #6]("http://ubuntuforums.org/showpost.php?p=1864058&postcount=6") using either the internal IP or my DynDNS address, but not using UVNC's "Single-click".
 
For example, on my Windows XP laptop (ip: 192.168.1.107), I can use UltraVNC to "add a client" and connect to Gutsy running [COLOR=blue]vncviewer -listen[/COLOR] (ip: 192.168.1.106) and I get connected.  I can also connect using my DynDNS address using the same method of "add new client".
 
I'll confirm this again tonight and then add the information to Launchpad.
 
-Dave

---

### Post by dbott67 on 2007-11-28
Okay, here's an update.  

It may be the version of RFB (remote frame buffer?) that UltraVNC single-click uses (3.16) vs. the supported versions of up to 3.6.

According the the output below, VNC-SC uses v.3.16, while UltraVNC server uses v.3.3.

Here's what I did:

I was able to connect using the "Add New Client" option in UltraVNC Server both internally and externally (see attached screen shots and text output below):

_**Successful connection from Laptop (192.168.1.107) to Gutsy (192.168.1.106) using UltraVNC Server's "Add New Client" option:**_

```
dbott@gutsy:~$ vncviewer -listen

VNC Viewer Free Edition 4.1.1 for X - built Sep 10 2007 17:17:04
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Wed Nov 28 18:49:56 2007
 main:        Listening on port 5500


Wed Nov 28 18:50:25 2007
 CConn:       Accepted connection from [COLOR=Blue]192.168.1.107::4049[/COLOR] [COLOR=Purple]<-- connection from my laptop using the internal IP address in UltraVNC[/COLOR]
 CConnection: Server supports RFB protocol [COLOR=Red]version 3.6[/COLOR]
 CConnection: Using RFB protocol [COLOR=Red]version 3.3[/COLOR]
 TXImage:     Using default colormap and visual, TrueColor, depth 24.
 CConn:       Using pixel format depth 6 (8bpp) rgb222
 CConn:       Using ZRLE encoding

Wed Nov 28 18:50:26 2007
 CConn:       Throughput 20135 kbit/s - changing to hextile encoding
 CConn:       Throughput 20135 kbit/s - changing to full colour
 CConn:       Using pixel format depth 24 (32bpp) little-endian rgb888
 CConn:       Using hextile encoding
```_**Successful connection from Laptop (192.168.1.107) to Gutsy (using public DynDNS address) using UltraVNC Server's "Add New Client" option:**_

```
dbott@gutsy:~$ vncviewer -listen

VNC Viewer Free Edition 4.1.1 for X - built Sep 10 2007 17:17:04
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Wed Nov 28 19:01:26 2007
 main:        Listening on port 5500


Wed Nov 28 19:06:37 2007
 CConn:       Accepted connection from [COLOR=Blue]69.49.xxx.yyy::62000[/COLOR] [COLOR=Purple]<-- connection from UltraVNC using my DynDNS address[/COLOR]
 CConnection: Server supports RFB protocol [COLOR=Red]version 3.6[/COLOR]
 CConnection: Using RFB protocol [COLOR=Red]version 3.3[/COLOR]

Wed Nov 28 19:06:38 2007
 TXImage:     Using default colormap and visual, TrueColor, depth 24.
 CConn:       Using pixel format depth 6 (8bpp) rgb222
 CConn:       Using ZRLE encoding
 CConn:       Throughput 11900 kbit/s - changing to hextile encoding
 CConn:       Throughput 11900 kbit/s - changing to full colour
 CConn:       Using pixel format depth 24 (32bpp) little-endian rgb888
 CConn:       Using hextile encoding
```[U][B]Unsuccessful connection from Laptop (192.168.1.107) to Gutsy (using public DynDNS address) using UltraVNC's Single-click:

[/B][/U] ```
dbott@gutsy:~$ vncviewer -listen

VNC Viewer Free Edition 4.1.1 for X - built Sep 10 2007 17:17:04
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Wed Nov 28 19:01:26 2007
 main:        Listening on port 5500

Wed Nov 28 19:10:57 2007
 CConn:       Accepted connection from 69.49.xxx.yyy::62008 [COLOR=Purple]<--- using UVNC Single-click[/COLOR]
 CConnection: Server supports RFB protocol [COLOR=Red]version 3.16[/COLOR]
 CConnection: Using RFB protocol[COLOR=Red] version 3.8[/COLOR]

Wed Nov 28 19:12:00 2007
 main:        End of stream

```Both attached screenshots show successful connections back to the vncviewer in listen mode.  It appears as though the problem lies with Ultra VNC's "Single Click" add-on application.

-Dave

---

### Post by dazwin on 2007-11-29
[COLOR="Red"]This workaround no longer works for Ubuntu 8.04 - try [post #105]("http://ubuntuforums.org/showpost.php?p=5064825&postcount=105") instead, which works for me.

(You could also download and install xvncviewer 3.3.7 from Gutsy manually - it still works in Hardy, but the above solution is probably better.)[/COLOR]

A workaround is to revert back to the old v3.3.7 viewer (from universe):

$ sudo apt-get install xvncviewer
$ sudo update-alternatives --set vncviewer /usr/bin/xrealvncviewer

---

### Post by dazwin on 2007-11-29
Ok, I opened a bug report against the wrong package. There is already a bug open for this filed against vnc4 ([https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/123631](https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/123631)).

It's also not really a bug with vncviewer, but a bug in UltraVNC SingleClick, which reports an incorrect protocol version. There is a thread about this on the UltraVNC forums:

[http://forum.ultravnc.info/viewtopic.php?t=10451](http://forum.ultravnc.info/viewtopic.php?t=10451)

---

### Post by dbott67 on 2007-11-29
> **dazwin said:**
> A workaround is to revert back to the old v3.3.7 viewer (from universe):

$ sudo apt-get install xvncviewer
$ sudo update-alternatives --set vncviewer /usr/bin/xrealvncviewer

Great work, dazwin!

Thanks for the workaround.  I will post this info into the original post.

Just to add a bit of info to the workaround:  I needed to specify the display number in the [COLOR=Purple]*vnciewer -listen*[/COLOR] command *(my original HOWTO omitted the display # and it just automatically defaulted to display 0; xvncviewer seems to default to display 1)*:
```

vncviewer -listen [COLOR=Red]0[/COLOR]
```For some reason, running *[COLOR=Purple]vncviewer -listen[/COLOR]* without specifying the display # defaulted to 1 (which means that vncviewer listens on port 5501 instead of 5500).

```
dbott@gutsy:~$ [COLOR=Red]vncviewer -listen 0[/COLOR]
VNC viewer version 3.3.7 - built May 24 2007 12:45:44
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See http://www.realvnc.com for information on VNC.
vncviewer -listen: [COLOR=Red]Listening on port 5500[/COLOR] (flash port 5400)
vncviewer -listen: Command line errors are not reported until a connection comes in.
VNC server supports protocol version 3.16 (viewer 3.3)
No authentication needed
Desktop name "WinVNC"
Connected to VNC server, using protocol version 3.3
VNC server default format:
  32 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0
Using default colormap and visual, TrueColor, depth 24.
Got 256 exact BGR233 colours out of 256
Using BGR233 pixel format:
  8 bits per pixel.
  True colour: max red 7 green 7 blue 3, shift red 0 green 3 blue 6
Using shared memory PutImage
Throughput 3690 kbit/s - changing from 8bit
Using viewer's native pixel format:
  32 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0
ShmCleanup called

``````
dbott@gutsy:~$ [COLOR=Red]vncviewer -listen[/COLOR]
VNC viewer version 3.3.7 - built May 24 2007 12:45:44
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See http://www.realvnc.com for information on VNC.
vncviewer -listen: [COLOR=Red]Listening on port 5501[/COLOR] (flash port 5401)
vncviewer -listen: Command line errors are not reported until a connection comes in.

```-Dave

---

### Post by go_beep_yourself on 2007-12-12
> **dbott67 said:**
> [COLOR=Red]can "send their desktop", you need to set vncviewer to listen-mode on your computer:
```
vncviewer -listen 0

```4. Lastly, the **remote user** needs to issue the following command:


Shouldn't that 0 be a port number such as 5500?

---

### Post by dbott67 on 2007-12-13
> **go_beep_yourself said:**
> Shouldn't that 0 be a port number such as 5500?

No. By default, the program takes the number specified (in this case 0) and adds it to 5500.  If you were to specify 5500, the app would listen on port 11,000 (5500 + 5500):
```
dbott@gutsy:~$ [COLOR=Red]vncviewer -listen 5500[/COLOR]
VNC viewer version 3.3.7 - built May 24 2007 12:45:44
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See http://www.realvnc.com for information on VNC.
vncviewer -listen: [COLOR=Red]Listening on port 11000[/COLOR] (flash port 10900)
vncviewer -listen: Command line errors are not reported until a connection comes in.

```-Dave

---

### Post by gigaferz on 2007-12-31
Hello all

ok, so im providing a kubuntu computer to a remote friend.
We are both using 7.10, i have ubuntu, and i setup somebodyelse with feisty a while ago.

I have my dynamic hostname setup, i m sure i did the protforwarding properly , (somebody from irc was looking at my personal wiki, using my.dyndns.org:2500)

But my question is what is the method to get this reverse vnc to work in gutsy?

Who has to do the workaround?, the remote computer or the local?

and what are the commands to get it done, I tried on remote computer xrealvncviewer, realvncviewer,vncviewer  with  -connect my.dyndns.org:5500 and it gives me an output with the usage and options for the viewer.
 
So far in my local network i can vnc (with the included software in ubuntu & kubuntu) my computers.

But i'd like to know the reverse method for my remote friends.

---

### Post by zipperback on 2007-12-31
> **gigaferz said:**
> Hello all

ok, so im providing a kubuntu computer to a remote friend.
We are both using 7.10, i have ubuntu, and i setup somebodyelse with feisty a while ago.

I have my dynamic hostname setup, i m sure i did the protforwarding properly , (somebody from irc was looking at my personal wiki, using my.dyndns.org:2500)

But my question is what is the method to get this reverse vnc to work in gutsy?

Who has to do the workaround?, the remote computer or the local?

and what are the commands to get it done, I tried on remote computer xrealvncviewer, realvncviewer,vncviewer  with  -connect my.dyndns.org:5500 and it gives me an output with the usage and options for the viewer.
 
So far in my local network i can vnc (with the included software in ubuntu & kubuntu) my computers.

But i'd like to know the reverse method for my remote friends.


You have to run VNC server to allow remote connections, and VNC Client is the application used to connect to the server.

If you want your friend to connect to you, then start your vnc server and have your friend use the vnc client.

- zipperback
:popcorn:

---

### Post by gigaferz on 2007-12-31
the idea is to do it the same way as the first post shows.

But since in gutsy doesnt work, id like to know how to do it.

---

### Post by zeroconf on 2008-01-01
zipperback is right - you have to use vnc server at the computer, who needs help and your computer, who will help, must use vncviewer in listen mode and have right redirections in router and open ports in firewall if used any. Default port is 5500/tcp but you can use any other port, which is not used in your networks.

For further reading you may see here - [https://help.ubuntu.com/community/x11vnc](https://help.ubuntu.com/community/x11vnc)

---

### Post by dbott67 on 2008-01-01
> **gigaferz said:**
> Hello all

ok, so im providing a kubuntu computer to a remote friend.
We are both using 7.10, i have ubuntu, and i setup somebodyelse with feisty a while ago.

I have my dynamic hostname setup, i m sure i did the protforwarding properly , (somebody from irc was looking at my personal wiki, using my.dyndns.org:2500)

But my question is what is the method to get this reverse vnc to work in gutsy?

Who has to do the workaround?, the remote computer or the local?

and what are the commands to get it done, I tried on remote computer xrealvncviewer, realvncviewer,vncviewer  with  -connect my.dyndns.org:5500 and it gives me an output with the usage and options for the viewer.
 
So far in my local network i can vnc (with the included software in ubuntu & kubuntu) my computers.

But i'd like to know the reverse method for my remote friends.

Follow all steps as outlined in [post #1]("http://ubuntuforums.org/showpost.php?p=1756919&postcount=1").

Then, on your Gutsy computer, follow the steps in [post #66]("http://ubuntuforums.org/showthread.php?p=3858988#post3858988").  

The "bug" is with the default vncviewer version provided with Gutsy.  The workaround provided by dazwin in [post #66]("http://ubuntuforums.org/showthread.php?p=3858988#post3858988") just replaces the default 'vncviewer' with the viewer provided in the **xvncviewer** package and links it to the 'vncviewer' command.  This step needs to be done on _*your*_ computer (not the remote).

Provided you have forwarded port 5500 on your router to the internal IP of your Gutsy box and set the vncviewer to listen mode:
```
vncviewer -listen 0
```

your friend should be able to run the command and his desktop should appear on your desktop:
```
x11vnc -connect your.dyndns.org:5500
```

I am currently doing this quite regularly in Gutsy with no problems since running the fix in post #66.

-Dave

---

### Post by gigaferz on 2008-01-01
thanks for the explanation dbott67.

The explanation of the bug and the workaround  is what I needed to know to do it right


SWeet!!!  I mean is unveliebable!!! 

My dyndns works!!!

Ive seen you got 2 remote computers  in your desktop, do I need another command, or everything stays the same?

---

### Post by oni5115 on 2008-01-16
I've been looking into doing this securely and was wondering if there is a more straight forward guide for it?  Something like tweepy did, but just for SSL or SSH.

So far, I installed x11vnc through apt-get, but since the 'official' version is only 0.8.2-2, I decided to roll my own .deb package.  This way I can install an updated version on their computer easily and not need to use a longer script that connects to a website to get the binary.  Since I am only working on Ubuntu boxes, it seemed a lot easier for me to do it this way.   Besides, I very much like one line command scripts, far less likely I will muck it up somehow.  :lolflag:

I assume on the computer to be controlled, I need them to run a script that has: 
x11vnc -connect host: port -ssl ???

On my machine I will need to have run SSVNC.  But I don't really see a 'listen' button on the GUI.  Only a connect.  Can it be used for a reverse connection?  I read quite a bit on x11vnc site, but it seems like all the examples are for connecting normally, unless I missed it.

I'm just trying to get to the simplest method of getting a secure connection.  Simplest, disregarding any issues you might have with corporate firewalls blocking SSL, SSH, or VNC ports (this will not be an issue).  I just want it to be secure in case I need to remote install software (and hence use the sudo password) over the internet.

NX sounded interesting, but I'd like to confirm that you cannot actually show them how to do stuff with it.

---

### Post by dbott67 on 2008-01-16
I'll let Karl (krunge - the creator/developer/author of x11vnc) answer the specifics about your questions over ssh/ssl.  He has posted a number of times in this thread.

> **oni5115 said:**
> ... NX sounded interesting, but I'd like to confirm that you cannot actually show them how to do stuff with it.

As for NX Machine, as of version 3, the capability of desktop sharing/shadowing is included:
> **Can NX be used to implement application sharing and white-board based collaboration?**                                
                               NoMachine has added support for desktop sharing and session shadowing in NX 3.0.0. 
 
This was one of the most requested features by customers and opens up NX to a full range of different usage scenarios, like remote help-desk activity and collaborative brainstorming. 
 
In the past there have been attempts to use the X11 protocol for this purpose but no one had ever reached a stage that proved to be usable. The main reason was that the involved "proxies" lacked the knowledge of the X protocol required to implement this in a reliable way. With NX it is different. 

nxagent is a fully-featured X server and knows everything it needs to know to forward a single X connection to multiple X servers on the remote clients. More technical details on nxagent running in shadow mode are available here: 
 
[http://www.nomachine.com/fr/view.php?id=FR10C01069](http://www.nomachine.com/fr/view.php?id=FR10C01069) 
 
 
_What is the difference between desktop sharing and session shadowing? _
 
NX 3.0.0 offers the possibility to connect either to a local desktop (desktop sharing of the local native display), i.e.the X server running on the NX Node host machine, or to a NX session, named the master session, running on the NX Node host machine (session shadowing). This kind of session, named shadow in both desktop sharing and session shadowing, can be requested by setting  Desktop -> Shadow in the NX Client GUI-> General tab. Upon the request of the end user, the server provides to the client the list of available sessions. The user, via the NX Available sessions GUI, can then choose to which session he/she would like to attach to.

I've added some screenshots of a shadow session in action.
-Dave

---

### Post by krunge on 2008-01-16
> **oni5115 said:**
> 
I assume on the computer to be controlled, I need them to run a script that has: 
x11vnc -connect host: port -ssl ???

Yes.  Also, if the default port (listening display :0, port 5500) is used it can just be "-connect host".

I recommend using "-ssl SAVE" to create a permanent certificate, but a temporary one might be OK too for your usage.

> 
On my machine I will need to have run SSVNC.  But I don't really see a 'listen' button on the GUI.  Only a connect.  Can it be used for a reverse connection?  I read quite a bit on x11vnc site, but it seems like all the examples are for connecting normally, unless I missed it.


To get the Listen button click on:  Options -> Reverse VNC connection (-listen)

One gotcha:  before clicking Listen you should deselect "Verify All Certs" in SSVNC.   Otherwise the SSL negotiation will fail because SSVNC doesn't have x11vnc's  public cert.

Of course if you use "x11vnc ... -ssl SAVE" and have copied the x11vnc cert to the SSVNC side for verification that is a Good Thing (prevents man in the middle).

---

### Post by oni5115 on 2008-01-17
Thanks, got it working now.  At least between my laptop and desktop on my home LAN.  Shouldn't be too hard to get it working through the internet now.

---

### Post by systemwise on 2008-01-28
Hello,

Brand new to the ubuntu world and love it so far.  This may be a stupid question but when I type:

[I]any@UbuntuTest:~$ #!/bin/bash
any@UbuntuTest:~$ xllvnc -connect tony-pc01:5901[/I]

I get:

*bash: xllvnc: command not found*

Tony-pc01 is a windows machine  with vnc listening on port 5901 rather than 5900.  I have followed the guide and carried out step 

*sudo apt-get install x11vnc*

Any ideas where I am going wrong:confused:

Cheers,

Tony

---

### Post by dannyboy79 on 2008-01-28
x11vnc is a vnc server, not a vnc client. at least that's what I thought. for example, I ssh into my home pc and while doing so I create a tunnel for vnc back to the loopback interface on the windows machine that I sshing from. them once I am connected over ssh thru putty, I start up x11vnc using this command, x11vnc --usepw, this starts the vnc server on port 5900 requiring a password. then I can connect to it through a tunneled ssh secure connection by opening tightvncviewer and using 127.0.0.1 as the ip to connect to.

So you want like vncviewer or a vnc client to connect to your windows box, I don't think you're really reverse vnc'ing? I may be misunderstanding what you're doing though.

---

### Post by krunge on 2008-01-28
> **systemwise said:**
> Hello,

[I]any@UbuntuTest:~$ #!/bin/bash
any@UbuntuTest:~$ xllvnc -connect tony-pc01:5901[/I]

I get:

*bash: xllvnc: command not found*

They are "ones" not "ells" (i.e. x-eleven-vnc).
> 
Tony-pc01 is a windows machine  with vnc listening on port 5901 rather than 5900.  I have followed the guide and carried out step 

*sudo apt-get install x11vnc*

Ah. Like dannyboy79 says, x11vnc is a VNC server.  So if Tony-pc01 is running another  VNC server it won't work.

Your command would work if Tony-pc01 was running a VNC Viewer in listen mode (but the default VNC listening port is 5500).

---

### Post by zeroconf on 2008-01-28
> **dannyboy79 said:**
> x11vnc is a vnc server, not a vnc client. at least that's what I thought. for example, I ssh into my home pc and while doing so I create a tunnel for vnc back to the loopback interface on the windows machine that I sshing from. them once I am connected over ssh thru putty, I start up x11vnc using this command, x11vnc --usepw, this starts the vnc server on port 5900 requiring a password. then I can connect to it through a tunneled ssh secure connection by opening tightvncviewer and using 127.0.0.1 as the ip to connect to.

So you want like vncviewer or a vnc client to connect to your windows box, I don't think you're really reverse vnc'ing? I may be misunderstanding what you're doing though.


Would you like to write tutorial, how you do this exactly? It would be quite interesting, especially between Windows and Linux machines.

---

### Post by bodhi.zazen on 2008-01-28
> **dannyboy79 said:**
> x11vnc is a vnc server, not a vnc client. at least that's what I thought. for example, I ssh into my home pc and while doing so I create a tunnel for vnc back to the loopback interface on the windows machine that I sshing from. them once I am connected over ssh thru putty, I start up x11vnc using this command, x11vnc --usepw, this starts the vnc server on port 5900 requiring a password. then I can connect to it through a tunneled ssh secure connection by opening tightvncviewer and using 127.0.0.1 as the ip to connect to.

So you want like vncviewer or a vnc client to connect to your windows box, I don't think you're really reverse vnc'ing? I may be misunderstanding what you're doing though.

With reverse vnc we are basically initiating the connection from the server rather then the client. This allows us to connect to a remote VNC server without our freinds and  family knowing how to coffigure their firewall / server.

The flag "-listen"

vncviewer -listen

> **zeroconf said:**
> Would you like to write tutorial, how you do this exactly? It would be quite interesting, especially between Windows and Linux machines.

[uwiki]VNC[/uwiki]

[uwiki]VNCOverSSH[/uwiki]

[uwiki]AdvancedOpenSSH[/uwiki]

---

### Post by dannyboy79 on 2008-01-28
> **bodhi.zazen said:**
> With reverse vnc we are basically initiating the connection from the server rather then the client. This allows us to connect to a remote VNC server without our freinds and  family knowing how to coffigure their firewall / server.

The flag "-listen"

vncserver -listen
 
forgive me if I am wrong here but vnc server's listen automatically. there would be no reason to add the -listen option for the vncserver command? I think the point of this guide is so that you run a vncviewer in listening mode isn't it? the person trying to help the other user would have to make their vncviewer listen, and then they activate the vnc server on their end.

zeroconf
I can write a guide but it's not that difficult. You basically use 3 programs.

openssh (ubuntu ssh server)
x11vnc on ubuntu machine (don't have it running all the time though, very insecure if it's only a password someone could brute force)
putty (ssh client) from windows machine (if you use rsa or dsa public/private keys you'll also need puttygen to convert key to what putty needs)
tightvncviewer from windows machine

I am at work when I do this so I want to ensure that work doesn't see what I am doing so I use putty and create secure encrypted tunnels for my vnc session. This is only because port 22 (ssh) is open to begin with. I don't have time to write this up now but it is super cool.

---

### Post by dbott67 on 2008-01-28
> **dannyboy79 said:**
> forgive me if I am wrong here but vnc server's listen automatically. there would be no reason to add the -listen option for the vncserver command? I think the point of this guide is so that you run a vncviewer in listening mode isn't it? the person trying to help the other user would have to make their vncviewer listen, and then they activate the vnc server on their end.

I think bodhi just had a typo.  I'm sure that he meant to type:
```
vncviewer -listen
```
as his prior explanation indicates that the the "server" is initiating the connection to the listening client.

> **dannyboy79 said:**
> zeroconf,
I can write a guide but it's not that difficult...

bodhi's links provide some pretty thorough guides to refer to for VNC & VNC over SSH that may get zeroconf started, although you may have a technique that makes it easier/better/faster, so feel free to write up a guide if the posted method has any deficiencies.

@zeroconf:

You may also want to refer to Karl's homepage.  He has compiled excellent documentation, examples and FAQs on how to best utilize x11vnc here:

[http://www.karlrunge.com/x11vnc/index.html](http://www.karlrunge.com/x11vnc/index.html)

-Dave

---

### Post by bodhi.zazen on 2008-01-28
> **dannyboy79 said:**
> forgive me if I am wrong here but vnc server's listen automatically. there would be no reason to add the -listen option for the vncserver command? I think the point of this guide is so that you run a vncviewer in listening mode isn't it? the person trying to help the other user would have to make their vncviewer listen, and then they activate the vnc server on their end.

:redface: yea, sorry for the confusion, I edited my post ...

---

### Post by DaymItzJack on 2008-02-17
I'm trying to connect from XP to my Ubuntu machine using that "single click" program, if I have listen running, it detects the computer but then does nothing after it, what's wrong?

```
jack@jack-desktop:~$ vncviewer -listen 5500

VNC Viewer Free Edition 4.1.1 for X - built Sep 10 2007 17:17:04
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Sun Feb 17 18:45:28 2008
 main:        Listening on port 5500


Sun Feb 17 18:45:38 2008
 CConn:       Accepted connection from 68.*.*.*::45817
 CConnection: Server supports RFB protocol version 3.16
 CConnection: Using RFB protocol version 3.8


```

How can I control that computer now?

---

### Post by dbott67 on 2008-02-17
> **DaymItzJack said:**
> ```
jack@jack-desktop:~$ vncviewer -listen 5500
```How can I control that computer now?
Try this:
```
jack@jack-desktop:~$ vncviewer -listen 0
```

-Dave

---

### Post by DaymItzJack on 2008-02-17
The XP is not my machine, so how would port 0 help? ;(

---

### Post by dbott67 on 2008-02-18
> **DaymItzJack said:**
> The XP is not my machine, so how would port 0 help? ;(

This runs on the _Ubuntu computer_, not XP.
```
jack@jack-desktop:~$ vncviewer -listen 0
```The 0 specifies the the desktop/port to use:

0=5500
1=5501
2=5502
etc.

By entering **vncviewer -listen 5500**, you are telling the viewer to listen on port 11,000 (5500 + 5500).

Here is the output when I set listen to 0:
```
dbott@gutsy:~$ netstat -l -n
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:39682           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:37201           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:51606           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
[COLOR=Red]tcp        0      0 0.0.0.0:5400            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:5500            0.0.0.0:*               LISTEN  [/COLOR]   
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN 
```If you'll notice the 2 lines in red indicate that VNCviewer is listening on ports 5400 (for web/java access) and port 5500 (for VNCserver).


And here it is set to 5500:

```
dbott@gutsy:~$ netstat -l -n
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:39682           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:37201           0.0.0.0:*               LISTEN     
[COLOR=Red]tcp        0      0 0.0.0.0:10900           0.0.0.0:*               LISTEN   [/COLOR]  
tcp        0      0 0.0.0.0:51606           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
[COLOR=Red]tcp        0      0 0.0.0.0:11000           0.0.0.0:*               LISTEN  [/COLOR]   
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN   
```The 2 ports in question are now 10,900 for web/java (5400 + 5500) and 11,000 (5500 + 5500).

So, set the command on your Ubuntu computer to:
```
jack@jack-desktop:~$ vncviewer -listen 0
```and you should be good to go.

-Dave

---

### Post by krunge on 2008-02-18
> **dbott67 said:**
> If you'll notice the 2 lines in red indicate that VNCviewer is listening on ports 5400 (for web/java access) and port 5500 (for VNCserver).

Actually the port 5400 is the goofy (and undocumented AFAICS) 'flash port' message system from the original VNC.

I believe this has been removed from most newer viewers, probably both for security and lack of use.

To make use of it, try this for fun:
```
# echo 'Dave, Lunch!' | nc localhost 5400
```

(or if you don't have netcat, nc, telnet localhost 5400 can be used too).

---

### Post by dbott67 on 2008-02-18
> **krunge said:**
> Actually the port 5400 is the goofy (and undocumented AFAICS) 'flash port' message system from the original VNC.

I believe this has been removed from most newer viewers, probably both for security and lack of use.

To make use of it, try this for fun:
```
# echo 'Dave, Lunch!' | nc localhost 5400
```(or if you don't have netcat, nc, telnet localhost 5400 can be used too).

Cool... thanks, Karl.

Actually, I was confusing the listening port -100 with vnc**server**'s web/java port (typically 5800).

For those that want to see Karl's example in action see the attached screenshot.

-Dave

---

### Post by DaymItzJack on 2008-02-18
I tried doing -listen 0 and that didn't popup with anything once I tried to connect.

---

### Post by dbott67 on 2008-02-18
Can you post the output of netstat -l -n (that's a lowercase L, not an uppercase i) from your Ubuntu computer:

```
dbott@gutsy:~$ netstat -l -n
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:39682           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:37201           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:51606           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
[COLOR=Red][COLOR=Black]tcp        0      0 0.0.0.0:5400            0.0.0.0:*               LISTEN [/COLOR]    
tcp        0      0 0.0.0.0:5500            0.0.0.0:*               LISTEN  [/COLOR]   
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN 
```

This will allow us to verify if the vncviewer is listening on the correct port.

Also I need to know a few more things:

1. Is the XP computer on the same network, or are you trying for remote access?

2. If it's a remote PC, are you behind a NAT router?  If so, have you forwarded TCP port 5500 to the internal IP address of your Ubuntu computer?

3. How is the XP client connecting?  Are you using UVNC single-click, or a full-blown VNC server, like UltraVNC?

4.  Are you running any firewalls on either computer?

Please provide as many details as possible as to how the XP computer is trying to establish the reverse connection.

Thanks,
Dave

---

### Post by DaymItzJack on 2008-02-18
[http://paste.ubuntu-nl.org/56552/](http://paste.ubuntu-nl.org/56552/)
that's before and after using the command "vncviewer -listen 0"

1. I'm testing on a networked one, but I'm aiming for other computers later.
2. VNC works fine on Vista last time I checked.
3. single-click
4. not that I know of

---

### Post by elvisd on 2008-03-06
dbott67!
Thank you very much for this thread/how to.
The remote support was one of my pains... I love Linux and I'm trying to deliver as much as possible linux machines to my family/parents/friends/... 
And to guide someone through linux's first step, its absolutely a 'must have' the remote support.

Thank you. Thank you. Thank you.

And what I hope is that in a next verison of ubuntu this functionality is built-in, maybe as pidgin plugin or normal menu item.

I wish you all the best!

---

### Post by doughoman on 2008-05-01
> **dazwin said:**
> A workaround is to revert back to the old v3.3.7 viewer (from universe):

$ sudo apt-get install xvncviewer
$ sudo update-alternatives --set vncviewer /usr/bin/xrealvncviewer


This workaround doesn't seem to work for hardy heron 8.04.  I get a message:
Package xvncviewer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xvncviewer has no installation candidate

Any ideas on a fix for 8.04?

---

### Post by rmconard on 2008-05-04
FYI... this still works with Hardy and Windows XP

See my post about Reverse VNC with Windows XP


[http://ubuntuforums.org/showthread.php?t=779255](http://ubuntuforums.org/showthread.php?t=779255)

---

### Post by doughoman on 2008-05-05
I read your post but it deals with ubuntu reverse connecting to windows, different than the problem with the work around I am talking about.

I am using UltraVNC SC on windows machines to reverse vnc to my ubuntu 8.04 desktop.  The bug with UltraVNC SC requires us to revert ubuntu back to the old v3.3.7 viewer.  Unfortunately it appears that version is no longer in the repositories for 8.04.

Does anyone have a new work around for 8.04?

---

### Post by nettobr on 2008-05-26
Well, got same problem...

I have a small Ultravnc SC that my clients tranfer the control of their machines (XP) to mine at home.

If I boot XP on my PC, no problem to gain control of their machines.

But If I boot Kubuntu 8.04 LTS xvnc4viewer doesnt open viewer window, they have to open a server instance of ultravncserver and add a client...

Just let us know if a workaround, or solution is available...

NettoBr

Thanks from Brazil

---

### Post by dbott67 on 2008-05-26
Does this not work (post #66 by dazwin)?

[http://ubuntuforums.org/showthread.php?p=3858988#post3858988](http://ubuntuforums.org/showthread.php?p=3858988#post3858988)

rmconard in post #100 has posted that it works for him (I haven't upgraded to Hardy yet, so I can't confirm).

-Dave

---

### Post by nettobr on 2008-05-28
Hi Dave,

Sorry, but xvncviewer is obsolete for 8.04 LTS.

New is xvnc4viewer...

and dont know what to do...

Thanks from Brazil

NettoBr

---

### Post by SprocXet on 2008-05-28
I found a solution at [forum.ultravnc.info]("http://forum.ultravnc.info/viewtopic.php?t=12353").

```
apt-get install xtightvncviewer

xtightvncviewer -encodings "hextile copyrect" -listen
```

It works for me.

---

### Post by jac0b on 2008-09-23
> **SprocXet said:**
> I found a solution at [forum.ultravnc.info]("http://forum.ultravnc.info/viewtopic.php?t=12353").

```
apt-get install xtightvncviewer

xtightvncviewer -encodings "hextile copyrect" -listen
```

It works for me.


Thanks, that works for me also.

---

### Post by kashokkumar14 on 2008-10-23
**hi dbott**
         I have an important question to looking forward a good solution.I think u've done it.I have two ubuntu systems.One system connected through static ip address and another system is connected through dynamic IP.I have to view my remote system through VNC viewer.through dyndns.org we can connect.But im not much clear about this.i used [www.dnsexit.com.I](www.dnsexit.com.I) registered my system so i got on domain name like clbtinhoc.net.later i removed this dns.i did this on static IP system.i cannot able to connect my remote dynamic IP system.if i get domain name for static IP system how do i connect my remote dynamic IP system?should i make any configuration in dynamic IP system?How do i add my dynamic remote host system in static IP system.please explain briefly.Im in very confusing.

Regards,
ASHOK

---

### Post by Tak11 on 2008-10-24
This saved my life xD

I was trying to SSH tunnel.

---

### Post by vjones777 on 2008-11-02
There is a cross-platform almost one click reverse VNC solution that even grandma can install (hopefully).  :):)  Its called [gitzo.]("http://code.google.com/p/gitso/")  Not much in the way of documentation but it seems straighforward.
I havn't used it myself as I'm already set up, but theres an audio review of it in [Episode 16]("http://podcast.ubuntu-uk.org/") (you'll have to fast forward to the section where they discuss remote support.

Hope this helps, it requires very little work at the PC at the remote end, and just setting up the firewall hole at the local end.

---

### Post by lui22 on 2009-01-17
> **SprocXet said:**
> I found a solution at [forum.ultravnc.info]("http://forum.ultravnc.info/viewtopic.php?t=12353").

```
apt-get install xtightvncviewer

xtightvncviewer -encodings "hextile copyrect" -listen
```

It works for me.

all that it shows is...
xtightvncviewer -encodings "hextile copyrect" -listen
user117@ubuntu-117:~$ xtightvncviewer -encodings "hextile copyrect" -listen
xtightvncviewer -listen: Listening on port 5500
xtightvncviewer -listen: Command line errors are not reported until a connection comes in.
... what do i do know

---

### Post by krunge on 2009-01-17
> **lui22 said:**
> all that it shows is...
xtightvncviewer -encodings "hextile copyrect" -listen
user117@ubuntu-117:~$ xtightvncviewer -encodings "hextile copyrect" -listen
xtightvncviewer -listen: Listening on port 5500
xtightvncviewer -listen: Command line errors are not reported until a connection comes in.
... what do i do know

Make a VNC server on some other machine connect to it.

---

### Post by appzattak on 2009-02-05
Hey all, I've used this single click for a while now, first on my 7.10 and then on 8.04, although on 8.04 I had to install the vnc-3.3.7.orig from source and it worked great. Now on 8.10 I went to do that and it will not install. I get this:
```
steve@steve-laptop:~/downloads/vnc-3.3.7.orig$ ./configure
loading cache ./config.cache
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) no
checking for c++... (cached) c++
checking whether the C++ compiler (c++  ) works... yes
checking whether the C++ compiler (c++  ) is a cross-compiler... no
checking whether we are using GNU C++... (cached) yes
checking whether c++ accepts -g... (cached) no
checking for ranlib... (cached) ranlib
checking whether make sets ${MAKE}... (cached) yes
checking how to run the C++ preprocessor... (cached) c++ -E
checking for X... (cached) no
configuring zlib...
Checking for gcc...
Building static library libz.a version 1.1.4 with gcc.
Checking for unistd.h... Yes.
Checking for errno.h...	 Yes.
Checking for mmap support... Yes.
...done configuring zlib
checking for socklen_t... yes
creating ./config.status
creating Makefile
creating rdr/Makefile
creating rfb/Makefile
creating vncconnect/Makefile
creating vncpasswd/Makefile
creating vncviewer/Makefile
creating Xvnc/config/cf/vnclibs.def
steve@steve-laptop:~/downloads/vnc-3.3.7.orig$ make
make[1]: Entering directory `/home/steve/downloads/vnc-3.3.7.orig/zlib'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/steve/downloads/vnc-3.3.7.orig/zlib'
make[1]: Entering directory `/home/steve/downloads/vnc-3.3.7.orig/rdr'
make[1]: Leaving directory `/home/steve/downloads/vnc-3.3.7.orig/rdr'
make[1]: Entering directory `/home/steve/downloads/vnc-3.3.7.orig/rfb'
make[1]: Leaving directory `/home/steve/downloads/vnc-3.3.7.orig/rfb'
make[1]: Entering directory `/home/steve/downloads/vnc-3.3.7.orig/vncconnect'
make[1]: Leaving directory `/home/steve/downloads/vnc-3.3.7.orig/vncconnect'
make[1]: Entering directory `/home/steve/downloads/vnc-3.3.7.orig/vncpasswd'
make[1]: Leaving directory `/home/steve/downloads/vnc-3.3.7.orig/vncpasswd'
make[1]: Entering directory `/home/steve/downloads/vnc-3.3.7.orig/vncviewer'
gcc  -DX_DISPLAY_MISSING=1  -I.. -DVNC_SOCKLEN_T=socklen_t   -O2 -Wall  -c argsresources.c
In file included from argsresources.c:25:
vncviewer.h:30:28: error: X11/IntrinsicP.h: No such file or directory
vncviewer.h:31:28: error: X11/StringDefs.h: No such file or directory
vncviewer.h:32:23: error: X11/Shell.h: No such file or directory
vncviewer.h:36:28: error: X11/Xmu/StdSel.h: No such file or directory
In file included from argsresources.c:25:
vncviewer.h:60: error: expected specifier-qualifier-list before ‘Bool’
vncviewer.h:100: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘listenSpecified’
vncviewer.h:103: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cmdLineOptions’
vncviewer.h:107: error: expected ‘)’ before ‘w’
vncviewer.h:109: error: expected ‘)’ before ‘w’
vncviewer.h:111: error: expected ‘)’ before ‘w’
vncviewer.h:113: error: expected ‘)’ before ‘w’
vncviewer.h:115: error: expected ‘)’ before ‘w’
vncviewer.h:122: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cmap’
vncviewer.h:123: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
vncviewer.h:125: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘usingBGR233’
vncviewer.h:132: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘wmDeleteWindow’
vncviewer.h:133: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘form’
vncviewer.h:134: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘desktopWin’
vncviewer.h:135: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gc’
vncviewer.h:136: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘srcGC’
vncviewer.h:137: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘dpyWidth’
vncviewer.h:141: error: expected ‘)’ before ‘w’
vncviewer.h:148: error: expected ‘)’ before ‘w’
vncviewer.h:151: error: expected ‘)’ before ‘w’
vncviewer.h:157: error: expected ‘)’ before ‘w’
vncviewer.h:159: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘BumpScroll’
vncviewer.h:171: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘TimeFromEvent’
vncviewer.h:172: error: expected ‘)’ before ‘w’
vncviewer.h:174: error: expected ‘)’ before ‘w’
vncviewer.h:180: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘popup’
vncviewer.h:181: error: expected ‘)’ before ‘w’
vncviewer.h:183: error: expected ‘)’ before ‘w’
vncviewer.h:189: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘canUseCoRRE’
vncviewer.h:190: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘canUseHextile’
vncviewer.h:193: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘pendingFormatChange’
vncviewer.h:196: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘newServerCutText’
vncviewer.h:198: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘InitialiseRFBConnection’
vncviewer.h:199: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘SendSetPixelFormat’
vncviewer.h:200: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘SendSetEncodings’
vncviewer.h:202: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘CheckUpdateNeeded’
vncviewer.h:203: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘SendPointerEvent’
vncviewer.h:204: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘SendKeyEvent’
vncviewer.h:205: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘SendClientCutText’
vncviewer.h:206: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘HandleRFBServerMessage’
vncviewer.h:213: error: expected ‘)’ before ‘w’
vncviewer.h:215: error: expected ‘)’ before ‘w’
vncviewer.h:220: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
vncviewer.h:225: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sameMachine’
vncviewer.h:227: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ConnectToRFBServer’
vncviewer.h:228: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘SetRFBSock’
vncviewer.h:233: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ReadFromRFBServer’
vncviewer.h:234: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘WriteToRFBServer’
vncviewer.h:244: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘appContext’
vncviewer.h:245: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
vncviewer.h:246: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘toplevel’
vncviewer.h:250: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘zrleDecode’
argsresources.c:26:28: error: X11/Xaw/Toggle.h: No such file or directory
argsresources.c:148: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘appDataResourceList’
argsresources.c:222: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cmdLineOptions’
argsresources.c:237: warning: implicit declaration of function ‘XtNumber’
argsresources.c:237: error: ‘cmdLineOptions’ undeclared here (not in a function)
argsresources.c:237: error: initializer element is not constant
argsresources.c:244: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘actions’
argsresources.c: In function ‘GetArgsAndResources’:
argsresources.c:305: warning: implicit declaration of function ‘XtGetApplicationResources’
argsresources.c:305: error: ‘toplevel’ undeclared (first use in this function)
argsresources.c:305: error: (Each undeclared identifier is reported only once
argsresources.c:305: error: for each function it appears in.)
argsresources.c:305: error: ‘appDataResourceList’ undeclared (first use in this function)
argsresources.c:308: error: ‘AppData’ has no member named ‘encodingsString’
argsresources.c:308: error: ‘AppData’ has no member named ‘useBGR233’
argsresources.c:309: error: ‘AppData’ has no member named ‘autoDetect’
argsresources.c:309: error: ‘False’ undeclared (first use in this function)
argsresources.c:312: error: ‘AppData’ has no member named ‘autoDetect’
argsresources.c:313: error: ‘AppData’ has no member named ‘useBGR233’
argsresources.c:313: error: ‘True’ undeclared (first use in this function)
argsresources.c:319: warning: implicit declaration of function ‘XtAppAddActions’
argsresources.c:319: error: ‘appContext’ undeclared (first use in this function)
argsresources.c:319: error: ‘actions’ undeclared (first use in this function)
argsresources.c:326: error: ‘listenSpecified’ undeclared (first use in this function)
argsresources.c:337: error: ‘AppData’ has no member named ‘passwordDialog’
argsresources.c: At top level:
argsresources.c:373: error: expected ‘)’ before ‘w’
argsresources.c:377: error: expected ‘)’ before ‘w’
argsresources.c:381: error: expected ‘)’ before ‘w’
argsresources.c:390: error: expected ‘)’ before ‘w’
argsresources.c:405: error: expected ‘)’ before ‘w’
make[1]: *** [argsresources.o] Error 1
make[1]: Leaving directory `/home/steve/downloads/vnc-3.3.7.orig/vncviewer'
make: *** [all] Error 1

```

Also, I've tried what most here say works for them which is the:
```
steve@steve-laptop:~$ xtightvncviewer -encodings "hextile copyrect" -listen
xtightvncviewer -listen: Listening on port 5500
xtightvncviewer -listen: Command line errors are not reported until a connection comes in.
Connected to RFB server, using protocol version 3.8

```

As you see it shows connected and on the client says it says connected however their desktop never appears, not even a black window on my end. I know my single click file is about 1 and half old but I don't thing the single click is updated. So does anyone have a working solutions that works in 8.10. Or can anyone guide me in getting the vnc 3.3.7-orgin installed???


--Steve

---

### Post by moodog on 2009-03-12
> **appzattak said:**
> 
Also, I've tried what most here say works for them which is the:
```
steve@steve-laptop:~$ xtightvncviewer -encodings "hextile copyrect" -listen
xtightvncviewer -listen: Listening on port 5500
xtightvncviewer -listen: Command line errors are not reported until a connection comes in.
Connected to RFB server, using protocol version 3.8

```

As you see it shows connected and on the client says it says connected however their desktop never appears, not even a black window on my end. I know my single click file is about 1 and half old but I don't thing the single click is updated. So does anyone have a working solutions that works in 8.10. Or can anyone guide me in getting the vnc 3.3.7-orgin installed???


--Steve

I get the same as steve above - any recent updates to this? a pain that it used to work and now doesn't...

---

### Post by krunge on 2009-03-12
> **appzattak said:**
> 

Also, I've tried what most here say works for them which is the:
```
steve@steve-laptop:~$ xtightvncviewer -encodings "hextile copyrect" -listen
xtightvncviewer -listen: Listening on port 5500
xtightvncviewer -listen: Command line errors are not reported until a connection comes in.
Connected to RFB server, using protocol version 3.8

```

As you see it shows connected and on the client says it says connected however their desktop never appears, not even a black window on my end. I know my single click file is about 1 and half old but I don't thing the single click is updated. So does anyone have a working solutions that works in 8.10. Or can anyone guide me in getting the vnc 3.3.7-orgin installed???


--Steve

I've lost track, which VNC server are you using and what cmdline do you use and what messages does the VNC server print out?

For your compile problem, it looks like you are missing a build/dev package  , these headers are missing: X11/IntrinsicP.h, etc.

You could probably also download a non-debian/ubuntu vnc 3.3.7 package and it probably will run fine.

---

### Post by Boynas on 2009-08-26
Any new word on this???

I tried all this options, and it still doesn't work.

It works if they download say, Realvnc and invite me "add new client" style.

But SC doesn't work, tried with their latest and nothing. Tried disableing compiz... just to make sure that it wasn't a window problem... 

Still, the listener xvnc4viewer or xtightvncviewer they all show the connection as active, the client specifies that is active but no screen pops up.

---

### Post by jac0b on 2009-08-26
Try [teamviewer.com]("http://www.teamviewer.com") it works with ubuntu under wine.

---

### Post by mwildam on 2009-11-05
Tried the client exe yesterday on my upgraded notebook (from Jaunty 9.04 to karmic 9.10) under Wine and it did not come up.

---

### Post by bundabrg on 2009-11-12
Hi All,

Just wanted to say that under Karmic, I was able to get SC to work with SSVNC.

I used the following PPA to get it: -

```

deb http://ppa.launchpad.net/whoopie79/ppa/ubuntu karmic main 

```


Brendan

---

### Post by hengst on 2009-12-31
i Confirm that installing SSVNC as replacement for "vncviewer -listen" works ok with Karmic.
and solves the problems with getting the -listen mode for me at last. 

hell its even with a nice GUI and easy disabel/enable any option.

first add the reposite as mentioned. 

install ssvnc via terminal " sudo apt-get install ssvnc "

Thanks people, you helped me, hope i help another some . keep up the spirit

---

### Post by ld.4lpha on 2010-01-05
I can confirm that ssvnc is the only thing that seems to work on Jaunty with UltraVNC's SC on XP.

The other viewers accept the connection but do not bring up an interface to the remote machine.

---

### Post by ZarathustraDK on 2010-01-18
Question for the original How-to :

I'm trying to get this to work on a slightly bigger scale. I have multiple users who need support, a server that they can reverse-vnc to, and multiple supporters (as in "we each have our own workstation and can't physically access the server itself to remote-support the users").

I've gotten the reverse-vnc-part working, but only from the server. What would you do if, say, you were sitting on your own computer and wanted to connect to the server in order to get the vnc-connection to the user?

What would make it easy? I'm thinking something like this :
1. User clicks a "Help me"-script on their desktop.
2. Script asks for a server-side port-number, user is told a port-number from a range of portnumbers (there may be more people being supported at the same time) by the supporter.
3. User enters the portnumber and clicks ok. Reverse vnc-connection to the server is established.
4. Supporter does "**something**" from his computer and gets the customers vnc-feed.

I need to know what "**something**" is in this instance :)

---

### Post by michaelparez on 2010-01-18
Thanks for your guidelines it helped me a lot.

---

### Post by yodasoda on 2010-03-11
I have no problem using vncviewer -listen .   What I need help with is making it work the other way around ie with vncconnect or vncconfig.

---

### Post by Dan Stieneke on 2010-04-22
***SOLVED***

You can make your own single-click file using 7zip & RealVNC. It's not as pretty (it uses a text menu), but it works in approximately the same way as SCVNC.

Details at [https://bugs.launchpad.net/ubuntu/+source/tightvnc/+bug/123631/comments/23](https://bugs.launchpad.net/ubuntu/+source/tightvnc/+bug/123631/comments/23)

---

### Post by jakupl on 2010-06-06
You can altso install the ubuntu version of [teamviewer]("teamviewer.com"). It works well for me.

---

### Post by markp1989 on 2010-07-18
this is pretty cool. is there a way to use this with windows remote assistant, my friend keeps wanting my help using the remove assistant button in msn messenger,

---

### Post by nettobr on 2010-11-20
At last...

Now I can support my clients using my SC little Program Using Ubuntu 10.10.

And without rebooting in windoze...

Since Ubuntu 8 it was not working for me.

Thanks for all that helped in this topic.

The hint from bundabrg (#118) and hengst (#119) still works on Ubuntu 10.10 Maverick.


SSVNC is the Salvation.

Add this repository: 

deb [http://ppa.launchpad.net/whoopie79/ppa/ubuntu](http://ppa.launchpad.net/whoopie79/ppa/ubuntu) karmic main

install ssvnc via terminal " sudo apt-get install ssvnc "

---

### Post by nettobr on 2010-11-29
Helo friends,

Well, not that much...

SSVNC aborts in the middle of section.

UltraVNC is much better, but in Windoze.

Ciao

NettoBr

---

### Post by nshiell on 2010-12-20
Wow Reverse VNC is a real mess in the latest versions of Ubuntu
I just spent the last 4hours trying to get reverse VNC working.
And with ssvnc I got it (yay)
If anyone else has any probs plz ask in this thread so I/we can help

(I need a rest now, that was a nasty bug)

---

### Post by malapradej on 2013-03-25
This works for me too. 

xtightvncviewer -encodings "hextile copyrect" -listen

---

