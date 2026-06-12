---
title: "Mono ditched in Ubuntu 12.04"
date: 2011-11-05
forum: The Cafe
---

### Post by Dragonbite on 2011-11-05
Banshee will be replaced by Rythmbox (again), and Tomboy will be removed. Since those were the only applications in the default installation that uses Mono, this mean the Mono framework will likewise be dropped.

> [[COLOR="Blue"]_Banshee, Tomboy And Mono Dropped from Ubuntu 12.04 CD_[/COLOR]]("http://www.omgubuntu.co.uk/2011/11/banshee-tomboy-and-mono-dropped-from-ubuntu-12-04-cd/")
The news was confirmed during the wrap-up session of the Ubuntu Developer Summit.

But Banshee is not the only removal: note-taking application Tomboy is also to be removed from the default application set on the CD.

Both applications will remain easily installable from the Ubuntu Software Centre for those who prefer to use them.

Tomboy and Banshee both relied on the ‘mono’ framework. As this is no longer needed “out of the box”, it too will be removed form the default CD.

Of course it is all available from the repositories.

---

### Post by sffvba[e0rt on 2011-11-05
Interesting development...


404

---

### Post by thenixedreport on 2011-11-05
As much as I don't mind Banshee and Tomboy, Mono is a pretty hefty dependency.  While it may not be that big of a deal on a hard drive these days, it's another story altogether when we're talking about a 700 MB CD.  With that much more space freed up, more options for the live CD would be opened up.  They could put GIMP back in.  They could add OpenShot or maybe the rest of LibreOffice.

---

### Post by MadCow108 on 2011-11-05
> **thenixedreport said:**
> As much as I don't mind Banshee and Tomboy, Mono is a pretty hefty dependency.  While it may not be that big of a deal on a hard drive these days, it's another story altogether when we're talking about a 700 MB CD.  With that much more space freed up, more options for the live CD would be opened up.  They could put GIMP back in.  They could add OpenShot or maybe the rest of LibreOffice.

yeay its really "hefty", its pretty much the same as python:
```
apt-get install mono-runtime
The following NEW packages will be installed:
  libmono-corlib4.0-cil libmono-security4.0-cil libmono-system-configuration4.0-cil
  libmono-system-security4.0-cil libmono-system-xml4.0-cil libmono-system4.0-cil mono-4.0-gac
  mono-gac mono-runtime
Need to get 3957 kB of archives.
After this operation, 11.5 MB of additional disk space will be used.
```
maybe 10mb for all extras you need for banshee + tomboy + gbrainy

I don't really get this descision, how has rhythmbox improved since it was removed?
its still as unmaintained as ever to my knowledge.

---

