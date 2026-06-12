---
title: "I have a new toy"
date: 2009-05-17
forum: The Cafe
---

### Post by gnomeuser on 2009-05-17
Being a Fluendo beta tester once again paid off. Here is the latest toy which soon will be on offer (pending naturally that it doesn't blow up horribly in testing). 

Fluendo DVD, a legally licensed DVD player for Linux (currently i386 and x86_64) along with media package version 8 (I haven't investigated the news in this one yet).

So far testing has been good, it plays back DVDs perfectly, the menus work and everything is very shiny. 

Screenshot provided for your enjoyment.

---

### Post by pwnst*r on 2009-05-17
imo, toys are tangible, physical objects.  

cool none the less.

---

### Post by metallicamike on 2009-05-17
> **pwnst*r said:**
> imo, toys are tangible, physical objects.  

cool none the less.

lol

---

### Post by calrogman on 2009-05-17
Or you could just, you know, use VLC, totem-xine, mplayer or any other media player that supports DVD playback.

---

### Post by lukjad on 2009-05-17
> **calrogman said:**
> Or you could just, you know, use VLC, totem-xine, mplayer or any other media player that supports DVD playback.
True, but some places they are in a legal gray area. If you are running a business, you may think that having this is a nice way to cut down on legal fees. :)

---

### Post by Patrick Snyder on 2009-05-17
> **lukjad007 said:**
> [QUOTE=calrogman;7297628]Or you could just, you know, use VLC, totem-xine, mplayer or any other media player that supports DVD playback.
True, but some places they are in a legal gray area. If you are running a business, you may think that having this is a nice way to cut down on legal fees. :)[/QUOTE]

Where are using these legally grey?  Are they not all FOSS?  They don't promote the subversion of copy protection.  Have there been any lawsuits involving the use of VLC, totem-xine, or mplayer?

I was under the impression that using these 3 programs would be about as "legally grey" as using Google.

---

### Post by BuffaloX on 2009-05-17
> **calrogman said:**
> Or you could just, you know, use VLC, totem-xine, mplayer or any other media player that supports DVD playback.

Does the menus work too in those?

---

### Post by gnomeuser on 2009-05-17
> **Patrick Snyder said:**
> Where are using these legally grey?  Are they not all FOSS?  They don't promote the subversion of copy protection.  Have there been any lawsuits involving the use of VLC, totem-xine, or mplayer?

I was under the impression that using these 3 programs would be about as "legally grey" as using Google.

They are not just legally a grey area anywhere that has software patents. Additionally DVD playback in Open Source requires libdvdcss which is illegal (tried in court) many many places.

While I can here in Denmark use them legally, and I am legally (at least the last time I checked) allowed to break protection schemes if they prevent me from viewing the content most places that is not the case.

For situations like that, especially when say an OEM ships Linux on a machine they need a license for the patents involved with media playback. This is why things like the fluendo codec pack exists as well as the DVD player. There is a clear market for it.

Now as a private person it is very unlikely that the patent holders will come after you, it is likely to expensive in comparison to the fee they might pull in from you violating their patent license. If however a DELL or a Red Hat were to ship these components they would be sued to kingdom come.

Having this available removes a speedbump for Linux adoption in OEM deployments. Your OEM can buy this and Linux will have media playback including DVD support out of the box, yes it will add costs but it will make Linux a much more attractive target for vendors who have to comply with the law in such places as the US.

Aside that as private person or a company you might like to know that you paid for support from people who have full access to the specifications for these codecs. Even if you are legally unencumbered in using the open source versions of these codecs. 

In a world were open formats have not yet been fully accepted, Fluendo provides a fine service. I am happy that I get to test these products as they help make Linux a better place, I believe getting a piece of the OEM pie is vital and these tools being available to us is important to making that happen.

---

### Post by nolliecrooked on 2009-05-17
> **gnomeuser said:**
> They are not just legally a grey area anywhere that has software patents. Additionally DVD playback in Open Source requires libdvdcss which is illegal (tried in court) many many places.

While I can here in Denmark use them legally, and I am legally (at least the last time I checked) allowed to break protection schemes if they prevent me from viewing the content most places that is not the case.

For situations like that, especially when say an OEM ships Linux on a machine they need a license for the patents involved with media playback. This is why things like the fluendo codec pack exists as well as the DVD player. There is a clear market for it.

Now as a private person it is very unlikely that the patent holders will come after you, it is likely to expensive in comparison to the fee they might pull in from you violating their patent license. If however a DELL or a Red Hat were to ship these components they would be sued to kingdom come.

Having this available removes a speedbump for Linux adoption in OEM deployments. Your OEM can buy this and Linux will have media playback including DVD support out of the box, yes it will add costs but it will make Linux a much more attractive target for vendors who have to comply with the law in such places as the US.

Aside that as private person or a company you might like to know that you paid for support from people who have full access to the specifications for these codecs. Even if you are legally unencumbered in using the open source versions of these codecs. 

In a world were open formats have not yet been fully accepted, Fluendo provides a fine service. I am happy that I get to test these products as they help make Linux a better place, I believe getting a piece of the OEM pie is vital and these tools being available to us is important to making that happen.

How many euros is this and the full codec pack? and does it work with openSUSE?

---

### Post by gnomeuser on 2009-05-17
> **nolliecrooked said:**
> How many euros is this and the full codec pack? and does it work with openSUSE?

