---
title: "Simple little Ubuntu tricks others may not know about"
date: 2009-09-18
forum: The Cafe
---

### Post by snakeman21 on 2009-09-18
So I'm always stumbling across little tricks that are included in the OS that I hadn't previously heard of.  One of the first ones was holding ALT to drag windows, which I discovered after about a month of using Linux.  Just the other day, I accidentally found out that I could scroll by dragging two fingers on the touchpad.  This was so much more convenient than using the right edge that I immediately disabled the little right-side scroll setting and have been using two fingers since then.  

Everyone, post helpful little things like this, so maybe some of us could learn things like this to make our computing a little more convenient!

---

### Post by coldReactive on 2009-09-18
ALT+Click to drag is actually not good for GIMP, as one of its tools uses that shortcut too. (So does Inkscape)

Had a bug for it on compiz, thinking it was a compiz issue: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/427608](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/427608)

---

### Post by HappinessNow on 2009-09-18
Ctrl + Alt + F1 when you need to restart x when everything appears to be stuck (never needed in Ubuntu) :P

---

### Post by tjwoosta on 2009-09-18
You can add aliases to the end of your ~/.bashrc to make commands simpler
(remember to reboot after adding aliases to make changes take effect)

example 
```

alias update='sudo apt-get update && sudo apt-get upgrade'

```

with that one you can update from command line with a single word
```
update
```

---

### Post by snakeman21 on 2009-09-18
> **tjwoosta said:**
> You can add aliases to the end of your ~/.bashrc to make commands simpler
(remember to reboot after adding aliases to make changes take effect)

example 
```

alias update='sudo apt-get update && sudo apt-get upgrade'

```

with that one you can update from command line with a single word
```
update
```

Ooh, that's one I didn't know... Cool!  I'll have to set a couple of aliases up for my wife, she's no good at remembering commands.  This would make things a lot easier for her!

---

### Post by slakkie on 2009-09-18
> **tjwoosta said:**
> You can add aliases to the end of your ~/.bashrc to make commands simpler
(remember to reboot after adding aliases to make changes take effect)

example 
```

alias update='sudo apt-get update && sudo apt-get upgrade'

```

with that one you can update from command line with a single word
```
update
```

A reboot? You just need to run a new shell for the changes. Or just simply sourcing the file will do the same. Rebooting for such minor things is not needed. If you start a new terminal session the changes are in effect. 

In addition to your aliasses, I've created some time ago these function to make your upgrading your system a bit quicker (less typing):

```

# Only update if we haven't updated for an hour, giving an argument will force the update. 
apt_update () {
        local date_stamp=$(stat -c "%Z" /var/cache/apt/pkgcache.bin)
        local now=$(date "+%s")
        now=$((now - 3600))
        [ $date_stamp -lt $now ] || [ -n "$1" ] && sudo aptitude update && sudo apt-file update
}

# Purge packages and clean the package cache
purge_pkg () {
        sudo aptitude purge $(dpkg -l | grep '^rc' | awk '{print $2}')
        sudo aptitude clean
}

# Regular upgrade, no dist-upgrade or anything, can be run after this if you want.
safe_upgrade () {
        apt_update
        sudo aptitude safe-upgrade && purge_pkg
}

```

---

### Post by MaxIBoy on 2009-09-18
You do **not** need to restart to apply aliases. Just run the command "source ~/.bashrc" and it will be applied.

---

### Post by bruno9779 on 2009-09-18
> **&#20170 said:**
> Ctrl + Alt + F1 when you need to restart x when everything appears to be stuck (never needed in Ubuntu) :P

you have 6 of these sessions availabe, from F1 to F6
Ctrl + Alt + F7 will bring you back to the desktop environement

---

### Post by ubuntu27 on 2009-09-18
> **tjwoosta said:**
> You can add aliases to the end of your ~/.bashrc to make commands simpler
(remember to reboot after adding aliases to make changes take effect)

example 
```

alias update='sudo apt-get update && sudo apt-get upgrade'

```

with that one you can update from command line with a single word
```
update
```

I like this. I never knew of this. I will take a note of it.

Thank you tjwoosta

---

### Post by kerry_s on 2009-09-18
> alias update='sudo apt-get update && sudo apt-get upgrade'

i use a much simpler alias's.

