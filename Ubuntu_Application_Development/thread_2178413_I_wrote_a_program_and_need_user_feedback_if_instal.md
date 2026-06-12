---
title: "I wrote a program and need user feedback if installation went o.K."
date: 2013-10-03
forum: Ubuntu Application Development
---

### Post by rusche on 2013-10-03
Hello,

i wrote a post-it application called "papersavers" that is ready for use, but I am not sure if the install works correct for everybody.
Could you please install it from my ppa and give feedback in this thread? 
You should use Ubuntu 13.04 Raring, because there are only packages for this version on Launchpad at the moment.
If it installed, after starting you should see an indicator in the launcher to create new notes.

sudo add-apt-repository ppa:rusche/projects
sudo apt-get update
sudo apt-get install papersavers

Thank you very much!

---

### Post by rusche on 2013-10-03
Now that already 100 people saw this thread, is nobody willing to help me? :confused:

---

### Post by Bucky Ball on 2013-10-03
Doesn't look that way at this point. Please wait twenty four hours before bumping your post.

Most users are not in the habit of installing PPAs from unknown and untrusted sources. It doesn't help that this is your first post. It may help if you give a little detail about yourself and perhaps a link to your website or something else, if you have one. ;)

Give it time. A fellow dev might be able to give you some tips for the best way of getting it tested (making the PPA accessible from a trusted site might help). Getting involved on Launchpad might also be a good idea.

[https://launchpad.net/](https://launchpad.net/)

Good luck.

---

### Post by ibjsb4 on 2013-10-03
> **rusche said:**
> Now that already 100 people saw this thread, is nobody willing to help me? :confused:

Im one of those 100 :)  Im running 12.04 :(

Also I think it would help to give a full description of what your app will do.

---

### Post by rusche on 2013-10-03
Yes I see your point. It is my first post because I was more active on  stackoverflow and askubuntu and thought this place here a better one for  my question.

Let be assured that this package is clean.

It  is a post-it application that comes with an indicator in the panel and  aims to deliver a minimalistic visual experience, with a lot of settings  to tweak, and offers outstanding features like

 - keep on desktop (no minimize, optional)
 - print
 - hyperlinks (but not blue underlined - hold ctrl and click)
 - secret notes
 - synchronisation (via Cloud, say Ubuntu1 or Dropbox)
 - import/export
 - easy internationalisation
 - multiple cases for startup
 - and the usual ones like lock, change color/font and so on

Here is a gallery with some informative pictures: [http://www.abload.de/gallery.php?key=sM2QaLzB](http://www.abload.de/gallery.php?key=sM2QaLzB)

Find attached one of the pictures.

---

### Post by rusche on 2013-10-03
Now I've copied the binaries to other distro series: Quantal, Precise and Saucy, should be running the same like on Raring. Perhaps it takes some time on Launchpad to take effect.

---

### Post by rusche on 2013-10-03
> **Bucky Ball said:**
> Doesn't look that way at this point. Please wait twenty four hours before bumping your post.

Most users are not in the habit of installing PPAs from unknown and untrusted sources. It doesn't help that this is your first post. It may help if you give a little detail about yourself and perhaps a link to your website or something else, if you have one. ;)

Give it time. A fellow dev might be able to give you some tips for the best way of getting it tested (making the PPA accessible from a trusted site might help). Getting involved on Launchpad might also be a good idea.

[https://launchpad.net/](https://launchpad.net/)

Good luck.

Yes thanks, I have already made a hint to OMGUbuntu and Webupd8 but they did not post about it yet and perhaps won't.

---

### Post by ibjsb4 on 2013-10-03
When your ppa gets updated I will give it a try.

---

### Post by rusche on 2013-10-03
> **ibjsb4 said:**
> When your ppa gets updated I will give it a try.

Thank you :)

---

### Post by rusche on 2013-10-03
> **ibjsb4 said:**
> When your ppa gets updated I will give it a try.

Thank you :)

Packages should now be ready

---

### Post by Bucky Ball on 2013-10-04
Looking better and looks handy. ;)

