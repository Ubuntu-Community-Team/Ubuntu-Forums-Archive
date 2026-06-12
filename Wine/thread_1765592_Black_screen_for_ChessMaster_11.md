---
title: "Black screen for ChessMaster 11"
date: 2011-05-23
forum: Wine
---

### Post by layers on 2011-05-23
So, I installed the game, it did not have any problems doing that. After that, I clicked on "Install DirextX" below the play button, it installed. I made a new player, but after that there is a black window, and from what I can see, there is sound. How can I make it work?
I tried following some guide to install winetricks, but all that happens is that it says "winetricks now lives in" some website.

---

### Post by layers on 2011-05-23
According to [this]("http://ubuntuforums.org/showthread.php?p=9934603#post9934603") I have to install [these]("http://jeffhoogland.blogspot.com/2010/07/howto-starcraft-2-on-linux-with-wine.html"):
```
cd ~/Downloads
wget http://winezeug.googlecode.com/svn/trunk/winetricks
chmod +x winetricks
./winetricks droid fontfix fontsmooth-rgb gdiplus gecko
./winetricks vcrun2008 vcrun2005 allfonts d3dx9 win7
winecfg

```and to **add** and **disable** mmdevapi dll.

But on this first actual step, I think it is not installing it, but I don't know what to do.
```
ibo@ibo-laptop:~/Downloads$ ./winetricks droid fontfix fontsmooth-rgb gdiplus gecko
Winetricks now lives in the svn repository at http://winetricks.org
ibo@ibo-laptop:~/Downloads$ 

```What does that mean? To install winetricks from Software Center? (no such thing in there)

---

### Post by Kladiator on 2011-05-24
I can't help you with your problem but I think you might be possibly be interested in knowing that Chessmaster 10, which from what I read is very similar to your version, works perfectly well on Virtualbox (XP Pro guest),
without the single smallest glitch.

The game looks and behaves exactly like on a native Windows installation.

---

