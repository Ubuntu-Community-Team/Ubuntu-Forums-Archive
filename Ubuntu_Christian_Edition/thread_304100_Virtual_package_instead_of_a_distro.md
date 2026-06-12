---
title: "Virtual package instead of a distro?"
date: 2006-11-21
forum: Ubuntu Christian Edition
---

### Post by og-emmet on 2006-11-21
Have you thought of building a single meta/virtual package instead of a separate distro? A virtual .deb package could easily put be together with everything you'd want from your own distro. The size would be less than a few megs and could include:

1. Links (.deb not http) to packages on Ubuntu's servers.
2. Links to other repositories (like Debian's) for other packages.
3. Links to packages not included in the standard Ubuntu distros like flash and mp3 support.
4. Custom artwork, config files, etc. dropped exactly where you want them.
 
While a stand alone distro has it advantages it's a monster to keep up to date. The virtual package route would save you this hassle and many, many hours of work. gdebi-gtk makes for an installer anyone can use. After the install it would look exactly like your custom distro.

If you want to avoid downloading issues just build the virtual package and burn it with the dependent pkgs on a cd. You could ever use a 215M 80mm mini-cd or 50M "business card" cd (always eye catching).
 
This would avoid mastering issues which seem to always crop up, greatly simplify adding cross platform support and allow for the user to use their choice of Ubuntu/Kubuntu/Xubuntu. Your legal liability and exposure also drops considerably. Just one frivolous law suit (even a totally bogus one) will cost you thousands in legal fees.  

Try it yourself by grabbing a package (say from: [http://packages.debian.org/stable/games/fortune-mod](http://packages.debian.org/stable/games/fortune-mod)) from a web browser. You should be presented with a choice of saving or opening with gdebi-gtk (choose this one). gdebi-gtk should open up and allow you to directly install. (BTW, don't install it - just for demo use).

I think in the long run this route will save a ton of time and hassle. Plus if some users need paid support Ubuntu can make a few bucks.

It's your baby and this is just a suggestion.

---

### Post by mhancoc7 on 2006-11-21
> **og-emmet said:**
> Have you thought of building a single meta/virtual package instead of a separate distro? A virtual .deb package could easily put be together with everything you'd want from your own distro. The size would be less than a few megs and could include:

1. Links (.deb not http) to packages on Ubuntu's servers.
2. Links to other repositories (like Debian's) for other packages.
3. Links to packages not included in the standard Ubuntu distros like flash and mp3 support.
4. Custom artwork, config files, etc. dropped exactly where you want them.
 
While a stand alone distro has it advantages it's a monster to keep up to date. The virtual package route would save you this hassle and many, many hours of work. gdebi-gtk makes for an installer anyone can use. After the install it would look exactly like your custom distro.

If you want to avoid downloading issues just build the virtual package and burn it with the dependent pkgs on a cd. You could ever use a 215M 80mm mini-cd or 50M "business card" cd (always eye catching).
 
This would avoid mastering issues which seem to always crop up, greatly simplify adding cross platform support and allow for the user to use their choice of Ubuntu/Kubuntu/Xubuntu. Your legal liability and exposure also drops considerably. Just one frivolous law suit (even a totally bogus one) will cost you thousands in legal fees.  

Try it yourself by grabbing a package (say from: [http://packages.debian.org/stable/games/fortune-mod](http://packages.debian.org/stable/games/fortune-mod)) from a web browser. You should be presented with a choice of saving or opening with gdebi-gtk (choose this one). gdebi-gtk should open up and allow you to directly install. (BTW, don't install it - just for demo use).

I think in the long run this route will save a ton of time and hassle. Plus if some users need paid support Ubuntu can make a few bucks.

It's your baby and this is just a suggestion.

Well, the main reason for having a full iso is the fact that I wanted those who are completely new to Linux to be able to download the full distro. I think sometimes we forget that not everyone understands what metapackages are.

Now, I have tried to put together a metapackage, and the problem that I ran into was the fact that the dansguardian setup requires so much tweaking post install. I was unable to get this to work in the form of a meta-package. That is why I went the route of scripts.

Anyway, thank you for the suggestions. I am always looking for ways to make the project better.

God Bless, Jereme

---

### Post by junk269 on 2006-12-29
jereme im one of the ones you refer to. thanks for noticing us lol an hi.  any idea  who slaps the iso's together? i really want/need 1 made for me an the people weening off the dredded windows........woo woo woo lol yes i said it im not brainwashed im not a teckie eather lol :D ubuntu rocks man an i  can say that ive tryd most of the live cds i could get my hands on lol 
Ubuntu gets :KS :KS :KS  out of 3 

> **mhancoc7 said:**
> Well, the main reason for having a full iso is the fact that I wanted those who are completely new to Linux to be able to download the full distro. I think sometimes we forget that not everyone understands what metapackages are.

Now, I have tried to put together a metapackage, and the problem that I ran into was the fact that the dansguardian setup requires so much tweaking post install. I was unable to get this to work in the form of a meta-package. That is why I went the route of scripts.

Anyway, thank you for the suggestions. I am always looking for ways to make the project better.

God Bless, Jereme

---

### Post by mhancoc7 on 2006-12-29
> **junk269 said:**
> jereme im one of the ones you refer to. thanks for noticing us lol an hi.  any idea  who slaps the iso's together? i really want/need 1 made for me an the people weening off the dredded windows........woo woo woo lol yes i said it im not brainwashed im not a teckie eather lol :D ubuntu rocks man an i  can say that ive tryd most of the live cds i could get my hands on lol 
Ubuntu gets :KS :KS :KS  out of 3

Thanks for your kind words. I am working on a little project that may be what you are looking for. I don't want to give too much info as I am not really ready to release it yet. :)

I have put together what I call Ubuntu XP. It has the look and feel of Windows XP. It has codecs and what not preinstalled. You can download it from the link below. 

This comes with no support and should be USED AT YOUR OWN RISK. (Sorry I have to say that)

[http://www.mediafire.com/?2nytbndntyt](http://www.mediafire.com/?2nytbndntyt)

Jereme

---

### Post by junk269 on 2006-12-30
my laptop is to old an slow to run xp lol heck i m just staying afloat now lol if you can email me id like to bend your ear for a few mins. or im me will work too thanks for the comeback bythe way.



1thing why does ubuntu not like my wireless card from what im reading itll work i know it does on knoppix. an linspire <--i didnt have to do a thing  why dont ubuntu types have the eyes to see(so to speak) the wireless cards that are out?](*,) ugh...

---

