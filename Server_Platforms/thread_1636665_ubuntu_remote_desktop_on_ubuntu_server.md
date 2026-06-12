---
title: "ubuntu remote desktop on ubuntu server"
date: 2010-12-03
forum: Server Platforms
---

### Post by Helbo15 on 2010-12-03
Hi I've installed a ubuntu 10.10 server and added a desktop to it
I enabled the possibility of using remote desktop to it and it worked. however it is Very slow and almost impossible to use because of it.
so I started looking in to alternatives, found someone recommending the Freenx so I tried to install that, I couldn't it keept complaining about the repository I couldn't figure it out so I moved on and found out that I could download the NX from nomashine's homepage. well I did that and it installed nice and easy, so I went to my client a windows 7 client installed the required client and tried to connect to my server. it didn't work it keep making an error when I try to connect.
```
Error: The remote NX proxy closed the connection.
Error: Failure negotiating the session in stage '7'.
Error: Wrong version or invalid session authentication cookie.
```

I've tried various things to avoid that error now with no success.

so now I'm asking is there a easier way to make my remote desktop to my server fast and usable that doesn't require me to work with so many annoying things that the previously attempts have made me do. it's not cause I'm a total noob with ubuntu or servers I have a fair amount of knowledge using both linux server and clients, thou I am by no means an expert with linux. I just want it to work so I can move on with my home project of using a linux server with dhcp dns firewall remote desktop and virtualbox to run a windows 2008 server that will have both a web server and a printserver.  

What I have working right now is
DNS
DHCP
Firewall
slow remote desktop
virtualbox is installed but haven't installed windows server yet

or is there something I've missed when trying to set up the remote desktop so I have a easy and fast way to remote control my server . ? 

in advance thanks :)

---

### Post by arrrghhh on 2010-12-03
Ubuntu-server comes without a DE aka GUI.  So if you want one, install ubuntu-desktop, don't even bother with the server edition.

You can run VBoxHeadless, and have virtual machines with GUI's, while still having the host OS GUIless.

Again, there's no point in trying to fit a square peg in a round hole.  If you want a GUI, don't use the server edition.

---

### Post by Helbo15 on 2010-12-03
well thanks for that advice now I have server and the gui installed so that is not my problem :) and it works perfectly. I actually have everything up and running, I'm just looking for a better remote desktop that doesn't get me so annoyed with how slow it is and that is why I'm asking for help and explaining what I have done so far overall :)

---

### Post by HermanAB on 2010-12-03
Howdy,

VNC is mainly a Windows thing and it is pretty much a sure fire way to get your server hacked. There are many tales of woe on these forums about VNC.  

The best way to manage an Ubuntu server is with Webmin and SSH.  Ubuntu server comes with both.  If you install the Ubuntu server, then you don't need to run a GUI on the machine.

---

### Post by pricetech on 2010-12-03
NX from nomachine dot com has always just worked for me.

Different from FreeNX.

---

### Post by Helbo15 on 2010-12-03
about the gui I'm sorry but i need it not just to have the remote desktop but also to run virtualbox with a windows 2008 server inside. 

well I'm well aware that it puts my server at risk, but I don't see any real alternative, I am asking for a faster alternative not comments on my current setup, Everything is something I've decided to have after Careful consideration. 

the NX from Nomachine doesn't work(or I can't get it to work ;) ), the freenx wont even download.

the vnc is too slow. Are there really no alternative. ? 
are there something I can use as a terminal server instead ? 

Webmin is fine but not what I'm looking for.
and people saying that programs puts a server at risk from hackers, just connecting the server to the internet puts the server at risk so why do you need the connection to the internet? 

so my question still remains I want a way to connect to my server were I can control both the server and the virtualbox with the windows system inside it. and preferable similar to VNC just faster or similar to a terminal system.

---

### Post by arrrghhh on 2010-12-03
> **Helbo15 said:**
> about the gui I'm sorry but i need it not just to have the remote desktop but also to run virtualbox with a windows 2008 server inside.

I already said you can run VBoxHeadless... Did you not see that?

IMHO it's worth the extra effort, saves you overhead and unnecessary updates!

---

### Post by Helbo15 on 2010-12-03
> **arrrghhh said:**
> I already said you can run VBoxHeadless... Did you not see that?

IMHO it's worth the extra effort, saves you overhead and unnecessary updates!

I Saw it and responded to it, it is not what I need just because you like it to be like that doesn't mean I like it. I build my system to what it is now I'm asking for help to complete it not to change it.

