---
title: "E: Internal Error, No file name for libssl1.0.0"
date: 2014-01-25
forum: Server Platforms
---

### Post by JnPson on 2014-01-25
I have a small error that has been annoying me for many days. I do 
```
apt-get update ; apt-get dist-upgrade
```
and the update stops with 
```
E: Internal Error, No file name for libssl1.0.0.
```
Earlier I got other errors about runnin out of disk space on /boot so I did 
```
rm *3.5.0-34*
```
just to free up space on /boot. I don't know if my action has led to this error or if it has to do with some upgrade error.

---

### Post by TheFu on 2014-01-25
removing files managed by the package manager is bad. Really, really bad. That includes kernels.  Always use the package manager (apt-get, aptitude, Synaptic, whatever ... ) to install, remove, purge, reinstall those files.

I learned this a few yrs ago the hard way.  I didn't have time to wait for an answer, ended up rebuilding the box instead.  Solve it ASAP. It will only get worse.

Oh - and here's a kernel cleanup script maker script. It only builds the cmd to be run - doesn't do anything: [http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt](http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt)

---

### Post by JnPson on 2014-02-01
Yes it was very foolish of me. But is there a way to solve this without having to re-install the server?

---

### Post by JnPson on 2014-02-13
I found this searching AskUbuntu.com [URL="http://askubuntu.com/questions/167784/how-to-resolve-e-internal-error-when-using-apt-get-remove"]http://askubuntu.com/questions/167784/how-to-resolve-e-internal-error-when-using-apt-get-remove
[/URL]```
dpkg --configure -a
```
When it's done you reboot your server and the you can run
```
apt-get update
``` and ```
apt-get dist-upgrade
```without problems.

---