```
alias !='sudo'
alias u='sudo apt-get update;sudo apt-get upgrade'
alias s='apt-cache search'
alias i='sudo apt-get install --no-install-recommends'
alias r='sudo apt-get purge'
alias ?='dpkg -l | grep'
alias c='sudo apt-get autoremove;sudo apt-get clean'
alias ch='clear;rm -f ~/.bash_history;history -c'
```

> Ctrl + Alt + F1 when you need to restart x when everything appears to be stuck (never needed in Ubuntu)  

:lolflag: that does not restart x, that's simply switching tty.

---

### Post by bodyharvester on 2009-09-18
i never knew about the alias thing, this is gonna be so useful

---

### Post by keplerspeed on 2009-09-18
> **kerry_s said:**
> i use a much simpler alias's.

```
alias !='sudo'
alias u='sudo apt-get update;sudo apt-get upgrade'
alias s='apt-cache search'
alias i='sudo apt-get install --no-install-recommends'
alias r='sudo apt-get purge'
alias ?='dpkg -l | grep'
alias c='sudo apt-get autoremove;sudo apt-get clean'
alias ch='clear;rm -f ~/.bash_history;history -c'
```


Ha, that would mean to run the previous command as root:
```

! !!

```

---

### Post by t0p on 2009-09-18
Just thought I'd mention: despite the title of this thread, most/all of the tricks mentioned are *not* "Ubuntu tricks".  Multiple consoles via Ctrl-Alt-F1-6 is a *nix thing.  Aliases is a bash thing (and other shells too).  Two-finger scroll on the touchpad is probably a hardware thing.  I don't know for sure, but I think Alt+left click to drag windows is a Gnome thing.

This is not to deny the usefulness of a thread like this.  I just wanted to clarify these details.  Most/all of these tricks will apply to other Linux distros too, plus *BSD and Unix.

---

### Post by bodyharvester on 2009-09-18
> **t0p said:**
> Just thought I'd mention: despite the title of this thread, most/all of the tricks mentioned are *not* "Ubuntu tricks".  Multiple consoles via Ctrl-Alt-F1-6 is a *nix thing.  Aliases is a bash thing (and other shells too).  Two-finger scroll on the touchpad is probably a hardware thing.  I don't know for sure, but I think Alt+left click to drag windows is a Gnome thing.

This is not to deny the usefulness of a thread like this.  I just wanted to clarify these details.  Most/all of these tricks will apply to other Linux distros too, plus *BSD and Unix.

good to know, i have a recovery puppy

---

### Post by kerry_s on 2009-09-18
> Ha, that would mean to run the previous command as root:

:lolflag: i usually just use the up key, but yeap, thats right.

---

### Post by wojox on 2009-09-18
Okay, install packages on a new install/reinstall if you have home on a separate partition.

Copy all current packages to a file in you home directory:

```
$ sudo dpkg --get-selections > myPackages
```

Reinstall the packages after installation:

```
$ sudo dpkg --set-selections < myPackages && sudo apt-get dselect-upgrade
```

The End. :p

---

### Post by 3rdalbum on 2009-09-18
You can drag launchers from the Applications menu to the panel or the desktop, and it will copy the launcher to the new location.

Install the "padevchooser" package, and make sure its program runs at login, to get control over what programs use what sound devices and to give each program its own individual volume control. There is one side-effect: You may become a Pulseaudio fan.

Not an Ubuntu trick, but you can buy little rechargable AA batteries where the positive terminal comes off and underneath is a USB plug. You can plug it into any computer or games console to charge it. Awesomeness! You can find out where to buy them at [www.usbcell.com](www.usbcell.com).

---

### Post by Bölvaður on 2009-09-18
aptlinks plugin for firefox (preinstlled)


write [apt:crack-attack](apt:crack-attack)  into the url

---

### Post by scragar on 2009-09-18
Install the imagemagick addon for nautilus```
sudo apt-get install nautilus-image-converter
killall nautilus
```so you can resize huge numbers of images in just a few clicks.

Alt+F2 launches a run box, try ```
free the fish
``` or```
gegls from outer space
``` :p

Also try launching a terminal and running```
apt-get moo
```Doesn't work? Try in verbose mode```
apt-get -v moo
```Or step up the verbose mode```
apt-get -vv moo
```Repeat as needed for lulz :p

---

### Post by marchwarden on 2009-09-18
> **tjwoosta said:**
> You can add aliases to the end of your ~/.bashrc to make commands simpler
(remember to reboot after adding aliases to make changes take effect)

example 
```

alias update='sudo apt-get update && sudo apt-get upgrade'

