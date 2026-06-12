---
title: "Secure Remote Access"
date: 2005-07-01
forum: Server Platforms
---

### Post by ano1 on 2005-07-01
I have recently been researching Remote (Desktop) Access applications, like VNC, NX terminal server. I realize that remotely controlling ones computer can be a security issue, expecially if the wrong person gains control of it. So my question to all you security experts is: 

In your opinion what is the most secure way to have remote GUI access of a Linux box? I am interested in remote access from another OS (mostly Windows, or linux) or possibly via a website. What software package(s) would you suggest and why? 

Thanks for sharing your expertise for us security newbies.

---

### Post by A-star on 2005-07-01
I use a ssh connection over which I run everything: vnc,nx and so on.
the ssh connection is encrypted from beginning to end so no one can tell what is going over it.

---

### Post by ano1 on 2005-07-06
Does anyone know aobut freeNX? I would like to know what seurity risks one truely has to worry about when using it (assuming it is proprly setup with SSH etc.).  Would SSH have to be setup on the client as well as the server for it to be truely secure? or is there no difference either way?

I guess we could broaden this question to be about any remote admin tool using SSH, what issue might arise, and what ways are there to detect and prevent unwanted intrusion? Thanks for the info.

---

### Post by dare2dreamer on 2005-07-06
NX is tunneled over ssh, so it's as secure as ssh is.

In the words of John Bloom, "Joe Bob says check it out." :-)

---

### Post by larry_smith on 2005-07-14
if you don't want to hassle with setting up VNC, [logmein](http://www.logmein.com) is another that works on the PC no matter what IP it's on (just like gotomypc) Auto-runs at startup, password protection, encryption, etc.  clean installation and interface.

---

### Post by ano1 on 2005-07-18
[QUOTE=larry_smith]if you don't want to hassle with setting up VNC, [logmein](http://www.logmein.com) is another that works on the PC no matter what IP it's on (just like gotomypc) Auto-runs at startup, password protection, encryption, etc.  clean installation and interface.[/QUOTE]

That is an interesting thought. However I want it to be free, that is why I like VNC and FreeNX. I noticed this service had a limited functionality free version Do you know of any others that are totally free? Thanks for the input.

---

### Post by larry_smith on 2005-07-18
logmein's trial version has the enhanced features--mostly file transfer.  (but there are ways around it) i like logmein better because it bypasses my work firewalls and is easier to install than VNC if you're using it to help a friend troubleshoot their comp. its competitors are mywebexpc, gotomypc and pcanywhere, but they are not free and don't work as well.  hope this helps!

---

### Post by Brylee on 2005-12-14
[RemotePC]("http://www.remotepc.com") has it’s entire communication between the computers encrypted using 128-bit RC4/SSL to ensure security during remote access and this is a high standard of encryption. They also have a web based access.

---

### Post by Joeak on 2005-12-14
Tunnelling through ssh is the way to go.  Learning to use the port forwarding to tunnel VNC or other traffic is worth the effort, and as secure as ssh is, which is as secure as it gets.  You do have to watch your logs for invalid connection attempts; I got alerted to one of those (by snort?) and decided to limit ssh connections to come only from my usual haunts (work).  If I go somewhere else and need to open up my home further, I can RDP into work, SSH into home, and open it up further.

---

### Post by airtonix on 2006-04-21
so on a reverse tip: how to setup a ssh server on windows? so that one can use vnc in a secure fashion? I ask, as the guys this i for wont switch to ubuntu, which if he did....this process would be damn simple.

@[larry_smith]("http://ubuntuforums.org/member.php?u=29912") : I wouldn;t recommend trustin your remote access to anyone but yourself dude, I say this because my friend (who loves windows), wanted to use this website...and i was like "Noooooooo"(diving to take the bullet).
 I wouldn't trust a third party with your login phrase. just imagine all those hacked credit card dbases gleaned for passwords.....

