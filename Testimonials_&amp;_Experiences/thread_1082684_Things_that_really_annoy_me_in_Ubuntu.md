---
title: "Things that really annoy me in Ubuntu"
date: 2009-02-28
forum: Testimonials &amp; Experiences
---

### Post by DjNDB on 2009-02-28
There are some aspects in ubuntu that **really** tempt me to not use it anymore. Some of them annoy me every day, others are just bad design decisions.

I just make this list to let others know, and to archive what I would fix if I had the time. It sure is not complete, but those are the things I immediately thought about when I tried to summarize them. 



- nautilus has no drag and drop in the tree view. Also it does not give the same context menu options there as in list view. Also it is not possible to rename there.
I tried a lot of other file management programs of cause they had other aspects i did not like since they are not well integrated in gnome. But maybe i might get used to those or find solutions to mitigate them if i use them for a while.

- pulseaudio sometimes does not work after suspend, although it comes with /usr/lib/pm-utils/sleep.d/01PulseAudio which seems to be supposed to handle that. I tried adding my own version 

in /etc/pm/sleep.d which does not work:

[QUOTE=/etc/pm/sleep.d]
#!/bin/bash
if [[ $1 == resume || $1 == thaw ]]
then
 su username -c "pulseaudio -k"
 su username -c "pulseaudio -D"
fi
[/QUOTE]

If i do the same manually when it's broken it works again

- In several applications context menus can only be used on empty spaces. e.g. Nautilus. If you have a folder with content and white space you can right click to create new files/folders and so on. However there is no way to do that if the folder is so full, that there is no whitespace.

- There is no gapless playback of mp3s in rhythmbox and other apllications. Only some kind messy of workaround by crossfading.


- pulseaudio has no AC3 passthrough. There is a solution by reencoding which works, but sounds quite bad. If i suspend pulseaudio and use the device exculsively there is a 2 second period until the device started and therefore the beginning of the audio is missing.

- I bought a new Mainboard for Ubuntu on which suspend to ram basically works. However often one of the Hard disks fails and I have to run a script I came up with in order to reset them. I should think of automating it. 

- Sometimes the systray icons float around as windows on the desktop

- pidgin has no xml history, but only crappy csv files. That makes it harder to export into other formats because no XSLT could be used.

---

### Post by chriskin on 2009-02-28
i failed to understand why those are important problems, i can think of more important problems in other distros or operating systems in general.
which distro are you tempted to use then?

---

### Post by NoReflex on 2009-02-28
Regarding your pulseaudio issues - you could try to remove pulseaudio and use alsa. I'm using alsa right now because PulseAudio + FlashPlayer = Firefox crash on my notebook (Ubuntu Jaunty - Dell Inspiron 1520). 
You could try to convert pidgin's csv files to xml with csv2xml : [http://csv2xml.sourceforge.net/](http://csv2xml.sourceforge.net/) and then modify it to your needs - maybe using sed.
When you can' use context menus in Nautilus you can use the menus (File, Edit, Go etc.).

Best wishes,
NoReflex

---

### Post by trendyabinash on 2009-02-28
Hey man see it is our own choices.
Nothing in the world is perfect, but I know these ubuntu guys try their level best to make UBUNTU PERFECT. And I love their efforts and support.

If you do have bugs then file it in launchpad it would be more useful to all of us

---

### Post by DjNDB on 2009-02-28
> **trendyabinash said:**
> Hey man see it is our own choices.
Nothing in the world is perfect, but I know these ubuntu guys try their level best to make UBUNTU PERFECT. 

Sure it is my own choice and I did not intend to say that the developers were bad. Although there do exist a lot of those...
I would love to do open source development too, but at the moment I am very busy with my Master of computer science study. After that I might have some time on the weekends to do my own projects, but I wish I could develop open source full time and somehow get paid so I can live. I will have to figure out what options exist for that in about 2 years.

> **trendyabinash said:**
> If you do have bugs then file it in launchpad it would be more useful to all of us

The Nautilus tree view issue has been reported 6 years ago.
As some of the other issues they would just be feature requests with a low priority.

