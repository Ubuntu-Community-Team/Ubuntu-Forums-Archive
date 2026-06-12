---
title: "New cover designer, Try it!"
date: 2008-09-29
forum: Ubuntu Studio
---

### Post by Amazona aestiva on 2008-09-29
[CENTER][IMG]http://sourceforge.net/dbimage.php?id=189196[/IMG][/CENTER]


**[SIZE="5"]What's that?[/SIZE]**
Very shortly: It is a cover designer for homemade discs. [**[COLOR="DarkOrange"]Homepage[/COLOR]**]("http://discwrapper.sf.net")

Specify:
It was made with Code::Blocks and it uses the wxWidgets library. It has template covers. Depending on the case there are pages where you can place labels whether multi or single line, images with options like scaling and rotating, and create directory lists. It can export the design into an image file or print directly. It can lightscribe the disc design(see below). And last but not least, you can save your custom design as a project so that you don't have to remake it for each of your discs.

**[SIZE="5"]Introduction:[/SIZE]**
One day I wanted to print a simple cover to a disc of mine, but it spent an hour to do it in Gimp. I had looked for a cover designer application, but I could hardly find any and they weren't up to date and I couldn't even compile one because of a dependency problem. I decided to make a cover designer for home use.

It has template covers. Depending on the case there are pages where you can place labels, images, and directory lists. Now I can make a cover within a minute, so it has already achieved something. I definitely want to improve it in the (near) future, but I hardly have any freetime.
Future plans are:
- translate it to several languages(please, have a look at the Development section)
- add support to more cases
- make better cover templates(please, have a look at the Development section)
- and last but not least, fix the bugs reported and keep it up to date

**[SIZE="5"]Installation:[/SIZE]**
[B][[COLOR="DarkOrange"]Intrepid[/COLOR] users may want to install it from GetDeb.net.:)]("http://www.getdeb.net/app/DiscWrapper")
Otherwise you can compile the source:[/B]
**[SIZE="3"]First you have to get wxWidgets 2.8.8 or above:[/SIZE]**

**[COLOR="DarkOrange"]Intrepid users:[/COLOR]**
```
sudo apt-get install libwxbase2.8-0 libwxbase2.8-dev libwxgtk2.8-0 libwxgtk2.8-dev wx2.8-headers
```

**[COLOR="DarkOrange"]All the others:[/COLOR]**
_Open a terminal and do..._
Ubuntu:
```
sudo gedit /etc/apt/sources.list
```
Kubuntu:
```
sudo kate /etc/apt/sources.list
```
_append one of these lines depending on your distribution:_

**Hardy:**
```
deb http://apt.wxwidgets.org/ hardy-wx main
```
**Gutsy:**
```
deb http://apt.wxwidgets.org/ gutsy-wx main
```
**Feisty:**
```
deb http://apt.wxwidgets.org/ feisty-wx main
```
**Edgy:**
```
deb http://apt.wxwidgets.org/ edgy-wx main
```
**Dapper:**
```
deb http://apt.wxwidgets.org/ dapper-wx main
```


_Close the text editor and add the GPG Key:_
```
wget -q http://apt.wxwidgets.org/key.asc -O- | sudo apt-key add -
```

_Update your repository list:_
```
sudo apt-get update
```

_Install wxWidgets:_
```
sudo apt-get install libwxbase2.8-0 libwxbase2.8-dev libwxgtk2.8-0 libwxgtk2.8-dev wx2.8-headers
```

**[SIZE="3"]Install g++:[/SIZE]**
```
sudo apt-get install g++
```

**[SIZE="3"]Download and install DiscWrapper:[/SIZE]**
```
wget http://osdn.dl.sourceforge.net/sourceforge/discwrapper/discwrapper-1.1.5.tar.gz
tar -xzvf ~/discwrapper-1.1.5.tar.gz
cd ~/discwrapper-1.1.5
./configure
make
sudo make install
```

Now it is in Applications->Graphics :D

**[SIZE="3"]To be able to LightScribe:[/SIZE]**
It can use LaCie's LightScribe Labeler, but it's only available through rpm binary, so...
Get them into one directory. [Host Software]("http://www.lacie.com/download/drivers/lightscribe-1.8.15.1-linux-2.6-intel.rpm"), [Labeler]("http://www.lacie.com/download/drivers/4L-1.0-r6.i586.rpm")
Open terminal and cd to them.
Check and necessarily install alien:```
sudo apt-get install alien
```
Now make the deb packages:```
sudo alien ./4L-1.0-r6.i586.rpm
sudo alien ./lightscribe-1.8.15.1-linux-2.6-intel.rpm
```
And install them:```
sudo dpkg -i lightscribe-1.8.15.1-linux-2.6-intel.deb 4L-1.0-r6.i586.deb
```

Now when you click on Print while viewing the Disc, it will offer you to use this Labeler. Just to know: It will ask you for your password because It needs sudo to print on the disc.


**[SIZE="5"]Development:[/SIZE]**
**_Every help is appreciated very much!_**
Current issues:
- If you feel, you would like to make some cover templates, DO IT and contact me by e-mail or send a private message and I'll implant it.
- If you speak a language that it hasn't been translated to, feel free to do it, BUT contact me and I'll post you the current po translation file.


**[SIZE="4"][COLOR="DarkOrange"]Regards, Amazona aestiva[/COLOR][/SIZE]**

---

### Post by binbash on 2008-09-29
I am using inkscape for the covers.Can you post a screenshot of the application so we can see before the installation first?I would like to try it

---

### Post by Stochastic on 2008-09-30
> **binbash said:**
> Can you post a screenshot of the application so we can see before the installation first?

The SourceForge website Amazona aestiva provided has a couple screenshots.

---

### Post by binbash on 2008-09-30
sorry it is my fault.i see them now, i installed it and it is working fine here.

---