I have attached your large screenshot. Please think of those with slow connections and/or accessibility issues. They will miss out on reading your thread altogether. ;)

Please attach large pics rather than inserting them in the body of your posts.

---

### Post by ibjsb4 on 2013-10-05
It won't launch, I get this ..

```
~$ papersavers
Traceback (most recent call last):
  File "/opt/extras.ubuntu.com/PaperSavers/papersavers.py", line 74, in <module>
    from gi.repository import Gio #to read dconf (Ambiance or Radiance Icons)
ImportError: No module named gi.repository
```

---

### Post by rusche on 2013-10-06
> **ibjsb4 said:**
> It won't launch, I get this ..

```
~$ papersavers
Traceback (most recent call last):
  File "/opt/extras.ubuntu.com/PaperSavers/papersavers.py", line 74, in <module>
    from gi.repository import Gio #to read dconf (Ambiance or Radiance Icons)
ImportError: No module named gi.repository
```

Thank you for the feedback.

Which version of Ubuntu are you running?

I installed PaperSavers on a fresh Ubunu 13.04 i386 and it works so i am not sure why the error occurs.
I thought python3-gi was not installed, but I checked in synaptic and on my machine is has been installed.
Perhaps you used 12.04 and it is different there, if you tell me your system version i can test it in a VM.

---

### Post by ibjsb4 on 2013-10-06
Thanks

Gnome-classic-desktop 12.04 i386

---

### Post by rusche on 2013-10-06
> **ibjsb4 said:**
> Thanks

Gnome-classic-desktop 12.04 i386

Now I've checked it on 12.04.
Installed the same package as in 13.04 and it did not work. Figured out that python3-gi is installed by default in 13.04, but not in 12.04.
 Adding that as a dependency and uploading in the next hours...

Could you please check it again this week, if it works? I think it should now.

---

### Post by rusche on 2013-10-07
Could someone please install the program and give me more feedback? It is only 3 minutes of help and in the end you have a nice application (which you can also remove if you wish).

Thank you.

---

### Post by ibjsb4 on 2013-10-07
> **rusche said:**
> Now I've checked it on 12.04.
Installed the same package as in 13.04 and it did not work. Figured out that python3-gi is installed by default in 13.04, but not in 12.04.
 Adding that as a dependency and uploading in the next hours...

Could you please check it again this week, if it works? I think it should now.

Reinstalled and ..

> ~$ papersavers
in setPath()
/home/host0/.papersavers
in loadNotes(self)
in setPath()
File is ok; Loading
No systemtrayicon available

And it just hangs up at that point.

---

### Post by pqwoerituytrueiwoq on 2013-10-07
using 13.10 xubuntu 64bit
looks to work
does not respect system context menu theme
close dialog lacks window decorations (the do you want to save one)
like the sound effects
dark icons in context menu don't show up will on my albatross theme

---

### Post by rusche on 2013-10-08
> **ibjsb4 said:**
> Reinstalled and ..



And it just hangs up at that point.

Ok I am going to check this. Did a quick test on 13.04 switching to Gnome-Fallback, where it is running. Perhaps the Qt binding is not capable of creating an indicator on 12.04... using the QSystemTrayIcon lib for that.
Thank you so far I will work on that.

---

### Post by rusche on 2013-10-08
> **pqwoerituytrueiwoq said:**
> using 13.10 xubuntu 64bit
looks to work
does not respect system context menu theme
close dialog lacks window decorations (the do you want to save one)
like the sound effects
dark icons in context menu don't show up will on my albatross theme

Glad to hear, thanks for the effort!
Nice that you like the sound theme. But if you want, you can also deactivate it.

The theme... currently, the program checks for Radiance or Ambiance, if none of those activated, it uses the Ambiance icon.
To make each theme fit, I will have to create a discrete icon for each theme.

What do you mean by close dialog? The delete confirm of a note? That was intended, but I am not confident with its looks, though.

Thank you :)

---