and yes you may say that you are not a threat or important enough to be hacked, but your computer presents some nice resources that can be  used in a massive attack on something else...nice to know you helped to bring down sydeny's nuclear power plant aie?

I think not.

gee if your even familiar with googledorks, then you know that there are heaps of exposed htaccess files out there....

i really dont like "easy". because it usually leads to "lazy". which then leads to "windows", which then leads to DRM, which then eventually leads to most people giving up their rights to the nearest dictator in return for a jam donut.

yeah gotta love the jam donuts!! lol

---

### Post by Joeak on 2006-05-06
(sorry for the mangled posting; if I could post attachments it would be neater)

Download the free versions of OpenSSH and RealVNC for Windows from [http://www.openssh.org](http://www.openssh.org) and [http://www.realvnc.com](http://www.realvnc.com).

FIREWALL ISSUE &#8211; The host machines you try to connect to must allow tcp port 22 connections from the machine(s) you use to connect to them.  At my office we use Windows AD Group Policy to punch firewall exceptions in our Windows XP SP2 machines&#8217; Windows firewalls (limited to subnets that our admins use).

A completely manual install lets you see all the options and make different selections, such as prompting the user to allow remote connections, locking the screen upon disconnect, etc.
&#8226;	log onto the machine at the console with local admin rights
&#8226;	For NT4 machines, download and run an updated Windows Installer &#8220;instmsiw.exe /q&#8221; on the client PC.
&#8226;	run setupssh-3.8.1.exe
&#8226;	De-select the Client and Start Menu Shortcuts options, leaving only Shared Tools and Server checked.
&#8226;	After it&#8217;s finished, as the Quickstart guide states open a command prompt and run the mkgroup and mkpasswd files:
&#8226;	The security files that determine who can connect have to be tweaked because they&#8217;re set up for my domain.  Since the # of domain groups may be large I limited it to the &#8220;domain users&#8221; group, which is what most users&#8217; default groups are.  Whatever users you add to the passwd file, their default group listed in the domain needs to be in the group file.
o	C:
o	Cd  &#8220;\program files\openssh\bin&#8221;
o	Mkgroup  &#8211;d | find &#8220;domain users&#8221; /i  >  ..\etc\group
o	Mkpasswd  &#8211;l  &#8211;u  jtspears  >  ..\etc\passwd    (first user)
o	Mkpasswd  &#8211;l  &#8211;u  jsjordan  >>  ..\etc\passwd    (append additional user(s))
o	&#8230;etc&#8230;

&#8226;	To set yours up to access it using the local administrator account instead of domain authentication do:
o	C:
o	Cd  &#8220;\program files\openssh\bin&#8221;
o	Mkgroup  &#8211;l  >  ..\etc\group    (group file must be populated for some reason.  &#8211;l is local groups)
o	Mkpasswd  &#8211;l  &#8211;u  administrator  >  ..\etc\passwd    (the local user you connect with)

&#8226;	Run vnc-4_1_1-x86_win32.exe
&#8226;	Check &#8220;Don&#8217;t create a Start Menu folder&#8221;
&#8226;	Check &#8220;Register VNC Server as a system service&#8221;.  DON&#8217;T START THE SERVICE YET.
&#8226;	Save the following as a *.reg file and run it; otherwise go through the VNC options pages to set them.  The DisableClose and DisableOptions settings are not available in the VNC gui, so if you want to disable the user&#8217;s ability to close the VNC icon in their system tray (which would stop the service) and the option to view and change the options, you&#8217;ll have to do a reg file anyway.

Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\RealVNC\WinVNC4]
"AcceptCutText"=dword:00000001
"AcceptKeyEvents"=dword:00000001
"AcceptPointerEvents"=dword:00000001
"AlwaysShared"=dword:00000001
"DisableClose"=dword:00000001
"DisableEffects"=dword:00000001
"DisableLocalInputs"=dword:00000000
"DisableOptions"=dword:00000001
"DisconnectAction"="None"
"DisconnectClients"=dword:00000000
"Hosts"="+,"
"HTTPPortNumber"=dword:00000000
"IdleTimeout"=dword:00000e10
"LocalHost"=dword:00000001
"NeverShared"=dword:00000000
"PollConsoleWindows"=dword:00000001
"PortNumber"=dword:0000170c
"Protocol3.3"=dword:00000001
"QueryConnect"=dword:00000000
"QueryOnlyIfLoggedOn"=dword:00000000
"RemovePattern"=dword:00000001
"RemoveWallpaper"=dword:00000001
"ReverseSecurityTypes"="None"
"SecurityTypes"="None"
"SendCutText"=dword:00000001
"UpdateMethod"=dword:00000001
"UseCaptureBlt"=dword:00000000
"UseHooks"=dword:00000001

