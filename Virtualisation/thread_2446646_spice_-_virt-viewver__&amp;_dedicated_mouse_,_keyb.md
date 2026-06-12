---
title: "spice - virt-viewver  &amp; dedicated mouse , keyboard"
date: 2020-07-04
forum: Virtualisation
---

### Post by maziar123 on 2020-07-04
Hi


I have problem with virt-viewer & dedicated mouse keyboard
I use spice with VirGL in Ubuntu 20.04 server with also Ubuntu guest 20.04


We Have TWO monitor & also TWO mouse & keyboard


then i pass 2nd mouse & keyboard to guest , and also use  virt-viewer


for use of two different user i move virt-viewer to 2nd monitor but seems when host mouse out of  virt-viewer screen , guest mouse work BUT cursor hide :-(


how  always show cursor in this mode ?




thx

---

### Post by TheFu on 2020-07-05
May not work for your setup, but are you tied to spice?  I know that multiple client machines can connect to multiple x2go sessions. As long as the GPU isn't in heavy use, this works well and works great over the internet.

In general, I don't sit at the computer with my desktop. That desktop is almost always accessed over a network connection.

---

### Post by maziar123 on 2020-07-07
Hi 

i currently use Nomachine for it X2go not stable for some environment such as cinnamon :(

for some reason ...  search solution for spice .... ;)

---

