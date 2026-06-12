---
title: "Kerrighed on Ubuntu, easy way?"
date: 2010-09-02
forum: Server Platforms
---

### Post by e-San on 2010-09-02
Hi there!

I have just set up my 'new' server (old one is gone due to weird bios problems) wich is 2xP3@933 and almost 1GB.
Since it is more 'home server' than 'regular server' i set up transmission, nfs, mpd, samba and will set up more useful stuff for home network and other purposes.

BUT.
I decided to make some funny stuff (not as usful as nfs for example) to /make some fun/ lern something new.

I decided to build some 'home cluster'. I read some articles, manuals and howto's, but there is, propably, too hard to force language barier for me.

I found many useful pages and few softwares like ie. 
Beowulf
on XBOX: [http://www.anandtech.com/show/1539/11](http://www.anandtech.com/show/1539/11)
[http://ubuntuforums.org/showthread.php?t=1030849](http://ubuntuforums.org/showthread.php?t=1030849)


Kerrighed
for Debian, i almost understand it! 
[http://ubuntuforums.org/showthread.php?t=1030849](http://ubuntuforums.org/showthread.php?t=1030849)
build.sh from EasyUbuntuClustering [https://wiki.ubuntu.com/EasyUbuntuClustering?action=AttachFile&do=view&target=build.sh](https://wiki.ubuntu.com/EasyUbuntuClustering?action=AttachFile&do=view&target=build.sh) wich covers everithing from Kerrighed's official manual
TRAC? [http://trac.nchc.org.tw/grid/wiki/krg_DRBL](http://trac.nchc.org.tw/grid/wiki/krg_DRBL)
[https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide](https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide)

LinuxPMI
again trac? [http://linuxpmi.org/trac/](http://linuxpmi.org/trac/)

OpenMosix
[http://ubuntuforums.org/showthread.php?t=17012](http://ubuntuforums.org/showthread.php?t=17012)

Heartbeat, UltraMonkey and so on...
[http://www.linuxjournal.com/article/5862?page=0,2](http://www.linuxjournal.com/article/5862?page=0,2)

It should be enought to make this working, but still - i do not get it.

Well, meybe it is beacose i have some diffrent goals.
So, what they are?
I am trying to set up speciffic cluster.
I operate on small laptop eeePC 900 - quite cool but slow, got my parents PC (Ubuntu 10.04) and server (Ubuntu server 10.04).

Goal is to make server ocassionally machine to make some compiling or something CPU-stress. But, when my parent's pc is turned on, server should connect to it and use it as another CPU.

I am wondering, if i could use configured-like-that-server to work as my laptop's SMP and, if not, to use my laptop (when connected) as another node.

Another BUT.
in most of those howto's i found information how to prepare standalone linux for node's purposes. And thats the first problem.

Secondly, I have some problems with naming. When there is main server, when helping server (node?) and who is calling work to done (i.e. comiling kernel).

That's all folks!
Regards!

P.s. i know there is few topics about howto, but ain't like to make any rubbish in PRO topics.

This is quite cool story, inspiration: [http://helmer.sfe.se/](http://helmer.sfe.se/) - linux cluster in  IKEA's 'rack' ;)
more and more: [http://www.linuxclusters.com/](http://www.linuxclusters.com/)

---

