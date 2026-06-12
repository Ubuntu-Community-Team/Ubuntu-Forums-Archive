---
title: "bigbluebutton and ubuntu"
date: 2020-04-02
forum: Server Platforms
---

### Post by altrian on 2020-04-02
Good morning everyone,

I'm trying to install bigbluebutton on my server, but my server runs on ubuntu 18.04 and the latest version of bbb only runs on ubuntu 16.04. So I got the idea to run it in a container in 16.04 and make it listen on a port.

I try to create a bluid to have an image with bbb installed on it, except that the procedure to install bbb on the official website doesn't work, the yq package being untraceable:

- When I run the command : **add-apt-repository ppa:rmescandon/yq -y**
He replies: **'ascii' codec can't decode byte 0xc3 in position 108: ordinal not in range(128)**

While searching the net I found a solution to this problem. I use the command: **apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6657DBE0CC86BB64** before the previous one then I update all this and the installation is done.

The problem is that when I try to build the image, it stops at the above problem and crashes with this message :
[B]'ascii' codec can't decode byte 0xc3 in position 108: ordinal not in range(128)
The command '/bin/sh -c add-apt-repository ppa:rmescandon/yq -y' returned a non-zero code: 1[/B]

The question is if it's possible to force a build (because when I put myself in a container just with ubuntu:xenial and do the installations step by step myself, it works).

Or does anyone know another way to install the yq package? (PS: with snap it doesn't work either).

I hope I've been clear enough, thank you.

---

### Post by TheFu on 2020-04-03
Years ago, I looked at BBB and decided it was much to complex for the need we had.  

Would you consider other F/LOSS tools? Are there specific things that BBB does you require?  

For example, Jitsi and Jitsi-meet took about 10 minutes to setup.  I've been running a nextcloud-talk system for the family. Both of those projects are active and widely used today.  They aren't for just anyone and both have liabilities, but the do work really well for many situations.

---

