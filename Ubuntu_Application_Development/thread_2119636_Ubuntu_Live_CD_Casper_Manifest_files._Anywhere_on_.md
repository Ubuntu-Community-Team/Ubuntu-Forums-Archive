---
title: "Ubuntu Live CD Casper Manifest files. Anywhere on the net?"
date: 2013-02-24
forum: Ubuntu Application Development
---

### Post by tartalo on 2013-02-24
I'm writing a bash script that needs a list of all the packages installed by default by an Ubuntu CD.

I'm using now the manifest files found in every Ubuntu CD inside the casper folder, but because of forward compatibility I would like to avoid that and let the script itself download them from somewhere.

One of these files can be found, for example here's a Lubuntu manifest:
[http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-i386.manifest](http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-i386.manifest)

However, in recent releases there is another manifest file inside the ISO called filesystem.manifest-remove and I couldn't find it. In older versions there was only one manifest outside and one inside, but they are different and the one I need is the one inside the ISO.

So,

Does anyone know if I can download these manifest files without downloading the ISO?
OR
Any other method to get a full list of the packages installed by different Ubuntu version and flavors?

Thanks in advance

---