```

with that one you can update from command line with a single word
```
update
```

> **wojox said:**
> Okay, install packages on a new install/reinstall if you have home on a separate partition.

Copy all current packages to a file in you home directory:

```
$ sudo dpkg --get-selections > myPackages
```

Reinstall the packages after installation:

```
$ sudo dpkg --set-selections < myPackages && sudo apt-get dselect-upgrade
```

The End. :p

Some sweet tips there, I'm looking forward to trying the latter when Karmic is released. :-D

---

### Post by infinitejones on 2009-09-18
Everyone got so caught up talking about aliases that nobody has mentioned the TWO-FINGER SCROLLING thing!! It's brilliant!

Or was I the only one who didn't know about it....?

---

### Post by scragar on 2009-09-18
> **infinitejones said:**
> Everyone got so caught up talking about aliases that nobody has mentioned the TWO-FINGER SCROLLING thing!! It's brilliant!

Or was I the only one who didn't know about it....?

Or they use a mouse so it doesn't work.
Or they don't have a trackpad that supports it.

Personally I find the highlight-middle click alternative to copy/paste sounds impressive.

---

### Post by Bölvaður on 2009-09-18
> **scragar said:**
> 
Personally I find the highlight-middle click alternative to copy/paste sounds impressive.

yes it is quite good. Specially if you need to copy multiple texts

lets say if you need to copy a user name and password

then first you'd copy the user name and then highlight the password

then you paste the user name and middle click to paste the password

---

### Post by nothingspecial on 2009-09-18
> **MaxIBoy said:**
> You do **not** need to restart to apply aliases. Just run the command "source ~/.bashrc" and it will be applied.

Just type ```
bash
``` to restart bash after adding an alias

---

### Post by nothingspecial on 2009-09-18
In gnome -

Alt + F1 = menu

Alt + F2 = run command

Alt + F4 = Close window

Alt + F5 = Restore Widow

Alt + F7 = Move Window

Alt + F8 = Resize Window

Alt + F9 = Minimize Window

Alt + F10 = maximize Window

Ctrl + + = zoom in

Ctrl + - = zoom out.........

I could go on but I`m getting bored now

---

### Post by coldReactive on 2009-09-18
> **3rdalbum said:**
> You can drag launchers from the Applications menu to the panel or the desktop, and it will copy the launcher to the new location.

That won't work in Xubuntu though.

> **Bölvaður said:**
> aptlinks plugin for firefox (preinstlled)


write [apt:crack-attack](apt:crack-attack)  into the url

Not for me. aptlinks doesn't come with my Ubuntu Firefox, not in 3.0 nor 3.5

> **kerry_s said:**
> :lolflag: that does not restart x, that's simply switching tty.

Yeah, and restarting X isn't enabled by default through the keyboard. Damn dontzap package.

---

### Post by coldReactive on 2009-09-18
-- delete post --

---

### Post by coldReactive on 2009-09-18
-- delete post --

---

### Post by snakeman21 on 2009-09-18
> **infinitejones said:**
> Everyone got so caught up talking about aliases that nobody has mentioned the TWO-FINGER SCROLLING thing!! It's brilliant!

Or was I the only one who didn't know about it....?

Nobody mentioned it because I did, in the first post.

---

