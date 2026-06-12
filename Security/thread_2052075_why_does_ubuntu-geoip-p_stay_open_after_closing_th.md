---
title: "why does ubuntu-geoip-p stay open after closing the browser out?"
date: 2012-09-02
forum: Security
---

### Post by s1baker on 2012-09-02
hi,
After visting the Ubuntu forum website, ( or any website for that matter )
and closing out the browser, doing a "sudo netstat -atulpen" normally shows all the foreign connections closed out.

I have noticed though, that this connection stays in the "CLOSE_WAIT"
state after visiting the ubuntu forums:
```
91.189.94.25:80  ubuntu-geoip-p
```

Anybody know what it is and why it stays in a "CLOSE_WAIT" state?
Dissapears after a period of time for some reason.

Thanks

---

### Post by sanderj on 2012-09-02
It's not started by Ubuntu forums, I would say.

See [http://askubuntu.com/questions/142581/is-ubuntu-geoip-geoclue-is-used-for-tracking](http://askubuntu.com/questions/142581/is-ubuntu-geoip-geoclue-is-used-for-tracking)


PS:

It seems to be a program, not something from your browser


```
sander@R540:~$ sudo netstat -atulpen | grep geo
tcp        1      0 192.168.1.53:59870      91.189.89.144:80        CLOSE_WAIT  1000       414738      2329/ubuntu-geoip-p
tcp        1      0 192.168.1.53:59869      91.189.89.144:80        CLOSE_WAIT  125        414737      31291/ubuntu-geoip-
sander@R540:~$ ps -ef | grep -i geoip
sander    2329     1  0 Sep01 ?        00:00:03 /usr/lib/ubuntu-geoip/ubuntu-geoip-provider
sander   20644 20582  0 22:35 pts/2    00:00:00 grep --color=auto -i geoip
125      31291     1  0 16:36 ?        00:00:02 /usr/lib/ubuntu-geoip/ubuntu-geoip-provider
sander@R540:~$ 
sander@R540:~$ ll /usr/lib/ubuntu-geoip/ubuntu-geoip-provider 
-rwxr-xr-x 1 root root 18936 Jun 29  2011 /usr/lib/ubuntu-geoip/ubuntu-geoip-provider*
sander@R540:~$
```

---

### Post by Soul-Sing on 2012-09-02
"close-wait" is fine.
"ESTABLISHED" isn 't. (connection is "up"and "active") 91.189.94.25:80  ubuntu-geoip-p is a static situation.
a time-wait is also possible with geo-ip.
i am not a big fan of geo-ip by the way. You could remove it, but you get rid of the data/time server as well.
geo-ip is rather new on ubuntu.(12.04)

whoopsie can be removed

disable NTP phoning home at every boot also, via: ```
sudo gedit /etc/default/ntpdate
```  insert a new line: exit 0

good to see you monitoring your system via: sudo netstat -atulpen

---

### Post by maxclaus on 2012-09-05
Hi s1baker,

using 12.04 Precise (Gnome3 'fallback' mode only), i realized practically the same behaviour (see also [http://ubuntuforums.org/showthread.php?t=2000108&highlight=geoclue](http://ubuntuforums.org/showthread.php?t=2000108&highlight=geoclue)) which is caused by geoclue-master. For my setup the following worked:

- with a Linux live-cd as root the permissions of /usr/lib/geoclue/geoclue-master and /usr/lib/ubuntu-geoip/ubuntu-geoip-provider were changed to 644 => both none executable.

Result: 
- geoclue-master doesn't start again and doesn't contact Internet (verified for a few days with wireshark).
- date-time applet is still working and updating system date-time as long as you don't switch off automatic date-time update via the according setting in the applet. If you dislike only the contact with the Ubuntu npd server by ntpd, you may also change the server (see [http://ubuntuforums.org/showthread.php?t=2000108&highlight=geoclue](http://ubuntuforums.org/showthread.php?t=2000108&highlight=geoclue))

Same or similar procedure should work with Lubuntu (i'm not quite shure if you simply couldn't remove geoclue with synaptic without affecting your system: e.g. trying a Xubuntu live-cd, geoclue is not installed by default as it is in 12.04 Precise).

Other: i' can't state anything if the a.m. affects Unity or Gnome-Shell, as i don't use them.

Regards / maxclaus

---

