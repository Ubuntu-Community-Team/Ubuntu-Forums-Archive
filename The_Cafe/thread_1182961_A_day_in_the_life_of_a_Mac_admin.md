---
title: "A day in the life of a Mac admin"
date: 2009-06-09
forum: The Cafe
---

### Post by decoherence on 2009-06-09
I administer a couple of Mac labs at my work (a school) and let me tell you; it ain't all roses. Here, for your perusal, is an email I wrote to my boss and the video course teacher regarding next year's setup. We are subscribed to the iLife maintenance package so we get 'free' upgrades. This conversation is about which version we should use. As you'll see, none of them are quite right. If you can make your way through the email, I'd be curious to know what you think about any aspect.

Also, be aware that these labs are directory services enabled. So if there are Mac users out there wondering why this is so freaking complicated, being hooked up to a directory server and using network homes has a lot to do with it.

> We are sort of between a rock and a hard place, as far as video stuff goes.

If we use iMovie 6 (the version we used two years ago) we have complete flexibility about where captured video goes. The problem is that iMovie 6 is two versions behind and any students who wish to do work at home will likely have a newer, incompatible version. iMovie 6 was available as a free download, last I checked. Requiring students to use that version at home might be an option.

If we use iMovie '08 (there is no 7 or '07... they went from version numbers to years) we can continue doing things the way we have, using disk images to capture our video to. 

Just a refresher, the reason we need to use disk images is because iMovie '08 will ONLY put captured video in the root level of a volume. This doesn't work in a multi-user, security-conscious system unless each user has their own hard drive to use as a capture destination. My solution was to provide each user with a disk image, giving them a virtual hard drive to use as iMovie 08's capture destination. 

The problems with disk images is that they get corrupted, and occasionally they won't open without some manual intervention on my part (not doable by teacher or students... you have to manually disconnect the AFP connection at the server end.) Also, I'm sure this isn't an "Apple approved" technique. Again, iMovie '08 isn't the latest version. I'm not sure if work done in iMovie '09 is compatible with '08.

iMovie '09, in its current state, will simply not work with our current setup. Not only does it demand access to the root level of a volume in order to capture video, it also doesn't recognize disk images as valid capture destinations.

The only way I can see of using iMovie '09, aside from students having their own hard drives, would be if I created a bunch of dedicated partitions on each iMac for users. The Mac system itself is only taking up about 50GB, leaving us with ~70GB free to play with. The problem with such a setup is that it would leave potential 'casual users' in the lurch. Also, I'd need a list of all users, or at very least, numbers of users, so that I only have to re-partition each iMac once, at the start of the year. Further repartitioning, once there is work on the drive, would require I back it up first, which will be a lengthy process. In such a configuration, students would be locked to a particular iMac. All of this is contingent on ~70GB per computer being sufficient, and I'm not sure of that. Assuming the current limit of 20GB per user, that's three classes. If anyone wants to go beyond 20GB (a couple did this year) it will be much harder to make it happen as it would again require that the drive be backed up before partitions are resized.

In other words, this solution could work, technically. It could also easily become unworkable, logistically. 

I'm going to send a more concise version of this to our friends at Apple and see if they can suggest anything better.

My poor friends at ubuntuforums didn't get the concise version. I haven't done up the email to Apple yet.

Oh, and before anyone suggests students get their own drives to store the stuff on, I already suggested it. It didn't fly (they'll lose them!)

---

### Post by PhilMize on 2009-06-09
lol yea that looks like a fun issue to tackle...

I deal with some macs (i administer a school district) and alot of the times i just poke around a bit and scratch my head... then call my buddy whos a ummm what do hey call the guys in the stores? I forgot... lol Anyways, yea crap is frustrating. Don't even get me started on connecting to printers shared from a Windows network.

I guess one day I should steal my coworkers MacBook and start crunching some hours learning the ins and outs of a Mac.

---

### Post by billgoldberg on 2009-06-09
Seems pretty unprofessional from Apple's part that those things aren't possible.

You could use alternative software instead of iMovie.

---

