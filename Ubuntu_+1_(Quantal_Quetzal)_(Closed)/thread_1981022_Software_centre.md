---
title: "Software centre"
date: 2012-05-16
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Miykel on 2012-05-16
G'Day;  All of a sudden software centre crashes just after opening, it started when I installed Gnome shell, I removed Gnome shell but it still crashes...........damn.....any ideas would be greatly appreciated
Regards Miykel

---

### Post by codemaniac on 2012-05-16
Cannot you just remove software-center package and reinstall it again .

---

### Post by kc1di on 2012-05-16
in a terminal try the following commands:

```
sudo apt-get autoclean 
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get update
```
copy and paste them one at a time see if software center still crashes?

---

### Post by Miykel on 2012-05-16
Thanks for the help kc1di, I run them commands but it still crashes, I'll try remove install if that don't work I'll give this install the ceremonial and start again.
Regards Miykel

---

### Post by kc1di on 2012-05-16
before you chuck it try the following also

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Miykel on 2012-05-16
Thanks for hangin' in there kc1di, just finished remove/install then update/upgrade all to no avail, I won't scrap the install just yet I'd rather find out what went wrong so I might avoid it next time.......or not...all part of the fun.
Regards Miykel

---

### Post by kc1di on 2012-05-16
> **Miykel said:**
> Thanks for hangin' in there kc1di, just finished remove/install then update/upgrade all to no avail, I won't scrap the install just yet I'd rather find out what went wrong so I might avoid it next time.......or not...all part of the fun.
Regards Miykel

Good cause that may help others also. 
try taking a look at your home directory look to view hidden files then .config and Software center foder. there is a file there called Software-center-log or something like that. it may hold a clue.

---

### Post by Miykel on 2012-05-16
G'Day     This is what I found in the software centre log

 [general]
maximized = False
size = 1200, 800
add_to_launcher = True
recommender_uuid = 
recommender_profile_id = 
 

Shouldn't the last two have a value ???
Regards Miykel

---

### Post by ts3 on 2012-05-16
You can try to open Software Centre through terminal by typing

```
software-center
```

or possibly "software-centre" depending on language version, I'm not sure :)

If you get an output that ends with something along the lines of  

```
AttributeError: 'ProgressBar' object has no attribute 'set_data'
```

then it's a bug & here's the link to the bug report

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1000238](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1000238)

---

### Post by Miykel on 2012-05-16
thanks again ts3 here is the output from that command

miykel@miykel:~$ software-centre
No command 'software-centre' found, did you mean:
 Command 'software-center' from package 'software-center' (main)
software-centre: command not found
miykel@miykel:~$ 

Regards Miykel

---

### Post by cariboo on 2012-05-16
You may not have the software-center installed, look in /usr/bin you should see a symlink to /usr/share/softwae-center/software-center.

BTW the Software Centre, crash on me too, with the following output on the command line:

```
cariboo@alexis:~$ software-center
2012-05-16 20:09:30,779 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-05-16 20:09:30,783 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-05-16 20:09:31,091 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-05-16 20:09:31,559 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Traceback (most recent call last):
  File "/usr/bin/software-center", line 176, in <module>
    app.run(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1343, in run
    self.show_available_packages(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1273, in show_available_packages
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 149, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 133, in init_view
    SoftwarePane.init_view(self)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/softwarepane.py", line 233, in init_view
    self.datadir)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/appdetailsview.py", line 886, in __init__
    self._layout_page()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/appdetailsview.py", line 1185, in _layout_page
    self.pkg_statusbar = PackageStatusBar(self)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/appdetailsview.py", line 176, in __init__
    self.progress.set_data("transparent-bg-hint", True)
AttributeError: 'ProgressBar' object has no attribute 'set_data'
```

I don't use the Software Centre, so I never noticed the problem. I find Synaptic Package  Manager, gives me more details, and works the way I want it to.

---