### Post by lisati on 2008-09-30
Looks promising.....
Got a bunch of warnings, mostly about converting between INT and DOUBLE when compiling (my terminal lost some of the output, otherwise I'd post), but it can be run.

---

### Post by Amazona aestiva on 2008-09-30
> **lisati said:**
> ...Got a bunch of warnings, mostly about converting between INT and DOUBLE when compiling...

That's not a problem, it gives lots of warnings, but they have no affect. :)

---

### Post by Amazona aestiva on 2008-10-02
See what it is going to be able to do!!!

It will also give the image directly to LaCie's LightScribe Labeller!

[IMG]http://sourceforge.net/dbimage.php?id=189196[/IMG]

My dream comes true! :D

---

### Post by Amazona aestiva on 2008-10-07
First stable release is out! check it [here]("https://sourceforge.net/projects/discwrapper/").

---

### Post by badrunner on 2008-10-08
> **Amazona aestiva said:**
> First stable release is out! check it [here]("https://sourceforge.net/projects/discwrapper/").

Looks really nice, ill get round to trying it out when 8.10 comes out and i setup a non production ubuntu box.

In the meantime, keep up the good work.

---

### Post by Amazona aestiva on 2008-10-09
> **badrunner said:**
> Looks really nice, ill get round to trying it out when 8.10 comes out and i setup a non production ubuntu box.

In the meantime, keep up the good work.

Thanks, that's my plan:)

---

### Post by Joe_Linux on 2008-10-12
Amazona aestiva

When I tried to cd command I got this 
joe52@joe52-desktop:~$ cd ~/discwrapper
bash: cd: /home/joe52/discwrapper: No such file or directory
joe52@joe52-desktop:~$ 
Thank you Joe_Linux

---

### Post by Amazona aestiva on 2008-10-13
> **Joe_Linux said:**
> Amazona aestiva

When I tried to cd command I got this 
joe52@joe52-desktop:~$ cd ~/discwrapper
bash: cd: /home/joe52/discwrapper: No such file or directory
joe52@joe52-desktop:~$ 
Thank you Joe_Linux

Thanks for pointing that out, I'll fix that.

Until then, do this:
```
wget http://downloads.sourceforge.net/discwrapper/discwrapper-1.0.0.tar.gz?modtime=1223414523&big_mirror=0
tar -xzvf ~/discwrapper-1.0.0.tar.gz
cd ~/discwrapper-1.0.0
./configure
make
sudo make install
```


Greetings,  Amazona aestiva

---

### Post by Joe_Linux on 2008-10-14
Amazona aestiva

Thank you for answering my other post, lightscribe will not let me print 
unless I am root I tried to change permissions but it did not work 
joe52@joe52-desktop:~$ chmod 700 4L-gui
chmod: cannot access `4L-gui': No such file or directory
joe52@joe52-desktop:~$ sudo chmod 700 4L-gui
chmod: cannot access `4L-gui': No such file or directory
joe52@joe52-desktop:~$ cd 4L-gui
bash: cd: 4L-gui: No such file or directory
joe52@joe52-desktop:~$ 

Any help would be appreciated thanks Joe_Linux

---

### Post by Amazona aestiva on 2008-10-14
> **Joe_Linux said:**
> Amazona aestiva

Thank you for answering my other post, lightscribe will not let me print 
unless I am root I tried to change permissions but it did not work 
joe52@joe52-desktop:~$ chmod 700 4L-gui
chmod: cannot access `4L-gui': No such file or directory
joe52@joe52-desktop:~$ sudo chmod 700 4L-gui
chmod: cannot access `4L-gui': No such file or directory
joe52@joe52-desktop:~$ cd 4L-gui
bash: cd: 4L-gui: No such file or directory
joe52@joe52-desktop:~$ 

Any help would be appreciated thanks Joe_Linux

You see DiscWrapper would ask for the password now if you have changed the permissions, because the default situation that it is needed.

I've not tried this yet, but it should fix the permission stuff:
```
sudo chmod 700 /usr/bin/4L-gui
```
I don't know if it is enough to chage the permissions of the link, so you might want to try this one too:
```
sudo chmod 700 /usr/4L/4L-gui
```

Regards, Amazona aestiva

---

### Post by Amazona aestiva on 2008-11-01
GetDeb.net has binary files for Intrepid Ibex users!!!

Check it out [here]("http://www.getdeb.net/app/DiscWrapper")

---

### Post by cotcot on 2008-11-01
Got it compile and installed as in the above description (on hardy amd64).
Opening the program, selecting "new" , clicking anyone of the 4 possibilities and then selecting anyone of the 2 layout options and OK gives an error message :  [COLOR="Blue"]This isn't a DiscWrapper project file, or it is corrupted[/COLOR].
I have not installed lightscribe. Is it necessary ?

---

### Post by Amazona aestiva on 2008-11-01
> **cotcot said:**
> Got it compile and installed as in the above description (on hardy amd64).
Opening the program, selecting "new" , clicking anyone of the 4 possibilities and then selecting anyone of the 2 layout options and OK gives an error message :  [COLOR="Blue"]This isn't a DiscWrapper project file, or it is corrupted[/COLOR].
I have not installed lightscribe. Is it necessary ?

That shouldn't have happened. Could you post me the log file? It's located $HOME/.discwrapper/discwrapper.log, but it's erased every time you run the app, so run it, try to load a cover, then post the file.

Btw, every of those cover designs are corrupted?

Lightscribe isn't necessary, it runs without it.

Thanks

EDIT:
You may also post a wrong cover design. They're /usr/local/share/discwrapper. Thanks again

---

### Post by cotcot on 2008-11-02
This is the content of the log file with discwrapper running giving the error message:
> > Starting up...
> Loading defaults
> Loading list of recent projects
> Ready to work

>>>> Creating dialog
>>>> Loading cases
>>>> Loading templates/projects........OK
> Loading selected template
> Opening project.

I get the error with all cover types.
I cannot add a design cover because it is not a valid file extension.

---

### Post by Amazona aestiva on 2008-11-02
> **cotcot said:**
> This is the content of the log file with discwrapper running giving the error message:


I get the error with all cover types.
I cannot add a design cover because it is not a valid file extension.

Create a zip or gz package of them, I have to see what's the problem with them, because it exits at the first checking.

Thanks

Btw: I've just tried that if you have wxWidgets 2.8.8 or above, the Intrepid package of getdeb will run fine, but you have to uninstall your current.

EDIT:
Or you could post md5 checksums. And if they mach I'll have an idea what the problem is.

---

### Post by cotcot on 2008-11-02
I uninstalled the compiled version and installed the getdeb package of intrepid instead (I have wxWidgets 2.8.9). I can open discwrapper without the error message now.

md5 checksum of the downloaded file for compilation is d41d8cd98f00b204e9800998ecf8427e

Are you still interested in the design cover of the compiled version ? (If so I need to remove discwrapper and compile the other version again and sent the design covers: no problem if it helps you)

---

### Post by Amazona aestiva on 2008-11-02
> **cotcot said:**
> I uninstalled the compiled version and installed the getdeb package of intrepid instead (I have wxWidgets 2.8.9). I can open discwrapper without the error message now.

md5 checksum of the downloaded file for compilation is d41d8cd98f00b204e9800998ecf8427e

Are you still interested in the design cover of the compiled version ? (If so I need to remove discwrapper and compile the other version again and sent the design covers: no problem if it helps you)

The md5 checksum of the original discwrapper-1.0.0.tar.gz: 153dd1ecb63b1e70b835f70aadb733f6

I suppose that was the problem. I wonder how could you compile it, anyway I hope it'll be useful.

Thanks & Regards

---

### Post by ranch hand on 2008-11-09
I do not get any error indication what so ever.  Every thing opens nicely.  Templates come up.  Can select one.  Seem to be able to set font and color.  Can rotate the "title" box.

There is a problem though when I try to type in the box.  Nothing happens.  Just what am I missing.

I am doing this under Hardy.
thanks

---

### Post by Amazona aestiva on 2008-11-10
> **ranch hand said:**
> I do not get any error indication what so ever.  Every thing opens nicely.  Templates come up.  Can select one.  Seem to be able to set font and color.  Can rotate the "title" box.

There is a problem though when I try to type in the box.  Nothing happens.  Just what am I missing.

I am doing this under Hardy.
thanks

See I couldn't have managed to solve the writing directly on the design. There is a text field on the left which contains the selected item's label. There you can modify it.

Regards

---

### Post by ranch hand on 2008-11-10
WELL.  I certainly know how to make myself fell like a weeny.

Maybe I should not try this stuff in the meddle of the night.

Thank you very much for answering such a question.

---

### Post by Amazona aestiva on 2008-11-17
Greetings Everybody!

Release 1.1.0 is out. [Check it out!]("http://sourceforge.net/projects/discwrapper/")

---

### Post by clasikowski on 2008-12-07
Hi!

Very nice program! Just what I was missing to get away from windows with label-printing; one of the last tasks my windows-installation has to do.

Some "wishes" I have: I would like to be able to enlarge images to up to 300%, the 250% is not enough for my needs - is it possible to have a larger ratio?

Another thing: I would like to print the CD-labels directly onto printable cd's with my Canon-PIXMA iP6000D - any suggestions how that could be accomplished?
Would it be possible to have an option just to make a cd-image without the case-inlays, and vice versa?

so long
clasikowski AKA hank

---

### Post by Amazona aestiva on 2008-12-07
> **clasikowski said:**
> I would like to be able to enlarge images to up to 300%, the 250% is not enough for my needs - is it possible to have a larger ratio?

I'll pay respect to your request.

> Another thing: I would like to print the CD-labels directly onto printable cd's with my Canon-PIXMA iP6000D - any suggestions how that could be accomplished?

Well that's the hard point, because I don't have a printer like that, so guess you have to wait until I borrow one at least. However one thing you may want to try: (I have no idea if it works or not)
After the disc design is ready, you can save it as an image file. (menu: File->Export)
If you figure out how to print that image on the disc, the problem's solved.

Btw: DiscWrapper might try to print that on the disc, but... you had better not try that.

> 
Would it be possible to have an option just to make a cd-image without the case-inlays, and vice versa?

This request will be considered as well.


Current development: very slooow, so don't wait for these very soon.

I'd like to thank you for your post, it means a lot to me.

Regards, Amazona aestiva

---

### Post by clasikowski on 2008-12-07
Hi!

Thanks for the quick answer. 

I will try and export the files; actually I hoped for a linux-programm to replace my Canon CD-LabelPrint-program, which doesn't run with wine...:wink:

Just another question regarding the preference window: What is the Default Class-thing supposed to do? I'll play around a bit, perhaps I'll find out, but right now  I haven't got a clue. :confused:

If your interested in a german translation, I could do one (well, at least for the features I've understood...;))

so long
clasikowski AKA hank

---

### Post by Amazona aestiva on 2008-12-08
Greetings,

> **clasikowski said:**
> I will try and export the files; actually I hoped for a linux-programm to replace my Canon CD-LabelPrint-program, which doesn't run with wine...:wink:

As I have said before I know nothing about printing on disc yet...

> Just another question regarding the preference window: What is the Default Class-thing supposed to do? I'll play around a bit, perhaps I'll find out, but right now  I haven't got a clue. :confused:

Well, labels within one class will have the same value after editing one of them. For example "<Title>" labels are in the same class. (if you know a word that fits better, let me know)

> If your interested in a german translation, I could do one (well, at least for the features I've understood...;))

Thanks that would be great... Could you send an e-mail to me, so I can save yours. (my e-mail can be found in the README file)

Regards, Amazona aestiva

---

### Post by halovivek on 2008-12-08
This is the first time i am coming across. thanks i will try and let you know.

---

### Post by clasikowski on 2008-12-08
Hi! 

> As I have said before I know nothing about printing on disc yet...
Never mind; I'll try with OpenOffice; there are supposed to be some templates in the net to print cds with the drawing program.

> Well, labels within one class will have the same value after editing one of them. For example "<Title>" labels are in the same class. (if you know a word that fits better, let me know)
Still beats me - If I put 5 labels in "class 2" and change the title of one of them, all other titles  will be changed, too? I hope not; I would like to save more than 5 labels/covers... Or are all titles within one "project" are changed, if I use the same "class" for the front, the inlay, the cd-label itself etc? But why would I need 5 classes? (I can't thing of another term yet, but I'm still not certain that I have understood that feature correctly...):???:

I found the address, I will be in touch soon!

so long
clasikowski AKA hank

---

### Post by Amazona aestiva on 2008-12-08
> **clasikowski said:**
> ...Still beats me - If I put 5 labels in "class 2" and change the title of one of them, all other titles  will be changed, too? I hope not; I would like to save more than 5 labels/covers... Or are all titles within one "project" are changed, if I use the same "class" for the front, the inlay, the cd-label itself etc? But why would I need 5 classes? (I can't thing of another term yet, but I'm still not certain that I have understood that feature correctly...)...

Huh... I don't know where to start, so I start it from the beginning:

Preferences dialog:
New labels will be set to the settings you have chosen here.

On the left panel: (when a label is selected)
If you change the class here it will only change the class of the selected label.
There is a class: None - If a label is set to this one, it won't have any connection to the others.
If a label is in class 1: - Every label, that are in class one, will be edited at once, on every page.
Class 2,3,4,5 works like that as well.

> But why would I need 5 classes?
You don't. This is an option that makes life easier. See, template projects have already been set to have <Title> and <Date> labels. If you want to create a cover you don't need to type the title of the disc more than once because they're in the same class. And therefore all will contain the same text, the one you want.

Regards, Amazona aestiva

---

### Post by clasikowski on 2008-12-10
Hi!

Ok, I think I got it now...

If I put a string, lets say the title, in "class 1", I can use the string on the front, the inside, and the cd, and change it in one go for the whole project... I can put the artist in "class 2", the date in "class 3".

Now I understand why 5 classes could be useful.:D

On the other hand I'll have to be careful to use "none" for entries I want to use only once; otherwise it would be changed without notice if I should have put it in "class 1" or any other previously used class by accident... 

I guess, in addition I was a little confused by the usage of the term 'label', which in this context seems to apply to one item only, but not the whole project. So perhaps 'element' would be more appropriate? (It's always difficult for non-native-speakers like us...)  

so long
clasikowski AKA hank

btw.: Which list formats are supported? And could you explain about the "Filter hidden" option in the preferences? thanks...

---

### Post by Amazona aestiva on 2008-12-10
> **clasikowski said:**
> ...Which list formats are supported? And could you explain about the "Filter hidden" option in the preferences?...

Hello,

Well the list tool is a bit... so it's rather underdeveloped.

Currently it can list the files and subdirectories in a directory.
Filter hidden option removes the hidden files and hidden directories.

This tool will have more options in the future.(Audio CD track listing for example)

Regards, Amazona aestiva

---

### Post by clasikowski on 2008-12-10
Hi!
> **Amazona aestiva said:**
> 
Well the list tool is a bit... so it's rather underdeveloped.

Currently it can list the files and subdirectories in a directory.
Filter hidden option removes the hidden files and hidden directories.

This tool will have more options in the future.(Audio CD track listing for example)


Well, I can't get it to work at all; neither do the options have any effect so far, nor am I able to open any files - all of them are grayed out, that's why I asked for supported formats (so far I couldn't find any...but it looks like I'm to plain stupid to understand that only the directory list will be included, but no single files...Ok, I got that one)


thanks anyway

so long
clasikowski AKA hank

---

### Post by Amazona aestiva on 2008-12-11
> **clasikowski said:**
> ...nor am I able to open any files - all of them are grayed out, that's why I asked for supported formats...

Hi!

You have to open a directory, which you want a list of. Example:

I have a directory: ./main
There are subdirs and files in it:
./main/subdir1
./main/subdir2
./main/.hiddenfile.x
./main/text.txt
./main/image.jpg

If you make a directory list of main with ticked List files only and Filter hidden it will look like:
main
text.txt
image.jpg

If you untick the List files only:
main
subdir1
subdir2
text.txt
image.jpg

And if untick the Filter hidden files too:
main
subdir1
subdir2
.hiddenfile.x
text.txt
image.jpg

So, overall it's a tool which creates a list about files on a cd.

Maybe the meaning of directory list is not clear?
In other words: This tool creates a catalog of files in a folder.

Regards, Amazona aestiva

---

### Post by clasikowski on 2008-12-11
Hi!

Thanks; I guess this makes it clear enough, even for me:
> In other words: This tool creates a catalog of files in a folder.

Would it be possible to include some kind of device to import playlists, .txt-files or anything like that?

so long
hank

---

### Post by Amazona aestiva on 2008-12-11
> **clasikowski said:**
> ...Would it be possible to include some kind of device to import playlists, .txt-files or anything like that?...

Hi!

The list tool is the most underdeveloped part of the application.

As I've said:
> This tool will have more options in the future.(Audio CD track listing for example)
It will also be capable of imorting text files and such things:) But there is no such option for the time being.

Regards, Amazona aestiva

---

### Post by Amazona aestiva on 2008-12-11
DiscWrapper 1.1.1 is out!

Re-release due to a serious bug. (1.1.1a)

---

### Post by cotcot on 2008-12-18
Installed 1.1.1a from getdeb in hardy 64 bit. I could use the version 1.0.0 after the some troubleshooting as mentioned in this thread. After upgrade to 1.1.1a it went wrong.
The program opens. Selecting a type of cover is possible but then no continuation is allowed. The OK-button remains grey shaded. No error messages in the program window when a new cover is started. An error message "This isn't a discwrapper project or file is corrupted" appears when I want to open an existing file (that I made with version 1.0.0).
I get this whe I start the program in terminal at the moment I selected a cover type :
> (discwrapper:7033): Gtk-WARNING **: /build/buildd/gtk+2.0-2.12.9/gtk/gtkwidget.c:8547: widget class `GtkPizza' has no property named `row-ending-details'

Googling on this gives  :
> >  GtkPizza is the name of a custom GTK widget that wxWidgets has implemented
> to help with things like wx.Panel, generic controls, etc. Apparently GTK
> 2.12 has added a new standard slot that wx isn't implementing yet.  It
> should be safe to ignore it for now as GTK should have an appropriate
> default for the property.

This is in the log-file :
> > Starting up...
> Loading defaults
> Loading list of recent projects
> Ready to work

>>>> Creating dialog
>>>> Loading cases
>>>> Loading templates/projects........OK

Regards

Cotcot

---

### Post by Amazona aestiva on 2008-12-19
> **cotcot said:**
> Installed 1.1.1a from getdeb in hardy 64 bit. I could use the version 1.0.0 after the some troubleshooting as mentioned in this thread. After upgrade to 1.1.1a it went wrong.
The program opens. Selecting a type of cover is possible but then no continuation is allowed. The OK-button remains grey shaded. No error messages in the program window when a new cover is started. An error message "This isn't a discwrapper project or file is corrupted" appears when I want to open an existing file (that I made with version 1.0.0).
I get this whe I start the program in terminal at the moment I selected a cover type :

Googling on this gives  :

This is in the log-file :


Regards

Cotcot

Greetings,

At first there is no DiscWrapper package on GetDeb for Hardy... this can cause the problem.

That button... well it must work as it is in the source: enable it when you click on a template... I don't really know what to say. Btw:You can open a template by a double click.

Could you post your wxWidgets version?

"This isn't a DiscWrapper project file, or it is corrupted.":
However 1.1.x can't open the 1.0.0 projects because a new string storage method has been applied that enables saving all the UTF-8 characters. Anyway IT should write that it is the wrong version. So something is terribly wrong there.

Remove your source code installation if any.

Summary: DiscWrapper doesn't have such errors by default... these errors are from external source(s) or depedenci(es) I suppose.

Regards, Amazona aestiva

---

### Post by cotcot on 2008-12-19
wxwidget version is 2.8.9.1

Uninstalled the getdeb (for intreprid) version

uninstalled from source code (1.0.0 and 1.1.1a)

reinstalled 1.1.1a from source code

Same errors (the pizza one and the "This isn't a DiscWrapper project file, or it is corrupted")
You are right the "OK" remained grey because I did not select a template. So double clicking on the template gives the "This isn't a DiscWrapper project file, or it is corrupted" error. But -if I understood you well - this error is not in the source code of discwrapper, so i must search somewhere else.

Thanks anyway for following up the posts.

---

### Post by Amazona aestiva on 2008-12-19
> **cotcot said:**
> wxwidget version is 2.8.9.1

Uninstalled the getdeb (for intreprid) version

uninstalled from source code (1.0.0 and 1.1.1a)

reinstalled 1.1.1a from source code

Same errors (the pizza one and the "This isn't a DiscWrapper project file, or it is corrupted")
You are right the "OK" remained grey because I did not select a template. So double clicking on the template gives the "This isn't a DiscWrapper project file, or it is corrupted" error. But -if I understood you well - this error is not in the source code of discwrapper, so i must search somewhere else.

Thanks anyway for following up the posts.

Gretings,

That error message is in the source, but for a 1.0.0 project it should show another one.

If the template projects can not be opened, I can only think that the source you have downloaded is corrupted. (this has already happened to someone here)

Here is a md5 checksum for you:
f6da165307dbcfff24411c85e4da51b8  discwrapper-1.1.1a.tar.gz

Regards, Nándor

EDIT: I don't get that "Pizza" error when opening a template, you may have some local settings that affect DiscWrapper.

---

### Post by BigSilly on 2008-12-19
I've just discovered DiscWrapper from this month's Linux Format magazine, and I've installed it from GetDeb. I'd just like to say a big thank you for this fantastic program. I've been after something like this on Linux for an absolute age. No errors so far for me using the GetDeb package, and I'm thrilled to bits with it!

Can we get this excellent program in the repositories? I think it would be a brilliant addition. My thanks again!

:guitar:

---

### Post by Amazona aestiva on 2008-12-19
> **BigSilly said:**
> I've just discovered DiscWrapper from this month's Linux Format magazine, and I've installed it from GetDeb. I'd just like to say a big thank you for this fantastic program. I've been after something like this on Linux for an absolute age. No errors so far for me using the GetDeb package, and I'm thrilled to bits with it!

Can we get this excellent program in the repositories? I think it would be a brilliant addition. My thanks again!

:guitar:

Thank you very much! :)

Maybe it will get in the repo, but there are still some issues to be fixed.

---

### Post by cotcot on 2008-12-20
> **Amazona aestiva said:**
> 
That error message is in the source, but for a 1.0.0 project it should show another one.

If the template projects can not be opened, I can only think that the source you have downloaded is corrupted. (this has already happened to someone here)

Here is a md5 checksum for you:
f6da165307dbcfff24411c85e4da51b8  discwrapper-1.1.1a.tar.gz

Regards, Nándor

EDIT: I don't get that "Pizza" error when opening a template, you may have some local settings that affect DiscWrapper.

The error quote is from 1.1.1a.
The checksum is OK.
The compilation from source on my other desktop (intrepid, 32 bit, wxwidgets 2.8.8.0) works OK.
The Pizza-stuff is a GTK issue (nothing to do with your app). From what I see on google it is a message that can just be neglected. It does not stop the app from working.

---

### Post by Amazona aestiva on 2009-01-12
Version 1.1.2 released :)

---

### Post by Sabayon on 2009-01-12
looks nice

---

### Post by clasikowski on 2009-01-12
Hi!

Works nice, too!
(only setback - my old projects are useless... - any way to make the new version open older files?)

Would be nice if everyone using the disc-printing could submit the right settings along with the printer model, so the settings can be usable for all. 

I asked users to submit their's in the german ubuntuusers-wiki [http://wiki.ubuntuusers.de/DiscWrapper]("http://wiki.ubuntuusers.de/DiscWrapper"); my Canon PIXMA ip6000D works perfectly with (-43;-257); that's just another task I don't need to use windows anymore!:guitar:

so long
Clasikowski AKA hank

---

### Post by Amazona aestiva on 2009-01-14
> **clasikowski said:**
> Hi!

Works nice, too!
(only setback - my old projects are useless... - any way to make the new version open older files?)

Would be nice if everyone using the disc-printing could submit the right settings along with the printer model, so the settings can be usable for all. 

I asked users to submit their's in the german ubuntuusers-wiki [http://wiki.ubuntuusers.de/DiscWrapper]("http://wiki.ubuntuusers.de/DiscWrapper"); my Canon PIXMA ip6000D works perfectly with (-43;-257); that's just another task I don't need to use windows anymore!:guitar:

so long
Clasikowski AKA hank

Greetings,

Approximately the 30% of the source has been rewritten last week, and I can't keep project compatiblity with such huge modifications. I suppose/hope the final project file format will be ready in May.

One more fact: However the version of DiscWrapper is above 1.0, but that's only because the original goals have already been achieved. It doesn't really mean ready or complete.

Thanks!

Regards, Amazona

---

### Post by Amazona aestiva on 2009-01-17
1.1.3 released

---

### Post by clasikowski on 2009-03-05
Hi!

Works good so far!

Just one thing: It would be nice if the inner circle for the cd-printing could be adjusted. Some printers don't crop it to the usable size, and print onto the transparent plastic (produces ugly smears on the disc); others do crop to a certain size, but in the print preview you can't see what will actually be printed onto the disc...

A (rather clumsy) work-around is to produce a small fitting white circle with Gimp (or whatever) and place it in the middle of the cd-view. 

Any possibility to include adjusting the inner circle?

so lonk
clasikowski AKA hank

---

### Post by Amazona aestiva on 2009-03-05
> **clasikowski said:**
> Hi!

Works good so far!

Just one thing: It would be nice if the inner circle for the cd-printing could be adjusted. Some printers don't crop it to the usable size, and print onto the transparent plastic (produces ugly smears on the disc); others do crop to a certain size, but in the print preview you can't see what will actually be printed onto the disc...

A (rather clumsy) work-around is to produce a small fitting white circle with Gimp (or whatever) and place it in the middle of the cd-view. 

Any possibility to include adjusting the inner circle?

so lonk
clasikowski AKA hank

Greetings,

Thank you for reporting that issue. I'll put it on my todo list. :)

There was a rather long break in the project's life, but I'll get down to work shortly.

Regards, Amazona aestiva

---

### Post by Amazona aestiva on 2009-03-05
As I promised this morning, here is the  1.1.4  with the following changes:
- PrintDiscDialog.cpp: Disc-surface scaling option
- Disc printing support for "hp Photosmart D5460"
- New translations: Swedish, Spanish
- Updated translation: Danish

---

### Post by Stochastic on 2009-03-05
Amonia, could you please move this project to its own webpage?  Sourceforge would be happy to host it.  It's just continuing on much longer than any one-time announce that would be appropriate in a help fourm such as this.  It'd also be nice to get this project into the repositories for 9.10 - pm me to discuss what that would take.

---

### Post by Amazona aestiva on 2009-03-06
Project homepage ready :) (link in first post)
See news there afterwards

