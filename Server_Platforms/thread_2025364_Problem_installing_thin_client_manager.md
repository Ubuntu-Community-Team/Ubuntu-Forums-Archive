---
title: "Problem installing thin client manager"
date: 2012-07-14
forum: Server Platforms
---

### Post by jamigf on 2012-07-14
Hi,
I have install ltsp with success on ubuntu 12.04. All wark fine! :-)
But now I want manage thin client and I'm trying to install thin client manager.
When i try to install it i receive the error:

"Some packages could not be installed. This may mean
 that you have requested an impossible situation or if you are
 using the unstable distribution that some required packages
 have not yet been created or been moved out of Incoming.
 The following information may help to resolve the situation:

 The following packages have unmet dependencies:
  Thin-client-manager-backend: Depends: python-tcm but not going to be installed
                                Recommends: gksudo but it is not installable"

If i try to install python-tcm I have:

"Some packages could not be installed. This may mean
 that you have requested an impossible situation or if you are
 using the unstable distribution that some required packages
 have not yet been created or been moved out of Incoming.
 The following information may help to resolve the situation:

 The following packages have unmet dependencies:
  python-tcm: Depends: pessulus but it is not installable
               Recommends: gksudo but it is not installable"

Sorry for english but I use google translate.

Please help me!
Thank you

---

### Post by gmackerz on 2012-07-24
try Epoptes to replace Thin client manager

apt-get install epoptes

add your username to epoptes group

gpasswd -a username epoptes
(replace username with your username)

install epoptes in client-side

sudo chroot /opt/ltsp/i386
apt-get install epoptes-client
epoptes-client -c 
exit

update image
sudo ltsp-update-image --arch i386

and you are good to go

---

