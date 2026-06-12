---
title: "Pidgin 2.5.3 Released!   (.deb)"
date: 2008-12-21
forum: The Cafe
---

### Post by Kosimo on 2008-12-21
Pidgin reached [2.5.3]("http://www.pidgin.im/") version! 

Here the changelog: 

> -libpurple:
     * The Buddy State Notification plugin no longer prints duplicate
       notifications when the same buddy is in multiple groups. (Florian
       Quèze)
     * The Buddy State Notification plugin no longer turns JID's, MSN
       Passport ID's, etc. into links. (Florian Quèze)
     * purple-remote now has a "getstatusmessage" command to retrieve
       the text of the current status message.
     * Various fixes to the nullprpl. (Paul Aurich)
     * Fix a crash when accessing the roomlist for an account that's not
       connected. (Paul Aurich)
     * Fix a crash in purple_accounts_delete that happens when this
       function is called before the buddy list is initialized.
       (Florian Quèze)
     * Fix use of av_len in perl bindings to fix some off-by-one bugs
       (Paul Aurich)
     * On ICQ, advertise the ICQ 6 typing capability.  This should fix
       the reports of typing notifications not working with third-party
       clients. (Jaromír Karmazín)
     * Many QQ fixes and improvements, including the ability to connect
       using QQ2008 protocol and sending/receiving of long messages.
       The recommended version to use is still QQ2005.
     * Fix a crash with DNS SRV lookups. (Florian Quèze)
     * Fix a crash caused by authorization requests. (Florian Quèze)
 .
   - Gadu-Gadu:
     * Add support for IM images. (Adam Strzelecki)
     * Gadu-Gadu now checks that UID's are valid. (Adam Strzelecki)
     * Gadu-Gadu now does proper charset translations where needed. (Adam
       Strzelecki)
 .
   - MSN:
     * Fix an error with offline messages by shipping the *new*
       "Microsoft Secure Server Authority" and the "Microsoft Internet
       Authority" certificates. These are now always installed even when
       using --with-system-ssl-certs because most systems don't ship
       those intermediate certificates.
     * The Games and Office media can now be set and displayed (in
       addition to the previous Music media). The Media status text now
       shows the album, if possible.
     * Messages sent from a mobile device while you were offline are now
       correctly received.
     * Server transfers after you've been connected for a long time
       should now be handled correctly.
     * Many improvements to handling of "federated" buddies, such as those
       on the Yahoo network.
     * Several known crashes have been resolved.
     * Many other fixes and code cleanup.
 .
   - MySpace:
     * Respect your privacy settings set using the official MySpace client.
     * Add support for blocking buddies.
     * Fix a bug where buddies didn't appear in their correct groups the
       first time you sign into your account.
     * Properly disconnect and sign out of the service when logging off.
     * Support for foreground and background font colors in outgoing IMs.
     * Support for background font colors in incoming IMs.
     * Many other fixes and code cleanup.
 .
   - Sametime:
     * Fix insanely long idle times for Sametime 7.5 buddies by assuming
       0 idle time if the idle timestamp is in the future. (Laurent
       Montaron)
     * Fix a crash that can occur on login. (Raiko Nitzsche)
 .
   - SIMPLE:
     * Fix a crash when a malformed message is received.
     * Don't allow connecting accounts if no server name has been
       specified. (Florian Quèze)
 .
   - XMPP:
     * Fix the namespace URL we look for in PEP reply stanzas to match
       the URL used in the 'get' requests (Paul Aurich)
     * Resources can be set to the local machine's hostname by using
       __HOSTNAME__ as the resource string. (Jonathan Sailor)
     * Resources can now be left blank, causing the server to generate a
       resource for us where supported. (Jonathan Sailor)
     * Resources now default to no value, but "Home" is used if the
       server refuses to provide a resource.
     * Quit trying to get user info for MUC's. (Paul Aurich)
     * Send "client-accepts-full-bind-result" attribute during SASL
       login. This will fix Google Talk login failures if the user
       configures the wrong domain for his/her account.
     * Support new  element to indicate no XEP-0084 User
       Avatar. (Paul Aurich)
     * Fix SHA1 avatar checksum errors that occur when one of the bytes
       in a checksum begins with 0. (Paul Aurich)
     * Fix a problem with duplicate buddies. (Paul Aurich)
 .
   - Yahoo:
     * Corrected maximum message lengths for Yahoo!
     * Fix file transfers with older Yahoo protocol versions.
 .
   - Zephyr:
     * Enable auto-reply, to emulate 'zaway.' (Toby Schaffer)
     * Fix a crash when an account is configured to use tzc but tzc is
       not installed or the configured tzc command is invalid. (Michael
       Terry)
     * Fix a 10 second delay waiting on tzc if it is not installed or the
       configured command is invalid. (Michael Terry)
 .
   - Pidgin:
     * On GTK+ 2.14 and higher, we're using the gtk-tooltip-delay setting
       instead of our own (hidden) tooltip_delay pref.  If you had
       previously changed that pref, add a line like this to
       ~/.purple/gtkrc-2.0 (where 500 is the timeout (in ms) you want):
           gtk-tooltip-timeout = 500
       To completely disable tooltips (e.g. if you had an old
       tooltip_delay of zero), add this to ~/.purple/gtkrc-2.0:
           gtk-enable-tooltips = 0
     * Moved the release notification dialog to a mini-dialog in the
       buddylist. (Casey Ho)
     * Fix a crash when closing an authorization minidialog with the X
       then immediately going offline. (Paul Aurich)
     * Fix a crash cleaning up custom smileys when Pidgin is closed.
     * Fix adding a custom smiley using the context menu in a conversation
       if no custom smilies have previously been added using the smiley
       manager.
     * Improved support for some message formatting in conversations.
     * Allow focusing the coversation history or userlist with F6.
     * Fixed the Send Button plugin to avoid duplicate buttons in a single
       conversation.
     * Double-clicking a saved status will now activate it and close the
       saved status manager, rather than edit the status.
 .
   - Finch:
     * Allow binding meta+arrow keys for actions.
     * Added default meta+erase binding for delete previous word.
     * Added "Show When Offline" to buddy menus, so a plugin is no longer
       needed.



