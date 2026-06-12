---
title: "Can't connect to FTP server running vsftpd"
date: 2010-05-29
forum: Server Platforms
---

### Post by HittingSmoke on 2010-05-29
I just made a Ubuntu Server install in a virtual machine and am having trouble setting up FTP to transfer files.

I've installed LAMP and vsftp. The web server works great, but FTP gives a connection refused error locally and remotely from the host machine. '*Connection attempt failed with "ECONNREFUSED - Connection refused by server".*'

*nmap localhost* doesn't list FTP as open even though I have vsftpd set to listen. I've tried restarting vsftpd with no luck.

Any ideas?

---

### Post by markbahnman on 2010-05-29
I have much the [same problem]("http://ubuntuforums.org/showthread.php?t=1496291"). I tried having apache2 listen to the port, changing the listening port, playing with iptables, playing with the .conf file and all I get is that connection refused message or just a hanging connection.

---

### Post by Vegan on 2010-05-29
You need to open port 21 for FTP.

---

### Post by HittingSmoke on 2010-05-29
> **Vegan said:**
> You need to open port 21 for FTP.

How would I go about doing that?

I tried opening port 21 in iptables with a command that was something like:

```
iptables -A INPUT -p tcp -s dport 21
```
(not this exact command, but it was similar. I don't remember what it was exactly)

---

### Post by HermanAB on 2010-05-30
Howdy,

Either use the UFW firewall wizard and enable FTP, or kill your firewall completely (you probably don't really need it anyway - firewalls are mainly a Windows relic).  The problem is that FTP requires a tracker in the firewall - just opening port 21/TCP is not enough.

You can kill your mostly useless firewall rules with:
$ sudo iptables -F

---

### Post by hictio on 2010-05-30
If you decide that you actually want to keep your iptables firewall up & running, check this page [Ubuntu Server Project #4: Iptables Firewall](http://www.theosquest.com/2008/01/23/ubuntu-server-project-4-iptables-firewall/), it is really pretty simple to have an iptables firewall enabled on your Linux box (without getting onto the debate whether it is a Windows heritage thing or not ;) )

As HermanAB, says, you'll pretty sure need to have not only 21 TCP open, but also a dinamic range of ports open as well, check the vsftpd.conf file, the directives are called "pasv_max_port" and "pasv_min_port".

Then, you'll have to add rules like this:

```

iptables -A INPUT -p tcp --dport 21
iptables -A INPUT -p tcp --dport $pasv_min_port_value
iptables -A INPUT -p tcp --dport $pasv_max_port_value

```

You'll need at least one port open, that is one port increment in order to work, if you want concurrent connections, add more difference between pasv_min_port and pasv_max_port; something like leaving 50 ports is a good ballpark.

---

### Post by HermanAB on 2010-05-30
Hmm - any kind of reverse procedure call thing like FTP turns a firewall into Swiss cheese with so many holes that there is not much point in keeping it.  However, there is a FTP tracker module for iptables that reduces the damage.

---

### Post by HittingSmoke on 2010-05-30
Ok, I think I've narrowed down my problem, and it's not the firewall.

I've written a firewall script via [this guide]("http://ubuntuforums.org/showthread.php?t=159661") to enable FTP and it's still is not working.

Turns out the FTP server isn't even running. I set it to run at startup so I figured it was.

*'service vsftpd status'* reports that it is not running even after trying to start it using *'sudo service vsftpd start'* and *'sudo /etc/init.d/vsftpd start'*

Any idea why my ftp server wont start? Both of the service start commands report:
> *Starting FTP server: vsftpd [OK]

---

### Post by hictio on 2010-05-30
> **HittingSmoke said:**
> Ok, I think I've narrowed down my problem, and it's not the firewall.

I've written a firewall script via [this guide]("http://ubuntuforums.org/showthread.php?t=159661") to enable FTP and it's still is not working.

Turns out the FTP server isn't even running. I set it to run at startup so I figured it was.

*'service vsftpd status'* reports that it is not running even after trying to start it using *'sudo service vsftpd start'* and *'sudo /etc/init.d/vsftpd start'*

Any idea why my ftp server wont start? Both of the service start commands report:

As usual, with this type of problem, your best friends are the logs. If you haven't already, enable logging on the vsftpd.conf, and restart or try to, the daemon.
Another logs to check might be /var/log/messages & /var/log/syslog to see if you spot any error.

---

### Post by HittingSmoke on 2010-06-01
> **hictio said:**
> As usual, with this type of problem, your best friends are the logs. If you haven't already, enable logging on the vsftpd.conf, and restart or try to, the daemon.
Another logs to check might be /var/log/messages & /var/log/syslog to see if you spot any error.

I just gave up and installed proftpd

Works much better now, thanks.

---

