---
title: "Multiple Dedicated Hardware for everything or Virtual Instances from one beefy server"
date: 2016-08-16
forum: Ubuntu, Linux and OS Chat
---

### Post by soamz on 2016-08-16
As im building the business plan for what hardware to order to dell or super micro, I need some help, as Im getting mixed opinions. 
Im going to offer Shared Hosting with HDD, Shared hosting with SSD, VPS Hosting with SSD, and Dedicated BareBones (when we get order, we will buy 1U server for each dedicated server client)

Some say, go for dedicated hardware for each type of hosting, means they said, 


get 1 server like single Xeon E5 1585 with 32GB of RAM and you can host like 1500+ shared hosting HDD clients and shared hosting SSD clients easily.

get 1 server 1 server like dual Xeon E5 1585 with 96GB of RAM and you can host like 100+ shared hosting HDD clients and shared hosting SSD clients easily.

And get 1 big Supermicro with 24 bays for RAID backup and auto backups of both shared hosting server and VPS server both to act as SAN storage and emergency backup restore. 
And some said,

get one beefy server, run Xen server in it and create 2 huge instances. 
One instance use Cloud Linux and offer shared hosting from it. 
And one instance use KVM+Openstack and offer VPS hosting from it. 

And And get 1 big Supermicro with 24 bays for RAID backup and auto backups of both shared hosting server and VPS server both to act as SAN storage and emergency backup restore.
Now Im confused, which one to finalize. 

I think,1st plan is better, as the fail rate would be much less, and we wont be depending on one single big server for everything, because if it fails, then whole business will go down until we replace it. 

What do you think ?

Which is better ?

---

### Post by howefield on 2016-08-16
Please use the default font properties in your postings.

Can you explain what your question(s) has to do with Ubuntu ?

---

### Post by soamz on 2016-08-16
We are looking to use Ubuntu instead of CentOS for our servers, so I think its better to take the experts help here in this forum too. 

Did you read my question ?

---

### Post by Habitual on 2016-08-16
> **soamz said:**
> What do you think ?Which is better ?
Since you asked.
You are up against some heavily vetted Hosting Provider$ and you have your work cut out for you.
I'd be thinking about how you are going to elevate your service(s) to that of your competition.
What software will you use to Manage, Monitor, and Deploy these Virtual assets?

Anybody can throw money at it. ;)

---

### Post by howefield on 2016-08-16
> **soamz said:**
> We are looking to use Ubuntu instead of CentOS for our servers, so I think its better to take the experts help here in this forum too. 

Did you read my question ?

Yes, I read your question, it has zero to do with Ubuntu.

Moved to a non support forum.. "*Ubuntu, Linux and OS Chat*"

---

### Post by grahammechanical on 2016-08-16
[http://www.ubuntu.com/cloud/openstack/managed-cloud](http://www.ubuntu.com/cloud/openstack/managed-cloud)

[http://www.ubuntu.com/download/cloud](http://www.ubuntu.com/download/cloud)

[URL="http://www.canonical.com/services"]http://www.canonical.com/services

[/URL]

---

### Post by SeijiSensei on 2016-08-16
> **Habitual said:**
> You are up against some heavily vetted Hosting Provider$ and you have your work cut out for you. I'd be thinking about how you are going to elevate your service(s) to that of your competition.
What software will you use to Manage, Monitor, and Deploy these Virtual assets?

Apropos to Habitual's comment, you'd have a hard time convincing me to migrate from Linode.

---

