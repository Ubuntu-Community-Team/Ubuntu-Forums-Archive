---
title: "ssh brute force"
date: 2011-02-07
forum: Security
---

### Post by Mosabama on 2011-02-07
Hey,

can someone explain this for me:

I tried to make a dynamic DNS entry in dyndns.org so I can ssh my machine from the internet. and I choose (lets say) mosab.dyndns.org.
I installed the software that updates my ip address and configured my router to forward port 22 to my local linux machine. and I configured that correctly.
after all the efforts it seems that the router DOES NOT forward the ssh request to my local machine.. when I ssh mosab.dyndns.org I reach my router and I can access it. any way I tried and I tried then I gave up thinking that my router has a problem.

today I went through my /var/auth.log and I noticed that some one is trying to access my local machine by ssh.. and its a software I guess cause its trying all usernames and all password and it fails.

my question is that if my attempts to access my local machine from the internet failed.. how this software or person reaches my machine????

This is a very small sample of the tries:

```

Feb  8 00:07:49 mosab-Lap sshd[14262]: Failed password for root from 61.181.23.125 port 28387 ssh2
Feb  8 00:07:53 mosab-Lap sshd[14264]: Invalid user demo from 61.181.23.125
Feb  8 00:07:53 mosab-Lap sshd[14264]: pam_unix(sshd:auth): check pass; user unknown
Feb  8 00:07:53 mosab-Lap sshd[14264]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.181.23.125 
Feb  8 00:07:53 mosab-Lap sshd[14264]: pam_winbind(sshd:auth): getting password (0x00000388)
Feb  8 00:07:53 mosab-Lap sshd[14264]: pam_winbind(sshd:auth): pam_get_item returned a password
Feb  8 00:07:55 mosab-Lap sshd[14264]: Failed password for invalid user demo from 61.181.23.125 port 29552 ssh2
Feb  8 00:07:59 mosab-Lap sshd[14266]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.181.23.125  user=root
Feb  8 00:07:59 mosab-Lap sshd[14266]: pam_winbind(sshd:auth): getting password (0x00000388)
Feb  8 00:07:59 mosab-Lap sshd[14266]: pam_winbind(sshd:auth): pam_get_item returned a password
Feb  8 00:07:59 mosab-Lap sshd[14266]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Feb  8 00:08:01 mosab-Lap sshd[14266]: Failed password for root from 61.181.23.125 port 31397 ssh2
Feb  8 00:08:05 mosab-Lap sshd[14268]: Invalid user mysql from 61.181.23.125
Feb  8 00:08:05 mosab-Lap sshd[14268]: pam_unix(sshd:auth): check pass; user unknown
Feb  8 00:08:05 mosab-Lap sshd[14268]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.181.23.125 
Feb  8 00:08:05 mosab-Lap sshd[14268]: pam_winbind(sshd:auth): getting password (0x00000388)
Feb  8 00:08:05 mosab-Lap sshd[14268]: pam_winbind(sshd:auth): pam_get_item returned a password
Feb  8 00:08:07 mosab-Lap sshd[14268]: Failed password for invalid user mysql from 61.181.23.125 port 32533 ssh2
Feb  8 00:08:09 mosab-Lap sudo:    mosab : TTY=pts/0 ; PWD=/var/log ; USER=root ; COMMAND=/bin/cat auth.log
Feb  8 00:08:11 mosab-Lap sshd[14270]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.181.23.125  user=root
Feb  8 00:08:11 mosab-Lap sshd[14270]: pam_winbind(sshd:auth): getting password (0x00000388)
Feb  8 00:08:11 mosab-Lap sshd[14270]: pam_winbind(sshd:auth): pam_get_item returned a password
Feb  8 00:08:11 mosab-Lap sshd[14270]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Feb  8 00:08:13 mosab-Lap sshd[14270]: Failed password for root from 61.181.23.125 port 34340 ssh2
Feb  8 00:08:17 mosab-Lap sshd[14278]: Invalid user password from 61.181.23.125
Feb  8 00:08:17 mosab-Lap sshd[14278]: pam_unix(sshd:auth): check pass; user unknown
Feb  8 00:08:17 mosab-Lap sshd[14278]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.181.23.125 
Feb  8 00:08:17 mosab-Lap sshd[14278]: pam_winbind(sshd:auth): getting password (0x00000388)
Feb  8 00:08:17 mosab-Lap sshd[14278]: pam_winbind(sshd:auth): pam_get_item returned a password
Feb  8 00:08:19 mosab-Lap sshd[14278]: Failed password for invalid user password from 61.181.23.125 port 35476 ssh2
Feb  8 00:08:23 mosab-Lap sshd[14280]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.181.23.125  user=root
Feb  8 00:08:23 mosab-Lap sshd[14280]: pam_winbind(sshd:auth): getting password (0x00000388)
Feb  8 00:08:23 mosab-Lap sshd[14280]: pam_winbind(sshd:auth): pam_get_item returned a password
Feb  8 00:08:23 mosab-Lap sshd[14280]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user

```   

