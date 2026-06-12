---
title: "IE4linux on Intrepid?"
date: 2008-12-05
forum: Wine
---

### Post by bionnaki on 2008-12-05
Hello. I need to use Internet Explorer 6 for a government website and firefox does not work nor is it allowed. I've tried the usual user agent tricks but they do not work.

How exactly can I run IE6 on my intrepid install? I see that IE4linux is an option, but it looks like only edgy, fiesty, and dapper are supported. [http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu](http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu)

any ideas?

---

### Post by ajmorris on 2008-12-06
hi there,
IEs4linux can be used in your intrepid install. That tutorial is just very outdated, which is the reason it only has the old versions of ubuntu in it. Whilst (if they exist) you could just substitute 'edgy' with your version of ubuntu where it is specified in the tutorial for adding the wine budgetdedicated repo, you do not actually need this for wine/cabextract.  Wine and cabextract are both in the ubuntu repositories, so just run:
```
sudo apt-get install wine cabextract
```  (NOTE: i cannot remember if wine is in universe or not (it is probably in multiverse), but it is provided in one of the default repositories that is listed in /etc/apt/sources.list  so just edit that file, and uncomment all repositories in there (the deb-src ones are not needed though) then run sudo apt-get update, and then the command outlined above.)

after running that command, run the next steps outlined in the tutorial:
```
 wget http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz
 tar zxvf ies4linux-latest.tar.gz
 cd ies4linux-*
 ./ies4linux

```and you should be good to go, it should work fine.


AJ

---

### Post by bionnaki on 2008-12-07
thanks
that worked
even though my cpu was 100%.

but that's fine for now - just had to fill out a form on a government website. 

thanks!

---

### Post by gemme on 2008-12-12
I tried that commands (up-to-date Intrepid) and got an error:
> /home/mati/Pulpit/ies4linux-2.99.0.1/ui/pygtk/ies4linux-gtk.py:264: GtkWarning: gtk_text_layout_real_invalidate: assertion `layout->wrap_loop_count == 0' failed
  self.textbuffer.delete(it, self.textbuffer.get_end_iter())
**
Gtk:ERROR:/build/buildd/gtk+2.0-2.14.4/gtk/gtktextview.c:3425:gtk_text_view_validate_onscreen: assertion failed: (text_view->onscreen_validated)
ui/pygtk/python-gtk.sh: line 6: 11565 Aborted                 (core dumped) python "$IES4LINUX"/ui/pygtk/ies4linux-gtk.py

Any ideas how to fix it? IE6 is the only app I need to run in Wine :(

---

### Post by robertjack on 2008-12-12
Hi,
I have installed wine first and later realized that I would also need cabextra to run internet explorer 7.0. I have tried above mentioned steps and got the following error.
[COLOR="Red"]
robertjack@ROBERTJACK:~/ies4linux-2.99.0.1$ ./ies4linux
IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).

/home/robertjack/ies4linux-2.99.0.1/ui/pygtk/ies4linux-gtk.py:268: GtkWarning: gtk_text_layout_real_invalidate: assertion `layout->wrap_loop_count == 0' failed
  self.textbuffer.insert_with_tags(self.textbuffer.get_end_iter(), line, tag)
ui/pygtk/python-gtk.sh: line 6: 20885 Segmentation fault      python "$IES4LINUX"/ui/pygtk/ies4linux-gtk.py
robertjack@ROBERTJACK:~/ies4linux-2.99.0.1$ [/COLOR]

BTW, Should I really need both wine and cabextract to run IE7?
Please advise,
Jack

---

### Post by robertjack on 2008-12-12
Hi,
I have installed wine first and later realized that I would also need cabextra to run internet explorer 7.0. I have tried above mentioned steps and got the following error.
[COLOR="Red"]
robertjack@ROBERTJACK:~/ies4linux-2.99.0.1$ ./ies4linux
IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).