### Post by mdurham on 2012-05-17
same crash here too

---

### Post by Miykel on 2012-05-17
Thank goodness for that, I was starting to feel  a bit left out lol.
 I use Synaptic usually but I use the software manager to find out whats available.
  What do you think ;

[general]
maximized = False
size = 1200, 800
add_to_launcher = True
recommender_uuid = 
recommender_profile_id = 

This is from home/config/sofware-centre /software.cfg , do you think the last two entries should have a value ??
Regards Miykel

---

### Post by cariboo on 2012-05-17
> **Miykel said:**
> Thank goodness for that, I was starting to feel  a bit left out lol.
 I use Synaptic usually but I use the software manager to find out whats available.
  What do you think ;

[general]
maximized = False
size = 1200, 800
add_to_launcher = True
recommender_uuid = 
recommender_profile_id = 

This is from home/config/sofware-centre /software.cfg , do you think the last two entries should have a value ??
Regards Miykel

Mine looks the same, so I think that isn't the problem.

---

### Post by UsernameIsInUse on 2012-05-17
Well, try running it in the Terminal. See if anything usefull appears. Less destructive than reinstalling it.

---

### Post by Miykel on 2012-05-17
Cariboo, yours looks the same but yours doesn't launch either does it ????

  I'm seriously thinking of doing an install,  on a small partition, but not update/upgrade or anything, to be used as a blue print, what do you think.
Regards Miykel

---

### Post by cariboo on 2012-05-17
> **Miykel said:**
> Cariboo, yours looks the same but yours doesn't launch either does it ????

  I'm seriously thinking of doing an install,  on a small partition, but not update/upgrade or anything, to be used as a blue print, what do you think.
Regards Miykel

It launches for me, but never finishes loading, before crashing.

---

### Post by fjgaude on 2012-05-17
> **cariboo907 said:**
> It launches for me, but never finishes loading, before crashing.

Same here on my Dell mini-10.

---

### Post by ts3 on 2012-05-17
> **Miykel said:**
> thanks again ts3 here is the output from that command

miykel@miykel:~$ software-centre
No command 'software-centre' found, did you mean:
 Command 'software-center' from package 'software-center' (main)
software-centre: command not found
miykel@miykel:~$ 

Regards Miykel

Hi & you're welcome. There might be a language/spelling problem here :)  The command to launch the software centre is spelled

```
software-center
```

that's US spelling, C-E-N-T-E-R, rather than UK/Australian -TRE

Try launching it this way and take a look at the output. The bug I mentioned earlier has been confirmed by the way: [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1000238](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1000238)

I reported what turned out to be a duplicate bug and am keeping an eye on launchpad for a solution.  In the meantime I hope apt-get install works :)

Cheers

---

### Post by ronacc on 2012-05-17
> **cariboo907 said:**
> It launches for me, but never finishes loading, before crashing.

and then apport crashes trying to report it !

---

### Post by ts3 on 2012-05-17
> **ronacc said:**
> and then apport crashes trying to report it !

Same here :) What works is

```
ubuntu-bug <name of package>
```

Are you getting the same "AttributeError" when you try to launch through a terminal?

---

### Post by ronacc on 2012-05-17
> **ts3 said:**
> Same here :) What works is

```
ubuntu-bug <name of package>
```

Are you getting the same "AttributeError" when you try to launch through a terminal?

no I'm getting "could not get usefullness from server , no username in config file " atleast that seems to be what it is .

---

### Post by jppr on 2012-05-17
> **ronacc said:**
> and then apport crashes trying to report it !

That is Firefox bug...

