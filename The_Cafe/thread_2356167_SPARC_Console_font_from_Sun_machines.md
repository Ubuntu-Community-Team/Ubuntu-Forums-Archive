---
title: "SPARC Console font from Sun machines"
date: 2017-03-20
forum: The Cafe
---

### Post by Hobart on 2017-03-20
(Since Google takes people here for "sparc console font" searches and the last question from 2006 went unanswered, am posting this here for general interest)

For those Ubuntu users nostalgic for old Sun hardware, the font they want is called "Sun 12x22".

The font is in the Linux kernel tree as a ".c" file, so can be compiled into a custom kernel image, but a ".psf" or ".psfu" version is not currently (Yakkety/16.10) in any Ubuntu binary packages.

There are usable fonts in the "kbd" source package, to get them, make an empty directory and run ```
apt-get source kbd
``` In the resulting folders you'll find the .../data/consolefonts/ folder with several 12x22 .psfu descended from the SPARC console font.

To use, copy to your /usr/share/consolefonts/ folder, then ```
setfont LatGrkCyr-12x22
```

Another font descended from this is on GitHub here - (screenshot at end of post)

[https://github.com/talamus/solarize-12x29-psf](https://github.com/talamus/solarize-12x29-psf)

If you want this one, get the Solarize.12x29.psfu.gz file off of GitHub, copy it to your /usr/share/consolefonts/ and use 'setfont' as above.

An issue this does not address - manual adjustment of /etc/default/console-setup per the console-setup(5) manual pages to ensure proper encoding is handled (as "dpkg-reconfigure console-setup" doesn't work with manually added fonts)

I'm guessing that Solarize font or kbd's LatGrkCyr might map similarly to one of the existing ones, but I haven't tried it.  I'd recommend using "w3m -dump" with foreign-language websites to test.

Cheers.
-jon

Screenshot of the Solarize font: 
[IMG]http://i.imgur.com/KBoRRrH.png[/IMG]

---

