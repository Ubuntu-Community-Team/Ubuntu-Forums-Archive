---
title: "I really want to edit videos in Ubuntu (kdenlive question)"
date: 2009-05-13
forum: Ubuntu Studio
---

### Post by mjpatey on 2009-05-13
Hello, all-

I am something of a longtime user of Ubuntu (running it exclusively since June of '06), so I have no axe to grind, I love Ubuntu, free software, etc.

But I bought a little portable camcorder that transfers its video files directly via USB (Ubuntu loves it, treats it like any other USB drive), but thus far I haven't been able to edit said files together to make a finished product.  I've tried all these:

Kino
Kdenlive
LMMS
Open Movie Editor
Pitivi

...and really wanted Jahshaka to work, but it hasn't been updated since '06, from what I can tell, and was not in a pretty state at that point.

Of them all, I've been really hoping Kdenlive works, because it's the closest thing I've found to a familiar, fully-featured environment for editing video (it's a lot like Sony Vegas running on Windows).  I'm able to use kdenlive for a few minutes, but inevitably it freezes after a short time.  Also, when I try to save a project, it will actually crash with a segfault.

I'm running 64-bit Ubuntu 9.04 (Gnome desktop) on a dual-core 2.7GHz AMD processor with 4GB of RAM and plenty of hard disk space.  The kdenlive install is straight from the repos.

Has anybody had this sort of problem with kdenlive and fixed it?

Thanks in advance for any insight or direction you may be able to provide!

-Mark

---

### Post by lisati on 2009-05-13
I'm sure there's a success story of video editing with Ubuntu - I'd love to hear of it too! 

<rant>
I gave up some time back, partly out of unfamiliarity/dissatisfaction with the batch of offerings that are Ubuntu-friendly (or is that laziness, not wanting to get one working or learning how to use it?) and kept Windows around for editing.
</rant>

I did have a look at Kino recently, and actually managed to get it to capture from a couple of cameras I have that hook up by firewire, and it looks promising. It was also able use files imported from another camera which hooks up via USB. Haven't had the time to learn the editing side yet.....

---

### Post by mjpatey on 2009-05-13
OK, to see what's going wrong, I ran it from a Terminal this time, and below is the output. It seems it may have a permissions problem early on (it can't create folders), then just before it terminates, a Fatal IO error 9 (Bad file descriptor), resulting in the inability to start Dr. Konqui.

 This run did not include the other problem I get a lot, which is after a while, I'm unable to play clips or the timeline. The program appears to be working in every other respect, but hitting "play" does nothing.

 I'm running kdenlive 0.7.3 as installed from the Ubuntu repos, on Gnome Ubuntu 9.04, 64-bit edition using an AMD dual-core 2.7 GHz processor with 4 GB RAM and plenty of hard disk space.
 
Thanks for any light you may be able to shed on this!  Terminal output follows...

-Mark
 
