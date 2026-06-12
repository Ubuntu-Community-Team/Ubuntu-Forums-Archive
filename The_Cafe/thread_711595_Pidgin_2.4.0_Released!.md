---
title: "Pidgin 2.4.0 Released!"
date: 2008-02-29
forum: The Cafe
---

### Post by Kosimo on 2008-02-29
Here the changelog:

>     * libpurple
          o Added support for offline messages for AIM accounts (thanks to Matthew Goldstein)
          o Fixed various problems with loss of status messages when going or returning from idle on MySpaceIM.
          o Eliminated unmaintained Howl backend implementation for the Bonjour protocol. Avahi (or Apple's Bonjour runtime on win32) is now required to use Bonjour.
          o Partial support for viewing ICQ status notes (Collin from ComBOTS GmbH).
          o Support for /notice on IRC.
          o Support for Yahoo! Messenger 7.0+ file transfer method (Thanumalayan S.)
          o Support for retrieving full names and addresses from the address book on Yahoo! Japan (Yusuke Odate)
          o The AIM/ICQ server-side preference for "allow others to see me as idle" is no longer unconditionally set to "yes" even when your libpurple preference is "no."
          o Fix SSL certificate checks for renewed certificates
          o Fix the ability to set vCard buddy icons on Google Talk/XMPP
          o D-Bus fixes on 64bit
          o Fixed retrieval of buddy icons and setting of server-side aliases on Yahoo! and Yahoo! Japan when using an HTTP proxy server (Gideon N. Guillen)
          o Fixed an MSN bug that would leave you appearing offline when transferred to different server 

    * Pidgin
          o Input text area in conversation windows auto-resizes to fit more lines (up to a maximum of 4 lines)
          o Added the ability to theme conversation name colors (red and blue) through your GTK+ theme, and exposed those theme settings to the Pidgin GTK+ Theme Control plugin (Dustin Howett)
          o Fixed having multiple alias edit areas in the infopane (Elliott Sales de Andrade)
          o Save the conversation "Enable Logging" option per-contact (Moos Heintzen)
          o Typing notifications are now shown in the conversation area 

    * Finch
          o Color is used in the buddylist to indicate status, and the conversation window to indicate various message attributes. Look at the sample gntrc file in the man page for details.
          o The default keybinding for dump-screen is now M-D and uses a file request dialog. M-d will properly delete-forward-word, and M-f has been fixed to imitate readline's behavior.
          o New bindings alt+tab and alt+shift+tab to help navigating between the higlighted windows (details on the man page).
          o Recently signed on (or off) buddies blink in the buddy list.
          o New action 'Room List' in the action list can be used to get the list of available chat rooms for an online account.
          o The 'Grouping' plugin can be used for alternate grouping in the buddylist. The current options are 'Group Online/Offline' and 'No Group'.
          o Added a log viewer
          o Added the ability to block/unblock buddies - see the buddy context menu and the menu for the buddy list.
          o Fixed a bug preventing finch working on x86_64 




As always:

Download the sourcecode, and then:
```

./configure
make
sudo make install
```


Don't want to compile?
Get it compiled in .deb from Getdeb! ;)   

