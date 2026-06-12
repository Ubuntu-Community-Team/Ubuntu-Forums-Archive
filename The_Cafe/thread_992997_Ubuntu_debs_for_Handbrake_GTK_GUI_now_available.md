---
title: "Ubuntu debs for Handbrake GTK GUI now available"
date: 2008-11-25
forum: The Cafe
---

### Post by vishzilla on 2008-11-25
[Handbrake]("http://handbrake.fr/") has released a new update 0.9.3. They have included ubuntu binaries for the GUI. Check it out!!!

---

### Post by notwen on 2008-11-25
Any idea if these debs will work on Hardy?  =]  Currently at work and unable to find out for myself.

---

### Post by bobbocanfly on 2008-11-25
> **notwen said:**
> Any idea if these debs will work on Hardy?  =]  Currently at work and unable to find out for myself.

They are working fine on Intrepid (encoding some stuff now and not having any problems with Handbrake itself) and I dont see any reason for it not to work on Hardy.

---

### Post by mageus on 2008-11-25
Apparently Handbrake depends on libxcb-render-util, which isn't in the standard repositories for Hardy.  Run 'ghb' from the command line to see the error.

---

### Post by zeronothing on 2008-11-26
I have to say, the new handbrake 0.9.3 is really good. I would usually use OGMRIP to rip my DVDs to Xvid. With the new handbrake I have less errors plus it seems to be much faster. If your a Intrepid user I highly recommend using it if you do any DVD ripping. Thanks Handbrake, here is the [[COLOR="Blue"]website[/COLOR]]("http://handbrake.fr/?article=download") to download the package.

---

### Post by Polygon on 2008-11-26
> **mageus said:**
> Apparently Handbrake depends on libxcb-render-util, which isn't in the standard repositories for Hardy.  Run 'ghb' from the command line to see the error.

it shouldent......cuase i have been compiling from source for and it works fine

---

### Post by mageus on 2008-11-26
> **Polygon said:**
> it shouldent......cuase i have been compiling from source for and it works fine

I was referring to the current precompiled binary .deb on Handbrake's website.

I prefer to use debs (or even better, repos) for software since they're easier to update.

Only reason I haven't switched to 8.10 is that the switch to HAL input kills my trackball functionality.

---

### Post by binbash on 2008-11-27
good news, i love handbrake

---

### Post by jdong on 2008-11-27
The new 0.9.3 release of Handbrake is pretty awesome -- it takes most file formats now as input. As far as generating H.264 content for portable devices like the AppleTV/iPod or PSP, IMO HandBrake is one of the best tools for the job. The predefined profiles are very reasonable and shouldn't require much user tweaking.

---

### Post by chessboxing on 2008-11-28
> **mageus said:**
> Apparently Handbrake depends on libxcb-render-util, which isn't in the standard repositories for Hardy.  Run 'ghb' from the command line to see the error.

I came a cross the same issue. Anyone knows how to solve this. I tried to install in the synaptics to install something very a like.

---

### Post by jdong on 2008-11-28
Hardy and Intrepid are not ABI compatible. You must compile HandBrake on Hardy if you'd like to use it on Hardy.

---

### Post by bruce89 on 2008-11-28
I could put this in my PPA, but not just now.

> **jdong said:**
> >  Originally Posted by WebCore/platform/graphics/win/SimpleFontDataCGWin.cpp
m_allowFontSmoothing = (nameStr != "Ahem");
Good job, WebKit. Way to pass that Acid3. 

That hack is no longer there, and it was only for the Windows CoreGraphics port.

---

### Post by jdong on 2008-11-28
Ubuntu packaging welcome for HandBrake -- someone was working on it for Jaunty but work seems to have stalled. The buildsystem is a bit weird in that by default it heads out and wgets all the libraries it needs, which won't work on the buildd's.

---

### Post by bruce89 on 2008-11-28
> **jdong said:**
> Ubuntu packaging welcome for HandBrake -- someone was working on it for Jaunty but work seems to have stalled. The buildsystem is a bit weird in that by default it heads out and wgets all the libraries it needs, which won't work on the buildd's.

It's interesting to note that upstream don't release their (questionable) Debian packaging under the same licence.

The "debs'" binaries are awfy big for some reason, but they are not statically linked.

---

### Post by jdong on 2008-11-28
> **bruce89 said:**
> It's interesting to note that upstream don't release their (questionable) Debian packaging under the same licence.

Inspecting the contents a bit, it's pretty clear that it's almost next to useless even if released. [http://revu.ubuntuwire.com/details.py?package=handbrake](http://revu.ubuntuwire.com/details.py?package=handbrake)

That guy has been working on the previous version of HandBrake packaging; I spoke with him yesterday and he said that he was interested in continuing the attempt to get 0.9.3 in, too. It should be relatively close to the point that we can generate valid PPA packages from his work, but at the same time I feel we're pretty far away from it being in the repositories (there seems to be some licensing issues in the upstream tarball, too, not to mention debian/copyright will be a pain in the NECK to write for all the stuff it bundles)

---

### Post by bruce89 on 2008-11-28
Ouch, it downloads tarballs of most of the libraries it uses and applies patches to them. That's why the binaries are so big.

To be honest, I can see why they don't use the GNU build system, but this really is a bit far (obviously it's a Mac-oriented program).

---

### Post by bobbocanfly on 2008-11-28
> **bruce89 said:**
> Ouch, it downloads tarballs of most of the libraries it uses and applies patches to them.

In that case It'll be pretty hard to get that into the official Ubuntu repos. I seriously do not envy whoever tries to write the debian/copyright for this.

---

### Post by jdong on 2008-11-28
Looking at the patches they might have some reason why they pick these specific versions of their dependency stack and statically link against everything, but (insert explicatives here) this is going to make it REALLY difficult to slip past the archive admins, etc. And yeah, debian/copyright will make everyone cry.

---

### Post by Polygon on 2008-11-28
> **bruce89 said:**
> It's interesting to note that upstream don't release their (questionable) Debian packaging under the same licence.

