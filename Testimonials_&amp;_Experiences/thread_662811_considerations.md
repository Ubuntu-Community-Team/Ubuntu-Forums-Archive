---
title: "considerations"
date: 2008-01-09
forum: Testimonials &amp; Experiences
---

### Post by ihatenicks on 2008-01-09
I have been really trying hard to switch from Win to LINUX for the last month but I don't know if I will keep working in this direction.

I am not a geek but my computer knowledge is above average. I can't deal with all the compiling and some times to long installation procedures.

APPLICATIONS

I need to work with progs like Photoshop, panorama stitching and image batch processing like I do with ACDSEE since years.
I tried to install GIMP SHOP following the instruction provided by the creator on his site. Result: Not working
I tried to find a program comparable to ACDSEE. Digikam seems to be the closest solution but, I can't beleive that after the batch rename process I have to manually 1) refresh the thumbs and 2) synchronize the DB. I mean... this is simply crazy!
The Hugin for stitching pano pics can't automatically generate control points. I use the same images in PTAssembler in Windows and all it goes smooth and fast until the final image.

Also, I can't understand why so many progs don't have an installer like Google Earth. I mean... if Google made such a Win-like installation for its application, why not making the same for all the other progs?

Of course I didn't give up on Ubuntu, yet, so... all the suggestions are welcomed.

Gabriele
Italy

EDIT

Look at this...
I am trying to install a mail notification program. THe installation guide says you need libnotify as MANDATORY (so why didn't you include it in the package?). Ok, I go to download the libnotify and I open the installation guide:

The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

I mean... how the h.ll should I know if I have a System V?

---

### Post by armandh on 2008-01-09
some things will just not fly
I dual boot
ubuntu for surfing/e-mail etc and 
xp for those win-only-things I can't do without
at my age [collecting SSI next month]
I find pounding a square peg in a round hole 
not worth the effort.

---

### Post by MNICY on 2008-01-10
install a virtual machine like Virtualbox.
(sudo apt-get install virtualbox)

---

### Post by wolfen69 on 2008-01-10
ive never had to compile anything or unpack tar.gz files. get your programs from [www.getdeb.net](www.getdeb.net) 
1 click to install these.

also, if you modify your sources list, you can download anything from synaptic.

---

### Post by 3rdalbum on 2008-01-10
> **ihatenicks said:**
> Also, I can't understand why so many progs don't have an installer like Google Earth. I mean... if Google made such a Win-like installation for its application, why not making the same for all the other progs?



The way Google has made the Google Earth installer limits its ability to run on other computers. If you made a "Win-like installer", it would mean that you'd only be able to install the program on the x86 architecture (i.e. generic PCs). People running Linux on other CPU architectures like ARM or PPC cannot install or run Google Earth due to the way Google has released the program.

Whereas the Linux programs that are released as source code can be compiled and run on ALL Linux computers - from PowerPC-based Macintoshes to the Nokia internet tablets to IBM supercomputers.

> The installation guide says you need libnotify as MANDATORY (so why didn't you include it in the package?).

It's a waste of space to include dependencies in a package. Think of iTunes - regardless of whether or not you have Quicktime, you still must download it whenever you download a new version of iTunes. Half the download is taken up with something you probably already have.

Also, if you want to use a new version of libnotify which has bugfixes or new features, you *can* use it rather than being stuck with whatever version the mail notification program shipped with.

The Linux concept of dependencies came in useful when Apple's new iPods broke compatibility with previous iPod management programs. All those programs use a library called "libgpod" to provide the backend functions. Developers of the management programs didn't have to alter a single line of code or make a new release to support the new iPods - they just had to tell their users to get the latest version of libgpod.

That's clever.

> Ok, I go to download the libnotify and I open the installation guide:

The simplest way to compile this package is:

Now it's time to be really clever, and use the Synaptic Package Manager.

First, do a search for the mail notification program you originally downloaded. If you're lucky, it will be in Synaptic for a simple 3-click install. If not, then look through Synaptic for a similar program. I'm sure there are some.

If that fails, then use Synaptic to install libnotify with a handful of clicks. Install these packages:

libnotify1
libnotify1-gtk2.10
libnotify-bin
libnotify-dev
libnotify-dev-gtk2.10

Don't worry, it's a common newbie mistake to go diving for Google whenever you want to install something. I did it a few times. Always check Synaptic first to see if it's got what you're after.

---

### Post by ihatenicks on 2008-01-10
First of all I thank you all of you for the replies.

Then...
> 
The way Google has made the Google Earth installer limits its ability to run on other computers....

Gotcha!

> Now it's time to be really clever, and use the Synaptic Package Manager.

First, do a search for the mail notification program you originally downloaded. If you're lucky, it will be in Synaptic for a simple 3-click install...


That is right and I feel so stupid right now :) I coould have checked there first, instead of going straight to google it.

Ok, I think we are on the right track.Let's move forward...

 It's Virtual Box a solution to emulate Win while in Linux?

I tried to install it but it didn't start after configuration. I just need a reply to my question (above) and if the answer is "yes" then I'll post a proper topic.

I really like this Linux. Applications start so quickly and everything is so smooth. Very low hardware needs. I really wish there would be a  valid alternative to ADCSEE, Photoshop and Premiere. 
Anyway, if this is ow linux works, maybe the solution is a Mac :)

---