[http://getdeb.net/app/Pidgin](http://getdeb.net/app/Pidgin)

Don't forget to uninstall first your current version

---

### Post by SomeGuyDude on 2008-02-29
Sweet. Installing it now. ...once I get all the build dependencies. Oy.

---

### Post by sstusick on 2008-02-29
I was able to download and compiled the source code and install it without any problems :D

---

### Post by Sammi on 2008-02-29
I love Pidgin. Use it daily, as it's a beautiful, simple, and easy program to use, but I'm a bit disappointed with this update, as there are almost no MSN Messenger updates. All my friends and family use MSN, and Pidgin is lacking quite a few features in it's implementation. Was hoping that some MSN features would be added...

---

### Post by bruce89 on 2008-02-29
My PPA might get this if Hardy does.

---

### Post by ntowakbh on 2008-02-29
Awesome.

A bit lazy too mess with compiling from source at the moment, so I'll just wait for a deb on getdeb.net.

---

### Post by Northsider on 2008-02-29
Awsome!  I love PIdgin

---

### Post by steveneddy on 2008-02-29
Since going 64 bit I find it easier to compile it myself.

It just works better for me.

The new Pidgen is OK I guess.

---

### Post by soapytheclown on 2008-02-29
same :( i just hope the emesene project speed up their development :)

---

### Post by Polygon on 2008-02-29
nice

and also, i think doing a 'sudo apt-get build-dep pidgin' will solve all the dependency problems.

and lol@ the ./configure script output:

> 
pidgin 2.4.0

Build GTK+ 2.x UI............. : yes
Build console UI.............. : yes
Build for X11................. : yes

Enable Gestures............... : yes
Protocols to build dynamically : bonjour gg irc jabber msnp9 myspace novell oscar qq sametime simple yahoo zephyr
Protocols to link statically.. :

Build with GStreamer support.. : yes
Build with D-Bus support...... : yes
D-Bus services directory...... : /usr/share/dbus-1/services
Build with NetworkManager..... : no
SSL Library/Libraries......... : Mozilla NSS and GnuTLS
Build with Cyrus SASL support. : no
Use kerberos 4 with zephyr.... : no
Use external libzephyr........ : no
**Has you....................... : yes**

Use XScreenSaver Extension.... : yes
Use X Session Management...... : yes
Use startup notification...... : yes
Build with GtkSpell support... : yes

Build with plugin support..... : yes
Build with Mono support....... : no
Build with Perl support....... : yes
Build with Tcl support........ : yes
Build with Tk support......... : yes

Print debugging messages...... : no

Pidgin will be installed in /usr/local/bin.
Warning: You have an old copy of Pidgin at /usr/bin/pidgin.

configure complete, now type 'make'


---

### Post by NET WT on 2008-03-01
I would like to use this latest version of Pidgin, but I am not sure exactally how. Is this How To going to work for this version? [ HowTo: Compile Pidgin From Source ]("http://ubuntuforums.org/showthread.php?t=613049") Should I follow it? I need step by step instructions, because I don't know enough.

---

### Post by 65 mustang on 2008-03-01
I followed that guide, does anyone else have the problem of not being able to adjust the spacing of the separation between the log and the free text box in the chat windows?

---

### Post by Kosimo on 2008-03-01
Getdeb made an easy three debs for us ;)  2.4.0

[http://getdeb.net/app/Pidgin](http://getdeb.net/app/Pidgin)

---

### Post by SlugO on 2008-03-01
For a long time I've liked Pidgin and used it as my main IM program, atleast on Linux, but I'm becoming increasingly frustrated with it. So please allow me to post this small rant ;)

Pidgin developers only seem interested in three things: usability and AIM and Yahoo protocols. Is this because these protocols are so popular in the US? My extremely rough estimate is that 75% to 95% of the world outside US uses MSN as its IM protocol.

Of course this is far from ideal but it just has so much more features that appeal to non-technical users than Jabber for example. With this being the reality I have to say that I'm extremely unhappy with the speed of Pidgin's MSN plugin development.

Pidgin only supports the **most** basic features of MSN, like messages, normal smileys and file transfers at the speed of 3kb/s. And that's it. No status/offline messages, winks, bearable file transfer speeds or anyhing.

Apparently this is because Pidgin still only supports the incredibly ancient MSNP9 protocol. I was really excited to see that they merged (or atleast claimed to) the MSNP14 code to Pidgin last fall but nothing real has come out of it. I've read somewhere that it is in there and you can hack it out to use it but it doesn't sound very stable.

Now we have a new major update, version 2.4.0 and MSN only got a couple of bug updates so I'm starting to think that it's never going to improve :P

