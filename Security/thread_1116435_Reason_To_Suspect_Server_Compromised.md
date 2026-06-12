---
title: "Reason To Suspect Server Compromised"
date: 2009-04-04
forum: Security
---

### Post by Ubuntification on 2009-04-04
Hello all,

Here is my attempt to make a long story short:

I am away at college but I run a server at home. Recently my dad informed me that the server's hub was blinking more than usual. I SSH'D in and looked around. When running 'top' I found two instances of SSHD - and one was running as root! In addition 'top' showed that root was running 'dd'. This greatly concerns me. It seems to indicate that my server has been compromised, someone has root access, and they are cloning my entire drive.

I ran 'sudo netstat > netstat.txt' to investigate any active connections and then halted the machine.

What makes matters worse is that my parents run a business out of the house and the attacker may have used my server to attack other computers on my home network. I've informed my dad of the entire situation.

My question is twofold. One, is there any other explanation for root showing sshd and dd running besides a compromised machine? Two, what are recommended courses of action? All other machines on the network have kept up with updates. I'm planning on keeping the server off until I go home in a week at which time I will investigate (with the ethernet cable unplugged!) and then reformat the drive and reinstall. I also plan on "hardening" the machine before bringing it back on-line.

Any input?

---

### Post by kreggz on 2009-04-04
I recommend you:

1. Disconnect the server from the network
2. Troll through your server's /var/log/auth* files
3. Backup your files to a dvd
3. Rebuild the server
4. Change ALL passwords to everything on the network
5. Investigate using certificates with your SSH server and better passwords.

If your running a business through this then it is better to be safe than sorry.

ps I run a SSH server but no DD command has ever been issued. It is likely that if your system has been broken into that they used a dictionary attack meaning your password was weak.

---

### Post by hyper_ch on 2009-04-05
if in doubt, resetup your server.

---

### Post by brian_p on 2009-04-05
> **Ubuntification said:**
> 

I am away at college but I run a server at home. Recently my dad informed me that the server's hub was blinking more than usual.

Blinking LEDs do not a break in make.

> I SSH'D in and looked around. When running 'top' I found two instances of SSHD - and one was running as root!

For sshd to function properly it usually runs as root. The exact output of the command you ran would have been useful.

> In addition 'top' showed that root was running 'dd'. This greatly concerns me. It seems to indicate that my server has been compromised, someone has root access, and they are cloning my entire drive.

Pass. The exact command being executed might have allowed an opinion. You would have to look at what you have running on your machine to assess this.

If sshd is the only service offered you would have had to have set it up very insecurely for unauthorised access to have taken place.

> I ran 'sudo netstat > netstat.txt' to investigate any active connections and then halted the machine.

Did it indicate anything alarming?

>  . . . . .  at which time I will investigate (with the ethernet cable unplugged!) and then reformat the drive and reinstall.

Why reinstall if your investigations provide no evidence to do so?

---

### Post by Ubuntification on 2009-04-05
> **kreggz said:**
> I recommend you:

This seems to match what I was thinking of doing. Didn't know about the /var/log/auth log files though, so thank you. Are these the only files that might help me determine if security was compromised?

> **kreggz said:**
> It is likely that if your system has been broken into that they used a dictionary attack meaning your password was weak.

My password was 17 characters alphanumeric. I don't think a dictionary or brute force attack is feasible.

> **brian_p said:**
> The exact output of the command you ran would have been useful.

I'll be able to provide this when I have physical access to the server.

> **brian_p said:**
> If sshd is the only service offered you would have had to have set it up very insecurely for unauthorised access to have taken place.

sshd was not the only service running. There were several, some of which were in beta form. I'm guessing one of them had a security hole which allowed an attacker to install a rootkit or back-door.

> **brian_p said:**
> Did it indicate anything alarming?

Not that I can tell. Unfortunately the server was a node on the tor network and therefore there are many connections to random hosts in foreign countries. When I can I will bring the server back on-line briefly, shutdown tor, and then run netstat again.

