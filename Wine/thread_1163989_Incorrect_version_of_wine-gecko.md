---
title: "Incorrect version of wine-gecko"
date: 2009-05-19
forum: Wine
---

### Post by risingsun on 2009-05-19
Hi,

A while back I was trying to get wine-gecko up and running. I've since managed to do that but originally I had tried using the file from [http://source.winehq.org/winegecko.php](http://source.winehq.org/winegecko.php) but I neglected to specify the version(just that direct url) resulting in retrieving a file wine_gecko.cab. 

However reflecting back I realise now that I'm not really sure what this file is or what version. It appears to have a different sha1sum to version 0.1.0, 0.9.0 and 0.9.1 and so I was just a little worried as to what the file did when I tried to use it to install gecko a while back (I think it came back complaining about the wrong version and possibly suggesting it was v 0.1.0 but I can't remember anymore.) If anyone could put my mind at ease by confirming what the file is I'd be grateful :) ( I unfortunatly get a little paranoid about these things.)

Edit: Nevermind, I checked it against v0.0.1 and the sha1sums match.

---

### Post by asdfoo on 2009-05-19
> **risingsun said:**
> Hi,

A while back I was trying to get wine-gecko up and running. I've since managed to do that but originally I had tried using the file from [http://source.winehq.org/winegecko.php](http://source.winehq.org/winegecko.php) but I neglected to specify the version(just that direct url) resulting in retrieving a file wine_gecko.cab. 

However reflecting back I realise now that I'm not really sure what this file is or what version. It appears to have a different sha1sum to version 0.1.0, 0.9.0 and 0.9.1 and so I was just a little worried as to what the file did when I tried to use it to install gecko a while back (I think it came back complaining about the wrong version and possibly suggesting it was v 0.1.0 but I can't remember anymore.) If anyone could put my mind at ease by confirming what the file is I'd be grateful :) ( I unfortunatly get a little paranoid about these things.)

Edit: Nevermind, I checked it against v0.0.1 and the sha1sums match.

You're not supposed to visit that url directly.

Wine fetches and installs the correct version automatically, otherwise use winetricks gecko to install it.

---

