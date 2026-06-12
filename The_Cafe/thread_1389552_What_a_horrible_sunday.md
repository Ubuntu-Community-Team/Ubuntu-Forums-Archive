---
title: "What a horrible sunday"
date: 2010-01-24
forum: The Cafe
---

### Post by Mariane on 2010-01-24
I spent the whole day trying to get my headphones to work. And part of every single day in the preceeding week, too. They still don't work. 

Mariane

---

### Post by yester64 on 2010-01-24
Sorry to hear that.
Perhaps they are broken inside. Cable can be an issue. Happend to my mine.

---

### Post by The Toxic Mite on 2010-01-24
> **Mariane said:**
> I spent the whole day trying to get my headphones to work. And part of every single day in the preceeding week, too. They still don't work. 

Mariane

Let's face it: if headphones don't work, they don't work.

Got $10 to spare? Buy new ones! ;)

---

### Post by cammin on 2010-01-24
Maybe it's time for a new set of headphones.

---

### Post by NoaHall on 2010-01-24
There are worse things happening in the world. Get over yourself.

---

### Post by Mariane on 2010-01-24
The headphones are not the problem, I tried 3 pairs which work on another computer. I can't redirect the sound to the headphone jack. 

Mariane

---

### Post by k64 on 2010-01-24
The whole point of open source software is fixing the problems yourself.

Unless, of course, it involves hardware not working. Especially networking hardware, because if your Wi-Fi isn't working, you can't access any other drivers.

---

### Post by k64 on 2010-01-24
> **Mariane said:**
> The headphones are not the problem, I tried 3 pairs which work on another computer. I can't redirect the sound to the headphone jack. 

Mariane

Probably it's your sound card that's the problem. Have you tried disabling PulseAudio? ALSA works much better.

---

### Post by Mariane on 2010-01-24
> **NoaHall said:**
> There are worse things happening in the world. 


Yes. And having my neighbour complaining about noise is shortly going to become one of them ;)

---

### Post by Mariane on 2010-01-24
> **k64 said:**
> Probably it's your sound card that's the problem. Have you tried disabling PulseAudio? ALSA works much better.

Everybody says alsa is better, but no-one has yet told me how to get rid of *** pulseaudio

---

### Post by k64 on 2010-01-24
> **Mariane said:**
> Everybody says alsa is better, but no-one has yet told me how to get rid of *** pulseaudio

In a Terminal:

```
sudo killall pulseaudio
```

Edit: If you want to get rid of PulseAudio permanently:

```
sudo apt-get purge pulseaudio
```

---

### Post by yester64 on 2010-01-24
> **Mariane said:**
> The headphones are not the problem, I tried 3 pairs which work on another computer. I can't redirect the sound to the headphone jack. 

Mariane

Then it might be the plugin. I don't think its a driver. Is there a way you can check if sound comes out anyhow? Like speakers?

---

### Post by llawwehttam on 2010-01-24
> **k64 said:**
> In a Terminal:

```
sudo killall pulseaudio
```Edit: If you want to get rid of PulseAudio permanently:

```
sudo apt-get purge pulseaudio
```

Problem being gnome-desktop depends on pulseaudio

```
llawwehttam@Deadlock:~$ apt remove pulseaudio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  libcanberra-pulse pulseaudio pulseaudio-esound-compat
  pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-udev
  pulseaudio-module-x11 **ubuntu-desktop**
0 upgraded, 0 newly installed, 8 to remove and 4 not upgraded.
After this operation, 5,325kB disk space will be freed.
Do you want to continue [Y/n]? 



```You might not want to do this.

I would love to remove pulse but its too intertwined with ubuntu at the moment.

And to answer the first post I do secretly enjoy troubleshooting!........ if I have time to kill. It can be nice to have at least one stable machine.
And yes I am one of those geeks who breaks things simply to fix them again. I can't help it, its just the way I learn.:lolflag:

