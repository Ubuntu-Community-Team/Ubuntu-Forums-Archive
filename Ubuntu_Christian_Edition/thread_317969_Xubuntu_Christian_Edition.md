---
title: "Xubuntu Christian Edition"
date: 2006-12-13
forum: Ubuntu Christian Edition
---

### Post by doobit on 2006-12-13
There are several things one needs to do to get a XFce interface version of Ubuntu CE.

One way is just to install Ubuntu CE first and then use Synaptic to install Xubuntu-desktop. The problem with this is you end up with all that unnecessary Gnome stuff on your hard drive ;) 

It's better to start with a standard Xubuntu install, either 6.06 or 6.10, then use Jeremy's scripts (on the install pages of [www.christianubuntu.com](www.christianubuntu.com) )to convert it to Christian Edition.
The scripts need zenity and gedit to work and these are not included in the standard Xubuntu install. You will need to use apt-get install in the terminal or use Synaptic package manager to get and install these first.
Also download and save the .deb for new Parental Controls GUI, because DansGuardian will make it impossible to do it after you convert. You can get it here:  [http://www.ubuntuforums.org/showthread.php?t=355935](http://www.ubuntuforums.org/showthread.php?t=355935)

Secondly, when you extract the files you need to right click on the tarball and choose "extract here" to get them into a folder intact. If you double click to extract them you will completely disassemble the files inside the folder and they won't work when you get ready to run the script. Also, you cannot simply double click on the convert_me script file and choose "open in terminal" becasue that choice is not available in Xubuntu. You will need to open a terminal and navigate to the file location, i.e. ```
$ cd /home/Desktop/christian_ubuntu_convert_me_edgy_blah_blah_blah/
```
Terminal tip: you don't need to type out that long file name. if you type the first letter of each file then hit the Tab key it will autocomplete.

Once you are in the folder you can type ```
ls -a
``` to see the filenames in there. Then type ```
./convert_me
```
to run the script. There will be several dialogs that you need to interact with. Fill in your password and click OK when you are asked.

You will see much activity in the terminal as Xubuntu is converted. It will take a while so be patient and watch for dialog boxes.
You will get the command line back when it's finished and a dialog telling you to reboot. Click OK and reboot.

You now have a converted Xubuntu. 

Next you should install the new DansGuardian GUI that you saved before the conversion. 
```
 $sudo dpkg -i dansguardian-gui-ubuntu_1.3_all.deb 
```
The file name here will change as Jereme updates the script. I recommend the betas because they seem to work just fine for me and they are more functional and beautiful than the old ones.
That's it!

---

### Post by daller on 2006-12-13
Next time, please add a "HOWTO:" to the start of the title...

(I jump those when I search for unanswered posts...)

---

### Post by doobit on 2006-12-13
> **daller said:**
> Next time, please add a "HOWTO:" to the start of the title...

(I jump those when I search for unanswered posts...)

I actually put How To in the tags. Or I tried to, I just noticed the tags have strange symbols in them instead of the text I thought I put in there.

Maybe a Moderator would be so kind as to change the title?

---

### Post by daller on 2006-12-13
> **doobit said:**
> I actually put How To in the tags. Or I tried to, I just noticed the tags have strange symbols in them instead of the text I thought I put in there.

Maybe a Moderator would be so kind as to change the title?

Don't use HOWTO in the tag... It's better in the title...

Forget it this time... Simply remember it next time...

---

### Post by doobit on 2007-01-23
Just curious as to whether or not anyone has benefited from this?

---

### Post by michaelg81 on 2007-01-31
I'm getting ready to try it. I'll try to remember to let you know how it goes. BTW I'm trying to set up on an old Compaq DeskPro (Pentium I), so I hope that using xfce will be a help.

---

### Post by chris308 on 2007-02-20
I have not tried this yet, but very glad to see this asked and answered.  We get older workstations donated to our school all the time that are best suited for a lighter weight desktop environment.  The prospect of getting the benefits of Ubuntu CE on these "obsolete" computers is exciting.

---

### Post by doobit on 2007-02-26
> **chris308 said:**
> I have not tried this yet, but very glad to see this asked and answered.  We get older workstations donated to our school all the time that are best suited for a lighter weight desktop environment.  The prospect of getting the benefits of Ubuntu CE on these "obsolete" computers is exciting.

I'm using XubuntuCE on a couple of older computers already. I have to say that a 233 MHZ PII computer will be very slow and you will need to have a swap partition that's twice the size of your RAM. I have used Puppy and DamnSmall and also dyne 2.x with great success. Puppy usually needs more configuration than the other three. I had DamnSmall on a 233 MHZ laptop and it worked great, although I know the name can be a problem for some.

---

### Post by TravMan63 on 2007-06-01
Plans are to install Ubuntu CE - then XFCE... this next week.

Thanks for the 'how to'

Will post results.

TM

---

### Post by TravMan63 on 2007-06-08
Here's my 'results' post:

Xubuntu installed ok.

Installed gedit (which I believe installed zenity as a requirement )

Downloaded and 'installed' the 'CE conversion'

Tried to install Dansguardian , but it exited with errors (said to run it again I think...)

Both it and the Virtual Rosary were reported as broken.  I removed them both.

====== * here's where things became more 'involved'*

Installed OO Impress (this machines main function is in our Youth program as a slideshow presenter - with videos and the like)

-- the title bar was bad (both in Impress and Write -- fix is here [http://ubuntuforums.org/showthread.php?t=282995](http://ubuntuforums.org/showthread.php?t=282995) )
(edit xorg.conf)

--Impress would not start a slide show - it would become unresponsive when a slide show was 'started'
I ended up hitting control alt del - to safely reboot (I later found I could have used 'process manager' to term or kill the process - that's a great addition as well as app finder and using that with panel manager to create a launcher for Impress see -> [http://ubuntuforums.org/showthread.php?t=448102](http://ubuntuforums.org/showthread.php?t=448102) )

-- I ran Impress in a terminal and had these errors : ( [http://ubuntuforums.org/showthread.php?t=466414](http://ubuntuforums.org/showthread.php?t=466414) )
...something about no JRE library found (I installed about all the java I could find - and pointed OO where it was installed - but... it didn't see it (later found out that Java isn't required for the functions I wanted Impress to perform...)



```

(process:5066): GLib-GObject-CRITICAL **
: gtype.c:2242: initialization assertion failed, 
use IA__g_type_init() prior to this function

(process:5066): Gdk-CRITICAL **
: gdk_screen_get_font_options: assertion 
`GDK_IS_SCREEN (screen)' failed

```

Impress also didn't have the usual icons on the bottom - just text buttons.  After hours of fighting these issues -  reinstalling etc... this fix was  (if I recall correctly) - was to use synaptic to completly remove the open office core, then to reinstall Impress (it seems that open office write is installed by default? - it's not on the live cd)

