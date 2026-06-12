---
title: "First impressions of 12.10"
date: 2012-10-18
forum: The Cafe
---

### Post by KiwiNZ on 2012-10-18
I have installed the final release on a test Laptop. Everything works, but it is slow. Opening the Software Centre takes around 20 seconds, Firefox 22 seconds, Libre Office Calc 17 seconds. Opening a simple Game in this case Naval Battle 15 seconds.

Now I know these numbers are not big, but on the same rig 12.04 was running considerably snappier. This was the rig that I recently tested Kubuntu on and creaking behemoth was snappier. One positive it did OK with my annoyingly fussy HP ink jet printer although it cannot find my Laser Printer.

Overall my initial score is B-

---

### Post by sffvba[e0rt on 2012-10-18
Could it be that Unity 3D is being rendered via the CPU (ala fallback mode) and not by the GPU?


404

---

### Post by KiwiNZ on 2012-10-18
> **not found said:**
> Could it be that Unity 3D is being rendered via the CPU (ala fallback mode) and not by the GPU?


404

ooops good point

---

### Post by KiwiNZ on 2012-10-18
does not appear to be the case, I am installing on another test rig to see if there is any improvement.

---

### Post by Mikeb85 on 2012-10-18
Hmmm, I haven't installed it on my desktop (which is old), but on my new laptop with i7 3520 processor and 8 GB ram, 12.10 seems to be about the same speed as 12.04 (Brtfs filesystem BTW).  It certainly doesn't seem slow.  Well, maybe a tad slower than SUSE on the same rig.

---

### Post by KiwiNZ on 2012-10-18
I just finished installing a second test rig, this is a Core 2 Duo with 2 GB Ram Nvidia GPU.
It is also sluggish compared to 12.04. Admittedly it is not a fast rig and it is a tad past it's prime being an ancient core 2 duo but the OS should run better.

---

### Post by sammiev on 2012-10-19
> **KiwiNZ said:**
> I just finished installing a second test rig, this is a Core 2 Duo with 2 GB Ram Nvidia GPU.
It is also sluggish compared to 12.04. Admittedly it is not a fast rig and it is a tad past it's prime being an ancient core 2 duo but the OS should run better.

I have a rig setup to install in the AM. I already have the ISO and will report back here then.

---

### Post by QIII on 2012-10-19
Ouch!

I'm not seeing that kind of difference judging subjectively.  I haven't used a stopwatch, so I don't have anything empirical.

There is just a hint of difference that I attribute to the fact that it's installed on a "green" 5400 rpm drive on my primary machine where Precise is installed on a 7200.

---

### Post by cariboo on 2012-10-19
With an Nvidia graphics card, there are a few things you can do to speed things up, but it means installing compizconfig-settings manager. 

The settings shown in the screenshot seem to help significantly

There is also a new driver being released by Nvidia on Friday, that should speed things up a bit also.

---

### Post by Elfy on 2012-10-19
Slow software centre is likely down to the addition of additional drivers to that.

Not managing to get nvidia installed any sense here - but with nouveau everything flies.

---

### Post by mips on 2012-10-19
> **KiwiNZ said:**
> I just finished installing a second test rig, this is a Core 2 Duo with 2 GB Ram Nvidia GPU.
It is also sluggish compared to 12.04. Admittedly it is not a fast rig and it is a tad past it's prime being an ancient core 2 duo but the OS should run better.

Really strange as I heard during the 12.10 buildup people saying 12.10 is faster than 12.04.

Those times you mentioned do sound really slow though.

---

### Post by CrusaderAD on 2012-10-19
Figured I'd start a thread with some feedback. So far, so good! I upgraded on 3 machines, 1 32bit and 2 64bit. The faster machines have taken to it perfectly. Runs smooth and fast.

The older machine had a bumpy start. It was slow and clunky. It took me a minute to find the "Additional Drivers" section to install my nvidia drivers. Searching the dash for anything regarding graphics didn't pull it up. I eventually found it under "Software Sources". Once I installed those drivers, everything seemed to pickup and run much smoother.

The positives: 
*Ubuntu One on all machines seems to be much faster than previous releases. Everything synced pretty quick.
*The menus are cleaner.
*The animations seem smoother.
*Installing apps from the dash is sweet.
*Online accounts makes setting up all your social much quicker. Plus the integration of social result in the dash is awesome.

The negatives:
*Gwibber is still slow and locks up when scrolling.
*There's no way to turn off social notifications (yes you can turn off bubbles but if gwibber is running, it's turning your envelope icon blue constantly unless you up the refresh rate time).
*Empathy's new contacts window is hideous. Absolutely hideous.
*I've noticed some crashes with nautilus so far.
*If you turn off online results in the dash, not only do you turn off shopping, but your social results as well. Maybe I just don't want ads...
*Installing the social "launchers" is great and all, but how do I get rid of them if I don't want them anymore?
*Sometimes exiting a social app (social app just opens firefox) leaves the icon active in the launcher (maybe because firefox is open elsewhere?).

This honestly isn't a rant, but some constructive feedback. I love the release so far, still my #1 operating system! Great job devs!

---

### Post by CrusaderAD on 2012-10-19
I had some speed issues until I installed the additional driver from Software Sources > Additional Drivers. Everything seems smooth now.

---

### Post by philinux on 2012-10-19
Threads merged.

---

### Post by sammiev on 2012-10-19
Done with the fresh install and had no issues to report at all.

---

### Post by Swagman on 2012-10-19
My Experience.

I have "Home" on its own partition so I was going to clean install 12:10.
I was running 11:10

However

She who **MUST** be obeyed decreed if I lose her chuffin passwords again she will NOT be impressed !!

So last night I upgraded to 12:04

Looked good. Quite pleased with it. Pretty kewl how you can now select sidebar width and reveal sensitivity etc.

Today I did the next step and upgraded to 12:10.

Ummm .... No sidebar (dislike the thing anyway but the missus uses this machine)

Cured by right clicking on desktop and selecting "Change Background" and switching  (permanently) on  the sidebar.

I've shrunk it to its minimum but it's always revealed and I hate it that way.

I've faffed around in various settings including CCSM .. Switched my Wobbly windows back on whilst I was there (how dare they switch those off!!)

So if anyones got a cure... I'm all ears

Next.. Click on the envelope to fire up Thunderbird and its gone !!
Just these "Available, Away, Busy" options that I imagine no-one ever uses !

So I found it in the dash and pinned it to the "wont go away" sidebar !

(Sorry .. It WILL go away .. just can't get it back ! without pressing windows key)

The envelope still goes blue though when you get an email.

Next (minor gripe..liveable with) my drop down menus in Firefox have turned white ? System ones have remained dark however.

So.. I went to themes and couldn't find a way to edit them ?

Hey Ho....There we go.. that's all I've found so far

---

### Post by tjeremiah on 2012-10-19
Buggy. The BETA was smoother.:mad:

I clean installed it yesterday to be greeted with my wireless not working. Using the steps that helped sovled the issue in the beta did not work in the final releas and I kept getting errors.

Compiz seems to crash every 12mins.This did not happen in the BETA.

Ubuntu 1210 also seems SLOWER than 12.04 for now.

The message menu, or w/e its called, not sure it thats the way it suppose to be but its not present on my panel.

If I have the time later im going to reinstall and see what happens.

---

### Post by Lightstar on 2012-10-19
It was super buggy for me.
Booted up Live CD (well.. not a cd anymore.. live usb is more like it)
I had only BLANK WINDOWS (blank menus too)
ARGH!

thought I had a bad .iso. 
redownloaded.
booted the new one..
BLANK WINDOWS
ARGH!

I was able to boot with the nomodeset switch.
installed ubuntu.
booted into the installation
BLANK WINDOWS
ARGH!

booted into the installation with nomodeset in grub
installed nvidia.
yay, I can see!
System is up and running now, very smooth.
Faster than 12.04 for me.  But when I was at 12.04 I had been upgrading for three versions.  12.10 is a fresh install.  So the performance might be because of this.

Booting with nomodeset seemed like the only solution.  But the performance was extra super slow while in that mode.

---

### Post by donniezazen on 2012-10-19
I am not so happy with power consumption. Power consumption goes over 25 W and system temp reaches 80C. I am sure kernel is more at blame here.

---

### Post by MikeCyber on 2012-10-20
PS: fxaa is a Gnome bug as it works fine in KDE



Nouveau looked terrible with my GTX460, install was hardly readable. Hence first clicked Nvidia current in software center and reboot. Unity was unusable as I couldn't reach panel etc. Must have been very low resolution. I had to kill x from vt1 and install nvidia with a ppa.
A beginner would have got stuck...my impression: Ugly install about the same as it was 10 years ago.-
Fixed sound by simply moving volume a little and disabled fd0 in Bios. Still fxaa is broken with my GTX460 (at least with Flightgear). Anyone has a working GTX460? 
And also still this: [http://ubuntuforums.org/showthread.php?t=2004739](http://ubuntuforums.org/showthread.php?t=2004739)

---

### Post by robert shearer on 2012-10-20
12.10 slower than a wet week. :-(

Crashes random apps at least twice per session.
Drops usb connections to webcam and when transferring data to devices.

Thought it was a hardware problem (several upgrades recently) and moments before a total stripdown I thought I should boot into the Oneiric install on the same machine.....

Result= sweet, **FAST**, and no crashes, no usb errors. Stable as...!

 11.10 has never given an ounce of trouble from day one. Perhaps it has hit the optimum spot for this hardware and Ubuntu is all downhill from here ? (unless I upgrade my system ?...) 
Funny, that sounds like that other O/S I left some years ago...


Will not be running 12.10. :-(
12.04 was slops too so now off to try  Debian.

(mumble mumble Amazon mumble Bugs unfixed mumble no legacy hardware support mumble Eye-candy mumble same mumble as last time mumble) 

:-)

---

### Post by vasa1 on 2012-10-20
It looks like this thread is limited to the Unity flavor. If it isn't, then I'd just like to say that Lubuntu 12.10 has nothing to mumble or grumble about ;)

---

### Post by robert shearer on 2012-10-20
> **vasa1 said:**
> It looks like this thread is limited to the Unity flavor. If it isn't, then I'd just like to say that Lubuntu 12.10 has nothing to mumble or grumble about ;)

No grumbling here, we Kiwis have a long tradition of voting with our feet.... :-)

 Lubuntu 12.04 and 12.10 fast smooth and stable, especially using a command line install and then adding lubuntu-core rather than the full desktop and all the facequack-plugins and other social media trivia.

