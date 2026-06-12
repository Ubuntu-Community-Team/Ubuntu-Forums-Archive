---
title: "new /etc/apt/sources.list format can cause properties.gtk errors"
date: 2015-10-23
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-10-23
All the way back from the last Trusty point release the /sources.list/ and the /sources.list.save/ have been truncated! to only one version. So if you have used standard method to update soures.list you will only see repos for that current distro and not the history of distros that we are used to. Also  gtk-properties flag is up as usual.

 I was able to bypass all of this on one system through a mistake ( I am not saying there are not other methods- I am just posting what I did).

 I had one /vivid/ install of ubuntu-desktop on one machine and so , just for the sake of having fun, I entered:

```

sudo sed -i 's/vivid/xenial/'g /etc/apt/sources.list

sudo apt-get update
sudo apt-get dist-upgrade

```

 all went well ...  lsb_release -a reported that I was updated to 15.10 but there were no /wily/ repos. Only xenial and vivid. I then went to software&updates and enabled /vivid proposed. That blew out (unity) ubuntu desktop. I was then able to go to terminal and install xubuntu desktop.

```

sudo apt-get install xubuntu-desktop

```

Worked like a charm. I was able to log on to GUI and then go to terminal and reset xenial back to vivid.

```

sudo sed -i 's/xenial/vivid/'g /etc/apt/sources.list
sudo apt-get update
sudo apt-get dist-upgrade

```

It seemed to somehow reset itself with no errors - then:

```

sudo sed -i 's/vivid/wily/'g /etc/apt/sources.list
sudo apt-get update
sudo apt-get dist-upgrade

```

and it all updated without glitch. Software&updates was now all set right (proposed on) and then:

```

sudo sed -i 's/wily/xenial/'g /etc/apt/sources.list
sudo apt-get update
sudo apt-get dist-upgrade

```

and voila'  /xenial/ base.files loaded 16.10 development descriptors. and no gtk errors.  

regards..

---

### Post by grahammechanical on 2015-10-23
I don't really follow what you are doing. But, when I used the sed command yesterday to set the sources.list from wily to xenial the URLs went into the Other Software tab and none of the boxes were ticked in the software tab. I put this down to the repos not being open.

Today, I switched sources.list back to wily and the usual boxes were ticked in the Software tab and the Xenial URLs were gone from the Other Software tab. Again I went from wily to xenial and the same situation of no boxes ticked in Software tab and all URLs in Other Software tab occurred. I got the little update that others are getting. But now the Software & Updates utility crashed and will not load.

There's something strange in the neighborhood. Who're gonna call?

Some other stuff has just come through

> The following packages will be upgraded:
  gnome-calculator indicator-datetime indicator-sound libcolumbus1-common
  libcolumbus1v5 zenity zenity-common


---

### Post by ventrical on 2015-10-23
I also have same as you on other installs.

It is:

```

software-properties-gtk

```

as usual....

 I tired to edit sources.list but it is not like the old format. There are two files now. sources.list and sources.list.save.

  I know how to fix this .. it is just that I fergit at the moment.. so I'll have to look some stuff up.

[QUOTE]
There's something strange in the neighborhood. Who're gonna call?
[/CODE]

Ubuntubusters of course. :)  I can see how all this early adopter schtick can make our systems ... er umm .. well .. a little bit squirrely if you know what I mean .. no pun intended .. bwwahahaha :)

Regards..

---

### Post by ventrical on 2015-10-23
Yeah ... don't forget to edit the ubuntu.info file :)

[https://wiki.ubuntu.com/U%2B1/common-problems#Software-Properties-Gtk_doesn.27t_work](https://wiki.ubuntu.com/U%2B1/common-problems#Software-Properties-Gtk_doesn.27t_work)

Just switch wily instances to xenial.

---

### Post by grahammechanical on 2015-10-23
Thank you, UbuntuBuster, that fixed it.

---

### Post by QDR06VV9 on 2015-10-23
> **ventrical said:**
> Yeah ... don't forget to edit the ubuntu.info file :)

[https://wiki.ubuntu.com/U%2B1/common-problems#Software-Properties-Gtk_doesn.27t_work](https://wiki.ubuntu.com/U%2B1/common-problems#Software-Properties-Gtk_doesn.27t_work)

Just switch wily instances to xenial.
I was waiting for someone to make mention of this, Usually it is zika.
But it was the one and only (Drumroll) [COLOR=#000000]Ubuntubuster...[/COLOR]:popcorn: 
I thank you for the reminder ventrical.
Regards

---

### Post by ventrical on 2015-10-23
> **runrickus said:**
> I was waiting for someone to make mention of this, Usually it is zika.
But it was the one and only (Drumroll) [COLOR=#000000]Ubuntubuster...[/COLOR]:popcorn: 
I thank you for the reminder ventrical.
Regards

And I even put up a share for copy 'n paste  [http://ubuntuforums.org/showthread.php?t=2300113](http://ubuntuforums.org/showthread.php?t=2300113)  so I might treat myself to some chocolate cookies tonight :)

You guys are a riot :)

regards..

---

### Post by QDR06VV9 on 2015-10-23
> **ventrical said:**
> And I even put up a share for copy 'n paste  [http://ubuntuforums.org/showthread.php?t=2300113](http://ubuntuforums.org/showthread.php?t=2300113)  so I might treat myself to some chocolate cookies tonight :)

> You guys are a riot :)

regards..
Yuumm maybe a fudge brownie with ice cream.
> You guys are a riot :)
You taught me everything I know..:D
[COLOR=#000000]even grahammechanical is starting to show a side I seldom see.
Maybe it will be infectious. [/COLOR]

---

### Post by ventrical on 2015-10-23
> **runrickus said:**
> Yuumm maybe a fudge brownie with ice cream.

You taught me everything I know..:D
[COLOR=#000000]even grahammechanical is starting to show a side I seldom see.
Maybe it will be infectious. [/COLOR]

Thank you for your kind and generous words...

...quoting Mark Shuttleworth...

> 

..on LXD containers..

"For me, personally, it has become a fun way to clean up my build  processes, spinning up a container on demand to make sure I always build  in a fresh filesystem."



.. so the keyword is *fun*   and you guys *are* fun (specially runrickus) :) and graham too but we need graham  to be stoic and stalwart because it helps us keep on track! So thanks for making  me feel like a rockstar for a day .. and I am throwing it right back at yas! :) and zika ... last cycle I was first to get the wily descriptor. This cycle , zika was the first one in.. so maybe he just left a few cookies in the jar for the rest of us :)

