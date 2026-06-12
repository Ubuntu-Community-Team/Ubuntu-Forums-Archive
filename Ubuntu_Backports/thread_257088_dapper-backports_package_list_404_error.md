---
title: "dapper-backports package list 404 error"
date: 2006-09-14
forum: Ubuntu Backports
---

### Post by bheekling on 2006-09-14
I recently setup a partial mirror using debmirror of the ubuntu dapper repositories on one of the servers of our university, all the packages downloaded fine and I am now mirroring dapper, dapper-updates and dapper-backports with all sections and i386 and amd64 archs. But now when I try to update the repository, it gives a Packages not found 404 error for dapper-backports.
These are the errors it gives.

> 
debmirror --host=archive.ubuntu.com --root=/ubuntu -v --progress --dist=dapper,dapper-updates,dapper-backports --section=main,restricted,universe,multiverse --arch=i386,amd64 --ignore-release-gpg --proxy="http://<user>:<pass>@<host>:<port>" --method=http --nosource --dry-run /services/ftp/repos/ubuntu/archive
Mirroring to /services/ftp/repos/ubuntu/archive from [http://anonymous:archive.ubuntu.com//ubuntu/](http://anonymous:archive.ubuntu.com//ubuntu/)                         Arches: i386,amd64
Dists: dapper,dapper-updates,dapper-backports
Sections: main,restricted,universe,multiverse
Proxy: http://<user>:<pass>@<host>:<port>.
Dry run.
Attempting to get lock, this might take 2 minutes before it fails.
Get Release files.
Getting: dists/dapper/Release... ok
Getting: dists/dapper/Release.gpg... ok
gpg: Signature made Thursday 01 June 2006 12:32:10 AM IST using DSA key ID 437D05B5
gpg: Can't check signature: public key not found
Release signature does not verify.
Getting: dists/dapper-updates/Release... ok
Getting: dists/dapper-updates/Release.gpg... ok
gpg: Signature made Wednesday 23 August 2006 03:55:01 PM IST using DSA key ID 437D05B5
gpg: Can't check signature: public key not found
Release signature does not verify.
Getting: dists/dapper-backports/Release... ok
Getting: dists/dapper-backports/Release.gpg... ok
gpg: Signature made Wednesday 13 September 2006 11:04:36 PM IST using DSA key ID 437D05B5
gpg: Can't check signature: public key not found
Release signature does not verify.
Get Packages and Sources files and other miscellany.
dists/dapper-backports/universe/binary-i386/Packages needs fetch
Getting: dists/dapper-backports/universe/binary-i386/Packages... dists/dapper-backports/universe/binary-i386/Packages failed 404 Not Found
dists/dapper-backports/universe/binary-i386/Packages failed md5sum check, removing
dists/dapper-backports/universe/binary-i386/Packages failed md5sum check
dists/dapper-backports/universe/binary-amd64/Packages needs fetch
Getting: dists/dapper-backports/universe/binary-amd64/Packages... dists/dapper-backports/universe/binary-amd64/Packages failed 404 Not Found
dists/dapper-backports/universe/binary-amd64/Packages failed md5sum check, removing
dists/dapper-backports/universe/binary-amd64/Packages failed md5sum check
Errors:
 Release signature does not verify.
 Release signature does not verify.
 Release signature does not verify.
 Download of dists/dapper-backports/universe/binary-i386/Packages failed: 404 Not Found dists/dapper-backports/universe/binary-i386/Packages failed md5sum check
 Download of dists/dapper-backports/universe/binary-amd64/Packages failed: 404 Not Found dists/dapper-backports/universe/binary-amd64/Packages failed md5sum check
Failed to download some Package, Sources, Contents or release files!
WARNING: releasing 1 pending lock...


I tried downloading backports into a new directory thinking perhaps something is wrong with my partial mirror but that too failed giving md5 errors.
I tried changing the mirror to no avail. However dapper and dapper-updates mirror nicely.

---

### Post by elvis on 2006-09-14
Is there a transparent http caching-proxy between you and the outside world?  If so, try pointing to ftp mirrors rather than http mirrors to avoid cache poisoning.

---

### Post by bheekling on 2006-09-14
Ours is a non-transparent caching squid proxy... trying to use an ftp mirror gives the following error

> Mirroring to /services/ftp/repos/ubuntu/test from [ftp://anonymous:uk.archive.ubuntu.com//ubuntu/](ftp://anonymous:uk.archive.ubuntu.com//ubuntu/)
Arches: i386,amd64
Dists: dapper,dapper-updates,dapper-backports
Sections: main,restricted,universe,multiverse
Proxy: http://<user>:<pass>@<host>:<port>.
Dry run.
Attempting to get lock, this might take 2 minutes before it fails.
Net::FTP: Bad hostname 'uk.archive.ubuntu.com'
WARNING: releasing 1 pending lock...


---

