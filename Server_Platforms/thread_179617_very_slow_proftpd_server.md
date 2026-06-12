---
title: "very slow proftpd server"
date: 2006-05-20
forum: Server Platforms
---

### Post by zasf on 2006-05-20
Hi all, I setted up a ftp server on my home server. The purpose is to share a local dapper repository for a forthcoming dapper install day.

My big problem is that the ftp server is terrible slow. All this is performed on a local network, since people will bring their comp here, so it can't be a ADSL problem or firewall problem. My only firewall is performed by the router towards WAN.

I paste here the top output (taken while downloading from the ftp server a 700mb file) in case you want to see it:
```

top - 16:12:52 up  1:29,  1 user,  load average: 0.00, 0.01, 0.07
Tasks:  49 total,   1 running,  48 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.7% us,  1.0% sy,  0.0% ni, 97.7% id,  0.0% wa,  0.3% hi,  0.3% si
Mem:    515064k total,   322280k used,   192784k free,     3288k buffers
Swap:   835340k total,    18788k used,   816552k free,   280884k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4654 sniff     16   0  2196 1080  856 R  0.7  0.2   0:03.37 top  
 4655 userftp   15   0  4728 2164 1504 S  0.7  0.4   0:00.38 proftpd
    1 root      16   0  1564  528  460 S  0.0  0.1   0:03.92 init
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 events/0
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.04 khelper
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.96 kblockd/0
   66 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
   65 root      15   0     0    0    0 S  0.0  0.0   0:13.26 kswapd0
  654 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod
 1745 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd
 1826 root      15   0     0    0    0 S  0.0  0.0   0:02.27 kjournald
 2048 root      19  -4  2108  552  368 S  0.0  0.1   0:01.36 udevd
 2847 root      20   0     0    0    0 S  0.0  0.0   0:00.00 shpchpd_event
 3272 root      15   0     0    0    0 S  0.0  0.0   0:01.75 kjournald
 3737 syslog    16   0  1768  676  548 S  0.0  0.1   0:00.09 syslogd
 3760 root      15   0  1680  496  412 S  0.0  0.1   0:00.08 dd
 3762 klog      20   0  2404 1328  388 S  0.0  0.3   0:00.38 klogd
 3781 messageb  16   0  2188  788  660 S  0.0  0.2   0:00.00 dbus-daemon
 3796 haldaemo  15   0  6636 5220 1560 S  0.0  1.0   0:02.40 hald
 3797 root      16   0  2716  972  836 S  0.0  0.2   0:00.12 hald-runner
 3849 haldaemo  25   0  2000  788  692 S  0.0  0.2   0:00.00 hald-addon-keyb
 3856 haldaemo  17   0  2004  816  716 S  0.0  0.2   0:01.19 hald-addon-stor
 3857 haldaemo  17   0  2008  816  716 S  0.0  0.2   0:01.15 hald-addon-stor
 3897 cupsys    16   0  4048 1652 1212 S  0.0  0.3   0:00.05 cupsd
 3906 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kapmd
 3917 root      16   0  1564  452  384 S  0.0  0.1   0:00.00 apmd
 4011 root      16   0  5764 1380  900 S  0.0  0.3   0:00.11 nmbd

```

top takes more resources than proftpd :-k Do I miss something?

---

### Post by linuxone on 2006-05-20
Hi,

[QUOTE=zasf]My big problem is that the ftp server is terrible slow. All this is performed on a local network, since people will bring their comp here, so it can't be a ADSL problem or firewall problem. My only firewall is performed by the router towards WAN.[/QUOTE]

top doesn't solve any network problems and network performance has nothing to do with the process resources in use. :)

Bad FTP download performance MAY be caused be a bad configured FTP server or bad FTP client configuration. But this should happen real seldom. Mostly a bad network performance is caused from very different things .... which are difficult to locate.

Network perfomance could be caused by (for example):

-> Hardware damage (NIC, Switch, bad cable)
-> Hardware configuration (ie. NIC: incompatible duplex configuration on 2 sides of one connection)

You can try to locate it by doing some tests:

