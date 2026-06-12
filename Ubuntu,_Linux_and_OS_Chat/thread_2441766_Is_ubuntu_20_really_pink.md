---
title: "Is ubuntu 20 really pink?"
date: 2020-04-26
forum: Ubuntu, Linux and OS Chat
---

### Post by WHK on 2020-04-26
It is one thing to use colors like violet or blue to give a retro and modern style and another very different thing is to have abused the pale pink color.

[https://i.ibb.co/MpHwZJH/20200426-172350.jpg](https://i.ibb.co/MpHwZJH/20200426-172350.jpg)

[https://i.ibb.co/7GN0Q8m/Captura-de-pantalla-de-2020-04-26-17-30-04.png](https://i.ibb.co/7GN0Q8m/Captura-de-pantalla-de-2020-04-26-17-30-04.png)

[https://i.ibb.co/X787gLh/Captura-de-pantalla-de-2020-04-26-17-31-08.png](https://i.ibb.co/X787gLh/Captura-de-pantalla-de-2020-04-26-17-31-08.png)

The access screen is pink, the contrast of controls such as the radios and selectors are pink, the icons of images and documents are pale pink, i think the new style of ubuntu 20 is not bad, but I think that the colors reflect the tastes of a person or a group of people that we are not all, it is as if I made a design loaded with yellow, maybe not everyone likes it.

Is there a way to change the color of the login screen? I am really ashamed to authenticate myself in ubuntu, when I enter it looks all pink (only the white flowers are missing) and when I enter it it is seen in a dark theme with green and orange tones.

If people like pink, that's fine, but I have my personal tastes and I don't like pink. Why do they not allow this type of thing to be changed? For example, in Windows you can use a background image or change the color palette of the system windows in general, in Mac it is not necessary because they are cleaner, they use white and grays to be more generic with the tastes, but ubuntu abused too much with the colors in this version, not all of us have the same tastes.

In ubuntu mate the green is very strong and in manjaro the colors are a bit more sober, but I like the combination of colors and style of deepin and chrome os.

Can someone tell me how to change these aberrant system colors without causing problems when wanting to get updates?

---

### Post by coffeecat on 2020-04-26
The Art & Design sub-forum where you posted is a bit of a neglected backwater. I've moved this to ***Ubuntu, Linux & OS Chat*** where you are more likely to get responses.

> **WHK said:**
> Is there a way to change the color of the login screen? I am really ashamed to authenticate myself in ubuntu, when I enter it looks all pink

Pink? Perhaps you need to adjust your monitor. On my system the login screen for 20.04 is the same purple that Ubuntu has used for years.

**Edit:** while I was posting you edited your post to include large off-site images. Please don't do that. It is inconsiderate of those who use mobile devices to browse the forum. If you wish to include images, please use the paper-clip icon to upload them to the forum. That way you get clickable thumbnails. Ive reduced your images to hyperlinks.

By the way, the colour you are complaining about in your images looks purple to me - on my monitor.

---

### Post by oarion7 on 2020-04-26
Yes, I've been working with color hex codes a lot this week and this color is clearly achieved from equal or near equal data in the red and blue fields. It's purple by definition.

I've been using Mint for about 2 years now but I've been an Ubuntu user about ten years before that and that purple has been around for a *while*. I always disabled the splash screen because I like to see boot info. I don't remember the lock screen ever bothering me, of course that can be replaced as well.

---

### Post by CatKiller on 2020-04-26
The colour Ubuntu has used, since they stopped using the earth-tones palette about a decade ago, is [light aubergine]("https://design.ubuntu.com/brand/colour-palette/"): HEX #77216F (along with the orange, of course). I agree with coffeecat that if that looks light pink to you then your monitor is not displaying colours accurately.

For the other part, there are a bunch of login screen themes for a bunch of display managers. It's easy to pick a non-default one.

---

### Post by Claus7 on 2020-04-26
Hello,

> **WHK said:**
> ...when I enter it looks all pink (only the white flowers are missing) and when I enter it it is seen in a dark theme with green and orange tones.
...

I have to admit that reading this line of yours is still placing a smile on my face.

Now, concerning your question, I guess that this is what you are looking for:
[https://askubuntu.com/questions/1227070/how-to-change-login-screen-theme-or-background-in-20-04](https://askubuntu.com/questions/1227070/how-to-change-login-screen-theme-or-background-in-20-04)

and especially this one:
some of the content:

#lockDialogGroup {
  background-color: #4f194c; }

so, if your change the color hex to your liking, it might change. I haven't tested it though.

Regards!

---

### Post by WHK on 2020-04-26
You really need to know how to program and package resources to change a simple background color.

> go to this for complete flexibility Workaround 1. But risk of breaking the system if wrongly edited the contents.

Ok xD, i don't know why something that should be simple like changing the background color of the login screen can end up ruining the entire operating system, but that's fine. To extract the css and change the rgb value of the color sounds easy, I already have, but to pack and apply it sounds quite complex xD, I think it will take a little longer.

---

### Post by WHK on 2020-04-27
Ok, reading tutorials, reading about how to extract, list resources, how to compile, how the update-alternative works for the compiled theme resource, directories, etc, from archlinux wiki (have a best documentation, more than ubuntu), and i made a script to make it easier for the template developer to extract and publish themes, it took longer to read than to do the script, but here it is:

[https://github.com/WHK102/gnome-shell-3-helper](https://github.com/WHK102/gnome-shell-3-helper)

I still do not understand why the gresource command can only extract one resource at a time, it is as if from the unzip command I could extract from a single file, it is crazy, I do not know who can think of these barbarities.

Ubuntu should have an application with official support that is capable of navigating the themes published in gnomelook and these in turn deliver the information through rest api services, so that users can install modifications with a single click, or integrate a Basic panel for modifying custom themes, something like a custom sandbox in real time.

In terms of design, use of modern technology and end-user satisfaction, it lags far behind. For now I had to switch to the Faenza icon theme with Adapta for Gtk. Tomorrow I will try to unify everything in a single theme.

Still, thanks for the help.

---

