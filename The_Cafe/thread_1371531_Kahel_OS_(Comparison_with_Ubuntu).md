---
title: "Kahel OS (Comparison with Ubuntu)"
date: 2010-01-03
forum: The Cafe
---

### Post by skewty on 2010-01-03
The other **Kahel OS** thread was closed.

My hope for this thread is to provide Ubuntu users who are looking for a rolling release Gnome distribution reviews of Kahel OS.

If posting:

Please don't talk about theft from Arch.  That has been covered in other threads and on other forums.  No license politics please.

Please don't talk about other distributions (aside from Ubuntu and Kahel OS).  If you must, please create a new thread.

Please don't post unless you have used the December 2009 release of Kahel OS yourself.  Most people will not interested in how it used to be.

Please post your questions regarding Kahel OS in the Kahel OS forums, not here.

I am downloading the CD image now.  A log of my impressions and experience with this PC will follow shortly.

---

### Post by RaZe42 on 2010-01-03
...So what are we supposed to discuss in this thread?

Seems like advertising to me.

---

### Post by RATM_Owns on 2010-01-03
[s]I love the logo.[/s]

EDIT: Aw, it isn't fun anymore without the image...

---

### Post by skewty on 2010-01-03
So I got the December 2009 release of Kahel OS installed.

I'll start by saying the textmode installer needs a lot of work and polish.
The progress reporting is well, there isn't any.  It also asks questions it answers for you (giving you no choice at all).

I thought it had locked up at Installing Packages but it is just working away with no progress indication at all.  [Installation Problems]("http://forum.kahelos.org/topic/installation-problems")

During the Configure Your System process it appeared to hang at
"Generating glibc base locales..." but it just took a long time with no progress indication.

I had the Lockup after GRUB Installation at the Software RAID Question Problem which basically leaves your system with a broken GRUB so it doesn't boot anymore.
The fix was found in [Grub problems]("http://forum.kahelos.org/topic/grub-problems")

After rebooting, you notice that the grub configuration it generated required you to uncomment a few lines to enable your windows partition which this computer has.  I had to go back into /boot/grub/menu.lst to uncomment some lines to get the Windows GRUB entry back.

Once installed, I tried to play a movie from a NTFS partition.  It mounted the NTFS volume just fine and brought up a window telling me I didn't have the codec required.  It did not offer to install the required codec like Ubuntu.  I went into the package manager and installed gstreamer-*.  (New users would not know to do this)
The movie played properly after doing this.

I went into Firefox and it complained it wasn't the default browser.  I was not able to find any other browsers installed so I don't know why it wasn't the default.  Anyways I went to youtube.com and guess what no flash.  No window came up asking me to install flash.  I went into the package manager, did a search for "flash" and installed flashplugin.  That fixed it; YouTube works now.

I also wanted to get the Compiz 3D effects going.  As of this time, I haven't figured it out.  Initially I tried installing the compiz* packages.  That didn't do it.  A quick google search pointed me to type "pacman -S compiz-fusion".  I did that and got further but still don't have it.

Oh!  My screen resolution wasn't detected correctly.  I am stuck at 1024x768 for now.  The video card is a "nVidia Corporation NV15DDR [GeForce2 Ti]".

Sound and Network work just fine.

Using Alt-F1 virtual consoles doesn't work.  They are black.  Only Alt-F7 seems to work.

Once the setup is done, it could be a very nice system.  When I setup ubuntu for other people I always need to tweak things anyways.  Getting a new GIMP and OpenOffice installed in 8.04 is much more involved than what I had to do today.  

Perhaps their next release will impress me more.  For now, i'll stick to Ubuntu.

---

### Post by NoaHall on 2010-01-03
> **skewty said:**
> So I got the December 2009 release of Kahel OS installed.

I'll start by saying the textmode installer needs a lot of work and polish.
The progress reporting is well, there isn't any.  It also asks questions it answers for you (giving you no choice at all).

I thought it had locked up at Installing Packages but it is just working away with no progress indication at all.  [Installation Problems]("http://forum.kahelos.org/topic/installation-problems")

During the Configure Your System process it appeared to hang at
"Generating glibc base locales..." but it just took a long time with no progress indication.

I had the Lockup after GRUB Installation at the Software RAID Question Problem which basically leaves your system with a broken GRUB so it doesn't boot anymore.
The fix was found in [Grub problems]("http://forum.kahelos.org/topic/grub-problems")

After rebooting, you notice that the grub configuration it generated required you to uncomment a few lines to enable your windows partition which this computer has.  I had to go back into /boot/grub/menu.lst to uncomment some lines to get the Windows GRUB entry back.

Once installed, I tried to play a movie from a NTFS partition.  It mounted the NTFS volume just fine and brought up a window telling me I didn't have the codec required.  It did not offer to install the required codec like Ubuntu.  I went into the package manager and installed gstreamer-*.  (New users would not know to do this)
The movie played properly after doing this.

