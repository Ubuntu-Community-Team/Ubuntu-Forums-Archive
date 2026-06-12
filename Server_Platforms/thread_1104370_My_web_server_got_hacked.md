---
title: "My web server got hacked"
date: 2009-03-23
forum: Server Platforms
---

### Post by Johnsie on 2009-03-23
When I logged into my ssh it said the last user to access the system was from a strange isp that I don't use. That isp doesn't appear on the logs, I'm assuming he/she modified the logs. I've disconnected the system and am looking at ways to tighten the security and check for any back doors they may have installed. Any advice would be much appreciated. I'm also curious if there is a way to make a shell script be executed any time someone logs in. I have a shell script here that will email send me but I need a way to execute it at login.

---

### Post by Bachstelze on 2009-03-23
Use a strong password or (even better) key-based authentication.

---

### Post by Johnsie on 2009-03-23
they logged in with the username 'root'. Is that the same password that I have for my username? Is there a way of changing the pasdsword for the root username?

---

### Post by volkswagner on 2009-03-23
to change the root password.
```
sudo passwd root
```

Don't forget the new password.

You can also setup hosts.deny and hosts.allow, if you set up limited ip address's in the allow file, it will help.

There is also failtoban.

---

### Post by Chemical Imbalance on 2009-03-23
> **volkswagner said:**
> to change the root password.
```
sudo passwd root
```

Don't forget the new password.

You can also setup hosts.deny and hosts.allow, if you set up limited ip address's in the allow file, it will help.

There is also failtoban.

+1 failtoban

And ubuntu has a randomized root password that is not accessible to anyone except with sudo by default--unless you specify the password yourself.

---

### Post by MJWitter on 2009-03-23
I don't have much experience with log files and authorisations, but I believe those Last two lines are the server performing scheduled operations(cron) requiring root.  I could be corrected?

Also, unless you have given root a password already and are using Ubuntu surely no-one can log into the server as root?

---

### Post by Johnsie on 2009-03-23
I think it would be best for mme to have a whitelist of trusted ip address. Can anyone explain to me in detail how to do that?


When Ubuntu starts it tells you the last IP to login. The Ip address that came up wasn' one that I reconginise. I only access my server from home and work and this one had a completely different isp.

---

### Post by Bachstelze on 2009-03-23
> **MJWitter said:**
> I don't have much experience with log files and authorisations, but I believe those Last two lines are the server performing scheduled operations(cron) requiring root.  I could be corrected?

Also, unless you have given root a password already and are using Ubuntu surely no-one can log into the server as root?

You are totally right, I guess I should read logs more carefuly. :p

@Johnsie: as MJWitter said, no one logged in in your system. If you look at the last wo lines carefully, you'll see they say "cron" instead of "sshd".

---

### Post by Johnsie on 2009-03-23
Yeah but it said a strange ip was the last user to log in when I logged in. That's what got me looking at the logs in the first place. It came from an isp that I don't use.

---

### Post by hictio on 2009-03-23
Did you enabled root logins over SSH???
Disable those at once! It is the single most dangerous thing to have enabled on a Linux server.
After you do that, setup a handful of users that can connect via SSH, using the directive 'AllowUsers'.

You have to edit the file '/etc/ssh/sshd_config' via sudo and your favorite text editor to make the changes, and after editing the file, issue a:

```

sudo /etc/init.d/sshd reload ENTER

```

---

### Post by Johnsie on 2009-03-23
I'm not sure if it was root they got in as. I'm scouring through the logs and haven't found anything from that ip address yet.

---

### Post by FiberOptix on 2009-03-23
> **Johnsie said:**
> I think it would be best for mme to have a whitelist of trusted ip address. Can anyone explain to me in detail how to do that?


When Ubuntu starts it tells you the last IP to login. The Ip address that came up wasn' one that I reconginise. I only access my server from home and work and this one had a completely different isp.

Your attacker appears to be using a computer from somewhere in asia. A whois lookup reports that the block 222.0.0.0/8 is allocated to APNIC and using traceroute I noticed one addresses just a few hops downstream resolved to a ".cn" (as in China) address.

