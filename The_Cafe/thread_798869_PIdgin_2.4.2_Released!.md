---
title: "PIdgin 2.4.2 Released!"
date: 2008-05-18
forum: The Cafe
---

### Post by Kosimo on 2008-05-18
Pidgin folks has just released a new version: 2.4.2  [Download it!]("http://pidgin.im/")

Here the changelog: 

>     * libpurple
          o In MySpaceIM, messages from spambots are discarded (Justin Williams)
          o Strip mIRC formatting codes from quit and part messages.
          o IRC now displays ban lists in-channel for joined channels.
          o Fixed a bug where the list of loaded plugins would get removed when switching between different operating systems.
          o Fix reception of IRC PART without a part message on Undernet (fixes a problem with litter in the channel user list).
          o IRC no longer crashes on /list on servers which erroneously omit RPL_LISTSTART.
          o Update the NetworkManager support to use D-Bus directly, instead of libnm-glib. Hopefully it's stable now. It will now compile by default if you have D-Bus support and NetworkManager.h. (Elliott Sales de Andrade)
          o MSN buddy list synchronization is now more forgiving, only asking about buddies who have disappeared completely from the server list and not those that have simply moved groups.
          o IRC will now try to append 1-9 to your nick if it is in use, instead of substituting the last character with 1-9 where possible.
          o Bonjour buddies will be saved persistently if they're moved out of the "Bonjour" group. (Eion Robb) 

    * Pidgin
          o The typing notification in the conversation history can be disabled or customized (font, color etc.) in .gtkrc-2.0.
          o Added a plugin (not installed by default) which adds a Send button back to the conversation window. People without physical keyboards have a hard time with the lack of the button.
          o Clicking on the buddyicon in the conversation window toggles the size of the icon between small and large.
          o The settings of a chat (e.g. Handle in an XMPP chat, or Exchange in an AIM chat) can be edited from its context menu in the buddy list.
          o Add a "Present conversation window" preference to the Message Notification plugin; the "Raise conversation window" option does not unminimize windows or draw attention to them when they are on other workspaces--the "Present" option should.
          o Add a preference to set Escape as the keyboard shortcut for closing the conversation window.
          o Add an option in the context menu to disable smileys in the selected text in the conversation history/log viewer. This should help people who regularly paste code in conversations.
          o Add a preference to choose the minimum size of the text input area in lines.
          o Moved the "Local alias" field in the Modify Account dialog to be below the "User Options" heading on the "Basic" tab.
          o Number of room occupants is now shown in chat tooltips where possible 

    * General
          o The configure script now dies on more absent dependencies. The --disable-xxx arguments to configure can be used to bypass unneeded dependencies. This will also cause the configure script to die if an --enable-xxx option is used and the dependencies it requires are missing.
          o The Evolution integration plugin must now be explicitly enabled. Use the --enable-gevolution argument to configure to enable it.
          o The Contact Availability Prediction plugin must now be explicitly enabled. Use the --enable-cap argument to configure to enable it. 

    * Finch
          o New default binding ctrl+x to open context menus.
          o Menu triggers and other bindings will no longer conflict.
          o Middle click pastes the internal clipboard (when mouse support is enabled). 


As always:

1, uninstall your current version
2, download the source code:

Then:  > ./configure
make
sudo make install




**EDIT:**   If you want to install with easy .deb's specially built for Hardy, get them from getdeb! [Link]("http://getdeb.net/app/Pidgin")

---

### Post by Arwen on 2008-05-18
Thanx for letting us know,I'm so bored of kopete :-P

---

### Post by Foster Grant on 2008-05-18
That appears to take care of the reason behind the code fork.

---

### Post by mech7 on 2008-05-18
i hope there will be cam support one day... its all perfect but no cam sex.. umm conversations :p

---

### Post by Jonne on 2008-05-18
> **Foster Grant said:**
> That appears to take care of the reason behind the code fork.
yeah, I noticed that. It's a good thing, because Funpidgin wasn't exactly a good name for an app anyway...

---

### Post by graabein on 2008-05-18
I just use meebo.com anyhow.

---

### Post by Kosimo on 2008-05-18
> **graabein said:**
> I just use meebo.com anyhow.

Wow...
That's amazing!!  I've never head about it, and looks great!

Thanks for the heads up

---

### Post by bufsabre666 on 2008-05-18
> **Kosimo said:**
> Wow...
That's amazing!!  I've never head about it, and looks great!

Thanks for the heads up

the meebo firefox plugin is awesome too

---

### Post by 34.50 on 2008-05-18
So, when will this be in the update manager?

---

