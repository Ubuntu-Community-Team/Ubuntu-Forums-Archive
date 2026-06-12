---
title: "Testers and Ideas needed for my first linux app :D"
date: 2005-06-26
forum: The Cafe
---

### Post by sapo on 2005-06-26
[SIZE=4]Features and Problems:[/SIZE]

The main problem is that: **You will LOSE the id3tags on the new files**, but i m already working on it  :grin: 

if you want to add tags after encoding you can use the easytag:
[http://easytag.sourceforge.net/screenshots-gtk2.htm](http://easytag.sourceforge.net/screenshots-gtk2.htm)

```

sudo apt-get install easytag

```

The app worked perfectly in my tests, and now you can chose the folder to save the files to.. if you dont chose one, a converted_files folder will be created inside the source folder!


[SIZE=4]Goals for the app:[/SIZE]

1 - Be able to convert mp3, ogg, mpc and maybe flac (i think i ll not make support to wma)
2 - Copy the id3 tag to the new files
3 - The user will be able to select each files from the folder that will be converted, it just converts everything now.. but i want to make possible to select the files
4 - I want to make a Preferences menu that will store all the users preferences. This preferences will have a lot of lame and oggenc features, so the user can customize without using the terminal.
5 - i want to keep it as simple as possible  :grin: 


[SIZE=4]Download and try it out:[/SIZE]

[http://xgn.no-ip.org:1000/downloads/converter.py](http://xgn.no-ip.org:1000/downloads/converter.py)

Just download this file and run with: python converter.py or chmod +x converter.py and the ./converter.py

[SIZE=4]Dependencies:[/SIZE]

The script depends on: wxpython >= 2.5.2, lame and vorbis-tools
```

sudo apt-get install wxpython lame vorbis-tools 

```

this should do the trick ;)

[SIZE=4]Screenshot:[/SIZE]

Version 0.0.2:
[IMG]http://img216.echo.cx/img216/4572/converter0022uu.jpg[/IMG]

[SIZE=4]Please send me some feedback:[/SIZE]

If someone have ideas i ll try to make a TODO list with using this topic as a base.. so.. post your ideas for improvement please!

thanx for anyone that can test it, and please post a feedback and ideas to improve it!

I ve decided to do it cause i was browsing the Breezy goals last week and i saw this stuff:

[http://udu.wiki.ubuntu.com/CommandLineDisintegration?highlight=%28DistroSpec%29](http://udu.wiki.ubuntu.com/CommandLineDisintegration?highlight=%28DistroSpec%29)

specially this part:

> SebastienBacher wants to convert his .ogg files to .mp3 files, since his MP3 player refuses to play .ogg files - somebody told him to use the "terminal" for it.

So i think.. i could try to help  :grin: 

And here somple people looking for it:
[http://ubuntuforums.org/showthread.php?t=44076&highlight=convert+ogg+mp3](http://ubuntuforums.org/showthread.php?t=44076&highlight=convert+ogg+mp3)
[http://ubuntuforums.org/showthread.php?t=38903&highlight=convert+ogg+mp3](http://ubuntuforums.org/showthread.php?t=38903&highlight=convert+ogg+mp3)

And they all end in the command line  :roll:

---

### Post by UbuWu on 2005-06-26
Nice idea, but somebody else has already done it: SoundConverter: [http://soundconverter.berlios.de/](http://soundconverter.berlios.de/)

---

### Post by az on 2005-06-26
I think they both seem nice.  Which one is faster?

---

### Post by allforcarrie on 2005-06-26
Kind of like this sweet program? [http://www.dbpoweramp.com/dmc.htm]("http://www.dbpoweramp.com/dmc.htm")

---

### Post by sapo on 2005-06-26
[QUOTE=UbuWu]Nice idea, but somebody else has already done it: SoundConverter: [http://soundconverter.berlios.de/](http://soundconverter.berlios.de/)[/QUOTE]

2 months ago i had to convert my files with a script cause i didnt found any app to do it.. ](*,) 

and i didnt know this one.. i ll give it a try.

btw i ve added some features to my script:

[http://xgn.no-ip.org:1000/downloads/converter.py](http://xgn.no-ip.org:1000/downloads/converter.py)

i ll take a look at this sound converter to see what it is about.. if its good i think i can start another more usefull thing  :roll:

edit: this didnt worked:
```

Traceback (most recent call last):
  File "./soundconverter.py", line 1352, in on_convert_button_clicked
    self.converter.add(fields["META"])
  File "./soundconverter.py", line 1226, in add
    c.set_mp3_quality(self.window.prefs.get_int(quality[mode]))
KeyError: 2

```

and it cant convert to mp3  :?

---

### Post by UbuWu on 2005-06-26
[QUOTE=sapo]
and i didnt know this one.. i ll give it a try.
[/QUOTE]

I decided to give your program a try as well  :)  But I get the following error:

```
Traceback (most recent call last):
  File "converter.py", line 331, in ?
    app = MyApp(0)
  File "/usr/lib/python2.4/site-packages/wxPython/wx.py", line 1951, in __init__    _wxStart(self.OnInit)
  File "converter.py", line 324, in OnInit
    frame = main_frame(NULL, -1, "Music Converter")
  File "converter.py", line 28, in __init__
    self.__do_layout()
  File "converter.py", line 77, in __do_layout
    grid_sizer_2.Add(self.text_input, 0, wxEXPAND|wxFIXED_MINSIZE, 0)
NameError: global name 'wxFIXED_MINSIZE' is not defined

```

---

### Post by UbuWu on 2005-06-26
[QUOTE=sapo]
and it cant convert to mp3  :?[/QUOTE]

Looks like gstreamer-lame which is neede for that isn't in the Ubuntu repositories, while lame itself is there...  :???:

---

### Post by UbuWu on 2005-06-26
[QUOTE=sapo]
i ll take a look at this sound converter to see what it is about.. if its good i think i can start another more usefull thing  :roll:

edit: this didnt worked:
```

Traceback (most recent call last):
  File "./soundconverter.py", line 1352, in on_convert_button_clicked
    self.converter.add(fields["META"])
  File "./soundconverter.py", line 1226, in add
    c.set_mp3_quality(self.window.prefs.get_int(quality[mode]))
KeyError: 2

```
[/QUOTE]

I got the same error... (had it installed for a while, thought it looked nice, just hadn't used it yet...)
And I don't know if it preserves the tags...?

---

### Post by UbuWu on 2005-06-26
[QUOTE=allforcarrie]Kind of like this sweet program? [http://www.dbpoweramp.com/dmc.htm]("http://www.dbpoweramp.com/dmc.htm")[/QUOTE]

I think that is a bit of an overkill... I like clean and simple apps. And it is not for linux.

---

### Post by sapo on 2005-06-26
[QUOTE=UbuWu]I decided to give your program a try as well  :)  But I get the following error:

```
Traceback (most recent call last):
  File "converter.py", line 331, in ?
    app = MyApp(0)
  File "/usr/lib/python2.4/site-packages/wxPython/wx.py", line 1951, in __init__    _wxStart(self.OnInit)
  File "converter.py", line 324, in OnInit
    frame = main_frame(NULL, -1, "Music Converter")
  File "converter.py", line 28, in __init__
    self.__do_layout()
  File "converter.py", line 77, in __do_layout
    grid_sizer_2.Add(self.text_input, 0, wxEXPAND|wxFIXED_MINSIZE, 0)
NameError: global name 'wxFIXED_MINSIZE' is not defined

```[/QUOTE]

man.. you are not the first one to get this error.. i m wondering why some people get this error and some do not  ](*,) 

wxFIXED_MINSIZE is a wxPython default stuff...  :-? 

i ll try to fix it out

I think you will have to update your wxPython

i found this in google:

> 
Found the reason why wx-2.5.2 gui was messed: starting with
wx-2.5.2, a new flag must be added when adding components to
sizers to keep the old behaviour (wxFIXED_MINSIZE).


could you post your wxPython version? just use:

apt-cache showpkg wxpython

it should return something higher than 2.5.2

---

### Post by UbuWu on 2005-06-26
[QUOTE=sapo]

could you post your wxPython version? just use:

apt-cache showpkg wxpython

it should return something higher than 2.5.2[/QUOTE]

Maybe that's the problem: it looks like I don't have wxpython installed. It isn't even in the breezy repositories  :?: ... (I thought libwxgtkpython was what was needed as that was the only thing I could find with both wx and python in it's name...  :mad: )

I will try it later in my hoary install.

---

### Post by sapo on 2005-06-26
[QUOTE=UbuWu]Maybe that's the problem: it looks like I don't have wxpython installed. It isn't even in the breezy repositories  :?: ... (I thought libwxgtkpython was what was needed as that was the only thing I could find with both wx and python in it's name...  :mad: )

I will try it later in my hoary install.[/QUOTE]

wxpython2.5.3.2ubuntu4 is in the hoary repository.. i ll try to find out if its in universe, multiverse or main... and try to find a link for you..

---

### Post by UbuWu on 2005-06-26
I know, but it is not in the breezy repositories.

---

### Post by sapo on 2005-06-26
[QUOTE=UbuWu]I know, but it is not in the breezy repositories.[/QUOTE]

here you go ;)

wxpython:
[http://archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.5/wxpython2.5.3_2.5.3.2ubuntu4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.5/wxpython2.5.3_2.5.3.2ubuntu4_i386.deb)

libwxgtk-python:
[http://archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.5/libwxgtk2.5.3-python_2.5.3.2ubuntu4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.5/libwxgtk2.5.3-python_2.5.3.2ubuntu4_i386.deb)

---

### Post by scourge on 2005-06-26
Nice job Sapo. I especially liked this helpful message:
```
Encoding in progress. Visit www.ubuntuforums.org while the software works!
```

It doesn't get any more user-friendly than that  :smile:

---

### Post by sapo on 2005-06-26
[QUOTE=scourge]Nice job Sapo. I especially liked this helpful message:
```
Encoding in progress. Visit www.ubuntuforums.org while the software works!
```

It doesn't get any more user-friendly than that  :smile:[/QUOTE]

thanx! did it work as it is supposed to?  :grin:

---

### Post by crashtest on 2005-06-26
Works great for me.  Nice job!

---

### Post by az on 2005-06-26
That other app does not convert to mp3.


Do you need help making your's into a deb with proper dependancies?

---

### Post by timczer on 2005-06-26
I was getting the same error message as mentioned earlier and I have the two packages you mentioned.  I am not sure what else to look for.

---

### Post by sapo on 2005-06-26
[QUOTE=azz]That other app does not convert to mp3.


Do you need help making your's into a deb with proper dependancies?[/QUOTE]

sure! i m working on a progress bar right now  :grin: 

but i m getting segmentation fault when the progress ends  ](*,)

---

### Post by sapo on 2005-06-27
Hi fellows... i ve added i progress bar to the app, is still dummy cause i cant find a way to detach the external apps from the main window... btw.. if somebody could test it:

Just download the script again please:
[http://xgn.no-ip.org:1000/downloads/converter.py](http://xgn.no-ip.org:1000/downloads/converter.py)

---

### Post by UbuWu on 2005-06-27
Just tried it on hoary, nice first version, does what it says.

Things that can be improved:
- The ugly directory selection dialog (because of using wxwidgets??)
- The window with the progress bar doesn't close after finishing encoding
- No need to see all the commands that the program executes
- Possibility of selecting individual files instead of directories
- open folder and save files to buttons should have equal width

And of course the interface could be more polished...

Note that soundconverter is listed as currently being packaged, so it will probably be available (working) soon. One thing that really needs to be packaged as well is gstreamer-lame as this will add mp3 support to soundconverter and soundjuicer! I really want soundjuicer to rip to mp3... (my ipod doesn't play ogg's  :mad: )

---

### Post by sapo on 2005-06-27
[QUOTE=UbuWu]Just tried it on hoary, nice first version, does what it says.

Things that can be improved:
- The ugly directory selection dialog (because of using wxwidgets??)
- The window with the progress bar doesn't close after finishing encoding
- No need to see all the commands that the program executes
- Possibility of selecting individual files instead of directories
- open folder and save files to buttons should have equal width

And of course the interface could be more polished...

Note that soundconverter is listed as currently being packaged, so it will probably be available (working) soon. One thing that really needs to be packaged as well is gstreamer-lame as this will add mp3 support to soundconverter and soundjuicer! I really want soundjuicer to rip to mp3... (my ipod doesn't play ogg's  :mad: )[/QUOTE]


thanx for testing ^^


I already was thinking about the commands and stuff i ll ty to make the interface better  :grin: 

But first i need help to run the encoding stuff in a separate process.. and as i m kind new to python i cant make it work properly  ](*,)

---

### Post by sapo on 2005-06-27
[QUOTE=UbuWu]Just tried it on hoary, nice first version, does what it says.

Things that can be improved:
- The ugly directory selection dialog (because of using wxwidgets??)
- The window with the progress bar doesn't close after finishing encoding
- No need to see all the commands that the program executes
- Possibility of selecting individual files instead of directories
- open folder and save files to buttons should have equal width

And of course the interface could be more polished...

Note that soundconverter is listed as currently being packaged, so it will probably be available (working) soon. One thing that really needs to be packaged as well is gstreamer-lame as this will add mp3 support to soundconverter and soundjuicer! I really want soundjuicer to rip to mp3... (my ipod doesn't play ogg's  :mad: )[/QUOTE]

man i stayed more than 8 hours today trying to make the process run in the background and put a progress bar.. but it didnt work...

And i tryed to make the filename appear in the progress bar instead of the command.. but it got all messed up... i think i ll rewrite everything  ](*,)

---

### Post by mtron on 2005-06-28
Hi sapo! 

i have the latest wxpython installed (and the other deps) but get the same error.

[QUOTE=UbuWu]Traceback (most recent call last):
  File "converter.py", line 331, in ?
    app = MyApp(0)
  File "/usr/lib/python2.4/site-packages/wxPython/wx.py", line 1951, in __init__    _wxStart(self.OnInit)
  File "converter.py", line 324, in OnInit
    frame = main_frame(NULL, -1, "Music Converter")
  File "converter.py", line 28, in __init__
    self.__do_layout()
  File "converter.py", line 77, in __do_layout
    grid_sizer_2.Add(self.text_input, 0, wxEXPAND|wxFIXED_MINSIZE, 0)
NameError: global name 'wxFIXED_MINSIZE' is not defined
[/QUOTE]

---

### Post by sapo on 2005-06-28
[QUOTE=mtron]Hi sapo! 

i have the latest wxpython installed (and the other deps) but get the same error.[/QUOTE]


this happens cause you should have a version < than 2.5.2 :? 

try updating it... i dont now how to fix it.. if i take this option off the gui messes up  ](*,)

---

### Post by UbuWu on 2005-06-28
I don't have much experience with python, but I think you can avoid people getting strange errors when they don't have wxpython installed this way:

```

try:
    from wxPython.wx import *
except ImportError:
    print "Install wxPython before running this program."
    sys.exit(0)
```

---

### Post by UbuWu on 2005-06-28
And you should allow for .Ogg .oGg . ogG .Mp3 .mP3 as input files.

---

### Post by sapo on 2005-06-28
already fixed that...

Version 0.0.2 is coming out from the oven in a few minutes.. with a lot of fixes and a nice progress bar (that is half working.. still dummy)  :grin:

[QUOTE=UbuWu]And you should allow for .Ogg .oGg . ogG .Mp3 .mP3 as input files.[/QUOTE]

man.. i should kill who name files like that  ](*,)

---

### Post by sapo on 2005-06-28
[QUOTE=UbuWu]And you should allow for .Ogg .oGg . ogG .Mp3 .mP3 as input files.[/QUOTE]

man.. i should kill how name files like this  ](*,)

