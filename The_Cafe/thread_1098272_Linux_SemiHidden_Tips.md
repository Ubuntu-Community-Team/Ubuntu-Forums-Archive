---
title: "Linux SemiHidden Tips"
date: 2009-03-16
forum: The Cafe
---

### Post by Islington on 2009-03-16
So there are a lot of things that experienced users, like yourself know about that make life much easier for users. Perhaps you are a new user, who has discovered something. Please Contribute to this thread and make those little things known! :)

Here are the ones that I know and use:

> 
Selecting any text automatically adds it to a clipboard. MiddleClicking in a text field/place will paste this text. 

> 
Window List Applet, on a panel: you can cycle through the windows by using the scrollwheel. 

> 
Scrollbar in gnome: right clicking on the up/down arrows will scroll you all the way up/down. 

> 
Compiz scale: when scale is activated, you can filter through the windows by typing (a bit like gnome do), by default this is case-sensitive, but can be turned off using the option in the Scale Window Title Plugin

---

### Post by smartboyathome on 2009-03-16
Here is my tip (related to your first one):

> In Linux, there are actually two clipboards. One uses the standard ctrl-c, ctrl-v meathod of copying and pasting, and the other uses the highlight, middle click paste meathod.

Another:

> Read the bolded link in my signature to avoid the mistake mentioned.

---

### Post by Islington on 2009-03-16
> **smartboyathome said:**
> snipYour second tip is rather important, I feel. :D

---

### Post by bsharp on 2009-03-16
I know someone else will eventually post this, but I will do it first :twisted:

Tab-complete.

Type the first couple of letters of a program/command into a terminal and push tab twice. it will either finish out the rest of the program's name or give a list of several programs with the same beginning. (If someone can explain it better, please do so.)

---

### Post by Islington on 2009-03-16
> **bsharp said:**
> I know someone else will eventually post this, but I will do it first :twisted:

Tab-complete.

Type the first couple of letters of a program/command into a terminal and push tab twice. it will either finish out the rest of the program's name or give a list of several programs with the same beginning. (If someone can explain it better, please do so.)

this only seems to work for me when specifying a directory path ...:|

---

### Post by smartboyathome on 2009-03-16
> **Islington said:**
> this only seems to work for me when specifying a directory path ...:|

You need to switch to something like ZSH to enable it on more stuff than commands and directory paths. It doesn't work with sudo.

---

### Post by spupy on 2009-03-17
[QUOTE=Islington]Scrollbar in gnome: right clicking on the up/down arrows will scroll you all the way up/down.[/QUOTE]
Whoa, thanks for that one :)

My protips:
> Something that in Windows is not working everywhere: ctrl+backspace and control+delete delete whole words, not only a single letter. Similarly, control+arrows moves the caret (text cursor) to the next/previous word.

> Firefox: Press ctrl+shift+T to restore the last closed tab. It will also restore any text you've written in that tab, any buttons you've clicked, and its whole back/forward history.

---

### Post by jimi_hendrix on 2009-03-17
alt+sysrq+REISUB....saves lives

---

### Post by Mehall on 2009-03-17
Generally, if you use scrollwheel, you scroll on whatever window the cursor is over, not necessarily the active window


And not tested it in Gnome, but in Openbox if you scroll down on an icon in a task bar (so it might be specific to that task bar in Crunchbang) then it will minimize to tray the window you scrolled of the icon.

Thats  abad explanation. I scroll down on Firefox's icon, Firefox minimizes. I scroll up, it un-minimizes.

---

### Post by spupy on 2009-03-17
> **Mehall said:**
> Generally, if you use scrollwheel, you scroll on whatever window the cursor is over, not necessarily the active window.

It is a good tip. It works on all window managers, i think. It's a xserver thing.

---

### Post by Mehall on 2009-03-17
I knew that one worked in them all, does the other one?

---

### Post by Bodsda on 2009-03-17
[SIZE="4"]_Your friends_[/SIZE]

[LIST]
[*]Man pages (man sudo)
[*]Google (This is the greatest undisputed resource you have)
[*]--help (If you need to know about a  programs command line options use <command> --help e.g. mv --help)
[/LIST]

Command line tool for downloading youtube videos

```
sudo apt-get install youtube-dl
```

consult ```
man youtube-dl
``` to learn how to use it

---

### Post by bryncoles on 2009-03-17
> **Islington said:**
> this only seems to work for me when specifying a directory path ...:|

try pressing tab twice fast...

---

### Post by ssam on 2009-03-17
> **smartboyathome said:**
> You need to switch to something like ZSH to enable it on more stuff than commands and directory paths. It doesn't work with sudo.