---

### Post by ikt on 2012-10-20
[http://www.techdrivein.com/2012/10/ubuntu-needs-project-butter-like-android.html](http://www.techdrivein.com/2012/10/ubuntu-needs-project-butter-like-android.html)

Ubuntu needs a project butter.

---

### Post by x-shaney-x on 2012-10-20
My first impression is the dash.
Instead of tweaking it for performance, they are filling it up with pointless things.

It is getting slower and slower, the gwibber lens is not functional enough to be of any use and just seems to be there for the sake of appearing "social" and trendy.
The music lens STILL isn't fixed since they dropped banshee.

In my opinion, they should keep lenses to an absolute minimum and add a "get more lenses" button somewhere to make it super easy for users to only install lenses they want with one click instead of having to remove them through a package manager.

They should either do away with the laggy dash blur or at the very least make the "no blur" option actually useful.
That alone would only require simply tinting the lens darker but they won't even do that.

Instead of being a flagship focal point for ubuntu, the dash seems to be to me a prime example of everything that is wrong with ubuntu all in one place.

---

### Post by Docaltmed on 2012-10-20
I did a fresh install of the GNOME remix on an Asus eeePC that is being repurposed as basically an EMR client in one of my exam rooms. 

I gotta say, the latest Gnome Shell looks totally sweet! I have to say, the route that Gnome took with its notifications is far, far better than Unity.

Eventually, of course, the computer is going to be put in lockdown/kiosk mode, but I took a little bit of time to play with the new OS and DE first.

If I upgrade to 12.10 (a really big if), it will probably be to go back to Gnome Shell. For now, I think I'll stay on 12.04 myself. I used to do the intermediate upgrades (non-LTS) because there were compelling technology/functional reasons. Unity on 12.04 is a pretty nice gig, if you ask me.

Automatic Amazon search somehow doesn't seem to me to be a compelling reason.

If it sounds like I'm all over the place on this...well, I am.


EDIT: I just re-read what I wrote, and I apologize for even posting this publically. My entire comment should be taken out, washed, dried, ironed and have the words put in some sort of order where they make sense. I hope someone derives some joy from reading this old man's clearly senile rambles.

---

### Post by alphacrucis2 on 2012-10-20
> **Swagman said:**
> My Experience.


Today I did the next step and upgraded to 12:10.

Ummm .... No sidebar (dislike the thing anyway but the missus uses this machine)

Cured by right clicking on desktop and selecting "Change Background" and switching  (permanently) on  the sidebar.




If you are running nvidia blob its a known bug. Try installing the "experimental" driver. Worked for me. Actually the "experimental driver should be called "stable". The other two offered should be titled "junk".

---

### Post by thatguruguy on 2012-10-20
The Dash in 12.10 on my laptop was slow when I first upgraded a couple days ago. Oddly enough, it now seems to be working a normal speed. I don't know if there were internal things that needed to be optimized, or if some sorcery happened.

---

### Post by philinux on 2012-10-20
> **thatguruguy said:**
> The Dash in 12.10 on my laptop was slow when I first upgraded a couple days ago. Oddly enough, it now seems to be working a normal speed. I don't know if there were internal things that needed to be optimized, or if some sorcery happened.

That'll be zeitgeist indexing I think. Or sorcery lol.

Flipping evolution keeps crashing though. I hope that settles down.

---

### Post by tjeremiah on 2012-10-20
did another fresh install. Manage to get the wireless to work but Compiz continues to crash every 12 minutes. Went to additional drivers to install the correct AMD drivers to be greeted with Unity completely gone. I run to the AMD website to get the proper drivers and have the same issue. 

These things did not happen in the BETA which to me is crazy because the final version so far feels as if im testing an alpha build. :(

Going to keep testing to see if I can fix this graphic issue.

---

### Post by The Cog on 2012-10-20
> **alphacrucis2 said:**
> If you are running nvidia blob its a known bug. Try installing the "experimental" driver. Worked for me. Actually the "experimental driver should be called "stable". The other two offered should be titled "junk".

I concur. I was having lots of strange performance problems until I tried the "experimental" driver.

---

### Post by Swagman on 2012-10-20
> **alphacrucis2 said:**
> If you are running nvidia blob its a known bug. Try installing the "experimental" driver. Worked for me. Actually the "experimental driver should be called "stable". The other two offered should be titled "junk".

Thanks.. Will give it a shot

---

### Post by Swagman on 2012-10-20
Warning to n00bs

Do **NOT** try this at home.

Not unless you have a fetish for the terminal or plan on complete re-installing.

[img]http://imageshack.us/a/img405/7597/buggeredresolution1.jpg[/img]


Whoopie.

No top bar.. No sidebar.. windows key *doesn't reveal* the dash

Using the terminal to run programs.

Bollocking from the missus duly administered !!

---

### Post by Sijmen on 2012-10-20
> **donniezazen said:**
> I am not so happy with power consumption. Power consumption goes over 25 W and system temp reaches 80C. I am sure kernel is more at blame here.

Have that too. With xubuntu 12.04 the temp of my notebook was around 40. Now it's around 50. Not liking that. It if much faster though. 

Although I do like the new way of deciding which buttons should be visible, I thought 12.10 wouldn't allow me to reboot my machine and in order to restart I had to shut it down first..... :-k

---

### Post by Lightstar on 2012-10-20
> **ikt said:**
> [http://www.techdrivein.com/2012/10/ubuntu-needs-project-butter-like-android.html](http://www.techdrivein.com/2012/10/ubuntu-needs-project-butter-like-android.html)

Ubuntu needs a project butter.

Agreed.
Maybe they should dedicate a version for it.  like 13.04.

---

### Post by Swagman on 2012-10-20
Ok ..Back with the nouveau driver and it's working again... The sidebar even pops out correctly, but the redraw is painfully slow.

Interestingly @ Grub screen I tried recovery mode but was left with a blank screen so couldn't even see what options were there !!

Bah !

---

### Post by ZarathustraDK on 2012-10-20
Had a couple of gripes during clean install:

- Wanted to try using Btrfs for my system-disk, got a "sparse-error" and the system locked up when rebooting. Redid the install with ext4, no problems.

- At first installation attempt a lot of the desktop-decor was missing, replaced by white rectangles.

- When dropping to the commandline, I get a recurring I/O-error on /dev/fd0, whatever that is. EDIT: blacklisting floppy in /etc/modprobe.d/blacklist got rid of the error.

- Switching to the binary Nvidia-driver with the software updater left me with no interface after reboot. Just a clean wallpaper. Fixed it by making a folder, entering it and then navigating to the firefox-binary, went to Nvidia's driver page and got their blob, killed lightdm, installed kernel-headers and installed the blob. Then it worked.

Yeah, 12.10 unity and nautilus seems a lot slower than in 12.04. Hope it gets better. Programs, games and stuff run nice and fast just like 12.04, but the bulk of interface navigation has taken quite a hit in this version, it just feels downright sluggish.

---

### Post by KiwiNZ on 2012-10-20
Hmmm spent yesterday spanner and screw driving 12.10, it still runs like a badly tuned Model T Ford or a 2012 Kia Picanto. This not what a modern OS should be like. I tried it on a i7 with 16GB Ram and still had serious performance issues, I fail to see how these issues could be missed in Beta testing, and if they were present and noted the release should have been delayed.

---

### Post by Swagman on 2012-10-20
Please pray to whatever diety floats your boat for me coz I've just nuked /

with a clean install and I hope I've done it right. It's a long time since I've clean installed.

Weirdly, running from live cd and it all runs hunky dory so perhaps I had some crud in there that was conflicting ?

---

### Post by offgridguy on 2012-10-20
> **not found said:**
> Could it be that Unity 3D is being rendered via the CPU (ala fallback mode) and not by the GPU?


404
What actually is unity 3D ?

---

### Post by sffvba[e0rt on 2012-10-20
> **KiwiNZ said:**
> Hmmm spent yesterday spanner and screw driving 12.10, it still runs like a badly tuned Model T Ford or a 2012 Kia Picanto. This not what a modern OS should be like. I tried it on a i7 with 16GB Ram and still had serious performance issues, I fail to see how these issues could be missed in Beta testing, and if they were present and noted the release should have been delayed.

[-X I drive a [s]2012[/s] 2013 Kia Picanto (which makes no sense to me as I bought it in 2012 :p) and it runs like a beast.

> **offgridguy said:**
> What actually is unity 3D ?

Initially there was two versions for Unity, one that needed 3D acceleration and a 2D version written in Qt that didn't.

Now there is only the "3D" version that needs acceleration but there has been a tweak that makes it possible for it to use the CPU if a GPU capable of the rendering isn't found.


404

---

### Post by tjeremiah on 2012-10-20
alright I think im done for a week. Cant get compiz to behave and cant get the proper AMD drivers to install like I managed to do without a problem with the BETA!!!!! 

Unity keeps crashing (disappearing), system seems a bit slow and this is me using Ivy bridge  w/ 4GB RAM 2.8ghz (3.5turbo) i5 CPU/System when as said at least 2 times now was a lot smoother during the BETA stages of testing...

Also, I notice the S.updater still doesnt work. It always tells me to check my connection. Thought this would be fix before release. 

I think im going to take a day off and cool down. Hopefully the NY JETS win tomorrow :) .

Sorry for being annoying.

---

### Post by kevdog on 2012-10-20
Thank god I've made the decision not to upgrade.  Seems like a half baked release from reading these comments.  Very disappointing to me.

---

### Post by Swagman on 2012-10-20
Back

Clean installed and kept all our logins, which is the advantage of a separate /Home. Even Thunderbird kept all our ISP settings etc

It was running surprisingly well using Nouveau but I've selected nvidia-experimental.

Installed ubuntu-restricted-extras and CCSM.

Display is crystal clear, very sharp :)

No Wobbly Windows though :(


All in all... Not bad.

Might disable that "search the net for everything" option in Privacy though as the dash gets a tad cluttered.

eg:

Before I nuked / I had Shutter installed. Now as stuff is *supposed* to install in /Home I did a search for it.... Some weird results

[img]http://img267.imageshack.us/img267/5497/dash1j.jpg[/img]

---

### Post by Swagman on 2012-10-20
> **kevdog said:**
> Thank god I've made the decision not to upgrade.  Seems like a half baked release from reading these comments.  Very disappointing to me.

If you're still on 11:10 I do recommend you upgrade to 12:04

---

### Post by KiwiNZ on 2012-10-20
> **not found said:**
> [-X I drive a [s]2012[/s] 2013 Kia Picanto (which makes no sense to me as I bought it in 2012 :p) and it runs like a beast.



Initially there was two versions for Unity, one that needed 3D acceleration and a 2D version written in Qt that didn't.

Now there is only the "3D" version that needs acceleration but there has been a tweak that makes it possible for it to use the CPU if a GPU capable of the rendering isn't found.


404

My Sister in Law has a Kia Picanto I can accelerate faster in my wheelchair :P

0 - 100KMH takes from 8am to 11.47am

---

### Post by sffvba[e0rt on 2012-10-20
> **KiwiNZ said:**
> My Sister in Law has a Kia Picanto I can accelerate faster in my wheelchair :P

0 - 100KMH takes from 8am to 11.47am

:cry:  I guess...

As for 12.10, sounds on par for a .10 release so far, a mixture of YMMV.


404

---

### Post by sammiev on 2012-10-20
I switched over my last laptop to 12.10 yesterday. All run perfect but an update release one week before the lease caused the shut down time to increase from 3 seconds to 15 seconds. 12.10 is faster and runs cooler on all 5 laptops. All else is perfect. :)

---

### Post by thatguruguy on 2012-10-20
> **Swagman said:**
> Back

Clean installed and kept all our logins, which is the advantage of a separate /Home. Even Thunderbird kept all our ISP settings etc

It was running surprisingly well using Nouveau but I've selected nvidia-experimental.

Installed ubuntu-restricted-extras and CCSM.

Display is crystal clear, very sharp :)

No Wobbly Windows though :(


All in all... Not bad.

Might disable that "search the net for everything" option in Privacy though as the dash gets a tad cluttered.

Install the compiz-plugins metapackage using synaptic. Wobbly windows is in there.

---

### Post by Swagman on 2012-10-20
> **thatguruguy said:**
> Install the compiz-plugins metapackage using synaptic. Wobbly windows is in there.

Indeed it is Thankyou and I've also found the culprit that stops the sidebar popping out.

Yup.. compiz-plugins... Wobbly Windows !!

:(

Bah ..Uninstalling compiz-plugins wont return the sidebar to it's former function

[Edit]

Scratch that.. Restarted X and we're back. Looks like I'll have to live without the Wobblies.

Wonder how long it'll take for a fix ?

---

### Post by PaulInBHC on 2012-10-20
Backed up home from 12.04 to an external drive. Installed 12.10 on separate partition. Started up ok with ATI 5670. Restored home from backup. Installed proprietary driver.
Downhill from there.
Walked away for a while, came back to black screen, flashing caps lock light, would not wake up. Hit restart button, no unity. blablablah
Back to 12.04, I have a wedding to attend.

---

### Post by mr john on 2012-10-20
Haven't had much time for testing, but the software centre still takes a long time to load on older machines (compared to firefox & chrome). 

On my HP G6 laptop I was unable to get the iso to start a usb (unetbootin, works fine on my other computers). The screen goes black and then nothing happens. OOTB it's a failure, but I'm going to play around with some other options to see if i can find another way to make it work. If I do that I'll post a tutorial for anyone else that might be interested in installing Ubuntu on this type of laptop. HP are the 2nd biggest PC manufacturer, so I'm sure there are quite a few people with this model.

note: 12.04 would start with different boot options, but 12.10 is proving more tricky.

---

### Post by ~LoKe on 2012-10-20
Running pretty good here.  Haven't had UBuntu since around 9.04.  Having lots of problems with 12.10 though (nVidia Drivers, as usual...).

---

### Post by Peeved Chemist on 2012-10-20
> **philinux said:**
> Flipping evolution keeps crashing though. I hope that settles down.

That's more progress I've made with evolution.  Bug #1055973 is going to send me back to 12.04 - since I can't even get my mail backup to restore in 12.10.

It's a real shame, because 12.10 definitely seemed nicer on my X200 Tablet ... other than the fact that I can't use e-mail.

---

### Post by ade234uk on 2012-10-21
Hopefully Ubuntu 13.04 will improve on performance issues, because I remember when Ubuntu used to fly. 

All in all I like 12.10. Performance could always be better and I have experienced the odd bug, but these will be sorted and ironed out. 

The bigger picture, I just take a step back and actually look at how far Ubuntu has come and what they are trying acheive is fantastic.

---

### Post by KiwiNZ on 2012-10-21
Painfully slow performance, crashes and constant errors, Evolution you total pain of an App. I have removed 12.10 from all machines, what an embarrassing release.Final grade F.

---

### Post by DobsonM on 2012-10-21
Absolutely perfect over here.  Not one error message, not one crash or freeze.  Super happy with 12.10.

---

### Post by mr john on 2012-10-21
> ubuntu used to fly

I miss those days. I'm hoping 13.04 addresses the performance issues. I've heard they are going to be focusing on making things lighter, but it's going to be a long wait and I will believe it when I see it. I think alot of resources are going into Ubuntu One, Unity and the software centre, features which for most of us techies aren't really crucial. I use the command line to install apps, never use Ubuntu One and only use Unity because it's shiny.

---

### Post by qyot27 on 2012-10-21
I seem to remember some of these same issues occurring when I first installed 12.04, but unfortunately I didn't write down what fixed them then, so have little to go on now.

As a summary,
*The first and most egregious problem was that the Ubiquity slideshow crash is still there, bringing the entire install process down with it.  Thankfully the fix is just to purge ubiquity-slideshow-ubuntu before attempting the install, but this is something that *really* should have been fixed after it happened with Precise.

*The OS code name identifier in /usr/share/python-apt/templates/Ubuntu.info doesn't properly identify Quantal Quetzal the way it has for prior releases - the new section for Quantal is there, and the important bits of data for the repos are correct, but the full information still calls it 12.04 Precise Pangolin.  This caused an issue because I have Conky set up to read the code name from here and it actually wasn't displaying *anything*.  I had to manually amend it to the correct number and code name and then it was happy.

*My graphics settings don't stick.  I open the NVIDIA X Server settings, turn the brightness and gamma down so my screen doesn't look absolutely washed out, and then reboot.  It's washed out again.  It's like it's not even reading the configuration file anymore.  Tried with two of the proprietary drivers (as nouveau doesn't allow you to do anything like this except possibly through xorg.conf, or I just haven't found the nouveau-centric way yet), but since I saw talk earlier in the thread of the Experimental driver being the one to use, I'll try that next.

*As usual, Unity works fine (if sluggish, but that's expected when dealing with a Coppermine-based Celeron and GeForce 6200 PCI) when I first install and haven't done any tweaking.  But after I start to set stuff up so that I can get other work done, it stops doing so - no Dash, no panel, nothing but the background and the right-click menu.  I have to Ctrl+Alt+F1 just to use the system again.  Thank goodness I learned my lesson last time and didn't have it set to automatically log in or else I'd have to dig up how LightDM manages your default DE again.

*LXDE's DPI settings are not right.  I got MATE looking normal with 96 DPI and adjusting the font settings, but LXDE is set at 86x84 and while the menus and system stuff look relatively okay, Conky's text is huge and overflows the area I set for it.  This may be related to the driver issues so I'll have to wait until I've tested the experimental driver too before going into .conkyrc and changing things.



Other than those things, it seems stable enough.  I still have stuff to install to finalize things, though (like my cross-compiling environment and video tools).  I also need to find out how to make it see the secondary user account, because it's not showing up.

---

### Post by robert shearer on 2012-10-21
> **KiwiNZ said:**
> Painfully slow performance, crashes and constant errors, Evolution you total pain of an App. I have removed 12.10 from all machines, what an embarrassing release.Final grade F.

Agreed, **Vistabuntu.**

---

### Post by georgelappies on 2012-10-21
Terrible release...

My WiFi keeps on getting disconnecting and has problems authenticating with the access point.

After installing ATI proprietary drivers there is no more Unity. I need the ATI drivers to play some games.

Using the dash now just throws a lot of amazon clutter at you instead of being useful, this should be DISABLED BY DEFAULT.

Worst is I actually paid for this release :confused: 

Wiped it after a few tormented hours and is back on 12.04.01. I really, really hope this release and thought pattern is not what the future holds for Ubuntu...

---

### Post by mips on 2012-10-21
This thread saved me from wasting some of my data plan.

---

### Post by vasa1 on 2012-10-21
> **georgelappies said:**
> ...
Worst is I actually paid for this release :confused: 
...
Someone was arguing about whether "pay" is an appropriate term. I think it's just another example of poor communication we've been seeing a lot of recently.

IANAL, but "pay" implies something contractual. I feel Canonical should have gone with "contribute".

---

### Post by alphacrucis2 on 2012-10-21
Running well here once I installed the nvidia experimental driver. Everything is fast and snappy. I was getting colord crashing every boot on 12.04. No crashes at all on 12.10 so far. The only thing I miss is some of the compiz effects like burn on close have been removed.

---

### Post by Paqman on 2012-10-21
Quite like it, it's nice and snappy and the integration of Google documents into Dash searches is a killer feature. The Dash is now quick enough to be actually usable, so I'm trying out opening things with that instead of Synapse.

As for Software Centre. It was always painfully slow, it's still painfully slow. I don't use it except to install the odd random .deb.

---

### Post by alphacrucis2 on 2012-10-21
> **Paqman said:**
> Quite like it, it's nice and snappy and the integration of Google documents into Dash searches is a killer feature. The Dash is now quick enough to be actually usable, so I'm trying out opening things with that instead of Synapse.

As for Software Centre. It was always painfully slow, it's still painfully slow. I don't use it except to install the odd random .deb.

gdebi is still in the repos and is much faster for installing deb files than software centre. You can also install deb files from the command line via dpkg -i ....

---

### Post by Swagman on 2012-10-21
One thing that annoys me is..

I (instinctively) click on the cog at the top right of the screen to see if there are any software updates and the option isn't there !!

Grrr

Open dash just to see if there are any updates !

---

### Post by Paqman on 2012-10-21
> **alphacrucis2 said:**
> gdebi is still in the repos and is much faster for installing deb files than software centre. You can also install deb files from the command line via dpkg -i ....

All true. I don't really do it enough to bother though. I can handle opening Software Centre once in a blue moon to install a .deb, I'd hate to be using it every day. It'a a lovely app once it launches, but it's just teeth-grindingly slow to launch.

---

### Post by andriansah on 2012-10-21
I installed on virtualbox on 12.04, it's a little bit slow i think. 
I will look it again later

---

### Post by Paqman on 2012-10-21
> **andriansah said:**
> I installed on virtualbox on 12.04, it's a little bit slow i think. 
I will look it again later

A VM is not a great place to judge the speed of an OS.

---

### Post by sffvba[e0rt on 2012-10-21
> **andriansah said:**
> I installed on virtualbox on 12.04, it's a little bit slow i think. 
I will look it again later

With the lack of Unity 2D using 12.10 in a VM should be slow as all graphics rendering will also be done by the host CPU which is already taking the punch of running to OS's... Yes, they should have thought about that before the change...


404

---

### Post by tjeremiah on 2012-10-21
quick question. If install ubuntu 12.04 on my machine, when 13.04 is release would I be able to upgrade straight to that verison?

---

### Post by vasa1 on 2012-10-21
> **tjeremiah said:**
> quick question. If install ubuntu 12.04 on my machine, when 13.04 is release would I be able to upgrade straight to that verison?
Very much doubt it.

---

### Post by vasa1 on 2012-10-21
Quidsup reviews 12.10: [http://youtu.be/OZSJprVBVcs](http://youtu.be/OZSJprVBVcs)

---

### Post by Paqman on 2012-10-21
> **tjeremiah said:**
> quick question. If install ubuntu 12.04 on my machine, when 13.04 is release would I be able to upgrade straight to that verison?

No. From 12.04 you can either upgrade to 12.10 or to 14.04 when it comes out. You would need to upgrade twice (12.04 > 12.10 > 13.04).

---

### Post by tjeremiah on 2012-10-21
> **vasa1 said:**
> Quidsup reviews 12.10: [http://youtu.be/OZSJprVBVcs](http://youtu.be/OZSJprVBVcs)

its a good thing Ubuntu.com removed their Windows 8 "jab."

---

### Post by tjeremiah on 2012-10-21
> **Paqman said:**
> No. From 12.04 you can either upgrade to 12.10 or to 14.04 when it comes out. You would need to upgrade twice (12.04 > 12.10 > 13.04).

ok. Well im going to install Ubuntu 12.04 on my machine getting rid of 12.10 completely. IF I hear some good news, bug fixes, etc in the coming weeks, I might go back to 12.10 to see if all is good. 

Later.

---

### Post by exploder on 2012-10-21
I have installed 12.10 on my HP DV6 laptop with ATI discrete graphics. 12.10 runs perfectly with my hardware, I had problems with 12.04 as far as graphics. The new release is not as snappy as the LTS but the hardware is working much better. With the LTS one of the cores on my quad core processor would max out almost all of the time, with the new release the problem is gone.

Also when I tried the LTS on my laptop installing the ATI drivers was tricky and I would get an error, with 12.10 the ATI drivers installed with no problems.

For my hardware, I figure I would rather have a slightly slower system that works properly. Also, 12.10 was just released and updates over time might speed it up a little. 

Yesterday I installed 12.10 on my father-in-laws 6 year old HP desktop, it was a little sluggish but everything worked perfectly. The desktop has on-board Intel graphics and even Plymouth displayed nice with the new release. This is my father-in-laws first time running Ubuntu, he has had constant virus issues with Windows. I am anxiously waiting to hear how he gets along using Unity. I almost installed the LTS on his computer but decided to give him the refinements that have been made to Unity. I am hoping my father-in-law enjoys Unity but I did tell hime that I would put Windows back on his computer if he did not like it. 

Time will tell but I like 12.10 and maybe after some updates arrive it will get a little quicker. I did notice that higher end games ran just fine so really the only thing that is slower seemed to be Unity. The Ubuntu developers are working on Compiz and they have their hands full with other projects too.

---

### Post by wykedengel on 2012-10-21
> **CrusaderAD said:**
> *If you turn off online results in the dash, not only do you turn off shopping, but your social results as well. Maybe I just don't want ads...

Try this: ```
sudo apt-get remove unity-lens-shopping
```

---

### Post by PC_load_letter on 2012-10-21
I'm not sure if this has already been mentioned, but in this review:
[http://www.zdnet.com/ubuntu-linux-12-10-review-better-but-slower-7000005948/](http://www.zdnet.com/ubuntu-linux-12-10-review-better-but-slower-7000005948/)
The author is saying pretty much the same thing and he is suggesting that the shift to **llvmpipe** is causing that + other video playing issues.

In my experience, 12.04.1 is simply amazing and very snappy, I hate it to have to go slower now.

---

### Post by monkeybrain2012 on 2012-10-21
Guess it depends on your hardware. My impression is opposite. I find compiz more efficient and uses less cpu in 12.10 then in 12.04 with the Nvidia driver and chrome also consumes much less cpu with multiple tabs open. 12.04 is smooth with nouveau but it is not very good with the Nvidia proprietary driver.  Boot time is about the same as 12.04 (about 15s) but log in time is much faster for 12.10. Some bugs in Unity are also fixed.  Applications do seem to open a bit slower, but not  a lot. The only problem so far is that gecko-mediaplayer doesn't work in both Firefox and Chrome. Made a thread about that but there is no response. [URL="http://ubuntuforums.org/showthread.php?t=2073487"]http://ubuntuforums.org/showthread.php?t=2073487  
[/URL]

---

### Post by qyot27 on 2012-10-22
So to follow up what I'd posted earlier,
> **qyot27 said:**
> *My graphics settings don't stick.  I open the NVIDIA X Server settings, turn the brightness and gamma down so my screen doesn't look absolutely washed out, and then reboot.  It's washed out again.  It's like it's not even reading the configuration file anymore.  Tried with two of the proprietary drivers (as nouveau doesn't allow you to do anything like this except possibly through xorg.conf, or I just haven't found the nouveau-centric way yet), but since I saw talk earlier in the thread of the Experimental driver being the one to use, I'll try that next.
So yeah, the experimental driver does even things out a lot (when working X-less, I can actually see everything on the screen instead of it hanging off one edge), but it still had the issue with not retaining settings.  A Google search brought up a similar topic on the Arch forum and that revealed the actual cause: nvidia-settings isn't even writing the Brightness and Gamma adjustments into .nvidia-settings-rc, resulting in it being lost on log out or reboot - adding them in manually is the only thing you can do.  After that it worked fine.

> *LXDE's DPI settings are not right.  I got MATE looking normal with 96 DPI and adjusting the font settings, but LXDE is set at 86x84 and while the menus and system stuff look relatively okay, Conky's text is huge and overflows the area I set for it.  This may be related to the driver issues so I'll have to wait until I've tested the experimental driver too before going into .conkyrc and changing things.
The DPI setting issue was resolved by editing xorg.conf, and Conky's issue could only be fixed by reducing the font size.  Still no idea why the exact same point size that was reasonable in 12.04 was suddenly too big now.  I actually had to err on the side of being too small, since stepping the size down just one point still made the text overflow the window boundary.

---

### Post by KiwiNZ on 2012-10-22
This release is simply not good enough for a product in it's eight year. If we are ever going to get above the 1% we cannot release products that will require the user to spend hours searching the web for solutions for things that just should work and then spending fruitless days trying to man handle the OS to work.

---

### Post by BigSilly on 2012-10-22
> **KiwiNZ said:**
> This release is simply not good enough for a product in it's eight year. If we are ever going to get above the 1% we cannot release products that will require the user to spend hours searching the web for solutions for things that just should work and then spending fruitless days trying to man handle the OS to work.

Hmmm. A bit of tweaking here and there is to be expected of any OS, but having to wrangle the thing into working form is where I draw my line personally. That said, I'm using the KDE variant of 12.10 and it's really excellent, and I haven't had any major issues at all.

---

### Post by CrusaderAD on 2012-10-22
After using it for a few days, it has been a rather bumpy start. Remote Desktop crashes, stupid app pop ups trigger all over firefox to "install the app", which is garbage imo. I don't need a glorified bookmark on my launcher that just pops up firefox. I'd like to be able to remove the thing if I wanted to (maybe this functionality is out there and I'm just no seeing it?), but seems to be forever stuck in my dash. The background in the login screen doesn't always seem to work. It's a lot of really little things that add up quick. This was the worst beta I've used, and I don't see many performance improvements since the beta. Might switch back to Xubuntu for a bit till this gets ironed out.

---

### Post by oldgraf on 2012-10-22
After long time with Lucid I reinstall my Toshiba with Xubuntu 12.10, then with Lubuntu. Both have problem with Intel 3945ABG wifi card. Connect to router OK, buth speed is very slow - no more 150 KB/s and skype disconnect under install of office suit or wine. Never had this in Lucid. For any one with this problem 
create file /etc/modprobe.d/iwl3945.conf and paste next contents
alias wlan0 iwl3945
options iwl3945 disable_hw_scan=0
then reboot and all is fine like in Lucid ~2700 KB with my Linksys 54gl router WPA2 security

---

### Post by cbennett926 on 2012-10-22
With the specs in my signature, would you recommend an upgrade or just stick with the LTS?

---

### Post by mr-woof on 2012-10-22
Tonight I took the plunge and upgraded from 12.04 to 12.10, all went well, at least I thought it did. Unity appears to be broken, I'm currently logged in with Gnome Classic. 

Unity won't start, no sidebar, no bar at the top, but I can change the background etc, now on top of that the software centre keeps crashing :(

I might go for the fresh install and see how I get on

---

### Post by KiwiNZ on 2012-10-22
I am hearing praises of Kubuntu 12.10, so I am going to give it a whirl on one of my test machines

---

### Post by OrangeCrate on 2012-10-22
> **KiwiNZ said:**
> **This release is simply not good enough for a product in it's eight year.** If we are ever going to get above the 1% we cannot release products that will require the user to spend hours searching the web for solutions for things that just should work and then spending fruitless days trying to man handle the OS to work.

Though I normally do take a look at the Ubuntu releases, I'm an Xubuntu guy, and when I booted up the Xubuntu final, and saw that there were still two floppy disk drive icons on the desktop, I was speechless (I first saw this problem in Alpha 3) - what are these people thinking, letting this go past the final release?

Edit:

Was looking for the bug report, found it:

[https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1039375](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1039375)

and, a related thread:

[http://ubuntuforums.org/showthread.php?p=12291525](http://ubuntuforums.org/showthread.php?p=12291525)

---

### Post by KiwiNZ on 2012-10-22
I have installed Kubuntu 12.10 on a test machine, a machine I had previously tried unbuntu 12.10 on and Kubuntu  so far is performing well.

---

### Post by tjeremiah on 2012-10-22
ill do a clean install of Kubuntu "soon" and will report back.

---

### Post by thatguruguy on 2012-10-22
As noted earlier, everything on my computer has seemingly sped up since I first moved up to 12.10.  Everything except for Software Center, at least. It's still a dog.

---

### Post by vasa1 on 2012-10-22
quidsup looks at Xubuntu 12.10 here: [http://www.youtube.com/watch?v=HVYwnbHbKJQ](http://www.youtube.com/watch?v=HVYwnbHbKJQ)
He's also looked at Kubuntu 12.10.

---

### Post by cbennett926 on 2012-10-22
FWIW, and this may be because I somewhat intentionally bought an Ubuntu Certified laptop, I absolutely loved it and it just so happened to be certified, but I did an upgrade and this rig ROCKS! I just wanna scream from the mountains how awesome 12.10 is.

It's the little things that I noticed, it seems the panel on the top has been slimmed down, and the battery charging notification looks different when it is fully charged. My dash and launcher are running 2-3x faster, and the new Amazon store is pretty sweet too! 

I know most people do not like this release from what I have seen, however I for one love the direction this is headed and I wish there was a way I could contribute more!

---

### Post by cbennett926 on 2012-10-22
I was looking for this thread when I made a thread, any mod who see's this please merge :)

---

### Post by ArtF10 on 2012-10-23
Xubuntu 12.10 - haven't tried it, but it looks and feels the same (based on youtube videos). Boring. This used to be my main flavour of Ubuntu but I realized that it is NEVER updated in terms of its look. Very disappointing.

LUbuntu 12.10 - using this. New artwork and theme.....LOVE THESE! For me, Lubuntu has gone past Xubuntu, in terms of look and feel. If you really want lightweight, don't bother with Xubuntu...it is pointless. Lubuntu is the way to go. If you disagree, then you don't really NEED lightweight, in which case you shouldn't be bothering with LXDE or XFCE.

However, a few problems with Lubuntu 12.10:
a. Loading is slower.
b. The "Customize the Look and Feel" dialog box crashes when I try to install Faenza icons.

Ubuntu 12.10 - TBD

Kubuntu 12.10 - Never tried. Never will.

---

### Post by sffvba[e0rt on 2012-10-23
*Threads **merged**.*


404

---

### Post by Erik1984 on 2012-10-23
> **vasa1 said:**
> quidsup looks at Xubuntu 12.10 here: [http://www.youtube.com/watch?v=HVYwnbHbKJQ](http://www.youtube.com/watch?v=HVYwnbHbKJQ)
He's also looked at Kubuntu 12.10.

Thanks, those are nice reviews.

---

### Post by qyot27 on 2012-10-23
> **ArtF10 said:**
> However, a few problems with Lubuntu 12.10:
a. Loading is slower.
b. The "Customize the Look and Feel" dialog box crashes when I try to install Faenza icons.
How did you try to do it?  Since the equinox ppa hasn't been updated to work with Quantal yet, I just added the one for Precise and snagged them from there.  No crashing for me.

Granted, I'm using regular Ubuntu with LXDE installed on top of it rather than Lubuntu, but I don't see why that should matter.

---

### Post by Chdslv on 2012-10-23
> **KiwiNZ said:**
> I have installed the final release on a test Laptop. Everything works, but it is slow. Opening the Software Centre takes around 20 seconds, Firefox 22 seconds, Libre Office Calc 17 seconds. Opening a simple Game in this case Naval Battle 15 seconds.

Now I know these numbers are not big, but on the same rig 12.04 was running considerably snappier. This was the rig that I recently tested Kubuntu on and creaking behemoth was snappier. One positive it did OK with my annoyingly fussy HP ink jet printer although it cannot find my Laser Printer.

Overall my initial score is B-

Try this;

1) Download and Install Lubuntu 12.10,
2) Install Unity through Synaptic. About 65MB. You'd get Compiz-core too, and some lenses.
3) Restart and log into Ubuntu
4) Install any apps you want

Here is the screenshot. Didn't take out shopping lens, just to show you guys, but I'd delete that.

If you want the Gnome experience, install Gnome-shell through Synaptic.

And another screenshot with Gnome-shell.

No hitches, no crashes. Smooth as could be.
Rig: Lenovo T400, 2.8GB memory. Age more than 3 years, nearing 4th.

Ubuntu itself with Unity or without, with Gnome is somewhat slow, but Lubuntu, that is Ubuntu+LXDE+Gnome or +Unity is snappier.  

Good day!:)

---

### Post by sffvba[e0rt on 2012-10-23
Just did an install of 12.10 on my Gaming rig... and works like a charm.

Haven't spent enough time with it to say it is faster/slower than 12.04.  The only odd thing thus far is that I couldn't find a way to isntall restricted drivers.  Had to go to the AMD site and read up on doing it command-line.  Well it worked at least :)



404

---

### Post by Erik1984 on 2012-10-23
> **Chdslv said:**
> Try this;

1) Download and Install Lubuntu 12.10,
2) Install Unity through Synaptic. About 65MB. You'd get Compiz-core too, and some lenses.
3) Restart and log into Ubuntu
4) Install any apps you want

Here is the screenshot. Didn't take out shopping lens, just to show you guys, but I'd delete that.

If you want the Gnome experience, install Gnome-shell through Synaptic.

And another screenshot with Gnome-shell.

No hitches, no crashes. Smooth as could be.
Rig: Lenovo T400, 2.8GB memory. Age more than 3 years, nearing 4th.

Ubuntu itself with Unity or without, with Gnome is somewhat slow, but Lubuntu, that is Ubuntu+LXDE+Gnome or +Unity is snappier.  

Good day!:)

The Gnome Shell marks for memory and cpu usage are quite impressive on that screenshot. Is Gnome Shell running compositing effects and all?

---

### Post by Luffield on 2012-10-23
I upgraded my desktop computer to 12.10 a few days ago. I ususally use Xfce but after the upgrade xfce4-panel segfaults so I don't have panels. Gnome-shell didn't work either (can't remember why). Gnome classic works, but the windows don't have title bars. Unity works, but I don't like this interface very much and it seems to be slower than it was last time I used it (a few months ago).

I've been using Ubuntu since 5.10 and so far my experience with 12.10 can be summed with the words "worst version yet". I'm sure that a clean install would improve things but I use my 12.04 laptop most of the time so I can't be bothered to fiddle with the desktop.

---

### Post by Swagman on 2012-10-23
One thing I'm noticing is that the audio is very quiet now ?

I can hardly hear it through my headphones, even when the volume is flat out.

I'm using a Xonar turbo nutter soundcard with logitech sub.. It aint that that's the problem !!

And that's another thing.. In sound prefs, shedloads of options are no longer there !!

---

### Post by fatality_uk on 2012-10-23
Useless! Wont load. Wont work in a VM. Ubuntu has been the same for me a long while. Day to day I am using Win 7 because as a CEO for an SME I can't afford the hours/days/weeks it takes to get Ubuntu to where it needs to be.

---

### Post by newbie2 on 2012-10-23
> **fatality_uk said:**
>  I am using Win 7 because as a CEO for an SME I can't afford the hours/days/weeks it takes to get Ubuntu to where it needs to be.
Keep sticking with Win7 then , because Win8 is gonna take you also 'some time' to get where you want it ; [http://www.reuters.com/article/2012/10/22/us-microsoft-windows8-business-idUSBRE89L03N20121022](http://www.reuters.com/article/2012/10/22/us-microsoft-windows8-business-idUSBRE89L03N20121022)
:P

---

### Post by fatality_uk on 2012-10-23
> **newbie2 said:**
> Keep sticking with Win7 then , because Win8 is gonna take you also 'some time' to get where you want it ; [http://www.reuters.com/article/2012/10/22/us-microsoft-windows8-business-idUSBRE89L03N20121022](http://www.reuters.com/article/2012/10/22/us-microsoft-windows8-business-idUSBRE89L03N20121022)
:P

Will do!

---

### Post by Chdslv on 2012-10-23
> **Euroman said:**
> The Gnome Shell marks for memory and cpu usage are quite impressive on that screenshot. Is Gnome Shell running compositing effects and all?

Gnome-shell has all its own compositing effects, but don't want to work with CCSM.

With Unity and Gnome-Classic (which came with Gnome-shell) Compiz effects work superbly. In any 12.10, Compiz doesn't have Animation-addons and cylinder. I have no idea why. 12.04 had them.

Here are some screenshots;

---

### Post by mips on 2012-10-23
> **fatality_uk said:**
> Useless! Wont load. Wont work in a VM. Ubuntu has been the same for me a long while. Day to day I am using Win 7 because as a CEO for an SME I can't afford the hours/days/weeks it takes to get Ubuntu to where it needs to be.

Ubuntu went for the bling factor. I reckon you are better off installing something like Debian, Opensuse etc. Don't be restricted by a single linux distros, there are many other good ones out there.

Maybe try Crunchang testing and add Gnome. It's based on debian testing which in itself is not that unstable and pretty close to release when considering debian time frames.

---

### Post by linuxvstheworld on 2012-10-23
Hello all,

          It's only been a couple of days since the release of Ubuntu 12.10, but with it's great features and additions such as the updated Linux Kernel, and more controversial features, like the shopping lens, which has been reported to bring up shopping results when one is searching for an application, which seems rather annoying, but that's just me. What does the forum think about this release? (I think it's great..... many improvements.)

---

### Post by sffvba[e0rt on 2012-10-23
*Threads **merged**.*


404

---

### Post by *^kyfds( on 2012-10-23
> **linuxvstheworld said:**
> Hello all,

          It's only been a couple of days since the release of Ubuntu 12.10, but with it's great features and additions such as the updated Linux Kernel, and more controversial features, like the shopping lens, which has been reported to bring up shopping results when one is searching for an application, which seems rather annoying, but that's just me. What does the forum think about this release? (I think it's great..... many improvements.)

Am I the only one here who doesn’t mind ads?

I mean, canonical are a company, and they need a stable source of income...

---

### Post by KiwiNZ on 2012-10-23
For the first time ever Kubuntu is performing way better than Ubuntu on any of my machines.

---

### Post by MasterNetra on 2012-10-23
> **Thehumorouscheese said:**
> Am I the only one here who doesn’t mind ads?

I mean, canonical are a company, and they need a stable source of income...

As long as they're not pop ups, I don't really care. I usually ignore 99% of ads anyway.

---

### Post by Paqman on 2012-10-23
I use Google Docs a lot, so for me having them integrated into the Dash is miles and miles of win. The Dash seems a lot quicker now too, to the point where it's actually useful instead of a pain.

---

### Post by sffvba[e0rt on 2012-10-23
Just did an upgrade from 12.04 to 12.10 on my lappy... so far so good, nothing strange to report.


404

---

### Post by mips on 2012-10-23
> **Thehumorouscheese said:**
> Am I the only one here who doesn’t mind ads?

I mean, canonical are a company, and they need a stable source of income...

I don't like adds, they take up part of my data allocation. I use addblock, flashblock etc on my pc, turn off auto media information fetching in vlc etc

---

### Post by seenthelite on 2012-10-23
I have installed Xubuntu 12.10 on one older Laptop and am pleased with it. Tried Kubuntu on my Desktop and had problems with the installer, if I I had install additional software ticked the install would not go any further so I tried without that and the install stopped at 90% then I tried disconnected from the internet and the install completed but will not resume from sleep. So I have removed it. I have Mint 13 KDE on that machine working really well anyway. I will stay with  Ubuntu 12.04 on the other machines I have it installed on.
This release is the first from the changed testing regime and I have observed that the Ubuntu +1 Forum is not as active as in the past and a large number of experienced very active testers have gone from there.

---

### Post by MasterNetra on 2012-10-23
Just installed 12.10 (clean install). First off the installation. I like that fact we finally have a straight up easy option to encrypt our hard drive like you can do in fedora..finally! So naturally (for me) I installed 12.10 encrypting the entire drive in addtion to encrypting home dir (for the heck of it). One thing I did notice doing this though using a long password triggers a message that claims its a short password, despite my password being over 24 chars (its easy for me to remember though).

 Other then that, 12.10 seems fine thus far. Still testing though. Apps seems to load fine, firefox loads up quickly, at least once all the startup stuff Ubuntu is doing behind the scenes is finished. Also as reported, Dash is much snappier. I also noticed a driver selection thing in Sources (Addtional Drivvers tab) now. Don't know if that was in 12.04, didn't notice it there but meh.

*Update* Once again STA driver does not work for me at all. And Addtional driver tab in sources is claiming I have a bcm 4311 instead of a 4312 for wireless... O.o

---

### Post by suprman2020 on 2012-10-23
Not a good experience so far. Everything works with the exception of the switchable AMD graphics. I've been going through hell trying to get it to work but the drivers provided by AMD don't work.

Ubuntu Gnome Remix is really good. I just there were working drivers so it can be used at its full potential.

---

### Post by fatality_uk on 2012-10-23
> **mips said:**
> Ubuntu went for the bling factor. I reckon you are better off installing something like Debian, Opensuse etc. Don't be restricted by a single linux distros, there are many other good ones out there.

Maybe try Crunchang testing and add Gnome. It's based on debian testing which in itself is not that unstable and pretty close to release when considering debian time frames.

It's not the distro as such MIPS, it's the lack of a fully compatible Office suite to match Microsoft Office. Yes OOo & LibreOffice are good if you create the docs in them, but try getting a Office 2010 from a client to format as expected just doesn't happen. 2013 is worse, I know I use it and Libre just gives up on many docs.

I and many other Linux users have been banging on about this for YEARS! If the big Linux companies got together, funded a project for LibreOffice with the sole purpose of being 99.9999% compatible with MS Office, you could easily add 10,000,000 small business installs around the world within 2 years.

That feeds into tech vendors being confident to sell home PC's that wont come back because little Jack can't do his homework on doc/docx files given to him by school.

Cmon Linux, get this right and the world opens up!

---

### Post by thatguruguy on 2012-10-23
> **fatality_uk said:**
> It's not the distro as such MIPS, it's the lack of a fully compatible Office suite to match Microsoft Office. Yes OOo & LibreOffice are good if you create the docs in them, but try getting a Office 2010 from a client to format as expected just doesn't happen. 2013 is worse, I know I use it and Libre just gives up on many docs.

I and many other Linux users have been banging on about this for YEARS! If the big Linux companies got together, funded a project for LibreOffice with the sole purpose of being 99.9999% compatible with MS Office, you could easily add 10,000,000 small business installs around the world within 2 years.

That feeds into tech vendors being confident to sell home PC's that wont come back because little Jack can't do his homework on doc/docx files given to him by school.

Cmon Linux, get this right and the world opens up!

Well, MIPS was referring to your earlier post that Ubuntu won't work properly in a VM. Compiz has problems properly utilizing llvmpipe in a VM. Hence, the suggestion to use another distro. Although you could also try it on bare metal, as a dual-boot with Windows 7.

---

### Post by alphacrucis2 on 2012-10-23
> **not found said:**
> Just did an install of 12.10 on my Gaming rig... and works like a charm.

Haven't spent enough time with it to say it is faster/slower than 12.04.  The only odd thing thus far is that I couldn't find a way to isntall restricted drivers.  Had to go to the AMD site and read up on doing it command-line.  Well it worked at least :)



404

The restricted drivers are installed via "Software Sources" now.

---

### Post by Chdslv on 2012-10-23
Oh, if you are using Google as your home page, then you might see "Drive" there, so you really don't need the "integration with Dash." 

Even, though 12.10 is with newer kernel etc, I think 12.04 is better. You can install a newer kernel in that too. If you like Gnome (new release), then you have to stick with 12.10.

Actually, I am waiting for 13.04 alpha release, as it would have all the pluses of 12.04, 12.10 and some more. I have been using these alphas and betas, and know that they don't fail, even though they are named pre-release/not good for production machines. :)

Over the years, I have come to trust the abilities of the Ubuntu and the community devs, my first being 4.10. By the way, it is still available for download. Why not try it, if you haven't used it before. 

Have a nice day!:)

