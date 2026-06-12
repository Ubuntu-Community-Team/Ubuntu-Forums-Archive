---
title: "Gazelle Pro crashes...related to fingerprint reader?"
date: 2011-05-11
forum: System76 Support
---

### Post by Bufke on 2011-05-11
Since upgrading to Natty, I've been having some random crashes. Screen turns black and I am put at the log in screen. Looking at syslog it looks like pam_fingerprint-gui.so segfaults and somehow this results in everything exploding.

```
May 11 10:41:22 lilix2 kernel: [ 5859.439626] login[1686]: segfault at 0 ip 00007fd9449b5745 sp 00007fff8fef6cb0 error 4 in pam_fingerprint-gui.so[7fd9449b3000+5000]
May 11 10:41:22 lilix2 init: tty1 main process (1686) killed by SEGV signal
May 11 10:41:22 lilix2 init: tty1 main process ended, respawning
May 11 10:41:22 lilix2 NetworkManager[874]: <info> (wlan0): device state change: 8 -> 3 (reason 38)
May 11 10:41:22 lilix2 NetworkManager[874]: <info> (wlan0): deactivating device (reason: 38).
May 11 10:41:22 lilix2 acpid: client 1604[0:0] has disconnected
May 11 10:41:22 lilix2 acpid: client 1604[0:0] has disconnected
May 11 10:41:22 lilix2 acpid: client connected from 4148[0:0]
May 11 10:41:22 lilix2 acpid: 1 client rule loaded
May 11 10:41:22 lilix2 NetworkManager[874]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 2326
May 11 10:41:22 lilix2 avahi-daemon[758]: Withdrawing address record for 10.10.50.132 on wlan0.
May 11 10:41:22 lilix2 avahi-daemon[758]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.10.50.132.
May 11 10:41:22 lilix2 avahi-daemon[758]: Interface wlan0.IPv4 no longer relevant for mDNS.
May 11 10:41:22 lilix2 kernel: [ 5859.680980] wlan0: deauthenticating from 00:18:74:d0:5d:00 by local choice (reason=3)
May 11 10:41:23 lilix2 acpid: client connected from 4148[0:0]
May 11 10:41:23 lilix2 acpid: 1 client rule loaded
May 11 10:41:23 lilix2 kernel: [ 5860.905910] cfg80211: All devices are disconnected, going to restore regulatory settings
May 11 10:41:23 lilix2 kernel: [ 5860.905914] cfg80211: Restoring regulatory settings
May 11 10:41:23 lilix2 kernel: [ 5860.905917] cfg80211: Calling CRDA to update world regulatory domain
May 11 10:41:23 lilix2 kernel: [ 5860.908413] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
May 11 10:41:23 lilix2 kernel: [ 5860.908418] cfg80211: World regulatory domain updated:
May 11 10:41:23 lilix2 kernel: [ 5860.908419] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May 11 10:41:23 lilix2 kernel: [ 5860.908421] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 11 10:41:23 lilix2 kernel: [ 5860.908423] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 11 10:41:23 lilix2 kernel: [ 5860.908425] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 11 10:41:23 lilix2 kernel: [ 5860.908426] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 11 10:41:23 lilix2 kernel: [ 5860.908428] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 11 10:41:23 lilix2 wpa_supplicant[965]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0

```

It then continues with what looks to be starting everything back up. I'll post again after another crash to confirm it is pam_fingerprint-gui.so then try removing it to see if it fixes the problem. I can't reproduce the crash but it's been happening about once a day. Note I wasn't using the finger print reader as the time of crash. It seems to correspond exactly as press a keyboard button, but this could be coincidence.

---

### Post by Bufke on 2011-05-12
Today's crash doesn't seem to have anything suspicious in syslog. Guess it's reinstall time :cry:

