---
title: "A simple tweak I made to make Netflix more user friendly via Chrome on my HTPC."
date: 2014-11-13
forum: Tutorials
---

### Post by Roasted on 2014-11-13
Hello friends. I made a simple change to my HTPC tonight and figured I'd share. As a result, this is more of an informational post than your typical question oriented post. A little back story, I have a HTPC running Ubuntu 14.04 with Unity. I set display scaling to 2.0, which makes Unity surprisingly awesome as a HTPC interface. Thing is, I wanted a "do it all" HTPC, hence the full computer OS in favor of my Chromecast that I have but don't really use any more. I needed something that could stream my 2 TB worth of MKVs from my server in the basement and play them flawlessly on the TV in the living room. Likewise, I wanted Netflix for online streaming. The recent Netflix support via Chrome helped make all of this possible.

In a nutshell, here's all I did. I grabbed a Netflix icon from an online image search, loaded it into Inkscape, and saved it as netflix.svg. I copied the file to my icons directory. Then, I copied google-chrome.desktop and edited it so it reflected the Netflix icon as well as Netflix in the name. I also adjusted the Exec= path to launch Chrome in kiosk mode. With netflix.com as the home page, it's a one click way to pipe right in to Netflix. My wife approves, so I figured that meant something. :)

Steps:

1) Locate which Netflix image you'd like to use as an icon. I used this one [here.]("https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQhTtytxC5EIFkCvhWF4IQDPjUU1it9lMHb6gUdPpnd7ri38e7H")

2) Open the image in Inkscape. I changed nothing to the image, and instead just went File - Save As and named it netflix.svg.

So we have the icon. Let's copy it to a specific directory. For me, I chose /usr/share/app-install/icons, but really only because I saw Audacity's svg icon was in there, so I figured it would fly without issue.

3) To copy the file, run this in terminal. Remember to edit in your username as well as the path to where your new netflix.svg file is located:
```
sudo cp /home/USERNAME/path/to/netflix.svg /usr/share/app-install/icons/
```

So the icon is created and copied to the final directory. Let's create a dedicated netflix.desktop file by copying Chrome's.

4) In terminal, run this command to make a copy of your Chrome desktop file but under the Netflix name.
```
sudo cp /usr/share/applications/google-chrome.desktop /usr/share/applications/netflix.desktop
```

5) Then let's edit the netflix.desktop file.
```
sudo gedit /usr/share/applications/netflix.desktop
```

This is my netflix.desktop file [here.]("http://pastebin.com/7KG4ggxC") I edited several lines. Having worked with .desktop files before, I knew what I was looking for, so I just did a CTRL + F to search for name, icon, and exec.

Line 3: Change name to Netflix
Line 108, 168, 221: Added --kiosk to the command to launch Chrome. This launches Chrome in "F11" mode. Skip this step if you don't want this to launch in full screen/F11/kiosk mode.
Line 110: This is where I referenced the netflix.svg icon. Notice that I used a direct path. Wherever you put your netflix.svg image, make sure the path you put in this file matches it.

After that, boom: [http://imgur.com/a/vJzLv](http://imgur.com/a/vJzLv)

Given that I set Chrome's default zoom to 200% and have it set to "large" text (available in the Chrome perferences), along with having netflix.com as the home page, this provides a one click passage to a full screened instance of Netflix. Might not be overly convenient for your regular desktop, but if you folks are rocking a HTPC with flat Ubuntu on it, this could make things a bit more seamless. Likewise, if you're doing this on a regular laptop or desktop, ramping up the zoom and text size might not be favorable. For a living room setting it makes things a lot nicer though.

To close the full screened (kiosk) instance of Chrome (Netflix), use CTRL + W or else ALT + F4.

FYI: I found that if you have Chrome already open and try to launch this Netflix instance, it may not work. Given that the Netflix entry is calling Chrome, but you already have Chrome running.... well you can see why this may not fly (but again, only if Chrome is already open when you launch this Netflix/Chrome instance). As long as Chrome is closed, the "Netflix" instance will launch Chrome accordingly.

So overall, nothing glorious. All this does is pairs a Netflix icon with a desktop file that calls on Chrome in a full screened format. That said, it makes the HTPC experience a little more streamlined, which I dig. If this helps anybody, great. If it doesn't, then apologies for soaking up a few lines of text on the forum's server. :D

---

### Post by Bucky Ball on 2014-11-14
*Thread moved to **Tutorials**.*

Please be aware that the support areas are for support questions only. 

Thanks for sharing. ;)

---

