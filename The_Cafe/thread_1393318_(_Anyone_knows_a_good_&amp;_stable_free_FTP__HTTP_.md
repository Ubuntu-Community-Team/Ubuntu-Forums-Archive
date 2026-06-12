---
title: ":( Anyone knows a good &amp; stable free FTP / HTTP host provider?"
date: 2010-01-29
forum: The Cafe
---

### Post by frenchn00b on 2010-01-29
Hello,

I have been trying for having my website and upload files with ftp : [http://exofire.net/](http://exofire.net/)
well I do not recommend. 

 
Is there another alternative, good, and stable ? 
The space is whatever, it is just for some debs.

Thank you for any ftp ideas / suggestions!

---

### Post by juancarlospaco on 2010-01-29
Launchpad for DEBs

---

### Post by dolphinaura on 2010-01-29
just use launchpad's bazzar (i think its spelt like this...)

---

### Post by frenchn00b on 2010-01-29
> **dolphinaura said:**
> just use launchpad's bazzar (i think its spelt like this...)

I have bash scripts too ... not only deb ... :( :popcorn::KS


I have also this ubuntu LAMP / server installer [http://easyldap.exofire.net/files/installer/](http://easyldap.exofire.net/files/installer/)
I have to update it for samba / kerberos and would like an host

---

### Post by dolphinaura on 2010-01-29
> **frenchn00b said:**
> I have bash scripts too ... not only deb ... :( :popcorn::KS


I have also this ubuntu LAMP / server installer [http://easyldap.exofire.net/files/installer/](http://easyldap.exofire.net/files/installer/)
I have to update it for samba / kerberos and would like an host

you can upload almost ANYTHING to bazzar.

or you can try one of those dropbox/spideroak thingies, provided you place the files you want to share in the dropbox public folder.

---

### Post by frenchn00b on 2010-01-29
> **dolphinaura said:**
> you can upload almost ANYTHING to bazzar.

or you can try one of those dropbox/spideroak thingies, provided you place the files you want to share in the dropbox public folder.

Indeed bazzar, means what it is... it is damn too complicated 

You can spend a week trying to simply upload a tar.gz, come on

```

  launchpadhelp
 
Packaging/PPA/Uploading
Logged in as     –

Launchpad Help > Packaging > PPAs > Uploading a package to a PPA

Contents

   1. Uploading a package to a PPA
         1. Using packages from other distributions
   2. Next steps

Uploading a package to a PPA

Once you've built your source package, you need to upload it to Launchpad using the dput tool.

Note: We will not accept uploads of packages that are unmodified from their original source in Ubuntu or Debian, only packages that include your own changes. We ask that people include useful changelogs for each package so that users and other developers can understand what new features they are exploring in their work. Read the PPA Terms of Use for more information.

Dput uploads the following files:

    *

      .dsc
    *

      .changes
    *

      .diff.gz
    *

      and optionally the .orig.tar.gz (if you used debuild -S -sa to build your package) 

First, you need to tell dput where to send your package and by what method. To do that, edit ~/.dput.cf to look like this:

[my-ppa]
fqdn = ppa.launchpad.net
method = ftp
incoming = ~<your_launchpad_id>/<ppa_name>/ubuntu/
login = anonymous
allow_unsigned_uploads = 0

You'll need to:

    *

      Change the first line to whatever name you want to use to refer to your PPA, while retaining the square brackets. Do not use just "ppa" as the name here: that conflicts 


```

---

### Post by dolphinaura on 2010-01-29
> **frenchn00b said:**
> Indeed bazzar, means what it is... it is damn too complicated 

You can spend a week trying to simply upload a tar.gz, come on

```

  launchpadhelp
 
Packaging/PPA/Uploading
Logged in as     –

Launchpad Help > Packaging > PPAs > Uploading a package to a PPA

Contents

   1. Uploading a package to a PPA
         1. Using packages from other distributions
   2. Next steps

Uploading a package to a PPA

Once you've built your source package, you need to upload it to Launchpad using the dput tool.

Note: We will not accept uploads of packages that are unmodified from their original source in Ubuntu or Debian, only packages that include your own changes. We ask that people include useful changelogs for each package so that users and other developers can understand what new features they are exploring in their work. Read the PPA Terms of Use for more information.

Dput uploads the following files:

    *

      .dsc
    *

      .changes
    *

      .diff.gz
    *

      and optionally the .orig.tar.gz (if you used debuild -S -sa to build your package) 

First, you need to tell dput where to send your package and by what method. To do that, edit ~/.dput.cf to look like this:

[my-ppa]
fqdn = ppa.launchpad.net
method = ftp
incoming = ~<your_launchpad_id>/<ppa_name>/ubuntu/
login = anonymous
allow_unsigned_uploads = 0

You'll need to:

    *

      Change the first line to whatever name you want to use to refer to your PPA, while retaining the square brackets. Do not use just "ppa" as the name here: that conflicts 


```
thats not bzr. thats the launchpad ppa setup.

---

### Post by nilarimogard on 2010-01-29
Use Google Code (code.google.com).

---

### Post by Hetor on 2010-01-29
127.0.0.1

---

