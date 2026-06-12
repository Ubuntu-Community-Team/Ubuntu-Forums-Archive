---
title: "Share your commandline cheat sheets"
date: 2008-10-03
forum: The Cafe
---

### Post by billgoldberg on 2008-10-03
Ok, I have been needing to do this for a long time.

I need a cheat sheet of commands.

I know there are some on the web, but they are mostly basic lists.

Do you have a list with useful commands?

Share them.

*(I'll be happy to rip them)*

ps: I have a basic one here:

[http://linuxowns.wordpress.com/2008/04/23/hardy-cheat-sheet/](http://linuxowns.wordpress.com/2008/04/23/hardy-cheat-sheet/)

---

### Post by dbbolton on 2008-10-03
It seems kind of redundant to open a root shell with sudo. I guess it's because Ubuntu doesn't set a root password by default.

Here are some handy basic commands to know:

cat - print contents of a file
cd - change directories
chmod - change file permissions
cp - copy a file
grep - searches for a given string
ln - link files
ls - list the files in the current directory
mkdir - make directory
more - helps page through output ( cat file.txt | more)
mv - move a file 
rm - delete files and directories 
top - shows resource usage 

Helpful symbols:
| - pipe the output of one command into the next
& - detach process from shell (run in background)
&& - chain two or more commands together (if the first is successful)

---

### Post by hansdown on 2008-10-03
Fosswire has a couple good printable sheets.  

[http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/](http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/)

[http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/](http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/)

---

### Post by artir on 2008-10-03
And don't forget the >
useful when doing top > top.txt or lspci > log.txt

---

### Post by crimesaucer on 2008-10-03
These 4 commands are useful:




-- CHANGE folder of .svg's to .png's and resize all the images:

```
for i in *.svg; do inkscape -f "$i" -e "$i.png" -w24 -h24; done
```




-- CHANGE one .svg to a .png and resize the image:

```
inkscape *.svg --export-png=*.png -w24 -h24
```



-- check hard drive temp:


```
hddtemp /dev/sda
```


-- GDM screenshot:

```
chvt 7 ; sleep 5 ; XAUTHORITY=/var/lib/gdm/:0.Xauth DISPLAY=:0.0 import -window root /tmp/gdm-shot.png
```

---

### Post by fatality_uk on 2008-10-03
One I use a lot is:
> ls -ltr
ls -a -ltr
For seeing what is actually in a directory

---

### Post by LaRoza on 2008-10-03
```

~$cat .bashrc | grep "alias"
# ~/.bash_aliases, instead of adding them here directly.
alias code='cd /media/STORAGE/code/'
alias ccode='cd /media/STORAGE/cCode/'
alias py='cd /media/STORAGE/code/pythonCode/'
alias tti='./ttime'
alias off='/home/laroza/off'
alias search='apt-cache search'
alias install='sudo aptitude install'
alias clean='sudo apt-get clean && sudo apt-get autoremove'
alias upgrade='sudo apt-get update && sudo apt-get upgrade && sudo apt-get autoclean && sudo apt-get clean'
alias pingg='ping -c 1 www.google.com'
alias targz="tar -xvvzf"
alias headset='asoundconf set-default-card headset'
alias intel='asoundconf set-default-card intel'
alias black='/home/laroza/p/.setroot'
alias tarup='tar -cvvf'
~$

```

---

### Post by cardinals_fan on 2008-10-03
```
*
```
I believe that says it all (literally!) :)

---

### Post by billgoldberg on 2008-10-04
> **LaRoza said:**
> ```

~$cat .bashrc | grep "alias"
# ~/.bash_aliases, instead of adding them here directly.
alias code='cd /media/STORAGE/code/'
alias ccode='cd /media/STORAGE/cCode/'
alias py='cd /media/STORAGE/code/pythonCode/'
alias tti='./ttime'
alias off='/home/laroza/off'
alias search='apt-cache search'
alias install='sudo aptitude install'
alias clean='sudo apt-get clean && sudo apt-get autoremove'
alias upgrade='sudo apt-get update && sudo apt-get upgrade && sudo apt-get autoclean && sudo apt-get clean'
alias pingg='ping -c 1 www.google.com'
alias targz="tar -xvvzf"
alias headset='asoundconf set-default-card headset'
alias intel='asoundconf set-default-card intel'
alias black='/home/laroza/p/.setroot'
alias tarup='tar -cvvf'
~$

```

Interesting.

I might start doing this when intrepid comes out.

---

### Post by LaRoza on 2008-10-04
> **billgoldberg said:**
> Interesting.

I might start doing this when intrepid comes out.

Aliases are quite handy, especially ones for apt and tar, as the most command things I do are rather verbose.

---

### Post by urukrama on 2008-10-04
> **billgoldberg said:**
> Interesting.

Aliases are very handy. See [this thread]("http://ubuntuforums.org/showthread.php?t=679762") for more of them.

---

### Post by billgoldberg on 2008-10-04
> **urukrama said:**
> Aliases are very handy. See [this thread]("http://ubuntuforums.org/showthread.php?t=679762") for more of them.

I know what aliases are, just the commands used in laroza's bashrc file seem very handy.

---

### Post by Nxion on 2008-10-09
> **LaRoza said:**
> ```

~$cat .bashrc | grep "alias"
# ~/.bash_aliases, instead of adding them here directly.
alias code='cd /media/STORAGE/code/'
alias ccode='cd /media/STORAGE/cCode/'
alias py='cd /media/STORAGE/code/pythonCode/'
[COLOR=Red]**alias tti='./ttime'**[/COLOR]
alias off='/home/laroza/off'
alias search='apt-cache search'
alias install='sudo aptitude install'
alias clean='sudo apt-get clean && sudo apt-get autoremove'
alias upgrade='sudo apt-get update && sudo apt-get upgrade && sudo apt-get autoclean && sudo apt-get clean'
alias pingg='ping -c 1 www.google.com'
alias targz="tar -xvvzf"
alias headset='asoundconf set-default-card headset'
alias intel='asoundconf set-default-card intel'
**[COLOR=Red]alias black='/home/laroza/p/.setroot'[/COLOR]**
alias tarup='tar -cvvf'
~$

```

I am curious, what are these two alias for? I highlighted them in red.

---

### Post by Nxion on 2008-10-09
> **billgoldberg said:**
> Ok, I have been needing to do this for a long time.

I need a cheat sheet of commands.

I know there are some on the web, but they are mostly basic lists.

Do you have a list with useful commands?

Share them.

*(I'll be happy to rip them)*

ps: I have a basic one here:

[http://linuxowns.wordpress.com/2008/04/23/hardy-cheat-sheet/](http://linuxowns.wordpress.com/2008/04/23/hardy-cheat-sheet/)

I would be happy to share mine once I am home tonight, at work at the moment.

---

### Post by adamogardner on 2008-10-09
This one is pretty intense:
 [http://soledadpenades.com/articles/ubuntu/ubuntu-linux-cheatsheet/](http://soledadpenades.com/articles/ubuntu/ubuntu-linux-cheatsheet/)

---

### Post by billgoldberg on 2008-10-10
Keep em coming.

When I have enough I'll toss them all into one big text file and offer it as a download for all to enjoy.

---

### Post by LaRoza on 2008-10-10
> **Nxion said:**
> I am curious, what are these two alias for? I highlighted them in red.

Programs I wrote for my own use. One alters an X setting, which I don't use anymore and the other runs a clock I wrote.

---

### Post by kpkeerthi on 2008-10-10
Most of the commands have already been posted. Here are the few others (as much as I could remember)

```
thunar -B
```

I use the following commands in BASH scripts for mass updation.
```

id3v2 -D <file>.mp3
mp3gain -r -k <file>.mp3
convert cover.jpg -scale 100x100 cover.bmp

```

Other convert [tricks]("http://www.imagemagick.org/script/convert.php")

---

### Post by qazwsx on 2008-10-10
Some neat tricks via dcop. Might be usefull in some scripts or as aliases. 
You can not use these commands in KDE4 (D-BUS) without specific KDE 3 program. 
```

dcop klipper klipper getClipboardContents
dcop klipper klipper setClipboardContents "content"
dcop kmix Mixer0 setMasterVolume <0-100>
dcop kicker kicker restart

```

---

### Post by spupy on 2008-10-10
```
alias ..='cd ..'  #easy go up
alias lost_prompt='export PS1="\[\033[01;32m\]>: "' #4 8 15 16 23 42
alias gpsa='ps -A | grep' #check if a process is running
```

more later...

---

### Post by adamogardner on 2008-10-14
I justy found onother one.  This one is REally GrEaT!!
[http://blog.lxpages.com/linux_network.html](http://blog.lxpages.com/linux_network.html)

---

### Post by rakris on 2008-10-15
Most used.

$find /home -name "blah"

$df -h

$ps -e

$killall <blah>

$sudo apt-get update

$sudo apt-get install blah

$sudo mount -a

$ping google.com

$tar -xvzf blah

$tar -xvjf blah

$unrar e blah

**$fortune -o**:lolflag:

---

### Post by Nxion on 2008-10-15
> **LaRoza said:**
> Programs I wrote for my own use. One alters an X setting, which I don't use anymore and the other runs a clock I wrote.

Awesome, Thanks :)

---

### Post by adamogardner on 2008-10-15
here's one for firefox.  [http://lesliefranke.com/files/reference/firefoxcheatsheet](http://lesliefranke.com/files/reference/firefoxcheatsheet) 

no that link is totally whacked out. here it is:
 [http://lesliefranke.com/files/reference/firefoxcheatsheet.html](http://lesliefranke.com/files/reference/firefoxcheatsheet.html)

---

### Post by jgrabham on 2008-10-15
> **billgoldberg said:**
> Interesting.

I might start doing this when intrepid comes out.

Do it now, then just copy your ~/.bashrc or ~/.bashrc_aliases when the time comes.

---

### Post by dbbolton on 2008-10-15
> **adamogardner said:**
> here's one for firefox.  [http://lesliefranke.com/files/reference/firefoxcheatsheet](http://lesliefranke.com/files/reference/firefoxcheatsheet)
**Error 404 &#8212; Page Not Found!**

---

### Post by Iowan on 2008-10-15
Some of the ones I use:

cd
cp
less
locate
ls -al
lshw
lsof (this is a new one for me)
lspci
mv
sudo (sometimes gksu)
sudo halt (on server)
man (couldn't live without this one)
ping
ps -ax
rm
smbtree
touch

---

### Post by MaxIBoy on 2008-10-16
I made this for certain obvious reasons.
```
maxtothemax@maxtothemax-laptop:~$ cat /usr/bin/dos
#! /bin/bash
/home/maxtothemax/.wine/drive_c/windows/system32/cmd.exe
maxtothemax@maxtothemax-laptop:~$ 
```


But as far as a cheat sheet for bash goes, you can't beat this:
```
man bash
```
Yes, that's right, read the dang manual.

---

### Post by Prefix100 on 2008-10-16
*****, it is by far the most useful thing when using the CLI.

---

### Post by adamogardner on 2008-10-16
man bash is pretty tight.
try this: [http://blog.transmit.net/2008/10/my-best-unix-tricks.html](http://blog.transmit.net/2008/10/my-best-unix-tricks.html)

---

### Post by schauerlich on 2008-10-16
My cheatsheet?

```
man
```

---

### Post by caljohnsmith on 2008-10-16
Only if you have a wireless card would you be interested in this one...
```
watch 'sudo iwlist wlan0 scan | grep -A 10 -B 1 "My Home WLAN"'
```
The command will update every two seconds (at least it tries to, but the iwlist scan is slower sometimes), so you can see how the signal strength of "My Home WLAN" changes as you move your computer or antenna around to tweak for the best signal.

---

### Post by MaxIBoy on 2008-10-16
Actually, that's exactly what I needed on my laptop. Now if only I knew the command to *join* a wireless network, I would be able to spend whole days in textmode, which would be very cool.

---

### Post by cardinals_fan on 2008-10-16
> **MaxIBoy said:**
> Actually, that's exactly what I needed on my laptop. Now if only I knew the command to *join* a wireless network, I would be able to spend whole days in textmode, which would be very cool.
Do you mean like "ifconfig wlan0 essid *"?

---

### Post by unutbu on 2008-10-17
isconnected.py:
[PHP]#!/usr/bin/env python
import os
print True if os.system('dig +time=1 +retry=0 192.168.1.1 2>/dev/null 1>&2')==0 else False[/PHP]
This checks if my network connection is running.
If the connection is down, it reports "False" after a short timeout. I haven't found a way to make ping's timeout (ping -w1) work similarly.

---

### Post by MaxIBoy on 2008-10-17
> **cardinals_fan said:**
> Do you mean like "ifconfig wlan0 essid *"?

Oh! I was muddling around with iwconfig. 

Is there a way to filter out password-protected servers?

---

### Post by -grubby on 2008-10-17
Here's some useful, not so useful, and not working aliases

```

nathan@linda:~$ alias
alias ..='cd ..'
alias aaa='python -c "exec('\''import\tmath\nwhile\tTrue:\n\ttry:print(math.pi)\n\texcept\t
KeyboardInterrupt:print(\'\''suckers\'\'')'\'')"'
alias backup-acc='/home/nathan/nathan/backups/hostgator/sql/fluxbb/backup'
alias backup-ob='/home/nathan/nathan/backups/hostgator/sql/obforums/backup'
alias backup-omgpp='/home/nathan/nathan/backups/hostgator/sql/omgpp/backup'
alias backup-wiki='/home/nathan/nathan/backups/hostgator/sql/wiki/backup'
alias edbash='nano ~/.bashrc'
alias f-ssh='ssh nathangrubb@linda.homelinux.org'
alias fortune='fortune -a'
alias kronq='/usr/lib/kde4/bin/kfmclient openProfile webbrowsing'
alias ls='ls --color=auto'
alias nexuiz-fp='nexuiz +connect 76.189.184.232'
alias push-devel='bzr push sftp://nathangrub@bazaar.launchpad.net/~nathangrub/grubbot/devel'
alias pythondoc='python -c "help()"'
alias r-ssh='ssh nathangrubb@nathanr.ca'

```

---

### Post by schauerlich on 2008-10-17
> **nathangrubb said:**
> ```

alias edbash='nano ~/.bashrc'

```

You always made fun of me for using nano.

---

### Post by cardinals_fan on 2008-10-17
> **EDavidBurg said:**
> You always made fun of me for using nano.
You *what*? :)

---

### Post by schauerlich on 2008-10-17
> **cardinals_fan said:**
> You *what*? :)

Don't worry, I'm committed to learning vim now. :)

---

### Post by MaxIBoy on 2008-10-17
Pfft... cat+echo+middle-click = hard core.

---

### Post by adamogardner on 2008-10-18
> **MaxIBoy said:**
> Pfft... cat+echo+middle-click = hard core.

I always wondered, how can I middle click a touchpad?

---

### Post by adamogardner on 2008-10-18
I know this is a basic list of commands but the examples were excellent for me to get the hang of the command line.  I learn by doing. And trying out these were a nice opportunity to learn the basics but in a better way than any of the other basic manuals which all seem to say exactly the same thing by doing. And trying out these were a nice opportunity to..oops! now I'm doing it.

[http://linuxconfig.org/Portal:Linux_Commands](http://linuxconfig.org/Portal:Linux_Commands)

---

### Post by p_quarles on 2008-10-18
> **EDavidBurg said:**
> Don't worry, I'm committed to learning vim now. :)
Hmm. Not sure I understand this thread of the conversation. Vim is a very powerful text editor, but I'm not sure what relation (if any) it bears to nano. :confused:

---

### Post by Anzan on 2008-10-18
> **adamogardner said:**
> I always wondered, how can I middle click a touchpad?

Chord the right and left buttons underneath.

---

### Post by -grubby on 2008-10-18
> **EDavidBurg said:**
> You always made fun of me for using nano.

You used it on python scripts, not config files

---

### Post by -grubby on 2008-10-18
> **adamogardner said:**
> I always wondered, how can I middle click a touchpad?

press left and right at the same time

---

### Post by rakris on 2008-10-20
One help needed.

Can anybody post link to some simple/advanced bash exercises with optionally answers to it.?

Just for practice...\\:D/

---

### Post by unutbu on 2008-10-20
rakris, you might find this helpful:
[http://cis68b1.mikecappella.com/calendar.php](http://cis68b1.mikecappella.com/calendar.php)

---

### Post by billgoldberg on 2008-10-20
Resetting gnome-panels:

```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

If anyone has commands like that, please share.

---

### Post by unutbu on 2008-10-20
To change the background wallpaper while using gnome desktop:
```
gconftool-2 -t string -s /desktop/gnome/background/picture_filename ~/images/chipmunk/IMG_0450.JPG
```

Get info on font rendering settings:
```
gconftool-2 -a --all-dirs /desktop/gnome/font_rendering
```
Returns:
#  rgba_order = rgb
#  antialiasing = rgba
#  dpi = 92
#  hinting = full

Stop automounting of external devices:
```
gconftool-2 --type bool --set /desktop/gnome/volume_manager/automount_drives 'false'
gconftool-2 --type bool --set /apps/nautilus/preferences/media_automount_open 'false'
```

Stop partitions from showing up on the desktop:
```

gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible 'false'
```

Disables user switching:
```
gconftool-2 --type bool --set /desktop/gnome/lockdown/disable_user_switching 'false'
```

Change theme to Clearlooks:
```

gconftool-2  --type string /desktop/gnome/interface/gtk_theme 'Clearlooks'

```

---

### Post by billgoldberg on 2008-10-20
Nice, thanks.

I've already made a basic list of everything posted here:

> Helpful symbols:
| - pipe the output of one command into the next
& - detach process from shell (run in background)
&& - chain two or more commands together (if the first is successful)

Basics:

[http://linuxconfig.org/Portal:Linux_Commands](http://linuxconfig.org/Portal:Linux_Commands)

man - rtfm
cat - print contents of a file
cd - change directories
chmod - change file permissions
cp - copy a file
grep - searches for a given string
ln - link files
ls - list the files in the current directory
mkdir - make directory
more - helps page through output ( cat file.txt | more)
mv - move a file
rm - delete files and directories
top - shows resource usage

Specific commands

Puts outcome of lspci command in a textfile:
lspci > log.txt 

Change folder of .svg's to .png's and resize all the images:
for i in *.svg; do inkscape -f "$i" -e "$i.png" -w24 -h24; done

CHANGE one .svg to a .png and resize the image:
inkscape *.svg --export-png=*.png -w24 -h24

Check Hard Drive Temp:
hddtemp /dev/sda

GDM screenshot:
chvt 7 ; sleep 5 ; XAUTHORITY=/var/lib/gdm/:0.Xauth DISPLAY=:0.0 import -window root /tmp/gdm-shot.png

Search for a package:
apt-cache search packagename

Change default sound card (example):
asoundconf set-default-card intel

Join wireless network:
ifconfig wlan0 essid xxx

Signal strenght wireless network:
watch 'sudo iwlist wlan0 scan | grep -A 10 -B 1 "My Home WLAN"'

Connect to ssh:
ssh -X user@server

Resetting gnome-panels:
gconftool --recursive-unset /apps/panel && killall gnome-panel

To change the background wallpaper while using gnome desktop:
gconftool-2 -t string -s /desktop/gnome/background/picture_filename ~/images/chipmunk/IMG_0450.JPG

Info font rendering settings
gconftool-2 -a --all-dirs /desktop/gnome/font_rendering

Stop automounting of external devices:
gconftool-2 --type bool --set /desktop/gnome/volume_manager/automount_drives 'false'
gconftool-2 --type bool --set /apps/nautilus/preferences/media_automount_open 'false'

Stop partitions from showing up on the desktop:
gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible 'false'

Disables user switching:
gconftool-2 --type bool --set /desktop/gnome/lockdown/disable_user_switching 'false'

Change theme to Clearlooks:
gconftool-2  --type string /desktop/gnome/interface/gtk_theme 'Clearlooks'


Links to other cheat sheets:
[http://soledadpenades.com/articles/ubuntu/ubuntu-linux-cheatsheet/](http://soledadpenades.com/articles/ubuntu/ubuntu-linux-cheatsheet/)
[http://linuxowns.wordpress.com/2008/04/23/hardy-cheat-sheet/](http://linuxowns.wordpress.com/2008/04/23/hardy-cheat-sheet/)
[http://blog.lxpages.com/linux_network.html](http://blog.lxpages.com/linux_network.html)
[http://blog.transmit.net/2008/10/my-best-unix-tricks.html](http://blog.transmit.net/2008/10/my-best-unix-tricks.html)

Keep 'em coming!

---

### Post by caljohnsmith on 2008-10-20
EDIT: Actually, I just realized that the following does not really fit in with the original thread subject (sorry about that), but I'll leave it in case someone might find it useful anyway. 

When you run a command from a launcher as "run in terminal", it closes the terminal as soon as the command completes, which can be really annoying if you want to see the output of the command. So instead of using the "run in terminal" option, just run the command or bash script with:
```
gnome-terminal -x bash -c "[COLOR="Blue"]<commands or bash script>[/COLOR];read -n1"
```
The "read -n1" makes it so the terminal won't close until you press some key. For instance, to see who you are logged in as, your kernel version, and your free RAM and swap space (just a random cheesy example):
```
gnome-terminal -x bash -c "[COLOR="Blue"]whoami;echo;uname -r;echo;free[/COLOR];read -n1"
```
The "echo" commands are just to create a new line between the other commands to make it look at little bit nicer.

Another really good option for running commands/bash scripts in a window is zenity:
```
{ [COLOR="Blue"]whoami;echo;uname -r;echo;free;[/COLOR] }  | zenity --text-info --width=600 --height=500 --title="Cheesy Command Example"
```
And of course there are a lot of great possibilities with Zenity in bash scripts, but I assume that this thread is for commands that can be directly run at the command line. :)

---

### Post by rakris on 2008-10-21
> **unutbu said:**
> rakris, you might find this helpful:
[http://cis68b1.mikecappella.com/calendar.php](http://cis68b1.mikecappella.com/calendar.php)


Thank you very much.... :popcorn:

---

### Post by adamogardner on 2008-10-25
here's one.  after a while they all start looking alike even though they are not.  [http://yabblog.com/2008/10/25/ubuntu-reference/](http://yabblog.com/2008/10/25/ubuntu-reference/)

---

### Post by adamogardner on 2008-10-25
> **rakris said:**
> One help needed.

Can anybody post link to some simple/advanced bash exercises with optionally answers to it.?

Just for practice...\\:D/

Yes I did just that in post #43.  click the link and try the examples out,   they're all good and unique

---

### Post by caljohnsmith on 2008-10-25
Here's a complete overload of commands related to package management :shock::

To search which *installed* package a file/program comes in:
```
dpkg -S <file/program>   
```
(Note that the search term will be treated as a substring, no need to use any asterisks *). Also similar is:
```
dpkg-query --search <file/program>
```
To search which *installed or uninstalled* package a file/program comes in:
```
sudo apt-file -v update     [if haven't done it recently]
apt-file search <file/program>
```
(Again no need for *, the search term will be treated as a substring). To search the installed/uninstalled package names/descriptions for a key word:
```
apt-cache search <key word>
```
To search for available versions of a package, or to show the version all ready installed, and to show which repository it is available in:
```
apt-cache policy <package>
```
To try installing a different version:
```
sudo apt-get install <package>=version
```
To add a CD-ROM as a repository (like the Ubuntu Live CD):
```
sudo apt-cdrom add
```
Get a list of all installed packages:
```
dpkg --get-selections
```
Format and output that list into a file:
```
dpkg --get-selections | grep '[[:space:]]install$'| awk '{print $1}' > installed_packages.txt
```
To search through all installed packages for a substring in the package name, e.g. to find nautilus related packages:
```
dpkg --get-selections *nautilus*
```
Similar is:
```
dpkg -l *nautilus*
```
To use dpkg to install a bunch of .deb files in a directory:
```
sudo dpkg -i /directory/*.deb
```
Reconfigure an all ready installed package:
```
sudo dpkg-reconfigure <package>
```
To clean out packages in /var/cache/apt/archives:
```
sudo apt-get clean
```
To list the dependencies of a package:
```
apt-cache depends <package name>
```
(Note the file that keeps track of installed packages is /var/lib/dpkg/status). To find dependencies of packages:
```
sudo debfoster
```

---

### Post by rakris on 2008-10-28
> **adamogardner said:**
> Yes I did just that in post #43.  click the link and try the examples out,   they're all good and unique

Wow. That was very helpful..Thanks...

---

### Post by ukripper on 2008-10-28
Some commands from my personal commands-list:

_Useful Commands_

```

find / -user "alex" -exec cp {} /groups/sales \;
```


The command find / -user "alex" will find all files created by user alex. The fun thing about find is

that you can execute a command on the result of the find command by using the -exec

option. For example, if you want to copy all files of user alex to the directory /groups/sales,

use find / -user "alex" -exec cp {} /groups/sales \;. In such a command, you should

pay attention to two specific elements. First is the {} construction, which is used to refer to the

result of the find command that you&#8217;ve started with. Next is the \; element, which is used to

tell find that this is the end of the part that began with -exec.

 

```
find / -user susan &#8211;exec grep root {} \;
```


To illustrate how this rather complex construction works, let&#8217;s have a look at another

example. In this example you want to search all files owned by user susan to check if the word

&#8220;root&#8221; occurs in it. So the first thing you&#8217;d need to do is find all files that are owned by user

susan, and you&#8217;d do this by typing find / -user "susan". Next, you need to search these files

to see if they contain the word &#8220;root&#8221;. To do this, you&#8217;d need a construction like grep root *.

However, that construction is not the right way of doing it, because the grep command would

search all files in the current directory. Therefore, you first need to combine the two commands

using -exec. Next, you need to replace the * from the grep root * example by {}, which

refers to the result of the find command. So the final construction would be find / -user susan &#8211;exec grep root {} \;


To find drivers being used for network:
```
lshw -C network
```

To change the permissions back to original owner:

```
sudo chmod -R 600 /home/john && sudo chown -R john /home/john
```



**_VBOX_**
Code:

```
sudo aptitude install virtualbox-ose virtualbox-ose-source
```

From reading other docs, it turns out that sometimes the kernel modules break when the kernel image upgrades. One of the bug comments had instructions for building the modules:

Code:

```
sudo aptitude install build-essential module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i virtualbox-ose
sudo /etc/init.d/vboxdrv restart
```



**_HDD TOOLS_**

Here are some useful commands for troubleshooting:

To search all logs for keywords:

Code:

```
sudo egrep -i 'keyword1|keyword2|keyword3' /var/log/* > ~/errors
```

Note I am directing the output of the egrep search to a file in the home directory named "errors". It's easier to look and search through the file instead of scrolling though the terminal.

To get info on your partitions:

Code:

```
sudo hdparm -I /dev/sda > ~/sda_info
```

Again the output is directed to a file for easier viewing.

To run SMART tests on your hard drive, first install smartmontools, then:

Code:

```
sudo smartctl -t long /dev/sda
```

Then a few hours later run the following to see the final results:

Code:
```

sudo smartctl -l selftest /dev/sda
```

You can also look at the history of SMART errors being logged by the drive:

Code:

```
sudo smartctl -a /dev/sda
```

To check a drive for badblocks, boot with the live CD, don't mount the drive, find out which partition you want to scan using "sudo fdisk -l", then:

Code:
```

sudo badblocks -nvs /dev/sda
```

You can also do this, check the man page for more options:

Code:

```
sudo e2fsck -cfp /dev/sda1
```

The following will tell you if there are any blocks marked as bad on your partition:

Code:
```

sudo dumpe2fs -b /dev/sda1
```

This command lists all the IRQs and the devices assigned to them:

Code:

```
cat /proc/interrupts
```



How to mount iso as a virtual CD/DVD:-

```
mkdir ~/Desktop/ubuntu
sudo mount -t iso9660  ubuntustudio-8.04-alternate-i386.iso ~/Desktop/ubuntu

```

**_BACKUP_**
How to backup/sync using rsync over SSH 

In Terminal use following to check SSH is working:
```
$ ssh username@ip-address-remote-machine
```
create rsync script:
```
#! bin/bash

echo this script will backup to remote server
echo backup starting.......

rsync -e "ssh" -avz --progress --exclude=directory/ ~/ebooks/ username@ip-address-remote:/media/hdd/LINUX-BACKUP/server-backup
/VOSTRO/ebooks/

echo start Music sync.....

rsync -e "ssh" -avz --progress ~/Music/ username@ip-address-remote:/media/hdd/Multimedia/Music/

#rsync -e "ssh" -avz --progress ~/movies/ username@ip-address-remote:/media/hdd/Multimedia/movies/

rsync -e "ssh" -avz --progress ~/.evolution/ username@ip-address-remote:/media/hdd/LINUX-BACKUP/server-backup/VOSTRO
/.evolution/

rsync -e "ssh" -avz --progress ~/scripts/ username@ip-address-remote:/media/hdd/LINUX-BACKUP/server-backup/VOSTRO
/scripts/

rsync -e "ssh" -avz --progress ~/wallpapers/ username@ip-address-remote:/media/hdd/Multimedia/wallpapers/
echo Finished Syncing to remote Mediaserver-
echo ...............................................backup finished
```

save & exit the script e.g: backup-script.sh

Using SSH without using password everytime you backup, do following:
You need to add id_rsa.pub key to remote machine's .ssh:
On local machine generate ssh key:
```
$ ssh-keygen
``` and keep pressing enter till it finishes.

> Then copy on remote machine use SCP command to copy the key over:
$ scp [email]user@remotemachine:/home/remote-user/.ssh/id_rsa.pub[/email] .
Append to authorized_keys2 on local machine currently logged on to.
$ cat id_rsa.pub >> /home/user/.ssh/authorized_keys2
$ rm id_rsa.pub

To run the backup-script.sh --> ```
$ sh backup-script.sh
```

more to come...

---

### Post by adamogardner on 2008-10-29
linux shortcuts:  [http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)

---

### Post by Sam on 2008-10-29
Bash advanced features:

[http://www.deadman.org/bash.html](http://www.deadman.org/bash.html)
[http://www.deadman.org/bash2.html](http://www.deadman.org/bash2.html)

---

### Post by dbbolton on 2008-10-29
Here's a simple but good one to help you find the name of a command:

```
ls /usr/bin | grep "searchterm"
```Or for root commands

```
ls /usr/sbin | grep "searchterm"
```

---

### Post by Grant A. on 2008-10-29
My cheat sheet is quite obvious.

[IMG]http://tbn0.google.com/images?q=tbn:kqzWGRrrXqwB8M:http://www.ipmc.cnrs.fr/~duprat/neurophysiology/images/brain2.jpg[/IMG]

---

### Post by caljohnsmith on 2008-10-30
> **dbbolton said:**
> Here's a simple but good one to help you find the name of a command:

```
ls /usr/bin | grep "searchterm"
```Or for root commands

```
ls /usr/sbin | grep "searchterm"
```
If the command you want to find begins with "searchterm", you can just use tab-completion to do the search by entering the the search term, and then hitting tab twice to see a list of commands that begin with your search term, for example:
```
user@ubuntu-computer:~$ wh     [COLOR="Blue"]<--press TAB twice and get:[/COLOR]
whatis    which     whiptail  whoami    
whereis   while     who       whoi
```
Of course tab-completion will search all paths in your $PATH, so if you specifically want to search /usr/bin or /usr/sbin, then your method would work. Also, if you want to search for "update-grub" by entering "grub", you would have to use something like your method since the tab completion would only find commands that start with "grub", like "grub-install". :)

---

### Post by adamogardner on 2008-10-30
> **Grant A. said:**
> My cheat sheet is quite obvious.

[IMG]http://tbn0.google.com/images?q=tbn:kqzWGRrrXqwB8M:http://www.ipmc.cnrs.fr/~duprat/neurophysiology/images/brain2.jpg[/IMG]

how do you hook it up?

---