> mjpatey@zippy:~$ kdenlive
kdenlive(30482) MainWindow::parseProfiles: RESULTING MLT PATH:  "/usr/share/mlt/profiles/"
kdenlive(30482) initEffects::parseEffectFiles: //  INIT EFFECT SEARCH
kdenlive(30482) Render::Render: //////////  USINGÂ PROFILE:  hdv_1080_50i
kdenlive(30482) Monitor::Monitor: /////// BUILDING MONITOR, ID:  58720755
kdenlive(30482) Render::Render: //////////  USINGÂ PROFILE:  hdv_1080_50i
kdenlive(30482) Monitor::Monitor: /////// BUILDING MONITOR, ID:  58720937
QPainter::fontMetrics: Painter not active
kdenlive(30482) RecMonitor::RecMonitor: /////// BUILDING MONITOR, ID:  58720980
kdenlive(30482) MainWindow::loadPlugins: // PARSING FIOLER:  "/usr/lib/kde4/"
kdenlive(30482) MainWindow::loadPlugins: // FOUND PLUGIN: "libkdenlive_sampleplugin.so" = "/usr/lib/kde4/libkdenlive_sampleplugin.so"
kdenlive(30482) MainWindow::addToMenu: // ADD to MENU ("Countdown", "Noise")
kdenlive(30482) KdenliveDoc::setProfilePath: KDEnnlive document, init timecode from path:  "hdv_1080_50i" ,   25
trying to create local folder /titles: Permission denied
trying to create local folder /thumbs: Permission denied
trying to create local folder /ladspa: Permission denied
kdenlive(30482) KdenliveDoc::KdenliveDoc: KDEnlive document, init timecode:  25
kdenlive(30482) TrackView::slotAddProjectTrack: *************  ADD DOC TRACK  4 , DURATION:  0
kdenlive(30482) TrackView::slotAddProjectTrack: *************  ADD DOC TRACK  3 , DURATION:  0
kdenlive(30482) TrackView::slotAddProjectTrack: *************  ADD DOC TRACK  2 , DURATION:  0
kdenlive(30482) TrackView::slotAddProjectTrack: *************  ADD DOC TRACK  1 , DURATION:  0
kdenlive(30482) TrackView::slotAddProjectTrack: *************  ADD DOC TRACK  0 , DURATION:  0
kdenlive(30482) TrackView::parseDocument: ///////////  TOTAL PROJECT DURATION:  300
kdenlive(30482) Render::setSceneList: // NEW SCENE LIST DURATION SET TO:  0
kdenlive(30482) KdenliveDoc::checkProjectClips: +++++++++++++ + + + + CHK PCLIPS
kdenlive(30482) MainWindow::connectDocument: ///////////////////   CONNECTING DOC TO PROJECT VIEW ////////////////
kdenlive(30482) MainWindow::connectDocument: ///////////////////   CONNECTING DOC TO PROJECT VIEW ////////////////
kdenlive(30482) Render::stop: /////////////   RENDER STOPPED:  "project"
kdenlive(30482) Render::stop: /////////////   RENDER STOP2-------
kdenlive(30482) Render::stop: /////////////   RENDER STOP3-------
kdenlive(30482) Render::start: -----  STARTING MONITOR:  "clip"
kdenlive(30482) Render::start: -----  MONITOR:  "clip"  WAS STOPPED
kdenlive(30482) Render::start: -----  MONITOR:  "clip"  REFRESH
kdenlive(30482) Render::stop: /////////////   RENDER STOPPED:  "clip"
kdenlive(30482) Render::stop: /////////////   RENDER STOP2-------
kdenlive(30482) Render::stop: /////////////   RENDER STOP3-------
kdenlive(30482) Render::start: -----  STARTING MONITOR:  "project"
kdenlive(30482) Render::start: -----  MONITOR:  "project"  WAS STOPPED
kdenlive(30482) Render::start: -----  MONITOR:  "project"  REFRESH
kdenlive(30482) Render::stop: /////////////   RENDER STOPPED:  "project"
kdenlive(30482) Render::stop: /////////////   RENDER STOP2-------
kdenlive(30482) Render::stop: /////////////   RENDER STOP3-------
kdenlive(30482) Render::start: -----  STARTING MONITOR:  "clip"
kdenlive(30482) Render::start: -----  MONITOR:  "clip"  WAS STOPPED
kdenlive(30482) Render::start: -----  MONITOR:  "clip"  REFRESH
kdenlive(30482) Render::resetProfile: reset to same profile, nothing to do
kdenlive(30482) Render::stop: /////////////   RENDER STOPPED:  "clip"
kdenlive(30482) Render::stop: /////////////   RENDER STOP2-------
kdenlive(30482) Render::stop: /////////////   RENDER STOP3-------
kdenlive(30482) Render::start: -----  STARTING MONITOR:  "project"
kdenlive(30482) Render::start: -----  MONITOR:  "project"  WAS STOPPED
kdenlive(30482) Render::start: -----  MONITOR:  "project"  REFRESH
kdenlive(30482) Render::resetProfile: reset to same profile, nothing to do
kdenlive(30482) AddClipCommand::redo: ----  redoing action
kdenlive(30482) ProjectList::slotAddClip: Adding clip with groupid:  ""
kdenlive(30482) Render::getFileProperties: REquested fuile info for: "/home/mjpatey/Desktop/Flip Video/Hannah's Recitatio/VID00001.AVI"
kdenlive(30482) AddClipCommand::redo: ----  redoing action
kdenlive(30482) ProjectList::slotAddClip: Adding clip with groupid:  ""
kdenlive(30482) Render::getFileProperties: REquested fuile info for: "/home/mjpatey/Desktop/Flip Video/Hannah's Recitatio/VID00002.AVI"
kdenlive(30482) AddClipCommand::redo: ----  redoing action
kdenlive(30482) ProjectList::slotAddClip: Adding clip with groupid:  ""
kdenlive(30482) Render::getFileProperties: REquested fuile info for: "/home/mjpatey/Desktop/Flip Video/Hannah's Recitatio/VID00003.AVI"
kdenlive(30482) AddClipCommand::redo: ----  redoing action
kdenlive(30482) ProjectList::slotAddClip: Adding clip with groupid:  ""
kdenlive(30482) Render::getFileProperties: REquested fuile info for: "/home/mjpatey/Desktop/Flip Video/Hannah's Recitatio/VID00004.AVI"
kdenlive(30482) AddClipCommand::redo: ----  redoing action
kdenlive(30482) ProjectList::slotAddClip: Adding clip with groupid:  ""
kdenlive(30482) Render::getFileProperties: REquested fuile info for: "/home/mjpatey/Desktop/Flip Video/Hannah's Recitatio/VID00005.AVI"
kdenlive(30482) AddClipCommand::redo: ----  redoing action
kdenlive(30482) ProjectList::slotAddClip: Adding clip with groupid:  ""
kdenlive(30482) Render::getFileProperties: REquested fuile info for: "/home/mjpatey/Desktop/Flip Video/Hannah's Recitatio/VID00006.AVI"
kdenlive(30482) AddClipCommand::redo: ----  redoing action
kdenlive(30482) ProjectList::slotAddClip: Adding clip with groupid:  ""
kdenlive(30482) Render::getFileProperties: REquested fuile info for: "/home/mjpatey/Desktop/Flip Video/Hannah's Recitatio/VID00007.AVI"
kdenlive(30482) AddClipCommand::redo: ----  redoing action
kdenlive(30482) ProjectList::slotAddClip: Adding clip with groupid:  ""
kdenlive(30482) Render::getFileProperties: REquested fuile info for: "/home/mjpatey/Desktop/Flip Video/Hannah's Recitatio/VID00008.AVI"
kdenlive(30482) AddClipCommand::redo: ----  redoing action
kdenlive(30482) ProjectList::slotAddClip: Adding clip with groupid:  ""
kdenlive(30482) Render::getFileProperties: REquested fuile info for: "/home/mjpatey/Desktop/Flip Video/Hannah's Recitatio/VID00009.AVI"
kdenlive(30482) AddClipCommand::redo: ----  redoing action
kdenlive(30482) ProjectList::slotAddClip: Adding clip with groupid:  ""
kdenlive(30482) Render::getFileProperties: REquested fuile info for: "/home/mjpatey/Desktop/Flip Video/Hannah's Recitatio/VID00010.AVI"
kdenlive(30482) AddClipCommand::redo: ----  redoing action
kdenlive(30482) ProjectList::slotAddClip: Adding clip with groupid:  ""
kdenlive(30482) Render::getFileProperties: REquested fuile info for: "/home/mjpatey/Desktop/Flip Video/Hannah's Recitatio/VID00011.AVI"
kdenlive(30482) AddClipCommand::redo: ----  redoing action
kdenlive(30482) ProjectList::slotAddClip: Adding clip with groupid:  ""
kdenlive(30482) Render::getFileProperties: REquested fuile info for: "/home/mjpatey/Desktop/Flip Video/Hannah's Recitatio/VID00012.AVI"
kdenlive(30482) Render::stop: /////////////   RENDER STOPPED:  "project"
kdenlive(30482) Render::stop: /////////////   RENDER STOP2-------
kdenlive(30482) Render::stop: /////////////   RENDER STOP3-------
kdenlive(30482) Render::start: -----  STARTING MONITOR:  "clip"
kdenlive(30482) Render::start: -----  MONITOR:  "clip"  WAS STOPPED
kdenlive(30482) Render::start: -----  MONITOR:  "clip"  REFRESH
kdenlive(30482) CustomTrackView::mousePressEvent: mousePressEvent STARTED
kdenlive(30482) Render::stop: /////////////   RENDER STOPPED:  "clip"
kdenlive(30482) Render::stop: /////////////   RENDER STOP2-------
kdenlive(30482) Render::stop: /////////////   RENDER STOP3-------
kdenlive(30482) Render::start: -----  STARTING MONITOR:  "project"
kdenlive(30482) Render::start: -----  MONITOR:  "project"  WAS STOPPED
kdenlive(30482) Render::start: -----  MONITOR:  "project"  REFRESH
kdenlive(30482) EffectStackEdit::transferParamDesc: in
kdenlive(30482) CustomTrackView::mousePressEvent: mousePressEvent STARTED
kdenlive(30482) EffectStackEdit::transferParamDesc: in
kdenlive(30482) CustomTrackView::mousePressEvent: mousePressEvent STARTED
kdenlive(30482) EffectStackEdit::transferParamDesc: in
kdenlive(30482) CustomTrackView::mousePressEvent: END mousePress EVENT
kdenlive(30482) CustomTrackView::mousePressEvent: mousePressEvent STARTED
kdenlive(30482) EffectStackEdit::transferParamDesc: in
kdenlive(30482) CustomTrackView::mousePressEvent: mousePressEvent STARTED
kdenlive(30482) EffectStackEdit::transferParamDesc: in
kdenlive(30482) CustomTrackView::mousePressEvent: mousePressEvent STARTED
kdenlive(30482) EffectStackEdit::transferParamDesc: in
kdenlive(30482) CustomTrackView::mousePressEvent: mousePressEvent STARTED
kdenlive(30482) EffectStackEdit::transferParamDesc: in
kdenlive(30482) Render::mltMoveClip: //////  LOOKING FOR CLIP TO MOVE, INDEX:  0
kdenlive(30482) MoveClipCommand::redo: ----  redoing action
kdenlive(30482) CustomTrackView::mousePressEvent: mousePressEvent STARTED
kdenlive(30482) EffectStackEdit::transferParamDesc: in
kdenlive(30482) CustomTrackView::mousePressEvent: mousePressEvent STARTED
kdenlive(30482) EffectStackEdit::transferParamDesc: in
kdenlive(30482) CustomTrackView::mousePressEvent: mousePressEvent STARTED
kdenlive(30482) EffectStackEdit::transferParamDesc: in
kdenlive(30482) Render::mltMoveClip: //////  LOOKING FOR CLIP TO MOVE, INDEX:  2
kdenlive(30482) MoveClipCommand::redo: ----  redoing action
kdenlive(30482) CustomTrackView::mousePressEvent: mousePressEvent STARTED
kdenlive(30482) EffectStackEdit::transferParamDesc: in
kdenlive(30482) CustomTrackView::mousePressEvent: mousePressEvent STARTED
kdenlive(30482) EffectStackEdit::transferParamDesc: in
kdenlive(30482) CustomTrackView::mousePressEvent: mousePressEvent STARTED
kdenlive(30482) EffectStackEdit::transferParamDesc: in
kdenlive(30482) Render::mltMoveClip: //////  LOOKING FOR CLIP TO MOVE, INDEX:  4
kdenlive(30482) MoveClipCommand::redo: ----  redoing action
kdenlive(30482) CustomTrackView::mousePressEvent: mousePressEvent STARTED
kdenlive(30482) EffectStackEdit::transferParamDesc: in
kdenlive(30482) CustomTrackView::mousePressEvent: mousePressEvent STARTED
kdenlive(30482) EffectStackEdit::transferParamDesc: in
kdenlive(30482) CustomTrackView::mousePressEvent: END mousePress EVENT
kdenlive(30482) CustomTrackView::mousePressEvent: mousePressEvent STARTED
kdenlive(30482) EffectStackEdit::transferParamDesc: in
kdenlive(30482) CustomTrackView::mousePressEvent: END mousePress EVENT
kdenlive(30482) CustomTrackView::mousePressEvent: mousePressEvent STARTED
kdenlive(30482) EffectStackEdit::transferParamDesc: in
kdenlive(30482) CustomTrackView::mousePressEvent: END mousePress EVENT
kdenlive(30482) CustomTrackView::mousePressEvent: mousePressEvent STARTED
kdenlive(30482) EffectStackEdit::transferParamDesc: in
kdenlive(30482) CustomTrackView::mousePressEvent: END mousePress EVENT
: Fatal IO error 9 (Bad file descriptor) on X server :0.0.
Unable to start Dr. Konqi
mjpatey@zippy:~$ 

