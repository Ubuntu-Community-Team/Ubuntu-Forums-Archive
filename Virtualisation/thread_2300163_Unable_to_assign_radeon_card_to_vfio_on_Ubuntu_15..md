---
title: "Unable to assign radeon card to vfio on Ubuntu 15.10"
date: 2015-10-24
forum: Virtualisation
---

### Post by manvir2 on 2015-10-24
Im trying to assign one of my two R9 280's to vfio so I can use it for vga passthrough the only problem I'm having is I cant assign the card to vfio because the radeon driver loads before vfio gets a chance to load and assign the card to vfio. In Ubuntu 15.04 I never had this problem its only in 15.10. What could I do is there some way of telling ubuntu to load vfio first? I believe that the radeon driver loading before the vfio driver is the problem but I could be wrong. (The hdmi audio on the card gets assigned to vfio-pci but not the vga part)

dmesg: [http://pastebin.com/WX8HGyK0](http://pastebin.com/WX8HGyK0)

---

