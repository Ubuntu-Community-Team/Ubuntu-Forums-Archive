---
title: "Unwanted Listening Ports"
date: 2009-02-22
forum: Security
---

### Post by prinny42 on 2009-02-22
I might just be overreacting and this is nothing.  Indeed, I hope that is the case, but this is the output of "sudo netstat -lp":

```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost:ipp           *:*                     LISTEN      5076/cupsd      
udp        0      0 *:60848                 *:*                                 4908/avahi-daemon: 
udp        0      0 *:bootpc                *:*                                 5704/dhclient   
udp        0      0 *:mdns                  *:*                                 4908/avahi-daemon: 
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     15429    5078/winbindd       /tmp/.winbindd/pipe
unix  2      [ ACC ]     STREAM     LISTENING     17844    5920/scim-launcher  /tmp/scim-socket-frontend-(My Username)
unix  2      [ ACC ]     STREAM     LISTENING     16707    5517/X              /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     18167    5927/scim-helper-ma /tmp/scim-helper-manager-socket-(My Username)
unix  2      [ ACC ]     STREAM     LISTENING     18171    5928/scim-panel-gtk /tmp/scim-panel-socket:0-(My Username)
unix  2      [ ACC ]     STREAM     LISTENING     17288    5798/gnome-keyring- /tmp/keyring-1Kp9B5/socket
unix  2      [ ACC ]     STREAM     LISTENING     19528    6028/scim-bridge    /tmp/scim-bridge-0.3.0.socket-1000@localhost:0.0
unix  2      [ ACC ]     STREAM     LISTENING     17294    5798/gnome-keyring- /tmp/keyring-1Kp9B5/ssh
unix  2      [ ACC ]     STREAM     LISTENING     21483    6259/liferea-bin    /tmp/liferea.(My Username).3028378970
unix  2      [ ACC ]     STREAM     LISTENING     17300    5798/gnome-keyring- /tmp/keyring-1Kp9B5/socket.pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     16393    5383/bluetoothd     /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     17850    5917/pulseaudio     /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     17862    5917/pulseaudio     /tmp/pulse-(My Username)/native
unix  2      [ ACC ]     STREAM     LISTENING     17908    5924/gconfd-2       /tmp/orbit-(My Username)/linc-1724-0-7f74cf1876d5a
unix  2      [ ACC ]     STREAM     LISTENING     18153    5922/gconf-helper   /tmp/orbit-(My Username)/linc-1722-0-d6093389efa8
unix  2      [ ACC ]     STREAM     LISTENING     18198    5936/seahorse-agent /tmp/seahorse-5XVT5m/S.gpg-agent
unix  2      [ ACC ]     STREAM     LISTENING     18223    5809/x-session-mana /tmp/.ICE-unix/5809
unix  2      [ ACC ]     STREAM     LISTENING     18245    5809/x-session-mana /tmp/orbit-(My Username)/linc-16b1-0-73a056fd79c9a
unix  2      [ ACC ]     STREAM     LISTENING     18290    5936/seahorse-agent /tmp/orbit-(My Username)/linc-1730-0-1309affa76c74
unix  2      [ ACC ]     STREAM     LISTENING     18417    5947/gnome-settings /tmp/orbit-(My Username)/linc-173b-0-57293fe4bd909
unix  2      [ ACC ]     STREAM     LISTENING     16662    5511/gdm            /var/run/gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     18533    5955/metacity       /tmp/orbit-(My Username)/linc-1743-0-fb7dfc510620
unix  2      [ ACC ]     STREAM     LISTENING     18738    5962/gnome-panel    /tmp/orbit-(My Username)/linc-174a-0-57ea90fab2f7
unix  2      [ ACC ]     STREAM     LISTENING     18802    5968/nautilus       /tmp/orbit-(My Username)/linc-1750-0-3399b07045a78
unix  2      [ ACC ]     STREAM     LISTENING     18850    5972/bonobo-activat /tmp/orbit-(My Username)/linc-1754-0-2cf2ff66d3eea
unix  2      [ ACC ]     STREAM     LISTENING     18902    5990/gnome-screensa /tmp/orbit-(My Username)/linc-1761-0-2e89c22836955
unix  2      [ ACC ]     STREAM     LISTENING     19078    6000/trashapplet    /tmp/orbit-(My Username)/linc-1770-0-4deb305dc56f3
unix  2      [ ACC ]     STREAM     LISTENING     19307    6015/glunarclock-ap /tmp/orbit-(My Username)/linc-177f-0-7b31cb59b7e7c
unix  2      [ ACC ]     STREAM     LISTENING     19324    6020/mixer_applet2  /tmp/orbit-(My Username)/linc-1784-0-7b31cb59bed86
unix  2      [ ACC ]     STREAM     LISTENING     19346    6012/fast-user-swit /tmp/orbit-(My Username)/linc-177c-0-7b31cb59e0c89
unix  2      [ ACC ]     STREAM     LISTENING     19901    6038/nm-applet      /tmp/orbit-(My Username)/linc-1796-0-3964bbf2e532c
unix  2      [ ACC ]     STREAM     LISTENING     15396    5074/atieventsd     /var/run/atieventsd.socket
unix  2      [ ACC ]     STREAM     LISTENING     14885    4823/acpid          /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     19965    6044/gnome-power-ma /tmp/orbit-(My Username)/linc-1795-0-c15ace6d369c
unix  2      [ ACC ]     STREAM     LISTENING     19971    6039/update-notifie /tmp/orbit-(My Username)/linc-1797-0-c15ace6d5263
unix  2      [ ACC ]     STREAM     LISTENING     20000    6047/notification-d /tmp/orbit-(My Username)/linc-179f-0-6cc6747e69bf8
unix  2      [ ACC ]     STREAM     LISTENING     15607    5217/hald           @/var/run/hald/dbus-HUZCxJrHRv
unix  2      [ ACC ]     STREAM     LISTENING     21505    6259/liferea-bin    /tmp/orbit-(My Username)/linc-1873-0-35c24336cc867
unix  2      [ ACC ]     STREAM     LISTENING     97487    23065/firefox       /tmp/orbit-(My Username)/linc-5a19-0-54675093dfcff
unix  2      [ ACC ]     STREAM     LISTENING     112146   10514/gnome-termina /tmp/orbit-(My Username)/linc-2912-0-7bd41ca4cdfcc
unix  2      [ ACC ]     STREAM     LISTENING     15431    5078/winbindd       /var/run/samba/winbindd_privileged/pipe
unix  2      [ ACC ]     STREAM     LISTENING     16395    5383/bluetoothd     @/org/bluez/audio
unix  2      [ ACC ]     STREAM     LISTENING     16706    5517/X              @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     17805    5914/dbus-daemon    @/tmp/dbus-Em1g5kpe15
unix  2      [ ACC ]     STREAM     LISTENING     15002    4881/dbus-daemon    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     106653   5076/cupsd          /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     15062    4908/avahi-daemon:  /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     15594    5217/hald           @/var/run/hald/dbus-1msZhx5MaQ
```