### Post by bodyharvester on 2009-09-18
um... i freed the fish, but its been several hours now and i would like to know how to un-free the fish.:(

thanks

---

### Post by snakeman21 on 2009-09-18
> **bodyharvester said:**
> um... i freed the fish, but its been several hours now and i would like to know how to un-free the fish.:(

thanks

Same problem here... Now the damn fish won't stop swimming across my screen.

I tried:

```
kill free the fish
```

Then I tried:

```
killall free the fish
```

And even:

```
kill the fish
```

I would just restart, but I'm downloading a few things right now.

---

### Post by cmay on 2009-09-18
Sometimes when I am about to reinstall I just run tasksel instead of finding the livecd and install from that. I do it sometimes when I am really bored and want to try a different windows manager instead. I do this because  It preserves the files in home directory . I never met anyone else doing this however so I cant say its a official or even reccomended trick.

---

### Post by scragar on 2009-09-18
> **snakeman21 said:**
> Same problem here... Now the damn fish won't stop swimming across my screen.

I tried:

```
kill free the fish
```

Then I tried:

```
killall free the fish
```

And even:

```
kill the fish
```

I would just restart, but I'm downloading a few things right now.

lol
```
killall gnome-panel 
```
Sorry, I forgot to mention that before going to bed.

---

### Post by Marlonsm on 2009-09-18
Another one I've found out a few days ago, here in the UbuntuForums:

The compose key, a very handy tool to make special characters like ÷ ½ © &#8482; &#729; å ß æ » ...

Go to System > Preferences > Keyboard > Layout > Layout Options and choose a key (I use the right Super key).

So when you hold it and press the keys to compose, for example, Compose + C + O = ©, Compose + 1 + 2 = ½ and so on.
You can also hold the right Alt and press any key to get another character, like Alt + S = ß, Alt + M = µ.

---

### Post by MaxIBoy on 2009-09-18
> **3rdalbum said:**
> Install the "padevchooser" package, and make sure its program runs at login, to get control over what programs use what sound devices and to give each program its own individual volume control. There is one side-effect: You may become a Pulseaudio fan.

Or you can install OSS4, which includes "ossxmix" in its default distribution. (Do not confuse this with the obsolete OSS3, which is what is included by default with the Linux kernel.) OSS4 has similar features to PulseAudio, but unlike PulseAudio it's actually usable (not buggy or unstable in any way!) Also, the CPU usage is less, and there's far less latency, which makes it great for things like games and audio editing. (Hearing an explosion a quarter second after it happens can really ruin the experience.) Both OSS4 and PulseAudio have high-quality mixing, but OSS4 is more usable in the real world.

I've attached a screenshot of ossxmix while watching a Youtube video and listening to sound files with 

[LIST=1]
[*]Audacious 2
[*]VLC
[*]GMPlayer
[*]Totem
[/LIST]
The CPU usage on my Core 2 Duo 1.83 Ghz was a little on the high side, but the system is still quite zippy and responsive and all the sound sources mixed flawlessly.

---

### Post by CJ Master on 2009-09-18
> **keplerspeed said:**
> Ha, that would mean to run the previous command as root:
```

! !!

```

Somebody's excited. ;)

---

### Post by Megrimn on 2009-09-21
> **scragar said:**
> 
Alt+F2 launches a run box, try ```
free the fish
``` or```
gegls from outer space
``` :p


I typed 'free the fish' in the command line instead and got this: 
```
megrimn@megrimn-laptop:~$ free the fish
             total       used       free     shared    buffers     cached
Mem:       3731964    1017304    2714660          0      43728     473936
-/+ buffers/cache:     499640    3232324
Swap:      2747072          0    2747072
megrimn@megrimn-laptop:~$ 

```

interesting...

also, if you click on the fish, he will run away for a short time.

---

### Post by schauerlich on 2009-09-21
> **Megrimn said:**
> I typed 'free the fish' in the command line instead and got this:

"free" lists your used/free RAM.

Try this:

```
free -m
```
And of course:
```
man free
```
for more information.

---

### Post by scragar on 2009-09-21
> **Megrimn said:**
> I typed 'free the fish' in the command line instead and got this: 
```
megrimn@megrimn-laptop:~$ free the fish
             total       used       free     shared    buffers     cached
Mem:       3731964    1017304    2714660          0      43728     473936
-/+ buffers/cache:     499640    3232324
Swap:      2747072          0    2747072
megrimn@megrimn-laptop:~$ 

```

interesting...

also, if you click on the fish, he will run away for a short time.

That's because `free` is a command that shows ram usage, it's only in the run box that it has a special meaning.

---

### Post by Megrimn on 2009-09-21
and now I know.

---

### Post by stuart.reinke on 2009-09-21
One of my favourite tricks is the tab auto complete. Start typing a command or directory or file name and hit <tab> and it auto completes it for you. I know it's a BASH short cut and not exclusive to Ubuntu.

---

### Post by Keith Hedger on 2009-09-21
Right click on the Applications menu and select "Edit Menus" to add delete or hide menu items there are also some nice hidden menu items there, especially in the "System Tools" section (varies from release to release) I just found the "Archive Mounter" in the "Other" section dragged it to my desktop (which creates a copy of the launcher) and now I can drag an archive onto it to mount the archive as a normal disk, much easier to browse than using the archive manager

---

### Post by dmglouis on 2009-09-21
I've tried doing the two-finger scrolling thing, but it is not working for me, is there an option to enable it somewhere or does it need some special trackpad?

btw, for people with compiz and scale installed, I made the top-right corner of the screen activate scale, so (with a mouse) it is dead easy to switch between open applications.

---

### Post by earthpigg on 2009-09-21
if you install using the alternate installer .iso or 10mb mini.iso, you get the option to encrypt your home directory. 

this is handy on computers you share with others that may be pranksters, as ***your yahoo/msn/etc passwords are stored*** by pidgin ***in plain text***. proof:

(turn around and make sure no one is looking over your shoulder. your passwords are all about to be displayed on the screen)
```
cat ~/.purple/accounts.xml | grep password
```
and if you want to prove it to others you share your computer with who may be dubious about the need for encryption:
```
cat /home/(username)/.purple/accounts.xml | grep password
```

as we all know, local access is root access... but encryption will at least do a bit to keep your younger sibling from playing pranks on you or reading your e-mails, and you him. the plain text thing, by the way, does not just apply to pidgin or just to Ubuntu.

if you use the mini.iso, the various thousands of packages that make up Ubuntu will download at install time -- this also means you will get more up-to-date packages than using one of the larger .iso files. instead of a massive 400 mb apt-get upgrade immediately after install, you get the up-to-date stuff **_at_** install time.

if you have the reliable bandwidth and it is more than 1 month since the release you are about to install was released, mini.iso is the way to go. in my opinion.

---

### Post by snakeman21 on 2009-09-22
> **dmglouis said:**
> I've tried doing the two-finger scrolling thing, but it is not working for me, is there an option to enable it somewhere or does it need some special trackpad?

btw, for people with compiz and scale installed, I made the top-right corner of the screen activate scale, so (with a mouse) it is dead easy to switch between open applications.

There isn't an option that I know of, your trackpad probably doesn't support it.

---

### Post by tjwoosta on 2009-09-22
I use gpointing-device-setitngs and there is an option to turn two finger scrolling on and off in there. I believe gsynaptics also has this option.

---

### Post by ZarathustraDK on 2009-09-22
Using png's with transparent areas as wallpapers on the cube in compiz, then add a nice skydome. Your desktop becomes partly see-through, and if you use cut-out characters you wont have to worry about matching backgrounds as the skydome effectively becomes the background.

---

### Post by TwiceOver on 2009-09-22
> **stuart.reinke said:**
> One of my favourite tricks is the tab auto complete. Start typing a command or directory or file name and hit <tab> and it auto completes it for you. I know it's a BASH short cut and not exclusive to Ubuntu.

Along with tab, if you hit tab twice it will give you a list of the possible auto completes for whatever command you are running.  Such as "cd /var/www/ [tab] [tab]" would give you the directory contents of /var/www/. 

Tab autocomplete also works in apt-get.  So if you don't know the complete name of the program (or a version changes) just start typing it and hit [tab][tab] to get the autocomplete list.

---

### Post by FuturePilot on 2009-09-22
```
^D
```

It's much quicker than typing exit.

---

### Post by snakeman21 on 2009-09-22
> **ZarathustraDK said:**
> Using png's with transparent areas as wallpapers on the cube in compiz, then add a nice skydome. Your desktop becomes partly see-through, and if you use cut-out characters you wont have to worry about matching backgrounds as the skydome effectively becomes the background.

Ooh, that's creative!  I never would have thought of that.  

Great, guys!  I'm learning a lot of new tricks, as well as being reminded of ones I knew.  Keep 'em coming!

---

### Post by Mobil1 on 2009-09-22
> **snakeman21 said:**
>  Just the other day, I accidentally found out that I could scroll by dragging two fingers on the touchpad

That's cool thanks for that one :)
Umm the only one I could possible add... more of a function than a trick ... if you activate a console via Ctrl+Alt+F1 (tty1 I think) then Shift+PgUp scrolls back a page and Shift+PgDown is the opposite.

I know it sounds really simple but last time I used it I couldn't figure how to do it as the page buttons weren't working by themselves :sad:

---

### Post by imbjr on 2009-09-22
> **scragar said:**
> ```
gegls from outer space
``` :p


wtf

---

### Post by imbjr on 2009-09-22
> **snakeman21 said:**
> Same problem here... Now the damn fish won't stop swimming across my screen.

I tried:

```
kill free the fish
```

Then I tried:

```
killall free the fish
```

And even:

```
kill the fish
```

I would just restart, but I'm downloading a few things right now.

Double-click on them?

---

### Post by coldReactive on 2009-09-22
> **imbjr said:**
> Double-click on them?

Already stated before: killall gnome-panel

---

### Post by snakeman21 on 2009-12-02
Got another one!  You can right-click with the touchpad by tapping it with two fingers.

---

