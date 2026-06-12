---
title: "Quick and dirty file transfer server for PS3."
date: 2010-07-02
forum: Server Platforms
---

### Post by Captain Smiley Pants on 2010-07-02
So here's the drill; I've been having headaches trying to get mediatomb, ps3mediaserver, and other upnp stuff up and running my Ubuntu box.

You know what? I don't want any of that fancy pants stuff going on anyway.

I'd think it would be really nice and simple to just have an apache server up and running. Then, through the PS3's browser, I can just save the target file into my PS3. Done and done, no muss no fuss, that's how I want it done.

So what I've done so far is install apache. I go into Firefox and type in localhost to get:

```
**It works!**

 This is the default web page for this server.
 The web server software is running but no content has been added,  yet.

```

That's the default apache page, so far so good. Wonderful.

I change my httpd.conf to include the following:

```
DocumentRoot /home/coleman
```

Now, there are a few problems for whatever reason.

Problem 1: Well, after making these changes, I try localhost again and it still says the default page. I clear my cache and it's still doing that. OK, no problem, I'm sure I'm supposed to update something, right? Anybody know real quick on that one?

Problem 2: When I'm on the PS3's browser, I type in the IP of my Ubuntu box (box the PS3 and the box have static IPs, just so I can avoid confusion). The PS3 indicates that it is talking to my netbook, but it times out. I'm sure I'm supposed to change some permissions somewhere on here, right?

Problem 3: Just to make sure mediatomb is off of the computer, I type in my address plus it's port. I get the mediatomb login page, even though I've specifically told apt-get to *purge* the packages. I've even removed the .mediatomb folder in my home folder. Why is it still haunting me?

And a quick question:

So, after I've configured everything, is there a way to make sure I have to manually start apache with my computer starting on and off? It's great for my home network but there's no way I'd like anyone at school and work to see my home folder. I'm sure I could create come launchers/shortcuts that turn the server on and off, right?

I'm sure there are some apache guru's who'd love to point out my server newbness, so don't be afraid!

---

### Post by Captain Smiley Pants on 2010-07-03
Now this is happening:

```
httpd not running, trying to start
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

```

When I try to restart the process.

I'm still wondering why the hell Mediatomb is still coming up when I supposedly got rid of it.

Am I going to have to reinstall my entire Ubuntu install?

---

### Post by CharlesA on 2010-07-03
How did you remove mediatomb?

Do you have another web-based interface installed?

Run this and post the output:

```
sudo netstat -lpn
```

---

### Post by Captain Smiley Pants on 2010-07-03
Here ya go:

