---
title: "Volenteers Required to test Small App"
date: 2006-09-13
forum: The Cafe
---

### Post by DoctorMO on 2006-09-13
Attached to this post you will find a small python/gtk program which should run on all ubuntu machines without any problems.

It's the editor section of my up and comming hardware project. the design is basicly around the idea of guiding data structure by existing data choices. these can be seen in the way it handles drop down and booklean checkboxes and the way in which it can have sub-values for each kind of pre defined choice you can make.

I need some bug testing done on it and to see if the comunity has any ideas on improvement. the aim is to be able to capture user input for hardware information in a structured way.

For all those developers and geeks the data that is saved is in data.xml and the data structure is in conf/fields/fields.xml

---

### Post by xhaan on 2006-09-13
Seems to work, it correctly saved what I entered in the program into the xml file, and then loaded the correct values when I restarted the script.

Is this what it does? Should I be doing anything else with it?

---

### Post by DoctorMO on 2006-09-14
Yep thats perfect. even though there has only been one test I'll begin merging it into the main project. thanks xhaan

---

### Post by Polygon on 2006-09-14
works perfectly.

---

### Post by DoctorMO on 2006-09-14
Thanks Polygon, nothing in the interfact that makes understanding what it does difficult?

---

### Post by maniacmusician on 2006-09-14
> **DoctorMO said:**
> Thanks Polygon, nothing in the interfact that makes understanding what it does difficult?
well  at this point it's hard to answer that question, since there's not much to understand; it's not presented relatively to the rest of the project.

But it didn't seem complex or anything. I guess the true test will be after it's integrated

---

### Post by DoctorMO on 2006-09-14
which it now is:

