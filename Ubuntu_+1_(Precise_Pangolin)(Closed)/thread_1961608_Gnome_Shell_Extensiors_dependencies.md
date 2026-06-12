---
title: "Gnome Shell Extensiors dependencies"
date: 2012-04-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ayozito on 2012-04-19
Today I got an update that said that the better for does it was make a partial update because some package are no longer needed.

I noticed now that Gnome Shell Extensions aren't working, look at tweak-tool and I see that they are all disabled. Go to Software Center and they are all uninstalled...

I tried install them (well... it, because I only use the alternative status menu) and the installation failed due to dependencies.

I tried adding the webupd8 repository again, but nothing, can't install it back.

How can I install it again? or change manual the shutdown menu.

---

### Post by forrestcupp on 2012-04-19
> **ayozito said:**
> Today I got an update that said that the better for does it was make a partial update because some package are no longer needed.

I noticed now that Gnome Shell Extensions aren't working, look at tweak-tool and I see that they are all disabled. Go to Software Center and they are all uninstalled...

I tried install them (well... it, because I only use the alternative status menu) and the installation failed due to dependencies.

I tried adding the webupd8 repository again, but nothing, can't install it back.

How can I install it again? or change manual the shutdown menu.

It's more than likely because you've updated to a version of Gnome Shell that the extensions don't support yet. If that's the case, you'll either have to wait until they update the extensions for the new version, or edit all of the metadata.json files with your version of Gnome Shell, and hope they're compatible.

---

### Post by soro2005 on 2012-04-19
Most of the extensions are now on [http://extensions.gnome.org](http://extensions.gnome.org) . Go there with Firefox or Epiphany, and you can install them with the click of a button. You may have to uninstall the old versions first, though.

---

### Post by BigCityCat on 2012-04-19
Yes gnome extensions from the website are working but after they are installed you can't open gnome tweak tool anymore. Unless you locate to home/.local/share/gnome-shell and delete the extensions folder. You can then open gnome tweak tool. At least on my computer anyway.

---

### Post by marrok1 on 2012-04-19
I had the same problem with opening gnome-tweak-tool. Executing gnome-tweak-tool from the terminal showed that it was looking for gnome-shell-exensions-user-themes but it was no longer available. Just a quick uninstall and re-install of gnome-tweak-tool solved all my issues.

---

### Post by BigCityCat on 2012-04-19
Thanks but that didn't do it form me. Oops yes it did.

---

### Post by ayozito on 2012-04-20
Without change nothing, I have installed it from that web and still I can open the Gnome Tweak Tool.

---

### Post by jjcv on 2012-04-21
> **marrok1 said:**
>  Just a quick uninstall and re-install of gnome-tweak-tool solved all my issues.

This worked for me.  Great and thanks.

---