So what's the solution? Convert all my friends and relatives to Jabber? Probably not going to happen as long as non-technical users care a lot more about animated smileys and video than the openness of their IM protocol.

I'm probably first gonna try to hack the MSNP14 features out of there but if I can't even get the status messages to work then I'm gonna switch to Emesene or something until Pidgin improves their MSN features.

I have to say that despite all this I really like Pidgin and it's one of the most usable and versatile IM programs out there. I just really really really wish that the developers would start focusing on protocol (especially MSN) features instead of just usability.

I think it's far from ideal if your program has better usability than the one it's meant to substitute but only has a small fraction of the features.

---

### Post by Kosimo on 2008-03-01
> **SlugO said:**
> For a long time I've liked Pidgin and used it as my main IM program, atleast on Linux, but I'm becoming increasingly frustrated with it. So please allow me to post this small rant ;)

Pidgin developers only seem interested in three things: usability and AIM and Yahoo protocols. Is this because these protocols are so popular in the US? My extremely rough estimate is that 75% to 95% of the world outside US uses MSN as its IM protocol.

Of course this is far from ideal but it just has so much more features that appeal to non-technical users than Jabber for example. With this being the reality I have to say that I'm extremely unhappy with the speed of Pidgin's MSN plugin development.

Pidgin only supports the **most** basic features of MSN, like messages, normal smileys and file transfers at the speed of 3kb/s. And that's it. No status/offline messages, winks, bearable file transfer speeds or anyhing.

Apparently this is because Pidgin still only supports the incredibly ancient MSNP9 protocol. I was really excited to see that they merged (or atleast claimed to) the MSNP14 code to Pidgin last fall but nothing real has come out of it. I've read somewhere that it is in there and you can hack it out to use it but it doesn't sound very stable.

Now we have a new major update, version 2.4.0 and MSN only got a couple of bug updates so I'm starting to think that it's never going to improve :P

So what's the solution? Convert all my friends and relatives to Jabber? Probably not going to happen as long as non-technical users care a lot more about animated smileys and video than the openness of their IM protocol.

I'm probably first gonna try to hack the MSNP14 features out of there but if I can't even get the status messages to work then I'm gonna switch to Emesene or something until Pidgin improves their MSN features.

I have to say that despite all this I really like Pidgin and it's one of the most usable and versatile IM programs out there. I just really really really wish that the developers would start focusing on protocol (especially MSN) features instead of just usability.

I think it's far from ideal if your program has better usability than the one it's meant to substitute but only has a small fraction of the features.

I'm 100% Agree with you. 

It's been a while since Pidgin's devs are working in MSNP14 inclusion, but there are some bugs to be solved before activating it:  Have a look on here

[http://developer.pidgin.im/roadmap](http://developer.pidgin.im/roadmap)

Then,: Pidgin is the global IM program, that just give you basic functionalities. If you're looking for a complete MSN IM, I strongly recommend you to give it a try to emesene. It has a promising future. It supports already MSNP15, P2P file transfers and much more, (still not video) and is in a strong development stadium.    

In my opinion, Pidgin devs are too focus in stability forgetting some basic features for the rest of the world... There is NO WAY that file transfers between MSN clients in pidgin is still locked at 3 kbps...

By the way, the most complete MSN IM in Linux is aMSN 0.97 even if I don't like it, but when I have to make a videocall I use it and it works perfectly.

---

### Post by TrD on 2008-03-01
> **SlugO said:**
> For a long time I've liked Pidgin and used it as my main IM program, atleast on Linux, but I'm becoming increasingly frustrated with it. So please allow me to post this small rant ;)

Pidgin developers only seem interested in three things: usability and AIM and Yahoo protocols. Is this because these protocols are so popular in the US? My extremely rough estimate is that 75% to 95% of the world outside US uses MSN as its IM protocol.

Of course this is far from ideal but it just has so much more features that appeal to non-technical users than Jabber for example. With this being the reality I have to say that I'm extremely unhappy with the speed of Pidgin's MSN plugin development.

