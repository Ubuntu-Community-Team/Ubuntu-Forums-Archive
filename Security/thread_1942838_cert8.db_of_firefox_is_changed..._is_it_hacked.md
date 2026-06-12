---
title: "cert8.db of firefox is changed... is it hacked?"
date: 2012-03-18
forum: Security
---

### Post by q.dinar on 2012-03-18
( copy from [http://ubuntuforums.org/showthread.php?t=1942684](http://ubuntuforums.org/showthread.php?t=1942684) )

hello
i backed up my system and have discovered that cert8.db of firefox is changed. they said to me in #firefox in freenode, that it can change only by update, or when i accept unknown certificate. i have not accepted unknown certificate nor updated firefox since last backup... i will show packages installed since last backup, (in case one of they may change certificate, but i am sure only mozilla packages "may do so", because it is changed only in one profile, and profile folders has random names):
grep installed /var/log/dpkg.log|grep -v half
...
2012-03-12 12:06:16 status installed man-db 2.5.7-8
2012-03-12 12:06:18 status installed menu 2.1.44
2012-03-12 12:06:19 status installed gnome-menus 2.30.3-1
2012-03-12 12:06:19 status installed desktop-file-utils 0.15-2
2012-03-12 12:06:20 status installed libgc1c2 1:6.8-1.2
2012-03-12 12:06:21 status installed libexiv2-9 0.20-2
2012-03-12 12:06:21 status installed exiv2 0.20-2
2012-03-12 12:06:21 status installed imagemagick 8:6.6.0.4-3+squeeze1
2012-03-12 12:06:21 status installed libgsl0ldbl 1.14+dfsg-1
2012-03-12 12:06:21 status installed libgtkspell0 2.0.16-1
2012-03-12 12:06:22 status installed libmagick++3 8:6.6.0.4-3+squeeze1
2012-03-12 12:06:22 status installed inkscape 0.47.0-2+b1
2012-03-12 12:06:22 status installed libcdt4 2.26.3-5
2012-03-12 12:06:22 status installed libgd2-noxpm 2.0.36~rc1~dfsg-5
2012-03-12 12:06:22 status installed libgraph4 2.26.3-5
2012-03-12 12:06:22 status installed libpathplan4 2.26.3-5
2012-03-12 12:06:22 status installed libxdot4 2.26.3-5
2012-03-12 12:06:22 status installed libgvc5 2.26.3-5
2012-03-12 12:06:22 status installed libmagickcore3-extra 8:6.6.0.4-3+squeeze1
2012-03-12 12:06:23 status installed libnetpbm10 2:10.0-12.2+b1
2012-03-12 12:06:23 status installed libplot2c2 2.5-4
2012-03-12 12:06:23 status installed libpstoedit0c2a 3.50-3+b1
2012-03-12 12:06:23 status installed libwmf-bin 0.2.8.4-6.1+b1
2012-03-12 12:06:23 status installed netpbm 2:10.0-12.2+b1
2012-03-12 12:06:23 status installed perlmagick 8:6.6.0.4-3+squeeze1
2012-03-12 12:06:23 status installed pstoedit 3.50-3+b1
2012-03-12 12:06:23 status installed ufraw-batch 0.16-3+b1
2012-03-12 12:06:25 status installed menu 2.1.44
2012-03-16 16:16:05 status installed man-db 2.5.7-8
2012-03-16 16:16:07 status installed tcpdump 4.1.1-1
i have checked my browsing history, i have not been in site which asked to accept certificates, even if would, i do not accept forever, only a certificate of "webmoney" is accepted forever by me.

i will attach 2 certificates. old is with "1", new is with "2".

yesterday or before it my iceweasel is crashed 2 times while i was watching embedded youtube.

i am using debian squeeze, i could not attach files in mozillazine and debian forums, so i post here. another option is mozilla support forum... but i see there is no attachments.

firefox version is iceweasel 3.5.16


attachment: [http://ubuntuforums.org/attachment.php?attachmentid=214509&d=1332058621](http://ubuntuforums.org/attachment.php?attachmentid=214509&d=1332058621) 2cert8s.zip 82.3 KB

---

### Post by CharlesA on 2012-03-18
Please don't make duplicate threads.

Since this issue applies to Debian running iceweasel, you might get more help from the debian forums, or IRC.

---