/home/robertjack/ies4linux-2.99.0.1/ui/pygtk/ies4linux-gtk.py:268: GtkWarning: gtk_text_layout_real_invalidate: assertion `layout->wrap_loop_count == 0' failed
  self.textbuffer.insert_with_tags(self.textbuffer.get_end_iter(), line, tag)
ui/pygtk/python-gtk.sh: line 6: 20885 Segmentation fault      python "$IES4LINUX"/ui/pygtk/ies4linux-gtk.py
robertjack@ROBERTJACK:~/ies4linux-2.99.0.1$ [/COLOR]

BTW, Should I really need both wine and cabextract to run IE7? If so, why?
Please advise,
Jack

---

### Post by sges on 2008-12-14
I have found a work around (a hack) to this problem.

do as instructed but stop just after **cd ies4linux-***

type **gedit ui/pygtk/ies4linux-gtk.py **

goto line 268. Lines 267 268 and 269 are as follows

# Insert text and relocate scroll
self.textbuffer.insert_with_tags(self.textbuffer.get_end_iter(), line, tag)
self.textview.scroll_to_iter(self.textbuffer.get_end_iter(), 0)

Comment these two lines 268 and 269 changing them so 267, 268 and 269 read

# Insert text and relocate scroll
#self.textbuffer.insert_with_tags(self.textbuffer.get_end_iter(), line, tag)
#self.textview.scroll_to_iter(self.textbuffer.get_end_iter(), 0)

Save and File|quit

You will be at the command prompt

Now run **./ies4linux**


After you click **OK** in the .ies4linux window the status window will be blank. This is correct as we have commented out the lines that generated the text on the status window. Wait until **Cancel** changes to **Close** then close the window.

IE will now be installed.


PS. Does anyone know how to make a bug report on the ies4linux web site? I could not find a way.

---

### Post by sges on 2008-12-15
another solution is 
**./ies4linux --no-gui**

---

### Post by drizad on 2009-01-04
Yes, I also have same problem when installing ies4linux in my Intrepid. This is the error:

python: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
ui/pygtk/python-gtk.sh: line 6:  6456 Aborted                 python "$IES4LINUX"/ui/pygtk/ies4linux-gtk.py

and sges suggestion with
./ies4linux --no-gui

works like a charm...

---

### Post by Leoncio on 2009-01-14
Worked for me too.  After adding "http://wine.budgetdedicated.com/apt intrepid main" to the repos, I ran the following:
```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install wine cabextract
wget http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz
tar zxvf ies4linux-latest.tar.gz
cd ies4linux-*
**./ies4linux --no-gui**

```

Cheers!

---

### Post by wstay on 2009-01-22
After successfully installing ie6/ie7 using wine, ie7 freezes on loading while with ie6 it opens Ok but when viewing shares and stocks on a bank website, although  I installed with -- no-localization to use English only, I don't know why after few minutes or a little longer after viewing, the English characters change to Chinese characters by itself.
Can anyone please explain why and how I can view my shares and stocks in English only?

---

### Post by iNaitvad on 2009-01-22
Use Winedoors XD

---

### Post by wstay on 2009-01-24
> **iNaitvad said:**
> Use Winedoors XD

Thank you for the help.
I use Winedoors to download Ares.
Ares downloaded and opened ok but it keep on connecting and never got connected. 
When I click on Internet and fill in [http://aresgalaxy.sourceforge.net](http://aresgalaxy.sourceforge.net), it gives me an error message as follows - HTML rendering is currently disabled.
How can I correct this problem.
Please advise.

---

### Post by Old *ix Geek on 2009-01-24
> **bionnaki said:**
> I need to use Internet Explorer 6 for a government website and firefox does not work nor is it allowed.I know you're not asking, but I'm going to say it anyway because this is a BIG pet peeve of mine: You need to COMPLAIN to that government web site and tell them to get over it. Explain that not only is IE the most insecure browser on the planet but that you--as an enlightened, intelligent Linux user--do not use it and do not have access to it.  (They don't need to know that it's possible to put that bloated piece of crap on Linux. Just say it's a windoze program and you're on Linux.)

Back when I used to come across "IE only" web sites I **ALWAYS** complained to them--and I'd like to think that my efforts, combined with those of other anti-IE folks, were responsible for doing away with that ridiculous phenomenon.  If people don't complain...how/why/when will sites like that see the light? :confused:

---

### Post by vonkad on 2009-02-17
Thanks sges, your --no-gui did the trick.

---

### Post by MedellinManDem on 2009-02-20
> **ajmorris said:**
> hi there,
IEs4linux can be used in your intrepid install. That tutorial is just very outdated, which is the reason it only has the old versions of ubuntu in it. Whilst (if they exist) you could just substitute 'edgy' with your version of ubuntu where it is specified in the tutorial for adding the wine budgetdedicated repo, you do not actually need this for wine/cabextract.  Wine and cabextract are both in the ubuntu repositories, so just run:
```
sudo apt-get install wine cabextract
```  (NOTE: i cannot remember if wine is in universe or not (it is probably in multiverse), but it is provided in one of the default repositories that is listed in /etc/apt/sources.list  so just edit that file, and uncomment all repositories in there (the deb-src ones are not needed though) then run sudo apt-get update, and then the command outlined above.)

after running that command, run the next steps outlined in the tutorial:
```
 wget http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz
 tar zxvf ies4linux-latest.tar.gz
 cd ies4linux-*
 ./ies4linux

