---
title: "Vim 256 color display problems (Ubuntu Server)"
date: 2018-03-02
forum: Server Platforms
---

### Post by rdtzn1 on 2018-03-02
Hi All

I'm new to Linux so apologies in advance for any dumb questions.

I've recently set up Ubuntu Server on an old laptop that I have.
I'm trying to get the zenburn colorscheme working in Vim but it requires enabling 256 color mode.

This seemed like it would be pretty straightforward. 
The instructions that I followed explained that I needed to set my TERM environment variable to xterm-256color like this:

```
if [ -e /usr/share/terminfo/x/xterm-256color ]; then
        export TERM='xterm-256color'
else
        export TERM='xterm-color'
fi
```
however the x directory did not exist as it appears that xterm was not installed.
So I installed it using sudo apt-get install xterm.

However, when I tried to run xterm, I got a message which said xterm: Xt error: Display not set (or something along those lines) 
so I ran export DISPLAY=:0.0
and now get a message which says xterm: Xt error: Can't open display: :0.0
I've also tried with Display=:0 and Display=:1 but get the same message.

Also the x directory in terminfo still does not exist.
If anyone could point me in the right direction for enabling 256 color mode I would be very grateful.
Installing this colorscheme seemed like a 5 minute job which has now consumed most of my afternoon!

---

### Post by slickymaster on 2018-03-02
Thread moved to **Server Platforms** for a better fit

---

### Post by rdtzn1 on 2018-03-03
Ok - I've solved this problem.
For the record, in case anyone else experiences a similar issue. the problem was that my terminal didn't support 256 colours.
So I installed a new terminal (I actually installed 2, gnome-terminal and terminator to see which I preferred - the jury is still out).
I then couldn't get them to work either as I didn't have an X environment.
So I used :

sudo apt-get install xorg
sudo apt-get install openbox

I can now use 

startx terminator (or startx gnome-terminal) to launch a terminal which supports 256 color mode, the colorscheme works and VIM now looks great.

Also for the record, according to the comments on the page that I got the code snippet from ([http://vim.wikia.com/wiki/256_colors_in_vim](http://vim.wikia.com/wiki/256_colors_in_vim)), "Setting $TERM in the shell profile is generally a bad idea, since you may wish to use different terminals. It is preferable to add it to  .Xdefaults (or similar file read by X applications):" - and definitely don't do the other bit that he suggests:

set t_AB=^[[48;5;%dm
set t_AF=^[[38;5;%dm

as (in an incompatible terminal) this can make any documents opened in Vim display a whole load of gobbledygook making them totally unreadable.

---

