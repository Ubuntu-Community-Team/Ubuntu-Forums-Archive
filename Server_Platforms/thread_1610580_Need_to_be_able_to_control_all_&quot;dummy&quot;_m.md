---
title: "Need to be able to control all &quot;dummy&quot; machines in the building"
date: 2010-10-31
forum: Server Platforms
---

### Post by carsonrose on 2010-10-31
I have about 16 machines that all run Ubuntu, well really Xubuntu... but anyways.......

I want to be able to see all of them on the network, push updates to the machines, remotely control them... when i put a folder on one desktop I want it to appear on everyones desktops....

I used to do this in windows by making everyone remote into the server using TS client or Gnome-RDP... but that created a HUGE load on that server......

How would I do this with Ubuntu?

:guitar::guitar::guitar::guitar:

---

### Post by brettg on 2010-10-31
There is no single answer to this.

1) You can't AFAIK "push" updates to machines. You can however configure machines to automatically update at set times. You can control which updates go out with [apt-cacher-ng]("http://www.ubuntugeek.com/apt-cacher-ng-http-download-proxy-for-software-packages.html") 

2) I'm not sure I know what you mean by "remotely control them". Do you mean use vnc/remote desktop? If that is the case google for tightvnc, nxserver or "remote xwindows"

3) You can't have users share the same home folder because that would end in chaos. You may be able to use nfs-server to export user homes and put a link in each home to a common ~/Desktop directory. Not sure how well that would work out because users would be putting crap on each others desktops. You might be able to make  ~/Desktop ro but I'm not sure if that would break things altogether. A better solution is to either set a cronjob on each PC that rsyncs from a directory on a server at set intervals and when you want a file to "appear on every desktop" you can drop it in that directory. A better way would be to make a ro softlink (eg ~/Desktop/distrib) to that shared directory so that the files you drop in there appear instantly on all PC's.

---