-
The next challenge was to make impress play wmv, mpg etc file (as the user creates powerpoints at home with these files embedded).  
Using totem/xine would NOT work - I had to install the 'standard' totem, and the gstreamer codecs.

totem/xine  - would play the files ok - standing alone - but Impress would only play about 3 seconds of a video and then stop...

Again - the solution was installing Totem movie player (NOT the xine backend version), and the codecs required.  I think it's great that you can open a file in Totem, and it reports that it can't play it - and then goes and starts the process for the codecs!

======
other comments...
XFCE seems to be a pretty good window manager... pretty snappy on that older machine
Impress is a bit laggy, and the videos in particular take a second or two to start.
I think it may be a bit slower than powerpoint on XP (that was on that same machine)

Now that I'm back on XP, I find myself missing the extra desktops (although my nvidia 7600GT card supports them on this much faster machine (700mhz 256MB vs 1.5 ghz 1GB, XP's still not as responsive)... and I grew accustomed to gedit's hot keys (I like it mucho better than wordpad) - I'm hitting the wrong keys in wordpad now...:p

---
Now the 'real test' will be this Sunday's performance... :KS
TM

---

### Post by TravMan63 on 2007-06-09
Unfortunately, the performance of Impress, was unimpressive.

On some of the mpg files it stopped after a few seconds, and on other videos it was just too jerky.

Same machine played fine with XP and Powerpoint; unfortunately, that's not an option now.

I installed a monitor (for cpu, memory, swap), and it does not appear to be using swap - maybe it's actually a lack of video acceleration (Intel 82810 (E) graphic controller).

Any help?

TM
--- update 2007/06/12
I feel my posts are deviating from the original xubuntuCE 'theme'...
Other than not installing dansguardian and the rosary - all seems to be well with Xubuntu CE!

Other posts/threads concerning this video / office problem:
[http://ubuntuforums.org/showthread.php?t=470842](http://ubuntuforums.org/showthread.php?t=470842)
[http://ubuntuforums.org/showthread.php?t=459832](http://ubuntuforums.org/showthread.php?t=459832)
[http://ubuntuforums.org/showthread.php?t=426133](http://ubuntuforums.org/showthread.php?t=426133)
[http://ubuntuforums.org/showthread.php?t=466414](http://ubuntuforums.org/showthread.php?t=466414)
[http://ubuntuforums.org/showthread.php?t=282995](http://ubuntuforums.org/showthread.php?t=282995)

TM

---

### Post by TravMan63 on 2007-07-30
-- This IS a good thread on 'how to' convert/install XUbuntu to Christian Edition (other than the missing items I listed in an earlier post.

Unfortunately, videos are a requirement (and a preference at the least INSIDE of powerpoint - which I can NOT get to work)...

I found vlc to be the best video player, however this machine - just can't cut it - it's too slow running xubuntu.  It's also too slow with Elive.  I don't think Fluxbox would be much better.  The cpu is being used at 100%, swap is not.

We will need to go back to windows, just because of the performance and playability issues.

TM

---

### Post by Kilz on 2007-08-14
I have a computer I would like to install ubuntu ce on, but its a little to old for the official release. It has a pentium 2 , 400mgz with 256 of ram. 
The xfce desktop may be the answer, but I now have concerns after reading the last posts. I will need dans guardian to work. The computer is going into a classroom at a school our church runs. 
Will the above computer have the necessary power to run everything in the conversion script? Is there anything not listed in the first post that is needed? The internet connection will not be installed for a few weeks yet, and I would like to get everything working before it is.

---

### Post by mysticrider92 on 2007-08-14
> **Kilz said:**
> I have a computer I would like to install ubuntu ce on, but its a little to old for the official release. It has a pentium 2 , 4000mgz with 256 of ram. 
The xfce desktop may be the answer, but I now have concerns after reading the last posts. I will need dans guardian to work. The computer is going into a classroom at a school our church runs. 
Will the above computer have the necessary power to run everything in the conversion script? Is there anything not listed in the first post that is needed? The internet connection will not be installed for a few weeks yet, and I would like to get everything working before it is.

On a P2, your best choice would be one of the *box desktop environments (e.g. fluxbox or openbox). You could convert it in almost the same way, but with Fluxbox the computer will be faster than XFCE.

---

