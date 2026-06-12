---
title: "USP SVN Repository"
date: 2006-08-07
forum: Ubuntu System Panel
---

### Post by chanders on 2006-08-07
I have setup an SVN repository. Use this command to checkout the current (pre-alpha ;))

svn checkout [http://ubuntu-system-panel.googlecode.com/svn/trunk/](http://ubuntu-system-panel.googlecode.com/svn/trunk/) ubuntu-system-panel

If you want to be added as a developer, pm me..

---

### Post by chanders on 2007-01-15
SVN now available for USP2Alpha! Get it while it's hot!!

Again,  If you want to be added as a developer, pm me, and I'll speak to Malac about it also..

---

### Post by delfick on 2007-01-15
cool :D

thnx :D

:D

i'm confused though, how do we install it.... ??

---

### Post by deadlydeathcone on 2007-01-15
> **delfick said:**
> cool :D

thnx :D

:D

i'm confused though, how do we install it.... ??

Download the file I attached, decompress it and replace the <edit> part in the third line with the path where the svn version was downloaded, then copy it to the correct location with the command:

```
sudo cp usp-dev.server /usr/lib/bonobo/servers/
```

You may have to log out or refresh the gnome panel, but for me gnome picked up the change after a minute or two. When it does just add it to the panel; all of your plugins will be detected and all that.

---

### Post by delfick on 2007-01-17
sry it took me so long to answer.....

thnx for your help :D


where can i find a list of changes that are made ?? 

thnx :D

---

### Post by Malac on 2007-01-18
> **delfick said:**
> 
where can i find a list of changes that are made ?? 
From a terminal in the ubuntu-system-panel folder on your system.```
 svn log
```Or install kdesvn. (Lots of stuff available in there.) :)

---

### Post by delfick on 2007-01-18
> **Malac said:**
> From a terminal in the ubuntu-system-panel folder on your system.```
 svn log
```Or install kdesvn. (Lots of stuff available in there.) :)

cool thnx :D

though i use gnome.....kde apps are ugly in gnome :P....i'll just stick with svn log :D

---

### Post by deadlydeathcone on 2007-01-18
> **delfick said:**
> cool thnx :D

though i use gnome.....kde apps are ugly in gnome :P....i'll just stick with svn log :D

You should check out the svn nautilus scripts; you can just right click on usp's folder and check the log, update it and all of that good stuff if you don't want to use the terminal.

---

### Post by delfick on 2007-01-19
> **deadlydeathcone said:**
> You should check out the svn nautilus scripts; you can just right click on usp's folder and check the log, update it and all of that good stuff if you don't want to use the terminal.

cool :D

please tell more :D

---

### Post by chanders on 2007-01-19
> **deadlydeathcone said:**
> You should check out the svn nautilus scripts; you can just right click on usp's folder and check the log, update it and all of that good stuff if you don't want to use the terminal.

Where do we get the goodies?? :)

---

### Post by Malac on 2007-01-19
> **chanders said:**
> Where do we get the goodies?? :)
sudo apt-get install nautilus-script-collection-svn
Puts the scripts in /usr/share/nautilus-scripts/Subversion

---

### Post by groggyboy on 2007-01-19
ok, just to make sure I'm doing things right:
**1.** I download the svn version by running this in the terminal: "svn checkout [http://ubuntu-system-panel.googlecode.com/svn/trunk/](http://ubuntu-system-panel.googlecode.com/svn/trunk/) ubuntu-system-panel"  It appears in a new folder in my home folder.
**2.** I download the attached script in deadlydeathcone's script.
**3.** I replace the third line (where it says "<edit>") with the location of the svn folder (in my case, that would be "~/ubuntu-system-panel/ubuntu-system-panel")
**4.** I copy the file to /usr/lib/bonobo/servers
**5.** I add the panel to gnome menu (which is now called "Ubuntu System Panel Development Version").
**6.** To update it to the latest revision, I run the command from the first step in the terminal.
**7.** To check what changes were made, I can run "svn-log" from the terminal in the USP svn folder ("~/ubuntu-system-panel") or I can download install the package "nautilus-script-collection-svn" which lets me check the log among other things by right-clicking the svn folder within nautilus.

Am I missing anything?  Do I need to uninstall the original (non-svn) 0.91?  I don't mind running beta (or alpha) software, but I'm not usually one to install things from cvs or svn (hence this post...).  It's just that i love USP sooooo much!  :biggrin:   I noticed malac had mentioned that the HideSidePane bug had been fixed in the latest svn ([here]("http://www.ubuntuforums.org/showpost.php?p=2032000&postcount=105")), but it still hasn't changed for me.  I thought I'd just double check to make sure I'm doing things correctly.

Over christmas, I showed my Ubuntu laptop to my sister (who has an older macbook running OS X).  She's not really big into computers, but she was quite impressed by how slick things looked with beryl and USP.  thanks for the applet!

---

### Post by chanders on 2007-01-20
Yup everything looks good. However as a precaution 

1. I would remove any older versions of USP
2. Un-set the old gconf settings (see first post in alpha thread)
3. Copy the svn files to their appropriate directories on your system (anyone with good scripting abilities to whip up a script to do this? ;-) DBO?)

4. When you update from svn again, you just need to do step 3

You are good to go!

---

### Post by Malac on 2007-01-20
> **groggyboy said:**
>    I noticed malac had mentioned that the HideSidePane bug had been fixed in the latest svn ([here]("http://www.ubuntuforums.org/showpost.php?p=2032000&postcount=105")), but it still hasn't changed for me.  I thought I'd just double check to make sure I'm doing things correctly.
Sorry groggyboy I had forgotten to update the svn repo. I have done it now.

---

### Post by delfick on 2007-01-20
> **chanders said:**
> Yup everything looks good. However as a precaution 

1. I would remove any older versions of USP
2. Un-set the old gconf settings (see first post in alpha thread)
3. Copy the svn files to their appropriate directories on your system (anyone with good scripting abilities to whip up a script to do this? ;-) DBO?)

4. When you update from svn again, you just need to do step 3

You are good to go!

cool....now i think the svn version actually works for me :D (before i don't think it was)

so now we just need an "update" script in the svn folder that updates svn and moves the files :D

---

### Post by PsyberOneZero on 2007-01-20
I've attached an update script.
It checks your local revision against the remote revision, if it needs to be updated the script will automatically update and install usp.

Just download the attached file and place it in the first ubuntu-system-panel directory
i.e. <your dir>/**ubuntu-system-panel**/ubuntu-system-panel/<usp stuff>
then rename **usp_update.txt** to **usp_update.sh** and run
```
chmod a+x usp_update.sh
```

---

### Post by chanders on 2007-01-20
Thank you [PsyberOneZero]("http://ubuntuforums.org/member.php?u=33096") ! SVN made easy ;-)

---

### Post by delfick on 2007-01-20
thankyou PsyberOneZero :D :D

you're a legend :D !

---

### Post by PsyberOneZero on 2007-01-20
So I take it the script works ok?

I just figured I'd give back a little to such an awesome project.

---

### Post by rai4shu2 on 2007-01-22
Will this work with Python 2.5?

---

### Post by chanders on 2007-01-22
It should. Give it a try and let us know how it goes ;-)

---

### Post by rai4shu2 on 2007-01-22
So far so good. Just a couple things:

/usr/bin/usp:
changed line 22 to: sys.path.append( '/usr/lib/python2.5/site-packages/usp/plugins' )

