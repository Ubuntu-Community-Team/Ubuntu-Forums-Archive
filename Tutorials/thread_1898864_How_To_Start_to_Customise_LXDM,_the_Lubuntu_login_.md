---
title: "How To: Start to Customise LXDM, the Lubuntu login screen"
date: 2011-12-22
forum: Tutorials
---

### Post by MG&amp;TL on 2011-12-22
[SIZE="4"]Customising the Lubuntu Login Screen[/SIZE]

*Aim of guide:*

While Lubuntu's login screen is very nice by default, some people like to tweak things. This guide gets you started on doing just that, using configuration files. 


*Skill level*

While a reasonable level of experience is necessary to understand what is going on, I hope I have explained things in a way that will be accessible to all.


*Disclaimer*

As with all guides that involve configuration files, if you are not totally confident, then at least ensure you have backed up your important data before starting. While this guide is harmless if followed correctly (I hope!), it does involve root access, which carries its own dangers. See [RootSudo]("https://help.ubuntu.com/community/RootSudo") for more details. *Let's get started!*


[SIZE="3"]Change the Background[/SIZE]

The first and most obvious thing to do is change the background image of the login screen. Open a terminal:

*LXMenu -> Accessories -> LXTerminal*

and carefully type the following:

```
gksu leafpad /etc/lxdm/default.conf
```

then type your password. See [Using the Terminal]("https://help.ubuntu.com/community/UsingTheTerminal") for more details, and how to copy and paste.

A leafpad window will appear, the contents looking a bit like this:

```

[base]
## uncomment and set autologin username to enable autologin
autologin=michael

## uncomment and set timeout to enable timeout autologin,
## the value should >=5
# timeout=10

## default session or desktop used when no systemwide config
session=/usr/bin/startlubuntu

## uncomment and set to set numlock on your keyboard
# numlock=0

## set this if you don't want to put xauth file at ~/.Xauthority
# xauth_path=/tmp

## greeter used to welcome the user
greeter=/usr/lib/lxdm/lxdm-greeter-gtk

[server]
## arg used to start xserver, not fully function
# arg=/usr/bin/X -background vt1

[display]
## gtk theme used by greeter
gtk_theme=Clearlooks

## background of the greeter
bg=/usr/share/lubuntu/wallpapers/lubuntu-default-wallpaper.png

## if show bottom pane
bottom_pane=1

## if show language select control
lang=1

## if show keyboard layout select control
keyboard=0

## the theme of greeter
theme=Lubuntu

[input]

[userlist]
## if disable the user list control at greeter
disable=0

## whitelist user
white=

## blacklist user
black=


```

To change the background, you need to know the absolute path of the desired background. If you don't know this, copy the picture to your Pictures folder, and call it "background.png"-exactly, no upper case, no typos. If it's a .jpg, call it "background.jpg" instead, then follow the "easy instructions" below.

*easy instructions*

in your leafpad window, change 

```

bg=/usr/share/lubuntu/wallpapers/lubuntu-default-wallpaper.png


```

to 

```
bg=/home/<your username>/Pictures/background.png
```

or

```
bg=/home/<your username>/Pictures/background.jpg
```

if it's a JPEG image.


*Advanced instructions*

If you *do* know the absolute path of your picture, simply enter it after "bg="

like this:

```
bg=/usr/share/lubuntu/wallpapers/1110-natty-bug.png
```

now save the file and log out to admire your changed background. :D



[SIZE="3"]Remove the lower panel[/SIZE]

If you don't like the bottom panel (the white bit at the bottom, not the menus), you can easily remove it.

```
gksu leafpad /etc/lxdm/default.conf
```

and change:

```
bottom_pane=1
```

to

```
bottom_pane=0
```

then save the file, and logout to see the removed whiteness.


[SIZE="3"]Remove excessive language options[/SIZE]

Great as the language support is in Ubuntu, if you are a mono-linguistic household/user, there is not much point in having the language options. Therefore, we can disable those, too. :D

Change:

```
lang=1
```

to

```
lang=0
```

and save.

Logout, and there should not be a language option.


[SIZE="3"]Advanced users only: kill extraneous programs on logout[/SIZE]

*Background:*

A peculiar quirk of the LXDM Display Manager is that it doesn't kill users' programs when they log out. This can be disastrous for some programs (sylpheed needs killing, for example), and while conky may look good on your desktop, it certainly doesn't look good plastered over LXDM. So for advanced users only (killing processes is never a good idea), here's how to kill user programs on logout.

```
gksu leafpad /etc/lxdm/PostLogout
```

and add this line (thanks to the Arch wiki):

```
killall --user $USER -TERM
```

then save.

Logging out will now kill your programs as you leave.


Hopefully this guide will have given you some ideas for what else you can change; it is possible to set entire themes for LXDM, and I look forward to seeing a few of yours. :)

[SIZE="1"]*Please leave comments at the bottom, particularly if I've got something wrong. (still learning!)*[/SIZE]

---

