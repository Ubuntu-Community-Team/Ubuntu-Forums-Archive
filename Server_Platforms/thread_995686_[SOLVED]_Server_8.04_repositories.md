---
title: "[SOLVED] Server 8.04 repositories"
date: 2008-11-28
forum: Server Platforms
---

### Post by any.linux12 on 2008-11-28
HI!

I'm having problems with apt-get update and apt-get upgrade, like when type the apt-get update gives me problem   

> esp-admin@espSRV01:/etc/apt$ sudo apt-get update 
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not resolve 'security.ubuntu.com'                 
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'                            
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'                                  
Err [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) dapper Release.gpg                        
  Could not resolve 'ch.archive.ubuntu.com'                                
Err [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) dapper/main Translation-en_US             
  Could not resolve 'ch.archive.ubuntu.com'                                
Err [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) dapper/restricted Translation-en_US       
  Could not resolve 'ch.archive.ubuntu.com'                                
Err [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) dapper-updates Release.gpg                
  Could not resolve 'ch.archive.ubuntu.com'                                
Err [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) dapper-updates/main Translation-en_US     
  Could not resolve 'ch.archive.ubuntu.com'                                
Err [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) dapper-updates/restricted Translation-en_US
  Could not resolve 'ch.archive.ubuntu.com'                                 
Reading package lists... Done                                               
W: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://ch.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not resolve 'ch.archive.ubuntu.com'

W: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/dists/dapper/main/i18n/Translation-en_US.bz2](http://ch.archive.ubuntu.com/ubuntu/dists/dapper/main/i18n/Translation-en_US.bz2)  Could not resolve 'ch.archive.ubuntu.com'

W: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/dists/dapper/restricted/i18n/Translation-en_US.bz2](http://ch.archive.ubuntu.com/ubuntu/dists/dapper/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'ch.archive.ubuntu.com'

W: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://ch.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Could not resolve 'ch.archive.ubuntu.com'

W: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/i18n/Translation-en_US.bz2](http://ch.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'ch.archive.ubuntu.com'

W: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/i18n/Translation-en_US.bz2](http://ch.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'ch.archive.ubuntu.com'                                                                                                                                                  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'                                                                                                                                                     

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

But i think that my source.list is ok couse is the same that I use in other server.

Any help please!!!

---

### Post by jfernand on 2008-11-28
It looks like you are trying to use a sources.list file from Dapper6.06 to upgrade a Hardy 8.04 Distribution.

---

### Post by prshah on 2008-11-28
> **any.linux12 said:**
> 
I'm having problems with apt-get update and apt-get upgrade, like when type the apt-get update gives me problem   
[code]esp-admin@espSRV01:/etc/apt$ sudo apt-get update
Could not resolve 'security.ubuntu.com'
Could not resolve 'security.ubuntu.com'
Could not resolve 'security.ubuntu.com'


Doesn't look as though you are connected to the 'net, and/or a DNS problem... among other problems.

---

### Post by any.linux12 on 2008-11-28
lol. I was updating from dapper because I had copy the source.list file from a dapper server. But now I changed the source.list and I still have the same problem

> esp-admin@espSRV01:/etc/default$ sudo apt-get update 
Err [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) hardy Release.gpg
  Could not resolve 'ch.archive.ubuntu.com'
Err [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) hardy/main Translation-en_US
  Could not resolve 'ch.archive.ubuntu.com'
Err [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) hardy/restricted Translation-en_US
  Could not resolve 'ch.archive.ubuntu.com'
Err [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) hardy/universe Translation-en_US
  Could not resolve 'ch.archive.ubuntu.com'
Err [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) hardy/multiverse Translation-en_US
  Could not resolve 'ch.archive.ubuntu.com'
Err [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) hardy-updates Release.gpg
  Could not resolve 'ch.archive.ubuntu.com'
Err [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) hardy-updates/main Translation-en_US
  Could not resolve 'ch.archive.ubuntu.com'
Err [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
  Could not resolve 'ch.archive.ubuntu.com'
Err [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) hardy-updates/universe Translation-en_US
  Could not resolve 'ch.archive.ubuntu.com'
Err [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
  Could not resolve 'ch.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://ch.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'ch.archive.ubuntu.com'

W: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://ch.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not resolve 'ch.archive.ubuntu.com'

W: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://ch.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'ch.archive.ubuntu.com'

W: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://ch.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Could not resolve 'ch.archive.ubuntu.com'

W: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://ch.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'ch.archive.ubuntu.com'

W: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://ch.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Could not resolve 'ch.archive.ubuntu.com'

W: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://ch.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'ch.archive.ubuntu.com'

W: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://ch.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'ch.archive.ubuntu.com'

W: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://ch.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'ch.archive.ubuntu.com'

W: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://ch.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'ch.archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems


---

### Post by MJN on 2008-11-28
As prshah says it looks like a network/DNS connectivity issue. Does that machine have internet access? Does **host security.ubuntu.com** resolve correctly?
 
Mathew

---

### Post by any.linux12 on 2008-11-28
I'm almost sure that I've internet access couse i can ping ip like ex. 74.125.19.104

---

### Post by MJN on 2008-11-28
DNS?
 
Did the host command work?
 
Mathew

---

### Post by any.linux12 on 2008-11-28
ok probably I have a problem with DNS configuration in this server. But I don't want this new server as DNS server because I have other that makes that.

How do I configure that???

---

### Post by any.linux12 on 2008-11-28
> DNS?

Did the host command work?


No, they don't work :(
What can I do???

---

### Post by any.linux12 on 2008-11-28
ok I fond it

/etc/resolv.conf

and change a little thing

thanks anyway

---