---

### Post by Johnsie on 2009-03-23
unfortunately th offender was not from that ip address. I'm going to take that log down from my original post. The last ip to log in was using an ISP in the UK (bethere.co.uk). However there doesn'tseem to be anything from that ip in my logs.

---

### Post by FiberOptix on 2009-03-23
> **Johnsie said:**
> I'm not sure if it was root they got in as. I'm scouring through the logs and haven't found anything from that ip address yet.

Judging by the log you posted it looks very likely that it was the root account that was compromised. You should also assume that your log files have been tampered with. Check .bash_history for root as well as the usual /var/log entries.

---

### Post by Johnsie on 2009-03-23
Is there any way I can make my system email me or execute a shell script as soon as someone logs in?

---

### Post by hictio on 2009-03-23
Not sure if this is what you want or not, but it worked for me :)
I had a problem like that, I wanted to know when someone logged in, or tried to, via SSH to a server, so I have setup this on using TCP Wrappers, this snip was from the '/etc/hosts.allow':

```

## Logs all SSH attempts / connections  
 
sshd: xxx.xxx.xxx.xxxx/xxx.xxx.xxx.xxx : \ 
spawn (echo Access from %h to %d on `date` \ 
 | tee -a /var/log/sshd_connections.log \ 
 | mail -s "SSH attempt at serverXXXX" someusername@somedomain.something

```

On the '/etc/hosts.deny' there was a total block. Of course, you have to add the file '/var/log/sshd_connections.log' and you must have already enabled the server so it can send emails.

As usual, double and triple check for typos before editing the files '/etc/hosts.allow' & '/etc/hosts.deny'; specially if you only have remote access to the given server.

---

### Post by BkkBonanza on 2009-03-23
I would also find and run the chkrootkit script or similar to see if the person who logged in installed a "root kit". You don't want to go live again and then find out they did that and have already got ways back in. After all, if I were intent on doing this kinda thing I'd have already set up a way to return.

Also it's easy to add a scripted line to your .bashrc so that anyone logging in would trigger some action like an email. That will work until they remove it but first time they shouldn't have that option.

And definitely disable root logins in ssh. I always change the ssh port as well so that you rarely ever get people knocking at the door even. You just need to edit sshd_config for that. Use some high number. I found that instead of a continuous stream of hits by scanners on port 22 I was then rarely ever hit. For one thing it tells people that you at least have thought about security.

---

### Post by gtfourdreams on 2009-04-07
I hate to bring back up an old topic, but try this: [http://freshmeat.net/projects/ssh-faker/](http://freshmeat.net/projects/ssh-faker/)

> 
SSH-Faker
Ssh-faker is a wrapper for sshd to defeat brute force hacking. This program is meant to be called from /etc/hosts.deny when anyone connects to port 22 (ssh). If the person doesn't send a plaintext password (using telnet), the attempt is logged and the connection is dropped. If they send the right password, they are added to /etc/hosts.allow, and their next attempt will reach the real sshd. This will block most hackers and worms, assuming none of the computers listed in /etc/hosts.allow have been compromised. 


i had some random IP's (a couple from nigeria and a couple from china) trying to SSH into my computer using random usernames.  it got so bad that my hdd was clicking for hours at a time, writing the failed attempts into syslog. anyways, because there are only a few users who use the system, i just set up ssh-faker and now its quiet. im sure they are still trying, but ssh-faker will auto disconnect them unless they type in the correct access code. works for me, good luck.

---

### Post by dguitar on 2009-04-07
Also just to add, if this comes up in search or something. 

Some painful information:

You need to FIRST unplug your machine, find out how they got in (or hire someone to find it out for you) and then fix that. Lastly you need to **rebuild your server**. Yes you heard me correctly, you will need to reinstall the OS. You have no idea what the person did. They could have replaced LS so that every time you run it, it shows you the files, and also phones home to tell you. There are some many options of things they can do, it's endless. Rootkits are great, but it can't guarantee the box isn't doing something nasty behind your back.

---