Thanks

---

### Post by gmargo on 2011-02-07
Clearly the router is forwarding SSH to your machine.  What you're seeing is "script kiddies" trying to break in.  For this reason, you should use a different port than the well-known port 22, and also disable password based authentication.

If you try to ssh to your dyndns address from inside your network, you may get the router or you may get back to your machine, depending on the configuration and ability of the router.  If you ssh from outside your network, then it should work.

---

### Post by Mosabama on 2011-02-07
hmm .. well I didnt try to access my machine from outside to be honest. I will try that and I will let you know.

---

### Post by CharlesA on 2011-02-07
> **Mosabama said:**
> hmm .. well I didnt try to access my machine from outside to be honest. I will try that and I will let you know.

Most routers don't do "Nat redirection" so you wouldn't be able to connect from inside yer network using the external ip/hostname.

You'd have to do it from outside.

To cut down on login attempts, you can limit traffic by using iptables or something like deny hosts.

---

### Post by wojox on 2011-02-07
Works for me:

```

wojox@wojox-desktop:~$ ssh 61.181.23.125
The authenticity of host '61.181.23.125 (61.181.23.125)' can't be established.
RSA key fingerprint is cf:43:8b:95:37:ae:50:40:3e:92:85:de:be:81:08:f7.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '61.181.23.125' (RSA) to the list of known hosts.
Password: 
Password: 
Password: 
Permission denied (publickey,keyboard-interactive).


```

The attacker that is.

---

### Post by HermanAB on 2011-02-08
```
# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT

```

---

### Post by uRock on 2011-02-08
> **HermanAB said:**
> ```
# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT

```
That looks great! Will it block all incoming attempts for the period of time or just the offending IP?

---

### Post by CharlesA on 2011-02-08
That'll just limit the amount of new connections to 30 per minute. It'll drop anything that's more then that.

---

### Post by HermanAB on 2011-02-08
In my experience, if you throttle new connection attempts as above, the attacks time out and go away after a few attempts.

So that simple iptables rule works against pretty much all abuse.

---

### Post by uRock on 2011-02-08
Sounds good enough to me.

---

### Post by hollerith on 2011-02-17
I only enable three [ports]("http://min.us/mvb0fa7").  How do you get failed password attempts on the other ports?  

Feb  8 00:08:17 mosab-Lap sshd[14278]: pam_winbind(sshd:auth): pam_get_item returned a password
Feb  8 00:08:19 mosab-Lap sshd[14278]: Failed password for invalid user password from 61.181.23.125 port [COLOR="Red"]35476[/COLOR] ssh2

This is bad even if you use RSA (which I do) because it still reports whether users are valid or not.

EDIT:link to picture of router setup

---

### Post by CharlesA on 2011-02-17
That's the source port, which is usually a random high numbered port. Even if you only use keys, it will still log the connection attempt.

---

### Post by Doug S on 2011-02-17
For idenifying and temporily (90 minutes in this example) blocking IP addresses that are trying brute force attacks on the SSH (secure shell) port, I have been using the following iptable rules for many years now:
 
```
 
# Secure Shell on port 22.
#
# Dynamic Badguy List. Detect and DROP idiots that do password attacks on SSH.
# Once they are on the BADGUY list then DROP all packets from them.
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 5400 --name BADGUY_SSH -j DROP
$IPTABLES -A INPUT -i $EXTIF -p tcp -m tcp --dport 22 -m recent --set --name BADGUY_SSH -j ACCEPT


```
 
While not required, but to reduce the permitted number of password attempts per connection, I also edit the sshd_config file and add the following:
 
```
 
#Limit the number of bad passwords per connection to 2. Default is 6.
#Then the iptables connection counter will kick in sooner to drop
#password attack hackers.
MaxAuthTries 2
 

```

---

### Post by bodhi.zazen on 2011-02-17
> **HermanAB said:**
> In my experience, if you throttle new connection attempts as above, the attacks time out and go away after a few attempts.

So that simple iptables rule works against pretty much all abuse.

IMO using iptables is the way to go as well. It does not require installation of any additional daemons (denyhosts fail2ban).

both denyhosts and fail2ban can introduce additional vulnerabilities and they usually need to be configured.

You should also use keys and disable passwords.

---

### Post by hollerith on 2011-02-17
They cycle their own ports?  I thought was sort of brute force port scanner combo.  I've implemented a similar set of iptables rules from samhain.de (gaelic for halloween in case anyone is interested btw).  I was still getting root failed password attempts so I've changed from the default port now.  I know this happens from time to time (hence RSA instead of passwords, no root login and tricky user names) but I seem to drawing a LOT of fire lately, maybe I'm paranoid ;) but it seems like a consistent and concerted effort.  
Maybe they are just using the same lame scripts.

