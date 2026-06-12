---
title: "rkhunter scalper worm"
date: 2012-03-27
forum: Security
---

### Post by pfunk24 on 2012-03-27
Just ran rkhunter and received the following error:

Warning: Scalper Worm                             [ Warning ]
         File '/tmp/.a' found

How do I remove this from Ubuntu Server 10.04?  I tried to delete file and kill process, but neither works.

Thanks,

---

### Post by CharlesA on 2012-03-27
Check to see what process is using those files:

```
sudo lsof /tmp/.a
```

---

### Post by Dangertux on 2012-03-27
Do you think it's possible that /tmp/.a is just a temporary file you or some non-malicious application created? 

That's a pretty broad flag to say that  you have the scalper worm, especially considering scalper spread through vulnerable versions of Apache 1.3.x and 2.0.x. So unless you're running a VERY old webserver, it's highly unlikely you have the scalper worm

```

rm -f /tmp/.a 

```

should get rid of the file though you should do what Charles said and find out what's using it. Alternatively I like fuser as well for that purpose.

```

fuser /tmp/.a

```

Hope this helps.

---

### Post by pfunk24 on 2012-03-27
Thanks for the reply.

Ran lsof and .jboss is using the file.

---

### Post by Dangertux on 2012-03-27
In that case you might consider this...

> 
Red Hat has become aware of a worm  currently affecting unpatched or unsecured servers running JBoss  Application Server and products based on it.  This worm propagates by  connecting to unprotected JMX consoles, then uses the ability of the JMX  console to execute arbitrary code in the context of the JBoss user. 
 
The  worm affects users of JBoss Application Server who have not correctly  secured their JMX consoles as well as users of older, unpatched versions  of JBoss enterprise products.  An update to JBoss enterprise products  was produced in April 2010 to correct the flaw, [CVE-2010-0738]("https://access.redhat.com/kb/docs/DOC-30741")
 
Instructions for securing the JMX console are available here:  [http://community.jboss.org/wiki/SecureTheJmxConsole]("https://community.jboss.org/docs/DOC-12190").


---

### Post by pfunk24 on 2012-03-27
Once I secure Jboss, how do you suggest removing the worm?

---

### Post by Ms. Daisy on 2012-03-27
If it were me I would back up my data & reinstall everything.  Then I would secure Jboss.

---

### Post by CharlesA on 2012-03-27
> **Ms. Daisy said:**
> If it were me I would back up my data & reinstall everything.  Then I would secure Jboss.
That would be what I would do as well.

---

### Post by pfunk24 on 2012-03-27
Ok, thanks

---