```and you should be good to go, it should work fine.


AJ

I did this, then just went to the directory and double clicked the bin to install.

---

### Post by ashmew2 on 2009-03-02
> **Old *ix Geek said:**
> I know you're not asking, but I'm going to say it anyway because this is a BIG pet peeve of mine: You need to COMPLAIN to that government web site and tell them to get over it. Explain that not only is IE the most insecure browser on the planet but that you--as an enlightened, intelligent Linux user--do not use it and do not have access to it.  (They don't need to know that it's possible to put that bloated piece of crap on Linux. Just say it's a windoze program and you're on Linux.)

Back when I used to come across "IE only" web sites I **ALWAYS** complained to them--and I'd like to think that my efforts, combined with those of other anti-IE folks, were responsible for doing away with that ridiculous phenomenon.  If people don't complain...how/why/when will sites like that see the light? :confused:

Well sites in India dont really care what 1 person thinks. I need to open an auction site which opens fine in Firefox. But you cant place a bid on items with Firefox . IE works fine with that. And ive tried complaining but theyll ignore me every time. So i thought just sticking with IE would be a better idea.
Oh and plus , Firefox on Windows/Linux both dont work with the bid thing on that site.

---

### Post by ashmew2 on 2009-03-02
By the way , i didnt like the grey Win95 look of IE6 under Wine. IF anyone else wants to change it , take a look here : [http://gastly.wordpress.com/2007/06/18/apply-windows-xp-themes-in-wine/](http://gastly.wordpress.com/2007/06/18/apply-windows-xp-themes-in-wine/)

And even better . open IE6 and goto :

View > Toolbars > Customize.
Change Icon Options : Large Size.
Also , put a tick in Show Text Labels.


I personally thought it looks better this way..

---

### Post by DougieFresh4U on 2009-03-16
> **bionnaki said:**
> 
even though my cpu was 100%.

Yes, I noticed my CPU was at 100% when using  ie6 and also when I closed it, it was still running in the background and had to go to 'System Monitor' and kill the process.
 I installed AIM using 'ie6' and wine. (running Jaunty) the latest version I could get to install was AIM 5.9. My point being is that when I now open AIM, it automatically opens Internet Explorer and there is no 100% CPU, then I shut down AIM and continue what ever it was I needed from 'ie6', strange 'hacky' way of doing things, and when I close 'ie6', it's closed (not running in the background still)
Also, a couple of years ago a forum member made a package for ie6. Some thing to do with 'Ubuntu CE'  and the script made a 'IE4Linux installer' that was put in the 'Applications>Internet' menu and when you clicked it, it installed Internet Explorer and put a launcher in Applications>Internet menu. I looked it up not long ago but the links were 'dead', but I liked how it made the launcher in the menu and I didn't have to clutter my desktop up with icon. 
Just my little 2 cent thoughts

---

### Post by ashmew2 on 2009-04-10
You can always put a launcher under any Menu (Old or New) using a menu editor like Alacarte.

---

### Post by cristian.palmas on 2009-04-21
Hi All,

Is there a way to install ONLY IE7 after have installed IE6 and IE55? I just installed them and modified them in order to work best with my Kubuntu 8.10 and I don't want to work again on them.
So I'd like to know if I can run ./ies4linux targeting only IE7.

Thanks in advance.

Cristian Palmas

---

