---
title: "ssh d110.webcreatif.net"
date: 2008-08-28
forum: Security
---

### Post by chillifrost on 2008-08-28
Hi,

I run an ssh server on my machine, who's domain name is say X.net.

I saw the following when I ran netstat -t

tcp6       0      0  X.net:ssh  d110.webcreatif.net:50346 ESTABLISHED

I don't know anyone who would login from d110.webcreatif.net.  I ran 'who' and it didn't show anyone logged in from there.

So I turned off the SSH server using the KDE Services application. When I ran netstat that connection was gone. I turned the SSH service back on, and behold that connection was back.

What do you think is happening here?

Thanks,
Amit.

---

### Post by cdenley on 2008-08-28
> **chillifrost said:**
> Hi,

I run an ssh server on my machine, who's domain name is say X.net.

I saw the following when I ran netstat -t

tcp6       0      0  X.net:ssh  d110.webcreatif.net:50346 ESTABLISHED

I don't know anyone who would login from d110.webcreatif.net.  I ran 'who' and it didn't show anyone logged in from there.

So I turned off the SSH server using the KDE Services application. When I ran netstat that connection was gone. I turned the SSH service back on, and behold that connection was back.

What do you think is happening here?

Thanks,
Amit.

My guess is someone/something is trying and failing to login. I believe that would get logged here.
```

tail /var/log/auth.log

```

---

### Post by cariboo on 2008-08-29
It looks like another rooted server. I guess I'm lucky as I've only seen 5 of these so far this week.

Jim

---

### Post by rogeriopvl on 2008-08-29
Your server probably is compromised. And the attacker changed the "who" command to hide his presence. Try using something like chkrootkit ou rkhunter to check for rootkits installed. Backup your data.

If you have the time, you can now monitor the attacker's activity to gather more info.

---

### Post by cdenley on 2008-08-29
> **rogeriopvl said:**
> Your server probably is compromised. And the attacker changed the "who" command to hide his presence. Try using something like chkrootkit ou rkhunter to check for rootkits installed. Backup your data.

If you have the time, you can now monitor the attacker's activity to gather more info.

I respectfully disagree. It couldn't hurt to check for rootkits, but just because you have a connection opened to your ssh server doesn't mean you have been compromised. Unless, of course, you have a weak encryption key because you haven't been installing security updates.

---

### Post by moonpup on 2008-08-29
I concur with cdenley as well. Just because there is a connection does not mean you are compromised. Check your /var/log/auth.log and see if there actually is a successful login from that address. If there is a successful login, then yes you are compromised and you will need to backup and re-install.

Let us know what you find out.

---

### Post by brian_p on 2008-08-29
> **chillifrost said:**
> 

So I turned off the SSH server using the KDE Services application. When I ran netstat that connection was gone. I turned the SSH service back on, and behold that connection was back.

What do you think is happening here?

A record of the connection persists for a time after the remote end times out. If the service was reactivated a few seconds after stopping it you were seeing data for the same connection.

The chance of a compromise are very, very low (you do have a strong password or use keys with an up to date ssh?) so follow cdenley's advice. You could also try

```
last
```

and

```
lastlog
```

---

### Post by rogeriopvl on 2008-08-29
I didn't that said that just because I had a feeling.... 

I've said it because I know that d110.webcreatif.net is a compromised machine, and guess what? It's a DNS server! (Does it ring any bells?)

So given this information, I would pretty much say that it's not normal to have an SSH connection from that host...

---

### Post by chillifrost on 2008-08-29
Hi 

I have not been aware of SSH vulnerabilities, but I keep my updated on a daily basis. Whatever updates Ubuntu pushes, I apply to my machine.  Some weeks ago, as part of an update I did notice OpenSSL being updated and along with it the DSA keys.

I tried last and lastlog. Found nothing untoward there. But in the /var/logs/auth I found this.

Aug 28 15:16:30 myserver sshd[3716]: Failed password for root from 212.203.66.110 port 36500 ssh2
Aug 28 15:16:31 myserver sshd[3718]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=d110.webcreatif.net  user=root

Aug 28 15:16:33 myserver sshd[3718]: Failed password for root from 212.203.66.110 port 36677 ssh2
Aug 28 15:16:34 myserver sshd[3720]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=d110.webcreatif.net  user=root

Aug 28 15:16:36 myserver sshd[3720]: Failed password for root from 212.203.66.110 port 36818 ssh2
Aug 28 15:16:37 myserver sshd[3722]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=d110.webcreatif.net  user=root

There's at least a hundred such messages. So it seems like someone *is* trying to hack into my computer, but so far has failed. So even though in my original post, the SSH connection showed as established, it does not mean "successfully" authenticated, right? So thus far, I've been safe?

I've computer savvy, but my admin savvy is limited to (1) not running any services I'm not using, (2) firewalling everything but what is absolutely essential (like the SSH server), (3) applying the updates as soon as they are pushed to me, and (4) strong passwords and no privileges for anyone but me. If someone could point out how I can find out if my SSH/SSL installation is up to the mark security-wise, I'll be grateful.

And thanks for all the extremely helpful suggestions. You guys are wonderful. :)

Amit.

---

### Post by cdenley on 2008-08-29
> **rogeriopvl said:**
> I didn't that said that just because I had a feeling.... 

I've said it because I know that d110.webcreatif.net is a compromised machine, and guess what? It's a DNS server! (Does it ring any bells?)

So given this information, I would pretty much say that it's not normal to have an SSH connection from that host...

