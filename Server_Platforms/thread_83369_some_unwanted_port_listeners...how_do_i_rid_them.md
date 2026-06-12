---
title: "some unwanted port listeners...how do i rid them"
date: 2005-10-28
forum: Server Platforms
---

### Post by herot on 2005-10-28
ive got:
```
Starting nmap 3.81 ( http://www.insecure.org/nmap/ ) at 2005-10-28 13:56 EDT
Interesting ports on localhost.localdomain (127.0.0.1):
(The 1658 ports scanned but not shown below are in state: closed)
PORT     STATE SERVICE
22/tcp   open  ssh
1025/tcp open  NFS-or-IIS
1026/tcp open  LSA-or-nterm
5901/tcp open  vnc-1
6001/tcp open  X11:1

Nmap finished: 1 IP address (1 host up) scanned in 1.069 seconds

```
are the services running on 1025 and 1026 needed??? if not, how do i stop NFS and LSA from starting on boot??

---

### Post by Spudgun on 2005-10-29
Are those ports actually listening to the outside and not just local? Use an internet based scanner like Shields Up to find out.

---

### Post by NewWithoutClue on 2005-10-29
Don't know if you already knew about this, but a simple

netstat -l -np -p

will show you the processes owning the port(s).

( be root )

Regards,
Paul.

---

### Post by stimpack on 2005-10-30
mark@desktop:~$ sudo lsof -i
COMMAND  PID USER   FD   TYPE DEVICE SIZE NODE NAME
sshd    8375 root    3u  IPv6  10047       TCP *:ssh (LISTEN)
mark@desktop:~$ ls -l /etc/init.d/sshd
ls: /etc/init.d/sshd: No such file or directory
mark@desktop:~$ ls -l /etc/init.d/ssh
-rwxr-xr-x  1 root root 2016 2005-09-23 13:13 /etc/init.d/ssh
mark@desktop:~$ sudo chmod a-x /etc/init.d/ssh
mark@desktop:~$ tada!
bash: tada!: command not found

is another way.

---

### Post by HJThis on 2005-10-30
Hey,To all

@herot

The services running on 1025 and 1026
had me going mad so what i found was

that by doing 

sudo apt-get remove cupsys

removed the HP printer stuff that i did not need any way

once i used sudo apt-get remove cupsys did a reboot
did both nmap all clean also did netstat all clean

at last i killed them both 1025 & 1026

Best of luck;)

---

### Post by herot on 2005-10-31
thanks guys i think these suggestions will help alot!
i will try them today and post the results...

---

### Post by LordHunter317 on 2005-10-31
[QUOTE=stimpack]
mark@desktop:~$ sudo chmod a-x /etc/init.d/ssh[/quote]**No, don't *ever* disable services this way**.  Use update-rc.d or wajig or some other tool designed to do service management.  Don't ever just remove the executable bit on an initscript.

It won't work the way you want it to anyway, dpkg(8) will undo it on upgrade.

To the OP,
I seriously doubt those services were world-accessible.  You should **never** nmap scan localhost, as it tells you nothing useful.

---

### Post by herot on 2005-10-31
LordHunter317> You should never nmap scan localhost, as it tells you nothing useful.
it wont tell me what ports are open on my computer?? also i have found it useful just to tell me if my ssh,ftp,vnc, etc... are up and listening...especially when im trying to vnc in from another computer (windows) that doesnt have nmap installed... what do you mean by world accessible? i am on a lan here and i could see them from a different computer(via nmap) here... also LordHunter317 what about  HJThis's solution? would it work? i dont need print serving on my pc (that is what cupsys is right?)

---

### Post by LordHunter317 on 2005-10-31
[QUOTE=herot]LordHunter317
it wont tell me what ports are open on my computer??[/quote]Yes, but it also tells you what ports are accessibly locally only.

A server can set itself up so it can only be accessed by the local computer.  Nmap cannot differentiate between ports that are locally-accessible and globally-accessible.

OTOH, netstat can do that, while revealing the same information as nmap im this case.

>  what do you mean by world accessible?As in, computers other than the one in question can access them.

> also LordHunter317 what about  HJThis's solution? would it work? i dont need print serving on my pc (that is what cupsys is right?)I wouldn't know without netstat output.  And you need cupsys if you want to print, period.

---

### Post by herot on 2005-10-31
"*sigh* ok! ill learn how to use netstat...