[http://bugzilla.gnome.org/show_bug.cgi?id=110127]("http://bugzilla.gnome.org/show_bug.cgi?id=110127")

> **chriskin said:**
> i failed to understand why those are important problems

Depends on the issue. Those are the Major issues:

- File handling is something i do every day and it should be as intuitive as possible. i am currently trying dolphin, which i probably have to get used to yet.

- Audio is essential if you use a system for multimedia.

I can't use audacity at the moment without turning off pulseaudio.

Having no audio at all is aa mayor issue in that case

I had to create workarounds in order to be able to use ACE passthroug for movies.

- Suspend is one of the most important features for me. Normally I suspend my PC if I don't need it and wake it up within seconds. The alternative is rebooting for almost a minute and having to enter my passphrase at least 4 times to get to the same state. (2 times encryption of / and swap, Login, Unlock Thunderbird password manager)

- I forgot to mention that videos seem to lose frames every now and then, which I find disturbing since i am very sensitive to any abnormal Behavior of video and audio. I have seen this in mplayer and vlc so far

> **chriskin said:**
> which distro are you tempted to use then?

I was using windows before and had no problems, I have had the intention to use linux for 8 years now. I tried it several times, but there was always something that kept me back. Most recently the main issuewas that i could not watch HD Videos since there was no multithreading in ffmpeg yet. On windows however there was coreavc for which my old processor was powerfull enough.

One of the Major advantages of debian based distros compared to windows is however the package management. It is really easy to install all kinds of software and that is just perfect for computer scientist. If i had the time I would fix the issues myself, But that would require a lot of digging in foreign and often badly documented code. Sometimes even in unknown languages such as ASL as i tried to fix the DSDT implementation of the BIOS of my old mainboard for some days before i bought the new one. It just was not worth the effort and showed no sign of success. 

> **NoReflex said:**
> http://csv2xml.sourceforge.net/[/url]NoReflex

I just took a look at it again and it is worse than i remembered. Each  "conversation" is in a single file. There are multipe files per day. The single Message itself is in an easy to parse format, but retrieving it all together would be absolutely annoying. If it was XML it would be really simple to parse, since there would be a logical structure if it was done right.
However that is just one of the minor issues. I gave up importing my miranda history, because I would have had to convert it into exactly that weird convoluted format. I estimate that exporting from that format is almost as difficult, which would be an issue when switching from pidgin to something else.

> **NoReflex said:**
> Regarding your pulseaudio issues - you could try to remove pulseaudio and use alsa. I'm using alsa right now because PulseAudio + FlashPlayer = Firefox crash on my notebook (Ubuntu Jaunty - Dell Inspiron 1520). 

Thanks I will consider that at some point. I just fear that it might break other things that work now.

I still hope that it gets better with jaunty. Maybe I will run a test in a VM later at least for audacity with pulseaudio. That could possibly help me to figure out what it requires to work.

---

### Post by detroit/zero on 2009-02-28
> **trendyabinash said:**
> Hey man see it is our own choices.
Nothing in the world is perfect, but I know these ubuntu guys try their level best to make UBUNTU PERFECT. And I love their efforts and support.

If you do have bugs then file it in launchpad it would be more useful to all of us
I notice that a lot of bugs in Nautilus and gnome in general go ignored and un-resolved, sometimes for years.

They have a plan that they're sticking to, period. If what you report falls in line with their future plans, well ok. If not, screw you.

Oh well, it's not like we're paying customers or something.

---

### Post by BLTicklemonster on 2009-02-28
> **trendyabinash said:**
> Hey man see it is our own choices.
Nothing in the world is perfect, but I know these ubuntu guys try their level best to make UBUNTU PERFECT. And I love their efforts and support.

If you do have bugs then file it in launchpad it would be more useful to all of us

Eeek, I avoid launchpad like the plague. What a convoluted mess, in my opinion. This is not meant to be a statement that there's anything wrong with launchpad. I only state that when I look at it, I close it and move along. God only gives us so many hours in our life, and I'm not that concerned with tinkering in Linux that I'm going to spend that much time in launchpad. I'll leave that to the people who are into Linux more than I am, though I do consider Ubuntu as my main OS here.

I think it's great that people come in here and voice their opinions on things, though. Sure launchpad is great, and is a useful tool for resolving problems (for everyone but me, mind you), but I think a lot of times posts like this are helpful because someone might come along and be able to tell the OP that there's a simple edit that can be made to get the functionality which is sought.

I get a chuckle when I see people respond as if the OP said, "yo momma wears army boots", and get all upset and defensive.

---

### Post by Vince4Amy on 2009-02-28
The best solution may be to scrap Pulseaudio and Install KDE? Perhaps give Fedora 10 with KDE a go (Installs as KDE 4.1 and upgrades to KDE 4.2)

---

### Post by detroit/zero on 2009-02-28
> **blticklemonster said:**
> eeek, i avoid launchpad like the plague. What a convoluted mess, in my opinion. 
+1

---

### Post by steveneddy on 2009-02-28
Well - you could always go back to Windows, buy a virus scanner, scan daily, check your e-mail every time you open it for visua/trojan/spam, defrag all the time, reinstall once annually just to keep the speed up, call a help desk once in a while 

or go to Mac and pay the price.

Or try another Linux distro that meets your needs more than Ubuntu.

You could install Android on your PC.

You could try BSD or one or the UNIX variants.

It is all about choice. You choose the operating system that makes you happy.

Me? I just find some happy ground, find what works for me, buy Linux compatible hardware and go on with my life and I find that I'm not tweaking and "fixing" things all of the time.

I have Two Ubuntu laptops, several Ubuntu desktops and a Blackberry. It's not hard to stay connected, but I found a way to not try and "fix" it all the time and I can live my life. 

I'm sorry that you are having issues. Maybe you should contribute to a dev team or file bug reports.

I wonder if hardware with better Linux compatibility would help most of your issues.

Good luck.

Cheers

---

### Post by wolfen69 on 2009-02-28
if i complained about every distro that didn't work right for me, i would not have time to do the actual testing. use what works for you, or
participate in making it better. but posting here does nothing. go to launchpad for that. btw, steveneddy, well said.

---

### Post by DjNDB on 2009-02-28
> **steveneddy said:**
> 

Or try another Linux distro that meets your needs more than Ubuntu.

You could [...]

I know my options.
Trying other OSes does not help me getting Ubuntu to work right. People who respond with solutions to do that however do.

> **steveneddy said:**
> Well - you could always go back to Windows, buy a virus scanner, scan daily, check your e-mail every time you open it for visua/trojan/spam, defrag all the time, reinstall once annually just to keep the speed up, call a help desk once in a while 


I am aware of that and those bugs make me think about it every once in a while. But I think they are not impossible to fix and try to suck it up until i am too desperate.

All those things you say are not necessary to keep windows running. I never hat a virus on my PC. I however collected those 16 years ago when i was using the Amiga 500.
They are really hard to get when you use common sense. Virus scanners are available for free, and Linux could be affected as well. It all depends on the users behavior.
No one has to scan daily, defrag is not necessary, and i never called a help desk since i have been working with computers for 21 years now and learned a lot autodidacticly before i started to study computer science.

Spam does not depend on the OS. Someone could however develop a different mail system with mandatory AuthN and AuthZ to prevent Spam from unknown users. That however would make things a lot more complicated and would require that people communicate over another channel first in order to establish their trust. But sometimes it is necessary to get messages from unknown users, and therefore such a system would be obsolete.

---

### Post by wolfen69 on 2009-02-28
> **DjNDB said:**
> Linux could be affected as well. It all depends on the users behavior.

show me 1 instance of a linux user getting a virus. you may grow old looking for the answer.

---

### Post by BLTicklemonster on 2009-02-28
> **wolfen69 said:**
> show me 1 instance of a linux user getting a virus. you may grow old looking for the answer.

Maybe not a virus, but if you use untrusted repositories, you can get all kinds of problems. Happened to me once. Wallpaper was changed to some viral looking something, and I was locked out of certain things I needed to do. Had to redo everything, and learned my lesson real fast like. As he said, it's a user thing.

---

### Post by wolfen69 on 2009-02-28
> **BLTicklemonster said:**
> Maybe not a virus, but if you use untrusted repositories, you can get all kinds of problems. Happened to me once. Wallpaper was changed to some viral looking something, and I was locked out of certain things I needed to do. Had to redo everything, and learned my lesson real fast like. As he said, it's a user thing.

if that's the worst that happens, it's still not too bad.

---

### Post by solwic on 2009-02-28
> **wolfen69 said:**
> if i complained about every distro that didn't work right for me, i would not have time to do the actual testing. use what works for you, or
participate in making it better. but posting here does nothing. go to launchpad for that. btw, steveneddy, well said.

Exactly.  Curse at the dark or turn on a light.  If you don't like an OS, use another.  There are so many Linux distributions that simple statistical probability suggests you'll find at least one that works for you.  

> **wolfen69 said:**
> show me 1 instance of a linux user getting a virus. you may grow old looking for the answer.

Never underestimate the power of stupid people.  I'm sure Linux - like the Mac - has some privilege escalation issues somewhere.  Just because nobody is exploiting them on a grand enough scale to catch media/marketing attention doesn't mean they don't exist.  

Of course, if you have even a half-functioning brain cell[color="red"]*[/color], you'd almost have to *want* a virus to get one in Linux.  :P

[SIZE="1"][COLOR="Red"]
* Remark is meant in the abstract, and not as an attack or attempt to belittle/harass/annoy/agitate any other user/potential user/group/potential group or any other entity, real or imagined.  [/COLOR][/SIZE]

---

### Post by DjNDB on 2009-02-28
> **wolfen69 said:**
> show me 1 instance of a linux user getting a virus. you may grow old looking for the answer.

I said it "could", not that is is yet. As i said, it depends on the users behavior. If you only use the package system you are quite, but not entirely safe. 
There was an article not too long ago saying that the requirements to set up a package mirror are not that high and since the signatures for old packages are still valid, they could be installed in order to make the system exploitable through well known exploits in old versions.

Besides that, everyone who executes software, can damage all files that the process in his user context can get write access to.
It would be easier to get someone to execute a trojan horse however, since it would advertise a useful function and have a hidden damage function.
This is bad if you execute binary only software. Compiling it yourself makes detection easier, if anyone cares. 

After all it's just software and therefore it is always possible to create damage functions, independent from the operating system.
You can also take a look at the [CVE]("http://nvd.nist.gov/nvd.cfm?advancedsearch") to find known vulnerabilities, which implies that there are likely unknown exploitable ones left.

---

### Post by Tamlynmac on 2009-02-28
> DjNDB
I know my options.
Trying other OSes does not help me getting Ubuntu to work right. People who respond with solutions to do that however do.

This statement reveals quite a bit.
What is this fixation with Ubuntu? As others have pointed out there are alternatives. People who respond with solutions should be doing so in the [**Main Support Categories**]("http://ubuntuforums.org/forumdisplay.php?f=327") not in this section. You act as if you're entitled to get some sort of special dispensation. Why waste time complaining when you could simply move on?

I'd suggest you look at a alternative OS and let what appears to be the Ubuntu envy go. Unless your here for an alterer motive.

Good Luck.

---

### Post by BLTicklemonster on 2009-02-28
> **wolfen69 said:**
> if that's the worst that happens, it's still not too bad.

Lmao, except for the brief freakout-panic, and trouble of reinstall.

---

### Post by NeferalCrossfireX on 2009-02-28
> **DjNDB said:**
> There are some aspects in ubuntu that **really** tempt me to not use it anymore. Some of them annoy me every day, others are just bad design decisions.

I just make this list to let others know, and to archive what I would fix if I had the time. It sure is not complete, but those are the things I immediately thought about when I tried to summarize them. 



- nautilus has no drag and drop in the tree view. Also it does not give the same context menu options there as in list view. Also it is not possible to rename there.
I tried a lot of other file management programs of cause they had other aspects i did not like since they are not well integrated in gnome. But maybe i might get used to those or find solutions to mitigate them if i use them for a while.

- pulseaudio sometimes does not work after suspend, although it comes with /usr/lib/pm-utils/sleep.d/01PulseAudio which seems to be supposed to handle that. I tried adding my own version 

in /etc/pm/sleep.d which does not work:



If i do the same manually when it's broken it works again

- In several applications context menus can only be used on empty spaces. e.g. Nautilus. If you have a folder with content and white space you can right click to create new files/folders and so on. However there is no way to do that if the folder is so full, that there is no whitespace.

- There is no gapless playback of mp3s in rhythmbox and other apllications. Only some kind messy of workaround by crossfading.


- pulseaudio has no AC3 passthrough. There is a solution by reencoding which works, but sounds quite bad. If i suspend pulseaudio and use the device exculsively there is a 2 second period until the device started and therefore the beginning of the audio is missing.

- I bought a new Mainboard for Ubuntu on which suspend to ram basically works. However often one of the Hard disks fails and I have to run a script I came up with in order to reset them. I should think of automating it. 

- Sometimes the systray icons float around as windows on the desktop

- pidgin has no xml history, but only crappy csv files. That makes it harder to export into other formats because no XSLT could be used.

huh thats weird i can drag and drop in the nautilus tree view, and rename. it sounds like you have a crapped out install

---

### Post by DjNDB on 2009-02-28
> **Tamlynmac said:**
> This statement reveals quite a bit.
What is this fixation with Ubuntu? As others have pointed out there are alternatives.

That's because there i know what i have and what needs to be fixed. 
Intensively evaluating other Distributions or OSes would take more time than i have atm.
It always takes a while until the issues come up, because OSes are complex. Back in 2000 i used Mandrake for half a year, but i was still into gaming and at one point i reinstalled windows and had no interest in taking care of two OSes. Since then my needs involved into something more complex and i've been evaluating linuxes every few years to see that some aspects were not working the was i would expect them to. 
I switched to Ubuntu 2 Month ago, because i used it a lot already. However that was for working. At my University of applied science our faculty has ubuntu in all pools, so i've been exposed for 3 Years. Last year i developed software as my Bachelor thesis on Ubuntu for an Embedded system running STLinux.
Ubuntu is fine for my working requirements, as probably most of the other linux distributions. But Multimedia, such as video and audio editing and watching movies are an important part of my everyday life. I had an elaborate list with migration requirements and most of them seemed to be fulfilled by ubuntu at the point i made my decission. The issues however popped up after some days of use and having spent a lot of work and money to get things working so far. 

I will eventually look for alternatives if i can't resolve the major issues, but I will probably have a look at jaunty first in April to see if the worst has been fixed.

If i could not live with those issues at all I would have switched back immediately. However I created some workarounds for the worst ones that take the edge off them a little and make them bearable.

---

### Post by DjNDB on 2009-02-28
> **NeferalCrossfireX said:**
> huh thats weird i can drag and drop in the nautilus tree view, and rename. it sounds like you have a crapped out install

That's interesting. Which version of nautilus do you have? And you can drag+drop from tree view to tree view?

---

### Post by egalvan on 2009-02-28
> **DjNDB said:**
> That's interesting. Which version of nautilus do you have? And you can drag+drop from tree view to tree view?

I drag+drop (copy or move) from tree to tree,
 from hard drive to USB,
 from CD to hard drive.

I used it to move 96Gb of info off a 100GB drive onto another 750GB drive. (re-formatted the 100GB, then copied everything back)
Yes, using Nautilus, right mouse button.


Running Hardy 8.04.2

**Nautilus 2.22.5.1**

---

### Post by Tamlynmac on 2009-02-28
> DjNDB
That's because there i know what i have and what needs to be fixed. 

This again reflects a fixation, you remain in the Ubuntu environment for an illogical reason.

As an ex-electron microscopist (principally SEM), while at Los Alamos I realized what was wrong with Windows. Most all SEM apps are written for Windows and often x-ray analysis acqustion was interrupted by a Windows failure (no need to elaborate). Hence, my choice of Linux/Ubuntu when considering available options for personal use.

Identifying problems related to Ubutnu then rationalizing by remaining in said environment based on a time factor, is somewhat ambiguous. As you appear to have time to both identify issues and apply workarounds.

Your rational appears to be somewhat distorted. This is simply an observation and not meant to inpune your character in any way. 

I will no longer respond, as I suspect this post will be scrutinized. I bid you good day and will unscribe to this thread.

---

### Post by DjNDB on 2009-03-02
> **egalvan said:**
> 
Running Hardy 8.04.2

**Nautilus 2.22.5.1**

Thank you. I am running 8.10 Intrepid Ibex with Nautilus 2.24.1 .
I'll try downgrading to see if it works then.

---

### Post by DjNDB on 2009-03-02
> **Tamlynmac said:**
> This again reflects a fixation, you remain in the Ubuntu environment for an illogical reason.
The logical reason is simple. I spent a lot of time evaluating if Ubuntu meets my needs. To test another distribution would probably require several days, which i don't have until summer. Since i need my system up and running and the basic requirements are met i'll either keep Ubuntu until i have time to try something new to a degree that i am sure that migration does not break something more important, or go back to windows were I know that everything works and put Ubuntu back into a Virtual Machine for work only.

---

### Post by solwic on 2009-03-02
> **DjNDB said:**
> The logical reason is simple. I spent a lot of time evaluating if Ubuntu meets my needs. To test another distribution would probably require several days, which i don't have until summer. Since i need my system up and running and the basic requirements are met i'll either keep Ubuntu until i have time to try something new to a degree that i am sure that migration does not break something more important, or go back to windows were I know that everything works and put Ubuntu back into a Virtual Machine for work only.

The solution to this is simple:  use what works for you.  If you don't have the time/desire to investigate or test other distributions (which you, yourself, said), then you're going to have limited results.  This is a basic programmer's rule:  GIGO.  Which means, "Garbage In, Garbage Out."  You get what you put in.  It is what you make of it.  You reap what you sow.  

Pick your metaphor.  

Clearly you have time to argue the point on this forum, though, so I would recommend - if time is such a factor - spending more time fixing the solution and less time complaining/arguing about it.

Just my two cents.  :)

