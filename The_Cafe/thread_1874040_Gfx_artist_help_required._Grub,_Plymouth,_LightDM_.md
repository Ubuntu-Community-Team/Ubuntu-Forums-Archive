---
title: "Gfx artist help required. Grub, Plymouth, LightDM theme."
date: 2011-11-02
forum: The Cafe
---

### Post by mips on 2011-11-02
I would like to setup a simple theme. 

For grub it would be grey on a black background.
For plymouth I would like a grey background with a lighter spinner or ghosted progress bar.
For lightdm I would love to carry the background over from the plymouth one. All I want to see is a field for my password or passwd&username.
For logout I would like to have the same.

What is the max resolution I can share between all these? (I have a primary 1920x1080 & secondary 1680x1050 displays)

I would like to match the colours from grub throughout. I don't want any distro branding.

Can someone make this up for me and then I could just tweak the level of gray I prefer. Text on this would be lighter than the background or even black.

---

### Post by Legendary_Bibo on 2011-11-02
> **mips said:**
> I would like to setup a simple theme. 

For grub it would be grey on a black background.
For plymouth I would like a grey background with a lighter spinner or ghosted progress bar.
For lightdm I would love to carry the background over from the plymouth one. All I want to see is a field for my password or passwd&username.
For logout I would like to have the same.

What is the max resolution I can share between all these? (I have a primary 1920x1080 & secondary 1680x1050 displays)

I would like to match the colours from grub throughout. I don't want any distro branding.

Can someone make this up for me and then I could just tweak the level of gray I prefer. Text on this would be lighter than the background or even black.

Grub uses VESA or something, and only works at 4:3 ratio resolutions. Also, considering how there's less than 10 themes for grub I don't know if someone would make you one (but they're not that hard to make). Unless you just want to change the color/wallpaper of grub then it's not that hard.

---

### Post by cariboo on 2011-11-02
It's also very easy to change the lightdm background, just add the full path to the background you want to use in /etc/lightdm/unity-greeter.conf. I use the same image for lightdm as I do for my desktop. I created a screenshot of lightdm, using the following command:

```
lightdm --test-mode
```

---

### Post by Elfy on 2011-11-02
> **cariboo907 said:**
> It's also very easy to change the lightdm background, just add the full path to the background you want to use in /etc/lightdm/unity-greeter.conf. I use the same image for lightdm as I do for my desktop. I created a screenshot of lightdm, using the following command:

```
lightdm --test-mode
```
Just fyi - in Xubuntu the file to edit is
/etc/lightdm/lightdm-gtk-greeter.conf

---

