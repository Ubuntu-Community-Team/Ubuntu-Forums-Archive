---
title: "Intrepid Server Q: OpenOffice Headless TCP issue"
date: 2009-11-22
forum: Server Platforms
---

### Post by DenisonChapin on 2009-11-22
Hey guys and gals, thanks for the support, I've been all over trying to figure this out.

I'm running a headless Intrepid server and I've tried installing openoffice3 as well as using the default openoffice.org files.

I'm trying to use either PyODConverter or JODConverter to interact w/ a headless openoffice server.  

To start the server I'm using the following command:

$ soffice -headless -accept="socket,host=127.0.0.1,port=8100;urp;" -nofirststartwizard -nologo

This does begin the soffice program:
$ ps -a

  PID TTY          TIME CMD
16958 pts/3    00:00:00 soffice.bin
16961 pts/3    00:00:00 ps

However,** when I look for how it is connected on my network, it's saying unix when it should say TCP.**

$ netstat -nap | grep office
**unix  16     [ ACC ]     STREAM     LISTENING     15229    4553/soffice.bin  **  /tmp/OSL_PIPE_0_SingleOfficeIPC_bfa67ba891bd9b76f67a649f29db7e59
unix  2      [ ]         STREAM                   140662   16958/soffice.bin
unix  2      [ ]         STREAM                   42936    7097/soffice.bin
unix  2      [ ]         STREAM                   42899    7078/soffice.bin
unix  2      [ ]         STREAM                   28625    6026/soffice.bin
unix  2      [ ]         STREAM                   28571    6009/soffice.bin
unix  2      [ ]         STREAM                   28523    5988/soffice.bin
unix  2      [ ]         STREAM                   22528    5336/soffice.bin
unix  2      [ ]         STREAM                   22444    5314/soffice.bin
unix  2      [ ]         STREAM                   22392    5295/soffice.bin
unix  5      [ ]         STREAM     CONNECTED     22338    5276/soffice.bin
unix  5      [ ]         STREAM     CONNECTED     22270    5252/soffice.bin
unix  5      [ ]         STREAM     CONNECTED     15348    4591/soffice.bin
unix  2      [ ]         STREAM     CONNECTED     15232    4553/soffice.bin    /tmp/OSL_PIPE_0_SingleOfficeIPC_bfa67ba891bd9b76f67a649f29db7e59


Whenever I use either JOD or PyOD converters I'm getting a port error :

$ /usr/lib/openoffice/program# python /home/convert/DocumentConverter.py /home/convert3/beta_bugs.doc /home/convert3/beta.pdf
ERROR! failed to connect to OpenOffice.org on port 8100


Please help!  I've spent 10+ hours on this problem!

How do I get an OpenOffice headless server to use TCP instead Unix w/in Intrepid?

---

