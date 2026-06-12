---
title: "Cannot play videos using Firefox - Daru3"
date: 2009-02-10
forum: System76 Support
---

### Post by arepaking on 2009-02-10
Hello All,
I cannot play neither videos nor animations using Firefox. I read some post about installing some plugins (such as flashplugin-nonfree,etc..) and I followed those instructions without being able to get this thing work.

I also tried to manually install the adobe flash 10 player ([http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)) , but, when I double click the debian file I get this error: [COLOR="Red"]ERROR WRONG ARCHITECTURE i386.[/COLOR]


I am using Ubuntu 8.10 64bits.

Does anyone knows how to overcome this issue? Thank you very much in advance,

-AK

---

### Post by thomasaaron on 2009-02-10
Follow these instructions, and then you should be able to play videos (youtube for example)...

[http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats)

---

### Post by arepaking on 2009-02-10
> **thomasaaron said:**
> Follow these instructions, and then you should be able to play videos (youtube for example)...

[http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats)

Hi thomasaaron,
Thank you very much for your quick response.

I followed the instructions and the only thing that I haven't tried was executing the following command:

```
sudo apt-get install libdvdcss2 w64codecs
```

This resolved my problem.

Thank you very much!
-AK

---

### Post by demarshall on 2009-02-10
I'm running 32 bit Kubuntu Intrepid and followed the procedure at the link that you gave thomasaaron but I still cannot play YouTube videos. Any suggestions?

---

### Post by thomasaaron on 2009-02-10
Instead of installing Ubuntu Restricted Extras on that link. Install Kubuntu Restricted Extras.

If you did that, and it still doesn't work...

sudo apt-get --reinstall install flashplugin-nonfree

---

### Post by demarshall on 2009-02-10
Sorry, I posted my question in the wrong forum. I found what I thought was a similar problem and didn't even notice which forum it was in until after I posted it. I don't even know what System76 is.

BTW The reinstall idea made the audion work but I get blank white screen where the video player should be now.

---

### Post by Guille Damke on 2009-02-10
To solve this, I think you should install the new flashplayer.
At least in Ubuntu-64 bit (my guess is that the only difference is that you install the 32-bit version instead of 64-bit)
Uninstall the current flashplugin:
```
sudo apt-get purge flashplugin-nonfree
```
Download the version of flash and untar it in a folder. I think from here.
[HTML]http://get.adobe.com/flashplayer/[/HTML]
After extracting it into a folder, copy libflashplayer.so to mozilla plugins:
```
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
```
Finally, I deleted a broken link in this last directory, which you can check doing ```
ls -la /usr/lib/mozilla/plugins
```. 
You will see that "npwrapper.libflashplayer.so -> /var/lib/flashplugin-nonfree//npwrapper.libflashplayer.so' appears in red. To delete it:
```
sudo rm /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
```

That worked for me.
Anyway, I would check this for Kubuntu-32 bits.

---

### Post by Lee_Machine on 2009-02-11
To install flash in gnome the best way is to go to Add/Remove Programs and search for flash. Then install Macromedia Flash plugin. It will then install the newest Flash 10 player, even for 64 bit. 

It's always best to start using the GUI's at much as possible. 

I had an issue with full screen while watching movies on Hulu. So I just uninstalled the old on and installed the new one using add/remove programs. It will delete anything that needs deleting and install the new one.

Use CL as little as you can. 90% of things should be done via GUI. This will also help get rid of all the misinformed people that think everything in Linux needs to be done in the command line.

---

### Post by Guille Damke on 2009-02-11
Lee Machine, I did not know that now you get Flash 10 for 64-bit installed that easy. The last time I did it I had troubles with videos, so I replaced it by the just-released flash player 10 following with I posted before and worked.
Thanks for sharing.
Guille.

---

