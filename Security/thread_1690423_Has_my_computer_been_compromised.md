---
title: "Has my computer been compromised?"
date: 2011-02-18
forum: Security
---

### Post by chris_safrica on 2011-02-18
Hi, 

Today I got home from work and it seemed as if somebody had been at my computer. There were applications open (like skype) and chrome had been opened and was looking for new settings. No one had access to my computer. I am therefore that somehow my laptop has been compromised. I am a newbie but had a look around and ran rkhunter. 

I then got some warnings also it seemed to say not checking for trojans:

Please can you advise. Whether my laptop has been compromised and if so what should I do about it. 

Thanks in advance, 

Log below. 

```
]
[17:27:43] Performing trojan specific checks
[17:27:43] Info: Starting test name 'trojans'
[17:27:43]   Checking for enabled inetd services             [ Skipped ]
[17:27:43] Info: Check skipped - file '/etc/inetd.conf' does not exist.
[17:27:43]
[17:27:43]   Performing check for enabled xinetd services
[17:27:43]   Checking for enabled xinetd services            [ Skipped ]
[17:27:43] Info: Check skipped - file '/etc/xinetd.conf' does not exist.
[17:27:43] Info: Apache backdoor check skipped: Apache modules and configuration directories not found.
[17:27:43]
[17:27:43] Performing Linux specific checks
[17:27:43] Info: Starting test name 'os_specific'
[17:27:43]   Checking loaded kernel modules                  [ OK ]
[17:27:43] Info: Using modules pathname of '/lib/modules/2.6.32-28-generic'
[17:27:43]   Checking kernel module names                    [ OK ]
[17:27:43]
[17:27:43] Checking the network...
[17:27:43] Info: Starting test name 'network'
[17:27:43] Info: Starting test name 'ports'
[17:27:43]
[17:27:43] Performing check for backdoor ports
[17:27:44]   Checking for TCP port 1524                      [ Not found ]
[17:27:44]   Checking for TCP port 1984                      [ Not found ]
[17:27:44]   Checking for UDP port 2001                      [ Not found ]
[17:27:44]   Checking for TCP port 2006                      [ Not found ]
[17:27:44]   Checking for TCP port 2128                      [ Not found ]
[17:27:44]   Checking for TCP port 6666                      [ Not found ]
[17:27:44]   Checking for TCP port 6667                      [ Not found ]
[17:27:44]   Checking for TCP port 6668                      [ Not found ]
[17:27:44]   Checking for TCP port 6669                      [ Not found ]
[17:27:44]   Checking for TCP port 7000                      [ Not found ]
[17:27:45]   Checking for TCP port 13000                     [ Not found ]
[17:27:45]   Checking for TCP port 14856                     [ Not found ]
[17:27:45]   Checking for TCP port 25000                     [ Not found ]
[17:27:45]   Checking for TCP port 29812                     [ Not found ]
[17:27:45]   Checking for TCP port 31337                     [ Not found ]
[17:27:45]   Checking for TCP port 33369                     [ Not found ]
[17:27:45]   Checking for TCP port 47107                     [ Not found ]
[17:27:45]   Checking for TCP port 47018                     [ Not found ]
[17:27:45]   Checking for TCP port 60922                     [ Not found ]
[17:27:45]   Checking for TCP port 62883                     [ Not found ]
[17:27:46]   Checking for TCP port 65535                     [ Not found ]
[17:27:46]
[17:27:46] Performing checks on the network interfaces
[17:27:46] Info: Starting test name 'promisc'
[17:27:46]   Checking for promiscuous interfaces             [ None found ]
[17:27:46]
[17:27:46] Info: Test 'packet_cap_apps' disabled at users request.
[17:27:47]
[17:27:47] Checking the local host...
[17:27:47] Info: Starting test name 'local_host'
[17:27:47]
[17:27:47] Performing system boot checks
[17:27:47] Info: Starting test name 'startup_files'
[17:27:47]   Checking for local host name                    [ Found ]
[17:27:47] Info: Starting test name 'startup_malware'
[17:27:47]   Checking for system startup files               [ Found ]
[17:27:47]   Checking system startup files for malware       [ None found ]
[17:27:47]
[17:27:47] Performing group and account checks
[17:27:47] Info: Starting test name 'group_accounts'
[17:27:47]   Checking for passwd file                        [ Found ]
[17:27:47] Info: Found password file: /etc/passwd
[17:27:47]   Checking for root equivalent (UID 0) accounts   [ None found ]
[17:27:47] Info: Found shadow file: /etc/shadow
[17:27:47]   Checking for passwordless accounts              [ None found ]
[17:27:47] Info: Starting test name 'passwd_changes'
[17:27:47]   Checking for passwd file changes                [ None found ]
[17:27:47] Info: Starting test name 'group_changes'
[17:27:48]   Checking for group file changes                 [ None found ]
[17:27:48]   Checking root account shell history files       [ OK ]
[17:27:48]
[17:27:48] Performing system configuration file checks
[17:27:48] Info: Starting test name 'system_configs'
[17:27:48]   Checking for SSH configuration file             [ Not found ]
[17:27:48]   Checking for running syslog daemon              [ Found ]
[17:27:48]   Checking for syslog configuration file          [ Found ]
[17:27:48] Info: Found syslog configuration file: /etc/rsyslog.conf
[17:27:48]   Checking if syslog remote logging is allowed    [ Not allowed ]
[17:27:48]
[17:27:48] Performing filesystem checks
[17:27:48] Info: Starting test name 'filesystem'
[17:27:48] Info: SCAN_MODE_DEV set to 'THOROUGH'
[17:27:48]   Checking /dev for suspicious file types         [ Warning ]
[17:27:48] Warning: Suspicious file types found in /dev:
[17:27:48]          /dev/shm/pulse-shm-2796756562: data
[17:27:48]          /dev/shm/pulse-shm-4210084375: data
[17:27:48]          /dev/shm/pulse-shm-1097099770: data
[17:27:48]   Checking for hidden files and directories       [ Warning ]
[17:27:48] Warning: Hidden directory found: /etc/.java
[17:27:48] Warning: Hidden directory found: /dev/.udev
[17:27:48] Warning: Hidden directory found: /dev/.initramfs
[17:27:48] Warning: Hidden directory found: /bin/.gnome-desktop
[17:27:48] Warning: Hidden directory found: /usr/sbin/.gnome-desktop
[17:27:50]
[17:27:50] Info: Test 'apps' disabled at users request.
[17:27:50]
[17:27:50] System checks summary
[17:27:50] =====================
[17:27:50]
[17:27:50] File properties checks...
[17:27:50] Files checked: 132
[17:27:50] Suspect files: 0
[17:27:50]
[17:27:50] Rootkit checks...
[17:27:50] Rootkits checked : 242
[17:27:50] Possible rootkits: 0
[17:27:50]
[17:27:50] Applications checks...
[17:27:50] All checks skipped
[17:27:50]
[17:27:50] The system checks took: 1 minute and 4 seconds
```

