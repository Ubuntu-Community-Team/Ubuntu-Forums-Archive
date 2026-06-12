---
title: "Help me find Web/file editer?"
date: 2010-11-02
forum: The Cafe
---

### Post by Scarcer on 2010-11-02
The other day I had seen someone post screen shots of their desktop.

They had a file editor running on top of the wallpaper with 3 or 4 tables open editing various css/php files. I'm not sure if the editor was for web editing exclusively or for file editing in general.

Either way I could really use what ever program that was.  Would be a big help if someone could name it for me.

Edit: this post
[http://ubuntuforums.org/showpost.php?p=9911290&postcount=16](http://ubuntuforums.org/showpost.php?p=9911290&postcount=16)

---

### Post by dr_duck on 2010-11-02
Well the editor itself looks like vi (or vim) which is a generic console-based text editor. Some people love it, others hate it.  It's the marmite of text editors.

Somehow the guy/gal has it running either in a borderless terminal window, or directly on the desktop (not entirely sure how to do that anymore, xterm might be able to do it).

vim has syntax highlighting for almost everything, and can split the window into as many sections as you want (hence the table layout), boatloads of extensions & shortcuts: like a swiss army knife - very capable but prone to chopping your thumbs off.

Probably best to pm the guy/gal & ask for their config file, I'm sure they'd share.

---

### Post by Spice Weasel on 2010-11-02
They are using either a tiling window manager or Terminator. Looks to me like they are running the text editor vi in Terminator which is basically a terminal emulator that lets you split it into tables.

---

### Post by slackthumbz on 2010-11-02
Vi is both awesome and hardcore, learn it. Women will want you and men will want to be you. It's a well known fact that people who use Vi are naturally superior in all respects to people who don't use it. It's the ninja badass of text editors. :twisted:

---

### Post by Spice Weasel on 2010-11-02
Emacs has a command that turns you in to a ninja badass.

---

### Post by slackthumbz on 2010-11-02
> **Spice Weasel said:**
> Emacs has a command that turns you in to a ninja badass.

Pretty sure we're not supposed to discuss religion on this forum ;)

---

### Post by slackthumbz on 2010-11-02
> **Scarcer said:**
> The other day I had seen someone post screen shots of their desktop.

They had a file editor running on top of the wallpaper with 3 or 4 tables open editing various css/php files. I'm not sure if the editor was for web editing exclusively or for file editing in general.

Either way I could really use what ever program that was.  Would be a big help if someone could name it for me.

Edit: this post
[http://ubuntuforums.org/showpost.php?p=9911290&postcount=16](http://ubuntuforums.org/showpost.php?p=9911290&postcount=16)

Ah, since that's my screen shot I should probably clarify exactly what's going on there (only just checked the link). It's normal gnome with a custom compiz config that embeds a gnome terminal with a transparent background into the desktop. In the terminal window is a byobu session with Vi and and an ssh to my webserver that also hosts another screen session so I can stay permanently logged into IRC. There's only two actual windows in that terminal the splits in the text editor are all one instance of Vi with some split buffers.

Also, there's no php there, I hate php with a passion because it's evil.

---

### Post by Scarcer on 2010-11-02
Lol, I find that pretty funny. Yeah, I dig your setup. I'll see if I can find a way to pull something similar off. Would come in handy.

---

### Post by slackthumbz on 2010-11-02
Well the embedded terminal is pretty easy to set up in gnome, you'll need to install compizconfig manager to fine tune the window rules though.

1.```
sudo apt-get install compizconfig-settings-manager
```
2.Open up gnome-terminal and create a new profile called embedded, in the profile settings disable the scrollbar and the menubar and under 'Title and Command' set the initial Title as embedded and set it to retain its initial title.
3.Open up compiz config settings manager (should be in System->Preferences) and enable the Window Rules plugin, under the Window Rules settings add the line ```
title=embedded
``` to the following sections:
  Skip taskbar
  Skip pager
  Below
  Sticky
  Maximized
  Non-movable windows
  Non-minimisable windows
4.Go to the Window Decoration plugin settings (still in compiz config) and 'Decoration Windows' to ```
(any) & !(title=embedded)
```

That should be everything you need. I also have in my startup applications a hook that fires off the command ```
gnome-terminal --window-with-profile=embedded
``` so that it fires up at the beginning of every session.

Hope that helps :)

---

### Post by dr_duck on 2010-11-05
So what language is it?

---

### Post by KeLa on 2010-11-05
[slackthumbz]("http://ubuntuforums.org/member.php?u=223159") Do you know what's wrong because with your instructions i can't make this
embedded terminal work on 10.04 but it works great on 10.10

On 10.04 it always opens terminal in normal size window not maximized and with frames.

---

### Post by slackthumbz on 2010-11-05
> **KeLa said:**
> [slackthumbz]("http://ubuntuforums.org/member.php?u=223159") Do you know what's wrong because with your instructions i can't make this
embedded terminal work on 10.04 but it works great on 10.10

On 10.04 it always opens terminal in normal size window not maximized and with frames.

That's odd, I use exactly the same method in 10.10 as I did in 10.04, as long as all the window rules are set up right and you set the terminal profile up right then it should work.

Below are some screenshots of my config, I hope that helps.

---

### Post by slackthumbz on 2010-11-05
> **dr_duck said:**
> So what language is it?

on the left is CSS, the top right is a template using Template Toolkit syntax and the bottom right is perl.

---

