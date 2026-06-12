---
title: "apt-get install lighttpd#breaks other webserver remove/purge won't fix"
date: 2017-05-25
forum: Server Platforms
---

### Post by walterav on 2017-05-25
Like the title suggests, installing "lighttpd" webserver on a ubuntu mate 16.04 amd64 machine breaks a other libsoup based webserver which (occasionaly) has to run on port 8080. I'd like to have them both run side by side (different purpose), but this doesn't work although lighttpd runs on port 80 and libsoup webserver 8080. Removing or purging lighttpd packages from the machine still leaves this libsoup based webserver application broken/unusable?

The libsoup based webserver functions as a component for a remote trigger mechanism to start video playback in "dvpause" for use with "dvswitch" video mixer (both packages "dvpause/dvswitch" not in repo, see build instructions below). For debugging this broken behaviour only dvpause has to be build. Its video output will be redirected to /dev/null instead of the videomixer dvswitch to ease debugging.

```

#get packages for building dvswitch/dvpause
sudo apt-get install dvgrab ffmpeg cmake build-essential libboost-thread-dev libgtkmm-2.4-dev libavcodec-dev libavutil-dev libasound2-dev libxv-dev libjack-jackd2-dev liblo-dev git libgtk-3-dev libcairo2-dev libsoup2.4-dev
git clone -b httpserv https://github.com/Jeija/dvpause.git
cd dvpause

#alter Makefile line 7 so that $(FILES) is listed before $(LIBS)
nano Makefile

#line 7 must look like this
        $(CC) $(FILES) $(LIBS) $(CFLAGS) -Wall -g -rdynamic -o main

#keyboard CTRL + X and press Y to save changes

#build dvpause
make

#this will run dvpause and redirect stdout video to null(otherwise console will flood)
./main > /dev/null

#or run dvpause with actual video output (don't mind ffplay buffer delay)
./main | ffplay -

#select a video in the dvpause gui, choose sintel video its longer (it will open ffplay after you choose a video)

#open a webbrowser and go to this page it should trigger playing video(moving slider) in dvpause
http://127.0.0.1:8080/play

#if this works for you quite/exit dvpause, now break it by installing lighttpd and rebooting your machine
sudo apt-get install lighttpd

#reboot your machine

#open a webbrowser and go to this page, it should show lighttps status
http://127.0.0.1:80

#try starting dvpause again and try to trigger its play page on 8080 again and see that it is broken
./main > /dev/null
http://127.0.0.1:8080/play

#remove lighttpd
sudo apt-get remove lighttpd

#notice that dvpause is permanently broken
./main > /dev/null
http://127.0.0.1:8080/play


```

Tried this on two fresh installs of ubuntu mate 16.04 amd64 on different hardware and sadly dvpause stays broken after removing the package lighttpd.

Any idea's?

---

### Post by wildmanne39 on 2017-05-25
*Thread moved to **Server Platforms**.*

---

### Post by walterav on 2017-05-25
I wasn't sure if I should post this under network or developing but the default server part is indeed lighttpd.

---

