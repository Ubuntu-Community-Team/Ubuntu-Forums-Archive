---
title: "Advanced media converter w/ gui?"
date: 2009-05-03
forum: The Cafe
---

### Post by dragos240 on 2009-05-03
Hello,

I need to convert a file with some specific requirments such as, bitrate, framerate, size, audio codec, video codec, number of channels and sample rate. Is there a nice program for linux that would be good for this, and perhaps a gui forend for it?

---

### Post by gnomeuser on 2009-05-03
Arista or Transmaggedon maybe?

---

### Post by dragos240 on 2009-05-03
> **gnomeuser said:**
> Arista or Transmaggedon maybe?

Thank you on your quick responce, I did not find either in the main ubuntu repositories, so I found a PPA for arista. Thank you!

---

### Post by dragos240 on 2009-05-03
Nope sorry, arista is very limited, and I couldn't find anything on google about the second one. Misspelling?

---

### Post by CraigPaleo on 2009-05-03
How about Winff?

---

### Post by kevin11951 on 2009-05-03
> **CraigPaleo said:**
> How about Winff?

+100 for winff!

---

### Post by dragos240 on 2009-05-03
I'll try it.

---

### Post by gnomeuser on 2009-05-03
> **dragos240 said:**
> Thank you on your quick responce, I did not find either in the main ubuntu repositories, so I found a PPA for arista. Thank you!

[http://www.linuxrising.org/transmageddon/](http://www.linuxrising.org/transmageddon/)

But I think it might to "basic" for your needs as well.

---

### Post by unoodles on 2009-05-03
Handbrake is really good.

---

### Post by Paqman on 2009-05-03
> **unoodles said:**
> Handbrake is really good.

+1

It's multithreaded, and they have .debs for 64-bit so it's seriously fast. Re-encoding video and the like is where 64-bit multi-core machines really shine.

---

### Post by .Maleficus. on 2009-05-03
MEncoder maybe?  There are a bunch of GUIs for it, but having never used it I'm not sure of its capabilities or features.

---

### Post by dmn_clown on 2009-05-03
> **dragos240 said:**
> Hello,

I need to convert a file with some specific requirments such as, bitrate, framerate, size, audio codec, video codec, number of channels and sample rate. Is there a nice program for linux that would be good for this, and perhaps a gui forend for it?

ffmpeg can do this, but is CLI only.  Blender's sequencer can act as a semi-nice front end to ffmpeg so it should cover your requirements, its documentation starts here:  [http://wiki.blender.org/index.php/Doc:Manual/Sequencer](http://wiki.blender.org/index.php/Doc:Manual/Sequencer)

---

### Post by dragos240 on 2009-05-03
Okay, I've installed WinFF, although, there are issues. It's missing libxvid and msmpeg4. They seem to be libraries to encode videos. Alas, I do not know where to find them.

---

### Post by init1 on 2009-05-03
> **dragos240 said:**
> Okay, I've installed WinFF, although, there are issues. It's missing libxvid and msmpeg4. They seem to be libraries to encode videos. Alas, I do not know where to find them.
I think Medibuntu might help. 
[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by CraigPaleo on 2009-05-03
> **dragos240 said:**
> Okay, I've installed WinFF, although, there are issues. It's missing libxvid and msmpeg4. They seem to be libraries to encode videos. Alas, I do not know where to find them.
Do you have w32codecs and ubuntu-restricted-extras installed? If not, what Init1 posted should help.

---

### Post by dragos240 on 2009-05-03
> **init1 said:**
> I think Medibuntu might help. 
[http://www.medibuntu.org/](http://www.medibuntu.org/)

That fixed it ^_^

---

### Post by reprobus on 2009-05-03
I use handbrake, it is definitely the best.

[http://handbrake.fr/](http://handbrake.fr/)

---

### Post by dragos240 on 2009-05-03
I'm back with the results, they look VERY good, except the codec differentiation. How can I change the codec? I have posted an image of the comparison between a sansa fuze compatible video file, and the one I want on there:

---

### Post by fdrake on 2009-05-03
i don't know of a gui-application that does that. but ffmpeg is great as a terminal application . u practically have full control over the conversion.

can you be a little more spec of what kind of file are u trying to convert? and into what format( fram/sec, bitr, ect..) ? In this way someone can give u the right terminal options to attach to the ffmpeg .

---

### Post by Yannick Le Saint kyncani on 2009-05-03
There is also avidemux that you might want to try.

---

### Post by dragos240 on 2009-05-03
I need to now change the codec from XVID mpeg4 to divx mpeg4 version 5. How can I do this?

---

### Post by dragos240 on 2009-05-03
Bump.

---

### Post by CraigPaleo on 2009-05-03
Oops

---

### Post by dragos240 on 2009-05-03
Huh?

---

### Post by CraigPaleo on 2009-05-03
> **dragos240 said:**
> Huh?

I made a mistake and couldn't delete it.

---

### Post by dragos240 on 2009-05-03
Then why post again?

---

### Post by forrestcupp on 2009-05-03
> **dragos240 said:**
> Bump.

You can't bump after only 17 minutes.

Have you ever checked out [t@b Media Converter](http://www.thugsatbay.com/tab/?q=tab-video-converter-encoder)?  It's a graphical front end for mencoder and sox.

It's probably not what you're looking for, though.

---

### Post by CraigPaleo on 2009-05-03
> **dragos240 said:**
> Then why post again?
Because you said, "huh?"

---

### Post by forrestcupp on 2009-05-03
> **CraigPaleo said:**
> Because you said, "huh?"

That was just a clever way of bumping without appearing to be bumping. :)

---

### Post by fdrake on 2009-05-03
u might try this and let as know.

```
ffmpeg -i input_file -f avi -vcodec mpeg4 -b 800 -g 300 -bf 2 -acodec libmp3lame -ab 128 -vtag divx  output_file

```

it depends also from the qaulity of your source file . if you have an higher resolution or bitrade u might want to change this values too.

---

### Post by mips on 2009-05-04
ZevenOS (based on Ubuntu) has a very nice looking media converter application.

[http://www.zevenos.com/about/encode](http://www.zevenos.com/about/encode)

[IMG]http://www.zevenos.de/wp-content/uploads/2009/01/super-encode.png[/IMG]

---

### Post by forrestcupp on 2009-05-04
> **mips said:**
> ZevenOS (based on Ubuntu) has a very nice looking media converter application.

[http://www.zevenos.com/about/encode](http://www.zevenos.com/about/encode)


Wow.  That looks pretty awesome.

---

### Post by mips on 2009-05-04
> **forrestcupp said:**
> Wow.  That looks pretty awesome.

That's what I though the first time I saw it. It looks so easy to use without being featureless.

Hence it stuck in my mind.

It should be able to run in Ubuntu I recon for all the Ubuntu users out there, just need to find the package.

Edit:
People might want to browse the repos for this,
```
deb http://www.zevenos.com/packages/ ./
deb-src http://www.zevenos.com/packages/ ./
```

I got the above from the ZevenOS forum which I have not verified.

---

### Post by CraigPaleo on 2009-05-04
> **forrestcupp said:**
> wow.  That looks pretty awesome.

+1

---

### Post by Polygon on 2009-05-05
that looks nice! avidemux has some weird stuttering problem with any videos that i encode from my digital camera....so i'm looking for alternatives.

---

### Post by llelectronics on 2009-05-07
The Encode app aswell as the ZevenOS repo should work with Ubuntu 8.10 (Intrepid Ibex). 
Ubuntu 9.04 might not work fully.

---

