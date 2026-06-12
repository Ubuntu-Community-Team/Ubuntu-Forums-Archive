---
title: "&quot;Video edition is an area where Linux is clearly lacking&quot;, they say..."
date: 2009-12-12
forum: The Cafe
---

### Post by Keyper7 on 2009-12-12
...and although so far I agree, for the first time in my life I'm feeling the days of this sentence are numbered.

Today I finished a small, personal DVD project. I needed some non-linear editing, so I fired up OpenShot. Threw some audio, video and image files on the timeline, added some nifty transitions and effects, previewed and rendered.

Then I needed authoring, so I fired up 2ManDVD. Imported some files, build up a menu, added some buttons with video previews and rotated them a little bit just for fun. A couple more clicks and my ISO was done. Tested it on Totem and then burned it on a RW. Played perfectly on my player.

Except for rendering times, I did this in less than an hour, mainly with click and drag, with the occasional typing for fine tuning parameters.

As I sat watching my homemade DVD, I was hit with memories of past struggles with Kino, Cinelerra, LiVES, DVDStyler, QDVDAuthor, tovid... some of them were buggy and others lacked features. All of them are quite impressive projects, but on none of them I could do the job as quickly as I did today.

My, sometimes progress is a nice thing to witness! :)

---

### Post by MaxIBoy on 2009-12-12
OpenShot, eh? Never heard of it myself, but now I want to try it. If it's more stable than kdenlive, I am sold!

---

### Post by bigbrovar on 2009-12-13
I tried Man2dvd couple of years ago, I found it very unstable and crashy, seem the problem has been fixed? anyway am giving it a try as we speak. thanks

---

### Post by Keyper7 on 2009-12-13
> **bigbrovar said:**
> I tried Man2dvd couple of years ago, I found it very unstable and crashy, seem the problem has been fixed? anyway am giving it a try as we speak. thanks

Stable as a rock during my experience... which, I have to admit, wasn't particularly long or complex, so take this with a grain of salt. But I used a lot of things: graph visualization of the DVD structure, video thumbnail rotation, chaptering... never crashed.

---

### Post by Jose Catre-Vandis on 2009-12-13
Links to openshot:
```
http://www.openshotvideo.com/
```
They do debs for Ubuntu and a ppa for Karmic (built on Python/Gnome integration)

Links to 2ManDVD
```
http://www.kde-apps.org/content/show.php/2ManDVD?content=99450
```
(KDE App / QT4)

---

### Post by Keyper7 on 2009-12-13
> **Jose Catre-Vandis said:**
> Links to 2ManDVD
```
http://www.kde-apps.org/content/show.php/2ManDVD?content=99450
```
(KDE App / QT4)

Not KDE, just Qt.

---

### Post by quinnten83 on 2009-12-13
> **Jose Catre-Vandis said:**
> Links to openshot:
```
http://www.openshotvideo.com/
```
They do debs for Ubuntu and a ppa for Karmic (built on Python/Gnome integration)

Links to 2ManDVD
```
http://www.kde-apps.org/content/show.php/2ManDVD?content=99450
```
(KDE App / QT4)
 I have had a really bad experiences installing from PPA.
So I carefully install the deb nowadays.
The program itself is great, really easy to use and looks awesome.
Lots of options, a bit crashy at times, but definitely better than Kdenlive.
Now, all I need is camera :d

---

### Post by juancarlospaco on 2009-12-13
+1 OpenShot

---

### Post by zoodayz on 2009-12-13
Thanks for the heads up on the OpenShot looks like a nice project tho a little to buggy for me.  Tho everyones mileage may differ. cheers m8

---

### Post by loveandequality on 2009-12-13
Is hard to install.

---

### Post by Keyper7 on 2009-12-13
> **loveandequality said:**
> Is hard to install.

Which one? OpenShot recently got a new, experimental PPA that allows for easy installation without conflicting with anything you have. 2ManDVD requires compilation if you download it from the official site, but some sites make deb packages available.

