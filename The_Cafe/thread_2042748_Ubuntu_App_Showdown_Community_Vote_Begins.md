---
title: "Ubuntu App Showdown Community Vote Begins"
date: 2012-08-15
forum: The Cafe
---

### Post by s.fox on 2012-08-15
As some may be aware the [Ubuntu App Showdown]("http://developer.ubuntu.com/showdown/") recently ended, however a community prize is also going to be awarded where you all can vote.

I thought it would be nice to have a thread here to discuss the applications and competition in general.

The voting form can be found [here]("http://www.surveymonkey.com/s/P56YNQ9").

Oh I also submitted an application if anyone is interested. It is called [myshortcuts]("http://serial-coder.co.uk/blog/my-shortcuts/").  It is my first stab at application development on a gnu/linux platform and then trying to distribute it.

Screenshot:

[IMG]http://serial-coder.co.uk/blog/wp-content/uploads/2012/06/UI.png[/IMG]
Installation:

```
sudo add-apt-repository ppa:silver-fox/myshortcuts &&
sudo apt-get update; sudo apt-get install myshortcuts
```

---

### Post by kio_http on 2012-08-15
Interesting, I am a Windows developer and just moving in to Ubuntu development with python and eventually want to use qt.

What tools and languages are you using on ubuntu? That is a good first application for practice but if those shortcuts are static, I doubt it would get much votes. No offence though, you did a good job but while its great for personal use without shortcut customization its quite useless to people like me who use the KDE alternatives to all those programs.
 
If you use gtk, do you use a UI designer and link the UI to the code manually or do you have an IDE that integrates UI and coding together?

---

### Post by s.fox on 2012-08-15
> **kio_http said:**
> Interesting, I am a Windows developer and just moving in to Ubuntu development with python and eventually want to use qt.

What tools and languages are you using on ubuntu? That is a good first application for practice but if those shortcuts are static, I doubt it would get much votes. No offence though, you did a good job.

If you use gtk, do you use a UI designer and link the UI to the code manually or do you have an IDE that integrates UI and coding together?

Hi,

I built it using quickly.  All the code was written in python (not a language I have made use of a lot before) and the interface was created with glade.

You are right about the links being static, as I mentioned in the project page it is a feature I wish to implement at a later stage.   I did not enter the competition to get votes, or even win. I entered it because I like to learn and for me this involves a lot of new stuff for me learn. :-)

---

### Post by kio_http on 2012-08-15
> **s.fox said:**
> Hi,
I did not enter the competition to get votes, or even win. I entered it because I like to learn and for me this involves a lot of new stuff for me learn. :-)

Of course and in fact personally I have found this to be the best way to learn development; start small and then expand it as you learn more.

One question though, what would happen if I installed this and do not have xchat or some program installed.

About your plans to add selective shortcuts, an easy (not a good practice but good to learn) way would be to use a setting tool that asks the user to add path to executable and path to icon which could be stored in a simple txt file. Although you would have to limit the maximum number of shorcuts possible.

Start the process from a variable (string) and set that string variable by making python read the text file.

Also if you know any good python video tutorials please do point me in the right direction.

---

### Post by s.fox on 2012-08-15
> **kio_http said:**
> One question though, what would happen if I installed this and do not have xchat or some program installed.

To be honest I am not completely sure, but I think it will just not do anything if you click on the icon. It should not crash the application.

> **kio_http said:**
> 
About your plans to add selective shortcuts, an easy (not a good practice but good to learn) way would be to use a setting tool that asks the user to add path to executable and path to icon which could be stored in a simple txt file. Although you would have to limit the maximum number of shorcuts possible.

Start the process from a variable (string) and set that string variable by making python read the text file.

I was actually thinking similar myself (good to know someone else is thinking along the same lines), I was considering using XML though for the settings file.  I always intended for the number to be limited to 9 as I feel it is visually more appealing.

> **kio_http said:**
> Also if you know any good python video tutorials please do point me in the right direction.

Not any videos, no sorry but I do recommend reading [A byte of Python]("http://www.swaroopch.org/notes/Python") (it also comes as a free downloadable eBook) :)

---

### Post by madjr on 2012-08-15
learnpythonthehardway is also very good:

[http://learnpythonthehardway.org/book/index.html](http://learnpythonthehardway.org/book/index.html)

---

### Post by Baszczo on 2012-08-22
Hi. I am a participant in the Ubuntu App Showdown contest.
I have made simple music player. [Qtiko]("http://baszczewski.pl/2012/08/19/qtiko-odtwarzacz-muzyczny/").  

I think that we need another music player, because Rhytmbox or Banshe are slow and to complex. Most of users need simple tool with great design and functionality.  

Unfortunately 2-3 weeks it's not enought to prepare complete complex app. 

At the moment Qtiko have:
[LIST]
[*]fast library with filter (on tracks tab); 
[*]3 tabs to group songs: tracks, albums, artists; 
[*]functionality to download covers from Last FM 
[*]basic code for radios (not complete); 
[*]multithread code for database quries and image process - with this GUI could be very fluid - just look to albums or artist tabs;
[*]good integration with Ambiance Theme;
[/LIST]

My TO DO is more impresive:
[LIST]
[*]YouTube - support (to see/plays/download users playlists);
[*]Jamendo and Magnatude plugins (it should be simple to prepare);
[*]WEB service to download complete radios groups (I think that radios stations should be grouped) prepared by other users; 
[*]playlists functionality; 
[*]Party Mode with fancy GUI like media center; 
[*]better integration with Ubuntu;
[*]add other tabs to group music: folders 
[*]fix a lof of errors;
[/LIST]

**YOU CAN support Qtiko - just vote :)**
The voting form can be found [here]("http://www.surveymonkey.com/s/P56YNQ9").

[IMG]http://baszczewski.pl/wp-content/uploads/2012/08/qtiko_c.png[/IMG]

Installation:
```
sudo add-apt-repository ppa:baszczewski/qtiko; sudo apt-get update; sudo apt-get install qtiko
```

---

### Post by lovinglinux on 2012-08-24
> **Baszczo said:**
> My TO DO is more impresive:
[LIST]
[*]YouTube - support (to see/plays/download users playlists);
[*]Jamendo and Magnatude plugins (it should be simple to prepare);
[*]WEB service to download complete radios groups (I think that radios stations should be grouped) prepared by other users; 
[*]playlists functionality; 
[*]Party Mode with fancy GUI like media center; 
[*]better integration with Ubuntu;
[*]add other tabs to group music: folders 
[*]fix a lof of errors;
[/LIST]

My TO DO is even more:

[LIST]
[*]**Learn Python**;
[*]Port Flash-Aid from Javascript/XUL to Python/GTK;
[/LIST]

Congrats on the app btw. Looks impressive.

---

### Post by lovinglinux on 2012-08-24
> **kio_http said:**
> Also if you know any good python video tutorials please do point me in the right direction.


[http://ubuntuforums.org/showpost.php?p=1984319](http://ubuntuforums.org/showpost.php?p=1984319)


For beginners: [http://www.alan-g.me.uk/tutor/index.htm](http://www.alan-g.me.uk/tutor/index.htm)

---

### Post by Jakin on 2012-08-26
> **Baszczo said:**
> Hi. I am a participant in the Ubuntu App Showdown contest.
I have made simple music player. [Qtiko]("http://baszczewski.pl/2012/08/19/qtiko-odtwarzacz-muzyczny/"). 

Looks nice and clean, installed fine- nice how it fetches CoverArt via lastFM; however MANY of which are wrong.. its not my tags, it just guessed wrong. I can always fix my own art, though.
Wish the player had a systray indicator.

---

