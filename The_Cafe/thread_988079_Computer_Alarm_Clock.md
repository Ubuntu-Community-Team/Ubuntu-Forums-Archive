---
title: "Computer Alarm Clock"
date: 2008-11-20
forum: The Cafe
---

### Post by Ponomous on 2008-11-20
So I keep seeing this in movies and im sure its possible but im just wondering if anyone has run into a program that does this or a few that do similar things.

I want to make my computer an alarm clock, ok easy, seen some programs,but i also want it to have a wake up message with weather notifications.  so when the alarm went off it would have the music i want playing and then say "Good morning,  The current time is 6:30 it is 70 degrees out, you have 20 unread messages" or something like that.

I think it will come down to mostly just recording the different numbers for the morning message but before i start a project like this Has anyone seen anything like this?

---

### Post by lukjad on 2008-11-20
Ohh! I want that. Subscribing to this thread. ;)

---

### Post by eternalnewbee on 2008-11-20
> Ohh! I want that. Subscribing to this thread.
Count me in, too.
EDIT: There is KAlarm in KDE.

---

### Post by rolando2424 on 2008-11-20
I have a simple bash script that is ran by a crontab job every morning to wake me up.

It calls the "beep" command, mostly because if I leave my columns (? I don't know if that's the correct term, I mean the things where the sound comes out) turned on for the night, they make a low background noise and I can't sleep.

To make the voices, you can use festival (I believe there are a few tutorials on that in this forum). You can try this to get you started:

```

echo "Today is thursday" | festival --tts

```

I could probably do something like this, (it would be a fun side-project), but I have two tests next week, and I should probably study for them :P

---

### Post by Ponomous on 2008-11-20
Cool idea on festival, ill check that out.

---

### Post by rolando2424 on 2008-11-20
By the way, you could tell me a page to see the weather and what is the email you use (gmail, hotmail, etc.)

edit:

Otherwise, the script will turn into a very tiny
```

echo "Today is $(date '+%A'). The time is $(date '+%-H') and $(date '+%-M')" | festival --tts;

```

This says something like "Today is Thursday. The time is 23 and 16."

---

### Post by elmer_42 on 2008-11-20
Sleep.FM offers a browser-based wake-up you can set for multiple alarms, including a feature to wake up to the current time, date, and weather.

---

### Post by voteforpedro36 on 2008-11-20
Write a script to do it, use cron to execute the script when you want to wake up (I have a cronjob set to play music at 6:30 Monday through Friday).

---

### Post by barbedsaber on 2008-11-20
I want an alarm, that plays music really loudly for wakeing up, but when you acknowledge it, it reduces the volume to listening volume, so you can start the day with some tunes.
after the first song, it would give temperature, outside windspeed, and humidity (Take THAT barometric pressure, noone likes you) and if it is overcast or not, and then actually say, shorts + longsleeve shirt. :)
then, go onto the next song, until its time to leave for school.
I can't write scripts to save my life, but a kid can dream.

---

### Post by damis648 on 2008-11-20
> **lukjad007 said:**
> ohh! I want that. Subscribing to this thread. ;)

+1

---

### Post by damis648 on 2008-11-20
> **rolando2424 said:**
> By the way, you could tell me a page to see the weather and what is the email you use (gmail, hotmail, etc.)

edit:

Otherwise, the script will turn into a very tiny
```

echo "Today is $(date '+%A'). The time is $(date '+%-H') and $(date '+%-M')" | festival --tts;

```

This says something like "Today is Thursday. The time is 23 and 16."

