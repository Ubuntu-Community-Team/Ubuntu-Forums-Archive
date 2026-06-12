---
title: "Trouble ahead!"
date: 2009-06-12
forum: The Cafe
---

### Post by dioltas on 2009-06-12
Just got back from cinema with girlfriend and checked my laptop. Had aterm, ncmpc++ and deluge running and my aterm was filled up with:

> (firefox:31747): Gdk-WARNING **: XID collision, trouble ahead

(firefox:31747): Gdk-WARNING **: XID collision, trouble ahead

(firefox:31747): Gdk-WARNING **: XID collision, trouble ahead

(firefox:31747): Gdk-WARNING **: XID collision, trouble ahead

(firefox:31747): Gdk-WARNING **: XID collision, trouble ahead

(firefox:31747): Gdk-WARNING **: XID collision, trouble ahead

(firefox:31747): Gdk-WARNING **: XID collision, trouble ahead

(firefox:31747): Gdk-WARNING **: XID collision, trouble ahead

(firefox:31747): Gdk-WARNING **: XID collision, trouble ahead

(firefox:31747): Gdk-WARNING **: XID collision, trouble ahead

(firefox:31747): Gdk-WARNING **: XID collision, trouble ahead

(firefox:31747): Gdk-WARNING **: XID collision, trouble ahead
[me@arch_laptop ~]$ 


cept the whole aterm buffer was filled with it!

Firefox wasn't running so obviously there was some trouble! I thought it was funny so I said I'd share it, maybe it's just the tiredness :D (4:26 am here!) Oh well, good night ubuntu forums;)

---

