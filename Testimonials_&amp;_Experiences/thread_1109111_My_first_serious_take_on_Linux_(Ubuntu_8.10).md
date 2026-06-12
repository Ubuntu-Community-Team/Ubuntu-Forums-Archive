---
title: "My first serious take on Linux (Ubuntu 8.10)"
date: 2009-03-28
forum: Testimonials &amp; Experiences
---

### Post by Zalewa on 2009-03-28
First things first:
1. English is not my native language. Excuse me all language quirks.
2. My point isn't to say "omg linux suxx0rz use windowz". I realy wanted and tried to make it work.

I also posted this on other forums (not linux related) and someone already suggested that I should try out Kaffeine instead of VLC but I'll just paste my post unchanged. Here it goes:

-
I decided to give Linux a shot, mainly because it would allow me to develop Linux port of SSB (server browser for one of the Doom ports). I decided on Ubuntu 8.10 because:
a) it's Debian based and Debian makes a really great HTTP/FTP server and also a router that serves me well,
b) it's noob-friendly.

I thought that two years of college and several more of experience made me know enough about computers to try out a different system. Hell, I managed to make Workbench for Amiga do my bidding.
What I beheld forced me to revive this thread.

I need certain things on my computer to work properly and be as easilly accessible as properly. When I install a new Windows sytem I always install such stuff first, before anything else, and make sure that it's configured correctly from the very beginning. I'll point out what I wanted my Linux system to do:

[list=1]
[*] provide me with file manager similar to Total Commander, this includes archive previewing and FTP connections (Midnight Commander is not sufficient)
[*] access to Windows' LAN neighbourhood
[*] launch Doom 
[*] launch [The Regiment game (link)]("http://www.filg.uj.edu.pl/~mikolaj/regiment/images/TS%202009-03-24%2000-06-23-95.jpg") for Windows on Wine
[*] allow me to watch .avi and .mkv movies in a player that allows to dynamicaly change subtitles delay with hotkeys. AFAIK the only player that can do that is BSPlayer for Windows
[*] Fraps
[*] allow me to edit subtitles (for example by allowing me to run SubEdit player on Wine)
[*] Skype
[*] Hamachi
[*] run Microsoft Visual C++ 2005 Express on Wine, because I need it sometimes for college and for personal purposes
[*] run Microsoft Visual C# 2008 Express on Wine, because that's my job, my money and my grades[/list]

**Ad 1. The File Manager**
This one didn't cause me big problems. There are two alternatives: Gnome-commander or Krusader. And each has something that the other one doesn't. Gnome-commander doesn't allow me to preview archive files, or even unpack them from the GUI. Krusader on the other hand doesn't allow me to store FTP connections with their usernames and passwords. Not a big deal - I just keep both apps and use Gnome-commander as FTP client. After installing Krusader it lead me through a quick and nice setup wizard and then launched without any problems. Krusader is supposed to be for KDE (default Ubuntu 8.10 installation uses Gnome) but everyone says that Krusader works on everything. Right? Almost.
This is how the program should look like: [Picture (link)]("http://elendill.files.wordpress.com/2008/09/krusader_005-large.png")
This is what happened on my system: [Another Picture (link)]("http://zalewa.dyndns.org/robert/pic/images/krusader.jpg")
WTF? I solved this problem by removing program configuration and allowing it to rebuild itself. It works correctly, for now. Although I must say that the interface is bad. For example when I start typing I want the program to focus on the command line below (right above the F2, F3, F4 buttons). It doesn't. I must click the line to type in it. That's stupid, even Midnight Commander knows how to handle keystrokes properly.
Next.

**Ad 2. Windows Neighbourhood aka Samba**
Miraculously this was working almost right of the bat. I didn't want to edit the configuration file manualy so I installed GUI through aptitude that does it for me. It allows you (but it's not required) to configure a lot more stuff than Windows does. A point for Linux.

**Ad 3. Doom (SkullTag)**
I got the Ubuntu binary, installed required dependencies and I launched the game in OpenGL mode.
The result: [Picture (link)]("http://zalewa.dyndns.org/robert/pic/images/doomBlackBox.jpg") (adnotation: this should be transparent between the bars)
I have the newest official NVidia driver installed. My graphics card is an overclocked GeForce 6600.
Next.

**Ad 4. [The Regiment (link)]("http://regiment.hopto.org/")**
So, this also worked right off the bat. At least it seemed so. But then I noticed that I can't fully rotate my character. It looks like the mouse cursor gets to the edge of the screen and gets stuck there. The solution for this is to force mouse warp, which basically means that your mouse pointer will always remain at the center of the screen. This fixed the rotation problem but now I can't navigate the menus and there's no way to toggle this option while in game.

