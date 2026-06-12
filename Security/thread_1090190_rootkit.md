---
title: "rootkit"
date: 2009-03-08
forum: Security
---

### Post by warrior24 on 2009-03-08
I think I have a rootkit  on my box. 

ROOTDIR is `/'
Checking `amd'... not found
Checking `basename'... not infected
Checking `biff'... not found
Checking `chfn'... not infected
Checking `chsh'... not infected
Checking `cron'... not infected
Checking `crontab'... not infected
Checking `date'... not infected
Checking `du'... not infected
Checking `dirname'... not infected
Checking `echo'... not infected
Checking `egrep'... not infected
Checking `env'... not infected
Checking `find'... not infected
Checking `fingerd'... not found
Checking `gpm'... not found
Checking `grep'... not infected
Checking `hdparm'... not infected
Checking `su'... not infected
Checking `ifconfig'... not infected
Checking `inetd'... not infected
Checking `inetdconf'... not infected
Checking `identd'... not found
Checking `init'... not infected
Checking `killall'... not infected
Checking `ldsopreload'... not infected
Checking `login'... not infected
Checking `ls'... not infected
Checking `lsof'... not infected
Checking `mail'... not found
Checking `mingetty'... not found
Checking `netstat'... not infected
Checking `named'... not found
Checking `passwd'... not infected
Checking `pidof'... not infected
Checking `pop2'... not found
Checking `pop3'... not found
Checking `ps'... not infected
Checking `pstree'... not infected
Checking `rpcinfo'... not infected
Checking `rlogind'... not found
Checking `rshd'... not found
Checking `slogin'... not infected
Checking `sendmail'... not infected
Checking `sshd'... not found
Checking `syslogd'... not infected
Checking `tar'... not infected
Checking `tcpd'... not infected
Checking `tcpdump'... not infected
Checking `top'... not infected
Checking `telnetd'... not found
Checking `timed'... not found
Checking `traceroute'... not found
Checking `vdir'... not infected
Checking `w'... not infected
Checking `write'... not infected
Checking `aliens'... no suspect files
Searching for sniffer's logs, it may take a while... nothing found
Searching for HiDrootkit's default dir... nothing found
Searching for t0rn's default files and dirs... nothing found
[COLOR="Red"]Searching for t0rn's v8 defaults... Possible t0rn v8 \(or variation\) rootkit installed[/COLOR]
Searching for Lion Worm default files and dirs... nothing found
Searching for RSHA's default files and dir... nothing found
Searching for RH-Sharpe's default files... nothing found
Searching for Ambient's rootkit (ark) default files and dirs... nothing found
Searching for suspicious files and dirs, it may take a while... 
/usr/lib/xulrunner/.autoreg
/usr/lib/xulrunner-1.9.0.7/.autoreg
/usr/lib/firefox-3.0.7/.autoreg
/usr/lib/jvm/java-6-sun-1.6.0.07/.systemPrefs
/usr/lib/jvm/.java-6-sun.jinfo
/lib/modules/2.6.24-23-generic/volatile/.mounted

Searching for LPD Worm files and dirs... nothing found
Searching for Ramen Worm files and dirs... nothing found
Searching for Maniac files and dirs... nothing found
Searching for RK17 files and dirs... nothing found
Searching for Ducoci rootkit... nothing found
Searching for Adore Worm... nothing found
Searching for ShitC Worm... nothing found
Searching for Omega Worm... nothing found
Searching for Sadmind/IIS Worm... nothing found
Searching for MonKit... nothing found
Searching for Showtee... nothing found
Searching for OpticKit... nothing found
Searching for T.R.K... nothing found
Searching for Mithra... nothing found
Searching for OBSD rk v1... nothing found
Searching for LOC rootkit... nothing found
Searching for Romanian rootkit... nothing found
Searching for Suckit rootkit... nothing found
Searching for Volc rootkit... nothing found
Searching for Gold2 rootkit... nothing found
Searching for TC2 Worm default files and dirs... nothing found
Searching for Anonoying rootkit default files and dirs... nothing found
Searching for ZK rootkit default files and dirs... nothing found
Searching for ShKit rootkit default files and dirs... nothing found
Searching for AjaKit rootkit default files and dirs... nothing found
Searching for zaRwT rootkit default files and dirs... nothing found
Searching for Madalin rootkit default files... nothing found
Searching for Fu rootkit default files... nothing found
Searching for ESRK rootkit default files... nothing found
Searching for rootedoor... nothing found
Searching for ENYELKM rootkit default files... nothing found
Searching for anomalies in shell history files... /usr/bin/find: //home/adrian/.gvfs: Permission denied
/usr/bin/find: //home/adrian/.gvfs: Permission denied
nothing found
Checking `asp'... not infected
Checking `bindshell'... not infected
Checking `lkm'... chkproc: nothing detected
Checking `rexedcs'... not found
Checking `sniffer'... lo: not promisc and no packet sniffer sockets
eth0: PACKET SNIFFER(/sbin/dhclient3[6165])
Checking `w55808'... not infected
Checking `wted'... chkwtmp: nothing deleted
Checking `scalper'... not infected
Checking `slapper'... not infected
Checking `z2'... chklastlog: nothing deleted

---

### Post by hansdown on 2009-03-08
Hi warrior24.

What are you using to search?

Some good info.