from the Client: 
-> try an FTP download from another server
-> try an SFTP download from the "bad performance" server
-> try any other network service from the "bad" server (ie. www or copy to/from a Samba share)

from Server:
-> do an FTP and SFTP upload to the specific client and also another machine
-> do an FTP and SFTP download from another machine

If you have experiences in analysing network streams use Ethereal or tcpdump to catch and analyse all TCP/IP packets. Some problems, for example a defect NIC, could be found only by such a network analysing.

Anyway, to answer and help more detailed we need some exact details about your network and all related topics, furthermore configuration of: network on all related machines, ftp server and client.

Thomas

---

### Post by zasf on 2006-05-20
Thanks for your reply. Here are more details on my setup:

**Server "kate" 192.168.1.99**
P2 366Mhz, 512 MB Ram, 20Gb HD, wired VIA ethernet NIC
Dapper flight 7 install, upgraded yestarday
Using debmirror in order to mirror Dapper's repository (15Gb)

```
$ cat /etc/proftpd.conf
#
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
#

ServerName                      "kate ftp server"
ServerType                      standalone

MultilineRFC2228                on
DefaultServer                   on
ShowSymlinks                    off

#TimeoutNoTransfer              300
TimeoutStalled                  300
#TimeoutIdle                    1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                     "-lh"

#DenyFilter                     \*.*/

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
#PersistentPasswd               off

# Uncomment this if you would use TLS module:
#TLSEngine                      on

# Uncomment this if you would use quota module:
#Quotas                         on

# Uncomment this if you would use ratio module:
#Ratios                         on

# Port 21 is the standard FTP port.
Port                            21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances                    30

# Set the user and group that the server normally runs at.
User                            nobody
Group                           nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           022  022
# Normally, we want files to be overwriteable.
AllowOverwrite                  on

# Delay engine reduces impact of the so-called Timing Attack described in
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
# It is on by default.
#DelayEngine                    off

# A basic anonymous configuration, no upload directories.

<Anonymous ~userftp>
   User                         userftp
   Group                        nogroup
   UserAlias                    anonymous userftp
   RequireValidShell            off
   MaxClients                   10

   <Limit LOGIN>
     AllowAll
   </Limit>

#   <Directory *>
#       Umask 022 022
#       AllowOverwrite off
#       <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
#               DenyAll
#       </Limit>
#   </Directory>

  <Limit WRITE>
    DenyAll
  </Limit>

 <Directory uploads/*>
    <Limit READ>
      DenyAll
    </Limit>

    <Limit STOR>
      AllowAll
    </Limit>
  </Directory>
</Anonymous>

```

```
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              18G   11G  6.2G  64% /
varrun                252M  116K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M   52K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  234M   8% /lib/modules/2.6.15-21-686/volatile
/dev/hdb1             3.0G  749M  2.1G  27% /opt
/ubuntumirror          18G   11G  6.2G  64% /home/userftp/mirror
/opt/iso              3.0G  749M  2.1G  27% /home/userftp/iso

```

**Client "blasfemo" 192.168.1.6**
Toshiba Centrino 2GHz, 1GB Ram, using wireless connection
Dapper flight 5, constantly upgraded
No particular ftp settings

**Router 192.168.1.1**
Dlink DSL-G604T, no particular settings
Connects to the internet (ADSL 640/320 KBps)

[COLOR="Red"]**Some tests**[/COLOR]

**Download of a big file from an external ftp server (from client blasfemo)**

