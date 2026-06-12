---
title: "Encoding CD's"
date: 2012-04-23
forum: The Cafe
---

### Post by rmcellig on 2012-04-23
I have about 400 Audio CD's I need to encode. At the moment I am using iTunes on my iMac to rip the CD's to MP3 format. Is there anything in Linux that will allow me to do this? I tried Asunder but that is a dedicated ripping app. I was looking fo a music player like iTunes that allows you to encode CD's.

Regarding ripping apps, is there anything that might be better than asunder?

---

### Post by koleoptero on 2012-04-23
I haven't tried many, but I have used rhythmbox (which is default in 12.04) and it worked just fine. You can't get closer to itunes than that I believe.

---

### Post by rmcellig on 2012-04-23
Great. So I can encode CD's with Rhythmbox. I will give it a try.

---

### Post by chili555 on 2012-04-23
I like abcde. It's a command-line application. You specify your parameters (mp3, flac, etc.) in a .conf file and drop the CD in the tray. Invoke in a terminal:```
abcde
```That's all there is to it.

---

### Post by Bandit on 2012-04-23
> **rmcellig said:**
> I have about 400 Audio CD's I need to encode. At the moment I am using iTunes on my iMac to rip the CD's to MP3 format. Is there anything in Linux that will allow me to do this? I tried Asunder but that is a dedicated ripping app. I was looking fo a music player like iTunes that allows you to encode CD's.

Regarding ripping apps, is there anything that might be better than asunder?

GRIP.. Nothing beats this.. Nothing...
Make sure you install LAME and CDParanoia, think CDParanoia may be part of a tool package now. Not sure..

---

### Post by dniMretsaM on 2012-04-23
Rhythmbox can rip CD's if you install a plugin. Not sure what it's called. Search for it in Synaptic/USC.

---

### Post by Bandit on 2012-04-23
Sound Juicer is good if you like simple UI's.

---

### Post by rmcellig on 2012-04-23
What is GRIP and where can I download it from, same goes for abcde,

Thanks!

---

### Post by Bandit on 2012-04-23
> **rmcellig said:**
> What is GRIP and where can I download it from, same goes for abcde,

Thanks!

Should be in repos..

[http://sourceforge.net/projects/grip/](http://sourceforge.net/projects/grip/)

---

### Post by Steeperton on 2012-04-24
I believe that grip is no longer maintained (for a few years now).

abcde is the most powerful tool I've come across. See this site (by someone from this forum) for a good user guide:
[http://www.andrews-corner.org/abcde.html](http://www.andrews-corner.org/abcde.html)

---

### Post by 3rdalbum on 2012-04-24
GRIP wasn't that good anyway. It was quite slow because it ripped to WAV first, and then compressed the result afterwards, whereas the better programs will compress the data as it comes off the CD.

---

### Post by Bandit on 2012-04-24
> **3rdalbum said:**
> GRIP wasn't that good anyway. It was quite slow because it ripped to WAV first, and then compressed the result afterwards, whereas the better programs will compress the data as it comes off the CD.

Depends on how you look at that, with slower machines, you could rip disc left and right and then let grip finish encoding you MP3s. The other way it has to keep spinning your drive which wears it out over time.

But now modern PCs are fast enough to Rip/Encode on the fly without that hassle..

---

### Post by andrew.46 on 2012-05-01
> **Steeperton said:**
> I believe that grip is no longer maintained (for a few years now).

Mind you abcde has been a little quiet for some time as well :(.

---

### Post by Erik1984 on 2012-05-01
Like mentioned Rhythmbox has a built-in CD ripper but it stopped fetching album information after an update of the MusicBrainz API. Are those issues fixed in the version of Rhythmbox that comes with Precise?

---

### Post by ssam on 2012-05-01
soundjuicer has been fixed in 12.04 to use the new musicbrainz api.
[https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/797473](https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/797473)
i'd suspect that this means that rhythmbox is fixed too.

personally i tend to rip with sound juicer, and play with rhythmbox. it seemed harder to control options when ripping in rythmbox.

---

### Post by andrew.46 on 2012-06-04
> **andrew.46 said:**
> Mind you abcde has been a little quiet for some time as well :(.

Perhaps I should correct myself here, looks like some work underway:

[http://code.google.com/p/abcde/source/list](http://code.google.com/p/abcde/source/list)

and good to see r313, this is a patch I collected and sent in 3 years ago :).

---