Get an easy .deb from [GETDEB]("http://www.getdeb.net/app/Pidgin").

OR, download the source code, then:

```
./configure
make
sudo make install
```


EDIT: I've made a .deb to install latest pidgin-libnotify 0.14 which allows to see nice notification windows.

Download [libnotify_0.14-1_i386.deb]("http://kosimo.googlepages.com/pidgin-libnotify_0.14-1_i386.deb")  (for intrepid 32bits)

---

### Post by Vadi on 2008-12-21
Bad link... here's a better one: [http://www.getdeb.net/search.php?keywords=pidgin](http://www.getdeb.net/search.php?keywords=pidgin)

---

### Post by Grant A. on 2008-12-21
I don't use Pidgin, its IRC client is horrible. I don't have much use for MSN or AIM, since AIM now works straight through gmail.\\:D/

---

### Post by Kosimo on 2008-12-21
> **Vadi said:**
> Bad link... here's a better one: [http://www.getdeb.net/search.php?keywords=pidgin](http://www.getdeb.net/search.php?keywords=pidgin)

Thanks ;)

Bad link has been edit.

---

### Post by Polygon on 2008-12-21
good to see some msn fixes, by far the most buggy protocol on pidgin

---

### Post by koffeinöverdos on 2008-12-21
Wow uhh i'm showing up as my own QQ buddy. MSN seemed to connect a lot faster than normal though, that's good because it took forever.

---

### Post by andrewabc on 2008-12-21
Any idea if they improved MSN HTTP connections?
It has never worked for me. Some other messengers do work, but they are really bad to use.

I use a static IP address (on my router to connect to internet, computer is auto eth0), and port 80 must be used.
I've tried all settings on pidgin.