here is my output from netstat:
```

root@slasheru:/ # netstat -l -np -p
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name  
tcp        0      0 127.0.0.1:1025          0.0.0.0:*               LISTEN     6646/hpiod         
tcp        0      0 127.0.0.1:1026          0.0.0.0:*               LISTEN     6703/python        
tcp        0      0 0.0.0.0:6001            0.0.0.0:*               LISTEN     7360/Xrealvnc      
tcp6       0      0 :::5901                 :::*                    LISTEN     7360/Xrealvnc      
tcp6       0      0 :::22                   :::*                    LISTEN     6920/sshd          
udp        0      0 0.0.0.0:68              0.0.0.0:*                          5733/dhclient3     
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     11463    7519/gnome-netstatu /tmp/orbit-herot/linc-1d5f-0-1441421c5a028
unix  2      [ ACC ]     STREAM     LISTENING     11472    7521/mixer_applet2  /tmp/orbit-herot/linc-1d61-0-1441421c6532e
unix  2      [ ACC ]     STREAM     LISTENING     7526     6146/dbus-daemon    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     11493    7528/cpufreq-applet /tmp/orbit-herot/linc-1d68-0-1441421c966bf
unix  2      [ ACC ]     STREAM     LISTENING     11512    7525/multiload-appl /tmp/orbit-herot/linc-1d65-0-1441421ce576e
unix  2      [ ACC ]     STREAM     LISTENING     9627     6940/sdpd           /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     11550    7523/clock-applet   /tmp/orbit-herot/linc-1d63-0-30483801b8b4c
unix  2      [ ACC ]     STREAM     LISTENING     10970    7478/update-notifie /tmp/orbit-herot/linc-1d36-0-5673be25c89e2
unix  2      [ ACC ]     STREAM     LISTENING     10448    7399/gconfd-2       /tmp/orbit-herot/linc-1ce7-0-55b85ac1a91dc
unix  2      [ ACC ]     STREAM     LISTENING     10673    7401/gnome-keyring- /tmp/keyring-KVxgGn/socket
unix  2      [ ACC ]     STREAM     LISTENING     8937     6569/gdm            /tmp/.gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     7543     6160/hald           @/tmp/hald-local/dbus-4g7FAQcTQR
unix  2      [ ACC ]     STREAM     LISTENING     10743    7413/gam_server     @/tmp/fam-herot-
unix  2      [ ACC ]     STREAM     LISTENING     11074    7489/wnck-applet    /tmp/orbit-herot/linc-1d41-0-1d6bb694d5b22
unix  2      [ ACC ]     STREAM     LISTENING     10388    7360/Xrealvnc       /tmp/.X11-unix/X1
unix  2      [ ACC ]     STREAM     LISTENING     12455    7930/esd            /tmp/.esd-0/socket
unix  2      [ ACC ]     STREAM     LISTENING     11119    7497/geyes_applet2  /tmp/orbit-herot/linc-1d49-0-6b74798a2974b
unix  2      [ ACC ]     STREAM     LISTENING     10693    7403/esd            /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     10951    7463/nautilus       /tmp/orbit-herot/linc-1d27-0-3a30e6f72aed0
unix  2      [ ACC ]     STREAM     LISTENING     10708    7405/bonobo-activat /tmp/orbit-herot/linc-1ced-0-8eb0878aade
unix  2      [ ACC ]     STREAM     LISTENING     10729    7407/gnome-settings /tmp/orbit-herot/linc-1cef-0-43e26e3812d1e
unix  2      [ ACC ]     STREAM     LISTENING     10854    7456/metacity       /tmp/orbit-herot/linc-1d20-0-19dedde38a7ca
unix  2      [ ACC ]     STREAM     LISTENING     10881    7465/gnome-volume-m /tmp/orbit-herot/linc-1d29-0-8497f91e9853
unix  2      [ ACC ]     STREAM     LISTENING     10912    7461/gnome-panel    /tmp/orbit-herot/linc-1d25-0-3a30e6f03b9d8
unix  2      [ ACC ]     STREAM     LISTENING     11155    7499/trashapplet    /tmp/orbit-herot/linc-1d4b-0-6b74798af163a
unix  2      [ ACC ]     STREAM     LISTENING     11044    7487/gnome-vfs-daem /tmp/orbit-herot/linc-1d3f-0-23a32c176bb93
unix  2      [ ACC ]     STREAM     LISTENING     10664    7362/x-session-mana /tmp/.ICE-unix/7362
unix  2      [ ACC ]     STREAM     LISTENING     10413    7392/ssh-agent      /tmp/ssh-MKuwpe7362/agent.7362
unix  2      [ ACC ]     STREAM     LISTENING     11430    7517/notification-a /tmp/orbit-herot/linc-1d5d-0-1441421cb33c
unix  2      [ ACC ]     STREAM     LISTENING     7449     6096/acpid          /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     10455    7362/x-session-mana /tmp/orbit-herot/linc-1cc2-0-b9872f7ab7ac
unix  2      [ ACC ]     STREAM     LISTENING     11187    7503/mapping-daemon /tmp/mapping-herot
unix  2      [ ACC ]     STREAM     LISTENING     10418    7396/dbus-daemon    @/tmp/dbus-ml3l7VEz8P
unix  2      [ ACC ]     STREAM     LISTENING     9151     6621/X              /tmp/.X11-unix/X0
root@slasheru:/ #

```
does the "0.0.0.0:*" mean that these ports are NOT world accessible???

---

### Post by silverjsn on 2005-11-18
On your "Foreign Address", Whatever other then "localhost" or "127.0.0.1" is listening to outside.

---

### Post by omair.majid on 2005-12-12
This is what i get

```

omair@LinuxMachine:~$ netstat -l
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 localhost.localdom:1025 *:*                     LISTEN
tcp        0      0 localhost.localdom:1026 *:*                     LISTEN
udp        0      0 *:bootpc                *:*

```
Does this mean that the third item (using udp) is not listening and i can ignore it totally?

---

