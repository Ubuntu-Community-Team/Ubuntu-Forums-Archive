---
title: "Too many open files problems on Ubuntu Server"
date: 2012-04-18
forum: Server Platforms
---

### Post by renegadeandy on 2012-04-18
I am running a rational Jazz Team Server - and it is hosted within tomcat.

When running the server I very very very frequently get the following errors:

java.util.zip.ZipException: Too many open files 

basically - I need to raise the limits for the amount of open files I can have in my system. I dont know if there is some specific options for Java / Tomcat applications - because I have done this and the important bits from ulimit -a shows :

[PHP]open files -n 65536[/PHP]

Yet I am obviously missing something - please help!

---

### Post by hawkmage on 2012-04-18
There are different file handle limits.

To see where you are at with file handles run the command:
```
sysctl fs.file-nr
```
From this command you will get 3 numbers.  First is the number of used  file descriptor the second is the number of allocated but not used file  descriptor and the last is the system max file descriptor.

To up this limit you will need to add something similar to the following in the file /etc/sysctl.conf:
```
fs.file-max = 204708
```

Also there is an individual users file handle limit, that is where the "ulimit -n" command.  If you are running to this limit you will have to add entries to the /etc/security/limits.conf file for the user like the following:
```
UID soft nofile 4096
UID hard nofile 10240
```
Replace the UID with the user ID you want to increase the limit on.

---

### Post by renegadeandy on 2012-04-19
Thank you for your response!

When the server throws the exception the command outputs :


fs.file-nr = 1984	0	200000

so it LOOKS like something has an upper limit of 1984 - but I cannot find it.... Any ideas what I should check? ill post the contents of my limits files here:

[PHP]andy@ubuntu:~$ cat /etc/security/limits.conf 
# /etc/security/limits.conf
#
#Each line describes a limit for a user in the form:
#
#<domain>        <type>  <item>  <value>
#
#Where:
#<domain> can be:
#        - an user name
#        - a group name, with @group syntax
#        - the wildcard *, for default entry
#        - the wildcard %, can be also used with %group syntax,
#                 for maxlogin limit
#        - NOTE: group and wildcard limits are not applied to root.
#          To apply a limit to the root user, <domain> must be
#          the literal username root.
#
#<type> can have the two values:
#        - "soft" for enforcing the soft limits
#        - "hard" for enforcing hard limits
#
#<item> can be one of the following:
#        - core - limits the core file size (KB)
#        - data - max data size (KB)
#        - fsize - maximum filesize (KB)
#        - memlock - max locked-in-memory address space (KB)
#        - nofile - max number of open files
#        - rss - max resident set size (KB)
#        - stack - max stack size (KB)
#        - cpu - max CPU time (MIN)
#        - nproc - max number of processes
#        - as - address space limit (KB)
#        - maxlogins - max number of logins for this user
#        - maxsyslogins - max number of logins on the system
#        - priority - the priority to run user process with
#        - locks - max number of file locks the user can hold
#        - sigpending - max number of pending signals
#        - msgqueue - max memory used by POSIX message queues (bytes)
#        - nice - max nice priority allowed to raise to values: [-20, 19]
#        - rtprio - max realtime priority
#        - chroot - change root to directory (Debian-specific)
#
#<domain>      <type>  <item>         <value>
#

#*               soft    core            0
#root            hard    core            100000
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4

# End of file
* soft nofile 65536
* hard nofile 65536
[/PHP]

and the contents of the sysctl file are:

[PHP]andy@ubuntu:~$ cat /etc/sysctl.conf 
#
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables.
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# Uncomment the following to stop low-level messages on console
#kernel.printk = 4 4 1 7

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.all.forwarding=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Ignore ICMP broadcasts
#net.ipv4.icmp_echo_ignore_broadcasts = 1
#
# Ignore bogus ICMP errors
#net.ipv4.icmp_ignore_bogus_error_responses = 1
# 
# Do not accept ICMP redirects (prevent MITM attacks)
#net.ipv4.conf.all.accept_redirects = 0
#net.ipv6.conf.all.accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net.ipv4.conf.all.secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net.ipv4.conf.all.send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net.ipv4.conf.all.accept_source_route = 0
#net.ipv6.conf.all.accept_source_route = 0
#
# Log Martian Packets
#net.ipv4.conf.all.log_martians = 1
fs.file-max = 200000
[/PHP]

Help!

---

### Post by elico on 2012-04-19
did you applied the changes using sysctl -a ?

---

### Post by renegadeandy on 2012-04-19
Yes - tried running that command , then tried the server again,

It gets to a stage and then dies with exception:

[HTML]Request to service https://novo.dyndns.tv:9443/admin/jtsregistration failed with status code 500 and response body: 500 java.io.FileNotFoundException: /opt/IBM/JazzTeamServer/server/conf/admin/friends.rdf.1334853021281 (Too many open files) java.io.FileNotFoundException: /opt/IBM/JazzTeamServer/server/conf/admin/friends.rdf.1334853021281 (Too many open files) at java.io.FileOutputStream.<init>(FileOutputStream.java:205) at java.io.FileOutputStream.<init>(FileOutputStream.java:157) at com.ibm.team.lpa.common.util.FileUtil.copyFile(FileUtil.java:27) at com.ibm.team.lpa.common.clients.FriendsClient.updateFriendsConfig(FriendsClient.java:82) at com.ibm.team.lpa.common.services.JtsRegistrationService.writeNewFriendsRdf(JtsRegistrationService.java:77) at [/HTML]

with a sysctl fs.file-nr output of :

fs.file-nr = 1952 0 200000

help help!

---

### Post by Gyokuro on 2012-04-19
Hi,

can you please post:

cat /proc/sys/fs/file-max

and

ulimit -n

and if the limit is too low you can set it via:

echo 120000 > /proc/sys/fs/file-max

and set it permanent in /etc/sysctl.conf via:

fs.file-max = 120000

and in /etc/security/limits.conf you can set:

* - nofile 120000

Please note that the nofile item has two possible limits: a hard and soft limit and by using the "-" both limits are equal. The understand the meaning of soft and hard limits I recommend to check UNIX system administration literature. 
-HTH

---

### Post by renegadeandy on 2012-04-19
Absolutely :


andy@ubuntu:~$ cat /proc/sys/fs/file-max 
200000

andy@ubuntu:~$ ulimit -n
65536


Both look ok! Please bare in mind this is an apache tomcat Java based application - if that makes any difference to anything!

---

### Post by Gyokuro on 2012-04-19
Hi,

thanks - your problem seems to be known. Check IBM's documentation: [http://www-01.ibm.com/support/docview.wss?uid=swg21403391](http://www-01.ibm.com/support/docview.wss?uid=swg21403391)

---

### Post by renegadeandy on 2012-04-19
wow! How on earth did you actually find that - i am impressed! I am trying the fix out now :) :D:popcorn:

---

### Post by renegadeandy on 2012-04-19
To let people know - this has solved the problem!

Thanks again to the community for helping so diligently!):P

---

