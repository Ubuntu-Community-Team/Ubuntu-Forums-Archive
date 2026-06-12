---
title: "Alert from Tiger ..install.cmd suspicious file, Am I hack?"
date: 2009-01-31
forum: Security
---

### Post by argh2xxx on 2009-01-31
Hello all,

Go soft on me as I'm still new at using Linux.  Also I rarely post any question on Ubuntu's forum, and so if I do post, this means I really need help due to no other medium that could help me solve the problem that is related to Ubuntu.

I heard about Tiger, and so I use synaptic to install Tiger.  After install Tiger, I did a check by using $linux sudo tiger -H.  I use a browser to open up the tiger report's html page, and saw couple Alerts that I feel very scary.  It's about suspicious file.  I hope you guy can tip me or steer me in the right direction on this suspicious file that has populated in many directories of my Ubuntu 8.10.

# Part of tiger's report.

# Checking unusual file names...

# ALERT [fsys005a]Unusual filename `..install.cmd' found:

-rw-r--r-- 1 root root 680 Jan 29 16:42 /usr/include/asm-generic/..install.cmd

# ALERT [fsys005a]Unusual filename `..install.cmd' found:

-rw-r--r-- 1 root root 1023 Jan 29 16:42 /usr/include/asm/..install.cmd

# ALERT [fsys005a]Unusual filename `..install.cmd' found:

-rw-r--r-- 1 root root 3917 Jan 29 16:42 /usr/include/linux/..install.cmd

# ALERT [fsys005a]Unusual filename `..install.cmd' found:

-rw-r--r-- 1 root root 629 Jan 29 16:42 /usr/include/linux/byteorder/..install.cmd

# ALERT [fsys005a]Unusual filename `..install.cmd' found:

-rw-r--r-- 1 root root 577 Jan 29 16:42 /usr/include/linux/can/..install.cmd

# ALERT [fsys005a]Unusual filename `..install.cmd' found:

-rw-r--r-- 1 root root 617 Jan 29 16:42 /usr/include/linux/dvb/..install.cmd

# ALERT [fsys005a]Unusual filename `..install.cmd' found:

-rw-r--r-- 1 root root 571 Jan 29 16:42 /usr/include/linux/hdlc/..install.cmd

# ALERT [fsys005a]Unusual filename `..install.cmd' found:

-rw-r--r-- 1 root root 573 Jan 29 16:42 /usr/include/linux/isdn/..install.cmd

# ALERT [fsys005a]Unusual filename `..install.cmd' found:

-rw-r--r-- 1 root root 1265 Jan 29 16:42 /usr/include/linux/netfilter/..install.cmd

# ALERT [fsys005a]Unusual filename `..install.cmd' found:

-rw-r--r-- 1 root root 644 Jan 29 16:42 /usr/include/linux/netfilter_arp/..install.cmd

# ALERT [fsys005a]Unusual filename `..install.cmd' found:

-rw-r--r-- 1 root root 823 Jan 29 16:42 /usr/include/linux/netfilter_bridge/..install.cmd

# ALERT [fsys005a]Unusual filename `..install.cmd' found:

-rw-r--r-- 1 root root 1195 Jan 29 16:42 /usr/include/linux/netfilter_ipv4/..install.cmd

# ALERT [fsys005a]Unusual filename `..install.cmd' found:

-rw-r--r-- 1 root root 885 Jan 29 16:42 /usr/include/linux/netfilter_ipv6/..install.cmd

# ALERT [fsys005a]Unusual filename `..install.cmd' found:

-rw-r--r-- 1 root root 614 Jan 29 16:42 /usr/include/linux/nfsd/..install.cmd

# ALERT [fsys005a]Unusual filename `..install.cmd' found:

-rw-r--r-- 1 root root 577 Jan 29 16:42 /usr/include/linux/raid/..install.cmd

# ALERT [fsys005a]Unusual filename `..install.cmd' found:

-rw-r--r-- 1 root root 566 Jan 29 16:42 /usr/include/linux/spi/..install.cmd

# ALERT [fsys005a]Unusual filename `..install.cmd' found:

-rw-r--r-- 1 root root 583 Jan 29 16:42 /usr/include/linux/sunrpc/..install.cmd

# ALERT [fsys005a]Unusual filename `..install.cmd' found:

-rw-r--r-- 1 root root 626 Jan 29 16:42 /usr/include/linux/tc_act/..install.cmd

# ALERT [fsys005a]Unusual filename `..install.cmd' found:

-rw-r--r-- 1 root root 645 Jan 29 16:42 /usr/include/linux/tc_ematch/..install.cmd

# ALERT [fsys005a]Unusual filename `..install.cmd' found:

-rw-r--r-- 1 root root 607 Jan 29 16:42 /usr/include/linux/usb/..install.cmd

Anyone know what is this ..install.cmd file?  It's in many directories.  Thanks...  Is this file populated on brand new fresh install Ubuntu 8.10?  Anyone has freshly installed Ubuntu 8.10, can you try Tiger and see if the same Alert will appear?  Thanks...

---

### Post by cariboo on 2009-02-01
I have the same files on my system, they are nothing to worry about.

JIm

---

### Post by argh2xxx on 2009-02-01
Thanks cariboo907!

At least one person respond so far.  Though I still don't know what this file does... kinda wanna know what it is to be sure.  Anyone know?

---

### Post by ugm6hr on 2009-02-01
> **argh2xxx said:**
> Anyone know?

Don't know, but it appears in the contents of various -dev packages:
e.g. [http://packages.ubuntu.com/hu/intrepid-updates/amd64/linux-libc-dev/filelist](http://packages.ubuntu.com/hu/intrepid-updates/amd64/linux-libc-dev/filelist)

---

### Post by sanemanmad on 2009-02-01
Hi argh2xxx,

You should'nt have to worry, in fact those files are necessary for your kernel. Those are simply a copy of the Library to build the kernel headers.

I was able to get this information by using our favorite search engine giant GOOGLE :P

---

### Post by argh2xxx on 2009-02-02
Thanks guy for your helpful info.

---

### Post by cjacobsen on 2009-02-02
You don't need to worry to much about alerts, warnings however you need to take seriously!

---