Pidgin only supports the **most** basic features of MSN, like messages, normal smileys and file transfers at the speed of 3kb/s. And that's it. No status/offline messages, winks, bearable file transfer speeds or anyhing.

Apparently this is because Pidgin still only supports the incredibly ancient MSNP9 protocol. I was really excited to see that they merged (or atleast claimed to) the MSNP14 code to Pidgin last fall but nothing real has come out of it. I've read somewhere that it is in there and you can hack it out to use it but it doesn't sound very stable.

Now we have a new major update, version 2.4.0 and MSN only got a couple of bug updates so I'm starting to think that it's never going to improve :P

So what's the solution? Convert all my friends and relatives to Jabber? Probably not going to happen as long as non-technical users care a lot more about animated smileys and video than the openness of their IM protocol.

I'm probably first gonna try to hack the MSNP14 features out of there but if I can't even get the status messages to work then I'm gonna switch to Emesene or something until Pidgin improves their MSN features.

I have to say that despite all this I really like Pidgin and it's one of the most usable and versatile IM programs out there. I just really really really wish that the developers would start focusing on protocol (especially MSN) features instead of just usability.

I think it's far from ideal if your program has better usability than the one it's meant to substitute but only has a small fraction of the features.

I agree with all that you said. For how long has MSNP14 been unstable? I now use emesene but I really like pidgin, just wish they'd give MSN some features. Are AIM and Yahoo so big in the US? Here in Europe I've never came across anyone using other than MSN.

---

### Post by Baptiste on 2008-03-01
To install all the dependencies just do in a terminal (with the sources enables in the source.list) :

```
sudo apt-get build-dep pidgin
```

That's it!

---

### Post by Runn3r.cze on 2008-03-01
i've got a problem with finch. i installed version 2.4 of pidgin from deb package from getdeb. i also installed new versions of padgin-data and libpurple. pidgin works fine, but finch doesn't work at all.
i always get an error that finch depends on libpurple 2.2.1 which is not installed. 
i also tried installing pidgin from sourcecode but still the same error. 
does anyone know how to solve this?

---

### Post by Kosimo on 2008-03-01
> **Runn3r.cze said:**
> i've got a problem with finch. i installed version 2.4 of pidgin from deb package from getdeb. i also installed new versions of padgin-data and libpurple. pidgin works fine, but finch doesn't work at all.
i always get an error that finch depends on libpurple 2.2.1 which is not installed. 
i also tried installing pidgin from sourcecode but still the same error. 
does anyone know how to solve this?

Can I ask you why do you use finch?

---

### Post by Techwiz on 2008-03-01
Is there any way to just update, I don't want to have to re-add all my friends and protocols! I can't remember all of them!

---

### Post by loud_tiger on 2008-03-01
> **Techwiz said:**
> Is there any way to just update, I don't want to have to re-add all my friends and protocols! I can't remember all of them!

it shouldn't disrupt your settings, but you can copy the .purple folder from your home directory just to be sure.

---

### Post by ntowakbh on 2008-03-01
Is it just me, or has the little "keyboard typing image" gone AWOL? In place of it they added text, but I much prefer the image, as it's is harder to see the light gray text.  I looked through the options and I haven't found an option to enable it...

---

### Post by ImpressMe on 2008-03-01
> **Sammi said:**
> But I'm a bit disappointed with this update, as there are almost no MSN Messenger updates. All my friends and family use MSN, and Pidgin is lacking quite a few features in it's implementation. Was hoping that some MSN features would be added...

Me too, I miss the personal status messages a lot, and especially the offline messages. It is also a shame that we can't add emoticons and animated emoticons. We use it a LOT on MSN, and its kind of boring to be in Pidgin without them. But nice that all the rest of the kiddy features are absent...

Above all, BTW, I miss direct file transfers in the MSN protocol in Pidgin. The current file transfers SUCK.

