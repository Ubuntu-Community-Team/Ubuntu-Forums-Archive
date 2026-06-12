---
title: "[SOLVED] panv3 WLAN not working"
date: 2007-09-19
forum: System76 Support
---

### Post by osx424242 on 2007-09-19
Hey folks,

I am trying to include as much detail as possible up front, so _please_ be patient...:

I have been unable to get my wireless LAN working on my Pangolin Value.  It has an Intel 3945ABG internal wireless card, and my wireless router is a LinkSys WRT54GS (both of these seem to be rather common, so I am actually surprised that I am having this much trouble!).  I've tried pretty much every hint from every thread I've been able to find here on ubuntuforums.org, but still no luck.  My first week or so with the laptop I was sidetracked by the 'Fn-F2 not working' bug which may have led me down some wrong paths, but I am fairly certain that I now have my wireless card turned _on_ (e.g. it shows some (as opposed to none) orange bars for my wireless router in Network Manager, and the litle blue WLAN light on the front of my laptop flashes) and actively trying to connect to my network, but it is still unable to do so.

== More About the Problem

I am unable to connect both when I am (1) using WPA encryption, SSID broadcast disabled, and MAC ID filtering enabled (i.e. attempting to secure the two XP boxes and one OS X Mini); and (2) using no encryption, broadcasting an SSID, with MAC ID filtering disabled (i.e. completely open network to try to troubleshoot Ubuntu/panv3/Intel).  I have the same issues when I am (a) upstairs with a 10 foot-direct-line-of-sight to the wireless router; and (b) downstairs from the wireless router but within six feet of the Belkin USB WLAN adapater used by my Mac Mini.

While trying to connect with Network Manager, if I mouse over the NM icon on my top bar [ubuntu install; I haven't started customizing menu bars yet because I'm still fighting this WLAN thing] it says "Waiting for Network Key for the wireless network 'andrewsssid'..."

