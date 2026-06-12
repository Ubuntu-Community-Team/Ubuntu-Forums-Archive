---
title: "Netflix works"
date: 2014-08-10
forum: The Cafe
---

### Post by uRock on 2014-08-10
Thanks to the following link, I have Netflix working in Ubuntu. 

[http://www.omgubuntu.co.uk/2014/08/netflix-linux-html5-support-plugins](http://www.omgubuntu.co.uk/2014/08/netflix-linux-html5-support-plugins)

---

### Post by user1397 on 2014-08-11
> **uRock said:**
> Thanks to the following link, I have Netflix working in Ubuntu. 

[http://www.omgubuntu.co.uk/2014/08/netflix-linux-html5-support-plugins](http://www.omgubuntu.co.uk/2014/08/netflix-linux-html5-support-plugins)
Indeed.  I tried it, and it works flawlessly.  I did get that error everyone keeps mentioning, but all I had to do was exit chrome and open it again, and voila.

You should probably have included "netflix" in the title of this thread to get a little more attention on the subject.  Pretty crazy how this is the only thread on the subject here, my oh my! how the cafe has changed!!!

---

### Post by mörgæs on 2014-08-11
Changed the title.

---

### Post by mooreted on 2014-08-11
Nice, Windows gets less relevant every day.

---

### Post by kostkon on 2014-08-11
> **mooreted said:**
> Nice, Windows gets less relevant every day.
And browser plugins too, thanks to HTML5.

---

### Post by pqwoerituytrueiwoq on 2014-08-12
> **kostkon said:**
> And browser plugins too, thanks to HTML5.
still waiting on flash to die:popcorn:
i still end up using it for videos regularly, but it just let it act as a download client and let mplayer handle playback

---

### Post by SeijiSensei on 2014-08-12
> **ubuntuman001 said:**
> Pretty crazy how this is the only thread on the subject here, my oh my! how the cafe has changed!!!

You haven't looked hard enough.  There are lots of discussions about Netflix.  Search the forums for "pipelight" to see a bunch of them.

---

### Post by uRock on 2014-08-12
> **SeijiSensei said:**
> You haven't looked hard enough.  There are lots of discussions about Netflix.  Search the forums for "pipelight" to see a bunch of them.

I was tempted to try PipeLight. I got all the way through to the part where the terminal listed all of the packages required to make it work, then I typed no and removed the PPA from the system.

---

### Post by SeijiSensei on 2014-08-12
Well, I've been using that solution successfully for at least half-a-year now.  Why does it bother you if an application has a lot of dependencies?  Here's the dependency list from "dpkg -s pipelight-multi":
```

Depends: libc6 (>= 2.4), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.5), libx11-6, debconf (>= 0.5) | debconf-2.0, mesa-utils, ttf-mscorefonts-installer, wget, zenity | kde-baseapps-bin, zenity | qdbus, wine-compholio (>= 1.7.19-1~), bash (>= 4.0), unzip, cabextract, gnupg

```
Most of those are pretty vanilla except for the Microsoft fonts and cabextract.  The wine-compholio package is just a customized version of WINE with everything pipelight needs included in one easy-to-install object.

---

### Post by uRock on 2014-08-12
> **SeijiSensei said:**
> Well, I've been using that solution successfully for at least half-a-year now.  Why does it bother you if an application has a lot of dependencies?  Here's the dependency list from "dpkg -s pipelight-multi":
```

Depends: libc6 (>= 2.4), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.5), libx11-6, debconf (>= 0.5) | debconf-2.0, mesa-utils, ttf-mscorefonts-installer, wget, zenity | kde-baseapps-bin, zenity | qdbus, wine-compholio (>= 1.7.19-1~), bash (>= 4.0), unzip, cabextract, gnupg

```
Most of those are pretty vanilla except for the Microsoft fonts and cabextract.  The wine-compholio package is just a customized version of WINE with everything pipelight needs included in one easy-to-install object.
Your list looks a bit light.```
XXXXX:~$ sudo apt-get install pipelight
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-image-3.13.0-30-generic linux-image-extra-3.13.0-30-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  cabextract gcc-4.8-base:i386 gcc-4.9-base:i386 libasn1-8-heimdal:i386
  libasound2:i386 libasound2-plugins:i386 libasyncns0:i386
  libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386
  libc6:i386 libcapi20-3 libcapi20-3:i386 libcgmanager0:i386 libcomerr2:i386
  libcups2:i386 libdb5.3:i386 libdbus-1-3:i386 libdrm-intel1:i386
  libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libelf1:i386
  libexif12:i386 libexpat1:i386 libffi6:i386 libflac8:i386 libfontconfig1:i386
  libfreetype6:i386 libgcc1:i386 libgcrypt11:i386 libgd3:i386
  libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386
  libglu1-mesa:i386 libgnutls26:i386 libgpg-error0:i386 libgphoto2-6:i386
  libgphoto2-port10:i386 libgpm2:i386 libgsm1:i386 libgssapi-krb5-2:i386
  libgssapi3-heimdal:i386 libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386
  libheimntlm0-heimdal:i386 libhx509-5-heimdal:i386 libice6:i386
  libieee1284-3:i386 libjack-jackd2-0:i386 libjbig0:i386 libjpeg-turbo8:i386
  libjpeg8:i386 libjson-c2:i386 libk5crypto3:i386 libkeyutils1:i386
  libkrb5-26-heimdal:i386 libkrb5-3:i386 libkrb5support0:i386 liblcms2-2:i386
  libldap-2.4-2:i386 libllvm3.4:i386 libltdl7:i386 liblzma5:i386
  libmpg123-0:i386 libncurses5:i386 libnih-dbus1:i386 libnih1:i386 libodbc1
  libodbc1:i386 libogg0:i386 libopenal1:i386 libosmesa6 libosmesa6:i386
  libp11-kit0:i386 libpciaccess0:i386 libpng12-0:i386 libpulse0:i386
  libroken18-heimdal:i386 libsamplerate0:i386 libsane:i386 libsasl2-2:i386
  libsasl2-modules:i386 libsasl2-modules-db:i386 libsm6:i386 libsndfile1:i386
  libspeexdsp1:i386 libsqlite3-0:i386 libssl1.0.0:i386 libstdc++6:i386
  libtasn1-6:i386 libtiff5:i386 libtinfo5:i386 libtxc-dxtn-s2tc0:i386
  libudev1:i386 libusb-1.0-0:i386 libuuid1:i386 libv4l-0:i386
  libv4lconvert0:i386 libvorbis0a:i386 libvorbisenc2:i386 libvpx1:i386
  libwind0-heimdal:i386 libwrap0:i386 libx11-6:i386 libx11-xcb1:i386
  libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386
  libxcb-present0:i386 libxcb-sync1:i386 libxcb1:i386 libxcomposite1:i386
  libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386
  libxfixes3:i386 libxi6:i386 libxinerama1:i386 libxml2:i386 libxpm4:i386
  libxrandr2:i386 libxrender1:i386 libxshmfence1:i386 libxslt1.1:i386
  libxt6:i386 libxxf86vm1:i386 pipelight-multi ttf-mscorefonts-installer
  wine-compholio wine-compholio-amd64 wine-compholio-i386:i386 zlib1g:i386
Suggested packages:
  glibc-doc:i386 locales:i386 isdnutils-doc isdnutils-doc:i386 rng-tools:i386
  libgd-tools:i386 libglide3:i386 gnutls-bin:i386 gphoto2:i386 gtkam:i386
  gpm:i386 krb5-doc:i386 krb5-user:i386 jackd2:i386 liblcms2-utils:i386
  libmyodbc odbc-postgresql tdsodbc unixodbc-bin libmyodbc:i386
  odbc-postgresql:i386 tdsodbc:i386 unixodbc-bin:i386 libportaudio2:i386
  libroar-compat2:i386 pulseaudio:i386 hplip:i386 hpoj:i386
  libsane-extras:i386 libsasl2-modules-otp:i386 libsasl2-modules-ldap:i386
  libsasl2-modules-sql:i386 libsasl2-modules-gssapi-mit:i386
  libsasl2-modules-gssapi-heimdal:i386
Recommended packages:
  xml-core:i386
The following NEW packages will be installed:
  cabextract gcc-4.8-base:i386 gcc-4.9-base:i386 libasn1-8-heimdal:i386
  libasound2:i386 libasound2-plugins:i386 libasyncns0:i386
  libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386
  libc6:i386 libcapi20-3 libcapi20-3:i386 libcgmanager0:i386 libcomerr2:i386
  libcups2:i386 libdb5.3:i386 libdbus-1-3:i386 libdrm-intel1:i386
  libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libelf1:i386
  libexif12:i386 libexpat1:i386 libffi6:i386 libflac8:i386 libfontconfig1:i386
  libfreetype6:i386 libgcc1:i386 libgcrypt11:i386 libgd3:i386
  libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386
  libglu1-mesa:i386 libgnutls26:i386 libgpg-error0:i386 libgphoto2-6:i386
  libgphoto2-port10:i386 libgpm2:i386 libgsm1:i386 libgssapi-krb5-2:i386
  libgssapi3-heimdal:i386 libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386
  libheimntlm0-heimdal:i386 libhx509-5-heimdal:i386 libice6:i386
  libieee1284-3:i386 libjack-jackd2-0:i386 libjbig0:i386 libjpeg-turbo8:i386
  libjpeg8:i386 libjson-c2:i386 libk5crypto3:i386 libkeyutils1:i386
  libkrb5-26-heimdal:i386 libkrb5-3:i386 libkrb5support0:i386 liblcms2-2:i386
  libldap-2.4-2:i386 libllvm3.4:i386 libltdl7:i386 liblzma5:i386
  libmpg123-0:i386 libncurses5:i386 libnih-dbus1:i386 libnih1:i386 libodbc1
  libodbc1:i386 libogg0:i386 libopenal1:i386 libosmesa6 libosmesa6:i386
  libp11-kit0:i386 libpciaccess0:i386 libpng12-0:i386 libpulse0:i386
  libroken18-heimdal:i386 libsamplerate0:i386 libsane:i386 libsasl2-2:i386
  libsasl2-modules:i386 libsasl2-modules-db:i386 libsm6:i386 libsndfile1:i386
  libspeexdsp1:i386 libsqlite3-0:i386 libssl1.0.0:i386 libstdc++6:i386
  libtasn1-6:i386 libtiff5:i386 libtinfo5:i386 libtxc-dxtn-s2tc0:i386
  libudev1:i386 libusb-1.0-0:i386 libuuid1:i386 libv4l-0:i386
  libv4lconvert0:i386 libvorbis0a:i386 libvorbisenc2:i386 libvpx1:i386
  libwind0-heimdal:i386 libwrap0:i386 libx11-6:i386 libx11-xcb1:i386
  libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386
  libxcb-present0:i386 libxcb-sync1:i386 libxcb1:i386 libxcomposite1:i386
  libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386
  libxfixes3:i386 libxi6:i386 libxinerama1:i386 libxml2:i386 libxpm4:i386
  libxrandr2:i386 libxrender1:i386 libxshmfence1:i386 libxslt1.1:i386
  libxt6:i386 libxxf86vm1:i386 pipelight pipelight-multi
  ttf-mscorefonts-installer wine-compholio wine-compholio-amd64
  wine-compholio-i386:i386 zlib1g:i386
0 upgraded, 137 newly installed, 0 to remove and 0 not upgraded.
Need to get 72.2 MB of archives.
After this operation, 420 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.

```There's nothing really "wrong" about installing them. I have just seen too many workarounds that don't really work in Linux.
 
When I saw a workaround being linked on Facebook and people saying it worked without jumping through hoops, I figured I'd give it a try. 

When it actually worked, I decided to share the info.

---

### Post by mooreted on 2014-08-12
Followed the directions but it keeps asking me to install Silverlight. User agent is set to IE9. Maybe I'll try another UA.

---

### Post by mooreted on 2014-08-12
Nope, tried all the Windows ones. No go.

---

### Post by uRock on 2014-08-12
I had the same problem, I had to look in Unity for Chrome Beta. Installing the Beta doesn't remove the Chrome Stable.

---

### Post by mooreted on 2014-08-12
Ah ha! Needed custom string:

Mozilla/5.0 (Windows NT 6.3; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/38.0.2114.2 Safari/537.36

---

### Post by user1397 on 2014-08-12
> **SeijiSensei said:**
> You haven't looked hard enough.  There are lots of discussions about Netflix.  Search the forums for "pipelight" to see a bunch of them.
I guess I should've clarified, I haven't seen any netflix threads about this *latest* development, except for this one of course.

---

### Post by SeijiSensei on 2014-08-12
> **uRock said:**
> Your list looks a bit light.
I guess I already had all those i386 packages installed.  Maybe they came along with pipelight, or maybe they were installed for some other packages.  Someday we'll all be on the x64 platform, and we can leave all this duplication behind.  By then Netflix will be using some system [based on HTML5]("http://www.computerworld.com/s/article/9238421/Netflix_to_dump_Silverlight_Microsoft_s_stalled_technology"), and probably with a proprietary DRM layer that they'll never port to Linux.
> Park and Watson said Netflix would replace Silverlight on Windows and Mac desktops and notebooks with three HTML5 extensions -- Netflix collectively dubbed them "HTML5 Premium Video Extensions" -- to allow JavaScript to generate media streams, lock down the content with digital rights management (DRM) anti-piracy technology, and encrypt/decrypt the JavaScript-to-Netflix-server communications.

Netflix has already begun using two of the three extensions -- the exception is "WebCrypto," which handles JavaScript encryption -- in Google's Chrome OS on Samsung's Chromebook. Once WebCrypto is supported by the Chrome browser -- the foundation of Chrome OS -- Netflix will start testing the Silverlight substitute on Windows and OS X.
I notice that one operating system is glaringly absent from this discussion.

---

### Post by kostkon on 2014-08-12
> **SeijiSensei said:**
> I guess I already had all those i386 packages installed.  Maybe they came along with pipelight, or maybe they were installed for some other packages.  Someday we'll all be on the x64 platform, and we can leave all this duplication behind.  By then Netflix will be using some system [based on HTML5]("http://www.computerworld.com/s/article/9238421/Netflix_to_dump_Silverlight_Microsoft_s_stalled_technology"), and probably with a proprietary DRM layer that they'll never port to Linux.

I notice that one operating system is glaringly absent from this discussion.
??

But Chrome supports that ([EME]("http://en.wikipedia.org/wiki/Encrypted_Media_Extensions")) already on Linux, that's why it is working now and you don't need silverlight anymore. Actually, EME is a W3C standard.

---

### Post by mooreted on 2014-08-12
> **uRock said:**
> I had the same problem, I had to look in Unity for Chrome Beta. Installing the Beta doesn't remove the Chrome Stable.

Yeah, that perplexed me for a few minutes.

---

### Post by SeijiSensei on 2014-08-13
> **kostkon said:**
> But Chrome supports that ([EME]("http://en.wikipedia.org/wiki/Encrypted_Media_Extensions")) already on Linux, that's why it is working now and you don't need silverlight anymore. Actually, EME is a W3C standard.

I don't want to use Chrome.  I want to use Firefox.  Have a solution for that?

> **uRock said:**
> Your list looks a bit light.
**Update:**
I just installed wine on a machine that had no version of it before.  It brought in all those :i386 packages to support 32-bit Windows applications.  From the WINE FAQ:
> 
2.5. Is there a 64 bit Wine?

Yes. 64 bit Wine has been available on Linux since 1.2, and most major distros now package it for users. Normally, installation should be as simple as installing the Wine package for your distribution through your package manager. Check the Downloads page.

A couple of things to note:

    32 bit Wine runs on both 32-bit and 64-bit Linux/Unix installations. 16-bit and 32-bit Windows applications will run on it.

    64-bit Wine runs only on 64 bit installations, and at present only on Linux. **It requires the installation of 32 bit libraries in order to run 32 bit Windows applications.** Both 32-bit and 64-bit Windows applications (should) work with it; however, there are still many bugs. 

[emphasis mine]

Installing pipelight which depends on wine-compholio thus brings in all those i386 packages you saw.

---

### Post by sammiev on 2014-08-16
> **uRock said:**
> Thanks to the following link, I have Netflix working in Ubuntu. 

[http://www.omgubuntu.co.uk/2014/08/netflix-linux-html5-support-plugins](http://www.omgubuntu.co.uk/2014/08/netflix-linux-html5-support-plugins)

Thanks for the link and just today had time to try it.

Works great.

---

### Post by sffvba[e0rt on 2014-08-17
No advance in technology is going to help much if Netflix isn't yet available in the country you live in >.<

---

### Post by user1397 on 2014-08-17
> **not found said:**
> No advance in technology is going to help much if Netflix isn't yet available in the country you live in >.<
i thought people easily circumvented that by using proxies, or did i hear wrong.  i know my sister used our netflix account in england when she lived there without any problems, but i don't know how easy it is in england.

---

### Post by sffvba[e0rt on 2014-08-17
> **ubuntuman001 said:**
> i thought people easily circumvented that by using proxies, or did i hear wrong.  i know my sister used our netflix account in england when she lived there without any problems, but i don't know how easy it is in england.

Not sure how easy as as it typically only takes a week before a new work around gets "fixed".  Perhaps using a VPN but let us not go down that road (forum code of conduct and all :p)...

---

### Post by coffeecat on 2014-08-17
> **ubuntuman001 said:**
> i thought people easily circumvented that by using proxies, or did i hear wrong.  i know my sister used our netflix account in england when she lived there without any problems, but i don't know how easy it is in england.

Two points to make.

Your sister probably simply logged into her Netflix account while in the UK and used it. I'm almost certain that subscribers to Netflix can use it in any country in which Netflix is available, but they will find that the availability of content will vary from country to country.

Accessing content available in the US, for example, in another country where that content is not available would be a violation of [Netflix's Terms of Use]("https://www2.netflix.com/TermsOfUse"), and therefore we cannot allow support for how to do that on ubuntuforums.

> You may view a movie or TV show through the Netflix service only in geographic locations where we offer our service and have licensed such movie or TV show. The content that may be available to watch will vary by geographic location. Netflix will use technologies to verify your geographic location.

> The availability of movies & TV shows to watch will change from time to time, and from country to country. 

---

### Post by user1397 on 2014-08-23
> **coffeecat said:**
> Two points to make.

Your sister probably simply logged into her Netflix account while in the UK and used it. I'm almost certain that subscribers to Netflix can use it in any country in which Netflix is available, but they will find that the availability of content will vary from country to country.

Accessing content available in the US, for example, in another country where that content is not available would be a violation of [Netflix's Terms of Use]("https://www2.netflix.com/TermsOfUse"), and therefore we cannot allow support for how to do that on ubuntuforums.I see.  I thought that she being in England would simply mean that she could not use netflix at all, until she told me she was able to log in (and no, she didn't use anything like a proxy/vpn, she is not exactly tech savvy :)) But I guess that means that netflix works in england, just not in certain other countries.

---

### Post by sammiev on 2014-08-23
> **ubuntuman001 said:**
> I see.  I thought that she being in England would simply mean that she could not use netflix at all, until she told me she was able to log in (and no, she didn't use anything like a proxy/vpn, she is not exactly tech savvy :)) But I guess that means that netflix works in england, just not in certain other countries.

I have used a VPN for years and I do use Netflix. Netflix is some what different between Canada and the US without the VPN.

---

### Post by coffeecat on 2014-08-24
> **ubuntuman001 said:**
> I guess that means that netflix works in england, 

I guess that must be true, unless I'm hallucinating every time I settle down to watch a movie courtesy of my Netflix subscription.

---

### Post by user1397 on 2014-08-24
> **coffeecat said:**
> I guess that must be true, unless I'm hallucinating every time I settle down to watch a movie courtesy of my Netflix subscription.
;)

---

### Post by dekinstoke2 on 2014-09-17
I gave up trying to get pipelight to work and I just use a small Virtualbox VM running MicroXP for my Netflix use ....

---

### Post by user1397 on 2014-09-17
> **dekinstoke2 said:**
> I gave up trying to get pipelight to work and I just use a small Virtualbox VM running MicroXP for my Netflix use ....
Did you try the guide mentioned in this thread?  It doesn't use pipelight or wine anymore, it is native now...

---

### Post by ELD on 2014-09-17
Running perfectly well on the latest stable chrome for me with just the little user-agent switcher trick.

Using it to watch Firefly :D

---

### Post by Habitual on 2014-09-17
> **mooreted said:**
> Ah ha! Needed custom string:

Mozilla/5.0 (Windows NT 6.3; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/38.0.2114.2 Safari/537.36

I used
```
Mozilla/5.0 (Windows NT 6.3, Win64, x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/38.0.2114.2 Safari/537.36
```
on Google Chrome [COLOR=#303942][FONT=DejaVu Sans]Version 37.0.2062.120 (64-bit)[/FONT][/COLOR]

---

