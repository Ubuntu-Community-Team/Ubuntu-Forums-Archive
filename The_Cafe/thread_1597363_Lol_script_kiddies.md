---
title: "Lol script kiddies"
date: 2010-10-15
forum: The Cafe
---

### Post by slackthumbz on 2010-10-15
Perusing my apache error log this morning whilst debugging some CGI I noticed that some script kiddies had launched a primitive and lolworthy attack on the site, error log and traceroute data [here]("http://www.thumbnail.org.uk/cgi-bin/archive/post/1287137041"). 

Anyone else had anything like this lately? It's the first time I've ever noticed anything along these lines in the logs.

---

### Post by _outlawed_ on 2010-10-15
I had to purge the apache logs everyday on my old home server, as script kiddies kept trying to take it down but failed miserably each and every day.

They couldn't even slow down my network one bit. lol

---

### Post by slackthumbz on 2010-10-15
Heh, when we set this server up we got tons of ssh root login attempts from china. So we blocked chinese ips altogether :D It wouldn't have done them any good, the first thing we did was disable remote root logins anyway ;)

---

### Post by Spice Weasel on 2010-10-15
Reminds me of my FTP server logs.. Over 2000 attempted logins under "admin". Shame everyone knows the default is "root". :P

---

### Post by _outlawed_ on 2010-10-15
[deleted]

---

### Post by ticopelp on 2010-10-15
> Allow me to point something out; no self respecting programmer would use php, it's an abomination for amateurs who write dangerously insecure code and don't understand taint checking. 

#-o

---

### Post by slackthumbz on 2010-10-15
Hehehe, I stand by that :p

---

### Post by ubunterooster on 2010-10-15
A bit off-topic but the guy was likely Russian (IP lookup)

