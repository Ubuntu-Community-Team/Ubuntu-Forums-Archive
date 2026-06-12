---
title: "Jack No Longer Sees Wineasio"
date: 2012-06-11
forum: Ubuntu Studio
---

### Post by Precipitous on 2012-06-11
I am running a fresh install of Ubuntu 12.04 with a combination of UbuntuStudio and KXStudio applications and settings installed (UbuntuStudio apps, settings and desktop, KXStudio builds of Jackd, QJackctl, plugins). My current version of Wine is 1.4 and my current version of Wineasio is 0.9.

Ever since moving to version 12.04 I am no longer able to get Jack to see any Wineasio apps or VSTs. In the past I have always been able to use [SAVIHost]("http://www.hermannseib.com/english/savihost.htm") to run Windows soft-synths, and Jack automatically picks them up...   I **really** need this capability back.

Since everything worked the way I need it to using older versions of Wine I tried building/installing a copy of version 1.3 from source.  Everything seemed to go OK, but Ubuntu did not see it, so when I tried to install the latest build of Wineasio it kept trying to install Wine 1.4. I tried to get around this by installing Wineasio 0.75 from a .deb I downloaded, but I was never able to get it to register when I ran **regsvr32 wineasio.dll**.

I finally ended up un-installing 1.3/0.75 and re-installed 1.4/0.9...    Running **regsvr32 wineasio.dll** was successful, but I am back to where I started. Can anyone please tell me how to get everything back in working order? Also what settings to use for the audio options in Winecfg as that they are very different from the way they used to be....  Thanks in advance!

---

### Post by sgx on 2012-06-12
wine now uses a registry entry to choose alsa,
instead of winecfg, what a blunder! But games
and office apps are their focus. But the Wiki page,
scroll down to Configuring Sound, for the steps.

[http://wiki.jswindle.com/index.php/Wine_Registry#Configuring_Sound](http://wiki.jswindle.com/index.php/Wine_Registry#Configuring_Sound)

Also, there may be a folder /usr/lib/i386-linux-gnu/wine
that someone copied wineasio.dll there, and regisered it again,
remedy such a problem.

KX has a forum at [www.linuxmusicians.com](www.linuxmusicians.com)
I think it is listed under a 'linux distributions' heading,
should be easy to find, and get info from the man, himself.
Cheers

also, installing a 1.2 or 1.3 wine from a deb, might be
better than compiling, just because there are so many details
easily overlooked in that process, with no guarantee that
details are readily apparent, or even known, either.

---

### Post by Precipitous on 2012-06-12
> **sgx said:**
> Also, there may be a folder /usr/lib/i386-linux-gnu/wine
that someone copied wineasio.dll there, and regisered it again,
remedy such a problem.
@sgx: Thank you for the wonderful information. I was not aware that Wine 1.4 used a registry entry to set ALSA...  I will be trying your suggestions when I get home from work today and will report back.

I am curious as to what you meant by the quote above. Are you saying that I should delete the wineasio.dll from  /usr/lib/i386-linux-gnu/wine/ or are you saying something different?

---

### Post by Precipitous on 2012-06-12
> **sgx said:**
> wine now uses a registry entry to choose alsa,
instead of winecfg, what a blunder! But games
and office apps are their focus. But the Wiki page,
scroll down to Configuring Sound, for the steps.

[http://wiki.jswindle.com/index.php/Wine_Registry#Configuring_Sound](http://wiki.jswindle.com/index.php/Wine_Registry#Configuring_Sound)



@sgx - Thank you for your help.  Running wine regedit and setting the Audio key to Alsa did the trick!

---

### Post by sgx on 2012-06-13
> **Precipitous said:**
> @sgx: Thank you for the wonderful information. I was not aware that Wine 1.4 used a registry entry to set ALSA...  I will be trying your suggestions when I get home from work today and will report back.

I am curious as to what you meant by the quote above. Are you saying that I should delete the wineasio.dll from  /usr/lib/i386-linux-gnu/wine/ or are you saying something different?
Hi, in that, I was suggesting that if there were by chance two wine
folders, to make sure both had the wineasio.dll.

Glad things are working!
Cheers

---

### Post by windeguy on 2012-07-26
> **sgx said:**
> wine now uses a registry entry to choose alsa,
instead of winecfg, what a blunder! But games
and office apps are their focus. But the Wiki page,
scroll down to Configuring Sound, for the steps.

[http://wiki.jswindle.com/index.php/Wine_Registry#Configuring_Sound](http://wiki.jswindle.com/index.php/Wine_Registry#Configuring_Sound)





Great find, however the link:

[http://wiki.jswindle.com/index.php/Wine_Registry#Configuring_Sound](http://wiki.jswindle.com/index.php/Wine_Registry#Configuring_Sound)

Is not working for me.  Does anyone have the instructions for how to edit the registry for Alsa support?

---

### Post by Precipitous on 2012-07-27
> **windeguy said:**
> Great find, however the link:

[http://wiki.jswindle.com/index.php/Wine_Registry#Configuring_Sound](http://wiki.jswindle.com/index.php/Wine_Registry#Configuring_Sound)

Is not working for me.  Does anyone have the instructions for how to edit the registry for Alsa support?
These are the steps I used to get WINE to use ALSA:

Open a terminal and type: wine regedit
Navigate to: HKEY_CURRENT_USER\Software\Wine\Drivers
Open the Audio key and type Alsa

Hope this helps!

---

### Post by windeguy on 2012-07-27
Thanks Precipitous!

Along with what you suggested I also needed to find where the  wineasio.dll.so was and then I copied it using **sudo /usr/lib/i386-linux-gnu/wine**  (That was suggested elsewhere and through trial and error I found I needed to it as well). 

Then I did a &#8220;**regsver32 wineasio.dll**&#8221; and wineasio is working!

I can now run Canatabile Lite and VSTHost in the Ubuntu 12.04 with Wine 1.4 and wineasio. That was a bit tricky to get working through the trial and error process.

---

### Post by NodeEndo on 2012-12-20
:KS
     For anyone still having trouble installing and configuring WineASIO 0.9.0 with Wine 1.5 on Ubuntu 12.10 (amd64), I've started a dedicated blog on blogger.com to host a complete tutorial that I've written on how to accomplish this. 
*Tell me what you think, feedback on my blog will be very much appreciated.
              -Enjoy!
[http://linuxmusiciansunite.blogspot.com/]("http://linuxmusiciansunite.blogspot.com/")

---

