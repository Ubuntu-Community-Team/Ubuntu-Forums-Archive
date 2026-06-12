---
title: "New Ubuntu Pandora Radio Program Need Testers"
date: 2009-12-22
forum: The Cafe
---

### Post by AndThenWhat on 2009-12-22
Hello all,

I have developed a desktop application called "Pandora Control" that is a graphical wrapper for the command line program "pianobar".  When they are coupled together they form a standalone Pandora Radio desktop app for Ubuntu.

I need people to test this deb and application and confirm they work.  

You can download the debs here:
[http://www.mediafire.com/?sharekey=e4f3285d4edb57b3d41644271fb54c6ce13f17d9de70c83ee6900953521448c9](http://www.mediafire.com/?sharekey=e4f3285d4edb57b3d41644271fb54c6ce13f17d9de70c83ee6900953521448c9)

YouTube Demonstration here: 
[http://www.youtube.com/watch?v=Jc7FzQuZY9A](http://www.youtube.com/watch?v=Jc7FzQuZY9A)

---

### Post by steveneddy on 2009-12-22
But Pandora runs fine in a browser.

---

### Post by AndThenWhat on 2009-12-22
Yep..but it is much more convenient to minimize it to the system tray unless you need it. Not only that, but this method uses less processor power.

---

### Post by JoshuaRL on 2009-12-22
Have the source anywhere?  Might be a good idea to make that available so as not to make the GPL zealots angry.

And also to make it right.

---

### Post by donniezazen on 2009-12-22
> 
Error: Dependency is not satisfiable: libfaad2-0


This package is not available in Lucid. Can you also post some screen cast?

---

### Post by KIAaze on 2009-12-23
And again...
>  We are deeply, deeply sorry to say that due to licensing constraints, we can no longer allow access to Pandora for listeners located outside of the U.S. We will continue to work diligently to realize the vision of a truly global Pandora, but for the time being we are required to restrict its use. We are very sad to have to do this, but there is no other alternative. 

---

### Post by AndThenWhat on 2009-12-23
Here's some screenshots

---

### Post by AndThenWhat on 2009-12-23
Glade file and Python source in the attached archive.

---

### Post by steveneddy on 2009-12-23
> **AndThenWhat said:**
> Yep..but it is much more convenient to minimize it to the system tray unless you need it. Not only that, but this method uses less processor power.

OK - but why run it from the system tray if you can just keep it in as a little applet on the top bar.

---

### Post by dmillerw on 2009-12-23
Awesome program, some suggestions though.

Maybe have the stations listed instead of asking for the #.

Some sort of indicator of the song currently playing.

Otherwise, great program, although I think I'll use pianobar.

EDIT: If you would like a basic screencast made demonstrating it, I'd be happy to make it.

---

### Post by AndThenWhat on 2009-12-23
> **steveneddy said:**
> OK - but why run it from the system tray if you can just keep it in as a little applet on the top bar.

I'm not sure what you mean.  Basically, I have made it so that if you click the system tray icon the program hides itself and if you click it again it shows itself.  That way, if you are working for instance, you can listen to Pandora without an extra window to clutter your workspace and use less processing power at the same time by avoiding opening a browser and running Adobe Flash.

---

### Post by AndThenWhat on 2009-12-23
> **dmillerw said:**
> Awesome program, some suggestions though.

Maybe have the stations listed instead of asking for the #.

Some sort of indicator of the song currently playing.

Otherwise, great program, although I think I'll use pianobar.

EDIT: If you would like a basic screencast made demonstrating it, I'd be happy to make it.


I'm planning on adding those features later.  The main obstacle with that is that this is kind of a hack to use pianobar and I cannot figure out how to read from the Python pipe to pianobar while it is still open in order to fetch the station list.

Also, I will be adding a video screencast on YouTube shortly and will post here when it's up.

---

### Post by etnlIcarus on 2009-12-23
> **KIAaze said:**
> And again...And good luck finding an anonymous, free proxy reliable enough for streaming.

---

### Post by AndThenWhat on 2009-12-23
As promised, here is a basic screen cast of the program in action:

[http://www.youtube.com/watch?v=Jc7FzQuZY9A](http://www.youtube.com/watch?v=Jc7FzQuZY9A)

---

### Post by JimInLakeland on 2009-12-23
I'll give it a whirl.

---

### Post by VastOne on 2010-01-01
> **AndThenWhat said:**
> Hello all,

I have developed a desktop application called "Pandora Control" that is a graphical wrapper for the command line program "pianobar".  When they are coupled together they form a standalone Pandora Radio desktop app for Ubuntu.

I need people to test this deb and application and confirm they work.  

You can download the debs here:
[http://www.mediafire.com/?sharekey=e4f3285d4edb57b3d41644271fb54c6ce13f17d9de70c83ee6900953521448c9](http://www.mediafire.com/?sharekey=e4f3285d4edb57b3d41644271fb54c6ce13f17d9de70c83ee6900953521448c9)

YouTube Demonstration here: 
[http://www.youtube.com/watch?v=Jc7FzQuZY9A](http://www.youtube.com/watch?v=Jc7FzQuZY9A)

Hi

I am 64 bit and had to use -- force-architecture to run it and figured out it's dependencies (libfaad2-0 and libao2 for pianobar) but since gdebi did not install it I have no menu items.

What is the command line to start this and I can then add it

If I get it to work I will then write a step by step how to on getting it to work on 64 bit

Thanks

---

### Post by dccarson on 2010-01-06
I've just installed pianobar and pandoracontrol...very nice.

My only problem is that I get the same station regardless of which station number I enter.  It always plays station 1.

I'm using:

ii  pianobar                           2009.10.2
ii  pandoracontrol                     1.0-1

---

### Post by dccarson on 2010-01-06
> **dccarson said:**
> I've just installed pianobar and pandoracontrol...very nice.

My only problem is that I get the same station regardless of which station number I enter.  It always plays station 1.

I'm using:

ii  pianobar                           2009.10.2
ii  pandoracontrol                     1.0-1


Correction: I can choose any of my stations the first time.  However, any attempt to change the station results in the same station playing again.

---

### Post by VastOne on 2010-01-06
> **dccarson said:**
> I've just installed pianobar and pandoracontrol...very nice.

My only problem is that I get the same station regardless of which station number I enter.  It always plays station 1.

I'm using:

ii  pianobar                           2009.10.2
ii  pandoracontrol                     1.0-1

Is pianobar the command line that starts this app?

The OP asked for help on this but as you see in my above post I am having issues and have yet to hear back from him/her

Thanks

---

### Post by dccarson on 2010-01-07
> **VastOne said:**
> Is pianobar the command line that starts this app?

The OP asked for help on this but as you see in my above post I am having issues and have yet to hear back from him/her

Thanks

No, I do not need to start the pianobar command line in order to use pandoracontrol.  I only have to have it installed.

Go back in this discussion and find the YouTube link.  You can watch someone demonstrating the use of pandoracontrol to get an idea of how it works.

[Update: Just re-read your earlier post]

OK, here is the command line based on the properties of the menu item:
python /usr/bin/pandoracontrol.py

Hope that is what you need.
[/Update]

Thanks,
David

---

### Post by VastOne on 2010-01-07
> **dccarson said:**
> No, I do not need to start the pianobar command line in order to use pandoracontrol.  I only have to have it installed.

Go back in this discussion and find the YouTube link.  You can watch someone demonstrating the use of pandoracontrol to get an idea of how it works.

Thanks,
David

What I asked was if pianobar is the command line, I do not have icons or a launcher since I had to install via 64 bit architecture and for whatever reason I cannot start Pianobar.  The Youtube vid covers none of this.

If you would try to start it via command line it will at least confirm for me what is starting this app

---

### Post by VastOne on 2010-01-07
> **dccarson said:**
> No, I do not need to start the pianobar command line in order to use pandoracontrol.  I only have to have it installed.

Go back in this discussion and find the YouTube link.  You can watch someone demonstrating the use of pandoracontrol to get an idea of how it works.

[Update: Just re-read your earlier post]

OK, here is the command line based on the properties of the menu item:
python /usr/bin/pandoracontrol.py

Hope that is what you need.
[/Update]

Thanks,
David

Thanks for the confirmation

---

### Post by nutrapi on 2010-01-11
mine still crashes in browser on karmic

---

### Post by Giant Speck on 2010-01-11
It looks pretty good for it being so early in development, however, it would be nice to see what song is playing.

---

### Post by hooge1kanobi on 2010-01-14
> **dmillerw said:**
> Awesome program, some suggestions though.

Maybe have the stations listed instead of asking for the #.

Some sort of indicator of the song currently playing.

Otherwise, great program, although I think I'll use pianobar.


I'm a Newbi to Ubunto. 9.10 is my first install.  I've downloaded cuz I have the "OpenPandora" app for Windows and like the fact that I don't have to have Pandora open in a browser.

For early development It works.  However I don't know what my stations are by # and I've put several numbers in but it does not appear to be chaining stations.  So a little more tweaking is needed.  As stated in other posts.  You should be able to see the name of the station and the song playing.

Keep up the good work though!

---

### Post by HappinessNow on 2010-01-14
> **steveneddy said:**
> But Pandora runs fine in a browser.Pandora One is already awesome.

---

### Post by kmehall on 2010-01-31
Sorry to hijack the thread, but here's a Pandora app I made that uses pianobar as a library instead of accessing it through its command line interface. This means it can access song and station names, album art, etc.

[URL="http://blog.kevinmehall.net/2010/pithos"]http://blog.kevinmehall.net/2010/pithos

[IMG]http://kevinmehall.net/static/2010/pithos/pithos.300.png?uf[/IMG][/URL]

---

### Post by hooge1kanobi on 2010-03-05
Okay, I'll bite and try it.  I'm in the US but will be moving to Asia soon.  I know that Pandora does NOT work where I am going.  

As I am _new_ to Ubuntu/Linux can some one offer a step by step to go from Pianobar to Pithos?  Ub 9.10

---

### Post by sturnus on 2010-03-06
running pandoracontrol.   Nice Effort so far.  


Running the py directly, and kind of watching what is going on.  
On the changing station thing... 

Seeing this error when I work with stations (clicking the change station button in the GUI):

[?] Move song to station: 14
(i) Moving song to "Sleep To Dream Radio"... Traceback (most recent call last):
  File "./pandoracontrol.py", line 151, in on_btn_listen_clicked
    pandora.readline()
IOError: [Errno 9] Bad file descriptor
Ok.

FIX:
moving the song not what I wanted... Switch to station 14.  

  line 96... 
pandora.write("m") should be pandora.write("s")  pianobar uses s to switch stations.

(I FIXED A BUG!)  I usually just insert them...

also seeing:
./pandoracontrol.py:12: GtkWarning: Could not load image 'pandora.png'

have a pandora_small.png in the directory but no pandora.png

./pandoracontrol.py:12: GtkWarning: gtk_widget_grab_default: assertion `GTK_WIDGET_CAN_DEFAULT (widget)' failed


getting an error whenever I send a command through:  

 Traceback (most recent call last):
  File "./pandoracontrol.py", line 151, in on_btn_listen_clicked
    pandora.readline()
IOError: [Errno 9] Bad file descriptor



This is an outstanding script you have going on here.  Keep up the good work!  wish I could help with figuring out how to scrape the output...  time remaining, current song, current station and other status information would make this thing really useful.



Cheers!
Sturnus

---

