---
title: "SSH Problem -- hash mismatch debug1: ssh_rsa_verify: signature incorrect"
date: 2008-06-01
forum: Server Platforms
---

### Post by downforce on 2008-06-01
I seem to be having massive issues with 8.04-server and SSH.

I am installing it on a Gigabyte GA-P35-DS3 w/ 2x36GB SCSI drives in RAID0 on a 2100S Adaptec card.

I do an install w/ openssh-server ticked. When I try and SSH in I get the following from ssh user@ip -vvv:

```

hash mismatch
RSA_public_decrypt failed: error:0407006A:rsa routines:RSA_padding_check_PKCS1_type_1:block type is not 01
debug1: ssh_rsa_verify: signature incorrect

```

I follow up by doing a apt-get update & upgrade and same problem.

I have tried SSH'ing from a 8.04 sever install, upgraded from old Ubuntu versions and also a clean 8.04 desktop install. I can ssh in both these machines no problem from all 3 machines.

Just the server one, I can't connect to under any circumstances.

I've googled for 20-odd pages in and found nothing useful.

Anyone seen this and can help?
Cheers.

---

### Post by Prospero2006 on 2008-06-01
Here's what I would do:

/etc/init.d/ssh stop

Then, I'd download it from source, compile, and try it that way.

Just a suggestion.

---

### Post by downforce on 2008-06-04
Thanks for the reply Prospero2006.

Well, I attempted a compile from source and still no joy but something weird did happen.

Went through the ./configure, make and when I did the sudo make install the system took forever to create the RSA key. I left it running 58min with 100% CPU usage on the ssh-keygen thread. I CTRL-C'ed and re-ran sudo make install, this time it picked up a fingerprint and started the DSA key. 

It was getting late so I left it running overnight, came back 8hrs last (almost exactly) and the ssh-keygen -t dsa <snipped of screen> CPU thread was still running without generating a DSA key. I tried the CTRL-C trick again and re-ran the 'make install' and left it again for 30min to generate the DSA before killing it.

So it hasn't finished installing as it can't get past the ssh-keygen. 

I'm completely lost where to go from here, any suggestions?

BTW, the process was (I use wajig over apt-get)
* /etc/init.d/ssh stop
* apt-get purge openssh-server
* rm'ed /etc/ssh/sshd_config, both RSA and DSA key files
* downloaded and ./configure, make, sudo make install.

I'm using the latest openssl-0.9.8g from Ubuntu hardy repos also.

---

### Post by windependence on 2008-06-04
Well you probably didn't need to do all this stuff. The problem is your keys in /root/.ssh/known_hosts needs to be deleted because you probably sshed in from a diffferent IP at one time and now the keys are different. Find it and clear it out, it won't hurt anything. There will be several keys in it most likely. You can delete them all.

-Tim

---

### Post by downforce on 2008-06-04
Yeah, sorry, didn't state that but removing the ~/.ssh/known_host and ~/.ssh/authorized_keys was the first thing I did.

---

