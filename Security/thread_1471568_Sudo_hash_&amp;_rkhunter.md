---
title: "Sudo hash &amp; rkhunter"
date: 2010-05-03
forum: Security
---

### Post by iatn on 2010-05-03
Last night I noted some warnings in rkhunter on my Ubuntu 9.10 PC.  One or two of which alarm me the main being:

Warning: The file properties have changed:
[21:18:52]          File: /usr/bin/sudo
[21:18:52]          Current hash: daa60130c30c5df58e10e6d280fd9dfcb5673ecf
[21:18:52]          Stored hash : 8ac63a420a2fa2b359777f66a35e8c86d948108c
[21:18:52]          Current inode: 5182    Stored inode: 27762
[21:18:52]          Current file modification time: 1271179871
[21:18:52]          Stored file modification time : 1267140126

I assumed this was an update and searched the web for the sudo version (1.7.0) and it doesn't have this hash.  I get my updates from a specific mirror but don't know how to get the hashes from there.

Can anyone confirm if this is an issue or not? By the way I'm new to Linux (<2 months).

Thanks

---

### Post by cdenley on 2010-05-03
That is the correct SHA1 checksum for /usr/bin/sudo in sudo_1.7.0-1ubuntu2.2_i386.

---

### Post by iatn on 2010-05-03
> **cdenley said:**
> That is the correct SHA1 checksum for /usr/bin/sudo in sudo_1.7.0-1ubuntu2.2_i386.

Thanks cdenley.  How did you find that out, where are the hashes for individual files stored?

I realized about a minute before receiving your message that the hash I'd looked up was for the deb file not /usr/bin/sudo

---

### Post by Rubicon_82 on 2010-05-03
Every deb archive contains a list of the MD5 checksums for its contents.  The command
```

dpkg -e <path_to_deb_package> <destination>

```
will extract the control files for a the given deb archive file into the destination directory.  The file 'md5sums' is one of these control files.  You can also find this information for the currently installed packages in '/var/lib/dpkg/info/'.

Rkhunter maintains its list of SHA1 checksums in '/var/lib/rkhunter/db/rkhunter.dat'.  This file is (and should be) only readable by root.  

You can also verify the MD5/SHA1/SHA256 checksums for the deb packages by consulting the package descriptions, e.g. 'apt-cache show <package>'.  This information is taken from the package lists in '/var/lib/apt/lists/'.

As far as I'm aware, there are no published SHA1 checksums for the files contained in a deb archive.  If you want SHA1/256 instead of MD5 checksums, you'll have to calculate those yourself.

---

### Post by cdenley on 2010-05-03
> **iatn said:**
> Thanks cdenley.  How did you find that out, where are the hashes for individual files stored?

I realized about a minute before receiving your message that the hash I'd looked up was for the deb file not /usr/bin/sudo

I downloaded the package from packages.ubuntu.com, extracted the file, then used the sha1sum command.

---

### Post by iatn on 2010-05-04
Thanks everyone for all the help so far, which has already taught me a lot.  However I'm still confused.  I first did: apt-cache show sudo and got the following checksums:

Version: 1.7.0-1ubuntu2.2
Replaces: sudo-ldap
Depends: libc6 (>= 2.8, libpam0g (>= 0.99.7.1), libpam-modules
Conflicts: sudo-ldap
Filename: pool/main/s/sudo/sudo_1.7.0-1ubuntu2.2_i386.deb
Size: 297788
MD5sum: 275954f47eee1e3070a6ed4a8f88a44a
SHA1: c16f869ec36d0927d0b23f0d5503d91fc059adcb
SHA256: 5591a54edbe62dfbab15d94955da6c80e87dc245a001112aca45e65dd993994c

Then I downloaded the file sudo_1.7.0-1ubuntu2.2_i386.deb from the ubuntu packages page and extracted the control files which gives me an MD5sum (but no SHA1sum) of sudo file of:

8b019a9a090b068151feb48a6f61dcd8  usr/bin/sudo

Interestingly the usr/bin/sudoedit claims to have exactly the same md5sum - is that feasibly?  After extracting the SHA1sum of the extracted sudo file matches that indicated by rkhunter so I guess no issue there.  My confusion is why this differs to the SHA1sum indicated by apt-cache show sudo?

Can I extract the single file from a deb package without the whole bundle including directory structure?

Thanks again for all the help.

---

### Post by cdenley on 2010-05-04
> **iatn said:**
> Thanks everyone for all the help so far, which has already taught me a lot.  However I'm still confused.  I first did: apt-cache show sudo and got the following checksums:

Version: 1.7.0-1ubuntu2.2
Replaces: sudo-ldap
Depends: libc6 (>= 2.8, libpam0g (>= 0.99.7.1), libpam-modules
Conflicts: sudo-ldap
Filename: pool/main/s/sudo/sudo_1.7.0-1ubuntu2.2_i386.deb
Size: 297788
MD5sum: 275954f47eee1e3070a6ed4a8f88a44a
SHA1: c16f869ec36d0927d0b23f0d5503d91fc059adcb
SHA256: 5591a54edbe62dfbab15d94955da6c80e87dc245a001112aca45e65dd993994c

Then I downloaded the file sudo_1.7.0-1ubuntu2.2_i386.deb from the ubuntu packages page and extracted the control files which gives me an MD5sum (but no SHA1sum) of sudo file of:

8b019a9a090b068151feb48a6f61dcd8  usr/bin/sudo

Interestingly the usr/bin/sudoedit claims to have exactly the same md5sum - is that feasibly?  After extracting the SHA1sum of the extracted sudo file matches that indicated by rkhunter so I guess no issue there.  My confusion is why this differs to the SHA1sum indicated by apt-cache show sudo?

Can I extract the single file from a deb package without the whole bundle including directory structure?

Thanks again for all the help.

```

apt-cache show sudo

```
This command will list checksums for the "sudo" package (as in .deb file), not the checksums for any individual files that may be provided by that package such as /usr/bin/sudo.

The sudo and sudoedit commands are going to have the same checksums because one is actually a symlink to the other. In other words, they aren't just identical, they are the same file.

You can extract individual files from .deb packages using File Roller, aka Archive Manager.

---

