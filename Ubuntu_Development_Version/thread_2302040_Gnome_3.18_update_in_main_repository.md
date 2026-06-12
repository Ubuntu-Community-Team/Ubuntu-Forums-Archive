---
title: "Gnome 3.18 update in main repository"
date: 2015-11-07
forum: Ubuntu Development Version
---

### Post by fthx on 2015-11-07
Hi,

I've just upgraded from main repos to GS 3.18. I did not notice any *big* change. Epiphany is still buggy, as usual. Evolution is ok and show a Thunderbird-like "show external content" banner (no more Ctrl-I, good news).
Seems to work flawlessly. Still no Google drive in Nautilus (I don't know why, some updates are probably missing or I miss a package).

---

### Post by grahammechanical on 2015-11-07
We learnt earlier this week at UOS the Ubuntu will be moving to Gnome 3.18 DE during the development period of Xenial (16.04). Gedit is now at 3.18.1 and Gnome 
Shell is also at 3.18.1 according to the software Centre. How much of Gnome 3.20 will get into Xenial by release day is open to doubt. Gnome 3.20 does not become stable until the third week of March 2016.

[https://wiki.gnome.org/ThreePointNineteen](https://wiki.gnome.org/ThreePointNineteen)

Regards.

---

### Post by Mateusz Stachowski on 2015-11-08
> **grahammechanical said:**
> Gedit is now at 3.18.1

Only if you have the proposed repo enabled. Otherwise it's still at the ancient 3.10.4 version just like in any other Ubuntu release.

[http://packages.ubuntu.com/search?keywords=gedit&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=gedit&searchon=names&suite=all&section=all)

---

### Post by syntaxerror74 on 2015-11-09
> **Mateusz Stachowski said:**
> Only if you have the proposed repo enabled. Otherwise it's still at the ancient 3.10.4 version just like in any other Ubuntu release.
Yeah, it's getting ridiculous!!

I hope that at least for the next LTS release (in April 2016) Gedit will have been replaced by a more recent version - even in the vanilla installation.

---

### Post by fthx on 2015-11-09
gedit is now in main, so don't be upset !
:-)

I noticed ONE bug in Xenial-Gnome : when I press on power button, my laptop goes suspend instead of shutdown.

---

### Post by syntaxerror74 on 2015-11-09
> **fthx said:**
> gedit is now in main, so don't be upset !
It's of no interest for me whether gedit is "in main", but only in *what version*!! Mateusz' link gives it away: no main version change for the time span of 4 releases! That IS ridiculous, period.

---

### Post by sammiev on 2015-11-09
> **fthx said:**
> gedit is now in main, so don't be upset !
:-)

I noticed ONE bug in Xenial-Gnome : when I press on power button, my laptop goes suspend instead of shutdown.

Use Tweak Tool to change the setting.

---

### Post by mc4man on 2015-11-09
> **syntaxerror74 said:**
> Yeah, it's getting ridiculous!!

I hope that at least for the next LTS release (in April 2016) Gedit will have been replaced by a more recent version - even in the vanilla installation.
Obviously it will be in 16.04 as it's sitting in the 16.04 proposed repo right now & can be used if desired.
There were solid reasons that gedit could not be upgraded in last couple of Ubuntu releases, if curious then search out.

---

### Post by fjgaude on 2015-11-09
> **mc4man said:**
> Obviously it will be in 16.04 as it's sitting in the 16.04 proposed repo right now & can be used if desired.
There were solid reasons that gedit could not be upgraded in last couple of Ubuntu releases, if curious then search out.

Gee, the gedit is far from finished, not too useful in 16.04, at least in my installation.

---

### Post by fthx on 2015-11-10
> Use Tweak Tool to change the setting.

Yeah, thanks, but these settings are obviously correct.... ;)

---

### Post by fthx on 2015-11-10
> **syntaxerror74 said:**
> It's of no interest for me whether gedit is "in main", but only in *what version*!!

If you read this thread again, you could have understood it was 3.18...

> **fjgaude said:**
> Gee, the gedit is far from finished, not too useful in 16.04, at least in my installation.

What features are missing ?

---

### Post by mc4man on 2015-11-10
> **fthx said:**
> What features are missing ?
feature wise seems ok here though has theming issues in an ubuntu session with default ambiance theme

---

### Post by fthx on 2015-11-10
Yep, I noticed that. With default Gnome's Adwaita, it's perfect in Ub. Gnome.

---

### Post by fjgaude on 2015-11-10
> **fthx said:**
> What features are missing ?

I'm running Unity with Intel video driver and Ambiance GTK theme. Gedit has no menu, with only Save, Open a new file, Create a new document as options. When I try to open an existing document the screen to do so is compressed so that the files are unreadable.

I'm sure this will be fixed as time goes by.

###
Okay, after last update with Intel microcode installed the only thing missing is the screen compressed when Open a new file is used. The menu bar at the bottom shows most of the things one needs to use an editor.

###
I see that even the normal install is getting the new Gedit.

---

