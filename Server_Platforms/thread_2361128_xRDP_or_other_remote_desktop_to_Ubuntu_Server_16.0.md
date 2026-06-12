---
title: "xRDP or other remote desktop to Ubuntu Server 16.04 LTS hosted in Azure"
date: 2017-05-12
forum: Server Platforms
---

### Post by tankbyu on 2017-05-12
I have Ubuntu Server 16.04 LTS hosted in Azure. When I try connecting  with RDP I get a grey screen and then it disconnects. I read on another  forum that this could be due to a problem with the Unity desktop so I  installed Mate with the following modification to the  /etc/xrdp/startwm.sh file:

[COLOR=#222222][FONT=Verdana]#!/bin/sh[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]if [ -r /etc/default/locale ]; then[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]  . /etc/default/locale[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]  export LANG LANGUAGE[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]fi[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]. /etc/X11/Xsession[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]fi[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]#use the mate desktop[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]mate-session[/FONT][/COLOR]

Perhaps there is a problem with the Bash script above? Are the fi tags correct or do I need an "else?"

Another  issue could be with the way Azure now does resource groups instead of  the "classic" mode. There are not endpoints that I could see to  configure open ports so I configured them within my network security  group as shown in the attached image.
[ATTACH=CONFIG]275077[/ATTACH]

Any help would be appreciated.

Thank you.

---

### Post by TheFu on 2017-05-12
I hope you are using a full VPN with RDP/VNC.

Cannot help with the method you are trying to use. Sorry.

However ... if you are willing, NX is a fast, remote desktop protocol that doesn't require trusting some 3rd party.

Setup ssh first.  Get that working.
Next, install either lxde or xfce for the best remote desktop support, assuming you even want a desktop.
Next purge Unity and Mate. Don't need the bloat, right? Mate might work, but I know lxde and xfce work great.
Next install x2go.  This uses the NX protocol, which is about 2-3x faster than VNC or RDP methods.  It works over ssh, so no other ports need to be opened or secured.  Normal ssh authentication is used too, so you shouldn't use passwords, just ssh-keys for authentication.
There are x2go clients for the main 3 desktops - Windows, Linux, OSX.

x2go works well from 10 inches away or 15K miles away.  You can tune the image compression as needed based on the network bandwidth available.

I wouldn't run ssh on the standard port. It will be constantly attacked there. Move it somewhere else - a very high port and setup fail2ban or denyhosts to block the brute force attackers for a week at a time (or forever).  It would be smarter to only allow ssh connections from the exact, specific, IPs from which you will connect.  At least block all the countries you will never connect from. 

Oh, and yes, your script needs lots of help.  On my ubuntu systems, the LANG stuff isn't needed and exporting LANG would trash what was setup in the locale script, so that makes no sense.

For more details about x2go, a google search will find their website. Just follow those instructions.  Basically comes down to 
* get ssh working, secure it as normal
* use LXDE (that's the default, easy to use desktop, with correct keyboard mappings)
* Setup the x2go PPA for the client and server systems. 
* Install the server on the server
* Install the client on the client
* If Windows is the client, install the full-font package.
* Run the client, disable printing and audio and file sharing to start. If you used the non-standard ssh port, use that for the x2go connection.\
* If you aren't in the same city as the Azure data center, turn up the image compression and turn down the image sizes. Play with those settings, for productivity apps, you really can compress a bunch without noticing it.

Don't expect video playback to work over the internet. There are other solutions for that. Spreadsheets, code stuff, standard non-video/non-audio stuff works well.

---

### Post by wildmanne39 on 2017-05-12
*Thread moved to **Server Platforms**.*

---

