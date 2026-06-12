---
title: "HOWTO: Terminal as the desktop background."
date: 2006-06-23
forum: Tutorials
---

### Post by jinacio on 2006-06-23
The objective is to have a gnome terminal running as the desktop background, right above the actual background image, that won't be displayed by the statusbar or ticker.

It should look something like this:
[Full transparency](http://img336.imageshack.us/img336/378/desktopterminal0uz.png)
or
[Semi-transparent with shadows (using Xgl)](http://img135.imageshack.us/img135/7796/desktopterminal6vw.png)

Ok, lets get started... :)

1) Download devilspie
```
sudo apt-get install devilspie
```

2) Create a configuration file 
```

mkdir ~/.devilspie
nano ~/.devilspie/DesktopConsole.ds

```

3) Paste the following configuration (press Ctrl^X to save and exit):
```
(if
        (matches (window_name) "DesktopConsole")
        (begin
                (set_workspace 4)
                (below)
                (undecorate)
                (skip_pager)
                (skip_tasklist)
                (wintype "utility")
                (geometry "+50+50")
                (geometry "924x668")
        )
)
```

Notes:
- i use workspace 4 but you can use whatever you like.
- you should at least adjust the geometry lines to match your screen.
- **Read** the [devilspie wiki](http://wiki.foosel.net/linux/devilspie#geometry), for other commands!!!

4) Create a new gnome-terminal profile named "DesktopConsole"
- in the "General" tab, untick "show menubar by default..."
- in the "Scrolling" tab, select "Scrollbar is" -> Disabled.
- in the "Effects" tab, set "Transparent background" and shade to "None" (or to whatever you prefer)

5) Add devilspie and gnome-terminal to the Startup Programs in your session:
in System->preferences->sessions, "Startup Programs" tab, add the 2 programs:
```

devilspie
gnome-terminal --window-with-profile=DesktopConsole 

```

6) Logout, Login 8)

check to see that devilspie is running *before* the gnome-terminal command.


Thats it!

Edit:
added screenshot

---

### Post by frodon on 2006-06-23
You make my day man ;)

I was looking for the good devilspie matcher for a long time now, so a BIG thank you. I will put that on the UDSF ASAP.

---

### Post by jinacio on 2006-06-23
glad to know that :D

cheers!

Edit: (forgot something that might be important)

i use (wintype "utility") because it's the most compatible setting: also tried as "desktop" but if the geometry is not maximize and you click anywhere outside the terminal, it will disapear.
the drawback os using "utility" is that the "show desktop" will hide/unhide the terminal.

So far i havent't found a better method, but i'll keep looking into it.

---

### Post by frodon on 2006-06-23
It's perfect in my opinion, the "show desktop bug" is not so annoying.

I never tought that the good macher would be the profile name used by the terminal.

BTW, here is the UDSF link : [http://doc.gwos.org/index.php/Background_Terminal](http://doc.gwos.org/index.php/Background_Terminal)

---

### Post by geektron on 2006-06-23
Just installed it on my workstation. Worked great. Thanks a lot for the turorial.

---

### Post by JMO707 on 2006-06-23
Excellent. Great howto.

Just a problem:



The transparency disappear when I make a "clean console" (ctrl+l)

---

### Post by masterjonny on 2006-06-23
Brillinat guide dude, worked perfectly :)

---

### Post by .exe on 2006-06-23
I can't get this to work. No matter what I do, gnome-terminal --window-with-profile=DesktopConsole  ALWAYS appears in front of devilspie. NO matter what order I enter them in, or what I do after I enter them. Is there a text file that I can edit manually instead?

---

### Post by jinacio on 2006-06-23
[QUOTE=JMO707]
The transparency disappear when I make a "clean console" (ctrl+l)[/QUOTE]

Sorry, i can't seem to repeat that, so no clue on how to fix it :(

only thing i can say is if it's really bugging you try typing "clear" instead ;)

---

### Post by JMO707 on 2006-06-23
It seems like a problem with fake transparencies...
It has happened to me before. 

No clues of what to do neither =(

---

### Post by marcog on 2006-06-23
Really cool!!

One problem I noticed is that if I open a new tab (which works), the height of the terminal increases to display the tabs at the top. However, when I close all but one tab that additional height does *not* "dissapear. And if you keep on opening a tab, then closing it, opening one again, etc. you end up with a very tall terminal.

---

### Post by jinacio on 2006-06-23
[QUOTE=.exe]I can't get this to work. No matter what I do, gnome-terminal --window-with-profile=DesktopConsole  ALWAYS appears in front of devilspie. NO matter what order I enter them in, or what I do after I enter them. Is there a text file that I can edit manually instead?[/QUOTE]

you can also try like this:
```
devilspie & gnome-terminal --window-with-profile=DesktopConsole
```

---

### Post by bocmaxima on 2006-06-23
For sume reason I cant get this to work...I havent the slightest clue why either...I followed it exactly.

The best I ever got was a default sized window that I could see through, but it still had the borders and everything. And it was in Desktop 1, though i specified 3. :( This was cool too.

---

### Post by mistab1034 on 2006-06-24
Thanks for the how to. I got the gnome-terminal working fine. But has anyone tried using devilspie with Nvidia Twinview and tried putting a window on the second monitor? xwininfo shows the correct geometry but I can't get devilspie to put it where i want. Even if I just try and execute firefox with geometry options without devilspie I can't get it to work, and it's only firefox that doesn't work, i can get other windows to go to the second monitor fine. Anybody got an ideas?

---

### Post by jinacio on 2006-06-24
My best guess for devilspie troubles in their [wiki](http://wiki.foosel.net/linux/devilspie). other than that, i'm also clueless 8|

---

### Post by JurB on 2006-06-25
Tnx for this HOWTO, works great!

---

### Post by chipper_30 on 2006-06-25
Worked great for me too, except I had to change the color beacause black wasn't easy to read on the Ubuntu backgroung...
Thanks anyway!

---

### Post by noob_Lance on 2006-06-25
hey.. this program destroyed compiz on my computer. it worked perfectly fine until i tried this program... then every single window i opened was the way the terminal was set to be.. and because of this i have uninstalled compiz... reinstalled it...and to my suprise NO change!.... i have uninstalled devilspie completly! and still my problem comtinues. Please help me fix this..!

~Lance

---

### Post by jinacio on 2006-06-26
[QUOTE=noob_Lance]hey.. this program destroyed compiz on my computer. it worked perfectly fine until i tried this program... then every single window i opened was the way the terminal was set to be.. and because of this i have uninstalled compiz... reinstalled it...and to my suprise NO change!.... i have uninstalled devilspie completly! and still my problem comtinues. Please help me fix this..!

~Lance[/QUOTE]

Ugh thats weird. 

- did you uninstall devilspie and rebooted the pc/killed all instances of it? because if thats the case then devilspie can't be the cause of your problem.

Still, try removing the while ~/.devilspie directory:
```
rm -R ~/.devilspie
```

if that doesn't work then your problem can only be caused by something else.

---

### Post by noob_Lance on 2006-06-26
its being caused by gnome-window-decorator. i did a test start of compiz thru the terminal and found this to be the problem.

---

### Post by Wallakoala on 2006-07-02
can someone tell me how to get that cool semi-transparent effect in the second screenie?

I am using compiz.

---

### Post by Wallakoala on 2006-07-03
anyone?

---

### Post by bulldog on 2006-07-03
Execute the HowTo and all should work perfectly.
You use Xgl/compiz so you should get the effects you want.
Can't tell you more it's all explained on this pages.:D

---

### Post by joakim2 on 2006-07-03
[QUOTE=bulldog]Execute the HowTo and all should work perfectly.
You use Xgl/compiz so you should get the effects you want.
Can't tell you more it's all explained on this pages.:D[/QUOTE]

Seems like compiz still decorates the window... at least for me.

---

### Post by Wallakoala on 2006-07-03
with mine it is just the same as without compiz. I don't know why it doesn't work.

---

### Post by Johnnyboyct on 2006-07-04
I have it working, thanks alot, the howto worked well enough to get me to make it work lol...

Anyways, I have it working, but no matter what i do, it goes in workspace 1, also, if I change the size, it shows the titlebar and frame around the window. Am I doing something wrong.

Thanks I love it :)

---

### Post by baraider on 2006-07-04
[QUOTE=Wallakoala]can someone tell me how to get that cool semi-transparent effect in the second screenie?

I am using compiz.[/QUOTE]
Same here, what is the geometry dimension for the semi-transparent?

---

### Post by jinacio on 2006-07-11
> **Johnnyboyct said:**
> I have it working, thanks alot, the howto worked well enough to get me to make it work lol...

Anyways, I have it working, but no matter what i do, it goes in workspace 1, also, if I change the size, it shows the titlebar and frame around the window. Am I doing something wrong.

Thanks I love it :)

thats a weird glitch (after switching to/from workspace 4 a couple times it goes away)... what i did was remove "(set_workspace 4)" and add "(pin)" instead - it now shows on all desktops, so no glitch ;)


I have no clue on why it doesn't work on some desktops, all i can say is try following everything to the letter, and good luck :P

---

### Post by michaelt on 2006-07-13
[QUOTE=jinacio;1172497]The objective is to have a gnome terminal running as the desktop background, right above the actual background image, that won't be displayed by the statusbar or ticker...


```

devilspie
gnome-terminal --window-with-profile=DesktopConsole 

```

