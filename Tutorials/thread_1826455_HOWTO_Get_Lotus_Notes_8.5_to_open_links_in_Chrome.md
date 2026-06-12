---
title: "HOWTO: Get Lotus Notes 8.5 to open links in Chrome"
date: 2011-08-16
forum: Tutorials
---

### Post by twelve17 on 2011-08-16
I ran into a problem where no matter what browser I set in Unity, Lotus Notes 8.5.2 always used Firefox.  There is one solution involving usage of xdg-mime, but it appears that for me that was not enough.  That solution is described [_**here**_]("http://biounix.blogspot.com/2010/03/setting-default-browser-for-lotus-notes.html").

The short answer is: the system's default browser is Firefox, and the user's default is Chromium.  Lotus seems to be combining the system and user defaults, and determining that both of these browsers can open HTML, yet it picks Firefox (the system default) over Chrome, disregarding the user's settings. 

(Note that my conclusions are theoretical, as they are inferred from *strace* output, which isn't able to tell us the intention behind what Notes is doing.)

Anyway, the workaround is to change the system's default browser.  Whether this is acceptable for your scenario is up to you. :)

1. edit this file:

```
# sudo vi /usr/share/applications/defaults.list
```

Change this line:

```
text/html=firefox.desktop
```

to:

```
text/html=chromium-browser.desktop
```

2. Restart notes.


This workaround may also work for regular (classic) GNOME desktops as well, although I have not tested it.

---

Here's how I figured this out.

1. Started up notes.  This kicks off a few processes:

```

/opt/ibm/lotus/notes/notes /authenticate

nsdexec 17432 /home/myself/lotus/notes/data

/opt/ibm/lotus/notes/framework/rcp/eclipse/plugins/com.ibm.rcp.base_6.2.2.20100729-1241/linux/x86/notes2 --launcher.suppressErrors -nosplash -nl en_US -dir ltr -NPARAMS /authenticate -RPARAMS -name IBM Lotus Notes -personality com.ibm.rcp.platform.personality -product com.ibm.rcp.personality.framework.RCPProduct:com.ibm.notes.branding.notes -data /home/myself/lotus/notes/data/workspace -configuration /home/myself/lotus/notes/data/workspace/.config -plugincustomiz....

```

That last one is the one we care about.

2. In a terminal, kicked off strace on the above child notes process:

```
strace -p 16407 &> ~/notessucks.txt
```


3. Went to the Notes UI and clicked a http link.  Quit notes.

4. Inspected the strace file I piped output to (notessucks.txt).  Here's where the magic happens. And by "magic", I mean whatever messed up method Notes decides it wants to screw up your user experience.  


First, it reads the system wide default apps:

```
stat64("/usr/share/applications/defaults.list", {st_mode=S_IFREG|0644, st_size=8882, ...}) = 0
open("/usr/share/applications/defaults.list", O_RDONLY|O_LARGEFILE) = 162

```

My guess is that from here, it sees that firefox is used to open text/html files, because it closes the file right after it finds this out:

```
open("/usr/share/applications/defaults.list", O_RDONLY|O_LARGEFILE) = 162
fstat64(162, {st_mode=S_IFREG|0644, st_size=8882, ...}) = 0
read(162, "[Default Applications]\nvideo/mp4"..., 4096) = 4096
read(162, "audio=totem.desktop\napplication/"..., 4096) = 4096
read(162, "http=firefox.desktop\ntext/abiwor"..., 4096) = 690
read(162, "", 4096)                     = 0
close(162)                              = 0

```

Next, also watches the user's default apps folder:

```
inotify_add_watch(161, "/home/myself/.local/share/applications", IN_MODIFY|IN_ATTRIB|IN_MOVED_FROM|IN_MOVED_TO|IN_CREATE|IN_DELETE|IN_DELETE_SELF|IN_MOVE_SELF|IN_UNMOUNT|IN_ONLYDIR) = 1

```

That folder is where the user's browser preference is stored:

```
myself@myhost:~$ ls -l /home/myself/.local/share/applications/
total 4
-rw-r--r-- 1 myself myself 405 2011-08-16 15:50 mimeapps.list
myself@myhost:~$ cat /home/myself/.local/share/applications/mimeapps.list

[Default Applications]
x-scheme-handler/http=chromium-browser.desktop
x-scheme-handler/https=chromium-browser.desktop
text/html=chromium-browser.desktop
x-scheme-handler/about=chromium-browser.desktop
x-scheme-handler/unknown=chromium-browser.desktop
text/xml=chromium-browser.desktop

[Added Associations]
x-scheme-handler/http=chromium-browser.desktop;
x-scheme-handler/https=chromium-browser.desktop;

```

Later, it sees how it's supposed to handle opening firefox:

```

open("/home/myself/.local/share/applications/firefox.desktop", O_RDONLY|O_LARGEFILE) = -1 ENOENT (No such file or directory)
open("/usr/share/gnome/applications/firefox.desktop", O_RDONLY|O_LARGEFILE) = -1 ENOENT (No such file or directory)
open("/usr/local/share/applications/firefox.desktop", O_RDONLY|O_LARGEFILE) = -1 ENOENT (No such file or directory)
open("/usr/share/applications/firefox.desktop", O_RDONLY|O_LARGEFILE) = 162

```

And then does the same for chromium:

```
open("/home/myself/.local/share/applications/chromium-browser.desktop", O_RDONLY|O_LARGEFILE) = -1 ENOENT (No such file or directory)
open("/home/myself/.local/share/applications/chromium/browser.desktop", O_RDONLY|O_LARGEFILE) = -1 ENOENT (No such file or directory)
open("/usr/share/gnome/applications/chromium-browser.desktop", O_RDONLY|O_LARGEFILE) = -1 ENOENT (No such file or directory)
open("/usr/share/gnome/applications/chromium/browser.desktop", O_RDONLY|O_LARGEFILE) = -1 ENOENT (No such file or directory)
open("/usr/local/share/applications/chromium-browser.desktop", O_RDONLY|O_LARGEFILE) = -1 ENOENT (No such file or directory)
open("/usr/local/share/applications/chromium/browser.desktop", O_RDONLY|O_LARGEFILE) = -1 ENOENT (No such file or directory)
open("/usr/share/applications/chromium-browser.desktop", O_RDONLY|O_LARGEFILE) = 162

```


Now, I'm guessing, it knows that both can open the link I then click on, but for whatever reason, it picks firefox. (I couldn't find the actual exec call in the output, but I obviously saw the firefox app get kicked off.  The closest I found was the snippet below.)

