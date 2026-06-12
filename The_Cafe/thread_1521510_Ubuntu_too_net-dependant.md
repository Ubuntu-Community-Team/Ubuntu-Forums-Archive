---
title: "Ubuntu too net-dependant?"
date: 2010-06-30
forum: The Cafe
---

### Post by Stavro on 2010-06-30
Hi all techies! Just wondering if you think that Ubuntu and many Linux distros in general are too reliant on the internet? We all know that sometimes (especially in rural locations) the net can be down for a while.

I like the repositories; they work well but wouldn't it be nice to download programs and updates to keep them for future use rather than re-downloading all over again for another machine/reinstall? I do confess to like the nature of Windows whereby executable installers can be downloaded and saved easily like any other file; one can then reinstall without a working net connection.

Just a thought, let me know what you think?

---

### Post by Timmer1240 on 2010-06-30
Thats a good question thought I heard you could do that but cant remember where I heard it.

---

### Post by cj.surrusco on 2010-06-30
Kinda like this?

[https://help.ubuntu.com/community/AptGet/Offline/Repository]("https://help.ubuntu.com/community/AptGet/Offline/Repository")

---

### Post by Mr. Picklesworth on 2010-06-30
As cj.surrusco's link points out, APT lets CDs act as repositories. So, with an LTS release, the theory is you could stay up to date on the four point releases through its life.
Of course, for anything not in main, you're still doomed.

The problem is it's difficult to just download the list of dependencies for a specific package on another machine, since there's no telling which ones are installed at the moment.

Software Centre should support a user-friendly version of saving your list of installed packages in the future, so maybe the interest in that will bleed over to someone building a &#8220;download packages for the system described by this file and stick them all on a flash drive&#8221; app.

Although that *is* entirely attainable today, albeit less pleasantly: Head to Synaptic, go to File&#8250;Save Markings As. Somebody just needs to do the cute little dependency-grabbing app.

---

### Post by XubuRoxMySox on 2010-07-01
**[COLOR="Blue"]Aptoncd[/COLOR]** allows you, once you have installed all the programs you want, to back up all those installed programs onto a CD. Then you can use them to install them to other computers (without downloading them separately on each machine). It's great for multiple 'puters and dial-up situations.

---

### Post by snowpine on 2010-07-01
Debian offers the entire distro on a 5-DVD set, with "point" upgrades on a supplemental DVD. :)

---

### Post by Stavro on 2010-07-01
Thanks for all the replies! It is nice to know there are several options available.

---

### Post by 98cwitr on 2010-07-01
> **Stavro said:**
> Hi all techies! Just wondering if you think that Ubuntu and many Linux distros in general are too reliant on the internet? We all know that sometimes (especially in rural locations) the net can be down for a while.

I like the repositories; they work well but wouldn't it be nice to download programs and updates to keep them for future use rather than re-downloading all over again for another machine/reinstall? I do confess to like the nature of Windows whereby executable installers can be downloaded and saved easily like any other file; one can then reinstall without a working net connection.

Just a thought, let me know what you think?

APTonCD ftw. Without the net computers are useless imho ;)

---

### Post by Stavro on 2010-07-01
> **98cwitr said:**
> APTonCD ftw. Without the net computers are useless imho ;)

Not applicable to everyone; especially me as I do a lot of music creation and other 'traditional' desktop-tasks which don't require the net whatsoever.

---

### Post by 98cwitr on 2010-07-01
> **Stavro said:**
> Not applicable to everyone; especially me as I do a lot of music creation and other 'traditional' desktop-tasks which don't require the net whatsoever.

and you use Ubuntu?

---

### Post by m4tic on 2010-07-01
Another reason why windows has such a large support base has to be it's ease of software installation for everyone. apt is great but in all honesty not for the poor. the op brought up a good topic and i think this is one of the factors to why desktop linux is left out im some places. where i'm from we do not have many with internet. as i reply i'm on my mobile phone which beside from school or internet cafes i'm disconnected. i dual boot and there's a huge gap between the number of programs i have in ubuntu and windows. 

I just wish offline installs of linux software should be packaged with all dependencies since those with a good connection use package managers like mcc and apt

---

### Post by NightwishFan on 2010-07-01
I would like to see a nice way to get software offline. A while back someone tried to package "superdebs" but that sounded sloppy. The solutions we have now still involve some sort of program doing the downloading somewhere.

---

### Post by m4tic on 2010-07-02
.deb today are like links

---

### Post by Stavro on 2010-07-04
> **98cwitr said:**
> and you use Ubuntu?

hey, I didn't mean to be 'dry and boring' in response to your comment about computers being useless without the net; on hindsight you were being lighthearted I know.

In reply to using Ubuntu or not for media-creation, actually the truth is that I'm exploring the possibilities of it right now; but most of my media creation activities involve using Windows. I have more than one computer so there is no downtime involved in trying a new avenue.

