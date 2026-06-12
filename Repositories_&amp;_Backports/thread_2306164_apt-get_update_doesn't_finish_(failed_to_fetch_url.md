---
title: "apt-get update doesn't finish? (failed to fetch url)"
date: 2015-12-12
forum: Repositories &amp; Backports
---

### Post by Leslie_Suhm on 2015-12-12
Every time I try "sudo apt-get update" it does a little then I get the following,

Reading package lists... Done
W: GPG error: [http://ftp.us.debian.org](http://ftp.us.debian.org) sid InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8B48AD6246925553 NO_PUBKEY 7638D0442B90D010
W: GPG error: [http://ftp.spline.de](http://ftp.spline.de) sid InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9FFAACBAE3BD538B
W: GPG error: [http://ftp.de.debian.org](http://ftp.de.debian.org) unstable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8B48AD6246925553 NO_PUBKEY 7638D0442B90D010
W: GPG error: [http://cdn.debian.net](http://cdn.debian.net) sid InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8B48AD6246925553 NO_PUBKEY 7638D0442B90D010
W: GPG error: [ftp://ftp.nl.debian.org](ftp://ftp.nl.debian.org) sid InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8B48AD6246925553 NO_PUBKEY 7638D0442B90D010
W: Failed to fetch [http://us.old-releases.ubuntu.com/ubuntu/dists/utopic/InRelease](http://us.old-releases.ubuntu.com/ubuntu/dists/utopic/InRelease)  


W: Failed to fetch [http://us.old-releases.ubuntu.com/ubuntu/dists/utopic-updates/InRelease](http://us.old-releases.ubuntu.com/ubuntu/dists/utopic-updates/InRelease)  


W: Failed to fetch [http://us.old-releases.ubuntu.com/ubuntu/dists/utopic-backports/InRelease](http://us.old-releases.ubuntu.com/ubuntu/dists/utopic-backports/InRelease)  


W: Failed to fetch [http://us.old-releases.ubuntu.com/ubuntu/dists/utopic/Release.gpg](http://us.old-releases.ubuntu.com/ubuntu/dists/utopic/Release.gpg)  Could not resolve 'us.old-releases.ubuntu.com'


W: Failed to fetch [http://us.old-releases.ubuntu.com/ubuntu/dists/utopic-updates/Release.gpg](http://us.old-releases.ubuntu.com/ubuntu/dists/utopic-updates/Release.gpg)  Could not resolve 'us.old-releases.ubuntu.com'


W: Failed to fetch [http://us.old-releases.ubuntu.com/ubuntu/dists/utopic-backports/Release.gpg](http://us.old-releases.ubuntu.com/ubuntu/dists/utopic-backports/Release.gpg)  Could not resolve 'us.old-releases.ubuntu.com'


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/utopic/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.88.153 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/utopic/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/utopic/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.88.153 80]


W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/utopic/main/binary-amd64/Packages](http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/utopic/main/binary-amd64/Packages)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/utopic/main/binary-i386/Packages](http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/utopic/main/binary-i386/Packages)  404  Not Found


W: Some index files failed to download. They have been ignored, or old ones used instead.






Help please!

---

### Post by ian-weisser on 2015-12-12
What release of Ubuntu are you running?
A complete output, including the repositories that worked, would also be helpful.

Red Flag: Those Utopic (14.10) repositories are past End Of Life and no longer supported. If you are really running 14.10, the recommended solution will be to install a supported release of Ubuntu. If you are running a different release of Ubuntu, then there is a smill bit of maintenance to do.

Red Flag: Looks like you are trying to mix Debian Sid and Debian Unstable and Ubuntu repositories. That's not supported,  and it's an easy way to break your system quite terribly. If you tell us what you were trying to accomplish, we may be able to suggest a safer, supported way to accomplish it.

---