Regards..

---

### Post by flocculant on 2015-10-23
> **ventrical said:**
> ...

 I tired to edit sources.list but it is not like the old format. There are two files now. sources.list and sources.list.save....

Has been like that for a while

```
wolf@wily:/media/wolf/old wily/etc/apt$ ls sources*
sources.list  sources.list.save

sources.list.d:
flacon-ubuntu-ppa-wily.list
flacon-ubuntu-ppa-wily.list.save
me-davidsansome-ubuntu-clementine-dev-wily.list
me-davidsansome-ubuntu-clementine-dev-wily.list.save
shimmerproject-ubuntu-daily-wily.list
shimmerproject-ubuntu-daily-wily.list.save
ubuntu-sdk-team-ubuntu-ppa-wily.list
ubuntu-sdk-team-ubuntu-ppa-wily.list.save
ubuntu-testcase-ubuntu-community-testing-wily.list
ubuntu-testcase-ubuntu-community-testing-wily.list.save
xubuntu-dev-ubuntu-ppa-wily.list
xubuntu-dev-ubuntu-ppa-wily.list.save
xubuntu-dev-ubuntu-xubuntu-staging-wily.list
xubuntu-dev-ubuntu-xubuntu-staging-wily.list.save
```

Edit a source.list - get a source.list.save

---

### Post by VinDSL on 2015-10-23
> **ventrical said:**
> ```

sudo sed -i 's/vivid/xenial/'g /etc/apt/sources list

sudo apt-get update
sudo apt-get dist-upgrade

```

Missing a [dot] there, aren't we?!?!?  :D

---

### Post by VinDSL on 2015-10-23
> **ventrical said:**
> ```
sudo sed -i 's/xenial/vivid/'g /etc/apt/sources.list
sudo apt-get update
sudo apt-get dist-**[color="#ff0000"]update[/color]**

```

Heh!

---

### Post by ventrical on 2015-10-24
> **VinDSL said:**
> Heh!

Thanks for pointing those out :)  hehehe .. I get a little hyper during the beginning of a new cycle :) lol

regards..

---

### Post by ventrical on 2015-10-24
@VinDSL

Thanks again Hawkeye :) lol   I must of been half alseep... or all the way asleep :) lol

Regards..

---

### Post by VinDSL on 2015-10-24
No prob.  Just shows you're human.

I'm as guilty of typos as anyone...  ;)

---

### Post by mc4man on 2015-10-24
Out of curiosity, -  after altering sources.list to xdenial & updating does software-properties-gtk work?

---

### Post by grahammechanical on 2015-10-24
Yes, it does. It also removes the URLs out of Other Software tab and instead ticks the boxes in Ubuntu Software tab & Updates tab with the exception of Proposed.

---

### Post by zika on 2015-10-25
> **mc4man said:**
> Out of curiosity, -  after altering sources.list to [SIZE=4]**xdenial**[/SIZE] & updating does software-properties-gtk work?;)

---

### Post by VinDSL on 2015-10-25
lel :)

---

### Post by ventrical on 2015-10-25
> **mc4man said:**
> Out of curiosity, -  after altering sources.list to xdenial & updating does software-properties-gtk work?

Apport calls it to report a problem so the ubuntu.info file has to be configurated if you want properties-gtk error to go away after boot up. Some use /devel/ and get away with it. I think the proper file will come up on Oct. 29th with toolchain or somewhere along the line. Not a problem .. just a gui inconvenience to some ..

---

### Post by zika on 2015-10-25
> **VinDSL said:**
> lel :)Wait a minute: since I'm using Wayland “without“ X, am I (also) in xdenial... ;) ?

---

### Post by jerrylamos on 2015-10-25
I'm not as comfortable with command line as some of you are.

I do a sudo gedit /etc/apt/sources.list and do a replace all wily with xenial

sudo apt-get update 
sudo apt-get dist-upgrade

Looks to me like it worked.
DISTRIB_DESCRIPTION="Ubuntu Xenial Xerus (development branch)"

One "g" command line that is altogether broken for me is:

gsettings set org.gnome.desktop.background picture-uri 'file:////home/jerry/Pictures/Shark_Island'

Works on trusty et. al, on wily much flashing then default wallpaper.  No replies from ubuntu-bug.

I don't know if "gsettings" is still supported.

---

