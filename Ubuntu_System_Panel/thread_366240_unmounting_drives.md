---
title: "unmounting drives"
date: 2007-02-20
forum: Ubuntu System Panel
---

### Post by ADRez on 2007-02-20
I've added the ability to unmount drives from the places plugin clicking on the drive with the central button. I've only added this code after line 271 in places.py (latest svn), at the end of def ButtonReleased( self, w, ev ):

```
        elif ev.button == 2:
            for volume in gnomevfs.VolumeMonitor().get_mounted_volumes():
                if string.replace(string.join(volume.get_activation_uri().split( "//" )[1].split( "%20" ) ),"%23","#") == self.Exec[1]:
                        volume.unmount(self.do_mounted_volumes)
```

I've been searching a little for making a menu for unmounting and ejecting, but that was too much and I've only done this. I know it's not well done, but I don't know anything about python and it works :cool:

---

### Post by chanders on 2007-02-20
I will create a right click menu for this and send you the diff, that way you can see what I did to get the menu ;-)

---

### Post by Malac on 2007-02-21
Okay I've made some progress but I can't find any documentation as to what the DEVICE_TYPE numbers returned from gnomevfs.Volume.get_device_type() actually are. Can anyone help?

I've managed to workout CDROM is 4 and Hard Disk is 3.
I also keep getting ```
SystemError: NULL object passed to Py_BuildValue
``` everytime I unmount or eject something.

I've attached what I've got so far.

EDIT: new one at post #6

---

### Post by ADRez on 2007-02-21
Good work!

I've seen that cdroms are 4, and hard disks and usb pendrives are 3, but pendrives also have the eject option, so maybe instead of checking with volume.get_device_type() it has to be done with something else?

There is also a problem with volume.unmount(self.do_plugin) and volume.eject(self.do_plugin). I've been looking at [this page]("http://www.pygtk.org/pygnomevfs/class-gnomevfs-volume.html") and they are defined as this:
def eject(callback, user_data=None)
def unmount(callback, user_data=None)
I haven't seen how the callback procedure should be, and what params it should have, but if you do unmount the Filesystem / (shouln't allow this), usp crashes if you pass self.do_plugin procedure. If you pass self.do_mounted_volumes it gives errors but it doesn't crash, and you can see that the callback procedure takes 4 arguments, so there has to be a dedicated procedure for this.

---

### Post by Malac on 2007-02-21
> **ADRez said:**
> Good work!

I've seen that cdroms are 4, and hard disks and usb pendrives are 3, but pendrives also have the eject option, so maybe instead of checking with volume.get_device_type() it has to be done with something else?

There is also a problem with volume.unmount(self.do_plugin) and volume.eject(self.do_plugin). I've been looking at [this page]("http://www.pygtk.org/pygnomevfs/class-gnomevfs-volume.html") and they are defined as this:
def eject(callback, user_data=None)
def unmount(callback, user_data=None)
I haven't seen how the callback procedure should be, and what params it should have, but if you do unmount the Filesystem / (shouln't allow this), usp crashes if you pass self.do_plugin procedure. If you pass self.do_mounted_volumes it gives errors but it doesn't crash, and you can see that the callback procedure takes 4 arguments, so there has to be a dedicated procedure for this.
Surely pendrives are not actually ejected they are unmounted so this shouldn't be a problem.
To me ejecting is physically moving something whatever gnome says. :)
I'll take a look at the rest now.

---

### Post by Malac on 2007-02-21
Okay disallowed unmounting Filesystem ("/") and all working fine so far, except for the damn ```
SystemError: NULL object passed to Py_BuildValue
``` error keeps appearing.
Changed the callback to a combined unmount/eject function which just calls self.RegenPlugin. This seems to sort out the number of arguments issue.
New efforts attached.

EDIT: new attachment post #9

---

