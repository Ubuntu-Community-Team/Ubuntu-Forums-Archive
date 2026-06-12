---
title: "Alarm Clock, Date and Time"
date: 2009-03-02
forum: The Cafe
---

### Post by GaRRu on 2009-03-02
So Lets just get into the straight point.

I really appreciate all the hard work effort done in the forum and the people that help around Give them a round of Claps :D =D>=D>=D>=D>=D>

I have this scrip in my alarm clock, [COLOR="black"]_**I wondered if I could add a opening song to it with the name I chose to enter as a song in the music directory folder**_[/COLOR]. I have found some ways but its all the time stops the sound before the alarm talks and sometimes even do one thing at a time ( sound without voice, or voice without song).

_Is there a way to make the song go on and make it still continue to work while the voice echo is talking?_

Here is my script:
[PHP]echo "Good Morning." |  festival --tts;
echo "its $(date '+%-I') o'clock and $(date '+%-M') Minutes, today is $(date '+%A') $(date '+%-B') $(date '+%-e')" |  festival --tts;
echo "The Weather in Modi'in is"|  festival --tts;
weather-util -i KMDW | grep Temperature | cut -c16-19 | festival --tts;
echo "degrees"|  festival --tts;
echo "sky condition is"|  festival --tts;
weather-util -i KMDW | grep Sky | cut -c19-35 | festival --tts;
echo "And you have $(./gmail.py) e-mails to read." |  festival --tts;[/PHP]

This is a script I found that didn't quite help me at all...
[PHP]amixer -c 0 sset Master,0 100%
rhythmbox-client --set-volume .1
rhythmbox-client --play
sleep 3; rhythmbox-client --set-volume .2
sleep 3; rhythmbox-client --set-volume .3
sleep 3; rhythmbox-client --set-volume .4
sleep 3; rhythmbox-client --set-volume .5
sleep 3; rhythmbox-client --set-volume .6 
sleep 3; rhythmbox-client --set-volume .7
sleep 3; rhythmbox-client --set-volume .8
sleep 3; rhythmbox-client --set-volume .9
sleep 3; rhythmbox-client --set-volume 1.0
sleep 65; rhythmbox-client --set-volume .8
sleep 1; rhythmbox-client --set-volume .6
sleep 1; rhythmbox-client --set-volume .4
sleep 1; rhythmbox-client --set-volume .2
sleep 1; rhythmbox-client --set-volume .1
rhythmbox-client --set-volume .1
sleep 1; echo "Good Morning my friend. Today is $(date '+%A'). The time is $(date '+%-H') and $(date '+%-M'). You have $(./gmail.py) e-mails. The weather is as follows:" | padsp festival --tts;
weather-util -i KPTK | grep Sky | padsp festival --tts;
weather-util -i KPTK | grep Temperature | padsp festival --tts;
weather-util -i KPTK | grep Weather | padsp festival --tts;
weather-util -i KPTK | grep Humidity | padsp festival --tts;
sleep 1; rhythmbox-client --set-volume .2
sleep 1; rhythmbox-client --set-volume .4
sleep 1; rhythmbox-client --set-volume .6
sleep 1; rhythmbox-client --set-volume .8
sleep 1; rhythmbox-client --set-volume 1.0[/PHP]

---

