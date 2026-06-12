---
title: "Itunes alternative"
date: 2015-07-06
forum: The Cafe
---

### Post by scriptkitten_ on 2015-07-06
Is there an alternative to itunes that can organize my music for me and get the album artwork?

---

### Post by kurja on 2015-07-07
...Rhythmox? Windows media player? :rolleyes:

Really there are countless alternatives for displaying your locally stored music files in an orderly fashion with album arts, do you have any specific requirements?

---

### Post by user1397 on 2015-07-07
[http://www.osalt.com/itunes](http://www.osalt.com/itunes)

---

### Post by scriptkitten_ on 2015-07-07
I have about 200 songs all in one folder is there one that could recognize the song and organize it for me. (without having to install wine)

---

### Post by monkeybrain20122 on 2015-07-08
> **scriptkitten_ said:**
> I have about 200 songs all in one folder is there one that could recognize the song and organize it for me. (without having to install wine)

Well that would depend  on where they come from. The file carries metadata that would enable it to be recognized if say you ripped it from a CD, but not so much if you downloaded from Youtube or recorded from the output of your sound card.

---

### Post by Kpenguin on 2015-07-08
My favorite has always been Winamp. The media library is the best of any media player/manager I've used. Unfortunately, it's been discontinued and is not available for Linux. You could run it using Wine though.

---

### Post by pauljwells on 2015-07-09
I find Clementine to be the best Linux music player. It has good organization and links to various internet sources. There is an Android remote control that works well too. In addition, if you install jackd and qjackqtl you can get bit-perfect output to either SPDIF optical or an offboard DAC via USB. When you do this you are getting the sound as good as the source files; if you use flac to rip your cds then you lose nothing. The downside of Clementine is that it uses a bunch of older gstreamer plugins that U14.04 doesn't use, but it doesn't break anything and the plugins themselves work perfectly well.

If you have the time to learn how to use it, MPD (more of a platform than an application) is the "true" audiophile Linux solution. I could never get my head around it!

On Windows, there is Foobar2000 (with the WASAPI plugin) which also gives you bit-perfect playback. It isn't FOSS, but it it free as in beer. The only competiton is JRiver, which has more audiophile features, but doesn't sound any better, is a hideous mess of Java horrors and it costs $$$

---

### Post by shantiq on 2015-07-15
well   ....    i never knew this existed for a long time then found it  >>>[ aTunes]("http://www.atunes.org/")

does all that iTunes does but does not sync devices if I remember well  ....    actually it does but i do not know how well with ipod since i do not have one to try it on ..   tried it on a "normal"  mp3 player and fine  ...    so maybe someone could try and report ....
PS    on my machine it always takes a minute to load up but then is ok   AND sound is excellent as it uses mplayer

=====

To install      one command at a time in Terminal

```
sudo add-apt-repository ppa:noobslab/apps         >>> then hit enter
sudo apt-get update && sudo apt-get install atunes
#and if it tells you you have not got java6-runtime#
sudo apt-get -f install
```


**ALSO   **if you want REALLY good kit   **Clementine [**do all [these things]("http://ubuntuforums.org/showthread.php?t=2257567&p=13192069#post13192069") for great sound**] or Foobar** under Wine which works so well ...  but i would try aTunes too  ..   once understood  it is cool too

see  >>>    [[IMG]http://s20.postimg.org/vc96brcm1/atunes.jpg[/IMG]]("http://postimg.org/image/vc96brcm1/")

---

### Post by scriptkitten_ on 2015-07-19
Banshee gtkpod and rymthbox can all supposivly sync music to an I device so I don't think that'll be a problem I'll check out stunts thnx

---

### Post by shantiq on 2015-07-19
> does all that iTunes does but does not sync devices if I remember well   ....    actually it does but i do not know how well with ipod since i do  not have one to try it on ..   tried it on a "normal"  mp3 player and fine  ...    so maybe someone could try and report ....

Any of you got one of those to test? ... and report ...

---

### Post by shantiq on 2015-07-20
> **pauljwells said:**
> 

If you have the time to learn how to use it, MPD (more of a platform than an application) is the "true" audiophile Linux solution. I could never get my head around it!

Had a look and one of them is really quite manageable and really thorough in [what it offers]("http://ubuntuforums.org/showthread.php?t=2287569&p=13324508#post13324508")


[[IMG]http://s20.postimg.org/n8jfpzjq1/image.png[/IMG]]("http://postimg.org/image/n8jfpzjq1/")    click on the I icon and all this shows up     [[IMG]http://s20.postimg.org/erjxf2f15/image.png[/IMG]]("http://postimg.org/image/erjxf2f15/")

---

