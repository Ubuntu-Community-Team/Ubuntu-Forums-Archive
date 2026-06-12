---
title: "Persistant unauthorized login attempts on my server"
date: 2007-05-20
forum: Server Platforms
---

### Post by FastZ on 2007-05-20
Hey folks.  I have a home server running on Fiesty and I use it to host all of my digital music and a few videos and some other files and things that I share across my LAN and to a few of my friends on the other side of the internet.  Every so often, I will check out the sys logs and find that there have been hundreds of login attempts made from a number of IP addresses coming from out across the internet, and none of them are ones that I recognize.  The ports I have open on my server are 22, 23, 8888 and 6996, that I use for various things.  With Firestarter (I installed Ubuntu-Desktop on this server) I created a rule for these ports that only connections from inside my LAN were authorized.  22 is used for SSH and when connecting to my server via another computer, you're asked for a password.  SSH is the sole service I see on the logs for unauthorized login attempts.  Is there any way that I can keep these people from trying to crack my SSH login information and gain access to this server?  Without taking the server offline, because I share files with friends and with myself when I have my laptop and I'm out somewhere using someone else's connection.  

I have port 22 forwarded on my Linksys router to the server computer.  Since I only access port 22 on that computer from other computers on my LAN, can I unforward that and still be able to access that port from a computer on my LAN?  If that doesn't make sense, let me know and I'll try to clear it up some.

---

### Post by tturrisi on 2007-05-20
config the sshd to use a port such as 3022 & forward 3022 in the router.
Port 22 is a common port and kiddies will scan ranges of ip address to see if 22 shows up anywhere.
If you use port 3022 instead the router will not respond to port 22 requests and thus the kiddies will likely give up.
I use port 3022 for ssh and rarely if ever get attempted break ins.

---

### Post by FastZ on 2007-05-21
I had thought about doing that before.  I don't remember why I never actually followed through on it.  I will give that a shot and see if anything changes.  Hopefully everything takes a turn for the better.  Thanks for the help.

---

### Post by MJN on 2007-05-21
> **FastZ said:**
> I have port 22 forwarded on my Linksys router to the server computer. Since I only access port 22 on that computer from other computers on my LAN, can I unforward that and still be able to access that port from a computer on my LAN?
 
Yes, as long as when you're accessing your server the LAN you're using its internal IP addresses as opposed to the WAN address of the router.
 
If you did want to leave a standard port 22 forwarded from the router take a look at something like Fail2ban and use decent passwords (or public/private keys if not too inconvenient).
 
Mathew

---

### Post by hartz on 2007-05-21
Some suggestions on how to make your ssh server more secure:
1: Change the listening port as suggested earlier.  There is an option in the /etc/ssh/sshd_config file for this.
2: Disallow root login.  (option in the same file)
3: Disallow password authentication (option in the same file).  This way only users with known and trusted keys are authenticated.  For this to work, your users need to each generate a public/private key pair and put the public key into a file in their home directory.  The file in each user's home directory is .ssh/authorized_hosts

You need to sighup the sshd process for this to take effect.  You can run one of these commands (in a terminal):

```
sudo killall -HUP sshd
```

or

```
sudo /etc/init.d/ssh restart
```

Note: remember to backup system config files before making changes.

---

### Post by rich.bradshaw on 2007-05-21
sudo apt-get install fail2ban

bans people who get the password wrong 5 times in a row for 5 mins.

---

### Post by FastZ on 2007-05-21
I changed the port that SSH uses and disabled the root login capability.  I will download and install Fail2Ban this evening and work with that some.  Thanks again for all the suggestions guys.  I really appreciate it.

---

### Post by DrNick on 2007-05-21
If you don't access your server from any machine on the internet, you could just take the port forward out altogether...

---

