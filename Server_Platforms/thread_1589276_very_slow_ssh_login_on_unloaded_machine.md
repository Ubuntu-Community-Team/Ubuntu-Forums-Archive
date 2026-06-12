---
title: "very slow ssh login on unloaded machine"
date: 2010-10-06
forum: Server Platforms
---

### Post by chrisbay90 on 2010-10-06
Hi I have a Ubuntu server 10.04 installed on a desktop machine at home. It is used as a home file a torrent and file server it also has squid running serving 5 computers (usualy no more than 3 simultaneously).

However logging in via SSH is horrendously slow. Over a gigabit lan it can take around 30 seconds using a public key. Using a password is even slower, around 30s to password prompt and another 30 to bash prompt.

The puzzling part is it is way over spec'd for what it does. Intel Core 2 Duo @ 2Ghz with 6GB of RAM. It's load average seems to hover around 0.04 never going above 0.10 and is highly responsive in its file server and squid rolls. It is quick in all other respects with one exception. Calamaris, the squid log file analyser is rather slow, parsing roughly 100lines/sec however i'v seen lower spec'd machines do 2000+.

It gets even more puzzling. There have been a few occasions when it has been up around a week or so and unexpectedly became quick to login until the next reboot. This is not always the case. It is at 20 days now and is as slow as ever.

Does anyone have any idea what might be wrong? Or even a clue as to what i should hunt down? io wait time fluctuates between 0%-1% (excluding when large file transfers are going on, but that is once a week at most and doesn't last more than a minute or two being a Gb network)

---

### Post by yesrno on 2010-10-06
You ssh trough the hostname ? Or the ip ?
I remember I had some kind of issue once and DNS was the cause.

---

### Post by chrisbay90 on 2010-10-06
> **yesrno said:**
> You ssh trough the hostname ? Or the ip ?
I remember I had some kind of issue once and DNS was the cause.

hostname usually. I've just attempted using the IP address and still no change.
Thanks for you're suggestion though.

---

### Post by tojal on 2010-10-06
I might be remembering wrong (it sounds incorrect) but I "think" I fixed this problem by adding the line

```
socket options = TCP_NODELAY
```

to /etc/samba/smb.conf

I don't know what samba would have to do with ssh, my memory might be faulty. But give it a try nonetheless

Also, [http://ubuntuforums.org/showthread.php?t=361262](http://ubuntuforums.org/showthread.php?t=361262), but it seems to have varying success

---

### Post by SeijiSensei on 2010-10-06
SSH checks both "forward" (hostname->IP) and "reverse" (IP->hostname) name resolution for every connection.  It will hang for a good period of time trying to do so.

The easiest solution is to add the client's hostname and IP address to the server's /etc/hosts file, and the server's hostname and IP address to the client's /etc/hosts file.

---

### Post by chrisbay90 on 2010-10-06
Thank you everyone who replied.

adding the host names did the trick. Thankyou.

---

