---
title: "Wireless media streaming"
date: 2008-06-10
forum: The Cafe
---

### Post by jonwestin on 2008-06-10
Hey. I wanna set up an audio streaming device at home, to play my music collection on my stereo without all the cables. Does anyone know a model that works with Ubuntu? Or should I just get another comp and set up a Media center instead? Im not too much into this stuff yet so any advice would be appreciated. 

Cheers
/jon

---

### Post by nothingspecial on 2008-06-11
Squeezebox with squeezecenter.

[http://www.slimdevices.com/su_downloads.html](http://www.slimdevices.com/su_downloads.html)
[http://www.slimdevices.com/](http://www.slimdevices.com/)

Careful though I got hooked and now I`ve got 3. (kitchen,livingroom and bedroom). You can sync them or have them playing different stuff at the same time. 
 They support radio (podcasts,listenagain etc) and there are loads of plugins.

---

### Post by jonwestin on 2008-06-11
> **nothingspecial said:**
> Squeezebox with squeezecenter.

[http://www.slimdevices.com/su_downloads.html](http://www.slimdevices.com/su_downloads.html)
[http://www.slimdevices.com/](http://www.slimdevices.com/)

Careful though I got hooked and now I`ve got 3. (kitchen,livingroom and bedroom). You can sync them or have them playing different stuff at the same time. 
 They support radio (podcasts,listenagain etc) and there are loads of plugins.

Hey man. Yeah, i had a look at that. Does it work with Ubuntu? What would be the difference from setting up a computer with Media Center?

---

### Post by jonwestin on 2008-06-12
I've been looking around and Im thinking about buying a stationary computer and setting it up with either XBMC or Linux MCE, but Im not sure if that gives me the ability to stream via my laptop..?

---

### Post by jonwestin on 2008-06-16
bumping this a little

---

### Post by Harris2508 on 2008-06-29
Pardon if I jump in here. I've been using SqueezeCenter on a Windows box for quite awhile and it works very well. I'm in the process of setting up Ubuntu 8.04 to do some (or all) of this audio streaming. The SqueezeCenter software hangs about half way through the installation. I've seen mention in the SlimDevices site about modifying the "sources.list" file, but a) I'm not sure that's a good idea and 2)Ubuntu says I don't have the permissions anyway.

Any ideas on how I can get SqueezeCenter into this Ubuntu box? Any thoughts would be greatly appreciated.

Thanks a lot.

--Bob Harris

---

### Post by zmjjmz on 2008-06-29
Harris: You need to have root permissions to edit sources.list, as it's not in your home folder.
Do this 
```
sudo gedit /etc/apt/sources.list
```
Of course, you can do it the easier, GUI, way and open up System > Administration > Software Sources.
Open up the tab called Third Party Software, click "Add", and copy/paste the apt line (should be a url preceded by deb and followed by hardy) into it.
"Add Source" should do the trick. I believe you either have to then check the corresponding box in the list of sources it gives you and then reload, or just reload (it will prompt you to reload after closed, if not do ```
sudo apt-get update
```

---

### Post by nothingspecial on 2008-06-30
To install squeezecenter, add
```

deb http://debian.slimdevices.com stable main
```

to your software sources, reload then it will be in synaptic or you can apt-get it.

Once it`s done open up firefox and go to [http://localhost:9000/](http://localhost:9000/) and squeezecenter will start. Setting it up is very straight forward.

The only issue will be if you have any m4a files from using iTunes in a previous life. If this is the case -
```

cd /etc/squeezecenter/
sudo gedit custom-convert.conf
```

then copy and paste these lines in -

```
ape wav * *
	[mplayer] -novideo -ao pcm:nowaveheader:file=/dev/fd/4 $FILE$ 4>&1 1>/dev/null
alc wav * *
	[mplayer] -novideo -ao pcm:nowaveheader:file=/dev/fd/4 $FILE$ 4>&1 1>/dev/null
mov wav * *
	[mplayer] -novideo -ao pcm:nowaveheader:file=/dev/fd/4 $FILE$ 4>&1 1>/dev/null
```

Then ```
sudo apt-get install mplayer
``` if you don`t have it already.

Finaly ```
sudo /etc/init.d/squeezecenter restart
```

and you should be good to go.

---

### Post by jjdarling on 2008-08-14
I've installed squeezecenter and it seemed to install and run with now problems, however, when I direct my browser to [http://localhost:9000/](http://localhost:9000/) Firefox gives me the "Page load Error" message. I have restarted squeezecenter as described above and it doesn't help.

EDIT: This problem seemed to have worked itself out (I didn't change anything but it started working a few days later). Feel free to post if you have any idea why this might have happened.

---

### Post by jjdarling on 2008-08-26
So I finally acquired a Squeezebox and got it all working (aside from minor amplifier problems), but unfortunately I only have about half my library playing. I ran the fix that nothingspecial posted above, but it didn't seem to do anything. Any ideas on how I could fix this?

---

