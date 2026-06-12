---
title: "Terminal based replacements for common GUI apps"
date: 2010-07-28
forum: The Cafe
---

### Post by neurolysis on 2010-07-28
Over the last year or so I've found myself increasingly using terminal-based apps over GUI equivalents. By terminal 'apps' I mainly mean programs that do something that usually a GUI based program would handle. I did some searching and couldn't find a thread like this, so I figured I'd make one :)

Here are the top few terminal apps that I use on a daily basis:

**irssi** - Very extensible and user friendly IRC client
**links2** - Good lightweight browser
**nano/vim** - Text editor, much more capable at handling certain types of text documents than gedit/leafpad, and not messing about with character encodings it doesn't understand
**rtorrent** - Very fast and flexible torrent client

I'd be interested in hearing some more like these, I'm always interested in hearing about new command line apps :)

---

### Post by blueturtl on 2010-07-28
Here you go:

**centerim-utf8** - Use MSN/Jabber/Yahoo/etc. instant messengers from the commandline
**moc** - Music player that has it all, detachable to the background
**wodim, cdrdao** - Burn and rip CDs from the commandline
**htop** - Glorified task management for the console
**mc** - Two pane file manager that has built in FTP and pull-down menus as well as keyboard shortcuts

p.s. Also cool:

**ffmpeg** - cut, combine, (re)encode video/audio from the commandline

p.p.s. The coolest of all:

**screen** - "Window manager" for the console, use all the text mode apps you want ... at the same time!

---

### Post by zephyrblade on 2010-07-28
**newsbeuter** for rss feeds (though I'm not sure if I could drop google reader just yet ...)
[B]
elinks[/B] is often my browser of choice
[B]
feh[/B] for images (elinks plays nice with it too!)
[B]
nethack[/B] for gaming!

rtorrent used in conjunction with screen is great stuff!


I take it you know of k.mandla's fantastic site? 'Tis recomended:
 
 [http://kmandla.wordpress.com/software/](http://kmandla.wordpress.com/software/)

---

### Post by neurolysis on 2010-07-28
Thanks for the posts so far guys, didn't know quite a few of these :D

> **zephyrblade said:**
> I take it you know of k.mandla's fantastic site? 'Tis recomended:
 
 [http://kmandla.wordpress.com/software/](http://kmandla.wordpress.com/software/)

I didn't know of that until now, thanks!

---

### Post by samalex on 2010-07-28
GoogleCL is great -- [http://code.google.com/p/googlecl/](http://code.google.com/p/googlecl/)

Sam

---

### Post by Zorgoth on 2010-07-29
emacs -nw

- the terminal replacement for *all* GUI apps =D

---

### Post by nothingspecial on 2010-07-29
cmus for your music
screen/byobu for you desktop environment

---

### Post by wkhasintha on 2010-07-29
youtube-dl - download youtube videos (duh!)
mplayer

---

### Post by jerenept on 2010-07-29
links (web browser)
nano (text editor)

---

### Post by Legendary_Bibo on 2010-07-29
> **Zorgoth said:**
> emacs -nw

- the terminal replacement for *all* GUI apps =D

Draw the Mona Lisa with GIMP. ;)
You do need a GUI for some things, I'm sorry, but there's just no one solution to all.

---

### Post by mr_hangman on 2010-07-29
**mutt** - email client

---

### Post by NMFTM on 2010-07-29
> **Zorgoth said:**
> emacs -nw

- the terminal replacement for *all* GUI apps =D
I've just recently started tinkering with Emacs and I have to say, I really like the macros. The only problem is that when you try to impliment the macros outside of Emacs they'll conflict with other common macros (ctrl+f in Firefox is the find bar but in Emacs is the right arrow) and you'll have to choose one macros set over the other. And no matter which you choose you'll end up loosing some functionality.

Even more troublesome, forums like these which have nothing to do with what OS your using will have keystrokes automatically bound. Like ctrl+b for bolding text while that's the left arrow key in Emacs. Most of the time C-b will move backwards one character. But sometimes it'll bold text.

I hope there is a solution to this. But I've been kind busy (and lazy) lately and haven't looked for one yet.

I really wish that all apps would come with Emacs keybindings just like ctrl+c and ctrl+v is the standardized copy and paste among pretty much all apps and OS's. If I ever became dictator I think I might use my power to force developers to adopt Emacs macros in their apps and have it taught in schools right after basic keyboarding. Shortly there after I would switch my country over to the metric system.

---

### Post by mr_hangman on 2010-08-01
Can anyone login to facebook with one of these terminal based browser? 
I tried w3m, links2, elinks and lynx. Looks like none of them is supported.

---

### Post by limestone on 2010-08-01
moc - command line music player
nano - editor
mc - midnight commander (file manager)
elinks - web browser

---

### Post by red_Marvin on 2010-08-01
> **mr_hangman said:**
> Can anyone login to facebook with one of these terminal based browser? 
I tried w3m, links2, elinks and lynx. Looks like none of them is supported.

They are filtering based on the user agent string, try changing it.

---

### Post by mr_hangman on 2010-08-01
> **red_Marvin said:**
> They are filtering based on the user agent string, try changing it.

Thanks Marvin. I got it worked on links2 with the option -fake-user-agent :).

```
links2 -fake-user-agent Chrome/6.0.472.11 www.facebook.com
```

---