&#8226;	Start the services (the package incorrectly doesn&#8217;t start them, although they&#8217;re set to automatic so a reboot would start them&#8230;if yours start, you may need to stop and start them):
o	Net stop opensshd
o	Net start opensshd
o	Net stop &#8220;vnc server version 4&#8221;
o	Net start &#8220;vnc server version 4&#8221;

USING THE SSH AND VNC SERVICES:

&#8226;	Download a recent version of putty.exe from [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) and put it in your path (c:\windows).
&#8226;	Download either the 3.x or 4.x version of vncviewer.exe from [http://www.realvnc.com](http://www.realvnc.com).  I use the 3.x version because it support screen scaling.  IIRC you have to download a whole 3.x or 4.x package and install it, but all you need is the vncviewer.exe.  Put it in your path (c:\windows).

The easy way to connect from your admin PC to remote control one of your user&#8217;s workstations is to obtain my svnc.cmd script and run it.  I will either put the text of that script at the bottom of this post, or I will post it separately as a code attachment.

Running the SVNC.CMD script eases the process of connecting to multiple machines.  It chooses one of 50 tcp ports to use for connections, verifying that the ports are available before using them.  It creates the ssh connection and tunnels the vnc connection through it automatically.  The current logged-on user has to be in the host pc&#8217;s passwd file to connect, or you can pass it an alternate userid that IS allowed to connect.
Syntax:	svnc.cmd  <computername>  [userid]
ex:	svnc.cmd  anc-07-15323L
ex:	svnc.cmd  anc-07-15323L  jtspears
ex:	svnc.cmd  anc-07-15323L  administrator

More info on how connections work and how to run them manually:

How SSH tunneling works can be confusing.  Ordinary programs like VNC or IIS running on a machine listening on whatever TCP or UDP port they&#8217;re written to listen on, in these cases VNC listens on port 5900 and IIS (http) listens on port 80.  Default connections for VNC over port 5900 are unencrypted, so my package or reg hacks shown above set VNC so that it won&#8217;t allow any machine other than itself to connect to itself.

When an administrator creates an SSH connection from their PC to the client PC and configures a secure tunnel for VNC purposes, the way it works is that SSH will &#8220;listen&#8221; on a port of your choice on your own machine, receive any packet sent to that port, encrypt it, and tunnel it through SSH to the client PC.  The client PC receives the encrypted packet and then &#8220;forwards&#8221; it to itself on whatever port you designate, in this case for VNC it&#8217;s port 5900.  So as far as VNC is concerned, the machine&#8217;s connection request is coming from itself.  If you have to do this a lot, you have to use multiple local ports on your own PC, with each port being forwarded to different client PC&#8217;s.

The svnc.cmd script allows you to easily connect to up to 50 remote machines without having to worry about which port is used for which PC.

To do the SSH and VNC commands manually:

&#8226;	plink -ssh -L 59xx:localhost:5900 -C -l <account> <pcname>     (where 59xx is an available port)

On your PC in a separate command prompt or Start, Run dialog:

&#8226;	vncviewer  localhost:59xx                (where xx is the same as the plink/ssh port being forwarded)

