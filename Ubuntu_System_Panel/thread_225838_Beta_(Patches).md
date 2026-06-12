---
title: "Beta (Patches)"
date: 2006-07-30
forum: Ubuntu System Panel
---

### Post by Note360 on 2006-07-30
Ok, so profoX and me are both developers (kinda). So here is where we post the newest Beta versions with our fixes. 

**Disclaimer**
These patches in no way reflect on chanders they are just small patches me and profoX applied.
These patches are probably full of bugs and are unstable.
*************WARNING********************
Our patches may or may not effect your system in a good or bad way. We want to know about it but are in no way responsible.

Thank you for flying on Beta Airlines enjoy your flight.

---

### Post by _profox on 2006-07-30
Beta releases are normal releases that are known to work well and have all features frozen, but that are in a testing stage before the actual Release Candidate releases

So this is more like a "patches" section

---

### Post by Note360 on 2006-07-30
Sorry, lol cant change it now, but this should be helpful especially for development.

---

### Post by _profox on 2006-07-30
Here's the patch for the do_not_filter bugs:

```
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

```

---

### Post by Note360 on 2006-07-30
good but also include a link to a .deb package if at all possible.

---

### Post by _profox on 2006-07-30
> **Note360 said:**
> good but also include a link to a .deb package if at all possible.

You want me to release the official version + my patch? okay, I will try... hold on.
edit: chanders, what's the best way to do this? open up your .deb in a packager (and which one) and edit the version to say 0.30-patched1 etc and include a new /usr/bin/usp ?

---

### Post by chanders on 2006-07-30
> **Note360 said:**
> good but also include a link to a .deb package if at all possible.

Please make sure if you are providing  a .deb you include _testing in the name.

---

### Post by Note360 on 2006-07-30
sorry just thought it would be easier but then again.

---

### Post by chanders on 2006-07-30
> **_profox said:**
> You want me to release the official version + my patch? okay, I will try... hold on.
edit: chanders, what's the best way to do this? open up your .deb in a packager (and which one) and edit the version to say 0.30-patched1 etc and include a new /usr/bin/usp ?

It is a bit mor technical than that! .debs are signed so you cant muck with them. I used [this]("http://home.comcast.net/~3rdshift/articles/Nokia770/DebianPackaging.html") site to give me a *basic *guide...

---

### Post by _profox on 2006-07-30
Okay, give me some time guys :)
Pff, it's giving me a headache.. They're talking about completely different things.. Just wait for the next release :P I can provide the new /usr/bin/usp file though, if you want...

---

### Post by Note360 on 2006-07-30
Dont worry about the .deb.

---

### Post by _profox on 2006-07-31
**0.30 PATCH 2**
**Change button text (and resize properly)**

I hacked the code again, and I had to do alot of research to get this completed :)
There is a new option in gconf-editor that says "button_customtext"

Change it to change the "System" text on the button :)

But it doesn't just change the text, it also resizes the button to the appropriate size (figuring this out was a hard thing to do for a 1day python noob like me, but I did it for you guys!)

I also made the distance between the icon and the text smaller, because I had a few complaints about that.

Here is the patch! Please include it in the next version? It is "Pending approval" I will change definition to "Approved" if you add the patch. Thanks!!

In a following patch, I will try to make it able for you to use custom icons and to hide the text or icon.

Patch also includes a change to the About Dialog to say "profoX" instead of "profox" ;)

patch:

```
--- usp 0.30
+++ usp 0.30 patch2
@@ -86,12 +86,11 @@
         return GotData
 
 
-class MainWindow:
+class MainWindow (object):
     """This is the main class for the application"""
 
-    def __init__(self):
-
-
+    def __init__(self,menuwin):
+	self.menuwin = menuwin
         #Set the Glade file
         #self.gladefile = sys.path[0] + "/" + "usp.glade"
         self.gladefile = "/usr/share/usp/usp.glade"
@@ -124,6 +123,8 @@
         self.client.notify_add('/apps/usp/show_more_apps_button',self.GconfEntriesChanged)
         self.client.notify_add('/apps/usp/use_toggle_icon',self.GconfEntriesChanged)
         self.client.notify_add('/apps/usp/show_allapps_on_start',self.GconfEntriesChanged)
+        self.client.notify_add('/apps/usp/button_customtext',self.GconfEntriesChanged)
 
 
         self.get_gconf_info()
@@ -396,6 +397,16 @@
             self.client.set_int('/apps/usp/panel_size',24)
             self.panelsize = self.client.get_int('/apps/usp/panel_size')
 
+	self.buttonText = self.client.get_string('/apps/usp/button_customtext')
+	if self.buttonText == None:
+	    self.client.set_string('/apps/usp/button_customtext',"System")
+	    self.buttonText = self.client.get_string('/apps/usp/button_customtext')
 
     def ButtonsToggled(self, widget, **kargs):
 
@@ -543,6 +554,8 @@
             self.wTree.get_widget("vbuttonbox12").hide()
             self.wTree.get_widget("notebook2").set_size_request(-1,302)
 
+	self.menuwin.changeButton(self.buttonText)
+
     def TestForDir(self,dirname):
         try:
             os.makedirs (os.path.join(os.path.expanduser("~"),dirname))
@@ -1419,17 +1432,14 @@
 	def __init__(self, applet, iid):
 		self.applet = applet
 		self.orientation = gnomeapplet.ORIENT_DOWN
-
 		self.toggle = gtk.ToggleButton()
 		self.button_icon = gtk.image_new_from_icon_name("distributor-logo", gtk.ICON_SIZE_MENU)
-
-
 		self.orientation = self.applet.get_orient()
         	# if we have a horizontal panel 
         	if self.orientation == gnomeapplet.ORIENT_UP or self.orientation == gnomeapplet.ORIENT_DOWN:
             		self.button_box = gtk.HBox()
 			self.systemlabel = gtk.Label("System")
-			self.systemlabel.set_size_request(60,-1)
 			self.button_box.set_homogeneous(False)
 			self.button_box.pack_start(self.button_icon)
 			self.button_box.pack_start(self.systemlabel)
@@ -1437,7 +1447,7 @@
 		if self.orientation == gnomeapplet.ORIENT_LEFT:
             		self.button_box = gtk.VBox()
 			self.systemlabel = gtk.Label("System")
-			self.systemlabel.set_size_request(-1,60)
 			self.button_box.set_homogeneous(False)
 			self.systemlabel.set_angle(90)
 			self.button_box.pack_start(self.systemlabel)
@@ -1445,13 +1455,12 @@
 		if self.orientation == gnomeapplet.ORIENT_RIGHT:
             		self.button_box = gtk.VBox()
 			self.systemlabel = gtk.Label("System")
-			self.systemlabel.set_size_request(-1,60)
 			self.button_box.set_homogeneous(False)
 			self.systemlabel.set_angle(270)
 			self.button_box.pack_start(self.button_icon)
 			self.button_box.pack_start(self.systemlabel)
 
-
         	self.toggle.add(self.button_box)
 		self.toggle.set_relief(gtk.RELIEF_NONE)
 		self.toggle.set_active(False)
@@ -1461,7 +1470,7 @@
                 # Change color
                 self.applet.connect("change_background", self.change_background)
 		self.applet.add(self.toggle)
-		self.mainwin = MainWindow()
+		self.mainwin = MainWindow(self)
 		self.mainwin.wTree.get_widget("window1").add_events(gtk.gdk.FOCUS_CHANGE)
 		self.mainwin.wTree.get_widget("window1").connect("focus_out_event", self.loseFocus)
 
@@ -1528,12 +1537,18 @@
 	def enterNotify(self, *args, **kargs):
 		return True
 
+	def changeButton(self, text):
+		self.systemlabel.set_text(text)
+		print "box_size_1: ", self.button_box.size_request()
+		self.button_box.set_size_request(self.systemlabel.size_request()[0]+25,-1)
+		print "box_size_2: ", self.button_box.size_request()
+
 	def preferences(self):
      		pass # and display properties
 
 	def showAboutDialog(self, uicomponent, verb):
         	gnome.ui.About("Ubuntu System Panel", "Ver 0.30", "Copyright 2006 S. Chanderbally",
-                       "A simple system launcher for the GNOME desktop",["S.Chanderbally <schanderbally@gmail.com>","the_thunderbird <ianm@pungwe.com>","profox <profox@ubuntu-nl.org>","note360 <note360@gmail.com>"],[]).show()
+                       "A simple system launcher for the GNOME desktop",["S.Chanderbally <schanderbally@gmail.com>","the_thunderbird <ianm@pungwe.com>","profoX <profox@ubuntu-nl.org>","note360 <note360@gmail.com>"],[]).show()
 
     	def showMenu(self, widget, event):
 

```

---

### Post by _profox on 2006-08-01
Okay, don't get the patch(es) here. They are outdated.
Chanders, I sent you an email with the URL's to the launchpad with the .diff's

What I did for the next release:

**Bugfixes:**
[LIST]
[*] do_not_filter bug
[*] Launching applications with single quoted arguments (eg: cedega --run 'Group' 'Game')
[*] USP stops responding when "Alt"+"F4" are pressed
[/LIST]

**Features:**
I made several enhancements to the applet button:
[LIST]
[*] Change text ("System" text) (or hide text if you make text empty)
[*] Change icon to a different one in /usr/share/icons from your current theme
[*] Hide icon
[*] Resize properly on bigger/smaller text
[*] Resize properly in different orientations (top, bottom, left, right)
[/LIST]

I have nothing else to code right now. Request more features/changes in [https://launchpad.net/products/usp/+bugs](https://launchpad.net/products/usp/+bugs) as "Wish"

Also, don't forget adding your bugs to [https://launchpad.net/products/usp/+bugs](https://launchpad.net/products/usp/+bugs) if you find any bugs!! So we can solve them.

---

### Post by vonpmg on 2006-08-01
Hi.
I know you have told translations will be in near future when no bugs exists, but i have a small patch against 0.30 to show applications names and descriptions in your language.
If it doesn't exist it uses de Name or Description by default.
I hope it will be useful.

Here is the patch:
```

--- usp	2006-08-01 23:00:42.000000000 +0200
+++ usp_vonpmg	2006-08-01 23:00:17.000000000 +0200
@@ -23,6 +23,7 @@
     import gnome.ui
     import gmenu
     import string
+    import locale
 except:
     sys.exit(1)
 
@@ -94,6 +95,8 @@
 
         #Set the Glade file
         #self.gladefile = sys.path[0] + "/" + "usp.glade"
+        self.language,self.encoding=locale.getdefaultlocale()
+        self.lang=self.language[0:2]
         self.gladefile = "/usr/share/usp/usp.glade"
         self.wTree = gtk.glade.XML(self.gladefile,"window1")
         self.USPTips = gtk.Tooltips()
@@ -667,7 +670,6 @@
             Image1 = gtk.image_new_from_icon_name(icon_description, icon_size)
         return Image1
 
-
     def Todos(self):
 
         PlaceCategories=PlaceName=PlaceComment=PlaceExec=PlaceIconName=GenericName=WhatWasDropped=BTip=""
@@ -699,8 +701,17 @@
                                         PlaceName = datalist[i][5:29]+".."
                                     BTip = datalist[i][5:]
 
+                                if datalist[i][0:9] == "Name[%s]=" % self.lang:
+                                    if len(datalist[i][9:]) < 25:
+                                        PlaceName = datalist[i][9:]
+                                    else:
+                                        PlaceName = datalist[i][9:29]+".."
+                                    BTip = datalist[i][9:]
+
                                 if datalist[i][0:8] == "Comment=":
                                     PlaceComment = datalist[i][8:]
+                                if datalist[i][0:12] == "Comment[%s]=" % self.lang:
+                                    PlaceComment = datalist[i][12:]
                                 if datalist[i][0:5] == "Exec=":
                                     execstring = datalist[i][5:].replace("%u", "")
                                     execstring = execstring.replace("%U", "")
@@ -716,6 +727,11 @@
                                         GenericName = datalist[i][12:]
                                     else:
                                         GenericName = datalist[i][12:32]+".."
+                                if datalist[i][0:16] == "GenericName[%s]=" % self.lang:
+                                    if len(datalist[i][16:]) < 21:
+                                        GenericName = datalist[i][16:]
+                                    else:
+                                        GenericName = datalist[i][16:32]+".."
 
                                 if datalist[i][0:11] == "Categories=":
                                     PlaceCategories = datalist[i][11:]
@@ -1425,7 +1441,7 @@
 
 
 		self.orientation = self.applet.get_orient()
-        	# if we have a horizontal panel 
+        	# if we have a horizontal panel
         	if self.orientation == gnomeapplet.ORIENT_UP or self.orientation == gnomeapplet.ORIENT_DOWN:
             		self.button_box = gtk.HBox()
 			self.systemlabel = gtk.Label("System")
@@ -1471,7 +1487,7 @@
      			</popup>
      			"""
      		self.verbs = [ ( "About", self.showAboutDialog) ]
- 
+
 
         def change_background(self, applet, type, color, pixmap):
                 # get reset style
@@ -1513,10 +1529,10 @@
 			self.systemlabel.set_size_request(-1,60)
 			tmpbox.set_homogeneous(False)
 			self.button_box.reorder_child(self.button_icon,0)
-			
+
           	# reparent all the hboxes to the new tmpbox
         	for i in (self.button_box.get_children()):
-            		i.reparent(tmpbox)      
+            		i.reparent(tmpbox)
 
 
         	self.toggle.remove(self.button_box)
@@ -1541,7 +1557,7 @@
 			widget.emit_stop_by_name("button_press_event")
        			origin = widget.window.get_origin()
        			self.positionMenu(origin[0] , origin[1] , widget.size_request()[0] , widget.allocation.y + widget.allocation.height)
-			if self.toggle.get_active() == True: 
+			if self.toggle.get_active() == True:
 				self.mainwin.wTree.get_widget("entry1").set_text('')
 				self.mainwin.wTree.get_widget("window1").hide()
 				self.toggle.set_active(False)
@@ -1587,9 +1603,9 @@
 
         	if entryY + entryHeight + ourHeight < screenHeight:
             		# Align to the bottom of the entry
-            		newY = entryY + entryHeight 
+            		newY = entryY + entryHeight
         	else:
-            		newY = entryY - ourHeight   
+            		newY = entryY - ourHeight
 
         	# -"Move window"
         	self.mainwin.wTree.get_widget("window1").move(newX, newY)
@@ -1603,10 +1619,10 @@
         applet.show_all()
     	return gtk.TRUE
 
-if len(sys.argv) == 2 and sys.argv[1] == "run-in-window":   
+if len(sys.argv) == 2 and sys.argv[1] == "run-in-window":
    	main_window = gtk.Window(gtk.WINDOW_TOPLEVEL)
    	main_window.set_title("Ubuntu System Panel")
-   	main_window.connect("destroy", gtk.main_quit) 
+   	main_window.connect("destroy", gtk.main_quit)
    	app = gnomeapplet.Applet()
         menu_factory(app, None)
         app.reparent(main_window)
@@ -1614,6 +1630,6 @@
         gtk.main()
         sys.exit()
 
-gnomeapplet.bonobo_factory("OAFIID:GNOME_USP_Factory", 
-                             gnomeapplet.Applet.__gtype__, 
+gnomeapplet.bonobo_factory("OAFIID:GNOME_USP_Factory",
+                             gnomeapplet.Applet.__gtype__,
                              "System Panel", "0", menu_factory)


```

Please, continue with this great work.

---

### Post by _profox on 2006-08-01
Might be useful. But I don't think it'll be in the upcoming release, because we're going to rewrite alot of hardcoded code. But if you think translations are so necessary, I will try to use your code and build upon it to get a full translation "engine" soon.

Anyway, it's very nice :) When we're going to make actual use of this code, I'll put you in the contributors section. Keep up the good work.

---

### Post by chanders on 2006-08-01
> **vonpmg said:**
> Hi.
I know you have told translations will be in near future when no bugs exists, but i have a small patch against 0.30 to show applications names and descriptions in your language.
If it doesn't exist it uses de Name or Description by default.
I hope it will be useful.

Here is the patch:
```

--- usp	2006-08-01 23:00:42.000000000 +0200
+++ usp_vonpmg	2006-08-01 23:00:17.000000000 +0200
@@ -23,6 +23,7 @@
     import gnome.ui
     import gmenu
     import string
+    import locale
 except:
     sys.exit(1)
 
@@ -94,6 +95,8 @@
 
         #Set the Glade file
         #self.gladefile = sys.path[0] + "/" + "usp.glade"
+        self.language,self.encoding=locale.getdefaultlocale()
+        self.lang=self.language[0:2]
         self.gladefile = "/usr/share/usp/usp.glade"
         self.wTree = gtk.glade.XML(self.gladefile,"window1")
         self.USPTips = gtk.Tooltips()
@@ -667,7 +670,6 @@
             Image1 = gtk.image_new_from_icon_name(icon_description, icon_size)
         return Image1
 
-
     def Todos(self):
 
         PlaceCategories=PlaceName=PlaceComment=PlaceExec=PlaceIconName=GenericName=WhatWasDropped=BTip=""
@@ -699,8 +701,17 @@
                                         PlaceName = datalist[i][5:29]+".."
                                     BTip = datalist[i][5:]
 
+                                if datalist[i][0:9] == "Name[%s]=" % self.lang:
+                                    if len(datalist[i][9:]) < 25:
+                                        PlaceName = datalist[i][9:]
+                                    else:
+                                        PlaceName = datalist[i][9:29]+".."
+                                    BTip = datalist[i][9:]
+
                                 if datalist[i][0:8] == "Comment=":
                                     PlaceComment = datalist[i][8:]
+                                if datalist[i][0:12] == "Comment[%s]=" % self.lang:
+                                    PlaceComment = datalist[i][12:]
                                 if datalist[i][0:5] == "Exec=":
                                     execstring = datalist[i][5:].replace("%u", "")
                                     execstring = execstring.replace("%U", "")
@@ -716,6 +727,11 @@
                                         GenericName = datalist[i][12:]
                                     else:
                                         GenericName = datalist[i][12:32]+".."
+                                if datalist[i][0:16] == "GenericName[%s]=" % self.lang:
+                                    if len(datalist[i][16:]) < 21:
+                                        GenericName = datalist[i][16:]
+                                    else:
+                                        GenericName = datalist[i][16:32]+".."
 
                                 if datalist[i][0:11] == "Categories=":
                                     PlaceCategories = datalist[i][11:]
@@ -1425,7 +1441,7 @@
 
 
 		self.orientation = self.applet.get_orient()
-        	# if we have a horizontal panel 
+        	# if we have a horizontal panel
         	if self.orientation == gnomeapplet.ORIENT_UP or self.orientation == gnomeapplet.ORIENT_DOWN:
             		self.button_box = gtk.HBox()
 			self.systemlabel = gtk.Label("System")
@@ -1471,7 +1487,7 @@
      			</popup>
      			"""
      		self.verbs = [ ( "About", self.showAboutDialog) ]
- 
+
 
         def change_background(self, applet, type, color, pixmap):
                 # get reset style
@@ -1513,10 +1529,10 @@
 			self.systemlabel.set_size_request(-1,60)
 			tmpbox.set_homogeneous(False)
 			self.button_box.reorder_child(self.button_icon,0)
-			
+
           	# reparent all the hboxes to the new tmpbox
         	for i in (self.button_box.get_children()):
-            		i.reparent(tmpbox)      
+            		i.reparent(tmpbox)
 
 
         	self.toggle.remove(self.button_box)
@@ -1541,7 +1557,7 @@
 			widget.emit_stop_by_name("button_press_event")
        			origin = widget.window.get_origin()
        			self.positionMenu(origin[0] , origin[1] , widget.size_request()[0] , widget.allocation.y + widget.allocation.height)
-			if self.toggle.get_active() == True: 
+			if self.toggle.get_active() == True:
 				self.mainwin.wTree.get_widget("entry1").set_text('')
 				self.mainwin.wTree.get_widget("window1").hide()
 				self.toggle.set_active(False)
@@ -1587,9 +1603,9 @@
 
         	if entryY + entryHeight + ourHeight < screenHeight:
             		# Align to the bottom of the entry
-            		newY = entryY + entryHeight 
+            		newY = entryY + entryHeight
         	else:
-            		newY = entryY - ourHeight   
+            		newY = entryY - ourHeight
 
         	# -"Move window"
         	self.mainwin.wTree.get_widget("window1").move(newX, newY)
@@ -1603,10 +1619,10 @@
         applet.show_all()
     	return gtk.TRUE
 
-if len(sys.argv) == 2 and sys.argv[1] == "run-in-window":   
+if len(sys.argv) == 2 and sys.argv[1] == "run-in-window":
    	main_window = gtk.Window(gtk.WINDOW_TOPLEVEL)
    	main_window.set_title("Ubuntu System Panel")
-   	main_window.connect("destroy", gtk.main_quit) 
+   	main_window.connect("destroy", gtk.main_quit)
    	app = gnomeapplet.Applet()
         menu_factory(app, None)
         app.reparent(main_window)
@@ -1614,6 +1630,6 @@
         gtk.main()
         sys.exit()
 
-gnomeapplet.bonobo_factory("OAFIID:GNOME_USP_Factory", 
-                             gnomeapplet.Applet.__gtype__, 
+gnomeapplet.bonobo_factory("OAFIID:GNOME_USP_Factory",
+                             gnomeapplet.Applet.__gtype__,
                              "System Panel", "0", menu_factory)


```

Please, continue with this great work.

I have looked over your patch and I think it is great work (thankfully as profoX said you do not have much hard coded lines ;)). Thanks for your input. Seeing that a lot of our users are French and Italian not to mention where else in the world I will include this patch in the next release along with profoX's

