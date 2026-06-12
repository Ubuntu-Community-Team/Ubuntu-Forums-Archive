---
title: "Flash Server"
date: 2008-03-27
forum: Server Platforms
---

### Post by Black Mage on 2008-03-27
Does anyone know how to create a flash ubuntu server? I currently have a web server running apache2, and when I embedd a swf file into html, it doesn't play. Are there things I have to modify?

---

### Post by cdenley on 2008-03-27
[http://www.w3schools.com/flash/flash_inhtml.asp](http://www.w3schools.com/flash/flash_inhtml.asp)

Check your html code and your file permissions. Did you install the flash plugin?

---

### Post by Black Mage on 2008-03-27
Yes, I did sudo apt-get install flashplugin-non free. 

My HTML tags look like this:

```

	<OBJECT classid="clsid:D27CDB6E-AE6D-11cf-96B8-444553540000"
codebase="http://download.macromedia.com/pub/shockwave/cabs/flash/swflash.cab#version=6,0,40,0"
WIDTH="550" HEIGHT="400" id="myMovieName"><PARAM NAME=movie VALUE="hitchhike.swf">
<PARAM NAME=quality VALUE=high>
<PARAM NAME=bgcolor VALUE=#FFFFFF>
<EMBED src="hitchhike.swf" quality=high bgcolor=#FFFFFF WIDTH="550" HEIGHT="400"
NAME="myMovieName" ALIGN="" TYPE="application/x-shockwave-flash"
PLUGINSPAGE="http://www.macromedia.com/go/getflashplayer"></EMBED></OBJECT>

```
Not only does it not play in the html, but it also doesn't play if I try to run flash on the server using the actual Macromedia Flash to create/play .swf. Would I be required to set Apache mime types or anything like that? And I can play youtube videos on the server.

---

### Post by cdenley on 2008-03-27
Works fine for me. Are you sure your .swf file works? Are you sure the file permissions are correct? The default mime types should be fine. What happens when you open the file from you local hard drive?

---

### Post by Black Mage on 2008-03-27
What should the permissions be set too or look like?

---

### Post by cdenley on 2008-03-27
Whatever you want as long as www-data has read permission.

---

