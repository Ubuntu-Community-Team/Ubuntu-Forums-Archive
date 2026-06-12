---
title: "My security setup/guide"
date: 2009-09-02
forum: Security
---

### Post by go_beep_yourself on 2009-09-02
```
$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo "1" > /proc/sys/net/ipv4/ip_forward
mkdir -p /var/run/motion/
chown -R root:motion /var/run/motion/
chmod -R 770 /var/run/motion/
[SIZE="5"][COLOR="red"]/etc/init.d/privoxy start[/COLOR][/SIZE]
[SIZE="6"][COLOR="red"]macchanger -A wlan2[/COLOR][/SIZE]
alsactl restore
exit 0

```

As you can see, most of what I've done there is for security, as well as video surveillance security. Other things are just hacks/workarounds to fix problems like my PCM volume going to 0% every time I reboot.

I wrote a guide on security/staying anonymous on the internet on my blog that's in my signature. Most of what I write about has to do with security. It is very informative, and the goal is to inform the end user and developers as well as beginners. I contact developers to make changes happen in software, and I start petitions!

The macchanger is good for wifi security testing on your own network.

---

### Post by unspawn on 2009-09-03
> **go_beep_yourself said:**
> As you can see, most of what I've done there is for security, 
"Most"? No, not really. Unless you have a very limited view of what "security" is about and think it can be controlled by some initscript.


> **go_beep_yourself said:**
> I wrote a guide on security/staying anonymous on the internet on my blog that's in my signature. Most of what I write about has to do with security.
With all due respect but from the looks of it (odd pictures and you applauding somebody who uploads warez) this doesn't look like a security web log to me unless the definition changed radically overnight.

---

### Post by go_beep_yourself on 2009-09-05
> **unspawn said:**
> "Most"? No, not really. Unless you have a very limited view of what "security" is about and think it can be controlled by some initscript.

What I meant was most of the security in that file, of course not my entire system. Just to name a few things, Gpg, Truecrypt (3 layers (different algorithms) of Encryption including the use of keyfiles), LUKS, Keyring.


> With all due respect but from the looks of it (odd pictures and you applauding somebody who uploads warez) this doesn't look like a security web log to me unless the definition changed radically overnight.

He can legally do that. In his country, there are no laws against it. Not all his torrents are warez. 

Check out this specific blog entry. This url will load only this blog entry about security.

[http://linuxinnovations.blogspot.com/2009/08/staying-anonymous-on-internet.html](http://linuxinnovations.blogspot.com/2009/08/staying-anonymous-on-internet.html)

---

### Post by unspawn on 2009-09-06
> **go_beep_yourself said:**
> What I meant was most of the security in that file, of course not my entire system. 

It's nice to see you know how to use GnuPG, Truecrypt, LUKS,  but what I mean is that if somebody uses a thread title like "My security setup/guide" one would expect more than "security" of one file...



> **go_beep_yourself said:**
> He can legally do that. In his country, there are no laws against it. Not all his torrents are warez.

First and foremost it's a personal principles issue. Warezing basically is about stealing. If you disagree or don't understand, try to assess how you would react when somebody steals something valuable from you and plasters it all over the 'net or even try to cash in on it by selling it. The "no laws" argument therefore is flawed: warez peddling is warez peddling anywhere and the fact not all his torrents are warez does not right a wrong.


> **go_beep_yourself said:**
> Check out this specific blog entry. This url will load only this blog entry about security.

I'm sorry, I think there's been a mistake. Anonymity is nice for those that need it, opposing restrictive governments and all that, but it doesn't equal network or host security. Good luck with your web log.

---

