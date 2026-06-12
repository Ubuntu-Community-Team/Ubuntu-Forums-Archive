---
title: "System hacked via ssh"
date: 2007-04-06
forum: Server Platforms
---

### Post by jonberling on 2007-04-06
Hello everyone,

I installed a fresh copy of Ubuntu 6.10 desktop. The only servers I installed were ssh and sftp (using Synaptic), I edited the ssh server so root can't log on. I also configured my firewall (a lynksys router) so that only port 22 gets forwarded to my linux box. 

Now I can't log into root. Someone changed the password. I checked /var/log/ and the auth files are pretty big.
[INDENT]
[FONT="Lucida Console"]
jonathan@realm:/var/log$ ls -l | grep auth
-rw-r----- 1 root adm   691133 2007-04-06 20:17 auth.log
-rw-r----- 1 root adm  1199472 2007-04-04 07:30 auth.log.0
-rw-r----- 1 root adm     8255 2007-03-31 07:30 auth.log.1.gz[/FONT]
[/INDENT]

Most of them come from the same few IP address. I'm going to reinstall Ubuntu (because I'm not skilled enough to find out what they did with root). I need ssh and sftp because I need to be able to log in from school.

Is there a way to keep this from happening? I thought I was safe by not allowing anyone  to log on as root via ssh, but I guess they hacked my account and then got root.

Any help would be greatly appreciated.

Thanks,
Jonathan

---

### Post by falcon15500 on 2007-04-07
Wow.  That really sucks!  Feel for you.  Really, re-installing from scratch (again) is your best option.  There's no telling what was changed or modified or overwritten by the intruder(s).  Fresh install covers that.  What is of concern is that they were able to penetrate at all in the first place.  A couple of suggestions:

1)  Double-check your SSH setup - perhaps use keys rather than password?
2)  Run SSHD on a non-standard port.  You will need to change the port you are forwarding on your router too. (I personally am not big on this one - as I feel it is an attempt at security through obscurity.  However, some people swear by it and it _will_ reduce the number of successful port scans you get.)

falc

---

### Post by yellowtip on 2007-04-07
Sorry to hear about your security breach. I know how bad this sucks.

I'm also quite paranoid about this happening to my servers, so hopefully this will become an interesting thread with some good security tips.

Some basic measures I take are:
1. Disable direct root login via SSH
2. Change the default SSH port from 22 to something else (like 2213)
3. Install IPKungfu and make sure only those ports are open that need to be open
4. I know this sounds obvious, but use different secure passwords for your accounts
5. Keep my ssh server up to date

Would love to hear about other security measures... as I'm absolutely no security expert.

---

### Post by weresheep on 2007-04-07
Hello,

Sorry to hear about your situation. One thing I would add that hasn't been mentioned is to install fail2ban (after you've done a fresh install of course)...

"sudo apt-get install fail2ban"

It monitors the auth.log for failed login attemps and after 5 failures it adds an entry into your firewall rules to ban the offending IP address for 10 minutes. Both the number of failures and the ban time are configurable. I used to see IP addresses making hundreds of login attempts until I installed fail2ban. Now, they only ever get a few before they get locked out.

fail2ban logs (/var/log/fail2ban.log) when it bans and unbans addresses so its easy to see  who has been naughty :) There are other programs out there that do similar things to fail2ban so do a search to find one that suits your needs.

In gerneral, as others have said...

1) disable root logins (sounds like you did this anyway)

2) make sure only SSH protocol version 2 is in use.

3) set AllowUsers in sshd_config to contain only the usersname(s) you want to allow ssh access to.

4) switch to key only access (if practical)

5)  use *strong* passwords.

6) install fail2ban (or other failure monitoring/banning program)

There are plenty of threads about SSH security but the above are the main points I've learned. Good luck.

-weresheep

---

### Post by shawnerz on 2007-04-07
Wow!  That really sucks.  I use ssh to get back to my home linux box from my job.

I have ssh on the default (22) port and I was getting a lot of login attemps as well.  For me, it seemed to be coming from "bots" located on a certian ISP in Austraila.  The IP address was probably spoofed.

