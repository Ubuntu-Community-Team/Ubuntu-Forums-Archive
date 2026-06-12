---
title: "ardour3 doesn't start in awesome WM"
date: 2014-09-28
forum: Ubuntu Studio
---

### Post by nova-deviator on 2014-09-28
Hi all,

I'm a happy UbuntuStudio user for about 3-4 years. I just recently upgraded (fresh install) to a Ubuntu Studio 14.04 64bit.

I'm running Awesome Window Manager instead of xfce4. No matter how I login into Awesome (either via lightdm login screen or via s startx script) I cannot start ardour3. When I login into a 'regular' UbuntuStudio [xfce4] session Ardour works. Starting Ardour (3.5.308~dfsg-1) in a terminal in Awesome it just hangs after few lines and nothing happens. I installed the version of Ardour from KXstudio (3.5.380-1kxstudio1) and situation is similar, only now the termnal continuously outputs:


```
$ ardour3 
bnd txt domain [gtk2_ardour3] to /opt/ardour3/share/locale
Ardour3.5.380 (built using 3.5-380-g2f6065b and GCC version 4.4.6)
ardour: [INFO]: Your system is configured to limit Ardour to only 4096 open files
ardour: [INFO]: Loading system configuration file /opt/ardour3/etc/ardour_system.rc
Loading user configuration file /home/random/.config/ardour3/ardour.rc
Using SSE optimized routines
(ardour-3.5.380:3932): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
(ardour-3.5.380:3932): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
(ardour-3.5.380:3932): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
(ardour-3.5.380:3932): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
(ardour-3.5.380:3932): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
(ardour-3.5.380:3932): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
(ardour-3.5.380:3932): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
(ardour-3.5.380:3932): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
(ardour-3.5.380:3932): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
...

```

Murrine engine is installed.
What exactly does xfce4 runs that satisfies Ardour to run that Awesome doesn't? Has anyone had any experience running Ardour outside of 'official' UbuntuStudio's XFCE4 session?

Any pointers would be greatly appreciated!

---

### Post by CrocoDuck on 2014-09-30
Hi! I am using openbox and sometimes GTK can get tricky. Could you repost the output of these commands?

```
ls -l -a ~
```

```
ls -l -a ~/.config/
```

---

### Post by nova-deviator on 2014-10-14
> **CrocoDuck said:**
> Hi! I am using openbox and sometimes GTK can get tricky. Could you repost the output of these commands?

```
ls -l -a ~
```

[https://gist.github.com/novadeviator/e69ac8afd484b3497f81](https://gist.github.com/novadeviator/e69ac8afd484b3497f81)


> **CrocoDuck said:**
> 
```
ls -l -a ~/.config/
```

[https://gist.github.com/novadeviator/e5172d6a72d3c84a8882](https://gist.github.com/novadeviator/e5172d6a72d3c84a8882)

---

### Post by CrocoDuck on 2014-10-15
Ok... Here what I did on my openbox to get rid of issues: I have renamed these directories in ~/.config/ to something else:

```

lrwxrwxrwx   1 random random    49 sep 21 13:35 gtk-2.0 -> /home/random/.themes/FlatStudioDark_Nova/gtk-2.0//
drwx------   2 random random  4096 sep 20 11:56 gtk-2.0_bak/
lrwxrwxrwx   1 random random    49 sep 20 12:02 gtk-3.0 -> /home/random/.themes/FlatStudioDark_Nova/gtk-3.0//

```

([here]("http://bbs.archbang.org/viewtopic.php?id=5001") the thread where that has been suggested to me).

I am testing a minimal Debian stable net install with awesome wm. Sooner or later I will be able to test Ardour on top of it and see what happens!

---

### Post by nova-deviator on 2014-10-17
> **CrocoDuck said:**
> Ok... Here what I did on my openbox to get rid of issues: I have renamed these directories in ~/.config/ to something else:

unfortunately, this didn't help.



> **CrocoDuck said:**
>  I am testing a minimal Debian stable net install with awesome wm. Sooner or later I will be able to test Ardour on top of it and see what happens!

ok. i would greatly appreciate any new info if something comes up.

---

### Post by CrocoDuck on 2014-10-18
Hi! I have tested Ardour and it is working good at first sight:


[IMG]http://th04.deviantart.net/fs70/PRE/f/2014/291/d/1/debian_7_6___awesome_wm_audio_workflow_test_1_by_crocoduck_oducks-d83bg6n.png[/IMG]

[IMG]http://th07.deviantart.net/fs70/PRE/f/2014/291/f/a/debian_7_6___awesome_wm_audio_workflow_test_2_by_crocoduck_oducks-d83bfsy.png[/IMG]

I am using Debian 7.6 on virtualbox. I did a very minimal install (just the core operative system). Then I installed awesome, configured it a little and installed alsa-base, Ardour and all its dependencies. Awesome is set to use Clearlooks. So sorry, but I cannot reproduce your problem. However, since Debian is running older and stable versions of the software, I think you could be experiencing a bug in the latest versions of Ardour or in the window manager / libraries. Also, I suppose your system to be much more configured and less minimal than mine, hence you could be experiencing some problem with configuration files... Sorry, but I cannot come with an idea to understand what is happening... :(:confused:

---

### Post by nova-deviator on 2014-10-19
> **CrocoDuck said:**
> 
I am using Debian 7.6 on virtualbox. I did a very minimal install (just the core operative system). Then I installed awesome, configured it a little and installed alsa-base, Ardour and all its dependencies. Awesome is set to use Clearlooks. So sorry, but I cannot reproduce your problem. However, since Debian is running older and stable versions of the software, I think you could be experiencing a bug in the latest versions of Ardour or in the window manager / libraries. Also, I suppose your system to be much more configured and less minimal than mine, hence you could be experiencing some problem with configuration files... Sorry, but I cannot come with an idea to understand what is happening... :(:confused:

thanks for trying this out and sharing results.
what is Ardour's version?
my configuration is 
UbuntuStudio 14.04.1
Ardour 3.5.403-1kxstudio1

the version of ardour3 that came with UbuntuStudio (3.5.308~dfsg-1) already had the same problem

i have a feeling that this mess has something to do with gtk3...

if someone can shed some light on this would be awesome...

---

### Post by nova-deviator on 2014-10-19
ok , i found the culprit.
it's the GTK theme.
with LXappearance i set any other theme (like for example ClearLooks) and the Ardour3 is happy to start. If I set the theme in LXappearance to FlatStudio ([http://gnome-look.org/content/show.php/?content=154296](http://gnome-look.org/content/show.php/?content=154296)) ardour complains in a loop with 

Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", and doesn't start.

perhaps there's a way to improve or hack FlatStudio, because that's the only good dark theme that also changes appearance to new gtk3 applications...

hope that helps someone around...

---