This Windows background of mine is for the main what prompted me to start this thread in the first place. I'm the sort-of person that once I find something that works well I will stand-by it until it is quite clearly superseded by a later version or other package entirely. Thus, keeping things on CD is a big bonus; I cannot rely on the net to always offer an old download and I cannot rely on it anyway because I'm in a really rural area where the net can be sporadic.

I just like 'owning' things on CD; it seems more substantial. I'm not saying we should all go back to the terrible wastefulness of those giant cardboard boxes of the 90's too!

Thanks everyone for all the replies, it has been an interesting read and +1 for Mr. Picklesworth who thinks we need the cute little app that does all the hard-work for this task.

---

### Post by rahilm on 2010-07-04
> **m4tic said:**
> Another reason why windows has such a large support  base has to be it's ease of software installation for everyone. apt is  great but in all honesty not for the poor. the op brought up a good  topic and i think this is one of the factors to why desktop linux is  left out im some places. where i'm from we do not have many with  internet. as i reply i'm on my mobile phone which beside from school or  internet cafes i'm disconnected. i dual boot and there's a huge gap  between the number of programs i have in ubuntu and windows. 

I just wish offline installs of linux software should be packaged with  all dependencies since those with a good connection use package managers  like mcc and apt

One of my biggest gripes with linux. I never updated my system.  Hesitated to install anything and spend hours or even days of trying to  find a way to cut out the net dependence. Those were the days when i was  without an unlimited bandwidth connection.