you dont need zsh. you just need the bash-completion package.

if this does not enable advanced completion, then you may have it disabled in you .bashrc. old versions of ubuntu had it disabled by default, maybe you kept your .bashrc since then.

it will autocomplete program names, but it will do it by executable name, rather than pretty name. so gedit rather than Text editor

---

### Post by sisco311 on 2009-03-17
> **smartboyathome said:**
> It doesn't work with sudo.

It works in Ubuntu by default.

In arch you have to install *bash-completion* and add something like:
```
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

[B]complete -cf sudo
complete -cf gksu
complete -cf gksudo
[/B]

```to the ~/.bashrc file.

EDIT:
@ssam 
i did't refresh the page before posting. :)

---

### Post by smartboyathome on 2009-03-17
Ah, ok. I'm just not used to bash anymore. :|

---

### Post by Trail on 2009-03-17
Edit: Eh yeah, nevermind.

---

### Post by damis648 on 2009-03-17
> **jimi_hendrix said:**
> alt+sysrq+REISUB....saves lives

Wrong!!
Its RSEIUB. :popcorn:
**R**aising **S**kinny **E**lephants **I**s **U**tterly **B**orning.

---

### Post by Islington on 2009-03-17
> **damis648 said:**
> Wrong!!
Its RSEIUB. :popcorn:
**R**aising **S**kinny **E**lephants **I**s **U**tterly **B**orning.

:popcorn: Neither works for me, because the sysRq key doesn't seem to trigger anything.

---

### Post by Exershio on 2009-03-17
Pressing CTRL + C in terminal will terminate any current process running. For example, if you're doing a disk check in terminal, CTRL + C will terminate it.

---

### Post by phaed on 2009-03-17
This is probably the most useful thread on Ubuntu Forums that I've read that had nothing to do with a specific problem I was having.

"Selecting any text automatically adds it to a clipboard. MiddleClicking in a text field/place will paste this text."

You just made my life a lot easier. :)

---

### Post by yabbadabbadont on 2009-03-17
> **damis648 said:**
> Wrong!!
Its RSEIUB. :popcorn:
**R**aising **S**kinny **E**lephants **I**s **U**tterly **B**orning.

According to the wikipedia entry, both are correct, but there is debate about whether to sync early or late in the sequence.  The one originally posted is the one listed at wikipedia.

Personally, I sync in both places, just to be safe.

I.E.  Raising Skinny Elephants Is So Utterly Boring

;)

---

### Post by vambo on 2009-03-17
> **phaed said:**
> This is probably the most useful thread on Ubuntu Forums that I've read that had nothing to do with a specific problem I was having.

"Selecting any text automatically adds it to a clipboard. MiddleClicking in a text field/place will paste this text."

You just made my life a lot easier. :)

As an adendum
<Shift> <Insert> will also do the pasting

---

### Post by Islington on 2009-03-17
> **Exershio said:**
> Pressing CTRL + C in terminal will terminate any current process running. For example, if you're doing a disk check in terminal, CTRL + C will terminate it.

excellent! Is there anyway to move it to the background? so that it no longer has to use the terminal?

---

### Post by init1 on 2009-03-17
```

lsof

```
lists all open files.

---

### Post by sisco311 on 2009-03-17
> **Islington said:**
> excellent! Is there anyway to move it to the background? so that it no longer has to use the terminal?

yes, press Ctrl+Z to stop the process, then 

you can use the *bg* command to continue it in the background and 

*fg* to continue it in the foreground. 

you can list the jobs with the *jobs -l* command.

for more info read the man page.
```
man bash
```
press / to search the page, type *bg*(or any other search term) and hit Enter. 

for the next match just hit / and Enter. press q to quit.

---

### Post by MaxIBoy on 2009-03-17
> **Islington said:**
> So there are a lot of things that experienced users, like yourself know about that make life much easier for users. Perhaps you are a new user, who has discovered something. Please Contribute to this thread and make those little things known! :)

Here are the ones that I know and use:
None of these have anything to do with Linux. They are all based around either GNOME or Compiz, both of which run on operating systems other than Linux. (Although a lot of these actions are conventional behaviors that appear in other desktop environments/window managers, in a similar way to how F11 often means "fullscreen.")

