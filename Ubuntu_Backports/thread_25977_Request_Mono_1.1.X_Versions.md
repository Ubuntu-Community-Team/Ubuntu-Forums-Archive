---
title: "Request: Mono 1.1.X Versions"
date: 2005-04-11
forum: Ubuntu Backports
---

### Post by MoB on 2005-04-11
It will be very nice if it can be done, for start writing porting .NET apps with Windows.Forms in Mono 1.1.6 :D

[http://www.mono-project.com/Downloads#Development_release](http://www.mono-project.com/Downloads#Development_release)

Greetings!  [-o<

---

### Post by jdong on 2005-04-11
Certainly doable, but unsure when I'll finish it -- the last mono backport for Warty took a considerable chunk out of an afternoon, so probably it'll be done this weekend.

---

### Post by jdong on 2005-04-14
[https://sourceforge.net/pm/task.php?func=detailtask&project_task_id=114399&group_id=125877&group_project_id=42440](https://sourceforge.net/pm/task.php?func=detailtask&project_task_id=114399&group_id=125877&group_project_id=42440)

I've added a task for your request. You may use the link to see the progress and expected finish date :)

---

### Post by MoB on 2005-04-14
Thanks in advance!  :)  \\:D/

---

### Post by JuanC on 2005-04-15
I went to [http://www.mono-project.com/Downloads](http://www.mono-project.com/Downloads) and download mono-1.1.6-installer.bin

Now , when i try to run mono i get this message :
```
/opt/mono-1.1.6/bin/mono.bin: relocation error: /opt/mono-1.1.6/bin/mono.bin: symbol __libc_stack_end, version GLIBC_2.1 not defined in file ld-linux.so.2 with link time reference
```
Any ubuntu package for Mono 1.1.6 ?

---

### Post by rjlawr on 2005-04-17
[QUOTE=jdong]Certainly doable, but unsure when I'll finish it -- the last mono backport for Warty took a considerable chunk out of an afternoon, so probably it'll be done this weekend.[/QUOTE]


I am looking forward to this as well.  Will it be for Hoary or Warty?

---

### Post by jdong on 2005-04-17
This'll be for Hoary. I don't dare to try it with Warty ;)

---

### Post by nehalem on 2005-04-18
This will be great.  I'm very anxious to see what kind of memory usage optimizations we can expect.  I've heard they're pretty significant and with blam using 150mb that is a good thing.  

I can only imagine the scope of this backport as I wonder how much of the current apps (tomboy, muine, blam, etc) will eventually have to be backported as well in order to work.  Then of course everyone will want Beagle...

Thanks for the hard work!

---

### Post by rjlawr on 2005-04-18
Oh, beyond mono, can you also backport related tools and libraries? Such as MonoDevelop 0.6 and gtk#2?

You know you are a geek when you drool over the prospect of new versions of development tools.


Now . . . where did I put my mop?

 :grin:

---

### Post by rjlawr on 2005-04-24
[QUOTE=jdong][https://sourceforge.net/pm/task.php?func=detailtask&project_task_id=114399&group_id=125877&group_project_id=42440](https://sourceforge.net/pm/task.php?func=detailtask&project_task_id=114399&group_id=125877&group_project_id=42440)

I've added a task for your request. You may use the link to see the progress and expected finish date :)[/QUOTE]
 According to the task on the sourceforge project page, the expected release date was 22 April 2005.  Can we have an update on its status?

Also this may help: [http://pkg-mono.alioth.debian.org/](http://pkg-mono.alioth.debian.org/)  is a project to create pkgs for Debian and could be used as a base for Ubuntu, but they do not install and work properly as-is.

I understand the project is run in by volunteers in their free time and I appreciate their efforts. 

Thanks again.

---

### Post by jdong on 2005-04-25
Sorry,

Backports are running behind schedule due to my massive load of stuff to do in my own life ;)


Currently, I'm getting the critically important packages backported, like Firefox 1.0.3 (which contains security fixes).

Then, I'll move on to FreeNX (because of its high demand).

After that would come Mono and WINE, then games.

---

### Post by RastaMahata on 2005-04-25
[QUOTE=jdong]Sorry,

Backports are running behind schedule due to my massive load of stuff to do in my own life ;)


Currently, I'm getting the critically important packages backported, like Firefox 1.0.3 (which contains security fixes).

Then, I'll move on to FreeNX (because of its high demand).

After that would come Mono and WINE, then games.[/QUOTE]
 aww... no acrobat or transcode or avidemux2 :(

oh well, thumbs up for the good work :D

---

### Post by jdong on 2005-04-25
No, I haven't rejected those yet; I'm just putting it off for later.


Though I will have to reject Acrobat Reader due to licensing issues (redistribution restriction) beyond my control.

---

### Post by RastaMahata on 2005-04-25
[QUOTE=jdong]No, I haven't rejected those yet; I'm just putting it off for later.


Though I will have to reject Acrobat Reader due to licensing issues (redistribution restriction) beyond my control.[/QUOTE]
 heh, no worries. I've learned to live with evince. (I wish it was translated though).

Keep up the good work. I'm about to do a clean hoary install, and only add the backports debs appart from the official ubuntu multiverse and universe ones, and see how it goes (I wont add marillat...)

That's it, I'm not hijacking this thread any longer. :(

---

### Post by rlcoach on 2005-04-26
Looking forward to this. I have just this weekend moved over to Ubuntu from Windows XP. The .net framework is the only thing that keeps me on Windows for long portions of time, if we can get the latest versions of Mono/MonoDevelop with Hoary that would be fantastic, and not just for development as Beagle looks good too and that has a dependency on latest MOno.

---

### Post by gamehack on 2005-04-28
Any progress on this? I've been waiting for this for quite some weeks now :(

Regards,
gamehack

---

### Post by jdong on 2005-04-30
1.1.6 is currently in Debian Experimental.

I'll grab it and place it in -staging tonight.

---

### Post by jdong on 2005-04-30
I'm uploading Mono packages now.

Due to my creative ways around the cli-common and mono-1.1.6 cross-circular dependency, this first package may not have proper dependencies and such.


After this upload, if it's deemed that deps are not correct, I'll upload a ~ubp2 revision.

---

### Post by panabar on 2005-05-01
[QUOTE=jdong]I'm uploading Mono packages now.

Due to my creative ways around the cli-common and mono-1.1.6 cross-circular dependency, this first package may not have proper dependencies and such.


After this upload, if it's deemed that deps are not correct, I'll upload a ~ubp2 revision.[/QUOTE]
 I just installed these packages.
Blam starts much faster than with the hoary mono but,
Muine Music Player does not work after upgrading to these new mono packages. 

:/

Thank You

---

### Post by rlcoach on 2005-05-01
[QUOTE=panabar]I just installed these packages.
Blam starts much faster than with the hoary mono but,
Muine Music Player does not work after upgrading to these new mono packages. 

:/

Thank You[/QUOTE]

Are the packages up? Where do I have to go to get em?

---

### Post by jdong on 2005-05-01
They're currrently in hoary-backports-staging/universe. Install the "mono" package, and the rest should be pulled along with it.

---

### Post by A-star on 2005-05-02
any possibility that you could add mono-mcs?

---

### Post by nehalem on 2005-05-02
Nice!

Before i install I must know one thing.  Does tomboy break?

---

### Post by rlcoach on 2005-05-02
[QUOTE=jdong]They're currrently in hoary-backports-staging/universe. Install the "mono" package, and the rest should be pulled along with it.[/QUOTE]

Thanks for that, it worked great.

Are there any plans to do MonoDevelop 0.6? As this sort of goes hand in hand with Mono.

---

### Post by jdong on 2005-05-02
There are no Debian packages for MonoDevelop 0.6 yet. I'll wait for Sid or Breezy to get them, because getting too far ahead of the development release spells living nightmare when upgrading to the next release :)

---

### Post by rlcoach on 2005-05-02
[QUOTE=jdong]There are no Debian packages for MonoDevelop 0.6 yet. I'll wait for Sid or Breezy to get them, because getting too far ahead of the development release spells living nightmare when upgrading to the next release :)[/QUOTE]

Was looking at doing it manually until I saw all the dependencies and thought as a Linux/Ubuntu noob, it might not be wise  :) .

---

### Post by darrenadams on 2005-05-02
[QUOTE=nehalem]Nice!

Before i install I must know one thing.  Does tomboy break?[/QUOTE]


Short Answer: Yes.

Longer Answer: Yes, but you can get the not-yet-officially-released 0.3.2 deb file from [http://www.beatniksoftware.com/tomboy/releases/tomboy-0.3.2/tomboy_0.3.2-1_i386.deb](http://www.beatniksoftware.com/tomboy/releases/tomboy-0.3.2/tomboy_0.3.2-1_i386.deb)  which, from what I've seen so far works without a problem.

---

### Post by nehalem on 2005-05-02
[QUOTE=darrenadams]Short Answer: Yes.

Longer Answer: Yes, but you can get the not-yet-officially-released 0.3.2 deb file from [http://www.beatniksoftware.com/tomboy/releases/tomboy-0.3.2/tomboy_0.3.2-1_i386.deb](http://www.beatniksoftware.com/tomboy/releases/tomboy-0.3.2/tomboy_0.3.2-1_i386.deb)  which, from what I've seen so far works without a problem.[/QUOTE]

That sounds like a good solution then.  I still think I may wait (even though my excitement may get the better of me).

---

### Post by nehalem on 2005-05-02
[QUOTE=jdong]There are no Debian packages for MonoDevelop 0.6 yet. I'll wait for Sid or Breezy to get them, because getting too far ahead of the development release spells living nightmare when upgrading to the next release :)[/QUOTE]

What about beagle, maybe with some nautilus integration.  That's not too far ahead right.

 :grin: 

(joking)

---

### Post by jdong on 2005-05-02
Ok, so do you guys want Mono bumped to stable? Or does it need further testing?

---

### Post by gbil on 2005-05-03
[QUOTE=jdong]Ok, so do you guys want Mono bumped to stable? Or does it need further testing?[/QUOTE]


Well every app I have tested so far with this version (Monodevelop, beagle, tomboy, fspot) works fine so it could go to stable.

---

### Post by xmlblog on 2005-05-03
[QUOTE=gbil]Well every app I have tested so far with this version (Monodevelop, beagle, tomboy, fspot) works fine so it could go to stable.[/QUOTE]
 Thank you very much for this port. I *finally* managed to install mono 1.1.6. I am a Linux nubie and was wondering several things both directly related to this thread as well as more generally. Any answers or pointers in the right direction are greatly appreciated. 
On-topic:
When I got mono, I noticed MonoDevelop and mod_mono were absent. Can I just grab these from go-mono.org and they *should* work? If not, is there some other location? I noticed gbil mentioned he got MonoDevelop (and beagle) to work. 

General:
Why are backports necessary to begin with? Pardon my ignorance, but it seems to me like having library dependencies installed should be the end of the issue. Clearly, this is not the case and I'm wondering what is it about Linux architecture that makes it necessary to backport code to various distributions (Debian in particular). 

Ex. Windows Server 2000, 2003, XP doesn't matter as long as .NET 1.1 is installed and all library dependencies resolved I can compile and .NET srouce into an app and have it work. Again, pardon my ignorance with this platform but coming from that world the easiest way for me to understand concepts is by analogy... 

Thanks again.

---

### Post by Nis on 2005-05-03
Backports aren't really a Linux in general thing but more of a distribution specific thing.  With Ubuntu (and Debian stable) the only time an application or library is updated is if there is a serious bug or security release.  And only the patches that fix the bug or security hole are applied.  Any new features are not applied to make technical support easier by not having multiple versions of an application available with multiple features.  A backport is an unofficial package that adds the new features but at the cost of being, well, unofficial.  Support is not offered on all unofficial packages (backports and anything from uni/multiverse).

jdong provides a great service by making backports of some things.  In the case of Mono version 1.1.x is vastly superior to 1.0.x but because Ubuntu will not release a new feature version to a stable release a backport is necessary.  This whole thing is a non-issue on some distributions; Fedora regularly releases new feature versions of some packages and a distribution like Gentoo releases new feature versions on everything (although it takes forever for GNOME to be considered stable on Gentoo).

As far as the compile thing goes you'll need Mono to develop Mono apps (C# code).  The older versions of Mono might not have all the features you need implemented so if you're going to code a Mono app you should use the latest stable version.

---

### Post by jdong on 2005-05-03
[QUOTE=xmlblog]
Ex. Windows Server 2000, 2003, XP doesn't matter as long as .NET 1.1 is installed and all library dependencies resolved I can compile and .NET srouce into an app and have it work. Again, pardon my ignorance with this platform but coming from that world the easiest way for me to understand concepts is by analogy... 

Thanks again.[/QUOTE]

Windows has the same problems:

1. MS compiled .NET for each version of Windows -- If there were 300 distributions of Windows, there'd be a similar problem ;)

2. If I install a 3rd party library in .NET, similar library versions result.


Backports are necessary because each distribution's binaries are different because they all use slightly differing libraries.

---

### Post by rjlawr on 2005-05-04
[QUOTE=jdong]There are no Debian packages for MonoDevelop 0.6 yet. I'll wait for Sid or Breezy to get them, because getting too far ahead of the development release spells living nightmare when upgrading to the next release :)[/QUOTE]

jdong, there is an offiical website for Debian pkgs of Mono / Monodevelop at [http://pkg-mono.alioth.debian.org/](http://pkg-mono.alioth.debian.org/) .  The people at this website are the ones that submit the packages to Debian Sid.  If nothing else, a release candidate of monodevelop 0.6 can be built from their source packages.  **monodevelop 0.5.1 will not work with mono 1.1.6, as it is a known problem**.

I was (with some trouble) able to build monodevelop 0.6 from source and create a  *.deb with checkinstall, though its not suitable for redistribution. 

The new packages seem to work well and appear to be stable. Thanks for your work on getting these packages working.

---

### Post by jdong on 2005-05-04
[http://debian.meebey.net/monodevelop/source/monodevelop_0.6.orig.tar.gz](http://debian.meebey.net/monodevelop/source/monodevelop_0.6.orig.tar.gz)


Alright, I'll take a look at the those sources and see if I can make a MonoDevelop deb.

---

### Post by xmlblog on 2005-05-04
Thank you all for educating me. 
One question I still have, do I even need to request mod_mono be backported? Is there another way to write Mono (1.1.6)/ASP.NET  web apps for Apache2?

---

### Post by jdong on 2005-05-04
I don't understand how mono works too much. mod-mono is currently at 1.0-1 ([http://packages.ubuntu.com/hoary/web/libapache-mod-mono)](http://packages.ubuntu.com/hoary/web/libapache-mod-mono)), which is the current Ubuntu Hoary version.


Is there another package? Or should I just compile mod-mono against the new mono-dev? I'll do the latter right now.

---

### Post by Juergen on 2005-05-06
When installing I get the following errors for each *.deb (partly translated from german):
> E: /var/cache/apt/archives/mono-jit_1.1.6-2~5.04ubp1_i386.deb is not a valid DEB-Package.
E: Prior errors apply to /var/cache/apt/archives/mono-jit_1.1.6-2~5.04ubp1_i386.deb
debconf: apt-extracttemplates failed: Invalid filedescriptor
But after that the packages are unpacked and installed - and they seem to work.

---

### Post by XDevHald on 2005-05-06
jdong, the latest is 0.8 of mod_mono. 
[http://go-mono.com/archive/xsp-0.10.html]("http://go-mono.com/archive/xsp-0.10.html")

And mono 1.1.7
[http://go-mono.com/archive/1.1.7](http://go-mono.com/archive/1.1.7)

And check out - [http://www.mono-project.com/Downloads]("http://www.mono-project.com/Downloads") for those that want a little more detail on the latest information or release of mono.

---

### Post by jdong on 2005-05-06
[QUOTE=Juergen]When installing I get the following errors for each *.deb (partly translated from german):

But after that the packages are unpacked and installed - and they seem to work.[/QUOTE]
Yeah, I see this. It's due to my inability to sign packages properly.

I'm rolling back the repository now.

---

### Post by nehalem on 2005-05-06
[QUOTE=rjlawr]jdong, there is an offiical website for Debian pkgs of Mono / Monodevelop at [http://pkg-mono.alioth.debian.org/](http://pkg-mono.alioth.debian.org/) .  The people at this website are the ones that submit the packages to Debian Sid.  If nothing else, a release candidate of monodevelop 0.6 can be built from their source packages.  **monodevelop 0.5.1 will not work with mono 1.1.6, as it is a known problem**.

I was (with some trouble) able to build monodevelop 0.6 from source and create a  *.deb with checkinstall, though its not suitable for redistribution. 

The new packages seem to work well and appear to be stable. Thanks for your work on getting these packages working.[/QUOTE]

Well monodevelop is working for me.  It seems to have bugs but I know I have mono 1.1.6 on my machine (I have beagle using it and stuff).  Also tomboy has worked without a problem?  Is there something I'm missing?  Poeple keep reporting that these programs aren't working but they are for me so I'm wondering what I may have done differently...

EDIT:  I shoudl say that monodevelop doestn' seem to work perfectly.  Autocompletion doesn't seem to work but to be honest it's always seemed pretty fickle to me anyway (I was hoping the .6 would address some of this as I understand it's a major bug fix version)

---

### Post by jdong on 2005-05-06
[QUOTE=jdong]Yeah, I see this. It's due to my inability to sign packages properly.

I'm rolling back the repository now.[/QUOTE]

UPDATE: Rolling back 10GB of packages is a pretty time-consuming endeavor, especially if I issue the command incorrectly twice ;)

I hope to have this straightened out by tonight.

---

### Post by bdoetsch on 2005-05-07
tomboy works if you use the version to be released soon... but f-spot doesn't work anymore. at least not for me - see [bug #302853 ](http://bugzilla.gnome.org/show_bug.cgi?id=302853)

---

### Post by Yolteotl on 2005-05-10
jdong, are you planning on backporting MonoDevelop? Since version 0.6 now available.

BTW, let me take the oportunity to thankyou on this great service you are providing to us Ubuntu users.

---

### Post by ow50 on 2005-05-12
The Hoary muine segfaulted on song change with this new mono. Went back to Hoary mono and it works again.

As others too have reported problems with Hoary versions of mono apps, shouldn't this keep the mono packages out of the stable repository?

---

### Post by Ozitraveller on 2005-05-14
How can I install mono, when I try using synaptic I get circular references issues?

---

