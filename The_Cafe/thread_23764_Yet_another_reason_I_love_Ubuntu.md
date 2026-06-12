---
title: "Yet another reason I love Ubuntu"
date: 2005-04-03
forum: The Cafe
---

### Post by kassetra on 2005-04-03
I've been trying for *ages* to get this one applet to work called "[Blogfish]("http://www.gnomefiles.org/app.php?soft_id=306")" ... I've tried it with a ton of different versions of SuSE et al... and nada.

But 'lo and behold - I decided to give it yet another try here in Ubuntu Warty... and poof.  it worked.

That's right, it worked - not a single glitch, error, problem, nada.

So now I'm another blogfish in a great big blogpond.  :)

---

### Post by Gandalf on 2005-04-03
[QUOTE=kassetra]I've been trying for *ages* to get this one applet to work called "[Blogfish]("http://www.gnomefiles.org/app.php?soft_id=306")" ... I've tried it with a ton of different versions of SuSE et al... and nada.

But 'lo and behold - I decided to give it yet another try here in Ubuntu Warty... and poof.  it worked.

That's right, it worked - not a single glitch, error, problem, nada.

So now I'm another blogfish in a great big blogpond.  :)[/QUOTE]
 ```

wael@ubuntu://$ blogfish.py
Traceback (most recent call last):
  File "/usr/local/bin/blogfish.py", line 11, in ?
	import gnome.applet
ImportError: No module named applet

```8-[

---

### Post by kassetra on 2005-04-03
[QUOTE=Gandalf]```

wael@ubuntu://$ blogfish.py
Traceback (most recent call last):
  File "/usr/local/bin/blogfish.py", line 11, in ?
	import gnome.applet
ImportError: No module named applet

```8-[[/QUOTE]

Did you edit the blogfish_config.py - so that instead of local/bin it was just bin before you configured and installed?

---

### Post by Gandalf on 2005-04-03
[QUOTE=kassetra]Did you edit the blogfish_config.py - so that instead of local/bin it was just bin before you configured and installed?[/QUOTE]
 hmmmmm no lol i just replaced lib/python2.3/site-packages/ with lib/python2.4/site-packages/
i will try again with bin

---

### Post by electroglas on 2005-04-03
"Poof"

"Did you edit the blogfish_config.py?"


I don't think this qualifies as a poof installation if you had to edit something...

---

### Post by Gandalf on 2005-04-03
same thing
```

wael@ubuntu:/$ /usr/bin/blogfish.py
Traceback (most recent call last):
  File "/usr/bin/blogfish.py", line 11, in ?
	import gnome.applet
ImportError: No module named applet

```

my blogfish_config.py
[code]
#!/usr/bin/env python

prefix = "/usr/"
bin_dir = prefix + "bin/"
bonobo_server_dir = prefix + "lib/bonobo/servers/"
pixmaps_dir = prefix + "share/pixmaps/blogfish/"
python_lib_dir = prefix + "lib/python2.4/site-packages/"
glade_dir = prefix + "lib/blogfish/"
[/url]

---

### Post by TravisNewman on 2005-04-03
[QUOTE=electroglas]"Poof"

"Did you edit the blogfish_config.py?"


I don't think this qualifies as a poof installation if you had to edit something...[/QUOTE]
 It is if that's part of the installation procedure.

---

### Post by kassetra on 2005-04-03
[QUOTE=panickedthumb]It is if that's part of the installation procedure.[/QUOTE]

It's part of the installation/configuration procedure, yeah.

---

### Post by kassetra on 2005-04-03
[QUOTE=Gandalf]same thing
```

wael@ubuntu:/$ /usr/bin/blogfish.py
Traceback (most recent call last):
  File "/usr/bin/blogfish.py", line 11, in ?
	import gnome.applet
ImportError: No module named applet

```[/QUOTE]
you're trying to run it from the command line?  It's an applet that you run from the panel...

---

### Post by Gandalf on 2005-04-03
[QUOTE=kassetra]you're trying to run it from the command line?  It's an applet that you run from the panel...[/QUOTE]
 hmm, i have still one problem with this gnome version, i didn't find the menu editor...

---

### Post by kassetra on 2005-04-03
[QUOTE=Gandalf]hmm, i have still one problem with this gnome version, i didn't find the menu editor...[/QUOTE]

All I did was right click on the panel, left click on "Add to panel..." and then left click again on Blogfish.

---

### Post by telmo on 2005-04-03
There is none! :) This Gnome 2.10 doesn't come with it. We'll have to wait for 2.12
But you can search the forum to find one.

---

### Post by Gandalf on 2005-04-04
[QUOTE=telmo]There is none! :) This Gnome 2.10 doesn't come with it. We'll have to wait for 2.12
But you can search the forum to find one.[/QUOTE]
 hmmm, i hope (as today is the scheduled final release of hoary ) that gnome 2.12 is integrated

