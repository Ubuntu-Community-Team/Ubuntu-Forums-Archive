---
title: "Cannot ping outside of the network"
date: 2013-01-02
forum: Server Platforms
---

### Post by achtyl on 2013-01-02
Please help if you are able, this thread is for a student project so please no arguing and insulting each other. For my senior project I chose to build a network with both a linix side and a windows side. I completed the windows build already and was able to add ubuntu 10.10 to the domain and i am struggling to add Ubuntu 10.10 server to the domian. Previously i had a gui installed to make the process easier, and something got corrupt inside of the os so i had to reinstall the server. now i cant even get updates or install the gui. i am also struggling to add the server to the domain, i recieve the error connection refused when i try to add the server to the domain. some one please help.

---

### Post by lykwydchykyn on 2013-01-02
Since you can't install things, can't get updates, and can't join the domain, one immediately would suspect a basic network connectivity issue.

Are you able to connect to any network services on the server?  Can you ping anything?

Also, why are you using 10.10?  It's not supported any more. (which may be another possible reason you aren't getting updates).

---

### Post by achtyl on 2013-01-02
i was able to ping before. i just finished the new install so i will check that now

---

### Post by achtyl on 2013-01-02
Nope i can not ping at all. i tried to ping google by ip and name and both failed. how can i resolve not getting to the internet?

---

### Post by lykwydchykyn on 2013-01-03
> **achtyl said:**
> Nope i can not ping at all. i tried to ping google by ip and name and both failed. how can i resolve not getting to the internet?

Without knowing any of the particulars of your network setup, that's hard to say, but the basics usually go like:

- Check cables and connections
- If something is handing out IP addresses (DHCP), make sure it's working
- If not, make sure you've entered the proper network configuration on the server.
- Ping some things by IP (e.g. 8.8.8.8) to make sure you aren't just missing DNS

A full-on "how to fix your non-working network connection" tutorial is more than anyone wants to type into a forum, but I'm sure they aren't hard to find.

---

### Post by spynappels on 2013-01-03
You should also consider using a current (LTS) version to ensure it is still receiving updates such as security and bug fixes.

Server 12.04 is the current LTS version.

---

### Post by Bucky Ball on 2013-01-03
10.10 has been out of support for quite some time, as mentioned. Go back, wrong way.

12.04 LTS server edition is what you should be using, as suggested. Have you talked to your lecturers/teachers/tutors/fellow students about your predicament???

---

### Post by achtyl on 2013-01-03
Ok so i did as you guys sugested and instaled 12.04 and so far so good. the only reason i went with 10.10 is the ease of adding it to the domain but i experanced problems there as well. for 12.04 is the process the same? will Likewise work here too?

---

### Post by koenn on 2013-01-03
should be the same or better

---

### Post by lykwydchykyn on 2013-01-03
I've joined 12.04 and 12.10 machines to the domain with Likewise, easy easy easy.

---

### Post by achtyl on 2013-01-04
Ok i have successfuly added the server to the domain. Thankyou for all your help i just have one more small problem and that is samba. i created a share by just creating a folder and sharing it. then on the windows side i tried to access it and i am propted with a request for credintals and neither Domain administrator or root credintals grant me access

---

### Post by Bucky Ball on 2013-01-04
Please post a new thread regarding your Samba issue and mark this one as Solved from Thread Tools. You dilute your chances of getting help by starting a new problem buried here on a thread with a title that doesn't relate. Cheers. ;)

---

### Post by achtyl on 2013-01-07
Thank you for all your help.

---

