---
title: "rootkit found system compromised"
date: 2011-06-27
forum: Security
---

### Post by Unguidedone on 2011-06-27
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

the security log file is huge.... 400+ pages

seems i can only upload a file up to 150 kb so i mega uploaded it

_(megaupload link was removed due to system insecurity)_


**TIGER System Security Scanner**

 Tiger security scripts *** 3.2.2, 2007.08.28.00.00 ***
HTML Generator developed by the Advanced Research Corporation (R)
Sun Jun 26 21:49:48 MST 2011
21:49> Beginning security report for julio-ThinkCentre-M52 (i686 Linux 2.6.35-28-generic).

# Performing check of passwd files...
# Checking entries from /etc/passwd.
***WARN*** [pass014w]Login (backup) is disabled, but has a valid shell. 
***WARN*** [pass014w]Login (bin) is disabled, but has a valid shell. 
***WARN*** [pass014w]Login (couchdb) is disabled, but has a valid shell. 
***WARN*** [pass014w]Login (daemon) is disabled, but has a valid shell. 
***WARN*** [pass014w]Login (games) is disabled, but has a valid shell. 
***WARN*** [pass014w]Login (gnats) is disabled, but has a valid shell. 
***WARN*** [pass014w]Login (irc) is disabled, but has a valid shell. 
***WARN*** [pass014w]Login (julio) is disabled, but has a valid shell. 
***WARN*** [pass016w]User kernoops has / as home directory 
***WARN*** [pass014w]Login (libuuid) is disabled, but has a valid shell. 
***WARN*** [pass014w]Login (list) is disabled, but has a valid shell. 
***WARN*** [pass014w]Login (lp) is disabled, but has a valid shell. 
***WARN*** [pass014w]Login (mail) is disabled, but has a valid shell. 
***WARN*** [pass014w]Login (man) is disabled, but has a valid shell. 
***WARN*** [pass014w]Login (news) is disabled, but has a valid shell. 
***WARN*** [pass014w]Login (nobody) is disabled, but has a valid shell. 
***WARN*** [pass014w]Login (proxy) is disabled, but has a valid shell. 
***WARN*** [pass014w]Login (root) is disabled, but has a valid shell. 
***WARN*** [pass014w]Login (speech-dispatcher) is disabled, but has a valid           shell. 
***WARN*** [pass015w]Login ID sync does not have a valid shell (/bin/sync). 
***WARN*** [pass014w]Login (sys) is disabled, but has a valid shell. 
***WARN*** [pass014w]Login (uucp) is disabled, but has a valid shell. 
***WARN*** [pass014w]Login (www-data) is disabled, but has a valid shell. 
***WARN*** [pass006w]Integrity of password files questionable (/usr/sbin/pwck           -r). # Performing check of group files...  # Performing check of user accounts... # Checking accounts from /etc/passwd. 
***WARN*** [acc021w]Login ID avahi-autoipd appears to be a dormant account. 
***WARN*** [acc021w]Login ID libuuid appears to be a dormant account. 
***WARN*** [acc022w]Login ID nobody home directory (/nonexistent) is not           accessible. # Performing check of /etc/hosts.equiv and .rhosts files...  # Checking accounts from /etc/passwd...  # Performing check of .netrc files...  # Checking accounts from /etc/passwd...  # Performing common access checks for root (in /etc/default/login, /securetty, and /etc/ttytab... 
***WARN*** [root003w]Root user has message capability turned on. # Performing check of PATH components... 
***WARN*** [path009w]/etc/profile does not export an initial setting for PATH. # Only checking user 'root'  # Performing check of anonymous FTP...  # Performing checks of mail aliases... # Checking aliases from /etc/aliases.  # Performing check of `cron' entries... 
***WARN*** [cron004w]Root crontab does not exist 
***WARN*** [cron005w]Use of cron is not restricted # Performing check of 'services' ... # Checking services from /etc/services. 
***WARN*** [inet003w]The port for service sieve is also assigned to service           cisco-sccp. 
***WARN*** [inet003w]The port for service ndtp is also assigned to service           pipe_server. 
***WARN*** [inet003w]The port for service ndtp is also assigned to service           search. 
***WARN*** [inet003w]The port for service postgres is also assigned to service           postgresql. 
***WARN*** [inet003w]The port for service postgres is also assigned to service           postgresql. 
***WARN*** [inet003w]The port for service sane is also assigned to service           sane-port. 
***WARN*** [inet003w]The port for service webcache is also assigned to service           http-alt. 
***WARN*** [inet003w]The port for service webcache is also assigned to service           http-alt. # Performing NFS exports check...  # Performing check of system file permissions... 
***ALERT*** [perm023a]/bin/su is setuid to `root'. 
***ALERT*** [perm023a]/usr/bin/at is setuid to `daemon'. 
***ALERT*** [perm024a]/usr/bin/at is setgid to `daemon'. 
***WARN*** [perm001w]The owner of /usr/bin/at should be root (owned by daemon). 
***WARN*** [perm002w]The group owner of /usr/bin/at should be root. 
***ALERT*** [perm023a]/usr/bin/passwd is setuid to `root'. 
***ALERT*** [perm024a]/usr/bin/wall is setgid to `tty'. # Checking for known intrusion signs... # Testing for promiscuous interfaces with /bin/ip # Testing for backdoors in inetd.conf  # Performing check of files in system mail spool...  # Performing check for rookits... # Running chkrootkit (/usr/sbin/chkrootkit) to perform further checks... 
***ALERT*** [rootkit005a]Chkrootkit has found a file which seems to be infected            because of a rootkit 
***ALERT*** [rootkit009a]A rootkit seems to be installed in the system INFECTED (PORTS: 1524 6667 31337)  # Performing system specific checks... # Performing checks for Linux/2...  # Checking for single user-mode password...  # Checking boot loader file permissions... 
***WARN*** [boot03w]Could not access LILO's or Grub's configuration file # Checking for vulnerabilities in inittab configuration...  # Checking for correct umask settings for init scripts... 
***WARN*** [misc021w]There are no umask entries in /etc/init.d/rcS # Checking Logins not used on the system ...  # Checking network configuration 
***WARN*** [lin012w]The system accepts ICMP redirection messages 
***WARN*** [lin017w]The system is not configured to log suspicious (martian)           packets # Verifying system specific password checks...  # Checking OS release... 
***WARN*** [osv004w]Unreleased Debian GNU/Linux version `squeeze/sid' # Checking installed packages vs Debian Security Advisories...  # Checking md5sums of installed files  # Checking installed files against packages...

---

### Post by Dangertux on 2011-06-27
It would seem to appear you do actually have a root kit. My guess would be Ambient's Root Kit (ARK)

I can't give you any more information without seeing the logs. If you want me to read them post them in a plain text format ; not OpenOffice, sorry not opening that from a rooted box ;-) , in fact a mod may wish to remove that download link until it is reposted as plain text.

---

