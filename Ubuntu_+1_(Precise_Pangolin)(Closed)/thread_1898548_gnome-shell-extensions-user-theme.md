---
title: "gnome-shell-extensions-user-theme"
date: 2011-12-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by SushiR on 2011-12-21
I'm running a freshly installed Precise with no further ppa added. How can I change the shell-theme?

---

### Post by paul_in_london on 2011-12-21
If you have the universe repo enabled on a vanilla precise install you should (AFAIK) just be able to do:

```
sudo aptitude install gnome-tweak-tool
```

and use that to manage/install extensions.

There's a GS extensions website which you **may** be able to use to install some extensions using firefox:

```
webupd8.org/2011/12/gnome-shell-extensions-website-launched.html
```

Was having a look around to see if the **gnome-shell-extensions** and **gnome-shell-extensions-user-theme** packages are available in the main repos (i.e. without adding a ppa), but I'm not sure that they are right now.

If you don't mind adding a ppa you could do:

```
sudo add-apt-repository ppa:ricotz/testing
sudo aptitude update
```
and ```
sudo aptitude safe-upgrade
``` or ```
sudo aptitude full-upgrade
```

(which is the ppa I'm using) and then:

```
sudo aptitude install gnome-shell-extensions
``` or:

```
sudo aptitude install gnome-shell-extensions-user-theme
```

Then have a look at this page (shows how to reload GS and how to use gnome tweak tool):

[techdrivein.com/2011/10/how-to-install-and-manage-gnome-shell.html](techdrivein.com/2011/10/how-to-install-and-manage-gnome-shell.html)

---

### Post by lonniehenry on 2011-12-21
Gnome3 gnome-shell extensions can be found at [https://extensions.gnome.org/?](https://extensions.gnome.org/?) and added just by turning on the ones you want to add. Very simple and works.  No special ppa needed.  I have used ricotz and the webupd8 ppas in the past but have had problems.  Going to extension.gnome.org gives more extensions with no problems.

---

### Post by paul_in_london on 2011-12-21
> **lonniehenry said:**
> Gnome3 gnome-shell extensions can be found at [https://extensions.gnome.org/?](https://extensions.gnome.org/?) and added just by turning on the ones you want to add. Very simple and works.  No special ppa needed.  I have used ricotz and the webupd8 ppas in the past but have had problems.  Going to extension.gnome.org gives more extensions with no problems.

Yes, apologies to the OP or anyone else for any confusion - that's the page I was talking about in my previous post.

---

### Post by SushiR on 2011-12-22
> **lonniehenry said:**
> Gnome3 gnome-shell extensions can be found at [https://extensions.gnome.org/?](https://extensions.gnome.org/?) and added just by turning on the ones you want to add. Very simple and works.  No special ppa needed.  I have used ricotz and the webupd8 ppas in the past but have had problems.  Going to extension.gnome.org gives more extensions with no problems.

Should have mentioned before that I know about the extensions website. But unfortunately the theme extension cannot be installed because of my GS version.

---

### Post by paul_in_london on 2011-12-22
> **SushiR said:**
> Should have mentioned before that I know about the extensions website. But unfortunately the theme extension cannot be installed because of my GS version.

I also have extensions installed that I'm unable to use because they're incompatible with my GS version from the ricotz-testing ppa. I can't remember if the **gnome-shell-extensions-user-theme** is one of the ones which is not working. I can't check that right now, but I'll confirm later.

---

### Post by creata.physics on 2012-03-06
Has anybody found a fix for this issue? I'm having the same problem and would like this extension since my theme is all messed up on default.

---

### Post by bmbaker on 2012-03-07
the extensions from ricotz/testing ppa are for the G-S version installed from  the testing ppa.
i can confrim that they are wking fine :-)

---

### Post by creata.physics on 2012-03-07
I've installed the extension as well, but when I enable it and go to themes from the tweak tool I still don't have access to the shell theme, it's all greyed out.  is there something else I need to install?

---

### Post by bmbaker on 2012-03-07
you should have gnome-shell gnome-shell-extensions and gnome-shell-extensions-common installed.

perhaps try reinstalling them!

```
sudo aptitude reinstall gnome-shell gnome-shell-extensions gnome-shell-extensions-common gnome-tweak-tool
```

---

