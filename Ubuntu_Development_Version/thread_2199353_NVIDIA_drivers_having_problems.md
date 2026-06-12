---
title: "NVIDIA drivers having problems"
date: 2014-01-13
forum: Ubuntu Development Version
---

### Post by Ramesh_Jude_Fernando on 2014-01-13
I am running a Acer Aspire V3 771G with Intel i5 processor and NVIDIA Geoforce 710M and the Nvidia drivers crash on Trusty Tahr Ubuntu 14.04. It says must configure video yourself and goes into low graphics mode (text BASH shell). I did the sane thing and ran "sudo apt-get remove nvidia*.*" and the display works fine now with the Intel drivers instead of the Optimus!

---

### Post by jmmL on 2014-01-13
I've been having similar problems as well (also on an laptop with a discrete nVidia card + intel processor). I haven't been able to find any useful error messages yet, partly because I'm not sure where to look. Any help would be appreciated.

For the time being I've removed bumblebee, nvidia drivers and associated packages so that I least have a working desktop through the integrated graphics.

---