---

### Post by clasikowski on 2009-03-20
Hi!

Great, no more smears on discs and WYSIWYG in print previews! (496 pixel for 'surface' in the cd print dialog works just fine for me!) 

Thank you!

(and if you're interested in an update for the german translation, just drop me a line...rsp. send the po-file...)

so long
clasikowski AKA hank

---

### Post by mjitkop on 2009-03-25
Hello.
Great program!

I am French and wondering if you would want it to be available in French too. On my spare time I could work on translating the interface to French. 

If you are interested, please let me know how I can help.

Keep up the good work! :)

---

### Post by VitalBodies on 2009-04-03
I created a template for GIMP for making a Ubuntu CD/DVD cover and wondered if that could help you or others in some way. 
[http://www.vitalbodies.net/site/open-source.html]("http://www.vitalbodies.net/site/open-source.html")
There is a link to the Ubuntu font, a downloadable cover in GIMPs native format and a link to a blog post I did on getting LightScribe to work. 

[CENTER][IMG]http://www.vitalbodies.net/site/images/uploads/ubuntu_disk.jpg[/IMG][/CENTER]

Note that this image does not look as nice or as interesting as the disk does when held in the hand as light plays upon the disk when your holding it and moving it.

Your program looks amazing I can not wait to try it!

---

### Post by VitalBodies on 2009-04-04
I added a link to your software from my site also. Thanks again...

---

### Post by VitalBodies on 2009-04-04
Was playing around with ideas for a graphic for you. Made this...

[CENTER][IMG]http://vitalbodies.net/site/images/uploads/DiscWrapper_logo_0.png[/IMG]

...and this header

[IMG]http://vitalbodies.net/site/images/uploads/DiscWrapper_header_0.png[/IMG]

...and this ad

[IMG]http://vitalbodies.net/site/images/uploads/DiscWrapper_ad_0.png[/IMG]

...and this button

[IMG]http://vitalbodies.net/site/images/uploads/DiscWrapper_button_2.png[/IMG][/CENTER]

I wanted to create something that told everyone that had never heard of your software what it is and what it is for and where to find it. 
Since the software is new, it is likely most people have never heard it. I thought this graphic might give them the idea right away. 
Comments from any and all are fun and welcome...

---

### Post by Amazona aestiva on 2009-04-04
Thank you very much for your contribution to my project. :D

I'll definitely upload the header to the project's website, and I'd really like to use the others, but I have no idea yet where and how.

Any idea or suggestion is welcome. :)

