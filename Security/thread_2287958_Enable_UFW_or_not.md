---
title: "Enable UFW or not?"
date: 2015-07-23
forum: Security
---

### Post by peter1897 on 2015-07-23
What is the best solution for Ubuntu server, to enable UFW or not, and just use iptables with the iptables-persistent package installed with which to save the rules?

---

### Post by Habitual on 2015-07-23
UFW provides a "friendly" interface to manage the firewall rules.
If you are comfortable with c-line, iptables + persistent may very well be enough.

---

### Post by peter1897 on 2015-07-24
For web server, for incoming connections, is it ok to allow only access to port 22 and port 80?
Also, can you suggest any backup variant to connect to the server if i lost ssh access in case, for example, missconfiguring the sshd_config file?

---

### Post by Lars Noodén on 2015-07-24
> **peter1897 said:**
> For web server, for incoming connections, is it ok to allow only access to port 22 and port 80?
Also, can you suggest any backup variant to connect to the server if i lost ssh access in case, for example, missconfiguring the sshd_config file?

About the first question, you are likely to outgrow UFW if you are doing a lot with iptables beyond basics.  

For a web server's incoming connections, you probably want to allow TCP in on 22 (ssh), 80 (http) and 443 (https) plus ICMP Echo Request (for ping).  

About backup connections, ideally if your server has a serial console connected to another machine, you can ssh to that other machine and do your work via it.  If not, then you have to be extra careful.  

If you use [iptables-apply](http://manpages.ubuntu.com/manpages/trusty/en/man8/iptables-apply.8.html) to test your changes, there is less chance of getting locked out.  There is also a way using [at](http://manpages.ubuntu.com/manpages/trusty/en/man1/at.1.html), too.  

If you're working with sshd, then you can create a second config file that accepts connections on an unusual port and manually launch an extra sshd and connect to it.  But even then do your experimentation in a copy of your main sshd_config and don't move it over to the real sshd_config until you are sure it works.  That way the machine can always has a working sshd_config and safely reboot and come back up and so on.

---

### Post by peter1897 on 2015-07-24
For the incoming connections is these the right commands for UFW rules:
```
sudo ufw allow 80/tcp
sudo ufw allow 22/tcp
sudo ufw allow 443/tcp
```

I am not sure how to set the rule for ICMP Echo Request.

---

### Post by Lars Noodén on 2015-07-24
Or **sudo ufw allow in 22/tcp** and so on.  If you are using UFW then I think that does ping (ICMP Echo Request) by default.  You'll have to check from a second machine to be sure.  If you are going to use plain iptables, then you'd have to add in something like this, more or less:

```

   iptables -A INPUT -p icmp --icmp-type echo-request \
        -m limit --limit 1/s -i eth0 -j ACCEPT

```

The limit part is optional.

---

### Post by peter1897 on 2015-07-24
Thanks, i think i will use UFW, it looks more easy to configure. 
Is the default Ubuntu firewall iptables/ufw provides high level of security or i should look for other firewall if i want to achieve higher level of security?

---

### Post by Lars Noodén on 2015-07-24
UFW has fairly sane defaults.  When it is enabled, it blocks all TCP and UDP traffic and any exceptions have to be enabled explicitly.  You can see the configuration in two ways:

```

sudo ufw status verbose
sudo iptables-save | less

```

Be sure to read through the manual page for UFW to see the options.  

To see more of what working with iptables directly could do instead check [iptables-extensions](http://manpages.ubuntu.com/manpages/trusty/en/man8/iptables-extensions.8.html) in addition to the regular manual page for iptables.

---

### Post by peter1897 on 2015-07-24
How to setup ssl server on Ubuntu? I installed openssl with the command:
```
sudo apt-get install openssl
```
But nothing is listening on port 443:
```
max@ubuntu:~$ sudo netstat -ntlp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      7711/sshd
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1019/mysqld
tcp6       0      0 :::22                   :::*                    LISTEN      7711/sshd
tcp6       0      0 :::80                   :::*                    LISTEN      2480/apache2
```

Also if i try to connect to apache with https i get: **The connection has timed out**

---

### Post by Lars Noodén on 2015-07-24
If you're thinking of TLS/SSL for Apache2, it is mostly set up. You just need to buy or create your own certificates and activate (or copy) the existing vhost.  

[https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04)

[https://help.ubuntu.com/lts/serverguide/certificates-and-security.html](https://help.ubuntu.com/lts/serverguide/certificates-and-security.html)
[https://help.ubuntu.com/lts/serverguide/httpd.html#https-configuration](https://help.ubuntu.com/lts/serverguide/httpd.html#https-configuration)

---

### Post by peter1897 on 2015-07-24
If i setup ssl certificate does that mean the users who try to visit my site will get the message "this connection is untrusted"? Can this message be disabled?

---

### Post by Lars Noodén on 2015-07-24
They will get that message if their browser does not recognize the certificate.  One way around it is to pay for one but there are some free options out there too, but I'm not up on what all the choices are.

---

