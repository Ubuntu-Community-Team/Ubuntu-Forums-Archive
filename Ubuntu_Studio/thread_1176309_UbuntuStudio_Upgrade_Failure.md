---
title: "UbuntuStudio Upgrade Failure"
date: 2009-06-02
forum: Ubuntu Studio
---

### Post by dawiba on 2009-06-02
Well I had 'upgraded' to UbuntuStudio and gave it a spin over the weekend.

Total disaster.

The programs I mainly use are Ardour and Rosegarden (Jack is a given). I was able to load up a piece that I was doing in Ardour before the change and that seemed to run fine. The computer seemed okay at first but then started becoming sluggish until I had a freeze. After a re-boot, things still worked but somehow seemed a little unstable, windows taking longer to open, controls sluggish and so on.

Anyway, I carried on and opened up Rosegarden. Before upgrading, I used Rosegarden for midi and Ardour for audio. The first thing that happened was that I got a message telling me the system timer resolution was too low. A bit surprised, I rebooted and chose the rt kernel manually instead of allowing ubuntu to possibly default to the regular kernel. I restarted the applications and got the same error message when starting Rosegarden. If I tried opening things in a different order or even just Rosegarden on it's own, I still got the timer resolution message.

For the record, I had changed none of the settings I had been using successfully under regular Ubuntu (booting into the rt kernel). The only difference from opening Rosegarden one day and the next, was that I had 'upgraded' to UbuntuStudio. So, I tried different Jack settings, I checked everything in Rosegarden. I tried different interfaces. All to no avail. I couldn't use Rosegarden with the real time kernel that came with UbuntuStudio. It wouldn't lock. It wouldn't sync with Ardour or Jack. Everything was wonky.

While I tried all these different things, the computer must have hung at least half a dozen times. After wasting most of a day coming back and forward and trying different things, I gave up. I reinstalled regular Ubuntu and the other stuff I had before and have got back to a working system.

I'm disappointed that it didn't work. I don't know why it didn't work. I do know that I wanted it to work. I also know that I'll not touch UbuntuStudio again. The applications are available separately to install in regular Ubuntu anyway and at least that way, you know roughly what's in your computer and you have half a chance to sort things if you have a problem. As it is, for me, there's just too much stuff piled into it that doesn't seem to work too well together. When I tried to remove stuff (in the hope of removing a conflict somewhere), I kept getting a message telling me that I couldn't remove it because other programs depended on it. The rt kernel not working is a show stopper for me.

My suggestion for those thinking of ugrading is, ask yourself just what it is you're trying to do and go get the programs that will allow this from the repos and hopefully things will be okay for you. Making music is just a hobby for me, so I don't mind (and actually enjoy) a bit of tweaking to get things to work (no deadlines!), but this went too far. I just want to make and record some music, not be constantly trying to work out what went wrong. 

Perhaps UbuntuStudio should ship with less software and instead ship with a core bundle that works, including the rt kernel, set up so that users can 'plug and play'. It's easy enough to add stuff for those that want it. For those that don't want it, it's just junk that gets in the way.

---