---

### Post by skullmunky on 2009-05-13
I don't have an answer, sadly, but have you tried posting on the kdenlive forum / bug tracker also?  the developers are pretty responsive.

Dr. Konqui (drkonqi) is the KDE crash reporter.

The fatal IO error looks like it might be a symptom, rather than a cause; just the usual stuff that an X app says when it crashes.

---

### Post by wkulecz on 2009-05-14
I know its  no consolation, but you get further before it crashes than I do!

I keep a Windows 2000 box running Sony Vegas Movie Studio 7(?, last version to support W2K) Platnium to meet my video editing needs.

My old Sonic Foundry Vegas Video 3 does seem to run fine in a Virtualbox VM, but I had to resort to "cracks" to activate it and the MPEG encoder, since the SF servers are long gone.

Since I can't seem to find current motherboards which have Windows 2000 drivers anymore, when this dies or I upgrade to HD, I'll have to decide on Windows 7 or a Mac if Linux isn't there yet for video editing.

--wally.

---

### Post by mjpatey on 2009-05-14
This seems to be the consensus, unfortunately.  My temporary solution right now is to copy my files over to my wife's laptop running Vista and cobble something together with Windows Movie Maker.

This is a big, gaping hole in the Linux world!  I do understand there are programs that *work*, but they're not on par with their Windows and Mac counterparts by a long shot.  Kdenlive looks like the most promising entry so far, but when inquiries here and on the Kdenlive forums lead nowhere, it's obvious there's a lot of work to be done.