---

### Post by CharlesA on 2011-02-17
It'll always be a connection to port 22, or whatever port you are using, but the source port is the one that is logged.

"The source port, which can be a random number, is assigned to the client and is used to keep track of user sessions."

[Source]("http://www.pcmag.com/encyclopedia_term/0,2542,t=TCPIP+port&i=52617,00.asp").

Changing the port will only stop bot attacks from cluttering your logs. If you aren't using password auth (which you aren't) and ban an IP after xx number of connection attempts within a certain time frame, you'll be fine. :)

---

### Post by bodhi.zazen on 2011-02-17
> **hollerith said:**
> I was still getting root failed password attempts so I've changed from the default port now.

It is a sustained effort to brute force your ssh server, but ...

Honestly , as long as you use keys and disable password authentication you probably do not need to do anything more.

If you are paranoid you can add a few rules for iptables, but, IMHO, keys only is secure enough (so long as you do not use paswordless keys).

changing the port may make you feel better, and certainly quiets the log, but does little to add to security, and adds an inconvenience factor to your clients.

---

### Post by kevdog on 2011-02-20
I'd second bodhi recommendations.  But also look at the needs of the server.  If you are the only one using it, changing ports make sense (if you want to decrease the log entries).  If you have a bunch of users, this approach may confuse many.

Between altering the sshd_config file, where you can potentially limit users, limit groups, limit authentication attempts, limit IP addresses, you can use IPTables to refine the denial process.  

If you really want to get crazy you can use a port knocker program like fwknop, however again this isn't really practical with a bunch of users since this just complicated the login process.

The only potential problem which I could envision by using RSA keys, altering the sshd_config file, along with using IP Tables for packet filtering, would be a zero day exploit in the ssh daemon itself.  This is an extremely unlikely event, although an exploit was discovered I believe 2-3 years ago.  Prior to this discovery the exploit was present for many years within the ssh code itself.  I'm uncertain however if anyone was actually compromised by this exploit, however the point is -- you will hear the term "zero-day" thrown around a lot.  Its something unless you are guarding national secrets I really wouldn't concern myself with.

---

### Post by matt_symes on 2011-02-21
Hi

The only real way to secure any PC is to unhook it from the internet and all networks, put it in a locked vault and destroy the key. ;)

Seriously though, the advice you have been given here will make your ssh server as secure as it can be.

Keys with a pass phrase, changing the default port, editing the options in sshd_config and, of course, filtering by IP tables.

As far as changing the port goes, if you are connecting via Putty from Windows you can save the session details so the port only needs to be entered once. From any Linux box you can set up an alias so the port only has to be remembered once as well.

```
alias ssh_to_server=ssh username@<host_or_ip> -p <port_number>
```

You can, of course, edit your .ssh/config file as well.

As kevdog highlighted, your biggest issue with ssh is lightly to be a zero day exploit but as you are running Linux any security holes will be patched very very quickly. You will not have to wait a month or more for it to be patched.

Nothing is ever totally secure but neither is Fort Knox. However with that much security and that many guards, have a go at getting in and see where you get to :)

Your biggest security issues are lightly to be with other services you run on your server such as apache.

Kind regards

---

### Post by hawkmage on 2011-02-23
I had an issue with literally hundreds to thousands of ssh login attempts when I used the standard port 22 on my firewall through to my Linux system.  Before I had a firewall that would do NAT port translation I added another listen port on sshd.  This way I could allow the alternate port through the firewall to the Linux box and still use the standard port 22 while on the internal network.  It also allowed me to create seporate iptables rules for the two ports.  

I agree that changing ports will not make it any more secure but it will keep the regular script kitties from blasting you with connections.

---

### Post by Mosabama on 2011-03-14
I tried connecting from outside the network and it worked, it seems the router doesnt have this capability. (ssh from inside the network back to the network).

I use a key now, and I changed the default port. attempts to ssh my machine stopped completely now.

Thanks all your comments were helpful.

---

### Post by Mosabama on 2011-03-14
> **hollerith said:**
> I only enable three [ports]("http://min.us/mvb0fa7").  How do you get failed password attempts on the other ports?  

Feb  8 00:08:17 mosab-Lap sshd[14278]: pam_winbind(sshd:auth): pam_get_item returned a password
Feb  8 00:08:19 mosab-Lap sshd[14278]: Failed password for invalid user password from 61.181.23.125 port [COLOR="Red"]35476[/COLOR] ssh2

This is bad even if you use RSA (which I do) because it still reports whether users are valid or not.

EDIT:link to picture of router setup


yeah I wonder whats the reason of that !!

---

