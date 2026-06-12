---
title: "Different icons in each workspace?"
date: 2007-02-09
forum: Ubuntu Customization Guide
---

### Post by Balaam's Miracle on 2007-02-09
I know that in Gnome it is possible to have a different for each workspace using a certain script i've run across in [another forum](http://www.linux-noob.com/forums/index.php?showtopic=2706), but i was wondering if it's also possible to have different icons in each workspace.

The thing is, i love cramming my desktop/workspace with icons for fast access but i figured it would be real handy if i could configure workspace 1 for audio stuff, workspace 2 for games, workspace 3 for programming, etc.

Can this be done? A hack would be great too.

---

### Post by CheshireMac on 2007-02-14
> **Balaam's Miracle said:**
> I know that in Gnome it is possible to have a different for each workspace using a certain script i've run across in [another forum]("http://www.linux-noob.com/forums/index.php?showtopic=2706"), but i was wondering if it's also possible to have different icons in each workspace.
 
The thing is, i love cramming my desktop/workspace with icons for fast access but i figured it would be real handy if i could configure workspace 1 for audio stuff, workspace 2 for games, workspace 3 for programming, etc.
 
Can this be done? A hack would be great too.
To the best of my knowledge, this isn't possible (YET). I've asked the same question in the past, and gotten basically the same answer . . .the desktops are default upon startup and there's nothing to be done about it. Hopefully in the future, that will change.

---

### Post by motin on 2007-04-23
I'd like to the same thing. 

I won't accept accept that it isn't possible - not with Linux... I'll search on it some more.

