---
title: "Can't change wallpaper"
date: 2015-03-10
forum: Ubuntu Development Version
---

### Post by sgage on 2015-03-10
I did a fresh install yesterday with the new systemd-default build, and everything is working great. Was working great. After a handful of updates last evening, my wallpaper reverted to the standard issue Gnome wallpaper. I can change it to any of the wallpapers shipped with Gnome, but not to an arbitrary picture in my Pictures directory. When I try to do so, it says to try adding pictures to that directory, with a link to the directory. Clicking on the link goes right to my Pictures directory, and it's full of pictures - they're just not being seen for some reason.

Cavsfan reported a similar thing at the end of January, which he resolved by deleting his dconf user file and rebooting (several times?). This has not worked for me.

Anyone else seeing this?

---

### Post by mc4man on 2015-03-10
Not sure about a gnome session but in an ubuntu one simply deleting the dconf user file & rebooting or loging out/in won't suffice as that file is re-written from mem on session end.
You may have to be a bit more aggressive. Either delete the file from another user session or another install. 
Alternately you can delete the file in your session  & then do an immediate  hard shutdown (power button), this will prevent the file from being re-created until next log in where you'll get a fresh default user file.

---

### Post by sgage on 2015-03-10
> **mc4man said:**
> Not sure about a gnome session but in an ubuntu one simply deleting the dconf user file & rebooting or loging out/in won't suffice as that file is re-written from mem on session end.
You may have to be a bit more aggressive. Either delete the file from another user session or another install. 
Alternately you can delete the file in your session  & then do an immediate  hard shutdown (power button), this will prevent the file from being re-created until next log in where you'll get a fresh default user file.

It's the same with a Gnome session. I just log out of my account, go to a VT, delete the file, then log back in. (After a fresh clean install, I use the same technique to copy in a saved user file with all my settings in it.)

---

### Post by sgage on 2015-03-10
Here's a strange thing, which might provide a clue:

Using the dconf editor, I can look at org/gnome/desktop/background and see that the background picture file set there is indeed the file in my Pictures directory that I want - the one I set originally before this problem cropped up. But the wallpaper on my desktop is the stock blue pattern. 

If I go into 'change desktop background', the wallpaper thumbnail shows as plain black. Now, if I select any one of the wallpapers that ships with Gnome, the background shows up properly, and the filename in dconf is set accordingly.

---

### Post by Cavsfan on 2015-03-10
Mc4man has provided the only solution that works. It has helped me 2 times. 
I could look into dconf and see my wallpaper and it also showed in Appearance > Desktop but still would not actually show on the desktop.

I've got 4 linux installs so I just booted into another one deleted the **~/.config/dconf/user** file and it was fixed.

I took notes and this is the 2nd time it happened. That time it took a couple of reboots to finally get it fixed.

 [http://ubuntuforums.org/showthread.php?t=2263408](http://ubuntuforums.org/showthread.php?t=2263408)

---

### Post by sgage on 2015-03-10
> **Cavsfan said:**
> Mc4man has provided the only solution that works. It has helped me 2 times. 
I could look into dconf and see my wallpaper and it also showed in Appearance > Desktop but still would not actually show on the desktop.

I've got 4 linux installs so I just booted into another one deleted the **~/.config/dconf/user** file and it was fixed.

I took notes and this is the 2nd time it happened. That time it took a couple of reboots to finally get it fixed.

 [http://ubuntuforums.org/showthread.php?t=2263408](http://ubuntuforums.org/showthread.php?t=2263408)

Seems strange that it took two reboots. I'll give it another try.

---

### Post by Cavsfan on 2015-03-10
> **sgage said:**
> Seems strange that it took two reboots. I'll give it another try.

It may have took more than 2 lol! But, that is the only way I believe there is to fix it. I fought with it for a while and deleted the file a couple of times.

As I mentioned in that thread after 3-4 (I think) reboots it fixed itself. Strange but true.

---

### Post by sgage on 2015-03-10
Well, logging out and deleting user from a VT definitely deletes it, but just for completeness I did as you suggest and deleted it from another installation I have on this machine. After 3 reboots, no joy. Whatever - the stock blue Gnome wallpaper kind of grows on you after a while. :-)

---

### Post by Cavsfan on 2015-03-11
> **sgage said:**
> Well, logging out and deleting user from a VT definitely deletes it, but just for completeness I did as you suggest and deleted it from another installation I have on this machine. After 3 reboots, no joy. Whatever - the stock blue Gnome wallpaper kind of grows on you after a while. :-)

Lol! That is strange. Maybe it will iron itself out like mine did.

Here's the first time it happened to me on Utopic in the development cycle.

[http://ubuntuforums.org/showthread.php?t=2245724](http://ubuntuforums.org/showthread.php?t=2245724)

---

### Post by sgage on 2015-03-11
I'm sure it will iron itself out soon enough. It's just such a strange little regression...

---

### Post by sammiev on 2015-03-11
This must be a hit or miss thingy as I never had that problem and over the last day I changed my background at least 5 or more times.

Works every time for me with the background I selected on many boots. ( All stock but my background wallpaper )

The only question would be, did you add any other packages that may cause the problem on hand?

---

### Post by Cavsfan on 2015-03-12
> **sgage said:**
> I'm sure it will iron itself out soon enough. It's just such a strange little regression...

Yes, I agree. At this stage beta1 funny things happen a lot. Some strange things that cannot be accounted for lol!

---

