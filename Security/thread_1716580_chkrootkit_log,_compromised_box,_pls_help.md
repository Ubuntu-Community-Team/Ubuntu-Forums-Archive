---
title: "chkrootkit log, compromised box, pls help"
date: 2011-03-28
forum: Security
---

### Post by g3skyfire on 2011-03-28
Looks like my firefox has been compromised and i have a packet sniffer. Not sure what to do. Should I just delete the suspicous files? here's the chkrootkit log:

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
Checking `inetdconf'...                                     not infected
Checking `identd'...                                        not found
Checking `init'...                                          not infected
Checking `killall'...                                       not infected
Checking `ldsopreload'...                                   not infected
Checking `login'...                                         not infected
Checking `ls'...                                            not infected
Checking `lsof'...                                          not infected
Checking `mail'...                                          not infected
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
Checking `aliens'...                                        ^C
g1skywarp@g1skywarp:~$ sudo chkrootkit -q
The following suspicious files and directories were found:  
/usr/lib/firefox-3.6.16/.autoreg /usr/lib/xulrunner-1.9.1.16/.autoreg /usr/lib/jvm/.java-6-openjdk.jinfo /usr/lib/pymodules/python2.6/.path

eth0: PACKET SNIFFER(/sbin/dhclient3[2267])
user jojo deleted or never logged from lastlog!

---

### Post by Karlchen on 2011-03-28
Hello, g3skyfire.
> **g3skyfire said:**
> Looks like my firefox has been compromised and i have a packet sniffer. Not sure what to do. Should I just delete the suspicous files? here's the chkrootkit log:
[...]
g1skywarp@g1skywarp:~$ sudo chkrootkit -q
The following suspicious files and directories were found:  
/usr/lib/firefox-3.6.16/.autoreg /usr/lib/xulrunner-1.9.1.16/.autoreg /usr/lib/jvm/.java-6-openjdk.jinfo /usr/lib/pymodules/python2.6/.path

eth0: PACKET SNIFFER(/sbin/dhclient3[2267])
user jojo deleted or never logged from lastlog!
I doubt that your Firefox has been compromised. chkrootkit seems to dislike all files named .autoreg. I can spot a similar line in my chkrootkit.log as well.
And the packet sniffer dhclient3 will be [the genuine DHCP client]("http://ubuntuforums.org/showthread.php?t=136685").
So I will not advise to remove any of the files.

Kind regards,
Karl

---

### Post by g3skyfire on 2011-03-28
Here's the rkhunter output, its never showed this before. The only thing I did was add a user to sudoer list so that i could play a mmo game online (it needed some ports open and i had to have sudo to run firestarter). Oh and i even did a full update last night.