---

### Post by alred on 2005-06-28
nice GUI from the first posting !
but i can't reach your site , can't download the program .....  :|

---

### Post by sapo on 2005-06-28
[QUOTE=alred]nice GUI from the first posting !
but i can't reach your site , can't download the program .....  :|[/QUOTE]

sorry.. there was a power failure (is rainning here, my cpu went down, but now is ok)

I will upload it to somewhere else to prevent this kind of stuff [img]http://ubuntuforums.org/images/smilies/eusa_whistle.gif[/img]

---

### Post by sapo on 2005-06-28
Version 0.0.2 OUT!

[http://xgn.no-ip.org:1000/downloads/converter.py](http://xgn.no-ip.org:1000/downloads/converter.py)

CHANGELOG: 

27/06/2005
---Version 0.0.2
* Dummy progress windows with progress bar added
* Now it shows the filename and status when encoding, instead of showing the running command
* The commands output are now sent to terminal, if you run it from terminal you can check what is going on in the background
* Checking for wxPython on startup -> thanx UbuWu

---

### Post by UbuWu on 2005-06-28
Bug in line 311: .GGG should be .OGG  ;-)

---

### Post by UbuWu on 2005-06-28
Tried it:

==== The following files will be encoded: ====
26-bon_garcon_-_freek_u-wk24-woei.mp3
26-bon_garcon_-_freek_u-wk24-woei.mp3
26-bon_garcon_-_freek_u-wk24-woei.mp3

 ==== Current File: ====
