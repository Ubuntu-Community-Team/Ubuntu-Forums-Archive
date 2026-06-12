---
title: "Finding the perfect Media Player"
date: 2006-06-23
forum: The Cafe
---

### Post by plueken on 2006-06-23
I'm wondering if anyone can point me to the Linux media (audio, to be honest) player of my dreams.  I want only three things, that I got accustomed to with Winamp 5 in my Windows days.

1. A popup toaster with track information whenever a song changes or I press a global hotkey (This one is common, I'll admit.  Nearly everyone has this capability.)

2. Media library capability.  Or the ability to have 5000+ songs in one playlist.  One way or another, I want to be able to search through all of my music collection for any particular song I might want, without having to open files or load other saved playlists.

3. Most important: something like the Winamp "Jump To File" popup.  I want to be able to press a global hotkey anywhere and bring up a tiny popup that can search through my library/playlist for any song I want, so my media player becomes less of an GUI and more of a background daemon that I never actually have to see.

Is there any *nix media player, famous or obscure, that meets these requirements (or has a plugin that can)?  Or should I humble myself by dropping #3 for now, and stick with the dependable amaroK?

Thanks.

plueken

---

### Post by roderikk on 2006-06-23
Hi,

I use XMMS and have it as a really tiny bar in the upper right corner of my screen to show some basic controls (I use XGL so my multimedia keyboard shortcuts don't really work).
XMMS also has a plugin called XMMSfind, which you can just install from the repos! and just does this thing you ask at number 3.

Hope this works for you.

---

### Post by BoyOfDestiny on 2006-06-23
[QUOTE=plueken]I'm wondering if anyone can point me to the Linux media (audio, to be honest) player of my dreams.  I want only three things, that I got accustomed to with Winamp 5 in my Windows days.

1. A popup toaster with track information whenever a song changes or I press a global hotkey (This one is common, I'll admit.  Nearly everyone has this capability.)

2. Media library capability.  Or the ability to have 5000+ songs in one playlist.  One way or another, I want to be able to search through all of my music collection for any particular song I might want, without having to open files or load other saved playlists.

3. Most important: something like the Winamp "Jump To File" popup.  I want to be able to press a global hotkey anywhere and bring up a tiny popup that can search through my library/playlist for any song I want, so my media player becomes less of an GUI and more of a background daemon that I never actually have to see.

Is there any *nix media player, famous or obscure, that meets these requirements (or has a plugin that can)?  Or should I humble myself by dropping #3 for now, and stick with the dependable amaroK?

Thanks.

plueken[/QUOTE]

[http://audacious-media-player.org/Main_Page](http://audacious-media-player.org/Main_Page)

AFAIK does everything you ask, not so sure about the sound library thing, I think the devs are working on something like that... Large playlists work fine, most hotkeys same as winamp (j for jump to file :) )

Hope this is what you are looking for.

---

### Post by Kimm on 2006-06-23
XMMS2 sounds like something for you.
But its not complete yet...

---

### Post by AndyCooll on 2006-06-23
If you liked Winamp then XMMS is probably the way to go since it models itself on it. If you do a search in Synaptic for XMMS you'll find the player plus loads of plugins, some of which will be of interest, many which won't!

:cool:

---

### Post by INMCM on 2006-06-23
[BMPx ]("http://bmpx.beep-media-player.org/site/BMPx_Homepage")

---

### Post by Wolki on 2006-06-23
[QUOTE=plueken]1. A popup toaster with track information whenever a song changes or I press a global hotkey (This one is common, I'll admit.  Nearly everyone has this capability.)

2. Media library capability.  Or the ability to have 5000+ songs in one playlist.  One way or another, I want to be able to search through all of my music collection for any particular song I might want, without having to open files or load other saved playlists.

3. Most important: something like the Winamp "Jump To File" popup.  I want to be able to press a global hotkey anywhere and bring up a tiny popup that can search through my library/playlist for any song I want, so my media player becomes less of an GUI and more of a background daemon that I never actually have to see.

Is there any *nix media player, famous or obscure, that meets these requirements (or has a plugin that can)?  Or should I humble myself by dropping #3 for now, and stick with the dependable amaroK?
[/QUOTE]

One player you might want to have a look at is Muine. It's in the repos, but a new and much much better version is out since a few days, you might want to grab that and compile it yourself (or maybe there's already a .deb?)

1. There is currently no toaster stuff, though a patch for the tray icon plugin exists that does this. I have not tried that yet, but I wrote a small python thing that displays them which works kinda ok. I've stopped using it myself since i have show/hide window on a global shortcut.
2. I find Muine's library to be one of the best. It doesn't really have large browsing capabilities, just add song/add album functionality that will filter the list of all your stuff for what you type. Simple but everything I need.
3. Get muine-shell, it will give you commands to control muine, which you can then define global shortcuts for. Press a key combination, a few letters, enter and you're done and back at what you were doing. Very nice.

By itself it's rather low-functional (designed to be good for playing stuff from your library and nothing else), but there are a number of plugins that greatly extend its functionality.

---

### Post by Hairy_Palms on 2006-06-23
you can make almost any player have global keyboard shortcuts,

* Run gconf-editor

* Go to "Apps->Metacity->Keybinding Commands"

Here we have a list of twelve slots for commands. We want one of them
(command_3, say) to Play/pause in audacious:

you can see a list of audacious commands by typing audacious --help in a terminal


Double click (or right-click and choose "Edit key" in the popup-menu), and you
will get to edit the key. In "Key Value", enter "audacious -t". Press OK.

Note that there is a bit of explanatory text at the bottom of the gconf-editor
screen.

We have our command, but now we must also tell Metacity what key to press to
run it. Go to "Global keybindings" (in the list to the left). As you see, there
are a lot of stuff to bind keys to. Scroll down until you find the line
"run_command_3" - it's about in the middle of the list.

* Select the line and double-click or select "Edit key". Change the key value
to "<Control>p". Press "Ok".

You're done! Try it by pressing ctrl-p and audacious should play or pause the current song! you can do the same with any other commands for it. :) im writing an updated howto to install audacious that ill post in the howto section later today.

---

### Post by BWF89 on 2006-06-23
Their making this sweet new media player based on Firefox. It's only in its alpha stage right now (version 0.1.1) and its only for windows (their currently porting it to Linux and Macintosh), and it crashes every 10 minutes.

But in a year or so it's going to be really good aslong as the company thats developing it doesn't go bankrupt.

[http://en.wikipedia.org/wiki/Songbird_%28software%29](http://en.wikipedia.org/wiki/Songbird_%28software%29)

---

### Post by jnev on 2006-06-23
[QUOTE=BWF89]Their making this sweet new media player based on Firefox. It's only in its alpha stage right now (version 0.1.1) and its only for windows (their currently porting it to Linux and Macintosh), and it crashes every 10 minutes.

But in a year or so it's going to be really good aslong as the company thats developing it doesn't go bankrupt.

[http://en.wikipedia.org/wiki/Songbird_%28software%29](http://en.wikipedia.org/wiki/Songbird_%28software%29)[/QUOTE]

I'm REALLY looking forward to this player... hopefully it'll be as good as they say it is.

---

### Post by BWF89 on 2006-06-23
[QUOTE=jnev]I'm REALLY looking forward to this player... hopefully it'll be as good as they say it is.[/QUOTE]
Me too, I installed it a few weeks ago but it was so unstable I removed it. I'll give it another try when they release 0.2. Until then I just use VLC.

---

### Post by plueken on 2006-06-23
Wow.  I was familiar with XMMS and beep-media-player already, but I hadn't known that there were so many new and updated projects in development, like XMMS2, BMPx, and Audacious.  I'm sure that I'll find what I'm looking for now (and thanks to roderikk for mentioning XmmsFind, because that plugin sounds exactly like my elusive #3!)

Thanks to everyone who helped out.  It's people like you that make me proud to be trying out Ubuntu Linux.

plueken

---

### Post by Mr Wrath on 2006-06-23
Try Windows Media Player 10---Just kidding...ok........I'll shut up.

---