```
sudo rkhunter -c --rwo
Warning: The file properties have changed:
         File: /bin/dmesg
         Current hash: ba73cf0644bb863cae79e56922a7ffcf1630e59b
         Stored hash : b610b6bfa0982fcf40b49c98ba4b64a17394f98e
         Current inode: 92    Stored inode: 52
         Current file modification time: 1291989422
         Stored file modification time : 1256248468
Warning: The file properties have changed:
         File: /bin/login
         Current hash: 011ad278b22a14127dc745c13b67c928fad45f6c
         Stored hash : 4e1abd52f4f8b3e6463922937abf5e1948e9ce90
         Current inode: 1474    Stored inode: 84
         Current size: 39200    Stored size: 43352
         Current file modification time: 1297721506
         Stored file modification time : 1249048536
Warning: The file properties have changed:
         File: /bin/more
         Current hash: 02ae19f99b0a52daafefc78a7e455024d154c011
         Stored hash : b11eba4ec5c29d06158f9cdea44fccbbec0360fa
         Current inode: 145    Stored inode: 91
         Current file modification time: 1291989422
         Stored file modification time : 1256248468
Warning: The file properties have changed:
         File: /bin/mount
         Current hash: c8e2bc735489034a4f030e827289b24aea0b30bd
         Stored hash : 2f02c434866be2854bcdafdbc8165264f06ba27d
         Current inode: 819    Stored inode: 92
         Current file modification time: 1291989422
         Stored file modification time : 1256248468
Warning: The file properties have changed:
         File: /bin/su
         Current hash: c41480f11521faf537ae652a8b61b6a5559044f0
         Stored hash : 5b6b47b0c9cf29d70d6fbc89773b9447f7dc05e5
         Current inode: 1534    Stored inode: 136
         Current size: 31068    Stored size: 31124
         Current file modification time: 1297721506
         Stored file modification time : 1249048536
Warning: The file properties have changed:
         File: /usr/bin/dpkg
         Current hash: 629193eada2e8c130ade1aaaf20429f2e105ffb9
         Stored hash : 53d7c6c257b70f354bcf6d1cddd171180b24e8d0
         Current inode: 264714    Stored inode: 370267
         Current file modification time: 1294341454
         Stored file modification time : 1268271142
Warning: The file properties have changed:
         File: /usr/bin/dpkg-query
         Current hash: 0fd9e9b25abb9ff734b128f25c3a20a199aa6874
         Stored hash : e3fa9c39564c1860bd7d86f7005a90ef8da821a2
         Current inode: 264721    Stored inode: 370270
         Current file modification time: 1294341454
         Stored file modification time : 1268271142
Warning: The file properties have changed:
         File: /usr/bin/GET
         Current inode: 262687    Stored inode: 262685
         Current file modification time: 1283405480
         Stored file modification time : 1278518915
Warning: The file properties have changed:
         File: /usr/bin/lastlog
         Current hash: 39207a61ca04248ed0ad0047c1ac5e1b761973cd
         Stored hash : 7a33766830877a1938f55835119742561566b5da
         Current inode: 330018    Stored inode: 263299
         Current size: 9696    Stored size: 9752
         Current file modification time: 1297721506
         Stored file modification time : 1249048536
Warning: The file properties have changed:
         File: /usr/bin/ldd
         Current inode: 265040    Stored inode: 277295
         Current file modification time: 1294738613
         Stored file modification time : 1274429808
Warning: The file properties have changed:
         File: /usr/bin/logger
         Current hash: 512558f774f6b9e25ba5f0b71205cd77e5c155d8
         Stored hash : 1d45598db8e9e304dac01dc1fc8f7337115fe622
         Current inode: 263005    Stored inode: 263330
         Current file modification time: 1291989422
         Stored file modification time : 1256248468
Warning: The file properties have changed:
         File: /usr/bin/newgrp
         Current hash: f6fe1997d3fe14a97517a46b095c8e0885123b06
         Stored hash : 3645364e32a1db037510a3aea0153007eafec2c9
         Current inode: 330019    Stored inode: 263451
         Current size: 26784    Stored size: 30936
         Current file modification time: 1297721506
         Stored file modification time : 1249048536
Warning: The file properties have changed:
         File: /usr/bin/passwd
         Current hash: b44e4d0d51a7862be2a4fb95bad19c507f044df0
         Stored hash : 45fffb70df44904603e07c9b5af1a6a3639b0226
         Current inode: 335189    Stored inode: 263513
         Current size: 37140    Stored size: 41292
         Current file modification time: 1297721504
         Stored file modification time : 1249048533
Warning: The file properties have changed:
         File: /usr/bin/sudo
         Current hash: 19d4fd0295a8d758d9196eaab3ea73f8bff5a67a
         Stored hash : 6c22192ed023977e2354eaf54f4ca75e63a8a6b8
         Current inode: 273563    Stored inode: 281965
         Current file modification time: 1295460119
         Stored file modification time : 1277762260
Warning: The file properties have changed:
         File: /usr/bin/wget
         Current hash: 8d75bb181ccf0c3e677ed011a76e1fc80ac24b8b
         Stored hash : 241bec6c24c32e0ba38cc3b351c7f886b44e6612
         Current inode: 325368    Stored inode: 263906
         Current size: 230260    Stored size: 242516
         Current file modification time: 1283357492
         Stored file modification time : 1254841930
Warning: The file properties have changed:
         File: /usr/bin/whereis
         Current hash: 01ac3d0c56badfe49b8f10a878c47d9292067fff
         Stored hash : 436fe0bcb7098efb26f3f3ffb4f3fd4792be7617
         Current inode: 273663    Stored inode: 263908
         Current file modification time: 1291989422
         Stored file modification time : 1256248468
Warning: The file properties have changed:
         File: /usr/bin/lwp-request
         Current inode: 275875    Stored inode: 263357
         Current file modification time: 1282937508
         Stored file modification time : 1250356784
Warning: The file properties have changed:
         File: /sbin/ifdown
         Current hash: 1dbe4bad205cf4e388f1fef185cb0ebfd85208a1
         Stored hash : 9b09364c44c8d6891c6e7bee14943b280bf10cc8
         Current inode: 406    Stored inode: 1038
         Current file modification time: 1280243211
         Stored file modification time : 1266866128
Warning: The file properties have changed:
         File: /sbin/ifup
         Current hash: 1dbe4bad205cf4e388f1fef185cb0ebfd85208a1
         Stored hash : 9b09364c44c8d6891c6e7bee14943b280bf10cc8
         Current inode: 406    Stored inode: 1038
         Current file modification time: 1280243211
         Stored file modification time : 1266866128
Warning: The file properties have changed:
         File: /usr/sbin/groupadd
         Current hash: f02be3515aee3de07e7cc7d1c6b03ba9379d1609
         Stored hash : 2fa47f68c3218386826d777be01a63080c20652a
         Current inode: 335193    Stored inode: 267259
         Current size: 37272    Stored size: 41424
         Current file modification time: 1297721504
         Stored file modification time : 1249048533
Warning: The file properties have changed:
         File: /usr/sbin/groupdel
         Current hash: 24a85f901a06b31464fee47c789d6a8d8751095d
         Stored hash : d6593d4c019bcfaf9f9fbcb0af8525c513238380
         Current inode: 335194    Stored inode: 267260
         Current size: 33028    Stored size: 37180
         Current file modification time: 1297721504
         Stored file modification time : 1249048533
Warning: The file properties have changed:
         File: /usr/sbin/groupmod
         Current hash: 0bad9c59deddca6882ebe3b1e6fe55376366dfc3
         Stored hash : a0ab5c5a79ac333bb9cae79e25fe237d4a516353
         Current inode: 335195    Stored inode: 267261
         Current size: 43588    Stored size: 51836
         Current file modification time: 1297721504
         Stored file modification time : 1249048533
Warning: The file properties have changed:
         File: /usr/sbin/grpck
         Current hash: a3f21540dbdf94b40ddfe5004248ee919401b3a2
         Stored hash : eca47cffa6c6f7f9996b0a4a7c732e1bb2a70491
         Current inode: 335196    Stored inode: 267262
         Current size: 37120    Stored size: 41272
         Current file modification time: 1297721504
         Stored file modification time : 1249048533
Warning: The file properties have changed:
         File: /usr/sbin/nologin
         Current hash: 1e847bf5cd9d55f15132d73d56ef400498307458
         Stored hash : 38b2f9efc653e73e21e25aae464f8c11602b2d31
         Current inode: 330016    Stored inode: 267322
         Current size: 5496    Stored size: 5552
         Current file modification time: 1297721506
         Stored file modification time : 1249048536
Warning: The file properties have changed:
         File: /usr/sbin/pwck
         Current hash: 928591cc6aa201951d03e0384cb6ac8ac4b7e653
         Stored hash : 3db9567ab143ac1815726fad893d81a356ff890f
         Current inode: 335200    Stored inode: 267346
         Current size: 33012    Stored size: 37164
         Current file modification time: 1297721504
         Stored file modification time : 1249048533
Warning: The file properties have changed:
         File: /usr/sbin/useradd
         Current hash: 1f230bcd78304349e115576d485aba7c5d5c6351
         Stored hash : 19e44e3d6c4dceef4692d1fdf8ccd98ae4b1b5ad
         Current inode: 335203    Stored inode: 267416
         Current size: 76916    Stored size: 85164
         Current file modification time: 1297721504
         Stored file modification time : 1249048533
Warning: The file properties have changed:
         File: /usr/sbin/userdel
         Current hash: 4fcb305a1fb455d242b2ebdab2900c8503040621
         Stored hash : db0948298d9894e07099a9b0ddb046b67e9868f5
         Current inode: 335204    Stored inode: 267417
         Current size: 51828    Stored size: 60076
         Current file modification time: 1297721504
         Stored file modification time : 1249048533
Warning: The file properties have changed:
         File: /usr/sbin/usermod
         Current hash: fc7034320fcd1117f538615bc453b9a5f4015e31
         Stored hash : 47f49d77287d86c701604ff0b1f8adf120a4d64e
         Current inode: 335205    Stored inode: 267418
         Current size: 76692    Stored size: 84940
         Current file modification time: 1297721504
         Stored file modification time : 1249048533
Warning: The file properties have changed:
         File: /usr/sbin/vipw
         Current hash: 4e4ae0ae656ed13d6644c9371709a386f111da77
         Stored hash : 8b7bcd33d27ac55d1b99b46d1a4e285ab6aedb0d
         Current inode: 335206    Stored inode: 267425
         Current size: 39520    Stored size: 43672
         Current file modification time: 1297721504
         Stored file modification time : 1249048533
Warning: Suspicious file types found in /dev:
         /dev/shm/pulse-shm-953124018: data
         /dev/shm/pulse-shm-1068140145: data
         /dev/shm/pulse-shm-1378752424: data
         /dev/shm/pulse-shm-646991172: data
         /dev/shm/pulse-shm-752203320: data
         /dev/shm/pulse-shm-490064508: data
         /dev/shm/pulse-shm-3229531846: data
         /dev/shm/pulse-shm-3380310566: data
         /dev/shm/pulse-shm-2018645127: data
         /dev/shm/pulse-shm-2181030698: data
         /dev/shm/pulse-shm-3706113287: data
         /dev/shm/pulse-shm-1159605297: data
         /dev/shm/pulse-shm-651661739: data
         /dev/shm/pulse-shm-480994417: data
         /dev/shm/ecryptfs-g1skywarp-Private: ASCII text
Warning: Hidden directory found: /etc/.java
Warning: Hidden directory found: /dev/.udev
Warning: Hidden directory found: /dev/.initramfs
Warning: Application 'exim', version '4.69', is out of date, and possibly a security risk.
Warning: Application 'gpg', version '1.4.9', is out of date, and possibly a security risk.
Warning: Application 'openssl', version '0.9.8g', is out of date, and possibly a security risk.
```