I WANT it to have a GUI Stop suggesting changes to what already is WORKING. 

I also want remote desktop or Terminal server which ever is easiest to set up and maintain. 
just to make sure that people don't start talking about something I've already tried without success, I'm listing up what I didn't have any success with:

Freenx(Couldn't install it for some reason)
NX from homemachine(won't connect for some other reason)
ubuntu build in remote desktop(to slow)

and just to repeat myself, I want to be able to control the server from a windows computer.

---

### Post by CharlesA on 2010-12-03
> **Helbo15 said:**
> 
Freenx(Couldn't install it for some reason)
NX from homemachine(won't connect for some other reason)
ubuntu build in remote desktop(to slow)

and just to repeat myself, I want to be able to control the server from a windows computer.

I have installed FreeNX (From nomachine.com) on Ubuntu desktop with no problems. You do need openSSH-server installed, since that's what FreeNX uses as a transport protocol.

Sidenote: I've run Windows Server 2008 as a guest on my Ubuntu 10.04 box running headless. I just had to use remote desktop to access the guest.

---

### Post by Helbo15 on 2010-12-03
> **CharlesA said:**
> I have installed FreeNX (From nomachine.com) on Ubuntu desktop with no problems. You do need openSSH-server installed, since that's what FreeNX uses as a transport protocol.

Sidenote: I've run Windows Server 2008 as a guest on my Ubuntu 10.04 box running headless. I just had to use remote desktop to access the guest.

well do please explain me how I can install FreeNX

because the places I've tried so far have directed me to add some repository to my apt-get and then download it, they have all failed and I've added those repositories only to learn that they can't connect to those repositories, I already have openSSH-server installed.

and I know it's possible to run it headless people keep reminding me about it what do I need to say for people to stop saying it?

sorry CharlesA the next part is not minded on you in particular but all the people that are trying to come with good intentions suggestions that aren't even closely related to what I'm asking for :)

it is simply not my intention to run the server without a desktop gui. nothing people can say will change that fact. 

YES I know it will use more resources,
YES I know there will be a lot of unnecessary updates,
YES I know that it will open up the system for hackers

BUT I want a Desktop gui END OF STORY 

I have my own reasons as to why but I don't need to list them up here because it have nothing to do with what I'm asking help for.

---

### Post by CharlesA on 2010-12-03
If you already have ssh server installed, you would download the [Linux debs]("http://www.nomachine.com/select-package.php?os=linux&id=1") for whatever architecture you have i686 or x86_64 and install them with ***sudo dpkg -i somefile.deb***

Just a note: It would have been easier to just install Ubuntu Desktop instead of server if you wanted a GUI. Less stuff to download and mess with.

I've done that before and it's a whole lot easier then trying to cobble together a GUI on a server install.

---

### Post by Helbo15 on 2010-12-03
> **CharlesA said:**
> If you already have ssh server installed, you would download the [Linux debs]("http://www.nomachine.com/select-package.php?os=linux&id=1") for whatever architecture you have i686 or x86_64 and install them with ***sudo dpkg -i somefile.deb***

Just a note: It would have been easier to just install Ubuntu Desktop instead of server if you wanted a GUI. Less stuff to download and mess with.

I've done that before and it's a whole lot easier then trying to cobble together a GUI on a server install.

Thanks for that :) Well it seems I've mistaken that are what I Called NX from homemachine it seems I should had said nomachine ;) 

I have downloaded and it looks like it works But once I try and connect it comes up with the error I've described in my first post ;)

---

### Post by Helbo15 on 2010-12-03
and as a polite answer to your note. 

the server version installed without any thing to mess with the gui installed easily too I don't recall needing to mess with anything I wouldn't had needed to mess with anyway. had I just installed the desktop version I would had to install dhcp and bind and my samba server anyway so either way I would had to install and mess around with things :)

---

### Post by endotherm on 2010-12-03
did you completely purge freenx before installing the nomachine nx?
if not, purge both, and then reinstall whatever version you prefer. you may want to reinstall sshd on the way. worth a try.

---

### Post by Helbo15 on 2010-12-03
Thanks I'll try that, however i never got to install Freenx couldn't even download that without error. 

but I'll try your suggestion of purging the SSHD and the NX and then reinstalling them.

---

### Post by endotherm on 2010-12-03
Oh, did you add any repos for the freenx install? you may want to remove them before installing the non-free nx.

---

### Post by Helbo15 on 2010-12-03
yes I did add repositories for them but I didn't realize that I needed to remove them to get a correct install of the NX

---

### Post by endotherm on 2010-12-03
> **Helbo15 said:**
> yes I did add repositories for them but I didn't realize that I needed to remove them to get a correct install of the NX
you may not need to. just a hunch.

---

### Post by CharlesA on 2010-12-03
The only thing I've done when I installed the version from nomachine is this:

Download nxclient, nxnode, and nxserver for whatever architecure I am using (x86 or x64) and then run this from the folder I downloaded them to:

```
sudo dpkg -i nx*.deb
```

---

### Post by arrrghhh on 2010-12-03
Just for the record, to the OP we're just trying to help.  There's certain things that are common 'best practices', and just tryin to let you know what those are - especially when you're running a Windows VM that already has a great RDP client built-in.

No biggie tho, I always say use what works best for you - we just want you to be aware of what 'best practices' are in this situation - I know I would want to know, so we're letting you know :D

---

### Post by Helbo15 on 2010-12-04
> **arrrghhh said:**
> Just for the record, to the OP we're just trying to help.  There's certain things that are common 'best practices', and just tryin to let you know what those are - especially when you're running a Windows VM that already has a great RDP client built-in.

No biggie tho, I always say use what works best for you - we just want you to be aware of what 'best practices' are in this situation - I know I would want to know, so we're letting you know :D

yea I know that you are saying them with the best intentions :)

