---
title: "What is terminal good for?"
date: 2008-10-22
forum: The Cafe
---

### Post by jhulf on 2008-10-22
Hi there,
until now, i was just copying and pasting some 'sudo apt-get' stuff to the terminal. Recently i discovered some applications like 'mutt' or 'mpd' running from inside the terminal, and i was wondering what else can be done with the terminal.
So i am asking you to post your favorite terminal applications, like doing torrents, managing files, configure your servers, backups and what not.
Also i am interrested in tutorials on handling the terminal.

Thanks.
jhulf

---

### Post by lisati on 2008-10-22
This produces some interesting information about a system:
```
sudo dmidecode
```

---

### Post by MaxIBoy on 2008-10-22
Remember that the terminal was originally the *only* way people had of using their computers, no graphics, no click-n'-drag. It was designed originally for everyday use. For a basic rundown of how to use the terminal for simple stuff, bring up a terminal and type this:
```
info coreutils
```


I didn't know what made the terminal a more-powerful interface until I discovered [grep](http://www.gnu.org/software/grep/). Until then, the terminal was mainly useful as a way to recover a system when xorg broke. Grep taught me different.

For instance, suppose I want to run a search for all jpeg files with the letter b in the name:
```
maxtothemax@maxtothemax-laptop:~/Pictures$ ls | grep .*b.*jpg
90086-Nebula Ubuntu.jpg
kabloey.jpg
WordToolbars.jpg
maxtothemax@maxtothemax-laptop:~/Pictures$
```
In this example, "ls" and "grep" are both programs I've run.

"ls" prints out every file in the current directory:
```
maxtothemax@maxtothemax-laptop:~/Pictures$ ls
62001-into_the_fire.JPG
72456-water-flame-fantasy01.jpg
72463-dogfox-wf.jpg
84662-813-1680.jpg
88960-19305-python.jpg
90086-Nebula Ubuntu.jpg
Aaaouugh.png
aareview
aascreen_resized.jpg
Abuse_Coverart.png
add_rem.png
audacious_shot.png
Blacksquirrel0.jpg
Blacksquirrel1.jpg
blankwhite.gif
Bliss2.jpg
Bliss.jpg
boot_background.png
buttonsmockup.png
cake.png
docx_support.png
efficiency_forthewin.png
eye.jpg
eyeScaled.jpg
fail1.png
fear.png
feuertanz_1_1600x1200.jpg
feuertanz_2_1600x1200.jpg
fire1600.jpg
fire2.jpg
fire3.jpg
firefoxes.png
fire.jpg
firestyles.png
fist
Flames-Usplash-ss.jpg
fractall\.png
frames2.png
frames.png
funny-pictures-tiger-fetches-a-large-trunk.jpg
glassesFUP.png
glitchdemo
goldfish.jpg
greenlightningscreen_0.1.png
green-lightning-screen-desktop.jpg
greytheme
gscrot.png
helmet
huh1.png
IMG_0747.jpg
inferno\.jpg
In_flames.jpg
irishvirus.jpg
kabloey.jpg
klingonSupport.png
lighting_theme_buttons.above.png
lighting_theme_buttons.below.png
lighting_theme_buttons.close.png
lighting_theme_buttons.max.png
lighting_theme_buttons.menu.png
lighting_theme_buttons.min.png
lighting_theme_buttons.restore.png
lightning1.jpg
lightning1_tweaked.jpg
lightning2.jpg
lightning2_tweaked.jpg
lightning3.jpg
lightning4.jpg
lightning4_tweaked.jpg
lightning_theme_bottom_left.png
lightning_theme_bottom.png
lightning_theme_bottom_right.png
lightning_theme_button_blank.png
lightning_theme_left.png
lightning_theme_right.png
lightning_theme_top_left.png
lightning_theme_top_right.png
links0.png
links1.png
links2.png
Mercury_3.jpg
metaupdate.png
mockup1
not_aero.png
not_aero_small.png
not_aero.xcf
ohCrap__Errors.png
oil1.tga
ominous.png
pond_scum.jpg
pond_scum_tweaked.jpg
pool.jpg
pool.xcf
printing.jpg
project.jpg
Screenshot-DOSBox 0.72, Cpu Cycles:      max, Frameskip  0, Program:  DCNTSHR.png
Screenshot-QEMU_UNIX7.png
Screenshot-Windows shares on mshome - File Browser.png
screwedup_panel
spiral-tunnel.zip
splash1.xcf
splash.jpg
SporkIcon.ico
SporkIcon.png
SporkIcon.xcf
terriblereception.png
textures
theme2.png
theme.png
thesaurusFail.png
thunarman
titlebargone.png
torch0.jpg
torch1.xcf
towelrackclean.JPG
towelrack.JPG
tricorn.jpg
ubuntu-babe.png
UbuntuLogo.png
UbuntuLogoTh.png
unixv7.png
unless-you-can-jump.png
visualAid1.png
visualAid2.png
volcano.jpg
volcano-scaled.jpg
volcano-screen.jpg
wmii_is_small.png
WordToolbars.jpg
maxtothemax@maxtothemax-laptop:~/Pictures$ 
```

