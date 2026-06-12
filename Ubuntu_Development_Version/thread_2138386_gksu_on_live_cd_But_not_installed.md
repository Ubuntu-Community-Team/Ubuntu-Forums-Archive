---
title: "gksu on live cd But not installed"
date: 2013-04-23
forum: Ubuntu Development Version
---

### Post by mc4man on 2013-04-23
gksu(do) is on the way out but as of yet common uses of using pkexec aren't in place. (gedit, nautilus, gdebi, ect.

So why it's not installed is unknown here, just another fault in what may just be  an 'obligated' release

Anyway users will be prompted to install but should be aware that the default install mode of gksu is "su" which doesn't work out well in Ubuntu.
So after installing one must run  (possibly only in 64 bit
```
gksu-properties
```
And change the mode from su (screen) to sudo or you'll be prompted to provide the 'root' password instead of the admin user password

---

### Post by mc4man on 2013-04-23
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1172095](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1172095)
(too late likely to change even if They want, more curious then anything else

---

### Post by tdockery97 on 2013-04-23
> **mc4man said:**
> gksu(do) is on the way out but as of yet common uses of using pkexec aren't in place. (gedit, nautilus, gdebi, ect.

So why it's not installed is unknown here, just another fault in what may just be  an 'obligated' release

Anyway users will be prompted to install but should be aware that the default install mode of gksu is "su" which doesn't work out well in Ubuntu.
So after installing one must run 
```
gksu-properties
```
And change the mode from su (screen) to sudo or you'll be prompted to provide the 'root' password instead of the admin user password

Thanks for the info.  That was driving me crazy.  One thing I've discovered is that this problem exists only in the 64 bit flavor.  gksu works like it should out of the box in the 32 bit spin.

---

### Post by Warren Hill on 2013-04-24
**gksu** is not the preferred way to run GUI applications as root any more.  At least that's what I was told yesterday when I asked some of the developers in IRC yesterday.

 #ubuntu-dev on irc.freenode.net

In the long term they want us to use **pkexec** instead or better still command line programs with **sudo**.

Some of the developers were surprised that users might edit config files with 

```
gksu gedit path_to_file
```

when 

```
sudo vim path_to_file
```

saves you two keystrokes. [vim]("http://www.openvim.com/tutorial.html") is very powerful but not something I would expect a casual user to be instantly comfortable with.

pkexec however is not trivial to use with GUI applications.

You can install  gksu in 13.04 however but it may be removed from future versions of Ubuntu.

There is more information here on [URL="http://askubuntu.com/a/284717/107450"]Ask Ubuntu

[/URL]

---

### Post by zika on 2013-04-24
> **Warren Hill said:**
> **gksu** is not the preferred way to run GUI applications as root any more.  At least that's what I was told yesterday when I asked some of the developers in IRC yesterday.

 #ubuntu-dev on irc.freenode.net

In the long term they want us to use **pkexec** instead or better still command line programs with **sudo**.

Some of the developers were surprised that users might edit config files with 

```
gksu gedit path_to_file
```

when 

```
sudo vim path_to_file
```

saves you two keystrokes. [vim]("http://www.openvim.com/tutorial.html") is very powerful but not something I would expect a casual user to be instantly comfortable with.

pkexec however is not trivial to use with GUI applications.

You can install  gksu in 13.04 however but it may be removed from future versions of Ubuntu.

There is more information here on [URL="http://askubuntu.com/a/284717/107450"]Ask Ubuntu

[/URL]I use```
alias gsudo='/usr/bin/sudo -H'
```and use **gsudo** for GUI applications... It is completely correct in any way, check that...

---

### Post by Elfy on 2013-04-24
vim is something I would expect the casual user to cry out with a 

"I though Ubuntu was linux for normal people"

developers might find it easier to use vim ... 

glass towers again :|

---

### Post by philinux on 2013-04-24
I thought this was the preferred new method as described in synaptic.

gksu-polkit
> This is the new generation of gksu, a simple utility to run programs
as root, even in X-based environments. This version uses the new
libgksu-polkit library, which uses PolicyKit for authorization
purposes and a D-Bus service to actually perform the work.

```
gksu-polkit gedit pathtofile
```

---

### Post by sdowney717 on 2013-04-24
no way I will use vim.
I dont even want to learn how to use that geeky editor.

gksu was also not working as I expected, so thanks. I am on 64 bit

---

### Post by grahammechanical on 2013-04-24
The first time we try to run gksudo <program> on a new install, the terminal advises to install gksu. I have done that and I have not had any problems running gksudo gedit or gksudo nautilus or anything like that. Mind you, when I close the application the terminal throws up a mass of error messages. But that is not my problem. I achieved what I set out to do. I have not needed to run sudo -i or anything like that.

It seems that gksu authentication is set (on my machine) to sudo. I did not do it. May be that is the default setting on Ubuntu or may be it becomes the default setting when gksudo is first run.

---

### Post by stoneguy on 2013-04-24
"Just use vim" is really arrogant advice (even to people that know it). And there's no excuse for the 64-bit framework working differently from the 32-bit one.

---

### Post by mc4man on 2013-04-24
> **philinux said:**
> I thought this was the preferred new method as described in synaptic.
gksu-polkit

```
gksu-polkit gedit pathtofile
```
Thanks - that works so that'll be the new way.., thought I'd tried it a while back & didn't work, maybe wrong syntax, whatever
(not default installed so - 

sudo apt-get install gksu-polkit
ect.
gdebi will pull in gksu until that package is fixed, shifted here to use gksu-polkit & it seems to use it fine instead

As far as gksu being on the image, that a bug that will be corrected at some point (ubiquity should use pkexec instead

---

### Post by tdockery97 on 2013-04-24
> **stoneguy said:**
> "And there's no excuse for the 64-bit framework working differently from the 32-bit one.

That's the larger issue in my opinion.

---

### Post by mc4man on 2013-04-24
Overall I like this better, for personal use can now add "org.gnome.gksu.spawn" to a .pkla & dispense with a password altogether

---

### Post by matt_symes on 2013-04-24
> **Warren Hill said:**
> 
Some of the developers were surprised that users might edit config files with 

```
gksu gedit path_to_file
```

when 

```
sudo vim path_to_file
```

saves you two keystrokes. [vim]("http://www.openvim.com/tutorial.html") is very powerful but not something I would expect a casual user to be instantly comfortable with.


This sounds like a developers joke or someone with the same sense of humour as me.

Any experienced developer would not expect Joe public to use vim.

---

### Post by jbicha on 2013-04-24
> **philinux said:**
> I thought this was the preferred new method as described in synaptic.

gksu-polkit


No, gksu-polkit is unmaintained with security bugs. See [bug 1172339]("http://pad.lv/1172339") for more info.

---

### Post by EgoGratis on 2013-04-24
> **Warren Hill said:**
> **gksu** is not the preferred way to run GUI applications as root any more.  At least that's what I was told yesterday when I asked some of the developers in IRC yesterday.

 #ubuntu-dev on irc.freenode.net

In the long term they want us to use **pkexec** instead or better still command line programs with **sudo**.

Some of the developers were surprised that users might edit config files with 

```
gksu gedit path_to_file
```

when 

```
sudo vim path_to_file
```

saves you two keystrokes. [vim]("http://www.openvim.com/tutorial.html") is very powerful but not something I would expect a casual user to be instantly comfortable with.

pkexec however is not trivial to use with GUI applications.

You can install  gksu in 13.04 however but it may be removed from future versions of Ubuntu.

There is more information here on [URL="http://askubuntu.com/a/284717/107450"]Ask Ubuntu

[/URL]

In other words average Joe got scre*ed again and alternative fall short.

---

### Post by mc4man on 2013-04-24
> **jbicha said:**
> No, gksu-polkit is unmaintained with security bugs. See [bug 1172339]("http://pad.lv/1172339") for more info.

Well then for 13.04 users gksu is still the solution (even though no dev's would ever use) when or if though don't want to use terminal editors or terminal commands, ect.

Nothing like putting in replacements before removing the current & common method.
(and if gksu-polkit is such a bad deal then why so late to remove from raring or earlier?

---

### Post by mc4man on 2013-04-27
Just as an aside - 
Decided to enable pkexec here for both nautilus & gedit, maybe properly, maybe not quite so. (not really worried.

Previosly had been using sudo -i <command> but what the heck & also like a context menu options. (& occassional alt+f2.
No sense getting into unless others wish to check out, ect., screen show some ex.

---

### Post by mc4man on 2013-04-29
per a messaged request, do at own risk & keep in mind someday maybe this will be done officially. (& possibly better, suggestions welcome
1st. - create 2 new policies. I'm naming them as I saw fit to do.

```
sudo nano /usr/share/polkit-1/actions/com.ubuntu.pkexec.gedit.policy
```

copy below, paste into nano, then on keyboard -  ctrl+o, enter, ctrl+x

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC
 "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/PolicyKit/1/policyconfig.dtd">
<policyconfig>

  <action id="com.ubuntu.pkexec.gedit">
    <message>Authentication is required to run gedit as root</message>
    <icon_name>accessories-text-editor</icon_name>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>auth_admin</allow_active>
    </defaults>
    <annotate key="org.freedesktop.policykit.exec.path">/usr/bin/gedit</annotate>
    <annotate key="org.freedesktop.policykit.exec.allow_gui">true</annotate>
  </action>

</policyconfig>
```


```
sudo nano  /usr/share/polkit-1/actions/com.ubuntu.pkexec.nautilus.policy  
```   
same deal, copy below, paste into nano, ctrl+o, enter, ctrl+x                     

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC
 "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/PolicyKit/1/policyconfig.dtd">
<policyconfig>

  <action id="com.ubuntu.pkexec.nautilus">
    <message>Authentication is required to run nautilus as root</message>
    <icon_name>system-file-manager</icon_name>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>auth_admin</allow_active>
    </defaults>
    <annotate key="org.freedesktop.policykit.exec.path">/usr/bin/nautilus</annotate>
    <annotate key="org.freedesktop.policykit.exec.allow_gui">true</annotate>
  </action>

</policyconfig>
```

At this point (or maybe a log out/in) you'll have 2 terminal only commands - 
pkexec gedit
pkexec nautilus

To improve upon (adds alt+F2 & nautilus actions entries.

In a bin in PATH, (/usr/bin, /usr/local/bin, or ~/bin), create 2 script files, make executable (I use ~/bin

Name this one gedit-pkexec
```
#!/bin/sh
pkexec "/usr/bin/gedit" "$@"

```

Name this one nautilus-pkexec
```
#!/bin/sh
pkexec "/usr/bin/nautilus" "$@"
```

So now you can use in a terminal or from alt+F2
gedit-pkexec
nautilus-pkexec

Adding to nautilus actions -  
screen 1 shows nautilus set up in command tab, screen 2 shows nautilus set up in the mimetype tab (set to only show on directories

screen 3 shows gedit set up in command tab, screen 4, (optional),  shows gedit in the mimetype tab

As far as screen 4, for gedit I leave the default of all files(*), then add exclusions for mimetypes I Don't want the root gedit option to show, screen reflects excluding .c files, .cpp files, .h files,  folders, &  .so files

screen 5 is just an example of how to set up the Action tab (in this case gedit

Tips on nautilus actions - 
to show directly in context menu adjust nautilus-actions > Edit > Preferences, & disable "Create a root 'Nautilus-Actions' menu & may as well disable the option below "About Nautilus-Actions item"

When adding or editing a mimetype or basename, after entering,  press enter on keyboard while focus is still on the edit or it won't set.

---

### Post by matt_symes on 2013-04-30
Nice post mc4man and required for anybody not comfortable with the terminal.

Just one point, make sure *~/.bin* is last and not first in your PATH.

---

### Post by mc4man on 2013-04-30
> **matt_symes said:**
> 

Just one point, make sure *~/bin* is last and not first in your PATH.
Have always wondered about that & any reasons for or against.
By default if one mkdir bin & a restart then ~/bin is added first in PATH.
(at least here have left so with explicit intention that any 'same name' scripts or binaries take precedence. 

However, in many/most cases I do add a number to end of script or alt. binary names so as not to match the name of some linux command, installed or not. 
(I remember once looking at a list of 'used' command names, must of been in the thousands, didn't see any ending in a # though probably didn't go thru complete list..

---

### Post by dino99 on 2013-04-30
The discussion is opened, but still wait for devs answers
[http://askubuntu.com/questions/288087/can-i-use-pkexec-in-a-python-script-or-a-desktop-file](http://askubuntu.com/questions/288087/can-i-use-pkexec-in-a-python-script-or-a-desktop-file)
[http://askubuntu.com/questions/287845/how-to-configure-pkexec](http://askubuntu.com/questions/287845/how-to-configure-pkexec)

---

### Post by matt_symes on 2013-04-30
Hi

> **mc4man said:**
> Have always wondered about that & any reasons for or against.
By default if one mkdir bin & a restart then ~/bin is added first in PATH.
(at least here have left so with explicit intention that any 'same name' scripts or binaries take precedence. 

However, in many/most cases I do add a number to end of script or alt. binary names so as not to match the name of some linux command, installed or not. 
(I remember once looking at a list of 'used' command names, must of been in the thousands, didn't see any ending in a # though probably didn't go thru complete list..

It's considered a security risk - i believe - however slight. I remember reading a discussion about the fact.

I once unpacked busybox into ~/.bin with symlinks and all. ~/bin was first in my path. Coming back to that PC later, i could not work out why i had lost half the functionality of some of the binaries. :D

D'oh.

Kind regards

---

### Post by mc4man on 2013-04-30
> **dino99 said:**
> The discussion is opened, but still wait for devs answers
[http://askubuntu.com/questions/288087/can-i-use-pkexec-in-a-python-script-or-a-desktop-file](http://askubuntu.com/questions/288087/can-i-use-pkexec-in-a-python-script-or-a-desktop-file)
[http://askubuntu.com/questions/287845/how-to-configure-pkexec](http://askubuntu.com/questions/287845/how-to-configure-pkexec)
One is totally open, the other implies that "pkexec gedit" works from cli in 13.04. 
I found it doesn't without a .policy file in place, maybe that's what the poster was doing??

In any event the way I described works just fine here for all MY uses of root gedit & nautilus, (no terminal needed),  but at the end of the day this is Ubuntu's problem, they're the ones that removed/depreciated gksu & put nothing in to replace.

I'm surmising that the error seen about "WARNING **: Could not open X display", ect. is due to no .policy, particularly the line in  - 
"annotate key="org.freedesktop.policykit.exec.allow_gui">true"

matt - thanks for add. info

---

### Post by dino99 on 2013-04-30
yes the past ubuntu history have proved that quality is still a wish ;)
and new decisions often dont care about the required transition.
even with mature projects like ubiquity or compiz, to talk only about most problematic's, we still get unnumbered issues.
strangely its take ages to get fixes (i mean real fixes); so where is the bottom problem : design or coding lacks ?

---

### Post by mc4man on 2013-04-30
> **dino99 said:**
> ; so where is the bottom problem : design or coding lacks ?
I'm thinking not enough cooks in the (current) kitchen nor waiters in 'bug room'

---