### Post by cgroza on 2011-11-05
> **thenixedreport said:**
> As much as I don't mind Banshee and Tomboy, Mono is a pretty hefty dependency.  While it may not be that big of a deal on a hard drive these days, it's another story altogether when we're talking about a 700 MB CD.  With that much more space freed up, more options for the live CD would be opened up.  They could put GIMP back in.  They could add OpenShot or maybe the rest of LibreOffice.
They increased the ISO size by 50 MB:
[http://www.omgubuntu.co.uk/2011/11/ubuntu-12-04-disc-size-to-be-750mb/](http://www.omgubuntu.co.uk/2011/11/ubuntu-12-04-disc-size-to-be-750mb/)

---

### Post by CharlesA on 2011-11-05
> **cgroza said:**
> They increased the ISO size by 50 MB:
[http://www.omgubuntu.co.uk/2011/11/ubuntu-12-04-disc-size-to-be-750mb/](http://www.omgubuntu.co.uk/2011/11/ubuntu-12-04-disc-size-to-be-750mb/)
I thought an 80 minute cd only held 700mb?

[s]There goes a waste of a dvd[/s] Guess I'll be putting it on a usb drive instead.

---

### Post by IWantFroyo on 2011-11-05
> **cgroza said:**
> They increased the ISO size by 50 MB:
[http://www.omgubuntu.co.uk/2011/11/ubuntu-12-04-disc-size-to-be-750mb/](http://www.omgubuntu.co.uk/2011/11/ubuntu-12-04-disc-size-to-be-750mb/)

Ouch...

See ya, blank DVDs.

---

### Post by CharlesA on 2011-11-05
> **IWantFroyo said:**
> Ouch...

See ya, blank DVDs.
Yep. I don't use cds or dvds all that much anymore, but I use an Ubuntu cd at work for data recovery and whatnot and some of the machines don't have dvd drives.

Guess I will be looking into a leaner distro for that, or just stick with 10.04. :p

---

### Post by IWantFroyo on 2011-11-05
> **CharlesA said:**
> Yep. I don't use cds or dvds all that much anymore, but I use an Ubuntu cd at work for data recovery and whatnot and some of the machines don't have dvd drives.

Guess I will be looking into a leaner distro for that, or just stick with 10.04. :p

I tend to use DVDs because I like testing non-Ubuntu distros. It's much easier to burn an ISO file than wait for something like UNetBootin to be updated (is it even in development anymore?).

Same here. My machines run Ubuntu Lucid or Debian Squeeze. I'm not sure if I'll end up updating them.

---

### Post by CharlesA on 2011-11-05
> **IWantFroyo said:**
> 
Same here. My machines run Ubuntu Lucid or Debian Squeeze. I'm not sure if I'll end up updating them.

Same here, my main server is running Lucid and I've got a couple desktop installs of Lucid bouncing around.

I wonder if the server cd will be smaller then the desktop cd - it should be but I suppose time will tell.

---

### Post by thenixedreport on 2011-11-05
Why couldn't they just work on improving the compression used for the live environment instead?  While CD-R's above 700 MB work, from what I gathered, they require overburn and are not guaranteed to work.

---

### Post by thenixedreport on 2011-11-05
> **MadCow108 said:**
> yeay its really "hefty", its pretty much the same as python:
```
apt-get install mono-runtime
The following NEW packages will be installed:
  libmono-corlib4.0-cil libmono-security4.0-cil libmono-system-configuration4.0-cil
  libmono-system-security4.0-cil libmono-system-xml4.0-cil libmono-system4.0-cil mono-4.0-gac
  mono-gac mono-runtime
Need to get 3957 kB of archives.
After this operation, 11.5 MB of additional disk space will be used.
```
maybe 10mb for all extras you need for banshee + tomboy + gbrainy

I don't really get this descision, how has rhythmbox improved since it was removed?
its still as unmaintained as ever to my knowledge.

From what this link is saying, it actually is.

[http://projects.gnome.org/rhythmbox/rhythmbox-0.13.3.news](http://projects.gnome.org/rhythmbox/rhythmbox-0.13.3.news)

---

### Post by stinkeye on 2011-11-05
The news certainly excited Roy Schestowitz.
He's already claiming victory.
> This marks a victory of sorts to a push we’ve put a lot of effort into, along with Boycott Novell. A lot of personal compromise was involved as I was on the receiving end of persistent bullying and smears. Thanks to all those who help share information about the problems with Mono. GNU/Linux is a lot safer (and better) now.

---

### Post by thenixedreport on 2011-11-05
Unfortunately, there were people calling that guy names which didn't help their position any.

---

### Post by philinux on 2011-11-05
> **CharlesA said:**
> I thought an 80 minute cd only held 700mb?

[s]There goes a waste of a dvd[/s] Guess I'll be putting it on a usb drive instead.

DVD rw ;)

UDS shortlist for precise.

[http://www.webupd8.org/2011/11/expected-changes-in-ubuntu-1204-precise.html](http://www.webupd8.org/2011/11/expected-changes-in-ubuntu-1204-precise.html)

I've posted this in Ubuntu+1 forum sticky.

---

### Post by CharlesA on 2011-11-05
> **philinux said:**
> DVD rw ;)
I did not think of that! Good idea.

---

### Post by IWantFroyo on 2011-11-05
> **CharlesA said:**
> I did not think of that! Good idea.

My problem with these is I keep losing them... They do the job, however.

---

### Post by CharlesA on 2011-11-05
> **IWantFroyo said:**
> My problem with these is I keep losing them... They do the job, however.
That's true. I probably have a dozen or so Ubuntu cds since I put them down somewhere and then they are not there when I need them.

*headdesk*

---

### Post by BeRoot ReBoot on 2011-11-05
> **IWantFroyo said:**
> It's much easier to burn an ISO file than wait for something like UNetBootin to be updated (is it even in development anymore?).

Tip: $dd if=ubantolunix.iso of=/dev/usbdrive works now.

---

### Post by gsmanners on 2011-11-05
Maybe we could format the DVDs with partitions so that you have the iso at the front of the disc and some other stuff using the rest of the space...

You'd still have about 3700MiB to fill on a single-layer, so maybe just a bunch of deb files you could copy in the /var/cache/apt/archive after you install. Or music/videos/whatever.

---

### Post by wolfen69 on 2011-11-05
> **stinkeye said:**
> The news certainly excited Roy Schestowitz.
He's already claiming victory.
> This marks a victory of sorts to a push we’ve put a lot of effort into, along with Boycott Novell. A lot of personal compromise was involved as I was on the receiving end of persistent bullying and smears. Thanks to all those who help share information about the problems with Mono. GNU/Linux is a lot safer (and better) now. 

I'm sure the neckbeards are happy.
[IMG]http://images.icanhascheezburger.com/completestore/2008/10/2/128674887138143892.jpg[/IMG]

---

### Post by gsmanners on 2011-11-05
Another way to not waste a DVD would be [multiCD]("http://www.webupd8.org/2010/02/multicd-builds-multi-boot-cd-dvd-with.html").

---

### Post by Ric_NYC on 2011-11-05
Thank you!

---

### Post by koenn on 2011-11-05
> **CharlesA said:**
> That's true. I probably have a dozen or so Ubuntu cds since I put them down somewhere and then they are not there when I need them.

*headdesk*
I turned to the mini-isos. Faster to download, faster to burn + you install an up to date system automatically. It's a bit of a waste of a CD but at least it's not such a waste of time. 

that, and a proxy to cache the stuff you need to download during the install, just to have it there in case you need to install more than once, for whatever reason (a second computer, a virtual machine, an error or a mistake during the install, ...)

---

### Post by travissparks1307 on 2011-11-05
I am so happy to say that my faith in Ubuntu has been restored. :biggrin: First Canonical teams up with RedHat to fight M$ secure boot, then they get rid of mono. It proves to me that they're serious about competing with Microsoft and not just Apple. I am really looking forward to Ubuntu 12.04! Bravo Ubuntu. Bravo.=D>

---

### Post by koleoptero on 2011-11-05
Great decision as far as I am concerned. The first thing I would do on a fresh ubuntu install is sudo apt-get purge libmono-corlib-<tab>.

> **MadCow108 said:**
> yeay its really "hefty", its pretty much the same as python:
```
apt-get install mono-runtime
The following NEW packages will be installed:
  libmono-corlib4.0-cil libmono-security4.0-cil libmono-system-configuration4.0-cil
  libmono-system-security4.0-cil libmono-system-xml4.0-cil libmono-system4.0-cil mono-4.0-gac
  mono-gac mono-runtime
Need to get 3957 kB of archives.
After this operation, 11.5 MB of additional disk space will be used.
```
maybe 10mb for all extras you need for banshee + tomboy + gbrainy

I don't really get this descision, how has rhythmbox improved since it was removed?
its still as unmaintained as ever to my knowledge.
If you remove all the mono stuff from a fresh install and then install rhythmbox+gnote you'll see that they need much less things to download and take less space.

Also rhythmbox is alive and hale, it just doesn't change much on the outside.
> **IWantFroyo said:**
> I tend to use DVDs because I like testing non-Ubuntu distros. It's much easier to burn an ISO file than wait for something like UNetBootin to be updated (is it even in development anymore?).

Same here. My machines run Ubuntu Lucid or Debian Squeeze. I'm not sure if I'll end up updating them.

unetbootin is alive and hale too.

---

### Post by Legendary_Bibo on 2011-11-05
> **travissparks1307 said:**
> I am so happy to say that my faith in Ubuntu has been restored. :biggrin: First Canonical teams up with RedHat to fight M$ secure boot, then they get rid of mono. It proves to me that they're serious about competing with Microsoft and not just Apple. I am really looking forward to Ubuntu 12.04! Bravo Ubuntu. Bravo.=D>

Using M$ in place of MS for Microsoft was so clever! OMG I can't believe no one else has thought of that clever label to imply that Microsoft was a corporation that inherently made money *gasp*.

Oh, and they've definitely got something up their sleeve with that Mono project. I mean the whole project is only released under GPLv2, and Microsoft explicitly placing ECMA 334 and ECMA 335 standards under the Microsoft Community Promise, and even going as far as contributing code to the Mono project. Oh wait...

---

### Post by inobe on 2011-11-05
wow

---

### Post by gsmanners on 2011-11-05
> **Legendary_Bibo said:**
> Oh, and they've definitely got something up their sleeve with that Mono project. I mean the whole project is only released under GPLv2, and Microsoft explicitly placing ECMA 334 and ECMA 335 standards under the Microsoft Community Promise, and even going as far as contributing code to the Mono project. Oh wait...

I know right? And Microsoft would NEVER sue anyone over patents. Why that would just be so unfair! :P

---

### Post by Legendary_Bibo on 2011-11-05
> **gsmanners said:**
> I know right? And Microsoft would NEVER sue anyone over patents. Why that would just be so unfair! :P

[quote=Microsoft Open Specification Promise]Microsoft ***_[SIZE="3"]irrevocably[/SIZE]_*** promises not to assert any Microsoft Necessary Claims against you for making, using, selling, offering for sale, importing or distributing any implementation to the extent it conforms to a Covered Specification (“Covered Implementation”), subject to the following. This is a personal promise directly from Microsoft to you, and you acknowledge as a condition of benefiting from it that no Microsoft rights are received from suppliers, distributors, or otherwise in connection with this promise.[/quote]

[Source](http://www.microsoft.com/openspecifications/en/us/programs/osp/default.aspx)

> The base technologies submitted to the ECMA, and therefore also the Unix/GNOME-specific parts, are not problematic due to Microsoft's explicitly placing both ECMA 334 and ECMA 335 standards under the Microsoft Community Promise. The concerns primarily relate to technologies developed by Microsoft on top of the .NET Framework, such as ASP.NET, ADO.NET and Windows Forms (see non-standardized namespaces), i.e. parts composing Mono’s Windows compatibility stack. These technologies are today not fully implemented in Mono and not required for developing Mono-applications, they are simply there for developers and users who need full compatibility with the Windows system.

Yeah we live in a pretty black and white world.

---

### Post by inobe on 2011-11-05
> **Legendary_Bibo said:**
> [Source](http://www.microsoft.com/openspecifications/en/us/programs/osp/default.aspx)



Yeah we live in a pretty black and white world.

>  
** they are simply there for developers and users who need full compatibility with the Windows system.**

that in itself must be a typo:P

---

### Post by beew on 2011-11-05
What was the reason that they switched from Rhythmbox to Banshee again? I think Rhythmbox was no longer developed, how has that changed? Well not that I really care one way or the other.

---

### Post by Frogs Hair on 2011-11-05
I switched back to Rythmbox after an half hour with Banshee on 11.04 and didn't even bother to open it 11.10 . Some like it but it just isn't for me . I have never used Tomboy .

---

### Post by inobe on 2011-11-05
> **llua+ said:**
> Don't argue with an <snip> people watching may not be able to tell the difference.

please consider the ubuntu code of conduct before posting, good day :)

[http://www.ubuntu.com/project/about-ubuntu/conduct](http://www.ubuntu.com/project/about-ubuntu/conduct)

---

### Post by KiwiNZ on 2011-11-06
"Any topic or discussion that causes problems or  drama will be closed. This area is intended for fun and community  building, not arguments. Please take those elsewhere. Thanks!"


Closed in 10,9,8,7....to heck with patience over. Closed

---