Now, if I understand correctly, by default, every port is closed on Ubuntu and that only changes if you set something to listen on it.  I was trying to be careful not to set any ports to listen, and the only things I did with the internet other than standard things like web browsing and apt was using ssh and telnet, respectively, to connect to the devnull and alt.org Nethack servers.

So I have a few questions.  Is this what it looks like (a bunch of ports are listening and just waiting to be broken into)?  Should I be worried?  Further, why are things like "trashapplet" and the gnome screensaver listening, of all things?  Finally, should I close these or something, and if so, how?

Thank you very much.

---

### Post by bodhi.zazen on 2009-02-22
You need to scan your box from a remote location or use a different command.

Those all look normal to me. Your computer talks to itself via the lo interface , this does not mean you have a problem.

See the top part of this page :

[http://bodhizazen.net/beginners/Firewall/](http://bodhizazen.net/beginners/Firewall/)

---

### Post by brian_p on 2009-02-22
> **prinny42 said:**
> 

So I have a few questions.  Is this what it looks like (a bunch of ports are listening and just waiting to be broken into)?  Should I be worried?  Further, why are things like "trashapplet" and the gnome screensaver listening, of all things?  Finally, should I close these or something, and if so, how?

Of the Active Internet connections the only listening process is

```
tcp        0      0 localhost:ipp
```

That's the printing system (cupsd). Note it listens only for requests made from itself (localhost).

The UNIX domain sockets are for moving data about **on the computer itself**. None of those data leaves the computer.

Nothing to close, nothing to do and nothing to worry about.

---

### Post by prinny42 on 2009-02-22
I see; I think I understand what's going on now.  I didn't realize that the computer communicated with itself like that.  I just wanted to be sure I hadn't inadvertently messed something up.

Thank you for your help, bodhi.zazen and brian_p.

EDIT:  For some reason "Thread Tools" is not giving me the option to mark the thread as solved.  Has that been moved to another location?  Anyway, I simply wanted to apologize for not marking it.

---

### Post by bodhi.zazen on 2009-02-22
We had to disable that feature on the forums for the moment. You can change the title and manually add "[Solved]" if you wish.

---

### Post by cdenley on 2009-02-23
The frequent claim that you have no listening network processes by default isn't entirely accurate. You also have avahi and dhclient listening on UDP sockets, which is the default for a desktop configuration. They aren't considered a security risk, but you can remove them if you don't need them.
```

sudo apt-get remove avahi-daemon dhcp3-client

```
If you use dhcp, you might have network problems, though.

---

