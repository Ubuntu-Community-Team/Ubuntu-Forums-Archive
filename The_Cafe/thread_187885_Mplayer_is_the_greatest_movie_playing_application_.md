---
title: "Mplayer is the greatest movie playing application to have ever hit our universe."
date: 2006-06-03
forum: The Cafe
---

### Post by michaeljb2005 on 2006-06-03
Mplayer is the greatest movie playing application to have ever hit our universe.

---

### Post by iAlta on 2006-06-03
[QUOTE=michaeljb2005]Mplayer is the greatest movie playing application to have ever hit our universe.[/QUOTE]
Great. Where can I get it? 
ps. I dont know how to use apt-get with kde, so dont even think about it.

---

### Post by angkor on 2006-06-03
[QUOTE=iAlta]ps. I dont know how to use apt-get with kde, so dont even think about it.[/QUOTE]

same as you would with gnome:

```
sudo apt-get install mplayer
```

;)

---

### Post by Lord Illidan on 2006-06-03
Xine is better, imho... and what about vlc?

---

### Post by curuxz on 2006-06-03
Mplayer and Vlc crash for a past time for me, personaly I use Totem unless I have something it really really cant play then I use mplayer but then I lose the ability to seek using the scroll wheel in totem which I love being able to do.

---

### Post by angkor on 2006-06-03
[QUOTE=curuxz]but then I lose the ability to seek using the scroll wheel in totem which I love being able to do.[/QUOTE]

what do you mean? I can use the scroll wheel in mplayer to skip forward and backward.

---

