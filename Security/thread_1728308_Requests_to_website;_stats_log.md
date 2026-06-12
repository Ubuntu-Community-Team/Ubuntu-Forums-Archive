---
title: "Requests to website; stats log"
date: 2011-04-13
forum: Security
---

### Post by .Guest. on 2011-04-13
Below is the print out of requests, with the website address  "#.com". The requests are listed in the order in which they appear on the stats page. What does it mean?:
```

#.com/

#.com/?Mode=debug

#.com/?cmd=Config

#.com/?M=A

#.com/?

#.com/?ho+{COMPLETE VERSION}

#.com/?<IMG SRC=\"javascript:alert(cross_site_scripting.nasl);\">

#.com/?<script>cross_site_scripting.nasl</script>

#.com/?urlmaskfilter=<script>foo</script>

#.com/?p=subscribe

#.com/?

#.com/?username=\"<script>foo</script

#.com/?mod=read&id=../../../../../../../../../../../../../etc/passwd%00

#.com/?user=#_user_sql_injection.nasl' UNION SELECT 2, 'admin','#','Administrator'--&file=index&pass=

#.com/icons/

#.com/icons/?\><script>alert('struts_sa_surl_xss.nasl')</script>
```

Thanks.

---

### Post by CandidMan on 2011-04-13
At a glance it looks like someone's been trying javascript and SQL injections to get sensitive data. Looks like they might have gained access to the /etc/passwd file as well and might be trying to crack it.

Sorry can't tell you much more than that, maybe someone else can

I'm guessing > $1$RxS1R0tX$IzA1S3fcCfyVA9rwKBMi is your hashed password. Given enough time and a weak enough password, this person could get the real password

---

### Post by bodhi.zazen on 2011-04-13
You are correct, those are all cracking attempts.

Assuming the server is properly configured, probably nothing to it.

Put that code in a browser and see what you get.

These two are probably the most concerning :

> #.com/?mod=read&id=../../../../../../../../../../../../../etc/passwd%00

#.com/?user=jjnms_user_sql_injection.nasl' UNION SELECT 2, 'admin','$1$RxS1R0tX$IzA1S3fcCfyVA9rwKBMi.','Administrator'--&file=index&pass=

The short story is these are like watching the logs if you are running a ssh server.

You need to make sure apache, php, mysql are secure with secure passwords ;)

You can also look at mod_security

---

### Post by EJeanmaire on 2011-04-13
nasl = NESSUS plugin.  Someone is vulnerability scanning your website, most likely with the unsafe/website attack plugins enabled.

> **CandidMan said:**
> At a glance it looks like someone's been trying javascript and SQL injections to get sensitive data. Looks like they might have gained access to the /etc/passwd file as well and might be trying to crack it.

Sorry can't tell you much more than that, maybe someone else can

I'm guessing  is your hashed password. Given enough time and a weak enough password, this person could get the real password

No, its not his password, its NESSUS trying to inject that user.

---

### Post by dfreer on 2011-04-13
> **bodhi.zazen said:**
> 

```
#.com/?mod=read&id=../../../../../../../../../../../../../etc/passwd%00

#.com/?user=jjnms_user_sql_injection.nasl' UNION SELECT 2, 'admin','$1$RxS1R0tX$IzA1S3fcCfyVA9rwKBMi.','Admin istrator'--&file=index&pass= 
```

Put that code in a browser and see what you get.



+1. You'll also want to check the actual apache logs to see whether it served the page (200 OK) or didn't (404 or something similiar).

Also, the first bit of code is simply trying a Directory Transversal, to see if it can grab your /etc/passwd file. And it does appear like the second one is trying to insert a user, that hash is a passwd hash.

---

### Post by .Guest. on 2011-04-19
How would you instruct a complete newbie how to

1 Set up their own server (linux)
2 Set up a security system to monitor (see) this kind of attack
3 Set up security to prevent this kind of atack

?
Thank you all for your replies.

---

### Post by bodhi.zazen on 2011-04-19
> **.Guest. said:**
> Thank you all for your replies. The hosting company has not offered much support for this.

How would you instruct a complete newbie how to

1 Set up their own server (ubuntu, debian or other linux os)
2 Set up a security system to monitor (see) this kind of attack
3 Set up security to prevent this kind of atack
4 Host their own websites on this server

What can a newbie do to monitor and prevent this type of attack, if the site is still on hosting company's servers?

Thank you, again

That is a ton of information to ask for, and whole books have been written on each of your questions.

Server guide : [https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

In terms of monitoring, see the security stickies. There is information on both HIDS and NIDS.

You may also want to look at hardening each of the servers and / or mod_security.

[http://www.howtoforge.com/apache_mod_security](http://www.howtoforge.com/apache_mod_security)

mod_security takes some time to learn ;)

---

### Post by Doug S on 2011-04-19
I just wanted to add one note to bodhi's reply: Myself, I much prefer to download and use the PDF versions of the server guides. Then I can print pages and add handwritten notes and such specific to my application. However, I always have difficulty finding the PDF versions. They are in the same locatation as the html but called serverguide.pdf (which I rename upon download to reflect the version, i.e. serverguide1004.pdf.)
[https://help.ubuntu.com/10.04/serverguide/C/serverguide.pdf](https://help.ubuntu.com/10.04/serverguide/C/serverguide.pdf) 
if you want the 10.10 stuff just change that part of the link.

---

