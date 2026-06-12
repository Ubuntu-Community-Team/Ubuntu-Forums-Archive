---
title: "Update Apache to the newest version via apt-get (Ubuntu Server 8.10)"
date: 2011-05-31
forum: Server Platforms
---

### Post by mat3us on 2011-05-31
Good afternoon,

 I have a server with Ubuntu 8.10 installed. The version of Apache and some other packages are outdated, probably due to the discontinuity of this version of Ubuntu, when running, for example, an "apt-get upgrade apache2" is not given an opportunity to upgrade. The version of apache is installed Apache/2.2.9 (Ubuntu).
 I've tried to add the repositories below (as the official distribution no longer exist) and they have no updates as well.

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-updates main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-updates main restricted universe multiverse


 I was experimenting with the repositories of newer versions (9.04 and 9.10 and later) and also unsuccessfully.
 Does anybody know if there is a chance to upgrade via apt-get the software on this machine without having to update the version of Ubuntu?

 Note: After making the changes I did everything right... "apt-get update "....

Best regards

---

### Post by sanderd17 on 2011-05-31
8.10, 9.40 and 9.10 have all reached end of life. That means that their repositories don't exist anymore. 

See this list to know what release or supported for what period: [http://en.wikipedia.org/wiki/List_of_Ubuntu_releases](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases)

---

### Post by snowpine on 2011-05-31
I *strongly* recommend upgrading to a supported LTS release (such as 10.04) however if that is not an option for whatever reason, you can always find the latest Apache here: [http://www.apache.org/](http://www.apache.org/)

---

### Post by mat3us on 2011-05-31
Thanks for the replies.
 The server is in another city, and thus can not access it physically, only by ssh.
 I also tried "sudo do-release-upgrade" and the error is shown below:


user@machine:/var/www$ sudo do-release-upgrade 
Checking for a new ubuntu release
Failed Upgrade tool signature
Failed Upgrade tool
Done downloading            
extracting 'jaunty.tar.gz'
Failed to extract

 Since you can not only upgrade the packages via apt, the solution is to upgrade the operating system to a newer version.
 I need to update it in the safest way (without losing data or settings) remotely.
 Can anyone help?

 Best regards

---

### Post by snowpine on 2011-05-31
Upgrading End Of Life releases:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

