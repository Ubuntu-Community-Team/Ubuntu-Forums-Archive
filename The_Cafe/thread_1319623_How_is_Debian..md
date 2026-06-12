---
title: "How is Debian."
date: 2009-11-08
forum: The Cafe
---

### Post by kio_http on 2009-11-08
Has anyone used Debian? I want to know how is it. A review would be appreciated.

---

### Post by szymon_g on 2009-11-08
yes, i think that someone here used debian
it's nice

---

### Post by kk0sse54 on 2009-11-08
[http://distrowatch.com/table.php?distribution=debian](http://distrowatch.com/table.php?distribution=debian)

---

### Post by Xbehave on 2009-11-08
Far too many on this forum to list, key points:
[LIST]
[*]It's stable or rolling release or the [best of both ]("http://jaqque.sbih.org/kplug/apt-pinning.html").
[*]It is harder to install prop drivers than ubuntu (well it was in lenny)
[*]It lacks a few desktop specific tweaks that haven't reached upstream yet.
[*]Installing from the netinstall CD, gives you plenty of choices
[/LIST]

---

### Post by mthei on 2009-11-08
If you only use the many GUI tools that Ubuntu provides, you may feel a little lost with Debian. So, as mentioned above, you may have trouble installing some proprietary drivers if necessary.
That said, my install had all sound codecs (including MP3 and AAC) installed by default (I think it installs these depending on where you live).
After using Debian for over a year, there have been only two small issues that I have had - one was a Kernel upgrade not letting me boot, leaving me to use the previous one I had installed (this was still when Lenny was the "testing" branch, and I had resolution issues upon resuming from sleep mode (although startup takes about 30 seconds, so I rarely use suspend anymore anyway).
But aside from the GUI tools, I've not really noticed any real difference between Debian and Ubuntu.

---

### Post by kerry_s on 2009-11-08
debian is more hands on, you actually have to pick the program & install it.
everything is in the repo though, so you just use synaptic to install it.
i don't think proprietary drivers are a issue, as i can see them in the repo, so it's a simple install(see pic).

the main thing is the stuff in lenny can be old, thats what makes them stable. for instance iceweasel(firefox) is 3.0.6.

i recommend using the expert mode to install.

---

### Post by slakkie on 2009-11-08
Debian is really Ubuntu, but a bit harder and more conservative and of course, it also pre-dates Ubuntu :).

I have two Debian installs myself, one running stable (lenny), which can be compared to the Ubuntu LTS versions. Package versions on Debian stable are older then in Ubuntu LTS. Stable is aimed at servers.
My other install is Debian testing. This is for me a machine which can compare itself with Ubuntu as a desktop OS. The packages are newer then on stable, at the same version or a bit older versions compared to regular Ubuntu releases. I have the exact same setup as I have with Ubuntu except for and do not notice a thing, or [one thing really](http://en.wikipedia.org/wiki/Mozilla_Corporation_software_rebranded_by_the_Debian_project).

Then you have Debian unstable aka sid. This is the version Ubuntu is based on, with the exception of Ubuntu LTS version - based on Debian testing. In this version you have bleeding edge, so bugs may break your system. like they would say: *if it breaks: you get to keep both parts :-)*. I personally mix the packages from unstable on my testing desktop. I use the same software on both distro's, Debian is faster then Ubuntu. The simutrans version in Debian is more stable compared to Karmic. Debian automated the grub2 migration from grub-legacy (but this will be the default in Ubuntu 10.04 iirc). 

I approach Debian and Ubuntu the same, for me the are the same. There are differences, yes, but all the things you can do in Debian you can do in Ubuntu.

---

### Post by kio_http on 2009-11-08
Will I get latest updates easily. Like Kubuntu offeres KDe 4.3.3 almost instant to release.

---

### Post by SunnyRabbiera on 2009-11-08
> **kio_http said:**
> Will I get latest updates easily. Like Kubuntu offeres KDe 4.3.3 almost instant to release.

Not if you use lenny/stable

You may want to try debian testing (squeeze), more stable then sid but more up to date then lenny.
[http://www.debian.org/releases/testing/](http://www.debian.org/releases/testing/)

---

### Post by Hallvor on 2009-11-08
There is not much difference. Debian is a little faster and more KISS. It is just a little more conservative and the stable branch has less bugs.

> **slakkie said:**
> Package versions on Debian stable are older then in Ubuntu LTS. Stable is aimed at servers.


No. Lenny was released on the 14th of February this year. The last Ubuntu LTS was released in april 2008, so the package versions are newer in Debian Lenny. Secondly, there is always the possibility to use the backports repository.

Stable is great on servers - or if you just want (or need) stability on your desktop. It is not as exciting as running the rolling release Debian testing, but it never breaks.

---

### Post by Rambar on 2009-11-08
If you want to try Debian be careful installing it. If you want to dual boot it with Ubuntu on a Ext4 partition you'll have to work a little. Debian overwrites your Grub and installs 0.97 which doesnt read EXT 4. So once you install it you have to get Grub 2 in order to be able to boot into Ubuntu again.

 Yes, this may sound like a stupid warning, but made me panic when I first booted into Debian.

---

### Post by Icehuck on 2009-11-08
Debian is not too bad, but I think I will potentially like it more when they ditch sysv init.

Right now I'm really liking CentOS a whole lot better then anything at the moment. All my servers at home are now CentOS.

---

### Post by JeffersonX on 2009-11-08
I used Debian for a few years. Debian is a great operation system, but I don't recommend it for new Linux users because Debian requires some abilities that new users probably don't have. For example to configure some things we have to do it in text mode. For Linux learning Debian is a good way.

Debian also have apt-get, Synaptic, sudo (we have to configure sudo to enable it), graphical boot (we have to configure it to enable it) and update-notifier like Ubuntu.

Debian has the same Ubuntu features, but many items requires manually configuration to enable.

If you want the most recent software, Debian might disappoint you because Debian privileges the stable softwares version. So in Debian Stable is common to see older version of some softwares.

Other interesting thing is Mozilla Firefox. Debian has a Firefox-based browser called Iceweasel. A "fight" with the Firefox developers was the reason of this software replacement. Icewaesel works fine and it is Firefox with other name.

Gnome is the desktop environment in Debian although we can have KDE.

For more information see Debian's website:
[www.debian.org](www.debian.org)

---

### Post by beercz on 2009-11-08
Debian is fine!

Thanks for asking.

---

### Post by madhi19 on 2009-11-08
Debian is fine the community on the other hand... Well lets just say they are on the extreme Stallman side of the Gnu/Linux spectrum. lolll
[IMG]http://ubuntuforums.org/picture.php?albumid=1351&pictureid=5168[/IMG]

---

### Post by Exodist on 2009-11-08
> **kio_http said:**
> Has anyone used Debian? I want to know how is it. A review would be appreciated.


I love using Debian. Its fast, stable and flexible.
I am not sure how you would want me to do a write up, it uses base defaults for the Desktop Enviroments like Gnome and KDE. So they leave those up to you to customize other then the default debian wallpaper.

Biggest keynote on the stable release is that when you install it, there is not 4 million bug patches. Yes there are a small handfull of security ones. But after you isntall it, its stable. There isnt any of that **** "maybe they will fix it soon" issues like you find on some distros.
It has a fairly long release cycle, 22months on 5.0 Lenny. So the software may not be the most cutting edge, its not going to break with you after you install it.

In the end, there isnt much really diferent then ubuntu except:
- Not sigle user configured like Ubuntu, so you can easily add multiple users.
- Doesnt use "sudo" by default, so you just have to "su" into root mode to install stuff.
- Doesnt include "PissAudio" in default setup.
- Not poo brown.


Hope this helps..

- Exo

---

### Post by MaxIBoy on 2009-11-08
I use Debian on my laptop.

If you install Gnome on it, then **superficially** there's not much difference from the stock Ubuntu setup (same with KDE and Kubuntu, XFCE4 and Xubuntu, etc.) It's true that you are asked to give a root password, and that your main user isn't by default a sudoer. However, it's really only twenty minutes to change that (most of that is changing all the menu entries from gksu to gksudo.) You may find you prefer it Debian's way, but I didn't. No big deal.



There are two ways to use Debian: you can use one of the stable releases or one of the rolling repositories. 

The stable releases are going to come out exactly every two years from now on, similar to the six month cycle in Ubuntu, but I don't think there will be as much effort to make a dist-upgrade easy after two years of drift between versions. Outdated stable versions are also kept on life support for one full year past when the next stable release comes out. So if you want utter, complete stability, don't mind using three-year-old versions of software, and don't mind reinstalling every two or three years, use one of the Debian releases and it will be great for you.


You can also use the rolling repositories. 

"Testing" is whatever the repository is which is destined to become the next stable release. So the testing repository used to be called Lenny until Lenny was released as stable, now it's called Squeeze. Testing is still a rolling repository, it just changes names now and then. You get a major advantage of a rolling release distro, which is that you don't need to worry about distro updates. Squeeze is still solid like a rock, almost as much as a stable release. But it's still not cutting edge. Expect to see a delay of three weeks to four months for a new version of something to get into the testing repo (depending on how important the update is.) Debian has a strict quality-assurance policy, a package must filter through Unstable and usually also Experimental to get here. 

"Unstable," AKA "Sid," is more of a "beta test" repository. I can't remember who said this originally, but this person phrased it best-- "Sid isn't really unstable. It's just a moving target." It depends on what you do with it and what you install, but I personally hanven't had too many problems with it. You get the advantages of a rolling-release distro, a bit more cutting edge than testing, and you can still use apt (best package management in the world!) However, as a precaution, if you run Sid, you may wish to disable automatic updates and apply updates through Synaptic manually. That way you can make sure packages don't clash and remove each other as you upgrade them.

Unstable and Testing can be easily enabled both at once and freely intermixed. However, be careful with holding back too many packages, dependancy issues get real complicated real quick.

"Experimental" isn't a complete distro, in that it doesn't have all the packages needed for a usable system. To use the experimental repos, you must also enable one of the other ones (obviously Sid is going to work best for this.) Experimental is the first stage of Quality Assurance. There is usually no checking to make sure if a package is going to clash with another due to dependency issues, so disabling automatic updates is a **must**. Expect to spend at least 20-30 minutes every other day, going through updates to see whatever can be installed without breaking anything else. If you like the bleeding edge and have the time to micromanage your OS, by all means, go for Experimental, but be very careful.



You can see a good example of how the Debian repositories are managed using the "status of gnome in Debian" pages:
[http://www.0d.be/debian/debian-gnome-2.24-status.html](http://www.0d.be/debian/debian-gnome-2.24-status.html)
[http://www.0d.be/debian/debian-gnome-2.26-status.html](http://www.0d.be/debian/debian-gnome-2.26-status.html)
[http://www.0d.be/debian/debian-gnome-2.28-status.html](http://www.0d.be/debian/debian-gnome-2.28-status.html)
Expect to see a page created soon for Gnome 2.30 (or 3.00, these numbers both refer to the same version.) Then you can watch it all the way through.

You can also see more information if you look in a "PTS" page for a package:
[http://packages.qa.debian.org/libx/libxi.html](http://packages.qa.debian.org/libx/libxi.html)


You can infer all kinds of things about Debian by looking at that stuff.





Overall, I'd say there isn't one single Debian OS. All the Debian operating systems are great, but which one you choose depends on what you want.




I hope this impromptu review was helpful.

---

### Post by ~sHyLoCk~ on 2009-11-08
Debian as server is alright but as desktop you'd probably want to use latest stuffs so enable sid.

---

### Post by jheaton5 on 2009-11-08
I run Debian Lenny (stable) on my home server.  I run Squeeze (testing) as a dual boot with Ubuntu Karmic on my laptop.  Debian is more spartan than ubuntu.  There are not many gui tools and the recommended way to administer the system is through the command line.  I like it a lot.  I would agree that it is not for linux beginners.  But I have learned more about the Linux OS using Debian than using Ubuntu.

---

### Post by Xbehave on 2009-11-08
> It's true that you are asked to give a root password, and that your main user isn't by default a sudoer. However, it's really only twenty minutes to change that (most of that is changing all the menu entries from gksu to gksudo.)
If you use the expert install mode you can choose to install it sudo style.

> Unstable and Testing can be easily enabled both at once and freely intermixed. However, be careful with holding back too many packages, dependancy issues get real complicated real quick.
Do you get problems if you do it the other way, hold forward a few pacakges (e.g firefox,gimp,etc) but keep the rest one distro behind? (e.g stable+ a few unstable/testing)

p.s thanks for the thorough review.

---

### Post by kevCast on 2009-11-08
> **Xbehave said:**
> If you use the expert install mode you can choose to install it sudo style.


Do you get problems if you do it the other way, hold forward a few pacakges (e.g firefox,gimp,etc) but keep the rest one distro behind? (e.g stable+ a few unstable/testing)

p.s thanks for the thorough review.

Do not mix stable with another branch. You're asking for trouble. Instead, use backports.

[http://backports.org/dokuwiki/doku.php]("http://backports.org/dokuwiki/doku.php")

---

### Post by MaxIBoy on 2009-11-09
> **Xbehave said:**
> Do you get problems if you do it the other way, hold forward a few pacakges (e.g firefox,gimp,etc) but keep the rest one distro behind? (e.g stable+ a few unstable/testing)


As a rule, Testing and Unstable can be mixed if you are careful. It doesn't matter if you pick mostly Testing or mostly Unstable. 

However, mixing Stable with Testing/Unstable is a **big** no-no.

Until recently, I held nm-applet back to the Lenny version while running Sid, but that was very tricky to maintain. I had to pin a bunch of other packages and refuse certain upgrades. Every once in a while I'd screw it up and have broken packages. I was very glad to see this arrangement go.

I imagine that doing the opposite, mostly Lenny with a few Unstable/Testing, would be even worse. That package will gradually drag its dependencies forward with it, resulting in a slippery slope; eventually you'd be running Unstable/Testing anyway. Might as well dist-upgrade and save yourself a lot of headaches.

---

### Post by Yellow Pasque on 2009-11-09
I run sidux (based on Debian sid/unstable) as an Ubuntu alternative.

---

### Post by blueturtl on 2009-11-09
I first migrated to Debian when I had to work on a really old system. I had downloaded Ubuntu's alternate installer CD so that I would be able to install a pure command line based system and then work up from there. However the Ubuntu installer freaked out at the partitioning stage.

I remembered Ubuntu being based on Debian, so I went and downloaded the then latest stable Debian (4.0 Sarge). Debian's partition tool worked, and so I was now working with Debian and not Ubuntu. Things I immediately noticed being different:

[LIST]
[*]Debian has a separate root account, and thus a separate root password. Your own user cannot administer the system. Personally I think both approaches have their benefits. Also Debian can be set up to use sudo, just like Ubuntu.
[*]Lack of branding. No "AppCenter" or "UbuntuOne" type things. Firefox is called Iceweasel because the some trademark/copyright issues.
[*]Certain things that Ubuntu has made easy for newbies (like installing video drivers not included with X.org) need to be done manually in Debian.
[*]Absolute stability. I got used to a certain amount of shakiness with Ubuntu: every release would break something previously working while fixing some prior bugs. If hard crashes (kernel panic) are rare in Ubuntu, they are absolutely non-existent with Debian stable.
[*]Obviously since the stable release has a longer release cycle, by the end of the cycle Debian's applications tend to be much older than those in the latest Ubuntu release.
[/LIST]

Personally I think Debian is a great system for any veteran Ubuntu user to consider. It is a bit more hands on, but considerably more stable. As a desktop user, the only thing I'm really left missing was the latest Firefox (which I can get from Mozilla.com anyway). For me, Debian has become a new mainstay on all our computers.

---

### Post by Hallvor on 2009-11-09
> **MaxIBoy said:**
> 
The stable releases are going to come out exactly every two years from now on, similar to the six month cycle in Ubuntu, but I don't think there will be as much effort to make a dist-upgrade easy after two years of drift between versions.

I think there may be a misunderstanding here. The stable releases are not going to come out in fixed intervals. The repository freezes will be at fixed intervals, but the releases will come when it is done, tested and ready.

As to dist-upgrades, they have been working very well in the past. I talked to a guy that had the same install of Derbian running for nine years with several dist-upgrades without any issues. This has been a priority among the Debian developers in the past, and it will probably continue to be so in the future. When Squeeze arrives, I`ll dist-upgrade and let you know how it goes. ;)

---

### Post by Yellow Pasque on 2009-11-09
> **madhi19 said:**
> Debian is fine the community on the other hand... Well lets just say they are on the extreme Stallman side of the Gnu/Linux spectrum.

On the plus side, after a lengthy battle with Mozilla, they did name their Firefox clone after a weasel and gave it a logo of the weasel humping the Earth (the browser has since been renamed and given a new logo for the sake of political correctness):

[IMG]http://engtech.files.wordpress.com/2006/10/th_humpingiceweaselst6.gif[/IMG]

---

### Post by Rambar on 2009-11-09
> **madhi19 said:**
> Debian is fine the community on the other hand... Well lets just say they are on the extreme Stallman side of the Gnu/Linux spectrum. lolll


I agree. Asking #Debian is not like asking #Ubuntu at all....

---

### Post by Exodist on 2009-11-09
> **Rambar said:**
> I agree. Asking #Debian is not like asking #Ubuntu at all....


On the bright side if you can look through that, your more likely to get a more correct answer. Just be polite, straight forward and dont beat around the bush asking stuff thats been answered a thousand times. ;)

---

### Post by slakkie on 2009-11-09
> **Hallvor said:**
> There is not much difference. Debian is a little faster and more KISS. It is just a little more conservative and the stable branch has less bugs.



No. Lenny was released on the 14th of February this year. The last Ubuntu LTS was released in april 2008, so the package versions are newer in Debian Lenny. Secondly, there is always the possibility to use the backports repository.

I looked on my hardy box and I saw it has newer versions of software compared to the stable branch. The latest Ubuntu version (which are also stable) have newer versions. It could be different per stable release and Ubuntu release. But in general Debian has older packages then Ubuntu. That was the point I wanted to make.

---

### Post by Zoot7 on 2009-11-09
I used Debian stable for about a year before I found Ubuntu.
It's about stable as you can get because of it's long release cycle, but it ages rapidly, I found a lot of the software that was in the repos was quite old and it wasn't easy to upgrade to the latest version for whatever you might want.

If you want stability and don't care about being on the bleeding edge or having the latest version of every utility installed then it's a good Distro, there's also a bit of a learning curve considering if you use all the GUI tools that are provided in Ubuntu, then you'll probably find yourself lost in Debian.

My 0.02...

---

### Post by Exodist on 2009-11-09
I've got to be missing something. Whats these Ubu* tools everyone keeps mentioning? Most all the tools I ever seen on Ubuntu are the same *Gnome* tools on every Gnome desktop I have seen. Including Debian. Only distro I have seen with something diferent was SuSE's YaST.
It may be I am just used to hoping over as SuperUser or sudo and editing everything by hand. This is why I am asking.
Other then the Ubuntu Proprietary Driver installer, I cant think of another program except the just introduced Software Centre.

---

### Post by Hallvor on 2009-11-09
*****

---

### Post by Hallvor on 2009-11-09
> **slakkie said:**
> I looked on my hardy box and I saw it has newer versions of software compared to the stable branch.

Something tells me you have backports enabled. Ubuntu 8.04 is almost a year older than Debian Lenny.

> But in general Debian has older packages then Ubuntu. That was the point I wanted to make.

That is correct.

---

### Post by VertexPusher on 2009-11-09
One of the best things about Debian is that PulseAudio is an optional package, not installed by default, even if you upgrade to Debian unstable. On the other hand, Debian's ALSA packages are not crippled in any way. For example, they include the Jack plugin for ALSA and the asoundconf tool to select the default soundcard if there are several cards (or USB headsets etc.) installed. These things are missing in Ubuntu.

---

### Post by King_Critter on 2009-11-09
Don't think anyone mentioned this yet: [Sidux]("http://sidux.com/").

Basically, it's Debian Sid with a few tweaks and it's own bug-fixing repository, which adds a bit of stability.

I just installed it on my netbook, and everything seems to going just fine. ;)

---

### Post by ~sHyLoCk~ on 2009-11-09
King_Critter

Did you install from the 2009.3 preview or the 2009.2 one? I was interested to see how the new artwork is. I just simply love their grub-gfx menu theme. Although I don't think they have shifted to grub2 yet? Maybe in 2009.3 they will.

---

### Post by Yellow Pasque on 2009-11-09
Yeah, I mentioned sidux. It's a great rolling-release, cutting-edge version of Debian AS LONG AS you follow the devs' recommendations (i.e. no Synaptic, check sidux forums before dist-upgrading, no aptitude or auto-remove, etc.)

The bad part of sidux is no GNOME. I'm sure you can still run it, but expect occasional breakage and don't expect support when things go wrong.

---

### Post by slakkie on 2009-11-09
> **Hallvor said:**
> Something tells me you have backports enabled. Ubuntu 8.04 is almost a year older than Debian Lenny.


Compare Firefox on both distro's:

```

Debian:
     3.0.14-1 0
        100 ftp://ftp.nl.debian.org testing/main Packages
     3.0.6-3 0
        500 http://security.debian.org lenny/updates/main Packages
     3.0.6-1 0
        500 ftp://ftp.nl.debian.org lenny/main Packages

Ubuntu:
 *** 3.0.15+nobinonly-0ubuntu0.8.04.1 0
        995 http://security.ubuntu.com hardy-security/main Packages
        995 http://archive.ubuntu.com hardy-updates/main Packages
     3.0~b5+nobinonly-0ubuntu3 0
        990 http://archive.ubuntu.com hardy/main Packages


```

With samba is it the other way around. mplayer is more or less the same.

---

### Post by Hallvor on 2009-11-09
> **slakkie said:**
> Compare Firefox on both distro's:

```

Debian:
     3.0.14-1 0
        100 ftp://ftp.nl.debian.org testing/main Packages
     3.0.6-3 0
        500 http://security.debian.org lenny/updates/main Packages
     3.0.6-1 0
        500 ftp://ftp.nl.debian.org lenny/main Packages

Ubuntu:
 *** 3.0.15+nobinonly-0ubuntu0.8.04.1 0
        995 http://security.ubuntu.com hardy-security/main Packages
        995 http://archive.ubuntu.com hardy-updates/main Packages
     3.0~b5+nobinonly-0ubuntu3 0
        990 http://archive.ubuntu.com hardy/main Packages


```

With samba is it the other way around. mplayer is more or less the same.

OK. I know Debian Lenny has had Iceweasel 3.0.6 all along. Iceweasel in Debian tends to lag behind the releases of Firefox because of rebranding, etc., but almost anything else should be a little newer in Debian Lenny.

---

### Post by snowpine on 2009-11-09
Instead of guessing, compare Debian and Ubuntu package versions here:

[http://distrowatch.com/table.php?distribution=debian](http://distrowatch.com/table.php?distribution=debian)
[http://distrowatch.com/table.php?distribution=ubuntu](http://distrowatch.com/table.php?distribution=ubuntu)

Some things are a little newer in Lenny (the kernel), others are a little newer in Hardy (gnome). Neither of them are "the latest" of course (by design).

---

### Post by OrangeCrate on 2009-11-09
> **kio_http said:**
> Has anyone used Debian? I want to know how is it. A review would be appreciated.

I've used Lenny since it's release, on my home computer, dual booted with Windows 7, and I like it. Here's a tutorial, that will give you the gist of how to install, add repositories, etc. It helped me a lot when I first got started with Debian (and no, I didn't install all of the programs to mimic Windows, I installed just what I wanted.)

[http://www.howtoforge.com/the-perfect-desktop-debian-lenny](http://www.howtoforge.com/the-perfect-desktop-debian-lenny)

This was also of great help in learning Debian:

[http://www.debian.org/doc/FAQ/](http://www.debian.org/doc/FAQ/)

---

### Post by Eisenwinter on 2009-11-09
> **slakkie said:**
> Debian is really Ubuntu, but a bit harder and more conservative and of course, it also pre-dates Ubuntu :).
This should be phrased as "Ubuntu is really Debian, but 'easier' and less conservative'"

---

### Post by julianb on 2009-11-09
> Re: How is Debian

Debian says, "I'm doing well, thanks for asking....  and you, how're you doing?"


But seriously, Debian is so much like ubuntu that it has a whole lot of the same advantages and disadvantages... but Ubuntu is usually easier for a total beginner to use.

---

### Post by judge jankum on 2010-01-16
I was about to ask this same question lol!!!!

---

### Post by 3rdalbum on 2010-01-16
I just tried Debian on my netbook, from the Netinstall CD. I installed Debian because I was sick of my mobile broadband being half-broken in Karmic.

It almost installed itself. I used the 'tasksel' screen to install "Desktop Environment" (Gnome) and that went okay. Then I booted up to find that I'd just installed Debian Lenny and everything was ancient. My screen resolution was wrong, I had no wireless, and Network Manager was the same version as in Hardy so I had no mobile broadband support.

I tried upgrading to Debian Squeeze. The HAL upgrade broke and Gnome wouldn't start; thankfully TWM is included so I could start gnome-panel, Nautilus and Network Manager manually. Of course, NM doesn't work without HAL.

I'm not blaming Debian; I very probably bollocksed it up myself as user error.

Now I'll try Lucid Alpha 2. I don't use my netbook much, and when I do it's only as a netbook anyway. I should really contribute to Ubuntu by testing the next LTS, which I believe will stay permanently on my netbook assuming the wifi and mobile broadband work better.

---

### Post by nitehawk777 on 2010-01-16
Debian Lenny is my main distro.  But if you want a "Debian-Testing" distro all set-up,..just use Parsix.  Parsix is directly based on Debian Squeese,..with the Gnome desktop.

---

