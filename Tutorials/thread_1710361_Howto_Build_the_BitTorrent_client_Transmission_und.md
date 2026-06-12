---
title: "Howto: Build the BitTorrent client Transmission under the latest Ubuntu release"
date: 2011-03-19
forum: Tutorials
---

### Post by andrew.46 on 2011-03-19
In February Transmission 2.50 was released. This mini-guide demonstrates how to build this version from source under for the latest Ubuntu release: Oneiric Ocelot. I will update this guide periodically for newer versions of both Transmission and Ubuntu :).

**Remove the repository version...**

First we need to remove the repository version, which has been split into a few different components (we will be building instead a *single* package that has the gtk frontend, the cli client, the remote utility and the daemon). The following is a *single* command:

```

sudo apt-get remove transmission transmission-daemon \
transmission-common transmission-gtk transmission-cli transmission-qt

```

**Dependencies and compilers...**

Next download some compiling tools and dependencies with the following *single* command:

```

sudo apt-get install build-essential automake autoconf checkinstall libtool \
pkg-config libcurl4-openssl-dev intltool libxml2-dev libgtk2.0-dev \
libnotify-dev libglib2.0-dev libgconf2-dev libcanberra-gtk-dev libappindicator-dev

```

The newest Transmission requires an external copy of libevent so we will download and compile this, then install it *locally*. The following is a *single* command:

```

mkdir -v $HOME/transmission_build && cd $HOME/transmission_build && \
wget https://github.com/downloads/libevent/libevent/libevent-2.0.17-stable.tar.gz && \
tar xvf libevent-2.0.17-stable.tar.gz && \
cd libevent-2.0.17-stable && \
./configure --prefix=$HOME/transmission_build/libevent && \
make && make install

```

**Download and compile Transmission...**

Next download the Transmission source code, open the tarball and compile and install it with the following *single* command:

```

cd $HOME/transmission_build && \
wget http://download.transmissionbt.com/files/transmission-2.50.tar.bz2 && \
tar xjvf transmission-2.50.tar.bz2 && cd transmission-2.50 && \
export PKG_CONFIG_PATH="$HOME/transmission_build/libevent/lib/pkgconfig" && \
./configure && make && \
sudo checkinstall --pakdir "$HOME/transmission_build" --backup=no --deldoc=yes \
  --fstrans=no --deldesc=yes --delspec=yes --default --pkgversion "2.50" && \
make clean

```

And that is it! This gives you the newest version of a great BitTorrent program, perfect for downloading and sharing the latest versions of Ubuntu. Remember: Have Fun!!

**Recent Updates to this Guide:**

[LIST]
[*]Mar 18 2012: Updated for Transmission 2.50 and libevent 2.0.17
[*]Oct 24 2011: Updated for Transmission 2.42
[*]Oct 09 2011: Updated for Transmission 2.41
[*]Sep 30 2011: Updated for Oneiric Ocelot, Transmission 2.33 and libevent 2.0.14
[*]Jul 16 2011: Updated for Transmission 2.32
[/LIST]

---

### Post by andrew.46 on 2011-06-03
I have upgraded the guide to cater for Natty Narwhal and the newest Transmission which came out a week or 2 ago. Have fun with the new version :).

---

### Post by nothingspecial on 2011-06-11
Another great guide.

Thankyou Andrew :p

---

### Post by nothingspecial on 2011-06-11
Works perfectly on Ubuntu 11.04, Xubuntu 11.04 running Gnome 3 and Gnome shell and Ubuntu server 10.04.2 LTS (with absolute minimum X).

But please bear in mind, the command transmissioncli now has a dash

transmission-cli

And if you do this while you have unfinished torrents, you will have to start again (or at least I can't figure out how to resume them with the cli interface).

I would be interested, if you know Andrew, if it is possible to build the latest Transmission, without the gui.

---

### Post by andrew.46 on 2011-06-12
> **nothingspecial said:**
> Works perfectly on Ubuntu 11.04, Xubuntu 11.04 running Gnome 3 and Gnome shell and Ubuntu server 10.04.2 LTS (with absolute minimum X).

Thanks or having a look at this and testing it so widely :).

> **nothingspecial said:**
> But please bear in mind, the command transmissioncli now has a dash

