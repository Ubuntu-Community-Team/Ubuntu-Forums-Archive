---
title: "VIM 7 released!!!"
date: 2006-05-08
forum: The Cafe
---

### Post by benplaut on 2006-05-08
[www.vim.org](www.vim.org)

i'm compiling mine right now, if someone could make a deb that would be great!

happy :ing :p 

> Vim 7 is out!

Before announcing it everywhere I'll wait until the Subversion
repository has it.  And I need to update the website.

Since version 7.0g BETA quite a few things changed.  Too many perhaps,
but I can't postpone the release any longer.  Hopefully the last-minute
changes don't cause more trouble than they fixed.

- When the result of 'guitablabel' is empty fall back to the default
   label.
- The tar and zip plugins detect failure to get the contents of the
   archive and edit the file as-is.
- Using CTRL-N that searches a long time, pressing space to interrupt
   the searching and accept the first match, the popup menu was still
   displayed briefly.
- Insert mode completion: When finding matches use 'ignorecase', but
   when adding matches to the list don't use it, so that all words with
   different case are added, "word", "Word" and "WORD".
- Fixed a few things for Insert mode completion, especially when typing
   BS, CTRL-N or a printable character while still searching for matches.
- exists() could not be used to detect whether ":2match" is supported.
   Added a check for it specifically.
- exists() ignored characters after the recognized word, which can be
   wrong when using a name with non-keyword characters.  Specifically,
   these calls no longer allow characters after the name:
   exists('*funcname') exists('*funcname(...') exists('&option')
   exists(':cmd') exists('g:name') exists('g:name[n]') exists('g:name.n')
- GUI: when doing completion and there is one match and still searching
   for another, the cursor was displayed at the end of the line instead
   of after the match.  Now show the cursor after the match.
- Report +reltime feature in ":version" output.
- Mac: When sourcing the "macmap.vim" script and then finding a .vimrc
   file the 'cpo' option isn't set properly, because it was already set
   and restored.  Added the <special> argument to ":map", so that 'cpo'
   doesn't need to be changed to be able to use <> notation.  Also do
   this for ":menu" for consistency.
- Mac: inputdialog() didn't work when compiled with big features.
- Mac: When building with "--disable-gui" the install directory would
   still be "/Applications" and Vim.app would be installed.  Now install
   in /usr/local as usual for a console application.
- GTK2: Selecting a button in the confirm() dialog with Tab or cursor
   keys and hitting Enter didn't select that button.
- GTK1: Tab page labels didn't work.
- Interrupting ":vimgrep" while it is busy loading a file left a
   modified and hidden buffer behind.
- When one window has the cursor on the last line and another window is
   resized to make that window smaller, the cursor line could go below
   the displayed lines.  Also avoid that using "~" lines makes the window
   scroll down.
- When 'encoding' and 'printencoding' were both "utf-8" then ":hardcopy"
   didn't work.
- When making 'keymap' empty the b:keymap_name variable wasn't deleted.
- When opening a quickfix window in two tabs they used different
   buffers, causing redrawing problems later.  Now use the same buffer
   for all quickfix windows.
- Trigger the TabEnter autocommand only after entering the current
   window of the tab page, otherwise the commands are executed with an
   invalid current window.
- When evaluating 'balloonexpr' takes a long time it could be called
   recursively, which could cause a crash.
- When 'cursorline' and 'hlsearch' are set and the search pattern is
   "x\n" the rest of the line was highlighted as a match.
- Win32: When using two monitors and Vim is on the second monitor,
   changing the width of the Vim window could make it jump to the first
   monitor.
- Several obvious bug fixes.  See the end of ":help version7" for more
   info.


Happy Vimming!

---

### Post by dolson on 2006-05-08
I am compiling it too, and I was going to make a .deb using the existing one as a base, but it's messy, so I'll just wait for debian Sid to get the package, or Edgy, whichever happens first (likely Sid), and then I'll just backport it to my Dapper box.

