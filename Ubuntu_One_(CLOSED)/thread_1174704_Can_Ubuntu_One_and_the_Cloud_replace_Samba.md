---
title: "Can Ubuntu One and the Cloud replace Samba"
date: 2009-05-31
forum: Ubuntu One (CLOSED)
---

### Post by Anzan on 2009-05-31
Getting a LAN to work correctly with Samba is kludgy. We have had to create mountpoints to consistently access directories on filseservers which is fine for desktops using ethernet but not so great for wireless laptops. Having to use tools that enter the grey areas of file systems created by proprietary vendors such as Microsoft is also not so great.

Will it be possible to just bypass all of this by using services like Ubuntu One or something involving Eucalyptus?  

I'm just an end user with little grasp as yet of the technologies involved.

---

### Post by gn2 on 2009-06-01
From what I've discovered about Ubuntu One (powered by Amazon), the answer to that seems to be not unless you can write your own server side component and install it on your own server on your own LAN.

---

### Post by Anzan on 2009-06-01
Yes, that is what we have in mind.

I'm just a user who knows a bit of bash, bit of Perl, bit of Python.

But we have people who can spit code through their teeth while riding Unix bareback. They just don't grok the cloud yet.

---

### Post by gotsanity on 2009-06-06
> **Anzan said:**
>  But we have people who can spit code through their teeth while riding Unix bareback. They just don't grok the cloud yet.

best... quote... evar!

---

### Post by cariboo on 2009-06-07
I understand that the cloud ( i hate that term) has it uses, but my server has close to 600Gb of data on it. Unless internet speeds pick up quite a bit I'll keep my personal server, plus I can personally look after backing up myself through the usage of custom made scripts.

BTW I can't create a script from scratch, but there a plenty of suitable scripts on the internet that can be modified to suit my purposes. :)

---

### Post by Anzan on 2009-06-08
What I'm wondering is if there will be a paradigm shift away from the MS based network shares system.

---

### Post by pookiebear on 2009-06-08
> **gotsanity said:**
> best... quote... evar!


They will when google starts selling ERP and Healthcare management apps based on user login times or input times. Cloud is cool. We just need to bump the encryption up a notch beyond 128 bit is my biggest gripe. Cloud would be nice for a lot of customers I have now as they have so much crap to backup they don't even remember what 90% of it was or who created it. But I have to make sure it gets put on tape every night. If you think about it simpler terms. Cloud is just a fancy front end for FTP if all you are talking about is storage. If you want to get on the app side of it then the coders get to make cool front ends for the databases. But those databases are still some for of SQL or close to it.

---

### Post by Wiebelhaus on 2009-06-08
> **Anzan said:**
> Getting a LAN to work correctly with Samba is kludgy. We have had to create mountpoints to consistently access directories on filseservers which is fine for desktops using ethernet but not so great for wireless laptops. Having to use tools that enter the grey areas of file systems created by proprietary vendors such as Microsoft is also not so great.

Will it be possible to just bypass all of this by using services like Ubuntu One or something involving Eucalyptus?  

I'm just an end user with little grasp as yet of the technologies involved.

I run a office and home networks all using Samba as well as a few customer locations with 3-5 workstations all with servers and so forth and have never had any issues with Samba and actually prefer it to NT networking so if your having issues post a support thread and pm it to me just in case I miss it and I will provide you with all the information you need to properly configure your network , I'm actually surprised your having any major issues with Samba , somethings a miss.

And no , I don't think dropbox or ONE will replace traditional networking or even be a viable substitute to be honest.

---

### Post by Wiebelhaus on 2009-06-08
> **cariboo907 said:**
> I understand that the cloud ( i hate that term) has it uses, but my server has close to 600Gb of data on it. Unless internet speeds pick up quite a bit I'll keep my personal server, plus I can personally look after backing up myself through the usage of custom made scripts.

BTW I can't create a script from scratch, but there a plenty of suitable scripts on the internet that can be modified to suit my purposes. :)

No kidding mate.

---

### Post by Anzan on 2009-06-09
> **Wiebelhaus said:**
> I run a office and home networks all using Samba as well as a few customer locations with 3-5 workstations all with servers and so forth and have never had any issues with Samba and actually prefer it to NT networking so if your having issues post a support thread and pm it to me just in case I miss it and I will provide you with all the information you need to properly configure your network , I'm actually surprised your having any major issues with Samba , somethings a miss.

And no , I don't think dropbox or ONE will replace traditional networking or even be a viable substitute to be honest.

Actually, I've just upgraded several boxen to 9.04 and all is flawless. It was fine in 7.04-.10 but borked in 8.04 and 8.10.

Thank you for your offer.

---

