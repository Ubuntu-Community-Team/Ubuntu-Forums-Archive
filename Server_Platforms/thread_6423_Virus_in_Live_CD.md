---
title: "Virus in Live CD?"
date: 2004-11-28
forum: Server Platforms
---

### Post by penipol on 2004-11-28
I recently did a virus scan of my machine using Clamav. It reported that there was a virus in a Ubuntu Live CD I downloaded using bittorrent. I got the .torrent for it through an official Ubuntu download mirror. Can anyone tell me if the virus is real or if it is a false alarm? 
The following is a piece of the output from the virus scan:
warty-release-live-i386.iso: Trojan.URLspoof.gen FOUND

---

### Post by scp on 2004-11-28
Weird, I see the same thing (see below.) But I also scanned my iso with f-prot and got nothing. I am hoping/guessing it is a false-positive.

 
CLAMSCAN
================
$ clamscan warty-release-live-i386.iso
warty-release-live-i386.iso: Trojan.URLspoof.gen FOUND

----------- SCAN SUMMARY -----------
Known viruses: 25657
Scanned directories: 0
Scanned files: 1
Infected files: 1
Data scanned: 263.38 MB
I/O buffer size: 131072 bytes
Time: 64.087 sec (1 m 4 s)

F-PROT Scan
================
$ f-prot -ai warty-release-live-i386.iso
Virus scanning report  -  28 November 2004 @ 15:06

F-PROT ANTIVIRUS
Program version: 4.4.8
Engine version: 3.14.13

VIRUS SIGNATURE FILES
SIGN.DEF created 24 November 2004
SIGN2.DEF created 24 November 2004
MACRO.DEF created 22 November 2004

Search: warty-release-live-i386.iso
Action: Report only
Files: "Dumb" scan of all files
Switches: -ARCHIVE -PACKED -SERVER -AI


Results of virus scanning:

Files: 1
MBRs: 0
Boot sectors: 0
Objects scanned: 1

Time: 0:00

No viruses or suspicious files/boot sectors were found.

MD5
================
$ md5sum warty-release-live-i386.iso
dac84a3abf5a1a104d768d569a62579e  warty-release-live-i386.iso

$ links -dump [http://releases.ubuntu.com/warty/MD5SUMS](http://releases.ubuntu.com/warty/MD5SUMS) | grep live
   dac84a3abf5a1a104d768d569a62579e warty-release-live-i386.iso

---

### Post by scp on 2004-11-28
Just as a sidenote here, this if from McAfee's Virus Profile on this trojan:

"Indications of Infection:

There are no obvious symptoms of this exploit.  Files detected as Exploit-URLSpoof are benign themselves.  No system changes or damage occurs from accessing an Expliot-URLSpoof file.  However, following an exploited hyperlink within a detected file can result in users being tricked to divulge personal information, install malicious software, etc."

Taken from: [http://us.mcafee.com/virusInfo/default.asp?id=description&virus_k=100927](http://us.mcafee.com/virusInfo/default.asp?id=description&virus_k=100927)

(Also note that their own engine has been getting false positives on this Trojan as well  :lol:  )

I am not an expert on how Clam identifies viruses, but I am pretty certain this isn't something to worry over. Especially since this is something that exploits IE.

---

### Post by jdong on 2004-12-04
Must be a coincidental magic string in the ISO.


Try extracting the ISO and scanning all the files inside. Do any of the files get flagged?

---

### Post by khad on 2004-12-06
Not to be a jerk or anything, but can a virus do much damage on a LiveCD? This thread seems kind of pointless. The CD filesystem is read-only. It seems like a false positive, but even if a virus existed if it wanted to destroy anything, it can't really corrupt the operating system as it is on a CD and therefore cannot be changed. One of the reasons that Devil Linux is a LiveCD distribution is for that very security feature.

---

### Post by jdong on 2004-12-06
Yes. The Ubuntu LiveCD does have some Windows components -- an autorun, some Windows installers for Openoffice, Firefox, etc. It's perfectly possible that a virus slipped in with these components, which could cause SERIOUS trouble.

And since ISO's don't compress/encode data, it's perfectly possible that an AV could pick up a virus's signature from inside an ISO.

---

### Post by bazuka on 2004-12-06
Strangely, some old DOS programs do the same thing. I wouldn't be too concerned about it.

---

### Post by scp on 2004-12-06
Ok, to beat the dead horse some more, the file that clamscan doesn't like is: mainmod/mainmod1.mod   :)

(If you don't know, this file is the majority of the CD. To learn more about what this file is, read some Morphix docs :)  )
========================
$ sudo mount -o loop warty-release-live-i386.iso /mnt
$ cd /mnt
$ clamscan mainmod/mainmod1.mod
mainmod/mainmod1.mod: Trojan.URLspoof.gen FOUND

----------- SCAN SUMMARY -----------
Known viruses: 25991
Scanned directories: 0
Scanned files: 1
Infected files: 1
Data scanned: 208.00 MB
I/O buffer size: 131072 bytes
Time: 54.592 sec (0 m 54 s)

========================

But, again, f-prot finds no problems:

========================
$ f-prot -ai mainmod/mainmod1.mod
Virus scanning report  -  6 December 2004 @ 23:08

F-PROT ANTIVIRUS
Program version: 4.4.8
Engine version: 3.14.13

VIRUS SIGNATURE FILES
SIGN.DEF created 3 December 2004
SIGN2.DEF created 3 December 2004
MACRO.DEF created 6 December 2004

Search: mainmod/mainmod1.mod
Action: Report only
Files: "Dumb" scan of all files
Switches: -ARCHIVE -PACKED -SERVER -AI


Results of virus scanning:

Files: 1
MBRs: 0
Boot sectors: 0
Objects scanned: 1

Time: 0:00

No viruses or suspicious files/boot sectors were found. 
========================

Again, for the record, I think/hope this is just coincidence.

---

### Post by jdong on 2004-12-07
mainmod.o is the cloop file containing the entire / of the MORPHIX subsystem.

---

