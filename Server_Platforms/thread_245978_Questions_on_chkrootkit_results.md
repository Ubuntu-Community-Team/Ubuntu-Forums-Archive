---
title: "Questions on chkrootkit results"
date: 2006-08-28
forum: Server Platforms
---

### Post by Sagotis on 2006-08-28
Hi All

I have a few questions on the results of a chkrootkit test that I performed today.

The results in question are:

[I]Searching for suspicious files and dirs, it may take a while...
/usr/lib/jvm/.java-gcj.jinfo
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/.systemPrefs
/usr/lib/jvm/.java-1.5.0-sun.jinfo
/lib/modules/2.6.15-26-686/volatile/.mounted

Checking `sniffer'... lo: not promisc and no packet sniffer sockets
eth0: PACKET SNIFFER(/sbin/dhclient3[4389])
vmnet1: not promisc and no packet sniffer sockets
vmnet8: not promisc and no packet sniffer sockets[/I]

If I am reading this right the first group shows that the Java Virtual Machine is some how a security risk along with the mount module of the 2.6.15-26-686 kernel, while the second group shows that eth0 has a packet sniffer on it?

I Checked eth0 by doing a nmap <ip> on my system and it shows no open ports on my system - is this a false positive? Perhaps it has somethign to do with Vmware and using dhclient3 to pull an ip for the guest OS? In what ways can I test this further, to ease my conscious? And another question does the number 4389 in brackets denote the port that the sniffer is on, because if that is the case then nmap only scanned the first 1674 ports, can nmap scan above that, and how?

As to the suspicious files I did a rkhunter test and all was shown to be clean and going by rkhunter alone one would conclude that this was a false positive? However, I do not like the idea of relying on one prog alone to prove if my system is clean or not, thus there any way to test these suspicious files in question other then to use rkhunter?

Thanks in advance

from the noob,

Sagotis

---

### Post by skymt on 2006-08-28
Looks like all false positives to me. Still, please post the contents of the files chkrootkit warned about (unless they're binaries!).

dhclient3 is probably safe. It's the standard DHCP client. Still, here's what I'd do:

* Download the latest .deb ([http://archive.ubuntu.com/ubuntu/pool/main/d/dhcp3/dhcp3-common_3.0.3-6ubuntu7_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dhcp3/dhcp3-common_3.0.3-6ubuntu7_i386.deb))
* Extract /sbin/dhclient3 to your desktop from the .deb using file-roller.
* Run md5 checksums on both and compare them.

---

### Post by Sagotis on 2006-08-28
The contents of the files chkrootkit warned about are:

(1) /usr/lib/jvm/.java-gcj.jinfo 
name=java-1.4.2-gcj-4.1-1.4.2.0
alias=java-gcj
priority=1041
section=main

jre jar /usr/lib/jvm/java-gcj/jre/bin/jar
jre java /usr/lib/jvm/java-gcj/jre/bin/java
jre rmiregistry /usr/lib/jvm/java-gcj/jre/bin/rmiregistry
jdk javac /usr/lib/jvm/java-gcj/bin/javac
jdk javadoc /usr/lib/jvm/java-gcj/bin/javadoc
jdk javah /usr/lib/jvm/java-gcj/bin/javah
jdk rmic /usr/lib/jvm/java-gcj/bin/rmic

(2) /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/.systemPrefs
No editer can open this file, which would mean that this is a binary file?

(3) /usr/lib/jvm/.java-1.5.0-sun.jinfo
name=java-1.5.0-sun-1.5.0.06
alias=java-1.5.0-sun
priority=53
section=non-free

jre ControlPanel /usr/lib/jvm/java-1.5.0-sun/jre/bin/ControlPanel
jre java /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
jre java_vm /usr/lib/jvm/java-1.5.0-sun/jre/bin/java_vm
jre javaws /usr/lib/jvm/java-1.5.0-sun/jre/bin/javaws
jre keytool /usr/lib/jvm/java-1.5.0-sun/jre/bin/keytool
jre pack200 /usr/lib/jvm/java-1.5.0-sun/jre/bin/pack200
jre policytool /usr/lib/jvm/java-1.5.0-sun/jre/bin/policytool
jre rmid /usr/lib/jvm/java-1.5.0-sun/jre/bin/rmid
jre rmiregistry /usr/lib/jvm/java-1.5.0-sun/jre/bin/rmiregistry
jre unpack200 /usr/lib/jvm/java-1.5.0-sun/jre/bin/unpack200
jdk HtmlConverter /usr/lib/jvm/java-1.5.0-sun/bin/HtmlConverter
jdk appletviewer /usr/lib/jvm/java-1.5.0-sun/bin/appletviewer
jdk apt /usr/lib/jvm/java-1.5.0-sun/bin/apt
jdk extcheck /usr/lib/jvm/java-1.5.0-sun/bin/extcheck
jdk idlj /usr/lib/jvm/java-1.5.0-sun/bin/idlj
jdk jar /usr/lib/jvm/java-1.5.0-sun/bin/jar
jdk jarsigner /usr/lib/jvm/java-1.5.0-sun/bin/jarsigner
jdk java-rmi.cgi /usr/lib/jvm/java-1.5.0-sun/bin/java-rmi.cgi
jdk javac /usr/lib/jvm/java-1.5.0-sun/bin/javac
jdk javadoc /usr/lib/jvm/java-1.5.0-sun/bin/javadoc
jdk javah /usr/lib/jvm/java-1.5.0-sun/bin/javah
jdk javap /usr/lib/jvm/java-1.5.0-sun/bin/javap
jdk jconsole /usr/lib/jvm/java-1.5.0-sun/bin/jconsole
jdk jdb /usr/lib/jvm/java-1.5.0-sun/bin/jdb
jdk jinfo /usr/lib/jvm/java-1.5.0-sun/bin/jinfo
jdk jmap /usr/lib/jvm/java-1.5.0-sun/bin/jmap
jdk jps /usr/lib/jvm/java-1.5.0-sun/bin/jps
jdk jsadebugd /usr/lib/jvm/java-1.5.0-sun/bin/jsadebugd
jdk jstack /usr/lib/jvm/java-1.5.0-sun/bin/jstack
jdk jstat /usr/lib/jvm/java-1.5.0-sun/bin/jstat
jdk jstatd /usr/lib/jvm/java-1.5.0-sun/bin/jstatd
jdk native2ascii /usr/lib/jvm/java-1.5.0-sun/bin/native2ascii
jdk rmic /usr/lib/jvm/java-1.5.0-sun/bin/rmic
jdk serialver /usr/lib/jvm/java-1.5.0-sun/bin/serialver
plugin mozilla-javaplugin.so /usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
plugin firefox-javaplugin.so /usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
plugin mozilla-snapshot-javaplugin.so /usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

And (4) /lib/modules/2.6.15-26-686/volatile/.mounted
Nothing inside

And as to the checksums of the /sbin/dhclient3 there was no dhclient3 in the dhcp3-common_3.0.3-6ubuntu7_i386.deb file that you linked to, however, the one on my system came back as 6670fe2b280e74ff6da7518454b738c9  /sbin/dhclient3 when issuing the command md5sum /sbin/dhclient3.

Sagotis

---

### Post by Sagotis on 2006-08-29
An update on this issue.

skymt, I looked into the .deb files that resided in the [http://archive.ubuntu.com/ubuntu/pool/main/d/dhcp3/](http://archive.ubuntu.com/ubuntu/pool/main/d/dhcp3/) directory that you pointed to and it seems that on my system the dhcp3-client_3.0.3-6ubuntu7_i386.deb file was the one that I needed to test the checksum of the dhclient3 on my system against.

In extracting the /sbin/dhclient3 of the dhcp3-client_3.0.3-6ubuntu7_i386.deb file and then doing a md5sum on it, it does indeed match the checksum number/letter string of the one installed on my system. So I guess I can safely assume that the sniffer being reported on eth0, by chkrootkit, is in fact a false positive. Also I found out how to have nmap scan above the 1674 port defult, which is done by issuing the command nmap <ip> -p1-65535. This also shows no open ports.

As to the suspicious files and dirs that chkrootkit reported on. It would seem that all of them (/usr/lib/jvm/.java-gcj.jinfo, usr/lib/jvm/java-1.5.0-sun-1.5.0.06/.systemPrefs,/usr/lib/jvm/.java-1.5.0-sun.jinfo and /lib/modules/2.6.15-26-686/volatile/.mounted) have root only permissions. 

(It should be noted, however, that /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/.systemPrefs is a directory and not a binary.)

This doesn't rule out the fact that these could still be malicious, but this is unlikely given the fact that jvm, java firefox plugin and any modules of the 686 kernel came from the Ubuntu repositories. Thus, I can also conclude that these too are false positives.

Thanks for you're help skymt.

Sagotis

---

### Post by skymt on 2006-08-29
You're welcome. Good to hear you ruled out a hack attack.

---

