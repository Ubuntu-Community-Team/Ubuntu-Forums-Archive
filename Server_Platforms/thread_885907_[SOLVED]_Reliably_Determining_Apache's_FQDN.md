---
title: "[SOLVED] Reliably Determining Apache's FQDN"
date: 2008-08-10
forum: Server Platforms
---

### Post by Jesdisciple on 2008-08-10
```
$ sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
```A similar message is given when I stop it.  It was working when I went to bed yesterday...

Help?

---

### Post by ikonia on 2008-08-10
no problem on this one.

In your apache config file you'll find "ServerName" parameter.

when apache starts it will try to resolve this parameter if it's set to an IP address,

eg: if ServerName = mymachine

your machine will do a lookup on mymachine to get an IP address to start apache against

eg: nslookup mymachine = 192.168.1.1 apache will start bound to 192.168.1.1

so if you want this to work you need to make sure that your machines ServerName varible is set to a hostname that can be resolved.

if it's not set or can't be resolved it will fall back to localhost - which is what your seeing.

---

### Post by Jesdisciple on 2008-08-10
Then I guess that's not my real problem; I want localhost because this is a development server.  I guess I should make a new thread with a more relevant title.

---

### Post by MJN on 2008-08-11
That's fine - just set it to localhost (this will resolve via /etc/hosts anyway). It might well prefer a fully qualified in which case use localhost.localdomain.

Note it's only a warning - Apache really has to know what it's called for various reasons (loop detection in self-referrals is one) as so in the absence if you telling it what it's called it's had to go with whatever it felt best. Set it straight with a Servername directive and it will thank you for it.

Mathew

---

### Post by Jesdisciple on 2008-08-11
Oh, that is *a* problem...  Why is it resolving to 127.0.1.1 instead of 127.0.0.1?  That might be a symptom of the bigger problem for all I know.
**the top of /etc/hosts**> 127.0.0.1	localhost
127.0.1.1	Jesdisciple-laptopI can access the filesystem via the second, which is more than I can do on the first.  (I have now changed ServerName, but I want to follow every possible clue.  :sherlock: )

---

### Post by MJN on 2008-08-11
I'm not sure I understand your question.