```
getcwd("/home/opt/ibm/lotus/notes", 4096) = 26
access("/home/opt/ibm/lotus/notes/http://www.terracotta.org/products", F_OK) = -1 ENOENT (No such file or directory)
```

Anyway, hope that helps someone else.  Feedback welcome.

---

### Post by bbrady on 2011-10-05
Hi twelve17,

Thanks for posting this, I have been trying to get notes to open links in Chrome for a while now.  The solution you posted worked for me.  

One point of difference was that my [font=courier]/usr/share/applications/defaults.list[/font] was slightly different than yours:

Mine: 
```
text/html=firefox.desktop;google-chrome.desktop
```

Yours: 
```
text/html=firefox.desktop
```

I changed mine to:
```
text/html=google-chrome.desktop;firefox.desktop
```

and that did the trick.  

I suppose I could have removed [font=courier]firefox.desktop[/font] from [font=courier]text/html[/font], however I was curious to see what happened. Now I know. Notes picks the first in the list.

---

### Post by bbrady on 2011-10-05
Better yet, I replaced all occurrences of:

```
firefox.desktop;google-chrome.desktop
```

with

```
google-chrome.desktop;firefox.desktop
```

in 

```
/usr/share/applications/defaults.list
```

---

### Post by luxor on 2012-01-20
Thank you for the writeup.  It is great that you included the steps to figure out the solution.  If more people did this, it would allow more of us in the community to add to our bag of tricks and apply similar tools and logic to solving more of our issues with software on Linux.  I had been searching for this solution for months!

---

### Post by twelve17 on 2012-03-30
@luxor, no problem!  If for no other reason, I write it out for myself for future reference. :)

---

### Post by EclipseAgent on 2012-05-04
Mine still doesn't work. I've updated my personal mimeapps.list and the /usr one. However, I also don't see anything in an strace that indicates it's being pulled as firefox. 

I'm using chromium, so I'm using chromium-browser.desktop.

---

### Post by EclipseAgent on 2012-05-04
I figured it out. On my openSUSE 12.1 box running KDE w/ GTK from GNOME 3.2, the stuff to modify resided in: 
/home/<homedir>/.gconf/desktop/gnome/url-handlers

---

### Post by kdford on 2012-06-07
> **EclipseAgent said:**
> I figured it out. On my openSUSE 12.1 box running KDE w/ GTK from GNOME 3.2, the stuff to modify resided in: 
/home/<homedir>/.gconf/desktop/gnome/url-handlers

EclipseAgent, I think you're on to it.  But my gconf setting for http/https in url-handlers points to a shell script called sensible-browser. (in /usr/bin).  I will look into this (don't have time now) but want to give a bit of time for somebody to reply if they already have an understanding of how this script works and what it provides.

---

### Post by kdford on 2012-06-07
> **kdford said:**
> EclipseAgent, I think you're on to it.  But my gconf setting for http/https in url-handlers points to a shell script called sensible-browser. (in /usr/bin).  I will look into this (don't have time now) but want to give a bit of time for somebody to reply if they already have an understanding of how this script works and what it provides.

Well, I found this post on how to set your default browser using update-alternatives (it updates a script called x-www-browser if I got it right)... Anyway, this page says that sensible-browser CALLS x-www-browser.  I don't think that's the case.

I updated my alternatives for x-www-browser to point to firefox, but when I invoke sensible-browser it still launches chromium.  if I invoke x-www-browser, it now launches firefox.  Notes seems to be calling sensible-browser, since that is what is stored in my gconf settings.  I could of course just change gconf to call firefox.desktop, but I'd rather understand sensible-browser.  will look at it after work.

[https://lists.ubuntu.com/archives/ubuntu-devel/2004-December/002628.html](https://lists.ubuntu.com/archives/ubuntu-devel/2004-December/002628.html)

---

