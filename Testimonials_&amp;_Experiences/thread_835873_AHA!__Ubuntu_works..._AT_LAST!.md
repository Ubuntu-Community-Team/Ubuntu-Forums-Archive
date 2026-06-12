---
title: "AHA!  Ubuntu works... AT LAST!"
date: 2008-06-20
forum: Testimonials &amp; Experiences
---

### Post by jinchoung on 2008-06-20
howdy,

there was another thread in which i was venting my frustrations about the inability to get a good ubuntu installation up and running where i was instructed this is the appropriate forum for such threads.

happily, this time i am back to report success!  an ubuntu installation that looks and feels great and makes vista look like a monkey turd.
-------------------------------------------------------------------
preamble: these are my own experiences and may not reflect reality in any way.  and my account is told in the form of recommendations and feature requests.

**1. 'irqpoll' needs to be autodetected.**  i've tried a handful of distros and only mandriva one successfully booted... let alone install off the bat.

you can say a lot of bad (and true) things about windows but i've never ever personally seen it unable to even get to actual installation.  but no 'irqpoll' when you need it scuttles you before you even start.

(one SUPER NICE THING that i discovered is that if you 'irqpoll' into livecd and then install from there, when you use the advanced button to install your boot loader, the boot loader entry in menu.lst already has 'irqpoll'.  very very nice.)

**2. installing can render your windows system inoperable.**  in my case at least, on a system with drives that require IRQPOLL, overwriting the bootsector with grub makes you UNABLE to boot windows at all.

if you try to boot windows from a grub, you get "ntloader" not found.  very common.  try googling it.

i wouldn't venture to estimate a percentage but i would imagine a great number of people trying linux are gonna be dual booting.  there should be some ACKNOWLEDGMENT of this during the install process and proper caveats and warnings should be given when necessary.

for instance, fixing win to boot (but then disabling the ability to boot linux) requires nothing more than a FIXMBR command.  but it took me over an hour's search to find that info and exactly how to do it.  and in the process running into a lot of nonsense advice and needlessly dire warnings about possible hardware breakdown, incompatibility, etc.

ULTIMATELY, my solution for having a dualboot necessitated GRUB4DOS.  it leaves the bootsector completely untouched and works in concert with the windows bootloader instead of necessitating a power struggle for the bootsector.

i installed ubuntu, i installed the bootloader into a 50mb partition (and NOT the window's primary drive) and then i just copy over the generated menu.lst from the ubuntu menu.lst to the grub4dos one on my c: drive.

THIS WAS A NIGHTMARE.  and some way should be found to somehow mitigate it for newbs.

**3. during installation, there should be an OPTIONAL GUIDE about how hard drives are being named.**  as a windows user, i had no FING IDEA WHATSOEVER what hda0, hdb1, sda0, etc. meant!  not AT ALL.  not only that, but i couldn't easily reconcile which drive that I KNEW as C: D: E: etc corresponded to what linux was seeing.  especially since i'm mixing and matching PATA and SATA drives.  and unless you call that a rare thing, some attention needs to be given to this circumstance.  some kind of miniprogram or tutorial should pop up to go over with the user what the naming schemes are.

sure, they could look this up on their own.  but it is an organic and UNAVOIDABLE ASPECT OF THE INSTALLATION PROCESS.  therefore it falls within the purview of installation documentation and there's no reason not to have it be an optional dialogue during install.

**4. it should be stated UPFRONT that a fully functional and nicely configured ubuntu installation REQUIRES AN INTERNET CONNECTION. ** don't hem and haw on this.  don't cover it up.  just state this really balls to the walls upfront.  this is much much much more the case with linux than with windows.  sure, it is much more the case with windows now and getting ever moreso but coming from win land for the past decade, i didn't imagine that so much would need to be done through a net connection to get a nice installation with all the whiz bang eye candy stuff going.
[B]
5. WIFI should be tried and if it doesn't work, it should be abandoned for a WIRED CONNECTION.[/B]  if it works, great.  but if it doesn't there's no guarantee that it ever will.  the state of the drivers are not such that all the various devices out there can be reasonably expected to work.  **you should put this up as a caveat way up front and SERIOUSLY RECOMMEND A WIRED CONNECTION for people having problems.**

this was recommended to me as an option by someone (forgot his name but i thanked him) in my rant thread and i'm very grateful.  i didn't know that my att broadband router had the option of a wired connection but frankly, IT DIDN'T EVEN OCCUR TO ME TO LOOK!

FYI a 50ft network cable is $6... a very good and cheap way to go.
-----------------------------------------------------------------

this brings to end for me a month long, herculean effort to get this ubuntu thing to go.  but it went.

alas, i have to shake my head that successfully installing linux onto my system gives me a sense of accomplishment!  i really wish it didn't.

hopefully this will inform or help someone.

my advice: get a notebook.  pray you won't need it.  but if things don't go right, you're gonna have a lot of notes to take, keep track of, scratch out and reconcile.

jin

---

### Post by lisati on 2008-06-20
It's good to here of a success story, and how you tackled some of the difficulties you encountered on the way. Keep up the good work, and don't give up on finding solutions to the annoyances!

---