You can use weather-utils for the weather. It is a cli weather utility, you just need to know your METAR id for your city. Here is a slight guide:
[http://www.weather-watch.com/smf/index.php/topic,7688.0.html](http://www.weather-watch.com/smf/index.php/topic,7688.0.html)
What you need to know it just use the letter before the X's and your city ID, I am in Detroit so I use KDTW. Here is the directory for all cities so you can view the file and cuztomize the script: [http://weather.noaa.gov/pub/data/observations/metar/decoded/](http://weather.noaa.gov/pub/data/observations/metar/decoded/)
Anyway, check it out (after installing weather-utils)

```
echo "Good Morning my friend. Today is $(date '+%A'). The time is $(date '+%-H') and $(date '+%-M')" | festival --tts;
weather-util -i KDTW | grep Sky | festival --tts;
weather-util -i KDTW | grep Temperature | festival --tts;
weather-util -i KDTW | grep Weather | festival --tts
weather-util -i KDTW | grep Humidity | festival --tts;
```

Save that as a bash script and run it. It works quite well, I am quite pround of myself. The only thing is, is that it has to download the information each time... I am sure that can be solved and it could be alot more elegant, but this is pretty good for now... what do you think?:popcorn:

EDIT: Also, the "Temperature" line comes out wrong on festival because it reads the line like "Temperature: 29.5 F 1.5 C" so it sounds wierd... if that could be fixed, it would be practically perfect!

---

### Post by damis648 on 2008-11-20
I made one more modification for music playing. With this script, music will play for 60 seconds in Rhythmbox (the music in the play queue) and then reduce the volume to half and speak good morning, and tell you the time, date, and weather. Now, until I can get festival to use pulseaudio (maybe using padsp?) the music and festival cannot play at the same time. Anyway, if you can get it to work, post your festival config and the script if you modified it. Good luck!

Here it is:
```
rhythmbox-client --set-volume 1.0
rhythmbox-client --play
echo "Good Morning my friend. Today is $(date '+%A'). The time is $(date '+%-H') and $(date '+%-M')" | festival --tts;
sleep 60; rhythmbox-client --set-volume .5
weather-util -i KDTW | grep Sky | festival --tts;
weather-util -i KDTW | grep Temperature | festival --tts;
weather-util -i KDTW | grep Weather | festival --tts
weather-util -i KDTW | grep Humidity | festival --tts;
```

EDIT: fixed.

---

### Post by zmjjmz on 2008-11-20
Although this is a very crude alarm clock, I set up my Thinkpad to play Rammstein very loudly at a certain time.
```
mpg123 Moskow.mp3 | at 6:30
``` or something like that.

---

### Post by damis648 on 2008-11-21
Well I have tinkered a bit more and got festival using ESD. Everything works, but there is still a small issue. Now, when festival reads what I echo, it will sometimes read words running together. What I mean is two words are read at the same time by festival. It is kind-if wierd, but happens consistently at the same spot in the line. Any ideas? I will tinker some more until I can find something that works.

The Script:

```
rhythmbox-client --set-volume 1.0
rhythmbox-client --play
sleep 5; rhythmbox-client --set-volume .1
echo "Good Morning my friend. Today is $(date '+%A'), The time is $(date '+%-H') and $(date '+%-M')," | festival --tts;
weather-util -i KDTW | grep Sky | festival --tts;
weather-util -i KDTW | grep Temperature | festival --tts;
weather-util -i KDTW | grep Weather | festival --tts
weather-util -i KDTW | grep Humidity | festival --tts;
rhythmbox-client --set-volume 1.0
```

And my /etc/festival.scm (course ;; are comments):

```
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;
;;;; setup audio output
;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

;;;; defaults to oss output

;;;; use esd to output sound
(Parameter.set 'Audio_Command "esdplay $FILE") 
(Parameter.set 'Audio_Method 'Audio_Command)
(Parameter.set 'Audio_Required_Format 'snd)

;;;; use alsa to output sound
;;(Parameter.set 'Audio_Command "aplay -D plug:dmix -q -c 1 -t raw -f s16 -r $SR $FILE") 
;;(Parameter.set 'Audio_Method 'Audio_Command)
;;(Parameter.set 'Audio_Required_Format 'snd)


;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;
;;;; setup voices
;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

;;;; Festvox voices
;;(set! default_voice 'voice_rab_diphone)
;;(set! default_voice 'voice_don_diphone)
;;(set! default_voice 'voice_kal_diphone)
;;(set! default_voice 'voice_ked_diphone)

;;;; MBROLA voices
;;(set! default_voice 'voice_us1_mbrola)
;;(set! default_voice 'voice_us2_mbrola)
;;(set! default_voice 'voice_us3_mbrola)

;;;; CMU Arctic voices
;;(set! voice_default 'voice_cmu_us_rms_arctic_clunits)
;;(set! voice_default 'voice_cmu_us_bdl_arctic_clunits)
;;(set! voice_default 'voice_cmu_us_slt_arctic_clunits)
;;(set! voice_default 'voice_cmu_us_clb_arctic_clunits)
;;(set! voice_default 'voice_cmu_us_awb_arctic_clunits)
;;(set! voice_default 'voice_cmu_us_jmk_arctic_clunits)

;;;; Nitech HTS voices
;;(set! voice_default 'voice_nitech_us_rms_arctic_hts)
;;(set! voice_default 'voice_nitech_us_bdl_arctic_hts)
(set! voice_default 'voice_nitech_us_slt_arctic_hts)
;;(set! voice_default 'voice_nitech_us_clb_arctic_hts)
;;(set! voice_default 'voice_nitech_us_awb_arctic_hts)
;;(set! voice_default 'voice_nitech_us_jmk_arctic_hts)
;;(set! voice_default 'voice_cmu_us_kal_com_hts)
;;(set! voice_default 'voice_cstr_us_ked_timit_hts)


;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;
;;;; Advanced voice configuration
;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

;;;; Slow the HTS speech down.
;;(set! hts_duration_stretch 0.1)

;;;; Slow the standard voices down
;;(Parameter.set 'Duration_Stretch 2.5)

;;;; Set volume.
;;(set! default_after_synth_hooks
;;    (list (lambda (utt) (utt.wave.rescale utt 2.0 t))))
```

---

### Post by damis648 on 2008-11-21
It is almost done! I would call this an RC... it works VERY well. I fixed the running-together issue with a few things. Anyway, this is it. The only bug is that it will read the temperature weird. In any case, it works AWESOME! I have also included a script that works in conjunction to tell you how many new emails (from gmail) you have! This is sweet!

Instructions:
1. Delete everything in your /etc/festival.scm, except for your default voice setting. (The reason is you will want for festival to use OSS instead of alsa or ESD, because then we can use the padsp wrapper)

2. Download the scripts.

3. Put the gmail script and the alarm script in your home directory, and put your username and password where it says to in the gmail script.

4. Customize the scripts (changing the sleep time until the volume goes down to whatever you want, default is at 5 but you will probably want 60 or 120, as well as setting the correct METAR id for weather-utils, default is KDTW) and set up the script as a cron job, good luck!

EDIT: **DO NOT DOWNLOAD THE morningalarm.sh SCRIPT FROM THIS POST. SEE BELOW, POST 18.**

---

### Post by myusername on 2008-11-21
is there anyway i can make it boot at a certain time and run that script?

---

### Post by damis648 on 2008-11-21
> **myusername said:**
> is there anyway i can make it boot at a certain time and run that script?

If your BIOS has the option to boot at a certain time, do that, and set up a cron job. If not, try suspending. I think it will wake it when the job starts, though I am not sure.

---

### Post by damis648 on 2008-11-21
I have improved the script again. Follow the directions from post 15, but use this script instead. Lines have been commented within to illustate what does what and what can be changed. Enjoy! :-)