---

### Post by SMOKE14 on 2012-10-23
12.10 is solid for me. A-, maybe B+. On my C2D/3GB RAM setup, it's about the same speed as 12.04. I use KDE desktop, and I finally got some Windows stuff running in Ubuntu. If I can just get PS to run in Ubuntu, I might not need Windows anymore! :guitar:

---

### Post by Linuxisfast on 2012-10-23
> **fatality_uk said:**
> It's not the distro as such MIPS, it's the lack of a fully compatible Office suite to match Microsoft Office. Yes OOo & LibreOffice are good if you create the docs in them, but try getting a Office 2010 from a client to format as expected just doesn't happen. 2013 is worse, I know I use it and Libre just gives up on many docs.

I and many other Linux users have been banging on about this for YEARS! If the big Linux companies got together, funded a project for LibreOffice with the sole purpose of being 99.9999% compatible with MS Office, you could easily add 10,000,000 small business installs around the world within 2 years.

That feeds into tech vendors being confident to sell home PC's that wont come back because little Jack can't do his homework on doc/docx files given to him by school.

Cmon Linux, get this right and the world opens up!
With Libreoffice adaption happening in record numbers specifically by government bodies in Europe and Asia, time is not far when the reverse would be expected that is MS would need to be compatible 100% with LO.