---

### Post by kostkon on 2008-12-21
Nice! And at last!!:
> The Buddy State Notification plugin no longer prints duplicate
notifications when the same buddy is in multiple groups. (Florian
Quèze)

---

### Post by Vadi on 2008-12-21
I'm amused by their redesigned webpage. First, it tells you that there is a download available for Ubuntu and then it tells you that no, there is none, go compile the source code.

Nice thinking...

---

### Post by kevdog on 2008-12-21
I love compiling from source: 
[http://ubuntuforums.org/showthread.php?t=975783](http://ubuntuforums.org/showthread.php?t=975783)

---

### Post by doorknob60 on 2008-12-21
Nice, it came in with my daily pacman -Syu in Arch, rolling release FTW, looks good, especially for MSN.

---

### Post by IainPurdie on 2008-12-22
This could be a great release if they've fixed a lot of the MSN bugs. I've been using the version from the Ubuntu repository for ages and would love to update to this one, but can't seem to get it to work.

I've downloaded the three .deb packages.

pidgin-data installs fine, but the other two fail on dependencies. libpurple tells me I must have libgadu3 installed (I do - the latest version from the repository) and pidgin_2.5.3-1 tells me I need libgtk2.0-0 (again, I do have the latest version installed).

Any ideas why these aren't being picked up?

---

### Post by Eisenwinter on 2008-12-22
> **doorknob60 said:**
> Nice, it came in with my daily pacman -Syu in Arch, rolling release FTW, looks good, especially for MSN.
+1, just upgraded.

---

### Post by Kosimo on 2008-12-22
Guys I just made a .deb from source that installs the latest pidgin-libnotify 0.14 
Tested on Intrepid 32 bits with latest pidgin 2.5.3.


Download [libnotify_0.14-1_i386.deb]("http://kosimo.googlepages.com/pidgin-libnotify_0.14-1_i386.deb")

Good luck! ;)

By the way, once installed you have to restart pidgin and enable this specific plug-in: Tools-Plugins

---

### Post by ithanium on 2008-12-22
downloaded it today, works good as always. Thanks!

---

### Post by Polygon on 2008-12-22
there is also a usage survey on their website ([www.pidgin.im](www.pidgin.im)). Seems like a good way to get your voice heard on what features you want first (it talked about voice/video support, encrypted messaging, actually encrypted account information, etc) so fill it out! it takes like 2 minutes =)

---

### Post by Listen2TheTruth on 2008-12-22
Read this post before it gets deleted and my account suspended.

I guess there will always be people who can look at gold and throw it away and think its "fake" or "can't be" or "im an ignorant moron". Pick one of the above im pretty sure you are right up there with any of the above described. 

Ok to clarify. I've build and been using an HHO system in my car for the past 6 months. If anyone can tell you about results, its not a oil lobbied PhD holder, a fake scientist or a opinionated freak who is so paraniod thinking his birth is a conspiracy, no..but someone like me- a regular consumer who has used it and loves it to death!

I drive a volvo that gets 31 MPG HWY with my HHO system off, 53MPG HWY with it on. Any questions? Didnt think so! 

Besides some of you (removed by moderator) forgot that Hydrogen can be extracted from water using electroalysis with solar panels, windenergy etc. so although the extraction process may not be 100% efficient, it sure as hell can be "FREE" if we choose to. 

Oil requires a hell lot of energy to obtain too. Researching, Drilling, Extracting, destilling etc...look at all the processes that it has to go through before it can be made available as a combustable gas. Do some research before you post your ignorant, nonsensical opinions on a topic you have no idea about! 

Do a google search on zero point energy or zero field energy, a guy in kansas invented a device that produces more energy (output)than the energy put into the system to extract it (input). Thats the future of energy "creation" and if you are one of those misleading, good-for-nothing opinionated pinheads thinking "oh matter can neither be created nor distroyed - i learned that in High School...waahhh waahhhh cryyy cryyy" then all i have to say is "you have been living on the moon" for science and technology is a dynamic world and it changes every nanosecond of your existence! So get with the plan and stop being ignorant and crying about a solution that really works!

