---
title: "Pidgin 2.3.0 Released!"
date: 2007-11-27
forum: The Cafe
---

### Post by Kosimo on 2007-11-27
Pidgin 2.3.0 Is here! :)

As always:

```
./configure
make
sudo make install
```




Edit:   Here an easy .deb installation file from Getdeb:   [Link]("http://www.getdeb.net/app.php?name=Pidgin")




This is the changelog:

>     * libpurple
          o Real usernames are now shown in the system log.
          o We now honor a PURPLE_DISABLE_DEPRECATED define to allow plugins to catch deprecated functions earlier rather than later.
          o Thanks to a patch from Intel, the Bonjour prpl now supports file transfers using XEP-0096 and XEP-0065. This should enable file transfers between libpurple clients and Gajim clients, but will not work with iChat or Adium as they use a different file transfer implementation.
          o XMPP password changes that return errors no longer cause the saved password to be changed.
          o XMPP file transfer support has been enhanced to support sending files through a proxy when the server supports discovering a a bytestream proxy. This should make file transfers much more reliable. The next release will add support for manually specifying a proxy when the server doesn't advertise one. 
    * Pidgin
          o If a plugin says it can't be unloaded, we now display an error and remove the plugin from the list of saved plugins so it won't load at the next startup. Previously, we were ignoring this case, which could lead to crashes.
          o Connection errors are now reported in mini-dialogs inside the buddy list, rather than as buttons in the buddy list and with dialog boxes. If several accounts are disabled when you sign on elsewhere, you can now re-enable them all with a single click.
          o Added tooltips to the Room List window to show full topics
          o Added buttons in preferences to access GNOME network and browser preferences configuration dialogs when running under GNOME
          o If you alias a buddy to an alias that is already present within a particular group, we now offer to merge the buddies into the same contact.
          o A music emblem is now displayed in the buddy list for a buddy if we know she is listening to some soothing music.
          o Added a 'Move to' menu in buddy list context menu for moving buddies to other groups as an alternative to dragging.
          o Group headings are now marked via an underline instead of a different color background.
          o It is now possible to mark a chat on your buddy list as "Persistent" so you do not leave the chat when the window or tab is closed.
          o The auto-join option for chats is now listed in the "Add Chat" dialog along with the new persistence option.
          o Closing an IM no longer immediately closes your conversation. It will now remain active for a short time so that if the conversation resumes, the history will be retained. A preference has been added to toggle this behavior.
          o The "Smiley" menu has been moved to the top-level of the toolbar.
          o Pidgin's display is now saved with the command line for session restoration. (David Mohr)
          o ICQ Birthday notifications are shown as buddy list emblems.
          o Plugin actions are now available from the docklet context menu in addition to the Tool menu of the buddy list.
          o The manual page has been heavily rewritten to bring it in line with current functionality. 
    * Finch
          o If a plugin says it can't be unloaded, we now display an error and remove the plugin from the list of saved plugins so it won't load at the next startup. Previously, we were ignoring this case, which could lead to crashes.
          o It's possible to bind key-strokes to specific menuitems in the windows. Read the 'Menus' section in the man-page for details.
          o 'transpose-chars' operation for the entry boxes. The default key-binding is ctrl+t.
          o 'yank' operation for the entry boxes. The default binding is ctrl+y 
    * Windows-specific changes
          o Updated SILC to use SILC Toolkit 1.1.5. 

---

### Post by st4rdr1ft3r on 2007-11-27
is the MSP14 merge in there yet?

---

### Post by Steve Fisher on 2007-11-27
> **st4rdr1ft3r said:**
> is the MSP14 merge in there yet?

Apparently not, I've heard that the dev's have done it, but they simply haven't put it into Pidgin yet. Ironing out a few bugs I guess.

So, is Pidgin ever going to appear in Update Manager, or will we always have to compile from source? Also, correct me if i'm wrong, but don't we Ubuntu users have to add something to the ./configure line?

EDIT: Ah, yes. This is what I meant...
```
Pidgin will be installed in /usr/local/bin.
Warning: You have an old copy of Pidgin at /usr/bin/pidgin.

```

---

### Post by FooAtari on 2007-11-27
Trying to install this under Kubunut but having problems.

Pidgin appears in the menu but with no icon.  When I try and run it it starts to load for a while but nothing else happen it just disappears from the taskbar.

It appears to install with any problems, any ideas?  How do I completely remove it?

---

### Post by Steve Fisher on 2007-11-27
Having problems as well. Removed old Pidgin via synaptic, then did the usual ./configure, make, sudo make install. Everything seemed OK, but Pidgin won't launch.
```
fish@el-crappo-lappo:~$ pidgin
pidgin: symbol lookup error: pidgin: undefined symbol: purple_account_get_current_error

```

---

### Post by n3tfury on 2007-11-27
old.

