---
title: "How to set sepetate password for 'sudo' and regular 'user account'?"
date: 2010-12-31
forum: Security
---

### Post by s.a.patil on 2010-12-31
Respected Members, I searched through forms and didn't find good answer for my question, I also googled around and didn't find any satisfactory answer either, So I'm posting the message here.
I'm the lone user of my Ubuntu 10.4.1 computer and very paranoid about security, for this reason I have installed Bit Defender anti virus on my Ubuntu 10.4.1 installation, and configured 'UFW' to deny in-coming traffic (Yes I know it is default). After setting my 'sudo' password to some difficult combination I made further research to secure my installation. From Ubuntu Help I learnt that by default 'root' account is disabled and one has to use 'sudo' command by giving his user account password to elevate the privilege. In my opinion this is the best method as no one can do any harm to my computer as the 'root' account is disabled. But this give rise to question that if any one is able to hack my system and get access to my account he can distroy my whole system and steal my valuable data. When this thought came to my mind I dicided to have sepetate password for 'sudo'  and my ordinary user account, so I googled around and found on Ubuntu forum that by adding  following line in /etc/sudoers 'Defaults:myusername    timestamp_timeout=0, runaspw, passwd_tries=1' will solve my problem. Fine, but it also stated that by doing so we enable 'root' account, meaning that we will deprive ourself the advantage given by Ubuntu's default installation of disabled 'root'. This is not the thing I wanted, so I have made list of things that I want to achive.
1.I want to retain the facility of disabled 'root' user.
2.I want to change password for 'sudo' application only.
3.I want seperate password for my user account.
Is this possible, please help me, thanks in advance.
Another much needed information, I'm studing web developmnet on 'LAMP' platform, but I have taken care that Apache web server and Axigen mail server replies only for 121.0.0.1 and not any other address. But what I wanted to know is by configuring 'UFW' to deny in-coming traffic can I prevent hacker gaining access to my computer via internet? Please reply, thanks in advance.
Note: I have set user 'home' to 0700 and I recomend every one to do so.
Command: 'sudo chmod 0700 /home/yourusername/'

---

### Post by arapaho on 2010-12-31
If you want two separate passwords for sudo and regular user then create another user without sudo privileges.

Read this topic:
user (in jail) with very limited permissions
[http://ubuntuforums.org/showthread.php?t=1627240](http://ubuntuforums.org/showthread.php?t=1627240)

---

### Post by s.a.patil on 2010-12-31
Many thanks arapaho, I have already done that. I have created another user-account without any privilege. But I wanted to know whether I can achieve what I wanted to achieve.

---

### Post by stmiller on 2010-12-31
nope

:)

---

### Post by handy on 2011-01-01
> **s.a.patil said:**
> ...
I have made list of things that I want to achive.
1.I want to retain the facility of disabled 'root' user.
2.I want to change password for 'sudo' application only.
3.I want seperate password for my user account.
Is this possible, please help me, thanks in advance.


Why not either have a root account &/or sudo using a monstrously difficult password?

If this isn't enough for you then setup a separate firewall/router like IPCop (on an old PII or an even more energy efficient machine) which is specifically tailored to keep crackers out.

---

### Post by s.a.patil on 2011-01-01
Many thanks handy, in fact I have set 15 digit alpha-numeric complex password. I didn't have idea of IPCop, thanks, I check it and get back to forum. Mean while I experimented with file permission for my main 'User Account', I chmod 000 /home/userdirectory/ and found that, by setting this permission I will not be able to open any application, nor can I login to GNOME after re-boot. When I discovered this I was very happy that my main 'User Account' is locked for outside world and my self, but not so, one can select 'xterm' and give it 'sudo' command and change back the file permission to chmod 0700 thus defeating my happiness. Ok no problem. I really needed this feature for following reasons, I beg community's pardon, it is only my opinion.
1. My approach give total of two level security, which make hacking more difficult.
2. Our work environment will be sand-boxed, leaving us worry free.
3. An advantage of simple but very effective protection of system without performance loss or without any resource loss.
Just ponder on point, then you really understand my concern, by this approach one can get benefit of disabled 'root' account and using 'sudo' and thus can bring arguments of another school down. (Anti-sudo school, we can find many if we google around)

---

### Post by handy on 2011-01-01
The following link is to a post in a thread I started over 2 years ago when I was initially setting up IPCop, you may find some help in it. I would have liked to have seen something similar when I was setting up:

[http://ubuntuforums.org/showpost.php?p=6303994&postcount=29](http://ubuntuforums.org/showpost.php?p=6303994&postcount=29)

---

### Post by CharlesA on 2011-01-01
If you have services listening on the lo interface (127.0.0.1 or ::1) and don't have SSH installed, you are fine.

Even if you have SSH installed, using a 15 character alpha numeric password will normally keep the crackers at bay, if that machine is exposed to the internet.

If you are that worried about it, just enable the firewall and go about yer business. :)

---

### Post by s.a.patil on 2011-01-01
Many thanks handy & CharlesA. 
Dear handy I will go through your post on MiniITX & IPCop Firewall with Advanced Proxy add-on. 
Dear CharlesA I checked my Ubuntu synaptic package manager and found that open-ssl-client is installed, since I don't connect to any server for any purpose I feel it is not needed and would like to uninstall it, since Linux depend on dependency is it safe to remove? Please guide thanks in advance.

---

### Post by CharlesA on 2011-01-01
You can leave the SSH client installed, as it's handy to have. I was talking about openssh-server, which allows you to connect to a machine remotely.

You can try to uninstall it and Synaptic will tell you if it depends on anything.

---

### Post by handy on 2011-01-01
Unless you have a number of machines doing a lot of time on the internet you probably won't need the advanced proxy add-on for IPCop.

IPCop has its own built in proxy which with the 3 or 4 machines online here still never gets used as there is just not enough data moving internet wise.

I've spoken with people who have a low powered IPCop box serving a network with 300 people on it! It is quite an amazing installation. Easy to install too, once you know how. :)

Also, I should mention that it has a quite a range of powerful tools available without using any add-ons, such as "intrusion detection" which I tend to think would appeal to you. I don't use it personally as I don't need it.

---

### Post by s.a.patil on 2011-01-02
Many many thanks handy, I really appreciate your help. Yesterday I went through your post, when you first mentioned IPCop I thought it was IP table configuring software or an additional firewall, but after going through your post I learnt that it is a separate Linux distro which can be used as additional protection. Thank you very much for enlightening on this, but as of now as you mentioned I don't need such facility now since my only Linux laptop will connect to internet, disabling incoming traffic in 'UFW' and see that OpenSSH server is not installed is sufficient. All other's people computer used in my home are on Windows with Kaspersky Internet Security installed. I'm the only one in my home who use Ubuntu Linux for my personal and business needs. Thanks a lot handy.

---

