---
title: "Great OS, great community, lacking stability"
date: 2010-08-18
forum: Testimonials &amp; Experiences
---

### Post by GenBattle on 2010-08-18
I still love Ubuntu, but i think that for now it has no place on my computer.

I've used Ubuntu since playing around with Warty on an old G3 mac when i was a kid, and i've been testing and trying Ubuntu installations on a variety of desktop and laptop computers ever since. For the last 18 months or so i've actually adopted Ubuntu permanently in a dual-boot configuration (but i only use windows when i absolutely must).

This has all been fine and well until the Lucid release and my most recent hardware upgrade.

My first real installation barrier occurred when 10.04 was released. Having built up a habit of formatting every 6-12 months to simply clean out all the stuff i'm not using, i backed up my essential files and decided to do a fresh install from the Live CD. Unfortunately, every time i attempted to boot my computer from the image the screen would simply turn off and on in a periodic pattern, with no apparent activity or response from the computer. I searched high and low for a solution, and eventually just got lumped in with another set of people reporting the same problem. There still hasn't been a fix to the livecd image available for download which will allow me to use it to install Ubuntu. In the end i found a workaround in the form of upgrading from 9.10 to 10.04 via ubuntu's update system. Not idealy, but i could live with the subsequent ATi driver installation issues and extra chaff floating around my ubuntu partition.

Not more than a few days later i found my next major barrier to Ubuntu adoption. I found that under certain conditions my network card would brick itself (yes, brick itself) and become unresponsive in both Ubuntu and Windows because of a mix of crappy hardware and terrible Ubuntu drivers. The card would show up in both windows and Ubuntu, but would not respond in any way, shape or form. I was astonished; i never thought i would come across an instance of a GNU/Linux OS actually bricking a piece of hardware. Fortunately after much digging i found out this could be fixed with a hard reset of the system (powered off and unplugged). This problem still occurs, and regularly forces me to hard reset my system. Again, all i can do is wait patiently in a ticket with a bunch of other affected people.