> **brian_p said:**
> Why reinstall if your investigations provide no evidence to do so?

I would rather error on the safe side. A two to three hour re-install is far less of a hassle then the potential consequences of running a compromised machine.

---

### Post by hyper_ch on 2009-04-05
brian_p:

actually if you suspect your system has been compromised the only thing you can do is to reinstall it as you can't trust it anymore.

---

### Post by kreggz on 2009-04-05
hyper_ch - I agree

---

### Post by brian_p on 2009-04-05
> **Ubuntification said:**
> 

sshd was not the only service running. There were several, some of which were in beta form. I'm guessing one of them had a security hole which allowed an attacker to install a rootkit or back-door.

Apart from sshd (which you don't see as a possible cause) they'll be disappearing from your hard disk then. Having a look at their security track records wouldn't do any harm.

> I would rather error on the safe side. A two to three hour re-install is far less of a hassle then the potential consequences of running a compromised machine.

If you cannot be sure of what evidence to look for or what it is telling you or whether it is reliable (logs can be altered), classing the machine as compromised may be the only option left to you.

---

### Post by brian_p on 2009-04-05
> **hyper_ch said:**
> 

actually if you suspect your system has been compromised the only thing you can do is to reinstall it as you can't trust it anymore.

Having solid grounds for the suspicion would be nice.

---

### Post by hyper_ch on 2009-04-06
that's the difference between suspicion and proof :) as said, on a compromised computer you can't trust anything.

---

### Post by brian_p on 2009-04-06
> **hyper_ch said:**
> that's the difference between suspicion and proof :) as said, on a compromised computer you can't trust anything.

Rapidly flashing lights on a router are not the best indicator of a compromised machine.

---

### Post by hyper_ch on 2009-04-06
that's why there's the "if in doubt re-setup the machine"-doctrine :)

---

### Post by brian_p on 2009-04-06
> **hyper_ch said:**
> that's why there's the "if in doubt re-setup the machine"-doctrine :)

Ah, I see. Lights flash rapidly, mouse pointer twitches unexpectedly, fonts disappear from a dialogue box. The user concludes 'This is unusual, I think I could have been compromised' and, working on such a slim doubt, goes on to reinstall the OS. I'd see that as extreme but it is his machine after all.

---

### Post by kpatz on 2009-04-06
sshd running as root doesn't indicate a break-in.  Here's an example while I'm ssh'd into one of my boxes:

> kpatz@zuul:~$ ps -ef | grep ssh
root      5302     1  0 Mar01 ?        00:00:00 /usr/sbin/sshd
root     30257  5302  0 07:34 ?        00:00:00 sshd: kpatz [priv]
kpatz    30259 30257  0 07:34 ?        00:00:00 sshd: kpatz@pts/0
kpatz    30386 30261  0 07:35 pts/0    00:00:00 grep ssh
kpatz@zuul:~$

PID 5302 is the sshd daemon that listens for connections.  It runs as root, in order to bind to a privileged port (22).  PID 30257 also runs as root, and provides my ssh connection, which runs under my id (PID 30259).

The dd command... did it look like this (ps -ef | grep dd)

> 
root      5184     1  0 Mar01 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg


Some sort of kernel logging process set up by init.  Not indicative of a break-in.

---

### Post by hyper_ch on 2009-04-06
> **brian_p said:**
> Ah, I see. Lights flash rapidly, mouse pointer twitches unexpectedly, fonts disappear from a dialogue box. The user concludes 'This is unusual, I think I could have been compromised' and, working on such a slim doubt, goes on to reinstall the OS. I'd see that as extreme but it is his machine after all.

exactely

---

### Post by cdenley on 2009-04-06
As for flashing lights, you said you were running your server as a tor node. You were willingly allowing anonymous users to download whatever they wish using your computer network. Why would you be surprised when remote users start transferring large amounts of data through your network?

---

### Post by brian_p on 2009-04-06
> **kpatz said:**
> 

