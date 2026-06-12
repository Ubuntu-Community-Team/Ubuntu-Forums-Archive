---
title: "Unexplained failures and cosmic rays......."
date: 2020-09-14
forum: The Cafe
---

### Post by vidtek on 2020-09-14
During my long life as an electronics engineer I have always been involved with electronics repair and since the early 1980's with computers.

There have been many instances of failure and unexplained glitches in signal processing I have encountered.

This has been particularly true of programmes run in various computer systems which after thorough investigation proved to have no obvious cause.

I have always put this sort of occurrence down to random chance, but recently having read of the impact of cosmic rays on various materials and the effect they can have on the atomic level, I am wondering if maybe cosmic rays can be the root cause of all these mysterious failures.

Thoughts anyone?  Or should I just get out my tinfoil hat?:confused::confused::confused:

Cheers Tony.[COLOR=#ff0000][/COLOR]

---

### Post by ameinild on 2020-09-14
[Bit rot]("https://en.wikipedia.org/wiki/Data_degradation") is a thing, which is why you want to store important stuff on ZFS or btrfs (but ZFS is more mature). I believe this can also cause unexplainable errors in aging software.
Related phenomenon are [disc rot]("https://en.wikipedia.org/wiki/Disc_rot") and [software rot]("https://en.wikipedia.org/wiki/Software_rot").
Whether or not this is caused by cosmic rays really doesn't matter IMO - the fact is it happens slowly over time, no matter what the medium is - and this will probably always be the case, although future storage mediums could reduce the risk. 
But I don't believe we can ever achieve storage medium that is completely immune to data decay, no matter how advanced.

Oh, and by all means, keep the tinfoil hat, and while doing so, check out [SciManDan]("https://www.youtube.com/channel/UCRtsZ5Iak9wSLsQLQ3XOAeA") on Youtube. :D

---

### Post by PJs Ronin on 2020-09-14
I have "Alien Invasion During September" in the 2020 End of The World Sweepstakes so I'm guessing these signal processing failures are a prelude.

---

### Post by TheFu on 2020-09-14
Cosmic rays are real, for computer systems in space.  There are different rating levels for spacecraft DPS based on the environment they are expected to operate.  Jupiter has extreme radiation, to the point that humans will probably never be able to live there or on the moons.  Multiple spacecraft have been lost near Jupiter.  I had a programming job that used 30 yr old computers on a spacecraft.

The farther a spacecraft gets from the Earth, the less protection there is. The normal solution is shielding, larger components, and more error checking for RAM and data storage.  This is why spacecraft launch using 10-20 yr old components, not the newest, fastest stuff.

On the ground, bit rot is real, but a good backup schedule will ensure that the OS checks access to, and bytes on, storage in a routine, scheduled, way.  This is much more common for Unix systems, than for Windows.  Different user communities attract different sorts of admins. Unix people create backups.  Windows people do not.  This is why I believe that Windows systems experience bit rot much more often - those users don't have weekly or monthly OS backups.  It could also be because Linux people tend to reinstall fresh OS versions every 2-3 yrs, worse case.  Windows users go 10+yrs. That's a long time for bit rot to happen.

For *nix systems inside a data center, the greatest risks for system failures after bad power or water damage would be metal filaments in the air getting sucked into a case and onto electrical components, causing a short.   This is real.  Companies install filters in the DC HVAC ducts to filter metal filaments. Worked at a place that would close 1 room in their DCs every few years and remove everything, pay a hazardous materials company to come and clean all the dust and filaments, while also removing all the cables. Whenever a new system went in, they never reused cables. We'd add 12% of the project estimated cost for new cables.

Inside your house, the cause is most likely to be dust, pet stuff, overheating, or incorrect settings, not anything more exotic.  I have a ryzen 5 system that has been very stable for 2 yrs.  Noticed that some HDDs in a drive cage were a little hotter than I'd like, so I replaced the cage fan with an "better" fan. Tweaking the fan speed has been manual and I'd like a quieter system, but not at the expense of HDDs lifespans being shorter from over heating. Started with 800 rpm, but the temps where hitting 46 deg. Too hot.  Raised it to 950 rpm and temps are 43 deg.  Looks like 1050 rpm should get to the 40 deg spot, my target.  While I was in the BIOS, decided top tweak the CPU and memory performance settings too. After all, the system is stable and doesn't crash or shutdown unless I run a command.  Tweaked a few settings and the BIOS refused to boot at all. Ouch.  Slowed down the RAM a bit more and it booted. Everything seemed fine. It ran all day, then around 8pm, it rebooted for no reason that could be found. I was on connected from a different room, or ssh when it crashed.  It rebooted automatically, immediately and the logs didn't show anything wrong.  I decided to sleep on the issue. 

It hasn't rebooted again. Yesterday,  had it transcode some videos for about an hour.  The CPU got near 98 deg, which I consider a problem, but it kept going. When the task completed, temps dropped back to 46-48 deg.  The CPU is overclocked about 300Mhz now and using the stock cooler. I'll back that off a little today and see how that helps the temperatures. 

There is always a scientific reason for why any system fails. There isn't some old man with a beard causing it, unless he is a tech and some beard hair is causing a shot. Problems can always be explained, we just need to figure out the possible causes and mitigate each.

---

### Post by vidtek on 2020-09-14
ameinild-Thanks for your post, bit rot can only explain so much.....

TheFu- Thanks for your input too and your insights into spacey stuff.  I didn't think any material or shielding could stop cosmic rays-they pass right through the earth so how could anything devised by man stop them?  I suspect the shielding is mainly for gamma and rf  waves.

As a former IT director sysop with 12 servers and 250 desktops, I have seen some weird failures unattributable to any physical cause.   While as a humble tv engineer repairing anything from vcrs and videodisc players to digital tv's, projector systems, video walls and large-scale PA systems I have seen stuff that cannot be explained through normal fault-finding procedures that point to a faulty component or ragged output from psu's.

Pj's Ronin-watch out for those little green men mate...

---

