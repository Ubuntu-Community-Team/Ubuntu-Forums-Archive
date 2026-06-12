---
title: "HOWTO: Use URLs to open Ubuntu Software Center"
date: 2012-05-19
forum: Tutorials
---

### Post by Lisiano on 2012-05-19
[SIZE="3"]**Preface**[/SIZE]

Like a lot of helpers on the forum, I have to type out boxes like this

> [noparse]```
sudo apt-get update
sudo apt-get install gimp
```[/noparse]
```
sudo apt-get update
sudo apt-get install gimp
```

Not only must we teach them how to install software from the command line, we also need to explain how to open a terminal and sometimes explain how sudo works, not ideal. But there is a way to change it.

[SIZE="3"]**Introducing AptURL.**[/SIZE]

This package is automatically installed in _every_ Ubuntu version starting from 7.10, well to use it we need to only give the user an url, following our **Gimp** example, all we need to do is just type

> [noparse][Click here to install Gimp](apt://gimp)[/noparse]

[Click here to install Gimp](apt://gimp)

Quite simple. But what if we need to give them a ton of stuff to install? Say **Banshee** and _a ton_ of it's extensions. Again, simple

> [noparse][Click here to install Banshee and all of it's extensions](apt://banshee,banshee-extension-alarm,banshee-extension-albumartwriter,banshee-extension-ampache,banshee-extension-appindicator,banshee-extension-awn,banshee-extension-coverwallpaper,banshee-extension-duplicatesongdetector,banshee-extension-foldersync,banshee-extension-jamendo,banshee-extension-karaoke,banshee-extension-lastfmfingerprint,banshee-extension-lcd,banshee-extension-lirc,banshee-extension-liveradio,banshee-extension-lyrics,banshee-extension-magnatune,banshee-extension-mirage,banshee-extension-openvp,banshee-extension-radiostationfetcher,banshee-extension-randombylastfm,banshee-extensions-common,banshee-extension-soundmenu,banshee-extension-streamrecorder,banshee-extension-telepathy,banshee-extension-zeitgeistdataprovider)[/noparse]

[Click here to install Banshee and all of it's extensions](apt://banshee,banshee-extension-alarm,banshee-extension-albumartwriter,banshee-extension-ampache,banshee-extension-appindicator,banshee-extension-awn,banshee-extension-coverwallpaper,banshee-extension-duplicatesongdetector,banshee-extension-foldersync,banshee-extension-jamendo,banshee-extension-karaoke,banshee-extension-lastfmfingerprint,banshee-extension-lcd,banshee-extension-lirc,banshee-extension-liveradio,banshee-extension-lyrics,banshee-extension-magnatune,banshee-extension-mirage,banshee-extension-openvp,banshee-extension-radiostationfetcher,banshee-extension-randombylastfm,banshee-extensions-common,banshee-extension-soundmenu,banshee-extension-streamrecorder,banshee-extension-telepathy,banshee-extension-zeitgeistdataprovider)

Notice how that wall of text easily shrinks to just a _few words_.

[SIZE="3"]**Why bother?**[/SIZE]

Quite simple. New users are **afraid** of the terminal. Instructing them to do something they never did before might scare them and might even drive them away. Using **AptURL** we can provide users with simple **URLs** that they only need to click. Every user knows how to click links.

[SIZE="3"]**Random titbits.**[/SIZE]

[LIST]
[*]Same links can be used to uninstall stuff
[*]If you are lazy, you can skip on typing out the 2 slashes and decrease the size to just apt:gimp
[*]Remember, **AptURLs** are links and so they shouldn't be used when telling someone how to install stuff on **Ubuntu Server**
[*]If you are talking about a **non-Ubuntu** based **OS**, **AptURL** might not be installed and you should provide terminal instructions
[*]If you want to tell someone how to install something from a **PPA**, you should stick to **GUI** only or **CLI** only.
> To install a PPA - open the Software Sources menu by launching the Ubuntu Software Center and selecting Edit -> Software Sources. Choose the Other Software tab and click Add. Paste ppa:ubuntu-wine/ppa
Now just [noparse][press here to install Wine](ppa://wine1.5)[/noparse]
[*]If you want to make use of apt links easier, go to this launchpad bug (#[lpbug]1001791[/lpbug]) and press "Does this bug affect you?", no need to leave a comment on Launchpad. This will let us use [apt]Gimp[/apt][/LIST]

---