Lastly, watch ZEITGEIST 1 + 2 and be changed forever.

---

### Post by Tom--d on 2008-12-22
Is there any debs for Hardy? There are none on Getdeb

---

### Post by Kosimo on 2008-12-22
> **Tom--d said:**
> Is there any debs for Hardy? There are none on Getdeb

Don't looks like.
In getdeb you'll find 2.5.2 for hardy. You should then try to compile by yourself if you want to have the latest version

---

### Post by Eisenwinter on 2008-12-22
nothing wrong with compiling from source every now and then, it's good - in fact it allows you to configure the program exactly to your needs.

Go and get ffmpeg from the ubuntu repos, and try it out, see how many features were configured to be enabled by default. Then, go and get the svn version of ffmpeg, and enable all the options you need, compile and install, it's WAY better than the precompiled version.

---

### Post by Vadi on 2008-12-22
Well, except the fact that you don't get menu entries automatically and you need to keep sources about if you want to install.

getdeb will have an 8.04 version soon

---

### Post by jcm4 on 2008-12-22
> **Vadi said:**
> I'm amused by their redesigned webpage. First, it tells you that there is a download available for Ubuntu and then it tells you that no, there is none, go compile the source code.

Nice thinking...

Thank God for getdeb....

---

### Post by Vadi on 2008-12-23
They're having a survey on their website, voice your opinion: [http://www.pidgin.im/survey/index.php?sid=84494](http://www.pidgin.im/survey/index.php?sid=84494)

---

### Post by jcm4 on 2008-12-23
I find it quite funny how their survey says that they have no translated surveys....in English!

---

### Post by Johnsie on 2008-12-23
Whenever MYspaceIM came out I went into the #gaim irc channel and suggested they added support for it. They laughed in my face. No way were they ever going to support that horrible site, even if it did have 50 million users. I wonder what changed their mind...

Turned out MyspaceIM seems to have flopped. Which is funny because I was wrong and they were right but they implemented it anyway :-D

I have to say, I have never willingly used that feature to talk to anyone. I don't use the facebook plugin either, because I dont want people thinking I'm one of those weirdos who spends all their time on facebook.

---

### Post by Tom--d on 2008-12-23
> **Eisenwinter said:**
> nothing wrong with compiling from source every now and then, it's good - in fact it allows you to configure the program exactly to your needs.

Go and get ffmpeg from the ubuntu repos, and try it out, see how many features were configured to be enabled by default. Then, go and get the svn version of ffmpeg, and enable all the options you need, compile and install, it's WAY better than the precompiled version.

Compiling from source is fun but I don't have the time now. I just want the new Pidgin on Hardy :P

---

### Post by Johnsie on 2008-12-23
> **doorknob60 said:**
> Nice, it came in with my daily pacman -Syu in Arch, rolling release FTW, looks good, especially for MSN.

I think I'm going to have to give this arch business a try. Ubuntu is a fine vintage, but I want the newer stuff.

---

### Post by FuturePilot on 2008-12-23
> **Vadi said:**
> They're having a survey on their website, voice your opinion: [http://www.pidgin.im/survey/index.php?sid=84494](http://www.pidgin.im/survey/index.php?sid=84494)

Took the survey. :)

---

### Post by Eisenwinter on 2008-12-23
> **FuturePilot said:**
> Took the survey. :)
Me too, overall, I'm satisfied with the way Pidgin works, there's only 2 little things I want fixed/improved.

---

### Post by Vadi on 2008-12-23
Getdeb.net will have an 8.04 version soon(ish). Everybody's gotten busy with work lately and not enough people to help out packaging ;(

---

### Post by Tom--d on 2008-12-23
> **Vadi said:**
> Getdeb.net will have an 8.04 version soon(ish). Everybody's gotten busy with work lately and not enough people to help out packaging ;(