The version of vncviewer I use at work is still 3.3.7, because the RealVNC 4.x had the screen scaling ripped out of it.  They said it caused problems with some video adapters or something.  In our environment, the vncviewer 3.3.7 screen scaling works, so we&#8217;re using it.  VNC 3.x also uses an older version of the VNC protocol, so we set the options in the vnc 4.x host services to also use the older protocol, which speeds up connections.

---

### Post by Joeak on 2006-05-06
[QUOTE=Joeak]The easy way to connect from your admin PC to remote control one of your user’s workstations is to obtain my svnc.cmd script and run it.  I will either put the text of that script at the bottom of this post, or I will post it separately as a code attachment.

Running the SVNC.CMD script eases the process of connecting to multiple machines.  It chooses one of 50 tcp ports to use for connections, verifying that the ports are available before using them.  It creates the ssh connection and tunnels the vnc connection through it automatically.  The current logged-on user has to be in the host pc’s passwd file to connect, or you can pass it an alternate userid that IS allowed to connect.
Syntax:	svnc.cmd  <computername>  [userid]
ex:	svnc.cmd  anc-07-15323L
ex:	svnc.cmd  anc-07-15323L  jtspears
ex:	svnc.cmd  anc-07-15323L  administrator
[/QUOTE]

```
@echo off
:: svnc.cmd - mondo ssh-based vnc script
::
:: Joe's attempt to script an SSH connection, specifying an available
:: port redirected and launching VNC over that port with as little user
:: input as possible (hopefully just a password to connect).

setlocal

set xuser=%username%
if not x%2==x set xuser=%2

:: pick a localhost port to use for the tunnel
set xport=
call :pickxport

:: launch the putty window and prompt for a password
start "SSH to %1...this will close when the VNC session is ended" plink -ssh -L %xport%:localhost:5900 -C -l %xuser% %1 ping localhost -n 10

:: watch for the ssh tunnel and port forwarding to be established
set x=1
:top-wait
netstat -a -n | find "127.0.0.1:%xport%" | find "LISTENING" /i >nul
if not errorlevel 1 goto :start-vnc
if '%x%'=='30' goto :error
set /a x=x+1
ping loopback -n 2 -w 1000 >nul
goto :top-wait

:start-vnc
start %~dp0vncviewer /shared /8bit localhost:%xport%
goto :eof


:error
echo.
echo.  you have to enter a valid ssh password for the machine
echo.  you're connecting to within 30 seconds!
echo.
pause
goto :eof


:::::::::::::::::::::::::::::::::::
:pickxport
:: checks to see if ports are currently in use and picks one.
:: Default range is 5950-5999

set x=5950
set y=5999
if not '%1'=='' set x=%1
if not '%2'=='' set y=%2

:top-port
netstat -a -n | find "127.0.0.1:%x%" /i >nul
if errorlevel 1 goto :done
set /a x=x+1
if /i x leq y goto :top-port

:done
set xport=%x%
set x=
set y=
goto :eof

```

---

### Post by Joeak on 2006-05-06
Of course, if you're using a Linux admin workstation, instead of using a mondo script to choose a local port to route through and run separate programs to establish the secure tunnel and run vnc through it, you can just use the -via parameter built into vncviewer!

```
vncviewer -via <sshserver> -shared -8bit <vncpc>
vncviewer -via myserver.atwork.com -shared -8bit Joespc1
vncviewer -via Joespc1 -shared -8bit Joespc1

```

---

### Post by airtonix on 2006-05-23
wow, Joeak thats hardcore.

I think i will digest this and release a howto designed to appear in a walmart catalouge or a target catalouge....

Which will obviously be for windows users. lol

---

### Post by Joeak on 2006-05-25
I'm not sure if I included it in this thread, but I used Wininstall LE (the free version before they time-limited it) to build an MSI package to install both OpenSSH and RealVNC, and for my techs at work I gave them a button to push to install it remotely using a couple of scripts and PSEXEC.  Works great.  The only part that has to be tweaked for others to use it is to replace the passwd and group files with ID's that are valid on your/their systems.  For this forum I thought people would prefer to know how to do it.

