---
title: "Audio priority not released when program closes"
date: 2013-05-03
forum: Ubuntu Studio
---

### Post by Sweetdaddydong on 2013-05-03
Ubuntu Studio 13.04
AMD Phenom 9950
Asus M3N72-D
8 GB RAM DDR2

I just installed Ubuntu Studio and when I use one of the Audio creation applications (ie, Ardour, LMMS, etc) and then exit afterwards then I have no audio for any other applications like when I want to listen to MP3's, watch videos, or browse the web with youtube. 

So far I have had to fully restart my system each time to get back the audio. Logging out just doesn't get the job done. 

How can I fix this issue, or work around the issue so I don't have to restart my system each time?

---

### Post by zequence on 2013-05-03
Which audio server were you using with those applications? 

jack is preferred with Ardour. You can control jack with the application qjackctl.

Also, please read [https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro](https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro), for an introduction on pro audio on Ubuntu (Studio).

---

### Post by Sweetdaddydong on 2013-05-03
> **zequence said:**
> Which audio server were you using with those applications? 

jack is preferred with Ardour. You can control jack with the application qjackctl.

Also, please read [https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro](https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro), for an introduction on pro audio on Ubuntu (Studio).

I was not using any audio server. I just opened the program and then closed it without doing anything special. I didn't receive any error messages or anything so I assumed everything was just fine. Should I have been using an audio server? and is that the cause of my issue?

I am really, really new to this stuff so thank you for the link I will check that out.

---

### Post by jejeman on 2013-05-03
If you used Ardour than you used JACK.
My guess is that JACK didn't quit after you closed Adrour, and thats why you don't have sound. You need to kill JACK.

You have to know that audio applications in ubuntu Studio are not casual. You need to know what is going on and how it works.

Next time just try
```
killall -9 jackd
```

---

### Post by Sweetdaddydong on 2013-05-05
> **jejeman said:**
> If you used Ardour than you used JACK.
My guess is that JACK didn't quit after you closed Adrour, and thats why you don't have sound. You need to kill JACK.

You have to know that audio applications in ubuntu Studio are not casual. You need to know what is going on and how it works.

Next time just try
```
killall -9 jackd
```

WOw, thanks a ton man that really worked. Sound started playing immediately.

---

