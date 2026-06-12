---
title: "Unknown outbound connections - port 80"
date: 2008-09-16
forum: Security
---

### Post by ene_dene on 2008-09-16
I'm using firestarter firewall and in active connections i see 4 connections where I'm the source and some IPs throughout the world are destinations, port 80 http.
I've shut every program down, I even blocked all the outgoing connections for testing, and these connections are always there (I can't browse, but these connections are up). I've tried [http://IP](http://IP) address and just one of a pages had some content on it "someday I might put something here".
What could be making these outbound connections to these specific sources?

---

### Post by ene_dene on 2008-09-16
This has to be some kind of a bug, now I've physically disconnected the computer from internet and still the connections were there.

---

### Post by kevdog on 2008-09-16
What does 

sudo netstat -tunap | grep 80

show?

---

### Post by ene_dene on 2008-09-16
```
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      2227/apache2    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      5807/cupsd      
tcp        1      0 192.168.0.10:55570      209.85.135.103:80       CLOSE_WAIT  5766/boinc_client
tcp        1      0 192.168.0.10:35455      209.85.135.99:80        CLOSE_WAIT  5766/boinc_client
tcp        1      0 192.168.0.10:45851      209.85.135.104:80       CLOSE_WAIT  5766/boinc_client
tcp        0      0 192.168.0.10:52573      209.85.135.147:80       TIME_WAIT   -               
tcp        1      0 192.168.0.10:46671      129.89.61.70:80         CLOSE_WAIT  5766/boinc_client
tcp        1      0 192.168.0.10:50701      129.89.61.70:80         CLOSE_WAIT  11602/einstein_S5R4
udp6       0      0 fe80::21d:7dff:feba:123 :::*                                4596/ntpd
```
These are connections that should be there, but there are no 4 connections here that I see in Firestarter.

---

### Post by ene_dene on 2008-09-16
Here is an image from Firestarter.

---

### Post by cdenley on 2008-09-16
Apparently you didn't run the netstat command while the connections were active. Try running this command while the connections are active.
```

sudo lsof -n -i TCP:80

```
The output you posted shows boinc connected to a few google servers and a website for "Join Einstein". It also shows some other Einstein process connected to that website.

As far as the firestarter screen capture you posted, I can't tell what those servers are supposed to be doing, except for 69.63.176.184.
```

whois 69.63.176.184

```
> 
OrgName:    Thefacebook.com 
OrgID:      THEFA-3
Address:    156 University Ave, 3rd floor
City:       Palo Alto
StateProv:  CA
PostalCode: 94301
Country:    US

NetRange:   69.63.176.0 - 69.63.191.255 
CIDR:       69.63.176.0/20 
NetName:    TFBNET2
NetHandle:  NET-69-63-176-0-1
Parent:     NET-69-0-0-0-0
NetType:    Direct Assignment
NameServer: DNS1.SCTM.TFBNW.NET
NameServer: DNS2.SCTM.TFBNW.NET
NameServer: DNS04.SF2P.TFBNW.NET
NameServer: DNS05.SF2P.TFBNW.NET
Comment:    Contact [email]abuse@facebook.com[/email] with issues.
RegDate:    2007-02-07
Updated:    2007-03-12

RAbuseHandle: OPERA82-ARIN
RAbuseName:   Operations 
RAbusePhone:  +1-650-543-4800
RAbuseEmail:  [email]ops@facebook.com[/email] 

RNOCHandle: OPERA82-ARIN
RNOCName:   Operations 
RNOCPhone:  +1-650-543-4800
RNOCEmail:  [email]ops@facebook.com[/email] 

RTechHandle: OPERA82-ARIN
RTechName:   Operations 
RTechPhone:  +1-650-543-4800
RTechEmail:  [email]ops@facebook.com[/email] 

OrgTechHandle: OPERA82-ARIN
OrgTechName:   Operations 
OrgTechPhone:  +1-650-543-4800
OrgTechEmail:  [email]ops@facebook.com[/email]

# ARIN WHOIS database, last updated 2008-09-15 19:10
# Enter ? for additional hints on searching ARIN's WHOIS database.

Do you use facebook? They could be using that server for images or something.

---

### Post by ene_dene on 2008-09-16
Here is a screenshot, I've run the commands and had Firestarter opened at the same time. I use boinc - einstein@home and that is not a problem, but I can't understand what are these four connections, and they seem to be active no matter is my comp connected to net or not, which is impossible.
> Do you use facebook? They could be using that server for images or something.
I do use facebook rarely, but just over firefox.

---

### Post by kpatz on 2008-09-17
install iptstate (sudo apt-get install iptstate) and then run it with "sudo iptstate".

This will give you your iptables connection state in real-time (like a top command similar to the firestarter active connections).  Plus you'll see if the connections are active or not, and how long before they expire.

Post a screenshot of the results.

---

### Post by ene_dene on 2008-09-17
Nice program!
Screenshot, all the same... I forgot about this 5060 SIP, that connection is also unknown to me.

---

### Post by ene_dene on 2008-09-17
I've just made the test with physically disconnected comp, and again the same, all the connections ESTABLISHED. :)

---

### Post by cariboo on 2008-09-17
Have you restarted apache, just in case it is caching the addresses. To do this in a terminal type:

```
sudo /etc/init.d.apache2 restart
```

Then check ipstate again.

Jim

---

### Post by ene_dene on 2008-09-18
Yes, I've tried it. I use apache on this comp just on my home network for testing, my another comp is a web server.
Anyway, I don't think that I should worry about these "connections" since they seem to be present even when I'm not connected to internet and they don't make any traffic, but it's just weird.

---

### Post by prshah on 2008-09-18
> **ene_dene said:**
> 
i see 4 connections where I'm the source and some IPs throughout the world are destinations, port 80 http.

Don't want to alarm you, but about last week I read [this article]("http://seclists.org/incidents/2002/Jan/0073.html") which talks about a linux "virus" which uses port 80 to "call home" and attempt to allow "backdoor" access to the linux machine. (OK, it was not _exactly_ this article, but a much more recent one (dated within the past month), but I've lost that link and this is the closest I could get.)

But in that article, apparently the information is sent to only one particular ip address, 207.66.155.21 (ns1.xoasis.com). Further, it seems that the requested content does not currently exist at that address.

In any case, I've blocked outgoing connections to that address: (and after a little thought, incoming as well)```
history | grep ufw
  244  sudo ufw deny to 207.66.155.21 port 80
  245  sudo ufw logging on
  248  sudo ufw deny from 207.66.155.21