---

### Post by cariboo on 2011-02-18
You have the usual false positives, check /var/log/auth.log to see if anyone has logged in. look for something similar to this:

```
Feb 18 09:01:07 chilanko gdm-session-worker[1219]: pam_unix(gdm:session): session opened for user cariboo by (uid=0)
```

---

### Post by chris_safrica on 2011-02-18
This is my auth.log

Keep in mind as well that I am playing around with filezilla. Otherwise does this look normal?


Feb 18 00:17:01 chris-laptop CRON[5496]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 18 00:17:01 chris-laptop CRON[5496]: pam_unix(cron:session): session closed for user root
Feb 18 01:17:01 chris-laptop CRON[6147]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 18 01:17:01 chris-laptop CRON[6147]: pam_unix(cron:session): session closed for user root
Feb 18 02:17:01 chris-laptop CRON[6854]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 18 02:17:01 chris-laptop CRON[6854]: pam_unix(cron:session): session closed for user root
Feb 18 03:17:01 chris-laptop CRON[7487]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 18 03:17:01 chris-laptop CRON[7487]: pam_unix(cron:session): session closed for user root
Feb 18 04:17:01 chris-laptop CRON[8238]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 18 04:17:01 chris-laptop CRON[8238]: pam_unix(cron:session): session closed for user root
Feb 18 05:17:01 chris-laptop CRON[8978]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 18 05:17:01 chris-laptop CRON[8978]: pam_unix(cron:session): session closed for user root
Feb 18 06:17:01 chris-laptop CRON[9953]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 18 06:17:01 chris-laptop CRON[9953]: pam_unix(cron:session): session closed for user root
Feb 18 06:25:01 chris-laptop CRON[10009]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 18 06:25:01 chris-laptop CRON[10009]: pam_unix(cron:session): session closed for user root
Feb 18 07:17:01 chris-laptop CRON[10682]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 18 07:17:01 chris-laptop CRON[10682]: pam_unix(cron:session): session closed for user root
Feb 18 07:30:01 chris-laptop CRON[10886]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 18 07:30:01 chris-laptop CRON[10886]: pam_unix(cron:session): session closed for user root
Feb 18 07:40:14 chris-laptop su[11164]: Successful su for proxy by root
Feb 18 07:40:14 chris-laptop su[11164]: + ??? root:proxy
Feb 18 07:40:14 chris-laptop su[11164]: pam_unix(su:session): session opened for user proxy by (uid=0)
Feb 18 07:40:14 chris-laptop su[11164]: pam_unix(su:session): session closed for user proxy
Feb 18 08:17:01 chris-laptop CRON[11684]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 18 08:17:01 chris-laptop CRON[11684]: pam_unix(cron:session): session closed for user root
Feb 18 09:17:01 chris-laptop CRON[12445]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 18 09:17:01 chris-laptop CRON[12445]: pam_unix(cron:session): session closed for user root
Feb 18 10:17:01 chris-laptop CRON[13231]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 18 10:17:01 chris-laptop CRON[13231]: pam_unix(cron:session): session closed for user root
Feb 18 11:17:01 chris-laptop CRON[14661]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 18 11:17:01 chris-laptop CRON[14661]: pam_unix(cron:session): session closed for user root
Feb 18 12:17:01 chris-laptop CRON[15530]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 18 12:17:01 chris-laptop CRON[15530]: pam_unix(cron:session): session closed for user root
Feb 18 13:17:01 chris-laptop CRON[16399]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 18 13:17:01 chris-laptop CRON[16399]: pam_unix(cron:session): session closed for user root
Feb 18 14:17:01 chris-laptop CRON[17319]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 18 14:17:01 chris-laptop CRON[17319]: pam_unix(cron:session): session closed for user root
Feb 18 15:17:01 chris-laptop CRON[18287]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 18 15:17:01 chris-laptop CRON[18287]: pam_unix(cron:session): session closed for user root
Feb 18 16:17:01 chris-laptop CRON[19156]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 18 16:17:01 chris-laptop CRON[19156]: pam_unix(cron:session): session closed for user root
Feb 18 16:24:47 chris-laptop dbus-daemon: Rejected send message, 2 matched rules; type="error", sender=":1.27" (uid=1000 pid=1574 comm="bluetooth-applet) interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply=0 destination=":1.135" (uid=0 pid=27466 comm="/usr/sbin/bluetoothd))
Feb 18 16:29:09 chris-laptop dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.276" (uid=1000 pid=19682 comm="/usr/bin/python) interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply=0 destination=":1.63" (uid=0 pid=3372 comm="/usr/bin/python))
Feb 18 16:29:15 chris-laptop polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session2 FAILED to authenticate to gain authorization for action org.debian.apt.install-packages for system-bus-name::1.276 [/usr/bin/python /usr/bin/software-center] (owned by unix-user:chris)
Feb 18 16:29:59 chris-laptop sudo:    chris : TTY=unknown ; PWD=/home/chris ; USER=root ; COMMAND=/usr/sbin/firestarter
Feb 18 16:40:09 chris-laptop dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.279" (uid=1000 pid=20637 comm="/usr/bin/python) interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply=0 destination=":1.63" (uid=0 pid=3372 comm="/usr/bin/python))
Feb 18 16:50:56 chris-laptop gdm-session-worker[1540]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "chris"
Feb 18 16:50:58 chris-laptop gdm-session-worker[1540]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=chris
Feb 18 16:51:15 chris-laptop gdm-session-worker[1913]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "chris"
Feb 18 16:51:18 chris-laptop gdm-session-worker[1913]: pam_unix(gdm:session): session opened for user chris by (uid=0)
Feb 18 16:51:18 chris-laptop gdm-session-worker[1913]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Feb 18 16:51:22 chris-laptop polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.34 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_ZA.utf8)
Feb 18 17:00:29 chris-laptop sudo:    chris : TTY=unknown ; PWD=/home/chris ; USER=root ; COMMAND=/usr/sbin/firestarter
Feb 18 17:10:10 chris-laptop dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.55" (uid=1000 pid=3679 comm="/usr/bin/python) interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply=0 destination=":1.57" (uid=0 pid=3719 comm="/usr/bin/python))
Feb 18 17:10:13 chris-laptop polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session2 successfully authenticated as unix-user:chris to gain TEMPORARY authorization for action org.debian.apt.install-packages for system-bus-name::1.55 [/usr/bin/python /usr/bin/software-center] (owned by unix-user:chris)
Feb 18 17:13:02 chris-laptop sudo:    chris : TTY=pts/1 ; PWD=/home/chris ; USER=root ; COMMAND=/usr/bin/rkhunter -c
Feb 18 17:17:01 chris-laptop CRON[24955]: pam_unix(cron:session): session opened for user root by (uid=0)

---

### Post by chris_safrica on 2011-02-18
Thanks for the Quick Reply By the Way :)

