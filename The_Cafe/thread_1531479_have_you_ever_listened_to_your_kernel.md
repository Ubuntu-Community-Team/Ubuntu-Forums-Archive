---
title: "have you ever listened to your kernel?"
date: 2010-07-15
forum: The Cafe
---

### Post by SIGTERMer on 2010-07-15
I'm not talking about logs here, I mean literally listening to your kernel. 
Ladies and gentlemen, if you may lend me your ears for a few moments for you are about to be enlightened with the most beautiful sound you'll hear:

[http://soundcloud.com/sigtermer/vmlinuz-2-6-32]("http://soundcloud.com/sigtermer/vmlinuz-2-6-32")
Sound Properties: 44100Hz/Stereo/16bps

This sound was produced by adding a wave header to the linux kernel that I'm currently using on my machine (vmlinuz-2.6.32-21-generic). The best part about it is that you can remove the first 44 bytes and you'll get a fully functional kernel image.

it, along with a bitmap image (pbm, and also reversible to a functional image), are tared in a package hosted here: [http://sites.google.com/site/sigtermer/miscellaneous/vmlinuz-2.6.32-21-fun.tar.gz?attredirects=0&d=1]("http://sites.google.com/site/sigtermer/miscellaneous/vmlinuz-2.6.32-21-fun.tar.gz?attredirects=0&d=1")

cheers :popcorn:

PS: I must warn you that seeing the kernel as an image might be too graphic for some.

---

### Post by earthpigg on 2010-07-15
everyone should turn their speakers down prior to pressing play if anyone is sleeping near you :D

downloading the picture now

edit: what is the stuff at the very beginning, and 90% towards the end?

---

### Post by Anxious Nut on 2010-07-15
The image is amazing, but i'd rather make it a wallpaper size! I'm one person who's ready to have it on his desktop!

sadly, teh sound was just like an old antenna TV! No special sounds!

---

### Post by Stancel on 2010-07-15
> **Anxious Nut said:**
> The image is amazing, but i'd rather make it a wallpaper size! I'm one person who's ready to have it on his desktop!

sadly, teh sound was just like an old antenna TV! No special sounds!

I don't see anything amazing about the image? Are we talking about the same thing? The sound sounds like white noise, the image is....grey.

---

### Post by 3rdalbum on 2010-07-15
You can also do something like:

```
cat <filename> > /dev/dsp
```

---

### Post by SIGTERMer on 2010-07-15
> what is the stuff at the very beginning, and 90% towards the end?
If your reffering to the image, it's a direct 1:1 bitmap of the kernel itself. every pixel represents one bit of the kernel (with 0 interprited as white and 1 as black). you'll have to reffer to the compiler's documentation to know why the image looks the way it does. and sorry if the noise woke up anyone :)

> i'd rather make it a wallpaper size
the original image (included in the tarball) is 2048 * 15773. just how large is your desktop?

> cat <filename> > /dev/dsp
not cross-platform  ;)

---

### Post by Stancel on 2010-07-15
oh I didn't realize you had to zoom in a lot to see it.
yeah, that's cool.

---

### Post by MaxIBoy on 2010-07-15
That is pretty awesome!

Another cool idea is some kind of waveform generator built into the kernel itself, which generates sound based on CPU load or something like that as a diagnostic.

---

### Post by Kdar on 2010-07-15
Beautiful :)

---

### Post by Austin25 on 2010-07-15
> **3rdalbum said:**
> You can also do something like:

```
cat <filename> > /dev/dsp
```
so would this be able to do what the C64 used to do with tapes?

---

### Post by KiwiNZ on 2010-07-15
One question ...why?

---

### Post by SIGTERMer on 2010-07-15
> **KiwiNZ said:**
> One question ...why?
why? the question you should be asking is why not?
It's common knowledge that if two linux fanatics come within speaking distance, illogical chaos would ensue :)

---

### Post by Directive 4 on 2010-07-15
> **Austin25 said:**
> so would this be able to do what the C64 used to do with tapes?


yesh!!

this is the future...

i can't wait, just play the white noise and get linuz

epic!:popcorn:

---

### Post by Timmer1240 on 2010-07-15
Boy that was a letdown I was expecting to hear some symphony or something good!

---

### Post by Legendary_Bibo on 2010-07-15
Would I be considered insane if I could see every bug and hole in the linux kernel by looking at it represented as an image?

---

### Post by Stancel on 2010-07-15
> **Legendary_Bibo said:**
> Would I be considered insane if I could see every bug and hole in the linux kernel by looking at it represented as an image?

Yes.:p

---

### Post by Superkoop on 2010-07-15
Just in case you guys didn't know... if you unplug the cable from a television, you will get almost identical results...

*Makes note not to ever watch movies with Kernal geeks, nor listen to their music.*

---

### Post by alexfish on 2010-07-15
you can get a better sound with a nutcracker and a bowl of walnuts

Whatever next 

NEXT

---

### Post by undecim on 2010-07-15
```
cat /bin/* | sudo tee /dev/dsp > /dev/null
```

---

### Post by chriswyatt on 2010-07-15
That's awesome! :D

---

### Post by chriswyatt on 2010-07-15
I managed to get that code to play a spring boing wav I had lying around (Uncompressed 8-bit PCM audio, Mono, 11025 Hz) but another wav which is supposed to be a woman's voice just sounded like white noise (Uncompressed 16-bit PCM audio, Mono, 16000 Hz).

Can anyone explain why this is?  I assume it's something to do with 8-bit and 16-bit.  Also the 'boing' played at about half speed, I assume if it was half the frequency it would've played at about the right speed.

---

### Post by cloyd on 2010-07-15
I opened it in lucid and it opened with archive manager. Where did it put everything?  Once I've seen it and heard it, I want to get rid of it. Where is it?

---

### Post by chriswyatt on 2010-07-15
> **cloyd said:**
> I opened it in lucid and it opened with archive manager. Where did it put everything?  Once I've seen it and heard it, I want to get rid of it. Where is it?

Open up System Monitor and look at your processes, it'll probably be called 'cat' or something.  Alternatively "killall cat" might get rid of it.  If all fails log out and back in again ;)

---