I tried this and eventually succeeded, but eventually abandoned develspie. Once I'd figured out how to play with geometry of the terminal window, and to have it open without titlebar, and to open with multiple tabs, I realized there wasn't a great advantage to devilspie's approach. I'd prefer that the transparency apply to solid-colour desktop backgrounds and gradients (not just images) and that the transparency be real, rather than simulated (i.e. you can see through terminal windows to what is actually on the desktop - something that's possible with OS X, for example, on another of my computers).

For those interested in automatic multiple tabs, its a simple matter of adding 

```
 --tab --tab
```

to the command line in the Sessions, Startup Programs command line for gnome-terminal.

You can also add

```
 --working-directory=%f
```

to set the working directory to your home folder. More options, of course, in the manual: 

```
man gnome-terminal
```

---

### Post by Paradoxx on 2006-07-13
Very nice HOWTO... 

I just have one problem, how do i hide the windoweframe ??

I've tried to add (unshade) to config file...

Thanks in advance

---

### Post by JMO707 on 2006-07-15
> **JMO707 said:**
> Excellent. Great howto.

Just a problem:



The transparency disappear when I make a "clean console" (ctrl+l)

Anybody with this problem?

Any sugestion?

---

### Post by bluevoodoo1 on 2006-07-26
I really like this HOWTO!

I made a crummy script to start/stop this from a launcher or from your menu. It will see if devilspie is running, if so, it will killall gnome-terminal and devilspie. If devilspie isn't running, then it will start it and gnome-terminal. (You have to have the devilspie setting stated here) 

```

#!/bin/sh

if ps -A | grep -e " devilspie$" > /dev/null; then
	killall gnome-terminal &
	killall devilspie &
else
	gnome-terminal --window-with-profile=DesktopConsole --working-directory=/home/$USER &
	devilspie &
fi
```

Copy the code to an empty file. 
Save it.
chmod +x FILENAME
then run it... $ path/to/FILENAME

I only use devilspie and gnome-terminal for this eyecandy, so if you use either for something else, this might not be the best script for you!!!!!

Feel free to change anything to enhance it.

---

### Post by gamerteck on 2006-07-30
Great Guide!

I fixed mine, sorta, by setting the actual path to the OurFile.ds script in the Sessions Startup Programs. 

So instead of.```

devilspie
gnome-terminal --window-with-profile=OurFile
```

I had to put.
```
devilspie
gnome-terminal --window-with-profile=/home/yourusername/.devilspie/OurFile.ds
```

The set_workspace 4 doesn't seem to work for me. So the window always shows in workspace 1. Also gnome-terminal --window-with-profile=YourFilename will always show before devilspie in the Startup Programs.

---

### Post by gamerteck on 2006-07-30
set_workspace 4 now works for me.
I had to edit the .ds config as follows.
```

(if
    (matches (application_name) "Gdesk")
    (begin
        (set_workspace 4)
        (geometry "800x600")
        (undecorate)
        (center)
        (above)
        (skip_pager)
        (skip_tasklist)
    )
)

```

I swapped out window_name with application_name and I also ommited the wintype and second geometry setting, I had also renamed the .ds folder and my terminal profile and title profile to Gdesk.

---

### Post by Aurdal on 2006-07-31
How can I make the terminal fill the whole screen, except the panels?

---

### Post by gorilla_king on 2006-07-31
> **Aurdal said:**
> How can I make the terminal fill the whole screen, except the panels?

have you tried changing the DesktopConsole.ds file to the correct resolutions, or am i misunderstanding

and now for my problem, i feel kind of dumb, but i can't find start up programs in my system=>preferences menu, any idea y? i also looked in alecarte menu editor.

---

### Post by Aurdal on 2006-07-31
Start up programs is a tab in the System > Preferences > Sessions "program".

Yes I have tried changeing the resolutions but it always leaves afew pixels on two of the sides.

---

### Post by Faytz on 2006-07-31
it wont show and the gnome terminal is always before devilspie any solution

---

### Post by xXx 0wn3d xXx on 2006-07-31
Thanks for the tutorial it's very well written. I used it on Archlinux 7.2 and it works great. I attached a screenshot if anyone wants to see it. I have it set to 800x600 so I have some room for desktop icons.

---

### Post by em3raldxiii on 2006-07-31
This is pretty cool.  But I prefer using a program called Yakuake.  It's a drop-down terminal that is reminiscent of the Quake or HL terminal.  Mine's configured to use the F12 key, but I believe you can change it to use the ~ key that many of us are familar with.  The dropdown terminal is also configurable to be dark, lose the scrollbars, and a different height-width.  It's super handy, especially when entering commands from the forums.  

```
sudo apt-get install yakuake
```

I am not sure which repository it's in though ... one of the universes I think.  Perhaps multiverse or PLF.

---

### Post by Faytz on 2006-07-31
:( please anybody help me

---

### Post by em3raldxiii on 2006-08-01
Don't worry big fella ... someone will come to the rescue soon enough :D.  You should be able to put the correct script first depending on the order in which you add them.

Either way, like I said, I actually prefer yakuake.  You might too ... try it out (see my last post).

Good luck!

---

### Post by greenstar on 2006-08-01
> **bocmaxima said:**
> The best I ever got was a default sized window that I could see through, but it still had the borders and everything. And it was in Desktop 1, though i specified 3.

Exactly. I specified Workspace 2, as I only have 2 enabled. Otherwise, that's exactly what I got after following the instructions precisely.

I even tried gamerteck's suggested fixes, to no avail. 

Why was this put into the UDSF? Is this guide really *that* significant, or am I missing the point of the UDSF?

Greenstar

---

### Post by overmetal61 on 2006-08-04
Has anyone been able to play with the geometry to terminal window?

I would like to use devilspie and make the terminal window smaller.  I edit the geometry settings in DesktopConsole.ds and restarted multiple times.

I have also attempted to pass geometry with gnome-terminal --geometry xxx

Can anyone tell if they have gotten resizing/location to work?

Thx
Kevin

---

### Post by greenstar on 2006-08-04
I just installed tilda: ```
sudo apt-get install tilda
```Tilda does the same thing without the script. It can be configured to look the same. Pseudo-transparent background, no borders, custom size & screen location, visible on any workspace you choose, don't show on taskbar, etc.

I use tilda on Workspace 2, other stuff on Workspace 1. Screenshot below.

Greenstar

---

### Post by pay on 2006-10-13
How do you get this to work with kde? Can you just change this line 
devilspie
gnome-terminal --window-with-profile=DesktopConsole

to 

devilspie
konsole --window-with-profile=DesktopConsole

---

### Post by finferflu on 2006-11-15
Well, I used to use tilda as well, but now that I have Beryl installed it is almost useless. In fact it's extremely slow now, so I have to use this solution. The only problem is that I can't get the terminal to show up on Workspace 4, maybe because Beryl has a different concept of "Workspaces"... has anyone managed to fix that?

Thanks

---

### Post by 5h4rk on 2006-11-17
> **.exe said:**
> I can't get this to work. No matter what I do, gnome-terminal --window-with-profile=DesktopConsole  ALWAYS appears in front of devilspie. NO matter what order I enter them in, or what I do after I enter them. Is there a text file that I can edit manually instead?

I got pretty much the same problem, and now I got only 1 workspace...somebody help me?

---

### Post by Isoss on 2006-11-21
> **finferflu said:**
> Well, I used to use tilda as well, but now that I have Beryl installed it is almost useless. In fact it's extremely slow now, so I have to use this solution. The only problem is that I can't get the terminal to show up on Workspace 4, maybe because Beryl has a different concept of "Workspaces"... has anyone managed to fix that?

Thanks

Same problem! 

I love this howto, it worked, but I have two problems:
1. I have beryl, ans so I can't get the terminal to show in the 4 workspaces
2. when I hit "show desktop" button it is minimized, and so I have to hit it again to have the terminal maximized back again! so if I want to get to the desktop I have to minimize each window alone! well .. for me I'm just too lazy to do that every time I want to use the command line! any solution?

Thanks

---

### Post by tigerstripedcat on 2006-11-25
Finally you all are asking my question.  I find that a k/console on the desktop is the only way to go.  With one key you can go to your console with all your terminals.  But I want this to be always on bottom not always on top.  I want to be able to look at other windows while I work on the desktop.  Anyone have a solution with beryl yet???

---

### Post by pavel_kbc on 2006-12-22
nice how to ... i love it and its works great on my ubuntu . can i get icons on desktop? i cant see the desktop when its runing

---

### Post by finferflu on 2006-12-22
I think you would need true transparency in order to see the icons...

---

### Post by moore757 on 2006-12-22
> **finferflu said:**
> I think you would need true transparency in order to see the icons...

Yes, if you are running something like Beryl it looks absolutely fantastic and incredibly clean.  

This is the first I have ever heard of devilspie and i'm thrilled with it.  It took me awhile to mess around with xterm and such to achieve this effect.  This is so fast and easy, thanks so much.  

:cool:

---

### Post by zetsumei on 2006-12-23
i got a question about the geometry lines

if i have a 1280x1024 resolution, what would i put in the 2nd geometry line area?

---

### Post by navneeth on 2006-12-29
Could someone tell me how to get true transparency with devilspie? I don't have any fancy stuff (i.e. Berly, Xgl, etc.) installed.

---

### Post by hikaricore on 2006-12-29
> **navneeth said:**
> Could someone tell me how to get true transparency with devilspie? I don't have any fancy stuff (i.e. Berly, Xgl, etc.) installed.

As far as I know you can't do true transparency with devilspie.

---

### Post by navneeth on 2006-12-29
Well, then, is there some other method by which I could achieve the same effect of devilspie and yet have true transparency?

---

### Post by FaceorKneecaps on 2007-01-04
I have only two workspaces in use (1 and 2) and tried all the tips in this tread but I can't get it to work. The terminal window now opens on startup but thats all. Should Devilspie be configured in some way?

---

### Post by fubar0 on 2007-01-19
Does anybody know how to make comments in the .ds code file? I haven't found anything in the devilspie wiki.

Thanks

---

### Post by fubar0 on 2007-01-19
To answer my question myself: After having found out that devilspie uses a lisp style syntax, it would be the semicolon that introduces a line-oriented comment. 
That was exactly what i was looking for, an I hope that it will be helpful to some other people as well.

Regards

---

### Post by Korken on 2007-03-28
Hmm, when I install it and restart the computer it stops to work.
Anyone else had this problem? How to fix it?

Thanks!

---

### Post by bve on 2007-03-28
Nice howto...

Works like a charm with one caveat, which may or not be related.

Wondering how I can configure my system to use a hotkey vs. the mouse to refocus the term when it loses focus?

And while I'm at it a screenshot.

---

### Post by CityofAsh on 2007-05-30
Very cool!! Thanks much for that tutorial. Any ideas on how to use consoles useing the F Keys like on redhat?  Just wondering i kinda miss that.

---

### Post by buzlink on 2007-05-31
Looks good, I'll have to try that on my new Ubuntu install.

Any idea if something of this sort can be done within OS X?

Thanks

---

### Post by gineraso on 2007-05-31
Excellent, thanks for sharing.

---

### Post by shijirou on 2007-06-09
Can't seem to get this working with Beryl. I tried almost everything on this thread and nohter thread that I've found to no avail. 

If you check the image I've attached, the emerald theme window decorations are showing. I have no idea how to make it blend into the desktop. Anyone with the same problem?

---

### Post by herroy on 2007-06-09
Awesome guide thanks!

but,

I have beryl too and mine only opens as a border-less terminal without the cool 3d effect shown on the howto/first post.

Could anyone help me please?

---

### Post by PaulFXH on 2007-06-10
Thanks for this guide. It works very well for me with Feisty and Beryl.
However, because I have some icons on my desktop, I have reduced the size of the embedded terminal and this was straightforward. But I had a lot more difficulty in specifying where the upper left-hand corner of this terminal is located.
To illustrate what I did
```
(if
        (matches (window_name) "DesktopConsole")
        (begin
                (set_workspace 4)
                (below)
                (undecorate)
                (skip_pager)
                (skip_tasklist)
                (wintype "utility")
                (geometry "+50+50")
                (geometry "924x668")
        )
)
```
I assumed *geometry "+50+50"* refers to the location of the upper left-hand corner and that *geometry "924x668" *refers to the x/y dimensions of the rectangular terminal.
This latter seems to be correct but I find that the location of the terminal seems to wander around my desktop everytime I reboot suggesting that the specified "geometry" is only a rough indication of where the terminal will end up.
Has anybody else had this problem and knows how to resolve it?

---

### Post by ZarathustraDK on 2007-06-10
What am I doing wrong here?

I can get the single console embedded in the desktop, but I'm having trouble getting two of them at the same time.

My DesktopConsole.ds is as follows :

```
(begin
	(if
		(matches (window_name) "DesktopConsole")
		(begin
			(set_workspace 1)
			(below)
			(undecorate)
			(skip_pager)
			(skip_tasklist)
			(wintype "utility")
			(geometry "+700+50")
			(geometry "700x350")
		)
	)

        (if
                (matches (window_name) "DesktopConsole1")
                (begin
                        (set_workspace 1)
                        (below)
                        (undecorate)
                        (skip_pager)
                        (skip_tasklist)
                        (wintype "utility")
                        (geometry "+700+450")
                        (geometry "700x350")
                )
        )
)

```

I make 2 profiles (DesktopConsole and DesktopConsole1) in gnome-terminal.

I make 2 session instances where I start each gnome-terminal with its respective profile.

I set devilspie's order to 51 and the terminals' order to 50 in order to make the terminals before executing the script.

What am I missing?

---

### Post by Hortinstein on 2007-06-13
wow this is really cool idea, but i still cant get it to load....it gives me a 6689 error

---

### Post by NeoLithium on 2007-06-15
> **ZarathustraDK said:**
> What am I doing wrong here?

I can get the single console embedded in the desktop, but I'm having trouble getting two of them at the same time.

My DesktopConsole.ds is as follows :

```
(begin
	(if
		(matches (window_name) "DesktopConsole")
		(begin
			(set_workspace 1)
			(below)
			(undecorate)
			(skip_pager)
			(skip_tasklist)
			(wintype "utility")
			(geometry "+700+50")
			(geometry "700x350")
		)
	)

        (if
                (matches (window_name) "DesktopConsole1")
                (begin
                        (set_workspace 1)
                        (below)
                        (undecorate)
                        (skip_pager)
                        (skip_tasklist)
                        (wintype "utility")
                        (geometry "+700+450")
                        (geometry "700x350")
                )
        )
)

```

I make 2 profiles (DesktopConsole and DesktopConsole1) in gnome-terminal.

I make 2 session instances where I start each gnome-terminal with its respective profile.

I set devilspie's order to 51 and the terminals' order to 50 in order to make the terminals before executing the script.

What am I missing?

Devilspie is setting them both to workspace 1, switch the 2nd instance to another console number, and it should work just fine :)  Another way to do it, if you want the same window on multiple workspaces, is to use the (pin) option, though that will pin the SAME window to all workspace, ie- you type something on workspace 1, it will be showing up in the term on workspace 2.

---

### Post by short4lif2 on 2007-06-24
I have a strange problem.  Everything works fine except that it takes an extremely long time to load the devilspie-ed desktop.  The gnome splash screen sticks around for a good 45 seconds to 2 minutes trying to load the programs before it closes.  The programs do finally open, but what is making it take so long?

---

### Post by bronze on 2007-07-01
My best result so far is a terminal at workspace 1 (ws 3 desired) with transparent background but still with borders. I followed this guide quite precisely two times. I also tried the "devilspie & gnome-terminal" suggestion, to doublecheck that devilspie started first. Help?

---

### Post by chm0d on 2007-08-14
well i have followed this to a t, and I still have borders around my terminal?  I see other people have had the same problem.  How do we get rid of that?

fsckr

SOLVED:

When you put the commands in the sessions startup at the end dont type DesktopConsole.ds just type DesktopConsole with the .ds.  Then make sure devilspie is running first of course before gnome-terminal.  These post were a bit confusing with this fix.  At least I found it.  Thx for the howto.

fsckr

---

### Post by mickc1303 on 2007-08-16
I tried this but found that it killed Beryl.

I have since removed devilspie and done a full reinstall of beryl to no avail.

I can start beryl manually by reloading the window manager but it's a pain to do it every time I login even though it is set to do it automatically in sessions.

Also I have a terminal window start every time I login and I can't figure out how to stop it.  Any help appreciated.

---

### Post by il-luzhin on 2007-08-17
Devilspie won't even load.  It tells me that whichever workspace I specify doesn't exist.

---

### Post by il-luzhin on 2007-08-17
I actually found Tilda to be an excellent alternative

---

### Post by soeten on 2007-08-18
Thanks, this really looks great and is very handy indeed. I should have ditched windows years ago. xD

---

### Post by 5h4rk on 2007-08-19
> **chm0d said:**
> well i have followed this to a t, and I still have borders around my terminal?  I see other people have had the same problem.  How do we get rid of that?

fsckr

SOLVED:

When you put the commands in the sessions startup at the end dont type DesktopConsole.ds just type DesktopConsole with the .ds.  Then make sure devilspie is running first of course before gnome-terminal.  These post were a bit confusing with this fix.  At least I found it.  Thx for the howto.

fsckr

Nop, I'm still getting the windows frame. Can anybody post a solution for this please?

Thanks.

---

### Post by eentonig on 2007-08-22
I can't get devilspie to draw my gnome-terminal without window decorations. 

Does somebody see what I'm doing wrong?

devilspie config:
> ~/.devilspie$ cd ~
rfonteyn@gauloises:~$ more ~/.devilspie/DesktopConsole.ds
(if
(matches (window_name) "DesktopConsole"
         (application_name) "gnome-terminal" )
(begin
        (pin)
        (below)
        (undecorate)
        (skip_pager)
        (skip_tasklist)
        (wintype utility)
        (geometry +50+50)
        (geometry 924x668)
)


startup script.
> #!/bin/bash
#
# Start devilspie en gnome-terminal with profile DesktopConsole
devilspie;
gnome-terminal --window-with-profile=DesktopConsolen  --working-directory=~/bin


And the output of running devilspie.
> ** (devilspie:8436): WARNING **: Error in parsing: Unknown identifier: DesktopConsole
Cannot parse /home/rfonteyn/.devilspie/DesktopConsole.ds: Unknown identifier: DesktopConsole
No s-expressions loaded, quiting
[1]+  Exit 1                  devilspie
rfonteyn@gauloises:~$ 

---

### Post by p2im0 on 2007-08-22
eentonig,
You left a bracket out at the very end.  To close the initial "if" statement.

BTW anyone do anything different to get this running under Beryl/compiz?  & what versions of beryl/compiz packages are people running that have gotten it to work?

---

### Post by znorris on 2007-08-23
Running 
beryl "0.2.1.dfsg+git20070318-0ubuntu2"
emerald "0.2.1-0ubuntu1"

I used the default configuration file for *devilspie* and have only changed the geometry.  I WANTED it to be on the right side of the computer instead of the left but *you don't always get what you want.* :guitar:

Anyway, here is what i have done outside of the scope of the original tutorial.  
1.  I logged off and back in.
2.  A.  System --> Preferences --> Sessions --> Current Session (tab)
     B.  Changed the default order for *devilspie* to 48, changed the desktop *gnome-terminal* to 49.   (note: *beryl-manager* was set to 50)
3.  Hit close on the "Sessions" window.  Told it to save.


I logged off and back in, the desktop terminal was placed in the correct position and does not have any of the window borders that beryl would normally place on it.  (note: it is taking the normal amount of time to load)
Now all i have to do is play with the geometry settings in the config file and all will be peachy.

---

### Post by rogun on 2007-08-23
Those of you having problems getting rid of the window decorations,might want to make sure that your terminal's profile and title names match the name and contents of your config file. I was having the same problem and finally realized that my terminals initial title was all in lower-case. After correcting the case, the window decorations went away.

---

### Post by eentonig on 2007-08-23
Got it working.

For those having problems with their sessions ordering. I just created a startup script for it, and call that from the sessions menu.
This is how my startup script now looks. 
> After some issues with gedit being pinned to all desktops afterwards (strange, because it was the only app that xperienced this and wasn't mentioned in the devilspie .ds file) I found out that you can kill devilspie after the initial startup.

#!/bin/bash
#
# Start devilspie en gnome-terminal with profile DesktopConsole
devilspie & gnome-terminal --window-with-profile=DesktopConsole --geometry 125x45+300+100 --working-directory=~/
killall devilspie

---

### Post by ahawks on 2007-08-24
How do you get the drop shadow, as shown in the screenshot in first post,
[http://img135.imageshack.us/img135/7796/desktopterminal6vw.png](http://img135.imageshack.us/img135/7796/desktopterminal6vw.png) ?

I'm using compiz-fusion, and have devilspie all set up and working, with a beautiful transparent embedded terminal... but I can't figure out how to get the drop shadow.

---

### Post by studiomohawk on 2007-08-27
Thanks for the tip!
It's cool.

I took liberty to translate into Japanese.
[http://gtd.studiomohawk.com/archives/181](http://gtd.studiomohawk.com/archives/181)

---

### Post by Yes on 2007-08-27
I have it working almost fine, thank's for the guide!  My one problem is that if I try and add it to sessions, it always crashes compiz-fusion.  Anyone know why that might be?  I think might need to run eetonig's script, but I'm not sure how.  Can anyone help me?

Thanks again for the great guide!

---

### Post by nest on 2007-08-27
does anyone know what i have to do to have the terminal in every desktop?

---

### Post by s_spiff on 2007-08-28
guys, one solution to the beryl issue is that instead of set_workspace 4 use (pin) that way it appears on workspace 4..or rather the 4th face of the cube.
check it out and lemme know if you guys could reproduce it.

---

### Post by Thomar on 2007-08-28
Rockin'!

This is great!  Now if only I could figure out a font color that consistently stands out against my desktop wallpaper...

---

### Post by grokwik on 2007-08-29
Thanks for this how to :)
I wouldn't say you changed my life but you made it a little bit better !!

---

### Post by nest on 2007-08-29
people, just wanna ask something.

i did all you said and it was perfect. just wanna know what i've to do to put the terminal in every desktop. i made a little research on google and saw that i have to put (pin) instead of (set_workspace num).

i did that and the terminal was in the same workspace that was before.

any ideas?

---

### Post by markp1989 on 2007-09-14
this is exactly what i have been looking for, thank you, i attached a screen shot as well, cause it looks good lol

---

### Post by Hubi17 on 2007-09-27
This is awesome. Thanks a lot for the great HowTo!!!!

I have only one slight problem. I have set the console to be on desktop 2, but once i log it it shows it on desktop 1. after switching to desktop 2 it gets moved correctly. If i switch from desktop 1 to 3 initially, skipping 2, it also appears on desktop 3. Only after switching to desktop 2 does it stay there. any suggestions on how to fix that?

And in order to get the correct startup sequence i found it a good idea to add bluevoodoo1's script to the session instead of devilspie and the gnome-terminal.

---

### Post by FreakTech on 2007-10-03
I am getting this when devilspie starts  
```
** (devilspie:14658): WARNING **: Error in parsing: Unexpected token encountered: 226
Cannot parse /home/cmuncy/.devilspie/DesktopConsole.ds: Unexpected token encountered: 226
No s-expressions loaded, quiting

```


Any ideas.

---

### Post by nawitus on 2007-10-04
This is how to fix the "show desktop bug":
First, open the show desktop about, take a screenshot, and use gimp/picture editor to create icon (I saved it as a .png). Then, open up terminal, click edit->profiles and select DesktopConsole. Go to title and command and changeDynamically-set-title : Isin't displayed.

Create a file called "showdesktop" anywhere, and edit it.
Paste this:
```

#!/bin/bash
wmctrl -k on
wmctrl -a DesktopConsole
exit

```
and save it.
Right-click on desktop and create launcher. Open the folder where you saved the icon and select it. Select the file "showdesktop". Drag the icon to your panel, and delete the other icon from your desktop.

Type:
```

sudo apt-get install wmctrl

```

Delete the old "show desktop button" which didn't work.

Now your new show desktop button should work correctly.

Also, replace the Ctrl-Alt-D hotkey to execute "showdesktop" script by following this guide:
[http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/)

---

### Post by FreakTech on 2007-10-04
Anyone know how to get this to show up on all 4 desktops with compiz-fusion.  I researched and found the (pin) suggestion, but this is not working.  Here's my .ds file.

```
(if
(matches (window_name) "DesktopConsole")
(begin
(pin)
(below)
(undecorate)
(skip_pager)
(skip_tasklist)
(wintype "utility")
(geometry "+50+50")
(geometry "924x668")
)
)

```

---

### Post by nawitus on 2007-10-05
> **FreakTech said:**
> Anyone know how to get this to show up on all 4 desktops with compiz-fusion.  I researched and found the (pin) suggestion, but this is not working.  Here's my .ds file.

```
(if
(matches (window_name) "DesktopConsole")
(begin
(pin)
(below)
(undecorate)
(skip_pager)
(skip_tasklist)
(wintype "utility")
(geometry "+50+50")
(geometry "924x668")
)
)

```

try (stick)

---

### Post by FreakTech on 2007-10-05
(stick) worked great.  Thanks nawitus

---

### Post by Ant_Merlin on 2007-10-07
Hello, I have got this working, following the Totorial but using a script as suggested by eentonig:
> After some issues with gedit being pinned to all desktops afterwards (strange, because it was the only app that xperienced this and wasn't mentioned in the devilspie .ds file) I found out that you can kill devilspie after the initial startup.

#!/bin/bash
#
# Start devilspie en gnome-terminal with profile DesktopConsole
devilspie & gnome-terminal --window-with-profile=DesktopConsole --working-directory=~/
killall devilspie

Notice i used same but removed geometry as i have that in the DesktopConsole file.
My Problem however is that no matter what i try, emerald will not start upon boot and I have to reload window manager each time. Anyone any suggestions?

---

### Post by chez17 on 2007-10-11
After hours of trying trying to get this to work, I finally got it running perfectly with beryl. Since I had the same questions as a lot of people, let me just say a few things that I did to make it work perfectly on my desktop.

1. turns out "gnome" only has 1 g at the beginning, not 2. That took a while for me to figure out. SPELL CHECK.

2. I couldn't get Beryl to load as the default window manager, it always went to metacity and when I switched it, the geometry coords I wanted got all sorts of messed up. Now I am not sure how scientific this is, but they way I got this to work every time is to do 2 things. First, I separated the geometry() statements. First I did the offset, then I did the length. Second, and this is what got it working for me was I made sure it didn't over lap any icons. I have one icon in my upper left corner for my external hard drive, when it overlapped that, Beryl would not load by default, now it does. Maybe Im connecting things that shouldn't be connected, but all Im saying is it worked for me.

(if
        (matches (window_name) "DesktopConsole")
        (begin
                (set_workspace 1)
                (below)
                (undecorate)
                (skip_pager)
                (skip_tasklist)
                (wintype "utility")
                (geometry "+130+30")
                (geometry "700x800")
        )
)


Ok, so that did it for me, hope this helps somebody.

---

### Post by DefianceX on 2007-10-13
> **nawitus said:**
> This is how to fix the "show desktop bug":
First, open the show desktop about, take a screenshot, and use gimp/picture editor to create icon (I saved it as a .png). Then, open up terminal, click edit->profiles and select DesktopConsole. Go to title and command and changeDynamically-set-title : Isin't displayed.

Create a file called "showdesktop" anywhere, and edit it.
Paste this:
```

#!/bin/bash
wmctrl -k on
wmctrl -a DesktopConsole
exit

```
and save it.
Right-click on desktop and create launcher. Open the folder where you saved the icon and select it. Select the file "showdesktop". Drag the icon to your panel, and delete the other icon from your desktop.

Type:
```

sudo apt-get install wmctrl

```

Delete the old "show desktop button" which didn't work.

Now your new show desktop button should work correctly.

Also, replace the Ctrl-Alt-D hotkey to execute "showdesktop" script by following this guide:
[http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/)


Wow that is genius!

I was on the verge of giving up this desktop terminal thing because of the showdesktop bug but this saved it. Thanks.

May I ask what about this code that make this thing work?

---

### Post by michiel.patrick on 2007-10-13
What an excellent how-to. Props to you

---

### Post by drworm01 on 2007-10-20
This stopped working for me once I upgraded to Gutsy. Worked fine in Feisty. Now I can't control where the terminal goes. No matter what geometry I input, the terminal's always locked to the upper left hand corner. The size corresponds to the geometry command, but the positioning doesn't. When I try adding (center), it centers the terminal as though it were 800x600 (I think) and then resizes it from there with the upper left corner locked (so it bloats down into the lower right corner). Anyone else have this problem? Is it something with Gutsy and Devilspie? Any suggestions?

---

### Post by soeten on 2007-10-22
Doesn't work for me in Gutsy either. No idea of what to do. : p

---

### Post by nedmas on 2007-10-24
Yeah same since upgrading to Gusty devilspie has just not worked! Has something changed with geometry or wot?! Anyone got any smart ideas?

---

### Post by Six_Digits on 2007-10-27
I followed the guide EXACTLY, twice. Had the same problem as many, with the window decorations, size, etc. 

You know why? Devilspie couldnt find the "DesktopConsole.ds" file. It's not about to tell you all that though. Heres what I did:

1. Read the info on devilspies page, read the read-me included in their package, read more, read, read, and read.
2. Found that devilspie searches two locations for its ".ds" files, "~/.devilspie/" and "/etc/devilspie". 
3. I created the other directory devilspie uses, and created the new  "DesktopConsole.ds":

sudo mkdir /etc/devilspie
sudo gedit

Pasted this:

(if
        (matches (window_name) "DesktopConsole")
        (begin
                (pin)
                (below)
                (undecorate)
                (skip_pager)
                (skip_tasklist)
                (wintype "utility")
                (geometry "+50+50")
                (geometry "1024x768")
        )
)

And then saved it to the new directory, "/etc/devilspie" with the filename "DesktopConsole.ds".
4. Login-logout and everything was about perfect, with beryl running too.

I seem to have no control of what workspace my terminals on, but I think I can point a finger at  Beryl for that.  Also, When I want to post code on the forums, how do I get that fancy box?

---

### Post by DaymItzJack on 2007-10-28
@Six_Digits: Use [code] tags


I tried doing this on gutsy & compiz fusion, but for some reason, gedit is doing it instead of terminal. Anyone have solutions for gutsy?

---

### Post by BoarderX2k3 on 2007-10-28
I'm having the same problem with Gutsy and the geometry commands. No matter what I try, it always sticks in the upper left. I have also placed my config file in ~/.devilspie and /etc/devilspie. Nothing works yet, anyone have a fix?

---

### Post by DaymItzJack on 2007-10-29
I ditched the (geometry) lines and replaced it with (maximize) which I personally think is better.

---

### Post by ernia on 2007-10-31
if it would be helpful (debian + xfce4) :
-i gave geometry options in the terminal command line --geometry 78x78+120+0
-i've obtained better results with (wintype "dock")

thanks for your great info!!

---

### Post by Green_Star on 2007-11-03
> **ernia said:**
> if it would be helpful (debian + xfce4) :
-i gave geometry options in the terminal command line --geometry 78x78+120+0
-i've obtained better results with (wintype "dock")

thanks for your great info!!

Finally made it work in gusty with your instructions, but still using utility instead of dock. but the command prompt starts at top edge , there is a space between command prompt and left side edge. i tried but i couldnt make command prompt to start little down instead of top edge. any help?

---

### Post by crobruncato on 2007-11-03
Is there a way to do this on kubuntu?

Thanks!
Rob

---

### Post by ernia on 2007-11-03
> **Green_Star said:**
> Finally made it work in gusty with your instructions, but still using utility instead of dock. but the command prompt starts at top edge , there is a space between command prompt and left side edge. i tried but i couldnt make command prompt to start little down instead of top edge. any help?
in the "--geometry 78x78+120+0"  terminal option 78x78 means the window size, 120 is the offset in pixel from the left side and 0 is the offset from the top side. if you want your prompt appear a little bit down try 78x78+120+60.
you can find a better description of that (and in a better english too :oops: ) by typing "man X" and looking for "GEOMETRY SPECIFICATIONS" (i'm not shouting, it's written this way). bye

---

### Post by DefianceX on 2007-11-03
What do you mean 

> i gave geometry options in the terminal command line --geometry 78x78+120+0

No matter what I do, only the window size works in my geometry but not the offset option.

---

### Post by ernia on 2007-11-03
> **DefianceX said:**
> What do you mean 



No matter what I do, only the window size works in my geometry but not the offset option.
stop devilspie and launch the terminal trough a command line with the geometry option (check your terminal man page to know if you need only one - or two), try until you get the window you want.
when you get the right command use it to launch the terminal and then apply devilspie to that window with no devilspie's geometry options, just ignore geometry in devilspie .ds file.
it worked for me, i've done this way because i haven't been able to place the window in the rigth position with devilspie. if it does not work for you i cant help you, sorry

---

### Post by DefianceX on 2007-11-03
> **ernia said:**
> stop devilspie and launch the terminal trough a command line with the geometry option (check your terminal man page to know if you need only one - or two), try until you get the window you want.
when you get the right command use it to launch the terminal and then apply devilspie to that window with no devilspie's geometry options, just ignore geometry in devilspie .ds file.
it worked for me, i've done this way because i haven't been able to place the window in the rigth position with devilspie. if it does not work for you i cant help you, sorry

It worked perfect for me!  Thanks ernia.

---

### Post by drworm01 on 2007-11-05
> **ernia said:**
> you can find a better description of that (and in a better english too :oops: ) by typing "man X" and looking for "GEOMETRY SPECIFICATIONS" (i'm not shouting, it's written this way). bye

Still no luck with terminal as background. I tried doing the geometry in the command line and just ended up with a terminal window the size of the desktop. This might be part of the problem though: What do you mean by "man X"? Is "X" an actual program or do you just mean "fill in terminal program name"? Because "man X" just produced a "no program" response from my system. So maybe my problem lies in my lack of X.

But, using geometry in the command line did produce some strange results. Maybe they illuminate my problem. Putting the DesktopConsole command directly in produces a terminal window with the DesktopConsole profile sitting in the upper-left corner the size of a regular terminal. If I add "--geometry=(geometry command)" I get a terminal the size of the entire screen. If I add "--geometry(geometry command)" I get a regular-sized terminal. It doesn't matter what numbers I enter, I only get the two sizes. It's decided by the equals sign.

Any ideas?

Thanks.

---

### Post by ernia on 2007-11-05
> **drworm01 said:**
> Still no luck with terminal as background. I tried doing the geometry in the command line and just ended up with a terminal window the size of the desktop. This might be part of the problem though: What do you mean by "man X"? **Is "X" an actual program or do you just mean "fill in terminal program name"**? Because **"man X" just produced a "no program" response from my system**. So maybe my problem lies in my lack of X.

But, **using geometry in the command line did produce some strange results. Maybe they illuminate my problem**. Putting the DesktopConsole command directly in produces a terminal window with the DesktopConsole profile sitting in the upper-left corner the size of a regular terminal. If I add "--geometry=(geometry command)" I get a terminal the size of the entire screen. If I add "--geometry(geometry command)" I get a regular-sized terminal. It doesn't matter what numbers I enter, I only get the two sizes. It's decided by the equals sign.

Any ideas?

Thanks.
X is the X window system, you should have it in /usr/bin/X (unless Ubuntu is so different from Debian, wich I don't think)
man is a command that shows you manual page of the programs you have in your system (unless your system lack the man program itself)
I don't use gnome, i can't help you about gnome terminal command line, and i think (i don't want to be offensive, forgive me if i am) that you don't know exactly the difference from a program and an option,and this (and my broken english too)  is a little bit confusing. i'm not sure to have understood what you really mean.
I think you should try forgetting about devilspie, don't launch devilspie and check ( ps aux | grep devilspie) if there is any devilspie running in the background. if there is one kill him. Play with the geometry option until you get the right terminal window and after this try to use devilspie with no geometry in the .ds file to put the window in the background.
you could try aterm instead of gnome terminal (apt-get install aterm).

---

### Post by Tristan_F on 2007-11-06
> **crobruncato said:**
> Is there a way to do this on kubuntu?

Thanks!
Rob

I use Kubuntu and use an alternative method. You can use Eterm as a terminal and tell it to be transparent with no scrollbar. You can even configure it to not show in Kicker.

Just apt-get Eterm and use the following command for example

kstart --skiptaskbar Eterm -trans --borderless --scrollbar=false -buttonbar=false -f black --font-fx none -g 90x45+5+172 ; kstart --skiptaskbar Eterm -trans --borderless --scrollbar=false --buttonbar=false -f black --font-fx none -g 82x45+565+172 ; kstart --skiptaskbar Eterm -trans --borderless --scrollbar=false --buttonbar=false -f black --font-fx none -g 120x11+335+10;

You'll get exactly something like in the screenshot here. In my case I have three terminal open. If you use only kstart --skiptaskbar Eterm -trans --borderless --scrollbar=false -buttonbar=false -f black --font-fx none -g 90x45+5+172 you'lll have only the left one. 

Hope this help

[IMG]http://tristan.ferroir.free.fr/Linux/Transparent_Eterm.jpg[/IMG]

---

### Post by drworm01 on 2007-11-10
Now it's working. And yes, I was muddling my terminology.

I added the geometry option before the terminal profile, ie
```
gnome-terminal --geometry=100x40+150+50 --window-with-profile=DesktopConsole
```
 instead of 
```
gnome-terminal --window-with-profile=DesktopConsole --geometry=100x40+150+50. 
```

The window would only move in 50 pixel increments (so 50, 100, 150 but not 75 or 90) and the 100x40 is in the terminal's own units, not pixels (click on the edge of a terminal window to resize and it'll pop up with it's current scale). Devilspie is working fine now with geometry added to the command line. 

The problem I had earlier--with the geometry option producing either a big-as-desktop terminal or a regular-sized terminal depending on the presence of an equals sign--stems from the terminal not being sized in pixels. Setting the geometry option in pixels (say 800x400) made the terminal massive when the equals sign was there. The option was ignored when the equals sign was absent.

"man X" produces a "No manual entry" result in Ubuntu even though the X Windows System is clearly present. There's just no manual page for it, although there is a manual page for xman, the manual viewer program for the X Windows System.

---

### Post by IIIV on 2007-11-12
**For those of you on Gutsy + Compiz, here's a nice tutorial on embedding the terminal on your desktop: **[http://ubuntology.com/2007/10/25/howto-embedded-terminal-on-your-gutsy-desktop/]("http://ubuntology.com/2007/10/25/howto-embedded-terminal-on-your-gutsy-desktop/")

[B]The only problem it has is it doesn't work properly on start up, because it loads up before Compiz does. So, what I did was I just didn't put it on my start up sessions at all. I just load the terminal manually whenever I need it and it loads up embedded in my desktop.

Hope this helps! [/B] :-)

---

### Post by frodon on 2007-11-13
No need to use bold or link to an external link when there's just to use the search feature of the forum ! :
[http://ubuntuforums.org/showthread.php?t=535098](http://ubuntuforums.org/showthread.php?t=535098)

In addition the devilspie method is not WM dependant.

---

### Post by Scruffynerf on 2007-11-13
Many thanks for the HOWTO, I followed it and it worked... kinda. 2 quick questions:

Quick question 1) - is there a way to find the coordinates or window size on a given screen at a given resolution? I'd ideally like to be able to put it in a particular place, however am having trouble locating the particular place. Sizing seems to work, but not the offsets.

Quick question 2) - it seems that if I open applications via this terminal, such as gedit, it will strip away the window controls for the application and forces it fullscreen. Is there a way around this problem? It seems to fault in locating some items in my theme.

cheers

Rob

---

### Post by kdarkentity on 2007-11-19
I have this set-up and set to workspace1, however the terminal wallpaper appears on my first workspace.

---

### Post by Fredrik_b on 2007-12-02
Kepp geting tiss error message:

```
** (devilspie:5766): WARNING **: Error in parsing: Unexpected token encountered: 226
Cannot parse /home/fredrik/.devilspie/gpodder.ds: Unexpected token encountered: 226

```

my .ds file

```

(if
(is (application_name) &#8220;gpodder&#8221;)
(begin
(set_workspace 4)
(minimize)
)
)

```

---

### Post by crisnoh on 2007-12-05
How do I make sure that devilspie is starting before gnome terminal?  I have my system set to run the following command at startup, but I'm still getting a window border when the terminal comes up:

```
devilspie & gnome-terminal --window-with-profile=DesktopConsole
```

Here is my ds file:

```
(if
        (matches (window_name) "DesktopConsole")
        (begin
                (set_workspace 1)
                (below)
                (undecorate)
                (skip_pager)
                (skip_tasklist)
                (wintype "utility")
                (geometry "+700+50")
                (geometry "620x668")
        )
)
```

---

### Post by CosmicFlux on 2007-12-05
Hey,

OK, it works perfectly. One problem I'm having...

I've set the DesktopConsole profile to run as default, but I now want to change the transparency settings for the profile. How do I access it now that the menu bar is gone? Is there command-line access?

CosmicFlux

---

### Post by subs on 2007-12-06
thnx man!!!

my desktop looks gr8 now!!

---

### Post by CosmicFlux on 2007-12-06
OK, I've got this;

[[IMG]http://img441.imageshack.us/img441/7794/terminalxx9.th.png[/IMG]](http://img441.imageshack.us/my.php?image=terminalxx9.png)


What do I edit to get the size changed?


CosmicFlux

---

### Post by CosmicFlux on 2007-12-06
It's OK, I've figured it out. 

Thanx!

---

### Post by Snakob808 on 2007-12-07
Awesome, awesome, awesome tutorial!

Thank you.

---

### Post by legolas on 2007-12-08
> **nawitus said:**
> This is how to fix the "show desktop bug":
First, open the show desktop about, take a screenshot, and use gimp/picture editor to create icon (I saved it as a .png). Then, open up terminal, click edit->profiles and select DesktopConsole. Go to title and command and changeDynamically-set-title : Isin't displayed.

Create a file called "showdesktop" anywhere, and edit it.
Paste this:
```

#!/bin/bash
wmctrl -k on
wmctrl -a DesktopConsole
exit

```
and save it.
Right-click on desktop and create launcher. Open the folder where you saved the icon and select it. Select the file "showdesktop". Drag the icon to your panel, and delete the other icon from your desktop.

Type:
```

sudo apt-get install wmctrl

```

Delete the old "show desktop button" which didn't work.

Now your new show desktop button should work correctly.

Also, replace the Ctrl-Alt-D hotkey to execute "showdesktop" script by following this guide:
[http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/)


I couldn't get it working.  Darn permissions.  622 is good it looks like.  I had 600 and it didn't like it for some reason.
Thanks for the great idea.

---

### Post by fx55 on 2007-12-08
It works excellent!!! Thanks!!!

---

### Post by Slippy Lane on 2007-12-27
RIght-click, Show menu bar. :-)

---

### Post by Slippy Lane on 2007-12-27
I love this howto, and it mostly worked fine for me until recently. 

Starting the terminal with DesktopConsole profile works fine manually, but doesn't work for me when starting with the session - for some reason, the terminal window title is wrong.

Even though I have, in the DesktopConsole profile, told gnome-terminal to set the title to DesktopConsole and not display a dynamic title, for some reason it has changed it to "user@domain: ~ user@domain: ~"
(For reference, defailt title is "Terminal - user@domain: ~")

Calling "gnome-terminal --window-with-profile=DesktopConsole" manually after startup works fine. Odd, huh?

---

### Post by Slippy Lane on 2007-12-27
Been playing about with this for quite a few hours now, trying to get a console on each screen of my dual monitor configuration, and below is what I came up with. It also gets rid of the annoying tendency for the scripts to apply to any app with "DesktopConsole" in the title ;-)

_ Instructions:_

 Create two gnome-terminal profiles, named DesktopConsoleLeft and
 DesktopConsoleRight, respectively, with transparent backgrounds.

 Add these three entries to the session manager autostart list:
  devilspie -a
  gnome-terminal --window-with-profile=DesktopConsoleLeft
  gnome-terminal --window-with-profile=DesktopConsoleRight 

**Note:** Adding the '-a' to devilspie means it doesn't matter what order they open in - it will apply to existing windows as well as newly opened ones.

And here's the code...
```

(if (and (is  (window_class) "Gnome-terminal")
         (matches (window_name) "DesktopConsole"))
  (begin
    (if (matches (window_name) "DesktopConsoleLeft")
      (begin
        (pin)
        (below)
        (undecorate)
        (skip_pager)
        (wintype "utility")
        (geometry "800x924+240+50")
      )
    )
    (if
      (matches (window_name) "DesktopConsoleRight")
      (begin
        (pin)
        (below)
        (undecorate)
        (skip_pager)
        (wintype "utility")
        (geometry "800x924+1520+50")
      )
    )
  )
)
```

If you're using Compiz Fusion, the (pin) setting probably won't work. The way around that is to open up ccsm (compiz-config settings manager), Enable and open the Window Rules plugin configuration and change the "sticky" entry to

```
title=DesktopConsoleLeft|title=DesktopConsoleRight
```

Here's what the finished article looks like on my desktop:

[IMG]http://slippy.lane.googlepages.com/bigscreenshot.jpg[/IMG]

---

### Post by dlegend on 2007-12-28
For those who can't get the windows decoration (borders) removed on system start up I have posted a solution at the following thread:

[http://ubuntuforums.org/showthread.php?t=652173](http://ubuntuforums.org/showthread.php?t=652173)

---

### Post by RavUn on 2007-12-28
Could anyone help me adjust the size and position of the terminal on the background?

I've messed with the geometry settings and gone up and down with the numbers but it seems to jump around without any rhyme or reason.

I assumed +50+50 meant it goes right and down 50 but I was wrong...
Right now I have it as 800x964 and +50+50 but it just goes to the top right corner and takes up a quarter of the screen.

I'm trying to make it come out about an inch from the left and go all the way up and down.  Can anyone explain what I'd need to do?

It seems devilspie is creating the right sized window because when I login I see it takes up the space I want but then when the terminal loads it just takes up that top left corner.

---

### Post by days_of_ruin on 2007-12-30
Havent gotten it too work yet, I am using 7.10 btw.
In step five, am I supposed to add both lines of code into
one program?How do I check to see if they are running?

---

### Post by dlegend on 2007-12-31
> **days_of_ruin said:**
> Havent gotten it too work yet, I am using 7.10 btw.
In step five, am I supposed to add both lines of code into
one program?How do I check to see if they are running?

Step 5 you should add each line as a separate startup program. Either that or you could try adding this as a program alone:

> 
devilspie & gnome-terminal --window-with-profile=DesktopConsole


Once that has been added and you log out/log back in you go to the Sessions manager again and click "Current Sessions" and see if those programs are running under "Program". It should say devilspie and gnome-terminal in the list somewhere.

Also you could go to System > Administration > System Monitor and check your processes list to see if it is running.

---

### Post by days_of_ruin on 2007-12-31
Okay I got it to work finally but its always halfway in the workspace that I launch it from(using the terminal) and the workspace to theright.
How do I move it where I want?

---

### Post by jbeck22 on 2007-12-31
I can get this to work, but the terminal only appears in the middle of the screen.

My screen resolution is 1024x768 and I'm trying to get the terminal in the upper left corner.

I can get it in the upper left corner if I change my screen resolution to something really small like 640x480.

---

### Post by dlegend on 2007-12-31
> **days_of_ruin said:**
> Okay I got it to work finally but its always halfway in the workspace that I launch it from(using the terminal) and the workspace to theright.
How do I move it where I want?

Change this line (in your DesktopConsole.ds file):

> 
(geometry "+50+50")


The first number +50 is the X position or the amount of pixels from the left of the screen that the terminal will be located at.

The second +50 is the Y position or the amount of pixels from the top of the screen that the terminal will be located at.

This line is your width/height of the terminal:

> 
(geometry "924x668")


If it doesn't position correctly you may need to read/follow this post: [http://ubuntuforums.org/showpost.php?p=1304494&postcount=32](http://ubuntuforums.org/showpost.php?p=1304494&postcount=32)

If you do decide to create the script as described in the above link then you'll need to add the location to the script in your Sessions manager and remove the other two applications that you added (as it will be executed from the script).

---

### Post by jbeck22 on 2007-12-31
Got it working now....



still not working....

here is the contents of  :

(if
(matches (window_name) "DesktopConsole")
(begin
(set_workspace 1)
(below)
(undecorate)
(skip_pager)
(skip_tasklist)
(wintype "utility")
(geometry "0+70")
(geometry "1024+768+0+0")
)
)

I have attached a screenshot of my desktop...

---

### Post by dlegend on 2008-01-01
> **jbeck22 said:**
> Got it working now....



still not working....

here is the contents of  :

(if
(matches (window_name) "DesktopConsole")
(begin
(set_workspace 1)
(below)
(undecorate)
(skip_pager)
(skip_tasklist)
(wintype "utility")
(geometry "0+70")
(geometry "1024+768+0+0")
)
)

I have attached a screenshot of my desktop...


You set the position twice. +value+value indicates the position (eg. +50+50 means 50 pixels to the right and 50 pixels down) geometry "500x500" for instance indicates the width and height of the terminal.

---

### Post by jbeck22 on 2008-01-01
This is what I'm using now and it seems to work pretty well...

(if
(matches (window_name) "DesktopConsole")
(begin
(set_workspace 1)
(below)
(undecorate)
(skip_pager)
(skip_tasklist)
(wintype "utility")
(geometry "70+70")
(geometry "924x668")
)
)



although it still doesn't automatically load when I login...I have to open terminal manually and then open the DesktopConsole profile by hand.

O well.

---

### Post by dlegend on 2008-01-01
> **jbeck22 said:**
> This is what I'm using now and it seems to work pretty well...

(if
(matches (window_name) "DesktopConsole")
(begin
(set_workspace 1)
(below)
(undecorate)
(skip_pager)
(skip_tasklist)
(wintype "utility")
(geometry "70+70")
(geometry "924x668")
)
)



although it still doesn't automatically load when I login...I have to open terminal manually and then open the DesktopConsole profile by hand.

O well.

See this thread: [http://ubuntuforums.org/showthread.php?t=652173](http://ubuntuforums.org/showthread.php?t=652173)

It may help you get it automatically loading.

---

### Post by SevenDeuce on 2008-01-01
> **jinacio said:**
> ... what i did was remove "(set_workspace 4)" and add "(pin)" instead - it now shows on all desktops, so no glitch ;)

Thank you so much, that has been what I've been trying to accomplish since I found this!

You are a hero!

---

### Post by TheTank on 2008-01-12
Tried to get it running for a few hours and it won't work correctly.
1. I cannot position it correctly.
2. it screws up and moves gedit. Yeah, it moves gedit but not the intended window.

I also noticed that I had to change some settings in the terminal to get it to print out the profile in the title, but that did not change anything.

One positive thing I might be able to contribute: you can add --hide-menubar as a param to the terminal to get it to hide the menu bar.

---

### Post by chris4585 on 2008-01-26
> **greenstar said:**
> I just installed tilda: ```
sudo apt-get install tilda
```Tilda does the same thing without the script. It can be configured to look the same. Pseudo-transparent background, no borders, custom size & screen location, visible on any workspace you choose, don't show on taskbar, etc.

I use tilda on Workspace 2, other stuff on Workspace 1. Screenshot below.

Greenstar

dude thanks!!!! i love tilda, i love how you can configure tilda, the only thing that could be added in the config setup is possibly "auto fill" (i just made that up) which will fill all the empty space not being used by panels or dock's, sure doing the math of how high the panel is then subtract that from your screen res, but everything is better when auto configured! 

anywho thanks! i love this program

P.S. the transparency option is a bit buggy, for me everything i type disappears then it gets a bit more buggier when i try to highlight the text

> **il-luzhin said:**
> I actually found Tilda to be an excellent alternative

+1

tilda is so easy, the only problem i've had is that i cant get the transparency to work... no excuse for this i might of set something wrong but everything seems default, the config files are easy to change and figure out, for instance download and install tilda

sudo apt-get install tilda

then run tilda

you should see a config in gui, i would not check any of the window display options, set the appearance to your liking, if you want to be able to open tilda multiple times i *would* run the command tilda again, then set another config the same as your last one, do this as many times as you think you would ever have tilda open, i set mine 4 times for each of my work spaces

and i just saved you a few minutes of figuring out tilda, the config option itself on the command line is "tilda -C" your first config file will be saved in /home/user/.tilda/ as config_0 once you do have the config open it should display which config you do have open so you dont get confused

---

### Post by lamnk on 2008-02-03
> **RavUn said:**
> Could anyone help me adjust the size and position of the terminal on the background?

I've messed with the geometry settings and gone up and down with the numbers but it seems to jump around without any rhyme or reason.

I assumed +50+50 meant it goes right and down 50 but I was wrong...
Right now I have it as 800x964 and +50+50 but it just goes to the top right corner and takes up a quarter of the screen.

I'm trying to make it come out about an inch from the left and go all the way up and down.  Can anyone explain what I'd need to do?

I had the same problem, reinstalling devilspie solved it :) Strange, no ?

---

### Post by Mary.Riley on 2008-02-03
That's a really cool trick. Thanks for the help...

---

### Post by Jojan on 2008-02-08
Great guide. :)

But I have a problem (maybe not be caused by devilspie but still...). When I use the action key to focus on desktop the desktop terminal too disapears. How do I make so that it does not?

Edit: I also noticed that I used "set_workspace 4" but got it on workspace 1. And if I set more workspaces, no difference is happening.

---

### Post by kmullinax on 2008-02-12
Ok, I tried to do this last night, but it didn't work so well.
First, the geometry wasn't working correctly.  In retrospect I think I figured out why by reading this entire thread, but anyway like a number of other people, the window was about 1/4 the size of the screen.  While there were no borders or anything, my emerald theme caused there to be a glowing shadow where the border would have been.

Strangely enough, a glowing border also appeared around my entire screen, outlining the bottom of the appbar at the top of the screen, both sides of the screen, and the top of the appbar at the bottom of the screen.  ALSO, for some reason, the right-click context menu no longer appeared when I clicked on the background.  It was as if there were two copies of terminal running... one that I could type in that was small and to the upper left, and another that filled the whole usable screen area and kept me from being able to click on the desktop.

Anyway, I figured I would play with it this weekend, so for the time being, I removed devilspie, deleted the two startup commands from Sessions, deleted the DesktopConsole.ds file, and removed the devilspie directory.  Then I went into the System Monitor and shut down both running services and rebooted.

I'm still having the same problem!  devilspie is gone, and neither sevice is running, but I have the glowing border around my entire desktop and right-clicking the desktop does nothing.
Anyone know how this happened or how I can fix it??

---

### Post by defenestratos on 2008-02-13
> **Johnnyboyct said:**
> I have it working, thanks alot, the howto worked well enough to get me to make it work lol...

Anyways, I have it working, but no matter what i do, it goes in workspace 1, also, if I change the size, it shows the titlebar and frame around the window. Am I doing something wrong.

Thanks I love it :)

How did you get it working? I got the borders and it is just small even though I adjusted the resolution to my screen... If that is what geometry is.

---

### Post by mozetti on 2008-02-13
If you have Compiz working, I just wrote a how-to to accomplish this without using devilspie.

[http://ubuntuforums.org/showthread.php?t=694936](http://ubuntuforums.org/showthread.php?t=694936)

---

### Post by chris4585 on 2008-02-14
this is a great howto, i've been putting off doing it but i like how it came out over all 

[IMG]http://i25.tinypic.com/29xfdvr.png[/IMG]

---

### Post by alanhaggai on 2008-02-14
Worked well! Now the desktop is more useful and attractive. Thank you very much. :-D

---

### Post by chochem on 2008-02-22
I just wanted to add that this trick can be easily adapted to the Xfce4 terminal. Sadly, xfce4-terminal doesn't do profiles, but most of the necessary settings can be run as arguments, e.g.
```
xfce4-terminal --hide-menubar --hide-borders --hide-toolbars --title=descon &
```
though some will have to be set as permanent (e.g. colour/transparency settings)
I'm having trouble with getting devilspie to work and to load before the terminal (xfce4 autostart applications really need a workover) so I can recommend using *wmctrl* (that's the name of the package as well) instead (basically it does the same as devilspie, just post festum). It has got way better documentation and a simpler syntax, too.

Having experimented a bit with this, I got the best results, running the whole thing as a single command line (if you're unfamiliar with the syntax, the &&'s wait for the former command to exit succesfully before starting the next command). 

```
#! /bin/bash

xfce4-terminal --hide-menubar --hide-borders --hide-toolbars --title=descon && sleep 0.1 && wmctrl -r descon -e 0,10,10,720,720 && sleep 0.1 && wmctrl -r descon -b add,sticky,below && sleep 0.1 && wmctrl -r descon -b add,skip_pager,skip_taskbar
```

(the sleep intermezzos which causes the shell to wait for 0.1 seconds before continuing can probably be cut - more sort of a superstittion thing, I guess :) )

wmctrl runs with various arguments: "-r descon" identifies the window (see the --title argument in the terminal-command) to be targeted. "-e [numbers]" is the geometry bit (0 for 'gravity'; 10,10 for upper left coordinate; 720,720 for width-height). "-b [action],[property]" is for changing properties of the window targeted, in this case we tell it to add the sticky quality (reappering on all workspaces), the below quality (stays below other windows even when focused), and tell it not to show up in the pager (showing workspaces) or the taskbar.

Save the above line as a script and make it executable. One strange thing to notice: This script/line has somehow to be run from a terminal itself (at least in xfce). Depending on how you want to run it, you can add a launcher to the panel and click 'run in terminal' or you can have it start up by adding it to autostarted applications. If the script is /usr/local/bin/descon, add an autostarted application with the following command: "xfce4-terminal -x /usr/local/bin/descon" which will fire up a terminal, run the script in that, and close down the 'launching terminal' in a splitsecond.

---

### Post by Placified on 2008-02-26
I had a bit of trouble with it but in the end got it working.  It seems that putting it (below) puts it below everything including your desktop if you have any further layers behind it.  for those running the desktop cube with the dome there are.  so I tried a few things and this is how it worked for me.

(if
        (matches (window_name) "DesktopConsole")
        (begin
                (pin)
                (undecorate)
                (skip_pager)
                (skip_tasklist)
                (wintype "utility")
                (center)
        )
)

here are pictures of my terminal settings, alot of you were having the same problem I was with the title bar and stuff the person that posted this left some settings out.

[IMG]http://img.photobucket.com/albums/v430/Mattfoder/Screenshot-2.png[/IMG]

[IMG]http://img.photobucket.com/albums/v430/Mattfoder/Screenshot1.png[/IMG]

[IMG]http://img.photobucket.com/albums/v430/Mattfoder/Screenshot-1.png[/IMG]

[IMG]http://img.photobucket.com/albums/v430/Mattfoder/Screenshot.png[/IMG]
 the default size was fine for me so I took out the res and just told it to center.  I also didnt specify below or above.  If you specify above it's above everything; and if you specify below it's below your desktop and now you cant see you desktop because attention is on you console behind it.  this worked for me and I think it may have been the problem for the couple of other people who could not get it to work. only thing I would like to know is how to specify what layer to put it on and what layer the desktop is.  I read thru the wiki and saw something called veiwpoint but everytime I tried it it was like putting it on the bottom. any thoughts from some more experianced people

---

### Post by Techwiz on 2008-03-11
a fix for some of the problems at the beginning of the thread is to set the wintype to "dock".

---

### Post by joshrobinson on 2008-03-11
i did the same thing, but in a different way (one that requires compiz), i used the following tutorial

[http://www.ubuntu-unleashed.com/2007/08/howto-completely-transparent-shell-on.html]("http://www.ubuntu-unleashed.com/2007/08/howto-completely-transparent-shell-on.html")

and heres what it looks like on my laptop

[http://www.ruins-edge.com/screenshot2.png]("http://www.ruins-edge.com/screenshot2.png")

id post the image in this thread, but its 1280x800

---

### Post by LinuX-M@n1@k on 2008-04-02
awesome! look at my desktop now :D i have 5 terminals on the background! thanks a lot for that thread!
[ATTACH]64662[/ATTACH]

---

### Post by Shingo [fw] on 2008-04-15
I can't get this work correctly.

(if
(matches (window_name) "DesktopConsole")
(begin
(geometry "400x400+50+50")
(stick)
(below)
(undecorate)
(skip_pager)
(skip_tasklist)
(wintype "utility")
)
)

With this code terminal window is resized but always placed at the left top corner. I tried many configurations. Only command (center) moves the window.

---

### Post by Rigrig on 2008-04-22
I'm also having trouble with moving the window, using ```
(geometry "800x700+150+100")
``` resizes the window fine, but it doesn't move.
The work-around I found is specifying the geometry at the start of gnome-terminal:
```
/usr/bin/gnome-terminal **--geometry=+150+100** --window-with-profile=DesktopConsole
```

---

### Post by love2learn on 2008-04-30
> **em3raldxiii said:**
> This is pretty cool.  But I prefer using a program called Yakuake.  It's a drop-down terminal that is reminiscent of the Quake or HL terminal.  Mine's configured to use the F12 key, but I believe you can change it to use the ~ key that many of us are familar with.  The dropdown terminal is also configurable to be dark, lose the scrollbars, and a different height-width.  It's super handy, especially when entering commands from the forums.  

```
sudo apt-get install yakuake
```I am not sure which repository it's in though ... one of the universes I think.  Perhaps multiverse or PLF.



AMAZING, sorry for caps but i am so excited. Thanks for thread crapping, this is the way to do cli imho.

---

### Post by boob11 on 2008-05-08
[thnx]("http://tech-rantings.blogspot.com/2007/09/must-have-applications-on-ubuntu-linux.html")

---

### Post by SkonesMickLoud on 2008-05-08
> **gamerteck said:**
> Also gnome-terminal --window-with-profile=YourFilename will always show before devilspie in the Startup Programs.

Not if you name it differently.  I have devilspie named as "Devilspie", and the terminal named "zClearTerminal".  The commands stay the same, only the name changes.

---

### Post by Vasto on 2008-05-27
> **joshrobinson said:**
> i did the same thing, but in a different way (one that requires compiz), i used the following tutorial

[http://www.ubuntu-unleashed.com/2007/08/howto-completely-transparent-shell-on.html]("http://www.ubuntu-unleashed.com/2007/08/howto-completely-transparent-shell-on.html")

Thank you! The updated guide is [here](http://ubuntuforums.org/showthread.php?p=3254093)

---

### Post by murlosad on 2008-06-22
Don't know if anyone is still reading this thread, but thanks for all the help. I got this up and running, and now have a nice term on my desktop. Here it is running rtorrent (which is what it's usually doing).

I couldn't figure out the geometry, so I just centered the window and adjusted the size in the command line. Since Devilspie just looks for a window with the DesktopConsole title, I am actually using aterm. this is the command I used: 

```

aterm +sb -tr -rv -sh 70 -g 115x36 -title DesktopConsole

```

Oh and the main reason for this post: I found a gui for setting up devilspie it's called [**_gdevilspie_**]("http://code.google.com/p/gdevilspie/wiki/gDevilspie") and there is a .deb for hardy on the site. It does make it easier to setup the config file.

Hope this helps someone else too.

---

### Post by SkonesMickLoud on 2008-06-28
I've been trying for hours to get twin terminals to no avail.  Devilspie takes control of the geometry and places both in the upper left corner of my screen, even though geometry isn't specified in the .ds but rather in the startup line of the terminal itself.

Is there any way to prevent Devilspie from doing this?

I'd post what code I had, but I've since deleted it trying to get the single terminal back.

I copied [this post](http://ubuntuforums.org/showpost.php?p=4025878&postcount=137) almost word for word, and I still have no control over the placement of the second terminal.

---

### Post by victorgreen on 2008-07-15
How did everyone solve the 

> :~$ devilspie

** (devilspie:15451): WARNING **: Error in parsing: Unexpected token encountered: 226
Cannot parse /home/me/.devilspie/DesktopConsole.ds: Unexpected token encountered: 226
No s-expressions loaded, quiting



issue??

The gnome profile is fine, the config file seems fine

> (if
	(matches (window_name) “DesktopConsole”)
	(begin
		(stick)
		(below)
		(undecorate)
		(skip_pager)
		(skip_tasklist)
		(wintype “utility”)
		(geometry “+240+250&#8243;)
		(geometry “954×680&#8243;)
	)	
)

Its just that devilspie wont load correctly [Ubuntu 8.04 64, no compiz running]

---

### Post by victorgreen on 2008-07-15
I was dumb. Apparently if you copy paste the .ds config files it copies some extra encoding characters that you cant really find easily. The way to to get around this is simply to type out the whole config file yourself. Then it worked...

---

### Post by kk0sse54 on 2008-07-15
If you ever want to embed a terminal in your desktop you don't need devilspie or any extra programs just use compiz window rules using as much or as little transparency as you want. I believe i used this link to embed the terminal in my desktop [http://www.ubuntu-unleashed.com/2007/08/howto-completely-transparent-shell-on.html](http://www.ubuntu-unleashed.com/2007/08/howto-completely-transparent-shell-on.html)

---

### Post by victorgreen on 2008-07-16
C!oud-- I believe this thread was to show people how to run a terminal as background if they didnt have compiz. There's plenty of reasons not to between bad driver support, stability issues, the fact that on laptops compiz just sucks too many watts, and older hardware not running the effects well, many of us cant/dont run it and still want an awesome terminal background.

---

### Post by cdtech on 2008-07-16
I agree, although I've been using mine with compiz with no issues. Now I can't do without my desktop terminal.

[ATTACH]77946[/ATTACH]

---

### Post by kk0sse54 on 2008-07-17
> **victorgreen said:**
> C!oud-- I believe this thread was to show people how to run a terminal as background if they didnt have compiz. There's plenty of reasons not to between bad driver support, stability issues, the fact that on laptops compiz just sucks too many watts, and older hardware not running the effects well, many of us cant/dont run it and still want an awesome terminal background.

Was just putting it out there for those who do run compiz since I find it an easier approach although I am well aware of the reasons not to run compiz as I myself prefer not to run it or gnome instead I like openbox.

---

### Post by blazercist on 2008-07-17
> **joshrobinson said:**
> i did the same thing, but in a different way (one that requires compiz), i used the following tutorial

[http://www.ubuntu-unleashed.com/2007/08/howto-completely-transparent-shell-on.html]("http://www.ubuntu-unleashed.com/2007/08/howto-completely-transparent-shell-on.html")

and heres what it looks like on my laptop

[http://www.ruins-edge.com/screenshot2.png]("http://www.ruins-edge.com/screenshot2.png")

id post the image in this thread, but its 1280x800

Using this method worked for me consistantly and easily.  Thanks.

---

### Post by moocher on 2008-08-11
I've found a problem that I haven't noticed when skimming this topic. On startup the terminal always loads with the right profile, but that's all. Devilspie doesn't seem to do anything, I've tried changing their order it still ignored everything other than the profile. So I tried cutting Devilspie out of the equation, and just wrote a startup command that had the right position and size (ignoring the other effects that actually make this embedded) but still to no avail. The commands work fine in terminal, and I made a launcher to check it, which launches fine. But the startup command still doesn't work. Anyone know why this might be happening?

---

### Post by cdtech on 2008-08-11
What start up command are you using?

---

### Post by moocher on 2008-08-13
gnome-terminal --window-with-profile=DesktopConsole --working-directory=/home/alex/Desktop --geometry=95x51+0+0
I'm sure there's just a small problem, but I don't know what.

---

### Post by ex.hav0k on 2008-08-16
i'm having similar problems with the startup.  i tried adding devilspie and gnome-terminal --window-with-profile=DesktopConsole as different startup items, but that didn't work.  so i tried to do 'devilspie & gnome-terminal --window-with-profile=DesktopConsole' and that didn't work either.  i've gotten the terminal to work on my desktop by running gnome-terminal --window-with-profile=DesktopConsole from another terminal with devilspie already running, but i can't figure out why it won't work on startup.  any ideas?

---

### Post by heiNey on 2008-08-20
got this working...thanks!

but got a question...how do i switch back to the terminal without minimizing every other window first?  normally i would alt+tab, but it doesnt appear on the window list anymore.

---

### Post by El_Belgicano on 2008-08-20
> **heiNey said:**
> got this working...thanks!

but got a question...how do i switch back to the terminal without minimizing every other window first?  normally i would alt+tab, but it doesnt appear on the window list anymore.

Just need to minimize all windows...

---

### Post by heiNey on 2008-08-20
so that's the only way?  cant set up a keyboard shortcut or something to switch to it immediately?

---

### Post by El_Belgicano on 2008-08-20
> **heiNey said:**
> so that's the only way?  cant set up a keyboard shortcut or something to switch to it immediately?

I don't know, if there's another way ...
of course you can do that to minimize all windows... I don't use that much windows at one time so I just minimize them ...

---

### Post by chemando on 2008-09-01
When I save a file to my desktop the icon is always placed underneath the terminal.  Is there anyway to get the icons to be placed outside the boundaries of the terminal?

---

### Post by Lord C on 2008-09-23
Thanks for the guide.

I used gdevilspie for quick reloading/editing while I was trying to get the geometry correct.

Starting up didn't work as suggested (window always had borders), so I just put the commands into one of my present startup scripts...

devilspie &
gnome-terminal --window-with-profile=DesktopConsole &

---

### Post by bartos on 2008-10-03
Here is my setup. Because of my shorter panel bar so I can see ram and cpu details with conky above any windows. I had to set my terminal into the middle of my desktop.This terminal is only for running [email]Folding@Home.The[/email] geometry is in the startup entry as the terminal would end up under conky a bit no matter what number was put in for geometry.

Session Startup Entry 
```
gnome-terminal --geometry=50x15+500+50 --window-with-profile=DesktopConsole
```

DesktopConsole.ds
```
(if
        (matches (window_name) "DesktopConsole")
        (begin
                (set_workspace 2)
                (below)
                (undecorate)
                (skip_pager)
                (skip_tasklist)
                (wintype "utility")
        )
)

```

Hope this gives others ideas and any help.:D
The screenshots also show the width and length of terminal.

---

### Post by caseymadaline on 2008-10-03
How to create comments in .ds code file? I can't find it in the wiki. Thanks

---

### Post by bartos on 2008-10-03
> **caseymadaline said:**
> How to create comments in .ds code file? I can't find it in the wiki. Thanks

nano ~/.devilspie/DesktopConsole.ds

:D

---

### Post by jastonas on 2008-11-03
Using this tutorial will only affect the 4th workspace?

---

### Post by mytik on 2008-11-03
Hi there, I have a problem with this tutorial, I followed this correctly but it always shows the window border with close maximize etc...

what can be wrong?

Thanks

---

### Post by LouisZepher on 2008-11-03
> **greenstar said:**
> I just installed tilda: ```
sudo apt-get install tilda
```Tilda does the same thing without the script. It can be configured to look the same. Pseudo-transparent background, no borders, custom size & screen location, visible on any workspace you choose, don't show on taskbar, etc.

I use tilda on Workspace 2, other stuff on Workspace 1. Screenshot below.

Greenstar
I was going to suggest the same thing. ^.^;  Been using Tilda as my main terminal app since first switching to Ubuntu earlier this year, and I swear by it.

---

### Post by Jean-DrEaD on 2008-11-05
> **mytik said:**
> Hi there, I'm a problem with this tutorial, I followed this correctly but it always shows the window border with close maximize etc...

what can be wrong?

Thanks

same here... :(

---

### Post by m3tatr0n on 2008-11-09
Hello.  I'm trying to do this in Fedora 8.  Everything seemed to be the same as with Ubuntu.  The only thing I changed was instead of (set_workspace 4), I used (pin) to make it available on all my workspaces.  
For step 5 I went to Sytem>Personal>Sessions and added devilspie in the Startup Programs tab with command /usr/bin. Then I added gnome terminal --window-with-profile=DesktopConsole and put /usr/bin for command.
I logged out and logged back in and no embedded console. I've tried playing around with everything and I can't figure out what I did wrong. Did anyone do anything differently, or did I screw up somewhere? One thing I noticed, is that when I try to find the DesktopConsole config file I can't find it anywhere.
Thanks.

---

### Post by frodon on 2008-11-11
I have problem with this under intrepid, the below command doesn't seem to do a good job anymore for me.

Will keep you updated if i find a solution.

Update: The only thing that is different in intrepid is that opening a new terminal makes the new terminal always below the embedded terminal which was not the case in hardy and which is as you guess annoying.
Except this point i confirm that this method works for intrepid ibex.

If any of you is running tis on intrepid please share your experience.

---

### Post by amauk on 2008-11-18
> **frodon said:**
> If any of you is running tis on intrepid please share your experience.

In the gnome-terminal profile preferences,
under the "Title and Command" tab
change the initial title to something unique
(I use "Terminal - DesktopConsole")

and select "Keep initial title"

in the devilspie .ds file,
change
```
(matches (window_name) "DesktopConsole")

```
to
```
(is (window_name) "Terminal - DesktopConsole")

```

---

### Post by ajay.cse.nitjsr on 2008-12-03
now you can put a wallpaper on ur ubuntu terminal by following few steps
no need to install any extra softwares
follow :
   Terminal-> Edit-> Profile->New -> Create ->Background ->Background Images


now select ur image and set transparency finally close .
  


be coolllllllllll   ):P   ):P

---

### Post by frodon on 2008-12-03
Unfortunately the devilspie behaviour is a bit different on intrepid, all is fine if i don't open another terminal but if i do then my desktop terminal don't stay behind like it was used to since i use this trick (dapper).

I guess i just have to live with this.

---

### Post by feriender on 2008-12-30
you may experience problems if you're using Compiz-fusion (terminal appears in new window instead of background). 
To solve it, the original devilspie configuration file (~/.devilspie/DesktopConsole.ds) should be modified as follows: (the line: "(set_workspace 4)" was deleted)
```

(if
        (matches (window_name) "DesktopConsole")
        (begin
                (below)
                (undecorate)
                (skip_pager)
                (skip_tasklist)
                (wintype "utility")
                (geometry "+100+100")
                (geometry "924x668")
        )
)

```

because compiz has different workspace naming.
Thus your terminal will appear on the first workspace.

An other small correction should be done on gnome-terminal's profile setting. On the "Title and Command" tab, set the initial title to "DesktopConsole" - corresponding your configuration file, and let gnome-commander to keep the initial title.

---

### Post by dannytatom on 2009-01-03
Err, it works but I have a problem and question.

1) If I open a window from the terminal (wether with gedit, clicking a link in irc, etc) it doesn't have a titlebar.

2)  Is there a way to not show the tabs?  I still want ot use tabs, but not see the actual *tabs* at the top, as I go through 'em with alt+1, alt+2, etc anyway.

Also, now all of a sudden (I think it only started happening after doing this), If I grab a side of any window I can stretch it to go under the panel.  Moving it around won't do it, just resizing.  Not a big deal, but weird nonetheless.

---

### Post by lukjad on 2009-01-07
I gotta try this. :D

---

### Post by Masterofpsi on 2009-01-08
I tried this topic out and had some trouble with it. However, I have found a configuration set that works perfectly, at least for me:

**FIRST:** In gnome-terminal, under Edit>Profiles>DesktopConsole, in the "Title and Command" tab, in the field "Initial Title:" you should enter the text "DesktopConsole". Under the next drop-down menu, you should select "Keep initial title."
 
(This is on the off-chance that you have devilspie set to check all open windows when it starts up, kill devilspie during a session, and start it back up while you have something else--say, nano--open.)

**SECOND:** The devilspie config should look like this:

```

(if (matches (window_name) "DesktopConsole")
    (begin
        (maximize)
        (stick)
        (below)
        (undecorate)
        (skip_pager)
        (skip_tasklist)
        (wintype "desktop")
    )
)

```

The code now maximizes the window before sticking it, and then declares it a desktop type, which should get rid of the problems people have had when opening new terminals and should also keep it up when "show desktop" is pressed.

**THIRD:** In the startup list, devilspie and gnome-terminal should be named so that gnome-terminal follows devilspie alphabetically. I can't figure out how to get them to run at the same time, but that should do the trick. (I could be wrong on this one.)

---

### Post by Jammanuser on 2009-01-08
> **em3raldxiii said:**
> This is pretty cool.  But I prefer using a program called Yakuake.  It's a drop-down terminal that is reminiscent of the Quake or HL terminal.  Mine's configured to use the F12 key, but I believe you can change it to use the ~ key that many of us are familar with.  The dropdown terminal is also configurable to be dark, lose the scrollbars, and a different height-width.  It's super handy, especially when entering commands from the forums.  

```
sudo apt-get install yakuake
```

I am not sure which repository it's in though ... one of the universes I think.  Perhaps multiverse or PLF.

I was unable to install yakuake, with either synaptic or apt-get...:( It said it was unable to "retrieve" or something the URL path (it actually mentioned the **exact** URL, but i can't recall the specifics right now, because i'm in XP, and i need to be in Ubuntu). I even tried adding the specific URL in the repositories, but got some kind of error saying the repository was not able to be added because blah, blah, blah! :( Again, i can't recall the exact error message, and i know that that it isn't very helpful. i will try it again, to obtain the necessary information, which i will later post.

Cheers! :D

-Jam man

:guitar:

---

### Post by ashsmith on 2009-01-08
> **jinacio said:**
> The objective is to have a gnome terminal running as the desktop background, right above the actual background image, that won't be displayed by the statusbar or ticker.



This is great! Thanks for this wonderful tutorial..

---

### Post by Jammanuser on 2009-01-09
Ok, so here is the full output that I got when I tried using apt-get to install yakuake:
```

Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
The following packages were automatically installed and are no longer required: 
  ocaml-base-nox 
Use 'apt-get autoremove' to remove them. 
The following extra packages will be installed: 
  kde-icons-oxygen kdebase-runtime kdebase-runtime-bin-kde4 
  kdebase-runtime-data kdebase-runtime-data-common kdelibs-bin kdelibs5 
  kdelibs5-data khelpcenter4 konsole libclucene0ldbl libphonon4 libpq5 
  libqt4-opengl libqt4-svg libraptor1 librasqal0 librdf0 libsoprano4 
  libstreamanalyzer0 libstreams0 libstrigiqtdbusclient0 phonon 
  phonon-backend-gstreamer raptor-utils redland-utils soprano-daemon 
Suggested packages: 
  kdebase phonon-backend-xine phonon-backend-vlc phonon-backend-mplayer 
The following NEW packages will be installed: 
  kde-icons-oxygen kdebase-runtime kdebase-runtime-bin-kde4 
  kdebase-runtime-data kdebase-runtime-data-common kdelibs-bin kdelibs5 
  kdelibs5-data khelpcenter4 konsole libclucene0ldbl libphonon4 libpq5 
  libqt4-opengl libqt4-svg libraptor1 librasqal0 librdf0 libsoprano4 
  libstreamanalyzer0 libstreams0 libstrigiqtdbusclient0 phonon 
  phonon-backend-gstreamer raptor-utils redland-utils soprano-daemon yakuake 
0 upgraded, 28 newly installed, 0 to remove and 0 not upgraded. 
Need to get 38.4MB of archives. 
After this operation, 109MB of additional disk space will be used. 
Do you want to continue [Y/n]? y 
WARNING: The following packages cannot be authenticated! 
  kde-icons-oxygen libphonon4 libqt4-svg libclucene0ldbl libraptor1 libpq5 
  librasqal0 librdf0 soprano-daemon libsoprano4 libstreams0 libstreamanalyzer0 
  libqt4-opengl phonon-backend-gstreamer phonon kdelibs5-data kdelibs-bin 
  kdelibs5 libstrigiqtdbusclient0 kdebase-runtime-bin-kde4 
  kdebase-runtime-data-common kdebase-runtime-data kdebase-runtime 
  khelpcenter4 konsole raptor-utils redland-utils yakuake 
Install these packages without verification [y/N]? y 
Err http://us.archive.ubuntu.com intrepid-updates/main kde-icons-oxygen 4:4.1.3-0ubuntu1~intrepid1 
  302 Redirect [IP: 91.189.88.31 80] 
Err http://us.archive.ubuntu.com intrepid/main libphonon4 4:4.2.0-0ubuntu1 
  302 Redirect [IP: 91.189.88.31 80] 
Err http://us.archive.ubuntu.com intrepid-updates/main libqt4-svg 4.4.3-0ubuntu1.1 
  302 Redirect [IP: 91.189.88.31 80] 
Err http://us.archive.ubuntu.com intrepid/main libclucene0ldbl 0.9.20-3 
  302 Redirect [IP: 91.189.88.31 80] 
Err http://us.archive.ubuntu.com intrepid/main libraptor1 1.4.17-1 
  302 Redirect [IP: 91.189.88.31 80] 
Err http://us.archive.ubuntu.com intrepid-updates/main libpq5 8.3.5-0ubuntu8.10 
  302 Redirect [IP: 91.189.88.31 80] 
Err http://us.archive.ubuntu.com intrepid/main librasqal0 0.9.15-2 
  302 Redirect [IP: 91.189.88.31 80] 
Err http://us.archive.ubuntu.com intrepid/main librdf0 1.0.7-1 
  302 Redirect [IP: 91.189.88.31 80] 
Err http://us.archive.ubuntu.com intrepid/main soprano-daemon 2.1.1+dfsg.1-0ubuntu1 
  302 Redirect [IP: 91.189.88.31 80] 
Err http://us.archive.ubuntu.com intrepid/main libsoprano4 2.1.1+dfsg.1-0ubuntu1 
  302 Redirect [IP: 91.189.88.31 80] 
Err http://us.archive.ubuntu.com intrepid/main libstreams0 0.5.11-1ubuntu2 
  302 Redirect [IP: 91.189.88.31 80] 
Err http://us.archive.ubuntu.com intrepid/main libstreamanalyzer0 0.5.11-1ubuntu2 
  302 Redirect [IP: 91.189.88.31 80] 
Err http://us.archive.ubuntu.com intrepid-updates/main libqt4-opengl 4.4.3-0ubuntu1.1 
  302 Redirect [IP: 91.189.88.31 80] 
Err http://us.archive.ubuntu.com intrepid/main phonon-backend-gstreamer 4:4.2.0-0ubuntu1 
  302 Redirect [IP: 91.189.88.31 80] 
Err http://us.archive.ubuntu.com intrepid/main phonon 4:4.2.0-0ubuntu1 
  302 Redirect [IP: 91.189.88.31 80] 
Err http://us.archive.ubuntu.com intrepid-updates/main kdelibs5-data 4:4.1.3-0ubuntu1~intrepid4 
  302 Redirect [IP: 91.189.88.31 80] 
Err http://us.archive.ubuntu.com intrepid-updates/main kdelibs-bin 4:4.1.3-0ubuntu1~intrepid4 
  302 Redirect [IP: 91.189.88.31 80] 
Err http://us.archive.ubuntu.com intrepid-updates/main kdelibs5 4:4.1.3-0ubuntu1~intrepid4 
  302 Redirect [IP: 91.189.88.31 80] 
Err http://us.archive.ubuntu.com intrepid/main libstrigiqtdbusclient0 0.5.11-1ubuntu2 
  302 Redirect [IP: 91.189.88.31 80] 
Err http://us.archive.ubuntu.com intrepid-updates/main kdebase-runtime-bin-kde4 4:4.1.3-0ubuntu1~intrepid1 
  302 Redirect [IP: 91.189.88.31 80] 
Err http://us.archive.ubuntu.com intrepid-updates/main kdebase-runtime-data-common 4:4.1.3-0ubuntu1~intrepid1 
  302 Redirect [IP: 91.189.88.31 80] 
Err http://us.archive.ubuntu.com intrepid-updates/main kdebase-runtime-data 4:4.1.3-0ubuntu1~intrepid1 
  302 Redirect [IP: 91.189.88.31 80] 
Err http://us.archive.ubuntu.com intrepid-updates/main kdebase-runtime 4:4.1.3-0ubuntu1~intrepid1 
  302 Redirect [IP: 91.189.88.31 80] 
Err http://us.archive.ubuntu.com intrepid-updates/main khelpcenter4 4:4.1.3-0ubuntu1~intrepid1 
  302 Redirect [IP: 91.189.88.31 80] 
Err http://us.archive.ubuntu.com intrepid-updates/main konsole 4:4.1.3-0ubuntu1~intrepid1 
  302 Redirect [IP: 91.189.88.31 80] 
Err http://us.archive.ubuntu.com intrepid/main raptor-utils 1.4.17-1 
  302 Redirect [IP: 91.189.88.31 80] 
Err http://us.archive.ubuntu.com intrepid/main redland-utils 1.0.7-1 
  302 Redirect [IP: 91.189.88.31 80] 
Err http://us.archive.ubuntu.com intrepid/universe yakuake 2.9.3-0ubuntu1 
  302 Redirect [IP: 91.189.88.31 80] 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-runtime/kde-icons-oxygen_4.1.3-0ubuntu1~intrepid1_all.deb  302 Redirect [IP: 91.189.88.31 80] 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/phonon/libphonon4_4.2.0-0ubuntu1_amd64.deb  302 Redirect [IP: 91.189.88.31 80] 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-svg_4.4.3-0ubuntu1.1_amd64.deb  302 Redirect [IP: 91.189.88.31 80] 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/clucene-core/libclucene0ldbl_0.9.20-3_amd64.deb  302 Redirect [IP: 91.189.88.31 80] 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/r/raptor/libraptor1_1.4.17-1_amd64.deb  302 Redirect [IP: 91.189.88.31 80] 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/postgresql-8.3/libpq5_8.3.5-0ubuntu8.10_amd64.deb  302 Redirect [IP: 91.189.88.31 80] 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/r/rasqal/librasqal0_0.9.15-2_amd64.deb  302 Redirect [IP: 91.189.88.31 80] 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/r/redland/librdf0_1.0.7-1_amd64.deb  302 Redirect [IP: 91.189.88.31 80] 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/soprano/soprano-daemon_2.1.1+dfsg.1-0ubuntu1_amd64.deb  302 Redirect [IP: 91.189.88.31 80] 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/soprano/libsoprano4_2.1.1+dfsg.1-0ubuntu1_amd64.deb  302 Redirect [IP: 91.189.88.31 80] 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/strigi/libstreams0_0.5.11-1ubuntu2_amd64.deb  302 Redirect [IP: 91.189.88.31 80] 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/strigi/libstreamanalyzer0_0.5.11-1ubuntu2_amd64.deb  302 Redirect [IP: 91.189.88.31 80] 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-opengl_4.4.3-0ubuntu1.1_amd64.deb  302 Redirect [IP: 91.189.88.31 80] 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/phonon/phonon-backend-gstreamer_4.2.0-0ubuntu1_amd64.deb  302 Redirect [IP: 91.189.88.31 80] 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/phonon/phonon_4.2.0-0ubuntu1_all.deb  302 Redirect [IP: 91.189.88.31 80] 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs5-data_4.1.3-0ubuntu1~intrepid4_all.deb  302 Redirect [IP: 91.189.88.31 80] 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs-bin_4.1.3-0ubuntu1~intrepid4_amd64.deb  302 Redirect [IP: 91.189.88.31 80] 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs5_4.1.3-0ubuntu1~intrepid4_amd64.deb  302 Redirect [IP: 91.189.88.31 80] 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/strigi/libstrigiqtdbusclient0_0.5.11-1ubuntu2_amd64.deb  302 Redirect [IP: 91.189.88.31 80] 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-runtime/kdebase-runtime-bin-kde4_4.1.3-0ubuntu1~intrepid1_amd64.deb  302 Redirect [IP: 91.189.88.31 80] 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-runtime/kdebase-runtime-data-common_4.1.3-0ubuntu1~intrepid1_all.deb  302 Redirect [IP: 91.189.88.31 80] 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-runtime/kdebase-runtime-data_4.1.3-0ubuntu1~intrepid1_all.deb  302 Redirect [IP: 91.189.88.31 80] 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-runtime/kdebase-runtime_4.1.3-0ubuntu1~intrepid1_amd64.deb  302 Redirect [IP: 91.189.88.31 80] 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-runtime/khelpcenter4_4.1.3-0ubuntu1~intrepid1_amd64.deb  302 Redirect [IP: 91.189.88.31 80] 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/konsole_4.1.3-0ubuntu1~intrepid1_amd64.deb  302 Redirect [IP: 91.189.88.31 80] 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/r/raptor/raptor-utils_1.4.17-1_amd64.deb  302 Redirect [IP: 91.189.88.31 80] 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/r/redland/redland-utils_1.0.7-1_amd64.deb  302 Redirect [IP: 91.189.88.31 80] 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/y/yakuake/yakuake_2.9.3-0ubuntu1_amd64.deb  302 Redirect [IP: 91.189.88.31 80] 
E: Unable to fetch some archives, maybe run apt-get update or try with –fix-missing? 
```

And here is what happens when I try adding the following APT line in my repositories: 
```
deb http://us.archive/ubuntu.com/ubuntu/intrepid main
```

I get the following error message:
> 
Could not download all repository indexes 

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

And then another error, after I close that dialog box:
> 
E: Malformed line 46 in source list /etc/apt/sources.list (dist parse) 
E: Unable to lock the list directory
And then another one:
> 
E: Malformed line 46 in source list /etc/apt/sources.list (dist parse) 
E: The list of sources could not be read. 
Go to the repository dialog to correct the problem. 
E: _cache->open() failed, please report.
And here is what I get in my terminal, after trying to install yakuake, after adding that source:
> 
~$ sudo apt-get install yakuake 
E: Malformed line 46 in source list /etc/apt/sources.list (dist parse) 
E: The list of sources could not be read. 
As you can see, it is the same as one of the errors (specifically the second one) that I got in synaptic, after adding that line to the repositories. 

I have also tried adding the exact address mentioned in the terminal output above, but had no better luck...each time I do this, I make sure to remove the line again, so it is now gone again, in case you're wondering. 

So can anyone please tell me what is my problem, and what can be done to fix it?

Thanks in advance!

-Jam man

:guitar:

---

### Post by boob11 on 2009-01-14
tnx

---

### Post by r4z0rw0lf on 2009-01-17
i simply cannot do this. every time i try and log out and log back in the desktop  does not have a terminal embedded in it i have checked all of my workspaces andnone of them have it. could someone PLEASe help? is it because i have *Intrepid Ibex*???

---

### Post by macvr on 2009-01-19
> **Masterofpsi said:**
> 
```

(if (matches (window_name) "DesktopConsole")
    (begin
        (maximize)
        (stick)
        (below)
        (undecorate)
        (skip_pager)
        (skip_tasklist)
        (wintype "desktop")
    )
)

```

The code now maximizes the window before sticking it, and then declares it a desktop type, which should get rid of the problems people have had when opening new terminals and should also keep it up when "show desktop" is pressed.

^^^well if this is done then _u cant access any desktop icons!!!_

this works for me ... but the show desktop makes it disappear!
```
( if 
( and 
( is ( window_name ) "DesktopConsole" )
) 
( begin 
( undecorate )
( skip_pager )
( skip_tasklist )
( stick )
( geometry "843x783+126+24" )
( below )
( println "match" )
)
)
```

but i think TILDA works better, and does the job well...

---

### Post by eatberrys on 2009-01-19
Very nice tutorial!

---

### Post by ilyaostr on 2009-02-28
@OP: Thanks for this, it worked out brilliantly :)

> **.exe said:**
> I can't get this to work. No matter what I do, gnome-terminal --window-with-profile=DesktopConsole  ALWAYS appears in front of devilspie. NO matter what order I enter them in, or what I do after I enter them. Is there a text file that I can edit manually instead?

What I did, is, I made a shell script with the following:

```
devilspie & 
gnome-terminal --window-with-profile=DesktopConsole
```

and just made startup run that (sh /path/to/script.sh) instead of the two commands. The & after devilspie is important, otherwise gnome-terminal won't start.

---

### Post by Jammanuser on 2009-02-28
Still waiting for a response to posts #206 and #207...;)

-Jam man

:guitar:

---

### Post by jastonas on 2009-02-28
> **jinacio said:**
> 

the drawback os using "utility" is that the "show desktop" will hide/unhide the terminal.

So far i havent't found a better method, but i'll keep looking into it.

Has there been any workaround for that?

---

### Post by matmat07 on 2009-03-06
Look at page 14 I think. Uoi have to change the button to use a script.

---

### Post by jastonas on 2009-03-07
> **nawitus said:**
> This is how to fix the "show desktop bug":
First, open the show desktop about, take a screenshot, and use gimp/picture editor to create icon (I saved it as a .png). Then, open up terminal, click edit->profiles and select DesktopConsole. Go to title and command and changeDynamically-set-title : Isin't displayed.

Create a file called "showdesktop" anywhere, and edit it.
Paste this:
```

#!/bin/bash
wmctrl -k on
wmctrl -a DesktopConsole
exit

```
and save it.
Right-click on desktop and create launcher. Open the folder where you saved the icon and select it. Select the file "showdesktop". Drag the icon to your panel, and delete the other icon from your desktop.

Type:
```

sudo apt-get install wmctrl

```

Delete the old "show desktop button" which didn't work.

Now your new show desktop button should work correctly.

Also, replace the Ctrl-Alt-D hotkey to execute "showdesktop" script by following this guide:
[http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/)

Very helpful but it doesnt work properly. It will minimise everything but wont bring them back. To bring them back i need to press the original show desktop icon.

---

### Post by phpadik on 2009-03-07
Thanks a lot. My desktop is now geekier than ever! FIVE THUMBS UP!

---

### Post by Roanoke on 2009-03-15
It doesn't work for me. It stays on top of all the windows.
```

(if
        (matches (window_name) "DesktopConsoleTerminal")
        (begin
                (set_workspace 4)
                (undecorate)
                (skip_pager)
                (geometry "+900+900")
                (wintype "utility")
                (skip_tasklist)
                (below)
        )
)

```

---

### Post by jastonas on 2009-03-24
I managed to make the terminal work as a background and not be affected when show desktop is pressed just from compiz. I dont have time now but i ll make a step by step tutorial pretty soon. The 3 places to visit are place windows-window decoration-window rules. It took my 5 minutes and i didnt have the knowledge before.. pretty easy to use for anyone who wants to give it a go.

As far as the "bug" of minimizing the terminal there is a very easy workaround in gconf.

Run gconf-editor, go to apps>compiz>general>allscreens>option and uncheck the hide_skip_taskbar_windows.

---

### Post by Roanoke on 2009-03-24
Could someone help me?

---

### Post by pw_f100_220 on 2009-03-31
Anyone know about getting this to work in Fluxbox?
After much tweaking, I was able to get it working wonderfully in Gnome with the following .ds file.  I think the problem might be devil's pie in Fluxbox because the correct profile opens but it doesn't have any desired properties, and there are visual glitches as well

```
(if
        (matches (window_name) "DesktopConsole")
        (begin
                (pin)
                (below)
                (undecorate)
                (skip_pager)
                (skip_tasklist)
                (wintype "desktop")
                (geometry "+50+50")
                (geometry "924x1050")
        )
)
```

Thanks!

---

### Post by Roanoke on 2009-04-01
Thank you, that works perfectly for me. Unfortunately, I don't use fluxbox, so I can't help.

---

### Post by dfmalh on 2009-04-01
It works... kind of...in Ibex, but I can't drop the top bar, and have my terminal as "wallpaper". 

Out of pure frustration I tried "Tilda" following this tutorial: [http://www.linuxhaxor.net/2008/05/01/configuring-linux-terminal-to-work-as-a-transparent-wallpaper-part-1/]("http://www.linuxhaxor.net/2008/05/01/configuring-linux-terminal-to-work-as-a-transparent-wallpaper-part-1/"), and it works great.

Hope someone can get this method to work as a "Desktop Wallpaper" in Ibex.

:lolflag:

---

### Post by bhart007 on 2009-05-01
I'm trying to figure out how to move or relocate the terminal window to the lower right hand corner of the screen, which I assume would be the geometry value...anyone do this?

---

### Post by dupsatOU on 2009-06-02
I had set this up on my system a while ago but since upgrading to Jaunty I've not had it work since.  I finally got fed up with my problem (specifically that my terminal could be unintentionally raised above other windows) and stumbled on this thread.  Thought I'd share what ended up fixing it for me...

Obviously, the window_name isn't relevant to the fix - it's just the name I have assigned for my window. I believe the wintype 'dock' was what finally did the trick for me.
```

(if
	(matches (window_name) "mainbg-term")
	(begin
	(below)
	(pin)
	(undecorate)
	(skip_pager)
	(skip_tasklist)
	(geometry "+790+50")
	(wintype "dock")
	)
)

```

---

### Post by CosmicFlux on 2009-06-07
Hey,

I also had this working back in 2007 when I was using Gutsy. I tried it on Jaunty and all I got was a standard terminal window, complete with title bar and window borders. In fact, the only recognisable change was the transparency setting.

I sorted this ALL just by taking the two lines of geometry code and putting it all on a single line, like this:

***(geometry "900x500+150+130")***

It now works absolutely fine. I did have to remove the the start-up information, but I'm not really interested in having it there when the computer boots anyway.


Cosmic

---

### Post by M4rotku on 2009-06-09
I'm trying this in Jaunty (and I did try what is listed in the above post) and nothing works.  It just starts up as normal.  I ideally want the computer to start-up into what looks like recovery mode (except being centered and with a border so i can still have a dock and files on my desktop), but being capable of having windows open and programs running.

---

### Post by BlazeFire247 on 2009-06-09
This is useful. How do you resize it/make it smaller?

---

### Post by M4rotku on 2009-06-11
bump

---

### Post by Nikayah on 2009-07-06
I figured out the problem on Jaunty! What happened was the new terminal's name was NOT "DesktopConsole" but instead "Gnome-Terminal". Obviously you don't want to force all terminals to the background, and since I couldn't find a simple way (in my 3 second search) to change the new terminal's name I decided to use the --role="String" option provided by Gnome terminal turning my terminal startup command into

```

gnome-terminal --window-with-profile=DesktopConsole --role="DesktopConsole"

```

and my .ds script into 

```

(if
	(matches (window_role) "DesktopConsole")
		(begin
			(below)
			(pin)
			(undecorate)
			(skip_pager)
			(skip_tasklist)
			(geometry "900x500+150+130")
			(wintype "dock")
		)
)

```

I hope that this helped in some way ;P

EDIT: Here's what you'll probably want to run in your startup stuff 
```

devilspie -a

```

and

```

gnome-terminal --window-with-profile=DesktopConsole --role="DesktopConsole"

```

---

### Post by wotsit on 2009-08-12
Im using 8.04 and this worked perfectly for me, using CarbonMine theme from gnome-look, and swapped to green lettering with the dark theme and dark wallpaper. looks fantastic. Great job man

---

### Post by Guy Sibley on 2009-10-03
Is there any way to get the top menu/title bar and borders to go away? Other than that thank you for this it made my day
-Guy

---

### Post by joshua.smith7 on 2009-10-06
Hey I am new to all this. I tried this but the Black border is still around it.

Could  have some help please???

Thanks Josh

---

### Post by Trinexx on 2009-11-04
I've applied all the little tweaks and such to get it working in Karmic, and it works. Mostly.


If I click anywhere on the desktop that isn't the terminal, the terminal goes out of focus (not visually, you know what I mean) and I can't get focus back to it without restarting devilspie.

Any ideas?

---

### Post by sosostris on 2009-11-07
From my point of view you no longer have to use devilspie as long as you are using compiz. Unless I am missing something.

My solution is as follows: 

I have a script file to start the console which simply defines the geometry, the profile and the working directory. This is script is called on startup of course.
```
gnome-terminal --window-with-profile=DesktopConsole --geometry="120x30+310+125" --working-directory=/home/mike
```

The **Profile DesktopConsole** has to have the following properties set:

*On Title and command*
[LIST]
[*] Keep initial title
[*] Restart command when closed
[/LIST]

Furthermore I defined the rules not in pager, not in taskbar, sticky, not movable, not resizable, not closable, ...  in **ccsm (Compiz config settings manager)** -> Window Rules for
```

(title=desktop console)

```

and in Window Decoration
```

Decorate windows: !(title=desktop console)

```

That's it.

Here is a screenshot:
[http://static.wochs.com/images/desktop-console.png](http://static.wochs.com/images/desktop-console.png)

---

### Post by laceration on 2009-11-09
frickin excellent sosostris!

I even set the window size in window rules.  I suppose this thread is pertinent for those w/o the juice to run compiz, but if you have Compiz its the way to go.

Since I like to have a bunch of terminals open, I run 2 each on 2 workspaces.  I open from a launcher and position with alt + mouse1 -- which is another compiz setting.

---

### Post by Weevil on 2009-11-16
I have the (strange?) problem that whenever I open another terminal the devilspie controlled terminal pops over other windows. Got it working right by setting wintype to "normal".

Also geometry only worked for me by setting it like this:
 (geometry "200x200+50+50")

---

### Post by mathfreak123 on 2009-12-07
Wow, this is what I've been wondering how to do ever since I saw that one screenshot in the conky files thread! Thanks a lot!

---

### Post by Jammanuser on 2009-12-07
Hi,

Can someone please help?

I followed the instructions in the first post to the letter, but things do not work the same as in the screenshot.

1. I can see the terminal window in the taskbar (which, as I understand it, is supposed to disappear).
2. Though the terminal is transparent, it shows only the background behind it, and not the icons on the desktop.
3. I changed the geometry in the DesktopConsole profile, but the size of the terminal is still the same as a normal terminal window (I wanted to make it the same size as the screen).

I would like to:
[LIST]
[*]Make terminal window in the taskbar disappear.
[*]Make the terminal only above the wallpaper, and not above the desktop icons.
[*]Make terminal the same size as screen.
[/LIST]
Anyone have any ideas how I can do just that?

Thanks in advance.

-Jam Man

:guitar:

---

### Post by mathfreak123 on 2009-12-08
Jammanuser: Have you tried sosostris's method a few posts above yours? It works great for me.

---

### Post by Jammanuser on 2009-12-08
> **mathfreak123 said:**
> Jammanuser: Have you tried sosostris's method a few posts above yours? It works great for me.
Nope, because I'm not using compiz. Appreciate the reply though.

---

### Post by guriinii on 2009-12-08
what are the commands to start the 2 applications on startup?

---

### Post by Jammanuser on 2009-12-08
> **guriinii said:**
> what are the commands to start the 2 applications on startup?

```
devilspie
```

and

```
gnome-terminal --window-with-profile=DesktopConsole
```

---

### Post by guriinii on 2009-12-08
One thing sorted. I can't seem to get it as my wallpaper, I've had a play around but nothing seems to happen.

Can anyone help?

---

### Post by guriinii on 2009-12-09
Got it and it is awesome

```
( if
        ( matches ( window_name ) "DesktopConsole" )
        ( begin
                ( set_workspace 2 )
                ( undecorate )
                ( skip_pager )
                ( skip_tasklist )
                ( geometry "1024x768+0+0" )
                ( below )
                ( println "match" )
        )
)
```

hope this helps someone

---

### Post by Jammanuser on 2009-12-09
> **guriinii said:**
> One thing sorted. I can't seem to get it as my wallpaper, I've had a play around but nothing seems to happen.

Can anyone help?

Yeah, I have the same problem (see [this post]("http://ubuntuforums.org/showpost.php?p=8458153&postcount=239")), but no one's helping...:(

I would try the above poster's code in the .ds file, but I can't get gedit to open the file. I've tried, and it sort of acts like its opening, but the program wont open. Anyone have any idea why that is? Before, I was having a similar problem with gedit, but the program *would* at least open (just in the wrong workspace, and the top part of the program with the exit button wasn't showing; i had to exit the program through the file menu). Now it wont open at all (not even through the command-line).

UPDATE: The System Monitor shows the gedit process running, but its status is "Sleeping". I'm going to try ending the process, and attempting to open the file through gedit again.

UPDATE 2: Ok, that worked to open Gedit and edit the file, but Gedit is still acting weirdly, and not showing the top of the program (in addition to not showing up in the taskbar). It wont let me resize, minimize, or exit the window like normally.

---

### Post by guriinii on 2009-12-09
> **Jammanuser said:**
> Yeah, I have the same problem (see [this post]("http://ubuntuforums.org/showpost.php?p=8458153&postcount=239")), but no one's helping...:(

I would try the above poster's code in the .ds file, but I can't get gedit to open the file. I've tried, and it sort of acts like its opening, but the program wont open. Anyone have any idea why that is? Before, I was having a similar problem with gedit, but the program *would* at least open (just in the wrong workspace, and the top part of the program with the exit button wasn't showing; i had to exit the program through the file menu). Now it wont open at all (not even through the command-line).

UPDATE: The System Monitor shows the gedit process running, but its status is "Sleeping". I'm going to try ending the process, and attempting to open the file through gedit again.

I'm not sure about your gedit problem, although this happened to me and I used nano. The code in my last post worked fine, just copy and paste it. Change the geometry to your current resolution. Play about with the X and Y axis, I don't really understand how it works though. 

But I haven't managed to get the icons above the Terminal. If you work it out let me know.

Hope it works for you.

---

### Post by Jammanuser on 2009-12-09
> **guriinii said:**
> I'm not sure about your gedit problem, although this happened to me and I used nano. The code in my last post worked fine, just copy and paste it. Change the geometry to your current resolution. Play about with the X and Y axis, I don't really understand how it works though. 

But I haven't managed to get the icons above the Terminal. If you work it out let me know.

Hope it works for you.
This happened with nano too? How, since nano is command-line only?

I just tried your above code in my .ds file (though I of course changed the resolution to the correct one in my case), but the same thing still happens, i.e.  the terminal that loads at startup is still the same size as the normal terminal, it is just transparent, and you can see the wallpaper behind it when you move it around the screen (even when the terminal window is above another window), and of course the icons do not show up in front. Not to mention, the terminal shows up in the taskbar (which I gather from the first post, isn't supposed to happen).

Here is my complete code:
```

(if
        (matches (window_name) "DesktopConsole")
        (begin
                (set_workspace 2)
                (below)
                (undecorate)
                (skip_pager)
                (skip_tasklist)
                (wintype "utility")
                ( geometry "1280x800+0+0" )
                ( below )
                ( println "match" )

        )
)

```
And yeah...gedit is still messing up. It opens in workspace2 instead of workspace1, and I just had the previously mentioned problem again, which i fixed in the same way (i.e. ended the gedit process, and double-clicked the file again to open it).

---

### Post by guriinii on 2009-12-09
Put a space after and before every bracket, for example:

```

( if
        ( matches ( window_name ) "DesktopConsole" )
        ( begin

```

make them changes and it will sort the size problem out but not the icon placement.

---

### Post by Jammanuser on 2009-12-09
> **guriinii said:**
> Put a space after and before every bracket, for example:

```

( if
        ( matches ( window_name ) "DesktopConsole" )
        ( begin

```

make them changes and it will sort the size problem out but not the icon placement.
Thanks. I didn't notice the spaces thing at first and/or didn't think whitespace made any difference (I'm used to coding in C++ which doesn't care what whitespace you put in it), but I made the changes, and I'm off to test it now to see if it works. :)

Cheers.

-Jam Man

:guitar:

---

### Post by Jammanuser on 2009-12-10
Nope. :(
Had absolutely none effect. 
Guess I'll have to turn to Google...

---

### Post by Jammanuser on 2009-12-10
Ahh...
Found some interesting things. Should have checked devilspie's documentation, to begin with.

I changed my .ds file to the following:

( if
        ( matches ( window_name ) "DesktopConsole" )
        ( begin
                ( set_workspace 1 )
                ( below )
                ( skip_pager )
                ( skip_tasklist )
                ( wintype "utility" )
                ( maximize )
                ( println "match" )

        )
)

Turns out the "undecorate" line was what was causing the gedit problem (I think), since it removes the "decoration" for all windows (decoration apparently being the window bar which contains the exit and minimize buttons). I removed that line (don't know why the OP suggested it in the first place), and also replaced the geometry line(s) with ( maximize ) instead which maximizes the window. That should fix the problem. I'm off now to test it.

---

### Post by Jammanuser on 2009-12-10
Hmm...I just tried it with both "maximize" and "fullscreen", and both times the terminal window still remained the same size. I think that's probably why they suggested using the geometry commands. I'm going to try adding that again, and see if it works...

---

### Post by nitstorm on 2009-12-19
> **noob_Lance said:**
> hey.. this program destroyed compiz on my computer. it worked perfectly fine until i tried this program... then every single window i opened was the way the terminal was set to be.. and because of this i have uninstalled compiz... reinstalled it...and to my suprise NO change!.... i have uninstalled devilspie completly! and still my problem comtinues. Please help me fix this..!

~Lance


maybe this would help? [http://tombuntu.com/index.php/2007/08/27/transparent-terminal-on-your-desktop/](http://tombuntu.com/index.php/2007/08/27/transparent-terminal-on-your-desktop/)

---

### Post by glnerd on 2009-12-19
Thanks, nice tutorial. still havent figured out how to hide the terminals active taskbar indication but it looks good so far. thought i'd give you a preview:
[http://i49.tinypic.com/2egfg51.png](http://i49.tinypic.com/2egfg51.png)

Thanks alot ^_^

---

### Post by Crunchy the Headcrab on 2010-01-03
ah, crap I double posted again.  sorry.

---

### Post by Crunchy the Headcrab on 2010-01-03
> **sosostris said:**
> ...
Thanks man.  That's good stuff!

---

### Post by Rigbonn on 2010-01-03
I found this tutorial very useful, I like the idea, and it's beautiful, awesome. Thanks for this one.

Edit:
So, I'm stuck here. How do I exactly add these programs you told to @ 5th step?

---

### Post by kyuubi777 on 2010-01-03
this is awesome! thanks to op!.. i've yet to reboot, and will probably run into issues but those can be easily enough dealt with.

---

### Post by Rigbonn on 2010-01-04
So, I'm stuck here. How do I exactly add these programs you told to @ 5th step? I'm using v9.10 Ubuntu.

---

### Post by Ildanach on 2010-01-12
I have to say, I really like the look of this setup, but I'm having some trouble getting it to work on my system. When I installed Devil's pie on my system and put in devilspie and Gnome Terminal under startup applications, only the Terminal appeared, and on the wrong desktop. Didn't know if anyone had a solution. Sorry if someone has already asked this question, I tried a couple other answers, but none of them worked.

---

### Post by Drew Barfield on 2010-01-16
If you have an Nvidia video card and are using the 'Separate X Screen' configuration, use this command line to launch the terminal in the second screen:

```
sh -c 'DISPLAY=:0.1 gnome-terminal --window-with-profile=DesktopConsole'
``` 

For me, this command line is run as a Startup Application (so is devilspie).

So, in a sense, devilspie can 'function' on the screen of your choice.

-Drew

---

### Post by glethro on 2010-02-24
One instruction left out that caused me to problems is that you have to set the initial title to "DesktopConsole" in order for this to work.

So for anyone experiencing trouble, when you edit the profile try changing Title and Command>Initial Title to DesktopConsole

That fixed all my problems. Great setup btw.

---

### Post by wkjid10t on 2010-06-01
Alright, so  followed the setup instructions to the detail... Ended up putting those two lines into startup and then my linux stopped working... It was functioning, but no responding to anything that i did...

Now i reformatted and followed instructions again, but not yet at the startup code yet...

Still testing the devilspie and terminal...
Now i logged out/restarted and on startup i use alt F4 to startup devilspie, then i us alt F4 again to startup the terminal with DesktopConsole name etc... Nothing changed...

Then when i used either console... gnome or terminator, and ran the devilspie, i got this error:

(devilspie:7883): Wnck-WARNING **: Unhandled action type _OB_WM_ACTION_UNDECORATE


The number in brackets is not a constant number, it changes every time that i try running devilspie...



I am currently running Crunchbang linux... So i dont know if there is anything that might cause this not to work?

Thank, i appreciate any help. (i wanna make my destop look cool)

H

---

### Post by allroys on 2010-07-04
For those of you having trouble getting devilspie to actually DO anything to the terminal: When you're setting up the DesktopConsole profile for the terminal, under the "title and commands" tab, change "replace initial title" to "keep initial title" in the dropdown. Otherwise, the name of the window becomes "me@mycomputer: ~" while devilspie is looking for "DesktopConsole." 

Now if anybody could find out why it won't change workspaces for me...

Whoops. just noticed glethro already caught this one....

---

### Post by ajju15 on 2010-09-08
hey 

thank you for guide. Everything is fine but terminal is displayed in my panel bar and it also show me the close (x) at the top of the window is there any way to remove them. i'm using ubuntu10

---

### Post by MonsterreactioN on 2010-09-19
> **jinacio said:**
> glad to know that :D

cheers!

Edit: (forgot something that might be important)

i use (wintype "utility") because it's the most compatible setting: also tried as "desktop" but if the geometry is not maximize and you click anywhere outside the terminal, it will disapear.
the drawback os using "utility" is that the "show desktop" will hide/unhide the terminal.

So far i havent't found a better method, but i'll keep looking into it.

Check out: 
wmctrl 
To solve the show Desktop problem

---

### Post by Habitual on 2010-11-22
I used ( wintype "dock" ) and the show desktop issue went away.

---

### Post by Andras B. on 2010-12-17
Just wanted to show my working setup, based on the tutorial and the tremendous amount of comments in this thread. :)

The first post definitely lacks important info...

... like how to position and size the terminal window (the geometry values in the .ds file are ignored, use the --window-geometry 80x24+200+100 switch when starting gnome-terminal)
... like how to make devilspie recognize the window (you have to change title in the Profile settings to DesktopConsole, or anything that you regmatch for in the .ds file)

[ATTACH]178635[/ATTACH]

---

### Post by I'mGeorge on 2010-12-17
cool tutorial, for gnome desktops

---

### Post by tanusfarms on 2010-12-21
I can't get this to work properly. When i log out and then log in the terminal window is on workspace 1 with the correct profile loaded but no other changes that the devilspie was supposed to do. I am unsure if the devilspie is running correctly or not how can I be sure it is?

---

### Post by nudewind on 2011-07-02
> **jinacio said:**
> The objective is to have a gnome terminal running as the desktop background, right above the actual background image, that won't be displayed by the statusbar or ticker.

It should look something like this:
[Full transparency](http://img336.imageshack.us/img336/378/desktopterminal0uz.png)
or
[Semi-transparent with shadows (using Xgl)](http://img135.imageshack.us/img135/7796/desktopterminal6vw.png)

Ok, lets get started... :)

1) Download devilspie
```
sudo apt-get install devilspie
```

2) Create a configuration file 
```

mkdir ~/.devilspie
nano ~/.devilspie/DesktopConsole.ds

```

3) Paste the following configuration (press Ctrl^X to save and exit):
```
(if
        (matches (window_name) "DesktopConsole")
        (begin
                (set_workspace 4)
                (below)
                (undecorate)
                (skip_pager)
                (skip_tasklist)
                (wintype "utility")
                (geometry "+50+50")
                (geometry "924x668")
        )
)
```

Notes:
- i use workspace 4 but you can use whatever you like.
- you should at least adjust the geometry lines to match your screen.
- **Read** the [devilspie wiki](http://wiki.foosel.net/linux/devilspie#geometry), for other commands!!!

4) Create a new gnome-terminal profile named "DesktopConsole"
- in the "General" tab, untick "show menubar by default..."
- in the "Scrolling" tab, select "Scrollbar is" -> Disabled.
- in the "Effects" tab, set "Transparent background" and shade to "None" (or to whatever you prefer)

5) Add devilspie and gnome-terminal to the Startup Programs in your session:
in System->preferences->sessions, "Startup Programs" tab, add the 2 programs:
```

devilspie
gnome-terminal --window-with-profile=DesktopConsole 

```

6) Logout, Login 8)

check to see that devilspie is running *before* the gnome-terminal command.


Thats it!

Edit:
added screenshot
thx

---

### Post by briigga on 2011-08-18
can someone help me out with this out i cannot get it to work.tried it about 3x..all i get is a transparent terminal profile called desktopconsole1...I cannot get it to be my background!!!!!!!

---

### Post by briigga on 2011-08-19
> **jinacio said:**
> The objective is to have a gnome terminal running as the desktop background, right above the actual background image, that won't be displayed by the statusbar or ticker.

It should look something like this:
[Full transparency]("http://img336.imageshack.us/img336/378/desktopterminal0uz.png")
or
[Semi-transparent with shadows (using Xgl)]("http://img135.imageshack.us/img135/7796/desktopterminal6vw.png")

Ok, lets get started... :)

1) Download devilspie
```
sudo apt-get install devilspie
```2) Create a configuration file 
```

mkdir ~/.devilspie
nano ~/.devilspie/DesktopConsole.ds

```3) Paste the following configuration (press Ctrl^X to save and exit):
```
(if
        (matches (window_name) "DesktopConsole")
        (begin
                (set_workspace 4)
                (below)
                (undecorate)
                (skip_pager)
                (skip_tasklist)
                (wintype "utility")
                (geometry "+50+50")
                (geometry "924x668")
        )
)
```Notes:
- i use workspace 4 but you can use whatever you like.
- you should at least adjust the geometry lines to match your screen.
- **Read** the [devilspie wiki]("http://wiki.foosel.net/linux/devilspie#geometry"), for other commands!!!

4) Create a new gnome-terminal profile named "DesktopConsole"
- in the "General" tab, untick "show menubar by default..."
- in the "Scrolling" tab, select "Scrollbar is" -> Disabled.
- in the "Effects" tab, set "Transparent background" and shade to "None" (or to whatever you prefer)

5) Add devilspie and gnome-terminal to the Startup Programs in your session:
in System->preferences->sessions, "Startup Programs" tab, add the 2 programs:
```

devilspie
gnome-terminal --window-with-profile=DesktopConsole 

```6) Logout, Login 8)

check to see that devilspie is running *before* the gnome-terminal command.


Thats it!

Edit:
added screenshot




Ok i finally got this to work. I was doing step 5 wrong. I was foolishly writing the gnome terminal command in the terminal and figured out i was supposed to add that to the command line for a new startup application..duh..

---

### Post by JooseyJay on 2011-09-15
My terminal still has the window border, still the same size, has a task bar tab, and is in the tasklist. It seems like the devilspie isn't there, maybe it ran after the console was created? How do I set it to run first?

Edit: I didn't change "Initial Title" to DesktopConsole, fixed and thanks for a great tut.

---

### Post by AvalonSpirit on 2011-10-26
Thanks for the tutorial. plus all the helpful comments.

I'm running oneiric with gnome 3.2.

I was originally using the gnome-terminal and everything was working well. But since the launchers are now task based, when I wanted to open another terminal, it just focused on the desktop terminal.

So i tried to use aterm, like someone in this thread sugested to have gnome-terminal available as a regular terminal.

It is working fine, except the ( undecorate ) option sort of eats away a border of the actual application instead of just removing the borders of the window. 

This wouldn't be so much of a problem except that once the prompt reaches the bottom of the window it disappears beyond the edge.

My DesktopConsole.ds file:
```

(if
        ( matches ( window_name ) "DesktopConsole" )
        ( begin
                ( pin )
		        ( stick )
                ( below )
                ( undecorate )
                ( skip_pager )
                ( skip_tasklist )
                ( wintype "utility" )
                ( geometry "900x700+450+80" )
                
        )
)

```

The command I use at startup to run aterm is:
```

aterm -name aterm -title 'DesktopConsole' -tr +sb -sh 0 -fn -misc-fixed-medium-r-normal-*-22-200-*-*-c-*-iso8859-2 -ls

```

I also get xterm displayed in the tasklist (when using gnome-terminal it did skip the tasklist as the script intends)


Any thoughts on how to solve this?

---

### Post by khughitt on 2012-07-30
Just tried this out and was able to it working by setting the initial title to "DesktopConsole", however, I'm using Gnome Shell and shortly after the window is drawn at the offset specified in the devilspie config, Gnome moves it to the top-left corner of the screen.

Anyone know a way around this?

---

### Post by khughitt on 2012-07-30
Okay that wasn't so bad. The solution is to combine the geometry settings into one line, e.g.:

    (geometry "1200x800+50+50")

---