The "debs'" binaries are awfy big for some reason, but they are not statically linked.

most likely cause its designed to be compiled on mac/linux and windows

im sure you guys could go to their irc channel and have a chat with them about any questions you have about their build system....

---

### Post by jdong on 2008-11-28
> **bruce89 said:**
> 
The "debs'" binaries are awfy big for some reason, but they are not statically linked.

Why do you think they are not statically linked? From the build system I'm fairly certain it statically links against all of the media libraries and even its own libhb.a

---

### Post by bruce89 on 2008-11-28
> **jdong said:**
> Why do you think they are not statically linked? From the build system I'm fairly certain it statically links against all of the media libraries and even its own libhb.a

It is dynamically linked to common libraries (X, etc, I checked with ldd), but statically linked to less common ones (X264, Theora, Vorbis etc.).

---

### Post by jdong on 2008-11-28
> **bruce89 said:**
> It is dynamically linked to common libraries (X, etc, I checked with ldd), but statically linked to less common ones (X264, Theora, Vorbis etc.).

Yeah, you are correct there -- it's an Anjuta default project which links against the GUI and HAL libraries dynamically but links against its libhb.a statically

---

### Post by jdong on 2008-11-28
Ok, I've got a hackage (hacked up package) that builds in pbuilder for Intrepid (produces ghb and HandBrakeCLI). If anyone is interested, I can attempt to build some Hardy packages for i386 or amd64, too.

The packaging is awful in that it is a quick and dirty dh_make job, so it probably adheres to next to none of the debian policies, lintian has a field day with boilerplates and invalid licenses. But, the resulting deb should work fairly well. A quick dpkg inspection shows that it's fairly reasonably packaged.

---

### Post by bobbocanfly on 2008-11-28
> **jdong said:**
> Ok, I've got a hackage (hacked up package) that builds in pbuilder for Intrepid (produces ghb and HandBrakeCLI). If anyone is interested, I can attempt to build some Hardy packages for i386 or amd64, too.

The packaging is awful in that it is a quick and dirty dh_make job, so it probably adheres to next to none of the debian policies, lintian has a field day with boilerplates and invalid licenses. But, the resulting deb should work fairly well. A quick dpkg inspection shows that it's fairly reasonably packaged.

Stick it up in a PPA? I've got a pile of time tonight, so I can have an attempt at cleaning it up tonight if you would like? (Can you grab source packages from PPAs?).

---

### Post by bruce89 on 2008-11-28
> **bobbocanfly said:**
> (Can you grab source packages from PPAs?).

Yes, it's under a wee context triangle.

---

### Post by JohnAStebbins on 2008-11-28
Howdy all,

I'm the developer of the new gtk gui for handbrake and made the packages that are currently available.  Since this is the first time I've made deb's, I'm certain there is plenty wrong with them.  I'm interested in fixing that and welcome any help you would like to give in doing that.

As some have pointed out, the build system is unconventional.  Lots of good reasons for that and some that aren't so good.  But changing the build system is a slow process because every little change seems to break someone. So it's done cautiously.

The libraries under the contrib directory are all statically linked to the binary.  We use versions of several libraries that are not available in any distribution, and apply patches to several others, so using the dynamic system libs just isn't feasible.  You would be missing lots of nice features if we attempted to do this.

Also, as someone pointed out, we do most of our communication on irc.  irc.freenode.net #handbrake & #handbrake-dev. So if you have ideas, you can find me there often.

---

### Post by jdong on 2008-11-28
> **JohnAStebbins said:**
> Howdy all,

I'm the developer of the new gtk gui for handbrake and made the packages that are currently available.  Since this is the first time I've made deb's, I'm certain there is plenty wrong with them.  I'm interested in fixing that and welcome any help you would like to give in doing that.


Hi, welcome to UbuntuForums -- it's a pleasure to have you here. I love the work that you and the rest of your team does -- HandBrake has always been my favorite DVD ripping tool and now it's hands-down my favorite general transcoding tool too.

I'm interested in good packaging for HandBrake, too -- it's such a valuable tool it would be idea if we can bring it to the multiverse repository for Jaunty and even backport it to Intrepid and Hardy.

As far as your deb packages, they don't seem too bad, at least the final output looks safe to install and use. However, for a major distribution with 20,000+ packages, we must have a packaging convention/policy that everything abides by, which can appear tough or cumbersome at times, but is a necessity to prevent the repositories from becoming a big mess. In addition, since we would have to distribute your software on our mirror network, care has to be taken to make sure that everything is consistently licensed and those distribution terms are properly documented.

> 
As some have pointed out, the build system is unconventional.  Lots of good reasons for that and some that aren't so good.  But changing the build system is a slow process because every little change seems to break someone. So it's done cautiously.


Completely understood -- I have some experience working with some of the underlying libraries you use in HandBrake and I can completely sympathize and agree with some of your reasons for wanting to do things this way. I am personally not interested in having Ubuntu rip out the build system and build against system libraries, and I will fight to the death to preserve the upstream build system relatively intact as much as is possible for us to distribute.


Currently, my attempts at packaging HandBrake results in HandBrakeCLI and ghb building on i386 and amd64 for Intrepid and Hardy. I'm working on cleaning up the packaging a bit to look somewhat less embarassing. The immediate roadmap for me looks like:

(1) Cleaning up boilerplates and obvious lintian violations, then posting these source packages and some amd64/i386 debs onto my personal hosting space.

(2) Properly documenting the license of all bundled components in debian/copyright, then uploading the source package to a PPA. I really don't want to shove things in a PPA until I'm sure that the licensing is okay.

(3) That, of course, will fail to build because the PPAs do not have internet access. I will then repack the source, including all the upstream contrib sources so that they can be used without fetching.

(4) At this point, I will look at integrating this work in Ubuntu if possible.


