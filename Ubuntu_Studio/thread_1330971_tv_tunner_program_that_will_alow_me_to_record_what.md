---
title: "tv tunner program that will alow me to record what I watch?"
date: 2009-11-18
forum: Ubuntu Studio
---

### Post by nacho32 on 2009-11-18
on ubuntu 9.10 I use tv time to watch my tv on a old ATI pci wonder ve card , is their a way I can record what I watch?

---

### Post by unamanic on 2009-11-18
It might be a little heavy for you, mythtv does that.  I believe vlc can as well.

---

### Post by lovinglinux on 2009-11-19
I develop a Firefox extension, called [FoxMediaCenter]("http://fmc.isgreat.org"), that allows you to record TV and watch the recording on the fly, among other things.

---

### Post by steveneddy on 2009-11-19
Kaffine - works on Ubuntu

---

### Post by idkfa on 2009-11-19
In xine you can press F1 while watching program. It will save your video in mpeg2 file.

---

### Post by nacho32 on 2009-11-19
well I tried the Kaffine and Xine both failed to detect my card. I do like the Xine it has a very nice gui, I will have to try MythTV again it's been a while and it was a little more then what I really want just veiw click record like WinDVR I use on XP boot, but thanks for the replies.

---

### Post by realzippy on 2009-11-19
Tvtime should run...terminal:

**sudo apt-get install tvtime**

---

### Post by nacho32 on 2009-11-19
> **lovinglinux said:**
> I develop a Firefox extension, called [FoxMediaCenter]("http://fmc.isgreat.org"), that allows you to record TV and watch the recording on the fly, among other things.
I installed your plug in and all the required stuff it asked but still dont, see how to record from tvtime?

---

### Post by Jose Catre-Vandis on 2009-11-19
mplayer and mencoder will do this for analog or dvb. Kaffiene will only do dvb tv.

You can create a script where mplayer will dump the stream (dvb) or mencoder will record the analog tv, and then use mplayer again to view what you have recorded (you'll need a little delay and some cache!)

---

### Post by lovinglinux on 2009-11-19
> **nacho32 said:**
> I installed your plug in and all the required stuff it asked but still dont, see how to record from tvtime?

Open the playlist manager and click the record button, select the recorder settings and click OK. A new entry will be displayed in the PVR list. Select it and click play.

---

### Post by nacho32 on 2009-11-19
> **lovinglinux said:**
> Open the playlist manager and click the record button, select the recorder settings and click OK. A new entry will be displayed in the PVR list. Select it and click play.
I dont get it I installed it but do not see a button on the firefox bar to click? that shows its their?
[IMG]http://files.myopera.com/web4me/albums/663346/3Screenshot.png[/IMG]
[IMG]http://files.myopera.com/web4me/albums/663346/2Screenshot-1.png[/IMG]

---

### Post by lovinglinux on 2009-11-19
Right-click on a toolbar, select "Customize" than drag the FoxMediaCenter button to the bar. This is demonstrated [here](http://fmc.isgreat.org/index.php?option=com_content&view=article&id=47:vt30201&catid=12:vt302&Itemid=112). The [video tutorials](http://fmc.isgreat.org/index.php?option=com_content&view=category&id=12&Itemid=112) on the site are for FoxMediaCenter version 3.0.2. So some things, like the recorder, has changed, but most of the interface and functionality is the same. I will publish new tutorials for the next version release.

---

### Post by nacho32 on 2009-11-20
fantastic that did the trick, great program and great video demo. Thanks now I just have to tweak my video settings

---

### Post by lovinglinux on 2009-11-20
> **nacho32 said:**
> fantastic that did the trick, great program and great video demo. Thanks now I just have to tweak my video settings

You are welcome. Any suggestions to improve the extension will be appreciated.

---

### Post by WisJim on 2012-06-30
Hi, I clicked on the link and was redirected to Newsfudge.com.  :( 

I have been looking for a TV Tuner that will work on my system with no luck.  Ubuntu, UE and Studio all recognize the tuner but none of the programs I install see it.

I have a multiboot system.  Currently Ultimate Edition v3.2, Ubuntu Studio Xfce 4.8 and Vista.  The tuner works fine on Vista.  

Could my problem be that I'm using Xfce instead of Gnome?  Could you point me to an explanation of the difference?

I have yet to try mythtv.  That's next on my list.  Is it probable it too will not work on Xfce?

Mostly, I was wondering about the link redirection.

Whoops.  REALLY old post.  Note to self - look at the date before posting a question.

Thanks for the help already given and yet to come!


> **lovinglinux said:**
> I develop a Firefox extension, called [FoxMediaCenter]("http://fmc.isgreat.org"), that allows you to record TV and watch the recording on the fly, among other things.

---

### Post by lovinglinux on 2012-07-01
This is a very old thread. Please create a new one.

Closing it.

---