---

### Post by HermanAB on 2011-02-18
Howdy,

If you had previously played with VNC, then yes, it can be compromised.  VNC is notorious for opening up your machine to the wild wild world (VNC automatically opens ports in home routers through plug and pray) and eventually a script kiddie will discover it.

Look through the system logs and see who logged in.

---

### Post by Rubi1200 on 2011-02-18
As HermanAB mentioned, VNC can be highly problematic.

Check for who logged on with this in the terminal:

```
last | more
```Press Enter to scroll down the list.

---

### Post by chris_safrica on 2011-02-18
It look like just me in the terminal. Only thing thats strange is that there is nothing before I got home...16:27

\not sure what all the stuff below means...anyone? Sorry I really am still a new at this

chris    pts/2        :0.0             Fri Feb 18 21:08   still logged in   
chris    pts/2        :0.0             Fri Feb 18 17:38 - 20:57  (03:18)    
chris    pts/3        :0.0             Fri Feb 18 17:26 - 17:38  (00:12)    
chris    pts/2        :0.0             Fri Feb 18 17:20 - 17:26  (00:06)    
chris    pts/1        :0.0             Fri Feb 18 17:12 - 17:20  (00:07)    
chris    tty7         :0               Fri Feb 18 16:51   still logged in   
reboot   system boot  2.6.32-28-generi Fri Feb 18 16:50 - 21:08  (04:18)    
chris    pts/1        :0.0             Fri Feb 18 16:27 - 16:28  (00:00)    
chris    pts/1        :0.0             Thu Feb 17 11:23 - 11:23  (00:00)    
chris    tty7         :0               Wed Feb 16 21:21 - down  (1+19:27)   
reboot   system boot  2.6.32-28-generi Wed Feb 16 21:21 - 16:49 (1+19:27)   
chris    tty7         :0               Wed Feb 16 20:23 - down   (00:56)    
reboot   system boot  2.6.32-28-generi Wed Feb 16 20:10 - 21:20  (01:09)    
chris    tty7         :0               Wed Feb 16 16:11 - down   (03:58)    
reboot   system boot  2.6.32-28-generi Wed Feb 16 16:10 - 20:09  (03:58)    
chris    pts/2        :0.0             Tue Feb 15 19:37 - 19:37  (00:00)    
chris    pts/1        :0.0             Tue Feb 15 19:37 - 19:37  (00:00)    
chris    tty7         :0               Sat Feb 12 10:14 - down  (4+05:55)

