---
title: "Google Chrome build now uses GTK!"
date: 2009-05-10
forum: The Cafe
---

### Post by Sashin on 2009-05-10
The lines seem to be a small graphical glitch but other than that it does resemble my theme (which is a modified dust theme).

[http://i39.tinypic.com/28umrtc.jpg](http://i39.tinypic.com/28umrtc.jpg)

Looks like it may be complete by the first half of the year after all.

---

### Post by apoth on 2009-05-10
I've got the lines too, other than that it appears to be coming together very well, did keep me wondering for a while though as to if it was ever going to happen!

---

### Post by joey-elijah on 2009-05-10
Yes! I too noticed this and at first thought it was perhaps a dodgy daily build, but several of my blog readers confirmed they were having a more unified look, whereas i am getting the grey lines. (I too use Dust). 

[http://d0od.blogspot.com/2009/05/google-chromium-gtk-tab-bar-coming.html](http://d0od.blogspot.com/2009/05/google-chromium-gtk-tab-bar-coming.html)

---

### Post by joey-elijah on 2009-05-10
> **apoth said:**
> I've got the lines too, other than that it appears to be coming together very well, did keep me wondering for a while though as to if it was ever going to happen!

Really? The advancements/feature additions have been coming thick and fast for the last month! I fully expect Google goal of having a beta release of Chrome ready by June to be met!

---

### Post by Mr. Picklesworth on 2009-05-10
Well, it's been using GTK for quite a while. Just now it's using GTK colours ;)

The use of GTK colours is a bit ugly so far, I should add. I hope they get it to use the appropriate toolbar styling. (And start using some stock icons...)

---

### Post by Sashin on 2009-05-10
Hopefully they make it themeable. It'll be cool having a DustChrome theme in the same light as the DustFox theme.

---

### Post by zekopeko on 2009-05-10
it sucks that the tab aren't integrated with the window borders like in windows and mac builds. that would really rock.

---

### Post by bashveank on 2009-05-10
Where can I download it?

---

### Post by Sashin on 2009-05-10
It's the normal one from the PPA.

---

### Post by days_of_ruin on 2009-05-10
> **zekopeko said:**
> it sucks that the tab aren't integrated with the window borders like in windows and mac builds. that would really rock.

But then it wouldn't integrate with everything else.
Now that it is actually using the gtk colors I think if you used
a theme that integrates the menubar/toolbar with the window border it might
look good.

---

### Post by apoth on 2009-05-20
The lines are gone now.

Just need to be able to set my homepage, maybe get flash support and proxy support and I'd be happy to switch to it by default. It's brilliantly fast, like I remember firefox being originally, whether it was this quick or not!

---

### Post by kaivalagi on 2009-05-20
> **bashveank said:**
> Where can I download it?

The PPA for the chromium daily builds is here: [https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

To use it add the following to your /etc/apt/sources.list file (remember to be sudo to save the file):

```
#chrome
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
```

And save the following key to a temp text file and import it in synaptic by going here settings->repositories->authentication tab

```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESaSPtAEEAK1nJtoDZ0ewpOOf0ET6Vp28LqO9mB4ubWjzXyRSbiha5pCvnnSIU1K+7Gzb
t3r0iUV9eKLUmf8pqfF/9kwsoqFqFSCjp+XjUzXsEChcGBWvyfGdTX8ClFfwNxSVLvGSqmdX
gZhs0F8tQB0lPWHGy3VvEt7wG/VHqpcOYpdNYRqxABEBAAG0IExhdW5jaHBhZCBQUEEgZm9y
IGNocm9taXVtLWRhaWx5iEYEEBECAAYFAknOwV0ACgkQ9rPTxuzZSv0f2QCeLjemEkq5tYjI
xtFpw3F11szeakYAoKsBZcl3Az08cYEd9UNZjQE1j4YtiEYEEBECAAYFAknS5Z8ACgkQrZOR
ep7Yx+qZ8wCfZYBABDkYO0Ulrivpxn6hARmgLxEAn0SeWaGjVQ4UE3zpNESguf+t9K1xiLYE
EwECACAFAkmkj7QCGwMGCwkIBwMCBBUCCAMEFgIDAQIeAQIXgAAKCRBam/O7Tl4XtV/2BACs
/RTpEWB/NUlluJmp1e6iFoyyfbT+HOD3hg35aQMzbdcmijsAiY9MvIfZ0YKWyqNUdGpDj5n0
bUNO0IcvKBBkOn5o4CiBsMp4DJHdrgJU4S00nAJK00E8I/yAv+x4C9uOacW3yrzSHs7Hv/vG
6Z1Jh+1JrabK13hdhwOL8+aY6Q==
=9P6G
-----END PGP PUBLIC KEY BLOCK-----

```

After that "reload" your packages in synaptic and search for "chromium-browser" then install it....

Hope that helps

---

### Post by Tipped OuT on 2009-05-20
Should look something a little more like this, by the time it's done...hopefully:

[[IMG]http://img40.imageshack.us/img40/9146/28umrtcsmallw.png[/IMG]](http://img40.imageshack.us/my.php?image=28umrtcsmallw.png)

:D

---

### Post by kaivalagi on 2009-05-20
Working a treat for me until on try to go to options :)

---

### Post by binbash on 2009-05-20
This is not Google Chrome, it is Chromium

---

### Post by Sashin on 2009-05-20
It would be awesome if it looked like that.

---

### Post by bashveank on 2009-05-20
> **kaivalagi said:**
> The PPA for the chromium daily builds is here: [https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

Great, thanks!

---

### Post by albinootje on 2009-05-20
Looks pretty interesting, although it's a bit crashy :) 
Any idea when a stable version can be expected ?

---

### Post by hanzomon4 on 2009-05-20
> **binbash said:**
> This is not Google Chrome, it is Chromium

It's the same thing! 
....for the love of God

---

### Post by Giant Speck on 2009-05-20
> **hanzomon4 said:**
> It's the same thing! 
....for the love of God

No it's not.

Chromium is the open-source project from which Google Chrome is based.

---

### Post by geoken on 2009-05-20
> **binbash said:**
> This is not Google Chrome, it is Chromium

Why does the title bar say Google - Chrome?

---

### Post by binbash on 2009-05-20
about:linux-splash

"It's &#8216;Chromium&#8217;, not &#8216;Google Chrome&#8217;

Chromium is an open source browser project. Google Chrome is a browser from Google, based on the Chromium project. This is a build of Chromium. No versions of Google Chrome for Linux will exist until Google makes an official release."

---

### Post by Giant Speck on 2009-05-20
> **geoken said:**
> Why does the title bar say Google - Chrome?

Where do you see that?

---

### Post by ghindo on 2009-05-20
> **geoken said:**
> Why does the title bar say Google - Chrome?If you're referring to [this post]("http://ubuntuforums.org/showpost.php?p=7316039&postcount=13"), then it says "Chrome" because it's a mockup, not an actual screenshot.

---

### Post by Tipped OuT on 2009-05-20
> **ghindo said:**
> If you're referring to [this post]("http://ubuntuforums.org/showpost.php?p=7316039&postcount=13"), then it says "Chrome" because it's a mockup, not an actual screenshot.

Actually "Google - Chromium" is in the original screenshot from the OP. All I did was change "Chromium" to "Chrome" and made it look like the GTK  title bar extends into the client area, like Vista.

I believe Chrome is short for Chromium? Even if I'm wrong, Google's name is still in the title.

---

### Post by zekopeko on 2009-05-20
for some reason chromium isn't using GTK color scheme here. running build from 20.5

---

### Post by OutOfReach on 2009-05-20
Yeah looks like they reverted to the blue scheme

---

### Post by Sashin on 2009-06-06
THIS is what it should look like when finished

[http://i43.tinypic.com/5bz1c9.jpg](http://i43.tinypic.com/5bz1c9.jpg)

---

### Post by solitaire on 2009-06-06
Well why don't yous all just download Goggle Chrome and try it out?

[http://blog.chromium.org/2009/06/danger-mac-and-linux-builds-available.html](http://blog.chromium.org/2009/06/danger-mac-and-linux-builds-available.html)

---

### Post by swoll1980 on 2009-06-06
> **solitaire said:**
> Well why don't yous all just download Goggle Chrome and try it out?

[http://blog.chromium.org/2009/06/danger-mac-and-linux-builds-available.html](http://blog.chromium.org/2009/06/danger-mac-and-linux-builds-available.html)

That's not Google Chrome. That's Chromium.

---

### Post by solitaire on 2009-06-06
> **swoll1980 said:**
> That's not Google Chrome. That's Chromium.

RTFA!

it's google CHROME!!
Here;s the About page from my Linux install of it![IMG]http://i12.photobucket.com/albums/a233/s0litaire/GoogleChrome.png[/IMG]

---

### Post by DougieFresh4U on 2009-06-06
You can see it's 'Google Chrome' symbol in the upper left corner!!

---

### Post by swoll1980 on 2009-06-06
> **solitaire said:**
> RTFA!

it's google CHROME!!
Here;s the About page from my Linux install of it!

Oh... Excuse me it was a chromium blog. Why is the Google chrome download on there? I have the Google Chrome installed. Does it update on it's own? I had the chromium installed, and the repo enabled. Does google Chrome have a repo?

---

### Post by solitaire on 2009-06-06
> **swoll1980 said:**
> Oh... Excuse me it was a chromium blog. Why is the Google chrome download on there? I have the Google Chrome installed. Does it update on it's own? I had the chromium installed, and the repo enabled. Does google Chrome have a repo?

Yup 

[http://dev.chromium.org/getting-involved/dev-channel](http://dev.chromium.org/getting-involved/dev-channel)

[quote=Google Dev]
**For Linux**

 Requires Intel Pentium 4 / Athlon 64 or later CPU, and 32 or 64 bit Ubuntu 8.04 or later, or 32 bit Debian 5. Support for other Linux distributions is planned; unpacking the .deb files by hand may work. 
***Installing Google Chrome will add the Google repository*** so your system will automatically keep Chrome up to date. (If you don't want Google's repository, do "sudo touch /etc/defaults/google-chrome" before installing the package.) 
[/quote]

---

### Post by swoll1980 on 2009-06-06
> **solitaire said:**
> Yup 

[http://dev.chromium.org/getting-involved/dev-channel](http://dev.chromium.org/getting-involved/dev-channel)

Thank you. I read that yesterday, completeley forgot about it.

---

### Post by solitaire on 2009-06-06
^_^ No worries! ^_^

---