```

May 12 09:27:27 lilix2 acpid: client 1718[0:0] has disconnected
May 12 09:27:27 lilix2 acpid: client 1718[0:0] has disconnected
May 12 09:27:28 lilix2 NetworkManager[1017]: <info> (wlan0): device state change: 8 -> 3 (reason 38)
May 12 09:27:28 lilix2 NetworkManager[1017]: <info> (wlan0): deactivating device (reason: 38).
May 12 09:27:28 lilix2 acpid: client connected from 10493[0:0]
May 12 09:27:28 lilix2 acpid: 1 client rule loaded
May 12 09:27:28 lilix2 NetworkManager[1017]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 2435
May 12 09:27:28 lilix2 kernel: [ 1245.968702] wlan0: deauthenticating from 00:18:74:d0:5d:00 by local choice (reason=3)
May 12 09:27:29 lilix2 acpid: client connected from 10493[0:0]
May 12 09:27:29 lilix2 acpid: 1 client rule loaded
May 12 09:27:29 lilix2 avahi-daemon[987]: Withdrawing address record for 10.10.50.132 on wlan0.
May 12 09:27:29 lilix2 avahi-daemon[987]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.10.50.132.
May 12 09:27:29 lilix2 avahi-daemon[987]: Interface wlan0.IPv4 no longer relevant for mDNS.

```

---

### Post by isantop on 2011-05-12
Did you try removing the fingerprint reader software first? We have seen lots of instability with it in Natty, and I think that's what's causing your problem.

---

### Post by Bufke on 2011-05-14
Will do, I'll see how it goes throughout next week.

---

### Post by Bufke on 2011-05-15
Bah same crash today. fingerprint-gui is uninstalled. Nothing suspicious in syslog. Seems like it always happens about an hour after boot up, then is fine the rest of the day. Could be [this?]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/765136") One comment mentions it always happens when typing, which is true for me. Found this in my Xorg log I'm really not sure how to read it.

```

[  1737.341] 
Backtrace:
[  1737.342] 0: /usr/bin/X (xorg_backtrace+0x26) [0x4a2626]
[  1737.342] 1: /usr/bin/X (0x400000+0x6219a) [0x46219a]
[  1737.343] 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f7949180000+0xfc60) [0x7f794918fc60]
[  1737.343] 3: /lib/x86_64-linux-gnu/libc.so.6 (__select+0x13) [0x7f7948189123]
[  1737.343] 4: /usr/bin/X (WaitForSomething+0x19b) [0x45c76b]
[  1737.343] 5: /usr/bin/X (0x400000+0x2e032) [0x42e032]
[  1737.343] 6: /usr/bin/X (0x400000+0x21a7e) [0x421a7e]
[  1737.343] 7: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xff) [0x7f79480c9eff]
[  1737.343] 8: /usr/bin/X (0x400000+0x21629) [0x421629]
[  1737.343]
Caught signal 3 (Quit). Server aborting
[  1737.343]
Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.
[  1737.343] Please also check the log file at "/var/log/Xorg.3.log" for additional information.
[  1737.343]

```

---

### Post by isantop on 2011-05-16
It's worth noting that the instability we found during test didn't come from fingerprint-gui, but rather the patched PAM packages. Did those get uninstalled too? If not, you'll want to have a look at this page:

[http://knowledge76.com/index.php/Fingerprint_Reader_Usage](http://knowledge76.com/index.php/Fingerprint_Reader_Usage)

---

### Post by Bufke on 2011-05-17
Thanks, there were some packages still installed apparently, I removed them. But it crashed again today. Saw this come up when booting.

May 17 09:50:05 lilix2 gnome-session[5592]: WARNING: Could not launch application 'fingerprint-polkit-agent.desktop': Unable to start application: Failed to execute child process "/usr/lib/fingerprint-gui/fingerprint-polkit-agent" (No such file or directory)

Also gnome-keyring keeps prompting me for password. I use no password, I explicitly set it not to. It prompts me anyway and accepts nothing. Something clearly is very wrong. Any other ideas?

---

### Post by isantop on 2011-05-19
When you removed the fingerprint reader packages, did you reinstall the original Ubuntu package that got replaced? if not, then that's probably part of the lockup problem.

As for the password issue, do you mean to say that your password is blank, or that you've set it up to skip it. Do you still need a password to do administrative changes?

---

### Post by Bufke on 2011-05-24
policykit-1-gnome was installed while it was crashing. I did a "restore system" from the system76 driver tool and this seems to have fixed the problem. Wonder what in that did it? I ran it after upgrading to natty as it says to do.

The password issue is a [separate problem]("https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/744929") I think. Not so worried about it.

---

### Post by isantop on 2011-05-25
Sounds good! Let us know if you have any other problems.

---