### Post by curuxz on 2006-06-03
Can you? does not work for me :( maybe im just being dense.

---

### Post by Rackerz on 2006-06-03
I just checked, Wow. Mplayer is pretty!

---

### Post by Sheinar on 2006-06-03
MPlayer is pretty fantastic, though I really don't like Gmplayer at all.

---

### Post by Scunizi on 2006-06-03
I just tried sudo apt-get install mplayer and it returned with a "not available" or valid package.  I checked synaptic and it's not in there either.  what's UP?

Edit:  All repositories are checked.  There is a kmplayer in synaptic.

---

### Post by greggh on 2006-06-03
I just got mplayer through synaptic with xubuntu earlier today. My friend also said he wasn't able to find it in the repositories using ubuntu. Do different packages show up in synaptic depending on whether you're using ubuntu, kubuntu or xubuntu?

---

### Post by sophtpaw on 2006-06-03
I just like a player that works - don't care what its called. Right now its neither Totem, Mplayer, nor Xine movie player nor Gxine Movie Player. Hven't tried Kaffeine or VLC yet

hmpf...

---

### Post by sapo on 2006-06-03
I just wrote a MPlayer Compilation HowTo for dapper:

[http://ubuntuforums.org/showthread.php?t=187709](http://ubuntuforums.org/showthread.php?t=187709)

The only problem is that i still didnt get how to make x264 codec work with it, maybe you guys could help me out :mrgreen:

---

### Post by Perfect Storm on 2006-06-03
Did you tried pointing it to libx264-dev?

---

### Post by sapo on 2006-06-03
[QUOTE=Artificial Intelligence]Did you tried pointing it to libx264-dev?[/QUOTE]
I installed the libx264-dev and even compiled the x264 from source, but mplayer couldnt find it, how can i force mplayer to detect it?

---

### Post by shrimphead on 2006-06-03
custom compiled, command line mplayer all the way :D

I fully agree with the OP, best media player ever

---

### Post by jdong on 2006-06-03
Mplayer is the media guru's swiss army knife 2.0 :)


Sure it's ugly, gruesome, and unrefined, but if any media player is going to read that mystery format file, it'll be mplayer...

From the man page:
> 
       # I love practicing handstands while watching videos.
       flip=yes



Not only is is a player, it's also a transcoder. The only other package that comes close to mplayer's feature set is VLC, but VLC is somewhat shakier at support than mplayer.



I do use Totem or Xine as much as possible... I like their interfaces better for daily use. But that transcoding job or that weird 3DS Max rendered video that nobody can figure out how to do... mplayer is well worth the investment of time and patience :)

---

### Post by shrimphead on 2006-06-03
[QUOTE=Scunizi]I just tried sudo apt-get install mplayer and it returned with a "not available" or valid package.  I checked synaptic and it's not in there either.  what's UP?

Edit:  All repositories are checked.  There is a kmplayer in synaptic.[/QUOTE]

you need to install the mplayer specific to your architecture, try:

sudo apt-cache search mplayer

or 

sudo apt-get install mplayer-686 (providing you have a 686 of course)

---

### Post by Somenoob on 2006-06-03
I find VLC to be the fastest, but Mplayer is good as well.

---

### Post by polo_step on 2006-06-03
[FONT="Courier New"]I'd be grateful for any player that would simply work.

In 5.04 [spit!] I spent months trying to get proper playback with any player.  The best I could ever do was to get gxine to play with creeping A/V synchronization loss.  Every few minutes, I'd have to hit pause and restart so the mouths could catch up with the dialog.  No one here could ever figure it out, either.

Never tried in 5.10.[/FONT]

---

### Post by xmastree on 2006-06-04
Nah, mplayer sucks. Tried viewing full screen? Sure, the app fills the screen but the video is still tiny in the centre.

---

### Post by Sheinar on 2006-06-04
[QUOTE=xmastree]Nah, mplayer sucks. Tried viewing full screen? Sure, the app fills the screen but the video is still tiny in the centre.[/QUOTE]
It has never done that to me.

---

### Post by xmastree on 2006-06-04
Here's a sample:
[ATTACH]10538[/ATTACH]
That's a 720x480 WMV.
See the original here:
[http://www.trackvision.net/videos/WebsterLagunaSeca.wmv](http://www.trackvision.net/videos/WebsterLagunaSeca.wmv)

---

### Post by Sheinar on 2006-06-04
Tried it and the video played full-screen for me. Perhaps it's an Ubuntu specific problem, maybe a bug in the MPlayer from the repositories.

---

### Post by FISHERMAN on 2006-06-04
[QUOTE=xmastree]Here's a sample:
[ATTACH]10538[/ATTACH]
That's a 720x480 WMV.
See the original here:
[http://www.trackvision.net/videos/WebsterLagunaSeca.wmv](http://www.trackvision.net/videos/WebsterLagunaSeca.wmv)[/QUOTE]
You can change that somewhere in the options.
Choose preferences=>tab Video=>change the driver(i forgot the correct one)=>close MPlayer=>restart it.

On-topic: I prefer VLC as stand-alone Player. But I do use MPlayer as Firefox plugin and to view video's that are to stubborn to play in VLC.

---

### Post by xmastree on 2006-06-04
ah, that's better. 
Thanks. X11/Xv seems to work better. It was set to X11/(Ximage/Shm)

---

### Post by Perfect Storm on 2006-06-04
[QUOTE=FISHERMAN]You can change that somewhere in the options.
Choose preferences=>tab Video=>change the driver(i forgot the correct one)=>close MPlayer=>restart it.

On-topic: I prefer VLC as stand-alone Player. But I do use MPlayer as Firefox plugin and to view video's that are to stubborn to play in VLC.[/QUOTE]


Same here. VLC play most of things I throw at it. Only in very rare occasion I've to use Mplayer or other.
But I use Mplayer for browser player.

---

### Post by shrimphead on 2006-06-04
[QUOTE=xmastree]ah, that's better. 
Thanks. X11/Xv seems to work better. It was set to X11/(Ximage/Shm)[/QUOTE]

mplayer can take a bit of configuring but once you've set up a decent .config file it just works every time.

hint: also you'll want to run 

```
echo 1024 > /proc/sys/dev/rtc/max-user-freq
```

on startup too, this will generally sort out most a/v sync problems

---

### Post by Kimm on 2006-06-04
I use mplayerplug-in as a browserplugin but VLC for other desktop use... I like the interface more

---

### Post by angkor on 2006-06-04
[QUOTE=shrimphead]mplayer can take a bit of configuring but once you've set up a decent .config file it just works every time.

hint: also you'll want to run 

```
echo 1024 > /proc/sys/dev/rtc/max-user-freq
```

on startup too, this will generally sort out most a/v sync problems[/QUOTE]

Do you mean to put this line in .mplayer/config or in the session startup?

Hm, I don't have permission, neither as user nor with sudo.

---

### Post by shrimphead on 2006-06-04
[QUOTE=angkor]Do you mean to put this line in .mplayer/config or in the session startup?

Hm, I don't have permission, neither as user nor with sudo.[/QUOTE]

what I do is create a file in /etc/init.d called mplayer and put that line in it. then make it executable with 
```
sudo chmod +x /etc/init.d/mplayer
```

then you need to create a symbolic link in the /etc/rc.2 (i think) directory that links to the file you just created

```
cd /etc/rc2.d
sudo ln -s S20mplayer /etc/init.d/mplayer
```

the S20 gives the priority of the script in your system startup, now every time your machine boots that line will run and mplayer will work fine.

---

### Post by OffHand on 2006-06-04
I tried most of them... I like VLC the best. Plays almost any video I throw at it.
No sync problems. I like Totem the least.

---

### Post by angkor on 2006-06-04
[QUOTE=shrimphead]
```
cd /etc/rc2.d
sudo ln -s S20mplayer /etc/init.d/mplayer
```
[/QUOTE]

I got this far. When trying to add the link in rc2.d I get:

```
ln: creating symbolic link `/etc/init.d/mplayer' to `S20mplayer': File exists
```

thanks for the help.


Edit:
Ah I think it's the other way around:

```
 sudo ln -s /etc/init.d/mplayer s20mplayer
```

I'll reboot and see what it does.

thanks again

---

### Post by shrimphead on 2006-06-04
[QUOTE=angkor]
Ah I think it's the other way around:

```
 sudo ln -s /etc/init.d/mplayer s20mplayer
```

I'll reboot and see what it does.

thanks again[/QUOTE]

sorry that's my bad, I always get the arguments of ln the wrong way round, and I'm not on my ubuntu box at the moment to check ](*,) 

don't forget the capital S otherwise the system won't recognize it as a startup script.
should be ```


sudo ln -s /etc/init.d/mplayer S20mplayer
```

---

### Post by angkor on 2006-06-04
[QUOTE=shrimphead]sorry that's my bad, I always get the arguments of ln the wrong way round, and I'm not on my ubuntu box at the moment to check ](*,) 

don't forget the capital S otherwise the system won't recognize it as a startup script.
should be ```


sudo ln -s /etc/init.d/mplayer S20mplayer
```[/QUOTE]

Very nice! This is the first time in all my years of using mplayer I see it start up without that error. Thanks, shrimphead! 

This made mplayer even better, I think. :) What does this line do? Improve audio sync?

---

### Post by shrimphead on 2006-06-04
[QUOTE=angkor]Very nice! This is the first time in all my years of using mplayer I see it start up without that error. Thanks, shrimphead! 

This made mplayer even better, I think. :) What does this line do? Improve audio sync?[/QUOTE]

glad to help :D

I believe it increases the resolution of the real time clock, meaning it can sync frames with greater accuracy, not 100% certain tho.

If you want better performance from mplayer, compile from source and use checkinstall to make your own (simple) .deb specific to your architecture.

that way you can disable run time cpu detection (and a lot of other mostly useless stuff that the repo deb is built with).  This will make mplayer start up faster.

although there are a lot of build dependancies for mplayer and I can't remember what most of them are :-?

EDIT: sorry if that sounds a bit patronising, I just noticed you said you'd been using mplayer for years :S

---

### Post by angkor on 2006-06-04
[QUOTE=shrimphead]EDIT: sorry if that sounds a bit patronising, I just noticed you said you'd been using mplayer for years :S[/QUOTE]

Not at all. :) 

I used to compile it from source on Debian but ever since I had mplayer in the repos in Ubuntu I took the easy way out. Maybe I'll do that to see if it improves. It does work very nice atm though.

---

### Post by shamrock_uk on 2006-06-04
[QUOTE=angkor]Not at all. :) 

I used to compile it from source on Debian but ever since I had mplayer in the repos in Ubuntu I took the easy way out. Maybe I'll do that to see if it improves. It does work very nice atm though.[/QUOTE]

Sorry, this may also be a bleeding obvious point if you've been using it for years, but provided you have the source repositories enabled, if you do sudo apt-get build-dep mplayer then it'll pull in the dependencies for you. 

Then, when you go to compile it yourself, it's hassle free :)

---

### Post by angkor on 2006-06-05
[QUOTE=shamrock_uk]Sorry, this may also be a bleeding obvious point if you've been using it for years, but provided you have the source repositories enabled, if you do sudo apt-get build-dep mplayer then it'll pull in the dependencies for you. 

Then, when you go to compile it yourself, it's hassle free :)[/QUOTE]

Thanks, that helped. Used to be a pain in the *** to compile it. I used your build dep suggestion and [this howto]("http://www.ubuntuforums.org/showthread.php?t=187709"). Compiled fine and plays anything I've tried so far.

---

### Post by Kza on 2006-06-10
The main reason I prefer mplayer to the others is that I can start it by sshing in from the laptop near the couch and press butons in the ssh window to switch on and off the OSD, subtitles, pause it, go back and forward in the video etc. Every other player I have to get up and use the GUI on the main computer.

But I use totem for dvds / dvd isos in case there is a menu i need to click on which mplayer cant handle.

---

### Post by patrick295767 on 2006-06-10
[QUOTE=xmastree]Nah, mplayer sucks. Tried viewing full screen? Sure, the app fills the screen but the video is still tiny in the centre.[/QUOTE]
  
I would recommand you to check : 
man mplayer 
( mplayer -fullscreen -zoom sthg)
  
You can do so much things with it !
  
This is funny : 
press ALT CTRL F1
mplayer -vo aa myvideo.avi
:-) 

Greetz

---

