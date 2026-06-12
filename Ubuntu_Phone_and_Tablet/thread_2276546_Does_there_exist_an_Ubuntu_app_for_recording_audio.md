---
title: "Does there exist an Ubuntu app for recording audio through microphone?"
date: 2015-05-03
forum: Ubuntu Phone and Tablet
---

### Post by kjell159 on 2015-05-03
Hello,
I'm enjoying my new Ubuntu Touch phone.
I was in the need for a new smartphone as of my last one almost nothing remains, it was completely broke,
so I waited and then ordered the Ubuntu phone as I was very curious and wanted to get along on this boat.
The idea and just the tought of running mostly free software is amazing,
no company like Microsoft, Apple or Google (Inc.) in your back. ;)
So that means I've got the BQ Aquaris E 4.5 model.

The phone seems to have got two microphones: one near the USB-port - which I noticed is used while calling - and a 'noise cancelling'  one on the back.
I wondered if those, or one of those, can be utilised for recording audio, preferably in WAV format,
for say making field recordings and voice memos?
If so, is there already an application to do so as I cannot find one yet?

---

### Post by _march_ on 2015-05-03
Not an app but I've read somewhere that using arecord worked fine via Terminal.

---

### Post by grahammechanical on 2015-05-03
There is a web site that is an unofficial app browser for Ubuntu Touch apps.

[https://uappexplorer.com/apps](https://uappexplorer.com/apps)

Under the music & audio category it has Soundtrap, which is described as a "web app that allows you to record, edit collaborate and share music on Ubuntu phone." Clicking install is said to "take you to the official app store on a Ubuntu Touch device."

I do not have a Ubuntu phone so I can make no assessment of this app.

Regards.

---

### Post by _march_ on 2015-05-03
Just tested it on my bq:

> arecord test.wav records.

> aplay test.wav plays your file.

Isn't a comfortable way but works fine for the moment.

[Source]("http://forum.ubuntuusers.de/topic/ubuntu-touch-plauder-thread/89/#post-7524268")

---

### Post by kjell159 on 2015-05-06
The mentioned app wont recognize the microphone and is quite resource hungry, it's more of an audio workstation then just a recorder.
But I tried through terminal and it works perfect, thanks for the tip!

---

### Post by lgd on 2015-05-09
By the way, you can stop the recording by CTRL + C in the terminal app.

I tested the two commands for the community(s) on the most popular German community because of a missing app for this more or less core functionality as a use case. You could also create a icon like a app. Make simply two, one "record start" and another "record stop". And a third for "play recording" if you will not use the music app or mediaplayer.

For this you need to create or copy and modify a [desktop file]("https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles") in ~/.local/share/applications/record-start.desktop and so on. In this file you have to set especially
```

Exec=arecord myrecord.wav

```
and in the other desktop file then for example
```

Exec="bash -c kill $(pidof arecord)"

```
And for playing:
```

Exec=aplay myrecord.wav

```

In addition to this you need to insert a line
```

X-Ubuntu-Touch=true

```
to appear as a icon when you scrolled down your app scope to refresh it. Don't forget Name and maybe Icon, too. Terminal could be set to true. Other fields are not really important or necessary.

Greetings, lgd

**Edit:** Some changes because of record stop and play recording.

---

### Post by jtappin on 2015-07-21
I just noticed that such an app has now been incorporated in the app store. It's called "recorder". At the moment it is fairly basic but the key parts are there.

(I have no connection with the author of the app).

---

### Post by Harald_Walker on 2015-07-21
> **jtappin said:**
> I just noticed that such an app has now been incorporated in the app store. It's called "recorder". At the moment it is fairly basic but the key parts are there.


Thanks. It works on my MX4. Better than terminal solution.

---

