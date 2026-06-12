---
title: "Time restricted access to certain websites"
date: 2010-06-11
forum: Security
---

### Post by potatan on 2010-06-11
Hi,

I'd like to be able to limit access to a particular website, based on the time of day.  I would also like to be able to password protect this if possible.

So for instance, from 7am until 10pm daily, I can access [http://www.ubuntu.com](http://www.ubuntu.com) but after 10pm it redirects to 127.0.0.1 or something.  And this configuration be protected by only allowing a certain user (other than root) to change the config?

Just some pointers about where to begin would be great, thanks.

---

### Post by HermanAB on 2010-06-11
squid-cache

---

### Post by new_tolinux on 2010-06-11
The short quick-and-dirty way:
Create a hostfile called hostday and another called hostnight.
In hostday you specify 127.0.0.1 [www.ubuntu.com](www.ubuntu.com)
In hostnight you don't specify anything

Create a cronjob for root:
```
sudo -i
crontab -e
```
Create 2 entries: one to copy hostday to /etc/hosts (for example at 7 AM) and one to copy hostnight to /etc/hosts (for example at 10 PM).

Although there's no option to use a password to allow certain sites during a special period, you should be able to edit /etc/hosts as sudo (removing the line linking [www.ubuntu.com](www.ubuntu.com) to 127.0.0.1 will allow your computer to access the website).

Note that this is in no way the official way, since hosts wasn't meant to block access to certain sites.

---

### Post by sanderj on 2010-06-11
> **new_tolinux said:**
> The short quick-and-dirty way:
Create a hostfile called hostday and another called hostnight.
In hostday you specify 127.0.0.1 [www.ubuntu.com](www.ubuntu.com)
In hostnight you don't specify anything

Create a cronjob for root:
```
sudo -i
crontab -e
```
Create 2 entries: one to copy hostday to /etc/hosts (for example at 7 AM) and one to copy hostnight to /etc/hosts (for example at 10 PM).

Although there's no option to use a password to allow certain sites during a special period, you should be able to edit /etc/hosts as sudo (removing the line linking [www.ubuntu.com](www.ubuntu.com) to 127.0.0.1 will allow your computer to access the website).

Note that this is in no way the official way, since hosts wasn't meant to block access to certain sites.

Clever hack!

---

### Post by new_tolinux on 2010-06-11
> **sanderj said:**
> Clever hack!
It's a bit limited. For instance, you can still access the sites by using their IP-adress, and you can't specify sites on a per-user base.
It's also not very useful if you'll have to block site_a from 9am till 10pm and site_b from 7am till 1pm.
It's also very easy to "crack" if the user has the rights to use sudo ;)

But as I said, it's the quick-and-dirty way. Not a lot of RTFM, not a lot of work and no need to install any program.

---

### Post by cariboo on 2010-06-11
If you are using a router, most of them have the ability to block access by day and time, see the screenshot from my Linksys WRT310N

---

### Post by potatan on 2010-06-11
Thanks, I'll give that a go!

cheers

---

### Post by bodhi.zazen on 2010-06-11
If it is a single ipaddress, you can do this with iptables.

```
sudo iptables -A OUTPUT -p tcp --dport 80 -d ipaddress_here -m time --timestart 09:00 --timeend 22:00 -j ACCEPT
sudo iptables -A OUTPUT -p tcp --dport 80 -d ipaddress_here -j REJECT
```

You can expand on that if you wish.

The time module does not take daylight savings time into account, so you may need to adjust your times.

You then save and restore your settings.

```
sudo iptables-save > /etc/iptables.save
```

And add this to /etc/rc.local

```
/sbin/iptables-restore < /etc/iptables.save
```

---

