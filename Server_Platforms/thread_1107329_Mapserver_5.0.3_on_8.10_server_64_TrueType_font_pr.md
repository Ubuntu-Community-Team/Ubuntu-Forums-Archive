---
title: "Mapserver 5.0.3 on 8.10 server 64 TrueType font problem"
date: 2009-03-26
forum: Server Platforms
---

### Post by radiognome on 2009-03-26
I have cgi-mapserver 5.0.0.3 running on Server 8.04 i386 without any problem.

Today I installed cgi-mapserver on a Server 8.10-amd64 machine. The ibex-repository gave me cgi-mapserver 5.0.3.
The two machines are identical in their installed packages, appart from of course the latter being 8.10 and 64 bits and having been upgraded to this from 8.04.

I used the same mapfiles, only altering a path here and there (the 8.04 has some files on a NAS). Everything works fine appart from...
I use TrueType fonts for displaying labels in some layers, and that does not work anymore. A default bitmap-font works, but not the truetype font's I refer to in my fontset. I get a server-misconfiguration-error. :confused:

I checked all my path's tripple, compared both servers for different right's settings, apache2 settings and such. Checked if the fontset could be found (symbolset right next to it is found and if I move the fonts.txt, the error message changes telling me the fonts can't be found). I tried to use the TrueType fonts build in Ubuntu, used relative and absolute paths, I reinstalled libfreetype6 and left the office way past dinnertime not having the problem solved.

Anyone have a clue? I will check again tomorrow morning at work, where I will be able to post some details from the serversettings, mapfiles, logs and such, if anyone is interested.

Thanks for reading,

Martin

---

