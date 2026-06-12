---
title: "Starting shorewall at boot"
date: 2004-12-12
forum: Server Platforms
---

### Post by sharingan on 2004-12-12
hi!

i've configured shorewall. it's working fine, but when booting Ubuntu, it spends a long time (a couple of minutes!!) waiting for shorewall to start.

this is the content of my */etc/default/shorewall*, which i think is correct, since i connect through PPP:

```
# prevent startup with default configuration
# set the below varible to 1 in order to allow shorewall to start
startup=1

# if your shorewall's configuration need to detect the ip address of a ppp
# interface you must list such interface in "wait_interface" to get shorewall to
# wait until the interface is configured otherwise the script will fail because
# it won't be able to detect the address.
#
# Example:
#    wait_interface="ppp0"
# or
#    wait_interface="ppp0 ppp1"
# or, if you have defined  in /etc/shorewall/params
#    wait_interface=
wait_interface="ppp0"
# EOF

```

could it be a runlevels issues? i mean, that shorewall starts before ppp?
i don't understand yet the debian runlevels (i come from gentoo, and it looked easier there)

executing sysv-rc-conf:

[list]
[*]ppp service is running in runlevels 2, 3, 4 and 5
[*]shorewall in runlenvel **S**
[/list] 

this doesn't make fully sense for me...

i would like to speed up the boot time of my computer.

any tip or help is welcome!

thnx!!

---

### Post by wallijonn on 2005-01-05
What did the logs in /var/log show?

---

### Post by LB06 on 2005-01-05
How did you tell Ubuntu to start shorewall @ boottime? By symlinking /etc/init.d/shorewall to /etc/rcX.d/? (Or is this done automatically?)

---

### Post by sharingan on 2005-01-06
hi and sorry for my late reply, but i had a problem with my hard disk and had to reinstall ubuntu again :(
therefore, right now i don't have any log to provide

what i can say is that the installation was done automatically. i didn't have to take care of any of the symlinks for the start up.

---

### Post by nocturn on 2005-01-06
[QUOTE=sharingan]hi and sorry for my late reply, but i had a problem with my hard disk and had to reinstall ubuntu again :(
therefore, right now i don't have any log to provide

what i can say is that the installation was done automatically. i didn't have to take care of any of the symlinks for the start up.[/QUOTE]

Hmm

I think this might be the problem:
shorewall in runlenvel S

That is Single user if I am not mistaken...

Yeah, Gentoo had a great way of handling this (using depends).  I wish the other distro's would adopt this.

---

### Post by sharingan on 2005-01-06
[QUOTE=nocturn]Yeah, Gentoo had a great way of handling this (using depends).  I wish the other distro's would adopt this.[/QUOTE]
i also like Gentoo. i've been using it for a year in my laptop and at work, but compiling big stuff (like kde) was too much heat for my CPU, and keeping the system up-to-date was really time consuming: i was spending most of my time *emerging* and compiling the kernel than doing other things. that's why i have changed to Ubuntu.

[QUOTE=nocturn]shorewall in runlenvel S

That is Single user if I am not mistaken...[/QUOTE]
i have little idea about debian runlevels... it was easier for me in gentoo  ;)

---