This release looks sweet.

---

### Post by bites on 2006-05-08
It compiles fine, but I'd like to try and build a package.  Is there a way to find out about the build options on the standard ubuntu packages?

---

### Post by dolson on 2006-05-08
Since you are in Dapper, hit F1 and look at the home page of the help system.

Fourth option from the top is what you want: Ubuntu Packaging Guide.

---

### Post by bites on 2006-05-08
Thanks dolson!  Never knew this was in the help system :)

---

### Post by brahms on 2006-05-08
[QUOTE=dolson]I am compiling it too, and I was going to make a .deb.[/QUOTE]

Hello,

I am trying to compil it myself, but can't convince the configure script to build it with gnome2 or gtk2 gui support :-(

Could you please point me how to achieve that ?

TIA

---

### Post by joshuapurcell on 2006-05-08
[QUOTE=brahms]Hello,

I am trying to compil it myself, but can't convince the configure script to build it with gnome2 or gtk2 gui support :-(

Could you please point me how to achieve that ?

TIA[/QUOTE]
You probably need the development packages for gnome and gtk.

---

### Post by nousplacidus on 2006-05-08
I am having the same trouble with the gtk, and I tried downloading some of the packages but even when I use 

--enable-gui=gtk

It shows up as 

..
checking --enable-gui argument... no GUI support
..

Any ideas?

---

### Post by endersshadow on 2006-05-08
Anybody get this up and running yet?  I love my gvim, and I don't want to take out any vim packages that I need.

---

### Post by jason.b.c on 2006-05-08
> VIM 7 released!!!


[QUOTE=endersshadow]Anybody get this up and running yet?  I love my gvim, and I don't want to take out any vim packages that I need.[/QUOTE]



What the heck is it, and what in the heck does it do..????](*,) 


:-k

---

### Post by briancurtin on 2006-05-08
vim is a text editor...

you cant really call yourself a 'super user' if you dont know what vim is

---

### Post by jason.b.c on 2006-05-08
[QUOTE=briancurtin]vim is a text editor...

you cant really call yourself a 'super user' if you dont know what vim is[/QUOTE]

Yes i can.!?

How am i supposed to know about **every new freakin thing** coming out on the internet nowaday.???:-k

---

### Post by briancurtin on 2006-05-08
vi/vim is probably older than me. its not new and has nothing to do with the internet.

edit: vi is from 1976, so yes its older than me by a good deal. vim is from 91

---

### Post by jason.b.c on 2006-05-08
[QUOTE=briancurtin]vi/vim is probably older than me. its not new and has nothing to do with the internet.

edit: vi is from 1976, so yes its older than me by a good deal. vim is from 91[/QUOTE]

> VIM 7 released!!!  Sounds like you get it from the internet to me..??

**1976.?** Well then it's older than me too..;)

---

### Post by tonyr on 2006-05-08
I built **gvim**. Took a few tries to figure it out.  Here are my notes:
> 
requires:
libx11-dev libxaw7-dev

the configure command:
./configure --with-x --enable-gui=gtk2 --x-includes=/usr/include/X11 --x-libraries=/usr/lib


EDIT:  It installs in **/usr/local** using **make install**. There are no installation
conflicts with the Ubuntu v6 that I could see.  I added **/usr/local/bin**
to the front of my **path** environment variable.

---

### Post by canen on 2006-05-08
--enable-gui seems to work here for me (still compiling), it found the libraries ok though.

---

### Post by tonyr on 2006-05-09
I forgot to say that I did this in Kubuntu (KDE), that's why I chose **gtk2**.
Gnome requires a different choice.  Look in **src/auto/configure** near line
863 for all of the options.  It's either **gnome** or **gnome2**.
What's the difference?

---

### Post by endersshadow on 2006-05-09
In Gnome, you can just use:

```
./configure --enable-gui
make
sudo checkinstall -D make install
```