26-bon_garcon_-_freek_u-wk24-woei.mp3
**** Decoding Finished!! ****
 ==== Current File: ====
26-bon_garcon_-_freek_u-wk24-woei.mp3
**** Encoding Finished!! ****
 ==== Current File: ====
26-bon_garcon_-_freek_u-wk24-woei.mp3
**** Encoding Finished!! ****

Looks like the encoding is done twice?

---

### Post by UbuWu on 2005-06-28
- The temporary .wav file isn't removed.
- This file should be created in /tmp ??
- Doesn't ask before overwriting files.
- If you have a directory with both mp3 and ogg files, it doesn't make much sense to convert the mp3 files to mp3 files...

---

### Post by sapo on 2005-06-28
it was just a test stuff.. i m working in it right now:

ogg123 -d wav -f - 01\ -\ Angra\ -\ Unfinished\ Allegro.ogg | lame - outfile.mp3

i will stream the wav direct to lame without temp files....

it dont requires disk space.. and is less risky than using a rm to remove the temp file

a few minutes and it will be done so you will be able to test it  :grin:

---

### Post by sapo on 2005-06-28
man.. this thing was buggy.. had to fix a lot of things...

*Fixed the name of files showing twice and the feedback is better now.
*Fixed a problem with the .ogg files


And my idead to stream the decoding direct to the encoder didnt work... i ll have to make threads and use another method.. cause the wx stuff isnt allowing me to run 2 commands in the same line  ](*,)

