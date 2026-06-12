---
title: "Fox TV On Demand"
date: 2007-04-09
forum: The Cafe
---

### Post by forrestcupp on 2007-04-09
On myspace.com, the Fox network has TV On Demand where you can watch the latest episode of some of their popular tv shows.  I am a big 24 fan, and would like to be able to watch it there if I miss an episode.  I have Flash for Linux, the w32codecs, real player, and quicktime all installed.  But the website detects that I am not using Windows and won't let me play the show.  I even tried running MS Internet Explorer with wine, and it still wouldn't work.

So does anyone have any ideas for a workaround, or a way to fool it into working with Linux?

---

### Post by josephus on 2007-04-09
have you tried the user agent switcher extension in firefox?

---

### Post by Hendrixski on 2007-04-09
Why should you suffer because some idiot got paid too much money to create a website that doesn't work.  If they want your business they should adapt to you!

Email them and tell them that they are losing money because it doesn't work on Linux.  Tell your friends to email them, and make sure they know how much money they're losing.  Even if it's a free service, they're not reaching their potential customer base, and they're not showing the comercials (which equals dollar revenue).

---

### Post by yabbadabbadont on 2007-04-09
It is probably a matter of Windows DRM being used with the videos.

---

### Post by mips on 2007-04-09
Lol, it brings up the player screen for me but tells me the service is not available for people outside the USA. I will try it via proxy/anonimizer later.

---

### Post by chollis888 on 2007-04-09
It's because it has to install client software. Under Windows it tries to install:

qmpsetup_win_ie_07010901.exe

I dont trust myspace enough to install software from it. It's hard enough keeping the hijackers from stealing my page. Noway I'd give them access to my home network.

---

### Post by forrestcupp on 2007-04-09
Well, I've used it on a Windows computer, and it never caused me any trouble.  I wonder if there's any way to get that file working under wine.

About emailing them, I might do it, but I really doubt if it will do any good.  There aren't enough Linux users that want to use that website to make them care.

---

### Post by hkgonra on 2007-04-09
Instead of wine why not run windows in vmware ?

---

### Post by BarfBag on 2007-04-09
Other networks are doing this as well.  ABC has free streams of shows, and I believe NBC does as well.  MySpace sucks, though.  I can barely log-on to my account.  Why would I put myself through the hell of trying to watch streaming video on the same server?

---

### Post by warp99 on 2007-04-09
I downloaded and installed the qmpsetup_win_ie_07010901.exe using Wine. It's a library file titled "Move Networks Player for Internet Explorer". Some more information from Move Networks:

> **Fast and Simple Video Encoding**

The process of encoding video for multiple bandwidths (dial-up, wireless, broadband) and target platforms (cell phone, laptop, desktop, large screen TV) is managed through a single process called &#8220;Quantum Simulcoding.&#8221; This revolutionary process leverages hardware clustering and software pipelining to prepare video for on-demand or &#8220;live&#8221; streaming without the limitations imposed by CPU processing power.