[https://lists.ubuntu.com/archives/quantal-changes/2012-May/000824.html](https://lists.ubuntu.com/archives/quantal-changes/2012-May/000824.html)

---

### Post by ronacc on 2012-05-17
not using FF , using chrome .

---

### Post by cariboo on 2012-05-17
I reported the problem. Bug #[lpbug]1000943[/lpbug]

---

### Post by ronacc on 2012-05-17
we duped my bug# is 1000937

---

### Post by cariboo on 2012-05-17
Our bug reports are both duplicates of Bug #[lpbug]1000238[/lpbug]

---

### Post by Miykel on 2012-05-17
@ ts3...Yep wrong spelling,here is the output;

miykel@miykel:~$ software-center
2012-05-18 07:42:44,942 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-05-18 07:42:44,996 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-05-18 07:42:45,598 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-05-18 07:42:45,773 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Traceback (most recent call last):
  File "/usr/bin/software-center", line 176, in <module>
    app.run(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1343, in run
    self.show_available_packages(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1273, in show_available_packages
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 149, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 133, in init_view
    SoftwarePane.init_view(self)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/softwarepane.py", line 233, in init_view
    self.datadir)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/appdetailsview.py", line 886, in __init__
    self._layout_page()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/appdetailsview.py", line 1185, in _layout_page
    self.pkg_statusbar = PackageStatusBar(self)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/appdetailsview.py", line 176, in __init__
    self.progress.set_data("transparent-bg-hint", True)
AttributeError: 'ProgressBar' object has no attribute 'set_data'
miykel@miykel:~$ 

Is that the same as veryone else ???

Regards Miykel

---

### Post by ts3 on 2012-05-17
> **Miykel said:**
> Is that the same as veryone else ???

Regards Miykel

Yep, we all filed duplicates of the bug linked above.  I'm subscribed and checking my email for new developments.  I reckon Canonical will fix it at some point before October ;)

---

### Post by ronacc on 2012-05-17
even though mine was duped I'm not entirely sure it is , when I launch software-center from a term I get no out put indicating a problem , software-center launches the quits after about 1 min still no output and no indication as to what caused the crash . Reading through the bug report generated by ubuntu-bug I don't see the problem ( maybe I'm not reading it right ) .

---

### Post by mc4man on 2012-05-17
> **ronacc said:**
> even though mine was duped I'm not entirely sure it is , when I launch software-center from a term I get no out put indicating a problem , software-center launches the quits after about 1 min still no output and no indication as to what caused the crash . Reading through the bug report generated by ubuntu-bug I don't see the problem ( maybe I'm not reading it right ) .

If you wanted to see if same bug you could do this which would allow S-C to start

```
sudo gedit /usr/share/software-center/softwarecenter/ui/gtk3/views/appdetailsview.py
```

(set your root gedit to show line numbers on edit > preferences
Then scroll down to line 175 & remove these 2 lines & 1 empty line
```
        # theme engine hint for bug #606942
        self.progress.set_data("transparent-bg-hint", True)
```

If S-C then works you're affected by this bug, if not then it's something else

---

### Post by cariboo on 2012-05-17
> **mc4man said:**
> If you wanted to see if same bug you could do this which would allow S-C to start

```
sudo gedit /usr/share/software-center/softwarecenter/ui/gtk3/views/appdetailsview.py
```

(set your root gedit to show line numbers on edit > preferences
Then scroll down to line 175 & remove these 2 lines & 1 empty line
```
        # theme engine hint for bug #606942
        self.progress.set_data("transparent-bg-hint", True)
```

If S-C then works you're affected by this bug, if not then it's something else

This solution works for me, so the bug I reported is definitely a duplicate.

Now I can continue to ignore the software-center. :)

---

### Post by ronacc on 2012-05-17
I guess it is the same bug . your suggestion got it .

---

### Post by wilee-nilee on 2012-05-17
> **mc4man said:**
> If you wanted to see if same bug you could do this which would allow S-C to start

```
sudo gedit /usr/share/software-center/softwarecenter/ui/gtk3/views/appdetailsview.py
```(set your root gedit to show line numbers on edit > preferences
Then scroll down to line 175 & remove these 2 lines & 1 empty line
```
        # theme engine hint for bug #606942
        self.progress.set_data("transparent-bg-hint", True)
```If S-C then works you're affected by this bug, if not then it's something else

All the same errors above this post, and the daily cd also crashes, have not tried this edit on it.

Edit worked on install GSC opens now.

---

### Post by mc4man on 2012-05-17
Probably this was caused by the gtk3 upgrade the other day, Wouldn't know if it worked before that, but whenever gtk3 upgrades it's not surprising if something breaks

Not gtk3, python-gobject instead

---

### Post by wilee-nilee on 2012-05-17
> **mc4man said:**
> Probably this was caused by the gtk3 upgrade the other day, Wouldn't know if it worked before that, but whenever gtk3 upgrades it's not surprising if something breaks

I rarely use it except for easy access to the software sources, worked till today for me.

---

### Post by mc4man on 2012-05-18
Wasn't gtk3 upgrade, seems to be the python-gobject* upgrades that did the deed (3.3.1

---

### Post by ts3 on 2012-05-18
> **mc4man said:**
> If you wanted to see if same bug you could do this which would allow S-C to start

```
sudo gedit /usr/share/software-center/softwarecenter/ui/gtk3/views/appdetailsview.py
```

(set your root gedit to show line numbers on edit > preferences
Then scroll down to line 175 & remove these 2 lines & 1 empty line
```
        # theme engine hint for bug #606942
        self.progress.set_data("transparent-bg-hint", True)
```

If S-C then works you're affected by this bug, if not then it's something else

Thanks for the fix, it works without a hitch.

---

### Post by bcbc on 2012-05-23
+1 thanks

---

### Post by Sk8er72 on 2012-06-04
It's help: [http://ubuntovod.ru/instructions/ubuntu-software-center-crashes.html](http://ubuntovod.ru/instructions/ubuntu-software-center-crashes.html) :)

---

### Post by cariboo on 2012-06-04
> **Sk8er72 said:**
> It's help: [http://ubuntovod.ru/instructions/ubuntu-software-center-crashes.html](http://ubuntovod.ru/instructions/ubuntu-software-center-crashes.html) :)

Seeing as the working language of this forum is English, we'd prefer that you link to solutions written in English.

---

### Post by effenberg0x0 on 2012-06-04
> **cariboo907 said:**
> Seeing as the working language of this forum is English, we'd prefer that you link to solutions written in English.

Hi, I think I can help with the translation:
> "*&#1058;&#1086; &#1074;&#1086;&#1090; &#1074;&#1072;&#1084; &#1080;&#1085;&#1089;&#1090;&#1088;&#1091;&#1082;&#1094;&#1080;&#1103; &#1087;&#1086; &#1080;&#1089;&#1087;&#1088;&#1072;&#1074;&#1083;&#1077;&#1085;&#1080;&#1102; &#1087;&#1088;&#1086;&#1073;&#1083;&#1077;&#1084;&#1099;*"
[I]> In Soviet Russia, you don't fix Software-Center. Software-Center fixes _[COLOR="Red"]**[YOU]("http://uncyclopedia.wikia.com/wiki/Russian_reversal_(joke)")**[/COLOR]_!
[/I]

Sorry, I just couldn't resist the opportunity.
Anyway, the fix has already been posted here and everywhere else. It works.

Regards,
Effenberg

---

### Post by mc4man on 2012-06-04
The latest S-C should be fixed by now, one of those rare where the workaround is the same as the fix

---

### Post by cariboo on 2012-06-04
> **effenberg0x0 said:**
> Hi, I think I can help with the translation:

**

Sorry, I just couldn't resist the opportunity.
Anyway, the fix has already been posted here and everywhere else. It works.

Regards,
Effenberg

I realize that the fix has already been posted elsewhere. I use chromium which pops up a translate button on foreign language web sites, so it isn't a problem for me, but for those that use other browsers, they may not have that option, it is best to stay with English language web sites, but thanks for your version of the translation, :):)

---

