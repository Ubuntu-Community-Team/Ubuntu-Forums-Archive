---
title: "Edirol UA-700"
date: 2011-07-26
forum: Ubuntu Studio
---

### Post by marseille on 2011-07-26
In the same vein as `_[JWD1973]("http://ubuntuforums.org/showthread.php?p=11086695#post11086695")_', I want to contribute something positive about my UbuntuStudio experience. 

Rarely have I said much in forum but I have been with UbuntuStudio since its debut OS -- my much-loved 7.04 -- and try to keep up (with reading) the Ubuntu Women's list. Prior to that, I was a 64Studio user but Ubuntu quickly changed my mind.

Recently, I picked up an _[Edirol UA-700]("http://www.soundonsound.com/sos/dec02/articles/edirol700.asp")_ on E-bay. I based my decision on a few things but I owe special thanks to this website, `_[LINUX STUDIO PRO COMPATIBLE AUDIO HARDWARE]("http://linuxstudiopro.com/")_', for narrowing down my choices to use with Linux.

```
$ cat /proc/asound/cards /proc/asound/modules
 0 [UA700          ]: USB-Audio - UA-700
                      EDIROL UA-700 at usb-0000:00:12.0-3, full speed
 1 [M1x1           ]: USB-Audio - MidiSport 1x1
                      M-Audio MidiSport 1x1 at usb-0000:00:12.1-1, full speed
 2 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe024000 irq 16
 0 snd_usb_audio
 1 snd_usb_audio
 2 snd_hda_intel

```

As you can see, the UA-700 uses the snd_usb_audio module. More on that at ALSA: [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Roland_Edirol](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Roland_Edirol)


Once I acquired my mixer, Ztomic was a very big help and I thank Ztomic very much for it. It just so happens that Ztomic is one of the very few people who have _[written]("http://ubuntuforums.org/showthread.php?t=932071")_ about the Edirol UA-700 hooked up to Ubuntu... which he did back in 2008.

Admittedly, I went through a very rough couple of days with the UA-700 (and have no idea what the future holds) but discovered that as soon as I upgraded my 10.04 LTS pre-empt kernel, I was no longer fighting with Jackd, could use `alsa' (not portaudio anymore) and was able to enjoy the *full plug-n-play action*, as well as the UA-700 advanced settings. In other words, the UA-700 ended up being the perfect choice for me because it's a no-brainer: just plug the darn thang in!

This [is my current] *pre-empt kernel* (which, *according to Debian*, is enjoyed for it's better security and data protection than the RT kernel has but is still spectacular where latency may be an issue...):

```
$ uname -a

2.6.32-33-preempt #70-Ubuntu SMP PREEMPT Thu Jul 7 23:43:37 UTC 2011 x86_64 GNU/Linux
```

For all the ``fighting'' I did with Jackd over the last few days (which is really a first for me), having the time to read up and study actually did me a favor since I picked up a few tricks.

I never bothered with the `arecord' utility before but now that I have, I know I'll use it again because it records such a clean signal from the UA-700 (with all applied effects) and I don't have to turn on jackd.

The quote you see below has been appropriately modified from ALSAs page: `_[Understanding the Edirol UA-25EX logic]("http://alsa.opensrc.org/Edirol_UA-25EX#Understanding_the_Edirol_UA-25EX_logic")_'.


> 

*Recording sound*

In this example, the UA-700 device is set to Advance ON and 96 Khz recording. REC button is pressed.

You can use arecord utility, which is part of Alsa package, to record any sound from the microphone:



```
$arecord -r 96000 -f cd -t wav -D plughw:UA700 foobar.wav
```

For a better understanding, try the same command in verbose mode:

```
$arecord -v -r 96000 -f cd -t wav -D plughw:UA700 foobar.wav
```


[http://alsa.opensrc.org/Edirol_UA-25EX#Understanding_the_Edirol_UA-25EX_logic](http://alsa.opensrc.org/Edirol_UA-25EX#Understanding_the_Edirol_UA-25EX_logic)

Another nifty trick I picked up was the ``speaker-test''. I found that losing sound wasn't always because I really `lost' any sound. Yes, there were times I had to:

> kill the existing server, with the command

```
$pulseaudio -k
```


... just to get my sound back on! But, there were many times when the sound was always there -- even though Jackd was broke and pulseaudio seemed like it, too-- and I could only tell I had sound with the ``speaker-test''.

```
$speaker-test -c2 -D plughw:SB -twav
```

more about the `speaker-test':
[http://drona.csa.iisc.ernet.in/~uday/alsamch.shtml](http://drona.csa.iisc.ernet.in/~uday/alsamch.shtml)
```
$man speaker-test
```


Last, but not least, I just want to thank Pablo once again for helping me out these past few days. He's been an angel! :guitar:

---