Many thanks :D

---

### Post by VitalBodies on 2009-04-04
> **Amazona aestiva said:**
> Thank you very much for your contribution to my project. :D

I'll definitely upload the header to the project's website, and I'd really like to use the others, but I have no idea yet where and how.

Any idea or suggestion is welcome. :)

Many thanks :D

Exciting, I am glad you like them! 
Last night after turning off my computer I had two more ideas. 
Which do you like best? 

[CENTER]
[IMG]http://www.vitalbodies.net/site/images/uploads/DiscWrapper_button_0.png[/IMG]


[IMG]http://www.vitalbodies.net/site/images/uploads/DiscWrapper_button_1.png[/IMG]


[IMG]http://www.vitalbodies.net/site/images/uploads/DiscWrapper_button_2.png[/IMG][/CENTER]

The difference is the words:
Make Cover
Cover Maker
Make Covers

---

### Post by Amazona aestiva on 2009-04-04
I suppose the third would be the best. It sound better than the first one and it is a command therefore it catches your attention :D

Would you be so kind to remake the ones in your pervious post with the text "MAKE COVERS"?

Thank you in advance

---

### Post by VitalBodies on 2009-04-04
I uploaded the files and they will show up in the post above if you do a hard refresh (shift refresh). 


...and added this header

[CENTER][IMG]http://vitalbodies.net/site/images/uploads/DiscWrapper_header_1.png[/IMG][/CENTER]