(I like checkinstall to install packages.)

I removed all vim related packages before I installed in Synaptic, and then after installing 7.0, I went back into Synaptic and locked the Vim version so it wouldn't update it.

Looks great!

---

### Post by tseliot on 2006-05-09
If you want the .deb package I've just built, here it is:
[vim70_20060509-1_i386.deb]("www.webalice.it/albertomilone/ubuntu/vim70_20060509-1_i386.deb")


Enjoy

---

### Post by Reshin on 2006-05-09
any reason for it being so freaking confusing? :|

---

### Post by helpme on 2006-05-09
[QUOTE=Reshin]any reason for it being so freaking confusing? :|[/QUOTE]
Any reason for you entertaining us with only negative, trollish comments?

---

### Post by Reshin on 2006-05-09
[QUOTE=helpme]Any reason for you entertaining us with only negative, trollish comments?[/QUOTE]
Wait, how is that trollish? Is IS complicated :|

---

### Post by helpme on 2006-05-09
[QUOTE=Reshin]Wait, how is that trollish? Is IS complicated :|[/QUOTE]
It isn't for those who know how to use it.

---

### Post by brahms on 2006-05-09
[QUOTE=tseliot]If you want the .deb package I've just built, here it is:
[vim70_20060509-1_i386.deb]("www.webalice.it/albertomilone/ubuntu/vim70_20060509-1_i386.deb")
Enjoy[/QUOTE]

Big thanks for that package :D 

By the way, I could not manage to build vim with gui support by myself under Dapper Drake as configure does not detect gnome or gtk libs, and I am very curious to know how you configured it.
 I did installed libgnome2-dev, but I have obviously missed something... Any clues ?

Thanks again,

Brahms

---

### Post by xerxesdaphat on 2006-05-09
Has anybody made a package without gui support? I like my editors to be editors, not pretty little windows ^_^. Plus, it ought to be significantly lighter than 5MB+... what, is this the emacs binary renamed? Lol.

As far as I'm concerned, all GNOME is good for is tiling 9 gnome-terminals across the screen...

---

### Post by kabus on 2006-05-09
[QUOTE=xerxesdaphat]
As far as I'm concerned, all GNOME is good for is tiling 9 gnome-terminals across the screen...[/QUOTE]

If that's how you use Gnome you might want to take a look at Ion or wmii-3.

---

### Post by tseliot on 2006-05-09
[QUOTE=brahms]Big thanks for that package :D 

By the way, I could not manage to build vim with gui support by myself under Dapper Drake as configure does not detect gnome or gtk libs, and I am very curious to know how you configured it.
 I did installed libgnome2-dev, but I have obviously missed something... Any clues ?

Thanks again,

Brahms[/QUOTE]
```
sudo apt-get install libx11-dev libxaw7-dev ncurses*
```

```
cd path_to_vim_sources
```

```
./configure --with-x --enable-gui=gtk2 --x-includes=/usr/include/X11 --x-libraries=/usr/lib
```

```
make
```
```
sudo checkinstall -D && sudo dpkg -i vim70*
```

---

### Post by tseliot on 2006-05-09
--

---

### Post by Ob1 on 2006-05-09
How good of a text editor is WIM?

---

### Post by kabus on 2006-05-09
[QUOTE=Ob1]How good of a text editor is WIM?[/QUOTE]

It's installed by default on Ubuntu, so you could just type 'vimtutor' in a terminal and find out for yourself. :)

---

### Post by Union Jack on 2006-05-09
type in wimtutor and find out

---

### Post by meuserj on 2006-05-09
There are deb-src packages for vim 7.0 in debian experimental.  You can build packages for Dapper quite easily:

edit /etc/apt/sources.list and add this line (replace with your favorite debian mirror if you wish):

```

deb-src http://ftp.us.debian.org/debian/ experimental main contrib non-free

```