```
root 5184 1 0 Mar01 ? 00:00:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
```

The dd command is run from /etc/init.d/klogd. I agree; not suspicious at all.

---

### Post by Ubuntification on 2009-04-06
> **kpatz said:**
> sshd running as root doesn't indicate a break-in.  
Here's an example while I'm ssh'd into one of my boxes...

Some sort of kernel logging process set up by init.  Not indicative of a break-in.

Thank you. This is what I was asking here; is there any other reason dd would be running as root? Since there is, and since sshd also runs as root I am no longer concerned. I will still inspect the machine in detail (chrootkit, log files) just to be sure. 

> **brian_p said:**
> Rapidly flashing lights on a router are not the best indicator of a compromised machine.

I never said that the flashing lights on the router were the reason I was concerned. The fact that the hub was blinking a lot when nothing was running just prompted me to look around. Seeing root running sshd and dd caused me concern and I came to the forums to check if there was a valid reason for this other than a break-in. Apparently there is.

> **brian_p said:**
> If you cannot be sure of what evidence to look for or what it is telling you or whether it is reliable (logs can be altered), classing the machine as compromised may be the only option left to you.

That is why I came here for advice rather than just pulling the trigger on the machine...

> **cdenley said:**
> As for flashing lights, you said you were running your server as a tor node. You were willingly allowing anonymous users to download whatever they wish using your computer network. Why would you be surprised when remote users start transferring large amounts of data through your network?

I probably should have made this more clear, but a cron job starts the server every night and stops it every morning. I don't need the bandwidth in the middle of the night. When the hub was originally blinking it was the middle of the day and tor was not running. 

When investigating the suspected break-in I did a reboot. Since tor starts automatically and I forgot to stop it before running netstat, there were connections due to tor listed.

---

### Post by kpatz on 2009-04-08
Mysterious blinking lights on the LAN side of a hub/switch/router could be caused by ARP packets too.

One night I noticed my switch was showing activity on all ports (broadcast packets) every few seconds, even though all my machines were idle at the time (Windows machines powered off, Linux machines running but idle).  I was curious so I logged into one of the machines and ran tcpdump, and found ARP packets going over the wire.  Zuul (one of my 'buntu boxes) was looking for Stalkerii (one of my 'doze boxes).  I logged into Zuul and found I had mounted a share on Stalkerii and since I powered it down, Zuul was pinging the network looking for it.  After unmounting the share the ARP packets stopped.

---

### Post by Ubuntification on 2009-04-13
I've finally made it home and inspected all of the logs. It turns out that when I was notified the hub was blinking a lot, someone in Russia was attempting to brute-force my SSH password. I can see the attack was in progress when I logged in remotely to investigate. I know it isn't unusual to have somebody try to brute-force your server and I'm not concerned that they could/will succeed due to the strength of my password.

> **brian_p said:**
> Rapidly flashing lights on a router are not the best indicator of a compromised machine.

I agree. How much of a coincidence this was can be debated, but the unusual amount of traffic (hence blinking) in this particular instance actually was an indicator that something suspicious was going on. I stand by my original assessment that unusual network activity is something worth at least looking into. I'd rather error on the paranoid side than the incautious.

> **kpatz said:**
> Mysterious blinking lights on the LAN side of a hub/switch/router could be caused by ARP packets too.

I logged into Zuul and found I had mounted a share on Stalkerii and since I powered it down, Zuul was pinging the network looking for it.  After unmounting the share the ARP packets stopped.

Interesting. I have shares on several computers here, many of which are not always online. I imagine this might cause some of the "phantom" activity I see sometimes.


Thanks for the help everyone, I'm glad I don't have to do a re-install.

---

### Post by sloggerkhan on 2009-04-13
I run sshd on my home server. On a typical day I have 1 - 3 login attempts from extraneous sources. However, I run denyhosts on my server and they get blocked.

You should probably denyhosts or fail2ban on yours.

---

