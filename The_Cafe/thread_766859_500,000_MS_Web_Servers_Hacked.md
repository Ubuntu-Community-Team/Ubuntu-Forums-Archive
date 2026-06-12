---
title: "500,000 MS Web Servers Hacked"
date: 2008-04-25
forum: The Cafe
---

### Post by NullHead on 2008-04-25
Here is the link: [http://it.slashdot.org/it/08/04/25/1358234.shtml](http://it.slashdot.org/it/08/04/25/1358234.shtml)

The article: 

> "According to F-Secure, over 500,000 webservers across the world, including some from the United Nations and UK government, have been victims of a SQL injection. The attack uses an SQL injection to reroute clients to a malicious javascript at nmidahena.com, aspder.com or nihaorr1.com, which use another set of exploits to install a Trojan on the client's computer. As per usual, Firefox users with NoScript should be safe from the client exploit, but server admins should be alert for the server-side injection. Brian Krebs has a decent writeup on his Washington Post Security Blog, Dynamoo has a list of some of the high-profile sites that has been hacked, and for fun you can watch some of the IIS admins run around in circles at one of the many IIS forums on the 'net."

This happened to my Mom't brand new Sony Vio ... I ended up formatting it because I had no idea how to remove this monster of a torjan.

---

### Post by Seisen on 2008-04-25
That is why I am glad I don't use Window's very much and when I do I use Firefox with NoScript.

---

### Post by Johnsie on 2008-04-25
Yes, MS web servers have vulnerabilties. Apache2 isn't 100% safe either though. A lot of Linux servers have been hacked too. Keeping a web server secure is as much about the quality of the adminstrators code and network setup as the operating system and server software you use. Put simply, if someone runs a webserver and dosesnt secure it properly it will be hacked no matter what OS is on there.

It's important for anyone runninmg a webserver to keep up to date with the patches but also to look at the methods used by malicious hackers. A simple thing like an insecure php upload script can compromise the security of a whole system/network. Linux and Windows both have permission based systems and webmasters/administrators need to learn how to use them properly. Also, many people use unencrypted ftp which is really dangerous because the client communicates with the server in an unencrypted manner, even when sending login details. Any remote accessing of servers should be done using encryption.

The bottom line is, if you want to be safe do it yourself. Dont trust the operating system or webserver to do it all for you because they wont.

---

### Post by NullHead on 2008-04-25
> **Seisen said:**
> That is why I am glad I don't use Window's very much and when I do I use Firefox with NoScript.
Unfortunately there is less technically inclined people like my Aunt and Cousin who both use Vista and hate it, but struggle with things like moving the windows task bar from the top of the screen to the bottom. This monster that was on my Mom's new laptop had the capability to monitor website browsing habits, change your active desktop background, expand your user privileges from user to administrator, so it can install more of it "buddies" and the list goes on. 

For the average user this is a very serious thing. Geek squad and Firedog better figure out how to remove these nasty things and get these poor people back on track.

---

### Post by ShadowGray on 2008-04-25
Hmm, how would you know if you picked up this nasty little Trojan?

---

### Post by NullHead on 2008-04-25
Oh you'll know ... you'll get like 10 different system information bubbles from the system tray telling your your system is infected, your system is running slow click here to optimize. There is little quirks in the grammar that you can detect. I can't remember an exact example of something that you'll fine, but you can run a search for one file that kept coming back on my system it is "bat.exe" don't be fooled ... it is a malicious file and if you have the file all I can say it try to remove it best you can ... I ended up formating the drive ..... it evolved form what seamed like spyware to a trojan, to a very nasty mutated piece of malware ... 

I'd just run a few scans and if it picks up things like "zango" and "2020 webseach" then you have the same thing that my machine had. I recommend [[URL="V"]a-squared free]("http://www.emsisoft.com/en/software/free/")[/URL] and [sbybot S&D]("http://www.safer-networking.org/en/index.html").

EDIT: also I forgot, but this thing would disable the task manager ... you need to download this one if you end up having the trojan I had: [http://technet.microsoft.com/en-us/sysinternals/bb896653.aspx](http://technet.microsoft.com/en-us/sysinternals/bb896653.aspx)

---

### Post by Tundro Walker on 2008-04-25
> **NullHead said:**
> This monster... had the capability to monitor website browsing habits, change your active desktop background, expand your user privileges from user to administrator, so it can install more of it "buddies" and the list goes on. 

I keep waiting for that one "leet haxor" who decides for April Fools he'll send out a virus that ...

1) scans your system and eliminates all viruses and malware currently on it
2) blocks up ports and vulnerabilities that other viruses may exploit
3) cleans out the recycle bin
4) monitors computer usage and tweaks the services to only what's needed, causing a 200% boost in computer performance
5) defrags the hard drive
6) propagates itself to 20 other computers via email then deletes itself.

It might not get them "leet" props amongst their peers, but it sure would get their name in the history books.

---

### Post by NullHead on 2008-04-25
> **Tundro Walker said:**
> I keep waiting for that one "leet haxor" who decides for April Fools he'll send out a virus that ...

1) scans your system and eliminates all viruses and malware currently on it
2) blocks up ports and vulnerabilities that other viruses may exploit
3) cleans out the recycle bin
4) monitors computer usage and tweaks the services to only what's needed, causing a 200% boost in computer performance
5) defrags the hard drive
6) propagates itself to 20 other computers via email then deletes itself.

It might not get them "leet" props amongst their peers, but it sure would get their name in the history books.

That would be the best virus ever! I'd love to contract that one any time! :lolflag:

---

### Post by LaRoza on 2008-04-25
> **Tundro Walker said:**
> I keep waiting for that one "leet haxor" who decides for April Fools he'll send out a virus that ...

1) scans your system and eliminates all viruses and malware currently on it
2) blocks up ports and vulnerabilities that other viruses may exploit
3) cleans out the recycle bin
4) monitors computer usage and tweaks the services to only what's needed, causing a 200% boost in computer performance
5) defrags the hard drive
6) propagates itself to 20 other computers via email then deletes itself.

It might not get them "leet" props amongst their peers, but it sure would get their name in the history books.

Sounds like an auto Linux installer.

---

### Post by NullHead on 2008-04-25
Except for the sixth one... Linux don't spread through email and then delete its self :lolflag:

---

### Post by Ghil on 2008-04-25
> **NullHead said:**
> Except for the sixth one... Linux don't spread through email and then delete its self :lolflag:

...yet. ;)

---

### Post by porcupineapples on 2008-05-24
One of my friends had this virus, didn't know it was this until i read the behavior described above. I booted up his computer and i couldn't do anything, the pop ups and bogus system tray notifications kept interfering, so i just said screw it and reinstalled.

---

### Post by happyhamster on 2008-05-24
> **NullHead said:**
> 1) scans your system and eliminates all viruses and malware currently on it
That reminded me of:
[http://it.slashdot.org/article.pl?sid=06/10/21/079200](http://it.slashdot.org/article.pl?sid=06/10/21/079200)

Scary (but funny).

---