Likewise, tab completion is one of the features of BASH, the standard command line interpreter (CLI) for UNIX. BASH runs on an enormous number of operating systems, including Windows (Cygwin.) However, tab completion is also an expected feature, going back to 1964 with the Berkley Timesharing System (it's true, I just looked it up.) It's a feature of almost every CLI in existence, including DOS.




Also, here are some of my tips. 
> #built into BASH, may or may not work on other CLIs
history #built-in program that prints out your recent command history; more useful when piped through to grep
cd #defaults to "cd ~"
cd - #takes you to the previous directory

#networking stuff. These are programs that will run if you have them installed, doesn't matter what CLI you use to call them. Almost all Linux distros include these by default. 
ifup eth0 #automatically configure ethernet connection; short for "ifconfig eth0 up"
ifdown eth0 #short for "ifconfig eth0 down"
iwconfig wlan0 essid any #for a wireless card named wlan0, automatically join the network with the strongest signal
iwconfig wlan0 essid Max_network #try to join a wifi network with the name "Max_network"
iwlist wlan0 scan #scan for networks and display stats about the results



---

### Post by Sealbhach on 2009-03-17
Stick a bunch of terminal commands into a text file, preceded by #!/bin/bash

Save the file. Make it executable, by right-clicking on it and going to the permissions tab. Double click on the file, select Run in Terminal.

Example here:

```
#!/bin/bash
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get clean all
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get clean all
sudo apt-get autoremove
```

This keeps the package manager clean and oiled. But you can have any set of commands.


.

---

### Post by MaxIBoy on 2009-03-17
> **Sealbhach said:**
> Stick a bunch of terminal commands into a text file, preceded by #!/bin/bash

Save the file. Make it executable, by right-clicking on it and going to the permissions tab. Double click on the file, select Run in Terminal.

Example here:

```
#!/bin/bash
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get clean all
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get clean all
sudo apt-get autoremove
```This keeps the package manager clean and oiled. But you can have any set of commands.


.EEK! Be careful where you aim those dist-upgrades!

---

### Post by smartboyathome on 2009-03-17
> **Islington said:**
> :popcorn: Neither works for me, because the sysRq key doesn't seem to trigger anything.

If you're on a laptop, then you should do this:

Hold Alt, then hold fn down and perss your sysrq key and then let go of the fn key, then use your boring elephants to kill your computer. ;)

---

### Post by treesurf on 2009-03-18
> **smartboyathome said:**
> If you're on a laptop, then you should do this:

Hold Alt, then hold fn down and perss your sysrq key and then let go of the fn key, then use your boring elephants to kill your computer. ;)


That gave me a screenshot of a screenshot.:popcorn:

---

### Post by sujoy on 2009-03-18
to end anything in a terminal that expects input, press Ctrl+D
for example the terminal itself, expects commands, so to close it you can use Ctrl+D instead of typing 'exit' everytime

run a command from terminal and stick it to background. 
$ gedit &         
that in bash will run gedit and free up the terminal for further use.
in zsh try this instead, 
$ gedit &!

for the above, you might sometimes see harmless error/warning messages, like for instance something in your gtkrc is wrong. so redirect the error to /dev/null like this
$ gedit 2>/dev/null &  _________ (for bash)
$ gedit 2>/dev/null &! __________ (for zsh)

another pro-tip, run important commands that must not be interrupted like distupgrades, filesystem check, whatever, inside screen. then detach it. that way if your X crashes it wont matter. i am saying this because xserver is the most probable thing to crash on a linux system.

use apropos to find commands related to a search keyword.
$ apropos sud
that should find gksudo, sudo, visudo etc

in firefox, press Alt+D or Ctrl+L to highlight the address bar. and you can assign a keyword to your bookmarks from the bookmark property.
so i have this community cafe bookmarked with a keyword of 'ufc'. hence i type 'ufc' in the address bar and arrive here :)

---

### Post by Trail on 2009-03-18
How about
```
nohup <command>
```
to execute something in the background, and keep it running even when the terminal is closed. Can be a lifesaver.

---

### Post by yabbadabbadont on 2009-03-18
> **Trail said:**
> How about
```
nohup <command>
```
to execute something in the background, and keep it running even when the terminal is closed. Can be a lifesaver.

That brings back (painful) memories of my Unix days and fighting with crappy Telebit modems while doing support.  You had to nohup any command that might take more than a few seconds to run because you never knew when the connection was going to drop on you.  You also had to be careful to always use the absolute path to things when removing them as the modems had this bad habit of resending the commands at random times if you had a bad connection.  (and they would be run in whichever directory was your current one...)

---

### Post by Occasionally Correct on 2009-03-18
Bash tip: Use ! to recall history. For example, *!mv* recalls and repeats the last line entered that starts with mv (it executes the entire line, so if you entered something like *mv x y; touch x*, it repeats both commands). Use a number after the ! to recall a certain line in history---useful alongside MaxIBoy's tip about the history command! :)

