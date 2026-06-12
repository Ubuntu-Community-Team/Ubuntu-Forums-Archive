---
title: "white window overlaying desktop"
date: 2013-04-05
forum: Ubuntu Development Version
---

### Post by cariboo on 2013-04-05
I finally bit the bullet, and installed the three gnome ppas, after having nothing but problems on previous installs. This time everything seems to be working OK, except that I have a white window overlaying the desktop. During boot up, after logging in I can see the desktop background I chose before setting up the ppas, but just before the top panel shows, I can see the window open, and completely cover the desktop.

Has anyone else run into this, and if so what did you do to solve the problem?

---

### Post by mc4man on 2013-04-05
You need to disable fm handling the Desktop, what you're seeing is an empty Desktop folder as the background
```
gsettings set org.gnome.desktop.background show-desktop-icons false
```

---

### Post by dino99 on 2013-04-05
> **mc4man said:**
> You need to disable fm handling the Desktop, what you're seeing is an empty Desktop folder as the background
```
gsettings set org.gnome.desktop.background show-desktop-icons false
```

Should be reported as a bug, as its not easy to find the solution, and has nothing related to "show-desktop-icons"

---

### Post by mc4man on 2013-04-05
> **dino99 said:**
> Should be reported as a bug, as its not easy to find the solution, and has nothing related to "show-desktop-icons"
Don't think it's a bug, it seems many are installing Ubuntu then dist-upgrading to the gnome3 ppa(s).
In that case ubuntu-settings is installed & show-desktop-icons true is set as default. 
I'd suspect that if one used the gnome image that this wouldn't be an issue.

Can be seen if one removes ubuntu-settings or edits /usr/share/glib-2.0/schemas/10_ubuntu-settings.gschema.override changing key to false, then compiling glib-2.0 schemas. If a new user account is then created it will get a desktop background, which one depends on whether removing ubuntu-settings or editing the .override

---

### Post by cariboo on 2013-04-05
This is really weird, I don't have ubuntu-settings installed, I have desktop-show-icons set to false, and creating a new user, has the same problem.

This is a gnome install using the Ubuntu Gnome iso, with just normal updates, and then the ppas added

---

### Post by mc4man on 2013-04-05
> **cariboo907 said:**
> This is really weird, I don't have ubuntu-settings installed, I have desktop-show-icons set to false, and creating a new user, has the same problem.

This is a gnome install using the Ubuntu Gnome iso, with just normal updates, and then the ppas added