---

### Post by 0verm1nd on 2012-10-23
So far, not the best release. Although, I'm not sure if many of my problems are Ubuntu's fault, or due to gnome 3.6

I use gnome shell, so I can't comment on how well unity is working other than the brief time I tested it out, but 12.04 performed much better and faster on my machines than 12.10 has. The shell crashes often and graphics performance is way down. 

The archive manager crashes every time I try to extract an archive, and many other applications I install just plain don't start. I still don't bother with USC because of how slow browsing and installing is, and the Ubuntu one client is still ugly, but I can't complain as long as it works. The additional drivers aren't easily discoverable hidden in  software sources (had to really search, and ended up going back to the open source drivers after I tried out the proprietary ones anyway :p), though I assume they'll be changing software sources up a bit.
Also, the overlay scrollbars are acting oddly for me. And I'm hoping to see some more gnome shell extensions as well as gtk3 and gnome shell themes soon, but again thats a gnome issue and can't be blamed on Ubuntu. ( Is that going to happen each release?)

I'm optimistic though! If things don't improve, gnome-wise, I'll head back to 12.04 or try another distro, no big deal.

---

### Post by vasa1 on 2012-10-23
> **fatality_uk said:**
> It's not the distro as such MIPS, it's the lack of a fully compatible Office suite to match Microsoft Office. Yes OOo & LibreOffice are good if you create the docs in them, but try getting a Office 2010 from a client to format as expected just doesn't happen. 2013 is worse, I know I use it and Libre just gives up on many docs.

