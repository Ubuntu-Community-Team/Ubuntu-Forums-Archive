---
title: "Any concern."
date: 2019-01-24
forum: Ubuntu, Linux and OS Chat
---

### Post by poorguy on 2019-01-24
I ran across these links and wonder if this fixed through the updates or do I need to run the commands listed below.


[https://www.theregister.co.uk/2019/01/22/debian_package_manager_flaws/](https://www.theregister.co.uk/2019/01/22/debian_package_manager_flaws/)

[https://justi.cz/security/2019/01/22/apt-rce.html](https://justi.cz/security/2019/01/22/apt-rce.html)



sudo apt update -o Acquire::http::AllowRedirect=false 

sudo apt upgrade -o Acquire::http::AllowRedirect=false


Thanks

---

### Post by yetimon_64 on 2019-01-24
Running 14.04 LTS here I checked and found I was vulnerable according to this [[COLOR=#0000ff]--link--[/COLOR]]("https://usn.ubuntu.com/3863-1/").

The updated/patched version for apt in 14.04 is apt-1.0.1ubuntu2.19.
Up till now I was using apt-1.0.1ubuntu2.18.
After doing a standard update/upgrade I now am using apt-1.0.1ubuntu2.19.

It appears from the link above this is fixed with the latest updates in 14.04, 16.04 and 18.04.
Just doing a standard update/upgrade fixed the vulnerability here, so shouldn't be a concern from now on.

Regards, yeti

---

### Post by poorguy on 2019-01-25
Hey Yetimon_64,

I'm using 18.04 and just checked and I'm using***  apt-1.6.6ubuntu0.1*** so I'm good.


 Thanks. :cool:

---