I realize Kdenlive is a KDE app, but I wonder if the Ubuntu Studio team would consider working with the Kdenlive team to create a viable platform, a marriage of full-featured video editing and an OS tuned to allow it to run seamlessly?

That would be awesome.

By the way, does anybody have a POSITIVE video editing experience on Ubuntu to share?  Do any of the aforementioned apps (but most importantly Kdenlive) work better on 32-bit systems, maybe?

---

### Post by pixel :-) on 2009-05-14
kdenlive is very buggy, this behavior is normal for the program unfortunatly.

Use something on wine.

---

### Post by mjpatey on 2009-05-14
Actually, I've tried Windows Movie Maker on Wine, and it appeared to install correctly, but nothing happens when I run it.  I also tried under Wine an old free version of Avid software; I forget the exact name of it, and it did run, but was missing some key functionality... like sound.

I'll check the Wine compatibility list and see what, if anything, can be done in that area.  Thanks for the idea!

---

### Post by cotcot on 2009-05-16
You have tried a lot. If that all does not work than it looks like the problem has nothing to do with the editors as such but with some tools all of them use.
If you still have some energy to try something else I could recommend [[COLOR="Blue"]Blender VSE[/COLOR]]("http://wiki.blender.org/index.php/Doc:Manual/Sequencer/Usage"). It is generally very stable. 
I haven't seen Cinelerra on your list neither. Its stability improved a lot  with the [[COLOR="Blue"]cinelerra-4  version[/COLOR]]("http://cinelerra.org/getting_cinelerra.php").

