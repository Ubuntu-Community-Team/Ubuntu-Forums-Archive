---
title: "SSL for MD5 checksums page"
date: 2012-10-18
forum: Security
---

### Post by TDK800 on 2012-10-18
Shouldn't the checksums page be maybe ssl only to protect against MITM?

[http://releases.ubuntu.com/quantal/MD5SUMS](http://releases.ubuntu.com/quantal/MD5SUMS)

Currently not possible to access it on https protocol.

---

### Post by Lars Noodén on 2012-10-18
Also the MD5 checksum should be retired in favor of SHA2.  It seems there are already [exploits using MD5 collisions](http://www.forbes.com/sites/richardstiennon/2012/06/14/flames-md5-collision-is-the-most-worrisome-security-discovery-of-2012/).  Collisions are no longer a theoretical threat.

---

### Post by CharlesA on 2012-10-18
Just use a torrent and not worry about the MD5SUM (or SHA1SUM either).

[s]They should use the way debian does and use GPG to encrypt the MD5SUM file, so you need to grab it off a mirror... /sarcasm[/s]

EDIT: They must have changed something since the last time I installed Debian because I could actually find the MD5SUM for the current live image. I wonder it it was because the last one I used was the netinstall iso... hmmmm

---

### Post by Lars Noodén on 2012-10-18
Yes, torrent works best in that regard.  About the md5 checksums, I was thinking more about APT.

---

### Post by CharlesA on 2012-10-18
> **Lars Noodén said:**
> Yes, torrent works best in that regard.  About the md5 checksums, I was thinking more about APT.
Gotcha. Isn't the stuff in the repos signed with GPG or some such thing?

---

### Post by Lars Noodén on 2012-10-18
> **CharlesA said:**
> Gotcha. Isn't the stuff in the repos signed with GPG or some such thing?

Last I read the list of MD5 checksums of the packages was signed with PGP but that the checksums were still MD5.  Also, inside the packages, I was not sure whether the checksum was obligatory or not.

---

### Post by rookcifer on 2012-10-18
> **Lars Noodén said:**
> Last I read the list of MD5 checksums of the packages was signed with PGP but that the checksums were still MD5.  Also, inside the packages, I was not sure whether the checksum was obligatory or not.

In such a case, it's not a big deal to use MD5.  For what Ubuntu uses it for, it doesn't need to be collision resistant because it is only used as a checksum.  As for package integrity, the PGP signature is what really matters as far as the repositories are concerned.  So even if someone could create a fake package that hashes to the same MD5 signature as the real package, it wouldn't do them any good since they would need to sign it with the correct PGP key. 

But, yeah I see no reason to keep using MD5.  It has been broken for many years and *everyone* should have stopped using it years ago.  Unfortunately, for whatever reason, people are slow to adopt new crypto.  We have SHA-3 now and few people have even upgraded to SHA-2.

---

### Post by Lars Noodén on 2012-10-18
It was my understanding that the packages themselves are not signed with PGP but only checksummed and that list of checksums signed.  It would be great if all the packages themselves were actually signed with PGP, that would be rather bullet-proof.  Like I said, it was a while back since I read up on it.

---

### Post by Ms. Daisy on 2012-10-18
> **Lars Noodén said:**
> It was my understanding that the packages themselves are not signed with PGP but only checksummed and that list of checksums signed.  It would be great if all the packages themselves were actually signed with PGP, that would be rather bullet-proof.  Like I said, it was a while back since I read up on it.
I believe the packages are actually signed with PGP. 

[https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)
[QUOTE=from help.ubuntu.com][gpg (GNU Privacy Guard)]("http://www.gnupg.org/") is the tool used in secure apt to sign files and check their signatures. [/QUOTE]

---

### Post by Lars Noodén on 2012-10-19
> **Ms. Daisy said:**
> I believe the packages are actually signed with PGP. 

[https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

Thanks.  There's some more details at the Debian page, too:
[http://wiki.debian.org/SecureApt](http://wiki.debian.org/SecureApt)

It looks like the only thing that is PGP-signed is Releases:
[http://fi.archive.ubuntu.com/ubuntu/dists/quantal/](http://fi.archive.ubuntu.com/ubuntu/dists/quantal/)

and that contains only a list of MD5 sums.  It does not look like the individual packages are PGP signed.  The concern there is that it's now feasible for individuals and small groups to generate MD5 collisions and be able to inject modified packages that nonetheless have matching MD5 checksums.  

It would require coordination with Debian and a bit of hassle, but it appears feasible to start using SHA256 or better in Releases.

---

### Post by ottosykora on 2012-10-19
but if you have not the right pubkey on your keyring you can not install any package, therefore to me it looks like everything is signed and only if this sig is OK it will be installed.

---