will have to give that a try later (if you don't figure out why.

To ck. if you're seeing the Desktop folder is simple, open nautilus  > Desktop & add something to the folder. Then log out/in, if what you added is now in your Bg then that's what you are getting.

Can you change to a normal Bg?

edit: did you do a dist-upgrade after adding ppa(s)?

---

### Post by ronacc on 2013-04-05
I too have been having the white background in gnome shell from the gnome 3 ppa  . used gnome-tweak-tool to turn off have file manager handle desktop there and got the normal background back . when I invoked from term I got this , ```
INFO    : GSettings missing key org.gnome.nautilus.desktop (key computer-icon-visible)
```  . maybe some missing settings are causing the problem .

---

### Post by Stinger on 2013-04-05
@ cariboo907
What does 
```
nautilus --version
gnome-shell --version
gdm --version
```
give you ?
Just to check if you have conflicting packages like I did.
Mine are:
```
GNOME nautilus 3.8.0
GNOME Shell 3.8.0.1
GDM 3.8.0
```

---

### Post by ronacc on 2013-04-05
@ Stinger . I'm showing the same versions as you are .

---

### Post by cariboo on 2013-04-05
> **Stinger said:**
> @ cariboo907
What does 
```
nautilus --version
gnome-shell --version
gdm --version
```
give you ?
Just to check if you have conflicting packages like I did.
Mine are:
```
GNOME nautilus 3.8.0
GNOME Shell 3.8.0.1
GDM 3.8.0
```

My versions are

[LIST]
[*]GNOME nautilus 3.8.0
[*]GNOME Shell 3.8.0.1
[*]GDM 3.8.0
[/LIST]

I tried ronacc's suggestion to use tweak tool to unset the file manager managing he desktop, then setting it. When I let nautilus manage the desktop, I see the files I placed in the desktop folder on the desktop. I tried different backgrounds, and the only one that seems to work is /usr/share/backgrounds/gnome/blinds.jpg, if I select anything else, I get the white background. If I use something from my pictures directory, that also works, so I'm going to assume that most of the background files are somehow corrupted. I'll reinstall gnome-backgrounds, and see what happens.

**Update:** I cleaned out the archived packages, and reinstalled gnome-backgrounds, and blinds.jpg, is still the only included background that works. I guess I'll use it or something from my pictures directory, until I do a fresh install at the end of the month. Thanks everyone for all the help.

---

### Post by ronacc on 2013-04-05
can't you copy the normal desktop bacground and rename it blinds.jpg and put that in /usr/share/backgrounds/gnome/  instead of the one thats there ?

---

### Post by zegnus on 2013-04-25
I've found a solution for fixing it rolling back without needing to reinstall the whole system.

1. remove the gnome3 ppa repositories
2. purge gnome-shell*
3. purge nautilus*
4. purge unity*
5. purge gnome-session*
6. install nautilus unity ubuntu-desktop

Log in again and you should have again everything ok

---

### Post by Sir Rodness on 2013-04-26
I don't know if it was mc4man or someone else. But however or whomever figured out this bug, CHEERS!! Well done!

---

### Post by markbl on 2013-04-26
I upgraded to 13.04 release today and struck this bug after installing gnome-shell and the gnome3 ppa. I experienced it on both a standard ubuntu iso + apt-get install gnome-shell, and also on a ubuntu GNOME iso install. Happened when installing on my host system and also when I installed as a new Virtualbox guest so it just seems a generic bug. The white screen disappears if I disable the file manager from managing my desktop via gnome-tweak-tool.

---

### Post by glaubersm on 2013-04-26
I have the same problem here (Ubuntu Gnome) after add Gnome Team ppa and run dist-upgrade command. The command...
> gsettings set org.gnome.desktop.background show-desktop-icons false
does not solve the problem. Also no result if I disable the file manager from managing my desktop via gnome-tweak-tool.

---

### Post by idarek on 2013-04-27
> **glaubersm said:**
> I have the same problem here (Ubuntu Gnome) after add Gnome Team ppa and run dist-upgrade command. The command...

does not solve the problem. Also no result if I disable the file manager from managing my desktop via gnome-tweak-tool.

Hi guys, I have experienced this problem today as I upgrade to 13.04 and then active gnome3 ppa package.
The solution for this was to restore **nautilus** package to prev. version. 
To do this, you may use **synaptics** and on package **nautilus** from menu > packages and switch version.

---

### Post by DefinityX on 2013-04-27
Great work! I ended up purging the Gnome PPA completely :-(

Can't seem to use your solution though. When I have Nautilus selected in Synaptec, it has the force version option greyed out. Any ideas?

---

### Post by markbl on 2013-04-27
> **DefinityX said:**
> Great work! I ended up purging the Gnome PPA completely :-(
The reason I want the gnome ppa is to get gnome-shell 3.8 instead of the default 3.6 on ubuntu 13.04. The activities view scales windows much smarter in 3.8 compared to 3.6.

---

### Post by cariboo on 2013-04-27
Have any of you that have run into this problem, tried another background, rather than the default ones? When I had the problem, the only default background that would work was /usr/share/backgrounds/gnome/Blinds.jpg. I'm currently using another background from my wallpaper collection which does work without a problem.

---

### Post by mc4man on 2013-04-27
> **markbl said:**
> The reason I want the gnome ppa is to get gnome-shell 3.8 instead of the default 3.6 on ubuntu 13.04. The activities view scales windows much smarter in 3.8 compared to 3.6.

If you want to use Gs 3.8 & Gnome 3.8* then no reason not to but it's not a bug, you can't have nautilus handle the Desktop anymore. 
 The 'white screen' is just your Desktop folder.
(If you were to delete your Desktop folder then you'd see another folder, maybe Home, I forget which one is next in line.

---

### Post by markbl on 2013-04-28
> **mc4man said:**
> If you want to use Gs 3.8 & Gnome 3.8* then no reason not to but it's not a bug, you can't have nautilus handle the Desktop anymore.
I realise that. I don't want Nautilus to manage my desktop. [As I said here a day or so ago](http://ubuntuforums.org/showthread.php?t=2130575&page=2&p=12619804#post12619804), people who want that are not thinking hard enough about it.

---

### Post by DefinityX on 2013-04-28
Yeah, I realize that. But unfortunately switching off Nautilus as the desktop control makes Unity go all wonky. Users that like to jump back and forth will get frustrated. All ready, there's tons of people complaining about this "bug" that don't know any better.

It's a shame that it forked like this... many users do interpret it as "breaking"

---

### Post by markbl on 2013-04-28
> **DefinityX said:**
> All ready, there's tons of people complaining about this "bug" that don't know any better.
Well it is a bug. Unfortunately, after [today's article](http://www.omgubuntu.co.uk/2013/04/gnome-3-8-ppa-for-ubuntu-gnome) in the very popular OMG Ubuntu there is going to be a large number of Unity users trying the GNOME ppa only to find it breaks their Unity environment due to this bug. They will stumble around finding how to ppa-purge then never come back.

---

### Post by RobertSwipe on 2013-05-24
Thanks - this sorted my desktop out.

---