then run each of the following commands:
```

sudo apt-get update
sudo apt-get build-dep vim
apt-get --build source vim

```
When you are done you should have several vim packages in the current directory.  Install them with:
```

sudo dpkg --force-overwrite -i *.deb

```

Of course you can pick and choose which packages you want.  The only reason I have --force-overwrite in there is that there is at least one file that has moved from vim-common to vim-runtime, so you'll get errors when installing vim-runtime without --force-overwrite.
Happy vimming!:wq

---

### Post by dolson on 2006-05-09
[QUOTE=meuserj]There are deb-src packages for vim 7.0 in debian experimental.  You can build packages for Dapper quite easily:

edit /etc/apt/sources.list and add this line (replace with your favorite debian mirror if you wish):

```

deb-src http://ftp.us.debian.org/debian/ experimental main contrib non-free

```

then run each of the following commands:
```

sudo apt-get update
sudo apt-get build-dep vim
apt-get --build source vim

```
When you are done you should have several vim packages in the current directory.  Install them with:
```

sudo dpkg --force-overwrite -i *.deb

```

Of course you can pick and choose which packages you want.  The only reason I have --force-overwrite in there is that there is at least one file that has moved from vim-common to vim-runtime, so you'll get errors when installing vim-runtime without --force-overwrite.
Happy vimming!:wq[/QUOTE]
Alternately, you can install them in a different order, one at a time. I did this this morning at work, but I didn't modify my sources.list, I just downloaded the orig.tar.gz, the diff.gz, and the .dsc and then build the binary packages out of that.

But the version that I see on the mirrors is only a beta of 7.0, and not the final version 7.0, the same as this morning, and hasn't changed in over a week. Do you see the 7.0 final up there?

[QUOTE=jason.b.c]What the heck is it, and what in the heck does it do..????](*,) 


:-k[/QUOTE]

You know that there is Google and if that is too hard, the OP put a link directly to the VIM homepage right in the original post.

---

VIM isn't hard if you put a few minutes into learning it. If you expect it to work just like any other text editor, then yes, it is hard.

Here is a good resource for you who wish to learn:
[http://www.viemu.com/a_vi_vim_graphical_cheat_sheet_tutorial.html](http://www.viemu.com/a_vi_vim_graphical_cheat_sheet_tutorial.html)

---

### Post by benplaut on 2006-05-09
couldn't figure out how to get gvim (beofre ya'll popped in with your helpful instructions :P ), but tseliot's deb is working great...

:)

---

### Post by Athropos on 2006-05-10
[QUOTE=benplaut]couldn't figure out how to get gvim (beofre ya'll popped in with your helpful instructions :P ), but tseliot's deb is working great...
[/QUOTE]

That ?

```

vim -g

```

---

### Post by mikl on 2006-05-10
[QUOTE=tseliot]If you want the .deb package I've just built, here it is:
[vim70_20060509-1_i386.deb]("www.webalice.it/albertomilone/ubuntu/vim70_20060509-1_i386.deb")


Enjoy[/QUOTE]
This is brilliant. Thanks a bunch.

---

### Post by mikl on 2006-05-10
oops, my bad

---

### Post by stoffe on 2006-05-10
Tab completion does not seem to work for me, it only outputs ^I like so: ```
:se^I
```
I had the same (om multiple computers) when I compiled the beta, does anyone else see it? And more importantly, know why? :)

---

### Post by meuserj on 2006-05-10
[QUOTE=dolson]But the version that I see on the mirrors is only a beta of 7.0, and not the final version 7.0, the same as this morning, and hasn't changed in over a week. Do you see the 7.0 final up there?
[/QUOTE]

You're right, it is 7.0g... didn't realize that.  It can keep me satisfied until 7.0 final reaches experimental though.

---

### Post by Crazy Man on 2006-05-10
For some reason, even though I've installed the package, when I type in vim, it's says 6.3.something.

