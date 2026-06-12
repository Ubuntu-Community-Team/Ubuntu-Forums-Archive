---
title: "JACK in Ubuntu 10.10 working but..."
date: 2010-12-07
forum: Ubuntu Studio
---

### Post by Saulevas on 2010-12-07
Hello everyone ;)

I have Ubuntu 10.10 (Maverick Meerkat) installed on my ASmobile laptop running JACK with Tascam US-122L pluged-in. Everything works like a charm (although it took me some time to get my Tascam to work). I use Ardour and Hydrogen for audio recording, Audacious for mp3's and Gnome MPlayer for video because they all work with JACK, and as a result I can hear the sound coming through US-122L. However, I'm curious if there's a way to have my whole system running through JACK, I mean when Ubuntu boots up I would like to hear the boot up sound through my Tascam (and through JACK that is) as well as the whole Ubuntu sound theme, everything in my web browser and etc. through JACK and my Tascam. 
Is this even possible? :)

Thanks in advance;)

P.S. What I liked with Windows (which was not much) was that when I would plud in my external Tascam soundcard the default soundcard would automatically change to it, and vice versa without any hastle.

---

### Post by cchhrriiss121212 on 2010-12-07
You could try this:
[http://ubuntuforums.org/showpost.php?p=9344940&postcount=6](http://ubuntuforums.org/showpost.php?p=9344940&postcount=6)
I can't say I use it myself but if it is simple enough to undo if it does not work for you.

---

### Post by Pablo_F on 2010-12-07
Hi, 

The alsa-jack plugin is an option, but nowadays, and in ubuntu maverick, I think the pulseaudio-module-jack approach is better and simpler. 

In maverick, you have to install the package "pulseaudio-module-jack" and then a command like this one:
[B]
pacmd load-module module-jack-sink channels=2[/B]

You can put this command in qjackctl, so you don't need to launch it everytime. Setup -> Options -> Execute script after StartUp. In this case, don't forget to put an ampersand at the end.

As an example, I like doing jack connections in patchage and I have a midi keyboard that I sometimes use with jack midi clients. My qjackctl's post-start script in ubuntu maverick is now: 
[B]
a2jmidid -e & pacmd load-module module-jack-sink channels=2 & patchage &[/B]

In sound preferences, or pavucontrol, put the default device jack sink. 

Cheers, Pablo

---

### Post by Sidar on 2010-12-07
[Not trying to hijack the thread!]

Pablo,

Thanks, i was looking for ages on how to do that.
But the thing is the moment i stop jack and try to run it again, it gives me an error that it can't start. It is starting but i think the jack-module kinda goes wrong. Something about unable to load module. ( first time i tried it, it did work, but then again i had some trouble with other stuff as well)

If i then load the module by hand in the terminal(not jack, jack is already running at this point) it nicely boots up( patchage is updated nicely). There is sound coming from jack output but in my sound preference i havn't even selected the jack-sink...which is pretty weird.

When quitting entirely audio goes back to the pulseaudio output again.( i like that so thats good)
Also can you explain on how i can load this module by default so i do not have to load it in jack ( or do you not recommand it? it just seems nicer to have the module ready when ever...).

Also Pulseaudio device chooser, does that evern work? Ive never managed to get sink on there in the sink list.

Again im not trying to hijack this thread, im sorry for this xD

---

### Post by AutoStatic on 2010-12-08
> **Saulevas said:**
> However, I'm curious if there's a way to have my whole system running through JACK, I mean when Ubuntu boots up I would like to hear the boot up sound through my Tascam (and through JACK that is) as well as the whole Ubuntu sound theme, everything in my web browser and etc. through JACK and my Tascam. 
Is this even possible? :)Yes, but personally I would highly discourage using JACK this way. JACK is not a desktop sound daemon, that's what PulseAudio is for.

Best,

Jeremy

---

