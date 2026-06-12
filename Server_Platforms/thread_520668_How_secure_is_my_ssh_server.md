---
title: "How secure is my ssh server?"
date: 2007-08-08
forum: Server Platforms
---

### Post by Warren Watts on 2007-08-08
Ok, here is what I have done:

-Changed my password to a 16 character password
-Installed ssh
-Changed the defualt port for ssh to another higher port number
-Used firestarter to modify my iptables to restrict access to the specific IP's I will be logging in remotely from
-Created a file called /etc/remusers that contains the users able to remotely login
-Restricted logins to just those users listed in /etc/remusers with the following addition to /etc/profile:
> trap "" 2 3
 if [ $LOGNAME != "root" ]
 then
 if [ $TERM != "linux" ]
 then
 if [ -z `cat /etc/remusers |grep $LOGNAME` ]
 then
 echo " *************************************************** "
 echo " * * "
 echo " * Remote logins are not allowed on this system * "
 echo " * Please use a terminal or see the administrator. * "
 echo " * Press RETURN to exit. * "
 echo " * * "
 echo " *************************************************** "
 echo
 read
 exit
 fi
 fi
 fi
 trap 2 3

Anything else I need to do to tighten security, or is this pretty good?

I have already experienced several (unsuccessful) automated attempts by hackers to access my server via FTP and apache.

I know that ssh can provide an easy way into my computer if it isn't secured properly, and I want to be sure I've covered all the bases.

---

### Post by koenn on 2007-08-08
man tcpd
man hosts.allow

access control based on hostname and username for services such as ssh, etc.

---

### Post by ssam on 2007-08-08
maybe use denyhosts or fail2ban to blacklist IPs that try to brute force.

set up keys and disable password logins

---

### Post by eentonig on 2007-08-08
pretty secure already.

---

### Post by foxylad on 2007-08-08
Good work - looks like you are onto most things already, with respect to SSH anyway. I disable anything but named users, and disallow root logins  in /etc/ssh/sshd_config:

```
#Allowed Users
AllowUsers wallace grommit
PermitRootLogin no

```

This means attackers have to figure out my non-standard port, my non-standard username **and ** my password. 

I restrict SSH to three attempts from any one IP address in any five minute period with IP tables - a bit like denyhost mentioned above, but far more efficient and elegant. The following rules are for SSH on the standard port 22, just change that to the port you use:
```
#------------------------#
# SSH daemon - tcp Port 22 - drop any more than 3 new connections from one address every 5 mins
$IPTABLES -I INPUT -p tcp -i eth0 --dport 22 -m state --state NEW -m recent --set
$IPTABLES -I INPUT -p tcp -i eth0 --dport 22 -m state --state NEW -m recent --update --seconds 300 --hitcount 3 -j DROP
$IPTABLES -A INPUT -p tcp -i eth0 --dport 22 -j ACCEPT

```

So attackers now only have three shots at guessing username/password before my server stops responding - not good odds, especially as 75% use "root" as the username.

But now you have to look at all other services too - I don't allow FTP any more (SCP is just as good and is secure) and if you don't need external mail access etc, close off those avenues too.

---

### Post by Warren Watts on 2007-08-09
Thanks to everyone that responded!

I applied the suggested changes to iptables, and I feel fairly confident that I can safely leave my ssh server in place without fear of being hacked....

I just LOVE the Ubuntu Community!

Thanks, all!

---

### Post by Warren Watts on 2007-08-09
can I change the iptables commands listed to port 21 and limit my FTP logins to three attempts the same way?

And pardon my noobieness, but do the commands listed reset after a while and allow a user to try again later?

---

### Post by primski on 2007-08-09
brilliant iptables solution. i might use that as well.

---

### Post by bodhi.zazen on 2007-08-09
You might want to look at the use of keys :

[http://alblue.blogspot.com/2005/08/howto-ssh-logins-using-keys.html](http://alblue.blogspot.com/2005/08/howto-ssh-logins-using-keys.html)

[http://kimmo.suominen.com/docs/ssh/](http://kimmo.suominen.com/docs/ssh/)

Then in sshd_config Change :

#Change to no to disable tunnelled clear text passwords
passwordAuthentication **no**

This is what it looks like with out the key :

> user@xxx:~$ ssh <ip> -p y
The authenticity of host '[xxx]:y ([xxx]:y)' can't be established.
RSA key fingerprint is xxx.yyy.zzz.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '[xxx]:y' (RSA) to the list of known hosts.
Permission denied (publickey).
user@xxx:~$  

he he he ... no chance to even try a log in :twisted:

=================

And, add a new line to your sshd_config to the extent of &#8220;AllowUsers username&#8221; to limit connections to just yourself or &#8220;AllowUsers [email]username@work.com[/email]&#8221; to only allow your username from your work or office domain.

---

### Post by Warren Watts on 2007-08-09
I really like the idea of using a key stored on a USB flash memory device.  I already have a 256MB USB device I carry on my keyring (imagine that!) anyway.

In effect it really would be a key, one I would plug into the computer i was using to access my PC remotely.

Nifty!

---

### Post by wirelessmonkey on 2007-08-09
Also in sshd_config make sure ssh v1 is disabled.  I think it's that way by default, but if you've upgraded from an older version, the config may not have been changed....

---

### Post by cypresstwist on 2007-12-07
Also worth having a look at: [Tips for a more secure OpenSSH server ]("http://www.mylro.org/index.php/2007102698/Articole/How-To/Tips-for-a-more-secure-OpenSSH-server/menu-id-52.html")

---

### Post by HermanAB on 2007-12-07
Do a scan with nmap:
$ sudo nmap -sT -P0 -v -F w.x.y.z

That will quickly tell you whether there are other things to fix.

Cheers,

Herman

---

