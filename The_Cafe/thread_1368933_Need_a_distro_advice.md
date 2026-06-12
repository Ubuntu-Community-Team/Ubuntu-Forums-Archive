---
title: "Need a distro advice"
date: 2009-12-31
forum: The Cafe
---

### Post by ~sHyLoCk~ on 2009-12-31
Not for me. I use slack  and openBSD. My niece wants to checkout Linux in her laptop. She has only 20gigs of space available, rest is windows and other ntfs drives where she keeps her school data. I thought about Arch and Slack but I think they will take up a huge space by default install. Arch will not take up big space but eventually as ```
pacman -Syu == space--
```
Anyway, as ubuntu karmic has been causing problems all around, I need an advice on a distro where space won't keep on decreasing due to updates, or to phrase correctly , I need a distro which doesn't update often. If however the distro updates, cleaning cache is not an option, since this is her first time using *nix, she will break it and re-install it a lot. So saved packages means no re-downloads. I'm thinking openSUSE, any thoughts?

---

### Post by handy on 2009-12-31
I know, you don't want to do it this way, but I couldn't resist. ;)

**pacman -Sc** To clear the */var/cache/pacman/pkg/* of all packages except the currently installed packages. Just do it every now & then when confident no problems have come from upstream.

These installation packages have been so helpful to me from time to time when I stuff up, as I can just go into the cache & reinstall whatever package(s) necessary; I found this to be particularly useful for the kernel, more than once. :)

pacman -U /your way to the downgrade/

***[Edit:]** **dotpac** is a great (ncurses) script that handles the finding, viewing, editing & deleting of .pacnew & .pacsave files found inside of /etc & /boot. I wish I had of found it years ago. It can be downloaded from AUR.*

***[Edit2:]** If you can't use Arch, you could go with Mint-Xfce, & do the light install, uses less space. I use version 6, on No.2. box & it is great, easiest install ever, it's surprisingly quick, & not bogged down by too much Ubuntu under the hood (I still don't know how they managed that?)*

---

### Post by ~sHyLoCk~ on 2009-12-31
Hmm I just thought of a crazy idea, what about creating a separate /pkg partition? Then edit pacman.conf to save the cache in that partition? She can use her external HDD as /pkg. Only thing though she has to keep it attached every-time she wants to update system.
Anyway, I think it's better to just use a distro that doesn't update a lot, just firefox,pidgin,etc.

Btw, thanks handy. :)

EDIT: Well I used pacdiffviewer, any different than that?

---

### Post by handy on 2009-12-31
I think [**_dotpac_**]("http://wiki.archlinux.org/index.php/Dotpac") is about as simple as it could get, suits me perfectly. :)

---

### Post by ~sHyLoCk~ on 2009-12-31
Hey, why does the forum thread say:

> Bad request. The link you followed is incorrect or outdated.

Does it say the same for you? :confused:

---

### Post by handy on 2009-12-31
Nope, works for me, try it this way:

[http://wiki.archlinux.org/index.php/Dotpac](http://wiki.archlinux.org/index.php/Dotpac)

---

### Post by ~sHyLoCk~ on 2009-12-31
The wiki link works but the Frum thread link about dotpac doesn't. Wanted to check out the comments and discussions. 
Anyway, I think Mint-xfce is a good option. Thanks for that, I had almost forgotten about Mint, I loved it. :D

---

### Post by Hallvor on 2009-12-31
> **~sHyLoCk~ said:**
> Not for me. I use slack  and openBSD. My niece wants to checkout Linux in her laptop. She has only 20gigs of space available, rest is windows and other ntfs drives where she keeps her school data. I thought about Arch and Slack but I think they will take up a huge space by default install. Arch will not take up big space but eventually as ```
pacman -Syu == space--
```
Anyway, as ubuntu karmic has been causing problems all around, I need an advice on a distro where space won't keep on decreasing due to updates, or to phrase correctly , I need a distro which doesn't update often. If however the distro updates, cleaning cache is not an option, since this is her first time using *nix, she will break it and re-install it a lot. So saved packages means no re-downloads. I'm thinking openSUSE, any thoughts?

Debian + XFCE? Few updates, light, very solid. But probably not what she wants to run if she breaks it every other day. You could set it up with multimedia and make a backup with partimage or similar to restore it the way you want if she breaks it.

---

### Post by ~sHyLoCk~ on 2009-12-31
> **Hallvor said:**
> Debian + XFCE? Few updates, light, very solid. But probably not what she wants to run if she breaks it every other day. You could set it up with multimedia and make a backup with partimage or similar to restore it the way you want if she breaks it.

Good idea. Debian will be lighter and will have lesser programs than Mint , if I use netInst. Thanks. :)

---