Thanks :)

---

### Post by Kosimo on 2008-12-23
Guys, Pidgin 2.5.3a is here!   "Fixed a bug when using the fast-user-switch applet" 


Download it from [getdeb.]("http://www.getdeb.net/app/Pidgin")

---

### Post by Polygon on 2008-12-23
is version 2.5.3 a bugfix from the offical pidgin team or just the person who was packaging it?

---

### Post by Vadi on 2008-12-23
8.04 packages are now available: [http://www.getdeb.net/app/Pidgin](http://www.getdeb.net/app/Pidgin)

the a version is because Pidgin got a bad commit that broke the fast user switch applet, Pidgin devs fixed it so getdeb published another version.

edit: yes, it's a bugfix from the pidgin team.

---

### Post by Polygon on 2008-12-23
ok. is that the only thing that this 'a' release fixed? i noticed on windows vista, pidgin crashes every time you try to quit out of it. Surely if they would of tested it before releasing it they would of found that out..... *grumbles*

---

### Post by Vadi on 2008-12-23
> **Polygon said:**
> ok. is that the only thing that this 'a' release fixed? i noticed on windows vista, pidgin crashes every time you try to quit out of it. Surely if they would of tested it before releasing it they would of found that out..... *grumbles*

Yeah, only the fast user switch applet.

---

### Post by Vadi on 2008-12-24
If you had some dependency error with Perl, do the update that came out for it in Ubuntu recently, and try again. It'll install fine.

---

### Post by Johnsie on 2008-12-24
Don't install debs from external sources.  It's very easy for someone to insert an evil shell script.

---

### Post by Vadi on 2008-12-24
Yep, true, but getdeb for 2 years now did not have a single security incident. Should say something.

All of the .deb sources are available too.

---

### Post by kevdog on 2008-12-24
why wouldn't you just compile and install from source?  I mean seriously is everyone just that lazy?  It takes less than 10 minutes to compile!

---

### Post by Kosimo on 2008-12-25
> **kevdog said:**
> why wouldn't you just compile and install from source?  I mean seriously is everyone just that lazy?  It takes less than 10 minutes to compile!

Many people just doesn't know how to do it.

---

### Post by Vadi on 2008-12-25
> **kevdog said:**
> why wouldn't you just compile and install from source?  I mean seriously is everyone just that lazy?  It takes less than 10 minutes to compile!

It also doesn't install any menu icons, it also requires you to keep sources about, it also doesn't have a decent way of uninstalling. Unless you use checkinstall, which is even more work.

So in short no point if you're on Ubuntu already. If gentoo, slackware, understandable...

---

### Post by Polygon on 2008-12-25
also, look at the compile options for the getdeb/ubuntu versions of pidgin:

> 
Debugging Information
  Arguments to ./configure:   '--build=i486-linux-gnu' '--prefix=/usr' '--includedir=${prefix}/include' '--mandir=${prefix}/share/man' '--infodir=${prefix}/share/info' '--sysconfdir=/etc' '--localstatedir=/var' '--libexecdir=${prefix}/lib/pidgin' '--disable-maintainer-mode' '--disable-dependency-tracking' '--enable-gevolution' '--enable-cap' '--with-system-ssl-certs=/etc/ssl/certs' '--enable-perl' '--with-zephyr=/usr' '--enable-dbus' '--enable-gnutls=no' '--enable-nss=yes' '--enable-cyrus-sasl' 'build_alias=i486-linux-gnu' 'CC=cc' 'CFLAGS=-fstack-protector' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS='
  Print debugging messages: No
  Plugins: Enabled
  SSL: SSL support is present.

  Library Support
    Cyrus SASL: Enabled
    D-Bus: Enabled
    Evolution Addressbook: Enabled
    Gadu-Gadu library (libgadu): Enabled
    GtkSpell: Enabled
    GnuTLS: Disabled
    GStreamer: Enabled
    Mono: Disabled
    NetworkManager: Enabled
    Network Security Services (NSS): Enabled
    Perl: Enabled
    Startup Notification: Enabled
    Tcl: Disabled
    Tk: Disabled
    X Session Management: Enabled
    XScreenSaver: Enabled
    Zephyr library (libzephyr): External
    Zephyr uses Kerberos: No


i dont even know what half of these things are, and im always afraid that something is going to go wrong / not work correctly (like spelling support) if i dont have the right compile options. And even if i copy/paste the arguments to 'configure', it still errors out.

so yeah, ill just use getdeb =)

