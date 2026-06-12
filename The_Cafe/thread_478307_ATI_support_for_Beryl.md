---
title: "ATI support for Beryl"
date: 2007-06-19
forum: The Cafe
---

### Post by Bengaul on 2007-06-19
Does any one know what the time-scale is for Beryl support on ATI cards? Or if there is any? I would love to give it a go...

---

### Post by forrestcupp on 2007-06-19
I wouldn't get in any hurry, unless you want to use xgl.  If you use xgl,  you can do it right now.  You just pretty much have to get out of xgl any time you want to run an opengl app.

Or you can use the open source ati drivers and experience the benefits of Beryl with aiglx right now, too.  But those drivers don't support all of the opengl extensions yet, so 3d gaming is out of the question.  If you're not a gamer, this is the way to go.

I ended up getting so frustrated about it that I sold my ATI on ebay and bought an nvidia card.

---

### Post by Bengaul on 2007-06-19
Yes bit of a bummer. Do they have any sort of road map?

---

### Post by igknighted on 2007-06-19
> **Bengaul said:**
> Yes bit of a bummer. Do they have any sort of road map?

Not officially, unless it is already in a development build.  Each new driver (they release every month) takes between 2 and three months to build.  Until a feature is stable enough, it stays in general development.  Then they add it to the next release, and 2 months later it shows up.  It is now the same process as their windows drivers.  So to answer your question, no, there is not any official road map.  However, it could be any time from next month to next year.

On a side note, what ATI card do you have?  If it is older than the x800 then you should have full composite/3d functionality with the OSS radeon driver.  I used that for a long time and it worked wonderfully, and was completely open source.

---

### Post by forrestcupp on 2007-06-19
> **igknighted said:**
> 
On a side note, what ATI card do you have?  If it is older than the x800 then you should have full composite/3d functionality with the OSS radeon driver.  I used that for a long time and it worked wonderfully, and was completely open source.

Boy, I must have been right at the cutoff.  I had an x800 XL.  The OSS drivers didn't work well when I ran opengl stuff, especially games.  So it works well with the older ones, huh?

---

### Post by aks44 on 2007-06-19
As far as I can tell, my ATI 9600 works fine with Beryl / AIGLX, using the OSS Radeon driver.

---

### Post by CarpKing on 2007-06-19
> **aks44 said:**
> As far as I can tell, my ATI 9600 works fine with Beryl / AIGLX, using the OSS Radeon driver.

Same here, though using other OpenGL stuff at the same time is iffy (tends to cause flickering and such) and things like Google Earth are really slow.

---

### Post by juxtaposed on 2007-06-19
> f it is older than the x800 then you should have full composite/3d functionality with the OSS radeon driver.

Really? So my x200 integrated can do stuff? :P

I thought that 'ati' was the open source just 2d one, while fglrx was the closed source 3d + 2d one.

EDIT: I tried setting the driver to radeon in xorg.conf, but it went back to just 'ati'.

Sudo dpkg-reconfigure xserver-xorg doesn't have an option for radeon.

---

### Post by blah blah blah on 2007-06-19
> **forrestcupp said:**
>  an nvidia card.

That's not how you pronounce "nvidia". [-X

---

### Post by forrestcupp on 2007-06-19
> **blah blah blah said:**
> That's not how you pronounce "nvidia". [-X

how do you pronounce it then?

---

### Post by eldragon on 2007-06-19
> **juxtaposed said:**
> Really? So my x200 integrated can do stuff? :P

I thought that 'ati' was the open source just 2d one, while fglrx was the closed source 3d + 2d one.

EDIT: I tried setting the driver to radeon in xorg.conf, but it went back to just 'ati'.

Sudo dpkg-reconfigure xserver-xorg doesn't have an option for radeon.

you need to set it to ati which is the open source radeon driver....

make sure to uninstall the fglrx drivers and the linux restricted module that it uses. otherwise, no 3d for you :)

---

### Post by forrestcupp on 2007-06-19
> **blah blah blah said:**
> That's not how you pronounce "nvidia". [-X

I looked it up on wikipedia:

> NVIDIA Corporation (NASDAQ: NVDA) (pronounced /&#603;n&#712;v&#618;d&#618;&#601;/) is an American corporation and a worldwide leader in GPU technologies for video cards, graphics cards, workstations, desktop computers, handhelds and more.

See, I was pronouncing it right.

---

