---
title: "Need help for an email server"
date: 2009-06-29
forum: Server Platforms
---

### Post by ReneTheriault on 2009-06-29
Hi,

I'm searching for a tutorial or help to install an Ubuntu email server.  

This server will be for a schoolboard and they asking me to have a Postfix/Cyrus configuration that authenticate against Active directory.

I searched Google and forums and did'nt find anything interesting that include those 3 aspects.

Does anyone can help me?

Thanks!

---

### Post by dlehman on 2009-07-04
Ah someone in the same boat I am.  
I am also setting up an email system my two requirements are AD authentication and IMAP.  
I am going to setup a student mail server first which I would like to restrict to internal only and the staff email domain.  
Then once I get a good grasp of the setup move the teachers from First Class to an Ubuntu Mail server.  
I am not picky about MTA I just need to get it working.  
I will post here when I get something working.  


dlehman.

---

### Post by black_shadow on 2009-07-05
Hi All

Try this as it is easy to setup no complicated configuration to do
```

http://www.citadel.org/doku.php/installation:easyinstall:easyinstall
```

Dont install from repo as it doesnt work.

Mike

---

### Post by windependence on 2009-07-05
I think Zimbra open source edition will do all of this for you. It's a lot less troublesome than building everything yourself and you still have the underlying components if you need to tweak something. There also is a very active online support community. I have several of these running on 8.04 LTS if you need help.

[http://www.zimbra.com/community/downloads.html](http://www.zimbra.com/community/downloads.html)

[http://wiki.zimbra.com/index.php?title=Ubuntu_8.04_LTS_Server_(Hardy_Heron)_Install_Guide](http://wiki.zimbra.com/index.php?title=Ubuntu_8.04_LTS_Server_(Hardy_Heron)_Install_Guide)

Forums:   [http://www.zimbra.com/forums/](http://www.zimbra.com/forums/)

-Tim

---

### Post by dlehman on 2009-07-07
Thank you for the replies.
  
Black_Shadow I tried citadel before posting this I don’t think it fits very well, the look and feel were just off to me, it looks to be a good program though.  

ReneTheriault a few tips if you decide on zimbra
Install from ssh such as putty so you can scroll
Check the time zone setting it threw me off it is option 1-6
And of course the admin password at option 3-4

Windependence I like zimbra I think it will work but I have a couple questions and need help with it.  
First my setup is 

Zimbra box 	zimbra.school.local	1.40

AD+DNS	host.domain.school.k12.oh.us	1.44 & 1.45

Zimbras /etc/resolv.conf has two name server entries for 1.44 1.45

In AD DNS I created a new primary zone school.local and added two records

An A record for zimbra.school.local with ip 1.40

A MX record with address zimbra.school.local

Now I can send email from zimbra to school.k12.oh.us just fine

I can browse from my desktop on the school domain to zimbra.school.local just fine

I cannot send email from school.k12.oh.us to zimbra 

And MX record check in zimbra fails.

I have three questions

1 how do I setup mx record properly

2 can I set and permitted to domains list and block all others 

3 can I filter for and be altered of key words 

Thank you for your help in advance.

dlehman

---

