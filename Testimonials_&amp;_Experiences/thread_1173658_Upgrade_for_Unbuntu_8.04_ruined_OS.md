---
title: "Upgrade for Unbuntu 8.04 ruined OS"
date: 2009-05-30
forum: Testimonials &amp; Experiences
---

### Post by richg on 2009-05-30
I use removable hard drives. I slipped in the one for Ubuntu 8.04 I have not used for some weeks. Updates were waiting so I downloaded them. Told to restart PC so I did. Everything look ok so I went to click on the shutdown icon and both bottom panels disappeared. I had to push the switch on the power supply to shut down. No start icon, nothing on the desktop. What a stupid way to get me to install a new operating system. 
Next time please broadcast, the x.xx OS is no longer supported. I had to put in another OS which took quite a bit of time and it is not Ubuntu anymore. Fortunately, all my files are on an external hard drive. That was really a dirty trick. Go ahead, have a good laugh.

Rich

---

### Post by Sef on 2009-05-30
> Next time please broadcast, the x.xx OS is no longer supported.8.04 is still supported.

> Go ahead, have a good laugh.No one is laughing.

>  I had to put in another OS which took quite a bit of time and it is not Ubuntu anymore. Use the os that you feel is best for you.

---

### Post by richg on 2009-05-30
My Ubuntu 8.04 ended up useless after the last update. A desktop with no where to go. There were no panels, no way to see how I could select an application. I generally go with the defaults and do not mess with the OS. I do not like working under the hood. Fortunately I had another hard drive handy so I could use my PC.
No start button, just the standard 8.04 brown desktop that was useless. With all the Linux OS systems I have had, never had anything like this happen before.

Rich

---

### Post by MartyBuntu on 2009-05-30
I would have just restored my drive image.

---

### Post by moster on 2009-05-30
Something similar happend to me on ubuntu 8.10. I was so mad that I went on windows for a while... But I came back eventually. It seems that on mission critical systems, it is wise to update only critical updates. Recomended updates are just recomended. At least, I know how you feel :(

In your place, I would make fresh install on every new Ubuntu an do only critical updates. If you do not install 9.4 yet, do it. You will not be sorry, every new one is little more polished.

---

### Post by longtom on 2009-06-01
My 8.04 works fine the way I have it - so I switched of the updates.  Also they shouldn't be, they appear to be an occasional source of trouble.

Other solution is, to make an image of your drive before you get updates going.  Not a bad idea to have that ready in any case...

---

### Post by vikramaditya on 2009-06-01
Did you try restoring the default panels?  Alt F2, check "use terminal" box, then:
```
gconftool-2 &#8211;shutdown

rm -rf ~/.gconf/apps/panel

pkill gnome-panel
```

---

