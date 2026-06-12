---
title: "The Ultimate Ubuntu for Students"
date: 2009-09-08
forum: The Cafe
---

### Post by Rich_B_uk on 2009-09-08
Hi everyone,

Myself and a friend (who are both proficient with Ubuntu) are looking at quickly knocking together a personalised Linux distro to present to some faculty members at a local University.

The faculty that we are presenting to is a technology focused one. Although we are aware that there are LOADS of distros out there aimed at multimedia (Ubuntu Studio) and science (Poseidon) we're going to start out with the default 9.04 (to get live-cd functionality), and throw on a ton of applications we think are useful to undergraduate students.

Apart from the immediately obvious (apps already included in these distros), would anyone like to offer apps that they have found useful, and that they think University students would get some mileage out of?

Disk space is not an issue to a degree (8GB USB), and the subjects are as follows:

Multimedia (Animation, video etc)
Audio Engineering
Computer Science
Computer Communications
Business Studies (Information systems etc)
Web Development
Software Engineering (C + Java mainly, we're not experts on this)
Graphic Design (GIMP or bust?)
Games Design
Computer Forensics (Although I suppose it makes more sense to show them Backtrack or Nbuntu)

Essentially I want a big list I can apt-get over the course of a night (please include package names and/or repos if poss). We are using Reconstructor to compile this because we've had positive experiences with it in the past.

What we want is a disk that staff can use and perhaps start thinking about using or at least discussing with students. I.e. I'm going to collar the video editing staff and show them 'Elephants Dream', made on Blender.

---

### Post by NoaHall on 2009-09-08
Multimedia - VLC Media Player, audiocity
Web Development - Gedit. Or maybe Geany, gPHPedit, Mono.
Graphics design - gimp 
Game design/3D design - Blender
Computer Communications? As is remote desktop connection or Instant messeging?

OpenOffice Math (and all the rest)

---

### Post by Rich_B_uk on 2009-09-08
> **NoaHall said:**
> Multimedia - VLC Media Player, audiocity
Web Development - Gedit. Or maybe Geany, gPHPedit, Mono.
Graphics design - gimp 
Game design/3D design - Blender
Computer Communications? As is remote desktop connection or Instant messeging?

OpenOffice Math (and all the rest)

Thanks for the input Noa. We're using the Ubuntu Studio packages which will pull in most of that, but Geany & gPHPedit are good shouts we would not have thought of (with not being web devs and all).

Computer Communications - as in networking. I know tools are think on the ground here, and we'll be sure to bundle the basics like Putty if I can locate a port (to ease student transition to Windows) and OpenSSH. Just wondering if there's anything interesting out there that we are missing. Bring on the suggestions! :popcorn:

---

### Post by NoaHall on 2009-09-08
Wireshark - it's good for testing networks - and maybe you should install one computer with Ubuntu Server.
Other IDE's - Anjuta IDE
NetBeans
Eclipse.

Oh yes, and this! [http://italc.sourceforge.net/](http://italc.sourceforge.net/)
I told my teacher to install it in school - it helped a lot.

---

### Post by Whiffle on 2009-09-08
How long is this presentation going to be?  Somehow I don't think you're going to have time to show them 8GB worth of apps in a presentation without having to force their eyelids open or talk too fast.

I think I would make a list of apps and their uses, and if they have questions along the lines of "Well, can you do X on ubuntu?," then I'd get out the list and if they seem unconvinced or highly interested, demonstrate that particular app.

I would also focus more on the cost aspect (people in such positions always listen to the budget), by preparing a honest comparison between Ubuntu and whatever their current solution is (extra points...get a list of what the school actually pays for their current system).  Don't forget to let them know that support is available through canonical as well, so that they know its not going to be a support nightmare.  

I could think of a bazillion more things to go after, but if its a presentation as I'm imagining it, you would do good to focus on certain aspects of ubuntu, instead of trying to demonstrate a ton of apps.  Time is always short.

---

### Post by Rich_B_uk on 2009-09-08
> **Whiffle said:**
> How long is this presentation going to be?  Somehow I don't think you're going to have time to show them 8GB worth of apps in a presentation without having to force their eyelids open or talk too fast.

I think I would make a list of apps and their uses, and if they have questions along the lines of "Well, can you do X on ubuntu?," then I'd get out the list and if they seem unconvinced or highly interested, demonstrate that particular app.

I would also focus more on the cost aspect (people in such positions always listen to the budget), by preparing a honest comparison between Ubuntu and whatever their current solution is (extra points...get a list of what the school actually pays for their current system).  Don't forget to let them know that support is available through canonical as well, so that they know its not going to be a support nightmare.  

I could think of a bazillion more things to go after, but if its a presentation as I'm imagining it, you would do good to focus on certain aspects of ubuntu, instead of trying to demonstrate a ton of apps.  Time is always short.

I think my use of 'presentation' was a little misnomer on my part. It's more of an afternoon where I'll be wandering round and trying to get staff to engage with Frankenstein distro on a 1:1 level. I would also like to burn a few copies to give away, hence the all-encompassing nature of what we're aiming for - rather than having to go back and add x app later. I realise it might be construed as cracking a nut with a sledgehammer but I feel that might be the best way to go about in one go.

Thoughts welcome.

---

### Post by NoaHall on 2009-09-08
In that case - if you really want to get it showing off - it might be best to get a laptop(with favourably nvidia card on) which you can install onto, (or a usb drive) and show them compiz. I'm sure there will be plenty of students happy to take a cd off you then. Having it installed will show the true benefits - the speed and power.

---

### Post by Rich_B_uk on 2009-09-08
Compiz is interesting - I'm sure there will be an audience for that.

I just want to make the guys who teach Logic think about all the alternatives. And the guys that teach Max look at "Elephants Dream". That sort of stuff. You never know, some of the software dev students may start to take the FOSS way to heart and release their code if they hadn't though of doing so in the past.

More thoughts welcome :P

---

### Post by Whiffle on 2009-09-08
> **Rich_B_uk said:**
> I think my use of 'presentation' was a little misnomer on my part. It's more of an afternoon where I'll be wandering round and trying to get staff to engage with Frankenstein distro on a 1:1 level. I would also like to burn a few copies to give away, hence the all-encompassing nature of what we're aiming for - rather than having to go back and add x app later. I realise it might be construed as cracking a nut with a sledgehammer but I feel that might be the best way to go about in one go.

Thoughts welcome.

Ah okay.  You might throw together a categorized list then, and put that on the desktop or something (or make it the wallpaper), because often the names of the programs aren't really related to whatever they do.

Here's apps I'd suggest:
Stellarium - good for astronomy classes
Octave (maybe with one of the GUI's for it), list as a replacement for MATLAB
Kile/Texmaker - LaTeX
SAGE - replacement for mathematica/Maple ( can actually try this one online... [http://www.sagenb.org/](http://www.sagenb.org/) )
gEDA - gschem in particular, electrical engineering tools
Qcad - not really open source, I don't think, but its a good basic CAD program.
OpenProj - Project Management software
FreeMind - Mindmapping software 


thats all i got at the moment.

---

### Post by NoaHall on 2009-09-08
Maybe you should download something like a cube2/cube game which will show people what you can do with open source.

---

### Post by rob-ward on 2009-09-08
Some more apps that you way want to consider are:

gvim
codeblocks
ssh
vnc
samba
eclipse 3.5
synergy/quicksynergy
virtualbox
inkscape
thunderbird
xchat - irc
sunbird and google integration
gears
kino - movie editing
mplayer
vlc
Thoggen
DeVeDe
Wine
Skype
Google earth
Deluge Bittorrent
ubuntu-restricted-extras

There are probably lots of others as well I will have a think

I think that a student version of Ubuntu would be a brilliant idea, If you get a distro up and running let me know cos I would be really interested in helping/using it.

---

### Post by Rich_B_uk on 2009-09-08
> **Whiffle said:**
> Ah okay.  You might throw together a categorized list then, and put that on the desktop or something (or make it the wallpaper), because often the names of the programs aren't really related to whatever they do.

Here's apps I'd suggest:
Stellarium - good for astronomy classes
Octave (maybe with one of the GUI's for it), list as a replacement for MATLAB
Kile/Texmaker - LaTeX
SAGE - replacement for mathematica/Maple ( can actually try this one online... [http://www.sagenb.org/](http://www.sagenb.org/) )
gEDA - gschem in particular, electrical engineering tools
Qcad - not really open source, I don't think, but its a good basic CAD program.
OpenProj - Project Management software
FreeMind - Mindmapping software 


thats all i got at the moment.

Like that idea (categorising apps up). Defo worth doing.

Thanks for the suggestions. Appreciated.

---

### Post by Rich_B_uk on 2009-09-08
Rob - I'm also in Yorkshire as well! PM me in a few days and I will let you know the end result. I won't quote you but thanks for the apps.

Cheers also Noah - worth it for the games guys I reckon.

Uh oh, about to shutdown!

---

### Post by Whiffle on 2009-09-08
Oh yeah, CUPS-PDF.  So useful.  So very very useful (when it works right...)

---

### Post by VipX1 on 2009-09-08
For Web Design Komodo-edit-5 is the Dogs... Also put Firebug on your Firefox browser so you can see what way other people have writen html,css or whatever it may be in a simple and convenient manner. 
Security: everybody should have EtherApe (network monitor), ClamAV (antivirus) and QuickJava add-on for Firefox. Disable Java in unchartered water!!

---

### Post by Rich_B_uk on 2009-09-08
Back on the AC!

VipX1 & Whiffle, good suggestions. These are just what I need. Little things that I might have overlooked.

For those interested in respinning Ubuntu, the latest version of Reconstructor (2.9) uses xserver-xephyr to give a kind of GUI chroot, allowing you to make allsorts of cool changes without having to resort to Bash kung-fu. Firefox extensions are probably a good example of this.

I wrote about the old version [HERE]("http://up-stream.co.uk/2009/05/adventures-in-benchmarking-part-4-reconstructing-an-environment/")
The official site is [HERE]("http://www.reconstructor.org/")

The limited web design I did on Ubuntu was done in Kompozer so having more suggestions on things we (as more sysadmin style guys) may have only touched on is v.helpful.

---

### Post by kyle2595 on 2009-09-08
You should check out Openshot ([http://www.openshotvideo.com/](http://www.openshotvideo.com/)), it is still in the beta stages but well worth a look.  It is an extremely simple to use and easy video editor For Ubuntu. It Is easy to install too, this page will explain everything that you need to know: [http://www.howtogeek.com/howto/3558/openshot-is-video-editing-software-for-ubuntu/](http://www.howtogeek.com/howto/3558/openshot-is-video-editing-software-for-ubuntu/)

---

### Post by Rich_B_uk on 2009-09-08
> **kyle2595 said:**
> You should check out Openshot ([http://www.openshotvideo.com/](http://www.openshotvideo.com/)), it is still in the beta stages but well worth a look.  It is an extremely simple to use and easy video editor For Ubuntu. It Is easy to install too, this page will explain everything that you need to know: [http://www.howtogeek.com/howto/3558/openshot-is-video-editing-software-for-ubuntu/](http://www.howtogeek.com/howto/3558/openshot-is-video-editing-software-for-ubuntu/)

Thanks Kyle. I'd only used Kino and I don't think (guessing) that OpenShot is bundled with the Ubuntu Studio packages so that's great.

---

### Post by earthpigg on 2009-09-08
consider looking outside *your* department and finding out what software your fellow students are presently paying for, and including the Free Software equivelents on the LiveUSB where possible.

example: what software do medical majors presently purchase?

i would suggest including an outstanding and easy-to-use PDF scanner (Ubuntu will *already* work with most flatbed scanners, you just need to decide which software to include in your remix...) and tools for pdf-to-plaintext conversion and whatnot. 

we all know what broke college students will do once they realize how simple it is to copy/distribute college books, but this can be the official justification:

college books are EXPENSIVE, but you can get some of your money back if you *scan* your new book (fair use includes making personal 'backups'), never use it, and then sell it to a used reseller in perfect condition afterwards. naturally, the law-obiding student will delete all traces of his/her personal digital backup of the book when he resells it to a used reseller...



include custom helpfiles -- maybe even a website that you will have bookmarked by default in firefox -- that explains how certain stuff works, maybe a link to a "how to use GIMP if you are already a photoshop expert" website or two, for example.

when i say custom help resources, i am not saying reinvent the wheel. link to and compile links to existing resources, mostly. make it easy for 'em. i link to existing ubuntu support stuff all over the site for my remix.

heck, maybe just include gimpshop instead of and/or alongside gimp.

if you go the website route -- and i think you should -- consider asking an already existing student-oriented website (with an already existing ***userbase***) to host a subforum for you folks.


if you are having problems creating a custom ubuntu remix, i went through all the trials & tribulations not to long ago. go to the link in my sig and click on 'notes to myself' - there is a chance i have already experienced whatever headache you may be going through and found a solution.



also, the company behind Ubuntu may come down on you for trademark violation. don't include *buntu in the name.

if you are having problems thinking of a name, you do have something you can simply emulate: *BSD is the #1 Free Software distribution of Unix, and one of the greatest & most secure operating systems available for certain tasks. what does BSD stand for? **B**erkley **S**oftware **D**istribution. 

BSD itself is no longer developed by Berkley, but all the still-active and still-great spinoffs kept the BSD name. thats some pretty serious geek pride: "I go to the school that produced what is now one of the finest servers on the planet."

make your project officially endorsed by your school (or a department thereof), and i see no reason why you could not do the same :D

---

### Post by Rich_B_uk on 2009-09-09
earthpigg - That's all really good stuff. I like that this idea (simple as it potentially is) is not being shot down in flames.

We're grads now, but I'm going to try and get this taken up by some undergrads when we're done and hopefully they will implement some of the things you've mentioned that we might not have time for in the next couple of days. I especially like the custom help idea.

Also, I never thought of the whole trademark infringement argument with 'buntu'. I'll rename as appropriate.

---

### Post by jaxxstorm on 2009-09-09
I'd throw Geany in there as a programming environment, as well as glade.

---

### Post by Rich_B_uk on 2009-09-09
Anyone else have any input?

---

### Post by chessnerd on 2009-09-09
I think all of the apps I would have suggested have been, so I'll make a different suggestion:

If this will be used by people who have never used Linux I think you should include documentation with this distro about the software. Something on the desktop that users can open and it will tell them all the software installed and what Windows/Mac software it is similar to in a simple list format like:

> Intenet Software
-Firefox.....Similar to: Internet Explorer/Safari

Office Software:
-OpenOffice.org Word Processor.....Similar to: Microsoft Word

Graphics Software:
-The Gimp.....Similar to: Adobe Photoshop


You could also create hyperlinks on the names of the software that link to the Wikipedia page about the software.

I like the idea of this project. A Linux derivative for universities could do really well in this economy as schools are low on funds and looking for ways to cut costs. I don't think you'll end up getting this put on every computer on campus, but you might end up with a few Linux-based labs if you market it properly.

Best of luck.

---

### Post by rob-ward on 2009-09-09
I think that you should consider installing a couple more dvd/cd writers like xcdroast or k3b for people. Also what about utilities such as ManDVD and oggconvert for encoding and stuff. 

What about installing ubuntu restricted extras by default for out of the box mp3 playback. There are also application like umbrello that you may want to install for diagrams and stuff.

Also what about installing the bluetooth utilatise so there is bluetooth out to of the box as well.

I'm struggling to think of any more apps but I am sure there are many more.

Also I think that the use of ubuntu or buntu in the name is fine as Ubuntu is just a word and many other distros do it.

It may also be an idea to install some gmes to show what ubuntu can do, and what about dosbox, have that install and put some of the old retro and abandonware games on it.

Let me know how you get on as I think that a student distro is a great idea, oh and you need a really good looking wallpaper as well....

---

### Post by Siph0n on 2009-09-09
What about subversion or bazaar for revision control?

---

### Post by rob-ward on 2009-09-09
Also an decent ftp client might be useful;, although I can't think of one of top of my head...

---

### Post by adam.d.clemons on 2009-09-09
the iTalc client is a great tool that the teachers will like for computer lab environments. it lets teachers lock screens, monitor screens, and even put presentation slides, or the teachers screen on the student's computer screens for demonstrations and such. i had a teacher who used the windows version for his lab, but i know it's also on 32bit ubuntu.

---

### Post by Rich_B_uk on 2009-09-10
> **Siph0n said:**
> What about subversion or bazaar for revision control?

Gotta be subversion for universal acceptance? Not all too familiar with these systems.

> **rob-ward said:**
> Also an decent ftp client might be useful;, although I can't think of one of top of my head...

FileZilla is ace. And cross-platform. And also has a server variant. Job done :)

> **adam.d.clemons said:**
> the iTalc client is a great tool that the teachers will like for computer lab environments. it lets teachers lock screens, monitor screens, and even put presentation slides, or the teachers screen on the student's computer screens for demonstrations and such. i had a teacher who used the windows version for his lab, but i know it's also on 32bit ubuntu.

Never thought of that. Appreciate the tip.

Loving the reaction to this. Crowdsourced 'buntu eh?

---

### Post by earthpigg on 2009-09-10
subversion and whatnot is probably beyond the scope of your project, but maybe not.

---

### Post by Rich_B_uk on 2009-09-10
> **earthpigg said:**
> subversion and whatnot is probably beyond the scope of your project, but maybe not.

Perhaps. Especially as this isn't a hosted environment. 

Maybe (depending on footprint) a client would be good to include though.

[http://subversion.tigris.org/links.html#clients](http://subversion.tigris.org/links.html#clients)

Anyone recommend me one?

---

### Post by rob-ward on 2009-09-10
I tend to use the commandline or a svn client integrated into an IDE os I don't have much experience with SVN clients, I have however heard good things about subcommander.

---

### Post by purgatori on 2009-09-10
Packages:

r-base -- statistics
texlive-full -- document creation
vim-full - code/text editing
octave3.0 - numerical computations
apvlv - extremely light pdf viewer with vi-like-keybindings
vifm - file-browser with vi-like-keybindings

---

### Post by Rich_B_uk on 2009-09-10
> **purgatori said:**
> Packages:

r-base -- statistics
texlive-full -- document creation
vim-full - code/text editing
octave3.0 - numerical computations
apvlv - extremely light pdf viewer with vi-like-keybindings
vifm - file-browser with vi-like-keybindings

Like the look of apvlv. Perhaps if I'd been using Linux earlier (maybe with a distro like this) I'd have learn the way of vi!

---

### Post by Warpnow on 2009-09-10
A note taking applicatio, but not like a note app. Something like Notecase, or Zim, definitely best for taking notes in class. One file or project per class. Works really well.

Stubuntu?

---

### Post by Rich_B_uk on 2009-09-10
> **Warpnow said:**
> A note taking applicatio, but not like a note app. Something like Notecase, or Zim, definitely best for taking notes in class. One file or project per class. Works really well.

Stubuntu?

Ha. I can imagine the email from Canonical now.

They actually already do something aimed at students. Technically it's just the ubuntu-edu-tertiary, but it hardly includes anything really. Still, at least it's a shot in the right direction.

Having some troubles with Reconstructor 2.9 at the moment which is a shame.

---

### Post by earthpigg on 2009-09-10
> **Rich_B_uk said:**
> 
Having some troubles with Reconstructor 2.9 at the moment which is a shame.

give remastersys a shot, and see above where i suggested you read the 'notes to myself' at my project's website to see trials and tribulations, and how i came over them.

---

### Post by rob-ward on 2009-09-10
> **Warpnow said:**
> A note taking applicatio, but not like a note app. Something like Notecase, or Zim, definitely best for taking notes in class. One file or project per class. Works really well.

Stubuntu?

Just tried zim now, never used it before, me thinks I have found my new note taking app for lectures, this should definetly be included in the distro. Question have you thought about how you are going to make the distro available to people outside of your university(are you even considering doing so) I think it may be worth hosting on the internet then PM me, I think I know where it could be placed with a large ammount of bandwidth.

---

### Post by Rich_B_uk on 2009-09-10
> **earthpigg said:**
> give remastersys a shot, and see above where i suggested you read the 'notes to myself' at my project's website to see trials and tribulations, and how i came over them.

Yep, defo will do. Just going to sit down now and  take a look at things.

> **rob-ward said:**
> Just tried zim now, never used it before, me thinks I have found my new note taking app for lectures, this should definetly be included in the distro. Question have you thought about how you are going to make the distro available to people outside of your university(are you even considering doing so) I think it may be worth hosting on the internet then PM me, I think I know where it could be placed with a large ammount of bandwidth.

Thanks Rob. Appreciate the offer. I will PM you as and when I get things sorted.

If anyone has more apps to suggest, fire away!

---

### Post by NormanFLinux on 2009-09-10
Isn't there already Edubuntu? Do we need another educational buntu distro?

---

### Post by Rich_B_uk on 2009-09-10
> **NormanFLinux said:**
> Isn't there already Edubuntu? Do we need another educational buntu distro?

Hi Norman,

I've had tons of experience with Edubuntu, and so I wouldn't suggest this 'package' (I shouldn't call it a distro) if I didn't think there was a role for it.

Edubuntu (as it is now) is simply base 9.04 Desktop with educational packages on top. The educational packages are split up into various levels of education.

If we take a look at the 'tertiary' stream, suited to uni students and beyond, we see that it only really installs 10 packages of questionable use to most students. 

[http://packages.ubuntu.com/jaunty/ubuntu-edu-tertiary](http://packages.ubuntu.com/jaunty/ubuntu-edu-tertiary)

What I am trying to do is put together a flavour of Ubuntu that is tailored towards what my faculty teach. I hope to disseminate this to teaching staff and pupils alike to get them to test-drive the software that falls into their particular stream of study - and perhaps even go on to use it more seriously.

I am not making core changes to the kernel.
I am not coding things from scratch.
I am simply putting together apps, utilities & branding I think work together in a cohesive way.

Only time will tell if this is a good idea.

More feedback is welcomed.

---

### Post by NormanFLinux on 2009-09-10
Sounds good. Edubuntu sounds like a set of educational packaging aimed at the primary and secondary educational levels and it may not be good enough for university-level studies. So another set of packages could well be appropriate. It would take time and test to devise a set suitable for higher education. I wish you success in the endeavor.

---

### Post by Rich_B_uk on 2009-09-10
> **NormanFLinux said:**
> Sounds good. Edubuntu sounds like a set of educational packaging aimed at the primary and secondary educational levels and it may not be good enough for university-level studies. So another set of packages could well be appropriate. It would take time and test to devise a set suitable for higher education. I wish you success in the endeavor.

Thanks Norman. Edubuntu packages are great for younger students, but as you say the market here is for those studying at undergraduate level and above.

The barrier to entry in my mind is that they might not have the time or inclination to burn off Ubuntu, install it, research what apps may be of use to them, and install them. All I want to do is cut out that stage of the process.

If you're interested in educational Linux distributions, I have some work here that may be of use - [http://up-stream.co.uk/](http://up-stream.co.uk/)

---

### Post by rob-ward on 2009-09-11
It may be an idea to include the ubuntu-edu-tertiary packages in you distro as there are some intresting mathmatical and physics apps that you don't have at the moment.

---

### Post by Rich_B_uk on 2009-09-11
> **rob-ward said:**
> It may be an idea to include the ubuntu-edu-tertiary packages in you distro as there are some intresting mathmatical and physics apps that you don't have at the moment.

Indeed Rob. That'll be one of the first things I put on. There's relatively little included, but the packages that are part of it are really useful.

I don't see space as a huge problem with this anyway. As long as we avoid bloat (anything that tries to launch as a daemon etc) then I'm happy with an .iso that squeezes onto a DVD. Plus, that leaves a handy 3.3GB (Less wasted FS space) when used with a 8GB flash drive.

---

### Post by rob-ward on 2009-09-11
I think you will be fine space wise, even with all the packages you have mentioned I don't think you will even be at 2 gig if you are even at 1.5gig i'd be suprised.

Which method are you using to create the livecd remastersys or Reconstructor?

---

### Post by Rich_B_uk on 2009-09-11
> **rob-ward said:**
> I think you will be fine space wise, even with all the packages you have mentioned I don't think you will even be at 2 gig if you are even at 1.5gig i'd be suprised.

Which method are you using to create the livecd remastersys or Reconstructor?

I'd always had joy using Reconstructor if I'm honest. Found it really easy to use and I was actually really looking forward to trying ChrootX out.

However, 2.9 is being really buggy - with 8.04 and 9.04. I don't fancy regressing so I'll probably use Remastersys. I've been giving moonpig's docs a read to help me out.

---

### Post by Warpnow on 2009-09-11
> **Rich_B_uk said:**
> Indeed Rob. That'll be one of the first things I put on. There's relatively little included, but the packages that are part of it are really useful.

I don't see space as a huge problem with this anyway. As long as we avoid bloat (anything that tries to launch as a daemon etc) then I'm happy with an .iso that squeezes onto a DVD. Plus, that leaves a handy 3.3GB (Less wasted FS space) when used with a 8GB flash drive.

Install space will be higher than iso space because the packages are not compressed, and a bunch of other reasons too complex for my knowledge.

A 300mb iso still installs onto over a gig, at least when I remastersys.

And a heavy DE will run like **** off of 90% of USB sticks to outrageously slow speed.

---