Aaaih and the dynamic input field is a disaster! Max 4 lines big and you cannot resize it. Why don't they just start coding enhancements instead of the latest UI "improvements" that were changed back later anyway due to negative feedback. I think users approve more of fast file transfers than of needless small changes.

I downgraded in a hurry to 2.3.1. I can't stand it.

---

### Post by bruce89 on 2008-03-01
> **bruce89 said:**
> My PPA might get this if Hardy does.

Done:
> 
pidgin (1:2.4.0-0ubuntu1+ppa1) gutsy; urgency=low

  * New upstream release
  * debian/control:
    - Unbump libnss3-dev, gutsy uses old Firefox one.
  * 00_debian-ca-certs.patch:
    - Remove, makes build fail.
  * 22_makedocs_build.patch:
    - Dropped, no longer required.

 -- Bruce Cowan < [email]bcowan@fastmail.co.uk[/email]>   Sat, 01 Mar 2008 17:14:25 +0000

I'm not sure why I had to remove those 2 patches, but it wouldn't build otherwise. Once Hardy gets 2.4.0, I will backport it.

---

### Post by Sammi on 2008-03-01
Just checked out Emesene, and as a forced MSN user, I must say that it delivers to my needs much better than Pidgin. The UI of Pidgin and Emesene look very much alike, but Emesene has the extra MSN features I would like.

---

### Post by Runn3r.cze on 2008-03-01
> **Kosimo said:**
> Can I ask you why do you use finch?

because i just like it... i like working in console and at finch i like it uses the same settings as pidgin so i don't have to set up two programms.
but it already works. maybe it needed a system restart...

---

### Post by sstusick on 2008-03-01
I downgraded to 2.2.1. The available/status message doesn't seem to work in 2.4.0, nor does spellchecking. 

It seems all Pidgin is, is useless changes on the GUI.

I prefer the way GAIM was, and wish they'd stick to the original idea, there was nothing wrong with it.

---

### Post by JacobRogers on 2008-03-01
It seems funny to me that people are complaining about the lack of moving and complex smilies in Pidgin.  If you ask me that sounds more like a FEATURE than a bug LOL.

---

### Post by sstusick on 2008-03-01
I disable all smilies, they're annoying.

---

### Post by Mazza558 on 2008-03-01
> **Sammi said:**
> Just checked out Emesene, and as a forced MSN user, I must say that it delivers to my needs much better than Pidgin. The UI of Pidgin and Emesene look very much alike, but Emesene has the extra MSN features I would like.

I was just about to say the same thing. The plugins are unbelievably powerful! How about changing my avatar to the album cover of whichever song I'm listening to? gmail support? Popup window notifying you when a new user comes online (if you want)? How about the youtube thumbnails feature? Create Tinyurl links with "/tinyurl"? Send someone a random xkcd comic with /xkcd <random>? 

This thing is unbelievable! It's like the Amarok of messaging programs (as long as you use MSN).

---