---

### Post by BLTicklemonster on 2009-03-02
> **NeferalCrossfireX said:**
> huh thats weird i can drag and drop in the nautilus tree view, and rename. it sounds like you have a crapped out install

Come to think of it, I can drag from where ever I am into a folder in the tree, but not one of my partition icons, just the folder icons beneath them. Always have been able to since I can remember.

---

### Post by stchman on 2009-03-02
I personally use Nautilus and like it.  Is it perfect, no.  I can do file management just as well as when I was on Windows.

As far as PulseAudio, I just use ALSA in my sound preferences.

When it comes to viruses unless someone has specifically written a virus for Linux it will not affect Linux systems.  In order for a Linux virus to work it would need to be executed as root or sudo.  Unless someone has gone out of their way and made a root account the OS is protected.  Also the user would have to go out of their way and sudo the virus.  Lets not forget that you would have to give the virus executable permission.

There is too much that needs to be done to make a Linux virus.  Besides there are millions of moronic Windows users that will double click on anything.  Why make it difficult by writing Linux viruses when Windows viruses are easier to implement.

---

### Post by jbysmith on 2009-03-02
Could always try something different if its not working out for you too.  PCManFM is a pretty interesting replacement. There's others out there too of course, Thunar, Rox, etc etc.

---

### Post by solwic on 2009-03-02
> **stchman said:**
> 
As far as PulseAudio, I just use ALSA in my sound preferences.