### Post by asac on 2009-06-23
This is not a new bug. Its just that there was a gtk+ commit that now shows this error: [http://git.gnome.org/cgit/gtk+/commit/?id=339298b638ae76c546717f2136970b93438295a9](http://git.gnome.org/cgit/gtk+/commit/?id=339298b638ae76c546717f2136970b93438295a9).

Bugs on the underlying issue:

Gnome bug 581526 in gdk "XID table corruption from reuse of XIDs, resulting in leak, incorrect window destroyed status ("unexpectedly destroyed"), and crash" - [http://bugzilla.gnome.org/show_bug.cgi?id=581526](http://bugzilla.gnome.org/show_bug.cgi?id=581526).

Mozilla bug 467744 in Widget: Gtk "crash @gdk_window_new from moz_drawingarea_create_windows after GdkWindow 0x???????? unexpectedly destroyed" - [http://bugzilla.mozilla.org/show_bug.cgi?id=467744](http://bugzilla.mozilla.org/show_bug.cgi?id=467744).

---

### Post by jatinps on 2010-04-05
the problem still exists in ubuntu lucid with latest firefox!

---

### Post by Beatbreaker on 2010-04-13
confirmed, this still exists, occurring on both FF 3.6 and Google Chrome:

(exe:15102): Gdk-WARNING **: XID collision, trouble ahead

(exe:15112): Gdk-WARNING **: XID collision, trouble ahead


 uname -a
Linux michael-desktop 2.6.32-19-generic #28-Ubuntu SMP Wed Mar 31 17:46:20 UTC 2010 i686 GNU/Linux

---

### Post by Jose Consuervo on 2010-04-21
Just got this tonight for the first time, Lucid 64-bit, with firefox. I haven't installed/tried it with chrome. But just today I installed my Gigabyte GSX 250 Nvidia card, and am running it via HDMI to my monitor with s/pdif leads plugged in. I say this because I never had this issue before hand. I haven't ran Konqueror via command line, but that has crashed as well. I hope this helps!

---

### Post by Jose Consuervo on 2010-04-21
Forgot this in the last post, but I seem to have only crashed with Gmail, with a seg fault, (yikes you can't point their firefox!) <<((that was me)) and yahoo caused many "(firefox-bin:2242): Gdk-WARNING **: XID collision, trouble ahead" warnings, however no crash. This info should help more than my last useless post.

---

### Post by dennymallow on 2010-05-03
Same thing here using Namoroka development version and visiting Launchpad. (that's really weird... I have a bug visiting a bug tracking site!! :S)

---

### Post by aktiwers on 2010-06-16
```
aktiwers@HAL2:~$ firefox
FoxyProxy settingsDir: /home/aktiwers/.mozilla/firefox/wdtnbv9m.default/foxyproxy.xml

(firefox-bin:17615): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:17615): Gdk-WARNING **: XID collision, trouble ahead
info: 0, warning: 936, error: 3976
Done
info: 0, warning: 0, error: 1
Done
info: 0, warning: 0, error: 1
Done
info: 0, warning: 0, error: 1
Done
info: 0, warning: 936, error: 3976
Done
Segmentation fault
aktiwers@HAL2:~$ firefox -v
Mozilla Firefox 3.6.3, Copyright (c) 1998 - 2010 mozilla.org
aktiwers@HAL2:~$ uname -a
Linux HAL2 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux
aktiwers@HAL2:~$
```

Got it as well

---

### Post by 7oby on 2010-06-18
@aktiwers: Same system and problem (firefox segfaulting even after purging session information form filesystem manually):

Mozilla Firefox 3.6.3, Copyright (c) 1998 - 2010 mozilla.org
Linux thinktank 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux
Ubuntu 10.04 LTS w/ latest Updates and Patches installed

--

I was able to fix the problem by moving from open source radeon_drv.so to ATI closed source fglrx_drv.so.

Either install the one that comes with Ubuntu 10.04 LTS or install the latest catalyst 10.6:
ati-driver-installer-10-6-x86.x86_64.run --buildpkg Ubuntu/lucid
purge existing fglrx drivers and install at least:
sudo dpkg -i fglrx_8.741-0ubuntu1_amd64.deb
sudo dpkg -i fglrx-amdcccle_8.741-0ubuntu1_amd64.deb
sudo dpkg -i fglrx-modaliases_8.741-0ubuntu1_amd64.deb
sudo dpkg-reconfigure fglrx
sudo aticonfig --initial --force

All steps (including the latest) are required or google or head over to
[http://www.phoronix.com/forums/showthread.php?t=24300](http://www.phoronix.com/forums/showthread.php?t=24300)

Latest catalyst 10.6 fixes long outstanding bug:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/568988](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/568988)

If you don't have ATI then I don't know how to fix your bug. At least I had the same segfault and the above worked for me.

---

### Post by aktiwers on 2010-06-21
Im on Nvidia..

But did an upgrade to FF 3.6.4 and the problem seams to be gone for now..

---

### Post by fzimper on 2010-07-22
I am also getting an abundance of these:
```

(<unknown>:8846): Gdk-WARNING **: XID collision, trouble ahead
```and occasionally, e.g. when I am displaying the Search Requests page in the Google Webmaster Tools.

```
  (parent won, so we're not deferring)
  (parent won, so we're deferring)
  (processing deferred in-call)
```The XID collision messages are reliably reproducible when I use piwik (version 0.6.4). Then they are printed one after the other.
I am running a 64-bit Lucid Lynx with Firefox 3.6.6

Hope this helps,
Frank

---

### Post by Offoffoff on 2010-07-27
I have the same problem. What is wrong with Firefox? How to fix it? How to diminish bug or excessive logging?

---

### Post by wucan on 2010-07-31
Firefox 3.6.8 still had these message, in my latest lucid updated today.

Are firefox folk know these issue?

---

### Post by bebop52 on 2010-08-02
It's not only a firefox problem, I have the same errors with Ubuntu 10.04 Lucid und Chrome. Actually there are these error messages, but chrome keeps working. 

My real problem ist with Emacs 23.1.1 GTK+ Version 2.20.0 on the same machine. It works, but then all of sudden the fonts are totally scrambled in all buffers. It still remains functional, but its impossible to read anything (here is a sreenshot: [http://www.mediafire.com/i/?5e1f6refc4em5jd](http://www.mediafire.com/i/?5e1f6refc4em5jd)).
Emacs is the only application until now affected by this problem. It seems (!) that Emacs works ok in an xterm session (instead of a gnome session), but time will show... 

I tried to fontconfigure and it helped a bit, but the problem always came back. May be it is related to these trouble warnings. 
It is really annoying, I would really would appreciate any hints how to solve it. 


(exe:2658): Gdk-WARNING **: XID collision, trouble ahead

(exe:2658): Gdk-WARNING **: XID collision, trouble ahead

(exe:2709): Gdk-WARNING **: XID collision, trouble ahead

(exe:2709): Gdk-WARNING **: XID collision, trouble ahead

(exe:2709): Gdk-WARNING **: XID collision, trouble ahead
[2615:2615:1454867949:ERROR:chrome/app/chrome_dll_main.cc(234)] Gdk: gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed

---

### Post by shafin on 2010-08-02
How come this thread has only 13 posts and 22000 views?

Hmm, Resident Troll, where are you hiding?

---

### Post by Tristam Green on 2010-08-02
I was disappointed; I expected more Grateful Dead lyrics.

---

### Post by bebop52 on 2010-08-08
The problem seems to be gone after deaktivating the propietary accelerating Nvidia graphics drivers for my Nvidia graphic card.

---

### Post by zoubidoo on 2010-08-28
I routinely get 
```
(qiv:18631): Gdk-WARNING **: XID collision, trouble ahead
```
using qiv (image viewer).

Up-to-date 10.04 on 32 bit hardware.  Intel graphics card (open source driver).

Judging from the other comments, the problem is neither the graphics card nor the application.

---

### Post by handy on 2010-08-28
> **Tristam Green said:**
> I was disappointed; I expected more Grateful Dead lyrics.

Riding that train high on cocaine,
Casey Jones you better watch your speed

---

### Post by dirghrabadia on 2010-09-06
I am still stuck with the problem, on FF 3.6.8. Any help? :?

---

### Post by fibrebiz on 2010-09-12
I get this when I run firefox from the terminal.

Firefox didn't crash, everything worked fine but for some reason, terminal is filled with an abundance of these messages

(<unknown>:6651): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:6651): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:6651): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:6651): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:6651): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:6651): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:6651): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:6651): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:6651): Gdk-WARNING **: XID collision, trouble ahead