EDIT: and in the code above I have an alias line as follows.

```
alias apt='sudo apt-get'
```

---

### Post by Zoot7 on 2010-01-24
> **k64 said:**
> Edit: If you want to get rid of PulseAudio permanently:

```
sudo apt-get purge pulseaudio
```
That works but, if you're using Karmic you'll soon find your media keys won't function and there's no gnome volume control as there once was.

I think the only way actually remove it and just use Alsa with no reduced functionality (as you could in earlier releases) is to fetch the source code for gnome-applets and gnome-media from the Debian Testing/Unstable repository and build it yourself against Ubuntu.

---

### Post by NoaHall on 2010-01-24
I'm not using pulseaudio at all, I've made my media controls work better than they did before.
Easy.

```
sudo apt-get remove --purge pulseaudio*
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
sudo apt-get alsa-source

Then, to enable the volume control on my keyboard, I did this -

System -> Preferences -> Keyboard Settings -> Add ->

Then, -

Name : Volume Up
Command : amixer set Master 1%+
Keyboard Shortcut: Press your "volume up" button

Name : Volume Down
Command : amixer set Master 1%-
Keyboard Shortcut: Press your "volume down" button

Name : Volume Mute/Unmute
Command : amixer sset Master toggle
Keyboard Shortcut: Press of "mute" button
```

---

### Post by NoaHall on 2010-01-24
> **Mariane said:**
> Yes. And having my neighbour complaining about noise is shortly going to become one of them ;)

You know, most speakers have a little turny thing. It's for "turning it down" ;)

---

### Post by k64 on 2010-01-24
A better idea:

```
sudo apt-get install kubuntu-desktop
```

Use KDE instead of GNOME.

---

### Post by llawwehttam on 2010-01-24
> **k64 said:**
> A better idea:

```
sudo apt-get install kubuntu-desktop
```Use KDE instead of GNOME.

[OPINION]no thanks because KDE ( since 4.0) is the most cluttered and saggy bug ridden piece of junk.[/OPINION]

---

### Post by k64 on 2010-01-24
> **llawwehttam said:**
> [OPINION]no thanks because KDE ( since 4.0) is the most cluttered and saggy bug ridden piece of junk.[/OPINION]

Changed:

```
sudo apt-get install xubuntu-desktop
```

XFCE all along.

---

### Post by BETATEST on 2010-01-24
> **k64 said:**
> The whole point of open source software is fixing the problems yourself.

That's not the point at all for Open Source.  :confused:

---

### Post by nmccrina on 2010-01-24
> **BETATEST said:**
> That's not the point at all for Open Source.  :confused:

Well, yeah, kind of the point of Open Source is to allow developers to tweak things the way they want/need  them. If you can't program, there really isn't a difference between open source and proprietary software, except price. Unless zealous Linux fanatics have brainwashed you. :P

---

### Post by Yes on 2010-01-24
You sure the headphone jack isn't just broken?

---

### Post by cammin on 2010-01-24
I don't use gnome anymore but i remember having a similar problem getting my mic to work.

The volume control should have a setting somewhere that lets you change the device it controls. The options should look like:
Device0: 1 analog output 1 analog input
Device1: 2 digital output 1 analog input
Device2: 2 analog output 2 digital output

.etc

If you mess around with the device being used, one of them should have output to the headphone jack.

Some intel hda audio cards like to play sound out of the speakers even if the headphones are connected.


If all else fails, you can plug the headphones into the speaker jack in the back. At least it will keep the neighbors off your back.



> **llawwehttam said:**
> Problem being gnome-desktop depends on pulseaudio

```
llawwehttam@Deadlock:~$ apt remove pulseaudio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  libcanberra-pulse pulseaudio pulseaudio-esound-compat
  pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-udev
  pulseaudio-module-x11 **ubuntu-desktop**
0 upgraded, 0 newly installed, 8 to remove and 4 not upgraded.
After this operation, 5,325kB disk space will be freed.
Do you want to continue [Y/n]? 



```

