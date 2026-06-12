---
title: "Partitioning and Other Suggestions for Installation of U-S"
date: 2010-09-10
forum: Ubuntu Studio
---

### Post by -kg- on 2010-09-10
I [made a post]("http://ubuntuforums.org/showthread.php?t=967077") a couple of years back on very nearly this same subject and considered resurrecting it, but as nearly two years and a lot of water has passed behind, I decided instead to make a new post.

I have just downloaded Ubuntu Studio 10.04 (64 bit) and burned it to a flash drive, with the intention of installing it to my desktop downstairs and to my External drive for some limited use on my laptop.  I intend to use my laptop for some limited audio editing (and maybe some video) and my desktop for the heavier stuff.

As I said, I have advanced considerably since I made that original post.  This is not a request for help in installing Ubuntu Studio...I am quite capable of installing Linux OSes and all the configuration and post installation setup involved.

What I want are suggestions concerning what others consider a good efficient setup as far as what directories I might want to put in a separate partition, as well as any other suggestions you feel might be pertinent.  In the old post, for instance, it was suggested that I might want a separate "/tmp" partition, and I can't swear to it, but something I read somewhere suggested that I might want to consider a separate "/etc" partition, as well.

Also very welcome would be any suggestions concerning setting up U.S. other than the standard setup one would do with any Linux installation.  I'm well aware that there are software packages that I'm unfamiliar with (I never did install U.S. back 2 years ago) and would appreciate guidance with some of the audio/video editing and other non-standard software included.  Maybe some additional software I might want to check out?

One of my first projects will be cleaning up some recordings that I digitized from cassette tape some years back.  I recorded and otherwise obtained those recordings some 25 years back, and as soon as I was capable digitized them and stored them as mp3 files.  They were digitized at a fairly good bit-rate (256 bits), but by the time I did it the tapes had deteriorated a bit.

I'd like to be able to clean them up and enhance them a bit.  I know that I won't be able to work miracles with them...most of it was recorded directly to the cassette tape it resides on...but I'd like to clean them up and see if I can get them to sound at least better than they currently are.  At least one member of the original band  would love to get copies of those songs, and I'd like to clean them up before providing them.

I also have videos that I haven't dealt with yet and would like to get some of those dealt with, as well.  All suggestions and help will be appreciated!

---

### Post by reiki on 2010-09-11
I rarely do upgrades any more and usually have 2 or 3 native installations in multiboot with several more installations in Virtual machines. I have a very basic partitioning procedure. I know this is somwhat subjective and relative to disk space, but I have a 750GB internal and a 640GB eSATA external so I really am not lacking for space.

My everyday Ubuntu installation has 50GB / and 570GB /home.  This is a single user machine for the most part. OK my wife has her own login but she also has her own computer so she doesn't use a lot of room. I have an 8GB swap. I have 8GB of memory and the swap has never been touched, but I don't miss that 8GB so I leave it alone.

When I had 2 drives internal, I would put my swap on a separate drive from the OS and /home. Just something I started doing way back in my slackware experiment days. It made a difference then. Not sure if it's necessary any more.

So that's it. KISS principal. Root and home partitions. That's my current method. It seems to work well. And it's easy to remember (and at 58, easy-to-remember can be important!).

I can reinstall the OS without screwing up my home folder. There's no real reason why my root folder is 50GB. I have used 10GB in the past and it wasn't an issue.

---

### Post by JC Cheloven on 2010-09-11
Hi, -kg-, nice to see how a knowledgeable person as you still has questions :D

> **-kg- said:**
> I [URL="http://ubuntuforums.org/showthread.php?t=967077"]
(...)What I want are suggestions concerning what others consider a good efficient setup as far as what directories I might want to put in a separate partition, as well as any other suggestions you feel might be pertinent.
I have a Carillon computer, a machine conceived (in principle) as a dedicated audio computer. It has a fast disk for the OS, and a big disk for the audio. I really never understood completely the reason to advice separate partitions for /home, /etc, or whatever. I find it much more practical to simply use a separate disk (or partition) for your data. I disciplined myself to not use my home directory for that. I think on it as a place where the system stores my configuration files. This eases both using several OSes, and reinstalling. Very personal though.