At step #4, I already anticipate some bickering from other developers and archive administrators about the bundled-library setup. I will try to make a convincing argument why this is necessary. This is where **I could use some upstream help** -- if you have specific examples about customizations or specific versions of your bundled libraries that Handbrake requires, it'd be helpful to know. At a cursory glance I already see that HandBrake derives its libmp4v2 differently from Ubuntu, and applies some pretty specific patches to its various encoders.

---

### Post by bruce89 on 2008-11-28
> **JohnAStebbins said:**
> The libraries under the contrib directory are all statically linked to the binary.  We use versions of several libraries that are not available in any distribution, and apply patches to several others, so using the dynamic system libs just isn't feasible.  You would be missing lots of nice features if we attempted to do this.


It sounds as if the libraries are

[LIST]
[*]liba52
[*]libfaad
[*]libavcodec
[*]libavutil
[*]libdvdcss
[*]libdca
[*]libdvdread
[*]libfaac
[*]libmp3lame
[*]libmp4v2
[*]libmkv
[*]libmpeg2
[*]libogg
[*]libsamplerate
[*]libvorbis
[*]libvorbisenc
[*]libtheora
[*]libx264
[*]libxvidcore
[*]zlib
[*]bzip2
[/LIST]

Apart from a few libraries which I've never heard of (libdca), these are all pretty common.

Using GStreamer would be an interesting cross-platform(?) solution.

---

### Post by jdong on 2008-11-28
Most of the libraries you mentioned have highly volatile APIs and ABIs not to mention they are fast-moving project and svn snapshots even a month off can behave drastically differently. There' still reasons why upstream may want to bundle a very specific version.

---

### Post by bruce89 on 2008-11-28
> **jdong said:**
> Most of the libraries you mentioned have highly volatile APIs and ABIs not to mention they are fast-moving project and svn snapshots even a month off can behave drastically differently. There' still reasons why upstream may want to bundle a very specific version.

True enough, and that would be another reason to use some kind of layer such as GStreamer. Of course, this would take ages to change.

---

### Post by JohnAStebbins on 2008-11-28
jdong, is there something specific I can do to help you out. When I prepare the package, I use a script to pre-download all the contrib packages. So they are in the source tar that get generated.  Basically my steps are:
- get the contribs
- update debian files
- autogen.sh in the gtk directory
- dpkg-buildpackage -rfakeroot

My debian directory was initially set up with 
dh_make --createorig

I'm glad to share anything that would be useful to you.

---

### Post by jdong on 2008-11-28
The script to get the contribs would be very helpful!

---

### Post by JohnAStebbins on 2008-11-28
jdong, here you go.

---

### Post by jdong on 2008-11-28
> **JohnAStebbins said:**
> jdong, here you go.

Very nice, thanks!

With this much I think by the end of the night I can get some PPA packages going.

---

### Post by JohnAStebbins on 2008-11-28
jdong,

Here's a run down of the contrib library situation in handbrake that
I hope will help you. 

One of the points to recognize it that substituting a supposedly 
compatible version of a library can cause user support issues for
us if there is some unexpected problem.  Static linking these
quickly evolving libraries gives us predictable results.

a52dec - 0.7.4
	patch to allow downmix to dolby prologic ii

faad2 2.6.1
	patch to configure.ac so it will build with libtool 2.2.x

ffmpeg svn 15462
	patch for building on beos
	patch that adds aac-latm codec
	patch fixes memory leak provoked by h264 streams with lots of errors
	patch for cygwin
	patch for solaris

libdca svn 81
	newer than released version

libdvdread 0.9.7
	patch for os x, changes path to dvdcss
	patch for cygwin, configure fixes

faac
	patch for cygwin configure

lame version 3.98

libmp4v2 svn 45
	project was stagnant.  using a fork that has picked up development

libmkv 0.6.3

mpeg2dec 0.5.1

libogg 1.1.3

libsamplerate 0.1.4

libvorbis aotuv fork b5

libtheora 1.0

libx264 git 1028
	patch for cygwin configure
	patch for solaris build scripts
	patch to allow forcing an IDR frame

xvidcore 1.1.3
	patch for os x configure
	patch for cygwin configure
	patch configure to recognize nasm 2.0

---

### Post by jdong on 2008-11-28
Thanks so much for that information!

---

### Post by jdong on 2008-11-29
Ugh I'm tired today, initial debianization attempt at [http://jdong.mit.edu/~jdong/handbrake/](http://jdong.mit.edu/~jdong/handbrake/)


This should build proper handbrake debs that include the CLI and ghb. I've confirmed the build to work on Hardy and Intrepid, but for Hardy you need to first backport yasm from intrepid or x264 will fail to build.


Tomorrow I'll pick up work on including the getlibs.sh script's bundled libraries and repack the orig.tar.gz. At that point, we will be able to generate PPA packages.


**EDIT**: Obviously I'm an insomniac:

I repacked and created a Launchpad PPA: [https://edge.launchpad.net/~handbrake-ubuntu/+archive](https://edge.launchpad.net/~handbrake-ubuntu/+archive)


Shoved Hardy and Intrepid build jobs in there.

I also registered HandBrake on Launchpad in order to store packaging in bzr: [https://edge.launchpad.net/handbrake](https://edge.launchpad.net/handbrake)

I really had no interest of controlling either project or team on launchpad. Particularly for the HandBrake project, the author/team is welcome to register themselves on Launchpad and I'll turn over project ownership.

As the changelog on the initial project states, there is some debian/copyright work that needs to be done (understatement of the day) as well as splitting of the GUI and CLI.

**EDIT2**: Ok *NOW* I'm seriously going to bed, but I'd like to warn that I haven't tried these PPA packages yet (i.e. they're still building now). Please test with caution until I get a chance to try em out!

---

### Post by jdong on 2008-11-29
UPDATE: Still can't sleep :)

I was able to confirm that the amd64 and i386 packages for Hardy in the PPA work.

---

### Post by jdong on 2008-12-01
Ok, the packages in the PPA are now split into handbrake-cli, handbrake-gtk, and handbrake-common, representing the command-line, graphical, and common packages.


Left on my TODO list still:

(1) debian/copyright
(2) manpages



I am happy to say that at this point, we do have functional Hardy and Intrepid packages for HandBrake that are building inside a buildd :)