If a compromised machine is connecting to your ssh server, that sounds completely expected to me. Just because a person/script is using a compromised server to guess your password doesn't mean they have hacked you. Did you think hackers were using their personal computers for all those failed authentication attempts you find for any ssh server on port 22? Just because it has an open TCP connection to your server doesn't mean they have successfully authenticated or have any access whatsoever except an authentication attempt.

---

### Post by cdenley on 2008-08-29
> **chillifrost said:**
> Hi 

I have not been aware of SSH vulnerabilities, but I keep my updated on a daily basis. Whatever updates Ubuntu pushes, I apply to my machine.  Some weeks ago, as part of an update I did notice OpenSSL being updated and along with it the DSA keys.

I tried last and lastlog. Found nothing untoward there. But in the /var/logs/auth I found this.

Aug 28 15:16:30 myserver sshd[3716]: Failed password for root from 212.203.66.110 port 36500 ssh2
Aug 28 15:16:31 myserver sshd[3718]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=d110.webcreatif.net  user=root

Aug 28 15:16:33 myserver sshd[3718]: Failed password for root from 212.203.66.110 port 36677 ssh2
Aug 28 15:16:34 myserver sshd[3720]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=d110.webcreatif.net  user=root

Aug 28 15:16:36 myserver sshd[3720]: Failed password for root from 212.203.66.110 port 36818 ssh2
Aug 28 15:16:37 myserver sshd[3722]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=d110.webcreatif.net  user=root

There's at least a hundred such messages. So it seems like someone *is* trying to hack into my computer, but so far has failed. So even though in my original post, the SSH connection showed as established, it does not mean "successfully" authenticated, right? So thus far, I've been safe?

I've computer savvy, but my admin savvy is limited to (1) not running any services I'm not using, (2) firewalling everything but what is absolutely essential (like the SSH server), (3) applying the updates as soon as they are pushed to me, and (4) strong passwords and no privileges for anyone but me. If someone could point out how I can find out if my SSH/SSL installation is up to the mark security-wise, I'll be grateful.

And thanks for all the extremely helpful suggestions. You guys are wonderful. :)

Amit.

Just as I suspected, they were trying to guess your root password. This will always fail, since by default, there is no valid password for root.

To prevent attacks such as these, you can install fail2ban or denyhosts and/or change the port that ssh listens on.

---

### Post by brian_p on 2008-08-29
> **chillifrost said:**
> Hi 

I have not been aware of SSH vulnerabilities, but I keep my updated on a daily basis. Whatever updates Ubuntu pushes, I apply to my machine.

Great!

> I tried last and lastlog. Found nothing untoward there.

Good.

> But in the /var/logs/auth I found this.

Aug 28 15:16:30 myserver sshd[3716]: Failed password for root from 212.203.66.110 port 36500 ssh2

Most attempts try passwords. Yours is strong so they fail even if they manage to guess a username, which is highly unlikely.

> There's at least a hundred such messages. So it seems like someone *is* trying to hack into my computer, but so far has failed.

Automated scripts are being used. They will always fail against strong passwords or keys.

> So even though in my original post, the SSH connection showed as established, it does not mean "successfully" authenticated, right?

Correct. You just happened to catch the attempted logins at a time you were using netstat.

>  So thus far, I've been safe?

Yes. And will remain so if you continue your present practices.

> I've computer savvy, but my admin savvy is limited to (1) not running any services I'm not using, (2) firewalling everything but what is absolutely essential (like the SSH server), (3) applying the updates as soon as they are pushed to me, and (4) strong passwords and no privileges for anyone but me. If someone could point out how I can find out if my SSH/SSL installation is up to the mark security-wise, I'll be grateful.

That's it. You've done it. Firewalling's not necessary but the rest is spot on.

Read

```
man sshd_config
```

The  AllowUsers directive might be useful.

---

### Post by moonpup on 2008-08-29
> **rogeriopvl said:**
> I didn't that said that just because I had a feeling.... 

I've said it because I know that d110.webcreatif.net is a compromised machine, and guess what? It's a DNS server! (Does it ring any bells?)

So given this information, I would pretty much say that it's not normal to have an SSH connection from that host...

How do you know for sure that it's a compromised dns server? Also, if you are positive that it's compromised have you at least tried to contact the owner of it?

and to add: i just scanned the box, and looked at the web addres and it looks like a default fedora box with alot of stuff running. also the alternate http port that redirects to a login page... lol that doesn't look good!

---

### Post by rogeriopvl on 2008-08-29
> **moonpup said:**
> How do you know for sure that it's a compromised dns server? Also, if you are positive that it's compromised have you at least tried to contact the owner of it?

and to add: i just scanned the box, and looked at the web addres and it looks like a default fedora box with alot of stuff running. also the alternate http port that redirects to a login page... lol that doesn't look good!

yes I did tried to contact some time ago, no response yet.

---

### Post by tubezninja on 2008-08-31
I used to contact people about potentially compromised boxes, but have unfortunately found the effort to be fruitless.  Now I only do it in cases where the box is at a university, or part of a webhosting/rackspace service, generally. Those types of locations both have IT security departments and tend to be proactive about compromised systems.

---

### Post by cariboo on 2008-08-31
I contacted an ISP in India about a compromised computer, and they actually answered back and said they would look into it. That's the best answer I ever got when I contacted an outfit about a problem, usually they just ignore you. Mind you this time I included a snippet from /var/log/auth.log

Jim

---

