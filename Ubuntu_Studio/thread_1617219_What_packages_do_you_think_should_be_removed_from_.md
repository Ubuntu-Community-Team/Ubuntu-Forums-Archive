---
title: "What packages do you think should be removed from or added to Ubuntu Studio?"
date: 2010-11-09
forum: Ubuntu Studio
---

### Post by Stochastic on 2010-11-09
Some of the Ubuntu Studio developers have collectively decided to streamline and reorganize the meta packages of Ubuntu Studio for the Natty release (April 2010).  They're asking for the community to add work-flows for any tasks that Ubuntu Studio should be designed to handle, to the following Wiki page: [https://wiki.ubuntu.com/UbuntuStudio/Workflows](https://wiki.ubuntu.com/UbuntuStudio/Workflows)

Please don't destroy other workflows, just add to the page.  Also it would be VERY, VERY, VERY helpful to everyone if the same formatting was used for all workflows.

So I encourage a brainstorm of activity on that page, as a lack thereof may result in a very stripped down version of Ubuntu Studio in future releases.  (just one idea right now, there is yet to be a single workflow to mention how to create a bass line)

---

### Post by Bi11yy on 2010-11-09
Yeah I'll start. It would be good if UbStu would start out by saying its workflow is completely different from DAWS as we might know them in other OS'. Whereas most DAWs are self contained, UbStu as the OS _IS_ the DAW, and the seperate pieces are part of that DAW. Ardour isn't the DAW, its part of the DAW in reality. Pretty big concept off the bat. I spent days looking for ways to place a virtual instrument in Ardour, until I found out I could just record the output of Alsa or ZynAddSubEfx through JACK into Ardour, like Rewiring. Idea such as this and the Workflow Wiki should be presented to the user on the first run of the OS install, in a big html page or something. It would help, as the info out there for all the different distros and versions are literally beyond confusing. Have the latest info with the latest distro as it applies. 

To add, the specialty programs like those that apply to Envy24, Echo mixer and HDSP should go. I mean if you've got that hardware thats great, provide a link to dl that stuff. Muse, Linux Music maker, Freebirth, while nice programs, they really show their age.
 UbStu should be more cutting edge, at the same time, be lean and mean, not bloated and stuffed with the Linux Music and Video showcase. It just comes across as Cadillac Deville instead of Cadillac CTS-V, feel me?
 I would, however, include WINE and some of the music software that works with WINE, even if in demo form. Demo Reason would be big on my list as well as demo Ableton, those seem to work with UbStu if packaged right. If there is something to show off, let it be those.

---

### Post by AutoStatic on 2010-11-09
> **Bi11yy said:**
> Demo Reason would be big on my list as well as demo Ableton, those seem to work with UbStu if packaged right. If there is something to show off, let it be those.That's impossible. The licenses of the demo versions of both Reason and Ableton prohibit redistributing. Besides, the Ubuntu ISO's only contain FLOSS software.

---

### Post by Bi11yy on 2010-11-09
> **AutoStatic said:**
> That's impossible. The licenses of the demo versions of both Reason and Ableton prohibit redistributing. Besides, the Ubuntu ISO's only contain FLOSS software. I might be getting the licensing info wrong, but Ableton offers demos with everything from sample cd's to midi controllers. Why would UbStu be different? However you're right about FLOSS, my bad. Coming from a Windows background, which has a more robust music software history, I would do anything to see Linux be more competitive. I like UbStu, I've gotten it to look nice and I'm glad for the ability to tweak until my hearts content. But frankly, using it in a project studio environment is lackluster at best. Software like Ableton and Reason have no match in the Linux arena, and I fear thats what really holds a lot of people back.

---

### Post by cchhrriiss121212 on 2010-11-09
> Software like Ableton and Reason have no match in the Linux arena, and I fear thats what really holds a lot of people back.I can understand wanting to use Reason, but what do you think Ableton can do that is not possible with qTractor or Ardour? But if you want to see a linux version of these then contact the manufacturer, this is the only way it is going to change. I would not like to see WINE included with the Studio distro as I think it will imply this to new users: 
1. Ubuntu can run all your windows audio apps (which it can't)
2. Don't bother with the native audio apps (which defeats the purpose of a FOSS music distro)

To address post #2, I'd also like to know where these workflow ideas will end up. Is there any way that these could be included in the Studio install image along with other helpful documents? This is a good area for improvement.

When a new user installs the OS he is greeted with an empty desktop and a big pile of audio software (I say audio only as it is more complex than video+graphical) he does not know how to use. Why not include a welcome screen with repackaged community docs and maybe some videos? 
Here is what I would like to see:

[LIST]
[*]Explain how the modular setup works
[*]What is jack and how to set it up, firewire subsection
[*]How to connect everything
[*]Examples from the workflows
[/LIST]

---

### Post by Bi11yy on 2010-11-09
> **cchhrriiss121212 said:**
> I can understand wanting to use Reason, but what do you think Ableton can do that is not possible with qTractor or Ardour? But if you want to see a linux version of these then contact the manufacturer, this is the only way it is going to change. I would not like to see WINE included with the Studio distro as I think it will imply this to new users: 
1. Ubuntu can run all your windows audio apps (which it can't)
2. Don't bother with the native audio apps (which defeats the purpose of a FOSS music distro)


 No offense but really what Ableton can do in an all-contained system is amazing. The ability to record, edit the recorded audio and then drag and drop back into a sampler, and the ability to create Racks and thereby custom instruments (think Combinator for Reason) and then those instruments become presets. You just can't do that in Ardour by itself. And using plugins through JACK ain't the nearly the same. I've used DAW after DAW and by far Ableton kicks ***, it brings about a whole new way of doing things extremely fast and intuitive. No other DAW can compare. Reason would come close based on its flexibility, but to get the same functionality Ableton has, you'd have to add Record. Cubase cant do this, Logic cant do this, Cakewalk, nope. Its as close to a modular sequencing recording editing environment there is, as it is. Unfortunately its not the most stable software in the game. Its frustrates me in that way, one of the reasons I decided to check out UbStu.

 But I can see why not use WINE, my point was to show how flexible UbStu can be for those that constantly nay-say it as not a good environment for multimedia creation. Its like a Corvette but it only comes in pink. Baddass but nobody wants to drive it, lol. Put it in a different colors and see what happens.

---

### Post by Stochastic on 2010-11-12
Three days after making this post, I've yet to see any new edits on the mentioned wiki page.  I do hope that there is some community involvement in this page VERY SOON - this wiki page will not only shape the future of Ubuntu Studio, but will likely be a major piece of documentation for new users.

The idea of including more documentation in the ISO for new users is a good one, I'll pass it along to the other developers.

Please go edit: [https://wiki.ubuntu.com/UbuntuStudio/Workflows](https://wiki.ubuntu.com/UbuntuStudio/Workflows)

please.

---

### Post by cchhrriiss121212 on 2010-11-12
Just added a few bits in, also moved the "live music" section up to the rest of the audio rather than having it under "miscellaneous" at the bottom. Hope that is OK.

Edit: I added alsaplayer to my workflow as I think there should be at least one jack aware audio player included on the ISO. Audacious does not do this AFAIK.

---

### Post by cchhrriiss121212 on 2010-11-19
Also: network manager. It has been left out for some time now and is a major source of confusion for new users, please make this absense clear to users either before, during or post install.

Personally I have my doubts whether installing/using it makes any difference. I have been using it on my own machine for a year with no obvious issues. I run jack with 2.6ms latency and rarely see any xruns or anything.

---