So I found a fix for DirectInput library, recompiled Wine with this fix and launched Wine configuration program. And this is where my horror began:
[img]http://zalewa.dyndns.org/robert/pic/images/winecfg.jpg[/img]
See the fonts? They're microscopic! When I used Wine installed from aptitude they were ok, but now they're ******** UP**. I literaly spent half of the day trying to figure out why it happened and force Wine to use different font. In the end I used **Blzut3** suggestion: install Wine from aptitude and then overwrite the DirectInput library by the one I compiled myself. Seeing no other solution I decided to try it out and it worked like a charm.
Next.

**Ad 5. Watch movies**
VLC player does that. It's Linux native so all I had to do is aptitude it. But I can't change delay on subtitles dynamically so when I want to watch a movie I need perfectly aligned subtitles. As far as I know VLC player is the only movie player for Linux that's worth trying.
Next.

** Ad 6. Fraps**
Screw the movies, I want to take screenshots with PrintScreen and save them automaticaly to a preconfigured directory as .jpg files. I admit I didn't really look but from what I read there's no Fraps substitute for Linux.
Next.

** Ad 7. Subtitle editing**
The best program I know that can do that is SubEdit-player. Unfortunately the Linux version requires libraries that are now **DEPRECATED** and thus **UNAVAILABLE** which means I'm stuck with Windows version. Windows version crashed on Wine. I tried to install stuff like dotnet20 or comctl32 for Wine but this has broken Wine completely.

...
And this is when I gave up. I honestly don't want to know what happens when I try to install Visual C++ on Wine. I just don't. So don't tell me that "Linux hez it all and fook Windows"...

At least Ubuntu's installation is very easy.
And it has linuxupdate :P

-
Despite all that what I said I still would like to make it work. Any suggestions are welcome.

---

### Post by lovinglinux on 2009-03-28
> **Zalewa said:**
> [list=1]
[*] allow me to watch .avi and .mkv movies in a player that allows to dynamicaly change subtitles delay with hotkeys. AFAIK the only player that can do that is BSPlayer for Windows
[/list]

**Ad 5. Watch movies**
VLC player does that. It's Linux native so all I had to do is aptitude it. But I can't change delay on subtitles dynamically so when I want to watch a movie I need perfectly aligned subtitles. As far as I know VLC player is the only movie player for Linux that's worth trying.
Next.


VLC does allow to change subtitles delay dynamically, like several of others applications for Windows (KMPlayer, GOM Player...) and for Linux (gnome-mplayer, smplayer...). I personally like gnome-mplayer due to it's simplicity, but I guess you will like smplayer.

> **Zalewa said:**
> [list=1]
[*] Fraps
[/list]

** Ad 6. Fraps**
Screw the movies, I want to take screenshots with PrintScreen and save them automaticaly to a preconfigured directory as .jpg files. I admit I didn't really look but from what I read there's no Fraps substitute for Linux.
Next.



I don't know if there is a substitute, but you can create a simple script to dump a screenshot and probably bind it to a key.

```
import -window root /home/you/screenshot.jpg
```

> **Zalewa said:**
> [list=1]
[*] allow me to edit subtitles (for example by allowing me to run SubEdit player on Wine)
[/list]

** Ad 7. Subtitle editing**
The best program I know that can do that is SubEdit-player. Unfortunately the Linux version requires libraries that are now **DEPRECATED** and thus **UNAVAILABLE** which means I'm stuck with Windows version. Windows version crashed on Wine. I tried to install stuff like dotnet20 or comctl32 for Wine but this has broken Wine completely.


Subtitle Editor is very good. It has video preview, translation an a lot of other stuff.

```
sudo apt-get install subtitleeditor
```

> **Zalewa said:**
> [list=1]
[*] Skype
[/list]


There is a Skype version for Linux.

> **Zalewa said:**
> [list=1]
[*] Hamachi
[/list]


> Hamachi is a zero-configuration virtual private network (VPN) shareware application capable of establishing direct links between computers that are behind NAT firewalls without requiring reconfiguration (in most cases); in other words, it establishes a connection over the Internet that very closely emulates the connection that would exist if the computers were connected over a local area network. Currently available as a production version for Microsoft Windows and, as beta, for Mac OS X and Linux.

There is also a Linux version. Never used, but VPN is definitely not an issue on Linux. 

> **Zalewa said:**
> [list=1]
[*] run Microsoft Visual C++ 2005 Express on Wine, because I need it sometimes for college and for personal purposes
[*] run Microsoft Visual C# 2008 Express on Wine, because that's my job, my money and my grades[/list]


