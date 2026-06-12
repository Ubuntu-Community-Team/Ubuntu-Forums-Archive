---
title: "Path to PHP5 binary"
date: 2007-06-14
forum: Server Platforms
---

### Post by mevets on 2007-06-14
For a long I have wanted to setup ktorrent with the web interface. It needs to know the path to the php executable though. It can't auto find it cause its not in its normal path. I apt-get installed the thing so it should be in a logical location. I have tried using the whereis cmd to track down the binary but I still cannot find it. Also, when I try 'which php5' it returns nothing.

Does anyone know the path to the php5 binary?

---

### Post by dominator22 on 2007-06-14
Should be /usr/bin/php5

---

### Post by mevets on 2007-06-14
Not there.

I went into synaptic and found 'php5-cli'. I installed that and now I have a binary in /usr/bin called php5. Weird.  Theres also a symlink called 'php' (I think it is at least, never truly known what a symlink is, but when I click on the properties of 'php' it does say it is a link to an application). Anyway I now have a php5 binary in my /usr/bin. It also works perfectly with ktorrent's webinterface. It's jsut weird that I had to apt-get php5-cli.

---