[http://ubuntuforums.org/showthread.php?t=624252](http://ubuntuforums.org/showthread.php?t=624252)

---

### Post by Kosimo on 2007-11-27
Edit:

This deb I've created doesn't works. 

Sorry guys.

---

### Post by Lucretius on 2007-11-27
nope... didn't work for me i'm afraid (the .deb that is)

---

### Post by FooAtari on 2007-11-27
Im not entirely sure this actually fixed the problem.  But I got an error that it couldn't load libpurple or something along those lines, sorry should have noted the exact message.

So I installed libpurple0 from Synaptic, Reinstalled Pidgin and it's now working.

Edit:
Or not, Pidgin now loads but cant use MSN "SSL Support is needed for MSN"
Libssl 0.9.8 is already installed.  So I tried installing libssl-dev and re-installing Pidgin but no difference.

Any suggestions?

Bloody hell, I didn't think installing Pidgin would be so difficult :).  I might just keep using Kopete.  I just like to use the same apps across Linux and Windows whenever possible,,,

---

### Post by mridkash on 2007-11-27
I want more smileys with Pidgin, where are they?

---

### Post by x0as on 2007-11-27
Built fine for me & msn connects, configure line needs to be 

```
./configure --enable-gnutls=yes --prefix=/opt/pidgin
```

---

### Post by aho on 2007-11-27
Great to see a new update for Pidgin.
One thing i would like to see with Pidgin is a little message come up when users come online. Im sure im right by saying at the moment it only comes up with sound.

---

### Post by atomkarinca on 2007-11-27
Pidgin has guifications and libnotify for that:

```
sudo apt-get install pidgin-guifications

or 

sudo apt-get install pidgin-libnotify
```

---

### Post by FooAtari on 2007-11-27
> **x0as said:**
> Built fine for me & msn connects, configure line needs to be 

```
./configure --enable-gnutls=yes --prefix=/opt/pidgin
```

Thanks, but didnt work.  Does Pidign need to be removed first?

---

### Post by eldragon on 2007-11-27
got this error while compiling too
```
 pidgin: symbol lookup error: pidgin: undefined symbol: purple_account_get_current_error 
```

i did ```
 sudo apt-get remove pidgin libpurple0 
```

and then i did ```
 sudo apt-get install pidgin 
```

and it run again..

i thought id be getting plain old 2.2.1 but instead it loads 2.3.0

so wtf?! is this alright...?

---

### Post by x0as on 2007-11-27
I removed pidgin & libpurple.  Don't forget to change PATH & LD_LIBRARY_PATH before running pidgin.

Do you get this near the end after running configure?

```
SSL Library/Libraries......... : Mozilla NSS and GnuTLS
```

---

### Post by FooAtari on 2007-11-27
surely apt-get wont work for removing pidgin 2.0.3?

And x0as kind of lost me there what do you mean by change PATH & LD_LIBRARY_PATH before running pidgin?

---

### Post by x0as on 2007-11-27
I got errors about missing libs without changing LD_LIBRARY_PATH

```
LD_LIBRARY_PATH=/opt/pidgin/lib
export LD_LIBRARY_PATH
```

---

### Post by Manan on 2007-11-27
same problem cant find a solution :( help help please some one help :(

---

### Post by darweth on 2007-11-27
Eeeeep.  I will just wait for a nicely-constructed .deb to pop up from somewhere.  One that easy makes and could then roll back the changes necessary.  My compiling days are over!  Well... for stuff like Pidgin at least. ;)

---

### Post by meborc on 2007-11-27
i'm feeling lazy... "if it doesn't itch, don't scratch" - meaning the old/current pidgin is running OK, so i'll just wait for the getdeb.net .deb file... or repo update :)

---

### Post by FooAtari on 2007-11-27
Perhaps not a bad idea meborc...

I still have the ssl problem with msn  which I cant seem to fix.

Anyway to uninstall an app installed from source? I can delete the file from the usr/local/bin folder but that doesnt remove everything does it?

---

### Post by igknighted on 2007-11-27
> **FooAtari said:**
> Perhaps not a bad idea meborc...

I still have the ssl problem with msn  which I cant seem to fix.

Anyway to uninstall an app installed from source? I can delete the file from the usr/local/bin folder but that doesnt remove everything does it?

cd to the directory of the source that you built and type "sudo make uninstall".  Or, if you used checkinstall, you should be able to use dpkg to remove it.

---

### Post by FooAtari on 2007-11-27
I was just about to post and say I found out. Thanks anyway :D

Not sure why I cant get msn to work but Ill just use Pidgin 2.1 from Synaptic

---

### Post by x0as on 2007-11-27
Is it only Kubuntu users having problems?  The deb I built works on both Ubuntu gutsy boxes I've installed it on :confused:

---

### Post by FooAtari on 2007-11-27
Mever thought that xa0s, maybe it is.

Anyway, I did make uninstall but its still there. When I enter pidgin in the terminal 2.3.0 stil loads.  Any suggestions?

---

### Post by altonbr on 2007-11-27
Hmm, still stuck at 2.2.0: [http://www.getdeb.net/app.php?name=pidgin](http://www.getdeb.net/app.php?name=pidgin)

:(

Says it will no longer be supported. I assume they'll support it once again since 2.3.0 is out and it's not even included in Hardy (yet), let along Gutsy.

---

### Post by maddog39 on 2007-11-27
I am also having some issues compiling, I have a few ideas and I am going to try and get a compiled version running. If I get it running I'll post a miniguide or something.

---

### Post by maddog39 on 2007-11-27
Okay I got it running from sources. These are the things I believe I did to get it to work, so if it doesnt work just tell me and I'll try to sort it out.

```

sudo aptitude install libnss-dev
sudo aptitude remove --purge pidgin libpurple0
sudo rm /usr/local/bin/pidgin
./configure
make
sudo make install
sudo ldconfig
pidgin &

```
Try that out and see if it works for anybody.

---

### Post by ImpressMe on 2007-11-27
HOW-TO compile 2.2.2 from source, perhaps this will help:
[http://ubuntuforums.org/showthread.php?p=3785277#post3785277](http://ubuntuforums.org/showthread.php?p=3785277#post3785277)

or use Bruce Cowans repository:
[https://launchpad.net/~bruce89/+archive]("https://launchpad.net/%7Ebruce89/+archive")

Note this line! : Change the "hardy" below to "gutsy", and change "main" to "main universe"

** It still doesn't include 2.3.0** but it did update GIMP to 2.4.2 a few days ago. I am patiently waiting for Bruce to update to 2.3.0, I tried compiling Pidgin too many times. I got it working but then Synaptic wanted to downgrade even though my version number was bigger. I got tired of that, I like Synaptic when it is working properly just a damn shame that we have to look everywhere for updates. Give us that damn autopackage at the main Pidgin site!

---

### Post by n3tfury on 2007-11-27
works great in windows  -_#

---

### Post by ImpressMe on 2007-11-27
Hehe yes, it is a silly feeling almost to BEG for 2.3.0 on Linux when it was a click-click and run experience to install it on Windows.

Ah, they finally moved smilies **back** to the toolbar in 2.3.0...

---

### Post by neoaddict on 2007-11-27
Oh noes!  Has anyone experienced any nickname hijackings in Pidgin 2.3?

---

### Post by x0as on 2007-11-27
> **neoaddict said:**
> Oh noes!  Has anyone experienced any nickname hijackings in Pidgin 2.3?

No, why?

---

### Post by viclim on 2007-11-28
It's running on my feisty, although I have to include the launcher in my menu manually. Well, no error occur yet. :)

---

### Post by Kosimo on 2007-11-28
> **ImpressMe said:**
> HOW-TO compile 2.2.2 from source, perhaps this will help:
[http://ubuntuforums.org/showthread.php?p=3785277#post3785277](http://ubuntuforums.org/showthread.php?p=3785277#post3785277)

or use Bruce Cowans repository:
[https://launchpad.net/~bruce89/+archive]("https://launchpad.net/%7Ebruce89/+archive")

Note this line! : Change the "hardy" below to "gutsy", and change "main" to "main universe"

** It still doesn't include 2.3.0** but it did update GIMP to 2.4.2 a few days ago. I am patiently waiting for Bruce to update to 2.3.0, I tried compiling Pidgin too many times. I got it working but then Synaptic wanted to downgrade even though my version number was bigger. I got tired of that, I like Synaptic when it is working properly just a damn shame that we have to look everywhere for updates. Give us that damn autopackage at the main Pidgin site!


I had exactly the same problem than you....  
Strange... 

So, I'm sick of compiling... I'll wait 'till getdeb or someone else will create a .deb for us ;)

---

### Post by Kynan on 2007-11-28
> **x0as said:**
> I removed pidgin & libpurple.  Don't forget to change PATH & LD_LIBRARY_PATH before running pidgin.

Do you get this near the end after running configure?

```
SSL Library/Libraries......... : Mozilla NSS and GnuTLS
```

With the release of pidgin 2.3.0 i attempted to install by compiling and noticed as you did that the ssl did not work. I compiled a previous version back when i was using ubuntu but now im using mint, however im using the same ssl dev files as ubuntu. I found some information on the FAQ section of the website [http://developer.pidgin.im/wiki/FAQssl](http://developer.pidgin.im/wiki/FAQssl) havent had the time to muck around trying it yet but ill give it a go sometime and let you know.
Kynan

---

### Post by x0as on 2007-11-28
> **Kynan said:**
> With the release of pidgin 2.3.0 i attempted to install by compiling and noticed as you did that the ssl did not work. 

I think you read my post wrong, I built ubuntu & debian packages of 2.3.0 that connect to msn fine.

I can't see why it doesn't work for everybody else :confused:

edit: can somebody test this deb work, see if it workis for them, installs to /opt/pidgin. Usual warning apply.  Uninstall the old pidgin & libpurple then install this version.

[http://ppa.launchpad.net/x0as/ubuntu/pool/main/p/pidgin/pidgin_2.3.0-x0as3_i386.deb](http://ppa.launchpad.net/x0as/ubuntu/pool/main/p/pidgin/pidgin_2.3.0-x0as3_i386.deb)

---

### Post by Deathmoon on 2007-11-28
Worked fine for me on Ubuntu 7.10.

downloaded
./configure
make
sudo make install

and then removed old version via synaptic

2.3.0 launches fine with no problems

---

### Post by altonbr on 2007-11-28
> **x0as said:**
> I think you read my post wrong, I built ubuntu & debian packages of 2.3.0 that connect to msn fine.

I can't see why it doesn't work for everybody else :confused:

edit: can somebody test this deb work, see if it workis for them, installs to /opt/pidgin. Usual warning apply.  Uninstall the old pidgin & libpurple then install this version.

[http://ppa.launchpad.net/x0as/ubuntu/pool/main/p/pidgin/pidgin_2.3.0-x0as3_i386.deb](http://ppa.launchpad.net/x0as/ubuntu/pool/main/p/pidgin/pidgin_2.3.0-x0as3_i386.deb)

Just letting you know that your version numbers are incorrect because I get this warning with gDebi:
> A later version is available in a software channel

You are strongly advised to install the version from the software channel, since it is usually better supported.

---

### Post by x0as on 2007-11-28
> **altonbr said:**
> Just letting you know that your version numbers are incorrect because I get this warning with gDebi:

Thanks, I noticed that as after posting.  Cant find out why though :confused:

---

### Post by paszczak on 2007-11-28
Hey ubuntu freaks!
I've tried to compile pidgin 2.3.0 from sources but without succes, so i've searched for deb and... i've found it! :-)
So the solution is:
Go to [http://ubuntu.schmidtke-hb.de/]("http://ubuntu.schmidtke-hb.de/") and add new repo to your list, How to do it you can find here:
[http://ubuntu.schmidtke-hb.de/apt-quelle-hinzufuegen]("http://ubuntu.schmidtke-hb.de/apt-quelle-hinzufuegen")
This is very nice site, very up-to-date ;-)

---

### Post by Steve Fisher on 2007-11-28
> **maddog39 said:**
> Okay I got it running from sources. These are the things I believe I did to get it to work, so if it doesnt work just tell me and I'll try to sort it out.

```

sudo aptitude install libnss-dev
sudo aptitude remove --purge pidgin libpurple0
sudo rm /usr/local/bin/pidgin
./configure
make
sudo make install
sudo ldconfig
pidgin &

```
Try that out and see if it works for anybody.

This seems to have worked for me, but I should point out a couple of things...

The first line should read **sudo aptitude install libnss3-dev**

After the second line I was told that it was also going to remove nautilus-sendto and, more worryingly, ubuntu-desktop. I let it do this.

I changed the ./configure command to **./configure --prefix=/usr --enable-gnutls=yes**

The rest went OK. Once finished I could easily reinstall nautilus-sendto, but ubuntu-desktop wanted to reinstall pidgin and libpurple0 as well, so just left it out... not sure what effect that's going to have.... :(

---

### Post by Colro on 2007-11-28
Isn't working here, either :[

---

### Post by mattheiw on 2007-11-28
> **paszczak said:**
> Hey ubuntu freaks!
I've tried to compile pidgin 2.3.0 from sources but without succes, so i've searched for deb and... i've found it! :-)
So the solution is:
Go to [http://ubuntu.schmidtke-hb.de/]("http://ubuntu.schmidtke-hb.de/") and add new repo to your list, How to do it you can find here:
[http://ubuntu.schmidtke-hb.de/apt-quelle-hinzufuegen]("http://ubuntu.schmidtke-hb.de/apt-quelle-hinzufuegen")
This is very nice site, very up-to-date ;-)
Thanks paszczak. Just installed it successfully! :)

---

### Post by bruce89 on 2007-11-28
Bugger, another one for my PPA, possibly tomorrow.

---

### Post by kingofpain on 2007-11-28
> **paszczak said:**
> Hey ubuntu freaks!
I've tried to compile pidgin 2.3.0 from sources but without succes, so i've searched for deb and... i've found it! :-)
So the solution is:
Go to [http://ubuntu.schmidtke-hb.de/]("http://ubuntu.schmidtke-hb.de/") and add new repo to your list, How to do it you can find here:
[http://ubuntu.schmidtke-hb.de/apt-quelle-hinzufuegen]("http://ubuntu.schmidtke-hb.de/apt-quelle-hinzufuegen")
This is very nice site, very up-to-date ;-)

It seems that the repo is for x86 only... :(

---

### Post by Jammerdelray on 2007-11-28
The greatest Multi IM Client just keeps getting better.

---

### Post by ImpressMe on 2007-11-29
> **bruce89 said:**
> Bugger, another one for my PPA, possibly tomorrow.


Thanks a lot, Bruce! :KS

---

### Post by Kynan on 2007-11-29
> **paszczak said:**
> Hey ubuntu freaks!
I've tried to compile pidgin 2.3.0 from sources but without succes, so i've searched for deb and... i've found it! :-)
So the solution is:
Go to [http://ubuntu.schmidtke-hb.de/]("http://ubuntu.schmidtke-hb.de/") and add new repo to your list, How to do it you can find here:
[http://ubuntu.schmidtke-hb.de/apt-quelle-hinzufuegen]("http://ubuntu.schmidtke-hb.de/apt-quelle-hinzufuegen")
This is very nice site, very up-to-date ;-)

Thanks worked perfectly!, I made a simplified English guide for the linux mint forums based on your post, it can be found here. for anyone interested. [http://www.linuxmint.com/forum/viewtopic.php?f=47&t=7177](http://www.linuxmint.com/forum/viewtopic.php?f=47&t=7177)

---

### Post by ubuntu27 on 2007-11-29
> **st4rdr1ft3r said:**
> is the MSP14 merge in there yet?

> **Steve Fisher said:**
> Apparently not, I've heard that the dev's have done it, but they simply haven't put it into Pidgin yet. Ironing out a few bugs I guess.


What's MSP14? :confused:

---

### Post by hyperair on 2007-11-29
Latest MSN protocol. Support for personal messages among other things.

Anyway I've tried compiling it the same method I used to compile pidgin-2.2.2, and for some reason it complains about a doxy2devhelp.xsl file, then refuses to make completely.

---

### Post by achillescp on 2007-11-29
Hi guys! Sorry to jump in the discussion, but I believe I have some good information:

The code for MSNP14 is already in the source for 2.3.0. When compiling from source, you can enable it editing a line in the 'configure' file. Look for

```
enable_msnp14=no
```

and change it to

```
enable_msnp14=yes
```

You can be sure the support is on when, in the end of the './configure' output, you see among the dynamically build protocols 'msn' instead of 'msnp9'.

The developers warn that the code is really buggy, but for the use I make of it (viewing and setting personal messages), works just fine.

This setting on the 'configure' file worked on the first try I made, so I don't believe I can help if it doesn't work for you. But I can always try, if anyone has any questions =)

See ya!

PS.: One can ask, 'How DA HELL did you find out about this?'
And I can answer, '"grep" is a wonderful tool, when you know what you're looking for...' =DDD

---

### Post by wersdaluv on 2007-11-29
> **paszczak said:**
> Hey ubuntu freaks!
I've tried to compile pidgin 2.3.0 from sources but without succes, so i've searched for deb and... i've found it! :-)
So the solution is:
Go to [http://ubuntu.schmidtke-hb.de/]("http://ubuntu.schmidtke-hb.de/") and add new repo to your list, How to do it you can find here:
[http://ubuntu.schmidtke-hb.de/apt-quelle-hinzufuegen]("http://ubuntu.schmidtke-hb.de/apt-quelle-hinzufuegen")
This is very nice site, very up-to-date ;-)

I just installed pidgin from the repo. With that Pidgin, I can't use Guifications or the libnotify plugins even if I have them installed :(

---

### Post by hyperair on 2007-11-29
Well does anybody know about my doxygen2devhelp.xsl file problem? If I get that fixed I'll upload my deb.

---

### Post by bruce89 on 2007-11-29
> **ImpressMe said:**
> Thanks a lot, Bruce! :KS

Indeed, it'll be done a few minutes from now.

> **achillescp said:**
> Hi guys! Sorry to jump in the discussion, but I believe I have some good information:

The code for MSNP14 is already in the source for 2.3.0. When compiling from source, you can enable it editing a line in the 'configure' file. Look for

```
enable_msnp14=no
```

and change it to

```
enable_msnp14=yes
```

[...]



I'd be interested in building an extra package in my PPA for this, but not right now (too much homework).

---

### Post by ImpressMe on 2007-11-29
Got it from your repository and it works flawlessly! Thanks again.

---

### Post by bruce89 on 2007-11-29
> **ImpressMe said:**
> Got it from your repository and it works flawlessly! Thanks again.

I did personal backports anyway, so I thought I would let everyone benefit.

---

### Post by darweth on 2007-11-29
Thank you!  Bruce is the man!

---

### Post by Montsegur87 on 2007-11-29
Optimize your build. I removed gstream , evolution and screensaver support

From INSTALL
```
Optional Features
=================

   Some packages pay attention to `--enable-FEATURE' options to
`configure', where FEATURE indicates an optional part of the package.
They may also pay attention to `--with-PACKAGE' options, where PACKAGE
is something like `gnu-as' or `x' (for the X Window System).  The
`README' should mention any `--enable-' and `--with-' options that the
package recognizes.

   For packages that use the X Window System, `configure' can usually
find the X include and library files automatically, but if it doesn't,
you can use the `configure' options `--x-includes=DIR' and
`--x-libraries=DIR' to specify their locations.

	By default both the GTK+ UI (Pidgin) and the ncurses UI (Finch) will be
built, assuming that configure finds the necessary libraries and headers for
each.  You can disable the GTK+ UI with `--disable-gtkui' and the ncurses UI
with `--disable-consoleui'.

	`--disable-screensaver' will build libpurple without support for detecting
when it should mark accounts idle based on mouse or keyboard usage.

	`--disable-sm' will build without support for the X session management.
Doing so will remove the ability to have pidgin start up with your window
manager.

	`--disable-gtkspell' will remove the ability to highlight misspelled words.

	`--disable-gevolution' will cause the evolution integration plugin not to
compile.

	`--disable-gstreamer' will build without sound support.  This applies to
*both* Pidgin and Finch.

	`--enable-gnutls=yes,no' will enable or disable the use of gnutls for ssl support.  Disabling both gnutls and nss will mean you cannot use either MSN or Google Talk.  There is no static option for gnutls at this time.

	`--enable-nss=yes,no,static'  will enable or disable the use of nss for ssl support.  This is the only option for ssl support if you are attempting to compile a static version of Pidgin or Finch.  

Optional Packages:

	`--with-silc-includes=DIR' 	and `--with-silc-libs=DIR' can be used if your silc libraries are installed to a location not in your path. 

	`--with-static-prpls' takes a list of comma separated protocols to build in statically (rather than as plugins).  Use this with care.

	`--with-dynamic-prpls' takes a list of comma separated protocols also.  If used only those listed will be built.  If no protocols are listed with either `--with-static-prpls' or with `--with-dynamic-prpls' then Pidgin and Finch will be effectively useless.

	If configure does not find python, it will build without DBUS support.  Thiswill disable scripts such as purple-remote and purple-uri-handler, effectively disabling integration with the browser.  You can tell configure where your python binary is located with `--with-python=PATH'

```

---

### Post by bruce89 on 2007-11-29
> **Montsegur87 said:**
> Optimize your build. I removed gstream , evolution and screensaver support



Nope, sorry, I make my packages as similar to the Ubuntu one as possible (although I'm thinking of adding another package with a optional MSNP14 binary).

---

### Post by Polygon on 2007-11-29
without screensaver support, you dont marked away when your idle for a long time...and without gstreamer you dont get sounds. I couldent live without those two personally.

---

### Post by Montsegur87 on 2007-11-29
its a instant messaging software , not a jukebox =\

Im experimenting a problem with my name , its being changed randomly to one of my contacts

---

### Post by hyperair on 2007-11-30
I've got the same problem. It keeps changing.

---

### Post by ImpressMe on 2007-11-30
> **Montsegur87 said:**
> its a instant messaging software , not a jukebox =\

This notification and idle support (based on when the computer is idle, not Pidgin) is actually pretty important to quite a few.

I would rather see Flash commercials on webpages STFU during "mouse overs" ...;)

---

### Post by ImpressMe on 2007-11-30
> **hyperair said:**
> Latest MSN protocol. Support for personal messages among other things.

Anyway I've tried compiling it the same method I used to compile pidgin-2.2.2, and for some reason it complains about a doxy2devhelp.xsl file, then refuses to make completely.

Monitor this ticket:

[http://developer.pidgin.im/milestone/Activate%20MSNPV14](http://developer.pidgin.im/milestone/Activate%20MSNPV14)

---

### Post by hyperair on 2007-11-30
Well I've tried compiling it by apt-get source pidgin, then copy over the debian folder, remove the patches, and add stuff to the top of the changelog, then dpkg-buildpackage -rfakeroot. It worked for previous versions of pidgin. Apparently 2.3.0 can't be compiled that way.

---

### Post by hyperair on 2007-11-30
It's on getdeb!

---

### Post by RSVampire on 2007-11-30
so is 2.3.0 going to show up in the regular repositories or am I going to HAVE to compile this from the source or from another repository location?

---

### Post by ImpressMe on 2007-11-30
The easiest thing right here and now is to get it here:
[http://www.getdeb.net/app.php?name=Pidgin](http://www.getdeb.net/app.php?name=Pidgin)

I use the repository from bruce89, easier in the long run. Don't compile unless it turns you on. :)

---

### Post by hyperair on 2007-11-30
It'll probably get backported sooner or later. If you're impatient, just head over to Hardy's repositories and grab the required packages xD

---

### Post by Polygon on 2007-11-30
its on getdeb right now (link on the previous page)

to install:

save it all to one place like your desktop

cd ~/Desktop
sudo dpkg -i *.deb

and it will work and not yell about files that are conflicting and all that.

---

### Post by Kosimo on 2007-11-30
> **Polygon said:**
> its on getdeb right now (link on the previous page)

to install:

save it all to one place like your desktop

cd ~/Desktop
sudo dpkg -i *.deb

and it will work and not yell about files that are conflicting and all that.



Here we go guys :D


[http://www.getdeb.net/app.php?name=Pidgin](http://www.getdeb.net/app.php?name=Pidgin)


Getdeb is always here to solve my problems! :)

---

### Post by Kosimo on 2007-11-30
> **Kosimo said:**
> Here we go guys :D


[http://www.getdeb.net/app.php?name=Pidgin](http://www.getdeb.net/app.php?name=Pidgin)


Getdeb is always here to solve my problems! :)

Make sure you install it following this order:

First uninstall your current version y typig ```
Sudo apt-get remove pidgin
```

Then download the three debs, and install first libpurple, then pidgin-data and finally pidgin.   

Everything should be fine

---

### Post by bruce89 on 2007-11-30
> **ImpressMe said:**
> I use the repository from bruce89, easier in the long run. Don't compile unless you it turns you on. :)

You just made my day.

Getdeb isn't an option for me, I don't trust them. Looking at their diff.gz, I notice that 04_let_crasher_for_apport.patch has been removed from their version for some reason (has to be updated for 2.3.0, see below). They also haven't merged in Debian and Ubuntu changes since Gutsy's releases, like I do.

My package is just Hardy's latest version (2.2.2-2ubuntu1 I think) but with uscan and uupdate done to it to get the new upstream. I also fixed one of the patches to apply.

---

### Post by godmode0 on 2007-12-02
> **maddog39 said:**
> Okay I got it running from sources. These are the things I believe I did to get it to work, so if it doesnt work just tell me and I'll try to sort it out.

```

sudo aptitude install libnss-dev
sudo aptitude remove --purge pidgin libpurple0
sudo rm /usr/local/bin/pidgin
./configure
make
sudo make install
sudo ldconfig
pidgin &

```
Try that out and see if it works for anybody.

Hi wanted to say thanks.. this is the only way it worked for me :)

Thx 

works like acharm and no anoyiing auto update msg to back/update back 2.2.1  :)

---

### Post by SOULRiDER on 2007-12-02
> **neoaddict said:**
> Oh noes!  Has anyone experienced any nickname hijackings in Pidgin 2.3?

> **Montsegur87 said:**
> 
Im experimenting a problem with my name , its being changed randomly to one of my contacts

> **hyperair said:**
> I've got the same problem. It keeps changing.

Its a bug, it doesnt actually change but it looks like it does. I think it might be fixed, in my Archlinux I got an update the day after 2.3 was released that fixed the problem.

---

### Post by Kynan on 2007-12-03
> **SOULRiDER said:**
> Its a bug, it doesnt actually change but it looks like it does. I think it might be fixed, in my Archlinux I got an update the day after 2.3 was released that fixed the problem.
Well I have been having the same problem but i can say that it does actually change because the way i found out about it is someone said what up with your display name? (unless it was just coincidence)
but since its on getdeb ill try that and see if its still stuffing up.

---

### Post by zugu on 2007-12-03
Wow, how ironic. I managed to install it on Windows without any hassles. Why can't it be like that on Ubuntu?

---

### Post by Kynan on 2007-12-03
Still got the same problems except as you said it still says one of my friends names in the friendly name box but i asked and they said its just normal. (apparently its going to be fixed/updated soon like this week)

Also does anyone else have the problem with opening a hotmail account (windows live hotmail) and it working the first time after opening pidgin, but the second time and then after it will ask for a password?

---

### Post by jasmuz on 2007-12-03
Hello to all, i've tried using the Deb files from GetDeb, but after the install and run, one of my MSN (passport accounts) fails to keep itself connected, just does the following:

Connects-->Loads contact list-->Quits-->Retries.

Any ideas?

Im going to try the Bruce Cowan backports to see if it does work for me.

---

### Post by hyperair on 2007-12-03
I've got that problem too. I don't think it's a bug on Pidgin's side though. I tried using that account to login to ebuddy.net during that time, as well as MSN's webmessenger. Both failed miserably.

---

### Post by Turin Turambar on 2007-12-03
Thanks for the deb file. I hate compiling. :)

---

### Post by Kynan on 2007-12-04
Yep its definitely changing the friendly name to be viewable by others atleast when you first log in.
and i quote my friend.
"lol? wtf was that about? u logged in as me?"

i really hope an update comes out soon.

---

### Post by nw_raptor on 2007-12-04
yay!

/me compiled with enable_msnp14=yes :D

so far so good :D

---

### Post by hyperair on 2007-12-04
You wouldn't happen to have a deb around would you? =P

---

### Post by nw_raptor on 2007-12-04
> **hyperair said:**
> You wouldn't happen to have a deb around would you? =P

Is that question directed to me?

---

### Post by hyperair on 2007-12-04
Well yes. I'm looking for an MSNP14 Pidgin deb. =P

---

### Post by nw_raptor on 2007-12-04
> **hyperair said:**
> Well yes. I'm looking for an MSNP14 Pidgin deb. =P

well, unfortunately i am not familiar with building packages. i'd be glad to learn though, if someone can point me to the right direction. i've only heard of checkinstall and debhelper, but to be honest, i have never used them.

---

### Post by hyperair on 2007-12-04
Well I've been buliding debs for some time now, but what I usually do is I copy the debian folder from the source of the previous version (which was in the repo) into the source of the new version of the package, then edit the changelog, add a new version there, and run dpkg-buildpackage -rfakeroot. I tried doing that this time, but it failed miserably complaining of some oxy2devhelper.xsl missing. Compiling it via make and make install works fine though. =\

---

### Post by nw_raptor on 2007-12-04
> **hyperair said:**
> Well I've been buliding debs for some time now, but what I usually do is I copy the debian folder from the source of the previous version (which was in the repo) into the source of the new version of the package, then edit the changelog, add a new version there, and run dpkg-buildpackage -rfakeroot. I tried doing that this time, but it failed miserably complaining of some oxy2devhelper.xsl missing. Compiling it via make and make install works fine though. =\

Can you PM me with details on how to (attempt to) create pidgin .debs?

---

### Post by bruce89 on 2007-12-04
> **nw_raptor said:**
> Can you PM me with details on how to (attempt to) create pidgin .debs?

What I do is get the latest Ubuntu/Debian version (whichever is newer), and run uscan and uupdate in its sources. I then test if it builds in pbuilder, and see why it doesn't. I then fix it.

> **zugu said:**
> Wow, how ironic. I managed to install it on Windows without any hassles. Why can't it be like that on Ubuntu?

Package managers.

Windows programs have copies of every library require, Linuxes have only one in a centralised location.

---

### Post by Turin Turambar on 2007-12-04
When we shall expect the backport?

---

### Post by bruce89 on 2007-12-04
> **Turin Turambar said:**
> When we shall expect the backport?

Probably never.

---

### Post by altonbr on 2007-12-04
> **nw_raptor said:**
> yay!

/me compiled with enable_msnp14=yes :D

so far so good :D

Am I dumb? Or just missing something?

```
$ ./configure --enable_msnp14=yes
```
> configure: error: unrecognized option: --enable_msnp14=yes
Try `./configure --help' for more information.

```
./configure --help | grep enable_msn
```
nothing returned.

Yes, this is in the extracted Pidgin 2.3.0 source code.

---

### Post by altonbr on 2007-12-04
PS: Looks like they've added a "Activate MSNPV14" milestone!

[http://developer.pidgin.im/milestone/Activate%20MSNPV14](http://developer.pidgin.im/milestone/Activate%20MSNPV14)

---

### Post by theShaggy on 2007-12-04
Tried compiling with just enable_msnp14=yes, but it screwed up my installation and caused it to crash with hundreds of synch errors.

When I uncomment, like the config suggests, I get this:

> ./configure: line 31159: syntax error near unexpected token `msnp14,[AC_HELP_STRING'
./configure: line 31159: `AC_ARG_ENABLE(msnp14,[AC_HELP_STRING([--enable-msnp14], [Disable the newer MSNP14 protocol])],,enable_msnp14=no)'


---

### Post by altonbr on 2007-12-04
Found it:
```
$ ./configure --enable-msnp14
```

Configured properly. Now I cross my fingers for make and make install!

---

### Post by theShaggy on 2007-12-04
Doesn't seem to work for me.  Still configures with "msnp9"

---

### Post by altonbr on 2007-12-04
I WAS NOT FULLY ABLE TO GET THIS TO WORK, SO PLEASE READ THROUGH THIS POST BEFORE TRYING.

This is what I had to run to get Pidgin to "compile" on my Gutsy machine. This process actually attempts to install all dependancies from the repositories and compile Pidgin to a .deb for easy removal.

Official help file: [https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

*Assuming you are in the directory ./pidgin-2.3.0*

```
$ sudo aptitude install build-essential checkinstall gettext libglib2.0-dev libgtk2.0-dev libxml++2.6-dev && auto-apt run ./configure
```

Is there a line like this?:
> configure: error:

Yes? Then install the files requested.

No? Then you're free to run this:
*(Please note, that this process can take a very long time)*
```
$ make
```

If everything went well, the last four lines should look similar to:
> Found cached translation database
Merging translations into pidgin.desktop.
make[2]: Leaving directory `/home/$USER/pidgin-2.3.0'
make[1]: Leaving directory `/home/$USER/pidgin-2.3.0'


Now run:
```
$ sudo checkinstall
```

and fill out the information asked.

If you want to be 'professional', this is Pidgin's official description for 2.2.1 in the repositories:

> graphical multi-protocol instant messaging client for X 
Pidgin is a graphical, modular Instant Messaging client capable of using
AIM/ICQ, Yahoo!, MSN, IRC, Jabber, Napster, Zephyr, Gadu-Gadu, Bonjour,
Groupwise, Sametime, SILC, and SIMPLE all at once.

Some extra packages are recommended to use the core functionality present
in most pidgin installations:
 * gstreamer0.10-plugins-base, gstreamer0.10-plugins-good
   - Sound support.

More extra packages are suggested to use increased functionality:
 * gnome-panel | kicker | docker:
   - To use the system tray icon functionality (minimizing to an icon, having
     the icon blink when there are new messages, etc.)
 * evolution-data-server:
   - For interfacing with an Evolution address book

For me, it seemed to pause on "Installing Debian package..." for a long time so I hit enter and it seemed to finish (???).

If successful, you should receive this:
> **********************************************************************

 Done. The new package has been installed and saved to

 /home/$USER/pidgin-2.3.0/pidgin_2.3.0-1_i386.deb

 You can remove it from your system anytime using: 

      dpkg -r pidgin

**********************************************************************

That .deb has already been installed, so no need to double-click and install with GDebi.

I unfortunately, received this when running
```
$ pidgin
```
> pidgin: error while loading shared libraries: libpurple.so.0: cannot open shared object file: No such file or directory

Almost got it!

I still miss the "double-click the .exe/.deb" method, don't you?

---

### Post by theShaggy on 2007-12-04
I seem to have broken something.

When I managed to install with MSNP14 working, I got a buddy synchronisation error for every single contact on my list.  It flooded my buffer with hundreds of them and crashed the program.  So I'm going to hold off on the protocol, until (at the very least) someone comes up with a deb that has it activated.

I tried to roll back to a non-active one, and after installing it did the same thing.  Compiling again now, but I hope this won't stay broken forever.

*Added* Nope, didn't work.  It's giving my synchronisation errors now.

I really don't know what to do.  I've done sudo make uninstall, and short of deleting every known file related to pidgin off my computer, I've got nothing.

Am I missing dependencies?  Can I figure out how to do that?  Somebody please help me, I'm going crazy without MSN.

---

### Post by undine on 2007-12-04
> **theShaggy said:**
> I seem to have broken something.

When I managed to install with MSNP14 working, I got a buddy synchronisation error for every single contact on my list.  It flooded my buffer with hundreds of them and crashed the program.  So I'm going to hold off on the protocol, until (at the very least) someone comes up with a deb that has it activated.

I tried to roll back to a non-active one, and after installing it did the same thing.  Compiling again now, but I hope this won't stay broken forever.

*Added* Nope, didn't work.  It's giving my synchronisation errors now.

I really don't know what to do.  I've done sudo make uninstall, and short of deleting every known file related to pidgin off my computer, I've got nothing.

Am I missing dependencies?  Can I figure out how to do that?  Somebody please help me, I'm going crazy without MSN.

This might be a good time to try Emesene ;)

---

### Post by theShaggy on 2007-12-04
Don't tempt me, man.  Don't tempt me. :-)

---

### Post by bruce89 on 2007-12-04
Warning:

[COLOR="Red"][SIZE="6"]Don't compile the msnp14 version unless you want breakage.[/SIZE][/COLOR]

---

### Post by theShaggy on 2007-12-04
Okay, here's a question:

In both the make and the make install, I notice that there are a bunch of things which read "/lib64/somethingortheother may have been movied."

Unfortunately, the install goes to quick to catch it.

Would these be dependencies that the program is missing, and how do I find them?

**ADDED** OKAY!  I have found a solve for the synch error issues: delete blist.xml.  It will redo it for you.

Now, the only concern, is that I'm getting "Unable to Add User: Uknown Error 241" for a specific MSN contact list.  I have two of them, and one works fine, the other does not.

Anyone want to take a stab?  Just ask what files you may need, and I'll post them.  I'm still poking around, and Meebo is my homey.

---

### Post by hyperair on 2007-12-05
How do you get msnp14 running?! I edited the configure file to show enable_msnp14=yes instead of no, and then:
```

./configure --prefix=/usr/local
make
sudo checkinstall

```

It doesn't seem to be enabled. ><

All right, it seems that there was a linking error and libpurple.so from the non-msnp14 build was linked instead. So I uninstalled the other version of pidgin, and managed to get it to run. Now I've got a new problem entirely. MSN connects complain of an unexpected length. Something to do with gnutls. Did anyone else have that problem?

---

### Post by ImpressMe on 2007-12-06
How many experienced the problem with nicknames? Some guy in this thread was concerned about nickname hijacking, but I think it is a bug.

After installing Pidgin 2.3.0 from the repository provided by Bruce (without uninstalling 2.2.2 first) I suddenly got a wrong nickname on MSN. I think Pidgin grabbed the first nickname on the MSN list and used it as it was my name.

I changed it back and it never happened again.

I didn't find a ticket about this bug in the Pidgin development section.

---

### Post by nw_raptor on 2007-12-06
> **ImpressMe said:**
> How many experienced the problem with nicknames? Some guy in this thread was concerned about nickname hijacking, but I think it is a bug.

After installing Pidgin 2.3.0 from the repository provided by Bruce (without uninstalling 2.2.2 first) I suddenly got a wrong nickname on MSN. I think Pidgin grabbed the first nickname on the MSN list and used it as it was my name.

I changed it back and it never happened again.

I didn't find a ticket about this bug in the Pidgin development section.

i think it changes your local alias, not the screen name which is shown to your buddies. and i think the solution to this is to set an alias yourself and not leave it blank...

---

### Post by Kosimo on 2007-12-06
I'm experiencing a very very strange bug.

When putting the mouse just above some contact, it automatically appears the contact information (yellow small window) with the nickname. address and picture...   

But...   In some partiular cases, on that small yellow window, I see another buddy, and that second one is not on the buddy list but is visible only on this "yellow small window" 

Then, I realize that this second (hided) buddy is online, but I only see it when moving the mouse up to some particular buddy...

Wired, wired, wired, wired...

My english is simple, but I hope you understood me.

Cosimo.

---

### Post by ImpressMe on 2007-12-07
Can anyone explain in plain English what Pidgin supports directly from MSNP14? What is in it for the end user? I understand that offline messages is finally supported, fx.

---

### Post by Johnsie on 2007-12-07
So does multimedia work yet or are they still using 90's style text based messaging?

---

### Post by asnd16 on 2007-12-07
I still have an issue with MSN connecting . . .funny my MSN account works but not the hotmail account.. . . not sure if that has anything to do with it but . . anyone have a solution?

---

### Post by NullHead on 2007-12-07
My msn account doesn't even work when using the windows install of pidgin!! :shock:

EDIT: ok never mind .. it works now for some reason ...

---

### Post by zugu on 2007-12-07
Still no video calls or even voice-only calls for Yahoo! Messenger network? Are they serious? If I want IRC I know where to go ](*,)

Somewhat like someone above me said, welcome to the stone age.

If Skype can do it, why can't they do it? :confused:

---

### Post by bruce89 on 2007-12-07
> **zugu said:**
> If Skype can do it, why can't they do it? :confused:

Are the Pidgin developers paid?

FOSS developers have no obligation to implement features, so don't act like they do.

Nothing stops you writing patches yourself you know, saying as you find this feature useful.

---

### Post by khurrum1990 on 2007-12-07
Hi can someone tell me for which protocols does Pidgin support audio and video conferencing. I have to use Kopete for video calls and I don't like Kopete much.

---

### Post by david.rahrer on 2007-12-07
> **Kynan said:**
> Yep its definitely changing the friendly name to be viewable by others atleast when you first log in.
and i quote my friend.
"lol? wtf was that about? u logged in as me?"

i really hope an update comes out soon.

I'm having the same issue and I installed from getdeb.  Is this happening to anyone on accounts other than MSN?

---

### Post by Kynan on 2007-12-07
Pidgin 2.3.1 is now released, not gonna even try to compile it... been there tried that....waiting for someone to release the repositories or a .deb file :D

---

### Post by Depressed Man on 2007-12-07
> **khurrum1990 said:**
> Hi can someone tell me for which protocols does Pidgin support audio and video conferencing. I have to use Kopete for video calls and I don't like Kopete much.

I don't think Pidgin supports audio/video for anything..

---

### Post by Kynan on 2007-12-07
Yea i dont think it does either. If you want some support for such things Amsn is currently developing support as is Mercury (they both have some webcam support but audio is lacking) and Emesene will eventually have it but its a long way off yet but looks very promising. Kopete has it i am told but i have never used it. Appart from that if there is wengophone which has audio and webcam support and works much like skype and a IM client in one.

But i keep coming back to pidgin due to its lovely simple GUI.

---

### Post by ImpressMe on 2007-12-08
BUMP: Can anyone explain in plain English what Pidgin supports directly from MSNP14? What is in it for the end user? I understand that offline messages is finally supported, fx.

---

### Post by zugu on 2007-12-08
> **bruce89 said:**
> Are the Pidgin developers paid?

FOSS developers have no obligation to implement features, so don't act like they do.

Nothing stops you writing patches yourself you know, saying as you find this feature useful.

I never compared the Skype developers with the Pidgin developers. I just compared the functionality offered by Linux versions of Skype and Pidgin and it's obvious Pidgin is missing some critical features.

For me, they're just two pieces of software. That's it. I'm not interested in the politics behind the projects, heck, I don't even care what the programmers eat, it's not my business. **I won't refrain myself from portraying Pidgin as crippled and incomplete just because its developers work for free.**

If they need more money, maybe they should think about getting a stream of revenue from a business model other than the current one. Or maybe they should quit developing Pidgin alltogether, or whatever. Not my problem.

Also, portraying the free software model of Pidgin as the main reason for the lack of features is just wrong. There are other free software IM clients that have support for either audio or video calls.

It's also wrong because I heard a lot of people using that same reasoning to bash the lack of features in some stagnant closed source applications (the "if-project-X-were-open-source,-the-community-could-improve-it" reasoning).

Pidgin, in its current form, is unusable for people in search of more than text-only instant messaging.

---

### Post by Kosimo on 2007-12-08
Hi guys, as said, new pidgin 2.3.1 is availabe: How about continue the conversation in the new topic?


Here: [http://ubuntuforums.org/showthread.php?t=634819]("http://ubuntuforums.org/showthread.php?t=634819")

Cheers

---

### Post by nw_raptor on 2007-12-08
> **ImpressMe said:**
> BUMP: Can anyone explain in plain English what Pidgin supports directly from MSNP14? What is in it for the end user? I understand that offline messages is finally supported, fx.


Pidgin doesnt support MSNP14 yet. At least not officially. The only way to get MSNP14 is to fiddle with the configure file and compile on your own.

I haven't checked offline messaging yet, but I think they are working on it (since I read a bug report about this). Personal messages (and what others are listening to) work nicely here. You can also set a personal message for your self (and I suspect also what you're listening to via a plugin of some sort).

Edit: I just compiled 2.3.1, and as I suspected, the MSNP14 code is probably removed. AFAIK, that was the intention for 2.3.0, but it probably slipped through.

---

### Post by hyperair on 2007-12-09
Offline messages and personal messages. Not much apart from that I reckon.

---

### Post by david.rahrer on 2007-12-09
> Pidgin, in its current form, is unusable for people in search of more than text-only instant messaging.
The key to its popularity I should say. It works, and works well, for what the vast majority want IM to do - and you only need one client.  That's why I like Pidgin myself - I don't want a miniature three ring circus performing in the corner of my desktop. But if I didn't like it, I could use something else, or take the code and learn how to make it do what I want.  

Creating a local alias in account settings does seem to have corrected the nickname "spoofing" behavior, though I suspect that is still a bug of sorts to be fixed.  Thanks.

---

### Post by hyperair on 2007-12-09
It's fixed in 2.3.1

---

### Post by david.rahrer on 2007-12-09
> **hyperair said:**
> It's fixed in 2.3.1

Cool, thanks.  I'll check out that thread.

---

### Post by ariel on 2007-12-14
> **ImpressMe said:**
> How many experienced the problem with nicknames? Some guy in this thread was concerned about nickname hijacking, but I think it is a bug.

After installing Pidgin 2.3.0 from the repository provided by Bruce (without uninstalling 2.2.2 first) I suddenly got a wrong nickname on MSN. I think Pidgin grabbed the first nickname on the MSN list and used it as it was my name.

I changed it back and it never happened again.

I didn't find a ticket about this bug in the Pidgin development section.

+1... looks like a bug

---

