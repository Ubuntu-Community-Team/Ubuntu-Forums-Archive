---
title: "Install Ubuntu server with GUI?"
date: 2008-07-06
forum: Server Platforms
---

### Post by Ameoba on 2008-07-06
Hi,
Could someone please let me know how to install ubuntu server with a gui? I've given it a try, yet i think i did something wrong as when the gui loads, my screen can't display the resolution (does linux not have a low default res?) and when i go to the cosole, the screen does not scroll down to follow my inputs. 

If someone has a start to finish install method. i'd like to start over and get this right.

---

### Post by Dr Small on 2008-07-06
Servers were designed to run and be built without a GUI. If you wanted a GUI, you should just install the default Ubuntu CD, as it comes with everything needed and you don't have to set it all up.

---

### Post by ixus_123 on 2008-07-06
when doesn't the GUI load?

Are you talking about during the actual install as I had this issue when insalling to an old iBook and had to adjust the xorg config.

However, if you have installed, you should only be getting a text prompt.

To install a minimal gui you could

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

```
sudo apt-get install gdm xorg xterm icewm menu gksu synaptic
```

```
sudo dpkg-reconfigure xserver-xorg
```

```
/etc/init.d/gdm start
```

---

### Post by Ameoba on 2008-07-06
Right,
So you're telling me that to run a game server... I should use the desktop version. 

Not having a GUI makes it much harder to manage servers. I know it makes it slower to have a GUI, but i'm sure a basic GUI wouldn't add that much to it. Certanly worth it when you think about the increased ability to manage and setup the server.

EDIT - I'll give that method a try and let you know if it worked.
       (I was writing this post when you posted)

---

### Post by steveneddy on 2008-07-06
These

**xterm icewm**

are lightweight window managers

or you could install the regular Gnome desktop

```
sudo apt-get install ubuntu-desktop
```

---

### Post by hyper_ch on 2008-07-06
> **Ameoba said:**
> So you're telling me that to run a game server... I should use the desktop version.
Server version without gui

> **Ameoba said:**
> Not having a GUI makes it much harder to manage servers.
Not really, you're just unfamiliar with it

> **Ameoba said:**
> I know it makes it slower to have a GUI, but i'm sure a basic GUI wouldn't add that much to it.
Did you measure it?

> **Ameoba said:**
> Certanly worth it when you think about the increased ability to manage and setup the server.
Not really

---

### Post by Ameoba on 2008-07-06
After following your instructions i get the following:

> *Starting GNOME Display Manager...       [fail]

Any suggestions as to why this failed?

---

### Post by steveneddy on 2008-07-06
> **Ameoba said:**
> After following your instructions i get the following:



Any suggestions as to why this failed?

Whose instructions are you referring?

---

### Post by Ameoba on 2008-07-06
ixus_123's

---

### Post by Dr Small on 2008-07-06
If you want something lightweight then, install xorg, xterm and openbox.

---

### Post by simon_ives on 2008-07-06
> **Ameoba said:**
> Right,
So you're telling me that to run a game server... I should use the desktop version. 

Not having a GUI makes it much harder to manage servers. I know it makes it slower to have a GUI, but i'm sure a basic GUI wouldn't add that much to it. Certanly worth it when you think about the increased ability to manage and setup the server.

EDIT - I'll give that method a try and let you know if it worked.
       (I was writing this post when you posted)

Why not just install Ubuntu server as is and install webmin to manage it via a networked workstation?  If you have to run x apps on the server you can always x-forward them to your workstation over ssh too (assuming you installed x).

---

### Post by Ameoba on 2008-07-06
Ok lets get this sorted out. I'm wanting to run a couple of small LAN game servers. They run in windows allowing me to see live info of each one. From a comand line interface you can't get that kind of data presented on the screen. 

I don't want to have to run 2 computers in order to use 1! The only type of remote admin that i like for general remote use is RDP (i havn't used linux enough to know an equivilant) as it gives me the option of remote admin while my desktop isn't doing anything and while my desktop is busy i can use the server normaly anyway. 

I would like to install and interface onto server. but currently all the intructions people have offered that i've found (not just this thread) havn't worked! and because i havn't studied a text book on the operation of linux, and there is no usefull error messages, i don't know what is going on.

I'll be trying the desktop version now that should hopefully install without any issues. But if someone does have a method of installing an interface that is proven, i'd love to try it.

---

### Post by windependence on 2008-07-06
> **Ameoba said:**
> Right,
So you're telling me that to run a game server... I should use the desktop version. 

Not having a GUI makes it much harder to manage servers. I know it makes it slower to have a GUI, but i'm sure a basic GUI wouldn't add that much to it. Certanly worth it when you think about the increased ability to manage and setup the server.

EDIT - I'll give that method a try and let you know if it worked.
       (I was writing this post when you posted)

I'm curious, when you say you are going to run a gaming server, what is it exactly you are going to be running? I was under the impression that most games ran on Windows, except for the Doom, Quake and other ports unless you run cedega. How will you be setting this up?

-Tim

---

### Post by Ameoba on 2008-07-06
Battlefield 2, QUAKE III, CS1.6, Battlefield 1942. For a small LAN with friends (about 13-20 users)

BF will only run in windows, but they do have a linux server which i imagine works exactly like the windows dedicated server, but on linux. They basically have a window where you set the game settings, then once running they have a windows displying current game status, score, map, number of players etc. as well as the log which includs chats and game events.

---

### Post by windependence on 2008-07-06
Interesting.... I learned something today. :)

You should really follow dr_small's advice and learn more command line though. There is no need for you to run a GUI on this thing.

-Tim

---

### Post by simon_ives on 2008-07-07
> **Ameoba said:**
> I don't want to have to run 2 computers in order to use 1! The only type of remote admin that i like for general remote use is RDP (i havn't used linux enough to know an equivilant) as it gives me the option of remote admin while my desktop isn't doing anything and while my desktop is busy i can use the server normaly anyway.

With x forwarding you can perform many linux 'equivalents' of Remote Desktop Protocol on your server.  Even nautilus can browse your server and any x apps will display on your workstation.

When you say '...I can use the server normally anyway' do you mean that you want to have a keyboard, mouse and monitor attached to the server so that x apps will display on the server?  If so then you will definitely need an x environment installed.  For a server you'd best use [Xfce]("http://www.xfce.org/") which is the default in [Xubuntu]("http://www.xubuntu.org/").

---

### Post by hyper_ch on 2008-07-07
> **Ameoba said:**
> Ok lets get this sorted out. I'm wanting to run a couple of small LAN game servers. They run in windows allowing me to see live info of each one. From a comand line interface you can't get that kind of data presented on the screen.

what kind of data can't?

---

### Post by Ameoba on 2008-07-07
Multitasking. you can't be monitoring the stats of one system while making a change or even monitoring the stats of 2 systems at once.

---

### Post by hyper_ch on 2008-07-07
> **Ameoba said:**
> Multitasking. you can't be monitoring the stats of one system while making a change or even monitoring the stats of 2 systems at once.

sure you can

---

### Post by windependence on 2008-07-07
> **Ameoba said:**
> Multitasking. you can't be monitoring the stats of one system while making a change or even monitoring the stats of 2 systems at once.

What you can't open two or ten ssh windows at once?

-Tim

---

### Post by hyper_ch on 2008-07-07
> **windependence said:**
> What you can't open two or ten ssh windows at once?

-Tim

or preferrably use "screen" ^^

---

### Post by rijalul on 2008-07-07
Is there any ubuntu server guide-book in depth?

Thx before... :)

---

### Post by Ameoba on 2008-07-07
> **windependence said:**
> What you can't open two or ten ssh windows at once?

-Tim
Yeah, but not on the same screen. I like having lots of info infront of me and not having to switch consoles all the time. Thats why my vista box has dual screens

---

### Post by Vivaldi Gloria on 2008-07-07
> **Ameoba said:**
> I've given it a try, yet i think i did something wrong as when the gui loads, my screen can't display the resolution (does linux not have a low default res?) and when i go to the cosole, the screen does not scroll down to follow my inputs. 

How did you install the gui? What gui?

> **Ameoba said:**
> If someone has a start to finish install method. i'd like to start over and get this right.

Installing the full ubuntu desktop on ubuntu server is as simple as

```
sudo apt-get install ubuntu-desktop
```

But if this is what you want then you can use the desktop cd as well. You can install a lighter desktop on a server install: 

> **Dr Small said:**
> If you want something lightweight then, install xorg, xterm and openbox.

I suggest you look at urukrama's page (he's also a member here):

[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

---

### Post by Vivaldi Gloria on 2008-07-07
> **rijalul said:**
> Is there any ubuntu server guide-book in depth?

Thx before... :)

Start here:

[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

Continue with various documents at

[http://tldp.org/](http://tldp.org/)

Especially look at the guides.

---

### Post by Vivaldi Gloria on 2008-07-07
> **Ameoba said:**
> Yeah, but not on the same screen. I like having lots of info infront of me and not having to switch consoles all the time. Thats why my vista box has dual screens

Pal, you can do whatever you like with the terminal. You're just not familiar with it. If you don't have time to get familiar (or you don't want to) then install the full ubuntu desktop (or the desktop cd) and get it over with.

---

### Post by hyper_ch on 2008-07-07
> **Ameoba said:**
> Yeah, but not on the same screen. I like having lots of info infront of me and not having to switch consoles all the time. Thats why my vista box has dual screens

telling it again: "screen"

---

### Post by Vivaldi Gloria on 2008-07-07
> **hyper_ch said:**
> telling it again: "screen"

Some links about screen:

[http://www.gnu.org/software/screen/](http://www.gnu.org/software/screen/)
[http://en.wikipedia.org/wiki/GNU_Screen](http://en.wikipedia.org/wiki/GNU_Screen)
[http://www.kuro5hin.org/story/2004/3/9/16838/14935](http://www.kuro5hin.org/story/2004/3/9/16838/14935)
[http://aperiodic.net/screen/quick_reference](http://aperiodic.net/screen/quick_reference)

---

### Post by windependence on 2008-07-07
> **hyper_ch said:**
> telling it again: "screen"

Or PuTTY on a Windoze box. As many sessions as you want. I am never at my actual consoles unless I am installing the OS.

-Tim

---

### Post by hyper_ch on 2008-07-07
windependence:

I guess you don't get quite the concept of "screen"

---

### Post by windependence on 2008-07-07
> **hyper_ch said:**
> windependence:

I guess you don't get quite the concept of "screen"

I know what it is, and it's supposed to be cool and all but honestly, I just open terminals on my Macbook Pro and I'm fine. I can have 6 or 8 of them on the screen at one time. 

Tell me more about screen and why it's better.

-Tim

---

### Post by Vivaldi Gloria on 2008-07-07
> **windependence said:**
> I know what it is, and it's supposed to be cool and all but honestly, I just open terminals on my Macbook Pro and I'm fine. I can have 6 or 8 of them on the screen at one time. 

Tell me more about screen and why it's better.

-Tim

We are talking about when you have no gui. How are you going to "open terminals" then?

Besides there are more reasons why screen is useful. You can start a remote screen session, close that computer, and then continue with that session somewhere else. 

Read more about it.

---

### Post by hyper_ch on 2008-07-07
(1) you can have multiple virtual terminals open in one terminal --> easy switching without using the mouse

(2) you can disconnect from the virtual terminal and resume later at the same point where you did disconnect - with all your virtual terminals open in the state where you disconnected --> basically do some work on computer a, disconnect with ^a-d, go to computer b, resume with screen -r and you are at the same point where you left on computer a...

(3) the disconnection from the session is especially nice if you let game servers run ;) you don't need to have them run in the "background" but within a screen session and you can watch the log output on the screen in realtime ;)

---

### Post by windependence on 2008-07-07
Yep, just read a tutorial. Looks good, especially if I am stuck at a co-lo.

Thank guys, I'll give it a try.

-Tim

---

### Post by jmirick on 2008-07-17
I have to say I don't understand why everybody objects so to managing a server with a GUI.  I have 35 years of various console and command-line experience on all kinds of stuff, and maybe I'm just lazy or old but I fail to see why people were chapping this guy so much over this.  I've wanted to install a simplified server without Open Office and all that stuff but has Gnome, I'll try some of the suggestions above "when I have some time".

Maybe if you have a server that is running at 98% you can't stand ANY wasted effort in the box but short of that it seems that this is almost a religious position, not an ease-of-use one.

I have several Ubuntu servers running the standard desktop OS (some of whose defaults are granted not optimal for a server) but they're up, and lightning hasn't struck yet.  And I would also note that if you want to convert system managers who are used to managing Win servers through a GUI, you will need to give them a GUI or they'll badmouth it, and that's not what we need.

---

### Post by odysseusjak on 2008-07-17
I completely agree with jmirick, on this one.  I've been doing this a while in the Windows world and I'm not very familiar with the terminal.  This type of 'anti-GUI' on the server is like the 80s all over again.  "Graphical User Interface?  Who needs it!  We have DOS!"  People today are all about graphics.  If a small business needs to have a small file/print server it needs to be easily managed.  Giving them a book of commands is not very helpful.  They (I) want to be able to just open up a 'Control Panel' and work with printers or folder sharing or users/groups.  Heck, even Mac OS X Server uses a lot of OpenSource apps within GUIs.  It just makes sense to move in that direction.

I think there should be an option when you install Ubuntu Server to install a GUI for basic admin/configuration stuff.  I think it would go over very well with the home office/small office crowd and those of us who support them.

---

### Post by Vivaldi Gloria on 2008-07-17
> ... if you want to convert system managers who are used to managing Win servers through a GUI, you will need to give them a GUI or they'll badmouth it, and that's not what we need.

Why should we care if they badmouth it or not? Most servers are run on *nix anyway. If they are too stupid to grasp why then I hope they stay away from *nix. 


> I think there should be an option when you install Ubuntu Server to install a GUI for basic admin/configuration stuff. I think it would go over very well with the home office/small office crowd and those of us who support them.

You are talking like if it is not possible to run a gui on a server system or run a server program on a desktop system. Both are possible and very easy to do. Why bother having such an option during boot? What you guys miss are 99.9 percent of all servers are administered remotely. Maybe by ssh, may be by a gui like webmin. But there's no point in including a gui in a server cd just as there is no point in putting apache in a default desktop installation. You want it then go on and install it. But don't expect things to be changed for that 0.01 percent.

---

### Post by Titan8990 on 2008-07-17
I don't know which disk you all are installing from but I just used the "Alternate CD". I selected the option for "Install a Server" which installed the Ubuntu server kernel. After it installed the server kernel ubuntu-desktop was one of my package options to choose from. 

I personally only use the GUI for web browsing as I do a lot of research for learning the server. 100% of my server administration is done via the terminal.

When it comes time for my server to go in to production the GUI will get uninstalled.

---

### Post by windependence on 2008-07-17
Once my OS is installed, I rack the server and I don't use the console again unless I HAVE to, which usually means something is hosed. This deosn't happen often.

To the people who say the terminal is so 80s, they don't have a clue as to how to administer a REAL server. They also don't have any idea just how powerful and fast the terminal can be because they have been using a junk OS all their lives where the GUI CANNOT be separated from the terminal. We are raising a generation of lazy people who don't want to learn. Pointy clicky is the thing that is "80s", not the terminal.

Here is what Ubuntu has to say about there being no GUI on the SERVER os:

[SIZE="3"]**No X server by design**[/SIZE]

By design, Ubuntu Server Edition does not include an X server. This is a deliberate choice as we believe that most servers should be serviced remotely, are safer without the addition of code that needs direct communication from user space to hardware, and should not be used as a desktop by their administrator.

    [I]"So I applaud the Ubuntu team’s common sense (and courage) in keeping the X Window System out of the default installation of Ubuntu Server."
    --Mick Bauer in April 2008 Linux Journal - "Security Features in Ubuntu Server" [/I]

[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security)

Now just why do you think Ubuntu would make that statement if the terminal was so "80s"?

-Tim

---

### Post by odysseusjak on 2008-07-17
No reason for hostility, windependence.  I was just stating it from my view and most of my customers.  But you're right, most of the time, we just turn it on and leave it alone.  However, on the rare occasion that we need to do something on it, it would be NICE to do so through a GUI and not the command line.  Some people are more comfortable with a GUI.  That is the 'choice' they like and people shouldn't be bashed if they want to go that route.  The thread started by asking how to install a GUI on the server and most of the posts have been 'why?' followed by some trying to dissuade the user from choosing to do things his/her way.  If you and the server team like doing it that way, that's cool.  But don't make others feel bad or question their (our) skills for wanting a GUI.

---

### Post by hyper_ch on 2008-07-17
> **odysseusjak said:**
> If you and the server team like doing it that way, that's cool.  But don't make others feel bad or question their (our) skills for wanting a GUI.

Maybe they don't know any better because they can't imagine to run any computer without gui so it is also our task to show them all possibilities ;)

---

### Post by q.dinar on 2008-07-17
hello.
i say a little offtopic and i've read only 4th page yet.

what i do not like in terminal.

sometimes i run some commands that i remember and it gives its result to screen but i cannot scroll it, i do not know how to scroll, it is in pure terminal, it is when i lost normal gui i have to come here.

if i want to do something for example to see a file or directory content or copy a file or make or remove file or directory and others and i do not remember commands for them i do not know how to know out that commands. then i know that i can run mc if it is installed.

it is very hard to type long filenames and what i do if there are some symbols that are not in keyboard? i do not know now.

---

### Post by Vivaldi Gloria on 2008-07-17
> **q.dinar said:**
> sometimes i run some commands that i remember and it gives its result to screen but i cannot scroll it,

Pipe it through less:

```
command | less
```


> if i want to do something for example to see a file or directory content or copy a file or make or remove file or directory and others and i do not remember commands for them i do not know how to know out that commands. then i know that i can run mc if it is installed.

If you use it frequently then you'll remember. Read the guides at tldp.org to learn more about the terminal.


> it is very hard to type long filenames and what i do if there are some symbols that are not in keyboard? i do not know now.

Press tab key and the shell will complete the names.

---

### Post by odysseusjak on 2008-07-17
> **hyper_ch said:**
> Maybe they don't know any better because they can't imagine to run any computer without gui so it is also our task to show them all possibilities ;)

I get that.  But no one is 'show[ing] them all possibilities' by bashing people who want to use a different means.  The person asked how to install a GUI -- not how to do stuff from the terminal.  If they want to learn terminal commands, then the best way to find out is ask them, not make them feel inferior or resort to name-calling.  What if they don't want to imagine running a computer from the terminal?  Perhaps they want a gui?  Is that such a bad thing?  We should be fine with that and not look down upon them for that decision.

---

### Post by Vivaldi Gloria on 2008-07-17
> **odysseusjak said:**
> I get that.  But no one is 'show[ing] them all possibilities' by bashing people who want to use a different means.  The person asked how to install a GUI -- not how to do stuff from the terminal.

If you read this thread carefully you'll see that op was given instructions for gui installation a few times.

>  If they want to learn terminal commands, then the best way to find out is ask them, not make them feel inferior or resort to name-calling.  What if they don't want to imagine running a computer from the terminal?  Perhaps they want a gui?  Is that such a bad thing?  We should be fine with that and not look down upon them for that decision.

When did anybody look down on somebody? I don't see it.

---

### Post by odysseusjak on 2008-07-17
Vivaldi, I know that people have instructed the op about how to install the GUI.  I wasn't referring to them.  I was referring to the people who automatically start telling the op about using the terminal instead.  That was not what was asked.  That type of response in not very helpful.

Concerning 'looking down' upon someone: That is the typical feeling I get from reading posts about putting a gui on a server.  It seems that terminal users are quick to question the technical skills of people who prefer a gui.  This thread is a perfect example.  There have been five pages of bantering about using something that the op didn't ask about using.  People calling other people 'stupid' doesn't help matters.

---

### Post by hyper_ch on 2008-07-17
> **q.dinar said:**
> sometimes i run some commands that i remember and it gives its result to screen but i cannot scroll it, i do not know how to scroll, it is in pure terminal, it is when i lost normal gui i have to come here.
You enter scroll mode with ctrl+a and exit it by pressing twice esc.

> **odysseusjak said:**
> The person asked how to install a GUI -- not how to do stuff from the terminal.
> **odysseusjak said:**
> Vivaldi, I know that people have instructed the op about how to install the GUI.  I wasn't referring to them.  I was referring to the people who automatically start telling the op about using the terminal instead.  That was not what was asked.  That type of response in not very helpful.
Because that's what he used to and doesn't know any better way... go in the street and ask people about Linux... most have maybe heard of it... so if you think Linux is a better approach at computing then it's the same with telling them that CLI is a better approach at server management.

---

### Post by windependence on 2008-07-17
> **odysseusjak said:**
> No reason for hostility, windependence.  I was just stating it from my view and most of my customers.  But you're right, most of the time, we just turn it on and leave it alone.  However, on the rare occasion that we need to do something on it, it would be NICE to do so through a GUI and not the command line.  Some people are more comfortable with a GUI.  That is the 'choice' they like and people shouldn't be bashed if they want to go that route.  The thread started by asking how to install a GUI on the server and most of the posts have been 'why?' followed by some trying to dissuade the user from choosing to do things his/her way.  If you and the server team like doing it that way, that's cool.  But don't make others feel bad or question their (our) skills for wanting a GUI.

No hostility intended.

You may have noticed, however, this is the "server" forum. "Servers" are not normally managed in a GUI environment, <except> on Windoze. Does this make the Windoze way the best way? Of course not. If the GUI indeed WAS a better way to administer the sever, why would Ubuntu make the statement they do in their marketing materials. Think about it. 

Clearly, if you want to use the GUI for things that is your choice, but then IMHO you should be using the version that has the GUI pre-installed, NOT the server version where a GUI was never INTENDED to be installed. It's like saying I want a glass of chocolate milk and then asking someone to filter out the chocolate.

If I made anyone feel like I was questioning their admin skills I am sorry. I WAS questioning their command line skills because if you are skilled at the command line you would realize the full potential of it and we would not be having this discussion. 

Linux != Windoze. There are those of us who do NOT want Linux to EVER be Windoze especially on the server side. On the desktop many of us will be very happy with a nice GUI, myself included, BUT certainly not on the server. I picked Ubuntu server precisely because it does not all that crap by default. 

Finally, you probably don't know that I was in your shoes just a few years ago. I had a friend who was a sysadmin who used to make fun of me all the time about me wanting to use a GUI for everything. I made all the arguments you use and more, but still, it wasn't until I had a major server crash that of course killed the GUI. I was lost. I called my friend and googled until I got the server back on line, but from that day on I swore no GUI for me, and you know what? After I got so far in to it, I began to just "get it" that the CLI is faster, more powerful, and much more relaible than any GUI or even web interface. It's just a crutch for server admins. Real admins use the CLI, even in Windows. I know, because I work with companies that have thousands of servers all over the world. Try accessing the GUI on a server in Greece from the USA with any kind of speed or usability and you would soon see what I mean.

I will say one more thing. I will personally help ANYONE on this board who wants to learn the CLI, night or day, 24/7/365. It's that important. 

-Tim

---

### Post by Titan8990 on 2008-07-17
Well said Tim.

---

### Post by windependence on 2008-07-17
> **Titan8990 said:**
> Well said Tim.

Thanks. I really DO want to help these guys become good at the CLI. They will be GREAT admins with that knowledge.

-Tim

---

### Post by /etc/init.d/ on 2008-07-18
I have a 366MHz server with 128MB RAM.  It's headless, i.e. no monitor, mouse or keyboard, and doesn't have any X Server or GUI. 

I can SSH in, see a split screen view of everything I need to see (with screen), switch between as many screens as I want instantly (again with screen).  I can install, update and configure services.  I can transfer files to/from the server over SSH.

I can do everything I need to do.  A GUI would require so much memory, it would make the machine unusable.  If it's harder to administrate a service through the CLI than it is with the GUI, it's because the designers have built a broken piece of software.

---

### Post by q.dinar on 2008-07-18
thanks.

i think it would be  good if pressing F1 in cli i get help: like this: 1. general file operations, 2. ftp commands, 3. viewing/editing files, 4. comparing/synchronising files and directories, .... press the number of help category then if i press 1 there are: 1. cp - to copy files 2. ls - to to see directory content 3. rmdir - to remove directories 4. ... - to make new files 5. ... - to rename ....

or this help should be accessible with "help" command. i have just tried it there is something other: not the basic and general commands. there is a link to "info bash" but that is also not that: it is big and starts with syntax, not basic commands, i listed it long but have not reached to basic commands.

---

### Post by q.dinar on 2008-07-18
i have posted this to "brainstorm": [http://brainstorm.ubuntu.com/idea/11274/](http://brainstorm.ubuntu.com/idea/11274/)

---

### Post by hyper_ch on 2008-07-18
google for "FOSS ubuntu cheat sheet" and "FOSS command line cheat sheet". Print them out (or save them or learn them by heart) ;)

---

### Post by Titan8990 on 2008-07-18
Man pages are the "help" for bash. After a week or so of solid command line use you will really get used to your basic commands such as mkdir, ls, less, cat, etc. 

If you are ever thinking "How does this command work?" then man pages are the way to go. They are not exactly easy to read but that is something that you will get used to.

Example: You are thinking "How do I grep a directory?"

You type:

$man grep

and you will see that -r flag will grep a directory. IMO internet is great and everything but I tend to learn better from a book. You may want to consider that.

Also, there is simple help for many commands. If I wanted to know arguements I can pass to rsync:

```
**root@einstein:/scripts# rsync --help**
rsync  version 2.6.9  protocol version 29
Copyright (C) 1996-2006 by Andrew Tridgell, Wayne Davison, and others.
<http://rsync.samba.org/>
Capabilities: 64-bit files, socketpairs, hard links, symlinks,
              batchfiles, inplace, IPv6, ACLs,
              64-bit system inums, 64-bit internal inums

rsync comes with ABSOLUTELY NO WARRANTY.  This is free software, and you
are welcome to redistribute it under certain conditions.  See the GNU
General Public Licence for details.

rsync is a file transfer program capable of efficient remote update
via a fast differencing algorithm.

Usage: rsync [OPTION]... SRC [SRC]... DEST
  or   rsync [OPTION]... SRC [SRC]... [USER@]HOST:DEST
  or   rsync [OPTION]... SRC [SRC]... [USER@]HOST::DEST
  or   rsync [OPTION]... SRC [SRC]... rsync://[USER@]HOST[:PORT]/DEST
  or   rsync [OPTION]... [USER@]HOST:SRC [DEST]
  or   rsync [OPTION]... [USER@]HOST::SRC [DEST]
  or   rsync [OPTION]... rsync://[USER@]HOST[:PORT]/SRC [DEST]
The ':' usages connect via remote shell, while '::' & 'rsync://' usages connect
to an rsync daemon, and require SRC or DEST to start with a module name.

Options
 -v, --verbose               increase verbosity
 -q, --quiet                 suppress non-error messages
     --no-motd               suppress daemon-mode MOTD (see manpage caveat)
 -c, --checksum              skip based on checksum, not mod-time & size
 -a, --archive               archive mode; same as -rlptgoD (no -H, -A)
     --no-OPTION             turn off an implied OPTION (e.g. --no-D)
 -r, --recursive             recurse into directories
 -R, --relative              use relative path names
     --no-implied-dirs       don't send implied dirs with --relative
 -b, --backup                make backups (see --suffix & --backup-dir)
     --backup-dir=DIR        make backups into hierarchy based in DIR
     --suffix=SUFFIX         set backup suffix (default ~ w/o --backup-dir)
 -u, --update                skip files that are newer on the receiver
     --inplace               update destination files in-place (SEE MAN PAGE)
     --append                append data onto shorter files
 -d, --dirs                  transfer directories without recursing
 -l, --links                 copy symlinks as symlinks
 -L, --copy-links            transform symlink into referent file/dir
     --copy-unsafe-links     only "unsafe" symlinks are transformed
     --safe-links            ignore symlinks that point outside the source tree
 -k, --copy-dirlinks         transform symlink to a dir into referent dir
 -K, --keep-dirlinks         treat symlinked dir on receiver as dir
 -H, --hard-links            preserve hard links
 -p, --perms                 preserve permissions
 -E, --executability         preserve the file's executability
     --chmod=CHMOD           affect file and/or directory permissions
 -A, --acls                  preserve ACLs (implies --perms)
 -o, --owner                 preserve owner (super-user only)
 -g, --group                 preserve group
     --devices               preserve device files (super-user only)
     --specials              preserve special files
 -D                          same as --devices --specials
 -t, --times                 preserve times
 -O, --omit-dir-times        omit directories when preserving times
     --super                 receiver attempts super-user activities
 -S, --sparse                handle sparse files efficiently
 -n, --dry-run               show what would have been transferred
 -W, --whole-file            copy files whole (without rsync algorithm)
 -x, --one-file-system       don't cross filesystem boundaries
 -B, --block-size=SIZE       force a fixed checksum block-size
 -e, --rsh=COMMAND           specify the remote shell to use
     --rsync-path=PROGRAM    specify the rsync to run on the remote machine
     --existing              skip creating new files on receiver
     --ignore-existing       skip updating files that already exist on receiver
     --remove-source-files   sender removes synchronized files (non-dirs)
     --del                   an alias for --delete-during
     --delete                delete extraneous files from destination dirs
     --delete-before         receiver deletes before transfer (default)
     --delete-during         receiver deletes during transfer, not before
     --delete-after          receiver deletes after transfer, not before
     --delete-excluded       also delete excluded files from destination dirs
     --ignore-errors         delete even if there are I/O errors
     --force                 force deletion of directories even if not empty
     --max-delete=NUM        don't delete more than NUM files
     --max-size=SIZE         don't transfer any file larger than SIZE
     --min-size=SIZE         don't transfer any file smaller than SIZE
     --partial               keep partially transferred files
     --partial-dir=DIR       put a partially transferred file into DIR
     --delay-updates         put all updated files into place at transfer's end
 -m, --prune-empty-dirs      prune empty directory chains from the file-list
     --numeric-ids           don't map uid/gid values by user/group name
     --timeout=TIME          set I/O timeout in seconds
 -I, --ignore-times          don't skip files that match in size and mod-time
     --size-only             skip files that match in size
     --modify-window=NUM     compare mod-times with reduced accuracy
 -T, --temp-dir=DIR          create temporary files in directory DIR
 -y, --fuzzy                 find similar file for basis if no dest file
     --compare-dest=DIR      also compare destination files relative to DIR
     --copy-dest=DIR         ... and include copies of unchanged files
     --link-dest=DIR         hardlink to files in DIR when unchanged
 -z, --compress              compress file data during the transfer
     --compress-level=NUM    explicitly set compression level
 -C, --cvs-exclude           auto-ignore files the same way CVS does
 -f, --filter=RULE           add a file-filtering RULE
 -F                          same as --filter='dir-merge /.rsync-filter'
                             repeated: --filter='- .rsync-filter'
     --exclude=PATTERN       exclude files matching PATTERN
     --exclude-from=FILE     read exclude patterns from FILE
     --include=PATTERN       don't exclude files matching PATTERN
     --include-from=FILE     read include patterns from FILE
     --files-from=FILE       read list of source-file names from FILE
 -0, --from0                 all *-from/filter files are delimited by 0s
     --address=ADDRESS       bind address for outgoing socket to daemon
     --port=PORT             specify double-colon alternate port number
     --sockopts=OPTIONS      specify custom TCP options
     --blocking-io           use blocking I/O for the remote shell
     --stats                 give some file-transfer stats
 -8, --8-bit-output          leave high-bit chars unescaped in output
 -h, --human-readable        output numbers in a human-readable format
     --progress              show progress during transfer
 -P                          same as --partial --progress
 -i, --itemize-changes       output a change-summary for all updates
     --out-format=FORMAT     output updates using the specified FORMAT
     --log-file=FILE         log what we're doing to the specified FILE
     --log-file-format=FMT   log updates using the specified FMT
     --password-file=FILE    read password from FILE
     --list-only             list the files instead of copying them
     --bwlimit=KBPS          limit I/O bandwidth; KBytes per second
     --write-batch=FILE      write a batched update to FILE
     --only-write-batch=FILE like --write-batch but w/o updating destination
     --read-batch=FILE       read a batched update from FILE
     --protocol=NUM          force an older protocol version to be used
 -4, --ipv4                  prefer IPv4
 -6, --ipv6                  prefer IPv6
     --version               print version number
(-h) --help                  show this help (-h works with no other options)

Use "rsync --daemon --help" to see the daemon-mode command-line options.
Please see the rsync(1) and rsyncd.conf(5) man pages for full documentation.
See [http://rsync.samba.org/](http://rsync.samba.org/) for updates, bug reports, and answers
```


If I wanted examples and better descriptions I would:

$man rsync

Edit: Last resort:

Post for help on the Ubuntu forums. There are plenty of people willing to help.

---

### Post by jmirick on 2008-07-18
> Why should we care if they badmouth it or not? Most servers are run on *nix anyway. If they are too stupid to grasp why then I hope they stay away from *nix.

That's why Linux has such an uphill battle against Windows, just that attitude.  I don't have an ideological position on it, if some people want a GUI-ed server, let them have it.  Companies won't train people any more, MS tells them that the GUI makes it "easier" and "error free" and "minimal training costs" and management, who knows GUI-on-their-desktop, buys it, and presto -- an order for 500 Win servers.  Then a bunch of people are thereby convinced that Linux is too complex to be useful.

---

### Post by hyper_ch on 2008-07-18
> **jmirick said:**
> That's why Linux has such an uphill battle against Windows, just that attitude.  I don't have an ideological position on it, if some people want a GUI-ed server, let them have it.  Companies won't train people any more, MS tells them that the GUI makes it "easier" and "error free" and "minimal training costs" and management, who knows GUI-on-their-desktop, buys it, and presto -- an order for 500 Win servers.  Then a bunch of people are thereby convinced that Linux is too complex to be useful.

you're missing the super cool new powershell in VISTA or the newere M$ servers which makes administration so much easier...

I daresay even M$ has recognized that servers really don't need a gui ;)

---

### Post by Vivaldi Gloria on 2008-07-18
> **jmirick said:**
> That's why Linux has such an uphill battle against Windows, just that attitude. 

I remember that there are more *nix servers out there than win servers. I don't remember where I read this so I'd be glad if anybody can give a source. So I don't see an uphill struggle. *nix is ahead.

>  I don't have an ideological position on it, if some people want a GUI-ed server, let them have it.  

Who says that they cannot have it? They have the freedom to have whatever they want.

>  Companies won't train people any more, MS tells them that the GUI makes it "easier" and "error free" and "minimal training costs" and management, who knows GUI-on-their-desktop, buys it, and presto -- an order for 500 Win servers.  Then a bunch of people are thereby convinced that Linux is too complex to be useful.

CLI is simple! Not guis! That's why MS has come up with poweshell. That's why people deploy win2008 servers without guis. 

I think you are confusing desktop systems vs server systems. I have a server in a server farm in some other part of the world. What is the point of a gui when you are not sitting in front of that computer? My desktop has a gui and I can use that desktop to administer the server. Do you think that there is a user sitting in front of each server in a server farm? 

Let me repeat again. Servers exist to be administered remotely. So what is the point of having a gui in a server? It will only make the server bloated, nothing else.

---

### Post by frenz on 2008-07-19
i learned a lot of this thread thanks :)

i experience using desktop server its very slow to response so i switch to server edition running with vmware server then its fast now im using [putty]("http://www.chiark.greenend.org.uk/~sgtatham/putty/") to manage server its easy to use you can copy paste text & i use [webmin]("http://www.webmin.com/") to easily manage server

---

### Post by windependence on 2008-07-19
> **jmirick said:**
> That's why Linux has such an uphill battle against Windows, just that attitude.  I don't have an ideological position on it, if some people want a GUI-ed server, let them have it.  Companies won't train people any more, MS tells them that the GUI makes it "easier" and "error free" and "minimal training costs" and management, who knows GUI-on-their-desktop, buys it, and presto -- an order for 500 Win servers.  Then a bunch of people are thereby convinced that Linux is too complex to be useful.

You're missing the point here. We don't WANT Linux dumbed down like that. Then, when everything starts crashing from too much bloatware, M$ gets to say Linux sucks. Some of us just get it. If you have been working in an M$ world all your life, it is a totally different paradigm. You have to think differently.

That's another thing, with Linux and virtualization, you probably won't need 500 servers. Server farms are basically a Windoze invention so that when one crashes no one notices. Mickey$oft LOVES all those software licenses.

-Tim

---

### Post by jmirick on 2008-07-22
> You're missing the point here.

With all respect, I think you are missing my point.  I'm not saying that all servers should be GUI-ed, I'm saying that there are situations where a GUI would be useful.  For example, a sysadmin who is running around supporting several branch offices, each with local shared files, a VPN, a mail server, FTP, and Lord knows what else.  He has many desktops, maybe a Win server with a GUI on it, and -- oops -- a Linux box or two, with only command line?  Really, not so hot.  Will he be good at all that and command line too?  Probably not, in the real world.

Would I think it's appropriate to be managing 50 or 100 remote servers via a GUI?  No, of course not.

Now I don't consider this "dumbed down," just for that person, more convenient.  Now you might say that if he can't master this, he shouldn't be running a server on the open Internet, and maybe that's true, but it's reality.  In this case, he's more likely to "do it right" with a GUI to help him.

And PowerShell is kind of cute, how MS packages it as "a new and advanced function" and implies it's their invention.  Oh well, they didn't get where they are in the world by not shading the truth from time to time!

---

### Post by windependence on 2008-07-22
There are tons of "web tools" for this kind of thing. no need to log into the box unless there is a problem, and you would know it using something like Nagios, Big Brother, Cacti, etc.

-Tim

---

### Post by Titan8990 on 2008-07-22
> With all respect, I think you are missing my point. I'm not saying that all servers should be GUI-ed, I'm saying that there are situations where a GUI would be useful. For example, a sysadmin who is running around supporting several branch offices, each with local shared files, a VPN, a mail server, FTP, and Lord knows what else. He has many desktops, maybe a Win server with a GUI on it, and -- oops -- a Linux box or two, with only command line? Really, not so hot. Will he be good at all that and command line too? Probably not, in the real world.

Would I think it's appropriate to be managing 50 or 100 remote servers via a GUI? No, of course not.

Now I don't consider this "dumbed down," just for that person, more convenient. Now you might say that if he can't master this, he shouldn't be running a server on the open Internet, and maybe that's true, but it's reality. In this case, he's more likely to "do it right" with a GUI to help him.

And PowerShell is kind of cute, how MS packages it as "a new and advanced function" and implies it's their invention. Oh well, they didn't get where they are in the world by not shading the truth from time to time!

So we need to add GUIs so Windows admins can administer Linux server without learning how to use Linux properly? And they are going to do it right?

---

### Post by Seaker on 2008-08-06
> **Titan8990 said:**
> I don't know which disk you all are installing from but I just used the "Alternate CD". I selected the option for "Install a Server" which installed the Ubuntu server kernel. After it installed the server kernel ubuntu-desktop was one of my package options to choose from. 

I personally only use the GUI for web browsing as I do a lot of research for learning the server. 100% of my server administration is done via the terminal.

When it comes time for my server to go in to production the GUI will get uninstalled.

Maybe I'm just a dense newbie, but I tried to reproduce this trick. I have tried every install path that I can find with the 8.04.1 alternate install AMD64 CD and cannot find the options that you mention.  Would you mind telling me how you got to the options for Install a Server and where you could choose the ubuntu-desktop as an option?  

Even the option install mode of "Install an LTSP server" looks like all the other installs save it does talk of DHCP.  But I have not found anything that tells me the kernel is different.  'uname -a' and 'cat /etc/lsb-lease' give exactly the same results as my Ubuntu desktop.  So, it appears that everything was installed on a desktop kernel.  (Though I could be looking in the wrong place to tell me the kernel is different.  And if so, any corrections would be appreciated.)

Thanks!

---

### Post by Titan8990 on 2008-08-06
I had the 32bit 7.10 version. That is probably the difference. Still, apt-get install ubuntu-desktop is not a tough task.

---

### Post by windependence on 2008-08-07
> **Seaker said:**
> Maybe I'm just a dense newbie, but I tried to reproduce this trick. I have tried every install path that I can find with the 8.04.1 alternate install AMD64 CD and cannot find the options that you mention.  Would you mind telling me how you got to the options for Install a Server and where you could choose the ubuntu-desktop as an option?  

Even the option install mode of "Install an LTSP server" looks like all the other installs save it does talk of DHCP.  But I have not found anything that tells me the kernel is different.  'uname -a' and 'cat /etc/lsb-lease' give exactly the same results as my Ubuntu desktop.  So, it appears that everything was installed on a desktop kernel.  (Though I could be looking in the wrong place to tell me the kernel is different.  And if so, any corrections would be appreciated.)

Thanks!

The kernel in Server is definitely different. 

[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel)

I'm not sure what you are asking here. Do you want to know how to install a desktop on the server kernel?

-Tim

---

### Post by Seaker on 2008-08-07
I was just trying Titan8990's trick to see if I would have an easy way of having a crutch when doing the install.  I'll go ahead and do what was suggested at the beginning of this thread and use: ```
sudo apt-get install ubuntu-desktop
```
The idea was to use the GUI crutch to help check and tweak a server to be what I want it to be.  While I realize the CLI is more powerful and often there are things that can only be done through the CLI, I find that the GUI gives a alternative view that allows one to see more of what can be done and what other options that there are that I need to consider.  That in turn helps me know what to look for when digging through the man pages to figure out how to use the CLI.

---

### Post by trash on 2008-08-23
> **Vivaldi Gloria said:**
> Why should we care if they badmouth it or not? Most servers are run on *nix anyway. If they are too stupid to grasp why then I hope they stay away from *nix. 
You are talking like if it is not possible to run a gui on a server system or run a server program on a desktop system. Both are possible and very easy to do. Why bother having such an option during boot? What you guys miss are 99.9 percent of all servers are administered remotely. Maybe by ssh, may be by a gui like webmin. But there's no point in including a gui in a server cd just as there is no point in putting apache in a default desktop installation. You want it then go on and install it. But don't expect things to be changed for that 0.01 percent.

Dude, you so sound like you are thinking of linux only in terms of the past.. Up until a few years ago the linux home user was a MUCH SMALLER % than it is today. More computers under one roof than ever before and that translates to way more potential servers than you are willing to admit.... Don't expect things to change.... HUH? WHY NOT! It's rediculous not to expect change... and just as a side note I work for a few people who own/run home business who would benefit from a server but they sure as he** don't have time to learn any commandline LOL.
I'm all for server gui option, he** there's room on the cd for it!

---

### Post by windependence on 2008-08-23
That's where you come in as a consultant. Most small businesses do not admin their own servers, I know, i am a consultant to many of them. :)

You can make it easy for them as far as things like e-mail using something like Zimbra with a nice web GUI for things like adding users, etc, but bare metal administration is normally done by an outside consultant like myself on an hourly basis or on a service contract.

You need to get out of that Windoze mindset and actually try the CLI for a while. I think you'll find out after you get over the initial fear, it's much faster than anything GUI for administration. A GUI is just a front end for the commands anyway and adds a layer of overhead, complexity, and security threats. Linux installs are already bloated IMHO. It was refreshing to see a distro offer a lean and mean approach. Do you really want a default install to take as much disk and RAM as Windoze Vista?

-Tim

---

### Post by hyper_ch on 2008-08-23
> **trash said:**
> HUH? WHY NOT! It's rediculous not to expect change... and just as a side note I work for a few people who own/run home business who would benefit from a server but they sure as he** don't have time to learn any commandline LOL.
I'm all for server gui option, he** there's room on the cd for it!

let's recapitulate things:

First computers server were Unix.... CLI only...
The sometime Apple and Microsoft made it on the desktop market...
Microsoft also entered server markets - they had the dogma to run GUI...
At some time, not all too long ago, M$ announced the "new" powershell for servers...

Hmmm, if GUI on a server is really that superior why does M$ who has preached GUI and GUI-only for years, suddenly introduce a powershell...

In my opinion it seems that there's not really a benefit running a gui on a server... at least not if you are serious about operating a computer as a server...

---

### Post by trash on 2008-08-23
"Microsoft Windows PowerShell command line shell and scripting language helps IT professionals achieve greater control and productivity."

We are not talking about server professionals, we are talking about home users who have lives outside of computers.

I'm not saying Gui's are better, i'm not saying use only Gui's, it's about choice and comfort zone and if it can be done why not.

---

### Post by hyper_ch on 2008-08-23
> **trash said:**
> "Microsoft Windows PowerShell command line shell and scripting language helps IT professionals achieve greater control and productivity."
And so it does also for non-IT professionals

> **trash said:**
> We are not talking about server professionals, we are talking about home users who have lives outside of computers.
So, everything realted to "professionals" shouldn't be used by "home" users?

> **trash said:**
> I'm not saying Gui's are better, i'm not saying use only Gui's, it's about choice and comfort zone and if it can be done why not.
And I'm talking about a paradigm shift at Microsoft to have introduced the powershell because it has an edge over gui... even more so on linux where you have no registry but config files.

---

### Post by trash on 2008-08-23
> **hyper_ch said:**
> And so it does also for non-IT professionals

So, everything realted to "professionals" shouldn't be used by "home" users?

Sure if they have time/desire for the learning curve, but as already seen here in this thread not all do.

---

### Post by windependence on 2008-08-23
> **trash said:**
> "Microsoft Windows PowerShell command line shell and scripting language helps IT professionals achieve greater control and productivity."

We are not talking about server professionals, we are talking about home users who have lives outside of computers.

I'm not saying Gui's are better, i'm not saying use only Gui's, it's about choice and comfort zone and if it can be done why not.

Remember - you are in the SERVER forum, and the topic is about SERVERS not home power users. You can't make any argument that will convince us because we have been there, done that, and got the T-shirt. GUIs only slow you down when you know what you are doing and they keep you from REALLY learning what is happening on your machine. A GUI is nothing more than a front end for the CLI anyway so why not bypass the middle man and get to it? All configuration files in Linux are just easy to read plain text files. No voodoo, just understandable text. What is hard about that? You can't remember the commands? No problem, we have man and appropos for that, right from the command line without ever leaving your seat.

Still not convinced? Give us some more "reasons" and we'll give you the "reasons" to use the CLI instead - on a SERVER.

-Tim

---

### Post by trash on 2008-08-23
> **windependence said:**
> Remember - you are in the SERVER forum, and the topic is about SERVERS not home power users. You can't make any argument that will convince us because we have been there, done that, and got the T-shirt. GUIs only slow you down when you know what you are doing and they keep you from REALLY learning what is happening on your machine. A GUI is nothing more than a front end for the CLI anyway so why not bypass the middle man and get to it? All configuration files in Linux are just easy to read plain text files. No voodoo, just understandable text. What is hard about that? You can't remember the commands? No problem, we have man and appropos for that, right from the command line without ever leaving your seat.

Still not convinced? Give us some more "reasons" and we'll give you the "reasons" to use the CLI instead - on a SERVER.

-Tim

LOL, the forum is Server Platforms which to me could include gui servers:lolflag: CUPS is an example no?

---

### Post by windependence on 2008-08-23
CUPS (Common Unix Printing System) does not even need X to run. It also has a web interface that runs on port 631 so you don't even need X if you want a visual interface. The only "server" that has anything to do with a GUI is an X server or VNC server.

C'mon, you know you are splitting hairs here. If you wanna load a GUI, run desktop. I'll post this again. Here is what Canonical says about GUI on the server:

> **[COLOR="Sienna"]No X server by design[/COLOR]**

By design, Ubuntu Server Edition does not include an X server. This is a deliberate choice as we believe that **[COLOR="Red"]most servers should be serviced remotely, are safer without the addition of code that needs direct communication from user space to hardware, and should not be used as a desktop by their administrator[/COLOR]**.

    "So I applaud the Ubuntu team&#8217;s common sense (and courage) in keeping the X Window System out of the default installation of Ubuntu Server."
    --Mick Bauer in April 2008 Linux Journal - "Security Features in Ubuntu Server" 

[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security)

Emphasis is mine of course but you get the idea. So you think Canonical is wrong?

---

### Post by mikey5555 on 2008-08-23
Amoeba, 
I installed the Ubuntu Desktop ewith the3 following command :  **sudo apt-get install ubuntu-desktop**.  Only one command, but you will be asked for the "superuser" password, usually your password, if you're logged in using the account created during installation.  
Hope this helps....

Regards...

mikey5555

---

### Post by windependence on 2008-08-23
Mikey, I think he's probably installed it by now, that was over a month ago. people keep dredging up this thread from the dead. I'm sure he appreciates your effort though. :)

-Tim

---

### Post by mikey5555 on 2008-08-23
> **windependence said:**
> Mikey, I think he's probably installed it by now, that was over a month ago. people keep dredging up this thread from the dead. I'm sure he appreciates your effort though. :)

-Tim

OOPS.... I did not realize this thread was that old...

Regards...

mikey5555

---

### Post by trash on 2008-08-23
> **windependence said:**
> CUPS (Common Unix Printing System) does not even need X to run. It also has a web interface that runs on port 631 so you don't even need X if you want a visual interface. The only "server" that has anything to do with a GUI is an X server or VNC server.

C'mon, you know you are splitting hairs here. If you wanna load a GUI, run desktop. I'll post this again. Here is what Canonical says about GUI on the server:



[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security)

Emphasis is mine of course but you get the idea. So you think Canonical is wrong?

Nobody is trying to change the default install, simply an option.
Anyhow, the thread keeps getting dredged up because people do searches for server gui.

---

### Post by redmk2 on 2008-08-23
@windependence

I'm curious, what do you consider a "server"?  Is it hardware/software?  Is it the server in "client/server"?  Other than memory management and user permissions, and the GUI, what is the differences between Ubuntu Desktop and Server editions?

---

### Post by trash on 2008-08-24
> **hyper_ch said:**
> And so it does also for non-IT professionals


So, everything realted to "professionals" shouldn't be used by "home" users?


And I'm talking about a paradigm shift at Microsoft to have introduced the powershell because it has an edge over gui... even more so on linux where you have no registry but config files.

You forgot to mention but I saw it posted in this forum that Microsoft also came out with a Home server which clearly illustrates a difference between the needs of a professional and the needs of a home user.

I've also seen security raised as an issue but quite frankly the more gui servers running out there, the more likely these issues will get fixed a lot faster than if we just keep saying no to gui's.

---

### Post by Titan8990 on 2008-08-24
> You forgot to mention but I saw it posted in this forum that Microsoft also came out with a Home server which clearly illustrates a difference between the needs of a professional and the needs of a home user.

I've also seen security raised as an issue but quite frankly the more gui servers running out there, the more likely these issues will get fixed a lot faster than if we just keep saying no to gui's.

So what you are saying that we can fix a problems faster by causing more problems?

---

### Post by trash on 2008-08-24
> **Titan8990 said:**
> So what you are saying that we can fix a problems faster by causing more problems?

Hey if you want to look at it like that sure, but I think this happens with just about every big/new feature anyway so i'm not sure what the big deal is.

---

### Post by wirepuller134 on 2008-08-24
For a single home server, such as Microsofts I could see the benefit of a GUI.  For a set up like ours it would be hectic to say the least.  We have always ran our servers headless, not for security but for the convenience.  The kvm switches and cables would be a nightmare, not including the added heat from the monitors, the added cost of hardware, and the cost of electricity to run the extra hardware.

---

### Post by windependence on 2008-08-25
> **redmk2 said:**
> @windependence

I'm curious, what do you consider a "server"?  Is it hardware/software?  Is it the server in "client/server"?  Other than memory management and user permissions, and the GUI, what is the differences between Ubuntu Desktop and Server editions?

I have a feeling you are splitting hairs here to try and support your position on a GUI on a server. Yes, there are large differences between the server edition and the desktop version. Here are some major ones just in the kernel alone:

> Here is a list of the server-specific kernel optimisations that we include:

    *

      The Server Edition uses the Deadline I/O scheduler instead of the CFQ scheduler used by the Desktop Edition.
    *

      Pre-emption is turned off in the Server Edition.
    *

      The timer interrupt is 100 Hz in the Server Edition and 250 Hz in the Desktop Edition.
    *

      The Server Edition is optimised for i686 processors while the Desktop Edition is optimised for both the i586 and i686.
    *

      Virtualization is better supported in the Server Edition through the enabling of IPC namespaces.
    *

      Multiple routing tables for the IPv6 protocol are also supported in the Server Edition.
    *

      For 32-bit systems the Server Edition is configured to use PAE which allows addressing up to 64GB of memory while the Desktop Edition is configured for 4GB.
    *

      When running a 64-bit version of Ubuntu on 64-bit processors you are not limited by memory addressing space.





[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel)

You should read this to educate yourself:

[http://www.ubuntu.com/products/whatisubuntu/serveredition](http://www.ubuntu.com/products/whatisubuntu/serveredition)

Especially read the security section where they talk about not having a GUI.

You should also know that I work for a large company that is mostly Micro$oft and we have to secure it with THREE layers of routers, firewalls, and switches. It's a nightmare.

-Tim

---

### Post by mikey5555 on 2008-08-31
Hello all, 
I know I will probably kick up a "crap storm" for what follows.  I'm gonna say it anyway.  

I wanted to use UBUNTU Server till I visited this forum and asked ONE simple question about using a GUI in an UBUNTU Server installation.  After a short answer, telling me I did not need a GUI, I started reading more of this Thread.  My thoughts follow.

I've read all I can stand in this absurd thread!  It's attitudes like the ones presented in this Thread that sent me and my company to CentOS 5 - an "unlabeled" distro of RedHat Enterprise Linux SERVER, complete with GUI - STANDARD - no questions, no belittlement, no hassles - use it or not, **your choice**.

So, if you're tired of being treated  like a pariah for asking for a GUI in your server platform OS, then leave these elitist attitudes to those who seem to think they know best for all people and find a product whose preponents are willing to help with **your** questions, not belittle you for asking questions that the "*professionals*" of this forum are very willing and, apparently, anxious to do!!!

UBUNTU *did* build the server platform without GUI support pre-installed.  You **can** install one if you wish, contrary to the "*prevailing opinions*" of these "*self-acclaimed professionals*".  

I decided the crap slinging and belittlement of users evidenced here by "*supporters*" of UBUNTU in this forum, was NOT worth of my tolerance.  I went elsewhere for my server product - CentOS. 

I am an *avid* supporter and user of UBUNTU desktop - I have more than 10 or 12 systems running UBUNTU 7.1 16 and 64 bit and 8.04 32 and 64 bit OS, in my business.  If I needed any assistance with these systems, I always found it in the forums - given freely and proudly by the members thereof.  I recommend UBUNTU to every PC user I know (and that's quite a lot - I run a PC Service and Repair company) who is frustrated or dis-satisfied with any MS product, and has no apps they cannot find or duplicate in UBUNTU.  

Bottom line:
I saw only a very small number of the "Replies" to the original question **"Install Ubuntu server with GUI?"**, that actually offered any useful advice or help about the selection and installation of a GUI.  the rest were aimed at telling the asker (and anyone else willing to listen) that they, in essence, know what is **correct and proper** for a server interface and that those not in agreement with their exalted opinion were were not *worthy* of an actual answer to their original question. 

If this is what passes for UBUNTU Server "Community Support" here..... well.... glad I elected to use a different server OS.  At least I am not belittled for asking a "dumb-***" question in their forums - just treated like a 'newb" and pointed to the answer I asked for, along with any advice that might be **relevant** to or a "**better alternative**" than my original question or request.

Keep this sort of attitude and many potential users of the UBUNTU Server platform will move on to more friendly and/or helpful alternatives.

Just my $.02..... so flame away, if you feel so inclined.......

Regards...

mikey5555

---

### Post by brad8266 on 2008-08-31
> **windependence said:**
> That's where you come in as a consultant. Most small businesses do not admin their own servers, I know, i am a consultant to many of them. :)

I am also a consultant and I have some clients that already have been running Windows Server 2003 and all they do is file sharing, lol. Thye were surprised when I told them they could have saved the many thousands of $$ with Linux. They spent lots of $$ on windows and they couldnt afford the exchange server so they everyone in that office uses the email from their ISP for email. Linux server could have done all of that and more and all tnhey had to pay for was my companys labor time.

Yes almost all small businesses hire consultants to do admin because they cant afford full time admin nor is it practical for them.

---

### Post by trash on 2008-08-31
Well after trying a few times to install a desktop over the server install i gave up, no end of trouble doing that!

I found some other things that HELPED a great deal...

installing webmin for one(though this does require remote accessing)

tools that helped on the server itself both available thought apt-get:
links - browser
gpm - which enables your mouse (making 'simple' tasks like copy/paste easy)

for the print server i wanted i installed:
CUPS - though it was still a pain in the a$$ to setup but links browser fixed it in the end via [http://localhost:631](http://localhost:631). lord know why this should still be so complicated though??

Strangely enough CUPS didn't install when i did the server install selecting print server which is kinda what i expected since thats what Ubuntu uses.
I'm guessing now, that it is time for a completely seperate server project, one that is geared for home users rather than admin server professionals.

---

### Post by brad8266 on 2008-08-31
> **mikey5555 said:**
> Hello all, 
I know I will probably kick up a "crap storm" for what follows.  I'm gonna say it anyway.  

I wanted to use UBUNTU Server till I visited this forum and asked ONE simple question about using a GUI in an UBUNTU Server installation.  After a short answer, telling me I did not need a GUI, I started reading more of this Thread.  My thoughts follow.

I've read all I can stand in this absurd thread!  It's attitudes like the ones presented in this Thread that sent me and my company to CentOS 5 - an "unlabeled" distro of RedHat Enterprise Linux SERVER, complete with GUI - STANDARD - no questions, no belittlement, no hassles - use it or not, **your choice**.

So, if you're tired of being treated  like a pariah for asking for a GUI in your server platform OS, then leave these elitist attitudes to those who seem to think they know best for all people and find a product whose preponents are willing to help with **your** questions, not belittle you for asking questions that the "*professionals*" of this forum are very willing and, apparently, anxious to do!!!

UBUNTU *did* build the server platform without GUI support pre-installed.  You **can** install one if you wish, contrary to the "*prevailing opinions*" of these "*self-acclaimed professionals*".  

I decided the crap slinging and belittlement of users evidenced here by "*supporters*" of UBUNTU in this forum, was NOT worth of my tolerance.  I went elsewhere for my server product - CentOS. 

I am an *avid* supporter and user of UBUNTU desktop - I have more than 10 or 12 systems running UBUNTU 7.1 16 and 64 bit and 8.04 32 and 64 bit OS, in my business.  If I needed any assistance with these systems, I always found it in the forums - given freely and proudly by the members thereof.  I recommend UBUNTU to every PC user I know (and that's quite a lot - I run a PC Service and Repair company) who is frustrated or dis-satisfied with any MS product, and has no apps they cannot find or duplicate in UBUNTU.  

Bottom line:
I saw only a very small number of the "Replies" to the original question **"Install Ubuntu server with GUI?"**, that actually offered any useful advice or help about the selection and installation of a GUI.  the rest were aimed at telling the asker (and anyone else willing to listen) that they, in essence, know what is **correct and proper** for a server interface and that those not in agreement with their exalted opinion were were not *worthy* of an actual answer to their original question. 

If this is what passes for UBUNTU Server "Community Support" here..... well.... glad I elected to use a different server OS.  At least I am not belittled for asking a "dumb-***" question in their forums - just treated like a 'newb" and pointed to the answer I asked for, along with any advice that might be **relevant** to or a "**better alternative**" than my original question or request.

Keep this sort of attitude and many potential users of the UBUNTU Server platform will move on to more friendly and/or helpful alternatives.

Just my $.02..... so flame away, if you feel so inclined.......

Regards...

mikey5555


I agree any name calling or belittlement is uncalled for and only aids in driving people away from the product they are trying to support. 

I myself have been using linux for a few years and am familiar with the CLI but when it came to the server I tried it with and without the GUI and I like using the server with no GUI and remote administration using Webmin for the basic file/print services. Most small businesses only use file/print serving and I can easily administer their server remotely.

The server without the GUI was a lot faster then running the GUI. The difference was very noticeable.

---

### Post by brad8266 on 2008-08-31
> **trash said:**
> Well after trying a few times to install a desktop over the server install i gave up, no end of trouble doing that!



 You are probably missing a step. I am fairly new the the ubuntu server side and I found it very simple to install the desktop. I am very familiar with the Linux CLI though.

sudo aptitude update
sudo aptitude upgrade
sudo aptitude install ubuntu-desktop

You need to have a working connection to the internet also because you will be fetching files.

I did uninstall the desktop because it does run better without the GUI, as a matter of fact I really didnt even use the desktop GUI for server admin anyway. Most of my work was done using webmin for an easy to use remote graphical admin tool and putty for CLI. Once I uninstalled the desktop my memory usage went way down as well.

---

### Post by Vivaldi Gloria on 2008-08-31
> **mikey5555 said:**
> Hello all, 
I know I will probably kick up a "crap storm" for what follows.  I'm gonna say it anyway.  

Hello mate. There is nothing like a good discussion. If only we were having beers at the same time... ;)

> I wanted to use UBUNTU Server till I visited this forum and asked ONE simple question about using a GUI in an UBUNTU Server installation.  After a short answer, telling me I did not need a GUI, I started reading more of this Thread.  My thoughts follow.

I've read all I can stand in this absurd thread!  It's attitudes like the ones presented in this Thread that sent me and my company to CentOS 5 - an "unlabeled" distro of RedHat Enterprise Linux SERVER, complete with GUI - STANDARD - no questions, no belittlement, no hassles - use it or not, **your choice**.

Good job on choosing centos. I also like it. During the installation centos asks what to install and yes, you can install a desktop environment of your choice. But note that when you only tick "server" it doesn't include a desktop. Also don't forget that centos iso is kind of ubuntu desktop and server versions combined. 

> So, if you're tired of being treated  like a pariah for asking for a GUI in your server platform OS, then leave these elitist attitudes to those who seem to think they know best for all people and find a product whose preponents are willing to help with **your** questions, not belittle you for asking questions that the "*professionals*" of this forum are very willing and, apparently, anxious to do!!!

I'm also a member of centos forums and my attitude is same in both forums. I don't think I know best for all people but I think I know what is best for most people. And that's to use servers without desktop environments. Why? Because you can admin a server remotely with a gui if you want. No DE overhead. No added security risk. More stable. Most importantly familiarizing yourself with the server will save a lot of headaches later on.

> UBUNTU *did* build the server platform without GUI support pre-installed.  You **can** install one if you wish, contrary to the "*prevailing opinions*" of these "*self-acclaimed professionals*".  

No body said that you cannot install. We said you shouldn't. There is a difference.

>  I decided the crap slinging and belittlement of users evidenced here by "*supporters*" of UBUNTU in this forum, was NOT worth of my tolerance.  I went elsewhere for my server product - CentOS. 

Different OSes may have different features and security measures. For example ubuntu does not let root login. It's even forbidden in this forum to tell users how to do it. Why? Read the FAQ here:

[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

Similarly, it is not good advice to tell ubuntu users install a DE on their servers without mentioning the risks and overhead. 

>  I am an *avid* supporter and user of UBUNTU desktop - I have more than 10 or 12 systems running UBUNTU 7.1 16 and 64 bit and 8.04 32 and 64 bit OS, in my business.  If I needed any assistance with these systems, I always found it in the forums - given freely and proudly by the members thereof.  I recommend UBUNTU to every PC user I know (and that's quite a lot - I run a PC Service and Repair company) who is frustrated or dis-satisfied with any MS product, and has no apps they cannot find or duplicate in UBUNTU.  

Agreed.

> Bottom line:
I saw only a very small number of the "Replies" to the original question **"Install Ubuntu server with GUI?"**, that actually offered any useful advice or help about the selection and installation of a GUI. 

Small number? Why is not one enough? You install it by

```
sudo apt-get install ubuntu-desktop
```

How many different ways do we need to tell it?

>  the rest were aimed at telling the asker (and anyone else willing to listen) that they, in essence, know what is **correct and proper** for a server interface and that those not in agreement with their exalted opinion were were not *worthy* of an actual answer to their original question. 

Yes, the thread turned into a discussion of guis. So what? If you want you can ignore all the latter posts.

We may have said something of the sorts "correct and proper" but I don't agree with the rest of your sentence.

> If this is what passes for UBUNTU Server "Community Support" here..... well.... glad I elected to use a different server OS.  

Well, different OS communities may push for different user habits. This doesn't necessarily make them crap. Actually guis are not popular in the centos server as well. 

> At least I am not belittled for asking a "dumb-***" question in their forums - just treated like a 'newb" and pointed to the answer I asked for, along with any advice that might be **relevant** to or a "**better alternative**" than my original question or request.

I think it's much better to tell new users about good habits along with the answers they seek. This will prevent a lot of problems in the long run.

> Keep this sort of attitude and many potential users of the UBUNTU Server platform will move on to more friendly and/or helpful alternatives.

Getting used to a new OS takes a bit of time and practice. Cutting corners will eventually hurt yourself. It doesn't matter if it is ubuntu or centos or whatever. The way I see it, the OP both recieved the answer he was looking for and also some good advice. 

I'd rather have potential users moving to other platforms because that ubuntu is not "user friendly" rather than them moving because ubuntu is not secure or stable or fast or any of the things you sacrifice when you install a DE.

[/QUOTE]Just my $.02..... so flame away, if you feel so inclined.......

Regards...

mikey5555[QUOTE]

Cheers.

---

### Post by trash on 2008-08-31
> **brad8266 said:**
> You are probably missing a step. I am fairly new the the ubuntu server side and I found it very simple to install the desktop. I am very familiar with the Linux CLI though.

sudo aptitude update
sudo aptitude upgrade
sudo aptitude install ubuntu-desktop

You need to have a working connection to the internet also because you will be fetching files.

I did uninstall the desktop because it does run better without the GUI, as a matter of fact I really didnt even use the desktop GUI for server admin anyway. Most of my work was done using webmin for an easy to use remote graphical admin tool and putty for CLI. Once I uninstalled the desktop my memory usage went way down as well.

I tried both Ubuntu and Xubuntu, Ubuntu gave me dependency issues and Xubuntu did install ok but I HAL issues afterwards.. so i just decided to forget it and I am happy I did, once i searched for other tools.:)

---

### Post by brad8266 on 2008-08-31
> **trash said:**
> I tried both Ubuntu and Xubuntu, Ubuntu gave me dependency issues and Xubuntu did install ok but I HAL issues afterwards.. so i just decided to forget it and I am happy I did, once i searched for other tools.:)

I cant rememebr if i had to manually install the dependencies or not for the desktop because I did intsall a few things at the same same time and I remember that I did have to manually install some dependencies first, I just cant rememebr if they were for the desktop or some other program.

---

### Post by halitech on 2008-09-05
I guess I'll jump in here as well and stir the pot a little seeing as how it's been 4 days and no new posts on this thread ;)

I just finished reading this thread and this one [http://ubuntuforums.org/showthread.php?t=772796&highlight=desktop+environment](http://ubuntuforums.org/showthread.php?t=772796&highlight=desktop+environment) because I was looking for a way to do a command line install on a LAPTOP and then install a lightweight DE or WM because its an older laptop.

Yes I do realize that both threads are in the SERVER PLATFORMS section and both thrads were asking how do I install a gui and a few gave a direct answer that answered the question but the majority seemed very ... whats the word I'm looking for ... condescending works, because they wanted to install a gui and why they shouldn't install one. Now, I'll admit I am not a server farm admin nor do I wish to be one but what I think alot of people are missing out on, is that some people looking to install a "server" are normal home users who are looking to share a printer, store files (pictures, movies, music) for sharing with other people in the house, maybe share an internet connection instead of buying a router and for those people, the cli is not what they want and bickering at them to not install a gui is just going to have them look at Ubuntu and say F*ck it and go shell out a few hundred bucks to MS because they can install it, click a few things and have their sharing set up. Something happens and they pick up the phone and call support or they reinstall and reclick on a few things and they are back up and running. 

Now, having said that, I'm not saying don't give them the information about the cli, but ask a few questions as you answer theirs and point them to examples showing how easy it is to use the command line and how fast it can be done. 

Personally, I've been using Ubuntu since January 2008 and it is just now that I've gotten to the point that I can actually remember a fair bit of the commands to do things in the cli when I need to but at the same time, its nice having a gui to pull up Nautilus to double check a file location in case I've forgotten it. Remember, it all comes down to choice and if a person comes here looking for help because he liked the help he got in the beginners forum and decides to dump MS for a small home server and gets jumped on for asking about a gui on a server, it's going to sour the whole experience of Ubuntu for all of their machines.

*dons fireproof suit* flame away with your retorts on a home server not really being a server so they shouldn't be in this forum anyway.

---

### Post by z3uSS on 2008-09-06
hy ppl, this is my first post here :)

i just installed ubuntu server 8.04 2 days ago, and i have KDE on it ( i'm kinda new to UNIX ). So first thing u do after completing instalation is to set up u're internet conection. After u had full acces to the web just run the folowing line

sudo apt-get install kubuntu-desktop

it requires something like 3k+ Mb and takes some time to do it (for me something like 5-10 mins and i have very good dld rate >4MB). When installation is done just restart the server ( sudo reboot ) and the server does the rest. U'll be in GUI mode and u can do what ever u want after this.

---

### Post by hyper_ch on 2008-09-06
> **halitech said:**
> Yes I do realize that both threads are in the SERVER PLATFORMS section and both thrads were asking how do I install a gui and a few gave a direct answer that answered the question but the majority seemed very ... whats the word I'm looking for ... condescending works, because they wanted to install a gui and why they shouldn't install one.
Why were those answers condescending? Those people that ask how to add a gui on their server mostly think they must have one to get along. This is not the case. So it was not "condescending" but showing why it's not needed.

There is a reason why a linux/unix server does run without a gui. Furthermore, if you really want to operate a server, you should get yourself accustomed to learning things. It applies for all things. Just because you know how to drive a car (a means of transport) it doesn't mean you know how to handle an airplane (also a means of transport).

If you want to do new things then it is required to learn new things also. By indicating and showing how to run a server properly on a linux/unix machine those people will profit a lot more.

You may call that "condescending". I don't.

---

### Post by windependence on 2008-09-06
> **halitech said:**
> I guess I'll jump in here as well and stir the pot a little seeing as how it's been 4 days and no new posts on this thread ;)

I just finished reading this thread and this one [http://ubuntuforums.org/showthread.php?t=772796&highlight=desktop+environment](http://ubuntuforums.org/showthread.php?t=772796&highlight=desktop+environment) because I was looking for a way to do a command line install on a LAPTOP and then install a lightweight DE or WM because its an older laptop.

Yes I do realize that both threads are in the SERVER PLATFORMS section and both thrads were asking how do I install a gui and a few gave a direct answer that answered the question but the majority seemed very ... whats the word I'm looking for ... condescending works, because they wanted to install a gui and why they shouldn't install one. Now, I'll admit I am not a server farm admin nor do I wish to be one but what I think alot of people are missing out on, is that some people looking to install a "server" are normal home users who are looking to share a printer, store files (pictures, movies, music) for sharing with other people in the house, maybe share an internet connection instead of buying a router and for those people, the cli is not what they want and bickering at them to not install a gui is just going to have them look at Ubuntu and say F*ck it and go shell out a few hundred bucks to MS because they can install it, click a few things and have their sharing set up. Something happens and they pick up the phone and call support or they reinstall and reclick on a few things and they are back up and running. 

Now, having said that, I'm not saying don't give them the information about the cli, but ask a few questions as you answer theirs and point them to examples showing how easy it is to use the command line and how fast it can be done. 

Personally, I've been using Ubuntu since January 2008 and it is just now that I've gotten to the point that I can actually remember a fair bit of the commands to do things in the cli when I need to but at the same time, its nice having a gui to pull up Nautilus to double check a file location in case I've forgotten it. Remember, it all comes down to choice and if a person comes here looking for help because he liked the help he got in the beginners forum and decides to dump MS for a small home server and gets jumped on for asking about a gui on a server, it's going to sour the whole experience of Ubuntu for all of their machines.

***dons fireproof suit* flame away with your retorts on a home server not really being a server so they shouldn't be in this forum anyway**.

Well you saved me the trouble of posting that anyway.

>  its nice having a gui to pull up Nautilus to double check a file location in case I've forgotten it.

I can do this ten times faster using find and grep or locate or if it's a program which or whereis. Anything you can do in the GUI I can do faster at the command line and use less resources on the server. And what about when the GUI pukes (and it does sometimes) and you have to recover from that? In a production environment you don't reboot servers, especially just to bring up a pretty GUI. In fact, unless you need to patch the kernel or the machine hangs (rare without a GUI), you should NEVER have to reboot a Linux/Unix box.

> the cli is not what they want and bickering at them to not install a gui is just going to have them look at Ubuntu and say F*ck it and go shell out a few hundred bucks to MS because they can install it, click a few things and have their sharing set up.

Then they can do the same thing with an Ubuntu desktop product for the use it was intended. You do not need the server version optimizations to run a file server. If that's too difficult then maybe they SHOULD stick with M$.

> Something happens and they pick up the phone and call support or they reinstall and reclick on a few things and they are back up and running. 

Yes, for sure whenever something doesn't work we should always re-install at least 5 or 6 times, if the first 3 or 4 don't work, surely the last few will.

> Now, having said that, I'm not saying don't give them the information about the cli, but ask a few questions as you answer theirs and point them to examples showing how easy it is to use the command line and how fast it can be done. 

Not only will we and have we done this, but we have done an excellent job of it I believe. In addition, we have told them SEVERAL times how to install the desktop while recommending they don't. 

The point is, do you want a server, or a desktop. If you want a desktop, don't install a product that was not intended to BE a desktop. Ubuntu left out the GUI for a REASON, and it's a good one. They have a good server product. They also have a good desktop product. Users should dknow which one they need.

If you notice, I hang out here in the server forums. I do this because I am IMHO a decent server admin and have experience running Linux in a production environment. If you wanna run a server, I will help you. If you wanna run a server the wrong way, I will warn you not to do it that way. Do you think this is somehow wrong? This part of the forums is after all for SERVER platforms, correct?

-Tim

---

### Post by Vivaldi Gloria on 2008-09-06
I was reading [[COLOR="Sienna"]ubuntu-devel-discuss[/COLOR]]("https://lists.ubuntu.com/archives/ubuntu-devel-discuss/") today and I found out a similar discussion also took place there. See July-August 2008 archives. I thought it might interest some of you. A few quotes:

From the post [[COLOR="Sienna"]004990[/COLOR]]("https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-July/004990.html")  which started it:

> People don't know about linux, they won't try it if it doesn't allow them to get their stuff done. What the reasons are for a sysadmin to use (paid licensed) Windows instead of Linux ? GUI. And things they feel in control on ...

From [[COLOR="Sienna"]004993[/COLOR]]("https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-August/004993.html")

> Two decades of Windows thinking have taught people that their systems are essentially incomprehensible black boxes that they cannot understand.  This is not true of Linux and other Unix like operating systems.  I was helping someone out this week on #ubuntu-server with a Postfix problem.  He'd given up and reinstalled his system and still had the same problem.  He'd never really looked at the error he was getting and tried to understand it and how to fix it.  His Windows experience told him he couldn't.

I can understand wanting a GUI because it is helpful (hey, I'm writing this in Kmail and not Mutt), but they should also work on learning to understand their systems.  I'm in favor of GUI tools where they are more effecient and where they help people get started, but not as a long term substitute for knowing what you are doing.

From [[COLOR="Sienna"]005008[/COLOR]]("https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-August/005008.html")

> Fact One: an ISP who allows people running smtp servers should be punished. Private users should use an SMTP Gateway at their ISP or on some root server, but shouldn't be able to send via smtp server <-> smtp server. (HInt: Spammers are using those methods)

Setting up SMTP + POP3 server is definitly nothing you want to have at home...because it's unreliable. No usecase here.

People who have a clue about those topics, don't do this, only people without a clue are trying to do this.

From Mark Shuttleworth's post [[COLOR="Sienna"]005005[/COLOR]]("https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-August/005005.html"):

> I do agree with you that this [running cli servers] requires a more expert understanding of the free software stack, and thus is quite different to our promise with the Ubuntu desktop, which is "the easiest and most modular desktop experience possible with free software". I can understand that this creates a potential shock for users who are new to Linux, find Ubuntu very easy to use on the desktop, and then are dropped into the deep end when they install Ubuntu server.

---

### Post by halitech on 2008-09-06
> **hyper_ch said:**
> Why were those answers condescending? Those people that ask how to add a gui on their server mostly think they must have one to get along. This is not the case. So it was not "condescending" but showing why it's not needed.

There is a reason why a linux/unix server does run without a gui. Furthermore, if you really want to operate a server, you should get yourself accustomed to learning things. It applies for all things. Just because you know how to drive a car (a means of transport) it doesn't mean you know how to handle an airplane (also a means of transport).

If you want to do new things then it is required to learn new things also. By indicating and showing how to run a server properly on a linux/unix machine those people will profit a lot more.

You may call that "condescending". I don't.

I found them to be condescending when I was reading the answers because of the way they are being posted and maybe thats just my take on the post but I'm sure a few people at least have come here looking for an answer, read some of the posts and then decided not to ask their questions because of the way others were answered.

I never said a person shouldn't learn how to do things properly but maybe I'm looking at things from the point of view of a home user that has maybe 2 or 3 home computers and wants a nice easy setup for personal use so they can set it up and forget about it, not the professional who should know 10001 commands to do everything at his finger tips and not be using a gui.

Showing and telling someone how to do it properly? no, I don't find that condescending but when it takes 15 posts for someone to finally give them the answer instead of why they shouldn't, that I do find condescending.

> **windependence said:**
> Well you saved me the trouble of posting that anyway.



I can do this ten times faster using find and grep or locate or if it's a program which or whereis. Anything you can do in the GUI I can do faster at the command line and use less resources on the server. And what about when the GUI pukes (and it does sometimes) and you have to recover from that? In a production environment you don't reboot servers, especially just to bring up a pretty GUI. In fact, unless you need to patch the kernel or the machine hangs (rare without a GUI), you should NEVER have to reboot a Linux/Unix box.

thats my point, YOU can do it faster because you do the job day in and day out but not everyone works with servers for a living so having a gui or some sort makes life easier for them to change something when they do it once every 3 months when they make a change on the network or the power goes out and they need to check a setting.

> Then they can do the same thing with an Ubuntu desktop product for the use it was intended. You do not need the server version optimizations to run a file server. If that's too difficult then maybe they SHOULD stick with M$.

and its attitudes like that that I do find condescending when I'm trying to find help

> Yes, for sure whenever something doesn't work we should always re-install at least 5 or 6 times, if the first 3 or 4 don't work, surely the last few will.



Not only will we and have we done this, but we have done an excellent job of it I believe. In addition, we have told them SEVERAL times how to install the desktop while recommending they don't. 

The point is, do you want a server, or a desktop. If you want a desktop, don't install a product that was not intended to BE a desktop. Ubuntu left out the GUI for a REASON, and it's a good one. They have a good server product. They also have a good desktop product. Users should dknow which one they need.

If you notice, I hang out here in the server forums. I do this because I am IMHO a decent server admin and have experience running Linux in a production environment. If you wanna run a server, I will help you. If you wanna run a server the wrong way, I will warn you not to do it that way. Do you think this is somehow wrong? This part of the forums is after all for SERVER platforms, correct?

-Tim

I can't say you are a good admin, a bad admin or a great admin because I don't know you personally so I'll take your word on it that you are a decent server admin. All I'm trying to get across is this, when someone asks a question (unless the answer is forbidden to answer like how do I log in as root), give them a straight answer first with exactly how to do what they are asking, then ask why they want to do it that way and then explain the better/safer/faster way of doing it from the cli. If you think I'm wrong for thinking this then thats your opinion and I'll leave your server platform area and leave you alone

---

### Post by hyper_ch on 2008-09-06
> **halitech said:**
> I never said a person shouldn't learn how to do things properly but maybe I'm looking at things from the point of view of a home user that has maybe 2 or 3 home computers and wants a nice easy setup for personal use so they can set it up and forget about it, not the professional who should know 10001 commands to do everything at his finger tips and not be using a gui.
You don't need to learn the commands, just how to copy and paste them ;) there are quite a few sites where you just have to copy'n'paste and even by doing so you learn stuff.

Furthermore, not everything is at your finger tips in a gui. A gui is restricting what you actually can do - and that on a large scale.

> **halitech said:**
> Showing and telling someone how to do it properly? no, I don't find that condescending but when it takes 15 posts for someone to finally give them the answer instead of why they shouldn't, that I do find condescending.
Did your parents every say "don't pick your nose", "clean your bedroom", ....? Did they ever say why you shouldn't pick your nose or clean your bedroom? Do you think they were condescending when they told you to do so? Do you meanwhile know why you shouldn't pick the nose and clean up your bedroom?

> **halitech said:**
> thats my point, YOU can do it faster because you do the job day in and day out but not everyone works with servers for a living so having a gui or some sort makes life easier for them to change something when they do it once every 3 months when they make a change on the network or the power goes out and they need to check a setting.
Anybody can do that faster on a cli. Not just him ;)

> **halitech said:**
> then ask why they want to do it that way and then explain the better/safer/faster way of doing it from the cli.
That answer is simple: They don't know any better. Most of them have been used to a GUI for their live long and they just don't know any better. There's no need to ask as of why they want to do that.

---

### Post by halitech on 2008-09-06
> **hyper_ch said:**
> You don't need to learn the commands, just how to copy and paste them ;) there are quite a few sites where you just have to copy'n'paste and even by doing so you learn stuff.

Furthermore, not everything is at your finger tips in a gui. A gui is restricting what you actually can do - and that on a large scale.

I never said a gui was the end all and be all to everything and yes, I have learned over 2 years by copying and pasting commands from help I've gotten here. I also read and try to understand the command before I paste it in case I've talked to an idiot who gave me a bad command.  

> Did your parents every say "don't pick your nose", "clean your bedroom", ....? Did they ever say why you shouldn't pick your nose or clean your bedroom? Do you think they were condescending when they told you to do so? Do you meanwhile know why you shouldn't pick the nose and clean up your bedroom?

I was the type that I always asked why when told to do something or was told not to do something and if the answer was along the lines of "because I said so" I kept asking till I got an answer (far as picking your nose, it can cause damage to the membranes in there so you lose sense of smell and it can also cause persistant nosebleeds if enough damage is done)

> Anybody can do that faster on a cli. Not just him ;)


That answer is simple: They don't know any better. Most of them have been used to a GUI for their live long and they just don't know any better. There's no need to ask as of why they want to do that.

sorry, I used the collective he instead of they

In the world of point and click, most people don't know about the cli or don't want to know about it and thats fine, linux is about choice and if they chose to use a gui and want to use a gui, that is their choice. And I'll give you that point so it goes back to, instead of telling them not to use a gui, (or install it, whatever) give them the steps but also tell them about the cli and that if they copy and paste such and such command it will do the same thing instead of debating with them over why they want the gui for 15 posts before giving them an answer.

I guess I'm still new enough that I see things how someone coming from windows will see things, not as a lifetime server admin who has learned to do things the proper way with real live servers that only have access through ssh to the machines and its 2 different approaches thats needed.

---

### Post by hyper_ch on 2008-09-06
before you can make a choice you must know what choices you have and that is not the case for the people asking on howto install a gui on a server. If they knew how to operate the cli then they would also know how to get a gui on it - if they really want to ;)

---

### Post by windependence on 2008-09-06
> **halitech said:**
> 
I can't say you are a good admin, a bad admin or a great admin because I don't know you personally so I'll take your word on it that you are a decent server admin. All I'm trying to get across is this, when someone asks a question (unless the answer is forbidden to answer like how do I log in as root), give them a straight answer first with exactly how to do what they are asking, then ask why they want to do it that way and then explain the better/safer/faster way of doing it from the cli. If you think I'm wrong for thinking this then thats your opinion and I'll leave your server platform area and leave you alone

If you had actually read any of my posts here, you would quickly find that they always get a straight answer and in more than 50% of cases, I will fix their problem. Not only that but you'll se that every single day I receive thank yous for helping people out.

What bothers me most is when someone come here in the SERVER forum looking for answers related to SERVER questions and then whines about it when we give them a proper SERVER related answer. You don't see the mods transferring questions to the SERVER forums of how to do X in the GUI. My feeling is if you want to run a DESKTOP, then you need to run the DESKTOP version and ask questions in the DESKTOP forums. Yes, I know, you think I'm a CLI snob. Maybe you're right, but let me tell you, I was EXACTLY where you are and I did EXACTLY what you are doing when I was learning. I finally found out that without my precious GUI I was helpless. That's a scary feeling when all your data is on your 'nix machine and you can't access it, even for a home user. You don't think we all popped out of the womb spouting off commands do ya? FYI, I look up a LOT of commands, and you only have to remember one - man. Learning to search google is another invaluable tool. You wouldn't have any idea how many people I help out here simply by looking up the answer on Google. I don't know everything - far fro it. ;)

-Tim

---

### Post by halitech on 2008-09-06
> **hyper_ch said:**
> before you can make a choice you must know what choices you have and that is not the case for the people asking on howto install a gui on a server. If they knew how to operate the cli then they would also know how to get a gui on it - if they really want to ;)

if they can get themselves to a cli then they *should* know the cli exists, otherwise what do they think they are looking at? 

> **windependence said:**
> If you had actually read any of my posts here, you would quickly find that they always get a straight answer and in more than 50% of cases, I will fix their problem. Not only that but you'll se that every single day I receive thank yous for helping people out.

What bothers me most is when someone come here in the SERVER forum looking for answers related to SERVER questions and then whines about it when we give them a proper SERVER related answer. You don't see the mods transferring questions to the SERVER forums of how to do X in the GUI. My feeling is if you want to run a DESKTOP, then you need to run the DESKTOP version and ask questions in the DESKTOP forums. Yes, I know, you think I'm a CLI snob. Maybe you're right, but let me tell you, I was EXACTLY where you are and I did EXACTLY what you are doing when I was learning. I finally found out that without my precious GUI I was helpless. That's a scary feeling when all your data is on your 'nix machine and you can't access it, even for a home user. You don't think we all popped out of the womb spouting off commands do ya? FYI, I look up a LOT of commands, and you only have to remember one - man. Learning to search google is another invaluable tool. You wouldn't have any idea how many people I help out here simply by looking up the answer on Google. I don't know everything - far fro it. ;)

-Tim

and I can understand your frustration on giving a proper answer and hearing people whine about it, I see the same thing up in the beginners forum where I hang out mostly (after 2 years I still consider myself a beginner but one who can answer more then I have to ask anymore) and it annoys me as well when someone asks how do I do this and you tell them point blank and then they ask if thats the only way. Don't like the possible answer, don't ask the question :lolflag:

I know a good sysadmin is not something that is born, they make themselves into it because they want to be good at it. And yes, waking up and sitting down at the keyboard to only see the cli is scary for anyone. Maybe what the admins here need to do is create a new section for Home server questions where people can get help with home server type things where a gui more then likely is in use because its also the computer with the printer connected to it and the burner and the scanner so people who want a gui on a small home server will go there for help that suits their needs instead of being in the server forum where you guys take things seriously because you do it for a living.

No one can ever know it all and I do the same thing, Google is the best friend of any techie (and even none techie who is curious about anything). Its not a matter of knowing all the answers but knowing where to look to find those answers.

---

### Post by perspectoff on 2008-11-18
This is the silliest thread I have ever read.

Simply install the server (e.g. Ubuntu Hardy Heron Server Edition). During installation, I recommend installing the LAMP server stack (as well as other services you might need).

At the first command line prompt, login with the administrator id and password you set at installation.

Set a root user password:

sudo passwd root

the become the root user:

sudo -s

Now update your server installation:

apt-get update

Now install your desktop of choice:

apt-get install kubuntu-desktop

(or apt-get install ubuntu-desktop or apt-get install xubuntu-desktop)

Now you have a server with a full GUI desktop.

---

### Post by hyper_ch on 2008-11-18
it is against forum rules to tell how to enable the root account.

---

### Post by Ameoba on 2008-11-19
Can i just say as the one who started this, that i was never looking for a full set of desktop applications like the ubuntu-desktop package. I was just planing to ease my self into the text based OS slower. So i could easily get used to the file structure, load files accross with an ftp program etc on the gui, but start doing more and more on the command line. 

So a simple 'here is how to load a simple gui' would have suited my question fine. Although i have implemented screen now that i'm manageing my server remotely and wanting to disconnect ssh without loosing the session. So i appreciate those suggestions, as long as my question is also answered.

I've always thought that comand line is the best way to have the most control within easy reach... however a well desgined gui CAN make the tasks they are designed for easier. So if the task dosn't require custom options, is inconsistent enough that a script couldn't do it, then i would prefer a gui.

I agree with the statements about gui taking server load... but on the machine i'm running i've got load to spare and would like that bit of ease while i get used to it.

---

### Post by startrekker on 2010-03-19
I would use the GUI desktop install. Then:
sudo tasksel 

from there pick the parts of the server you need.

If I were running the LAMP stack I would look at securing it:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

