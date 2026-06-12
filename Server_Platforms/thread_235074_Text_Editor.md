---
title: "Text Editor"
date: 2006-08-12
forum: Server Platforms
---

### Post by lugos on 2006-08-12
I've installed Ubuntu Server 6.06 and the xubuntu desktop.  I want to edit the menu.lst.  Does xubuntu desktop come with a text editor?  If not, is there a way I can install one?

Any help would be greatly appreciated.

Thanks,
lugos

---

### Post by jordilin on 2006-08-12
Vi/Vim is always installed in any Linux/Unix distro. So, I'm quite sure you'll have vim available.

---

### Post by lugos on 2006-08-12
Do you know of any graphical text editors?  I tried gedit, but I don't think that's installed by default.

---

### Post by jordilin on 2006-08-12
If you are in a server, you'll have to learn vi. Mostly if you access it remotely by means of ssh. In the Ubuntu server edition there is no graphical window managers. It's all about the command line :grin: 
As for the xubuntu, I can't tell you because I only use Gnome :wink:

---

### Post by ajgreeny on 2006-08-12
If you want a lightweight GUI try xfce; on my machine which already has both gnome and kde it would mean a download of only 9Mb, though it may be a lot more on a server install.  You could also try xubuntu-desktop, a metapackage which installs the packages needed for a xubuntu set-up.  Both will end up very similar and could be good for use if you're not keen on the command line all the time.

---

### Post by junglepeanut on 2006-08-13
Since you have xubuntu-desktop you should have mousepad, the xfce text editor. The only thing not fast about opening and using it is...you have to type mousepad instead of four letters like some of the other editors.

no syntax highlighting, just a simple editor.

you can install any of the others.

As mentioned above vim is also installed. I have tried vim and emacs many times, I think they are editors that even if you want to learn (for me at least) are hard to get past the first stages...until you need to use vim i.e. you have a server. Thats what forced me to spend some time really learning.

My biggest mistakes.... the colon. Never saw it. kept hitting q and nothing happened. I was so pissed. Tried other commands nothing ever happened until finaly something would happen and I had no idea how I did it. Trust me fight through it, it is worth it. I think my typing speed is even increasing from vim.

---

### Post by stormblue on 2006-08-13
I would reccommend nano, which is a pico clone. It's on (x)(k)ubuntu, so it'll always be there.  You can learn vi/vim if you want, although, I agree it's a pain.  For a lightweight GUI text editor I'd reccomend SciTE.  It's in the repo's.

---

### Post by slakkie on 2006-08-13
> **stormblue said:**
> You can learn vi/vim if you want, although, I agree it's a pain.  
They have an excelent tutorial for vim teaching you the basics. I would recommend this.

---