I and many other Linux users have been banging on about this for YEARS! If the big Linux companies got together, funded a project for LibreOffice with the sole purpose of being 99.9999% compatible with MS Office, you could easily add 10,000,000 small business installs around the world within 2 years.

That feeds into tech vendors being confident to sell home PC's that wont come back because little Jack can't do his homework on doc/docx files given to him by school.

Cmon Linux, get this right and the world opens up!

Trying to be compatible with something else is a loser's game. Some information will always be withheld or buried. It's for users to realize they've been suckered into thinking that one particular piece of software will forever be essential.

BTW, this is a totally different topic and has nothing to do with 12.10.

---

### Post by Chdslv on 2012-10-24
Have a look at Precise Puppy based on 12.04.1
It is the fastest 12.04.1 I've seen. I know this thread is about 12.10, but have a look.:)

---

### Post by KiwiNZ on 2012-10-24
> **vasa1 said:**
> Trying to be compatible with something else is a loser's game. Some information will always be withheld or buried. It's for users to realize they've been suckered into thinking that one particular piece of software will forever be essential.

BTW, this is a totally different topic and has nothing to do with 12.10.

Run an enterprise IT environment and compatibility is very important.

---

### Post by viperdvman on 2012-10-24
Doing a major data recovery on my big Data hard drive right now *(NTFS file system corrupted after a defrag)*, otherwise I would be trying Ubuntu 12.10 out right now. 