### Post by Sand &amp; Mercury on 2009-06-09
I've seen firsthand on my old TAFE campus that a network setup that isn't correct down to the last tiny little detail will reduce every Mac on the network to an unstable jittery mess.

---

### Post by decoherence on 2009-06-09
> **PhilMize said:**
> lol yea that looks like a fun issue to tackle...

I deal with some macs (i administer a school district) and alot of the times i just poke around a bit and scratch my head... then call my buddy whos a ummm what do hey call the guys in the stores? I forgot... lol Anyways, yea crap is frustrating. Don't even get me started on connecting to printers shared from a Windows network.

I guess one day I should steal my coworkers MacBook and start crunching some hours learning the ins and outs of a Mac.

If only to familiarize yourself with the interface. My main gripe with it is that the type of troubleshooting UNIX folks are used to is of very limited application when dealing with Cocoa or Carbon programs (which make up at least 90% of the graphical software on OS X.) Every now and then they throw you a bone like including Sun's dtrace, but I really wouldn't need dtrace if the various pieces of software logged in a consistent fashion (or at all.)

---

### Post by decoherence on 2009-06-09
> **Sand & Mercury said:**
> I've seen firsthand on my old TAFE campus that a network setup that isn't correct down to the last tiny little detail will reduce every Mac on the network to an unstable jittery mess.

Yes, I've seen that as well. In many cases this comes down to improperly set up DNS. Macs don't fail gracefully -- at all -- when it comes to network weirdness. Curse that spinning beachball!!

---

### Post by Yashiro on 2009-06-09
By 'demand access to root level volume' do you mean that when run as a standard user iMovie fails because it can't write a file to / ?

---

### Post by sloggerkhan on 2009-06-09
> **Yashiro said:**
> By 'demand access to root level volume' do you mean that when run as a standard user iMovie fails because it can't write a file to / ?

I don't get this either, on a normal system, wouldn't a user's iMovie files go in their personal folder?

It sounds more like whatever you are using for remote homes isn't transparent to iMovie's directory parsing.

Unless movie files really do only go in /.

---

### Post by MikeTheC on 2009-06-09
@OP:

Am I correct in assuming it won't let you write to a network share then?

---

### Post by earthpigg on 2009-06-09
why are you determined to use Apple software?

the school paying for the iVendor iLockin or whatever is a sunk cost. nothing can be done to recover those funds that where clearly appropriated immorally. may as well keep OS X, i suppose, but no reason to bother with iMovie 9billion or whatever.

how about installing iMovie 6, and something like avidemux that runs on pretty much _**whatever**_ OS your students have at home, and letting them use whichever they prefer? the current iMovie (any version) plan locks students into Apple.

our Free Software stuff is great, and i support it, but even more vital is students being given every opportunity to excel. it should _**not**_ be the case that only students with parents wealthy enough to own Apples can work on their projects at home.

avidemux runs on Windows, Linux, OS X, BSD, etc

