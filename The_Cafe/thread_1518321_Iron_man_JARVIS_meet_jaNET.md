---
title: "Iron man JARVIS meet jaNET"
date: 2010-06-26
forum: The Cafe
---

### Post by jambel on 2010-06-26
Hello to community!

I'm working on a JARVIS-like system for a while and I finally release a first open source version of it! It is written in C# under Mono.

I call it Project jaNET and you can find it [**here**]("http://sites.google.com/site/projectjanet/")

Thanks for watching and please be gentle :oops:

---

### Post by Sonsum on 2010-06-26
So how exactly does this work? 

(I read the overview on the website and it confused me. Haha.)

---

### Post by jambel on 2010-06-27
hi,

if you don't want to mess with the code then you just run jaNET.exe on the bin directory, but it's better to recomplile it for yourself with mono. Then edit the AppConfig.xml with gedit or your favorite editor and give instructions you want to use, like mail, weather etc (at the time weather rss feed changed within code but I'll fix it). For instance you can setup your mail like
```
[FONT=courier new]set mail add  <host> <username> <pass> <port> <ssl>[/FONT]
``` and then with ```
 [FONT=courier new]set mail  check <int ms>[/FONT]
``` enables the listener and check the mail you have setup in the time you write in milliseconds.

You can even plug your own programs to controlling your hardware. I have include my two java programs for phidgets sonar and dual relay board. And if you look at AppConfig.xml you'll find out the calls. For example if your write sonar to janet it will return a value in cm.

If you haven't any programming skills you may find it hard but it's not actually. Things that need programming or changes to work for your needs, that may be the listeners (threads) which they're responsible to check bluetooth devices, sonar, web service, mail check etc.
Try to follow Project definition and write anything it says to get an idea.

Thanks for looking anyway!

---

### Post by rflores2323 on 2010-07-10
I want to control my home theater pc with xbmc ([www.xbmc.org]("http://www.xbmc.org/")). via some voice commands and also have the pc talk back.    Couple of questions.  

Are you able to give commands to open applications I want to be able to open xbmc application up and then maybe have janet say. welcome to xbmc or something like that. 

Are you able to control an application by putting a voice command to a key command (keyboard emulation)?  

also are you able to make custom commands? For instance making a prefix to be able to make sure the pc only hears the command when you say the prefix. For instance you say "jabba open xbmc" and it opens the application. But if you say open xbmc it does not do anything unless you give a special command like "jabba listen" so that it just listens to all your commands until another command is given. 

basically take a look at this program that is currently freeware but only works on win7 [http://voxcommando.com/](http://voxcommando.com/)
this app is really doing a great job of integrating with xbmc.  

I am sure that you would get many followers from the xbmc community as its a large community and your software can really be added to it with the new add on plugin system they are developing. take a look at the forums and go to the linux forums as there are tons and tons of users.  I am also looking at VEDICS but I see that your software talks back which is very cool.

---

### Post by jambel on 2010-07-10
I'm currently working on speech recognition and probably the second version will ship with that feature which will make jaNET even better.

Scenarios you've described probably can happen but I'm not familiar with xbmc platform.
An example to create a shortcut command to launch for example windows explorer on your system could be a record on the AppConfig.xml file like this:

        <cmdSet id="*explorer">explorer.exe </cmdSet> 
        <cmdSet id="explorer">*explorer</cmdSet>

and if you want to make it talk:

        <cmdSet id="*explorer">explorer.exe </cmdSet> 
        <cmdSet id="explorer">*explorer Explorer launched.</cmdSet>

so, when you hit explorer it will be launched.

Also jaNET is more targeting on linux systems, I'm just more interest on that and doesn't mean that if you manipulate the code you shouldn't get the results you want.

---

### Post by jambel on 2010-07-10
a recent video

[http://www.youtube.com/watch?v=M38mqXbAuLE](http://www.youtube.com/watch?v=M38mqXbAuLE)

---

### Post by rflores2323 on 2010-07-10
when do you think the 2nd version will be out?

---

### Post by Naitsirhc Hsem on 2010-07-10
How do I run this in ubuntu? what language/ compiler?

---

### Post by jambel on 2010-07-11
> **Naitsirhc Hsem said:**
> How do I run this in ubuntu? what language/ compiler?

you should install [monodevelop]("http://monodevelop.com/"), if you are not familiar it's a c# IDE and you can install it by synaptic

---

### Post by Naitsirhc Hsem on 2010-07-11
Thanks, I'm trying it now :)

---

### Post by jambel on 2010-07-16
> **rflores2323 said:**
> when do you think the 2nd version will be out?

I haven't plan a date for the second version cause I'm too busy at the time, but it will have features like voice dictation and a kind of scripting language support.

---

### Post by LowSky on 2010-07-16
you should talk with this guy, your basically working on the same thing
[http://projectjarvis.com/](http://projectjarvis.com/)

---

### Post by jambel on 2010-07-16
> **LowSky said:**
> you should talk with this guy, your basically working on the same thing
[http://projectjarvis.com/](http://projectjarvis.com/)

I have sent him an email for collaboration, especially when he decide to re-design it, but I get no reply at all :(

---

### Post by jambel on 2010-12-04
jaNET has an installation guide and currently supports speech recognition.

[Installation guide]("http://sites.google.com/site/projectjanet/installation")

[Recent Video]("http://www.youtube.com/watch?v=i2DUL4vOHm4")

---

### Post by Sonsum on 2010-12-20
> **jambel said:**
> I have sent him an email for collaboration, especially when he decide to re-design it, but I get no reply at all :(

If you're still looking into a collaboration with him, don't. His project only works through AppleScript and isn't very marvelous at all. I had a Mac for a bout a month and made my own system. He wouldn't be very helpful.

---

### Post by Dustin2128 on 2010-12-20
impressive! The Celsius pronunciation (chelsius) bugs me a bit though.

---

### Post by PhantmKllr on 2010-12-20
I would like to see a debian package of jaNET. Plus I'd like to help out anyway I can. I have a reseller hosting plan, and I'll be glad to give you free hosting if you're interested.

---

### Post by Sonsum on 2010-12-21
> **Dustin2128 said:**
> impressive! The Celsius pronunciation (chelsius) bugs me a bit though.

It was driving me insane. I found a neat little fix. All you have to do is remove Celsius from the response string in AppConfig.xml.

It'll just say degrees which also makes it universal (I measure my degress in Farenheit ;))

---

### Post by jambel on 2011-01-04
;)

> **Sonsum said:**
> If you're still looking into a collaboration with him, don't. His project only works through AppleScript and isn't very marvelous at all. I had a Mac for a bout a month and made my own system. He wouldn't be very helpful.

---

### Post by jambel on 2011-01-04
you can remove it as mentioned from Sonsum!

> **Dustin2128 said:**
> impressive! The Celsius pronunciation (chelsius) bugs me a bit though.

---

### Post by jambel on 2011-01-04
I have a friend that can provide me free hosting but google sites are more convenient. Thank you anyway, I really appreciate it!

I intend to build a Debian package in future versions.

> **PhantmKllr said:**
> I would like to see a debian package of jaNET. Plus I'd like to help out anyway I can. I have a reseller hosting plan, and I'll be glad to give you free hosting if you're interested.

---

### Post by rflores2323 on 2011-01-04
This project is awesome and I cant wait to see a stable release.  I think you need a rss feed or something to inform people of hte progress.  

Also if I download this what type of mic does it need?  Or can I use a cell phone?  Are you thinking of developing an application for android that interacts with it.  I love the bluetooth integration however I also think using the cell phone to get information to send/receive is the way to go.   I am in noway a coder or anything but this project is awesome and I am looking forward to trying it out.

---

### Post by Sonsum on 2011-01-04
> **rflores2323 said:**
> This project is awesome and I cant wait to see a stable release.  I think you need a rss feed or something to inform people of hte progress.  

Also if I download this what type of mic does it need?  Or can I use a cell phone?  Are you thinking of developing an application for android that interacts with it.  I love the bluetooth integration however I also think using the cell phone to get information to send/receive is the way to go.   I am in noway a coder or anything but this project is awesome and I am looking forward to trying it out.

The current release is very stable and works quite well! Currently, it appears that interaction takes place either by voice command via SIMON (which can be a little frustrating) or by terminal entry. There's currently no .deb, but the instructions on installation work great!

---

### Post by Shpongle on 2011-01-04
This is very cool , I was thinking about starting a system like this but Ill just help if I can, wont be able to help until the summer I'm afraid due to college.

---

### Post by Windows Nerd on 2011-01-05
Have you heard about the openkinect project and the stuff they are developing over there? Some hand-gesture stuff/movement recognition would be a neat addition to this project. Just an idea.

---

### Post by zer010 on 2011-01-05
> **Windows Nerd said:**
> Have you heard about the openkinect project and the stuff they are developing over there? Some hand-gesture stuff/movement recognition would be a neat addition to this project. Just an idea.
+1  
That's actually a great idea.

---

### Post by jambel on 2011-01-05
Thanks man, you can subscribe to [project's site]("https://sites.google.com/site/projectjanet/") and get alerts when something is changed. Also [https://sites.google.com/site/projectjanet/project-updates/posts.xml](https://sites.google.com/site/projectjanet/project-updates/posts.xml)

You can work with any mic you can connect to your computer even your bluetooth headset!

Yes, maybe in the future I will create a program for android. In the next version 0.1.4 I include a python script for Symbian S60 phones like my Nokia X6 to send remotely commands to jaNET. Also already jaNET send responses by mail or sms.

I'm also preparing an installation script for those who have difficulties with [installation tutorial]("https://sites.google.com/site/projectjanet/installation").

> **rflores2323 said:**
> This project is awesome and I cant wait to see a stable release.  I think you need a rss feed or something to inform people of hte progress.  

Also if I download this what type of mic does it need?  Or can I use a cell phone?  Are you thinking of developing an application for android that interacts with it.  I love the bluetooth integration however I also think using the cell phone to get information to send/receive is the way to go.   I am in noway a coder or anything but this project is awesome and I am looking forward to trying it out.

---

### Post by jambel on 2011-01-05
Yes I've heard it and before kinect I was trying to understand some fundamentals in optical recognition by creating a windows webcam based application ([http://www.youtube.com/watch?v=zstj8vJ609A](http://www.youtube.com/watch?v=zstj8vJ609A))

When kinect was introduced as project natal I thought, wow it would be great if I could  integrate it with jaNET and when I'm in my workshop builting something and listening music and then my cell phone rang, I could have something like...

- jaNET
- Yes John
- Adjust Volume
- Waiting for adjustment..
- and then move my hand down or up to increase or decrease it

Unfortunately I'm not a gamer to buy one, so it's not an essential.
My drawbacks are not the lack of ideas or technical resources but money :(

> **Windows Nerd said:**
> Have you heard about the openkinect project and the stuff they are developing over there? Some hand-gesture stuff/movement recognition would be a neat addition to this project. Just an idea.

---

### Post by jambel on 2011-01-05
Take your time, probably until summer jaNET would be more functional as I see many people, including this forum, getting involved to the project!

Already someone named platinummonkey make an [entry to Arch linux wiki]("https://wiki.archlinux.org/index.php/JaNET")!

My hope is to create a community, including some programmers, to provide better results in a short period!

> **Shpongle said:**
> This is very cool , I was thinking about starting a system like this but Ill just help if I can, wont be able to help until the summer I'm afraid due to college.

---

### Post by jambel on 2011-01-05
Until debian package in next version I'll try to make an installation script to automate most of the progress, if not all!

> **Sonsum said:**
> The current release is very stable and works quite well! Currently, it appears that interaction takes place either by voice command via SIMON (which can be a little frustrating) or by terminal entry. There's currently no .deb, but the instructions on installation work great!

---

### Post by Shpongle on 2011-01-05
> **jambel said:**
> Take your time, probably until summer jaNET would be more functional as I see many people, including this forum, getting involved to the project!

Already someone named platinummonkey make an [entry to Arch linux wiki]("https://wiki.archlinux.org/index.php/JaNET")!

My hope is to create a community, including some programmers, to provide better results in a short period!

Cool Im doing an android based project for my final year project so I could help  with that too if needed.

---

### Post by jambel on 2011-01-05
Definitely, we will talk about the specs when you are available!

> **Shpongle said:**
> Cool Im doing an android based project for my final year project so I could help  with that too if needed.

---

### Post by Shpongle on 2011-01-05
Cool I'm looking forward to it and have lots of ideas... just out of curiosity does Janet require the user to train her?/it to recognize the users voice ?. I can pick up c# too if needed . I have a experience with few other languages and can help with design and testing too. for now Ill keep making a note of the ideas and Ill let you know when I have a good few.

---

### Post by Sonsum on 2011-01-05
> **Shpongle said:**
> Cool I'm looking forward to it and have lots of ideas... just out of curiosity does Janet require the user to train her?/it to recognize the users voice ?. I can pick up c# too if needed . I have a experience with few other languages and can help with design and testing too. for now Ill keep making a note of the ideas and Ill let you know when I have a good few.

As far as I can tell, JaNET gets her voice input from SIMON, which I've had to train a bit to work right.

---

### Post by Windows Nerd on 2011-01-05
> **jambel said:**
> Yes I've heard it and before kinect I was trying to understand some fundamentals in optical recognition by creating a windows webcam based application ([http://www.youtube.com/watch?v=zstj8vJ609A](http://www.youtube.com/watch?v=zstj8vJ609A))

When kinect was introduced as project natal I thought, wow it would be great if I could  integrate it with jaNET and when I'm in my workshop builting something and listening music and then my cell phone rang, I could have something like...

- jaNET
- Yes John
- Adjust Volume
- Waiting for adjustment..
- and then move my hand down or up to increase or decrease it

Unfortunately I'm not a gamer to buy one, so it's not an essential.
My drawbacks are not the lack of ideas or technical resources but money :(

It's lack of money that stops me from buying one as well. The kinect is, however, apparently much cheaper than entry-level all-in-one light sensors/ir_sensors/microphones (which is what the kinect essentially is). That's why many universities like it, and  that use is causing Microsoft to support the open drivers (to some extent).

I would love to help out with this project, it sounds cool and quite useful, but my time is limited, and I am just a novice when it comes to programming.

---

### Post by jambel on 2011-01-06
Yes for speech recognition jaNET using Simon.

There is no need for training if words included to the dictionary. The reason I pick Simon, it's because it's very easy to configure.

I can help you if you have issues!

> **Sonsum said:**
> As far as I can tell, JaNET gets her voice input from SIMON, which I've had to train a bit to work right.

---

### Post by jambel on 2011-01-06
> **Windows Nerd said:**
> It's lack of money that stops me from buying one as well. The kinect is, however, apparently much cheaper than entry-level all-in-one light sensors/ir_sensors/microphones (which is what the kinect essentially is). That's why many universities like it, and  that use is causing Microsoft to support the open drivers (to some extent).

>  I would love to help out with this project,you are welcome!

>  it sounds cool and quite useful,>  but my time is limited,as mine :)

>  and I am just a novice when it comes to programming.

---

### Post by slackthumbz on 2011-01-06
[http://en.wikipedia.org/wiki/JANET](http://en.wikipedia.org/wiki/JANET)

Just sayin'...

---

### Post by Sonsum on 2011-01-06
> **slackthumbz said:**
> [http://en.wikipedia.org/wiki/JANET](http://en.wikipedia.org/wiki/JANET)

Just sayin'...

But ours has fancy capitalization. :p

---

### Post by Shamgar91 on 2011-03-19
quick question: I've installed jaNET and Simon on my computer and, for the most part, things seem to be running quite smoothly. However, I have two minor difficulties right now. I say "janet" and jaNET is supposed to start up right? I get this message in the Terminal every time: There was an error creating the child process for this terminal. Failed to execute child process "janet.sh" (No such file or directory)

Problem number two; whenever I type "janet" into the terminal the program works and I can use it, but after I used it and it gets done telling me what I want it to, it automatically closes.

Any help with these would be great!

---

### Post by jambel on 2011-03-21
Currently script is called janet without .sh. Go to simon and replace every command refer to janet.sh with janet.

The unexpected closes might probably happen if you haven't an internet connection. Please download again the Bin.tar.gz and replace your jaNET.exe with the new one.

> **Shamgar91 said:**
> quick question: I've installed jaNET and Simon on my computer and, for the most part, things seem to be running quite smoothly. However, I have two minor difficulties right now. I say "janet" and jaNET is supposed to start up right? I get this message in the Terminal every time: There was an error creating the child process for this terminal. Failed to execute child process "janet.sh" (No such file or directory)

Problem number two; whenever I type "janet" into the terminal the program works and I can use it, but after I used it and it gets done telling me what I want it to, it automatically closes.

Any help with these would be great!

---