>  
Also very welcome would be any suggestions concerning setting up U.S. other than the standard setup one would do with any Linux installation.
I completely uninstalled pulseaudio because I had particular severe problems with my pci audio card (see post #4 and #42 [here]("http://ubuntuforums.org/showthread.php?t=1313253")). But I wouldn't advise that in general: the pulseaudio -k / pulseaudio -D commands should work just fine if pulse is getting in your way.

>    I'm well aware that there are software packages that I'm unfamiliar with (I never did install U.S. back 2 years ago) and would appreciate guidance with some of the audio/video editing and other non-standard software included.  Maybe some additional software I might want to check out? 
Well, you can ckeck out my signature, and eventually have a look [here]("http://ubuntuforums.org/showthread.php?t=1370121") ;)

> 
One of my first projects will be cleaning up some recordings that I digitized from cassette tape some years back (...)  
The program SoX has a noise reduction based on noise profile, which can be well suited for the kind of noise from audio tapes. I used it succesfully. Please install sox and have a look at the noiseprof and noisered functions in the man pages. Some audio editors, as audacity, implement a noise reduction function using (I believe) SoX as a the backend. You can use also SoX conveninently from the program in my signature, using the external processing facility.
EDIT: I never used [gramofile]("http://www.opensourcepartners.nl/~costar/gramofile/")  It seems inactive since 2005 but interesting anyway. I you eventually try it, please tell us how it was.

> 
I also have videos that I haven't dealt with yet and would like to get some of those dealt with, as well.  All suggestions and help will be appreciated!
In which format are the videos stored in? Are they old VHS tapes, or something more actual?

---

### Post by -kg- on 2010-09-12
Thank you to everyone who has answered so far.  I'll address a few of the issues submitted:

> **reiki said:**
> I rarely do upgrades any more and usually have 2 or 3 native installations in multiboot with several more installations in Virtual machines.

That's the way I handle it as well.  I don't use Virtual machines, but I do fresh install almost every time I upgrade.  The only (successful) upgrade I've had is on my desktop, and just about all I use it for is processing BOINC work units and light Internet surfing (for now).  On my laptop, in addition to Vista, I multiboot Ubuntu, Fedora, and OpenSUSE, and have Ubuntu installed on my external (soon to be replaced by U.S.).

It's almost a given that I have to fresh install on my laptop, because that is what I do my experimental poking and prodding on.  In fact, a separate /home partition doesn't do me any good, either...I have to replace it, too, backing up my critical data before doing so.

> **reiki said:**
> I have a very basic partitioning procedure. I know this is somwhat subjective and relative to disk space, but I have a 750GB internal and a 640GB eSATA external so I really am not lacking for space.

I'm in the same position.  I have 3 internal drives in my desktop - 400GB, 160 GB, and a 1 TB internal SATA.  My laptop has 2 internal drives - 120 GB and 100 GB, and a 1 TB External drive.

> **reiki said:**
> When I had 2 drives internal, I would put my swap on a separate drive from the OS and /home. Just something I started doing way back in my slackware experiment days. It made a difference then. Not sure if it's necessary any more.

Same thing I would do with Windows Swap and Paging files.  It made a bit of a difference, but as fast as processors and hard drives are these days, it probably wouldn't make a noticeable difference, except under special circumstances.  My swap rarely gets used either, even on my desktop with only 1 GB.  Windows is a different thing, though, as it seemingly uses swap or paging constantly.

> **reiki said:**
> So that's it. KISS principal. Root and home partitions. That's my current method. It seems to work well. And it's easy to remember (and at 58, easy-to-remember can be important!).

I can reinstall the OS without screwing up my home folder. There's no real reason why my root folder is 50GB. I have used 10GB in the past and it wasn't an issue.

That's the thing...video and audio editing is a different thing, and can use significant hardware resources, as well as a great deal of hard drive space.  I've done this before, especially under Windows using Ulead VideoStudio (this was several years back).  I ended up with a hard drive full of massive files.  Of course, back then I didn't have near the hard drive space I do now.