[I replaced my actual SSID with andrewsssid, but the single quotes (') and ellipses (...) are a direct quote from the pop-over message]

== Unwanted Workaround

I have no problems at all when I plug the LAN cable directly into one of my wireless router's LAN ports: I get a very stable internet connection but I also have one very un-wireless 50' cable connected to my laptop.

== Backstory

When I try to connect with Network Manager (similar story when I uninstalled Network Manager and tried wicd), Network Manager seems to see my wireless router and then sits for a little while (somewhere between 30 seconds and two minutes; I've never tried to time it), trying to connect, and then times out.

[Side note, it did succeed _once_, about a week ago (I turned my computer on [it had been off overnight] and it immediately found the network and connected to it), and I downloaded a few hundred kilobytes (about half) of some file or system update (I forget what) before the download stalled and Network Manager said I was disconnected.  Other than that brief, unexpected success, I have never been able to connect to my wireless router.]

At one point I surmised that the problem was related to the Keyring program and I deleted my keyring; no joy; then I eventually uninstalled Keyring (I don't like programs like that, anyway).  Also, if it matters, the _first_ thing I did after getting my laptop was plug in the LAN cable and install all the needed updates (I assumed at the time that Wireless LAN would "just work" and that installing updates was more important).

I have run the System | Administration | System76 Driver | {Install Drivers; Restore System} multiple times since receiving this laptop.  For example, from time to time the Wireless Network options would disappear from Network Manager and I found that "Restore System" would also restore the option (but, unfortunately, not the ability!) to connect to a wireless network.

Please let me know if you have any suggestions, and I'm more than willing to try new things (send you the output from logs or commands, play with my router settings, etc.).  I'm a fairly-long-time *nix _user_ but a first-time *nix _administrator_, so I think that I can do whatever you ask, but I don't understand enough of the 'why's or 'how's yet to figure this out on my own.

thanks.....

Andrew

---

### Post by thomasaaron on 2007-09-19
Hi, Andrew.

First, it's probably not a good idea to start deleting things like Network Manager and the Keyring program == which actually do work quite well out of the box. Your problem is definitely configuration-based, not software-based.

At this point, your explanation is so complex that I think we should get things back to some default settings.

1. Go to a terminal and enter: sudo gedit /etc/network/interfaces
Make the resulting file look EXACTLY like this. If it has other configurations in it, delete them.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
```

2, A few useful principles:
First: Use your network manager icon to connect to wireless access points. Avoid using System > Administration > Networks, as it hoses the above file.

Second: You should only RARELY have to use the manual configuration option on network manager. Network Manager is smart enough in most cases to prompt you for what it needs.

Third: THIS IS IMPORTANT. Network Manager must be set up EXACTLY like your router. That does not mean ALMOST like your router. Network Manager is extremely picky. If the router says 64bit Hex, so should NM. If the router is set up as an Open System, so should NM be. I'm not trying to be over simplistic here, but 99% of the problems we have with networking is because of this. Thus, my overemphasis.

Fourth: I use the same router you do. I've had the best luck with setting it to: Open System, 64-BIT hex, WEP encryption.

---

### Post by osx424242 on 2007-09-19
Thanks, Thomas.  I think I am much closer now.

I changed /etc/network/interfaces to match what you said and rebooted.  I was prompted by Network Manager for the password to connect to my wireless router and I entered it, and I also changed from "Auto" to "TKIP" (the only option; I took this step because I have read several times on ubuntuforums that using 'Auto' seems to cause problems sometimes) and clicked OK: it connected right away!  Then I was prompted for a password for the default keyring (well, I _thought_ I had uninstalled it!).  I entered a password and pressed OK, and Network Manager immediately popped up a small "network disconnected" message.  I had _not_ tried to verify network connectivity (e.g. open Firefox, connect to a web site) before it disconnected.

I left-clicked on Network Manager and it could still see my wireless router's SSID, so I left-clicked on that line.  It did its normal thing of taking about 30 seconds to try to connect, then giving up.

I checked /etc/network/interfaces and it looked exactly like it should.

Reboot....

On powerup, I was asked for the keyring password before any icons had loaded (e.g. Network Manager's icon on the top menu bar).  I waited about 20 seconds, in that time the icons all loaded and Network Manager had tried to connect, but hadn't been able to yet.  Before NM timed out, I entered my keyring password and pressed OK.  Again, Network Manager did it's usual "Waiting for Network Key for the wireless network 'myssid'..." for half a minute or so, then gave up and just says "No network connection".  I tried again to left-click on it and select my wireless router, but it still could not connect.  I plugged my LAN cable back in so I could post this.

I checked the interfaces file again after rebooting, just in case:

```
$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
$ 
```

I will try your next recommendation this evening, after work.

Thanks.....

---

### Post by thomasaaron on 2007-09-19
If it's sees the router and tries for a long period of time to connect, the settings of the router and NM are not in sync.

---

### Post by osx424242 on 2007-09-19
I reset my wireless router to "Factory Defaults" in an effort to get NM synced up to the router.  I rebooted and NM saw the 'linksys' network.  It tried to connect but I am still seeing the same behavior: "Attempting to join the wireless network 'myssid'..." while that little comet still goes around and around the NM icon and it never connects.

I'm not really sure what to try from here.

---

### Post by osx424242 on 2007-09-20
Update: still on the right track, maybe.  I turned my laptop off for a couple hours and moved it back downstairs (the wireless router is on the upper floor).  I turned the laptop on and it immediately connected to the wireless network!  I opened Firefox and it connected to all my tabs (about a dozen, mostly ubuntuforums.org).  I wandered away for about 5 minutes; when I came back I tried to refresh a page (my gmail Inbox) and open a new page (ubuntuforums.org homepage).  Both tabs just kept trying to refresh.   I noticed that my keyboard seemed to more-or-less stop working (I could move my USB mouse and click on text boxes and see a cursor appear like I expected, and focus followed the mouse correctly, but I didn't see any letters when I typed them, for example in the Fx location bar).  I eventually had to power down the laptop (hold down the physical power button for ~5 seconds).  When I turned the laptop back on, I was not able to connect to the wireless network.

I also tried connecting using my Belkin USB WLAN adapter, which I use for my Mac Mini, but was not able to connect to the network.  The adapter was recognized by Network Manager as an Unknown USB Vendor Specific Interface (NM didn't support WPA for this device so I turned off encryption on my wireless router, but the Belkin still couldn't connect) but I was never able to get it connected to my wireless network.

Grrr, it was encouraging that I was able to actually connect and transfer some data, but it is irritating that I have yet to get a stable connection.

---

### Post by thomasaaron on 2007-09-20
Trying to refresh a dozen windows at once could definitely slow things down and cause an unresponsive keyboard. Also, it would be better for you to just let the refreshing time-out than kill the computer with the power button.

If the computer is reading or writing to the wrong file when you do that, you could hose your file-system. That would make the cure much worse than the problem. :lolflag:

There is a "Force Quit" launcher that you can put on your upper panel that will kill firefox without endangering anything.

---

### Post by octathlon on 2007-09-20
This sounds similar to some of the problems I was having with my panv3  described in [http://ubuntuforums.org/showthread.php?t=532367](http://ubuntuforums.org/showthread.php?t=532367) and [http://ubuntuforums.org/showthread.php?t=534606](http://ubuntuforums.org/showthread.php?t=534606)

I never figured out exactly what caused all the problems, but the changes I made in my router setup were: set the router to broadcast the SSID, set it to Open system.  I was using WEP encryption and MAC filtering the whole time.  Then I deleted the default keyring in Keyring manager and restarted, so when I logged in I got prompted for the network settings again (I made sure to select Open system there) and for a password for Keyring manager(this time I used the same password as my login password).

Since then, the only problem I have is occasional dropping of the connection but no problems reconnecting when that happens.

---

### Post by osx424242 on 2007-10-19
I wasn't able to get anywhere with my wireless, so I spent a couple weeks with a long blue LAN cable and waited for Gutsy -- unfortunately, it still isn't working after the Gutsy upgrade.

A little more about what I did today: I turned on my computer, and within about 10 seconds it had connected to my wireless network.  I was able to load several web pages; about 30 seconds or so later, connectivity went away.  I did an 'iwconfig' while things were working and saw what looked like a good connection for 'eth1' (I didn't think to run 'script', and my terminal's scrollback buffer was way too low, so I can't post it here).  'dmesg' output while things were working was fine: it didn't mention ipw3945 at all except for a couple status updates that things seemed to be okay.

After network connectivity goes away, the network manager icon bounces between no bars, 1 bar, and full bars for a couple minutes, but at no time can I get a web page to load.  After a couple minutes of this, it seems to give up trying to connect, although left-clicking on the network manager icon still shows my wireless network at around 80% signal strength.  At this point, iwconfig reports:

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.
```

and dmesg output is littered with

```
[  173.896000] ipw3945: Radio Frequency Kill Switch is On:
[  173.896000] Kill switch must be turned off for wireless networking to work.
[  174.292000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
```

I don't know how to change the kill switch state, because Fn-F2 (the F2 key on my panv3 has an antenna icon it) causes this dmesg output (I remember, long ago, seeing someone else with a similar problem on a system76 laptop, I think there is a bug filed about it; I looked more recently but couldn't find the bug report):

```
[   99.052000] atkbd.c: Unknown key pressed (translated set 2, code 0x84 on isa0060/serio0).
[   99.052000] atkbd.c: Use 'setkeycodes e004 <keycode>' to make it known.
[   99.060000] atkbd.c: Unknown key released (translated set 2, code 0x84 on isa0060/serio0).
[   99.060000] atkbd.c: Use 'setkeycodes e004 <keycode>' to make it known.
```

When the wireless networking stops trying to connect, I get this dmesg output:

```
[  244.524000] ipw3945: Radio Frequency Kill Switch is On:
[  244.524000] Kill switch must be turned off for wireless networking to work.
[  245.752000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[  247.960000] ipw3945: Radio Frequency Kill Switch is On:
[  247.960000] Kill switch must be turned off for wireless networking to work.
[  248.848000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[  251.084000] ipw3945: Error sending SCAN_ABORT_CMD: time out after 500ms.
[  251.084000] ipw3945: Radio Frequency Kill Switch is On:
[  251.084000] Kill switch must be turned off for wireless networking to work.
[  251.584000] ipw3945: Error sending ADD_STA: time out after 500ms.
[  252.084000] ipw3945: Error sending RATE_SCALE: time out after 500ms.
[  252.084000] ipw3945: XXXL we have skipped command
[  256.080000] ipw3945: Microcode SW error detected.  Restarting.
[  256.080000] ipw3945: Error Reply type 0x00000005 cmd LEDS_CMD (0x48) seq 0x0411 ser 0x004A0000
```

I've actually seen the "Microcode SW error detected.  Restarting." a _lot_ in the last couple weeks in my dmesg, while trying occasionally to get wireless to work.  I did download the latest microcode from the Intel 3945 site, just in case, but diff reports that it is identical to what I already have.


I've looked around plenty of sites online, but haven't found anyone else with the same problem.  Any ideas?

Also, you mentioned that you suspect a "configuration" problem -- were you referring to something obvious like encryption (WAP/WEP/none) or broadcast SSID state; or something less obvious, like DTIM Interval or Fragmentation Threshold (settings on the "Advanced Wireless Settings" tab on y router setup page)?

---

### Post by thomasaaron on 2007-10-22
There is a switch for your wireless radio along the leading edge of the computer on the left hand side.

---

### Post by osx424242 on 2007-10-23
Thanks... although my understanding has been that the switch on the front controls the Bluetooth transceiver.  I usually leave that switch in what I believe is the 'Off' position.  Just for kicks, after my WLAN worked for a minute and then gave up, printing Radio Frequency Kill Switch is On messages to 'dmesg', I tried changing that switch: WLAN continued to not work, a Bluetooth icon appeared in the menubar at the top of the screen, and the LED (that flashes blue every once in a while to taunt me by reminding me that I have a WLAN card but it doesn't work) turned on with a solid (as opposed to blinking) pink.

---

### Post by thomasaaron on 2007-10-23
That switch definitely kills the wireless radio.

---

### Post by osx424242 on 2007-10-24
Wow, that did the trick.  Thanks!  Pretty serious case of PEBKAC here.

For future use, in case anyone stumbles across this thread:
- Need to power up with the wireless switch in the On position.  Turning it on after the laptop has been on for a while seems to not work.
- With the wireless switch in the Off position, you can actually get the WLAN to connect and work for about a minute.

---

### Post by thomasaaron on 2007-10-24
> Pretty serious case of PEBKAC here.:lolflag:

That's funny! I had to google PEBKAC. Never heard it before.

Welcome to ***my*** life.

---