How do I change this? I forget...

Also, how do I switch between tabs?

---

### Post by Moobert on 2006-05-11
[QUOTE=Crazy Man]
Also, how do I switch between tabs?[/QUOTE]

ctrl+alt+pgup or ctrl+alt+pgdown

---

### Post by BDembroski on 2006-05-11
[QUOTE=stoffe]Tab completion does not seem to work for me, it only outputs ^I like so: ```
:se^I
```
I had the same (om multiple computers) when I compiled the beta, does anyone else see it? And more importantly, know why? :)[/QUOTE]

Yup. Same problem here. Can't really help as to the why, but you are not alone.

Installed from the .deb posted here. If I get a minute or three, I'll compile from source and see what happens.

--
Ben

---

### Post by kabus on 2006-05-11
[QUOTE=stoffe]Tab completion does not seem to work for me, it only outputs ^I [/QUOTE]

The problem is most likely that you don't have a .vimrc in your home directory, which apparently means that vim will run in vi compatibility mode.
Try if 

```
touch ~/.vimrc
```

fixes it.

Entering ':set nocompatible' works too, but is only temporary.

---

### Post by BDembroski on 2006-05-11
[QUOTE=kabus]The problem is most likely that you don't have a .vimrc in your home directory, which apparently means that vim will run in vi compatibility mode.
Try if 

```
touch ~/.vimrc
```

fixes it.

Entering ':set nocompatible' works too, but is only temporary.[/QUOTE]

Did the trick.

Thanks!

---

### Post by meuserj on 2006-05-12
vim 7.0 has now hit debian experimental.  You can build it for ubuntu easily by following the directions that I posted [previously.]("http://ubuntuforums.org/showpost.php?p=998296&postcount=32") Happy vimming!:wq

---

### Post by kar-tar on 2006-05-14
in case people don't know:

vim is a very powerful text editor.  it is mainly used by people who have to write code for 8+ hours a day, and if your text-file needs aren't that severe, it might not be for you.  vim is popular because it is lightweight, installed virtually everywhere (at least some version of vi, its parent is) and very configurable.

the downside to vim is that it has a near-asymptotic learning curve.  to start you off:  there are two modes to vim: command and insert (this is a lie, there are more modes, but you don't need to know that yet)

you start in command mode, which doesn't let you type text.  type ':q!' to quit, ':wq' to save and quit, and 'i' to inter insert mode.

in insert mode, you can type text.  hit 'escape' to switch back to command mode.

there are a bunch of tutorials for learning vim on the internets.

the basic philosophy is: you spend more time reading & searching text files than you do actually typing, so having a distinct command mode allows for many more 'short' shortcuts to move around and manipulate text, since keystrokes don't have to be first interpereted as entered text.

again, if you aren't writing pages and pages of code, it probably won't appeal.

personally i love it, and think it is greatly superior to emacs.  there are folks with different opinions, howevever.

---

### Post by dolson on 2006-05-15
[IMG]http://www.viemu.com/vi-vim-cheat-sheet.gif[/IMG]

---

### Post by Freddd on 2006-05-15
Why do you prefer vim over gvim? Or is it the same?

---

### Post by endersshadow on 2006-05-15
gvim is just vim w/ a GUI.  I personally prefer gvim.

---

### Post by dolson on 2006-05-15
You can't use Gvim on a remote server.

But there is very little difference... The power of Vim is in the keyboard controls, not pointy-clicky menus anyhow.

I use Gvim on my desktops.

---

### Post by FredSambo on 2006-05-16
I've been using vi and vim now for a few years.  I like it because I prefer to admin my ubuntu servers at home via ssh (putty on my winders box).  I guess I got into the habit of using vi because it is guaranteed to be on every system, especially UNIX systems, and is completely accessable from the terminal, which makes it a handy little tool all the way around.  

when i first did vimtutor i was like, "I'm never going to get this."  But now it is second nature to me. I still can't get into the graphical version though, i'd rather just use gedit or kwrite or even kate for that.  :)