### Post by random_mike on 2007-05-21
I use above and
[http://freshmeat.net/projects/ssh-faker/](http://freshmeat.net/projects/ssh-faker/)

---

### Post by FastZ on 2007-05-21
> **DrNick said:**
> If you don't access your server from any machine on the internet, you could just take the port forward out altogether...
 
That was one of my questions in my original post.  I dont SSH into my server from across the internet, only from within my LAN.  However, I will sometimes use FileZilla to connect to the server using SFTP over SSH, and I do so from outside of my LAN at times to upload and download files onto my laptop when I'm not at home.  In order to use SFTP over SSH, would I still need to forward that SSH port on the router for that to continue to work correctly?

---

### Post by Cheese Sandwich on 2007-05-21
> **FastZ said:**
> I will check out the sys logs and find that there have been hundreds of login attempts...

Novice here - which particular files are these?

---

### Post by DrNick on 2007-05-21
Yes, I would say you would need to keep the port forward in that case.  Using one of the other suggestions would be your best option now...

---

### Post by Ramses de Norre on 2007-05-21
Look into denyhosts too, I think it does the same as fail2ban and I find it really easy to configure.

---

### Post by FastZ on 2007-05-21
> **Cheese Sandwich said:**
> Novice here - which particular files are these?

/var/log is where they are.  You can go to System>Administration>System Log and that will show you all the logs in your /var/log directory in a central window.  And the sshd logs are included in auth.log.

do
```

cat /var/log/auth.log | grep sshd | less[FONT=Tahoma,Sans,Arial,Helvetica,sans-serif]
```
and that will bring up just those logs from sshd that are in the auth.log file.
[/FONT]

---

### Post by Cheese Sandwich on 2007-05-21
> **FastZ said:**
> /var/log is where they are.  You can go to System>Administration>System Log and that will show you all the logs in your /var/log directory in a central window.  And the sshd logs are included in auth.log.

do
```

cat /var/log/auth.log | grep sshd | less[FONT=Tahoma,Sans,Arial,Helvetica,sans-serif]
```
and that will bring up just those logs from sshd that are in the auth.log file.
[/FONT]

Got it, thanks.

---

### Post by MJN on 2007-05-22
> **Ramses de Norre said:**
> Look into denyhosts too, I think it does the same as fail2ban and I find it really easy to configure.

A bit more tricky (verging on pulling-your-hair-out-tricky) to get an IP pulled out of the blacklists though if you need it to.

Mathew

---

### Post by Ramses de Norre on 2007-05-22
> **MJN said:**
> A bit more tricky (verging on pulling-your-hair-out-tricky) to get an IP pulled out of the blacklists though if you need it to.

Mathew

It puts blocked ip's in hosts.deny and that's all... If you remove that ip from that file again, you can login from it like before. I never personally had troubles with it but I never tried fail2ban neither so I don't know which is the best, denyhosts just works like I want for me ;)

---

### Post by MJN on 2007-05-22
> **Ramses de Norre said:**
> It puts blocked ip's in hosts.deny and that's all... If you remove that ip from that file again, you can login from it like before. I never personally had troubles with it but I never tried fail2ban neither so I don't know which is the best, denyhosts just works like I want for me ;)
 
If you remove the IP from hosts.deny it'll just put it back in again on the next iteration. You need to remove them (or reset the failure counter) from the Denyhosts working files, of which there are several (hosts-* and users-*) each keeping an eye on different aspects (e.g. valid users, invalid users, root, ip, etc).
 
Try it - it's a real pain! (and when you've got slack-handed users screwing up their logins...)
 
Don't get me wrong, I do like Denyhosts (other than this aspect) and it does what it says on the tin (I also like the sharing ability of offenders), but I think the Fail2ban model is more elegant - I'm very much of the 'keep it simple, stupid' mentality!
 
Mathew

---

### Post by Ramses de Norre on 2007-05-23
Strange, I can't remember having to do so, but it's been a while since someone legitimate  got itself denied. Maybe I'll need to have a look at fail2ban before I get into those troubles though :)

---

### Post by Chayak on 2007-05-23
Welcome to the internet :D

It's a daily occurrence to see port scans and login attempts from bots and skiddies.  We changed the default ports for access and had good results.

---

