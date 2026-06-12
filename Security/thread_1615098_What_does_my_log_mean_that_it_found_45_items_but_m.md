---
title: "What does my log mean that it found 45 items but most are clam items"
date: 2010-11-06
forum: Security
---

### Post by toolmania1 on 2010-11-06
I ran the clam scan and 45 items were found.  Most of them said something about a clam.... type fille.  All are various type.  Do I have infections are is clam av scanning itself and finding infections that way?

How can I tell what an infection is in this output?

Do I need to put different parameters to show only the infected files?  I thought the -i parameter ensured that I only saw infected files.  This may be the case in the below posted, but I am new at running this.  Thanks in advance!

 ```
clamscan -ri --bell --exclude-dir=proc --exclude-dir=sys --exclude-dir=dev /
/usr/share/MailScanner/MailScanner/MessageBatch.pm: Eicar-Test-Signature-1 FOUND
/usr/share/clamav-testfiles/clam.exe.html: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam_cache_emax.tgz: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.7z: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam-wwpack.exe: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.exe.binhex: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.newc.cpio: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam_IScab_ext.exe: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.arj: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam-upx.exe: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam-aspack.exe: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam-nsis.exe: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.exe.mbox.base64: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.mail: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam-upack.exe: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.exe.mbox.uu: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam-pespin.exe: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.odc.cpio: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.d64.zip: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.tnef: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.bin-be.cpio: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.ole.doc: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam_IScab_int.exe: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.exe.szdd: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.sis: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.exe: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam-mew.exe: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam-fsg.exe: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam-petite.exe: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.impl.zip: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.bz2.zip: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.bin-le.cpio: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.exe.bz2: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.ea06.exe: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.chm: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.cab: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.ea05.exe: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.ppt: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam-yc.exe: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.tar.gz: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.exe.rtf: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam_ISmsi_ext.exe: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.pdf: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam_ISmsi_int.exe: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.zip: ClamAV-Test-File FOUND

----------- SCAN SUMMARY -----------
Known viruses: 848464
Engine version: 0.96.3
Scanned directories: 16219
Scanned files: 102075
Infected files: 45
Total errors: 104
Data scanned: 4691.05 MB
Data read: 10046.59 MB (ratio 0.47:1)
Time: 1285.444 sec (21 m 25 s)
```

---

### Post by uRock on 2010-11-06
Hello and welcome to the forums,

Looks like you installed the clamav-testfiles package. They are all fake virus files.

---

### Post by toolmania1 on 2010-11-06
Ha,

That's a relief.  I am new to the Ubuntu world and ClamAV.  I messed around with Red Hat years ago.  So, I still have much to learn.  But, hey, at least I know that ClamAV is working if it found the fake virus files.  I am going to leave them so that I can tell its running.  Thanks for the info!

---

### Post by uRock on 2010-11-06
Your welcome. Glad I could be of help.:P

---