[http://divajutta.com/doctormo/do.tar.bz2](http://divajutta.com/doctormo/do.tar.bz2)

If you can all form an queue, download this software which is at mile stone 3 and have a play and tell me how you break it.

I've just added all my own hardware so if you happen to have any of the devices I do you should see them (I admit this is unlikly)

To Extract:

tar xjvf do.tar.bz2

To Run:

cd do
./do.py

You must be running Ubuntu Dapper or Kubuntu with gtk-python installed.

As soon as Mile stone 4 is there I'll make a start on the server side (collecting all the information)

---

### Post by maniacmusician on 2006-09-14
:-P what happened to using the website? lol, i'll try it out and add it to the website later. should I assume this is dohickey 0.04?

For all other users that don't know what's going on; This is the Dohickey Project. you can read more about it at [http://dohickey.project.googlepages.com](http://dohickey.project.googlepages.com) . It explains the project, it's goals and all that. This current release should be up in a couple of hours at the latest (probably within the hour). 

Thanks.

---

### Post by Polygon on 2006-09-14
is edit supposted to do anything in that program? cause it didnt do anything for me. quit worked though

here is my console output in case you want it, dont mind the gtk errors. its a problem with my icon theme and i get it with everything.

> 
./do.py:37: GtkWarning: Theme directory 96x96/action of theme Human_UltraGray has no size field

  self.wTree = gtk.glade.XML('do.glade', 'mainWindow')
Traceback (most recent call last):
  File "./do.py", line 48, in addItems
    self.hardware = hardware.List()
  File "/home/doctormo/Projects/Py/do/hill/hardware.py", line 27, in __init__
  File "/home/mowens/Projects/do/hill/device.py", line 30, in __init__
  File "/home/mowens/Projects/do/hill/device.py", line 155, in __init__
  File "/home/mowens/Projects/do/hill/device.py", line 182, in set_type
AttributeError: Device instance has no attribute 'bus'
Nothing to edit
Nothing to edit
mark@ubuntu:~/Desktop/do$ ./do.py
./do.py:37: GtkWarning: Theme directory 96x96/action of theme Human_UltraGray has no size field

  self.wTree = gtk.glade.XML('do.glade', 'mainWindow')
Traceback (most recent call last):
  File "./do.py", line 48, in addItems
    self.hardware = hardware.List()
  File "/home/doctormo/Projects/Py/do/hill/hardware.py", line 27, in __init__
  File "/home/mowens/Projects/do/hill/device.py", line 30, in __init__
  File "/home/mowens/Projects/do/hill/device.py", line 155, in __init__
  File "/home/mowens/Projects/do/hill/device.py", line 182, in set_type
AttributeError: Device instance has no attribute 'bus'
Nothing to edit
Nothing to edit
Nothing to edit
Nothing to edit
mark@ubuntu:~/Desktop/do$



---

### Post by maniacmusician on 2006-09-14
i'm typing this while running the program. I don't notice an option for CD/DVD drive in the drop down for "Type". more thoughts about this; perhaps there should be an attempt at automated detection here...you can usually pick up what kind of drive it is from the text that Dohickey displays...you could just have it scan that for keywords. such as "CD-RW", "IDE-DVD" or "DROM", and have it classify automatically by doing that....the less user interaction, the better, probably, right? I'm not sure

for hard drives, same as I said above. Dohickey usually tells me that it's a hard drive. Also, I love the rps function when you select "Hard Drive" from the dropdown menu...classy hehe. Are you sure it is called rps? As far as I know, it's usually RPM. I have another hard drive, and the text that comes up shows the manufacturer, model, etc.

I have a wireless card too, and while the text shows the chipset and speed of the card, it doesn't show the manufacturer...well i'm not really sure that belkin manufactured it...but they definitely sold it to me.  I also have at the end, an "Unknown (0x5a3f)(pci:1002:5A3F)", i don't really know what that's all about. 

Overall, it's pretty damn good! well on its way. It remembered everything I entered in the fields when I stopped and restarted the script, so that's handy also. Suggestions: I would suggest that you add a few extra parameters that Dohickey would detect from the system, such as the date, the kernel version and distro...this will probably help people as they browse the database. That's pretty much all that's coming to mind right now. Off i go to put this up on the site.

---

### Post by maniacmusician on 2006-09-14
> **Polygon said:**
> is edit supposted to do anything in that program? cause it didnt do anything for me. quit worked though

here is my console output in case you want it, dont mind the gtk errors. its a problem with my icon theme and i get it with everything.
yo, i think you're using the wrong version. did you download the one from the site? Like I said, that's an older version. I'm gonna go put the new one up right now. For now, use the link that martin provided in his post. The edit works fine for me in that one...

In the old version, Edit didn't work on the first item (which would usually be the motherboard). so yeah, are you sure you're on the right version?

edit: [http://www.ubuntuforums.org/showthread.php?p=1500363](http://www.ubuntuforums.org/showthread.php?p=1500363),  and we're all updated at [http://dohickey.project.googlepages.com](http://dohickey.project.googlepages.com)

---

### Post by Polygon on 2006-09-14
dled the lastest version from the project site, and still nothing comes up and edit doesnt work (it says nothing to edit)

here is my console output: (again ignore gtkwarnings)

> mark@ubuntu:~$ cd /home/mark/Desktop/do
mark@ubuntu:~/Desktop/do$ ls
conf           do.glade   do.py  fields  images  tempory
documentation  do.gladep  esid   hill    mod
mark@ubuntu:~/Desktop/do$ ./do.py
./do.py:37: GtkWarning: Theme directory 96x96/action of theme Human_UltraGray has no size field

  self.wTree = gtk.glade.XML('do.glade', 'mainWindow')
Traceback (most recent call last):
  File "./do.py", line 48, in addItems
    self.hardware = hardware.List()
  File "/home/doctormo/Projects/Py/do/hill/hardware.py", line 27, in __init__
  File "/home/mowens/Projects/do/hill/device.py", line 30, in __init__
  File "/home/mowens/Projects/do/hill/device.py", line 155, in __init__
  File "/home/mowens/Projects/do/hill/device.py", line 182, in set_type
AttributeError: Device instance has no attribute 'bus'
Nothing to edit
Nothing to edit
Nothing to edit



---

### Post by maniacmusician on 2006-09-14
that's not too good. the expected output at the beginning is:

> Adding hardware pci:1106:3044:4371:4372:4373:4374:4375:4376:4377:4379:437A:437B:
5A33:5A61:8139
Adding hardware ide:48X12X50CDRW1.0120020904
Adding hardware ide:IDEDVDDROM6216
Adding hardware ide:ExcelStorTechnologyJ680
Adding hardware ide:SAMSUNGSP0802NR
Adding hardware pci:14E4:4320
Adding hardware pci:1002:5A3F


or something like that....basically saying that hardware was found. martin does all the programming, so i'm not too sure but it's looking like it's finding "errors" in the scrip, which could be because....well...hmm do you have all the dependencies installed? they're listed on the downloads page. 

-HAL  
-Gtk
-Gtk-python
-Python
-Linux

thats the only reason I can think of at the moment.

---

### Post by Polygon on 2006-09-14
i believe i have all of those installed, i checked hal, i know for a fact that gtk and gtk/python is installed...

---

### Post by maniacmusician on 2006-09-14
okay...i'm not really a programmer but i've been looking at your error

it seems like your gtk theme fails to provide a certain size specification that's needed here...are you using the default theme on ubuntu? if not you could try that. 

I also find it odd that paths that are on martin's computer are showing up in your errors. for instance, /home/doctormo is a directory on martins computer. oO

anyways those errors don't have anything to do with the new addition, I don't think, because that is "fields", and all the errors are in "hill" I dont really know what hill does. but i dont think it has anything to do with the new version. do you get the same errors with the older version in the archive? 

sry i cant be of more help. but do try changing your theme back to default (temporarily of course)

---

### Post by Polygon on 2006-09-14
thos gtkwarning errors are just my icon theme bugging out or something. I get it with basically everything, and it hasnt caused me any problems yety.

but i did switch back and tried it again, and same errors

---

### Post by maniacmusician on 2006-09-14
oh. 

sorry if it's too much hassle, but can you see if the older one works for you?

[http://dohickey.project.googlepages.com/archive](http://dohickey.project.googlepages.com/archive)

---

### Post by SoundMachine on 2006-09-14
Says incompatible pointer on a 64 bit system.

813 errors before that beceause while you added known good HW you knew perfectly well that all other stups would fail.

According to yoru script my v210 shouldn't even be capable of booting Limux.

This is a sad excuse to a HS relibility script that no on can or will ever rely on, i suggest you contact Patrick V or Linus T to get a thorough vadlidation, without it it iw simply worthless.

Not that i don't apprecie the effort, i just don't seee your script wothwhile.

At all.

---

### Post by maniacmusician on 2006-09-14
[shrug] no one has a great script out of the box. this is a baby project. you shouldnt be so quick to slam on it. 

thanks for your feedback, though, it'll be looked into.

---

### Post by SoundMachine on 2006-09-14
> **maniacmusician said:**
> [shrug] no one has a great script out of the box. this is a baby project. you shouldnt be so quick to slam on it. 

thanks for your feedback, though, it'll be looked into.

An Uvuntu HW project, using the same damn kernels as so many others.


What is the point and how ******* boring can you be?

---

### Post by SoundMachine on 2006-09-14
> **maniacmusician said:**
> [shrug] no one has a great script out of the box. this is a baby project. you shouldnt be so quick to slam on it. 

thanks for your feedback, though, it'll be looked into.


I did, that was the point.

I don't slam anyone, but i do think that rewriting the changelog is just daft.

---

### Post by maniacmusician on 2006-09-14
the point? 

the point is to create a database of hardware that is known to work or not work with linux so that users can make informed choices about what kind of hardware they should be looking to buy.

there's  no reliable source of information out there right now that has a large amount of data in it that's up to date. the point of this project is to create an easily updatable source of information that gives users information they need....what's wrong with a goal like that?

---

### Post by maniacmusician on 2006-09-14
> I did, that was the point.

I don't slam anyone, but i do think that rewriting the changelog is just daft

calm down...what're you making so much fuss about? you were just asked to try  it and give feedback. you did, and that's awesome. don't create a problem where there doesn't have to be one.

edit: i  need to go to bed. Oh and yes, I am a little daft. I get excited over little things too. I'm pretty obsessive compulsive as well. [shrug] ya take what you can get in this world. thanks for testing the script

---

### Post by SoundMachine on 2006-09-14
> **maniacmusician said:**
> calm down...what're you making so much fuss about? you were just asked to try  it and give feedback. you did, and that's awesome. don't create a problem where there doesn't have to be one.

Yeah, what am i making so much fuss about? De nada, i am not amking any fuss at all, i'm offering a viewpoint that you don't like everyone on the other side are "making a fuss" while everyone on yor side agree and are all "team players".


So yppie cay ey motherfucker.

---

### Post by Polygon on 2006-09-15
tried version .003 and i got similar results

> 
mark@ubuntu:~/Desktop/do$ ./do.py
./do.py:36: GtkWarning: Theme directory 96x96/action of theme Human_UltraGray has no size field

  self.wTree = gtk.glade.XML('do.glade', 'mainWindow')
Traceback (most recent call last):
  File "./do.py", line 47, in addItems
    self.hardware = hardware.List()
  File "/home/doctormo/Projects/Py/do/hill/hardware.py", line 27, in __init__
  File "/home/doctormo/Projects/Py/do/hill/device.py", line 30, in __init__
  File "/home/doctormo/Projects/Py/do/hill/device.py", line 155, in __init__
  File "/home/doctormo/Projects/Py/do/hill/device.py", line 182, in set_type
AttributeError: Device instance has no attribute 'bus'
Traceback (most recent call last):
  File "./do.py", line 163, in editSelection
    if self.selected:
AttributeError: HillManager instance has no attribute 'selected'
Traceback (most recent call last):
  File "./do.py", line 163, in editSelection
    if self.selected:
AttributeError: HillManager instance has no attribute 'selected'
Traceback (most recent call last):
  File "./do.py", line 163, in editSelection
    if self.selected:
AttributeError: HillManager instance has no attribute 'selected'
mark@ubuntu:~/Desktop/do$


---

### Post by DoctorMO on 2006-09-15
Thanks Polygon for your results, this is exactly the kind of thing we need (i.e errors) because the project has only been run on a few machines it's very likly to have bugs which are unforseen. i.e the reason I've asked you all to test it. (I'll get them fixed)

Thanks maniacmusician for updating the webpage, I was too jazzed up once I'd fixed a really damn anoyyed pointer bug.

SoundMachine can we keep this thread about feedback for the technicalities and constructive critism? I don't need this thread closed. besides the path of a thousand miles begins witha single step (followed by a thousand miles worth of steps). I'll try and figure out whats wrong with 64bit machines, although I don't think it's a big problem.

Hopefully I'll get the sourcefroge account set up soon and we can have bug tracking ect.

---

### Post by DoctorMO on 2006-09-15
OK what I've done is remove all the stupid pyc files, it's a python thing. this might be whats causing some of the issues as I see no reason why errors should come about on a 64bit machine any more than on a 32bit machine.

So here you will find it's been updated and should work a little better:

[http://divajutta.com/doctormo/do.tar.bz2](http://divajutta.com/doctormo/do.tar.bz2)

(could you update the website maniacmusician? I don't know how)

---

### Post by maniacmusician on 2006-09-15
since it's just a quick bug fix, do you want me to just make it 0.04-02? a whole number upgrade is not really warranted I dont think. just email, pm, or post back on here. it'll take only a few minutes to update the site.

---

### Post by maniacmusician on 2006-09-15
version 0.04.1 is on the site. it should run on 64bit machines now.

---

### Post by Polygon on 2006-09-16
same errors in the newest version that i got with all the other ones.

all im seeing is a blank window with "edit" and "quit" at the top.

---

### Post by DoctorMO on 2006-09-16
Polygon in the tempory directory you'll find a program called list.py if you run './list.py > poly-hal.list' and send it to me via email I can have a look to see what kind of devices you have that might be causing the issue. I thought it might be SCSI or SATA devices since it's not been tested on those.

---

### Post by Polygon on 2006-09-19
can i have your email address?

---

