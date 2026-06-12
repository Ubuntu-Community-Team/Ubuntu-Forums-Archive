---
title: "Updater stopped working on 2 of 5 Ubuntu studio boxes"
date: 2017-01-22
forum: Ubuntu Studio
---

### Post by rjhanson on 2017-01-22
Hello All,

I am not understanding why 2 of my 5 ubuntu studio 16.10 boxes after the last updates last week now has their software update function disabled.  The software updater and sudo apt-get update, and sudo aptitude update all fail to access the repositories.

I have search high and low on the forums all over the internet with no solution that will fix the problem.

Any ideas for me?

Thanks

Richard

---

### Post by wildmanne39 on 2017-01-22
Please run this command and post the output using code tags.
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by rjhanson on 2017-01-22
aaastreaming@aaastreaming:~$ sudo apt-get update
Err:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety InRelease
  Could not resolve 'archive.ubuntu.com'
Err:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-updates InRelease               
  Could not resolve 'archive.ubuntu.com'
Err:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-backports InRelease             
  Could not resolve 'archive.ubuntu.com'
Hit:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) yakkety-security InRelease             
Hit:5 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) yakkety InRelease                    
Reading package lists... Done                     
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/yakkety/InRelease](http://archive.ubuntu.com/ubuntu/dists/yakkety/InRelease)  Could not resolve 'archive.ubuntu.com'
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/yakkety-updates/InRelease](http://archive.ubuntu.com/ubuntu/dists/yakkety-updates/InRelease)  Could not resolve 'archive.ubuntu.com'
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/yakkety-backports/InRelease](http://archive.ubuntu.com/ubuntu/dists/yakkety-backports/InRelease)  Could not resolve 'archive.ubuntu.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.
aaastreaming@aaastreaming:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
aaastreaming@aaastreaming:~$ 


This last time it finally got 2 hits, but before all repositories were fails

---

### Post by wildmanne39 on 2017-01-22
I believe it is a dns server issue, please add the google nameservers 8.8.8.8 and 8.8.4.4) in "IPv4-settings" in the network-manager applet.

Right-click->Edit connections->choose your network name->Edit->IPv4-setings

Change to "Automatic (DHCP), addresses only" and add the nameservers like this 8.8.8.8,8.8.4.4 in the field "DNS-servers".

Then go into the IPV6 setting and set it to ignore.

Save settings then restart the network after that by doing:
```
sudo  systemctl restart NetworkManager.service[/CODE
Then run this command again:
[CODE]sudo apt-get update && sudo apt-get upgrade
```

---