### Post by mc4man on 2015-11-10
The combo of gnome 3.18 or higher & ubuntu session/theming seems to be something that won't quite look right, whether someone takes/has the time to address we'll see. Probably has something to do with csd (client-side-decorations.

So currently in an ubuntu session with light themes gedit has no window deco, just a toolbar. If maximized you then get 2 sets of close/min/max buttons. Also seems gnome doesn't support rounded corners well. 
gnome-terminal also shows an inconsistency in upper right corner, no big deal, just not 'right'

Nautilus is currently at 3.14, if it goes to 3.18 likely more 'not quite right's'

---

### Post by sgage on 2015-11-10
> **mc4man said:**
> The combo of gnome 3.18 or higher & ubuntu session/theming seems to be something that won't quite look right, whether someone takes/has the time to address we'll see. Probably has something to do with csd (client-side-decorations.

So currently in an ubuntu session with light themes gedit has no window deco, just a toolbar. If maximized you then get 2 sets of close/min/max buttons. Also seems gnome doesn't support rounded corners well. 
gnome-terminal also shows an inconsistency in upper right corner, no big deal, just not 'right'

Nautilus is currently at 3.14, if it goes to 3.18 likely more 'not quite right's'

Not seeing any of this in Ubuntu Gnome, fully updated as of 19:00 EST.

---

### Post by syntaxerror74 on 2015-11-10
> **mc4man said:**
> There were solid reasons that gedit could not be upgraded in last couple of Ubuntu releases, if curious then search out.
Trust me dude, I did - but I found zilch after all. Maybe I had used the wrong search terms though (this often *does* matter these days)

---

### Post by fthx on 2015-11-14
We'll have to wait for gvfs 1.26 (does exist in Sid, atm) to get Google Drive support.

It seems that the power button issue will be solved in gnome settings daemon that is present in proposed (refering to Gnome's official changelog).

---

### Post by kurt18947 on 2015-11-14
> **syntaxerror74 said:**
> Yeah, it's getting ridiculous!!

I hope that at least for the next LTS release (in April 2016) Gedit will have been replaced by a more recent version - even in the vanilla installation.

I 'fixed' Gedit by installing Mousepad :D.

---

### Post by monkeybrain20122 on 2015-11-23
> **mc4man said:**
> 
Nautilus is currently at 3.14, if it goes to 3.18 likely more 'not quite right's'

I am wondering which nautilus will be shipped with 16.04. Get 3.18 in Fedora 23. It is a real pain to use. No more permanently delete option, even the delete button sends files to trash so there is no way to delete without passing through trash, have to delete everything twice.[https://bugzilla.gnome.org/show_bug.cgi?id=756637#c5](https://bugzilla.gnome.org/show_bug.cgi?id=756637#c5)   Just noticed that I have run out of diskspace on the small Fedora partition because I have 10G in trash which I thought have deleted with the delete button. Other shocker is if show hidden file with ctrl + h once then hidden file always show until you uncheck the option manually.  

On other note gnome-session properties aka startup applications is not around anymore, probably not around since 3.16 and instead have to use gnome-tweak tool but it only shows applications with .desktop files so if you want to run a command at start up instead of just entering a command you have to make a desktop file maybe plus a bash script. 

They are wrecking it upstream. It is a usability nightmare.

---

### Post by mc4man on 2015-11-23
> **monkeybrain20122 said:**
> I am wondering which nautilus will be shipped with 16.04. Get 3.18 in Fedora 23. It is a real pain to use.

They are wrecking it upstream. It is a usability nightmare.
Without some significant patching it'll be even worse in 16.04 in an ubuntu session. csd & GtkHeaderBar have no place in 16.04 Ubuntu if their poor effect in Ubuntu can't be negated

 At least upstream recently came to their senses about the DnD hover opening the dir. hovered over in canvas view (icon). At first they reverted that nonsense, now have brought back as a gsettings option, default disabled. 
In general the last couple of years Gnome seemed to make many commits aimed towards mobile use. Maybe one of their lead dev's was 'auditioning' for the job he ([Cosimo Cecchi]("https://endlessm.com/about-us/#row-3")) recently got at ... 
[http://www.endlessm.com/](http://www.endlessm.com/)

---

### Post by monkeybrain20122 on 2015-11-24
> **mc4man said:**
> Without some significant patching it'll be even worse in 16.04 in an ubuntu session. csd & GtkHeaderBar have no place in 16.04 Ubuntu if their poor effect in Ubuntu can't be negated


Well enough of this bs, in Fedora I just installed nemo and made it the default, sanity restored. Perhaps it is easier to patch nemo for Unity instead of battling gnome upstream's ongoing sabotage of user experience? Afterall nemo is just a fork of the old nautilus before upstream lost its mind. IIRC there is a patched version of nemo for unity in webupd8's ppa which doesn't pull in other Cinnamon dependencies. I tried it back in 13.04 or 13.10 and it was a bit glitchy but it is probably working better now.

---

### Post by philinux on 2015-11-24
> Ubuntu GNOME 16.04 LTS is getting GNOME 3.19

It was to be expected for Ubuntu GNOME 16.04 LTS to ship with GNOME 3.20, so it’s not really a surprise that the devs are starting to upload the GNOME 3.19 packages for the daily builds.

[http://news.softpedia.com/news/ubuntu-gnome-16-04-lts-gets-first-gnome-3-19-packages-for-daily-build-496640.shtml](http://news.softpedia.com/news/ubuntu-gnome-16-04-lts-gets-first-gnome-3-19-packages-for-daily-build-496640.shtml)

---

### Post by fthx on 2015-11-24
We now have new systemd  gnome-logs and new gvfs/goa with Google Drive support. Seems to work !

---