It looks like a lot of people are having both minor and major issues with this release. But, don't we have issues with **every** Ubuntu release? And surely the 12.10 issues aren't as bad as the 11.10 issues a lot of us had last year. I am curious as to how my NVidia card and proprietary NVidia drivers will work in Ubuntu 12.10. I know **nouveau** has issues with my GeForce GTX 560. But I'll just have to see before I consider making the full switch to Quantal.

Though, I was seriously considering actually switching to Kubuntu for this release cycle since I tend to use KDE **far** more than I use Unity. I do have that third empty partition for testing out full installs of Linux, so I will definitely give Ubuntu 12.10 a shot after I finish this data recovery.

---

### Post by qyot27 on 2012-10-24
> **viperdvman said:**
> It looks like a lot of people are having both minor and major issues with this release. But, don't we have issues with **every** Ubuntu release? And surely the 12.10 issues aren't as bad as the 11.10 issues a lot of us had last year.
This, although I can't really remember what the issues were with 11.10 or if I even had any that were worse than the current crop.  I know that post-install tweaking is always a given; and to its credit, I've managed to resolve all but one of those things (the importing second user thing).  So I'm back to a solid install and can basically pick up where I left off with Precise, once I get my MinGW-w64 environment compiled and ready.


Although I have no idea why this release suddenly wants to start seeing floppy drives and show them in Nautilus and PCManFM...

