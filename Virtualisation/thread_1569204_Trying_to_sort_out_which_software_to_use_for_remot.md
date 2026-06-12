---
title: "Trying to sort out which software to use for remoting clients in"
date: 2010-09-06
forum: Virtualisation
---

### Post by bdemers on 2010-09-06
I don't understand the differences between vnc and rpc. Would someone be kind enough to enlighten me, please?  I believe that ms uses rpc for terminal services.  Will linux terminal services work just as well with vnc?
Understanding the differences will help me decide which virtual software to use.

---

### Post by TheFu on 2010-09-06
"rpc" is Remote Procedure Call [http://en.wikipedia.org/wiki/Remote_procedure_call](http://en.wikipedia.org/wiki/Remote_procedure_call) - a very low level way for applications running on different machines to communicate. Perhaps you meant to say "RDP" - Remote Desktop Protocol [http://en.wikipedia.org/wiki/Remote_Desktop_Protocol](http://en.wikipedia.org/wiki/Remote_Desktop_Protocol) which is used mainly by Microsoft, but others do as well. In Vista or Win7, MS added more security to RDP and broke most of the free implementations, unless you force the RDP server to allow insecure connections.  Further, RDP is not included in MS-Windows-Home versions (look for Remote Desktop in the help on Professional or greater versions).

VNC is a remote desktop protocol created by AT&T Labs. There are multiple implementations each with pros/cons. To my knowledge, they are all interchangeable and work with each others' servers.  VNC is the free alternative and used extensively on Linux systems and for virtual server access.

Both VNC and RDP are used for remote desktops. If you just want to run a remote application, perhaps using the built-in X/Windows remote display would suffice?  X-protocol is not secure, but neither are RDP or VNC protocols. However, X can be trivially tunneled thru an ssh connection:
$ ssh -X user@server program-to-run

The sshd on the server must be configured to all X-Forwarding.  This method is secure.

If you truly want a remote desktop and you are in a mixed environment, then VNC is the easiest to use. Personally, I believe that RDP is a little more network efficient than VNC and it seems to do a better job following the mouse pointer, IMHO. 

The NX protocol, (FreeNX) [http://en.wikipedia.org/wiki/Freenx](http://en.wikipedia.org/wiki/Freenx) gets high marks for being much more efficient than either RDP or VNC **AND** it includes encryption.  Here's a FreeNX guide from Ubuntu [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)  - I just followed it and have a remote desktop working over the WAN using my own ssh-keys (not the NX generated keys). It took about 10 minutes to get everything setup and working following the ubuntu guide. I used the FreeNX server and qtnx client.

99% of the time, I use `ssh -X` to remotely start remote applications and have them displayed on my current machine. It works best over a LAN, but I've used it over 14.4Kbps dial up links too.  Having an entire "remote desktop" seems like overkill to me, but I'm very comfortable on a shell prompt.

If you are looking for multimedia display + sound over any of these links, I think you'll want a specialized client, perhaps from Citrix, but for standard office productivity applications, any of the methods will work fine.

After you look at them all, your opinion would be useful and appreciated.

---

### Post by hasafraker on 2010-09-15
@TheFu  thanks for that explanation, I've been trying to rdp into my ubuntu box at home from my win7 box and nothing works. I tested it this morning from an XP box and it works like a champ, so I was pretty sure MS in their infinite wisdom broke something, sure enough. 

I may continue messing with it but I have setup FreeNX before and that works wonderfully, just a bit more effort is involved is all, and since rdp was already installed I figured I'd try that first. I may have to just setup FreeNX on this box and use that.

thanks again for the info re: win7 rdp changes at least I know it's not something I did wrong heh

---

### Post by TheFu on 2010-09-16
> **hasafraker said:**
> @TheFu  thanks for that explanation, I've been trying to rdp into my ubuntu box at home from my win7 box and nothing works. I tested it this morning from an XP box and it works like a champ, so I was pretty sure MS in their infinite wisdom broke something, sure enough. 

I avoid RDP except "into" Windows machines. I prefer pretty much any FLOSS over RDP going "into" UNIX/Linux machines.

Again - 99% of the time I use ssh.

---