[28&#8364; including 1 year of support and upgrades](http://www.fluendo.com/shop/product/complete-set-of-playback-plugins/) - I don't yet know the price for the DVD player product as it is not on the market yet whereas the codec pack is.

I don't know when media pack 8 is planned to ship but I have access to the beta, if you have files you want tested poke me via private message and I will get that done.

The install works with any distribution for the ix86 and x86_64 architectures. The beta team gets them as tarballs, rpms and deb packages, I assume those are the distribution methods available for the commercial clients as well. I have personally tested them on Ubuntu, Fedora, openSUSE and Foresight (all ix86 and x86_64). Additionally I know that OpenSolaris (ix86 and x86_64) is supported but I haven't personally tested that option.

You can either install using the packages or just put the content of the tarball into ~/.gstreamer-0.10/plugins.

---

### Post by chris200x9 on 2009-05-17
> **gnomeuser said:**
> [28€ including 1 year of support and upgrades](http://www.fluendo.com/shop/product/complete-set-of-playback-plugins/) - I don't yet know the price for the DVD player product as it is not on the market yet whereas the codec pack is.

I don't know when media pack 8 is planned to ship but I have access to the beta, if you have files you want tested poke me via private message and I will get that done.

The install works with any distribution for the ix86 and x86_64 architectures. The beta team gets them as tarballs, rpms and deb packages, I assume those are the distribution methods available for the commercial clients as well. I have personally tested them on Ubuntu, Fedora, openSUSE and Foresight (all ix86 and x86_64). Additionally I know that OpenSolaris (ix86 and x86_64) is supported but I haven't personally tested that option.


You can either install using the packages or just put the content of the tarball into ~/.gstreamer-0.10/plugins.
28 euros....hmmm wasn't there a thread around here about OEM windows going for like $25...

---

### Post by starcannon on 2009-05-17
> **gnomeuser said:**
> Being a Fluendo beta tester once again paid off. Here is the latest toy which soon will be on offer (pending naturally that it doesn't blow up horribly in testing). 

Fluendo DVD, a legally licensed DVD player for Linux (currently i386 and x86_64) along with media package version 8 (I haven't investigated the news in this one yet).

So far testing has been good, it plays back DVDs perfectly, the menus work and everything is very shiny. 

Screenshot provided for your enjoyment.

Very nice, I'll buy a copy when its made available to the public.

---

### Post by TBOL3 on 2009-05-17
> **chris200x9 said:**
> 28 euros....hmmm wasn't there a thread around here about OEM windows going for like $25...

I heard $20.  So isn't it ironic that Linux+DVD playback costs more than Windows (for OEMs).  But than again, I don't know if default windows comes with dvd playback, as I've only used windows from an OEM, and they may be bundling their own DVD decoder.

---

### Post by gnomeuser on 2009-05-18
> **chris200x9 said:**
> 28 euros....hmmm wasn't there a thread around here about OEM windows going for like $25...

I don't know what the OEM costs for Windows is. I am sure that if you were to do an OEM license deal with Fluendo the price would go down (people tend to get flexible when you order 100.000 of pretty much anything). Thus the comparison is hardly fair.

Aside that as the Linux market grows, the number of people and more importantly companies which may need this grows. More demand should lower the price as they can exist very easily on support contracts.

But yes they are expensive however they work very well and you get support from people who really know the GStreamer framework inside and out. Fluendo does good work, and they provide a way out for people stuck in need of codec support but who cannot use the open source implementations legally.

---

### Post by fatality_uk on 2009-05-18
> **gnomeuser said:**
> I don't know what the OEM costs for Windows is. I am sure that if you were to do an OEM license deal with Fluendo the price would go down (people tend to get flexible when you order 100.000 of pretty much anything). Thus the comparison is hardly fair.

Aside that as the Linux market grows, the number of people and more importantly companies which may need this grows. More demand should lower the price as they can exist very easily on support contracts.

But yes they are expensive however they work very well and you get support from people who really know the GStreamer framework inside and out. Fluendo does good work, and they provide a way out for people stuck in need of codec support but who cannot use the open source implementations legally.

PM'd you re volume license!

---

### Post by 3rdalbum on 2009-05-18
> **gnomeuser said:**
> (people tend to get flexible when you order 100.000 of pretty much anything).

I don't think you needed that many decimal places; I doubt Fluendo would give you a license for 0.009 codec packs...

---

### Post by gnomeuser on 2009-05-18
> **3rdalbum said:**
> I don't think you needed that many decimal places; I doubt Fluendo would give you a license for 0.009 codec packs...

note to poster. , != . and my country (sane as it is sometimes) separates with . and denotes decimates with ,

I would certainly hope sanity would prevail and make that the standard.

Because 100.000 is easier to read than 100000.

---

### Post by TBOL3 on 2009-05-18
Ah, that explains a lot.  But I still think 100,000 makes more sense than 100.000 unless you mean 100.

BTW, what country are you from?

---

### Post by pwnst*r on 2009-05-18
gnomeuser
Skinny Soy Caramel Ubuntu
 
gnomeuser's Avatar
 
Join Date: Jul 2006
Location: Århus, [SIZE="7"]**[COLOR="Red"]Denmark[/COLOR]**[/SIZE]
Beans: 692

---

### Post by TBOL3 on 2009-05-18
Oops...

I actually looked there, but I didn't see a location, maybe I had inadvertently scrolled up, and was looking at someone else's.

---

### Post by pwnst*r on 2009-05-18
;)

---

### Post by calrogman on 2009-05-18
> **BuffaloX said:**
> Does the menus work too in those?

Yes.

---