---

### Post by Warpnow on 2009-12-13
I just installed Openshot from the deb files on the site. I tried to import an avi. It imported, tried to play it, crackling in the audio, I tried to skip ahead. Openshot crashed.

Hrmm...I don't see how this video editor is better than any of the other subpar editors.

---

### Post by Keyper7 on 2009-12-13
> **Warpnow said:**
> I just installed Openshot from the deb files on the site. I tried to import an avi. It imported, tried to play it, crackling in the audio, I tried to skip ahead. Openshot crashed.

Hrmm...I don't see how this video editor is better than any of the other subpar editors.

Strange, I'm throwing different avis, flvs and mpegs and OpenShot at the timeline and moving the playhead everywhere and it doesn't crash. Probably something to do with library versions. You should run it from the terminal and see which error messages you get.

Anyway, don't be so quick to judge OpenShot based on a single personal crash experience. [This video](http://www.youtube.com/watch?v=ECoWSHRQzME) should give you a good idea of its capabilities and user-friendliness. The developers have stabilization as a priority before the 1.0 release.

---

### Post by Jose Catre-Vandis on 2009-12-13
Just carried out the install.

Already had ffmpeg and x264 installed from SVN/GIT so the two debs included in the dependencies failed to install. But Openshot installed OK and it runs. Yet to test it out in the field though.

---

### Post by daverich on 2009-12-13
Kdenlive is hugely better than it was - install the version from their website - it really is very very good now.

Kind regards

Dave Rich

---

### Post by Mustard on 2009-12-13
I tried openshot very briefly.  I already had ffmpeg et al compiled from source, so only needed to install one of the supplied dependencies.

  When I added a video file, cpu usage shot up and it seemed to be doing very little other than eating cpu time.  Eventually I killed the program and uninstalled.  I'll revisit it at another date I think. :)

---

### Post by Keyper7 on 2009-12-13
> **Mustard said:**
> I tried openshot very briefly.  I already had ffmpeg et al compiled from source, so only needed to install one of the supplied dependencies.

  When I added a video file, cpu usage shot up and it seemed to be doing very little other than eating cpu time.  Eventually I killed the program and uninstalled.  I'll revisit it at another date I think. :)

You might have hit a known ALSA-related bug. Did you have the package libsdl1.2debian-pulseaudio?

---

### Post by MaxIBoy on 2009-12-13
> **daverich said:**
> Kdenlive is hugely better than it was - install the version from their website - it really is very very good now.

Kind regards

Dave Rich
I pull from their SVN repo. Indeed it is better than it once was, but it still crashes occasionally, and even worse, a lot of the output is not accurate (timing is off, clips moving around on you randomly, etc.) I can see it actively getting better in real time, but it has a ways to go.

---

### Post by azangru on 2009-12-13
Since I have cr@ppy hardware, I'm not checking out these video editors myself, but out of curiosity - can you record sound in any of the Linux video editors directly, like you can in Adobe Premiere or in Apple iMovie, or do you have to import sound files and then arrange them along the audio tracks?

---

### Post by SunnyRabbiera on 2009-12-13
Noth Kdenlive and Pitivi are shaping up nicely, they are still shaky around the edges yes but they are slowly but surely improving over time.

---

### Post by Mustard on 2009-12-14
> **Keyper7 said:**
> You might have hit a known ALSA-related bug. Did you have the package libsdl1.2debian-pulseaudio?

I'll try that out.

---

### Post by daverich on 2009-12-14
> **MaxIBoy said:**
> I pull from their SVN repo. Indeed it is better than it once was, but it still crashes occasionally, and even worse, a lot of the output is not accurate (timing is off, clips moving around on you randomly, etc.) I can see it actively getting better in real time, but it has a ways to go.

ah yes,- you must make sure the settings for your project are correct,- i.e. resolution and fps.

for some reason it doesn't just automatically use the imported video settings.

Kind regards

Dave Rich

---

