---
title: "Attach Pictures to new Email using Nautilus"
date: 2007-08-06
forum: Tutorials
---

### Post by razerraz on 2007-08-06
**Mailpictures nautilus extension** ------ **Download the last version : [mailpictures-0.96.deb](http://sourceforge.net/projects/mailpictures/files/mailpictures/mailpictures-0.96.deb/download)**
[[IMG]http://brainstorm.ubuntu.com/idea/19868/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/19868/)

**Up 16/11/2009 - 0.96 released : [mailpictures-0.96.deb](http://sourceforge.net/projects/mailpictures/files/mailpictures/mailpictures-0.96.deb/download)**

Changelog 0.95-> 0.96 :
[I]Works now with Windows and samba share folders
Use of internal perl zip library instead of zip shell command
Bugfixes, code cleanup, optimisation[/I]


Mailpictures is a nautilus extension. It allows sending pictures and files directly from a nautilus window
It take the place of "Nautilus-sendto", who seems to have less features

Here is a short list of it features :
Support for mailers Evolution, Mozilla Thunderbird, Kde Kmail et Icedove
Save settings
Access to default settings, via Gnome menus
If there are pictures in the selection  :
  Ability to change size : width 1024, 800, 600 or custom
  Ability to change jpg compression
  Ability to create archive with the files
  Ability to have the size estimation of the selection
  Ability of direct pictures sending, using default settings
If the selection is data files :
  Ability to create zip archive for several files

**Installation :**
The ubuntu package installer (gdebi) will take care of that without any questions. 
**You must log out/log on your session to have the nautilus menu entry**
If you have problems installing this application, please post a message here

**Screenshots overview**

-------------------------------------------- **Default settings** --------------------------------------------------------

You can change the default settings via the gnome menu:

[img]http://razerraz.free.fr/MailPictures/App_Configure.jpg[/img]

[img]http://razerraz.free.fr/MailPictures/App_ConfigWin.jpg[/img]

-------------------------------------------- **Pictures sending** --------------------------------------------------------

[img]http://razerraz.free.fr/MailPictures/App_Launch.gif[/img]

[img]http://razerraz.free.fr/MailPictures/Launch_Pics.jpg[/img]

[img]http://razerraz.free.fr/MailPictures/Processing.jpg[/img]

-------------------------------------------- **Sending files** --------------------------------------------------------

[img]http://razerraz.free.fr/MailPictures/Launch_Datas.jpg[/img]

[b][Mailpictures on Sourceforge](http://sourceforge.net/projects/mailpictures)
[Mailpictures on Freshmeat](http://freshmeat.net/projects/mailpictures)
[Mailpictures on Launchpad](https://launchpad.net/mailpictures)[/b]

**Mailpictures nautilus extension** ------ **Download the last version : [mailpictures-0.96.deb](http://sourceforge.net/projects/mailpictures/files/mailpictures/mailpictures-0.96.deb/download)** 
[[IMG]http://brainstorm.ubuntu.com/idea/19868/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/19868/)

---

### Post by razerraz on 2007-08-14
Version 0.4 released :
Changes from release 0.4 <- 0.3
===============================
Bug fixes :
	Install and uninstall script should not depend on gladexml-perl

Fork main process and add a small status window with progression bar
Add Application window icon

Take look at Mail Pictures on GrumZ nautilus-actions webpage :
[http://www.grumz.net/?q=node/298](http://www.grumz.net/?q=node/298)

---

### Post by razerraz on 2007-08-26
Version 0.6 released :
Changes from release 0.6 <- 0.5
===============================
Bug fixes :
	Replace special caracters in selection's filenames when thunderbird is selected : bug in attachment command line
	Fork launching of mailer to be sure progress window is always closed when necessary

Improvment of progress window artwork
Add "About" dialog
Add custom resolution setting

Changes from release 0.5 <- 0.4
===============================
Bug fixes :
	Imlib2 functions width a height don't work with old versions, replace by get_

Email attachment and zip creation is now possible for all type of files, not only images
Install script tells now to uninstall before, if old version found
Add Gentoo specific emerge command for dependencies

---

### Post by ubi-laptop on 2008-10-12
wonderful job.
works a charme.
thank you.

---

### Post by ubi-laptop on 2008-10-12
wonderful job.
works a charme.
thank you

---

### Post by razerraz on 2009-02-19
Mailpictures is now deb packaged.
Some other improvements have been made :
better interface (I guess)
estimate the size of attachment before sending mail

IMPORTANT : For users who have used older tar.gz release, please run the uninstall.pl script present in the archive

Download Mailpictures here : [mailpictures-0.91.deb](http://razerraz.free.fr/mailpictures-0.91.deb)

---

### Post by binbash on 2009-02-20
Thanks for the update, it works great

---

### Post by razerraz on 2009-02-21
Thanks for your feedback

I need allways guys for translating
You'll find my email in the "about" window, by clicking in the mailpictures logo

---

### Post by binbash on 2009-02-21
One bug : 

I try to attach 14kb image, then i click estimated file size.It says 0.0mo.I tried this one different picture around same size, it still says 0.0mo

---

### Post by razerraz on 2009-02-21
> **binbash said:**
> One bug : 

I try to attach 14kb image, then i click estimated file size.It says 0.0mo.I tried this one different picture around same size, it still says 0.0mo

In fact, less than 100ko selection always return 0.0.
But is it really a mess ?

---

### Post by binbash on 2009-02-22
No it is ok for me, i don't care since i don't use the file size feature.But of course it will be better if it returns the valid size if the image(s) is under 100kb.

---

### Post by razerraz on 2009-02-23
> **binbash said:**
> No it is ok for me, i don't care since i don't use the file size feature.But of course it will be better if it returns the valid size if the image(s) is under 100kb.

I'll take care of that for future releases

---

### Post by razerraz on 2009-03-21
EDIT 21/03/2009: 
[b]Version 0.92 released : [mailpictures-0.92.deb](http://razerraz.free.fr/mailpictures-0.92.deb)

Improving of the size estimation : [/b]
   The progress win appears during process
   If the size < 1024, Ko is used instead of 0.x Mo

**Add direct email mode : The nautilus contextual menu give now two different choices**
   *Send as email attachment : setup* - open mailpictures conf window
   *Send as email attachment* - use saved setup and open directly new email window

**Please give feedback !!!**

---

### Post by desperado666 on 2009-03-21
Can i use it with Opera ?

---

### Post by razerraz on 2009-03-21
> **desperado666 said:**
> Can i use it with Opera ?

Not at this time, but if you know the command line for opening a new email writing window, who take care of line arguments for attachment, I can add it easly

---

### Post by razerraz on 2009-03-25
A new sourceforge project has been opened for mailpictures :
[http://sourceforge.net/projects/mailpictures/](http://sourceforge.net/projects/mailpictures/)

Thanks to report bugs, blueprints, eventual contribution on it

---

### Post by razerraz on 2009-04-11
Hi,

Please be aware that actually mailpictures don't work with the new gnome version (2.26), from the jaunty release
The problem is nautilus-action related, and mailpictures use this extension to handle the selection.
Unfortunaly, nautilus-actions is not anymore maintened by the author, it is in C so I don't have capability to debug it
You can follow the bug evolution here :
[http://bugzilla.gnome.org/show_bug.cgi?id=574919](http://bugzilla.gnome.org/show_bug.cgi?id=574919)

---

### Post by binbash on 2009-04-11
> **razerraz said:**
> Hi,

Please be aware that actually mailpictures don't work with the new gnome version (2.26), from the jaunty release
The problem is nautilus-action related, and mailpictures use this extension to handle the selection.
Unfortunaly, nautilus-actions is not anymore maintened by the author, it is in C so I don't have capability to debug it
You can follow the bug evolution here :
[http://bugzilla.gnome.org/show_bug.cgi?id=574919](http://bugzilla.gnome.org/show_bug.cgi?id=574919)

That is bad news

---

### Post by razerraz on 2009-04-12
> **binbash said:**
> That is bad news

Don't panic, it seems I have allready found a way to get it working without using nautilus-actions anymore, and by the way a great guy (who help me a lot with python bindings) have allready post a patch to get nautilus-actions working with 2.26.

---

### Post by binbash on 2009-04-13
Great, i really like this extension and i will be happy if i can use it at my jaunty box.Again thanks for this awesome extension..

---

### Post by razerraz on 2009-04-21
**Mailpictures nautilus extension** ------ **Download the last version : [Mailpictures-0.93.deb](http://razerraz.free.fr/mailpictures-0.93.deb)** 

Changelog - 0.93 :
[i]New interface
Nautilus-actions is no more used (python-nautilus)
Ubuntu Jaunty support
New gnome menu entry for default settings
Icedove Mailer support
So many things...[/i]

---

### Post by binbash on 2009-04-22
Thanks for the jaunty update and other features!

---

### Post by razerraz on 2009-04-22
> **binbash said:**
> Thanks for the jaunty update and other features!

You are welcome !

---

### Post by razerraz on 2009-05-20
A brainstorm about mailpictures :

[http://brainstorm.ubuntu.com/idea/19868/](http://brainstorm.ubuntu.com/idea/19868/)
[[IMG]http://brainstorm.ubuntu.com/idea/19868/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/19868/)

---

### Post by razerraz on 2009-05-21
**Up 21/05/2009 - 0.94 released : [mailpictures-0.94b.deb](http://sourceforge.net/project/downloading.php?group_id=257360&filename=mailpictures-0.94b.deb)**

Changelog :
[I]Support folders as selection
UI change
Cancel during process is now effective
Don't do resizing of pictures if they have small size
Stop process at the beginning if one of the selected file is too big (15Mo)
Optimisation
Rewrite of the size estimating [/I]

---

### Post by razerraz on 2009-05-23
Version 0.94b : minor bugs fix of 0.94
[mailpictures-0.94b.deb](http://sourceforge.net/project/downloading.php?group_id=257360&filename=mailpictures-0.94b.deb)

---

### Post by razerraz on 2009-07-17
**Up 17/07/2009 - 0.95 released : [mailpictures-0.95.deb](http://sourceforge.net/projects/mailpictures/files/mailpictures/mailpictures-0.95.deb/download)**

Changelog 0.94-> 0.95 :
[I]Support for thunderbird 3.x
Use of exiftool instead of libexif for exif orientation
Bugfixes[/I]

---

### Post by razerraz on 2009-11-16
**Mailpictures nautilus extension** ------ **Download the last version : [mailpictures-0.96.deb](http://sourceforge.net/projects/mailpictures/files/mailpictures/mailpictures-0.96.deb/download)**
[[IMG]http://brainstorm.ubuntu.com/idea/19868/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/19868/)

**Up 16/11/2009 - 0.96 released : [mailpictures-0.96.deb](http://sourceforge.net/projects/mailpictures/files/mailpictures/mailpictures-0.96.deb/download)**
Changelog 0.95-> 0.96 :
[I]Works now with Windows and samba share folders
Use of internal perl zip library instead of zip shell command
Bugfixes, code cleanup, optimisation[/I]

---

### Post by simonbcn on 2009-12-17
Thanks for this useful program.
I have a problem with v0.96. 
My Preferences windows:
[[IMG]http://i238.photobucket.com/albums/ff28/simonbcn/especial/th_captura_010.png[/IMG]]("http://i238.photobucket.com/albums/ff28/simonbcn/especial/captura_010.png")

I send 7 images but this program doesn't compress them into a file ZIP. Is this a bug?
Regards

---

### Post by razerraz on 2010-01-16
> **simonbcn said:**
> Thanks for this useful program.


You are welcome

> **simonbcn said:**
> I send 7 images but this program doesn't compress them into a file ZIP. Is this a bug?
Regards

No, it is supposed to be a feature, but I admit : it is not clear and I don't know if I'm right on that.
If you look at the exact tip in the config window, it says : "create a zip archive for several **data** files"
In fact, creating a zip archive without a special setup during process only affect when there are data files in the selection.
Generaly, users wants that the mailer show the sending pictures directly, so they do not create archive with.
If you want to do special thing, like sending a lot of pictures with low quality in a zip, you have to setup that during process

---

### Post by salguod on 2010-05-02
I have have been looking for something like this for a long time! Very nice.


I have been using it and it works well, but...
ALL the images emailed end up 550x400 pixels, no matter what I choose in the configuration panel, AND since 550x400 is not always the same proportion as the original, they come out a bit stretched.

Sorry for the complaints, because I really like the action. I hope it helps improve future releases. ;)

salguod

---

### Post by tellapu on 2012-01-18
Hi! Thanks for this great tool. I have used it for a long time.
Now I switched to Ubuntu 11.10 and also installed nautilus actions extra (NAE) ([https://launchpad.net/~dr3mro/+archive/nautilus-actions-extra]("https://launchpad.net/%7Edr3mro/+archive/nautilus-actions-extra")).
Then I installed mailpictures 0.96, but it would not show in the context menu of nautilus. I can open the preferences with "send by email" through the dash. Not sure if there are some conflicts between mailpictures and the NAE.

Any hints? 
[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

### Post by ilmkidunya on 2012-01-20
Good Tutorial keep it up

---