but I have before setting this system up and during the setup of this system made a conscious decision knowing full well what I lose compared to what I gain from getting a GUI. I am by no means a novice, neither with linux or windows, but I'm not an expert in linux, which also means the only things I'm really good for in linux are the things I can read about in well documented guides and best practices. and I have read tons of documents of the things I need I'm not one of those that does something half heartely, however I'm also making decisions based on what I need not what is best practices for similar things.

I'm gonna report back here if it works to remove the repositories and remove it all and reinstall it again. however I have to work today so it will be sometime this evening. :)

---

### Post by CharlesA on 2010-12-04
Good luck. :)

For the record: I've been using an install of Ubuntu desktop for my web development server and it works great. It would probably work fine for running virtual machines as well, if it wasn't a virtual machine itself.

---

### Post by Helbo15 on 2010-12-04
Well I removed all repositories and removed the opensshd-server and removed every NX client server and node. and after that I installed the openssh-server and client and then I installed the nx client node and server. Still same problem.```
Error: The remote NX proxy closed the connection.
Error: Failure negotiating the session in stage '7'.
Error: Wrong version or invalid session authentication cookie.
```
however there are a little progress now at least I can actually use the ssh to connect to the server. 

so any other suggestions how to either solve this problem or maybe try some other software that does something similar ?

---