---

### Post by kevdog on 2008-12-25
> **Vadi said:**
> It also doesn't install any menu icons 

Ok, so what?  Add them yourself

> it also requires you to keep sources about 

Hmm, an extra directory with bits of data inside?  Who cares?  And after you compile and install the program you could throw away the sources if you want.  How is this in any way a hinderance?

> it also doesn't have a decent way of uninstalling. Unless you use checkinstall, which is even more work. 

Hmm, without checkinstall, uninstalling is as simple as

sudo make uninstall

With checkinstall, it would be

sudo aptitude purge pidin

> So in short no point if you're on Ubuntu already. If gentoo, slackware, understandable...

So from this statement am I to assume Ubuntu is in someway different than Slack or Gentoo?

Perhaps you could check out this guide and it may clear up any misconceptions:
[http://ubuntuforums.org/showthread.php?t=975783](http://ubuntuforums.org/showthread.php?t=975783)

---

### Post by Vadi on 2008-12-25
That's the point, if you're willing to do all that, why are you on Ubuntu anyway?

---

### Post by kevdog on 2008-12-25
I guess the whole crux of it for me is that if you really trust 3rd repository sources or not.  Not that I don't use 3rd party repositories (mediabuntu, wicd) however I try to limit these as best as I can.  Additionally, if you really enjoy pidgin, its likely you are going to use additional plugins with the program. In most cases you need to compile and install these manually.  So if going through all the trouble to compile the plugins, why not just compile everything?  I guess if compiling from source were really all that difficult, and documentation about how to undertake the process was vague and missing explanations, I wouldn't recommend the process.  However in this case, the process is straightforward and well documented.  Possibly we just have a difference of opinion on this one.

---

### Post by rudihawk on 2008-12-26
I have tried numerous times to compile various things from source, and I have never gotten it right. Despite everyone saying: "its easy!, all you have to do is ./configure, blah blah, and no matter how many guides I follow, or additional packages I install so that the thing will compile I can never get it right. Therefore getdeb is useful for people like me, that want to keep using Ubuntu but can't compile everything from source.

---

### Post by Kosimo on 2008-12-26
> **rudihawk said:**
> i have tried numerous times to compile various things from source, and i have never gotten it right. Despite everyone saying: "its easy!, all you have to do is ./configure, blah blah, and no matter how many guides i follow, or additional packages i install so that the thing will compile i can never get it right. Therefore getdeb is useful for people like me, that want to keep using ubuntu but can't compile everything from source.

+1

---

### Post by kevdog on 2008-12-26
For all those that can't compile pidgin, try this guide and then tell me if you were unsuccessful:
[http://ubuntuforums.org/showthread.php?t=975783](http://ubuntuforums.org/showthread.php?t=975783)

I wrote the guide and can attest to its accuracy.  The entire process may take 10 minutes to compile the base pidgin package unless you have an ancient processor.

---

### Post by agabus_volks on 2008-12-31
will 2.5.3 become available on ubuntu 8.10 through the update manager sometime soon?

---

### Post by tahina on 2008-12-31
> **agabus_volks said:**
> will 2.5.3 become available on ubuntu 8.10 through the update manager sometime soon?

To my understanding, if it will be available, it will be available in the *backports* repository which you can enable from the menu "Administration" > "Software Sources" and then checking the checkbox for "Unsupported updates (backports)" in the "Updates"-tab.

Backports means that new versions of applications will be there. In the normal repositories, only securityfixes and bugfixes will be. It is explained at [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

Of course, not everything will be updated in backports. Only the most important exciting applications, depending on how many people there are packaging new versions of applications to the version  (8.10 in this case) of ubuntu in question (as I understand it, unless I'm mistaken). Happy GNU year!

---

### Post by agabus_volks on 2008-12-31
so since the 2.5.3 release contains bugfixes, I assume that will mean it will be released as an update for 8.10?

---

### Post by Vadi on 2009-01-01
Well, a lot of software updates contains bugfixes. It also introduces new bugs.

Only time when a bugfix update is justified is when it affects a large majority in a very negative way, or is a security flaw fix.

---

### Post by Sef on 2009-01-02
> so since the 2.5.3 release contains bugfixes, I assume that will mean it will be released as an update for 8.10?


Once a release is stable in ubuntu no more software updates are done - only security patches.  Though it may end up in backports and it could be updated through there.

---

### Post by novafluxx on 2009-01-15
Is this true? There are not updates to software, so I'm stuck using the same versions for 6 months until the next release of Ubuntu??? Oh man, I didn't know that, I thought new versions would be added to add/remove programs for me to update and get new versions of programs.

I wish there were a central location I could read things like this instead of finding it burried in a thread about Pidgin 2.5.3 lol

---

### Post by Vadi on 2009-01-15
They're updated if needed (ie, security). Otherwise, why would you want an applicaion that has not been tested and can potentially crash?

---

### Post by Islington on 2009-01-15
> **novafluxx said:**
> Is this true? There are not updates to software, so I'm stuck using the same versions for 6 months until the next release of Ubuntu??? Oh man, I didn't know that, I thought new versions would be added to add/remove programs for me to update and get new versions of programs.

I wish there were a central location I could read things like this instead of finding it burried in a thread about Pidgin 2.5.3 lol

you can often times find a repository offered by the devs of a program to get the latest and greatest version. Failing that, there are always instructions on how to build it yourself. The version in the official repos is the stable one, that way only tested stuff is installed by default.

---

### Post by Vadi on 2009-01-15
Nevermind that Pidgin developers are actively refusing to provide .debs for Ubuntu, while providing installers for other platforms.

---

### Post by TheGorf on 2009-01-15
> **Vadi said:**
> They're updated if needed (ie, security). Otherwise, why would you want an applicaion that has not been tested and can potentially crash?

In contrast I think Pidgin represents a good example of when a package does need to be updated that isn't security related.  I use 8.04 LTS.  It includes Pidgin 2.5.2.  With the recent MSN changes and the release of 2.5.4, I am now left with a broken package that I have to manually attempt to upgrade.  That makes 8.04 LTS worthless to me.  Why would I stay with it if package updates aren't going to track broken packages as well as security updates?  

For perspective I thought that I say that this isnt just my personal system.  As and IT Administrator I support an environment of about 175 users, about half of which we deploy with Ubuntu 8.04 LTS.  From a business perspective of course this is good because we don't have to reimage machines every 6 months.  However this bug represents a little bit of a flaw in the TLS support system.  If the bug were to affect say the Jabber functionality we would be hosed.

---

### Post by Vadi on 2009-01-15
TheGorf, there is a process called SRU then that takes care exactly of this.

Ubuntu doesn't update software because it's lazy / wants to make it useless, but because of the stability reasons. That's why security, and important updates (like your case) are done. See [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates) on how to file one.

---

### Post by novafluxx on 2009-01-17
I apologize for my tone. I just was under the wrong impression I guess. I'm a Windows user, who hasn't used Linux since Red Hat 6 nearly 10 years ago, and I was by no means an expert, and forgot a lot of what I knew.

I'm used to just downloading a binary (.exe) and running it, and having the program installed/updated.

I understand things are different in the Linux world, I'm just beginning to realise HOW different!

---

