---
title: "Webmin removal successful/Nmap claims Ports Open"
date: 2010-10-22
forum: Server Platforms
---

### Post by .35Whelen on 2010-10-22
To remove webmin: COMMAND:  /etc/webmin/uninstall.sh was successful.

To check the removal in used Nmap with the following code:
sudo nmap -sV -O -v -PN -T4 XXX.XX.XXX.XX this showed

PORT    STATE SERVICE     VERSION
22/tcp  open  ssh         OpenSSH 5.3p1 Debian 3ubuntu4 (protocol 2.0)
80/tcp  open  http        Apache httpd 2.2.14 ((Ubuntu))
139/tcp open  netbios-ssn Samba smbd 3.X (workgroup: WORKGROUP)
445/tcp open  netbios-ssn Samba smbd 3.X (workgroup: WORKGROUP)

I wanted a complete shut down of these services and my IP to show clean with ALL ports closed.

Throw me a bone please.
Cheers

---

### Post by paulsp on 2010-10-23
You would also need to remove these other services. Webmin is only a 'skin' that allows you to manage Apache, SSH, etc. It does not contain these programs. So something like:

```
apt-get remove apache2 sshd samba
```

Should remove these programs. Furthermore, please note that the best way to close off ports is using a firewall, not by simply not installing certain programs. Do you have a firewall installed? With ufw you can eaily shut down these ports even though the programs still exist on the server.

---

### Post by jaimerosario on 2012-04-20
Webmin uses only port 10000 with SSL:

**https**://webminhost:**10000**

It doesn't use Samba and/or Apache ports.

---

