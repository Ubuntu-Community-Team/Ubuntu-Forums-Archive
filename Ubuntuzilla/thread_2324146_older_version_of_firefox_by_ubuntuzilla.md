---
title: "older version of firefox by ubuntuzilla"
date: 2016-05-11
forum: Ubuntuzilla
---

### Post by fbird3 on 2016-05-11
Hello, all.
Knowing that Ubuntuzilla is a repository and that, as such, tends to make available the latest version of what releases I wonder if it would be possible to get an older version of firefox by Ubuntuzilla [I am aiming, in particular, for ff 45, since ff 46 did not work for me at all].
That is it.
Thanking you in advance.

---

### Post by vasa1 on 2016-05-11
We don't recommend using older browsers because they could pose security risks. We'd rather help you fix any issues you have with Fx 46 if we can!

---

### Post by fbird3 on 2016-05-11
Hi, vasa1
I tried getting assistance, but so far none has been offered.
I am curious about getting ff 45 from Ubuntuzilla because that one worked [minus a lot of crashes which might be solvable by creating a fesh profile], whereas ff 46 simply refuses to even start [no only that, but impedes my current version to start as well, so I had to remove ff 46 to continue using ff at all...].
I could wait for the release of ff 47, but what if it backfires just like ff 46 did...?
I would take the help I can get, if any was forthcoming...

---

### Post by vasa1 on 2016-05-11
> **fbird3 said:**
> Hi, vasa1
I tried getting assistance, but so far none has been offered ...
I would take the help I can get, if any was forthcoming ...
Where did you ask for help? I can't find any previous threads by you :(

---

### Post by fbird3 on 2016-05-11
I did not request assistance here [directly], but from another Ubuntuzilla user.
Anyway, I do not intend to install ff 45 from Mozilla, but through Ubuntuzilla. I know the wise advice about not going back to older versions that worked fine [kind of...], but to try to resolve the current problems, if at all possible; but other than paste here the error message I received [again, it is related to Ubuntuzilla and not to Mozilla directly] I am at my wits end. So, here it goes nothing:

firefox -P                N.B.: I was using a common directory; not ~; and not /opt/firefox; should it work all the same...?

XPCOMGlueLoad error for file /opt/firefox/libmozgtk.so:
libgtk-3.so.0: cannot open shared object file: No such file or directory
Couldn't load XPCOM.

  also; clicking the icon of "mozilla build of firefox" does nothing [not launching firefox as always]; but the version 45 did launch this way...; it did impede the launching of old firefox too; I had to uninstall it to get back to firefox 20

That is all...; does anyone have any idea what could be wrong, since ff 45 from Ubuntuzilla worked flawlessly [starting, that is, although I never got around creating a fresh profile before ff 46 was made available by Ubuntuzilla]?

---

### Post by vasa1 on 2016-05-11
I discussed your issue with other staff members and it was mentioned that Firefox 45 is available as an ESR version.