---

### Post by chris_safrica on 2011-02-18
It looks similar to above....in any event what should I do if I system HAS been compromised?

---

### Post by cariboo on 2011-02-18
Thats' why Rubi1200 you use:

```
last | more
```

Just check the entries for the date when you think the system was broken into.

---

### Post by chris_safrica on 2011-02-18
Ok...There's nothing there (I suspect its somewhere between the 17th and 18th of FEB 2011) 

So does this mean I'm clear?

---

### Post by cariboo on 2011-02-18
We can't say if your system is secure, but nobody else logged into your system. I'd suggest you use:

```
sudo lsof -i -P -n
```

to check for open connections

---

### Post by chris_safrica on 2011-02-18
This is the output - But I'm afraid I have no idea what it means.

COMMAND    PID       USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
smbd       926       root   22u  IPv6   4801      0t0  TCP *:445 (LISTEN)
smbd       926       root   23u  IPv6   4803      0t0  TCP *:139 (LISTEN)
avahi-dae  959      avahi   13u  IPv4   4740      0t0  UDP *:5353 
avahi-dae  959      avahi   14u  IPv4   4741      0t0  UDP *:59109 
postgres  1206   postgres    3u  IPv6   6159      0t0  TCP [::1]:5432 (LISTEN)
postgres  1206   postgres    6u  IPv4   6160      0t0  TCP 127.0.0.1:5432 (LISTEN)
postgres  1206   postgres    8u  IPv6   6170      0t0  UDP [::1]:57403->[::1]:57403 
dhclient  1236       root    5w  IPv4   6214      0t0  UDP *:68 
postgres  1242   postgres    8u  IPv6   6170      0t0  UDP [::1]:57403->[::1]:57403 
postgres  1243   postgres    8u  IPv6   6170      0t0  UDP [::1]:57403->[::1]:57403 
postgres  1244   postgres    8u  IPv6   6170      0t0  UDP [::1]:57403->[::1]:57403 
postgres  1245   postgres    8u  IPv6   6170      0t0  UDP [::1]:57403->[::1]:57403 
polipo    1328      proxy    0u  IPv4   6867      0t0  TCP 127.0.0.1:8118 (LISTEN)
master    1408       root   12u  IPv4   7148      0t0  TCP *:25 (LISTEN)
tor       1426 debian-tor    4u  IPv4   7872      0t0  TCP 10.0.0.3:38670->147.228.93.93:9001 (ESTABLISHED)
tor       1426 debian-tor    7u  IPv4   7298      0t0  TCP 127.0.0.1:9050 (LISTEN)
tor       1426 debian-tor   10u  IPv4   9807      0t0  TCP 10.0.0.3:59566->62.212.66.193:9001 (ESTABLISHED)
tor       1426 debian-tor   11u  IPv4  14416      0t0  TCP 10.0.0.3:44592->78.46.246.116:9001 (ESTABLISHED)
cupsd     1471       root    6u  IPv6   7585      0t0  TCP [::1]:631 (LISTEN)
cupsd     1471       root    7u  IPv4   7586      0t0  TCP 127.0.0.1:631 (LISTEN)
chrome    1942      chris   91u  IPv4  26723      0t0  TCP 10.0.0.3:39637->196.23.168.145:80 (ESTABLISHED)
chrome    1942      chris  110u  IPv4  14405      0t0  TCP 10.0.0.3:58854->209.85.227.17:443 (ESTABLISHED)
chrome    1942      chris  115u  IPv4  15179      0t0  TCP 10.0.0.3:46298->209.85.227.189:443 (ESTABLISHED)
chrome    1942      chris  121u  IPv4  27313      0t0  TCP 10.0.0.3:37970->91.189.94.12:80 (ESTABLISHED)
chrome    1942      chris  126u  IPv4  26721      0t0  TCP 10.0.0.3:39636->196.23.168.145:80 (ESTABLISHED)
chrome    1942      chris  129u  IPv4  27086      0t0  TCP 10.0.0.3:36058->204.9.163.163:80 (ESTABLISHED)
chrome    1942      chris  133u  IPv4  25984      0t0  TCP 10.0.0.3:35708->196.36.108.168:80 (ESTABLISHED)
nmbd      1994       root    9u  IPv4  11280      0t0  UDP *:137 
nmbd      1994       root   10u  IPv4  11281      0t0  UDP *:138 
nmbd      1994       root   11u  IPv4  11283      0t0  UDP 10.0.0.3:137 
nmbd      1994       root   12u  IPv4  11284      0t0  UDP 10.0.0.3:138

