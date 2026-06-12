---
title: "Ubuntu Server does not recognise any type of internet...???"
date: 2017-02-08
forum: Server Platforms
---

### Post by thatonegamer999 on 2017-02-08
So, hi there.

I was bringing life into my old hardware by using it as a minecraft server/storage server for my friends and I.
So, long story short, after FINALLY getting ubuntu server onto a usb, it was time to rock.

Then I ran into my first issue.
While going through the installation process, It claimed it was connected to my WiFi, and it was, because it downloaded some programs like an ssh server.
Then after installation and a reboot, I typed
```
ping google.com
```
and I got this:
```
root@mcserv12:~$ ping google.com
error: unknown host google.com
 
```
I have gone through at least five hours of troubleshooting, even plugging in a wired ethernet cable, and lo and behold, after getting it to recognise the cable, and start using it:
```
root@mcserv12:~$ ping google.com
error: unknown host google.com

```

Can someone help me?
](*,)

---

### Post by wildmanne39 on 2017-02-08
Click on the wireless script in my signature and follow the directions for running it and posting the file it creates here using code tags.

It is best to have a server plugged in to an ethernet connection.

---

### Post by chili555 on 2017-02-08
It is sad and happy at the same time that it is quite easy to download and install the server edition. However, once you've done so, the server edition assumes that since you know what a server is, know why you'd need a server of your own and have it running, that you just automagically know about setting up networking.

But most of you don't!

A pretty smart guy wrote a howto about wireless on a server. Try it and tell us if it gets you going.

[http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal/464552#464552](http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal/464552#464552)

Be sure to check your wireless interface:```
ifconfig
```Yours may not be wlan0. It may be something different like wlo1 or wlp3s0 or some such.

---