---

### Post by UbuWu on 2005-06-28
OK, current output:

==== The following files will be encoded: ====
26-bon_garcon_-_freek_u-wk24-woei.mp3

 ==== Status: ====
Encoding: 26-bon_garcon_-_freek_u-wk24-woei.mp3
**** Encoding Finished!! ****
Encoding: 26-bon_garcon_-_freek_u-wk24-woei.mp3

Still showing twice??

And if I select 128k for ogg output and NOT vbr, I can see at the commandline it is actually vbr with an average 128k bitrate

---

### Post by sapo on 2005-06-28
[QUOTE=UbuWu]OK, current output:

==== The following files will be encoded: ====
26-bon_garcon_-_freek_u-wk24-woei.mp3

 ==== Status: ====
Encoding: 26-bon_garcon_-_freek_u-wk24-woei.mp3
**** Encoding Finished!! ****
Encoding: 26-bon_garcon_-_freek_u-wk24-woei.mp3

Still showing twice??

And if I select 128k for ogg output and NOT vbr, I can see at the commandline it is actually vbr with an average 128k bitrate[/QUOTE]


its showing twice when you select what format and what option?

i ll fix the vbr stuff

here the output is ok: see:

==== The following files will be encoded: ====
01 - Angra - Unfinished Allegro.mp3

 ==== Status: ====