---

### Post by cariboo on 2011-02-19
I don't see anything weird in your output. From the looks of it you have several servers running, including Samba, Postgresql and CUPS. I see you are also using Tor and chromium.

When running a command, that outputs something you don't understand, Google is your friend, for instance the first line states that you are running smbd and it is listening on port 445

You can check the name smbd or the port to see what the common name of the service is eg: searching for smbd gets you [this]("http://www.samba.org/samba/docs/man/manpages-3/smbd.8.html") result

and searching for port 445 gets you [this]("http://www.pc-library.com/ports/tcp-udp-port/445/") result

---

### Post by dodo3773 on 2011-02-19
This line 

> master    1408       root   12u  IPv4   7148      0t0  TCP *:25 (LISTEN)looks kind of interesting to me. But there is also a good chance that it is probably nothing.

What I would do would be to go into your start up applications also bum boot up manager and disable some of that stuff temporarily like tor, polipo, samba, cups, etc.. Then reboot your computer (do not open any applications web browser, bit torrent client, email client, etc..). Wait about 5 minutes and run 
> sudo lsof -i -P -nagain. 
and then run something like 

```
netstat --tcp --numeric | awk 'NR>2 {print $5}' | uniq
```to see what foreign ip addresses are connected to your computer. I also agree with cariboo907              on checking out the ports. The port numbers are the numbers after the : on the ip address. For example in the ip address 192.168.1.1:25 the port number is 25. Here is an O.K. port reference that I use