---

### Post by mcduck on 2009-03-18
> **damis648 said:**
> Wrong!!
Its RSEIUB. :popcorn:
**R**aising **S**kinny **E**lephants **I**s **U**tterly **B**orning.

I'd say REISUB. You'll want to end your processes (E and I) before you sync your drives (S). Syncing them before ending running programs would be quite pointless.

---

### Post by Sealbhach on 2009-03-18
> **MaxIBoy said:**
> EEK! Be careful where you aim those dist-upgrades!

OK, but I'm using this in Jaunty so what the heck, I might get a sneak preview of Karmic Koala.:P


.

---

### Post by Islington on 2009-03-18
Is there a difference between using ```
<command> &
```(this seems to be a faster way of doing (ctrl+z + bg) and doing ```
nohup <command>
```.


I gotta say I love ff bookmarks, I also have some bookmarklets, as the bookmarks do accept javascript.

---

### Post by Botbob89 on 2009-03-18
Not really a tip for running Ubuntu; but when you first start using it, be patient and know that you are going to make mistakes.

Installing it and expecting to be someone who can fully use it with no problems is just wrong :P

Also, and slightly related, Ubuntu is not Windows............

---

### Post by Trail on 2009-03-18
> **Islington said:**
> Is there a difference between using ```
<command> &
```and doing ```
nohup <command>
```.

In the first way, if you close the terminal window (or SSH connection etc), the command stops executed. In the second way, the command still runs whatever happens.

> Bash tip: Use ! to recall history. For example, !mv recalls and repeats the last line entered that starts with mv (it executes the entire line, so if you entered something like mv x y; touch x, it repeats both commands). Use a number after the ! to recall a certain line in history---useful alongside MaxIBoy's tip about the history command!

Also try using Ctrl+R. This is a reverse search in history, keyed to some text you type after pressing Ctrl-R. For example if i pressed Ctrl-R and "ouch", it would probably find the line "mv x y; touch x" you mentioned above. Hit Ctrl-R another time, and it retrieves the previous result. Play with it a bit, it's very handy.

---

### Post by Sealbhach on 2009-03-18
I saw someone give another way to open up an app in the terminal which will not close when the terminal is closed:

```
*command* &disown
```


.

---

### Post by 3rdalbum on 2009-03-18
Pressing Alt-F2 in Gnome, KDE or XFCE will open a "Run application" box where you can quickly type the name of the program or command you want to run, and then press Enter to run it. Much quicker than surfing the Applications menu... "is it in Graphics or is it in Office? Or in Accessories?"

--------
Placing a little penguin ornament on top of your computer will prevent most kernel panics, and cause your computer to run faster.
--------

If you want to schedule your computer to shut down, use the "at" command:

```
sudo at now + 7 hours
halt

```

(then press Control-D to quit the At prompt)

Just don't shut down your computer manually, otherwise the next time you start it up it will run the AT job... and shut down your computer again.

--------

If you're on a laptop or netbook, download Powertop from the repositories to see what programs are wasting power by causing your CPU to keep waking up. It also suggests things you can improve in your system to get better battery life.

---

### Post by Bodsda on 2009-03-18
To shutdown

```
sudo shutdown -P now
```

To reboot 

```
sudo shutdown -r now
```

To shutdown in 1 hour

```
 shutdown -P now + 60
```

To shutdown your sons computer at 23:00 to make him go to bed

```
sudo shutdown -P 23:00
```

=================
How to stop your partner from using your computer to access facebook/<insert name of annoying website here>

We need to edit the /etc/hosts file (you need sudo for this) (replace 'vim' with your preffered text editor
```
sudo vim /etc/hosts
```
The file should look something like this
```
127.0.0.1       localhost
127.0.1.1       bod-ubuntu
92.2.76.121   www.bodsda.co.uk

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
As you can see i have already put in an entry, which redirects 'www.bodsda.co.uk' to '92.2.76.121' because i couldnt be bothered to purchase a domain name. 

Anyway what we need to do is add a newline to the top section (before the #comment)

add a line like the following

```
91.189.94.12    www.facebook.com
```

The syntax is
<address of redirect>    <www.url-of-site-to-redirect.com>

The line in my example will cause anyone who attempts to go to [www.facebook.com](www.facebook.com) on your computer to end up at [www.canonical.com](www.canonical.com)

Have fun,

Bodsda

---

### Post by unutbu on 2009-03-18
How to wake your computer up (by itself) after 30 minutes:

```
sudo sh -c "echo $(date '+%s' -d '+ 30 minutes') > /sys/class/rtc/rtc0/wakealarm"
sudo shutdown -P now
```

See [http://ubuntuforums.org/showpost.php?p=6896157&postcount=5](http://ubuntuforums.org/showpost.php?p=6896157&postcount=5)
for how to wake your machine up at 5am every day.
Add ```
cvlc reveille.ogg
``` to /etc/rc.local and you have an alarm clock :)

---

### Post by wersdaluv on 2009-03-18
> **Bodsda said:**
> [SIZE="4"]_Your friends_[/SIZE]

[LIST]
[*]Man pages (man sudo)
[*]Google (This is the greatest undisputed resource you have)
[*]--help (If you need to know about a  programs command line options use <command> --help e.g. mv --help)
[/LIST]

Command line tool for downloading youtube videos

```
sudo apt-get install youtube-dl
```

consult ```
man youtube-dl
``` to learn how to use it
That's so un-pro. hehe. Just access the flash vids in /tmp/ hehe

---

### Post by Islington on 2009-03-18
> **unutbu said:**
> How to wake your computer up (by itself) after 30 minutes:

```
sudo sh -c "echo $(date '+%s' -d '+ 30 minutes') > /sys/class/rtc/rtc0/wakealarm"
sudo shutdown -P now
```

See [http://ubuntuforums.org/showpost.php?p=6896157&postcount=5](http://ubuntuforums.org/showpost.php?p=6896157&postcount=5)
for how to wake your machine up at 5am every day.
Add ```
cvlc reveille.ogg
``` to /etc/rc.local and you have an alarm clock :)

This is brilliant! Absolutely brilliant, now I can take a nap and tell my comp to wake me up. 


wersdaluv: some flash vids dont show up in /tmp for some reason. Most obvious example hulu.

---

### Post by Islington on 2009-03-18
> **3rdalbum said:**
> --------
Placing a little penguin ornament on top of your computer will prevent most kernel panics, and cause your computer to run faster.
--------


Or a tasmanian devil is reported to work just as well ([Source.](http://www.phoronix.com/scan.php?page=news_item&px=NzE1MA))

---

### Post by lykwydchykyn on 2009-03-18
- SSH is the swiss army knife of networking on Linux.  It covers a wide variety of functions -- remote terminal, remote desktop, file sharing, file synchronization, encrypting other services.  If you learn one CLI program, learn SSH.

 - If you use a full blown desktop environment like GNOME, KDE, or XFCE, also install a minimal window manager like jwm, openbox, or icewm.  That way, if something gets screwed up in your main environment (bad compiz setting, stuck lock file, etc) you still have a graphical environment to log into so you don't have to fix it all in a VT.

---

### Post by Islington on 2009-03-18
bump!

---

### Post by DougieFresh4U on 2009-03-18
> **Sealbhach said:**
> I saw someone give another way to open up an app in the terminal which will not close when the terminal is closed:

```
*command* &disown
```


.

I know the command name 'nohup' , but I have forgotten if it's before or after what ever it is you want to stay open from terminal.
Some one care to help out on this one please?

---

### Post by yabbadabbadont on 2009-03-18
> **DougieFresh4U said:**
> I know the command name 'nohup' , but I have forgotten if it's before or after what ever it is you want to stay open from terminal.
Some one care to help out on this one please?

Go back one page...  :lol:

Edit: OK, two pages since this one is on a new one.  :D

---

### Post by DougieFresh4U on 2009-03-18
> **yabbadabbadont said:**
> Go back one page...  :lol:

Edit: OK, two pages since this one is on a new one.  :D

That's twice today I have gotten myself into something without reading the whole thread :(
Thanks

---

### Post by red_Marvin on 2009-03-18
> **vambo said:**
> As an adendum
<Shift> <Insert> will also do the pasting

Also, ctrl+insert copies to clipboard and shift-delete cuts, this dates back to the dos days (msdos edit and qbasic accepts it). However, note that in nautilus shift-delete is "delete file permanently" (ie like rm)

I'd also recommend learning a cli web browser; links, link2, lynx, w3m - great to search for help with if X breaks down, to that list I should probably add irssi or somesuch.

Oh, and learn ed... it is the standard text editor.

---

### Post by chris4585 on 2009-03-18
Here are some things I've learned by just messing around with, ctrl, alt, shift, scrolling, and middle mouse click mostly, which has taught me that these combinations are everywhere.

Hold down middle mouse button on a file and drag it somewhere to link/copy/move it somewhere else.

Holding ctrl and the middle mouse button with a file/folder on the desktop with compiz cube/sphere/etc.. will do the same as holding the middle mouse button in nautilus, helpful if you want to link/copy/move a file from the desktop to a folder.

In firefox you can drag/drop links to FILES to automatically download to a location in nautilus including the desktop.  This also works with image links to files, aka a image link to a video will work too.

ctrl + scroll in firefox will increase/decrease the size of the page

ctrl + h in nautilus will unhide files, and ctrl + h again will hide them again

To create a hidden file just add a period infront of the file name, such as .file-name-example.txt

In gnome-terminal ctrl+shift+v will paste whatever is in your clipboard.

In firefox middle clicking on a link will open the link in a new tab, same goes for nautilus with a folder.

alt + left click on a window will move a window

In nautilus with list view, hold down ctrl and select a file, and select another file while holding down ctrl, and another and you can move those certain files only or you can link/copy/move those certain files drag and droping with the middle mouse button, or just regular drag and drop will work too.

You can select in bulk with nautilus in list view with selecting one file to initiate the starting point, and holding down shift to a file way down the list, you will then have a bunch of selected files

(I just now discovered this works in other views, but to me seems most useful in list view).

With compiz enabled and with the cube/sphere/etc.. using the middle mouse button will initiate the cube/sphere/etc..

Holding down ctrl + scrolling in nautilus and other apps usually makes items bigger.

---

### Post by MaxIBoy on 2009-03-18
> **chris4585 said:**
> Here are some things I've learned by just messing around with, ctrl, alt, shift, scrolling, and middle mouse click mostly, which has taught me that these combinations are everywhere.

Hold down middle mouse button on a file and drag it somewhere to link/copy/move it somewhere else.

Holding ctrl and the middle mouse button with a file/folder on the desktop with compiz cube/sphere/etc.. will do the same as holding the middle mouse button in nautilus, helpful if you want to link/copy/move a file from the desktop to a folder.

In firefox you can drag/drop links to FILES to automatically download to a location in nautilus including the desktop.  This also works with image links to files, aka a image link to a video will work too.

ctrl + scroll in firefox will increase/decrease the size of the page

ctrl + h in nautilus will unhide files, and ctrl + h again will hide them again

To create a hidden file just add a period infront of the file name, such as .file-name-example.txt

In gnome-terminal ctrl+shift+v will paste whatever is in your clipboard.

In firefox middle clicking on a link will open the link in a new tab, same goes for nautilus with a folder.

alt + left click on a window will move a window

In nautilus with list view, hold down ctrl and select a file, and select another file while holding down ctrl, and another and you can move those certain files only or you can link/copy/move those certain files drag and droping with the middle mouse button, or just regular drag and drop will work too.

You can select in bulk with nautilus in list view with selecting one file to initiate the starting point, and holding down shift to a file way down the list, you will then have a bunch of selected files

(I just now discovered this works in other views, but to me seems most useful in list view).

With compiz enabled and with the cube/sphere/etc.. using the middle mouse button will initiate the cube/sphere/etc..

Holding down ctrl + scrolling in nautilus and other apps usually makes items bigger.
About half of those work on almost all programs. But I must admit I did not know you could middle click-n-drag.

---

### Post by DOS4dinner on 2009-03-19
Did anyone mention xkill? I love brutally killing programs;)

Simply hit alt-f2, then type xkill and hit enter. Your mouse becomes an x, and the next program you click on will be killed instantly.

Also, this terminal commmand:

xrandr -s 0

It resets your monitor's resolution back to what it should be. Useful for wine apps that crash, but leave your desktop all huge and 640x480.

---

### Post by FuturePilot on 2009-03-19
Ever forget to use sudo in front of some command that needed to be run as root? Don't waste your time pressing the up arrow and editing it or retyping it, just do 
```
sudo !!
```
and it executes the previous command with sudo in front of it. :)

---

### Post by Bou on 2009-03-19
> **unutbu said:**
> How to wake your computer up (by itself) after 30 minutes:

```
sudo sh -c "echo $(date '+%s' -d '+ 30 minutes') > /sys/class/rtc/rtc0/wakealarm"
sudo shutdown -P now
```

See [http://ubuntuforums.org/showpost.php?p=6896157&postcount=5](http://ubuntuforums.org/showpost.php?p=6896157&postcount=5)
for how to wake your machine up at 5am every day.
Add ```
cvlc reveille.ogg
``` to /etc/rc.local and you have an alarm clock :)

That's the most amazing computer-related thing I've seen in a while. How come no one has done a GUI for that yet?

---

### Post by sim-value on 2009-03-19
> **Bou said:**
> That's the most amazing computer-related thing I've seen in a while. How come no one has done a GUI for that yet?

That doesnt work for me :(

---

### Post by t0p on 2009-03-19
> **smartboyathome said:**
> It [tab-completion] doesn't work with sudo.

Yes it does.

---

### Post by t0p on 2009-03-19
> **chris4585 said:**
> 
To create a hidden file just add a period infront of the file name, such as .file-name-example.txt
.

To un-hide a hidden file, just remove the period from the start of the filename.  
 :)

---

### Post by t0p on 2009-03-19
Oh yeah, this is a good one: **apropos**.  Say you're looking for a certain command or program that is to do with browsers.  Type in the command:

```
t0p@ubunty:~$ apropos browser
alien-arena-browser (6) - wrapper script to run the Alien Arena browser.
gnome-moz-remote (1) - remote control of browsers.
goad-browser (1)     - Graphical GOAD browser
gthumb (1)           - an image viewer and browser for GNOME
infobrowser (1)      - read Info documents
kdcop (1)            - A graphical DCOP browser/client
konqueror (1)        - Web browser, file manager, ...
libsmbclient (7)     - An extension library for browsers and that can be used...
lynx (1)             - a general purpose distributed information browser for ...
sensible-browser (1) - sensible editing, paging, and web browsing
smbtree (1)          - A text based smb network browser
viewres (1)          - graphical class browser for Xt
w3m (1)              - a text based Web browser and pager
www-browser (1)      - a text based Web browser and pager
x-www-browser (1)    - Web browser, file manager, ...
xfbrowser4 (1)       - wrapper script to run user defined browser

```

I find this one very very useful.

---

### Post by sisco311 on 2009-03-20
to open URL's or files from a terminal with the preferred application:

```

exo-open url's or path/to/files                               #xfce4

gnome-open http://ubuntuforums.org/showthread.php?t=520091    #gnome

kde-open url's or path/to/files                               #kde

```

---

### Post by FuturePilot on 2009-03-20
> To create a hidden file just add a period infront of the file name, such as .file-name-example.txt

Another way to do this is to create a file called .hidden and put the names of directories and files you want to be hidden inside of it. This is useful if you want something hidden out of your way but renaming it with a dot in front of it would probably break something.

For example here's the contents of my .hidden
```
Examples
Templates
```

This will only work with Nautilus though.

---

### Post by imlinux on 2009-03-20
i don't know if someone has discussed this tip to download/get any video which ever you play in your browser,let the video load first completely,after this go to "/tmp" directory  there you can find video file most of the time, copy that file to home you can play it with totem anytime.

---

### Post by olejorgen on 2009-03-21
Here's a litte gem I recently found out about:

> 
In many GTK applications (not all fro some reason) hovering the mouse over a menu item and pressing a key combo. (eg. ctrl + k) assigns this combo as a keybinding for the menu item.

You need to add
gtk-can-change-accels = 1
in you ~/.gtkrc-2.0 first though


---

### Post by kimda on 2009-03-21
alt+. cycle through previous commands or use up down arrows. This is very handy together with ctrl+r and history. You can execute previous commands by using !number. So if 1 in history is ls /home, !1 will execute the same command.  Also cd - will return you to last location. Another useful command is pushd.

By entering pushd you will return to the previous directory. Just enter cd /etc and then enter "pushd". You will jump right back from where you came. I never use pushd anymore since I think "cd -" does the same thing and is faster to type. I've put alot of tips on my squidoo page. The link is in my signature.

Another nice tip is add the following line to you're .bashrc
alias upgrade='sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean'

Now you can use the command upgrade to upgrade to upgrade to the latest packages. you can add more aliases or make shell scripts to save time typing those long commands.

---

### Post by MaxIBoy on 2009-03-21
Commands to run in a framebuffered virtual terminal with no X11 running:
```
mplayer -fb video_file #watch movies

fbi image_file #framebuffered image viewer. Features zooming and panning. 
#If you open multiple files with it, you'll be able to use "next image" 
#and "previous image" buttons.

```> **t0p said:**
> Oh yeah, this is a good one: **apropos**.  Say you're looking for a certain command or program that is to do with browsers.  Type in the command:

```
t0p@ubunty:~$ apropos browser
alien-arena-browser (6) - wrapper script to run the Alien Arena browser.
<snip>

```I find this one very very useful.
Unrelated, buy I see that you have Alien Arena installed from the repositories. The repository version is almost a year out of date (unless you've installed it from getdeb.) 

If you want my personal recommendation, checkout the game from the Subversion repository: svn://svn.icculus.org/alienarena/trunk

---

### Post by Sealbhach on 2009-03-21
> **MaxIBoy said:**
> 

If you want my personal recommendation, checkout the game from the Subversion repository: svn://svn.icculus.org/alienarena/trunk

How do you install something with Subversion?


.

---

### Post by MaxIBoy on 2009-03-21
> **Sealbhach said:**
> How do you install something with Subversion?


.
Checkout whatever is in the Subversion repo:
```
svn co svn://URL_of_svn_repository destination_directory 
```
Destination_directory doesn't have to already exist. If you don't specify destination_directory, it will choose the default directory name of the specific SVN repo you are using.



After that, it depends. Sometimes you get pre-compiled binaries that can be run. Sometimes you get installer scripts. Sometimes you just get source code. You can have an SVN repo of whatever you like. For example, you might checkout the latest draft of someone's book from SVN. 




In the case of Alien Arena, you get pre-compiled binaries for Windows and the source code. To get Linux binaries, just compile from source:
```
cd alienarena
cd source
make clean #if you've already installed this before, you should always make clean, otherwise the two versions will clash
make 
make install
cd ..
sudo chmod +x crx.sdl
```

After that, you can go to the "alien arena" directory you've created and double-click "crx.sdl." Note that "crx" works too, but for most people, sound won't work unless you use "crx.sdl." 




Repeat this process whenever you want to update. For Alien Arena, SVN hosts the developers' codebase, so you get new features as soon as they're written.

---

### Post by ninjapirate89 on 2009-03-21
> **Bodsda said:**
> 

Command line tool for downloading youtube videos

```
sudo apt-get install youtube-dl
```

consult ```
man youtube-dl
``` to learn how to use it

This is not necessary. If you are at say [http://www.youtube.com/watch?v=AAdXowU1cBI](http://www.youtube.com/watch?v=AAdXowU1cBI) simply type the word "pwn" in front of youtube as shown [http://www.pwnyoutube.com/watch?v=AAdXowU1cBI](http://www.pwnyoutube.com/watch?v=AAdXowU1cBI) and it will open to another page with the option to download the video. Only a web browser is needed.

---

### Post by Sealbhach on 2009-03-21
> **MaxIBoy said:**
> 
Repeat this process whenever you want to update. For Alien Arena, SVN hosts the developers' codebase, so you get new features as soon as they're written.

Cool, thanks. It's a bit like wget?

.

---

### Post by unutbu on 2009-03-21
> **Bou said:**
> How come no one has done a GUI for that yet?

Here is a GUI for configuring your machine to automatically wake at a certain time.

Requirements for the script to work:
[list]
[*]Your linux kernel version must be >= 2.6.22 (Gutsy and above)
[*]Your BIOS must have support to wake. See [http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup)
[*]You must have ACPI enabled. (You can not be booting with the kernel option acpi=off, for example).
[/list]

Save the attached script at /usr/local/bin/set_wake.py

Make it executable:```


chmod 755 /usr/local/bin/set_wake.py
```

Run:
```

gksu set_wake.py
```

So as not to drag this thread off topic, if you run into any problems, please start a new thread, and PM me with the link.

---

### Post by MaxIBoy on 2009-03-22
> **Sealbhach said:**
> Cool, thanks. It's a bit like wget?

.
Subversion is a version control system. If you have a complex project you're working on, you use a VCS. When you modify something, you "commit" a new version. All versions throughout the history of the project are stored. When you want to retrieve a version, you "check out" that version (think "check out a book from the library," not "check out that wierd tree.") It's like hitting "save as" every time you make a change, only:

[LIST=1]
[*]You don't have thousands of files to sift through.
[*]It keeps track of a whole project, not just one file at a time.
[*]It takes up *much* less space, because the archive is heavily compressed.
[/LIST]
Version control systems include CVS, Subversion (SVN,) Mercurial (Hg,) Bazaar (Bzr,) and Git. 

The "svn co" command "checks out" a revision from a subversion archive which is set up to allow downloading over the Internet. Unless otherwise specified, it will pick the most recent revision.

---

### Post by billgoldberg on 2009-03-22
> **Mehall said:**
> Generally, if you use scrollwheel, you scroll on whatever window the cursor is over, not necessarily the active window

[


This is one of my favorite features.

---

### Post by t0p on 2009-03-22
Want to download video from youtube?  Easy!  Watch the video you want to download.  Next, and *before you leave that web page*, go look in the /tmp directory.  There should be a flash video file with a name like "FlashfQ5a1h".  That's the file you want.  So copy it to your desktop.  Job done! :)

---