```
matteo@blasfemo:~$ ftp ftp.belnet.be
Connected to niue.belnet.be.
220 ProFTPD 1.3.0 Server (BELNET FTPD Server) [193.190.198.20]
Name (ftp.belnet.be:matteo): anonymous
331 Anonymous login ok, send your complete email address as your password.
Password:
230 Anonymous access granted, restrictions apply.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> cd pub/mirror/ubuntu.com
250 CWD command successful
ftp> ls
200 PORT command successful
150 Opening ASCII mode data connection for file list
drwxr-x---  11 ftp      ftp          1024 Dec  6 06:37 releases
drwxr-x---   6 ftp      ftp          1024 May 20 14:29 ubuntu
226 Transfer complete.
ftp> cd ubuntu
250 CWD command successful
ftp> ls
200 PORT command successful
150 Opening ASCII mode data connection for file list
drwxr-x---  22 ftp      ftp          1024 Jan 23 16:47 dists
drwxr-x---   2 ftp      ftp         24576 May 20 14:29 indices
-rw-r-----   1 ftp      ftp       2868223 May 20 14:28 ls-lR.gz
drwxr-x---   6 ftp      ftp            96 May 20 14:08 pool
drwxr-x---   3 ftp      ftp            96 Jun 15  2004 project
226 Transfer complete.
ftp> get ./pool/main/l/linux-source-2.6.15/linux-image-2.6.15-22-386_2.6.15-22.34_i386.deb linux-image-2.6.15-22-386_2.6.15-22.34_i386.deb
local: linux-image-2.6.15-22-386_2.6.15-22.34_i386.deb remote: ./pool/main/l/linux-source-2.6.15/linux-image-2.6.15-22-386_2.6.15-22.34_i386.deb
200 PORT command successful
150 Opening BINARY mode data connection for ./pool/main/l/linux-source-2.6.15/linux-image-2.6.15-22-386_2.6.15-22.34_i386.deb (21593570 bytes)
226 Transfer complete.
21593570 bytes received in 284.32 secs (74.2 kB/s)

```

**upload of the same big file to kate from blasfemo**
```
matteo@blasfemo:~$ ftp 192.168.1.99
Connected to 192.168.1.99.
220 ProFTPD 1.2.10 Server (kate ftp server) [192.168.1.99]
Name (192.168.1.99:matteo): anonymous
331 Anonymous login ok, send your complete email address as your password.
Password:
230-Welcome, archive user anonymous@192.168.1.6 !
230-
230-           `/smNs
230-   /+++ssmNMMMMs.
230-  `ossss++oMMs`
230-        +NMs`
230-    /soNMs`
230-   .MMNMMy+.
230-    `` `/smMNyym`
230-           `.++/
230-
230-The local time is: Sun May 21 02:24:37 2006.
230-
230 Anonymous access granted, restrictions apply.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> cd upload
550 upload: No such file or directory
ftp> cd uploads
250 CWD command successful
ftp> put linux-image-2.6.15-22-386_2.6.15-22.34_i386.deb linux-image-2.6.15-22-386_2.6.15-22.34_i386.deb
local: linux-image-2.6.15-22-386_2.6.15-22.34_i386.deb remote: linux-image-2.6.15-22-386_2.6.15-22.34_i386.deb
200 PORT command successful
150 Opening BINARY mode data connection for linux-image-2.6.15-22-386_2.6.15-22.34_i386.deb
226 Transfer complete.
21593570 bytes sent in 108.52 secs (194.3 kB/s)

```

**Download of the same file from local ftp server**
```
ftp> get ./pool/main/l/linux-source-2.6.15/linux-image-2.6.15-22-386_2.6.15-22.34_i386.deb linux-image-2.6.15-22-386_2.6.15-22.34_i386B.deb
local: linux-image-2.6.15-22-386_2.6.15-22.34_i386B.deb remote: ./pool/main/l/linux-source-2.6.15/linux-image-2.6.15-22-386_2.6.15-22.34_i386.deb
200 PORT command successful
150 Opening BINARY mode data connection for ./pool/main/l/linux-source-2.6.15/linux-image-2.6.15-22-386_2.6.15-22.34_i386.deb (21593570 bytes)
Bytes transferred: 21593570226 Transfer complete.
21593570 bytes received in 63.59 secs (331.6 kB/s)

```

wow that seems fast.. the point is that when in ftp I type any commands the response is really really slow. For example "ls" takes a couple of seconds while in external ftp sites does not, the response is really quick.

