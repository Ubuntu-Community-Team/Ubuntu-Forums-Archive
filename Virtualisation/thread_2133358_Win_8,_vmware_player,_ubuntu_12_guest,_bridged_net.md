---
title: "Win 8, vmware player, ubuntu 12 guest, bridged network/PORT 80 NOT ACCESSIBLE/WHY?"
date: 2013-04-07
forum: Virtualisation
---

### Post by gsmi on 2013-04-07
Hi,
First time I make this install, trying to start a web server, as many others. I'm a straight to the point guy, so:

After installing vmware player, had issues and cannot install vmware tools on ubuntu. I guess I can live with that.

Installed, tried both NAT and bridged, hell, even tried a bridge from windows, with linux in NAT mode. Anyways, right now I'm bridged, my router assigns static addresses to both win(.72) and ubuntu(.70).

Installed the server (apache, php, mysql). I can see the test web page on local ubuntu IP .70. When I try to go on the router wan IP, does not work. Even testing with [http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/) tells me port 80 is closed. Forwarding is done properly on the router. If I do the forwarding towards win .72, everything works fine, port 80 works, my win server works, local or wan IP. On ubuntu, same setup, same forwarding, doesn't. I must be missing something, don't know what.

Tried google for about two days now, no answer.

PLS HELP! Thanks :).

---

### Post by gsmi on 2013-04-07
Update - this is what I have:

netstat -an | grep "LISTEN "
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN

---

### Post by dcstar on 2013-04-08
> **gsmi said:**
> Hi,
First time I make this install, trying to start a web server, as many others. I'm a straight to the point guy, so:

After installing vmware player, had issues and cannot install vmware tools on ubuntu. I guess I can live with that.

Installed, tried both NAT and bridged, hell, even tried a bridge from windows, with linux in NAT mode. Anyways, right now I'm bridged, my router assigns static addresses to both win(.72) and ubuntu(.70).

Installed the server (apache, php, mysql). I can see the test web page on local ubuntu IP .70. When I try to go on the router wan IP, does not work. Even testing with [http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/) tells me port 80 is closed. Forwarding is done properly on the router. If I do the forwarding towards win .72, everything works fine, port 80 works, my win server works, local or wan IP. On ubuntu, same setup, same forwarding, doesn't. I must be missing something, don't know what.

Tried google for about two days now, no answer.

PLS HELP! Thanks :).

[http://ubuntuforums.org/showthread.php?t=1944290](http://ubuntuforums.org/showthread.php?t=1944290)

---

### Post by gsmi on 2013-04-16
Well, tried as many things as I could and as I was able to find and make sense on the internet, even installed VirtualBox with Ubuntu. Same no port 80 forwarding (on box as vmware player). Port forwarding works excellent on my Win apache web server (host)... right now I don't know if to blame the router USA-ATT-2wire, or my neurons not being capable to forward a port!

I'll keep playing with port forwarding in vbox see if I can come up with something.

LE: actually it's bridged, not NAT, so no port forwarding...

---

### Post by gsmi on 2013-04-16
And YES, I have WIRELESS!!

As I see here:
[http://www.virtualbox.org/manual/ch06.html#natforward](http://www.virtualbox.org/manual/ch06.html#natforward)
in case of a wireless network adapter, the situation seems to be different, and I don't really know how to configure it. I'll check, see if I can find an answer. Somebody else MUST have had the same issue and talked about it :). Will post if I find a solution.

---

### Post by Trakwup on 2013-05-29
Hello,

After much frustration, experimentation, and searching, I came across this post which would appear to fairly accurately describe the same issue that I am currently experiencing. Note that I am a complete Ubuntu beginner, however in this case I believe that I have done much of my due diligence in running the appropriate tests.

Like OP, I have Ubuntu 12.04 running in a VM through VMWare Player on a Win7 workstation. Windows Firewall is disabled on the host, and I've tried with ufw configured as intended as well as completely disabled in the guest with no difference. In my case the application I'm trying to run is transmission-daemon, which creates a Web interface on port 9091 (by default). That page and port is completely accessible from within the home network (e.g., 192.168.x.x), but with port-forwarding enabled, I am unable to access the page externally. I know that port-forwarding is working correctly, as I can forward successfully to another host in my environment. Moreover, if I enable port-forwarding to one of the Win7 default ports (e.g., 135), I can connect to said port on the host machine without problem.

I did come across some posts that suggested that attempting this via WiFi could be causing an issue, so at the moment I've connected via a wired line (well, technically I've connected via wire to a Wireless Bridge), but that has not made a difference. I could try connecting via wire directly to the router to see if that makes a difference.

Everything I've configured thus far has been using bridged networking; I've not yet tried to accomplish this via NAT. In fact, per this article:
  [http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1004813](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1004813)
I've currently disabled VMNet1 and VMNet8 on the host.

The post that dcstar linked to above is interesting, but would appear to be very specific to Apache hence not applicable to me.

Any tips or advice would be greatly appreciated.

---

