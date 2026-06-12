---
title: "SSH attack within 14 hours of install"
date: 2009-10-21
forum: Security
---

### Post by matherp on 2009-10-21
Yesterday evening 19:00 I built a unbuntu server (9.04) for the first time. I want to use it remotely and included ssh in the install. the configuration was absolutely standard and I haven't enabled root etc. I configured port forwarding on port 22 in the router but made no other changes to the default ssh setup. I'm using dyndns to allow my dynamic ip address to be seen from the outside. I have never previously exposed port 22.
 
This morning at 08:27 the server came under a sustained attempt by 202.104.183.2 to log into ssh trying a range of user names including root and most common first names - but not by the time I discovered it mine - which is my username.
 
I have to say I'm staggered and appalled that within 14 hours my address is under attack.
 
I googled 202.104.183.2 and found it in a couple of lists of hosts.deny that appear on the web but no other information.
 
To further protect my site I'm intending to do the following and would appreciate comments.
 
1. remove all simple usernames and replace by non-guessable ones
2. implement hosts.deny as per the best listing found
3. change all outside ports from defaults to something random (i.e. not 1022 etc.)
 
Is there anything else I should do (I'm not a unix guru)
 
Be careful out there!
 
Peter

---

### Post by Rhubarb on 2009-10-21
Yes this is quite common, there's quite a few script kiddies / botnets scanning randem IP addresses on port 22 trying to gain root access.

I would reccomend:

[LIST]
[*]Using a non-standard ssh port
[*]Using a not-so-common username and a reasonably strong password
[*]Installing denyhosts, which is very powerful and effective - have a read up what it can do as I'd very much recommend using it :)
[/LIST]

---

### Post by renkinjutsu on 2009-10-21
also, it's good to disable a password login and use keys instead

---

### Post by stinger30au on 2009-10-21
i remember not too long ago reading that a default install of ubuntu server is extermely easy to attack from the net and get taken over by someone else

i will go a googling and see if i can find it

the article also told how to fix it as well

---

### Post by stinger30au on 2009-10-21
here we go

heres the article i was talking about

[http://www.linux-mag.com/id/7297](http://www.linux-mag.com/id/7297)

---

### Post by lovinglinux on 2009-10-21
> **renkinjutsu said:**
> also, it's good to disable a password login and use keys instead

+1

See [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)



.

---

### Post by kevdog on 2009-10-21
Use iptables to limit the rate of connection attempts per ip address.

---

### Post by CharlesA on 2009-10-21
> **Rhubarb said:**
> Yes this is quite common, there's quite a few script kiddies / botnets scanning randem IP addresses on port 22 trying to gain root access.

I would reccomend:

[LIST]
[*]Using a non-standard ssh port
[*]Using a not-so-common username and a reasonably strong password
[*]Installing denyhosts, which is very powerful and effective - have a read up what it can do as I'd very much recommend using it :)
[/LIST]

+1

> **renkinjutsu said:**
> also, it's good to disable a password login and use keys instead

+2

Also just wanted to note: Out of the box the only thing SSH prompts for is a password, which can be cracked given enough time. I'd do all of the above.

Personally I've got my SSH server set up on a non-standard port, using keys for authentication and denyhosts (probably unneeded with keys) installed. I've also set iptables to only accept connections on the port SSH uses from the IPs I connect from.

---

### Post by movieman on 2009-10-21
> **stinger30au said:**
> heres the article i was talking about

While I agree with the suggestions in the article, it doesn't mean that an Ubuntu server is 'extremely easy to take over from the Net'. For a start, any server should sit behind a firewall, which would block access to services that you don't want people to use.

---

### Post by cdenley on 2009-10-21
> **stinger30au said:**
> here we go

heres the article i was talking about

[http://www.linux-mag.com/id/7297](http://www.linux-mag.com/id/7297)

Well that article does not show at all that ubuntu is "extermely easy to attack".

1. world readable home directory
Making any user permissions more restrictive would be safer, but this only allows local users to access your home directory, which shouldn't contain anything sensitive anyway.

2. mysql password optional
If the user chooses not to use a password, they're still safe since mysql doesn't accept remote connections by default.

3. "pop3" and "imap2"
Netstat does not indicate what protocol is being used. It simply indicates the protocol commonly used for that port. A mail server listening for connections on port 110 and 143 should be expected. The server may support encrypted connections, but not all clients may. Anyone running a server should know how to configure it. The only way unencrypted mail connections could make your system insecure is if a user uses your server without encryption, and someone intercepts their password.

4. Changing the shell for system accounts wouldn't be a bad idea. However, if a process running as that user is compromised and used to execute arbitrary code, a shell can be executed regardless of what that user's shell is configured as in /etc/passwd. You need to configure apparmor to protect from potential arbitrary code execution vulnerabilities. The only situation changing the user's shell to /bin/false would protect you is if someone attempts to start a terminal session as that user, which shouldn't be possible with no password set and no ssh keys configured.

To summarize, that author appears to be less of an expert than myself, and that article is nothing but FUD. Ubuntu is not insecure by default.

---

### Post by QLee on 2009-10-21
[QUOTE=matherp]I have to say I'm staggered and appalled that within 14 hours my address is under attack. [/QUOTE]

You've already received good advice on ways to deal with the situation you stated, I just want to put this quoted comment in perspective. I have a system that accesses the 'Net with a dialup account. Hits on its port 22 start within minutes (sometimes seconds, rather than hours) of it going online, as well as hits other ports known for exploits, you probably have hits on other ports in your firewall log too, or in your kern.log. Some are probably benign, some are probably trying to be malicious.

---

### Post by Lars Noodén on 2009-10-21
> **QLee said:**
> You've already received good advice on ways to deal with the situation you stated, I just want to put this quoted comment in perspective. I have a system that accesses the 'Net with a dialup account. Hits on its port 22 start within minutes (sometimes seconds, rather than hours) of it going online, as well as hits other ports known for exploits, you probably have hits on other ports in your firewall log too, or in your kern.log. Some are probably benign, some are probably trying to be malicious.

Even if it is not installed, you will still get hit on port 22.  It's just that you weren't looking before.  He was also getting ssh attacks 14 hours, or more, prior to install.  

As suggested, disable remote root login in sshd_config.
Use tcpd (hosts.deny, hosts.allow)
Use iptables to limit the rate of the scans at least.  

There are also slower, distributed scans going on sending a packet or two just every long once in a while and rarely to the same target twice. Those would require pooling of information from many hosts, to properly identify the misbehaving machines.

---

### Post by QLee on 2009-10-21
> **Lars Noodén said:**
> Even if it is not installed, you will still get hit on port 22.  It's just that you weren't looking before.  He was also getting ssh attacks 14 hours, or more, prior to install. 

Even if "what" is not installed Lars, I don't understand your response, I was just telling him port scans are common and frequent and that 14 hours after going online isn't surprising.

Edit: Aha, I believe I understand now, you were responding to OP rather than me and you meant even if port 22 wasn't open. Sorry for the noise.

---

### Post by undecim on 2009-10-21
Standard SSH installs get attacked a lot. People will run scripts to try random IP addresses at port 22 for SSH servers, then hammer those with random names and common passwords. (I'm personally thinking of setting up a honeypot for fun...)

What I do to prevent this is route my server's ssh port (22) to a different external port with my router.

Some routers don't let you route one internal port to another external port though (linksys/cisco routers are the only ones that do, AFAIK), so you may have to change the port in sshd_config

You might also want to set up an IP whitelist (either with your router, though iptables, or with the /etc/hosts.* files)

There are lots of ways to secure it, but the best, IMHO, is changing the port number. After all, you can't attack what you cant find.

---

### Post by cdenley on 2009-10-21
> **undecim said:**
> I'm personally thinking of setting up a honeypot for fun...

A while ago, I patched openssh to log incorrect passwords.
```

*** ../orig/openssh-4.7p1/auth2-passwd.c        2006-08-04 21:39:39.000000000 -0500
--- auth2-passwd.c      2008-09-15 15:46:07.000000000 -0500
***************
*** 29,35 ****
--- 29,40 ----
  
  #include <string.h>
  #include <stdarg.h>
+ #include <time.h>
+ #include <sys/stat.h>
+ #include <stdio.h>
+ #include <errno.h>
  
+ #include "canohost.h"
  #include "xmalloc.h"
  #include "packet.h"
  #include "log.h"
***************
*** 72,77 ****
--- 77,94 ----
        if (check_nt_auth(1, authctxt->pw) == 0)
  		authenticated = 0;
  #endif
+     if(authenticated==0)
+     {
+         FILE *pot;
+         pot = fopen("/honeypot/ssh.txt", "a");
+         if(pot!=NULL) {
+             fprintf(pot,"%i\r%.100s\r%.100s\r%.200s\n",
+                 (int)time(NULL),authctxt->user,password,get_remote_ipaddr());
+             fclose(pot);
+         }
+         else
+             logit(strerror(errno));
+     }
  	memset(password, 0, len);
  	xfree(password);
  	return authenticated;

```
I think I found that patch somewhere, don't remember where. You have to turn off UsePrivilegeSeparation in sshd_config. I ran it as a separate instance in addition to my regular ssh, and configured it to not allow any users.

---

### Post by Soul-Sing on 2009-10-21
Add some basic iptables rules:

[COLOR="Red"]some protection of Denial of Service attacks[/COLOR]
example:

iptables -A FORWARD -p tcp --syn -m limit --limit 1/s -j ACCEPT
iptables -A INPUT -p icmp -m limit --limit 1/s -j ACCEPT

[COLOR="Red"]some protection against 'Syn-flood'[/COLOR],:

iptables -A FORWARD -p tcp --tcp-flags SYN,ACK,FIN,RST RST -m limit --limit 1/s -j ACCEPT

[COLOR="Red"]some protection against 'Ping of deaths[/COLOR]':
iptables -A FORWARD -p icmp --icmp-type echo-request -m limit --limit 1/s -j ACCEPT

---

### Post by echo6 on 2009-10-24
Try sshblack [http://www.pettingers.org/code/sshblack.html](http://www.pettingers.org/code/sshblack.html) which will allow you to automatically block repeated ssh attempts using iptables.

---

### Post by cdenley on 2009-10-24
> **echo6 said:**
> Try sshblack [http://www.pettingers.org/code/sshblack.html](http://www.pettingers.org/code/sshblack.html) which will allow you to automatically block repeated ssh attempts using iptables.

I haven't looked at that script, but I would avoid installing software from outside the repos whenever possible. Stick with fail2ban, denyhosts, or just use iptables rate-limiting.

---

### Post by shihabs on 2009-10-24
Use a very strong password - Include symbols, numbers, ALT key sequences. 
If your password is in the dictionary it is insecure

---

### Post by cprofitt on 2009-10-25
> **renkinjutsu said:**
> also, it's good to disable a password login and use keys instead

Keys are likely the best idea.

Changing ports does little to really hide the service -- it will be found.

---

### Post by cprofitt on 2009-10-25
> **shihabs said:**
> Use a very strong password - Include symbols, numbers, ALT key sequences. 
If your password is in the dictionary it is insecure

If you are going to use a password then a long password is much more secure than using one than a shorter one with symbols, numbers and Caps. Just think of a Ven Diagram to understand why.

---

