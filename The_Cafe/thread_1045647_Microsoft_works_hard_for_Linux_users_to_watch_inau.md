---
title: "Microsoft works hard for Linux users to watch inauguration via Moonlight &amp; Mono"
date: 2009-01-20
forum: The Cafe
---

### Post by Grant A. on 2009-01-20
[http://news.slashdot.org/article.pl?sid=09/01/20/134228]("http://news.slashdot.org/article.pl?sid=09/01/20/134228")

This is rather nice of them. This shows that not only do they support Mono, but this is proof the Novell deal is working since Novell leads the Mono project and Microsoft is contractually required to help out.

Although, could this be a new page for Microsoft?

---

### Post by jenkinbr on 2009-01-20
WHOA!

Microsoft is required to contribute to Open Source Software?

Whether this is a new page for Microsoft, I don't know.  Time will tell what MS does with this....

---

### Post by smartboyathome on 2009-01-20
> **jenkinbr said:**
> WHOA!

Microsoft is required to contribute to Open Source Software?

Whether this is a new page for Microsoft, I don't know.  Time will tell what MS does with this....

They are because the European Union declared them a monopoly and Microsoft doesn't want to go to court with the EU.

---

### Post by Grant A. on 2009-01-20
> **smartboyathome said:**
> They are because the European Union declared them a monopoly and Microsoft doesn't want to go to court with the EU.

As a provision of the Microsoft-Novell deal, not only does it grant patent immunity to Novell, but it also requires Microsoft to contribute to open source projects.

I personally declare this a small victory for cooperation between Microsoft and the Linux community. Hopefully Microsoft will look towards licensing some major products as open source. :popcorn:

---

### Post by speedwell68 on 2009-01-20
> **Grant A. said:**
> As a provision of the Microsoft-Novell deal, not only does it grant patent immunity to Novell, but it also requires Microsoft to contribute to open source projects.

I personally declare this a small victory for cooperation between Microsoft and the Linux community. Hopefully Microsoft will look towards licensing some major products as open source. :popcorn:

Yeah, if they could release the source code for the next release of Office, that would be just dandy.  I know OpenOffice is good, but MS Office is better.  A bit bloaty but better.

---

### Post by Thirtysixway on 2009-01-20
Releasing the source of office would never happen.  That's like their next most popular product after windows.  It brings in so much money for microsoft.

---

### Post by speedwell68 on 2009-01-20
> **Thirtysixway said:**
> Releasing the source of office would never happen.  That's like their next most popular product after windows.  It brings in so much money for microsoft.

I believe I was being ironic.:D

---

### Post by directhex on 2009-01-21
> **Grant A. said:**
> As a provision of the Microsoft-Novell deal, not only does it grant patent immunity to Novell, but it also requires Microsoft to contribute to open source projects.

I personally declare this a small victory for cooperation between Microsoft and the Linux community. Hopefully Microsoft will look towards licensing some major products as open source. :popcorn:

Novell do not have patent immunity from Microsoft, nor vice versa.

Novell/MS *customers* do. It's an important distinction, as it still means Novell can sue MS for patent infringement (and vice versa) should they want to

---

### Post by Dragonbite on 2009-01-21
> **Grant A. said:**
> [http://news.slashdot.org/article.pl?sid=09/01/20/134228]("http://news.slashdot.org/article.pl?sid=09/01/20/134228")

This is rather nice of them. This shows that not only do they support Mono, but this is proof the Novell deal is working since Novell leads the Mono project and Microsoft is contractually required to help out.

Although, could this be a new page for Microsoft?

The MS/Novell deal is for interoperability and virtualization. Mono is not specified in there and Microsoft has not helped as much with Mono as it has with Moonlight.  While Moonlight is based on Mono it isn't the same thing as Mono.

The Patent protection (or "I promise not to sue if you promise not to sue") is for customers and (individual) developers of Novell products (which is the way Mono and Moonlight developers are protected, though Mono and Moonlight themselves are not).

Honestly, I don't think MS really gives a darn about the EU calling it a Monopoly.  Looks like a stuffy group trying to "stick it to the man" than anything else.

---

### Post by bobbob1016 on 2009-01-21
No x86_64bit Ubuntu support though.

---

### Post by directhex on 2009-01-21
> **bobbob1016 said:**
> No x86_64bit Ubuntu support though.

Really?

**Really?**

[size=4]REALLY?[/size]

```
jms@osc-franzibald:~$ dpkg -l \*moon\* | grep ^ii
ii  libmoon                                                      1.0-1~dhx2                                           Free Software clone of Silverlight 1.0 - unstable runtime library
ii  moonlight-plugin-core                                        1.0-1~dhx2                                           Free Software clone of Silverlight 1.0 - plugin core components
ii  moonlight-plugin-mozilla                                     1.0-1~dhx2                                           Free Software clone of Silverlight 1.0 - Xulrunner 1.9 plugin
```

Worked fine for me for watching the inauguration. Unlike Adobe Flash, Moonlight is multi-platform, including things like PowerPC

---

### Post by jrusso2 on 2009-01-21
I never did get it working for the inauguration which I ended up using Flash.  Moonlight does work however on some demo sites I found by searching.

---

### Post by sydbat on 2009-01-21
Does it work side-by-side with Flash? Or does one have to be removed for the other to work?

---

### Post by fluxlizard on 2009-01-21
Does this mean I can watch it now on Netflix sooner?

---

### Post by directhex on 2009-01-21
> **sydbat said:**
> Does it work side-by-side with Flash? Or does one have to be removed for the other to work?

They're different plugins, for different purposes. They're no more incompatible than, say, having Java and Flash support at the same time. In fact, some sites use both SL and Flash at the same time

> **fluxlizard said:**
> Does this mean I can watch it now on Netflix sooner?

Netflix requires Silverlight 2.0, due to DRM (1.0 does not support DRM), and Moonlight only offers Silverlight 1.0 support right now.

---

### Post by eragon100 on 2009-01-21
> **bobbob1016 said:**
> No x86_64bit Ubuntu support though.

CRAP I watched the stream perfectly on 64-bit ubuntu, there is a one-mouse-click install 64-bit version of the plugin. And I read multiple other people saying it works fine on their 64-bit ubuntu in the other thread about this.

I will repeat what I said there: way to go MS. Kudos to you. Seriously! :popcorn: :KS

---

### Post by sydbat on 2009-01-21
I took the plunge and installed it for testing purposes...but every site I have checked (so far) wants me to install other 'Microsoft codecs' to view content. I cancel the popup and cannot view anything. Suggestions??

---

### Post by directhex on 2009-01-21
> **sydbat said:**
> I took the plunge and installed it for testing purposes...but every site I have checked (so far) wants me to install other 'Microsoft codecs' to view content. I cancel the popup and cannot view anything. Suggestions??

Use packages which are compiled against FFmpeg?

---

### Post by timcredible on 2009-01-21
so what sites does this work on?  i tried a few that i couldn't use before like abc.com, cwtv.com, they still don't work.  so, microsoft went and made a linux version of their video player, but all sites still specifically look for and deny linux?  what good is this?

---

### Post by directhex on 2009-01-21
> **timcredible said:**
> so what sites does this work on?  i tried a few that i couldn't use before like abc.com, cwtv.com, they still don't work.  so, microsoft went and made a linux version of their video player, but all sites still specifically look for and deny linux?  what good is this?

Sites which look for Silverlight 2.0 won't work, as Moonlight doesn't yet support SL2.

---

### Post by bobbob1016 on 2009-01-22
> **directhex said:**
> Really?

**Really?**

[size=4]REALLY?[/size]

```
jms@osc-franzibald:~$ dpkg -l \*moon\* | grep ^ii
ii  libmoon                                                      1.0-1~dhx2                                           Free Software clone of Silverlight 1.0 - unstable runtime library
ii  moonlight-plugin-core                                        1.0-1~dhx2                                           Free Software clone of Silverlight 1.0 - plugin core components
ii  moonlight-plugin-mozilla                                     1.0-1~dhx2                                           Free Software clone of Silverlight 1.0 - Xulrunner 1.9 plugin
```

Worked fine for me for watching the inauguration. Unlike Adobe Flash, Moonlight is multi-platform, including things like PowerPC

You're right, I mean how could I have missed it saying Ubuntu x86_64 on their support page [http://mono-project.com/MoonlightSupportedPlatforms](http://mono-project.com/MoonlightSupportedPlatforms)

x86-64 (64 bit) 	 SUSE Linux Enterprise Desktop 10 	 yes 	 yes
openSUSE 11.0 		yes 

Nothing about 64bit Ubuntu...

Edit:  No OFFICIAL support, is that better?

---

### Post by sydbat on 2009-01-22
Aaaaand...I just finished uninstalling it. It kept crashing FF. Not sure why, but it is the only add-on I have installed in months and FF was working perfectly beforehand. Coincidence?

---