[http://en.wikipedia.org/wiki/Avidemux](http://en.wikipedia.org/wiki/Avidemux)
[http://fixounet.free.fr/avidemux/download.html](http://fixounet.free.fr/avidemux/download.html)

---

### Post by decoherence on 2009-06-09
> **sloggerkhan said:**
> Unless movie files really do only go in /.

The short answer is "yes, that's right." But it's not quite right. The pedant in me won't let me say 'yes' because your phrasing of the question combined with my pedantry brings up an interesting point. The more I think of it, the more it seems to me that iMovie has no concept of the filesystem layout.

Allow me to digress in order to re-iterate that I'm talking about video capture scratch disks. Not the place where you save the project file or render out your final movies, but the place where the video goes when you're capturing it from a camera. Previous versions of iMovie allowed you to specify an arbitrary directory for this. So does any other video editing software I've used, and I've used quite a few different packages over the years.

If you have a single-disk system, then -- in answer to the part of your post that I quoted -- "yes": iMovie will ONLY capture to the root level of the filesystem, AKA "/".

However, it will also capture to the root level of any other partition it decides is valid. You would not express this as "/" in a UNIX style filesystem. You would express this as a mount point: /mnt, /media/disk, etc.. iMovie (and the Mac interface in general) does not work this way. It's more like Windows (or more properly, the classic Mac OS, System "Whatever.") iMovie '08 and up presents a list of partitions that you can capture to. It ALWAYS captures to the 'root level' of that partition. This is not UNIX-like in the least.

On top of that, iMovie does not require a superuser password when it runs or when it captures video. Nonetheless, it writes that video straight to / (or equivalent mount point.) That tells me iMovie completely bypasses the security features that Apple is touting when they talk about OS X being based on UNIX.

Most of this only just registered to me, and I'm sure it warrants further thought. It's hard to think objectively when you're in the middle of things. I'm very glad I posted this here and got the feedback that I did. Thank you all!

Of course, more feedback is alwasy welcome! :D

---

### Post by decoherence on 2009-06-09
> **MikeTheC said:**
> @OP:

Am I correct in assuming it won't let you write to a network share then?

I haven't tried. Capturing video over the network is a no-no. Far too much bandwidth, far too much latency. I've found that you can get away with a couple of simultaneous captures, but it's not reliable, and we have 24 students in a class. So even if iMovie '09 let me capture to a network share, it wouldn't really be an option.

Still, it is something to check. Network shares, like disk images, show up as partitions ('volumes' in Mac parlance) on the desktop and to applications. If iMovie '09 doesn't recognize those as valid capture scratch disks -- same as it doesn't recognize disk images -- it may indicate that Apple is on a mission to eliminate the use of 'non-standard' (which likely means 'not well tested by apple') configurations. Maybe. Wouldn't surprise me.

In which case, I'm extra curious about how the heck I *AM* supposed to do this in a typical networked setup. Questions for my Apple rep.

---

### Post by decoherence on 2009-06-09
> **earthpigg said:**
> why are you determined to use Apple software?

the school paying for the iVendor iLockin or whatever is a sunk cost. nothing can be done to recover those funds that where clearly appropriated immorally. may as well keep OS X, i suppose, but no reason to bother with iMovie 9billion or whatever.

how about installing iMovie 6, and something like avidemux that runs on pretty much _**whatever**_ OS your students have at home, and letting them use whichever they prefer? the current iMovie (any version) plan locks students into Apple.

our Free Software stuff is great, and i support it, but even more vital is students being given every opportunity to excel. it should _**not**_ be the case that only students with parents wealthy enough to own Apples can work on their projects at home.

avidemux runs on Windows, Linux, OS X, BSD, etc

[http://en.wikipedia.org/wiki/Avidemux](http://en.wikipedia.org/wiki/Avidemux)
[http://fixounet.free.fr/avidemux/download.html](http://fixounet.free.fr/avidemux/download.html)

I agree with you 100%, however these are not my decisions to make. I am in the unfortunate position of having to support a system that was mostly in place before I ever got there.

One thing I must make clear is that this is an independent school whose tuition is far, far beyond anything my parents could ever afford. "Expensive" means "better," doesn't it? (please picture me gagging now)

Regarding the suggestion about iMovie 6... I agree that this is our best option at this point and is probably what I'll push for. That or another alternative, if I can find one. Regarding avidemux, I looked at it a while ago and determined it wasn't up to the job. I guess it's time to look at it again! Hopefully I'll be pleasantly surprised. Thanks for that tip.

As far as letting people use what they want, they are perfectly welcome to do that now -- that is completely outside my domain. However if they are having trouble with some random video editing suite they got off download.com, well I'll try my best like good tech support should, but ultimately they're on their own.

Let me just say again, I'm in total agreement with your point about Apple lock-in and am not at all happy with the current setup. This is something most of us forum goers are acutely aware of but I've yet to be able to get it through the heads of anyone of influence at work. So at this point, the conversation is constrained to 'what version of iMovie should we use?' Le sigh.

Thanks again for the replies!

ADD: this is why it is extra, extra sad for me that the only good video editing suites for linux cost too much for even this school to afford. mmm discreet smoke....

---