### Post by Saulevas on 2010-12-08
> **cchhrriiss121212 said:**
> You could try this:
[http://ubuntuforums.org/showpost.php?p=9344940&postcount=6](http://ubuntuforums.org/showpost.php?p=9344940&postcount=6)
I can't say I use it myself but if it is simple enough to undo if it does not work for you.

Hey, **cchhrriiss121212**, thanks for the link!
I tried it but can't say that it worked, probably because I already have an .asoundrc file with different inputs (that were made for my Tascam Us-122L to work) and i didn't manage to edit it as suggested by **shyseeker** to make it work ;) 
However I appreciate your help!

I think I'll go with Pablo's suggestion :)

---

### Post by Saulevas on 2010-12-08
> **Pablo_F said:**
> Hi, 

The alsa-jack plugin is an option, but nowadays, and in ubuntu maverick, I think the pulseaudio-module-jack approach is better and simpler. 

In maverick, you have to install the package "pulseaudio-module-jack" and then a command like this one:
[B]
pacmd load-module module-jack-sink channels=2[/B]

You can put this command in qjackctl, so you don't need to launch it everytime. Setup -> Options -> Execute script after StartUp. In this case, don't forget to put an ampersand at the end.

As an example, I like doing jack connections in patchage and I have a midi keyboard that I sometimes use with jack midi clients. My qjackctl's post-start script in ubuntu maverick is now: 
[B]
a2jmidid -e & pacmd load-module module-jack-sink channels=2 & patchage &[/B]

In sound preferences, or pavucontrol, put the default device jack sink. 

Cheers, Pablo

Thanks, Pablo_F! This really worked! I did exactly like you said and, hey now I can hear the sound from any app through my Tascam. I still get some error about Jack being unable to start correctly if I add it to the start-up application list with the settings you suggested, but if I start it manually everything works like a charm! :popcorn:
Thanks again! ;)

---

### Post by Pablo_F on 2010-12-08
> Yes, but personally I would highly discourage using JACK this way. JACK is not a desktop sound daemon, that's what PulseAudio is for.

Hi Jeremy :) I completely understand your point. You are a musician who just get down to work. But put in the shoes of someone who is not very keen on their own music but they like to write a note or two in hydrogen or just enjoy playing the guitar with rakarrack for example. They get bored soon and they want to listen to music by others. Should they close the "music" session to start a "desktop" session? I can think of more user cases, like video artists.

This is, from the point of view of many users they would like sound from every app that claims to make noise, being music production oriented or not. I mean, even if they understand the problem. A few days ago prokoudine pointed to this article by the author of pulseaudio. A must read for the curious linux audio user, imho:

[http://0pointer.de/blog/projects/when-pa-and-when-not.html](http://0pointer.de/blog/projects/when-pa-and-when-not.html)

Until now, my approach to solve the "I want sound form every app" issue has been "jackify them all" so I have been using jack as a music production and desktop server, without pulseaudio. However, playback through jack is not easy or even possible with every app. Before this, I had a dual boot but that was a real chore... I think you use the "different users, one for music, another one for desktop" approach. Linux is all about choice, isn't it?


> Thanks, i was looking for ages on how to do that.
But the thing is the moment i stop jack and try to run it again, it gives me an error that it can't start. It is starting but i think the jack-module kinda goes wrong. Something about unable to load module. ( first time i tried it, it did work, but then again i had some trouble with other stuff as well)

If i then load the module by hand in the terminal(not jack, jack is already running at this point) it nicely boots up( patchage is updated nicely). There is sound coming from jack output but in my sound preference i havn't even selected the jack-sink...which is pretty weird.

When quitting entirely audio goes back to the pulseaudio output again.( i like that so thats good)
Also can you explain on how i can load this module by default so i do not have to load it in jack ( or do you not recommand it? it just seems nicer to have the module ready when ever...).

Also Pulseaudio device chooser, does that evern work? Ive never managed to get sink on there in the sink list.
 
Hi Sidar, I have been looking into this... Depending on the jack version and/or on other things that I don't see, sometimes jack does not start because there is a server already running (pulseaudio). 

This command is useful:

**pacmd list-sinks |grep name:**

In my case, I see:

	[I]name: <alsa_output.pci-0000_00_1b.0.analog-stereo>
	name: <alsa_output.pci-0000_05_01.0.analog-stereo>
	name: <jack_out>[/I]

...when jack is up and running. When jack is not running I don't see the jack_out. I have two audio cards right now. I can set the default with, for example:

**pacmd set-default-sink alsa_output.pci-0000_05_01.0.analog-stereo**

However, when I run jack with the "pacmd load-module ..." command rhytmhbox audio goes to the jack_out sink, which besides of weird, is cool :) . If I stop jackd, the audio goes to the default sink I chose. Then, I try with sounds coming from firefox. The first time I have to tell them to use the jack_out sink, the second time they recall they have to use it! Cool. Right now I am able to stop the jackd server and the transition to puseaudio is gapless! The opposite transition is not gapless though.