Encoding: 01 - Angra - Unfinished Allegro.mp3
**** Encoding Finished!! ****

---

### Post by UbuWu on 2005-06-28
I was encoding from mp3 to ogg at 128k.

I think VBR/CBR should be a separate option so you can select either of them on any bitrate.

---

### Post by sapo on 2005-06-28
[QUOTE=UbuWu]I was encoding from mp3 to ogg at 128k.

I think VBR/CBR should be a separate option so you can select either of them on any bitrate.[/QUOTE]

it will be.. but first i want it to work properly.. and then i will add features

i m planning to added a config menu.. and stored your default configs.. you will not have to change it each time you start the app..

and i want to make a "custom" field.. so you can pass your own options to the encoder  :grin: 

but first i need to make it work  ](*,)

---

### Post by UbuWu on 2005-06-28
When I have encoded a file, and close the program, python keeps running. I don't get returned to th commandline if I started it from there. This doesn't happen when I don't have encoded a file.

---

### Post by sapo on 2005-06-28
[QUOTE=UbuWu]When I have encoded a file, and close the program, python keeps running. I don't get returned to th commandline if I started it from there. This doesn't happen when I don't have encoded a file.[/QUOTE]

i dont know why it is happening.. i ll try to find a way to debug  :-P

---

### Post by sapo on 2005-06-28
lol.. after a hour trying to find the bug.. i found it! it was a stupid msg box that i forgot do destroy when it was closed.. 

