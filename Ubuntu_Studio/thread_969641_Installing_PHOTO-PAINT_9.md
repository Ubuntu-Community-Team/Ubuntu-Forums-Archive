---
title: "Installing PHOTO-PAINT 9"
date: 2008-11-03
forum: Ubuntu Studio
---

### Post by claus on 2008-11-03
Hi all,

I would like to install PHOTO-PAINT 9 for Linux, which I found on a Czech server as a .gz archive. I found a brief howto on the Internet and tried to follow the steps described there. I put the command lines into a shell script, but got  some error messages 'Permission denied' (although I added 'sudo' to each line).

The script:

```
#!/bin/sh

sudo mkdir /usr/local/debian
sudo mv /home/claus/Downloads/dists/slink/main/binary-i386/*.* /usr/local/debian
sudo dpkg-scanpackages /usr/local/debian /dev/null | gzip - > /usr/local/debian/Packages.gz
sudo echo "deb file:/usr/local/debian ./" > /etc/apt/sources.list
```

Since the script didn't work properly, I moved the respective directories containing the .deb packages as well as 'Packages' and 'Packages.gz' manually to /usr/local/debian. 'Synaptic' accepts the new sources, but notifies me that '/usr/local/debian/Packages.gz' is missing. Executing

```
'sudo dpkg-scanpackages /usr/local/debian /dev/null | gzip - > /usr/local/debian/Packages.gz'
```

results in 'Permission denied'. What can I do to generate this 'Packages.gz' file?

The directory structure of the PHOTO-PAINT files is as follows:

```

/usr/local/debian/--|--main/binary-i386/<deb files>, <Packages>, <Packages.gz>
                    |
                    |--nonfree/binary-i386/<deb files>, <Packages>, <Packages.gz>

```

I'm doing all of this because I worked with PHOTO-PAINT under Windows for some time and am looking for an alternative to the Gimp, whose output is not always that good (bad anti-aliasing, 'stripes' after performing 'Lighting Effects', etc.).

TIA,

Claus

---

