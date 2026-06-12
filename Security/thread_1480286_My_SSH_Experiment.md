---
title: "My SSH Experiment"
date: 2010-05-11
forum: Security
---

### Post by mr-woof on 2010-05-11
hi all,

I finally got round to having another play around with SSH, so I've got a ubuntu server 9.10 virtual machine setup, updated, upgraded, a static IP set and ssh server installed. 

I've followed the below steps, am I missing anything before I open up the port on my router and test this from the internet?

1) sudo nano /etc/ssh/sshd_config 
2) change loginGraceTime 120 to LoginGraceTime 20
3) PermitRootLogin to no
4) change log level from INFO to VERBOSE
Tested ssh from laptop, working with password
5) change PasswordAuthentication to no and delete #
6) sudo nano /etc/ssh/sshd_config 
7) change PasswordAuthentication to yes
and sudo /etc/init.d/ssh restart

On the client machine
9) mkdir ~/.ssh
10) chmod 700 ~/.ssh
11) ssh-keygen -t rsa -b 4096
12) cd .ssh
13) ssh-copy-id -i id_rsa.pub me@x.x.x.x
14) sudo nano /etc/ssh/sshd_config 
15) change PasswordAuthentication to no
16) sudo /etc/init.d/ssh restart

Client logs in fine, once the passphrase key is entered. 

I've then installed, fail2ban and deny hosts. I haven't changed the default port from 22 yet, as I want to see what sort of brute force attacks are the norm, what the logs look like etc

Can anyone think of anything I've missed, looks wrong etc?

Edit: just to add, I've tried to ssh from another ubuntu machine and i'm getting permission denied(public key), so that's working ok?

Edit again: Can ssh run on any port? I was thinking of 443 as work does let that through the firewall(s), I just want to see if it'll work and how important is the passphrase when you create the rsa key?

---

### Post by 8Kuula on 2010-05-11
> **mr-woof said:**
> I've then installed, fail2ban and deny hosts. I haven't changed the default port from 22 yet, as I want to see what sort of brute force attacks are the norm, what the logs look like etc

Can anyone think of anything I've missed, looks wrong etc?

I would suggest to add 2 lines in iptables.
> ```
iptables -A INPUT -m recent --update --seconds 40 --hitcount 5 --name SSH --rsource -j DROP
iptables -A INPUT -m recent --set --name SSH --rsource -j ACCEPT
```
If the rules detect 5 attempts to connect to SSH from any given IP address within 40 seconds, it will prevent further connections to SSH from that IP address.  If attempts are continued, the counter is reset, thus prolonging the black hole for that IP address. Source: [http://www.gagme.com/greg/linux/protect-ssh.php](http://www.gagme.com/greg/linux/protect-ssh.php)

Works nicely against login bots.

Edit: that fail2ban does same, I think.

---

### Post by CharlesA on 2010-05-11
Set ```
PubkeyAuthentication yes
``` in sshd_config

Everything looks good except from that.

SSH can listen/run on any port you choose.

If you don't have a passphrase on the key, if someone got a hold of the key, they'd be able to log in without being prompted for the passphrase.

---

### Post by cariboo on 2010-05-11
Using port 443 isn't a good idea, as it's used by https, use something like 2020, 2200.

---

### Post by CharlesA on 2010-05-11
> **cariboo907 said:**
> Using port 443 isn't a good idea, as it's used by https, use something like 2020, 2200.

Guessing the OP wants to use 443 so that it is able to get past a firewall.

---

### Post by pricetech on 2010-05-11
Unless it's someone else's firewall you can open any port you want.  I suggest using a port above the registered ports range (above 49151 as I recall)

I'm using ports up there and they're working just fine.

---

### Post by mr-woof on 2010-05-11
hi all and thanks for the replies, yes port 443 just as a test to see if I can bypass the firewalls in work etc. I'll move it then to a random port :)

What benefits would I have by turning PubkeyAuthentication to yes?

Does fail2ban do the same thing as the two Iptables lines?

---

### Post by pricetech on 2010-05-11
As I understand it, fail2ban monitors attempts to connect to your computer.  After so many failed attempts, it blocks the IP from which the attempts are coming.

---

### Post by CharlesA on 2010-05-11
> **mr-woof said:**
> hi all and thanks for the replies, yes port 443 just as a test to see if I can bypass the firewalls in work etc. I'll move it then to a random port :)

What benefits would I have by turning PubkeyAuthentication to yes?

Does fail2ban do the same thing as the two Iptables lines?

By using keys, you won't have to worry about someone bruteforcing your password.

It looks like you already created your keys, so why not just used keyed logons?

---

### Post by mr-woof on 2010-05-12
PubkeyAuthentication was already set to yes, I didn't have to change it :)

I've just been reading up on how to use my ssh server for secure browsing, If I was say in an airport/coffee shop. I've been testing the socks proxy using firefox, using the following command:

ssh -p 443 -D localhost:9999 me@x.x.x.x 

I've been looking at the traffic using wire shark and to me, it looks right, SSL and TCP data between the laptop and the server. 

Now, what else can i do using ssh lol :)