now it looks like bug free  :roll: 

but just until sombody try it  ](*,) 

btw... could somebody help me make a .deb package with dependencies? i wanna learn how to do it  :grin:

i found this:
[http://linuxdevices.com/articles/AT8047723203.html](http://linuxdevices.com/articles/AT8047723203.html)

but its a lot of things to read omg.. i think i need to sleep first..  :roll:

---

### Post by sapo on 2005-06-29
And for those who want to edit or add id3 tags after losing them with my app.. you can try this out:

[http://easytag.sourceforge.net/screenshots-gtk2.htm](http://easytag.sourceforge.net/screenshots-gtk2.htm)

its a very good app...

its in the repositories.. just run:

```

sudo apt-get install easytag

```

Btw.. i m already starting to study the python-id3 modulo.. copy the tags to the new files are one of my priorities.. but first i ll add more encoding options to the app..  :grin: 

a little screenshot:
[img]http://easytag.sourceforge.net/images/screenshot-gtk2/screenshot_main_window.jpg[/img]

---

### Post by oddabe19 on 2005-06-29
what about m4a to mp3/ogg?

---

### Post by sapo on 2005-06-29
[QUOTE=oddabe19]what about m4a to mp3/ogg?[/QUOTE]

m4a? i dont know this format.. could you give me more information about it? if its free and have a encoder and decoder i can make something to it  :-P

---

### Post by sapo on 2005-06-29
And regarding to the app.. anyone tested the new file.. did it work?

Any suggestions.. is it usefull?

please i want some feedback  :grin:

---

### Post by alred on 2005-06-30
works fine for me when batch converting 10 ogg files to mp3 files

but is it not better to use piping when running batch conversion in-order to avoid writing to wave files firstly and then deleting those in the end ?

...

---

### Post by oddabe19 on 2005-06-30
[QUOTE=sapo]m4a? i dont know this format.. could you give me more information about it? if its free and have a encoder and decoder i can make something to it  :-P[/QUOTE]
 m4a is basically mp version 4 (mp4). It sucks cause nothing supports it, gstreamer uses faad to decode it.

---

### Post by sapo on 2005-06-30
[QUOTE=alred]works fine for me when batch converting 10 ogg files to mp3 files

but is it not better to use piping when running batch conversion in-order to avoid writing to wave files firstly and then deleting those in the end ?

...[/QUOTE]

Yes it is... but as i m using wxPython.. it cant run more than one command at time.. i m thinking about rewriting it in pyGTK or maybe use another kind of stuff to run the commands...

---

### Post by UbuWu on 2005-06-30
Instead of rewriting it, I think you should consider using soundconverter which will probably be in the repositories soon... See [http://siretart.tauware.de/revu/index.py](http://siretart.tauware.de/revu/index.py) , the package seems to be ready. You would just be rewriting that program.

Only problem is that it can't produce mp3's without gstreamer-lame (lame is in the repositories, gstreamer-lame isn't). So maybe you could package gstreamer-lame??

---

### Post by alred on 2005-06-30
hmm .. it seems that wxExecute is using execvp() [or is it ?] for command execution , problems in piping though i guess , and they have wxProcess for fine tunning , look complicated for me cause i never use python ....

hope you solve the command runnung problem as fast as possible , after that i guess your very first linux app will definately grows ...


waiting for your latest release ...

---

### Post by sapo on 2005-06-30
[QUOTE=alred]hmm .. it seems that wxExecute is using execvp() [or is it ?] for command execution , problems in piping though i guess , and they have wxProcess for fine tunning , look complicated for me cause i never use python ....

hope you solve the command runnung problem as fast as possible , after that i guess your very first linux app will definately grows ...


waiting for your latest release ...[/QUOTE]


Thanx.. man.. this thing drove me so mad that i didnt tried to change that stuff.. i know what to do.. i know how to do.. but this thing just doesnt work!  ](*,) 

This week i ll try to make the process run in background and stream the decoding direct to the encoding (no need to wav file anymore)...

And i ll change the file list to.. the user will be able to choose wich file he is (or not) going to encode  :grin: 

but the main problem is that wxExecute stuff  ](*,)

---

