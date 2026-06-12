---
title: "your opinions on FOSS Video editors?"
date: 2007-06-15
forum: The Cafe
---

### Post by Somenoob on 2007-06-15
**Kino** 
looks good but importing videos takes too long and sometimes the importing fails without any explanation.

**Avidemux**
Great for altering the video's brightness and things like that but there is no editing.

**Pitivi**
too simple, okay for editing but my vids often come flawed out.

**Diva**
The development has ceased(unfortunately) Judging from it's screenshots it looks pretty good. Doesn't have any packages just the source which is difficult to install.

Is there anything I'm missing or aren't there any good editors?

---

### Post by Gannin on 2007-06-15
There's also Cinelerra, which can be a bit of a mess, and I personally use Blender, because it can do video editing in addition to 3D modeling.

---

### Post by DC@DR on 2007-06-15
There's no REAL video editor out there for Linux users, unfortunately. I have tried them all, but feel really disappointed since they're not on par with commercial, Windows-only apps, to name just a few like: lack of features, unstable... That's sad but true :-(

---

### Post by Warpnow on 2007-06-15
Has avid or premiere been tried in wine?

---

### Post by reclusivemonkey on 2007-06-15
I've used Kino many times importing different formats and never had a problem.

---

### Post by TBOL3 on 2007-06-15
Blender actually has a video editor.  They're also working on a good sound editor, but for now, if you make a good sound in audacity, you can import it into blender.

---

### Post by Extreme Coder on 2007-06-15
I've been looking for a video editor as simple as Windows Movie Maker... Just something to cut or add clips, add simple animations like fading or a bit of music. Can't find anything like that in linux :/

---

### Post by igknighted on 2007-06-15
Cinellera is the way to go.  It can be a pita to install in ubuntu, but it is so much better than Kino et al that it is worth it.  If you use PCLOS/SAM Linux I know it is in the repo's, not sure what other distros have it.

---

### Post by %hMa@?b&lt;C on 2007-06-15
cinelerra is great! but the setbacks are that it is buggy and slow.  It is very powerful, but difficult to pick up.  For quick stuff, I use Kdenlive.  Kdenlive is very similar to Diva or Windows Movie Maker.   I highly suggest it.  THere may be a package on getdeb.

---

### Post by forrestcupp on 2007-06-15
> **jeffc313 said:**
> cinelerra is great! but the setbacks are that it is buggy and slow.  It is very powerful, but difficult to pick up.  For quick stuff, I use Kdenlive.  Kdenlive is very similar to Diva or Windows Movie Maker.   I highly suggest it.  THere may be a package on getdeb.