BTW: I recommend voice_nitech_us_slt_arctic_hts, its the bet voice to wake up to.

---

### Post by Ponomous on 2008-11-22
Wow amazing job damis!! Im loving it!

---

### Post by damis648 on 2008-11-22
> **Ponomous said:**
> Wow amazing job damis!! Im loving it!

Thanks! Glad you like it! I am sure it could be better though, so go right ahead if anyone wants to modify it.

---

### Post by Ponomous on 2008-11-23
Next step for me (and this will take a while) is to make a visual interface and have it run stand alone in the background!

---

### Post by andrewabc on 2008-11-23
> **barbedsaber said:**
> I want an alarm, that plays music really loudly for wakeing up, but when you acknowledge it, it reduces the volume to listening volume, so you can start the day with some tunes.


Audacious has a plugin that allows that. It will play at a certain level, then get quieter (or louder) as time goes on, until a specific volume. You can set the alarm for different time each day of week.

---

### Post by jdong on 2008-11-23
> **andrewabc said:**
> Audacious has a plugin that allows that. It will play at a certain level, then get quieter (or louder) as time goes on, until a specific volume. You can set the alarm for different time each day of week.


Or you can just play around with alsamixer via the script, too.

---

### Post by easybake on 2008-12-27
Not enough people know about this script. 

