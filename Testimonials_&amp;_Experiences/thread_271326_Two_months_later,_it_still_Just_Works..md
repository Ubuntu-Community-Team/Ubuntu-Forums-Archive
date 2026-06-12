---
title: "Two months later, it still Just Works."
date: 2006-10-04
forum: Testimonials &amp; Experiences
---

### Post by CydoniaRaven on 2006-10-04
It hasn't been two months exactly, but I've been wanting to contribute to the forums and haven't had much else to say, so here's a bit of a progress report / additional testimonial / whatever you wish to call it, from me.

On August 15th, my computer decided it was going to stop working.  [My initial thread]("http://www.ubuntuforums.org/showthread.php?t=236612") chronicles the incident.  I installed Breezy Badger after the transplant surgery, then updated to Dapper Drake.

Now, eleven days shy of two full months later, I don't really even notice anymore.  I don't think in "Windows".  I'm not all that adept at thinking in "Linux" yet, but everything I need/want to do, I can do quite easily and with comfort.  Not bad for a guy who was with Windows since the 3.1 era.

But that's not because I have any particular talent.  In part it's because I'm lucky to have knowledgeable friends, but mainly it's because of Ubuntu.  There are things Ubuntu can't really help with -- for example I still have trouble installing anything that's not in a .deb -- but that hasn't harmed me, and it's not a failing on Ubuntu's part.

SIDETRACK: I do find it tongue-in-cheek humorous that the one thing I asked the forums to help me with completely failed.  (My question: "I want to know if I can have an XFCE-style right-click context menu in Gnome.  I tried installing XFCE overtop of Ubuntu and it broke, and I do not want to try that again.  I just want to know if such a menu is possible in Gnome.  Can you help me?"  Answer: "Oh, here's how you can install XFCE overtop of Ubuntu!"  And then no further response. ](*,) )  Again, that's not Ubuntu's fault.  The respondant just didn't read my full post, and then the thread got buried; that's a pretty busy forum up there. :rolleyes:  If someone here happens to know the answer, I'm still interested!

At any rate, after two months, I don't feel any pain.  I have no burning desire to go back to Windows, especially with Vista so near.  I am happy with my Linux experience, thanks to Ubuntu, and I want to stay and continue to learn.  That, I believe, is the mark of a true conversion.  So thanks again, Ubuntu.  I'm looking forward to a long and prosperous relationship.

---

### Post by DoctorMO on 2006-10-04
You can install XFC with apt-get ;) 

the only thing I can't do in Linux is use all those viruses and torjens I collected over the years :-D

---

### Post by 3rdalbum on 2006-10-05
Just a minor little quibble with your post; it's not a "contextual menu" - you are invoking it with no context, and it's showing you all the programs on your system :-)

I believe that if you go into the script that starts up Gnome, and replace the "nautilus" line with "xfdesktop" (if you've got Xfdesktop loaded, you probably don't), you will get the menu. But don't quote me on that, it's probably easier to install XFCE :-)   If the apt-get method failed, remember there's a great, easy-to-use compiler-installer available on the XFCE website.

---

### Post by CydoniaRaven on 2006-10-05
> **3rdalbum said:**
> If the apt-get method failed, remember there's a great, easy-to-use compiler-installer available on the XFCE website.

Yeah, it failed pretty hard.  I can't adequately describe what went wrong; I wish I could, because it was bad.  My "solution" will probably be to back up all my data on the DVDs I got as a birthday present and just install Xubuntu fresh.  I have an uneasy feeling about doing that, though, as if I'm going to find myself missing something.  Ah well, vague FUD is MS's way, not mine. :-k 

Regardless of my little menu issue, everything is running great, and I primarily intended this as a "thank you" to Ubuntu, and an example to Windows folks that it really can be easy to switch over.  I can think of a few things I would like to see; perhaps an app that lists programs that have been installed and *where everything associated with them has been placed*... but that would really just be a crutch.  Might as well learn to hobble along without it. :)

---

### Post by DoctorMO on 2006-10-05
cat /var/lib/dpkg/info/$MYPACKAGE.list

will list all the files installed. although it could be done better I think with some kind of script or maybe an option via dpkg (there probably is but I havn't found it)

---

### Post by phormion on 2006-10-05
> **DoctorMO said:**
> 
...
or maybe an option via dpkg (there probably is but I havn't found it)

dpkg -L <package>

---

### Post by DoctorMO on 2006-10-05
See I was right *trying to save some pride*

---

### Post by dolphinsonar on 2006-10-05
I have been on Ubuntu for 2 moths too.  Same deal.  Learning command line is pretty cool, finding software in synaptic is very convenient.  People in the cafe look at my computer screen and wonder, what the hell is that THING?!?!

---

### Post by srt4play on 2006-10-05
> **CydoniaRaven said:**
> I can think of a few things I would like to see; perhaps an app that lists programs that have been installed and *where everything associated with them has been placed*... but that would really just be a crutch.  Might as well learn to hobble along without it. :)

You can do this in synaptic by selecting the installed package, clicking the properties button at the top, then the "installed files" tab. This will show you every file installed by the package.

---

### Post by Senshi on 2006-10-05
I haven't been running Ubuntu for that long but it still works, as opposed to Windows that tends to grow old and then die (at least on my machine).  Now I dual boot, and only use Windows for certain tasks.  Not to often.  I'm just waiting for my Windows to die, and the new version of Ubuntu to come out so I can do a clean installation of both.  :)

---

### Post by ferd on 2006-10-06
It's been about two months for me too. I'm on my 8th install of Ubuntu/Kubuntu and I now have a boringly stable and entirely usable installation. Yes, I am that old and dumb. I can only hope that the nex:) t release is as good as this one.

---

### Post by mynimal on 2006-10-06
I used to use that right-click menu all the time under GNOME. Here's how to do it (This is guaranteed to work):

1. Open gconf-editor to /apps/nautilus/preferences, and uncheck "show_desktop"
2. sudo apt-get install xfdesktop4
3. System -> Preferences -> Sessions, navigate to the Startup Programs tab
4. Click the Add button, type in xfdesktop. Click ok, etc.

Now you're all set. Nautilus no longer manages your desktop, but Xfdesktop does. This is **not** installing XFCE over Ubuntu, only the desktop manager (And its dependencies) are installed.

---

