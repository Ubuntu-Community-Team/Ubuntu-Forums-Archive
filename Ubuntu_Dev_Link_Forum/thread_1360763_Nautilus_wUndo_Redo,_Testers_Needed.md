---
title: "Nautilus w/Undo Redo, Testers Needed"
date: 2009-12-21
forum: Ubuntu Dev Link Forum
---

### Post by mriya3 on 2009-12-21
Hello,
I've implemented undo-redo support for nautilus (2.28... but it should work also for the current development version 2.29), see [https://bugzilla.gnome.org/show_bug.cgi?id=167501](https://bugzilla.gnome.org/show_bug.cgi?id=167501) 
(for a video of the undo-redo in action see [http://www.youtube.com/watch?v=YCf94_p2SyA](http://www.youtube.com/watch?v=YCf94_p2SyA) )

Edit: I've set up a PPA with packages for Lucid (2.29) and Karmic (2.28)

[https://launchpad.net/~mriya3/+archive/ppa](https://launchpad.net/~mriya3/+archive/ppa)

I would like to ask you to try it out and give me some feedback.

Thank you very much for your help!

:):):)

[SIZE="4"]Important[/SIZE]
**Because this feature is still being worked on, please avoid using it on production machines and on important data... Additionally, as the GPL licence says "This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details."**

---

### Post by nilarimogard on 2010-01-10
Works great, thank you! I posted it on my blog: [http://www.webupd8.org/2010/01/download-undo-redo-patched-nautilus.html](http://www.webupd8.org/2010/01/download-undo-redo-patched-nautilus.html)

Hope that's ok.

---

### Post by NFblaze on 2010-01-10
I cant seem to get it to work, I've installed on two differnet machines but I have not seen the "Undo" or "Redo" buttons. Is a restart required?

---

### Post by Locke_99GS on 2010-01-10
You'll have to reload Nautilus to get this. Since Nautilus draws your wallpaper, it is usually running, even without any windows open. Just restart X.

---

### Post by NFblaze on 2010-01-11
Yes, I figured. I eventually reloaded/restarted. It's just that I was so used to not doing that since I haven't used Windows for such a long while. Anyway, it's up and running...

---

### Post by habtool on 2010-01-13
> **mriya3 said:**
> Hello,
I've implemented undo-redo support for nautilus (2.28... but it should work also for the current development version 2.29), see [https://bugzilla.gnome.org/show_bug.cgi?id=167501](https://bugzilla.gnome.org/show_bug.cgi?id=167501) 
(for a video of the undo-redo in action see [http://www.youtube.com/watch?v=YCf94_p2SyA](http://www.youtube.com/watch?v=YCf94_p2SyA) )

I would like to ask you to try it out and give me some feedback.

You can find nautilus packages (2.28.1 for ubuntu 9.10) compiled with the undo-redo patch at:
[SIZE="3"]
[http://www.fuzzbug.com/nautilus](http://www.fuzzbug.com/nautilus)[/SIZE]

(download the deb files and install them with 'sudo dpkg -i *.deb')

Thank you very much for your help!

:):):)

[SIZE="4"]Important[/SIZE]
**Because this feature is still being worked on, please avoid using it on production machines and on important data... Additionally, as the GPL licence says "This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details."**


Are you thinking of putting these into a PPA on launchpad?

---

### Post by mriya3 on 2010-01-13
Yes, I'm looking to do that in the next days. I have to check if I can stick to ubuntu's nautilus package releases, and as I've currently switched to gnome 2.29 (git), the available packages will probably only work in lucid.

;)

---

### Post by habtool on 2010-01-13
> **mriya3 said:**
> Yes, I'm looking to do that in the next days. I have to check if I can stick to ubuntu's nautilus package releases, and as I've currently switched to gnome 2.29 (git), the available packages will probably only work in lucid.

;)


Thanks for the reply and do keep up the good work.

I am also booting into Lucid on one of my partitions, so will keep an eye out.

Would be nice to see this implemented upstream too :)

Stay Well

---

### Post by habtool on 2010-01-13
I have no idea how PPA's work in launchpad, but for some reason I pictured that you supply the source and they have build servers that build the packages for the versions of Ubuntu that it can work on, or something to this extent.

But this may be me sucking my thumb and talking complete nonsense!

---

### Post by shakaran on 2010-01-13
Great feature!

This should be merged on Nautilus by default!

---