happy vimming and good luck to everyone!

---

### Post by Freddd on 2006-05-17
[QUOTE=tseliot]```
sudo apt-get install libx11-dev libxaw7-dev ncurses*
```

```
cd path_to_vim_sources
```

```
./configure --with-x --enable-gui=gtk2 --x-includes=/usr/include/X11 --x-libraries=/usr/lib
```

```
make
```
```
sudo checkinstall -D && sudo dpkg -i vim70*
```[/QUOTE]Is there an easier way for an ubuntu beginner to install vim? Do I need to uninstall the pre-installed version first? To be able to do make I guess I need gnumake?

---

### Post by kabus on 2006-05-17
[QUOTE=Freddd]Is there an easier way for an ubuntu beginner to install vim? Do I need to uninstall the pre-installed version first? To be able to do make I guess I need gnumake?[/QUOTE]

You'll need the build-essential package.
Or if you don't have a problem with using an unofficial package you can use the one that was posted a few pages back in this thread.

---

### Post by gyhelle on 2006-05-17
Heelo,

I'm trying to compile vim 7.0 on my ubuntu box (breezy). I would like to have at least a gui (gnome2) and a python support. the python support seems to be Ok but not the gui.

When I'm trying to compile : 

./configure --enable-gui # simplest case with gui
make

I obtain  :
./vim -g
E25: GUI cannot be used: Not enabled at compile time

I had a look on the configure ouput, I 've found these 4 lignes corresponding to X :

checking for X... (cached) no
checking if X11 header files can be found... yes
checking --enable-gui argument... no GUI support
checking for X11/SM/SMlib.h... (cached) no

I installed :
xlibs-dev, xlibs-static-dev, libxaw7-dev, libx11-dev, libgtk2.0-dev, libgnome2-dev and  libxaw7-dev.


tseliot's deb work well with the gui but it lack python support.

Anybody can help me ?

thanks !

---

### Post by tseliot on 2006-05-17
[QUOTE=Freddd]Is there an easier way for an ubuntu beginner to install vim? Do I need to uninstall the pre-installed version first? To be able to do make I guess I need gnumake?[/QUOTE]
1) Uninstall the preinstalled version from Synaptic or Adept (it's 3 packages unless I'm wrong).

2) Download the packages I've posted:

[http://www.webalice.it/albertomilone/ubuntu/vim70_20060509-1_i386.deb]("http://www.webalice.it/albertomilone/ubuntu/vim70_20060509-1_i386.deb")

3) Install the package by doing a:
```
sudo dpkg -i vim70_20060509-1_i386
```

---

### Post by Koobi on 2006-05-17
i loooooove vim

i tried compiling without removing vim and vim-common (i can't because ubuntu-minimal depends on it) and it didn't come up as vim7 although the compile appeared to be successful.

eventually, i decided to go for **tseliot**'s deb and that worked miracles :)
thanks tseliot, i will name my kid after you hehe



but i'm just so glad vim 7 is out. the absense of tabs was the only thing that made me use other editors but now i wont need to.

---

### Post by andrew! on 2006-05-17
After reading all the posts and trying all the suggested actions, I still cannot compile vim7 with gui. Although I can install with this deb package, I need some more functions missing in this deb package, such as cscope support. Can anyone help me?

my configure commands:

```
./configure --prefix=/usr --with-x --enable-gui=gtk2 --x-includes=/usr/include/X11 --x-libraries=/usr/lib --enable-cscope --enable-perlinterp --enable-multibyte 

```
btw, I have the same problem with most of the people here:
```
checking for X... no
checking if X11 header files can be found... yes
checking --enable-gui argument... no GUI support

```

[QUOTE=tseliot]1) Uninstall the preinstalled version from Synaptic or Adept (it's 3 packages unless I'm wrong).

