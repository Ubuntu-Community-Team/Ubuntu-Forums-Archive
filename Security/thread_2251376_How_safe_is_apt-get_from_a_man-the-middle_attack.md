---
title: "How safe is apt-get from a man-the-middle attack?"
date: 2014-11-03
forum: Security
---

### Post by jamal5 on 2014-11-03
I know apt-get downloads over http, meaning that your ISP or somebody using Wireshark on an unsecured wifi network can see what file you're downloading

Would it be possible for an attacker who controls the connection to inject malicious packets into a download from apt-get (and install a rootkit or similar)? I've heard apt-get has an automatic checksum feature which is supposed to prevent file corruption like this, is this bulletproof though?

Cheers

---

### Post by bashiergui on 2014-11-03
Yes if you use http then someone sniffing traffic on the wifi could see the binaries you're downloading. An attacker could sit in the middle and intercept the binaries and inject malicious code into them, then deliver them to you. However, Ubuntu uses checksums and gpg keys to verify updates. And Ubuntu would reject any tampered binaries because the keys and/or checksums won't match. See this link for details (it's for debian but it works the same for ubuntu) 

[https://wiki.debian.org/SecureApt](https://wiki.debian.org/SecureApt)

You can easily force updates over https, I'm sure several tutorials can be found if Googled. If you use https in addition to the built-in gpg keys and checksums, it won't be bullet proof. But it's as close as you'll get. There are easier ways to get root which makes attacking this particular vector improbable. Like if you choose not to update at all, then an unpatched vulnerability can be exploited.

---

### Post by jamal5 on 2014-11-05
> **bashiergui said:**
> 
You can easily force updates over https, I'm sure several tutorials can be found if Googled. If you use https in addition to the built-in gpg keys and checksums, it won't be bullet proof. But it's as close as you'll get. There are easier ways to get root which makes attacking this particular vector improbable. Like if you choose not to update at all, then an unpatched vulnerability can be exploited.

As I understand apt-get uses md5sums which are flawed, is there any way to configure it to use sha256sum? Or could you use sha256 to verify a downloaded program immediately before installation? This would take a different command then just sudo apt-get install, is it possible to use the command line to just download a program, verify it, and once it clears install it?

Sorry for the paranoia but some files like VPN clients my life depends on them being genuine!

---

### Post by slickymaster on 2014-11-05
All of packages within the Ubuntu and Debian apt repositories are signed using [SecureApt]("https://help.ubuntu.com/community/SecureApt"). Asymmetric cryptography is very secure and its highly unlikely that you will be compromised this way. 3rd party repositories are hit and miss, they may or may not be singed. If they aren't signed, apt should throw a warning informing you that you are installing an unsigned package. But if it's from a 3rd party you could also just be installing a backdoor, so make sure you trust that source.

On a side note, people don't really "inject packets" to perform MITM. They are going to use something like DNS cache poisoning or ARP table poisoning so that you download the package from an HTTP server that they control, and that isn't an injection attack.

---

### Post by Lars Noodén on 2014-11-05
> **slickymaster said:**
> All of packages within the Ubuntu and Debian apt repositories are signed using [SecureApt]("https://help.ubuntu.com/community/SecureApt"). 

Yes, but [apt-secure](http://manpages.ubuntu.com/manpages/trusty/en/man8/apt-secure.8.html) does not appear to go into the details.  OpenPGP is used to sign the Release file, e.g.
  [http://fi.archive.ubuntu.com/ubuntu/dists/trusty/Release](http://fi.archive.ubuntu.com/ubuntu/dists/trusty/Release)
  [http://fi.archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg](http://fi.archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg)

which contains the checksums for the Packages files, e.g.
  [http://fi.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages.gz](http://fi.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages.gz)

which in turn contains the checksums for the individual packages.  

However, the Release file and the dependent Packages files contain md5, sha1, and sha256 but it is not clear (to me at least) from the documentation how they are used.  

Are all three required?  Or does it fall back to a weaker one if a stronger one is missing?  If so, quietly or needing confirmation before proceeding with a fall back?  Or would it even fall back to allow un-checksummed packages?   

I guess if one knows C++ it is possible to look at the source and know for sure,

```

cd /tmp
apt-get source apt
tar Jxf apt_1.0.1ubuntu2.5.tar.xz 
cd apt-1.0.1ubuntu2.4.1

```

but it'd be nice for those kinds of details to be mentioned in the documentation.

---

