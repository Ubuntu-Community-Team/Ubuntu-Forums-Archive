---
title: "XServer 1.4 delayed to Gutsy+1?"
date: 2007-08-18
forum: The Cafe
---

### Post by bash on 2007-08-18
According to [this](www.phoronix.com) XServer 1.4 and with it X.Org 7.3, the GTK frontend for configurating Monitors and the Bulletproof X are being delayed to Ubuntu 8.04

> Following a developer meeting this week, the decision has been made to leave Xserver 1.4 out of 7.10 Gutsy Gibbon and then include it in Ubuntu 8.04, in what is currently another eight months away. The reason behind abandoning Xserver 1.4 is that it won't be released until after the Ubuntu Gutsy feature freeze, but at the same time the development version (Xserver 1.3.99) is already available. Xserver 1.4 is what X.Org 7.3 will use. Dependent upon X.Org 7.3 is also Ubuntu's displayconfig-gtk and their bullet-proof-x. Unless the Ubuntu developers decide to make an exception or extend their feature freeze, Xserver 1.4 is out of the question for Ubuntu users until next year. Mark Shuttleworth frequently talks about wanting the major open-source projects to coordinate and schedule their release cycles with one another, but it doesn't look like Mark wants to play ball on this one by adjusting the Ubuntu 7.10 "Gutsy Gibbon" release cycle so late in the game.

The Ubuntu blueprints for X.Org 7.3 and Bryce Harrington's mention of Xserver 1.4 not until Gutsy+1 can be read on the Launchpad. Ubuntu 8.04 LTS may end up getting X.Org 7.4 with Xserver 1.5.