```
transmission-cli
```



Almost worth putting an alias in $HOME/.bashrc:

```

alias transmissioncli=transmission-cli

```

I have not tested this, in part because I am on my *other* computer at the moment (without Transmission), but it should save a few mistypings!

And if you do this while you have unfinished torrents, you will have to start again (or at least I can't figure out how to resume them with the cli interface).

> **nothingspecial said:**
> I would be interested, if you know Andrew, if it is possible to build the latest Transmission, without the gui.

It should not be too much trouble, there are several *enable* and *disable* options seen in *./configure --help* and certainly the Ubuntu package splits the Transmission source up into several discrete packages. It would not be too much trouble to build a set of formal debian packages for the new version by modifying the existing package but I have never enjoyed building packages in this way.

And I confess that I have always used rtorrent for ncurses/cli and Transmissioon for gui rather than the Transmission cli interface :).

---

### Post by nothingspecial on 2011-06-12
> **andrew.46 said:**
> 


And I confess that I have always used rtorrent for ncurses/cli and Transmissioon for gui rather than the Transmission cli interface :).

I have to confess that I am not much of a torrenter (if that is a word). I tend to use them to download single files (linux distros mainly).

So, I have an alias

```
alias trm='transmissioncli -d -U 10 -er'
```

-d means no limit to download speed

-U 10 means limit upload speed to 10kbs

-er means use encryption (even though the torrents are completely legal, and my isp does not concern itself with such things, some isps do).

For my situation, rtorrent is overkill.

Simply ```
trm <url_of_latest_ubuntu_release>
```

---

### Post by ron999 on 2011-07-16
Hi
This HowTo has worked OK with Lucid Lynx.:D
(Transmission 2.32 and libevent 2.0.12)

---

### Post by andrew.46 on 2011-07-16
Thanks Ron! I have updated the guide to cover the latest Transmission release now..

---

### Post by babygenius55 on 2011-09-25
I tried these instructions with 10.10 ubuntu, and everything seemed to install fine, but the program doesn't start when i click any short cuts.  Running from terminal gives me

~/Desktop$ transmission-gtk %U
[1]+  Bus error               transmission-gtk %U
Bus error

I'm using transmission 2.33.  i changed the numbers where neccesary, but i think i'll just do it excatly how you have it in the code.

     --with 2.32 I only get
     --desktop:~$ transmission-gtk us error

---

### Post by andrew.46 on 2011-09-25
Those Transmission guys must never sleep :). I am in the process of installing Oneiric beta 2 so when this is settled in I shall retest the guide and make sure all is well. Check that you only have one copy of Transmission installed at the moment though, and perhaps also test starting with:

```
transmission -p
```

---

