---
title: "LibreOffice 4.0 released."
date: 2013-02-07
forum: The Cafe
---

### Post by kagashe on 2013-02-07
Hi,

[LibtrOffice 4.0 released]("http://blog.documentfoundation.org/2013/02/07/the-document-foundation-announces-libreoffice-4-0/").

How can I intsall it side by with LibreOffice 3.5.4.2 keeping both versions?
Answered in [this post]("http://ubuntuforums.org/showpost.php?p=12500097&postcount=17").

We can discuss new features in this thread even if you don't answer my question.

Kamalakar

---

### Post by ACubed10 on 2013-02-08
It says in the readme that you must remove a previous version.  Not sure you can install it with 3.  I just did the install and it was super simple.  search libreoffice-core in the software center to remove LibreOffice 3.  Then follow the instructions in the readme for Ubuntu/Debian.  Worked perfect.  Writer opens really fast on my computer...looks nice.  Not really sure what all the improvements are but it definitely opened faster! :p


BTW the torrent download was much faster.  Was saying in firefox that the download would take 35 mins.  I did the torrent download, downloading at 3.5MB/sec down and took 30 seconds or so :)

---

### Post by ubuntu27 on 2013-02-08
I also downloaded the LibreOffice with qBittorrent and it finished the download in 2 minutes! :D I know, longer than you seconds, but that is still amazing.

What's new in LibreOffice 4.0:

[https://www.libreoffice.org/download/4-0-new-features-and-fixes](https://www.libreoffice.org/download/4-0-new-features-and-fixes)

[http://www.omgubuntu.co.uk/2013/02/libreoffice-hits-4-0-adds-unity-integration-persona-theming](http://www.omgubuntu.co.uk/2013/02/libreoffice-hits-4-0-adds-unity-integration-persona-theming)

[http://www.webupd8.org/2013/02/libreoffice-40-available-for-download.html](http://www.webupd8.org/2013/02/libreoffice-40-available-for-download.html)

---

### Post by monkeybrain2012 on 2013-02-08
I haven't tried it but I think you can install both versions. I have installed manually from LBO and it is installed in /opt/ and synaptic shows that Libreoffice is not installed (the names are a bit different from the repo version) So it should be possible for me to install the repo version as well if I so wish.

---

### Post by MadmanRB on 2013-02-08
I think I will wait for a ppa.

---

### Post by zombifier25 on 2013-02-08
> **monkeybrain2012 said:**
> I haven't tried it but I think you can install both versions. I have installed manually from LBO and it is installed in /opt/ and synaptic shows that Libreoffice is not installed (the names are a bit different from the repo version) So it should be possible for me to install the repo version as well if I so wish.

You still shouldn't do that though. The configs may conflict with each other, and cause some errors.

(I haven't seen any LibreOffice errors not cured by deleting the ~/.config/libreoffice folder)

---

### Post by kagashe on 2013-02-08
I removed Libreoffice 3.5
sudo apt-get purge libreoffice*

and installed Libreoffice 4.0 from debs:
sudo dpkg -i *.deb
cd desktop-integration
sudo dpkg -i *.deb

Libreoffice can be started from Dash or from the command:
libreoffice4.0

The icons can be locked to launcher for next start.

Kamalakar

---

### Post by ACubed10 on 2013-02-08
> **kagashe said:**
> I removed Libreoffice 3.5
sudo apt-get purge libreoffice*

and installed Libreoffice 4.0 from debs:
sudo dpkg -i *.deb
cd desktop-integration
sudo dpkg -i *.deb

Kamalakar
perfect!  BTW when I tried to install the .deb's it gave me a message in terminal that said "package conflict"  Just FYI.  You do have to remove 3 to install 4

---

### Post by kurt18947 on 2013-02-08
I have a couple .docx files I've downloaded to test .docx import capability.  They're pretty heavily formatted with a bunch of graphics.    IMO LO4 does a better job of rendering them than LO 3.6 does.  Not by a lot, but better.  Saving to  docx?  I haven't tried that yet.

---

### Post by kagashe on 2013-02-08
The Unity Desktop integration is not working for Menu and it is not working in Ubuntu 13.04 either. There is a discussion on [this thread]("http://ubuntuforums.org/showthread.php?t=2113397").

Kamalakar

---

### Post by skellat on 2013-02-08
I'll be waiting to see if there is going to be a PPA and what it will take to get it compiled on armhf since the PPAs do not automagically produce ARM packages.

---

### Post by kagashe on 2013-02-08
> **skellat said:**
> I'll be waiting to see if there is going to be a PPA and what it will take to get it compiled on armhf since the PPAs do not automagically produce ARM packages.

[PPA is there]("https://launchpad.net/~libreoffice/+archive/libreoffice-4-0") but it has no files.

Kamalakar

---

### Post by skellat on 2013-02-08
> **kagashe said:**
> [PPA is there]("https://launchpad.net/~libreoffice/+archive/libreoffice-4-0") but it has no files.

Kamalakar

Hmm.  Nothing is even submitted for building yet.  This could get interesting.

PPAs still need special ARM blessing to punch out ARM packages.

---

### Post by monkeybrain2012 on 2013-02-08
> **kagashe said:**
> The Unity Desktop integration is not working for Menu and it is not working in Ubuntu 13.04 either. There is a discussion on [this thread]("http://ubuntuforums.org/showthread.php?t=2113397").

Kamalakar

Do you mean the global menu? I don't find anything unusual here but I  use Unity without the global menu.

---

### Post by 3rdalbum on 2013-02-08
What part of Libreoffice do the MS Publisher and Visio files open in? I guess Visio files open in LO Draw.

Is there editing and exporting to Publisher format, or just read-only opening or conversion to LO Writer format?

---

### Post by divergex on 2013-02-08
> **3rdalbum said:**
> What part of Libreoffice do the MS Publisher and Visio files open in? I guess Visio files open in LO Draw.

Is there editing and exporting to Publisher format, or just read-only opening or conversion to LO Writer format?

I tried a Publisher doc and it opened in Writer. I was surprised at how well the fidelity was maintained. I only had to fix an automatic page number that I placed on a master page in the original document. I have not tried to save in Publisher format because I no longer have Publisher to test it.

---

### Post by gefalu2008 on 2013-02-09
I found that these instructions make it possible to install parallel versions of LibreOffice - i.e., there is no need to remove the old version:

[https://wiki.documentfoundation.org/Installing_in_parallel](https://wiki.documentfoundation.org/Installing_in_parallel)

---

### Post by gefalu2008 on 2013-02-09
LibreOffice 4.0 has a new regular expressions engine based on ICU. Does anyone know where to find a user-friendly user guide for the new engine with examples?

Available 'metacharacters' are listed at
[http://userguide.icu-project.org/strings/regexp](http://userguide.icu-project.org/strings/regexp)
but there are no examples.

The old list of regular expressions at 
[https://help.libreoffice.org/Common/List_of_Regular_Expressions](https://help.libreoffice.org/Common/List_of_Regular_Expressions)
seems to be outdated.

Thank you!

---

### Post by kagashe on 2013-02-09
> **gefalu2008 said:**
> I found that these instructions make it possible to install parallel versions of LibreOffice - i.e., there is no need to remove the old version:

[https://wiki.documentfoundation.org/Installing_in_parallel](https://wiki.documentfoundation.org/Installing_in_parallel)

Yes. I think it answers my question in the [first post]("http://ubuntuforums.org/showpost.php?p=12498172&postcount=1").

For trying this I need to remove Libreoffice 4.0, install default Libreoffice 3.5 and reinstall Libreoffice 4.0 as described in /opt.

I hope someone should try it instead.

Thank you.

Kamalakar

---

### Post by Asatru9 on 2013-02-09
I"ll install Libre Office fairly soon, I'll get things the way I want them on the PC first than put it on.

---

### Post by neu5eeCh on 2013-02-10
Just installed LibreOffice 4 on my Xubuntu 12.04 System.  It doesn't work. I get the splash screen and then -- nothing. Running it in Terminal I get the following errors:

> 
(soffice:14860): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(soffice:14860): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-40Nvt0/pkcs11: No such file or directory

Any ideas?

---

### Post by forrestcupp on 2013-02-10
> **kurt18947 said:**
> I have a couple .docx files I've downloaded to test .docx import capability.  They're pretty heavily formatted with a bunch of graphics.    IMO LO4 does a better job of rendering them than LO 3.6 does.  Not by a lot, but better.  Saving to  docx?  I haven't tried that yet.This is what I'm interested in. I never really had a problem with opening docx files, but saving to docx totally sucks, especially if you're using bullet points.

> **divergex said:**
> I tried a Publisher doc and it opened in Writer. I was surprised at how well the fidelity was maintained. I only had to fix an automatic page number that I placed on a master page in the original document. I have not tried to save in Publisher format because I no longer have Publisher to test it.Publisher uses pub files, not doc. Can Writer actually open pub files now? There has never been a way to work with pub files other than Publisher.

---

### Post by neu5eeCh on 2013-02-10
Meh. Not ready for prime time. Removed and reinstalling 3.x. Guess I'll have to wait for the PPA.

---

### Post by mike acker on 2013-02-10
> **forrestcupp said:**
> This is what I'm interested in. I never really had a problem with opening docx files, but saving to docx totally sucks, especially if you're using bullet points.

{snip}

my testing with docx and xlsx files transmitted to Win7 MSFT Ofc 2010 have looked pretty good so far . 

I would note if the Windows system is using the start office pack you still have a NO GO .

But this appears to be a HUGE improvement

I'm even reading some Official Rumours claiming msft will offer Office for Linux ... It is amusing to ponder the implications of this... if there is anything to it ...

I cannot imagine any reason for retaining LO Vers 3.5

---

### Post by neu5eeCh on 2013-02-10
> **mike acker said:**
> I'm even reading some Official Rumours claiming msft will offer Office for Linux ... It is amusing to ponder the implications of this... if there is anything to it ...

I can't fathom there's any truth to the rumor.  If it's true, however, I'm guessing it's because MS sees Open Office (& possibly Libre Office) as a serious threat. After all, if MS loses the business community, then they're in serious trouble. Windows, as far as businesses are concerned, is little more than a platform for MS Office. If governments (Munich) are willing to switch to Open Office, then this could be the beginning of the end of Windows.

I wonder if, somewhere in the bowels Redmond, the argument is being made that they need to decapitate Open/Libre Office just like Netscape. Offer MS Office on Linux and they can kill Open Office. I can't imagine Ballmer going for that (besides the fact that it wouldn't work). Such a strategy would be tantamount to giving up on Windows.

As it is, Ballmer is probably having sleepless nights.

---

### Post by kagashe on 2013-02-11
> **VTPoet said:**
> Just installed LibreOffice 4 on my Xubuntu 12.04 System.  It doesn't work. I get the splash screen and then -- nothing. Running it in Terminal I get the following errors:
Any ideas?

> (soffice:14860): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

(soffice:14860): Gtk-WARNING **: Unable to locate theme engine in module_path: "equinox",

The solution is on [this page]("http://superuser.com/questions/337639/how-to-fix-unable-to-locate-theme-engine-in-module-path-murrine"):
sudo apt-get install --reinstall gtk2-engines

> WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-40Nvt0/pkcs11: No such file or directory

This is related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/932177") on XFCE.

Kamalakar

---

### Post by neu5eeCh on 2013-02-11
> **kagashe said:**
> The solution is on [this page]("http://superuser.com/questions/337639/how-to-fix-unable-to-locate-theme-engine-in-module-path-murrine"):
sudo apt-get install --reinstall gtk2-engines

This is related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/932177") on XFCE.

Kamalakar

Thanks kagashe. These seem to be such in-your--face bugs that it kind of makes me wonder how they were never noticed by the powers-that-be. (Does every last coder only develop Libre Office with Gnome Keyring enabled?) I've subscribed to the bug. Hopefully they'll sort out the Gnome Keyring business.  I detest the feature. Ought to have an option to disable it in Libre, in my opinion, but what do *I* know...

---

### Post by kagashe on 2013-03-05
LibreOffice 4.0 PPA is now available.
sudo add-apt-repository ppa:libreoffice/libreoffice-4-0
sudo add-apt-repository ppa:libreoffice/libreoffice-4-0

and you can upgrade to LibreOffice 4.0

Kamalakar

---

### Post by ubuntu27 on 2013-03-07
By the way guys a new Guide for LibreOffice 4.0 has been relieasd for both [print]("http://www.lulu.com/shop/libreoffice-documentation-team/libreoffice-40-getting-started-guide/paperback/product-20725693.html;jsessionid=E85E6FB62FE6916B628CF0CFD23D02AC") (around $20) format and [PDF]("http://wiki.documentfoundation.org/images/1/13/GS40-GettingStartedLO.pdf") (free)
[URL="http://www.iloveubuntu.net/390-pages-long-libreoffice-40-getting-started-guide-freely-available-download"]
See here[/URL]

Its great to see the new features and some hidden (not so obvious) features explained. ^_^

---

### Post by Apurvam on 2013-03-07
Is the Libre Office available un Ubuntu Software Center version 4? If not how do I install Libre Office 4?

---

### Post by aykoola on 2013-03-07
Hi Apurvam!

If you perform these steps: [http://www.liberiangeek.net/2012/08/libreoffice-3-6-lands-in-its-official-ppa-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/08/libreoffice-3-6-lands-in-its-official-ppa-in-ubuntu-12-04-precise-pangolin/)  - you will have LO4 installed. 
It updated my libreoffice 3.6 install to 4 on my Xubuntu.

---

### Post by kagashe on 2013-03-07
> **Apurvam said:**
> Is the Libre Office available un Ubuntu Software Center version 4? If not how do I install Libre Office 4?

You need to add this ppa "ppa:libreoffice/libreoffice-4-0"

The procedure to add ppa through Software Center is available on [URL="http://www.omgubuntu.co.uk/how-to-add-a-ppa-to-software-sources-in-ubuntu"]this page on omgubuntu site.
[/URL]

Kamalakar

---

### Post by vanadium on 2013-03-08
The ppa:libreoffice/ppa now provides Version 4.0.1.2 (Build ID: 400m0(Build:2)). The ppa:libreoffice/libreoffice-4-0 is yet another ppa, but perhaps the version there is more bleeding edge and unstable? I am not sure which of these repo's is recommended for more general use, beyond testers.

---

### Post by Apurvam on 2013-03-08
I added PPA (post #32), but when I search Libre in Ubuntu Software Center (I'm using Xubuntu 12.10 btw) and try to install LibreOffice Calc I get following error:
**Requires installation of untrusted packages**
> This requires installing packages from unauthenticated sources.
**Details:** libclucene-contribs1 libclucene-core1 libcmis-0.3-3 libexttextcat-2.0-0 libexttextcat-data libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-help-en-gb libreoffice-help-zh-cn libreoffice-l10n-en-gb libreoffice-l10n-en-za libreoffice-l10n-zh-cn libreoffice-math libreoffice-style-galaxy libreoffice-writer uno-libs3 ure

It gives to 2 options: OK and Repair.

I tried "Repair" but it didn't help.

---

### Post by Pinoy Tux on 2013-03-16
> **vanadium said:**
> The ppa:libreoffice/ppa now provides Version 4.0.1.2 (Build ID: 400m0(Build:2)). The ppa:libreoffice/libreoffice-4-0 is yet another ppa, but perhaps the version there is more bleeding edge and unstable? I am not sure which of these repo's is recommended for more general use, beyond testers.

AFAIK,
ppa:libreoffice/ppa - always the latest version that is available
ppa:libreoffice/libreoffice-4-0 - only the 4.0.x series

So, if you subscribe to the 4.0 ppa only and 4.1, 4.2, ... 5.x, 6.x, et al. comes out, you are not going to get updates beyond the 4.0.x series.

Read the descriptions [here]("https://launchpad.net/~libreoffice/+archive/ppa") and [here]("https://launchpad.net/~libreoffice/+archive/libreoffice-4-0").

---

### Post by vanadium on 2013-03-16
If I read the descriptions well, then the best advise to provide to general users is to use the ppa:libreoffice/libreoffice-4-0. This will contain stable releases, although only for the 4.0 series. The  ppa:libreoffice/ppa indeed may even push alpha releases at some time. Knowing this, I'll change my repo to ppa:libreoffice/libreoffice-4-0.

---

### Post by Pinoy Tux on 2013-03-16
> **vanadium said:**
> The  ppa:libreoffice/ppa indeed may even push alpha releases at some time.
Well, you have to take into proper context what the alpha/beta builds are for:
> **For the current development release of Ubuntu** this ppa might even contain alpha and beta releases
So, if you are using a version of Ubuntu that is yet to be released (e.g., 13.04 as of this writing), then it's possible that what you will get from the main PPA may be alpha/beta builds as well.

Looking at their [Packaging PPA page]("https://launchpad.net/~libreoffice"), they also list a [Pre-Releases PPA]("https://launchpad.net/~libreoffice/+archive/libreoffice-prereleases") that:
> contains alpha and beta release (before the 3.X.0/4.X.0 release)

---

