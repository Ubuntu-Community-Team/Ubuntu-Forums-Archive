---
title: "How do you edit video?"
date: 2008-07-11
forum: The Cafe
---

### Post by wersdaluv on 2008-07-11
We know that Linux lacks a competent video editing software. The main reason could be the lack of focus on the development of video editing programs for Linux. Cinerella is powerful but the interface is... jurassic. It's also true for an app like Open Movie Editor.

Windows has a nice and simple Windows Movie Maker and OS X has iMovie.

What do you use when you edit videos? Do you settle with Linux apps? Do you use another OS for that? Do you use a webapp (if there is such)?

---

### Post by zmjjmz on 2008-07-11
Open Movie Editor is just fine, even if the interface is horrible.
KDEnlive is on it's way too.

---

### Post by atomkarinca on 2008-07-11
You're right about Cinelerra's interface but it gets the job done and that's enough for me.

---

### Post by ad_267 on 2008-07-11
Avidemux or kdenlive

---

### Post by lisati on 2008-07-11
At the risk of "swearing": Mainly Pinnacle Studio Plus, occasionally Windows Movie Maker, occasionally Sonic MyDVD 

(Yes, they''re all Windows programs)

---

### Post by fatality_uk on 2008-07-11
Just a thought. Is there an exe for Windows movie maker. I seem to remember it being an auto install from their site.

---

### Post by ChameleonDave on 2008-07-11
> **wersdaluv said:**
> Cinerella is powerful but the interface is... jurassic.
Isn't that a fairytale character?

Do you mean [Cinelerra]("http://cinelerra.org/")?

I've tried Kino, and it's relatively intuitive.  Avidemux and Kdenlive don't work for me.  I agree that liber and gratis editing software for video needs a lot of work.

---

### Post by rsambuca on 2008-07-11
I am not sure how you can really compare Cinelerra and Windows Movie Maker.  Cinelerra is much more powerful, and as such, has a much more complex interface.  If you want something with a simple interface for use in linux, try Avidemux.  It is in the standard Ubuntu repos.

---

### Post by fatality_uk on 2008-07-11
For me Lives is the current best of the bunch!!

---

### Post by tubasoldier on 2008-07-11
I bought a mac. It will be a while before video editing in Linux is worth talking about.

---

### Post by hessiess on 2008-07-11
[> It seems lots of people are wishing for Windows Movie Maker or iMovie for Linux. Well, the last time I looked at iMovie it was unable to import standard MPEG-2 video. So if you had such a stream and wanted to make a DVD from it, you had to transcode to Quicktime, import into iMovie, do the editing and then have iMovie transcode the result to MPEG-2 again. Ridiculous. These applications are nothing but toys that pretend to be video editors.]("http://ubuntuforums.org/showthread.php?t=831672&page=2")

Personaly I use Blender(editior) and FFmpeg(re-encoding formts). This works well, but tackes time to get use to.

---

### Post by zmjjmz on 2008-07-11
> **tubasoldier said:**
> I bought a mac. It will be a while before video editing in Linux is worth talking about.

Agreed.
iMovie is pretty win (well, the old one is).

---

### Post by tubasoldier on 2008-07-11
> **zmjjmz said:**
> Agreed.
iMovie is pretty win (well, the old one is).

Absolutely. You can still get the '06 version. Its now called iMovie HD. It also checks to see if you have iLife '08 installed before it will install. iMovie '08 is a terrible disappointment.

---

### Post by cardinals_fan on 2008-07-11
I don't edit videos.  Just that simple :)

---

### Post by munchkinmunchkin on 2008-10-02
I've just started using LiVES video editor.

A few problems, but I got results in different video formats.

---

### Post by 3rdalbum on 2008-10-02
I use Kdenlive. Apart from the occasional crash it does what I want it to do.

I must say that I hate iMovie - people say that Linux software doesn't have the features of the competition, but practically every Linux video editor has more features than iMovie.

iMovie tries to make things so simplistic, it's actually difficult to use. Kdenlive doesn't have a huge featureset, but at least you can do pretty much anything via a combination of its editing tools.

---

### Post by wersdaluv on 2008-10-02
> **3rdalbum said:**
> I use Kdenlive. Apart from the occasional crash it does what I want it to do.

