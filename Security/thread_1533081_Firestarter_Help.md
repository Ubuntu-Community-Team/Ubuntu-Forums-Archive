---
title: "Firestarter Help"
date: 2010-07-17
forum: Security
---

### Post by puma1 on 2010-07-17
I just downloaded firestarter and want to "add rule" for allowing file sharing or maybe ftp.. but no matter what screen I am on, the ADD RULE option under the POLICY menu is always greyed out. I cannot get to a screen where this menu is available. any ideas?

---

### Post by jbrown96 on 2010-07-17
You probably need to open it with root privileges. Try Alt+F2 then gksudo firestarter.

Firestarter is an out-dated program. You should probably look at ufw, which is the preferred Ubuntu firewall. It's command line, but very easy to use. 

you can get it running with FTP only with the following. ```
sudo ufw enable
sudo ufw default deny
sudo ufw allow ftp
```

You can check your rules with ```
sudo ufw status
```

Documentation [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by pytheas22 on 2010-07-17
I dealt with this same problem in Firestarter a few days ago.  I'm pretty sure it's just a bug in the application, not a permissions issue.  [This thread]("http://ubuntuforums.org/showthread.php?t=456062") solved it for me.

That said, I'd also recommend ufw over Firestarter.  If you don't want to use the command line, ufw also has a pretty user-friendly graphical interface that you can install with:
```

sudo apt-get install gufw
```

Launch it from the System>Applications>Firewall configuration menu.

---

### Post by bodhi.zazen on 2010-07-17
You will have to purge firestarter if you want to go with UFW/GUFW

```
sudo apt-get purge firestarter
```

---

### Post by CJ_Hudson on 2010-08-25
I just can't seem to get anywhere with Firestarter.
First of all it just seemed to make everything slower (i.e. loading pages, streaming etc.)
Then I noticed it had blocked something so unblocked it. Fine, that worked now.
Then I went to a different website. It blocked it. But this time I couldn't see where to unblock it because the new address didn't appear in the 'Blocked websites' section.
I'm going to give this a few more days trial then uninstall it if no joy.

Edit:
Oh, and please can somebody tell me if you 'Quit' Firestarter is it still running in the 'background' or not?

---

### Post by bodhi.zazen on 2010-08-25
> **MogBug said:**
> I just can't seem to get anywhere with Firestarter.
First of all it just seemed to make everything slower (i.e. loading pages, streaming etc.)
Then I noticed it had blocked something so unblocked it. Fine, that worked now.
Then I went to a different website. It blocked it. But this time I couldn't see where to unblock it because the new address didn't appear in the 'Blocked websites' section.
I'm going to give this a few more days trial then uninstall it if no joy.

Edit:
Oh, and please can somebody tell me if you 'Quit' Firestarter is it still running in the 'background' or not?

Firestarter is not a firewall, it is a configuration tool for iptables.

"Turn off your firewall" (allow all connections) then purge it

See : [http://ubuntuforums.org/showpost.php?p=9603421&postcount=4](http://ubuntuforums.org/showpost.php?p=9603421&postcount=4)

---

### Post by uRock on 2010-08-25
One day they'll remove that from the repos.:D

---

### Post by OpSecShellshock on 2010-08-25
> **uRock said:**
> One day they'll remove that from the repos.:D

I think it appeals to a lot of people because it's got an interface more like what people expect from a firewall--first of all because even though it isn't a firewall it's labeled as one. Additionally, I think it's because it's got the little "play" and "stop" button thingy, and when you open it, it shows a list of blocked connections. To be succinct, it's attractive for all the wrong reasons.

Since the website and detail page in Software Center don't do much by way of disambiguation, we'll just have to keep repeating ourselves until it's gone. So: it's just a front-end for iptables. Blocked connections are blocked connections--intrusion attempts are a common thing and as long as they fail, they're irrelevant. Being able to view blocked connections is only really useful when something's blocked that isn't supposed to be. Yes, it's still running even though you can't see it. Keeping active running graphical applications with administrative privileges is actually riskier than not having a firewall, especially considering that it isn't really a firewall and iptables is active with or without a front-end.

What did I miss?

---

### Post by DawieS on 2010-08-26
> **OpSecShellshock said:**
> 
What did I miss?
You did not mention that Firestarter also has a status panel, where you can see:

1) All current active connections. This is handy to keep an eye on website redirections, and to have at least some privacy control.
2) The network activity for each network device. This is handy for checking network speed, and whether connections are throttled.

The last time I checked, GUFW had a long way to go to reach the level of sophistication already attained by Firestarter. It is a pity that the wheel has to be redesigned, in this day and age of open source software.

---

### Post by uRock on 2010-08-26
> **DawieS said:**
> You did not mention that Firestarter also has a status panel, where you can see:

1) All current active connections. This is handy to keep an eye on website redirections, and to have at least some privacy control.
2) The network activity for each network device. This is handy for checking network speed, and whether connections are throttled.

The last time I checked, GUFW had a long way to go to reach the level of sophistication already attained by Firestarter. It is a pity that the wheel has to be redesigned, in this day and age of open source software.
Are those functions dependable? From what I have read, there have been no updates to Firestarter in years.

---

### Post by bodhi.zazen on 2010-08-26
> **DawieS said:**
> You did not mention that Firestarter also has a status panel, where you can see:

1) All current active connections. This is handy to keep an eye on website redirections, and to have at least some privacy control.
2) The network activity for each network device. This is handy for checking network speed, and whether connections are throttled.

The last time I checked, GUFW had a long way to go to reach the level of sophistication already attained by Firestarter. It is a pity that the wheel has to be redesigned, in this day and age of open source software.

Linux is modular. Use Wireshark.

---

### Post by CJ_Hudson on 2010-08-28
Okay, thanks guys, that really helps.

---

### Post by cariboo on 2010-08-28
> **uRock said:**
> One day they'll remove that from the repos.:D

I have actually started trying to get firestarter removed from the repositories on the ubuntu-devl mailing list, but there seem to be a few people on the list that don't understand that updating it so that it works with newer gtk libraries in maverick, is not really considered a program update.

---