---

### Post by VitalBodies on 2009-04-04
[CENTER][IMG]http://vitalbodies.net/site/images/uploads/DiscWrapper_logo_1.png[/IMG]

[IMG]http://vitalbodies.net/site/images/uploads/DiscWrapper_logo_2.png[/IMG]

: )[/CENTER]

---

### Post by VitalBodies on 2009-04-04
I made an ad, and enough graphics that, so even if you do not advertise much you can place them on your site so others can download them and advertise for you. This allows many site owners to have something cool looking to place on their sites to promote your open source software. I suggest you make a page for the ones you think they should use and invite them to use the graphics. I added these blanks that you can add your own slogan (or whatever) to. 
[CENTER]
[IMG]http://vitalbodies.net/site/images/uploads/DiscWrapper_ad_1.png[/IMG]



[IMG]http://vitalbodies.net/site/images/uploads/DiscWrapper_skyscraper_1.png[/IMG][/CENTER]

---

### Post by VitalBodies on 2009-04-04
All 8 on the same page... 


[CENTER]
**Logo: **

[IMG]http://vitalbodies.net/site/images/uploads/DiscWrapper_logo_1.png[/IMG]


[IMG]http://vitalbodies.net/site/images/uploads/DiscWrapper_logo_2.png[/IMG]