The "|" takes the output of "ls" and uses it as the input of "grep." This is called a "pipe" symbol.
After the word "grep" is a pattern, or "regular expression." I'll go over it character by character:
[list]
[*]"." can match any character
[*]"*" means that the previous character is repeated zero or more times (without the "*" the "." would represent exactly one character.)
[*]"b" literally looks for a letter "b."
[*]".*" is repeated again.
[*]Since there's nothing after "jpg," it must be at the end of the filename.
[/list]
In other words, any file with a name ending in "jpg," which must have the lowercase letter "b" in it, and the letter "b" can optionally have some other characters before and after it (but not after "jpg.") That kind of search would be incredibly annoying in a graphical interface. Note that in most Linux file browsers, you can use regular expressions, but the field where you type in the pattern is really just a specialized terminal.

---

### Post by cariboo on 2008-10-22
Every program in /bin are command line programs. Check it out. Another great thing about the terminal is man pages for example:

```
man grep
```

will tell you everything you want to know about grep.

Jim

---

### Post by sertse on 2008-10-22
I suggest you try INX. Link - [http://inx.maincontent.net/](http://inx.maincontent.net/)

It is a terminal only distro, remastered from Ubuntu. It has several hand on tutorials for you to be familiar to basic linux commands, and showcases various apps that can be run from the terminal to do your usual computer things. Examples include net browsing, media playing...

---

### Post by MaxIBoy on 2008-10-22
+1

Get yourself a copy of QEMU and a bootable disk image of INX, and play around a little. You don't even have to install it or burn a CD.

---

### Post by chris4585 on 2008-10-22
> **sertse said:**
> I suggest you try INX. Link - [http://inx.maincontent.net/](http://inx.maincontent.net/)

It is a terminal only distro, remastered from Ubuntu. It has several hand on tutorials for you to be familiar to basic linux commands, and showcases various apps that can be run from the terminal to do your usual computer things. Examples include net browsing, media playing...

+1 for INX, this will show you the light of the command line

---

### Post by pelle.k on 2008-10-22
> What is terminal good for?
How about scripting]?
You dont think programming is done in a gui, do you?
Basically, it's very hard to tell a computer what to do by "pointing and clicking", unless it's a very specific task such as text/video editing or whatever, but in the end, every GUI started of as code, or text if you will.
Granted, these programs may have been done in a GUI text editor of some sort, but the fact remains that a textual interface is superior to a GUI for instructing a computer of what to do, unless it's a very specific task, as i ponted out earlier.
I'm not one of those guys who hate GUI apps, quite the opposite - but the fact remains, some things just cant be done with a GUI.

---

### Post by billgoldberg on 2008-10-22
> **jhulf said:**
> Hi there,
until now, i was just copying and pasting some 'sudo apt-get' stuff to the terminal. Recently i discovered some applications like 'mutt' or 'mpd' running from inside the terminal, and i was wondering what else can be done with the terminal.
So i am asking you to post your favorite terminal applications, like doing torrents, managing files, configure your servers, backups and what not.
Also i am interrested in tutorials on handling the terminal.

Thanks.
jhulf

I mostly use the terminal for administrative work.

Installing, removing applications.

Opening system files.

Getting system info.

Identify errors and fixing them (if possible),...

Connecting to other pc's (ssh).

...

---

### Post by scragar on 2008-10-22
The terminal is faster, it#s easier to do things more precisely(with find I can find files edit in the past 2 minutes, or 7 hours, or 3 days, maybe just files starting with 'bob', what about combining the lot, files accessed in the past 3 days starting with bob?```
sudo find / -atime 3 -name "bob*"
```), faster(compair searching in synaptic for "abiword" with apt-cache```
apt-cache search abiword
```), I can use information without needing to see it(thanks to piping and such), I can recive feedback from malfunctioning applications(or ones that arn't running because for some reason they arn't installed).

All in all the terminal is great for a number of things, the most important for these forums, is the ability to share infromation, which is easier "paste back the output of **sudo apt-get update**" or "can you tell me what it says when you got to system>preferences>synaptic and choose to reload?" -- I can tell you which people give you the most accurate information from.

---

### Post by Sealbhach on 2008-10-22
I find 

```
locate *name of file*
```

very useful.

Also, searching for installed pacakges:

```
sudo dpkg -l | grep *packagename*
```

Also:

```
ps aux
```

and to kill runaway apps:

```
kill -9 *name of pr*ocess
```

or 

```
killall *name of process*
```

.

---

### Post by chucky chuckaluck on 2008-10-22
i've used **mpd+ncmpc** in the past, but i find **cplay** simpler and quicker. **htop** is great for monitoring resources (though, i use it mostly for decoration). i just quit using thunar in favor of **mc**. and, i do almost all my editing using **nano**.

the nice thing about terminal apps is that they will fit into any environment, including the console. i find them less fussy than gui apps and faster as a result. also, when using a transparent terminal, i can choose 'the look' of my work environment, which is important to me.

**screen** and **dvtm** are useful in stretching your terminals usefulness.

---

### Post by Greyed on 2008-10-22
Jack is a good console app, too..

```

Package: jack                       
Description: Rip and encode CDs with one command
 Jack has been developed with one main goal: making OGGs (or MP3s)
 without having to worry. There is nearly no way that an incomplete rip
 goes unnoticed, e.g. jack compares WAV and OGG file sizes when
 continuing from a previous run. Jack also checks your HD space before
 doing anything (even keeps some MB free).
 .
 Jack is different from other such tools in a number of ways:
  - it supports different rippers and encoders
  - it is very configurable
  - it doesn't need X
  - it can "rip" virtual CD images like the ones created by cdrdao
  - when using cdparanoia, cdparanoia's status information is displayed
    and archived for all tracks, so you can see if something went wrong
  - it uses sophisticated disk space management, i.e. it schedules its
    ripping/encoding processes depending on available space.
  - freedb query, file renaming and id3/ogg-tagging
  - it can resume work after it has been interrupted. If all tracks have
    been ripped, it doesn't even need the CD anymore, even if you want
    to do a freedb query.
  - it can do a freedb query based on OGGs alone, like if you don't
    remember from which CD those OGGs came from.
  - freedb submissions

```The other cool part not mentioned here.  Single-rip, multi-encode.  I use jack to RIP my CDs and encode to MP3 (for the iPod because Apple's dumb), Ogg (for local or network playback) and FLAC (for archival lossless backups).  It does all that in a single pass where most other tools would require you to rip the CD three times.

Actually, let me answer the question another way.  If my GUI went away right now what applications would I be unable to live without?

mutt - Email.
vim - text editor for everything
slrn - usenet news if I still read it (which, with no GUI, I would start doing again)
mbsync - IMAP sync client that plays well with mutt.
links - text-only browser.
ssmtp - simple smtp; send all your mail to a mail host.  Plugs that nasty design hole in mutt.
ssh - Give me access to other machines.
screen - the X of TTYs,  Seriously.  ;)
finch - I've not given this a try but without Pidgin I'd give its console cousin a look for my IM needs.
bitchx - The only IRC client I could deal with (is it still around, even)
mc - File manager with 'tude though these days I mostly work with just zsh.
zsh - the shell that weened me from mc.

Do I use all of these now?  Some almost daily.  Others off-and-on.  Still others no longer but I would pick them up again if so inclined.  With the exception of Firefox -> Links my productivity would probably not decline all that much if at all.

---

### Post by jhulf on 2008-10-22
Wow,thank you guys for all the replies. I will definately try this all out. Just downloading 'inx' , this seems to be a fun way to start terminaling.

thanks
jhulf

---

### Post by Northsider on 2008-10-22
> What is terminal good for?
Finding, downloading, and installing programs so I don't have to use the terminal.  :-p

---

### Post by cookieofdoom on 2008-10-22
I find it's great for fixing broken xorg.conf files.:)

---

### Post by Steveway on 2008-10-22
How about:
> sudo apt-get install bb
> bb
?

---

### Post by mentallaxative on 2008-10-22
I find the terminal useful when I just want to look through my folders. If I want to do some serious shuffling around, I open Pcmanfm.

I use the Lua and the Python interpreter in the terminal when I need to test something out. You wouldn't be able to learn those languages as quickly as you could without a terminal to load the intepreter in. I find as time goes by and I get more experience with Linux, I am spending more time in the terminal and less with GUI.

I have not used Ubuntu in a while now, but I believe you can install software just as easily in the terminal with apt-get/aptitude as opening Synaptic.

---

### Post by LaRoza on 2008-10-22
What is terminal good for? Everything.

You can watch movies, listen to music, edit, email, chat, im, browse internet, manage system, etc all in the terminal.

---

### Post by jhulf on 2008-10-22
> **Steveway said:**
> How about:
sudo apt-get install bb 
?

Hehe. Nice.

---

### Post by oldos2er on 2008-10-22
Favorite CLI apps: slrn, nn, mc, and of course aptitude.

---

### Post by userundefine on 2008-10-22
> **LaRoza said:**
> What is terminal good for? Everything.

You can watch movies, listen to music, edit, email, chat, im, browse internet, manage system, etc all in the terminal.
Exactly.

If I want to watch a video file, it's laborious to click click click click deep into a folder structure (I like hierarchy and classification).  Plus, I use a laptop exclusively, and while I've set the trackpad to very high sensitivity, it's still a laborious task to do all that moving and clicking.  Why, with a terminal ALWAYS available (like tilda, for example, a drop-down terminal), I hit a keyboard combination, the terminal appears, I type a few letters of each directory to get to the file and then press TAB.

For example, the file I want is located in ~/video/action/80s/.  So I bring down the terminal, type v, and press tab.  Tab completion completes the word I wanted to use because it scans the directory for files/dirs beginning with v.  So now I have video/.  Then I type a.  Tab complete finds action, and now I have /video/action.  You get the picture.  This is extremely fast, and works for whatever you want.  Media files, program names (like 'mplayer' -- type mp and press tab).  Why do I want to drag my cursor to the top of the screen, click Applications, and then go find it among the menus while trying to keep the cursor in the right area so I don't go in the wrong menu?  Laborious!  I'm lazy.  I want to type fast and be done.

And, if you think commands are obscure, well, just rewrite it to whatever you like!  In a file called .bashrc located in your home directory, you can customize commands to suit you better.  So, instead of typing "sudo apt-get install *program*" whenever I want to install something, I've set a custom command called "install" that includes all that.  So now I type "install mplayer" and it works.  If I want to search, why remember "apt-cache search"?  Just set a custom command to "search" or whatever you like.  (Disclaimer: when you're just starting the command line, though, it's probably a good idea to use the traditional names until you know them well enough that you don't need to type them every time.  IMO anyway.)

So, part of my .bashrc file looks like this:

```
## apt
alias install='sudo apt-get install'
alias remove='sudo apt-get remove'
alias upgrade='sudo apt-get upgrade'
alias update='sudo apt-get update'
alias search='apt-cache search'
alias changelog='aptitude changelog'
alias clean='sudo apt-get autoclean && sudo apt-get autoremove'
```

---

### Post by jimi_hendrix on 2008-10-22
terminal is much quicker for me to do somethings in and its how i compile my code

---

### Post by richg on 2008-10-22
It is good for techies.

Rich

---

### Post by Grant A. on 2008-10-22
> **userundefine said:**
> Exactly.

If I want to watch a video file, it's laborious to click click click click deep into a folder structure (I like hierarchy and classification).  Plus, I use a laptop exclusively, and while I've set the trackpad to very high sensitivity, it's still a laborious task to do all that moving and clicking.  Why, with a terminal ALWAYS available (like tilda, for example, a drop-down terminal), I hit a keyboard combination, the terminal appears, I type a few letters of each directory to get to the file and then press TAB.

For example, the file I want is located in ~/video/action/80s/.  So I bring down the terminal, type v, and press tab.  Tab completion completes the word I wanted to use because it scans the directory for files/dirs beginning with v.  So now I have video/.  Then I type a.  Tab complete finds action, and now I have /video/action.  You get the picture.  This is extremely fast, and works for whatever you want.  Media files, program names (like 'mplayer' -- type mp and press tab).  Why do I want to drag my cursor to the top of the screen, click Applications, and then go find it among the menus while trying to keep the cursor in the right area so I don't go in the wrong menu?  Laborious!  I'm lazy.  I want to type fast and be done.

And, if you think commands are obscure, well, just rewrite it to whatever you like!  In a file called .bashrc located in your home directory, you can customize commands to suit you better.  So, instead of typing "sudo apt-get install *program*" whenever I want to install something, I've set a custom command called "install" that includes all that.  So now I type "install mplayer" and it works.  If I want to search, why remember "apt-cache search"?  Just set a custom command to "search" or whatever you like.  (Disclaimer: when you're just starting the command line, though, it's probably a good idea to use the traditional names until you know them well enough that you don't need to type them every time.  IMO anyway.)

So, part of my .bashrc file looks like this:

```
## apt
alias install='sudo apt-get install'
alias remove='sudo apt-get remove'
alias upgrade='sudo apt-get upgrade'
alias update='sudo apt-get update'
alias search='apt-cache search'
alias changelog='aptitude changelog'
alias clean='sudo apt-get autoclean && sudo apt-get autoremove'
```

Are those variables? That is a very good idea! I need to try that sometime.

---

### Post by cardinals_fan on 2008-10-22
[http://linux.die.net/Linux-CLI/](http://linux.die.net/Linux-CLI/)

---

### Post by crimesaucer on 2008-10-22
I use the Terminal to build apps from source, edit a file with nano or vim, resize bulk images, convert bulk .svg images to bulk .png images..... update packages, and also search for packages and info (pacman).


Those are a few of my everyday usages for my Terminal..... I also move a file, or copy a directory every now and then.

---

### Post by MaxIBoy on 2008-10-22
> How about:

sudo apt-get install bb
bb

?


WOW! I want to do something like that now.

---

### Post by LaRoza on 2008-10-22
> **Grant A. said:**
> Are those variables? That is a very good idea! I need to try that sometime.

No, they are aliases, which I guess is sort of like a variable, but shell variables are different.

```

~$cat .bashrc | grep "alias"
alias code='cd /media/STORAGE/code/'
alias ccode='cd /media/STORAGE/cCode/'
alias py='cd /media/STORAGE/code/pythonCode/'
alias off='/home/laroza/off'
alias search='apt-cache search'
alias install='sudo aptitude install'
alias clean='sudo apt-get clean && sudo apt-get autoremove'
alias upgrade='sudo apt-get update && sudo apt-get upgrade && sudo apt-get autoclean && sudo apt-get clean'
alias pingg='ping -c 1 www.google.com'
alias targz="tar -xvvzf"
alias headset='asoundconf set-default-card headset'
alias intel='asoundconf set-default-card intel'
alias tarup='tar -cvvf'

```

---

### Post by lotus49 on 2008-10-23
Now perhaps it's just because I am a bit of an old codger, but I learnt Unix when there was only the command line so it has always been very familiar to me.

My single favourite command line program is vi.  When I first started learning it I thought it was some kind of sick joke but it is super powerful and now I know it well, it is far and away my favourite text editor.

---

### Post by chucky chuckaluck on 2008-10-23
> **lotus49 said:**
> My single favourite command line program is vi.  When I first started learning it I thought it was some kind of sick joke...

i think i'm still stuck in the 'sick joke' phase.

---

### Post by DoktorSeven on 2008-10-23
The stages of learning vi:
1) "Why doesn't it work?  I'm typing stuff and all it does is beep!"
2) "What?  This is some sort of sick joke."
3) "Eh, ok, I see how this works, but why the heck would you want to go through all that just to edit a file?"
4) "Ok, I can see how that can be useful, I'd still rather stick to nano."
5) "vi is the best text editor on the planet."

Give it time, you'll all be at stage 5 soon enough.

:)

---

### Post by scragar on 2008-10-23
> **DoktorSeven said:**
> The stages of learning vi:
1) "Why doesn't it work?  I'm typing stuff and all it does is beep!"
2) "What?  This is some sort of sick joke."
3) "Eh, ok, I see how this works, but why the heck would you want to go through all that just to edit a file?"
4) "Ok, I can see how that can be useful, I'd still rather stick to nano."
5) "vi is the best text editor on the planet."

Give it time, you'll all be at stage 5 soon enough.

:)

6) ?
7) profit

Couldn't resist :p

---

### Post by MaxIBoy on 2008-10-23
"Cat" plus "echo" plus redirection is all anyone ought to need.

---

### Post by urukrama on 2008-10-25
> **chucky chuckaluck said:**
> i think i'm still stuck in the 'sick joke' phase.

Have you tried **vimtutor**? It comes with vim and is really helpful in learning vim in an easy and straightforward way. The tutorial is easy and requires you to perform certain operations. It lasts about half an hour and after that you are able to use vim for basic editing, find and replace, etc.

I don't claim I've learned vim in half an hour, but I can edit text files pretty easily with it now, and that is generally all I need it for.

I often still prefer nano, though, especially since it has similar keybindings as alpine, which helps in not getting confused or distracted.

---

