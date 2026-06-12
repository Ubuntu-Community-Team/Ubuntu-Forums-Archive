---
title: "Gnome Desktop looks very Win 98ish"
date: 2007-08-22
forum: The Cafe
---

### Post by swoll1980 on 2007-08-22
Any way to make it look more streamlined like  "rounder lines" I don't know how to explain it. Hopefully you will know what I'm talking about.

---

### Post by LookTJ on 2007-08-22
In what way does GNOME look like Windows 98?

GNOME: [http://www.desktoplinux.com/files/article109/debian-07.jpg](http://www.desktoplinux.com/files/article109/debian-07.jpg)

Windows 98: [http://toastytech.com/guis/win98desk.gif](http://toastytech.com/guis/win98desk.gif)

---

### Post by picpak on 2007-08-22
I think he's referring to the little things like the look of the taskbar and start menu. In some ways, I agree, but that's what things like taskbar transparency and [USP](http://ubuntuforums.org/forumdisplay.php?f=156) are for.

---

### Post by amazingtaters on 2007-08-22
You could also apply different themes. Simply head on over to gnome-look.org and you will be able to download plenty of themes (GTK) and install them straight from the .tar.gz

---

### Post by racoq on 2007-08-22
> **bloor75 said:**
> Any way to make it look more streamlined like  "rounder lines" I don't know how to explain it. Hopefully you will know what I'm talking about.

So costumize it to be different. Gnome is far more flexible than any windows version will ever be :p

---

### Post by swoll1980 on 2007-08-22
I'm refering to it's boxyness looking at taylers screenshots I don't know how you can say they don't look alike. I'm not talking About the wall paper or Icons I'm talking about the panels and the things in the panels. Is there any way to round them of so there not so boxy

---

### Post by blithen on 2007-08-22
O.o I still don't see it. I mean the only similarity is that both taskbars are boxed shaped.

---

### Post by picpak on 2007-08-22
> **blithen said:**
> O.o I still don't see it. I mean the only similarity is that both taskbars are boxed shaped.

I'm pretty sure that's all he's referring to.

---

### Post by phrostbyte on 2007-08-22
Go on the sticked desktop screenshots thread.

---

### Post by Acglaphotis on 2007-08-22
Where are the kde fanboys saying its true? lol

Yeah i too dislike the squareness of the bars... maybe you can install a dock (awn or kiba dock) and/or install kde (sudo aptitude install kde-core).

---

### Post by swoll1980 on 2007-08-22
I got that usp2 how would I install the beta patch it is a text file that looks like this 

--- usp 2006-07-30 07:08:09.000000000 +0200
+++ usp2        2006-07-30 18:55:05.000000000 +0200
@@ -1114,25 +1113,29 @@


     def Filter(self,widget,categorytext):
-        self.ShowAllApps()
-        self.wTree.get_widget("entry1").grab_focus()
-
-        if self.donotfilterapps == False:
-            for i in self.wTree.get_widget("vbuttonbox9").get_children():
-
-                if categorytext == "":
-                    full_label = i.Label1 + i.Label2 + i.Label3 + i.Label4
+       full_label=text=""
+       showAllAppsBool=False
+       if categorytext != "" or self.donotfilterapps == False:
+           self.ShowAllApps()
+           self.wTree.get_widget("entry1").grab_focus()
+           showAllAppsBool = True
+
+        for i in self.wTree.get_widget("vbuttonbox9").get_children():
+           if categorytext != "":
+               showAllAppsBool = True
+                full_label = i.Label3
+                text = categorytext
+                self.wTree.get_widget("entry1").set_text('')
+           else:
+               if self.donotfilterapps == False:
+                   full_label = i.Label1 + i.Label2 + i.Label3 + i.Label4
                     text = self.wTree.get_widget("entry1").get_text()
-                else:
-                    full_label = i.Label3
-                    text = categorytext
-                    self.wTree.get_widget("entry1").set_text('')
-
-                if not re.search(text,full_label,re.IGNORECASE):
-                     i.hide()
-                else:
-                     i.show()

+           if showAllAppsBool == True:
+               if not re.search(text,full_label,re.IGNORECASE):
+                   i.hide()
+               else:
+                   i.show()

     def AddFavourite(self,a,widget, event, Exec, ButtonBox,menutogo):
         self.Add_Button(widget.MyButtonName,'application',False)

---

### Post by swoll1980 on 2007-08-22
> **Acglaphotis said:**
> Where are the kde fanboys saying its true? lol

Yeah i too dislike the squareness of the bars... maybe you can install a dock (awn or kiba dock) and/or install kde (sudo aptitude install kde-core).

What do you mean by dock? Like "Stardock" I didn't know they had these in linux. Is  kiba  like "Stardock"

---

### Post by toupeiro on 2007-08-22
uhh ,.. they're both GUI's??! (as far as similarities)

---

### Post by swoll1980 on 2007-08-22
Stardocks a panal you can put widgits on like Google Desktop

---

### Post by phrostbyte on 2007-08-22
[http://ubuntuforums.org/showthread.php?t=515076](http://ubuntuforums.org/showthread.php?t=515076)

^ Go there and browse around a bit.

---

### Post by igknighted on 2007-08-22
Kinda like this?

I could add a more 3d look to the panel if I desired, I find this more readable.  Everything is customizable.  Go to [http://art.gnome.org](http://art.gnome.org) or [http://gnome-look.org](http://gnome-look.org) and browse around I am sure you will find something that tickles your fancy.

---

### Post by stmiller on 2007-08-23
Gnome like Windows98? Interesting.

Most people say perhaps the exact opposite, that Gnome mimics MacOS9.

[IMG]http://wrds.files.wordpress.com/2007/04/mac_os_9_screenshot_2.png[/IMG]

---

### Post by igknighted on 2007-08-23
> **stmiller said:**
> Gnome like Windows98? Interesting.

Most people say perhaps the exact opposite, that Gnome mimics MacOS9.

Also interesting, because KDE actually does (can do) the application menus on the top bar like that, and (to my knowledge) gnome cannot :P.

I do see what the OP means though.  Stock Ubuntu has very 2d panels.  XP and Vista both have depth to them.  Via GTK themes it is easy to add depth to the panels, so its easy to overcome... but a little texture by default couldn't hurt, right?

EDIT: And for the record. OS9 was the most frustrating, difficult OS that I have ever dealt with, glad I didn't make that connection when I started Linux!

---

### Post by ~LoKe on 2007-08-23
Uh...

[img]http://tn3-1.deviantart.com/fs18/300W/f/2007/219/5/0/Desktop_as_seen_on_08_07_07_by_IcedLoKi.jpg[/img]
[http://icedloki.deviantart.com/art/Desktop-as-seen-on-08-07-07-61696579](http://icedloki.deviantart.com/art/Desktop-as-seen-on-08-07-07-61696579)

---

### Post by swoll1980 on 2007-08-23
> **stmiller said:**
> Gnome like Windows98? Interesting.

Most people say perhaps the exact opposite, that Gnome mimics MacOS9.

[IMG]http://wrds.files.wordpress.com/2007/04/mac_os_9_screenshot_2.png[/IMG]

It does look more like OS 9 there both ugly though

---

### Post by happy-and-lost on 2007-08-23
The old default Gnome did look a bit boxy and icky, but there've been major changes made to Clearlooks and the Gnome icon theme. Now it looks gorgeous :)

---

### Post by bash on 2007-08-23
No [kiba-dock](http://www.kiba-dock.org/) and [awn](http://awn.wetpaint.com/?t=anon) are docks like the mac os x docks.

You can see a picture of awn here: [Click me](http://static.flickr.com/112/284328104_6995c6f4b7_o.jpg)

With Stardock I guess you mean something similar to Windowblinds and all the other customasation software you need in Windows. Well in Gnome its buit-in.

Go to [www.gnome-look.org](www.gnome-look.org) to download new themes and icons for you Gnome desktop. Also I would recommend that you take a look at [Beryl](http://www.beryl-project.org/) or [Compiz](http://compiz.org/). If you don't know what they are I would advise you to watch this Youtube Video as it show quite nicely what, in this case Beryl, does: [http://youtube.com/watch?v=ZD7QraljRfM](http://youtube.com/watch?v=ZD7QraljRfM)

And last but not least I think you might also like [screenlets](http://www.ryxperience.com/storage/screenlets-0.0.8.jpg) or [desklets](http://upload.wikimedia.org/wikipedia/de/3/34/Gdesklets.png).

You can find Desklets here: [http://www.gdesklets.de/](http://www.gdesklets.de/)
And Screenlets here. But watch out for Screenlets to work you need to have Beryl or Compiz running!!!: [http://forum.compiz-fusion.org/showthread.php?t=323](http://forum.compiz-fusion.org/showthread.php?t=323)

---