deselected uspuser plugin (I don't have a ~/.face folder)

---

### Post by Malac on 2007-01-22
> **rai4shu2 said:**
> So far so good. Just a couple things:

/usr/bin/usp:
changed line 22 to: sys.path.append( '/usr/lib/python2.5/site-packages/usp/plugins' )

deselected uspuser plugin (I don't have a ~/.face folder)
Right click and choose preferences to open uspconfig add uspuser back to your plugins list and then go to the User tab and put in the path to a picture you would like to use instead. Gif's work as an animated image if entered using uspconfig. Not sure about other formats.
I have updated SVN with a check whether the .face file exists.

---

### Post by rai4shu2 on 2007-01-22
Cool. This is coming along nicely.

---

### Post by Malac on 2007-01-24
updated svn with new uspconfig which now does backups and restores of usp settings to/from a file.

---

### Post by -fin on 2007-01-24
lookin' good!

what are the easy*-plugins doing, btw?

(checking the shortcut-stuff now ... can't promise anything tho)

---

### Post by chanders on 2007-01-24
> **-fin said:**
> lookin' good!

what are the easy*-plugins doing, btw?

(checking the shortcut-stuff now ... can't promise anything tho)

Thanks!
The easy* aren't plugins per se, they are actually helper files for the real plugins ;-)

---

### Post by delfick on 2007-01-24
> **Malac said:**
> updated svn with new uspconfig which now does backups and restores of usp settings to/from a file.

awsome :D

---

### Post by unabatedshagie on 2007-01-24
My brain cells must be taking a holiday but I can't seem to get this to work.

I have downloaded the svn.

Now do I still have to edit and copy the file from the fourth post?

Also what about the file that PsyberOneZero made? It looks to me like it's included now? Am I correct?

If so how do I run it? **./usp_update.sh** ?

The script is supposed to copy the files to the system so I can delete the folder in the home directory?

---

### Post by chanders on 2007-01-24
> **unabatedshagie said:**
> My brain cells must be taking a holiday but I can't seem to get this to work.

I have downloaded the svn.

Now do I still have to edit and copy the file from the fourth post?

Also what about the file that PsyberOneZero made? It looks to me like it's included now? Am I correct?

If so how do I run it? **./usp_update.sh** ?

The script is supposed to copy the files to the system so I can delete the folder in the home directory?

OK here are the easy steps..

1. Download the SVN 
2. In a terminal, cd into the directory with usp_update.sh
3. run the command like so 
```

./usp_update.sh
```4. This should install usp svn on your system
5. For safety logout of gnome
6. Log back in, right click on a panel and add USP..
7. Thats it!

You can safely ignore the fourth post. That was before we had PsyberOneZero's script.
Yup. PsyberOneZero's script is now included in the SVN repository.
You shouldnt delete the folder in your home directory because you will need it everytime you want to update usp svn via step 3..

---

### Post by unabatedshagie on 2007-01-25
Strange, thats what I was doing yesterday and in the terminal it said that USP is up-to-date, although even after numerus logouts USP wouldn't show up in the add panel window.

Now I started the computer this morning and ran through the commands you have posted (which were exactly the same as I was doing yesterday) and it updated, I'm guessing that the SVN was updated?

Now after a logout USP shows up in the add panel window but doesn't get added to the bar.

I used to have the older non-svn version which I uninstalled and ran the command **gconftool-2 --recursive-unset /apps/usp** and emptied the plugins folder but I just can't get it to add to the panel.

Any ideas?

---

### Post by Malac on 2007-01-25
> **unabatedshagie said:**
> Strange, thats what I was doing yesterday and in the terminal it said that USP is up-to-date, although even after numerus logouts USP wouldn't show up in the add panel window.

Now I started the computer this morning and ran through the commands you have posted (which were exactly the same as I was doing yesterday) and it updated, I'm guessing that the SVN was updated?

Now after a logout USP shows up in the add panel window but doesn't get added to the bar.

I used to have the older non-svn version which I uninstalled and ran the command **gconftool-2 --recursive-unset /apps/usp** and emptied the plugins folder but I just can't get it to add to the panel.

Any ideas?
There has been a problem with the uspuser plugin causing USP to "hang", thanks to a Python code update breaking popen().
To check if this is what you are suffering from open gconf-editor and navigate to /apps/usp and remove uspuser from the plugins_list value and try restarting usp. If usp works then you are suffering from this bug, leave out uspuser until you have updated to todays revision.
I have uploaded a fixed copy of uspuser to the svn today at about 11-00am GMT. Revision 93.

---

### Post by unabatedshagie on 2007-01-25
I must have royally screwed something up :)  because I don't have an entry in gconf-editor for usp.

[IMG]http://img262.imageshack.us/img262/3840/screenshot69bq.png[/IMG]

I have also updated to the newest build.

Any ideas on what I could have done to mess this up?

Strange thing is if I add it to the panel and move the panel from the bottom to any other side I can see the button just not click on it.

---

### Post by Malac on 2007-01-25
> **unabatedshagie said:**
> I must have royally screwed something up :)  because I don't have an entry in gconf-editor for usp.

[IMG]http://img262.imageshack.us/img262/3840/screenshot69bq.png[/IMG]

I have also updated to the newest build.

Any ideas on what I could have done to mess this up?

Strange thing is if I add it to the panel and move the panel from the bottom to any other side I can see the button just not click on it.
That's a new one on me :)

Try running ```
usp run-in-window
``` and paste the output here.
Also have you done a reboot since you updated the files. I know the instructions say just logout but I always feel happier doing a reboot if logout doesn't work.

---

### Post by unabatedshagie on 2007-01-25
I have done a full reboot a couple of time.

Here's the output for the command```
(usp:5843): libglade-WARNING **: could not find glade file '/usr/share/usp/usp2.glade'
Traceback (most recent call last):
  File "/usr/bin/usp", line 677, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 667, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 456, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 39, in __init__
    self.wTree = gtk.glade.XML( self.gladefile, "window1" )
RuntimeError: could not create GladeXML object

```

---

### Post by Malac on 2007-01-25
> **unabatedshagie said:**
> I have done a full reboot a couple of time.

Here's the output for the command```
(usp:5843): libglade-WARNING **: could not find glade file '/usr/share/usp/usp2.glade'
Traceback (most recent call last):
  File "/usr/bin/usp", line 677, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 667, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 456, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 39, in __init__
    self.wTree = gtk.glade.XML( self.gladefile, "window1" )
RuntimeError: could not create GladeXML object

```
If you are running this from the svn update script then something has gone wrong and it hasn't copied the usp2.glade file to that folder.
Try going to *[COLOR=DimGray]<where you put the svn>[/COLOR]*/ubuntu-system-panel/ubuntu-system-panel/usr/share/usp and manually copy the usp2.glade file to  /usr/share/usp.
then run ```
usp run-in-window
``` again.

---

### Post by PsyberOneZero on 2007-01-25
I've attached an updated script, that fixes the /usr/share/usp bug.  I should have another version out tonight that will do the same as this version just a smaller file.

---

### Post by Malac on 2007-01-25
Excellent :)

---

### Post by groggyboy on 2007-01-25
PsyberOneZero: thanks for the script! it makes life sooo much easier!  :D 
However, I'm having a problem with your updated script.  after updating from svn, i downloaded your new script to the proper folder, removed the ".txt" and made it executable, and this is what it returned:```
groggyboy@ono-sendai:~/ubuntu-system-panel$ ./usp_update
**bash: ./usp_update: /bin/bash^M: bad interpreter: No such file or directory**
groggyboy@ono-sendai:~/ubuntu-system-panel$
```
I'm not very good with scripts, so I can't help you any further, sorry!

Keep up the good work, folks!

---

### Post by PsyberOneZero on 2007-01-25
> **groggyboy said:**
> PsyberOneZero: thanks for the script! it makes life sooo much easier!  :D 
However, I'm having a problem with your updated script.  after updating from svn, i downloaded your new script to the proper folder, removed the ".txt" and made it executable, and this is what it returned:```
groggyboy@ono-sendai:~/ubuntu-system-panel$ ./usp_update
**bash: ./usp_update: /bin/bash^M: bad interpreter: No such file or directory**
groggyboy@ono-sendai:~/ubuntu-system-panel$
```
I'm not very good with scripts, so I can't help you any further, sorry!

Keep up the good work, folks!

It's wierd I downloaded the one I just uploaded and it doesn't want to work, so I'll upload it again from a script that I know works.

---

### Post by groggyboy on 2007-01-25
Thanks PsyberOneZero, that's fixed it

---

### Post by unabatedshagie on 2007-01-26
Thanks for updating the script PsyberOneZero, I have finally got usp working now :)

Thanks for the help everyone.

---

### Post by ~LoKe on 2007-01-31
For starters, I'm running Feisty, perhaps this is the reason.

Anyways, running USP shows completely empty menus (no places, applications, etc).

Tried unsetting the gconf keys.

usp run-in-window gives:
> Loading plugin 'uspuser' : sucessful
Loading plugin 'system_management' : sucessful
Loading plugin 'applications' : sucessful
No recent applications
Loading plugin 'recent' : sucessful
No recent applications
/usr/bin/usp:618: GtkWarning: Invalid icon size 0

  main_window.show_all()
/usr/bin/usp:619: GtkWarning: Invalid icon size 0

  gtk.main()
Static User Image Used

---

### Post by Malac on 2007-01-31
> **~LoKe said:**
> For starters, I'm running Feisty, perhaps this is the reason.

Anyways, running USP shows completely empty menus (no places, applications, etc).

Tried unsetting the gconf keys.

usp run-in-window gives:
open gconf-editor and set icon_size to something other than 0
And you may have to set width and height keys for each plugin this is a known bug which is fixed in the svn version.
From the mis-spelled "sucessful" it looks like you are not using the latest svn. :)

---

### Post by zekopeko on 2007-01-31
how to add a custom applet icon without deleting distributor-logo? i want to add apple logo next to the text.

thnx in advance

---

### Post by Malac on 2007-02-15
I've added the ability to have icons on the tabs as well as or instead of the text.
This is done by putting the icon name in square brackets '[]' either before or after the text.
e.g.
newtab=Standard Plugins[gnome-settings.png]
[SIZE=1]*[COLOR=DimGray]<some plugins and newpanes here>[/COLOR]*[/SIZE]
newtab=[add.png]Extra/Add-On Plugins
[SIZE=1]*[COLOR=DimGray]<some plugins and newpanes here>[/COLOR]*[/SIZE]
newtab=Internet
[SIZE=1]*[COLOR=DimGray]<some plugins and newpanes here>[/COLOR]*[/SIZE]
newtab=[tux]
[SIZE=1][I][COLOR=DimGray]<some plugins and newpanes here>

[/COLOR][/I][/SIZE] Would give this :
[ATTACH]25333[/ATTACH]
As you can see from the example you can mix and match icons and text.
As before if you just use 'newtab' it will be given a number.
Also full paths to icons can be used too.
e.g.
newtab=Extra/Add-On Plugins[/home/dave/add.png]

---

### Post by delfick on 2007-02-15
> **Malac said:**
> I've added the ability to have icons on the tabs as well as or instead of the text.
This is done by putting the icon name in square brackets '[]' either before or after the text.
e.g.
newtab=Standard Plugins[gnome-settings.png]
newtab=[add.png]Extra/Add-On Plugins
newtab=Internet
newtab=[tux]

Would give this :
[ATTACH]25333[/ATTACH]
As you can see from the example you can mix and match icons and text.
As before if you just use 'newtab' it will be given a number.

awsome !! :D

thnx :D

---

### Post by Malac on 2007-02-15
You're Welcome.
Forgot to mention absolute paths can be used if you want an icon that's not in your current theme.
e.g.:
newtab=Internet[/home/dave/.icons/glass-icons/scalable/apps/firefox-icon.svg]

gives me:
[ATTACH]25336[/ATTACH]

---

### Post by chanders on 2007-02-15
Sweet! (can we get the icon bigger ;-))

---

### Post by Malac on 2007-02-15
> **chanders said:**
> Sweet! (can we get the icon bigger ;-))
Just committed the change (now rev 123)
As per requests added icon size adjustment and as a pre-emptive strike added font size adjustment . :)
[ATTACH]25343[/ATTACH]

EDIT: oh yeah, I can't remember whether I mentioned that the tabs can now be placed at the top, left, right or bottom of the menu.
[ATTACH]25344[/ATTACH]

---

### Post by delfick on 2007-02-15
> **Malac said:**
> Just committed the change (now rev 123)
As per requests added icon size adjustment and as a pre-emptive strike added font size adjustment . :)

EDIT: oh yeah, I can't remember whether I mentioned that the tabs can now be placed at the top, left, right or bottom of the menu.


cool thnx :D

though it doesn't appear right for me ..... (see screenshot)

o ye, and thnx for making items in the pluginlist and compactlist editable via double click :D

---

### Post by Malac on 2007-02-15
> **delfick said:**
> cool thnx :D

though it doesn't appear right for me ..... (see screenshot)

o ye, and thnx for making items in the pluginlist and compactlist editable via double click :D
You have your Tab Font Size set to 2: so the text is tiny. :)

EDIT: oops my bad I had set the default at 2. :)
Okay rev 124.

---

### Post by delfick on 2007-02-15
> **Malac said:**
> You have your Tab Font Size set to 2: so the text is tiny. :)

EDIT: oops my bad I had set the default at 2. :)
Okay rev 124.

hehehe...thnx :D

much better :D

---

### Post by sweetthdevil on 2007-02-15
ok, i getting frustrated now!

I can't seem to install USP_svn

i run into the terminal:
svn checkout [http://ubuntu-system-panel.googlecode.com/svn/trunk/](http://ubuntu-system-panel.googlecode.com/svn/trunk/) ubuntu-system-panel

which download the svn version into /home/sweetth/ubuntu-system-panel

i download the usp_update, which i renome on .sh and also did the chmod

then i run into the terminal cd to go to the folder which contain the usp_update.sh, the ./up_date.sh 

and then i've got a error:

sweetth@sweetth-desktop:~/ubuntu-system-panel$ ./usp_update.sh 
./usp_update.sh: line 15: ((: > : erreur de syntaxe : opérande attendu (error token is "> ")
USP is up-to-date


First it's telling me usp is up to date! i used synaptic to un-install it, i did 
gconftool-2 --recursive-unset /apps/usp
and empty your ~/.usp/plugins folder before installing

so where am i doing wrong?

thanks so much for your help.:roll:

---

### Post by delfick on 2007-02-15
i thought usp_update was already in svn ??

just checkout the svn again, cd into the newly created folder and do "./usp_update".....

 :D

---

### Post by sweetthdevil on 2007-02-15
same as before! 

i don't get it!

and if i run usp run-in-window
bash: usp : commande introuvable

---

### Post by sweetthdevil on 2007-02-15
i erase the folder, and did it again!

```
sweetth@sweetth-desktop:~$ svn checkout http://ubuntu-system-panel.googlecode.com/svn/trunk/ ubuntu-system-panel
A    ubuntu-system-panel/ubuntu-system-panel
A    ubuntu-system-panel/ubuntu-system-panel/usr
A    ubuntu-system-panel/ubuntu-system-panel/usr/share
A    ubuntu-system-panel/ubuntu-system-panel/usr/share/usp
A    ubuntu-system-panel/ubuntu-system-panel/usr/share/usp/usp2.glade
A    ubuntu-system-panel/ubuntu-system-panel/usr/share/usp/dotted.png
A    ubuntu-system-panel/ubuntu-system-panel/usr/share/usp/uspconfig.glade
A    ubuntu-system-panel/ubuntu-system-panel/usr/lib
A    ubuntu-system-panel/ubuntu-system-panel/usr/lib/python2.4
A    ubuntu-system-panel/ubuntu-system-panel/usr/lib/python2.4/site-packages
A    ubuntu-system-panel/ubuntu-system-panel/usr/lib/python2.4/site-packages/usp
A    ubuntu-system-panel/ubuntu-system-panel/usr/lib/python2.4/site-packages/usp/plugins
A    ubuntu-system-panel/ubuntu-system-panel/usr/lib/python2.4/site-packages/usp/plugins/uspuser.glade
A    ubuntu-system-panel/ubuntu-system-panel/usr/lib/python2.4/site-packages/usp/plugins/places.glade
A    ubuntu-system-panel/ubuntu-system-panel/usr/lib/python2.4/site-packages/usp/plugins/shortcuts.py
A    ubuntu-system-panel/ubuntu-system-panel/usr/lib/python2.4/site-packages/usp/plugins/computer.py
A    ubuntu-system-panel/ubuntu-system-panel/usr/lib/python2.4/site-packages/usp/plugins/__init__.py
A    ubuntu-system-panel/ubuntu-system-panel/usr/lib/python2.4/site-packages/usp/plugins/execute.py
A    ubuntu-system-panel/ubuntu-system-panel/usr/lib/python2.4/site-packages/usp/plugins/system_management.glade
A    ubuntu-system-panel/ubuntu-system-panel/usr/lib/python2.4/site-packages/usp/plugins/recent.glade
A    ubuntu-system-panel/ubuntu-system-panel/usr/lib/python2.4/site-packages/usp/plugins/usp_util.py
A    ubuntu-system-panel/ubuntu-system-panel/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py
A    ubuntu-system-panel/ubuntu-system-panel/usr/lib/python2.4/site-packages/usp/plugins/places.py
A    ubuntu-system-panel/ubuntu-system-panel/usr/lib/python2.4/site-packages/usp/plugins/applications.glade
A    ubuntu-system-panel/ubuntu-system-panel/usr/lib/python2.4/site-packages/usp/plugins/easygconf.py
A    ubuntu-system-panel/ubuntu-system-panel/usr/lib/python2.4/site-packages/usp/plugins/system_management.py
A    ubuntu-system-panel/ubuntu-system-panel/usr/lib/python2.4/site-packages/usp/plugins/easybuttons.py
A    ubuntu-system-panel/ubuntu-system-panel/usr/lib/python2.4/site-packages/usp/plugins/recent.py
A    ubuntu-system-panel/ubuntu-system-panel/usr/lib/python2.4/site-packages/usp/plugins/computer.glade
A    ubuntu-system-panel/ubuntu-system-panel/usr/lib/python2.4/site-packages/usp/plugins/shortcuts.glade
A    ubuntu-system-panel/ubuntu-system-panel/usr/lib/python2.4/site-packages/usp/plugins/easyfiles.py
A    ubuntu-system-panel/ubuntu-system-panel/usr/lib/python2.4/site-packages/usp/plugins/applications.py
A    ubuntu-system-panel/ubuntu-system-panel/usr/lib/bonobo
A    ubuntu-system-panel/ubuntu-system-panel/usr/lib/bonobo/servers
A    ubuntu-system-panel/ubuntu-system-panel/usr/lib/bonobo/servers/usp.server
A    ubuntu-system-panel/ubuntu-system-panel/usr/bin
A    ubuntu-system-panel/ubuntu-system-panel/usr/bin/usp
A    ubuntu-system-panel/ubuntu-system-panel/usr/bin/uspconfig
A    ubuntu-system-panel/usp_update
 U   ubuntu-system-panel
Révision 124 extraite.
sweetth@sweetth-desktop:~$ cd /home/sweetth/ubuntu-system-panel/
sweetth@sweetth-desktop:~/ubuntu-system-panel$ ./usp_update 
./usp_update: line 15: ((: > : erreur de syntaxe : opérande attendu (error token is "> ")
USP is up-to-date

```

---

### Post by sweetthdevil on 2007-02-15
all right got it!

i simply did all the command from the script... :KS 


anyway, just a question, the search box seem to have a problem, what's the command to able to search for application?

---

### Post by PsyberOneZero on 2007-02-15
OK, I fixed up the script. It may have a few bugs in it but it works fine on my machine.

To Install:
```
./usp_update install ( or Install)
```
this is for first time

To Update
```
./usp_update update ( or Update)
```
or
```
./usp_update
```

I will work on having it remove the old gconf entries but that could get fun.

---

### Post by Mateo on 2007-02-17
installation doesn't work for me.  not sure why:

```
matthew@matthew-desktop:~/ubuntu-system-panel$ usp run-in-window
Using Standard Menu
Traceback (most recent call last):
  File "/usr/bin/usp", line 846, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 836, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 625, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 58, in __init__
    self.PopulatePlugins()
  File "/usr/bin/usp", line 384, in PopulatePlugins
    if pos == gtk.POS_LEFT:
UnboundLocalError: local variable 'pos' referenced before assignment
```

---

### Post by unabatedshagie on 2007-02-17
Thats the exact same error I get```
alex@mysterymachine:~$ usp run-in-window
Using Standard Menu
Traceback (most recent call last):
  File "/usr/bin/usp", line 846, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 836, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 625, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 58, in __init__
    self.PopulatePlugins()
  File "/usr/bin/usp", line 384, in PopulatePlugins
    if pos == gtk.POS_LEFT:
UnboundLocalError: local variable 'pos' referenced before assignment
```

---

### Post by Malac on 2007-02-17
@ unabatedshagie and mateo
I have fixed this but I am away from my machine until 2-00pm (GMT) so I will update the SVN.
This is my bad and is the result of too late a night, sorry.

---

### Post by Malac on 2007-02-17
> **Malac said:**
> @ unabatedshagie and mateo
I have fixed this but I am away from my machine until 2-00pm (GMT) so I will update the SVN.
This is my bad and is the result of too late a night, sorry.
FIXED:
Revision 128.
This only happened if tabs were not being used.
Sorry I should have tested all the possibilities.

---

### Post by Mateo on 2007-02-17
no need to apologize, I'm glad that it was a problem with the code because if it was something I was doing wrong I would probably never figure it out!  i'll try it out in a bit and let you know if it works now.

---

### Post by Mateo on 2007-02-17
sorry to say, still not working.  here's my latest output:

```
matthew@matthew-desktop:~/ubuntu-system-panel$ usp run-in-windowUsing Standard Menu
Loading plugin 'uspuser' : successful
Loading plugin 'system_management' : successful
Loading plugin 'applications' : successful
Traceback (most recent call last):
  File "/usr/bin/usp", line 846, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 836, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 625, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 58, in __init__
    self.PopulatePlugins()
  File "/usr/bin/usp", line 241, in PopulatePlugins
    MyPlugin = X.pluginclass( self )
  File "/usr/lib/python2.4/site-packages/usp/plugins/recent.py", line 70, in __init__
    self.RegenPlugin()
  File "/usr/lib/python2.4/site-packages/usp/plugins/recent.py", line 93, in RegenPlugin
    self.GetGconfEntries()
  File "/usr/lib/python2.4/site-packages/usp/plugins/recent.py", line 110, in GetGconfEntries
    self.RebuildPlugin()
  File "/usr/lib/python2.4/site-packages/usp/plugins/recent.py", line 121, in RebuildPlugin
    self.do_recent_applications_file()
  File "/usr/lib/python2.4/site-packages/usp/plugins/recent.py", line 239, in do_recent_applications_file
    TestForFiles( ".usp/recentapps.list" )
  File "/usr/lib/python2.4/site-packages/usp/plugins/easyfiles.py", line 18, in TestForFiles
    file = open(os.path.join(os.path.expanduser("~"), filename),"w")
IOError: [Errno 2] No such file or directory: '/home/matthew/.usp/recentapps.list'

```

I checked and I don't have a .usp directory.  I uninstalled USP1 and deleted the .usp directory.  maybe I shouldn't have done it that way.  i'll try to install USP1, then only delete the plugins and try to install uspSVN.

by the way, there is something wrong with the install script.  It doesn't create the /usr/share/usp directory, so the files it tries to copy there don't get copied.  I did that manually to get past that problem.

---

### Post by Mateo on 2007-02-17
Installing USP, making sure the plugin directory is empty, clearing the gconf stuff, then installing the SVN gets the job done.  Looking good.

---

### Post by sweetthdevil on 2007-02-17
two quick question if i may

How do i update the svn? do i need to erase the gconf setting? or any thing special, or do i need simply to run the script?

And my search box doesn't work, I can't type in it, and when i can it doesn't search any things.? :confused:

---

### Post by Mateo on 2007-02-17
to update the SVN you should probably clear your gconf with this:

```
gconftool-2 --recursive-unset /apps/usp
```

then run the command

```
./usp_update update
```

---

### Post by Mateo on 2007-02-17
how do you change the button icon?  I tried changing by putting in the entire location of the image (in my case /usr/share/icons/mandrake.png) but that didn't work.  are there size restrictions maybe?

---

### Post by kobewan on 2007-02-17
Alright, I've gotten the SVN version now (which is excellent I must add...I love tabs!) and the gap between my menu and panel is still there. I've also found out that this only occurs when it is on the bottom panel. If I move USP to the top panel, or drag my panel to a different side of the screen, then 'usp_offset' works perfectly.

> **sweetthdevil said:**
> 
And my search box doesn't work, I can't type in it, and when i can it doesn't search any things.? :confused:

Heh, just had the same problem (I think). Open up gconf-editor, to apps->usp->plugins->applications. Make sure that the 'do_not_filter' box is unchecked. Then, goto the field that says 'search_command' and make sure that it isn't empty. If it is, then find out what it used to say as the default.

I don't know why, but if you uncheck that box in USPConfig, it automatically clears the search command. I assume that this is a bug, since I can't think of any good reason for this. Mine is gone now too, and I'm missing my search until somewhat posts the default....

---

### Post by sweetthdevil on 2007-02-17
sweetth@sweetth-desktop:~/ubuntu-system-panel$ ./usp_update update
./usp_update: line 17: ((: > : erreur de syntaxe : opérande attendu (error token is "> ")
USP is up-to-date


same trouble with the update script! :(

---

### Post by chanders on 2007-02-17
^^ If you are running beryl, make sure focus stealing is set to 'None' !! ;-)

---

### Post by Malac on 2007-02-17
Search command fixed rev 129:
Actually clicking anything in the applications section of USPconfig  was wiping the search command, but hopefully now fixed.
Any probs let me know.

---

### Post by sweetthdevil on 2007-02-17
ok, i update it now, could you tell me which command to put for the search box, i restore the setting and the search box command is still empty. :/

And also, i read about tabs? i don't seem to have them, or don't know how to produce them, could i get some info please.

And last question, how do i get my firefox bookmarks to be available in ups, ups doesn't seem to read the file produce by firefox

Many thanks for your great work...

---

### Post by kobewan on 2007-02-17
Yeah, I also want that default search command. Could you please post it?

To find out how to make tabs, look here : [http://ubuntuforums.org/showthread.php?t=361376](http://ubuntuforums.org/showthread.php?t=361376)

I think (but am not sure) that you can read the Firefox bookmarks by downloading the extra plugins here:
[http://www.ubuntuforums.org/showpost.php?p=1981614&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1981614&postcount=2)
and setting up the internet plugin.

Oh yeah, and another bug report: USPConfig doesn't allow opening of folders that have a space in them when saving/loading backups. For example, if I'm trying to save to ~/Assorted Junk/USP , then it will save it as ~/Assorted.xml. It also won't load the xml file if you manually copy it the same folder above.

---

### Post by sweetthdevil on 2007-02-17
no need of the internet pluggin the places one form the svn version does it staight away. 

but don't know wich kind of file usp need :/

---

### Post by Mateo on 2007-02-17
I think I need the default search command too, it doesn't appear for me (though when I press the search button, it does work.

My only problem is that it searches my ~ folder, instead of the entire filesystem, so it's really no use.  anyway to fix that?

---

### Post by sweetthdevil on 2007-02-17
well, that the command i've got "gnome-search-tool --named=SEARCH_STRING --start"

But doesn't seem to work, 

and for the bookmarks USP read the file produce by Firefox, my mistake.

But from the latest svn, if you use the "places" item, you will see, a choice between places and bookmarks, but i couldn't find where to show USP where to get the actual bookmarks, probably a next feature.

But I must say, USP is a great tools!

Many many thanks to you guys!!

---

### Post by PsyberOneZero on 2007-02-17
@ sweetthdevil: Are you still having that error with the update script?

if so try running
```
svn up
./usp_update update
```
if that's still giving you problems then try running
```
usp_update install
```

---

### Post by Malac on 2007-02-17
@Mateo et al
the search command is:
**gnome-search-tool --named=SEARCH_STRING --start**

Here is an explanation of what you can do with the tabs with examples:
[http://ubuntuforums.org/showpost.php?p=2159324&postcount=46](http://ubuntuforums.org/showpost.php?p=2159324&postcount=46)


Hope this helps.

---

### Post by Strash on 2007-02-17
> **sweetthdevil said:**
> sweetth@sweetth-desktop:~/ubuntu-system-panel$ ./usp_update update
./usp_update: line 17: ((: > : erreur de syntaxe : opérande attendu (error token is "> ")
USP is up-to-date


same trouble with the update script! :(
Same problem here... on Ubuntu Edgy

---

### Post by kobewan on 2007-02-17
> **sweetthdevil said:**
> I think I need the default search command too, it doesn't appear for me (though when I press the search button, it does work.

My only problem is that it searches my ~ folder, instead of the entire filesystem, so it's really no use.  anyway to fix that?

I *think* that it's supposed to search the home folder when you click on the search button.

Anyways, to fix it, uncheck the do_not_filter key in gconf-editor under plugins-->applications. For some reason, unchecking it doesn't work if you do it in USPConfig, so make sure that USPConfig is not open first.


> and for the bookmarks USP read the file produce by Firefox, my mistake.

But from the latest svn, if you use the "places" item, you will see, a choice between places and bookmarks, but i couldn't find where to show USP where to get the actual bookmarks, probably a next feature.

I'm pretty sure that's supposed to be only for your Nautilus bookmarks, not your Firefox ones. 

Also, I can't figure out how to add anything to the Shortcuts plugin. Anybody care to explain what it does? (couldn't find any useful information with some searching)

---

### Post by chanders on 2007-02-17
To add to the shortcuts plugin, just pin USP and drag and drop items in the shortcuts plugin ;-)

---

### Post by Malac on 2007-02-17
> **kobewan said:**
> I *think* that it's supposed to search the home folder when you click on the search button.

Anyways, to fix it, uncheck the do_not_filter key in gconf-editor under plugins-->applications. For some reason, unchecking it doesn't work if you do it in USPConfig, so make sure that USPConfig is not open first.




I'm pretty sure that's supposed to be only for your Nautilus bookmarks, not your Firefox ones. 

Also, I can't figure out how to add anything to the Shortcuts plugin. Anybody care to explain what it does? (couldn't find any useful information with some searching)
For anyone who needs it the default search is :
gnome-search-tool --named=SEARCH_STRING --start

Fixed Do Not filter in uspconfig Rev 131.

To add something to the shortcuts plugin click the pin menu button top left of sidepane then drag a launcher/shortcut towards just below the Shortcuts title (this is tricky for the first one as the target area is really thin at this point) then let it go. Further shortcuts are easy as you can drop them on the first button.

Bookmarks is for the Nautilus bookmarks not Firefox. This was why I created the Internet plugin. This reads your default firefox bookmarks or you can point it at another file so long as it is in the same format.

Hope this helps.

---

### Post by PsyberOneZero on 2007-02-17
For those having problems with the update script, I just updated it (minor formatting stuff) but it might fix it. :? 

Is everyone on Edgy having problems with the script?

---

### Post by kobewan on 2007-02-17
Worked flawlessly for me. I installed it at revision 128 using 

```
./usp_update install
```

Right after you posted this, I checked to see if it worked using:

```
./usp_update update
```

and it worked without any problem. Told me that the latest version was 132, showed what had changed and then told me that installation was successful.

---

### Post by sweetthdevil on 2007-02-17
> **Malac said:**
> 

Bookmarks is for the Nautilus bookmarks not Firefox. This was why I created the Internet plugin. This reads your default firefox bookmarks or you can point it at another file so long as it is in the same format.


Is there any chance, in a near future to be able to use firefox bookmarks with the places plugins?

---

### Post by Mateo on 2007-02-18
where can I find a list of all of the plugins that are available by default with the svn?  not anything you have to install, just the ones you can type in uspconfig.

---

### Post by kobewan on 2007-02-18
Try looking at which files are in:

/usr/lib/python2.4/site-packages/usp/plugins

Or at the post [here]("http://ubuntuforums.org/showpost.php?p=1967430&postcount=1").

The default plugins should be:

uspuser
system_management
applications
shortcuts
places
computer
recent

---

### Post by Mateo on 2007-02-18
The application plugin doesn't seem to like anything but normal launchers.  My experience is that launchers which are supposed to run in terminal, run in the background.  And applications that run off wine don't load.  I think this feature needs major work, as it's possibly the most important in the program.

---

### Post by kobewan on 2007-02-18
Actually, I think that these are all because USP doesn't run anything off of bash. I don't know what it does run off of, and I don't have enough knowledge and experience with Linux to know if what I just said even made any sense :D.

Anyways, most problem are caused because USP isn't able to properly detect spaces in folder names (not even if you use quotation marks, or the '\' character). This screws with wine big time, since most programs that you want to launch are in "Program Files". I got around this by making a small script:

```
#/bin/bash
wine "C:\Program Files\uTorrent\uTorrent.exe" &
exit
```

Make it executable, and point USP at it by putting this in the exec field of the Favorites launcher:

"bash /script path/script"

Maybe not the best workaround, but it does its job. If you have problem with any other launchers, run "usp run-in-window" in a terminal and click on the launcher from the pop-up window. It should print some feedback about why the launcher isn't working.

---

### Post by Mateo on 2007-02-18
That solves wine (or is a workaround), but what about terminal programs?  Neither hellanzb or rtorrent will launch for me.  Hellanzb launches in the background, but I don't think rtorrent launches at all.

edit:  actually it does.  both launch in the background.

---

### Post by Malac on 2007-02-19
> **Mateo said:**
> That solves wine (or is a workaround), but what about terminal programs?  Neither hellanzb or rtorrent will launch for me.  Hellanzb launches in the background, but I don't think rtorrent launches at all.

edit:  actually it does.  both launch in the background.
I will be looking into the launching with terminal/wine problems.
I'll post back as soon as it is fixed.

---

### Post by Malac on 2007-02-19
.Scratch

---

### Post by ADRez on 2007-02-19
In latest svn version there is still a glitch: in system management control center is not aligned as install software, lock screen and quit. Can you solve it?

It's in system_management.glade file, after line 63 add this:
```
                        <property name="width_request">40</property>
```

---

### Post by kobewan on 2007-02-19
Wow, how'd you even notice it? The difference is pretty hard to see...

Also, just wondering, is there any way to use full paths for normal icons (i.e. not the icons for tabs)? Or is it not implemented (yet)?

---

### Post by Malac on 2007-02-19
> **ADRez said:**
> In latest svn version there is still a glitch: in system management control center is not aligned as install software, lock screen and quit. Can you solve it?

It's in system_management.glade file, after line 63 add this:
```
                        <property name="width_request">40</property>
```
Done in SVN Revision 140.

---

### Post by ADRez on 2007-02-19
Thanks!

```
Wow, how'd you even notice it? The difference is pretty hard to see...
```
Well, I didn't see it so hard to see, and it annoyed me a little... now it's OK :cool:

---

### Post by Malac on 2007-02-19
Updated SVN to Revision 141 with a fix for launchers that need to launch in a terminal from applications, recent apps and shortcuts.
I have tested this with all my launchers (and I do mean all :) ) but let me know if one of yours won't launch, or launches missing arguments, or errors in any other way.

---

### Post by Mateo on 2007-02-19
nope, not for me :( .  This is the first time I tried upgrading, so maybe I did it wrong, but I just downloaded the trunk and then ran ./usp_update update and it said it was now up to date.  But the launchers still launch in the background.  I think reset my gconf info and reran the install hoping that I updated incorrectly but the result is the same.

I can't exactly give you an error message either.  If I run usp run-in-window, the programs launch in the same terminal window that USP is running in.  not sure if that helps.

---

### Post by chanders on 2007-02-19
Make sure to remove USP  from the panel and re-add when you update ;-)

---

### Post by Mateo on 2007-02-19
now none of the launchers work.  here's what I get when I try to run Calculator:

```
TypeError: ButtonReleased() takes exactly 5 arguments (4 given)
```

i will reinstall USP1 and then upgrade it and hopefully it at least goes back to launching X based apps!

---

### Post by Mateo on 2007-02-19
I'm not sure which files to delete.  I tried just installing USP1 but USPsvn still showed up.

---

### Post by Mateo on 2007-02-20
So, I deleted every file that the script installs.  Deleted the ~/.usp directory.  Ran the command to clear the gconf.  Reinstalled usp1, then uninstalled it with apt-get (basically this just left the .usp directory I guess).  Then installed the latest SVN.  No go, same error message no matter which program I try to launch.

---

### Post by Malac on 2007-02-20
> **Mateo said:**
> So, I deleted every file that the script installs.  Deleted the ~/.usp directory.  Ran the command to clear the gconf.  Reinstalled usp1, then uninstalled it with apt-get (basically this just left the .usp directory I guess).  Then installed the latest SVN.  No go, same error message no matter which program I try to launch.
Have you rebooted or killall gnome-panel?
Revision 141 is the correct one for terminal launchers.
Can you please check that you have the revised execute.py file by running this in the first ubuntu-system-panel directory.
 ```
svn info ./ubuntu-system-panel/usr/lib/python2.4/site-packages/usp/plugins/execute.py | grep Rev
```You should get:
```
Revision: 141
Last Changed Rev: 141
```If not your update hasn't worked.
I've tried this on Edgy with beryl and metacity and it works on both.
Are you running Feisty?
Also there seems to be a bug. I'm not sure at what stage it is getting introduced whether it is a gnome bug or a USP one but I opened up some of my favourite app launchers in gedit and found the line that should read "Terminal=true", actually read "Terminal=Terminal=True".
It should be single word Terminal (capital T) with true (or false) all lowercase. Can you check this also?

---

### Post by roberTO on 2007-02-20
Same problem here...

"TypeError: ButtonReleased() takes exactly 5 arguments (4 given)"

Uninstall, clear all usp related stuff, install, rev: 141, but not working....
Also not work the right click menu (add favs...)
Output:

"TypeError: ButtonReleased() takes exactly 5 arguments (4 given)"

Run in Ubuntu Feisty, updated today 10.00 AM...

:(((
:confused:

---

### Post by roberTO on 2007-02-20
DELETED...

Not bug...

---

### Post by kobewan on 2007-02-20
> **roberTO said:**
> Same problem here...

"TypeError: ButtonReleased() takes exactly 5 arguments (4 given)"

Uninstall, clear all usp related stuff, install, rev: 141, but not working....
Also not work the right click menu (add favs...)

Yep, same thing here as well. I'm running on Edgy. The applications in "Favorites" launch, but not the ones in All Applications. When running, for example, Firefox in Favorites, it gives this message:> ['firefox']
False
['firefox']

(It doesn't give firefox in all the errors, e.g. for Gedit it puts 'gedit' in between the quotes). When running something that's in All Applications, it gives the same error about 5/4 arguments. It's been giving me the same error since I updated to rev. 137. I've tried restarting my computer, killall gnome-panel, remove and readd USP etc.

EDIT: Alright, I confirmed that the problem is in rev. 137 and after. If I run ```
svn update -r 136
``` and then ```
./usp_update install
``` USP starts working again. Installing rev. 137 (and after) again brings the problems back.

---

### Post by Malac on 2007-02-20
Okay it looks like I broke the All Applications section of the applications plugin,  sorry.:redface:
I'll get on it right away.

---

### Post by Malac on 2007-02-20
^^ Fixed in Revision 142.

---

### Post by Mateo on 2007-02-20
Ok, back to where we were at least.  ;)  Still no terminal apps are launching for me though.

> **Malac said:**
> 
Also there seems to be a bug. I'm not sure at what stage it is getting introduced whether it is a gnome bug or a USP one but I opened up some of my favourite app launchers in gedit and found the line that should read "Terminal=true", actually read "Terminal=Terminal=True".
It should be single word Terminal (capital T) with true (or false) all lowercase. Can you check this also?

I tried to look but couldn't find where the launchers were.  Most of them are in /usr/share/applications/ but these terminals apps I made manually.  I'm not sure if a .desktop file is created for launchers you make manually... I can't find a .desktop file for any of my terminal apps.  Maybe this is the problem!

---

### Post by Malac on 2007-02-20
> **Mateo said:**
> Ok, back to where we were at least.  ;)  Still no terminal apps are launching for me though.



I tried to look but couldn't find where the launchers were.  Most of them are in /usr/share/applications/ but these terminals apps I made manually.  I'm not sure if a .desktop file is created for launchers you make manually... I can't find a .desktop file for any of my terminal apps.  Maybe this is the problem!
The ridiculous part is that you have to open them in gedit to change the Terminal=False part or unless you use ls in a terminal you can't even see that they are called <something>.desktop .
As I say there was a bug in either gnome or usp which was making the Terminal line read Terminal=Terminal=False instead of Terminal=false perhaps you are suffering from this.
But this is definitely working for me now.

Here is an example of one of mine which launches firefox in a terminal:
```
[Desktop Entry]
Encoding=UTF-8
Name=Firefox Web Browser
Comment=Browse the World Wide Web
Exec=firefox %u
Icon=/usr/share/pixmaps/firefox.png
GenericName=Web Browser
Terminal=true
```
And the only difference to the one that doesn't is the last line changed to ```
Terminal=false
```

---

### Post by Malac on 2007-02-20
SVN Revision is now 143.
I have added hotkey opening to USP.
Alterations to uspconfig/Preferences to take this into account. Added _keybinder.so to plugins folder at the moment.

The default is set to <Ctrl><Alt>U at the mo as this didn't seem to be bound to anything already on my system. :)
This should open and close USP.
If you want to use the "Windows" keys then Meta_L or Meta_R without the <> symbols should do it.
Or if you use the word Menu without the <> symbols then the right hand key with a menu symbol and arrow on it (between the Alt Gr and Ctrl keys on the right) works to open USP.
If the demand is there I can add one key to open and one to close if you like.

EDIT:  Tested with metacity and beryl, both work fine.

---

### Post by kobewan on 2007-02-20
Excellent update :D.

Just a note though; when you open it with the hotkey, it opens pinned (regardless of your settings). You can close it  by hitting the hotkey again, or by clicking on the menu button. Is this supposed to happen or is it a bug? I imagine that it could be either...

---

### Post by Malac on 2007-02-20
> **kobewan said:**
> Excellent update :D.

Just a note though; when you open it with the hotkey, it opens pinned (regardless of your settings). You can close it  by hitting the hotkey again, or by clicking on the menu button. Is this supposed to happen or is it a bug? I imagine that it could be either...
Okay it doesn't seem to do this on mine, hmmmm.:confused:
It should follow the pin menu settings regardless of how it is called as all I've done is hook into the button's open menu function.
Most strange, I'll see if I can replicate it.

---

### Post by Mateo on 2007-02-20
Malac:

I can't check to see if mine says Terminal=true or not because I can't find the .desktop files. I even looked in terminal using ls and they aren't in the /usr/share/applications folder.  I created them using Alacarte...  Is there any other place they could be?  I even searched for all of the desktop files on my computer and couldn't find any of my terminal apps among them.

---

### Post by Malac on 2007-02-20
> **Mateo said:**
> Malac:

I can't check to see if mine says Terminal=true or not because I can't find the .desktop files. I even looked in terminal using ls and they aren't in the /usr/share/applications folder.  I created them using Alacarte...  Is there any other place they could be?  I even searched for all of the desktop files on my computer and couldn't find any of my terminal apps among them.
Unfortunately if you call your shortcut Firefox this is not necessarily what alacarte calls the actual .desktop file.
Seems daft to me but there you go. e.g. my Firefox .desktop file is actually called "-home-dave-.local-share-applications-firefox.desktop" even though what I see in nautilus is just "Firefox Web Browser".


You could try looking in [COLOR=DimGray]*<your-home-folder>*[/COLOR]/.usp/applications this is where usp stores your favourites.
Open gedit then open one of those files from inside gedit.

I'm not sure but I think alacarte may use /usr/share/app-install/desktop for files it creates.

Create this script in [COLOR=DimGray]*<your-home-folder>*[/COLOR]/.gnome2/nautilus-scripts
and call it "Open With GEdit" or something similar
```
#!/bin/sh
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
gedit $uri &
done
```make it executable chmod +x
It should then appear in your right-click menu under Scripts.
[ATTACH]25767[/ATTACH]
I find this saves time when editing .desktop files.

---

### Post by Mateo on 2007-02-20
You know what, I'm using a newer version of gnome-panel, perhaps this is somehow involved.  I'll try reinstalling the version in the repos.

also, still can't find the .desktop file.  checked both directories and they're simply not there.  I added the terminal programs to favorites and they work fine that way.  i guess i'll use that for now.

---

### Post by Malac on 2007-02-20
> **Mateo said:**
> You know what, I'm using a newer version of gnome-panel, perhaps this is somehow involved.  I'll try reinstalling the version in the repos.

also, still can't find the .desktop file.  checked both directories and they're simply not there.  I added the terminal programs to favorites and they work fine that way.  i guess i'll use that for now.
Which version of gnome were you using just out of curiosity. As if it was a newer one then we will probably come across this in the future.

---

### Post by Mateo on 2007-02-20
I think this is it:

[https://launchpad.net/ubuntu/+source/gnome-panel/2.16.1-0ubuntu4](https://launchpad.net/ubuntu/+source/gnome-panel/2.16.1-0ubuntu4)

---

### Post by chanders on 2007-02-20
@Mateo - .desktop files don appear with their extension in Nautilus. They look like an actual application and the only way to really know is to open them up in gedit. 

I find the easiest way is to drag a 'suspect' .desktop file directly in an open gedit window. If you get an error it wont show up but if it is a bonafide .desktop file it will open up ;-)

Also I think files created by Alacarte is in ~./local

---

### Post by Mateo on 2007-02-20
I never had a problem recognizing .desktop files in nautilus.  My problem was that they weren't in the /usr/share/applications/ or /usr/share/app-install/ directories.  I see that they are in the ~/.local folder though, along with a lot of old .desktop files.  I moved the relevant ones to /usr/share/applications.  No change in functionality.  I'm going to try and reinstall the version of gnome-panel that's in the repos but that might be difficult.  I'm not sure how to remove the one I installed from source.

---

### Post by chanders on 2007-02-20
Ok, cool Any particular reason you are using a custom compilled panel?

---

### Post by Mateo on 2007-02-21
I wanted to remove the arrow in the "Main Menu" applet.  There is a line of source that you can comment out, then compile it and the arrows are gone.  Don't need that anymore now that I'm using USP ;)

To no avail, though.  I uninstalled the old panel by sudo make uninstall, then reinstalled the repo version.  I can clearly see from a few features that this is the old gnome-panel now, but this didn't change the problem.  I'm at the point where I think i'll give up and hope it miraculously gets fixed in a future svn version ;)

---

### Post by delfick on 2007-02-21
thnx Malac for the hotkey support !! :D

though Meta_L doesn't work for me :(

even after "killall gnome-panel"

though "menu" worked :D

---

### Post by Malac on 2007-02-21
> **delfick said:**
> thnx Malac for the hotkey support !! :D

though Meta_L doesn't work for me :(

even after "killall gnome-panel"

though "menu" worked :D
Think this depends on your keymap and keyboard variant, you could try Super_L instead. If you run xev from a terminal that can give a clue as to what the key is being recognised as.

---

### Post by delfick on 2007-02-21
> **Malac said:**
> Think this depends on your keymap and keyboard variant, you could try Super_L instead. If you run xev from a terminal that can give a clue as to what the key is being recognised as.

hazaa!!!

I tried "Super" before which didn't work, adding the "_L" to it makes it magicly work :D

thnx :D

---

### Post by mikemn84 on 2007-02-21
Im not sure if this has been covered somewhere, but I recently downloaded the SVN USP and I can't get any border to display.  Both the USPconfig dialog and border_width in configuration editor are set to 6.  And usp run-in-window yields no errors.  Is there a setting im missing?

---

### Post by chanders on 2007-02-21
This was fixed in the last update to SVN. Try to update again ;-)

---

### Post by mikemn84 on 2007-02-21
One more thing,

When I go to my Places plugin under bookmarks the folder named 'School Stuff' opens one level beneath where it should.  So when I click it, I get taken to its parent folder where I can see 'School Stuff' listed.  The path listed in the title bar at this point is '/home/username/School Stuff' but it is actually showing '/home/username'.  So if I click on School Stuff, which im supposedly already in, it causes issues.  The other folders I have in bookmarks work fine, I'm thinking it could be because that 'School Stuff' has a space in it and the others dont.

Cheers and thanks for your hard work

---

### Post by PsyberOneZero on 2007-02-21
Several updates to the script :)  **SVN Rev. 148**
[COLOR="Red"]NOTE in 147 the script is broken (stupid error on my part) so if you already updated to 147 just type[/COLOR]
```
svn up
./usp_update install
```

**1st) Uninstall**
```
./usp_update uninstall
```
**2nd) Complete Uninstall**
this will remove your .usp directory in home and unset the gconf keys.
```
./usp_update uninstall complete
```
**3rd) First Time Install**
this is for those upgrading from USP 0.41, this also removes the old .usp dir and the old gconf keys.
```
./usp_update install fresh
```

This should be all the needed cases, let me know if there's anything missing or needed in the script.

---

### Post by Malac on 2007-02-22
> **mikemn84 said:**
> One more thing,

When I go to my Places plugin under bookmarks the folder named 'School Stuff' opens one level beneath where it should.  So when I click it, I get taken to its parent folder where I can see 'School Stuff' listed.  The path listed in the title bar at this point is '/home/username/School Stuff' but it is actually showing '/home/username'.  So if I click on School Stuff, which im supposedly already in, it causes issues.  The other folders I have in bookmarks work fine, I'm thinking it could be because that 'School Stuff' has a space in it and the others dont.

Cheers and thanks for your hard work
Fixed. SVN Revision 151. :)

---

### Post by sweetthdevil on 2007-02-22
Quick question, I want to use my mouse to open USP, got a MX518, so i kept the default shortcut <Ctrl><Alt>U and using xbindkeys to allow, the 8th boutton of my mouse using this shortcut, so i edit the file .xbindkeysrc like so:

```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:6
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
 m:0x0 + b:7
[B]"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Control_L]\[u]""
 m:0x0 + b:8[/B]
```

But obviously it doesn't work, anyone know what am I doing wrong?

---

### Post by kobewan on 2007-02-25
> **sweetthdevil said:**
> Quick question, I want to use my mouse to open USP, got a MX518, so i kept the default shortcut <Ctrl><Alt>U and using xbindkeys to allow, the 8th boutton of my mouse using this shortcut, so i edit the file .xbindkeysrc like so:

```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:6
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
 m:0x0 + b:7
[B]"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Control_L]\[u]""
 m:0x0 + b:8[/B]
```

But obviously it doesn't work, anyone know what am I doing wrong?

I've found xvkbd to be notoriously bad with handling many certain key presses (in particular, holding modifier keys). The -xsendevent option was supposed to fix it, but it never worked properly for me. I would recommend install, from the repositories, xautomation. It works muuuch better (IMO), and helped me configure my mouse properly. To use it, just edit your .xbindkeysrc file to include this:

```
"/usr/bin/xte 'keydown Control_R' 'keydown Alt_R' 'key u' 'keyup Alt_R' 'keyup Control_R'"
   b:8
```

(Remember, the spacing and capitalization is very important!) After that, open up a terminal and restart xbindkeys by typing in ```
killall -HUP xbindkeys
``` That should definitely work, I just tried it with my mouse without a problem.

---

### Post by kobewan on 2007-02-25
> **PsyberOneZero said:**
> 

**3rd) First Time Install**
this is for those upgrading from USP 0.41, this also removes the old .usp dir and the old gconf keys.
```
./usp_update install fresh
```

This should be all the needed cases, let me know if there's anything missing or needed in the script.

What would happen if you used this but hadn't installed USP 0.41 before? Would it still work, or would it give an error message, or what?

---

### Post by PsyberOneZero on 2007-02-25
> **kobewan said:**
> What would happen if you used this but hadn't installed USP 0.41 before? Would it still work, or would it give an error message, or what?

It would just reset all of your options, and clear out any downloaded plug-ins in ~/.usp

It could also be used to do a clean re-install.

---

### Post by sweetthdevil on 2007-02-25
> **kobewan said:**
> I've found xvkbd to be notoriously bad with handling many certain key presses (in particular, holding modifier keys). The -xsendevent option was supposed to fix it, but it never worked properly for me. I would recommend install, from the repositories, xautomation. It works muuuch better (IMO), and helped me configure my mouse properly. To use it, just edit your .xbindkeysrc file to include this:

```
"/usr/bin/xte 'keydown Control_R' 'keydown Alt_R' 'key u' 'keyup Alt_R' 'keyup Control_R'"
   b:8
```

(Remember, the spacing and capitalization is very important!) After that, open up a terminal and restart xbindkeys by typing in ```
killall -HUP xbindkeys
``` That should definitely work, I just tried it with my mouse without a problem.

Many thanks!!!!

Love you man, but just to let you know i had to change to:

```
"/usr/bin/xte 'keydown Control_R' 'keydown Alt_L' 'key u' 'keyup Alt_L' 'keyup Control_R'"
   b:8
```

Note the Alt_L :) 

Many many thanks!

---

### Post by kobewan on 2007-02-25
> **PsyberOneZero said:**
> It would just reset all of your options, and clear out any downloaded plug-ins in ~/.usp

It could also be used to do a clean re-install.

Alright, updated the guide.

Also, has the feature-freeze started? I was wondering if it was possible to include an option which makes the search show hits from your shortcuts as well your applications.

Just out of curiosity sweetthdevil, why Alt_L over Alt_R? Do you have Alt_R set as your third level chooser?

---

### Post by sweetthdevil on 2007-02-26
> Just out of curiosity sweetthdevil, why Alt_L over Alt_R? Do you have Alt_R set as your third level chooser?

what do you mean??

---

### Post by sweetthdevil on 2007-03-09
so what's new?
Just update to 169..

---

### Post by ssteinbr on 2007-03-20
Hello all,
  I've been trying to get the USP svn running on my machine and have run into a few problems.  The stable version (installed from the deb file) works fine, but I'd like to try out all the new goodies.  Grabbing the svn and installing seems to go fine.  After logging out, the applet shows up on the panel but nothin' happens when I click on it.  
I've been browsing through the forums for awhile, but haven't been able to find a solution.

Here's the output of usp run-in-window

```
/usr/bin/usp:31: RuntimeWarning: Python C API version mismatch for module _keybinder: This Python has API version 1012, module _keybinder has version 1013.
  from _keybinder import tomboy_keybinder_bind as bindkey
******** PLEASE IGNORE ANY API VERSION WARNING ***********
********** IT SHOULD NOT EFFECT USP OPERATION ************
Using Standard Menu
Loading plugin 'uspuser' : successful
Loading plugin 'system_management' : successful
Loading plugin 'applications' : successful
Loading plugin 'recent' : successful
Traceback (most recent call last):
  File "/usr/bin/usp", line 916, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 901, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 663, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 70, in __init__
    self.PopulatePlugins()
  File "/usr/bin/usp", line 440, in PopulatePlugins
    self.plugins[plugin].do_plugin()
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 647, in do_plugin
    self.Todos()
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 411, in Todos
    ItemButton.MyButtonName = path
UnboundLocalError: local variable 'path' referenced before assignment


```


Looking forward to figuring out how I can get USP svn working.  BTW, ver 0.41 works great, awesome app.

---

### Post by Malac on 2007-03-20
@ssteinbr
It looks like one of your .desktop files is corrupt or doesn't have a path statement.
Can you check the~/.usp/applications.list has no blank lines in it.
As a quick fix insert this line:```
                    path="Error"
```at line 370 just above```
                     for grandchild in child.get_contents():
```So it reads:```
                    path="Error"
                    for grandchild in child.get_contents():
```This should allow usp to launch but you may have a damaged menu entry, chanders would know better.

---

### Post by ssteinbr on 2007-03-20
@Malac - Thanks for the quick reply.  ~/.usp/applications.list seems tp be a blank file.  I found

```
for grandchild in child.get_contents():
```

in the file usr/lib/python2.4/site-packages/usp/plugins/applications.py, and placed

```
path="Error"
```

above it as suggested.  And now usp run-in-window gives 
```

ssteinbr@dude:~$ usp run-in-window
/usr/bin/usp:31: RuntimeWarning: Python C API version mismatch for module _keybinder: This Python has API version 1012, module _keybinder has version 1013.
  from _keybinder import tomboy_keybinder_bind as bindkey
******** PLEASE IGNORE ANY API VERSION WARNING ***********
********** IT SHOULD NOT EFFECT USP OPERATION ************
Using Standard Menu
Loading plugin 'uspuser' : successful
Loading plugin 'system_management' : successful
Loading plugin 'applications' : successful
Loading plugin 'recent' : successful
Traceback (most recent call last):
  File "/usr/bin/usp", line 916, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 901, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 663, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 70, in __init__
    self.PopulatePlugins()
  File "/usr/bin/usp", line 440, in PopulatePlugins
    self.plugins[plugin].do_plugin()
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 648, in do_plugin
    self.Todos()
  File "/usr/lib/python2.4/site-packages/usp/plugins/applications.py", line 414, in Todos
    ItemButton.connect( "button_release_event", self.ButtonReleased, "Favs", InTerm )
UnboundLocalError: local variable 'InTerm' referenced before assignment
```

Thanks again for the help!

---

### Post by Malac on 2007-03-20
@ssteinbr
Can you download the latest SVN Revision 213, this should be fixed now, hopefully :).

---

### Post by ssteinbr on 2007-03-20
Malac, Thank you thank you!  Seems to be workin' fine now.  Great work.  Not that I know that much about programming/scripting, but I'm curious as to what the problem was.

---

### Post by Malac on 2007-03-20
> **ssteinbr said:**
> Malac, Thank you thank you!  Seems to be workin' fine now.  Great work.  Not that I know that much about programming/scripting, but I'm curious as to what the problem was.
As Python doesn't use { } like C to denote program flow it use whitespace, either tabs or spaces.
e.g.
```
    if this == that:
        do-this
        do-this-too
```Both statements get executed if this == that as they are both indented the same amount after the if staement.
However:
```
    if this == that:
        do-this
    do-this-too
```In this example do-this-too gets executed always as it is outside the indented section.
C gets round this by using { }
e.g.
```
    if (this == that){
    do-this;
    do-this-too;}
```C just executes the bit between the {}.

Unfortunately some of the older plugins suffer from a mix of tabs and spaces so the program flow can get a little confused. This was the case here. It took me a while to figure out that it was this with your problem.
You can illustrate the problem by opening applications.py in gedit and going to [Edit->Preferences] "Editor" tab and changing the Tab width value.

---

### Post by ssteinbr on 2007-03-20
Thanks again for taking the time.  One of my resolutions for the year is to learn a bit more about some these languages.  That way, maybe I can fix somethings myself.

---

### Post by Malac on 2007-03-20
> **ssteinbr said:**
> Thanks again for taking the time.  One of my resolutions for the year is to learn a bit more about some these languages.  That way, maybe I can fix somethings myself.
Give python a try. It's really quite intuitive and you can be up and running really quickly.
[http://docs.python.org/](http://docs.python.org/)
[PyGTK 2.0 Tutorial]("http://www.pygtk.org/pygtk2tutorial/index.html")

---

### Post by ssteinbr on 2007-03-20
> **Malac said:**
> Give python a try. It's really quite intuitive and you can be up and running really quickly.
[http://docs.python.org/](http://docs.python.org/)
[PyGTK 2.0 Tutorial]("http://www.pygtk.org/pygtk2tutorial/index.html")

Will do.  Thanks for the links.

---

### Post by panicz on 2007-03-24
im not able to add usp to panel
in console after 'usp run-in-window' command i got:
```
Traceback (most recent call last):
  File "/usr/bin/usp", line 25, in <module>
    from easygconf import *
  File "/usr/lib/python2.4/site-packages/usp/plugins/easygconf.py", line 3, in <module>
    from easybuttons import *
ImportError: No module named easybuttons

```
svn version 223

---

### Post by xpod on 2007-04-03
No joy with the .deb on my Edgy install but this one works a treat:) 
All i need to do now is make it look as nice as some of the ones i`ve seen posted:-k 

Good stuff!!

---