I must say that I hate iMovie - people say that Linux software doesn't have the features of the competition, but practically every Linux video editor has more features than iMovie.

iMovie tries to make things so simplistic, it's actually difficult to use. Kdenlive doesn't have a huge featureset, but at least you can do pretty much anything via a combination of its editing tools.
Just installed it. I can't even start it because it keeps on crashing

---

### Post by qazwsx on 2008-10-02
> **wersdaluv said:**
> Just installed it. I can't even start it because it keeps on crashing
Clear your kdenlive config files (look into $HOME/.kde/share/config). The very first dialog will cause problems if you pick certain format.

---

### Post by Ubuntiac on 2008-12-15
Many people are complaining about Kdenlive (from the repo's) being unstable without realising that Ubuntu's repo version was an SVN snapshot over a year old not intended for public use. The current version (0.7) and the next version (0.7.1 due in a couple of weeks) have been rewritten, almost from the ground up and are much more stable and faster, too.

If you check the link at the end of my signature, you'll see that there should be Intrepid packages in the next couple of weeks as well. :)

Alternatively, there's a GUI app that installs the latest version from SVN for you easily. There's instructions in the Ubuntu community wiki docs on using it.

---

### Post by tadcan on 2008-12-15
Does Kdenlive support capturing from decks. (A machine to capture a DV tape) I have a loan of a JVC BR-HD50 deck, which is not recognised by version 0.7.0. I applied to join the kdenlive forum but have not been accepted yet so I'm asking here.

---

### Post by TBOL3 on 2008-12-15
When people talk about there being no video software on linux, I have to have an inward chuckle, because there is..

Blender really gets an A when it comes to video editing.  It even beats out several cheap packages that I've seen on other platforms, and it's not until you get well into three figures (sometimes even four) that the competition begins to catch up.

Now, the only thing that blender lacks, is the ability to import from a digital camera (well, maybe it doesn't lack it, but I don't know how).  So, I import it using kino, which splits shots into individual files, making it very easy to import, and play with. 

I then render the whole thing via ffmpeg (which is built into blender)

---

### Post by hessiess on 2008-12-15
> **TBOL3 said:**
> When people talk about there being no video software on linux, I have to have an inward chuckle, because there is..

Blender really gets an A when it comes to video editing.  It even beats out several cheap packages that I've seen on other platforms, and it's not until you get well into three figures (sometimes even four) that the competition begins to catch up.

Now, the only thing that blender lacks, is the ability to import from a digital camera (well, maybe it doesn't lack it, but I don't know how).  So, I import it using kino, which splits shots into individual files, making it very easy to import, and play with. 

I then render the whole thing via ffmpeg (which is built into blender)

As far as im aware, Blender cannot import video directilly. Though I guess it wouldn't be to hard to add, by integrating DVGrab, for example.

---

### Post by Onyros on 2008-12-15
LiVES is pretty good, and I haven't really bothered with Cinelerra, because I've always used the former.

---

### Post by derekr44 on 2008-12-15
For me, it's Cinelerra and Avidemux.

---

### Post by wersdaluv on 2008-12-15
Very easy to say that. Just installed blender. When I ran it, I didn't understand anything at all. differently when I ran Windwos Movie Maker.

---

### Post by bruce89 on 2008-12-15
> **wersdaluv said:**
> Very easy to say that. Just installed blender. When I ran it, I didn't understand anything at all. differently when I ran Windwos Movie Maker.

It's a 3D modelling program that can render films of 3D proportions.

I use PiTiVi for minor editing (hope it will improve) and Kino for DV stuff (wish it used GStreamer).

---

### Post by Ubuntiac on 2008-12-15
Applied to join? It's completely automated, so you certainly haven't been snubbed (well, by any human anyway). The website was only just upgraded and has had a couple of password issues. If you let me know the username you signed up as, I'll pass it onto the webmaster.

Anyway, as to your actual question, Kdenlive uses DVgrab to capture, so anything DVgrab can handle, Kdenlive can. Really that should be just about any Firewire DV device. The only trick is that there can be some permission issues. I'll explain:

When you plug in and turn on a DV device like a deck / camera, it Ubuntu creates the device /dev/dv1394 which is owned by disk / video. You need to add a new group say (dv1394), add yourself and /dev/1394 to it. It's pretty easy to google how to do this.

If you only capture occasionally then that's all you need, but Ubuntu deletes and recreates that everytime the device is turned on, so a UDEV rule is in order if you don't want to chmod /dev/dv1394 every time you reboot. Once again google udev plus dv1394 plus ubuntu and you'll find howto's.

I should note that this isn't a Kdenlive thing, this is a DV capture on Ubuntu thing, so any other program not running as root has the same issues (and giving programs access to DV1394 as root is a *major* security problem).

---

### Post by doorknob60 on 2008-12-15
THe only Linux one I can stand using is Kdenlive (which is often buggy).I typically use WMM in Windows, unfortunately.

---

### Post by Ubuntiac on 2008-12-16
> **doorknob60 said:**
> THe only Linux one I can stand using is Kdenlive (which is often buggy)

Even the newest Kdenlive has bugs to iron out, but can I ask which version you're talking about there? The version in the Ubuntu repo's is an SVN grab never meant for public release that is over a year old (0.6svn).

0.7 is a near complete rewrite using different underlying libraries (KDE4 over KDE3, also a near complete rewrite). I'm not saying that 0.7 is perfect, but there are many, many people spouting that Kdenlive is so buggy who's opinion is based on very, very outdated versions.

At the end of my signature is a link to a launchpad packaging request. If you haven't tried 0.7, it might be worth looking at the comments in there about it.

If you can try the Kdenlive Builder Wizard at KDE-apps.org which builds the most stable version currently (0.7.1 from SVN).

---

### Post by tadcan on 2008-12-16
After I filled in the form I was sent an email.

> tadcan,

Thank you for registering at Kdenlive. Your application for an account is currently pending approval. Once it has been approved, you will receive another e-mail containing information about how to log in, set your password, and other details.


--  Kdenlive team

Thanks for explaining about DVgrab. The deck wasn't recognised by Ubuntu so hopefully its possible. Back to google!

---

### Post by billgoldberg on 2008-12-16
> **wersdaluv said:**
> We know that Linux lacks a competent video editing software. The main reason could be the lack of focus on the development of video editing programs for Linux. Cinerella is powerful but the interface is... jurassic. It's also true for an app like Open Movie Editor.

Windows has a nice and simple Windows Movie Maker and OS X has iMovie.

What do you use when you edit videos? Do you settle with Linux apps? Do you use another OS for that? Do you use a webapp (if there is such)?

The interface may look outdated but these programs work just fine. (if you can get them installed correctly).

---

### Post by igknighted on 2008-12-16
> **wersdaluv said:**
> We know that Linux lacks a competent video editing software. The main reason could be the lack of focus on the development of video editing programs for Linux. Cinerella is powerful but the interface is... jurassic. It's also true for an app like Open Movie Editor.

Windows has a nice and simple Windows Movie Maker and OS X has iMovie.

What do you use when you edit videos? Do you settle with Linux apps? Do you use another OS for that? Do you use a webapp (if there is such)?

Cinelerra isn't a bad interface if you truly need all the features it offers.  However, 99.9% of users have no need for an app with as many features as Cinelerra and so it feels clunky.  Remember cinelerra was designed for professionals, not ordinary users.

lives, Kdenlive and other programs are on the way, and there are some abandoned projects (pitivi, kino, etc.) that are usable.  In fact, kdenlive 0.7 is absolutely tremendous (IMO).

I don't feel like I "settle" with linux apps.  I don't think there is anything special about imovie, or wmm for that matter.  And I would never pay for a program like final cut or vegas because I simply don't use it enough.  I think that the linux apps give me more features at a price that a "once in a while" user can handle.

---

### Post by TBOL3 on 2008-12-16
> **wersdaluv said:**
> Very easy to say that. Just installed blender. When I ran it, I didn't understand anything at all. differently when I ran Windwos Movie Maker.

You were seing the default screen, which is a 3d modeller.  Click on the button at the top that says 2-Model.  And then click on 4-Sequence.  Maybe you can understand that a bit more.

---

### Post by hessiess on 2008-12-17
> **TBOL3 said:**
> You were seing the default screen, which is a 3d modeller.  Click on the button at the top that says 2-Model.  And then click on 4-Sequence.  Maybe you can understand that a bit more.

or hit ctrl + right 2 times. everything in blender is based on keyboard short cuts, which makes it very fast to use.

---