### Post by Thirtysixway on 2008-05-18
```

checking for GLIB... no
no
configure: error:

You must have the GLib 2.0 development headers installed to build.

If you have these installed already you may need to install pkg-config so
I can find them.

josh@josh-desktop:~/pidgin-2.4.2$ sudo apt-get install pkg-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pkg-config is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
josh@josh-desktop:~/pidgin-2.4.2$ 

```

:( what the heck?

---

### Post by Half-Left on 2008-05-18
> **Thirtysixway said:**
> ```

checking for GLIB... no
no
configure: error:

You must have the GLib 2.0 development headers installed to build.

If you have these installed already you may need to install pkg-config so
I can find them.

josh@josh-desktop:~/pidgin-2.4.2$ sudo apt-get install pkg-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pkg-config is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
josh@josh-desktop:~/pidgin-2.4.2$ 

```

:( what the heck?

You'll need quiet a few dev packages to compile this and it's plugins, you need libglib2.0-dev for that error.

---

### Post by sports fan Matt on 2008-05-18
I get a "could not find file or directory" when trying to compile

---

### Post by Mr. Picklesworth on 2008-05-18
> **34.50 said:**
> So, when will this be in the update manager?

6 months! (Unless there's a Pidgin PPA, which would be cool).
Keep an eye on [GetDeb]("http://www.getdeb.net/"), though...

---

### Post by bufsabre666 on 2008-05-18
> **Thirtysixway said:**
> ```

checking for GLIB... no
no
configure: error:

You must have the GLib 2.0 development headers installed to build.

If you have these installed already you may need to install pkg-config so
I can find them.

josh@josh-desktop:~/pidgin-2.4.2$ sudo apt-get install pkg-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pkg-config is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
josh@josh-desktop:~/pidgin-2.4.2$ 

```

:( what the heck?

do you have build-essential installed?

```
sudo apt-get install build-essential
```

---

### Post by 34.50 on 2008-05-18
```
ku@kUbuntu:~/Desktop/pidgin-2.4.2$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
ku@kUbuntu:~/Desktop/pidgin-2.4.2$ 
``` Can anyone tell me how to fix this?

/command_line n00b

---

### Post by Thirtysixway on 2008-05-18
```

checking for XScreenSaverRegister in -lXext... no
checking for XScreenSaverRegister in -lXss... no
configure: error:
XScreenSaver extension development headers not found.
Use --disable-screensaver if you do not need XScreenSaver extension support,
this is required for detecting idle time by mouse and keyboard usage.

```
 
x; what do I need for this, xscreensaver didn't help

---

### Post by bigbrovar on 2008-05-18
for all the pple having dependency issues with pidgin try running sudo apt-get build-dep pidgin which would install all the dependencies for pidgin .. so u wouldnt have any more problem should u try to compile

---

### Post by Xanatos Craven on 2008-05-18
> **Foster Grant said:**
> That appears to take care of the reason behind the code fork.
Fail.

[http://gadgetopia.com/post/6392?rc](http://gadgetopia.com/post/6392?rc)
> 
The reason we forked the code was not, as many seem to think, over the text entry window. **This was the event that finally made it clear to Connor and I that the attitude of the Pidgin developers wasn’t going to change anytime soon, and there were many people who felt that this fork was a long time coming, so we did.** And our mission is to accommodate our users as best we can.

Forking is just a cycle of life for an open-source application. Forks lead to new developments in the code, it fosters creativity and even competition, but in the end whether both survive or one or the other dies, the software has progressed and become better. This benefits everyone.

We actually have been in long discussion with the Pidgin developers in our IRC channel, and you could say we’re even collaborating on some issues, discussing new ideas, etc. Forks aren’t a bad thing at all.


---

### Post by Exsecrabilus on 2008-05-18
> **Mr. Picklesworth said:**
> 6 months! (Unless there's a Pidgin PPA, which would be cool).
Keep an eye on [GetDeb]("http://www.getdeb.net/"), though...
Wait, are you talking about when it's going to be available in Synaptic?

---

### Post by Mr. Picklesworth on 2008-05-18
> **Exsecrabilus said:**
> Wait, are you talking about when it's going to be available in Synaptic?

In response to question above that. Should have quoted :O

Edit:
Especially since it ended up /not/ above my post!

---

### Post by mrgnash on 2008-05-18
Built, installed, and working perfectly :)

---

### Post by PRGUY85 on 2008-05-19
```
checking for NETWORKMANAGER... no
configure: error:
NetworkManager development headers not found.
Use --disable-nm if you do not need NetworkManager support.

```

I cannot make or make install after this.

---

### Post by mustang on 2008-05-19
> **bigbrovar said:**
> for all the pple having dependency issues with pidgin try running sudo apt-get build-dep pidgin which would install all the dependencies for pidgin .. so u wouldnt have any more problem should u try to compile

Thank you! That saves a lot of trouble.

> **PRGUY85 said:**
> ```
checking for NETWORKMANAGER... no
configure: error:
NetworkManager development headers not found.
Use --disable-nm if you do not need NetworkManager support.

```

I cannot make or make install after this.

network-manager-dev. The fact that this was needed suggest to me they've fixed the suspend issues. This would be promising if I didn't use wicd.

edit: Thanks Kosimo for the heads up!

---

### Post by kevdog on 2008-05-19
Or simply add this to the configure statement

./configure --disable-nm

---

### Post by Kosimo on 2008-05-21
Getdeb made easy pidgin 2.4.2 .deb's for Hardy! ;)


[Get them!]("Get them!")

---

### Post by Exsecrabilus on 2008-05-22
> **Kosimo said:**
> Getdeb made easy pidgin 2.4.2 .deb's for Hardy! ;)


[Get them!]("Get them!")
WHOOOOO!!!!! [http://www.getdeb.net/](http://www.getdeb.net/)

---

### Post by FFighter on 2008-05-22
No cam support yet? Even the ugly aMSN has it... why can't pidgin folks implement it!? Ohh well.. guess I still need to keep aMSN installed.

---

### Post by bobbocanfly on 2008-05-22
> **Thirtysixway said:**
> ```

checking for XScreenSaverRegister in -lXext... no
checking for XScreenSaverRegister in -lXss... no
configure: error:
XScreenSaver extension development headers not found.
Use --disable-screensaver if you do not need XScreenSaver extension support,
this is required for detecting idle time by mouse and keyboard usage.

```
 
x; what do I need for this, xscreensaver didn't help

running 'sudo apt-get build-dep pidgin' should get most of the dependencies needed.

---

### Post by OZFive on 2008-05-22
Still has the issue with Guifications having 4 notices pop up when someone registers activity on XMPP.  :S

---

### Post by racoq on 2008-05-23
Does anyone know how to get the plugin,  to make the send button appear in the conversation , and how to make it work?

---

### Post by StOoZ on 2008-05-25
Downloaded it and cant install it on gusty,any idea??
it just doesnt compile, gives me some errors...

---

### Post by Exsecrabilus on 2008-05-26
> **StOoZ said:**
> Downloaded it and cant install it on gusty,any idea??
it just doesnt compile, gives me some errors...
Just go to [http://getdeb.net/](http://getdeb.net/)

No need to compile.....

---

### Post by Old Marcus on 2008-05-26
> **Exsecrabilus said:**
> Just go to [http://getdeb.net/](http://getdeb.net/)

No need to compile.....
I thought they were only for hardy? or is there not much difference?

No matter to me anyways, I successfully compiled it. :)

---

### Post by StOoZ on 2008-05-27
on getdeb they are for hardy, I use gusty... :(
did anyone tried them on gusty?

@Old Marcus :
how did you compile it? I get many errors, the first one is for the xscreensaver.. and more to come.

any bunch of packages that I should install of get over with it??

thanks,

---

### Post by Exsecrabilus on 2008-05-27
Did you try upgrading to Hardy?

If you can't, what is it?
Is it all the complaints you hear about it?
Or does it just not work for you?

---

### Post by bufsabre666 on 2008-05-27
> **StOoZ said:**
> on getdeb they are for hardy, I use gusty... :(
did anyone tried them on gusty?

@Old Marcus :
how did you compile it? I get many errors, the first one is for the xscreensaver.. and more to come.

any bunch of packages that I should install of get over with it??

thanks,

```
 sudo apt-get build-dep pidgin
```
extract the tarball where ever you want
```
 cd (extracted directory)
./confiure 
``` if you get any missing dependencies jusy google them and do the standard ./configure make and sudo make install, if not just follow
```
 make
sudo make install
```

just the standard like most compiling

---

### Post by PPPP on 2008-06-08
> **bufsabre666 said:**
> ```
 sudo apt-get build-dep pidgin
```
extract the tarball where ever you want
```
 cd (extracted directory)
./confiure 
``` if you get any missing dependencies jusy google them and do the standard ./configure make and sudo make install, if not just follow



googling brought me to this :)

Running the previous commands did not resolve the issues I had running configure.  I'm disabling quite a few things with configure but still not working...I'm on Gutsy by the way...do I *have* to upgrade to Hardy?

---

### Post by kevdog on 2008-06-08
It should work, however you are probably missing one or two necessary libraries -  are you getting any errors that may give some clues?

---

### Post by PPPP on 2008-06-08
When I ran configure, I got the following

```
configure: error:
XScreenSaver extension development headers not found.
Use --disable-screensaver if you do not need XScreenSaver extension support,
this is required for detecting idle time by mouse and keyboard usage.

```

So then I ran:
```

./configure --disable-screensaver

```

Then I got:
```

configure: error:
GtkSpell development headers not found.
Use --disable-gtkspell if you do not need it.

```

This disabling went on for a few more times...after disabling about 5-6 things, I stopped :(

---

### Post by hanzomon4 on 2008-06-09
I would search for the dev packages in synaptic for the things you are disabling. That's what it means when it says in can't find the header files, that's the *-dev packages

---

### Post by PPPP on 2008-06-09
> **hanzomon4 said:**
> I would search for the dev packages in synaptic for the things you are disabling. That's what it means when it says in can't find the header files, that's the *-dev packages

Thanks! It took a while but I resolved all the needed packages and I got it installed.  Thanks a lot!  :D

---

### Post by BiGBeN_87 on 2008-07-02
Here is, what I needed to install additionally:

XSceenSaver development headers: libxss-dev
Startup notification development headers: libstartup-notification0-dev
GtkSpell development headers: libaspell-dev libgtkspell-dev
libxml2 >= 2.6.0 development headers: libxml2-dev
GStreamer development headers: libgstreamer0.10-dev
Meanwhile development headers: libmeanwhile-dev
avahi development headers:  --disable-avahi
D-Bus development headers : libdbus-1-dev libdbus-glib-1-dev
NetworkManager development headers: network-manager-dev
Perl development headers: libperl-dev
GnuTLS or NSS SSL development headers: libnss3-dev
Tcl development headers: tcl8.4-dev
Tk development headers: tk8.4.dev


Perhaps this saves some googleing. :)

---

### Post by jayvora on 2008-07-16
Thnks a lottt...

i found another help :
apt-get install libglib2.0-dev
apt-get install libgtk2.0-dev (will install a lot of dependencies)
apt-get install libxml2-dev
#at this point pidgin it will compile
apt-get install libgnutls-dev (for ssl support for msn and google talk)
apt-get install libgstreamer0.10-dev (for gstreamer support)
apt-get install libdbus-1-dev libdbus-glib-1-dev
(for dbus support)
apt-get install libgtkspell-dev (for gtkspell support)

##compile pidgin

tar xvfj pidgin-2.0.0.tar.bz2
cd pidgin-2.0.0/
./configure
make
su
make install


# run it
./pidgin


Good luck to the reader

---

### Post by RiceMonster on 2008-07-16
If you're compling it on Ubuntu, it's

```
sudo make install
```

not

```
su
make install
```

because you can't log in as root. If compiled as above, you should be able to run it by typing "pidgin" from any directory. "./pidgin" is not required.

---

### Post by kevdog on 2008-07-16
> **BiGBeN_87 said:**
> Here is, what I needed to install additionally:

XSceenSaver development headers: libxss-dev
Startup notification development headers: libstartup-notification0-dev
GtkSpell development headers: libaspell-dev libgtkspell-dev
libxml2 >= 2.6.0 development headers: libxml2-dev
GStreamer development headers: libgstreamer0.10-dev
Meanwhile development headers: libmeanwhile-dev
avahi development headers:  --disable-avahi
D-Bus development headers : libdbus-1-dev libdbus-glib-1-dev
NetworkManager development headers: network-manager-dev
Perl development headers: libperl-dev
GnuTLS or NSS SSL development headers: libnss3-dev
Tcl development headers: tcl8.4-dev
Tk development headers: tk8.4.dev


Perhaps this saves some googleing. :)

Excellent list, I would just like to add to install the pidgin-dev (or gaim-dev) package and libpurple-dev in addition to the above list.  Thanks however for writing those packages down.  Its nearly all inclusive.

---

### Post by jdorenbush on 2008-09-13
> **PPPP said:**
> ```
configure: error:
XScreenSaver extension development headers not found.
Use --disable-screensaver if you do not need XScreenSaver extension support,
this is required for detecting idle time by mouse and keyboard usage.

```


Goto Synaptic Package Manager and install this:

**libxss-dev**
X11 Screen Saver extension library (development headers) 

Check out this for more...
[http://packages.ubuntu.com/source/hardy/xscreensaver](http://packages.ubuntu.com/source/hardy/xscreensaver)

---

### Post by Sef on 2008-09-14
Locked. Necromancing.  Anyway current pidgin is 2.5.1.

---

