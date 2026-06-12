---
title: "Cookbook - ubuntu desktop install on Ultra 10"
date: 2006-09-13
forum: Sun Sparc Users
---

### Post by kmantronix on 2006-09-13
Hello,

I ve been working with solaris for 8 years, i don't know a lot about linux and i wanted to install ubuntu sparc on my old Ultra 10

It has been quite a long run, but i succeeded in installing ubuntu server + gnome desktop environment

- download and burn the .iso install ubuntu server CD
  
- remove any additionnal Graphic card :  I first tried to install ubuntu linux with a PGX 32 card installed and the boot install got stuck desperately with the "booting linux ..." message

- update OBP to the latest level, which is 3.31

- always do a cold start (poweroff/poweron) before booting cdrom. If you don't you will fall into the well known SILO problem :

Allocated 8 Megs of memory at 0x40000000 for kernal
Loaded kernal version 2.6.15
loading initial ramdisk (4821666 bytesat 0x40000000 phys, 0x40C00000 virt)...
Illegal instruction
{0} ok 

- boot cdrom - answer to the installer questions 


optionnal :
- when installed add ssh server package with

# sudo apt-get install openssh-server

this package is available on the install CD

You can now connect remotetely with ssh on your ubuntu U10 


- Install ubuntu-desktop package to get the whole gnome graphical environment

As i was behind a proxy, I add to set an http proxy with  

# declare -x http_proxy=http://webcache.xx.xx.xx:8080

# sudo apt-get install ubuntu-desktop

Once downloaded and configured, reboot.

# reboot

that s all and it works ! :)

---

### Post by bhuvan72 on 2006-10-25
Hello,

I got the server installed successfully on a Untra 5 system (256M, IDE 4GB drive). No problems with graphics cards.

There was one error displayed... that it could not get latest security updates and pointed out a file name /etc/opt/sources.list. When I checked later, that file was not there...

Another issue is...

I am behind a firewall and so I set the proxy. I was able to run nslookup and get IP addresses of sites.

But I am not able to get the desktop using the apt-get install ubuntu-desktop command.

Is there a way of getting it seperately and installing.

As you had said.. the SSH package was in the CD. Is there a way to get the desktop in the CD and install it?

Any help would be appreciated..

Thanks,
Bhuvan.

---

### Post by H0bb3z on 2006-10-26
You might be behind a firewall, but perhaps not a web proxy.  The apt-get command uses web protocols (http) to get package information and updates, so unless you have a web proxy (like squid, or similar) running on your firewall, you don't need to specify a proxy server.  Your firewall translates your internal private address to a public one (usually the public IP address on your firewall) so to other destinations on the Internet, there is a public address to reply to (the firewall) - the firewall keeps track of the session and hands the response back to your workstation on the internal network.

set the proxy to nothing:
```
# declare -x http_proxy=  <hit enter here to leave the setting blank>
#
```To explain why nslookup works -- that isn't using web protocols to lookup IP addresses -- it uses DNS (usually udp 53), so a web proxy would not ever be called to help proxy traffic to the Internet for this function.

---

### Post by bhuvan72 on 2006-10-27
Hi,

When I try to install using apt-get I get the foll. message.
BW, I have just installed the 6.10 sparc server version...

The error is as below.

Reading package lists... done
Building dependency tree
Reading state information ... done
E: Couldn't find package ubuntu-desktop

I have even tried it with the http_proxy unset.

If you need any more info, please let me know.
If I have a sparc desktop CD, how can I install the desktop package from the cdrom...

Any help is greatly appreciated.

Thanks,
Bhuvan.

---

### Post by jfinn on 2006-11-01
did you try "apt-get update" first?  I had to do that first to download everything...then try installing the desktop.

---

### Post by mikeduffy13 on 2008-03-10
Thanks Jfinn, your post solved my issue!!

---

### Post by themish on 2008-03-13
Hi, I just put ubuntu7 on my ultrasparc.  I get responses when I ping google.com that are within reason, but aptitude cant connect to its servers at all.  I uncommented every repository in sources.list but it 404's on all of them.  I can set a static IP in this university network and it still does nothing.  The machine can ssh to other computers in the network.  Would really like ubuntu-desktop to roll on this machine, thanks!

---

