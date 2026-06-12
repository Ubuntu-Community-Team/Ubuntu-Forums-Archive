---
title: "Freenx - help"
date: 2005-06-13
forum: Ubuntu Backports
---

### Post by supergrapeman on 2005-06-13
Hi dudes,

I installed freenx for hoary from backports, having read this great little article: [http://www.linuxjournal.com/article/8342](http://www.linuxjournal.com/article/8342)

The server appeared to install just fine.

On a winxp sp2 laptop I installed the latest windows nx client from nomachine.com. Installation went just fine. But when I try to connect to the ubuntu freenx server, the windows machine just pops up a window with the text "Host not found". On this window, there's a detail button. Clicking this reveals:

NX> 203 NXSSH running with pid: 3876
Warning: Identity file C:\PROGRA~1\NX does not exist.
nxssh: Client: no address associated with hostname.

I've taken a peek at the network traffic, and it doesn't look like the Windows nx client event attempts to communicate with the ubuntu freenx server, so this may well be a Windows nx client issue. If so, please hold the flames, apologies if this is off-topic.

I'm just stuck, and it would be cool if someone else has seen (and fixed?) this.  :)

---

### Post by supergrapeman on 2005-06-14
Bad form to reply to your own post, I know, but I've fixed this. Thought it worth posting, just in case s/one else hits this when trying to use the Windows client.

Fix was to uninstall, then install the windows client to a different place (!). On reinstall, I told it to install to c:\program files\nx. Thereafter all was sweetness and light, and I'm now typing this from the nx client on a windows machine, connecting thru to freenx on my ubuntu server.

Performance is whizzy. Will see what it's like over some mixed-rate DSL links soon, but so far it feels like this is an order of magintude faster than VNC  :)

---