I went into Firefox and it complained it wasn't the default browser.  I was not able to find any other browsers installed so I don't know why it wasn't the default.  Anyways I went to youtube.com and guess what no flash.  No window came up asking me to install flash.  I went into the package manager, did a search for "flash" and installed flashplugin.  That fixed it; YouTube works now.

I also wanted to get the Compiz 3D effects going.  As of this time, I haven't figured it out.  Initially I tried installing the compiz* packages.  That didn't do it.  A quick google search pointed me to type "pacman -S compiz-fusion".  I did that and got further but still don't have it.

Oh!  My screen resolution wasn't detected correctly.  I am stuck at 1024x768 for now.  The video card is a "nVidia Corporation NV15DDR [GeForce2 Ti]".

Sound and Network work just fine.

Using Alt-F1 virtual consoles doesn't work.  They are black.  Only Alt-F7 seems to work.

Once the setup is done, it could be a very nice system.  When I setup ubuntu for other people I always need to tweak things anyways.  Getting a new GIMP and OpenOffice installed in 8.04 is much more involved than what I had to do today.  

Perhaps their next release will impress me more.  For now, i'll stick to Ubuntu.

It sounds like you need to try another distro than Ubuntu before trying a Arch based one.

---

### Post by Pogeymanz on 2010-01-03
Wow. Thank you for writing that, skewty.

There doesn't seem to be much reason to use KahelOS over Arch if you still have to do all that stuff by yourself. For me, the reason I use Arch is that it doesn't install ANYTHING unless I want it to, but an OS that is in between Arch and Ubuntu doesn't sound good to me.

Does this OS offer anything at all that I don't/can't have with Arch? Is it true that they use the Arch servers for their packages?

---

### Post by juancarlospaco on 2010-01-03
> **Pogeymanz said:**
> Is it true that they use the Arch servers for their packages?

Thats not illegal or something like that, i use Arch servers on Ubuntu,
you can use Ubuntu packages on Arch to, if you know how...

---

### Post by Xbehave on 2010-01-03
> **Pogeymanz said:**
> For me, the reason I use Arch is that it doesn't install ANYTHING unless I want it to
I've used ubuntu/fedora/debian/openSuse and nothing has ever installed itself either :O, it seams silly to pick arch/kahel because it's default install is nothing when you can just use the minimal CD of any other distro. That isn't to say there arn't reasons to use arch, just that one is silly.

As for the OP, I have no idea what kahel OS is? 
What are it's pro's/con's w.r.t to ubuntu (or any distro for that matter)?

---

### Post by skewty on 2010-01-03
Kahel OS is a rolling release that is heavily based on Arch.
It is Gnome biased.  It aims to be easier to install than Arch.

They now have seperate release for Desktop, Server and Netbook.

[http://www.kahelos.org/]("http://www.kahelos.org/")

Here's a few pros/cons for you:

_Pros_
Rolling Release (if you prefer this release style)

_Cons_
Less Mature
Smaller User Base for Support

---

### Post by skewty on 2010-01-03
> Wow. Thank you for writing that, skewty.

You are very welcome.

> an OS that is in between Arch and Ubuntu doesn't sound good to me.

If you are happy with Arch stay with it.  

I believe: (KahelOS << Arch) at the current time.

If you have the time and know how to run Arch, stick with it.

I was hoping it would be a quick to install, easy to setup rolling Gnome distribution.  I don't believe it is quite there yet.  

I am looking for a rolling release Ubuntu to install on some of my family's computers.  Currently they run 8.04 with updated versions of Firefox, OpenOffice, Brasero and GIMP.

---

### Post by ~sHyLoCk~ on 2010-01-03
spam thread is spam

---

### Post by Linuxforall on 2010-01-03
Really sad to see how the Kahel devs were treated by holier than thou Arch forum members. If Kahel or any other distro spreads desktop linux and specifically arch to the masses, where is the wrong in that may I ask? I also love the snide anti Ubuntu remarks by the same arch vermins there and yet those very arch fanboys will come trolling around here on every thread and shamelessly promote their distro without any reason or rhyme.

Strangely debian users which Ubuntu is based are on a totally different plane and I never hear any similar vitriolic spewed against Ubuntu at the debian forum.

---

### Post by ~sHyLoCk~ on 2010-01-03
Linuxforall

The attitudes of the kahel devs are the reason which triggered the dislike. Please read their forum posts in Arch forum. Also the fact that they did really stupid mistakes at the beginning of their releases, which as some claim have been corrected by now.

---

### Post by Linuxforall on 2010-01-03
> **~sHyLoCk~ said:**
> Linuxforall

The attitudes of the kahel devs are the reason which triggered the dislike. Please read their forum posts in Arch forum. Also the fact that they did really stupid mistakes at the beginning of their releases, which as some claim have been corrected by now.

I read that thread and I agree, initially they are a bit off on their big mega announcement, even then, I feel anyone trying to popularize Linux desktop shouldn't be punished that harshly. The more it spreads, the better for us all. They are targeting their native Philippines where the ones who can't afford PCs due to costly OS would surely appreciate this.

---

### Post by KiwiNZ on 2010-01-03
> **~sHyLoCk~ said:**
> spam thread is spam

If you do not like this thread or the OS  stay out of it last and only warning.

---

### Post by NoaHall on 2010-01-03
After going to that site, I have to say, I agree with my fellow archers. Aim and fire, aim and fire.

---

### Post by Dharmachakra on 2010-01-03
> **Linuxforall said:**
> 
Strangely debian users which Ubuntu is based are on a totally different plane and I never hear any similar vitriolic spewed against Ubuntu at the debian forum.

You must not have looked very hard. The fact is that almost all "base" distros have users that will bitch about a spin-off. It happens here too. 

That said, I'll try this one out when I have time. It's always nice to have a new distro to play around with. I always feel jaded when I browse through my 112 archived .iso's...

---

### Post by ~sHyLoCk~ on 2010-01-03
Ok I've been warned [where as yesterday no one received any warning, when I was stating the facts I was accused of calling all Filipinos thieves and verbally abusing a woman that she wants to go to women's rights or whatever lol, in fact she herself used abusive words and I replied to her rather politely and even asked her to "report abuse" me If she felt like it, please search and read that thread. ] and I won't express my opinions on kahel here anymore. But those who know, will know for themselves. 
> **NoaHall said:**
> After going to that site, I have to say, I agree with my fellow archers. Aim and fire, aim and fire.

