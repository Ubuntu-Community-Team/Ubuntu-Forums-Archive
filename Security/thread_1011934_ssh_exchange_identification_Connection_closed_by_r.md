---
title: "ssh_exchange_identification: Connection closed by remote host"
date: 2008-12-15
forum: Security
---

### Post by rodendahl on 2008-12-15
If this has been posted before, I apologize.
Prior to last Thursday, I have been able to ssh into my server at home every day. Last week, I had a number of ssh login failures due to fat fingering the keyboard. 

Now, I get the error "ssh_exchange_identification: Connection closed by remote host". I am locked out. The /var/log/auth.log file shows the IP address of the subsequent login attempts and they are all failures.

I have tried from another Ubuntu laptop and a Windows laptop using WinSCP. All attempts are locked. It appears to be IP address related because I tried to ssh using another username and I get the same message.
I'm guessing that the IP address is blocked. I cannot get to another location.

How do I get back in?

---

### Post by Nepherte on 2008-12-15
Maybe you still have to allow the ip addresses in /etc/hosts.allow
```
sshd: xxx.xxx.xxx.xxx
```
You can use single ip addresses or network addresses with subnet masks.

---

### Post by rodendahl on 2008-12-15
With the help of a friend, I found the solution. 
1) clear out the hosts.deny file
2) restart the denyhosts daemon

Problem solved

---

### Post by Ampi on 2009-01-02
I have the same problem, but the posted solution doesn't help me. 

Since I moved and got a new IP address, I get this error. I have always been able to log in before. I do not have access to the remote computer. 

On my own computer I don't find the ssh logs. I have no idea what to do.

---

### Post by ploum on 2009-01-20
I've the same problem since today. My workaround: ssh to another box with another IP and then, from there, ssh to my server.

So it seems that my current IP is blocked somewhere. Unfortunatly, I cannot find where (both /etc/hosts.* files are empty)

---

### Post by cariboo on 2009-01-20
I have had  the same problem due to a ssh misconfiguration. The way to repair the problem that was recommened in the forum, was to go to /var/lib/denyhosts and clear any instances of your ip address in the files in that directory. Be sure to stop the denyhost daemon before making any changes, as you will just be added to the hosts.deny list again.

Jim

---

### Post by ploum on 2009-01-21
Well, I don't have any denyhost file. The only file I have is /etc/hosts.deny and it's empty.

Also, package denyhosts is not installed on that server...

---

### Post by Ampi on 2009-01-21
same goes for me..

---

### Post by espakm on 2009-02-04
Same for me.
I usually get this message (ssh_exchange...), but sometimes not.
When I try to login repeatedly (6-10 times), sooner or later it asks for a password and I can log in.
The host.deny is empty, I have no /var/lib/denyhosts file, and there is much free memory.

---

### Post by cariboo on 2009-02-04
If you don't have denyhosts installed then the solution I mentioned will not work. 

Jim

---

### Post by Nepherte on 2009-02-05
If it's any help, this is my /etc/hosts.deny:
```
#
# /etc/hosts.deny
#

ALL: ALL: DENY

# End of file
```
And this is my /etc/hosts.allow
```

#
# /etc/hosts.allow
#

sshd: ALL EXCEPT /etc/hosts.evil

# End of file

```
I'm using DenyHosts though. Since you don't use it, remove EXCEPT /etc/hosts.evil

---

### Post by flint_ on 2009-03-01
Dear Rodendahl,

Thanks!

> **rodendahl said:**
> With the help of a friend, I found the solution. 
1) clear out the hosts.deny file
2) restart the denyhosts daemon

Problem solved

This worked for me.  As an extra measure put the ip address of your firewall or nat in the /etc/hosts.allow file like this:

ssh ip.of.nat.box  # where these are the canonical ip address as numbers.

Regards,

Flint

---

### Post by maphilli14 on 2009-06-29
I see this when switching from wired to wireless networks.  Then it goes away if I switch back and reboot the server.... any ideas???

TIA,

Mike

---

### Post by ejackman on 2009-07-17
Thanks rodendahl, this worked beautifully

> **rodendahl said:**
> With the help of a friend, I found the solution. 
1) clear out the hosts.deny file
2) restart the denyhosts daemon

Problem solved

---

### Post by zzzisgood on 2010-01-29
I had the same problem several days ago, it was working perfectly, but suddenly broken without any reason. 

Clearing the hosts.deny did not solve the problem for me, instead, I had to remove and reinstall openssh-server to get it work.

---

### Post by brianwc on 2010-02-06
I'm getting this problem on two Debian Lenny installs that use apt-pinning to install a few packages from Squeeze. This only began happening after doing the Lenny upgrades made available on January 30, 2010. 

I don't have a hosts.deny problem, changing the MaxStartups doesn't help, and removing and re-installing openssh-server and ssh made no difference. When I do ssh -v 192.168.1.35 I get:

OpenSSH_5.1p1 Debian-5, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.1.35 [192.168.1.35] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/identity type -1
debug1: identity file /root/.ssh/id_rsa type -1
debug1: identity file /root/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host

Any other ideas?

---

### Post by brianwc on 2010-02-07
Solution for me was:

```
         apt-get remove --purge libk5crypto3
         apt-get install --reinstall libkrb53

```

This also fixed an error that was causing apache2 not to start.

---

### Post by asm2000 on 2010-03-01
this worked for me 

echo "00 */4 * * 6 root /etc/init.d/ssh restart" >> /var/spool/cron/crontabs/root

---

