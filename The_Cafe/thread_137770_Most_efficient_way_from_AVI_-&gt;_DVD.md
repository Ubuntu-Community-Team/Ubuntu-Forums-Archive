---
title: "Most efficient way from AVI -&gt; DVD"
date: 2006-02-28
forum: The Cafe
---

### Post by Spudly on 2006-02-28
I've been using Kino on an Ubuntu Hoary Hedgehog server installation (BlackBox WM - no KDE or GNOME) with some success. The only success I'm not having is getting the video from AVI (which can be captured and manipulated in Kino) to an actual lounge-room-DVD-player-ready DVD-R. Kino will export to an MPEG-2 format file so I'm wondering what dvd tools i need to use. Kino has an option to export with dvd-authoring.xml information, so I'm assuming that's the way to go...but am not sure where to go next.

FYI - I currently use Pinnacle Studio v9.4 on WindowsXP to do this because it's do damn simple (capture or import AVI's, pop DVD-R in the drive, make the DVD - hey presto!). Does anyone know of a plugin or tool that allows Kino to make/burn the DVD?

Thoughts/Comments would be appreciated.

---

### Post by keyboardslave on 2007-08-23
Greetings Spudly,

I am currently facing the same problems as you im using Kino to export a XML with the right audio formats and video formats then using qdvdauthor to create my menus and make the iso.

sudo apt-get install qdvdauthor

that is a GUI for dvdauthor.

Also you could try here for some more info:

<http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/AVI_to_DVD>

Enjoy your movies!! :popcorn:

Its a handy tutorial that helped me alot.

Kind Regards,
keyboardslave

---

### Post by ahaslam on 2007-08-23
I used Tovid many moons ago & was very impressed. It appears to have developed substantially in the mean time: [http://tovid.wikia.com/wiki/Main_Page](http://tovid.wikia.com/wiki/Main_Page)

;)

---

### Post by ahaslam on 2007-08-23
Deleted, duplicate post (damn forward/back buttons)...

---

### Post by Steve1961 on 2007-08-23
For a simple dvd with no menus I found this method worked for me:

[http://ubuntuforums.org/showthread.php?t=320389](http://ubuntuforums.org/showthread.php?t=320389)

For something with a menu I combined the above method (up to where I created mpegs) with todisk (part of the tovid package)

---