I now have an unlimited connection, so this doesn't affect me now. But  problems do come up when i try to 'spread the word'. I currently use  this method which is time consuming (but worth it)
[http://www.omgubuntu.co.uk/2010/05/with-all-new-installing-of-ubuntu-and.html](http://www.omgubuntu.co.uk/2010/05/with-all-new-installing-of-ubuntu-and.html)

Even though I don't have a problem with this , I do want this net dependence to go away. Because I understand the problem people face.

One solution I thought long ago was to have a modified gdebi which will scan for the dependencies within the folder and install it. This will make backing and sharing of software much much easier. 

Obviously, this method cannot be used for linux in general. Because different distros come bundled with different dependencies. If there are still some dependencies left out, option can be given to  download them (kind of like directx dependency in windows). Also, it is quite possible the user may have removed some dependecy. (like i remove all that nvidia and hplip stuff) Bundling programs with every kind of dependency is really stupid.



> **Stavro said:**
> Not applicable to everyone; especially me as I do a lot of music creation and other 'traditional' desktop-tasks which don't require the net whatsoever.
Hey.. how did you install the codecs and the software without internet?? or do you use PitVi and ogg format?

---

### Post by Stavro on 2010-07-04
> **rahilm said:**
> Hey.. how did you install the codecs and the software without internet?? or do you use PitVi and ogg format?

My question came about because of my familiarity with Windows and how easy it is to keep things once you've downloaded them. I'm not sure how to do this on Ubuntu as I'm still learning and hence my question in the title of this thread.

If I misunderstood you and you are indeed asking how this is done on Windows, then I'll simply say codec downloads are easy to keep provided they have an executable installer (which is often the case).

I'm thinking of the excellent ffmpeg package which can be saved to a flash-drive along with a lot of other quality encoders; RazorLame would be one such an example. Even VLC media player is really good and serves as an excellent case in point: I find that sometimes new versions of this program introduce regressions, so consequently, I keep 'gold' versions and they are kept safe on removable-media for re-instillation on any Windows box/installation. On Linux, even upgrading to the latest version of VLC is a hassle; I don't even know how one would go about installing a specific legacy version.

---

### Post by Warpnow on 2010-07-04
The dependence on the internet is one of the biggest differences between raw debian and ubuntu. If you have an offline machine I'd highly reccomend going with Debian.

---

### Post by NightwishFan on 2010-07-04
Warpnow, you mean something like grabbing the Debian DVD?

---

### Post by MCVenom on 2010-07-04
You can buy repo-on-DVD sets for Ubuntu too: [http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu/repo.html](http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu/repo.html)

---

### Post by Warpnow on 2010-07-04
> **NightwishFan said:**
> Warpnow, you mean something like grabbing the Debian DVD?

Well, rather, the DVDs. Aren't there like 5 of them now?

Once you have them all you don't need internet access anymore to install packages.

---

### Post by NightwishFan on 2010-07-04
I know Ubuntu has a DVD available as well but it is not nearly the same thing. It mostly contains a lot of the main, and some restricted packages like NVidia drivers. (At least I think so).

I know that Debian sorts their packages due to popularity so I am pretty sure the first and perhaps the second DVD may be quite sufficient.

---

### Post by robert shearer on 2010-07-05
Anyone use Keryx...?
[http://keryxproject.org/](http://keryxproject.org/)

Interested as they say...
> Keryx is a portable, cross-platform package manager for APT-based (Ubuntu, Debian) systems. It provides a graphical interface for gathering updates, packages, and dependencies for offline computers. Keryx is free and open source. 

---

### Post by neoargon on 2010-07-05
You don't NEED to download packages each time , because the downloaded ones will be kept in cache . The downloaded packages can be found in the folder  /var/cache/apt/packages  . You can copy the packages and save somewhere for future use . 

But it is ofcourse difficult to use Ubuntu without net . It can be a reason why Ubuntu is not popular in third world countries .  I did not have net about 3moths ago . It was very difficult to install apps .

---

### Post by neoargon on 2010-07-05
> **m4tic said:**
> Another reason why windows has such a large support base has to be it's ease of software installation for everyone. apt is great but in all honesty not for the poor. the op brought up a good topic and i think this is one of the factors to why desktop linux is left out im some places. where i'm from we do not have many with internet. as i reply i'm on my mobile phone which beside from school or internet cafes i'm disconnected. i dual boot and there's a huge gap between the number of programs i have in ubuntu and windows. 

I just wish offline installs of linux software should be packaged with all dependencies since those with a good connection use package managers like mcc and apt

Just consider how apps are installed in iphone

---

### Post by nerdtron on 2010-07-05
> **robert shearer said:**
> Anyone use Keryx...?
[http://keryxproject.org/](http://keryxproject.org/)

Interested as they say...


+1

I personally haven't use it but I think this one is good too!

---

### Post by rahilm on 2010-07-05
> **neoargon said:**
> You don't NEED to download packages each time , because the downloaded ones will be kept in cache . The downloaded packages can be found in the folder  /var/cache/apt/packages  . You can copy the packages and save somewhere for future use . 

But it is ofcourse difficult to use Ubuntu without net . It can be a reason why Ubuntu is not popular in third world countries .  I did not have net about 3moths ago . It was very difficult to install apps .

yeah.. another way to backup apps. This method will work only if you pledge to never update you system. Else, it may cause broken packages.

---

### Post by EXCiD3 on 2010-07-05
I made Keryx so that I could use Ubuntu easily on my dial connection (which I couldn't ever get my modem driver working on Linux anyways, so I was completely offline). It works much easier than APTonCD for most people, you get a GUI, can use it from any operating system, and can install your software and updates (including their dependencies) in a snap, just like you would with Synaptic. The problem with using Synaptic's script is that offline, you cannot download the list of available packages so you won't be able to make useful download scripts with it. Keryx lets you do that on any computer. Check it out, Linux isn't too bad offline with it. :)

---

### Post by NightwishFan on 2010-07-05
So you are the keryx dev? Aweseome my friend, you should keep up the good work. Perhaps enough to get keryx in universe. It would be useful even for Ubuntu users with the net to distribute packages.

---

### Post by EXCiD3 on 2010-07-05
> **NightwishFan said:**
> So you are the keryx dev? Aweseome my friend, you should keep up the good work. Perhaps enough to get keryx in universe. It would be useful even for Ubuntu users with the net to distribute packages.

Yessir, [mac9416]("http://ubuntuforums.org/member.php?u=506161") is my trusty sidekick. Actually, Michael Vogt contacted me about getting it into the repositories a few weeks ago so I built a PPA for it ([https://launchpad.net/~keryx-admins/+archive/keryx-ppa](https://launchpad.net/~keryx-admins/+archive/keryx-ppa)) and it seems to be working alright. I never really gave that much consideration because it's only useful if the online machine would have Keryx installed from the repositories, but I guess it could be useful.

If you've got any ideas or questions, let me know. I'm always open to new ideas. And thanks for the support! :D

---

### Post by rahilm on 2010-07-06
I downloaded the latest keryx tar.gz  and extracted it..
I cd in the linux folder and run ./keryx
i get this error
```

Loading config: /home/rahil/keryx/linux/keryx.conf

(keryx:2487): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so) initialization check failed: Gtk+ version too old (micro mismatch)

(keryx:2487): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so) initialization check failed: Gtk+ version too old (micro mismatch)

(keryx:2487): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so) initialization check failed: Gtk+ version too old (micro mismatch)

(keryx:2487): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so) initialization check failed: Gtk+ version too old (micro mismatch)

(keryx:2487): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so) initialization check failed: Gtk+ version too old (micro mismatch)

(keryx:2487): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so) initialization check failed: Gtk+ version too old (micro mismatch)
/home/rahil/.themes/Finery/gtk-2.0/gtkrc:256: Unable to locate image file in pixmap_path: "panel_bg.png"

(keryx:2487): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so) initialization check failed: Gtk+ version too old (micro mismatch)

(keryx:2487): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so) initialization check failed: Gtk+ version too old (micro mismatch)

(keryx:2487): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so) initialization check failed: Gtk+ version too old (micro mismatch)

(keryx:2487): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so) initialization check failed: Gtk+ version too old (micro mismatch)

(keryx:2487): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so) initialization check failed: Gtk+ version too old (micro mismatch)

(keryx:2487): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so) initialization check failed: Gtk+ version too old (micro mismatch)

(keryx:2487): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so) initialization check failed: Gtk+ version too old (micro mismatch)

(keryx:2487): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libequinox.so) initialization check failed: Gtk+ version too old (micro mismatch)

(keryx:2487): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so) initialization check failed: Gtk+ version too old (micro mismatch)

(keryx:2487): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libequinox.so) initialization check failed: Gtk+ version too old (micro mismatch)

(keryx:2487): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so) initialization check failed: Gtk+ version too old (micro mismatch)
Fontconfig warning: "/etc/fonts/conf.d/11-lcd-filter-lcddefault.conf", line 9: invalid constant used : lcddefault
Fontconfig warning: "/etc/fonts/conf.d/53-monospace-lcd-filter.conf", line 17: invalid constant used : lcdlegacy
wxWidgets interface loaded
./keryx: symbol lookup error: /usr/lib/gio/modules/libgiobamf.so: undefined symbol: g_desktop_app_info_launch_handler_get_type
```

however , when i cd in the source directory nd run
```
python keryx.py
```
it starts correctly..

is this how it is supposed to be or am i missing some dependencies???

---

### Post by EXCiD3 on 2010-07-06
Sorry I should have mentioned: We are having issues with the executable build scripts, so our Linux executable is only 32 bit, and doesn't always work. I've been using pyinstaller to build it, but it doesn't seem to work all too well. What we've done is included the GUI libraries inside of it so that you *should* be able to run that executable on any linux box, but it hasn't been working too well lately. If anyone knows of some good python executable builders for Linux send em my way. :) 

The source should run just fine as long as you've got wxPython installed. The current stable release is reasonably old but I'm working on a complete rewrite using GTK instead of wxWidgets which should be much more seamless and pretty on Ubuntu. And hopefully I'll be able to build the executables much better, but moving to GTK will mean that I don't even need to include that for Ubuntu. I will still have to do it for KDE users though, so they might run into some issues.

Then again, I'm still a noob and it's pretty much just me and one other developer working on it primarily so if anyone wants to help, feel free! :) I'm going to be extremely busy once school starts since it's my last year of uni. Let me know if you have any other problems and I'll see what I can do.

---

### Post by mahela007 on 2010-07-17
What you're doing is simply AWESOME!!!! As you can see, I'm from Sri lanka and being able to make Ubuntu a little more independent -particularly in the updating department-  of the net is certainly a step forward.
Best wishes... I'm downloading Keryx right now ;-)

---

### Post by EXCiD3 on 2010-07-17
> **mahela007 said:**
> What you're doing is simply AWESOME!!!! As you can see, I'm from Sri lanka and being able to make Ubuntu a little more independent -particularly in the updating department-  of the net is certainly a step forward.
Best wishes... I'm downloading Keryx right now ;-)

Good luck! Trying my best, the next version is shaping up pretty well. We are getting close to building the new interface and could use some feedback. If you get the chance, take a look at our ideas and let us know what you think. We are trying to make it look at lot more like Software Center so it will be easier to use. :)

[http://keryxproject.org/2010/07/keryx-1-0-interface-mockups/](http://keryxproject.org/2010/07/keryx-1-0-interface-mockups/)

---

### Post by Shining Arcanine on 2010-07-17
> **dixiedancer said:**
> **[COLOR="Blue"]Aptoncd[/COLOR]** allows you, once you have installed all the programs you want, to back up all those installed programs onto a CD. Then you can use them to install them to other computers (without downloading them separately on each machine). It's great for multiple 'puters and dial-up situations.

If you have several computers, it would probably be better to install a mirror of the official repositories on a local server. Corporate PCs running Microsoft Windows use Windows Server Update Services, which is a similar concept.

---

### Post by Stavro on 2010-07-21
Thanks for all the excellent replies. This thread has received more attention than I could have anticipated. I have been reading up on Linux Mint of late and I notice one of the new features specific to version 9 is a backup tool. Could this be the 'cute' little app that allows one to download programs and keep them for future use?

[http://www.linuxmint.com/rel_isadora_whatsnew.php#mintbackup](http://www.linuxmint.com/rel_isadora_whatsnew.php#mintbackup)

I'm the sort-of person that once I've found a 'gold' configuration I stick with it until something noticeably better comes along. This is the old good is good enough approach.

---

