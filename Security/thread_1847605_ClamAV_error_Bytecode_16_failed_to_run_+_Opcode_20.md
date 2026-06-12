---
title: "ClamAV error: Bytecode 16 failed to run + Opcode 20 of type 0 is not implemented yet!"
date: 2011-09-21
forum: Security
---

### Post by nicorac on 2011-09-21
On my samba fileserver I run a virus scan each night with a cron job like this:
```
nice -n15 /usr/local/bin/clamscan -r -i /shares/ | grep "FOUND"
```

Till some days I'm getting these errors, repeated 7 times:
```
LibClamAV Error: Opcode 20 of type 0 is not implemented yet!
LibClamAV Warning: Bytecode 16 failed to run: Invalid argument passed to function
```

I already checked ClamAV version, as told here: [http://ubuntuforums.org/showthread.php?p=11077595]("http://ubuntuforums.org/showthread.php?p=11077595#post11077595")
```
# dpkg -l | grep clamav
clamav             0.97.2+dfsg-1ubuntu1.11.04~lucid1   anti-virus utility for Unix - command-line i
clamav-base        0.97.2+dfsg-1ubuntu1.11.04~lucid1   anti-virus utility for Unix - base package
clamav-docs        0.97.2+dfsg-1ubuntu1.11.04~lucid1   anti-virus utility for Unix - documentation
clamav-freshclam   0.97.2+dfsg-1ubuntu1.11.04~lucid1   anti-virus utility for Unix - virus database
libclamav-dev      0.97.2+dfsg-1ubuntu1.11.04~lucid1   anti-virus utility for Unix - development fi
libclamav6         0.97.2+dfsg-1ubuntu1.11.04~lucid1   anti-virus utility for Unix - library

# clamscan -V
ClamAV 0.97/13058/Mon May  9 03:12:05 2011

```
PS: I'm using the ppa repo for ClamAV.

The only strange thing I see is the output of clamscan -V that reads "0.97/..." instead of "0.97.2/...".
Already tried to remove/reinstall ClamAV package.

Can anyone help me?

---

### Post by nicorac on 2011-09-22
Problem solved, running **which** and **find** helped me to find the culprit.

I had two versions of ClamAV installed:
[LIST]
[*]0.97    compiled from source
[*]0.97.2  installed through packages
[/LIST]

v0.97 was installed into /usr/local/..., while 0.97.2 into /usr/....
Since /usr/local comes first inside PATH environment 0.97 was the running version and not the newer one.

Sorry for the noise.

---

### Post by nicorac on 2011-10-03
I'm here again because the error message reappeared today :(.

Versions I'm running:
```
# clamscan -V
ClamAV 0.97.2/13731/Mon Oct  3 15:38:40 2011

```

After some investigation, I fount that the error comes when scanning some .NET executables (stored on a Samba share):
```
# clamscan TextEditor.exe
LibClamAV Error: Opcode 20 of type 0 is not implemented yet!
LibClamAV Warning: Bytecode 16 failed to run: Invalid argument passed to function
TextEditor.exe: OK

----------- SCAN SUMMARY -----------
Known viruses: 1047674
Engine version: 0.97.2
Scanned directories: 0
Scanned files: 1
Infected files: 0
Data scanned: 0.28 MB
Data read: 0.28 MB (ratio 1.00:1)
Time: 4.887 sec (0 m 4 s)

```

I already added the ClamAV ppa to my sources and updated from there...

Can anyone help me?

---