---

### Post by ghindo on 2008-12-01
Kudos on the work you're doing on this project, jdong.  I'm eager to see where this leads for Debian, Ubuntu, and Handbrake.

---

### Post by maino82 on 2008-12-05
For those building from source on Hardy, x264 will fail to compile as others have mentioned. To get around this, install yasm 0.7.2 from source as follows (taken from [here]("http://ubuntuforums.org/showthread.php?t=786095"))

```
cd ~/
wget http://www.tortall.net/projects/yasm/releases/yasm-0.7.2.tar.gz
tar xzvf yasm-0.7.2.tar.gz
cd yasm-0.7.2
./configure
make
sudo checkinstall
```

For this to work you'll need build-essential, checkinstall, etc. etc (see link above)

After that I would recommend installing from svn as described [here]("http://trac.handbrake.fr/wiki/CompileGuide"). After you install the cli handbrake, go into the gtk directory and follow the readme instructions to build the gui and you're good to go! I know this isn't as user friendly as the folks who have graciously been trying to put together deb files (many thanks by the way), but if you like to have the latest and greatest updates, svn is the way to go and it's dead simple to upgrade later!

---

### Post by PhoenixMaster00 on 2008-12-05
Good news because i loved Handbrake on my OSX its such a simple an effective tool.

---

### Post by jdong on 2008-12-06
The PPA I linked to above has properly built Hardy packages. **DO NOT checkinstall yasm packages** unless you want to risk upgrade breakages. Doing so is entirely unsupported.

Use the PPA above, or if you want to build yourself, use prevu or pbuilder to properly backport the Intrepid yasm package, as was done for the PPA.

---

### Post by MikeTheC on 2008-12-06
I've been using Handbrake on my Macs for a while now, and it is good to see both the feature improvements it's made, as well as a full-on port to Linux (which means I can now run this on the fastest box in my house! yay!)

---

### Post by ecfitzgerald on 2008-12-06
Has anyone had any luck getting the ai64 version to work in Kubuntu 8.10?   I have other GTK apps working but handbrake gets a bouncing icon for 30 seconds, then 30 seconds of existing in the task bar then it dissappears from there too.  I have tried both the Handbbrake deb and the one Jdong has made.

---

### Post by jdong on 2008-12-06
> **ecfitzgerald said:**
> Has anyone had any luck getting the ai64 version to work in Kubuntu 8.10?   I have other GTK apps working but handbrake gets a bouncing icon for 30 seconds, then 30 seconds of existing in the task bar then it dissappears from there too.  I have tried both the Handbbrake deb and the one Jdong has made.

What architecture are you using? I've only built HandBrake for i386, amd64, and LPIA.

---

### Post by notwen on 2008-12-06
> **jdong said:**
> Ok, the packages in the PPA are now split into handbrake-cli, handbrake-gtk, and handbrake-common, representing the command-line, graphical, and common packages.


Left on my TODO list still:

(1) debian/copyright
(2) manpages



I am happy to say that at this point, we do have functional Hardy and Intrepid packages for HandBrake that are building inside a buildd :)

Thanks jdong for your effort in getting this into the repos and going through all the necessary procedures to do so.  Handbrake is a fantastic tool and w/ a working gui to boot now.  =]

---

### Post by ecfitzgerald on 2008-12-06
> **jdong said:**
> What architecture are you using? I've only built HandBrake for i386, amd64, and LPIA.

I have a AMD64.

---

### Post by wd5gnr on 2008-12-06
Thanks for the deb JDong. I have an AMD64 box (Heron) and when I start I get a long delay. Then this message. Then it finally starts and at least at a glance is working:

(ghb:4095) Warning: seems that HAL is not running: Did not receive a reply.

Anyone else seeing that or is it just me?

Odd. I guess HAL was not running. /etc/init.d/hal restart  and the problem went away. Hmm....

---

### Post by ecfitzgerald on 2008-12-06
> **ecfitzgerald said:**
> I have a AMD64.

I just tried it on another computer, with Kubuntu.  It has i386 installed, the behavior is the same. 
The other computer has i386 Kubuntu installed, but the processor is AMD64 also.

I tried restarting HAL too, no luck.

---

### Post by jdong on 2008-12-06
Can you run **ghb** on a Konsole and see if any errors display? I've not tried HandBrake in Kubuntu yet.

---

### Post by wd5gnr on 2008-12-06
I just ripped a movie on a Hardy Kubuntu AMD64 box. Once I restarted the HAL (see above) I had no problems.

---

### Post by ecfitzgerald on 2008-12-06
> **jdong said:**
> Can you run **ghb** on a Konsole and see if any errors display? I've not tried HandBrake in Kubuntu yet.

I get
ghb: error while loading shared libraries: libgtkhtml-3.14.so.19: cannot open shared object file: No such file or directory

---

### Post by wd5gnr on 2008-12-06
Just install the lib from your package manager. There were two I had to install including that one.

---

### Post by jdong on 2008-12-06
> **ecfitzgerald said:**
> I get
ghb: error while loading shared libraries: libgtkhtml-3.14.so.19: cannot open shared object file: No such file or directory

Can you run **apt-cache show handbrake-gtk** and paste the output here for me?


i'm interested in getting to the bottom of these errors because in theory they shouldn't happen.... For example, from the deb I just downloaded from my PPA:

