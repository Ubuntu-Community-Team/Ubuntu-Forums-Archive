---
title: "[SOLVED] Please explain the difference (netstat -l command and ufw status)"
date: 2008-05-14
forum: Security
---

### Post by RRFarFar on 2008-05-14
Hie to everybody
After reading some things about linux os in general, I know now that firewall service like UFW in Hardy is nothing but utility to close/open ports on system. 
Also by default Ubuntu has most ports closed, but if one installs new software, especially  with server behavior it opens ports automatically. 

If I use 'netstat -l' command
I get:
"Active Internet connections (only servers)

Proto Recv-Q Send-Q Local Address           Foreign Address         State      

tcp        0      0 *:dict                  *:*                     LISTEN     

tcp        0      0 localhost:mysql         *:*                     LISTEN     

tcp        0      0 localhost:ipp           *:*                     LISTEN     

tcp        0      0 localhost:smtp          *:*                     LISTEN     

udp        0      0 *:53521                 *:*                                

udp        0      0 *:bootpc                *:*                                

udp        0      0 *:mdns                  *:*                                

udp        0      0 rilxublts804ru-dell:ntp *:*                                

udp        0      0 localhost:ntp           *:*                                

udp        0      0 *:ntp                   *:*                                

udp6       0      0 fe80::219:d2ff:feaf:ntp [::]:*                             

udp6       0      0 ip6-localhost:ntp       [::]:*                             

udp6       0      0 [::]:ntp                [::]:*                             

Active UNIX domain sockets (only servers)

Proto RefCnt Flags       Type       State         I-Node   Path

unix  2      [ ACC ]     STREAM     LISTENING     13591    /var/run/dbus/system_bus_socket

unix  2      [ ACC ]     STREAM     LISTENING     14374    /var/run/samba/winbindd_privileged/pipe

unix  2      [ ACC ]     STREAM     LISTENING     13356    /var/run/acpid.socket

unix  2      [ ACC ]     STREAM     LISTENING     26869    /tmp/OSL_PIPE_1000_SingleOfficeIPC_1845c8d9182da8152129a54c91663a

unix  2      [ ACC ]     STREAM     LISTENING     13698    /var/run/avahi-daemon/socket

unix  2      [ ACC ]     STREAM     LISTENING     16000    /tmp/orbit-roman/linc-1976-0-48902640b0229

unix  2      [ ACC ]     STREAM     LISTENING     16331    /tmp/seahorse-P3tABS/S.gpg-agent

unix  2      [ ACC ]     STREAM     LISTENING     16374    /tmp/orbit-roman/linc-1976-0-7802b7fc72e8c

unix  2      [ ACC ]     STREAM     LISTENING     16378    /tmp/.ICE-unix/6518

unix  2      [ ACC ]     STREAM     LISTENING     16393    /tmp/orbit-roman/linc-19d5-0-78479113a6e8c

unix  2      [ ACC ]     STREAM     LISTENING     16398    /tmp/keyring-NWKB6V/socket

unix  2      [ ACC ]     STREAM     LISTENING     16400    /tmp/keyring-NWKB6V/ssh

unix  2      [ ACC ]     STREAM     LISTENING     16402    /tmp/keyring-NWKB6V/socket.pkcs11

unix  2      [ ACC ]     STREAM     LISTENING     16466    /tmp/orbit-roman/linc-19da-0-2de4b1143602c

unix  2      [ ACC ]     STREAM     LISTENING     20670    /tmp/.esd-1000/socket

unix  2      [ ACC ]     STREAM     LISTENING     20674    /tmp/pulse-roman/native

unix  2      [ ACC ]     STREAM     LISTENING     20715    /tmp/orbit-roman/linc-19e8-0-42374530e9440

unix  2      [ ACC ]     STREAM     LISTENING     14466    @/var/run/hald/dbus-wamXJCrq0r

unix  2      [ ACC ]     STREAM     LISTENING     20870    /tmp/orbit-roman/linc-19f1-0-7159a43dcfd2

unix  2      [ ACC ]     STREAM     LISTENING     21023    /tmp/orbit-roman/linc-19f8-0-32b2c60acb30

unix  2      [ ACC ]     STREAM     LISTENING     14004    /var/run/cups/cups.sock

unix  2      [ ACC ]     STREAM     LISTENING     21082    /tmp/orbit-roman/linc-19f9-0-32b2c60ecd85

unix  2      [ ACC ]     STREAM     LISTENING     22172    /tmp/orbit-roman/linc-1a3a-0-2407461d5b479

unix  2      [ ACC ]     STREAM     LISTENING     22290    /tmp/orbit-roman/linc-1a3d-0-31bf88a57255a

unix  2      [ ACC ]     STREAM     LISTENING     22300    /tmp/orbit-roman/linc-1a3b-0-31bf88a5753ba

unix  2      [ ACC ]     STREAM     LISTENING     22309    /tmp/orbit-roman/linc-1a4b-0-5d258fcc76f6b

unix  2      [ ACC ]     STREAM     LISTENING     14372    /tmp/.winbindd/pipe

unix  2      [ ACC ]     STREAM     LISTENING     23094    /tmp/orbit-roman/linc-1a56-0-3b76d12c4bcd3

unix  2      [ ACC ]     STREAM     LISTENING     15411    /tmp/.X11-unix/X0

unix  2      [ ACC ]     STREAM     LISTENING     15957    /tmp/ssh-cMCjde6518/agent.6518

unix  2      [ ACC ]     STREAM     LISTENING     22343    /tmp/orbit-roman/linc-1a53-0-5d258fcd3996c

unix  2      [ ACC ]     STREAM     LISTENING     15993    /tmp/orbit-roman/linc-19ca-0-49f923093211