### Post by mc4man on 2011-09-25
> **andrew.46 said:**
> I am in the process of installing Oneiric beta 2 so when this is settled in 
If you're using the beta 2 image then the 1st thing i'd do is update, B2 shipped w/ some packages that were less than 'ideal'
(today's daily would be in better shape.

---

### Post by andrew.46 on 2011-09-25
> **mc4man said:**
> If you're using the beta 2 image then the 1st thing i'd do is update, B2 shipped w/ some packages that were less than 'ideal'
(today's daily would be in better shape.

Thanks for the tip, I have updated now. Runs a little better than Natty in my VM..... Can't believe that Synaptic is no longer default :(.

---

### Post by babygenius55 on 2011-09-27
The -p flag yields the same results.  :(

...and it's weird/sort of important to me because qBittorrent isn't reading my partial downloads properly.

---

### Post by andrew.46 on 2011-09-30
Upgraded the guide to Oneiric, latest libevent and Transmission. Not too many benefits at the moment as Oneiric currently has the latest version but 2.34 will be out soon and this will not be in Oneiric I suspect.

@babygenius55: It may be worthwhile to remove all of the Transmission preferences and allow Transmission to start from scratch. To do this safely close Transmission down and then simply run the following command in red:

```

andrew@corinth:~$ **[COLOR="Red"]mv -v $HOME/.config/transmission $HOME/.config/transmission_bak[/COLOR]**
`/home/andrew/.config/transmission' -> `/home/andrew/.config/transmission_bak'

```

When you restart Transmission the defaults will be in place and hopefully all will be well. All of your old settings will remain in *$HOME/.config/transmission_bak* for reference or reversion... BTW anybody know any safe blocklist URLs?

---

### Post by andrew.46 on 2011-10-09
Update to Transmission 2.41, looks like this version will not be part of Oneiric...

---

### Post by andrew.46 on 2011-10-24
Thanks Ron for the heads-up: updated to Transmission 2.42 :)

---

### Post by josh6025 on 2011-11-27
First off I would like to thank andrew.46 for a great guide but I've got just got one question, I have run all the commands and now I am unsure of how to run the GTK version, I'm using 10.04LTS.

---

### Post by andrew.46 on 2011-11-27
> **josh6025 said:**
>  I have run all the commands and now I am unsure of how to run the GTK version, I'm using 10.04LTS.

While I have not tested this version of the guide under 10.04 I suspect that Transmission should appear on your GNOME Menu? If the icon is not there try logging off and back on and hopefully it will appear :)

---

### Post by josh6025 on 2011-12-04
> **andrew.46 said:**
> While I have not tested this version of the guide under 10.04 I suspect that Transmission should appear on your GNOME Menu? If the icon is not there try logging off and back on and hopefully it will appear :)

I logged out and tried rebooting as well and the icon didn't appear in the menu, I'm using 10.04LTS server with the gnome GUI installed on top of it.

---

### Post by mpw on 2012-01-28
Hello,

after I nearly killed my system integrity by installing Transmission-cli 2.42 from a debian repo with dpkg, I ran u skript from the first post! And it works!

Thank you very much andrew.46!

Can someone explain me, how this works with the libc6-Library? What does "install locally" mean?

Bye
MPW

---

### Post by andrew.46 on 2012-03-18
Sorry about the delay answering, I had thought that this guide was no longer being used :). I have updated Transmission to 2.50 and bumped the libevent version as well. Local installation of libevent is simply to avoid any potential repercussions from altering versions of system support libraries, not a huge possibility with libevent but all the same...

---

### Post by adriankoooo on 2012-04-16
I successfully compiled transmission-daemon 2.51, following this guide, but auto start doesn't work anymore. How I can make transmission-daemon to run automatically on startup?

Thank you

---

### Post by andrew.46 on 2012-04-17
And still this guide bubbles along :). I have not set Transmission in this way myself but I suspect the answer will be found on this nicely written wiki page:

AddingProgramToSessionStartup
[https://help.ubuntu.com/community/AddingProgramToSessionStartup](https://help.ubuntu.com/community/AddingProgramToSessionStartup)

Hope this helps?

---

### Post by Cincinnatux on 2012-04-19
> **andrew.46 said:**
> In February Transmission 2.50 was released. This mini-guide demonstrates how to build this version from source under for the latest Ubuntu release: Oneiric Ocelot. I will update this guide periodically for newer versions of both Transmission and Ubuntu :).


Um, I must be missing something.  Aren't BitTorrent clients relatively feature-stable?  Why not just rely on the repository version?

---

### Post by andrew.46 on 2012-07-28
> **Cincinnatux said:**
> Um, I must be missing something.  Aren't BitTorrent clients relatively feature-stable?  Why not just rely on the repository version?

The answer is here:

[https://trac.transmissionbt.com/wiki/Changes](https://trac.transmissionbt.com/wiki/Changes)

As you can see there have been many security and bug fixes. In the world of torrents I think it is thus well worthwhile keeping abreast of recent changes with Transmission!

---

### Post by andrew.46 on 2012-07-28
This guide has been transferred to the Ubuntu Community Wiki, but support will still be available in this thread. The address is:

Compiling Transmission
[https://help.ubuntu.com/community/CompilingTransmission](https://help.ubuntu.com/community/CompilingTransmission)

Feel free to post any questions here or modify the wiki page yourself if there are obvious changes needed.

---

### Post by ads52 on 2012-08-12
The wiki page has received an update. I have tidied up the docs in the Transmission package and more importantly updated 2 of the -dev files to* libappindicator3-dev* and* libgtk3-dev*. Screenshot attached of the successful build under Precise Pangolin.

---

### Post by cariboo on 2012-12-30
There is a new version of this howto please have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=2099851](http://ubuntuforums.org/showthread.php?t=2099851)

---