...You get the idea.

I'm running the maverick beta, kept up to date.

---

### Post by earlra on 2010-09-15
I get this message when running Thunderbird (3.0.7).  As it is, I have to run Thunderbird in Safe Mode, otherwise I get a segmentation fault.  (I prefer T'bird due to cross-platform compatability as I access from other machines as well).

---

### Post by HrdRok on 2010-10-29
(<unknown>:23954): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:23954): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:23954): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:23954): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:23954): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:23954): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:23954): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:23954): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:23954): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:23954): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:23954): Gdk-WARNING **: XID collision, trouble ahead
NOTE: child process received `Goodbye', closing down



Problem still exist...nothing happened but this was just in my terminal when running firefox from terminal

---

### Post by xaqrox on 2010-11-14
I've been noticing this one too:

(exe:8243): Gdk-WARNING **: XID collision, trouble ahead

When I killed process 8243, I got this message on the terminal:

[1713:1713:86377809747:ERROR:chrome/browser/tab_contents/tab_contents.cc(2040)] Not implemented reached in virtual void TabContents::OnCrashedPlugin(const FilePath&) convert plugin path to plugin name

And a popup yellow bar across the top of my chrome window saying:

The following plug-in has crashed: /opt/google/chrome/libgcflashplayer.so

It appeared in some tabs but not others, I'll try to see if there's a pattern next time.

---

### Post by xaqrox on 2010-11-14
Got it again. This appeared in the terminal:

(exe:8380): Gdk-WARNING **: XID collision, trouble ahead

Then I killed the process and got:

[1713:1713:103805239673:ERROR:chrome/browser/tab_contents/tab_contents.cc(2040)] Not implemented reached in virtual void TabContents::OnCrashedPlugin(const FilePath&) convert plugin path to plugin name
[1713:1713:103805251645:ERROR:chrome/browser/tab_contents/tab_contents.cc(2040)] Not implemented reached in virtual void TabContents::OnCrashedPlugin(const FilePath&) convert plugin path to plugin name
[1713:1713:103805273365:ERROR:chrome/browser/tab_contents/tab_contents.cc(2040)] Not implemented reached in virtual void TabContents::OnCrashedPlugin(const FilePath&) convert plugin path to plugin name
[1713:1713:103805274148:ERROR:chrome/browser/tab_contents/tab_contents.cc(2040)] Not implemented reached in virtual void TabContents::OnCrashedPlugin(const FilePath&) convert plugin path to plugin name

And the yellow bar saying: "The following plug-in has crashed: /opt/google/chrome/libgcflashplayer.so" popped up on the tabs where gmail and the nytimes were open.

---

### Post by xaqrox on 2010-11-14
> **xaqrox said:**
> Got it again. This appeared in the terminal:

(exe:8380): Gdk-WARNING **: XID collision, trouble ahead

Then I killed the process and got:

[1713:1713:103805239673:ERROR:chrome/browser/tab_contents/tab_contents.cc(2040)] Not implemented reached in virtual void TabContents::OnCrashedPlugin(const FilePath&) convert plugin path to plugin name
[1713:1713:103805251645:ERROR:chrome/browser/tab_contents/tab_contents.cc(2040)] Not implemented reached in virtual void TabContents::OnCrashedPlugin(const FilePath&) convert plugin path to plugin name
[1713:1713:103805273365:ERROR:chrome/browser/tab_contents/tab_contents.cc(2040)] Not implemented reached in virtual void TabContents::OnCrashedPlugin(const FilePath&) convert plugin path to plugin name
[1713:1713:103805274148:ERROR:chrome/browser/tab_contents/tab_contents.cc(2040)] Not implemented reached in virtual void TabContents::OnCrashedPlugin(const FilePath&) convert plugin path to plugin name

And the yellow bar saying: "The following plug-in has crashed: /opt/google/chrome/libgcflashplayer.so" popped up on the tabs where gmail and the nytimes were open.
PID 1713 is the earliest instance of chrome. It's /usr/bin/google-chrome, which has on other instance, all the rest are /opt/google/chrome/chrome

---

### Post by DachaArh on 2010-12-10
bump... I too have this problem, when running Firefox via Terminal... Ubuntu 10,10 32 bit... Firefox 3-6-13

---

