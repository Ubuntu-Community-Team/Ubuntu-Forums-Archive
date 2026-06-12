---
title: "Change icon in upper left hand corner"
date: 2009-10-01
forum: Ubuntu Moblin Remix
---

### Post by nevarDeath on 2009-10-01
I'm not real big on the ubuntu logo and would like to change the ubuntu logo in the upper left hand corner to a penguin. I'm using ubuntu netbook remix. I believe the graphic file is

/usr/share/icons/Human/48x48/places/start-here.png

I can't rename it in Nautilus because I'm not the owner. I can't rename it in terminal either. I get this message when I do:
```

daniel@PC:/usr/share/icons/Human/48x48/places$ sudo rename start-here.png start-here.old
[sudo] password for daniel: 
Bareword "start" not allowed while "strict subs" in use at (eval 1) line 1.
Bareword "here" not allowed while "strict subs" in use at (eval 1) line 1.
Bareword "png" not allowed while "strict subs" in use at (eval 1) line 1.

```I'm wanting to rename it, then copy the replacement picture file I already have. I assume I get this message since the overlay is running. Does anyone know how to change that icon or what the above messages mean?

---

### Post by nevarDeath on 2009-10-07
Thought I'd bump this see if anyone has an idea. I've not found anything new to solve it though

---

### Post by wojox on 2009-10-07
I don't think you can if you don't have the permissions. Try:

```
sudo mv start-here.png start-here.old
```

---

### Post by jeremyswalker on 2009-10-07
Press 'Alt + F2'.
Enter in 'gconf-editor' and press enter.

Go to 'apps -> panel -> objects' and select the menu_bar.
On the right of the window, check the box that says 'use_custom_icon'. Then, right click the entry that says 'custom_icon'. Select 'Edit Key' and enter the path to your preferred icon.

---

### Post by cariboo on 2009-10-08
Try sudo -i, this will drop you to a root shell, you should then be able to do anything you need.

---

### Post by nevarDeath on 2009-10-08
> **wojox said:**
> I don't think you can if you don't have the permissions. Try:
 
 ```
sudo mv start-here.png start-here.old
```
 
 Thank you, this allowed the file to be renamed. I moved my file into place and nothing changed lol. your advice did work for that aspect of it though thank you!

> **cariboo907 said:**
> Try sudo -i, this will drop you to a root shell, you should then be able to do anything you need.

I didn't try this as the above command worked, but I'm always glad to learn something new like that, thanks!

> **jeremyswalker said:**
> Press 'Alt + F2'.
Enter in 'gconf-editor' and press enter.

Go to 'apps -> panel -> objects' and select the menu_bar.
On the right of the window, check the box that says 'use_custom_icon'. Then, right click the entry that says 'custom_icon'. Select 'Edit Key' and enter the path to your preferred icon.

This did it! Thanks so much!! Lots easier than I thought it would be!:guitar: One minor thing is that it was under 'apps -> panel -> default_setup -> objects' but still you got me to where I needed to go. Thanks again!

---

### Post by jeremyswalker on 2009-10-08
Great! I'm glad you figured it out. Yeah, I realized after I posted that you said you were running the netbook remix, which would change the object in the settings. I figured you could figure it out from there, though. Congrats!

---

### Post by letodude on 2011-01-12
I am bumping the thread as I'm running into a similar problem. 

I went through all the steps (gconf-editor....) and my new icon is in place in /usr/share/icons/Humanity/places/64/start-here2.svg. 
In gconf I also changed the object_type key to drawer-object, as it says it has to be so for the custom_icon key to be relevant, but I'm seeing no light......help?

Ubuntu 10.04 here, and I downloaded the icon from an image on the internet, it was a png and i renamed it as svg, could that be the problem??
Also it's pretty big, i put it in the 64 folder as the size matches them 64 icons. (I tried to put it in other sizes folders but nothing worked).

Not that it's all important and everything, but I decided I'd change the icon, and I won't get to sleep until it worked now!

---

### Post by slw0000 on 2011-02-10
Penitence is something that enervates our spirit, causing a greater loss than loss itself and making a bigger mistake than mistake itself, so never regret.

---

### Post by Make Space for Science on 2011-02-23
i tried said methods on 10.10 but no joy, no biggy i guess. :)

---

