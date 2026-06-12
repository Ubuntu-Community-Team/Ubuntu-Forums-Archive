---
title: "Transmission-daemon remote access"
date: 2009-06-27
forum: Server Platforms
---

### Post by Jeztastic on 2009-06-27
Hi,

Transmission-daemon has stopped allowing me remote access. My ip has not changer, nor has my settings.json, which is located here:

```
home/user/.config/transmission-daemon
```

When I attempt remote access I get this error message.

```
403: Forbidden

Unauthorized IP Address.

Either disable the IP address whitelist or add your address to it.

If you're editing settings.json, see the 'rpc-whitelist' and 'rpc-whitelist-enabled' entries.

If you're still using ACLs, use a whitelist instead. See the transmission-daemon manpage for details.
```

This is my settings.json

```
{
    "alt-speed-down": 50, 
    "alt-speed-enabled": false, 
    "alt-speed-time-begin": 540, 
    "alt-speed-time-day": 127, 
    "alt-speed-time-enabled": false, 
    "alt-speed-time-end": 1020, 
    "alt-speed-up": 50, 
    "bind-address-ipv4": "0.0.0.0", 
    "bind-address-ipv6": "::", 
    "blocklist-enabled": false, 
    "download-dir": "\/home\/jez\/downloads", 
    "download-limit": 10, 
    "download-limit-enabled": 0, 
    "encryption": 1, 
    "lazy-bitfield-enabled": true, 
    "max-peers-global": 200, 
    "message-level": 2, 
    "open-file-limit": 32, 
    "peer-limit-global": 240, 
    "peer-limit-per-torrent": 60, 
    "peer-port": 16868, 
    "peer-port-random-enabled": 0, 
    "peer-port-random-high": 65535, 
    "peer-port-random-low": 1024, 
    "peer-port-random-on-start": false, 
    "peer-socket-tos": 0, 
    "pex-enabled": true, 
    "port-forwarding-enabled": false, 
    "preallocation": 1, 
    "proxy": "", 
    "proxy-auth-enabled": false, 
    "proxy-auth-password": "", 
    "proxy-auth-username": "", 
    "proxy-enabled": false, 
    "proxy-port": 80, 
    "proxy-type": 0, 
    "ratio-limit": 2.000000, 
    "ratio-limit-enabled": false, 
    "rpc-authentication-required": false, 
    "rpc-bind-address": "0.0.0.0", 
    "rpc-enabled": true, 
    "rpc-password": "{1cc72c39f8a3d1c23e81a6ea37f72f2d0085399dKxhyBIwU", 
    "rpc-port": 9091, 
    "rpc-username": "jez", 
    "rpc-whitelist": "127.0.0.1,192.168.*.*,192.168.1.65,192.168.1.73", 
    "rpc-whitelist-enabled": false, 
    "speed-limit-down": 100, 
    "speed-limit-down-enabled": false, 
    "speed-limit-up": 100, 
    "speed-limit-up-enabled": false, 
    "upload-limit": 20, 
    "upload-limit-enabled": 0, 
    "upload-slots-per-torrent": 14
}
```

Please help, this is driving me up the wall!

Jez

---

### Post by TwiceOver on 2009-06-27
What if you change rpc-whitelist-enabled to true?  Then does it allow connection to the IPs in your rpc-whitelist?

---

### Post by Jeztastic on 2009-06-27
> **TwiceOver said:**
> What if you change rpc-whitelist-enabled to true?  Then does it allow connection to the IPs in your rpc-whitelist?

Nope, just tried that. 

I should add, the transmission is clearly working, and the whitelist is loading OK.

```
jez@mediaserver:~$ transmission-daemon -f
[15:35:11.251] Couldn't bind port 16868 on 0.0.0.0: Address already in use
[15:35:11.252] Couldn't bind port 16868 on ::: Address already in use
[15:35:11.253] RPC Server: Adding address to whitelist: 127.0.0.1
[15:35:11.253] RPC Server: Adding address to whitelist: 192.168.*.*
[15:35:11.254] RPC Server: Adding address to whitelist: 192.168.1.65
[15:35:11.254] RPC Server: Adding address to whitelist: 192.168.1.73
[15:35:11.254] RPC Server: Adding address to whitelist: *.*.*.*
[15:35:11.255] RPC Server: Serving RPC and Web requests on port 9091
[15:35:11.255] RPC Server: Whitelist enabled
[15:35:11.256] Transmission 1.71 (8646) started
[15:35:11.586] Loaded 6 torrents
[15:35:11.647] Rudyard_Kipling.Jungle_Book.[1994].BBC_Radio_drama.ogg.radioCat: Got 12 peers from tracker
[15:35:12.778] The Hound of the Baskervilles by Sir Arthur Conan Doyle - BBC Radio: Got 3 peers from tracker

```

---

### Post by TwiceOver on 2009-06-27
> [15:35:11.251] Couldn't bind port 16868 on 0.0.0.0: Address already in use
[15:35:11.252] Couldn't bind port 16868 on ::: Address already in use


Does netstat -a show the port open and listening?  The startup shows that the port isn't binding to any address, which is probably why you can't connect to it.

EDIT:  I guess you wouldn't even get the 403 message if the port wasn't open.  Hrm...

---

### Post by Jeztastic on 2009-06-27
> **TwiceOver said:**
> Does netstat -a show the port open and listening?  The startup shows that the port isn't binding to any address, which is probably why you can't connect to it.

EDIT:  I guess you wouldn't even get the 403 message if the port wasn't open.  Hrm...

