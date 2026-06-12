---
title: "Ubuntu CE upgrade?"
date: 2007-02-12
forum: Ubuntu Christian Edition
---

### Post by shane2peru on 2007-02-12
Hey Jereme,

  I just noticed that the upgrade is out.  I'm downloading the upgrade script as I type.  I was wondering if this would affect my current wine installation?  I'm currently using Ubuntu CE 6.10 version 2.  I have wine working great, and would like to not change it if possible.  Please let me know what you think.  Thanks.

Shane

---

### Post by mhancoc7 on 2007-02-12
Hi Shane,

It should not have any affect if you installed wine using the following sources.

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

However, if you want to be sure then you can do the following.

1. Download the upgrade_me archive.
2. Extract the archive.
3. Open the folder and set nautilus to "Show Hidden Files" (View>Show Hidden Files).
4. Now open the .start file in a text editor.
5. Now do the following.

Change this
```
function install_virtualrosary()
{
    apt-get install --assume-yes "libartsc0"
    apt-get install --assume-yes --allow-unauthenticated "wine"
    dpkg -i ".virtual_rosary/virtual_rosary_ubuntu_1.0_all.deb" 
}
```

to this

```
function install_virtualrosary()
{
    dpkg -i ".virtual_rosary/virtual_rosary_ubuntu_1.0_all.deb" 
}
```

6. Save the file and then run the upgrade_me script lik normal.

If you have any questions just let me know.

God Bless, Jereme

---

### Post by shane2peru on 2007-02-13
Jereme,

Ok, thanks!!!!  Worked like a charm!  I do have wine installed from that source, however I went in  and removed it anyway just to be on the safe side.  I also removed Automatix2 and the Rosary thing just to learn a little and see how to edit the script.  Worked great, and I got a little education too.  Thanks.

Shane

Ps.  I love the Start button!!!  Is there anyway I can change its color?

---

### Post by mhancoc7 on 2007-02-13
> **shane2peru said:**
> Jereme,

Ok, thanks!!!!  Worked like a charm!  I do have wine installed from that source, however I went in  and removed it anyway just to be on the safe side.  I also removed Automatix2 and the Rosary thing just to learn a little and see how to edit the script.  Worked great, and I got a little education too.  Thanks.

Shane

Ps.  I love the Start button!!!  Is there anyway I can change its color?

Great to hear it!

Yes you can change the start button.

Here is a link to a How to that I did a while back.
[http://www.ubuntuforums.org/showthread.php?t=205005&highlight=energy+bliss](http://www.ubuntuforums.org/showthread.php?t=205005&highlight=energy+bliss)

There is info and links there for customizing the Ubuntu Start Button.

There are also some other buttons in some of the other posts in the thread and at gnome-look.org.

Hope that helps, Jereme

---

### Post by shane2peru on 2007-02-14
Jereme,

Ok, those are some awesome screen shots.  I like the blue, I have always like the look of XP, I can't say I have been that impressed with the OS itself, but the look is very nice.  The only thing that worked for me off of those forums was the GDM thing.  Some of the links appear to not be active any longer.  When I try to add the Clearlooks-XP to the **System -> Preferences -> Themes** it says it is the wrong format.  The link for the start button only showed one post that was not very helpful for me.  I need to know what was before and after that post to figure it out.  I love the start button, and will love it more when it is blue, or green!  Thanks for the help, and great themes!

Shane

**Edit:**Ok, scratch what I said about the Clearlooks-XP theme, I just realized my download was not right for some reason or another.  I got it now, I just need the start button fix.  Thanks!

**Edit2:**  Ok, I should get things straight before posting.  :D  also this link is no longer active so I don't have the blue spalsh screen either > Splash Screen: (System > Preferences > Splash Screen)
Ubuntu Splash Blue (attached)
  Thanks.

---

### Post by mhancoc7 on 2007-02-14
> **shane2peru said:**
> Jereme,

Ok, those are some awesome screen shots.  I like the blue, I have always like the look of XP, I can't say I have been that impressed with the OS itself, but the look is very nice.  The only thing that worked for me off of those forums was the GDM thing.  Some of the links appear to not be active any longer.  When I try to add the Clearlooks-XP to the **System -> Preferences -> Themes** it says it is the wrong format.  The link for the start button only showed one post that was not very helpful for me.  I need to know what was before and after that post to figure it out.  I love the start button, and will love it more when it is blue, or green!  Thanks for the help, and great themes!

Shane

**Edit:**Ok, scratch what I said about the Clearlooks-XP theme, I just realized my download was not right for some reason or another.  I got it now, I just need the start button fix.  Thanks!

**Edit2:**  Ok, I should get things straight before posting.  :D  also this link is no longer active so I don't have the blue spalsh screen either   Thanks.


Sorry for the trouble. 

You can get the blue splash here.
[http://ubuntuforums.org/attachment.php?attachmentid=12750&d=1152936010](http://ubuntuforums.org/attachment.php?attachmentid=12750&d=1152936010)

You can get the Start Button here.
[http://ubuntuforums.org/attachment.php?attachmentid=12748&stc=1&d=1152936010](http://ubuntuforums.org/attachment.php?attachmentid=12748&stc=1&d=1152936010)

Let me know if you need anything else.

God Bless, Jereme

---

### Post by shane2peru on 2007-02-14
No, not a problem it is no trouble at all on my end.  I just need one more thing.  Ok, I saved both files and now, I don't know what to do with them.  :D  I haven't messed around too much with the art side of Ubuntu, and changing things.  Other than a splash image for grub, and the nice gui menus that allow you to change some things.  I appreciate the help!  

Shane

---

### Post by mhancoc7 on 2007-02-14
> **shane2peru said:**
> No, not a problem it is no trouble at all on my end.  I just need one more thing.  Ok, I saved both files and now, I don't know what to do with them.  :D  I haven't messed around too much with the art side of Ubuntu, and changing things.  Other than a splash image for grub, and the nice gui menus that allow you to change some things.  I appreciate the help!  

Shane

Ok, this link will help you with changing the start button.

[http://www.ubuntuforums.org/showpost.php?p=519310&postcount=13](http://www.ubuntuforums.org/showpost.php?p=519310&postcount=13)

For the splash screen you just need to install the gnome-splashscreen-manager (sudo apt-get install gnome-splashscreen-manager). This little app will make it a breeze to change the splash screen.

Hope that helps.

God Bless, Jereme

---

### Post by shane2peru on 2007-02-15
Jereme,

   Hey thanks man!!!  Now it is looking great!  I'm a little partial to Blue and green colors.  I really have never liked the colors of Ubuntu.  I love Ubuntu, just not there color scheme.  But I will say that it is original!  Thanks again for the help.  :D

Shane

---