```
[sudo] password for coleman: 
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1283/cupsd      
tcp        0      0 127.0.0.1:38082         0.0.0.0:*               LISTEN      2155/beam.smp   
tcp6       0      0 :::80                   :::*                    LISTEN      1358/apache2    
tcp6       0      0 ::1:631                 :::*                    LISTEN      1283/cupsd      
tcp6       0      0 :::445                  :::*                    LISTEN      891/smbd        
tcp6       0      0 :::139                  :::*                    LISTEN      891/smbd        
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           770/avahi-daemon: r
udp        0      0 0.0.0.0:35320           0.0.0.0:*                           770/avahi-daemon: r
udp        0      0 192.168.0.3:137         0.0.0.0:*                           1932/nmbd       
udp        0      0 0.0.0.0:137             0.0.0.0:*                           1932/nmbd       
udp        0      0 192.168.0.3:138         0.0.0.0:*                           1932/nmbd       
udp        0      0 0.0.0.0:138             0.0.0.0:*                           1932/nmbd       
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     7315     1579/gnome-session  @/tmp/.ICE-unix/1579
unix  2      [ ACC ]     STREAM     LISTENING     4865     901/X               /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     7274     1619/ssh-agent      /tmp/ssh-YNlzJz1579/agent.1579
unix  2      [ ACC ]     STREAM     LISTENING     7316     1579/gnome-session  /tmp/.ICE-unix/1579
unix  2      [ ACC ]     STREAM     LISTENING     3051     1/init              @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     76973    3293/dbus-daemon    @/tmp/dbus-ag4rCoCPM4
unix  2      [ ACC ]     STREAM     LISTENING     7336     1626/gconfd-2       /tmp/orbit-coleman/linc-65a-0-30dd493d163d2
unix  2      [ ACC ]     STREAM     LISTENING     7569     1579/gnome-session  /tmp/orbit-coleman/linc-62b-0-71a7abd28784
unix  2      [ ACC ]     STREAM     LISTENING     7707     1561/gnome-keyring- /tmp/keyring-KBea1u/ssh
unix  2      [ ACC ]     STREAM     LISTENING     4429     770/avahi-daemon: r /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     5303     1232/bluetoothd     @/org/bluez/audio
unix  2      [ ACC ]     STREAM     LISTENING     65706    3107/hald           @/var/run/hald/dbus-yc4nkh74cy
unix  2      [ ACC ]     STREAM     LISTENING     65701    3107/hald           @/var/run/hald/dbus-ABNdiPq5sL
unix  2      [ ACC ]     STREAM     LISTENING     6851     1535/gnome-screensa /tmp/orbit-gdm/linc-5fe-0-1fd10d607c706
unix  2      [ ACC ]     STREAM     LISTENING     5217     1215/acpid          /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     7030     1561/gnome-keyring- /tmp/keyring-KBea1u/control
unix  2      [ ACC ]     STREAM     LISTENING     4864     901/X               @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     7711     1561/gnome-keyring- /tmp/keyring-KBea1u/pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     7718     1633/gnome-settings /tmp/orbit-coleman/linc-661-0-3d563bc6f2dc7
unix  2      [ ACC ]     STREAM     LISTENING     8383     1663/gnome-power-ma /tmp/orbit-coleman/linc-67f-0-3026a73f5c34d
unix  2      [ ACC ]     STREAM     LISTENING     7890     1644/metacity       /tmp/orbit-coleman/linc-66c-0-446af38a12577
unix  2      [ ACC ]     STREAM     LISTENING     5737     1360/apache2        /var/run/apache2/cgisock.1358
unix  2      [ ACC ]     STREAM     LISTENING     7946     1647/pulseaudio     /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     7949     1647/pulseaudio     /home/coleman/.pulse/492ecf704e3c7626a32ed3ba4c2ab1f2-runtime/native
unix  2      [ ACC ]     STREAM     LISTENING     5561     856/gdm-simple-slav @/tmp/gdm-session-gDascvHl
unix  2      [ ACC ]     STREAM     LISTENING     7998     1656/gconf-helper   /tmp/orbit-coleman/linc-678-0-4171a1f26aad1
unix  2      [ ACC ]     STREAM     LISTENING     5376     856/gdm-simple-slav @/tmp/gdm-greeter-ylNFUwJh
unix  2      [ ACC ]     STREAM     LISTENING     5260     1232/bluetoothd     /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     8017     1653/netbook-launch /tmp/orbit-coleman/linc-675-0-762501797ba17
unix  2      [ ACC ]     STREAM     LISTENING     8426     1660/nautilus       /tmp/orbit-coleman/linc-67c-0-43b9b02d8be2e
unix  2      [ ACC ]     STREAM     LISTENING     8461     1658/nm-applet      /tmp/orbit-coleman/linc-67a-0-4c7ae84cacb3b
unix  2      [ ACC ]     STREAM     LISTENING     8469     1657/maximus        /tmp/orbit-coleman/linc-679-0-22436e43b37f6
unix  2      [ ACC ]     STREAM     LISTENING     8486     1662/gnome-panel    /tmp/orbit-coleman/linc-67e-0-3bdd67a7c7e69
unix  2      [ ACC ]     STREAM     LISTENING     8492     1659/bluetooth-appl /tmp/orbit-coleman/linc-67b-0-1fc703ebc93ef
unix  2      [ ACC ]     STREAM     LISTENING     8583     1687/gnome-screensa /tmp/orbit-coleman/linc-68b-0-667ad798a37b3
unix  2      [ ACC ]     STREAM     LISTENING     8709     1694/bonobo-activat /tmp/orbit-coleman/linc-69e-0-67e2f6d192233
unix  2      [ ACC ]     STREAM     LISTENING     9049     1713/indicator-appl /tmp/orbit-coleman/linc-6b1-0-6a19e8c461c74
unix  2      [ ACC ]     STREAM     LISTENING     9107     1709/indicator-appl /tmp/orbit-coleman/linc-6ad-0-1826ba5b82cc2
unix  2      [ ACC ]     STREAM     LISTENING     9112     1706/window-picker- /tmp/orbit-coleman/linc-6aa-0-662deadf83577
unix  2      [ ACC ]     STREAM     LISTENING     9128     1712/notification-a /tmp/orbit-coleman/linc-6b0-0-22a8e28888e83
unix  2      [ ACC ]     STREAM     LISTENING     9194     1711/clock-applet   /tmp/orbit-coleman/linc-6af-0-591a1ed0c58c4
unix  2      [ ACC ]     STREAM     LISTENING     9211     1705/go-home-applet /tmp/orbit-coleman/linc-6a9-0-598ef255cc200
unix  2      [ ACC ]     STREAM     LISTENING     9334     1728/indicator-sess /tmp/orbit-coleman/linc-6c0-0-1820d7f514dd1
unix  2      [ ACC ]     STREAM     LISTENING     9358     1730/indicator-me-s /tmp/orbit-coleman/linc-6c2-0-376276ff42522
unix  2      [ ACC ]     STREAM     LISTENING     9701     1739/notify-osd     /tmp/orbit-coleman/linc-6cb-0-2af89fe7b7361
unix  2      [ ACC ]     STREAM     LISTENING     9985     1934/gnome-user-sha /tmp/orbit-coleman/linc-78e-0-66dc54ab8bf43
unix  2      [ ACC ]     STREAM     LISTENING     265004   5469/python         /tmp/orbit-coleman/linc-155d-0-277d7d4f608ed
unix  2      [ ACC ]     STREAM     LISTENING     10415    1966/evolution-data /tmp/orbit-coleman/linc-7ae-0-1dafa5122c185
unix  2      [ ACC ]     STREAM     LISTENING     11065    1986/empathy        /tmp/orbit-coleman/linc-7c2-0-3032022d98318
unix  2      [ ACC ]     STREAM     LISTENING     11632    2020/evolution-alar /tmp/orbit-coleman/linc-7e4-0-424b4adf1efa0
unix  2      [ ACC ]     STREAM     LISTENING     13948    2258/update-notifie /tmp/orbit-coleman/linc-8d2-0-72720a2cb02b3
unix  2      [ ACC ]     STREAM     LISTENING     65742    3106/gvfsd-http     /tmp/orbit-coleman/linc-c22-0-74e1a5ce5e251
unix  2      [ ACC ]     STREAM     LISTENING     76882    3286/gksu           /tmp/orbit-coleman/linc-cd6-0-416d40f8a3e64
unix  2      [ ACC ]     STREAM     LISTENING     76991    3295/gconfd-2       /tmp/orbit-root/linc-cdf-0-4ead023daf1ac
unix  2      [ ACC ]     STREAM     LISTENING     77016    3287/nautilus       /tmp/orbit-root/linc-cd7-0-6ffcdd51bcf34
unix  2      [ ACC ]     STREAM     LISTENING     334782   6630/firefox-bin    /tmp/orbit-coleman/linc-19e6-0-387d2f517e562
unix  2      [ ACC ]     STREAM     LISTENING     353356   6803/gnome-terminal /tmp/orbit-coleman/linc-1a93-0-11375e4e3a609
unix  2      [ ACC ]     STREAM     LISTENING     4304     747/dbus-daemon     /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     7287     1623/dbus-daemon    @/tmp/dbus-XIRcLYNPMx
unix  2      [ ACC ]     STREAM     LISTENING     206843   1283/cupsd          /var/run/cups/cups.sock

```

---

### Post by CharlesA on 2010-07-03
Looks like Apache is bound to the ipv6 address but not ipv4. I don't really deal with apache, but maybe there is a setting in the config to make it bind to the ipv4 address.

---

### Post by Captain Smiley Pants on 2010-07-04
Hey, I've "solved" this problem by installing Win 7. I know, I know, it's not a real solution but I kinda need it back on here for school anyway. But hey, I'll leave this thread open (It's up to mods to close it I guess) if anyone else wants to discuss setting up a http server for their PS3 or whatnot.

---

### Post by CharlesA on 2010-07-04
Just mark it as solved. Thread tools > mark as solved. :-)

---