[http://whatismyipaddress.com/ip/77.95.95.43](http://whatismyipaddress.com/ip/77.95.95.43)

---

### Post by slackthumbz on 2010-10-15
> **ubunterooster said:**
> A bit off-topic but the guy was likely Russian (IP lookup)

[http://whatismyipaddress.com/ip/77.95.95.43](http://whatismyipaddress.com/ip/77.95.95.43)

Yeah, I noted that from the traceroute data 
```
10 router154.fiber.ru (77.95.91.86) 101.207 ms 102.675 ms 115.279 ms
11 77.95.95.43 (77.95.95.43) 120.681 ms 113.737 ms 113.250 ms
```

Not surprising really, I expected something like this would eventually occur and it'd either be from china or russia.

---

### Post by markp1989 on 2010-10-15
i get the same on my ssh login.

some one from leeds has been hammering on this thing all morning. 
[http://whatismyipaddress.com/ip/92.14.135.168](http://whatismyipaddress.com/ip/92.14.135.168)

```
grep fail auth.log | wc -l
4082

```

half of these attempts are from the same person 
```

$grep 92.14.135.168 auth.log | wc -l
2309
```

rest are from turkey [http://whatismyipaddress.com/ip/212.156.122.94](http://whatismyipaddress.com/ip/212.156.122.94)

edit: done a nmap on there ip, they have a load of services running```


mark@mark-laptop:~$ nmap 92.14.135.168

Starting Nmap 5.00 ( http://nmap.org ) at 2010-10-15 16:38 BST
Interesting ports on host-92-14-135-168.as43234.net (92.14.135.168):
Not shown: 982 closed ports
PORT      STATE    SERVICE
22/tcp    open     ssh
53/tcp    open     domain
80/tcp    open     http
110/tcp   open     pop3
111/tcp   open     rpcbind
113/tcp   open     auth
135/tcp   filtered msrpc
139/tcp   filtered netbios-ssn
143/tcp   open     imap
445/tcp   filtered microsoft-ds
548/tcp   open     afp
901/tcp   open     samba-swat
993/tcp   open     imaps
1720/tcp  filtered H.323/Q.931
2049/tcp  open     nfs
8080/tcp  open     http-proxy
10000/tcp open     snet-sensor-mgmt
10082/tcp open     amandaidx

Nmap done: 1 IP address (1 host up) scanned in 9.81 seconds
mark@mark-laptop:~$
```

---

### Post by slackthumbz on 2010-10-15
> **markp1989 said:**
> i get the same on my ssh login.

some one from leeds has been hammering on this thing all morning. 
[http://whatismyipaddress.com/ip/92.14.135.168](http://whatismyipaddress.com/ip/92.14.135.168)

```
grep fail auth.log | wc -l
4082

```

half of these attempts are from the same person 
```

$grep 92.14.135.168 auth.log | wc -l
2309
```

crikey, persistent SOB :shock:

---

### Post by Cuddles McKitten on 2010-10-15
I don't know why you're so down on PHP in your post.  Yes, you have to validate input in a few ways and be careful, but that's like saying C is stupid because of buffer overflows; sound programming practices eliminate security problems.  Wikipedia, for example, is a high-profile website that uses PHP exclusively and has had minimal security issues.

I do agree with your point about SSH though.  No reason to use anything but for remote access.


EDIT: [markp1989]("http://ubuntuforums.org/member.php?u=332495"), you might want to at least temporarily firewall someone who's failed several times to log in to your SSH server.  [OSSEC]("http://ossec.net") allows you to do that relatively easily.

---

### Post by slackthumbz on 2010-10-15
> **Cuddles McKitten said:**
> I don't know why you're so down on PHP in your post.  Yes, you have to validate input in a few ways and be careful, but that's like saying C is stupid because of buffer overflows; sound programming practices eliminate security problems.  Wikipedia, for example, is a high-profile website that uses PHP exclusively and has had minimal security issues.

I do agree with your point about SSH though.  No reason to use anything but for remote access.


EDIT: [markp1989]("http://ubuntuforums.org/member.php?u=332495"), you might want to at least temporarily firewall someone who's failed several times to log in to your SSH server.  [OSSEC]("http://ossec.net") allows you to do that relatively easily.

My distaste for PHP comes from my experience with a great many PHP "programmers" particularly in my work place. These are usually the kind of people that think dreamweaver is cool (it's evil) and that code re-use is a euphemism for cut and paste. I'm sure it's entirely possible to write good code in PHP. I just have yet to read any PHP code that didn't make me want to violently stab the author in the face.

My other issue with it is simply a matter of preference, I don't like mixing form and function. I use templates and perl/CGI for my site backend and a lightweight MVC that I wrote a while ago.

---

### Post by angryfirelord on 2010-10-15
Yeah, a lot of spam comes from Russia and China, so I guess it's not surprising that you got something from there. If it happens again, you may also want to block .ru addresses as well. While it won't stop the more malicious attacks, it will at least put some of the junior script kiddies at bay.

---

### Post by themarker0 on 2010-10-15
I remember this happened to me once. Though it was some newb in New York. So i simply just started sending 4mb pings at him until his address somehow became unreachable. Nevertheless to say, i haven't had a recent attack from him.

---

### Post by slackthumbz on 2010-10-15
> **themarker0 said:**
> I remember this happened to me once. Though it was some newb in New York. So i simply just started sending 4mb pings at him until his address somehow became unreachable. Nevertheless to say, i haven't had a recent attack from him.

Now there's an idea :twisted:

---

### Post by whoop on 2010-10-15
Was this the complete log of the attack, or just a part?
It's seems rather short...

---

### Post by themarker0 on 2010-10-15
> **slackthumbz said:**
> Now there's an idea :twisted:
 
Its was through rage, the kid actually emailed me telling me he was. >_>!

---

### Post by perspectoff on 2010-10-15
I'll put in a plug for knockd here.

Knockd allows you to hide your important ports and then reveal them only when a specific sequence of port requests are made.

It is useful in filtering out a lot of random attacks (including DoS-type attacks). (Yeah, I like the DoS ping counterattack used by the previous poster, but that is hardly the higher ground).

Linux is available to every kid worldwide (and increasingly accessible), so I think attacks will be increasing as Linux systems become even more widespread. While it may not be so easy to break into systems with good and proper security administration, this does not mean that the attempts do not slow down the Internet at large.

Deflecting even the attempts (with both good firewalls and knockd) is a good step, IMO.

So what I do, for example, is to use a custom SSH port (instead of 22) and that port is only revealed / opened using knockd.

---

### Post by slackthumbz on 2010-10-15
> **whoop said:**
> Was this the complete log of the attack, or just a part?
It's seems rather short...

That's the entire log, it looks like they were using a script that probably fired off those initial requests just to see if I was using any form of web-based remote admin for the site. Since none was found it probably gave up fairly quickly.

---

### Post by annoyingrob on 2010-10-16
> **Cuddles McKitten said:**
> Wikipedia, for example, is a high-profile website that uses PHP exclusively and has had minimal security issues.
Heaven forbid somebody hack in, and somehow change the site's content. ;)

---

### Post by inobe on 2010-10-16
the whole server is something else, i applaud you fellas for not stooping to their level and showing them the same consideration :)

---

### Post by slackthumbz on 2010-10-16
> **annoyingrob said:**
> Heaven forbid somebody hack in, and somehow change the site's content. ;)

Genuine LOL, well played sir. I wish I'd thought of that ;)

---

### Post by samjh on 2010-10-16
> **slackthumbz said:**
> Genuine LOL, well played sir. I wish I'd thought of that ;)

Ah, but some Wikipedia articles are "protected" against vandalism so that only authorised users can edit.

Clever call, but not complete. ;)

---

### Post by Sporkman on 2010-10-16
> **annoyingrob said:**
> Heaven forbid somebody hack in, and somehow change the site's content. ;)

:lol:

---

### Post by mainerror on 2010-10-16
OT: Yes I've been noticing the same attack attempts lately.

If they actually manage to find a host with a default configured (open) phpmyadmin then the admin of that machine deserves it. :p

---

