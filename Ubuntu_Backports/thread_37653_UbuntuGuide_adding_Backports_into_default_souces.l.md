---
title: "UbuntuGuide adding Backports into default souces.list"
date: 2005-05-28
forum: Ubuntu Backports
---

### Post by jiyuu0 on 2005-05-28
Have started removing Marillat from UbuntuGuide and puttin in Backports into the default sources.list

Downside:
-older version of Acroread
-missing Transcode

Any chance adding this 2 in? Am still testing the whole guide...

---

### Post by mrbass on 2005-05-29
ok now I'm seeing the bigger picture...hehe

---

### Post by jiyuu0 on 2005-05-29
[QUOTE=mrbass]ok now I'm seeing the bigger picture...hehe[/QUOTE]

wow... u are answering me in PM, Email, and 2 threads... hehe

btw, what mentioned above has already been done.

UbuntuGuide 3.00 is using Ubuntu + Backports
Marillat is only for Acroread + Transcode

---

### Post by jdong on 2005-05-29
Ooh, I like I like :) :)

Ok, few things:

1. I'll work on getting new acroread uploaded... it's a 70 meg pain to transport :)
2. transcode -- I'll start looking into that, too.


Can you pick a mirror to get Backports from? The fastest is

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main restricted universe multiverse

and so on. Refer users to [http://backports.ubuntuforums.org/url.php](http://backports.ubuntuforums.org/url.php) for picking other mirrors. :)

Thanks for your support.

---

### Post by jiyuu0 on 2005-05-29
[QUOTE=jdong]Ooh, I like I like :) :)

Ok, few things:

1. I'll work on getting new acroread uploaded... it's a 70 meg pain to transport :)
2. transcode -- I'll start looking into that, too.


Can you pick a mirror to get Backports from? The fastest is

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main restricted universe multiverse

and so on. Refer users to [http://backports.ubuntuforums.org/url.php](http://backports.ubuntuforums.org/url.php) for picking other mirrors. :)

Thanks for your support.[/QUOTE]

thanks :) you have a done a great job putting those packages in place

yes, have already changed the link to mirrormax

the day will come when ubuntu is free from using marillat and only use backports for extra stuff

---

### Post by jdong on 2005-05-31
I got both Transcode and Acrobat in Staging.

---

### Post by crvendramini on 2005-05-31
[QUOTE=jdong]I got both Transcode and Acrobat in Staging.[/QUOTE]

Thank you for Acrobat Reader...  \\:D/

---

### Post by jdong on 2005-05-31
Ok, Acrobat is ready to promote


What about transcode? I don't use it.

I'd like to promote both of these tomorrow.

---

### Post by jiyuu0 on 2005-05-31
[QUOTE=jdong]Ok, Acrobat is ready to promote


What about transcode? I don't use it.

I'd like to promote both of these tomorrow.[/QUOTE]


ok, currently out of broadband (on dialup). ill also test it in 2 days time. is mozilla-acroread in the backports too?

transcode is needed for dvdrip to work...

EDIT: Is it safe to include the staging into the sources.list?

---

### Post by poofyhairguy on 2005-05-31
[QUOTE=jiyuu0]Have started removing Marillat from UbuntuGuide and puttin in Backports into the default sources.list
[/QUOTE]

Thank you very much for this.

---

### Post by Michael R Head on 2005-06-01
[QUOTE=jiyuu0]Have started removing Marillat from UbuntuGuide and puttin in Backports into the default sources.list

Downside:
-older version of Acroread
-missing Transcode

Any chance adding this 2 in? Am still testing the whole guide...[/QUOTE]
 Many of the packages (w32codecs, sun-j2sdk, libdvdcss2) seem to have disappeared from hoary-extras. They appear to be there in the repository, but synaptic can't find them anymore.  for the moment, I'm using the (out of date) UMN mirror, since it still has these packages, but all the other mirrors are missing them (with newer Packages.gz files). hoary-extras can't replace marillat without some of the packages...

Since I had them already installed, they appear with the status "Installed (local or obsolete)." Also, wesnoth and mono are gone. Is this to be expected?

---

### Post by fng on 2005-06-01
[QUOTE=Michael R Head]Many of the packages (w32codecs, sun-j2sdk, libdvdcss2) seem to have disappeared from hoary-extras. They appear to be there in the repository, but synaptic can't find them anymore.  for the moment, I'm using the (out of date) UMN mirror, since it still has these packages, but all the other mirrors are missing them (with newer Packages.gz files). hoary-extras can't replace marillat without some of the packages...

Since I had them already installed, they appear with the status "Installed (local or obsolete)." Also, wesnoth and mono are gone. Is this to be expected?[/QUOTE]

There seems to be a problem with empty packages.gz 
More information here : [http://ubuntuforums.org/showthread.php?t=38572](http://ubuntuforums.org/showthread.php?t=38572)

---

### Post by jiyuu0 on 2005-06-02
UbuntuGuide 4.00

Marillat is now out of the picture... thanks to backports :)

---

### Post by ubuntu_demon on 2005-06-03
great work guys!!!

---

### Post by mpeters13 on 2005-06-16
Meh.. even w/ the backports, and follow the ubuntuguide... I'm still here 32 hours later with no working apt-gets.   Are the packages just no longer available?(w32codecs, gstreamer deb file, about a million other codecs, flashplayer ... the list goes on... even mp3 support.)  And none of the guides I follow for the source work either. I wish I knew what I was doing wrong. This is quite frustrating.

---

