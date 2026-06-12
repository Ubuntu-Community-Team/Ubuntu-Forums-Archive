---
title: "clamscan files infected"
date: 2009-08-20
forum: Security
---

### Post by swiftwood on 2009-08-20
I downloaded the lasted clamscan using the system updater and ran clamscan

The clamscan files themselves came up infected!

/usr/share/clamav-testfiles/clam.exe: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.zip: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.exe.bz2: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.cab: ClamAV-Test-File FOUND
/var/lib/clamav-getfiles/eicar.com: Eicar-Test-Signature FOUND

Now what?

Do I just deleted this files and reinstall? 
Which I'm afraid to do obviously!

---

### Post by ceezy10 on 2009-08-20
I believe those are test files to see if the AV is working. I know he eicar file is a test virus. But even if these were real viruses you don't have to worry because they can't affect your safe linux machine
[http://en.wikipedia.org/wiki/EICAR_test_file](http://en.wikipedia.org/wiki/EICAR_test_file)

---

### Post by cprofitt on 2009-08-20
The directory is:

/clamav-testfiles/

the result is:

ClamAV-Test-File FOUND

Pretty sure they are just test files.

---

### Post by Agent ME on 2009-08-20
The test files are harmless files which Clamscan is set to detect, simply to help in testing that the scanning is set up properly (so you don't have to use a real virus to make sure it's running correctly).

---