---

### Post by Mikeb85 on 2012-10-24
> **KiwiNZ said:**
> Run an enterprise IT environment and compatibility is very important.

Random curiosity - have you tested Google docs?  I'm curious how it stacks up against MS Office in an enterprise setting.  I personally love it, but don't really do anything too advanced with it.

---

### Post by BigSilly on 2012-10-24
Well, I can definitely say, after a week or so of using it, that Kubuntu 12.10 is performing really well for me and I have no reason to switch to anything else. I'm happy with gaming, video playback, general resource usage, attractiveness and usability with the latest KDE. In fact, I might even go so far as to say it may be the most perfect Linux I've ever used.

Thanks to Ubuntu and Kubuntu for making it happen. :)

---

### Post by KiwiNZ on 2012-10-24
> **Mikeb85 said:**
> Random curiosity - have you tested Google docs?  I'm curious how it stacks up against MS Office in an enterprise setting.  I personally love it, but don't really do anything too advanced with it.

Personally yes, in a Corporate environmental, no. I would never authorise it's use in an enterprise environment.

---

### Post by mr-woof on 2012-10-24
i generally stay on the lts versions, i had a ati card installed on 12.04 and the peformance wasn't very good, slow at looking through bookmarks, slugglish on youtube etc. So, i thought I'd upgrade, ive had no end of problems, all sorts of crashing, random errors.

I then did a fresh install using the onboard nvidia graphics, couldnt get the drivers to work, either really slow like the ati card or just a blank desktop, ive tried the onboard nvidia and two other pci express nvidia cards with the same result.

I've given up, ubuntu doesnt like my hardware, i've just installed mint 13 mate using the onboard nvidia and everything appears (touch wood) to be working so far.

what flaming nvidia cards are supported and actually work on ubuntu?

---

### Post by Mikeb85 on 2012-10-24
> **KiwiNZ said:**
> Personally yes, in a Corporate environmental, no. I would never authorise it's use in an enterprise environment.

Because of security concerns or usability?  

Anyhow, concerning Ubuntu 11.10, the Unity and Dash integration with Google Docs is pretty awesome :)

---

### Post by redhive on 2012-10-24
I tried to upgrade my ubuntu 12.04 vm to the new 12.10, but changed my mind after a pop up appeared before the installation started warning me that if I continued with the upgrade, unity would be extremely slow due to the graphics card acceleration issue (in other words, removal of unity 2d) and it recommended that I stay with the 12.04....so I did it...but still...would like to upgrade at some point - wonder if anyone will come with a solution to this problem and helps us vm users?

Any ideas? 