Have you now set Servername to localhost? Is Apache now not complaining, and is it responding to [http://localhost](http://localhost) ?

Mathew

---

### Post by dmizer on 2008-08-11
Don't worry about this at all.  I get the same error on starting my Apache2 server, but I can access it both from localhost and from other computers on the local network.

---

### Post by MJN on 2008-08-11
You really ought to set it properly as you can run into trouble with the uncertainty of leaving Apache to deduce its own identity. It also allows extended features such as name-based virtual hosting.

Mathew

---

### Post by Jesdisciple on 2008-08-11
I have set ServerName to localhost and the server does respond to [http://localhost](http://localhost).  As it happens much too often, my point is being completely missed.> **Jesdisciple said:**
> Why is it resolving to 127.0.1.1 instead of 127.0.0.1?  That might be a symptom of the bigger problem for all I know. ... (I have now changed ServerName, but I want to follow every possible clue.  :sherlock: )Why would it not use the default loopback IP of 127.0.0.1?  Why increment the third number?  EDIT: My issue is no longer what the server answers to, but how it thinks of itself.

---

### Post by MJN on 2008-08-11
See your [other thread](http://ubuntuforums.org/showthread.php?p=5568353), and do please keep all topics within a single thread as it makes it difficult for others to follow.

(for those that are reading here it is down to the machine name being mapped to 127.0.1.1 in /etc/hosts and in the absence of being told otherwise Apache has determined that it is using the host machine's name)

Mathew

---

### Post by Jesdisciple on 2008-08-11
I still feel my point is being missed somehow.  But it seems I can't change that.

I apparently need to use a broader definition of "topic."

---

### Post by MJN on 2008-08-11
Start again at the beginning and we'll give it another shot...

Mathew

---

### Post by MJN on 2008-08-11
I just noticed one of your previous edits:

> EDIT: My issue is no longer what the server answers to, but how it thinks of itself.If that's what confusing you let me elaborate...

The only reason Apache considered itself to be '127.0.1.1' was because you didn't give it any sense of identity using the Servername directive. Hence it found out the name of the machine (via a call that would've looked in /etc/hostname) and found Jesdisciple-laptop. It then found your mapping in /etc/hosts which said this name mapped to the IP address 127.0.1.1 and hence used that as its 'identity'.

Does that make it clearer?

You might prefer to stick to the one loopback address and alias it in /etc/hosts to multiple names:

127.0.0.1 localhost jesdisciple-laptop

This way any reference to that single machine results in the same mapping (as it ought to).

Mathew

P.S. I am assuming we are talking about a single machine here, and it's your laptop!

---

### Post by Jesdisciple on 2008-08-11
> **MJN said:**
> Does that make it clearer?Yes, much clearer.  I thought the mapping was going the other direction, i.e. "I am 127.0.1.1 therefore I am Jesdisciple-laptop."  Kind of like a reverse DNS lookup.

Thanks!

---

### Post by MJN on 2008-08-11
Ah that's good...

I'm off to lie down now... your two threads alone have tired me out... ;)

Mathew

---

### Post by dmizer on 2008-08-11
Not to be contrary here, but this doesn't actually solve any problems:
```
dmizer@tokkyu:~$ cat /etc/hostname 
tokkyu
dmizer@tokkyu:~$ cat /etc/hosts
127.0.0.1 localhost tokkyu
127.0.1.1

# The following lines are desirable for IPv6 capable hosts
[snip]
dmizer@tokkyu:~$ sudo /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server...                                   
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
                                                                         [ ok ]
```

I finally spent some time researching this error (I was not concerned about it at all before).  I was able to fix the problem by adding this line:
```
ServerName tokkyu
```
to /etc/apache2/apache2.conf

---

### Post by Jesdisciple on 2008-08-12
@dmizer:  ...Huh?  Based on your post, I would have guessed that you have the problem, but your rank and the fact that you haven't previously posted in this thread indicate otherwise.

---

### Post by MJN on 2008-08-12
> **dmizer said:**
> Not to be contrary here, but this doesn't actually solve any problems

Dmizer, do us a favour please and actually read the thread?

The suggestion to populate the Servername directive was suggested by Ikonia in post #2!

The discussion of /etc/hosts manipulation was as part of an explanation as to why Apache was using 127.0.1.1 and not 127.0.0.1 (which you have demonstrated given Apache is now using 127.0.0.1 in the absence of a Servername directive). It is not a means of avoiding the Servername warning message which you really ought to heed.

Mathew

---

### Post by dmizer on 2008-08-12
> **MJN said:**
> Dmizer, do us a favour please and actually read the thread?

The suggestion to populate the Servername directive was suggested by Ikonia in post #2!
Believe me, I read the whole thread. The directions in post #2 were too vague even for me, but that may be because I've migrated nearly everything to LightTPD now, and I haven't used Apache in quite some time.

> **MJN said:**
> The discussion of /etc/hosts manipulation was as part of an explanation as to why Apache was using 127.0.1.1 and not 127.0.0.1 (which you have demonstrated given Apache is now using 127.0.0.1 in the absence of a Servername directive).
This is the part I failed to read closely enough, my apologies.

> **MJN said:**
> It is not a means of avoiding the Servername warning message which you really ought to heed.

Mathew

This Apache server is local only (I recalled that Jesdisciple indicated the same), and is on an isolated subnet.  I don't even recall even why I installed it in the first place.  In fact, I haven't even turned the thing on for about 2 years.  I simply remembered (upon reading this thread) that this server had the domain name error but I also remembered that the server functioned exactly as needed despite the error.

To be sure, if this server was live, I would have been more concerned about it.

---

