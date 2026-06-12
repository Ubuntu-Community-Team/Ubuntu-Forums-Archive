---
title: "Human icons in Open Office in Windows"
date: 2007-06-10
forum: Windows
---

### Post by FuturePilot on 2007-06-10
I'm kind of stuck in Windows for the time being as I'm not going to reinstall Feisty on a HD that's about to crash. So I was board and noticed that the icons in Open Office in Windows are kind of ugly. So I found a way to get Human icons in OO. The same principle applies in Ubuntu if you're not running OO 2.2. That's where I got the idea;)

First download the Human icons from here [http://ubuntuforums.org/showthread.php?t=343044]("http://ubuntuforums.org/showthread.php?t=343044")

Now navigate to C:\Program Files\OpenOffice.org2.2\share\config

There should be a .zip file called "images_industrial"
Rename it to something else like "images_industrial_backup"

Now move the "images_industrial" zip file you downloaded before into this directory

Start Open Office and go Tools>Options>View where it says Icon Size and Style change Automatic to Industrial. You can also change the icon size to Large. I think it looks better but that's up to you.

Click Ok. You might have to restart OO. (Not necessary in Ubuntu:p)

If they still don't appear close OO and navigate to C:\Documents and Settings\USER_NAME\Application Data\OpenOffice.org2\user\config\imagecache 
and delete everything out of there.

Now they should be there when you run OO

Now you can enjoy nice Human icons in Windows:D

---