---

### Post by Soul-Sing on 2011-03-29
Thank you for sharing the rkhunter log.
Would you please run a:
```
sudo rkhunter --propupd
```
reboot
and run a rkhunter check again, it could be very useful to compare the results.

---

### Post by Karlchen on 2011-03-29
Hello, g3skyfire.
> **g3skyfire said:**
> Here's the rkhunter output, its never showed this before. The only thing I did was add a user to sudoer list so that i could play a mmo game online (it needed some ports open and i had to have sudo to run firestarter). Oh and i even did a full update last night. [...] What does "a full update" mean in this context? You installed all the official Ubuntu updates which Synaptic offered you?

Anyway.

When first invoked, rkhunter will save a list of checksums for a lot of binary files and assume that the binaries are clean at this point in time.
Whenever rkhunter is run again, it will compare the current checksums to the saved checksums. It will alert any difference as potentially dangerous.

The point is: if you install legitimate updates then the checksums of the updated binaries will be different of course, but this does not spell any danger. Nonetheless rkhunter detects the changed checksum and displays an alert for each changed file.

The issue with tools like chkrootkit and rkhunter is that they generate messages about *potentially malicious* manipulations and leave the verification to you.

In order not to suffer a heart attack in the future when running rkhunter again, it will be helpful to regenerate the fresh set of clean rkhunter checksums immediately after you have installed new genuine updates.

