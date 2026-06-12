---
title: "Female Robotic Text-To-Speech Tutorial"
date: 2011-07-27
forum: Tutorials
---

### Post by wolterh on 2011-07-27
Hi, I've been trying to get a robotic voice TTS to replace the default voice in espeak, which is boring and terrible.

I have achieved a female robotic voice, which I explain how to obtain here.

The tools used are
[LIST]
[*]espeak
[*]sox (play)
[/LIST]

First, to "say" something with espeak, the TTS engine, you can use the following code:
```
echo "All systems online" | espeak
```

The voice the text is read with is the one we want to change. Specifically for the female robotic voice, we are going to use as base voice the **female3** voice. We can set espeak to use it with the **-v** parameter, followed by the name of the voice: e.g.
```
echo "I sound like a female" | espeak -v female3
```

Now is when the robotic part comes in. Robotic voices are typically characterized by two things:
[LIST]
[*]Echo
[*]Metallic sound
[/LIST]

These effects we can achieve with the sound manipulation application **play**, which is an interface to sox used solely for playing audio.
You can read the manual on sox ```
man sox
``` to understand the following code, which will transform normal computer voice into robotic-ish voice. You should read the **espeak** manual as well.


[SIZE="4"]**OBTAINING THE ROBOTIC VOICE**[/SIZE]
To get the robotic voice, follow these steps:
[LIST=1]
[*]Save the following text in a text file (in this example, it will be referred to as **femalebot**:
```

espeak --stdout -v female3 | play -t wav - \
overdrive 10 \
echo 0.8 0.8 5 0.7 \
echo 0.8 0.7 6 0.7 \
echo 0.8 0.7 10 0.7 \
echo 0.8 0.7 12 0.7 \
echo 0.8 0.88 12 0.7 \
echo 0.8 0.88 30 0.7 \
echo 0.6 0.6 60 0.7 \
gain 8

```
*The metallic effect is achieved by using the echo effect with a very short delay. The overdrive enhances the sound a bit, and the other echo effects give the final kick to the robotic voice.*


[*]Now, set it to be executable with the **chmod** command, e.g.
```
chmod +x /path/to/femalebot
```

[*]You can now use the robot voice in TTS, by issuing the following command:
```

echo "All systems online." | /absolute/path/to/femalebot

```
[/LIST]

Additionally, and to make things easier, you can place the script in any directory in the PATH variable. This way, you can issue the last command as follows:
```

echo "All systems online." | femalebot

```

---

### Post by coolglobal on 2011-07-27
Sweet! Very sci-fi! Works as described. I'm going to have fun with this.

---

### Post by Bandit on 2011-07-27
Very nice.
I have been playing around with it every now and then for a month or two trying to get the female voice to sound more life like.

---

### Post by Aquix on 2011-07-27
Nice, tts is fun to play with. I'll test it this weekend.

Btw, it's called **fembot**  ;P

---

### Post by lovinglinux on 2011-07-27
Cool. Now I can add voice to my scripts. :-)

BTW, the sox script didn't work for me.

---

### Post by tjeremiah on 2011-07-27
ill give this a shot. I tried this on KDE because they have this feature where it can tell you the time, but I couldnt get it to sound normal.

---

### Post by wolterh on 2011-07-27
You can easily let it tell you the time by adding a cron job :) I did it myself, on an hourly basis.

However, I did some modifications to my script, I think it sounds a bit better:

```

espeak --stdout -v female3 | play -t wav - \
overdrive 10 \
echo 0.8 0.8 5 0.7 \
echo 0.8 0.7 6 0.7 \
echo 0.8 0.7 10 0.7 \
echo 0.8 0.7 12 0.7 \
echo 0.8 0.88 12 0.7 \
echo 0.8 0.88 30 0.7 \
echo 0.6 0.6 60 0.7 \
gain 8

```

> **lovinglinux said:**
> Cool. Now I can add voice to my scripts. :-)

BTW, the sox script didn't work for me.

Does it throw an error or something?

---

### Post by uRock on 2011-07-27
Moved to Tutorials & Tips. In the future please post your tutorials here and wait for them to be approved.

Thanks,
uRock

---

### Post by Bandit on 2011-07-30
Here is one I think is fairly good. Its less glass sounding then Wolis but will require some minor editing to one of the voices in the espeak shared data directory.

Editing the F5 voice in the voices/!v folder, copy and past this data over the existing voice info in that file:

```

language variant 
name female5 
gender female 

pitch 165 220
roughness 0

formant 0 105  80 150 
formant 1 110  80 160 
formant 2 110  70 150 
formant 3 110  70 150 
formant 4 115  80 200 
formant 5 115  80 100 
formant 6 110  70 150 
formant 7 110  70 100 
formant 8 110  70 150 

stressAdd 0 0 -10 -10 0 0 10 40 
breath 5 14  16   16   16   6  0 10 
echo 20 10 
voicing 75 
consonants 150 150
breathw 150 150 200 200 400 400 

```

Then use this script to get the voice fine tuned a great deal:
```
espeak --stdout -s120 -k18 -a200 -v female5 | play -t wav - \
chorus 0.4 0.8 20 0.5 0.10 2 -t \
echo 0.9 0.8 33 0.9 \
echo 0.7 0.7 10 0.2 \
echo 0.9 0.2 55 0.5 \
gain 10
```

Cheers..

---

### Post by wolterh on 2011-07-30
Nice job! The female voice is a lot more clear! Sometimes I barely understand the other one!

---

### Post by Bandit on 2011-07-30
> **woli said:**
> Nice job! The female voice is a lot more clear! Sometimes I barely understand the other one!

Thanks, I think I can get it more clear. But what it boils down to is adding a lot of stops and pauses in the wording to make it sound more natural.

---

### Post by H3g3m0n on 2011-12-21
Been looking for a way to make voices sound more robotic myself.

Those scripts are nice but the problem is they all have those weird accents, they sound like a combination of mentally handicapped, deaf and European (even the US voices).

Might be worth looking at trying to use [OpenMARY]("http://mary.dfki.de/") instead of espeak. Has some more natural base voices. And running that through the overdrive.

Current speech synthesis just sounds so bad, even the top end stuff. Even if they do manage to get it sounding right you will never have the emotional tones that get added in when talking about different topics.

It's better to just avoid the uncanny valley by not trying to make things sound as real as possible.

Also I don't see why I would want my computer to sound like a person when it's not. I would prefer it to be obviously a computer.

---

### Post by wolterh on 2011-12-22
OpenMARY sounds so much better than the espeak voices! I think the robotic voice will sound a lot less cryptic

---

### Post by go_beep_yourself on 2012-05-09
Have you taken a look at JSpeak?

[http://linuxinnovations.blogspot.com/2012/05/jspeak-ultimate-in-linux-text-to-speach.html](http://linuxinnovations.blogspot.com/2012/05/jspeak-ultimate-in-linux-text-to-speach.html)

---

