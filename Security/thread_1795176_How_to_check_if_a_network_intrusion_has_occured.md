---
title: "How to check if a network intrusion has occured?"
date: 2011-07-02
forum: Security
---

### Post by Extrm3 on 2011-07-02
Ok, so I don't know if this thread belongs in this forum since it's more about network security than ubuntu security, but here it goes.

So the other day I was setting up a private minecraft server for me and my friend. As I'm no computer guru or anything like that, I just read a quick guide on how to portforward and did as it said.

After about an hour I also setup a firewall with a rule to only let my friends ip through.

Now my question is, during this time when this port was open is it probable that a hacker could've gotten in to my system. And if he/she did get in, could they have installed any malware on the hard drive.

I'm currently using wubi with Windows Vista and Natty.

---

### Post by Sef on 2011-07-02
> Now my question is, during this time when this port was open is it probable that a hacker could've gotten in to my system. And if he/she did get in, could they have installed any malware on the hard drive.

Probable, no. Possible, yes. Unless something has happened been happening that makes you believe that you have been hacked, I would not worry about it.

---

### Post by Rubi1200 on 2011-07-02
If you are really concerned that this might have happened, start by searching the logs for signs of unusual activity:
[http://beginlinux.com/sec_train_m/sec_secure/777-logschecks](http://beginlinux.com/sec_train_m/sec_secure/777-logschecks)

---

### Post by donniezazen on 2011-07-02
Are their logs in Ubuntu-server which can tell me total data transfer over a period of time? I have had magnanimous amount of data transfer this month.

---

### Post by Extrm3 on 2011-07-02
Ok, thanks for the response.

As I said I am no computer guru and I was not sure whether these types of things are very common and so if I should worry.

I've also read through the syslog breifly and I spot some unknown IP adresses. Should I worry about them or just leave it (most of the entries are from my friends IP)?

---

### Post by Dangertux on 2011-07-02
> **Extrm3 said:**
> Ok, thanks for the response.

As I said I am no computer guru and I was not sure whether these types of things are very common and so if I should worry.

I've also read through the syslog breifly and I spot some unknown IP adresses. Should I worry about them or just leave it (most of the entries are from my friends IP)?

Exposing any service to the global network is asking to be probed. This does not indicate that access actually occured, more like someone knocking on the door to see who was home.

There are many reasons this can occur, some possible and highly probable ones are.

+ You were port scanned either by a person , or by an automated program looking for vulnerable systems. If you are running SSH, SSH based attacks are huge, and commonly scanned for so it wouldn't shock me if you see a lot of failed login attempts in auth.log, usually from IP's from southeast asia, or eastern europe , attempting to authenticate as random users, and a list of known system users. If this bothers you consider running denyhosts.

+ I am not particularly familiar with Minecraft, I know I'm behind the times lol, but it may have some sort of public list server that it was talking to (despite the intention of your server being private, a misconfiguration could have caused it to attempt to list itself publicly)

+ If you are running a webserver or any other forward facing service you will get probed frequently, webserver may also get picked up by various search engine bots, this is normal. 

Honestly, like someone above said unless you notice something out of the ordinary, I wouldn't really stress it.

Enjoy your game would be my suggestion.

---

### Post by Extrm3 on 2011-07-02
Ok, thanks

---

