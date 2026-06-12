---
title: "Gentoo user for 8 years, love Ubuntu! But have some questions"
date: 2008-02-12
forum: Testimonials &amp; Experiences
---

### Post by Rugger1 on 2008-02-12
I've used Gentoo for over 8 years.  Originally I picked Gentoo as my Linux distro because I was fairly new to Linux and wanted to learn all I could about it so one day I could get a job in it.  Now that has all paid off and I do have a job where I administer UNIX and Linux. 

I also have multiple computers at home dual booted with Windows and Linux and I am always upgrading them and reloading O/S's fairly often.  So I thought maybe I would find something that was quicker to install but still gave me the power to do everything from a command shell if I so wished and run World of Warcraft in wine good.  Gentoo wasn't bad on the running of wine, and it was easy to keep updated once you had a fully operational system.  However they are having political issues right now and some argue Gentoo is dead. We use Fedora at work, so I tried it.  Not bad, just seemed sluggish.  SuSE was the same way.  Then I tried Ubuntu and WOW! I absolutely love it! Quick install, and with a few keystrokes and apt-get commands I have wine, all my music codec’s, video codec’s and so forth installed an running.  On top of that, World of Warcraft just runs awesome in wine.  I couldn't be happier!

But I do have a question.  It seems the shell or VIM in Ubuntu has a keyboard difference I'm not used to.  Of course I am used to KDE and Konsole as my shell.  Everything seems to work like expected until when I'm editing a file with VIM and I go into edit mode.  All of a sudden my arrow keys start throwing letters when I'm pushing them instead of moving around.  Of course they work fine when I'm not in edit mode.  Any ideas? I've made sure my keyboard was set up correctly.

---

### Post by LaRoza on 2008-02-12
> **Rugger1 said:**
> 
But I do have a question.  It seems the shell or VIM in Ubuntu has a keyboard difference I'm not used to.  Of course I am used to KDE and Konsole as my shell.  Everything seems to work like expected until when I'm editing a file with VIM and I go into edit mode.  All of a sudden my arrow keys start throwing letters when I'm pushing them instead of moving around.  Of course they work fine when I'm not in edit mode.  Any ideas? I've made sure my keyboard was set up correctly.

For vim, 

```

sudo aptitude install vim-full

```

vim-tiny is installed, which lacks a lot. That might fix it.

You can install KDE and Konsole easily, 

```

sudo aptitude install kde-core

```

When you log on, you can use KDE by selecting it under "Session".

---

### Post by Rugger1 on 2008-02-12
Awesome that fixed it! Thanks for the info.

Actully I don't really mind Gnome.  It does seem to be a bit snappier then KDE.  Plus it reminds my wife of the apple computers she uses at work so she doesn't mind either.  KDE 4 is pretty nice and once they get some issues worked out (like being able to adjust the size of the start menu and task bar) I might switch back.  But for now I'm perfectly happy with Gnome.

---

