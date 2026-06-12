---
title: "bind on local network problems help please"
date: 2012-09-20
forum: Server Platforms
---

### Post by tombruton87 on 2012-09-20
IM trying to setup bind on a local network, what I am trying to do is setup a local intranet and network login.

What I want to do is convert and ipaddress to a domain name

so when somebody goes to there browser and enters example.com it will take them to 192.168.1.2

happy to do it in terminal or using webmin any help much appreciated

---

### Post by cybercity@localhost on 2012-09-23
you need to add zone record in your bind configuration. using webmin is easiest way to create zone records. install webmin, go to servers and select bind dns server.

Now you will see **BIND DNS SERVER** and various icons.

First we have to create forward zone click on create master zone

in Zone Type : Select Forward

in Domain name / Network , type the name you want to configure your domain with.

type your email address and click create.

As shown in image belew...
[IMG]http://i47.tinypic.com/34jetyf.png[/IMG]
now we'll create reverse zone Click on create master zone

now because we're creating a reverse zone so our zone type will become from Forward to reverse.
 
As Shown in image below

[IMG]http://i48.tinypic.com/29qfk2u.png[/IMG]

click on create.... now click Apply Configuration at top left.

now do a nslookup to check your domain.

nslookup test.com

---