```

Maybe you need to do the same. 

Don't want to alarm you, I may be wrong altogether.

---

### Post by ene_dene on 2008-09-18
Is there any way to check if I'm infected by that thing?
I've restarted the comp, and blocked these addresses, the connections are gone, but as an effect of restarting, not blocking by firewall since I'd be noticed by firestarer.

---

### Post by cariboo on 2008-09-18
hat exploit is old that if the system hasn't been patched by now, then there would have been nothing to worry about. Remember any malware has to be installed by root for it to do anything system wide. To avoid this type of problem only install software from trusted sources.

Jim

---

### Post by prshah on 2008-09-18
> **prshah said:**
> (OK, it was not _exactly_ this article, but a much more recent one (dated within the past month), but I've lost that link and this is the closest I could get.)

Don't want to alarm you, I may be wrong altogether.

> **cariboo907 said:**
> hat exploit is old that if the system hasn't been patched by now, 


Found the current, correct link: [http://www.sophos.com/security/blog/2008/09/1748.html](http://www.sophos.com/security/blog/2008/09/1748.html)

Note it's dated 8th September 2008.

You cannot "patch" the system in any way to prevent this from happening; it's a (rootkit) worm. 

However, once again, I reiterate that's it's a long shot and unlikely to be what is affecting the OP.

---

### Post by ene_dene on 2008-09-18
Since the restart I don't have these strange connections. I'm still curious how can I check if I have this? It's said that the most common way for this virus to gain access is via weak ssh pass. In my case that is highly unlikely since my pass is more than 15 random characters, changed port access and I use fail2ban and thats the only port opened on this comp. 
It is a very disturbing article indeed.

---

### Post by ene_dene on 2008-09-19
Update:
again I was surfing, shot down firefox and another address appeared. I wanted to check a little so I used nmapfe scan of that address it was a Unix comp. I saw an 22 port opened and as a test I tried to connect, connection was refused. And after that now I see that I have two new connections to that address I can't get rid of, one is ssh 22 and another one is 1 Tcpmux. So the summary is now I have 3 outbound connections to unknown destination on ports: 80, 22 and 1, disconnecting comp physically, blocking all outbound connectios doesn't help, they just stand there... I guess until the restart... traffic is 0.0kbs.
But this is strange to me, I have a Debian comp in front of this ubuntu comp:
internet -> router (192.168.1.1) -> (eth1) Debian comp (eth0 ->192.168.0.1) -> This ubuntu comp (192.168.0.10).
And I can see every connection on my Debian comp that is made on Ubuntu comp, for example pidgin connections, but I can't see these mysterious connections, like they don't exist (as they seem not to exist). Could it be that there is some roting error or something so ubuntu comp thinks that it's somehow connected?

---

### Post by kevdog on 2008-09-19
What is the boinc_client application?

---

### Post by kpatz on 2008-09-19
The IPs in your original screenshot appear to be:

76.13.216.11: ad1.rtm-1.vip.rm.ac4.yahoo.com
92.37.116.59: an IP in Croatia :confused:
69.63.176.184: channel24.01.05.sf2p.facebook.com

Had you been surfing Facebook prior to running iptstate?

They're all on port 80 so they're http connections.  I'm surprised they still said ESTABLISHED though.  They should say TIME_WAIT once the connection terminates.  Are you running any firewall (iptables rules) or proxy?

Boinc_client is Berkeley's distributed computing project, for SETI@home and related projects.

---

### Post by ene_dene on 2008-09-19
I live in Croatia, so that is the probable cause why one of the addresses is from Croatia. :)
I think that maybe the problem could be the TTL - time to live, all these port 80 connections have a really large time to live. Maybe some servers declare that large time and my comp sticks to that connection until TTL passes. I have one connection now and 103h TTL, I'll see will it still be there in next few days. Why does it say established while phisicaly disconnected... I don't know. I do occasionally use facebook, but I don't remember if I've used it just before checking.
As for a firewall I have a router firewall, then Debian comp uses iptables and it roots the traffic to ubuntu comp, and on that comp I use firestarter, which is GUI for iptables. I have all inbound ports except 22 closed and almost all the outbound ports closed (except 80, 22, 21, mail...). I think that from that viewpoint it's not insecure, but I'm afraid if it is possible that I got something while surfing. I never use root account, nevertheless... if would be nice if there was some way to check for suspicious programs.

---

### Post by prshah on 2008-09-19
> **ene_dene said:**
> 
if would be nice if there was some way to check for suspicious programs.

You can use RKHunter (rootkit huneter). Sorry, can't be more specific, since I've never used it and just heard about it. Apparently it can throw up some disturbing messages, so don't worry too much about anything it finds; post the output here for someone to tell you if you really have a problem.

---

### Post by ene_dene on 2008-09-19
Thanks for this tool. Here's an output:
```
[20:11:43] Running Rootkit Hunter version 1.3.0 on killers2
[20:11:43]
[20:11:43] Info: Start date is Fri Sep 19 20:11:43 CEST 2008
[20:11:43]
[20:11:43] Checking configuration file and command-line options...
[20:11:43] Info: Detected operating system is 'Linux'
[20:11:43] Info: Found O/S name: Ubuntu 8.04.1
[20:11:44] Info: Command line is /usr/bin/rkhunter --check
[20:11:44] Info: Environment shell is /bin/bash; rkhunter is using dash
[20:11:44] Info: Using configuration file '/etc/rkhunter.conf'
[20:11:44] Info: Installation directory is '/usr'
[20:11:44] Info: Using language 'en'
[20:11:44] Info: Using '/var/lib/rkhunter/db' as the database directory
[20:11:44] Info: Using '/usr/share/rkhunter/scripts' as the support script directory
[20:11:44] Info: Using '/usr/local/sbin /usr/local/bin /usr/sbin /usr/bin /sbin /bin /usr/X11R6/bin /bin /usr/bin /sbin /usr/sbin /usr/local/bin /usr/local/sbin /usr/libexec /usr/local/libexec' as the command directories
[20:11:44] Info: Using '/' as the root directory
[20:11:44] Info: Using '/var/lib/rkhunter/tmp' as the temporary directory
[20:11:44] Info: No mail-on-warning address configured
[20:11:44] Info: X will automatically be detected
[20:11:44] Info: Using second color set
[20:11:44] Info: Found the 'diff' command: /usr/bin/diff
[20:11:44] Info: Found the 'file' command: /usr/bin/file
[20:11:44] Info: Found the 'find' command: /usr/bin/find
[20:11:44] Info: Found the 'ifconfig' command: /sbin/ifconfig
[20:11:44] Info: Found the 'ip' command: /sbin/ip
[20:11:44] Info: Found the 'ldd' command: /usr/bin/ldd
[20:11:44] Info: Found the 'lsattr' command: /usr/bin/lsattr
[20:11:44] Info: Found the 'lsmod' command: /sbin/lsmod
[20:11:44] Info: Found the 'lsof' command: /usr/bin/lsof
[20:11:44] Info: Found the 'mktemp' command: /bin/mktemp
[20:11:44] Info: Found the 'netstat' command: /bin/netstat
[20:11:44] Info: Found the 'perl' command: /usr/bin/perl
[20:11:44] Info: Found the 'ps' command: /bin/ps
[20:11:44] Info: Found the 'pwd' command: /bin/pwd
[20:11:44] Info: Found the 'readlink' command: /bin/readlink
[20:11:44] Info: Found the 'sort' command: /usr/bin/sort
[20:11:44] Info: Found the 'stat' command: /usr/bin/stat
[20:11:44] Info: Found the 'strings' command: /usr/bin/strings
[20:11:44] Info: Found the 'uniq' command: /usr/bin/uniq
[20:11:44] Info: System is not using prelinking
[20:11:44] Info: Using the '/usr/bin/sha1sum' command for the file hash checks
[20:11:44] Info: Stored hash values used hash function '/usr/bin/sha1sum'
[20:11:44] Info: Stored hash values did not use a package manager
[20:11:44] Info: The hash function field index is set to 1
[20:11:44] Info: No package manager specified: using hash function '/usr/bin/sha1sum'
[20:11:44] Info: Previous file attributes were stored
[20:11:44] Info: Enabled tests are: all
[20:11:44] Info: Disabled tests are: suspscan hidden_procs deleted_files packet_cap_apps
[20:11:44] Info: Found ksym file '/proc/kallsyms'
[20:11:44]
[20:11:44] Checking if the O/S has changed since last time...
[20:11:45] Info: Nothing seems to have changed
[20:11:45]
[20:11:45] Starting system checks...
[20:11:45]
[20:11:45] Checking system commands...
[20:11:45] Info: Starting test name 'system_commands'
[20:11:45]
[20:11:45] Performing 'strings' command checks
[20:11:45] Info: Starting test name 'strings'
[20:11:45] Scanning for string /usr/sbin/ntpsx               [ OK ]
[20:11:45] Scanning for string /usr/lib/.../ls               [ OK ]
[20:11:45] Scanning for string /usr/lib/.../netstat          [ OK ]
[20:11:45] Scanning for string /usr/lib/.../lsof             [ OK ]
[20:11:45] Scanning for string /usr/lib/.../bkit-ssh/bkit-shdcfg [ OK ]
[20:11:45] Scanning for string /usr/lib/.../bkit-ssh/bkit-shhk [ OK ]
[20:11:45] Scanning for string /usr/lib/.../bkit-ssh/bkit-pw [ OK ]
[20:11:45] Scanning for string /usr/lib/.../bkit-ssh/bkit-shrs [ OK ]
[20:11:45] Scanning for string /usr/lib/.../uconf.inv        [ OK ]
[20:11:45] Scanning for string /usr/lib/.../psr              [ OK ]
[20:11:45] Scanning for string /usr/lib/.../find             [ OK ]
[20:11:45] Scanning for string /usr/lib/.../pstree           [ OK ]
[20:11:45] Scanning for string /usr/lib/.../slocate          [ OK ]
[20:11:45] Scanning for string /usr/lib/.../du               [ OK ]
[20:11:45] Scanning for string /usr/lib/.../top              [ OK ]
[20:11:46] Scanning for string /usr/lib/...                  [ OK ]
[20:11:46] Scanning for string /usr/lib/.../bkit-ssh         [ OK ]
[20:11:46] Scanning for string /usr/lib/.bkit-               [ OK ]
[20:11:46] Scanning for string /tmp/.bkp                     [ OK ]
[20:11:46] Scanning for string /tmp/.cinik                   [ OK ]
[20:11:46] Scanning for string /tmp/.font-unix/.cinik        [ OK ]
[20:11:46] Scanning for string /lib/.sso                     [ OK ]
[20:11:46] Scanning for string /lib/.so                      [ OK ]
[20:11:46] Scanning for string /var/run/...dica/clean        [ OK ]
[20:11:46] Scanning for string /var/run/...dica/xl           [ OK ]
[20:11:46] Scanning for string /var/run/...dica/xdr          [ OK ]
[20:11:46] Scanning for string /var/run/...dica/psg          [ OK ]
[20:11:46] Scanning for string /var/run/...dica/secure       [ OK ]
[20:11:46] Scanning for string /var/run/...dica/rdx          [ OK ]
[20:11:46] Scanning for string /var/run/...dica/va           [ OK ]
[20:11:46] Scanning for string /var/run/...dica/cl.sh        [ OK ]
[20:11:46] Scanning for string /usr/bin/.etc                 [ OK ]
[20:11:46] Scanning for string /usr/lib/.fx/sched_host.2     [ OK ]
[20:11:46] Scanning for string /usr/lib/.fx/random_d.2       [ OK ]
[20:11:46] Scanning for string /usr/lib/.fx/set_pid.2        [ OK ]
[20:11:47] Scanning for string /usr/lib/.fx/cons.saver       [ OK ]
[20:11:47] Scanning for string /usr/lib/.fx/adore/adore/adore.ko [ OK ]
[20:11:47] Scanning for string /bin/sysback                  [ OK ]
[20:11:47] Scanning for string /usr/local/bin/sysback        [ OK ]
[20:11:47] Scanning for string /usr/lib/.tbd                 [ OK ]
[20:11:47] Scanning for string /dev/.lib/lib/lib/t0rns       [ OK ]
[20:11:47] Scanning for string /dev/.lib/lib/lib/du          [ OK ]
[20:11:47] Scanning for string /dev/.lib/lib/lib/ls          [ OK ]
[20:11:47] Scanning for string /dev/.lib/lib/lib/t0rnsb      [ OK ]
[20:11:47] Scanning for string /dev/.lib/lib/lib/ps          [ OK ]
[20:11:47] Scanning for string /dev/.lib/lib/lib/t0rnp       [ OK ]
[20:11:47] Scanning for string /dev/.lib/lib/lib/find        [ OK ]
[20:11:47] Scanning for string /dev/.lib/lib/lib/ifconfig    [ OK ]
[20:11:47] Scanning for string /dev/.lib/lib/lib/pg          [ OK ]
[20:11:47] Scanning for string /dev/.lib/lib/lib/ssh.tgz     [ OK ]
[20:11:47] Scanning for string /dev/.lib/lib/lib/top         [ OK ]
[20:11:47] Scanning for string /dev/.lib/lib/lib/sz          [ OK ]
[20:11:47] Scanning for string /dev/.lib/lib/lib/login       [ OK ]
[20:11:47] Scanning for string /dev/.lib/lib/lib/in.fingerd  [ OK ]
[20:11:47] Scanning for string /dev/.lib/lib/lib/1i0n.sh     [ OK ]
[20:11:47] Scanning for string /dev/.lib/lib/lib/pstree      [ OK ]
[20:11:48] Scanning for string /dev/.lib/lib/lib/in.telnetd  [ OK ]
[20:11:48] Scanning for string /dev/.lib/lib/lib/mjy         [ OK ]
[20:11:48] Scanning for string /dev/.lib/lib/lib/sush        [ OK ]
[20:11:48] Scanning for string /dev/.lib/lib/lib/tfn         [ OK ]
[20:11:48] Scanning for string /dev/.lib/lib/lib/name        [ OK ]
[20:11:48] Scanning for string /dev/.lib/lib/lib/getip.sh    [ OK ]
[20:11:48] Scanning for string /usr/info/.torn/sh*           [ OK ]
[20:11:48] Scanning for string /usr/src/.****/.1addr         [ OK ]
[20:11:48] Scanning for string /usr/src/.****/.1file         [ OK ]
[20:11:48] Scanning for string /usr/src/.****/.1proc         [ OK ]
[20:11:48] Scanning for string /usr/src/.****/.1logz         [ OK ]
[20:11:48] Scanning for string /usr/info/.t0rn               [ OK ]
[20:11:48] Scanning for string /dev/.lib                     [ OK ]
[20:11:48] Scanning for string /dev/.lib/lib                 [ OK ]
[20:11:48] Scanning for string /dev/.lib/lib/lib             [ OK ]
[20:11:48] Scanning for string /dev/.lib/lib/lib/dev         [ OK ]
[20:11:48] Scanning for string /dev/.lib/lib/scan            [ OK ]
[20:11:48] Scanning for string /usr/src/.****                [ OK ]
[20:11:48] Scanning for string /usr/man/man1/man1            [ OK ]
[20:11:48] Scanning for string /usr/man/man1/man1/lib        [ OK ]
[20:11:48] Scanning for string /usr/man/man1/man1/lib/.lib   [ OK ]
[20:11:49] Scanning for string /usr/man/man1/man1/lib/.lib/.backup [ OK ]
[20:11:49]
[20:11:49] Performing 'shared libraries' checks
[20:11:49] Info: Starting test name 'shared_libs'
[20:11:49] Checking for preloading variables                 [ None found ]
[20:11:49] Checking for preload file                         [ Not found ]
[20:11:49] Info: Starting test name 'shared_libs_path'
[20:11:49] Checking LD_LIBRARY_PATH variable                 [ Not found ]
[20:11:49]
[20:11:49] Performing file properties checks
[20:11:49] Info: Starting test name 'properties'
[20:11:49] Checking for prerequisites                        [ OK ]
[20:11:49] /bin/bash                                         [ OK ]
[20:11:50] /bin/cat                                          [ OK ]
[20:11:50] /bin/chmod                                        [ OK ]
[20:11:50] /bin/chown                                        [ OK ]
[20:11:50] /bin/cp                                           [ OK ]
[20:11:50] /bin/date                                         [ OK ]
[20:11:51] /bin/df                                           [ OK ]
[20:11:51] /bin/dmesg                                        [ OK ]
[20:11:51] /bin/echo                                         [ OK ]
[20:11:51] /bin/ed                                           [ OK ]
[20:11:51] /bin/egrep                                        [ OK ]
[20:11:51] Info: Found file '/bin/egrep': it is whitelisted for the 'script replacement' check.
[20:11:52] /bin/fgrep                                        [ OK ]
[20:11:52] Info: Found file '/bin/fgrep': it is whitelisted for the 'script replacement' check.
[20:11:52] /bin/grep                                         [ OK ]
[20:11:52] /bin/ip                                           [ OK ]
[20:11:52] /bin/kill                                         [ OK ]
[20:11:52] /bin/login                                        [ OK ]
[20:11:53] /bin/ls                                           [ OK ]
[20:11:53] /bin/lsmod                                        [ OK ]
[20:11:53] /bin/mktemp                                       [ OK ]
[20:11:53] /bin/more                                         [ OK ]
[20:11:53] /bin/mount                                        [ OK ]
[20:11:54] /bin/mv                                           [ OK ]
[20:11:54] /bin/netstat                                      [ OK ]
[20:11:54] /bin/ps                                           [ OK ]
[20:11:54] /bin/pwd                                          [ OK ]
[20:11:54] /bin/readlink                                     [ OK ]
[20:11:55] /bin/sed                                          [ OK ]
[20:11:55] /bin/sh                                           [ OK ]
[20:11:55] /bin/su                                           [ OK ]
[20:11:55] /bin/touch                                        [ OK ]
[20:11:55] /bin/uname                                        [ OK ]
[20:11:56] /bin/which                                        [ OK ]
[20:11:56] Info: Found file '/bin/which': it is whitelisted for the 'script replacement' check.
[20:11:56] /bin/dash                                         [ OK ]
[20:11:56] /usr/bin/awk                                      [ OK ]
[20:11:56] /usr/bin/basename                                 [ OK ]
[20:11:57] /usr/bin/chattr                                   [ OK ]
[20:11:57] /usr/bin/cut                                      [ OK ]
[20:11:57] /usr/bin/diff                                     [ OK ]
[20:11:57] /usr/bin/dirname                                  [ OK ]
[20:11:57] /usr/bin/dpkg                                     [ OK ]
[20:11:58] /usr/bin/dpkg-query                               [ OK ]
[20:11:58] /usr/bin/du                                       [ OK ]
[20:11:58] /usr/bin/env                                      [ OK ]
[20:11:58] /usr/bin/file                                     [ OK ]
[20:11:58] /usr/bin/find                                     [ OK ]
[20:11:59] /usr/bin/GET                                      [ OK ]
[20:11:59] /usr/bin/groups                                   [ OK ]
[20:11:59] Info: Found file '/usr/bin/groups': it is whitelisted for the 'script replacement' check.
[20:11:59] /usr/bin/head                                     [ OK ]
[20:11:59] /usr/bin/id                                       [ OK ]
[20:11:59] /usr/bin/killall                                  [ OK ]
[20:12:00] /usr/bin/last                                     [ OK ]
[20:12:00] /usr/bin/lastlog                                  [ OK ]
[20:12:00] /usr/bin/ldd                                      [ OK ]
[20:12:00] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.
[20:12:00] /usr/bin/less                                     [ OK ]
[20:12:00] /usr/bin/locate                                   [ OK ]
[20:12:01] /usr/bin/logger                                   [ OK ]
[20:12:01] /usr/bin/lsattr                                   [ OK ]
[20:12:01] /usr/bin/lsof                                     [ OK ]
[20:12:01] /usr/bin/md5sum                                   [ OK ]
[20:12:01] /usr/bin/mlocate                                  [ OK ]
[20:12:02] /usr/bin/newgrp                                   [ OK ]
[20:12:02] /usr/bin/passwd                                   [ OK ]
[20:12:02] /usr/bin/perl                                     [ OK ]
[20:12:02] /usr/bin/pstree                                   [ OK ]
[20:12:02] /usr/bin/rkhunter                                 [ OK ]
[20:12:03] /usr/bin/runcon                                   [ OK ]
[20:12:03] /usr/bin/sha1sum                                  [ OK ]
[20:12:03] /usr/bin/size                                     [ OK ]
[20:12:03] /usr/bin/sort                                     [ OK ]
[20:12:03] /usr/bin/stat                                     [ OK ]
[20:12:04] /usr/bin/strace                                   [ OK ]
[20:12:04] /usr/bin/strings                                  [ OK ]
[20:12:04] /usr/bin/sudo                                     [ OK ]
[20:12:04] /usr/bin/tail                                     [ OK ]
[20:12:04] /usr/bin/test                                     [ OK ]
[20:12:04] /usr/bin/top                                      [ OK ]
[20:12:05] /usr/bin/touch                                    [ OK ]
[20:12:05] /usr/bin/tr                                       [ OK ]
[20:12:05] /usr/bin/uniq                                     [ OK ]
[20:12:05] /usr/bin/users                                    [ OK ]
[20:12:05] /usr/bin/vmstat                                   [ OK ]
[20:12:05] /usr/bin/w                                        [ OK ]
[20:12:06] /usr/bin/watch                                    [ OK ]
[20:12:06] /usr/bin/wc                                       [ OK ]
[20:12:06] /usr/bin/wget                                     [ OK ]
[20:12:06] /usr/bin/whatis                                   [ OK ]
[20:12:06] /usr/bin/whereis                                  [ OK ]
[20:12:07] /usr/bin/which                                    [ OK ]
[20:12:07] /usr/bin/who                                      [ OK ]
[20:12:07] /usr/bin/whoami                                   [ OK ]
[20:12:07] /usr/bin/gawk                                     [ OK ]
[20:12:07] /usr/bin/lwp-request                              [ OK ]
[20:12:07] Info: Found file '/usr/bin/lwp-request': it is whitelisted for the 'script replacement' check.
[20:12:07] /usr/bin/w.procps                                 [ OK ]
[20:12:08] /sbin/depmod                                      [ OK ]
[20:12:08] /sbin/ifconfig                                    [ OK ]
[20:12:08] /sbin/ifdown                                      [ OK ]
[20:12:09] /sbin/ifup                                        [ OK ]
[20:12:09] /sbin/init                                        [ OK ]
[20:12:09] /sbin/insmod                                      [ OK ]
[20:12:09] /sbin/ip                                          [ OK ]
[20:12:09] /sbin/lsmod                                       [ OK ]
[20:12:10] /sbin/modinfo                                     [ OK ]
[20:12:10] /sbin/modprobe                                    [ OK ]
[20:12:10] /sbin/rmmod                                       [ OK ]
[20:12:10] /sbin/runlevel                                    [ OK ]
[20:12:11] /sbin/sulogin                                     [ OK ]
[20:12:11] /sbin/sysctl                                      [ OK ]
[20:12:11] /sbin/syslogd                                     [ OK ]
[20:12:11] /usr/sbin/adduser                                 [ OK ]
[20:12:11] Info: Found file '/usr/sbin/adduser': it is whitelisted for the 'script replacement' check.
[20:12:12] /usr/sbin/chroot                                  [ OK ]
[20:12:12] /usr/sbin/cron                                    [ OK ]
[20:12:12] /usr/sbin/groupadd                                [ OK ]
[20:12:13] /usr/sbin/groupdel                                [ OK ]
[20:12:13] /usr/sbin/groupmod                                [ OK ]
[20:12:13] /usr/sbin/grpck                                   [ OK ]
[20:12:13] /usr/sbin/nologin                                 [ OK ]
[20:12:14] /usr/sbin/pwck                                    [ OK ]
[20:12:14] /usr/sbin/tcpd                                    [ OK ]
[20:12:14] /usr/sbin/useradd                                 [ OK ]
[20:12:15] /usr/sbin/userdel                                 [ OK ]
[20:12:15] /usr/sbin/usermod                                 [ OK ]
[20:12:15] /usr/sbin/vipw                                    [ OK ]
[20:12:22]
[20:12:22] Checking for rootkits...
[20:12:22] Info: Starting test name 'rootkits'
[20:12:22]
[20:12:22] Performing check of known rootkit files and directories
[20:12:22] Info: Starting test name 'known_rkts'
[20:12:22]
[20:12:22] Checking for 55808 Trojan - Variant A...
[20:12:22]   Checking for file '/tmp/.../r'                  [ Not found ]
[20:12:22]   Checking for file '/tmp/.../a'                  [ Not found ]
[20:12:22] 55808 Trojan - Variant A                          [ Not found ]
[20:12:22]
[20:12:22] Checking for ADM Worm...
[20:12:22]   Checking for string 'w0rm'                      [ Not found ]
[20:12:22] ADM Worm                                          [ Not found ]
[20:12:22]
[20:12:22] Checking for AjaKit Rootkit...
[20:12:22]   Checking for file '/dev/tux/.addr'              [ Not found ]
[20:12:22]   Checking for file '/dev/tux/.proc'              [ Not found ]
[20:12:22]   Checking for file '/dev/tux/.file'              [ Not found ]
[20:12:22]   Checking for file '/lib/.libgh-gh/cleaner'      [ Not found ]
[20:12:22]   Checking for file '/lib/.libgh-gh/Patch/patch'  [ Not found ]
[20:12:22]   Checking for file '/lib/.libgh-gh/sb0k'         [ Not found ]
[20:12:22]   Checking for directory '/dev/tux'               [ Not found ]
[20:12:23]   Checking for directory '/lib/.libgh-gh'         [ Not found ]
[20:12:23] AjaKit Rootkit                                    [ Not found ]
[20:12:23]
[20:12:23] Checking for aPa Kit...
[20:12:23]   Checking for file '/usr/share/.aPa'             [ Not found ]
[20:12:23] aPa Kit                                           [ Not found ]
[20:12:23]
[20:12:23] Checking for Apache Worm...
[20:12:23]   Checking for file '/bin/.log'                   [ Not found ]
[20:12:23] Apache Worm                                       [ Not found ]
[20:12:23]
[20:12:23] Checking for Ambient (ark) Rootkit...
[20:12:23]   Checking for file '/usr/lib/.ark?'              [ Not found ]
[20:12:23]   Checking for file '/dev/ptyxx/.log'             [ Not found ]
[20:12:23]   Checking for file '/dev/ptyxx/.file'            [ Not found ]
[20:12:23]   Checking for directory '/dev/ptyxx'             [ Not found ]
[20:12:23] Ambient (ark) Rootkit                             [ Not found ]
[20:12:23]
[20:12:23] Checking for Balaur Rootkit...
[20:12:23]   Checking for file '/usr/lib/liblog.o'           [ Not found ]
[20:12:23]   Checking for directory '/usr/lib/.kinetic'      [ Not found ]
[20:12:23]   Checking for directory '/usr/lib/.egcs'         [ Not found ]
[20:12:23]   Checking for directory '/usr/lib/.wormie'       [ Not found ]
[20:12:23] Balaur Rootkit                                    [ Not found ]
[20:12:24]
[20:12:24] Checking for BeastKit Rootkit...
[20:12:24]   Checking for file '/usr/sbin/arobia'            [ Not found ]
[20:12:24]   Checking for file '/usr/sbin/idrun'             [ Not found ]
[20:12:24]   Checking for file '/usr/lib/elm/arobia/elm'     [ Not found ]
[20:12:24]   Checking for file '/usr/lib/elm/arobia/elm/hk'  [ Not found ]
[20:12:24]   Checking for file '/usr/lib/elm/arobia/elm/hk.pub' [ Not found ]
[20:12:24]   Checking for file '/usr/lib/elm/arobia/elm/sc'  [ Not found ]
[20:12:24]   Checking for file '/usr/lib/elm/arobia/elm/sd.pp' [ Not found ]
[20:12:24]   Checking for file '/usr/lib/elm/arobia/elm/sdco' [ Not found ]
[20:12:24]   Checking for file '/usr/lib/elm/arobia/elm/srsd' [ Not found ]
[20:12:24]   Checking for directory '/lib/ldd.so/bktools'    [ Not found ]
[20:12:24] BeastKit Rootkit                                  [ Not found ]
[20:12:24]
[20:12:24] Checking for beX2 Rootkit...
[20:12:24]   Checking for directory '/usr/include/bex'       [ Not found ]
[20:12:24] beX2 Rootkit                                      [ Not found ]
[20:12:24]
[20:12:24] Checking for BOBKit Rootkit...
[20:12:24]   Checking for file '/usr/sbin/ntpsx'             [ Not found ]
[20:12:24]   Checking for file '/usr/lib/.../ls'             [ Not found ]
[20:12:24]   Checking for file '/usr/lib/.../netstat'        [ Not found ]
[20:12:24]   Checking for file '/usr/lib/.../lsof'           [ Not found ]
[20:12:24]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shdcfg' [ Not found ]
[20:12:25]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shhk' [ Not found ]
[20:12:25]   Checking for file '/usr/lib/.../bkit-ssh/bkit-pw' [ Not found ]
[20:12:25]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shrs' [ Not found ]
[20:12:25]   Checking for file '/usr/lib/.../uconf.inv'      [ Not found ]
[20:12:25]   Checking for file '/usr/lib/.../psr'            [ Not found ]
[20:12:25]   Checking for file '/usr/lib/.../find'           [ Not found ]
[20:12:25]   Checking for file '/usr/lib/.../pstree'         [ Not found ]
[20:12:25]   Checking for file '/usr/lib/.../slocate'        [ Not found ]
[20:12:25]   Checking for file '/usr/lib/.../du'             [ Not found ]
[20:12:25]   Checking for file '/usr/lib/.../top'            [ Not found ]
[20:12:25]   Checking for directory '/usr/lib/...'           [ Not found ]
[20:12:25]   Checking for directory '/usr/lib/.../bkit-ssh'  [ Not found ]
[20:12:25]   Checking for directory '/usr/lib/.bkit-'        [ Not found ]
[20:12:25]   Checking for directory '/tmp/.bkp'              [ Not found ]
[20:12:25] BOBKit Rootkit                                    [ Not found ]
[20:12:25]
[20:12:25] Checking for CiNIK Worm (Slapper.B variant)...
[20:12:25]   Checking for file '/tmp/.cinik'                 [ Not found ]
[20:12:25]   Checking for directory '/tmp/.font-unix/.cinik' [ Not found ]
[20:12:25] CiNIK Worm (Slapper.B variant)                    [ Not found ]
[20:12:25]
[20:12:25] Checking for Danny-Boy's Abuse Kit...
[20:12:25]   Checking for file '/dev/mdev'                   [ Not found ]
[20:12:25]   Checking for file '/usr/lib/libX.a'             [ Not found ]
[20:12:26] Danny-Boy's Abuse Kit                             [ Not found ]
[20:12:26]
[20:12:26] Checking for Devil RootKit...
[20:12:26]   Checking for file '/var/lib/games/.src'         [ Not found ]
[20:12:26]   Checking for file '/dev/dsx'                    [ Not found ]
[20:12:26]   Checking for file '/dev/caca'                   [ Not found ]
[20:12:26] Devil RootKit                                     [ Not found ]
[20:12:26]
[20:12:26] Checking for Dica-Kit Rootkit...
[20:12:26]   Checking for file '/lib/.sso'                   [ Not found ]
[20:12:26]   Checking for file '/lib/.so'                    [ Not found ]
[20:12:26]   Checking for file '/var/run/...dica/clean'      [ Not found ]
[20:12:26]   Checking for file '/var/run/...dica/xl'         [ Not found ]
[20:12:26]   Checking for file '/var/run/...dica/xdr'        [ Not found ]
[20:12:26]   Checking for file '/var/run/...dica/psg'        [ Not found ]
[20:12:26]   Checking for file '/var/run/...dica/secure'     [ Not found ]
[20:12:26]   Checking for file '/var/run/...dica/rdx'        [ Not found ]
[20:12:26]   Checking for file '/var/run/...dica/va'         [ Not found ]
[20:12:26]   Checking for file '/var/run/...dica/cl.sh'      [ Not found ]
[20:12:26]   Checking for file '/usr/bin/.etc'               [ Not found ]
[20:12:26]   Checking for directory '/var/run/...dica'       [ Not found ]
[20:12:26]   Checking for directory '/var/run/...dica/mh'    [ Not found ]
[20:12:26]   Checking for directory '/var/run/...dica/scan'  [ Not found ]
[20:12:27] Dica-Kit Rootkit                                  [ Not found ]
[20:12:27]
[20:12:27] Checking for Dreams Rootkit...
[20:12:27]   Checking for file '/dev/ttyoa'                  [ Not found ]
[20:12:27]   Checking for file '/dev/ttyof'                  [ Not found ]
[20:12:27]   Checking for file '/dev/ttyop'                  [ Not found ]
[20:12:27]   Checking for file '/usr/bin/sense'              [ Not found ]
[20:12:27]   Checking for file '/usr/bin/sl2'                [ Not found ]
[20:12:27]   Checking for file '/usr/bin/logclear'           [ Not found ]
[20:12:27]   Checking for file '/usr/bin/(swapd)'            [ Not found ]
[20:12:27]   Checking for file '/usr/bin/snfs'               [ Not found ]
[20:12:27]   Checking for file '/usr/lib/libsss'             [ Not found ]
[20:12:27]   Checking for directory '/dev/ida/.hpd'          [ Not found ]
[20:12:27] Dreams Rootkit                                    [ Not found ]
[20:12:27]
[20:12:27] Checking for Duarawkz Rootkit...
[20:12:27]   Checking for file '/usr/bin/duarawkz/loginpass' [ Not found ]
[20:12:27]   Checking for directory '/usr/bin/duarawkz'      [ Not found ]
[20:12:27] Duarawkz Rootkit                                  [ Not found ]
[20:12:27]
[20:12:27] Checking for Enye LKM...
[20:12:27]   Checking for file '/etc/.enyelkmHIDE^IT.ko'     [ Not found ]
[20:12:27] Enye LKM                                          [ Not found ]
[20:12:28]
[20:12:28] Checking for Flea Linux Rootkit...
[20:12:28]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[20:12:28]   Checking for file '/lib/security/.config/ssh/ssh_host_key' [ Not found ]
[20:12:28]   Checking for file '/lib/security/.config/ssh/ssh_host_key.pub' [ Not found ]
[20:12:28]   Checking for file '/lib/security/.config/ssh/ssh_random_seed' [ Not found ]
[20:12:28]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[20:12:28]   Checking for file '/usr/lib/ldlibns.so'         [ Not found ]
[20:12:28]   Checking for file '/usr/lib/ldlibpst.so'        [ Not found ]
[20:12:28]   Checking for file '/usr/lib/ldlibdu.so'         [ Not found ]
[20:12:28]   Checking for file '/usr/lib/ldlibct.so'         [ Not found ]
[20:12:28]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[20:12:28]   Checking for directory '/dev/..0'               [ Not found ]
[20:12:28]   Checking for directory '/dev/..0/backup'        [ Not found ]
[20:12:28] Flea Linux Rootkit                                [ Not found ]
[20:12:28]
[20:12:28] Checking for FreeBSD Rootkit...
[20:12:28]   Checking for file '/usr/lib/.fx/sched_host.2'   [ Not found ]
[20:12:28]   Checking for file '/usr/lib/.fx/random_d.2'     [ Not found ]
[20:12:28]   Checking for file '/usr/lib/.fx/set_pid.2'      [ Not found ]
[20:12:28]   Checking for file '/usr/lib/.fx/cons.saver'     [ Not found ]
[20:12:28]   Checking for file '/usr/lib/.fx/adore/adore/adore.ko' [ Not found ]
[20:12:28]   Checking for file '/bin/sysback'                [ Not found ]
[20:12:29]   Checking for file '/usr/local/bin/sysback'      [ Not found ]
[20:12:29]   Checking for directory '/usr/lib/.fx'           [ Not found ]
[20:12:29]   Checking for directory '/usr/lib/.fx/adore'     [ Not found ]
[20:12:29] FreeBSD Rootkit                                   [ Not found ]
[20:12:29]
[20:12:29] Checking for ****`it Rootkit...
[20:12:29]   Checking for file '/dev/proc/fuckit/hax0r'      [ Not found ]
[20:12:29]   Checking for file '/dev/proc/fuckit/hax0rshell' [ Not found ]
[20:12:29]   Checking for file '/dev/proc/fuckit/config/lports' [ Not found ]
[20:12:29]   Checking for file '/dev/proc/fuckit/config/rports' [ Not found ]
[20:12:29]   Checking for file '/dev/proc/fuckit/config/rkconf' [ Not found ]
[20:12:29]   Checking for file '/dev/proc/fuckit/config/password' [ Not found ]
[20:12:29]   Checking for file '/dev/proc/fuckit/config/progs' [ Not found ]
[20:12:29]   Checking for file '/dev/proc/system-bins/init'  [ Not found ]
[20:12:29] ****`it Rootkit                                   [ Not found ]
[20:12:29]
[20:12:29] Checking for GasKit Rootkit...
[20:12:29]   Checking for file '/dev/dev/gaskit/sshd/sshdd'  [ Not found ]
[20:12:29]   Checking for directory '/dev/dev'               [ Not found ]
[20:12:29]   Checking for directory '/dev/dev/gaskit'        [ Not found ]
[20:12:29]   Checking for directory '/dev/dev/gaskit/sshd'   [ Not found ]
[20:12:29] GasKit Rootkit                                    [ Not found ]
[20:12:29]
[20:12:29] Checking for Heroin LKM...
[20:12:30]   Checking for kernel symbol 'heroin'             [ Not found ]
[20:12:30] Heroin LKM                                        [ Not found ]
[20:12:30]
[20:12:30] Checking for HjC Kit...
[20:12:30]   Checking for directory '/dev/.hijackerz'        [ Not found ]
[20:12:30] HjC Kit                                           [ Not found ]
[20:12:30]
[20:12:30] Checking for ignoKit Rootkit...
[20:12:30]   Checking for file '/lib/defs/p'                 [ Not found ]
[20:12:30]   Checking for file '/lib/defs/q'                 [ Not found ]
[20:12:30]   Checking for file '/lib/defs/r'                 [ Not found ]
[20:12:30]   Checking for file '/lib/defs/s'                 [ Not found ]
[20:12:30]   Checking for file '/lib/defs/t'                 [ Not found ]
[20:12:30]   Checking for file '/usr/lib/defs/p'             [ Not found ]
[20:12:30]   Checking for file '/usr/lib/defs/q'             [ Not found ]
[20:12:30]   Checking for file '/usr/lib/defs/r'             [ Not found ]
[20:12:30]   Checking for file '/usr/lib/defs/s'             [ Not found ]
[20:12:30]   Checking for file '/usr/lib/defs/t'             [ Not found ]
[20:12:30]   Checking for file '/usr/lib/.libigno/pkunsec'   [ Not found ]
[20:12:30]   Checking for file '/usr/lib/.libigno/.igno/psybnc/psybnc' [ Not found ]
[20:12:30]   Checking for directory '/usr/lib/.libigno'      [ Not found ]
[20:12:31]   Checking for directory '/usr/lib/.libigno/.igno' [ Not found ]
[20:12:31] ignoKit Rootkit                                   [ Not found ]
[20:12:31]
[20:12:31] Checking for ImperalsS-FBRK Rootkit...
[20:12:31]   Checking for directory '/dev/fd/.88'            [ Not found ]
[20:12:31]   Checking for directory '/dev/fd/.99'            [ Not found ]
[20:12:31] ImperalsS-FBRK Rootkit                            [ Not found ]
[20:12:31]
[20:12:31] Checking for Irix Rootkit...
[20:12:31]   Checking for directory '/dev/pts/01'            [ Not found ]
[20:12:31]   Checking for directory '/dev/pts/01/backup'     [ Not found ]
[20:12:31]   Checking for directory '/dev/pts/01/etc'        [ Not found ]
[20:12:31]   Checking for directory '/dev/pts/01/tmp'        [ Not found ]
[20:12:31] Irix Rootkit                                      [ Not found ]
[20:12:31]
[20:12:31] Checking for Kitko Rootkit...
[20:12:31]   Checking for directory '/usr/src/redhat/SRPMS/...' [ Not found ]
[20:12:31] Kitko Rootkit                                     [ Not found ]
[20:12:31]
[20:12:31] Checking for Knark Rootkit...
[20:12:31]   Checking for file '/proc/knark/pids'            [ Not found ]
[20:12:31]   Checking for directory '/proc/knark'            [ Not found ]
[20:12:31] Knark Rootkit                                     [ Not found ]
[20:12:31]
[20:12:31] Checking for Li0n Worm...
[20:12:32]   Checking for file '/bin/in.telnetd'             [ Not found ]
[20:12:32]   Checking for file '/bin/mjy'                    [ Not found ]
[20:12:32]   Checking for file '/usr/man/man1/man1/lib/.lib/mjy' [ Not found ]
[20:12:32]   Checking for file '/usr/man/man1/man1/lib/.lib/in.telnetd' [ Not found ]
[20:12:32]   Checking for file '/usr/man/man1/man1/lib/.lib/.x' [ Not found ]
[20:12:32]   Checking for file '/dev/.lib/lib/scan/1i0n.sh'  [ Not found ]
[20:12:32]   Checking for file '/dev/.lib/lib/scan/hack.sh'  [ Not found ]
[20:12:32]   Checking for file '/dev/.lib/lib/scan/bind'     [ Not found ]
[20:12:32]   Checking for file '/dev/.lib/lib/scan/randb'    [ Not found ]
[20:12:32]   Checking for file '/dev/.lib/lib/scan/scan.sh'  [ Not found ]
[20:12:32]   Checking for file '/dev/.lib/lib/scan/pscan'    [ Not found ]
[20:12:32]   Checking for file '/dev/.lib/lib/scan/star.sh'  [ Not found ]
[20:12:32]   Checking for file '/dev/.lib/lib/scan/bindx.sh' [ Not found ]
[20:12:32]   Checking for file '/dev/.lib/lib/scan/bindname.log' [ Not found ]
[20:12:32]   Checking for file '/dev/.lib/lib/1i0n.sh'       [ Not found ]
[20:12:32]   Checking for file '/dev/.lib/lib/lib/netstat'   [ Not found ]
[20:12:32]   Checking for file '/dev/.lib/lib/lib/dev/.1addr' [ Not found ]
[20:12:32]   Checking for file '/dev/.lib/lib/lib/dev/.1logz' [ Not found ]
[20:12:32]   Checking for file '/dev/.lib/lib/lib/dev/.1proc' [ Not found ]
[20:12:32]   Checking for file '/dev/.lib/lib/lib/dev/.1file' [ Not found ]
[20:12:32] Li0n Worm                                         [ Not found ]
[20:12:32]
[20:12:32] Checking for Lockit / LJK2 Rootkit...
[20:12:32]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_config' [ Not found ]
[20:12:33]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key' [ Not found ]
[20:12:33]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key.pub' [ Not found ]
[20:12:33]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_random_seed*' [ Not found ]
[20:12:33]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshd_config' [ Not found ]
[20:12:33]   Checking for file '/usr/lib/libmen.oo/.LJK2/backdoor/RK1bd' [ Not found ]
[20:12:33]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/du' [ Not found ]
[20:12:33]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ifconfig' [ Not found ]
[20:12:33]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/inetd.conf' [ Not found ]
[20:12:33]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/locate' [ Not found ]
[20:12:33]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/login' [ Not found ]
[20:12:33]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ls' [ Not found ]
[20:12:33]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/netstat' [ Not found ]
[20:12:33]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ps' [ Not found ]
[20:12:33]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/pstree' [ Not found ]
[20:12:33]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/rc.sysinit' [ Not found ]
[20:12:33]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/syslogd' [ Not found ]
[20:12:33]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/tcpd' [ Not found ]
[20:12:33]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/top' [ Not found ]
[20:12:33]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1sauber' [ Not found ]
[20:12:33]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1wted' [ Not found ]
[20:12:33]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1parser' [ Not found ]
[20:12:33]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1sniff' [ Not found ]
[20:12:34]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1addr' [ Not found ]
[20:12:34]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1dir' [ Not found ]
[20:12:34]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1log' [ Not found ]
[20:12:34]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1proc' [ Not found ]
[20:12:34]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/RK1phidemod.c' [ Not found ]
[20:12:34]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/README.modules' [ Not found ]
[20:12:34]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1hidem.c' [ Not found ]
[20:12:34]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1phide' [ Not found ]
[20:12:34]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshconfig/RK1ssh' [ Not found ]
[20:12:34]   Checking for directory '/usr/lib/libmen.oo/.LJK2' [ Not found ]
[20:12:34] Lockit / LJK2 Rootkit                             [ Not found ]
[20:12:34]
[20:12:34] Checking for Mood-NT Rootkit...
[20:12:34]   Checking for file '/sbin/init__mood-nt-_-_cthulhu' [ Not found ]
[20:12:34]   Checking for file '/_cthulhu/mood-nt.init'      [ Not found ]
[20:12:34]   Checking for file '/_cthulhu/mood-nt.conf'      [ Not found ]
[20:12:34]   Checking for file '/_cthulhu/mood-nt.sniff'     [ Not found ]
[20:12:34]   Checking for directory '/_cthulhu'              [ Not found ]
[20:12:34] Mood-NT Rootkit                                   [ Not found ]
[20:12:34]
[20:12:34] Checking for MRK Rootkit...
[20:12:34]   Checking for file '/dev/ida/.inet/pid'          [ Not found ]
[20:12:35]   Checking for file '/dev/ida/.inet/ssh_host_key' [ Not found ]
[20:12:35]   Checking for file '/dev/ida/.inet/ssh_random_seed' [ Not found ]
[20:12:35]   Checking for file '/dev/ida/.inet/tcp.log'      [ Not found ]
[20:12:35]   Checking for directory '/dev/ida/.inet'         [ Not found ]
[20:12:35]   Checking for directory '/var/spool/cron/.sh'    [ Not found ]
[20:12:35] MRK Rootkit                                       [ Not found ]
[20:12:35]
[20:12:35] Checking for Ni0 Rootkit...
[20:12:35]   Checking for file '/var/lock/subsys/...datafile.../...net...' [ Not found ]
[20:12:35]   Checking for file '/var/lock/subsys/...datafile.../...port...' [ Not found ]
[20:12:35]   Checking for file '/var/lock/subsys/...datafile.../...ps...' [ Not found ]
[20:12:35]   Checking for file '/var/lock/subsys/...datafile.../...file...' [ Not found ]
[20:12:35]   Checking for directory '/tmp/waza'              [ Not found ]
[20:12:35]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[20:12:35]   Checking for directory '/usr/sbin/es'           [ Not found ]
[20:12:35] Ni0 Rootkit                                       [ Not found ]
[20:12:35]
[20:12:35] Checking for Ohhara Rootkit...
[20:12:35]   Checking for file '/var/lock/subsys/...datafile.../...datafile.../in.smbd.log' [ Not found ]
[20:12:35]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[20:12:35]   Checking for directory '/var/lock/subsys/...datafile.../...datafile...' [ Not found ]
[20:12:35]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../bin' [ Not found ]
[20:12:35]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/bin' [ Not found ]
[20:12:36]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/sbin' [ Not found ]
[20:12:36]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../lib/security' [ Not found ]
[20:12:36] Ohhara Rootkit                                    [ Not found ]
[20:12:36]
[20:12:36] Checking for Optic Kit (Tux) Worm...
[20:12:36]   Checking for directory '/dev/tux'               [ Not found ]
[20:12:36]   Checking for directory '/usr/bin/xchk'          [ Not found ]
[20:12:36]   Checking for directory '/usr/bin/xsf'           [ Not found ]
[20:12:36]   Checking for directory '/usr/bin/ssh2d'         [ Not found ]
[20:12:36] Optic Kit (Tux) Worm                              [ Not found ]
[20:12:36]
[20:12:36] Checking for Oz Rootkit...
[20:12:36]   Checking for file '/dev/.oz/.nap/rkit/terror'   [ Not found ]
[20:12:36]   Checking for directory '/dev/.oz'               [ Not found ]
[20:12:36] Oz Rootkit                                        [ Not found ]
[20:12:36]
[20:12:36] Checking for Phalanx Rootkit...
[20:12:36]   Checking for file '/usr/share/.home.ph1/cb'     [ Not found ]
[20:12:36]   Checking for file '/etc/host.ph1'               [ Not found ]
[20:12:36]   Checking for file '/bin/host.ph1'               [ Not found ]
[20:12:36]   Checking for file '/usr/share/.home.ph1/phalanx' [ Not found ]
[20:12:36]   Checking for directory '/usr/share/.home.ph1'   [ Not found ]
[20:12:36] Phalanx Rootkit                                   [ Not found ]
[20:12:36]
[20:12:36] Checking for Phalanx Rootkit (strings)...
[20:12:37]   Checking for string 'phalanx'                   [ Not found ]
[20:12:37] Phalanx Rootkit (strings)                         [ Not found ]
[20:12:37]
[20:12:37] Checking for Portacelo Rootkit...
[20:12:37]   Checking for file '/var/lib/.../.ak'            [ Not found ]
[20:12:37]   Checking for file '/var/lib/.../.hk'            [ Not found ]
[20:12:37]   Checking for file '/var/lib/.../.rs'            [ Not found ]
[20:12:37]   Checking for file '/var/lib/.../.p'             [ Not found ]
[20:12:37]   Checking for file '/var/lib/.../getty'          [ Not found ]
[20:12:37]   Checking for file '/var/lib/.../lkt.o'          [ Not found ]
[20:12:37]   Checking for file '/var/lib/.../show'           [ Not found ]
[20:12:37]   Checking for file '/var/lib/.../nlkt.o'         [ Not found ]
[20:12:37]   Checking for file '/var/lib/.../ssshrc'         [ Not found ]
[20:12:37]   Checking for file '/var/lib/.../sssh_equiv'     [ Not found ]
[20:12:37]   Checking for file '/var/lib/.../sssh_known_hosts' [ Not found ]
[20:12:37]   Checking for file '/var/lib/.../sssh_pid'       [ Not found ]
[20:12:37]   Checking for file '~/.sssh/known_hosts'         [ Not found ]
[20:12:37] Portacelo Rootkit                                 [ Not found ]
[20:12:37]
[20:12:37] Checking for R3dstorm Toolkit...
[20:12:37]   Checking for file '/var/log/tk02/see_all'       [ Not found ]
[20:12:37]   Checking for file '/bin/.../sshd/sbin/sshd1'    [ Not found ]
[20:12:37]   Checking for file '/bin/.../hate/sk'            [ Not found ]
[20:12:38]   Checking for file '/bin/.../see_all'            [ Not found ]
[20:12:38]   Checking for directory '/var/log/tk02'          [ Not found ]
[20:12:38]   Checking for directory '/var/log/tk02/old'      [ Not found ]
[20:12:38]   Checking for directory '/bin/...'               [ Not found ]
[20:12:38] R3dstorm Toolkit                                  [ Not found ]
[20:12:38]
[20:12:38] Checking for RH-Sharpe's Rootkit...
[20:12:38]   Checking for file '/bin/lps'                    [ Not found ]
[20:12:38]   Checking for file '/usr/bin/lpstree'            [ Not found ]
[20:12:38]   Checking for file '/usr/bin/ltop'               [ Not found ]
[20:12:38]   Checking for file '/usr/bin/lkillall'           [ Not found ]
[20:12:38]   Checking for file '/usr/bin/ldu'                [ Not found ]
[20:12:38]   Checking for file '/usr/bin/lnetstat'           [ Not found ]
[20:12:38]   Checking for file '/usr/bin/wp'                 [ Not found ]
[20:12:38]   Checking for file '/usr/bin/shad'               [ Not found ]
[20:12:38]   Checking for file '/usr/bin/vadim'              [ Not found ]
[20:12:38]   Checking for file '/usr/bin/slice'              [ Not found ]
[20:12:38]   Checking for file '/usr/bin/cleaner'            [ Not found ]
[20:12:38]   Checking for file '/usr/include/rpcsvc/du'      [ Not found ]
[20:12:38] RH-Sharpe's Rootkit                               [ Not found ]
[20:12:38]
[20:12:38] Checking for RSHA's Rootkit...
[20:12:38]   Checking for file '/bin/kr4p'                   [ Not found ]
[20:12:38]   Checking for file '/usr/bin/n3tstat'            [ Not found ]
[20:12:39]   Checking for file '/usr/bin/chsh2'              [ Not found ]
[20:12:39]   Checking for file '/usr/bin/slice2'             [ Not found ]
[20:12:39]   Checking for file '/usr/src/linux/arch/alpha/lib/.lib/.1proc' [ Not found ]
[20:12:39]   Checking for file '/etc/rc.d/arch/alpha/lib/.lib/.1addr' [ Not found ]
[20:12:39]   Checking for directory '/etc/rc.d/rsha'         [ Not found ]
[20:12:39]   Checking for directory '/etc/rc.d/arch/alpha/lib/.lib' [ Not found ]
[20:12:39] RSHA's Rootkit                                    [ Not found ]
[20:12:39]
[20:12:39] Checking for Scalper Worm...
[20:12:39]   Checking for file '/tmp/.a'                     [ Not found ]
[20:12:39]   Checking for file '/tmp/.uua'                   [ Not found ]
[20:12:39] Scalper Worm                                      [ Not found ]
[20:12:39]
[20:12:39] Checking for Sebek LKM...
[20:12:40]   Checking for kernel symbol 'adore or sebek'     [ Not found ]
[20:12:40] Sebek LKM                                         [ Not found ]
[20:12:40]
[20:12:40] Checking for Shutdown Rootkit...
[20:12:40]   Checking for file '/usr/man/man5/.. /.dir/scannah/asus' [ Not found ]
[20:12:40]   Checking for file '/usr/man/man5/.. /.dir/see'  [ Not found ]
[20:12:40]   Checking for file '/usr/man/man5/.. /.dir/nscd' [ Not found ]
[20:12:40]   Checking for file '/usr/man/man5/.. /.dir/alpd' [ Not found ]
[20:12:40]   Checking for file '/etc/rc.d/rc.local '         [ Not found ]
[20:12:40]   Checking for directory '/usr/man/man5/.. /.dir' [ Not found ]
[20:12:40]   Checking for directory '/usr/man/man5/.. /.dir/scannah' [ Not found ]
[20:12:40]   Checking for directory '/etc/rc.d/rc0.d/.. /.dir' [ Not found ]
[20:12:40] Shutdown Rootkit                                  [ Not found ]
[20:12:40]
[20:12:40] Checking for SHV4 Rootkit...
[20:12:40]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[20:12:40]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[20:12:40]   Checking for file '/lib/lidps1.so'              [ Not found ]
[20:12:40]   Checking for file '/usr/sbin/xntps'             [ Not found ]
[20:12:40]   Checking for directory '/lib/security/.config'  [ Not found ]
[20:12:40]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[20:12:40] SHV4 Rootkit                                      [ Not found ]
[20:12:40]
[20:12:40] Checking for SHV5 Rootkit...
[20:12:41]   Checking for file '/etc/sh.conf'                [ Not found ]
[20:12:41]   Checking for file '/dev/srd0'                   [ Not found ]
[20:12:41]   Checking for directory '/usr/lib/libsh'         [ Not found ]
[20:12:41] SHV5 Rootkit                                      [ Not found ]
[20:12:41]
[20:12:41] Checking for Sin Rootkit...
[20:12:41]   Checking for file '/dev/.haos/haos1/.f/Denyed'  [ Not found ]
[20:12:41]   Checking for file '/dev/ttyoa'                  [ Not found ]
[20:12:41]   Checking for file '/dev/ttyof'                  [ Not found ]
[20:12:41]   Checking for file '/dev/ttyop'                  [ Not found ]
[20:12:41]   Checking for file '/dev/ttyos'                  [ Not found ]
[20:12:41]   Checking for file '/usr/lib/.lib'               [ Not found ]
[20:12:41]   Checking for file '/usr/lib/sn/.X'              [ Not found ]
[20:12:41]   Checking for file '/usr/lib/sn/.sys'            [ Not found ]
[20:12:41]   Checking for file '/usr/lib/ld/.X'              [ Not found ]
[20:12:41]   Checking for file '/usr/man/man1/...'           [ Not found ]
[20:12:41]   Checking for file '/usr/man/man1/.../.m'        [ Not found ]
[20:12:41]   Checking for file '/usr/man/man1/.../.w'        [ Not found ]
[20:12:41]   Checking for directory '/usr/lib/sn'            [ Not found ]
[20:12:41]   Checking for directory '/usr/lib/man1/...'      [ Not found ]
[20:12:41]   Checking for directory '/dev/.haos'             [ Not found ]
[20:12:41] Sin Rootkit                                       [ Not found ]
[20:12:41]
[20:12:41] Checking for Slapper Worm...
[20:12:41]   Checking for file '/tmp/.bugtraq'               [ Not found ]
[20:12:42]   Checking for file '/tmp/.uubugtraq'             [ Not found ]
[20:12:42]   Checking for file '/tmp/.bugtraq.c'             [ Not found ]
[20:12:42]   Checking for file '/tmp/httpd'                  [ Not found ]
[20:12:42]   Checking for file '/tmp/.unlock'                [ Not found ]
[20:12:42]   Checking for file '/tmp/update'                 [ Not found ]
[20:12:42]   Checking for file '/tmp/.cinik'                 [ Not found ]
[20:12:42]   Checking for file '/tmp/.b'                     [ Not found ]
[20:12:42] Slapper Worm                                      [ Not found ]
[20:12:42]
[20:12:42] Checking for Sneakin Rootkit...
[20:12:42]   Checking for directory '/tmp/.X11-unix/.../rk'  [ Not found ]
[20:12:42] Sneakin Rootkit                                   [ Not found ]
[20:12:42]
[20:12:42] Checking for Suckit Rootkit...
[20:12:42]   Checking for file '/sbin/initsk12'              [ Not found ]
[20:12:42]   Checking for file '/sbin/initxrk'               [ Not found ]
[20:12:42]   Checking for file '/usr/bin/null'               [ Not found ]
[20:12:42]   Checking for file '/usr/share/locale/sk/.sk12/sk' [ Not found ]
[20:12:42]   Checking for file '/etc/rc.d/rc0.d/S23kmdac'    [ Not found ]
[20:12:42]   Checking for file '/etc/rc.d/rc1.d/S23kmdac'    [ Not found ]
[20:12:42]   Checking for file '/etc/rc.d/rc2.d/S23kmdac'    [ Not found ]
[20:12:42]   Checking for file '/etc/rc.d/rc3.d/S23kmdac'    [ Not found ]
[20:12:42]   Checking for file '/etc/rc.d/rc4.d/S23kmdac'    [ Not found ]
[20:12:43]   Checking for file '/etc/rc.d/rc5.d/S23kmdac'    [ Not found ]
[20:12:43]   Checking for file '/etc/rc.d/rc6.d/S23kmdac'    [ Not found ]
[20:12:43]   Checking for directory '/dev/sdhu0/tehdrakg'    [ Not found ]
[20:12:43]   Checking for directory '/etc/.MG'               [ Not found ]
[20:12:43]   Checking for directory '/usr/share/locale/sk/.sk12' [ Not found ]
[20:12:43]   Checking for directory '/usr/lib/perl5/site_perl/i386-linux/auto/TimeDate/.packlist' [ Not found ]
[20:12:43] Suckit Rootkit                                    [ Not found ]
[20:12:43]
[20:12:43] Checking for SunOS Rootkit...
[20:12:43]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[20:12:43]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[20:12:43]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[20:12:43]   Checking for file '/bin/xlogin'                 [ Not found ]
[20:12:43]   Checking for file '/usr/lib/crth.o'             [ Not found ]
[20:12:43]   Checking for file '/usr/lib/crtz.o'             [ Not found ]
[20:12:43]   Checking for file '/sbin/login'                 [ Not found ]
[20:12:43]   Checking for file '/lib/security/.config/sn'    [ Not found ]
[20:12:43]   Checking for file '/lib/security/.config/lpsched' [ Not found ]
[20:12:43]   Checking for file '/dev/kmod'                   [ Not found ]
[20:12:43]   Checking for file '/dev/dos'                    [ Not found ]
[20:12:43] SunOS Rootkit                                     [ Not found ]
[20:12:43]
[20:12:43] Checking for SunOS / NSDAP Rootkit...
[20:12:43]   Checking for file '/usr/lib/vold/nsdap/.kit'    [ Not found ]
[20:12:44]   Checking for file '/usr/lib/vold/nsdap/defines' [ Not found ]
[20:12:44]   Checking for file '/usr/lib/vold/nsdap/patcher' [ Not found ]
[20:12:44]   Checking for file '/usr/lib/vold/nsdap/pg'      [ Not found ]
[20:12:44]   Checking for file '/usr/lib/vold/nsdap/cleaner' [ Not found ]
[20:12:44]   Checking for file '/usr/lib/vold/nsdap/utime'   [ Not found ]
[20:12:44]   Checking for file '/usr/lib/vold/nsdap/crypt'   [ Not found ]
[20:12:44]   Checking for file '/usr/lib/vold/nsdap/findkit' [ Not found ]
[20:12:44]   Checking for file '/usr/lib/vold/nsdap/sn2'     [ Not found ]
[20:12:44]   Checking for file '/usr/lib/vold/nsdap/sniffload' [ Not found ]
[20:12:44]   Checking for file '/usr/lib/vold/nsdap/runsniff' [ Not found ]
[20:12:44]   Checking for file '/usr/lib/lpset'              [ Not found ]
[20:12:44]   Checking for directory '/usr/lib/vold/nsdap'    [ Not found ]
[20:12:44] SunOS / NSDAP Rootkit                             [ Not found ]
[20:12:44]
[20:12:44] Checking for Superkit Rootkit...
[20:12:44]   Checking for file '/usr/man/.sman/sk'           [ Not found ]
[20:12:44] Superkit Rootkit                                  [ Not found ]
[20:12:44]
[20:12:44] Checking for TBD (Telnet BackDoor)...
[20:12:44]   Checking for file '/usr/lib/.tbd'               [ Not found ]
[20:12:44] TBD (Telnet BackDoor)                             [ Not found ]
[20:12:44]
[20:12:44] Checking for TeLeKiT Rootkit...
[20:12:44]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/sniff' [ Not found ]
[20:12:45]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/telnetd' [ Not found ]
[20:12:45]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/teleulo' [ Not found ]
[20:12:45]   Checking for file '/usr/man/man3/.../cl'        [ Not found ]
[20:12:45]   Checking for file '/dev/ptyr'                   [ Not found ]
[20:12:45]   Checking for file '/dev/ptyp'                   [ Not found ]
[20:12:45]   Checking for file '/dev/ptyq'                   [ Not found ]
[20:12:45]   Checking for file '/dev/hda06'                  [ Not found ]
[20:12:45]   Checking for file '/usr/info/libc1.so'          [ Not found ]
[20:12:45]   Checking for directory '/usr/man/man3/...'      [ Not found ]
[20:12:45]   Checking for directory '/usr/man/man3/.../lsniff' [ Not found ]
[20:12:45]   Checking for directory '/usr/man/man3/.../TeLeKiT' [ Not found ]
[20:12:45] TeLeKiT Rootkit                                   [ Not found ]
[20:12:45]
[20:12:45] Checking for T0rn Rootkit...
[20:12:45]   Checking for file '/dev/.lib/lib/lib/t0rns'     [ Not found ]
[20:12:45]   Checking for file '/dev/.lib/lib/lib/du'        [ Not found ]
[20:12:45]   Checking for file '/dev/.lib/lib/lib/ls'        [ Not found ]
[20:12:45]   Checking for file '/dev/.lib/lib/lib/t0rnsb'    [ Not found ]
[20:12:45]   Checking for file '/dev/.lib/lib/lib/ps'        [ Not found ]
[20:12:45]   Checking for file '/dev/.lib/lib/lib/t0rnp'     [ Not found ]
[20:12:45]   Checking for file '/dev/.lib/lib/lib/find'      [ Not found ]
[20:12:45]   Checking for file '/dev/.lib/lib/lib/ifconfig'  [ Not found ]
[20:12:45]   Checking for file '/dev/.lib/lib/lib/pg'        [ Not found ]
[20:12:46]   Checking for file '/dev/.lib/lib/lib/ssh.tgz'   [ Not found ]
[20:12:46]   Checking for file '/dev/.lib/lib/lib/top'       [ Not found ]
[20:12:46]   Checking for file '/dev/.lib/lib/lib/sz'        [ Not found ]
[20:12:46]   Checking for file '/dev/.lib/lib/lib/login'     [ Not found ]
[20:12:46]   Checking for file '/dev/.lib/lib/lib/in.fingerd' [ Not found ]
[20:12:46]   Checking for file '/dev/.lib/lib/lib/1i0n.sh'   [ Not found ]
[20:12:46]   Checking for file '/dev/.lib/lib/lib/pstree'    [ Not found ]
[20:12:46]   Checking for file '/dev/.lib/lib/lib/in.telnetd' [ Not found ]
[20:12:46]   Checking for file '/dev/.lib/lib/lib/mjy'       [ Not found ]
[20:12:46]   Checking for file '/dev/.lib/lib/lib/sush'      [ Not found ]
[20:12:46]   Checking for file '/dev/.lib/lib/lib/tfn'       [ Not found ]
[20:12:46]   Checking for file '/dev/.lib/lib/lib/name'      [ Not found ]
[20:12:46]   Checking for file '/dev/.lib/lib/lib/getip.sh'  [ Not found ]
[20:12:46]   Checking for file '/usr/info/.torn/sh*'         [ Not found ]
[20:12:46]   Checking for file '/usr/src/.****/.1addr'       [ Not found ]
[20:12:46]   Checking for file '/usr/src/.****/.1file'       [ Not found ]
[20:12:46]   Checking for file '/usr/src/.****/.1proc'       [ Not found ]
[20:12:46]   Checking for file '/usr/src/.****/.1logz'       [ Not found ]
[20:12:46]   Checking for file '/usr/info/.t0rn'             [ Not found ]
[20:12:46]   Checking for directory '/dev/.lib'              [ Not found ]
[20:12:46]   Checking for directory '/dev/.lib/lib'          [ Not found ]
[20:12:47]   Checking for directory '/dev/.lib/lib/lib'      [ Not found ]
[20:12:47]   Checking for directory '/dev/.lib/lib/lib/dev'  [ Not found ]
[20:12:47]   Checking for directory '/dev/.lib/lib/scan'     [ Not found ]
[20:12:47]   Checking for directory '/usr/src/.****'         [ Not found ]
[20:12:47]   Checking for directory '/usr/man/man1/man1'     [ Not found ]
[20:12:47]   Checking for directory '/usr/man/man1/man1/lib' [ Not found ]
[20:12:47]   Checking for directory '/usr/man/man1/man1/lib/.lib' [ Not found ]
[20:12:47]   Checking for directory '/usr/man/man1/man1/lib/.lib/.backup' [ Not found ]
[20:12:47] T0rn Rootkit                                      [ Not found ]
[20:12:47]
[20:12:47] Checking for Trojanit Kit...
[20:12:47]   Checking for file '/bin/.ls'                    [ Not found ]
[20:12:47]   Checking for file '/bin/.ps'                    [ Not found ]
[20:12:47]   Checking for file '/bin/.netstat'               [ Not found ]
[20:12:47]   Checking for file '/usr/bin/.nop'               [ Not found ]
[20:12:47]   Checking for file '/usr/bin/.who'               [ Not found ]
[20:12:47] Trojanit Kit                                      [ Not found ]
[20:12:47]
[20:12:47] Checking for Tuxtendo Rootkit...
[20:12:47]   Checking for file '/dev/tux/.addr'              [ Not found ]
[20:12:47]   Checking for file '/dev/tux/.cron'              [ Not found ]
[20:12:47]   Checking for file '/dev/tux/.file'              [ Not found ]
[20:12:47]   Checking for file '/dev/tux/.log'               [ Not found ]
[20:12:48]   Checking for file '/dev/tux/.proc'              [ Not found ]
[20:12:48]   Checking for file '/dev/tux/backup/crontab'     [ Not found ]
[20:12:48]   Checking for file '/dev/tux/backup/df'          [ Not found ]
[20:12:48]   Checking for file '/dev/tux/backup/dir'         [ Not found ]
[20:12:48]   Checking for file '/dev/tux/backup/find'        [ Not found ]
[20:12:48]   Checking for file '/dev/tux/backup/ifconfig'    [ Not found ]
[20:12:48]   Checking for file '/dev/tux/backup/locate'      [ Not found ]
[20:12:48]   Checking for file '/dev/tux/backup/netstat'     [ Not found ]
[20:12:48]   Checking for file '/dev/tux/backup/ps'          [ Not found ]
[20:12:48]   Checking for file '/dev/tux/backup/pstree'      [ Not found ]
[20:12:48]   Checking for file '/dev/tux/backup/syslogd'     [ Not found ]
[20:12:48]   Checking for file '/dev/tux/backup/tcpd'        [ Not found ]
[20:12:48]   Checking for file '/dev/tux/backup/top'         [ Not found ]
[20:12:48]   Checking for file '/dev/tux/backup/updatedb'    [ Not found ]
[20:12:48]   Checking for file '/dev/tux/backup/vdir'        [ Not found ]
[20:12:48]   Checking for directory '/dev/tux'               [ Not found ]
[20:12:48]   Checking for directory '/dev/tux/ssh2'          [ Not found ]
[20:12:48]   Checking for directory '/dev/tux/backup'        [ Not found ]
[20:12:48] Tuxtendo Rootkit                                  [ Not found ]
[20:12:48]
[20:12:48] Checking for URK Rootkit...
[20:12:48]   Checking for file '/usr/man/man1/xxxxxxbin/find' [ Not found ]
[20:12:48]   Checking for file '/usr/man/man1/xxxxxxbin/du'  [ Not found ]
[20:12:49]   Checking for file '/usr/man/man1/xxxxxxbin/ps'  [ Not found ]
[20:12:49]   Checking for file '/tmp/conf.inf'               [ Not found ]
[20:12:49]   Checking for directory '/usr/man/man1/xxxxxxbin' [ Not found ]
[20:12:49] URK Rootkit                                       [ Not found ]
[20:12:49]
[20:12:49] Checking for VcKit Rootkit...
[20:12:49]   Checking for directory '/usr/include/linux/modules/lib.so' [ Not found ]
[20:12:49]   Checking for directory '/usr/include/linux/modules/lib.so/bin' [ Not found ]
[20:12:49] VcKit Rootkit                                     [ Not found ]
[20:12:49]
[20:12:49] Checking for Volc Rootkit...
[20:12:49]   Checking for directory '/var/spool/.recent'     [ Not found ]
[20:12:49]   Checking for directory '/var/spool/.recent/.files' [ Not found ]
[20:12:49]   Checking for directory '/usr/lib/volc'          [ Not found ]
[20:12:49]   Checking for directory '/usr/lib/volc/backup'   [ Not found ]
[20:12:49] Volc Rootkit                                      [ Not found ]
[20:12:49]
[20:12:49] Checking for X-Org SunOS Rootkit...
[20:12:49]   Checking for file '/usr/lib/libX.a/bin/tmpfl'   [ Not found ]
[20:12:49]   Checking for file '/usr/lib/libX.a/bin/rps'     [ Not found ]
[20:12:49]   Checking for file '/usr/bin/srload'             [ Not found ]
[20:12:49]   Checking for file '/usr/lib/libX.a/bin/sparcv7/rps' [ Not found ]
[20:12:49]   Checking for file '/usr/sbin/modcheck'          [ Not found ]
[20:12:49]   Checking for directory '/usr/lib/libX.a'        [ Not found ]
[20:12:50]   Checking for directory '/usr/lib/libX.a/bin'    [ Not found ]
[20:12:50]   Checking for directory '/usr/lib/libX.a/bin/sparcv7' [ Not found ]
[20:12:50]   Checking for directory '/usr/share/man...'      [ Not found ]
[20:12:50] X-Org SunOS Rootkit                               [ Not found ]
[20:12:50]
[20:12:50] Checking for zaRwT.KiT Rootkit...
[20:12:50]   Checking for file '/dev/rd/s/sendmeil'          [ Not found ]
[20:12:50]   Checking for file '/dev/ttyf'                   [ Not found ]
[20:12:50]   Checking for file '/dev/ttyp'                   [ Not found ]
[20:12:50]   Checking for file '/dev/ttyn'                   [ Not found ]
[20:12:50]   Checking for file '/rk/tulz'                    [ Not found ]
[20:12:50]   Checking for directory '/rk'                    [ Not found ]
[20:12:50]   Checking for directory '/dev/rd/s'              [ Not found ]
[20:12:50] zaRwT.KiT Rootkit                                 [ Not found ]
[20:12:50]
[20:12:50] Performing additional rootkit checks
[20:12:50] Info: Starting test name 'additional_rkts'
[20:12:50]
[20:12:50]   Performing Suckit Rookit additional checks
[20:12:50]     Checking /sbin/init link count                [ OK ]
[20:12:50]     Checking for hidden file extensions           [ None found ]
[20:12:50]     Running skdet command                         [ Skipped ]
[20:12:50] Info: Unable to find the 'skdet' command
[20:12:50]   Suckit Rookit additional checks                 [ OK ]
[20:12:51]
[20:12:51]   Performing check of possible rootkit files and directories
[20:12:51] Info: Starting test name 'possible_rkt_files'
[20:12:51]     Checking for file '/dev/sdr0'                 [ Not found ]
[20:12:51]     Checking for file '/tmp/.syshackfile'         [ Not found ]
[20:12:51]     Checking for file '/tmp/.bash_history'        [ Not found ]
[20:12:51]     Checking for file '/usr/info/.clib'           [ Not found ]
[20:12:51]     Checking for file '/usr/sbin/tcp.log'         [ Not found ]
[20:12:51]     Checking for file '/usr/bin/take/pid'         [ Not found ]
[20:12:51]     Checking for file '/sbin/create'              [ Not found ]
[20:12:51]     Checking for file '/dev/ttypz'                [ Not found ]
[20:12:51]     Checking for directory '/usr/bin/take'        [ Not found ]
[20:12:51]     Checking for directory '/usr/src/.lib'        [ Not found ]
[20:12:51]     Checking for directory '/usr/share/man/man1/.1c' [ Not found ]
[20:12:51]     Checking for directory '/lib/lblip.tk'        [ Not found ]
[20:12:51]     Checking for directory '/usr/sbin/...'        [ Not found ]
[20:12:51]     Checking for directory '/usr/share/.gun'      [ Not found ]
[20:12:52]   Checking for possible rootkit files and directories [ None found ]
[20:12:52]
[20:12:52]   Performing check for possible rootkit strings
[20:12:52] Info: Starting test name 'possible_rkt_strings'
[20:12:52] Info: Found local startup file: /etc/rc.local
[20:12:52]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[20:12:52]     Checking for string '****'                    [ Not found ]
[20:12:52]     Checking for string 'backdoor'                [ Not found ]
[20:12:52]     Checking for string 'vt200'                   [ Not found ]
[20:12:52]     Checking for string '/usr/bin/xstat'          [ Not found ]
[20:12:52]     Checking for string '/bin/envpc'              [ Not found ]
[20:12:52]     Checking for string 'L4m3r0x'                 [ Not found ]
[20:12:52]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[20:12:52]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[20:12:52]     Checking for string '/dev/sgk'                [ Not found ]
[20:12:52]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[20:12:52]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[20:12:53]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[20:12:53]     Checking for string '/lib/.sso'               [ Not found ]
[20:12:53]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[20:12:53]     Checking for string '/dev/caca'               [ Not found ]
[20:12:53]     Checking for string '/dev/ttyoa'              [ Not found ]
[20:12:53]     Checking for string 'syg'                     [ Not found ]
[20:12:53]     Checking for string '/dev/pts/01'             [ Not found ]
[20:12:53]     Checking for string 'tw33dl3'                 [ Not found ]
[20:12:53]     Checking for string 'psniff'                  [ Not found ]
[20:12:53]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[20:12:53]     Checking for string '/dev/ptyxx'              [ Not found ]
[20:12:53]     Checking for string 'promiscuous'             [ Not found ]
[20:12:53]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[20:12:54]     Checking for string '/dev/xdta'               [ Not found ]
[20:12:54]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[20:12:54]     Checking for string 'in.inetd'                [ Not found ]
[20:12:54]     Checking for string '#<HIDE_.*>'              [ Not found ]
[20:12:54]     Checking for string 'bin/xchk'                [ Not found ]
[20:12:54]     Checking for string 'bin/xsf'                 [ Not found ]
[20:12:54]   Checking for possible rootkit strings           [ None found ]
[20:12:54]
[20:12:54] Performing malware checks
[20:12:54] Info: Starting test name 'malware'
[20:12:54]
[20:12:54] Info: Test 'deleted_files' disabled at users request.
[20:12:54] Info: Starting test name 'running_procs'
[20:12:55]   Checking running processes for suspicious files [ None found ]
[20:12:55]
[20:12:55] Info: Test 'hidden_procs' disabled at users request.
[20:12:55]
[20:12:55] Info: Test 'suspscan' disabled at users request.
[20:12:55]
[20:12:55]   Performing check for login backdoors
[20:12:55] Info: Starting test name 'other_malware'
[20:12:55]     Checking for '/bin/.login'                    [ Not found ]
[20:12:55]     Checking for '/sbin/.login'                   [ Not found ]
[20:12:55]   Checking for login backdoors                    [ None found ]
[20:12:55]
[20:12:55]   Performing check for suspicious directories
[20:12:55]     Checking for directory '/usr/X11R6/bin/.,/copy' [ Not found ]
[20:12:55]     Checking for directory '/dev/rd/cdb'          [ Not found ]
[20:12:55]   Checking for suspicious directories             [ None found ]
[20:12:55]
[20:12:55]   Checking for software intrusions                [ Skipped ]
[20:12:55] Info: Check skipped - tripwire not installed
[20:12:55]
[20:12:55]   Performing check for sniffer log files
[20:12:55]     Checking for file '/usr/lib/libice.log'       [ Not found ]
[20:12:55]   Checking for sniffer log files                  [ None found ]
[20:12:55]
[20:12:55] Performing trojan specific checks
[20:12:55] Info: Starting test name 'trojans'
[20:12:55] Info: Using inetd configuration file '/etc/inetd.conf'
[20:12:55]   Checking for enabled inetd services             [ OK ]
[20:12:56]
[20:12:56]   Performing check for enabled xinetd services
[20:12:56]   Checking for enabled xinetd services            [ Skipped ]
[20:12:56] Info: Check skipped - file '/etc/xinetd.conf' does not exist.
[20:12:56]   Checking for Apache backdoor                    [ Not found ]
[20:12:56]
[20:12:56] Performing Linux specific checks
[20:12:56] Info: Starting test name 'os_specific'
[20:12:56]   Checking kernel module commands                 [ OK ]
[20:12:56] Info: Using modules pathname of '/lib/modules/2.6.24-19-generic'
[20:12:56]   Checking kernel module names                    [ OK ]
[20:13:07]
[20:13:07] Checking the network...
[20:13:07] Info: Starting test name 'network'
[20:13:07] Info: Starting test name 'ports'
[20:13:07]
[20:13:07] Performing check for backdoor ports
[20:13:07]   Checking for UDP port 2001                      [ Not found ]
[20:13:07]   Checking for TCP port 2006                      [ Not found ]
[20:13:07]   Checking for TCP port 2128                      [ Not found ]
[20:13:08]   Checking for TCP port 14856                     [ Not found ]
[20:13:08]   Checking for TCP port 47107                     [ Not found ]
[20:13:08]   Checking for TCP port 60922                     [ Not found ]
[20:13:08]
[20:13:08] Performing checks on the network interfaces
[20:13:08] Info: Starting test name 'promisc'
[20:13:08]   Checking for promiscuous interfaces             [ None found ]
[20:13:08]
[20:13:08] Info: Test 'packet_cap_apps' disabled at users request.
[20:13:14]
[20:13:14] Checking the local host...
[20:13:14] Info: Starting test name 'local_host'
[20:13:14]
[20:13:14] Performing system boot checks
[20:13:14] Info: Starting test name 'startup_files'
[20:13:14]   Checking for local host name                    [ Found ]
[20:13:14] Info: Starting test name 'startup_malware'
[20:13:14] Info: Found local startup file: /etc/rc.local
[20:13:14]   Checking for local startup files                [ Found ]
[20:13:14]   Checking local startup files for malware        [ None found ]
[20:13:14] Info: Found system startup directory: /etc/init.d
[20:13:16]   Checking system startup files for malware       [ None found ]
[20:13:16]
[20:13:16] Performing group and account checks
[20:13:16] Info: Starting test name 'group_accounts'
[20:13:16]   Checking for passwd file                        [ Found ]
[20:13:16] Info: Found password file: /etc/passwd
[20:13:16]   Checking for root equivalent (UID 0) accounts   [ None found ]
[20:13:16] Info: Found shadow file: /etc/shadow
[20:13:16]   Checking for passwordless accounts              [ None found ]
[20:13:16] Info: Starting test name 'passwd_changes'
[20:13:16]   Checking for passwd file changes                [ None found ]
[20:13:16] Info: Starting test name 'group_changes'
[20:13:16]   Checking for group file changes                 [ None found ]
[20:13:16]   Checking root account shell history files       [ None found ]
[20:13:16]
[20:13:16] Performing system configuration file checks
[20:13:16] Info: Starting test name 'system_configs'
[20:13:17]   Checking for SSH configuration file             [ Found ]
[20:13:17] Info: Found SSH configuration file: /etc/ssh/sshd_config
[20:13:17] Info: Rkhunter option ALLOW_SSH_ROOT_USER set to 'no'.
[20:13:17]   Checking if SSH root access is allowed          [ Warning ]
[20:13:17] Warning: The SSH and rkhunter configuration options should be the same:
[20:13:17]          SSH configuration option 'PermitRootLogin': yes
[20:13:17]          Rkhunter configuration option 'ALLOW_SSH_ROOT_USER': no
[20:13:17]   Checking if SSH protocol v1 is allowed          [ Not allowed ]
[20:13:17]   Checking for running syslog daemon              [ Found ]
[20:13:17]   Checking for syslog configuration file          [ Found ]
[20:13:17] Info: Found syslog configuration file: /etc/syslog.conf
[20:13:17]   Checking if syslog remote logging is allowed    [ Not allowed ]
[20:13:17]
[20:13:17] Performing filesystem checks
[20:13:17] Info: Starting test name 'filesystem'
[20:13:17] Info: SCAN_MODE_DEV set to 'THOROUGH'
[20:13:34]   Checking /dev for suspicious file types         [ Warning ]
[20:13:34] Warning: Suspicious file types found in /dev:
[20:13:34]          /dev/shm/pulse-shm-3310971082: data
[20:13:34]   Checking for hidden files and directories       [ Warning ]
[20:13:34] Warning: Hidden directory found: /etc/.java
[20:13:34] Warning: Hidden directory found: /dev/.static
[20:13:34] Warning: Hidden directory found: /dev/.udev
[20:13:34] Warning: Hidden directory found: /dev/.initramfs
[20:14:18]
[20:14:18] Checking application versions...
[20:14:18] Info: Starting test name 'apps'
[20:14:18]   Checking version of Exim MTA                    [ OK ]
[20:14:18] Info: Application 'exim' version '4.69' found.
[20:14:19]   Checking version of GnuPG                       [ OK ]
[20:14:19] Info: Application 'gpg' version '1.4.6' found.
[20:14:19] Info: Application 'httpd' not found.
[20:14:19] Info: Application 'named' not found.
[20:14:19]   Checking version of OpenSSL                     [ OK ]
[20:14:19] Info: Application 'openssl' version '0.9.8g' found.
[20:14:19]   Checking version of PHP                         [ OK ]
[20:14:19] Info: Application 'php' version '5.2.4' found.
[20:14:19] Info: Application 'procmail' not found.
[20:14:19] Info: Application 'proftpd' not found.
[20:14:19]   Checking version of OpenSSH                     [ OK ]
[20:14:19] Info: Application 'sshd' version '4.7p1' found.
[20:14:19] Info: Applications checked: 5 out of 9
[20:14:19]
[20:14:19] System checks summary
[20:14:19] =====================
[20:14:19]
[20:14:19] File properties checks...
[20:14:19] Files checked: 122
[20:14:19] Suspect files: 0
[20:14:19]
[20:14:19] Rootkit checks...
[20:14:19] Rootkits checked : 110
[20:14:19] Possible rootkits: 0
[20:14:19]
[20:14:19] Applications checks...
[20:14:20] Applications checked: 5
[20:14:20] Suspect applications: 0
[20:14:20]
[20:14:20] The system checks took: 2 minutes and 34 seconds
[20:14:20]
[20:14:20] Info: End date is Fri Sep 19 20:14:20 CEST 2008
```

---