### Post by ADRez on 2007-02-21
I've been searching why it gives that error, but I haven't found anything.
When you check for the root filesystem, you use volume.get_display_name(), but it returns the name in your language (in my case Volumen raíz, I'm  spanish), so it doesn't work. Another way could be this:
self.Exec[1] != '/'
And in UnmountEjectCallback you execute self.RegenPlugin(), but this is not needed

---

### Post by Malac on 2007-02-21
> **ADRez said:**
> I've been searching why it gives that error, but I haven't found anything.
The documentation for gnomevfs is really awful the closest I found was for mono and that hadn't been finished yet.
> **ADRez said:**
>  When you check for the root filesystem, you use volume.get_display_name(), but it returns the name in your language (in my case Volumen raíz, I'm  spanish), so it doesn't work. Another way could be this:
self.Exec[1] != '/'
You are correct. I had tried that self.Exec[1] != "/" first but then changed it to volume.get_display_name() thinking it would be more reliable. I'll change it back.
> **ADRez said:**
>  And in UnmountEjectCallback you execute self.RegenPlugin(), but this is not needed
It was just in case the holders needed redrawing. As I was thinking of expanding the menu to cover deleting/renaming the gtk-bookmarks stuff too but they are covered by RegenPlugin calls anyway.
So it could just be changed to [COLOR=DarkRed]return[/COLOR].

---

### Post by Malac on 2007-02-22
Okay this is as far as I can get with the places for at least a week as I'm going to be really busy.
I've added rename and remove options to the right-click menu if you are on the bookmarks page.
And the only error that I get is still that Py_BuildValue thing when unmounting though I don't think it is doing any harm..
I've attached what I've done so far.

It could be committed to SVN, I think. :)

---

### Post by chanders on 2007-02-22
^^ I think so ;-)  I'll go ahead and update it...

---

### Post by ADRez on 2007-02-22
A little bit of optimization :p, doesn't fix the Py_BuildValue thing :( 

```
        #Check it's right-click and we are on Places Tab
        elif ev.button == 3:
            self.mTree = gtk.glade.XML( self.gladefile, "DriveMenu" )
            self.mTree.get_widget( "UnmountItem" ).connect( "activate", self.UnmountChosen, w, self.mTree)
            self.mTree.get_widget( "EjectItem" ).connect( "activate", self.EjectChosen, w, self.mTree )
            self.mTree.get_widget( "RemoveItem" ).connect( "activate", self.RemoveChosen, w, self.mTree, self.Exec )
            self.mTree.get_widget( "RenameItem" ).connect( "activate", self.RenameChosen, w, self.mTree, self.Exec )
            x = int( ev.x )
            y = int( ev.y )
            time = ev.time
            self.mTree.get_widget( "UnmountItem" ).hide()
            self.mTree.get_widget( "EjectItem" ).hide()
            showdrivemenu = False

            if self.wTree.get_widget('notebook1').get_current_page()==0:
                self.mTree.get_widget( "RemoveItem" ).hide()
                self.mTree.get_widget( "RenameItem" ).hide()
                for volume in gnomevfs.VolumeMonitor().get_mounted_volumes():
                    if string.replace(string.join(volume.get_activation_uri().split( "//" )[1].split( "%20" ) ),"%23","#") == self.Exec[1] and self.Exec[1] != "/":
                        self.mTree.get_widget( "UnmountItem" ).show()
                        # Shouldn't need to do this but you never know
                        if volume.is_mounted() == True:
                            self.mTree.get_widget( "UnmountItem" ).show()
                        if volume.get_device_type() != 3:
                            # print volume.get_device_type()
                            # Theses are the devices that we should be able to eject.
                            # [DEVICE_TYPE_AUDIO_CD,DEVICE_TYPE_VIDEO_DVD,DEVICE_TYPE_CDROM,DEVICE_TYPE_ZIP,DEVICE_TYPE_JAZ]
                            # Show the Eject MenuItem if it is not a Hard Disk
                            self.mTree.get_widget( "EjectItem" ).show()
                        showdrivemenu = True
            else:
                self.mTree.get_widget( "RemoveItem" ).show()
                self.mTree.get_widget( "RenameItem" ).show()
                showdrivemenu = True

            if showdrivemenu:
                self.mTree.get_widget( "DriveMenu" ).popup( None, None, None, ev.button, time )
```

---

### Post by Malac on 2007-02-22
Excellent, I'll commit this to the SVN now.

---

### Post by Quikee on 2007-02-22
Instead of manual URI -> PATH... 
```
string.replace(string.join(volume.get_activation_uri().split( "//" )[1].split( "%20" ) ),"%23","#")
```

You could use..
```

gnomevfs.get_local_path_from_uri(volume.get_activation_uri())
```

---