Chanders

---

### Post by vonpmg on 2006-08-01
Thanks for so rapid response.
I think translation is not very important at this moment.
I have it translated at home for my family members (i am spanish), and thought it could be useful to people.
But please, concentrate your efforts in more importants features and bugfixes and work with this if you have enought time.
I am waiting for the next release, i think it is going to be awesome.
Another note. Please could you add a little feature?
When you work in the keyboard code, i think pressing the escape key should close the menu. In the same way that Gimmie or deskbar.

---

### Post by _profox on 2006-08-01
I think that's very easy, I will work on it tomorrow or tonight :) vonpmg

Also, I will work on getting full translation for the program ;) And thanks for the patch. You will be listed as contributor :)

PS: We had a bug in USP that messed up USP if you pressed alt+f4, the same bug is in deskbar :) I already made a fix and I am sending it to the deskbar bugtracker :) just try pressing alt+f4 when the deskbar "window" is open... and then try typing something in again.. :D

---

### Post by Note360 on 2006-08-01
That is great. Keep up the work, are you going to be makeing any more fixes (if so I will add you to the launcpad site)

---

### Post by lazyd2 on 2006-08-01
Its getting better all the time!

---

### Post by lazyd2 on 2006-08-01
[COLOR=Silver]Oops! double post...[/COLOR]

---

### Post by _profox on 2006-08-01
Yes, we do our best :D
@lazyd2: thanks for the link in your sig ;) we appreciate it

---

### Post by lazyd2 on 2006-08-01
> **_profox said:**
> Yes, we do our best :D
@lazyd2: thanks for the link in your sig ;) we appreciate itIts nothing...the more people will try it, the better it will become ;)

---

### Post by _profox on 2006-08-01
Very true ;)

---

### Post by vonpmg on 2006-08-02
Glad to see the patch is welcome.
I'll try to contribute with more patches.
If you have anything todo perhaps i can help, tell me.
When _profox add the translation system i'll add the spanish translation.
I think it's very simple at this moment, only a few strings in the .glade file.
One more thing. Are you going to use any CVS,Subversion, git or similar system?
Keep the good work :grin:

---

### Post by chanders on 2006-08-02
> **vonpmg said:**
> Glad to see the patch is welcome.
I'll try to contribute with more patches.
If you have anything todo perhaps i can help, tell me.
When _profox add the translation system i'll add the spanish translation.
I think it's very simple at this moment, only a few strings in the .glade file.
One more thing. Are you going to use any CVS,Subversion, git or similar system?
Keep the good work :grin:

Thanks for your input! CVS/SVN is in the process of being setup ;)

---

### Post by vonpmg on 2006-08-02
Well. Here we go again.
Here is the patch (against the recent 0.31) to make the aplication translatable.
Actually it only look for the strings in the .glade file, i think usp itself have no translatable string.

```

--- usp031	2006-08-02 12:09:10.000000000 +0200
+++ usp_vonpmg	2006-08-02 12:30:51.000000000 +0200
@@ -24,9 +24,13 @@
     import gmenu
     import string
     import locale
+    import gettext
 except:
     sys.exit(1)
 
+gtk.glade.textdomain("usp")
+_=gettext.gettext
+
 class Menu:
     def __init__(self,MenuToLookup):
         self.tree = gmenu.lookup_tree(MenuToLookup)
@@ -879,8 +883,17 @@
                         else:
                             PlaceName = datalist[i][5:29]+".."
 
+                    if datalist[i][0:9] == "Name[%s]=" % self.lang:
+                        if len(datalist[i][9:]) < 25:
+                            PlaceName = datalist[i][9:]
+                        else:
+                            PlaceName = datalist[i][9:29]+".."
+                                                                                          
                     if datalist[i][0:8] == "Comment=":
                         PlaceComment = datalist[i][8:]
+                    if datalist[i][0:12] == "Comment[%s]=" % self.lang:
+                        PlaceComment = datalist[i][12:]
+                        
                     if datalist[i][0:5] == "Exec=":
                         execstring = datalist[i][5:].replace("%u", "")
                         execstring = execstring.replace("%U", "")
@@ -895,6 +908,11 @@
                         else:
                             GenericName = datalist[i][12:32]+".."
 
+                    if datalist[i][0:16] == "GenericName[%s]=" % self.lang:
+                        if len(datalist[i][16:]) < 21:
+                            GenericName = datalist[i][16:]
+                        else:
+                            GenericName = datalist[i][16:32]+".."
 
                 if where == "place" or where == "software":
                     Button1 = gtk.Button(Button_Name,"ok",True)

```

Here is the messages.pot (extracted from the .glade file, for the translators)

```

# SOME DESCRIPTIVE TITLE.
# Copyright (C) YEAR THE PACKAGE'S COPYRIGHT HOLDER
# This file is distributed under the same license as the PACKAGE package.
# FIRST AUTHOR <EMAIL@ADDRESS>, YEAR.
#
#, fuzzy
msgid ""
msgstr ""
"Project-Id-Version: PACKAGE VERSION\n"
"Report-Msgid-Bugs-To: \n"
"POT-Creation-Date: 2006-08-02 11:24+0200\n"
"PO-Revision-Date: YEAR-MO-DA HO:MI+ZONE\n"
"Last-Translator: FULL NAME <EMAIL@ADDRESS>\n"
"Language-Team: LANGUAGE <LL@li.org>\n"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=CHARSET\n"
"Content-Transfer-Encoding: 8bit\n"

#: usp.glade:115 usp.glade:479
msgid "Places"
msgstr ""

#: usp.glade:181 usp.glade:917 usp.glade:1091
msgid "Applications"
msgstr ""

#: usp.glade:247
msgid "Settings"
msgstr ""

#: usp.glade:568
msgid "label42"
msgstr ""

#: usp.glade:598
msgid "System Management"
msgstr ""

#: usp.glade:663
msgid "Install Software"
msgstr ""

#: usp.glade:725 usp.glade:3012
msgid "Control Center"
msgstr ""

#: usp.glade:788
msgid "Lock screen"
msgstr ""

#: usp.glade:852
msgid "Quit..."
msgstr ""

#: usp.glade:972 usp.glade:2308 usp.glade:2392
msgid "Computer"
msgstr ""

#: usp.glade:1149
msgid "<span size=\"small\">All Applications</span>"
msgstr ""

#: usp.glade:1252
msgid "label78"
msgstr ""

#: usp.glade:1287
msgid "All Applications"
msgstr ""

#: usp.glade:1345
msgid "<span size=\"small\"> Applications</span>"
msgstr ""

#: usp.glade:1429
msgid "<span size=\"small\"> Accessories</span>"
msgstr ""

#: usp.glade:1487
msgid "<span size=\"small\"> Games</span>"
msgstr ""

#: usp.glade:1545
msgid "<span size=\"small\"> Graphics</span>"
msgstr ""

#: usp.glade:1603
msgid "<span size=\"small\"> Internet</span>"
msgstr ""

#: usp.glade:1661
msgid "<span size=\"small\"> Office</span>"
msgstr ""

#: usp.glade:1719
msgid "<span size=\"small\"> Programming</span>"
msgstr ""

#: usp.glade:1777
msgid "<span size=\"small\"> Sound and Video</span>"
msgstr ""

#: usp.glade:1835
msgid "<span size=\"small\"> System Tools</span>"
msgstr ""

#: usp.glade:1893
msgid "<span size=\"small\"> Settings</span>"
msgstr ""

#: usp.glade:1951
msgid "<span size=\"small\"> All</span>"
msgstr ""

#: usp.glade:2046
msgid "label100"
msgstr ""

#: usp.glade:2115
msgid "<span weight=\"bold\">More Applications...</span>"
msgstr ""

#: usp.glade:2174
msgid "Enter item to search"
msgstr ""

#: usp.glade:2216
msgid "Search"
msgstr ""

#: usp.glade:2516
msgid "Network"
msgstr ""

#: usp.glade:2640
msgid "Date and Time"
msgstr ""

#: usp.glade:2764
msgid "Theme"
msgstr ""

#: usp.glade:2888
msgid "Screen Resolution"
msgstr ""

#: usp.glade:3037
msgid "Configure your system"
msgstr ""

#: usp.glade:3133
msgid "Move up"
msgstr ""

#: usp.glade:3142
msgid "Move down"
msgstr ""

#: usp.glade:3151
msgid "Edit labels"
msgstr ""

#: usp.glade:3160
msgid "Insert separator"
msgstr ""

#: usp.glade:3169
msgid "Insert space"
msgstr ""

#: usp.glade:3178
msgid "Remove"
msgstr ""

#: usp.glade:3187
msgid "Edit item"
msgstr ""

#: usp.glade:3256
msgid "Name"
msgstr ""

#: usp.glade:3300
msgid "Generic name"
msgstr ""

#: usp.glade:3343
msgid "Comment"
msgstr ""

#: usp.glade:3386
msgid "Exec"
msgstr ""

#: usp.glade:3429
msgid "Icon"
msgstr ""

#: usp.glade:3484
msgid "Add to favourites"
msgstr ""

```

