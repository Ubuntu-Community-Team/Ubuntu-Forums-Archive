---
title: "ubuntu not  asking for sudo  password anymore"
date: 2011-09-16
forum: Security
---

### Post by linuxyogi on 2011-09-16
Hi,

I recently installed the dialer for my 3G USB modem. I am atm using it . 

But the problem is Ubuntu doesn't ask for sudo password anymore. 

I am not sure that the dialer has caused the issue. 

I am using [http://airtel.in/3Gmobile/index.htm](http://airtel.in/3Gmobile/index.htm)

I am really scared. Please reply.

---

### Post by linuxyogi on 2011-09-16
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults    env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
ALL ALL=(ALL) NOPASSWD:ALL

```

---

### Post by linuxyogi on 2011-09-16
I removed the line 

ALL ALL=(ALL) NOPASSWD:ALL

& everything is as usual now.

Got the idea from [http://maestric.com/doc/unix/ubuntu_sudo_without_password](http://maestric.com/doc/unix/ubuntu_sudo_without_password)

Kindly check the rest of the file, in case there are more unnecessary modifications.

---

### Post by haqking on 2011-09-16
> **linuxyogi said:**
> I removed the line 

ALL ALL=(ALL) NOPASSWD:ALL

& everything is as usual now.

Got the idea from [http://maestric.com/doc/unix/ubuntu_sudo_without_password](http://maestric.com/doc/unix/ubuntu_sudo_without_password)

Kindly check the rest of the file, in case there are more unnecessary modifications.


Looks fine.

See here for more info [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by linuxyogi on 2011-09-16
> **haqking said:**
> Looks fine.

See here for more info [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

Thanks for the link. As of now there is no sudo related issue that I know of. 

But I am curious about something. My friend also uses [Mobile broadband.]("http://www.tataphoton.com/")

I configured his connection myself. These are the steps that I followed 

> plug the usb modem 

> open network manager

>choose mobile broadband

>**The modem was visible in "create a connection for this mobile broadband device"**
 
> Then I had to choose the appropriate plan after which connection was established upon dialing.


But in my case the modem is not visible in network manager. I am dialing using the tool provided by Airtel. >>>>>[http://dl.dropbox.com/u/30630174/Screenshot-airtel.png](http://dl.dropbox.com/u/30630174/Screenshot-airtel.png)

Someone please tell me whats going on. Network Manager can't seem to detect the modem yet connection can be established.

I wanted to connect using the Network Manager. 

```
$ lsusb 
Bus 002 Device 004: ID 1d57:ac01  
Bus 002 Device 003: ID 1c4f:0002 SiGma Micro 
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 12d1:1436 Huawei Technologies Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

