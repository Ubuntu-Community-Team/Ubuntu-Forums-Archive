---
title: "Any known list of CLI packages in Ubuntu?"
date: 2011-01-09
forum: The Cafe
---

### Post by themarker0 on 2011-01-09
I'm going through making a slightly more newb friendly remix, just wondering if anyone compiled a list of CLI programs in Ubuntu 10.10?

---

### Post by red_Marvin on 2011-01-09
Depends on what you mean with programs/packages;
is it basic terminal stuff like [COLOR="DarkGreen"]ls cd cat grep [/COLOR] a little more involved stuff like [COLOR="DarkGreen"]sed awk[/COLOR]
or bigger programs as [COLOR="DarkGreen"]vi/vim emacs mpd/ncmpc links/lynx/w3m[/COLOR]
IE basic stuff present on any linux distribution for system management, or more like user oriented every day programs that happen to run in cli?

But I don't think that there is such a list.

If you are looking for terminal programs, there is a (ubuntu derivative I think) distro targeted for cli use, Crunchbang I think it's called--never used it though.

---

### Post by juancarlospaco on 2011-01-09
Theres a category like that on Synaptic...

---

### Post by jerenept on 2011-01-09
> **juancarlospaco said:**
> Theres a category like that on Synaptic...

AFAIK, those are packages related to Mono and not the command line.

---

### Post by juancarlospaco on 2011-01-09
> **jerenept said:**
> AFAIK, those are packages related to Mono and not the command line.

Not that one...

---

### Post by Firestem4 on 2011-01-09
Open a terminal window and hit tab, 90% of the commands that show up should be Command-Line only :)

---

### Post by Megaptera on 2011-01-10
Is CLI Companion in Launchpad any help? Quote "CLI Companion is a tool to store and run Terminal commands from a GUI. People unfamiliar with the Terminal will find CLI Companion a useful way to become acquainted with the Terminal and unlock its potential. Experienced users can use CLI Companion to store their extensive list of commands in a searchable list."

[https://launchpad.net/clicompanion](https://launchpad.net/clicompanion)

---

### Post by duanedesign on 2011-01-10
You can find CLI Companion's Launchpad page here:

[https://launchpad.net/clicompanion](https://launchpad.net/clicompanion)

You can install CLI Companion with the following commands:

To get the deb:
```
wget http://launchpad.net/clicompanion/1.0/1.0rc2/+download/clicompanion_1.0-3.1_all.deb

```
To install the deb:
```
dpkg -i clicompanion_1.0-3.1_all.deb
```

To automatically receive updates you can add the clicompanion-nightlies ppa to your Software Sources with the following command:
```
sudo add-apt-repository ppa:clicompanion-devs/clicompanion-nightlies
```

Then install the .deb (not necessary if you already followed the wget and dpkg commands above):
```
sudo apt-get update; sudo apt-get install clicompanion
```

---

