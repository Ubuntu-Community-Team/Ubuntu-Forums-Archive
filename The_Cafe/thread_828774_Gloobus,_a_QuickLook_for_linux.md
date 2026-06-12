---
title: "Gloobus, a QuickLook for linux"
date: 2008-06-14
forum: The Cafe
---

### Post by badchoice on 2008-06-14
//============= EDITED 02/02/2010 ==================== //

Check the webpage: [http://gloobus.net](http://gloobus.net)
and the wiki: [http://gloobus.net/wiki](http://gloobus.net/wiki)

To install gloobus-preview:
```

  sudo add-apt-repository ppa:gloobus-dev/gloobus-preview
  sudo apt-get install gloobus-preview
  sudo apt-get upgrade

```

  And then restart nautilus

To install covergloobus (The music player..)
```

  sudo add-apt-repository ppa:gloobus-dev/covergloobus
  sudo apt-get isntall covergloobus

```

To install gloobus-flow (coverflow like nautilus)
```

  sudo add-apt-repository ppa:gloobus-dev/gloobus-flow !!!! NOT AVAILABLE WORKING YET!!!
  sudo apt-get install gloobus-flow
  sudo apt-get upgrade

```
  And restart nautilus

//============= EDITED 09/09/2009 ==================== //
Woww, have you seen the date!!

Gloobus PPA up and running with the last version and patched nautilus to launch gloobus-preview with just pressing the space key.
Follow instructions here:

**[https://answers.launchpad.net/gloobus/+question/73391](https://answers.launchpad.net/gloobus/+question/73391)**


//============= EDITED 10/05/2009 ==================== //
Hi!!!!

Good News!!!
New version of **Gloobus-Preview** Available!!!!
It works for jaunty with no problems! Here you have the URL and the ChangeLog

About CoverGloobus, I've done some improvements, you can find the new link here to!!

I hope you like it!!
**[Gloobus-Preview-0.03.2]("http://jordihp.deviantart.com/art/Gloobus-Preview-0-03-2-122054947")**

**[CoverGloobus]("http://jordihp.deviantart.com/art/CoverGloobus-1-2-118080718")**

[**Donate**]("https://www.paypal.com/us/cgi-bin/webscr?cmd=_flow&SESSION=0ffR9mMKmWT2y9c0DV-04ZuX2Hsun9i2LOh44aOQ0aEdnF5nL7kGk4NGIDG&dispatch=5885d80a13c0db1f998ca054efbdf2c25fe4a05bcb33bff66824cbab1a92dde6")

ChangeLog Gloobus-Preview 0.03.1
- iComic (cbz and cbr)
- iPdf solved som bugs
- Shadow in the application
- iMp3 with ogg support
- iDocument fixed a very annoing warning
- iFolder

Installation Instructions Inside the file! (32bits and 64bits versions)

// =================================================== //

Hi everyone,
I'm developing a free opensource QuickLook for linux in openGL (c++) it is a coverflow for see the in a fast way the files without opening them,

There are the links for download, screencast and launchpad page:

Blog: [http://gloobus.wordpress.com/](http://gloobus.wordpress.com/)
Launchpad: [http://launchpad.net/gloobus](http://launchpad.net/gloobus)
Screenshots: [http://sourceforge.net/projects/gloobus](http://sourceforge.net/projects/gloobus)
Screencasts: [http://www.youtube.com/profile_videos?user=badchoice](http://www.youtube.com/profile_videos?user=badchoice)
External Downloads: [https://edge.launchpad.net/gloobus/+download](https://edge.launchpad.net/gloobus/+download)


[B]DONATE: [https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=guitarboy000%40gmail%2ecom&item_name=Gloobus%2c%20A%20Quicklook%20for%20linux&no_shipping=0&no_note=1&tax=0&currency_code=EUR&lc=US&bn=PP%2dDonationsBF&charset=UTF%2d8](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=guitarboy000%40gmail%2ecom&item_name=Gloobus%2c%20A%20Quicklook%20for%20linux&no_shipping=0&no_note=1&tax=0&currency_code=EUR&lc=US&bn=PP%2dDonationsBF&charset=UTF%2d8)
[/B]

Now I have it in a very good way but there are a couple of things I would like to do and I don't know how, maybe you can help me.

First one: How to bind space key in nautlius to launch my own nautilus-script (this will be used for bind space key to preview file)

Second : How to add a button on the toolbar that lauches my own nautilus-script (this will be used for launch folder coverflow)

If anyone of you know how to do this It will be one of the remaining points solved!

Some information about:Now I can preview, any kind of images, any kind of plain text files and pdf. It supports mp3 (album coverts and song preview)
and I'm working on video files support and plugin architecture.

I also would like to know your ideas so this way we can make it beat apples one!!!!

Thank you!

---

### Post by pt123 on 2008-06-14
Thanks for posting about it here. You might want to mention "Cover Flow" in the title.

It would be good if there was a way to navigate into to a folder shown in cover flow. 

Also it might be better to cache only the first 20 or so images in a folder with many images.

It doesn't currently work well with PNGs, no problems with jpgs. 

Keep up the good work

---

### Post by badchoice on 2008-06-14
Yes, there are still a lot of things to do...

Now I'll add coverflow on the title so it will be easy for the people to know what is it about!!

I've planned to load only 20 images every time, but now I'm developing the plugin architecture to make it more modular and easyest to find the bugs and solve them (like the pngs one, or the blanc shapes), plus this way everyone can develop his onw preview plugin! I'm doing it givint total liberty for the plugins so each one can do whatever they want!!

I'll post on launchpad and here when the next version is ready!

Thanks !

---

### Post by Tomatz on 2008-06-14
Looks cool :)

Thanks

---

### Post by bash on 2008-06-14
It looks really nice. Great work so far. I really liked that idea when I first saw it on a mac. Although I would probably mostly use it to play around and not for productivity ;)

So far I see you have to activate the gloobus mode through rightclicking a file. Are there any plans to include the gloobus mode as part of the nautilus window? So just can just activate or deactive it like the status- or sidebar of nautilus?

---

### Post by badchoice on 2008-06-14
Yes, it's planned to integrate it with nautilus, I'm talking with nautilus developers to see if we can achieve this.

---

### Post by The Cosmic Hobo on 2008-06-14
That looks pretty promising. Good luck with the project and the Nautilus integration.

---

### Post by aktiwers on 2008-06-14
Looks very nice!

---

### Post by Jay_Bee on 2008-06-14
Wow, this stuff is great, good job badchoise! :D
This really made my day, I can't wait to see it in nautilus!:grin:

---

### Post by badchoice on 2008-06-15
Thank you all!
I'll post here the new releases and the new information about the project!

---

### Post by badchoice on 2008-06-15
**[COLOR="Red"]Version 0.02 is out!![/COLOR]**

It has the preview wit plugin architecture, this way we can find and solve problems in a very easy way and now, everyone can develop his own plugin. When everything is more stable I'll post a quick guide on how to implement your own plugin. I hope we can preview almost all the files!!

**Download:** [https://launchpad.net/gloobus/gloobus-0.02/0.02](https://launchpad.net/gloobus/gloobus-0.02/0.02)

And remember, you can donate me some money ;)

**DONATE: [http://widget.chipin.com/widget/id/0b88c464e8dfbcce](http://widget.chipin.com/widget/id/0b88c464e8dfbcce)**

---

### Post by pt123 on 2008-06-16
What's new in 0.02?

Hopefully that amount will have a good conversion rate, where you are from.

---

### Post by scorp123 on 2008-06-16
> **badchoice said:**
>  I'm developing a free opensource QuickLook for linux in openGL (c++) Could you please also post a version for Gutsy (= Ubuntu 7.10)? Or could you please post the source package so us Gutsy users could compile our own binary release version?

I don't feel like upgrading to Ubuntu 8.04 yet as it's still way too buggy for my taste. But it would be nice to have gloobus nontheless ;)

---

### Post by Colonel Kilkenny on 2008-06-16
> **scorp123 said:**
> Could you please also post a version for Gutsy (= Ubuntu 7.10)? Or could you please post the source package so us Gutsy users could compile our own binary release version?

I don't feel like upgrading to Ubuntu 8.04 yet as it's still way too buggy for my taste. But it would be nice to have gloobus nontheless ;)

And same humble request goes for 64bit systems. Either package for amd64 or sources.

---

### Post by badchoice on 2008-06-16
The main reason of this new version is the plugin architecture, I've rewrited all the preview function and now it supports plugins.

Plugins can have his own load, update and render function so it can be very scalable!!

I'm from Barcelona (Spain), these days I'll be fixing a lot of issues, till now I just made it work to see what were the capibilities of it, now I very proud and I'm fixing a lot of things till version 0.03 that will have both gloobus and preview with plugin architecture.

There should be no problem at all in compiling it for gutsy or 64  bits version, if you want to compile it and send me the binaries I'll put them on launchpad page (I have no gusty machine neither 64bits one) if you have any problem, please tell me and I'll try to solve it.

Thank you all!

I put 1000$ on chipIn widget to put something, you can donate the amount you want there is no problem about it or not reaching 1000$, I'm doing it cause I think it will be good to have a quicklook for linux, and since it takes me a lot of time, get paid is allways a great reward :D :D :):KS

Thank you again!

---

### Post by scorp123 on 2008-06-16
> **badchoice said:**
> There should be no problem at all in compiling it for gutsy or 64  bits version, if you want to compile it and send me the binaries I'll put them on launchpad page OK, but where are the source files please? And what libraries are needed? It would be nice if you could give a quickie overview of the requires packages and post the source code somewhere where we can easily find it :)

---

### Post by badchoice on 2008-06-16
Of course!
Here you have the code addres, the project is under launchpad

**[https://code.launchpad.net/gloobus](https://code.launchpad.net/gloobus)**

Bugs managment, code, releases, answers...

The libraries needed are listed in the README file inside the release and in the main folder in the code.

GL
GLU
SDL
SDL_IMAGE  
SDL_MIXER (For mp3 plugin)
TAGLIB    (For mp3 plugin)
Magick++  (For text and pdf plugin)
Magic     (To know the file type)

If you still have any problem, please tell me.

---

### Post by scorp123 on 2008-06-16
> **badchoice said:**
>  The libraries needed are listed in the README file inside the release and in the main folder in the code.

GL
GLU
SDL
SDL_IMAGE  
SDL_MIXER (For mp3 plugin)
TAGLIB    (For mp3 plugin)
Magick++  (For text and pdf plugin)
Magic     (To know the file type)

If you still have any problem, please tell me. Can you list the package names for those libraries please? I am sure there are many users out there who don't know that e.g. to get what you call "Magick++" they'd need to install "libmagick++10-dev" and so on. See what I mean? 

Please list the package names needed so people can copy & paste the list and "apt-get install" it, OK? ;)

---

### Post by DeadSuperHero on 2008-06-16
I think this is a fantastic project, I hope to see it grow!
I'll be putting up some suggestions on LaunchPad.

---

### Post by Le-Froid on 2008-06-16
I think I installed everything needed for it, but for some reason it doesn't respond to my keyboard, and after 3-5 seconds my computer freezes :S

Can you list, exactly, what I need to make it work (using Ubuntu 8.04)

edit: Got keyboard working, but it is EXTREMELY SLOW on my computer :S On windows, all  SDL/OpenGL programs and stuff work just fine

---

### Post by badchoice on 2008-06-16
Hey, I've just uploaded a new version 0.021 

**[https://launchpad.net/gloobus/gloobus-0.02/0.02](https://launchpad.net/gloobus/gloobus-0.02/0.02)**

I've improved some things (Faster pdf and text renders), less memory hungry and some other things...

I've changed the way it loads the textures and I hope it fixes the white shape bug and the slow one...

You can run it from command line to see the debugin lines, and if there are errors you can post them in launchpad.

It only affects the preview function not the gloobus one, so please, don't report bugs about the gloobus one till I upgrade it to the plugin architecture!!

**Donate: [http://widget.chipin.com/widget/id/0b88c464e8dfbcce](http://widget.chipin.com/widget/id/0b88c464e8dfbcce)**

The dependences needed:

```
sudo apt-get install libsdl-mixer1.2-dev libsdl1.2-dev libsdl-ttf2.0-dev libsdl-image1.2-dev libmagick++9-dev libmagic-dev libtag1-dev
```


Thanks!

---

### Post by scorp123 on 2008-06-16
> **badchoice said:**
>  The dependences needed:

```
sudo apt-get install libsdl-mixer1.2-dev libsdl1.2-dev libsdl-ttf2.0-dev libsdl-image1.2-dev libmagick++9-dev libmagic1
```  You're the man :D

Thanks :)

---

### Post by scorp123 on 2008-06-16
> **badchoice said:**
> Of course!
Here you have the code addres, the project is under launchpad

**[https://code.launchpad.net/gloobus](https://code.launchpad.net/gloobus)**

Bugs managment, code, releases, answers... Hmmmm ... sorry, I still can't figure out how to download the source files as one single archive? :confused: .... Or can we use cvs or svn to get to those files? Sorry, I am lost here.

---

### Post by scorp123 on 2008-06-16
Self-reply ... reading the small print helps it seems :)
```
bzr branch lp:gloobus/gloobus-0.02
```

---

### Post by Le-Froid on 2008-06-16
Still slow after new one + all needed things, but atleast at this point it is usable for me :)
edit: Got a lot faster, but uses 90% of my memory (Ive got 2gb ram)

---

### Post by badchoice on 2008-06-17
90% of 2BG of memory????
Are you using gloous or preview? preview just loads one file, and gloobus loads all the folder, and does the coverflow transitions but now it don't use the plugin architecture were I've made all the improvements, its the next step, join gloobus with the plugin and improve it a lot, one of this improvements is to have just 10 files on memory.

---

### Post by scorp123 on 2008-06-17
Something else ... Can you please post how one is supposed to compile "gloobus"? I get endless amounts of errors when I try to execute "make all" despite having all the needed libraries installed.

---

### Post by badchoice on 2008-06-18
> **scorp123 said:**
> Something else ... Can you please post how one is supposed to compile "gloobus"? I get endless amounts of errors when I try to execute "make all" despite having all the needed libraries installed.

I had some issues with TagLib, it reported me a lot of errors on compiling. Taglib library in Ubuntu has some bugs and it searches for his own headers files in a wrong path...

To solve this you just need to edit the file that give errors (I can't remeber now) is the two firs lines of errors (attachedpicturetag.h or something like this) and at the top of this file, add "../" on the include paths.

I hope it helps! 

I will do a better search and post here the solution in a better explanation!

---

### Post by scorp123 on 2008-06-18
These are the errors I get:

```
:~/tmp/Gloobus/gloobus-0.02/Gloobus-dev > make

g++ -Wall -o gloobus main.cpp engine.cpp timer.cpp load.cpp font.cpp -lSDL -lGL -lGLU -lSDL_image -lMagick++ -lmagic -lSDL_ttf -ltag
In file included from engine.h:12,
                 from main.cpp:1:
load.h:14:44: error: magic.h: No such file or directory
load.h:18:29: error: taglib/mpegfile.h: No such file or directory
load.h:19:41: error: taglib/attachedpictureframe.h: No such file or directory
load.h:20:29: error: taglib/id3v2tag.h: No such file or directory
In file included from engine.h:12,
                 from engine.cpp:8:
load.h:14:44: error: magic.h: No such file or directory
load.h:18:29: error: taglib/mpegfile.h: No such file or directory
load.h:19:41: error: taglib/attachedpictureframe.h: No such file or directory
load.h:20:29: error: taglib/id3v2tag.h: No such file or directory
engine.cpp: In function ‘int getdir(std::string, std::vector<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > >&)’:
engine.cpp:39: error: ‘magic_t’ was not declared in this scope
engine.cpp:39: error: expected `;' before ‘myt’
engine.cpp:40: error: ‘myt’ was not declared in this scope
engine.cpp:40: error: ‘magic_load’ was not declared in this scope
engine.cpp:46: error: ‘magic_file’ was not declared in this scope
engine.cpp:67: error: ‘magic_close’ was not declared in this scope
In file included from load.cpp:1:
load.h:14:44: error: magic.h: No such file or directory
load.h:18:29: error: taglib/mpegfile.h: No such file or directory
load.h:19:41: error: taglib/attachedpictureframe.h: No such file or directory
load.h:20:29: error: taglib/id3v2tag.h: No such file or directory
load.cpp: In member function ‘std::string Load::getFileType(std::string)’:
load.cpp:29: error: ‘magic_t’ was not declared in this scope
load.cpp:29: error: expected `;' before ‘myt’
load.cpp:30: error: ‘myt’ was not declared in this scope
load.cpp:30: error: ‘magic_load’ was not declared in this scope
load.cpp:31: error: ‘magic_file’ was not declared in this scope
load.cpp:32: error: ‘magic_close’ was not declared in this scope
load.cpp: In member function ‘void Load::loadMP3(Photo*)’:
load.cpp:233: error: ‘TagLib’ has not been declared
load.cpp:233: error: expected `;' before ‘file’
load.cpp:234: error: ‘TagLib’ has not been declared
load.cpp:234: error: ‘tagv2’ was not declared in this scope
load.cpp:234: error: ‘file’ was not declared in this scope
load.cpp:238: error: ‘TagLib’ has not been declared
load.cpp:238: error: expected `;' before ‘tags’
load.cpp:239: error: ‘TagLib’ has not been declared
load.cpp:239: error: expected `;' before ‘pictures’
load.cpp:241: error: ‘pictures’ was not declared in this scope
load.cpp:244: error: ‘TagLib’ has not been declared
load.cpp:244: error: ‘picture’ was not declared in this scope
load.cpp:245: error: expected type-specifier before ‘TagLib’
load.cpp:245: error: expected `>' before ‘TagLib’
load.cpp:245: error: expected `(' before ‘TagLib’
load.cpp:245: error: ‘TagLib’ has not been declared
load.cpp:245: error: expected primary-expression before ‘>’ token
load.cpp:245: error: expected `)' before ‘;’ token
load.cpp:247: error: ‘TagLib’ has not been declared
load.cpp:247: error: expected `;' before ‘pictureData’
load.cpp:249: error: ‘pictureData’ was not declared in this scope
load.cpp: In member function ‘void Load::scaleImage(Photo*, int, int)’:
load.cpp:291: warning: converting to ‘int’ from ‘float’
load.cpp:292: warning: converting to ‘int’ from ‘float’
load.cpp:298: warning: converting to ‘int’ from ‘float’
load.cpp:299: warning: converting to ‘int’ from ‘float’
load.cpp: In member function ‘void Load::getSizeResized(Photo*, int*, int*)’:
load.cpp:326: warning: converting to ‘int’ from ‘float’
load.cpp:327: warning: converting to ‘int’ from ‘float’
load.cpp:333: warning: converting to ‘int’ from ‘float’
load.cpp:334: warning: converting to ‘int’ from ‘float’
load.cpp:342: warning: converting to ‘int’ from ‘float’
load.cpp:343: warning: converting to ‘int’ from ‘float’
load.cpp:350: warning: converting to ‘int’ from ‘float’
load.cpp:351: warning: converting to ‘int’ from ‘float’
make: *** [gloobus] Interrupt

```

---

### Post by badchoice on 2008-06-18
There are two main errors.

magic.h
and taglib, it like you don't have magic-dev and taglib-dev..

Maybe I posted wrong the packages needed to compile, when I get home I'll make sure that the apt-get install code I give you is Ok.

Anyway, you can use sudo apt-cache search taglib and search fort something like taglib-dev..

and sudo apt-cache search magic and search for something like libmagic-dev

---

### Post by badchoice on 2008-06-18
You're right I put wrong the packages the good one:

sudo apt-get install libsdl-mixer1.2-dev libsdl1.2-dev libsdl-ttf2.0-dev libsdl-image1.2-dev libmagick++9-dev libmagic-dev libtag1-dev

---

### Post by scorp123 on 2008-06-18
The error messages have changed.

Now I get this:

```
 make

g++ -Wall -o gloobus main.cpp engine.cpp timer.cpp load.cpp font.cpp -lSDL -lGL -lGLU -lSDL_image -lMagick++ -lmagic -lSDL_ttf -ltag
In file included from load.h:19,
                 from engine.h:12,
                 from main.cpp:1:
/usr/include/taglib/attachedpictureframe.h:25:24: error: id3v2frame.h: No such file or directory
/usr/include/taglib/attachedpictureframe.h:26:25: error: id3v2header.h: No such file or directory
/usr/include/taglib/attachedpictureframe.h:42: error: expected class-name before ‘{’ token
/usr/include/taglib/attachedpictureframe.h:122: error: ‘Type’ in class ‘TagLib::String’ does not name a type
/usr/include/taglib/attachedpictureframe.h:129: error: ‘struct TagLib::String::Type’ has not been declared
/usr/include/taglib/attachedpictureframe.h:205: error: ‘Header’ has not been declared
In file included from load.h:19,
                 from engine.h:12,
                 from engine.cpp:8:
/usr/include/taglib/attachedpictureframe.h:25:24: error: id3v2frame.h: No such file or directory
/usr/include/taglib/attachedpictureframe.h:26:25: error: id3v2header.h: No such file or directory
/usr/include/taglib/attachedpictureframe.h:42: error: expected class-name before ‘{’ token
/usr/include/taglib/attachedpictureframe.h:122: error: ‘Type’ in class ‘TagLib::String’ does not name a type
/usr/include/taglib/attachedpictureframe.h:129: error: ‘struct TagLib::String::Type’ has not been declared
/usr/include/taglib/attachedpictureframe.h:205: error: ‘Header’ has not been declared
In file included from load.h:19,
                 from load.cpp:1:
/usr/include/taglib/attachedpictureframe.h:25:24: error: id3v2frame.h: No such file or directory
/usr/include/taglib/attachedpictureframe.h:26:25: error: id3v2header.h: No such file or directory
/usr/include/taglib/attachedpictureframe.h:42: error: expected class-name before ‘{’ token
/usr/include/taglib/attachedpictureframe.h:122: error: ‘Type’ in class ‘TagLib::String’ does not name a type
/usr/include/taglib/attachedpictureframe.h:129: error: ‘struct TagLib::String::Type’ has not been declared
/usr/include/taglib/attachedpictureframe.h:205: error: ‘Header’ has not been declared
load.cpp: In member function ‘void Load::loadMP3(Photo*)’:
load.cpp:245: error: invalid static_cast from type ‘TagLib::ID3v2::Frame*’ to type ‘TagLib::ID3v2::AttachedPictureFrame*’
load.cpp: In member function ‘void Load::scaleImage(Photo*, int, int)’:
load.cpp:291: warning: converting to ‘int’ from ‘float’
load.cpp:292: warning: converting to ‘int’ from ‘float’
load.cpp:298: warning: converting to ‘int’ from ‘float’
load.cpp:299: warning: converting to ‘int’ from ‘float’
load.cpp: In member function ‘void Load::getSizeResized(Photo*, int*, int*)’:
load.cpp:326: warning: converting to ‘int’ from ‘float’
load.cpp:327: warning: converting to ‘int’ from ‘float’
load.cpp:333: warning: converting to ‘int’ from ‘float’
load.cpp:334: warning: converting to ‘int’ from ‘float’
load.cpp:342: warning: converting to ‘int’ from ‘float’
load.cpp:343: warning: converting to ‘int’ from ‘float’
load.cpp:350: warning: converting to ‘int’ from ‘float’
load.cpp:351: warning: converting to ‘int’ from ‘float’
In file included from load.h:19,
                 from font.h:10,
                 from font.cpp:1:
/usr/include/taglib/attachedpictureframe.h:25:24: error: id3v2frame.h: No such file or directory
/usr/include/taglib/attachedpictureframe.h:26:25: error: id3v2header.h: No such file or directory
/usr/include/taglib/attachedpictureframe.h:42: error: expected class-name before ‘{’ token
/usr/include/taglib/attachedpictureframe.h:122: error: ‘Type’ in class ‘TagLib::String’ does not name a type
/usr/include/taglib/attachedpictureframe.h:129: error: ‘struct TagLib::String::Type’ has not been declared
/usr/include/taglib/attachedpictureframe.h:205: error: ‘Header’ has not been declared
make: *** [gloobus] Error 1
```

---

### Post by badchoice on 2008-06-18
Yes, this is the bug in the taglib library for ubuntu I commented you in the previous post:

You just need to edit the file
/usr/include/taglib/attachedpictureframe.h

and replace the two includes at the top of the file:
#include <id3v2frame.h>
#include <id3v2header.h>

for 
[B]
#include <taglib/id3v2frame.h>
#include <taglib/id3v2header.h>[/B]


Then it should compile!!!

---

### Post by scorp123 on 2008-06-18
I changed the lines in the file you mentioned but it didn't help.

```
 > make
g++ -Wall -o gloobus main.cpp engine.cpp timer.cpp load.cpp font.cpp -lSDL -lGL -lGLU -lSDL_image -lMagick++ -lmagic -lSDL_ttf -ltag
In file included from load.h:19,
                 from engine.h:12,
                 from main.cpp:1:
/usr/include/taglib/attachedpictureframe.h:28:31: error: taglib/id3v3frame.h: No such file or directory
/usr/include/taglib/attachedpictureframe.h:45: error: expected class-name before ‘{’ token
/usr/include/taglib/attachedpictureframe.h:125: error: ‘Type’ in class ‘TagLib::String’ does not name a type
/usr/include/taglib/attachedpictureframe.h:132: error: ‘struct TagLib::String::Type’ has not been declared
In file included from load.h:19,
                 from engine.h:12,
                 from engine.cpp:8:
/usr/include/taglib/attachedpictureframe.h:28:31: error: taglib/id3v3frame.h: No such file or directory
/usr/include/taglib/attachedpictureframe.h:45: error: expected class-name before ‘{’ token
/usr/include/taglib/attachedpictureframe.h:125: error: ‘Type’ in class ‘TagLib::String’ does not name a type
/usr/include/taglib/attachedpictureframe.h:132: error: ‘struct TagLib::String::Type’ has not been declared
In file included from load.h:19,
                 from load.cpp:1:
/usr/include/taglib/attachedpictureframe.h:28:31: error: taglib/id3v3frame.h: No such file or directory
/usr/include/taglib/attachedpictureframe.h:45: error: expected class-name before ‘{’ token
/usr/include/taglib/attachedpictureframe.h:125: error: ‘Type’ in class ‘TagLib::String’ does not name a type
/usr/include/taglib/attachedpictureframe.h:132: error: ‘struct TagLib::String::Type’ has not been declared
load.cpp: In member function ‘void Load::loadMP3(Photo*)’:
load.cpp:245: error: invalid static_cast from type ‘TagLib::ID3v2::Frame*’ to type ‘TagLib::ID3v2::AttachedPictureFrame*’
load.cpp: In member function ‘void Load::scaleImage(Photo*, int, int)’:
load.cpp:291: warning: converting to ‘int’ from ‘float’
load.cpp:292: warning: converting to ‘int’ from ‘float’
load.cpp:298: warning: converting to ‘int’ from ‘float’
load.cpp:299: warning: converting to ‘int’ from ‘float’
load.cpp: In member function ‘void Load::getSizeResized(Photo*, int*, int*)’:
load.cpp:326: warning: converting to ‘int’ from ‘float’
load.cpp:327: warning: converting to ‘int’ from ‘float’
load.cpp:333: warning: converting to ‘int’ from ‘float’
load.cpp:334: warning: converting to ‘int’ from ‘float’
load.cpp:342: warning: converting to ‘int’ from ‘float’
load.cpp:343: warning: converting to ‘int’ from ‘float’
load.cpp:350: warning: converting to ‘int’ from ‘float’
load.cpp:351: warning: converting to ‘int’ from ‘float’
In file included from load.h:19,
                 from font.h:10,
                 from font.cpp:1:
/usr/include/taglib/attachedpictureframe.h:28:31: error: taglib/id3v3frame.h: No such file or directory
/usr/include/taglib/attachedpictureframe.h:45: error: expected class-name before ‘{’ token
/usr/include/taglib/attachedpictureframe.h:125: error: ‘Type’ in class ‘TagLib::String’ does not name a type
/usr/include/taglib/attachedpictureframe.h:132: error: ‘struct TagLib::String::Type’ has not been declared
make: *** [gloobus] Error 1
```

---

### Post by badchoice on 2008-06-18
Sorry, I typed it down wrong:

```
taglib/id3v3frame.h
```

must be

```
taglib/id3v**2**frame.h
```

---

### Post by scorp123 on 2008-06-18
Could you then update the source code please and include your corrections in the 'README' file? I guess anyone trying to compile this will experience the same errors. It would be nice to have corrected sources + a comment in the 'README' giving clear instructions. ;)

---

### Post by badchoice on 2008-06-18
I'v uploaded Version 0.022
It includes a lot of improvements, now gloobus coverflow uses the plugin architecture with all the benefits it has.

I've added a lot of things, for the moment nothing visually new, just faster and lees memory eater, in newer versions I'll add some eyecandy things!!

**[https://launchpad.net/gloobus/gloobus-0.02/0.02](https://launchpad.net/gloobus/gloobus-0.02/0.02)**

I'v forget to put the taglib corrections in the readme but I have corrected the libs needed, in the next version I'll put a note on how to fix that taglib bug.

And remeber you can still donate ;)
**Donate: [http://widget.chipin.com/widget/id/0b88c464e8dfbcce](http://widget.chipin.com/widget/id/0b88c464e8dfbcce)**

Thank you all!

---

### Post by Aghosh993 on 2008-06-20
Hi,
I'm trying to install gloobus on my Ubuntu 7.10 laptop. I did exactly what you instructed in the README file (running install.sh in su mode, and installing the dependencies). However, when I try to use gloobus mode in nautilus, the window pops up for about 1/2 second, and then disappears. Also, when I try running gloobus as sudo from terminal, I get:
abhi@ubuntu:~/Desktop/RELEASE$ sudo ./gloobus ~/Desktop
LOADING PLUGINS:
         /usr/share/gloobus/plugins/iFolder.so
         /usr/share/gloobus/plugins/iMp3.so
         /usr/share/gloobus/plugins/iPdf.so
Error loading Plugin: libMagick++.so.10: cannot open shared object file: No such file or directory

Ideas?
Thanks

---

### Post by badchoice on 2008-06-20
You need imagemagick installed, try:

```
sudo apt-get install imagemagick 
```

If it solves you problem please tell me and I will add it to the README file

---

### Post by pt123 on 2008-06-20
Just installed the binary release of 0.22 below are some comments:
* it works a lot smoother now but the CPU% always reaches 100% and will stay there even if you don't do anything. This happens with compiz on or off, the directory had 5 images.
Edit: strangely even if it is at 100% everything else is very useable, not sure if this is because of the hyperthreading on my old cpu. 

*large image directories stalls it. The CPU% reaches 190% and the application becomes unusable. So I am wondering is there any limiting used currently like only caching 15 thumbnails.
Edit: After seeing the terminal output it is caching all the images.

* also is it possible to skip the directories when displaying the first thumbnail, so an image is displayed rather than a row of orange folders.

*is there a way to start it up in a terminal to see some output, which might assist you in finding bugs.
Edit: found it :)

Keep up the good work.

---

### Post by Aghosh993 on 2008-06-20
Nope, still gives me the same error message when I try to run it within terminal as su. Also, same response in nautilus.

---

### Post by Exsecrabilus on 2008-06-20
Badchoice, you should make your own blog or forums for people to keep track of this project.

All the information on the two different topics on these forums and the first post not being updated frequently is kind of frustrating.

---

### Post by zekopeko on 2008-06-21
we need desktop integration for gloobus. stuff like default fonts in coverflow and custom icons for folders if they are specified or just use icon themes of gnome/kde.
that would be awesome

---

### Post by badchoice on 2008-06-22
Version 0.023 is Out!!
You can download it from here:
[https://launchpad.net/gloobus/+download](https://launchpad.net/gloobus/+download)

And the screencast:
[http://www.youtube.com/watch?v=OauVAOuUnXQ](http://www.youtube.com/watch?v=OauVAOuUnXQ)

Donations:
**[http://widget.chipin.com/widget/id/0b88c464e8dfbcce](http://widget.chipin.com/widget/id/0b88c464e8dfbcce)**


Aghosh993: Try with:
```
sudo apt-get install libmagick10
```
And tell me if it works :P

Exsecrabilus:
good idea, I'll create a gloobus.blogspot.com account :D

Zekopeko:
Yes, I have planed to do this when no plugin is found, use the theme icon, but now I don't know how to use theme icons.. I'll do some research :D

---

### Post by Exsecrabilus on 2008-06-22
> **badchoice said:**
> Version 0.023 is Out!!
You can download it from here:
[https://launchpad.net/gloobus/+download](https://launchpad.net/gloobus/+download)

And the screencast:
[http://www.youtube.com/watch?v=OauVAOuUnXQ](http://www.youtube.com/watch?v=OauVAOuUnXQ)

Donations:
**[http://widget.chipin.com/widget/id/0b88c464e8dfbcce](http://widget.chipin.com/widget/id/0b88c464e8dfbcce)**


Aghosh993: Try with:
```
sudo apt-get install libmagick10
```
And tell me if it works :P

Exsecrabilus:
good idea, I'll create a gloobus.blogspot.com account :D

Zekopeko:
Yes, I have planed to do this when no plugin is found, use the theme icon, but now I don't know how to use theme icons.. I'll do some research :D
That's so hot, I think it looks really awesome. XD

---

### Post by Aghosh993 on 2008-06-23
The terminal output gives me "can't find package libmagick10". 
Ideas?
Thx.

---

### Post by Exsecrabilus on 2008-06-23
> **Aghosh993 said:**
> The terminal output gives me "can't find package libmagick10". 
Ideas?
Thx.
In the README.txt, near the end, he tells to run the following command:
```
sudo apt-get install ?????, ?????, ?????, etc.
```
Open up the Terminal and copy and paste that.

---

### Post by quinnten83 on 2008-06-23
On a completely unrelated note, I would love it if you could actually implement a coverflow for rhythmbox, that is if you can find some time in your busy schedule. There is a dude already working on this, but his seems still a bit buggy.

---

### Post by Islington on 2008-06-23
[http://digg.com/linux_unix/Gloobus_a_QuickLook_for_Linux](http://digg.com/linux_unix/Gloobus_a_QuickLook_for_Linux)

Posted on Digg. Help digg it up!

---

### Post by tretle on 2008-06-23
This looks awesome. How do you fetch the album art.. Would it be a good idea to create a new thumbnail view for album art in nautilus based off it and this would be 100% perfect if it was integrated into the nautilus widget instead of creating a new one... For the coverflow effect that is. The quicklook widget is perfect the way it is now :D :P Great work... Thanks for the contribution.

---

### Post by Hells_Dark on 2008-06-23
> gloobus ~/Image
LOADING PLUGINS:
	 /usr/share/gloobus/plugins/iFolder.so
	 /usr/share/gloobus/plugins/iMp3.so
Error loading Plugin: /usr/share/gloobus/plugins/iMp3.so: cannot open shared object file: Permission denied
zsh: exit 255   gloobus ~/Image
I always have that :/

(ho, and if somebody could detail the nautilus-action part, i din't really understand it)

EDIT : resolved with a 
> sudo chmod 755 /usr/share/gloobus/plugins/iMp3.so

But now..
> Creating iText...
FILE: ./.zsnes
FileType: application/x-not-regular-file
Creating iFolder...
		Thread
Loading Folder Cover: ./Auto/cover.jpg
Loading no Folder Cover: nofolder.jpg
zsh: **segmentation fault**  gloobus .

EDIT 2 : i had to do the same for preview :
> sudo chmod 755 /usr/bin/preview 

But (again) :
> preview .
LOADING PLUGINS:
	 /usr/share/gloobus/plugins/iFolder.so
	 /usr/share/gloobus/plugins/iMp3.so
	 /usr/share/gloobus/plugins/iPdf.so
	 /usr/share/gloobus/plugins/iPhoto.so
	 /usr/share/gloobus/plugins/iText.so
FileType: application/x-not-regular-file
Using Plugin:iFolder
Creating iFolder...
Loading Folder Cover: ./cover.jpg
Loading no Folder Cover: nofolder.jpg
zsh: **segmentation fault**  preview .


---

### Post by 16777216 on 2008-06-23
I get the same.

---

### Post by Hells_Dark on 2008-06-23
It's a chmod problem.
Just enter something like 

> sudo chmod 755 /usr/share/gloobus/*

;)

---

### Post by hotweiss on 2008-06-23
> **Hells_Dark said:**
> It's a chmod problem.
Just enter something like 



;)

hmmm, that might solve another problem that I was having...

---

### Post by hotweiss on 2008-06-23
> **Hells_Dark said:**
> It's a chmod problem.
Just enter something like 



;)

This actually didn't work. Even when I used gksudo nautilus, I did not get an option to give myself permission.

I also got this error when running it as root:

> 
LOADING PLUGINS:
	 /usr/share/gloobus/plugins/iFolder.so
	 /usr/share/gloobus/plugins/iMp3.so
	 /usr/share/gloobus/plugins/iPdf.so
	 /usr/share/gloobus/plugins/iPhoto.so
	 /usr/share/gloobus/plugins/iText.so
FILE: .//--
FileType: application/octet-stream
This filetype has no preview function
FILE: .//bin
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//Desktop
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//Documents
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//Dogville
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//Downloads
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//Music
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//Pictures
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//Projects
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//Templates
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//Videos
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//Warcraft III
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//..
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//openSUSE-11.0-RC1-GNOME-LiveCD-i386-iso
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//openSUSE-11.0-RC1-KDE4-LiveCD-i386-iso
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//ies4linux-2.99.0.1
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.gstreamer-0.10
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.gimp-2.4
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.adobe
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.bash_history
FileType: text/plain; charset=us-ascii
Creating iText...
FILE: .//.bash_logout
FileType: text/plain; charset=us-ascii
Creating iText...
FILE: .//.bashrc_vanilla
FileType: text/plain; charset=us-ascii
Creating iText...
FILE: .//dsdt.bin
FileType: text/plain; charset=us-ascii
Creating iText...
FILE: .//.cache
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.checkgmail
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.config
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//dsdt.dat
FileType: application/octet-stream
This filetype has no preview function
FILE: .//.dbus
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.dmrc
FileType: text/plain; charset=us-ascii
Creating iText...
FILE: .//.dvdcss
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.emerald
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.esd_auth
FileType: application/octet-stream
This filetype has no preview function
FILE: .//GarminKey_Parser.exe
FileType: application/x-dosexec\012-  application/octet-stream\012- application/octet-stream
This filetype has no preview function
FILE: .//Keygen v1.3.exe
FileType: application/x-dosexec\012-  application/octet-stream\012- application/octet-stream
This filetype has no preview function
FILE: .//.fontconfig
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.gconf
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.gconfd
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.gnome
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.gnome2
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.gnome2_private
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.gnupg
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.gvfs
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted


---

### Post by Islington on 2008-06-23
how do I create the nautilus scripts? I installed nautilus action and launched nautilus-actions-config. I added the 2 commands and gave them a name and such. Now what?

---

### Post by hotweiss on 2008-06-23
> **Islington said:**
> how do I create the nautilus scripts? I installed nautilus action and launched nautilus-actions-config. I added the 2 commands and gave them a name and such. Now what?

you can just type gksudo nautilus in terminal

---

### Post by Islington on 2008-06-23
I did that. I see no different options being present..

---

### Post by hotweiss on 2008-06-23
> **Islington said:**
> I did that. I see no different options being present..

You won't find any new options, you will just be able to perform that options that you did not have permission to perform before. What options are you looking for?

---

### Post by Islington on 2008-06-23
doesnt seem to work for me...

```

islington@Theta:~$ gloobus %d /home/islington/Pictures/sticker.png
LOADING PLUGINS:
	 /usr/share/gloobus/plugins/iFolder.so
	 /usr/share/gloobus/plugins/iMp3.so
	 /usr/share/gloobus/plugins/iPdf.so
	 /usr/share/gloobus/plugins/iPhoto.so
	 /usr/share/gloobus/plugins/iText.so
FILE: .//compiz-git
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//Desktop
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//Documents
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//Games
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//Music
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//Pictures
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//Programs
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//Projects
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//Videos
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//..
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.gtkrc-2.0-kde
FileType: text/plain; charset=us-ascii
Creating iText...
FILE: .//.gtkrc-2.0-kde4
FileType: text/plain; charset=us-ascii
Creating iText...
FILE: .//.gstreamer-0.10
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.gimp-2.4
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.adobe
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.ardour2
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.bash_history
FileType: text/plain; charset=us-ascii
Creating iText...
FILE: .//.bash_logout
FileType: text/plain; charset=us-ascii
Creating iText...
FILE: .//.bashrc
FileType: text/plain; charset=us-ascii
Creating iText...
FILE: .//.cache
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.xscreensaver-getimage.cache
FileType: text/plain; charset=us-ascii
Creating iText...
FILE: .//.comix
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.compiz-git
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.fonts.conf
FileType: text/xml
This filetype has no preview function
FILE: .//.config
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.cvspass
FileType: application/x-empty
This filetype has no preview function
FILE: .//.dbus
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.dmrc
FileType: text/plain; charset=us-ascii
Creating iText...
FILE: .//.e
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.e17_cvs
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.easytag
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.elisa
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.emerald
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.esd_auth
FileType: application/octet-stream
This filetype has no preview function
FILE: .//.face
FileType: image/png
This filetype has no preview function
FILE: .//.FBReader
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.fontconfig
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.fr-nqQyKi
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.fr-sdo4ip
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.gconf
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.gconfd
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.gnome
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.gnome2
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.gnome2_private
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.gnupg
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.gtk-bookmarks
FileType: text/plain; charset=us-ascii
Creating iText...
FILE: .//.gtk_qt_engine_rc
FileType: text/plain; charset=us-ascii
Creating iText...
FILE: .//.gvfs
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//compiz-git-newest.tar.gz
FileType: application/x-gzip
This filetype has no preview function
FILE: .//.ICEauthority
FileType: application/octet-stream
This filetype has no preview function
FILE: .//.icons
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.inkscape
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.jackdrc
FileType: text/plain; charset=us-ascii
Creating iText...
FILE: .//.java
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.kderc
FileType: text/plain; charset=us-ascii
Creating iText...
FILE: .//.local
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.gksu.lock
FileType: application/x-empty
This filetype has no preview function
FILE: .//.macromedia
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.mcop
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.mcoprc
FileType: text/plain; charset=us-ascii
Creating iText...
FILE: .//.metacity
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.miro
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.mozilla
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.nautilus
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.openoffice.org2
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.prism
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.profile
FileType: text/plain; charset=us-ascii
Creating iText...
FILE: .//.pulse
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.pulse-cookie
FileType: application/octet-stream
This filetype has no preview function
FILE: .//.purple
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.qemu_history
FileType: application/x-empty
This filetype has no preview function
FILE: .//.qt
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.recently-used
FileType: text/xml
This filetype has no preview function
FILE: .//.registry
FileType: application/octet-stream
This filetype has no preview function
FILE: .//.screenlets
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.songbird1
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.songbird2
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.ssh
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.subversion
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.sudo_as_admin_successful
FileType: application/x-empty
This filetype has no preview function
FILE: .//.synaptic
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.themes
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.thumbnails
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.transmission
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.update-manager-core
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.update-notifier
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.usp
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.VirtualBox
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.wallpapoz
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.wapi
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.wine
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.Xauthority
FileType: video/unknown
This filetype has no preview function
FILE: .//.recently-used.xbel
FileType: text/xml
This filetype has no preview function
FILE: .//.xine
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.xsession-errors
FileType: text/x-pascal; charset=us-ascii
This filetype has no preview function
		Thread
Loading Folder Cover: .//compiz-git/cover.jpg
Loading no Folder Cover: nofolder.jpg
Segmentation fault

```

---

### Post by Aghosh993 on 2008-06-23
I know, I did exactly the steps outlined in his README file, including getting all the dependencies, which is why I'm puzzled by this error message. 
Anyone here have an idea about the libMagick10.so file and what exactly it does?
Thx,
Aghosh993

---

### Post by hotweiss on 2008-06-23
> **Islington said:**
> doesnt seem to work for me...

```

islington@Theta:~$ gloobus %d /home/islington/Pictures/sticker.png
LOADING PLUGINS:
	 /usr/share/gloobus/plugins/iFolder.so
	 /usr/share/gloobus/plugins/iMp3.so
	 /usr/share/gloobus/plugins/iPdf.so
	 /usr/share/gloobus/plugins/iPhoto.so
	 /usr/share/gloobus/plugins/iText.so
FILE: .//compiz-git
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//Desktop
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//Documents
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//Games
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//Music
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//Pictures
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//Programs
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//Projects
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//Videos
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//..
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.gtkrc-2.0-kde
FileType: text/plain; charset=us-ascii
Creating iText...
FILE: .//.gtkrc-2.0-kde4
FileType: text/plain; charset=us-ascii
Creating iText...
FILE: .//.gstreamer-0.10
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.gimp-2.4
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.adobe
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.ardour2
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.bash_history
FileType: text/plain; charset=us-ascii
Creating iText...
FILE: .//.bash_logout
FileType: text/plain; charset=us-ascii
Creating iText...
FILE: .//.bashrc
FileType: text/plain; charset=us-ascii
Creating iText...
FILE: .//.cache
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.xscreensaver-getimage.cache
FileType: text/plain; charset=us-ascii
Creating iText...
FILE: .//.comix
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.compiz-git
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.fonts.conf
FileType: text/xml
This filetype has no preview function
FILE: .//.config
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.cvspass
FileType: application/x-empty
This filetype has no preview function
FILE: .//.dbus
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.dmrc
FileType: text/plain; charset=us-ascii
Creating iText...
FILE: .//.e
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.e17_cvs
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.easytag
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.elisa
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.emerald
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.esd_auth
FileType: application/octet-stream
This filetype has no preview function
FILE: .//.face
FileType: image/png
This filetype has no preview function
FILE: .//.FBReader
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.fontconfig
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.fr-nqQyKi
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.fr-sdo4ip
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.gconf
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.gconfd
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.gnome
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.gnome2
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.gnome2_private
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.gnupg
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.gtk-bookmarks
FileType: text/plain; charset=us-ascii
Creating iText...
FILE: .//.gtk_qt_engine_rc
FileType: text/plain; charset=us-ascii
Creating iText...
FILE: .//.gvfs
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//compiz-git-newest.tar.gz
FileType: application/x-gzip
This filetype has no preview function
FILE: .//.ICEauthority
FileType: application/octet-stream
This filetype has no preview function
FILE: .//.icons
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.inkscape
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.jackdrc
FileType: text/plain; charset=us-ascii
Creating iText...
FILE: .//.java
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.kderc
FileType: text/plain; charset=us-ascii
Creating iText...
FILE: .//.local
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.gksu.lock
FileType: application/x-empty
This filetype has no preview function
FILE: .//.macromedia
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.mcop
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.mcoprc
FileType: text/plain; charset=us-ascii
Creating iText...
FILE: .//.metacity
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.miro
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.mozilla
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.nautilus
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.openoffice.org2
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.prism
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.profile
FileType: text/plain; charset=us-ascii
Creating iText...
FILE: .//.pulse
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.pulse-cookie
FileType: application/octet-stream
This filetype has no preview function
FILE: .//.purple
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.qemu_history
FileType: application/x-empty
This filetype has no preview function
FILE: .//.qt
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.recently-used
FileType: text/xml
This filetype has no preview function
FILE: .//.registry
FileType: application/octet-stream
This filetype has no preview function
FILE: .//.screenlets
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.songbird1
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.songbird2
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.ssh
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.subversion
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.sudo_as_admin_successful
FileType: application/x-empty
This filetype has no preview function
FILE: .//.synaptic
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.themes
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.thumbnails
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.transmission
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.update-manager-core
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.update-notifier
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.usp
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.VirtualBox
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.wallpapoz
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.wapi
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.wine
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.Xauthority
FileType: video/unknown
This filetype has no preview function
FILE: .//.recently-used.xbel
FileType: text/xml
This filetype has no preview function
FILE: .//.xine
FileType: application/x-not-regular-file
Creating iFolder...
FILE: .//.xsession-errors
FileType: text/x-pascal; charset=us-ascii
This filetype has no preview function
		Thread
Loading Folder Cover: .//compiz-git/cover.jpg
Loading no Folder Cover: nofolder.jpg
Segmentation fault

```

Same error for me...

---

### Post by pt123 on 2008-06-24
I don't think gloobus does PNG files ATM.

---

### Post by davim on 2008-06-25
any news on the nautilus integration??

---

### Post by badchoice on 2008-06-25
Hey! that i think that the segmentation fault is because it can't load the nofolder.jpg

is the file nofolder.jpg in /usr/share/gloobus ??

if it is, run 

```
sudo chmod -R 777 /usr/share/gloobus/
```

And try again! :)

About nautilus integrations, there are still no news...

---

### Post by teolemon on 2008-06-25
For those who didn't follow the discussion, the question was asked by BadChoice, and he got the following answer: [http://mail.gnome.org/archives/nautilus-list/2008-June/msg00064.html](http://mail.gnome.org/archives/nautilus-list/2008-June/msg00064.html)

---

### Post by TheAL76 on 2008-06-25
This looks really great...I can't wait to go home and try it.

---

### Post by teolemon on 2008-06-25
More links :
[http://www.linux.com/articles/114134?page=3](http://www.linux.com/articles/114134?page=3) >> A tutorial on extending Nautilus
[http://developer.gnome.org/doc/whitepapers/nautilus/nautilus-internals.pdf](http://developer.gnome.org/doc/whitepapers/nautilus/nautilus-internals.pdf) >> An official documentation

---

### Post by prismpirate on 2008-06-26
Anyone know what the readme means when it says


3. With Nautilus-actions create two scripts
	coverflow: gloobus %d/
	preview  : preview %d/%f

I have no idea whatsoever on what to do at this step.

---

### Post by 16777216 on 2008-06-26
The Nautilus-actions extension enables you to add customized entries to the context menu such that, when you right-click a file, the context menu will show options specific to that file.

```
sudo apt-get install nautilus-actions
```Then **System > Preferences > Nautilus Actions Configuration**

And just add the lines mentioned in the readme.

I forgot to add the description was cut from this article   [http://www.linux.com/feature/119603](http://www.linux.com/feature/119603)

---

### Post by badchoice on 2008-06-26
Hey!! new version is out! 0.024

Its a very must one version!! it implements a lot of new things such multislide, png support, gloobus window rezisable and improvements!

[https://launchpad.net/gloobus/gloobus-0.02/0.02](https://launchpad.net/gloobus/gloobus-0.02/0.02)


Remember, donations: [http://widget.chipin.com/widget/id/0b88c464e8dfbcce](http://widget.chipin.com/widget/id/0b88c464e8dfbcce)

---

### Post by Choad on 2008-06-26
hmm it's kinda cool, but how come you can't traverse the filesystem? imo up should go in to the directory and down should move you "up" one directory (not that that makes much sense written like that but you know what i mean lol)

---

### Post by Le-Froid on 2008-06-26
> **Choad said:**
> hmm it's kinda cool, but how come you can't traverse the filesystem? imo up should go in to the directory and down should move you "up" one directory (not that that makes much sense written like that but you know what i mean lol)

/agree, extremely useful imo

By the way, gloobus is starting to work better/faster on my system with each release, thanks :)

---

### Post by Choad on 2008-06-26
oh and also use the gtk theme icons too! you'd stand a much better chance of it being added to nautilus if it conformed to the look and feel of the system.

---

### Post by zekopeko on 2008-06-26
could we get the preview window with out border like it used to be? or are you just experimenting with it?

i agree with choad. it would be cool to have default icons.

---

### Post by badchoice on 2008-06-27
Yes, I added it to see what you like more, now I'm doing a config file so you can choose you preferences there, I like it more without the border but some people asked me to add it so I'll put the two possibilites.

---

### Post by MadsRH on 2008-06-27
This is a great project! :)

Will this be stable and ready for 8.10, and will it be included by default?

[B]
//MadsRH[/B]

---

### Post by zombiepig on 2008-06-27
badchoice,

I'm eager to give gloobus a try, but i'm running into a couple of problems:

- If I download the compiled snapshots, I can install, but always get a "error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory" when I try to launch. I think this may be because I'm using a 64 bit...
- If I download the sources, I can't work out the correct method to compile them. It seems I can run 'make' in each subdirectory of the project (but this fails on the plugins). Is there a proper way to compile the whole project yet?

Hope you can help!

---

### Post by spg76 on 2008-06-27
> **badchoice said:**
> Yes, I added it to see what you like more, now I'm doing a config file so you can choose you preferences there, I like it more without the border but some people asked me to add it so I'll put the two possibilites.

I like it more with the border, that way you can move the preview window. It's great that you add the two options, so the user can choose.
It possible to add more options, like view in full screen, open with..., add to F-Spot, etc.? You know, like in [Quick Look]("http://www.apple.com/macosx/features/quicklook.html").
Anyway, Great work!

---

### Post by Hells_Dark on 2008-06-27
> **spg76 said:**
> I like it more with the border, that way you can move the preview window.
Use **alt**

But i agree, it's better with the choice.

---

### Post by pt123 on 2008-06-27
0.24 is a great update, so much faster and smoother. 

I also like how it doesn't try and grab previews of all the images in a folder, this really helps large folders.

Still not sure why CPU usage for it is around 95%, but other programs are able to function without hinderance. 

There seems to be a bug for wide images. The thumbnails for them seem to be a much lower quality. Attached a screenshot.

Thanks

---

### Post by tretle on 2008-06-27
An irc channel should be started, this way developers will be more likely to help out and users can get help faster.

---

### Post by badchoice on 2008-06-28
Choad: it's a good idea! I would like to integrate it with nautilus but I get no response from them... anyway I can implement this two functions (DOWN to enter a directory, UP to go to parent directory).
There will be a good option to add enter key to launch the default program but I don't know how to do it.

Abut the gtk theme icons, its a good idea, I would like to do that if a file has no preview, it just loads the icon from theme.. but I still don't know how to do it :D

MadsRH: I don't think it will be included by default, anyway there is still a lot of work to do for this to be totaly functinally and without bugs... but, I would like to see it on the main ubuntu version :D

zombiepig: There is still not a complete makefile so you have to compile each one, just gloobus, preview and the plugins. What errors do the plugins compilation gives to you?

spg76: I'll add the option to show or not the border in the config file, now in the version 0.023 (last update) there is a config file for gloobus you can change some values like angles, speed, size of the window, front view angle...

pt123: You're right, There is a problem with the wide images cause I scale down all the photos to use less memory, but the wide ones are scaled more than what they can...

tretle: Feel free to star the chanel, I don't know how it works, do I only have to joint to #gloobus?

---

### Post by zekopeko on 2008-06-28
could you scale the images less? they look really fuzzy for me.
also what is up with the insane CPU usage? you said something about a main() loop using all the processor it can so i was wondering if you'll fix this soon.

---

### Post by pt123 on 2008-06-28
> **badchoice said:**
> Choad: it's a good idea! I would like to integrate it with nautilus but I get no response from them... anyway I can implement this two functions (DOWN to enter a directory, UP to go to parent directory).
There will be a good option to add enter key to launch the default program but I don't know how to do it.
That would be awesome.

> 
version 0.023 (last update) there is a config file for gloobus you can change some values like angles, speed, size of the window, front view angle...

Would it be possible if the config file was in the users home directory ~/.gloobus/config file ?

---

### Post by zekopeko on 2008-06-28
> **pt123 said:**
> That would be awesome.


Would it be possible if the config file was in the users home directory ~/.gloobus/config file ?

~/.config/gloobus

is freedesktop standard so we should use it

---

### Post by badchoice on 2008-06-28
Yeah, you're right! I'll do it ;)

---

### Post by b3n87 on 2008-06-28
Hi guys, just had a play with this and it looks awesome.

I get 99% on both processors tho but i think your already aware of that.

btw if anyone is reading this and wants to install it you need these dependencies

```

sudo apt-get install libsdl-mixer1.2-dev libsdl1.2-dev libsdl-ttf2.0-dev libsdl-image1.2-dev libmagick++9-dev libmagic-dev libtag1-dev libsdl-gfx1.2-dev

```

---

### Post by zombiepig on 2008-06-30
badchoice, I got gloobus compiled and it's looking really nice :)

I've got a couple of suggestions/thoughts to throw your way, they may be useful or I might be way off track :P

Firstly, IMO it'd make sense to spilt gloobus off into two projects - one which handles the preview function, the other which handles the cover flow function. 

Then, the cover flow project could be modified to use the freedesktop thumbnail spec ([http://people.freedesktop.org/~vuntz/thumbnail-spec-cache/](http://people.freedesktop.org/~vuntz/thumbnail-spec-cache/)). This is the same spec nautilus uses for it's thumbnailing. Following this would mean files thumbnailed in gloobus would have a thumbnail available immediately in nautilus, and vice versa. It'd also save a bunch of work re-creating thumbnailers that other applications already have available. 
For example, installing Comix installs a thumbnailer for all cbr/cbz comic book files. This would instantly give gloobus a method for thumbnailing these file types, with no extra work :) Or, installing the openoffice thumbnailer ([http://ubuntuforums.org/showthread.php?t=76566](http://ubuntuforums.org/showthread.php?t=76566)) would give gloobus thumbnails for all open office documents!

Unfortunately, I don't think the same kind of approach could work for the quick preview function, because the fdo 'large' thumbnails are only 256x256 pixels. That's why I suggested splitting the project into two components. So the focus for the cover flow would be on the graphic effects for navigating through the thumbnails, and the focus on the preview app would be fast, higher-resolution previews.

What do you think?

---

### Post by badchoice on 2008-06-30
zombiepig: Thanks for your comment, I have to say that now the project is split in two parts, as you said, is not the same how you preview a file and how it looks on coverflow.

Gloobus(Coverflow) and Preview now uses plugins and each plugin can implement his own method for gloobus and for preview, so it will be very easy to modify them for use the thumbnails created by nautilus.

I'll take a look at it and see if I can modify the iPhoto plugin to use it, but I don't know if the thumbnail size will be good for the coverflow because now it can be resized to fullscreen and the picture will look very bad...

Anyway, It can store the previews in the nautilus thumnails folder.

See you!

---

### Post by aantn on 2008-07-02
Is there any chance that you can include a makefile or at least some instructions for compiling?

The install script doesn't work with the current revision on bzr (you renamed the folders and forgot to change them in the script) and the tarballs contain i386 binaries.

I know that make can be a pain and coding is a lot more exciting, but you really need to fix things like this if you want to attract other developers.

---

### Post by zekopeko on 2008-07-11
any progress?

---

### Post by teolemon on 2008-07-13
I've filed a bug in Gnome's bugzilla about a "View as Coverflow" mode, asking for help on Nautilus integration, and I sent as well a mail to Christian Neumair.
[http://bugzilla.gnome.org/show_bug.cgi?id=542752](http://bugzilla.gnome.org/show_bug.cgi?id=542752)

Badchoice:
I've found the Nautilus-extension thingie that was talked about on nautilus-list:
[http://svn.gnome.org/viewvc/nautilus/trunk/libnautilus-extension/](http://svn.gnome.org/viewvc/nautilus/trunk/libnautilus-extension/)

By the way, be sure to check the research I've done on the blueprint @
[https://blueprints.edge.launchpad.net/gloobus/+spec/nautilus-integration](https://blueprints.edge.launchpad.net/gloobus/+spec/nautilus-integration)

Note that you can also develop Gloobus by branching the source code in Launchpad if you know how to code

---

### Post by badchoice on 2008-07-13
Hey! thanks for the researched, I readed about it, the main problem I have is that i need to integrate a GL windows in nautilus... anyway these days I've been busy with other things and I didn't do much work, now I ready again and with a friend of mine that will help me in developing it.

By the way there is the new link for donations:

[https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=guitarboy000%40gmail%2ecom&item_name=Gloobus%2c%20A%20Quicklook%20for%20linux&no_shipping=0&no_note=1&tax=0&currency_code=EUR&lc=US&bn=PP%2dDonationsBF&charset=UTF%2d8](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=guitarboy000%40gmail%2ecom&item_name=Gloobus%2c%20A%20Quicklook%20for%20linux&no_shipping=0&no_note=1&tax=0&currency_code=EUR&lc=US&bn=PP%2dDonationsBF&charset=UTF%2d8)


I'll inform you about the new progress!

---

### Post by zekopeko on 2008-07-13
ok not to undermine the effort here... but how about rewriting gloobus in clutter? 
now i'm far from an openGL expert but clutter is the new red :D
macslow is using it for the openGL GDM face browser and stuff. now the main point is that clutter offers/will offer? gtk+ widgets (i'm guessing those are what you need to embed it in nautilus?). and apparently is super easy to work with. and it just might be in GTK+ 3 and GNOME 3 so we can get some fancy app effects in gtk+ programs.

---

### Post by dracule on 2008-07-13
I would prefer it if we could have an option for non-coverflow. like just a normal file browser, but when you hover your mouse it gives you a nice large preview.

coverflow for large number of documents would be hard.

---

### Post by badchoice on 2008-07-14
Hey I looked this clutter and It seems really good, I'll take a closer look and see if it can do what I want, I hope it Can, I'll start with preview and if everything is fine, then I'll port gloobus.

Thanks.

Btw, you can preview the files without coverflow, just use nautilus-actions to add the " preview <file>"

---

### Post by teolemon on 2008-07-14
From the research I've done:
Clutter would be more GNOME-ish but the main problem won't lie there (see C.Neumair's response on the bug): it seems that Nautilus integration is not just making it a Nautilus widget. It's also about stacking it and coordinating it with the rest of Nautilus.
my guess would be to have a look at how icon and list view are done and try to modify the code. 
For stacking , I'd say use code made to draw either the toolbar or the sidebar , change the size and stack the Gloobus widget into it. But that must be a dirty solution, and I'm not even sure it is feasible.

@badchoice:
You may want to contact rainwoodman . He's not working on Nautilus, but he has learned a great deal by working on Gnomenu (Gnome Global's menu, a Mac-like menubar).
He's also really busy, but he's also a fan of the document centric approach.

---

### Post by kinap on 2008-07-14
can you please make a binary release (or anyone else) for ubuntu hardy 64bit
some plugins i can compile but some not.

as i can't seem to get the ffmpeg sources anymore

 sudo apt-get install libavcodec-dev libpostproc-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libavcodec-dev: Depends: libavcodec1d (= 3:0.cvs20070307-5ubuntu7) but 3:0.cvs20070307-5ubuntu7+medibuntu1 is to be installed
                  Depends: libavutil-dev (= 3:0.cvs20070307-5ubuntu7) but it is not going to be installed
  libpostproc-dev: Depends: libpostproc1d (= 3:0.cvs20070307-5ubuntu7) but 3:0.cvs20070307-5ubuntu7+medibuntu1 is to be installed
E: Broken packages


Felix

btw it works great on my 32 bit hardy

Felix

---

### Post by badchoice on 2008-07-15
From now you don't need the ffmpeg packages cause I haven't coded the iMovie plugins, so you can skip this part!

If you can compile it on your 64bits box, can you send me the binaries? I'll upload them with the 32bits version on launchpad! 

Thanks!

---

### Post by kahlil88 on 2008-07-15
Awesome! Let's hope you don't get sued for patent infringement. I sure hate [software patents]("http://www.endsoftpatents.org").

---

### Post by ryanhaigh on 2008-07-23
Im VERY happy to report that gloobus 0.024 works perfectly on Gutsy with only a very minor modification to the installation process. For gutsy the libMagick++10 package is not available with the closest available version being libmagick++9c2a so you need to change the dependancy installation from this

```
sudo apt-get install libsdl-mixer1.2 libsdl1.2debian libsdl-ttf2.0-0 libsdl-image1.2 libmagick++10 libmagic1 libtag1c2a libavcodec1d libavformat1d libswscale1d libsdl-gfx1.2-4
```

To this 
```

sudo apt-get install libsdl-mixer1.2 libsdl1.2debian libsdl-ttf2.0-0 libsdl-image1.2 **libmagick++9c2a** libmagic1 libtag1c2a libavcodec1d libavformat1d libswscale1d libsdl-gfx1.2-4
```

Once those packages are finished installing create a symbolic link to the .9 library from the .10 file that gloobus/preview look for 

```
sudo ln -s /usr/lib/libMagick++.so.9 /usr/lib/libMagick++.so.10
```

Proceed with the rest of the installation as normal and you have working (much better than in a VM) gloobus and preview.

---

### Post by Prefix100 on 2008-07-23
This is so awesome.

It would be nicer if it was integrated though.

Great Job!

---

### Post by badchoice on 2008-07-23
Thanks for you report! as soon as I get home I'll include the modifications on the installation for gutsy!!

I'v marked as solved the other thread so now this is the good one!

Thank you so much!

---

### Post by ryanhaigh on 2008-07-24
Just tried using the app with my music collection and its great! I use list view in nautilus and so the audio preview (by holding the mouse over the icon) isn't available to me but this makes it a lot easier to find the track I am looking for when I don't know the name of the track. A couple of ideas occurred to me whilst using this feature:

[LIST]
[*]Up/Down keys scroll through documents in preview can these keys be used to skip ahead in songs/movies?

[*]Most of my music doesn't have embedded cover art (half of it isn't even tagged well), I thought rather than use a static and identical icon for all tracks you might be able to create/read thumbnails created by this application: [http://ubuntuforums.org/showthread.php?p=4477668](http://ubuntuforums.org/showthread.php?p=4477668)
[/LIST]

---

### Post by badchoice on 2008-07-25
Coses,
Its a good idea that left-right keys loads next file in preview (for photos 
For the files without cover i use the cover.jpg file that is in the same folder, so this way you can have a folder with all albums each one with its cover.

By the way, I don't think that add a extern software preview funcion is the best way cause there are users that don't have or don't want it... but if its a very requested feature I can try to add it.

Thank for you comment and idea.

---

### Post by cozmicharlie on 2008-07-25
I can't seem to get this working.  I have the entry for coverflow and preview when I right click.  However, nothing happens when I select them.  I tried running gloobus in terminal ($ sudo gloobus) and I get an error that reads 

"gloobus: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory"

The . symbolic link /usr/liblibsdl_image-1.2.so and the shared library /usr/lib/libSDL_image-1.2.so.0.1.5 are installed.  For some reason Gloobus is not recognizing it - probably something to do with permissions but I beleive I changed them as recommended in the thread so I am at a loss.

Thanks for the help.

---

### Post by adamogardner on 2008-07-25
cosmikcharlie.  how do you do?....

---

### Post by ryanhaigh on 2008-07-25
It seems as though the files you have installed and the file gloobus is looking for are different, note the end of the filenames:

> **cozmicharlie said:**
> 
"gloobus: error while loading shared libraries: libSDL_image-1.2.so**.0:** cannot open shared object file: No such file or directory"

The . symbolic link /usr/liblibsdl_image-1.**2.so** and the shared library /usr/lib/libSDL_image-1.2.so**.0.1.5** are installed.

According to [ubuntu package search]("http://packages.ubuntu.com/search?searchon=contents&keywords=libSDL_image-1.2.so.0&mode=exactfilename&suite=hardy&arch=any") the package you need to install is [apt://libsdl-image1.2]("apt://libsdl-image1.2")

---

### Post by cozmicharlie on 2008-07-26
> **ryanhaigh said:**
> It seems as though the files you have installed and the file gloobus is looking for are different, note the end of the filenames:



According to [ubuntu package search]("http://packages.ubuntu.com/search?searchon=contents&keywords=libSDL_image-1.2.so.0&mode=exactfilename&suite=hardy&arch=any") the package you need to install is [apt://libsdl-image1.2]("apt://libsdl-image1.2")

When I click on the link you provided (apt://libsdl-image1.2"]apt://libsdl-image1.2) - it says "package already installed".  

When I check the files ([http://packages.ubuntu.com/hardy/amd64/libsdl-image1.2/filelist](http://packages.ubuntu.com/hardy/amd64/libsdl-image1.2/filelist)) - this is what they list.  These are the same as what I have isntalled on my system.
/usr/lib/libSDL_image-1.2.so.0
/usr/lib/libSDL_image-1.2.so.0.1.5
/usr/share/doc/libsdl-image1.2/README
/usr/share/doc/libsdl-image1.2/changelog.Debian.gz
/usr/share/doc/libsdl-image1.2/changelog.gz
/usr/share/doc/libsdl-image1.2/copyright

The version I installed from Synaptic is listed as 1.2.6-3 hardy.

Not sure what else I can do.  Looks like the right version is installed.

I appreciate your help.

---

### Post by teolemon on 2008-07-26
[http://www.cooliris.com/](http://www.cooliris.com/)
Just wanted to share this, and though inspiration could be taken from it.

---

### Post by artir on 2008-07-26
Nice project!

However, I cannot see my album covers, just the generic icon AND I can't see the .ogg files (90% of my music is .ogg) You can use some kind of fetching system like rhytmbox or just get the pictures from the rhytmbox folder.
And the ogg support should be easy to implement too.

---

### Post by ryanhaigh on 2008-07-26
cozmicharlie does the error still occur if you start the program as root?

```
sudo gloobus ~/
```

---

### Post by cozmicharlie on 2008-07-27
> **ryanhaigh said:**
> cozmicharlie does the error still occur if you start the program as root?

```
sudo gloobus ~/
```

Yes - I get the same error.  I loaded it onto another computer I have and got it to work.  The one it does not work on is an HP AMD64 laptop - if that matters.  

Also, FYI the install scripts comes back with error messages that their is no folder plugins" or "data.  It did create the etc/gloobus folder but neither the plugin or data folder was created.  I have to manually create the folders and move the files to them and change the permissions on all the binaries etc as per the thread.  I believe the script should do that - is that correct?

---

### Post by badchoice on 2008-07-28
**cozmicharlie:**

To run gloobus you must execute the install script as root, anyway, you can do it manually so create 
[B]/usr/share/gloobus 
/urs/share/gloobus/plugins[/B]

copy the files inside DATA folder on /usr/share/gloobus
and copy de plugins *.so into /usr/share/gloobus/plugins

this is all the files it needs to run, if it shows errors of dependeces install all libraries that readme says, if you use gusty, use the ryanhaigh trick in a previous post.

If you still have problems...

________________________________________________________
**artir: **For ogg files I think I can add it easyli, so please, **create a bug into launchpad**, so this way I won't forget!! 

Thanks and remember:
**Donate: [https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=guitarboy000%40gmail%2ecom&item_name=Gloobus%2c%20A%20Quicklook%20for%20linux&no_shipping=0&no_note=1&tax=0&currency_code=EUR&lc=US&bn=PP%2dDonationsBF&charset=UTF%2d8](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=guitarboy000%40gmail%2ecom&item_name=Gloobus%2c%20A%20Quicklook%20for%20linux&no_shipping=0&no_note=1&tax=0&currency_code=EUR&lc=US&bn=PP%2dDonationsBF&charset=UTF%2d8)**

---

### Post by teolemon on 2008-07-28
Bug reported for Ogg + another one about the 0.24 announcement

---

### Post by cozmicharlie on 2008-07-28
> **badchoice said:**
> **cozmicharlie:**

To run gloobus you must execute the install script as root, anyway, you can do it manually so create 
[B]/usr/share/gloobus 
/urs/share/gloobus/plugins[/B]

copy the files inside DATA folder on /usr/share/gloobus
and copy de plugins *.so into /usr/share/gloobus/plugins

this is all the files it needs to run, if it shows errors of dependeces install all libraries that readme says, if you use gusty, use the ryanhaigh trick in a previous post.

If you still have problems...

________________________________________________________
**artir: **For ogg files I think I can add it easyli, so please, **create a bug into launchpad**, so this way I won't forget!! 

Thanks and remember:
**Donate: [https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=guitarboy000%40gmail%2ecom&item_name=Gloobus%2c%20A%20Quicklook%20for%20linux&no_shipping=0&no_note=1&tax=0&currency_code=EUR&lc=US&bn=PP%2dDonationsBF&charset=UTF%2d8](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=guitarboy000%40gmail%2ecom&item_name=Gloobus%2c%20A%20Quicklook%20for%20linux&no_shipping=0&no_note=1&tax=0&currency_code=EUR&lc=US&bn=PP%2dDonationsBF&charset=UTF%2d8)**

I did run the script as root.  I will submit a bug report.  I was not sure if this was just something I was doing wrong or if others have the same experience (I guess that is what a bug report is for).

Thanks for your help

---

### Post by badchoice on 2008-07-30
What error do you have when running gloobus from console?

---

### Post by badchoice on 2008-07-30
Does anyone know hot to launch the default application in c++ i want to add that pressing the enter key, the file is opened with the default application.

However I'll serach throught the web and hope I find out how to do it!

During the next three weeks I've holidays so there won't be so much code update for the project. But I'll be reading this post and launchpad so you can keep contacting me!

See you!
Tahnks!

Donate: [https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=guitarboy000%40gmail%2ecom&item_name=Gloobus%2c%20A%20Quicklook%20for%20linux&no_shipping=0&no_note=1&tax=0&currency_code=EUR&lc=US&bn=PP%2dDonationsBF&charset=UTF%2d8](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=guitarboy000%40gmail%2ecom&item_name=Gloobus%2c%20A%20Quicklook%20for%20linux&no_shipping=0&no_note=1&tax=0&currency_code=EUR&lc=US&bn=PP%2dDonationsBF&charset=UTF%2d8)

---

### Post by cozmicharlie on 2008-07-30
> **badchoice said:**
> What error do you have when running gloobus from console?

Not sure if you meant this fore me or not.  If not then ignore this.

This is the error.

"gloobus: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory"

And as mentioned I have the correctly package installed.

---

### Post by badchoice on 2008-07-31
I've started a blog where I'll be posting news questions and other things...


**Blog: [http://gloobus.wordpress.com/](http://gloobus.wordpress.com/)**

---

### Post by spg76 on 2008-07-31
> **badchoice said:**
> I've started a blog where I'll be posting news questions and other things...


**Blog: [http://gloobus.wordpress.com/](http://gloobus.wordpress.com/)**

Great idea.
I'd read your request for a scrollbar and if I can I'll send you one later.
Keep up the good work!

---

### Post by EnGorDiaz on 2008-08-03
guys why dont you just make a gloobus compiz fusion plug in?

im using it its great 

compiz fusion plus nautilus plus gloobus = epic win

---

### Post by teolemon on 2008-08-03
That just doesn't make sense as it is supposed to be tightly integrated into Nautilus. It sure helps for the keystrokes though.

---

### Post by EnGorDiaz on 2008-08-03
> **teolemon said:**
> That just doesn't make sense as it is supposed to be tightly integrated into Nautilus. It sure helps for the keystrokes though.

well thats what i mean :P

---

### Post by tretle on 2008-08-04
[http://macslow.thepimp.net/?p=153](http://macslow.thepimp.net/?p=153)

---

### Post by EnGorDiaz on 2008-08-05
im not downgrading gtk i have to much software that runs gtk 2.0

---

### Post by badchoice on 2008-08-05
Hey! I've done a lot of work these days, In a few I'll update it into launchpad and explain it into the blog:

[http://gloobus.wordpress.com](http://gloobus.wordpress.com)

I've been looking into macslow post and I think that is a really good idea to joint gloobus into gtkext and cairo, I'll try to implement preview with it and if everything is ok, then I'll port gloobus itself!

Thanks!

---

### Post by badchoice on 2008-08-05
Hey!! Version 0.025 is out! there are some new features and bugs fixed:
you can download it from here:

[https://launchpad.net/gloobus/+download](https://launchpad.net/gloobus/+download)

	· New transition efect, now it uses x² functions instead of sqrt(x)
	· Arrows in gloobus
	· Pre scrollbar, you can navigate pressing a space between arrows
	· Preview Fullscreen, you can use F key or just use the icon below
	· Ogg music files support
	· preview binary on /usr/share/gloobus
	· Fixed the changetime bug

Please, take a look at my blog:

[http://gloobus.wordpress.com](http://gloobus.wordpress.com)

and remember that you can donate to keep this project going on!
[B]
Donate: [https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=guitarboy000%40gmail%2ecom&item_name=Gloobus%2c%20A%20Quicklook%20for%20linux&no_shipping=0&no_note=1&tax=0&currency_code=EUR&lc=US&bn=PP%2dDonationsBF&charset=UTF%2d8](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=guitarboy000%40gmail%2ecom&item_name=Gloobus%2c%20A%20Quicklook%20for%20linux&no_shipping=0&no_note=1&tax=0&currency_code=EUR&lc=US&bn=PP%2dDonationsBF&charset=UTF%2d8)[/B]

---

### Post by pikabuntu on 2008-08-05
Gloobus looked really cool, but I am having trouble getting it working.  When I choose "preview" nothing happens, and when I choose "coverflow" a black bar flashes on the screen and disappears...
What can I do to fix this?

---

### Post by badchoice on 2008-08-05
pikabuntu:
Launch it from console and send me the output

for preview in version 0.025:
/usr/share/gloobus/preview <yourfile>

and for gloobus

gloobus on the directory you want ;)

---

### Post by pikabuntu on 2008-08-05
zach@zach-desktop:~$ /usr/share/gloobus/preview /home/zach/Pictures/trustme.jpg
LOADING PLUGINS:
     /usr/share/gloobus/plugins/iFolder.so
     /usr/share/gloobus/plugins/iMp3.so
     /usr/share/gloobus/plugins/iPdf.so
Error loading Plugin: libMagick++.so.10: cannot open shared object file: No such file or directory

---

### Post by badchoice on 2008-08-06
Well, you don't have the library, use the instructions on readme file to install, in the new version there are different dependences for gusty and for hardy, maybe this is the problem..

---

### Post by Toshibawarrior on 2008-08-06
Ok, call me stupid, but I REALLY NEED HELP!...

I downloaded the newest version from launchpad, I read the README and installed the dependencies...but when I run the "install.sh" in terminal it just says...
```

ivan@PulgaMovil:~$ gksudo '/home/ivan/Desktop/RELEASE/install.sh' 

** (gksudo:8157): WARNING **: Invalid borders specified for theme pixmap:
        /home/ivan/.themes/Mac4Lin_GTK_v0.4/gtk-2.0/Buttons/button-default.png,
borders don't fit within the image

Installing Gloobus

Directory exists
 Copying plugins
 Copying Data
 Copying Binaries

Installation OK
cp: cannot stat `./DATA/*': No such file or directory
cp: cannot stat `preview': No such file or directory
cp: cannot stat `gloobus': No such file or directory
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSivan@PulgaMovil:~$ 

```

So how do i install this bloody cool program?...I really want to take it for a spin, but it always returns the same error...

I really don't know much about CLI, so if anyone can please help me and guide me through the process I'll be very grateful...

I did made the "scripts" on Nautilus-Actions but they don't even appear on context menus, and if I run:

```
sudo gloobus
```

nothing happens...

So please help me! I really don;t know how to do this!

---

### Post by ryanhaigh on 2008-08-06
```

cd /home/ivan/Desktop/RELEASE/
sudo ./install.sh

```
That should help. When a program looks for something like ./DATA it is looking for DATA in the current directory (./) so changing to the directory should sort it out for you.

badchoice: perhaps a revision to the instructions for this issue?

---

### Post by Toshibawarrior on 2008-08-06
THANKS A WHOLE LOT ryanhaigh!!...

It worked beautifully, although it gave me this output...

```
ivan@PulgaMovil:~$ cd /home/ivan/Desktop/RELEASE/
ivan@PulgaMovil:~/Desktop/RELEASE$ sudo ./install.sh
[sudo] password for ivan: 

Installing Gloobus

Directory exists
 Copying plugins
 Copying Data
 Copying Binaries
cp: cannot stat `preview': No such file or directory

Installation OK
ivan@PulgaMovil:~/Desktop/RELEASE$ 
```

Will it work anyway?...

Thanks again! And great work btw badchoice! Keep it up!

Edit: IT WORKED! IT FINALLY WORKED!!!...Although that output on the terminal made me think...anyways, you guys will let me know ;).

Thanks a lot to all the helpful people here on this awesome thread of this awesome forum :p!!!

---

### Post by badchoice on 2008-08-07
Hey, yes, with preview error will work without problem, I changed the location of the binary preview since the people of getdeb asked it to me to create the deb package, I forget to update the script ;)

I'll add these instructions into the readme

---

### Post by EnGorDiaz on 2008-08-07
> **pikabuntu said:**
> zach@zach-desktop:~$ /usr/share/gloobus/preview /home/zach/Pictures/trustme.jpg
LOADING PLUGINS:
     /usr/share/gloobus/plugins/iFolder.so
     /usr/share/gloobus/plugins/iMp3.so
     /usr/share/gloobus/plugins/iPdf.so
Error loading Plugin: libMagick++.so.10: cannot open shared object file: No such file or directory

you have to install libmagick10

---

### Post by EnGorDiaz on 2008-08-07
> **Toshibawarrior said:**
> THANKS A WHOLE LOT ryanhaigh!!...

It worked beautifully, although it gave me this output...

```
ivan@PulgaMovil:~$ cd /home/ivan/Desktop/RELEASE/
ivan@PulgaMovil:~/Desktop/RELEASE$ sudo ./install.sh
[sudo] password for ivan: 

Installing Gloobus

Directory exists
 Copying plugins
 Copying Data
 Copying Binaries
cp: cannot stat `preview': No such file or directory

Installation OK
ivan@PulgaMovil:~/Desktop/RELEASE$ 
```

Will it work anyway?...

Thanks again! And great work btw badchoice! Keep it up!

Edit: IT WORKED! IT FINALLY WORKED!!!...Although that output on the terminal made me think...anyways, you guys will let me know ;).

Thanks a lot to all the helpful people here on this awesome thread of this awesome forum :p!!!

i got it to work by changing nautilus actions to

/usr/share/gloobus/preview for preview in the path read the readme file

---

### Post by EnGorDiaz on 2008-08-07
> **Toshibawarrior said:**
> Ok, call me stupid, but I REALLY NEED HELP!...

I downloaded the newest version from launchpad, I read the README and installed the dependencies...but when I run the "install.sh" in terminal it just says...
```

ivan@PulgaMovil:~$ gksudo '/home/ivan/Desktop/RELEASE/install.sh' 

** (gksudo:8157): WARNING **: Invalid borders specified for theme pixmap:
        /home/ivan/.themes/Mac4Lin_GTK_v0.4/gtk-2.0/Buttons/button-default.png,
borders don't fit within the image

Installing Gloobus

Directory exists
 Copying plugins
 Copying Data
 Copying Binaries

Installation OK
cp: cannot stat `./DATA/*': No such file or directory
cp: cannot stat `preview': No such file or directory
cp: cannot stat `gloobus': No such file or directory
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSivan@PulgaMovil:~$ 

```

So how do i install this bloody cool program?...I really want to take it for a spin, but it always returns the same error...

I really don't know much about CLI, so if anyone can please help me and guide me through the process I'll be very grateful...

I did made the "scripts" on Nautilus-Actions but they don't even appear on context menus, and if I run:

```
sudo gloobus
```

nothing happens...

So please help me! I really don;t know how to do this!

thats quite a bad error... especialy with the borders hmmm you havent editted your gtkrc file have you? i did that and broke my old ubuntu

---

### Post by Toshibawarrior on 2008-08-07
I got gloobus to work. The error it says about the borders, is because of mac4lin...since I used it for changing my Ubuntu-looks it gives me that error...I don't even know what gtkrc is...lol...!:)

---

### Post by stani on 2008-08-09
Hi,
I just discovered this and it looks really cool. For using the native icons you can probably use bitmaps with gtk:
[http://library.gnome.org/devel/gtk/2.11/gtk-Stock-Items.html](http://library.gnome.org/devel/gtk/2.11/gtk-Stock-Items.html)

That's what I did with my application Phatch ([http://photobatch.stani.be](http://photobatch.stani.be)). Also I would really love to have mousewheel scroll support to flip through images.

Good luck!
Stani

---

### Post by pt123 on 2008-08-09
Anyone else having problems with GPU temperatures going extrememly high with 0.025.
My monitor kept powering off. The Nvidia applet showed the temp reaching 70C. Soon as I killed Gloobus the temp went down. 
6600GT Card

---

### Post by Exsecrabilus on 2008-08-09
WTF?: [http://getdeb.net/app/Gloobus](http://getdeb.net/app/Gloobus)

---

### Post by 16777216 on 2008-08-09
> **Exsecrabilus said:**
> WTF?: [http://getdeb.net/app/Gloobus](http://getdeb.net/app/Gloobus)

And???

---

### Post by saratchandra on 2008-08-09
I installed it and launched gloobus, but how do I get it to work? Are there any short cuts or nautilus addons?

---

### Post by Vadi on 2008-08-09
It looks like Gloobus is working *and* benchmarking your system. It's attempting to render as fast as it can (hence the overheat a guy had).

---

### Post by DJ_Peng on 2008-08-10
It looks pretty promising, but I'm getting massive lag from it. I'm having almost no chance to use my mouse to go back and forth through the files, although my arrow keys work pretty quickly. Also, is there a way to close a preview once it gets opened? I think I did something to kill the preview but it took so long to actually close I have no clue what I did.

I ran Gloobus on a directory with one subdirectory and 10 pics in the Terminal and this is what I got.

> peng@IceBox-Hardy:~$ gloobus /home/peng/Pictures/Fly\ pix/
COVER ANGLE: 70
LOADING PLUGINS:
     /usr/share/gloobus/plugins/iFolder.so
     /usr/share/gloobus/plugins/iMp3.so
     /usr/share/gloobus/plugins/iPdf.so
     /usr/share/gloobus/plugins/iPhoto.so
     /usr/share/gloobus/plugins/iPng.so
     /usr/share/gloobus/plugins/iText.so
FILE: /home/peng/Pictures/Fly pix//Andante
FileType: application/x-not-regular-file
Creating iFolder...
FILE: /home/peng/Pictures/Fly pix//Me and Mom.bmp
FileType: image/x-ms-bmp
This filetype has no preview function
FILE: /home/peng/Pictures/Fly pix//Hilary 5.jpg
FileType: image/jpeg
Creating iPhoto...
FILE: /home/peng/Pictures/Fly pix//km&sg2.jpg
FileType: image/jpeg
Creating iPhoto...
FILE: /home/peng/Pictures/Fly pix//km&sg.jpg
FileType: image/jpeg
Creating iPhoto...
FILE: /home/peng/Pictures/Fly pix//Me and Mom.jpg
FileType: image/jpeg
Creating iPhoto...
FILE: /home/peng/Pictures/Fly pix//SG and Hilary.jpg
FileType: image/jpeg
Creating iPhoto...
FILE: /home/peng/Pictures/Fly pix//sg.jpg
FileType: image/jpeg
Creating iPhoto...
FILE: /home/peng/Pictures/Fly pix//TheNeighborhood.jpg
FileType: image/jpeg
Creating iPhoto...
FILE: /home/peng/Pictures/Fly pix//theodrek1.jpg
FileType: image/jpeg
Creating iPhoto...
FILE: /home/peng/Pictures/Fly pix//theodrek.jpg
FileType: image/jpeg
Creating iPhoto...
        Thread
Loading Folder Cover: /home/peng/Pictures/Fly pix//Andante/cover.jpg
Loading no Folder Cover: nofolder.png
Loading Photo: /home/peng/Pictures/Fly pix//Hilary 5.jpg
Scaling Image (0.937500):320x213--> 300x199
Loading Photo: /home/peng/Pictures/Fly pix//km&sg2.jpg
Initializing iFolder (Load Texture)
Initializing iPhoto (Load texture)
Scaling Image (0.497664):428x600--> 213x300
Loading Photo: /home/peng/Pictures/Fly pix//km&sg.jpg
Scaling Image (0.434077):493x691--> 214x300
Loading Photo: /home/peng/Pictures/Fly pix//Me and Mom.jpg
Scaling Image (0.949206):315x240--> 299x228
Loading Photo: /home/peng/Pictures/Fly pix//SG and Hilary.jpg
Scaling Image (0.468750):640x426--> 300x199
Loading Photo: /home/peng/Pictures/Fly pix//sg.jpg
Scaling Image (0.500000):600x400--> 300x200
Loading Photo: /home/peng/Pictures/Fly pix//TheNeighborhood.jpg
Scaling Image (0.498728):393x600--> 196x299
Loading Photo: /home/peng/Pictures/Fly pix//theodrek1.jpg
Scaling Image (0.397129):418x750--> 166x300
Loading Photo: /home/peng/Pictures/Fly pix//theodrek.jpg
Initializing iPhoto (Load texture)
Initializing iPhoto (Load texture)
Initializing iPhoto (Load texture)
Initializing iPhoto (Load texture)
Initializing iPhoto (Load texture)
Initializing iPhoto (Load texture)
Initializing iPhoto (Load texture)
Scaling Image (0.166111):1800x1200--> 299x199
        END Thread
Initializing iPhoto (Load texture)
Right Arrow Pressed
Ending iFolder
Ending iPhoto
Ending iPhoto
Ending iPhoto
Ending iPhoto
Ending iPhoto
Ending iPhoto
Ending iPhoto
Ending iPhoto
Ending iPhoto
What isn't shown is that trying to drag the mouse back and forth did nothing for several seconds (I'm guessing 10-20, maybe longer) and when I finally ended the test and hit "q" it took another 5-10 seconds to close. And that's with a folder of a mere 11 items. On a more populated directory it just gets worse.

Also, I'm finding that if I get into full screen mode (I wasn't aware that's what that button was in the preview the first time or two) I end up having to kill the X session with a three finger salute to be able to get at any other windows. Not even Alt-Tab or Super-Tab seems to work while in a Gloobus full screen.My system specs, courtesy Ubuntu Tweak:

[LIST]
[*]Distro: Ubuntu 8.04.1
[*]Desktop Env: GNOME 2.22.3 (Ubuntu 2008-07-09)
[*]Kernel: Linux 2.6.24-19-generic
[*]Platform: i386
[*]CPU: Intel(R) Celeron(R) CPU 2.20GHz
[*]Memory: 748 MB
[/LIST]
My video card is an Nvidia GeForce2 MX 100/200 using the 96.43.05 driver (from NVIDIA X Server Settings).

---

### Post by EnGorDiaz on 2008-08-11
hwy badchoices i am just wondering what the next features will be in 0.26

---

### Post by EnGorDiaz on 2008-08-11
> **Toshibawarrior said:**
> I got gloobus to work. The error it says about the borders, is because of mac4lin...since I used it for changing my Ubuntu-looks it gives me that error...I don't even know what gtkrc is...lol...!:)

hmmm do you have global menu cus the only way you can get error is through gtkrc search it up

---

### Post by conundrumx on 2008-08-11
> **DJ_Peng said:**
> 
[list]
[*]CPU: Intel(R) Celeron(R) CPU 2.20GHz
[*]Memory: 748 MB
[/LIST]

There's your problem!  :p

---

### Post by DJ_Peng on 2008-08-12
Damn. I guess I have to move a RAM upgrade higher on the priority list.  :( Thanks for the info.

---

### Post by 16777216 on 2008-08-12
> **DJ_Peng said:**
> Damn. I guess I have to move a RAM upgrade higher on the priority list.  :( Thanks for the info.

Good news is that RAM is cheap.
I can get a GB for ~$30 - $40.

---

### Post by teolemon on 2008-08-13
Here's a quick howto for Ubuntu 8.04
[https://answers.edge.launchpad.net/gloobus/+question/42044](https://answers.edge.launchpad.net/gloobus/+question/42044)

---

### Post by DJ_Peng on 2008-08-13
> **16777216 said:**
> Good news is that RAM is cheap.
I can get a GB for ~$30 - $40.
Unfortunately, being disabled, I'm on a fixed income. $40 is a week's income for me, plus I have an older comp so memory isn't as easy to get as going down to my local big box. But it's a little higher on my list of things to spend money on. :)

---

### Post by teolemon on 2008-08-13
Using Ubuntu-Tweak, you can easily assign keybinding. Avoid using space, because anytime you want to use space (even when not in Nautilus), il will invoke Gloobus.
Good choices are ² or Arret Defil or Pause-Attn

Plus, Gloobus behaves weirdly on Hardy x64 and even more weirdly with Recordmydesktop.

---

### Post by gilir on 2008-08-14
Hi,

After some hours fighting against the source code and others packages, gloobus finally work on my 64 bits system :) And it's like the demo : very nice :) 

I needed to patch some files to manage this, it's available on my branch of gloobus : [https://code.launchpad.net/~gilir/gloobus/gloobus-debian](https://code.launchpad.net/~gilir/gloobus/gloobus-debian)

I'm also working on a debian packaging, which is working but need some clean up. Available soon.

I'll also try to add a proper build system, so it'll be easier to build it.

---

### Post by pikabuntu on 2008-08-14
> **badchoice said:**
> Well, you don't have the library, use the instructions on readme file to install, in the new version there are different dependences for gusty and for hardy, maybe this is the problem..
OK, I've got it going now !
Its pretty cool!

---

### Post by badchoice on 2008-08-18
Hey guys! 
These days I'm on my holidays trip, so this is why I haven't said anything! 
I'll be back on 26th august, ready to keep developing new features and solving those annoying bugs!

---

### Post by ryanhaigh on 2008-08-18
Just read something interesting over at [Phoronix]("http://www.phoronix.com/scan.php?page=article&item=gnome_224_highlights&num=1"). Apparently nautilus now supports keybindings for extensions.

---

### Post by Polygon on 2008-08-19
wait, at the above post, this program doesn't work for someone who has 768mb of ram? uhhhh......

---

### Post by zekopeko on 2008-08-19
i think the problem is that badchoice still hasn't optimized gloobus. it still tries to load ALL the pictures in memory even if you are just viewing only ten. btw a folder with 1000 pics eats my 2GB RAM in seconds.

---

### Post by DJ_Peng on 2008-08-20
> **ryanhaigh said:**
> Just read something interesting over at [Phoronix]("http://www.phoronix.com/scan.php?page=article&item=gnome_224_highlights&num=1"). Apparently nautilus now supports keybindings for extensions.
That's great news. It means more work for programmers (like badchoice) but it's definitely a win for users.

> **Polygon said:**
> wait, at the above post, this program doesn't work for someone who has 768mb of ram? uhhhh......
Yeah. But ...

> **zekopeko said:**
> i think the problem is that badchoice still hasn't optimized gloobus. it still tries to load ALL the pictures in memory even if you are just viewing only ten. btw a folder with 1000 pics eats my 2GB RAM in seconds.
This is good to know. (Being unoptimized, not that Gloobus has a more voracious appetite than even SecondLife.) I look forward to updates that will work better on my comp. It's news like this that make me glad I subscribe to so many threads. If I had unsubscribed from this thread I would have completely missed this good news.

---

### Post by graabein on 2008-08-20
Looks very nice from the screenshots. The *Globus QuickLook* name made me think of Google Earth and Outlook so that could probably change to something better, more coverflow like :)

Anyways, good luck with this project!

---

### Post by shakaran on 2008-08-20
Wow! This is a great program!

Feature suggestions and errors:
-I get a segmentation fault when I pressed key t
-Gloobus need a icon for Gnome Menu entry (an application)
-Characthers as ñ or á é is not display correcty in folders or files.
-Gloobus need a help menu for usage in terminal (and program)

I made a dirty script (for easy download):
**gloobus-installer.sh**
```

#!/bin/sh
version="0.025"
echo "Gloobus installer v $version";

echo "Downloading program...\n"
#wget http://edge.launchpad.net/gloobus/gloobus-0.02/0.02/+download/Gloobus-0.025.tar.gz

echo "Decompressing program...\n"
mkdir -p Gloobus-0.025
cd Gloobus-0.025
tar -xzf ../Gloobus-0.025.tar.gz

echo "Installing program...\n"
./RELEASE/install.sh

echo "All done!"
exit 0

```

Put in terminal:
```
sudo chmod +x gloobus-installer.sh;sudo ./gloobus-installer.sh
```

Just my 0.02 cent.

---

### Post by EnGorDiaz on 2008-08-23
> **Polygon said:**
> wait, at the above post, this program doesn't work for someone who has 768mb of ram? uhhhh......this is utter crap sorry for the language but it works on my old dell dimension just fine its got 512mb ram

---

### Post by DJ_Peng on 2008-08-24
Thanks, EnGorDiaz. I'll have to try to chase down what's slowing my comp to a crawl so I can use Gloobus. :)

---

### Post by EnGorDiaz on 2008-08-24
> **DJ_Peng said:**
> Thanks, EnGorDiaz. I'll have to try to chase down what's slowing my comp to a crawl so I can use Gloobus. :)

tell me what your running and i might help :P

---

### Post by EnGorDiaz on 2008-08-24
WARNING: it is illegal to use gloobus aparently where breaking apple EULA screw effing apple 


[http://www.mail-archive.com/nautilus-list@gnome.org/msg05180.html](http://www.mail-archive.com/nautilus-list@gnome.org/msg05180.html)

---

### Post by teolemon on 2008-08-25
Stop spreading FUD, please. 
It only may or might. Previewing files is not something especially new anyway.

---

### Post by zekopeko on 2008-08-25
> **EnGorDiaz said:**
> WARNING: it is illegal to use gloobus aparently where breaking apple EULA screw effing apple 


[http://www.mail-archive.com/nautilus-list@gnome.org/msg05180.html](http://www.mail-archive.com/nautilus-list@gnome.org/msg05180.html)

well thank the reason that america is only 5% of the worlds population and that software patents are not recognized in the rest of the world.

---

### Post by DJ_Peng on 2008-08-25
> **EnGorDiaz said:**
> tell me what your running and i might help :P
Sure thing. This is what I had posted a couple of pages back
> **DJ_Peng said:**
> 

[LIST]
[*]Distro: Ubuntu 8.04.1
[*]Desktop Env: GNOME 2.22.3 (Ubuntu 2008-07-09)
[*]Kernel: Linux 2.6.24-19-generic
[*]Platform: i386
[*]CPU: Intel(R) Celeron(R) CPU 2.20GHz
[*]Memory: 748 MB
[/LIST]
My video card is an Nvidia GeForce2 MX 100/200 using the 96.43.05 driver (from NVIDIA X Server Settings).
Let me know if you need more info from me. The post I quoted from has info on what I get when I tried to run it before.

---

### Post by EnGorDiaz on 2008-08-27
> **DJ_Peng said:**
> Sure thing. This is what I had posted a couple of pages back

Let me know if you need more info from me. The post I quoted from has info on what I get when I tried to run it before.

ok what  processes are you running in system monitor and also what aboutthe programs that start in default session monitor each programs cpu use and ram use you might have to uninstall some programs

---

### Post by EnGorDiaz on 2008-08-27
these programs include any heavy extensive programs you might have used

---

### Post by DJ_Peng on 2008-08-27
> **EnGorDiaz said:**
> ok what  processes are you running in system monitor and also what aboutthe programs that start in default session monitor each programs cpu use and ram use you might have to uninstall some programs
How do you get a listing of current processes again? I know there's an easy way to get a list but my brain keeps timing out when I try to access the data.

As far as my startup programs

[LIST]
[*]AWN with Cairo Menu, Places, AWN Terminal and Trash Cap applets
[*]GNOME Do
[*]Google Desktop (indexing is usually paused)
[*]Google Gadgets Sidebar with clock and WeatherBug
[*]Network Manager
[*]Power Manager
[*]Pulse Audio Session Management
[*]Reset Compiz (to fix a window border issue on launch, if I remember right)
[*]Update Notifier
[*]User Folders Update (I need to find if I really need it running at each and every startup)
[*]Volume Manager
[*]Wallpaper Tray
[/LIST]

---

### Post by EnGorDiaz on 2008-08-30
> **DJ_Peng said:**
> How do you get a listing of current processes again? I know there's an easy way to get a list but my brain keeps timing out when I try to access the data.

As far as my startup programs

[LIST]
[*]AWN with Cairo Menu, Places, AWN Terminal and Trash Cap applets
[*]GNOME Do
[*]Google Desktop (indexing is usually paused)
[*]Google Gadgets Sidebar with clock and WeatherBug
[*]Network Manager
[*]Power Manager
[*]Pulse Audio Session Management
[*]Reset Compiz (to fix a window border issue on launch, if I remember right)
[*]Update Notifier
[*]User Folders Update (I need to find if I really need it running at each and every startup)
[*]Volume Manager
[*]Wallpaper Tray
[/LIST]

so you reset compiz at start up? so each .profile file gets reset or just compiz itsself is it full reset there is one thing missing does the x server work and do you have full 3d enabled bcus it sounds like you have an old graphics card well no bs you do but there might be some patch's to get full 3d 

what graphics card slots do you have AGP PCI or pci express

---

### Post by EnGorDiaz on 2008-08-30
why hasnt there been any further development for this project over two weeks

---

### Post by EnGorDiaz on 2008-08-30
what im trying to get at is maybe some of your 3d features arent enabled have you got the full imagemagick up to date all that jazz what version of gloobus you running also

---

### Post by DJ_Peng on 2008-08-31
> **EnGorDiaz said:**
> so you reset compiz at start up? so each .profile file gets reset or just compiz itsself is it full reset there is one thing missing does the x server work and do you have full 3d enabled bcus it sounds like you have an old graphics card well no bs you do but there might be some patch's to get full 3d 

what graphics card slots do you have AGP PCI or pci express
I'm the only user on this comp, but I'm not sure if it's systemwide or just for me. I do have X on boot. I'm not sure why I restart Compiz, but I think I was needing to force a restart to get AWN and Google Gadgets Sidebar working properly. I have an old PCI video card.

> **EnGorDiaz said:**
> what im trying to get at is maybe some of your 3d features arent enabled have you got the full imagemagick up to date all that jazz what version of gloobus you running also
I have imagemagick 7.6.3.7.9.dfsgd1-2ubuntu1, but I'm not sure if I have everything or not. I've got Gloobus-0.25, which is the newest I've seen.

---

### Post by EnGorDiaz on 2008-08-31
i want to ask hello is there anymore development or not!!! crap man is this project just gunna die

---

### Post by EnGorDiaz on 2008-08-31
> **DJ_Peng said:**
> I'm the only user on this comp, but I'm not sure if it's systemwide or just for me. I do have X on boot. I'm not sure why I restart Compiz, but I think I was needing to force a restart to get AWN and Google Gadgets Sidebar working properly. I have an old PCI video card.


I have imagemagick 7.6.3.7.9.dfsgd1-2ubuntu1, but I'm not sure if I have everything or not. I've got Gloobus-0.25, which is the newest I've seen.

wait a second have you got ur compiz set to the most minimum performance

---

### Post by DJ_Peng on 2008-08-31
Not at all. I have a custom set of settings with quite a bit of eye candy enabled, including the desktop sphere and the Atlantis2 plugin enabled.

---

### Post by zekopeko on 2008-08-31
did you try gloobus without compiz enabled?

---

### Post by EnGorDiaz on 2008-09-01
> **zekopeko said:**
> did you try gloobus without compiz enabled?

quite stupid because compiz controls most 3d settings

---

### Post by DJ_Peng on 2008-09-01
> **zekopeko said:**
> did you try gloobus without compiz enabled?
No I haven't. I was under the (possibly mistaken) understanding that I needed Compiz enabled to use Gloobus. if I have to choose between Compiz or Gloobus Compiz is going to win due to my use of both AWN and the Google Gadgets Sidebar.

I can try it without Compiz later, but I'm probably going to spend most of the day following the coverage of Hurricane Gustav since I still have family down in the New Orleans area. Luckily it looks like Gustav will be less intense than Katrina was three years ago but I know how easily that can change even after the storm goes past New Orleans.

---

### Post by zekopeko on 2008-09-02
> **EnGorDiaz said:**
> quite stupid because compiz controls most 3d settings

please stop spurting your ignorance all over this thread. go and show your "advanced" knowledge somewhere else.

---

### Post by EnGorDiaz on 2008-09-03
> **zekopeko said:**
> please stop spurting your ignorance all over this thread. go and show your "advanced" knowledge somewhere else.

ignorance excuse me im trying to help this guy

---

### Post by ryanhaigh on 2008-09-03
EnGorDiaz, describing someone or their suggestion as stupid doesn't help anyone particularly when in this case your opinion is incorrect. Gloobus runs just as well if not better whilst using metacity as the window manager instead of compiz. Whilst your opinion in this instance was incorrect you are more than welcome to post it and should be able to do so without having to deal with derogatory remarks, we simply ask that you extend this same courtesy to others on the forum. It is our responsibility as a community to maintain the friendly and helpful atmosphere of these forums and in the end we all benefit.

---

### Post by EnGorDiaz on 2008-09-09
> **ryanhaigh said:**
> EnGorDiaz, describing someone or their suggestion as stupid doesn't help anyone particularly when in this case your opinion is incorrect. Gloobus runs just as well if not better whilst using metacity as the window manager instead of compiz. Whilst your opinion in this instance was incorrect you are more than welcome to post it and should be able to do so without having to deal with derogatory remarks, we simply ask that you extend this same courtesy to others on the forum. It is our responsibility as a community to maintain the friendly and helpful atmosphere of these forums and in the end we all benefit.

hmmm ur right most of the opengl and openal is vesa and crap

---

### Post by badchoice on 2008-09-09
Hi again!!

This project is not dead!! but these days I've been out, in my holidays trip, bussisnes trip and well, some relax!!

I have to define the direction I want gloobus to follow, what are the goals I want and all these things.

My first motivations right now are:
[B]
1. Less cpu hungry
2. OppenOffice files preview
3. Movies preview
4. Better user interface[/B]

I will work on these before anything else cause I think that I need a very robust base code before making it bigger!!

But I think that I couln't code oppenoffice preview cause I know anything about it!!

Anyway, help developing will be very gratefully cause as I said these days I'm a bit busy...


When these things are done, then I'll make an anouncement for features to add at the new version.

Thanks for the support and remember to use launchpad for blueprints and bugs cause its easyer to manage than searching throught this post!

See you!


**Donate: [https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=guitarboy000%40gmail%2ecom&item_name=Gloobus%2c%20A%20Quicklook%20for%20linux&no_shipping=0&no_note=1&tax=0&currency_code=EUR&lc=US&bn=PP%2dDonationsBF&charset=UTF%2d8](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=guitarboy000%40gmail%2ecom&item_name=Gloobus%2c%20A%20Quicklook%20for%20linux&no_shipping=0&no_note=1&tax=0&currency_code=EUR&lc=US&bn=PP%2dDonationsBF&charset=UTF%2d8)**

---

### Post by zekopeko on 2008-09-09
so.... is this thing gonna be made in clutter or SDL?

---

### Post by EnGorDiaz on 2008-09-10
here are some icosn to contribute badchoices

---

### Post by EnGorDiaz on 2008-09-10
here are more icons for you badchoices cheer's!

---

### Post by EnGorDiaz on 2008-09-12
there are some bugs in gloobus i would like to report

on some normal stock graphics card all of the dell integrated range you cant close the window of gloobus because of an error
window does scramble abit on default graphics

and i would like to see when you open a folder i would like to see a slider to slide from music file to another like the integrated preview feature in nautilus

and hopefuly some nautilus integration soon and other file manager support

---

### Post by EnGorDiaz on 2008-09-12
and if you want to help badchoices i would love to make a debian operating system based with the idea of quicklook and mac but not copying it completely

i would love to base it off mac but not like mac completely

---

### Post by teolemon on 2008-10-13
Jordi has just added some comments to the IPhoto plugin to make easier for people wanting to write new plugins to do so.

---

### Post by badchoice on 2008-10-13
Hi!
Yes I did!

Anyway I have news for you, I'm rewriting the preview application, I want it to be gtk + cairo + gtkglext (if needed)

**[http://gloobus.wordpress.com/](http://gloobus.wordpress.com/)**

Please take a look at gloobus blog for more infromation... and let me know what do you think about!!

Thanks!

---

### Post by pt123 on 2008-10-13
Glad to hear thought the project had died.

---

### Post by DJ_Peng on 2008-10-14
I'll add your blog to my RSS feeds, badchoice. You may want to consider adding it to the [Ubuntu Weblogs]("http://ubuntuweblogs.org/") planet. They're always looking for new blogs to include.

---

### Post by grigio on 2008-10-14
> **badchoice said:**
> Hi!
Yes I did!

Anyway I have news for you, I'm rewriting the preview application, I want it to be gtk + cairo + gtkglext (if needed)

**[http://gloobus.wordpress.com/](http://gloobus.wordpress.com/)**

Please take a look at gloobus blog for more infromation... and let me know what do you think about!!

Thanks!

Why don't you do a plugin for Nautilus?

---

### Post by badchoice on 2008-10-14
I talked with nautilus people and well, it seems that is not possible right now to add something like gloobus (coverflow there) but I think that with this new version is possible to add key bindings and toolbar buttons.

I would appreciate if any of you can help me with this, just bind space key to launch 

 preview <filename>

where filename is the file selected in nautilus

and add a two toolbar buttons un for coverflow (gloobus <floder>) and one for preview (preview <filename>)

If you can work it out please!! tell me! it will be one of best improvments on the application!

Now I'm very focused on making preview a very good application, redesign plugins to make it very easy to build one (yes!! very easy!!!!!!!!) and then I'll port gloobus to gtk + cairo + gtkglext using the same new plugins!!

I'll post on how to make plugins in the blog when I have it well perfiled!

I Hope we can improve it a lot!

---

### Post by Vadi on 2008-10-14
Anti-aliasing plz.

---

### Post by teolemon on 2008-10-15
They've managed to embed a widget right where we want it to be:
[http://blogs.sun.com/erwann/entry/zfs_on_the_desktop_zfs](http://blogs.sun.com/erwann/entry/zfs_on_the_desktop_zfs)
Have a look at the code. It can be switched on and off. That seems very promising. All that it would take would be to replace the timeline by the OpenGL thingie.
I don't know if it's as simple as changing an image link in HTML, but that seems doable

---

### Post by badchoice on 2008-10-15
> **teolemon said:**
> They've managed to embed a widget right where we want it to be:
[http://blogs.sun.com/erwann/entry/zfs_on_the_desktop_zfs](http://blogs.sun.com/erwann/entry/zfs_on_the_desktop_zfs)
Have a look at the code. It can be switched on and off. That seems very promising. All that it would take would be to replace the timeline by the OpenGL thingie.
I don't know if it's as simple as changing an image link in HTML, but that seems doable


Yes!! they have done it! It will be great If you can help me with this, I have no much time now and I prefer to develop gloobus and preview (now I'm redesigning preview to make it all esier) maybe we can talk to them and ask help!! but yes, this will do the trik!

Then just need for key binding!! :D

---

### Post by badchoice on 2008-10-16
Hi Again!!

Progress in the new preview application!!

Now I can load MP3 and render text in a scrollable window, this text can be colored if a parser is used (I won’t do this by now, so if anyone of you wants… there is a plugin for osx quicklook that does it.. I just need a gtkbuffertext) i can be coded as a plugin.

When I have all this more stable I’ll post a developer guide on how to develop plugins, like I said now is very easy!!!! very very, for example, to develop a plugin that just shows an image (gimp, psd or whatever) the plugin must inhert the class iImage and develop the funciton GtkPixbuf * get_pixbuf(); easy as this!!

For a text, the same, just develop a plugin that inherts iText and has the a function GtkTextBuffer * get_text_buffer();

For Mp3.. well two more functions inhert class iMusic and have get_pixbuf(); play_music(), stop_music(), get_artist(), get_album()… do you get it?

You can see the screenshots in the blog:
   [http://gloobus.wordpress.com/](http://gloobus.wordpress.com/)


and remember that you can donate here:

Donate: [https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=guitarboy000%40gmail%2ecom&item_name=Gloobus%2c%20A%20Quicklook%20for%20linux&no_shipping=0&no_note=1&tax=0&currency_code=EUR&lc=US&bn=PP%2dDonationsBF&charset=UTF%2d8](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=guitarboy000%40gmail%2ecom&item_name=Gloobus%2c%20A%20Quicklook%20for%20linux&no_shipping=0&no_note=1&tax=0&currency_code=EUR&lc=US&bn=PP%2dDonationsBF&charset=UTF%2d8)

---

### Post by teolemon on 2008-10-16
I've asked for pointers in the dev blog

---

### Post by zekopeko on 2008-10-16
this is so cool!
just a little aestetic suggestion on the scrollbars. lose the dark part above and left of the scrollbars and make scrollbars show only when there is a need for them.
are you using scrollbars of the current theme or are they hardcoded in? it would be far nicer if all scrollbars would follow the gnome theme.

also on the widget theme the sun devs coded in. i don't see how it would be useful for us to have coverflow there. can it be added in the folder view? like when you try do burn something with nautilus or open trash there is a panel thingy. could we expand it vertically and put coverflow there?

here is a screenshot of the panel thingy

[http://www.cyberciti.biz/tips/wp-content/uploads/2006/07/autilus.png](http://www.cyberciti.biz/tips/wp-content/uploads/2006/07/autilus.png)

---

### Post by badchoice on 2008-10-18
**[SIZE="5"]NEW GLOOBUS-PREVIEW FIRST RELEASE JUST FOR TESTING [/SIZE]**
Hello!

I’ve uploaded the first release of new preview, I call it gloobus-preview to differ from the old preview.

This is just a first version just for testing and find bugs!! there are not so many features but I hope to get the same funcitonality as I had with the old, but now, using more common libraries, reusing a lot of code, the new architecture is a lot better than the previous.

I’ve added a default plugin that will try to load any filetype, and show its default theme icon :) there are still some errors but its really nice. This default plugin also search if there is a thumnail for the file (with gnome-thumbnail) and uses it :D, also really nice!!

You can download it from launchpad

[http://launchpad.net/gloobus](http://launchpad.net/gloobus)

I hope you enjoy it!


remeber you can donate =) 
[B]
Donate: [https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=guitarboy000%40gmail%2ecom&item_name=Gloobus%2c%20A%20Quicklook%20for%20linux&no_shipping=0&no_note=1&tax=0&currency_code=EUR&lc=US&bn=PP%2dDonationsBF&charset=UTF%2d8](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=guitarboy000%40gmail%2ecom&item_name=Gloobus%2c%20A%20Quicklook%20for%20linux&no_shipping=0&no_note=1&tax=0&currency_code=EUR&lc=US&bn=PP%2dDonationsBF&charset=UTF%2d8)[/B]

------------------------------------------------

The scrollbars are from theme, like the icons when no plugin for the filetype is found ;)

---

### Post by JemW on 2008-10-18
Unfortunately, trying to install using the getdeb package produces the error as attached screenshot. Synaptic will not resolve the dependency. I'm running 8.10 Beta (with all current updates).

---

### Post by teolemon on 2008-10-19
Got no answer so far on this blog:
[http://blogs.sun.com/erwann/entry/zfs_on_the_desktop_zfs](http://blogs.sun.com/erwann/entry/zfs_on_the_desktop_zfs)
and this blog:
[http://aruiz.typepad.com/siliconisland/2008/10/zfs-meet-users.html](http://aruiz.typepad.com/siliconisland/2008/10/zfs-meet-users.html)

There's a link to the patch to Nautilus which is actually not that long.
Perhaps contacting the nautilus-list talking of the refactoring and asking help to integrate with the patch would receive more success thatn the previous attempt.

---

### Post by EnGorDiaz on 2008-10-20
> **badchoice said:**
> **[SIZE="5"]NEW GLOOBUS-PREVIEW FIRST RELEASE JUST FOR TESTING [/SIZE]**
Hello!

I’ve uploaded the first release of new preview, I call it gloobus-preview to differ from the old preview.

This is just a first version just for testing and find bugs!! there are not so many features but I hope to get the same funcitonality as I had with the old, but now, using more common libraries, reusing a lot of code, the new architecture is a lot better than the previous.

I’ve added a default plugin that will try to load any filetype, and show its default theme icon :) there are still some errors but its really nice. This default plugin also search if there is a thumnail for the file (with gnome-thumbnail) and uses it :D, also really nice!!

You can download it from launchpad

[http://launchpad.net/gloobus](http://launchpad.net/gloobus)

I hope you enjoy it!


remeber you can donate =) 
[B]
Donate: [https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=guitarboy000%40gmail%2ecom&item_name=Gloobus%2c%20A%20Quicklook%20for%20linux&no_shipping=0&no_note=1&tax=0&currency_code=EUR&lc=US&bn=PP%2dDonationsBF&charset=UTF%2d8](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=guitarboy000%40gmail%2ecom&item_name=Gloobus%2c%20A%20Quicklook%20for%20linux&no_shipping=0&no_note=1&tax=0&currency_code=EUR&lc=US&bn=PP%2dDonationsBF&charset=UTF%2d8)[/B]

------------------------------------------------

The scrollbars are from theme, like the icons when no plugin for the filetype is found ;)

badchoice if we could make a new rebuild of of nautilus you know patch it up would you think it would work

---

### Post by badchoice on 2008-10-20
yes.. this is the point, but I need some help in doing this... I hope, that now with this new version using all standards (gtk, gnomeui, gstreamer) they will be friendly on helping :D

But maybe the best is to ask them together!

---

### Post by teolemon on 2008-10-22
The Nautilus patch is here :
[http://src.opensolaris.org/source/xref/jds/spec-files/branches/gnome-2-24/patches/nautilus-13-zfs-snapshot.diff](http://src.opensolaris.org/source/xref/jds/spec-files/branches/gnome-2-24/patches/nautilus-13-zfs-snapshot.diff)
I don't know coding, but judging from the comments, I'd say it begin around line 1200. There are 2600 lines of code, but I guess most of it can be scraped.
The patch seems to provide a button to activate the widget (would be off by default), a menu entry, a right click entry as well as a toolbar icon
It also displays a widget right where the coverflow thingy would need to be displayed

---

### Post by QwUo173Hy on 2008-10-22
Is there any documentation for gloobus? The README I downloaded was empty. I'm wondering if it's possible to enter a folder and what other keybindings there are?

---

### Post by badchoice on 2008-10-24
I've just uplodaed a new verision release, with the default plugins working pretty well, now mp3 plugins also have sound using gstreamer iphoto works without problem and trying to solve the issue with iplain
I'll add the fullscreen function as well in next versions

I hope you like it! and report as bugs as you can!

[B]
Donate: [https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=guitarboy000%40gmail%2ecom&item_name=Gloobus%2c%20A%20Quicklook%20for%20linux&no_shipping=0&no_note=1&tax=0&currency_code=EUR&lc=US&bn=PP%2dDonationsBF&charset=UTF%2d8](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=guitarboy000%40gmail%2ecom&item_name=Gloobus%2c%20A%20Quicklook%20for%20linux&no_shipping=0&no_note=1&tax=0&currency_code=EUR&lc=US&bn=PP%2dDonationsBF&charset=UTF%2d8)[/B]

---

### Post by t4ggs on 2008-10-24
It will be helpfull if there would be a way to navigate in globus...i mean opening folders... also it would be better being able to integrate it to nautilus...i suppose this is the goal.

---

### Post by nanolightonair on 2008-10-25
Hi everybody,
First of all I'd like to thanks a lot badchoice for his application, it's great!
I've downloaded the 0.025 version last week with the getdeb package but I'd like to have always the last version, would it be possible to have a ppa to be able to have always the last gloobus-preview?

Thanks!
nanolight

---

### Post by yavez on 2008-10-25
> **JemW said:**
> Unfortunately, trying to install using the getdeb package produces the error as attached screenshot. Synaptic will not resolve the dependency. I'm running 8.10 Beta (with all current updates).

Same here?  Anybody got a fix for 8.10 users, would love to use this application.  And Kudos to the programmer for this, great work :)

Error: Dependecy is not satisfiable: libavcodec1d.

---

### Post by EnGorDiaz on 2008-10-25
> **teolemon said:**
> The Nautilus patch is here :
[http://src.opensolaris.org/source/xref/jds/spec-files/branches/gnome-2-24/patches/nautilus-13-zfs-snapshot.diff](http://src.opensolaris.org/source/xref/jds/spec-files/branches/gnome-2-24/patches/nautilus-13-zfs-snapshot.diff)
I don't know coding, but judging from the comments, I'd say it begin around line 1200. There are 2600 lines of code, but I guess most of it can be scraped.
The patch seems to provide a button to activate the widget (would be off by default), a menu entry, a right click entry as well as a toolbar icon
It also displays a widget right where the coverflow thingy would need to be displayed

ok well how does it work does it integrate it into nautilus?

---

### Post by teolemon on 2008-10-26
[http://brainstorm.ubuntu.com/search?keywords=gloobus&ordering=mostvotes](http://brainstorm.ubuntu.com/search?keywords=gloobus&ordering=mostvotes)
Please vote for Gloobus Ideas in Ubntu Brainstorm. This will help gain some attention.

---

### Post by DJ_Peng on 2008-10-26
Just keep in mind that not everyone has 3D acceleration after the upgrade to Intrepid. Anyone using the Nvidia legacy drivers will have to wait for Nvidia to write new drivers for the latest version of X.Org that's in Intrepid. We can se ethings, but anything that requires 3D acceleration (like Compiz-Fusion and Gloobus) will be busted until Nvidia comes to the rescue.

---

### Post by zekopeko on 2008-10-26
well after watching this project from the begining i have to say that i think that it lacks structure. not code wise since i have no idea about that part but the whole organization lacks coherence.
we really should make a ppa archive for this, setup an irc channel and mailing list.
also versioning gloobus is really weird. you have 0.2 branch for gloobus but the preview version is 0.11. stuff like that is really confusing.

also is there a list of dependencies that are required for gloobus to compile?
since you are the programmer badchoice perhaps you could do a build system if i want to pull gloobus from launchpad so that i can simply to ./autogen.sh ; make; sudo make install?
aslo gloobus-preview binary should give me it's version number (bzr revision number that is) if i do gloobus-preview --version so that when i report a bug you can be sure that i don't have an obsolete version and that the bug was fixed in trunk.

any suggestions to this proposal are more then welcome

---

### Post by badchoice on 2008-10-27
zekopeko: You're right, it is very confusing, but because it is...
I started gloobus, making it with SDL... and well, it was working pretty well, but as you said, it needed a lot of libraries, the code was not so standard and well, a lot of things...

Now, I've started gloobus-preview from zero (this is why the new versioning) using GTK, GSTREAMER, CAIRO.. the most standard libraries, so there won't be needed so many as before. My intention is to port Gloobus to gtk cario and gtkglext as well and making it as standard possible.
Right now there are 2 plugins one for each old and new gloobus, this will have to change and both use the new plugins...

Cause I'm just one developer, I keep it a little disorganized, but if any other developer wants to help me, or wants to contribute, then I will tidy it up!!

---

### Post by PsychedelicReaction on 2008-10-30
i would like to try out gloobus but i've got an unmet dependencies problem with Intrepid, someone could help me?

```
The following packages have unmet dependencies:
  gloobus: Depends: libavcodec1d (>= 0.cvs20070307) which is a virtual package.
           Depends: libavformat1d (>= 0.cvs20070307) which is a virtual package.
```

---

### Post by PsychedelicReaction on 2008-11-03
anyone?

---

### Post by coolen on 2008-11-03
Some of the packages have different names in Intrepid. I tracked them down manually in Synaptic.

However, I'm having trouble running it, though. I've tried gloobus and gloobus-preview, and they spit out the same error:

```
gloobus: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory
```

This file exists in /usr/lib. I noticed that other SDL libraries were kept in /usr/lib32 (I'm running 64-bit). Could this be the culprit?

I created a link in /usr/lib32, and then got this error:

```
gloobus: error while loading shared libraries: libSDL_image-1.2.so.0: wrong ELF class: ELFCLASS64
```

So, is this not working for 64-bit users?

---

### Post by zekopeko on 2008-11-19
dude what's going on with this project? any updates? need my gloobus fix :D

---

### Post by Nergar on 2008-11-23
Very confusing, I would like to test it but I don't know what to do. Please put something in the README.txt

---

### Post by zekopeko on 2008-12-17
badchoice is this project dead or are you just taking the time off?

---

### Post by Fiste788 on 2008-12-20
i think that now this project is not very useful. it became useful when it will be integrated in nautilus. can someone create a deb with gloobus integrated in nautilus??
sorry for english:)

---

### Post by zekopeko on 2008-12-20
well the nautilus in 8.10 can have keybinding for extensions so gloobus-preview could be assigned to space or something else.

---

### Post by DJ_Peng on 2008-12-31
> **PsychedelicReaction said:**
> i would like to try out gloobus but i've got an unmet dependencies problem with Intrepid, someone could help me?

```
The following packages have unmet dependencies:
  gloobus: Depends: libavcodec1d (>= 0.cvs20070307) which is a virtual package.
           Depends: libavformat1d (>= 0.cvs20070307) which is a virtual package.
```
I'm getting the libavcodec1d as well while installing from the .deb on GetDeb.

Also, I saw a story on CNET last week about [Google, MS and Apple getting sued over preview icons]("http://news.cnet.com/8301-1001_3-10129022-92.html"). Is this something Gloobus will have to watch out for?

---

### Post by coolen on 2009-01-02
Ars Technica has an article covering the suit ([http://arstechnica.com/news.ars/post/20081226-microsoft-apple-google-sued-over-icon-software-patent.html](http://arstechnica.com/news.ars/post/20081226-microsoft-apple-google-sued-over-icon-software-patent.html)).

They mentioned that Google is being sued for offering Chrome, which infringes on the patent, for sale. This seems to suggest that, if they do succeed against Apple and Microsoft, that will at least fail for wording, allowing free software a bit of breathing room.

I doubt it'll come to anything. They're going after some major names. For once, I actually hope that Microsoft and Apple will be able to defend themselves adequately.

---

### Post by DJ_Peng on 2009-01-02
Thanks for the AT link. It's pretty funny that they're going after Google's Chrome when they're not "selling" a thing. Yet.

---

### Post by teolemon on 2009-01-18
Development has started again, and Jordi is looking for coding help.

---

### Post by DJ_Peng on 2009-01-18
I've got a quick questions for those in the know. I recently upgraded my comp to use 2GB of RAM and an EVGA e-GeForce 6200 video card. Should I be installing Gloobus 0.025 or Gloobus Preview 0.11? I installed 0.025 from Christopn Korn's PPA but when I ran it the window opened and promptly closed with a silent fail. I finally ran it from the Terminal and this is what I got:
> :~$ gloobus
COVER ANGLE: 70
LOADING PLUGINS:
     /usr/share/gloobus/plugins/iFolder.so
     /usr/share/gloobus/plugins/iMp3.so
     /usr/share/gloobus/plugins/iPdf.so
     /usr/share/gloobus/plugins/iPhoto.so
     /usr/share/gloobus/plugins/iText.so
     /usr/share/gloobus/plugins/iVideo.so
Error loading Plugin: /usr/share/gloobus/plugins/iVideo.so: undefined symbol: _Z20avcodec_find_decoder7CodecID

I haven't installed Gloobus Preview yet although I do have the code on my hard drive. Which direction should I be going in? I have to say the README isn't very helpful at all for GP 0.11. Does GP need the edits to Nautilus Actions that Gloobus did?

---

### Post by badchoice on 2009-01-23
Hey people!! 

Finally I got time to get back in gloobus project!
I've done a lot of research and improvements in gloobus-preview. As I commented in the previous post, I've changed the deprectaded gnomevfs for the new gio / gnome vfs to acces to the icons thumbnails and file info!

I've added info in all plugins in the bottom part, info like size, mime type and depending on the plugin, can be added more information. If you have an idea or request of more info you wuold like to appear, **please ask!**

I've developed the PDF plugin! it loads the pages in a thread and displays it as they're loaded!! I get really amazed on how fast a PDF of 150 pages is loaded!! in gloobus-preview it is opened and first pdf page displayed in a blink!! You've to try it!!

Now I'll be fixin some code issues and searching something to launch it from a shortcut, its the missing step that keeps gloobus-preview completly off intregration, **so if you have any idea, please!!! TELL MEE!!**

For more information:
[B]Code at: 	[https://launchpad.net/gloobus](https://launchpad.net/gloobus)
More info at: 	[http://gloobus.wordpress.com/](http://gloobus.wordpress.com/)[/B]

---

### Post by Achetar on 2009-01-23
Hey badchoise, I'm gonna look through the code and see about maybe helping you. I'm not too familiar with GL and would like to get more familiar with it soo...but at the least I can bugtest (love it! great stuff this is!)

---

### Post by badchoice on 2009-01-23
Hey Achetar,
You'll see that is not so hard, and if you look for the gloobus-preview, it donesn't use GL so it's for babys :D
But well, now that I've gloobus-preview so mature, I think its time to rewrite gloobus (coverflow) to use gl inside GTK so this way the same plugins can be used in both gloobus and gloobus-preview!

If you need help in any part of the code, please tell me and I help you, you can find me on irc or in jabber so we can define the direction of the application!

---

### Post by Fionnzer on 2009-01-23
Has anyone managed to get this working on intrepid 8.10 ?
If so how ?
If not when will it come out for intrepid ? 

Thanks

---

### Post by Achetar on 2009-01-23
should I get the gloobus or gloobus-Preview branch? Getting the gloobus branch right now.

---

### Post by badchoice on 2009-01-24
Hey guys!

Now I'm developing the gloobus-preview, there is still no binaries for the newest version. There is the code in launchpad.

When I've gloobus-preview very healthy, then I'll get back on coverflow and try to use a more common libs.

Integration in nautilus is pretty hard for coverflow right now, but well, I can add a button on the toolbar to launch it quickly, the same for preview, the fact is, that I still don't know how to achieve this.

I'll upload binaries gloobus-preview (intrepid 64bits) soon, so you can test it and try to find a solution to launch it with a shortkey!

The project is not dead, but I have not so time as I would like...

See you!

---

### Post by Prominence on 2009-01-25
It's alright, it's an amazing project, I want to get the Preview though, and I wish there was a simple .deb package. Last time I tried Coverflow it didn't work well at all.

---

### Post by badchoice on 2009-01-26
Hey! I've just uploaded a video of gloobus-preview.
I get something to launch it directly, but well, it insn't still the best... (You can find the video in launchpad->screencasts)

Very soon I'll upload the binaries and a install.sh script that makes it all easier!!

---

### Post by pt123 on 2009-01-26
> **badchoice said:**
> Hey! I've just uploaded a video of gloobus-preview.


lol what was that PDF

---

### Post by badchoice on 2009-01-26
It's the book of books, the source of living, the happyines in PDF it's Kamasutra!!

hehe it was the PDF I was using for testing... so I get more happy when thing didn't work out as I would

---

### Post by azwar on 2009-01-27
> **DJ_Peng said:**
> I've got a quick questions for those in the know. I recently upgraded my comp to use 2GB of RAM and an EVGA e-GeForce 6200 video card. Should I be installing Gloobus 0.025 or Gloobus Preview 0.11? I installed 0.025 from Christopn Korn's PPA but when I ran it the window opened and promptly closed with a silent fail. I finally ran it from the Terminal and this is what I got:

:~$ gloobus
COVER ANGLE: 70
LOADING PLUGINS:
/usr/share/gloobus/plugins/iFolder.so
/usr/share/gloobus/plugins/iMp3.so
/usr/share/gloobus/plugins/iPdf.so
/usr/share/gloobus/plugins/iPhoto.so
/usr/share/gloobus/plugins/iText.so
/usr/share/gloobus/plugins/iVideo.so
Error loading Plugin: /usr/share/gloobus/plugins/iVideo.so: undefined symbol: _Z20avcodec_find_decoder7CodecID 

I haven't installed Gloobus Preview yet although I do have the code on my hard drive. Which direction should I be going in? I have to say the README isn't very helpful at all for GP 0.11. Does GP need the edits to Nautilus Actions that Gloobus did?

I also face the same problem like this... what to do. i've install gloobus & gloobus-preview

---

### Post by badchoice on 2009-01-27
just delete the ivideo plugin cause it is still not workin

```
rm /usr/share/gloobus/plugins/iVideo.so
```

---

### Post by zekopeko on 2009-01-27
could you provide an autogen.sh-way of installing from bzr? i think it would provide for easier testing of your awesome project. i'm sure that somebody from #gnome-do could help you.

and another thing that would be really nice to add is a close button in the top corner of preview.

OT: i see that you are emulating Mac OS X in you desktop screenshots. Did you try globalmenu? it allows for having the menu bar of any GTK app in the panel.

here is the link for installing from svn:
[http://ayozone.org/2009/01/08/install-gnome-globalmenu-07-series/](http://ayozone.org/2009/01/08/install-gnome-globalmenu-07-series/)

you can get vala from this ppa: [https://launchpad.net/~vala-team/+archive](https://launchpad.net/~vala-team/+archive) if you are running intrepid.

---

### Post by davim on 2009-01-28
This PPA has gloobus packages is it official?

[https://launchpad.net/~c-korn/+archive](https://launchpad.net/~c-korn/+archive)

You really should have an official PPA for Gloobus

OT: global menu is really cool :) you can follow this to install it:

[http://nancib.wordpress.com/2008/11/26/get-the-globalmenu-without-all-of-the-hassle/](http://nancib.wordpress.com/2008/11/26/get-the-globalmenu-without-all-of-the-hassle/)

use this PPA:
[https://launchpad.net/~globalmenu-team/+archive](https://launchpad.net/~globalmenu-team/+archive)

---

### Post by badchoice on 2009-01-28
Do this global menu work with firefox 3 and openoffice? cause I tested it time ago and only worked for gtk applications...

Thant ppa archive is not official... there is no stable version for gloobus but I hope we can reach it soon!

---

### Post by zekopeko on 2009-01-28
> **badchoice said:**
> Do this global menu work with firefox 3 and openoffice? cause I tested it time ago and only worked for gtk applications...

Thant ppa archive is not official... there is no stable version for gloobus but I hope we can reach it soon!

it works for GTK+ app only. For now. They plan to extend that to QT apps and possibly other toolkits. You can "fix" firefox by using the Hide Menu extension. Try looking for it on addons.mozilla.org. Don't know if it only hides the menu bar or does it provide the nice icon that contains all of the menu item (my FF doesn't have the menu bar but i have that icon that replaces the menu bar).

---

### Post by davim on 2009-01-28
> **badchoice said:**
> Do this global menu work with firefox 3 and openoffice? cause I tested it time ago and only worked for gtk applications...

Thant ppa archive is not official... there is no stable version for gloobus but I hope we can reach it soon!

I see no problem in having a testing PPA that way you would get more testers and possibly more visibility :)

---

### Post by badchoice on 2009-01-29
Any of you know if it is possible to load a .doc and .odt directly to gdkpixbuf?

I'm looking for creating the office plugin but I can't find a way to render those files...

---

### Post by davim on 2009-01-29
> **badchoice said:**
> Any of you know if it is possible to load a .doc and .odt directly to gdkpixbuf?

I'm looking for creating the office plugin but I can't find a way to render those files...

Maybe you should ask some Abiword developer :P

---

### Post by teolemon on 2009-01-29
[http://abiword.com/mailinglists/abiword-dev/](http://abiword.com/mailinglists/abiword-dev/)

---

### Post by DJ_Peng on 2009-02-06
I have to ask what is probably a really dumb question. What's the best way to install preview? Is there a deb available? I've been offline for the past two weeks and I want to check it out now that I finally have more RAM and a better video card but I'm at a loss for where to get the code from.

> **davim said:**
> OT: global menu is really cool :) you can follow this to install it:

[http://nancib.wordpress.com/2008/11/26/get-the-globalmenu-without-all-of-the-hassle/](http://nancib.wordpress.com/2008/11/26/get-the-globalmenu-without-all-of-the-hassle/)
Thanks for the plug. :guitar:

---

### Post by Islington on 2009-02-06
DJ_Peng:

try this:
[http://www.getdeb.net/app/Gloobus](http://www.getdeb.net/app/Gloobus)

---

### Post by Islington on 2009-02-06
I dont understand how to integrate it into Nautilus. It runs fine if I run, for example:

```
gloobus-preview /home/islington/Pictures/Screenshot.png
```

following the instructions here: [https://answers.launchpad.net/gloobus/+question/42044](https://answers.launchpad.net/gloobus/+question/42044)

I get a new menu item, but it doesnt do anything. what am I doing wrong?

---

### Post by badchoice on 2009-02-06
Hey!

The last version of gloobus-preview (bzr) can launch the preview without using the menu, just pressing ctrl+c and then ctrl+space, its really fast,

Anyway, for use it from the menu you just need to add the path in nautlius-actions 

something like this:

```
gloobus-preview %d/%f
```

Hope it helps you, anyway, I'll add a installation script soon and I'll ask getdeb people to create the package of it :D

---

### Post by DJ_Peng on 2009-02-06
> **Islington said:**
> DJ_Peng:

try this:
[http://www.getdeb.net/app/Gloobus](http://www.getdeb.net/app/Gloobus)
Is that the latest version? I see that's Hardy debs. Do they work with Intrepid?

---

### Post by Islington on 2009-02-06
Actually DJ_Peng

grab the bzr from here: [https://code.launchpad.net/~gloobus-dev/gloobus/main](https://code.launchpad.net/~gloobus-dev/gloobus/main)

the readme.txt has instructions

I am trying it out right now, I will report back.

---

### Post by Islington on 2009-02-06
> **badchoice said:**
> Hey!

The last version of gloobus-preview (bzr) can launch the preview without using the menu, just pressing ctrl+c and then ctrl+space, its really fast,

Anyway, for use it from the menu you just need to add the path in nautlius-actions 

something like this:

```
gloobus-preview %d/%f
```

Hope it helps you, anyway, I'll add a installation script soon and I'll ask getdeb people to create the package of it :D

I am having real trouble installing this. could you you post some instructions?

---

### Post by DJ_Peng on 2009-02-07
> **Islington said:**
> Actually DJ_Peng

grab the bzr from here: [https://code.launchpad.net/~gloobus-dev/gloobus/main]("https://code.launchpad.net/%7Egloobus-dev/gloobus/main")

the readme.txt has instructions

I am trying it out right now, I will report back.
I tried that code before my power supply died two weeks ago and it wasn't working properly for me. I thought gloobus-preview was the current version.

---

### Post by Islington on 2009-02-07
> **DJ_Peng said:**
> I tried that code before my power supply died two weeks ago and it wasn't working properly for me. I thought gloobus-preview was the current version.


there is a download for gloobus preview on the downloads page of the launchpad. Unfortunately I cant seem to get it integrated into nautilus/

---

### Post by DJ_Peng on 2009-02-08
I tried that one when I was trying to get Gloobus reinstalled after getting more memory but IIRC I couldn't seem to get that one to work at all.

---

### Post by badchoice on 2009-02-10
Hi!

How're you

I hope this week I can upload a release for gloobus-preview for intrepid (32 and 64bits).
It's not a final version but well, at least you can try it and see how it works.

I'll put a readme file explaining how to bind a key I haven't been able to find a direct shortcut but a dobule shortcut works perfect

The solution I found to launch it is getting the uris of the files in the clipboard so ctrl+c then ctrl+space works pretty well

lets go to gloobus.wordpress.com and you'll se the folder plugin screenshoots befor you get it in your pc!

Enjoy it! and consider to donate :D!

---

### Post by badchoice on 2009-02-14
Hey people as I said, here you have the download for gloobus-preview-0.03

There is not a deb, but you can request it to getdeb people!

[https://launchpad.net/gloobus/gloobus-0.03/gloobus-0.03](https://launchpad.net/gloobus/gloobus-0.03/gloobus-0.03)

I hope you try it and tell me the things you would like or the features you’ll like to be added!

And rember that you can donate something!

[https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=guitarboy000%40gmail%2ecom&item_name=Gloobus%2c%20A%20Quicklook%20for%20linux&no_shipping=0&no_note=1&tax=0&currency_code=EUR&lc=US&bn=PP%2dDonationsBF&chars](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=guitarboy000%40gmail%2ecom&item_name=Gloobus%2c%20A%20Quicklook%20for%20linux&no_shipping=0&no_note=1&tax=0&currency_code=EUR&lc=US&bn=PP%2dDonationsBF&chars)

See you!

---

### Post by DJ_Peng on 2009-02-14
I grabbed the 32bit version and saw that the instructions said to run "chmod +x install.sh && sudo install.sh". When I did I got "sudo: install.sh: command not found". It should have said to run "chmod +x install.sh && sudo ./install.sh". I haven't actually run it yet to see how it behaves, but I wanted to point out that slight glitch in the instructions.

Also I'd recommend changing the suggested key bindings unless you can confirm that ctrl+c won't cause conflicts with the standard behavior for that key combination (copy the selected text).

---

### Post by badchoice on 2009-02-14
DJ_PENG:

Thanks for the correction, you're right about the install.sh command,
Anyway, the ctrl+c behaviour is the same as allways, copy 
then, ctrl+space is the keybinding that can be changed by the user, cause preview uses the files in the clipboard (for now)

---

### Post by spg76 on 2009-02-14
I just installed gloobus-preview. I'm gonna try it out and post the bugs that I found and the features that I like to see.
Also, I want to ask if anyone knows if key-binding support for Nautilus extensions was included in GNOME 2.24 because I can't edit the accelerators in Intrepid and I don't know if I have to enable this somewhere (e.g., gconf).
If this it's possible maybe badchoice (or someone else) can make an extensions for gloobus-preview, like nautilus-sendto or nautilus-open-terminal.
Thank you.

---

### Post by teolemon on 2009-02-14
Thanks! It just works smoothly using DJPeng command and the HowTo.
Isn't it possible by using the %d and %f argument to avoid using CtrlC ?
Also, Gloobus appears behind my dock. Is there a way to put it in the foreground ?

Thanks a lot for the work done.

---

### Post by badchoice on 2009-02-19
Hi you all!

I would like to develop the iComic plugins, inherted form iDocument and i would like to know wich is the best library for uncompressing zip al rar files in c++ i Just want the files descompressed in memory not as temp files so it can be faster

thanks!

---

### Post by zekopeko on 2009-02-19
just installed 0.03. i like where it's going.
but it somethings should be a little different. for starters some images open too big. and some pdf open too small(or too big).

it would be nice if you could modify the iMp3 plugin to look for cover art in the same folder where the mp3 is. 
it could do something like this: if no embedded cover look for images in folder. if image count > 1 then search for folder.jpg and display it.otherwise display icon of the mp3 file. if image count == 1 then display that (since if there are multiple images you can't be sure which one is the cover art if it isn't named folder.jpg or what ever convention is).

iPDF eats through RAM like there is not tomorrow. 2.1 mb pdf = 110mb of RAM usage. but it does load fast. super fast.

---

### Post by badchoice on 2009-02-20
Hey!
I'll fix this mp3 issue, I'll add to load the cover.jpg or cover.png file in the folder (if its not done yet)

About the pdf I'll take a closer look at the code and see if there is a duplicated pixbuf... but every page is a photo, in bmp I mean, decompresed but well, I hope I can improve it :d

Now I'm developing two things, 
1. Use arrow keys to navigate between files 
2. Comic book zip and comic book rar previewer

Finally, I have wish :D could you, instead of donating money to me, donate a copy of **world of goo game! **I'm very addicted to the demo!!!

Well this is enought for today, I'll keep in touch!

---

### Post by zekopeko on 2009-02-20
well iPDF isn't so bad. the thing is that it used 110 mb for a 2.1 mb file and 230mb for a 110mb PDF. it would be nice if it could scale reasonably compared to the file size.

on another note i was thinking that perhaps it should close if it has no focus or allow only for one instance of preview. i noticed that when i was testing that if i didn't press space the preview would remain so i would have 10's of open files.
since the whole idea is for gloobus-preview to allow you to preview files there is no point to allow multiple preview windows.

keep up the good work.

---

### Post by davim on 2009-02-25
> **zekopeko said:**
> 
on another note i was thinking that perhaps it should close if it has no focus or allow only for one instance of preview. i noticed that when i was testing that if i didn't press space the preview would remain so i would have 10's of open files.
since the whole idea is for gloobus-preview to allow you to preview files there is no point to allow multiple preview windows.

keep up the good work.

I second this one :)

---

### Post by spady7 on 2009-03-01
Hi all, just a question: Is there a way to say to Gloobus iPdf plugin to open pdf's file larger then it does now?? I noticed that sometimes it opens a pdf file to a cetain size, other times it opens with a different size. It would be nice if I could enlarge previewed file to all display ( like Mac OS can ).
Thanks in advance

---

### Post by zekopeko on 2009-03-01
> **spady7 said:**
> Hi all, just a question: Is there a way to say to Gloobus iPdf plugin to open pdf's file larger then it does now?? I noticed that sometimes it opens a pdf file to a cetain size, other times it opens with a different size. It would be nice if I could enlarge previewed file to all display ( like Mac OS can ).
Thanks in advance

i would be nice if gloobus-preview had 2 sizes. when you first open a file it should open small something like 20% of the screen size and it should have a button for fullscreen.

---

### Post by badchoice on 2009-03-02
Well, I've to develop it, now, I don't know why, poppler scales the pdf small that its size, I want to develop to allways draw the pdf as big as the screen is.

I hope in the next release you'll see it.

For the fullscreen button, I want to perform some other things before it. The two new features I want to add is next and previous file, and multifile preview! So keep following it!

---

### Post by Depressed Man on 2009-03-04
> **badchoice said:**
> Well, I've to develop it, now, I don't know why, poppler scales the pdf small that its size, I want to develop to allways draw the pdf as big as the screen is.

I hope in the next release you'll see it.

For the fullscreen button, I want to perform some other things before it. The two new features I want to add is next and previous file, and multifile preview! So keep following it!

I love Gloobus, it's really useful for file previews. I wish I could donate money but I'm pretty much broke and I gotta find a way to fund my future Masters Program education (ugh.. didn't get into Maryland's PhD program..).

---

### Post by jurialmunkey on 2009-03-08
Hi

First off, I would like to say that the gloobus-preview is looking really nice. Perfect for a pop-up preview. However, in the current state without some sort of mouse-over support in nautilus, it is pretty much useless eye-candy. To me, it seems quicker, or just as quick, to just double click the file and let the built in gnome image viewer startup. 

So I was thinking, wouldn't it be possible just to edit the nautilus source code and implement this functionality into nautilus ourselves? I've edited the nautilus code previously to change the icon size in the places bar etc. Considering that audio mouse over preview is already built into nautilus, could we not simply modify/utilize the code for the audio preview to load up gloobus-preview for jpgs, pdfs etc? I'm having a look for the specific section of code now (still haven't found it). If anyone knows whereabouts to look let us know. 

I wouldn't mind having a go at it (I'm not the greatest programmer tho; but to get this functionality up and running I'm willing to put the effort in to learn more). If someone has already thought of this and was unsuccessful, let us know also.

---

### Post by badchoice on 2009-03-13
Hey! New features added, next and previous file with mouse keys, svg support cbr and cbz support and some bugfixes!!

Try it out in the bzr, there is still not a release, cause I want to develop one thing before!!

I hope you find it useful!!

And please, if you have a couple of €/$ that you don't know what to do with them.. you know donate!! there's a link at launchpad page!

---

### Post by spady7 on 2009-03-13
Cool!!!! It's a lovely tool really Bad.... I will wait for new release... and please... If u have time...give a look about iPDF. It would be cool if PDF can be zoommed like Leopard do...

---

### Post by spg76 on 2009-03-13
> **badchoice said:**
> Try it out in the bzr, there is still not a release, cause I want to develop one thing before!!

I can't wait to test the new features.
How can I build gloobus-preview from bzr?
Could you please post some instructions.
Thank you very much.

---

### Post by badchoice on 2009-03-14
To build from bzr you just need to download the branch, install the libraries listed in aa.txt and then just launch 

```
make && sudo make install
``` in each plugin directory and in the main directory!!

very easy!!

---

### Post by spady7 on 2009-03-14
Hi, Where can I download bzr???

---

### Post by Tibuda on 2009-03-14
> **spady7 said:**
> Hi, Where can I download bzr???

```
[sudo apitude install bzr]("apt:bzr")
```

---

### Post by Islington on 2009-03-14
Update. after I built the plugins for preview.

```
islington@Theta:~/Programs/gloobus-0.03/Gloobus-Coverflow$ make
g++ -Wall -rdynamic -o gloobus main.cpp engine.cpp timer.cpp font.cpp pluginManager.cpp ConfigFile.cpp interface.cpp input.cpp -lSDL -lSDL_gfx -lstdc++ -lGL -lGLU -lSDL_image -lSDL_ttf -lmagic 
In file included from main.cpp:1:
engine.h:6:21: error: SDL/SDL.h: No such file or directory
engine.h:7:27: error: SDL/SDL_image.h: No such file or directory
In file included from engine.h:13,
                 from main.cpp:1:
pluginManager.h:27:46: error: magic.h: No such file or directory
In file included from engine.h:14,
                 from main.cpp:1:
font.h:7:25: error: SDL/SDL_ttf.h: No such file or directory
main.cpp:3:27: error: SDL/SDL_syswm.h: No such file or directory
main.cpp:4:31: error: SDL/SDL_framerate.h: No such file or directory
In file included from engine.h:14,
                 from main.cpp:1:
font.h:17: error: ISO C++ forbids declaration of &#8216;TTF_Font&#8217; with no type
font.h:17: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
font.h:18: error: &#8216;SDL_Color&#8217; does not name a type
font.h:19: error: &#8216;SDL_Rect&#8217; does not name a type
font.h:26: error: &#8216;SDL_Rect&#8217; has not been declared
In file included from engine.h:18,
                 from main.cpp:1:
input.h:16: error: &#8216;SDLKey&#8217; does not name a type
input.h:19: error: &#8216;SDLMod&#8217; does not name a type
input.h:22: error: &#8216;Uint8&#8217; does not name a type
input.h:25: error: &#8216;Uint32&#8217; does not name a type
input.h:50: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;&&#8217; token
input.h:50: error: ISO C++ forbids declaration of &#8216;SDL_Event&#8217; with no type
input.h:58: error: &#8216;Uint8&#8217; does not name a type
input.h:61: error: &#8216;Uint8&#8217; does not name a type
input.h:64: error: &#8216;Uint16&#8217; does not name a type
input.h:65: error: &#8216;Uint16&#8217; does not name a type
input.h:68: error: &#8216;Sint16&#8217; does not name a type
input.h:69: error: &#8216;Sint16&#8217; does not name a type
input.h:72: error: &#8216;Uint32&#8217; does not name a type
input.h:75: error: &#8216;Uint8&#8217; does not name a type
input.h:81: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;&&#8217; token
input.h:81: error: ISO C++ forbids declaration of &#8216;SDL_Event&#8217; with no type
input.h:94: error: &#8216;Uint32&#8217; does not name a type
input.h:97: error: &#8216;Uint32&#8217; does not name a type
input.h:159: error: &#8216;Uint32&#8217; does not name a type
input.h:162: error: &#8216;Uint32&#8217; does not name a type
input.h:165: error: &#8216;Uint32&#8217; has not been declared
input.h:168: error: &#8216;Uint32&#8217; has not been declared
input.h:171: error: &#8216;Uint32&#8217; has not been declared
input.h:171: error: &#8216;Uint32&#8217; has not been declared
input.h:183: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;&&#8217; token
input.h:183: error: ISO C++ forbids declaration of &#8216;SDL_Event&#8217; with no type
In file included from main.cpp:1:
engine.h:146: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
main.cpp:27: error: variable or field &#8216;gtv_center_window&#8217; declared void
main.cpp:27: error: &#8216;SDL_Surface&#8217; was not declared in this scope
main.cpp:27: error: &#8216;screen&#8217; was not declared in this scope
In file included from engine.cpp:8:
engine.h:6:21: error: SDL/SDL.h: No such file or directory
engine.h:7:27: error: SDL/SDL_image.h: No such file or directory
In file included from engine.h:13,
                 from engine.cpp:8:
pluginManager.h:27:46: error: magic.h: No such file or directory
In file included from engine.h:14,
                 from engine.cpp:8:
font.h:7:25: error: SDL/SDL_ttf.h: No such file or directory
In file included from engine.h:14,
                 from engine.cpp:8:
font.h:17: error: ISO C++ forbids declaration of &#8216;TTF_Font&#8217; with no type
font.h:17: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
font.h:18: error: &#8216;SDL_Color&#8217; does not name a type
font.h:19: error: &#8216;SDL_Rect&#8217; does not name a type
font.h:26: error: &#8216;SDL_Rect&#8217; has not been declared
In file included from engine.h:18,
                 from engine.cpp:8:
input.h:16: error: &#8216;SDLKey&#8217; does not name a type
input.h:19: error: &#8216;SDLMod&#8217; does not name a type
input.h:22: error: &#8216;Uint8&#8217; does not name a type
input.h:25: error: &#8216;Uint32&#8217; does not name a type
input.h:50: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;&&#8217; token
input.h:50: error: ISO C++ forbids declaration of &#8216;SDL_Event&#8217; with no type
input.h:58: error: &#8216;Uint8&#8217; does not name a type
input.h:61: error: &#8216;Uint8&#8217; does not name a type
input.h:64: error: &#8216;Uint16&#8217; does not name a type
input.h:65: error: &#8216;Uint16&#8217; does not name a type
input.h:68: error: &#8216;Sint16&#8217; does not name a type
input.h:69: error: &#8216;Sint16&#8217; does not name a type
input.h:72: error: &#8216;Uint32&#8217; does not name a type
input.h:75: error: &#8216;Uint8&#8217; does not name a type
input.h:81: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;&&#8217; token
input.h:81: error: ISO C++ forbids declaration of &#8216;SDL_Event&#8217; with no type
input.h:94: error: &#8216;Uint32&#8217; does not name a type
input.h:97: error: &#8216;Uint32&#8217; does not name a type
input.h:159: error: &#8216;Uint32&#8217; does not name a type
input.h:162: error: &#8216;Uint32&#8217; does not name a type
input.h:165: error: &#8216;Uint32&#8217; has not been declared
input.h:168: error: &#8216;Uint32&#8217; has not been declared
input.h:171: error: &#8216;Uint32&#8217; has not been declared
input.h:171: error: &#8216;Uint32&#8217; has not been declared
input.h:183: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;&&#8217; token
input.h:183: error: ISO C++ forbids declaration of &#8216;SDL_Event&#8217; with no type
In file included from engine.cpp:8:
engine.h:146: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
engine.cpp: In member function &#8216;int Engine::resizeWindow(int, int)&#8217;:
engine.cpp:20: error: expected initializer before &#8216;*&#8217; token
engine.cpp:21: error: &#8216;SDL_OPENGL&#8217; was not declared in this scope
engine.cpp:21: error: &#8216;SDL_GL_DOUBLEBUFFER&#8217; was not declared in this scope
engine.cpp:21: error: &#8216;SDL_HWPALETTE&#8217; was not declared in this scope
engine.cpp:21: error: &#8216;SDL_RESIZABLE&#8217; was not declared in this scope
engine.cpp:22: error: &#8216;info&#8217; was not declared in this scope
engine.cpp:22: error: &#8216;SDL_HWSURFACE&#8217; was not declared in this scope
engine.cpp:23: error: &#8216;SDL_SWSURFACE&#8217; was not declared in this scope
engine.cpp:24: error: &#8216;info&#8217; was not declared in this scope
engine.cpp:25: error: &#8216;SDL_SetVideoMode&#8217; was not declared in this scope
engine.cpp: In member function &#8216;void Engine::init(std::string)&#8217;:
engine.cpp:82: error: &#8216;SDL_EnableKeyRepeat&#8217; was not declared in this scope
engine.cpp:88: error: &#8216;SDL_CreateMemberThread&#8217; was not declared in this scope
engine.cpp: In member function &#8216;void Engine::view_prev()&#8217;:
engine.cpp:109: error: &#8216;SDLK_LEFT&#8217; was not declared in this scope
engine.cpp: In member function &#8216;void Engine::view_next()&#8217;:
engine.cpp:128: error: &#8216;SDLK_RIGHT&#8217; was not declared in this scope
engine.cpp: In member function &#8216;void Engine::updatekeys()&#8217;:
engine.cpp:158: error: &#8216;SDL_BUTTON_LEFT&#8217; was not declared in this scope
engine.cpp:160: error: &#8216;GetMouseX&#8217; was not declared in this scope
engine.cpp:161: error: &#8216;GetMouseY&#8217; was not declared in this scope
engine.cpp:178: error: &#8216;SDL_BUTTON_LEFT&#8217; was not declared in this scope
engine.cpp:182: error: &#8216;GetMouseX&#8217; was not declared in this scope
engine.cpp:183: error: &#8216;GetMouseY&#8217; was not declared in this scope
engine.cpp:194: error: &#8216;SDLK_RIGHT&#8217; was not declared in this scope
engine.cpp:199: error: &#8216;SDLK_LEFT&#8217; was not declared in this scope
engine.cpp:206: error: &#8216;SDLK_SPACE&#8217; was not declared in this scope
engine.cpp: In member function &#8216;void Engine::render()&#8217;:
engine.cpp:454: error: &#8216;SDL_GL_SwapBuffers&#8217; was not declared in this scope
engine.cpp: In member function &#8216;void Engine::render_text()&#8217;:
engine.cpp:475: error: &#8216;class Font2&#8217; has no member named &#8216;m_position&#8217;
In file included from font.cpp:1:
font.h:6:21: error: SDL/SDL.h: No such file or directory
font.h:7:25: error: SDL/SDL_ttf.h: No such file or directory
In file included from font.h:9,
                 from font.cpp:1:
pluginManager.h:27:46: error: magic.h: No such file or directory
In file included from font.cpp:1:
font.h:17: error: ISO C++ forbids declaration of &#8216;TTF_Font&#8217; with no type
font.h:17: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
font.h:18: error: &#8216;SDL_Color&#8217; does not name a type
font.h:19: error: &#8216;SDL_Rect&#8217; does not name a type
font.h:26: error: &#8216;SDL_Rect&#8217; has not been declared
font.cpp: In member function &#8216;int Font2::init()&#8217;:
font.cpp:7: error: &#8216;TTF_Init&#8217; was not declared in this scope
font.cpp:9: error: &#8216;m_font&#8217; was not declared in this scope
font.cpp:9: error: &#8216;TTF_OpenFont&#8217; was not declared in this scope
font.cpp:10: error: &#8216;TTF_GetError&#8217; was not declared in this scope
font.cpp:13: error: &#8216;m_color&#8217; was not declared in this scope
font.cpp:19: error: &#8216;m_position&#8217; was not declared in this scope
font.cpp: In member function &#8216;void Font2::set_window_size(int, int)&#8217;:
font.cpp:28: error: &#8216;m_position&#8217; was not declared in this scope
font.cpp: At global scope:
font.cpp:56: error: &#8216;SDL_Rect&#8217; has not been declared
font.cpp: In member function &#8216;void Font2::SDL_GL_RenderText(std::string, int*)&#8217;:
font.cpp:59: error: &#8216;SDL_Surface&#8217; was not declared in this scope
font.cpp:59: error: &#8216;initial&#8217; was not declared in this scope
font.cpp:60: error: &#8216;intermediary&#8217; was not declared in this scope
font.cpp:65: error: &#8216;m_font&#8217; was not declared in this scope
font.cpp:65: error: &#8216;m_color&#8217; was not declared in this scope
font.cpp:65: error: &#8216;TTF_RenderText_Blended&#8217; was not declared in this scope
font.cpp:70: error: &#8216;SDL_CreateRGBSurface&#8217; was not declared in this scope
font.cpp:72: error: &#8216;SDL_BlitSurface&#8217; was not declared in this scope
font.cpp:90: error: request for member &#8216;x&#8217; in &#8216;* location&#8217;, which is of non-class type &#8216;int&#8217;
font.cpp:90: error: request for member &#8216;y&#8217; in &#8216;* location&#8217;, which is of non-class type &#8216;int&#8217;
font.cpp:91: error: request for member &#8216;x&#8217; in &#8216;* location&#8217;, which is of non-class type &#8216;int&#8217;
font.cpp:91: error: request for member &#8216;y&#8217; in &#8216;* location&#8217;, which is of non-class type &#8216;int&#8217;
font.cpp:92: error: request for member &#8216;x&#8217; in &#8216;* location&#8217;, which is of non-class type &#8216;int&#8217;
font.cpp:92: error: request for member &#8216;y&#8217; in &#8216;* location&#8217;, which is of non-class type &#8216;int&#8217;
font.cpp:93: error: request for member &#8216;x&#8217; in &#8216;* location&#8217;, which is of non-class type &#8216;int&#8217;
font.cpp:93: error: request for member &#8216;y&#8217; in &#8216;* location&#8217;, which is of non-class type &#8216;int&#8217;
font.cpp:97: error: &#8216;SDL_FreeSurface&#8217; was not declared in this scope
In file included from pluginManager.cpp:1:
pluginManager.h:27:46: error: magic.h: No such file or directory
pluginManager.cpp: In member function &#8216;std::string pluginManager::search_plugin_for_file(std::string)&#8217;:
pluginManager.cpp:65: error: &#8216;magic_t&#8217; was not declared in this scope
pluginManager.cpp:65: error: expected `;' before &#8216;myt&#8217;
pluginManager.cpp:66: error: &#8216;myt&#8217; was not declared in this scope
pluginManager.cpp:66: error: &#8216;magic_load&#8217; was not declared in this scope
pluginManager.cpp:67: error: &#8216;magic_file&#8217; was not declared in this scope
pluginManager.cpp:68: error: &#8216;magic_close&#8217; was not declared in this scope
In file included from interface.cpp:1:
interface.h:23:21: error: SDL/SDL.h: No such file or directory
interface.h:24:27: error: SDL/SDL_image.h: No such file or directory
interface.cpp: In member function &#8216;void Interface::addInterfaceTexture(const char*, bool)&#8217;:
interface.cpp:88: error: &#8216;SDL_Surface&#8217; was not declared in this scope
interface.cpp:88: error: &#8216;image&#8217; was not declared in this scope
interface.cpp:93: error: &#8216;IMG_Load&#8217; was not declared in this scope
interface.cpp:109: error: &#8216;SDL_FreeSurface&#8217; was not declared in this scope
In file included from input.cpp:1:
input.h:3:21: error: SDL/SDL.h: No such file or directory
In file included from input.cpp:1:
input.h:16: error: &#8216;SDLKey&#8217; does not name a type
input.h:19: error: &#8216;SDLMod&#8217; does not name a type
input.h:22: error: &#8216;Uint8&#8217; does not name a type
input.h:25: error: &#8216;Uint32&#8217; does not name a type
input.h:50: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;&&#8217; token
input.h:50: error: ISO C++ forbids declaration of &#8216;SDL_Event&#8217; with no type
input.h:58: error: &#8216;Uint8&#8217; does not name a type
input.h:61: error: &#8216;Uint8&#8217; does not name a type
input.h:64: error: &#8216;Uint16&#8217; does not name a type
input.h:65: error: &#8216;Uint16&#8217; does not name a type
input.h:68: error: &#8216;Sint16&#8217; does not name a type
input.h:69: error: &#8216;Sint16&#8217; does not name a type
input.h:72: error: &#8216;Uint32&#8217; does not name a type
input.h:75: error: &#8216;Uint8&#8217; does not name a type
input.h:81: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;&&#8217; token
input.h:81: error: ISO C++ forbids declaration of &#8216;SDL_Event&#8217; with no type
input.h:94: error: &#8216;Uint32&#8217; does not name a type
input.h:97: error: &#8216;Uint32&#8217; does not name a type
input.h:159: error: &#8216;Uint32&#8217; does not name a type
input.h:162: error: &#8216;Uint32&#8217; does not name a type
input.h:165: error: &#8216;Uint32&#8217; has not been declared
input.h:168: error: &#8216;Uint32&#8217; has not been declared
input.h:171: error: &#8216;Uint32&#8217; has not been declared
input.h:171: error: &#8216;Uint32&#8217; has not been declared
input.h:183: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;&&#8217; token
input.h:183: error: ISO C++ forbids declaration of &#8216;SDL_Event&#8217; with no type
input.cpp:9: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;&&#8217; token
input.cpp:9: error: ISO C++ forbids declaration of &#8216;SDL_Event&#8217; with no type
input.cpp: In constructor &#8216;cInput::tMouse::tMouse(int)&#8217;:
input.cpp:12: error: &#8216;SDL_GetTicks&#8217; was not declared in this scope
input.cpp:15: error: &#8216;type&#8217; was not declared in this scope
input.cpp:15: error: &#8216;Event&#8217; was not declared in this scope
input.cpp:17: error: &#8216;SDL_MOUSEMOTION&#8217; was not declared in this scope
input.cpp:20: error: &#8216;state&#8217; was not declared in this scope
input.cpp:23: error: &#8216;x&#8217; was not declared in this scope
input.cpp:24: error: &#8216;y&#8217; was not declared in this scope
input.cpp:27: error: &#8216;xrel&#8217; was not declared in this scope
input.cpp:28: error: &#8216;yrel&#8217; was not declared in this scope
input.cpp:31: error: &#8216;button&#8217; was not declared in this scope
input.cpp:33: error: &#8216;SDL_MOUSEBUTTONDOWN&#8217; was not declared in this scope
input.cpp:33: error: &#8216;SDL_MOUSEBUTTONUP&#8217; was not declared in this scope
input.cpp:36: error: &#8216;state&#8217; was not declared in this scope
input.cpp:39: error: &#8216;x&#8217; was not declared in this scope
input.cpp:40: error: &#8216;y&#8217; was not declared in this scope
input.cpp:43: error: &#8216;button&#8217; was not declared in this scope
input.cpp:46: error: &#8216;xrel&#8217; was not declared in this scope
input.cpp:47: error: &#8216;yrel&#8217; was not declared in this scope
input.cpp:51: error: &#8216;abort&#8217; was not declared in this scope
input.cpp: At global scope:
input.cpp:61: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;&&#8217; token
input.cpp:61: error: ISO C++ forbids declaration of &#8216;SDL_Event&#8217; with no type
input.cpp: In constructor &#8216;cInput::tKey::tKey(int)&#8217;:
input.cpp:64: error: &#8216;SDL_GetTicks&#8217; was not declared in this scope
input.cpp:67: error: &#8216;key&#8217; was not declared in this scope
input.cpp:67: error: &#8216;Event&#8217; was not declared in this scope
input.cpp:68: error: &#8216;mod&#8217; was not declared in this scope
input.cpp:69: error: &#8216;type&#8217; was not declared in this scope
input.cpp:72: error: &#8216;SDL_GetKeyName&#8217; was not declared in this scope
input.cpp:75: error: &#8216;KMOD_NUM&#8217; was not declared in this scope
input.cpp:76: error: &#8216;KMOD_CAPS&#8217; was not declared in this scope
input.cpp:77: error: &#8216;KMOD_LCTRL&#8217; was not declared in this scope
input.cpp:78: error: &#8216;KMOD_RCTRL&#8217; was not declared in this scope
input.cpp:79: error: &#8216;KMOD_LSHIFT&#8217; was not declared in this scope
input.cpp:80: error: &#8216;KMOD_RSHIFT&#8217; was not declared in this scope
input.cpp:81: error: &#8216;KMOD_LALT&#8217; was not declared in this scope
input.cpp:82: error: &#8216;KMOD_RALT&#8217; was not declared in this scope
input.cpp: At global scope:
input.cpp:139: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;&&#8217; token
input.cpp:139: error: ISO C++ forbids declaration of &#8216;SDL_Event&#8217; with no type
input.cpp: In member function &#8216;bool cInput::Poll(int)&#8217;:
input.cpp:142: error: &#8216;Event&#8217; was not declared in this scope
input.cpp:142: error: &#8216;SDL_KEYDOWN&#8217; was not declared in this scope
input.cpp:142: error: &#8216;SDL_KEYUP&#8217; was not declared in this scope
input.cpp:147: error: &#8216;SDL_MOUSEMOTION&#8217; was not declared in this scope
input.cpp:147: error: &#8216;SDL_MOUSEBUTTONDOWN&#8217; was not declared in this scope
input.cpp:147: error: &#8216;SDL_MOUSEBUTTONUP&#8217; was not declared in this scope
input.cpp: At global scope:
input.cpp:160: error: &#8216;Uint32&#8217; does not name a type
input.cpp:166: error: &#8216;Uint32&#8217; does not name a type
input.cpp:171: error: variable or field &#8216;SetMouseY&#8217; declared void
input.cpp:171: error: &#8216;Uint32&#8217; was not declared in this scope
make: *** [gloobus] Error 1

```

---

### Post by shakaran on 2009-03-14
@Islington: You need install some packages more.

sudo apt-get install libsdl1.2-dev libsdl-image1.2-dev libsdl-ttf2.0-dev

Maybe someone more. Show me again if you find problems.

---

### Post by Islington on 2009-03-14
thanks for the fast reply it certainly cut down on the amount of errors:

```
islington@Theta:~/Programs/gloobus-0.03/Gloobus-Coverflow$ make
g++ -Wall -rdynamic -o gloobus main.cpp engine.cpp timer.cpp font.cpp pluginManager.cpp ConfigFile.cpp interface.cpp input.cpp -lSDL -lSDL_gfx -lstdc++ -lGL -lGLU -lSDL_image -lSDL_ttf -lmagic 
In file included from engine.h:13,
                 from main.cpp:1:
pluginManager.h:27:46: error: magic.h: No such file or directory
main.cpp:4:31: error: SDL/SDL_framerate.h: No such file or directory
main.cpp: In function ‘int main(int, char**)’:
main.cpp:174: error: ‘FPSmanager’ was not declared in this scope
main.cpp:174: error: expected `;' before ‘manager’
main.cpp:175: error: ‘manager’ was not declared in this scope
main.cpp:175: error: ‘SDL_initFramerate’ was not declared in this scope
main.cpp:176: error: ‘SDL_setFramerate’ was not declared in this scope
main.cpp:204: error: ‘SDL_framerateDelay’ was not declared in this scope
In file included from engine.h:13,
                 from engine.cpp:8:
pluginManager.h:27:46: error: magic.h: No such file or directory
In file included from font.h:9,
                 from font.cpp:1:
pluginManager.h:27:46: error: magic.h: No such file or directory
In file included from pluginManager.cpp:1:
pluginManager.h:27:46: error: magic.h: No such file or directory
pluginManager.cpp: In member function ‘std::string pluginManager::search_plugin_for_file(std::string)’:
pluginManager.cpp:65: error: ‘magic_t’ was not declared in this scope
pluginManager.cpp:65: error: expected `;' before ‘myt’
pluginManager.cpp:66: error: ‘myt’ was not declared in this scope
pluginManager.cpp:66: error: ‘magic_load’ was not declared in this scope
pluginManager.cpp:67: error: ‘magic_file’ was not declared in this scope
pluginManager.cpp:68: error: ‘magic_close’ was not declared in this scope
make: *** [gloobus] Error 1

```

---

### Post by shakaran on 2009-03-15
Oh, well someone more:

sudo apt-get install libsdl-gfx1.2-dev libmagic-dev

I believe that these solve all errors. If not post again please ;)

---

### Post by teolemon on 2009-03-15
Here's a quick install guide: [http://code.google.com/p/gnome2-globalmenu/wiki/Gloobus](http://code.google.com/p/gnome2-globalmenu/wiki/Gloobus)

---

### Post by badchoice on 2009-03-16
Well, the coverflow needs an update to use the new plugin system I'm using in gloobus-preview, I would like to use another interface isntead of SDL and opengl, use something standard like gtk.. but I can't find anything really interesting

If you know anything good enought for it, please tell me!

Now I'm concerned in preview cause i find it more useful than coverflow, anyway, coverflow is amazing :D

---

### Post by Islington on 2009-03-16
> **badchoice said:**
> Well, the coverflow needs an update to use the new plugin system I'm using in gloobus-preview, I would like to use another interface isntead of SDL and opengl, use something standard like gtk.. but I can't find anything really interesting

If you know anything good enought for it, please tell me!

Now I'm concerned in preview cause i find it more useful than coverflow, anyway, coverflow is amazing :D
Preview is much better than coverflow. (Thanks shakaran). Currently the only way to launch it is ctrl+c then ctrl+ space ? Anyway you can make this just 1 keyboard shortcut?

---

### Post by badchoice on 2009-03-16
Well, I would like to achieve this but nautilus needs dbus or someting to be able to comunicate with other applications, now I can only get the uri of the copied files, so the ctrl+c needs to be presseds before ctrl+space.. anyway, gloobus-preview can be launnched with a parameter so any application can launch it.

for example i added gloobus-preview in easytag so to listen a song it uses as default player gloobus-preview (very nice!! :D)

There's a discussion in nautilus-list about his dbus integration but I don't know if its going to be developed..

---

### Post by spady7 on 2009-03-16
Hi BADCHOICE, can u tell me how to install coverflow?? Itried many times... but I can't uderstand how to make it working...
Thanks

---

### Post by zekopeko on 2009-03-16
> **badchoice said:**
> Well, the coverflow needs an update to use the new plugin system I'm using in gloobus-preview, I would like to use another interface isntead of SDL and opengl, use something standard like gtk.. but I can't find anything really interesting

If you know anything good enought for it, please tell me!

Now I'm concerned in preview cause i find it more useful than coverflow, anyway, coverflow is amazing :D

how about clutter?

[http://www.clutter-project.org/](http://www.clutter-project.org/)

btw it would be nice to polish gloobus-preview before working on coverflow. there are still weird bugs and behaviors in gloobus-preview.

---

### Post by spg76 on 2009-03-16
> **badchoice said:**
> Well, I would like to achieve this but nautilus needs dbus or someting to be able to comunicate with other applications, now I can only get the uri of the copied files, so the ctrl+c needs to be presseds before ctrl+space.. anyway, gloobus-preview can be launnched with a parameter so any application can launch it.

I don't know where you could find out about this but if you make an extension (like nautilus-open-terminal) for gloobus-preview, maybe it's possible to assign a key to that extension. This feature (key binding support for Nautilus extensions) appears on the [Nautilus Roadmap]("http://live.gnome.org/RoadMap/Nautilus") although I don't know if it's implemented yet.

---

### Post by pt123 on 2009-03-16
> **badchoice said:**
> Well, the coverflow needs an update to use the new plugin system I'm using in gloobus-preview, I would like to use another interface isntead of SDL and opengl, use something standard like gtk.. but I can't find anything really interesting

If you know anything good enought for it, please tell me!


Yes another one for Clutter.

---

### Post by zekopeko on 2009-03-17
> **spg76 said:**
> I don't know where you could find out about this but if you make an extension (like nautilus-open-terminal) for gloobus-preview, maybe it's possible to assign a key to that extension. This feature (key binding support for Nautilus extensions) appears on the [Nautilus Roadmap]("http://live.gnome.org/RoadMap/Nautilus") although I don't know if it's implemented yet.

i think that's been implemented. 

a quick google give this 

[http://library.gnome.org/devel/libnautilus-extension/stable/pt01.html](http://library.gnome.org/devel/libnautilus-extension/stable/pt01.html)

is there an extension that uses this in nautilus? so that badchoice could take a look at implementation.

---

### Post by teolemon on 2009-03-20
[http://live.gnome.org/Nautilus/Development/Extensions](http://live.gnome.org/Nautilus/Development/Extensions)

---

### Post by joelwhrs on 2009-03-25
I have installed gloobus on ubuntu 8.1 and have also gotten nautilus actions and added those 2 lines that it told me to in the readme but when I press space it just opens the file and doesnt give me coverflow or anything, what am I doing wrong? The version is .025 and I checked in the installed files and it was there. Sorry but i'm a ubuntu noob. Thanks for any help.

---

### Post by zekopeko on 2009-03-25
> **joelwhrs said:**
> I have installed gloobus on ubuntu 8.1 and have also gotten nautilus actions and added those 2 lines that it told me to in the readme but when I press space it just opens the file and doesnt give me coverflow or anything, what am I doing wrong? The version is .025 and I checked in the installed files and it was there. Sorry but i'm a ubuntu noob. Thanks for any help.

the only way to open files with gloobus-preview (with a keybinding) is by pressing Ctrl+C and then Ctrl+Space(or what ever you want).

ctrl+space has to be set up in compiz config settings manager under General Settings/Commands.
don't know where you could set it if you don't use compiz.

---

### Post by joelwhrs on 2009-03-25
> **zekopeko said:**
> the only way to open files with gloobus-preview (with a keybinding) is by pressing Ctrl+C and then Ctrl+Space(or what ever you want).

ctrl+space has to be set up in compiz config settings manager under General Settings/Commands.
don't know where you could set it if you don't use compiz.

I have tried using ctrl+c and then ctrl+space and when I press ctrl+c it just says that it copied the file. I have just now noticed that it shows the coverflow option on the right click menu but when I click on it nothing happens.

---

### Post by hcorey on 2009-03-28
I used gloobus in intrepid. Preview opened with spacebar, and I got a nice although buggy coverview by right-clicking a folder and choosing a nautilus action. I am now running jaunty, and i installed 0.03. I now have to right click a file, copy it, and then ctrl c (set in ccsm) for preview. For a folder, I just get a folder icon and a list of contents rather than coverflow. what happened?

---

### Post by zekopeko on 2009-03-31
coverflow development is paused for now. badchoice is focusing on preview.

---

### Post by badchoice on 2009-04-03
Hey People!!

I left gloobus for a wile so I can rest a little, but I couldn't so I started something new!!
Looking throught deviantart I found the coversutra application screenshots and well, a long time ago I used nowplaying screenlet that now is.. dead. So I decided to create a new one.

I used a lot of their code so its practically the same, but now as a standalone application without depending on screenlets

- It currently works for banshee
- NowPlaying themes are supported
- No playing controlls for now
- Lyrics support in the next version!

So please take a look at it!

[http://jordihp.deviantart.com/art/CoverGloobus-1-0-117908822](http://jordihp.deviantart.com/art/CoverGloobus-1-0-117908822)

Donate:
[https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=guitarboy000%40gmail%2ecom&item_name=Gloobus%2c%20A%20Quicklook%20for%20linux&no_shipping=0&no_note=1&tax=0&currency_code=EUR&lc=US&bn=PP%2dDonationsBF&chars](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=guitarboy000%40gmail%2ecom&item_name=Gloobus%2c%20A%20Quicklook%20for%20linux&no_shipping=0&no_note=1&tax=0&currency_code=EUR&lc=US&bn=PP%2dDonationsBF&chars)

---

### Post by pt123 on 2009-04-03
> **badchoice said:**
> 
I left gloobus for a wile 
Sad to hear that I found coverflow to be very useful for browsing image directories (apart from the high memory usage). Didn't have much use for preview. 

>  so I can rest a little, but I couldn't so I started something new!!
You need to rest, not start more projects. :)

---

### Post by CoreyCavalera on 2009-04-15
Hi people. I've problem with run this application on ubuntu 9.04, instalation is complete, but when I type in terminal: gloobus-preview <filename>, terminal write: LOADING PLUGINS:
	 /usr/share/gloobus/plugins-preview/iDefault.so
	 /usr/share/gloobus/plugins-preview/iFolder.so
	 /usr/share/gloobus/plugins-preview/iMp3.so
	 /usr/share/gloobus/plugins-preview/iPdf.so
Error loading Plugin: libpoppler-glib.so.3: cannot open shared object file: No such file or directory
Please, when I resolved it? Thank you for help. And sorry, my english it's so bad. Petr

---

### Post by zekopeko on 2009-04-17
> **CoreyCavalera said:**
> Hi people. I've problem with run this application on ubuntu 9.04, instalation is complete, but when I type in terminal: gloobus-preview <filename>, terminal write: LOADING PLUGINS:
	 /usr/share/gloobus/plugins-preview/iDefault.so
	 /usr/share/gloobus/plugins-preview/iFolder.so
	 /usr/share/gloobus/plugins-preview/iMp3.so
	 /usr/share/gloobus/plugins-preview/iPdf.so
Error loading Plugin: libpoppler-glib.so.3: cannot open shared object file: No such file or directory
Please, when I resolved it? Thank you for help. And sorry, my english it's so bad. Petr

see that Error loading Plugins part? you are missing libpoppler. try searching in synaptic for the library and install it (might not be the same name).

---

### Post by durand on 2009-04-17
Looks pretty cool! Can't wait for nautilus integration.

---

### Post by badchoice on 2009-04-18
Hi!!!!

Good News!!!
New version of **Gloobus-Preview** Available!!!!
It works for jaunty with no problems! Here you have the URL and the ChangeLog

About CoverGloobus, I've done some improvements, you can find the new link here to!!

I hope you like it!!

**[Gloobus-Preview-0.03.1]("http://jordihp.deviantart.com/art/Gloobus-Preview-0-03-1-119662155")**

**[CoverGloobus]("http://jordihp.deviantart.com/art/CoverGloobus-1-2-118080718")**

[**Donate**]("https://www.paypal.com/us/cgi-bin/webscr?cmd=_flow&SESSION=0ffR9mMKmWT2y9c0DV-04ZuX2Hsun9i2LOh44aOQ0aEdnF5nL7kGk4NGIDG&dispatch=5885d80a13c0db1f998ca054efbdf2c25fe4a05bcb33bff66824cbab1a92dde6")

ChangeLog Gloobus-Preview 0.03.1
- iComic (cbz and cbr)
- iPdf solved som bugs
- Shadow in the application
- iMp3 with ogg support
- iDocument fixed a very annoing warning
- iFolder

Installation Instructions Inside the file! (32bits and 64bits versions)

---

### Post by badchoice on 2009-04-22
Well guys!
I'm happy to anounce that I come back to gloobus-coverflow

I'll do it with clutter that can be a gtkwidget and maybe integrate it with nautilus.

So, if anyone of you would like to contribute in codding some clutter I would be very happy! I'll post some screnshoots or video when I have a descent state.

By the way, gloobus-preview works pretty well, soon it will be the 1.0 release ;)


SPREAD THE WORD!

---

### Post by Sashin on 2009-04-22
Nautilus integration with this would be awesome. Do you think it will be available by Karmic?

---

### Post by zekopeko on 2009-04-25
depends if nautilus devs build the Dbus interface for nautilus by the time karmic is out.

---

### Post by badchoice on 2009-04-25
I hope they do! ;)

---

### Post by davim on 2009-04-29
Could anyone setup a PPA repo for gloobus?

using [http://ppa-search.appspot.com/](http://ppa-search.appspot.com/) I find one repo related to gloobus but with no packages....

---

### Post by Orlsend on 2009-04-29
Ill try when theirs a deb, Also sadly its closed for translations.

---

### Post by grigio on 2009-04-30
badchoice: Thank you very much!!! Gloobus is the ideal sw to view photo and video together
Some feedback:
- the video plugin work for 5sec then **Xorg freezes** (fglrx and a ogg video file)!
- the image plugin could support image prefetching and wheel zoom

---

### Post by juancarlospaco on 2009-04-30
**[COLOR="Blue"]Gloobus.deb[/COLOR]** here:
[http://www.adrive.com/public/dd06d51c0a32392948b9fc2e19b17a651154458e76e2cd5ad195f5ad1a7a5310.html]("http://www.adrive.com/public/dd06d51c0a32392948b9fc2e19b17a651154458e76e2cd5ad195f5ad1a7a5310.html")

[IMG]http://img222.imageshack.us/img222/5306/tempf.jpg[/IMG]


[IMG]http://img26.imageshack.us/img26/2381/tempjsd.jpg[/IMG]

*have a nice day...*

---

### Post by teolemon on 2009-05-01
It does ask for libmagick10 which is not available under Jaunty.

---

### Post by badchoice on 2009-05-01
Yes.. well, it's a old version, now I'm developing gloobus-preview and gloobus-coverflow with very standard libraries, gloobus-coverflow is rewriten, using clutter now  if you take a look at my blog you'll see how it advances.

Bytheway, I've developed the iMovie plugin finally! and it works pretty well

[http://gloobus.wordpress.com](http://gloobus.wordpress.com)

---

### Post by spg76 on 2009-05-01
I tried the bzr version with the movie plugin and it's really great!
Now we just need play and stop buttons, and a seek bar to be perfect :)
Keep up the great work, Jordi.
Thanks.

---

### Post by pt123 on 2009-05-01
badchoice you clearly are very talented, why didn't you apply for any Google Summer of Code projects?

---

### Post by badchoice on 2009-05-02
Thanks, yes, I'll add pause and seek bar to the plugin, but time to time.. I have the new cluter interface... things I want to clean from preview.. if anybody would help me it would be faster! so if you know anybody with skills, present him to me!

---

### Post by teolemon on 2009-05-02
> **spg76 said:**
> I tried the bzr version with the movie plugin and it's really great!
Now we just need play and stop buttons, and a seek bar to be perfect :)
Keep up the great work, Jordi.
Thanks.

What are the steps required to compile from trunk ?

---

### Post by spg76 on 2009-05-02
> **teolemon said:**
> What are the steps required to compile from trunk ?

You have to install Bazaar and the dependencies.

```
sudo apt-get install bzr libgtk2.0-dev libgfvscommon-dev libgstreamer-plugins-base0.10-dev libcairomm-1.0-dev libtag1-dev libpoppler-glib-dev
```

Download gloobus with:

```
bzr branch lp:gloobus/gloobus-0.03 
```

Then you install gloobus-preview:

```
cd gloobus-0.03/Gloobus-Preview/
make && sudo make install
```

And for the plugins you have go to each folder and install them.
For example:
```
cd gloobus-0.03/Gloobus-Preview/iComic
make && sudo make install
```

Hope it helps you.

---

### Post by teolemon on 2009-05-02
Shame on me Shame on me. I had downloaded trunk from lp, attempted to do a ./configure and as it was spitting out that no configure file existed, i didn't even try to do a make.

Me goes in the forest to hide. :)

Edit: Just finished compiling and the new version is awesome. As soon as my finances permit, I'll donate once more.

---

### Post by badchoice on 2009-05-03
you can do a 

```

make && sudo make install && **sudo make plugins**
```

and all plugins will compile and install so you don't have to go folder by folder

;)

---

### Post by teolemon on 2009-05-04
Thanks a lot for the tip. I'll make sure to use it next time.

---

### Post by teolemon on 2009-05-05
Latest revision has issues: no more jpegs, and no more scrolling bar in pdfs. 
Also no idea on how to reach the right-click menu.

---

### Post by Orange Kingdom on 2009-05-05
I installed 0.11
I can exec gloobus-preview.

Whats the next step? How do i use it?
No read me, no documentation, no faq, nothing. :confused:

---

### Post by teolemon on 2009-05-06
The latest rev fixed my problem, but now I have something stange: 2 times the icon, and too long titles are not properly dealt with.
Also, I don't know the shortcut to get the right click menu (or more precisely, it doesn't appear when I right click)

[http://yfrog.com/a8captfrep](http://yfrog.com/a8captfrep)

---

### Post by teolemon on 2009-05-06
Here's the screenshot for problematic text overflow:
[http://img162.imageshack.us/my.php?image=captureikn.png&via=tfrog](http://img162.imageshack.us/my.php?image=captureikn.png&via=tfrog)

+ a pointer to the Clutter tutorial update:
[http://blogs.gnome.org/johannes/2009/05/06/clutter-tutorial-update/](http://blogs.gnome.org/johannes/2009/05/06/clutter-tutorial-update/)

---

### Post by coolen on 2009-05-06
Totally off topic, but that Matrix picture in the second screenshot is just too cute.

^_^

---

### Post by badchoice on 2009-05-06
Hey Teolemon!
You were right about that problem... I redesigned the code for draw the window so I can use it with classes and well, it had some countereffects. Now it's solved.

About the two images you don't see is because you haven't downloaded them. In the bzr **gloobus-preview/DATA** there are two images: **close_button.png and gloobus_button.png**, copy them in **/usr/share/gloobus** and run gloobus again.

There is no right click menu, the menu I made is like the gnome-do one, it appears when you click in the top righ image (the one you can't see right now)

Thanks for the clutter tutorial! I'll **wait till the 0.9 version** is out cause the 0.8 is still a bit buggy and the api is totally different...

Orange Kingdom:
Next steps are, configure in compiz settings or gconf that **ctrl+space**, launches gloobus-preview. Then, to see a file, ctrl+c (till nautilus develop dbus support) and ctrl+space!

---

### Post by teolemon on 2009-05-06
Gloobus Button is missing in DATA as of rev 49

---

### Post by badchoice on 2009-05-06
I'll look it, anyway, does the close_button work?

---

### Post by teolemon on 2009-05-06
Yep, but display problems as said above (another example, the close button overlays the image)
[http://img115.imageshack.us/my.php?image=capture2v.png&via=tfrog](http://img115.imageshack.us/my.php?image=capture2v.png&via=tfrog)

---

### Post by badchoice on 2009-05-06
Does it happen with all your pothos? or just with some of them?

If it only happens with some of them, can you send me one?

Thanks!

If you have a launchpad account you can upload it there!

---

### Post by teolemon on 2009-05-06
[https://bugs.edge.launchpad.net/gloobus/+bug/372683](https://bugs.edge.launchpad.net/gloobus/+bug/372683)

---

### Post by wheelie stunt on 2009-05-07
I managed to install gloobus followinng this guide into my Ubuntu Jaunty 64....

> **teolemon said:**
> Here's a quick install guide: [http://code.google.com/p/gnome2-globalmenu/wiki/Gloobus](http://code.google.com/p/gnome2-globalmenu/wiki/Gloobus)

but whenever I try to run gloobus I get this kind of log...


```
user@UbuntuJaunty64:~/Pictures/lol$ gloobus
COVER ANGLE: 70
LOADING PLUGINS:
	 /usr/share/gloobus/plugins/iFolder.so
	 /usr/share/gloobus/plugins/iPhoto.so
	 /usr/share/gloobus/plugins/iPng.so
FILE: .//Screenshot7.png
FileType: image/png
Creating iPng...
		Thread
Segmentation fault

```

I should mention that I also followed the above steps to install (compile?) the plugins (folder, photo and png as the others gave me errors when making).... I followed an advise from this thread and gave -R 777 permissions to the /usr/share/gloobus/ folder but that made no difference.... what else can I do or is it that gloobus just can't work in Jaunty64. BTW I want coverflow, not preview :twisted:

Thanks for any advise and thanks for developing this great app!

EDIT. I just noticed that those instructions are the same as those in post [#328]("http://ubuntuforums.org/showpost.php?p=7200171&postcount=328"), page 33 of this thread.

I just compiled the gloobus-preview with all the plugins with no problem whatsoever and everything works perfect..... but I want Coverflow.....

---

### Post by badchoice on 2009-05-08
gloobus is not working for now,
try gloobus-preview instead:

[http://jordihp.deviantart.com/art/Gloobus-Preview-0-03-1-119662155](http://jordihp.deviantart.com/art/Gloobus-Preview-0-03-1-119662155)

I'm developing anew version of gloobus-coverflow but now using clutter, anyway, I'll wait till they have a stable version cause there are major changes.

Hope it works for you!

---

### Post by badchoice on 2009-05-08
by the way, do you know how to create a IRC channel? I would like to create one so we can discuss some things there!

thanks!

---

### Post by teolemon on 2009-05-08
[http://freenode.net/using_the_network.shtml](http://freenode.net/using_the_network.shtml)

---

### Post by teolemon on 2009-05-09
Thanks a lot for the fix. The icon for the drop down menu is still missing in /DATA

Meanwhile, here's a quick and dirty fix.
Here's the icon from Gnome DO
[http://bazaar.launchpad.net/~do-core/do/trunk/annotate/head%3A/Do.Interface.Linux/Resources/settings-triangle.png]("http://bazaar.launchpad.net/%7Edo-core/do/trunk/annotate/head%3A/Do.Interface.Linux/Resources/settings-triangle.png")
Download it
Then:
sudo cp settings-triangle.png /usr/share/gloobus/gloobus_button.png

---

### Post by teolemon on 2009-05-09
And here's the icon, skinned and resized for Gloobus

---

### Post by teolemon on 2009-05-09
[LIST]
[*]I've updated the tutorial at: [http://code.google.com/p/gnome2-globalmenu/wiki/Gloobus](http://code.google.com/p/gnome2-globalmenu/wiki/Gloobus)
[*]I've dugg the thread (you should too, now there's Facebook integration so that you don't need to create a new account)
[/LIST]

---

### Post by teolemon on 2009-05-09
[LIST]
[*]BadChoice had added seek to the iMovie and iMusic plugins
[*]The icon bug is fixed
[*]New update to the tutorial: simplified it thanks to BadChoice's latest commit:
[LIST]
[*]sudo apt-get install bzr
sudo apt-get install libsdl1.2-dev libsdl-image1.2-dev libsdl-ttf2.0-dev libsdl-gfx1.2-dev libmagic-dev
sudo apt-get install libgtk2.0-dev libgvfscommon-dev libgstreamer-plugins-base0.10-dev libcairomm-1.0-dev libtag1-dev libpoppler-glib-dev
[*]bzr branch lp:gloobus/gloobus-0.03
cd gloobus-0.03
cd Gloobus-Preview
make && sudo make install && sudo make plugins
[*]In the bzr gloobus-preview/DATA there should be two images: close_button.png and gloobus_button.png. Copy them in /usr/share/gloobus: 
cd DATA
sudo cp *.png /usr/share/gloobus/
[/LIST]
 
[/LIST]

---

### Post by badchoice on 2009-05-10
Hey, I've released the new version, now in DEB! so no installation scripts are required, just double click! No dependences pain, the keybinding is added automatically (it uses the command1 and keybinding1 from metacity configuration)

You can download from here (both 32 and 64bits)

**[http://jordihp.deviantart.com/art/Gloobus-Preview-0-03-2-122054947](http://jordihp.deviantart.com/art/Gloobus-Preview-0-03-2-122054947)**

Changelog: [http://gloobus.wordpress.com/](http://gloobus.wordpress.com/)

---

### Post by teolemon on 2009-05-10
Congratulations!
:popcorn:

I'm now too addict to new features: I'll stay with trunk ;-)

Edit: instructions updated, and check out GlobalMenu homepage ;-)

---

### Post by shakaran on 2009-05-10
Bad news, there are some conflicts with older versions:

```
$ sudo dpkg -i gloobus-preview_0.03.2_i386.deb 
(Reading database ... 355559 files and directories currently installed.)
Unpacking gloobus-preview (from gloobus-preview_0.03.2_i386.deb) ...
dpkg: error processing gloobus-preview_0.03.2_i386.deb (--install):
 trying to overwrite `/usr/share/doc/gloobus/README.txt.gz', which is also in package gloobus
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 gloobus-preview_0.03.2_i386.deb
```

Removing older packages for gloobus:
```
$ sudo apt-get remove gloobus 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libavutil1d libdc1394-13 libmagick++10 libmagick10 openoffice.org-l10n-common libavformat1d evolution-documentation-es libavcodec1d
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gloobus
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 1016kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 355557 files and directories currently installed.)
Removing gloobus ...
dpkg - warning: while removing gloobus, directory `/usr/share/gloobus/plugins' not empty so not removed.
dpkg - warning: while removing gloobus, directory `/usr/share/gloobus' not empty so not removed.
Processing triggers for desktop-file-utils ...

```

Now install the new package:
```
$ sudo dpkg -i gloobus-preview_0.03.2_i386.deb 
(Reading database ... 355051 files and directories currently installed.)
Unpacking gloobus-preview (from gloobus-preview_0.03.2_i386.deb) ...
Setting up gloobus-preview (0.03.2) ...
Configuring the keybinding <Control>space
```

That error should be fix without apt-get remove (for next versions)

---

### Post by pt123 on 2009-05-10
am I the only one having trouble finding the link to the deb file on this page:
[http://jordihp.deviantart.com/art/Gloobus-Preview-0-03-2-122054947](http://jordihp.deviantart.com/art/Gloobus-Preview-0-03-2-122054947)

Do you have to register at deviantart to download it

---

### Post by Depressed Man on 2009-05-10
> **pt123 said:**
> am I the only one having trouble finding the link to the deb file on this page:
[http://jordihp.deviantart.com/art/Gloobus-Preview-0-03-2-122054947](http://jordihp.deviantart.com/art/Gloobus-Preview-0-03-2-122054947)

Do you have to register at deviantart to download it

Click download.

I can't get it to work though, copy+C and copy+space does nothing.

---

### Post by badchoice on 2009-05-11
Yeah, just click download in the left.

For ctrl+space to work, take a look at
> 
gconf-editor->apps->metacity->keybinding->keybinding1 = <Control>space
gconf-editor->apps->metacity->command->command1 = gloobus-preview

---

### Post by shakaran on 2009-05-11
For me not work. I don't have on Karmic these folder:

Only exists keybinding_commands for set command1, but not for keybinding1

---

### Post by badchoice on 2009-05-11
Sorry, before I hadn't a linux box to tell you the places exactly:

```
gconf-editor->apps->metacity->global_keybindings->run_command_1 = <Control>space
gconf-editor->apps->metacity->keybinding_commands->command_1 = gloobus-preview
```

It should be done automatically with the deb...
try 

```
dpgk -r gloobus-preview && dpgk -i <HERE THE DEB NAME>
```

And tell me if there appears a message saying "configurin keybinding"

Anyway here is the script:

```
#!/bin/bash

#Add the ctrl+space keybindin to gconf
echo "Configuring the keybinding <Control>space"
gconftool-2 -s --type string /apps/metacity/keybinding_commands/command_1 "gloobus-preview"
gconftool-2 -s --type string /apps/metacity/global_keybindings/run_command_1 "<Control>space"
```

---

### Post by pt123 on 2009-05-11
> **Depressed Man said:**
> Click download.


Thanks was looking for a file link with .deb.

---

### Post by pt123 on 2009-05-11
are these deb packages for Intrepid?
as I get this error: Dependency is not satisfiable for libpoppler-glib4

When I search for it in synaptic I can only find  libpoppler-glib2

---

### Post by badchoice on 2009-05-11
The deb is for jaunty...

Anyway, I'll change the deb so it can run in intrepid too

---

### Post by pt123 on 2009-05-11
Thanks :)

---

### Post by shakaran on 2009-05-11
> **badchoice said:**
> Sorry, before I hadn't a linux box to tell you the places exactly:

```
gconf-editor->apps->metacity->global_keybindings->run_command_1 = <Control>space
gconf-editor->apps->metacity->keybinding_commands->command_1 = gloobus-preview
```

It should be done automatically with the deb...
try 

```
dpgk -r gloobus-preview && dpgk -i <HERE THE DEB NAME>
```

And tell me if there appears a message saying "configurin keybinding"

Anyway here is the script:

```
#!/bin/bash

#Add the ctrl+space keybindin to gconf
echo "Configuring the keybinding <Control>space"
gconftool-2 -s --type string /apps/metacity/keybinding_commands/command_1 "gloobus-preview"
gconftool-2 -s --type string /apps/metacity/global_keybindings/run_command_1 "<Control>space"
```

I run this command (sorry for $LANG Spanish, I forget changed, but badchoice is Spaniard)

```
$ sudo dpkg -r gloobus-preview && sudo dpkg -i gloobus-preview_0.03.2_i386.deb 
(Leyendo la base de datos ...  
355077 ficheros y directorios instalados actualmente.)
Desinstalando gloobus-preview ...
Removing the keybinding <Control>space
dpkg - atención: al desinstalar gloobus-preview, el directorio /usr/share/gloobus'
no está vacío, no se borra.
Seleccionando el paquete gloobus-preview previamente no seleccionado.
(Leyendo la base de datos ...  
355061 ficheros y directorios instalados actualmente.)
Desempaquetando gloobus-preview (de gloobus-preview_0.03.2_i386.deb) ...
Configurando gloobus-preview (0.03.2) ...
Configuring the keybinding <Control>space
```

The message always show you, because is a echo, no there is a condition for not show these message or similar.

If on Karmic these directories for keybindings not are the same, then it not work.

The bash script doesn't help.

---

### Post by badchoice on 2009-05-11
I haven't tested it on karmic. 
Do you have those values in the gconf-editor? or something similar?

You just need to bind ctrl+space to "gloobus-preview" command.

You can also set it with compiz settings manager

---

### Post by shakaran on 2009-05-11
Yeah! With compiz settings manager it works!
The run_command appears empty, I put the <Control>space and now works ;) Maybe the values don't get set before for some reason unknown.

Thanks ;) You rise you probability for donations ;)

---

### Post by DJ_Peng on 2009-05-11
> **pt123 said:**
> Thanks was looking for a file link with .deb.
At the risk of asking a silly question, I understand that you may have needed to put the files into a .tar.gz to upload it, but is there a reason why once I got it extracted from the downloaded file that I had to perform a second layer of extraction?

Also, the GetDeb link on yoru Launchpad brings me to the GB home page, rather than a Gloobus page on GB.

---

### Post by joey-elijah on 2009-05-11
If you're running compiz, you have to make sure 'Commands' are enabled! (Find them in CompizConfig under 'General'.)

---

### Post by badchoice on 2009-05-11
DJ_Peng: About the compression... I compressed it in the bad format, I'll upload it againt with some deb changes when I go home.
About the link in launchpad, you're right... I'll change it as soon as I get home!

shakaran: It would be so good!! I spent a lot of hours developing it, and I'll spend a lot more

---

### Post by pierissimo on 2009-05-11
when i launch gloobus-preview get these:
```
piero@pnblin:~/Immagini$ gloobus-preview Altitude.jpg 
Creating Window...LOADING PLUGINS:
	 /usr/share/gloobus/plugins-preview/iComic.so
	 /usr/share/gloobus/plugins-preview/iFolder.so
	 /usr/share/gloobus/plugins-preview/iMp3.so
	 /usr/share/gloobus/plugins-preview/iMpg.so
	 /usr/share/gloobus/plugins-preview/iPdf.so
	 /usr/share/gloobus/plugins-preview/iPhoto.so
	 /usr/share/gloobus/plugins-preview/iPlain.so
CONTENT FOLDER: Altitude.jpg
Error(20) opening Altitude.jpg
Segmentation fault
```

a segmentation fault, I installed it with the deb package.
Why?

---

### Post by pierissimo on 2009-05-11
> **pierissimo said:**
> when i launch gloobus-preview get these:
```
piero@pnblin:~/Immagini$ gloobus-preview Altitude.jpg 
Creating Window...LOADING PLUGINS:
	 /usr/share/gloobus/plugins-preview/iComic.so
	 /usr/share/gloobus/plugins-preview/iFolder.so
	 /usr/share/gloobus/plugins-preview/iMp3.so
	 /usr/share/gloobus/plugins-preview/iMpg.so
	 /usr/share/gloobus/plugins-preview/iPdf.so
	 /usr/share/gloobus/plugins-preview/iPhoto.so
	 /usr/share/gloobus/plugins-preview/iPlain.so
CONTENT FOLDER: Altitude.jpg
Error(20) opening Altitude.jpg
Segmentation fault
```

a segmentation fault, I installed it with the deb package.
Why?

ok i got it works.. it need absolute paths

---

### Post by badchoice on 2009-05-11
add the ./

```
gloobus-preview ./attitude.jpg
```

or just ctrl+copy the file and ctrl+space

---

### Post by Fzang on 2009-05-11
Okay this might sound very stupid but...

How do you use this? When I press the spacebar, BAM... the default application opens up my file... I can't find or launch gloobus anywhere. I installed it from the .deb for Jaunty..

Do I need to do something special to "invoke" it or have I simply done something wrong and need to install again?

---

### Post by shakaran on 2009-05-11
@Fzang: You need press Ctrl + Spacebar on a file for execute gloobus-preview. If not work, you need enable the keybinding in gconf-editor or compiz-settings-manager (if you use compiz).

---

### Post by Depressed Man on 2009-05-11
This is unrelated to gloobus (it's for the other application for music covers). I dunno if there's a thread for it yet. But anyway, does it work with Songbird? I set it to Songbird in the settings but now it covergloobus doesn't start up when I turn it on.

---

### Post by badchoice on 2009-05-12
Depressed Man: Covergloobus dosn't work with songbird yet... there is no a good DBUS support for it, anyway, if you a way to interact with it, please let me know and I'll check that up!

---

### Post by Fzang on 2009-05-12
Exactly how do I bind gloobus to my keys? I'm not good at this :D

---

### Post by Depressed Man on 2009-05-12
> **badchoice said:**
> Depressed Man: Covergloobus dosn't work with songbird yet... there is no a good DBUS support for it, anyway, if you a way to interact with it, please let me know and I'll check that up!

Ah ok. I figured (odd that there was a Songbird option though).

---

### Post by Holmen on 2009-05-17
Thank you for a greal looking piece of OSS! Together whith Gnome-Do, this is my favorite. BUT - isnt there a way to start gloobus-preview by just got the file selected? Not havin' to press Ctrl+C first, I mean.

This is how it works now:
1. Mark/select a file.
2. Ctrl+C
3. Open Gloobus-Preview by ie. Ctrl+Space.

I would like it to work lite this:
1. Mark/select a file.
2. Run Gloobus!

I'm quite new with the programming, is this hard to to, or is it that you prefer to have it like it is?

Cheers and keep up the awesome work! I will give you a donation under the summer here in Sweden ;)

---

### Post by teolemon on 2009-05-17
No, it's not by design. It's because Nautilus won't let us easily do this. The idea would be to bind it to the spacebar: select the fine, hit SPACE.

---

### Post by badchoice on 2009-05-18
Holmen: 
Yes, I would like that but I need something from nautilus, this is the dbus support so I can connect and get the selected files... so, till then, a ctrl+c is required...

I'm looking forward to your donation ;)

Have you seen the new 3D coverflow implementation?

[http://gloobus.wordpress.com](http://gloobus.wordpress.com)

---

### Post by Sashin on 2009-05-18
You know what would be really awesome, if this was fully intergrated with nautilus. So that there'd be an icon view, a list view, a compact view and a coverflow view.

---

### Post by joey-elijah on 2009-05-18
> **Sashin said:**
> You know what would be really awesome, if this was fully intergrated with nautilus. So that there'd be an icon view, a list view, a compact view and a coverflow view.

Wasn't there mention of the Gnome team looking at this?

---

### Post by coolen on 2009-05-18
That's surprising. I would've thought they'd reject it out of hand for being too OSX-like.

It would definitely be cool. Best for multimedia-heavy folders, like music or picture folders. I also imagine you'd need some kind of rapid search functionality within the folder.

Very, very cool.

---

### Post by conundrumx on 2009-05-18
GNOME in particular has to walk a very fine line when it comes to taking features from OSX.  Apple is pretty quick to try and fight anyone copying what it views as unique UI elements.  There was a lot of noise over people copying the Dock back when it was new and exciting, I'm sure the GNOME team will be wary (at best) of any full on integration with Gloobus.

Their best bet is to simply open up things for Gloobus to interface with and say "well we didn't do *that*."

---

### Post by pt123 on 2009-05-18
looks sweet,

on the gloobus preview isn't ctrl+c a "copy" function.

---

### Post by pt123 on 2009-05-18
> **joey-elijah said:**
> Wasn't there mention of the Gnome team looking at this?
what like in 2018, Gnome is so slow to implement, I am still waiting for the ability to have different wallpapers on the different workspace.

---

### Post by badchoice on 2009-05-19
Hi guys!
I would like to ask you something,

Could anyone of you develop a nautilus extension (like nautilus-open-terminal) that launches gloobus <directory> and another one that launches gloobus-previes <directory>/<filename>

because I would like to include it in the deb and I prefer wasting my time in the application itself ;) I don't think it's hard so I hope you can help me in this.
I've gloobus coverflow in a very good state so in a week or two I'll upload the deb ;) !!! it's amazing!! HEHEHEHE

Thanks!

And of course.. if you want to donate me something I would appreciate it!

---

### Post by Sashin on 2009-05-19
While I can't help you, I can't wait to see what happens in a week or two.

---

### Post by nortexoid on 2009-05-23
How do you install and use covergloobus?

Any plans to support .doc?

Gnome needs something like this natively.

---

### Post by badchoice on 2009-05-25
[http://gloobus.wordpress.com](http://gloobus.wordpress.com)

Again, new version, now you can download and test the coverflow, Coverflow is still not very stable and well working, but is fair enough, if you see bugs fill them in launchpad ;)

You can download here:

[http://jordihp.deviantart.com/art/Gloobus-0-4-123645797](http://jordihp.deviantart.com/art/Gloobus-0-4-123645797)

Installation instructions:

1. Install gloobus-preview

2. Install gloobus

3. Import the *.schemas into nautilus actions (For menu entries)

4. Add the keybinginds (Here's a complete guide on how to bind the key)

Link

5. Enjoy!

6. Donate!!

---

### Post by Sashin on 2009-05-25
How do we import that file into nautilus actions?

---

### Post by Sashin on 2009-05-25
I think I've figured it out, but it's not intergrated into nautilus in anyway.

One question, with preview, why is the close button on the left hand side of the window?

---

### Post by Sashin on 2009-05-26
Okay the extension is working now by right click. My main problems is that in coverGloobus it doesn't used the icons from the GTK theme as well as not being able to navigate inside of covergloobus.

Would also be nice if you change the close button of the preview thing to the right hand side for consistency. I keep closing it wrong and accidently going to your blog.

This and a cooliris view in nautilus would be awesome.

---

### Post by badchoice on 2009-05-26
Sashin.. about the close button... I use the mac theme, so the left side is better for me, but anyway, you can close it just pressing space key (I allways close it this way)

About the navigation in the coverflow..I working on it but its a long term feature ;)

---

### Post by Sashin on 2009-05-26
Maybe you should make it customiseable, so it can be set to the left or the right.

---

### Post by nzjrs on 2009-05-26
Hi,

I spent some time integrating Gloobus inside nautilus

There is no animation or keyboard movement, I have done very little so far. I have just started to port Gloobus from C++ into a ClutterGroup derived Actor in C. I have also made the necessary changes to Nautilus.

If you would like to take a look, the steps for testing it are

1) Download nautilus from my Git repository (the clutter branch)

[https://github.com/nzjrs/nautilus/tree](https://github.com/nzjrs/nautilus/tree)

2) Build the test program.

cd src/file-manager
make -f Makefile.covflow && ./test-covflow

3) Built nautilus with --enable-clutter-view
4) cd src ; ./nautilus -q ; ./nautilus --no-desktop

See attached screenshot

---

### Post by nzjrs on 2009-05-26
I also emailed Jordi. We would both appreciate help with this. I might spend some more time working on this over the next few nights, but it is more of a proof of concept so far.....

---

### Post by teolemon on 2009-05-27
Stunned, and in awe. I'll now have to make you a donation as well.

Edit:I just realized who was behind (nzjrs). It's fantastic. :-)

---

### Post by Sashin on 2009-05-27
I'd love nautilus integration as well, but as of now the instructions are too complex to me. I don't understand step 4. But this is an indication that everything is going in the right direction, I hope this'll use our GTK icon theme...

---

### Post by nzjrs on 2009-05-27
I just posted some more information here:

[http://www.johnstowers.co.nz/blog/index.php/2009/05/27/playing-with-clutter/](http://www.johnstowers.co.nz/blog/index.php/2009/05/27/playing-with-clutter/)

---

### Post by nzjrs on 2009-05-27
Jordi and I spent a bit more time on this, and it is starting to look OK. I would appreciate it if people could check if this builds for them.

---

### Post by Sashin on 2009-05-28
I would but I can't make sense of your instructions, how exactly do I build a program? I've only been able to install from repositories and deb files.

---

### Post by teolemon on 2009-05-28
> pierre@pierre-laptop:~$ git clone git://github.com/nzjrs/nautilus.git
Initialized empty Git repository in /home/pierre/nautilus/.git/
remote: Counting objects: 105584, done.
remote: Compressing objects: 100% (17851/17851), done.
remote: Total 105584 (delta 87660), reused 105344 (delta 87473)
Receiving objects: 100% (105584/105584), 96.39 MiB | 331 KiB/s, done.
Resolving deltas: 100% (87660/87660), done.
warning: remote HEAD refers to nonexistent ref, unable to checkout.
I can't clone it. Am I missing smg ?
Googling suggests to run git update-server-info on the remote server.

I then proceed to download a tar archive of the git repo.
First instruction ok, but then:
> Package clutter-gtk-0.9 was not found in the pkg-config search path.
Perhaps you should add the directory containing `clutter-gtk-0.9.pc'
to the PKG_CONFIG_PATH environment variable
No package 'clutter-gtk-0.9' found
I don't seem to have any such package. Should I install another package, and if not, how to set the PKG_CONFIG_PATH

OHand mailing lists says:
export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig:${PKG_CONFIG_PATH}

---

### Post by teolemon on 2009-05-28
The compilation instructions for Gloobus-Preview and Gloobus-Coverflow have been updated:
[https://answers.edge.launchpad.net/gloobus/+question/71671](https://answers.edge.launchpad.net/gloobus/+question/71671)

---

### Post by davim on 2009-06-01
WoW this looks great :)

Great Job :)

---

### Post by Fzang on 2009-06-01
Check out this thread

[http://ubuntuforums.org/archive/index.php/t-659294.html](http://ubuntuforums.org/archive/index.php/t-659294.html)

Maybe it can help adding the gloobus button. I don't know what you'd have to enter as command though..

---

### Post by DJ_Peng on 2009-06-01
That rocks, Fzang. Thanks for posting the link.

---

### Post by badchoice on 2009-06-01
I've created the ##gloobus chanel in freenode ;) feel free to join us!

---

### Post by badchoice on 2009-06-03
To test the nautilus version John and me are working on

 ```
git clone git://github.com/nzjrs/nautilus.git
 git checkout origin/clutter
 cd src/file-manager/
 make -f Makefile.covflow && ./test-covflow
```

This will launch the C version, not inside nautilus,

to see it inside nautilus

 ```
cd ..
 ./autogen.sh --disable-tracker --disable-beagle --disable-xmp --enable-clutter-view --prefix=/usr
 make
```

(No need to install)

To try it out:

```

 ./nautilus -q
 ./nautilus --no-desktop

```

If you have any problem, please let me know!, to build nautilus there are some dependences needed
(gnome-comon, gnome-desktop, libunique and dbus-glib)

Then, when you pull the git for newer versions,

```

 cd src/file-manager && make -f Makefile.covflow && ./test-covflow
 cd .. 
 make

```

---

### Post by teolemon on 2009-06-05
[https://answers.edge.launchpad.net/gloobus](https://answers.edge.launchpad.net/gloobus)
Here are some updated instructions for: Gloobus-Nautilus, Gloobus-Preview and Gloobus-Coverflow

Let me know if they work well (or not)

---

### Post by Sashin on 2009-06-11
So, how's progress going along?

Is there a goal for a working .deb like by the end of July or something?

---

### Post by conchiuro on 2009-06-12
is there any way to make covergloobus  works with exaile?

---

### Post by davim on 2009-06-29
So! No news?

---

### Post by zekopeko on 2009-06-29
> **davim said:**
> So! No news?

try [www.gloobus.wordpress.com](www.gloobus.wordpress.com)

---

### Post by davim on 2009-07-01
> **zekopeko said:**
> try [www.gloobus.wordpress.com](www.gloobus.wordpress.com)

Nothing new there, the last post is 1 month old... :p

---

### Post by badchoice on 2009-07-01
Hey!

I've been very busy last days, I'm reformating a flat so I can live there, and I need cash so I'm doing some payed jobs in my free time.

I don't know how long it will take but as soon as I finish it, I hope I can work in gloobus again!

---

### Post by davim on 2009-07-02
Thanks for the update :)

Good luck with your flat :)

---

### Post by yuli_capone on 2009-07-02
A short question:
How can i make the theme smaller?
Or I have to wait new versions?

Thanks!

---

### Post by badchoice on 2009-07-02
Are you asking about covergloobus or about gloobus-preview?

About covergloobus, the theme can't be resized, but you can resize yourself the images and then, just modify the sizes in the xml file (very very easy), if you have any problem, please contact me and I'll try to help you!

---

### Post by yuli_capone on 2009-07-02
About coverglobus,sorry.
I resize the images.In the xml what should I change and how I modify the file?

---

### Post by badchoice on 2009-07-02
In the xml you need to change the size of each item, and then the position of the texts, for example, there is the line

<image src="bottom.png" 	x="32" y="8"  width="200" height="200"/>

x and y is the top left position of the bottom image, and then widht and height is the size of the image you just resized, you can do it with all the images you resize, and then you can change the x and y of each text item

I hope it helps you! if you finally get it, send it to me and I'll publish it!!

---

### Post by omargohan on 2009-07-10
When is coming out the new version?

BTW, pretty cool app!

:guitar:

---

### Post by teolemon on 2009-07-12
> **badchoice said:**
> Hey!

I've been very busy last days, I'm reformating a flat so I can live there, and I need cash so I'm doing some payed jobs in my free time.

I don't know how long it will take but as soon as I finish it, I hope I can work in gloobus again!

This is what Badchoice has to say about it.

---

### Post by nzjrs on 2009-07-12
> **teolemon said:**
> This is what Badchoice has to say about it.

I also got busy. Those with hacking skills are invited to help. The code for the nautilus integration part is still at

[http://github.com/nzjrs/nautilus/tree/clutter](http://github.com/nzjrs/nautilus/tree/clutter)

---

### Post by pt123 on 2009-07-25
Any updates on Nautilus using DBUS?


Searching through the internet Gnome-Do is also interested in this, (rather surprising why would one create this dbus architecture and not have the File Manager use it).

There doesn't seem to be any update:
[http://bugzilla.gnome.org/show_bug.cgi?id=498506](http://bugzilla.gnome.org/show_bug.cgi?id=498506)

Even a Google SoC project request but no update
[http://www.mail-archive.com/nautilus-list@gnome.org/msg05628.html](http://www.mail-archive.com/nautilus-list@gnome.org/msg05628.html)

Someone has even wrote some code on it
[http://code.google.com/p/nautilussvn/source/browse/other/NautilusDBus.py](http://code.google.com/p/nautilussvn/source/browse/other/NautilusDBus.py)

---

### Post by davim on 2009-08-01
Is there anyone working on this project now? Is it staled? Please dont let this die!

---

### Post by badchoice on 2009-08-24
Hi again! I've my flat ok, and I'm back of my holidays so I'm ready to work on gloobus again!!!

I want to create a project webpage but I'd like some help, do you know a free hosting? any of you wants to design the webpage? something like gnome-do (Its really good!!) I'm sure this will help people to know about gloobus.

The second and really interesting: KitKat had developed a patch for nautilus that LAUNCHES GLOOBUS-PREVIEW WITH THE SPACE KEY!! I tried it with my both computers and it works perfectly!

To install it

download the lastest stable nautilus:
[ftp://ftp.gnome.org/mirror/gnome.org/sources/nautilus/2.26/nautilus-2.26.3.tar.gz](ftp://ftp.gnome.org/mirror/gnome.org/sources/nautilus/2.26/nautilus-2.26.3.tar.gz)

Download kitkat patch (File attached)

```

tar zxvf archive.tar.gz
cd nautilus-2.26.3
patch -p1 < /path_to_my_patch

```

u ll see the files been patched here

all u have to do is compile nautilus now:
```

./configure --prefix=/usr 
make

```

at this step u can already test nautilus by lauching it (close it before if is runing with 
```

nautilus -q
./src/nautilus 

```

without deleting your distribution version
if u like the patch u can do a make install too ;)

Today I'll try to solve some bugs in the bugtrack so I familiarize with the code again and then I'll try to add some new things!!

See you!

---

### Post by Sashin on 2009-08-24
Awesome that you are working on this again.

What kind of site are you after? What do you need in it?

If you want I could make one, based on wordpress 
(I can make it similar if not better to the gnome-do site, and have your blog etc integrated).
If you want me to, can you give me a good picture of gloobus coverflow in action? To use as the main display.

You could get a .co.nr domain on it for free or even buy one if you want.

---

### Post by badchoice on 2009-08-24
Hey! Thanks for the reply!
I just want three things

1. A good interface so the people get attracted to it
2. A place where the features can be listed (video and images included)
3. Documentaion on how to use it, how to develop a plugin, and how help in the project

And a donate button visible, maybe with this I can buy a gloobus.net or something like this

What do you think¿
Someone in my blog said me that he can help in the design but not coding.. maybe we can do it togheter  :D

---

### Post by Sashin on 2009-08-24
So you have no problem in me using wordpress so long as the end result is good?

---

### Post by Sashin on 2009-08-24
I have some kind of an idea for the design, I'm thinking black. Coverflow is a really slick feature so we need site to match it.

When you can upload a picture of it in action, I'll be able to use it.

---

### Post by badchoice on 2009-08-24
No problem at all ;)

---

### Post by badchoice on 2009-08-25
Are any of those pictures good?

[http://jordihp.deviantart.com/art/Gloobus-Preview-0-03-2-122054947](http://jordihp.deviantart.com/art/Gloobus-Preview-0-03-2-122054947)

[http://jordihp.deviantart.com/art/Gloobus-Preview-0-03-1-119662155](http://jordihp.deviantart.com/art/Gloobus-Preview-0-03-1-119662155)

[http://jordihp.deviantart.com/art/Gloobus-0-4-123645797](http://jordihp.deviantart.com/art/Gloobus-0-4-123645797)

---

### Post by hanzomon4 on 2009-08-25
Slick.... linux has some hotness coming it's way. Is this a Macslow project?

---

### Post by badchoice on 2009-08-25
It isn't macslow project, is a new one.
I hope you like it!

---

### Post by Sashin on 2009-08-25
Those are good but could you take one with coverflow in nautilus maximized or even just coverflow full screen. And have media files displayed, like music, and video or even pdfs or documents with the thumbnailer plugin.

-->[http://d0od.blogspot.com/2009/08/openoffice-thumbnails-linux-nautilus.html](http://d0od.blogspot.com/2009/08/openoffice-thumbnails-linux-nautilus.html)

If you've added custom icons your home folder would work well as well

this is what I mean by custom icons :[http://i39.tinypic.com/2mmsl91.jpg](http://i39.tinypic.com/2mmsl91.jpg).

---

### Post by badchoice on 2009-08-25
Ok, when I get home I'll take them,
Anyway, about the gloobus inside nautilus, i think is better to wait for it cause it's not working yet and the people will ask for it..

I'll take screenshots of

1. Pdf file preview
2. Mp3 file preview
4. Movie preview
5. Coverflow in a folder of diferent kind of files (full screen)
6. PSD and XFC preview
7. Openoffice files preview

---

### Post by Sashin on 2009-08-25
Okay that sounds pretty good.

---

### Post by Sashin on 2009-08-25
As for hosting, this might be good.

---

### Post by loomsen on 2009-08-30
Hi.

I'm somewhat disappointed. This could be a very good project, but it's already so inconsistent that you should really consider breaking now and starting to follow common package naming rules. Otherwise I don't see how this should ever be supported by any non debian distro. 

I just finished with the 0.025 (horrible version string) cause 0.3-Preview sounds like it's not stable yet. But actually 0.4 is out already o.O

ok, went onto that, but other than being given a src tarball, after a while I found
Gloobus_0_4_by_JordiHP.gz

this.

This ain't never ever going to work as intended (and I'm not talking about the code)

I'd really appreaciate it if you'd consider doing all of us a favor and resetting the version string in order to get in touch with debians (or any other consistant package naming policy)

It might look similar, but 
(0.4-0.03) != 0.1

0.4 - 0.03 = 0.37

Further it would be reasonable to differe between main release versions, release versions and bug fixes.

0.4.0-1 for example, a bugfix causes this bump:
0.4.0-2 while some change in the package itself, like replacing png with svg for example bumps
0.4.1-1 Only a serious revision and new functionality should bump 
0.5.0-1

this way the whole project would be maintainable for other distributions, but like this, if another distro wants to include your package, there's nothing reliable. Basically I just had to repackage it. So please, get in touch with the debian policy, so that more people will be able to use your app.

As I said, I'm only refering to the horrific naming so far. 
I'd really appreaciate transparent and consistant version and name handling. This is, Gloobus-0.4 shouldnt extract itself to gloobus-0.4 nor to RELEASE, but to Gloobus-0.4

However, naming the source gloobus would be even more appropriate. 

Please choose _only ONE_ typo for this, and keep it. 

Like this it is currently impossible to write a generic spec file for rpm distros for instance. The arch package is built from bzr, otherwise this would look similar ( PKGBUILD in arch == SPEC(ification) file in rpm ) 

Thank you.

---

### Post by badchoice on 2009-08-31
Hi Loomsen

Thanks for you instructions! when I started with gloobus I dindn't know so much about linux, and didn't know anything about pakaging. I'm learning it now, and I tried to update gloobus version to a common package name.

First, note that there are two diferent packages in gloobus, gloobus itself that is the coverflow, and gloobus preview, that is the preview function that is launched when you press ctrl+c - ctrl+space (I don't know how to make it to configure automatically) 
Or thanks to kitkat patch to nautilus, it can be launched just pressing space.

So now, the version I'm working on is gloobus-0.4 and gloobus-preview-0.4, so I think, after reading your post, that it should be gloobus-0.4-1 and gloobus-preview-0.4-1.

As you can see, the first versions 0.0.2 and those strange names now are not developed anymore, it was using a very diferent architecture, and in 0.3 I started it again from 0.

I looked at your specs file in launchpad, and there are some SDL dependences that are used by the 0.0.2X versions, now are no longer required.

That name is because of deviantART, it changes the name, I will upload the gloobus-0.4.tar.gz and gloobus-preview-0.4.tar.gz in launchpad so it can be download as in any usual package.
and of course, if you find something else to change, please let me know that I'll change it!

Thanks a lot for you help!

---

### Post by kirsis on 2009-08-31
I'd just like to chime in and say a big thanks for this project.

Gloobus Preview provides functionality that I dearly missed from Mac OS X, when using Linux. It speeds up my workflow and makes the whole work experience more pleasurable.

I'm compiling nautilus now, so that I can launch it with Space. Big thanks to the patch author as well.

---

### Post by badchoice on 2009-08-31
You're welcome!

I'm glad you like it!

---

### Post by loomsen on 2009-08-31
Yes, I've seen that 0.02 and 0.03 are obsolete but just after I already finished writing the spec.

I'm gonna take a look into 0.4 when I find some time this week and let you know then.

And yes, it would be important to have a commonly accessible location for the source as for example rpm can download the source based on the URL in the specs file.

So, thank you for fixing this. I'll let you know about 0.4 spec when I'm done.

*edit*

@gloobus / gloobus-preview

Actually, it shouldn't be split into two packages, this would only cause unnecessary clobber. 
Either create a subdirectory for preview, or, if they use the same files anyway, just leave it.
An application may register more than one binary, gajim for example installs 
gajim (#the main app)
gajim-remote (#to act with gajim  using dbus for example)
gajim-history-manager (#used to browse history logs)

This would succeed the dependency of gloobus related to gloobus-preview, and you can easily integrate this in your source for new functions or so.

The main directory of your source should include Makefiles and configuration files, the README for installation purpose and the INSTALL for the same purpose. 

Then there should be a doc subdirectory for instance, holding the documentations for the program itself. And so on, I'll have to take a closer look at the source and I'll propose some dir structure.

gajim might be a good example as it's available for any distribution, and it's maintained on TRAC.

[http://trac.gajim.org/browser/](http://trac.gajim.org/browser/)

Use apt-build --source (I think it was in debian) to get source packages from your apt-repos.
This will download 
foo.src.tar.gz.orig
foo.src.tar.gz.diff
and the source to build itself, tho I'm not too sure cause I haven't used debian for a while.
But it shows how packages are usually maintained and with my example above you should figure out I think :)
However, sources are version bumped for main release versions, and patched for release versions.

[antiright for example](http://www.very-clever.com/download/nongnu/antiright/)

It's appropriate as an example. Or grab the gedit source or some basic app and look at it.

---

### Post by badchoice on 2009-08-31
Loomsen,
Thanks for you really good explanation,
I'll take care of all your suggestions, and try to make it as standard as possible, next thing I'm gonna do is rename the source files cause now they have not a standar names at all. (I've reported a bug in launchpad)

About the docs folder, I should create the docs for gloobus cause if I stay some time out and then I come back to the project, I need to spend some hours tring to figure out how it works again.. but as you know, creating a good docs take a lot of time and I prefer coding, anyway, I'll try to use one of those apps that create the docs automatically ;) (Do you know a good one)

I've just downloaded the pakages you mentioned and I'm gonna take a look to them to see how it is structured

Regards,

---

### Post by loomsen on 2009-08-31
Hi,

here's a draft.
[http://omploader.org/vMjk4OQ](http://omploader.org/vMjk4OQ)

I wrote comments into the Readmes in each folder.

It's by no means complete, but should give you a base to start from.

I'm gonna contribute as far as possible.

---

### Post by loomsen on 2009-08-31
Hello.

I'm gonna take this thread to inform you what I'm currently doing so we can keep in touch.
You may add me in jabber if you have it. If not there's a link in my sig how you can set it up for another IM protocol like ICQ, so you won't have to get it for these purpose only.

However, the current was to set the shortcuts binding is rather rude and set it to command_1 no matter if this is set already. I wrote a little while loop to check for unset commands and take the first unset slot to set the binding.
*edit*
Corrected both, postin and postun
Proper postint and postun scripts should look like
```

#!/bin/bash
## pre installation
i=1
_A="/apps/metacity/keybinding_commands/command_$i"
while [[ "`gconftool-2 -g $_A`" != "" ]] ; do 
	i=`expr $i + 1`
	_A="/apps/metacity/keybinding_commands/command_$i"
done

echo "`basename $_A` is unset yet, will set it to \"gloobus-preview\""
# doit
#gconftool-2 -s --type string $_A "gloobus-preview"

_B="/apps/metacity/global-keybindings/run_`basename $_A`"
echo "keybindings for $_B set to \"<Control>space\""
# doit
#gconftool-2 -s --type string $_B "<Control>space"
```
and
```

#!/bin/bash
## post uninstallation
i=1
_A="/apps/metacity/keybinding_commands/command_$i"
while [[ "`gconftool-2 -g $_A`" != "gloobus-preview" ]] ; do 
	i=`expr $i + 1`
	_A="/apps/metacity/keybinding_commands/command_$i"
done

echo "Unsetting $_A "
# doit
#gconftool-2 -s --type string $_A ""

_B="/apps/metacity/global-keybindings/run_`basename $_A`"
echo "Unsetting keybindings for $_A"
# doit
#gconftool-2 -s --type string /apps/metacity/global_keybindings/run_`basename $_A` "disabled"

```
Something like that. I have command 1 set to compiz deskmenu, so I wouldn't appreciate it if it was overwritten.
*/edit*

> 
[COLOR="Red"]docter[~/tmp/tests][/COLOR] sh while-test-gconf.sh 
command_2 is unset yet, will set it
[COLOR="Red"]docter[~/tmp/tests][/COLOR] 


*edit-2*
Here are the patches:
postinst
[http://omploader.org/vMjk5OQ](http://omploader.org/vMjk5OQ)
prerm
[http://omploader.org/vMjk5YQ](http://omploader.org/vMjk5YQ)

apply with 
patch -p1 postinst < postinst.patch
patch -p1 prerm < prerm.patch

This would bump 0.4.0-1 to 0.4.1-1

*final edit*
And here's the spec file included the source package I built it from. 
Still for documentation purpose, and I couldn't test the package yet neither cause I currently don't have a test OS setup, but I'm gonna go for it the next few days.
I named it 0.4.1-1 but please don't release or try to do anything with this package, it's still only a draft.
Please look at it and read the files i included too bad. This is no replacement for the example package above, which basically is targeted on how the development directory structure could look like.

And this package only packs the binaries, would be nice if you could open all source files (maybe following the structure from the package above or so.) 
Hope this gives you an idea what could, will and might be of importance if this project happens to grow further.
[http://omploader.org/vMjlhaA](http://omploader.org/vMjlhaA)

---

### Post by badchoice on 2009-09-02
Hey!

I'm gonna apply the patch right now, of course this is really a better version, It is a solution for the people that don't want to use the patched nautilus that launches gloobus with just pressing space.

I've a jabber account, is a gmail account but in pidgin I can use it without any problem my account is j.hernandezp at gmail dot com

Right now I'm changin the names of all source files to make them more standard, I'll do something like this 

[https://bugs.launchpad.net/gloobus/+bug/421846](https://bugs.launchpad.net/gloobus/+bug/421846)

When I get it done (I have to change all source files, makefiles etc..) I'll release the pakage, binaries with source, trying to follow the standars.

Anyway, I would like to contact you before so you can help me if something is wrong!

Thanks!

---

### Post by davim on 2009-09-03
Could you set a ppa repo for the gloobus packages?
Thanks :)

---

### Post by badchoice on 2009-09-03
> **davim said:**
> Could you set a ppa repo for the gloobus packages?
Thanks :)

Tualatrix helped me setting one up:

[https://launchpad.net/~tualatrix/+archive/gloobus](https://launchpad.net/~tualatrix/+archive/gloobus)

Its not complete, but its a start

---

### Post by davim on 2009-09-03
> **badchoice said:**
> Tualatrix helped me setting one up:

[https://launchpad.net/~tualatrix/+archive/gloobus](https://launchpad.net/~tualatrix/+archive/gloobus)

Its not complete, but its a start

great :) thanks :D

---

### Post by coolen on 2009-09-03
:O

Gloobus has a repo.

This is the most exciting thing to happen to me all month!

---

### Post by badchoice on 2009-09-03
loomsen:

I've renamed almost everything files in gloobus-preview and gloobus-coverflow so now there are no capital letters and the namings follow a more common rule.

About the preinst script, I noticed that is ran by user root, so it changes root schema not users one. Anyway, kitkat made a nautilus patch to launch it just pressing space, and this is the best way, but I don't know how to add it in the package..

What do you think of the naming now? you can get a copy of the code with

```
bzr branch lp:gloobus
```

Thanks!
See you

---

### Post by badchoice on 2009-09-04
By the way, anybody knows how to write a gtklabel  using a font from a file, without using the installed ones?

Thanks!!

---

### Post by loomsen on 2009-09-06
Hello.

Sry, I didn't find much time the last couple of days, I'm gonna take a look into this.

Thanks, seems like we got this going :)

---

### Post by DJ_Peng on 2009-09-06
I love the fact that there's now a PPA for Gloobus. It was an easy-peasy update now that I finally got my computer back from the dead (not sure how, and I hope it doesn't die again like it did a couple of weeks ago). Now I'll just have to take some time to remember how to use it. ;)

There is one slight problem I found in your updated OP while looking for you blog (Epiphany didn't have a bookmark yet and it rolled off the history):
> **badchoice said:**
> //============= EDITED 10/05/2009 ==================== //
I think you meant to date that **09**-05-2009.

Are there plans to add CoverGloobus to the PPA?

---

### Post by badchoice on 2009-09-09
PPA!!!!

Hey, the ppa is up and running with the last gloobus-preview version, including:

-Patched nautilus to launch gloobus-preview with just space key
-Source preview (highligthed text)
-TTF font preview

Instructions here:

[http://gloobus.wordpress.com/2009/09/08/ppa/](http://gloobus.wordpress.com/2009/09/08/ppa/)

And if you like it, consider donate something ;)

---

### Post by DJ_Peng on 2009-09-09
Woo hoo! The only problem I see using that patched version of Nautilus is that some of us are already using a patched version of nautilus to use a [simplified UI]("http://webupd8.blogspot.com/2009/07/install-simplified-nautilus-for-ubuntu.html") from the 100 Papercuts project. (I'm not sure if that's where I found the patched version of Nautilus but it's the best link I could find this am.) I'm concerned that if I use your version of Nautilus I'll lose the benefits from the Papercuts team.

---

### Post by badchoice on 2009-09-09
There is a double patched nautilus :P with the simplified version but thats not the one in the repository, you can compile it by yourself and get the simplified nautilus with the space launching gloobus-preview. 

I attach the patch here:

---

### Post by ammonkey on 2009-09-09
hello,

i just saw the patch ..it's from david siegel work right?
if u know how to apply a patch and compile

u can try the patch attached below, it an unified one, it implements:

- nautilus toolbar simplified, nautilus is too cluttered with all his bar. based on the work of David Siegel from planet gnome
  [http://davidsiegel.org/nautilus-simplified/](http://davidsiegel.org/nautilus-simplified/)
- alt +m to get the menu toolbar (i got to implement a timer on this to autohide)
- mouse extra button forward/back like in firefox
- and the famous press SPACE to launch gloobus-preview :)



how to install, like usual :

[INDENT]download the lastest stable nautilus:
[ftp://ftp.gnome.org/mirror/gnome.org/sources/nautilus/2.26/nautilus-2.26.3.tar.gz](ftp://ftp.gnome.org/mirror/gnome.org/sources/nautilus/2.26/nautilus-2.26.3.tar.gz)

download my patch in the attached file
and extract it

tar xvf newbar_mouse_forward_back_gloobus.patch.tar

tar zxvf archive.tar.gz
cd nautilus-2.26.3
patch -p1 < /path_to_my_patch

u ll see the files been patched here

all u have to do is compile nautilus now:
./configure --prefix=/usr 
make
at this step u can already test nautilus by lauching it via ./src/nautilus without deleting your distribution version
if u like my patch u can do a make install too ;)

by the way before launching the new version compiled of nautilus close nautilus if it s already running
[/INDENT]

The nautilus buttons are defined in an xml file:
/usr/share/nautilus/ui/nautilus-navigation-window-ui.xml
comment or delete the ones u don t want/like the reload button or the stop button they are defined at the end of the file in the section <toolbar name="Toolbar">.

and tell me your feedback.
or u can flood tualatrix on twitter to update the ppa :popcorn:


edit: burned by Jordi :lolflag:

---

### Post by zekopeko on 2009-09-09
Nice to see this project alive and kicking. But it's still has some fundamental bugs. When I open a movie with it on my  netbook it doesn't scale properly on my tiny screen. 
And why do we have to patch nautilus? Doesn't nautilus now support keybindings and couldn't it be done with an extension?
And is there any possibility for a Karmic PPA?

---

### Post by ammonkey on 2009-09-09
> **zekopeko said:**
> Nice to see this project alive and kicking. But it's still has some fundamental bugs. When I open a movie with it on my  netbook it doesn't scale properly on my tiny screen. 
And why do we have to patch nautilus? Doesn't nautilus now support keybindings and couldn't it be done with an extension?
And is there any possibility for a Karmic PPA?

We have to patch nautilus because nautilus don't provide any way to implement keybindings in it they are hardcoded and further more space keys is by default occupied .. by the way, anybodody know what for ? :D

Preview don't support resize or fullscreen at the moment. Jordi is on it. For a karmic version, well i don't have time to provide one at the moment but u got one before the official release of karmic (in october)

---

### Post by shakaran on 2009-09-09
> **badchoice said:**
> There is a double patched nautilus :P with the simplified version but thats not the one in the repository, you can compile it by yourself and get the simplified nautilus with the space launching gloobus-preview. 

I attach the patch here:

More better if you compress with tar.gz ;) zip...is more for windows xD

---

### Post by davim on 2009-09-09
> **ammonkey said:**
> hello,
 the patch attached below, it an unified one, it implements:

- nautilus toolbar simplified, nautilus is too cluttered with all his bar. based on the work of David Siegel from planet gnome
  [http://davidsiegel.org/nautilus-simplified/](http://davidsiegel.org/nautilus-simplified/)
- alt +m to get the menu toolbar (i got to implement a timer on this to autohide)
- mouse extra button forward/back like in firefox
- and the famous press SPACE to launch gloobus-preview :)



Could someone get this into the PPA?? :P

---

### Post by pt123 on 2009-09-09
> **davim said:**
> Could someone get this into the PPA?? :P

Why not create their own PPA. It doesn't even have tabs.

---

### Post by ammonkey on 2009-09-09
> **pt123 said:**
> Why not create their own PPA. It doesn't even have tabs.

It has tabs, the patch just add functionalities, u got the same functionalities as 2.26.3 branch...
(u don't see tabs in the screenshot because he just have one tab opened)

---

### Post by Exodist on 2009-09-09
> **badchoice said:**
> Yes, it's planned to integrate it with nautilus, I'm talking with nautilus developers to see if we can achieve this.

Sweet, keep up the good work.

It would make a great feature for Gnome 3.0

---

### Post by davim on 2009-09-10
> **Exodist said:**
> Sweet, keep up the good work.

It would make a great feature for Gnome 3.0

I agree :)

---

### Post by theZoid on 2009-09-13
I've never heard of Gloobus, but I've installed it from the PPA, and LIKE it !!  Keep up the good work !

---

### Post by davim on 2009-09-13
Hi! In OS X when you select multiple files and press space, you get one preview window with a previous and next buttons to navigate trough the selected files previews, could you add the same functionality to gloobus?

---

### Post by ammonkey on 2009-09-14
> **davim said:**
> Hi! In OS X when you select multiple files and press space, you get one preview window with a previous and next buttons to navigate trough the selected files previews, could you add the same functionality to gloobus?

hello,

We are aware of this functionalities and we're working on it. It s on the wishlist for the next releases.

---

### Post by badchoice on 2009-09-14
Yes, we are now fixing bugs in the current version to make it really stable, and in the other hand, we're working in new features like fullscreen and grid view when multiple files are selected.
Another improvments are adding mor info in audio and vido files such as lenght and bitrate

Anyway, if you have more features that can be added, please, fill them in launchpad as bugs or blueprints, we'll try to add them!!

And of course, if you like the app you can consider supporting us by donating a couple of $/€

Thanks!

---

### Post by C.B.Leslie on 2009-09-15
[https://answers.launchpad.net/gloobus/+question/82773](https://answers.launchpad.net/gloobus/+question/82773)

Any input from anyone?

---

### Post by ammonkey on 2009-09-15
> **C.B.Leslie said:**
> [https://answers.launchpad.net/gloobus/+question/82773](https://answers.launchpad.net/gloobus/+question/82773)

Any input from anyone?

Hi,

Gloobus is far from a finished application. Anyway it already adapts from your gtk theme: icon, scrollbar etc ...
So the only things close to the mac version would be the transparent window with rounded edge and the close and menu buttons.

if u want to change the buttons it's really easy just replace the following files :
- close_button.png 
- gloobus_button.png
(they are located in /usr/share/gloobus/)

if u have some suggestions about the design or the behavior of gloobus we would be happy to read them.

Thanks for your interest.

---

### Post by C.B.Leslie on 2009-09-15
Well one of the first thing's I would like to see is Gloobus be more consistent with ANY users' interface:  

[LIST]
[*]Use the _title bar_ (the rest of the window is fine) from the whatever current theme the user is running. This fixes 3 key things:
[LIST=1]
[*]It doesn't help a new user to be presented 'non-native' controls out of nowhere.
[*]This will also absolve any issues of button alignment for the user who might have the their system configured for "right handed" buttons. As of this moment, it's a left aligned close. I'm sure you can see where I am going with this.
[*]This improves typeface legibility.
[/LIST] 
[*]Let Compiz control the drop shadow. This will add to consistency across the interface, and let the user him/herself adjust it to their own liking.(Right now, the drop shadow is too much for my tastes.)
[*]In the future, add opacity control for the window. As per the fact that one may have typeface legibility issues with the transparency, depending on the theme that is being run.
[/LIST]

It's extra work, but I feel it we will be all much better in the long run.

---

### Post by samuraitor on 2009-09-15
> **C.B.Leslie said:**
> Well one of the first thing's I would like to see is Gloobus be more consistent with ANY users' interface:  

[LIST]
[*]Use the _title bar_ (the rest of the window is fine) from the whatever current theme the user is running. This fixes 3 key things:
[LIST=1]
[*]It doesn't help a new user to be presented 'non-native' controls out of nowhere.
[*]This will also absolve any issues of button alignment for the user who might have the their system configured for "right handed" buttons. As of this moment, it's a left aligned close. I'm sure you can see where I am going with this.
[*]This improves typeface legibility.
[/LIST] 
[*]Let Compiz control the drop shadow. This will add to consistency across the interface, and let the user him/herself adjust it to their own liking.(Right now, the drop shadow is too much for my tastes.)
[*]In the future, add opacity control for the window. As per the fact that one may have typeface legibility issues with the transparency, depending on the theme that is being run.
[/LIST]

It's extra work, but I feel it we will be all much better in the long run.

How to I go about installing covergloobus 1.4.tar file?

---

### Post by C.B.Leslie on 2009-09-15
[https://answers.edge.launchpad.net/gloobus/+question/72720](https://answers.edge.launchpad.net/gloobus/+question/72720)

Documentation on compiling.

---

### Post by Sashin on 2009-09-16
I agree with CB, it would be better if it was more consistent with the desktop. Like most people have the close button at the right hand side.

Also I think it would be better behaviour if clicking outside of the quicklook window closed it.

---

### Post by ammonkey on 2009-09-16
> **Sashin said:**
> Also I think it would be better behaviour if clicking outside of the quicklook window closed it.

We can't manage events outside our window, it's the window manager job.

---

### Post by Sashin on 2009-09-16
What if you made the window fullscreen but only a small part of it visible, so it looks like a small window and clicking on any other part would close it?

---

### Post by badchoice on 2009-09-16
> **samuraitor said:**
> How to I go about installing covergloobus 1.4.tar file?


Covergloobus doesn't need compile, is written in pyhton and you can launch it just double clicking in covergloobus.py and selectin execute.

Anyway, you first want to execute covergloobus-config.py to configure your player and theme

Hope it works for you!

---

### Post by DJ_Peng on 2009-09-16
This may be a dumb (or at least already answered) question, but what's the best way to add GlolbusCover to a comp that has Gloobus installed from the PPA? The CoverFlow is the feature I want to use most from Gloobus.

I was checking out my Google News this am and found some nice ink for Gloobus from Nillabyte: [Gloobus Brings QuickLook And CoverFlow To Ubuntu]("http://www.nillabyte.com/blog.php?b=239"). I wanted to post it here so others on this thread can see it.

---

### Post by badchoice on 2009-09-16
> **DJ_Peng said:**
> This may be a dumb (or at least already answered) question, but what's the best way to add GlolbusCover to a comp that has Gloobus installed from the PPA? The CoverFlow is the feature I want to use most from Gloobus.

I was checking out my Google News this am and found some nice ink for Gloobus from Nillabyte: [Gloobus Brings QuickLook And CoverFlow To Ubuntu]("http://www.nillabyte.com/blog.php?b=239"). I wanted to post it here so others on this thread can see it.


gloobus-coverflow isn't in the repo yet, anyway, you can install it from the deb at my deviantart page:

[http://jordihp.deviantart.com](http://jordihp.deviantart.com) 

There are two debs, one for a old gloobus-preview and one for the gloobus-coverflow, just install it and type gloobus on a terminal in the folder you want to see.
You can also add a menu entry with nautilus actions

---

### Post by spg76 on 2009-09-16
I made a couple of mockups based on some things that I've read here.
I don't know if they are any good or if it's even possible to make it.

---

### Post by DJ_Peng on 2009-09-16
> **badchoice said:**
> gloobus-coverflow isn't in the repo yet, anyway, you can install it from the deb at my deviantart page:

[http://jordihp.deviantart.com](http://jordihp.deviantart.com) 

There are two debs, one for a old gloobus-preview and one for the gloobus-coverflow, just install it and type gloobus on a terminal in the folder you want to see.
You can also add a menu entry with nautilus actions
Now I'm totally lost. I grabbed CoverGloobus_1_4_by_JordiHP.gz, extracted the .tar from it, extracted that and moved the resulting CoverGloobus to my /home folder. But when I ran python CoverGloobus.py, even in the /home/CoverGloobus directory, I got the player preview window but nothing else.

Something tells me I should just be patient and wait for GloobusCover to reach a PPA or something because I must be grabbing the wrong thing plus be missing dependencies. ](*,)

---

### Post by C.B.Leslie on 2009-09-16
> **ammonkey said:**
> We can't manage events outside our window, it's the window manager job.

Can you utilize events from the windows status. id est: Tell the window to close when it's lost focus?

---

### Post by C.B.Leslie on 2009-09-16
> **spg76 said:**
> I made a couple of mockups based on some things that I've read here.
I don't know if they are any good or if it's even possible to make it.
These look great. I should really post the mock ups I made.

---

### Post by C.B.Leslie on 2009-09-16
My mock-ups. And what envision is best for the users.

---

### Post by kopydis on 2009-09-17
> **C.B.Leslie said:**
> Well one of the first thing's I would like to see is Gloobus be more consistent with ANY users' interface:  

[LIST]
[*]Use the _title bar_ (the rest of the window is fine) from the whatever current theme the user is running. This fixes 3 key things:
[LIST=1]
[*]It doesn't help a new user to be presented 'non-native' controls out of nowhere.
[*]This will also absolve any issues of button alignment for the user who might have the their system configured for "right handed" buttons. As of this moment, it's a left aligned close. I'm sure you can see where I am going with this.
[*]This improves typeface legibility.
[/LIST]
 
[*]Let Compiz control the drop shadow. This will add to consistency across the interface, and let the user him/herself adjust it to their own liking.(Right now, the drop shadow is too much for my tastes.)
[*]In the future, add opacity control for the window. As per the fact that one may have typeface legibility issues with the transparency, depending on the theme that is being run.
[/LIST]

It's extra work, but I feel it we will be all much better in the long run.

This makes sense

---

### Post by yuli_capone on 2009-09-17
I installed Gloobus and i want to uninstall and install view split for nautilus.How do i remove completly Gloobus?Becouse dual panel for nautilus won't install with Gloobus installed

---

### Post by ammonkey on 2009-09-19
> **spg76 said:**
> I made a couple of mockups based on some things that I've read here.
I don't know if they are any good or if it's even possible to make it.

Nice mockups i like them. An application can look good even without tranparencie.

---

### Post by coolen on 2009-09-19
A window can detect when it loses focus, can it not?

I'm not a developer, so I don't actually know. Just a thought.

---

### Post by ammonkey on 2009-09-19
> **coolen said:**
> A window can detect when it loses focus, can it not?

I'm not a developer, so I don't actually know. Just a thought.

yes sure but well i don't want to relaunch a preview every-time i do another task. By the way u can close the preview window with simple shortcuts too (escape or space keyboard button), so don't tell me close a window is so painful ;). What we could do is to make sure gloobus-preview has only one window opened to avoid a cluttered desktop, but it s just an idea.

---

### Post by coolen on 2009-09-19
I know you can use shortcut keys, and I do.

It's not painful, it's just what you'd expect from a preview application: you do something else, and the preview stops.

Launching Gloobus is also not painful anymore.

---

### Post by Praxicoide on 2009-09-19
Wonderful app. I could get used to this.:)

---

### Post by Sashin on 2009-09-19
> **ammonkey said:**
> yes sure but well i don't want to relaunch a preview every-time i do another task. By the way u can close the preview window with simple shortcuts too (escape or space keyboard button), so don't tell me close a window is so painful ;). What we could do is to make sure gloobus-preview has only one window opened to avoid a cluttered desktop, but it s just an idea.

Do this, 
it would solve the problem.

---

### Post by azraiyan on 2009-09-25
Hi, I'm excited about gloobus. I have been trying all day to get gloobus to work with Nautilus 2.28 in Karmic Alpha 6. I have followed the steps and cannot get it to work using the Space key. Anyone here using Karmic Alpha 6 has the same problem?

---

### Post by badchoice on 2009-09-25
I haven't tested it with karmik.. is gloobus-preview working?

IS just the nautilus patch that doesn't work? Cause the patch is for nautilus 2.26, we haven't released it for 2.28.. so sure this is the problem.

I hope we can update it in time to get it working in the karmik release date!

---

### Post by davim on 2009-09-25
> **spg76 said:**
> I made a couple of mockups based on some things that I've read here.
I don't know if they are any good or if it's even possible to make it.

That looks great :)

---

### Post by azraiyan on 2009-09-25
Nope, the gloobus-preview is not working. I haven't try the patch but will try it for the last time.

---

### Post by Prominence on 2009-09-28
Did the latest release do something to nautilus? my nautilus is all messed up...anyway to fix it?

---

### Post by jolsz on 2009-09-28
Yes it did!!!
-> the menubar is gone
-> location bar toggle button is gone
-> view switch drop-down is gone

I was so irritated that I had to remove the patched version of nautilus and install the original one.

I would expect that the only change in nautilus is the "space key" patch and nothing more.

---

### Post by ammonkey on 2009-09-28
> **jolsz said:**
> Yes it did!!!
-> the menubar is gone
the menubar is auto hidden alt+m to show/hide the menu bar

> **jolsz said:**
> 
-> location bar toggle button is gone
-> view switch drop-down is gone
They're still here u can activate them with normal nautilus shortcut:
   - ctrl+l : location bar writable/clickable
   - ctrl+f : to find a file
   - ctrl+1 ..2/3: differents view icons/list/etc

The actual nautilus patched version available in Tualatrix ppa is a simplified nautilus from the spirit of 100 paper cuts. All i write here, we discussed it in a question in launchpad, pleas read the answers and tell me if they work for you:

[https://answers.launchpad.net/gloobus/+question/84080](https://answers.launchpad.net/gloobus/+question/84080)


> **jolsz said:**
> 
I was so irritated that I had to remove the patched version of nautilus and install the original one.

I would expect that the only change in nautilus is the "space key" patch and nothing more.

I understand now why gnome community developpers are so conservative.

---

### Post by l-x-l on 2009-09-28
I am absolutely confused on how to use coverflow. Am I supposed to use nautilus actions? Is it Ctrl+C & Ctrl+Space? Right-click?

Can someone give me step by step instructions? Thx.

---

### Post by coolen on 2009-09-28
Just updated, killed Nautilus, then started it again to see the new layout.

One query: is everyone else having Nautilus handle the desktop properly? My icons have disappeared, and the context menu will not show up. Is this just me? Is a reboot in order?

---

### Post by ammonkey on 2009-09-28
> **coolen said:**
> Just updated, killed Nautilus, then started it again to see the new layout.

One query: is everyone else having Nautilus handle the desktop properly? My icons have disappeared, and the context menu will not show up. Is this just me? Is a reboot in order?

if you are in a pure gnome session perhaps it's better to reload the gnome session as nautilus control the icons on your desktop too.
The ppa of the patched nautilus has been updated yesterday we are waiting for your feedback!

---

### Post by ammonkey on 2009-09-28
> **l-x-l said:**
> I am absolutely confused on how to use coverflow. Am I supposed to use nautilus actions? Is it Ctrl+C & Ctrl+Space? Right-click?

Can someone give me step by step instructions? Thx.

coverflow is for the moment experimental that's why it's not available in the ppa. Anyway if u want to try it u can download it and compile it from our bzr branch.
U can use it from the console with the command: 
gloobus path_to_directory_u_want

i am sure u can link this with a nautilus action too.

---

### Post by coolen on 2009-09-29
You're right. Logged out and back in, and my convoluted desktop is back :D

As for the new layout, it was a bit of a surprise. Users of Jaunty usually have to explicitly opt in to the new layout. I'm getting used to it...having no menubar by default is certainly odd.

---

### Post by jolsz on 2009-09-29
> **ammonkey said:**
> 
The actual nautilus patched version available in Tualatrix ppa is a simplified nautilus from the spirit of 100 paper cuts. All i write here, we discussed it in a question in launchpad, pleas read the answers and tell me if they work for you:
[https://answers.launchpad.net/gloobus/+question/84080](https://answers.launchpad.net/gloobus/+question/84080)
I understand now why gnome community developpers are so conservative.

Thanks for your tips regarding keyboard short cuts. Anyway in my opinion it is a matter of usability. Usually the key short cuts are only an add on to some GUI options. For me the situation were the shortcuts are present but I cannot do something using regular UI is not normal and breaks some common rules in area of usability. 
I'm not conservative but I like my desktop to be consistent.

---

### Post by badchoice on 2009-09-29
Hey!
I posted a poll in my blog to see what people thinks. So you can express yourself and we'll do the changes respection the results ;)

[http://gloobus.wordpress.com/2009/09/29/nautilus-or-simplified-nautilus/](http://gloobus.wordpress.com/2009/09/29/nautilus-or-simplified-nautilus/)

Thanks a lot for you suggestions, Its allways good to know what people thinks about.

---

### Post by azraiyan on 2009-09-29
> **jolsz said:**
> 
I was so irritated that I had to remove the patched version of nautilus and install the original one.


how did you remove the patched Nautilus, been trying without luck with the patched version but cant make gloobus to work.

---

### Post by ammonkey on 2009-09-29
> **azraiyan said:**
> how did you remove the patched Nautilus, been trying without luck with the patched version but cant make gloobus to work.

already answered here:
[http://ubuntuforums.org/showpost.php?p=8020042&postcount=5](http://ubuntuforums.org/showpost.php?p=8020042&postcount=5)

---

### Post by azraiyan on 2009-09-29
> **ammonkey said:**
> already answered here:
[http://ubuntuforums.org/showpost.php?p=8020042&postcount=5](http://ubuntuforums.org/showpost.php?p=8020042&postcount=5)

thanks, hope it works. But before I went to this thread again, I seemed to have gloobus worked when I open a file using a command which I use gloobus-preview. How do I bind the key to enable gloobus using space key.

---

### Post by ammonkey on 2009-09-29
> **azraiyan said:**
> thanks, hope it works. But before I went to this thread again, I seemed to have gloobus worked when I open a file using a command which I use gloobus-preview. How do I bind the key to enable gloobus using space key.

it's just not possible on an original (non patched) nautilus to interact with only the space bar it's a hardcoded shortcut from nautilus which execute the default action. That's why we distribute a patched version.

U can set gloobus(coverflow) in nautilus action, u can't bind it to any shortcut key because nautilus-action and any extensions can't have shortcuts.

With preview u can launch it with shortcuts like ctrl+c AND ctrl+space because it's a trick. In fact when u do a ctrl+c u create an entry in the clipboard and preview know how to read in the clipboard.

I hope i answered your question.

---

### Post by azraiyan on 2009-09-29
Finally I could bind the key using gconf-editor and now I'm at lost with coverflow. I have already added the schemas, preview and folder coverflow via nautilus action. The preview works but the folder coverflow does not. 

From the gloobus site, it mention you need to set the path "gloobus path to directory". How can I set this? Is is pointing to /usr/bin/gloobus-preview or somewhere else?

---

### Post by ammonkey on 2009-09-29
> **azraiyan said:**
> Finally I could bind the key using gconf-editor and now I'm at lost with coverflow. I have already added the schemas, preview and folder coverflow via nautilus action. The preview works but the folder coverflow does not. 

From the gloobus site, it mention you need to set the path "gloobus path to directory". How can I set this? Is is pointing to /usr/bin/gloobus-preview or somewhere else?

"gloobus path_to_directory" is a command you launch from a terminal.

---

### Post by ammonkey on 2009-09-29
Hi all, i come with some news about our patched nautilus,
A fix as been committed, so it's a question of hours before the next ppa update. For all who wonder where their menubar is, u'll find all the answers here:
[https://answers.launchpad.net/gloobus/+question/84080](https://answers.launchpad.net/gloobus/+question/84080)

---

### Post by nanolightonair on 2009-09-30
Hello all!
Do you think it could be possible to include this patch in the patched version of nautilus that gloobus use:
[http://ayozone.org/wp-content/uploads/2007/11/098_no_label_underline.patch](http://ayozone.org/wp-content/uploads/2007/11/098_no_label_underline.patch)
It comes from the project global menu and the goal of the patch is to delete the underline characters in the menu.
It's a very simple patch but I don't know how to do to apply it in addition to gloobus which has already a patch for nautilus.
Thanks for the great job!
nanolight

---

### Post by azraiyan on 2009-09-30
I still can't get Cover Flow to work. Is there a difference, Gloobus and Gloobus-Preview? Or am I missing installing Gloobus? 

I just want to have Cover Flow works. I right click and select Folder Cover Flow, nothing happened. Is it specific folder to make this work or right click on a file like a picture, still the Cover Flow wont come out.

---

### Post by spg76 on 2009-10-31
I just installed Karmic and I can't launch the preview with the space key anymore.
Apparently the patch doesn't work with Nautilus 2.28.
Anyone knows how to get it to work again? Is there a new patch somewhere?
Thanks.

---

### Post by ammonkey on 2009-10-31
hello,

Have u activated Tualatrix ppa or via ubuntu tweaks?
check your source list.

---

### Post by spg76 on 2009-11-01
> **ammonkey said:**
> hello,

Have u activated Tualatrix ppa or via ubuntu tweaks?
check your source list.

I'd only installed gloobus-preview.
Just add the PPA, installed nautilus and now it's working again :)
Thank you very much.

---

### Post by faical117 on 2009-11-06
Looks great :-)

---

### Post by sexyclient2 on 2009-11-08
Anyone manage to get this working with parcellite clipboard manager?  I have to disable parcellite to get previews.  Also, is there a way to add an entry in nautilus for one-click file previews?

---

### Post by badchoice on 2009-11-09
Why don't you install patched nautilus, then you can launch gloobus just pressing space :D

---

### Post by jdorenbush on 2009-11-10
It seems cool. I like it most for the text/doc integration, very handy to preview text in a document on the fly.

A few problems though...

1. I don't really understand how the cover art works. When I click on an MP3 all I get is the song playing and a default MP3 icon, no cover art is displayed.

2. I can't seem to get .doc files that were created on a Mac too open in preview. Not sure if Windows files have the same problem.

3. There seems to be a bug with the PDF preview. [Bug report here]("https://bugs.launchpad.net/gloobus/+bug/475517").

4. Excel files seem to have a flickering problem as well. They also open very slowly and have serious display issues. Everything is scattered and improperly formatted.

---

### Post by badchoice on 2009-11-11
Hey jdorenbush

I answer your questions:

1. It first looks for the cover in the mp3 file (using libtag) if not found, then searches for cover.jpg and then for cover.png in the folder where the file is

2. Can you send me one of those files? can you open them in OO 

3. Answered in the bug report, but maybe is a graphics card bug, wich one do you have?

---

### Post by the8thstar on 2009-11-11
the coverflow doesn't work for me:

> the8thstar@the8thstar-laptop:~$ gloobus-preview
Getting file from clipboard
Filename: 
ClipBoard: /home/the8thstar/Downloads/Monaco.ttf
LOADING PLUGINS:
	 /usr/lib/gloobus/audio.so
	 /usr/lib/gloobus/comic.so
	 /usr/lib/gloobus/folder.so
	 /usr/lib/gloobus/icns.so
	 /usr/lib/gloobus/openoffice.so
	 /usr/lib/gloobus/pdf.so
	 /usr/lib/gloobus/pixbuf.so
	 /usr/lib/gloobus/text.so
	 /usr/lib/gloobus/ttf.so
	 /usr/lib/gloobus/video.so
CONTENT FOLDER: /home/the8thstar/Downloads

(gloobus-preview:8438): GLib-GIO-CRITICAL **: g_file_info_get_attribute_string: assertion `G_IS_FILE_INFO (info)' failed
Segmentation fault

Any ideas why I get this?

---

### Post by hcorey on 2009-11-11
I know this is off topic, but in anyone's opinion does gloobus-coverflow violate Apple's patent 7,581,186, which was recently awarded?

---

### Post by pt123 on 2009-11-11
screw apple and their retarded patents, they are only valid in corrupt countries

---

### Post by jdorenbush on 2009-11-11
> **badchoice said:**
> Hey jdorenbush

I answer your questions:

1. It first looks for the cover in the mp3 file (using libtag) if not found, then searches for cover.jpg and then for cover.png in the folder where the file is

2. Can you send me one of those files? can you open them in OO 

3. Answered in the bug report, but maybe is a graphics card bug, wich one do you have?

1. Can I set it up to check for folder.jpg/png?

2. Yes, I can open in OpenOffice.

3. ATi Radeon X1950 Pro

But now for some reasom Gloobus isn't working at all.

---

### Post by booksnmore4you on 2009-11-14
Sheesh.  54 pages!!!  Can someone tell me briefly how to get this running on Ubuntu 9.10?  I've installed from PPA but am stuck at that point.

---

### Post by booksnmore4you on 2009-11-14
Never mind, I found out how at [https://answers.launchpad.net/gloobus/+question/83626](https://answers.launchpad.net/gloobus/+question/83626) and have it running.

However, I fail to see any advantage to this program.  Opening files in "preview" is really no faster than opening them with the default program!

---

### Post by badchoice on 2009-11-15
Well, try opening a video or pdf, or a openoffice file, or a xcf or psd file.

Anyway If you prefer opening them in the default app, you're free to use of course :D

---

### Post by kimda on 2009-11-19
I really like this program. The only problem I have with it right now is that I cannot use it with samba shares in Nautilus.

---

### Post by goldsniper on 2009-11-22
First of all, this is very good for Ubuntu. Congrats and thanks!

Now, my question:

 Is Cover flow, right now worked with Karmic?; How can I activate it so that it works with Gloobus preview?

---

### Post by Sutur on 2009-11-22
Ctrl+Space doesn't initialise coverflow, it just exits.

```
surt@muspell:~$ gloobus-preview img/02033_sunriseinareeiro_1920x1080.jpg 
CONTENT FOLDER: ./img
Actual file number: 0
Mime Type: image/jpeg
Creating Plugin Class: image 
IMAGE (iPhoto)
Creating iPhoto...
PLUGIN: Loading photo (./img/02033_sunriseinareeiro_1920x1080.jpg)
[INFO] Key Pressed Control_L (65507)
[INFO] Key Pressed space (32)
Destory Plugin:
Destroying iPhoto...
surt@muspell:~$ 
```

It seems as if the space bar is used to open & close the application, and also from the limited information I could find, to initialise coverflow. Could it be conflicting?

---

### Post by Cz-David on 2009-11-22
Feature idea... what about renaming previewed files by clicking on the top of the gloobus?

---

### Post by ammonkey on 2009-11-27
Hi,

coverflow is not a plugin, it's a different program  (an experimentation) it's not available in any ppa. If u want to try it u have to compile it, see gloobus.net for more detail.

---

### Post by guv999 on 2009-11-28
Hi - really sorry to ask this, I must be missing something obvious but I cannnot get this workng at all,  I installed the repositry and app via ubuntu tweak, when i click on the app in the menu nothing happens and when i hit space over a document it launches in the program itself - thanks for any hep, this looks good.

---

### Post by badchoice on 2009-11-29
So if when you click space the app launches, what is the problem?

---

### Post by guv999 on 2009-11-29
Hi Sorry - what I mean...say the document i am wanting to preview is an open office doc, it will actually open up in open office rather than preview mode - thanks

---

### Post by nanolightonair on 2009-12-10
Hello, do you have news about a package into the ppa that would include the nautilus-simplified and the nautilus-gloobus changes as it was the case for jaunty?
Cause I can't stop using nautilus-simplified and I can't install gloobus as it will erase nautilus-simplified!
Thanks for everything!
nanolight

---

### Post by spg76 on 2009-12-12
Checkout the Gloobus mockups made by DanRabbit (elementary and Humanity icons, Docky 2 artwork).
[http://danrabbit.deviantart.com/art/Gloobus-Music-146487346](http://danrabbit.deviantart.com/art/Gloobus-Music-146487346)
[http://danrabbit.deviantart.com/art/Gloobus-Folders-146491616](http://danrabbit.deviantart.com/art/Gloobus-Folders-146491616)

---

### Post by @B6Mwu8fN9M on 2009-12-25
A comment for your installation instructions at: [http://gloobus.net/installation/](http://gloobus.net/installation/)

At the offline instructions:
Shouldn't the line: 
```
./configure --prefix/usr/
```
be
```
./configure --prefix=/usr/
```

The instructions with the online access have the "=".

---

### Post by Indigo340 on 2009-12-26
Well I have tried everything and still can't get it to work.
The only thing that appears to be wrong is I don't have a key, it says PUB KEY NOT AVAILABLE, NO_PUBKEY 50DC901D5291C76F

I'm not sure if this is the root of the problem but I have everything installed (Gloobus-preview, Covergloobus, Clutter) and tried to forllow _all_ the instructions carefully but keep getting problems in Terminal when using "sudo ./configure" so can't go any further. 
I wish it was simpler to install !
I am a noobie with Ubuntu so I don't know all the terminology and it's quite possible that I have overlooked something but I have exhausted all the references on the net and still not getting it right. 
Please help !

---

### Post by zekopeko on 2009-12-26
Ok we now have a wiki with install instructions:

[http://gloobus.net/wiki/index.php/Install#Installing_Gloobus_Preview_from_the_PPA](http://gloobus.net/wiki/index.php/Install#Installing_Gloobus_Preview_from_the_PPA)

If you want the latest and greatest you will need to install it from source (recommended over the PPA).

Also don't use sudo at all until this part from the guide:

sudo make install

Doing sudo ./configure is a no-no.

You can also come to the #gloobus channel on irc.freenode.net

---

### Post by zekopeko on 2009-12-26
Duplicate post

---

### Post by isaacj87 on 2009-12-26
> **zekopeko said:**
> Ok we now have a wiki with install instructions:

[http://gloobus.net/wiki/index.php/Install#Installing_Gloobus_Preview_from_the_PPA](http://gloobus.net/wiki/index.php/Install#Installing_Gloobus_Preview_from_the_PPA)

If you want the latest and greatest you will need to install it from source (recommended over the PPA).

Also don't use sudo at all until this part from the guide:

sudo make install

Doing sudo ./configure is a no-no.

You can also come to the #gloobus channel on irc.freenode.net

What's up with the wiki instructions? The build-deps are misspelled and stuff. For example, "build-essentials" shouldn't it be "build-essential?"

This is what I installed: 
```
sudo apt-get install libgtk2.0-dev libgvfscommon-dev libgstreamer-plugins-base0.10-dev libcairomm-1.0-dev libtag1-dev libpoppler-glib-dev libgnomeui-dev unoconv libgtksourceview2.0-dev build-essential automake libtool bzr libbz2-dev

```

---

### Post by zekopeko on 2009-12-26
> **isaacj87 said:**
> What's up with the wiki instructions? The build-deps are misspelled and stuff. For example, "build-essentials" shouldn't it be "build-essential?"

This is what I installed: 
```
sudo apt-get install libgtk2.0-dev libgvfscommon-dev libgstreamer-plugins-base0.10-dev libcairomm-1.0-dev libtag1-dev libpoppler-glib-dev libgnomeui-dev unoconv libgtksourceview2.0-dev build-essential automake libtool bzr libbz2-dev

```

I don't know since I didn't add that part. Anyway its fixed know. Thanks for informing me.

---

### Post by isaacj87 on 2009-12-26
> **zekopeko said:**
> I don't know since I didn't add that part. Anyway its fixed know. Thanks for informing me.

Good to go :)

You might want to check them though because that's just what worked for me (on Karmic). I do a good bit of compiling so I might of missed a dep because I already had it installed. :)

---

### Post by Indigo340 on 2009-12-27
OK thanks guys I have it working now although I don't seem to have all the features.
I spent over 6 hours working on it yesterday and just kept going round in circles getting nowhere !!!

I used Synaptic to 'uninstall' the failed attempts and deleted the folders then followed the WIKI instructions and used your code and it was very easy, I wish I came here first !

Now I'll look at that stupid video again (he does not show how to install it, just shows what it does) to see how to set it up better, unless you have a better suggestion.

I am only able to preview contents of folder and preview pics, cannot find that 'carousel' view.

---

### Post by Indigo340 on 2009-12-27
OK it looks like I need to download Gloobus-Coverview ! Where do I find that ?

I tried this site [http://sunnybiologia.blogspot.com/2009/11/coverflow-previews-in-nautilusubuntu.html](http://sunnybiologia.blogspot.com/2009/11/coverflow-previews-in-nautilusubuntu.html) but as I'm a noob it really does not make much sense to me. When I followed the instructions and copied and pasted the code into Terminal, I can only get so far before Terminal stops responding, (how do I describe it ?) I input some lines and it runs through a sequence of actions up to a point then stops, after that I can only write commands but it fails to act, and the erm 'command prompt' is missing just a blinking cursor (does that make sense ?) normally it says something like 'ian@ian-laptop:~$' and that is where you input code but it does not show.

It's all very confusing for a noob! This page [http://sunnybiologia.blogspot.com/2009/11/coverflow-previews-in-nautilusubuntu.html](http://sunnybiologia.blogspot.com/2009/11/coverflow-previews-in-nautilusubuntu.html) assumes that you have a lot of experience which I don't have. 
Please can someone give me a walkthrough ?

---

### Post by teolemon on 2009-12-27
Gloobus Coverview >> It that CoverGloobus or GloobusFlow you're talking about ?

In other news, you can translate GloobusPreview at : [https://translations.edge.launchpad.net/gloobus-preview](https://translations.edge.launchpad.net/gloobus-preview)

We now also have a Facebook fanpage at [http://www.facebook.com/pages/Gloobus/213484369607](http://www.facebook.com/pages/Gloobus/213484369607)

---

### Post by teolemon on 2009-12-27
GloobusFlow is not ready for use by the way.

---

### Post by tibike on 2009-12-27
Hello!
I installed gloobus-preview from source following the instructions from this website: [http://gloobus.net/wiki/index.php/Install#Installing_Gloobus_Preview_from_the_PPA](http://gloobus.net/wiki/index.php/Install#Installing_Gloobus_Preview_from_the_PPA)

1. Preview is working good using 'space'. But I don't know how to enter cover-flow. Should I press some key's, write stuff in terminal or what??? 
(super-space is for gnome-do... just in case...)

2. Office documents like PDF, ODT or ODS don't open, just hang with max. processor use. 
I tried to call from terminal and I got this message:

[WARNING] Config file couldn't be readed
[INFO] Mime Type: application/vnd.oasis.opendocument.text
Creating iOO...
 or 

[WARNING] Config file couldn't be readed
[INFO] Mime Type: application/pdf
Creating iPdf...

---

### Post by zekopeko on 2009-12-27
> **tibike said:**
> Hello!
I installed gloobus-preview from source following the instructions from this website: [http://gloobus.net/wiki/index.php/Install#Installing_Gloobus_Preview_from_the_PPA](http://gloobus.net/wiki/index.php/Install#Installing_Gloobus_Preview_from_the_PPA)

1. Preview is working good using 'space'. But I don't know how to enter cover-flow. Should I press some key's, write stuff in terminal or what??? 
(super-space is for gnome-do... just in case...)

GloobusFlow is waiting on the work Badchoice and Kitkat are doing on Nautilus integration. So it's really not ready for use. I don't know what is with the PPA since another person is updating it. But AFAIK if you do have gloobus-coverflow installed the only way to start it is from the terminal by giving it the path of the folder you want to look.

> 2. Office documents like PDF, ODT or ODS don't open, just hang with max. processor use. 
I tried to call from terminal and I got this message:

[WARNING] Config file couldn't be readed
[INFO] Mime Type: application/vnd.oasis.opendocument.text
Creating iOO...
 or 

[WARNING] Config file couldn't be readed
[INFO] Mime Type: application/pdf
Creating iPdf...

This is a bug and you can report it here:

[https://bugs.launchpad.net/gloobus-preview](https://bugs.launchpad.net/gloobus-preview)

---

### Post by Indigo340 on 2009-12-30
This is driving me nuts !

It seems that Gloobus-Coverflow is bundled with Gloobus-Preview, is that correct ?

No matter what I do, I can't find it, "extract it, compile it" or install it ! 

It seems I need to download Clutter-gtk/0.10 but that gives me headaches too ! All I can find is the 'Index of sources' [http://www.clutter-project.org/sources/clutter-gtk/0.10/](http://www.clutter-project.org/sources/clutter-gtk/0.10/) and I don't know what I need to do to download from there. This probably sounds really stupid to some of you but all I can do is open the page, copying a page seems to be wrong, surely I need the file, what do I need to do in order to download it ?

I really want to have 'The Coverflow effect' but I'm getting nowhere !

---

### Post by ammonkey on 2009-12-30
apt-cache search clutter-gtk

was it really hard to find the package?
so it should be,

apt-get install libclutter-gtk-0.10-0 libclutter-gtk-0.10-dev

---

### Post by Indigo340 on 2010-01-02
Nope I'm still not getting it, I know it's user error, probably just don't understand enough about Ubuntu yet. I'll go over the start up docs again and try to figure it out.

---

### Post by ammonkey on 2010-01-02
> **Indigo340 said:**
> Nope I'm still not getting it, I know it's user error, probably just don't understand enough about Ubuntu yet. I'll go over the start up docs again and try to figure it out.

what's your next error? u can find help on irc too, on freenode channel gloobus.

---

### Post by Indigo340 on 2010-01-02
Thanks ammonkey, it just isn't showing up in any of the menus or when I try to initialise it with Terminal, although Synaptic says it's installed. I can see Preview and CoverGloobus I can't get the Covershow 'carousel' view which is the main reason I downloaded it

---

### Post by ammonkey on 2010-01-02
> **Indigo340 said:**
> Thanks ammonkey, it just isn't showing up in any of the menus or when I try to initialise it with Terminal, although Synaptic says it's installed. I can see Preview and CoverGloobus I can't get the Covershow 'carousel' view which is the main reason I downloaded it

guide to compile gloobus coverflow:
[https://answers.launchpad.net/gloobus/+question/95300](https://answers.launchpad.net/gloobus/+question/95300)

---

### Post by Indigo340 on 2010-01-03
OK thanks again, I didn't realise it was still being developed, that explains everything. I will wait to see how it develops and follow it's progress then try to download it and install it later, Cheers :-)

---

### Post by zekopeko on 2010-01-03
> **Indigo340 said:**
> OK thanks again, I didn't realise it was still being developed, that explains everything. I will wait to see how it develops and follow it's progress then try to download it and install it later, Cheers :-)

Gloobus-Flow is going to remain a gimmick until we have proper integration with Nautilus. 

ammonkey and BadChoice are working on it but it's still not release ready.

---

### Post by Tarlak on 2010-01-06
Hi, 

I install gloobus preview with the help of the [wiki](http://gloobus.net/wiki/index.php/Install#Installing_Gloobus_Preview_from_the_PPA), so the compilation goes weel, but gloobus preview doesn't work.

When i hit the space bar the preview don't come. But if on a file i use CTRL + C and then goes in Application -> Accessories -> Gloobus Preview, the preview appear.

I'm on Karmic with gnome.

Is there something to do after the compilation on gnome to work ?

---

### Post by ammonkey on 2010-01-06
> **Tarlak said:**
> Hi, 

I install gloobus preview with the help of the [wiki](http://gloobus.net/wiki/index.php/Install#Installing_Gloobus_Preview_from_the_PPA), so the compilation goes weel, but gloobus preview doesn't work.

When i hit the space bar the preview don't come. But if on a file i use CTRL + C and then goes in Application -> Accessories -> Gloobus Preview, the preview appear.

I'm on Karmic with gnome.

Is there something to do after the compilation on gnome to work ?

if u installed a patched version of nautilus, u have to restart nautilus:
nautilus -q
or delog from X and relog

---

### Post by Tarlak on 2010-01-07
I'd like to but how to patch nautilus ? because with the compilation i don't see how to do this

---

### Post by ThePantryMaster on 2010-01-08
Oh look it didn't work...  I got nothing but errors and Nautilus wouldn't show at all.  I followed the install instructions to the letter.

---

### Post by kamitsukai on 2010-01-08
Gloobus Preview isnt working for me...

I've installed the PPA in karmic and installed the patched nautilus and have gloobus installed

there's no menu option for it and pressing the space on a selected item doesn't work and also launching gloobus from the commandline says this:

```
carl@carl-laptop:~$ gloobus-preview
gloobus-preview: command not found

```

---

### Post by saturnblackhole on 2010-01-09
same here i tired i installed it from the ppa and nothing and then i uninstalled it and reinstalled it using the bzr and i couldn't get it to install.

---

### Post by ammonkey on 2010-01-09
> **saturnblackhole said:**
> same here i tired i installed it from the ppa and nothing and then i uninstalled it and reinstalled it using the bzr and i couldn't get it to install.

any output errors from the bzr intall?

---

### Post by ThePantryMaster on 2010-01-10
Ok, I had a really nice working Karmic before I tried installing this, can someone please tell me how to unpatch Nautilus please?
It doesn't work anymore, to get it to work I have to go into the terminal every time and type Nautilus &, and as soon as I close the terminal it goes away.  Very annoying.  I keep getting this error when trying to quit Nautilus:

> 
christoph@christoph-laptop:~$ nautilus -q
Gtk-Message: Failed to load module "gnomenu-panel": libgnomenu-panel.so: cannot open shared object file: No such file or directory

(nautilus:10365): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Then when I start it:

> christoph@christoph-laptop:~$ nautilus &
[1] 10753
christoph@christoph-laptop:~$ Gtk-Message: Failed to load module "gnomenu-panel": libgnomenu-panel.so: cannot open shared object file: No such file or directory

(nautilus:10753): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:10753): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:10753): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:10753): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.I just want the old Nautilus back, can someone help?

edit: fixed!  I forced version in synaptic to an older one.  Just have to remove the software source now.

---

### Post by saturnblackhole on 2010-01-11
> **ammonkey said:**
> any output errors from the bzr intall?

yeah but i figured it out and got it installed. if your the person who made the program thank you it works great and is really cool.

---

### Post by k64 on 2010-01-11
It would be a real shame, however, for Apple to kill this, just as Microsoft tried to kill other FOSS projects.

edit: and failed.

---

### Post by zekopeko on 2010-01-14
> **k64 said:**
> It would be a real shame, however, for Apple to kill this, just as Microsoft tried to kill other FOSS projects.

edit: and failed.

Please go and have paranoid ramblings in some other thread. Thank you.

---

### Post by skooter1121 on 2010-03-03
Just installed it.

Have a few questions.

1. I thought this is a full screen viewer. All the screenshots appear to be windows. And it appears in a window on my PC.
2. txt files are truncated
3. When pdf files ae displayed the window flickers like crazy till it loads completely.
4. optional settings for .cfg file (all mine are = 1)
5.Runnubg on EeePC netbook 1024×600 screen. Ubuntu 9.10 OS

I was hoping this would let me view full screen documents rather than windowing. Attempting to optimize my screen readability. Do I have a setting incorrect?

If this can do what I hope, it would be outstanding!

-S

---

### Post by badchoice on 2010-03-04
Hi skooter1121,

About your questions,

1. You can!
2. This is a bug that needs to be fixed, its in the list
3. Already fixed
4. Yes, but there is people that like to change some of that options


The problem is that you're using the last stable version, and all that fixes are in the development branch... we will release the new 0.5 version soon but if you can't wait you can download it from bzr, there are instructions on how to install it in the launchpad answers page

Tell me if you have problems, or simply wait a couple of weeks ;)

---

### Post by skooter1121 on 2010-03-04
Thank You for the quick reply.

I will wait for your new release with great anticipation.

:D

-S

---

### Post by davim on 2010-04-15
When will the ppa be available for Lucid??

---

### Post by davim on 2010-04-22
Any news on this project?

---

### Post by ammonkey on 2010-04-24
bump!

You can find the packages for lucid here in the official gloobus ppa,
ppa:gloobus-dev/gloobus-preview

or in elementary-desktop ppa (in a few minutes Danrabbit stop playing wii ;) ),
ppa:elementaryart/elementarydesktop

or in nautilus-elementary ppa,
ppa:am-monkeyd/nautilus-elementary-ppa

enjoy ;)

---

### Post by davim on 2010-04-28
Great :) thanks :)

---

### Post by davim on 2010-04-29
The Gloobus Project should be part of the Ayatana project :P

[https://wiki.ubuntu.com/Ayatana](https://wiki.ubuntu.com/Ayatana)

---

### Post by davim on 2010-05-21
Is it just me or the gloobus blog has been too quiet?

---

### Post by davim on 2010-06-09
Hi! I've dêem the new features on the bar branch, when will they hit the ppa???

---

### Post by badchoice on 2010-06-10
Hey! Sure they'll be in the ppa, just be a little patient, I'm really busy lately with personal works and I have not so much time for gloobus, but I keep working on it, 

In a while we'll post the new version in the ppa, including a few new features ;)

See u!

---

### Post by davim on 2010-06-23
You can open adobe illustrator files by changing their extention from ai to pdf, gloobus showld be able to preview .ai files by treating them as pdf files :) what do you think?

---

### Post by badchoice on 2010-06-23
Woo Nice to know this!

Can you fill a bug in launchpad so I can track it and do it, it will be easy :D

---

### Post by DJ_Peng on 2010-06-25
> **davim said:**
> You can open adobe illustrator files by changing their extention from ai to pdf, ... <snip>
Sweet! This is definitely news I can use. Thanks for posting it. And for all of the updates to Gloobus.

---

### Post by davim on 2010-06-28
Bug reported :)

[https://bugs.launchpad.net/gloobus-preview/+bug/599359](https://bugs.launchpad.net/gloobus-preview/+bug/599359)

---

### Post by davim on 2010-08-21
gloobus-preview got uninstaled and now I can't install it :(

gloobus-preview:
 Depends: libgvfscommon0 but it is not going to be installed

---

### Post by Shpongle on 2010-08-21
Kind of off topic but anyone interested in making a gtk to fit with the gloobus look ?

heres some mockups which would fit with it , [http://fav.me/d2e5b3x](http://fav.me/d2e5b3x)

[http://fav.me/d1zl22q](http://fav.me/d1zl22q)

---

### Post by ammonkey on 2010-08-21
> **Shpongle said:**
> Kind of off topic but anyone interested in making a gtk to fit with the gloobus look ?

heres some mockups which would fit with it , [http://fav.me/d2e5b3x](http://fav.me/d2e5b3x)

[http://fav.me/d1zl22q](http://fav.me/d1zl22q)

u mean something like this? ;) [http://linux.softpedia.com/get/Desktop-Environment/Themes/Gloobus-Meta-Theme-54524.shtml](http://linux.softpedia.com/get/Desktop-Environment/Themes/Gloobus-Meta-Theme-54524.shtml)

edit: didn't saw the screenshot when u posted the first time.
One thing for sure is u can't have tabs in windows decorations without heavy source code modifications on all the apps you use or rewriting the window manager. Maybe the windicators would introduce theses possibilities.

---

### Post by Shpongle on 2010-08-21
More so with transparency , akin  to those of the mockups , but thanks anyway

---

### Post by ammonkey on 2010-08-21
> **davim said:**
> gloobus-preview got uninstaled and now I can't install it :(

gloobus-preview:
 Depends: libgvfscommon0 but it is not going to be installed

works fine just removed reinstalled. just install the dependency.

---

### Post by davim on 2010-08-21
If I try to install it will remove lots of other packages:

$ sudo aptitude install libgvfscommon0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information... Done
Initializing package states... Done       
The following NEW packages will be installed:
  libgvfscommon0 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 67.3kB of archives. After unpacking 197kB will be used.
The following packages have unmet dependencies:
  gvfs: Conflicts: libgvfscommon0 but 1.6.1-0ubuntu1build1 is to be installed.
The following actions will resolve these dependencies:

       Remove the following packages:                                                       
1)       backintime-gnome                                                                   
2)       bleachbit                                                                          
3)       brasero                                                                            
4)       evolution                                                                          
5)       evolution-couchdb                                                                  
6)       evolution-exchange                                                                 
7)       evolution-indicator                                                                
8)       evolution-plugins                                                                  
9)       f-spot                                                                             
10)      gbrainy                                                                            
11)      gdm                                                                                
12)      gdm-guest-session                                                                  
13)      glade-gnome                                                                        
14)      glippy                                                                             
15)      gnome-about                                                                        
16)      gnome-activity-journal                                                             
17)      gnome-applet-globalmenu                                                            
18)      gnome-applets                                                                      
19)      gnome-do                                                                           
20)      gnome-do-docklets                                                                  
21)      gnome-do-plugins                                                                   
22)      gnome-globalmenu                                                                   
23)      gnome-mag                                                                          
24)      gnome-orca                                                                         
25)      gnome-panel                                                                        
26)      gnome-photo-printer                                                                
27)      gnome-power-manager                                                                
28)      gnome-session                                                                      
29)      gnome-utils                                                                        
30)      gufw                                                                               
31)      gvfs                                                                               
32)      gvfs-backends                                                                      
33)      gvfs-bin                                                                           
34)      gvfs-fuse                                                                          
35)      indicator-applet                                                                   
36)      indicator-applet-appmenu                                                           
37)      indicator-applet-complete                                                          
38)      indicator-applet-session                                                           
39)      libbonoboui2-0                                                                     
40)      libbonoboui2-dev                                                                   
41)      libgail-gnome-module                                                               
42)      libgnome-pilot2                                                                    
43)      libgnome2-0                                                                        
44)      libgnome2-dev                                                                      
45)      libgnome2-perl                                                                     
46)      libgnome2.24-cil                                                                   
47)      libgnomepanel2.24-cil                                                              
48)      libgnomeui-0                                                                       
49)      libgnomeui-dev                                                                     
50)      liblpint-bonobo0                                                                   
51)      libpanel-applet2-0                                                                 
52)      libunity0                                                                          
53)      mousetweaks                                                                        
54)      mysql-query-browser                                                                
55)      mysql-workbench-gpl                                                                
56)      nautilus                                                                           
57)      nautilus-image-converter                                                           
58)      nautilus-share                                                                     
59)      python-gnome2                                                                      
60)      python-gnome2-desktop                                                              
61)      python-gnomeapplet                                                                 
62)      python-pyatspi                                                                     
63)      remmina-gnome                                                                      
64)      revelation                                                                         
65)      rhythmbox                                                                          
66)      rhythmbox-plugin-cdrecorder                                                        
67)      rhythmbox-plugins                                                                  
68)      rhythmbox-ubuntuone-music-store                                                    
69)      scribes                                                                            
70)      system-config-printer-gnome                                                        
71)      tomboy                                                                             
72)      tsclient                                                                           
73)      ubuntu-desktop                                                                     
74)      ubuntu-netbook-unity-default-settings                                              
75)      ubuntu-tweak                                                                       
76)      unity                                                                              
77)      unity-place-applications                                                           
78)      unity-place-files                                                                  
79)      usb-creator-gtk                                                                    
80)      vinagre                                                                            

       Leave the following dependencies unresolved:                                         
81)      alacarte recommends gnome-panel                                                    
82)      apturl recommends libgnome2-perl                                                   
83)      gcalctool recommends gvfs                                                          
84)      gnome-bluetooth recommends gvfs-backends                                           
85)      gnome-system-monitor recommends gvfs                                               
86)      gnome-terminal recommends gvfs                                                     
87)      gstreamer0.10-plugins-base recommends gvfs                                         
88)      indicator-messages recommends indicator-applet | indicator-renderer                
89)      indicator-session recommends indicator-applet (>= 0.2) | indicator-renderer        
90)      metacity recommends gnome-session | x-session-manager                              
91)      ubuntu-desktop recommends evolution-couchdb                                        
92)      ubuntu-desktop recommends evolution-exchange                                       
93)      ubuntu-desktop recommends evolution-indicator                                      
94)      ubuntu-desktop recommends gbrainy                                                  
95)      ubuntu-desktop recommends gnome-mag                                                
96)      ubuntu-desktop recommends libgail-gnome-module                                     
97)      ubuntu-desktop recommends mousetweaks                                              
98)      ubuntu-desktop recommends nautilus-share                                           
99)      ubuntu-desktop recommends tsclient                                                 
100)     vino recommends gvfs                                                               
101)     bzr-gtk recommends python-gnome2-desktop                                           
102)     glade-gnome recommends libgnomeui-dev                                              
103)     glade-gnome recommends libbonoboui2-dev                                            
104)     meld recommends python-gnome2                                                      
105)     mysql-admin recommends mysql-query-browser                                         
106)     empathy recommends gvfs-backends                                                   
107)     evince recommends gvfs                                                             
108)     evolution-common recommends evolution                                              
109)     file-roller recommends gvfs                                                        
110)     gedit recommends python-gnome2                                                     
111)     gnome-control-center recommends gnome-session                                      
112)     gnome-control-center recommends mousetweaks                                        
113)     gnome-orca recommends gnome-mag (>= 0.12.5)                                        
114)     gnome-panel recommends gnome-applets (>= 2.12.1-1)                                 
115)     gnome-panel recommends gvfs                                                        
116)     gnome-panel-data recommends gnome-panel                                            
117)     gnome-screensaver recommends gnome-power-manager | xfce4-power-manager             
118)     synaptic recommends libgnome2-perl                                                 
119)     banshee recommends brasero                                                         
120)     gdebi recommends libgnome2-perl                                                    
121)     nautilus-data recommends nautilus                                                  
122)     awn-applets-python-core-trunk recommends gnome-applets                             
123)     unity recommends unity-place-applications                                          
124)     unity recommends unity-place-files                                                 
125)     indicator-appmenu recommends indicator-applet | indicator-renderer                 
126)     indicator-datetime recommends indicator-applet | indicator-renderer                
127)     glippy-ubuntu-mono recommends glippy                                               
128)     gnome-globalmenu-common recommends gnome-applet-globalmenu | gnome-globalmenu-xfce4
129)     terminator recommends python-gnome2                                                
130)     mutter recommends gnome-session | x-session-manager                                
       Tier: Safe actions, Remove packages (10000)

---

### Post by ammonkey on 2010-08-21
> **davim said:**
> If I try to install it will remove lots of other packages:

$ sudo aptitude install libgvfscommon0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information... Done
Initializing package states... Done       
The following NEW packages will be installed:
  libgvfscommon0 
.............
129)     terminator recommends python-gnome2                                                
130)     mutter recommends gnome-session | x-session-manager                                
       Tier: Safe actions, Remove packages (10000)

really weird, hum ok i am gonna update the package anyway this depencie is not necessary now.

---

### Post by ammonkey on 2010-08-21
@davim: just updated :)

---

### Post by guv999 on 2010-08-21
just updated through the PPA and now cannot locate Gloobus Preview or indeed use it.
I have checked in synaptic and gloobus-preview is installed.
It has been removed from the accessories section of the main menu, and when i try and run it through the terminal i just get 'command not found'.   any help gratefully appreciated

---

### Post by ammonkey on 2010-08-21
sudo add-apt-repository ppa:gloobus-dev/gloobus-preview
apt-get update
sudo apt-get install gloobus-preview

that's it.

if it still don't work:
sudo apt-get install --reinstall gloobus-preview


(work with elementary-desktop, nautilus-elementary ppas too)

---

### Post by guv999 on 2010-08-21
> **ammonkey said:**
> sudo add-apt-repository ppa:gloobus-dev/gloobus-preview
apt-get update
sudo apt-get install gloobus-preview

that's it.

if it still don't work:
sudo apt-get install --reinstall gloobus-preview


(work with elementary-desktop, nautilus-elementary ppas too)

Thanks for the advice, but it has not resolved the issue, i still cannot get Gloobus Preview going

---

### Post by ammonkey on 2010-08-21
fixed, sry i am running maverick as my default system so i had to launch a VM to check and rebuild the package. 

rebuilded and tested, should works fine now. just wait for your ppa to be updated.

---

### Post by guv999 on 2010-08-22
> **ammonkey said:**
> fixed, sry i am running maverick as my default system so i had to launch a VM to check and rebuild the package. 

rebuilded and tested, should works fine now. just wait for your ppa to be updated.

Thanks.....just updated now - all working well.  Thanks for your help:p

---

### Post by Frogs Hair on 2010-08-22
I have installed the Gloobus PPA Twice and it installs and opens but simply doesn't work . I'm not sure what I am doing wrong . I'm using Nautilus Elementary if that helps at all .

---

### Post by Elitist on 2010-08-22
Did the PPA install. Gloobus just shows empty black box, apparently doesn't work.

---

### Post by ammonkey on 2010-08-22
gloobus is a previewer if you just launch the application of course you'll get an empty black box because there s nothing to preview.

You can use from command line
gloobus-preview file_you_want_to_preview

Or more comfortable, use it with nautilus-elementary then for all the selected files press space and you've got your preview.

---

### Post by Frogs Hair on 2010-08-22
> **ammonkey said:**
> gloobus is a previewer if you just launch the application of course you'll get an empty black box because there s nothing to preview.

You can use from command line
gloobus-preview file_you_want_to_preview

Or more comfortable, use it with nautilus-elementary then for all the selected files press space and you've 

got your preview.
Thanks, I will try again

---

### Post by Frogs Hair on 2010-08-22
Success ! thanks again ammonkey.

---

### Post by davim on 2010-09-06
When installing in maverick from the PPA I'm gettin this error:



Setting up gloobus-preview (0.4.5-ubuntu7~ppa245) ...
/var/lib/dpkg/info/gloobus-preview.postinst: 33: gdk-pixbuf-query-loaders: not found
dpkg: error processing gloobus-preview (--configure):
 subprocess installed post-installation script returned error exit status 127

---

### Post by davim on 2010-09-06
Sovled by installing the package clutter-gtk-support :P maybe this showld be a dependency of the package gloobus-preview :)

> **davim said:**
> When installing in maverick from the PPA I'm gettin this error:



Setting up gloobus-preview (0.4.5-ubuntu7~ppa245) ...
/var/lib/dpkg/info/gloobus-preview.postinst: 33: gdk-pixbuf-query-loaders: not found
dpkg: error processing gloobus-preview (--configure):
 subprocess installed post-installation script returned error exit status 127

---

### Post by jastonas on 2010-09-22
> **davim said:**
> Sovled by installing the package clutter-gtk-support :P maybe this showld be a dependency of the package gloobus-preview :)

Having the same problem. Where can I get clutter-gtk-support ?

---

### Post by mul14 on 2010-09-26
> **jastonas said:**
> Having the same problem. Where can I get clutter-gtk-support ?
[http://www.webupd8.org/2010/02/nautilus-elementary-gets-coverflow.html](http://www.webupd8.org/2010/02/nautilus-elementary-gets-coverflow.html)

---

### Post by Legendary_Bibo on 2010-09-26
Well I'm trying to install it on lucid, and it did. Well I didn't realize that you needed elementary nautilus which I got, but afterwards. So as of now, it's not working and I don't know why. What I mean by it's not working is that when I hit spacebar nothing happens, and there's no preview option in nautilus. I've restarted nautilus, and even logged out and logged back in. What's going on?

---

### Post by Legendary_Bibo on 2010-09-26
wait scratch that. It doesn't work so well when you have your files to open on one click. Nice feature! Although I would like it if I could have it open with a mouse hover.

---

### Post by Dr Belka on 2010-09-26
Bro, that is a Coheed And Cambria album on the gloobus website

---

### Post by Legendary_Bibo on 2010-09-26
Ah, tested it with a bunch of file formats. Works for all of them! I don't have it set to look at text documents, pdf files, or gimp files though just because I consider those program specific files. Very nice! Although one note on it. It stutters heavily with HD videos, but that's fine. VLC has been the only thing that could handle it on Linux for me.

---

### Post by tjeremiah on 2010-09-27
for some reason I cant reinstall this program in 10.10. I have nautilus elementary but when I go to install Gloobus, it now tells me that I need libpoppler5. I'm searching for it and cant find any results.

---

### Post by habtool on 2010-09-28
> **tjeremiah said:**
> for some reason I cant reinstall this program in 10.10. I have nautilus elementary but when I go to install Gloobus, it now tells me that I need libpoppler5. I'm searching for it and cant find any results.

A quick work around for now is to install libpoppler5 from lucid, you can get it here:

[https://launchpad.net/ubuntu/lucid/+package/libpoppler5](https://launchpad.net/ubuntu/lucid/+package/libpoppler5)

[http://launchpadlibrarian.net/47847676/libpoppler5_0.12.4-0ubuntu5_i386.deb](http://launchpadlibrarian.net/47847676/libpoppler5_0.12.4-0ubuntu5_i386.deb)
[http://launchpadlibrarian.net/47850908/libpoppler5_0.12.4-0ubuntu5_ia64.deb](http://launchpadlibrarian.net/47850908/libpoppler5_0.12.4-0ubuntu5_ia64.deb)

---

### Post by tjeremiah on 2010-09-28
> **habtool said:**
> A quick work around for now is to install libpoppler5 from lucid, you can get it here:

[https://launchpad.net/ubuntu/lucid/+package/libpoppler5](https://launchpad.net/ubuntu/lucid/+package/libpoppler5)

[http://launchpadlibrarian.net/47847676/libpoppler5_0.12.4-0ubuntu5_i386.deb](http://launchpadlibrarian.net/47847676/libpoppler5_0.12.4-0ubuntu5_i386.deb)
[http://launchpadlibrarian.net/47850908/libpoppler5_0.12.4-0ubuntu5_ia64.deb](http://launchpadlibrarian.net/47850908/libpoppler5_0.12.4-0ubuntu5_ia64.deb)
thanks.

---

### Post by jdorenbush on 2010-09-28
> **habtool said:**
> A quick work around for now is to install libpoppler5 from lucid, you can get it here:

[https://launchpad.net/ubuntu/lucid/+package/libpoppler5](https://launchpad.net/ubuntu/lucid/+package/libpoppler5)

[http://launchpadlibrarian.net/47847676/libpoppler5_0.12.4-0ubuntu5_i386.deb](http://launchpadlibrarian.net/47847676/libpoppler5_0.12.4-0ubuntu5_i386.deb)
[http://launchpadlibrarian.net/47850908/libpoppler5_0.12.4-0ubuntu5_ia64.deb](http://launchpadlibrarian.net/47850908/libpoppler5_0.12.4-0ubuntu5_ia64.deb)

Thanks for the quick fix!

Is that ia64.deb supposed to be like the amd64 files? If so, it didn't work for me, I had to downloaded the .deb from Launchpad: [http://launchpadlibrarian.net/47847826/libpoppler5_0.12.4-0ubuntu5_amd64.deb](http://launchpadlibrarian.net/47847826/libpoppler5_0.12.4-0ubuntu5_amd64.deb)

---

### Post by ammonkey on 2010-09-28
Hello, 

some libs have changed/renamed so the package need to be rebuilded. I'll try to do it this week. I'll keep you in the loop.

---

### Post by DachaArh on 2010-10-27
Trying to install covergloobus on Ubuntu 10.10

I add repo and when I do : sudo apt-get update, I get this in terminal:
```
W: Failed to fetch http://ppa.launchpad.net/gloobus-dev/covergloobus/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/gloobus-dev/covergloobus/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

after that sudo apt-get install covergloobus gets me :
```
E: Unable to locate package covergloobus
```

any help?  thanks in advance...

---

### Post by ben2talk on 2010-11-21
Yes, it's installed - and the ppa too, but often (very often - for the last 4 days in a row now) I'm unable to clear my updates because of this repo.

Just be sure to make sure you check the sources and select the fastest of them - see if a change in server will clear it up for you.

---

### Post by Snoopy_5_1 on 2011-01-06
Hello,

I just installed gloobus, and I dont know how I could live before ;)
One small problem the openoffice dokuments are only shown as symbols and not the text itself.
Is there a way to fix it?
So pdg and pictures are shown correct.

In the small symbol is the browser there I can see the text with the help of nautilus but sadley not if I hit the space bar and want to make it big there only the smybol can be seen.

Best wishes

---

### Post by Snoopy_5_1 on 2011-01-11
Hy,

I installed the packed unconv
Now its working

---

### Post by blehmeco on 2011-02-22
Installed gloobus-preview as per the instructions found [here]("http://gloobus.net/wiki/index.php?title=Install#Installing_Gloobus_Preview_from_the_PPA") (under "Installing Gloobus Preview from Source (recommended)") but when I try to use it it just opens a gloobus preview window of my user folder (I defined a keyboard shortcut in compiz for gloobus-preview to open directly with the keyboard and when use that key combination with a file selected all I get is that window)...
Moreover, when trying to run Gloobus-preview on a Clipboard file using this method in Terminal:
```
gloobus-preview
```I get this error:
```
** (gloobus-preview:2010): WARNING **: Config file couldn't be readed
[WARNING] No cover found, using default icon
```I'm using Ubuntu 10.04 LTS with Macbuntu installed too...

Anyone knows what's wrong here?
Did I do anything wrong with the installation? Or is it related to Macbuntu stuff?

Appreciate your help guys!

Cheers!

---

### Post by PenguinOfSteel on 2011-04-21
Hi to all!! This is my first time in this thread!

I've been using covergloobus for months, adapted some themese for my personal use, etc.

Is there way to format the text displayed adding extra elements?
e.g. add a dot after track number, closing the length within [ ] etc.

Thanks

---

### Post by blehmeco on 2011-04-21
Hello there PenguinOfSteel!

Sorry I don't have an answer 4 U, but can U please tell me the steps you went through to get gloobus working?...I've been at this for months and didn't have any luck yet!

Thanks!

---

### Post by PenguinOfSteel on 2011-04-21
> **blehmeco said:**
> Hello there PenguinOfSteel!

Sorry I don't have an answer 4 U, but can U please tell me the steps you went through to get gloobus working?...I've been at this for months and didn't have any luck yet!

Thanks!

Hi! I've had some problem with the package in the repository.

I'm on ubuntu maverick 64 bit and I use guayadeque as mediaplayer.

I have downloaded the source code using the bazaar branch (the development channel of covergloobus)

to download it, type this in the terminal

bzr branch lp:covergloobus
cd covergloobus
./configure
make
sudo make install

Then you can find it the the menu or run it using the terminal.

This works for me.

---

### Post by EgoGratis on 2011-05-07
What is "official status" on development of Gloobus-Preview?

I got it working on Natty Narwhal but i think in Maverick Meerkat i had less trouble viewing video files (crashing). 

PPA packages...

[https://launchpad.net/~gloobus-dev/+archive/gloobus-preview]("https://launchpad.net/%7Egloobus-dev/+archive/gloobus-preview")

...are a bit old and only available up to Maverick Meerkat. I was able to get Gloobus-Preview from this PPA to work...

[https://launchpad.net/~am-monkeyd/+archive/nautilus-elementary-ppa]("https://launchpad.net/%7Eam-monkeyd/+archive/nautilus-elementary-ppa")

...but as i mentioned it does have a lot of troubles (crashing). It's such a nice "tool" and i was wondering if it still being actively developed?

Thanks!

---

### Post by EgoGratis on 2011-05-08
> What is "official status" on development of Gloobus-Preview?

OK, today i see new packages for Natty Narwhal on both PPA's.

> It's such a nice "tool" and i was wondering if it still being actively developed?

So i guess it is still being actively developed and that is good news!

---

### Post by KingYaba on 2011-11-30
Does CoverGloobus even work? I followed the instructions in the first post and this program doesn't do anything. It doesn't fetch lyrics, it doesn't display album artwork. I have toyed with all the preferences, too.

---

### Post by premodern on 2011-12-20
Thanks for this great piece of tool.

I got a quick question, can I skip to the next file when the preview window is open or do I have to close it every time I want to see a different file?

Thanks !

---

### Post by Frogs Hair on 2011-12-20
It will open a new window for each file , just select the next file and press the space bar .

---

