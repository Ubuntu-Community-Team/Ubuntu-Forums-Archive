---
title: "OpenVPN sloooow when windows is used"
date: 2010-05-16
forum: Server Platforms
---

### Post by toshko3 on 2010-05-16
I have many openvpn implementations. Every time I use windows shares over openvpn, the speed is no more than 500KB/s, in LAN environment. When I start a copy it reaches 200-300KB/s, when I start second one it reaches 500KB/s. No more is reached after more copies simultaneously. When I use linux to copy files - the first copy reaches 700KB/s, the second copy reaches 2.5MB/s (then the first grows also to 2.5MB/s), the third copy reaches also 2.5MB/s. All of these are copied simultaneously, otherwise when only one is started it sits on 700KB/s. Moreover when 2 of the 3 simultaneous copy processes end, the one left backs at 700KB/s again.
But this is linux. When I use Windows the transfer speed is no more than 400-500KB/s (LAN environment).
The OpenVPN server is always ubuntu (any version - I've tried 6.06, 8.04, 10.04).
Tried the OpenVPN client in ubuntu (and the windows machine behind the ubuntu), in windows (directly installed the client on windows) and it is all the same - no more than 500KB/s.
I can not use this because it is so slooow. When only one file is copied at a time it reaches only 200KB/s!!! Searched all the google results - no one have an answer, although there are many people with the same problem.
Now, I am sure that the problem is in Windows, because when I use linux as a server and as a client, the client copies fast. But when I use windows as machine behind the client it copies slow. I don't know... something in the tcp/ip settings in windows or something...
HEEELP, please, I can't resolve the problem for years now!

---

### Post by toshko3 on 2010-05-19
UPDATE: I tested a little more and it turns out that the problem is only when WIndows XP is used. No matter whether is the VPN (the TAP adapter driver) installed on the Windows machine or the Windows is behind the OpenVPN client/server (ubuntu). So I assume the problem is not in the TAP driver, but something in the traffic of Windows XP is shitting over.
:-k

---

### Post by toshko3 on 2010-06-02
anyone?

---

### Post by spynappels on 2010-06-02
Have you tried a different type of deployment where you use routing mode and use tun adaptors? I have had no difficulties with any Windows client in this config. Of course if you have services which rely on broadcasts etc, this may not work for you, but otherwise it may be an option.

Just remember to push routes to the home LAN and keep it on a relatively uncommon subnet.

---

### Post by toshko3 on 2010-06-04
Yes. I have tried tun, tap, udp, no compression, with compression. No difference! And this is not in one environment - every office that i've build. Vista and Win7 have no problem. So strange! :(
Thanks for the answer!

---

### Post by toshko3 on 2010-06-04
If anyone have tested the speed and it is over 500KB-1MB - I'll be very interested in the config files he uses and the architecture of the implementation.

---

### Post by HermanAB on 2010-06-04
I tend to think that MS deliberately messed with the XP network stack in order to promote Win2000 and Win2003.

---

### Post by Castorpoluks on 2010-06-05
Hmm problem is very odd. Did you try to contact live chat support of Open VPN?
I am using VPN with win7 and XP and it works perfect for me.

---

### Post by toshko3 on 2010-06-07
I didn't try to contact the OpenVPN support because I thought that it is not free. Am I wrong?

---

### Post by uberlinuxnerd on 2010-06-07
Check DNS settings... You really want the OpenVPN to push its DNS server down to the client.

---

### Post by toshko3 on 2010-06-07
I don't want, because they use their own internet, which is variable. But I think the DNS doesn't count because I test it with IP directly and moreover it's the traffic speed that is the problem, not the access. Thanks for the suggestion!

---

### Post by toshko3 on 2010-06-15
:confused:

---

### Post by toshko3 on 2010-07-09
Anyone?

---

### Post by thatitguy on 2010-09-19
I'm seeing exactly the same behaviour here.  No matter the configuration I try, my OpenVPN throughput is limited to 1MBps.

My setup:
Windows Vista 32bit laptop (or dual-booted in Ubuntu - the issue exists regardless of OS of client system) ->
54G Wifi ->
100Mbps Cat-5 ->
Cisco 2912xl switch ->
Dual-core Atom Firewall, 2Gb RAM (running CentOS5.5 i386 and OpenVPN 2.0.9-1) ->
Untangle spam filter running as a bridge (Dual-core Xeon, 2Gb RAM) ->
Netgear FS724 24port switch ->
1000Base-T-LX SFP -> singlemode fiber connecting 'campus' buildings -> 1000base-t LX SFP ->
Netgear FS750T2 48port Gig switch ->
LAN systems


The Firewall/ VPN server CPU is sitting at 1% even when I'm 'maxing' out the VPN (at that afore-mentioned mind-numbing 1MB/sec throughput rate).

I've double and triple-checked all the various infrastructure items - DNS, Wifi speeds etc.  All work correctly - Speedtest.net reports 16Mb down and 2.5Mb up from both the LAN and Wifi segments.

Untangle isn't tapped out either - CPU at max is running at about 10-15%.

In my troubleshooting, I realized I had forgotten a very important detail - I'd turned on QoS on my Untangle box, and set the speed of our Internet connection in the config.  As a result, Untangle was limiting 'outbound' throughput to the upstream cap on our Internet connection, *even if it was going to the DMZ*!  As far as the Untangle box is concerned, anything outside of it's external interface, including the DMZ, is going to be rate limited.  So it turned out not to be an OpenVPN issue at all - it was actually Untangle doing exactly what I'd asked it to.

The diagnostic that uncovered this was running an scp file copy from teh firewall to the fileserver (taking the Wireless and DMX config out of the mix).  That was also limited to 1mbps.

At first, I thought it may be a limitation of the throughput of the Untangle box (a not-insubstantial Intel Xeon dual-core 2.4GHz, with 2Gb RAM).  I tried using the policy manager to 'no-rack' the SSH traffic, which didn't do a thing.  Then I disabled QoS for a test, and my throughput shot up to nearly 50Mbps!  That was the real "AHA!" moment in my troubleshooting.

Hopefully this helps someone with a similarly complicated setup to diagnose their 'OpenVPN' issue...

Comments or flames to rbennett at thatITguy.com

Rubin

---

### Post by windependence on 2010-09-19
Are you using TCP/IP or UDP for your connections?
 
-Tim

---

