---
title: "Apt Authentication issue"
date: 2008-06-10
forum: Security
---

### Post by secure bit on 2008-06-10
Hi guys

I receive this message when I login to my system :



Apt Authentication issue
The package list update failed with a authentication failure. This usually happens behind a network proxy server. Please try to click on the "Run this action now" button to correct the problem or update the list manually by running Update Manager and clicking on "Check".

I believe that my isp trying to fool me to get some malicious software installed on my system through altering some software that I should get for upgrade, what counter actions can I do ? where can I find the temporary list to compare the fake list to the original list and find the difference ??

Note : I don't use a proxy at all !

---

### Post by /etc/init.d/ on 2008-06-10
Run **sudo apt-get update** in a terminal and copy and paste the output here.

---

### Post by acrostic on 2008-06-10
Possibly you have added third party repository in your apt configuration,

Please paste contents of /etc/apt/sources.list file 

Thanks


> **secure bit said:**
> Hi guys

I receive this message when I login to my system :



Apt Authentication issue
The package list update failed with a authentication failure. This usually happens behind a network proxy server. Please try to click on the "Run this action now" button to correct the problem or update the list manually by running Update Manager and clicking on "Check".

I believe that my isp trying to fool me to get some malicious software installed on my system through altering some software that I should get for upgrade, what counter actions can I do ? where can I find the temporary list to compare the fake list to the original list and find the difference ??

Note : I don't use a proxy at all !

---

### Post by secure bit on 2008-06-11
this is part of update process :

Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources [906B]                         
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages [42.2kB]                        
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources [7036B]                          
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages [7687B]                       
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources [1433B]                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Packages                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Sources
Fetched 394kB in 3min32s (1860B/s)
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

---

### Post by tinny on 2008-06-11
This bug report should help you.

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/24061]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/24061")

Note the last few comments that talk about a work around

---

### Post by secure bit on 2008-06-11
Note : when I try sudo apt-get update from another isp I get no error message !

its clear that this is in purpose

where can I find exactly the milicious part in the package list ?

---

### Post by secure bit on 2008-06-11
> **tinny said:**
> This bug report should help you.

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/24061]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/24061")

Note the last few comments that talk about a work around
the answer was :

> By simply waiting. This happens at times during archive updates.

the problem isn't the update time 

my current isp every time I MUST get the error, once I take my computer to another isp I get no problem !

---

### Post by tinny on 2008-06-11
> the problem isn't the update time .

True.

If you had read the whole bug report you will see its a caching issue between a Ubuntu install and the repositories.

> I believe that this error is caused by a caching proxy which returns stale files, instead of actually retrieving the latest files from the mirror and returning that. In my case, it is a transparent squid proxy.

This can be some sort of proxy your ISP may have in place (doesn't have to be your proxy) or anywhere else on the route between you and the repositories.

Reading the bug report further will also describe the work around for you.

---

### Post by secure bit on 2008-06-17
thank you tinny

---

