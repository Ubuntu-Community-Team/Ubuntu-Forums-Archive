---
title: "Ripping Audio Cd's"
date: 2009-03-07
forum: The Cafe
---

### Post by YoungQuiz on 2009-03-07
just wondering what you guy used?

and what do you think works the best for simplicity and usability

im looking for new programs to try so any input is good input:D

---

### Post by bluelamp999 on 2009-03-07
Personally, I find GRIP pretty good.

Like any new (Linux) app there's a small bit of a learning curve but the end results are good rips (it uses LAME to encode and cdparanoia to rip).

Good luck

---

### Post by Hallvor on 2009-03-07
K3b does the job.

---

### Post by YoungQuiz on 2009-03-07
> **bluelamp999 said:**
> Personally, I find GRIP pretty good.

Like any new (Linux) app there's a small bit of a learning curve but the end results are good rips (it uses LAME to encode and cdparanoia to rip).

Good luck

i just dl that lol its a bit confusing,but imma play around wit this to see if i can work with this.

thanks

---

### Post by YoungQuiz on 2009-03-07
> **Hallvor said:**
> K3b does the job.

will look into this now as well

thanks

---

### Post by jocheem67 on 2009-03-07
ABCDE is great, it's commandline but don't let that scare one off...
With conf-files, very much downloadable, it's a powerful ripper/encoder....;)

---

### Post by Daisuke_Aramaki on 2009-03-07
cdparanoia does it for me!

---

### Post by YoungQuiz on 2009-03-07
also something that will alow me to rip the cd into mp3 format

---

### Post by YoungQuiz on 2009-03-07
> **jocheem67 said:**
> ABCDE is great, it's commandline but don't let that scare one off...
With conf-files, very much downloadable, it's a powerful ripper/encoder....;)

alright,gonna check this out too!

---

### Post by YoungQuiz on 2009-03-07
> **Daisuke_Aramaki said:**
> cdparanoia does it for me!

i think i've seen this before,not sure

i gotta check in on this to

thanks

---

### Post by Skripka on 2009-03-07
> **Hallvor said:**
> K3b does the job.

Bingo...although it is ridiculous that I need a seperate utility to rip and playback CD audio...since the Amarok devs felt CD audio ripping and playback was unnecessary in Amarok2.

---

### Post by cmay on 2009-03-07
i use sound-juicer to rip cd. 
iriverter and acidrip to rip dvd. 
i found those programs to be most stable and easy to use.

---

### Post by gnomeuser on 2009-03-07
I use Banshee, then my files are ripped in my format of choice and added directly into my music library where I care about interacting with it. I can even set it up so that when a CD is inserted, it automatically gets ripped if it is known by musicbrainz and then the cd pops out. That is the exact level of interaction I desire with physical media.

---

### Post by bapoumba on 2009-03-07
sound-juicer, the default gnome ripper.

---

### Post by YoungQuiz on 2009-03-07
> **Skripka said:**
> Bingo...although it is ridiculous that I need a seperate utility to rip and playback CD audio...since the Amarok devs felt CD audio ripping and playback was unnecessary in Amarok2.

yeah i think i need a niiice all in one player

---

### Post by RiceMonster on 2009-03-07
I use Asunder. It's really simple, and it's never given me any problems like a lot of other's have.

---

### Post by rotwang888 on 2009-03-07
Rubyripper.  Closest thing to EAC in Linux.  And it's very handy if you need to encode to more than one format at a time (mp3/ogg, flac/ogg, whatever)

---

### Post by hellion0 on 2009-03-07
I use cdparanoia.

---

### Post by Yashiro on 2009-03-07
Simplest, Sound Juicer.
Best, Grip.

---

### Post by wolfen69 on 2009-03-07
ripperx

---

### Post by Dr Small on 2009-03-07
> **RiceMonster said:**
> I use Asunder. It's really simple, and it's never given me any problems like a lot of other's have.
+1. I've been using asunder for awhile and never had a problem out of it.

---

### Post by ghindo on 2009-03-07
> **rotwang888 said:**
> Rubyripper.  Closest thing to EAC in Linux.  And it's very handy if you need to encode to more than one format at a time (mp3/ogg, flac/ogg, whatever)I'm glad somebody mentioned it :)  I don't think I can recommend Rubyripper highly enough.  Check out the link in my signature for more details.

---

### Post by FuturePilot on 2009-03-07
I use Grip because it uses Cdparanoia which is excellent at correcting errors caused by scratches and what not. It's also multi threaded so the encoding can take advantage of multi-core CPUs.

---

### Post by Naiki Muliaina on 2009-03-07
Sound Juicer all the way for me ^^

---

### Post by jocheem67 on 2009-03-07
Is it true that we all forget rhythmbox now?

Shame on us.:lolflag:

---

### Post by Polygon on 2009-03-07
i just use sound juicer, but ive noticed that on my cowon music player, the artist name appears on it as ORT=<artist name>...im not sure if its an issue with sound juicer or my cowon player, but its kinda annoying.

---

### Post by benerivo on 2009-03-07
ripperx

---

### Post by jocheem67 on 2009-03-08
In fact there's not so much wrong with rhythmbox, as long as you don't use VBR when encoding to mp3.....there used to be something wrong with the gstreamer pipeline...there are certainly some old threads around.

> audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=320 ! id3v2mux

This is a good working line....

By the way, my favourite organizer/player is foobar2000. It runs well under wine, encoding is very decent....one can even use alternative encoders, like the optimized oggenc's from aoTuV....
The best on the block is the tagging, moving and renaming of files within foobar...
Pity it's not being ported.

---

### Post by Yashiro on 2009-03-08
The problem with sound juicer is lack of configuration and the tagging is broken. Tags are wrong and sometimes even non existent.

If you *must* have specific encoding and fully correct tags you want something like Grip, Abcde(no gui) or Rubyripper.

---

