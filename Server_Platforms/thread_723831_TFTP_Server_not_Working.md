---
title: "TFTP Server not Working"
date: 2008-03-13
forum: Server Platforms
---

### Post by NateMan on 2008-03-13
I am attempting to setup a pxe boot server on ubuntu 7.10, and I'm having a little trouble getting my TFTP server up and running. I'm using tftpd-hpa and I have the netboot folder for ubuntu 7.10 in my tftp directory. I can not get the tftp to download even on the local machine, so I know the tftp is not working. When I attempt to network boot my computer, it sees my dhcp server for netboot and sees the correct gateway for the web, however it fails at tftp boot, timing out. I have the deamon for tftp set to turn on in the .conf file, so I think this is working properly. Any ideas on what to try to get this working? I'm not sure what the permissions have to be set to allow a computer to boot from it, but I've read that the permissions are very sensitive and finicky.

---

### Post by HermanAB on 2008-03-13
Tftp is extremely finicky about directories and file permissions.  I think all files should be read only otherwise tftp will refuse to do anything - as you have found.  

The reason is that tftp has zarro authentication and therefore the only security measure is the file permissions.  Read the man page for details.

Cheers,

Herman

---

### Post by NateMan on 2008-03-13
I'm currently looking at it and the man, but here's my file permissions for my tftp folder if you want to take a look:

root@oden:~# ls -la /var/lib/tftpboot
total 26976
drwxr-xr-x  5 root root    4096 2008-03-13 21:01 .
drwxr-xr-x 34 root root    4096 2008-03-13 18:58 ..
drwxr-xr-x  4 root root    4096 2007-10-15 18:21 386
-rw-r--r--  1 root root 9018633 2007-10-15 17:21 boot.img.gz
-rw-r--r--  1 root root 9512960 2007-10-15 17:21 mini.iso
-rw-r--r--  1 root root 9002347 2007-10-15 17:21 netboot.tar.gz
-rw-r--r--  1 root root   13552 2007-11-29 15:05 pxelinux.0
drwxr-xr-x  2 root root    4096 2008-03-13 21:10 pxelinux.cfg
drwxr-xr-x  3 root root    4096 2007-10-15 18:21 ubuntu-installer

Thanks for the help.

---

### Post by NateMan on 2008-03-14
I tried adding -p to the config file for tftp, to make it not look for permissions, but was unable to get that to work, although the config was valid.

---

### Post by NateMan on 2008-03-14
I'm sure that the file permissions are set correctly, but I'm now thinking that the problem is in directory selection. Here's the config file for tftpd-hpa:

#Defaults for tftpd-hpa
RUN_DAEMON="yes"
OPTIONS="-l -s /var/lib/tftpboot"

and /var/lib/tftpboot is where my files are located. I can also get to the tftp prompt on the server using the local address, however it too times out.

---

### Post by HermanAB on 2008-03-14
Hmm, interesting.

All I know is that every time I need a tftp server I lose a bunch of hair, but it eventually works and I can never really tell exactly why it didn't work the first time...

So, keep banging away at it - you will eventually get it to go, but you may need some more coffee and doughnuts.

Cheers,

Herman

---