[http://www.movenetworks.com/simulcode.html](http://www.movenetworks.com/simulcode.html)

So it looks like it's just an end to end solution for streaming video. You should be able to install IE under Wine, then install the Move Network codec since it's only two files: library file (*.dll) and the uninstaller. I know for a fact that IE 6 will install under Wine. IE ran on my Edgy  64 machine without a problem. Check back to let us know on your progress.

Edit: Don't feel bad since the codec doesn't run on Vista either.

---

### Post by warp99 on 2007-04-10
I got this to work pretty easy first try. I downloaded Firefox 2.0 for Windows, installed it under wine, went to the Fox on demand site which prompted me to install Adobe Flash. I restarted Firefox to load Flash, for some reason it would not run until I restarted. Download the Move Networks program qmpsetup_win_mozilla_07010901.exe and installed it using Wine and viola! Instant high definition television from Fox 24.

I don't under why they don't make a library file for Linux because they make one for OS X Intel and PPC. Here is the error message:

> We're sorry, but only the following operating systems are supported at this time:

Microsoft Windows 2000/XP/Vista
(Intel) Apple Macintosh OS X or later
(PPC) Apple Macintosh OS X or later

Please check back soon for support for other operating systems

We should complain to the client list on Move Networks:

The CW:
[http://video.cwtv.com/support/feedback.html](http://video.cwtv.com/support/feedback.html)

Fox Interactive Media (myspace.com)
[http://www.myspace.com/index.cfm?fuseaction=misc.contact](http://www.myspace.com/index.cfm?fuseaction=misc.contact)

ParkCity.TV
[email]pctv-support@movenetworks.com[/email]

BYU.TV
[http://www.byu.tv/support/feedback.html](http://www.byu.tv/support/feedback.html) 

:guitar:

---

### Post by banjobacon on 2007-04-10
I would stop downloading 24 if Fox had a normal Flash based video player like ABC.

I've *thought* about writing an email.

---

### Post by forrestcupp on 2007-04-10
> **warp99 said:**
> I got this to work pretty easy first try. I downloaded Firefox 2.0 for Windows, installed it under wine, went to the Fox on demand site which prompted me to install Adobe Flash. I restarted Firefox to load Flash, for some reason it would not run until I restarted. Download the Move Networks program qmpsetup_win_mozilla_07010901.exe and installed it using Wine and viola! Instant high definition television from Fox 24.

Wow, thank you.  I made progress, but I couldn't get it to work.  At least it's not telling me I have an unsupported OS anymore.  When the Windows version of Firefox downloaded qmpsetup_win_mozilla_07010901.exe, I tried to open it and nothing happened.  I also tried to run it from the harddrive with wine, and still nothing happened.  The video still said loading, like it was still waiting on qmpsetup to run.

edit:

When I run it from wine in a terminal, this is the beginning of the output it gives me.  Any ideas?

wine: Call from 0x7ed192ea to unimplemented function riched20.dll.RichEdit10ANSIWndProc, aborting
wine: Unimplemented function riched20.dll.RichEdit10ANSIWndProc called at address 0x7ed192ea (thread 002c), starting debugger...
Unhandled exception: unimplemented function riched20.dll.RichEdit10ANSIWndProc called in 32-bit code (0x7bc39ffc).

---

### Post by warp99 on 2007-04-10
> **forrestcupp said:**
> Wow, thank you.  I made progress, but I couldn't get it to work.  At least it's not telling me I have an unsupported OS anymore.  When the Windows version of Firefox downloaded qmpsetup_win_mozilla_07010901.exe, I tried to open it and nothing happened.  I also tried to run it from the harddrive with wine, and still nothing happened.  The video still said loading, like it was still waiting on qmpsetup to run.

edit:

When I run it from wine in a terminal, this is the beginning of the output it gives me.  Any ideas?

wine: Call from 0x7ed192ea to unimplemented function riched20.dll.RichEdit10ANSIWndProc, aborting
wine: Unimplemented function riched20.dll.RichEdit10ANSIWndProc called at address 0x7ed192ea (thread 002c), starting debugger...
Unhandled exception: unimplemented function riched20.dll.RichEdit10ANSIWndProc called in 32-bit code (0x7bc39ffc).

I had Firefox for Windows open to the Fox on Demand page and at the same time ran qmpsetup_win_mozilla_07010901.exe using Wine. Once it was finished installing I clicked on play video in the browser and everything "just worked".

I am using Feisty x86_64 with Wine from the repo's sponsored by Doc.Horn. Here's the link with instructions to enable these repos:

[http://ubuntu.moshen.de/](http://ubuntu.moshen.de/)

If I can get x86_64 to run you should be able to get i386 to run without any problems. Wine is version 0.9.31 under Doc.Horn while the version in the universe ubuntu repo is 0.9.22. :)

Edit: Doc.Horn also has the Wine packages for i386, plus many other non-free packages for x86_64 and i386.

Edit Again: Wine 0.9.22 is edgy i386 with no x86_64 version in ubuntu universe. It appears that feisty now has version 0.9.33 for i386 in ubuntu universe, but no x86_64 version. So if you have x86_64 you still need to use the Doc.Horn repos.

---

### Post by forrestcupp on 2007-04-10
I finally got the guts to try vmplayer.  I installed XP with it.  It works, but TV On Demand is a lot choppier in a virtual box.  It would be nice to just have it native.  I couldn't get it to work with wine.  It keeps giving me an error, and it won't finish the qmpsetup installation.  I have the very latest version of wine, too.  I don't get it.  Oh well.

---

### Post by warp99 on 2007-04-11
> **forrestcupp said:**
> .  I have the very latest version of wine, too.  I don't get it.  Oh well.

What version of Wine do you have with which release? The reason I ask is that the changelog includes many fixes from version 0.9.22 (Edgy) to version 0.9.33 (Feisty):

[http://changelogs.ubuntu.com/changelogs/pool/universe/w/wine/wine_0.9.33-0ubuntu1/changelog](http://changelogs.ubuntu.com/changelogs/pool/universe/w/wine/wine_0.9.33-0ubuntu1/changelog)

The site works with version 0.9.31.0 from ubuntu.moshen.de, so if you have that version or greater it should work no problem.

---

### Post by forrestcupp on 2007-04-11
I have version 0.9.34.  It's the absolute latest release they list on [www.wine.hq](www.wine.hq).  So I don't think that is my problem.  The problem is with a certain function not being supported in the riched20.dll.  I even tried using the actual riched20.dll that is on my wife's XP computer.

Edit:

I just got it to work.  I remembered another time that I tried to run something by typing ```
wine ./programname
``` and it didn't work.  But when I typed ```
wine /complete/path/programname
``` the same thing then worked.  I don't know why it's like this.  So when I remembered this, I tried qmpsetup typing in the complete path, and now it works.  The video is kind of grainy, but it's a lot smoother than it is in vmware.  Thank you.

---

### Post by DoctorMO on 2007-04-11
An interesting problem, but I still encourage you to send an email to this folks.

Besides I have the downmost regards for fox news and the fox brand in general. as they say 'I wouldn't urinate on them if they were on fire'

---

### Post by forrestcupp on 2007-04-11
> **DoctorMO said:**
> An interesting problem, but I still encourage you to send an email to this folks.

Besides I have the downmost regards for fox news and the fox brand in general. as they say 'I wouldn't urinate on them if they were on fire'

I already emailed all of the links that were given above.  It may not do any good, but it's worth a shot.

---

### Post by warp99 on 2007-04-11
> **DoctorMO said:**
> 'I wouldn't urinate on them if they were on fire'

.. but instead break out the marshmallows for a Faux News exclusive:

( News model with very shiny lip gloss who is sometimes mistaken for a porn actress, not much difference from her present occupation except that her knees don't get dirty, fills the center of a 13 inch color TV inside your ex-wife's double wide trailer)

Bill O'Reilly and Shawn Hanity seized by angry mob, burned at the stake.  Details at 10:00. 

Faux News: We distort, you decide. :popcorn:

---

### Post by Tombo5150 on 2007-11-08
I did send an email to fox giving them a piece of my mind. I was just about to start a thread on this topic when I stumbled across this one. I'm going to give the wine a shot. But I haven't used it in awhile since I last had feisty on my old laptop that got stolen. Should be fun. Please more people send a message to fox.

---

### Post by bash on 2007-11-08
If your in the US you could try hulu.com (streams of Serieses of both NBC and Fox). Although I don't know if its not just the same service as the on Demand channel on MySpace or if it works on Ubuntu.

---

### Post by Sunflower1970 on 2007-11-08
> **ubun-two said:**
> If your in the US you could try hulu.com (streams of Serieses of both NBC and Fox). Although I don't know if its not just the same service as the on Demand channel on MySpace or if it works on Ubuntu.

I've signed up for their beta at hulu, but I don't think it'll work using Ubuntu...About a month ago I was able to watch anything on NBC.com not using Windows, but something's changed and now I cannot even get the player to go even though it's Flash. Earlier this year I was able to watch stuff on Fox.com, (May I believe) but since then it's a no-go. Using IE4Linux sort of works for NBC, but the video's so choppy it's not worth it...

---

### Post by tikal26 on 2007-11-20
Hulu works fine on my Kubuntu 64 box, no problems, so that  might be a good sign

---

### Post by Sunflower1970 on 2007-11-20
> **tikal26 said:**
> Hulu works fine on my Kubuntu 64 box, no problems, so that  might be a good sign

That's a great sign :D

Now if they would just send me the info to be a part of their beta testing, I could watch my shows

---

### Post by Tombo5150 on 2007-11-21
Whats up with this waiting list? I feel like I'm waiting in line at a club or party of some sort........

---

### Post by tikal26 on 2007-11-27
I feel so special!!!!!
I am so sorry that I cannot invite you or I would invite all of you, but I cna embed video on a blog or somethign so if anyone wants to seee how it works I could do it.

---

### Post by yabbadabbadont on 2007-12-04
> **Sunflower1970 said:**
> About a month ago I was able to watch anything on NBC.com not using Windows, but something's changed and now I cannot even get the player to go even though it's Flash.

I just discovered that the video refuses to play if you have doublclick.net blocked.  I had it blocked in my /etc/hosts file and the video would just sit at the "Loading..." screen while I could see in the status bar that it was trying to connect to ads.doubleclick.net.  Once I unblocked it, the video started playing correctly.  Of course, they don't pre-buffer the video at all, so it really sucked on my 768kbit DSL connection, but at least it played.

---

### Post by forrestcupp on 2007-12-18
About Fox TV On Demand - they don't use MySpace anymore, so On Topic doesn't apply anymore.  Hulu is the answer.

It took me about a month to get invited to participate in Hulu.
> **yabbadabbadont said:**
> Of course, they don't pre-buffer the video at all, so it really sucked on my 768kbit DSL connection, but at least it played.
If you click the pause button, it will pre-buffer.

The onlly thing that doesn't work in Linux is the full screen mode because of Flash problems.  But the pop out mode works, which makes it pretty much full screen in a pop up window.

If anyone is tired of waiting to be invited, check out [OPENhulu](http://www.openhulu.com).  Hulu allows you to embed their vids on your website or blog.  Some guy went through and embedded *all* of their videos on his site so people don't have to wait.

---

### Post by yabbadabbadont on 2007-12-18
> **forrestcupp said:**
> If you click the pause button, it will pre-buffer.

That is my usual tactic for dealing with my slow connection.  Unfortunately, in this instance it didn't work.  I even tried letting it run (stutteringly) through a minute of video before pausing it, as some sites won't buffer if you pause too soon.  Doesn't really matter.  There are always alternate methods for viewing such video...  Not that I would ever suggest that anyone should use such methods.  :)

---

### Post by Sunflower1970 on 2007-12-18
> **forrestcupp said:**
> If anyone is tired of waiting to be invited, check out [OPENhulu](http://www.openhulu.com).  Hulu allows you to embed their vids on your website or blog.  Some guy went through and embedded *all* of their videos on his site so people don't have to wait.

Openhulu.com is great. Ironically the day I discovered it and began using it, I got my invitation to hulu....:lolflag:

---

### Post by forrestcupp on 2007-12-18
> **yabbadabbadont said:**
> That is my usual tactic for dealing with my slow connection.  Unfortunately, in this instance it didn't work.  I even tried letting it run (stutteringly) through a minute of video before pausing it, as some sites won't buffer if you pause too soon.  Doesn't really matter.  There are always alternate methods for viewing such video...  Not that I would ever suggest that anyone should use such methods.  :)

That's weird.  Pausing it worked for me.

---

### Post by [Hmk] on 2008-04-30
Hulu works for me but it only works fine in the small video version. If I make the video full screen its really choppy and CPU usage jumps to 100%. Anybody know what to do about that? Thanks in advance.

---

### Post by madjr on 2008-04-30
> **'[Hmk] said:**
> Hulu works for me but it only works fine in the small video version. If I make the video full screen its really choppy and CPU usage jumps to 100%. Anybody know what to do about that? Thanks in advance.

the solution:

[http://ubuntuforums.org/showthread.php?t=769906](http://ubuntuforums.org/showthread.php?t=769906)

---

### Post by forrestcupp on 2008-04-30
> **'[Hmk] said:**
> Hulu works for me but it only works fine in the small video version. If I make the video full screen its really choppy and CPU usage jumps to 100%. Anybody know what to do about that? Thanks in advance.

Like madjr was pointing out, it's an issue with Flash.  But one thing you can do is this.  If you are using Compiz (visual effects), you can use the zoom feature to zoom in on the video to full screen.  It won't be choppy and it actually smooths it out to make it look better.

---

### Post by madjr on 2008-04-30
> **forrestcupp said:**
> Like madjr was pointing out, it's an issue with Flash.  But one thing you can do is this.  If you are using Compiz (visual effects), you can use the zoom feature to zoom in on the video to full screen.  It won't be choppy and it actually smooths it out to make it look better.

nice i'll try that

---

### Post by Shannon_VanWagner on 2009-08-19
This is the same issue for ABC Full Episodes and other TV shows that use the Movenetworks.com player on the Internet (i.e., CW, Oprah, Mr. Obama's speeches at the DNC convention, etc.). It seems movenetworks.com made the terrible mistake of NOT providing a Linux content player from the start. Adobe didn't make this mistake with Flash(at least not as badly), and I believe that's one reason that Flash is such a widely used content player at this point.

For those who are looking for more information on the subject, there's another post which has similar details on the issue and includes a "unofficial" "we're working on it, and for Moblin too" response from a movenetworks employee [here]("http://ubuntuforums.org/showthread.php?p=7808662#post7808662").

As for watching 24 on hulu.com, yes it works well, see the 24 search results page [here]("http://www.hulu.com/search?query=24").

I've recently been working to make a big stink about this by writing to the TV networks(ABC/Fox/Oprah), government officials, Mark Shuttleworth, and on digg.com, [here]("http://digg.com/linux_unix/Mr_Obama_s_DNC_speeches_BLOCKED_from_LINUX_by_movenetworks"), [here]("http://digg.com/linux_unix/Want_ABC_FOX_OprahTV_Full_Episodes_for_Linux_Comment_here"), and [here]("http://digg.com/linux_unix/ABC_movenetworks_for_Linux_video_plugin_Petition_1_049_sigs").

I'm convinced there's enough people that are mad about this to make something happen. We just all need to link together and focus our energy into one beam of mighty GNU/Linux resolve.

Regardless of what all the paid market-share counters say, we GNU/Linux users will be heard!

Between the promise of an impending move networks player, and the diversification of streaming media between hulu and movenetworks, things are looking up none the less. I think ABC/Fox have heard our calling, and that's why they are diversifying with hulu.com. Right on.

Let Freedom ring!

---

