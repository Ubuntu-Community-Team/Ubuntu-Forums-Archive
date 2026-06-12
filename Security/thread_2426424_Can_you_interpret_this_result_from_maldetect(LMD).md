---
title: "Can you interpret this result from maldetect(LMD)?"
date: 2019-09-09
forum: Security
---

### Post by linux-user-0987 on 2019-09-09
PATH:          /
TOTAL FILES:   15590
TOTAL HITS:    8
TOTAL CLEANED: 0

FILE HIT LIST:
{HEX}php.gzbase64.inject.452 : /home/computer/Documents/lmd/maldetect-current.tar.gz => /usr/local/maldetect/quarantine/maldetect-current.tar.gz.37049450
{HEX}php.gzbase64.inject.452 : /home/computer/Documents/lmd/maldetect-1.6.4/files/clean/gzbase64.inject.unclassed => /usr/local/maldetect/quarantine/gzbase64.inject.unclassed.288220715
{YARA}Safe0ver_Shell__Safe_Mod_Bypass_By_Evilc0der_php : /home/computer/Documents/lmd/maldetect-1.6.4/files/sigs/md5.dat => /usr/local/maldetect/quarantine/md5.dat.1006919246
{YARA}Safe0ver_Shell__Safe_Mod_Bypass_By_Evilc0der_php : /home/computer/Documents/lmd/maldetect-1.6.4/files/sigs/rfxn.ndb => /usr/local/maldetect/quarantine/rfxn.ndb.2394931744
{YARA}Safe0ver_Shell__Safe_Mod_Bypass_By_Evilc0der_php : /home/computer/Documents/lmd/maldetect-1.6.4/files/sigs/rfxn.hdb => /usr/local/maldetect/quarantine/rfxn.hdb.627526444
{YARA}Safe0ver_Shell__Safe_Mod_Bypass_By_Evilc0der_php : /home/computer/Documents/lmd/maldetect-1.6.4/files/sigs/hex.dat => /usr/local/maldetect/quarantine/hex.dat.2561518734
{HEX}php.gzbase64.inject.452 : /home/computer/Documents/lmd/maldetect-1.6.4/files/sigs/rfxn.yara => /usr/local/maldetect/quarantine/rfxn.yara.367626301
{YARA}Safe0ver_Shell__Safe_Mod_Bypass_By_Evilc0der_php : /home/computer/Documents/lmd/maldetect-1.6.4/files/sigs/md5v2.dat => /usr/local/maldetect/quarantine/md5v2.dat.1226626496

I don't understand. It seems to be saying that maldetect (LMD) is infected? If not than what are the results?

---

### Post by TheFu on 2019-09-09
Where does maldetect store the signatures it uses to scan for problems?  If you scan those places, wouldn't those signatures be found?  Look like each is a false positive.

---

### Post by #&amp;thj^% on 2019-09-09
> **linux-user-0987 said:**
> PATH:          /
TOTAL FILES:   15590
TOTAL HITS:    8
TOTAL CLEANED: 0

FILE HIT LIST:
{HEX}php.gzbase64.inject.452 : /home/computer/Documents/lmd/maldetect-current.tar.gz => /usr/local/maldetect/quarantine/maldetect-current.tar.gz.37049450
{HEX}php.gzbase64.inject.452 : /home/computer/Documents/lmd/maldetect-1.6.4/files/clean/gzbase64.inject.unclassed => /usr/local/maldetect/quarantine/gzbase64.inject.unclassed.288220715
{YARA}Safe0ver_Shell__Safe_Mod_Bypass_By_Evilc0der_php : /home/computer/Documents/lmd/maldetect-1.6.4/files/sigs/md5.dat => /usr/local/maldetect/quarantine/md5.dat.1006919246
{YARA}Safe0ver_Shell__Safe_Mod_Bypass_By_Evilc0der_php : /home/computer/Documents/lmd/maldetect-1.6.4/files/sigs/rfxn.ndb => /usr/local/maldetect/quarantine/rfxn.ndb.2394931744
{YARA}Safe0ver_Shell__Safe_Mod_Bypass_By_Evilc0der_php : /home/computer/Documents/lmd/maldetect-1.6.4/files/sigs/rfxn.hdb => /usr/local/maldetect/quarantine/rfxn.hdb.627526444
{YARA}Safe0ver_Shell__Safe_Mod_Bypass_By_Evilc0der_php : /home/computer/Documents/lmd/maldetect-1.6.4/files/sigs/hex.dat => /usr/local/maldetect/quarantine/hex.dat.2561518734
{HEX}php.gzbase64.inject.452 : /home/computer/Documents/lmd/maldetect-1.6.4/files/sigs/rfxn.yara => /usr/local/maldetect/quarantine/rfxn.yara.367626301
{YARA}Safe0ver_Shell__Safe_Mod_Bypass_By_Evilc0der_php : /home/computer/Documents/lmd/maldetect-1.6.4/files/sigs/md5v2.dat => /usr/local/maldetect/quarantine/md5v2.dat.1226626496

I don't understand. It seems to be saying that maldetect (LMD) is infected? If not than what are the results?

[https://github.com/rfxn/linux-malware-detect/issues/87](https://github.com/rfxn/linux-malware-detect/issues/87)

[https://github.com/rfxn/linux-malware-detect/issues/242](https://github.com/rfxn/linux-malware-detect/issues/242)

---