---

### Post by TravisNewman on 2005-04-04
[QUOTE=Gandalf]hmmm, i hope (as today is the scheduled final release of hoary ) that gnome 2.12 is integrated[/QUOTE]
 Gnome 2.12 isn't going to be released for a good long while. Gnome 2.10 just came out.

---

### Post by Gandalf on 2005-04-04
oh ok, execuse me for this, but just have ubuntu installed, i usually use debian sarge without X because it runs a server and on my laptop a windows :$ because i couldn't get debian sarge installed on my laptop but ubuntu (god i love this distro) rulessss.....

---

### Post by telmo on 2005-04-04
[QUOTE=kassetra]I've been trying for *ages* to get this one applet to work called "[Blogfish]("http://www.gnomefiles.org/app.php?soft_id=306")" ... I've tried it with a ton of different versions of SuSE et al... and nada.

But 'lo and behold - I decided to give it yet another try here in Ubuntu Warty... and poof.  it worked.

That's right, it worked - not a single glitch, error, problem, nada.

So now I'm another blogfish in a great big blogpond.  :)[/QUOTE]


Love it! Thank you very much! ;)

---

### Post by Gandalf on 2005-04-04
[QUOTE=telmo]Love it! Thank you very much! ;)[/QUOTE]
 how did you installed it?
i have intalled menu editor [http://ubuntuguide.org/temp/#menu-editor](http://ubuntuguide.org/temp/#menu-editor) changed the confiduration file sudo ./install then i added the file into the menu it doesn't start, one question, do i have to restar gnome?

---

### Post by kassetra on 2005-04-04
[QUOTE=telmo]Love it! Thank you very much! ;)[/QUOTE]

Woo!  Another blogfish in the blogpond!  :)

---

### Post by telmo on 2005-04-04
[QUOTE=kassetra]Woo!  Another blogfish in the blogpond!  :)[/QUOTE]

YEP! :D Can i add your peer? I don't see any fish swimming here :(

---

### Post by telmo on 2005-04-04
hmmm... why is mine always crashing???  :roll:

---

### Post by kassetra on 2005-04-04
[QUOTE=telmo]YEP! :D Can i add your peer? I don't see any fish swimming here :([/QUOTE]

I'm in the official list, so it will automagically add me... :)

Have you right clicked and setup your own fish?  (under preferences)

Also - you should have at least one fishy - your own, but sometimes they swim up to the top.  :)

---

### Post by kassetra on 2005-04-04
[QUOTE=telmo]hmmm... why is mine always crashing???  :roll:[/QUOTE]

ok, do you have a proxy?

---

### Post by telmo on 2005-04-04
I do! Is that any good? I have it written in paper somewhere. :S

---

### Post by kassetra on 2005-04-04
[QUOTE=telmo]I do! Is that any good? I have it written in paper somewhere. :S[/QUOTE]

No, I meant maybe your blogfish is crashing because the proxy settings aren't correct...

---

### Post by telmo on 2005-04-04
Nop... not that. Maybe it just crashes because i keep configuring it! :)

---

### Post by Gandalf on 2005-04-06
i'm still having a problem with it, today (don't know why but after a sudo apt-get upgrade even there was no gnome packages) i succeded to see blogfish in add to panel option but i get this error message [color=blue]The panel encountered a problem while loading "OAFIID:GNOME_BlogfishAppletSample"[/color]

here's my blogfish_config.py
```

#!/usr/bin/env python

prefix = "/usr/"
bin_dir = prefix + "bin/"
bonobo_server_dir = prefix + "lib/bonobo/servers/"
pixmaps_dir = prefix + "share/pixmaps/blogfish/"
python_lib_dir = prefix + "lib/python2.4/site-packages/"
glade_dir = prefix + "lib/blogfish/"

```
anyone knows a way to get it working?

---

### Post by jobezone on 2005-04-07
When I try to install blogfish, I get:
$ sudo ./install

Traceback (most recent call last):
  File "./install", line 7, in ?
    import gnome.applet
ImportError: No module named applet

Anyone knows how to install this applet module?

Thanks

---

### Post by kermy on 2005-04-07
[QUOTE=Gandalf]
anyone knows a way to get it working?[/QUOTE]
Nope, but I get the same error though.. :)

I don't even know what the applet does, but it sounds intriguing :)

---

### Post by Gandalf on 2005-04-07
[QUOTE=kermy]Nope, but I get the same error though.. :)

I don't even know what the applet does, but it sounds intriguing :)[/QUOTE]
 me neither loooooooooool :D but i like to discover that's why i'm killing myself to get it working

---

### Post by bored2k on 2005-04-07
[QUOTE=Gandalf]me neither loooooooooool :D but i like to discover that's why i'm killing myself to get it working[/QUOTE]
 Gandalf go to bed dude .. [off-topic :\]

---

