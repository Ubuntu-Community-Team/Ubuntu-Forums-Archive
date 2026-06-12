---
title: "default terminal replacement"
date: 2007-09-29
forum: The Cafe
---

### Post by n3tfury on 2007-09-29
i'm really starting to love using the terminal for as many things as i can and am curious if you fine folks use something other than the default terminal in Ubuntu. i've searched the forums but of course "terminal" is used just about in every thread, so forget it, i'm starting this one.

i know of eterm and tilda, but haven't tried either of these until i hear some suggestions/comments.  

thanks  ;O

---

### Post by fwojciec on 2007-09-29
I have 5 letters for you: urxvt (the unicode version or rxvt).  It takes a while to configure to your liking (configuration is done via .Xdefaults file) but once it's properly set up it looks great and works even better.

Screenshot:
[[IMG]http://img233.imageshack.us/img233/3245/urxvtur4.th.png[/IMG]](http://img233.imageshack.us/my.php?image=urxvtur4.png)

Small explanation: the line at the bottom is not a part of urxvt - it's a separate application called screen.

---

### Post by t0p on 2007-09-29
I kinda like Ctrl-Alt-F1-F6.  No cutting and pasting, I know, but it reminds me of the TRS-80.  Retro roools!!

Damn, now you all know I'm *old*.

---

### Post by fwojciec on 2007-09-29
> **t0p said:**
> I kinda like Ctrl-Alt-F1-F6.  No cutting and pasting, I know, but it reminds me of the TRS-80.  Retro roools!!

Damn, now you all know I'm *old*.

Just install gpm and voila - cut & paste enabled.  Also you can use gnu screen to cut and paste using keyboard only ;)

---

### Post by thomashauk on 2007-09-29
And If you want to replace bask, fish is a good choice, tab-completion for the win!

---

### Post by n3tfury on 2007-09-29
> **fwojciec said:**
> I have 5 letters for you: urxvt (the unicode version or rxvt).  It takes a while to configure to your liking (configuration is done via .Xdefaults file) but once it's properly set up it looks great and works even better.

Screenshot:
[[IMG]http://img233.imageshack.us/img233/3245/urxvtur4.th.png[/IMG]](http://img233.imageshack.us/my.php?image=urxvtur4.png)

Small explanation: the line at the bottom is not a part of urxvt - it's a separate application called screen.

thats sounds a bit hardcore for me :/

---

### Post by n3tfury on 2007-09-29
i also forgot to add: i'd like something with tabs (tab completion is cool too) but that's not what i'm talking about.

---

### Post by p_quarles on 2007-09-29
Have you tried Konsole? If not, it sounds like what you're looking for: very convenient tabbing, much easier to customize than gnome-terminal. I haven't tried it in Gnome, but it should work fine.

Btw, I'm assuming you meant gnome-terminal when you said the "default" terminal. If you meant all the default terminals for various flavors, then disregard.

---

### Post by RAV TUX on 2007-09-29
> **n3tfury said:**
> i'm really starting to love using the terminal for as many things as i can and am curious if you fine folks use something other than the default terminal in Ubuntu. i've searched the forums but of course "terminal" is used just about in every thread, so forget it, i'm starting this one.

i know of eterm and tilda, but haven't tried either of these until i hear some suggestions/comments.  

thanks  ;O

I also love using the terminal, don't understand why anybody would want to use anything else?

When I want a full and complete power user terminal I use Konsole:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=44805&d=1191110261[/IMG]

When I want to simply do an update or just install one or two things I use the default terminal:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=44806&d=1191110261[/IMG]

---

### Post by n3tfury on 2007-09-29
> **p_quarles said:**
> Have you tried Konsole? If not, it sounds like what you're looking for: very convenient tabbing, much easier to customize than gnome-terminal. I haven't tried it in Gnome, but it should work fine.

Btw, I'm assuming you meant gnome-terminal when you said the "default" terminal. If you meant all the default terminals for various flavors, then disregard.

i will check Konsole out, thank you!  yeah i meant gnome-terminal :)

---

### Post by n3tfury on 2007-09-29
> **RAV TUX said:**
> 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=44806&d=1191110261[/IMG]

i knew you'd be replying :P  thanks for the shots i'm opening synaptic now..

---

### Post by blithen on 2007-09-29
> **n3tfury said:**
> i knew you'd be replying :P  thanks for the shots i'm opening synaptic now..
O:! I am shocked! Why use synaptic when you can simply do 
```
sudo apt-get install konsole
```

---

### Post by Frak on 2007-09-29
You tried Konsole? I find it as good as Terminal, sometimes better. :)

