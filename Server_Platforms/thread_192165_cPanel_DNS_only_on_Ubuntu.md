---
title: "cPanel DNS only on Ubuntu"
date: 2006-06-08
forum: Server Platforms
---

### Post by root@localhost on 2006-06-08
I decided to go with an Ubuntu server (base system only) installation to set up a backup nameserver. However, when I download the cPanel DNS Only installer, it won't run. It gives me an error that it can't find a perl module or something. It says "Can't locate Sys/Hostname.pm in @INC." Where would I go about getting this perl module and how do I install it? 

Also, how do I change network settings from the command line? The server I'm working with is limited on hard drive space, so I didn't put a GUI on it. I just need to set up some network settings when it gets to its final home, such as the IP address, gateway, and DNS servers. I've never done that from the command line before, and would appreciate some pointers. 

Finally, I did a search here before I posted, and I didn't find a lot of people who were using Ubuntu with a cPanel server. Has anyone else ever tried this before? 

Thanks!

---

### Post by cyracks on 2006-06-08
[quote=root@localhost]
Also, how do I change network settings from the command line? The server I'm working with is limited on hard drive space, so I didn't put a GUI on it. I just need to set up some network settings when it gets to its final home, such as the IP address, gateway, and DNS servers. I've never done that from the command line before, and would appreciate some pointers. 
[/quote] 
To change network settings use **ifconfig** command (e.g. ifconfig eth0 192.168.0.1).

To make permanent changes edit file **/etc/network/interfaces.**

---

### Post by root@localhost on 2006-06-09
Ok, thanks for pointing out that file. I'll be able to set everything up without any issues. I'm not sure about Ubuntu, but do I need to set up the nameservers in /etc/resolv.conf? I've had to do that with CentOS before.

Also, how do I download and install a perl module, or even upgrade perl to the 5.8.8 version? I've tried sudo apt-get upgrade perl but that didn't upgrade perl, it just downloaded a bunch of other packages. I might be taking the wrong approach, but I found the module that I need, and I can't figure out where I can download it, or any other module for that matter. [Here]("http://search.cpan.org/~nwclark/perl-5.8.8/ext/Sys/Hostname/Hostname.pm") is a link to the module that I found by google searching, but I can't seem to find a download link, aside from the new version of perl.

---