---

### Post by CharlesA on 2010-05-12
Tunnel to services running on other machines on your internal network.

---

### Post by bodhi.zazen on 2010-05-12
> **mr-woof said:**
> I've then installed, fail2ban and deny hosts. I haven't changed the default port from 22 yet, as I want to see what sort of brute force attacks are the norm, what the logs look like etc

They look like this :

> auth.log.0:May  8 05:07:00 ufbt sshd[19466]: Invalid user tomcat from 109.169.17.204
auth.log.0:May  8 05:08:23 ufbt sshd[19570]: Invalid user oracle from 109.169.17.204
auth.log.0:May  8 05:08:24 ufbt sshd[19572]: Invalid user oracle from 109.169.17.204
auth.log.0:May  8 05:08:26 ufbt sshd[19574]: Invalid user oracle from 109.169.17.204
auth.log.0:May  8 05:08:27 ufbt sshd[19576]: Invalid user oracle from 109.169.17.204
auth.log.0:May  8 05:08:29 ufbt sshd[19578]: Invalid user oracle from 109.169.17.204
auth.log.0:May  8 05:08:31 ufbt sshd[19580]: Invalid user oracle from 109.169.17.204
auth.log.0:May  8 05:08:32 ufbt sshd[19582]: Invalid user oracle from 109.169.17.204
auth.log.0:May  8 05:08:34 ufbt sshd[19584]: Invalid user oracle from 109.169.17.204
auth.log.0:May  8 05:08:35 ufbt sshd[19586]: Invalid user test from 109.169.17.204
auth.log.0:May  8 05:08:37 ufbt sshd[19588]: Invalid user test from 109.169.17.204
auth.log.0:May  8 05:08:39 ufbt sshd[19590]: Invalid user test from 109.169.17.204
auth.log.0:May  8 05:08:40 ufbt sshd[19592]: Invalid user postgres from 109.169.17.204
auth.log.0:May  8 05:08:42 ufbt sshd[19594]: Invalid user postgres from 109.169.17.204
auth.log.0:May  8 05:08:43 ufbt sshd[19596]: Invalid user postgres from 109.169.17.204
auth.log.0:May  8 05:08:45 ufbt sshd[19598]: Invalid user user from 109.169.17.204
auth.log.0:May  8 05:08:47 ufbt sshd[19600]: Invalid user user1 from 109.169.17.204
auth.log.0:May  8 05:08:48 ufbt sshd[19602]: Invalid user user from 109.169.17.204
auth.log.0:May  8 05:08:50 ufbt sshd[19604]: Invalid user user1 from 109.169.17.204
auth.log.0:May  8 05:08:51 ufbt sshd[19606]: Invalid user nagios from 109.169.17.204
auth.log.0:May  8 05:08:53 ufbt sshd[19608]: Invalid user nagios from 109.169.17.204
auth.log.0:May  8 05:08:55 ufbt sshd[19610]: Invalid user nagios from 109.169.17.204
auth.log.0:May  8 05:08:56 ufbt sshd[19612]: Invalid user nagios from 109.169.17.204
auth.log.0:May  8 05:08:58 ufbt sshd[19614]: Invalid user nagios from 109.169.17.204
auth.log.0:May  8 05:09:00 ufbt sshd[19616]: Invalid user nagios from 109.169.17.204
auth.log.0:May  8 05:09:01 ufbt sshd[19618]: Invalid user nagios from 109.169.17.204
auth.log.0:May  8 05:09:03 ufbt sshd[19620]: Invalid user nagios from 109.169.17.204
auth.log.0:May  8 05:09:05 ufbt sshd[19622]: Invalid user nagios from 109.169.17.204
auth.log.0:May  8 05:09:06 ufbt sshd[19624]: Invalid user nagios from 109.169.17.204
auth.log.0:May  8 05:09:08 ufbt sshd[19626]: Invalid user weblogic from 109.169.17.204
auth.log.0:May  8 05:09:09 ufbt sshd[19628]: Invalid user weblogic from 109.169.17.204
auth.log.0:May  8 05:09:11 ufbt sshd[19630]: Invalid user weblogic1 from 109.169.17.204
auth.log.0:May  8 05:09:13 ufbt sshd[19632]: Invalid user ftp1 from 109.169.17.204
auth.log.0:May  8 05:09:14 ufbt sshd[19634]: Invalid user ftp1 from 109.169.17.204
auth.log.0:May  8 05:09:16 ufbt sshd[19636]: Invalid user ftp1 from 109.169.17.204
auth.log.0:May  8 05:09:17 ufbt sshd[19638]: Invalid user ftp1 from 109.169.17.204
auth.log.0:May  8 05:09:19 ufbt sshd[19640]: Invalid user ftp1 from 109.169.17.204
auth.log.0:May  8 05:09:21 ufbt sshd[19642]: Invalid user upload from 109.169.17.204
auth.log.0:May  8 05:09:22 ufbt sshd[19644]: Invalid user upload from 109.169.17.204
auth.log.0:May  8 05:09:24 ufbt sshd[19646]: Invalid user upload from 109.169.17.204
auth.log.0:May  8 05:09:25 ufbt sshd[19648]: Invalid user upload from 109.169.17.204
auth.log.0:May  8 05:09:27 ufbt sshd[19650]: Invalid user upload from 109.169.17.204
auth.log.0:May  8 05:09:29 ufbt sshd[19652]: Invalid user bill from 109.169.17.204
auth.log.0:May  8 05:09:30 ufbt sshd[19654]: Invalid user aaa from 109.169.17.204
auth.log.0:May  8 05:09:32 ufbt sshd[19656]: Invalid user karla from 109.169.17.204
auth.log.0:May  8 05:09:33 ufbt sshd[19658]: Invalid user upload from 109.169.17.204
auth.log.0:May  8 05:09:37 ufbt sshd[19662]: Invalid user tai from 109.169.17.204
auth.log.0:May  8 05:09:38 ufbt sshd[19664]: Invalid user fred from 109.169.17.204
auth.log.0:May  8 05:09:40 ufbt sshd[19666]: Invalid user a from 109.169.17.204
auth.log.0:May  8 05:09:41 ufbt sshd[19668]: Invalid user jeff from 109.169.17.204
auth.log.0:May  8 05:09:43 ufbt sshd[19670]: Invalid user scanner from 109.169.17.204
auth.log.0:May  8 05:09:44 ufbt sshd[19672]: Invalid user music from 109.169.17.204
auth.log.0:May  8 05:09:46 ufbt sshd[19674]: Invalid user evelyn from 109.169.17.204
auth.log.0:May  8 05:09:48 ufbt sshd[19676]: Invalid user carla from 109.169.17.204
auth.log.0:May  8 05:09:49 ufbt sshd[19678]: Invalid user art from 109.169.17.204
auth.log.0:May  8 05:09:51 ufbt sshd[19680]: Invalid user alex from 109.169.17.204
auth.log.0:May  8 05:09:52 ufbt sshd[19682]: Invalid user mark from 109.169.17.204
auth.log.0:May  8 05:09:54 ufbt sshd[19684]: Invalid user eva from 109.169.17.204
auth.log.0:May  8 05:09:56 ufbt sshd[19686]: Invalid user adam from 109.169.17.204
auth.log.0:May  8 05:09:57 ufbt sshd[19688]: Invalid user fax from 109.169.17.204
auth.log.0:May  8 05:09:59 ufbt sshd[19690]: Invalid user demo from 109.169.17.204

Brute force attacks look the same, but they go on longer (ip address 109.169.17.204 has not returned) and use the same user over and over until either they give up or you black list them.

root 
root
root
root

to see these things

```
grep sshd /var/log/auth.log > ~/ssh_traffic
```

Then open ~/ssh_trafic with any editor.

---

### Post by 8Kuula on 2010-05-12
> **mr-woof said:**
> Does fail2ban do the same thing as the two Iptables lines?

Fail2ban goes furter, like baning IP forever. And keeping records, so and so, actualy I have just read little about it, never actualy used :P
Iptable lines just block IP for little while, enough to login bot timeout and switch IP. IPs do not get saved anywhere.

---

### Post by mr-woof on 2010-05-13
Right, at least I know what i'm looking for now. Thanks Bodhi :)

What other attacks do you usually see?

---