---

### Post by n3tfury on 2007-09-29
lol, after i had posted that then started to open synaptic, i was like "wtf am i doing" and opened the terminal.  i should've edited my post but didn't think about it hehe.

i like Konsole, i think it's just what i was looking for.  funnily enough i also came across kuake.  for those that have played quake, the console is just like hitting the ~ in quake.

[http://199.231.140.154/kuake.php](http://199.231.140.154/kuake.php)

don't think i'm gonna try it though since it'd be too big.

---

### Post by RAV TUX on 2007-09-29
> **n3tfury said:**
> i knew you'd be replying :P  thanks for the shots i'm opening synaptic now..

A screenshot is worth a thousand words. ;)

---

### Post by RAV TUX on 2007-09-29
> **n3tfury said:**
> lol, after i had posted that then started to open synaptic, i was like "wtf am i doing" and opened the terminal.  i should've edited my post but didn't think about it hehe.

i like Konsole, i think it's just what i was looking for.  funnily enough i also came across kuake.  for those that have played quake, the console is just like hitting the ~ in quake.

[http://199.231.140.154/kuake.php](http://199.231.140.154/kuake.php)

don't think i'm gonna try it though since it'd be too big.

Honestly no matter what DE I am using I always do:

```
sudo apt-get install kde
```

Whether I am using e17, like I am now or if I am using GNOME, XFCE or Fluxbox I always install KDE, the KDE applications are just too powerful to ignore.

Whether it be AmaroK, K3B, Konsole, Kopete, Konqueror, Konversation, Kopete, KTorrent, Ksnapshot or Ksudoku...I can't imagine Linux without KDE applications.

---

### Post by oldos2er on 2007-09-29
zsh.

---

### Post by n3tfury on 2007-09-29
> **RAV TUX said:**
> Honestly no matter what DE I am using I always do:

```
sudo apt-get install kde
```



i don't care for KDE stuff, but i do use K3B and Amarok (and now Konsole) but i can live without the rest

---

### Post by RAV TUX on 2007-09-29
> **n3tfury said:**
> i don't care for KDE stuff, but i do use K3B and Amarok (and now Konsole) but i can live without the restFair enough, try KSnapshot and KSudoku ;)

---

### Post by n3tfury on 2007-09-29
> **RAV TUX said:**
> Fair enough, try KSnapshot and KSudoku ;)

for screenshots i've been trying to use scrot in the terminal.  i'll have to take a look at ksudoku, thanks

---

### Post by RedSquirrel on 2007-10-01
Most of the time, I use uxterm configured using ~/.Xdefaults. On rare occasions, I use urxvt (package: rxvt-unicode). 

You might also want to look at xfce4-terminal. It's quite nice (especially if you are running Xfce ;)).

---

### Post by fuscia on 2007-10-01
don't let urxvt scare you (just a humble end user, here). it has a lot of options you can learn over time. i don't mess with the .xdefaults, i just write the options into my openbox and fluxbox menus (you can do the same in xfce, i think).

---

### Post by RageOfOrder on 2007-10-01
I typically use Konsole now, but my choice used to be aTerm when I ran fluxbox
and I use eith urxvt or enterminus on my e17 laptop

---

### Post by der_joachim on 2007-10-01
I really like Yakuake. It's basically Konsole in a quake-like terminal (press ~ for a console). It is in the repos.

---

### Post by Havoc on 2007-10-01
WTF nobody mentioned Mrxvt. And the effects in those screenshots can be done with *any* terminal and shell combination. Even the very minimalistic rxvt + ash can do that. Ehm.

---

### Post by maybeway36 on 2007-10-01
xfce4-terminal isn't too bad uner GNOME. I use both Konsole and Yakuake, actually.

---

### Post by bonzodog on 2007-10-01
> **oldos2er said:**
> zsh.

+1 on that.

Yes, give zsh a try. It's a real power user shell, does all that bash does plus a lot more. I now have zsh set as my default shell, and it's the first thing that I install on any Linux box now before I set-up the user accounts, so I can point them to the zsh shell.

---

### Post by Pancetilla on 2007-10-01
I use tilda with Gnome and yakuake with Kde...but you can also try [Guake]("http://guake-gnome-vte.sourceforge.net/")

---

### Post by n3tfury on 2007-10-01
thanks again for the suggestions.  just for kicks on my next day off, i'm going to try each one of these :)

---

### Post by DoktorSeven on 2007-10-01
xterm.

Simple, no fluff, awesome.

I'll never leave bash though.

---

