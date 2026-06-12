---
title: "IPtable assitance needed"
date: 2009-09-09
forum: Security
---

### Post by Lori700698 on 2009-09-09
I swear I get one step figured out and these hackers are waiting with something new for me to try to figure out.  I can't learn these IPtables fast enough!

I got proxy rolling and blocked with this
```
-A INPUT -p tcp -m tcp --source 127.0.0.1 --dport 3128 -j ACCEPT
 -A INPUT -p tcp -m tcp --dport 3128 -j DROP
```

1. I think I understand, but 127.0.01 didn't work, had to use my public IP, I think coz all my computers go through the router not the server is this correct?

2.  Can I use the exact same code as above for SSH? (Changing to 22)

3.  I want to make snort base & ossec not available to anybody but inside my network...where do I find an example of this kind of code to put in my IPtable?  right now anybody can just access them.

Here's my new attack I need to learn about and I haven't got this far in my security education yet.  I know I can't just block a port and fix it, one good thing is I don't have any PHP unless ossec or snort/base use it.
```
Src IP: 64.15.159.169
First time this IDS alert is generated.
[**] [1:2281:3] WEB-PHP Setup.php access [**][Classification: access to a potentially vulnerable web application] [Priority: 2] 64.15.159.169:36570 -
```

I felt kind of felt just a tad secured when I got the proxy together only to be stomped on again!
Thank you sooo much for the help and education!
Lori

---

### Post by phillw on 2009-09-10
```
3. I want to make snort base & ossec not available to anybody but inside my network...where do I find an example of this kind of code to put in my IPtable? right now anybody can just access them.
```

The ongoing thread for ossec can be found here .....

[http://ubuntuforums.org/showthread.php?t=213445](http://ubuntuforums.org/showthread.php?t=213445)

As to the rest of it .... I'm also just learning !!

Phill.

---

### Post by cdenley on 2009-09-10
127.0.0.1 is the local loopback device. You can only connect to it from your local computer. You cannot directly connect to it across any network. If you want to make a server usable only for the local system the server is running on, you can filter all connections on that port except those coming from 127.0.0.1, but it would be easier to configure that server to listen on the 127.0.0.1 interface.

However, it sounds like you want to allow access from any computer on your LAN. If this is the case, you would want to allow your LAN subnet, not just 127.0.0.1. For example:
```

sudo iptables -A INPUT -p tcp -m tcp -s 192.168.0.0/24 --dport 3128 -j ACCEPT

```
Your LAN subnet may be different.

For your new "attack", it appears it is a warning about a "potentially vulnerable" PHP script. I'm guessing it shows that message anytime a "setup.php" file exists, since web applications often use such a file for initial system configuration, but it is often used by remote attackers after the file should have been deleted. This does not necessarily mean that your "setup.php" file is vulnerable to attack.
```

locate -b -i -r ^setup.php|xargs head -v

```

---

### Post by bodhi.zazen on 2009-09-10
By it's very nature snort gives a lot of false positives. You will need to read up on them, there are links to the warnings in base as well as on the snort home page.

If the warning is from ossec, same thing, look on the ossec web interface and on the ossec web site.

---

### Post by Lori700698 on 2009-09-11
> **bodhi.zazen said:**
> By it's very nature snort gives a lot of false positives. You will need to read up on them, there are links to the warnings in base as well as on the snort home page.

If the warning is from ossec, same thing, look on the ossec web interface and on the ossec web site.

Thank you, I am planning on reading up on all of this!  What made me freak out about that alert was that it was about 6 or 7 different attempts at accessing php files in a row from the same IP, so I assumed this was hostile behavior.  I found many of the OSSEC links lead to pages that are no longer available and googleing sometimes leaves me asking more questions.  The promiscuous(sniffing) mode almost made me crazy trying to figure out if it was a false or not, and what it meant.

On a side not, of course with a question.  I did get base and ossec blocked using Apache.  Is this a solid security fix, and  are all the sub pages blocked too when you use Apache to lock a directory to a certain IP?  I have a lot to learn and so many questions now.
```
allow from 127.0.1.1
deny from all

```

Thank you again for helping me figure some of this out!
Lori

---

### Post by __p1n__ on 2009-09-11
It's important to not automatically discount that sort of discovery traffic.

I actually bricked (not recoverable by firmware reload) my pos D-Link router while performing a paros auto-spider assessment on it.  The feedback was great - this was exactly the information I needed to understand the pos' practical security performance - but I certainly didn't expect an utterly unusable appliance.  The device is currently replaced by a linksys appliance running a custom ddwrt image so all is good.

---

### Post by bodhi.zazen on 2009-09-11
I agree with __p1n__ , but I do not believe I advised to ignore such events.

Yes, at first there is a ton of reading, but after a while you will get a sense of what is "normal".

In terms of taking action I ask myself 4 questions :

1. Am I vulnerable to this attack ? If the attack is for an OS I do not run or an older version of apache/php I am "OK" , otherwise update.

2. Is the ip address in question persistent ? 6 alerts is nothing =). If there is a persistant pattern of behavior from an IP => Blacklist.

3. Was the attack successful ? This is where OSSEC come into play, OSSEC will temporarily ban an IP which is sufficient to deter 99.9% of would be crackers. OSSEC will also alert you if system files have been altered.

4. Is "normal traffic" affected ? You need to test your server and see if you wish to allow the "Alert" (Alert != cracking).

Is it perfect, no, but it is much much better then allowing iptables to fill your logs.

Are there other options to OSSEC, yes, feel free to try them if you wish.

---

### Post by __p1n__ on 2009-09-11
Bodhi.Zazen, my comment was in general and not directed to your excellent post.  

Note: the specific target of my paros assessment was in fact the admin web server on the d-link device.  The fact that even without a valid login session the paros tool was able to trash the site and brick the device so hard that recovery was impossible by: reset, external, failsafe firmware reload just goes to underscore the importance of empirical testing and validation no matter how sound a logical security model may be.

The same sort of "discovery/audit" is trivially possible against any web application (use w3af, paros ,etc.) and the web server logs will reveal a pattern of varying permuted non-existing files similar to what lori reported.

---

### Post by Lori700698 on 2009-09-11
_p1n_ Thank you for sharing your story, I will know to never try that option....yikes!  I spent way to much money on my D-link extreme to have it get bricked!

bodhi.zazen, no need to worry I didn't get any impression that alerts are to be ignored.  I guess I'm more freaked seeing all this stuff flying in at my system that I'm sure has always been there I just wasn't looking.  It's overwhelming and sometimes not easy to find the answers of what is false and what needs immediate attention.  I have to start a notebook, I think I get one thing figured out and something new pops up.  I noticed in another post somebody provided some links that you wrote for Apache, I need to look at that too, there is just so much.  Have you ever thought about a stickey with all the links to the many security topics and how-to's you have posted on?

Lori

---

