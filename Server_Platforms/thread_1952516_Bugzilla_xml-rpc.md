---
title: "Bugzilla xml-rpc"
date: 2012-04-04
forum: Server Platforms
---

### Post by DigitalDouwe on 2012-04-04
Hi all,

We have a server install of oneiric on which we have installed bugzilla3 through apt-get. (version 3.6.3 if i understand the release notes correctly)

Everything seems to be working fine except for bugzilla's xml-rpc feature. All we get is a big red banner saying "The XML-RPC Interface feature is not available in this Bugzilla." I've checked the apache error logs but there's nothing of interest there. Nor does bugzilla give us any more clues than said banner.

Is there a way to get xml-rpc working through a normal install using apt-get? We rather not install from source to preserve settings etc and because we been down that road before and it took us a day...

Any help would be greatly appreciated.

---

### Post by sasbock on 2013-03-30
I was able to enable the XML-RPC interface feature in Bugzilla by installing "librpc-xml-perl" and "libtest-taint-perl":

sudo apt-get install librpc-xml-perl libtest-taint-perl

Hope this helps.
Stefan

---

### Post by sasbock on 2013-03-30
And of course you will need "libsoap-lite-perl" as well:


sudo apt-get install libsoap-lite-perl librpc-xml-perl libtest-taint-perl

---

