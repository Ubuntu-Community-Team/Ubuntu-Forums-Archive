---
title: "proftpd: disallow download from &quot;upload&quot; directory"
date: 2007-04-04
forum: Server Platforms
---

### Post by maksym on 2007-04-04
hi,

how do I prevent users from downloading back from the upload directory in proftpd?

spent some time reading mans in looking on the net but with no result.

here is the part of config which deals with the upload directory:

 # Upload directory

  <Directory /home/FTP-shared/upload/>
  Umask 133 133
    AllowOverwrite off
    <Limit ALL>
      DenyAll
    </Limit>

    <Limit LIST CDUP CWD XCWD XCUP PWD>
      AllowAll
    </Limit>

    <Limit STOR STOU>
      AllowAll
    </Limit>
prohibit everything in the beginnig, including RETR. How come that it is still possible to download something from that directory??

Thanks!
I

---

