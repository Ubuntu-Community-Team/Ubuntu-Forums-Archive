---
title: "apt-get issue"
date: 2010-07-07
forum: Server Platforms
---

### Post by ifny_keith on 2010-07-07
I have a fresh install of 10.04 and am having issues with apt-get. I have run: sudo apt-get update and receive this 
E: Some index files failed to download, they have been ignored, or old ones used instead.

along with a list of Failed to fetch ...

if i run this - sudo apt-get install apache2 this is the result:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package apache2

I can get on the web, no DNS issues, can do nslookups. I don't not have a proxy set up nor have i modified the sources.list file.

Read a bunch of posts and tried most everything that was suggested to no avail.

Thanks for any help!

---

### Post by stlsaint on 2010-07-07
1)Ensure your sources.list is complete and your servers arent commented out.
2) Check your internet connection speed.
3) The servers you are trying to pull from may be down at the momment!

---

### Post by ifny_keith on 2010-07-08
sources.list looks to be complete, nothing commented out

Plenty of bandwidth on a T-1

Do you think the servers would be down for several days? I would like to believe that is no the case. I can resolve and ping the servers as well as plug the URL's in my browser and navigate to the servers.

---

### Post by subba9000 on 2010-07-08
This is the update and upgrade
1) sudo apt-get update
2) sudo apt-get upgrade

For apache2
[https://help.ubuntu.com/8.04/serverguide/C/httpd.html](https://help.ubuntu.com/8.04/serverguide/C/httpd.html)

For DNS and proxy
[https://help.ubuntu.com/community/Servers#DNS](https://help.ubuntu.com/community/Servers#DNS)

---

### Post by ifny_keith on 2010-07-08
**sudo apt-get update results - **

Ign cdrom://Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release i386 (20100427)/ lucid/main Translation-en_US
Ign cdrom://Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release i386 (20100427)/ lucid/restricted Translation-en_US    
Err [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                                                                                                             
  Could not connect to archive.canonical.com:80 (91.189.88.33). - connect (110: Connection timed out)
Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US                                                                                       
  Unable to connect to archive.canonical.com:http:
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                                             
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                                                    
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                                                     
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                                                    
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                                                     
Err [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                                                    
  Unable to connect to archive.canonical.com:http:
Err [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                                                     
  Unable to connect to archive.canonical.com:http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                                                    
  Could not connect to security.ubuntu.com:80 (91.189.92.167). - connect (110: Connection timed out) [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US                                 
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US                           
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US                             
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US                           
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                                                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg      
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.45). - connect (110: Connection timed out) [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release.gpg
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages     
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.45). - connect (110: Connection timed out) [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/Release.gpg)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/main/i18n/Translation-en_US.bz2)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/restricted/i18n/Translation-en_US.bz2)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/universe/i18n/Translation-en_US.bz2)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)  Could not connect to archive.canonical.com:80 (91.189.88.33). - connect (110: Connection timed out)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_US.bz2)  Unable to connect to archive.canonical.com:http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (91.189.92.167). - connect (110: Connection timed out) [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz)  Unable to connect to archive.canonical.com:http:

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/lucid/partner/source/Sources.gz)  Unable to connect to archive.canonical.com:http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/main/binary-i386/Packages.gz)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/restricted/binary-i386/Packages.gz)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/universe/binary-i386/Packages.gz)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/multiverse/binary-i386/Packages.gz)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/main/source/Sources.gz)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/restricted/source/Sources.gz)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/universe/source/Sources.gz)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-backports/multiverse/source/Sources.gz)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.45 80]

**Sudo -apt-get upgrade results - **

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

**From what i can see I am unable to contact those servers for what ever reason.**

---

### Post by ifny_keith on 2010-07-08
OK - looks like I have a bad address on my network, changed the IP address of the server and now am able to sudo apt-get update /upgrade. apt-get apache2 working now.

Thanks!

---

### Post by anilga on 2010-12-18
Hi ifny_keith,

I have same issue.
Could you please let me know what exactly we need to do.

(where do we need to change the address and what should be the new address)

Thanks
Anil

---

### Post by sikander3786 on 2010-12-18
> **anilga said:**
> Hi ifny_keith,

I have same issue.
Could you please let me know what exactly we need to do.

(where do we need to change the address and what should be the new address)

Thanks
Anil
Welcome to the forums :-)

Even if sounding the same, you issue might not be the same as the OP's. Please post the _complete_ output of these commands from Applications > Accessories > Terminal.

```
sudo apt-get update
```

```
cat /etc/apt/sources.list
```

While posting, click the # icon in post menu and paste your text in between the generated code tags.

---