2) Download the packages I've posted:

[http://www.webalice.it/albertomilone/ubuntu/vim70_20060509-1_i386.deb]("http://www.webalice.it/albertomilone/ubuntu/vim70_20060509-1_i386.deb")

3) Install the package by doing a:
```
sudo dpkg -i vim70_20060509-1_i386
```[/QUOTE]

---

### Post by andrew! on 2006-05-18
I finally  manage to compile sucessfully. It seems ugrading pkg-config to 0.20 is necessary.

[QUOTE=andrew!]After reading all the posts and trying all the suggested actions, I still cannot compile vim7 with gui. Although I can install with this deb package, I need some more functions missing in this deb package, such as cscope support. Can anyone help me?

my configure commands:

```
./configure --prefix=/usr --with-x --enable-gui=gtk2 --x-includes=/usr/include/X11 --x-libraries=/usr/lib --enable-cscope --enable-perlinterp --enable-multibyte 

```
btw, I have the same problem with most of the people here:
```
checking for X... no
checking if X11 header files can be found... yes
checking --enable-gui argument... no GUI support

```[/QUOTE]

---

### Post by nuky on 2006-05-18
tseliot, thank you heeeeeeeeeeeaps for the .deb.. it was a life saver!! 

it worked well and installed vim70, but i 'm having a problem with changing my colorscheme in vim. only the font/syntax colors for the colorschemes are applied in vim, so i can't see any of the background/highlighting colors. However, in gvim, it works perfectly. I was wandering if anyone else has had this problem or if anyone knows what might be causing this? I also checked and i have all the lib files and ncurses packages mentioned at the beginning of this thread.. 

any help would be great, i LOVE vim and would love to get it sorted out.. sorry, i wasn't sure if this should have been a new thread :-? 

thanks, nuky.

---

### Post by gyhelle on 2006-05-18
Thanks, you solved my problem !

[COLOR="Red"][EDIT] I did a mistake, this is a no-python version .[/COLOR]
[COLOR="Red"][EDIT] corrected[/COLOR]

If someone is interested he can download my .deb here :
[http://gyhelle.free.fr/vim70_20060618-1_i386.deb](http://gyhelle.free.fr/vim70_20060618-1_i386.deb)

I compiled it with these options :
./configure --prefix=/usr/local --with-x --enable-gui=gnome2 --x-includes=/usr/include/X11 --x-libraries=/usr/lib --enable-pythoninterp --enable-multibyte --with-features=big


the vim ":version" fonctionalities :

+arabic +autocmd +balloon_eval +browse ++builtin_terms +byte_offset +cindent +clientserver +clipboard +cmdline_compl +cmdline_hist +cmdline_info +comments +cryptv +cscope
+cursorshape +dialog_con_gui +diff +digraphs +dnd -ebcdic +emacs_tags +eval +ex_extra +extra_search +farsi +file_in_path +find_in_path +folding -footer +fork() +gettext
-hangul_input +iconv +insert_expand +jumplist +keymap +langmap +libcall +linebreak +lispindent +listcmds +localmap +menu +mksession +modify_fname +mouse +mouseshape
+mouse_dec -mouse_gpm -mouse_jsbterm +mouse_netterm +mouse_xterm +multi_byte +multi_lang -mzscheme +netbeans_intg -osfiletype +path_extra -perl +postscript +printer
-profile +python +quickfix +reltime +rightleft -ruby +scrollbind +signs +smartindent -sniff +statusline -sun_workshop +syntax +tag_binary +tag_old_static -tag_any_white
-tcl +terminfo +termresponse +textobjects +title +toolbar +user_commands +vertsplit +virtualedit +visual +visualextra +viminfo +vreplace +wildignore +wildmenu +windows
+writebackup +X11 -xfontset +xim +xsmp_interact +xterm_clipboard -xterm_save

---

### Post by exclipy on 2006-05-18
This is awesome - tabs are life-changing, spellchecking and omni-complete are very nice.

I have one little niggle with the GUI.  If showtabline=1 (ie. the tab line shows only when there are > 1 tabs), it has problems when the window is maximised.  eg.  I'll have it maximised with one tab (no tab line showing) and create a new tab.  It'll do that, but I lose the status line at the bottom since the window normally needs to grow to accomodate the new tabline - but since it's maximised, it can't grow so the bottom of it just drops off.

I compiled it with tseliot's instructions, on Kubuntu Breezy.  For now, I'm working around it by using showtabline=2.

---

### Post by FredSambo on 2006-05-23
OK, so what are the advantages to using vim in GUI format vs. on the command line?

Seriously.  I want to know and maybe we can talk about it!

---

### Post by Crazy Man on 2006-05-23
[quote=FredSambo]OK, so what are the advantages to using vim in GUI format vs. on the command line?

Seriously.  I want to know and maybe we can talk about it![/quote] 
Well, I'd use the GUI version for writing more serious stuff (mostly because it's easier on the eyes (when configured correctly) and the options are there in the toolbar menu in case you for get them). The command line version I use for editing config/system files etc.