Ubuntu-desktop is a metapackage. it installs nothing of it's own, but has a bunch of dependencies that make up the stuff in a normal Ubuntu install. Removing it won't uninstall any of those dependencies so it's fine to get rid of it.

---

### Post by Mariane on 2010-01-24
> **Yes said:**
> You sure the headphone jack isn't just broken?

No I'm not. The way I test that is by plugging in headphones or external speakers. When I do this the headphones or external speakers don't work. The laptop speakers still work. 

Now I have no pulseaudio anymore and my problem remains. 

Correlated or uncorrelated weird thing is that if I type
say hi
I hear "hi hi"
everything after "say" has an echo at the end. I think it's a symptom that the problem is software related. 

Mariane

---

### Post by chessnerd on 2010-01-24
I had the same issue with my laptop. Onboard sound worked, but the headphone didn't. My post about it is here: [http://ubuntuforums.org/showthread.php?t=1265116](http://ubuntuforums.org/showthread.php?t=1265116) and the third post down has a link to the article that fixed it.

Hope this helps you.

---

### Post by steveneddy on 2010-01-24
> **NoaHall said:**
> You know, most speakers have a little turny thing. It's for "turning it down" ;)

I Googled for that phrase - turny thing - and didn't find it.

Is this something new in Karmic?

:popcorn:

---

### Post by FuturePilot on 2010-01-24
Try muting the "Front" channel in the sound mixer.

---

### Post by Mariane on 2010-01-24
> **FuturePilot said:**
> Try muting the "Front" channel in the sound mixer.

Didn't change much. Maybe the sound got marginally quieter. The column over "Headphones" is at zero and won't go up no matter what other column I raise or lower. 

> **chessnerd said:**
> I had the same issue with my laptop. Onboard sound worked, but the headphone didn't. My post about it is here: [http://ubuntuforums.org/showthread.php?t=1265116](http://ubuntuforums.org/showthread.php?t=1265116) and the third post down has a link to the article that fixed it.

Hope this helps you.

Thank you, apart from re-installing alsa it is at least something new to try. I'll do it tomorrow, now I'm going to watch a movie - and my neighbour will just have to bear the sound of it. 

Mariane

---

### Post by steveneddy on 2010-01-24
You got paper walls there or something?

---

### Post by dragos240 on 2010-01-24
I love troubleshooting. It's fun :)

---

### Post by lisati on 2010-01-24
> **steveneddy said:**
> I Googled for that phrase - turny thing - and didn't find it.

Is this something new in Karmic?

:popcorn:
Not sure if there's sarcasm here: I refer to the "turny" thing on my laptop as a volume control.......

And I just discovered this morning that part of me not getting my email server accessible from the outside world was that even though I'd changed my broadband password @ my ISPs website I still had to use the old one...... odd that the modem was able to connect with the "wrong" password.

---

### Post by Mariane on 2010-01-25
> **steveneddy said:**
> 
You got paper walls there or something?


I'm hard of hearing but unfortunately my neighbour is not :P 

Mariane

---

### Post by Tristam Green on 2010-01-25
> **k64 said:**
> Especially networking hardware, because if your Wi-Fi isn't working, you can't access any other drivers.

LOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOL

Penny, you crack me up.

---

### Post by audiomick on 2010-01-25
> **k64 said:**
> The whole point of open source software is fixing the problems yourself.

Not quite. It is not the whole point, and it is the possibility to find out how to fix it for yourself, even if you choose to pay someone to do it for you. 

Expressed that way, that is one of my main reasons for using linux.

---

### Post by SuperSonic4 on 2010-01-25
Yeah I like to troubleshoot although sometimes it's annoying. Compiling mplayer from SVN without a GUI and then adding smplayer makes it the best media player I've ever used.

---