### Post by Unguidedone on 2011-06-27
ok this is kinda scary that even on linux i get a rootkit :(

here is the plaintext log :

[http://www.megaupload.com/?d=ENAFVCQR](http://www.megaupload.com/?d=ENAFVCQR)

i put it in gedit so its a plain text

---

### Post by wirelessmonkey on 2011-06-27
Wow! Wipe and Reinstall. Not gonna touch it.

---

### Post by Unguidedone on 2011-06-27
what do i do with the files and stuff i got on my system?

---

### Post by Karlchen on 2011-06-27
Hello, Unguidedone.
> **Unguidedone said:**
> ok this is kinda scary that even on linux i get a rootkit :(
here is the plaintext log : [http://www.megaupload.com/?d=ENAFVCQR](http://www.megaupload.com/?d=ENAFVCQR)Hm, I am not really sure that there is a rootkit on the machine.

Tiger System Security  Scanner only stated that chkrootkit had identified a rootkit, but it failed to give any name. This is a bit strange, because chkrootkit checks for a list of rootkits which it knows by name. So in case chkrootkit had really found a rootkit it should have been able to give it a name and Tiger System Security  Scanner should have passed it on. But no name is given.

Disregarding the fact that there are a ton of warnings which may or may not be pieces of evidence that there is a rootkit, at minimum the overall system configuration might need more than a little bit of fine-tuning.

The ton of "dangling" links might suggest that someone simply removed files and folders from the system instead of properly uninstalling packages, they might also mean that a thorough file system scan is badly needed.

Either way, the Tiger System Security  Scanner logfile seems to suggest that your system is suffering from several problems. A rootkit might be one of those problems. Hence the advice which has been given before, wipe and re-install, may be appropriate.

On the other hand, I am not too sure that personally I would put too much trust in what a 4 year old security scanner > **Unguidedone said:**
> Tiger security scripts *** 3.2.2, 2007.08.28.00.00 *** tells me. At least I would not depend on its verdict only.

How about running current versions of
+ chkrootkit
+ rkhunter
+ ClamAV
first, and checking the integrity of the installed software packages with the help of Synaptic or apt and running a thorough fsck on the filesystem, before wiping the system?

Karl

---

### Post by Dangertux on 2011-06-27
Yeah I looked at your other logfile in a VM ;-)

I would say a re-install is in order.  If you want to though you can post the output of sudo netstat -alnp 

The dangling sym links and all that is a result of how Ubuntu handles compatibility with certain other distros and many "root kit detection" programs will return false positives from them. The concern is the promiscuous ports listed , which is why the netstat command.

However it will probably confirm what Tiger has already told you. This is just to rule out that legitimate services aren't running on those ports and causing a false positive. The reason I said ARK is those are it's default listening ports, I find it odd that those 3 ports of all lined up coincidentally.

---

### Post by Unguidedone on 2011-06-27
ok here is the terminal output :
```
unix  3      [ ]         STREAM     CONNECTED     11996    2107/gvfsd-trash    @/dbus-vfs-daemon/socket-0Ngcgz9W
unix  3      [ ]         STREAM     CONNECTED     11995    2167/trashapplet    
unix  3      [ ]         STREAM     CONNECTED     11997    2167/trashapplet    /tmp/orbit-julio/linc-877-0-35c480a52b973
unix  3      [ ]         STREAM     CONNECTED     11993    1717/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     11994    2107/gvfsd-trash    @/dbus-vfs-daemon/socket-MGFXsLOY
unix  3      [ ]         STREAM     CONNECTED     11992    2167/trashapplet    
unix  3      [ ]         STREAM     CONNECTED     11989    2107/gvfsd-trash    @/dbus-vfs-daemon/socket-5567BZZU
unix  3      [ ]         STREAM     CONNECTED     11988    2167/trashapplet    
unix  3      [ ]         STREAM     CONNECTED     11987    2107/gvfsd-trash    @/dbus-vfs-daemon/socket-VeRpv27l
unix  3      [ ]         STREAM     CONNECTED     11986    2167/trashapplet    
unix  3      [ ]         STREAM     CONNECTED     11983    1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     11982    2167/trashapplet    
unix  3      [ ]         STREAM     CONNECTED     11981    1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     11980    2159/wnck-applet    
unix  3      [ ]         STREAM     CONNECTED     11973    1717/gnome-panel    /tmp/orbit-julio/linc-6b5-0-2561899550c1
unix  3      [ ]         STREAM     CONNECTED     11972    2159/wnck-applet    
unix  3      [ ]         STREAM     CONNECTED     11952    1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     11951    2167/trashapplet    
unix  3      [ ]         STREAM     CONNECTED     11950    2159/wnck-applet    /tmp/orbit-julio/linc-86f-0-548b15e19706
unix  3      [ ]         STREAM     CONNECTED     11949    1627/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     11947    2167/trashapplet    /tmp/orbit-julio/linc-877-0-35c480a52b973
unix  3      [ ]         STREAM     CONNECTED     11946    1627/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     11948    2159/wnck-applet    /tmp/orbit-julio/linc-86f-0-548b15e19706
unix  3      [ ]         STREAM     CONNECTED     11945    1717/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     11943    1627/gconfd-2       /tmp/orbit-julio/linc-65b-0-53269bb7b14a8
unix  3      [ ]         STREAM     CONNECTED     11942    2167/trashapplet    
unix  3      [ ]         STREAM     CONNECTED     11941    1627/gconfd-2       /tmp/orbit-julio/linc-65b-0-53269bb7b14a8
unix  3      [ ]         STREAM     CONNECTED     11940    2159/wnck-applet    
unix  3      [ ]         STREAM     CONNECTED     11937    1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     11936    1717/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     11927    2167/trashapplet    /tmp/orbit-julio/linc-877-0-35c480a52b973
unix  3      [ ]         STREAM     CONNECTED     11926    2098/bonobo-activat 
unix  3      [ ]         STREAM     CONNECTED     11923    2098/bonobo-activat /tmp/orbit-julio/linc-832-0-1316a93f77da8
unix  3      [ ]         STREAM     CONNECTED     11922    2167/trashapplet    
unix  3      [ ]         STREAM     CONNECTED     11918    1000/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11917    2167/trashapplet    
unix  3      [ ]         STREAM     CONNECTED     11909    768/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11908    1721/nautilus       
unix  3      [ ]         STREAM     CONNECTED     11905    1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     11904    2170/gvfs-gphoto2-v 
unix  3      [ ]         STREAM     CONNECTED     11893    2159/wnck-applet    /tmp/orbit-julio/linc-86f-0-548b15e19706
unix  3      [ ]         STREAM     CONNECTED     11892    2098/bonobo-activat 
unix  3      [ ]         STREAM     CONNECTED     11889    2098/bonobo-activat /tmp/orbit-julio/linc-832-0-1316a93f77da8
unix  3      [ ]         STREAM     CONNECTED     11888    2159/wnck-applet    
unix  3      [ ]         STREAM     CONNECTED     11881    1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     11880    2163/gvfs-afc-volum 
unix  3      [ ]         STREAM     CONNECTED     11840    1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     11839    2138/gdu-notificati 
unix  2      [ ]         DGRAM                    11833    2160/pickup         
unix  2      [ ]         DGRAM                    11825    2161/qmgr           
unix  3      [ ]         STREAM     CONNECTED     11823    1000/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11822    2159/wnck-applet    
unix  3      [ ]         STREAM     CONNECTED     11815    1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     11814    2144/gvfs-gdu-volum 
unix  3      [ ]         STREAM     CONNECTED     11810    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11809    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11806    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11805    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11802    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11801    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11798    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11797    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11794    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11793    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11790    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11789    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11786    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11785    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11782    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11781    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11778    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11777    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11774    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11773    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11770    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11769    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11766    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11765    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11762    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11761    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11758    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11757    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11754    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11753    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11750    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11749    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11746    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11745    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11742    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11741    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11738    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11737    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11734    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11733    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11730    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11729    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11726    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11725    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11722    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11721    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11718    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11717    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11714    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11713    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11710    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11709    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11706    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11705    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11703    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11702    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11699    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11698    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11696    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11695    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11652    1717/gnome-panel    /tmp/orbit-julio/linc-6b5-0-2561899550c1
unix  3      [ ]         STREAM     CONNECTED     11651    2098/bonobo-activat 
unix  3      [ ]         STREAM     CONNECTED     11646    1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     11645    2098/bonobo-activat 
unix  3      [ ]         STREAM     CONNECTED     11644    2098/bonobo-activat /tmp/orbit-julio/linc-832-0-1316a93f77da8
unix  3      [ ]         STREAM     CONNECTED     11643    1717/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     11641    1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     11640    1721/nautilus       
unix  2      [ ]         DGRAM                    11631    2150/master         
unix  3      [ ]         STREAM     CONNECTED     11625    768/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11624    2147/udisks-daemon  
unix  3      [ ]         STREAM     CONNECTED     11619    768/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11618    2147/udisks-daemon  
unix  3      [ ]         STREAM     CONNECTED     11615    768/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11614    2138/gdu-notificati 
unix  3      [ ]         STREAM     CONNECTED     11612    1000/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11611    2138/gdu-notificati 
unix  3      [ ]         STREAM     CONNECTED     11608    2142/e-addressbook- /tmp/orbit-julio/linc-85e-0-56fc54bb2da71
unix  3      [ ]         STREAM     CONNECTED     11607    1627/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     11604    1627/gconfd-2       /tmp/orbit-julio/linc-65b-0-53269bb7b14a8
unix  3      [ ]         STREAM     CONNECTED     11603    2142/e-addressbook- 
unix  3      [ ]         STREAM     CONNECTED     11582    768/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11581    2144/gvfs-gdu-volum 
unix  3      [ ]         STREAM     CONNECTED     11576    1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     11575    2144/gvfs-gdu-volum 
unix  3      [ ]         STREAM     CONNECTED     11571    1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     11570    2142/e-addressbook- 
unix  3      [ ]         STREAM     CONNECTED     11561    1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     11560    1635/gnome-settings 
unix  3      [ ]         STREAM     CONNECTED     11566    1488/gnome-session  @/tmp/.ICE-unix/1488
unix  3      [ ]         STREAM     CONNECTED     11555    1712/pulseaudio     
unix  3      [ ]         STREAM     CONNECTED     11490    1000/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11489    1712/pulseaudio     
unix  3      [ ]         STREAM     CONNECTED     11479    2107/gvfsd-trash    @/dbus-vfs-daemon/socket-SqycpTPp
unix  3      [ ]         STREAM     CONNECTED     11478    1721/nautilus       
unix  3      [ ]         STREAM     CONNECTED     11480    2107/gvfsd-trash    @/dbus-vfs-daemon/socket-AWfoqsuu
unix  3      [ ]         STREAM     CONNECTED     11477    1721/nautilus       
unix  3      [ ]         STREAM     CONNECTED     11469    1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     11468    2107/gvfsd-trash    
unix  3      [ ]         STREAM     CONNECTED     11463    1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     11462    2107/gvfsd-trash    
unix  3      [ ]         STREAM     CONNECTED     11433    1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     11432    2032/e-calendar-fac 
unix  3      [ ]         STREAM     CONNECTED     11431    2032/e-calendar-fac /tmp/orbit-julio/linc-7f0-0-1ba543d760f7
unix  3      [ ]         STREAM     CONNECTED     11430    1627/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     11427    1627/gconfd-2       /tmp/orbit-julio/linc-65b-0-53269bb7b14a8
unix  3      [ ]         STREAM     CONNECTED     11426    2032/e-calendar-fac 
unix  3      [ ]         STREAM     CONNECTED     11397    1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     11396    1721/nautilus       
unix  3      [ ]         STREAM     CONNECTED     11367    1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     11366    1723/nm-applet      
unix  3      [ ]         STREAM     CONNECTED     11329    1488/gnome-session  @/tmp/.ICE-unix/1488
unix  3      [ ]         STREAM     CONNECTED     11326    1717/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     11271    1719/compiz         /tmp/orbit-julio/linc-6b7-0-2fdfa25d5e7ab
unix  3      [ ]         STREAM     CONNECTED     11270    1627/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     11252    1712/pulseaudio     /home/julio/.pulse/5f49f694146ee148291814dd00000006-runtime/native
unix  3      [ ]         STREAM     CONNECTED     11251    1635/gnome-settings 
unix  3      [ ]         STREAM     CONNECTED     11267    1627/gconfd-2       /tmp/orbit-julio/linc-65b-0-53269bb7b14a8
unix  3      [ ]         STREAM     CONNECTED     11248    1719/compiz         
unix  3      [ ]         STREAM     CONNECTED     11231    768/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11230    1712/pulseaudio     
unix  3      [ ]         STREAM     CONNECTED     11202    768/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11201    2093/gnome-screensa 
unix  3      [ ]         STREAM     CONNECTED     11200    1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     11199    2093/gnome-screensa 
unix  3      [ ]         STREAM     CONNECTED     11184    768/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11183    1712/pulseaudio     
unix  2      [ ]         DGRAM                    11162    2033/pads           
unix  3      [ ]         STREAM     CONNECTED     11153    1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     11152    1721/nautilus       
unix  3      [ ]         STREAM     CONNECTED     11126    1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     11125    2032/e-calendar-fac 
unix  3      [ ]         STREAM     CONNECTED     11119    1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     11118    1721/nautilus       
unix  3      [ ]         STREAM     CONNECTED     11117    2093/gnome-screensa /tmp/orbit-julio/linc-7cb-0-16cff71770abe
unix  3      [ ]         STREAM     CONNECTED     11116    1627/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     11106    1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     11105    1717/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     11104    1000/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11103    1719/compiz         
unix  3      [ ]         STREAM     CONNECTED     11102    1488/gnome-session  @/tmp/.ICE-unix/1488
unix  3      [ ]         STREAM     CONNECTED     11101    1719/compiz         
unix  3      [ ]         STREAM     CONNECTED     11097    1627/gconfd-2       /tmp/orbit-julio/linc-65b-0-53269bb7b14a8
unix  3      [ ]         STREAM     CONNECTED     11096    2093/gnome-screensa 
unix  3      [ ]         STREAM     CONNECTED     11053    1000/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11052    2093/gnome-screensa 
unix  3      [ ]         STREAM     CONNECTED     11045    1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     11044    1723/nm-applet      
unix  3      [ ]         STREAM     CONNECTED     11001    1960/gconf-helper   /tmp/orbit-julio/linc-7a8-0-25b1bbae86997
unix  3      [ ]         STREAM     CONNECTED     11000    1627/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     10981    1722/evolution-alar /tmp/orbit-julio/linc-6ba-0-2a35b2987947a
unix  3      [ ]         STREAM     CONNECTED     10980    1627/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     10978    768/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10977    1723/nm-applet      
unix  3      [ ]         STREAM     CONNECTED     10976    1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     10975    1723/nm-applet      
unix  3      [ ]         STREAM     CONNECTED     10982    1627/gconfd-2       /tmp/orbit-julio/linc-65b-0-53269bb7b14a8
unix  3      [ ]         STREAM     CONNECTED     10974    1960/gconf-helper   
unix  3      [ ]         STREAM     CONNECTED     10959    1627/gconfd-2       /tmp/orbit-julio/linc-65b-0-53269bb7b14a8
unix  3      [ ]         STREAM     CONNECTED     10958    1722/evolution-alar 
unix  3      [ ]         STREAM     CONNECTED     10946    1723/nm-applet      /tmp/orbit-julio/linc-6bb-0-4b01f2953331e
unix  3      [ ]         STREAM     CONNECTED     10923    1627/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     10915    1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     10914    1722/evolution-alar 
unix  3      [ ]         STREAM     CONNECTED     10912    1000/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10911    1722/evolution-alar 
unix  3      [ ]         STREAM     CONNECTED     10867    1627/gconfd-2       /tmp/orbit-julio/linc-65b-0-53269bb7b14a8
unix  3      [ ]         STREAM     CONNECTED     10865    1723/nm-applet      
unix  3      [ ]         STREAM     CONNECTED     10856    768/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10855    1712/pulseaudio     
unix  3      [ ]         STREAM     CONNECTED     10646    1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     10643    1718/bluetooth-appl 
unix  3      [ ]         STREAM     CONNECTED     10503    1000/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10502    1723/nm-applet      
unix  3      [ ]         STREAM     CONNECTED     10499    1721/nautilus       /tmp/orbit-julio/linc-6b9-0-96c9c0a9d395
unix  3      [ ]         STREAM     CONNECTED     10497    1627/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     10491    1627/gconfd-2       /tmp/orbit-julio/linc-65b-0-53269bb7b14a8
unix  3      [ ]         STREAM     CONNECTED     10489    1721/nautilus       
unix  3      [ ]         STREAM     CONNECTED     10490    1717/gnome-panel    /tmp/orbit-julio/linc-6b5-0-2561899550c1
unix  3      [ ]         STREAM     CONNECTED     10488    1627/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     10400    1488/gnome-session  @/tmp/.ICE-unix/1488
unix  3      [ ]         STREAM     CONNECTED     10399    1721/nautilus       
unix  3      [ ]         STREAM     CONNECTED     10397    1000/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10396    1721/nautilus       
unix  3      [ ]         STREAM     CONNECTED     10391    1627/gconfd-2       /tmp/orbit-julio/linc-65b-0-53269bb7b14a8
unix  3      [ ]         STREAM     CONNECTED     10390    1717/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     10380    1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     10379    1717/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     10324    768/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10323    1718/bluetooth-appl 
unix  3      [ ]         STREAM     CONNECTED     10291    1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     10290    1718/bluetooth-appl 
unix  3      [ ]         STREAM     CONNECTED     10288    1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     10287    1706/polkit-gnome-a 
unix  3      [ ]         STREAM     CONNECTED     10286    1000/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10285    1717/gnome-panel    
unix  2      [ ]         DGRAM                    10284    1668/polkitd        
unix  3      [ ]         STREAM     CONNECTED     10279    1000/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10278    1718/bluetooth-appl 
unix  3      [ ]         STREAM     CONNECTED     10218    1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     10217    1712/pulseaudio     
unix  3      [ ]         STREAM     CONNECTED     10183    768/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10182    1706/polkit-gnome-a 
unix  3      [ ]         STREAM     CONNECTED     10150    1000/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10149    1706/polkit-gnome-a 
unix  3      [ ]         STREAM     CONNECTED     10131    768/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10130    1714/rtkit-daemon   
unix  2      [ ]         DGRAM                    10129    1714/rtkit-daemon   
unix  3      [ ]         STREAM     CONNECTED     10118    768/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10117    1712/pulseaudio     
unix  3      [ ]         STREAM     CONNECTED     9933     1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     9932     1696/gvfs-fuse-daem 
unix  3      [ ]         STREAM     CONNECTED     9928     1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     9927     1696/gvfs-fuse-daem 
unix  3      [ ]         STREAM     CONNECTED     9880     1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     9879     1677/gvfsd          
unix  3      [ ]         STREAM     CONNECTED     9874     768/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9873     1668/polkitd        
unix  3      [ ]         STREAM     CONNECTED     9869     1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     9868     1635/gnome-settings 
unix  3      [ ]         STREAM     CONNECTED     9781     768/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9780     1642/upowerd        
unix  3      [ ]         STREAM     CONNECTED     9776     768/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9775     1642/upowerd        
unix  3      [ ]         STREAM     CONNECTED     9766     1630/gnome-power-ma /tmp/orbit-julio/linc-65e-0-5467ad1975b2
unix  3      [ ]         STREAM     CONNECTED     9765     1627/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     9762     1627/gconfd-2       /tmp/orbit-julio/linc-65b-0-53269bb7b14a8
unix  3      [ ]         STREAM     CONNECTED     9761     1630/gnome-power-ma 
unix  3      [ ]         STREAM     CONNECTED     9748     1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     9747     1630/gnome-power-ma 
unix  3      [ ]         STREAM     CONNECTED     9737     768/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9736     1630/gnome-power-ma 
unix  3      [ ]         STREAM     CONNECTED     9734     1000/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9733     1630/gnome-power-ma 
unix  3      [ ]         STREAM     CONNECTED     9730     1635/gnome-settings /tmp/orbit-julio/linc-663-0-52141d44e23d9
unix  3      [ ]         STREAM     CONNECTED     9729     1627/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     9726     1627/gconfd-2       /tmp/orbit-julio/linc-65b-0-53269bb7b14a8
unix  3      [ ]         STREAM     CONNECTED     9725     1635/gnome-settings 
unix  3      [ ]         STREAM     CONNECTED     9711     1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     9710     1635/gnome-settings 
unix  3      [ ]         STREAM     CONNECTED     9693     1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     9692     1636/gnome-keyring- 
unix  3      [ ]         STREAM     CONNECTED     9691     1000/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9690     1635/gnome-settings 
unix  3      [ ]         STREAM     CONNECTED     9515     768/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9514     1488/gnome-session  
unix  3      [ ]         STREAM     CONNECTED     9507     1488/gnome-session  /tmp/orbit-julio/linc-5d0-0-3783898ec1729
unix  3      [ ]         STREAM     CONNECTED     9506     1627/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     9503     1627/gconfd-2       /tmp/orbit-julio/linc-65b-0-53269bb7b14a8
unix  3      [ ]         STREAM     CONNECTED     9502     1488/gnome-session  
unix  3      [ ]         STREAM     CONNECTED     9498     768/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9497     1627/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     9377     1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     9376     1627/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     9314     1601/dbus-daemon    @/tmp/dbus-8Uj2FMQxaf
unix  3      [ ]         STREAM     CONNECTED     9313     1488/gnome-session  
unix  3      [ ]         STREAM     CONNECTED     9309     1000/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9308     1488/gnome-session  
unix  2      [ ]         DGRAM                    9297     1620/(squid)        
unix  2      [ ]         DGRAM                    9292     1618/squid          
unix  3      [ ]         STREAM     CONNECTED     9279     1000/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9278     1585/dbus-launch    
unix  3      [ ]         STREAM     CONNECTED     9261     1601/dbus-daemon    
unix  3      [ ]         STREAM     CONNECTED     9260     1601/dbus-daemon    
unix  3      [ ]         STREAM     CONNECTED     9226     1000/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9225     1585/dbus-launch    
unix  3      [ ]         STREAM     CONNECTED     8977     768/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8976     1388/gdm-session-wo 
unix  2      [ ]         DGRAM                    8933     1388/gdm-session-wo 
unix  3      [ ]         STREAM     CONNECTED     8928     1000/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     8927     974/gdm-simple-slav 
unix  3      [ ]         STREAM     CONNECTED     8926     974/gdm-simple-slav @/tmp/gdm-session-xCaPiTFe
unix  3      [ ]         STREAM     CONNECTED     8925     1388/gdm-session-wo 
unix  3      [ ]         STREAM     CONNECTED     8922     768/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8921     1388/gdm-session-wo 
unix  3      [ ]         STREAM     CONNECTED     8756     1000/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     8755     974/gdm-simple-slav 
unix  3      [ ]         STREAM     CONNECTED     8131     1066/acpid          /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     8050     1000/X              
unix  2      [ ]         DGRAM                    8032     1/init              
unix  2      [ ]         DGRAM                    8028     1066/acpid          
unix  3      [ ]         STREAM     CONNECTED     7862     768/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7861     974/gdm-simple-slav 
unix  3      [ ]         STREAM     CONNECTED     7832     768/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7831     970/wpa_supplicant  
unix  2      [ ]         DGRAM                    7830     970/wpa_supplicant  
unix  2      [ ]         DGRAM                    7827     827/gdm-binary      
unix  2      [ ]         DGRAM                    7826     971/dhclient        
unix  3      [ ]         STREAM     CONNECTED     7792     768/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7791     882/console-kit-dae 
unix  3      [ ]         STREAM     CONNECTED     7673     768/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7672     895/modem-manager   
unix  2      [ ]         DGRAM                    7671     895/modem-manager   
unix  3      [ ]         STREAM     CONNECTED     7665     768/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7664     882/console-kit-dae 
unix  3      [ ]         STREAM     CONNECTED     7636     768/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7635     893/NetworkManager  
unix  3      [ ]         STREAM     CONNECTED     7629     768/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7628     893/NetworkManager  
unix  2      [ ]         DGRAM                    7624     893/NetworkManager  
unix  3      [ ]         STREAM     CONNECTED     7557     768/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7556     827/gdm-binary      
unix  3      [ ]         STREAM     CONNECTED     7548     768/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7547     847/avahi-daemon: r 
unix  3      [ ]         STREAM     CONNECTED     7541     848/avahi-daemon: c 
unix  3      [ ]         STREAM     CONNECTED     7540     847/avahi-daemon: r 
unix  2      [ ]         DGRAM                    7537     847/avahi-daemon: r 
unix  3      [ ]         STREAM     CONNECTED     7433     768/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7432     1/init              
unix  3      [ ]         STREAM     CONNECTED     7410     768/dbus-daemon     
unix  3      [ ]         STREAM     CONNECTED     7409     768/dbus-daemon     
unix  3      [ ]         DGRAM                    6009     299/udevd           
unix  3      [ ]         DGRAM                    6008     299/udevd           
unix  3      [ ]         STREAM     CONNECTED     5972     1/init              @/com/ubuntu/upstart
unix  3      [ ]         STREAM     CONNECTED     5971     279/upstart-udev-br 
julio@julio-ThinkCentre-M52:~$
```

---

### Post by Unguidedone on 2011-06-27
a bit odd i tryed installing clamav

julio@julio-ThinkCentre-M52:~$ sudo apt-get install clamav
[sudo] password for julio: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
clamav is already the newest version.
clamav set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up prelude-lml (1.0.0-1) ...
Starting Prelude LML: prelude-lmlinvoke-rc.d: initscript prelude-lml, action "start" failed.
dpkg: error processing prelude-lml (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 prelude-lml
E: Sub-process /usr/bin/dpkg returned an error code (1)
julio@julio-ThinkCentre-M52:~$


i got it to work and now im scanning the entire system thank you for all the help with this matter.

---

### Post by Unguidedone on 2011-06-27
ok i scanned my system:


Known viruses: 976043
Engine version: 0.96.5
Scanned directories: 35136
Scanned files: 177345
Infected files: 46
Total errors: 524
Data scanned: 6520.91 MB
Data read: 25444.41 MB (ratio 0.26:1)
Time: 1891.886 sec (31 m 31 s)
julio@julio-ThinkCentre-M52:~$

---

### Post by doas777 on 2011-06-27
attempting to clean a rootkit is a futile activity. 

op, back up your user files, and doublecheck any scripts/executables you have installed.
when you rebuild, do a quick audit of your configuration as you are setting everything back up. some vulnerability in your configuration let someone in. check VNC (remote desktop) and SSH.

---

### Post by Unguidedone on 2011-06-27
everyone thank you for your help

i will reinstall the os :(

thanks again

---

### Post by Dangertux on 2011-06-27
> **doas777 said:**
> attempting to clean a rootkit is a futile activity. 

op, back up your user files, and doublecheck any scripts/executables you have installed.
when you rebuild, do a quick audit of your configuration as you are setting everything back up. some vulnerability in your configuration let someone in. check VNC (remote desktop) and SSH.

Pretty much this. 

You didn't paste the whole output of the netstat probably because your terminal window only scrolls back 512 lines by default (this can be changed). However ; after seeing the clamav output, I am fairly certain it is wise to go ahead and wipe the system. 

Few tips for when you reinstall 

+ Don't use your root account or sudo to poke around , use it only when needed. Only for procedures that you understand. 

+ Don't run shell scripts you don't understand, don't install from untrusted repos unless you know what you're installing (IE: you can audit the source code yourself and know exactly what it does)

+ When running SSH , FTP , VNC or any other type of server ; make sure you configure it before just putting it out there. There are many good hardening guides for just about any server you can think of. 

+ Don't punch holes with iptables unless it's necessary 

+ Do use ufw/iptables/netfilter

+ Do scan for malware (you did this obviously) 

+ Use common sense, I think this should be a lesson to everyone. Ubuntu IS more secure than Windows or even Mac OSX at this stage of the game. However, nothing is perfect. Don't hide behind the false assumption that you are safe solely because you run Ubuntu/Linux.

Good luck, and sucks that this happened :-/

---

### Post by Unguidedone on 2011-06-27
ok new probelms :

----------- SCAN SUMMARY -----------
Known viruses: 976049
Engine version: 0.96.5
Scanned directories: 24175
Scanned files: 107342
Infected files: 0
Total errors: 521  <-----what is this?
Data scanned: 3694.85 MB
Data read: 3709.90 MB (ratio 1.00:1)
Time: 1041.755 sec (17 m 21 s)
julio@julio-ThinkCentre-M52:~$ 

i cant access security report :

Will try to check using config for 'i686' running Linux 2.6.35-30-generic...
--CONFIG-- [con005c] Using configuration files for Linux 2.6.35-30-generic. Using
           configuration files for generic Linux 2.
Tiger security scripts *** 3.2.2, 2007.08.28.00.00 ***
Output Mode is HTML
20:16> Beginning security report for julio-ThinkCentre-M52.
20:16> Starting file systems scans in background...
20:16> Checking password files...
20:16> Checking group files...
20:16> Checking user accounts...
20:16> Checking .rhosts files...
20:16> Checking .netrc files...
20:16> Checking ttytab, securetty, and login configuration files...
20:16> Checking PATH settings...
20:16> Checking anonymous ftp setup...
20:16> Checking mail aliases...
20:16> Checking cron entries...
20:16> Checking 'services' configuration...
20:16> Checking NFS export entries...
20:16> Checking permissions and ownership of system files...
--CONFIG-- [con010c] Filesystem 'devtmpfs' used by 'none' is not recognised as a valid filesystem
20:16> Checking for indications of break-in...
--CONFIG-- [con010c] Filesystem 'devtmpfs' used by 'none' is not recognised as a valid filesystem
20:16> Performing rootkit checks...
20:17> Performing system specific checks...
/bin/grep: /etc/inittab: No such file or directory
20:27> Performing root directory checks...
20:27> Checking for secure backup devices...
20:27> Checking for the presence of log files...
20:27> Checking for the setting of user's umask...
20:27> Checking for listening processes...
20:27> Checking SSHD's configuration...
20:27> Checking the printers control file...
20:27> Checking ftpusers configuration...
20:27> Checking NTP configuration...
20:27> Waiting for filesystems scans to complete...
20:27> Filesystems scans completed...
20:27> Performing check of embedded pathnames...
20:29> Security report completed for julio-ThinkCentre-M52.
Security report is in `/var/log/tiger/security.report.julio-ThinkCentre-M52.110627-20:16.html'.
julio@julio-ThinkCentre-M52:~$ sudo bash -c "cp /var/log/tiger/security.report.* /home/bodhi
> sudo chown bodhi.bodhi /home/bodhi/security.report.*
> 
> sudo bash -c "cp /var/log/tiger/security.report.* /home/bodhi
[sudo] password for julio: 
chown: invalid user: `bodhi.bodhi'
cp: missing file operand
Try `cp --help' for more information.
julio@julio-ThinkCentre-M52:~$ gksudo firefox /var/log/tiger/security.report.julio-ThinkCentre-M52.110626-21:49.html
julio@julio-ThinkCentre-M52:~$ gksudo firefox /var/log/tiger/security.report.julio-ThinkCentre-M52.1106
julio@julio-ThinkCentre-M52:~$

---

### Post by Dangertux on 2011-06-28
> **Unguidedone said:**
> ok new probelms :

----------- SCAN SUMMARY -----------
Known viruses: 976049
Engine version: 0.96.5
Scanned directories: 24175
Scanned files: 107342
Infected files: 0
Total errors: 521  <-----what is this?
Data scanned: 3694.85 MB
Data read: 3709.90 MB (ratio 1.00:1)
Time: 1041.755 sec (17 m 21 s)
julio@julio-ThinkCentre-M52:~$ 

i cant access security report :

Will try to check using config for 'i686' running Linux 2.6.35-30-generic...
--CONFIG-- [con005c] Using configuration files for Linux 2.6.35-30-generic. Using
           configuration files for generic Linux 2.
Tiger security scripts *** 3.2.2, 2007.08.28.00.00 ***
Output Mode is HTML
20:16> Beginning security report for julio-ThinkCentre-M52.
20:16> Starting file systems scans in background...
20:16> Checking password files...
20:16> Checking group files...
20:16> Checking user accounts...
20:16> Checking .rhosts files...
20:16> Checking .netrc files...
20:16> Checking ttytab, securetty, and login configuration files...
20:16> Checking PATH settings...
20:16> Checking anonymous ftp setup...
20:16> Checking mail aliases...
20:16> Checking cron entries...
20:16> Checking 'services' configuration...
20:16> Checking NFS export entries...
20:16> Checking permissions and ownership of system files...
--CONFIG-- [con010c] Filesystem 'devtmpfs' used by 'none' is not recognised as a valid filesystem
20:16> Checking for indications of break-in...
--CONFIG-- [con010c] Filesystem 'devtmpfs' used by 'none' is not recognised as a valid filesystem
20:16> Performing rootkit checks...
20:17> Performing system specific checks...
/bin/grep: /etc/inittab: No such file or directory
20:27> Performing root directory checks...
20:27> Checking for secure backup devices...
20:27> Checking for the presence of log files...
20:27> Checking for the setting of user's umask...
20:27> Checking for listening processes...
20:27> Checking SSHD's configuration...
20:27> Checking the printers control file...
20:27> Checking ftpusers configuration...
20:27> Checking NTP configuration...
20:27> Waiting for filesystems scans to complete...
20:27> Filesystems scans completed...
20:27> Performing check of embedded pathnames...
20:29> Security report completed for julio-ThinkCentre-M52.
Security report is in `/var/log/tiger/security.report.julio-ThinkCentre-M52.110627-20:16.html'.
julio@julio-ThinkCentre-M52:~$ sudo bash -c "cp /var/log/tiger/security.report.* /home/bodhi
> sudo chown bodhi.bodhi /home/bodhi/security.report.*
> 
> sudo bash -c "cp /var/log/tiger/security.report.* /home/bodhi
[sudo] password for julio: 
chown: invalid user: `bodhi.bodhi'
cp: missing file operand
Try `cp --help' for more information.
julio@julio-ThinkCentre-M52:~$ gksudo firefox /var/log/tiger/security.report.julio-ThinkCentre-M52.110626-21:49.html
julio@julio-ThinkCentre-M52:~$ gksudo firefox /var/log/tiger/security.report.julio-ThinkCentre-M52.1106
julio@julio-ThinkCentre-M52:~$

Re-read the file name vs the file name you are trying to open.

Try this file
/var/log/tiger/security.report.julio-ThinkCentre-M52.110627-20:16.html

Errors are issues with ClamAV being able to scan a file. Likely due to permissions or apparmor messing with it , I wouldn't worry. I am assuming this is immediately after a fresh install.

Don't get too paranoid, the root kit didn't just magically come back after a brand new install ;-)

---

### Post by Unguidedone on 2011-06-28
this is odd when i restored my user files and im trying to add my sudo password its like blocked in terminal
sudo clamscan -r /

---

### Post by Dangertux on 2011-06-28
What do you mean it's blocked?

Did you set the same password at install time?

---

### Post by Unguidedone on 2011-06-28
when the prompt for the sudo password comes up no keystokes head to window ya ill have to reinstall again because i used the same password :( got to think of a new one


/var/spool/openoffice/uno_packages/cache/uno_packages.db: OK
/var/spool/mqueue: Can't open directory.
/var/spool/mqueue-client: Can't open directory.
/var/spool/cron/atspool: Can't open directory.
/var/spool/cron/atjobs: Can't open directory.
/var/spool/cron/crontabs: Can't open directory.
/var/spool/anacron/cron.monthly: Access denied
/var/spool/anacron/cron.daily: Access denied
/var/spool/anacron/cron.weekly: Access denied
/var/spool/cups: Can't open directory.
/var/backups/passwd.bak: Access denied
/var/backups/apt.extended_states.0: OK
/var/backups/group.bak: Access denied
/var/backups/dpkg.status.0: OK
/var/backups/shadow.bak: Access denied
/var/backups/gshadow.bak: Access denied

----------- SCAN SUMMARY -----------
Known viruses: 976049
Engine version: 0.96.5
Scanned directories: 25613
Scanned files: 141367
Infected files: 0
Total errors: 1237
Data scanned: 6912.50 MB
Data read: 17973.99 MB (ratio 0.38:1)
Time: 1696.557 sec (28 m 16 s)
julio@julio-ThinkCentre-M52:~$ sudo clamscan -r /
[sudo] password for julio:

---

### Post by Dangertux on 2011-06-28
> **Unguidedone said:**
> when the prompt for the sudo password comes up no keystokes head to window ya ill have to reinstall again because i used the same password :( got to think of a new one


/var/spool/openoffice/uno_packages/cache/uno_packages.db: OK
/var/spool/mqueue: Can't open directory.
/var/spool/mqueue-client: Can't open directory.
/var/spool/cron/atspool: Can't open directory.
/var/spool/cron/atjobs: Can't open directory.
/var/spool/cron/crontabs: Can't open directory.
/var/spool/anacron/cron.monthly: Access denied
/var/spool/anacron/cron.daily: Access denied
/var/spool/anacron/cron.weekly: Access denied
/var/spool/cups: Can't open directory.
/var/backups/passwd.bak: Access denied
/var/backups/apt.extended_states.0: OK
/var/backups/group.bak: Access denied
/var/backups/dpkg.status.0: OK
/var/backups/shadow.bak: Access denied
/var/backups/gshadow.bak: Access denied

----------- SCAN SUMMARY -----------
Known viruses: 976049
Engine version: 0.96.5
Scanned directories: 25613
Scanned files: 141367
Infected files: 0
Total errors: 1237
Data scanned: 6912.50 MB
Data read: 17973.99 MB (ratio 0.38:1)
Time: 1696.557 sec (28 m 16 s)
julio@julio-ThinkCentre-M52:~$ sudo clamscan -r /
[sudo] password for julio:

When you type your password in a terminal window it doesn't display the characters for security purposes. This is normal.

You also don't have to reinstall again just to change your password. You can use the passwd command to change your password or you can do it through the gui.

System > Administration > Users and Groups

Personally I think you should take a break and calm down, I understand that this type of security violation can be unnerving , but the constant re-scanning is fueling your paranoia I think. Please don't take offense at that. Sometimes it's just wise to relax a little bit turn off the computer and take a break, you've been at this for hours now.

---

### Post by Ezlivin on 2011-06-28
> **Dangertux said:**
> Personally I think you should take a break and calm down, I understand that this type of security violation can be unnerving , but the constant re-scanning is fueling your paranoia I think. Please don't take offense at that. Sometimes it's just wise to relax a little bit turn off the computer and take a break, you've been at this for hours now.

This sounds like good advice. I read what happened and it must suck but at least you'll be better prepared to make sure it doesn't happen again.

UFW firewall is really easy to enable and it's installed by default. That should keep your new install safe so you can get back to enjoying Ubuntu. There's loads of info on the forums and wiki if you search UFW but it's this easy to enable in a terminal

```
sudo ufw enable
```

All the best with it anyway.

---

### Post by Unguidedone on 2011-06-28
my system was hardened :(    (not saying it was perfect but it was reasonably safe)

i installed apparmor,selinux, harded the kernel, encrypted huge partions of my hardrive with truecrypt, used a password safe, only used aes encryption, setup firewalls (software firewall and physical firewall), used strong passwords, installed snort, installed 2 anti virus programs, checked all ports (all were steathed none were open) ~ updated my system often, i only downloaded programs from the ubuntu software center.


i found out before my system was scanned that something was wrong, i was using nmap and was seeing odd packet traffic activity yes from 3 ports (failed to write it down) and had higher then normal cpu usage

the only thing i would change is connect to the internet with a secure encrypted vpn. ya ill power down now...

---

### Post by crispy_420 on 2011-06-28
Maybe look into [bastille]("http://bastille-linux.sourceforge.net/") to further lock down the system. Its in the repos.

---

### Post by Unguidedone on 2011-06-29
the rootkit is back....

the only thing i did not install was bastille (because it failed to run in terminal)

3 ports are infected and there is +1 users on the system.....  (same ports to)
i am running port senetry so it could be a false positive.

ill have to reinstall (5th time in total)


the system is locked down pertty well and remote access is disabled i dont know if they are using ssh.  There is a security hole somewhere in here that i have yet to find. ill keep working....

---

### Post by linuxpenguin on 2011-06-29
I'm no security pro... but...

What non-default programs are you installing?
Do you have a backup that you're restoring from?
Is the drive/partition you're installing to the only one in the system? (And if not, have you tried scanning the other partitions or reinstalling without all the other drives hooked up?)

Are you installing from a burned ISO, or are you installing from an external drive (and if you are installing from an external drive, has that drive been scanned)?

The fact that it comes back (and comes back so quick) says to me that either someone is really dedicated and you're being targeted, or there's something snuck into something you're installing, or there's something that found its way onto a backup. If you're using backups, or have stuff outside the repos that you install, try holding off on all that for a while and see if it comes back.

---

### Post by Unguidedone on 2011-06-29
i have the following on my system:

last fm squabbler
skype
diablo 2 lod (tested and its safe)
codelite
truecrypt
wine
apparmor
selinux
codexs to run dvds/mp3's 

i only install stuff from the repository but i was thinking what ever it is that is installed to the boot sector because thats the only area that does not get wiped with i wipe the drives and reinstall.

but heres something really odd:

[http://ubuntuforums.org/showthread.php?t=1362074](http://ubuntuforums.org/showthread.php?t=1362074)

same problem what i have 100%

heres the terminal readout :

julio@julio-ThinkCentre-M52:~$ sudo chkrootkit
ROOTDIR is `/'
Checking `amd'...                                           not found
Checking `basename'...                                      not infected
Checking `biff'...                                          not found
Checking `chfn'...                                          not infected
Checking `chsh'...                                          not infected
Checking `cron'...                                          not infected
Checking `crontab'...                                       not infected
Checking `date'...                                          not infected
Checking `du'...                                            not infected
Checking `dirname'...                                       not infected
Checking `echo'...                                          not infected
Checking `egrep'...                                         not infected
Checking `env'...                                           not infected
Checking `find'...                                          not infected
Checking `fingerd'...                                       not found
Checking `gpm'...                                           not found
Checking `grep'...                                          not infected
Checking `hdparm'...                                        not infected
Checking `su'...                                            not infected
Checking `ifconfig'...                                      not infected
Checking `inetd'...                                         not infected
Checking `inetdconf'...                                     not found
Checking `identd'...                                        not found
Checking `init'...                                          not infected
Checking `killall'...                                       not infected
Checking `ldsopreload'...                                   not infected
Checking `login'...                                         not infected
Checking `ls'...                                            not infected
Checking `lsof'...                                          not infected
Checking `mail'...                                          not found
Checking `mingetty'...                                      not found
Checking `netstat'...                                       not infected
Checking `named'...                                         not found
Checking `passwd'...                                        not infected
Checking `pidof'...                                         not infected
Checking `pop2'...                                          not found
Checking `pop3'...                                          not found
Checking `ps'...                                            not infected
Checking `pstree'...                                        not infected
Checking `rpcinfo'...                                       not infected
Checking `rlogind'...                                       not found
Checking `rshd'...                                          not found
Checking `slogin'...                                        not infected
Checking `sendmail'...                                      not infected
Checking `sshd'...                                          not found
Checking `syslogd'...                                       not tested
Checking `tar'...                                           not infected
Checking `tcpd'...                                          not infected
Checking `tcpdump'...                                       not infected
Checking `top'...                                           not infected
Checking `telnetd'...                                       not found
Checking `timed'...                                         not found
Checking `traceroute'...                                    not found
Checking `vdir'...                                          not infected
Checking `w'...                                             not infected
Checking `write'...                                         not infected
Checking `aliens'...                                        no suspect files
Searching for sniffer's logs, it may take a while...        nothing found
Searching for rootkit HiDrootkit's default files...         nothing found
Searching for rootkit t0rn's default files...               nothing found
Searching for t0rn's v8 defaults...                         nothing found
Searching for rootkit Lion's default files...               nothing found
Searching for rootkit RSHA's default files...               nothing found
Searching for rootkit RH-Sharpe's default files...          nothing found
Searching for Ambient's rootkit (ark) default files and dirs... nothing found
Searching for suspicious files and dirs, it may take a while... The following suspicious files and directories were found:  
/usr/lib/pymodules/python2.6/.path /usr/lib/firefox-3.6.18/.autoreg /usr/lib/xulrunner-1.9.2.18/.autoreg

Searching for LPD Worm files and dirs...                    nothing found
Searching for Ramen Worm files and dirs...                  nothing found
Searching for Maniac files and dirs...                      nothing found
Searching for RK17 files and dirs...                        nothing found
Searching for Ducoci rootkit...                             nothing found
Searching for Adore Worm...                                 nothing found
Searching for ShitC Worm...                                 nothing found
Searching for Omega Worm...                                 nothing found
Searching for Sadmind/IIS Worm...                           nothing found
Searching for MonKit...                                     nothing found
Searching for Showtee...                                    nothing found
Searching for OpticKit...                                   nothing found
Searching for T.R.K...                                      nothing found
Searching for Mithra...                                     nothing found
Searching for LOC rootkit...                                nothing found
Searching for Romanian rootkit...                           nothing found
Searching for Suckit rootkit...                             Warning: /sbin/init INFECTED
Searching for Volc rootkit...                               nothing found
Searching for Gold2 rootkit...                              nothing found
Searching for TC2 Worm default files and dirs...            nothing found
Searching for Anonoying rootkit default files and dirs...   nothing found
Searching for ZK rootkit default files and dirs...          nothing found
Searching for ShKit rootkit default files and dirs...       nothing found
Searching for AjaKit rootkit default files and dirs...      nothing found
Searching for zaRwT rootkit default files and dirs...       nothing found
Searching for Madalin rootkit default files...              nothing found
Searching for Fu rootkit default files...                   nothing found
Searching for ESRK rootkit default files...                 nothing found
Searching for rootedoor...                                  nothing found
Searching for ENYELKM rootkit default files...              nothing found
Searching for common ssh-scanners default files...          nothing found
Searching for suspect PHP files...                          nothing found
Searching for anomalies in shell history files...           nothing found
Checking `asp'...                                           not infected
Checking `bindshell'...                                     not infected
Checking `lkm'...                                           chkproc: nothing detected
chkdirs: nothing detected
Checking `rexedcs'...                                       not found
Checking `sniffer'...                                       lo: not promisc and no packet sniffer sockets
eth0: PACKET SNIFFER(/sbin/dhclient3[7853])
Checking `w55808'...                                        not infected
Checking `wted'...                                          chkwtmp: nothing deleted
Checking `scalper'...                                       not infected
Checking `slapper'...                                       not infected
Checking `z2'...                                            user julio deleted or never logged from lastlog!
Checking `chkutmp'...                                       chkutmp: nothing deleted
Checking `OSX_RSPLUG'...                                    not infected
julio@julio-ThinkCentre-M52:~$ sudo rkhunter --check
[ Rootkit Hunter version 1.3.6 ]

Checking system commands...

  Performing 'strings' command checks
    Checking 'strings' command                               [ OK ]

  Performing 'shared libraries' checks
    Checking for preloading variables                        [ None found ]
    Checking for preloaded libraries                         [ None found ]
    Checking LD_LIBRARY_PATH variable                        [ Not found ]

  Performing file properties checks
    Checking for prerequisites                               [ OK ]
    /bin/bash                                                [ OK ]
    /bin/cat                                                 [ OK ]
    /bin/chmod                                               [ OK ]
    /bin/chown                                               [ OK ]
    /bin/cp                                                  [ OK ]
    /bin/date                                                [ OK ]
    /bin/df                                                  [ OK ]
    /bin/dmesg                                               [ OK ]
    /bin/echo                                                [ OK ]
    /bin/ed                                                  [ OK ]
    /bin/egrep                                               [ OK ]
    /bin/fgrep                                               [ OK ]
    /bin/fuser                                               [ OK ]
    /bin/grep                                                [ OK ]
    /bin/ip                                                  [ OK ]
    /bin/kill                                                [ OK ]
    /bin/less                                                [ OK ]
    /bin/login                                               [ OK ]
    /bin/ls                                                  [ OK ]
    /bin/lsmod                                               [ OK ]
    /bin/mktemp                                              [ OK ]
    /bin/more                                                [ OK ]
    /bin/mount                                               [ OK ]
    /bin/mv                                                  [ OK ]
    /bin/netstat                                             [ OK ]
    /bin/ps                                                  [ OK ]
    /bin/pwd                                                 [ OK ]
    /bin/readlink                                            [ OK ]
    /bin/sed                                                 [ OK ]
    /bin/sh                                                  [ OK ]
    /bin/su                                                  [ OK ]
    /bin/touch                                               [ OK ]
    /bin/uname                                               [ OK ]
    /bin/which                                               [ OK ]
    /bin/dash                                                [ OK ]
    /usr/bin/awk                                             [ OK ]
    /usr/bin/basename                                        [ OK ]
    /usr/bin/chattr                                          [ OK ]
    /usr/bin/cut                                             [ OK ]
    /usr/bin/diff                                            [ OK ]
    /usr/bin/dirname                                         [ OK ]
    /usr/bin/dpkg                                            [ OK ]
    /usr/bin/dpkg-query                                      [ OK ]
    /usr/bin/du                                              [ OK ]
    /usr/bin/env                                             [ OK ]
    /usr/bin/file                                            [ OK ]
    /usr/bin/find                                            [ OK ]
    /usr/bin/GET                                             [ OK ]
    /usr/bin/groups                                          [ OK ]
    /usr/bin/head                                            [ OK ]
    /usr/bin/id                                              [ OK ]
    /usr/bin/killall                                         [ OK ]
    /usr/bin/last                                            [ OK ]
    /usr/bin/lastlog                                         [ OK ]
    /usr/bin/ldd                                             [ OK ]
    /usr/bin/less                                            [ OK ]
    /usr/bin/locate                                          [ OK ]
    /usr/bin/logger                                          [ OK ]
    /usr/bin/lsattr                                          [ OK ]
    /usr/bin/lsof                                            [ OK ]
    /usr/bin/md5sum                                          [ OK ]
    /usr/bin/mlocate                                         [ OK ]
    /usr/bin/newgrp                                          [ OK ]
    /usr/bin/passwd                                          [ OK ]
    /usr/bin/perl                                            [ OK ]
    /usr/bin/pgrep                                           [ OK ]
    /usr/bin/pstree                                          [ OK ]
    /usr/bin/rkhunter                                        [ OK ]
    /usr/bin/runcon                                          [ OK ]
    /usr/bin/sha1sum                                         [ OK ]
    /usr/bin/sha224sum                                       [ OK ]
    /usr/bin/sha256sum                                       [ OK ]
    /usr/bin/sha384sum                                       [ OK ]
    /usr/bin/sha512sum                                       [ OK ]
    /usr/bin/size                                            [ OK ]
    /usr/bin/sort                                            [ OK ]
    /usr/bin/stat                                            [ OK ]
    /usr/bin/strace                                          [ OK ]
    /usr/bin/strings                                         [ OK ]
    /usr/bin/sudo                                            [ OK ]
    /usr/bin/tail                                            [ OK ]
    /usr/bin/test                                            [ OK ]
    /usr/bin/top                                             [ OK ]
    /usr/bin/touch                                           [ OK ]
    /usr/bin/tr                                              [ OK ]
    /usr/bin/uniq                                            [ OK ]
    /usr/bin/users                                           [ OK ]
    /usr/bin/vmstat                                          [ OK ]
    /usr/bin/w                                               [ OK ]
    /usr/bin/watch                                           [ OK ]
    /usr/bin/wc                                              [ OK ]
    /usr/bin/wget                                            [ OK ]
    /usr/bin/whatis                                          [ OK ]
    /usr/bin/whereis                                         [ OK ]
    /usr/bin/which                                           [ OK ]
    /usr/bin/who                                             [ OK ]
    /usr/bin/whoami                                          [ OK ]
    /usr/bin/mawk                                            [ OK ]
    /usr/bin/lwp-request                                     [ OK ]
    /usr/bin/w.procps                                        [ OK ]
    /sbin/depmod                                             [ OK ]
    /sbin/ifconfig                                           [ OK ]
    /sbin/ifdown                                             [ OK ]
    /sbin/ifup                                               [ OK ]
    /sbin/init                                               [ OK ]
    /sbin/insmod                                             [ OK ]
    /sbin/ip                                                 [ OK ]
    /sbin/lsmod                                              [ OK ]
    /sbin/modinfo                                            [ OK ]
    /sbin/modprobe                                           [ OK ]
    /sbin/rmmod                                              [ OK ]
    /sbin/runlevel                                           [ OK ]
    /sbin/sulogin                                            [ OK ]
    /sbin/sysctl                                             [ OK ]
    /usr/sbin/adduser                                        [ OK ]
    /usr/sbin/chroot                                         [ OK ]
    /usr/sbin/cron                                           [ OK ]
    /usr/sbin/groupadd                                       [ OK ]
    /usr/sbin/groupdel                                       [ OK ]
    /usr/sbin/groupmod                                       [ OK ]
    /usr/sbin/grpck                                          [ OK ]
    /usr/sbin/nologin                                        [ OK ]
    /usr/sbin/pwck                                           [ OK ]
    /usr/sbin/rsyslogd                                       [ OK ]
    /usr/sbin/tcpd                                           [ OK ]
    /usr/sbin/useradd                                        [ OK ]
    /usr/sbin/userdel                                        [ OK ]
    /usr/sbin/usermod                                        [ OK ]
    /usr/sbin/vipw                                           [ OK ]
    /usr/sbin/unhide-linux26                                 [ OK ]

[Press <ENTER> to continue]


Checking for rootkits...

  Performing check of known rootkit files and directories
    55808 Trojan - Variant A                                 [ Not found ]
    ADM Worm                                                 [ Not found ]
    AjaKit Rootkit                                           [ Not found ]
    Adore Rootkit                                            [ Not found ]
    aPa Kit                                                  [ Not found ]
    Apache Worm                                              [ Not found ]
    Ambient (ark) Rootkit                                    [ Not found ]
    Balaur Rootkit                                           [ Not found ]
    BeastKit Rootkit                                         [ Not found ]
    beX2 Rootkit                                             [ Not found ]
    BOBKit Rootkit                                           [ Not found ]
    cb Rootkit                                               [ Not found ]
    CiNIK Worm (Slapper.B variant)                           [ Not found ]
    Danny-Boy's Abuse Kit                                    [ Not found ]
    Devil RootKit                                            [ Not found ]
    Dica-Kit Rootkit                                         [ Not found ]
    Dreams Rootkit                                           [ Not found ]
    Duarawkz Rootkit                                         [ Not found ]
    Enye LKM                                                 [ Not found ]
    Flea Linux Rootkit                                       [ Not found ]
    FreeBSD Rootkit                                          [ Not found ]
    Fu Rootkit                                               [ Not found ]
    ****`it Rootkit                                          [ Not found ]
    GasKit Rootkit                                           [ Not found ]
    Heroin LKM                                               [ Not found ]
    HjC Kit                                                  [ Not found ]
    ignoKit Rootkit                                          [ Not found ]
    iLLogiC Rootkit                                          [ Not found ]
    IntoXonia-NG Rootkit                                     [ Not found ]
    Irix Rootkit                                             [ Not found ]
    Kitko Rootkit                                            [ Not found ]
    Knark Rootkit                                            [ Not found ]
    ld-linuxv.so Rootkit                                     [ Not found ]
    Li0n Worm                                                [ Not found ]
    Lockit / LJK2 Rootkit                                    [ Not found ]
    Mood-NT Rootkit                                          [ Not found ]
    MRK Rootkit                                              [ Not found ]
    Ni0 Rootkit                                              [ Not found ]
    Ohhara Rootkit                                           [ Not found ]
    Optic Kit (Tux) Worm                                     [ Not found ]
    Oz Rootkit                                               [ Not found ]
    Phalanx Rootkit                                          [ Not found ]
    Phalanx2 Rootkit                                         [ Not found ]
    Phalanx2 Rootkit (extended tests)                        [ Not found ]
    Portacelo Rootkit                                        [ Not found ]
    R3dstorm Toolkit                                         [ Not found ]
    RH-Sharpe's Rootkit                                      [ Not found ]
    RSHA's Rootkit                                           [ Not found ]
    Scalper Worm                                             [ Not found ]
    Sebek LKM                                                [ Not found ]
    Shutdown Rootkit                                         [ Not found ]
    SHV4 Rootkit                                             [ Not found ]
    SHV5 Rootkit                                             [ Not found ]
    Sin Rootkit                                              [ Not found ]
    Slapper Worm                                             [ Not found ]
    Sneakin Rootkit                                          [ Not found ]
    'Spanish' Rootkit                                        [ Not found ]
    Suckit Rootkit                                           [ Not found ]
    SunOS Rootkit                                            [ Not found ]
    SunOS / NSDAP Rootkit                                    [ Not found ]
    Superkit Rootkit                                         [ Not found ]
    TBD (Telnet BackDoor)                                    [ Not found ]
    TeLeKiT Rootkit                                          [ Not found ]
    T0rn Rootkit                                             [ Not found ]
    trNkit Rootkit                                           [ Not found ]
    Trojanit Kit                                             [ Not found ]
    Tuxtendo Rootkit                                         [ Not found ]
    URK Rootkit                                              [ Not found ]
    Vampire Rootkit                                          [ Not found ]
    VcKit Rootkit                                            [ Not found ]
    Volc Rootkit                                             [ Not found ]
    Xzibit Rootkit                                           [ Not found ]
    X-Org SunOS Rootkit                                      [ Not found ]
    zaRwT.KiT Rootkit                                        [ Not found ]
    ZK Rootkit                                               [ Not found ]

  Performing additional rootkit checks
    Suckit Rookit additional checks                          [ OK ]
    Checking for possible rootkit files and directories      [ None found ]
    Checking for possible rootkit strings                    [ None found ]

  Performing malware checks
    Checking running processes for suspicious files          [ None found ]
    Checking for login backdoors                             [ None found ]
    Checking for suspicious directories                      [ None found ]
    Checking for sniffer log files                           [ None found ]

  Performing Linux specific checks
    Checking loaded kernel modules                           [ OK ]
    Checking kernel module names                             [ OK ]

[Press <ENTER> to continue]


Checking the network...

  Performing check for backdoor ports
    Checking for TCP port 1524                               [ Not found ]
    Checking for TCP port 1984                               [ Not found ]
    Checking for UDP port 2001                               [ Not found ]
    Checking for TCP port 2006                               [ Not found ]
    Checking for TCP port 2128                               [ Not found ]
    Checking for TCP port 6666                               [ Not found ]
    Checking for TCP port 6667                               [ Not found ]
    Checking for TCP port 6668                               [ Not found ]
    Checking for TCP port 6669                               [ Not found ]
    Checking for TCP port 7000                               [ Not found ]
    Checking for TCP port 13000                              [ Not found ]
    Checking for TCP port 14856                              [ Not found ]
    Checking for TCP port 25000                              [ Not found ]
    Checking for TCP port 29812                              [ Not found ]
    Checking for TCP port 31337                              [ Not found ]
    Checking for TCP port 32982                              [ Not found ]
    Checking for TCP port 33369                              [ Not found ]
    Checking for TCP port 47107                              [ Not found ]
    Checking for TCP port 47018                              [ Not found ]
    Checking for TCP port 60922                              [ Not found ]
    Checking for TCP port 62883                              [ Not found ]
    Checking for TCP port 65535                              [ Not found ]

  Performing checks on the network interfaces
    Checking for promiscuous interfaces                      [ None found ]

[Press <ENTER> to continue]


Checking the local host...

  Performing system boot checks
    Checking for local host name                             [ Found ]
    Checking for system startup files                        [ Found ]
    Checking system startup files for malware                [ None found ]

  Performing group and account checks
    Checking for passwd file                                 [ Found ]
    Checking for root equivalent (UID 0) accounts            [ None found ]
    Checking for passwordless accounts                       [ None found ]
    Checking for passwd file changes                         [ None found ]
    Checking for group file changes                          [ None found ]
    Checking root account shell history files                [ None found ]

  Performing system configuration file checks
    Checking for SSH configuration file                      [ Not found ]
    Checking for running syslog daemon                       [ Found ]
    Checking for syslog configuration file                   [ Found ]
    Checking if syslog remote logging is allowed             [ Not allowed ]

  Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]

[Press <ENTER> to continue]



System checks summary
=====================

File properties checks...
    Files checked: 130
    Suspect files: 0

Rootkit checks...
    Rootkits checked : 242
    Possible rootkits: 0

Applications checks...
    All checks skipped

The system checks took: 1 minute and 24 seconds

All results have been written to the log file (/var/log/rkhunter.log)

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)

julio@julio-ThinkCentre-M52:~$ 


strange huh?


from rkunter.log

[18:22:38]   Checking for running syslog daemon              [ Found ]
[18:22:38]   Checking for syslog configuration file          [ Found ]
[18:22:38] Info: Found syslog configuration file: /etc/rsyslog.conf
[18:22:38]   Checking if syslog remote logging is allowed    [ Not allowed ]
[18:22:38]
[18:22:38] Performing filesystem checks
[18:22:38] Info: Starting test name 'filesystem'
[18:22:38] Info: SCAN_MODE_DEV set to 'THOROUGH'
[18:22:39]   Checking /dev for suspicious file types         [ Warning ]
[18:22:39] Warning: Suspicious file types found in /dev:
[18:22:39]          /dev/shm/pulse-shm-2435996179: data
[18:22:39]          /dev/shm/pulse-shm-112226101: data
[18:22:39]          /dev/shm/pulse-shm-3764120937: data
[18:22:39]          /dev/shm/pulse-shm-3230137181: data
[18:22:39]          /dev/shm/pulse-shm-2994921804: data
[18:22:39]          /dev/shm/ecryptfs-julio-Private: ASCII text
[18:22:39]   Checking for hidden files and directories       [ Warning ]
[18:22:39] Warning: Hidden directory found: /dev/.udev
[18:22:39] Warning: Hidden directory found: /dev/.initramfs
[18:22:39] Warning: Hidden file found: /dev/.blkid.tab: ASCII text
[18:22:39] Warning: Hidden file found: /dev/.blkid.tab.old: ASCII text
[18:22:43]
[18:22:43] Info: Test 'apps' disabled at users request.
[18:22:43]
[18:22:43] System checks summary
[18:22:43] =====================
[18:22:43]
[18:22:43] File properties checks...
[18:22:43] Files checked: 130
[18:22:43] Suspect files: 0
[18:22:43]
[18:22:43] Rootkit checks...
[18:22:43] Rootkits checked : 242
[18:22:43] Possible rootkits: 0
[18:22:43]
[18:22:43] Applications checks...
[18:22:43] All checks skipped
[18:22:43]
[18:22:43] The system checks took: 1 minute and 24 seconds
[18:22:43]
[18:22:43] Info: End date is Wed Jun 29 18:22:43 MST 2011

"data" is a 5 gb truecrypt container ment for holding secure files and its empty but the odd thing is "data" the file i made is in home folder so thats quite odd.

---

### Post by Dangertux on 2011-06-29
Ok -- let's take it back to square 1.

First , the above output does not show anything that leads me to believe there is a root-kit present on the system as of this moment.

Second, chkrootkit really is not the best option for Ubuntu, it tends to return a lot of false positives because of how Ubuntu functions. In order to maintain compatibility with certain scripts Ubuntu uses symlinks in place of certain files that by default are not installed on this distribution. This makes chkrootkit crap its pants thinking something bad is happening when in reality it's nothing out of the ordinary. 

Third, if you're using nmap to scan your machine FROM your machine, any firewalling you have in place is going to be bypassed (due to UFW automatically allowing loopback traffic). So you're going to get different results then someone scanning your computer remotely. If you're really concerned about outbound traffic, I would use wireshark to monitor it and see what is going on. See what is connecting to where. Failing this use netstat to find out what is listening (discount things listening only on localhost). You are particularly interested in ESTABLISHED or LISTENING sockets.

Fourth , SELinux and Apparmor don't play well together, I would advise using only one.

Fifth, I highly doubt that you got a rootkit that is still residing on your hard drive. IF for some reason it has eluded your multiple reinstalls. You can wipe your entire hard drive from a liveCD prior to reinstalling.  You can do something like this

```

sudo shred -n7 -v /dev/sda

```**WARNING: THIS WILL DESTROY ALL DATA ON THE HARD DRIVE IT IS USED ON, IT IS HIGHLY IMPROBABLE THAT THIS DATA WILL EVER BE RECOVERED**

Then reinstall your OS.

Sixth, I really think you're letting this get to you too much. If anything follow the above step, reinstall fresh, don't install anything from the previous installation, turn on UFW and just chill out for a little bit.

Edit: Another suggestion would be once you have your OS back up install your programs in a VM instance 1 at a time and observe which one of them is backdoored.

Good luck.

---

### Post by Unguidedone on 2011-06-29
ok just to be safe ill do a full wipe


 very useful command ^.^

I am thinking of getting some thermite in a bag  resting on top of the ssd (airtight so it does not dirty my computers system) and have a small glass bottle of kmn04/glycerin so i can break the bottle with a metal pin and have it leak.  I can always test out that command instead but i dont have to type a sudo password : ) 
[B]
[/B]

---

### Post by Dangertux on 2011-06-29
> **Unguidedone said:**
> ok just to be safe ill do a full wipe


 very useful command ^.^

I am thinking of getting some thermite in a bag  resting on top of the ssd (airtight so it does not dirty my computers system) and have a small glass bottle of kmn04/glycerin so i can break the bottle with a metal pin and have it leak.  I can always test out that command instead but i dont have to type a sudo password : ) 


Or maybe you should just go out with friends and let the paranoia wear off? LOL

The new Transformers movie was pretty cool , should go see that.

---

### Post by linuxpenguin on 2011-06-29
Yeah there always is the possibility of a false positive with any security scanner. If you know that you've been installing from scratch and have been using an uninfected install disk, I wouldn't worry about it. Try another anti-rootkit, and if that checks out OK then don't worry.

---

### Post by doas777 on 2011-06-30
> **Dangertux said:**
> Or maybe you should just go out with friends and let the paranoia wear off? LOL

The new Transformers movie was pretty cool , should go see that.
wait, so, the suggestion is to get out and be more sociable, but also to go see Michael Bay's latest crapfest?  my guess is that will instill additional paranoia and agoraphobia.

---

### Post by CandidMan on 2011-06-30
I don't have a citation for this to hand at the moment but I think it's generally advised to have either Apparmor OR Selinux running on your system.
Maybe it's tenable to have both running but I remember reading a thread on here that advised against it.
Then again if you're getting the intended results from both,
Have at it :D

---

### Post by Dangertux on 2011-06-30
> **doas777 said:**
> wait, so, the suggestion is to get out and be more sociable, but also to go see Michael Bay's latest crapfest?  my guess is that will instill additional paranoia and agoraphobia.

Better then wiping a system over and over again ;-)

---

### Post by Unguidedone on 2011-06-30
i have very important files/ (things?) that needs to be secured thats why making sure the system is safe is of the most importance.

---

### Post by emiller12345 on 2011-07-01
> **Unguidedone said:**
> i have very important files/ (things?) that needs to be secured thats why making sure the system is safe is of the most importance.
if your really concerned, you can drastically decrease the threat of remote data theft by storing the data on a 2nd computer that is not on the network.  You should also be careful of 'security overload', where you have too much security and nothings works properly because of it, which you assume is another rootkit taking hold of your computer.  One of the programs you used to scan your computer earlier detected open ports; these should be verified from a remote computer scanning the suspected one.  GRC has a website called shieldsup which can help.  but if your behind a NAT router or hardware firewall it may end up scanning that instead.

---

### Post by Dangertux on 2011-07-01
> **Unguidedone said:**
> i have very important files/ (things?) that needs to be secured thats why making sure the system is safe is of the most importance.

I understand , but IMO no piece of data is worth my sanity but that's just me.

---

### Post by doas777 on 2011-07-01
> **Unguidedone said:**
> my system was hardened :(    (not saying it was perfect but it was reasonably safe)

i installed apparmor,selinux, harded the kernel, encrypted huge partions of my hardrive with truecrypt, used a password safe, only used aes encryption, setup firewalls (software firewall and physical firewall), used strong passwords, installed snort, installed 2 anti virus programs, checked all ports (all were steathed none were open) ~ updated my system often, i only downloaded programs from the ubuntu software center.


i found out before my system was scanned that something was wrong, i was using nmap and was seeing odd packet traffic activity yes from 3 ports (failed to write it down) and had higher then normal cpu usage

the only thing i would change is connect to the internet with a secure encrypted vpn. ya ill power down now...

secure VPN is going overboard methinks. but definitely disable upnp on your router, and develop a password-change policy.

TBH, the most likely scenario is that you enabled a bad ppa/repo, installed the wrong .deb, or that someone gained physical access to your box.  rootkits aren't like spyware; they don't just happen. they can be installed by a trojan exploiting a sudo timeout, but that is obviously very rare, as the Trojan package would have to be specifically targeted at a linux stack. Were that the case, I would suspect a targeted attack (or at least that you got it from gnome-look.org).

traditionally a rootkit is part of a interactive p0wning (someone actively attacking via a service). usually an attacker cracks an account, leverages some escalation exploit if needed, and then installs the kit, so they can ensure reliable access to the asset. If you don't have any services or wholes in your firewall however, an interactive scenario is unlikely.

---

### Post by Unguidedone on 2011-07-02
i have been talking to a lot of people and it seems to be a false positive because of apparmor + selinux was installed when they dont work well together.

---

### Post by Dangertux on 2011-07-03
> **doas777 said:**
>  (or at least that you got it from gnome-look.org).

The number one malware distributor for Ubuntu right there...I'm only being semi-sarcastic about that lol:D

---

### Post by desire.linux on 2011-07-03
When reinstalling a compromised system, it is important to delete the partition table of the system HDD first. Gparted does that.

---