And here is the spanish .po file, fully working.
```

# SOME DESCRIPTIVE TITLE.
# Copyright (C) YEAR THE PACKAGE'S COPYRIGHT HOLDER
# This file is distributed under the same license as the PACKAGE package.
# FIRST AUTHOR <EMAIL@ADDRESS>, YEAR.
#
#, fuzzy
msgid ""
msgstr ""
"Project-Id-Version: usp 0.31\n"
"Report-Msgid-Bugs-To: \n"
"POT-Creation-Date: 2006-08-02 11:24+0200\n"
"PO-Revision-Date: 2006-08-02 11:24+02\n"
"Last-Translator: Von Pmg <vonpmg@gmail.com>\n"
"Language-Team: es <es@li.org>\n"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=utf-8\n"
"Content-Transfer-Encoding: 8bit\n"

#: usp.glade:115 usp.glade:479
msgid "Places"
msgstr "Lugares"

#: usp.glade:181 usp.glade:917 usp.glade:1091
msgid "Applications"
msgstr "Aplicaciones"

#: usp.glade:247
msgid "Settings"
msgstr "Preferencias"

#: usp.glade:568
msgid "label42"
msgstr "label42"

#: usp.glade:598
msgid "System Management"
msgstr "Administracion"

#: usp.glade:663
msgid "Install Software"
msgstr "Instalar aplicaciones"

#: usp.glade:725 usp.glade:3012
msgid "Control Center"
msgstr "Centro de Control"

#: usp.glade:788
msgid "Lock screen"
msgstr "Bloquear la pantalla"

#: usp.glade:852
msgid "Quit..."
msgstr "Salir..."

#: usp.glade:972 usp.glade:2308 usp.glade:2392
msgid "Computer"
msgstr "Ordenador"

#: usp.glade:1149
msgid "<span size=\"small\">All Applications</span>"
msgstr "<span size=\"small\">Todas las Aplicaciones</span>"

#: usp.glade:1252
msgid "label78"
msgstr "label78"

#: usp.glade:1287
msgid "All Applications"
msgstr "Todas las Aplicaciones"

#: usp.glade:1345
msgid "<span size=\"small\"> Applications</span>"
msgstr "<span size=\"small\"> Aplicaciones</span>"

#: usp.glade:1429
msgid "<span size=\"small\"> Accessories</span>"
msgstr "<span size=\"small\"> Accessorios</span>"

#: usp.glade:1487
msgid "<span size=\"small\"> Games</span>"
msgstr "<span size=\"small\"> Juegos</span>"

#: usp.glade:1545
msgid "<span size=\"small\"> Graphics</span>"
msgstr "<span size=\"small\"> Graficos</span>"

#: usp.glade:1603
msgid "<span size=\"small\"> Internet</span>"
msgstr "<span size=\"small\"> Internet</span>"

#: usp.glade:1661
msgid "<span size=\"small\"> Office</span>"
msgstr "<span size=\"small\"> Oficina</span>"

#: usp.glade:1719
msgid "<span size=\"small\"> Programming</span>"
msgstr "<span size=\"small\"> Programacion</span>"

#: usp.glade:1777
msgid "<span size=\"small\"> Sound and Video</span>"
msgstr "<span size=\"small\"> Sonido y Video</span>"

#: usp.glade:1835
msgid "<span size=\"small\"> System Tools</span>"
msgstr "<span size=\"small\"> Herramientas del Sistema</span>"

#: usp.glade:1893
msgid "<span size=\"small\"> Settings</span>"
msgstr "<span size=\"small\"> Preferencias</span>"

#: usp.glade:1951
msgid "<span size=\"small\"> All</span>"
msgstr "<span size=\"small\"> Todas</span>"

#: usp.glade:2046
msgid "label100"
msgstr "label100"

#: usp.glade:2115
msgid "<span weight=\"bold\">More Applications...</span>"
msgstr "<span weight=\"bold\">Mas Applicaciones...</span>"

#: usp.glade:2174
msgid "Enter item to search"
msgstr "Introduce el elemento a buscar"

#: usp.glade:2216
msgid "Search"
msgstr "Buscar"

#: usp.glade:2516
msgid "Network"
msgstr "Red"

#: usp.glade:2640
msgid "Date and Time"
msgstr "Fecha y Hora"

#: usp.glade:2764
msgid "Theme"
msgstr "Tema"

#: usp.glade:2888
msgid "Screen Resolution"
msgstr "Pantalla"

#: usp.glade:3037
msgid "Configure your system"
msgstr "Configurar tu sistema"

#: usp.glade:3133
msgid "Move up"
msgstr "Mover hacia arriba"

#: usp.glade:3142
msgid "Move down"
msgstr "Mover hacia abajo"

#: usp.glade:3151
msgid "Edit labels"
msgstr "Editar las etiquetas"

#: usp.glade:3160
msgid "Insert separator"
msgstr "Insertar un separador"

#: usp.glade:3169
msgid "Insert space"
msgstr "Insertar un espacio"

#: usp.glade:3178
msgid "Remove"
msgstr "Eliminar"

#: usp.glade:3187
msgid "Edit item"
msgstr "Editar el elemento"

#: usp.glade:3256
msgid "Name"
msgstr "Nombre"

#: usp.glade:3300
msgid "Generic name"
msgstr "Nombre generico"

#: usp.glade:3343
msgid "Comment"
msgstr "Comentario"

#: usp.glade:3386
msgid "Exec"
msgstr "Ejecutar"

#: usp.glade:3429
msgid "Icon"
msgstr "Icono"

#: usp.glade:3484
msgid "Add to favourites"
msgstr "Añadir a Favoritos"

```

Well. I hope you find it useful.
You can see also that i have added a few more lines to usp to "translate" the strings in the .desktop when you add it to favourites (not working).

---

### Post by _profox on 2006-08-02
It will come in handy :) I will get Dutch translation done.

---

### Post by Hells_Dark on 2006-08-02
Yeah, and i'm doing a french translation ;)

```
# SOME DESCRIPTIVE TITLE.
# Copyright (C) YEAR THE PACKAGE'S COPYRIGHT HOLDER
# This file is distributed under the same license as the PACKAGE package.
# FIRST AUTHOR <EMAIL@ADDRESS>, YEAR.
#
#, fuzzy
msgid ""
msgstr ""
"Project-Id-Version: usp 0.31\n"
"Report-Msgid-Bugs-To: \n"
"POT-Creation-Date: 2006-08-02 11:24+0200\n"
"PO-Revision-Date: 2006-08-02 11:24+02\n"
"Last-Translator: Von Pmg <vonpmg@gmail.com>\n"
"Language-Team: es <es@li.org>\n"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=utf-8\n"
"Content-Transfer-Encoding: 8bit\n"

#: usp.glade:115 usp.glade:479
msgid "Places"
msgstr "Raccourcis"

#: usp.glade:181 usp.glade:917 usp.glade:1091
msgid "Applications"
msgstr "Applications"

#: usp.glade:247
msgid "Settings"
msgstr "Préférences"

#: usp.glade:568
msgid "label42"
msgstr "label42"

#: usp.glade:598
msgid "System Management"
msgstr "Administration"

#: usp.glade:663
msgid "Install Software"
msgstr "Installer des applications"

#: usp.glade:725 usp.glade:3012
msgid "Control Center"
msgstr "Centre de Contrôle"

#: usp.glade:788
msgid "Lock screen"
msgstr "Verouiller l'écran"

#: usp.glade:852
msgid "Quit..."
msgstr "Quitter..."

#: usp.glade:972 usp.glade:2308 usp.glade:2392
msgid "Computer"
msgstr "Ordinateur"

#: usp.glade:1149
msgid "<span size=\"small\">All Applications</span>"
msgstr "<span size=\"small\">Toutes les Applications</span>"

#: usp.glade:1252
msgid "label78"
msgstr "label78"

#: usp.glade:1287
msgid "All Applications"
msgstr "Toutes les applications"

#: usp.glade:1345
msgid "<span size=\"small\"> Applications</span>"
msgstr "<span size=\"small\"> Applications</span>"

#: usp.glade:1429
msgid "<span size=\"small\"> Accessories</span>"
msgstr "<span size=\"small\"> Accessoires</span>"

#: usp.glade:1487
msgid "<span size=\"small\"> Games</span>"
msgstr "<span size=\"small\"> Jeux</span>"

#: usp.glade:1545
msgid "<span size=\"small\"> Graphics</span>"
msgstr "<span size=\"small\"> Images</span>"

#: usp.glade:1603
msgid "<span size=\"small\"> Internet</span>"
msgstr "<span size=\"small\"> Internet</span>"

#: usp.glade:1661
msgid "<span size=\"small\"> Office</span>"
msgstr "<span size=\"small\"> Bureautique</span>"

#: usp.glade:1719
msgid "<span size=\"small\"> Programming</span>"
msgstr "<span size=\"small\"> Programmation</span>"

#: usp.glade:1777
msgid "<span size=\"small\"> Sound and Video</span>"
msgstr "<span size=\"small\"> Son et Vidéo</span>"

#: usp.glade:1835
msgid "<span size=\"small\"> System Tools</span>"
msgstr "<span size=\"small\"> Outils système</span>"

#: usp.glade:1893
msgid "<span size=\"small\"> Settings</span>"
msgstr "<span size=\"small\"> Préférences</span>"

#: usp.glade:1951
msgid "<span size=\"small\"> All</span>"
msgstr "<span size=\"small\"> Toutes</span>"

#: usp.glade:2046
msgid "label100"
msgstr "label100"

#: usp.glade:2115
msgid "<span weight=\"bold\">More Applications...</span>"
msgstr "<span weight=\"bold\">Plus d'applications...</span>"

#: usp.glade:2174
msgid "Enter item to search"
msgstr "Entrez l'élément à chercher"

#: usp.glade:2216
msgid "Search"
msgstr "Chercher"

#: usp.glade:2516
msgid "Network"
msgstr "Réseau"

#: usp.glade:2640
msgid "Date and Time"
msgstr "Date et Heure"

#: usp.glade:2764
msgid "Theme"
msgstr "Thème"

#: usp.glade:2888
msgid "Screen Resolution"
msgstr "Résolution de l'écran"

#: usp.glade:3037
msgid "Configure your system"
msgstr "Configurer votre système"

#: usp.glade:3133
msgid "Move up"
msgstr "Monter"

#: usp.glade:3142
msgid "Move down"
msgstr "Descendre"

#: usp.glade:3151
msgid "Edit labels"
msgstr "Editer les étiquettes"

#: usp.glade:3160
msgid "Insert separator"
msgstr "Insérer un séparateur"

#: usp.glade:3169
msgid "Insert space"
msgstr "Insérer un espace"

#: usp.glade:3178
msgid "Remove"
msgstr "Enlever"

#: usp.glade:3187
msgid "Edit item"
msgstr "Editer l'étiquette"

#: usp.glade:3256
msgid "Name"
msgstr "Nom"

#: usp.glade:3300
msgid "Generic name"
msgstr "Nom Générique"

#: usp.glade:3343
msgid "Comment"
msgstr "Commentaire"

#: usp.glade:3386
msgid "Exec"
msgstr "Exécuter"

#: usp.glade:3429
msgid "Icon"
msgstr "Icône"

#: usp.glade:3484
msgid "Add to favourites"
msgstr "Ajouter aux favoris"
```

But i could do again few changes because
I asked the french community opinion on my translation ;)

---

### Post by Hells_Dark on 2006-08-02
[COLOR="Orange"]Oups, double post.[/COLOR]

---

### Post by lazyd2 on 2006-08-02
Maybe a dumb question, but what should I do if I wanted to translate USP into Greek?:oops:

---

### Post by _profox on 2006-08-02
Yea, there's something wrong with the ubuntu forums and doubleposting :P
Anyway, thanks for the translation. I will give you all credits for your translations when I add them.

---