See [https://www.mozilla.org/en-US/firefox/organizations/faq/](https://www.mozilla.org/en-US/firefox/organizations/faq/) for details. And see [http://ubuntuforums.org/showthread.php?t=2220353&p=13007916#post13007916](http://ubuntuforums.org/showthread.php?t=2220353&p=13007916#post13007916) for a recommendation by the Ubuntuzilla maintainer on getting Firefox ESR directly from Mozilla.

---

### Post by ajgreeny on 2016-05-11
To get the best help we can offer, you should re-install FF 46 from the current ubuntu repositories and then start it in terminal with command **firefox**.

With luck that will show you some errors to copy back here, that we may be able decipher in order to help you solve the problem.

---

### Post by fbird3 on 2016-05-11
I have downloaded the tar.bz2 of ff45 ESR, and I am trying to follow the recommendation by the Ubuntuzilla mantainer as per that post, but [having unpacked the file elsewhere], I am lost as to what to do next...:

1-I do not have a ~/bin in my home directory [should I create one?]; there is only ~/.local/bin which I created a long time ago and I only use it for my simple bash scripts
2-how do I launch this ESR version exactly [I found no README file]? At the moment, I do not wish to make it the default one, because I need to test it first; so, I presume it would be run from the cli, but what command should I use exactly?
3-all this questions go to show why I would prefer to use Ubuntuzilla ff 45 if possible: all I would have to do would be to select the entry on the applications menu and click it!

But I am grateful for the suggestions received and I will follow any further instructions.

---

### Post by fbird3 on 2016-05-11
Alas, I am outside the scope of the current Ubuntu repositories, because my version is Ubuntu 10.04 and my ff version is still 20! That is the main reason for me to stick with Ubuntuzilla, if possible, because that way I still can use the latest version of ff while using an old Ubuntu version.
If the error messages received I wrote before are no good, I suppose I will just have to follow other avenues to get it done.

---

### Post by Dennis N on 2016-05-11
Unless you upgrade Ubuntu, you will never run Firefox version 46 or later:

System requirements for FF 46:
> Firefox will not run at all without the following libraries or packages:
    [COLOR="#FF0000"]GTK+ 3.4 or higher[/COLOR]
    GLib 2.22 or higher
    Pango 1.14 or higher
    X.Org 1.0 or higher (1.7 or higher is recommended)
    libstdc++ 4.3 or higher


Ubuntu 10.04 has no gtk-3 libraries in it. It's all gtk-2. It will run FF 45.0.1, but that is the end of the line.

---

### Post by Bucky Ball on 2016-05-11
Seeing as 'The repository contains packages of the latest releases of Mozilla Firefox, Thunderbird, and Seamonkey', I very much doubt they would have anything BUT the newest versions in the Ubuntuzilla repo. [From here]("https://sourceforge.net/p/ubuntuzilla/wiki/Main_Page/#repository-contents-and-package-behavior").

---

### Post by nanotube on 2016-05-11
Howdy,

As others have already pointed out, it looks like ff45 is the end of the line for ubuntu 10, due to library version requirements.
On the plus side, according to this timeline:
[https://www.mozilla.org/en-US/firefox/organizations/faq/](https://www.mozilla.org/en-US/firefox/organizations/faq/)
firefox ESR will be maintained with security fixes on version 45 for roughly another year or so.
On the minus side... after this year, you'll have to either bite the bullet and upgrade your OS to a newer version, or take the risk of using a browser with known security vulnerabilities in it. (I would not recommend choosing the latter!)

In the meantime though, i took a look at the contents of the ESR tar.bz2 package. Here are some tips on how to get in running.
Extract it somewhere you want it to be - I make a ~/bin directory and stick all my bash scripts and other local binaries, but ~/.local/bin is just fine too! 
when you extract the archive there, it'll create a directory ~/.local/bin/firefox, and within there you'll find a 'firefox' binary.
To run it, just open a terminal, change to that directory with command 
```
cd ~/.local/bin/firefox
```
then run it with command 
```
./firefox -P
```
That will start firefox ESR and offer you the option to select or create a fresh profile. You should definitely create a fresh profile, since the one from firefox20 is probably incompatible. (the ./ is important, that tells the shell to look for the binary in the current directory. if you just run 'firefox' it will by default run the regular binary from /usr/bin, unless you change your default search path, but we can worry about that later :))

Once this is working and you are happy, then we can talk about changing your menu items to point to your custom ESR version instead of the ff20 you have from the repos. :)

Hope that helps!

---

### Post by fbird3 on 2016-05-13
Thank you, Dennis N.
Now I know what not to pursue.
I think I would be satisfied if I could get ff45 esr running properly, fully aware that one day I might have to decide about upgrading my system.


> **Dennis N said:**
> Unless you upgrade Ubuntu, you will never run Firefox version 46 or later:

System requirements for FF 46:


Ubuntu 10.04 has no gtk-3 libraries in it. It's all gtk-2. It will run FF 45.0.1, but that is the end of the line.

---

### Post by fbird3 on 2016-05-13
Hi, nanotube!
I followed your instructions and now I am running ff45 esr!
I am still 'feeling my way' around it, but it has not crashed nor frozen so far... [knock on wood!].
In terms of CPU and memory usage, ff45 esr is way better than ff20 [which is open at the moment with a different profile and 74 tabs open, but basically 'quiet'].
There a few error messages that I will try to paste below, before I close the shell that opened ff45 esr.
At the moment, I am still changing the preferences as to mimic my old and trusted ff20, and getting used to the new appearance.
Let me fiddle with it for a while longer and I will ask your instructions to have an entry for ff45 esr on the applications menu as well -- if it does require restarting my system, though, I will delay that for as long as I can, because I am over-supersticious when it comes to restarting and [God forbid!] switch it off and restart my system again.
These are the error messages so far [I will continue to test it and try to customize it for a while longer, but I think it is better to send the error messages now than to wait until a possible crash/freeze of ff45 esr]:

 --->./firefox -P