---

### Post by LBailey on 2006-08-18
> **Joeak said:**
> Tunnelling through ssh is the way to go.  Learning to use the port forwarding to tunnel VNC or other traffic is worth the effort, and as secure as ssh is, which is as secure as it gets.  You do have to watch your logs for invalid connection attempts; I got alerted to one of those (by snort?) and decided to limit ssh connections to come only from my usual haunts (work).  If I go somewhere else and need to open up my home further, I can RDP into work, SSH into home, and open it up further.

I have set up my VNC tunnel, and all is fine. Problem is, I can still vnc without using the tunnel. How do I disable that? Is there somewhere I can set vnc to accept localhost only?

I have tried:
1) adding this line "only_from = 127.0.0.1" to /etc/xinetd.conf
2) adding "-localhost" to my arguments for the vnc service specified in /etc/xinetd.d/Xvnc

But these changes have no effect.

Also, how exactly did you limit the ssh connections to your known IPs? You've mentioned it twice in this thread, but no details. Would you mind sharing?

---

### Post by Aurelius on 2006-08-28
> **LBailey said:**
> I have set up my VNC tunnel, and all is fine. Problem is, I can still vnc without using the tunnel. How do I disable that? Is there somewhere I can set vnc to accept localhost only?

I have tried:
1) adding this line "only_from = 127.0.0.1" to /etc/xinetd.conf
2) adding "-localhost" to my arguments for the vnc service specified in /etc/xinetd.d/Xvnc

But these changes have no effect.


I am interested in this, too. If anyone can clue me in, I'd appreciate it.

Edit: Nevermind. Shutting off the VNC port at my router worked. I can now VNC in over SSH but VNC is not accessible without SSH.

---

### Post by LBailey on 2006-08-29
I don't have access to anything but my computer, so I ended up installing a software firewall instead and blocking all ports except 22. I used [http://rocky.molphys.leidenuniv.nl/](http://rocky.molphys.leidenuniv.nl/), if anyone else is interested:)

I also want to disable vnc for most of the user accounts - does anyone know how to do that?

---

### Post by Joeak on 2006-08-31
On linux, to allow vnc only from localhost (i.e. only tunnelled through ssh):

in /etc/hosts.allow, add a line "vnc:localhost" (without the quotes).

in /etc/hosts.deny, add a line "vnc:ALL except localhost".

I've also used firestarter, a firewall tweaking gui that will start the linux firewall and monitor connection attempts and see if there's anything else I need to allow.

---

### Post by sciwhiz007 on 2006-09-03
I have been having similar troubles with setting up VNC (vnc4server) over SSH in a pretty standard installation of Dapper. I have tried adding "vnc:localhost" and "vnc:ALL except localhost" to hosts.allow and hosts.deny, tried adding -localhost to the server_args in /etc/xinetd.d/Xvnc, and also tried adding "only_from = localhost" to /etc/xinetd.d/Xvnc. None of these methods seem to work.

This particular post in a mailing list seems to suggest that it might be an issue with xorg ignoring vnc options? [http://www.realvnc.com/pipermail/vnc-list/2005-April/050349.html](http://www.realvnc.com/pipermail/vnc-list/2005-April/050349.html)

I am not sure what I should do. VNC accepting connections from outside localhost sorta defeats the point of setting up an SSH tunnel.

---

### Post by breuerp on 2006-09-08
If you're wanting to securely VNC from a Windows client I'd recommend installing Cygwin on the windows box and adding the VNC and ssh modules to it.  Another option is to use a virtual linux machine (like Metropipe) on your windows box.

I usually carry Metropipe (based on DSL) on my thumbdrive.  Metropipe runs as a virtual machine inside of QEMU and already has VNCviewer and ssh built into it.

---