> 
Package: handbrake-gtk
Source: handbrake
Version: **0.9.3+repack1-0ubuntu0~8.10jdong2**
Architecture: amd64
Maintainer: John Dong <jdong@ubuntu.com>
Installed-Size: 12428
Depends: libart-2.0-2 (>= 2.3.18), libatk1.0-0 (>= 1.20.0), libbonobo2-0 (>= 2.15.0), libbonoboui2-0 (>= 2.15.1), libbz2-1.0, libc6 (>= 2.7), libcairo2 (>= 1.2.4), libdbus-1-3 (>= 1.0.2), libenchant1c2a, libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.3.5), libgcc1 (>= 1:4.1.1), libgconf2-4 (>= 2.13.5), libglade2-0 (>= 1:2.6.1), libglib2.0-0 (>= 2.16.0), libgnome2-0 (>= 2.17.3), libgnomecanvas2-0 (>= 2.11.1), libgnomeui-0 (>= 2.22.0), libgnomevfs2-0 (>= 1:2.17.90), libgtk2.0-0 (>= 2.14.1), **libgtkhtml3.14-19 (>= 3.24.1.1)**, libhal-storage1 (>= 0.5.8.1), libhal1 (>= 0.5.8.1), libice6 (>= 1:1.0.0), liborbit2 (>= 1:2.14.10), libpango1.0-0 (>= 1.21.6), libpixman-1-0, libpng12-0 (>= 1.2.13-4), libpopt0 (>= 1.14), libsm6, libstdc++6 (>= 4.1.1), libx11-6, libxcb-render-util0, libxcb-render0, libxcb1, libxml2 (>= 2.6.27), libxrender1, zlib1g (>= 1:1.1.4), handbrake-common


It should be pulling in as a dependency.

---

### Post by ecfitzgerald on 2008-12-06
> **jdong said:**
> Can you run **apt-cache show handbrake-gtk** and paste the output here for me?


i'm interested in getting to the bottom of these errors because in theory they shouldn't happen.... For example, from the deb I just downloaded from my PPA:



It should be pulling in as a dependency.

I get
W: Unable to locate package handbrake-gtk
E: No packages found

For the debs you made I only ran the one that didn't say common, cli or gui.

BTW, thanks for the support!!

---

### Post by wd5gnr on 2008-12-06
For the record, I had installed the deb off the handbrake site and ran into two missing libs (including the one mentioned above) and installed them. Then I ran into one that wasn't in the repositories so I came here and found this thread. So I uninstalled the original deb and installed jdong's. And then I had no problem. So it could be that what I did masked one or two missing libs or not -- hard to tell.

---

### Post by jdong on 2008-12-06
> **ecfitzgerald said:**
> I get
W: Unable to locate package handbrake-gtk
E: No packages found

For the debs you made I only ran the one that didn't say common, cli or gui.

BTW, thanks for the support!!

I'd strongly recommend updating to the latest version in the PPA by adding the source line **deb [http://ppa.launchpad.net/handbrake-ubuntu/ubuntu](http://ppa.launchpad.net/handbrake-ubuntu/ubuntu) intrepid main** to your sources, and using your favorite package manager to install the **handbrake-gtk** package, which will smoothly update to this version. I'm not sure why the version of the deb you got didn't pull in gtkhtml correctly :(

---

### Post by ecfitzgerald on 2008-12-06
> **jdong said:**
> I'd strongly recommend updating to the latest version in the PPA by adding the source line **deb [http://ppa.launchpad.net/handbrake-ubuntu/ubuntu](http://ppa.launchpad.net/handbrake-ubuntu/ubuntu) intrepid main** to your sources, and using your favorite package manager to install the **handbrake-gtk** package, which will smoothly update to this version. I'm not sure why the version of the deb you got didn't pull in gtkhtml correctly :(

YAY! That worked, though Kubuntu's package manager didn't see it, running apt-get from the command line did work, and the app starts up now.

---

### Post by jdong on 2008-12-06
Glad to hear it worked for you! Although I can't officially say it in the packages, having libdvdcss2 installed gives you DVD decrypting abilities too, as with every other DVD-capable software on Ubuntu!

---

### Post by robertlankford on 2008-12-06
I'm late to the party with this comment.  Just downloaded Handbrake.  It's awesome!  Kudos to the developers on this.  It just replace K9copy/avidemux for me.

I'm stoked ... can you tell!?

---

### Post by The Belgain on 2008-12-07
Good stuff - I was going to try and package this but looks like there's no need now.  Are you still planning on submitting this for inclusion in multiverse ahead of 9.04?

One thing which seems a little surprising is that libhb is statically linked into the CLI and GTK programs.  Obviously this is a handbrake question rather than a packaging question as such, but is there a good reason why the libhb version isn't installed as a system library and dynamically linked to by the CLI anad GTK versions?  Does this make the OS X or Windows versions easier to set up or something?

---

### Post by jdong on 2008-12-07
> **The Belgain said:**
> Good stuff - I was going to try and package this but looks like there's no need now.  Are you still planning on submitting this for inclusion in multiverse ahead of 9.04?


Yes, I do plan on doing so but the packaging is not ready. debian/copyright right now details less than half of the licensing of all the codecs and contributed libraries that are bundled, and after that I need to write a get-orig-source line that repacks upstream tarballs with the contrib/ libraries. Finally, I need to write manpages for the binaries being installed. Only then do we have any chance of inclusion.

> 
One thing which seems a little surprising is that libhb is statically linked into the CLI and GTK programs.  Obviously this is a handbrake question rather than a packaging question as such, but is there a good reason why the libhb version isn't installed as a system library and dynamically linked to by the CLI anad GTK versions?  Does this make the OS X or Windows versions easier to set up or something?

That's something that upstream decided to do, and yeah, I bet it's for the OS X version so they can just ship a single file (HandBrakeCLI). Since so far only ghb and HandBrakeCLI use libhb, and libhb.a is less than 400k, I'm not going to cry too much about this anyway. I'd rather leave this as close to upstream as possible, so for now I simply don't see the benefit of separating out libhandbrake.

---

### Post by The Belgain on 2008-12-07
> **jdong said:**
> That's something that upstream decided to do, and yeah, I bet it's for the OS X version so they can just ship a single file (HandBrakeCLI). Since so far only ghb and HandBrakeCLI use libhb, and libhb.a is less than 400k, I'm not going to cry too much about this anyway. I'd rather leave this as close to upstream as possible, so for now I simply don't see the benefit of separating out libhandbrake.

