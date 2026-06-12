---
title: "Allow .bin, and .Run files to execute without physical input."
date: 2012-03-03
forum: The Cafe
---

### Post by ruinairas on 2012-03-03
Things to improve Ubuntu. (To become more mainstream that is....)
 

 

 

 *CHANGE THE DEFAULT WALLPAPER IN THE INSTALLER AND DESKTOP
 .
 *MORE CONTROLS IN THE SYSTEM SETTINGS, INCLUDING ADD/REMOVE APPLICATIONS. Ubuntu Software Center is nice, but I'd like an alternative to manage the applications.
 

 ***Allow (.bin) (.Run.) (.sh) to run without asking for executive rights. VERY ANNOYING.**
 

 *Have a easy solution to turn ON/OFF for Key Ring Passwords, and ROOT Password. Getting asked for a password every time I do something gets old. I know, it makes the system more secure, but isn't that what a firewall is for? Most users like to be a bit &#8220;Risky&#8221; if they have an opportunity to avoid annoyance.
 

 *Add a basic tutorial to show users around the new desktop.

---

### Post by uRock on 2012-03-03
I like the wallpapers. They are very "ubuntu". 

Synaptic can easily be installed, if one prefers a different way of installing from the repos.

Allowing (.bin) (.Run.) (.sh) to run without being given permissions will negate a very important security feature. 

There are plenty of HowTos on the net which explain how to effectively bypass built in security features. I would not recommend an easy solution to do such a thing. The keyring does not get activated if one requires a password to log in, which is good enough for most.

Your last request is already in place. With all windows closed or minimized you click on help, then click the Ubuntu Help button shown in the screenshot.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=213656&stc=1&d=1330821043[/IMG]

---

### Post by uRock on 2012-03-03
Moved to the *Cafe*.

---

### Post by forrestcupp on 2012-03-03
> **ruinairas said:**
> 
 *CHANGE THE DEFAULT WALLPAPER IN THE INSTALLER AND DESKTOPWhose opinion are you going to go with when you decide what is the perfect wallpaper?

> **ruinairas said:**
>  *MORE CONTROLS IN THE SYSTEM SETTINGS, INCLUDING ADD/REMOVE APPLICATIONS. Ubuntu Software Center is nice, but I'd like an alternative to manage the applications.Compared to Windows' one choice in managing applications, I'd say we have it pretty good. It's not a bad idea to include something like the Software Center in the system settings, though.
 
> **ruinairas said:**
>  ***Allow (.bin) (.Run.) (.sh) to run without asking for executive rights. VERY ANNOYING.**If you put a .bin .run or .sh file in your /home directory, you don't need to enter your password, unless it is trying to execute a command that would require it. I've downloaded plenty of .run files that install a program to your /home folder, and you don't need special permissions. If you tried to do system wide things that way, anybody could make a malicious script that appears safe that will destroy your system. How many people actually go through all of the code in every program or script they run?

> **ruinairas said:**
>  *Add a basic tutorial to show users around the new desktop.There's an interactive tutorial that interactively explains Unity on [Ubuntu's web site](http://www.ubuntu.com/tour/en/).

---

### Post by yetiman64 on 2012-03-03
Wallpapers: when the install is done (or in my case even on the live cd) right click the desktop and change it to something more palatable, or even supply one of your own images. Not something that will either improve or detract from Ubuntu. Just personal preference.

Software: apart from Software Center, apps can be installed from terminal or Synaptic (has to be added either from terminal or Software Center). You already have (at least) 3 ways of installing apps, one of them being "new user friendly" (USC), putting another means of installing in System Settings seems a bit over the top in my opinion. Maybe it is because that is what you are indoctrinated into using in Windows (see link towards end of post).

> **ruinairas said:**
> ...***Allow (.bin) (.Run.) (.sh) to run without asking for executive rights. VERY ANNOYING.**....
uRock has already commented that this would negate a current security feature. What you suggest here is one of the configuration aspects that stops Ubuntu getting viruses so easily.

I mean, really, how hard is it to right click a file, select Properties, select the Permissions tab and tick the executable box at the bottom of the tab for a file? You can even set the executable bit for several files at once with this when highlighting a selection of files,  just make sure the tick box is ticked and does not have the horizontal line set in it to set all the files selected as executable.

Just so you understand, this suggestion to "make Ubuntu more mainstream" would undermine one of the common reasons people adopt Ubuntu in the first place (the no viruses bit is pretty nice feature for Linux :-)).

Also understand, anyone who has used Ubuntu/Linux for any length of time would usually read your suggestions as a request to "please provide me with a free clone of Windows". With that in mind, finally a info link for you [[COLOR=Blue]--Linux != Windows--[/COLOR]]("http://linux.oneandoneis2.org/LNW.htm") (quite a long read, but well worth it imo, especially if you decide to persevere with learning Linux rather than expecting it to be a clone of Windows etc).

Regards yetiman64

---

