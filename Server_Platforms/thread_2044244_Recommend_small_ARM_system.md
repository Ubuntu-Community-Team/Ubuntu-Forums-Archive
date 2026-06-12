---
title: "Recommend small ARM system"
date: 2012-08-19
forum: Server Platforms
---

### Post by bakegoodz on 2012-08-19
I bought a couple Raspberry Pi and then sold them because it wasn't powerful enough for me. (I made $75 off 2 RaspPis, cha ching)  Also RaspPi doesn't run Ubuntu (yet?) No offense to Debian, but I like Ubuntu a little better.
I caught the bug for tiny ARM systems and I want nice one for $100 - $150
So I have found:
Cubox [http://www.solid-run.com/products/cubox](http://www.solid-run.com/products/cubox)
Odroid-X [http://www.hardkernel.com/renewal_2011/products/prdt_info.php](http://www.hardkernel.com/renewal_2011/products/prdt_info.php)

I leaning towards the Cubox, because it has eSata and Gb Ethernet and there seems to be a nice budding community for it too.
Which platform do you think is more Promising? Any other platforms?
Not worth mentioning Gooseberry, they are just a China Brand Android tablet motherboard. They only run Android.

---

### Post by LHammonds on 2012-08-19
I'm also interested in hardware to power a custom media player.  I'm in the process of converting all my Bluray and DVDs to digital files and about to start looking for inexpensive hardware to run a media player on all my TVs.

I'm looking at XBMC as my player of choice but I have not yet started looking at the hardware that is available out there.

I have found the following articles of interest in this regard:

[Build a silent/standalone xbmc media center]("http://lifehacker.com/5391308/build-a-silent-standalone-xbmc-media-center-on-the-cheap")
 - [Acer Nettop 1.8GHz]("http://www.newegg.com/Product/Product.aspx?Item=N82E16883103629") ($230)
- [ASUS Eee Box 1.6GHz]("http://www.newegg.com/Product/Product.aspx?Item=N82E16883220144R") ($173)
[Pandaboard]("http://pandaboard.org/content/resources/getting-started")
[Igloo Snowball board]("http://www.igloocommunity.org/")
[Versatile Express board]("http://www.arm.com/products/tools/development-boards/versatile-express/index.php")
[Origen Board]("http://www.origenboard.org/")
[Xtreamer Ultra2 Delux]("http://www.xtreamer.net/ultra2/") ($300)

As I find other hardware options out there that run Ubuntu, I'll update this post.

The Odroid-X won't work for me since it does not have HDMI output.
The CuBox seems to sold out and may or may not be able to handle HD.

Thanks,
LHammonds

---

### Post by papibe on 2012-08-19
Hi bakegoodz.

There are starting to appear ARM-based Android set top devices, both very affordable and able to play 1080p.

The only piece missing was XBMC, but now it is in the near future (read [here]("http://xbmc.org/theuni/2012/07/13/xbmc-for-android/")).

I've recently learned about this device: [Pivos Xios]("http://www.pivosgroup.com/xios.html"), currently at $114.99 at Newegg ([here]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815645003")).

Just a few thoughts.
Regards.

---

### Post by bakegoodz on 2012-08-19
Like the RaspPi both devices have a few weeks lead time. Does the Pivos run Ubuntu? A bunch of Odroid-Xs are use used by the Raspbian distro leader to recompile Debian packages. It has more ram, but I can't even find a case to house it. I also found the Mele A 1000, but you have to buy from China from questionable website. [http://liliputing.com/2012/03/mele-a1000-is-a-70-hackable-linux-friendly-arm-based-pc.html](http://liliputing.com/2012/03/mele-a1000-is-a-70-hackable-linux-friendly-arm-based-pc.html)

---

### Post by LHammonds on 2012-08-19
If you have the tools, you can make your own case.

[Example]("http://www.youtube.com/watch?v=71S9fek0FKA") (1 of a few thousand examples out there)

---

### Post by pchokola on 2012-08-19
Oops, I see you already found the Odroid-X.

---

### Post by cariboo on 2012-08-19
There is a list of supported devices [here]("http://www.linaro.org/downloads/")

---

### Post by bakegoodz on 2012-08-23
I'm going to try to make my project work with a RaspPi, maybe it can optimised enough not to run too slow. The Cubox was going to be $160 with shipping and a Pandaboard with a case is about $200. It is just too costly, you can get a booksize PC for less. A book size PC use more electricity, but are more powerful. All but the RaspPi all over priced and oversize for many embedded projects.

---

### Post by LHammonds on 2012-08-24
The Raspberry Pi (Model B) for $35 USD certainly does look like a great choice.

You'll  just need a case ( ~$7 ), USB power supply ( ~$8 ), SD Flash memory card  (4+ GB) ( ~$8 ) and USB hub (at least during setup) ( ~$6 )...USB mouse and  keyboard also needed.

So for about $70 you could have yourself a nice little server to play with.

There  are quite a few [OS  Distribution images]("http://elinux.org/RPi_Distributions") to choose from and several are XBMC-based  which is perfect for my needs.

According to the  [FAQ]("http://www.raspberrypi.org/faqs"), the GPU is also  supposed to be able to handle 1080p movies (Bluray quality).  With the  HDMI output for video and audio, that would be perfect for TV or AV  systems that take HDMI input.

I happen to have several 5V USB  power supplies laying around because of the amount of iPod and iPhones  we have so I'll won't need to buy that particular component...although  PoE would be an awesome feature for this board.

**EDIT 2012-08-26:** I just ordered my 1st Raspberry Pi model b.  It is on backorder and may take some number of weeks to get here.

LHammonds

---

