---
title: "Update and GPG signing errors"
date: 2016-09-27
forum: Server Platforms
---

### Post by ripstar2 on 2016-09-27
Hello Ubuntu Community,

My server is Xenial.    It used to be fine but recently after cleaning some useless programs I get signing errors.  I've checked and rechecked everything.  Everything seems to be fine keys are fine.

But i cant figure this out.

Here is the error




W: GPG error: [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) xenial InRelease: Unknown error executing apt-key
W: The repository 'http://nl.archive.ubuntu.com/ubuntu xenial InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) xenial-security InRelease: Unknown error executing apt-key
W: The repository 'http://nl.archive.ubuntu.com/ubuntu xenial-security InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) xenial-updates InRelease: Unknown error executing apt-key
W: The repository 'http://nl.archive.ubuntu.com/ubuntu xenial-updates InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) xenial-proposed InRelease: Unknown error executing apt-key
W: The repository 'http://nl.archive.ubuntu.com/ubuntu xenial-proposed InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) xenial-backports InRelease: Unknown error executing apt-key
W: The repository 'http://nl.archive.ubuntu.com/ubuntu xenial-backports InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.



It doesnt matter what repo I use its always the same issue.  My keys of apt-key list are 


pub   2048R/63961D39 2016-01-25
uid                  Elio Martinez (Installer compilation) <elio.martinez.monroy@intel.com>
sub   2048R/98E81FA7 2016-01-25


pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12


pub   4096R/C0B21F32 2012-05-11
uid                  Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>


pub   4096R/EFE21092 2012-05-11
uid                  Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>


pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>





Please assist.  I dont know whats wrong  and hope to help more people.

My only thought now...Is someone is MITM and this is why this is all of a sudden randomly happening

---