### Post by SomeGuyDude on 2008-03-01
As a note, if you use the Pidgin screenlet, you have to use the .deb, since installing from source doesn't seem to make the screenlet recognize that it's installed. I have no idea why (same reason something installed from source sometimes doesn't show up in synaptic, I assume).

---

### Post by DJ_Peng on 2008-03-01
Does anyone know if Gutsy will get this update or if we'll need to manually install the deb or upgrade to Hardy to get it?

---

### Post by Mazza558 on 2008-03-01
> **DJ_Peng said:**
> Does anyone know if Gutsy will get this update or if we'll need to manually install the deb or upgrade to Hardy to get it?

We might get it if it's stable enough, but I'm not that clear on which updates are allowed and which aren't.

---

### Post by GoHabsGo on 2008-03-01
> **Mazza558 said:**
> I was just about to say the same thing. The plugins are unbelievably powerful! How about changing my avatar to the album cover of whichever song I'm listening to? gmail support? Popup window notifying you when a new user comes online (if you want)? How about the youtube thumbnails feature? Create Tinyurl links with "/tinyurl"? Send someone a random xkcd comic with /xkcd <random>? 

This thing is unbelievable! It's like the Amarok of messaging programs (as long as you use MSN).

I have to admit, emesene is powerful !! It's farrrr better than Pidgin for MSN. File transfer are fast, plugins are cool, the GUI is effecient and it's light. Give it a try people !!!! Best MSN client on Linux, by far !!!:guitar:

---

### Post by bruce89 on 2008-03-01
> **sstusick said:**
> I downgraded to 2.2.1. The available/status message doesn't seem to work in 2.4.0, nor does spellchecking. 

Where are you getting your copy from?

> **Mazza558 said:**
> We might get it if it's stable enough, but I'm not that clear on which updates are allowed and which aren't.

You won't, see [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates).

---

### Post by Kosimo on 2008-03-01
> **DJ_Peng said:**
> Does anyone know if Gutsy will get this update or if we'll need to manually install the deb or upgrade to Hardy to get it?

We are talking about it on here:

[http://ubuntuforums.org/showthread.php?t=711596](http://ubuntuforums.org/showthread.php?t=711596)

---

### Post by 23meg on 2008-03-01
That thread is about Hardy. Gutsy is a stable release, thus will only get updates for security vulnerabilities and bugs with high impact.

---

### Post by DJ_Peng on 2008-03-01
Thanks. I guess I'll have to install the upgrade myself until I make the move to testing Hardy. Now to decide when I want o do what upgrade. :lol:

---

### Post by Kosimo on 2008-03-01
> **23meg said:**
> That thread is about Hardy. Gutsy is a stable release, thus will only get updates for security vulnerabilities and bugs with high impact.

Oooops, sorry, I read the previous post too fast and I didn't realize about he/she's meaning about including this new version in Gutsy. And of course it won't be included.

---

### Post by DJ_Peng on 2008-03-01
> **Kosimo said:**
> 
Don't want to compile?
Get it compiled in .deb from Getdeb! ;)   

[http://getdeb.net/app/Pidgin](http://getdeb.net/app/Pidgin)

Don't forget to uninstall first your current version
Damn. Remove the first? Makes me just want to wait for Hardy. ;)

Jokes aside, what's the order for installing those three debs? I can't remember from last time and it's not specified anywhere. Also, will I lose my plugins with these debs? Having to reinstall too many plugins could be a deal breaker on this box.

---

### Post by sstusick on 2008-03-01
> **bruce89 said:**
> Where are you getting your copy from?
From the Pidgin.im website.

---

### Post by bruce89 on 2008-03-01
> **sstusick said:**
> From the Pidgin.im website.

They probably have made a mess of the packaging.

---

### Post by Polygon on 2008-03-01
> **DJ_Peng said:**
> Damn. Remove the first? Makes me just want to wait for Hardy. ;)

Jokes aside, what's the order for installing those three debs? I can't remember from last time and it's not specified anywhere. Also, will I lose my plugins with these debs? Having to reinstall too many plugins could be a deal breaker on this box.

install all of them at the same time

put them in a folder like on your desktop

then open terminal

cd to that directory

then do a 

sudo dpkg -i *.deb

and it will install all 3 and not complain about dep. problems

---

### Post by DJ_Peng on 2008-03-01
Thanks. I'll try that after dinner. I know there was something above about moving a folder. I'll read back for it later as well.

---

### Post by snkiz on 2008-03-01
> **Sammi said:**
> I love Pidgin. Use it daily, as it's a beautiful, simple, and easy program to use, but I'm a bit disappointed with this update, as there are almost no MSN Messenger updates. All my friends and family use MSN, and Pidgin is lacking quite a few features in it's implementation. Was hoping that some MSN features would be added...

good luck with that the pidgin devs are closed minded its takes an army of complaints to change thier minds