### Post by endotherm on 2010-12-04
Its good that ssh is now working. without it there is little hope of nx. 
as for the stage 7 msg, there is an old bug related to that message but it is marked as closed.
[http://www.nomachine.com/tr/view.php?id=TR01D01264](http://www.nomachine.com/tr/view.php?id=TR01D01264)

this link says you should configure an option called "Enable SSL on all traffic" under "advanced options".  I don't know where that is, but can you find it?
[http://ubuntuforums.org/archive/index.php/t-303577.html](http://ubuntuforums.org/archive/index.php/t-303577.html)

also check your installation against this howto (post 2):
[http://ubuntuforums.org/showthread.php?t=204976](http://ubuntuforums.org/showthread.php?t=204976)

---

### Post by Helbo15 on 2010-12-04
> **endotherm said:**
> Its good that ssh is now working. without it there is little hope of nx. 
as for the stage 7 msg, there is an old bug related to that message but it is marked as closed.
[http://www.nomachine.com/tr/view.php?id=TR01D01264](http://www.nomachine.com/tr/view.php?id=TR01D01264)

this link says you should configure an option called "Enable SSL on all traffic" under "advanced options".  I don't know where that is, but can you find it?
[http://ubuntuforums.org/archive/index.php/t-303577.html](http://ubuntuforums.org/archive/index.php/t-303577.html)

also check your installation against this howto (post 2):
[http://ubuntuforums.org/showthread.php?t=204976](http://ubuntuforums.org/showthread.php?t=204976)

okay I've followed that howto now and it still doesn't work,

However when you said that about enable ssl on all traffic it got me thinking. 
So I tried a few various scenarios out. and this is what I found out.
if I disable my firewall.
And disable ssl encryption on all traffic both server side and client side I can actually make a connection to my server, so this is prof that it is working.

but once I set ssl on client side still with my firewall disabled i get the error described earlier.
So any good ideas of what might be wrong here ? obviously there is something wrong with the SSL but I have no idea of how to correct this.

---

### Post by endotherm on 2010-12-04
interesting. check this out:
[http://ubuntuforums.org/showthread.php?t=1522556](http://ubuntuforums.org/showthread.php?t=1522556)

it indicates that iptables was blocking the loopback connection from ssh to ssl. see if that works.

but that brings up an interesting question. why use ssl at all, since ssh is already in the mix? I don't know. prolly so you can route through ssh proxies and still maintain privacy from other users on the endpoint host.

---

### Post by Helbo15 on 2010-12-05
I've just checked my firewall and it allows the loop back already

And as said it was without firewall that I tested both with and without ssl so I doubt it can have an effect on it.

I think its more likely that there are something wrong with either the servers ssl setup or the clients ssl setup or both. 

I but I did check and try what you suggested without any improvements :(.

---

### Post by CharlesA on 2010-12-05
Best thing to do would probably be to export the VMs and start from scratch.

Or at least, try doing a clean install in a VM and then install nxclient/server/node and see if it works.

---

### Post by Helbo15 on 2010-12-05
> **CharlesA said:**
> Best thing to do would probably be to export the VMs and start from scratch.

Or at least, try doing a clean install in a VM and then install nxclient/server/node and see if it works.

considering that my dns server, DHCP server, Firewall with nat, samba server and virtualbox is already setup and working I'd be very sad if I'd had to start all over ;)

anyway I found some new information I'm still looking it through to figure out what it means to my inability to connect but I think it provides somewhat an explanation of what is happening when I fail to connect.
see my abilities with linux logging is Very limited but I found out how to get this out of the syslog :).

```
Dec  5 14:45:04 localhost NXSERVER-3.4.0-14[12498]: User 'X' logged in from 'xxx.xxx.xxx.xxx'. 'NXLogin::set'
Dec  5 14:45:04 localhost NXSERVER-3.4.0-14[12498]: Selected node host:localhost with port:22 'main::selectNode'
Dec  5 14:45:04 localhost NXSERVER-3.4.0-14[12498]: Current selected node: localhost is in status: running  'main::selectNode'
Dec  5 14:45:04 localhost NXSERVER-3.4.0-14[12498]: Selected session type: unix-gnome allowed in the profile of user: X 'NXShell::Static'
Dec  5 14:45:06 localhost NXSERVER-3.4.0-14[12498]: ERROR: nxssh process exited with '255' 'NXNodeExec::exec'
Dec  5 14:45:08 localhost NXSERVER-3.4.0-14[12498]: A valid NX Server public SSH key is missing on the node. '(eval)'
Dec  5 14:45:10 localhost NXSERVER-3.4.0-14[12498]: Session '4B5295066466C2C06F4F2D2B1DE2CCF1' started by user 'X'. 'NXShell::handler_session_start'
Dec  5 14:45:10 localhost NXSERVER-3.4.0-14[12498]: ERROR: run command: no child process with pid 12547 Logger::log nxserver 3127
Dec  5 14:45:10 localhost NXSERVER-3.4.0-14[12498]: User 'X' from 'xxx.xxx.xxx.xxx' logged out. 'NXLogin::reset'
Dec  5 14:45:10 localhost NXNODE-3.4.0-14[12666]: Using port '1012' on node 'localhost' for session 'unix-gnome'. Logger::log nxnode 6244
Dec  5 14:45:10 localhost NXNODE-3.4.0-14[12666]: Using host from available host list: 'xxx.xxx.xxx.xxx'. Logger::log nxnode 6245
Dec  5 14:45:30 localhost NXSERVER-3.4.0-14[12498]: ERROR: nxssh process exit with exit status: 255 and flag connected set to: [0] 'NXShell::handler_bye'
Dec  5 14:45:30 localhost NXSERVER-3.4.0-14[12498]: ERROR: Cannot establish ssh tunnel between nxserver and nxnode 'NXShell::handler_bye'
Dec  5 14:45:30 localhost NXSERVER-3.4.0-14[12498]: ERROR: Please check permissions of user's home directory on the 'NXShell::handler_bye'
Dec  5 14:45:30 localhost NXSERVER-3.4.0-14[12498]: ERROR: node host and file name for authorized keys set in the NX 'NXShell::handler_bye'
Dec  5 14:45:30 localhost NXSERVER-3.4.0-14[12498]: ERROR: node and SSHD configurations. 'NXShell::handler_bye'

```

---

### Post by CharlesA on 2010-12-05
It looks like there's something wrong with nxserver, but you already removed it and whatnot, right?

---

### Post by Helbo15 on 2010-12-05
> **CharlesA said:**
> It looks like there's something wrong with nxserver, but you already removed it and whatnot, right?

I removed it and installed the suggested which was the free version of the NX Server. so this was the result of looking through the syslog right after a failed connect to the NXserver

---

### Post by CharlesA on 2010-12-05
Something is causing a problem. You said that if you flush the firewall rules, you are able to connect?

---

### Post by HermanAB on 2010-12-05
Well, once you got SSH working, you don't really need anything else. Try this:
$ ssh -C -c blowfish -X user@server gnome-panel

and go click happy.

---

### Post by Helbo15 on 2010-12-05
> **CharlesA said:**
> Something is causing a problem. You said that if you flush the firewall rules, you are able to connect?

yes But only if I also disable SSL in the server and client.

---

### Post by Helbo15 on 2010-12-05
> **HermanAB said:**
> Well, once you got SSH working, you don't really need anything else. Try this:
$ ssh -C -c blowfish -X user@server gnome-panel

and go click happy.

well tried that command right now and it doesn't seem to work for me, beside even thou I do have a linux client I mostly use my windows client and then i wouldn't be able to use that command anyway ;)

---

### Post by CharlesA on 2010-12-05
> **Helbo15 said:**
> yes But only if I also disable SSL in the server and client.

SSL on the NX server and client?

> **Helbo15 said:**
> well tried that command right now and it doesn't seem to work for me, beside even thou I do have a linux client I mostly use my windows client and then i wouldn't be able to use that command anyway ;)

You could use Putty and XMing, or something similar. That's what I use when I need to use a Windows box to connect via SSH.

---

### Post by HermanAB on 2010-12-05
Cygwin

---

### Post by CharlesA on 2010-12-05
> **HermanAB said:**
> Cygwin

+1 to that too. Makes it easier to deal with Linux stuff on a Windows box. :)

---

### Post by Helbo15 on 2010-12-05
do I get a gui out of those options ? 

what I want is something similar to remote desktop or terminal clients with and without admin rights

---

### Post by Helbo15 on 2010-12-05
> **CharlesA said:**
> SSL on the NX server and client?


what I mean is that in the nx server there is an option to 

in the server
EnableUnencryptedSession

1 = allow connections without SSL on all connections
0 = disallow connctions without ssl on all connctions

and in the client there is and option regarding the same.

if I allow connctions without ssl on all connections it works.
if I disallow it doesn't work

---

### Post by CharlesA on 2010-12-05
I saw something in the settings that said "disable encryption on all traffic" but didn't see anything that mentioned SSL.

---

### Post by Helbo15 on 2010-12-05
> **CharlesA said:**
> I saw something in the settings that said "disable encryption on all traffic" but didn't see anything that mentioned SSL.
well I read in the server.cfg

and it says```

# Enable or disable SSL encryption of all traffic.
#
#
# 1: Enabled. Unencrypted connections between the proxies will
#    be allowed.
#
# 0: Disabled. Forbid the use of unencrypted connections. The
#    server will force the client to tunnel the proxy
#    connections over the encrypted channel.
#
# Session negotiation always happens across an encrypted channel.
# Normally the user can specify if subsequent communication must
# take place through a direct connection between the proxies or by
# tunneling it through SSH. You may uncomment the following line
# and set the value to 0 to increase the security of the host
# server or if your NX server is behind a firewall preventing
# the access to the set of ports used by the NX server.
#
# Unencrypted sessions require that the firewall lets the proxies
# communicate over the TCP ports ranging from:
#
# DisplayBase + 4000
#
# to:
#
# DisplayBase + 4000 + DisplayLimit
#
# By default the user is allowed to specify if a session will run
# unencrypted, for example when running the session across the
# same LAN or when performance is an issue.
#

```

I just assumed that that line in the client meant the same :)

---

### Post by CharlesA on 2010-12-05
Ah, I wasn't looking in server.cfg.

It's interesting that it works if you turn off SSL.

EDIT: Checked server.cfg and it was commented out with "#":
```
#EnableUnencryptedSession = "1"
```

---

### Post by Helbo15 on 2010-12-05
> **CharlesA said:**
> Ah, I wasn't looking in server.cfg.

It's interesting that it works if you turn off SSL.

EDIT: Checked server.cfg and it was commented out with "#":
```
#EnableUnencryptedSession = "1"
```

yea it was but when it's commented out it is the same as saying that the standard value applies and the standard value is the same value as the commented out part shows so if you want it otherwise you have to change that part :)

---

### Post by CharlesA on 2010-12-05
> **Helbo15 said:**
> yea it was but when it's commented out it is the same as saying that the standard value applies and the standard value is the same value as the commented out part shows so if you want it otherwise you have to change that part :)
Gotcha. :)

It's still puzzling.

---

### Post by Helbo15 on 2010-12-05
yea it is :( well I'm almost about to remove it and just use the ssh and then maybe setup some terminal server in windows server it doesn't give me what I want but at least I can have some control of the windows system running inside it then :(

---

### Post by CharlesA on 2010-12-05
> **Helbo15 said:**
> yea it is :( well I'm almost about to remove it and just use the ssh and then maybe setup some terminal server in windows server it doesn't give me what I want but at least I can have some control of the windows system running inside it then :(
You can login to the Windows server via RDP without having to set up terminal services - just enable remote desktop and login as the administrator.

Also: If you are using the non-free version of VirtualBox, you can connect using VRDP.

---

### Post by Helbo15 on 2010-12-05
> **CharlesA said:**
> You can login to the Windows server via RDP without having to set up terminal services - just enable remote desktop and login as the administrator.

Also: If you are using the non-free version of VirtualBox, you can connect using VRDP.

yea I know that :)

it's just my intention was to remote to the linux server and do whatever I needed to do from there.
Also I wanted to add a user with no rights so I could use it as a terminal for the internet so when I don't play games I could use a linux as my portal to the internet ;).

---

### Post by CharlesA on 2010-12-05
> **Helbo15 said:**
> yea I know that :)

it's just my intention was to remote to the linux server and do whatever I needed to do from there.
Also I wanted to add a user with no rights so I could use it as a terminal for the internet so when I don't play games I could use a linux as my portal to the internet ;).
I just use my normal user for browing the interwebs.

---

### Post by Helbo15 on 2010-12-05
> **CharlesA said:**
> I just use my normal user for browing the interwebs.

well I guess it requires a little information to explain this ;)

my setup is 

linux server

around 5 windows clients 

the only reason to have windows is playing games. 
so my idea was to keep using windows but no matter which of the windows I was on I could then log on to the terminal and then have all my internet and office programs with their setup. and the view would had been the same for no matter which client I'm logged on to. :) and I would had preferred that terminal to be a linux server, then on top of that my idea evolved in to that I could control the server the same way.

---

### Post by CharlesA on 2010-12-05
I see. That makes sense then. You can still use the normal user on the server to browse the internet without any problems. Altho, I'd suggest still using stuff like AppArmor and NoScript any time you are using yer browser.

---

### Post by Helbo15 on 2010-12-05
> **CharlesA said:**
> I see. That makes sense then. You can still use the normal user on the server to browse the internet without any problems. Altho, I'd suggest still using stuff like AppArmor and NoScript any time you are using yer browser.

yea I know that :) but seeing as the only remote desktop I can get to work is the systems own remote desktop and it's slow as hell and I can't use it when it's that slow, ;) 

the nx only works if I change my firewall and allow it to be without ssl, which turns down my security :) more than I had hoped.

so now I'm back to square one ;) but I guess I should just forget about it, thou it makes the desktop on the server unnecessary.

---

### Post by endotherm on 2010-12-05
> **Helbo15 said:**
> yea I know that :) but seeing as the only remote desktop I can get to work is the systems own remote desktop and it's slow as hell and I can't use it when it's that slow, ;) 

the nx only works if I change my firewall and allow it to be without ssl, which turns down my security :) more than I had hoped.

so now I'm back to square one ;) but I guess I should just forget about it, thou it makes the desktop on the server unnecessary.
well if it is your firewall mucking things up, are there any log entries about the packets being blocked? perhaps allowing them is the best bet.

---

### Post by Helbo15 on 2010-12-06
> **endotherm said:**
> well if it is your firewall mucking things up, are there any log entries about the packets being blocked? perhaps allowing them is the best bet.

it's not my firewall it's the SSL, But if I change the NX to allow the NX to run without SSL then I need to change the firewall :) and I know how it's just annoying cause it means less security

---

