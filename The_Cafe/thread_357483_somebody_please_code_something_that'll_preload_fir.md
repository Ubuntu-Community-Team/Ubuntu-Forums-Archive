---
title: "somebody please code something that'll preload firefox..."
date: 2007-02-09
forum: The Cafe
---

### Post by bionnaki on 2007-02-09
...surely it cannot be that difficult. Konqueror has the ability. Opera can load from the system tray. Why not firefox? You'll be the hero of many.

---

### Post by kerry_s on 2007-02-09
Try this->

sudo gedit /etc/rc.local

put

sudo -u user find /usr/lib/firefox ! -type d | xargs cat > /dev/null &
sudo -u user  find /home/user/.mozilla/firefox ! -type d | xargs cat > /dev/null &

Replace "user" (3 spots)with your name.

---

### Post by seijuro on 2007-02-09
or this

```

sudo apt-get install preload

```

---

### Post by kerry_s on 2007-02-09
> **seijuro said:**
> or this

```

sudo apt-get install preload

```

Preload can actually make a system slower than it was.

---

### Post by bionnaki on 2007-02-10
yes. I have preload and readahead installed. my system is quite fast, but loading firefox is always slow loading.

I edited /etc/rc.local has suggested and rebooted, but it did not help. load time was exactly the same as before.

hmmm. surely this is possible to have firefox load as quickly as konqueror (due to preloading an instance).

---

### Post by qalimas on 2007-02-10
> **bionnaki said:**
> hmmm. surely this is possible to have firefox load as quickly as konqueror (due to preloading an instance).

The reason Konqueror loads so fast is mainly because it uses many of the KDE libs already loaded into RAM.  That would be the same reason IE loads so quickly.

Firefox looks like it tries to do it all on it's own, no integration into GNOME or anything like that.

Maybe something more along the lines of the OpenOffice preloader is in order for Firefox?

---

### Post by bionnaki on 2007-02-10
sure, why not? whatever works. windows has this: [https://sourceforge.net/projects/ffpreloader/](https://sourceforge.net/projects/ffpreloader/)

all I want is firefox to open immediately. And if I click on a firefox icon while it is preloaded/loaded into the system tray, I only want *one window* to open (as is the problem with alltray'ing firefox).

---

### Post by kerry_s on 2007-02-10
> **bionnaki said:**
> yes. I have preload and readahead installed. my system is quite fast, but loading firefox is always slow loading.

I edited /etc/rc.local has suggested and rebooted, but it did not help. load time was exactly the same as before.

hmmm. surely this is possible to have firefox load as quickly as konqueror (due to preloading an instance).

Try uninstalling preload. Do you have alot of extensions in firefox? How much ram?

---

### Post by bionnaki on 2007-02-10
why uninstall preload? honestly, preload does make my system speed up or slow down. might as well keep it.

I only have 3 or 4 extensions and I run a lean system (commandline install + kde-core + many tweaks such as these: [http://murl.net/vi](http://murl.net/vi) ). I have 1 gig of RAM. Nevertheless, firefox still takes time to load. Even on my Arch linux partition, firefox takes several seconds to load and my harddrive has to spin up. Konqueror loads instantly due to preloading instances of itself. Seems like it would be easy to create some preload**er** (not *preload*) like OpenOffice, w32 firefox, and Konqueror have.

---

### Post by kerry_s on 2007-02-10
There is one project i came across that does exactly that, the thing is it's for kde. I took a look at it sometime back, but didn't dig deeper. Perhaps some of the coding genius's could take a look and maybe modify it to work with gnome.
-> [http://mozillaqs.sourceforge.net/](http://mozillaqs.sourceforge.net/)

As for me i use xubuntu and with my little script my firefox opens as soon as i click on it.

The preloader might be messing up that script and it's easy to reinstall, so why not give it a shot.

---

### Post by kinematic on 2007-02-10
> **bionnaki said:**
>  all I want is firefox to open immediately.

that's what i want too!
those 2-3 seconds it takes to load firefox from cache always seems like an eternity :rolleyes: 
i usually go out for a drive or something while it loads ;)

---

### Post by bionnaki on 2007-02-10
I removed preload
and rebooted to be safe.

firefox still takes several moments to load. no difference.

I'll try that app from [http://mozillaqs.sourceforge.net](http://mozillaqs.sourceforge.net)
but I doubt that'll be stable considering it was last updated in 2005.

hmmm...

---

### Post by Brainfart on 2007-02-10
Just don't ever close FF... that's what I do \\:D/

---

### Post by casaschi on 2007-02-10
I find it very simple and efficient to launch the following command
```
alltray firefox
```
as one of the session startup commands.
In this way, as soon as you login, firefox gets loaded and sits in your tray notification area.

A quick search in the forum will tell you how to install alltray if not found in the repos.

---

### Post by shining on 2007-02-10
> **Brainfart said:**
> Just don't ever close FF... that's what I do \\:D/

Even if you don't close it, it doesn't solve the problem, because it's only the first time which takes really long. And you still need to launch it once.

---

### Post by bionnaki on 2007-02-10
I dont really like the alltray hack. 

I wish someone could pickup the code from the firefox/mozilla preloader thats up on sourceforge.

---

### Post by Panama2305 on 2010-01-15
Hi friends!!!

I have a way to do this... As everybody know, if you have activated the option to save the screen when you shutdown, this will keep every single window or application that you have open before shutdown or restart, so, based on this I figured out that if I have mi firefox open before shutdown I will have the firefox open when I logon again, but I didn't wanna have the firefox window open whe I logon (and I thing nobody want this either) and knowing that firefox have an extension to minimize firefox (FireTray) to the system tray I instaled this extension and minimized one window to the system tray and keep it there and everytime I logon I have mi firefox running and this make a new firefox's window open faster, because actually firefox is already running. The window at the tray have a blank page open. This method is working perfectly for me and is doing the function of Firefox Preloader do in windows...

Hope this could help you...

Note: I also have installed the PRELOAD through apt-get install preload. Whit these two appication firefox is going to open faster than ever...

[IMG]http://img686.imageshack.us/img686/576/snapshot1n.png[/IMG]
Here the Firefox running at the system tray

[IMG]http://img686.imageshack.us/img686/6748/snapshot2y.png[/IMG]
And here you can see Firefox's new window open and the previous Firefox's windows running at the system tray.

[Download FireTray]("https://addons.mozilla.org/en-US/firefox/downloads/latest/4868/platform:2/addon-4868-latest.xpi?src=addondetail") <--------- Click there...


My distro is Kubuntu Netbook 9.10 Karmic Koala

---

### Post by TyrantWave on 2010-01-15
This topic is almost 3 years old.

Necro much?

---

### Post by sydbat on 2010-01-15
> **TyrantWave said:**
> This topic is almost 3 years old.

Necro much?What?? It sounds like you have a problem with Thredcromancy...

---

### Post by d3v1150m471c on 2010-01-15
let me get this right... all you need to do is put an icon on your panel to launch firefox?. I'm not savvy with kde but there is probably something in the properties of the default icon to change it to firefox. If not you can probably drag and drop firefox onto the panel.

---

### Post by cariboo on 2010-01-15
This thread is three years old. If you have new info, please start a new thread. Thread closed.

---

