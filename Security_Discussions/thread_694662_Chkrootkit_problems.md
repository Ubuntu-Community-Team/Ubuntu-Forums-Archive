---
title: "Chkrootkit problems"
date: 2008-02-12
forum: Security Discussions
---

### Post by jsvidyad on 2008-02-12
Hi!!

  I had posted this in another forum earlier. I am reposting it here as this forum is more appropriate.


I run Dapper Drake on a core 2 duo machine.

I ran chkrootkit on my computer and there are some suspicious results. can someone tell me if I have to worry or these are false positives. The suspicious items are given below:

Checking `lkm'... You have 4 process hidden for readdir command
You have 4 process hidden for ps command

chkproc: Warning: Possible LKM Trojan installed

The full result of chkrootkit is given below:

ROOTDIR is `/'
Checking `amd'... not found
Checking `basename'... not infected
Checking `biff'... not found
Checking `chfn'... not infected
Checking `chsh'... not infected
Checking `cron'... not infected
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
Checking `sendmail'... not found
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
Searching for t0rn's v8 defaults... nothing found
Searching for Lion Worm default files and dirs... nothing found
Searching for RSHA's default files and dir... nothing found
Searching for RH-Sharpe's default files... nothing found
Searching for Ambient's rootkit (ark) default files and dirs... nothing found
Searching for suspicious files and dirs, it may take a while...
/usr/lib/jvm/.java-gcj.jinfo
/usr/lib/jvm/.java-1.5.0-sun.jinfo
/usr/lib/jvm/.ia32-java-1.5.0-sun.jinfo
/usr/lib/jvm/java-1.5.0-sun-1.5.0.13/.systemPrefs
/usr/lib/blender/.Blanguages
/usr/lib/blender/.bfont.ttf
/usr/lib/scilab/libs/.cvsignore
/usr/lib/scilab/libs/.ghost
/usr/lib/scilab/bin/.scicos_pal
/usr/lib/scilab/util/.cvsignore
/usr/lib/scilab/macros/.cvsignore
/usr/lib/scilab/macros/scicos_blocks/Branching/.cv signore
/usr/lib/scilab/macros/scicos_blocks/Electrical/.c vsignore
/usr/lib/scilab/macros/scicos_blocks/Events/.cvsig nore
/usr/lib/scilab/macros/scicos_blocks/Hydraulics/.c vsignore
/usr/lib/scilab/macros/scicos_blocks/Linear/.cvsig nore
/usr/lib/scilab/macros/scicos_blocks/Misc/.cvsigno re
/usr/lib/scilab/macros/scicos_blocks/NonLinear/.cv signore
/usr/lib/scilab/macros/scicos_blocks/Sinks/.cvsign ore
/usr/lib/scilab/macros/scicos_blocks/Sources/.cvsi gnore
/usr/lib/scilab/macros/scicos_blocks/Threshold/.cv signore
/usr/lib/scilab/X11_defaults/.cvsignore
/usr/lib/scilab/config/.cvsignore
/usr/lib/scilab/.pvmd.conf
/usr/lib/scilab/.binary
/usr/lib/scilab/man/eng/arma/.cvsignore
/usr/lib/scilab/man/eng/dcd/.cvsignore
/usr/lib/scilab/man/eng/linear/.cvsignore
/usr/lib/scilab/man/eng/gui/.cvsignore
/usr/lib/scilab/man/eng/control/.cvsignore
/usr/lib/scilab/man/eng/elementary/.cvsignore
/usr/lib/scilab/man/eng/fileio/.cvsignore
/usr/lib/scilab/man/eng/functions/.cvsignore
/usr/lib/scilab/man/eng/graphics/.cvsignore
/usr/lib/scilab/man/eng/robust/.cvsignore
/usr/lib/scilab/man/eng/pvm/.cvsignore
/usr/lib/scilab/man/eng/identification/.cvsignore
/usr/lib/scilab/man/eng/metanet/.cvsignore
/usr/lib/scilab/man/eng/mtlb/.cvsignore
/usr/lib/scilab/man/eng/nonlinear/.cvsignore
/usr/lib/scilab/man/eng/polynomials/.cvsignore
/usr/lib/scilab/man/eng/programming/.cvsignore
/usr/lib/scilab/man/eng/statistics/.cvsignore
/usr/lib/scilab/man/eng/scicos/.cvsignore
/usr/lib/scilab/man/eng/signal/.cvsignore
/usr/lib/scilab/man/eng/sound/.cvsignore
/usr/lib/scilab/man/eng/translation/.cvsignore
/usr/lib/scilab/man/eng/strings/.cvsignore
/usr/lib/scilab/man/eng/tdcs/.cvsignore
/usr/lib/scilab/man/eng/tksci/.cvsignore
/usr/lib/scilab/man/eng/utilities/.cvsignore
/usr/lib/scilab/man/fr/arma/.cvsignore
/usr/lib/scilab/man/fr/dcd/.cvsignore
/usr/lib/scilab/man/fr/linear/.cvsignore
/usr/lib/scilab/man/fr/gui/.cvsignore
/usr/lib/scilab/man/fr/control/.cvsignore
/usr/lib/scilab/man/fr/elementary/.cvsignore
/usr/lib/scilab/man/fr/fileio/.cvsignore
/usr/lib/scilab/man/fr/functions/.cvsignore
/usr/lib/scilab/man/fr/graphics/.cvsignore
/usr/lib/scilab/man/fr/robust/.cvsignore
/usr/lib/scilab/man/fr/pvm/.cvsignore
/usr/lib/scilab/man/fr/identification/.cvsignore
/usr/lib/scilab/man/fr/metanet/.cvsignore
/usr/lib/scilab/man/fr/mtlb/.cvsignore
/usr/lib/scilab/man/fr/nonlinear/.cvsignore
/usr/lib/scilab/man/fr/polynomials/.cvsignore
/usr/lib/scilab/man/fr/programming/.cvsignore
/usr/lib/scilab/man/fr/statistics/.cvsignore
/usr/lib/scilab/man/fr/scicos/.cvsignore
/usr/lib/scilab/man/fr/signal/.cvsignore
/usr/lib/scilab/man/fr/sound/.cvsignore
/usr/lib/scilab/man/fr/translation/.cvsignore
/usr/lib/scilab/man/fr/strings/.cvsignore
/usr/lib/scilab/man/fr/tdcs/.cvsignore
/usr/lib/scilab/man/fr/tksci/.cvsignore
/usr/lib/scilab/man/fr/utilities/.cvsignore
/usr/lib/scilab/examples/callsci/.scicos_pal
/usr/lib/scilab/examples/callsci/callsciC/.scicos_ pal
/usr/lib/scilab/examples/callsci/callsciC++/.scico s_pal
/usr/lib/scilab/examples/callsci/callsciJava/.scic os_pal
/usr/lib/j2se/1.4/jre/.systemPrefs
/usr/lib/j2se/1.4/jre/.systemPrefs/.systemRootModF ile
/usr/lib/j2se/1.4/jre/.systemPrefs/.system.lock
/lib/modules/2.6.15-51-amd64-xeon/volatile/.mounted
/usr/lib/j2se/1.4/jre/.systemPrefs
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
Searching for anomalies in shell history files... nothing found
Checking `asp'... not infected
Checking `bindshell'... not infected
Checking `lkm'... You have 4 process hidden for readdir command
You have 4 process hidden for ps command
chkproc: Warning: Possible LKM Trojan installed
Checking `rexedcs'... not found
Checking `sniffer'... lo: not promisc and no packet sniffer sockets
eth1: PACKET SNIFFER(/sbin/wpa_supplicant[5625], /sbin/dhclient3[5658])
Checking `w55808'... not infected
Checking `wted'... chkwtmp: nothing deleted
Checking `scalper'... not infected
Checking `slapper'... not infected
Checking `z2'... chklastlog: nothing deleted

---

### Post by k_grdn on 2008-02-12
Hi,

Chkproc checks "ps" output with process dirs in /proc.
Some processes are shortlived and die before chkproc can check 'em,
then chkproc shows an error.

Install rkhunter and run a full check to get a second opinion.

It's good practice to investigate false positives.

Regards,

k_grdn

---

