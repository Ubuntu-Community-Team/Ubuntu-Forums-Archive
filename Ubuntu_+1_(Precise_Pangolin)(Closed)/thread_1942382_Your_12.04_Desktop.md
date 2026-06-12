---
title: "Your 12.04 Desktop"
date: 2012-03-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by neu5eeCh on 2012-03-17
This may not belong here, but it interests me to see what others are doing with their 12.04 desktops - gives me an idea what can be done and what does and doesn't work in the latest Unity.

[IMG]http://poemshape.files.wordpress.com/2012/03/desktop.jpg[/IMG]

---

### Post by mcellius on 2012-03-17
Here's mine:

---

### Post by wojox on 2012-03-17
Me
[http://ubuntuforums.org/attachment.php?attachmentid=214021&d=1331345493](http://ubuntuforums.org/attachment.php?attachmentid=214021&d=1331345493)

---

### Post by neu5eeCh on 2012-03-17
> **wojox said:**
> Me
[http://ubuntuforums.org/attachment.php?attachmentid=214021&d=1331345493](http://ubuntuforums.org/attachment.php?attachmentid=214021&d=1331345493)

Is this Unity with Emerald? Or Gnome fallback with Emerald?

---

### Post by wojox on 2012-03-17
Unity with Emerald. It's a little wonky. :p

---

### Post by neu5eeCh on 2012-03-17
> **mcellius said:**
> Here's mine:


Nice. Something I would like to do with mine is to somehow remove the edge altogether (from the launcher icons). I can remove the "back lighting" with myunity but not the edges.

---

### Post by neu5eeCh on 2012-03-17
> **wojox said:**
> Unity with Emerald. It's a little wonky. :p

Yeah... I want to run Emerald eventually, but I think I'll wait until 12.04 is out of Beta and the pros have spelled out the steps. Did you use the steps described [here]("http://ubuntuforums.org/showthread.php?t=1870792")?

---

### Post by wojox on 2012-03-17
> **VTPoet said:**
> Did you use the steps described [here]("http://ubuntuforums.org/showthread.php?t=1870792")?

Yes, with the exception of using the 0.9.5 package.

---

### Post by mcellius on 2012-03-19
> Nice. Something I would like to do with mine is to somehow remove the  edge altogether (from the launcher icons). I can remove the "back  lighting" with myunity but not the edges.

You need to replace the following icons in /usr/share/unity/5/ with blank icons:

launcher_icon_back_54.png
launcher_icon_edge_54.png
launcher_icon_glow_62.png
launcher_icon_shadow_62.png
launcher_icon_shine_54.png

(This is for Precise: in Oneiric, the folder was /usr/share/unity/4/ and there were only four icons to replace as there was no launcher_icon_shadow_62.png.)

I downloaded the blank icons - although one can create them easily enough - from this article: [http://www.omgubuntu.co.uk/2011/12/how-to-customise-unity-like-never-before/](http://www.omgubuntu.co.uk/2011/12/how-to-customise-unity-like-never-before/) from the first Download button in the article.  You'll also get some other replacement icons there that you won't need, so you can discard the ones that aren't listed above.  Copy one of the icons to launcher_icon_shadow_62.png so you have five instead of four (for Precise), and then copy all five of them to /usr/share/unity/4/.  Logout and then login again, and you'll have no edges or backgrounds around the icons in the launcher.

---

### Post by meborc on 2012-03-19
you guys should refer to this thread - [http://ubuntuforums.org/showthread.php?t=1933740](http://ubuntuforums.org/showthread.php?t=1933740)

many 12.04 users there

new thread every month

---

### Post by ratcheer on 2012-03-19
Since 12.04 is just a Beta testing installation, my desktop is just vanilla except for the wallpaper.

Tim

---

### Post by grahammechanical on 2012-03-19
I have a 12.04 install that I use to try and get 12.04 running as I like it. I am not very experimental. Although I did work out how to manually set up additional background slide shows. I see nothing wrong with doing this.

I also have a 12.04 install that is kept in default condition for running tests to see if it is behaving as it should do. I am planning to create some additional 6GB partitions so that I can test the various versions of Ubuntu in this way.

Regards.

---

### Post by keithpeter on 2012-03-19
Hello All

Like ratcheer I'm using a vanilla Unity, but the reason is lasyness not because this is a beta. I'm the kind of user for whom decent defaults are needed.

Anyone know any desktop extensions or enhancements? I'm using the veerable xpad as a sticky note app. I'd like arbitrary sized icons just on the desktop so that I can see inside documents - the current resize icon adjustment just blows up the thumbnail. I'm finding the 'activity journal' far more useful than I expected, and would like to make that 'disappear' into the desktop to make a sort of activity based pinboard.

---

### Post by oldos2er on 2012-03-19
[http://www.flickr.com/photos/piquant00/6811454520/in/photostream](http://www.flickr.com/photos/piquant00/6811454520/in/photostream)

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-19
My 2 cents:

[http://files.myopera.com/tomica/files/1204desktop.png]("http://files.myopera.com/tomica/files/1204desktop.png")

My Desktop is set to run through Precise's default backgrounds over time. The Launcher is hidden (of course!), Docky is at the bottom with my most used shortcuts (Terminal, System Monitor, text editors, Opera) docked and is set to autohide. Highlight colour is changed from orange to purple.

---

### Post by frogotronic on 2012-04-06
> **wojox said:**
> Unity with Emerald. It's a little wonky. :p

How did you get emerald to work in 12.04?

Thanks,
CH

---

### Post by grandtoubab on 2012-04-06
Hello
[[img]http://pix.toile-libre.org/upload/thumb/1333727966.png[/img]](http://pix.toile-libre.org/?img=1333727966.png)
[http://pix.toile-libre.org/upload/original/1333727966.png](http://pix.toile-libre.org/upload/original/1333727966.png)

---

### Post by jasonsmith01 on 2012-04-06
Here's mine.

[ATTACH]215552[/ATTACH]

---

### Post by neu5eeCh on 2012-04-06
> **jasonsmith01 said:**
> Here's mine.

[ATTACH]215552[/ATTACH]

What are the steps to set up Conky on one's system? Can you lay that out or point me toward a useful resource?

---

### Post by jasonsmith01 on 2012-04-06
> **VTPoet said:**
> What are the steps to set up Conky on one's system? Can you lay that out or point me toward a useful resource?

This thread and it's associated links have helped quite a bit. I must say Conky is a bit tedious but very rewarding in the end.  

[http://ubuntuforums.org/showthread.php?t=867076](http://ubuntuforums.org/showthread.php?t=867076)

Searching Conky (and specifically what you are looking for) ie Conky Time on Google has provided many scripts that one can start from.

The Conky Master is VinDSL, his setup instructions can be found here - [http://ubuntuforums.org/showthread.php?t=1771033](http://ubuntuforums.org/showthread.php?t=1771033)

---

