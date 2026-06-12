---
title: "Youtube 720p Video is Choppy"
date: 2010-06-24
forum: The Cafe
---

### Post by Shibblet on 2010-06-24
Works great with their 360p and 480p, but when I run 720p in window or fullscreen, I get an unbearable loss of framerate.

I have an Nvidia GTX260 video card, Running the current release Drivers.  

Now, my HD videos play fine in Mplayer.  So I am assuming this is a Flash problem.

Any ideas?

---

### Post by Miguel on 2010-06-24
Troll Adobe until they decide to use at least Xv. Or since you have an nVidia GPU, troll them to create some VDAPU hooks in flash.

Similar to the Mac case until 10.1, flash isn't hardware accelerated in linux. Adobe says that's because the linux video API is a mess. Oh, well, they could create some Xv hooks and then all drivers would have some accel. Or they could use VDAPU and nVidia cards would work great.

---

### Post by dragos240 on 2010-06-24
Flash sucks, especially on linux.

---

### Post by Rodney9 on 2010-06-24
Youtube 720p full screen works well for me.

---

### Post by Lucradia on 2010-06-24
Try turning off hardware acceleration for flash (if you have 10.1):

Right-click the flash object, click settings (not global settings), go to the first tab on the left of the settings. Then uncheck "Enable hardware acceleration."

Some videos are now "purposely" choppy because video cards process them too fast in flash 10.1.

---

### Post by TheNerdAL on 2010-06-24
It's due to Flash sucking and your CPU.

---

### Post by samalex on 2010-06-24
For Youtube I've switched to the HTML5 version, and it works MUCH better than Flash.  Though I think Flash has its place, I agree with Jobs in that HTML5 can and will eventually overtake Flash for such things as audio and video on the web.  

Sam

---

### Post by TheNerdAL on 2010-06-24
> **samalex said:**
> For Youtube I've switched to the HTML5 version, and it works MUCH better than Flash.  Though I think Flash has its place, I agree with Jobs in that HTML5 can and will eventually overtake Flash for such things as audio and video on the web.  

Sam

I wish ALL videos on Youtube are HTML5. :(

---

### Post by Johnsie on 2010-06-24
Flash > Html5

Steve Jobs just wants to stop people developing flash apps that run in a browser, thus bypassing the Apple market place.

---

### Post by samalex on 2010-06-24
> **TheNerdAL said:**
> I wish ALL videos on Youtube are HTML5. :(

That's true, but I hear they're working on it.

> **Johnsie said:**
> Flash > Html5

Steve Jobs just wants to stop people developing flash apps that run in a browser, thus bypassing the Apple market place.

HTML5 is still in flux, but I bet the final version will be quite impressive.  But from what I've seen with HTML5 it's VERY impressive and will give Flash, Silverlight, and Moonlight a run for their money.

Sam

---

### Post by Lucradia on 2010-06-24
> **TheNerdAL said:**
> I wish ALL videos on Youtube are HTML5. :(

Plus, HTML5 can do easter eggs. Which I didn't know it could do.

[http://smokescreen.us/demos/sb45demo.html](http://smokescreen.us/demos/sb45demo.html)

But if you notice, it can be a bit choppy.

---

### Post by lovinglinux on 2010-06-24
You could use [FlashVideoReplacer](https://addons.mozilla.org/en-US/firefox/addon/161869/) extension to replace flash with another plugin.

Also see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

