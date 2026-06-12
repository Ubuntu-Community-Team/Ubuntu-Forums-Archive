---
title: "Server will not update"
date: 2012-11-01
forum: Server Platforms
---

### Post by Dmaxx67 on 2012-11-01
HAving this isssue for a week now. I run sudo apt-get update and get this:
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease
  
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease
  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease
  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/precise/InRelease)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/InRelease)  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/InRelease](http://security.ubuntu.com/ubuntu/dists/precise-security/InRelease)  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg)  Temporary failure resolving 'security.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.

I followed this site and hardened my server security. [http://www.thefanclub.co.za/how-to/how-secure-ubuntu-1204-lts-server-part-1-basics](http://www.thefanclub.co.za/how-to/how-secure-ubuntu-1204-lts-server-part-1-basics)
It worked after i did all those things. Anyways I am running a static ip and Wildblue as my service provider. I cant set my own dns becuase their modem overrides it. Tried to upgrade to 12.10 and it says no new release. I can install packages like logwatch and such though and i have pinged google and its all there but no apt-get update. Any help is appreciated.

---

### Post by chadk5utc on 2012-11-02
This looks like 2 issues... Has anything on your Network changed? Has your ISP changed anything?? 
The following indicates a DNS issue
  Temporary failure resolving 'security.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease
  
Also package management issues
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...ates/InRelease](http://us.archive.ubuntu.com/ubuntu/...ates/InRelease)
W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...rity/InRelease](http://security.ubuntu.com/ubuntu/di...rity/InRelease) 

Have a look at this hopefully it will point you at least in the right direction:
[http://askubuntu.com/questions/91543/apt-get-update-fails-to-fetch-files-temporary-failure-resolving-error](http://askubuntu.com/questions/91543/apt-get-update-fails-to-fetch-files-temporary-failure-resolving-error)

---

### Post by Dmaxx67 on 2012-11-02
Problem solved I had to put my Wildblue Dns addresses under networkinterfaces.

---

### Post by Vegan on 2012-11-02
my isp was having all kinds of problems with their DNS servers so I upped my DNS server and now use that

along with a boat load of forwards

---

