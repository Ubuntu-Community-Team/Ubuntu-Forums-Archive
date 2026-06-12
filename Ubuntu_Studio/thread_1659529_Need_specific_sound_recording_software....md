---
title: "Need specific sound recording software..."
date: 2011-01-04
forum: Ubuntu Studio
---

### Post by prodotes on 2011-01-04
Hello ^^

well it's either a specific or a scripted one...
I need to have a pc up and runing 24/7 and a sound recording software that will record segments and save them... say from 7-22 and from 22-7 every day...

Anyone know a way or program that can do that? ^^

tyvm in advance :)

---

### Post by cchhrriiss121212 on 2011-01-04
[How about Cron?]("http://en.wikipedia.org/wiki/Cron")

---

### Post by prodotes on 2011-01-04
well... yea but obviously i need to tell cron to start something at 7 and 22 am and recorde an audio input... and stop the previous recording... that's the tricky part for a nubi like me ^^

---

### Post by cchhrriiss121212 on 2011-01-04
You could use [arecord]("http://alsa.opensrc.org/index.php/Arecord") to capture audio with gnome-schedule to set the times. If you only have one card (or you want to use the default card), you do not need to specify it when using arecord. If not, use arecord -l in a terminal to find out what device you want to use. Mine is hw:0 for example as it is the first and only card.

Using 7am to 10pm as an example:
arecord -f S32_LE -r 48000 -d 3240000 test

This command tells the computer to record in 32bit little endian at a rate of 48kHz for 15 hours (the duration is specified in seconds) with the default sound card. The WAV file is saved with the name test and will save to your home folder. 

Once you open gnome-schedule you can set the start time to 7 am and paste the above command in the "command" box.

I hope you have sufficient space, as WAV is uncompressed audio and 15 hours will be approaching 10GB.

---

### Post by Pablo_F on 2011-01-04
Hi, 

It is a bad idea to record as wav in your case, because of this:

[http://en.wikipedia.org/wiki/WAV#Limitations](http://en.wikipedia.org/wiki/WAV#Limitations)

For the man page, it seems that arecord cannot record to wav64

timemachine can record to wav64 but I don't know how to use it as a cron job in a script.

Neither do I know if mp3, ogg or flac can be used for very long recordings.

Ideas?

Cheers, Pablo

---

### Post by cchhrriiss121212 on 2011-01-04
^Good point Pablo. You could still use wav if you kept the quality low, or split the recording up into chunks. 5 sets of 3 hours should be safe by my calculations.

---

### Post by prodotes on 2011-01-05
so... i guess the "best bet" would be to do
arecord -f S32_LE -r 48000 -d 3605 test[hour]

where [hour] would be the time it records... so i would make 24 cron entries with test0,test1,test2... and so on...
and when i'm at work just use some sound editor to convert the test22-test7 and test7-test22 wavs into 2 mp3s...

any way to put the date or something into the file name so i can leave it running for a few days if need be tho?
or do i need to make 31*24 entries for every day of the month and make folders? :)

cheers for the help so far ^^

---

### Post by robert shearer on 2011-01-05
Audacity has a timer record function.
Audacity>Transport>Timer record.

---

### Post by AutoStatic on 2011-01-05
Yes, but iirc it can't do wav64.

Best,

Jeremy

---

### Post by robert shearer on 2011-01-05
> **AutoStatic said:**
> Yes, but iirc it can't do wav64.

Best,

Jeremy

Agreed,[http://en.wikipedia.org/wiki/Comparison_of_digital_audio_editors](http://en.wikipedia.org/wiki/Comparison_of_digital_audio_editors)

Though recordings could be made in multiple chunks with timings following on as needed ??

---

### Post by AutoStatic on 2011-01-05
That should be possible, never done it myself though. I know someone from the Dutch Ubuntu forums works with Audacity this way and files > 4 Gb.

---

### Post by prodotes on 2011-01-05
checked out audacity... sadly once you set 1 timer it just stands there and waits for it... while i need 7-22 and 22-7 segments all day, every day :)
so my best bet is still to use cron for 1 hour and 5 second segments and then combine them later... just need to figure out how to make it so 1 day doesn't overwrite the other :)

---

### Post by cchhrriiss121212 on 2011-01-05
> **prodotes said:**
> so... i guess the "best bet" would be to do
arecord -f S32_LE -r 48000 -d 3605 test[hour]

where [hour] would be the time it records... so i would make 24 cron entries with test0,test1,test2... and so on...
and when i'm at work just use some sound editor to convert the test22-test7 and test7-test22 wavs into 2 mp3s...
Yep, but one entry per hour is a bit much. The limit for WAV is 4GB and at these settings, one hour is only around 600MB (you could get that lower if you use 16bit instead of 32). Audacity could handle the editing. 

> 
any way to put the date or something into the file name so i can leave it running for a few days if need be tho?
or do i need to make 31*24 entries for every day of the month and make folders? :)
Have a go with something like this:
```
arecord -f S32_LE -r 48000 -d 3605 `date +"%d%B-%H:%M:%S"`
```
Or if using gnome schedule (as it does not like percentage signs):
```
arecord -f S32_LE -r 48000 -d 3605 `date +"\%d\%B-\%H:\%M:\%S"`
```

Which will give you this for a filename:
05January-12:59:01

If you want to change the naming, take a look [here]("http://www.computerhope.com/unix/udate.htm") for what each parameter does.

If you'd like to put these files in a certain folder, just add the path at the front of the name like this:
```
arecord -f S32_LE -r 48000 -d 3605 /home/chris/recordings/`date +"\%d\%B-\%H:\%M:\%S"`
```

---