I guess you won't be able to run those on Wine, but there plenty of C# and C++ IDEs for Linux. NetBeans for example. Anyways, there is always the possibility of running Windows inside a VM like Virtualbox, which I guess would be good practice to test software under development. If something goes wrong, you crash the VM OS, not Linux.

> **Zalewa said:**
> [list=1]
[*] launch Doom 
[*] launch [The Regiment game (link)]("http://www.filg.uj.edu.pl/~mikolaj/regiment/images/TS%202009-03-24%2000-06-23-95.jpg") for Windows on Wine


It is Wine, not Windows. Not everything works as expected, some stuff can be fixed with proper configuration, others can't. Can't comment about the applications you are trying to run tho.

---

### Post by betrunkenaffe on 2009-03-28
Do you need jpg for the screenshots? It does png by default, mostly because it's compressed high quality image. I always get a window asking for name (and location to save the image) when I screenshot. All I've ever had to do was hit printscreen. It's better than Windows because you need to paste into paint and then save it.

Never used Fraps.

May I suggest you not waste further time? You just want a Windows clone, I heard there is a project to do that online. I don't know the name of it.

---

### Post by lykwydchykyn on 2009-03-28
If you really want to make it work for you, why not take some time to find some native tools and explore their capabilities instead expecting to (a) run windows apps on a totally different OS or (b) find exact 1:1 clones. 

Not sure what is up with Krusader, since I run KDE and I've never tried running it in GNOME.  Konqueror is a pretty powerful file manager in its own right, and can do dual pane, network filesystems, and so forth.  Maybe you should give KDE a shot.  Even so, it's not going to do exactly everything your old software did.

---

### Post by jdrodrig on 2009-03-29
Clone of Windows online? mm... Do you mean Ajax Windows?

---

### Post by Tamlynmac on 2009-03-29
Might I suggest that the OP use the appropriate help sections to elicit assistance. By assisting individuals that circumvent the help sections, what impression are we conveying to those that do?

If we're going supporting this behavior, why have the help sections? :-k

---

### Post by howlingmadhowie on 2009-03-29
> **Zalewa said:**
> First things first:

2. My point isn't to say "omg linux suxx0rz use windowz". I realy wanted and tried to make it work.


it sounds to me more like you're looking for a windows clone. you can do all the things you mentioned on ubuntu with very little effort, but you have to learn how. that's where the help section comes in.

one question, how long had you been using a computer before you started doing all these things on windows? do you really expect to be able to apply the same methodology to complete the same tasks on ubuntu?

forget much you must, my young padawan ...

---

### Post by binbash on 2009-03-29
6 - wink
7- gnome subtitles

---

### Post by brayden13 on 2009-03-29
Everybody think of this before you post. "DO NOT FEED THE TROLLS" This guy made one post and never logged in again. It is obvious he is a troll trying to piss off a few people and get some cheap laughs out of it. If this guy was having real legitimate problems then he is pretty much underestimating Ubuntu.

Linux is not Windows, it is everything that windows is not.

---

### Post by Zalewa on 2009-03-29
I decided to try some things out. 
For example I went with suggestion given to me previously and tried out Kaffeine for movies. Kaffeine is great.

@lovinglinux
Thank you. You've been realy helpful. I'm still wondering if there's a subtitle editor that allows me to open, convert and save subtiltes in these formats:

```

[][]
{}{}

and

00:00:01
00:00:02

```

About Skype and Hamachi: I suspected that Linux ports exist. I just didn't get past point 7 of my list.
About Microsoft IDE's: ok, just forget about that...

@THR4SH
> thers a ton of crap for screen recordin. u can use gtkrecordmydesktop/istanbul/xvidcap. xvidcap records directly to avi files like fraps.
The thing is I don't even care that much about recording movies. I just want to run fullscreen OpenGL game (or DirectX game on Wine) and be able to dump a screenshot with single key and no additional "where do you want to save" windows.

