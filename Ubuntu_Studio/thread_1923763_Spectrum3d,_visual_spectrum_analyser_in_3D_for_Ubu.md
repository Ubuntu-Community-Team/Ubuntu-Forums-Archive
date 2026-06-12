---
title: "Spectrum3d, visual spectrum analyser in 3D for Ubuntu"
date: 2012-02-11
forum: Ubuntu Studio
---

### Post by victor-be on 2012-02-11
Hello

I'd like to (re-)introduce Spectrum3d, a visual spectrum analyser in 3D. It has been review in Linux Journal : [http://www.linuxjournal.com/content/short-notices-news-linux-audio]("http://www.linuxjournal.com/content/short-notices-news-linux-audio")

[ATTACH]212494[/ATTACH]

[ATTACH]212495[/ATTACH]

The new version should work smoother. It is now available in a ppa for easy installation in Ubuntu :

[https://launchpad.net/~nadaeck/+archive/spectrum3d]("https://launchpad.net/~nadaeck/+archive/spectrum3d")

The sources are on Sourceforge : 

[https://sourceforge.net/projects/spectrum3d/files/]("https://sourceforge.net/projects/spectrum3d/files/")

---

### Post by marin123 on 2012-02-13
It looks like nice piece of software, but when I try to analyse something it crashes...
This is terminal output:
```
marin@marincelo:~$ spectrum3d
Spectrum3d 2.1.0 
Please report any bug to nadaeck@hotmail.com
Getting saved rom rc file
WARNING : RC file doesn't exist or cannot be open; this is normal if you run Spectrum3d for the first time; 

(spectrum3d:3029): Gtk-CRITICAL **: IA__gtk_image_set_from_stock: assertion `GTK_IS_IMAGE (image)' failed
Showing Gtk GUI
Uri of selected_file = file:///home/marin/Desktop/clip.wav
playFromSource
*** Checking if JACK is running (Jack error messages are normal):
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
*** --> OK, JACK is not running
Now playing
Segmentation fault

```

Any idea why I get "Segmentation fault" and then a crash?

---

### Post by jejeman on 2012-02-13
> Any idea why I get "Segmentation fault" and then a crash? 
probably because
> *** --> OK, JACK is not running

---

### Post by victor-be on 2012-02-13
> probably because

*** --> OK, JACK is not running 

No this "error message" is normal; it is just a security message. When an audio stream is started, a check is done to see if Jack is running; when Jack is not running, it generates an error message that I cannot prevent to be displayed.

If you are using Ubuntu 11.10, this is most probably this is due to a bug in the gstreamer0.10-plugins-good (version 10.30).
The most easy solution is to use the 10.28 version that was used in Ubuntu 11.04 (Natty Narwhal).
For this, enable repository of gstreamer0.10-plugins-good for Natty in Synaptic (find it here). Then reload, select 'gstreamer0.10-plugins-good', go to Package  -> Force version, choose the 0.10.28 version; then it should work right away.  You should then go to Package  -> Lock version; this will prevent the 0.10.28 to be updated to 0.10.30 again next time you update your packages.

As said [here]("https://sourceforge.net/p/spectrum3d/discussion/general/thread/1d4a096c/8548/"), there are more complicated solutions, like installing an older version from sources or the developpment version from Git (the bug seems resolved there too), but I don't think it is necessary

Please let me know if it works

Victor

---

### Post by marin123 on 2012-02-13
> **victor-be said:**
> No this "error message" is normal; it is just a security message. When an audio stream is started, a check is done to see if Jack is running; when Jack is not running, it generates an error message that I cannot prevent to be displayed.

If you are using Ubuntu 11.10, this is most probably this is due to a bug in the gstreamer0.10-plugins-good (version 10.30).
The most easy solution is to use the 10.28 version that was used in Ubuntu 11.04 (Natty Narwhal).
For this, enable repository of gstreamer0.10-plugins-good for Natty in Synaptic (find it here). Then reload, select 'gstreamer0.10-plugins-good', go to Package  -> Force version, choose the 0.10.28 version; then it should work right away.  You should then go to Package  -> Lock version; this will prevent the 0.10.28 to be updated to 0.10.30 again next time you update your packages.

As said [here]("https://sourceforge.net/p/spectrum3d/discussion/general/thread/1d4a096c/8548/"), there are more complicated solutions, like installing an older version from sources or the developpment version from Git (the bug seems resolved there too), but I don't think it is necessary

Please let me know if it works

Victor

Fantastic! It works.

I have 64 bit Ubuntu, so I downloaded gstreamer-good-10.28-amd64. Now Synaptic is freaking out, but it's ok :)
It works pretty smooth, very nice application.

---