Most recently, i got home after a terrible day to sit down and blob in front of Ubuntu, only to be confronted with: 
[https://bugs.launchpad.net/upstart/+bug/522197](https://bugs.launchpad.net/upstart/+bug/522197)

So now i am returned to square 1; i need to back up my files, reinstall 9.10, upgrade to 10.04 (or try my luck with the alternate installer), copy my files back over and reinstall my applications. 

I know we all have to deal with issues and bugs in our pursuit of  Ubuntu, but some days it feels like Ubuntu hates me, like it doesn't want me to install it on my machine. 

The battle rages on.:popcorn:


Ubuntu is a great operating system. I've had experience working with other distros like Fedora, and the amount of work required to get them set up and working is several times that of Ubuntu. The problem is that Ubuntu seems to have traded its functional stability and consistency to achieve it's surface shininess and boundless range of user helper apps. This is compounded somewhat by the community approach that Ubuntu favours. The bug tracker is overflowing with bugs. There aren't enough people in the bug squad to triage and monitor bugs. Further downstream there simply aren't enough skilled developers to take responsibility of the bugs and fix them. Just take a look around launchpad, there are plenty of bugs which have been floating around for months. In many cases these are simply carried over from one release to another, and still they go unfixed. 

This would be fine for minor bugs with purely aesthetic manifestations, but for the sort of show-stopping bugs i've experienced in my short stint using 10.04, it should be unacceptable. What will people think of Ubuntu if they have to return their computer to the manufacturer because their network card suddenly stops responding, even when they format their computer and reinstall windows? (i almost got to this point) How are users going to trial the Ubuntu experience when their computer can't even boot off of the Ubuntu Live CD? How will non technical users resolve issues that cause their Ubuntu machine to suddenly not boot after they restart it? These issues are acceptable for some sort of niche hardcore operating system; but for an operating system like Ubuntu that wants to be the definition of mainstream GNU/Linux, these show stoppers are exactly that: show stoppers. I am a software developer/engineer; i have learned to accept and deal with these sort of computer issues. My fear for Ubuntu is that any less savvy computer user would probably have given up much sooner, with a solution out of reach.

This is not supposed to be a /ragequit post, or some sort of anti-ubuntu tirade. Sure, i admit i obviously go the wrong hardware for running ubuntu. And i admit that it is the proprietary manufacturers who are responsibe for flaky hardware, flaky drivers, and poor linux support. I am simply trying to communicate my experience with Ubuntu over the last few months in the hope that the community and Canonical can attempt to address some of these issues. Even if these issues aren't addressed, it feels right to put them out there; even if it is only my opinion.

If nothing else, Ubuntu has certainly made me believe in the spirit of "Ubuntu" and Free (as in speech) Software. For this i will always be grateful.

---

### Post by lancest on 2010-08-18
Doing a hard reset after every session is simply not tolerable in my book! 

Replace hardware like I allways do - or stick with Windows until driver issue gets solved. 

Good luck.

---

### Post by anubhavrocks on 2010-08-18
For the time being you can use Ubuntu in a Virtual Machine.I know it has its own issues, but at least it will much better than installing/reinstalling in your not so well supported hardware.

---

### Post by Jazzy_Jeff on 2010-08-18
Next time you want to do a clean install download the Alternate Install CD. It is text based but easy to follow. I have problems with the Live CD as well but since I know I want Ubuntu the Alternate Install is great.

---

### Post by intrader on 2010-08-18
I have reported UI problems with 9.10 and 10.04. These have not been resolved or addressed by developers.

It is really horrible - as I am trying to post this reply, the scrollbar is stuck as on and the mouse moves the window even when mous is up.

The problems are leading me to ditch Ubuntu 10.04. Unfortunately I can't go back to 9.04, as when I did that the problems of 10.04 reappeared in 9.04. I had a very stable 9.04, but had to reinstall on account of problems with sound in Skype.

My solution is to go back to Suse which I used successfully for quite a while until I ditched it to try ubuntu. For a while (with 8.10, and 9.04) things went well. However some update to 9.04 now brings the problems with 10.04.

For example, I have the following list in tomboy, to try to copy and paste, the scrollbar is still stuck and copying took many tries.
So here are my 10.04 problems:
Slow responding to button or link click - as for example Close, or Apply, or submit.
• Slow response of window when switching to another window
• Click on scrollbar bottom arrow button remains activated and continues to move even when mouse is lifted. It does cancel with a click (does cancel with ESC). Scrollbar remains active once the scrollbar button is clicked - moving the mouse on window scrolls once it starts; stops only when clicking (repeatedly) on scrollbar button or via the ESC key.
• After left mouse click on an icon or link, the mouse often changes to a hand icon and the icon moves along with the mouse (trailing a small thumbprint image)
• Hangs up on occasion on while moving mouse to some action - requires restart.tarts highlighting without the need to move mouse.
• Highlighting of text is difficult to cancel; it extremely difficult to reliably start the highlight action

JUST HORRIBLE:(:(:(](*,)

---

### Post by Swagman on 2010-08-19
Y'know, a lot of these issues could be down to BIOS settings. Just because an earlier install worked ok with current BIOS settings doesn't mean a newr install will.

My own personal experience with this is after I built a new machine (This one, a quad core 965 black edition AMD) I decided to opt for the 64 bit install.

Glitch after glitch ensued. I should point out that I've built quite advanced Non Linear Edit video machines in the past and was somewhat perplexed by all the freezes, crashes etc.
So I nuked the 64 bit install and installed the 32 bit version. Only for the same thing to keep on happening ?

After reading up on the components I had purchased I narrowed it down to incompatible RAM. In all the time I have built my own machines I have never fell foul to this, so I removed one stick of RAM (2gb). This seemed to cure it but ..No, it kept on happening.

It felt like I was beating my head against a brick wall and the wife was giving me *GBH of the ear-hole as well !!
So I stuck the other stick of RAM back in and started messing about in the BIOS. enabling stuff that wasn't in previous BIOS's, plus weird choices.

Something worked. This machine has been rock stable ever since, I wish I'd kept the 64 bit install now as it certainly was snappier.

I suspect the cure was selecting "Ganged Mode" for the RAM, I aint gonna select Unganged just to check that theory though !!


* GBH is a legal term meaning Grievous Bodily Harm

---

### Post by mastablasta on 2010-08-19
most users are shocked when you show them BIOS on their computer.

---

### Post by intrader on 2010-08-19
I appreciate your posts regarding this issue. It is possible that the some new Xorg software released during the 9.10 release has by also corrupted my old version of 9.04 as well as the new 10.04.

BIOS is a possibility; but where do I start tweaking? 

I am currently downloading Suse 11.3 as this machine used to run Suse quite happily before I installed ubuntu 8.10 (good but no Skype),. 9.04 (no microfone for Skype), 9.10 (Microphone ok, but no playback on Skype),back to 9.04 (update to Xorg introduced the bad artifacts,  and finally to 10.04 (Skype runns fine now, but I have all the bad UI artifacts).

This is an old machine:

Dell Inspiron 8200 with 1GB memory, 100GB 10000rpm disk, running NVIDIA driven display (I have tried with/without update of version 96 of driver).

I am also now running xubuntu - the system is a little more responsive, but it has the same problems.

In annoying order, the scrollbar problem, followed by the highlight problem and next the click action (takes many clicks to turn on the light of the mouse preferences applet).

HORRIBLE

I hope you can help recover this machine to run ubuntu.

---