Here are three suggestions that work for me:
1: Disable the root account.  I haven't had a need to enable it so it's been working for me.
2: Configure your router so it does not respond to pings.
3: Install a software firewall.  I installed firestarter ([http://www.fs-security.com/docs/wizard.php](http://www.fs-security.com/docs/wizard.php)) [(apt-get install firestarter) - if the Repositories option is enabled in Synaptic Package Manager].  In the IMCP section, disable Pings.  My auth.log files shrank dramatically since my system wasn't being hacked.
Good luck,
-Shawn

---

### Post by weresheep on 2007-04-07
Hi shawnerz,

If your set up works for you then thats great, however I personally don't like things like not responding to ping (or indeed moving the default port as others suggested).

I can understand why people do it, but ultimately I think security through obscurity isn't the way to go. These techniques may help keep logs clear of automated dictionary attacks but wont really help against a serious attack. I think its better to have a system that reacts to an attack and puts a stop to it, rather than one that quietly sits there and hopes not to get noticed. Of course, you could always combine the two schools of thought (i.e. install fail2ban as well as not responding to ping) but I just don't think hiding your machine buys you much protection.

In the six months I've had my spare machine online with SSH open to the internet, it's had maybe 7,000 login attemps. The most in one day was about 1,500 (all from the same address). Most made around 100 attemps using a variety of user names, but mainly 'root'. Funny thing, my actual username has never been tried, not once :-D

Since I installed fail2ban no IP address has been able to make more than 6 login attemps before it was banned. The odds of someone being able to guess my password in 6 attemps are astronomically stacking in my favour.

Still, I am a n00b myself and still learning stuff all the time so maybe theres some extra benefits to these techniques I am not aware of :)

-weresheep

---

### Post by marcosXL on 2007-04-07
Hello everyone,

I installed a fresh copy of Ubuntu 6.10 desktop. The only servers I installed were ssh and sftp (using Synaptic), [COLOR="Blue"]I edited the ssh server so root can't log on[/COLOR]. I also configured my firewall (a lynksys router) so that only port 22 gets forwarded to my linux box. 
[COLOR="Blue"][U]
Now I can't log into root[/U][/COLOR]. Someone changed the password. I checked /var/log/ and the auth files are pretty big.



changing the root passward is common what ever distribution it is, to
change the root passsward... while boot menu comes edit the menu and
go to the label and go to the end of the line and give 1 or init 1.
then press the b to boot once it come to prompt(sh# shell) type
passwd, it will ask for new passward give as u wish
  

               Good Luck!!

---

### Post by az on 2007-04-07
> **jonberling said:**
> Hello everyone,

I installed a fresh copy of Ubuntu 6.10 desktop. The only servers I installed were ssh and sftp (using Synaptic), I edited the ssh server so root can't log on. I also configured my firewall (a lynksys router) so that only port 22 gets forwarded to my linux box. 

Now I can't log into root. Someone changed the password. I checked /var/log/ and the auth files are pretty big.
[INDENT]
[FONT="Lucida Console"]
jonathan@realm:/var/log$ ls -l | grep auth
-rw-r----- 1 root adm   691133 2007-04-06 20:17 auth.log
-rw-r----- 1 root adm  1199472 2007-04-04 07:30 auth.log.0
-rw-r----- 1 root adm     8255 2007-03-31 07:30 auth.log.1.gz[/FONT]
[/INDENT]

Most of them come from the same few IP address. I'm going to reinstall Ubuntu (because I'm not skilled enough to find out what they did with root). I need ssh and sftp because I need to be able to log in from school.

Is there a way to keep this from happening? I thought I was safe by not allowing anyone  to log on as root via ssh, but I guess they hacked my account and then got root.

Any help would be greatly appreciated.

Thanks,
Jonathan

You should really find out if someone actually compromised your system or if you just made a typo when you changed the password.  Much of the auth.log is system activity (cron jobds and so forth).  Just because the auth.log is big doesn't mean anything.

The only two things you should do is to pick a strong password and restrict anyone from logging in via ssh from any IP address other than your school.  Why even have an active root acount?  Root is dissabled by deafult on a stock ubuntu.

---

### Post by jonberling on 2007-04-08
Thanks everyone for the help. Changing the port number is a good idea, but in my case I need it running on the standard port. fail2ban sounds good. I think I'll use it. Also, I'm 100% sure someone hacked my computer. I hadn't changed the password in a while.

---

### Post by Mr_Mischif on 2007-04-08
> **jonberling said:**
> Hello everyone,

I installed a fresh copy of Ubuntu 6.10 desktop. The only servers I installed were ssh and sftp (using Synaptic), I edited the ssh server so root can't log on. I also configured my firewall (a lynksys router) so that only port 22 gets forwarded to my linux box. 

Now I can't log into root. Someone changed the password. I checked /var/log/ and the auth files are pretty big.
[INDENT]
[FONT="Lucida Console"]
jonathan@realm:/var/log$ ls -l | grep auth
-rw-r----- 1 root adm   691133 2007-04-06 20:17 auth.log
-rw-r----- 1 root adm  1199472 2007-04-04 07:30 auth.log.0
-rw-r----- 1 root adm     8255 2007-03-31 07:30 auth.log.1.gz[/FONT]
[/INDENT]

Most of them come from the same few IP address. I'm going to reinstall Ubuntu (because I'm not skilled enough to find out what they did with root). I need ssh and sftp because I need to be able to log in from school.

Is there a way to keep this from happening? I thought I was safe by not allowing anyone  to log on as root via ssh, but I guess they hacked my account and then got root.

Any help would be greatly appreciated.

Thanks,
Jonathan

