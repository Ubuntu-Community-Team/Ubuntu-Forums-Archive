---
title: "How to install Flatpak in Deepin 15.11?"
date: 2019-10-02
forum: Ubuntu/Debian BASED
---

### Post by javierdl on 2019-10-02
I just tried it but is not looking very promising:

First I ran this command line:
```
sudo apt-get install software-properties-common
```
Then I tried to add the Flatpak repo:
```

sudo add-apt-repository ppa:alexlarsson/flatpak
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 95, in <module>
    sp = SoftwareProperties(options=options)
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 109, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 599, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python3/dist-packages/aptsources/distro.py", line 93, in get_sources
    (self.id, self.codename))
aptsources.distro.NoDistroTemplateException: 
[COLOR=#FF0000]**Error: could not find a distribution template for Deepin/stable**[/COLOR]

```

That error seems to say that this is the end of the road. There no Flatpak available for Deepin, is that it?

Thanks
----------------------------------------------------
Update:
I just recalled that I already have Flatpak installed actually. Except it's an older version. Reason why I cannot install Shotcut from the Flatpak Hub (it tells me it has to be the latest version). 
I don't remember how I got Flatpak installed on the first place, unfortunately.
[SIZE=3]**I guess my question really is: How to update Flatpak in Deepin 15.11?**[/SIZE]

---

### Post by Xian on 2019-10-02
Open the Deepin.info file:

```
sudo nano /usr/share/python-apt/templates/Deepin.info
```

Check to see what the file has for "Suite".

If it says unstable change it to stable.

Save the file and try again.

---

### Post by javierdl on 2019-10-03
Thank you Xian.

I did as you suggested.

And then I continued:

```


sudo add-apt-repository ppa:alexlarsson/flatpak
  Linux application sandboxing and distribution framework
 More info: https://launchpad.net/~alexlarsson/+archive/ubuntu/flatpak
Press [ENTER] to continue or ctrl-c to cancel adding it


gpg: keybox '/tmp/tmprffmn8ya/pubring.gpg' created
gpg: failed to start the dirmngr '/usr/bin/dirmngr': No such file or directory
gpg: connecting dirmngr at '/tmp/tmprffmn8ya/S.dirmngr' failed: No such file or directory
gpg: keyserver receive failed: No dirmngr




```

---

### Post by Xian on 2019-10-03
You'll just need to install that program:

```
sudo apt-get install dirmngr --install-recommends
```

---

### Post by javierdl on 2019-10-03
After installing dirmngr I attempted to add the repository:

```

sudo add-apt-repository ppa:alexlarsson/flatpak
  Linux application sandboxing and distribution framework
 More info: https://launchpad.net/~alexlarsson/+archive/ubuntu/flatpak
Press [ENTER] to continue or ctrl-c to cancel adding it


gpg: keybox '/tmp/tmp9rqezz1c/pubring.gpg' created
gpg: /tmp/tmp9rqezz1c/trustdb.gpg: trustdb created
gpg: key C793BFA2FA577F07: public key "Launchpad PPA for Alexander Larsson" imported
gpg: Total number processed: 1
gpg:               imported: 1
gpg: [COLOR=#FF0000]**no valid OpenPGP data found.**[/COLOR]



```

Then I updated apt:

```

sudo apt update
Hit:1 http://packages.deepin.com/deepin lion InRelease
Ign:3 http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu eoan InRelease 
Ign:4 http://repo.vivaldi.com/stable/deb stable InRelease                
Get:5 http://repo.vivaldi.com/stable/deb stable Release [3,831 B]
Get:6 http://repo.vivaldi.com/stable/deb stable Release.gpg [833 B]
Err:7 http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu eoan Release
  404  Not Found
Get:8 http://repo.vivaldi.com/stable/deb stable/main amd64 Packages [1,412 B]
Get:9 http://repo.vivaldi.com/stable/deb stable/main i386 Packages [1,412 B]
Get:2 https://repositorio.deepines.com/pub/deepines stable InRelease [7,471 B]
Get:10 https://repositorio.deepines.com/pub/deepines stable/main amd64 Packages [103 kB]
Get:11 https://repositorio.deepines.com/pub/deepines stable/main i386 Packages [31.1 kB]
Reading package lists... Done                                                           
[COLOR=#FF0000]**E: The repository 'http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu eoan Release' does not have a Release file.**[/COLOR]
[COLOR=#FF0000]**N: Updating from such a repository can't be done securely, and is therefore disabled by default.**[/COLOR]
N: See apt-secure(8) manpage for repository creation and user configuration details.




```
Then I checked for its inclusion (just in case): 

```

apt-cache policy | grep http | awk '{print $2 $3}' | sort -u
http://packages.deepin.com/deepinlion/contrib
http://packages.deepin.com/deepinlion/main
http://packages.deepin.com/deepinlion/non-free
http://repositorio.deepines.com/pub/deepinesstable/main
http://repo.vivaldi.com/stable/debstable/main

```

What do you think?

---

### Post by Xian on 2019-10-03
You have this issue because the eoan directory does not exist in the PPA:

```
Err:7 http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu eoan Release
  404  Not Found
```

[http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu/dists/](http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu/dists/)

You could change the release to disco for example but eoan does't exist.

---

### Post by javierdl on 2019-10-04
Ok. So due to the fact that the eoan dir does not exist: Flatpak cannot be installed in Deepin 15.11?
Or there is something else that can be done?
But wait a sec... I already have it installed, I just need to update it. I can't recall how I got it installed though. Could it be that this eoan dir was not a requirement before and now it is?

I do appreciate very much your help Xian :)

This is my second week in Deepin 15.11, I'm starting to feel like going back to Mint.

JDL

---

### Post by Frogs Hair on 2019-10-04
Deepin has not been Ubuntu based for a long time and is now based on Debian stable and will by default include older packages. I don't see any version of Vivaldi on flathub at all . PPA's generally don't apply unreleased operating systems such as eoan. Isn't there a .deb package that will update with the system on the web site? I had used Opera on Deepin and it updated with the system.

[https://flathub.org/home](https://flathub.org/home)

---

