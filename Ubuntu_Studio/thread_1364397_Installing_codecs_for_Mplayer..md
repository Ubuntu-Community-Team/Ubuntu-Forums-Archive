---
title: "Installing codecs for Mplayer."
date: 2009-12-25
forum: Ubuntu Studio
---

### Post by madmax.santana on 2009-12-25
Every time I play a new extension in Mplayer, .avi .mp3 .mpg .amr etc etc, it starts searching for a plugin. Is there a codec pack or a plugin pack which installs all the codecs and plugins for Mplayer at once??? Please guide here

---

### Post by trulan on 2009-12-25
Install the ubuntu-restricted-extras metapackage.  Either through synaptic package manager or by running sudo apt-get ubuntu-restricted-extras.

---

### Post by madmax.santana on 2009-12-26
Yeah man, thanks... It helped. I am currently installing it and it would take about 30 minutes before it's completely set up!
Anyway, I can see the gstreamer plugins in the package-download list... So I guess what you told me was the thing I was looking for. Probably it would install all plugins. Thanks a lot...

Shall be really glad if anyone could give me the details with the ubuntu-restricted-extras package. Just interested to know... Is it an optional megapack of all the secondary applications and plugins for Ubuntu which is not meant for primary install but can be installed later to expand the packages installed in primary run??? Am I thinking right?

---

### Post by trulan on 2009-12-26
Pretty much.  Restricted extras contains software that can't be included in default Ubuntu due to legal reasons, or copyright laws, or something like that.  But it's stuff that a lot of people are going to need, so they put it in a package that can be easily installed.

---

### Post by madmax.santana on 2009-12-26
Yeah trulan, thanks a lot for information. It's help a lot when I am inspiring others to Linux!!!

---