---

### Post by fetisha on 2008-03-02
> **NET WT said:**
> I would like to use this latest version of Pidgin, but I am not sure exactally how. Is this How To going to work for this version? [ HowTo: Compile Pidgin From Source ]("http://ubuntuforums.org/showthread.php?t=613049") Should I follow it? I need step by step instructions, because I don't know enough.

I followed those steps and when I get to the part about getting to the new directory it gives me this error:

bash: cd: pidgin-2.4.0/: No such file or directory

I downloaded the source onto my desktop, extracted it there. Am I supposed to extract it into somewhere else?

---

### Post by spamzilla on 2008-03-02
I cannot connect to MSN and get the following message:

> SSL support is needed for MSN. Please install a supported SSL library

What files do I need to install to get MSN working?

---

### Post by SomeGuyDude on 2008-03-02
> **spamzilla said:**
> I cannot connect to MSN and get the following message:



What files do I need to install to get MSN working?

```
sudo apt-get install libnss3-dev libnspr4-dev
```

Then reinstall Pidgin. I had the same issue.

---

### Post by spamzilla on 2008-03-02
> **SomeGuyDude said:**
> ```
sudo apt-get install libnss3-dev libnspr4-dev
```

Then reinstall Pidgin. I had the same issue.

libnss3-dev is already the newest version.
libnspr4-dev is already the newest version.
libnspr4-dev set to manually installed.

I already had those files installed, ive reinstalled pidgin several times, including reverting back the the repo version, and I still get this error :/

edit

I have just reinstalled libnspr4-dev and msn is now working :)

---

### Post by Ardrias on 2008-03-02
This release drove me to use emesene instead of Pidgin for MSN...

---

### Post by Namtabmai on 2008-03-02
> 
o Input text area in conversation windows auto-resizes to fit more lines (up to a maximum of 4 lines)


Awesome, now how do I disable this, or at least allow me to make the area bigger regardless of how much text I type?

---

### Post by Techwiz on 2008-03-02
> **Namtabmai said:**
> Awesome, now how do I disable this, or at least allow me to make the area bigger regardless of how much text I type?

I agree!

---

### Post by Sammi on 2008-03-02
> **Ardrias said:**
> This release drove me to use emesene instead of Pidgin for MSN...Same for me.

---

### Post by andrewabc on 2008-03-02
> **Ardrias said:**
> This release drove me to use emesene instead of Pidgin for MSN...

I tried it. HTTP port 80 connect does not work for me.

---

### Post by CaptainCabinet on 2008-03-02
Just updated my version of Pidgin.
A very useful program indeed. :)

---

### Post by DJ_Peng on 2008-03-02
Is MSN the only service people are having so much trouble with? I don't run MSN myself, but I'm wondering if I should just hold off on the update a little bit anyway. I use Jabber (GoogleTalk), AIM, and Yahoo! (in descending order of activity) so that's what I'm mostly concerned with. It seems kind of like TabMix Plus for Firefox. People love it, but every time I help test new versions I see TMP causing problems so much I wonder if it's really worth all the hassles. Plus I just don't see what it does that I don't already have with current extensions, but I stay away from it simply because too many nighlt build threads have issues with TMP for my taste.

---

### Post by psychok7 on 2008-03-02
> **Runn3r.cze said:**
> because i just like it... i like working in console and at finch i like it uses the same settings as pidgin so i don't have to set up two programms.
but it already works. maybe it needed a system restart...

HOw did you solve your problem? my finch also doesnt want to install trough synaptic since i updated the pidgin-data. can anyone help me? what should i do?

---

### Post by DJ_Peng on 2008-03-02
I ended up installing the upgrade. Rather than uninstalling Pidgin I saw that I could simply go to the directory I downloaded to and run ```
sudo dpkg -i *.deb
``` and it replaced the current packages with no problem. The only issue I'm seeing is that I can't see status messages from most of my buddies. Has anyone come up with a way to get them back?

