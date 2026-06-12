---
title: "SuSE to Ubuntu"
date: 2007-01-24
forum: The Cafe
---

### Post by kostaschatzi on 2007-01-24
Dear users hello...

I have heard a lot of nice things about ubuntu and the best of them is what its name mean.I am really new in linux and i have tried my luck with suse and i still have it.But when i found what the name ubuntu means i started downloading it.i know the differences it has with suse like the debian and the gnome stuff but i surely don t have a problem about these.I have a read quite some threads but unfortunately i didn t come up to any indication to the thing that concerns me.My question is if anyone can tell me if it is useless for me to install it because it will anyway not work.My pc has the following features

Asus P5B retail
Intel core 2 duo 6400
ati x1900 xt
western digital sata2 250g
2g ddr2
 
it will also be dual boot.the other os is winxp

FInally, i would like to ask if there is a compatibility or any other problem with maya and generally 3d animation programms as well as multimedia(i want it to support wmv,mpg,avi,...,mkv files etc.)

Thank you in advance
kostaschatzi

---

### Post by Quillz on 2007-01-24
If SuSE works on that same hardware, I can almost guarantee you that Ubuntu will work.

BTW... Why settle for GNOME? If you want to use KDE on (K)Ubuntu, go right ahead. Linux is all about choices. Never accept the default as your only option.

---

### Post by Choad on 2007-01-24
not sure about maya, im sure it can be done tho

blender is in the repositories, and works flawlessly.

your ati card will start using the radeon driver probably. its the open source driver for ati cards. you can optionally install ati's fglrx driver through synaptic to get more performance out of it

the install is perfectly seemless. after you boot the cd, you can play arround in the live cd environment, and when you're ready, just double click the install icon on the desktop.

the installer has a partition management built in, so you can avoid overwriting your xp partition

all being well, it will configure grub to boot windows as an option, although it will boot ubuntu by default. you can change this if you want though.

core 2 duo is supported by default. it should all be fine

---

### Post by kostaschatzi on 2007-01-24
Thank you for the rapid response

This is surely nice to hear.One more thing...Suse multimedia comes crippled...does the same happen in ubuntu or would i be able with VLC for example to play any kind or video or audio file?

---

### Post by Choad on 2007-01-24
multimedia is the same in all linux distros except linspire (which you pay for)

its all down to legal issues in america.

easy enough to sort it out tho. yep, VLC is in the repositories, and yep, it will play anything you throw at it just like the windows version. you do have to enable the "non free" repositories tho, but this is just a few clicks through some menus

search this forum and you will find a dozen threads on how to do this

---

### Post by Quillz on 2007-01-24
> **kostaschatzi said:**
> Thank you for the rapid response

This is surely nice to hear.One more thing...Suse multimedia comes crippled...does the same happen in ubuntu or would i be able with VLC for example to play any kind or video or audio file?
By default, no. You can only play open source formats. Like in SuSE, you would need to use your package manager to install non-free codecs, like MP3.

---

### Post by kostaschatzi on 2007-01-24
Thank you choad

Your responses give me a bit more push to go for it...

---

### Post by kostaschatzi on 2007-01-24
I iwll surely not have a problem with this quillz...

I will surely try to put all the codecs but in suse as it seems there was a storm of dependencies that never let me play the files normally...

---

### Post by Quillz on 2007-01-24
> **kostaschatzi said:**
> I iwll surely not have a problem with this quillz...

I will surely try to put all the codecs but in suse as it seems there was a storm of dependencies that never let me play the files normally...
There are dependencies in Ubuntu, but the whole point of a package manager (no matter the distro) is that it manages... the packages. It will install all the dependencies, or at least, it should.

---

### Post by kostaschatzi on 2007-01-24
Thank you guys...I will install the distribution and i will try to sort any problems to come up...

kostaschatzi

---

### Post by v8YKxgHe on 2007-01-24
Maya works fine, works better than in WinXP. There is a guide here that shows you how to [install maya]("http://ubuntuforums.org/showthread.php?t=66859&highlight=install+maya") - it's for Maya 7, but it works for Maya 8 on Edgy to.

---

### Post by Quillz on 2007-01-24
> **kostaschatzi said:**
> Thank you guys...I will install the distribution and i will try to sort any problems to come up...

kostaschatzi
Good luck! Remember we're here to help, although I doubt you'll need it. Your experience with SuSE should help you overcome any issues you may have, since Ubuntu is very friendly with desktops that use modern hardware.

---

### Post by mips on 2007-01-24
> **Choad said:**
> multimedia is the same in all linux distros except linspire (which you pay for)


Not true. There is Sabayon, Mint etc where nothing is crippled, everything actually works out of the box.

---

### Post by Choad on 2007-01-24
> **mips said:**
> Not true. There is Sabayon, Mint etc where nothing is crippled, everything actually works out of the box.
doesnt that make it illegal in america?

or am i missing something?

sureley if it was possible, ubuntu would be the same too?

---