However, that is why I posted this thread.  If you edit large video and/or audio projects, you can quickly fill up a partition, and doing something like that, a 50 GB root partition might possibly not be big enough!

For instance, in my thread from a couple years back, it was suggested that I might want to make a separate /tmp partition.  It might be true, depending on the size of my projects.  /tmp is not contained in the /home partition, it's contained in the root partition.  The one in my installation here is 56 K, but using video/audio projects, this could easily change.  I've seen people with multi-GB /tmp files.

So is /etc, which contains certain software installations and their configuration (and often, storage for that software).  Mines not too big, but that can change between distros and what's standard in them.  Then there's /usr, which contains installed software, configuration files, and more software storage.  The /usr directory on my standard Ubuntu installation takes around 2.5 GB itself.

All this thinking, and I think I'll just probably go with an oversized root, a good sized /home, and a separate /data partition for the actual files and output.  Like you said, KISS.  I'm all about that.

> **JC Cheloven said:**
> I really never understood completely the reason to advice separate partitions for /home, /etc, or whatever. I find it much more practical to simply use a separate disk (or partition) for your data.

I'm really rather ambivalent about it, myself.  The only real advantage I find in a separate /home (and other partitions) is the ease with which you can find what you need to back up when you're upgrading.  A lot of configuration files are contained in the /home directory, but it's not really too hard to find the data you need if you store it there.

> **JC Cheloven said:**
> I completely uninstalled pulseaudio because I had particular severe problems with my pci audio card (see post #4 and #42 [here]("http://ubuntuforums.org/showthread.php?t=1313253")). But I wouldn't advise that in general: the pulseaudio -k / pulseaudio -D commands should work just fine if pulse is getting in your way.

Pulseaudio works fine with all my computers and audio cards.  I wouldn't have any reason to do so that I know of.  I've heard of conflicts between Pulseaudio and Jack (which is contained in Ubuntu Studio and used by some of the software) though, so I'll have to see.

Thank you for the software recommendations.  I'll check them out.  And I've already checked out the links you provided me.  I'll check that out, as well.

> **JC Cheloven said:**
> In which format are the videos stored in? Are they old VHS tapes, or something more actual?

No, my video camera is a bit more modern than that.  It uses DVS digital tapes.  So I don't even have to transcode (much :p ).  At least they're digital files to start with. :D  All I have to do is stream them onto the hard drive.  I have done some of the work, but not all of it.  I posted one of my (unfinished) pieces on Youtube:

[http://www.youtube.com/watch?v=XR0A5YJBmSc]("http://www.youtube.com/watch?v=XR0A5YJBmSc")

That's one of the local bands that I videotaped.  It's unfinished because I stopped when I couldn't find an overlay that I wanted for it (crashing WWII fighter or bomber). :p

Thanks again! ):P

---

### Post by -kg- on 2010-09-14
I have finally gotten U. S. installed, but certainly not without issues.  I've found a dearth of information on several of my issues, so thought I might record some of them and their solution so that someone having one or more of these same problems might find this and perhaps have some solution to their problems.

All these problems, I researched every which way, and the answers were very hard to find and almost obscured in the issues that were being addressed.  The answers to one I found in this forum, but as I stated above, not actually part of the issue being addressed.  I'll also attempt to change the tags to this thread for easier searching.

I had determined that I was going to install via USB.  It is (generally) faster than the CD/DVD method, and doesn't waste one every time you need an installation disk (I must have 50 of the doggone things sitting around, and I'm constantly throwing away the outdated ones).  So I burned the .iso to a Flash drive (yes, I checked the MD5 Checksum...several times!...perfect) and set to it.  First problem...

It seems that with alternate-install .isos, you start the installation, go through the selection of time-zone and keyboard, then the installer does a search for its files...***on the CD-ROM***, even though you're installing from a Flash drive!  What's up with that?  I don't understand why the Live CD installer will do all this automatically from the USB or wherever you're installing from, but the Alternate Installer won't.

Anyway, it won't.  I looked and looked and Googled and Googled, and info on this was very hard to find.  But I finally found it:

[http://coliena.com/blog/2010/05/how-to-install-ubuntu-10-04-on-a-netbook-with-full-disk-encryption/comment-page-1/#comment-2701]("http://coliena.com/blog/2010/05/how-to-install-ubuntu-10-04-on-a-netbook-with-full-disk-encryption/comment-page-1/#comment-2701")

As I said above, the information wasn't exactly posted as an issue in itself that would be particularly searchable, unless you were specifically searching for information on installing secure encryption on a netbook using USB.  I haven't tried the method described on the page, but at least I now know where to find the information, and so does anyone who runs across this thread.

Well, before I (*finally!*) found this information, I was impatient to get U.S. installed, so I bit the bullet and burned the .iso to a DVD, where it could "find itself" (maybe I should have sent it on a European hiking vacation!) and set to installing.  Some notes now on the partitioning scheme I asked about in the OP...

Before launching any installations, I had previously (through Gparted from the installation on my internal drives) resized the swap drive on the External (from 3 GB to 4 GB...probably unnecessary, but considering the "the nature of the beast", and the fact that I have all the room in the world, it couldn't hurt!) and moved it 100 GB to the right, giving me room to manipulate the U. S. partitions without having to play with it.

Naturally, I selected the "Manual partitioning" selection and created my own partitioning scheme, especially since I was installing on my external hard drive (for use with my laptop).  I already had a Lucid installation on it (for emergencies and demonstration uses) in a 50 GB "/" partition, so I determined that I would use that partition as "/" for U.S., and create one or two more for "/home" and (originally) "/data".

I "edited" the existing "/" partition, marking it for formatting and marking the mount point, then went on to create the other partitions.  I determined to use half of the remaining 100 GB of free space (between "/" and swap...there's more on the other side) for each of the other partitions.

I created the first partition, and the partitioner defaulted to a mount point of "/home".  Okay, I was cool with that, since that was my intention anyway.  Then I created the second partition.  What it defaulted to might have answered one of my original questions.  The installer's mount point defaulted to "/usr".

Considering some of the uses software makes of that particular directory (and hoping that the "defaulting" was by intelligent choice rather than random chance :p ), I accepted that default as well.  In any case, directory usage can be assessed later, and partition sizes adjusted accordingly.

This last issue (in this post...I'm going to split the post for continuing "issues") is for those who, like me, are making an installation to an external hard drive and don't want to make booting their *entire computer* dependent on the external hard drive being connected (I've resolved this issue for others a number of times).

When installing an OS on external media, you ***_CAN_ _NOT_*** allow the GRUB installer to install to the default location, unless you intend that drive to be permanently connected to your system (in that case, get another internal hard drive)!  The GRUB installer portion of the OS installer installs GRUB by default to the MBR of the first (master) hard drive that the computer will normally be booted to, and that is your internal hard drive.  In this case, since the OS is on the external drive, if that drive isn't connected, the computer won't boot.

So if you're installing on an external drive, you must override the default GRUB bootloader installation location and point it to load to the MBR of the external drive (in my case, since I have two internal HDs on my laptop, my external drive is sdc).  This gives you two advantages...

First, it leaves your internal drives MBR as is.  Your computer is bootable whether the external is connected or not, and if you (like me) have GRUB from another installation installed on the internal HD, you can run "sudo update-grub" from that installation with the external connected and have the external drive installation included in its menu.

Second, you can boot into that installation from almost any computer (within some limitations) that can boot to a USB device.  Just select the boot device from the menu or make sure USB is ahead of hard drive in the list in BIOS, and it will pick up the bootloader and boot from it.

The reason I mention all this is that the Alternate Installer handles this differently from the Live CD installer.  With the Live CD installer, you determine the GRUB installation location from the last screen, under the "Advanced" button.

With the Alternate installer, a screen will come up that says it's going to install GRUB to the MBR of the primary hard drive and asks if that's OK.  In this case it was definitely ***not*** OK, so I selected "NO".  It then took me to a screen which instructed me in the method of determining location of installation.

If you will be using this method, you will need to know the device designation of your external drive.  In my case, it is sdc.  You will need to type in this location *exactly* as shown in the examples.  You cannot just type in "sd(x)"; you must type in "/dev/sd(x)".  I will make a special note on this in the next post, so watch for it.

More to come...

---

### Post by -kg- on 2010-09-14
Now to continue...

I successfully completed the installation and booted into it with the intention of applying any and all updates to the installation.  This is where I ran into my second issue.

Though I didn't know it at the time,  Network Manager is not installed with Ubuntu Studio.  Network Manager interferes with audio processing under the Real Time kernel, and therefore there is another network managing software installed instead..."gnome-network-admin".  The explanation for this (which was even harder finding the information on than the USB alternate install problem above) is on this page:

[http://www.mail-archive.com/ubuntu-studio-devel@lists.ubuntu.com/msg02286.html]("http://www.mail-archive.com/ubuntu-studio-devel@lists.ubuntu.com/msg02286.html")

***_Now_***, I know that I (*maybe*) could have hooked the laptop to an Ethernet connection and just installed Network Manager from the repositories, but at the time I was stymied.  I thought I might have screwed something up in the installation process.  So I booted back into my regular installation and started the research process.  It *(eventually!)* led me to a thread in this subforum:

[http://ubuntuforums.org/showthread.php?t=1514006]("http://ubuntuforums.org/showthread.php?t=1514006")

But being that I was already confused and a little anxious to get the installation up and going, I took another route.  I made a fresh installation of straight Ubuntu into the existing partitions, updated it, then installed the U. S. packages from the repos.  This gave me N. M. (so I could use my Wireless) and a U. S. installation, to boot.

Of course, at that time I hadn't found the information about N. M. and U. S. yet.  I thought that something I had done (or not done...remember that the MD5 Checksum checked out on the .iso) has caused N. M. to not be installed.  I tried installing it from the DVD, but for some reason it wouldn't install.  Thus, being impatient, the above method.

Now when you install the Studio packages in an existing Ubuntu installation, there are some considerations you should be aware of, the chief of which is the RT (real-time) configured kernel.  Installation of the packages (at least, the one dealing with audio) will include installation of the -rt kernel, but *will not* uninstall the generic kernels from the original installation.

In my experience, the -rt kernel was a lower version number of kernel, which placed it at the bottom of the GRUB menu list.  I booted back into U. S. several times before I realized that.  So the next time I install U. S. (and if I'm forced to do the same thing...upgrade my existing system), I will know that the first thing to do is to uninstall all "-generic" kernels, leaving the "-rt" kernel in place (that is, unless you want to use different kernels for different purposes.  Then you'll need to choose the kernel you want to use at boot time).

Something you also need to consider is the altered configuration files.  When you install U. S. proper, there are certain configuration files that are introduced by default.  If you install the packages, these configuration files will have to be altered (and created) manually.  The following page will tell you what and where these files are, and how they are to be altered, in addition to the command line method to install any or all of the packages:

[https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu]("https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu")

An additional post-installation note:

1.)  As has been noted previously, Network Manager interferes with some audio processing due to latency issues with the -rt kernel.  Of course, I have N. M. installed in my installation.  I have read elsewhere (by one who also has N.M. installed) that the way to deal with this is to uncheck N. M. in "System/Preferences/Start-up Applications" and then reboot.

I've found that it shouldn't be necessary to entirely reboot.  I did an experiment in which I performed the above, then instead of rebooting I just logged out and logged back in.  System Monitor confirmed that the N. M. services were no longer running.  I also read that you could restart N. M. by running the applet from the terminal; considering my previous statement, it would be just as easy to pull up the "S-U. Apps", check N. M., and log out/back in.

You'll need the ability to connect to the Internet from time to time to check for updates on the software, etc.  If your Ethernet connection is inconvenient to access (as is mine) then you'll want the ability to connect via wireless, and currently "gnome-network-admin" doesn't seem to do the job.  Perhaps someone has come up with a way to do it, but I'm satisfied with what I have now.

Now, on to bigger and better things, like figuring out how to use the software with my new installation and what software I might want to try that's not included by default! ;)

---

