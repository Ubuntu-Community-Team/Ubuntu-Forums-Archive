---
title: "RFC highly available multiple purpose small business server setup"
date: 2007-09-02
forum: Server Platforms
---

### Post by LanDan on 2007-09-02
Dear all,

Have been playing with Linux for a few years now and i found it to be a great and reliable tool for my needs, but i suppose as for most people my needs seem to be expanding all the time as time goes by.

At the time i use Debian as my Distro of choice running desktops and a single Xen based mail/web server and samba file server, but i would like to do some more and i'm planning to use Ubuntu 8.04 since i will also need LTSP in the mix.

Offcourse i can keep my current setup and load ubuntu as a DomO and add the mail + ltsp + etc.. domU's

needless to say is that this set up will be for an office environment otherwise it would not be worth the fuss.....

BUT!!!!!! 
I would like to offer these services on geographical separated locations and my concern is HARDWARE FAILURE.
Clustering would be nice (have no experience with this), but how would i do this in a Xen environment????

my idea is as follows and i think it should be possible to work this out for the next LTS release.

1) have multiple virtual servers so you don't need a new box for each service
2) have a highly available cluster so there is less worry of down time due to hardware failure and you can use cheaper hardware.

i think two cheap pc's with some external storage could provide a very nice affordable set up for small company's to have numerous services running with very little down time.

As the title says this is a "Request For Comments" so i would like to hear the experience of people who did a similar thing and if people with the same need would like to help out on this we could make a nice specification for the next LTS release

highly appreciated

randall shift 2 songshu.org

---