Having a quick look at the source, it looks like the makefile in the libhb directory does have a shared library target (libhb.so) for libhb as well as a static target (libhb.a) - this used by default from the CLI and GTK makefiles though.

I guess it doesn't really matter if the library is only 400k big, but that's surprising as I'd assumed all the contrib libraries (ffmpeg, etc) got statically linked into libhb.  Is that not the case?

---

### Post by jdong on 2008-12-07
> **The Belgain said:**
> 
I guess it doesn't really matter if the library is only 400k big, but that's surprising as I'd assumed all the contrib libraries (ffmpeg, etc) got statically linked into libhb.  Is that not the case?

Nope, libhb references all the contrib libraries, but it's eventually HandBrakeCLI and ghb's link-phase that pulls in all the contrib libraries and libhb, so the main binaries take the hit whether or not libhb is dynamic.

---

### Post by NewJack on 2008-12-07
Just wanted to say thanks to the Devs and to JDong for their work!

---

### Post by jdong on 2008-12-08
I'm glad to be able to help, and bring this great piece of software to more users, more easily.

I've been hanging out around the HandBrake IRC channels and the developers are reacting very positively to well-built Ubuntu packages and we plan on switching the handbrake.fr packages to these ones fairly soon.

---

### Post by The Belgain on 2008-12-10
I've installed your the handbrake-gtk package from your PPA in Hardy and it seems to install fine (program loads up, but I haven't had time to try an encode yet) - thanks for the good work.

FYI the "handbrake" binary package is still present in your PPA - it might be worth removing it to avoid confusion (as it's now deprecated and replaced by -common/-cli/-gtk)?

Also, the menu item for the Handbrake GUI doesn't have an icon at the moment.

---

### Post by jdong on 2008-12-10
> **The Belgain said:**
> I've installed your the handbrake-gtk package from your PPA in Hardy and it seems to install fine (program loads up, but I haven't had time to try an encode yet) - thanks for the good work.

FYI the "handbrake" binary package is still present in your PPA - it might be worth removing it to avoid confusion (as it's now deprecated and replaced by -common/-cli/-gtk)?

Also, the menu item for the Handbrake GUI doesn't have an icon at the moment.

I shoved the delete button on the old handbrake packages; I will also investigate the menu issue soon-ish.

---

### Post by JohnAStebbins on 2008-12-10
jdong, did you remember to update the icon cache during postinst.  I did this:

```

case "$1" in
    configure)
    touch --no-create %/usr/share/icons/hicolor
    if [ -x /usr/bin/gtk-update-icon-cache ]; then
        gtk-update-icon-cache -q /usr/share/icons/hicolor
    fi
    ;;

```

---

### Post by jdong on 2008-12-10
> **JohnAStebbins said:**
> jdong, did you remember to update the icon cache during postinst.  I did this:

```

case "$1" in
    configure)
    touch --no-create %/usr/share/icons/hicolor
    if [ -x /usr/bin/gtk-update-icon-cache ]; then
        gtk-update-icon-cache -q /usr/share/icons/hicolor
    fi
    ;;

```

Aha, **dh_icons**. Appologies, my idiocy. I will respin some packages soon :)

---

### Post by jacrider on 2008-12-12
Thanks to everyone involved.  A one-step process to get a DVD to an iPod/AppleTV format is a great improvement.  I used to use AdidRip and ThinLiquidFilm to do this in a two step process previously.

Of interest, I have experienced my Ubuntu (8.10/64-bit) machine being MUCH faster than my wife's iMac with a similar config in ripping/encoding a DVD.  Expected?

---

### Post by JohnAStebbins on 2008-12-12
If the machines are similarly configured, then the speed should be the same.  I've heard that some mac's have horribly slow optical drives.  You might want to test pre-ripping and encoding from the hard drive.

Visit the handbrake support forums and post a complete activity log of the same movie with the same settings on each system if your really concerned and would like someone to look into it.

---

### Post by jdong on 2008-12-12
I agree with John on this; a comparable-generation CPU in my experience has extremely similar encoding performance across all operating systems in my experience; the problem is likely related to the speed it can read off the optical drive. IMO Apple recently has been using poorer OEMs for its optical drives, though this is a practice becoming more and more universal across all computer vendors.

---

### Post by jdong on 2008-12-17
Quick update, I just uploaded a new packaging revision to the PPA. Changelog:

```

handbrake (0.9.3+repack1-0ubuntu0~8.10jdong4) intrepid; urgency=low

  * Incorporate fixes suggested by John Stebbins:
   - Don't have the buildsys override HB's optimized CFLAGS
   - Do an official build (not a snapshot)
   - dh_icons/dh_desktop to correctly install menu icon

 -- John Dong < jdong@ubuntu.com>   Wed, 17 Dec 2008 21:15:07 -0500

```

This fixes the icon problem, and in the about-box now acknowledges it's a real build (tm). More importantly, John Stebbins caught the build system overrode HandBrake performance optimization flags. This build from my quick testing yielded around a 5% framerate improvement.

---

### Post by matthew on 2008-12-17
Cool! I'm off to update... Thank you.

---

### Post by jrusso2 on 2008-12-18
This is one of the problems that keeps linux from being mainstream.  I download handbrake, installs and says all dependencies satisfied but won't start.

Hardy is only 6 months old.  These packages should work with a Linux thats only six months old.  No wonder no one will build commercial software for Linux

---

### Post by jdong on 2008-12-18
Where did you get your package from? Does running "ghb" from the command line produce any errors?

---

### Post by JohnAStebbins on 2008-12-18
jrusso2, if you are using the package from the handbrake download page, the problem could be missing dependencies.  This is the first time I've made ubuntu packages, and I screwed up the dependencies in that package.  You can either use the packages that jdong has created, or run "ldd /usr/bin/ghb" to figure out what your missing and install them.

---

### Post by sefs on 2008-12-18
Where can we grab the jdong packs?

---

