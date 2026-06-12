---
title: "BSG - Beyond the Red Line Demo on Ubuntu"
date: 2007-09-12
forum: Ubuntu Gamers Arena
---

### Post by leftcase on 2007-09-12
I wrote this for [my own website]("http://www.justuber.com/blog/2007/09/06/bsg-beyond-the-red-line-on-ubuntu/"), but thought it might help a couple of people out here too.

Battlestar Galactica: Beyond the Red Line is a 3D space combat simulation which takes place inside the Battlestar Galactica universe. The game is free, and the good folks over at Game Warden have also released a Linux client for it. Here&#8217;s how to get it up and running on Ubuntu.

1> [Download the game]("http://www.game-warden.com/bsg")
2> Install GTK 1.2 Libraries &#8220;sudo apt-get install libgtk1.2&#8243;
3> Run &#8220;./BtRLDemoInstaller.run&#8221;

[IMG]http://www.justuber.com/blog/wp-content/uploads/2007/09/screen09.jpg[/IMG]

Helpful hints

Make sure that you tick the &#8216;mouse&#8217; tickbox in the options menu, the game is setup as default to use a joystick. You&#8217;ll have to repeat this for both single and multiplayer.

If you want to change the screen resolution, edit the file fs2_open.ini which you&#8217;ll find in a hidden folder in your home directory called .btrl_demo

Visit the BSG site on GameWarden.com to get the game. Currently only a bittorent file is available. If that&#8217;s no good to you, send an email to chris at justuber put-a-dot-here com and I&#8217;ll send you a link to download it from my own server.

---

### Post by hikaricore on 2007-09-12
Been posted a number of times, but thanks for the quick guide.  ^_^

I've also posted about BtRL on UGA several times but it's been burried in the old news.

---

### Post by Perfect Storm on 2007-09-13
Aye, we have a guide: [http://gaming.gwos.org/doku.php/guides:beyond_the_red_line](http://gaming.gwos.org/doku.php/guides:beyond_the_red_line)

---

### Post by leftcase on 2007-09-14
> **Artificial Intelligence said:**
> Aye, we have a guide: [http://gaming.gwos.org/doku.php/guides:beyond_the_red_line](http://gaming.gwos.org/doku.php/guides:beyond_the_red_line)

Hey AI,

Do you think you could add the bits I put about changing screen resolution and changing to mouse into your guide. I know they both confused me a bit when I first got the game.

Cheers

Chris

---

### Post by Perfect Storm on 2007-09-14
Will do.

---

### Post by SteveMcQwark on 2008-10-17
I'm having trouble. The mouse doesn't work (it shows a top-left resizer and won't click) and the patch doesn't detect if properly.

---

### Post by Perfect Storm on 2008-10-18
Try disable compiz;

```
metacity --replace
```
Then run BSG again.

Does it help?

---

### Post by SteveMcQwark on 2008-10-18
No, I still an unusable resizer. It also fails to save the pilot file. I tried to use the patch, but its looking for a file that doesn't seem to have been installed: /home/steven/btrl_demo/installer/installer_error.log.txt and so tells me my installer is out of date, which it also does if I point it to some other random folder(though I just downloaded it).

---

