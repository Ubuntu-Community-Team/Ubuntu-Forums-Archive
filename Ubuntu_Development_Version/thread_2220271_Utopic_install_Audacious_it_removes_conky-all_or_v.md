---
title: "Utopic install Audacious it removes conky-all or vice versa"
date: 2014-04-27
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2014-04-27
Conky-all was removed when I changed the sourses to Utopic. I went to install it and it wanted to remove Audacious. I had to let it remove Audacious because I need conky-all.
But, should it be doing this? Am I no longer allowed to have Audacious on my system?

```
cavsfan@cavsfan-MS-7529:~$ sudo apt-get install audacious
[sudo] password for cavsfan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 audacious : Depends: audacious-plugins (>= 3.5.2) but it is not going to be installed
             Depends: libaudcore2 (= 3.5.2) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

```
cavsfan@cavsfan-MS-7529:~$ sudo apt-get install libaudcore2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libimlib2 liblua5.1-0 libxmmsclient6
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libguess1 libmowgli-2-0
The following packages will be REMOVED:
  conky-all libaudclient2
The following NEW packages will be installed:
  libaudcore2 libguess1 libmowgli-2-0
0 upgraded, 3 newly installed, 2 to remove and 0 not upgraded.
Need to get 147 kB of archives.
After this operation, 757 kB disk space will be freed.
Do you want to continue? [Y/n] 
```

This can't be right or can it?

---

### Post by mc4man on 2014-04-27
Nothing to do with Utopic, quite likely my fault if you're using my ppa. I meant to change the break on libaudclient2 a couple of weeks ago but then totally borked my ssd drive I use for Ubuntu & forgot.
(- I think I finally fixed the ssd yesterday so finally have Ubuntu back, am just about finished testing & looks ok..

Anyway libaudclient2 is no longer part of audacious 3.5   but the older version of libaudclient2 *should* remain usable. So if using the ppa check in about 15 min. or so for an update that will allow you to install libaudclient2/conky-all & keep aud 3.5

( - from release notes - 
> libaudclient is no longer included with Audacious because it is tied to the older dbus-glib library. However, existing copies of libaudclient will still work with Audacious 3.5

---

### Post by Cavsfan on 2014-04-27
> **mc4man said:**
> Nothing to do with Utopic, quite likely my fault if you're using my ppa. I meant to change the break on libaudclient2 a couple of weeks ago but then totally borked my ssd drive I use for Ubuntu & forgot.
(- I think I finally fixed the ssd yesterday so finally have Ubuntu back, am just about finished testing & looks ok..

Anyway libaudclient2 is no longer part of audacious 3.5   but the older version of libaudclient2 *should* remain usable. So if using the ppa check in about 15 min. or so for an update that will allow you to install libaudclient2/conky-all & keep aud 3.5

( - from release notes -

Yes, I was using your ppa. :) I got rid of all the trusty ppas I had added. I just added your ppa back.

```
sudo add-apt-repository ppa:mc3man/audtests
```

```
Fetched 22.7 MB in 33s (680 kB/s)
W: Failed to fetch http://ppa.launchpad.net/mc3man/audtests/ubuntu/dists/utopic/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/mc3man/audtests/ubuntu/dists/utopic/main/binary-i386/Packages  404  Not Found

```

But, when doing sudo apt-get update I get not found on your ppa:

[http://ppa.launchpad.net/mc3man/audtests/ubuntu/dists/utopic/main/binary-amd64/Packages](http://ppa.launchpad.net/mc3man/audtests/ubuntu/dists/utopic/main/binary-amd64/Packages) gets a 404 not found error.

Thanks I'm sure it's something simple. Sorry to hear about your SSD glad you were able to recover it.

---

### Post by mc4man on 2014-04-27
"Something simple", that it is. - the ppa is only for trusty
So you'd need to edit your sources & change utopic to trusty
(Note that that is a testing ppa, at some point will move aud 3.6-alpha which may not suit you. While there is more avail. packages here it will stay on 3.5.2 for foreseeable future, at least till 3.6 releases
[https://launchpad.net/~mc3man/+archive/trusty-media](https://launchpad.net/~mc3man/+archive/trusty-media)

---

### Post by Cavsfan on 2014-04-27
> **mc4man said:**
> "Something simple", that it is. - the ppa is only for trusty
So you'd need to edit your sources & change utopic to trusty
(Note that that is a testing ppa, at some point will move aud 3.6-alpha which may not suit you. While there is more avail. packages here it will stay on 3.5.2 for foreseeable future, at least till 3.6 releases
[https://launchpad.net/~mc3man/+archive/trusty-media](https://launchpad.net/~mc3man/+archive/trusty-media)

Ok, thanks! :) I was able to install 3.4.3-1 from Utopic repositories. I'll fix it though.

---