@betrunkenaffe
> Do you need jpg for the screenshots?
Yes. JPG files are a) smaller and b) I have a script on my server that allows me to upload .zip file full of JPG files through WWW site. Then the script produces thumbnails and displays everything on site. The exactly same script is used here:
[http://regiment.hopto.org](http://regiment.hopto.org)

---

### Post by lykwydchykyn on 2009-03-29
> **Zalewa said:**
> 

The thing is I don't even care that much about recording movies. I just want to run fullscreen OpenGL game (or DirectX game on Wine) and be able to dump a screenshot with single key and no additional "where do you want to save" windows.


You can do this by installing "scrot" and binding it to a hotkey.

For instance:
```

scrot ’%Y-%m-%d_$wx$h.jpg’ -e ’mv $f ~/shots/’

```
Would create a jpg file named after the year, month, day, and dimensions of the screenshot, then move it to the shots directory in your home directory.

---

### Post by solwic on 2009-03-29
> **lykwydchykyn said:**
> ...instead [of] expecting to (a) run windows apps on a totally different OS....


Yeah, 'cause why would we want to make the transition easier for new users?  Pfft.  They can figure it out on their own or hit the bricks.  

Silly Windows people....

[*Sarcasm*]("http://en.wikipedia.org/wiki/Sarcasm")

:biggrin:

---

### Post by lykwydchykyn on 2009-03-29
> **jrock612 said:**
> Yeah, 'cause why would we want to make the transition easier for new users?  Pfft.  They can figure it out on their own or hit the bricks.  

Silly Windows people....

[*Sarcasm*]("http://en.wikipedia.org/wiki/Sarcasm")

:biggrin:

I'm offering advice to help this guy use linux successfully.  If the first thing you do is try to make it run apps that don't natively run on Linux, you'll get frustrated and fail to use it.

It has nothing to do with whether or not Wine ought to work.  It, quite frankly, *doesn't* nine times out of ten.  Sorry, much respect to Wine devs, but that's just how it is.

The OP says he *wants* to use Linux and use it well.  It's unrealistic to expect it to run programs not designed for it.  If you want to be successful at learning it, learn programs designed for it.

---

### Post by solwic on 2009-03-29
> **lykwydchykyn said:**
> I'm offering advice to help this guy use linux successfully.  If the first thing you do is try to make it run apps that don't natively run on Linux, you'll get frustrated and fail to use it.

It has nothing to do with whether or not Wine ought to work.  It, quite frankly, *doesn't* nine times out of ten.  Sorry, much respect to Wine devs, but that's just how it is.

The OP says he *wants* to use Linux and use it well.  It's unrealistic to expect it to run programs not designed for it.  If you want to be successful at learning it, learn programs designed for it.

And I repeat:  [Sarcasm.]("http://en.wikipedia.org/wiki/Sarcasm")

Chill, not every comment that doesn't absolutely agree with one you made is an attack against you.  Besides, I agree with you: native Linux software will always run better on Linux, and if you want to fully experience Linux, learn the programs written for it.

But realistically, much of the Linux/Ubuntu user base are Windows converts, and so it only makes sense to do as much as possible to make the transition easier.  We don't have to pander to them, but we ought to at least *try* to make them feel at home.  Elitism is only good if you count yourself amongst the elite.

But hey, to each his own.  I just wonder how much better Wine would be if Shuttleworth put his money behind it, like he supposedly did with Gnome.  

Just sayin'....

---

### Post by lykwydchykyn on 2009-03-29
> **jrock612 said:**
> And I repeat:  [Sarcasm.]("http://en.wikipedia.org/wiki/Sarcasm")

Chill, not every comment that doesn't absolutely agree with one you made is an attack against you.  Besides, I agree with you: native Linux software will always run better on Linux, and if you want to fully experience Linux, learn the programs written for it.

The trouble with sarcasm is you never know which way it's cutting.  Especially when the tone of the post is already obviously sarcastic.  Then I don't know if you're being sarcastic about being sarcastic, or just reinforcing the sarcastic tone of the original post.  Or, if your reference to sarcasm is intended itself to be sarcastic, meaning you're really serious.  

I am, by definition, almost always chill.  I just like explaining myself.  It's what I do.

---

### Post by solwic on 2009-03-29
> **lykwydchykyn said:**
> 
I am, by definition, almost always chill.  I just like explaining myself.  It's what I do.

Fair enough.  :biggrin:

---

### Post by Tamlynmac on 2009-03-29
jrock612 being sarcastic, be still. I can't hardly believe that - there goes his image.
:lolflag:

---

### Post by solwic on 2009-03-30
> **Tamlynmac said:**
> jrock612 being sarcastic, be still. I can't hardly believe that - there goes his image.
:lolflag:

I'm just full of these little surprises....

:biggrin:

---

### Post by Cybie257 on 2009-03-30
> **brayden13 said:**
> Everybody think of this before you post. "DO NOT FEED THE TROLLS" This guy made one post and never logged in again. It is obvious he is a troll trying to piss off a few people and get some cheap laughs out of it. If this guy was having real legitimate problems then he is pretty much underestimating Ubuntu.

Linux is not Windows, it is everything that windows is not.

Who's the TROLL?? Never logged in again? Come on, one day, even two, will never constitute 'Never'. In addition, the post following your accusation was from the OP. Patience. not all of us sit at our computer and hit refresh every few minutes to check for replies. 

Sorry, just felt I should express the disappointment in posting such accusations. 

-Cybie

---

