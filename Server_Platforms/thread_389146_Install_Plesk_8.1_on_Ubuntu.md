---
title: "Install Plesk 8.1 on Ubuntu?"
date: 2007-03-20
forum: Server Platforms
---

### Post by Don Carcharo on 2007-03-20
SWSoft indicates that they support Plesk 8.1 on Ubuntu and there's a variety of different installers out there however I can't seem to get it installed. Has anyone had any luck? My preference is something that works with apt as so I can manage the install via synaptic. With that in mind I've focused most of my effort on trying to get Plesk installed via .deb packages. The only deb packages I could locate were from:

[http://autoinstall.plesk.com/PSA_8.1.0/dist-deb-Ubuntu-6.06-i386/](http://autoinstall.plesk.com/PSA_8.1.0/dist-deb-Ubuntu-6.06-i386/)

Within this directory there's about 10-12 .deb files (ignoring lower versions of the same file). Through trial and error I've gotten seven of these packages to install however I've hit a dependancy roadblock and can't get any further. The psa-api won't install because it depends on psa-8.1.0 however the psa-8.1.0 won't install because it depends on the psa-api.

Now although I see the humor in this little game of dependancy musical chairs it's growing old quick. Any advice? The debs don't seem to work, the autoinstaller doesn't work and even a make-install didn't work. I'm on Ubuntu Edgy currently though I've also tried Dapper with no success. I've also searched the forums here but couldn't find much on Plesk at all.

---