### Post by asm2000 on 2010-03-01
or this also
edit:
/etc/ssh/sshd_config

Look for

Port 22
Protocol 2
#ListenAddress 0.0.0.0
#ListenAddress ::

uncomment this line:

ListenAddress 0.0.0.0

So it look like this:

Port 22
Protocol 2
ListenAddress 0.0.0.0
#ListenAddress ::

---

### Post by brianwc on 2010-08-09
```
         apt-get remove --purge libk5crypto3
         apt-get install --reinstall libkrb53
```

also worked for me on a Debian Lenny box.

---

### Post by Sociologist on 2010-12-28
> **brianwc said:**
> ```
         apt-get remove --purge libk5crypto3
         
```

And what this command do?:popcorn:

---

### Post by cariboo on 2010-12-28
If you aren't sure what a command does, you can always check the man page to see what the options do. eg:

```
man apt-get
``` 

the command you quoted, completely removes the package called libk5crypto3, checking synaptic, it tells us that the package is MIT Kerberos runtime libraries - Crypto Library

---

### Post by bmartin on 2011-03-03
> **cariboo907 said:**
> the command you quoted, completely removes the package called libk5crypto3, checking synaptic, it tells us that the package is MIT Kerberos runtime libraries - Crypto Library
Did you also know that it removes hundreds of packages on an Ubuntu 10.10 install? It's true! APT has removed Gimp and Nautilus from my system. It's currently purging libgtk.

Fantastic! It's a good thing I have a 10.10 install disk handy.

---

### Post by cariboo on 2011-03-03
That's why you should never blindly run commands posted in the forums, the command will tell you what it is going to remove. If you don't stop to read the output before proceeding, you only have yourself to blame.

---

### Post by bmartin on 2011-03-03
Not if you've aliased the command to assume "yes" at prompts.

SSHD seems like something that should work out of the box. It does in other distros.

EDIT: It's OK, I just reinstalled ubuntu-desktop and that fixed most of it. Thank you for your helpful suggestions!

---

### Post by CharlesA on 2011-03-03
> **bmartin said:**
> Not if you've aliased the command to assume "yes" at prompts.

You really shouldn't do that. As you found out, it can be harmful.

> SSHD seems like something that should work out of the box. It does in other distros.

I haven't run across a distro where SSH doesn't work "out of the box" after install.

---

### Post by bmartin on 2011-03-03
OK, thank you for the elitist statements on what I should and shouldn't do with my own computer. Instead of answers, all I get is criticism. I really wish I could SSH remotely, but I get the infamous "ssh_exchange_identification: Connection closed by remote host" message. That's it, I'm unsubscribing.

---

### Post by CharlesA on 2011-03-03
> **bmartin said:**
> OK, thank you for the elitist statements on what I should and shouldn't do with my own computer. Instead of answers, all I get is criticism. I really wish I could SSH remotely, but I get the infamous "ssh_exchange_identification: Connection closed by remote host" message. That's it, I'm unsubscribing.

You didn't give us any information outside of "it removes hundreds of packages." The original post in from 2008, and there have been many releases of Ubuntu since then.

See [here]("http://serverfault.com/questions/119881/ssh-exchange-identification-connection-closed-by-remote-host") for a possible fix to the problem you are having, but without more information it's quite hard to troubleshoot a problem.

---

### Post by uRock on 2011-03-03
```
sudo apt-get install ubuntu-desktop
``` will reinstall everything that you have uninstalled. I recommend removing the aliasing that you have done or use Synaptic Package Manager so that you can read and heed warnings before damaging your system in the future.

---

### Post by pointee on 2011-03-03
have the same problem, tried couple of things, until i found out, that actually my IP address was being blocked by the server i wanted to login to. i have no idea why my IP was put into the list on /etc/hosts.deny on the server. 
does anyone actually have an idea?

but i guess, there is nothing i can do, to log in there (without getting a new IP, or logging into another server first...), other than request the deletion of my IP on the hosts.denied on the server...

---

### Post by CharlesA on 2011-03-03
If you have DenyHosts installed, and fail the login a certain number of times, your IP gets blacklisted.

---

### Post by bitwhys on 2011-03-29
I'm working in a mostly windows environment with DNS served up the AD.  The server, best I can tell since I've given enough blood get answers to other questions, is configured to not register unsecure (read: Linux) hosts.  For the most part I get a kick out of it.  DHCP works fine (the box uses a reserved address) and nslookup resolves host names (except for the box I'm on, more amusement) but...

to make sure of things I added the host name of the remote computer I was lining things up for to the /etc/hosts file just to lock things down.

At one point after I had wu-ftpd working fine and dandy while fixing other stuff on a whim I dropped the remote computer's host name from from /etc/hosts since nslookup was working fine and BINGO!...

I could ftp locally but the remote host got kicked out without mercy.

After a while and having confirmed the wu-fptd and open-bsd configuration files where lined up properly more times than I care to admit, the penny dropped and I remembered the /etc/hosts file.  I put a reference to the remote computer back into HOSTS and Bob's your uncle the remote host was able to connect again and reek the havoc for which it was intended.

So

its is possible, as in my case, that inetd is kicking the remote connection out because it's name isn't resolving according the openbsd rules, whatever they are.

Maybe in addition to lining up the wu-ftpd and inetd (or whatever you're working on) allow entries, try dropping a hard code for the problem remote into /etc/hosts before blowing blowing things WFO with /etc/hosts.allow

btw

hi everybody:)

ps. did I say "it's"?  screw it.  I'm on the clock.

---