### Post by jdong on 2008-12-18
> **sefs said:**
> Where can we grab the jdong packs?

[https://edge.launchpad.net/~handbrake-ubuntu/+archive](https://edge.launchpad.net/~handbrake-ubuntu/+archive)

Choose the dropdown that matches your version of Ubuntu, and copy the APT deb URL.

---

### Post by Polygon on 2008-12-18
the package to install is handbrake-gtk. Not handbrake. confused me for a minute.

---

### Post by jdong on 2008-12-18
Ack I thought I deleted handbrake from the PPA already :(. Stupid PPA.

---

### Post by bikerider42 on 2008-12-21
After much searching i found this sight that has an updated svn version that works in hardy!!! am using it now!

[url]http://filthypants.blogspot.com/2008/09/32-bit-handbrake-gtk-gui-and-yasm-deb.html

---

### Post by jrusso2 on 2008-12-21
> **jdong said:**
> [https://edge.launchpad.net/~handbrake-ubuntu/+archive](https://edge.launchpad.net/~handbrake-ubuntu/+archive)

Choose the dropdown that matches your version of Ubuntu, and copy the APT deb URL.

Where is the download?  Do I have to install the repo I just wanted the package?

I don't see anything that says Hardy.

---

### Post by jrusso2 on 2008-12-21
> **JohnAStebbins said:**
> jrusso2, if you are using the package from the handbrake download page, the problem could be missing dependencies.  This is the first time I've made ubuntu packages, and I screwed up the dependencies in that package.  You can either use the packages that jdong has created, or run "ldd /usr/bin/ghb" to figure out what your missing and install them.

Strange Gdebi told me all the dependency were satisfied. It installed fine but would not start.

---

### Post by jdong on 2008-12-21
> **jrusso2 said:**
> Where is the download?  Do I have to install the repo I just wanted the package?

I don't see anything that says Hardy.


Hit the dropdown next to **handbrake - 0.9.3+repack1-0ubuntu0~8.04jdong4 ** if you only want the packages; install all the provided .debs (-common before others)

---

### Post by jrusso2 on 2008-12-21
Wow, that looks pretty sweet, thanks for making that for us.

---

### Post by Ngtstlkr on 2009-01-04
JDong, you are the MAN.  Works great on my AMD64 ubuntu Hardy install.  So much appreciated, I can now get rid of my VirtualBox XP install where I was running all my DVD stuff!!

Everytime I tried to install the official DEB of the GTK GUI Handbrake it would complain that a depenency of GTK2.0 wasn't met, although I have it installed.

Thanks again man!!

---

### Post by toneman77 on 2009-01-08
Hi there.
First congrats to JohnAstebbins and you guys here who packaged handbrake and provided a ppa for all of us.
After a lot of successful encodings (I mainly do XviD) with the cli version I recently encoded some dvds with the gui version (original from handbrake.fr and from the ppa) and I get very good results. 
"Very good" except one big problem: The index of the resulting avi files seems to be broken. I cannot fast forward (I hope that's the correct word) or backwards in the resulting movies.

Did anyone else ran into such problems when encoding XviD?

Any help appreciated

Tone

---

### Post by zagor on 2009-01-12
I've been looking into HandBrake for linux for a while and ended up with quite a messy compile, with loads of [dependencies ]("http://ubuntuforums.org/showpost.php?p=5410459&postcount=54")to satisfy, on my mythbuntu 7.10 64bit, now upgraded to 8.04 64bit.
So, before installing jdong packages, should I remove the existing installation of HB 0.9.1? is there a quick and easy way to remove an installation from compile (possibly including jam and all its otherwise unused dependencies)? 

Thanks

---

### Post by JohnAStebbins on 2009-01-12
Since you were using handbrake 0.9.1, you didn't have the new gui and all that goes with it so things are at least a bit simpler. There is no install target for HandBrakeCLI, so you either ran it in place or copied it yourself to a directory in your path.  Your the only one that knows how to clean that up.  The only additional packages I can think of that you would need are all the development stuff.  No way to be sure what all you might have installed, but the current ubuntu requirements for the cli are:
# subversion
# jam
# yasm
# build-essential
# autogen
# autoconf
# intltool
# libtool
# zlib1g-dev
# libbz2-dev 

If your never going to do any compiling from source again, you may want to remove these things.  But there's no harm in leaving them.

---

### Post by Zack McCool on 2009-01-14
Thanks so much for this package.  I added the Launchpad PPA repo for Hardy, and it installed without a hitch (Mint 5.0, i386).  This looks like a great app!

---

### Post by rks1789 on 2009-01-21
After trying some other methods of installing Handbrake I finally got it to work using the Launchpad PPA for Hardy.

The one issue I have is that for audio options (ghb) are AAC and AC3, MP3(lame) and Vorbis are both there but greyed out.

I have tried installing lame and re-installing the handbrake packages (handbrake-common, handbrake-cli and handbrake-gtk), but nothing has worked yet.

Any suggestions?

I've searched google, and the forums and haven't seen this issue so it's probably something I'm doing wrong.

Thanks!

Rich

---

### Post by JohnAStebbins on 2009-01-21
Some audio codecs are not supported in some containers.  I'm guessing your attempting to use the mp4 container.  The mkv container supports all audio types.

---

### Post by rks1789 on 2009-01-22
> **JohnAStebbins said:**
> Some audio codecs are not supported in some containers.  I'm guessing your attempting to use the mp4 container.  The mkv container supports all audio types.


Thanks!  I would never have thought of changing the container.  I ripped a video and it seems to be working fine, now to batch up the whole list :)

Thanks for the PPA, all the other methods couldn't get the gui up and running (the CLI worked ok).

Rich

---

### Post by IanVonSpeedfreak on 2009-01-27
I'm having trouble signing jdong's HandbrakeGTK package.  I followed all of the directions [_[COLOR="Red"]here[/COLOR]_]("https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories"), but for some reason I keep getting warnings that the source is untrusted.  I used the same command for adding a key, except I replaced the AWN key with the key for the HandbrakeGTK package.  Like this:

```
gpg --no-default-keyring --keyring /tmp/awn.keyring --recv  C82083B00E564A8EB4B821F1E43D207C62D38753 && gpg --no-default-keyring --keyring /tmp/awn.keyring --export --armor C82083B00E564A8EB4B821F1E43D207C62D38753 | sudo apt-key add - && rm /tmp/awn.keyring
```

Is there a better way to add a PPA key?  Or am I simply doing something wrong?

btw.  Thanks to jdong for making this version of Handbrake available for Hardy Heron.

---

### Post by travis_x33 on 2009-02-05
I apologize for this very vague question - I have searched this thread and not found my exact problem.

I am running Ubuntu 8.10 and installed the 0.9.3 HandBrakeGTK binary.  Whenever I run it from the gnome menu nothing whatsoever happens (nothing that is visible to me in any case!).

When I run 'ghb' from the console I get simply 'Segmentation fault'.

When I run 'HandBrakeCLI -i /dev/scd1 -L -o ~/test.mp4', it appears to be working properly.  I'm too impatient to wait for it to finish to verify that - I should have ripped a shorter DVD title.  It does seem to be working astonishingly fast, at about 50% real-time (30 seconds to rip 1 minute of video, full frame rate).  My previous ripping attempt using a Windows ripper ran at about 3x real-time (at about half the DVD frame rate).  Same machine (dual-boot) in both cases.  I've read a couple of reviews that stated HandBrake isn't all that fast, so my Windows ripper must have been a real dog - or the rip isn't really working :(

I am getting no error messages, however, and it is building an ever-increasing .mp4.

I have re-downloaded and installed in case of a corrupted download, not to mention rebooting several times (unrelated) over the last couple of days.  No joy.

Any ideas?

---

### Post by Polygon on 2009-02-05
you might have better luck asking on the handbrake forums (handbrake.fr) since the developers hang out there more. just be sure to be very descriptive in your problem, provide exact error messages, what you did, your distro, etc

---

### Post by jhayes on 2009-02-10
i LOVED handbrake when i was on windows.
i just permanently and finally fully switched to ubuntu.
i installed the  .deb, all went well, but when i tried to run it,
i would see handbrake for a second then it would go away.
so i build from source.
the instructions on their site aren't very clear. so here is what i did.

sudo apt-get install subversion jam yasm build-essential \
autoconf intltool libtool zlib1g-dev libbz2-dev libglib2.0-dev \
libdbus-glib-1-dev libgtk2.0-dev libhal-dev libhal-storage-dev \
libgtkhtml3.14-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev

svn co svn://svn.handbrake.fr/HandBrake/trunk

cd trunk
make
cd gtk

after that ... worked great !
sudo make install

---

### Post by The Belgain on 2009-02-23
Out of interest, is there any progress getting these added to the official repos?

---

### Post by forger on 2009-02-24
[https://launchpad.net/~handbrake-ubuntu/+archive/ppa](https://launchpad.net/~handbrake-ubuntu/+archive/ppa)
[https://bugs.launchpad.net/ubuntu/+bug/105458](https://bugs.launchpad.net/ubuntu/+bug/105458)
[http://revu.ubuntuwire.org/p/handbrake](http://revu.ubuntuwire.org/p/handbrake)

---

### Post by The Belgain on 2009-02-25
Looks like the package in revu isn't the one jdong packaged (it's an old upload of 0.9.2 with a bunch of packaging issues).

jdong: are you planning on submitting the packages from your PPA to REVU at all?

---

### Post by jdong on 2009-02-26
> **The Belgain said:**
> Looks like the package in revu isn't the one jdong packaged (it's an old upload of 0.9.2 with a bunch of packaging issues).

jdong: are you planning on submitting the packages from your PPA to REVU at all?


Well unfortunately I am not able to get concensus that my way of packaging (namely: respecting upstream's request to bundle their preferred library versions rather than building against repository libraries) is correct. Due to that and business in my personal life I never had the chance to make a huge push to include it in the repositories. The 0.9.2 work is not the issue right now, Christian Marillat pushed into Debian Multimedia a copy of Handbrake that builds against system libs for unpatched libraries too. I attempted to convince him via e-mail that this isn't what upstream wants and we should respect that, but that did not succeed.

At this point I am content with assisting in the HandBrake team to package their latest versions in a way I feel to be of MOTU quality, so they can have packages they are satisfied with giving their user should they have problems with whatever Debian/Ubuntu distro repositories will include by default.

---

### Post by Mic_Droz on 2009-03-31
Just wondering...

I was playing around with the old svns for a while, but now I want to change to the "official" .deb, but after installing, I've got nothing in my menus, and when I try to and ghb to the menu and then run "ghb",  i get nothing...

I can still run the old svns through the commandline, but ideally, i want them to bugger off.. Can someone tell me how to remove the traces of the svn handbrake gtk stuff that I was screwing around with? I'm so lost - I was so happy about actually being able to compile the thing, i never thought of the consequences...

so i guess my question is - how do i get rid of the old, so I can use the new?

---

### Post by JohnAStebbins on 2009-03-31
If you really want to remove the svn version, the quick way is "make uninstall" from your svn sources.  If you've already eliminated those sources, then the list of files iirc is:
/usr/local/share/applications/ghb.desktop
/usr/local/bin/ghb
/usr/local/bin/HandBrakeCLI

Though, if you're successfully compiling svn, I don't know why you would want to revert to older code.  There have been many fixes since the release.

---

### Post by JohnAStebbins on 2009-06-23
There is now a pre-release svn snapshot available for Ubuntu 9.04 32/64 bit. Snapshots are unstable releases intended for knowledgeable users who can provide useful feedback.  They are by definition broken (in some as of yet unknown way).

The forum announcement is here:
[http://forum.handbrake.fr/viewtopic.php?f=6&t=11201](http://forum.handbrake.fr/viewtopic.php?f=6&t=11201)

---

