---
title: "Curl won't work on 10.04.1 LTS, but works on 9.10"
date: 2010-09-11
forum: Server Platforms
---

### Post by janpetterdale on 2010-09-11
Heya.

I've been using curl in a script of mine for a while on Ubuntu 9.10, without problems.
**Ubuntu 9.10 got the following curl installed through apt-get:**
ii  curl                              7.19.5-1ubuntu2                    Get a file from an HTTP, HTTPS or FTP server
ii  libcurl3                          7.19.5-1ubuntu2                    Multi-protocol file transfer library (OpenSS
ii  libcurl3-gnutls                   7.19.5-1ubuntu2                    Multi-protocol file transfer library (GnuTLS
ii  libcurl4-gnutls-dev               7.19.5-1ubuntu2                    Development files and documentation for libc
ii  php5-curl                         5.2.10.dfsg.1-2ubuntu6.4           CURL module for php5
ii  python-pycurl                     7.19.0-1                           Python bindings to libcurl

**My Ubuntu 10.04.1 LTS got the following curl installed through apt-get**

ii  curl                                7.19.7-1ubuntu1                   Get a file from an HTTP, HTTPS or FTP server
rc  gnupg-curl                          1.4.10-2ubuntu1                   GNU privacy guard - a free PGP replacement (
ii  libcurl3                            7.19.7-1ubuntu1                   Multi-protocol file transfer library (OpenSS
ii  libcurl3-gnutls                     7.19.7-1ubuntu1                   Multi-protocol file transfer library (GnuTLS
ii  php5-curl                           5.3.2-1ubuntu4.2                  CURL module for php5



The scripts are exactly the same, but it won't work on Ubuntu 10.04.1 LTS.
**Script is**

<snip>
USERID="snip"
PASSWORD="snip"
TAKEUPLOAD="http://snip.snip"
curl -b "uid=$USERID; pass=$PASSWORD" -F "file=@$P1.snip" -F "name=$P1" -F "nfo=@$NFO" -F "usenfo=1" -F "descr= " -F "type=$P2" -H "Expect:" $TAKEUPLOAD -D "/tmp/tmp.txt"
<snip>


**Error message:**

curl: (6) Couldn't resolve host 'uid=snip; pass=snip'
<h1>Not Found</h1>
<p>Sorry pal :(</p>


Obviously the "snip" is me cutting out sensitive information.

I've tested the script on both boxes within seconds apart so I know the receiving end is working, it has to be something with curl.

Anyone know?

Thanks

---

### Post by LightningCrash on 2010-09-20
Did you try putting the URL at the end of the command line?

from the man page:
 curl [options] [URL...]

You should also quote $TAKEUPLOAD... always quote all variables.

---