I don't understand padevchooser either. I understand and like pavucontrol.

Beware of /dev/shm/. It sometimes tend to be overcrowded and can result in system failure, especially in computers with little RAM. I have heard of problems in jack even with 1 GB and they were solved with a:

rm -f /dev/shm/pulse*

> 

I still get some error about Jack being unable to start correctly if I add it to the start-up application list with the settings you suggested

I am not sure if this will solve the problem but this is what Dreamstudio does:

It puts a script as "Execute Script on Startup" (which runs just before the jackd server starts) ("artshell -q terminate" is useless). The script is in /usr/bin and it is called pausepulse. It reads:
```

#!/bin/bash
#this is a script which will temporarily shut down pulseaudio and suspend its ability to respawn
sed -i 's/yes/no/g' ~/.pulse/client.conf 
pulseaudio -k
```

The script afterStartUp is called pulsejack and this is its content:

```
#!/bin/bash
#this is a script which will restore pulseaudio's ability to respawn, start pulseaudio, and finally connect pulseaudio to the jack audio server
sed -i 's/no/yes/g' ~/.pulse/client.conf
pulseaudio --daemonize --high-priority --realtime --exit-idle-time=-1
pactl load-module module-jack-sink
pactl load-module module-jack-source
```

I might change this to leave out the module-jack-source and append "channels=2" in the module-jack-sink line because I want front-left and front-right only.

For this to work you need to create a ~/.pulse/client.conf file with the line:

*autospawn=yes*

(or autospawn=no as these scripts change from no to yes when needed).

Scripts around qjacktl are very useful in any case. 

Cheers, Pablo

---

### Post by AutoStatic on 2010-12-09
> **Pablo_F said:**
> Hi Jeremy :) I completely understand your point. You are a musician who just get down to work. But put in the shoes of someone who is not very keen on their own music but they like to write a note or two in hydrogen or just enjoy playing the guitar with rakarrack for example. They get bored soon and they want to listen to music by others. Should they close the "music" session to start a "desktop" session? I can think of more user cases, like video artists.Hello Pablo, to everyone their own workflow, it is indeed all about choices. I just wanted to state that I discourage stacking multiple sound daemons. It's asking for trouble. But I don't have a real solution either.

> **Pablo_F said:**
> This is, from the point of view of many users they would like sound from every app that claims to make noise, being music production oriented or not. I mean, even if they understand the problem. A few days ago prokoudine pointed to this article by the author of pulseaudio. A must read for the curious linux audio user, imho:

[http://0pointer.de/blog/projects/when-pa-and-when-not.html](http://0pointer.de/blog/projects/when-pa-and-when-not.html)I attended Lennart's lecture at LAC2010 and it strengthened my point of view that PulseAudio has nothing to do on an audio production machine. But that is indeed from a musicians's perspective. For day to day desktop use PulseAudio does a great job. So yes, I separate the two by using different accounts.

Best,

Jeremy

---