### Post by drvista on 2010-01-14
Hi all . Nautilus by far is perfect but needs some tweaks >>>
i have managed to find another different project out there to tweak nautilus but works alone.
1. combine refresh and stop buttons .. patch from simplified nautilus
[http://davidsiegel.org/nautilus-simplified/](http://davidsiegel.org/nautilus-simplified/)
not all the patch but only the combination of reload and stop buttons
3. add undo and redo options from this thread
[http://ubuntuforums.org/showthread.php?t=1360763](http://ubuntuforums.org/showthread.php?t=1360763)

---

### Post by nilarimogard on 2010-01-14
Unfortunately, the Simplified Nautilus (1) no longer works...

---

### Post by mriya3 on 2010-01-15
Hello,
I've set up a ppa for Lucid (nautilus 2.29.1)

[https://launchpad.net/~mriya3/+archive/ppa](https://launchpad.net/~mriya3/+archive/ppa)

I'll try to backport the patch to nautilus 2.28.1 for Karmic.

enjoy :)

;)

---

### Post by joanrc93 on 2010-01-15
It's a great feature.
But, can I use this with an AMD 64 processor?

---

### Post by mriya3 on 2010-01-15
> **joanrc93 said:**
> It's a great feature.
But, can I use this with an AMD 64 processor?

yes :)

amd64 packages are in the ppa

---

### Post by nilarimogard on 2010-01-19
Any idea how to patch [Nautilus Elementary]("http://www.webupd8.org/2010/01/nautilus-elementary-simplified-nautilus.html")? I tried using your patch but it doesn't work since it's a different Nautilus version...

---

### Post by ammonkey on 2010-01-19
Nice patch, sad to see a hootie like this rejected from upstream for what 2-4 years now? i added your patch to [nautilus-elementary]("http://gloobus.wordpress.com/2010/01/18/nautilus-simplified-gloobus-is-dead-long-live-to-nautilus-elementary/")

---

### Post by nilarimogard on 2010-01-19
Already using it, thank you! :D

---

### Post by telaengancho on 2010-02-11
hi mriya3, i'm trying to compile nautilus with your patch, but i can't use it. it seems to be incompatible with version 2.28.4. Can you take a look to the patch? i ask you for that becouse i don't know how to program.
and sorry about my english, still learning

---

### Post by Locke_99GS on 2010-02-11
I've been using this patch (and a few other patches along with it) on Nautilus 2.28.4 for some time now. While I can't say I've had much opportunity to use Undo/Redo, I can say that the patch hasn't caused any apparent instabilities or other issues with Nautilus as a whole.

---

### Post by bocke on 2010-03-07
Thanx. I'll try it on my Fedora box too. I tought they were talking about official undo/redo implementation in 3.0, but thanx god (and yourself) we don't have to wait another year to get f-ing undo in gnome. ](*,)

Btw:
> **Locke_99GS said:**
> You'll have to reload Nautilus to get this. Since Nautilus draws your wallpaper, it is usually running, even without any windows open. Just restart X.

This could also work.
```
killall nautilus
```

---

### Post by Killigrew on 2010-03-21
hi

absolutely great word but
can you please update your ppa against latest lucid version?

greetings

---

### Post by telaengancho on 2010-05-08
I've used the patch in your ppa, and i made it works, so, suddenly i'll upload the PKGBUILd for archlinux
I've founded some bugs, but nothing important.

---

### Post by drvista on 2010-05-08
please can you patch nautilus elementary .. and create a PPA for it ... some of us uses it because of better look and design 
[IMG]http://img695.imageshack.us/img695/3571/53621993.jpg[/IMG]

---

### Post by Killigrew on 2010-05-10
Yes please, i would like to see that, too

greetings :)

---

### Post by telaengancho on 2010-05-10
the pkgbuild for nautilus 2.28.4 is working: [http://aur.archlinux.org/packages.php?ID=37121](http://aur.archlinux.org/packages.php?ID=37121)
but i can't make it work with the elementary or 2.30 version, sorry.

---

### Post by OzzyFrank on 2010-05-21
Anyone know if someone is working on a plugin/extension for this? Or if the Nautilus developers are planning to ever implement this? I've seen posts going pack 3 years asking for this to be a standard feature, and amazingly it still hasn't happened. Hate to admit Windows Explorer is superior in that respect.

---

### Post by nilarimogard on 2010-05-25
Are you still maintaining this patch? If not, please do... a lot of people love it: [http://www.webupd8.org/2010/05/nautilus-elementary-re-adds-undo-redo.html]("http://www.webupd8.org/2010/05/nautilus-elementary-re-adds-undo-redo.html")

---

### Post by nilarimogard on 2010-05-25
> **drvista said:**
> please can you patch nautilus elementary .. and create a PPA for it ... some of us uses it because of better look and design 


The latest Nautilus Elementary has this patch by default (see the link in my comment above).

---

### Post by NFblaze on 2011-01-22
Any updates on this?

---