**using local dapper repository mirror**
```
matteo@blasfemo:~$ sudo apt-get update
Password:
Hit ftp://192.168.1.99 dapper Release.gpg
Get: 1 ftp://192.168.1.99 dapper Release [34.8kB]
Get: 2 ftp://192.168.1.99 dapper/main Packages
Ign ftp://192.168.1.99 dapper/main Packages
99% [Packages gzip 0]
gzip: stdin: unexpected end of file
Errftp://192.168.1.99 dapper/main Packages
  Sub-process gzip returned an error code (1)
Fetched 34.8kB in 20s (1659B/s)
Failed to fetch ftp://192.168.1.99/mirror/dists/dapper/main/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Don't mind the error, the mirror is not ready yet. But see the DL time, it's damn slow.. what is wrong with that?

```
matteo@blasfemo:~$ cat /etc/apt/sources.list
deb ftp://192.168.1.99/mirror dapper main

```

What am I missing? Sorry for the very long post

---

### Post by linuxone on 2006-05-21
Hi,

[QUOTE=zasf]What am I missing? Sorry for the very long post[/QUOTE]

the test results looks really strange. As already mentioned, real network problems were really difficult to locate.

Guess the log files (syslog, proftpd.log) on kate (server) doesn't contain any related error message, isn't it?

Basicly your entire network seems to be slow, even 331 kb/s is not real fast for a local Intranet network. But without exact details about your network it is real difficult to say anymore.

In fact: it's quite unimpossible to solve such kind of network problems from remote. It's necessary to "see" the network and work with it, check hardware configuration, do network tests and TCP/IP analysis by packet sniffing.
I can give you some hints but no answer how to solve your problem.

What kind of network do you have (BNC or CAT5, Ethernet or FastEthernet or Gigabit)?
What kind of network structure (switched, using hubs)? Is the network hardware "managed", do you use a higher level switch (Layer-3 or more)? If yes (managed switch), were the switch ports specially configured (half or full duplex, fixed speed) or do you use auto negotiation? Does both sides of a single connection (cable) use the same NIC settings?
Are Windows machines connected to this network? Which Windows version, and how is their network configured?
Do you only use TCP/IP network protocol on your network or also other protocols, ie. IPX/SPX?
Do you have a high network traffic which can cause a smaller bandwidth for your download PC (which causes only 331 kb/s transfer speed)?
Did you catch TCP/IP packets (network sniffing -> Ethereal) and analyse the traffic, ie. to check for a defect NIC or wrong netmask setting or any other remarkably packets?

Usefull tools:
mii-tool (from net-tools) or mii-diag does show and manipulate the NIC settings on your linux box.
ethereal can catch TCP/IP packets and help to analyse them. But there are good network knowledges required to be able to analyse and find out what's going wrong ....
ncftp (command line ftp client) is a much more powerfull FTP client then the simple "ftp" tool. :)

Thomas

---

### Post by zasf on 2006-05-21
Thanks Thomas for your support, I post some more details

**Network setup**
[IMG]http://ubuntuforums.org/gallery/files/5/7/5/0/6/network.png[/IMG]

there is another windows box, but I keep it off during tests.

The 331 kb/s is performed on a wireless basis.. so you can't compare it with a wired connection. Kate has a 10/100 ethernet card. Router supports high speed since I was able to  transfer files from laptop (using wired NIC) at 1000kb/s with the windows box. This can't be performed anymore with dapper (my guess is that the portable wired NIC is not very well supported since connection drops at high speed with dapper).

When I did the famous 331 kb/s dowload I had no internet traffic. Machines were just performing the test and the win box was off.

Do you need other network specifications?

**troubleshooting**

```
sniff@kate:~$ tail -f /var/log/syslog
cut
May 21 13:15:45 localhost proftpd[4532]: localhost (192.168.1.6[192.168.1.6]) - FTP session opened.
May 21 13:16:06 localhost proftpd[4532]: localhost (192.168.1.6[192.168.1.6]) - FTP session closed.
```

the syslog doesn't say anything interesting related to ftp. But I'll check what you suggest: ethereal, mii-tool, ncftp.

The wrong thing is related to the local repository, 1659B/s when using the local repo is not accetable. 300Kb/s would be ok, why that difference?

EDIT: maybe this is less difficult than expected. If I enable more repos (not only 'main') from the local server, the transfer speed increases. This is due IMHO to the fact that connection speed is really slow (and also commands like ls, cd, etc). The more stuff you download the more speed grows.

```
matteo@blasfemo:~$ sudo apt-get update
Hit ftp://192.168.1.99 dapper Release.gpg
Get: 1 ftp://192.168.1.99 dapper Release [34.8kB]
Get: 2 ftp://192.168.1.99 dapper/main Packages
Ign ftp://192.168.1.99 dapper/main Packages
Get: 3 ftp://192.168.1.99 dapper/universe Packages [2444kB]
Get: 4 ftp://192.168.1.99 dapper/multiverse Packages [92.8kB]
Get: 5 ftp://192.168.1.99 dapper/restricted Packages [4573B]
Get: 6 ftp://192.168.1.99 dapper/main Packages
Errftp://192.168.1.99 dapper/main Packages
  Unable to fetch file, server said &#8216;/mirror/dists/dapper/main/binary-i386/Packages.gz: No such file or directory  &#8217;