[http://www.google.ca/search?q=torn+v8+rootkit&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=torn+v8+rootkit&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by LegendofTom on 2009-03-08
Looks like a rootkit.

---

### Post by hansdown on 2009-03-08
It could be a false positive, but if it really is, a fresh install might be in order.

---

### Post by brian_p on 2009-03-08
> **warrior24 said:**
> I think I have a rootkit  on my box. 

Maybe not:

[http://lists.debian.org/debian-user/2001/12/msg02253.html](http://lists.debian.org/debian-user/2001/12/msg02253.html)

Knowing the results of your investigations might help to reassure others who get the same warning.

---

### Post by hyper_ch on 2009-03-08
> **hansdown said:**
> It could be a false positive, but if it really is, a fresh install might be in order.

If in doubt, conduct a re-installation

---

### Post by brian_p on 2009-03-08
> **hyper_ch said:**
> If in doubt, conduct a re-installation

Before taking such a drastic step the OP could find out more about t0rn and conduct an audit of his system, examining, for example, the system binaries the rootkit is supposed to alter. I think ls is one such binary and chkrootkit doesn't report it as infected.

By the way, does t0rn work on libc6 based systems?

---

### Post by hyper_ch on 2009-03-08
if you got rootkitted you can't trust your system anymore.

---

### Post by warrior24 on 2009-03-08
well I found this web page [http://www.lockeddown.net/torn.html](http://www.lockeddown.net/torn.html) and I searched for the following files and didn't find them on my box.
/lib/libproc.a
/lib/libproc.so.2.0.6
/lib/libproc.so (symbolic link to /lib/libproc.so.2.0.6)
/lib/lidps1.so
/usr/include/file.h
/usr/include/hosts.h
/usr/include/log.h
/usr/include/proc.h
/lib/lblip.tk/shdcf2
/lib/lblip.tk/shhk.pub
/lib/lblip.tk/shk
/lib/lblip.tk/shrs
/usr/sbin/xntps (129.112.21.181 hardcoded into binary)
/dev/srd0 (contains encrypted md5sums)
/lib/ldd.so/tks (sniffer)
/lib/ldd.so/tkp (parser)
/lib/ldd.so/tksb (long cleaner)


That web page I linked talks about some binary's replaced with Trojans and timestamps restored, How Do I open those files? tried gedit  but it wont open it. Vi just displayed a bunch of special characters. I also ran rkhunter and got this.

---

### Post by brian_p on 2009-03-08
> **warrior24 said:**
> well I found this web page [http://www.lockeddown.net/torn.html](http://www.lockeddown.net/torn.html) and I searched for the following files and didn't find them on my box.

Good. No rootkit, then.

> That web page I linked talks about some binary's replaced with Trojans and timestamps restored, How Do I open those files? tried gedit  but it wont open it. Vi just displayed a bunch of special characters. I also ran rkhunter and got this.

The files are binaries not text files. If you want to check their integrity you could compare their md5sums with known good copies from the original debs.

---

### Post by albinootje on 2009-03-08
> **warrior24 said:**
> I think I have a rootkit  on my box. 

Searching for t0rn's default files and dirs... nothing found
[COLOR="Red"]Searching for t0rn's v8 defaults... Possible t0rn v8 \(or variation\) rootkit installed[/COLOR]

I suggest that you boot from a Linux live cd, and double check your Linux partition with rkhunter, not just with chkrootkit.

---

### Post by warrior24 on 2009-03-08
I will run the live cd thing when I get home from work. Which live cd has it included? Also if it is a false positive what is causing it?

---

### Post by jdong on 2009-03-08
Well any signature based rootkit finder is simply scanning for a small telltale fragment that it considers "unique" to a rootkit. It's perfectly feasible that random compiled output can show such patterns without being a rootkit.

If you actually have a rootkit though, and I hope you keep audit logs and periodic checksums of all system files logged to a different machine, you should not trust the system or a rootkit scanner. why?

(1) A rootkit may interfere with a scanner running within a compromised OS by giving false results.

(2) A rootkit finder is a signature based reactionary measure and lags behind the latest 0-day and custom made rootkit variants. It can find rootkits, but **because it doesn't find anything DOES NOT INDICATE you are rootkit free!**

If you actually have a rootkit I'd seriously say the only smart thing to do is restore the non-data portions of the system from your most recent uncompromised backups (which I hope is not an install CD :D).


This is why it's important to use things like tripwire so you know when the system is modified and have a history to fall back on and verify.


EDIT: I should also add that I am not convinced you have a rootkit. I think it's a false alarm more than anything else unless you have other reasons to believe you may have been rootkitted.

---

### Post by albinootje on 2009-03-08
> **warrior24 said:**
> I will run the live cd thing when I get home from work. Which live cd has it included? Also if it is a false positive what is causing it?

If you use a recent Ubuntu installation cdrom, then you can boot with the live session ("Try without installing"), and if you have an internet connection, then it's a matter of opening a terminal and run for example :
```

sudo apt-get update
sudo apt-get install rkhunter
sudo mkdir /media/sda3
sudo mount /dev/sda3 /media/sda3
sudo rkhunter -c -r /media/sda3

```
where in this example /media/sda3 is the mountpoint where your Linux / partition from your hard disk is mounted.
Replace /dev/sda3 in the example by the one that fits your Linux / partition.

---

### Post by albinootje on 2009-03-08
From the rkhunter manual page :
```

 -r, --rootdir <directory>
  If a suspect system is locally or remotely mounted, it is possible to tell rkhunter to inspect it by using
  this option. However, it must be used with care, as several of the other options specifying configuration
  directories may need to be set as well. There is no default.

```
I've just tested the rkhunter -r option, and the results are a bit shaky, i do however think that you came across a false positive from chkrootkit, and it can't harm to run rkhunter -r and compare the results concerning that specific rootkit warning.

---