I agree.  Cinelerra is a little slow, and it has a few bugs (it's getting better, though), but it's the only way to go in the FOSS realm if you need features.  I am using the latest Cinelerra CVS and it's usability has come a long way in the past couple of years.  I used Vegas Video in Windows, and Cinelerra isn't nearly as easy.  But I'm picking it up without much problem.  It does have some advanced features like motion tracking that is a bear to learn.  But for most usual editing, it's not that hard to grasp.  I'm really liking it.

If you want to install Cinelerra CVS, it's as easy as adding a repo, then using Synaptic or apt-get.  Go [here](http://cvs.cinelerra.org/docs/wiki/doku.php?id=english_manual:cinelerra_cv_en_2#ubuntu) to find easy installation instructions for Ubuntu.

---

### Post by ArtInvent on 2007-06-19
Jahshaka 2.0 is coming along. It is quite an ambitious project and the latest gives you an inkling of how nice it could be when done. There is no render yet which is the biggest limitation. But it is usable. Something to watch because Cinelerra needs a great deal of work and seems to be at a standstill. 

LiVES latest build is also actually usable. It also has promise but doesn't seem on quite the level of Jahshaka at least at this point. 

I've tried and tried with Cinelerra and am pretty sick of it. Maybe it's okay for standard definition. Cinelerra is extremely picky about file formats it can import. It is true that it will accept almost any resolution of video like HDV, but I have a new dual core AMD with 2gb ram and it won't play back HD files at more than a few fps. Have you tried the titling function? Is that a joke. I hate to say it but even the least expensive Windows program like Ulead Video Studio 11 runs beautifully even on older hardware and make Cinelerra look stone age. I may have to end up buying Ulead because the demo is quite impressive even on my 4 year old laptop and works far better than Cinelerra on the new Ubuntu box. I think I can get it for about $30 bucks with buy.com rebates. Although I promised myself I was off the non-free software merry-go-round.

I use Blender for 3D (fantastic) but haven't really been able to use it for video editing. Files don't play back at anything approaching real time. If you can't watch what your editing, you can't really edit it. (Same applies to Cinelerra.)

---

### Post by ArtInvent on 2007-06-19
By the way, mencoder is not an editor, just a powerful command line video encoder. Part of the mplayer packages. All linux video folks should know about it. It's extremely flexible when you figure it out. Lots of good codecs and filters. The command line gets long and complicated with all the options and switches so you have to read up on how to use it and do some experimenting. A nice GUI would make it rock. 

I've been experimenting around with it to de-interlace and reverse pulldown HDV files from my new Canon HV20 camera (shoots in 1080-24p) and re-encode them to mpeg4 and mpeg2 and that's not an easy thing to do. mencoder works and it's free.

---

### Post by Polygon on 2007-06-19
i used avidemux for simple editing of videos (basically taking a video and snipping a part of out it, and then saving that as a new video)

i havent found any other programs to do just that, kino seems like it only works if you hook a video camera up to it, as it doesnt import any movie files.

---

### Post by eriqk on 2007-06-20
> **Polygon said:**
> kino seems like it only works if you hook a video camera up to it, as it doesnt import any movie files.

That's odd, I've managed to import all kinds of stuff as long as it's some kind of .avi. 
This is the version that comes with Dapper, though. Haven't used the one on Feisty yet.

I actually like Kino- it's extremely limited, but it does what it does pretty well.

Groet, Erik

---

### Post by forrestcupp on 2007-06-20
I just completed my first project with Cinelerra, and I have to say, I love it.  It is possible to do about anything you want with it.  The preview is a little slow, but I think it's a bug or memory leak or something.  When I restarted my computer, the preview was smooth again.  One thing I didn't like about it, though is that in the titler, the settings apply to everything.  You can't have different fonts, sizes, colors, etc.  Everything has to be the same.  But I guess that's what things like the Gimp are for.

Another thing I didn't like is that you can't render to an mpg file.  I had to render to quicktime and use mencoder to convert it.  Other than that, I like cinelerra as much as any NLE I've used, and I've used a lot.

By the way, I found a sweet front-end to mencoder called T@b Media Converter.  It's not in the repos, but you can get a 32-bit Ubuntu compiled binary [here](http://devel.zs4.org/tabencode_linux.html).  Just untar it to your home directory and run the binary.  You need to make sure to have mencoder and sox installed to use this.

---

### Post by reclusivemonkey on 2007-06-20
> **eriqk said:**
> That's odd, I've managed to import all kinds of stuff as long as it's some kind of .avi. 
This is the version that comes with Dapper, though. Haven't used the one on Feisty yet.

I actually like Kino- it's extremely limited, but it does what it does pretty well.

Groet, Erik

I had quite a bit of trouble importing different formats in Edgy, but then I had tinkered with my Edgy install quite a lot. However, it works great in Feisty.

---

### Post by kelvin spratt on 2007-06-20
i use Cinelerra all the time its excellent takes time to master, used with Devede,  makes good movies but no menu i don't find that a problem, quality is very good i don't get any complaints i use Nero 3 to burn to DVD-RW test burn to verbatim X16 never fails

---

### Post by UbuWu on 2007-06-20
**Kdenlive**
[Kdenlive]("http://kdenlive.org/") is the best I have found so far.

---

### Post by forrestcupp on 2007-06-21
> **UbuWu said:**
> **Kdenlive**
[Kdenlive]("http://kdenlive.org/") is the best I have found so far.

I just tried it out.  It's the best app I've seen for simple editing, way better than kino.  But it lacks a lot of features for more complex stuff.  Cinelerra's still the only FOSS option for that right now.

---

### Post by eriqk on 2007-06-22
> **forrestcupp said:**
> I just completed my first project with Cinelerra, and I have to say, I love it.  It is possible to do about anything you want with it.  

May I ask what your setup is, and how you got Cinelerra running?

Groet, Erik

---

### Post by jacob01 on 2007-07-08
theres also mainactor but it is a commercial video editor that costs 200 dollars

---

### Post by forrestcupp on 2007-07-08
> **eriqk said:**
> May I ask what your setup is, and how you got Cinelerra running?

Groet, Erik

Boy, I'm kind of late on this.  [Here](http://cv.cinelerra.org/getting_cinelerra.php#ubuntu) is the instructions for installing the CVS version in Ubuntu.  I use Feisty 32-bit.  I don't know about 64-bit; it looks like they only have an Edgy version of that available, but it might work.  If you follow their instructions, it's pretty easy.  It just takes a little time to figure out how to use it, but any program will have a learning curve, especially something as complex as a full-featured video editor.

---

### Post by %hMa@?b&lt;C on 2007-07-08
> **jacob01 said:**
> theres also mainactor but it is a commercial video editor that costs 200 dollars

I tried the demo (full version w/ a watermark) and was not so impressed.  I honestly thought that I seems to lack features that even kdenlive had.

---