```
:~$ netstat -a
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:9090                  *:*                     LISTEN     
tcp        0      0 *:9091                  *:*                     LISTEN     
tcp        0      0 *:16868                 *:*                     LISTEN     
tcp        0      0 localhost:9092          *:*                     LISTEN     
tcp        0      0 *:9000                  *:*                     LISTEN     
tcp        0      0 localhost:mysql         *:*                     LISTEN     
tcp        0      0 *:netbios-ssn           *:*                     LISTEN     
tcp        0      0 *:webmin                *:*                     LISTEN     
tcp        0      0 *:51413                 *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 *:3483                  *:*                     LISTEN     
tcp        0      0 *:microsoft-ds          *:*                     LISTEN     
tcp        0      0 192.168.1.73:54056      79.107.238.7:6112       ESTABLISHED
tcp        0      0 192.168.1.73:36262      host59-169-dynami:61676 ESTABLISHED
tcp        0      0 192.168.1.73:47775      ip216-239-81-173.:32565 ESTABLISHED
tcp        0      0 192.168.1.73:45523      089-101-095253.nt:61747 ESTABLISHED
tcp        0      0 192.168.1.73:58795      89.131.242.26:56622     ESTABLISHED
tcp        0      0 localhost:9092          localhost:34627         ESTABLISHED
tcp        0      0 192.168.1.73:59578      host50-135-dynami:57066 ESTABLISHED
tcp        0      0 192.168.1.73:41457      net-93-65-100-173:63308 ESTABLISHED
tcp        0      0 192.168.1.73:3483       JezsSqueezebox:44366    ESTABLISHED
tcp        0      0 192.168.1.73:47211      host81-157-213-22:45122 ESTABLISHED
tcp        0      0 192.168.1.73:37246      host86-147-47-67.:22796 ESTABLISHED
tcp        0      0 localhost:34627         localhost:9092          ESTABLISHED

```

Does that help?

---

### Post by lweel on 2009-09-04
Hello Jeztastic,

I installed transmission-daemon on Ubuntu karmic server and also experienced the:

"403: Forbidden
Unauthorized IP Address.
Either disable the IP address whitelist or add your address to it.
..." message.

I solved it by placing the settings.json file to my local .config directory and tweaked some file owner and permission settings. Also I had to tweak the permissions of the download/ and info/ directory.

So:
> sudo cp /etc/transmission-daemon/settings.json ~/.config/transmission-daemon/
> cd ~/.config/transmission-daemon
> sudo chown debian-transmission:debian-transmission settings.json
> sudo chmod ugo+rwx settings.json
> sudo chmod u-s downloads info
> sudo chmod ugo+rwx downloads info

This in not a very save solution. All users can acces the settings.json file. But it is a workaround.
For some mystical reason the u+s permission will not give access to the transmission-deamon. This is probably a bug in the installation package.

If someone knows how to operate this with the u+s permission in place. Please keep me posted.

I hope this will help you futher.

---

### Post by hongan on 2009-10-18
Try change these

    "rpc-authentication-required":[COLOR="DarkRed"]true[/COLOR], 
    "rpc-bind-address": "0.0.0.0", 
    "rpc-enabled": true, 
    "rpc-password": "{1cc72c39f8a3d1c23e81a6ea37f72f2d0085399dKxhyBIwU", 
    "rpc-port": 9091, 
    "rpc-username": "jez", 
    "rpc-whitelist": "127.0.0.1,192.168.*.*,192.168.1.65,192.168.1.73", 
    "rpc-whitelist-enabled": [COLOR="DarkRed"]true[/COLOR], 
    "speed-limit-down": 100, 
    "speed-limit-down-enabled": false, 
    "speed-limit-up": 100, 
    "speed-limit-up-enabled": false, 
    "upload-limit": 20, 
    "upload-limit-enabled": 0, 
    "upload-slots-per-torrent": 14

and make sure your transmission-daemon will load this config file when it start up.

---

### Post by eaidoido on 2010-03-14
the latest reply didnt work for me. its strange because my configuration was working just fine before. the following command is what I used initially. any other suggestions?


sudo screen transmission-daemon -er -g /home/username/.config/transmission-daemon -c /home/username/torrents/ -p 9091 -f -T -a 192.168.2.*

---

### Post by eaidoido on 2010-04-13
the following gets me up and running with the transmission webgui:

```
screen transmission-daemon --bind-address-ipv4 192.168.2.6 -p 9091 -f -T -a 192.168.2.* -c /home/name/torrents/
```

seems like the only difference was that i set the bind address. 
looking at my settings.json file however these settings are not reflected which makes me think that perhaps the file isnt being used or just wasnt up to date.

also, i use screen so i can simply close the terminal to that server when im done.

---

### Post by elico on 2010-08-14
the problem comes from another place.

the transmission deamon runing using the debian-transmission user and group.
if you will try to run the trasmission-daemon using any user it will create .config dir in your user directory.

what you need to do is stop the daemon using

```
/etc/init.d/transmission-daemon stop
```then edit the settings file 
```
/etc/etc/transmission-daemon/settings.json
```run the daemon using

```
/etc/init.d/transmission-daemon stop
```if you want the daemon to have right to the download directory what every it is you should add him to the group that allowed read/write permissions or make the transmission-daemon owner of the directory.


edit:

found out that the directory that holds the settings is:

```
/var/lib/transmission-daemon/info
```i

---

### Post by kezeb on 2010-09-12
damn right man you got it
this freakin thing has been driving me crazy 'cause when you install it, it also creates another settings.json in /home/user/transmission-daemon/ so no matter how many times i changed it, it wasn't working for me, thank you!!!!!!!!!!!!!

---

### Post by masque7 on 2011-07-03
Hi I can confirm [post #10]("http://ubuntuforums.org/showpost.php?p=9720068&postcount=10") counters the issues I was having with settings.json not remembering the setting I was saving (setting whitelist to "*")

---

