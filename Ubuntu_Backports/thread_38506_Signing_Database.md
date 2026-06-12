---
title: "Signing Database"
date: 2005-05-31
forum: Ubuntu Backports
---

### Post by Mez on 2005-05-31
> Existing signing architecture:

All Packages[.gz] files contain md5sums for every .deb listed. The former files of course get refreshed whenever you do "apt-get update". apt-get [apt-zip, apt-cdrom] refuses to further handle any package whose md5sum proves upon download to not match the stored hash value. Instead, it will attempt redownload, on the assumption that it wasn't fully retrieved.

Each Packages[.gz] file's own md5sum is provided in the accompanying Release file.

Release files are in turn signed by the master package-releasing program's gpg key, and the hash stored in Release.gpg in the same directory.

Automated methods for checking Release.gpg files aren't yet in place. A script exists, but hasn't yet been disseminated because there are still some fundamental holes to deal with, e.g., EvilCo gets root on a mirror, and merely fails to roll in security updates. debsigs will still check out, and even Release.gpg will still be valid -- just outdated. But systems using the mirror will fail to get security updates that EvilCo makes sure the mirror isn't providing.

Package debian-keyring is (pardon the pun) key to all this, as it's the canonical list of authorised package signers. You have to get updates more often if you're on unstable/testing than if you're on stable.

[02/2004 update: apt version 0.6 adds the capability of checking Release.gpg files against debian-keyring, and enables it by default.]

Thats good ... so... you need to create a Release File for each dist with the content snad md5/SHA1 hashes of the Release fiels (for example

[http://archive.ubuntu.com/ubuntu/dists/hoary/Release](http://archive.ubuntu.com/ubuntu/dists/hoary/Release)

and

[ftp://ftp.nerim.net/debian-marillat/dists/unstable/Release](ftp://ftp.nerim.net/debian-marillat/dists/unstable/Release)

Then the hash from this (the signature part of the gpg --clearsign) is stored in Release.gpg

this should get rid of the error

Signing the actual Packages couldnt be easier either

Assuming you have your own secret key set up in gpg as your default key, and assuming that you have the Key detaisl stored in the debian/changelog as the person submitting the changelog, then adding the

-sgpg 

to the dpkg-buildpackage command will sign the .dsc and .change files..

The signing process doesnt actualyl sign the .deb files, just those (used in deb-src's I beleive)

hope this info is useful

---

### Post by jdong on 2005-05-31
Yep; It seems like only the big Release files should be signed with GPG and put in Release.gpg.
 
 
I'm working on implementing signing at the master server rather than at the developer's end.
 
In fact, I'm trying to centralize many tasks, including sources.list generation, at the server's end.

---

### Post by Mez on 2005-05-31
just as I told you on AIM :d Lets hope it works... and ahving it sort all mthat stuff out on the server end would be a lot better...  cause otherwise one person has to sign it.

I'm sure you can do it thugh, and look forward to seeing it, and hope i helped (even if I was probably annoying the hell out of you on AIM)

---

### Post by Mez on 2005-06-01
To sign:
```
gpg --armor --detach-sign -o Release.gpg Release
```
Remember, Release and Release.gpg need to eb in the root of the dist

---

### Post by jayc on 2005-06-14
[QUOTE=jdong]Yep; It seems like only the big Release files should be signed with GPG and put in Release.gpg.
 
 
I'm working on implementing signing at the master server rather than at the developer's end.
 
In fact, I'm trying to centralize many tasks, including sources.list generation, at the server's end.[/QUOTE]

Packages are supposed to be signed on the developer's end with their key.  The repository is supposed to add the developer's public key to their keyring.  When the repository receives a package, it checks that the .changes file is signed and valid.

Then the repository **just** signs the Release file with the repository's key.  In another thread you mentioned having to sign every single package.  That is not needed to just generate a secure repository.  Just the Release file is.

---

### Post by Mez on 2005-06-15
yeah, we know all this :D which is why access control is in place, because we dont upload sources.

---

