---
title: "Potential Hack?"
date: 2008-09-15
forum: Security
---

### Post by mregister on 2008-09-15
Hello All,

I orginally posted this in the new user forum but it was suggested that I post it here:

Hello All,

I am new to Linux/Ubuntu and I have setup a Ubuntu/Lamp box and I was just looking through the apache2 log file and i have a lot of lines that read 70.63.86.162 - - [14/Sep/2008:11:38:09 -0500] "GET /~fareeda/ HTTP/1.1" 404 319 "-" "-". There is a long list of these and it seems that it's an alpabetical list of poetntial user names. That is just one line of many. What is this? What does it mean? Is this an attempted hack?

Thanks.

---

### Post by Dr Small on 2008-09-15
It's not really a hack, as he isn't breaching the security of your server. The bruteforce is to find a list of users on the server, but attempting to access their public_html space. It could be gathering these valid names for a list to bruteforce your ssh server (if you are running one), or could simply be used to access their files.

---

### Post by cariboo on 2008-09-15
What i would do is send a copy of the logs to the abuse email address belonging to that netblock. I just happened to look up the information for you:

```
Organization;I:CAPE-FEAR-COMMUNITY-COLLEGE
network:Tech-Contact;I:ipaddreg@rr.com
network:Admin-Contact;I:IPADD-ARIN
network:AbuseEmail:kpratt@cfcc.edu

```

Jim

---

### Post by cdenley on 2008-09-16
> **cariboo907 said:**
> What i would do is send a copy of the logs to the abuse email address belonging to that netblock. I just happened to look up the information for you:

```
Organization;I:CAPE-FEAR-COMMUNITY-COLLEGE
network:Tech-Contact;I:ipaddreg@rr.com
network:Admin-Contact;I:IPADD-ARIN
network:AbuseEmail:kpratt@cfcc.edu

```

Jim

Most e-mails sent to the address listed in a whois query bounce back. At least that is my experience from yesterday. I don't think I will bother trying to contact ISP's anymore. You might have more luck with a community college than some ISP in China, though.

---

### Post by cariboo on 2008-09-16
I seem to have better luck, I don't bother with Chinese adresses, but I have received answering email from ISP's in India and the States. It seems sending snippets of log files seem to help.

Jim

---