**Header: **

[IMG]http://vitalbodies.net/site/images/uploads/DiscWrapper_header_0.png[/IMG]


[IMG]http://vitalbodies.net/site/images/uploads/DiscWrapper_header_1.png[/IMG]

[B]
Banner Ad:[/B]

[IMG]http://vitalbodies.net/site/images/uploads/DiscWrapper_ad_0.png[/IMG]


[IMG]http://vitalbodies.net/site/images/uploads/DiscWrapper_ad_1.png[/IMG]

**Button: **

[IMG]http://vitalbodies.net/site/images/uploads/DiscWrapper_button_2.png[/IMG]

**Skyscraper:** 

[IMG]http://vitalbodies.net/site/images/uploads/DiscWrapper_skyscraper_1.png[/IMG][/CENTER]

---

### Post by Maybelline on 2009-04-29
For posterity, I think I have found the settings for printing onto CD Stomper labels.

My labels are CD Stomper brand, matte white labels.  There are 2 full-size discs on each sheet.  The sheet says "Use Template CD Stomper 2-up Standard with Center Labels".

Anyway, I found these settings work pretty well:

Horizontal: -440 pixels
Vertical:    800 pixels
Surface:     612 pixels

This prints all the way to the center hole.  Hope someone finds this helpful.

Oh, obviously, you'll have to print twice per sheet.

