---
title: "Inkscape 0.45 for Edgy"
date: 2007-02-03
forum: Repositories &amp; Backports
---

### Post by gummibaerchen on 2007-02-03
Hi,

*NEW:*

Find Inkscape 0.45 here (final version):
[**Download the shiny new *Inkscape 0.45* here**]("http://t3-ie.info/inkscape_0.45-0~edgy_i386.deb")

[QUOTE=./configure]        Use Xft font database:    yes
        Use gnome-vfs:            yes
        Use openoffice files:     yes
        Use MMX optimizations:    yes
        Use relocation support:   no
        Internal Python:          skipped
        Internal Perl:            skipped
        Enable LittleCms:         yes
        Enable Inkboard:          no
        Enable SSL in Inkboard:   no
[/QUOTE]

Whiteboard is supposed to be very buggy, so I did compile Inkscape without whiteboard support.

*OLD:*
I just created a Debian package of **Inkscape 0.45-pre3 Beta**.

Don't be afraid by the "pre3 Beta".

inkscape.org says itself:
> Please try it out, and if there are no further problems we'll put out the final 0.45.0 release this weekend.

So probably this version is equal to the final 0.45.

If not, I will post a second package whenever Inkscape 0.45 is released.

:KS [**Get the Package here**]("http://t3-ie.info/inkscape_0.45-0~edgy_i386.deb")

Have Fun,
gummibaerchen

---

### Post by Rodneyck on 2007-02-04
Inkscape .45 stable was released, fyi.

---

### Post by gummibaerchen on 2007-02-04
> **Rodneyck said:**
> Inkscape .45 stable was released, fyi.

[inkscape.org]("http://inkscape.org") says nothing about that...

In fact it says:
[QUOTE=inkscape.org]Latest stable version: 0.44.1[/QUOTE]

---

### Post by kleeman on 2007-02-04
I compiled a high quality deb (i.e. with proper Debian infrastructure) of the final release for amd64 if anyone is interested. Looks sweet....

[http://www.yourfilelink.com/get.php?fid=278314](http://www.yourfilelink.com/get.php?fid=278314)

---

### Post by gummibaerchen on 2007-02-04
> **kleeman said:**
> I compiled a high quality deb (i.e. with proper Debian infrastructure) of the final release for amd64 if anyone is interested. Looks sweet....
WoW :KS sounds good, but also a little bit magic ;)


> **kleeman said:**
> [http://www.yourfilelink.com/get.php?fid=278314](http://www.yourfilelink.com/get.php?fid=278314)
That site sucks:
```
Ad Blocker Detected

We have detected what appears to be ad blocking software on your computer;
please disable it & try the link again if you wish to download the file.

Why are we doing this?

Recently more & more people have been making use of ad blocking software & in turn this is hurting the revenue we can make from the ads that help run this free service.

We are providing this service to everyone free of charge & if we were to continue running the site as it is now we would eventually go out of business; it costs a lot to run a file hosting service & without ad revenue the site will cease to exist.

We hope to introduce a new service soon where users who don't wish to see ads will be able to subscribe to a "Premium Downloader Account" which will allow you to download files without any ads whatsoever & also a bunch of other additional benifets for a low yearly fee.

In the mean time we ask that you please disable your ad blocker when visiting YourFileLink.com. 
```

---

### Post by kleeman on 2007-02-04
Yeah it does seem to have deteriorated lately. Here is an alternative:


[http://www.math.nyu.edu/faculty/kleeman/amd64/inkscape_0.45-1_amd64.deb](http://www.math.nyu.edu/faculty/kleeman/amd64/inkscape_0.45-1_amd64.deb)

I got the final source from the inkscape sourceforge site and then copied the Debianization from an earlier prerelease in Debian unstable. Compiled and runs without issue....

---

### Post by gummibaerchen on 2007-02-05
I just built and uploaded the Inkscape 0.45 stable.

See first post for the link.

---

### Post by Seven.issimo on 2007-02-06
Thanks a lot for deb :)

..but, to get it working, I've to install libgtkmm on my new (and so "very crean") ubuntu.
np, to do this, but i suppose it should go into package dependecies...

otherwise: ```
$ sudo apt-get install libgtkmm-2.4-1c2a
```

---

### Post by kleeman on 2007-02-06
> **Seven.issimo said:**
> Thanks a lot for deb :)

..but, to get it working, I've to install libgtkmm on my new (and so "very crean") ubuntu.
np, to do this, but i suppose it should go into package dependecies...

otherwise: ```
$ sudo apt-get install libgtkmm-2.4-1c2a
```
That is listed as a dependency in my amd64 deb........

---

### Post by gummibaerchen on 2007-02-06
> **Seven.issimo said:**
> Thanks a lot for deb :)

..but, to get it working, I've to install libgtkmm on my new (and so "very crean") ubuntu.
np, to do this, but i suppose it should go into package dependecies...

otherwise: ```
$ sudo apt-get install libgtkmm-2.4-1c2a
```

Ok, I will add it.

---

### Post by pato101 on 2007-02-07
> **kleeman said:**
> Yeah it does seem to have deteriorated lately. Here is an alternative:


[http://www.math.nyu.edu/faculty/kleeman/amd64/inkscape_0.45-1_amd64.deb](http://www.math.nyu.edu/faculty/kleeman/amd64/inkscape_0.45-1_amd64.deb)

I got the final source from the inkscape sourceforge site and then copied the Debianization from an earlier prerelease in Debian unstable. Compiled and runs without issue....

You are my hero!:) :) :) :):guitar: :guitar:

---

### Post by Alexander Grundner on 2007-02-18
Tip: To add Inkscape to your applications menu after installing the provided .deb type:

cd /usr/local/share/applications
sudo cp inkscape.desktop /usr/share/applications

---

### Post by ThomasU on 2007-02-20
Note that Inkscape 0.45 still has the "arrow head color bug", i.e. if you add a marker to a line or stroke, the marker is black despite the stroke having a different color. To draw an arrow is ridiculously difficult in Inkscape 0.45 (especially when compared to Xfig). Here's how to do it from beginning to end in 13 steps(!!!):
[LIST][*]Select the "Draw Bezier curves and straight lines" tool (shift-F6) [*]Line starting point: click mouse left[*]Line ending point: double-click mouse left[*]Open "Fill and Stroke" dialog (shift-ctrl-F)[*]Click "Stroke paint" tab[*]Select line color: adjust HSLA sliders or type-in RGBA value. You now have a colored line.[*]Click "Stroke style" tab[*]Line width: increase Width value[*]Line type: "Dashes" pull-down menu[*]Arrow style: "End Markers" and scroll down pull-down menu for quite a length till you find "Arrow2Mend". You now have a colored line with a black arrow head.[*]Back to Inkscape's tool selector in the side bar: select the arrow "Select and transform objects" (F1)[*]Click on the arrow you just drew[*]Go to the top bar's Effects menu and select: Modify Path --> Color Markers to Match Stroke
[/LIST]

Of course, you can still draw colored arrows in only 7 clicks and no pull-down menus in Xfig but the rendering is not as good as with Inkscape.

---

### Post by revertex on 2007-02-23
Are you against the oficial package?

Just get it from the inkscape site.

> Stable release 0.45 intended for production use is available:
Source Tarball &#8212; .gz See README to install, or CompilingInkscape for troubleshooting help.
Linux Autopackage &#8212; .package (See autopackage.org for directions).

Download any of the above (as well as .sig files and previous releases) at the Sourceforge Downloads page, or through your distro's update capabilities.get it here:

[http://sourceforge.net/project/showfiles.php?group_id=93438&package_id=99112&release_id=483704](http://sourceforge.net/project/showfiles.php?group_id=93438&package_id=99112&release_id=483704)

---

### Post by gummibaerchen on 2007-02-23
> **revertex said:**
> Are you against the oficial package?

Wasn't available that day.

Also I spoke to the folk in #inkscape while packaging.

---

### Post by kleeman on 2007-02-23
The newly appeared package on sourceforge is to be preferred in my opinion as it has versioning which will allow for smooth upgrade to fesity. BTW unofficial packagers like myself and  gummibaerchen  are trying to help people and don't appreciate snide remarks (if that is what they were).

---

### Post by revertex on 2007-02-23
> **kleeman said:**
> The newly appeared package on sourceforge is to be preferred in my opinion as it has versioning which will allow for smooth upgrade to fesity. BTW unofficial packagers like myself and  gummibaerchen  are trying to help people and don't appreciate snide remarks (if that is what they were).

Calm down people, no offences, i'm just asking.


First of all i didn't known your package is older than the inkscape one, and i'm curious if your package there is something better or different than the official one.

As example, inkscape from the ubuntu repos (0.44) don't install potrace, someone that don't known will blame inkscape for not trace bitmap at all untill install it.

Thank you, every contribution is EVEN aprecciated.

---

### Post by stalefries on 2007-03-02
Thank you so much, I've been using this package for several days at least, it's been working just fine.

---

### Post by NoWhereMan on 2007-03-09
thx for the package! ^^

---

### Post by sonmez on 2007-03-30
Hello,

Does anyone know how to use the whiteboard in Inkscape with a Gmail account?

Thanks.

---

### Post by airtonix on 2007-03-30
i looked and was interested.....looks like you use it like a jabber client

so if you can set it up like you do with gaim to connect with gmail then your set...

or you setup wildfire or ejabberd on your adsl connected machine.

also, isnt that blur funtion the absolute coolest?....excellent, on par with Xara. no only if we could bring in brushes, and kill Fireworks(4/mx).

---

### Post by sonmez on 2007-04-05
I tried it but didn't work. Did anyone get it to work.

Thanks

---

### Post by gummibaerchen on 2007-04-05
> **sonmez said:**
> I tried it but didn't work. Did anyone get it to work.

Thanks

The Whiteboard/Groupdraw-function is not yet very stable and not for everyday use afaik.

---

### Post by Alexander Grundner on 2007-04-05
> **sonmez said:**
> I tried it but didn't work. Did anyone get it to work.

Thanks
FYI, 0.45 has been added to the edgy-backports repository. I got my update about a month ago.

---

