---
title: "Netatalk broken in oneiric ?"
date: 2011-10-13
forum: Server Platforms
---

### Post by N1ko on 2011-10-13
After upgrading to Oneiric tonight I cant seem to get Netatalk working. Previously I had 2.2-beta4 in Natty, which I removed, then installed Netatalk from the Oneiric repos.

I cant get any shares open or even log to the share. This is the error I get when trying to connect from OSX Lion on two machines:

Oct 13 19:44:12 wagner afpd[18956]: ===============================================================
Oct 13 19:44:12 wagner afpd[18956]: INTERNAL ERROR: Signal 11 in pid 18956 (2.2-beta4)
Oct 13 19:44:12 wagner afpd[18956]: ===============================================================
Oct 13 19:44:12 wagner afpd[18956]: BACKTRACE: 3 stack frames:
Oct 13 19:44:12 wagner afpd[18956]:  #0 /usr/sbin/afpd(netatalk_panic+0x1c) [0x7f885667d49c]
Oct 13 19:44:12 wagner afpd[18956]:  #1 /usr/sbin/afpd(+0x4d59c) [0x7f885667d59c]
Oct 13 19:44:12 wagner afpd[18956]:  #2 /lib/x86_64-linux-gnu/libc.so.6(+0x36420) [0x7f8855659420]

I also tried 2.2.1 (by compiling myself) but the same error pops up. Probably not a netalk issue, but something to do with oneiric.

Theres a bug open in the tracker [https://bugs.launchpad.net/ubuntu/+source/netatalk/+bug/810732](https://bugs.launchpad.net/ubuntu/+source/netatalk/+bug/810732) but no answer. Workaround would be fine for now.. 

This was also reported to netatalk but seems that they aren't too enthustiastic to figure out the problem : [http://sourceforge.net/tracker/?func=detail&aid=3418627&group_id=8642&atid=108642](http://sourceforge.net/tracker/?func=detail&aid=3418627&group_id=8642&atid=108642)

---

### Post by paracycle on 2011-10-14
I just managed to find a workaround that works and is manageable in my particular setup. I added my findings to the bug report you linked to on Launchpad.

Best of luck,

Ufuk

---

### Post by foxxyben on 2011-10-15
Hi guys,

I'm having the same issue.  I'm using the workaround, but only for public shares.  I've temporarily switched to samba for private shares.  Very much looking forward to a fix for this!

 - Ben

---

### Post by paracycle on 2011-10-17
I guess I have a simpler workaround this time. :) I added the details to the original bug.

Please report if this temporarily solves your problem.

---

### Post by foxxyben on 2011-10-17
Just implemented your workaround from the bug report.  Things look like they are working as before.  Thanks!!!:guitar:

 - Ben

---

### Post by parisv on 2011-10-19
I'm having the same problem too. I had a couple of other problems so I reinstalled my machine completely also formatted and resized /

I also installed 11.10 on a virtual machine weird thing is it works on my vm but not on my actual server!

I tried copying over afpd.conf as a test but it didn't work.

I've tried the work around on the bug page but still no joy. If I want to reinstall netatalk do I apt-get remove it, then just reinstall it? Or do I have to remove other things?

For both cases this is how I installed:

```
sudo apt-get build-dep netatalk
sudo apt-get install cracklib-runtime fakeroot libssl-dev
sudo apt-get source netatalk
cd netatalk-2*

sudo DEB_BUILD_OPTIONS=ssl dpkg-buildpackage -rfakeroot

sudo dpkg -i ~/netatalk_2*.deb

echo "netatalk hold" | sudo dpkg --set-selections
```

I got the installation instructions from [here]("http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/")

It says install cracklib2-dev but I could only find cracklib-runtime. I did this last time in 11.04 and this was fine.


here are the log file differences between server and virtual machine:

```
*** not working server

Oct 19 19:02:43.256977 afpd[1979] {dsi_tcp.c:346} (I:DSI): dsi_tcp_init: bind: Address already in use

Oct 19 19:02:43.256983 afpd[1979] {dsi_tcp.c:360} (E:DSI): dsi_tcp_init: no suitable network config for TCP socket
Oct 19 19:02:43.256990 afpd[1979] {afp_config.c:361} (E:AFPDaemon): main: dsi_init: Address already in use
Oct 19 19:02:43.256998 afpd[1979] {auth.c:1165} (I:AFPDaemon): uam: uam not found (status=-1)
Oct 19 19:02:43.501732 afpd[1979] {afp_avahi.c:115} (I:AFPDaemon): Registering server 'homeserv' with with Bonjour
Oct 19 19:02:43.502886 afpd[1979] {afp_avahi.c:312} (I:AFPDaemon): Successfully started avahi loop.
Oct 19 19:02:43.502904 afpd[1979] {cnid.c:53} (I:AFPDaemon): Registering CNID module [last]
Oct 19 19:02:43.502922 afpd[1979] {cnid.c:53} (I:AFPDaemon): Registering CNID module [dbd]
Oct 19 19:02:43.502927 afpd[1979] {cnid.c:53} (I:AFPDaemon): Registering CNID module [tdb]
Oct 19 19:03:26.546391 afpd[1979] {main.c:170} (I:AFPDaemon): child[1982]: exited 1
Oct 19 19:03:26.555333 afpd[1983] {dsi_tcp.c:212} (I:DSI): AFP/TCP session from 192.168.20.54:51807
Oct 19 19:03:26.557512 afpd[1979] {main.c:172} (I:AFPDaemon): child[1983]: done
Oct 19 19:03:30.309057 afpd[1979] {main.c:170} (I:AFPDaemon): child[1984]: exited 1
Oct 19 19:03:30.309812 afpd[1985] {dsi_tcp.c:212} (I:DSI): AFP/TCP session from 192.168.20.54:51810
Oct 19 19:03:30.312602 afpd[1979] {main.c:172} (I:AFPDaemon): child[1985]: done
Oct 19 19:03:37.990511 afpd[1987] {dsi_tcp.c:212} (I:DSI): AFP/TCP session from 192.168.20.54:51811
Oct 19 19:03:37.992012 afpd[1987] {uams_dhx2_pam.c:321} (I:UAMS): DHX2 login: parisv
Oct 19 19:03:38.392022 afpd[1987] {uams_dhx2_pam.c:210} (I:UAMS): PAM DHX2: PAM Success
Oct 19 19:03:38.407088 afpd[1987] {fault.c:122} (S:Default): ===============================================================
Oct 19 19:03:38.407107 afpd[1987] {fault.c:123} (S:Default): INTERNAL ERROR: Signal 11 in pid 1987 (2.2-beta4)
Oct 19 19:03:38.407117 afpd[1987] {fault.c:124} (S:Default): ===============================================================
Oct 19 19:03:38.407329 afpd[1987] {fault.c:96} (S:Default): BACKTRACE: 3 stack frames:
Oct 19 19:03:38.407346 afpd[1987] {fault.c:102} (S:Default):  #0 /usr/sbin/afpd(netatalk_panic+0x1c) [0x7fa827c92a5c]
Oct 19 19:03:38.407356 afpd[1987] {fault.c:102} (S:Default):  #1 /usr/sbin/afpd(+0x4eb5c) [0x7fa827c92b5c]
Oct 19 19:03:38.407364 afpd[1987] {fault.c:102} (S:Default):  #2 /lib/x86_64-linux-gnu/libc.so.6(+0x36420) [0x7fa826c6d420]
Oct 19 19:03:38.407835 afpd[1979] {main.c:175} (I:AFPDaemon): child[1987]: killed by signal 6
Oct 19 19:03:47.166179 afpd[1979] {main.c:170} (I:AFPDaemon): child[1988]: exited 1
Oct 19 19:03:47.167103 afpd[1989] {dsi_tcp.c:212} (I:DSI): AFP/TCP session from 192.168.20.54:51814
Oct 19 19:03:47.171679 afpd[1979] {main.c:172} (I:AFPDaemon): child[1989]: done




*** working vm

ct 17 21:19:28.192513 afpd[17617] {dsi_tcp.c:346} (I:DSI): dsi_tcp_init: bind: Address already in use

Oct 17 21:19:28.192520 afpd[17617] {dsi_tcp.c:360} (E:DSI): dsi_tcp_init: no suitable network config for TCP socket
Oct 17 21:19:28.192527 afpd[17617] {afp_config.c:361} (E:AFPDaemon): main: dsi_init: Address already in use
Oct 17 21:19:28.192537 afpd[17617] {auth.c:1165} (I:AFPDaemon): uam: uam not found (status=-1)
Oct 17 21:19:28.464749 afpd[17617] {afp_avahi.c:115} (I:AFPDaemon): Registering server 'testserv' with with Bonjour
Oct 17 21:19:28.466330 afpd[17617] {afp_avahi.c:312} (I:AFPDaemon): Successfully started avahi loop.
Oct 17 21:19:28.466363 afpd[17617] {cnid.c:53} (I:AFPDaemon): Registering CNID module [last]
Oct 17 21:19:28.466370 afpd[17617] {cnid.c:53} (I:AFPDaemon): Registering CNID module [dbd]
Oct 17 21:19:28.466376 afpd[17617] {cnid.c:53} (I:AFPDaemon): Registering CNID module [tdb]
Oct 17 21:20:20.892614 afpd[17621] {dsi_tcp.c:212} (I:DSI): AFP/TCP session from 192.168.147.1:51794
Oct 17 21:20:20.894144 afpd[17617] {main.c:172} (I:AFPDaemon): child[17621]: done
Oct 17 21:20:20.895381 afpd[17617] {main.c:170} (I:AFPDaemon): child[17620]: exited 1
Oct 17 21:20:31.796632 afpd[17622] {dsi_tcp.c:212} (I:DSI): AFP/TCP session from 192.168.147.1:51795
Oct 17 21:20:31.797409 afpd[17622] {uams_dhx2_pam.c:321} (I:UAMS): DHX2 login: parisv
Oct 17 21:20:32.052782 afpd[17622] {uams_dhx2_pam.c:210} (I:UAMS): PAM DHX2: PAM Success
Oct 17 21:20:32.062562 afpd[17622] {uams_dhx2_pam.c:653} (I:UAMS): DHX2: PAM Auth OK!
Oct 17 21:20:32.062824 afpd[17622] {auth.c:269} (N:AFPDaemon): AFP3.3 Login by parisv
Oct 17 21:20:32.066459 afpd[17622] {volume.c:1961} (I:AFPDaemon): Volume /home/parisv use CNID scheme dbd.
Oct 17 21:20:32.066761 afpd[17622] {volume.c:1966} (I:AFPDaemon): CNID server: localhost:4700
Oct 17 21:20:40.087446 afpd[17622] {auth.c:940} (N:AFPDaemon): AFP logout by parisv
Oct 17 21:20:40.088109 afpd[17622] {dsi_stream.c:314} (E:DSI): dsi_stream_read: len:0, unexpected EOF
```

---

### Post by welshdavid on 2011-10-19
> **foxxyben said:**
> Just implemented your workaround from the bug report.  Things look like they are working as before.  Thanks!!!:guitar:

 - Ben
I also had an identical problem after upgrading to Oneric, and the workaround in the Bug Report seemed to do the trick nicely!

No need to reinstall anything, just need to make a minor modification to the /etc/netatalk/afpd.conf file

---

### Post by jackdale on 2011-11-01
Just made the mod as per the workaround and things are back to normal.

I did have a new cnid fault, but this was fixed by changing the cnidscheme back to the default (dbd) in AppleVolumes.default

---