Source: [http://phoronix.com/?page=news_item&px=NTk4OQ](http://phoronix.com/?page=news_item&px=NTk4OQ)

---

### Post by tehkain on 2007-08-18
[http://ubuntuforums.org/showpost.php?p=3223971&postcount=52](http://ubuntuforums.org/showpost.php?p=3223971&postcount=52)
[B]This does not affect XORG7.3, displayconfig-gtk, and BulletproofX
bryceharrington the developer who is implementing Xorg and BulletproofX made a statement on the third page. Xorg7.3 is modular. Most of it is in. Really only xserver1.4 is being left out.

The below is all wrong and based on the incorrect information that was passed around. Thanks to ubuwu for knowing what he is talking about.[/B]


Yea it sucks but i see why. These are the moments where I really wish gutsy would come a month late. No need to change the name. 7.3 brings so many usability enhancements(that non techy people can access) that i think it is something that might warrent a bit of waiting.

So much work was done to get BulletproofX and DisplayConfig-GTK ready. Just imagine telling a user to 'open you display preferences and click on your second monitor to activate it' or 'kust restart and x will load the default solution'. Thats like 470 less help post/irc questions per day.

---

### Post by sumguy231 on 2007-08-19
The problem with delaying it is that it would cut into the development time of 8.04. Of course, deep down I kinda wish they would throw caution to the wind, say "screw it" to the feature freeze, and defiantly work it in anyway. One of the problems with Ubuntu releases is that none of the improvements are ever considered essential/release-blockers, and pretty much nothing seems guaranteed to get in. It would be nice to have a clearly-defined set of core features which will be in the next release.

I have a bad habit of looking at the Launchpad blueprints for whatever is the development version of Ubuntu at the time. Following the blueprints page is not unlike someone offering you something nice, and then them saying "No, just kidding" and punching you in the face. It gets kinda annoying sometimes.

---

### Post by FuturePilot on 2007-08-19
I wonder if something like that would be backported? Might be kind of dangerous though.

---

### Post by hanzomon4 on 2007-08-19
Well, this sucks....

---

### Post by tehkain on 2007-08-19
Wrong information sucks.

---

### Post by tehkain on 2007-08-19
So what is the exact information on this? I am confused by many different reports on what Xorg consist of,

Can we have Xorg7.3(and bulletproof/displayconfig) without xserver1.4?
Is it required? I know some distros use Xorg7.2 with Xserver 1.3 even tho Xorg7.2 came with 1.2, so is the opposite possible?

How does this affect monitor detection without nrestarts(hotplugging)? How does it affect BulletProofX and DisplayConfig-GTK?

---

### Post by triptoe on 2007-08-19
I bet you we are in for a surprise. It is named gutsy after all :P

---

### Post by UbuWu on 2007-08-19
BulletProofX and DisplayConfig-GTK are NOT affected. In fact displayconfig has already been implemented and bulletproofx is being deployed.

[https://wiki.ubuntu.com/DevelTeamMeeting20070816](https://wiki.ubuntu.com/DevelTeamMeeting20070816)

---

### Post by UbuWu on 2007-08-19
> **tehkain said:**
> 
How does this affect monitor detection without nrestarts(hotplugging)? 

Not, this only affects input hotplugging, xrandr 1.2 (already included) does output, i.e. monitor, hotplugging.

---

### Post by tehkain on 2007-08-19
> **UbuWu said:**
> Not, this only affects input hotplugging, xrandr 1.2 (already included) does output, i.e. monitor, hotplugging.

Thanks!

---

### Post by bash on 2007-08-19
Ah this already sounds a lot better. Was really kinda worried when I read that everything was put on hold. 

So as far as I can now understand from the notes of the devel meeting is that Bulletproof-X and the GUI xorg.conf configurator are implemented, but that no decision has been made yet if X.org 7.3 is included completly, partially or not at all.

---

### Post by sumguy231 on 2007-08-19
Too bad Kubuntu won't get bulletproof-x anyway, though. :(

---

### Post by Miguel on 2007-08-19
> **sumguy231 said:**
> Too bad Kubuntu won't get bulletproof-x anyway, though. :(

Why? X11 is waaay lower level than any desktop environment. I'm running gutsy right now and I can tell you that if I delete it and reboot my system I will get both 3D accel (free r300 driver) and 1280x800 resolution. The latter is evident as soon as GDM launches. I fail to see where would KDE fail. I repeat: **this is without an /etc/X11/xorg.conf file in my system**. 

It's true though that displayconfig-gtk might not make kubuntu, due to, err, the gtk dependency. I'd expect a qt version soon (although gutsy +1 is the most likely candidate).

---

### Post by sumguy231 on 2007-08-19
> Why? X11 is waaay lower level than any desktop environment.
The developers were going to have it boot into a failsafe X session and load displayconfig-gtk (this is still the plan for Ubuntu as far as I know) but a technical limitation in KDM prevents that. But you're right, it will still do the above thing and work ok with a missing or damaged xorg.conf. But that's only part of bulletproof-x, I believe.

---

### Post by dasunst3r on 2007-08-19
I've been hearing reports of people without xorg.conf files.  Are you folks kidding?  How well is it working with the proprietary nVidia or ATi drivers?

---

### Post by Miguel on 2007-08-20
> **dasunst3r said:**
> I've been hearing reports of people without xorg.conf files.  Are you folks kidding?  How well is it working with the proprietary nVidia or ATi drivers?

I haven't tested it with the proprietary ATi driver. In any case, the worst that would happen is that (for my card) the radeon driver would load without 3D acceleration (if you install fglrx, you also install a library (libGL.so) incompatible with the open source drivers' acceleration.

---

### Post by Alex Fernandez on 2007-08-20
We better see it backported :P

---

### Post by Seisen on 2007-08-20
I guess I would rather have it stable then end up making a gigantic mess, imagine what that would do for Ubuntu reputation.

---

### Post by Alex Fernandez on 2007-08-20
> **Seisen said:**
> I guess I would rather have it stable then end up making a gigantic mess, imagine what that would do for Ubuntu reputation.

They can always have both 1.3 and 1.4, just like they can have kde3 and kde4 .. and let us, the user decide

---

### Post by Miguel on 2007-08-20
I'd say the X server is too low-level in the system to backport. Also, there are **lots** of binaries related to the X server and even more libraries against which lots of packages are built. I fail to see how could you have a system with two X installed. Well, you could have two sets of binaries a la gcc but that doesn't seem too practical for a backport.

---

### Post by rabidrabbit on 2007-08-20
so does xrandr 1.2 support rotating and positioning a second monitor? I've had a lot of trouble doing this in fiesty.

---

### Post by shingalated on 2007-08-20
SWEEEET!!!  I was highly disappointed when I saw that on digg

---

### Post by bryceharrington on 2007-08-20
Hi all,

I'm the Ubuntu X maintainer, and was the one who made the call to hold off on xserver 1.4.  I gave a detailed response here:  [http://ubuntuforums.org/showpost.php?p=3223971&postcount=52](http://ubuntuforums.org/showpost.php?p=3223971&postcount=52)

But to confirm, no this has no impact on displayconfig-gtk or bulletproof-x - really the only part of xorg 7.3 they really depended on was xrandr 1.2, and that's already in.  As others commented, displayconfig-gtk is already released in Gutsy (please play with it and send in patches if you discover bugs - its Python so should be easy).  Bulletproof-X is also deployed but not turned on yet by default.

Also, because Xorg is developed modularly, we've already incorporated a huge portion of Xorg 7.3.  It's just that since the final bits and pieces of Xorg 7.3 are coming out post-Feature Freeze, we're going to be missing on a few of the newer pieces.  Here is a page I maintain that shows the current merge status for all the 7.3 pieces:  [http://people.ubuntu.com/~bryce/Xorg/versions_current.html](http://people.ubuntu.com/~bryce/Xorg/versions_current.html).  As you can see, there are only a few packages still red.

It's heartening to see such strong interest in X, and especially for Displayconfig and Bulletproof-X.  If you'd like to get involved in helping push Ubuntu's X even further along through testing, backporting patches for Gutsy, or helping strengthen X for Gutsy+1, please join the rest of us at #ubuntu-x on Freenode, or drop me a message.  I'd love to welcome more people to the team!  :-)  There's lots of important work that can be done!

---

### Post by sumguy231 on 2007-08-20
Thanks for explaining it all. There's a lot of conflicting information floating around, and I'm pleased to hear that the new xrandr will still ship. I had no idea that all the different bits of Xorg were seperable like that. 

Keep up the good work. :)

---

### Post by vertigo1980 on 2007-08-20
thanks bryceharrington, it's comforting to know that most of 7.3 is going to make it in. would a backport for those missing/outdated pieces be possible, so that those of us who would like to can get the "complete" package? :)

anybody have a link to the xserver 1.4 changelog?

---

### Post by tehkain on 2007-08-21
Thank you Bryce, This is why I love the free software world. When would anyone at MS ever drop by on a forum to explain why and what certain changes mean.

---

### Post by bryceharrington on 2007-08-21
sumguy231, yeah, it used to be that X was a big monolithic piece and it was quite difficult to work with.  However, thanks to a truly monumental amount of effort by Daniel Stone and the other Xorg developers, the pieces were all broken out modularly.  It sure makes package maintenance straightforward.

vertigo1980, since 1.4 is not yet released, there isn't a changelog.  However the 1.3.99 changelog is quite thorough and comprehensive.  I've put a copy of it at  [https://wiki.ubuntu.com/X/Fixes_to_Backport](https://wiki.ubuntu.com/X/Fixes_to_Backport), and flagged some of the changes that looked interesting to me; I plan to investigate these more thoroughly and maybe backport them for Gutsy if it makes sense.  If you spot anything important I've missed, or if you know something I've flagged really shouldn't be backported, please let me know (or edit the page directly).

Regarding backports of xserver 1.4 and other major pieces, it's certainly doable.  This is also an area where community involvement would make a huge difference in getting the backports done swiftly.  If this is something you'd be interested in participating in, just pop by #ubuntu-x on Freenode or drop me a note, and I'll be happy to give the low-down.

---

