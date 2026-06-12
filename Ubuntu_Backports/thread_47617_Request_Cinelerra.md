---
title: "Request: Cinelerra"
date: 2005-07-09
forum: Ubuntu Backports
---

### Post by ulisse on 2005-07-09
I know this one is hard, but it would be wonderful to have [Cinelerra](http://heroinewarrior.com/cinelerra.php3)  in BackPorts...

---

### Post by MetalMusicAddict on 2005-07-09
That looks nice. Ide love to try this out.

---

### Post by fsman on 2005-07-09
Actually it is very easy to download the RPM use alien and then dpkg -i

---

### Post by ossi on 2005-09-14
There is a ubuntu package source, but non official. Add to sources.list:

deb [http://bootlab.org/~j/packages/hoary/](http://bootlab.org/~j/packages/hoary/) ./

then update. after that it should work. This version is 1.2. I got no clue if there is a Ubuntu Hoary Package of the new 2.0 release. Got to search it and test it myself first. Has anybody got sources??

---

### Post by ulisse on 2005-09-16
Thanks ossi, it works ;-)

---

### Post by senectus on 2005-09-21
is there any reason why this isn't in the repository?
As far as I can tell it _is_ GPL.. so should fit in the guidelines...

---

### Post by mstrymn on 2005-09-21
I actually have a Ubuntu .deb for x86_64 architecture.  It's highly recommended that you use only 64 bit processors for Cinelerra because of stability issues with 32 bit processors with memory allocations over 512 mb.  

If you wanna make your own, open terminal and "sudo apt-get install alien", then go to [http://heroinewarrior.com/download.php3](http://heroinewarrior.com/download.php3) and download the appropriate RPM.  Find the folder with the RPM, open to terminal and "sudo alien cinelerra-2.0-1.WHATEVER.rpm -d" then from the resulting deb, you type "sudo dpkg -i cinelerra_2.0-2_WHATEVER.deb".

I would be happy to put the debs in the backport if someone would show me how.

Bryan

---

### Post by ossi on 2005-10-09
I had a look at the mailing list again and found the following post. There should be a Ubuntu Breezy Package. Havent tried that myself since I do wait for the stable verision of breezy:
[I]

Hi all,
A friend made an ubuntu breezy package:
[http://socrates.if.usp.br/~liquid/pacotes/](http://socrates.if.usp.br/~liquid/pacotes/)
but I think it should work in other ubuntu versions (btw, i never used ubun=
tu)[/I]

---

### Post by reuben on 2005-10-15
Hey, just adding my vote. It'd be great if this was officially supported - it's a flagship product of linux desktop.

---

### Post by Annagul on 2005-10-15
My vote for cinelerra too

---

### Post by reuben on 2005-10-15
OSSI - I couldn't get that to work -- I get this error on startup:

MWindow::init_theme: theme Blue Dot not found.

Ideas?

---

### Post by ossi on 2005-10-17
Which version? 2.0 oder 1.2? It would be great to have a ubuntu cinelerra package which would give the whole system a more multimedia touch.

---

### Post by Fed7 on 2005-10-17
another unufficial repository:  deb [http://www.kiberpipa.org/~gandalf/ubuntu/](http://www.kiberpipa.org/~gandalf/ubuntu/) ./ 

By

---

### Post by ossi on 2005-10-17
You can find the repository you posted through the Herroinewarrior homepage; but when i try to execute it I get "missing libopenexr2 (>= 1.2.1)". Still this is a Cinelerra 1.2.2 not 2.0. Anyobody got a 2.0 package??

---

### Post by stimulator on 2005-10-18
Hey Y'all,

My name is Franklin Lopez and I am a filmmaker and very new to this linux thing. I'v been using Final Cut Pro for years, but as an anti-authoritarian it only makes sense that I switch to Linux. So here I am with an old Vaio rocking Ubuntu. 

Anywho, I want to install cinelerra and give it a go before I make my next desktop purchase and give the finger to Apple and other corporate thugs.

So two questions:

1. Anywhere you can point me as the best tutorial on compiling/installing programs for someone who has no idea what y'all are talking about. 

2. What system would be the best to purchase to run Cinelerra.

thanks in advance and if you're bored you can check out my films here - [http://submediatv.com](http://submediatv.com)

I hope that someday soon I can put a 'Made with Linux' log on the credits

cheers//frank

---

### Post by ossi on 2005-10-19
Hy again!

Yesterday I managed to get Cinelerra 2.0 running on my Ubuntu Hoary. After a little bit of trying everything turned out to be quite easy. First, it is very important to uninstall ALL packages according to Cinelerra. I tried to install 1.2.2 over apt-get first, but that didnt work. So I uninstalled a library which is specific for Cinelerra (libquicktimehv, if i remember correctly) which uninstalled all the Cinelerrapackages I used before. 

After that, I got that package from [http://socrates.if.usp.br/~liquid/pacotes/]("http://socrates.if.usp.br/~liquid/pacotes/") (means I just downloaded the .deb called cinelerra and saved it on my system). Then I went to the directory I saved the Package in terminal and pressed ```
dpkg -i cinelerra.....
``` (press tab in order to get the right package). After that it should work. 

Dont be dissapointed when playback doesn't work at first. Switch to preferences in Cinelerra and have a look at the sound-server settings. Choose "ALSA and try a bit with the devices (right to it - Cinelerra may crash if you choose something wrong, but simply restart find your best settings). I couldnt manage to get it to use ESD which worked with the version before. So it will be difficult to hear sounds from other applications while you run Cinelerra in Hoary.

When editing, save your projects a lot, because Cinelerra is designed for high performance hardware, which most people (like me) cant afford. Anyway usually it works, but you dont want to lose the work you did in the last hour. 
Pleasa give feedback if it worked with you. greets

---

### Post by ossi on 2005-10-19
@stimulator:

Check out the [site ]("http://www.heroinewarrior.com"). There should be some informations about it. Don't be afraid about what stands there; I use Cinelerra on a Notebook with a Intel Centrino 2GHZ and a gigabyte of RAM and it works. However I edit only short movies (up to 15 mins). Generally seen, from what I can tell you with my experiences, Cinelerra is a good programm for editing high quality content. You can transform your movies then easily with mencoder. Where I see a problem with Cinelerra and commercial use is the usability. You got to know what you want and sometimes go into deep. You can't bug people all the time in Mailinglists and you don't know if you ever get an answer. So you really can't expect anything you work unless you made the experience it does.

Anyway, if I would be you, I would have a close look at it first and decide then. Talk to people who really use it commercial, if there are any. Do not waste your time with freaks in boards who waste there free-time. ;)

---

### Post by JuanC on 2005-10-19
Cinelerra has AMD64 ubuntu package?

---

### Post by reuben on 2005-10-19
OSSI - tried again exactly as you described; same problem :(

MWindow::init_theme: theme Blue Dot not found.


Any idea what this is talking about?

---

### Post by fsman on 2005-10-20
Looks like people are having problems installing cinelerra. Mine's working 100% on Breezy. Here is what I did.

Fresh install of Breezy then used 'easyubuntu' to upgrade codecs etc.

Synapitic to get Alien
Got the RPM for Athlon (i386) from [http://heroinewarrior.com/download.php3](http://heroinewarrior.com/download.php3)
then
sudo alien cinelerra_package_file.rpm
and finally
dpkg -i cinelerra_package_file.deb

hope this helps everyone.

---

### Post by binks on 2005-10-20
ok just to note i followed the alien route and installed the amd rpm onto an old ibm p2 and it works sweet:eek: 


so far lol not encoded in it yet as its gettin late and i aint staying at work l8


ps gonna install on me home pc tonite

---

### Post by stimulator on 2005-10-21
Cool and thanks for the reply. I am still having problems installing but slowly getting a hang of this Linux thing and doing things through the terminal. I really hope to get it to work, or that other video editing warez get developed. Apple has a tight grip on the Indy community and FInal Cut costs $1000. Shiiiiit.

But believe me I won't buy a new system until i try it out first...

cheers//frank
[http://submediatv.com](http://submediatv.com)

---

### Post by onesojourner on 2005-10-22
I would like to add my vote that this is officially supported too.

---

### Post by reuben on 2005-10-22
If you have the same problem I got (missing blue dot theme) delete:
~/.bcast/Cinelerra_rc

It happens if you had 1.2 installed previously,

---

### Post by ossi on 2005-10-23
Talking bout Backports it would be great to have the 1.2.2 version and the 2.0 version in the Backports. Is there any realistic chance there will be a Ubuntu package?? Does anybody know something?

And I found another thing on the web:

[http://www.jahshaka.org/]("http://www.jahshaka.org/")

Does anybody have any experiences with Jahshaka??

---

### Post by stimulator on 2005-10-25
Gosh, finally got that fucker istalled using the packages that Ossi posted ([http://socrates.if.usp.br/~liquid/pacotes/](http://socrates.if.usp.br/~liquid/pacotes/)) reading all the help messages on this thread (THANKS!) and chatting with a Linux geek.

So first impressions, it has everything I need for simple editing but it's thin on the effects, but not bad for an open source app.

I will give Jahaskta or whatever it's called a shot next.

Again, thanks for all the helpful posts.

cheers//the_stimulator
[http://submediatv.com](http://submediatv.com)

---

### Post by moopoo on 2005-10-27
I'd really love to have Cinelerra supported by Ubuntu, too.

---

### Post by jeep05 on 2005-10-31
yes it would be cool !

---

### Post by rsay on 2005-11-16
I agree that this is a hole in the ubuntu lineup that needs to be filled. Cinelerra isn't exactly Adobe premiere but I think it really is the most complete open source package. I was regularly using Cinelerra-cvs when I changed from Gentoo to Ubuntu Warty. I could never figure out how to get the video capture from firewire to work in cinelerra so I always used Kino for that.  I was just starting to get the hang of the interface when somebody told me about the great stuff that was happening with ubuntu. I really hope this gets added to the repositories soon.

---

### Post by JuanC on 2005-11-18
Another vote for Cinelerra. 
And also AMD64 packages for Cinelerra.

---

### Post by p_schott on 2005-11-18
One more.

---

### Post by jnuts on 2005-11-21
Another vote for Cinelerra in backports.

---

### Post by tikal26 on 2005-11-21
it looks like cineerala and jahshaka is in their list to do for draper
[https://wiki.ubuntu.com/MOTUMedia?highlight=%28motu%29%7C%28media%29](https://wiki.ubuntu.com/MOTUMedia?highlight=%28motu%29%7C%28media%29)

---

### Post by 4linux on 2005-11-23
[QUOTE=fsman]Looks like people are having problems installing cinelerra. Mine's working 100% on Breezy. Here is what I did.

Fresh install of Breezy then used 'easyubuntu' to upgrade codecs etc.

Synapitic to get Alien
Got the RPM for Athlon (i386) from [http://heroinewarrior.com/download.php3](http://heroinewarrior.com/download.php3)
then
sudo alien cinelerra_package_file.rpm
and finally
dpkg -i cinelerra_package_file.deb

hope this helps everyone.[/QUOTE]

Worked like a charm here, Thanks :mrgreen: 

-Pat

---

### Post by Jubal on 2005-11-28
[QUOTE=fsman]Looks like people are having problems installing cinelerra. Mine's working 100% on Breezy. Here is what I did.

Fresh install of Breezy then used 'easyubuntu' to upgrade codecs etc.

Synapitic to get Alien
Got the RPM for Athlon (i386) from [http://heroinewarrior.com/download.php3](http://heroinewarrior.com/download.php3)
then
sudo alien cinelerra_package_file.rpm
and finally
dpkg -i cinelerra_package_file.deb

hope this helps everyone.[/QUOTE]

I am also on a fresh install of breezy with an athlon I used easy ubuntu, downloaded the rpm, put in the code and the small black window just popped up for a milisecond both times.  The rpm I downloaded was actually cinelerra-2.0-1.i386.rpm so I tried

sudo alien cinelerra-2.0-1.i386.rpm

same results.  I am a complete newb, and this is the first none synaptic install I am trying to do.  Thanks

---

### Post by Yogarine on 2005-11-29
Okay, here's a installation guide for complete newbs. All it takes is typing 4 lines of text:
(Should work fine on Breezy)

Open up a terminal:
[Applications] => [Accessories] => [Terminal]

Inside the terminal you type the following lines, followed by [Enter] after each line. Enter your own password whenever it asks for one. Whenever it asks for some kind of confirmation, just press [Y].
```

sudo apt-get install alien
wget http://voxel.dl.sourceforge.net/sourceforge/heroines/cinelerra-2.0-1.i386.rpm
sudo alien cinelerra-2.0-1.i386.rpm
sudo dpkg -i cinelerra_2.0-2_i386.deb

```

DONE!!!

Now to run Cinelerra you can type 'cinelerra' in the terminal. You can also add a launcher to you panel and fill in 'cinelerra' as command.

Have fun!

---

### Post by Yogarine on 2005-11-29
Just figured that some people also might want an explanation of those 4 lines of code:

**sudo apt-get install alien**
Downloads and installs **Alien**, a tool for converting Red Hat RPM Packages (that Ubuntu doesn't know how to use) into Debian packages (wich Ubuntu can handle).
The **sudo** at the start is needed to perform this action with root (administrator) priveliges.

**wget [http://voxel.dl.sourceforge.net/sourceforge/heroines/cinelerra-2.0-1.i386.rpm](http://voxel.dl.sourceforge.net/sourceforge/heroines/cinelerra-2.0-1.i386.rpm)**
Downloads the Cinelerra RPM package.

**sudo alien cinelerra-2.0-1.i386.rpm**
Makes Alien convert the Cinelerra RPM package to a Debian package.

**sudo dpkg -i cinelerra_2.0-2_i386.deb**
Installs the just created Cinelerra Debian package...

---

### Post by Jubal on 2005-11-30
Here is what happens after sudo alien cinelerra-2.0-1.i386.rpm

```
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
        xargs -0 -r -i cp -a {} debian/cinelerra
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: could not find path for libXv.so.1
dpkg-shlibdeps: warning: could not find path for libXxf86vm.so.1
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path /usr/lib32/libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXext (soname 6, path /usr/lib32/libXext.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libXv.so.1)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXv (soname 1, path , dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libXxf86vm.so.1)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXxf86vm (soname 1, path , dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpng12 (soname 0, path /usr/lib32/libpng12.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libz (soname 1, path /usr/lib32/libz.so.1, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 6, path /usr/lib32/libstdc++.so.6, dependency field Depends)dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: cinelerra-2.0: No such file or directory

```

Not sure if I messed something up in previous trys.  I have no idea what any of this means.

---

### Post by moopoo on 2005-11-30
Great,

it works. Thanx Yogarine.

---

### Post by reuben on 2005-12-09
Try Main Actor...I ditzed with cinelerra for a while, but it is buggy as hell IMO. Main Actor is commercial software, but there is a free download version that watermarks all of your vids. Worth the download. (The deb installs no problem using dpkg -i; the installation ends up in /opt/MainActor)


[http://www.mainconcept.com/mainactor_info.html](http://www.mainconcept.com/mainactor_info.html)

---

### Post by daki on 2005-12-11
Jubal, you need the x86_64 version.  

Thanks to fsman for the tip, it works great.

---

### Post by naraku on 2006-01-09
I used gentoo, few months ago. Cinelerra is available in gentoo linux, but not available in ubuntu linux, this is not good. I can't using now. :(

I hope next version of ubuntu will release with cinelerra! ;)

---

### Post by mmcmonster on 2006-01-10
Somewhat off topic:

For those of us who don't have 64 bit CPUs, why the i386 as a target.  I know, it's the least common denominator, but if any app would benefit from recompilation, I would think this would be it. :-)

Would there be a performance benefit for a 686 target (pentium pro (?) & up), or is the gain too minimal even with this sort of app?

I'm not exactly a newbie, but fairly new to the game, and was wondering about this for a whlie...

---

### Post by rustbucketz on 2006-02-05
Is their support for my pentium 4 m 1.6ghz?

---

### Post by JureCuhalev on 2006-02-10
Here is another set of cinelerra ubuntu ports, built for pentium4, athlonxp and i686.

More details and installation instructions at: [http://www.kiberpipa.org/~gandalf/ubuntu/README](http://www.kiberpipa.org/~gandalf/ubuntu/README)

(I just uploaded svn20060209 builds)

---

### Post by falloutvictim on 2006-02-27
Has anyone gotten Cinelerra installed on a PPC?  I'm running ubuntu breezy badger on a G4 and keep getting a version error... 


COULD NOT MARK ALL PACKAGES FOR INSTALLATION OR UPGRADE:
The following packages have unresolvable dependencies.  Make sure all repositories are added and enabled in the preferences

cinelerra:
 Depends: libopenexr2 (>=1.2.2) but it is not installable


So, libopenexr2c2 is installed, and it is version 1.2.2, and it's obviously not the same as libopenexr2, but it's supposed to do the same thing.

Here's the list of repositories I added:
deb [http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian](http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian) /mplayer/
deb [http://garbure.org/debian/](http://garbure.org/debian/) ./
deb-src [http://garbure.org/debian/](http://garbure.org/debian/) ./
deb htt://www.kiberpipa.org/~gandalf/ubuntu/breezy/mjpegtools ./

These I found at a couple of different sites.  I'm doing this all through synaptic package manager.  Everything works up until the libopenexr2 error.

Anyone know?
Thanks,
Kim

---

### Post by JureCuhalev on 2006-02-28
Adding my repositories won't help yo with this problems since they are for i386 arch only currently.

---

### Post by ulisse on 2006-02-28
If you are sure that libopenexr2c2 does the same thing than libopenexr2, you could edit the .deb to work with that file... it's not hard but I don't know if it is safe.

- Download the .deb file on your disk

- Create a folder called cinelerra in the same folder where you save the .deb

- run this commands: 
dpkg-deb --extract *the_downloaded_file.deb* cinelerra
dpkg-deb --control *the_downloaded_file.deb* cinelerra/DEBIAN

- now edit the file called "control" that you'll find inside "cinelerra/DEBIAN/", find the word libopenexr2 and change to libopenexr2c2

- rebuild the package with:
dpkg --build cinelerra
(you will obtain a file called cinelerra.deb)

- install the file:
sudo dpkg -i cinelerra.deb

- eventually correct the dependecies with:
sudo apt-get -f install

I did it with Skype, and it worked.

---

### Post by yasenov on 2006-02-28
[QUOTE=naraku]I used gentoo, few months ago. Cinelerra is available in gentoo linux, but not available in ubuntu linux, this is not good. I can't using now. :(

I hope next version of ubuntu will release with cinelerra! ;)[/QUOTE]
why don't you try building from source or use alien and convert a .deb fail from .rpm(here will have the problem with dependencies).

---

### Post by falloutvictim on 2006-02-28
I'll try to be as exact as I can, in order to try to be helpful.

I'm running Ubuntu Breezy for PPC, G4.
Between synaptic and terminal I've done the following on my install for cinelerra:
In terminal I got the source for the cinelerra cvs from the command: deb-src [http://garbure.org/debian/](http://garbure.org/debian/) ./
I tried to configure but didn't get very far, 8 hours and about 100 dependencies later.... 
l manually configured and compiled openexr, libiec61883, x264-snapshot-20060227-2245 (it was the daily tar.gz), tried to manually install the tgz of the videodev2.h, but still haven't managed that, it will configure without it, but it may be causing problems with my compiling.
Using synaptic, I got at least 50 other dependencies corrected as they popped up during the config session.  Some of the more important ones were g77, libasound, libsndfile, libgcc1, lame, toolame, a52, fftw, uuid and fftw.  Make sure all the dev apps are loaded with EVERYTHING.  There's a devutil and a devtool that helped alot.  
So as it stands, cinelerra is configured with all the necessary libraries, but during $make I start to get errors when it hits the quicktime directory.
So if anyone has any ideas on the compile, feel free, and I will keep you updated if I ever get this working.

god I need booze

---

### Post by knatten on 2006-03-07
Check this out:
[http://cvs.cinelerra.org/getting_cinelerra.html#ubuntu](http://cvs.cinelerra.org/getting_cinelerra.html#ubuntu)
Works for me.

---

### Post by falloutvictim on 2006-03-21
[QUOTE=knatten]Check this out:
[http://cvs.cinelerra.org/getting_cinelerra.html#ubuntu](http://cvs.cinelerra.org/getting_cinelerra.html#ubuntu)
Works for me.[/QUOTE]


This worked for me too... but here's some pointers.  Don't add their repositories until everything is updated and you've managed to install as many dependencies as possible.  Some aren't updated as of this post, and caused alot of problems when I tried to reinstall after a horrible crash.  Once you've gotten the last of your dependencies installed and cinelerra, remove the repositories.  Make sure ffmpeg and mjpegtools ESPECIALLY are installed BEFORE adding the repositories.  
This list is incomplete, but... stuff to install BEFORE adding repositories would be:
ffmpeg
mjpegtools
faad
lame
fftw3
a52 something or other... if you search a52 in synaptic it'll give you the lib
firewire support (search 1394)
installing dvdauthor will install a couple of things that come in handy
libraw1394
libdv
openexr
theora
gcc
g77
faac

I'm sure there's more but that's all I can think of for now.
Have fun stormin'  the castle.

---

### Post by Statik on 2006-03-23
I've tried everything. I cannot seem to get it to work. Although I've followed the instructions, when I bring an mpeg clip into the viewer or compositor and hit play, it continues to play past the end, or if I hit stop. I cannot crop my video.

This is getting really frustrating. Are there any support resources for Cinelerra or KinoDV on ubuntu? I need the ability only to crop and x-fade.

Statik

---

### Post by anders_gud on 2006-03-23
[QUOTE=falloutvictim]
So if anyone has any ideas on the compile, feel free, and I will keep you updated if I ever get this working.

god I need booze[/QUOTE]

Managed to get Cinelerra (not from CVS, never got that to compile) up and running on Breezy PPC after much troubles. It's not worth the effort...
Unstable, unoptimized for PPC (libdv) and had severe endian issues (reversed colours).

Belive me, I've been trying to get DV editing to work on PPC and tried:
Pitivi (buggy, endian issues, slow gstreamer/libdv)
Diva (promising, but will not work on PPC due to gstreamer/libdv)
Lives (can work - but cumbersome)
Jahshaka (weird and very slow, endian issues)
Shotcut (just weird, endian issues)
Cinelerra (see above)
Kino (mostly works with ffmpeg but has a bug that distorts audio on PPC)

Forget about Cinelerra and the rest, use Blender ( [http://www.blender.org](http://www.blender.org) ). Recent builds include FFMPEG support that enables NLE Video/Audio. 

Workflow:
->Grab DV with dvgrab or kino.
->Edit movie with Blenders Sequence Editor, do color corrections, 3d effects, texts, audio mixing and render/encode to mpeg, DV or quicktime output...
->Use DVDStyler to burn DVD

Tutorial on Sequence Editor (Old but one of the few around)
[http://download.blender.org/document...tmlI/ch25.html](http://download.blender.org/document...tmlI/ch25.html)

Recent Blender 2.41 FFMPEG Build for Breezy PPC:
[http://www.gudmundson.se/anders/uplo....2_powerpc.deb](http://www.gudmundson.se/anders/uplo....2_powerpc.deb)
or binary in tar.gz:
[http://www.graphicall.org/builds/builds/showbuild.php?action=show&id=118](http://www.graphicall.org/builds/builds/showbuild.php?action=show&id=118)

Some of the effect plugins:
[http://www-users.cs.umn.edu/~mein/blender/plugins/sequence.html](http://www-users.cs.umn.edu/~mein/blender/plugins/sequence.html)

More on FFMPEG support in Blender:
[http://peter.schlaile.de/blender/sequencer/index.html](http://peter.schlaile.de/blender/sequencer/index.html)

---

### Post by falloutvictim on 2006-03-24
[QUOTE=anders_gud]

Forget about Cinelerra and the rest, use Blender ( [http://www.blender.org](http://www.blender.org) ). Recent builds include FFMPEG support that enables NLE Video/Audio. 

Workflow:
->Grab DV with dvgrab or kino.
->Edit movie with Blenders Sequence Editor, do color corrections, 3d effects, texts, audio mixing and render/encode to mpeg, DV or quicktime output...
->Use DVDStyler to burn DVD

][/QUOTE]

I can't get blender to open on my  machine, but it's here.... do I just need more memory?  I only have 512 now... I had to donate to a children's charity (basically mine so they'd get out of my room.. )
KAL

---

### Post by anders_gud on 2006-03-24
[QUOTE=falloutvictim]I can't get blender to open on my  machine, but it's here[/QUOTE]
Can you get any error messages?
open a terminal and type:
blender -d

Memory shouldn't be an issue. This is a cvs build - and I did not update the deps... Most likely you are missing some libs.

---

### Post by falloutvictim on 2006-03-24
[QUOTE=anders_gud]Can you get any error messages?
open a terminal and type:
blender -d

Memory shouldn't be an issue. This is a cvs build - and I did not update the deps... Most likely you are missing some libs.[/QUOTE]

Blender V 2.37
argv[0] = blender-bin
argv[1] = -d
Using Python version 2.4
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x30
Color depth r 8 g 8 b 8
Aux buffers: 0

Registering scripts in Blender menus ...

Getting menu data for scripts from file:
/home/kim/.blender/Bpymenus

Color depth r 8 g 8 b 8
Aux buffers: 0
Color depth r 8 g 8 b 8
Aux buffers: 0
/usr/bin/blender: line 46:  7493 Segmentation fault      blender-bin $@

This is what I get
btw, I can't import with Kino either.. I have to use DVGrab... I'm having all kinds of issues.

---

### Post by anders_gud on 2006-03-24
[QUOTE=falloutvictim]Blender V 2.37
argv[0] = blender-bin
argv[1] = -d
[/QUOTE]
This is the one in the repos (2.37), right?
[QUOTE=falloutvictim]
Using Python version 2.4
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x30
Color depth r 8 g 8 b 8
Aux buffers: 0

Registering scripts in Blender menus ...

Getting menu data for scripts from file:
/home/kim/.blender/Bpymenus

Color depth r 8 g 8 b 8
Aux buffers: 0
Color depth r 8 g 8 b 8
Aux buffers: 0
/usr/bin/blender: line 46:  7493 Segmentation fault      blender-bin $@
[/QUOTE]

I think there is a problem with your Xorg/dri setup.
What is your hardware setup?
Does any of your other opengl apps work?
What is the output from glxinfo?

There is a static version of Blender here:
[http://www.gudmundson.se/anders/uploads/blender-2.41-linux-glibc2.3.5-ppc-static.tar.gz](http://www.gudmundson.se/anders/uploads/blender-2.41-linux-glibc2.3.5-ppc-static.tar.gz)
just unpack and test...

---

### Post by falloutvictim on 2006-03-25
[QUOTE=anders_gud]This is the one in the repos (2.37), right?


I think there is a problem with your Xorg/dri setup.
What is your hardware setup?
Does any of your other opengl apps work?
What is the output from glxinfo?

[/QUOTE]

libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x30
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control,
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_video_sync,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: VA Linux Systems, Inc.
OpenGL renderer string: Mesa DRI Rage 128 Pro 20041026 AGP 1x
OpenGL version string: 1.2 Mesa 6.3.2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture,
    GL_ARB_texture_compression, GL_ARB_texture_env_add,
    GL_ARB_texture_mirrored_repeat, GL_ARB_transpose_matrix,
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture,
    GL_EXT_draw_range_elements, GL_EXT_histogram, GL_EXT_packed_pixels,
    GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_separate_specular_color, GL_EXT_subtexture, GL_EXT_texture,
    GL_EXT_texture3D, GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_object, GL_EXT_vertex_array, GL_APPLE_packed_pixels,
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat,
    GL_MESA_ycbcr_texture, GL_MESA_window_pos, GL_NV_blend_square,
    GL_NV_light_max_exponent, GL_NV_texgen_reflection, GL_OES_read_format,
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_generate_mipmap,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 Slow
0x25 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x26 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x27 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x28 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 Slow
0x29 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x2a 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x2b 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x2c 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 Slow
0x2d 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x2e 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x2f 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x30 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 Slow
0x31 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x32 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow


WHEW that's long... ok.. you know... I do have an ATI AGP graphics card.... 
I hadn't thought of that.... nothing is working actually, Kino won't work, DVDauthor crashes, my movie players run really slow and stupid.... I'm pretty sure I can find the ATI driver install guide.. if I don't still have it written down somewhere... do I need fglrx?  That's definitely not in here.  I do have the instructions.. I guess I could give it a shot and see if it helps, huh?  

Any other ideas?  YOu're O SO VERY HELPFUL!

---

### Post by falloutvictim on 2006-03-25
kim@mrspotatohead:~/Desktop/blender-2.41-linux-glibc2.3.5-ppc-static$ blender
Using Python version 2.4
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x30
/usr/bin/blender: line 46:  8367 Segmentation fault      blender-bin $@
kim@mrspotatohead:~/Desktop/blender-2.41-linux-glibc2.3.5-ppc-static$ blender
Using Python version 2.4
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x30
/usr/bin/blender: line 46:  8367 Segmentation fault      blender-bin $@


Here's what i get with the static Blender.

---

### Post by anders_gud on 2006-03-27
[QUOTE=falloutvictim]
OpenGL renderer string: Mesa DRI Rage 128 Pro 20041026 AGP 1x
OpenGL version string: 1.2 Mesa 6.3.2
[/QUOTE]
Rage 128.. Ouch! Then try to set a lower color depth in your xorg.conf:
DefaultDepth 16

---

### Post by falloutvictim on 2006-04-10
[QUOTE=anders_gud]Rage 128.. Ouch! Then try to set a lower color depth in your xorg.conf:
DefaultDepth 16[/QUOTE]


Didn't work.. Nothing works.  I'm so frustrated.  I don't know if I"m missing codecs or waht but I can't get any thing to play back in anything I have.  Totem won't play, Kino won't play (although Kino will give me pictures frame by really slow frame).  Blender still won't even open and I get the exact same message.  I can't get movies to play online.  I can't dvdauthor to burn a dvd.  I'm hosed.  I dn't even want to try Cinelerra anymore.
Does anyone have like a step by step guide to making a multimedia center on a G4 with ubuntu?  Something for people who are just dumb as bricks?

HELP!!!!
Thank you all for your time.

---

### Post by The Sisko on 2006-04-12
Here is how to compile Cinelerra 2.0 on Breezy to run over a AMD64 X2 (dual core):

Get ready by installing all the usual tools for compiling: gcc, make, libtool, autoconf, etc. .
Install also nasm, an assembler.  The binary packages for all of this are available through Adept or, if you prefer, apt-get.

Create a directory into your home directory where to put all the source packages needed.  We'll call it here dwnld.

Download the sources for yasm from:
[http://www.tortall.net/projects/yasm/wiki/Download](http://www.tortall.net/projects/yasm/wiki/Download)
Be sure to download version 0.40 as previous versions will not recognize some multimedia instructions.
De-compress the file.
Open a terminal and cd dwnld/yasm-0.4.0
Run: ./configure
Run: make
Run: sudo make install (you will have to enter your password)

Download the cinelerra sources from:
[http://heroinewarrior.com/download.php3](http://heroinewarrior.com/download.php3)
De-compress the file.
Look in the folder cinelerra-2.0/guicast for the file bcnewfolder.inc
Edit it by adding the following line below the line "class BC_NewFolder":  class BC_NewFolderThread
Now look in the same folder for a file called bcpopupmenu.inc
Edit it by adding the following line below the line "class BC_PopupMenu":  class BC_MenuPopup
Open a terminal and cd dwnld/cinelerra-2.0
Run: ./configure
Run: make
Run: sudo make install (you will have to enter your password)

If you get any message like "ld cannot find -lXYZ" install the developmet package for that library.

Enjoy it!

---

### Post by binks on 2006-04-14
FATAL: can't create i686/soundtest.o: No such file or directory
make[1]: *** [i686/soundtest.o] Error 1
make[1]: Leaving directory `/home/binks/Desktop/cinelerra-2.0'
make: *** [all] Error 2
  ooops so what did i do thats what i get when i try to make no error on ./configure

---

### Post by zx80 on 2006-06-05
There is an easier method to get cinelerra working on ubuntu:

[http://www1.apt-get.org/search.php?query=cinelerra](http://www1.apt-get.org/search.php?query=cinelerra)

backports for ubuntu/breezy but deb-src could work on others debian-based distro (Added 2006-04-23, last checked 2006-04-24) (Download as text)  - maintained by eric at lprod dot org
Packages: avidemux, cinelerra with lprod.org skin plugin, dvdstyler, ffmpeg, ksubtitle, mencoder, mplayer, synfigstudio, ktoons
Architectures: all, i386
deb [http://lprod.org/deb/breezy/](http://lprod.org/deb/breezy/) ./
deb-src [http://lprod.org/deb/breezy/](http://lprod.org/deb/breezy/) ./

Just add these 2 last lines to your sources.list, 
apt-get update && apt-get upgrade && apt-get install cinelerra

---

### Post by XerXeX on 2007-11-21
I would really love to get Cinelerra working but as things are right now I cannot even get Celtx to run. Im a total noob in linux but I fully support the linux community and would like our film projects to be made with linux only appz!

First things first, get Celtx to run, then Cinelerra, hopefully I wont have to use Final Draft, Final Cut, Adobe CS3 or Avid to be able to finish the projects!

Btw, is there any good compositing software in linux? Something like After Effects?

---

### Post by d90 on 2007-12-12
my vote too :D

---

### Post by lenooh on 2008-01-09
I have not read all the posts, so maybe someone already suggested this.

Here is an easy way to install cinelerra:
[http://www.kiberpipa.org/~gandalf/ubuntu/README](http://www.kiberpipa.org/~gandalf/ubuntu/README)

hope it helps.

---

### Post by holmes85 on 2008-03-13
my vote too for Hardy

---