---

### Post by skullmunky on 2009-05-16
So, alas, I still don't have an answer to why yours is crashing; but, I can say, I just installed kubuntu 9.04 (32bit) and the kdenlive 0.7 from the repositories, and found to my delight that I could do a whole bunch of editing without any crashes, bugs, or other weirdness at all.  I've been trying out kdenlive every so often for a while now, and this was remarkably more stable and featureful than previous versions. 

I didn't do anything special, it all just worked out of the box - editing, effects, titles, importing things like flash FLV files, rendering to mp4.  Also, this was on a 5 or 6 year-old cheapo HP laptop, so I was pleased to see it runs well on lower-end hardware.

Just some encouragement, I guess, that it -is- possible for it to run well.  It's often hard to tell if you're having problems because there's something you can fix or update, or if the app is just inherently buggy.

---

### Post by Regele IONESCU on 2009-05-17
Cinelerra works pretty fine for me. The repository is at:

[http://akiradproject.net/repository]("http://akiradproject.net/repository")


Install the version that suits your needs.

God help us all!
Honestly,
Christian I. Ionescu

---

### Post by mjpatey on 2009-05-17
You folks who suggested Cinelerra must be psychic!  I'm revisiting this thread after just installing the latest "CV" (community version) of Cinelerra form the akiraproject repo, and it works beautifully!

Yes, it's a little more involved, but I'm used to working with pretty deep pro audio apps, so Cinelerra's level of complexity is quite all right with me!  Before the repo mentioned above existed, I'd tried installing Cinelerra from source (probably a few versions ago, too), and just for the life of me couldn't get it working.

The notes [here]("http://cinelerra.org/getting_cinelerra.php#jaunty") will get you going, right down to specific settings to make sound work in recent versions of Ubuntu (which use PuleAudio).

Skullmonky, thanks for the positive report on Kubuntu 32-bit... if I need something simpler/quicker down the line, I'll keep Kdenlive in mind.  It looks like one heck of a great app... add the stability, and I'd probably prefer it over Cinelerra for the basic stuff I'm doing.

Thanks, everybody!

-Mark

---

### Post by rulet on 2009-05-17
Kdenlive wasn't worked in Ubuntu under Gnome because it's made for KDE. There is else another project for videoediting named LiVes --
they say soon they will make deb package for Ubuntu...

---

### Post by mjpatey on 2009-05-17
rulet,

If it's in the Ubuntu repos, kdenlive should install with all the necessary KDE libraries (and it certainly does add a boatload of them).  I've also tried LiVes, and it won't start, reporting a missing file: libmjpegutils-1.9.so.0 (though a quick check reveals I do, in fact, have that exact file).

Thanks, I will try installing Kubuntu 9.04 on a separate partition, and give Kdenlive a shot over there.  But for now, Cinelerra (installed via the akiradproject repo) is working just fine!

-Mark

---

### Post by cotcot on 2009-05-17
You do not need to install kubuntu. Kdenlive works fine on ubuntu. As written by a previous poster the necessary dependencies are installed in ubuntu when you install kdenlive with synaptic.
It running OK on my box.

---

### Post by mjpatey on 2009-05-17
cotcot, I hadn't read that before... it must be in another thread.  I will give that a shot!  So installing via Synaptic is more thorough than installing with apt-get?  I always thought they used the same backend.

---

### Post by Chrissss on 2009-05-17
> **mjpatey said:**
> cotcot, I hadn't read that before... it must be in another thread.  I will give that a shot!  So installing via Synaptic is more thorough than installing with apt-get?  I always thought they used the same backend.

Yes, they do. It doesn't matter what you use.

---

### Post by mjpatey on 2009-05-17
That was my understanding, too, Chrisss... though I *have* heard proponents of "aptitude" versus "apt-get".  Can't remember on what grounds, though... now for some Googling...

---

### Post by rulet on 2009-05-18
Well, it is sad to say, but Kdenlive converts but much more slow then Nero Vision...

---

### Post by cotcot on 2009-05-18
> **mjpatey said:**
> cotcot, I hadn't read that before... it must be in another thread.  I will give that a shot!  So installing via Synaptic is more thorough than installing with apt-get?  I always thought they used the same backend.

Sorry that I was not clear. I mentioned the first sentence in post 14.
And for synaptic or apt-get : both work to install kdenlive.

---

### Post by mjpatey on 2009-05-18
Well, now I've tested two other Kdenlive setups on my system.  First, I uninstalled it with apt-get and re-installed with aptitude.  It looked promising, in that during the installation, aptitude threw up a warning that certain libraries requested by Kdenlive were now on to a newer version, and gave me the option to use Kdenlive's specified versions rather than the newer versions in the repo.  I began using Kdenlive, and it worked great for quite a while!  Then it puked on me when I played to the end of the last clip in my timeline (a favorite place for it to lock up in previous attempts).

So now, I've installed Kubuntu on a spare partition, and am posting this from within that installation.  I installed Kdenlive with aptitude in Kubuntu, and all the problems I was having under Gnome have vanished!  It hasn't locked up (yet), the video hasn't frozen (yet), and I'm able to actually render to a video file, and save a project, and the program doesn't crash!  And the rendered files play!

But under this setup, I have no audio in Kdenlive.  The rendered video files include the audio, but none plays back during editing in Kdenlive.  Has anybody heard of this problem, and do you know how to fix it?

-Mark

---

### Post by wkulecz on 2009-05-19
I tried Ubuntu 9.04, virgin install, then apt-get install kdenlive and apt-get install dvdauthor.

Could actually run kdenlive!  But....  put a couple of 2-minute DV clips on the timeline, trimmed them, couldn't find crossfade.  Got fade to black to work, couldn't get fade from black to do anything.  Tried to render the project, chose one of the few outputs that wasn't X'd out in the selcetion box and it seemed to be working, unfortunately when I came back a while later I was greated with a "Render has crashed" dialog box :(

Progress of sorts I guess, but fundamentally useless to me.


My solution:  Fry's had Sony Movie Studio 9 Platnium "on sale, free after rebate" ($70 if you just buy it), I got that, and downloaded the Windows7 RC1 beta.  Installed it and the Movie Studio 9 software and everything just worked (same machine I tried 9.04 and Kdenlive on).  I started with the short clips (all type 1 DV) I tried in Kdenlive and a few other short ones I wanted to trim and make into mp4.  No problems and the 640x480 "Ipod profile" mp4 outputs all play fine on my wife's Ubuntu 8.04 box over the wireless N network!  I left for work with a 2 hr project rendering (its near Windows7 minimum spec machine).

So it looks like I'm set until the Win7 RC1 expires in March 2010.  I'm not too keen on Windows 7, much better than Vista, though, but as a dedicated video and photo editing box, I could live with it.

I may give the Kubuntu 9.04 & Kdenlive a try over the weekend.

Does the current Cinelerra work with DV type 1 files that are in an *.avi wrapper?  Earlier versions only could import DV in a quicktime *.mov format.  Kino could convert them, but its not a practical solution for me, especially since Cinelerra was very crash prone and much harder to use than I'd like.  I'd give it a try again if it can work with the DV files I have.

--wally.

---

### Post by mjpatey on 2009-05-20
Wally,

Give it a shot... it doesn't like my .MOV files from the Flip camcorder, but it does take the DV-formatted AVIs that Kino (or something else?) converted them to before it could handle them.  So it's fine with whatever kind of DV files those are (not sure exactly).

I can't make any video editing software work in a VM because my sound hardware doesn't work in the guest OS, no matter what I've tried.

In Kdenlive, crossfade is now done this way:  put your second clip on an adjacent track.  When you hover over the first clip's diagonal red arrow, your pointer will turn to a finger pointing up; when it does, click the red arrow, and it will create an automatic crossfade.

-Mark

---

### Post by wkulecz on 2009-05-20
> **Chrissss said:**
> Yes, they do. It doesn't matter what you use.

My experience contradicts this somewhat, but I can't explain what went wrong.

Basically automatic updates has screwed the pooch several times for me and left packages synaptic couldn't update.

Doing:
apt-get update
apt-get upgrade 
has so far always fixed things.

Worst was some how Samba-common and Samba got out of sync version wise and all my shares became read-only!  Drove me nuts!

Synaptic couldn't fix it but that is where I noticed the version mismatch.

--wally.

---

### Post by mjpatey on 2009-05-22
Good news, everyone!  If you haven't read, the video editing app "Pitivi" has just received a refresh, and a new release is expected Monday, 5/25.  The release candidate can be installed from a Launchpad PPA at the following URL:

[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

The page contains instructions on how to install from a PPA if you're not familiar with the process (don't worry, no compiling from source or worrying about dependencies).  I've installed it on my 64-bit vanilla Jaunty installation, and it works!  I had one strange Gstreamer error the first time I tried dragging a clip from the library to the timeline (which caused video to stop playing back from the timeline), but once I played a clip directly from the library, timeline playback has worked flawlessly ever since.

Pitivi is light on features right now.  At this point, it allows you to import clips into the library, drag them to the timeline, trim them, move them around and render an output file.  No transitions, no text overlay, etc.  A very simple nonlinear editing experience, but it works!  And according to this story:

[http://lunduke.com/?p=571](http://lunduke.com/?p=571)

...Pitivi's development has been given a boost by an outside company, so hopefully more features will be added quickly!

---

### Post by wkulecz on 2009-05-27
> Kdenlive wasn't worked in Ubuntu under Gnome because it's made for KDE.

There seems to be something to this.  Perhaps an error in the KDE dependencies for Ubuntu vs. what gets installed with Kubuntu.

I've tried Kdenlive on 6.06, crashes without doing anything.  8.04, crashes on one system and on a second it appears to run and render, but the renders cut off early leaving a long sequence of black at the end of the finished video.  On 9.04 it appeared to run fine but rendering crashed.

So I installed Kubuntu 9.04 over the long weekend, let automatic updates do its thing and then did apt-get install kdenlive dvdauthor.

KDenlive appears to work fine.  I put three very different sized MJPEG videos on the timeline, did a few cross fades and exported to a variety of mp4 sizes and one HDV.  All seem fine.

Kdenlive will blow away windows movie maker once it stops crashing on most systems.  I was most impressed by the way it seamlessly handled the mixed resolutions on the timeline.  I didn't like the choice it made for for the final HDV aspect ratio.  I had videos of 1280x720, 364x244 and 244x192 from my Casio I would have prefered the low res be pillarboxed in the high res frame, instead it letterboxed the hi res video.  KDE's "Dragonplayer" is not very good in that I couldn't see a way to force 1:1 pixel display to see the final output, but looking at it in windows media player caused me to conclude a sub-optimal choice was automatically made for the aspect ratios, although the video looked pretty good overall.

Anyone know where to get the Kdenlive help files?  The help menu is pretty useles without them, hopefully there is a way to change the render choices to my taste.

I dislike KDE and its definitely not as stable as Gnome.  I had to install the restricted Nvidia drivers to get the full 1920x1200 of my display and the recomended drivers crashed KDE.  A repair and install of the older 170 series Nvidia drivers seems to work fine with both KDE and Kdnelive.

--wally.

---

### Post by Bungo Pony on 2009-05-27
I've had very little success with kdenlive. It has a really nice interface, but sound gets cut off when I export video. Oh yeah, and it crashes a lot.

The most success I've had is with Open Movie Editor. I've made some very flawless videos with it. It's by no means perfect, but it gets the job done, and it does it quite well. It took me a bit to get used to it (and find the zoom controls buried at the bottom right hand of the screen), and figure out which codecs worked the best, but everything works really well.

I'd suggest spending a bit more time with Open Movie Editor. All the other video editors I've tried on Linux were buggy, crashy, and didn't have the features I wanted. Cinelerra requires me to read the manual, and I currently don't have time for that.

---

### Post by mjpatey on 2009-05-27
Bungo-

At your suggestion, I just revisited Open Movie Editor.  I can see how it could be useful, if only on a really basic level (though more feature-filled than Pitivi at this point!)... but I can't get it to play.  I can move clips around, do crossfades, titles, but can't play the timeline!  If anybody has a fix for this, great... but I'm inclined not to pursue it, to be perfectly honest.  Getting tired... maybe I need some sleep!

I'm just hoping not too many Linux newcomers notice the messy state of affairs in Linux video editing.  Hopefully, one or two of these well-intentioned apps will take the lead soon!  As I mentioned, Pitivi is currently, I believe, going about it the right way:  building a strong, stable, though basic app first, and (I hope!) adding functionality once all's well with the basics.  As far as a feature wishlist, I'd love to see automatic crossfades as implemented in Open Movie Editor and many other video editing apps.  Just drag a clip over the end of another clip, and voila!  Crossfade.  Drag the clips to change the length of the overlap.  Then bring in other transitions, titling and clip- and track-based effects.  Then keyframe panning, zooming, audio levels, and other keyframable effects.  Go, Pitivi, go!!!

Kdenlive is currently, feature-wise, more like what I can see myself using, but it just crashes *so* much.  Cinelerra also has its strong points, but is really picky about what filetypes it will import, and has some awkward UI issues.

---

### Post by Ian Clark on 2009-06-07
I just tried the older version (0.11.1) instead of 0.13.01 and it was encouraging. Pretty neat, actually...very simple.  Didn't crash or anything.  Could import what I wanted (avi, mpg).  Didn't understand what the "trim" button was doing, or what was going on.  Hit "trim" and nothing seemed to happen.  Great interface otherwise, though. 

It was cool how it said, "click add to put clips here" and then you do that, then it reads on the timeline"drag clip here to edit" etc.  Steps you through what you're doing. I didn't try exporting what I did, because I couldn't use any features on it.

How can the new Pitivi 0.13 be installed on 8.10?

---

