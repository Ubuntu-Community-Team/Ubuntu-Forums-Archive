---
title: "Jokosher 0.10 is out!"
date: 2008-09-14
forum: The Cafe
---

### Post by Mr. Picklesworth on 2008-09-14
Not sure how old this news is, but I was excited to learn a few seconds ago that [Jokosher 0.10]("http://www.jokosher.org/") is out, with a lot of fun little tweaks.

Jokosher is a young but superb audio editing tool. It is a wonderful escape from the norm (such as Audacity) since it is one of very few audio editing tools to use a real user interface toolkit. (And a well organized interface, to boot).

I also just discovered why I didn't have any instrument effects: they are implemented by what must be a superbly cool API called LADSPA (Linux Audio Developer's Simple Plugin API), and the necessary plugins all must be installed separately. At first glance it seems a strange oversight that the Ubuntu package doesn't have them as Recommends, but then again they seem a bit hit & miss so far. See [http://userdocs.jokosher.org/Installation](http://userdocs.jokosher.org/Installation) and scroll down to "Instrument Effects".

This is exciting!
0.10 now supports PulseAudio properly, which means audio now sometimes "just works" (when you're lucky). Really, as one of the lucky ones for whom PulseAudio has always worked flawlessly, the smooth way that this operates (where it never quite coped for me via ALSA) is really encouraging.

---

### Post by zmjjmz on 2008-09-14
Hm, what would make Jokosher better is if they included loops for people who want something like Garageband.

---

### Post by Giant Speck on 2008-09-14
> **zmjjmz said:**
> Hm, what would make Jokosher better is if they included loops for people who want something like Garageband.

[IMG]http://www.afforums.com/forums/images/smilies/bandwagon.gif[/IMG]

---

### Post by loell on 2008-09-14
looking forward wit .11 or .12 for better pulseaudio.

---

### Post by Cresho on 2008-09-14
I installed a jokosher and tried using the record function and it did not work...i have version
 0.9..time to update!

---

### Post by Tomosaur on 2008-09-14
Jokosher is still very much a work in progress, so if you need a program for production use, you'd be best advised to use something else for the time being. I help out from time to time with Jokosher - haven't been able to do anything lately for a variety of reasons, but it's coming along anyway.

Simple things should work, but for anything complex you should look elsewhere. I think features such as looping etc might take a backseat until some of the more essential issues are worked out (many of these actually stem from gstreamer quirks and bugs, so if anybody can help out there, I think it would be greatly appreciated by the most active developers!).

Jokosher at Launchpad: [https://launchpad.net/jokosher](https://launchpad.net/jokosher)

---

### Post by Cresho on 2008-09-14
recording now works for me with the new update! :guitar:

---

### Post by DPic on 2009-06-15
And now it's at 0.11.1 and it just keeps getting better! xD

---

### Post by punkrawk101 on 2009-06-23
I was wondering if anybody could tell me how to export my audio to mp3. I tried exporting it with mixdown and it tells me i need a plugin that supports it. I have gstream which is supposed to support mp3 so i don't quite understand. Any suggestions?

---

### Post by ssam on 2009-06-23
> **punkrawk101 said:**
> I was wondering if anybody could tell me how to export my audio to mp3. I tried exporting it with mixdown and it tells me i need a plugin that supports it. I have gstream which is supposed to support mp3 so i don't quite understand. Any suggestions?

you need a gstreamer plugin package with the mp3 encoder. i think the one you want is.
```
gstreamer0.10-plugins-ugly-multiverse
```

---

### Post by ekeyme on 2012-02-02
> **ssam said:**
> you need a gstreamer plugin package with the mp3 encoder. i think the one you want is.
```
gstreamer0.10-plugins-ugly-multiverse
```
Thanks very much. That works.

---