### Post by ADRez on 2007-02-23
```
gnomevfs.get_local_path_from_uri(volume.get_activation_uri())
```
That's very better to use this, it displays other caracters (á, é, í, ó, ú, ñ...) that with the other method are wrongly displayed.
It should be also included in bookmarks too (I think it's line 172 in svn 154):

```
                bookmarkInfo[0] = string.join( bookmarkInfo[0].split( "%20" ) )
                bookmarkInfo[0] = gnomevfs.get_local_path_from_uri( bookmarkInfo[0] )
```

With this it displays everything OK, except special places like computer, that aren't shown.

Another little thing, in my last post with the code optimized I made a mistake:
```
                for volume in gnomevfs.VolumeMonitor().get_mounted_volumes():
                    if string.replace(string.join(volume.get_activation_uri().split( "//" )[1].split( "%20" ) ),"%23","#") == self.Exec[1] and self.Exec[1] != "/":
                        **self.mTree.get_widget( "UnmountItem" ).show()**
                        # Shouldn't need to do this but you never know
                        if volume.is_mounted() == True:
```
Bold line doesn't have to be there, delete it please, it's in svn :(

---

### Post by chanders on 2007-02-23
Updated in SVN 154 ;-)

---

### Post by ADRez on 2007-02-23
It should be changed in line 249-250, 256, 313, 390 and 398 with gnomevfs.get_local_path_from_uri( ) too, because if you have something mounted in a directory with special characters it displays the path wrong ;)

---

### Post by Malac on 2007-02-23
> **ADRez said:**
> It should be also included in bookmarks too (I think it's line 172 in svn 154):```
                bookmarkInfo[0] = string.join( bookmarkInfo[0].split( "%20" ) )
                bookmarkInfo[0] = gnomevfs.get_local_path_from_uri( bookmarkInfo[0] )
```With this it displays everything OK, except special places like computer, that aren't shown.
This does not work on smb:/ and ssh:/ volumes (see below for fix from line 167):
```
                if bookmarkInfo[0][:4] == 'file':
                    ButtonIcon = "gnome-fs-directory"
                    bookmarkInfo[0] = gnomevfs.get_local_path_from_uri( bookmarkInfo[0] )
 
                if bookmarkInfo[0][:3] == 'smb' or bookmarkInfo[0][:3] == 'ssh':
                    ButtonIcon = "gnome-fs-network"
                bookmarkInfo[0] = string.join( bookmarkInfo[0].split( "%20" ) )
                # This next line doesn't work for 'smb:/' or 'ssh:/' addresses so I have moved it to the 'file' section
                #bookmarkInfo[0] = gnomevfs.get_local_path_from_uri( bookmarkInfo[0] )
                if len( bookmarkInfo ) > 2:

```> **ADRez said:**
> It should be changed in line 249-250, 256, 313, 390 and 398 with gnomevfs.get_local_path_from_uri( ) too, because if you have something mounted in a directory with special characters it displays the path wrong ;)
Done this too.

I have committed these changes to SVN Revision 156.

---

### Post by ADRez on 2007-02-24
> This does not work on smb:/ and ssh:/ volumes (see below for fix from line 167):
It's true! I search if there was something like get_smb_path_from_uri, but as there isn't I have written a workaround:

```
                if bookmarkInfo[0][:4] == 'file':
                    ButtonIcon = "gnome-fs-directory"
                    bookmarkInfo[0] = gnomevfs.get_local_path_from_uri( bookmarkInfo[0] )
                else:
                    ext = bookmarkInfo[0][:3]
                    if ext == 'smb' or ext == 'ssh':
                        ButtonIcon = "gnome-fs-network"
                        bookmarkInfo[0] = ext + ':/' + gnomevfs.get_local_path_from_uri( 'file:/' + bookmarkInfo[0][4:] )
```

---

### Post by ADRez on 2007-02-26
I've separated the code that returns the path from the uri into a function and changed everywhere it was been used. I've also solved the problem that renaming bookmarks, it was displayed the name with %20 instead of spaces and that

---

### Post by ADRez on 2007-03-08
^^ not good?  :( 

It seems there aren't many bugs in current svn (I only know that if there is a submenu inside applications it is not shown and the error when unmounting), maybe time to translate? :)

---

### Post by chanders on 2007-03-08
^^ Sorry, myself and Malac have been a bit busy lately.. As soon as possible I will package a beta and then we can start the translations ;-)

---

### Post by ADRez on 2007-03-09
Don't worry, take your time ;)

---

### Post by Malac on 2007-03-16
Adrez can you test this file for me to see if it works on ssh, smb stuff.
I found a new function "format_uri_for_display()" but I want to check if it will work or not on another system.

Thanks.

---

### Post by ADRez on 2007-03-16
^^ I've checked it now but, sorry, it doesn't work for samba stuff

---

### Post by Malac on 2007-03-16
> **ADRez said:**
> ^^ I've checked it now but, sorry, it doesn't work for samba stuff
Oh well, back to the drawing board. :)

---

