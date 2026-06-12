---
title: "proftpd or vsftpd - cannot LIST from Internet using PASV"
date: 2008-02-07
forum: Server Platforms
---

### Post by einstein on 2008-02-07
Okay, two days of Googling is enough and yes I have posted this in Networking too - but I am just not getting anywhere... at all :(

I have ran proftpd for years on my LAN and it worked fine - from my LAN.  More recently, I have arranged a dynamic DNS so that I can access my server from the Internet.  HTTP works fine.  LDAP works fine.  FTP works if I ignore PASV command.  I can always login to my FTP server but things hang forever (no timeouts) waiting for the directory listing.  Everything works fine from within my LAN.

The problem seems to be a networking one as I have identical problems with both proftpd and now vsftpd.  Moreover, the problem appears to have something to do with the passive ports.

I have read the threads the forum thinks I should before posting (as well as dozens of Google results) without success.  It is troubling to find three posts that may be about precisely the same problem and that NONE of the three received a single reply..  One of the posts has nothing to do with my question.

[http://ubuntuforums.org/showthread.php?t=570263](http://ubuntuforums.org/showthread.php?t=570263) [no replies]
[http://ubuntuforums.org/showthread.php?t=412885](http://ubuntuforums.org/showthread.php?t=412885) [no solution here]
[http://ubuntuforums.org/showthread.php?t=287031](http://ubuntuforums.org/showthread.php?t=287031) [no replies]
[http://ubuntuforums.org/showthread.php?t=114649](http://ubuntuforums.org/showthread.php?t=114649) [no replies]
[http://ubuntuforums.org/showthread.php?t=101505](http://ubuntuforums.org/showthread.php?t=101505) [has nothing to do with my question]

My hardware arrangement is Internet->DSL modem->DLink DI-824VUP Router->server.

I have:
[LIST]
[*]Forwarded standard FTP ports on my router to my server.
[*]I have specified passive port ranges for either of the ftp servers I have tried and enabled PASV.
[*]I have forwarded the specified port ranges from my router to my server.
[/LIST]

I sure could use and sure would appreciate some help on this.  As long as I am using a FTP client that will ignore PASV, no problem.  But this is not always the case.

Regards,
           Dennis

---

### Post by faulkes on 2008-02-07
Have you checked the version of your router's firmware against any updates provided by the manufactuer (or an appropriate change list) to see if there is anything which might correlate to your issue?

Faulkes

---

### Post by einstein on 2008-02-07
Faulkes;

Yep, done that too.  

I have also checked that port forwarding works for at least two of the passive ports by setting them up as the port 21 equivalents in the conf files.

Thanks anyway.

Regards,
      Dennis

---

### Post by faulkes on 2008-02-07
Try turning on debug if you are using proftpd (probably exists for vsftpd as well), proftpd
is -d <log level>, 10 being the highest.

If you get anything interesting, put the output back here.

Edit: output will likely be in /var/log/messages or /var/log/secure afaik

Faulkes

---

### Post by freebeer on 2008-02-07
I'll be watching this with interest.  I was never able to get passive mode to work.  I've always suspected an issue with the router, but I've not spent the time to dig a lot deeper... active works just fine for my needs.  Although I can't add to this thread I can confirm that you're not alone with this particular quirk. ;)

---

### Post by Maxtorm on 2008-02-07
> **einstein said:**
> My hardware arrangement is Internet->DSL modem->DLink DI-824VUP Router->server.
Is it possible that the problem is not on the server side, but related to the network you are using on the client side? For instance, all access on one of my LANs goes out through a proxy with only a limited set of explicit ports (80, 443, jabber, etc.) open. In the second phase of a passive FTP conversation, your server will be responding to the client with a port number from the  passive range that you defined. If that port is firewalled/unproxied on the client side, you would experience hanging behaviour similar to what you're making reference to.

---

### Post by einstein on 2008-02-07
Thanks, Faulkes!

I couldn't find anything about debug levels ... so I had to look in the vsftpd man page.  On the way to finding something about debug, which I never did, I  stumbled upon pasv_address so I added that to the conf, reloaded the conf files and presto ... gFTP (client) craps with "child died" and disconnects.  But, hit connect again and all is well except that vsftpd says "Consider using PASV".  What?!?!

Hmmm... I had set pasv_address=me.mydomain.net but I think it is supposed to be dotted IP.  That isn't going to work very well because my public IP is dynamic.  Well, we are desperate, so we log into the router and find out what the current public IP is, enter pasv_address=xxx.xxx.xxx.xxx (x's standing in for real values), reload the conf file and now life is good .... until my public IP changes, that is.

So, after all this monkeying around (some of the unsolved posts on here go back to early 2006) ](*,) we discover what the pros considered brain dead obvious and therefore, I presume, not worth mentioning .

SOLUTION:
  For PASV to work, the server has to tell the client what it's dotted IP is!!!!  BUT, if what the server say and what the client knows are not the same, the client says "Bull ****!".  So, as long as we monitor public IP for changes and modify vsftpd.conf (I presume proftpd is same), PASV will work.

  Does anyone know how many ftp clients and which ones they are that will perform like gFTP - crap on the first try and then revert to ignore PASV subsequently (until restarting the client)?  I refer only to the ones where one cannot explicitly "ignore PASV command" like in gFTP.

Anyhow, thanks again Faulkes.  You did facilitate the identification of the solution, albeit a bit indirectly.

Regards,
    Dennis

---

### Post by inphektion on 2008-02-07
who does the PPPoE login your dsl modem or the router behind it?

---

### Post by einstein on 2008-02-08
The router.

---

### Post by einstein on 2008-02-08
Now, to deal with the dynamic public IP address....

One could use [http://corz.org/ip](http://corz.org/ip) in a perl script owned by root and run periodically ( I am going to do it every 15 minutes, I think - at least until I know how often the dynamic IP changes) by cron.

[http://corz.org/ip](http://corz.org/ip) returns ONLY your public ip address in plain text - easy to parse in perl... actually no parsing required, just read in the dotted IP address string.

Open vsftpd.conf and see if the IPs match.  If not, modify the conf.  Save it. Tell vsftpd to reload conf.

Done.  Problem solved.

A better way to get your public IP address is to query your router with, for example, perl and LWP::UserAgent.

Best regards,
               Dennis

---

### Post by faulkes on 2008-02-08
Well, glad to have helped, even if it was only to make you look in a different place for information.

Faulkes

---

### Post by einstein on 2008-02-09
I solved it.  Look here [http://ubuntuforums.org/showthread.php?t=692355](http://ubuntuforums.org/showthread.php?t=692355)

Dennis

---

