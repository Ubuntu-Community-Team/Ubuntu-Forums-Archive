---
title: "Gedit plugin for web developer/ webmasters"
date: 2008-06-12
forum: The Cafe
---

### Post by yinsee on 2008-06-12
hi guys, i am a web developer and i do lot of FTP editing directly from server. I really like PSPAD's (windows) FTP edit feature, but i can't find this feature in Ubuntu, except if i install Kate, or mount the FTP using nautilus. But the problem with mounting FTP is it is not convenient because i have to jump from one FTP account to another.

To solve my own problem, i have created a GEdit plugin (i call it FTP Browser) that simply connect to an FTP, download the file into /tmp, and open in gedit. When you save the file, it will upload the file back to your FTP server. Wolla! just what i needed. btw its my first python script :)


I would like to share the plugin with you guys, hopefully can help someone here who need it. It is shared via google code.
[http://code.google.com/p/gedit-ftp-browser/](http://code.google.com/p/gedit-ftp-browser/)

Dont forget to buy me beer if you like it :popcorn:

---

### Post by Johnsie on 2008-06-12
nice... where do I extract the files to?

oh nevermind its:

> 
.gnome2/gedit/plugins/ in your home directory.


---

### Post by pt123 on 2008-06-13
clever, how hard was it to write?

---

### Post by cpetercarter on 2008-06-13
Hate to say this, but doesn't gFTP already do this?

---

### Post by frup on 2008-06-13
> **cpetercarter said:**
> Hate to say this, but doesn't gFTP already do this?

Is there a gedit plugin to gftp? And no I don't mean assigning gedit as the GFTP editor.

Gftp is rather awkward. People I know who have begun using ubuntu and been forced to use gftp really miss the variety of different ftp clients. Flash FXP in particular it seems (I think the all cracked it)

For me when using gftp I have found setting gedit as the editor is immensely annoying because if I have other files open they get closed when I save the ftp file... because you have to exit gedit to complete process on the gftp side. bug IMO.

Having a plugin like this would definitely be a plus for me as I work on multiple sites with multiple html and php documents all the time. Perfect. I will try it when I get back on my own computer.

---

### Post by sybille on 2008-06-13
Ooo, that's really handy. Great job!

cpetercarter, yes, gftp does do this, and it's what I've been using. But I use gedit for web stuff - there are a lot of plugins for gedit that make it a really powerful HTML editor. So since I'm already using gedit, it's very nice to be able to stay there and easily upload newly edited pages.

If anyone is curious, here's some good information about how to set up gedit for web development:
[http://www.micahcarrick.com/09-29-2007/gedit-html-editor.html](http://www.micahcarrick.com/09-29-2007/gedit-html-editor.html)

I especially like the following plugins:
**Session saver**: part of [gedit-plugins]("apt:gedit-plugins")
**HTML tidy**: [http://www.eng.tau.ac.il/~atavory/gedit-plugins/html-tidy/]("http://www.eng.tau.ac.il/%7Eatavory/gedit-plugins/html-tidy/")
**Browser preview**: [http://my.opera.com/area42/blog/updated-gedit-browser-preview-plugin](http://my.opera.com/area42/blog/updated-gedit-browser-preview-plugin)   
**Live HTML timestamp**: [http://vax64.dk/live-html-timestamp/](http://vax64.dk/live-html-timestamp/)

There are lots of other gedit plugins here: [http://live.gnome.org/Gedit/Plugins](http://live.gnome.org/Gedit/Plugins)

yinsee, have you thought about putting a link to your plugin in on that GNOME plugin page? It would be a good way to let more people find out about it.

---