---

### Post by phead on 2009-05-05
Interesting, I installed on jaunty using an alternative repository from here:

[http://aspn.activestate.com/ASPN/Mail/Message/wxpython-users/3712761](http://aspn.activestate.com/ASPN/Mail/Message/wxpython-users/3712761)

it printed fine on an epson R200 direct to a printable cd.

Can I add my voice to the request to be able to alter the sizes on the cd/dvd label to cope with full face printable disks, both for inner diameter and outer closer to edge.

cheers

---

### Post by Amazona aestiva on 2009-05-05
> **phead said:**
> Interesting, I installed on jaunty using an alternative repository from here:

[http://aspn.activestate.com/ASPN/Mail/Message/wxpython-users/3712761](http://aspn.activestate.com/ASPN/Mail/Message/wxpython-users/3712761)

it printed fine on an epson R200 direct to a printable cd.

Can I add my voice to the request to be able to alter the sizes on the cd/dvd label to cope with full face printable disks, both for inner diameter and outer closer to edge.

cheers

I'm glad it worked for you, but that disc size altering function has already been built in in release 1.1.4. There is a value on the "Disc Printing" dialog called surface.

Haven't you noticed it, or it doesn't work for you?

If you would be so kind to explain your issue a bit more, I would be very grateful.

Thanks,
Nándor

---

### Post by phead on 2009-05-07
> **Amazona aestiva said:**
> I'm glad it worked for you, but that disc size altering function has already been built in in release 1.1.4. There is a value on the "Disc Printing" dialog called surface.

Haven't you noticed it, or it doesn't work for you?

If you would be so kind to explain your issue a bit more, I would be very grateful.

Thanks,
Nándor

Sorry, I misunderstood what that option was for.  After a bit of fiddling, and some wasted cd's, I found the cups ppd was not quite right, so reimported a new one.  After that a new cd hub and size option appeared in the printer options, so everythings fixed!

cheers

---

### Post by dido__15 on 2009-06-02
> **Amazona aestiva said:**
> As I promised this morning, here is the  1.1.4  with the following changes:
- PrintDiscDialog.cpp: Disc-surface scaling option
- Disc printing support for "hp Photosmart D5460"
- New translations: Swedish, Spanish
- Updated translation: Danish
Amazonia,

First off the program is fantastic, by far the easiest to use I have seen. However I am having trouble actually printing the labels once created. I have a HP Photosmart D5460 printer and when I choose to print the printer itsef says "CD/DVD tray is open. Close tray to continue printing". I have tried changing the settings under Ubuntu Printing to tell the printer to print straight to CD but it still will not allow me to print to anything but paper. Did you come accross this in your testing, and do you have any ideas how to bypass this problem?

Many Thanks,

Dido

---

### Post by Amazona aestiva on 2009-06-03
> **dido__15 said:**
> Amazonia,

First off the program is fantastic, by far the easiest to use I have seen. However I am having trouble actually printing the labels once created. I have a HP Photosmart D5460 printer and when I choose to print the printer itsef says "CD/DVD tray is open. Close tray to continue printing". I have tried changing the settings under Ubuntu Printing to tell the printer to print straight to CD but it still will not allow me to print to anything but paper. Did you come accross this in your testing, and do you have any ideas how to bypass this problem?

Many Thanks,

Dido

Hi,

I do not have a printer which is capable of printing on discs. The disc printing support was developed by help through e-mail. It was tested with a Canon PIXMA ip6000D. Other printers are not tested in any ways... they said to be working and that's all...

However! I know someone who had some problem with that printer and could solve it. I spoke with him/her in the Help forum of DiscWrapper on SF.net. ([link to topic]("http://sourceforge.net/forum/forum.php?thread_id=3086263&forum_id=867137"))
From there you can go to fictionx's SF page and send him/her an e-mail asking for help. ;)

Regards,
Nándor

---

### Post by clasikowski on 2009-09-10
Hi!
:popcorn:
Good news for turboprint-users! I just tested the TurboPrint-printer-driver ([www.turboprint.de](www.turboprint.de)) version 2.11-2, and with it the CD printing in DiscWrapper has become much easier! The position of the print doesn't need to be adjusted painfully, and with lots of misprints, the standard centered setting with no offset at all works just fine! 

I was even able reduce the non-printable area in the middle of the disc to the exact edge of the printable surface, which I couldn't achieve with the old version.... (with the above-mentiond Canon PIXMA iP6000D used for testing...))
:guitar:


so long
clasikowski AKA hank

---

### Post by Amazona aestiva on 2009-09-10
Thank you for the great news :)

---

### Post by Ryazanov on 2009-10-20
Installed on ubuntu 9.04
Works perfect! I like it! Simple and powerful.
Thanks a lot! :D

---

### Post by clasikowski on 2009-11-02
Hi!

DiscWrapper work with 9.10 (tested on an standard-32-bit installation) That's the good news.:D

The bad news: Printing CDs is getting cumbersome again, even using turboprint.:(

wxprint uses the default printer; and in the setting-window no other printer is selectable (at least in my case; this was different with ubuntu 9.04, there a different printer setting window/modul was used). Regardless of how many printers I have configured only the one defined as default is shown, and used. So to print cds first I have to change the default printer.

The wxprint setting window offers a huge amount of paper sizes; but no CD format (or I am too blind to find it...). So the CD print layout has to be changed again to fit the actual printout; same procedures as before without turboprint and with testing testing testing until the right position is found.

Is it possible that the wx-packages new to the ubuntu repos (they were added for karmic) are different to the ones from the developer-ppa ([http://apt.wxwidgets.org/dists/](http://apt.wxwidgets.org/dists/)) I used in 9.04?

I'd call that a regression...:cry:

so long
hank AKA clasikowski

---

### Post by Rorohiko on 2010-01-24
Hello Amazona aestiva!:D

First of all: Thank you for your programm, it is a great pice of programm!

And as usual when someone works the first time with a programm, he has one or two wishes or ideas for the programm to make it more comfortable. My one are:

1 - I work with two computers, the one is connected to a 22" monitor and the other is conneted with the lightscribe device. So I would like to design the labels on the computer with the big monitor, save the work with *DiscWrapper* on this one, copy it to the other computer, start *DiscWrapper* there and burn the label. This doesn't work, because when *DiscWrapper* opens the file, it shows the error message, that the graphics I included are not on the place as expected, which is right. So it deletes everything on this label. My idea is instead of only showing the error message, to show the directory as well, so that the user can choose were the graphic is now on this computer.

2 - I made it possible for the 'username' to use 4L-gui without putting in the root-password by:
> # User alias specification
User_Alias LIGHTSCRIBE = username

# Cmnd alias specification
Cmnd_Alias LACIE_4L = /usr/bin/4L-gui

# User privilege specification
LIGHTSCRIBE ALL = NOPASSWD: LACIE_4L
This works very fine if I start *4L-gui* from the terminal, but not if I start it with the print command from *DiscWrapper*. Why is it? Is it a routine from *DiscWrapper* which ask for it?

Thank you for your answer in advance!

Rorohiko

---

### Post by Amazona aestiva on 2010-01-25
You are welcome :) I'm glad DiscWrapper is helpful to you.

I sent a private message with aswers.

---

### Post by phead on 2010-03-23
Just installed on a new lucid B1 install, install went fine using the 1.22 release but as clasikowski said above something has gone wrong with the printer dialog in this new version. 

In the old one you selected the printer, choose 5" cd, print and thats it.  The new one seems to always have the wrong printer selected, and I cannot find the CD label sizes in the list.

I'll bounce back to 115 and see if that fixes it.

---

### Post by Amazona aestiva on 2010-03-24
Hi All!

Been very busy lately, but I'll have a look at this printing issue for Lucid. Not sure though if I can fix it. If the problem is that wxWidgets' sources have not yet been updated to use the new printing system properly I won't be able to do much.

Anyway, Spring is here :) yay!

---

### Post by BigSilly on 2010-03-25
Where can I safely download a .deb of this for Ubuntu 9.10 64 bit? Many thanks. :)

---

### Post by Amazona aestiva on 2010-03-26
Hi!

Well, the last release was a long time ago so this package was built for Hardy(I think) at GetDeb.net. I'm not sure if it works on 9.10, but this is your best chance to get it working.

[Legacy GetDeb]("http://old.getdeb.net/") site is now offline, so I attached it.
If you experiance DiscWrapper crash or something like that, you will need to build it from source.

---

### Post by BigSilly on 2010-03-26
That's excellent, thanks very much. Installed no problem after picking up it's dependencies, and is seemingly working just fine. :)  Brilliant app this. Hope to see it on Lucid. Good luck.

---

### Post by VeeDubb on 2010-04-06
I'm having an all together different printing problem.

Running the latest beta of lucid with all available updates, discwrapper appears to be working great, except that when I go to print a cover, the page prints out all in black.  And when I say the whole page, I mean the whole page.  Edge to edge.  Nothing but a giant black sheet.  It comes out looking like black paper.

What's worse, is that the all black it's using is coming from the "photoblack" cartridge in my printer.  I wasted about $35 worth of photoblack ink trying to figure this out today.

I know the problem must be related to discwrapper and not my printer, because every single thing I've tried to print for a variety of other apps today has printed just fine.  It's only discwrapper that is doing this.  Also, discwrapper was working fine just a few weeks ago.

I sincerely hope that this is fixable, because this program is INCREDIBLY valuable to me.  I have yet to find a single program anywhere that can do what this program does.  The closest I've come is using a combination of gimp, LaCie and OpenOffice, which takes 10 times as long, and only produces results that are half as nice.

---

### Post by VeeDubb on 2010-04-06
If the extra info helps, I'm using an HP Photosmart Premium with the HPLIP driver.

Also, I was able to print to a pdf from the cups pdf driver package, and then print that PDF without errors, so it's only direct printing that has a problem.

---

