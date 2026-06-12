---
title: "How do you install and set TFTP  on Ubuntu 10.04 LTS server"
date: 2012-04-12
forum: Server Platforms
---

### Post by ducthuan90 on 2012-04-12
I have some ways to install TFTP on ubuntu 10.04 server but I do not choice some ways. So I ask to you help me to find a good way.
Thank you for helping.
I come to Viet Nam.So my english is not good.

---

### Post by oldos2er on 2012-04-12
Moved to Server Platforms.

---

### Post by jonobr on 2012-04-12
Hello


theres some common packages that need to be installed and some minor configuration required.

[This link has information ]("http://wiki.answers.com/Q/How_do_you_install_and_configure_tftpd_under_ubuntu") on setting up tftp on ubuntu


You will also need to create some files which you can do by using gedit

eg
```
/etc/xinetd.d/tftp
```

and copy/paste in the information
> service tftp
{
protocol = udp
port = 69
socket_type = dgram
wait = yes
user = nobody
server = /usr/sbin/in.tftpd
server_args = /home/tftpboot
disable = no
}

---

### Post by Jonathan L on 2012-04-12
Hi Ductjuan

Just some alternatives to the excellent advice of jonobr...

I have used tftp a lot on Ubuntu 10.04 server.  You have several choices of server.  The one which is simplest is the "HPA" version, made by H Peter Alvin.

You install with
 ```
sudo apt-get install tftpd-hpa
```You might also want a client program to test with
 ```
sudo apt-get install tftp-hpa
```The benefits of this particular TFTP server is that you don't have to edit any config files.  The files for tftp are kept in /var/lib/tftpboot

I've also used atftpd with good results.

The server in the package actually called "tftpd" is not as good, in particular it won't support PXE booting, if that's what you want it for.

I hope this helps.

Kind regards,
Jonathan.

---

### Post by jonobr on 2012-04-12
You know what,

now that you mention it, I have used hpa before in a production environment and was very happy with it when I used it.

I would ignore my advice and go with the most excellent advice of JonathanL

Cheers

jonobr

---

### Post by ducthuan90 on 2012-04-12
Thanks you for helping me.
I will try to install it with my ubuntu server.

---

### Post by ducthuan90 on 2012-04-13
i configured TFTP on Ubuntu server(used to command sudo apt-get install xinetd tftpd tftp). But i had one error in sending file to TFTP server. Error:"Access Violation"
I hope to receive help from you.

---

### Post by jonobr on 2012-04-13
Go with jonathanL's recommendation of 

```
sudo apt-get install tftpd-hpa
```

That should install fine

---