[quote=Moobert]ctrl+alt+pgup or ctrl+alt+pgdown[/quote]

Is there a way to change this, maybe in .vimrc?

---

### Post by FredSambo on 2006-05-25
> Well, I'd use the GUI version for writing more serious stuff (mostly because it's easier on the eyes (when configured correctly) and the options are there in the toolbar menu in case you for get them). The command line version I use for editing config/system files etc.

cool!  those are excellent reasons.  i administrate my servers from a remote terminal quite often, so i've kind of become one with vim; which means i've got what i call "feature tunnel-vision."  :) 

thanks!

---

### Post by bedge on 2006-06-05
Add this to sources.list for vim7

deb [http://www.freshnet.it/debian/](http://www.freshnet.it/debian/) dapper/

-Bruce

---

### Post by suxen on 2006-07-17
nousplacidus,
i had the same trouble as you did:

-> -enable-gui=gtk

It shows up as

..
checking --enable-gui argument... no GUI support
..

I installed the following library files:
libgtk-1.2
libgtk-1.2-common
libgtk-1.2-dev
libgtk-2.0-dev

Now it works.
Probably libgtk-1.2 is the important one, it is cited in the output I get
from ./configure --enable-gui=gtk:

checking for GTK - version >= 1.1.16... yes; found version 1.2.10

Hope that helps you

---

### Post by tseliot on 2006-07-17
Here is a guide about how to backport it from Edgy to Dapper:
[http://ubuntuforums.org/showthread.php?t=216916](http://ubuntuforums.org/showthread.php?t=216916)

---

### Post by futaris on 2006-07-18
> **bedge said:**
> Add this to sources.list for vim7

deb [http://www.freshnet.it/debian/](http://www.freshnet.it/debian/) dapper/

-Bruce

Thanks Bruce...  These installed easily.

---

### Post by RAV TUX on 2006-07-18
Edit:;)

---

### Post by Bionic-Badger on 2006-07-21
> **gyhelle said:**
> Thanks, you solved my problem !

I compiled it with these options :
./configure --prefix=/usr/local --with-x --enable-gui=gnome2 --x-includes=/usr/include/X11 --x-libraries=/usr/lib --enable-pythoninterp --enable-multibyte --with-features=big


Thank you for this command line.  Finally, I can use GVim on Ubuntu; what a life saver!

---

### Post by wittyguysuku on 2006-09-26
> **nousplacidus said:**
> I am having the same trouble with the gtk, and I tried downloading some of the packages but even when I use 

--enable-gui=gtk

It shows up as 

..
checking --enable-gui argument... no GUI support
..

Any ideas?

I too have the same problem when I rushed to install my fave editor :(

How can I fix this?
Any sort of help will be appreciated!

---