### Post by vonpmg on 2006-08-03
Hi.
I have commited a patch to resolve the bug #54973  (System Management icons)
([https://launchpad.net/products/usp/+bug/54973](https://launchpad.net/products/usp/+bug/54973))
Somebody needs to review it. Chanders?
Hope it will be ok.

---

### Post by chanders on 2006-08-03
I have review both patches (Fixes Metacity focus bug) and (System Management icons) patch and they will both be included in the next release (later today hopefully)

@profoX - Can you send me the .diff for the Metacity bug?

@vonpmg - Welcome abord!

I have also setup subversion and will send you all the details when I am finished..

---

### Post by vonpmg on 2006-08-03
If you are going to make a new release i think you could add the already present translations.
Spanish and french, i think. They are in the forums and i have them in my Bazaar branch.
Glad to know the SVN repository.

---

### Post by _profox on 2006-08-04
Fixed bug: [https://launchpad.net/products/usp/+bug/54999](https://launchpad.net/products/usp/+bug/54999)

---

### Post by vonpmg on 2006-08-04
I have added the code to support translations, it is easy to translate it to your language.
I hope it will be added to the next version.
Here you have the file you should modify.
Fill the header and translate each string.
msgid "ORIGINAL STRING"
msgstr "YOUR TRANSLATION"

Ask if you have any question.

I have spanish and france translation (made by Hells_Dark),posted in forums
```

# SOME DESCRIPTIVE TITLE.
# Copyright (C) YEAR THE PACKAGE'S COPYRIGHT HOLDER
# This file is distributed under the same license as the PACKAGE package.
# FIRST AUTHOR <EMAIL@ADDRESS>, YEAR.
#
#, fuzzy
msgid ""
msgstr ""
"Project-Id-Version: PACKAGE VERSION\n"
"Report-Msgid-Bugs-To: \n"
"POT-Creation-Date: 2006-08-02 11:24+0200\n"
"PO-Revision-Date: YEAR-MO-DA HO:MI+ZONE\n"
"Last-Translator: FULL NAME <EMAIL@ADDRESS>\n"
"Language-Team: LANGUAGE <LL@li.org>\n"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=CHARSET\n"
"Content-Transfer-Encoding: 8bit\n"

#: usp.glade:115 usp.glade:479
msgid "Places"
msgstr ""

#: usp.glade:181 usp.glade:917 usp.glade:1091
msgid "Applications"
msgstr ""

#: usp.glade:247
msgid "Settings"
msgstr ""

#: usp.glade:568
msgid "label42"
msgstr ""

#: usp.glade:598
msgid "System Management"
msgstr ""

#: usp.glade:663
msgid "Install Software"
msgstr ""

#: usp.glade:725 usp.glade:3012
msgid "Control Center"
msgstr ""

#: usp.glade:788
msgid "Lock screen"
msgstr ""

#: usp.glade:852
msgid "Quit..."
msgstr ""

#: usp.glade:972 usp.glade:2308 usp.glade:2392
msgid "Computer"
msgstr ""

#: usp.glade:1149
msgid "<span size=\"small\">All Applications</span>"
msgstr ""

#: usp.glade:1252
msgid "label78"
msgstr ""

#: usp.glade:1287
msgid "All Applications"
msgstr ""

#: usp.glade:1345
msgid "<span size=\"small\"> Applications</span>"
msgstr ""

#: usp.glade:1429
msgid "<span size=\"small\"> Accessories</span>"
msgstr ""

#: usp.glade:1487
msgid "<span size=\"small\"> Games</span>"
msgstr ""

#: usp.glade:1545
msgid "<span size=\"small\"> Graphics</span>"
msgstr ""

#: usp.glade:1603
msgid "<span size=\"small\"> Internet</span>"
msgstr ""

#: usp.glade:1661
msgid "<span size=\"small\"> Office</span>"
msgstr ""

#: usp.glade:1719
msgid "<span size=\"small\"> Programming</span>"
msgstr ""

#: usp.glade:1777
msgid "<span size=\"small\"> Sound and Video</span>"
msgstr ""

#: usp.glade:1835
msgid "<span size=\"small\"> System Tools</span>"
msgstr ""

#: usp.glade:1893
msgid "<span size=\"small\"> Settings</span>"
msgstr ""

#: usp.glade:1951
msgid "<span size=\"small\"> All</span>"
msgstr ""

#: usp.glade:2046
msgid "label100"
msgstr ""

#: usp.glade:2115
msgid "<span weight=\"bold\">More Applications...</span>"
msgstr ""

#: usp.glade:2174
msgid "Enter item to search"
msgstr ""

#: usp.glade:2216
msgid "Search"
msgstr ""

#: usp.glade:2516
msgid "Network"
msgstr ""

#: usp.glade:2640
msgid "Date and Time"
msgstr ""

#: usp.glade:2764
msgid "Theme"
msgstr ""

#: usp.glade:2888
msgid "Screen Resolution"
msgstr ""

#: usp.glade:3037
msgid "Configure your system"
msgstr ""

#: usp.glade:3133
msgid "Move up"
msgstr ""

#: usp.glade:3142
msgid "Move down"
msgstr ""

#: usp.glade:3151
msgid "Edit labels"
msgstr ""

#: usp.glade:3160
msgid "Insert separator"
msgstr ""

#: usp.glade:3169
msgid "Insert space"
msgstr ""

#: usp.glade:3178
msgid "Remove"
msgstr ""

#: usp.glade:3187
msgid "Edit item"
msgstr ""

#: usp.glade:3256
msgid "Name"
msgstr ""

#: usp.glade:3300
msgid "Generic name"
msgstr ""

#: usp.glade:3343
msgid "Comment"
msgstr ""

#: usp.glade:3386
msgid "Exec"
msgstr ""

#: usp.glade:3429
msgid "Icon"
msgstr ""

#: usp.glade:3484
msgid "Add to favourites"
msgstr ""

```

---

### Post by chanders on 2006-08-04
I am testing the translation code and hopefully it will make it into the next release ;)

---

### Post by vonpmg on 2006-08-04
Chanders. I have sent you a private to comment about translations.
Is the first time i use it, you could read it.

---

### Post by chanders on 2006-08-04
> **vonpmg said:**
> Chanders. I have sent you a private to comment about translations.
Is the first time i use it, you could read it.

That is what I am testing ;)

---

### Post by _profox on 2006-08-04
#: usp.glade:568
msgid "label42"
msgstr ""

label42 ? what's that

---

### Post by vonpmg on 2006-08-04
The xgettext tool catch all the strings in the .glade file.
This is only the name of some control in the interface.
You could write label42 in the msgstr.
I post here a version without those "rare" strings.

```

# SOME DESCRIPTIVE TITLE.
# Copyright (C) YEAR THE PACKAGE'S COPYRIGHT HOLDER
# This file is distributed under the same license as the PACKAGE package.
# FIRST AUTHOR <EMAIL@ADDRESS>, YEAR.
#
#, fuzzy
msgid ""
msgstr ""
"Project-Id-Version: PACKAGE VERSION\n"
"Report-Msgid-Bugs-To: \n"
"POT-Creation-Date: 2006-08-02 11:24+0200\n"
"PO-Revision-Date: YEAR-MO-DA HO:MI+ZONE\n"
"Last-Translator: FULL NAME <EMAIL@ADDRESS>\n"
"Language-Team: LANGUAGE <LL@li.org>\n"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=CHARSET\n"
"Content-Transfer-Encoding: 8bit\n"

#: usp.glade:115 usp.glade:479
msgid "Places"
msgstr ""

#: usp.glade:181 usp.glade:917 usp.glade:1091
msgid "Applications"
msgstr ""

#: usp.glade:247
msgid "Settings"
msgstr ""

#: usp.glade:598
msgid "System Management"
msgstr ""

#: usp.glade:663
msgid "Install Software"
msgstr ""

#: usp.glade:725 usp.glade:3012
msgid "Control Center"
msgstr ""

#: usp.glade:788
msgid "Lock screen"
msgstr ""

#: usp.glade:852
msgid "Quit..."
msgstr ""

#: usp.glade:972 usp.glade:2308 usp.glade:2392
msgid "Computer"
msgstr ""

#: usp.glade:1149
msgid "<span size=\"small\">All Applications</span>"
msgstr ""

#: usp.glade:1287
msgid "All Applications"
msgstr ""

#: usp.glade:1345
msgid "<span size=\"small\"> Applications</span>"
msgstr ""

#: usp.glade:1429
msgid "<span size=\"small\"> Accessories</span>"
msgstr ""

#: usp.glade:1487
msgid "<span size=\"small\"> Games</span>"
msgstr ""

#: usp.glade:1545
msgid "<span size=\"small\"> Graphics</span>"
msgstr ""

#: usp.glade:1603
msgid "<span size=\"small\"> Internet</span>"
msgstr ""

#: usp.glade:1661
msgid "<span size=\"small\"> Office</span>"
msgstr ""

#: usp.glade:1719
msgid "<span size=\"small\"> Programming</span>"
msgstr ""

#: usp.glade:1777
msgid "<span size=\"small\"> Sound and Video</span>"
msgstr ""

#: usp.glade:1835
msgid "<span size=\"small\"> System Tools</span>"
msgstr ""

#: usp.glade:1893
msgid "<span size=\"small\"> Settings</span>"
msgstr ""

#: usp.glade:1951
msgid "<span size=\"small\"> All</span>"
msgstr ""

#: usp.glade:2115
msgid "<span weight=\"bold\">More Applications...</span>"
msgstr ""

#: usp.glade:2174
msgid "Enter item to search"
msgstr ""

#: usp.glade:2216
msgid "Search"
msgstr ""

#: usp.glade:2516
msgid "Network"
msgstr ""

#: usp.glade:2640
msgid "Date and Time"
msgstr ""

#: usp.glade:2764
msgid "Theme"
msgstr ""

#: usp.glade:2888
msgid "Screen Resolution"
msgstr ""

#: usp.glade:3037
msgid "Configure your system"
msgstr ""

#: usp.glade:3133
msgid "Move up"
msgstr ""

#: usp.glade:3142
msgid "Move down"
msgstr ""

#: usp.glade:3151
msgid "Edit labels"
msgstr ""

#: usp.glade:3160
msgid "Insert separator"
msgstr ""

#: usp.glade:3169
msgid "Insert space"
msgstr ""

#: usp.glade:3178
msgid "Remove"
msgstr ""

#: usp.glade:3187
msgid "Edit item"
msgstr ""

#: usp.glade:3256
msgid "Name"
msgstr ""

#: usp.glade:3300
msgid "Generic name"
msgstr ""

#: usp.glade:3343
msgid "Comment"
msgstr ""

#: usp.glade:3386
msgid "Exec"
msgstr ""

#: usp.glade:3429
msgid "Icon"
msgstr ""

#: usp.glade:3484
msgid "Add to favourites"
msgstr ""


```

Hope it is better now.

---

### Post by _profox on 2006-08-04
Something like this?

NL / Nederlands / Dutch

```
# Ubuntu System Panel 0.32 translation
# Copyright (C) 2006
# This file is distributed under the same license as the USP package.
# Wesley Stessens <profox@ubuntu-nl.org>, 2006.
#

msgid ""
msgstr ""
"Project-Id-Version: 0.32\n"
"Report-Msgid-Bugs-To: profox@ubuntu-nl.org\n"
"POT-Creation-Date: 2006-08-04 21:53+0200\n"
"PO-Revision-Date: 2006-08-04 21:53+0200\n"
"Last-Translator: Wesley Stessens <profox@ubuntu-nl.org>\n"
"Language-Team: Wesley Stessens <profox@ubuntu-nl.org>\n"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=CHARSET\n"
"Content-Transfer-Encoding: 8bit\n"

#: usp.glade:115 usp.glade:479
msgid "Places"
msgstr "Locaties"

#: usp.glade:181 usp.glade:917 usp.glade:1091
msgid "Applications"
msgstr "Programma's"

#: usp.glade:247
msgid "Settings"
msgstr "Instellingen"

#: usp.glade:568
msgid "label42"
msgstr "label42"

#: usp.glade:598
msgid "System Management"
msgstr "Systeembeheer"

#: usp.glade:663
msgid "Install Software"
msgstr "Software installeren"

#: usp.glade:725 usp.glade:3012
msgid "Control Center"
msgstr "Configuratiescherm"

#: usp.glade:788
msgid "Lock screen"
msgstr "Vergrendel scherm"

#: usp.glade:852
msgid "Quit..."
msgstr "Afsluiten..."

#: usp.glade:972 usp.glade:2308 usp.glade:2392
msgid "Computer"
msgstr "Computer"

#: usp.glade:1149
msgid "<span size=\"small\">All Applications</span>"
msgstr "<span size=\"small\">Alle Programma's</span>"

#: usp.glade:1252
msgid "label78"
msgstr "label78"

#: usp.glade:1287
msgid "All Applications"
msgstr "Alle Programma's"

#: usp.glade:1345
msgid "<span size=\"small\"> Applications</span>"
msgstr "<span size=\"small\"> Programma's</span>"

#: usp.glade:1429
msgid "<span size=\"small\"> Accessories</span>"
msgstr "<span size=\"small\"> Hulpmiddelen</span>"

#: usp.glade:1487
msgid "<span size=\"small\"> Games</span>"
msgstr "<span size=\"small\"> Spelletjes</span>"

#: usp.glade:1545
msgid "<span size=\"small\"> Graphics</span>"
msgstr "<span size=\"small\"> Grafisch</span>"

#: usp.glade:1603
msgid "<span size=\"small\"> Internet</span>"
msgstr "<span size=\"small\"> Internet</span>"

#: usp.glade:1661
msgid "<span size=\"small\"> Office</span>"
msgstr "<span size=\"small\"> Kantoor</span>"

#: usp.glade:1719
msgid "<span size=\"small\"> Programming</span>"
msgstr "<span size=\"small\"> Ontwikkeling</span>"

#: usp.glade:1777
msgid "<span size=\"small\"> Sound and Video</span>"
msgstr "<span size=\"small\"> Audio en video</span>"

#: usp.glade:1835
msgid "<span size=\"small\"> System Tools</span>"
msgstr "<span size=\"small\"> Systeemgereedschap</span>"

#: usp.glade:1893
msgid "<span size=\"small\"> Settings</span>"
msgstr "<span size=\"small\"> Instellingen</span>"

#: usp.glade:1951
msgid "<span size=\"small\"> All</span>"
msgstr "<span size=\"small\"> Alles</span>"

#: usp.glade:2046
msgid "label100"
msgstr "label100"

#: usp.glade:2115
msgid "<span weight=\"bold\">More Applications...</span>"
msgstr "<span weight=\"bold\">Meer Programma's...</span>"

#: usp.glade:2174
msgid "Enter item to search"
msgstr "Typ hier iets om naar te zoeken"

#: usp.glade:2216
msgid "Search"
msgstr "Zoeken"

#: usp.glade:2516
msgid "Network"
msgstr "Netwerk"

#: usp.glade:2640
msgid "Date and Time"
msgstr "Datum en Tijd"

#: usp.glade:2764
msgid "Theme"
msgstr "Thema"

#: usp.glade:2888
msgid "Screen Resolution"
msgstr "Schermresolutie"

#: usp.glade:3037
msgid "Configure your system"
msgstr "Configureer uw systeem"

#: usp.glade:3133
msgid "Move up"
msgstr "Naar boven"

#: usp.glade:3142
msgid "Move down"
msgstr "Naar beneden"

#: usp.glade:3151
msgid "Edit labels"
msgstr "Labels aanpassen"

#: usp.glade:3160
msgid "Insert separator"
msgstr "Scheidingslijn invoegen"

#: usp.glade:3169
msgid "Insert space"
msgstr "Spatie invoegen"

#: usp.glade:3178
msgid "Remove"
msgstr "Verwijderen"

#: usp.glade:3187
msgid "Edit item"
msgstr "Item aanpassen"

#: usp.glade:3256
msgid "Name"
msgstr "Naam"

#: usp.glade:3300
msgid "Generic name"
msgstr "Algemene naam"

#: usp.glade:3343
msgid "Comment"
msgstr "Commentaar"

#: usp.glade:3386
msgid "Exec"
msgstr "Uitvoeren"

#: usp.glade:3429
msgid "Icon"
msgstr "Icon"

#: usp.glade:3484
msgid "Add to favourites"
msgstr "Toevoegen aan favorieten"
```

---

### Post by vonpmg on 2006-08-05
Yes, that's right.
When chandlers add the translation support, we could add all the languages we allready have (es,fr,nl)

---

### Post by lazyd2 on 2006-08-05
I can add a Greek translation if you want...

---

### Post by chanders on 2006-08-05
> **lazyd2 said:**
> I can add a Greek translation if you want...

Sure go ahead! I have to choose between working on the translation code and plugins... :(

---

### Post by delfick on 2006-08-05
> **chanders said:**
> Sure go ahead! I have to choose between working on the translation code and plugins... :(

work on plugins!!! :D

(from a biased point of view that it is already in my language, u don't need translations)

(from me trying to find a reason...if u do the plugins first then translations won't have to be redone later...?)

---

### Post by lazyd2 on 2006-08-05
> **chanders said:**
> Sure go ahead! I have to choose between working on the translation code and plugins... :(

So I copy this
```
# SOME DESCRIPTIVE TITLE.
# Copyright (C) YEAR THE PACKAGE'S COPYRIGHT HOLDER
# This file is distributed under the same license as the PACKAGE package.
# FIRST AUTHOR <EMAIL@ADDRESS>, YEAR.
#
#, fuzzy
msgid ""
msgstr ""
"Project-Id-Version: PACKAGE VERSION\n"
"Report-Msgid-Bugs-To: \n"
"POT-Creation-Date: 2006-08-02 11:24+0200\n"
"PO-Revision-Date: YEAR-MO-DA HO:MI+ZONE\n"
"Last-Translator: FULL NAME <EMAIL@ADDRESS>\n"
"Language-Team: LANGUAGE <LL@li.org>\n"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=CHARSET\n"
"Content-Transfer-Encoding: 8bit\n"

#: usp.glade:115 usp.glade:479
msgid "Places"
msgstr ""

#: usp.glade:181 usp.glade:917 usp.glade:1091
msgid "Applications"
msgstr ""

#: usp.glade:247
msgid "Settings"
msgstr ""

#: usp.glade:598
msgid "System Management"
msgstr ""

#: usp.glade:663
msgid "Install Software"
msgstr ""

#: usp.glade:725 usp.glade:3012
msgid "Control Center"
msgstr ""

#: usp.glade:788
msgid "Lock screen"
msgstr ""

#: usp.glade:852
msgid "Quit..."
msgstr ""

#: usp.glade:972 usp.glade:2308 usp.glade:2392
msgid "Computer"
msgstr ""

#: usp.glade:1149
msgid "<span size=\"small\">All Applications</span>"
msgstr ""

#: usp.glade:1287
msgid "All Applications"
msgstr ""

#: usp.glade:1345
msgid "<span size=\"small\"> Applications</span>"
msgstr ""

#: usp.glade:1429
msgid "<span size=\"small\"> Accessories</span>"
msgstr ""

#: usp.glade:1487
msgid "<span size=\"small\"> Games</span>"
msgstr ""

#: usp.glade:1545
msgid "<span size=\"small\"> Graphics</span>"
msgstr ""

#: usp.glade:1603
msgid "<span size=\"small\"> Internet</span>"
msgstr ""

#: usp.glade:1661
msgid "<span size=\"small\"> Office</span>"
msgstr ""

#: usp.glade:1719
msgid "<span size=\"small\"> Programming</span>"
msgstr ""

#: usp.glade:1777
msgid "<span size=\"small\"> Sound and Video</span>"
msgstr ""

#: usp.glade:1835
msgid "<span size=\"small\"> System Tools</span>"
msgstr ""

#: usp.glade:1893
msgid "<span size=\"small\"> Settings</span>"
msgstr ""

#: usp.glade:1951
msgid "<span size=\"small\"> All</span>"
msgstr ""

#: usp.glade:2115
msgid "<span weight=\"bold\">More Applications...</span>"
msgstr ""

#: usp.glade:2174
msgid "Enter item to search"
msgstr ""

#: usp.glade:2216
msgid "Search"
msgstr ""

#: usp.glade:2516
msgid "Network"
msgstr ""

#: usp.glade:2640
msgid "Date and Time"
msgstr ""

#: usp.glade:2764
msgid "Theme"
msgstr ""

#: usp.glade:2888
msgid "Screen Resolution"
msgstr ""

#: usp.glade:3037
msgid "Configure your system"
msgstr ""

#: usp.glade:3133
msgid "Move up"
msgstr ""

#: usp.glade:3142
msgid "Move down"
msgstr ""

#: usp.glade:3151
msgid "Edit labels"
msgstr ""

#: usp.glade:3160
msgid "Insert separator"
msgstr ""

#: usp.glade:3169
msgid "Insert space"
msgstr ""

#: usp.glade:3178
msgid "Remove"
msgstr ""

#: usp.glade:3187
msgid "Edit item"
msgstr ""

#: usp.glade:3256
msgid "Name"
msgstr ""

#: usp.glade:3300
msgid "Generic name"
msgstr ""

#: usp.glade:3343
msgid "Comment"
msgstr ""

#: usp.glade:3386
msgid "Exec"
msgstr ""

#: usp.glade:3429
msgid "Icon"
msgstr ""

#: usp.glade:3484
msgid "Add to favourites"
msgstr ""

```

...and proceed?(newby asking):-$

---

### Post by vonpmg on 2006-08-06
Is very simple Lazyd2.
Supouse, in Greek "Places" is "Lugares" (Sorry i speak spanish not greek ;) )
So you only have to put "Lugares" (The greek translation for "Places") in the msgstr below Places.
The same for all the strings.
Then you Cut & paste the file here between the code tags.
I hope this help you.
See the _profox post with his nl translation above.

And, Chanders, go with plugins.
The translation support is 3 lines, but the plugins support i think is very important.
Anyway .... we all can speak english ;) (More or less)

---

### Post by fantan on 2006-08-06
Hi,

First, sorry for my bad English, but I'm Hungarian and my name is Albert Fazakas.
Also I did a translation to Hungarian. I don't know exactly, what to do with it, because of this I send it to you. I think, you know how to include this translation to one of the next version of the program.

The USP I use now (0.32), is very-very nice, I like it very much.

Thanks a lot for your hard work with it!

fantan

---

### Post by fantan on 2006-08-06
[HTML]
# SOME DESCRIPTIVE TITLE.
# Copyright (C) YEAR THE PACKAGE'S COPYRIGHT HOLDER
# This file is distributed under the same license as the PACKAGE package.
# Albert Fazakas <fantan@axelero.hu>, 2006.
#
#, fuzzy
msgid ""
msgstr ""
"Project-Id-Version: 0.32\n"
"Report-Msgid-Bugs-To: \n"
"POT-Creation-Date: 2006-08-02 11:24+0200\n"
"PO-Revision-Date: 2006-08-06 11:24+0100\n"
"Last-Translator: Albert Fazakas <fantan@axelero.hu>\n"
"Language-Team: Albert Fazakas <fantan@axelero.hu>\n"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=hu_HU.UTF-8\n"
"Content-Transfer-Encoding: 8bit\n"

#: usp.glade:115 usp.glade:479
msgid "Places"
msgstr "Helyek"

#: usp.glade:181 usp.glade:917 usp.glade:1091
msgid "Applications"
msgstr "Alkalmazások"

#: usp.glade:247
msgid "Settings"
msgstr "Beállítások"

#: usp.glade:598
msgid "System Management"
msgstr "Adminisztráció"

#: usp.glade:663
msgid "Install Software"
msgstr "Szoftver telepítés"

#: usp.glade:725 usp.glade:3012
msgid "Control Center"
msgstr "Vezérl&#337;központ"

#: usp.glade:788
msgid "Lock screen"
msgstr "Képerny&#337;zár"

#: usp.glade:852
msgid "Quit..."
msgstr "Kilépés..."

#: usp.glade:972 usp.glade:2308 usp.glade:2392
msgid "Computer"
msgstr "Számítógép"

#: usp.glade:1149
msgid "<span size=\"small\">All Applications</span>"
msgstr "<span size=\"small\"Minden alkalmazás</span>"

#: usp.glade:1287
msgid "All Applications"
msgstr "Minden alkalmazás"

#: usp.glade:1345
msgid "<span size=\"small\"> Applications</span>"
msgstr "<span size=\"small\"> Alkalmazások</span>"

#: usp.glade:1429
msgid "<span size=\"small\"> Accessories</span>"
msgstr "<span size=\"small\"> Kellékek</span>"

#: usp.glade:1487
msgid "<span size=\"small\"> Games</span>"
msgstr "<span size=\"small\"> Játékok</span>"

#: usp.glade:1545
msgid "<span size=\"small\"> Graphics</span>"
msgstr "<span size=\"small\"> Grafika</span>"

#: usp.glade:1603
msgid "<span size=\"small\"> Internet</span>"
msgstr "<span size=\"small\"> Internet</span>"

#: usp.glade:1661
msgid "<span size=\"small\"> Office</span>"
msgstr "<span size=\"small\"> Iroda</span>"

#: usp.glade:1719
msgid "<span size=\"small\"> Programming</span>"
msgstr "<span size=\"small\"> Programozás</span>"

#: usp.glade:1777
msgid "<span size=\"small\"> Sound and Video</span>"
msgstr "<span size=\"small\"> Audio és Video</span>"

#: usp.glade:1835
msgid "<span size=\"small\"> System Tools</span>"
msgstr "<span size=\"small\"> Rendszereszközök</span>"

#: usp.glade:1893
msgid "<span size=\"small\"> Settings</span>"
msgstr "<span size=\"small\"> Beállítások</span>"

#: usp.glade:1951
msgid "<span size=\"small\"> All</span>"
msgstr "<span size=\"small\"> Minden</span>"

#: usp.glade:2115
msgid "<span weight=\"bold\">More Applications...</span>"
msgstr "<span weight=\"bold\">További alkalmazások...</span>"

#: usp.glade:2174
msgid "Enter item to search"
msgstr "Írd be, mit keressek"

#: usp.glade:2216
msgid "Search"
msgstr "Keresés"

#: usp.glade:2516
msgid "Network"
msgstr "Hálózat"

#: usp.glade:2640
msgid "Date and Time"
msgstr "Dátum és id&#337;"

#: usp.glade:2764
msgid "Theme"
msgstr "Téma"

#: usp.glade:2888
msgid "Screen Resolution"
msgstr "Képerny&#337; felbontás"

#: usp.glade:3037
msgid "Configure your system"
msgstr "Rendszerkonfigurálás"

#: usp.glade:3133
msgid "Move up"
msgstr "Mozgatás fel"

#: usp.glade:3142
msgid "Move down"
msgstr "Mozgatás le"

#: usp.glade:3151
msgid "Edit labels"
msgstr "Cimkék módosítása"

#: usp.glade:3160
msgid "Insert separator"
msgstr "Elválasztó csík beszúrása"

#: usp.glade:3169
msgid "Insert space"
msgstr "Üres hely beszúrása"

#: usp.glade:3178
msgid "Remove"
msgstr "Eltávolítás"

#: usp.glade:3187
msgid "Edit item"
msgstr "Tétel módosítása"

#: usp.glade:3256
msgid "Name"
msgstr "Név"

#: usp.glade:3300
msgid "Generic name"
msgstr "Általános név"

#: usp.glade:3343
msgid "Comment"
msgstr "Megjegyzés"

#: usp.glade:3386
msgid "Exec"
msgstr "Futtatás"

#: usp.glade:3429
msgid "Icon"
msgstr "Ikon"

#: usp.glade:3484
msgid "Add to favourites"
msgstr "Hozzáadás a kedvencekhez"
[/HTML]

I didn't know, how to insert a quote, hope now will be fine. 
fantan

---

### Post by vonpmg on 2006-08-06
Thanks a lot fantan. :-D 
Well done.
I am sure Chanders will add it in the first version with translation support.
We have several translations now.
Anyone want to make another?

---

### Post by lazyd2 on 2006-08-06
Greek translation:

```
# SOME DESCRIPTIVE TITLE.
# Copyright (C) YEAR THE PACKAGE'S COPYRIGHT HOLDER
# This file is distributed under the same license as the PACKAGE package.
# Arion Tsakirakis <arion24@gmail.com>, 2006.
#
#, fuzzy
msgid ""
msgstr ""
"Project-Id-Version: 0.32\n"
"Report-Msgid-Bugs-To: \n"
"POT-Creation-Date: 2006-08-02 11:24+0200\n"
"PO-Revision-Date: YEAR-MO-DA HO:MI+ZONE\n"
"Last-Translator: Arion Tsakirakis <arion24@gmail.com>\n"
"Language-Team: Arion Tsakirakis <arion24@gmail.com>\n"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=el_GR.UTF-8\n"
"Content-Transfer-Encoding: 8bit\n"

#: usp.glade:115 usp.glade:479
msgid "Places"
msgstr "&#932;&#959;&#960;&#959;&#952;&#949;&#963;&#943;&#949;&#962;"

#: usp.glade:181 usp.glade:917 usp.glade:1091
msgid "Applications"
msgstr "&#917;&#966;&#945;&#961;&#956;&#959;&#947;&#941;&#962;"

#: usp.glade:247
msgid "Settings"
msgstr "&#929;&#965;&#952;&#956;&#943;&#963;&#949;&#953;&#962;"

#: usp.glade:598
msgid "System Management"
msgstr "&#916;&#953;&#945;&#967;&#949;&#943;&#961;&#953;&#963;&#951; &#931;&#965;&#963;&#964;&#942;&#956;&#945;&#964;&#959;&#962;"

#: usp.glade:663
msgid "Install Software"
msgstr "&#917;&#947;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; &#923;&#959;&#947;&#953;&#963;&#956;&#953;&#954;&#959;&#973;"

#: usp.glade:725 usp.glade:3012
msgid "Control Center"
msgstr "&#922;&#941;&#957;&#964;&#961;&#959; &#917;&#955;&#941;&#947;&#967;&#959;&#965;"

#: usp.glade:788
msgid "Lock screen"
msgstr "&#922;&#955;&#949;&#943;&#948;&#969;&#956;&#945; &#927;&#952;&#972;&#957;&#951;&#962;"

#: usp.glade:852
msgid "Quit..."
msgstr "&#904;&#958;&#959;&#948;&#959;&#962;"

#: usp.glade:972 usp.glade:2308 usp.glade:2392
msgid "Computer"
msgstr "&#933;&#960;&#959;&#955;&#959;&#947;&#953;&#963;&#964;&#942;&#962;"

#: usp.glade:1149
msgid "<span size=\"small\">All Applications</span>"
msgstr "<span size=\"small\">&#908;&#955;&#949;&#962; &#959;&#953; &#949;&#966;&#945;&#961;&#956;&#959;&#947;&#941;&#962;</span>"

#: usp.glade:1287
msgid "All Applications"
msgstr "&#908;&#955;&#949;&#962; &#959;&#953; &#949;&#966;&#945;&#961;&#956;&#959;&#947;&#941;&#962;"

#: usp.glade:1345
msgid "<span size=\"small\"> Applications</span>"
msgstr "<span size=\"small\"> &#917;&#966;&#945;&#961;&#956;&#959;&#947;&#941;&#962;</span>"

#: usp.glade:1429
msgid "<span size=\"small\"> Accessories</span>"
msgstr "<span size=\"small\"> &#914;&#959;&#951;&#952;&#942;&#956;&#945;&#964;&#945;</span>"

#: usp.glade:1487
msgid "<span size=\"small\"> Games</span>"
msgstr "<span size=\"small\"> &#928;&#945;&#953;&#967;&#957;&#943;&#948;&#953;&#945;</span>"

#: usp.glade:1545
msgid "<span size=\"small\"> Graphics</span>"
msgstr "<span size=\"small\"> &#915;&#961;&#945;&#966;&#953;&#954;&#940;</span>"

#: usp.glade:1603
msgid "<span size=\"small\"> Internet</span>"
msgstr "<span size=\"small\"> &#916;&#953;&#945;&#948;&#973;&#954;&#964;&#953;&#959;</span>"

#: usp.glade:1661
msgid "<span size=\"small\"> Office</span>"
msgstr "<span size=\"small\"> &#915;&#961;&#945;&#966;&#949;&#943;&#959;</span>"

#: usp.glade:1719
msgid "<span size=\"small\"> Programming</span>"
msgstr "<span size=\"small\"> &#928;&#961;&#959;&#947;&#961;&#945;&#956;&#956;&#945;&#964;&#953;&#963;&#956;&#972;&#962;</span>"

#: usp.glade:1777
msgid "<span size=\"small\"> Sound and Video</span>"
msgstr "<span size=\"small\"> &#905;&#967;&#959;&#962; &#954;&#945;&#953; &#914;&#943;&#957;&#964;&#949;&#959;</span>"

#: usp.glade:1835
msgid "<span size=\"small\"> System Tools</span>"
msgstr "<span size=\"small\"> &#917;&#961;&#947;&#945;&#955;&#949;&#943;&#945; &#931;&#965;&#963;&#964;&#942;&#956;&#945;&#964;&#959;&#962;</span>"

#: usp.glade:1893
msgid "<span size=\"small\"> Settings</span>"
msgstr "<span size=\"small\"> &#928;&#961;&#959;&#964;&#953;&#956;&#942;&#963;&#949;&#953;&#962;</span>"

#: usp.glade:1951
msgid "<span size=\"small\"> All</span>"
msgstr "<span size=\"small\"> &#908;&#955;&#949;&#962;</span>"

#: usp.glade:2115
msgid "<span weight=\"bold\">More Applications...</span>"
msgstr "<span weight=\"bold\">&#928;&#949;&#961;&#953;&#963;&#963;&#972;&#964;&#949;&#961;&#949;&#962; &#917;&#966;&#945;&#961;&#956;&#959;&#947;&#941;&#962;...</span>"

#: usp.glade:2174
msgid "Enter item to search"
msgstr "&#917;&#953;&#963;&#945;&#947;&#969;&#947;&#942; &#945;&#957;&#964;&#953;&#954;&#949;&#953;&#956;&#941;&#957;&#959;&#965; &#960;&#961;&#959;&#962; &#945;&#957;&#945;&#950;&#942;&#964;&#951;&#963;&#951;"

#: usp.glade:2216
msgid "Search"
msgstr "&#913;&#957;&#945;&#950;&#942;&#964;&#951;&#963;&#951;"

#: usp.glade:2516
msgid "Network"
msgstr "&#916;&#943;&#954;&#964;&#965;&#959;"

#: usp.glade:2640
msgid "Date and Time"
msgstr "&#911;&#961;&#945; &#954;&#945;&#953; &#919;&#956;&#949;&#961;&#959;&#956;&#951;&#957;&#943;&#945;"

#: usp.glade:2764
msgid "Theme"
msgstr "&#920;&#941;&#956;&#945;"

#: usp.glade:2888
msgid "Screen Resolution"
msgstr "&#913;&#957;&#940;&#955;&#965;&#963;&#951; &#927;&#952;&#972;&#957;&#951;&#962;"

#: usp.glade:3037
msgid "Configure your system"
msgstr "&#916;&#953;&#945;&#956;&#972;&#961;&#966;&#969;&#963;&#951; &#931;&#965;&#963;&#964;&#942;&#956;&#945;&#964;&#959;&#962;"

#: usp.glade:3133
msgid "Move up"
msgstr "&#924;&#949;&#964;&#945;&#954;&#943;&#957;&#951;&#963;&#951; &#949;&#960;&#940;&#957;&#969;"

#: usp.glade:3142
msgid "Move down"
msgstr "&#924;&#949;&#964;&#945;&#954;&#943;&#957;&#951;&#963;&#951; &#954;&#940;&#964;&#969;"

#: usp.glade:3151
msgid "Edit labels"
msgstr "&#917;&#960;&#949;&#958;&#949;&#961;&#947;&#945;&#963;&#943;&#945; &#949;&#964;&#953;&#954;&#949;&#964;&#974;&#957;"

#: usp.glade:3160
msgid "Insert separator"
msgstr "&#917;&#953;&#963;&#945;&#947;&#969;&#947;&#942; &#948;&#953;&#945;&#967;&#969;&#961;&#953;&#963;&#964;&#942;"

#: usp.glade:3169
msgid "Insert space"
msgstr "&#917;&#953;&#963;&#945;&#947;&#969;&#947;&#942; &#948;&#953;&#945;&#963;&#964;&#942;&#956;&#945;&#964;&#959;&#962;"

#: usp.glade:3178
msgid "Remove"
msgstr "&#913;&#966;&#945;&#943;&#961;&#949;&#963;&#951;"

#: usp.glade:3187
msgid "Edit item"
msgstr "&#917;&#960;&#949;&#958;&#949;&#961;&#947;&#945;&#963;&#943;&#945; &#945;&#957;&#964;&#953;&#954;&#949;&#953;&#956;&#941;&#957;&#959;&#965;"

#: usp.glade:3256
msgid "Name"
msgstr "&#908;&#957;&#959;&#956;&#945;"

#: usp.glade:3300
msgid "Generic name"
msgstr "&#915;&#949;&#957;&#953;&#954;&#972; &#972;&#957;&#959;&#956;&#945;"

#: usp.glade:3343
msgid "Comment"
msgstr "&#931;&#967;&#972;&#955;&#953;&#959;"

#: usp.glade:3386
msgid "Exec"
msgstr "&#917;&#957;&#964;&#959;&#955;&#942;"

#: usp.glade:3429
msgid "Icon"
msgstr "&#917;&#953;&#954;&#959;&#957;&#943;&#948;&#953;&#959;"

#: usp.glade:3484
msgid "Add to favourites"
msgstr "&#928;&#961;&#972;&#963;&#952;&#949;&#963;&#951; &#963;&#964;&#945; &#945;&#947;&#945;&#960;&#951;&#956;&#941;&#957;&#945;"

```

---

### Post by fantan on 2006-08-07
Hi again,

Today, after downloading the new version (0.33-1) I realised, that yesterday did an error in the translation.

I send the fixed version of the Hungarian translation now.

Please get it:
> 
# SOME DESCRIPTIVE TITLE.
# Copyright (C) YEAR THE PACKAGE'S COPYRIGHT HOLDER
# This file is distributed under the same license as the PACKAGE package.
# Albert Fazakas <fantan@axelero.hu>, 2006.
#
#, fuzzy
msgid ""
msgstr ""
"Project-Id-Version: 0.32\n"
"Report-Msgid-Bugs-To: \n"
"POT-Creation-Date: 2006-08-02 11:24+0200\n"
"PO-Revision-Date: 2006-08-07 11:24+0100\n"
"Last-Translator: Albert Fazakas <fantan@axelero.hu>\n"
"Language-Team: Albert Fazakas <fantan@axelero.hu>\n"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=hu_HU.UTF-8\n"
"Content-Transfer-Encoding: 8bit\n"

#: usp.glade:115 usp.glade:479
msgid "Places"
msgstr "Helyek"

#: usp.glade:181 usp.glade:917 usp.glade:1091
msgid "Applications"
msgstr "Alkalmazások"

#: usp.glade:247
msgid "Settings"
msgstr "Beállítások"

#: usp.glade:598
msgid "System Management"
msgstr "Adminisztráció"

#: usp.glade:663
msgid "Install Software"
msgstr "Szoftver telepítés"

#: usp.glade:725 usp.glade:3012
msgid "Control Center"
msgstr "Vezérl&#337;központ"

#: usp.glade:788
msgid "Lock screen"
msgstr "Képerny&#337;zár"

#: usp.glade:852
msgid "Quit..."
msgstr "Kilépés..."

#: usp.glade:972 usp.glade:2308 usp.glade:2392
msgid "Computer"
msgstr "Számítógép"

## 
#: usp.glade:1149
msgid "<span size=\"small\">All Applications</span>"
#msgstr "<span size=\"small\"Minden alkalmazás</span>" # I found the error in this line: the ">" character is missing
msgstr "<span size=\"small\">Minden alkalmazás</span>" # this is the fixed line with the ">" character

#: usp.glade:1287
msgid "All Applications"
msgstr "Minden alkalmazás"

#: usp.glade:1345
msgid "<span size=\"small\"> Applications</span>"
msgstr "<span size=\"small\"> Alkalmazások</span>"

#: usp.glade:1429
msgid "<span size=\"small\"> Accessories</span>"
msgstr "<span size=\"small\"> Kellékek</span>"

#: usp.glade:1487
msgid "<span size=\"small\"> Games</span>"
msgstr "<span size=\"small\"> Játékok</span>"

#: usp.glade:1545
msgid "<span size=\"small\"> Graphics</span>"
msgstr "<span size=\"small\"> Grafika</span>"

#: usp.glade:1603
msgid "<span size=\"small\"> Internet</span>"
msgstr "<span size=\"small\"> Internet</span>"

#: usp.glade:1661
msgid "<span size=\"small\"> Office</span>"
msgstr "<span size=\"small\"> Iroda</span>"

#: usp.glade:1719
msgid "<span size=\"small\"> Programming</span>"
msgstr "<span size=\"small\"> Programozás</span>"

#: usp.glade:1777
msgid "<span size=\"small\"> Sound and Video</span>"
msgstr "<span size=\"small\"> Audio és Video</span>"

#: usp.glade:1835
msgid "<span size=\"small\"> System Tools</span>"
msgstr "<span size=\"small\"> Rendszereszközök</span>"

#: usp.glade:1893
msgid "<span size=\"small\"> Settings</span>"
msgstr "<span size=\"small\"> Beállítások</span>"

#: usp.glade:1951
msgid "<span size=\"small\"> All</span>"
msgstr "<span size=\"small\"> Minden</span>"

#: usp.glade:2115
msgid "<span weight=\"bold\">More Applications...</span>"
msgstr "<span weight=\"bold\">További alkalmazások...</span>"

#: usp.glade:2174
msgid "Enter item to search"
msgstr "Írd be, mit keressek"

#: usp.glade:2216
msgid "Search"
msgstr "Keresés"

#: usp.glade:2516
msgid "Network"
msgstr "Hálózat"

#: usp.glade:2640
msgid "Date and Time"
msgstr "Dátum és id&#337;"

#: usp.glade:2764
msgid "Theme"
msgstr "Téma"

#: usp.glade:2888
msgid "Screen Resolution"
msgstr "Képerny&#337; felbontás"

#: usp.glade:3037
msgid "Configure your system"
msgstr "Rendszerkonfigurálás"

#: usp.glade:3133
msgid "Move up"
msgstr "Mozgatás fel"

#: usp.glade:3142
msgid "Move down"
msgstr "Mozgatás le"

#: usp.glade:3151
msgid "Edit labels"
msgstr "Cimkék módosítása"

#: usp.glade:3160
msgid "Insert separator"
msgstr "Elválasztó csík beszúrása"

#: usp.glade:3169
msgid "Insert space"
msgstr "Üres hely beszúrása"

#: usp.glade:3178
msgid "Remove"
msgstr "Eltávolítás"

#: usp.glade:3187
msgid "Edit item"
msgstr "Tétel módosítása"

#: usp.glade:3256
msgid "Name"
msgstr "Név"

#: usp.glade:3300
msgid "Generic name"
msgstr "Általános név"

#: usp.glade:3343
msgid "Comment"
msgstr "Megjegyzés"

#: usp.glade:3386
msgid "Exec"
msgstr "Futtatás"

#: usp.glade:3429
msgid "Icon"
msgstr "Ikon"

#: usp.glade:3484
msgid "Add to favourites"
msgstr "Hozzáadás a kedvencekhez"


Please change the Hungarian locale with this fixed version.

fantan

---

### Post by fantan on 2006-08-07
Hi Developers,

In conjunkcion with the "Favorites" problem, to solve it, I made a new Hungarian translation of the locale file.
Please compile it again, and change the originale usp.mo with the new version, and at the same time send it to this forum too.

> 
#SOME DESCRIPTIVE TITLE.
# Copyright (C) YEAR THE PACKAGE'S COPYRIGHT HOLDER
# This file is distributed under the same license as the PACKAGE package.
# Albert Fazakas <fantan@axelero.hu>, 2006.
# This is the second fix.
#, fuzzy
msgid ""
msgstr ""
"Project-Id-Version: 0.32\n"
"Report-Msgid-Bugs-To: \n"
"POT-Creation-Date: 2006-08-02 11:24+0200\n"
"PO-Revision-Date: 2006-08-07 11:24+0100\n"
"Last-Translator: Albert Fazakas <fantan@axelero.hu>\n"
"Language-Team: Albert Fazakas <fantan@axelero.hu>\n"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=hu_HU.UTF-8\n"
"Content-Transfer-Encoding: 8bit\n"

#: usp.glade:115 usp.glade:479
msgid "Places"
msgstr "Helyek"

#: usp.glade:181 usp.glade:917 usp.glade:1091
msgid "Applications"
msgstr "Alkalmazások"

#: usp.glade:247
msgid "Settings"
msgstr "Beállítások"

#: usp.glade:598
msgid "System Management"
msgstr "Adminisztráció"

#: usp.glade:663
msgid "Install Software"
msgstr "Szoftver telepítés"

#: usp.glade:725 usp.glade:3012
msgid "Control Center"
msgstr "Vezérl&#337;központ"

#: usp.glade:788
msgid "Lock screen"
msgstr "Képerny&#337;zár"

#: usp.glade:852
msgid "Quit..."
msgstr "Kilépés..."

#: usp.glade:972 usp.glade:2308 usp.glade:2392
msgid "Computer"
msgstr "Számítógép"

## 
#: usp.glade:1149
msgid "<span size=\"small\">All Applications</span>"
msgstr "<span size=\"small\">Minden alkalmazás</span>"

#: usp.glade:1287
msgid "All Applications"
msgstr "Minden alkalmazás"

#: usp.glade:1345
msgid "<span size=\"small\"> Applications</span>" # fix
msgstr "<span size=\"small\"> Kedvencek</span>" # fix

#: usp.glade:1429
msgid "<span size=\"small\"> Accessories</span>"
msgstr "<span size=\"small\"> Kellékek</span>"

#: usp.glade:1487
msgid "<span size=\"small\"> Games</span>"
msgstr "<span size=\"small\"> Játékok</span>"

#: usp.glade:1545
msgid "<span size=\"small\"> Graphics</span>"
msgstr "<span size=\"small\"> Grafika</span>"

#: usp.glade:1603
msgid "<span size=\"small\"> Internet</span>"
msgstr "<span size=\"small\"> Internet</span>"

#: usp.glade:1661
msgid "<span size=\"small\"> Office</span>"
msgstr "<span size=\"small\"> Iroda</span>"

#: usp.glade:1719
msgid "<span size=\"small\"> Programming</span>"
msgstr "<span size=\"small\"> Programozás</span>"

#: usp.glade:1777
msgid "<span size=\"small\"> Sound and Video</span>"
msgstr "<span size=\"small\"> Audio és Video</span>"

#: usp.glade:1835
msgid "<span size=\"small\"> System Tools</span>"
msgstr "<span size=\"small\"> Rendszereszközök</span>"

#: usp.glade:1893
msgid "<span size=\"small\"> Settings</span>"
msgstr "<span size=\"small\"> Beállítások</span>"

#: usp.glade:1951
msgid "<span size=\"small\"> All</span>"
msgstr "<span size=\"small\"> Minden</span>"

#: usp.glade:2115
msgid "<span weight=\"bold\">More Applications...</span>"
msgstr "<span weight=\"bold\">További alkalmazások...</span>"

#: usp.glade:2174
msgid "Enter item to search"
msgstr "Írd be, mit keressek"

#: usp.glade:2216
msgid "Search"
msgstr "Keresés"

#: usp.glade:2516
msgid "Network"
msgstr "Hálózat"

#: usp.glade:2640
msgid "Date and Time"
msgstr "Dátum és id&#337;"

#: usp.glade:2764
msgid "Theme"
msgstr "Téma"

#: usp.glade:2888
msgid "Screen Resolution"
msgstr "Képerny&#337; felbontás"

#: usp.glade:3037
msgid "Configure your system"
msgstr "Rendszerkonfigurálás"

#: usp.glade:3133
msgid "Move up"
msgstr "Mozgatás fel"

#: usp.glade:3142
msgid "Move down"
msgstr "Mozgatás le"

#: usp.glade:3151
msgid "Edit labels"
msgstr "Cimkék módosítása"

#: usp.glade:3160
msgid "Insert separator"
msgstr "Elválasztó csík beszúrása"

#: usp.glade:3169
msgid "Insert space"
msgstr "Üres hely beszúrása"

#: usp.glade:3178
msgid "Remove"
msgstr "Eltávolítás"

#: usp.glade:3187
msgid "Edit item"
msgstr "Tétel módosítása"

#: usp.glade:3256
msgid "Name"
msgstr "Név"

#: usp.glade:3300
msgid "Generic name"
msgstr "Általános név"

#: usp.glade:3343
msgid "Comment"
msgstr "Megjegyzés"

#: usp.glade:3386
msgid "Exec"
msgstr "Futtatás"

#: usp.glade:3429
msgid "Icon"
msgstr "Ikon"

#: usp.glade:3484
msgid "Add to favourites"
msgstr "Hozzáadás a kedvencekhez"


Thank you very much in advance.
This application becomes better and better! I like it very much!

fantan

---

### Post by Hells_Dark on 2006-08-07
Hi,
I did the french translation.
It works well ;)
Thanks.

However, there still having few text not translated.
Example : "Edit" when one does a "right click" on a element.

---

### Post by Fass on 2006-08-10
Here is a Swedish translation:

```
# SOME DESCRIPTIVE TITLE.
# Copyright (C) YEAR THE PACKAGE'S COPYRIGHT HOLDER
# This file is distributed under the same license as the PACKAGE package.
# Fass <ns.fass@gmail.com>, 2006.
#
#, fuzzy
msgid ""
msgstr ""
"Project-Id-Version: PACKAGE VERSION\n"
"Report-Msgid-Bugs-To: \n"
"POT-Creation-Date: 2006-08-02 11:24+0200\n"
"PO-Revision-Date: YEAR-MO-DA HO:MI+ZONE\n"
"Last-Translator: Fass <ns.fass@gmail.com>\n"
"Language-Team: Swedish <ns.fass@gmail.com>\n"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=sv_SE.UTF-8\n"
"Content-Transfer-Encoding: 8bit\n"

#: usp.glade:115 usp.glade:479
msgid "Places"
msgstr "Platser"

#: usp.glade:181 usp.glade:917 usp.glade:1091
msgid "Applications"
msgstr "Program"

#: usp.glade:247
msgid "Settings"
msgstr "Inställningar"

#: usp.glade:598
msgid "System Management"
msgstr "Systemhantering"

#: usp.glade:663
msgid "Install Software"
msgstr "Installera mjukvara"

#: usp.glade:725 usp.glade:3012
msgid "Control Center"
msgstr "Kontrollcenter"

#: usp.glade:788
msgid "Lock screen"
msgstr "Lås skärm"

#: usp.glade:852
msgid "Quit..."
msgstr "Avsluta..."

#: usp.glade:972 usp.glade:2308 usp.glade:2392
msgid "Computer"
msgstr "Dator"

#: usp.glade:1149
msgid "<span size=\"small\">All Applications</span>"
msgstr "<span size=\"small\">Alla program</span>"

#: usp.glade:1287
msgid "All Applications"
msgstr "Alla program"

#: usp.glade:1345
msgid "<span size=\"small\"> Applications</span>"
msgstr "<span size=\"small\"> Program</span>"

#: usp.glade:1429
msgid "<span size=\"small\"> Accessories</span>"
msgstr "<span size=\"small\"> Tillbehör</span>"

#: usp.glade:1487
msgid "<span size=\"small\"> Games</span>"
msgstr "<span size=\"small\"> Spel</span>"

#: usp.glade:1545
msgid "<span size=\"small\"> Graphics</span>"
msgstr "<span size=\"small\"> Grafik</span>"

#: usp.glade:1603
msgid "<span size=\"small\"> Internet</span>"
msgstr "<span size=\"small\"> Internet</span>"

#: usp.glade:1661
msgid "<span size=\"small\"> Office</span>"
msgstr "<span size=\"small\"> Kontor</span>"

#: usp.glade:1719
msgid "<span size=\"small\"> Programming</span>"
msgstr "<span size=\"small\"> Programmering</span>"

#: usp.glade:1777
msgid "<span size=\"small\"> Sound and Video</span>"
msgstr "<span size=\"small\"> Ljud och video</span>"

#: usp.glade:1835
msgid "<span size=\"small\"> System Tools</span>"
msgstr "<span size=\"small\"> Systemverktyg</span>"

#: usp.glade:1893
msgid "<span size=\"small\"> Settings</span>"
msgstr "<span size=\"small\"> Inställningar</span>"

#: usp.glade:1951
msgid "<span size=\"small\"> All</span>"
msgstr "<span size=\"small\"> Alla</span>"

#: usp.glade:2115
msgid "<span weight=\"bold\">More Applications...</span>"
msgstr "<span weight=\"bold\">Fler program...</span>"

#: usp.glade:2174
msgid "Enter item to search"
msgstr "Skriv sökterm"

#: usp.glade:2216
msgid "Search"
msgstr "Sök"

#: usp.glade:2516
msgid "Network"
msgstr "Nätverk"

#: usp.glade:2640
msgid "Date and Time"
msgstr "Tid och datum"

#: usp.glade:2764
msgid "Theme"
msgstr "Tema"

#: usp.glade:2888
msgid "Screen Resolution"
msgstr "Skärmupplösning"

#: usp.glade:3037
msgid "Configure your system"
msgstr "Konfigurera ditt system"

#: usp.glade:3133
msgid "Move up"
msgstr "Flytta upp"

#: usp.glade:3142
msgid "Move down"
msgstr "Flytta ned"

#: usp.glade:3151
msgid "Edit labels"
msgstr "Redigera etiketter"

#: usp.glade:3160
msgid "Insert separator"
msgstr "Infoga skiljelinje"

#: usp.glade:3169
msgid "Insert space"
msgstr "Infoga utrymme"

#: usp.glade:3178
msgid "Remove"
msgstr "Ta bort"

#: usp.glade:3187
msgid "Edit item"
msgstr "Redigera föremål"

#: usp.glade:3256
msgid "Name"
msgstr "Namn"

#: usp.glade:3300
msgid "Generic name"
msgstr "Generiskt namn"

#: usp.glade:3343
msgid "Comment"
msgstr "Kommentar"

#: usp.glade:3386
msgid "Exec"
msgstr "Kör"

#: usp.glade:3429
msgid "Icon"
msgstr "Ikon"

#: usp.glade:3484
msgid "Add to favourites"
msgstr "Lägg till i favoriter"
```

---

### Post by Oppi on 2006-08-12
Hi,

Here's a german translation. Not quite perfect, but I tried my best. If there are any suggestions for other words by the few german speaking users in this forum pls post. Did not change "Control Center" because it is the name of a application

[HTML]
# Ubuntu System Panel German-Translation
# Copyright (C) 2006
# This file is distributed under the same license as the USP package.
# Oppi <o.m@networld.at>, 2006.
#
#, fuzzy
msgid ""
msgstr ""
"Project-Id-Version: 0.33\n"
"Report-Msgid-Bugs-To: \n"
"POT-Creation-Date: 2006-08-02 11:24+0200\n"
"PO-Revision-Date: 2006-08-12 07.40+0100\n"
"Last-Translator: Oppi <o.m@networld.at>\n"
"Language-Team: Oppi <o.m@networld.at>\n"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=CHARSET\n"
"Content-Transfer-Encoding: 8bit\n"

#: usp.glade:115 usp.glade:479
msgid "Places"
msgstr "Orte"

#: usp.glade:181 usp.glade:917 usp.glade:1091
msgid "Applications"
msgstr "Programme"

#: usp.glade:247
msgid "Settings"
msgstr "Einstellungen"

#: usp.glade:598
msgid "System Management"
msgstr "Systemsteuerung"

#: usp.glade:663
msgid "Install Software"
msgstr "Software installieren"

#: usp.glade:725 usp.glade:3012
msgid "Control Center"
msgstr "Control Center"

#: usp.glade:788
msgid "Lock screen"
msgstr "Bildschirm sperren"

#: usp.glade:852
msgid "Quit..."
msgstr "Beenden"

#: usp.glade:972 usp.glade:2308 usp.glade:2392
msgid "Computer"
msgstr "Computer"

#: usp.glade:1149
msgid "<span size=\"small\">All Applications</span>"
msgstr "<span size=\"small\">Alle Programme</span>"

#: usp.glade:1287
msgid "All Applications"
msgstr "Alle Programme"

#: usp.glade:1345
msgid "<span size=\"small\"> Applications</span>"
msgstr "<span size=\"small\"> Programme</span>"

#: usp.glade:1429
msgid "<span size=\"small\"> Accessories</span>"
msgstr "<span size=\"small\"> Zubehör</span>"

#: usp.glade:1487
msgid "<span size=\"small\"> Games</span>"
msgstr "<span size=\"small\"> Spiele</span>"

#: usp.glade:1545
msgid "<span size=\"small\"> Graphics</span>"
msgstr "<span size=\"small\"> Grafik</span>"

#: usp.glade:1603
msgid "<span size=\"small\"> Internet</span>"
msgstr "<span size=\"small\"> Internet</span>"

#: usp.glade:1661
msgid "<span size=\"small\"> Office</span>"
msgstr "<span size=\"small\"> Office</span>"

#: usp.glade:1719
msgid "<span size=\"small\"> Programming</span>"
msgstr "<span size=\"small\"> Programmieren</span>"

#: usp.glade:1777
msgid "<span size=\"small\"> Sound and Video</span>"
msgstr "<span size=\"small\"> Audio und Video</span>"

#: usp.glade:1835
msgid "<span size=\"small\"> System Tools</span>"
msgstr "<span size=\"small\"> System Werkzeuge</span>"

#: usp.glade:1893
msgid "<span size=\"small\"> Settings</span>"
msgstr "<span size=\"small\"> Einstellungen</span>"

#: usp.glade:1951
msgid "<span size=\"small\"> All</span>"
msgstr "<span size=\"small\"> Alles</span>"

#: usp.glade:2115
msgid "<span weight=\"bold\">More Applications...</span>"
msgstr "<span weight=\"bold\">Mehr Programme...</span>"

#: usp.glade:2174
msgid "Enter item to search"
msgstr "Suchwort hier eingeben"

#: usp.glade:2216
msgid "Search"
msgstr "Suche"

#: usp.glade:2516
msgid "Network"
msgstr "Netzwerk"

#: usp.glade:2640
msgid "Date and Time"
msgstr "Datum und Uhrzeit"

#: usp.glade:2764
msgid "Theme"
msgstr "Thema"

#: usp.glade:2888
msgid "Screen Resolution"
msgstr "Bildschirmauflösung"

#: usp.glade:3037
msgid "Configure your system"
msgstr "Konfiguriere dein System"

#: usp.glade:3133
msgid "Move up"
msgstr "Nach oben"

#: usp.glade:3142
msgid "Move down"
msgstr "Nach unten"

#: usp.glade:3151
msgid "Edit labels"
msgstr "Labels anpassen"

#: usp.glade:3160
msgid "Insert separator"
msgstr "Trennzeichen einfügen"

#: usp.glade:3169
msgid "Insert space"
msgstr "Abstand einfügen"

#: usp.glade:3178
msgid "Remove"
msgstr "Entfernen"

#: usp.glade:3187
msgid "Edit item"
msgstr "Element bearbeiten"

#: usp.glade:3256
msgid "Name"
msgstr "Name"

#: usp.glade:3300
msgid "Generic name"
msgstr "Allgemeiner Name"

#: usp.glade:3343
msgid "Comment"
msgstr "Kommentar"

#: usp.glade:3386
msgid "Exec"
msgstr "Befehl"

#: usp.glade:3429
msgid "Icon"
msgstr "Symbol"

#: usp.glade:3484
msgid "Add to favourites"
msgstr "Zu Favoriten hinzufügen"
[/HTML]


greets, Oppi

---

### Post by comune on 2006-08-13
Hi! I made the Italian translation.

```


# SOME DESCRIPTIVE TITLE.
# Copyright (C) YEAR THE PACKAGE'S COPYRIGHT HOLDER
# This file is distributed under the same license as the PACKAGE package.
# FIRST AUTHOR <EMAIL@ADDRESS>, YEAR.
#
#, fuzzy
msgid ""
msgstr ""
"Project-Id-Version: usp 0.31\n"
"Report-Msgid-Bugs-To: \n"
"POT-Creation-Date: 2006-08-02 11:24+0200\n"
"PO-Revision-Date: 2006-08-02 11:24+02\n"
"Last-Translator: comune <EMAIL@ADDRESS>\n"
"Language-Team: it <it@li.org>\n"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=utf-8\n"
"Content-Transfer-Encoding: 8bit\n"

#: usp.glade:115 usp.glade:479
msgid "Places"
msgstr "Risorse"

#: usp.glade:181 usp.glade:917 usp.glade:1091
msgid "Applications"
msgstr "Applicazioni"

#: usp.glade:247
msgid "Settings"
msgstr "Preferenze"

#: usp.glade:568
msgid "label42"
msgstr "label42"

#: usp.glade:598
msgid "System Management"
msgstr "Amministrazione"

#: usp.glade:663
msgid "Install Software"
msgstr "Installa applicazioni"

#: usp.glade:725 usp.glade:3012
msgid "Control Center"
msgstr "Centro di controllo"

#: usp.glade:788
msgid "Lock screen"
msgstr "Blocca schermo"

#: usp.glade:852
msgid "Quit..."
msgstr "Esci..."

#: usp.glade:972 usp.glade:2308 usp.glade:2392
msgid "Computer"
msgstr "Computer"

#: usp.glade:1149
msgid "<span size=\"small\">All Applications</span>"
msgstr "<span size=\"small\">Tutte le applicazioni</span>"

#: usp.glade:1252
msgid "label78"
msgstr "label78"

#: usp.glade:1287
msgid "All Applications"
msgstr "Tutte le applicazioni"

#: usp.glade:1345
msgid "<span size=\"small\"> Applications</span>"
msgstr "<span size=\"small\"> Applicazioni</span>"

#: usp.glade:1429
msgid "<span size=\"small\"> Accessories</span>"
msgstr "<span size=\"small\"> Accessori</span>"

#: usp.glade:1487
msgid "<span size=\"small\"> Games</span>"
msgstr "<span size=\"small\"> Giochi</span>"

#: usp.glade:1545
msgid "<span size=\"small\"> Graphics</span>"
msgstr "<span size=\"small\"> Grafica</span>"

#: usp.glade:1603
msgid "<span size=\"small\"> Internet</span>"
msgstr "<span size=\"small\"> Internet</span>"

#: usp.glade:1661
msgid "<span size=\"small\"> Office</span>"
msgstr "<span size=\"small\"> Ufficio</span>"

#: usp.glade:1719
msgid "<span size=\"small\"> Programming</span>"
msgstr "<span size=\"small\"> Programmazione</span>"

#: usp.glade:1777
msgid "<span size=\"small\"> Sound and Video</span>"
msgstr "<span size=\"small\"> Suoni e video</span>"

#: usp.glade:1835
msgid "<span size=\"small\"> System Tools</span>"
msgstr "<span size=\"small\"> Risorse di sistema</span>"

#: usp.glade:1893
msgid "<span size=\"small\"> Settings</span>"
msgstr "<span size=\"small\"> Preferenze</span>"

#: usp.glade:1951
msgid "<span size=\"small\"> All</span>"
msgstr "<span size=\"small\"> Tutto</span>"

#: usp.glade:2046
msgid "label100"
msgstr "label100"

#: usp.glade:2115
msgid "<span weight=\"bold\">More Applications...</span>"
msgstr "<span weight=\"bold\">Più applicazioni...</span>"

#: usp.glade:2174
msgid "Enter item to search"
msgstr "Introduci l'elemento da cercare"

#: usp.glade:2216
msgid "Search"
msgstr "Cerca"

#: usp.glade:2516
msgid "Network"
msgstr "Rete"

#: usp.glade:2640
msgid "Date and Time"
msgstr "Data e ora"

#: usp.glade:2764
msgid "Theme"
msgstr "Tema"

#: usp.glade:2888
msgid "Screen Resolution"
msgstr "Risoluzione dello schermo"

#: usp.glade:3037
msgid "Configure your system"
msgstr "Configura il sistema"

#: usp.glade:3133
msgid "Move up"
msgstr "Sposta in alto"

#: usp.glade:3142
msgid "Move down"
msgstr "Sposta in basso"

#: usp.glade:3151
msgid "Edit labels"
msgstr "Modifica etichetta"

#: usp.glade:3160
msgid "Insert separator"
msgstr "Inserisci separatore"

#: usp.glade:3169
msgid "Insert space"
msgstr "Inserisci spazio"

#: usp.glade:3178
msgid "Remove"
msgstr "Elimina"

#: usp.glade:3187
msgid "Edit item"
msgstr "Modifica l'elemento"

#: usp.glade:3256
msgid "Name"
msgstr "Nome"

#: usp.glade:3300
msgid "Generic name"
msgstr "Nome generico"

#: usp.glade:3343
msgid "Comment"
msgstr "Commento"

#: usp.glade:3386
msgid "Exec"
msgstr "Comando"

#: usp.glade:3429
msgid "Icon"
msgstr "Icona"

#: usp.glade:3484
msgid "Add to favourites"
msgstr "Aggiungi ai favoriti"



```

Bye. :grin:

---

### Post by LordSavage on 2006-08-14
For the german translation you should use Büro instead of Office.

---

### Post by engla on 2006-08-16
> **Fass said:**
> Here is a Swedish translation:

Hey Fass, can we collaborate on this? Your translation is good for the most part, but in some places you have missed standard gnome & Ubuntu phrases, like programvara instead of mjukvara etc.

Perhaps we can put together a compromise. My suggestion is posted  at [http://paste.se.linux.org/?id=102](http://paste.se.linux.org/?id=102) (I didn't know that someone else already worked on this)

---

### Post by Fass on 2006-08-16
> **engla said:**
> Hey Fass, can we collaborate on this? Your translation is good for the most part, but in some places you have missed standard gnome & Ubuntu phrases, like programvara instead of mjukvara etc.

Sure. I chose "mjukvara" because I really think "programvara" is a stupid term, but if the rest of Gnome uses it (I've not seen that it does), I guess it would fit in better, silliness notwithstanding.

I went over your translation and there are a few things that are off: 

"Control Center" should not be "Kontrollpanel" as "Control Center" is called "Kontrollcenter" in the Swedish translation that already exists for it. We should use what it calls itself.

"Sätt in" as a translation for "Insert" is grammatically weak. "Infoga" is better. "Separator" as "avgränsare"... hmm... it works, even if I think "skiljelinje" is closer to describing what is being inserted. "Mellanrum," though, is better than my "utrymme" for space in the context.

"Fyll i sökterm" - what do you feel about "Ange sökterm"? "Fyll i" is so cross word puzzle...

Oh, and even if the original is "Date and time," "Tid och datum" is what is used by Gnome and "Datum och tid" disturbs Swedish prosody.

---

### Post by cime on 2007-02-09
```
# SOME DESCRIPTIVE TITLE.
# Copyright (C) YEAR THE PACKAGE'S COPYRIGHT HOLDER
# This file is distributed under the same license as the PACKAGE package.
# Cime <cime3d@gmail.com>, 2007.
#
#, fuzzy
msgid ""
msgstr ""
"Project-Id-Version: PACKAGE VERSION\n"
"Report-Msgid-Bugs-To: \n"
"POT-Creation-Date: 2006-08-02 11:24+0200\n"
"PO-Revision-Date: 2007-02-10 01:28+UTC+1\n"
"Last-Translator: Cime <cime3d@gmail.com>\n"
"Language-Team: Cime <cime3d@gmail.com>\n"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=CHARSET\n"
"Content-Transfer-Encoding: 8bit\n"

#: usp.glade:115 usp.glade:479
msgid "Places"
msgstr "Mesta"

#: usp.glade:181 usp.glade:917 usp.glade:1091
msgid "Applications"
msgstr "Programi"

#: usp.glade:247
msgid "Settings"
msgstr "Nastavitve"

#: usp.glade:568
msgid "label42"
msgstr "label42"

#: usp.glade:598
msgid "System Management"
msgstr "Upravljanje sistema"

#: usp.glade:663
msgid "Install Software"
msgstr "Namestitev programov"

#: usp.glade:725 usp.glade:3012
msgid "Control Center"
msgstr "Nadzorno središ&#269;e"

#: usp.glade:788
msgid "Lock screen"
msgstr "Zakleni ekran"

#: usp.glade:852
msgid "Quit..."
msgstr "Izhod..."

#: usp.glade:972 usp.glade:2308 usp.glade:2392
msgid "Computer"
msgstr "Ra&#269;unalnik"

#: usp.glade:1149
msgid "<span size=\"small\">All Applications</span>"
msgstr "<span size=\"small\">Vsi programi</span>"

#: usp.glade:1252
msgid "label78"
msgstr "label78"

#: usp.glade:1287
msgid "All Applications"
msgstr "Vsi programi"

#: usp.glade:1345
msgid "<span size=\"small\"> Applications</span>"
msgstr "<span size=\"small\"> Programi</span>"

#: usp.glade:1429
msgid "<span size=\"small\"> Accessories</span>"
msgstr "<span size=\"small\"> Pripomo&#269;ki</span>"

#: usp.glade:1487
msgid "<span size=\"small\"> Games</span>"
msgstr "<span size=\"small\"> Igre</span>"

#: usp.glade:1545
msgid "<span size=\"small\"> Graphics</span>"
msgstr "<span size=\"small\"> Grafika</span>"

#: usp.glade:1603
msgid "<span size=\"small\"> Internet</span>"
msgstr "<span size=\"small\"> Internet</span>"

#: usp.glade:1661
msgid "<span size=\"small\"> Office</span>"
msgstr "<span size=\"small\"> Pisarna</span>"

#: usp.glade:1719
msgid "<span size=\"small\"> Programming</span>"
msgstr "<span size=\"small\"> Programiranje</span>"

#: usp.glade:1777
msgid "<span size=\"small\"> Sound and Video</span>"
msgstr "<span size=\"small\"> Zvok in video</span>"

#: usp.glade:1835
msgid "<span size=\"small\"> System Tools</span>"
msgstr "<span size=\"small\"> Zvok in video</span>"

#: usp.glade:1893
msgid "<span size=\"small\"> Settings</span>"
msgstr "<span size=\"small\"> Nastavitve</span>"

#: usp.glade:1951
msgid "<span size=\"small\"> All</span>"
msgstr "<span size=\"small\"> Vse</span>"

#: usp.glade:2046
msgid "label100"
msgstr "label100"

#: usp.glade:2115
msgid "<span weight=\"bold\">More Applications...</span>"
msgstr "<span weight=\"bold\">Vsi programi...</span>"

#: usp.glade:2174
msgid "Enter item to search"
msgstr "Vnesite element ki ga iš&#269;ete"

#: usp.glade:2216
msgid "Search"
msgstr "Iskanje"

#: usp.glade:2516
msgid "Network"
msgstr "Omrežje"

#: usp.glade:2640
msgid "Date and Time"
msgstr "&#268;as in datum"

#: usp.glade:2764
msgid "Theme"
msgstr "Tema"

#: usp.glade:2888
msgid "Screen Resolution"
msgstr "Lo&#269;ljivost zaslona"

#: usp.glade:3037
msgid "Configure your system"
msgstr "Nastavite svoj sistem"

#: usp.glade:3133
msgid "Move up"
msgstr "Premakni gor"

#: usp.glade:3142
msgid "Move down"
msgstr "Premakni dol"

#: usp.glade:3151
msgid "Edit labels"
msgstr "Uredi naleke"

#: usp.glade:3160
msgid "Insert separator"
msgstr "Vstavit lo&#269;ilnico"

#: usp.glade:3169
msgid "Insert space"
msgstr "Vstavi presledek"

#: usp.glade:3178
msgid "Remove"
msgstr "Odstrani"

#: usp.glade:3187
msgid "Edit item"
msgstr "Uredi element"

#: usp.glade:3256
msgid "Name"
msgstr "Ime"

#: usp.glade:3300
msgid "Generic name"
msgstr "Generi&#269;no ime"

#: usp.glade:3343
msgid "Comment"
msgstr "Komentar"

#: usp.glade:3386
msgid "Exec"
msgstr "Izvedi"

#: usp.glade:3429
msgid "Icon"
msgstr "Ikona"

#: usp.glade:3484
msgid "Add to favourites"
msgstr "Dodaj med priljubljene"
```
Here is Slovenian translation. It's not perfect, but better than nothing.

---

### Post by M@teusz on 2007-03-24
Hi. Here is a polish translation. Bye.
```

# Ubuntu System Panel Polish-Translation
# Copyright (C) 2006
# This file is distributed under the same license as the USP package.
# mat02 aka M@teusz <mateuszknapik@gmail.com>, 2007.
#
#, fuzzy
msgid ""
msgstr ""
"Project-Id-Version: 0.33\n"
"Report-Msgid-Bugs-To: \n"
"POT-Creation-Date: 2006-08-02 11:24+0200\n"
"PO-Revision-Date: 2006-08-12 07.40+0100\n"
"Last-Translator: mat02 <mateuszknapik@gmail.com>\n"
"Language-Team: mat02 <mateuszknapik@gmail.com>\n"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=CHARSET\n"
"Content-Transfer-Encoding: 8bit\n"

#: usp.glade:115 usp.glade:479
msgid "Places"
msgstr "Miejsca"

#: usp.glade:181 usp.glade:917 usp.glade:1091
msgid "Applications"
msgstr "Aplikacje"

#: usp.glade:247
msgid "Settings"
msgstr "Ustawienia"

#: usp.glade:598
msgid "System Management"
msgstr "Administracja"

#: usp.glade:663
msgid "Install Software"
msgstr "Instalacja oprogramowania"

#: usp.glade:725 usp.glade:3012
msgid "Control Center"
msgstr "Centrum sterowania"

#: usp.glade:788
msgid "Lock screen"
msgstr "Zablokuj ekran"

#: usp.glade:852
msgid "Quit..."
msgstr "Zako&#324;cz..."

#: usp.glade:972 usp.glade:2308 usp.glade:2392
msgid "Computer"
msgstr "Komputer"

#: usp.glade:1149
msgid "<span size=\"small\">All Applications</span>"
msgstr "<span size=\"small\">Wszystkie aplikacje</span>"

#: usp.glade:1287
msgid "All Applications"
msgstr "Wszystkie programy"

#: usp.glade:1345
msgid "<span size=\"small\"> Applications</span>"
msgstr "<span size=\"small\"> programy</span>"

#: usp.glade:1429
msgid "<span size=\"small\"> Accessories</span>"
msgstr "<span size=\"small\"> Akcesoria</span>"

#: usp.glade:1487
msgid "<span size=\"small\"> Games</span>"
msgstr "<span size=\"small\"> Gry</span>"

#: usp.glade:1545
msgid "<span size=\"small\"> Graphics</span>"
msgstr "<span size=\"small\"> Grafika</span>"

#: usp.glade:1603
msgid "<span size=\"small\"> Internet</span>"
msgstr "<span size=\"small\"> Internet</span>"

#: usp.glade:1661
msgid "<span size=\"small\"> Office</span>"
msgstr "<span size=\"small\"> Biuro</span>"

#: usp.glade:1719
msgid "<span size=\"small\"> Programming</span>"
msgstr "<span size=\"small\"> Programowanie</span>"

#: usp.glade:1777
msgid "<span size=\"small\"> Sound and Video</span>"
msgstr "<span size=\"small\"> D&#378;wi&#281;k i obraz</span>"

#: usp.glade:1835
msgid "<span size=\"small\"> System Tools</span>"
msgstr "<span size=\"small\"> Narz&#281;dzia systemowe</span>"

#: usp.glade:1893
msgid "<span size=\"small\"> Settings</span>"
msgstr "<span size=\"small\"> Preferencje</span>"

#: usp.glade:1951
msgid "<span size=\"small\"> All</span>"
msgstr "<span size=\"small\"> Wszystko</span>"

#: usp.glade:2115
msgid "<span weight=\"bold\">More Applications...</span>"
msgstr "<span weight=\"bold\">Wi&#281;cej aplikacji...</span>"

#: usp.glade:2174
msgid "Enter item to search"
msgstr "Wpisz fraz&#281; do wyszukania"

#: usp.glade:2216
msgid "Search"
msgstr "Wyszukaj"

#: usp.glade:2516
msgid "Network"
msgstr "Sie&#263;"

#: usp.glade:2640
msgid "Date and Time"
msgstr "Data i czas"

#: usp.glade:2764
msgid "Theme"
msgstr "Motyw"

#: usp.glade:2888
msgid "Screen Resolution"
msgstr "Rozdzielczo&#347;&#263; ekranu"

#: usp.glade:3037
msgid "Configure your system"
msgstr "Skonfiguruj swój system"

#: usp.glade:3133
msgid "Move up"
msgstr "Przenie&#347; w gór&#281;"

#: usp.glade:3142
msgid "Move down"
msgstr "Przenie&#347; w dó&#322;"

#: usp.glade:3151
msgid "Edit labels"
msgstr "Zmie&#324; nazw&#281;"

#: usp.glade:3160
msgid "Insert separator"
msgstr "Dodaj separator"

#: usp.glade:3169
msgid "Insert space"
msgstr "Insert space"

#: usp.glade:3178
msgid "Remove"
msgstr "Usu&#324;"

#: usp.glade:3187
msgid "Edit item"
msgstr "Edytuj"

#: usp.glade:3256
msgid "Name"
msgstr "Nazwa"

#: usp.glade:3300
msgid "Generic name"
msgstr "Tytu&#322;"

#: usp.glade:3343
msgid "Comment"
msgstr "Komentarz"

#: usp.glade:3386
msgid "Exec"
msgstr "Polecenie"

#: usp.glade:3429
msgid "Icon"
msgstr "Ikona"

#: usp.glade:3484
msgid "Add to favourites"
msgstr "Dodaj do ulubionych"

```

---

### Post by Efigda on 2007-04-14
Here is a Dutch translation :) 
```

# Ubuntu System Panel Dutch translation
# Copyright (C) 2007
# This file is distributed under the same license as the USP package.
# Laurxp <laurxp@gmail.com>, 2007.
#
#, fuzzy
msgid ""
msgstr ""
"Project-Id-Version: 0.33\n"
"Report-Msgid-Bugs-To: \n"
"POT-Creation-Date: 2006-08-02 11:24+0200\n"
"PO-Revision-Date: 2006-08-12 07.40+0100\n"
"Last-Translator: Laurxp <laurxp@gmail.com>\n"
"Language-Team: Laurxp <laurxp@gmail.com>\n"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=CHARSET\n"
"Content-Transfer-Encoding: 8bit\n"

#: usp.glade:115 usp.glade:479
msgid "Places"
msgstr "Locaties"

#: usp.glade:181 usp.glade:917 usp.glade:1091
msgid "Applications"
msgstr "Toepassingen"

#: usp.glade:247
msgid "Settings"
msgstr "Voorkeuren"

#: usp.glade:598
msgid "System Management"
msgstr "Beheer"

#: usp.glade:663
msgid "Install Software"
msgstr "Installeren/Verwijderen"

#: usp.glade:725 usp.glade:3012
msgid "Control Center"
msgstr "Configuratiecentrum"

#: usp.glade:788
msgid "Lock screen"
msgstr "Scherm blokkeren"

#: usp.glade:852
msgid "Quit..."
msgstr "Afsluiten..."

#: usp.glade:972 usp.glade:2308 usp.glade:2392
msgid "Computer"
msgstr "Computer"

#: usp.glade:1149
msgid "<span size=\"small\">All Applications</span>"
msgstr "<span size=\"small\">Alle toepassingen</span>"

#: usp.glade:1287
msgid "All Applications"
msgstr "Alle toepassingen"

#: usp.glade:1345
msgid "<span size=\"small\"> Applications</span>"
msgstr "<span size=\"small\"> Toepassingen</span>"

#: usp.glade:1429
msgid "<span size=\"small\"> Accessories</span>"
msgstr "<span size=\"small\"> Hulpmiddelen</span>"

#: usp.glade:1487
msgid "<span size=\"small\"> Games</span>"
msgstr "<span size=\"small\"> Spelletjes</span>"

#: usp.glade:1545
msgid "<span size=\"small\"> Graphics</span>"
msgstr "<span size=\"small\"> Grafisch</span>"

#: usp.glade:1603
msgid "<span size=\"small\"> Internet</span>"
msgstr "<span size=\"small\"> Internet</span>"

#: usp.glade:1661
msgid "<span size=\"small\"> Office</span>"
msgstr "<span size=\"small\"> Kantoor</span>"

#: usp.glade:1719
msgid "<span size=\"small\"> Programming</span>"
msgstr "<span size=\"small\"> Ontwikkeling</span>"

#: usp.glade:1777
msgid "<span size=\"small\"> Sound and Video</span>"
msgstr "<span size=\"small\"> Audio en Video</span>"

#: usp.glade:1835
msgid "<span size=\"small\"> System Tools</span>"
msgstr "<span size=\"small\"> Systeemgereedschap</span>"

#: usp.glade:1893
msgid "<span size=\"small\"> Settings</span>"
msgstr "<span size=\"small\"> Voorkeuren</span>"

#: usp.glade:1951
msgid "<span size=\"small\"> All</span>"
msgstr "<span size=\"small\"> Alle</span>"

#: usp.glade:2115
msgid "<span weight=\"bold\">More Applications...</span>"
msgstr "<span weight=\"bold\">Meer toepassingen...</span>"

#: usp.glade:2174
msgid "Enter item to search"
msgstr "Typ zoekterm in"

#: usp.glade:2216
msgid "Search"
msgstr "Bestanden zoeken"

#: usp.glade:2516
msgid "Network"
msgstr "Netwerk"

#: usp.glade:2640
msgid "Date and Time"
msgstr "Datum en tijd"

#: usp.glade:2764
msgid "Theme"
msgstr "Thema"

#: usp.glade:2888
msgid "Screen Resolution"
msgstr "Schermresolutie"

#: usp.glade:3037
msgid "Configure your system"
msgstr "Configureer je systeem"

#: usp.glade:3133
msgid "Move up"
msgstr "Naar boven"

#: usp.glade:3142
msgid "Move down"
msgstr "Naar onder"

#: usp.glade:3151
msgid "Edit labels"
msgstr "Bewerk label"

#: usp.glade:3160
msgid "Insert separator"
msgstr "Voeg scheiding in"

#: usp.glade:3169
msgid "Insert space"
msgstr "Voeg lege ruimte in"

#: usp.glade:3178
msgid "Remove"
msgstr "Verwijder"

#: usp.glade:3187
msgid "Edit item"
msgstr "Bewerk item"

#: usp.glade:3256
msgid "Name"
msgstr "Naam"

#: usp.glade:3300
msgid "Generic name"
msgstr "Generieke naam"

#: usp.glade:3343
msgid "Comment"
msgstr "Commentaar"

#: usp.glade:3386
msgid "Exec"
msgstr "Uitvoeren"

#: usp.glade:3429
msgid "Icon"
msgstr "Ikoon"

#: usp.glade:3484
msgid "Add to favourites"
msgstr "Voeg toe aan favorieten"

```

---

### Post by LuisC-SM on 2007-08-21
I wonder what's the status of translations?

Regards

Luis

PS. Is there a way to apply one of this patches to the svn version? If yes.. How do I do it?

---

### Post by Malac on 2009-04-13
I know this is an old thread but thought it may tweak contributors interest.
Translation .pot files are now uploaded to the SVN.
They are under /usr/lib/python2.4/site-packages/usp/locale folder in the directory structure.
 
Hope this helps.

---

