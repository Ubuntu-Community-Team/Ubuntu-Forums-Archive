---
title: "Things you need to know about Ubuntu...that will make your life easier!"
date: 2009-04-27
forum: The Cafe
---

### Post by lovinglinux on 2009-04-27
I have been using Ubuntu for 8 months and only last week I learned that you can hit the up/down arrows in the keyboard when you are using the terminal to display the commands history :oops:. This is awesome and save a lot of time.

So I decided to create this thread, to exchange tips and tricks that make our experience with Ubuntu a lot easier.  I'm posting some things I think is worthy, but please post your own too. This is not supposed to be a tutorial thread, so if you need to post something complex and big, please just describe it and give a link. Here it goes.

------------------------------

Things you need to know about Ubuntu...that will make your life easier!
[b]
Installation[/b]

[list][*] you don't have to install Ubuntu to try it. You can use from the Live CD without affecting your current files
[*] you can install Ubuntu from inside Windows, like a regular program, using a nice tool called [Wubi](http://www.ubuntu.com/getubuntu/downloadmirrors#wubi)
[*] [having a separate partition for your personal stuff](http://www.psychocats.net/ubuntu/separatehome) can save you a lot of trouble when upgrading or fixing serious issues[/list]

**Usability**

[list][*] on Linux, you don't have to copy and paste a text using CTRL+C and CTRL+V, just select the text and hit the middle-mouse-button where you want to paste it[/list]

**Terminal (the command stuff)**

[list][*] when you type your password in the terminal it doesn't show up, but it is there. Just hit enter to continue.
[*]you can hit the up/down arrows or the [mousewheel](http://ubuntuforums.org/showpost.php?p=7157811&postcount=5) to access recently used commands
[*]you can type the initial letters of a command and hit Tab to auto-complete it or to display a list of options
[*] this symbol **~/** before a file means that it is located on your personal directory (i.e. /home/yourself/) and you can use it instead of typing the entire path
[*] most programs have a manual that you can read by typing "*man nameoftheprogram*"[/list]

**Security**

[list][*] [there are no virus capable of infecting Linux on the wild, seriously!](http://ubuntuforums.org/showthread.php?t=765421)
[*] Firestarter is not a firewall, it is just a tool for creating firewall rules (firewall manager). 
[*]UFW is currently the recommended firewall manager. You can install the GUFW (gui) from the Add/Remove menu.
[/list]

**Backup and Upgrade**

[list][*] before re-installing Ubuntu, you can [create a list of installed software](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)  and use it to install all of them at once in the clean system. It's like magic!
[*] [/list]

**Troubleshooting**

[list][*] you can search the forums threads using Google Site Search, by adding *site:ubuntuforums.org* after the keywords you want to look for.[/list]

---

### Post by Russell Burrows on 2009-04-27
Double clicking the sound button lets you select max sound level and fixes the low sound problem.

When playing back a video you can hit pause and select snapshot to make a cool wallpaper for your desktop from a scene in any video.

If your videos are choppy boys then select turning video effects to off for playable videos.

---

### Post by kellemes on 2009-04-27
Cool post for starting users, well done.

---

### Post by lovinglinux on 2009-04-27
> **Russell Burrows said:**
> Double clicking the sound button lets you select max sound level and fixes the low sound problem.

Until version 9.04, which shows a "Volume Control" button when you click it once. You cant double click anymore.

> **kellemes said:**
> Cool post for starting users, well done.

Thank you. Please add more stuff  8)

---

### Post by Bakon Jarser on 2009-04-27
more cool terminal stuff:

history = displays a history of recently run commands

you can also scroll through terminal history with the mousewheel (just like the up and down keys)

command | more  =  displays the information one page at a time, very useful for commands with lots of output.  use space to advance a page, return to advance a line, q to quit

cd - =   goes to the previous directory you were in

ctrl + c  =   stop a running command

---

### Post by lovinglinux on 2009-04-27
Thank you. Thank you. I'm adding the stuff to the first post.

---

### Post by ninjapirate89 on 2009-04-27
> **lovinglinux said:**
> Until version 9.04, which shows a "Volume Control" button when you click it once. You cant double click anymore.


I am using Jaunty and when I double-click the volume applet it mutes. It doesn't go to full volume though.

Edit -> Also when your mouse is over the volume applet you can scroll up/down to raise/lower the volume.

---

### Post by lisati on 2009-04-27
Here's my $0.02:

[LIST]
[*]Making backups of important data is ALWAYS a good idea, especially when trying a new operating system.
[*]Read what's on the screen carefully BEFORE you click on "Next" or "Forward"
[/LIST]

---

### Post by theozzlives on 2009-04-27
I've been using Ubuntu longer than you and didn't know about the installed programs list. I always just made a handwritten checklist and installed the programs one at a time. huh, I guess you learn something new every day.

---

### Post by Bakon Jarser on 2009-04-27
After finding that history command I started looking around and found out how to search through your command history.

[http://www.talug.org/events/20030709/cmdline_history.html](http://www.talug.org/events/20030709/cmdline_history.html)
> vague memory

    * If you really are uncertain of the history or if you know you could be searching back through many similar commands for one of particular interest, then you can use this more brute-force method.

    * Type the following command to get a list of all related commands with their history numbers:

            history | grep -i "<search string>"

    * Once you've found the command you want, you can execute it specifically by its number using the following built-in history expansion command:

            !<history number>

I finally gotta sit down and learn the terminal.  There's so much cool stuff you can do.

---

### Post by capnthommo on 2009-04-27
I am afraid i am a complete divot so i haven't got any to add.  but i just want to say this is a brilliant thread, and kudos for putting it in the ABT section.  until recently i wouldn't have found it if it had been pretty much anywhere else.
and +1 for the backup of your installed apps.  i usually rely on memory so it generally takes me a week to get things back to normal.  the good thing though, is that i tend to forget the things i have installed and really dont end up using so it kind of operates a form of natural selection.
but again, brilliant thread - perhaps a link to it with a suitable title in the stickies?  cos it's going to slip back as newer posts come in, isn't it, then it's less likely to be stumbled across.  that's unless people keep posting/bumping.
cheers
nigel

p.s.  sorry if i my post sounds more like a community cafe type comment.

---

### Post by humble3d on 2009-04-27
**Many Thanks for all your help...** :)

---

### Post by t0p on 2009-04-27
I like the **apropos** command.

Let's say you want to do something to do with passwords, but you don't know what command/program you need.  Open terminal, and type in:

```
apropos password
```

and ubuntu gives you a list:

```
chage (1)            - change user password expiry information
chgpasswd (8)        - update group passwords in batch mode
chpasswd (8)         - update passwords in batch mode
cpgr (8)             - copy with locking the given file to the password or gr...
cppw (8)             - copy with locking the given file to the password or gr...
des_read_2passwords (3ssl) - Compatibility user interface functions
des_read_password (3ssl) - Compatibility user interface functions
EVP_BytesToKey (3ssl) - password based encryption routine
expiry (1)           - check and enforce password expiration policy
getPasswordFormat (1) - SMBIOS management/utility program
gnome-keyring-daemon (1) - keep password and other secrets for users
gnome-pilot-make-password (1) - GNOME applet to manipulate a Palm PDA
Gnome2::PasswordDialog (3pm) - (unknown subject)
grpconv (8)          - convert to and from shadow passwords and groups
grpunconv (8)        - convert to and from shadow passwords and groups
grub-md5-crypt (8)   - Encrypt a password in MD5 format
login.defs (5)       - shadow password suite configuration
lppasswd (1)         - add, change, or delete digest passwords.
pam_cracklib (8)     - PAM module to check the password against dictionary words
pam_unix (8)         - Module for traditional password authentication
passwd (1)           - change user password
passwd (1ssl)        - compute password hashes
passwd (5)           - the password file
pwck (8)             - verify integrity of password files
pwconv (8)           - convert to and from shadow passwords and groups
pwunconv (8)         - convert to and from shadow passwords and groups
shadow (5)           - encrypted password file
shadowconfig (8)     - toggle shadow passwords on and off
smbpasswd (5)        - The Samba encrypted password file
smbpasswd (8)        - change a user's SMB password
su-to-root (1)       - A simple script to give an `interactive' front-end to ...
unix_chkpwd (8)      - Helper binary that verifies the password of the curren...
unix_update (8)      - Helper binary that updates the password of a given user
verifySmiPassword (1) - SMBIOS management/utility program
vigr (8)             - edit the password, group, shadow-password or shadow-gr...
vipw (8)             - edit the password, group, shadow-password or shadow-gr...

```

That's a long list, I know.  But at least you got somewhere to start now.

---

### Post by Arndt on 2009-04-27
> **lovinglinux said:**
> 

So I decided to create this thread, to exchange tips and tricks that make our experience with Ubuntu a lot easier.  I'm posting some things I think is worthy, but please post your own too.


Very nice, I already learned something new.

> 

[list]
[*]*ctrl + x* stop a running command [*](http://ubuntuforums.org/showpost.php?p=7157811&postcount=5)[/list] 


It's probably Ctrl-C you mean, not Ctrl-X.

Ctrl-Z also stops a program, but suspends it, so it can be continued by entering the command "fg". And Ctrl-\ stops it and also creates a core dump (subject to core dump settings in the shell). You can inspect and change those things with the 'stty' command.

---

### Post by me.translucent on 2009-04-27
to clear the history one can use history -c .

---

### Post by jmszr on 2009-04-27
lovinglinux,

      Good idea! Here are a couple of usability tips:
      
      ctrl + scroll in firefox will increase/decrease the size of the page

      Scrollbar in gnome: right clicking on the up/down arrows will scroll you all the way up/down.

---

### Post by wolfen69 on 2009-04-27
if playback in VLC is glitchy, open it and go to tools>preferences>video, and set output to X11. then save. restart VLC. this has worked for me.

---

### Post by meeples on 2009-04-27
Super [windows button] + scroll  - zooms in on everything, which is handy if you have eyesight problems :)

---

### Post by kirsis on 2009-04-27
**Terminal:**

*pushd* pushes the current directory to a stack and switches to another directory.

*popd* takes a directory off the stack and switches to it.

Example:

```

**pushd /tmp** # Like *cd /tmp*, only remember where we are
cd .. # Now move around
cd /etc
cd scim/
cd /var
**popd** # Return to the directory on the stack

```

The **`** character is useful, it allows to use the output of one command as part of another command.

Example:

```

gedit `locate fb.h | grep /usr/include`

```

In the example, I've opened a file for viewing, whose exact location I didn't know. I know it's called fb.h and it's somewhere in /usr/include, so I assemble a pipe to locate it and then pass the output directly to gedit.

**Misc** 

Highlighting something puts the text in a clipboard that's seperate from tyhe Ctrl+C/Ctrl+V clipboard. Middle clicking in a text input field pastes the text that's last highlighted.

This last one I read somewhere on these forums :) Passing it on, because the original post is probably buried somewhere by now.

---

### Post by Namtabmai on 2009-04-27
> **Bakon Jarser said:**
> After finding that history command I started looking around and found out how to search through your command history.

Ctrl-R and start typing, keep hitting Ctrl-R to cycle back through matching commands.

---

### Post by feelshift on 2009-04-27
> **jmszr said:**
> ctrl + scroll in firefox will increase/decrease the size of the page

Ctrl + 0 brings it back to normal.
> **meeples said:**
> Super [windows button] + scroll  - zooms in on everything, which is handy if you have eyesight problems :)
Only if you have desktop effects enabled (Zoom Desktop).

---

### Post by Arndt on 2009-04-27
> **kirsis said:**
> 
Highlighting something puts the text in a clipboard that's seperate from tyhe Ctrl+C/Ctrl+V clipboard. Middle clicking in a text input field pastes the text that's last highlighted.

This last one I read somewhere on these forums :) Passing it on, because the original post is probably buried somewhere by now.

The program xcutsel with suitable arguments can transfer between those different copy buffers. It doesn't display anything - maybe there are other programs which do that.

---

### Post by Bakon Jarser on 2009-04-27
> **Arndt said:**
> 
It's probably Ctrl-C you mean, not Ctrl-X.



Yeah, typo.  Nice catch


> [quote]
Originally Posted by jmszr View Post
ctrl + scroll in firefox will increase/decrease the size of the page
Ctrl + 0 brings it back to normal.[/quote]

I never have my keyboard close by.  I use [fire gestures]("https://addons.mozilla.org/en-US/firefox/addon/6366") and am lost whenever I use a computer without it.

I didn't know you could generate a list of programs you had installed.  That will come in handy since I always do clean installs of new releases.  But once you have your system set up the way you want you should use [remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html") to make a backup.  That way you can get your system back to the way it is now really easily.

---

### Post by Russell Burrows on 2009-04-28
You can have close to invisible top and bottom panels by selecting solid color and selecting total transparency for a clean look.

---

### Post by Johnsie on 2009-04-28
If you put your mouse arrow over the volume control icon and use the scroll wheel the volume will go up or down without you having to click anyhing.

---

### Post by cmay on 2009-04-28
great tread. thanks .
i have just one simple little trick  i like to share. not that its the greatest invention of all times  and i am not sure if it is already posted but i will post it anyway. . 

even when you dont have a printer and need to get instructions for some things to read later while off line or just later you can still print to pdf. 

i take tons of notes this way and so i have it all on a backup usb key if i need to  find a complex set of instructions again i just find the correct littel tutorial or page i have on pdf. 
those notes are pages like these ones as example. 

it is far more cheap than buying books also:).

---

### Post by billgoldberg on 2009-04-28
ctrl + alt + backspace to reset X server *(In Ubuntu 9.04, you'll have to hack that back into xorg)*.

Holding down Alt + SysRq (print screen) and slowly typing REISUB whilst doing so will bring down any frozen system in a safe way.

---

### Post by benj1 on 2009-04-28
for funky terminal commands look at [commandlinefu]("http://www.commandlinefu.com/commands/browse")

also 
```
apropos *term*
```
search for installed apps with 'term' in their man page description usful if you cant remember the name of something

---

### Post by lovinglinux on 2009-04-28
Thanks everyone for replying so positively about the thread and sharing so  nice tricks. I think this thread will soon become huge and get a life of it's own. It will be hard to keep up updating the first post and there won't be enough space for all the suggestions. So I guess it's better to just leave the discussion flowing.

Please keep posting.

---

### Post by Ptero-4 on 2009-05-09
You can drag any file to a terminal window to "paste" it's path into the terminal window.
You can "clone" an entire system (from a liveCD) by typing:
```
mksquashfs *"your system's mount point"* *"alternate partition or pendrive"* -nolzma
```
to clone the root partition itself, and:
```
dd if=*/dev/rootdevice* of=~/bootsect.dsk bs=512 count=1
```
to clone the boot sector.
Then you can use cp -a to restore the OS off the squashfs image (after mounting it) back to the formatted partition. And ```
dd if=*/path/to/bootsect.dsk* of=*/dev/rootdevice* bs=512 count=1
``` to restore the boot sector.

---

### Post by Bodyman on 2009-07-16
I'm very new to Ubuntu, I know almost nothing here. How ever you guys have some GREAT info here! It sure makes learning easier.

So, thank you all!!! Y'all are awesome.

---

### Post by ubudog on 2009-07-16
Use gedit /etc/motd to edit the message when you login via ssh.

---

### Post by papangul on 2009-07-17
WICD is a great alternative if you have issues with the default network manager.

If you need to telnet your router through crontab then using expect scripts make life easier than using bash scripts.

Evince supports djvu documents, it is a great format for storing scanned documents- [http://en.wikipedia.org/wiki/Djvu](http://en.wikipedia.org/wiki/Djvu)

---

### Post by Viva on 2009-07-17
Did anybody mention that you can preview music files in nautilus by hovering over them?

---

### Post by RiceMonster on 2009-07-17
> **Bakon Jarser said:**
> 
command | more  =  displays the information one page at a time, very useful for commands with lots of output.  use space to advance a page, return to advance a line, q to quit

I would reccomend using less rather than more (command | less). With more, you can only scroll downwards. With less you can scroll both ways, search for strings, etc.

---

### Post by l-x-l on 2009-07-17
Great thread.

---

### Post by Ashrael on 2009-07-17
Partitioning your harddisk the right way keeps you from losing your personal data!

I always upgrade from cd to stop breaking my upgrades, and divide my hd in three partitions: 

1) about 20 Gb for / 
2) double my ramsize for SWAP
3) the rest for /home

When my system breaks (not if, because I tinker a lot ;) ) I just put in the cd and laugh really hard for about 15 minutes and my system is back to pristine condition AND my /home is still there.

Very important for me....

HTH!

---

### Post by caalamus on 2009-07-17
I've got an odd one. More of an anomaly than an intended feature. If you install Ubuntu on an old iBook  & you can't right click... try hitting the eject button :] 

That serves as right click on my 500Mhz G3

Any beginner tips about display tweaks? Mine is three quarters the size of the screen.

---

### Post by Ashrael on 2009-07-23
What I forgot to say in post #37:

After I have laughed for about 15 minutes, my system is in pristine condition, but, without all packages I have installed after the installation of ubuntu. I want them all back! So **before** I start the clean install I do:

Read:

[http://www.hanckmann.net/?q=node/27](http://www.hanckmann.net/?q=node/27)

MOST EXCELENT!

---

### Post by lovinglinux on 2009-07-23
> **Ashrael said:**
> What I forgot to say in post #37:

After I have laughed for about 15 minutes, my system is in pristine condition, but, without all packages I have installed after the installation of ubuntu. I want them all back! So **before** I start the clean install I do:

Read:

[http://www.hanckmann.net/?q=node/27](http://www.hanckmann.net/?q=node/27)

MOST EXCELENT!

I have created a Firefox extension that do that and other things. Check the UMarks link in my signature.

---

### Post by dicairo on 2009-07-23
Nice thread , i want to add this one : if u want to see a window covered by another go the tittle bar and scroll up with the mouse and it fold to let u see the another window
(sorry about my english).

---

### Post by L815 on 2009-07-23
ctrl+r is a recursive history, meaning you can type part of the command and it will auto-fill previous commands with the same syntax.

---

### Post by baneb_djedet on 2009-07-23
**. Add NTFS Read/Write support**

 [SIZE=2]:popcorn:  
[/SIZE]
[SIZE=2]  ... If you're at the very beginning stages of switching from Windows, chances are you've got lots of data [/SIZE][SIZE=2]stored on an NTFS (New Technology File System) partition [/SIZE][SIZE=2]of your formatted drive  Luckily the Linux-NTFS project has built a driver(s) to keep some of the data that might be on your HDD that you might want to save.[/SIZE]
[SIZE=2]:
:
[/SIZE]
[SIZE=2]PS --Should have re-titled this thread with the words *keyboard* and *shortcuts* that make your life easiler :~ [/SIZE]

---

### Post by SpencerHolst on 2010-11-06
Graet thread for a newbie like myself. Just wanted to thank&bump.

---

### Post by SpencerHolst on 2010-11-06
and what is wrong with the server time? :/

---

### Post by Oxwivi on 2010-11-06
> **lovinglinux said:**
> **Backup and Upgrade**

[list][*] before re-installing Ubuntu, you can [create a list of installed software](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)  and use it to install all of them at once in the clean system. It's like magic!
[*] [/list]
Any similar way to *remove* software?

---

### Post by lovinglinux on 2010-11-06
> **Oxwivi said:**
> Any similar way to *remove* software?

It removes too.

---

### Post by Oxwivi on 2010-11-06
THANK YOU! TT_TT

My eternal gratitude!

---

### Post by matthew.ball on 2010-11-06
> **Bakon Jarser said:**
> more cool terminal stuff:

ctrl + c  =   stop a running command
ctrl + z will suspend the current application (process), executing [FONT="Courier New"]fg[/FONT] (foreground) will wake up the last suspended process.
ctrl + d will exit from the current terminal.
ctrl + r will do a search through history commands.

In nautilus, ctrl + h will show hidden files (though I guess this is the same as Windows [and possibly Mac?]), and ctrl + l (that's an L) will bring up the location bar (if you would rather type the location then navigate to it), pressing escape will hide it.

Edit: I thought this was a recent thread. Apologies.

---

### Post by tahitiwibble on 2010-12-17
You may find a couple of useful things here [http://www.makeuseof.com/tag/10-useful-ubuntu-keyboard-shortcuts-that-you-might-not-know-of/](http://www.makeuseof.com/tag/10-useful-ubuntu-keyboard-shortcuts-that-you-might-not-know-of/)

---

### Post by linuxforartists on 2010-12-18
**OpenOffice Essential Tips**
[B]
Speed[/B]

Before I discovered this tip to speed up OpenOffice, I nearly abandoned it because it was so slow to load.

1. Launch OpenOffice.  Go to: Tools --> Options --> Memory 

2. Check off the box for "Enable systray Quickstarter."  Now OpenOffice should launch *much* faster.

**Compatibility with Microsoft Office**

To make your OpenOffice files save in Microsoft format as default, do this:

1. Launch OpenOffice.  Go to: Tools --> Options

2. Go to: Load/Save --> General

3.  Under "Document type," select from a dropdown list what kind of OpenOffice file you want to configure.  For example, choose "Text document" for your word files.

4.  Under "Always save as," select from the dropdown list "Microsoft Word 97/2000/XP."

You can do the same to get your spreadsheets to save as Excel files, and your presentations as PowerPoint files.  This will save you the trouble of remembering to select MS formats every time you save a new document.  

I once accidentally sent my resume to an employer in Open Document Format (ODF) and the boss couldn't open it.  I quickly re-sent my resume as a Word file and got the job.  Whew!

Good stuff to know if you're creating documents to use at school or work, where everyone else is still using Microsoft Office.

Keep the tips coming.  This is a super-useful thread!

---

### Post by Zero2Nine on 2010-12-18
The package list is a very useful tip! Thanks :D

---

### Post by Deadman390 on 2012-04-19
amazing thread for newbs seeing as i am one lol.  found alot of very useful information

---

### Post by oldos2er on 2012-04-19
Old thread is old.  ZZZZZZZZZZZZZZZzzzzzzzzzzzzzzzzzzzzzzz

---

