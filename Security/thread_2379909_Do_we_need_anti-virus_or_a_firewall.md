---
title: "Do we need anti-virus or a firewall"
date: 2017-12-11
forum: Security
---

### Post by Linuxia on 2017-12-11
The thread is an old one I know but I have installed ClamTk and only install LTS versions. Periodically my screen greys out or the screen appears to be under another's control. I switch off, disconnect from the internet and run ClamTk. Like just recently it usually "finds" 4 or so trojans, which I delete (I should keep a screen print really). Following this, normal service is resumed which makes me think some thing was in there. Surprizingly they are nearly all in Mozilla files, I use Firefox and Thunderbird. I have used and enjoyed Ubuntu for years but am frankly useless at loading software, usually looking for the idiots guide to correct a fault or install something. My software updater cannot find firestarter and I am having trouble finding a Linux version of AVG, which I have used on other machines for years and trust.

Are other users having these issues and what are you using to prevent them?

---

### Post by Perfect Storm on 2017-12-11
Anti-virus for Linux isn't necessary. The anti-virus applications you can get for Linux is for search for Windows viruses. I have been using Linux since 1999 and I had never any problems.
You problems could be other things.

---

### Post by bridnour on 2017-12-11
On the firewall side of things: 

ufw (which stands for uncomplicated firewall) should be installed by default -- even if its not active -- on your system. If not, it can be installed though the software center or through the command line:

```
sudo apt install ufw
```

I would also install gufw (search for "Firewall Configuration" in the software center), or again the command line:

```
sudo apt install gufw
```

---

### Post by cariboo on 2017-12-11
> **Linuxia said:**
> The thread is an old one I know but I have installed ClamTk and only install LTS versions. Periodically my screen greys out or the screen appears to be under another's control. I switch off, disconnect from the internet and run ClamTk. Like just recently it usually "finds" 4 or so trojans, which I delete (I should keep a screen print really). Following this, normal service is resumed which makes me think some thing was in there. Surprizingly they are nearly all in Mozilla files, I use Firefox and Thunderbird. I have used and enjoyed Ubuntu for years but am frankly useless at loading software, usually looking for the idiots guide to correct a fault or install something. My software updater cannot find firestarter and I am having trouble finding a Linux version of AVG, which I have used on other machines for years and trust.

Are other users having these issues and what are you using to prevent them?

If your screen greys out, it is usually caused by the program you are using is under heavy load, or it is about to crash. No need to shut the system down, just wait for the program to come back. Firestarter was no longer maintained, so it isn't available any more.

If you are behind a router, it's firewall should be all you need.

---

### Post by Linuxia on 2017-12-12
Thank you Artificial Intelligence, bridnour and cariboo. ufw was loaded and I discovered a record of the program is held in ClamTK history, are the following two dates worth of possible threats harmless?

ClamTk, v5.24

Mon Dec 11 10:46:45 2017
ClamAV Signatures: 6367549
Directories Scanned:
/home/lionel/.cache/mozilla/firefox/l0rtxbb2.default-1440610852660/cache2/entries

Found 4 possible threats (57514 files scanned).

/home/lionel/.cache/mozilla/firefox/l0rtxbb2.default-1440610852660/cache2/entries/F95802BC3A6EE082CE21CDD0E5C2BF520A7BCBCB      PUA.Html.Trojan.Agent-37075          
/home/lionel/.cache/mozilla/firefox/l0rtxbb2.default-1440610852660/cache2/entries/F07D7B3B839E96CD5F7E4042BAD6035CDB420903      PUA.Html.Exploit.CVE_2014_0322-1     
/home/lionel/.cache/mozilla/firefox/l0rtxbb2.default-1440610852660/cache2/entries/AB6BC674EB6FE932A91B599766C58794BB61A69B      PUA.Html.Trojan.Agent-37075          
/home/lionel/.cache/mozilla/firefox/l0rtxbb2.default-1440610852660/cache2/entries/360FF1230562129827DD5D85500FA829E9CDF50E      PUA.Html.Exploit.CVE_2014_0322-1   

ClamTk, v5.24
Mon Dec  4 15:14:38 2017
ClamAV Signatures: 6361984
Directories Scanned:
/home/lionel/.cache/mozilla/firefox/l0rtxbb2.default-1440610852660/OfflineCache/0/6
/home/lionel/.cache/mozilla/firefox/l0rtxbb2.default-1440610852660/OfflineCache/D/4
/home/lionel/.cache/mozilla/firefox/l0rtxbb2.default-1440610852660/cache2/entries

Found 4 possible threats (55333 files scanned).

/home/lionel/.cache/mozilla/firefox/l0rtxbb2.default-1440610852660/OfflineCache/D/4/987FBA1949DB5D-0                            PUA.Win.Trojan.Xored-1      
/home/lionel/.cache/mozilla/firefox/l0rtxbb2.default-1440610852660/OfflineCache/0/6/53771CBA6E2E41-0                            PUA.Win.Trojan.Xored-1      
/home/lionel/.cache/mozilla/firefox/l0rtxbb2.default-1440610852660/cache2/entries/D9BFFD70D1EA2B667D3A2E4FCF88FF4C6A00A00B      PUA.Win.Tool.Packed-177     
/home/lionel/.cache/mozilla/firefox/l0rtxbb2.default-1440610852660/cache2/entries/81ECEDC5AA5214DAD8A24B476C95CFF6218F5E02      PUA.Win.Tool.Packed-177

---

### Post by ian-weisser on 2017-12-12
> **Linuxia said:**
> Are other users having these issues and what are you using to prevent them?

It does not seem to be a software issue.
It seems to be a you-are-browsing-malicious-websites issue.

---

### Post by Habitual on 2017-12-12
lionel:

My advice...
Clean browser cache often.
Don't enable PUA option.

Close your Firefox browser and open terminal and issue:
```
rm -fr /home/lionel/.cache/mozilla/firefox/
```
and the PUAs will be gone. (from that location anyway)

[https://ubuntuforums.org/showthread.php?t=1871177](https://ubuntuforums.org/showthread.php?t=1871177)
[https://ubuntuforums.org/showthread.php?t=510812](https://ubuntuforums.org/showthread.php?t=510812)

I never needed "A/V" or a firewall on my *desktop*.
Good luck.

---