---

### Post by Mazza558 on 2008-03-02
> **DJ_Peng said:**
> Is MSN the only service people are having so much trouble with? I don't run MSN myself, but I'm wondering if I should just hold off on the update a little bit anyway. I use Jabber (GoogleTalk), AIM, and Yahoo! (in descending order of activity) so that's what I'm mostly concerned with. It seems kind of like TabMix Plus for Firefox. People love it, but every time I help test new versions I see TMP causing problems so much I wonder if it's really worth all the hassles. Plus I just don't see what it does that I don't already have with current extensions, but I stay away from it simply because too many nighlt build threads have issues with TMP for my taste.

Remember that outside of the US, MSN is a very widely used protocol. For those of us in Europe, we can only really use the MSN protocol if we want to talk to friends.

---

### Post by DJ_Peng on 2008-03-02
Ouch, That sucks. I wasn't aware that people outside of the US had so few choices for IM. Sounds like another case of bug number one needing to get resolved..

---

### Post by Ardrias on 2008-03-02
10 years ago everyone used IRC... Then along came Microsoft :| 

Well actually ICQ was quite popular here in Sweden at least. It's still a better protocol than MSN, but IRC is where the real action is!

---

### Post by Iceni on 2008-03-02
IRC is still the best chat. No sillyness, just chat software.

---

### Post by DocHoliday52090 on 2008-03-02
One thing I've noticed is that people almost consistently laud Pidgin as being 'lightweight'. 

This annoys me quite a bit as Pidgin ranks high up on the memory usage ladder, almost always taking 25 - 35 mb. Trillian Astra, Miranda, and other native clients consume far less, most in the 13 - 18 range. 

What's going on? Why is Pidgin such a bloated memory hog for such little function?

Don't get me wrong - I love Pidgin and find it the easiest to use and simplest multi-protocol program out there, but for the little that it does it consumes far too much ram.

---

### Post by Namtabmai on 2008-03-02
> **DocHoliday52090 said:**
> This annoys me quite a bit as Pidgin ranks high up on the memory usage ladder, almost always taking 25 - 35 mb. Trillian Astra, Miranda, and other native clients consume far less, most in the 13 - 18 range. .

Given the other "native" clients you mention I guess your talking about Windows here not Linux? Anyway if you are there are 2 points
1) The memory column in Windows Task Manager is virtually meaningless
2) Pidgin uses GTK so this needs to be loaded where as the native ones use the windows GUI which is already loaded so of course they'd appear more memory efficient.

Comparative I'm running Pidgin in Gnome (so the GTK stuff will already be loaded  and used by every Gnome program) and Pidgin is using under 12Mb for me.

Perhaps someone should start a native messenger program for Windows that uses libpurple, similar to the way Adium is native to OS X.

---

### Post by SomeGuyDude on 2008-03-02
> **Namtabmai said:**
> Given the other "native" clients you mention I guess your talking about Windows here not Linux? Anyway if you are there are 2 points
1) The memory column in Windows Task Manager is virtually meaningless
2) Pidgin uses GTK so this needs to be loaded where as the native ones use the windows GUI which is already loaded so of course they'd appear more memory efficient.

Comparative I'm running Pidgin in Gnome (so the GTK stuff will already be loaded  and used by every Gnome program) and Pidgin is using under 12Mb for me.

Perhaps someone should start a native messenger program for Windows that uses libpurple, similar to the way Adium is native to OS X.

13.8MB here and it's been going for a good six hours or so (laptop, thus my uptime isn't days and days like some of you folks).

---

### Post by Vadi on 2008-03-02
> **Namtabmai said:**
> Awesome, now how do I disable this, or at least allow me to make the area bigger regardless of how much text I type?

> (11:14:35 PM) The topic for #pidgin is: You can't resize the text input in 2.4, nor disable auto-resizing; this won't change. 

Have fun, buddy!

---