1463147876162   FirefoxAccounts ERROR   Error updating FxA account info: Error: A different user signed in (resource://gre/modules/FxAccounts.jsm:157:29) JS Stack trace: [EMAIL="AccountState.prototype.resolve@FxAccounts.jsm"]AccountState.prototype.resolve@FxAccounts.jsm[/EMAIL]:157:29 < getUserAccountData/<@FxAccounts.jsm:141:14 < [EMAIL="Handler.prototype.process@Promise-backend.js"]Handler.prototype.process@Promise-backend.js[/EMAIL]:933:23 < [EMAIL="this.PromiseWalker.walkerLoop@Promise-backend.js"]this.PromiseWalker.walkerLoop@Promise-backend.js[/EMAIL]:812:7 < this.PromiseWalker.scheduleWalkerLoop/<@Promise-backend.js:746:1
1463147876162   FirefoxAccounts ERROR   Error updating FxA account info: Error: A different user signed in (resource://gre/modules/FxAccounts.jsm:157:29) JS Stack trace: [EMAIL="AccountState.prototype.resolve@FxAccounts.jsm"]AccountState.prototype.resolve@FxAccounts.jsm[/EMAIL]:157:29 < getUserAccountData/<@FxAccounts.jsm:141:14 < [EMAIL="Handler.prototype.process@Promise-backend.js"]Handler.prototype.process@Promise-backend.js[/EMAIL]:933:23 < [EMAIL="this.PromiseWalker.walkerLoop@Promise-backend.js"]this.PromiseWalker.walkerLoop@Promise-backend.js[/EMAIL]:812:7 < this.PromiseWalker.scheduleWalkerLoop/<@Promise-backend.js:746:1
1463147876164   browserwindow.syncui    ERROR   updateUI failed: Error: A different user signed in (resource://gre/modules/FxAccounts.jsm:157:29) JS Stack trace: [EMAIL="AccountState.prototype.resolve@FxAccounts.jsm"]AccountState.prototype.resolve@FxAccounts.jsm[/EMAIL]:157:29 < getUserAccountData/<@FxAccounts.jsm:141:14 < [EMAIL="Handler.prototype.process@Promise-backend.js"]Handler.prototype.process@Promise-backend.js[/EMAIL]:933:23 < [EMAIL="this.PromiseWalker.walkerLoop@Promise-backend.js"]this.PromiseWalker.walkerLoop@Promise-backend.js[/EMAIL]:812:7 < this.PromiseWalker.scheduleWalkerLoop/<@Promise-backend.js:746:1
1463148147024   addons.update-checker   WARN    Update manifest for {972ce4c6-7e08-4474-a285-3208198ce6fd} did not contain an updates property
1463148148015   addons.xpi      ERROR   Failed to clean updated system add-ons directories.: Unix error 2 during operation DirectoryIterator.prototype.next on file /home/eu2/.mozilla/firefox/gwpu894d.FF45-ESR/features (No such file or directory) ((unknown module)) No traceback available
1463148148851   addons.xpi      ERROR   Attempted to load bootstrap scope from missing directory /home/eu2/.mozilla/firefox/gwpu894d.FF45-ESR/extensions/firefox-hotfix@mozilla.org.xpi
1463148148851   addons.xpi      WARN    Add-on [EMAIL="firefox-hotfix@mozilla.org"]firefox-hotfix@mozilla.org[/EMAIL] is missing bootstrap method startup

(firefox:25935): Gtk-CRITICAL **: gtk_clipboard_set_with_data: assertion `targets != NULL' failed

(firefox:25935): Gtk-CRITICAL **: gtk_clipboard_set_with_data: assertion `targets != NULL' failed

I'll be back!

---

### Post by vasa1 on 2016-05-13
Don't forget to look at [Classic Theme Restorer]("https://addons.mozilla.org/en-US/firefox/addon/classicthemerestorer/").

---

