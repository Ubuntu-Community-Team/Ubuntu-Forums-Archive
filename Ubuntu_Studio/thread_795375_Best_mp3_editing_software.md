---
title: "Best mp3 editing software"
date: 2008-05-15
forum: Ubuntu Studio
---

### Post by VanEyck on 2008-05-15
Hi fellow penguins!

I have some very long mp3 audio files (some over 1hr long).  I would like to segment them into smaller files of shorter duration (without converting to ogg or other format).

What is the best program to use for this?

---

### Post by thorgal on 2008-05-15
it depends ...
you can always import your mp3 into audacity, split it into segments and export each segment separately into mp3 again. That's the easiest way I would know using a sound editor. But there could be more low level tools. I know how to merge files from a terminal just using the shell command 'cat' but that's not what you want ...

---

### Post by VanEyck on 2008-05-15
Thanks,

I've never really edited sound in a Linux environment before (having been cautioned to avoid AV editing).  Are their issues with Audacity that I should be aware of?  What is the general opinion of Audacity?

---

### Post by thorgal on 2008-05-15
to my mind, it is very neat for quick operations. You just need to get familiar with it at the beginning but it is rather straightforward. I don't know if they still have this policy about the mp3 format but they used to let the user switch on mp3 processing by picking a third party library (like liblame) due to legal issues. It's no big deal if you have lame already installed in your system. You just have to switch it on in the audacity preferences (if you still have this policy implemented).

Another program that works really nice for editing is Rezound. In both cases, I don't think you need the jackd audio server, they understand pure alsa outputting so if you have your soundcard working well with alsa, you should be fine. If you have no sound coming out of these apps, then you can still use them since they provide standard visual waveform editing.

---

### Post by kyozo on 2008-07-03
Hi, just saw this post. If you just want to split mp3 files into smaller segments, I think the easiest way is to use mp3splt, it's a shell tool, and it splits the mp3 files without reencoding them, so it is also very quick.

You can install it using synaptics or apt-get
```

sudo apt-get update
sudo apt-get install mp3splt

```

then if you want to split the file mymusic.mp3 into 5 minute segments and but them into the ./output directory you could use this command
```

mp3splt -f -t 5.0 mymusic.mp3 -d ./output

```
the -f option tells it to use "frame mode", which only works with mp3 files, but should split it better.
the -t option tells it to split into 5 minutes (format is minutes.seconds)
and the -d option tells it that the splitted files should go into the ./output folder

You can of course do all sort of shell scripting to automate this. Also explore mp3splt more, it can do lots of other things than just splitting by time.

Cheers

Kyozo

---

### Post by Bungo Pony on 2008-07-03
You can also use wavbreaker if you have the desire to convert them into .wav files first. I believe you can manually select the spots for splitting (good for music) and timed splits (good for speech)

There's nothing wrong with converting them to another format. Just batch convert before you go to bed or something and let it do its thing.

I do all my sound editing in .wav files. I usually only make MP3s when I have a 'final product' ready.

But there's nothing more accurate than splitting them manually.

---

### Post by Stochastic on 2008-07-03
Yes Kyozo's right, mp3split is a better tool to use if all you want to do is split a file, as audacity will de-encode, then re-encode your mp3 data, which will cause signal degredation.  It may take a touch of reading to get comfortable with a command line tool (try man mp3split for a techy explanation), and if you really need a gui interface, [http://mp3splt.sourceforge.net/mp3splt_page/home.php](http://mp3splt.sourceforge.net/mp3splt_page/home.php) mp3split has a gtk interface that has yet to make its way into ubuntu repositories (read: you'd need to compile it from source for the time being).

---

