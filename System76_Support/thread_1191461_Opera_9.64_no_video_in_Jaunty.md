---
title: "Opera 9.64 no video in Jaunty"
date: 2009-06-19
forum: System76 Support
---

### Post by solotwit on 2009-06-19
Anybody try using this version in Jaunty? I can't get video streaming, I have all plugins needed I think.

---

### Post by thomasaaron on 2009-06-19
Not sure what flash plugin it is that you are using... flashplugin-alternative. Is that gnash?

Try installing the 64-bit plugin from adobe. Instructions follow...
> 
1. Shut down Opera

2. Run the following commands from a terminal...

sudo apt-get remove flashplugin-*
sudo apt-get remove nspluginwrapper

3. Click the link at the very bottom of this page...
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
...to download the latest 64-bit Flash plugin. Save it to your Desktop and extract it to your Desktop.

4. Run these commands from the terminal...
mkdir -p .mozilla/plugins
mv ~/Desktop/libflashplayer.so .mozilla/plugins

5. Restart Firefox

---

### Post by solotwit on 2009-06-19
Okay, works great. Thank you! 

I just had to help opera find the right plugin path after step 5.

Ignore the thumbnail.

---

### Post by solotwit on 2009-06-21
Well, flash suddenly started to stop playing after a second or two. In both FF and Opera. I can't get a youtube video to play at all beyond a second or two. ?

---

### Post by Chris85HH on 2009-06-21
you are using the 64bit-edition, right?

so remove all your flash-plugins at first (for example "flashplugin-nonfree"), extract the data from the link thomasaaron told you and put the **libflashplayer.so** to this location: **/usr/lib/opera/plugins/** (as root)

than it should work.

---

### Post by solotwit on 2009-06-21
so I have flashplayer10 installed correctly, I removed all other flash players first, then installed it. I can watch hulu just fine in both FF and opera. but youtube vids load up with a black box but do not play, no video or sound. Whats up with that?

---

### Post by Chris85HH on 2009-06-22
did you follow my instruction?
i did it that way and youtube etc. works perfect in opera.

what did you mean with "installed correctly"? ... did you use an deb-data to install or something like that?, cause this could not work, because the deb-data is just for the 32bit edition.

---

### Post by solotwit on 2009-06-22
I did what thomasaaron said, and it didn't work in FF or opera. I then did this which came from another thread on here.

1.

sudo apt-get remove --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash 
sudo apt-get remove --purge swfdec-mozilla libflashsupport nspluginwrapper iceape-flashplugin 
sudo apt-get remove --purge iceweasel-flashplugin mozilla-flashplugin firefox-flashplugin 
sudo apt-get remove --purge xulrunner-flashplugin midbrowser-flashplugin xulrunner-addons-flashplugin
sudo rm -f /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/firefox/plugins/npwrapper.libflashplayer.so
sudo rm -f /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so
sudo rm -f ~/.mozilla/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/firefox-addons/plugins/npwrapper.libflashplayer.so
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -f /usr/lib/mozilla/plugins/*flash*

2.

sudo wget [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz)

3.

sudo tar xzf libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz

4.

sudo mv libflashplayer.so /usr/lib/mozilla/plugins

 I think I'm just gonna go back to the gnash 32bit emulator one, cuz that actually worked in FF. THanks anyways.

---

### Post by maria-n on 2009-06-22
Followed the instructions by thomasaaron exactly (copy and paste :-) ) and now Youtube works in FF, which is great (thanks Thomas!) 
But I don't know how to make Opera find it. After uninstalling the other flash plugins, Opera now reports the flash player missing, instead of using the new one.

In preferences-advanced-plugins Opera doesn't find the new plugin if I use "find new" button.

Can anyone tell me how to make the player work in Opera?

---

### Post by solotwit on 2009-06-22
Maybe I'll switch to 7.10.

I went to

Tools
 Preferences
   Advanced
    selected Content
     Plugin Options
      Change Path
       Add
then went to usr/lib/mozilla plugins

Still didn't work for me, but maybe if I use 7.10.

---

### Post by solotwit on 2009-06-30
Aha, I deleted files from my root folder and made more room in root and now youtube streams fine.

[http://ubuntuforums.org/showthread.php?t=1193733&page=3](http://ubuntuforums.org/showthread.php?t=1193733&page=3)

---

### Post by Abdus on 2009-07-09
thomasaaron's answer (2nd post) was enough to solve my problem, it now works in Opera as well as in Firefox (I had to point Opera to another plugins location, which is easily done using Opera Preferences menu, though).

Any way to make the 64 bit plugin update itself without user's help after this solution?

---

### Post by thomasaaron on 2009-07-09
Not that I'm aware of. But it's easy enough to change out. Just delete the libflashplayer.so and pop in a new one.

---