[http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers)

Also you can run a simple whois to get a little more information on who is connected to your machine. Something like 

```
 whois 72.14.213.109
```
Should tell you that 72.14.213.109 is Google. I hope that helps.

---

### Post by cariboo on 2011-02-19
It looks like master is a part of postfix, so the op is also ruining a mail server.

---

### Post by dodo3773 on 2011-02-19
> **cariboo907 said:**
> It looks like master is a part of postfix, so the op is also ruining a mail server.

Gotcha. That makes sense. Especially since the only log in seen is the one user in the output of "last" before and the port is 25 'smtp'.

---

### Post by arrrghhh on 2011-02-20
> **HermanAB said:**
> Howdy,

If you had previously played with VNC, then yes, it can be compromised.  VNC is notorious for opening up your machine to the wild wild world (VNC automatically opens ports in home routers through plug and pray) and eventually a script kiddie will discover it.

Look through the system logs and see who logged in.

I don't want to steal this thread, but basically this exact issue happened to my father.  I switched him to Ubuntu so he could be more secure, and when he enabled remote desktop, there was a checkbox "Configure network to automatically accept connections" <--- I'm assuming this is the culprit?  

He was working on a spreadsheet, and he said a popup showed up that someone was controlling his computer, and he said programs started opening.  He quickly clicked back to his spreadsheet software, where a ton of text got seemingly pasted into it, when he saved the doc and just shut it all off...

I honestly did not think that Ubuntu would ever allow RDP to traverse the WAN, but this is exactly what has happened evidently, and now of course my father is freaking out.  Can someone confirm that this checkbox was the source of his woes?  I'm still baffled that Ubuntu would make it this easy to become this vulnerable.  

Obviously my dad was dumb by having the lack of a confirmation for remote-ing in, lack of a password etc but of course in his defense he wanted to be able to "easily" remote into machines on his LAN... easily usually means low security, but if RDP was restricted to his LAN the risk would be minimal, compared to the outrageous risk of putting RDP open to the WAN...

Also, what logs can I check to see who or what was done... seems auth log is a good one, and it doesn't seem like anything bad was actually done to the system, I just want to be sure.  Oy... Thanks!

---

### Post by cariboo on 2011-02-20
>  don't want to steal this thread, but basically this exact issue happened to my father. I switched him to Ubuntu so he could be more secure, and when he enabled remote desktop, there was a checkbox "Configure network to automatically accept connections" <--- I'm assuming this is the culprit? 

If Upnp is enabled on the router, using that setting will open a connection to the internet, so it isn't surprising that someone accessed the system.

---

