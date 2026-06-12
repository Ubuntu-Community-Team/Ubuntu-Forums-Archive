---
title: "Little glitch/bug showing all apps on start"
date: 2007-02-01
forum: Ubuntu System Panel
---

### Post by ADRez on 2007-02-01
I don't use favourites in the applications plugin and I noticed that in usp2 when I start it, it always shows favourites instead of all applications. I've looked at this code:

```
    #Add from applications file
    def do_applications_file( self ):
        TestForDir( ".usp/applications" )
        TestForFiles( ".usp/applications.list" )
        TestForFiles( ".usp/recentapps.list" )


        applicationsFile = open ( os.path.join( os.path.expanduser( "~" ), ".usp/applications.list" ), "r" )
        applicationsList = applicationsFile.readlines()

        for i in self.wTree.get_widget( "applications_button_holder" ).get_children():
            i.destroy()

        if len( applicationsList ) < 1:
            self.ChangeTab( "", "", 1 )
        else:
```

It changes the tab if there are no favourites, but if you don't have any, in .usp/applications.list (although it has nothing in it, 0Kb) it counts like if there was 1 line, so it thinks there is 1 favourite.

Another problem is that I have show all applications on start enabled, but it doesn't work (I haven't checked the code for this one)

---

### Post by chanders on 2007-02-01
Ok, I will look into this and add the option to show all apps (which is not implemented in USP2 yet)...

---

### Post by ADRez on 2007-02-02
```
if len( applicationsList ) < 2:
```

That's OK :cool: 

I've changed this for showing all apps on start (only last 2 lines, left blank spaces the same as for the "for i in range"):

```
    #Add from applications file
    def do_applications_file( self ):
        TestForDir( ".usp/applications" )
        TestForFiles( ".usp/applications.list" )
        TestForFiles( ".usp/recentapps.list" )


        applicationsFile = open ( os.path.join( os.path.expanduser( "~" ), ".usp/applications.list" ), "r" )
        applicationsList = applicationsFile.readlines()

        for i in self.wTree.get_widget( "applications_button_holder" ).get_children():
            i.destroy()

        if len( applicationsList ) < 2:
            self.ChangeTab( "", "", 1 )
        else:
            for i in range( len( applicationsList ) ):
                if ( applicationsList[i][-8:-1] == 'desktop' ):
                    ApplicationData = ParseDesktopFile( applicationsList[i] )
		    LabelOrder = [ApplicationData[4], ApplicationData[0]]
		    if self.swapgeneric == True:
			LabelOrder.reverse()
                    if len( ApplicationData ) > 1:
                        AppStyle = [pango.AttrSize(self.appnamesize*1000,0,-1),pango.AttrWeight(pango.WEIGHT_BOLD, 0, -1 )]
                        GenStyle = [pango.AttrSize(self.appgensize*1000,0,-1),pango.AttrWeight(pango.WEIGHT_NORMAL,0,-1 )]
                        Button1 = MakeAButton( 200, -1, gtk.RELIEF_NONE, ApplicationData[3], self.iconsize, 48, -1, LabelOrder, [AppStyle,GenStyle] )
                        Button1.connect( "button_press_event", self.ButtonClicked, ApplicationData[2].split() )
                        Button1.connect( "button_release_event", self.ButtonReleased, True )
			self.ApplicationTips.set_tip( Button1, ApplicationData[1], tip_private=None )
                        Button1.MyButtonName = applicationsList[i][:-1]
                        self.wTree.get_widget( "applications_button_holder" ).pack_start( Button1, False, True, 0 )
                if applicationsList[i][:-1] == "separator":
                    self.do_separator( "" )
                if applicationsList[i][:-1] == "space":
                    self.do_space( "" )

	    if self.showappsonstart == True:
                    self.ChangeTab( "", "", 1 )
```

And this (line starts with self.showappsonstart =):

```
        # Allow plugin to be minimized to the left plugin pane
        self.sticky = SetGconf( self.client, "bool", "/apps/usp/plugins/applications/sticky", False )
        self.minimized = SetGconf( self.client, "bool", "/apps/usp/plugins/applications/minimized", False )
        self.showappsonstart = SetGconf( self.client, "bool", "/apps/usp/plugins/applications/show_allapps_on_start", False )
        self.showmoreapps = SetGconf( self.client, "bool", "/apps/usp/plugins/applications/show_more_apps_button", False )
```

Maybe you could add it?

---

### Post by chanders on 2007-02-02
Patch added(slight modification) and SVN updated! Thanks ADRez

---

### Post by ADRez on 2007-02-02
Well, this is going well, I only see one bug that is on start; it's a little empty window with the title System Panel when it is created and then destroyed before usp shows on the panel. It takes three seconds to dissappear.
¿Maybe that's beryl's fault?

Thanks to you chanders, for making usp!! :D 

PD: I'm anxious for getting feisty fawn final with usp2 translated and with the ability to unmount drives from it :rolleyes:

---

### Post by chanders on 2007-02-02
^^ Good idea! I'll look into the unmount code :-D.


Not sure why you see that little window though.

Here is a little exercise if you want to track it down. Open all glade files (in the plugins folder)  in GLADE and check to see that the main window is set to "visible off".  Are you running any plugins that are not included with usp? Like Terminal/clock/etc? You should check them too ;-)

---

### Post by Malac on 2007-02-03
> **chanders said:**
> Not sure why you see that little window though.

Here is a little exercise if you want to track it down. Open all glade files (in the plugins folder)  in GLADE and check to see that the main window is set to "visible off".  Are you running any plugins that are not included with usp? Like Terminal/clock/etc? You should check them too ;-)
I hadn't realised but the uspcalendar, remind and calrem Glade files all have their window1 set to visible. This has been carried over from the original USPcalendar glade which I used as a template for the three new ones. I will change the tar file on post #2 of my alpha test files thread to incorporate the altered Glade files.
Thanks ADRez for pointing it out.

Also places.glade in the svn has it's window set to visible too.
(Let you change this one chanders.;-))

---

### Post by ADRez on 2007-02-03
It was the places one, changing its visible propety to false did it, great! \\:D/ 
Thanks to both of you!

PD: I thought that right click menu on drives was going to be feature for usp2, but if it wans't, thanks again for watching it, I think unmounting drives is essential :wink:

---