### Post by Quillz on 2007-01-24
It may or may not be illegal, depending on where you live. If it is illegal, then you take a risk. (Although I highly doubt the Secret Service is going to bust down your door and arrest you for having MP3 codecs on your Linux box.)

---

### Post by Choad on 2007-01-24
> **Quillz said:**
> It may or may not be illegal, depending on where you live. If it is illegal, then you take a risk. (Although I highly doubt the Secret Service is going to bust down your door and arrest you for having MP3 codecs on your Linux box.)
well exactly!

ubuntu wouldnt be able to ship cd's to america if they included these codecs, would they?

---

### Post by MkfIbK7a on 2007-01-24
> **Quillz said:**
> It may or may not be illegal, depending on where you live. If it is illegal, then you take a risk. (Although I highly doubt the Secret Service is going to bust down your door and arrest you for having MP3 codecs on your Linux box.)

it **_is_** illegal in america but none is going to arrest you for having wmv codecs...

---

### Post by darkhatter on 2007-01-24
I believe maya works on ubuntu, but its been giving me nothing but problems, I've only tried version 7 I'm sure newer versions work

---

### Post by mips on 2007-01-24
> **Choad said:**
> doesnt that make it illegal in america?

or am i missing something?

sureley if it was possible, ubuntu would be the same too?

Contrary to popular belief (in the US) the world does not revolve around the USA.

We don't all live in the USA, the OP does not and neither do I. So I don't care for US law.

I cannot speak on ubuntus behalve but they reside outside the USA, Isle of Man I think although they operate from london.

---

### Post by mips on 2007-01-24
> **Choad said:**
> well exactly!

ubuntu wouldnt be able to ship cd's to america if they included these codecs, would they?

They could ship them to the USA but I dunno what your customs people would do with them though.

Sabayon & Mint for example you can buy online and have shipped to the USA.

---

### Post by Choad on 2007-01-24
> **mips said:**
> Contrary to popular belief (in the US) the world does not revolve around the USA.

We don't all live in the USA, the OP does not and neither do I. So I don't care for US law.

I cannot speak on ubuntus behalve but they reside outside the USA, Isle of Man I think although they operate from london.
crikey!

take that stick and put it somewhere other than ur ***

im from england, not america. america != the world but it is home of microsoft AND apple, and a very, very large portion of the worlds software developers. dont you think turning our back on america because of fiddly codec issues might be a foolish idea in the grand scheme of things? perhaps not in ubuntus best interest?

---

### Post by mips on 2007-01-24
> **Choad said:**
> crikey!

take that stick and put it somewhere other than ur ***

im from england, not america. america != the world but it is home of microsoft AND apple, and a very, very large portion of the worlds software developers. dont you think turning our back on america because of fiddly codec issues might be a foolish idea in the grand scheme of things? perhaps not in ubuntus best interest?

I'm sorry, did you want the sugar coated version ? That was a straight forward reply, you obviously took offense to it.

Stick comment is not nice, but i'm pretty thick skinned.

I never said you were in the USA (America is basically two continents, North & South of which the USA is part of). If you look at the part in brackets 'in the US' you would realise this.

Why must we always bow to the USA. We should rather change this subservent attitude of ours and ignore them. This DRM, Software patents thing is something they came up with. Won't be long and the internet will be something similair to pay per view cable if they get their way.

---

### Post by Choad on 2007-01-24
technically, north+south america is called the americas

cheeky north americans stole the name, and then called the original america "south america"

why must we bow to the US? well we dont. but we CHOOSE to play by their rules, in the hope of one day removing microsofts dominance. if we didnt play by their rules, ubuntu would have a much slimmer chance of becoming mainstream. im not saying that its right, its just a fact of life. america is dominant in this industry. if we didnt, another distro would gain in popularity and ubuntu would slowly fade in to obscurity like the other 95% of linux distributions.

---

### Post by AndyCooll on 2007-01-24
> **Quillz said:**
> BTW... Why settle for GNOME? If you want to use KDE on (K)Ubuntu, go right ahead. Linux is all about choices. Never accept the default as your only option.

I disagree. Stick with the defaults ...at least to begin with. Get to know the distro a little bit, and GNOME is the default (and hence the most likely to have answers available on these forums). Once you feel confident, then by all means consider other desktops ...you never know you might find you prefer KDE, or XFCE, or Enlightenment, or ...

:cool:

---

### Post by doobit on 2007-01-24
> **mips said:**
> I'm sorry, did you want the sugar coated version ? That was a straight forward reply, you obviously took offense to it.

Stick comment is not nice, but i'm pretty thick skinned.

I never said you were in the USA (America is basically two continents, North & South of which the USA is part of). If you look at the part in brackets 'in the US' you would realise this.

Why must we always bow to the USA. We should rather change this subservent attitude of ours and ignore them. This DRM, Software patents thing is something they came up with. Won't be long and the internet will be something similair to pay per view cable if they get their way.

GPL also something "we" came up with. We don't ask you to bow to America, just challenge you to come up with a better idea. ;)

---