> **not found said:**
> With the lack of Unity 2D using 12.10 in a VM should be slow as all graphics rendering will also be done by the host CPU which is already taking the punch of running to OS's... Yes, they should have thought about that before the change...


404

---

### Post by KiwiNZ on 2012-10-24
> **Mikeb85 said:**
> Because of security concerns or usability?  

Anyhow, concerning Ubuntu 11.10, the Unity and Dash integration with Google Docs is pretty awesome :)

Security and legal.

---

### Post by mc4man on 2012-10-24
> **mr-woof said:**
> 
what flaming nvidia cards are supported and actually work on ubuntu?
Most cards 6000 & newer should work with either the default nouveau or one of the nvidia-* packages (**not** any 173 packages
You should probably start a support thread if wishing to pursue
This shows adapter
```
sudo lshw -C display
```
This will give some info about current situation
```
sudo apt-get install mesa-utils
```
```
glxinfo |egrep 'OpenGL|vendor|rendering'
```

If trying to install nvidia-* or  fglrx  please read here first
[http://ubuntuforums.org/showthread.php?t=2073060](http://ubuntuforums.org/showthread.php?t=2073060)
Basically run this first
```
sudo apt-get install linux-headers-generic
```
(A current 'bug' that ubuntu devs aren't really addressing other than won't fix on the packages & ignoring on the initial install, par for the half-baked course

---

### Post by tjeremiah on 2012-10-24
[SIZE="3"]**_[COLOR="Red"]SOLVED:[/COLOR]_**[/SIZE]

The biggest issue appeared to have been the linux-headers-generic. For a week ive been reading to install this, I have, but it didnt solve anything.

Today in the terminal I "sudo apt-get update" and "upgrade" to notice a "new" linux-headers-generic was being held back so I "sudo apt-get installed" it. 

Restarted Ubuntu, picked the 3rd optioned ATI driver in software sources. Restarted Ubuntu again to notice Unity was still there :KS 

Ran to the AMD website, install the amd catalyst BETA so I can have more control over the graphics and it installed without ERROR :guitar:

My graphic card is AMD 7500 series.

Hope this post helps some. Cheers!

---

### Post by kansasnoob on 2012-10-25
> **KiwiNZ said:**
> I have installed the final release on a test Laptop. Everything works, but it is slow. Opening the Software Centre takes around 20 seconds, Firefox 22 seconds, Libre Office Calc 17 seconds. Opening a simple Game in this case Naval Battle 15 seconds.

Now I know these numbers are not big, but on the same rig 12.04 was running considerably snappier. This was the rig that I recently tested Kubuntu on and creaking behemoth was snappier. One positive it did OK with my annoyingly fussy HP ink jet printer although it cannot find my Laser Printer.

Overall my initial score is B-

Well I'd have to give Ubuntu Quantal itself a D, but not Canonical and it's devotion to providing a flavor for every taste. I have three sets of hardware in the house. 

One has P4M800 graphics and it's a total no-go now with Ubuntu since they dropped Unity-2D/metacity in favor of Compiz + llvmpipe, but it still works OK with Xubuntu, Lubuntu, and this remix that's now in the repos:

[http://ubuntuforums.org/showthread.php?p=12304298](http://ubuntuforums.org/showthread.php?p=12304298)

The second is an Intel Atom 230 w/i945 graphics and it will run Ubuntu 12.10 but very, very slow. It's comparable to dropping from DSL to dial up :(

The third is my HTPC and it should easily run any compatible modern OS. It runs Precise like a champ, but Quantal just drags along, way too many glitches :(

And the newest grub totally stinks on a complex multi-boot. Long and sometimes incorrect menu entries, and the failure to list device designations make it virtually unusable.

But I think this is a huge transitional period and I very much expect to see things improve greatly between now and 14.04. I doubt us desktop users will see a great deal of improvement in 13.04 or 13.10 though.

So ultimately Canonical still gets an A+ but Ubuntu (the default flavor) is just too buggy. That said it's not altogether uncommon to see this just after an LTS because some of the most innovative changes are held back during LTS dev, then the next release gets a double-whammy of bleeding edge goodies :D

---

### Post by viperdvman on 2012-10-25
I ran a quick Ubuntu 12.10 LiveUSB while doing the last of my data recovery [I](it was complicated... not gonna go into why I didn't use my native Ubuntu nor my Windows).

[/I]But... I had absolutely no problems for the little bit of time during data transfer. Then again, I didn't really do a whole lot with it outside the data transfer.

---

### Post by viperdvman on 2012-10-25
> **mc4man said:**
> Most cards 6000 & newer should work with either the default nouveau or one of the nvidia-* packages (**not** any 173 packages
You should probably start a support thread if wishing to pursue
This shows adapter
```
sudo lshw -C display
```This will give some info about current situation
```
sudo apt-get install mesa-utils
``````
glxinfo |egrep 'OpenGL|vendor|rendering'
```If trying to install nvidia-* or  fglrx  please read here first
[http://ubuntuforums.org/showthread.php?t=2073060](http://ubuntuforums.org/showthread.php?t=2073060)
Basically run this first
```
sudo apt-get install linux-headers-generic
```(A current 'bug' that ubuntu devs aren't really addressing other than won't fix on the packages & ignoring on the initial install, par for the half-baked course

As far as I know, my Nvidia GeForce GTX 560 is incompatible with the nouveau drivers. But it works great with the proprietary drivers.

---

### Post by viperdvman on 2012-11-01
Finally installed **Kubuntu** 12.10 yesterday instead of installing Ubuntu 12.10 and adding KDE on top of it. Keeps it just a bit more pure that way *(less hard drive space taken up by Unity and GNOME, and their default apps)*.

Note, I'm only giving my first impressions:

Running Kubuntu 12.10 really isn't much different than running Kubuntu 12.04. All we get are the newer Linux 3.5.x kernel, a few new and/or different pre-installed apps, and the new KDE 4.9.2 *(which can be installed in 12.04 from a PPA).* It does seem a bit less buggy than KDE 4.8.5, and I like some of the improved workspaces, activities, and Dolphin features. And I especially like the extra customizability when it comes to KWin and GTK themes for GTK-based apps.

However, there are a few apps that either aren't supported anymore due to lack of maintenance (AWN and KompoZer are two of them... though AWN sucks in 12.04), or just haven't been updated to Quantal yet *(snes9x being one of them)*. It does make me think that I should've stayed with 12.04 as fewer apps are available for Quantal... and fewer PPAs work with it *(only 90% of all my PPAs that aren't GNOME/Unity/Cinnamon-centric are updated for Quantal)*. Then again, we're only a couple weeks into the release, so most of the maintained PPAs will catch up.

Other than a couple of small gripes about apps no longer available and a few PPA's not available for Quantal (affects all derivatives, not just Kubuntu), I'm liking this new Kubuntu release.

---

### Post by CrusaderAD on 2012-11-01
I figured I'd chime in and say that Xubuntu 12.10 is awesome. I'm noticing far fewer crashes that the last release (although it still has issues with bluetooth). I'm loving the theme tweaks they've done, the blue is great. I'm still running Ubuntu 12.10 on a few machines, but I've plugged Xubuntu 12.10 in on a few, and I'm not sorry. Great release.

---

### Post by viperdvman on 2012-11-01
> **CrusaderAD said:**
> I figured I'd chime in and say that Xubuntu 12.10 is awesome. I'm noticing far fewer crashes that the last release (although it still has issues with bluetooth). I'm loving the theme tweaks they've done, the blue is great. I'm still running Ubuntu 12.10 on a few machines, but I've plugged Xubuntu 12.10 in on a few, and I'm not sorry. Great release.

Xfce is probably the DE I have messed with **the least**. However, a lot of good words regarding Xfce *(though not as lightweight as it used to be... more on the lines of GNOME 2.x)* are making me want to use my empty partition to give it a full metal install and try it out. :)

---

### Post by Bear on 2012-11-01
No problems here.

Really enjoying Ubuntu 12.10 64bit.

Good job team. :cool:

---

### Post by Uncle Spellbinder on 2012-11-01
I figured I'd give Xubuntu 12.10 a try. I haven't used XFCE in a very long time and I haven't tried Xubuntu since 11.10 was first released. I was *not* a fan. It felt a bit clumsy to me. And the highlighted text on folders and files on the desktop was horrid and *very annoying*.

I'm very pleased with Xubuntu 12.10 and seeing that the highlighted desktop text is gone is a MAJOR PLUS. It feels very comfortable and quite easy to use and navigate. Not unlike a classic Gnome feel (which I love).

All-in-all, Xubuntu 12.10 is excellent thus far. I think I'll continue with it and see if it has that "staying power."

---

### Post by Elfy on 2012-11-02
> **Uncle Spellbinder said:**
> I figured I'd give Xubuntu 12.10 a try. I haven't used XFCE in a very long time and I haven't tried Xubuntu since 11.10 was first released. I was *not* a fan. It felt a bit clumsy to me. And the highlighted text on folders and files on the desktop was horrid and *very annoying*.

I'm very pleased with Xubuntu 12.10 and seeing that the highlighted desktop text is gone is a MAJOR PLUS. It feels very comfortable and quite easy to use and navigate. Not unlike a classic Gnome feel (which I love).

All-in-all, Xubuntu 12.10 is excellent thus far. I think I'll continue with it and see if it has that "staying power."

I'd had a quick look before 2011 - same with Kubuntu, moved to Xubuntu 12.04 and have stayed.

---