Hold on a second, I thought root was disabled by default in Eft. And if you enabled it, why? You should be able to do anything under sudo which you can do as root. Unless I'm missing something, which I probably am...

---

### Post by tr333 on 2007-04-09
you might want to take a look at [https://help.ubuntu.com/community/AdvancedOpenSSH]("https://help.ubuntu.com/community/AdvancedOpenSSH") which is Ubuntu Documentation page on how to increase the security of your SSH install.

---

### Post by mgmiller on 2007-04-09
WOW!  I often have brute force ssh attacks against my machine, but with root disabled, they never get past many failed login attempts.  While I was reading this post I brought up my system log and watched as attempt after attempt was made every 2 seconds or so.  I then installed fail2ban and ran the command "fail2ban" in a terminal.  They instantly stopped.  I now get a "fatal: timeout before authentication" about every 2 mins.  They all seem to be coming from the same IP address, I thought it would just block the IP after 5 failed attempts, but it seems to only be blocking the name.  

:lolflag: 
OK,  when all else fails, READ THE MANUAL,  or in this case man fail2ban.
I needed to run it with the command "fail2ban -b".
That was the end for any attempted logins.  It totally stopped.

Very cool.  thank you!

---

### Post by zarg@henrikke on 2007-04-10
> **jonberling said:**
> 
Is there a way to keep this from happening? I thought I was safe by not allowing anyone  to log on as root via ssh, but I guess they hacked my account and then got root.


Yes,

you can use SSH via DSA/RSA authentication, for example when using rsync over SSH I used

[FONT="Courier New"]#ssh-keygen -t rsa -b 1024 -f my-rsync-key[/FONT]

to generate my SSH key and placed the public key on the server. **IF** you now turn off password based SSH logins, no one can break in, without your private RSA key. \\:D/ 


A while back I asked for a way to automaticly ban IP adresses which tried to brute-force SSH passwords, a couple of blooted python packages where suggested, which didn't appeal to me. The best solution I have figured out so far, is to use the built-in **ipt_recent** module. If you run

[FONT="Courier New"]
#!/bin/bash
# Block SSH brute-force attacks
iptables -A INPUT -p tcp --dport ssh -m state --state NEW -m recent --set --name SSHBLOCK -j ACCEPT
iptables -A INPUT -p tcp --dport ssh -m recent --update --seconds 600 --hitcount 4 --rttl --name SSHBLOCK -j DROP
[/FONT]

as root (or via sudo), you only allow 3 SSH login attempts per 10 minutes. I haven't tested the above with FTP blocking as well, possibly changing **--dport ssh** to **--dport ftp:ssh** will do the magic, if not.. just add two more lines with **--dport ftp**.

Besides, I have the same advice as **weresheep**, except his 6) using fail2ban...

---

### Post by az on 2007-04-10
Unless you have an extremely easy root password, I reckon it is far more likely that someone standing right behind you will steal your password and compromise your box rather than a remote brute force attack. The OP SSHes from school, right?

---

### Post by hasimir44 on 2007-06-04
I'm glad I saw this post.. it's an eye opener. I checked my auth.log and low and behold an ip from china has been attempting to brute force through ssh on my box for that last few days.. 

here's the *bad guy* ip (maybe just a compromised box):   221.232.160.217

They have way more ports open than I do.. 
```
arymcdo@basebox:/var/log> sudo nmap -sS 221.232.160.217
Password:

Starting Nmap 4.10 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2007-06-04 16:59 PDT
Stats: 0:00:28 elapsed; 0 hosts completed (1 up), 1 undergoing SYN Stealth Scan
SYN Stealth Scan Timing: About 29.76% done; ETC: 17:00 (0:00:59 remaining)
Interesting ports on 221.232.160.217:
Not shown: 1668 closed ports
PORT     STATE    SERVICE
21/tcp   open     ftp
22/tcp   open     ssh
80/tcp   open     http
111/tcp  open     rpcbind
135/tcp  filtered msrpc
136/tcp  filtered profile
137/tcp  filtered netbios-ns
138/tcp  filtered netbios-dgm
139/tcp  filtered netbios-ssn
445/tcp  filtered microsoft-ds
8080/tcp open     http-proxy

Nmap finished: 1 IP address (1 host up) scanned in 112.477 seconds
```

you can use nmap to scan yourself as well (has tons of options): 

```
nmap -sS localhost
```

I'm going to move sshd to a different port. I had to do the same for vsftpd a while back..

---

### Post by Chayak on 2007-06-05
A lot of tips have already been mentioned here but one I personally use from my laptop to my home systems is hamatchi.  I have a host.deny file blocking everything and the host.allow only lists my laptop hamatchi address.  I use a very long random string as my hamatchi password that I pasted from a text file kept on my USB key.

---

### Post by russell.h on 2007-06-05
I rather like the idea of not allowing login at all from any computer not at your school. If your school is anything like mine then every computer in the school will have the same external IP, so that should be fairly easy.

---

