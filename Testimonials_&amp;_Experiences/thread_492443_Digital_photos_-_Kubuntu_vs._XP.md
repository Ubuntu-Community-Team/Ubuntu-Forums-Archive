---
title: "Digital photos - Kubuntu vs. XP"
date: 2007-07-04
forum: Testimonials &amp; Experiences
---

### Post by mrming on 2007-07-04
I'm sad to say that tonight I had my first big Ubuntu disappointment. I plugged in my digital camera to download around 250 snaps from last week's holiday.

**Here's what I normally do in Windows XP:**

[LIST]
[*]Import my pics to a folder using the XP Camera and Scanner Wizard.

[*]Open the whole lot in Photoshop, go through them one by one and close the ones I don't think are good enough.

[*]Retouch any of the remaining photos as necessary and save them to a subfolder called 'edited'.

[*]Use the windows Flickr Uploadr to upload, this allows me to rotate the pics if necessary, and automatically resizes the photos to my preferred size (800 pixels wide).
[/LIST]
[B]
Now here's what happenned in Kubuntu:[/B]

I'm running Kubuntu Feisty, and after plugging in my Canon Ixus 55, everything went swimmingly and I was able to get my photos off the camera and into DigiKam very easily.

The problems began when I started to edit my photos with a view to uploading them to Flickr.

[LIST]
[*]I opened all the photos in the GIMP. It took a long time to open them all, and it quickly became apparent that the GIMP was struggling with memory. I'm using an Intel Core Duo Toshiba M400 Tablet PC with 1GB RAM. Adobe Photoshop CS2 running in Windows XP is quick and suffers from no noticable lack of memory.

[*]I eventually got all the pics open in the GIMP and started going through them, closing the ones I didn't want to upload to Flickr. I then went to go back through the remaining photos in order to any necessary retouching. There were probably 35 five megapixel photos left open after the initial purge. Unfortunately the GIMP seemed to have real problems rendering the images to the screen and when trying to view the pics all I got was a white rectangle in each window. I eventually managed to save the chosen photos into a seperate folder, albeit very slowly.

[*]Finally, I needed to resize the pics to display on Flickr. In XP you have two choices - you can use an automated batch action in Photoshop, or the Flickr Uploadr will do the resizing for you. In Kubuntu, alas, the GIMP doesn't seem to have any automation features (without resorting to the command line), and KFlickr doesn't provide any resizing.
[/LIST]

The net result of this is that I had to boot into Windows XP to edit, resize and upload my photos. If Linux on the desktop is going to succeed (which I sincerely hope it does), then basic functionality like this needs to be sorted, and it needs to be idiot-proof.

---

### Post by TheRingmaster on 2007-07-04
I would recommend you use Krita. It is a native kde app were as gimp requires the installation of some extra gtk libraries. I have found it easy to use.

---

### Post by Jerry N on 2007-07-05
Is there a Linux equivalent to XNVIEW or IRFANVIEW?

Jerry

---

### Post by roastdawgg on 2007-07-05
I would recommend using Digikam. It is a direct linux equivalent to Adobe Bridge. It is really fast and you can do batch resizing from within it. I am a photographer and have found this program easily handles my 50 Gig photo  library.

---

### Post by deepclutch on 2007-07-05
fyi google picasa for Linux is available.

---

### Post by benton on 2007-07-06
I don't know if it runs in Kubuntu, but in Ubuntu F-Spot is da bomb. I just connect my Canon S3 IS and Ubuntu launches the built-in import program. Once the pictures are on the HD, F-Spot imports them in and with a few clicks I create a gallery for the web and a gallery for printing. With another click I can export the web gallery to flickr, picasa web or whatever, and with the next one I can export the print gallery to CD. I could retouch them if needed too.

So basically... I love Ubuntu and F-Spot. Never thought digital photography was going to be  sooooo damn easy in Linux. No Canon or  third-party needed for anything!

HTH,

-Benton

---

### Post by 3rdalbum on 2007-07-07
> **mrming said:**
> The net result of this is that I had to boot into Windows XP to edit, resize and upload my photos. If Linux on the desktop is going to succeed (which I sincerely hope it does), then basic functionality like this needs to be sorted, and it needs to be idiot-proof.

No you didn't - you just should have used a proper photo management program.

It looks like you've run into a peculiar race condition in The Gimp. You should file a bug report. I just tried the same sort of test on my computer and it has worked fine, with the system still as responsive as ever. Note that my system is using 1/10th of the swap space that Windows does when it starts up. Now I've just got to close the rest of these windows :-)

By the way, this is going into my "reasons".

---