Now the task of verifying for each file which rkhunter displays that it is the genuine updated file will be on you. :( Going through the dpkg.log might and finding out what exactly has been updated might make this task less cumbersome.

I wonder what the initial piece of evidence was that suggested that you machine might be (partially) compromised. The chkrootkit.log only?

Kind regards,
Karl

---

### Post by g3skyfire on 2011-03-30
> **leoquant said:**
> Thank you for sharing the rkhunter log.
Would you please run a:
```
sudo rkhunter --propupd
```reboot
and run a rkhunter check again, it could be very useful to compare the results.

Ok done, here's the new log (only warnings):

```

g1skywarp@g1skywarp:~$ sudo rkhunter -c -x --rwo
Warning: Suspicious file types found in /dev:
         /dev/shm/pulse-shm-1478074912: data
         /dev/shm/pulse-shm-2229762378: data
         /dev/shm/pulse-shm-835743446: data
         /dev/shm/pulse-shm-1395884676: data
         /dev/shm/ecryptfs-g1skywarp-Private: ASCII text
         /dev/shm/pulse-shm-3230310528: data
Warning: Hidden directory found: /etc/.java
Warning: Hidden directory found: /dev/.udev
Warning: Hidden directory found: /dev/.initramfs
Warning: Application 'exim', version '4.69', is out of date, and possibly a security risk.
Warning: Application 'gpg', version '1.4.9', is out of date, and possibly a security risk.
Warning: Application 'openssl', version '0.9.8g', is out of date, and possibly a security risk.

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)
```

---

### Post by Soul-Sing on 2011-03-30
you could update rkhunter.
the '--versioncheck' option of rkhunter itself
will indicate if a new version is available.

> Warning: Hidden directory found: /etc/.java
Warning: Hidden directory found: /dev/.udev
Warning: Hidden directory found: /dev/.initramfs
these could be whitelisted in your rkhunter.config

> # Allow the specified hidden directories.
# One directory per line (use multiple ALLOWHIDDENDIR lines).
#
ALLOWHIDDENDIR=/etc/.java
ALLOWHIDDENDIR=/dev/.udev
#ALLOWHIDDENDIR=/dev/.udevdb
#ALLOWHIDDENDIR=/dev/.udev.tdb
#ALLOWHIDDENDIR=/dev/.static
ALLOWHIDDENDIR=/dev/.initramfs
#ALLOWHIDDENDIR=/dev/.SRC-unix
#ALLOWHIDDENDIR=/dev/.mdadm

i have them whitelisted, discussed this with several people, and
the rkhuhnter mailinglist.

now these:

> dev/shm/pulse-shm-1478074912: data
         /dev/shm/pulse-shm-2229762378: data
         /dev/shm/pulse-shm-835743446: data
         /dev/shm/pulse-shm-1395884676: data
         /dev/shm/ecryptfs-g1skywarp-Private: ASCII text
         /dev/shm/pulse-shm-3230310528: data

i have only 
[COLOR="Red"]ALLOWDEVFILE=/dev/shm/pulse-shm-* [/COLOR]in the whitelist. :)

/dev/shm/ecryptfs-g1skywarp-Private: ASCII text
is the only file I don't know how to "read".

thanks for posting/sharing this.

---

