---
title: "Digital picture frame with weather/news"
date: 2009-07-16
forum: The Cafe
---

### Post by canabal on 2009-07-16
Hi all,

I posted this to the tutorials section a while back, but it did not go through, likely because it is not yet ready in terms of cleanliness and ease of use.

I would like to share it anyway with the community, and I hope someone can assist me with checking through it, or making suggestions for ease of use.

The tutorial starts now:

Picture Frame

This project started when I wanted to build a picture frame from an old laptop a friend of mine gave me.  In this tutorial I will cover the software section of the process, and possibly expand to the hardware in the future.  My goal is to mount it in the back of a picture frame in the coming months, but that may require some hardware modifications to cut down on weight.

This will also sync automatically with a media-server or computer you have elsewhere to update as you add new pictures.

This tutorial will show you how to point firefox at certain web pages for certain amounts of time to show you the weather, show you the news, or do anything you want from firefox.

Steps:

Install Ubuntu:
I recommend the latest version (9.04 at the time of writing) so all the apps are up to date which can be found at [www.ubuntu.com](www.ubuntu.com).  We will be using a number of programs to run the various processes, and if they are older versions, they may not function the same as they currently do.  There are many tutorials online of how to do this, but it is very straightforward so there should be no need.

When installing, instruct it to take the entire hard drive (as the rest will not be used for anything).  Also, ensure you have automatic login enabled, you can do it later also, but it is easier if you do it straight off the bat.

Set up the internet:
Once you get into ubuntu for the first time, manually configure the wireless (or wired if that is your choice) to automatically connect for any user, and also to have a static IP (easier to remote desktop later if needed)

Set up remote desktop:
Do this through System>Preferences>Remote Desktop
Tick the "Allow other users to view your desktop" box.
Tick the "Allow other users to control your desktop" box.
Un-tick the "You must confirm each access to this machine" box. (necessary to untick because you will not have input devices attached at all times)
Your choice if you want a password and therefore to tick the "Require the user to enter this password: " box.
Tick the "Configure network automatically to accept connections" box.
The notification area choice is up to you, I let it always display an icon.

You should test it from another computer now to ensure it works.

Install programs:
These programs will be necessary to run the slideshow and sync.

gnome-schedule - a program that will assist in the managing of schedules (a gui that runs on top of crontab, so if you can use the cmd line, feel free to leave this out)
feh - a full-screen, non gui slideshow app
conduit - the program I am using to sync with the other computer/media server
samba + smbfs - samba allows the computer to see windows shares, and allows mounting the folder you want for syncing.

therefore the command you get is:
In a terminal type "sudo apt-get Install gnome-schedule feh conduit samba smbfs" (without the quotes)

Mount shared directory via samba: (from [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently))
Mounting a directory will allow you to:
a) use the pictures directly from another computer or media server if you so wish
b) allow you to sync the other compter or media server with the pictureframe

I am assuming you have an unprotected network share that allows guest access, if not use the wiki.ubuntu.com link above to help with other options.

to do this first, you will need to create a directory to mount the shared directory to:
In a terminal type "sudo mkdir /media/mountname"  (without the quotes)

You must then edit your /etc/fstab file to automatically mount the drive:
In a terminal type "sudo gedit /etc/fstab"  (without the quotes)
Add the line: //servername/sharename  /media/mountname  cifs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0

In the place of servername, you can also put an ip address.

guest indicates you don't need a password to access the share.
uid=1000 makes the Linux-user with specified uid or username owner of the mounted share, thereby allowing that user to rename files.
the combination iocharset=utf8,codepage=unicode,unicode allows access to files with names in non-English languages. This doesn't work with shares of devices like the Buffalo Tera Station, or Windows machines that export their shares using ISO8895-15. With these the codepage argument has to be codepage=cp850, otherwise characters like the German 'Umlaute' are displayed as garbage. 

Then save the file and exit the text editor.

In a terminal type "sudo mount -a" (without the quotes) to mount the drive for now, but on bootup it should automatically mount in the future.

Set up syncing:
Open conduit (it should be in the tray at the top).  Use the file menu and in examples, choose "synchronize two folders".
In the middle of what appears, right click on the line and untick "two way sync", and tick "always up to date".
For the folder on the left, choose the shared folder you have mounted, and on the right, choose your /home/username/Pictures folder.
Start a sync and it will do a full initial sync.

Set up your firefox pages:
In order to get the information to fit all on one screen, you will likely need to modify firefox and the web pages you are setting up slightly through a few addons.
in the addons menu, search for and install: greasemonkey and platypus.
greasemonkey allows scripts to be run.
Platypus allows you to go to a webpage and delete things you see (it uses greasemonkey).

So you can now go to the webpage you want to be shown, and using platypus, you can delete what you do not want to see (ads etc) which will allow everything to fit on one page.  Bookmark that page as the URL will be used later.

Using feh:
to use feh, there are a number of commands that are needed for different things, they can be seen by typing "feh --help" (without the quotes)in the command line.
some notable ones:
-r - recursive, meaning it checks folders within the folder that is chosen.
-z - randomize order
-D # - in the place of the # put a number for how long you want each slide to appear
-F - fullscreen
-Z - auto zoom's the image to fullscreen
--hide-pointer - hides the mouse pointer

That is what I used, but there are other options in the --help menu.  For me it turned out to be:
So in a terminal I typed "feh -r -z -D 5 -F -Z --hide-pointer /home/username/Pictures/" (without the quotes)

Set up the scheduler:
Using gnome-schedule, you choose what time you will have each program start (it is very basic using the scheduler).
for the feh command, you will add "export DISPLAY=:0 && " in front of the command or it will not appear properly.
so I typed in "export DISPLAY=:0 && feh -r -z -D 5 -F -Z --hide-pointer /home/username/Pictures/" with the timing 0 9 * * * (minute, hour, day, month, year)
when you want it to end, you type in "killall feh" which I did for 29 8 * * *

For firefox, you use the command "firefox http://www.xxxxx.com/xxx" from the URL you used before and my timing was 30 8 * * *
and then "killall firefox" with the timing 59 8 * * *

From now, you set your computer to run and all should be well.
I plan on re-vamping this tutorial with pictures and possibly hardware stuff in the future, but please let me know any tips, even if it may just be spelling mistakes.

---

### Post by canabal on 2009-07-17
Thoughts anyone?

---

### Post by starcannon on 2009-07-17
While having a list of great software, and instructions to install/use it is a great place to start; what about the picture frame itself? When I got to the end of the tutorial, my imaginary self still had a laptop, not a picture frame. While all laptops may be different in one way or another, there will be a general ballpark method to building a picture frame case to house the monitor and laptop guts.

Anyway, great article, perhaps you'll need to release it as a series though.

GL and HF

---

### Post by canabal on 2009-07-20
Thanks for the tips, and that is a very good point, I do need to work on the hardware.  Unfortunately, I have yet to do the hardware modification myself as I am in the finishing weeks of university.  I will attempt to do a tutorial for it, but I know it will not be up to scratch with many others out there (i.e. those at instructables.com).

As for releasing it in a series, that is a great idea, as currently it is long and drawn out, not very inviting for a newbie.

---