Wish that worked for me.  The program freezes whenever I try to change it.  Have to reboot to fix it, as logging out doesn't restore the lost sound.  

:(

---

### Post by munishvit on 2009-03-02
Nautilus is not as fast as windows explorer. One can check it by getting deep down in the long hierarchy and hitting 'back' or 'up' button quickly several times. 
Moreover 'up button works as if it is 'back' and visa versa.

Edit:
> Recently I installed Wallpapoz application to have different wallpapers on different Workspace. It takes considerable time to get the wallpaper changed, when you switch to other Workspace. But, in KDE the process is very fast. 
Does the reason behind this is the application package itself, or is this due to some internal differences in GNOME and KDE?

---

### Post by longtom on 2009-03-07
> **DjNDB said:**
> Thank you. I am running 8.10 Intrepid Ibex with Nautilus 2.24.1 .
I'll try downgrading to see if it works then.

Don't.

I never did that before, but since one wants to know the limitations of what you ae working with, I just did it to confirm your problems.

However - running 8.10 with Nautilus 2.24.1 I can do all these things you complained about in your first post.

> nautilus has no drag and drop in the tree view.

It does with me with above versione quite smoothly...

> Also it is not possible to rename there.

Just did that as well.  Worked like a charm...  Changed the name of my desktop pic...so it disappeared...stupid me...

> Also it does not give the same context menu options there as in list view

I don't see that as a show stopper.  It might actually be the reason it has different views...to provide to the user different options.



I guess some of the stuff you are struggling with might not be caused by the applications you are struggling with.  

Especially people who know a lot more than the average user have, on occasions, the tendency to tweak themselfes into trouble (I am the first one in the row...and I am average at best).


Just my R1.50

longtom

---

