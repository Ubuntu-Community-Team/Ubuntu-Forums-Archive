---
title: "Am I hacked?"
date: 2014-02-11
forum: Security
---

### Post by ubtutu654 on 2014-02-11
I am a UNIX novice but not total noob.

Something is leeching a ton of banwidth on my ubuntu 13.04 box.

While researching it I stumbled over a thread from a guy who was hacked and I wound up getting a list of all the users on my system.

I think this looks very suspicious - can anyone tell me if I'm hacked or not, please?

I am terry on this list

root
daemon
bin
sys
sync
games
man
lp
mail
news
uucp
proxy
www-data
backup
list
irc
gnats
nobody
libuuid
syslog
messagebus
avahi-autoipd
usbmux
dnsmasq
whoopsie
kernoops
rtkit
speech-dispatcher
lightdm
avahi
colord
pulse
hplip
saned
terry
dhcpd
guest-yla6m4
guest-J9XWdv
guest-bUlUPz
guest-ajBhyE

---

### Post by Habitual on 2014-02-11
Did you create these guest-* accounts?

---

### Post by ubtutu654 on 2014-02-11
No. I created terry. The rest just showed up. rtkit looks damn suspicious all by itself.

---

### Post by The Cog on 2014-02-11
rtkit is RealtimeKit. See "man rtkitctl". I don't think that's a problem.

If you want to see what's using the internet, probably these commands will help:
```
sudo netstat -tup
sudo lsof -i
```

---

### Post by Habitual on 2014-02-11
how about using the last command on each of the guest-* accounts and see *if* they have logged in?

I agree is it alarming and you would do well to be prepared for counter-measure of the re-install kind ***if*** you cannot find the method of entry.

---

### Post by ubudog on 2014-02-11
> **Habitual said:**
> how about using the last command on each of the guest-* accounts and see *if* they have logged in?

I agree is it alarming and you would do well to be prepared for counter-measure of the re-install kind ***if*** you cannot find the method of entry.

+1

Have you examined /var/log/auth.log?

---

### Post by cariboo on 2014-02-11
Those guest accounts are created automagically when you log into that account. They should be removed when you reboot the system.

---

### Post by Habitual on 2014-02-11
I never thought about the "guest" feature of the Ubuntu OS. My bad. :(

---

### Post by raja.genupula on 2014-02-13
okay , can you post output of 

> ac -p

you can see , all the users and their total active time. so that you can see the blackhat account.

---

### Post by bashiergui on 2014-02-13
I would focus on network traffic in your instance. If something is eating up bandwidth then start with ```
top
```and see what processes are using lots of cpus. You could try to run ```
sudo netstat -npta
``` on the suspect computer, but it's best to watch network traffic from another machine using tcpdump or Wireshark.


When you have a process name from top then Google it to determine if it's legit. Then you can determine if it's a hacker or if it's some process that has gone wrong.

---

### Post by mimilovell on 2014-02-21
just restart your system and remove the accounts just to be on the safe side

---

### Post by bashiergui on 2014-02-21
> **mimilovell said:**
> just restart your system and remove the accounts just to be on the safe side
If by "safe" you mean "completely break your computer", then yes. Do that.

If you'd like to keep using your computer then no. Don't delete users unless you research & figure out what they do.

---

### Post by fugu2 on 2014-02-21
> **bashiergui said:**
> If by "safe" you mean "completely break your computer", then yes. Do that.

If you'd like to keep using your computer then no. Don't delete users unless you research & figure out what they do.

lol +1
it is probably true that you 'might' be able to get rid of some uesrs with minimal or even zero loss in functionallity, but most likely everything will probably stop working.
I think ill test that out on a VM just to see what happens. I might be instresting.

---

