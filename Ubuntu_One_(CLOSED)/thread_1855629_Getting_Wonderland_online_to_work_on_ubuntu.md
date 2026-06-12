---
title: "Getting Wonderland online to work on ubuntu"
date: 2011-10-06
forum: Ubuntu One (CLOSED)
---

### Post by cade1302 on 2011-10-06
1. Download the Wondeland online game client near the bottom of the page on the Wonderland online download page
[IMG]http://www.janza.com.my/ubuntu/wlo/Color.jpg[/IMG] 
(Url: "http://wl.igg.com/download/download_client.php")
After download done. It should be save at /home/YOURPCNAME/Downloads
Go to the terminal and after each line press enter:
cd Downloads
wine wl_setup_6.0.0_20110127.exe

2. After Wonderland Online installing completed.

Navigate Applications > Wine > Configure Wine
Make Sure you add application and set windows version as Windows ME for aLogin.exe and Main.exe
[IMG]http://www.janza.com.my/ubuntu/wlo/winecfg1.jpg[/IMG]
[IMG]http://www.janza.com.my/ubuntu/wlo/winecfg2.jpg[/IMG]

3. special.sh 
Download wlo.sh [[COLOR="Red"]here[/COLOR] ]("http://www.janza.com.my/ubuntu/wlo/wlo.sh")
or open a txt document and type this

#!/bin/bash 
cd '/home/YOURPCNAME/.wine/drive_c/Program Files/Wonderland Online'
wine explorer "/desktop=WLO_[$RANDOM],800x600 aLogin.exe end /LUA:OFF"

then name the document "wlo.sh"
To Run Wonderland Online Properly. You need to set it Full Screen. Before you can click wlo.sh
You Navigate it at Applications > Wine > Programs > Wonderland Online > Wonderland Online
Click Screen Settings and Choose Full Screen.
I have managed to get it to not be in full screen but I don't remember how I just experimented a bit, haha!

4. Set wlo.sh to a executable file if it is not already.
[IMG]http://www.janza.com.my/ubuntu/wlo/wloshicon.jpg[/IMG]
click run
[IMG]http://www.janza.com.my/ubuntu/wlo/wloshrun.jpg[/IMG]

[SIZE="4"]HAVE FUN!!!;)[/SIZE]

---

