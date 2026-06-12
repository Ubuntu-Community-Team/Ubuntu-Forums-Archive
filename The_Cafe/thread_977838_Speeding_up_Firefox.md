---
title: "Speeding up Firefox"
date: 2008-11-10
forum: The Cafe
---

### Post by elmer_42 on 2008-11-10
I just read an interesting topic on the Arch forums, and I've taken two actions that seem to have dramatically increased the rendering speed of Firefox. After applying the following edits, Firefox seems to be much faster to me. By the time I open a page in a new tab and switch to it, it has already been loaded.**NOTE: Whatever you do to your system is your own fault, don't blame me for it. I offer this tip with no warranty whatsoever.**

First, I backed up the files I would need to edit.
```
cp ~/.bashrc ~/.bashrc_bak
sudo cp /etc/X11/xorg.conf ~/xorg.conf
```
Next, I added the following to my ~/.bashrc (I hear that if you use GDM you need to add it to /etc/profile). This disables Pango, which is a library for laying out and rendering of text. If after doing this your fonts look weird, do not hesitate to restore your backup with [FONT="Courier New"]cp ~/.bashrc_bak ~/.bashrc[/FONT]. However, my fonts did not change at all.
```
export MOZ_DISABLE_PANGO=1
```
Finally, I added the following to the section of /etc/X11/xorg.conf that referred to my graphics card. This is usually recommended for ATI cards, but there have been a few nVidia users (including myself) who have used it. Sometimes some pages with heavy graphics do not look right after doing this. This did not happen to me, but I have found a few cases where it did. If this happens to you, you can revert to your backup with [FONT="Courier New"]sudo cp ~/xorg.conf /etc/X11/xorg.conf[/FONT]. **NOTE: This edit is not as important as the other; in fact it is more risky and has less of a payoff.**
```
        Option       "MigrationHeuristic" "greedy"
```
After editing these files you will need to restart X (Ctrl+Alt+Backspace, then run startx)

---

### Post by shadowdude1794 on 2008-11-10
I'm iffy to try this, just because I don't know what this is changing. Could you describe what each edit does? Can someone confirm that this works?

---

### Post by elmer_42 on 2008-11-10
Oh, sorry about that. I added a short explanation to each one. Also, if you back up your stuff, there really is nothing to worry about.

---

### Post by aktiwers on 2008-11-10
I dont seam to feel any change doing these things, but adding
export MOZ_DISABLE_PANGO=1 

to .bashrc really did speed things up.. Thanks!

---

### Post by binbash on 2008-11-10
> **aktiwers said:**
> I dont seam to feel any change doing these things, but adding
export MOZ_DISABLE_PANGO=1 

to .bashrc really did speed things up.. Thanks!

Same here : )

---

### Post by wesley_of_course on 2008-11-10
Thanks I had forgot were I'd seen that ! [URL="http://ubuntuforums.org/showthread.php?t=615473"]http://ubuntuforums.org/showthread.php?t=615473 
[/URL]

---

### Post by elmer_42 on 2008-11-10
> **wesley_of_course said:**
> Thanks I had forgot were I'd seen that ! [URL="http://ubuntuforums.org/showthread.php?t=615473"][link]
[/URL]
Well, that's not the first place I saw it, but I eventually found it in search of a reason for disabling Pango increasing speed so much.

---

### Post by chucky chuckaluck on 2008-11-10
damn!

---

### Post by kernelhaxor on 2008-11-10
Cool .. renders much faster now .. Thanks, mate!

---

### Post by RiceMonster on 2008-11-11
Cool, this solved the rendering problem with firefox while using a compositor. It would distort for a second when I switched into a workspace with firefox opened.

---

### Post by elmer_42 on 2008-11-11
I'm glad I could help you all. I've tried finding a reason for the xorg.conf edit, and I can not find one, so I'm editing the first post.

---

### Post by ellalan on 2008-11-11
I have increased the FF speed with following method:
about:config
Network.http.pipelining- changed to "true" from "false"
Network.http.proxy.pipelining- changed to "true" from "false"
Network.http.pipelining.maxrequest-changed from 4(default) to 200.

It works well for me but when you do these changes please make a note of the original settings and back up your data. Hope this help someone.



EDIT.
Hi Friends,
Just ignore this post, its useless and it broke the sound. Sorry for posting without verifying the validity of this tweaking.

---

### Post by shadowdude1794 on 2008-11-11
Thanks elmer_42! I'll try this when I get home.

---

### Post by elmer_42 on 2008-11-11
> **shadowdude1794 said:**
> I'll try this when I get home.
If you do, post the results, I hope it works out well for you.

---

### Post by Lord Xeb on 2008-11-11
try these they worked for me

---

### Post by TwiceOver on 2008-11-11
Much better here also!  Thanks!

---

### Post by elmer_42 on 2008-11-12
> **Lord Xeb said:**
> try these they worked for me
I found those in [three]("http://ethicalgurus.com/yes-firefox-is-already-pretty-damn-fast-but-did-you-know-that-you-can-tweak-it-and-improve-the-speed-even-more/") [other]("http://jaiminworld.wordpress.com/2008/09/23/firefox-speed-tweaks/") [places]("http://www.hungry-hackers.com/2008/09/firefox-speed-tweaks.html"). They are tweaks in the way Firefox downloads pages, which may increase the speed. However, I believe that people on different connection speeds may notice different changes in the speed of Firefox, which is not the case when tweaking the way Firefox renders.

For all you speed-freaks who use JS-intensive sites (GMail, Facebook, AJAX-enabled sites) you should be looking forward to Firefox 3.1. It includes the TraceMonkey JavaScript engine, which is significantly faster than the current JavaScript engine in Firefox. If you want, you can try it out in the beta version of Firefox, found [here]("http://www.mozilla.com/en-US/firefox/all-beta.html"). Be warned, though, it's beta software, so it's not going to be entirely stable. Most users are recommended to keep using the latest stable version of Firefox until Firefox 3.1 becomes stable.

---

