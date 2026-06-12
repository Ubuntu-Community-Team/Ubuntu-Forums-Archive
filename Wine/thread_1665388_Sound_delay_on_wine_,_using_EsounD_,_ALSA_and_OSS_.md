---
title: "Sound delay on wine , using EsounD , ALSA and OSS and all the others not working."
date: 2011-01-12
forum: Wine
---

### Post by SuperXDE on 2011-01-12
Hello,

I have a problem with Wine , I started playing Counter-Strike , but it seems that when I start shooting the bullets don't make the sound except 2~3 seconds later , I have searched it on the internet but ... nothing useful has been found.

Here are the options I have :
Audio set to EsounD ( ALSA , OSS , all the others aren't working they do not produce any sound )
And the acceleration is set to "Emulation" 

as for the Ubuntu drivers' , I have no idea what they are , but probably they are PulseAudio.

-_- it is so frustrating and I need help , I tried everything including setting the registry stuff "UseDirectHW to 1"

---

### Post by mIXpRo on 2011-01-12
try :
```

padsp "path/the game.exe"

```

if it didn't work could you show the output of the terminal ?

---

### Post by Soulcage on 2011-01-13
Alsa works fine for me on ubuntu 10.10 and oss doesn't exist on 10.10 fyi. Did you check the [http://appdb.winehq.org/]("http://appdb.winehq.org/")?

---