I have a nice blog post to make about kahel. 

Cheers :)

/unjoins conversation

---

### Post by Dayofswords on 2010-01-03
it ok to make your own distro but it the way it was annouced and gloated around on the thread in the arch forums that brought the negative response

---

### Post by user1397 on 2010-01-03
As far as people who want a rolling release debian based distro, what's wrong with debian testing or unstable?

---

### Post by Linuxforall on 2010-01-03
> **ubuntuman001 said:**
> As far as people who want a rolling release debian based distro, what's wrong with debian testing or unstable?

Actually sidux rules in that facet, real good interface, very well maintained, easy to install, can't ask for more.

---

### Post by skewty on 2010-01-04
> **Linuxforall said:**
> Actually sidux rules in that facet, real good interface, very well maintained, easy to install, can't ask for more.

Sidux is a KDE distribution.  I am looking for a Gnome distribution.

---

### Post by Gizenshya on 2010-01-04
question...

are Simple installs and Customizable installs mutually exclusive?

I didn't think they were, but after reading this, I'm beginning to question that.

---

### Post by Xbehave on 2010-01-04
> **skewty said:**
> Sidux is a KDE distribution.  I am looking for a Gnome distribution.
Sidux is an easy way to install Debian Sid, most of the time it is just a standard debian install and so it supports Gnome as well as Debian does.


> **Gizenshya said:**
> question...

are Simple installs and Customizable installs mutually exclusive?

I didn't think they were, but after reading this, I'm beginning to question that.
They are not. try * minimal, and built an install of debian/ubuntu/fedora/etc up customising as you go? It's no different to building up an arch/gentoo install, just with the pain of having to deal with arch/gentoo.

---

### Post by meborc on 2010-01-04
so... arch has finally 2 spawns... ckakra for KDE and Kahel for Gnome

i was expecting it to be Gahel instead of Kahel though :D


my ideas on the comparison - the shear volume of howto's and blogposts and tutorials gives ubuntu a long lead... this combined with the fact that ubuntu is supported by Canonical assures me that this distribution is going to be available and under development for a long time, the same can not be said about Kahel

---

### Post by Pogeymanz on 2010-01-04
> **Xbehave said:**
> I've used ubuntu/fedora/debian/openSuse and nothing has ever installed itself either :O, it seams silly to pick arch/kahel because it's default install is nothing when you can just use the minimal CD of any other distro. That isn't to say there arn't reasons to use arch, just that one is silly.

As for the OP, I have no idea what kahel OS is? 
What are it's pro's/con's w.r.t to ubuntu (or any distro for that matter)?

Very true, but it's the same for me as all the Ubuntu spin-offs. I rather use the minimal install of Ubuntu and install Openbox if I want something like Crunch-Bang, you know? 

(I didn't literally mean that packages install themselves. I meant that nothing comes installed at all, as opposed to other distros where lots of stuff I don't want/need)

---

### Post by Linuxforall on 2010-01-04
> **skewty said:**
> Sidux is a KDE distribution.  I am looking for a Gnome distribution.

sidux also has xfce as an alternate.

---

### Post by Gizenshya on 2010-01-04
> **meborc said:**
> 
my ideas on the comparison - the shear volume of howto's and blogposts and tutorials gives ubuntu a long lead... this combined with the fact that ubuntu is supported by Canonical assures me that this distribution is going to be available and under development for a long time, the same can not be said about Kahel

I just pray that if Canonical ever decides to stop support, they designate a sucessor.  The last thing the world needs is another iteration of the whole Sunni/Shi'a fiasco.

---

### Post by snowpine on 2010-01-04
Ubuntu *is* rolling release... it completes one "rotation" every six months. :)

---

