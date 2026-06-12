---
title: "possible to do all your regular computing in terminal ?"
date: 2009-07-17
forum: The Cafe
---

### Post by djmh on 2009-07-17
is it possible to do evrything that you would normally do with a gui in terminal ?

im thinking it would be a neat challenge to go a few days of only using terminal...but would i be able to do all my regular stuff?

what i mean by regular stuff is basically just
music
email
surf the web

possible ?

---

### Post by mr.propre on 2009-07-17
> **djmh said:**
> is it possible to do evrything that you would normally do with a gui in terminal ?

im thinking it would be a neat challenge to go a few days of only using terminal...but would i be able to do all my regular stuff?

what i mean by regular stuff is basically just
music
email
surf the web

possible ?

Yes if you use CLI based programs.
For e-mail you can use Alpine
For the web W3C or Lynx
Don't know a good music program but they exist.

---

### Post by canadiandude007 on 2009-07-17
mpg123 player is command line (CLI) one => [http://www.mpg123.de/](http://www.mpg123.de/)

---

### Post by jelle_ on 2009-07-17
moc is a nice music player

---

### Post by sisco311 on 2009-07-17
[http://www.jaredandcoralee.com/CLIapps.html]("http://www.jaredandcoralee.com/CLIapps.html")

---

### Post by DeadSuperHero on 2009-07-17
I have some experience in the matter.

Short answer: Yes.

Long answer:

This should be an easy guide: [http://seanrtilley.blogspot.com/2008/06/goodbye-gui-thirty-days-of-command-line.html](http://seanrtilley.blogspot.com/2008/06/goodbye-gui-thirty-days-of-command-line.html)

You'll have to keep up with the days, I did it for a whole month with no X session running whatsoever. You can do Twitter, IM, IRC Chat, Music Playing, and even watch an ASCII-style movie with an MPlayer frontend, I believe.

A consolidated app list:

-screen: can work as a sort of "Task Bar" in which you navigate back and forth with a keyboard
-elinks: Great text-based web browser. My personal favorite. Hitting Esc key brings down menu.
-Nano: A simple text editor. There are better ones out there, but this is great for simple notes to yourself.
-Finch: Great IM, bonus if you already use Pidgin, since it uses libpurple.
-irssi: Great IRC app.
-cplay: My personal favorite CLI music player. Works best with sox, mpg123 (I think that's what it was called), and vorbis-tools.

There are more on the blog. Have fun!

---

### Post by abhilashm86 on 2009-07-17
> **djmh said:**
> is it possible to do evrything that you would normally do with a gui in terminal ?

music
email
surf the web

possible ?

yes it is possible to do all in terminal, just browse man [software/tool] to get usage details,
ex- man vim

basically i use
music- 
mocp = a lightweight superfast audio player
mplayer = for certain vids

email= try setting up your own mail server
mutt = email client for gmail, you can include imap!!

surf the web = 
elinks = superfast text browser...........

for other help forums is always there!!!

---

### Post by Sublime Porte on 2009-07-17
djmh,

There are replacements for everything, check out [this list of apps]("http://www.terminally-incoherent.com/blog/2007/05/21/a-day-without-x/") you can use in virtual console or virtual framebuffer.

There's even a framebuffer web browser and of course image and video viewers, which will actually create proper graphics in your framebuffer.

[Here is an image](http://www.nocrew.org/software/zen/screenshots/ofbis-screenshot-1.png) of images being loaded in the framebuffer web browser. It's not that pretty, but it's certainly possible.

Mr. Psychopath,

> and even watch an ASCII-style movie with an MPlayer frontend, I believe.Actually it's even possible to view actual movies, images and do many things without ever firing up X. Mplayer has an option to use the framebuffer to display the video.

I went for several years without using X (back a long time ago before there was much video card support for Linux), and I accomplished everything I ever needed to do.

---

### Post by Mornedhel on 2009-07-17
One word.

"Emacs".

(And yes, I do my mail and music in Emacs, and there's a web browser but no javascript or Flash support, sadly. I also do IM and IRC. And a lot more.)

---

### Post by binbash on 2009-07-17
Yup that is what i do except surfing and video stuff ;)

---

### Post by RiceMonster on 2009-07-17
> **djmh said:**
> music
moc
mpd (using ncmpcpp or just mpc)
cmus
cplay
mplayer

> **djmh said:**
> email
alpine
mutt

> **djmh said:**
> surf the web
elinks
links
lynx

---

### Post by chucky chuckaluck on 2009-07-17
gmail will even work in elinks.

+1 for cplay. you can use streamripper, as well.

bsdgames are fun, especially if you're a senior.

---

### Post by sertse on 2009-07-17
Try INX, it's in my sig. It's a live CD focusing on doing being regular computing from the terminal. Let the colourful ascii-like bash menus guide you in introducing a world of terminal apps to fulfil almost any need. Also explore the tutorials, they give a really good, interactive primer into console commands and how to use it use it effectively.

---

### Post by K.Mandla on 2009-07-17
> **djmh said:**
> is it possible to do evrything that you would normally do with a gui in terminal ?

im thinking it would be a neat challenge to go a few days of only using terminal...but would i be able to do all my regular stuff?

what i mean by regular stuff is basically just
music
email
surf the web

possible ?
Yes.

[http://kmandla.wordpress.com/software#Terminal](http://kmandla.wordpress.com/software#Terminal)
[http://kmandla.wordpress.com/2009/05/10/do-more-with-less/](http://kmandla.wordpress.com/2009/05/10/do-more-with-less/)
[http://kmandla.wordpress.com/2009/05/21/quit-x-screen-vs-is-more-fun/](http://kmandla.wordpress.com/2009/05/21/quit-x-screen-vs-is-more-fun/)

Lots of people live without a graphical desktop. You can do nearly anything with CLI and framebuffer applications you can do with the full X suite. And it's much easier on your system resources.

---

### Post by djmh on 2009-07-17
this is great guys, im defiantly going to try this out.

the whole reason i want to do it is to just learn a little more about how everything works.

would this be a good way to begin learning how a computer actually works ?

thanks for all the great info, and links evryone !

---

### Post by calrogman on 2009-07-17
mpg123/ogg123/mplayer for music.
mutt for email
w3m/lynx/links for web browsing (I prefer links, you should try it some time)
nano simple file editing
alsamixer adjusting the volume

tl;dr yes

---

### Post by MaxIBoy on 2009-07-17
Mutt or Alpine for emai. I've used both, I got the impression that Alpine was more fully-featured but Mutt was easier to setup.

For webrowsing, Lynx, Links, or Elinks. In my opinion, Links and Elinks render things more nicely than Lynx. Elinks supports tabbed browsing, and I don't think the others do.

For music and movies, look no farther than good ol' VLC (install the package "vlc-nox.") VLC can play sound from the command line. If you have a [framebuffered display](https://wiki.ubuntu.com/FrameBuffer) setup, *and* if VLC has been compiled with support for directfb, you can run this command:
```
vlc -vout fb [other arguments and filenames go here]
```

---

### Post by l-x-l on 2009-07-17
Good luck... be sure to let us know how it goes.

---

### Post by l-x-l on 2009-07-17
> **Mr. Psychopath said:**
> I have some experience in the matter.

You'll have to keep up with the days, I did it for a whole month with no X session running whatsoever... 

What made u stop after 1 month?

---

### Post by djmh on 2009-07-17
i will defiantly post my experience here.

it would be kinda neat to make a terminal day, one day a year where everybody uses terminal :)

---

### Post by koleoptero on 2009-07-21
Is there a terminal app that supports rtf editing? I'd truly love it if there were.

---

### Post by .Maleficus. on 2009-07-21
> **koleoptero said:**
> Is there a terminal app that supports rtf editing? I'd truly love it if there were.
There's a Vim plugin you could use.

[http://www.vim.org/scripts/script.php?script_id=1432](http://www.vim.org/scripts/script.php?script_id=1432)

And one for Emacs.

[http://savannah.nongnu.org/projects/emacs-rtf/](http://savannah.nongnu.org/projects/emacs-rtf/)

---

### Post by koleoptero on 2009-07-21
I was thinking more in the lines of actually displaying bold and italics etc...

---

### Post by Mornedhel on 2009-07-21
> **koleoptero said:**
> I was thinking more in the lines of actually displaying bold and italics etc...

Emacs supports bold, italics, and underline.

---

### Post by koleoptero on 2009-07-21
> **Mornedhel said:**
> Emacs supports bold, italics, and underline.

Hmmm... I haven't checked emacs in a decade or so... might give it a try, thanks.

---

### Post by marshag63 on 2009-07-21
++++1 for INX!  

You can't beat a live CD already set up to do the things you normally do in your average day, plus lots of great CLI tutorials to learn the essentials like:  

[LIST]
[*]apt-cache search -- when you are wondering "is there a program for that?

[*]using the up arrow at the command line  - you just typed a long command and made a typo - DOH!!!!  Just press the up arrow and there's your command, now move your cursor to the left and fix the mistake, when correct press enter - voila!
[/LIST]

INX comes with six terminals all set up and ready - some are:

One for learning tutorials.

One for listening to music via internet or on your computer

One for surfing web, IRC and email - all CLI

You can also:  

Watch a video in CLI 

Check Gmail (and view attachments)

IRC chatting (irssi)

Work on a spreadsheet, do calculations or check your schedule.

Have multiple CLI apps open on one screen (using "screen" or "dvtm."

Work with the files on your hard drive.

Monitor your network, connect to network wirelessly (ceni)

Boot INX to ram and the put your favorite CD in and listen to it.

Or even try the virtual box version.

Its already set up in one live CD - I know I'm learning a lot!!!

[http://inx.maincontent.net/download.html](http://inx.maincontent.net/download.html)

Let us know what you think of INX.

MarshaG.

---

### Post by clarkmkfox on 2009-07-22
I do all my programming work using the command line, vim, python, shell, java, apache ... love it.
but for web surfing? I sometime use lynx for fun, but for day to day work, just use firefox man.

---

### Post by praveesh on 2009-07-22
I wonder how the web browsing would be , without colours (isn't the terminal monochromatic?)and clicking.

---

### Post by RiceMonster on 2009-07-22
> **praveesh said:**
> I wonder how the web browsing would be , without colours (isn't the terminal monochromatic?)and clicking.

The terminal has colours. Type 'ls --color=auto' to see for yourself. Also, if you're curious to see what it's like to browse the web in the terminal, why don't you install elinks or something and try it?

---

### Post by Mornedhel on 2009-07-22
> **praveesh said:**
> I wonder how the web browsing would be , without colours (isn't the terminal monochromatic?)and clicking.

The terminal has colors. You can use the keyboard to navigate between links and follow them.

---

### Post by praveesh on 2009-07-22
> **RiceMonster said:**
> The terminal has colours. Type 'ls --color=auto' to see for yourself. Also, if you're curious to see what it's like to browse the web in the terminal, why don't you install elinks or something and try it?

ok  I shall try. Thanks

---

### Post by Mornedhel on 2009-07-22
In the interest of full disclosure, here is what my emacs session looks like. It's a pretty good example of "doing all your regular computing in terminal". Note that I don't actually often use the web browser, usually I just run Firefox. The rest of the screenshots are actual screenshots of my actual workflow. Also note that the terminal definitely supports color, and bold and underlined text. Some terminal emulators also support italics, but apparently it's not very common.

Screenshot-1 : Writing a paper in LaTeX, compiling and managing a bibliography. Emacs major modes AucTeX, BibTeX and the output of the compilation in three buffers. Notice in this and the following screenshots that in the modeline a little something warns me that someone said my nick in IRC. (Not showing the IRC mode for obvious privacy reasons.)

Screenshot-2 : Listening to Blind Guardian in EMMS. Emacs major modes Emms-Browser (left buffer) and Emms-Playlist (right buffer). The backend is MPD, EMMS is just a client.

Screenshot-3 : E-mail client. Wanderlust mail client in Emacs (multiple IMAP accounts in left buffer, summary for one account in right buffer).

Screenshot-4 : viewing this thread in a w3m session within Emacs.

The whole thing is within a single terminal. Emacs supports multiple windows : in a console or terminal emulator, this degrades to multiple workspaces (within one Emacs instance).

---

### Post by RiceMonster on 2009-07-22
I'm going to be honest, I don't know why you would want to listen to music or browse the web in an editor. Do one thing and do it well. You can also manage multiple windows in the console with screen, tmux, or dvtm.

---

### Post by praveesh on 2009-07-22
Thanks

---

### Post by Mornedhel on 2009-07-22
> **RiceMonster said:**
> I'm going to be honest, I don't know why you would want to listen to music or browse the web in an editor. Do one thing and do it well. You can also manage multiple windows in the console with screen, tmux, or dvtm.

Well, Emacs isn't an editor so much as a Lisp interpreter with a solid I/O layer that happens to be good at text edition.

As I mentioned, I don't actually browse the web in w3m, it was only included to illustrate the fact that it is possible.

Also, I don't "listen to music in an editor", I just listen to music, and from time to time I interact with the music player, and the keybindings are the same as in most of the rest of Emacs. (The multimedia keys even work.)

Mostly I like Emacs because I understand a bit of Lisp and I can extend it as I like. For instance, EMMS doesn't have a notification system. I took some elisp someone wrote to have the IRC client talk to libnotify and modified it so that EMMS would display a notification (with the fancy Ubuntu boxes) when a new track played. It took me ten minutes in all.

Also it infuriates the vim users.

*shrug* Why not ?

---

### Post by SuperSonic4 on 2009-07-27
[[img]http://imgs.xkcd.com/comics/real_programmers.png[/img]](http://xkcd.com/378/)

---

### Post by dragos240 on 2009-08-17
Photo viewing? How do you use fbi?

---

### Post by CJ Master on 2009-08-17
> **praveesh said:**
> I wonder how the web browsing would be , without colours (isn't the terminal monochromatic?)and clicking.

Framebuffer is ftw?

---

### Post by TheNessus on 2009-08-17
> **SuperSonic4 said:**
> [[img]http://imgs.xkcd.com/comics/real_programmers.png[/img]](http://xkcd.com/378/)

lol

---