EDIT: Seems to be a fact :(

[http://ubuntuforums.org/showthread.php?t=99985](http://ubuntuforums.org/showthread.php?t=99985)
[http://ubuntuforums.org/showthread.php?t=52969](http://ubuntuforums.org/showthread.php?t=52969)
[http://www.nabble.com/Different-icons-in-each-workspace-desktop-t3370770.html](http://www.nabble.com/Different-icons-in-each-workspace-desktop-t3370770.html)
[http://www.linuxquestions.org/questions/showthread.php?t=528616](http://www.linuxquestions.org/questions/showthread.php?t=528616)
[http://www.mail-archive.com/gnome-list@gnome.org/msg01775.html](http://www.mail-archive.com/gnome-list@gnome.org/msg01775.html)
[http://gnomesupport.org/forums/viewtopic.php?t=11835](http://gnomesupport.org/forums/viewtopic.php?t=11835)

.. everybody says it isn't possible - but a lot of people seem to request it - very strange!

---

### Post by QwUo173Hy on 2007-05-07
I would also really like this feature. I think that with Beryl/Compiz that this feature is a logical next step. Beryl/Compiz make your desktop interaction much more productive and I know I multitask a lot more now.

I made a feature request with the author of wallpapoz, which allows multiple desktop backgrounds. Maybe if more people request it...
[http://www.akbarhome.com/2007/03/12/it-is-working-with-beryl-now/#comment-974](http://www.akbarhome.com/2007/03/12/it-is-working-with-beryl-now/#comment-974)

---

### Post by pyros on 2007-05-09
seems like this would be more of a matter for nautilus, right?

---

### Post by adampyre on 2007-05-29
I would pay money for this feature. I think it is something that would be essential in an operating system, especially one that want's to be the leader of the pack! Who agrees! That's it, i'm going to start a poll....

---

### Post by Xbehave on 2007-05-30
no way would they add that to gnome, asking for it in kde might yield some luck but seams like a feature thats against the nature of gnome!

---

### Post by motin on 2007-11-07
> **Xbehave said:**
> no way would they add that to gnome, asking for it in kde might yield some luck but seams like a feature thats against the nature of gnome!

Why? Adding this and the possibility to have different backgrounds for each workspace would really help one to know where one is amongst the workspaces. It would also make it much simpler to have a clean icon set to start with, with gaming and utility / files icons on another workspace etc.

---

### Post by airtonix on 2007-12-16
Devils pie might do this for you.

You could also just run 'xNest ' on each of your workspaces... 
But if you just run four seperate copies of xnest on each workspace, then you need to log in.
So to get unique icons per xnest session, the easiest way is to make four psuedo users of yourself.....in the most crude fashion : 

user1 -> workspace 1, user2 -> workspace2, etc,etc

or more obviously : 

airtonix1 -> workspace 1, airtonix2 -> workspace2, etc,etc

---

### Post by motin on 2007-12-17
> **adampyre said:**
> I would pay money for this feature. I think it is something that would be essential in an operating system, especially one that want's to be the leader of the pack! Who agrees! That's it, i'm going to start a poll....

Great. Where's the poll?

---

### Post by motin on 2007-12-17
> **airtonix said:**
> You could also just run 'xNest ' on each of your workspaces... 
But if you just run four seperate copies of xnest on each workspace, then you need to log in.
So to get unique icons per xnest session, the easiest way is to make four psuedo users of yourself.....in the most crude fashion : 

user1 -> workspace 1, user2 -> workspace2, etc,etc

or more obviously : 

airtonix1 -> workspace 1, airtonix2 -> workspace2, etc,etc

An empty root X session, no gnome-panel and then 4 different X sessions, one on each workspace?

You'd loose the ability to move windows between workspaces, you'd have to have 4 different setting profiles in every app you start depending on in which workspace it was started. 

Sounds very counter-productive. 

> **airtonix said:**
> Devils pie might do this for you.

Now here is something that could be helpful. If there is a way to start Nautilus with different settings profiles, one could make a profile that shows a transparent background and no navbar, statusbar, sidebar etc, and then devilspie could move the window automatically to be under other windows without a taskbar-entry nor window-decorations. 

Something like (for the folder /home/$USER/DevilsDesktopFolder2/):
```
(if
        (matches (window_name) "DevilsDesktopFolder2")
        (begin
                (set_workspace 2)
                (below)
                (undecorate)
                (skip_pager)
                (skip_tasklist)
                (wintype "utility")
                (geometry "+50+50")
                (geometry "1280x752")
        )
)

```

Unfortunately, I see the following problems:

1. I do not know how to (or if it's possible) start nautilus with a certain settings profile.
2. I do not know how to (or if it's possible) to have a transparent Nautilus background.
3. I do not know how to (or if it's possible) to hide nautilus' menu bar (hmm but could maybe be solved by showing the undecorated window a bit under a gnome-panel lying in the top of the screen)
4. The ability to freely place icons is not available in these ordinary Nautilus windows.

---

### Post by seniorciz on 2008-01-09
> **airtonix said:**
> Devils pie might do this for you.

You could also just run 'xNest ' on each of your workspaces... 
But if you just run four seperate copies of xnest on each workspace, then you need to log in.
So to get unique icons per xnest session, the easiest way is to make four psuedo users of yourself.....in the most crude fashion : 

user1 -> workspace 1, user2 -> workspace2, etc,etc

or more obviously : 

airtonix1 -> workspace 1, airtonix2 -> workspace2, etc,etc


so that would acctually take away the time that is trying to be saved by having the customized desktops right? Logging out then back in to get something would be most inconveinen. Although i dont really have an idea of what xnest is so if you could outline that for me that woulds be awsome.

---

### Post by krivov on 2008-01-14
i was also looking for such option, but could not find it. so i wrote a small python script, which achieve this by simlinking the Desktop directory. It does almost all that i want, except that i have to manually refresh Nautilus by pressing Ctrl-R. If anyone knows how to do this from within python, please let me know.

---

### Post by bobby_d on 2008-01-30
Hi krivov, 

Thanks for your script.. As I saw on [http://ubuntuforums.org/archive/index.php/t-658040.html](http://ubuntuforums.org/archive/index.php/t-658040.html)

> You could try the program called xautomation (sudo apt-get install xautomation) . Then for sending F1 the call is
xte "key F1"

So I just added
```
    #mouse close to taskbar, but still on desktop
    os.popen("xte 'mousermove 0 -25' 'mousedown 1' 'mouseup 1' 'key F5'")
```
to your script and it seems to work.. Still, would be better if one could invoke Nautilus 'reload' directly from command line ... 

Cheers

PS: I use Ubuntu 6.06 persistent (from USB) so the corresponding home root location is in the script..

---

### Post by ewdij on 2008-01-31
[http://www.youtube.com/watch?v=oGXYLdZEf2c](http://www.youtube.com/watch?v=oGXYLdZEf2c)

Watch the above link ---- I am not sure how the guy did this but apparently there is an easier way to do this. Also from the webpage --- be briefly describes what he did.

"Maybe some Gnome uses got bored when wanting to have different files on desktop, in different workspaces - the solution may be using '~/Workspaces/.../' folder as option, instead of '~/Desktop/' folder. It's no hard work for the coders knows the source, for sure. - Will next version of Gnome and Ubuntu 8.04 have it?"

---

### Post by DouglasCaixeta on 2008-03-02
Let's vote on this in Ubuntu Brainstorming!!

[[IMG]http://brainstorm.ubuntu.com/idea/901/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/901/)

---

### Post by dallas7 on 2008-03-20
> **ewdij said:**
> [http://www.youtube.com/watch?v=oGXYLdZEf2c](http://www.youtube.com/watch?v=oGXYLdZEf2c)

Watch the above link ---- I am not sure how the guy did this but apparently there is an easier way to do this. Also from the webpage --- be briefly describes what he did.

"Maybe some Gnome uses got bored when wanting to have different files on desktop, in different workspaces - the solution may be using '~/Workspaces/.../' folder as option, instead of '~/Desktop/' folder. It's no hard work for the coders knows the source, for sure. - Will next version of Gnome and Ubuntu 8.04 have it?"

Obviously it can be done because this guy did it.  It seems, tho, it's going to be his secret.  Go fish.

---

### Post by DouglasCaixeta on 2008-03-21
This is just a video showing how this resource is gonna work. That doesn't mena the guy know how to do.
That's can't be do without modifying gnome code. I already do my search...

---

### Post by HDave on 2008-05-02
Based on the fact there is a bug in bugzilla for Nautilus from 2006, I am guessing it isn't going to be addressed by GNOME.  Check it out:

[http://bugzilla.gnome.org/show_bug.cgi?id=356922]("http://bugzilla.gnome.org/show_bug.cgi?id=356922")

On the other hand, there may soon be a Compiz-Fusion folder window Screenlet.  For those of you who don't know, you can have a different screenlet instance for each workspace.  Could be a viable approach.  Stay tuned.

---

### Post by k33bz on 2008-05-04
> **adampyre said:**
> I would pay money for this feature. I think it is something that would be essential in an operating system, especially one that want's to be the leader of the pack! Who agrees! That's it, i'm going to start a poll....


as would i:KS

---

### Post by motin on 2008-06-28
This issue has been frozen in Ubuntu Brainstorm due to erreniously reported dupes. Check the latest comments on [http://brainstorm.ubuntu.com/idea/901/:](http://brainstorm.ubuntu.com/idea/901/:)

> This is NOT a duplicate of idea #55: A wallpaper and icons by desktop ([http://brainstorm.ubuntu.com/idea/55/](http://brainstorm.ubuntu.com/idea/55/)) 

How can we unmark this duplicate? 

That one is about icons AND wallpapers, whereas this one only regards icons! 

This duplication report leads to a very weird situation: 
This one is about icons but is marked as a duplicate of icons+wallpapers. 
That one is in turn marked as a dupe of a wallpaper-only idea. 

Where did the icons go? This idea is about different icons...

> I suggest that this idea is re-opened as the official idea regarding different icons for each virtual desktop. 

Different wallpapers is a totally other issue and is being handled here: [http://brainstorm.ubuntu.com/idea/93/](http://brainstorm.ubuntu.com/idea/93/) (marked for inclusion in Intrepid btw)

Let's get this idea promoted once again!

[[IMG]http://brainstorm.ubuntu.com/idea/901/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/901/)

---

### Post by HDave on 2008-06-28
As the original author of the Brainstorm idea #901, I whole heartedly agree. 

Hate to report this, but I tracked down the guy who is implementing different wallpaper for each workspace as a Google summer of code project.  He told me that in his opinion, different icons per workspace violates the open desktop standard and won't be implemented in his work.  

See the conversation here:

[http://gsocblog.jsharpe.net/archives/12]("http://gsocblog.jsharpe.net/archives/12")

I have also found a bug with gnome here bating back to September, 2006:

[http://bugzilla.gnome.org/show_bug.cgi?id=356922]("http://bugzilla.gnome.org/show_bug.cgi?id=356922")

Based on the lack of reponse to the gnome bug, the low votes in Brainstorm, I think we will all die of old age before this get dealt with.

Perhaps the time has come to develop our own patch to nautilus/gnome or come up with a work-around....  I think we are on our own here.

Edit: I got $250 for anybody who develops a real working solution for this.

---

### Post by motin on 2008-06-28
Actually, after some chatting in #ubuntu-testing, nand helped me to unmark the duplicate status!

And, according to very many comments in idea #93 with duplicates, we still have a lot of support for this. 

I do not understand how the _option_ for this could violate the standard? The default should of course be having the same icons across all desktops...

Let's continue to promote this now re-opened idea and hope for the best!

Hey, great idea about the bounty - you should put that into the Ubuntu Brainstorm entry!

Cheers

---

### Post by krivov on 2008-07-15
Hi guys,

Try this little applet i wrote to manage multiple desktops. Not a perfect solution but works ok for me.

Instructions:

Download mdesktops.py to /usr/bin
make it executable: chmod 755 /usr/bin/mdesktops.py
run mdesktops.py install

then add applet mdesktops to the pannel, logout/login and have fun.
caveats: sometimes required to hit Cntrl-R to reload desktop; one nautilus window should always be opened. 

to uninstall run  mdesktops.py uninstall; logout/login

clicking with mouse to the applet area one may assign any directory as desktop directory to the current workspace. menu shows 5 recent directories, 6 default directories Desktop0-Desktop5 and .. to select any directory from the file system.

if applet could not be loaded most likely some of the python packager are not installed. run applet in window mode as mdesktops.py run-in-window to see what packages are missing.

Just found out it does not work with compiz; at least with wnck library i use.

---

### Post by motin on 2008-08-16
Thanks krivov!

I continued development somewhat and here is v0.2 of the applet:

See version history for changes. Mainly I added support for different backgrounds for each desktop. 

Source code:
```
#! /usr/bin/env python
# -*- coding: UTF-8 -*-
"""
*  Copyright (C) 2008  Sergei Krivov <krivov@yahoo.com>
*  Copyright (C) 2008  Fredrik Wollsén <fredrik.motin@gmail.com>
*
*  This program is free software; you can redistribute it and/or modify
*  it under the terms of the GNU General Public License as published by
*  the Free Software Foundation; either version 2 of the License, or
*  (at your option) any later version.
*
*  This program is distributed in the hope that it will be useful,
*  but WITHOUT ANY WARRANTY; without even the implied warranty of
*  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
*  GNU General Public License for more details.
*
*  You should have received a copy of the GNU General Public License
*  along with this program; if not, write to the Free Software
*  Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA.
"""
"""
Separate desktop for each workspace:
May need to Hit Ctrl-R to refresh desktop, when switched to new workspace.
One nautilus window should be running.
Desktop directories are created in ~/Desktops/ and are called 0, 1, 2 etc

To use different backgrounds for each desktop, put the background files 
in ~/Desktops/ with the name of the desktop directory with ".bg" added to 
the filename, for instance "~/Desktops/1.bg"
Note - do not use any ordinary file ending such as .jpg or .png - only .bg!

Installations instructions:
Rename and put a copy of this file in /usr/lib/mdesktops-applet/mdesktops-applet:
	sudo mkdir /usr/lib/mdesktops-applet/
	sudo cp mdesktops.py /usr/lib/mdesktops-applet/mdesktops-applet
Then run:
	sudo python /usr/lib/mdesktops-applet/mdesktops-applet install

Uninstallation instructions:
sudo python /usr/lib/mdesktops-applet/mdesktops-applet uninstall

A recommendation is to make the first virtual desktop point to your original desktop:
	rmdir ~/Desktops/0
	ln -s ~/Desktop ~/Desktops/0

Version history:
0.2 - Fredrik Wollsén
 * Different backgrounds for each desktop (~/Desktops/0.bg used for first desktop etc)
 * Changed structure:
	The desktop folders are now found in ~/Desktops instead of ~/.desktops - this way it's easier to find them for new users
	The symlink to the current desktop is named .current instead of current_desktop so that it isn't visible
	The desktop directories are named nothing but a number - makes the applet more discrete and avoids duplicate "Desktop" in path names (ie Desktops/Desktop1 etc)
	Desktop folders ranged 1-6 instead of 0-5 - for easier human interpretation of which folder belongs to which workspace
 * Commandline uninstallation feature
 * Misc changes:
	Added UTF-8 encoding declaration to file
	Friendlier installation and uninstallation messages
 * Renamed application file and bonobo server files to comply with debian and GNOME policies (next version will be packaged as a debian package)

0.1 - Sergei Krivov
 * Original Applet - Different Icons for each desktop

"""

import gtk,wnck,os,sys
import pygtk
pygtk.require('2.0')
import gnomeapplet
import gnome
import pickle
import commands

class Mdesktops_Applet(gnomeapplet.Applet):
    def __init__(self,applet,iid):
        self.__gobject_init__()
        gnome.init("mdesktops","1.0")
        self.applet=applet
        self.menu=gtk.Menu()
        self.litem=[]
        self.applet.connect("button-press-event",self.button_clicked,self.menu)
        self.screen=wnck.screen_get_default()
        self.screen.connect("active_workspace_changed",self.active_workspace_changed)
        self.home=os.path.expanduser('~')
        self.desktops=self.home+'/Desktops'
        self.check_desktops_dir()
        self.load_state()
        self.label=gtk.Label("0")
        self.applet.add(self.label)
        self.applet.connect("destroy",self.cleanup)
        self.applet.show_all()
	self.ordinary_background = commands.getoutput('gconftool -g /desktop/gnome/background/picture_filename')
    def button_clicked(self,widget,event,menu):
        if event.type == gtk.gdk.BUTTON_PRESS and event.button == 1:
            self.fill_menu(menu)
            menu.show_all()
            menu.popup(None,None,None,event.button,event.time)
            return True
    def response(self,widget,desktop):
        if desktop in self.history:self.history.remove(desktop)
        self.history.insert(0,desktop)
        if len(self.history)>5:self.history.pop()
        ws=self.screen.get_active_workspace().get_number()
        self.ws2dt[ws]=desktop
        self.set_desktop(ws)
    def response_new(self,widget,desktop):
        chooser = gtk.FileChooserDialog(title=None,action=gtk.FILE_CHOOSER_ACTION_SELECT_FOLDER,\
            buttons=(gtk.STOCK_CANCEL,gtk.RESPONSE_CANCEL,gtk.STOCK_OPEN,gtk.RESPONSE_OK))
        chooser.set_current_folder(self.desktops+'/..')
        response=chooser.run()
        if response == gtk.RESPONSE_OK:
            desktop=chooser.get_filename()
            chooser.destroy()
            self.response(None,desktop)
        chooser.destroy()
    def fill_menu(self,menu):
        for item in self.litem:self.menu.remove(item)
        self.litem=[]
        items=list(self.history)
        items.append(None)#separator
        ldir=os.listdir(self.desktops)
        ldir=[os.path.join(self.desktops,d) for d in ldir]
        ldir=[d for d in ldir if os.path.isdir(d) and not os.path.islink(d)]
        ldir.sort()
        items+=ldir
        items.append('..')
        for desktop in items:
            if desktop==None:item=gtk.SeparatorMenuItem()
            else:
                item=gtk.MenuItem(os.path.basename(desktop))
                if desktop=='..':item.connect("activate",self.response_new,desktop)
                else:item.connect("activate",self.response,desktop)
            menu.add(item)
            self.litem.append(item)
    def active_workspace_changed(self,screen,bla=None):
        ws=screen.get_active_workspace().get_number()
        self.set_desktop(ws)
    def set_desktop(self,ws):
        if self.ws2dt.has_key(ws):desktop=self.ws2dt[ws]
        else:        
            desktop='%s/%s' %(self.desktops,ws+1)
            if not os.access(desktop,os.F_OK):# desktop does not exist, take default
                desktop='%s/1' % self.desktops
        com='rm %s \n ln -s %s %s' %(self.current_desktop,desktop,self.current_desktop)
        os.popen(com)
        self.label.set_text(os.path.basename(desktop))
        os.popen('gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false')
        os.popen('gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop true')

	# load special desktop background (named the same as the desktop directory but with .bg added to the path) if available - otherwise restore the original background
	desktop_bg='%s.bg' %(desktop)
	if not os.access(desktop_bg,os.F_OK):
		desktop_bg=self.ordinary_background
	os.popen('gconftool -s -t string /desktop/gnome/background/picture_filename \"%s\"' %(desktop_bg))

    def load_state(self):
        name='%s/.mdesktops' % self.desktops
        self.ws2dt,self.history={},[]
        if os.access(name,os.F_OK):
            f=open(name)
            self.ws2dt,self.history=pickle.load(f)
    def save_state(self):
        name='%s/.mdesktops' % self.desktops
        f=open(name,'w')
        pickle.dump((self.ws2dt,self.history),f)
    def cleanup(self,event):
        self.save_state()
        os.popen('xdg-user-dirs-update --set DESKTOP %s/Desktop' %self.home)
        del self.applet
    def create_about_menu(self):
        self.applet.setup_menu(self.propxml,self.verbs,None)
    def about_info(self,event,data=None):
        about = gnome.ui.About("Desktop selection applet",0.2,"GPL",\
                               "GNOME Applet to manage multiple desktops (separate for each workspace). v0.2 by Fredrik Wollsén <fredrik.motin@gmail.com>",["Sergei Krivov <krivov@yahoo.com>"],\
                               ["Sergei Krivov <krivov@yahoo.com>"],"Sergei Krivov <krivov@yahoo.com>",None)
        about.show()
    def check_desktops_dir(self):
      if not os.access(self.desktops,os.F_OK):os.popen('mkdir '+self.desktops)
      for i in range(6):
        name=self.desktops+'/%i' %(i+1)
        if not os.access(name,os.F_OK):os.popen('mkdir '+name)
      name=self.desktops+'/.current'
      self.current_desktop=name
      os.popen('xdg-user-dirs-update --set DESKTOP %s' %self.current_desktop)


def sample_factory(applet,iid):
    Mdesktops_Applet(applet,iid)    
    return gtk.TRUE
 
def install(): #create bonobo server file
  com="""<oaf_info>

<oaf_server iid="OAFIID:mdesktops_Factory"
            type="exe" location="%s">

        <oaf_attribute name="repo_ids" type="stringv">
                <item value="IDL:Bonobo/GenericFactory:1.0"/>
                <item value="IDL:Bonobo/Unknown:1.0"/>
        </oaf_attribute>
        <oaf_attribute name="name" type="string" value="Multiple desktops"/>
        <oaf_attribute name="description" type="string" value="Multiple desktops"/>
</oaf_server>

<oaf_server iid="OAFIID:mdesktops"
            type="factory" location="OAFIID:mdesktops_Factory">

        <oaf_attribute name="repo_ids" type="stringv">
                <item value="IDL:GNOME/Vertigo/PanelAppletShell:1.0"/>
                <item value="IDL:Bonobo/Control:1.0"/>
                <item value="IDL:Bonobo/Unknown:1.0"/>
        </oaf_attribute>
        <oaf_attribute name="name" type="string" value="Multiple desktops"/>
        <oaf_attribute name="description" type="string" value="Multiple desktops"/>
        <oaf_attribute name="panel:category" type="string" value="Utility"/>
        <oaf_attribute name="panel:icon" type="string" value="bug-buddy.png"/>
</oaf_server>

</oaf_info>
"""
  try:
    f=open('/usr/lib64/bonobo/servers/GNOME_Mdesktops.server','w')
    f.write(com % '/usr/lib/mdesktops-applet/mdesktops-applet')
    f.close()
  except:
    try:
      f=open('/usr/lib/bonobo/servers/GNOME_Mdesktops.server','w')
      f.write(com % '/usr/lib/mdesktops-applet/mdesktops-applet')
      f.close()
    except:  
      print "Can not create bonobo server file; need root permisions"
      sys.exit(1)
  print "Multiple Desktops applet installed successfully. You may need to logout and log back before you can add it to the GNOME Panel."

def uninstall(): #remove bonobo server file
  server_64file='/usr/lib64/bonobo/servers/GNOME_Mdesktops.server'
  os.popen('rm -f %s' %(server_64file))
  server_file='/usr/lib/bonobo/servers/GNOME_Mdesktops.server'
  os.popen('rm -f %s' %(server_file))
  if not os.access(server_64file,os.F_OK) | os.access(server_file,os.F_OK):
    print "Multiple Desktops applet uninstalled successfully"
  else:
    print "Can not remove bonobo server file; need root permisions"
    sys.exit(1)

if len(sys.argv) == 2 and sys.argv[1] == "run-in-window":   
   main_window = gtk.Window(gtk.WINDOW_TOPLEVEL)
   main_window.set_title("Mdesktops Applet")
   main_window.connect("destroy", gtk.main_quit) 
   app = gnomeapplet.Applet()
   sample_factory(app, None)
   app.reparent(main_window)
   main_window.show_all()
   gtk.main()
   sys.exit()
if len(sys.argv) == 2 and sys.argv[1] == "install":
   install()   
   sys.exit()
if len(sys.argv) == 2 and sys.argv[1] == "uninstall":
   uninstall()
   os.popen('xdg-user-dirs-update --set DESKTOP %s/Desktop' % os.path.expanduser('~'))
   sys.exit()

if __name__ == '__main__':
    gnomeapplet.bonobo_factory("OAFIID:mdesktops_Factory",\
        gnomeapplet.Applet.__gtype__,"hello","0",sample_factory)
```

---

### Post by tarahmarie on 2008-09-10
I absolutely want to see this feature in KDE4!  Does anyone have any suggestions for a n00b with Kubuntu 8.04?  I REALLY want different workspace configurations (wallpaper, widget settings, icons, Firefox bookmarks, etc).

---

### Post by tarahmarie on 2008-09-10
Here is the KDE4 bug report:  [https://bugs.kde.org/show_bug.cgi?id=37067](https://bugs.kde.org/show_bug.cgi?id=37067)

It combines all our wishes: separate wallpaper/icons/widgets on each virtual desktop.

If you vote for that bug/desired feature, it's more likely to be implemented.  I've put all the votes into it that I can; let's publicize this desperately wanted feature and get it implemented ASAP !

---

### Post by HDave on 2008-09-11
> **tarahmarie said:**
> I REALLY want different workspace configurations (wallpaper, widget settings, icons, Firefox bookmarks, etc).

Unfortunately, each of these items requires a seperate approach.

Different wallpaper per workspace should be in 8.10.

Different icons per workspace should be done by Gnome, but they don't care.

Different Firefox boomarks would have to be done by Firefox, but I have simulated this very effectively by creating different firefox profiles.  This also gives you the added benefit (or hassle) of having different add-ons and themes per profile.  Thunderbird also supports profiles.

Different widget settings would have to be done by Gnome.  I have tried to simulate this using using Screenlets -- which CAN be individually assigned to a workspace.  It's very cool except there is an outstanding bug that randomly rearranges them across workspaces each time your reboot - thus rendering them useless to me until this issues is fixed.

I haven't tried this, but another approach would be to create separate X-sessions...or to login with 2 different ID's and use fast user switching.

---

### Post by tarahmarie on 2008-09-11
> **HDave said:**
> Unfortunately, each of these items requires a seperate approach.

Different wallpaper per workspace should be in 8.10.

Different icons per workspace should be done by Gnome, but they don't care.

Different Firefox boomarks would have to be done by Firefox, but I have simulated this very effectively by creating different firefox profiles.  This also gives you the added benefit (or hassle) of having different add-ons and themes per profile.  Thunderbird also supports profiles.

Different widget settings would have to be done by Gnome.  I have tried to simulate this using using Screenlets -- which CAN be individually assigned to a workspace.  It's very cool except there is an outstanding bug that randomly rearranges them across workspaces each time your reboot - thus rendering them useless to me until this issues is fixed.

I haven't tried this, but another approach would be to create separate X-sessions...or to login with 2 different ID's and use fast user switching.

I don't fully understand the issues involved, but the bug addresses the need for separate containers for each virtual desktop.  After reading the comments left by those requesting this feature, I think it's probably at least a good place to start.

---