unix  2      [ ACC ]     STREAM     LISTENING     22467    /tmp/orbit-roman/linc-1a03-0-214dc782e9d87

unix  2      [ ACC ]     STREAM     LISTENING     22553    /tmp/orbit-roman/linc-1a78-0-49247232ea2

unix  2      [ ACC ]     STREAM     LISTENING     22720    /tmp/orbit-roman/linc-1a5d-0-1c7117f665875

unix  2      [ ACC ]     STREAM     LISTENING     22825    /tmp/orbit-roman/linc-1a93-0-32ae1ebf58f4

unix  2      [ ACC ]     STREAM     LISTENING     22865    /tmp/orbit-roman/linc-1a59-0-1681e1b54f45e

unix  2      [ ACC ]     STREAM     LISTENING     23994    /tmp/orbit-roman/linc-1b75-0-e08c51e66184

unix  2      [ ACC ]     STREAM     LISTENING     16418    @/tmp/dbus-EcczvSuMb5

unix  2      [ ACC ]     STREAM     LISTENING     23459    /tmp/orbit-roman/linc-1a43-0-5b2075abacb6e

unix  2      [ ACC ]     STREAM     LISTENING     24267    /tmp/orbit-roman/linc-1b95-0-f9489be54737

unix  2      [ ACC ]     STREAM     LISTENING     24487    /tmp/orbit-roman/linc-1bae-0-638cbacf8c73a

unix  2      [ ACC ]     STREAM     LISTENING     24495    /tmp/orbit-roman/linc-1bab-0-638cbacf9edc2

unix  2      [ ACC ]     STREAM     LISTENING     24515    /tmp/orbit-roman/linc-1ba5-0-638cbacfa63be

unix  2      [ ACC ]     STREAM     LISTENING     24535    /tmp/orbit-roman/linc-1ba8-0-638cbacfb29a6

unix  2      [ ACC ]     STREAM     LISTENING     24609    /tmp/orbit-roman/linc-1bb4-0-638cbacfd8a70

unix  2      [ ACC ]     STREAM     LISTENING     24905    /tmp/orbit-roman/linc-1bf0-0-7e7a5d18cb665

unix  2      [ ACC ]     STREAM     LISTENING     26861    /tmp/orbit-roman/linc-1dae-0-3516db5564003

unix  2      [ ACC ]     STREAM     LISTENING     15331    /var/run/gdm_socket

unix  2      [ ACC ]     STREAM     LISTENING     13795    /var/run/mysqld/mysqld.sock

unix  2      [ ACC ]     STREAM     LISTENING     27345    /tmp/orbit-roman/linc-1df8-0-1e35f25a8d9e

unix  2      [ ACC ]     STREAM     LISTENING     14484    @/var/run/hald/dbus-m"

If I use 'sudo ufw status' command

Firewall loaded

To                         Action  From
--                         ------  ----
3478:udp                   ALLOW   Anywhere
3479:udp                   ALLOW   Anywhere
1720:tcp                   ALLOW   Anywhere

===========================================
Please explain the difference, and how can I close most of these programs with UFW. If would be great if someone could juts give me a hint of how manage so many connections.
THank in advance

---

### Post by cdenley on 2008-05-14
"netstat -l" lists all network connections you are listening for, including unix sockets which are not accessible through the network. If you want to show only tcp listeners, you could use "netstat -lnt". Whether the traffic on that port is being filtered or not, the server will still be listening, and it will still show with netstat. I think your firewall is already configured the way you expect.

[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

If you want to test how well your firewall is working, you should use this command.
```

nmap <my ip>

```
Replace <my ip> with your IP address. If you scan localhost or 127.0.0.1, your results will probably not reflect how your firewall is working. I think you might have to try this command from another computer since ufw won't seem to filter traffic from your own computer.

If you want a front-end for iptables (linux's firewall) that gives you more control or options, and are using the desktop version, you can use firestarter instead.
```

sudo ufw disable
sudo apt-get install firestarter

```
System>Administration>Firestarter

---

### Post by salvador_luna on 2008-05-14
Cdenley:
Do you know if that option to install firestarter disabling uwf would help to avoid problems when running firestarter?

---

### Post by RRFarFar on 2008-05-15
> **cdenley said:**
> 
```

sudo ufw disable
sudo apt-get install firestarter

```
System>Administration>Firestarter

Thanks very much, I would gladly use Firestarter, but after installing it; it is unusable. The button which adds rules for example is grey and non-clikable. Maybe you know how to fix it????
Any hint please, because nobody know really, I am trying to find solution for that long time ago

---

### Post by RRFarFar on 2008-05-15
Sorry I have to right in window there)))) DO not bother answering. I have asked stupid question here)))))))))

---

### Post by cdenley on 2008-05-15
> **salvador_luna said:**
> Cdenley:
Do you know if that option to install firestarter disabling uwf would help to avoid problems when running firestarter?

I think that if you have them both enabled, both of their rules will apply, but neither will see the other's rules. I never tried.

> 
Sorry I have to right in window there)))) DO not bother answering. I have asked stupid question here))))))))) 

You mean you were under the policy tab, and you can't click "Add Rule" until you select the listbox under "allow connections from host" or "allow service|Port|For"? I think someone else made the same mistake in another thread, but I didn't understand at the time.

---

### Post by RRFarFar on 2008-05-15
Yes))) It was to hard for me, to think of right clicking there))) Anyway it is sorted now. I asked the same question in another thread, so the help came from two sides)))
I getting better at using Linux. I like it very much except for multimedia. I deleted beta firefox 3, and installed firefox 2 which has all my favorite extension, but there is no mplayer plugin for ff2, so online videos are not really embedded. So I use media player connectivity extension that plays videos in separate windows, that is the only thing I can complain about)))

---