**Fetched 2576kB in 58s (43.8kB/s)**
Failed to fetch ftp://192.168.1.99/mirror/dists/dapper/main/binary-i386/Packages.gz  Unable to fetch file, server said &#8216;/mirror/dists/dapper/main/binary-i386/Packages.gz: No such file or directory  &#8217;
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by zasf on 2006-05-21
This is what I get if I upgrade from blasfemo using kate repository with wired connection

```
matteo@blasfemo:~$ sudo apt-get update
Get: 1 ftp://192.168.1.99 dapper Release.gpg [189B]
Get: 2 ftp://192.168.1.99 dapper Release [34.8kB]
Get: 3 ftp://192.168.1.99 dapper/main Packages [620kB]
Get: 4 ftp://192.168.1.99 dapper/universe Packages [2446kB]
Hit ftp://192.168.1.99 dapper/multiverse Packages
Hit ftp://192.168.1.99 dapper/restricted Packages
Fetched 3101kB in 53s (58.1kB/s)
Reading package lists... Done
matteo@blasfemo:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade...Done
The following NEW packages will be installed
  app-install-data-commercial linux-image-2.6.15-23-686 linux-restricted-modules-2.6.15-23-686
The following packages will be upgraded:
  example-content gnome-app-install linux-image-686 linux-restricted-modules-686
4 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 56.1MB of archives.
After unpacking 98.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 ftp://192.168.1.99 dapper/main app-install-data-commercial 1 [1440B]
Get: 2 ftp://192.168.1.99 dapper/main example-content 12 [25.3MB]
Get: 3 ftp://192.168.1.99 dapper/main gnome-app-install 0.1.31 [156kB]
Get: 4 ftp://192.168.1.99 dapper/main linux-image-2.6.15-23-686 2.6.15-23.35 [22.4MB]
Get: 5 ftp://192.168.1.99 dapper/main linux-image-686 2.6.15.22 [23.3kB]
Get: 6 ftp://192.168.1.99 dapper/restricted linux-restricted-modules-2.6.15-23-686 2.6.15.10-2 [8201kB]
Get: 7 ftp://192.168.1.99 dapper/restricted linux-restricted-modules-686 2.6.15.22 [23.4kB]
Fetched 56.1MB in 1m25s (654kB/s)

```

log in to the ftp server is really slow, but then it works ok. Maybe I should troubleshoot my ftp configuration.

---

### Post by zasf on 2006-05-22
**SOLVED!!!**

Put this in your /etc/proftpd.conf:

```
UseReverseDNS                   off
IdentLookups                    off
```

and then:

```
Fetched 6627kB in 4s (1531kB/s)
```

Thanks, Matteo

---

### Post by crapufish on 2006-07-29
Yes, this post solved my problem!

THANKS!!!!

---

### Post by victorius on 2006-10-04
I'm running a webserver on my lan. It used to run great until we had to change router. The the FTP server got real slow. Quite unusable.

I'm glad to report that "UseReverseDNS                   off" fixed it for me.

---

