---
title: "Productive habits..."
date: 2009-02-17
forum: The Cafe
---

### Post by somethingkindawierd on 2009-02-17
I was just wondering what experienced Linux/Ubuntu users do to be more productive on Linux. What habits, software tools, tweaks, etc. do you employ to be more productive? And by "more productive" I mean more so than competing operating systems or even the vanilla Ubuntu install.

---

### Post by nothingspecial on 2009-02-18
Aliases. In your .basrc you can create custom commands that you assign to real commands. For example if I want to ssh into my server I type

```
ssh -X -C -c blowfish me@192.168,1.4
``` alot of typing so in my .bashrc I add the line

   ```
 alias server='ssh -X -C -c blowfish me@192.168.1.4'
```

Now I only have to type ```
server
```

a few more I use

```
alias mp3s='sshfs server me@192.168.1.4:/media/disk/music'
```

So to mount my Flac collection as mp3s I just type mp3s.

And to listen to BBC 6Music I just type 6music

```
 alias 6music='mplayer mms://wmlive.bbc.net.uk/wms/6music/6music_e2s1
```

Another thing is to learn to become independent of the mouse, gnome-do is a great app for this.

```
sudo apt-get install gnome-do
```

---

### Post by somethingkindawierd on 2009-02-18
Yeah! I have wondered how to create aliases to commands, but have yet to research it. Thanks.

And I completely agree about Gnome-Do...it is an exceptional application.

---

### Post by nothingspecial on 2009-02-18
It`s not just gnome-do, it`s learning the keyboard shortcuts for your favourite apps, firefox shortcuts, gnome shortcuts etc etc. You`ll be suprised how much faster everything is.

Also if your searching the web for information or just browsing these forums, ie not watching youtube or shopping etc then use a commandline web browser such as lynx or elinks. They`re like lightning compared to good old ff. 

Same goes for everything really. Command line apps by their nature are faster than gooeys. If you know the path to the file you want to use and use the tab key alot.

---

