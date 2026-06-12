---
title: "Ubuntu Server 7.10 Vulnerabilities"
date: 2008-03-24
forum: Security Discussions
---

### Post by cueball516 on 2008-03-24
Hi All,
I am sure this may be a somewhat of a taboo topic, but I am looking for any/all vulnerabilities of the standard Ubuntu 7.10 distribution. 

I am looking for this because I am taking a Cyber Security course at the University of Maine.  This course requires that we secure our own Linux computer and attack other classmates. 

I choose to use Ubuntu Server 7.10, because I have been comfortable with Ubuntu Desktop, so I thought this was a good choice.  But it also seems that most of my other classmates are using Ubuntu Server. 

We are required to have the following services:
Web server - almost everyone is using the default apache2 package
MTA - many different configurations
Finger - many different versions
Guest Account - 
SSH/SCP - Everyone is use the standard OpenSSH package

So, what I am looking for is of course tips to secure my own system, and weaken others.

Any direction such as sites with vulnerabilities or known issues would be great.  Thanks for you help.

---

### Post by HermanAB on 2008-03-24
This will ensure perfect network security:
# sudo iptables -I INPUT -i eth0 -j DROP

---

### Post by thewanderer on 2008-03-24
sudo apt-get update
sudo apt-get upgrade

Don't forget to update your packages. The recent kernel vmsplice exploit would be a concern if anyone had access via a user account and you were not updated.

---

### Post by tubezninja on 2008-03-24
The list of KNOWN vulnerabilities in all supported versions of ubuntu can be found here:

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

However, ubuntu developers pretty much patch these up rather quickly.

Doing a 'sudo apt-get update" and 'sudo apt-get upgrade' as listed above is the best way to get these known issues patched up.  If your classmates don't do this, and just install the CD image, they are likely open.

Also, a good way to better secure OpenSSH on ubuntu is to install [DenyHosts]("http://denyhosts.sourceforge.net/").  A pacakge for it exsits in the repositories.  You can install it by issuing this command:

```
sudo apt-get install denyhosts
```

Then, configure by editing /etc/denyhosts.conf, and your classmates will very quickly lock themselves out if they try a dictionary attack. :)

---

### Post by Dr Small on 2008-03-24
Change ports for SSH and use strong passwords.

---

### Post by cueball516 on 2008-03-24
Hi All,

Thank you very much for your responses.  

I guess I forgot to mention that we are required to a guest account on our system, with a generic user name and password.  This makes exploits like vmsplice very realistic.  In fact I have been able to use it on one of the machines in our Cyber War.

I also forgot to mention that our professor has locked down our network for the Cyber War attack.  It is a private network with only ssh access. This makes any apt-get upgrades very complicated. 

My system is actually vulnerable to the vmsplice attack, but since I cannot do apt-get upgrade easily I don't have a full solution.  I do feel comfortable that the guest account can't run it, because I have locked them in jail, with a restricted shell, and disabled all execution on their home partition.

Denyhost - this is an awesome python script.  I have been using it when our machines were on the internet and it blocked tons of attacks.

Thanks again for all of your responses.

---

### Post by Dr Small on 2008-03-24
Pray tell me what "restricted shell" you are using for your guest account?
If it is rbash, it can be broken out of within 2 commands.

Dr Small

---

### Post by FakeOutdoorsman on 2008-03-24
Here is a mess of links. Secure access to your machine:
[Using iptables to rate-limit incoming connections]("http://www.debian-administration.org/articles/187")
[IPTables HOWTO]("http://wiki.centos.org/HowTos/Network/IPTables")
[Keeping SSH access secure]("http://www.debian-administration.org/articles/87")
[Securing OpenSSH]("http://wiki.centos.org/HowTos/Network/SecuringSSH#head-9c5717fe7f9bb26332c9d67571200f8c1e4324bc")

Secure Apache:
[20 ways to Secure your Apache Configuration]("http://www.petefreitag.com/item/505.cfm")
[Securing LAMP]("http://www.infiltrated.net/docs/modsecips.html")

Others:
[Towards a moderately paranoid Debian laptop setup]("http://www.hermann-uwe.de/blog/towards-a-moderately-paranoid-debian-laptop-setup--part-1-base-system")
You might also look into [Bastille-Linux]("http://bastille-linux.sourceforge.net/"), SELinux, and [modsecurity]("http://www.modsecurity.org/") but I have no experience with these.

honeyd:
Lastly, you can setup a honeypot to confuse your classmates.  I recommend [honeyd]("http://www.honeyd.org/"):
[honeyd]("http://www.youtube.com/watch?v=kRIZuS5AEVU") [YouTube]
[Open Source Honeypots: Learning with Honeyd]("http://www.securityfocus.com/infocus/1659")

Usage example:
```
sudo farpd 192.168.1.0/24
sudo honeyd -p /etc/honeypot/nmap.prints -f /etc/honeypot/config.fakeubuntu -l ~/honeyd/honeyd.log 192.168.1.0/24 -d
```

Example configuration for /etc/honeypot/config.fakeubuntu:
```
create linux
set linux personality "Linux 2.4.16 - 2.4.18"
set linux default tcp action reset
set linux default udp action reset
add linux tcp port 22 "scripts/unix/linux/suse8.0/ssh.sh"
add linux tcp port 79 "scripts/unix/linux/suse8.0/fingerd.sh"
add linux tcp port 80 "scripts/unix/linux/suse8.0/apache.sh"
set linux uptime 3284460
```

You should add a new "personality" and edit the scripts to better match Ubuntu.

---

### Post by netlogic on 2008-03-24
If you can use any distro, why not use a live-cd? How are they going to write to your drive? They are going to burn you  a new cd? Check out Knoppix STD. It has bunch of vulnerabilities scanning tools.

[http://www.knoppix-std.org/](http://www.knoppix-std.org/)

---

### Post by Nate53085 on 2008-04-22
Hey Jason,

Good luck with COS498 :)

---

### Post by Chayak on 2008-04-24
If you want to do something and have a bit of fun with everyone then write a script that looks like a normal shell but responds with an error to everything they try to type then set the script as the enviornment of the user so when they log in they're actually in the script instead of a real shell.  It drives people nuts and they'll keep telling you your system is broke.

---

