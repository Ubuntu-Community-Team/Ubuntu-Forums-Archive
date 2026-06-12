---
title: "Compiz Switcher Bug (newb warning)"
date: 2012-03-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by DrSkylaser on 2012-03-23
So I'm having [this problem]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/945816") (the alt-tab task switcher went away--it's amazing how disruptive to actual work that is!). I'm a rank newb, though, and can't figure out what version of compiz I have (the bug listing says fix released, so I probably need to update?) or how to fix it.  Instructions, or pointers to instructions?  Sad to say my google fu has failed me. . .

---

### Post by mc4man on 2012-03-23
The fix(s) will be in next compiz* upgrades, currently not available

If you were fooling around in the unity plugin settings then open compizconfig-settings-manager (ccsm) & set the "Key to show Hud" back to the default of <Alt> (in screen, click on little X icon where cursor is

Edit
can also be re-set with this command
```
gconftool-2 --set --type string  /apps/compiz-1/plugins/unityshell/screen0/options/show_hud "<Alt>"
```

---

### Post by dino99 on 2012-03-23
> **DrSkylaser said:**
> So I'm having [this problem]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/945816") (the alt-tab task switcher went away--it's amazing how disruptive to actual work that is!). I'm a rank newb, though, and can't figure out what version of compiz I have (the bug listing says fix released, so I probably need to update?) or how to fix it.  Instructions, or pointers to instructions?  Sad to say my google fu has failed me. . .

To get deatails and package changelog, your best friend is synaptic.

sudo apt-get install synaptic
sudo synaptic

then set the preferences to get the package detail

---

### Post by DrSkylaser on 2012-03-26
When try to update via Synaptic or command line, I get an error message "Could not download all repository indexes" with the further details "Failed to fetch [http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead."

The Compiz websites/wiki I can find are woefully out of date, so not particularly helpful.  Most of the documentation I can find on Compiz is pretty old--so I am puzzled about the very current bug report on Launchpad.  What no doubt very obvious thing am I missing?

---

### Post by dino99 on 2012-03-26
> **DrSkylaser said:**
> When try to update via Synaptic or command line, I get an error message "Could not download all repository indexes" with the further details "Failed to fetch [http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead."

The Compiz websites/wiki I can find are woefully out of date, so not particularly helpful.  Most of the documentation I can find on Compiz is pretty old--so I am puzzled about the very current bug report on Launchpad.  What no doubt very obvious thing am I missing?

as you says "its pretty old", if you know how to use a browser then check that url :)
i can confirm its very old :) but why are you using a ppa with Precise , where the latest packages are used ?

---

### Post by DrSkylaser on 2012-03-26
> **dino99 said:**
> as you says "its pretty old", if you know how to use a browser then check that url :)
i can confirm its very old :) but why are you using a ppa with Precise , where the latest packages are used ?

Beats me!  I didn't put anything in to Synaptic, that's just what it scanned & came up with.  Parts of my system are legacy from a previous user, so I'm always discovering old weird corners I don't understand despite updating to Precise.  I can't find any updated sources for Compiz though, which is my question now I suppose: this link is obviously no longer good, but what should I be using instead?

---

### Post by dino99 on 2012-03-26
so open a terminal and run :  

sudo gedit /etc/apt/sources.list

remove everything there (wipe all)  and add these lines: (copy/paste them)

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-proposed main universe restricted multiverse


deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) precise main #wine

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) oneiric contrib

then save and close that file. When its done, open synaptic and click on the update icon, you'll get the latest packages for upgrading.

---

### Post by DrSkylaser on 2012-03-26
Did that, hit reload in synaptic, and got the same "Could not download all repository indexes" with the details "GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0Failed to fetch [http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead."

Which is confusing me because those two ppas that got a 404 aren't in the source list any more. . .

---

### Post by alphacrucis2 on 2012-03-26
> **DrSkylaser said:**
> Did that, hit reload in synaptic, and got the same "Could not download all repository indexes" with the details "GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0Failed to fetch [http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead."

Which is confusing me because those two ppas that got a 404 aren't in the source list any more. . .

If you added them using apt-add-repository, then ppa's have their own .list file under /etc/apt/sources.list.d

You should see files in sources.list.d folder called 'ppa name'.list

---

