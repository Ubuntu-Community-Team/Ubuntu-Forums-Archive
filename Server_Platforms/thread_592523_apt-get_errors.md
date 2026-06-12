---
title: "apt-get errors"
date: 2007-10-26
forum: Server Platforms
---

### Post by davebgimp on 2007-10-26
I have a remote server running Dapper and for a while now, I've been unable to update via apt-get. I keep getting this error message:
[B]
Preparing to replace bsdutils 1:2.12r-4ubuntu6 (using .../bsdutils_1%3a2.12r-4ubuntu6.1_i386.deb) ...
Unpacking replacement bsdutils ...
dpkg: error processing /var/cache/apt/archives/bsdutils_1%3a2.12r-4ubuntu6.1_i386.deb (--unpack):
 unable to make backup link of `./usr/bin/script' before installing new version: Operation not permitted
Errors were encountered while processing:
 /var/cache/apt/archives/bsdutils_1%3a2.12r-4ubuntu6.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]

I've tried using the chattr command to fix this from what I read [here]("http://ubuntuforums.org/showpost.php?p=1090468&postcount=12") but I'm still getting the same error. By the way, this is not limited. If I try to apt-get -f install to upgrade any specific package, the same error returns for that package.

Does anyone know what I could do to fix this?

---

### Post by siriusfox on 2007-10-27
I'm not sure, but I'd first try to replace the broken package.

apt-get remove <packagename>
apt-get autoclean
apt-get clean <packagename>

then try

apt-get install <packagename> again.

---

### Post by davebgimp on 2007-10-27
Would that it were that simple. ALL my package updates error like this, not just a handful of programs. It's a permission error somewhere in the chain...wish I knew why this suddenly happened, not to mention fix it.

---