I changed up the weather part a bit to sound more natural.
```
echo "Good Morning Easy bake." |  festival --tts;
sleep 1; echo "Today is $(date '+%A') $(date '+%-B') $(date '+%-e')" |  festival --tts;
#sleep 1; echo "$(date '+%-B') $(date '+%-e')" |  festival --tts;
sleep 1; echo "The time is $(date '+%-I') $(date '+%-M')" |  festival --tts;
echo "It is currently"|  festival --tts;
weather-util -i KMDW | grep Temperature | cut -c16-19 | festival --tts;
echo "degrees outside and" |  festival --tts;
weather-util -i KMDW | grep Sky | cut -c19-35 | festival --tts;
echo "You have $(./gmail.py) e-mails." |  festival --tts;
```

Anyone want to post the cron that they use?

---

### Post by icecruncher on 2008-12-27
I found this really nice tutorial  @ [http://www.federicopistono.org/Set_up_an_MP3_OGG_Alarm_Clock_Using_Linux](http://www.federicopistono.org/Set_up_an_MP3_OGG_Alarm_Clock_Using_Linux)

you can have different playlists and you can choose between amarok or mplayer. It's set up via cron.
I highly recomend using it. it works. :D

---

### Post by icecruncher on 2008-12-27
and I can't get the gmail.py to work.  not sure what I'm doing wrong.

Traceback (most recent call last):
  File "./gmail.py", line 16, in <module>
    fc=int(msg[index+11:index2])
ValueError: invalid literal for int() with base 10: ''

edit:: that is because I have an @ sign in my password and it doesn't seem to want to work

---

### Post by icecruncher on 2008-12-27
so here is my config. 

```
#!/bin/bash 
#put a "cd" command here if your gmail and wakeup scripts aren't in the same folder
amixer -c 0 sset Master,0 100% #change the % here for starting Master volume
rhythmbox-client --set-volume .1 --hide
sleep 3 
rhythmbox-client --play
sleep 3; rhythmbox-client --set-volume .2 #commout out from here to
sleep 3; rhythmbox-client --set-volume .3
sleep 3; rhythmbox-client --set-volume .4
sleep 3; rhythmbox-client --set-volume .5
sleep 3; rhythmbox-client --set-volume .6 
sleep 3; rhythmbox-client --set-volume .7
sleep 3; rhythmbox-client --set-volume .8
sleep 3; rhythmbox-client --set-volume .9
sleep 3; rhythmbox-client --set-volume 1.0 #here to disable escalating the volume slowly
sleep 20; rhythmbox-client --set-volume .8 #change the '65' in this line to reflect how long you want to play (after volume escalation)
sleep 1; rhythmbox-client --set-volume .6 #comment out from here to
sleep 1; rhythmbox-client --set-volume .4
sleep 1; rhythmbox-client --set-volume .2
sleep 1; rhythmbox-client --set-volume .1 #here to disable the volume from "fading" when festival starts speaking
rhythmbox-client --set-volume .1
echo "Good Morning ice." |  festival --tts; 
sleep 1; echo "Today is $(date '+%A') $(date '+%-B') $(date '+%-e')" |  festival --tts;
#sleep 1; echo "$(date '+%-B') $(date '+%-e')" |  festival --tts;
sleep 1; echo "The time is $(date '+%-I') $(date '+%-M')" |  festival --tts;
sleep 2; echo "You have $(./gmail.py) e-mails." | festival --tts;
echo "It is currently" |  festival --tts;
#sleep 1; echo "Good Morning my friend. Today is $(date '+%A'). The time is $(date '+%-H') and $(date '+%-M'). You have $(./gmail.py) e-mails. The weather is as follows:" | padsp festival --tts;
weather-util -i VTCC | grep Sky | festival --tts;
#weather-util -i KPTK | grep Sky | padsp festival --tts; #visit http://www.nws.noaa.gov/tg/siteloc.shtml to help find the ID or your METAR station nearest you, and replace that anywhere you see KPTK.
weather-util -i VTCC | grep Temperature | festival --tts; #visit http://weather.noaa.gov/pub/data/observations/metar/decoded/ to see the txt file that the stations provide, and you can include your own weather lines here using grep like below
weather-util -i VTCC | grep Weather | festival --tts;
weather-util -i VTCC | grep Humidity | festival --tts;
sleep 1; rhythmbox-client --set-volume .2 #comment out from here to
sleep 1; rhythmbox-client --set-volume .4
sleep 1; rhythmbox-client --set-volume .6
sleep 1; rhythmbox-client --set-volume .8
sleep 1; rhythmbox-client --set-volume 1.0 #here to disable escalation back up from speaking
```

here is my crontab
```
# m h  dom mon dow   command
  30 9 *   *   1-5   /home/ice/bin/morningalarm.sh
```

---

### Post by glotz on 2008-12-27
[QUOTE=myusername]is there anyway i can make it boot at a certain time and run that script?[/QUOTE]Buy this little time controlled switch from any hardware store to power the box up at desired time. Then edit the boot to include whatever.

---

### Post by easybake on 2008-12-27
> **icecruncher said:**
> and I can't get the gmail.py to work.  not sure what I'm doing wrong.

Traceback (most recent call last):
  File "./gmail.py", line 16, in <module>
    fc=int(msg[index+11:index2])
ValueError: invalid literal for int() with base 10: ''

edit:: that is because I have an @ sign in my password and it doesn't seem to want to work

Instead of the @ sign use %40 

It should work.

---

### Post by markp1989 on 2008-12-27
> **rolando2424 said:**
> By the way, you could tell me a page to see the weather and what is the email you use (gmail, hotmail, etc.)

edit:

Otherwise, the script will turn into a very tiny
```

echo "Today is $(date '+%A'). The time is $(date '+%-H') and $(date '+%-M')" | festival --tts;

```

This says something like "Today is Thursday. The time is 23 and 16."

running that on arch, i get this mesage 

```
failed to open file "test" for reading
[mark@markspc ~]$ echo "Today is $(date '+%A'). The time is $(date '+%-H') and $(date '+%-M')" | festival --tts;
-=-=-=-=-=- EST Error -=-=-=-=-=-
{FND} Feature pbreak_index not defined

-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-
 
```

---

### Post by markp1989 on 2008-12-27
so far i have 

```
echo "good morning, today is $(date '+%A'). The time is $(date '+%-M') past $(date '+%-H')" |festival --tts
echo the current weather conditions are `/home/mark/.accweather.sh "EUR|UK|UK150|Harrow"`entigrade |festival --tts;
mpc volume -100
mpc play
mpc volume +25
sleep 30
mpc volume +5
sleep 1
mpc volume +5
sleep 1
mpc volume +5
sleep 1
mpc volume +5
sleep 1
mpc volume +5
sleep 1
mpc volume +5
sleep 1
mpc volume +5
sleep 1
mpc volume +5
sleep 1
mpc volume +5
sleep 60 
mpc pause
sleep 300 #snoze time
mpc play 
 
```

.accweather.sh (not mine , i think i foud it on arch forums

```
 #!/bin/sh
#AccuWeather (r) RSS weather tool for conky
#
#USAGE: weather.sh <locationcode>
#
#(c) Michael Seiler 2007

METRIC=1 #Should be 0 or 1; 0 for F, 1 for C

if [ -z $1 ]; then
    echo
    echo "USAGE: weather.sh <locationcode>"
    echo
    exit 0;
fi

curl -s http://rss.accuweather.com/rss/liveweather_rss.asp\?metric\=${METRIC}\&locCode\=$1 | perl -ne 'if (/Currently/) {chomp;/\<title\>Currently: (.*)?\<\/title\>/; print "$1"; }'
```


I need an mp3 file that makes an alarm sound, and then i will be done, anyone know where i can get one?

edit: how do i make festival speak faster?

---

### Post by ajcham on 2008-12-27
> **markp1989 said:**
> 
I need an mp3 file that makes an alarm sound, and then i will be done, anyone know where i can get one?

Try [http://www.pdsounds.org/tag/alarm](http://www.pdsounds.org/tag/alarm)

EDIT: Actually there are some better ones if you search 'alarm' here: [http://www.freesound.org/searchText.php](http://www.freesound.org/searchText.php)

---

### Post by easybake on 2008-12-29
I was having some problems getting the script to work through cron even though it worked perfectly through terminal. The solution was to change the cron to use display 0. This is what my cron ended up looking like```
# m h  dom mon dow   command
PATH=/sbin:/bin:/usr/sbin:/usr/bin
MAILTO=root
SHELL=/bin/bash
25 11 * * * DISPLAY=:0.0 $HOME/morningalarm.sh

```

---

