---
title: "Your Constructive Criticisms of Linux/Ubuntu (and Your Solutions if any!)"
date: 2007-10-10
forum: Testimonials &amp; Experiences
---

### Post by Yfrwlf on 2007-10-10
**Part 1**: What are your gripes about Linux/Ubuntu currently and what do you suggest as a fix for them?  Please give constructive criticisms only, and please no "stop complaining" or other unhelpful remarks.  While it is important that anyone who knows a bit about programming help to solve these bugs, giving those who don't know the opportunity to learn and get more information, or giving them other ways of helping out like bug finding and discussion is a helpful way to contribute too. :)

**Part 2**: Do you think that the next version, Hardy Heron, should mainly focus on fixing bugs and perfecting "blemishes" that exist, or do you think it should focus on adding more features?


I feel more widespread discussions about the problems currently facing Linux are needed in order to organize action to address them.  (Not that launchpad isn't also a great place to do so, but some problems go beyond bugs.)


My own list:

Part 1
1. Consistency and standards.  A very large topic, yes, but while it's important to recognize that programmers are free to do whatever they want of course, users like having applications that always have the user's decorator theme, mouse theme, and a copy/paste to clipboard that always works.  I feel there is a natural attraction to the programs that allow this because users prefer them, but I still feel that distro organizers should focus on sticking to modular systems/programs to allow compatibility and usability by other programs.  In other words, standards!  They can be very helpful to encourage further development of software for Linux!  At least now copy/paste works between KDE and Gnome applications, from what I've seen, but more work needs to be done to make things more modular like a theme system that can work with multiple window managers to allow any theme to be used by both, including the mouse cursor? :)

2. Ease of use.  Ubuntu's reason for life and it's subsequent gain in popularity.  While I feel Ubuntu is **easier** than alternate OSes to use, there is always room for improvement of course.  One particular area comes to mind.  While the power of the repository concept is great, what about applications that aren't in there?  How is it fair that Windows and Mac have nice auto-installers while Linux often falls very short in this category?  Why has the autopackage format failed?  Right now, the easiest package format for Ubuntu and Debian are DEB packages, while there are RPMs for Red Hat distros.  Does anyone have any ideas about what the problem is and why the "perfect" package installer hasn't been made, and if it has been why it's not being used?  Why isn't there a much greater pull to get the system sorted out so that users can find these nice packages much more easily on the internet for Linux?  Ubuntu could certainly help promote a universal package installer for Linux if it wanted to.  Again, while anyone is free to roll a distro how ever they want, keeping the system in tact that can handle an easy-to-use installation package should be highly sought after and users and developers alike should all demand a single system they can all use to ensure the widest compatibility of their programs.

3. To the more petty complaints.  I'd like to see a hotkey that will bail you out of X and into a user-friendly system for restarting X or an X program (say, a full-screen application that has frozen) whenever the Ctrl-Alt-F*, Ctrl-Alt-Backspace, or any other similar keys are locked out by the application or by X, yet the mouse is still responsive and the only fix is to remote in or do a hard reset.  You have to expect crashes for applications, so solidifying the rescue system should be a high priority IMO.  My only suggestions for this issue are to make it so the above hotkeys always have precedence over any others, and/or a user-friendly GUI tool can be made to allow X to be restarted and/or a process to be killed?

4. Auto-mount all disks with read and write access by default.  I recently witnessed a friend doing an install of 7.10 beta, and it doesn't seem like this issue has been addressed yet.  If you use the guided partitioning option to install Ubuntu, existing partitions (even ext3 ones) are to be mounted each time from Nautilus by clicking on them and then giving the admin password in order for root to mount them.  There is an option in Gnome for the name of the disk after it is mounted, but there is no option to always automatically mount these partitions without editing fstab.  If you do manual partitioning, after specifying all the mount points, fstab will contain them all, but the guided partitioner I feel should be smart enough to always mount any partitions that fstab missed without needing root to do so manually.  It's particularly a hassle for users wanting to migrate to Linux from Windows who have their content still on their Windows partition.  The guided partitioner (using gparted) does a great job of automatically shrinking the NTFS partition to install Ubuntu, but now if it'd only automatically keep it mounted, too. :)

5. Very small bugs, possibly bug reports for them already but I will mention it here.  Dolphin: Allowing margins to be adjusted when in detailed view would be awesome, and Nautilus: the first-click-doesn't-stick bug with the margins would be nice to have fixed.  I've seen this bug for a long time and it gets old when each time to try to click on the margin to widen it, the first click doesn't work, but the second time you try to do it it works.  Weird!

Part 2
I would like to see the current systems polished up, and only the most critical features added in order to solve the biggest problems.  While the bigger problems are big problems, polishing and bug fixing are also critical to an awesome overall user experience that leaves one confident in the security and stability of their system.  I think work should be focused on usability testing, polishing, and bug fixing above most other things so that version 8.04 will be very worthy of Canonical's Long Term Support.

---

### Post by BrendanM on 2007-10-10
My single biggest gripe about Linux: WILLFULY OBSCURE COMMAND LINE PROGRAMS

Examples:
"Hmm, I use mount to mount a drive, I'll bet unmount unmounts a drive..."
"Nope, it's umount."
"Wha...?"

Neither "del" nor "delete" actually deletes a file.
"Copy" doesn't copy a file, nor does "Move" move one.

I realize there are historical reasons behind a lot of these, but seriously, it's 2007. Any command that a reasonably intelligent person would try (and that wouldn't somehow conflict with other commands) should be aliased to the proper command. That is "delete" should call "rm", "copy" should call "cp", etc.

Another thing that irritates me is command line programs that give you zero feedback by default. We're not dealing with a teletype printer here, people, screen space is cheap. If you're an uber-hacker, there should be a global variable you can set to make all your programs return no feedback, but for the rest of us, it would be really nice if all programs operated in verbose mode by default. I wouldn't mind a "file copied" message when I cp something.

One of these days, I'll sit down and write a shell script that generates all the aliases I think should exist. Does anyone have any other examples where the obvious command is not the right one?

For the record, I love Linux, but it gets on my nerves when I have to google for how to do simple things because the first-guess command is hardly ever the correct one.

---

### Post by 23meg on 2007-10-10
> it gets on my nerves when I have to google for how to do simple things because the first-guess command is hardly ever the correct one

Try ```
apropos guessed_probable_command_name
```

---

### Post by BrendanM on 2007-10-10
Meh, not that helpful. For example, "apropos delete" doesn't return "rm" in its list of programs.

---

### Post by Lord Illidan on 2007-10-10
That's because rm stands for ReMove, not delete.

---

### Post by Dixon Bainbridge on 2007-10-10
Linux is like free form jazz. It just goes where it wants to, baby.  How do you impose standards on a collective that actively encourages self expression? Each linux distro is its own little personal statement. You can't really standardise that, otherwise there would be no point in distro's.  You'd just have one monolothic OS called Linux and nothing else.

I agree that there should be improvements in things like cutting and pasting, but then thats true of OSX and Windows as well.  And this ease of use thing, well, I guess you're talking about user-friendliness here? There's no such thing. People work differently and react differently to different environmets. THere is no one GUI fits all. The great thing about linux is there is no standardisation of GUI interface. Don't like Vista's filemanager? Tough. There's not too many alternatives. Don't like OSX? Tough, you will work the Apple way. Don't like Finder? Too bad.

At least with linux I can have bolt on what I want and work my way. And if thats at a price of less slickness and shine, and consistency, then so be it. At least its my way.

---

### Post by BrendanM on 2007-10-10
Thanks, I'm aware of that. My point is that a reasonable person will enter "delete" not knowing that the command is "rm" and I think "delete" should work. Even if you wanted to make it work and then throw a little message like "use 'rm' in the future" that would be fine. I'm just saying there's no reason for simple commands to be deliberately counterintuitive.

---

### Post by Kvark on 2007-10-10
I agree with BrendanM's points about the command line. But I don't think thats the only place with that problem, abbreviations in general are a pain. Just because someone is too lazy to write a whole word nobody has any clue what they wrote until they are told what the abbreviation means.

If I could remember my initial guesses the first time I saw a Unix like file system. Hm, it was something along these lines...
/dev = Development related stuff like that source code everyone are talking about.
/opt = Options, the configuration files I need to edit.
/usr = My user files.
/bin = The trash bin, luckily I didn't try emptying it when I saw how full it was.

When programming in C i always forget which random consonants from the full words where included in the (mis)spelling of function names. It would be a lot less painful if strncmp was compare_strings and strpbrk was find_character.

---

### Post by Yfrwlf on 2007-10-10
> **Dixon Bainbridge said:**
> At least with linux I can have bolt on what I want and work my way. And if thats at a price of less slickness and shine, and consistency, then so be it. At least its my way.

Then you can stick to the programs that have their own GUI instead of using the window theme that you chose.  I believe that most users like choosing the theme they want to use instead of allowing the programmer to decide for them.  Standards allow more choice, they allow the user to be more in control of their own programs, and if they don't, the standard isn't good enough and a new one should be made.  I'm talking about enabling users by modularizing and standardizing on certain systems so that everyone can have a much clearer idea about how to write programs for Linux, so that YOU, in turn, can have more programs, and more *freedom*.

I appreciate your comment, but believe this common argument against standardization is beating around the bush of a very important issue that often is not understood correctly IMO.  Yes, developers should be free to do whatever they want.  Yes, I can make my own distro that makes all the windows neon pink and unchangeable with black text on a black background.  But wouldn't you much rather have systems you controlled and had more software that was compatible and interoperable?  Users are deciding that right now, by going with distros like Ubuntu that are coherent and easy-to-use, but if Ubuntu started using a completely different platform that was incompatible with all other Linux programs they would alienate themselves and hurt development for their platform and in turn, their developers and users.

My point is that it **is** an important issue that effects the freedom of everyone.  There has to be a balance between conforming to an unchanging set of APIs (sticking with OpenGL 1.0 and never adopting 2.0 as technology advances) and every program using their own totally different systems that each use different libraries and different kernels.  Either one of those extremes are going to limit development, create duplicate work and a horrible OS, and most importantly take away *your* freedom to develop programs for the platform and also use the platform, as well as the freedom of everyone else.  Free Software is free only if access to it is realistic.  There are things that are very important for allowing widespread access to software other than the OSS license that gets tagged onto it.  Developers should empower users, and other developers, by programming with them in mind as well as their program.  It's considerate, it's also **not removing any freedoms like you imply** (just the opposite).  If they really need to make their own new API or whatnot, or even better, update an existing one, fine, they should do so.  I'm certainly not saying their freedom to do so should be removed, only discouraged where it's inappropriate and not needed unless there is clear benefit, otherwise no one is going to want to play baseball in their cactus patch.

In conclusion: Don't use bad programs.  Stick to ones that empower you by being modular, coherent, fast, and friendly toward other programs and your system (standardized) unless need be, and if bugs exist then consider the option to help fix them instead of reinventing the wheel.  I'm not trying to force you to use what I think you should use, I'm trying to say that for the sake of your freedom and that of others, please consider running something like Linux before you consider running Backwoods Unix #142 that is incompatible with all other programs ever made for any other platform.  You still have a choice, but one plays nicer and gives you much more freedom in every way than the other choice, and if you don't like some little thing about it you're free to improve it.

---

### Post by n3tfury on 2007-10-10
> **BrendanM said:**
> My single biggest gripe about Linux: WILLFULY OBSCURE COMMAND LINE PROGRAMS

Examples:
"Hmm, I use mount to mount a drive, I'll bet unmount unmounts a drive..."
"Nope, it's umount."
"Wha...?"

Neither "del" nor "delete" actually deletes a file.
"Copy" doesn't copy a file, nor does "Move" move one.

I realize there are historical reasons behind a lot of these, but seriously, it's 2007. Any command that a reasonably intelligent person would try (and that wouldn't somehow conflict with other commands) should be aliased to the proper command. That is "delete" should call "rm", "copy" should call "cp", etc.

Another thing that irritates me is command line programs that give you zero feedback by default. We're not dealing with a teletype printer here, people, screen space is cheap. If you're an uber-hacker, there should be a global variable you can set to make all your programs return no feedback, but for the rest of us, it would be really nice if all programs operated in verbose mode by default. I wouldn't mind a "file copied" message when I cp something.

One of these days, I'll sit down and write a shell script that generates all the aliases I think should exist. Does anyone have any other examples where the obvious command is not the right one?

For the record, I love Linux, but it gets on my nerves when I have to google for how to do simple things because the first-guess command is hardly ever the correct one.

i agreed with this when i first started using Linux, but over the short amount of time i've been working with the command line (and i actually LIKE and PREFER to use it so i learn as go) i'd rather keep things as they are.

that being said, a response to the OP:  Wireless, wireless, wireless  (yes i understand about lack of manufacturer support, thanks).  More and more people are untethered and a TON of issues in the AB forum are wireless ones.

---

### Post by Yfrwlf on 2007-10-10
> **n3tfury said:**
> i agreed with this when i first started using Linux, but over the short amount of time i've been working with the command line (and i actually LIKE and PREFER to use it so i learn as go) i'd rather keep things as they are.

that being said, a response to the OP:  Wireless, wireless, wireless  (yes i understand about lack of manufacturer support, thanks).  More and more people are untethered and a TON of issues in the AB forum are wireless ones.

I agree that making more sane versions of basic Linux commands would be very helpful for beginners, and the shorthand abbreviation method is faster for advanced users.  Perhaps both should be allowed?  That wouldn't be hard to implement, right? ;)

Fully agree with the wireless part, too.  Actually, that brings me to another important link in the Linux social/development network: A system for showing you ***exactly*** what hardware you can buy in order to build a very Linux-compatible computer to give those manufacturers who support Linux well preference over ones who don't.  I'd much rather have the ones that did get my money than those who didn't want to play nice with Tux.  There is a project here that is trying to do just that called The Dohickey Project: [http://www.dohickey-project.com/](http://www.dohickey-project.com/)

There are some docs on Ubuntu.com that tell you about compatible hardware, but nothing that's extensive nor that gives you an idea of exactly which things are 100% plug-and-play so you can buy the best components.

---

### Post by bonzodog on 2007-10-10
> **BrendanM said:**
> My single biggest gripe about Linux: WILLFULY OBSCURE COMMAND LINE PROGRAMS

Examples:
"Hmm, I use mount to mount a drive, I'll bet unmount unmounts a drive..."
"Nope, it's umount."
"Wha...?"

Neither "del" nor "delete" actually deletes a file.
"Copy" doesn't copy a file, nor does "Move" move one.

I realize there are historical reasons behind a lot of these, but seriously, it's 2007. Any command that a reasonably intelligent person would try (and that wouldn't somehow conflict with other commands) should be aliased to the proper command. That is "delete" should call "rm", "copy" should call "cp", etc.

Another thing that irritates me is command line programs that give you zero feedback by default. We're not dealing with a teletype printer here, people, screen space is cheap. If you're an uber-hacker, there should be a global variable you can set to make all your programs return no feedback, but for the rest of us, it would be really nice if all programs operated in verbose mode by default. I wouldn't mind a "file copied" message when I cp something.

One of these days, I'll sit down and write a shell script that generates all the aliases I think should exist. Does anyone have any other examples where the obvious command is not the right one?

For the record, I love Linux, but it gets on my nerves when I have to google for how to do simple things because the first-guess command is hardly ever the correct one.

Actually this is a *really* easy problem to fix, and I am surprised no-one has suggested it yet -- when ever you open a terminal, the first thing that bash (the shell) does is read your ~/.bashrc file. In there you can list aliases for commands that you would like to use. 
The idea behind this is so you can type in the name of a program, say, urxvt, and it will read the alias definition which might contain a whole bank of switches to use to change the look and feel of it each time.

All it would need is for the devs to write up a bashrc file thats installed in your home dir the first time you use the distro after install. This would contain a common set of aliases to use. In fact, it might be useful to set up a launchpad item about it.

---

### Post by Pekkalainen on 2007-10-10
Part 1:

1. We have seen great improvement in autodetecting hardware and peripherals. Except for the mouse. I want the forward/back buttons on my Logitech MX510 to work out of the box and so does a lot of other people, especially those we are trying to save from the clutches of that proprietary legacy operating system.

2. Not really Ubuntu specific at all but here it goes: Applications that follow open standards. While we have formats for music, spread sheets, word processing, movies, instant messaging and a few others (and thats a damn good job! dont get me wrong here) today we are aching for a free-as-in-freedom way to do voice and video chat so that we can beat the IM-client of that old proprietary legacy operating system. Most of the work is already done: we have free standards for these two. But they are not properly implemented anywhere.

If we want to win people over we should do it with our own standards, not imitate the ones of that old legacy operating system because naturally we would end up playing catch-up to their stuff all the time and frankly it makes us look bad:

"loLz? Linux cant do MSN? what a piece of crap!"

 Lead, not follow!

3. Nicer looking Gnome theme by default, especially the wallpaper. This has been discussed all over the forum so I wont go any deeper into it than this:

"Eye candy is a feature".

Part 2:

Since the next version will be an LTS I think most things from Gutsy should remain in feature freeze and this coming cycle should consist mostly of bug squashing and other ways to polish it. LTS promises stability and great support and thats what we should work for. Stability over features. We have plenty of time for bleeding edge between LTS releases.

---

### Post by forrestcupp on 2007-10-10
My only legitimate complaint is not in the system itself, but in the mentality of a lot of people in the community that think that Free software is a morality issue and Microsoft and anything proprietary is evil.

Other than that, I think Linux is coming along quite nicely at an amazingly fast speed.

---

### Post by phenest on 2007-10-10
> **Yfrwlf said:**
> I agree that making more sane versions of basic Linux commands would be very helpful for beginners, and the shorthand abbreviation method is faster for advanced users.  Perhaps both should be allowed?  That wouldn't be hard to implement, right? ;)

What makes you think the "shorthand abbreviation method" is for advanced users, or for speed? If there was a "version for beginners", you'd never move to the "advanced version". So, how do you think the "advanced users" got there?

That's like going to France and expecting the French to know English too, so it's easier for you. Why can't you just learn French?

If you want to use Linux, then learn Linux.

This is like asking to have a GUI for every terminal command, and just as ridiculous. :lolflag:

---

### Post by Pekkalainen on 2007-10-10
> **forrestcupp said:**
> My only legitimate complaint is not in the system itself, but in the mentality of a lot of people in the community that think that Free software is a morality issue and Microsoft and anything proprietary is evil.

Other than that, I think Linux is coming along quite nicely at an amazingly fast speed.

Morality? Would you like the hood of your car nailed shut and the only one allowed to open it is the manufacturer? You have no way of knowing if the car runs properly until it breaks down, you have no idea if the emission levels are optimal, you have no control over a thing that you own. Thats what free software is about. Freedom, choice and control. Morality is a subjective thing.

---

### Post by yorkie on 2007-10-10
My main complaint with Ubuntu is that there is no upgrade from 6.06 Dapper to 8.04 Hardy Heron.People who want to run a stable release have to do a clean install or upgrade from 6.10.,7.04, 7.10 and then finally to 8.04.
In my opinion  I would rather have 12 monthly  releases  so we have more stable versions of Ubuntu.

---

### Post by 23meg on 2007-10-10
[QUOTE=yorkie]My main complaint with Ubuntu is that there is no upgrade from 6.06 Dapper to 8.04 Hardy Heron.People who want to run a stable release have to do a clean install or upgrade from 6.10.,7.04, 7.10 and then finally to 8.04.[/QUOTE]

LTS to LTS upgrades *will* be supported. From [http://www.ubuntu.com/aboutus/faq](http://www.ubuntu.com/aboutus/faq) :

> **Is there a specific Enterprise Release?**

In addition to regular releases, the Ubuntu team may make an Enterprise Release, also known as a 'Long Term Support (LTS)' Release, that has received additional stabilisation, polish and translation work. These Enterprise Releases will be supported for a longer period of time than the standard 18 month support of the time-based Releases. Upgrades will be supported from Enterprise Release to Enterprise Release.

[QUOTE=yorkie]
In my opinion I would rather have 12 monthly releases so we have more stable versions of Ubuntu.[/QUOTE]

A longer release cycle doesn't necessarily mean more stability. As long as Ubuntu is to remain cutting edge and the workforce remains equal, expecting huge differences in release quality isn't realistic, since the work to be done remains equal regardless of the cycle length.

---

### Post by Incense on 2007-10-10
> **yorkie said:**
> My main complaint with Ubuntu is that there is no upgrade from 6.06 Dapper to 8.04 Hardy Heron.People who want to run a stable release have to do a clean install or upgrade from 6.10.,7.04, 7.10 and then finally to 8.04.
In my opinion  I would rather have 12 monthly  releases  so we have more stable versions of Ubuntu.

How do you know there is not an upgrade path?

---

### Post by houndhen on 2007-10-10
I understand the part about learning the terminal language but I also have known the frustration of not knowing a simple command to do what I would like to do. I know it takes time to get comfortable with linux. Some of us older people don't learn languages as quickly as others or when we were younger. "Delete" and "copy" are just used in so many things of our daily life that it is just mindblowing to a newbie like myself that they don't do anything when typed into a terminal. Not griping, just agreeing with BrendanM. I had never thought of saying it before but it makes a lot of sense.

I am learning but it is slow. I knew it would be. I will probably never be a linux guru but I want to be able to tweak my system and know how and why to do it. 

Recently I had 6.01 installed and working and got the bright idea to upgrade to 6.10. Things got messed up and I had no idea how to straighten it out. My solution with what little I know is to just re-install. Using an older machine so if 7.04 doesn't work on it then I will go back 6.01 and settle in on that computer. It is not my main computer. I have pclos and xp dual booted on my main computer. I plan to dual boot win98 and ubuntu on the older pc and increase my knowledge by using it.

BTW... On the forum I have found a lot of answers to questions that I have had. Great forum and community. The forum and community is one of the things that has prompted me to try ubuntu. At this point I don't know the difference between Gnome and KDE or the different kernels. Actually I don't care, right now I just want something that will work and I can learn and understand what I am doing.

houndhen

---

### Post by 50words on 2007-10-10
Better compatibility and support for document scanning Xsane is not particularly good at this, and neither is Kooka. They need to (1) recognize the "scan" button on most scanners, (2) work with auto-detecting blank pages for duplexing, (3) work with auto-detecting more pages, and (4) automatically pop up a "save as" box to a configurable directory.

---

### Post by maybeway36 on 2007-10-10
Linux needs a standardized way of installing 3rd party software from CD. .run isn't cutting it.

---

### Post by FuturePilot on 2007-10-10
I would really love to see something happen with sound. I want to be able to use my sound card's hardware. Right now EQ is pretty much left up to the individual apps and it's mostly software rendered. I would really love to see a way that I could set a global EQ that uses the hardware to render it. And possibly different environment effects too.

---

### Post by hardyn on 2007-10-10
linus's user space driver system that i think is in the 2.6.22 kernels should do alot to help with things like mouse buttons and other hardware... i don't think they work out of the box in windows either?

the terminal commands are legacy unix stuff (circa 1970), that is just the way it is... if the ubuntu people decied to change them, ubuntu would become a really obscure distro, and would probably fall out of favor by alot of people... but i don't think the changing of the syntax is something we will have to worry about.

what i would like to see is the implimentation of certain MS defacto standards, such as UNPN, there are groups working on it... but the implimentation of a unpn clone system into the networking components would in my mind to alot to make linux a little more successful on the desktop.

suspend and hybernation in notebooks still seems to be quite lacking... and is hit or miss at best.  I don't really know what technical issues surround this, but both apple and windows have nicely suspending machines (apples is very good), it would be nice to see linux work as well.
 
all and all i think it is progrssing very nicely... things like upstart, and the proposed changes to gnome are suggesting a really strong effort to become a proper desktop system.

---

### Post by kevdog on 2007-10-10
I think Ubuntu should dump Network Manager by default and go with WICD.  If people want NM they could get if from the repos.  

That's it, short and sweet!

---

### Post by Nano Geek on 2007-10-10
> **maybeway36 said:**
> Linux needs a standardized way of installing 3rd party software from CD. .run isn't cutting it.What 3rd party programs are you installing from a CD in Linux?

---

### Post by Yfrwlf on 2007-10-10
> **phenest said:**
> What makes you think the "shorthand abbreviation method" is for advanced users, or for speed? If there was a "version for beginners", you'd never move to the "advanced version". So, how do you think the "advanced users" got there?

That's like going to France and expecting the French to know English too, so it's easier for you. Why can't you just learn French?

If you want to use Linux, then learn Linux.

This is like asking to have a GUI for every terminal command, and just as ridiculous. :lolflag:

Understood and I agree for the most part, perhaps a better solution would be more ways to learn the system, more help pages and a "man"ual system that included placeholder help docs to redirect users to the commands they were probably looking for.  That, also, would be very easy to implement. :)

---

### Post by forrestcupp on 2007-10-10
> **asjdfwejqrfjcvm msz34rq33 said:**
> What 3rd party programs are you installing from a CD in Linux?

None, because there's no good way to do it.

---

### Post by maybeway36 on 2007-10-10
I wasn't referring to any software in general. An example of this, though, would be like UT2004 or StarOffice.

---

### Post by houndhen on 2007-10-11
Back again with something that I ran into last night.

I was trying to install ubuntu 7.04 and knew from previous installs that the screen resolution was going to be a problem. 

Is there a way to make the livecd where the installer could adjust the resolution so that he/she wouldn't have to drag the screen around using the ALT key and mouse just to see the buttons needed to install the distro to the hard drive?

I know that my video card will support 1024 X 768 but I was stuck with 800 X 600 or something similiar. I tried reducing the font size like I had seen in the forums but that didn't work.

houndhen

---

### Post by ATrentino on 2007-10-11
Mine isn't exactly a criticism, but rather a wish:

To be able to buy a good range of desktops, laptops and servers with Ubuntu preinstalled, and of course, working properly, with all necessary drivers, wireless  and hibernate/suspend working, etc. I know that there are some companies offering some models in some countries, but this is nowhere near satisfactory. 

One thing we can do to improve this is to ask for these machines. When I bought a new HP laptop last month, I emailed them to ask that they sell machines with preinstalled ubuntu. **If we don't show interest, they'll never do it. **

I was actually considering starting a group to lobby companies such as HP to start offering Ubuntu. Perhaps a few hundreds or thousands emails could help change things.

---

### Post by argie on 2007-10-11
> **BrendanM said:**
> Thanks, I'm aware of that. My point is that a reasonable person will enter "delete" not knowing that the command is "rm" and I think "delete" should work. Even if you wanted to make it work and then throw a little message like "use 'rm' in the future" that would be fine. I'm just saying there's no reason for simple commands to be deliberately counterintuitive.

I don't know. I don't think I ever used the word delete for removing stuff before I started using computers. 

My gripe: Upgrades have been hit-and-miss so far. Distribution release upgrades, that is. I don't know how this could be fixed or if it could be at all.

Another one: When packages are upgraded, and show up on the Update Manager, not all of them have Changelogs. Solution: Include changelogs?

I just like to see what the update is giving me and if it's worth it.

---

### Post by chewearn on 2007-10-11
Not something new, but my main gripe at this time:

A real monitor auto-detection (including multi-screens) that works and don't require hours of multiple xorg.conf editing and X restart.  

Not just during OS installation; but, if I just bought a new screen and plug it in, it should work immediately.  Or at least, a one-time auto/manual setup (no X restart please!) and within a minute it is up and running.

---

### Post by aysiu on 2007-10-11
> **AstalaVista said:**
> Not something new, but my main gripe at this time:

A real monitor auto-detection (including multi-screens) that works and don't require hours of multiple xorg.conf editing and X restart.  

Not just during OS installation; but, if I just bought a new screen and plug it in, it should work immediately.  Or at least, a one-time auto/manual setup (no X restart please!) and within a minute it is up and running.
Well, you're in luck. That's a high priority with development. They've implemented it in theory for Ubuntu 7.10, and I think it's still a bit rocky. I believe they are hoping to have it polished by Ubuntu 8.04.

---

### Post by phrostbyte on 2007-10-11
Guys, it's important to understand that Ubuntu (and Linux) is very modular. The command line you guys are complaining about is bash+gnu coreutils. The names of the coreutils (Core Utilities) come from UNIX, rm, cp. There is a reason they are named this way .. back then everything was teletype, it wasn't practical to have long command names!

But hey, as I said, Linux is modular. The command shell can be changed, you can even use python or some weird shell as your default shell. Hell, lets set up a project and come up with an entirely new and innovative shell! :popcorn:

You can do this and still keep bash. Have a cake and eat it too.

---

### Post by Dimitriid on 2007-10-11
If we talk Ubuntu yes there is things to improve  and simply saying "oh wait until X developer works on Y part of  his project" is not good enough, thats why software is Free as in Freedom. 

Ubuntu needs to improve/replace Network Manager as mentioned already, better support for "ugly" codecs ( Yes you want to keep it Law abiding and Free, but give ONE centralized option that installs ALL "ugly" codecs and extras, work with the automatix people for example ). Having something like Java licenses breaking the entire package engine because of a stupid license is exactly why I left windows, Just tell me that I **must** read the license before using it and then its squarely on me no more obscure, unacceptable ( because you cant say yes or not or anything you are just stuck there ) agreements in the middle of the package management.

Also better and more comprehensive support for source to binary packages: Your repos are not going to be updated? Gotta wait 6 months for newer versions of programs? Expand apt-get to handle source code, create a package, handle dependencies, identify is an older version is installed already and proceed. And yes I am aware that this is possible but it needs to be more transparent and easy.

Do something about Kubuntu. Its just not good enough, I know the main focus is Gnome and with good reason ( I personally prefer the gnome feel even if functionality is not as complete as KDE ). If you flatout do not want to spend time with it just take the KDE implementation for somebody else and adapt it better instead of doing your own Custom mess.

Oh and for the love of anything you might hold sacred preinstalla better theme! The art department  really needs to step it up! 

Now on a completely different subject, I don't think I have any criticism to Linux based systems as a whole. If you think about it, most if not ALL of the criticisms you can come up with can be reduced to 2 basic cases

1) Not a fault of developers but hardware manufacturers and other companies boycotting Free software.

2) Already covered somewhere on another distro.

This is specially true for some of the comments here: there are distros with more transparent bash command script on by default, distros with different file structures altogether, distros that address each and every one of my complains, etc. 

And if this mismatch of features do not work for you well you can bet somebody somewhere is already working on a distro that will incorporate most of those features you want together or you can too.

---

### Post by Tux Aubrey on 2007-10-11
I'm with those who actually think things are going really well, but I would love to see:

1) Linux Hardware Compatability Advisor - a Windows dohicky.exe downloadable from the web (or maybe as a virus!).   Just like the Vista Upgrade Advisor.  For everyone who is Linux-curious to get info on what will and won't work for them with Ubuntu (or any other distro).  

2) Better documentation - its so spreadout and much of it (How Tos, Wikis etc) is not maintained very well or is poorly written. Aysiu's site excepted.

3) Marketing - I appreciate what the M-Team has been doing but I would really like to be able download an up to date marketing pack when there is a new release - CD/DVD covers, presentations, sticker templates, Quick start guide etc.  Even the examples included with each new release are often labelled for earlier versions.  I also have a strong feeling that in someone's head there is a great viral marketing campaign for Ubuntu that would sweep the web and give Ubuntu another quantum leap in its user base. (If that person would now step forward and open their brain, it would be greatly appreciated.  I have my trepanning saw ready.)

---

### Post by RAV TUX on 2007-10-11
> **Tux Aubrey said:**
> 

3) Marketing - I appreciate what the M-Team has been doing but I would really like to be able download an up to date marketing pack when there is a new release - CD/DVD covers, presentations, sticker templates, Quick start guide etc.  Even the examples included with each new release are often labelled for earlier versions.  I also have a strong feeling that in someone's head there is a great viral marketing campaign for Ubuntu that would sweep the web and give Ubuntu another quantum leap in its user base. (If that person would now step forward and open their brain, it would be greatly appreciated.  I have my trepanning saw ready.)

You would have to be able to cut through my cast iron helmet. ;)

---

### Post by Tux Aubrey on 2007-10-12
> You would have to be able to cut through my cast iron helmet.

Yes RAV - it was you I initially thought of - but I then realized that your brain is mostly taken up with avatars, E17 hacks and links to video sites.  However, I could always use the practice!

---

### Post by 5-HT on 2007-10-12
Gripes:

** I.** Ubuntu is not (or does not offer) a rolling release :(
 Bring on Grumpy Groundhog- hopefully with an extra 'staging' repo for high-risk, breakage-will-ensue package updates!
[B]
II.[/B] "Restricted modules" :evil:
Many headaches could be solved if these modules were  available separately in the repos a la Debian instead of rolling all of 'em into a monolithic package. 

Apart from those two, I'm very happy with the state of things.

---

### Post by bigboy_pdb on 2007-10-12
There are a few things that I've read that I agree should be changed and there are a few things that I'd like to focus on that I think are important.

I agree that standards are important. Some people complain that standards interfere with freedom, and those people are incorrect. People who disagree with a given standard can easily write a modified version or create their own standard. If people think the modified versions are better then they will be adopted or merged with the preferred standard.

When clear and concise standards are written, it makes it easier for people to design and program software. Also, it is easier to debate about clearly written standards than it is to debate about the code or interfaces of software. In other words, by focusing on standards, emphasis is placed on software and system design.

Regarding terminal commands, I disagree that there should be changes to the terminal. Short commands allow people to enter them more quickly and they keep commands from flowing onto subsequent lines (especially when many commands are being used in conjunction). The terminal should be a tool that is primarily for power users and programmers. Regular users should only have to use the terminal under very limited circumstances. People who are complaining about the terminal (and more particularly the bash shell) should be complaining that there are a lack of GUI programs that correspond with commonly performed operations (where terminal use is not necessary).

I'm not stating that every command should be affiliated with a GUI. For example, it doesn't make sense to have a GUI for grep, sed, or awk. Nor am I stating that GUIs should replace the command line or any current file system. In fact, I believe that each GUI should always correspond to (or use) terminal commands and files. Two reasons for this are automation and systems that don't have GUIs (such as servers).

One advantage of GUIs is that they restrict how the user uses the interface. With a command line, a person can type whatever he/she wants to type. However, with a GUI a person's input is restricted to what the program requires. Another advantage of GUIs is that they can help a person to better understand a program/system just by using the GUI. For example, assume there is a GUI program that changes the fstab file and it has a list of file system types. Also assume that when a person clicks on a given file system, the options for that file system appear. If a person asks for help within the forums and he/she is told to change/paste a line in the fstab file, he/she learns nothing about what he/she is doing. However, if a person uses the GUI program, he/she has exposure to the different types of file systems, as well as, the different options for mounting them (which indicates something about the file system).

**[EDIT]**Although I think it should be apparent from my post, I should add that I think there should be more GUIs for performing common tasks (where it is applicable).**[/EDIT]**

---

### Post by n3tfury on 2007-10-12
> **houndhen said:**
> 
Is there a way to make the livecd where the installer could adjust the resolution so that he/she wouldn't have to drag the screen around using the ALT key and mouse just to see the buttons needed to install the distro to the hard drive?



so THAT'S how you do it, lol.  that was pissing me off on one of my laptops.

---

### Post by glupee on 2007-10-12
I would love to see a magical (i use magical because i'm  not sure if it's at all possible) wrapper type thing that will let me install windows drivers for non-supported devices. ndiswrapper style, but for any piece of hardware. 
ie. my tv-card :lolflag:

---

### Post by Yfrwlf on 2007-10-29
I just had to add that having universal APIs in no way takes away anyone's freedom, but instead gives you more freedom by allowing you to easily swap out programs without breaking everything, making your system more modular so you can have more *choice*.  For example, the fact that X allows me to use whatever window manager I want to with any graphics environment is awesome.  If I liked KWin or Compiz Fusion better than Metacity for running Gnome, I could switch to it.  OpenGL?  That's a very powerful graphics API which I'm told can do more than DirectX10 can (but I don't know if this is true myself) and supposedly can do so faster (not saying I'd be surprised, but simply that I have not confirmed any of this really, though a game programmer told it to me).  So standardization is good, and gives you choice, makes your system more modular and more powerful, and if you think that the API itself is in need of an upgrade, think about contributing to the existing ones before trying making your own, but if you think it necessary, make your own, I just hope it'll truely be better so that it catches on. :)

What I'd really like to see is more of this, like a standardized package manager which allows you to use ANY type of package you want to with your system, whether it's portage, RPMs, autopackages, or DEBs, your system will be able to understand it well enough so that it can install it correctly.  That's what needs to happen, and I've read several articles about people out there working on making it happen so I really hope they are successful.  This will mean programmers can use the package format of choice, and not have to worry about making one package for every system out there to ensure compatibility.

---

### Post by Yfrwlf on 2007-10-29
> **glupee said:**
> I would love to see a magical (i use magical because i'm  not sure if it's at all possible) wrapper type thing that will let me install windows drivers for non-supported devices. ndiswrapper style, but for any piece of hardware. 
ie. my tv-card :lolflag:

I think that's a good idea, but I think what you're wanting already exists in the form of scripts.  There are scripts to take Windows drivers, cut them up or whatever needs to be done with them (I've never used ndiswrapper before), and install them.  But, having a single program that can run a wide variety of scripts for you may be helpful.  A compilation of several ndiswrapper scripts, basically?  Just an idea.

Of course, another solution is to try to buy only Linux-compatible hardware.  That can sometimes be helpful in convincing them to support Linux more, too.

---

### Post by Yfrwlf on 2007-10-29
> **bigboy_pdb said:**
> When clear and concise standards are written, it makes it easier for people to design and program software. Also, it is easier to debate about clearly written standards than it is to debate about the code or interfaces of software. In other words, by focusing on standards, emphasis is placed on software and system design.

Couldn't agree more.  Having a common interface allows you to focus on which program is better that use the interface (API), so that you can easily swap between which program you prefer, giving you *more* freedom to choose.  It means that the wheel doesn't need to be reinvented, it offers a common hub to work with, and instead lets you focus on the programming and design.  OpenGL has been extremely helpful for graphics programming, for example.

> **bigboy_pdb said:**
> I'm not stating that every command should be affiliated with a GUI. For example, it doesn't make sense to have a GUI for grep, sed, or awk. Nor am I stating that GUIs should replace the command line or any current file system. In fact, I believe that each GUI should always correspond to (or use) terminal commands and files. Two reasons for this are automation and systems that don't have GUIs (such as servers).

Again, right on, having both is one thing that IMO has helped make Linux and other systems that do this be so powerful.  You don't need a special command-line program like you do with DOS/Windows, but instead have an all-in-one solution.  I hope it stays that way. :)

> **bigboy_pdb said:**
> One advantage of GUIs is that they restrict how the user uses the interface. With a command line, a person can type whatever he/she wants to type. However, with a GUI a person's input is restricted to what the program requires. Another advantage of GUIs is that they can help a person to better understand a program/system just by using the a GUI. For example, assume there is a GUI program that changes the fstab file and it has a list of file system types. Also assume that when a person clicks on a given file system, the options for that file system appear. If a person asks for help within the forums and he/she is told to change/paste a line in the fstab file, he/she learns nothing about what he/she is doing. However, if a person uses the GUI program, he/she has exposure to the different types of file systems, as well as, the different options for mounting them (which indicates something about the file system).

I agree for the most part that the GUI can be a *quick* learning tool especially in the cases where the program is so powerful that the range of things it can do is huge, but the program is really only normally used to do a few things.  The GUI often will present those few things first, while the man page may bury them and may make things much more confusing when what the user wants to do is simple.  This is sometimes more of a problem in how the man page was constructed though I think.  The only somewhat valid argument against it I think is that users still should learn things and Linux sometimes really makes you learn it and learn it fast, and that's good in a way, but for the normal user who just wants it to work they shouldn't have to, only if they *want* to.  There should always be ways to learn more about certain programs, and that's usually what the command line provides. :)

I fully agree though that there needs to be more GUI programs for certain things so that the non-command-line-oriented desktop user won't freak.  Thankfully many should be pretty easy to make since it's mostly just config file translation and run commands.  Seems like it to me, any way. I still need to try to make one though. =X

---

### Post by keyboardashtray on 2007-10-29
My biggest gripe is the console. GNU/Linux will never reach it's full potential for the desktop end user until it can provide a completely console-free experience. 

The console is a crutch for incomplete GUI programs. Whenever I *have to* do anything by console (or configuration file for that matter) I think "this program is incomplete". Read: *have to*.

I can respect the console on the user end, for it's style - a retro computer thing. I can dig it. I play NetHack. But I take issue with the console die-hards who say it is more powerful. It's only more powerful when the GUI has a limitation (which I'll grant you is most of the time). 

When the console crutch is most evident, when it truly rears its ugly head, and gives me that sad recurring epiphany that, as much as I love it, I could never put even the wonderful Ubuntu on my grandmas computer, is when you download a program, even from Synaptic, and you have "nothing". You have no icon, you have no point of reference to start this new program. You're just supposed to guess whatever console command starts this new program. And from my experience so far, that usually means the program is crap anyway, so I guess in that respect it saves me the hassle of having to run it.

A runner up for me is the filesystem. Wow. I hope the programmers are serious when they say it's a great system for them because from the user end it feels like a holdover from the days when computers were giant contraptions of tubes and wires in big air-conditioned rooms. 

I hate what I think of as the "Great Linux Lie", that "Well, it really doesn't matter that the file system is confusing because you don't need to go in to those files anyway". (Second to the "you really don't need to use the console in Linux anymore" only because everyone knows you need to use the console all the time.)

Whether it is finding a common system sound file to associate with an event in a program, picking an icon for a menu option, or (barring knowing the console command) finding the appropriate program icon for Firefox to associate a filetype with, the average user has plenty of digging around in poorly named directories to do, even on day one.

---

### Post by ncreek on 2007-10-29
I have been active with computers since 1978. I have graduated from 4bit Ohio Scientific to an AMD64x2 4400 over the intervening years. As most of us I have used DOS and Windows and am anxious to leave it behind. I see great things happening in the Ubuntu community and will look forward to it maturing. 
That having been said I think that the rush to put out new versions :I.E. Dapper,Feisty and now Gutsy is going a bit to fast. I have Gutsty AMD_64 running, well poorly, and that is THE issue. I have found a number of packages that the handlers did not do a good job in linking to folders and files. Programs don't work because of poor script calls to none existent locations or to old files that are not applicatable to the new install. 
I feel that a slower release will give the handlers time to debug all the lost associations. Furthermore I find that the wiki is my last effort due to the extreme amount of mislabled titles that have me reading till my eyes bleed and not finding an answer to my question. I know that the software is rapidly evolving but a in OS pointer to the current wiki or doc/man pages would aleviate a great amount of aggrevation

---

### Post by SunnyRabbiera on 2007-10-29
> **Yfrwlf said:**
> **Part 1**: What are your gripes about Linux/Ubuntu currently and what do you suggest as a fix for them?  Please give constructive criticisms only, and please no "stop complaining" or other unhelpful remarks.  While it is important that anyone who knows a bit about programming help to solve these bugs, giving those who don't know the opportunity to learn and get more information, or giving them other ways of helping out like bug finding and discussion is a helpful way to contribute too. :)

**Part 2**: Do you think that the next version, Hardy Heron, should mainly focus on fixing bugs and perfecting "blemishes" that exist, or do you think it should focus on adding more features?[

for part 1:
Lack of collaboration between distributions is a BIG issue and is one of the things keeping linux from gaining ground.
If we would stop bickering about distribution 1 is better then distribution B then a lot of progress can be made...
If there were some way to get the big leaders of Linux like Redhat, Canonical, Mandriva, Gentoo and Debian to co operate with the smaller distributions like PCLinux, Mepis, Mint and whoever else is out there then a lot of great things done... blind idealism, linux's gangland mentality and other things need to be put aside if innovation is ever to happen.

for part 2:
actually i think Hardy should be more focussed on stability and backporting then getting all the flashy stuff to work.
If its one thing I dont like about Ubuntu is its almost microsoft like tactics, if you want to update to version b of your favorite program you should not have to be forced to upgrade the whole @#$% system just to get it working... what is this, VISTA????

---

### Post by glupee on 2007-10-30
> **Yfrwlf said:**
> 
Of course, another solution is to try to buy only Linux-compatible hardware.  That can sometimes be helpful in convincing them to support Linux more, too.
I would have done that had i thought of using linux when i bought the card, but it wasn't so :( aw well. Maybe in time my card will be supported.

---

### Post by bruce89 on 2007-10-30
> **keyboardashtray said:**
> My biggest gripe is the console. GNU/Linux will never reach it's full potential for the desktop end user until it can provide a completely console-free experience. 

The console is a crutch for incomplete GUI programs. Whenever I *have to* do anything by console (or configuration file for that matter) I think "this program is incomplete". Read: *have to*.


[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

> **keyboardashtray said:**
> A runner up for me is the filesystem. Wow. I hope the programmers are serious when they say it's a great system for them because from the user end it feels like a holdover from the days when computers were giant contraptions of tubes and wires in big air-conditioned rooms. 

I hate what I think of as the "Great Linux Lie", that "Well, it really doesn't matter that the file system is confusing because you don't need to go in to those files anyway". (Second to the "you really don't need to use the console in Linux anymore" only because everyone knows you need to use the console all the time.)

Whether it is finding a common system sound file to associate with an event in a program, picking an icon for a menu option, or (barring knowing the console command) finding the appropriate program icon for Firefox to associate a filetype with, the average user has plenty of digging around in poorly named directories to do, even on day one.

The FHS has been around for a long time and will never change for good reason. Learn it.

Can you think of a better hierarchy?

---

### Post by New to Linux on 2007-10-30
As a new Ubuntu (and linux) user, I would have to say that there are a couple of  problems  that need to be addressed :

1. The ability to run a standard set of  linux commands
   - sh, rpm, etc 

Having to change ' sh' to 'bash' is one way to kill an application.

This would make it easier for manufacturers to distribute driver installation software. (such as printers and scanners)

2. Protect the operating system from hangs and crashes. 

Applications can fail, operating systems should not.

---

### Post by Yfrwlf on 2007-10-31
> **keyboardashtray said:**
> My biggest gripe is the console. GNU/Linux will never reach it's full potential for the desktop end user until it can provide a completely console-free experience.

Fully agreed, these remaining problems need to be conquered and you should point out some specifics when you can so that they can be addressed.  Bugs and ideas for improvements can be submitted to Launchpad for consideration.  They are working on many things though, like having X be more indestructible so that you don't have to edit xorg.conf or restart it all from the command line which most noobs would run away screaming at.  I hope these improvements continue so that all issues can be addressed via the GUI *as well as* the console.

> **keyboardashtray said:**
> When the console crutch is most evident, when it truly rears its ugly head, and gives me that sad recurring epiphany that, as much as I love it, I could never put even the wonderful Ubuntu on my grandmas computer, is when you download a program, even from Synaptic, and you have "nothing". You have no icon, you have no point of reference to start this new program. You're just supposed to guess whatever console command starts this new program. And from my experience so far, that usually means the program is crap anyway, so I guess in that respect it saves me the hassle of having to run it.

I think this may be partially due to lack of standardization for package management/installation programs or scripts.  I think both sides are partially to blame here.  There should be (and very well MAY be) a clear API or system for "installing programs" including copying the files AND making menu items.  Quite simply, more software companies need to A) use the package management systems in place now OR B) help the standardization and progress of a universal interface for packages and package management systems.  Get the API in place, so that no matter what system the user is on, the software company can rest assured that it will install correctly using one standard and not have to worry about making a package for every system: DEBs, RPMs, and the rest.

> **keyboardashtray said:**
> A runner up for me is the filesystem. Wow. I hope the programmers are serious when they say it's a great system for them because from the user end it feels like a holdover from the days when computers were giant contraptions of tubes and wires in big air-conditioned rooms. 

I hate what I think of as the "Great Linux Lie", that "Well, it really doesn't matter that the file system is confusing because you don't need to go in to those files anyway". (Second to the "you really don't need to use the console in Linux anymore" only because everyone knows you need to use the console all the time.)

Whether it is finding a common system sound file to associate with an event in a program, picking an icon for a menu option, or (barring knowing the console command) finding the appropriate program icon for Firefox to associate a filetype with, the average user has plenty of digging around in poorly named directories to do, even on day one.

I also agree with you here and believe that everything should be made so that it can be completely dynamic (even though it is a little bit dynamic in some ways).  What I mean by that is, correct me if any Linux gurus are reading this, it seems that there have been battles over where things should go.  Do the library files go into /usr/lib, /var/lib, or /lib?  I've seen some installation scripts *check* to see where they are, so that they will be able to correctly install and configure the program.  Well, why should we make the software programmer do all the work?  Why not have one universal traffic director?  You want the system's library files for user space (if that's even applicable here), OK!  Look in this directory here!  If such a thing was created, you could put anything anywhere, wherever you wanted to, and then "designate" it as the place to go for the files for X.  One of the "cop-outs" I get is that Debian is "doing it wrong".  They chose a different directory structure than what was the standard.  Why did they do that?  No clue, but it's really too bad they didn't stick with the standards so I hope there was a good reason for doing so.  Doing so has only made things more difficult though for everyone I think.

I think it'd be nice to group all the system stuff in one place, all the programs in another, all the shared sounds and other media in another, and all the user files in another.  Then, just let the system know where everything is.  For the most part though, I don't think this is a *massive* issue, because I think most users really do rarely go digging around in their system stuff, but I agree that the shared media could be placed someplace with a naming scheme that's friendlier, but it is true that it wouldn't be *incredibly* difficult for them to remember /usr/share.

Like with trying to get these two huge groups of Linux users to conform to one package system, I think trying to change the directory structure by brute force is also probably out of the question, and believe the easiest solution would be to put something in the Linux Standard Base that allowed the package manager and rest of the system components to make the directory structure a moot point.  Then, for the users, maybe the answer simply lies in making the GUI make the "user-friendly" places be quickly accessible by default, and keep the system stuff buried by default (which is how things are now for the most part).  Then, solve the problem of ever needing to go digging into the system directories in the first place in every way you can, or make certain directories (like /user/shared/sounds) are quickly accessible?  Maybe make a Nautilus shortcut to sounds? ;)

I know all that may be "patching around the problem", so that's why I feel adding a system file locater thingy to the LSB may solve that problem by allowing the system to be changed around since it will no longer matter, just like I feel the solution to the package management issue is by making the package format be a moot point, allowing developers to use whichever package format they like the best.

---

### Post by Yfrwlf on 2007-10-31
> **New to Linux said:**
> As a new Ubuntu (and linux) user, I would have to say that there are a couple of  problems  that need to be addressed :

1. The ability to run a standard set of  linux commands
   - sh, rpm, etc 

Having to change ' sh' to 'bash' is one way to kill an application.

This would make it easier for manufacturers to distribute driver installation software. (such as printers and scanners)

2. Protect the operating system from hangs and crashes. 

Applications can fail, operating systems should not.

I'd never heard about that bash/sh thing, but I fully agree that installation should be standardized or that the system should always be able to deal with all forms of installation and package types (well at least all the major ones), then old bad methods can be phased out because they will have equal and direct competition with all the other installation methods.  Freedom, *and* competition and comparison, can't get much better than that. :)

The kernel has seemed to be pretty stable for me, but I have had X crash before while the kernel was still going.  Would definitely be good to put in better safeguards so that that won't happen, and in Xorg 7.3 there are some (additional, probably) graphics failsafes, which is good, but more crash failsafes would be nice too. :)  Ubuntu 7.10 seems pretty stable in general I think, though I haven't put it through a whole lot of tests.  If you want to you can enable SSH though so if your system does hang you can remote in to see if just X has crashed or something.

---

### Post by keyboardashtray on 2007-10-31
> **bruce89 said:**
> [http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)



The FHS has been around for a long time and will never change for good reason. Learn it.

Can you think of a better hierarchy?

I take it back - *this* is my biggest criticism of LInux - even in ol' "Linux for People" Ubuntu, you've still got the number one reason people are hesitant to give it a try - leet users that reinforce the love it or leave it attitude. 

Why not throw a RTFM out?

And as for me thinking of a better hierarchy, *changing* it wasn't my point. The focus should be on making it so the end user doesn't need to know what all of them are. Windows has a ton of system folders that I had no clue of - and I never needed to know. Program Files, and Documents. Thats it.

How many computer users do you think hang around an OS forum? You and I might be interested in learning the Unix file system, but the average computer user could give a rat's *** less. They want to come on their computer, browse the web, type their resume, and not have to worry about the guts of it.

---

### Post by Yfrwlf on 2007-10-31
> **bruce89 said:**
> [http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)



The FHS has been around for a long time and will never change for good reason. Learn it.

Can you think of a better hierarchy?

I'm fairly sure by their post that they know where the terminal is.  They are wanting to be able to not have to ever need to terminal, to have GUI options to do things that *general* Ubuntu users would want.  So far, I think Ubuntu has done an excellent job of not requiring terminal knowledge, and Gnome has done a pretty good job with the intuitiveness of their layout I think, but there's always room for improvement. :)

Telling him to learn it also isn't his point.  I believe he was trying to say that the layout of the directories isn't intuitive to the normal user.  It's a given that someone who knows Debian/Ubuntu will know where everything is, obviously, and maybe for developers and system admins and such it **is intuitive**, and hopefully normal users wouldn't need to access it anyway, but I do agree that the layout could be more intuitive for *everyone*.

Anyone here know enough about the Linux system to suggest a simpler naming scheme, one that doesn't involve 4 different lib directories for example, or do you all feel that those [COLOR="Red"]really really are needed[/COLOR]?  If so, why, and is there any better naming scheme that'd be simpler and more intuitive for all users to learn?  Or, what layout would be best for end users, and which for developers?  I agree that this issue is becoming more of a moot point, but still, it may need some cleaning.

Don't make people afraid to challenge the system and status quo, those kinds of things are needed for anything to grow. :)

---

### Post by Yfrwlf on 2007-10-31
> **keyboardashtray said:**
> I take it back - *this* is my biggest criticism of LInux - even in ol' "Linux for People" Ubuntu, you've still got the number one reason people are hesitant to give it a try - leet users that reinforce the love it or leave it attitude. 

Why not throw a RTFM out?

And as for me thinking of a better hierarchy, *changing* it wasn't my point. The focus should be on making it so the end user doesn't need to know what all of them are. Windows has a ton of system folders that I had no clue of - and I never needed to know. Program Files, and Documents. Thats it.

How many computer users do you think hang around an OS forum? You and I might be interested in learning the Unix file system, but the average computer user could give a rat's *** less. They want to come on their computer, browse the web, type their resume, and not have to worry about the guts of it.

Exactly, and the constructive way he could have worded his opinion could have been thusly: "I feel that the directory layout is in my best interest, because I'm a sys admin or developer or whatever it is that I am, and I cannot think of a better way to structure things, nor do I think it's possible to change things now since it's the way things have always been."  That would have been far more descriptive of his feelings, without being so anti-opinionated. Everyone should try to get along and make Linux the warmest community they can. ;)

I think in all fairness different types of users are interested in seeing and using different parts of the system, so creating a way for both users to be happy using the same system is something Ubuntu should always be interested in bringing to the table. :)

---

### Post by keyboardashtray on 2007-10-31
> **Yfrwlf said:**
> Fully agreed, these remaining problems need to be conquered and you should point out some specifics when you can so that they can be addressed.  Bugs and ideas for improvements can be submitted to Launchpad for consideration. Yeah, I'd have a hard time generalizing to them what I think needs to come off the console, I have a hard enough time griping here in a criticism thread without getting a RTFM thrown at me ;), I'm not sure my "nerf the console" cries would get much creedence with the Launchpad folks. I have more a series of troubleshooting exercises that it's bothered me that there wasn't a GUI equivalent, although I guess I could say it's miscellaneous settings, although that might be a little too broad.

Some things that come to mind, just recently one would be trying to fool around with ipv4, some internet settings that everyone was saying might be causing some slowness. It felt like there should be a toggle somewhere. When I was brand new, problems moving files around - gksudo nautilus I know isn't too hard, but I think by default a gksudo nautilus in administration would be nice, I named mine "File Control".

And one dealing with Launchpad itself, recently I filed a bug report for yelp, and while it is easy enough to file the initial report, following through got a bit technical. The directions provided to me were clear enough, but it was still a pretty complicated ordeal. First, digging into the etc/apt/sources list, adding new dbgsym of yelp, grabbing the debugger, more commands I don't know. I'm very appreciative they got back to me so quick and seemed interested in my bug, that for all I know only affects me. I just wonder if there couldn't be an easier way to zap bug info/backtrace over to them, that would maybe be more conducive to simple folk like myself providing feedback. I mean, I have this "Bug Reporting Tool". What does it do? For all I've seen, it just serves as a hyperlink to Launchpad. But, I'm pretty sure I saw that one of the goals over there is a plan for some general bug reporting system, so maybe it is in the works. 

I see this reaction from people "How hard is it to copy and paste commands into a terminal?" It isn't hard, but people give sudo this and chmod that advice at the drop of a hat - oftentimes when there is a simpler GUI method available. I suppose some people just like to demonstrate their skillz. And beggars can't be choosers, I'll take what I can get. But the challenge isn't the copying and pasting, it's knowing, or not knowing, what this is going to do to your system, and while a GUI method can simply be navigated to, giving many clues to the context of what you are doing, and to undo or change back, a lot of these console commands, as given, are a one-way street for all intents and purposes to the inexperienced user.

> **Yfrwlf said:**
>  What I mean by that is, correct me if any Linux gurus are reading this, it seems that there have been battles over where things should go.  Do the library files go into /usr/lib, /var/lib, or /lib?  I've seen some installation scripts *check* to see where they are, so that they will be able to correctly install and configure the program.  Well, why should we make the software programmer do all the work?  Why not have one universal traffic director?

Yeah, that gets me too. I was trying to figure out some stuff for Yelp and scrollkeeper, and there are three possibilities for the  conf file, OMF_DIR=/usr/share/omf, /usr/local/share/omf or /opt/gnome2/share/omf:/opt/kde/omf. Sadly this kind of thing seems like a divergence that will never be reconciled between distros. 

And as for the documents themselves, I could be wrong, but if you download a documentation package from the repos, I'm assuming it's supposed to integrate into your main help documentation right? I mean, why package it at all, if it is just an archive of html files? Well, I think it must be the directory structure again, apparently people have different ideas on where the shared documents should go. 

> **Yfrwlf said:**
>  Then, for the users, maybe the answer simply lies in making the GUI make the "user-friendly" places be quickly accessible by default, and keep the system stuff buried by default (which is how things are now for the most part).  Then, solve the problem of ever needing to go digging into the system directories in the first place in every way you can, or make certain directories (like /user/shared/sounds) are quickly accessible?  Maybe make a Nautilus shortcut to sounds? ;)

I agree - some running list that GNOME tallies of shared icons, systems sounds, etc., a general palette of those sorts of things. And maybe a running list of programs, with full names, a brief description, and specific icons. Right now, there is a very small list available by default in Main Menu, but any deeper than that and you're digging around /usr/bin, where mainstay applications are given as much prominence as every other two-letter name program.

---

### Post by keyboardashtray on 2007-10-31
> **Yfrwlf said:**
> Exactly, and the constructive way he could have worded his opinion could have been thusly: "I feel that the directory layout is in my best interest, because I'm a sys admin or developer or whatever it is that I am, and I cannot think of a better way to structure things, nor do I think it's possible to change things now since it's the way things have always been."  

Right, and for I'll I know he'd be right - I mean, it's the core assumption I'm working off of, that the programmers/sys admins like it, and it works really well for them. Somebody's gotta like it, right? :-k

Oh well, I guess I better go study my FHS.:rolleyes:

---

### Post by runningwithscissors on 2007-10-31
Why does Ubuntu Linux attract these manager types who have a full vision, mission and plan rolled out. Only the implementation must be handled by the unwashed masses of developers.

Lots of these problems are well known. They are being worked upon (apart from the command line complaints).

Projects like freedesktop.org are trying to bring some degree of standardisation between the major desktop environments.

Tech like HAL and dbus are looking to make hardware easier to work with.

Give it time.

---

### Post by tashmooclam on 2007-10-31
Maybe this isn't useful, but I would have liked a pdf file "user guide to ubuntu" on the disk, so I could read about the OS without being online all the time. Nothing too fancy. Maybe a glossary I could have printed out, the terminology was new.
I wish the wireless worked with those broadcom cards well. 
Otherwise, I am pleased as can be with Ubuntu overall.

---

### Post by Yfrwlf on 2007-10-31
> **runningwithscissors said:**
> Why does Ubuntu Linux attract these manager types who have a full vision, mission and plan rolled out. Only the implementation must be handled by the unwashed masses of developers.

Lots of these problems are well known. They are being worked upon (apart from the command line complaints).

Projects like freedesktop.org are trying to bring some degree of standardisation between the major desktop environments.

Tech like HAL and dbus are looking to make hardware easier to work with.

Give it time.

Yep, it's awesome, important, and good to talk about I think.  When I can drag and drop files from Nautilus, a GTK program, into Amarok, a QT program, that's when I bow down and kiss the penguin's footsies for all the standardization goodness that is IMO helping to save Linux and pull things together.  Let program/programming competition occur, but just try to use the same API or whatever. :)

Anyone know if there are standardized programming methods for making a GUI program for X, so that I could simply give a "make button" entry and it would make a KDE button in KDE, and a Gnome button in Gnome, or are programmers forced to make the program for one or the other?  I mean, it'd be really awesome if you could use the same method so that a program isn't exclusively using one library or the other but instead will use whichever one is appropriate?  I mean, ideally isn't that what you want, to have everything to do with the GUI using the same standard system, while the "backend" so-to-speak uses it's own separate system?  Yes, as you can tell I don't have any experience in this, but I am interested in what it'd take to program if I wanted to tinker with it. :)  I'm just curious where the standard X API programming ends and the GTK or QT-specific programming begins I guess, and I'm curious if it can be improved/standardized any so that writing programs for X is more efficient and easier.  Any developers reading this (if any are) happen to know?

---

### Post by Yfrwlf on 2007-10-31
> **tashmooclam said:**
> Maybe this isn't useful, but I would have liked a pdf file "user guide to ubuntu" on the disk, so I could read about the OS without being online all the time. Nothing too fancy. Maybe a glossary I could have printed out, the terminology was new.
I wish the wireless worked with those broadcom cards well. 
Otherwise, I am pleased as can be with Ubuntu overall.

I assume you checked the restricted driver manager?  A 7.10 install on a friend's laptop showed that there were Broadcom wireless drivers available in the restricted driver manager to make his wireless function.  Boy do I hate Broadcom. >.<  I think the easiest solution would be to get Intel wireless for when you do upgrade next, since they are much more open and supportive it seems.

---

### Post by professor fate on 2007-10-31
Is there a way to lock the menu bar down?  I occasionally move it by accident and it frustrates the hell out of me.  lol.  A lock down feature would be nice. Maybe it already exists?

---

### Post by kopinux on 2007-10-31
how about a downloadable GUI build-essential compiling tool, if there is a source code, tar.gz, or other format like rpm, you can easily convert them and compile using a GUI to a .deb ubuntu compatible format, or it already exist?

bug fixing, hardware compatibility, software ports, more softwares/games for add/remove programs, nothing the usual, for me ubuntu is perfect os out of the box.

---

### Post by keyboardashtray on 2007-11-01
> **professor fate said:**
> Is there a way to lock the menu bar down?  I occasionally move it by accident and it frustrates the hell out of me.  lol.  A lock down feature would be nice. Maybe it already exists?

Just right click it and check "Lock to Panel", unless you are referring to a whole panel bar itself, in which case I'm not sure - the only other suggestion I could give there is go under Mouse in preferences and adjust your Drag and Drop threshold.

---

### Post by igknighted on 2007-11-01
> **Kvark said:**
> I agree with BrendanM's points about the command line. But I don't think thats the only place with that problem, abbreviations in general are a pain. Just because someone is too lazy to write a whole word nobody has any clue what they wrote until they are told what the abbreviation means.

If I could remember my initial guesses the first time I saw a Unix like file system. Hm, it was something along these lines...
/dev = Development related stuff like that source code everyone are talking about.
/opt = Options, the configuration files I need to edit.
/usr = My user files.
/bin = The trash bin, luckily I didn't try emptying it when I saw how full it was.

When programming in C i always forget which random consonants from the full words where included in the (mis)spelling of function names. It would be a lot less painful if strncmp was compare_strings and strpbrk was find_character.

See, the "problem" is that linux is not written for the least common denominator.  Just because a new user isn't going to guess a command like rm doesn't mean they will guess "delete" either.  I sure as hell wouldn't enter a command I didn't know what did.  They would look it up, see its rm, and be on there way.

A nice little terminal guide on the install disk (preferably upon first launch of the terminal there could be a message that asks the user if they want to launch the tutorial to show them basic commands) there could be a reference.

But back to my point.  Linux is designed to be efficient.  Not for novices, but for those who know how to use it.  It takes some time to learn all that, yes.  But having the commands be rm, cp and mv makes my life as someone who knows the commands easier (less typing, smaller scripts, etc... not a great example, the difference is minimal here... but its a principle).  Same is true of more complex things like vi.  I find vi so very frustrating at times and hard to learn.  But the more I learn, the better I get.  And the better I get, the more I see that making the changes I wanted when I didn't know how to use it would have crippled the power of the application.

So no, I don't think that we should cripple linux in the name of "user friendliness".  Because it is not really user friendliness.  It is "newb friendliness".  And call me elitist if you want, but I'm not going to advocate a change in my operating system to help new users adjust at the expense of my work.  I'll sit down and teach them, I'll write tutorials, but learn the software as it should be.

---

### Post by aysiu on 2007-11-01
Mac OS X also has /dev, /usr, and /bin, but no one complains about those directory names because they don't have to see them in order to take advantage of their functionality.

Programs are written in code that most humans cannot make sense of, but no one complains because they don't have to see the code in order to use the programs.

Things under the hood should stay under the hood... unless you choose to lift the hood.

There are only two major reasons people complain about the directory naming/structure in Linux: [list][*]There are not graphical frontends for absolutely every task, so sometimes you have to manually edit configuration files. Those configuration files sometimes lie outside the /home directory[*]Sometimes installed programs do not include a .desktop file, so users don't see a launcher and thus want to find out "where" the program "lives" in order to launch it.[/list] The solution is not to rename the directories people need to see. The solution is to make sure people don't need to see those directories.

---

### Post by tashmooclam on 2007-11-01
I did get the firmware etc. and the broadcom wireless works.
This process was easy and I was very impressed by Ubuntu.
The fly in the ointment seems to be network manager (default program) doesn't handle the wep wireless so well. So, in my home, wireless works poorly, my router has wep. But, outside, it's pretty good, since the free "wifi hotspots" are not asking me to use a password to get their wireless. 
The "solution" people are using seems to be using Wicd instead of network manager. I'll give it a try, I'm just a little tired of fiddling around at the moment.
Someone suggested Ubuntu use Wicd instead of Network Manager by default in their distribution. 
In this process, I have learned about how many pieces make up a computer. 
In my previous life I owned an iMac and it was a good experience.
What's interesting is the whole process started for me because I cannot stand those little macbook shiny screens, so I got a PC laptop and I can't stand using Windows. Ubuntu saved the day.

---

### Post by professor fate on 2007-11-01
> **keyboardashtray said:**
> Just right click it and check "Lock to Panel", unless you are referring to a whole panel bar itself, in which case I'm not sure - the only only suggestion I could give there is go under Mouse in preferences and adjust your Drag and Drop threshold.

Yes, I meant the whole panel.

---

### Post by Yfrwlf on 2007-11-01
> **professor fate said:**
> Yes, I meant the whole panel.

Maybe that's a feature that should be suggested to Gnome or to Launchpad, sorta funny how you can lock buttons down to the panel but not the panel itself.  The thing is, you have to drag the panel pretty far in order to move it, so I've never had a problem with accidentally moving it, but my roomie did the other day go figure, not sure how though.

---

### Post by Yfrwlf on 2007-11-01
> **aysiu said:**
> The solution is not to rename the directories people need to see. The solution is to make sure people don't need to see those directories.

That's one solution, and I agree with it fully, and Ubuntu has gone a long long way to complete that goal, but it's more of a patch, because lets just say that you *could* change it...can you think of a way to actually structure things better, and to do it in such a way as to make things simpler for everybody?  I still think it'd be cool having some system thingy that you can ask where all the essential things are and which programs could ask too that could be made a standard, that way it may be possible to reorganize everything into a more intuitive layout for everyone if there is one AND not totally confuse everyone...maybe. :)

I'm not a developer, yet, so I don't know if things are organized in the best possible way.  Like I mentioned earlier, I was under the impression that there were several duplicate directories already due to disagreements with where things should go.  At the very least, if that's the case, maybe there's a solution to work that out.

---

### Post by aysiu on 2007-11-01
You don't make a TV's insides easy to understand for normal folks. You make the TV's *outsides* easy to understand for normal folks. You make the TV's insides easy to understand for *TV repair people*.

Same deal for cars, for clothing manufacturer, for medicine, for art, for anything that involves a producer and user/consumer.

The user/consumer doesn't have to understand everything going on under the surface. She doesn't have to know what all the car parts are under the hood (that's the car mechanic's job). She doesn't have to understand the chemical processes involved in creating drugs (that's the pharmacist's/scientist's job). She doesn't have to understand color theory or perspective in order to appreciate paintings (that's the artist's job).

It makes perfect sense for the producer to make the steps involved in production and operation easily understandable for other producers and to make the steps involved in using the produced item easily understandable for users and consumers. If producers are used to the "under the hood" stuff being a certain way, why change that to make it easier for consumers to understand, when they have no business with production any way?

The obvious solution is to make it so that consumers do, in fact, have no business messing with production and maintenance *unless they desire to learn those things*. Reorganizing the filesystem hierarchy is surgery when only a bandage is needed.

---

### Post by Yfrwlf on 2007-11-01
> **igknighted said:**
> So no, I don't think that we should cripple linux in the name of "user friendliness".  Because it is not really user friendliness.  It is "newb friendliness".  And call me elitist if you want, but I'm not going to advocate a change in my operating system to help new users adjust at the expense of my work.  I'll sit down and teach them, I'll write tutorials, but learn the software as it should be.

Give a few more ways for noobs to learn, it's a good idea yes and a quick fix.  You could do something as easy as make the terminal say "Type in "man tutorial" for help.", or you could add some help section for terminal beginners to the help section for the Gnome terminal that explains how to get around, etc.  Another thing that could be done though to get them up and going faster is to tell them when they start it about "man command".  That way, even if you didn't make a "copy" command that could say, after it was run, "Next time you can use cp instead of copy, it's faster.", you could make a bunch of bogus man pages that were just pointers to the real thing, so you could make a man page for "copy" that says "see 'cp' instead."  Or, you could do all of the above to make using the console a bit easier to learn, to advance, to grow, so that it's not such a jarring experience for those who want to learn it.  I mean, the user experience isn't one solution, *keep them out of the console*, but it could be several solutions that help to make the overall experience better.  Yes, keep them out of the console if you can, but if they either want OR need to use it, make it friendlier for them how about? :)

---

### Post by bruce89 on 2007-11-01
Have fun patching 22000 packages to use another hierarchy.

Any ideas on a hierarchy which would be better and why are welcome.

---

### Post by Yfrwlf on 2007-11-01
> **aysiu said:**
> Reorganizing the filesystem hierarchy is surgery when only a bandage is needed.

I agree with the keep end-users from having to know what's under the hood philosophy, Ubuntu is supposed to be easy that's the entire point, but maybe that surgery is needed to fix an old battle wound.  If it *were* needed, if there *was* a better way of structuring the directories, could it be done?  That's what we're asking, so as a developer if any developers are out there, as any kind of user period, does [COLOR="Red"]anyone out there[/COLOR] feel that there is a better way things could be rearranged?  Hypothetical discussion is good, I mean come on, just because you've learned things a harder way doesn't mean that it's completely impossible to change it all into a better way.  I don't mean to turn it into a conservatives vs. the liberals but that shouldn't be what it all comes down to, it should come down to "is there a better way or not". ;)

Anyone?  Aren't there too many duplicate library directories?  I mean, seriously??  Does it make things painful for developers?  I've had to set up symbolic links before so that certain programs can find the libraries they need, so is there an issue here or not?  If it's simply a matter of learning A = Apple and learning the structure, and it makes things really easy for developers and it really is a good system for them, then great, but is it really, and what about da nooblets?  Keep them all in /home? ;)

I don't mind where everything is myself because I've learned of course, but for noobs wanting to install new sounds and stuff, maybe there's a way to make things simpler, I dunno, anyone? :popcorn:

---

### Post by Yfrwlf on 2007-11-01
> **bruce89 said:**
> Have fun patching 22000 packages to use another hierarchy.

Any ideas on a hierarchy which would be better and why are welcome.

That's what scripts are for. :D  You're right though, it'd be a big change and would need to have a standard path identification mechanism be used, like instead of saying install to /lib/modules/ say install to {libmod} or whatever. :P  I mean, isn't this one thing that causes debian packages to be different from RPMs, since the directories are in different places.  I know there are more differences lollerskates, but if there was a universal system making it not matter, maybe it'd be one more step to bring together specific distro installation packages since they no longer have to worry about different directory hierarchies. ^^

Actually I'm really curious about RPMs and DEBs and why they need to be different formats instead of just using a standardized API for compatibility across the board with package management systems...but any way back on topic.

My only idea is to make the media (sounds, pics, etc) more upfront or something so that users don't need to find the /usr/share/sounds directory and such.  Maybe this just goes back to the userland vs. systemland battle?  Obviously you can't install Gnome and KDE sounds to /home, so there has to be someplace else for it, so maybe it's OK where it is, I really don't know what would be more helpful for end-users but simply to have things more accessible, but maybe the solution is to change Nautilus's places menu to include more locations.  In /home/user/Examples there are some media files, pictures and sounds and videos, so perhaps it'd be helpful if it was all in one place.  I mean, out of ALL the stuff in /usr/share which is quite lengthy, I think the sound directory may be the one that's wanted the most to normal users.

You can right click on the desktop to change the background, and are brought to /home/user/Pictures.  But, to change the sound effects, you have to go into Preferences > Sounds > 2nd tab over, and then if you choose to add a sound that isn't listed you are brought to /usr/share/sounds.  It just makes things kind of rough I think.  If all the media could be consolidated into one place for users to easily access everything, I think it'd be best.  Not a huge issue, not sure how it'd be done, but there's my 2 cents. ;)

---

### Post by Kymus on 2007-11-01
> **23meg said:**
> A longer release cycle doesn't necessarily mean more stability. As long as Ubuntu is to remain cutting edge and the workforce remains equal, expecting huge differences in release quality isn't realistic, since the work to be done remains equal regardless of the cycle length.

that's a real good point

---

### Post by Rhapsody on 2007-11-01
One that irritate me are that refresh rates, on CRT monitors anyway, always seem to require manual tweaking to get above 60Hz. I've lost count of the amount of times I've been forced to mess with xorg.conf.

The other is ALSA. A complete mess really, I'm really thinking it should be junked entirely in favour of the (now GPLed) Open Sound System.

I'm gradually finding ways around these problems, but I really shouldn't be having them.

---

### Post by Kymus on 2007-11-01
> **ATrentino said:**
> I was actually considering starting a group to lobby companies such as HP to start offering Ubuntu. Perhaps a few hundreds or thousands emails could help change things.

I think that's a good idea, but, companies will need assurance of profit. If we petition and lobby to holy hell, and then there are little sales (which I hear is a problem Dell has experienced), it won't do us much good :(

---

### Post by igknighted on 2007-11-01
> **Yfrwlf said:**
> Give a few more ways for noobs to learn, it's a good idea yes and a quick fix.  You could do something as easy as make the terminal say "Type in "man tutorial" for help.", or you could add some help section for terminal beginners to the help section for the Gnome terminal that explains how to get around, etc.  Another thing that could be done though to get them up and going faster is to tell them when they start it about "man command".  That way, even if you didn't make a "copy" command that could say, after it was run, "Next time you can use cp instead of copy, it's faster.", you could make a bunch of bogus man pages that were just pointers to the real thing, so you could make a man page for "copy" that says "see 'cp' instead."  Or, you could do all of the above to make using the console a bit easier to learn, to advance, to grow, so that it's not such a jarring experience for those who want to learn it.  I mean, the user experience isn't one solution, *keep them out of the console*, but it could be several solutions that help to make the overall experience better.  Yes, keep them out of the console if you can, but if they either want OR need to use it, make it friendlier for them how about? :)

But without doubt there are already programs called "copy" or "delete", so they would need to change.  And really, who's going to sit down at a terminal WITH NO CLUE WHAT THEY ARE DOING and start typing in "copy filename new/filename"?  No one.  They are going to either (a) whine that the terminal is scary, or (b) look it up.  Your solution really doesn't help anyone except the mid-level user who is competent on the terminal, but forget commands.  And to cover all the commands this user might need "friendlier" would require immense amounts of aliases, to the point where it makes more clutter then it helps.

Any easy-to-find quick reference would be far, far more efficient.  Give people a friendly manual and they will learn the right way.  If they refuse to look at a manual that was written for new users (note: not the cryptic man pages), then they have to consider whether or not switching to a new OS is for them.

---

### Post by Kymus on 2007-11-01
> **Dimitriid said:**
> Oh and for the love of anything you might hold sacred preinstalla better theme! The art department  really needs to step it up!

I agree. Though, 99% of the themes I've seen on gnome-look are friggan ugly :(

But it shouldn't be too hard to have a small list of *nice* preinstalled themes (doesn't even have to look that fancy... just not ugly! It should be an issue of what looks best to the user, not which one looks the least bit ugly)

---

### Post by igknighted on 2007-11-01
> **Rhapsody said:**
> One that irritate me are that refresh rates, on CRT monitors anyway, always seem to require manual tweaking to get above 60Hz. I've lost count of the amount of times I've been forced to mess with xorg.conf.

The other is ALSA. A complete mess really, I'm really thinking it should be junked entirely in favour of the (now GPLed) Open Sound System.

I'm gradually finding ways around these problems, but I really shouldn't be having them.

Pulse Audio is on the way... its available for Gutsy, check it out.

Also, your monitor refresh can be changed through a GUI in Gutsy as well.

---

### Post by Yfrwlf on 2007-11-01
> **Rhapsody said:**
> One that irritate me are that refresh rates, on CRT monitors anyway, always seem to require manual tweaking to get above 60Hz. I've lost count of the amount of times I've been forced to mess with xorg.conf.

The other is ALSA. A complete mess really, I'm really thinking it should be junked entirely in favour of the (now GPLed) Open Sound System.

I'm gradually finding ways around these problems, but I really shouldn't be having them.

Have you tried 7.10 yet with the new Screens and Graphics tool, and did it change anything?  Xorg 7.3 is supposed to have better monitor detection but it didn't make it into 7.10. :/

Well it's good that Open Sound System comes with Ubuntu so you can select that one then. :)  Are you talking about a mess from a developer's perspective, or have you had problems with ALSA from a user's perspective, or both?

---

### Post by Kymus on 2007-11-01
> **Tux Aubrey said:**
> I'm with those who actually think things are going really well, but I would love to see:

1) Linux Hardware Compatability Advisor - a Windows dohicky.exe downloadable from the web (or maybe as a virus!).   Just like the Vista Upgrade Advisor.  For everyone who is Linux-curious to get info on what will and won't work for them with Ubuntu (or any other distro).  

2) Better documentation - its so spreadout and much of it (How Tos, Wikis etc) is not maintained very well or is poorly written. Aysiu's site excepted.

3) Marketing - I appreciate what the M-Team has been doing but I would really like to be able download an up to date marketing pack when there is a new release - CD/DVD covers, presentations, sticker templates, Quick start guide etc.  Even the examples included with each new release are often labelled for earlier versions.  I also have a strong feeling that in someone's head there is a great viral marketing campaign for Ubuntu that would sweep the web and give Ubuntu another quantum leap in its user base. (If that person would now step forward and open their brain, it would be greatly appreciated.  I have my trepanning saw ready.)

I agree whole heartedly, especially with point #1. Hardware incompatibility (like in the case of my old Mobo which refused to install any linux distro :confused:) is one of my biggest fears in regards to upgrading and I think that the process of *making the switch* would be much better if people could know ahead of time if there was going to be turbulance. Maybe this would cut down on the *"omgz ubuntu doesn't support my XYZ3000HD123X card! Ubuntu suxorz! I'm going back to Microsoft!"* posts.... maybe...

---

### Post by Yfrwlf on 2007-11-01
> **igknighted said:**
> But without doubt there are already programs called "copy" or "delete", so they would need to change.  And really, who's going to sit down at a terminal WITH NO CLUE WHAT THEY ARE DOING and start typing in "copy filename new/filename"?  No one.  They are going to either (a) whine that the terminal is scary, or (b) look it up.  Your solution really doesn't help anyone except the mid-level user who is competent on the terminal, but forget commands.  And to cover all the commands this user might need "friendlier" would require immense amounts of aliases, to the point where it makes more clutter then it helps.

Any easy-to-find quick reference would be far, far more efficient.  Give people a friendly manual and they will learn the right way.  If they refuse to look at a manual that was written for new users (note: not the cryptic man pages), then they have to consider whether or not switching to a new OS is for them.

Agreed that it'd probably be a better solution.  I'd guess there are no "learning to use the command line" manuals in Ubuntu by default, but I'm sure there are some online.  Perhaps one can be copied or and included in the help section.

Granted, a learning the command line tutorial really isn't Ubuntu's main focus, but maybe it's a document that could be downloaded automatically if it's too big for the CD and a user is interested in it or other advanced system configuration topics.

Or, it could be really small and simple, with just the most basic commands to navigate.  Sudo, cp, mv, cd, <TAB>, rm, rmdir, etc.  Is there a way to make the prompt spit out a welcome message even after loading up a terminal program from within a login?  I know fresh logins do, but what about a, what do you call them, child login?  Those don't give the welcome message, or if they do they are suppressed.  If that might be annoying to some users though perhaps just a menu entry under Help would be better, or the Help page simply expanded upon.

---

### Post by Yfrwlf on 2007-11-01
> **Kymus said:**
> I agree. Though, 99% of the themes I've seen on gnome-look are friggan ugly :(

But it shouldn't be too hard to have a small list of *nice* preinstalled themes (doesn't even have to look that fancy... just not ugly! It should be an issue of what looks best to the user, not which one looks the least bit ugly)

Perhaps it's an issue of space on the CD though?  What if the DVD got more attention and was advertised to come with a lot more themes and programs by default?  Also, I know many users don't use torrent programs, but I think the torrent should be more prominent to ease server loads and it may be needed if the DVD version starts getting lots of attention.

But any way, you only have two themes for the hard-of-seeing, one brown theme, a few blue, and one purple theme to choose from.  Perhaps there should be a poll set up to vote on the nicest themes from Gnome-look or other sites for inclusion in the next Ubuntu release? :)

---

### Post by Kymus on 2007-11-01
> **Yfrwlf said:**
> **Part 1**: What are your gripes about Linux/Ubuntu currently and what do you suggest as a fix for them?

Failsafe options so I'm not virtually screwed if I accidentally mess something up (like I've done with X, trying to manually configure my mouse). Given, one can boot to a live CD or a different partition (if there is a dual boot present) and try to search the forum or post a help topic, but this shouldn't be necessary. My biggest - and virtually only - gripe thus far is with how X can be touchy and can get all screwy if you do the wrong thing. 

From what I understand of Bullet Proof X, this may be a partial fix. Essentially, I'd like to see methods enabled so that one is never locked out of their desktop. Given, you can boot to the terminal to fix things, but that's not gonna help me all too much (given, it's better than nothing (windoze)) when I don't understand all the ins and outs of it yet.

---

### Post by Yfrwlf on 2007-11-01
> **Kymus said:**
> I agree whole heartedly, especially with point #1. Hardware incompatibility (like in the case of my old Mobo which refused to install any linux distro :confused:) is one of my biggest fears in regards to upgrading and I think that the process of *making the switch* would be much better if people could know ahead of time if there was going to be turbulance. Maybe this would cut down on the *"omgz ubuntu doesn't support my XYZ3000HD123X card! Ubuntu suxorz! I'm going back to Microsoft!"* posts.... maybe...

I want a XYZ3000HD123X card, it sounds sweet.  I think it needs more X's and HD's though to raise the coolness factor.

I also agree that the Doohickey project is awesome, and spreading the knowledge about what hardware you need in order to get Linux/Ubuntu is really important, not only to give people interested in Linux a great *single* knowledge source for that (instead of looking around in Google, trying to find out if anyone has had any problems with X hardware), but also in order to say more loudly "hey, hardware manufacturers, you might want to consider Linux support", because user N00b732 just chose brand Y instead of your brand.

---

### Post by Yfrwlf on 2007-11-01
> **Kymus said:**
> Failsafe options so I'm not virtually screwed if I accidentally mess something up (like I've done with X, trying to manually configure my mouse). Given, one can boot to a live CD or a different partition (if there is a dual boot present) and try to search the forum or post a help topic, but this shouldn't be necessary. My biggest - and virtually only - gripe thus far is with how X can be touchy and can get all screwy if you do the wrong thing. 

From what I understand of Bullet Proof X, this may be a partial fix. Essentially, I'd like to see methods enabled so that one is never locked out of their desktop. Given, you can boot to the terminal to fix things, but that's not gonna help me all too much (given, it's better than nothing (windoze)) when I don't understand all the ins and outs of it yet.

I think BulletProofX may actually be the entire solution, it's point is to make it so you can always recover your desktop, but it's new and still doesn't always catch problems yet.  Hopefully that will change, and you may be able to help if you submit any problems you've had with it.

Just FYI though in the meantime, if you're ever hit with a X server failed to load blue/white error, hit CTRL-ALT-F2 to get to a terminal so you can edit xorg.conf using your favorite console text editor like vi, vim, nano, etc. :)  Or, copy a functional xorg.conf back over it.

Actually, this brings me to another suggestion, why shouldn't Ubuntu make a copy of a functional xorg.conf file the first time the user boots into their system successfully, or simply of the initial xorg.conf, so that the absolute last failsafe, if they need it, is to replace xorg.conf back with the original one?  Maybe it's not needed, since most modification scripts of xorg.conf make their own backup, but for BulletProofX to use perhaps it'd help to have something like that?

---

### Post by runningwithscissors on 2007-11-02
> **Yfrwlf said:**
> Anyone know if there are standardized programming methods for making a GUI program for X, so that I could simply give a "make button" entry and it would make a KDE button in KDE, and a Gnome button in Gnome, or are programmers forced to make the program for one or the other?That is a very good idea, and I think we will move towards that in the future, in one way or another. Markup based GUI forms are already being used by both Qt and GTK. All you need to do is develop a common markup (which would have been done by now really, if XForms had really taken off). But I am certain some convergence of the techniques used to develop web and desktop interfaces will occur in the future, and you will be able to specify a "button" or any other form element and it will be appropriately drawn by any toolkit/browser that supports that markup. Microsoft is already there with XAML, in fact.

> **Yfrwlf said:**
> I mean, it'd be really awesome if you could use the same method so that a program isn't exclusively using one library or the other but instead will use whichever one is appropriate?  I mean, ideally isn't that what you want, to have everything to do with the GUI using the same standard system, while the "backend" so-to-speak uses it's own separate system?  Yes, as you can tell I don't have any experience in this, but I am interested in what it'd take to program if I wanted to tinker with it. :)  I'm just curious where the standard X API programming ends and the GTK or QT-specific programming begins I guess, and I'm curious if it can be improved/standardized any so that writing programs for X is more efficient and easier.  Any developers reading this (if any are) happen to know?
This actually has very little to do with X. When you program with GTK or Qt, you don't have to bother about what X is doing at all. Similarly, I suppose another layer of abstraction will be slapped on which will allow you to write GUI code that will work flawlessly on a bunch of toolkits and inside browsers as well. So you wouldn't have to worry about what toolkit is being used to draw the GUI.

---

### Post by bigboy_pdb on 2007-11-02
> **Yfrwlf said:**
> 
I agree for the most part that the GUI can be a *quick* learning tool especially in the cases where the program is so powerful that the range of things it can do is huge, but the program is really only normally used to do a few things.  The GUI often will present those few things first, while the man page may bury them and may make things much more confusing when what the user wants to do is simple.  This is sometimes more of a problem in how the man page was constructed though I think.  The only somewhat valid argument against it I think is that users still should learn things and Linux sometimes really makes you learn it and learn it fast, and that's good in a way, but for the normal user who just wants it to work they shouldn't have to, only if they *want* to.  There should always be ways to learn more about certain programs, and that's usually what the command line provides. :)


I think you misunderstood my last point.

Assume that you tell someone who is completely new to Linux to run a program on the command line. Even if the person frequently uses a Windows command line, it is likely that all the person knows how to do is run that one command with the options specified because the individual cannot access help for the command granted that the windows method for getting help for a command is "*command* /?" and the Linux method is "*command* --help". Also, the person will not be aware of the "man", "info", and "apropos" commands. Furthermore, even if the person is told about the "--help" option, the "man" command, or the "info" command, there is a good chance that he/she will be unaware of how to interpret the output of those commands. It should also be noted that a user with no knowledge of command lines will be worse off.

With a program that has a front end GUI, the person can see what options are available. The person can also see "Help" in the file menu and use it if need be. In other words, program usage is more obvious with GUIs and help options are visible.

Even when a person uses the command line frequently, if that individual needs to use a program that he/she is unfamiliar with then he/she might attempt to use options that cannot be used together and the individual might wonder why the program is failing. Another problem is that he/she might read the manual correctly, but he/she might be unaware of other potential problems. For example, the manual for "expr" states the following:
```

( EXPRESSION )
              value of EXPRESSION

```
A person might assume that 'expr ( 6 - 5 ) + 3' should print '4'; however, the program displays an error. The reason it prints an error is because the brackets are used to execute "6 - 5" (which is not really a command) in a separate shell. To fix this problem the user would need to add quotes around the brackets, making the expression 'expr "(" 6 - 5 ")" + 3'. Problems such as these are not likely to occur with most GUI programs.

---

### Post by boast on 2007-11-02
For making it easier on the noobs, a "welcome wizard" for fresh installs. It lets you setup accounts, setup network/wireless, enable/disable compiz or any fancy visuals, claim if any HP printer will be used, if any bluetooth will be used, etc...

This was only selected applications will be set to startup. Those without bluetooth utilitie's won't see any apps or startup services for bluetooth..

*shrug*

---

### Post by bigboy_pdb on 2007-11-02
An "Undo Changes" button beside the "Close" button in "Preferences" windows.

---

### Post by Rhapsody on 2007-11-02
> **igknighted said:**
> Pulse Audio is on the way... its available for Gutsy, check it out.
My problem is actually almost entirely solved now. My sound card is cooperating now that I've set everything to Open Sound System, but I get noting with ALSA for whatever reason.

Still, it was entirely or nearly entirely broken for almost a year, which is pretty bad.

> **igknighted said:**
> Also, your monitor refresh can be changed through a GUI in Gutsy as well.
Correction, my monitor refresh *should* be changable through a GUI in Gutsy. As it was, the monitor defaulted to 60Hz, KControl said I was already at 85Hz, and gave no other possible refresh rates.

I have managed to get 85Hz now, but that required going to the terminal and using a configuration utility that asked questions that would've terrified many users (do many people know what horizontal sync is?).

My advice to new Linux users with a CRT is to save up and buy a decent LCD panel. For anyone who needs 85Hz or more on a CRT to avoid eyestrain (like me), Linux can be a real nightmare.

---

### Post by indigoshift on 2007-11-02
My only complaint is that I'd like to be able to remove some bundled programs without getting a prompt that says I also have to remove ubuntu-desktop.

I've given up Totem for VLC media player, but can't free up the HD space by uninstalling Totem, for example.  It's a minor annoyance, but it's there.

---

### Post by Yfrwlf on 2007-11-02
> **bigboy_pdb said:**
> Problems such as these are not likely to occur with most GUI programs.

Yes, there are several ways that GUIs make things easier for non-command-line users, no doubt about it, and you point out some good reasons.  I was just pointing out that another one is simplicity, that sometimes the GUI will have the options that are more common either be the only options that exist, or they will be more pronounced, while the lesser-known things will either be non-existent or a little bit buried.  Sometimes if a user does a --help on the command line, they are given a massive list of options when the option they are looking for are the most common, simple ones, so it may be more confusing.

---

### Post by Yfrwlf on 2007-11-02
> **indigoshift said:**
> My only complaint is that I'd like to be able to remove some bundled programs without getting a prompt that says I also have to remove ubuntu-desktop.

I've given up Totem for VLC media player, but can't free up the HD space by uninstalling Totem, for example.  It's a minor annoyance, but it's there.

Annoys me too, and it's just because the metapackage ubuntu-desktop contains those packages.  So I'm wondering, does it need to be that way, or are these packages not modular enough that removing them will screw up the system?  It may be tempting for Ubuntu developers to tie different programs in together, but what they need to do is help to make things modular, everything should be! :)  Perhaps it could make things easier in the short run, but in the long run the system will have to have more work done to it in order to upgrade components if the components are too tweaked themselves perhaps, and it just makes it all more of a mess.  If they helped everything use standardized APIs though, then everything can be quickly disassembled in any way, and alternate programs can be installed in their places, and the Ubuntu packages that make Ubuntu cool could be used in *other distros*, which contributes much more smoothly to the Linux community as a whole and gives users much more freedom and creates much more competition and interoperability between distros.

In fact, IMO, I feel one threat Linux users should be aware of is standardization being removed from distros to make the distro more "locked down" by preventing modularity.  It's distro lock-in, basically, and it really hasn't happened yet too badly, but I think things should be pushing in the opposite direction, making everything so modular that I could install any of the cool Ubuntu components in, say, Fedora.  My dream is to see a Linux that is completely modular so that *all* a distro is is a certain set of packages, and the default configurations may be tweaked a little differently.  Ubuntu has it's Ubuntu desktop theme?  That's a simple desktop theme package.  Ubuntu has Upstart, Ubuntu has Compiz Fusion by default...all should be packages that I can install on any distro.  Things need to be modular so that ALL Linux communities can be working together and using each other's progress in Linux development, not segregated by the distro they happen to have chosen.  Yes, I know you can compile/install and run random programs, but then comes the chance that it breaks your system or something, I mean, I really really don't want to see Linux get to the point where end-users are totally reliant on their distro-rollers to provide them packages because everything is too customized and such.  That's not putting freedom at the forefront, and it will not help Linux progress as fast as if things were cross-distro and allowed more freedom.

Did that make anyone's bladder full to bursting and prostates weak? :P  (sorry, Kung Pow reference)

Any way, I think using aptitude you may be able to force single packages to be removed, but it doesn't look like Synaptic can do that.

---

### Post by keyboardashtray on 2007-11-02
> **boast said:**
> For making it easier on the noobs, a "welcome wizard" for fresh installs. It lets you setup accounts, setup network/wireless, enable/disable compiz or any fancy visuals, claim if any HP printer will be used, if any bluetooth will be used, etc...

This was only selected applications will be set to startup. Those without bluetooth utilitie's won't see any apps or startup services for bluetooth..

*shrug*

Definitely - play on GNOME's strengths and have a simple 'druid' ;) walk through some stuff. An early implementation could simply help determine what options are default on the menu (and close with an "at anytime, you can enable them again with Main Menu") so that there are less redundancies to distract you from a given option. 

A more developed version could set up printers, network, etc.

Can I just add, since you mentioned Bluetooth and startup services, that one of my major pet peeves with Windows was startup programs hogging resources or for all I know sending my browsing habits to Redmond. And there was never any description for what these were doing. Your best bet was to run Spybot and look through the system startup tab, hope the Spybot description was accurate, disable it, then cross your fingers on restart that you weren't going to have to go into a safe mode boot.

Well, I see the Services page with Ubuntu, and nice little checkboxes with nice little description fields under them, and half of the fields are blank. C'mon, they've come so far to write or implement some little daemon, etc., can't they take that last 15 seconds to type at least a one line description of what it does so I can at least have a more educated guess on if it is safe to disable or not? Is one of those power managements for laptops? Is one for desktops? It would project a more polished image, and another line of info or tooltip can't hurt anyone.

---

### Post by pt123 on 2007-11-02
Proper support for the mouse scroll wheel. 

Like Windows there should be an option to set number of lines scrolled by the mouse wheel. 

It is ridiculous that something simple and ergonomic as scrolling isn't properly supported in Linux.

This is one prime example why Linux isn't suited for desktops.
Most of the companies funding it are interested in the server side functionality.

---

### Post by Matakoo on 2007-11-02
> **pt123 said:**
> Proper support for the mouse scroll wheel. 

Like Windows there should be an option to set number of lines scrolled by the mouse wheel. 

Are you pulling our legs or something? At least in KDE that is a no-brainer to configure (it's available where you'd expect it to be...Control Center, Peripherals, Mouse), and I would be very surprised if Gnome doesn't allow you to change that.

---

### Post by Yfrwlf on 2007-11-02
> **runningwithscissors said:**
> That is a very good idea, and I think we will move towards that in the future, in one way or another. Markup based GUI forms are already being used by both Qt and GTK. All you need to do is develop a common markup (which would have been done by now really, if XForms had really taken off). But I am certain some convergence of the techniques used to develop web and desktop interfaces will occur in the future, and you will be able to specify a "button" or any other form element and it will be appropriately drawn by any toolkit/browser that supports that markup. Microsoft is already there with XAML, in fact.

So XForms is dead, surpassed by something else, or is the problem that XForms simply hasn't been adopted yet really?  I wonder if there's much discussion about it in the FreeDesktop.org groups.  That's where I assume discussion is needed the most, as well as on the Gnome, KDE, and other desktop enviro sites.

> **runningwithscissors said:**
> This actually has very little to do with X. When you program with GTK or Qt, you don't have to bother about what X is doing at all. Similarly, I suppose another layer of abstraction will be slapped on which will allow you to write GUI code that will work flawlessly on a bunch of toolkits and inside browsers as well. So you wouldn't have to worry about what toolkit is being used to draw the GUI.

That would be ideal!  Imagine using Amarok in Gnome with LITTLE LOADING TIME! ;)

---

### Post by pt123 on 2007-11-02
> **Matakoo said:**
> Are you pulling our legs or something? At least in KDE that is a no-brainer to configure (it's available where you'd expect it to be...Control Center, Peripherals, Mouse), and I would be very surprised if Gnome doesn't allow you to change that.

Not in Gnome, when KDE4 arrives I can't wait to dump Gnome, maybe then I might even suggest Ubuntu to other people.

---

### Post by Yfrwlf on 2007-11-02
> **Matakoo said:**
> Are you pulling our legs or something? At least in KDE that is a no-brainer to configure (it's available where you'd expect it to be...Control Center, Peripherals, Mouse), and I would be very surprised if Gnome doesn't allow you to change that.

Nope, Gnome doesn't have anything like that.  Two things Gnome needs in the Mouse section IMO:

1.  Scroll wheel click distance, like the poster mentioned.
2.  Speed!  Unless "sensitivity" is supposed to be the same thing as speed, i.e. the mouse cursor moves farther or shorter than you move the mouse, but all I know is sensitivity does not work with my mouse, I see no difference, and my mouse is pretty common.  (Even though it is a Mickeysoft one.) :P

But alas, we all know Gnome's motto: simplicity.  Which translates into "lack of any features that are not commonly needed/used".  I wish they'd change this philosophy into "put the normal, common settings up front, bury the 'advanced' or uncommon settings".

---

### Post by pt123 on 2007-11-02
> **Yfrwlf said:**
>  Which translates into "lack of any features that are not commonly needed/used".  I wish they'd change this philosophy into "put the normal, common settings up front, bury the 'advanced' or uncommon settings".

This is the problem with Linux, the distribution is at the mercy of individual developers. 

The only way to get around this mess is by using products from professional developers like Mozilla (i.e. Firefox) that have the resources and ability to understand user expectations, and allow the user to circumvent limitations of the window manager. i.e. in this case a feature to set number of scroll lines.

I not sure if this still the case but the screensavers that came with Gnome in Ubuntu 6.04? was limited because you couldn't configure the individual screensaver. For eg. the slideshow screensaver you could not specify which folder to get the images from.  The developer refused to add it this.

---

### Post by Matakoo on 2007-11-02
> **Yfrwlf said:**
> 
But alas, we all know Gnome's motto: simplicity.  Which translates into "lack of any features that are not commonly needed/used".  I wish they'd change this philosophy into "put the normal, common settings up front, bury the 'advanced' or uncommon settings".

Yeah, I know of that motto but I honestly didn't think they had taken it quite THAT far. Sure, making simplicity a priority is not wrong but this is what I at least would consider waaay over the top and giving the average computer user far too little credit. The ability to change that particular setting is, IMO, a BASIC necessity. Rather makes me even more happy that I've decided to stick with KDE and KDE applications really. 

Okay, right now I'm using Evolution, gLabels, and Firefox but I am seriously trying to find good KDE/Qt replacements of those three. Not only because of Gnome's serious case of over-simplicity though, but I rather like having a consistent computer experience.

---

### Post by Yfrwlf on 2007-11-03
> **pt123 said:**
> This is the problem with Linux, the distribution is at the mercy of individual developers. 

The only way to get around this mess is by using products from professional developers like Mozilla (i.e. Firefox) that have the resources and ability to understand user expectations, and allow the user to circumvent limitations of the window manager. i.e. in this case a feature to set number of scroll lines.

I not sure if this still the case but the screensavers that came with Gnome in Ubuntu 6.04? was limited because you couldn't configure the individual screensaver. For eg. the slideshow screensaver you could not specify which folder to get the images from.  The developer refused to add it this.

Well as long as everything is kept modular and standardized enough, you should be able to go out and get the stock program with stock configurations, or get a certain distro that has the default configuration that you like.  Keep everything inter-operable and you give the users much more power to choose.  For example, if Gnome was completely modular (and parts certainly are) and you could install a package/extension/plugin that made a screen saver preferences section then everyone who wanted the extra options could have it, and those who didn't could not have it.  Then, everyone would be happy.

Modularity = freedom of choice.

And no, Gnome still doesn't have a screen saver preferences section, though I swear at one point it did, but maybe KDE and Gnome are meshing together in my brain. :)

---

### Post by pt123 on 2007-11-03
> **Yfrwlf said:**
> Well as long as everything is kept modular and standardized enough, you should be able to go out and get the stock program with stock configurations, or get a certain distro that has the default configuration that you like.  Keep everything inter-operable and you give the users much more power to choose.  For example, if Gnome was completely modular (and parts certainly are) and you could install a package/extension/plugin that made a screen saver preferences section then everyone who wanted the extra options could have it, and those who didn't could not have it.  Then, everyone would be happy.

Modularity = freedom of choice.

And no, Gnome still doesn't have a screen saver preferences section, though I swear at one point it did, but maybe KDE and Gnome are meshing together in my brain. :)

But the problem is you need modularity within the application to make significant changes. This is usually doesn't exist and most of the changes done by distributions are topical.
Then in regards to modularity of applications you end up with many applications but not one that is fully featured. Because in those apps. when the lead developer loses interest, the application stagnates. Just look at  the Gnome music  players, you have Rhythmbox, Exaile, Quadlibet, Banshee, gMusic Browser. They are good but nothing like Amarok. You really need to have a community of developers and this requires support from one or more major distribution.

Look at gFTP it is nowhere near any of the FTP clients available on Windows Machines. Thankfully Filezilla has decided to port their application to Linux.

---

### Post by 23meg on 2007-11-03
[QUOTE=Yfrwlf]Anyone know if there are standardized programming methods for making a GUI program for X, so that I could simply give a "make button" entry and it would make a KDE button in KDE, and a Gnome button in Gnome, or are programmers forced to make the program for one or the other?[/QUOTE]

[http://www.wxwidgets.org/](http://www.wxwidgets.org/)

Its scope goes way beyond KDE and GNOME.

---

### Post by capink on 2007-11-03
On the subject the filesystem hierarchy. I would like someone with more knowledge answer my question.
can we have a more intuitive way to present the filesystem to new users without actually changing the fsh?

 My knowledge of programming is very limited - only bash scripts assuming that it can be called programming - but I think using virtual folders via something like gnome-vfs or kioslaves we can present the filesystem to the user in a more intuitive way without messing with fsh.

For example the user can type Settings:/// in the location bar and that will take him to virtual folder conatining all the config files in the same way typing fonts:/// is currently working.

Maybe also make it possible for vfs layer to contact the package manager and inquire about files belonging to a certain package (e.g. dpkg --listfiles packagename), so that if the user typed programname:/// it would take him to virtual folder containing all the files belonging to this program an so on.

---

### Post by bibas on 2007-11-03
Installig softwares in computers without an internet connection (coz it wont support my ISDN) is real pain. and the installer name dont make any sense. 
Also the 'dependencies'...gets on my nerves when a software  keeps asking one after another..........why cant they just make a package to satisfy all those dependencies.
Its scares you from ubuntu when internet doesnt work aswell.

---

### Post by Yfrwlf on 2007-11-04
> **pt123 said:**
> But the problem is you need modularity within the application to make significant changes. This is usually doesn't exist and most of the changes done by distributions are topical.
Then in regards to modularity of applications you end up with many applications but not one that is fully featured. Because in those apps. when the lead developer loses interest, the application stagnates. Just look at  the Gnome music  players, you have Rhythmbox, Exaile, Quadlibet, Banshee, gMusic Browser. They are good but nothing like Amarok. You really need to have a community of developers and this requires support from one or more major distribution.

Thankfully, if I'm right, it feels like there is more of a push toward plugins/extensions/modularity in programs and it's the new thing, because people realize that it makes the program so much more powerful.  Makes it as bloated as your needs desire it to be, and gives users more freedom in general.  Lets hope things keep moving in that direction. :)

> **pt123 said:**
> Look at gFTP it is nowhere near any of the FTP clients available on Windows Machines. Thankfully Filezilla has decided to port their application to Linux.

Filezilla ownz! :biggrin:

---

### Post by Yfrwlf on 2007-11-04
> **23meg said:**
> [http://www.wxwidgets.org/](http://www.wxwidgets.org/)

Its scope goes way beyond KDE and GNOME.

Very cool, thank you, will look into it. :)

Higher-level languages are becoming more popular, since you can leave the really greasy assembly-level code to the tech gurus, and have your average programmer finish off the project in a higher-level language that doesn't take as much brainpower and that isn't as complicated.  Is this a trend that will one day see the rise of extremely "user"-oriented programming languages where you simply tell the computer "put a box here, have it do this and this, place this object here that does such and such..." and it will do most of the work for you.

After all, computers love computing, that's what they're there for, to do the hard work. ;)  At least, for the normal computer user they do.

OK, I take that back, the average computer user barely makes their computer flinch, but you know what I meant. :P

---

### Post by Sawta on 2007-11-04
It would be nice if more people could revise some of the guides on how to fix hardware specific problems; I've had to only deal with getting the sound to work on my iMac, but I'm sure that other Desktops have to deal with other minor problems as well.

I feel that if some of these things were edited to be a tad more informative within the  first few posts, and possibly stickied, it could really help out newer people.  Of course, this is more of a message board thing, it would still be a very nice improvement.

Heck, I feel like listing this suggestion would actually help out future updates, since the forums them selves seem to be so integral to keeping your system up and running after muffing up an rm command :P *shudder*

Oh, I've heard that there's some kind of issue with DVD's.  Being very new to the system, I haven't run into any problems, but it would be nice if I don't HAVE TO run into any problems playing movies some time in the future!:lolflag:

---

### Post by perce on 2007-11-04
> **capink said:**
> 
For example the user can type Settings:/// in the location bar and that will take him to virtual folder containing all the config files in the same way typing fonts:/// is currently working.


You could make a symbolic link from /etc to a directory called Settings; however I don't see how a user who doesn't even know what /etc is 
could get any advantage from messing up with config files.

> 
Maybe also make it possible for vfs layer to contact the package manager and inquire about files belonging to a certain package (e.g. dpkg --listfiles packagename), so that if the user typed programname:/// it would take him to virtual folder containing all the files belonging to this program an so on.

Something like this is done by command line with the command apt-file; you're essentially asking for a GUI for apt-file in the same way as synaptic is a GUI for apt-get. That would be cool.

---

### Post by Yfrwlf on 2007-11-04
> **capink said:**
> On the subject the filesystem hierarchy. I would like someone with more knowledge answer my question.
can we have a more intuitive way to present the filesystem to new users without actually changing the fsh?

 My knowledge of programming is very limited - only bash scripts assuming that it can be called programming - but I think using virtual folders via something like gnome-vfs or kioslaves we can present the filesystem to the user in a more intuitive way without messing with fsh.

For example the user can type Settings:/// in the location bar and that will take him to virtual folder conatining all the config files in the same way typing fonts:/// is currently working.

Maybe also make it possible for vfs layer to contact the package manager and inquire about files belonging to a certain package (e.g. dpkg --listfiles packagename), so that if the user typed programname:/// it would take him to virtual folder containing all the files belonging to this program an so on.

Awesome idea, the Nautilus "virtual folders" that the user can go to like Computer and such are one way that the file system could be presented to end-users in a nicer way, like you say, if there are any folders/files that the user needs to access that aren't in their home directory as well.  I think Nautilus needs several new plugins for it, really.  If they are made as simple plugins, the Gnome devs don't have to complain about having too much clutter, and Ubuntu and/or users can add them in if they like them or take them out if they don't, AND it makes it so much easier for Ubuntu devs to update Gnome for new versions of Ubuntu. :)

---

### Post by Yfrwlf on 2007-11-04
> **capink said:**
> Maybe also make it possible for vfs layer to contact the package manager and inquire about files belonging to a certain package (e.g. dpkg --listfiles packagename), so that if the user typed programname:/// it would take him to virtual folder containing all the files belonging to this program an so on.

Actually, Synaptic already lists the installed files for a package in the package properties, so that would be the solution for what you need, right?  I mean, Add/Remove doesn't really need it because everything there installs a menu item, while Synaptic installs those plus libraries and command line programs, so if you can't guess the name of a command line program, since you're already in Synaptic, you can look at it's properties.  If you install from command line, you can just use apt-file like perce mentioned.

---

### Post by capink on 2007-11-04
> **Yfrwlf said:**
> Actually, Synaptic already lists the installed files for a package in the package properties, so that would be the solution for what you need, right?  I mean, Add/Remove doesn't really need it because everything there installs a menu item, while Synaptic installs those plus libraries and command line programs, so if you can't guess the name of a command line program, since you're already in Synaptic, you can look at it's properties.  If you install from command line, you can just use apt-file like perce mentioned.

I know that synaptic provide this. I am actually quite happy with the linux filesystem hierarchy. It is a lot better than anything I have seen. This why I am interested in virtual folders, as  it can present the filesystem to the user in many different ways without actually changing the filesystem.

I see a lot of people complaining that there are no program files folder like in windows. And I think virtual folders would allow different distros to present the filesystem in their own way without breaking compatibility with unix filesystem. And it adds to the linux flexibility. You can make linux look exactly like windows, not because windows way of doing things are better, but because linux flexibility allows for the user to make the system the way he likes. As for me, I am happy with my linux filesystem and don't want any change to it just to replicate another OS.

---

### Post by SpinningAround on 2007-12-10
First:
I enjoy a lot of things in Linux, it's free that is a major thing if you compare it to other OS around, I don't think the developers receive enough credit for this. It's also more secure the windows and feels a little more effective then windows and not to forget is all the free programs that is around.

To the Criticism:
1.
The first thing that indirect effect most experience users as I see it, is the lack of standard in Linux for home users. For bushinesses and similar do Fedora exist that bring some help to the standard for them i guess, but I haven't tried it so unsure about it.

When I say indirect is that if I think that company's that create programs and hardware can have problem with creating this for Linux since if you look at it is there so many different dist of Linux and no standard around it, with different package systems and I guess also file systems. Because of this does it usually take a longer time to get some hardware to work in Linux then in windows.

When you in windows notice that some hardware isn't working can you download a driver and it usually work. The same isn't truth for Linux where there usually isn't any easy to get and install drivers, like downloading a package in synaptic and it will work.

If there was a main system or a standard for Linux would businesses maybe start creating drivers for Linux that the average user would be able to install without going throw guide after guide. That would hopefully stop many of these *my wireless card isn't working*.

*Off Topic* Who release the hardware support in Linux?

2.
The second thing I see as a major problem in Ubuntu is that is harder to create a network between two machines that is running Ubuntu then between two where one is running Ubuntu and the other Windows, at lest for the home user. To change this is maybe more complicated that I would thing but if there ever would be a easier way to set up a network between Ubuntu would I hope that it did have a GUI.

---

### Post by Yfrwlf on 2008-01-04
> **SpinningAround said:**
> First:
I enjoy a lot of things in Linux, it's free that is a major thing if you compare it to other OS around, I don't think the developers receive enough credit for this. It's also more secure the windows and feels a little more effective then windows and not to forget is all the free programs that is around.

To the Criticism:
1.
The first thing that indirect effect most experience users as I see it, is the lack of standard in Linux for home users. For bushinesses and similar do Fedora exist that bring some help to the standard for them i guess, but I haven't tried it so unsure about it.

When I say indirect is that if I think that company's that create programs and hardware can have problem with creating this for Linux since if you look at it is there so many different dist of Linux and no standard around it, with different package systems and I guess also file systems. Because of this does it usually take a longer time to get some hardware to work in Linux then in windows.

When you in windows notice that some hardware isn't working can you download a driver and it usually work. The same isn't truth for Linux where there usually isn't any easy to get and install drivers, like downloading a package in synaptic and it will work.

If there was a main system or a standard for Linux would businesses maybe start creating drivers for Linux that the average user would be able to install without going throw guide after guide. That would hopefully stop many of these *my wireless card isn't working*.

*Off Topic* Who release the hardware support in Linux?

2.
The second thing I see as a major problem in Ubuntu is that is harder to create a network between two machines that is running Ubuntu then between two where one is running Ubuntu and the other Windows, at lest for the home user. To change this is maybe more complicated that I would thing but if there ever would be a easier way to set up a network between Ubuntu would I hope that it did have a GUI.

I agree fully with point #1, as I've said hundreds of times before.  I believe this problem with get fixed eventually.  Someone will come up with an "easy fix" that will allow a company to get their software installed correctly on basically any distro, or at least any distro that is LSB compliant and such (have to start somewhere).  However, helping it along would be, well, helpful. ;)

[Here]("http://www.linux.com/articles/59502") is an article about package management in Linux.

Also, read Ian Murdock's blog about it [here]("http://ianmurdock.com/2006/12/15/software-installation-on-linux-today-it-sucks-part-1/") and part 2 [here]("http://ianmurdock.com/2006/12/19/software-installation-on-linux-tomorrow-it-wont-with-some-cooperation-part-2/").

Finally, take a look at the Linux Foundation page [here]("http://www.linux-foundation.org/en/Packaging") and be sure to view the wiki.

But yes, an automated way to get installation done, SOMEHOW, would be really good.  I think it would be neat perhaps to see both a static and networked package format, one that would contain all the libraries needed to install a program, and another that would automatically download the required files needed.  The latter just wouldn't be as reliable, but it *would* provide an efficient and easy way to install programs from your browser from the net.  Instead of having to download a program that contained all the files, this format could check with your package manager to see what libraries you already had, saving you and them bandwidth.

Drivers would definitely be a really big help, but also general programs, and it would all allow users to make backups and archives of programs, and to be able to transport programs more easily.  The internet would start getting much more populated with Linux programs, because they would be *mobile*, instead of being tied down to a package manager, and before anyone says it, yes I know compiling from source is always possible, but the whole point of all this is to make Linux package installation easy, which *everyone* would appreciate.  Obviously installation from source should be an alternative too though, I'd also like to see an automated installation from source option, even though it's not that hard typing ./config make make install ;)

As for point #2, I agree, even though SMB sharing by default in Ubuntu is quite simple with Windows, the problem is you have to define a user and/or password for a Samba account for them to use to see your files, and you shouldn't have to do that.  Beginners needing the command line is a no-no, and Ubuntu needs to go after the migrating users.  Those who are slow to migrate will be turned off by this.  I'm sure this is a known issue though, and perhaps they'll change it for Hardy, or allow a way for users to specify a user and password for Windows users to use.  That would be an incredibly simple GUI tool to write...

I can possibly see why they might not want Windows users seeing Ubuntu file shares by default though.  It may be because the user/pass that Windows uses for unrestricted file sharing is widely known, so more hackers could spy on Ubuntu file shares if Windows users were allowed in by default.  Just an idea.

---

### Post by Yfrwlf on 2008-01-04
> **capink said:**
> I know that synaptic provide this. I am actually quite happy with the linux filesystem hierarchy. It is a lot better than anything I have seen. This why I am interested in virtual folders, as  it can present the filesystem to the user in many different ways without actually changing the filesystem.

I see a lot of people complaining that there are no program files folder like in windows. And I think virtual folders would allow different distros to present the filesystem in their own way without breaking compatibility with unix filesystem. And it adds to the linux flexibility. You can make linux look exactly like windows, not because windows way of doing things are better, but because linux flexibility allows for the user to make the system the way he likes. As for me, I am happy with my linux filesystem and don't want any change to it just to replicate another OS.

What about the changes that [Gobo Linux]("http://www.gobolinux.org/?page=at_a_glance") makes? ;)  Still not sure yet what impact this has on everything, or if there are any problems with it, but Compile and it's file structure are interesting.

---

### Post by cwej on 2008-01-04
You know, I really do appreciate the humor, especially in that last "/bin = The trash bin..."

However, just in case there might be some folks out there who are unfamiliar with the linux directory structure, "/bin" actually refers to "binaries." 

Here is a good quick reference link: [http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

---

### Post by swoll1980 on 2008-01-04
> **phenest said:**
> What makes you think the "shorthand abbreviation method" is for advanced users, or for speed? If there was a "version for beginners", you'd never move to the "advanced version". So, how do you think the "advanced users" got there?

That's like going to France and expecting the French to know English too, so it's easier for you. Why can't you just learn French?

If you want to use Linux, then learn Linux.

This is like asking to have a GUI for every terminal command, and just as ridiculous. :lolflag:

This is the problem with linux the people that think that everybody that has free time should spend it trying to learn how to use an operating system. if linux were as easy to use as microsoft everybody would be using it. You say if they don't use the advanced commands they wont learn them. Did it ever occure to you that maybe everyone on the earth does not want to be a computer geek? You act like it's all or nothing. If I want to shoot hoops in my driveway do I have to make it to the NBA? If I want to go to the local pool and go for swim, Do I have to become an olympic gold medalest? The world isn't black and white. The goal of Ubuntu is to bring Linux to the homes of regular people, and it would be great if the terminal was easy to use. They need to come up with a graphical way to add network users and passwords without using the cmd line. This is a task that anyone with more than 1 cpu needs to do so it should be as easy as possible.

---

### Post by popch on 2008-01-04
> **bloor75 said:**
> This is the problem with linux the people that think that everybody that has free time should spend it trying to learn how to use an operating system.

If you will, that's a major problem with every operating system and - indeed - with each piece of software: if you want to profit from it, you have to learn how to use it. Have you ever tried to program a video cassette recorder? Without looking up the manual?

> **bloor75 said:**
> if linux were as easy to use as microsoft everybody would be using it. 

What makes you say that microsoft is easy to use? It is not. In my daily life, I see grown up and intelligent people who are completely mystified by those products. In the literature I read of useability studies where practically every kind of software turns out to be easier to use than those by microsoft. Well, I exaggerate a bit, but not as much as you would think.

> **bloor75 said:**
> You say if they don't use the advanced commands they wont learn them. Did it ever occure to you that maybe everyone on the earth does not want to be a computer geek? You act like it's all or nothing.(...)  it would be great if the terminal was easy to use. .

I use Windows at work where the demands on flexibility are few. I use Linux at home where I want more flexibility and more applications. Guess what. I have to keep on using command lines and the registry editor and other GUI-less stuff in Windows just for a bit of tweaking. I have used the command line in Linux about five times in the last year, and that was to set up a function which was very particular to the PC I am using, and I have done so to run commands given to me by the friendly people in this forum.

It is all right for anyone to present his or her opinions in this forum. The presentation might be a bit more useful, however, if the opinions were based on observable facts.

---

### Post by swoll1980 on 2008-01-04
[QUOTE= I have used the command line in Linux about five times in the last year/QUOTE]

Well I guess you didn't have to set up network sharing. In the same year I've used the terminal 100 times. I'm being constructive I like Linux better and I did take the time to learn about it, but not everyone wants to spend that time. I managed to use windows my entire life without ever having to use a command line. In the last year I've spent hours in the command terminal. I don't care how much you like linux or if it's your god you can't honestly say that you think it's as easy to use. Just look at my post history you will see all the problems I had that requierd use of the terminal not just under bloor75 either but under swoll1980 witch was the name I was using untill my girlfreind used it to raise some contravrsy that I didn't agree with. look at all those post and all those problems Ive had and then tell me you don't have to use the terminal. And since before I started using Linux I never needed a forum to figure anything out on windows how can it be just as easy.

---

### Post by cardinals_fan on 2008-01-04
> The goal of Ubuntu is to bring Linux to the homes of regular people, and it would be great if the terminal was easy to use.

In my opinion, the terminal ***is*** easy to use.  The learning curve is steep, but after a while it becomes the easiest way to solve any problem.  And no, I'm not a linux guru with a lot of experience, I am a busy high school student who has used linux for about a year.

In terms of improvements, two come to mind.  Increased stability is *huge*.  Part of the appeal of linux (and Ubuntu in particular) is fewer crashes.  Also, it is time to lose the GNOME-mimicking default layout in Xubuntu!  Come on, Xfce is a distinct DE, not a branch of GNOME!  (Good to get that off my chest.) :-)

---

### Post by popch on 2008-01-04
> **bloor75 said:**
> Well I guess you didn't have to set up network sharing..

Guess again. Our household mixes several Windows-driven PCs, one MAC and a variable number of Linux PCs plus one or two routers, an ADSL modem, a small assortment of file server appliances and the odd printer or two.

---

### Post by swoll1980 on 2008-01-04
> **popch said:**
> Guess again. Our household mixes several Windows-driven PCs, one MAC and a variable number of Linux PCs plus one or two routers, an ADSL modem, a small assortment of file server appliances and the odd printer or two.

And you didn't need to use the terminal to do this. Please explain

---

### Post by swoll1980 on 2008-01-04
> **cardinals_fan said:**
> In my opinion, the terminal is easy to use.  The learning curve is steep

Thats an oxymoron how can something that is easy have a steep learning curve

---

### Post by popch on 2008-01-04
> **bloor75 said:**
> And you didn't need to use the terminal to do this. Please explain

I cheated a bit. The file server appliances are Linux driven,  and they come with nice web applications where you just point, click and enter the directory and user names. For one setup I used an entry in a file in /etc. That's editing, not command line, and has been seen to occur in the Windows world, too, and even - shh - in Mac OS. All other connections are done with the facitlities provided by the GUIs of the PCs.

---

### Post by Globulator on 2008-01-04
1) Kubuntu has issues between kdm and the control panel within KDE, in that you are stuck if your UID is 500 (below 1000), kdm themes mess up the kdm config, and finally the control panel does not restart kdm so no change appears to make any difference anyway.

2) After faffing with kdm setup and switching off the pc, on restart the X-windows res was stuck at 640x480, and could only be recovered by editing the XFree86 config file manually.

3) Ubuntu needs to be useable by your mum - it is to get noticed. It seems to ship with a bunch of programs that most poeple will not need - but Firefox + flash for looking at U-tube is not there, some video decoders need installing etc.

Ubuntu is better than kubuntu out of the box, but still I think it needs to aim to give people full OpenOffice, Thunderbird, Firefox+flash out of the box. Cut down on apps that do the same thing - just put the basic but good ones in.

Remember we are trying to gain ex Microsoft users, if nothing works without a good knowledge of apt-get then that isn't going to happen. It's getting there, but needs ***polish,*** and better package selection:  not *features.*

---

### Post by swoll1980 on 2008-01-04
> **popch said:**
> I cheated a bit. The file server appliances are Linux driven,  and they come with nice web applications where you just point, click and enter the directory and user names. For one setup I used an entry in a file in /etc. That's editing, not command line, and has been seen to occur in the Windows world, too, and even - shh - in Mac OS. All other connections are done with the facitlities provided by the GUIs of the PCs.

well thats what ubuntu needs a way to point and click or a graphical way to alter those scritps

---

### Post by cardinals_fan on 2008-01-04
> **bloor75 said:**
> Thats an oxymoron how can something that is easy have a steep learning curve

Incomplete thought, sorry.  What I mean is that the terminal is the easiest way to do things *once you figure it out the first time*.  I fully agree with everyone who said that a guide to the terminal for new users should be included.  That could give people a head start on how to use the terminal in their daily lives.

---

### Post by swoll1980 on 2008-01-04
> **Globulator said:**
> 1) Kubuntu has issues between kdm and the control panel within KDE, in that you are stuck if your UID is 500 (below 1000), kdm themes mess up the kdm config, and finally the control panel does not restart kdm so no change appears to make any difference anyway.

2) After faffing with kdm setup and switching off the pc, on restart the X-windows res was stuck at 640x480, and could only be recovered by editing the XFree86 config file manually.

3) Ubuntu needs to be useable by your mum - it is to get noticed. It seems to ship with a bunch of programs that most poeple will not need - but Firefox + flash for looking at U-tube is not there, some video decoders need installing etc.

Ubuntu is better than kubuntu out of the box, but still I think it needs to aim to give people full OpenOffice, Thunderbird, Firefox+flash out of the box. Cut down on apps that do the same thing - just put the basic but good ones in.

Remember we are trying to gain ex Microsoft users, if nothing works without a good knowledge of apt-get then that isn't going to happen. It's getting there, but needs ***polish,*** and better package selection:  not *features.*

Ubuntu did a great job with the automated codac installs so your a little behind the times. As far as kubuntu I don't know what the hell went wrong there If you try other kde distros like mandriva KDE is so much nicer. I don't think Ununtu and KDE are compatable for some reason

---

### Post by swoll1980 on 2008-01-04
> **cardinals_fan said:**
> Incomplete thought, sorry.  What I mean is that the terminal is the easiest way to do things *once you figure it out the first time*.  I fully agree with everyone who said that a guide to the terminal for new users should be included.  That could give people a head start on how to use the terminal in their daily lives.

Thats about the way it is. Now that I know a lot about it I use it for a lot of things I don't even need it for

---

### Post by Yfrwlf on 2008-01-04
The fact is that to use a GUI you need to know how to move the mouse around and click.  You use the command line, you need to know how to type and what to type, which involves word memorization and in slightly more complex cases an understanding of directory structure and navigation.  In other words, the command line is harder to learn, regardless of how easy it was for *you* to learn it.

I agree with bloor that you indeed can't expect everyone to understand the more complex terminal (to be "geeks"), and there are lots of people who can't even learn how to use a GUI interface.  Hell, I knew one lady who tried to use the mouse like a sewing pedal with her foot.

The fact is though, most people now days have learned the GUI and the basic point-and-click procedure to get certain things to happen.  That knowledge is the strength Macs play on, and the goal Ubuntu strives for as well.

bloor, I'm sorry you've had problems, and I agree that for the things that most people need to do, there should be a simple way of doing things the way they are used to without having to learn the command line.  I believe that for most everything, and for anything, if there is someone out there who wants to accomplish a task in **any way at all** whether it's speaking to load a program or clapping to make all the lights in your house turn on, if there is a will there is a way, especially with Linux.  So, Ubuntu's goal should be *your* goal, but since it can't "waste" it's resources too much, it should tackle the major problems, and those are the problems of giving the *majority* what they want as a priority that's only based on numbers of individuals.  That is the way that Linux is going to spread the furthest.  When that happens, you'll see more programs, more patches, more effort, and you'll also get the very specific things that you want as well, eventually, as long as there's someone else out there who wants the same and knows how to do some programming.

Any way back on topic, I think Gobo Linux has done some things to make the command line more palatable to beginner users, and potentially for everyone, by reorganizing the file structure into something that's easier to understand.  Now whether that structure really is easier or if it meets the needs of developers or not is a great question, but for normal users trying to find files by use of the command line or by browsing to the file's location, it makes things easier.  Not that this is normally done any way, most people just use the menu of course.

Arguments about making the commands on the command line easier though are pretty funny though in a sense, I believe the command line is simply fundamentally difficult by nature, and while there are ways to make it friendlier, and while you could even have a text-based "GUI" that guides you through doing command line things, what makes the command line the command line is remembering commands to type, and typing them in, and not everyone is good at doing it.  Desktop environments "teach" more easily by displaying your options, so you don't have to remember what they are all the time, or perhaps it'd be more accurate to say the GUI allows you to not have to remember as much, and slack mentally.  Nothing particularly wrong with that, some people have more important things to do than learn where things are or what they are called all the time.

Most users just want to get to their programs and files any way.

Glob, don't forget you can help polish Ubuntu by filing bug reports for any bugs you find, but try to find a way to reproduce them of course.  I agree that polish should be a strong goal.  It turns a "testing/development OS" into a rock-solid desktop OS.

---

### Post by Endolith on 2008-01-04
> **perce said:**
> you're essentially asking for a GUI for apt-file in the same way as synaptic is a GUI for apt-get. That would be cool.

Synaptic *itself* should be a GUI for apt-file.  It already lets you search for packages by name and description; why not by the same things as apt-file?

---

### Post by BreathEasy on 2008-01-04
Compiz Fusion needs to be as smart as Vista's Aero when running fullscreen applications, specifically games. Aero, when it detects a game wanting to run in fullscreen, will disable itself to reduce overhead and allow maximum performance for the game. When the game is closed down, Aero will restart automatically. If Vista can do this automatically, Compiz Fusion should be able to as well. In the meantime, I've had to use a hand-made script to do all the disabling/reenabling work myself.

---

### Post by Endolith on 2008-01-04
> **cwej said:**
> However, just in case there might be some folks out there who are unfamiliar with the linux directory structure, "/bin" actually refers to "binaries." 

Here is a good quick reference link: [http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

Ideally, no one who uses Ubuntu should *ever* have to know this.  Please hide system-level details from the user whenever possible.

---

### Post by Endolith on 2008-01-04
> **Yfrwlf said:**
> In other words, the command line is harder to learn, regardless of how easy it was for *you* to learn it.

The fact is though, most people now days have learned the GUI and the basic point-and-click procedure to get certain things to happen.  That knowledge is the strength Macs play on, and the goal Ubuntu strives for as well.

The best interface would be a combination of the two.  The descriptive power of language with the feedback, responsiveness, discoverability, and forgiveness of a GUI.  Things like Deskbar are a step in the right direction.

> for the things that most people need to do, there should be a simple way of doing things the way they are used to without having to learn the command line.

Definitely.  Unfortunately, those ways haven't always been written yet.

> and while you could even have a text-based "GUI" that guides you through doing command line things,

We need things like this for the cases where the "nice" ways haven't been written yet.

Do you know of any?  The only thing I know of is Hotwire shell.

---

### Post by swoll1980 on 2008-01-05
I found this thing called hotwire but haven't been able to figure out exacly what it does, but it's supposed to make the terminal easier to use

---

### Post by Yfrwlf on 2008-01-05
> **BreathEasy said:**
> Compiz Fusion needs to be as smart as Vista's Aero when running fullscreen applications, specifically games. Aero, when it detects a game wanting to run in fullscreen, will disable itself to reduce overhead and allow maximum performance for the game. When the game is closed down, Aero will restart automatically. If Vista can do this automatically, Compiz Fusion should be able to as well. In the meantime, I've had to use a hand-made script to do all the disabling/reenabling work myself.

Thought about this before too and if I have and you have then I'd guess the Compiz team has as well.  Hmm, a program wanting to let the system know it's going to do something intensive and to prepare for it...sounds like a need for an API to me. ;)  But, instead of adding a standard method of communicating "OK, turn off your advanced desktop effects now, I'm about to do some cool crap!" perhaps another solution would be if Compiz could see that there is demand for GPU power by another graphics application that has user priority.  Not sure how possible that would be, but yeah, something running "fullscreen" would be a pretty simple solution as well, but keep in mind it'd cause some simple programs that don't need effects disabled would load slower because of it, so a GPU demand monitor might be a more intelligent, although harder, solution.  Might be impossible too, since I'm sure a lot of proprietary cards don't allow GPU demand to be seen, but I'm not sure.

> **Endolith said:**
> Do you know of any?  The only thing I know of is Hotwire shell.

Nope.  Honestly, now that I know the command line, it's harder for me to know exactly what would make things easier.  I think there may be some cases where smarter default options should be made though, which is an easy thing to fix, but that's already the way things are in a lot of programs.  Doubletab is incredibly nice and helps you learn.  Locate is definitely helpful.  The manual pages are very nice.  For most things that most users would want to do, they can just use Nautilus any way.  The goal of Ubuntu is to make it so most all users will never need the terminal any way.

All I can really think of is a friendly little welcome message when you load up the terminal describing a few basic principals.  Then, chastising the nooblet for accidentally opening the terminal in the first place, telling them it must have been a mistake, and closing it automatically.

OK, maybe not those last three ideas...

---

### Post by Endolith on 2008-01-05
> **Yfrwlf said:**
> Nope.  Honestly, now that I know the command line, it's harder for me to know exactly what would make things easier.  I think there may be some cases where smarter default options should be made though, which is an easy thing to fix, but that's already the way things are in a lot of programs.

I found this last night:

[http://fishshell.org/](http://fishshell.org/)

It looks like a good step.

> Then, chastising the nooblet for accidentally opening the terminal in the first place, telling them it must have been a mistake, and closing it automatically.

Agreed. ;-)

---

### Post by GSS on 2008-01-05
I have a complaint based on a problem I'm having with Ubuntu 7.10. First, I figure I'll mention the problem.

I'm trying to get my wireless network card, under 7.10, to go online. The network I'm trying to access uses WEP for wirless security. It sounds like a joke I know but the network is not run by me and is not under my control.

Anyway, Ubuntu 7.10 has added all these extra programs like WPA suppliant and NetworkManager that are suppose to make connecting to networks or the Internet so much easier and sure enough all that new software sees the available networks and ask that I sign on.

Now when I do this for the network I'm trying to access a window pops up asking for the WPA code. A menu gives me several more options, including using a 64 or 128 WEP Hex key. I dutifully enter the information and the NetworkManager dutifully tries to connect me to the network, but, alas, it cannot.

I then try to manually enter the necessary data but that doesn't work either.

In brief, it appears that some of that software involved in automatically configuring a wireless network connection is not allowing me to access a WEP secured wireless network.

This problem is in contrast to the easiness of me manually configuring my wireless adapter under Ubuntu 6.10 to access the network and the Internet as I am now doing with a Ubuntu 6.10 LiveCD.

So, I guess what I have to say to say to Ubuntu is please don't break things that work pretty well as you rush to make things more easier for the average user and that is my only complaint... for today that is.

---

### Post by tgbrowning on 2008-01-05
After about 8 months of using Ubuntu, and reading lots and lots of stuff in the forums, my best advice is for the next version to do everything it can to make Ubuntu wifi configuration a cake walk. 

Honestly, look at the number of people who are constantly asking about how to get broadcom or other wifi cards to work.  It's the biggest stumbling block I can see. Especially when you consider that access to Internet is essential to getting Ubuntu up and running well.

Browning>>>

---

### Post by cardinals_fan on 2008-01-06
> **BreathEasy said:**
> Aero, when it detects a game wanting to run in fullscreen, will disable itself to reduce overhead and allow maximum performance for the game.

I don't disagree that Compiz Fusion needs more work (and you raise a good point about fullscreen apps), but any comment about Aero "reducing overhead" makes me want to laugh.  When it takes over 500 mb of memory with no programs open, Vista will *never* be efficient in my book. :)

---

### Post by cwej on 2008-01-06
I understand your point -- users shouldn't have to, and really don't have to know about the directory structure. My wife, for example, hasn't a clue, and doesn't care. She is barely aware that the computer that she uses ports Ubuntu, and doesn't care either, as long as she can surf, use email, and pay bills. That probably says a lot about the maturity of the platform. However, I've found a better understanding helpful.

---

### Post by sajro on 2008-01-06
I have two.

1) This is about liveCDs. ISOLINUX is nice but it doesn't support older hardware. I was wanting to put puppy on my old computer but it won't boot because it needs ISOLINUX. I think something needs to be done because Syslinux works on said hardware so why not ISOLINUX?

2) Source code access. I find it extremely confusing to locate source code for OSS. If there were a simple way to organize source code from projects (to download, manage, compile, etc.) it would be much easier to work on them. It would also help self-teaching programmers (like myself) learn by example more easily.

That's pretty much it. I think Linux is the best OS available today.

---

### Post by Tsen on 2008-01-06
> **cardinals_fan said:**
> I don't disagree that Compiz Fusion needs more work (and you raise a good point about fullscreen apps), but any comment about Aero "reducing overhead" makes me want to laugh.  When it takes over 500 mb of memory with no programs open, Vista will *never* be efficient in my book. :)

Okay, I'm a Vista hater, but memory usage is one thing it gets RIGHT.  I have 4 GB of RAM, and Linux doesn't touch it.  Frankly, it's wasteful.  Vista uses about 1.7 GB of it minimum when idling to keep programs precached so they open as fast as possible.  There's no reason NOT to use the RAM--otherwise it literally sits there and does nothing.  And the second you open a memory-intensive app, the cached RAM is freed and reallocated.  Of all the valid Vista criticisms, caching is not one.  There's even hacks to enable similar prefetching in Linux, for sizable performance gains--but it isn't stable enough for the mainstream last I checked.  So that's +1 for Microsoft.

Anyway, my criticisms for Ubuntu:
I've been away from Linux for a while as I've gotten my new gaming PC up and running to replace my old junker.  Last I used Ubuntu was the very late betas of Feisty, and frankly, they were better than Gutsy is.  Here's why, and how I think it could be fixed:

-Firefox:  Everything about it seems broken now.  Plugin installation is a pain, you have to edit etc/hosts to even allow you to install extensions or themes from Mozilla.  Yes, you can download some of the more popular ones via add/remove programs, but the key word there is "some".  Not to mention it's a bit of a workaround--I prefer to install mine through Firefox.  Others may prefer the add/remove option, but that's no reason to disable or inhibit the other.

-Compiz:  Yeah, it's nice to have it enabled by default.  It is rather annoying about the restricted drivers having to be manually enabled first, but I can live with it (though why not include restricted drivers as an "optional" update through the update manager?  Unselected by default?  I hate having to wait forty minutes while it updates before I can do anything about installing applications or fixing the annoying restricted drivers.)  Once I can actually get it running, though, it's a pain to figure out how the hell I'm supposed to configure it.  Eventually I come to find that the CCSM has been renamed "Advanced Desktop Effects Settings" and is not installed by default.  I knew I needed CCSM, but that's not what it's listed as in the Add/Remove list.  Why not?  Or why not have it installed by default?  Or at least SOME semblance of options for the effects?  I know very few people who use the default settings for Compiz.  So why cripple it?

---

### Post by saulgoode on 2008-01-06
> **Tsen said:**
> Okay, I'm a Vista hater, but memory usage is one thing it gets RIGHT.  I have 4 GB of RAM, and Linux doesn't touch it.  Frankly, it's wasteful.  Vista uses about 1.7 GB of it minimum when idling to keep programs precached so they open as fast as possible.  There's no reason NOT to use the RAM--otherwise it literally sits there and does nothing.  And the second you open a memory-intensive app, the cached RAM is freed and reallocated.  Of all the valid Vista criticisms, caching is not one.  There's even hacks to enable similar prefetching in Linux, for sizable performance gains--but it isn't stable enough for the mainstream last I checked.  So that's +1 for Microsoft.

The Linux kernel offers you the choice of whether to retain applications in memory versus having that memory available for caching. The value in /proc/sys/vm/swappiness will determine this. Change the value to "0" if you prefer that you huge app (and its data) are kept in memory when you switch to another process; or use "100" if you want that app transferred to swap. Or any number in between to provide a reasonable compromise.

---

### Post by allforcarrie on 2008-01-06
Come on people its 2008, who wants to use the stupid command line anyway?

---

### Post by allforcarrie on 2008-01-06
> **tashmooclam said:**
> Maybe this isn't useful, but I would have liked a pdf file "user guide to ubuntu" on the disk, so I could read about the OS without being online all the time.
 
 
 
EXAMPLE: I am currently deployed and cannot get my linux install online while i'm here. I i want to patch something or install a program i have to find a .deb and transer it over on my flash drive. I would love to see some kind of Ubuntu for dummys file on the disk. Yes, people will be screaming BLOAT BLOAT! This file could be put in and the annoying examples folder could be removed. :)

---

### Post by Yfrwlf on 2008-01-06
> **saulgoode said:**
> The Linux kernel offers you the choice of whether to retainapplications in memory versus having that memory available for caching. The value in /proc/sys/vm/swappiness will determine this. Change the value to "0" if you prefer that you huge app (and its data) are kept in memory when you switch to another process; or use "100" if you want that app transferred to swap. Or any number in between to provide a reasonable compromise.

Don't you just love /proc? :)  I think it would be neat if there was a GUI for system tweaks, like there are for those alternative OSes. ;)

GUIs can be an easy way for beginners to learn about Linux and to get straight to the options available without having to discover things via the command line and manual pages and such.  Basically, GUIs can be "easier", and I can see a lot of tweakers being very happy with a GUI-based tool for showing them all the things available in Linux that would normally only be available to them via the command line.

What about a performance and tweaker GUI that allowed the tweaking of things like this, as well as tweaking parallel system startup processes to allow faster booting, and any random tweaks that might be of interest or important to someone trying to squeeze more performance out of their Linux system.  I've heard a few users mention wanting something like this, and it couldn't be very difficult to implement most of them obviously since it's mostly just work in making the GUI.

> **Tsen said:**
> -Firefox:  Everything about it seems broken now.  Plugin installation is a pain, you have to edit etc/hosts to even allow you to install extensions or themes from Mozilla.  Yes, you can download some of the more popular ones via add/remove programs, but the key word there is "some".  Not to mention it's a bit of a workaround--I prefer to install mine through Firefox.  Others may prefer the add/remove option, but that's no reason to disable or inhibit the other.

There are extensions you can't install?  I've installed several Firefox extensions and never had a problem.  I thought you could always install extensions, since most of all of them are cross-platform.  Editing your hosts file to allow Mozilla extensions would be ridiculous indeed!

> **Tsen said:**
> -Compiz:  Yeah, it's nice to have it enabled by default.  It is rather annoying about the restricted drivers having to be manually enabled first, but I can live with it (though why not include restricted drivers as an "optional" update through the update manager?  Unselected by default?  I hate having to wait forty minutes while it updates before I can do anything about installing applications or fixing the annoying restricted drivers.)

For ATI cards at least, at least with many of them, you don't need the closed source driver to enable Compiz.  I think combining the restricted drivers with the updater tool might be a neat idea though, but there needs to be a way to easily keep them separate and to disable or reject any closed source drivers, but I could certainly see the updater being made more complex so it could replace the restricted manager.

If you want the video driver first though, then just install it first, before doing updates?  To get around the two things using the package manager at once problem though, it'd be neat if there was a "waiting for package manager to be free" message, instead of just refusing to work, that way you could que them up. :)

> **allforcarrie said:**
> Come on people its 2008, who wants to use the stupid command line anyway?

That's not very constructive, but if you are simply saying there needs to be more GUI programs, and more ways created to give alternatives to the command line to do most everything you'd want to do then I'd agree.  Perhaps you were joking or whatnot, but now I'll answer your question directly regardless.  GUIs are simply front-ends to engines.  This allows the use of scripts and system automation if you're an administrator, and offers speed and flexibility for certain types of situations.  Even Windows administrators write scripts and programs and use the command line.  I'm not saying it's impossible to completely get rid of it, but at the very least it's still used heavily today, and there are certain instances that I can see where it'd be insane not having a command line.  GUIs would all become extremely bloated with options to interface with other programs if there were no command line, since it's the method of inter-program communication.  What if you wanted to have a computer convert a bunch of images from one type into another at a certain time of day without making the computer load up The Gimp graphically?  You want the engine to do the work, not a GUI, because you don't want any GUI to pop up in this instance.  GUIs can be great learning tools though, or lazy-enablers, whichever you want to call them, but regardless are still preferred by most users.  It's fitting that the advanced knowledge is left to the admins or power users any way.  For non-admins and non-power-users, sure, most everything they want to do could be done through the GUI, but some users do use the command line and prefer to understand and have access to it in some situations.  Sending commands, retrieving logs and emails, you name it.  You use what you prefer, let other users use what they prefer. :)

To bring that back into the realm of being constructive, how about making suggestions for GUI applications that you'd like to have and use?  I, for one, think a GUI tool allowing quick access to the plethora of system tweaks that are possible in Linux might be a popular and neat program, and very easy to create.

---

### Post by Tsen on 2008-01-07
Everytime I reinstall Ubuntu on my new computer, Mozilla does nothing when I click an extension to download it.  About three minutes later, a window will pop up like I just clicked it, but the extension won't download and Firefox hangs.  After searching the forum, I found several people started having the problem around Feisty's release and the only known solution is to add Mozilla's IP address to etc/hosts, otherwise only Add/Remove extensions can be installed.
Though on closer inspection, this isn' t because of them allowing extensions in the Add/Remove list, it's because of an IPv4/IPv6 conflict.

---

### Post by saulgoode on 2008-01-07
> **Yfrwlf said:**
> What about a performance and tweaker GUI that allowed the tweaking of things like this, as well as tweaking parallel system startup processes to allow faster booting, and any random tweaks that might be of interest or important to someone trying to squeeze more performance out of their Linux system.  I've heard a few users mention wanting something like this, and it couldn't be very difficult to implement most of them obviously since it's mostly just work in making the GUI.

Cool! Let me know when you finish writing it.

---

### Post by Yfrwlf on 2008-01-07
> **saulgoode said:**
> Cool! Let me know when you finish writing it.

Ha, not much of a programmer, yet. ;)  Know some relatively easy GUI visual programming software, or the easiest way to create something like this?  WXWidgets?  Python?  Or do I need to learn GTK?  Any learning resources about Linux programming in general? =P

I just hate the idea of making a program that's not even cross-DE, let alone platform (not that that matters in this case), so if WXWidgets would allow that then that might be cool.

Also, know of any Linux power tweaking resources to use as the basis of such a program?

Sorry, I just have no clue where to begin really, any suggestions would be awesome but if not that's fine, thank you! :)

---

### Post by yatt on 2008-01-07
I think that Hardy should focus on polish. That is what happened with Dapper and it turned out very stable (considering most testing releases where more stable than the gold release of Edgy).

Anyways, my gripes:

1) Themes (in before then Ubuntu would be blue and look like everyone else). I think some of the currently shipping themes should be scrapped and replaced with something made by the Ubuntu Art Team. Open up Appearance Preferences and you will see what I mean. I am currently using the live CD and really you are left with slim pickings. Human is a good theme if you are into Orange (I personally am not), and the similar Glossy and Clearlooks. Actually, Gutsy is worse off than Feisty as Gutsy got rid of one of the better icon themes: Tango. Then there are five other themes that look about as old as the Windows 95 style. I think we should take two of the themes, Clearlooks and Human, and offer each in a bunch of colors. Have both engines offer say orange, blue, green, pink, purple, black, and of course brown. In the likely case of an 'abstract' default background (like Gutsy's), include it in each color and have the theme suggest it. Before anyone brings up Gnome-Look, how do those that do not know find out about it? The theme manager does not link there, and not everyone spends all day on this forum or Google searching ways the can mod their Ubuntu install. Nobody would look at it if it was made a default bookmark for Firefox either.

2) Again themes, but slightly different than the last ramble. When you are running Gnome, KDE apps should be themed to match the current Gnome theme and vice-versa. Actually, KDE is mostly able to theme Gnome apps at the moment. All it lacks is setting icon support. Right now, it picks the ugliest icon set the system comes with. Gnome on the other hand, does nothing.

3) Compiz. To be honest, I haven't actually used Compiz on Ubuntu since it became an Ubuntu default. It is very probable that it behave completely differently from how it does on Debian and Gentoo, which I will be referring to here. Compiz lacks polish. Badly. A good example is when you log in. It causes a couple extra screen flashes, and there is a moment where if you have a window open, it loses its decorator. Not pretty. This is really where Quartz and Aero have Compiz beat. They may not offer the same functionality as Compiz, but they look there best at all times. When you start, they are just there. For those who have a dual monitor setup, try opening a game with a window open on the other screen. You will notice the Aero no long has access to direct rendering and goes into basic mode. When it gets DR back, it goes back into its full mode and it does so without massive flickering or temporarily lose the window decorator.

4) Now it is time to combine 1 and 3. I think that the theme engines should start using the composite capabilities when available. I know it is on its way in Murrine, but we still need the applications themselves to use the feature (which is a sound idea). To bring 2 into this, it would be nice if KDE could bring this in too.

5) nm-applet. It is so annoying that it deserves its own section. Is there any particular reason as to why it prompts for a password every time I log in? Really what is the point? It could just ask me for the network password every time. Which would still be annoying. It is the only networking solution I have used that prompts for a password every time you start it. In this case, being different is not an improvement.

6) Folder and Printing sharing. On Vista it required me a grand total of 6 clicks, IIRC. On Linux you need to get a networking degree, then sacrifice a goat to the gods. For people with multiple computers, wanting to share the printer is quite common. I know CUPS will let you share just the printer, but even that is not as elegant as it could be. Plus it requires all machines to support CUPS.

I think those are some of my bigger issues at the moment.

---

### Post by yatt on 2008-01-07
> **Yfrwlf said:**
> Ha, not much of a programmer, yet. ;)  Know some relatively easy GUI visual programming software, or the easiest way to create something like this?  WXWidgets?  Python?  Or do I need to learn GTK?  Any learning resources about Linux programming in general? =P

I just hate the idea of making a program that's not even cross-DE, let alone platform (not that that matters in this case), so if WXWidgets would allow that then that might be cool.

Also, know of any Linux power tweaking resources to use as the basis of such a program?

Sorry, I just have no clue where to begin really, any suggestions would be awesome but if not that's fine, thank you! :)
Python would be a good for the job. The default python tutorial is pretty good. Lots of people recommend Dive into Python, but it is a bit advanced. I'd only recommend it if you have had some previous programming experience. I'd probably just use Gtk.

---

### Post by twin_57103 on 2008-01-08
Here are a few ideas:

A GUI for common configuration needs, especially a 5-button mouse.  If Ubuntu is to increase in mainstream use, the user should not have to manually edit configuration files after wading through internet posts to figure out how.  Also, support 5-button mice without post-installation configuration.

Easier installation of non-repository software (as in the original post).  Also, keep the repositories more up to date.  The versions in the repositories are often old and installing non-repository software can be a beast.

A reboot to other OS option - would be helpful for those of us who dual-boot.  I believe this exists in other distros?  Perhaps this could be a post-installation add-on.

Multisession burning support in the integrated/default CD/DVD creator.  Brasero is great for this, but I'd like to see this feature in the default application as well.

Better help files, documentation, and manuals!!  Help files are often underdeveloped and sometimes completely useless.  I know this has more to do with the individual program developers than the OS as a whole, but it is a major oversight.  I've tried to learn some of the Gnome Games only to have to go to the internet to find out what to do because there was so little in the help files!

---

### Post by allforcarrie on 2008-01-08
IN the apperance settings, there could be a button that says "get mroe themes" and directs you to gnome-look.org or respective window managers.

---

### Post by jespdj on 2008-01-08
My criticisms:

1. Ubuntu / Linux needs better power management, especially for laptops. My impression of power management on Ubuntu 7.10 is that it's a bit crude, not as sophisticated as power management on Windows. The difficulty is that a lot of parts / drivers need to participate to make power management really good. The battery on my laptop does not last terribly long on Ubuntu 7.10 and I've read many posts by people (especially in the Hardware / Laptops forum) who have noticed the same thing.

2. Lots of little bugs and problems that need to be solved by typing in obscure sequences of commands. Look at the General Help or Hardware forums. These forums are completely full of posts by people who's video card / wireless network / external harddisk / sound card / other piece of hardware doesn't work (properly) and in many cases they need to type in sequences of obscure commands to get it working (if it's possible at all). The Ubuntu developers should really be watching the most common problems very closely and make sure that such problems don't happen in future Ubuntu versions. Ofcourse, there's new hardware coming available all the time and it's hard to keep the drivers up to date, but I believe that diagnosing problems could be made a lot more user-friendly that it currently is.

3. Ubuntu 7.10 had a really nice and user-friendly way to install Adobe Flash in Firefox. Unfortunately it is currently broken, because Adobe published a new version of the Flash player on their website, and the Ubuntu installer refuses to install it (see [this thread](http://ubuntuforums.org/showthread.php?t=636397)). What happens now is that if you use the Ubuntu installer to install Flash from Firefox, it does not show any error message, but the Flash player is not installed, so the next time you go to a page with Flash you get the same prompt to install the player again. This bug started somewhere in the first week of December 2007 and it still isn't fixed. I'm astonished to see that this isn't a high priority bug that's fixed ASAP. The whole wonderful user-friendly Flash installation, which is one of the nice improvements in Gutsy, is already broken for more than a month.

4. I like Compiz Fusion, but it's clear that it has to be polished more in the future. There are some applications that do not work well when Compiz Fusion is enabled. Why isn't compizconfig-settings-manager installed by default on Ubuntu 7.10?

5. Some programs are clearly written by developers who don't have a lot of sense about what a user-friendly GUI is. Look at compizconfig-settings-manager. It shows you hundreds of options, but what all those options do is very poorly documented. (Maybe that's the reason it isn't included in Gutsy by default?). The GNOME menu editor is another example that really needs improvement. There are other programs, but you can't really blame Ubuntu for those. For example, I've tried a few programs for ripping DVDs or converting video and audio formats. Those programs are full of technical terms; you need to be an expert in video and audio encoding algorithms to be able to understand what all those terms mean. Such programs are not useable for the average non-technical user.

6. Sometimes there are obvious bugs in Ubuntu which make me think "Did anybody actually test this before the Ubuntu release?". For example, in the 64-bit version, lots of people have problems with the logo screen while booting: it doesn't show up. Those things sound like simple little problems that would have been noticed immediately if anyone had actually tried to install Ubuntu on a fresh system. Why do the Ubuntu releases contain such obvious bugs; isn't anyone even doing a "smoke test" before a release is done?

Added: It would be really nice if there were some really nice "killer applications" bundled with Ubuntu; something like Garage Band on the Mac, for example. I think that would help the popularity of Ubuntu immensely.

---

### Post by capink on 2008-01-08
There is something called wxwidgets that I belive enbale devs to write gui applications for linux and windows. It uses the native controls of both windows and gtk gui elements. 

What about a similar api or toolkit ot whatever it is called, that would allow devs to develop gui programs for both qt and gtk? with an option to compile the application using one of them.

---

### Post by plun on 2008-01-08
> **jespdj said:**
> 
3. Ubuntu 7.10 had a really nice and user-friendly way to install Adobe Flash in Firefox. Unfortunately it is currently broken, because Adobe published a new version of the Flash player on their website, and the Ubuntu installer refuses to install it (see [this thread](http://ubuntuforums.org/showthread.php?t=636397)). What happens now is that if you use the Ubuntu installer to install Flash from Firefox, it does not show any error message, but the Flash player is not installed, so the next time you go to a page with Flash you get the same prompt to install the player again. This bug started somewhere in the first week of December 2007 and it still isn't fixed. I'm astonished to see that this isn't a high priority bug that's fixed ASAP. The whole wonderful user-friendly Flash installation, which is one of the nice improvements in Gutsy, is already broken for more than a month.



Well this point is just tragic...  :(

Security Bypass
Cross Site Scripting
Manipulation of data
Exposure of sensitive information
Privilege escalation
DoS
System access
 
Solution:
**Update to version 9.0.115.0.**

[http://secunia.com/advisories/28161/](http://secunia.com/advisories/28161/)

Should be done within a few days to avoid risks after a security update from a vendor and Adobe IS the vendor....:)

---

### Post by Arkenzor on 2008-01-08
I definitely agree with the fact that Ubuntu needs to make the command-line more "accessible".
I'm not thinking about my grand-mother, or even my mother, when I say this. That is, people who only want a basic desktop experience - browsing the internet, receiving and sending mail and the such can already do it perfectly using the more natural gui programs. Of course they wouldn't be able to setup their system or troubleshoot it by themselves, but that's true of any current OS and it's probably better to just tell them to have someone else do it for them. So I agree, there's not much point in making the command-line more accessible to real end-users.

But many people (I think) want to have control over their computer, and are ready to take a little time for it as long as the information _is easily available_ and all they need to do is put a little effort in understanding it. However, it seems Linux always considers its users are either my mother/grandmother, or full-fledged sysadmins with nothing more to learn. The sysadmin side makes no effort at all to allow newcomers to understand it, and the gui side's main priority seems to be to make sure that its users never ever stumble upon command-line nothions. 

So basically, there's no learning curve at all for Linux without plowing through details and useless pages on google to finally find a tutorial that was written 10 years ago and uses totally outdated notions. Windows 98 taught me by itself how to master it (though Microsoft's Great Crusade for User-Friendliness made subsequent versions thouroughly obscure and un-learnable), Ubuntu doesn't teach me anything, and all the things I learned were out of pure chance, when the right web page fell from the sky right under my nose.

So, I think a simple welcome message in the console telling you about man and apropos would already be an awesome help, just like a noob-friendly basic guide to the command-line (easily accessible -> not buried in /usr/share/doc, come on, it took me 4 whole monts to actually notice that directory and realize it was just so easy to find documentation), and maybe a simple notice in Synaptic after installing programs "This package installed the following command-line commands: <Files installed in /usr/bin>. The list of all the files that were installed can be found under Installed Files in the package properties". As mentioned before, there must also be a way of having all commands run in verbose mode by default.
Also, why not see if we can find a less unusable version of KRegExpEditor and mention it in a visible place? 
It probably wouldn't take much effort to help people discover and learn the command-line by themselves.


Apart from this point, I also agree that an unstable Ubuntu release similar to Debian Sid would be neat ("If you want bleeding edge try another distro" doesn't really make it for me, we're trying to conquer the world after all °><°).



I do think Hardy as a LTS release should focus more on fixing what already exists than adding new features, though.

---

### Post by dgoodma on 2008-01-08
Laptops, NVIDIA setup to get the cool desktop features.... that process should be easier. 

On Xubuntu, the Keyring manager always wanting a password before it connects to Wireless. Read the fixes, makes me afraid to try, so I continue to type the password each time.

CODECS to play DVDs etc. That process should be easier. I know there are legal issues, but a script to setup all, or have it there but not implemented.

Something like a Restore Point, maybe there is?

---

### Post by hellmet on 2008-01-08
I do like ubuntu a lot. But, one major thing that I've found with ubuntu an linux in general is that the OS looks like its a patch work of several different programs. Windows on the other hand looks like a completely integrated operating system. I'm not trolling, though.

---

### Post by jbonll05 on 2008-01-08
Currently running 7.04, 7.10, & 8.04b2
The only one that will easily connect my BCM43XX wifi, on my laptop, is 7.10 using restricted driver mgr. . It is fast(as wired), but has limited range. This the last piece in the puzzle for me to leave M$ completely behind. 

7.10 is on 2nd hard drive for my laptop. I am a small businessman and travel some. I have to use the factory(HP) installed XP hard drive to fully wifi. I had not used M$ for a year and a half until I bought this laptop.
JB, Ubuntu user since 5oct05

---

### Post by Yfrwlf on 2008-01-10
> **capink said:**
> There is something called wxwidgets that I belive enbale devs to write gui applications for linux and windows. It uses the native controls of both windows and gtk gui elements. 

What about a similar api or toolkit ot whatever it is called, that would allow devs to develop gui programs for both qt and gtk? with an option to compile the application using one of them.

From the [wxWidgets wiki]("http://www.wxwidgets.org/wiki/index.php/WxWidgets_Compared_To_Other_Toolkits"): "There is nothing to stop somebody writing a Qt-based implementation of wxWidgets, though wxWidgets applications can already be made to appear Qt-native using wxGTK and GTK-Qt."

I agree though that programmers should be writing code that's DE-independent, so you no longer would have to load up part of KDE to load Amarok for example.

---

### Post by Yfrwlf on 2008-01-10
> **yatt said:**
> 
6) Folder and Printing sharing. On Vista it required me a grand total of 6 clicks, IIRC. On Linux you need to get a networking degree, then sacrifice a goat to the gods. For people with multiple computers, wanting to share the printer is quite common. I know CUPS will let you share just the printer, but even that is not as elegant as it could be. Plus it requires all machines to support CUPS.

Since all you have to do is right click on a folder and select "share folder", I don't really understand your complaint.  Also, when you install a printer, by default it shares it out, or that is the default option if it asks you (can't remember).  If it's a local printer, all you do is plug it in, I don't see how it could get any easier.  If you want to adjust if a printer is shared or not, go to the "policy" tab in Red Hat's printer utility.

> **yatt said:**
> 1) Themes (in before then Ubuntu would be blue and look like everyone else). I think some of the currently shipping themes should be scrapped and replaced with something made by the Ubuntu Art Team. Open up Appearance Preferences and you will see what I mean. I am currently using the live CD and really you are left with slim pickings. Human is a good theme if you are into Orange (I personally am not), and the similar Glossy and Clearlooks. Actually, Gutsy is worse off than Feisty as Gutsy got rid of one of the better icon themes: Tango. Then there are five other themes that look about as old as the Windows 95 style. I think we should take two of the themes, Clearlooks and Human, and offer each in a bunch of colors. Have both engines offer say orange, blue, green, pink, purple, black, and of course brown. In the likely case of an 'abstract' default background (like Gutsy's), include it in each color and have the theme suggest it. Before anyone brings up Gnome-Look, how do those that do not know find out about it? The theme manager does not link there, and not everyone spends all day on this forum or Google searching ways the can mod their Ubuntu install. Nobody would look at it if it was made a default bookmark for Firefox either.

If I understand you correctly, the reason there are not lots of colors in the theme section is because that is the theme section, not the color section.  The themes combine several different controls, boarders, icons, colors, and mouse pointers to give a different "theme".  You *can* have any colors you want, just click on a theme and then click customize and change the colors of everything to whatever you want.  The gradients give you quite a big selection. :)  Perhaps this layout is a little confusing to new users though, and they may think the same thing (if that's the way you understood it) and be confused by the lack of colors and think that the options are very limited.  Perhaps a few more themes should be created and placed into the themer which simply add a few more colors to get around this problem, but at the same time the developers are probably thinking that if they do then the user will have an even *worse* chance at finding the colors selection area.  Maybe what really needs to change there is the layout to give better access to the color and other settings, perhaps provide the theme customizations as "sub tabs" so they get more easily noticed and accessed instead of having to open a new window.

> **yatt said:**
> Python would be a good for the job. The default python tutorial is pretty good. Lots of people recommend Dive into Python, but it is a bit advanced. I'd only recommend it if you have had some previous programming experience. I'd probably just use Gtk.

I've heard Python is supposed to be pretty easy/nice as well and will look into it, thank you.  wxWidgets looks like it may be fairly simple as well, so I might try it out and see how it works within both KDE and Gnome.

> **twin_57103 said:**
> Here are a few ideas:

A GUI for common configuration needs, especially a 5-button mouse.  If Ubuntu is to increase in mainstream use, the user should not have to manually edit configuration files after wading through internet posts to figure out how.  Also, support 5-button mice without post-installation configuration.

Easier installation of non-repository software (as in the original post).  Also, keep the repositories more up to date.  The versions in the repositories are often old and installing non-repository software can be a beast.

A reboot to other OS option - would be helpful for those of us who dual-boot.  I believe this exists in other distros?  Perhaps this could be a post-installation add-on.

Better help files, documentation, and manuals!!  Help files are often underdeveloped and sometimes completely useless.  I know this has more to do with the individual program developers than the OS as a whole, but it is a major oversight.  I've tried to learn some of the Gnome Games only to have to go to the internet to find out what to do because there was so little in the help files!

I'm not sure why the package maintainers for some of the repository packages let them get so out of date when there are specific 7.10 packages on the program's website in many cases that are more up-to-date.  Not sure why whoever makes those packages don't upload them to the 7.10 repository as well.  In any case, and much more importantly, if the Linux packaging mess was fixed, repository maintenance would no longer be an issue, because there could be one universal repository, or several mirrored universal Linux repositories.  Wouldn't that be grand.  We need to work together against Microsoft, not fracture ourselves. :)

The reboot to other OS option, you could just move the default OS setting in the grub conf before rebooting.  Problem is, that would be the new default, so how would you move it back, and what would you do where there was more than one other OS?  I wonder how the other distros do it.

Any way, fully agree about the mouse thing, mice are simple devices so you'd think that implementing a nicer mouse settings GUI wouldn't be too difficult.  I'd love to see an image of a mouse with the same number of buttons as the one(s) detected, and allow you to define the action for each button.  Seriously, one thing that really makes Linux great is a fairly simple underlying system of files that makes doing a lot of tasks easier, so just writing the GUI interface to change the settings seems like it would be cakewalk, and I really don't understand why user interface devs haven't done a lot more with settings, unless having a mouse configuration GUI would go against Gnome's simplicity ideologies, or I'm missing something.

> **allforcarrie said:**
> IN the apperance settings, there could be a button that says "get mroe themes" and directs you to gnome-look.org or respective window managers.

Awesome and simple idea! :)

---

### Post by reiki on 2008-01-10
For installation:

Ask me all the darn questions up front. Ask me to fill out a form or something. Even if you ask for stuff you don't ultimately end up needing for the install. 

Why?

So that I can sit down, fill out a "form" (or whatever) and then say "Install" and I can walk away. And I won't come back a half hour or 45 minutes later and see a dialog box waiting for me to type my name or my time zone or some such nonsense and find out that it popped up right after I walked away and I still have another 40 minutes to go on the install.

This is something that always twisted my twitters about any windows install. Yeah I know about the "unattended install" procedures for windows. But let's make it EASY on home users who aren't going to be able to figure all that stuff out. Just present it up front and then tell me to go have a coffee and pastry or something.

---

### Post by Endolith on 2008-01-10
> **Yfrwlf said:**
> I agree though that programmers should be writing code that's DE-independent, so you no longer would have to load up part of KDE to load Amarok for example.

Or the DE developers should be writing code that's more portable to other things, like GNOME VFS.

---

### Post by Endolith on 2008-01-10
> **Arkenzor said:**
> So, I think a simple welcome message in the console telling you about man and apropos would already be an awesome help, just like a noob-friendly basic guide to the command-line

And use something like [fish shell]("http://fishshell.org/") for the default in gnome-terminal.

> maybe a simple notice in Synaptic after installing programs "This package installed the following command-line commands: <Files installed in /usr/bin>. The list of all the files that were installed can be found under Installed Files in the package properties

Good idea.  But doesn't the "Add programs" version of synaptic kind of do that?

---

### Post by Yfrwlf on 2008-01-10
> **reiki said:**
> So that I can sit down, fill out a "form" (or whatever) and then say "Install" and I can walk away

I'd agree, but isn't this the way things are now, you fill out all the information and then after the partitioning it starts copying the files and then it's done?  This is vastly different from XP, where you do stuff, it copies the files, then you do more stuff, it does some things, then you have to do more stuff again.  It's actually been quite a while since I've done a Ubuntu install though so I might be forgetting something.  Shows you just how much re-installation I've had to do with which OSes. :lolflag:

> **Endolith said:**
> Or the DE developers should be writing code that's more portable to other things, like GNOME VFS.

I agree that things should always be more modular, but allowing the easy creation of different versions would not be as good of a fix as writing one version that can work in any DE to begin with, and even better on any platform, so wxWidgets seems like an amazing accomplishment to me. :)

---

### Post by cardinals_fan on 2008-01-10
I am very fond of the Zenwalk distro (it's dual booted with Xubuntu on my machine) and run the Live version occasionally just for a change of pace.  One thing that amazed me was how easy it was to set up my wireless card!  Installing the rt73 drivers from serialmonkey was the same as on Ubuntu, but connecting to the network, using the wifi-radar tool, was really easy.  Compare this to network manager (NM), possibly the most frustrating program ever written!

Many have already mentioned a dissatisfaction with NM, and I agree.  Removing it would be a really nice addition to Ubuntu.

---

### Post by Linuxratty on 2008-01-11
> **aysiu said:**
> You don't make a TV's insides easy to understand for normal folks. You make the TV's *outsides* easy to understand for normal folks. You make the TV's insides easy to understand for *TV repair people*.


The obvious solution is to make it so that consumers do, in fact, have no business messing with production and maintenance *unless they desire to learn those things*. Reorganizing the filesystem hierarchy is surgery when only a bandage is needed.

Nail whacked on the head...I could not have said it better!=D>
 I have no interest whatsoever in learning pages of strange commands to make old Gozz here jump through a hoop of virtual fire  and open a file,for me...None,zero...
 I like Linux,it fascinates me,but a lot of this stuff is on a need to know basis and I really don't need to know it...Some things are worth learning,some not.
 I have better things to do with my time than to scower though forums looking for some obscure command so Gozz will do my bidding...
 And i agree with what others have said too...There has to be a better way,an easier way.
 Linux users have harped on this stuff for years..It's not new info. .

---

### Post by Roasted on 2008-01-11
I think we've had enough eye candy for the time being. I think it's time you take the existing platform of Ubuntu and go balls to the wall with making it a more well rounded and well supported operating system. It's already great as is, but it's really upsetting to have a Linux Desktop and XP Laptop. I want a Linux Laptop, damnit! 

Complaints with my laptop - lack of sound and wireless support. I've spent countless hours trying to get it to work and I have not succeeded yet. In fact, I won't succeed. Using XP is just plain easier at this point. So... Ubuntu developers... I love the OS, it'll forever be on my desktop, but damnit I want it on my laptop too!!!! 

:guitar:

---

### Post by yatt on 2008-01-11
> **Yfrwlf said:**
> From the [wxWidgets wiki]("http://www.wxwidgets.org/wiki/index.php/WxWidgets_Compared_To_Other_Toolkits"): "There is nothing to stop somebody writing a Qt-based implementation of wxWidgets, though wxWidgets applications can already be made to appear Qt-native using wxGTK and GTK-Qt."

I agree though that programmers should be writing code that's DE-independent, so you no longer would have to load up part of KDE to load Amarok for example.
Amarok is part of KDE, why wouldn't it be dependant on KDE? If it where not to be KDE dependent, with what should it replace all the KDE components it uses?

---

### Post by Yfrwlf on 2008-01-12
> **cardinals_fan said:**
> I am very fond of the Zenwalk distro (it's dual booted with Xubuntu on my machine) and run the Live version occasionally just for a change of pace.  One thing that amazed me was how easy it was to set up my wireless card!  Installing the rt73 drivers from serialmonkey was the same as on Ubuntu, but connecting to the network, using the wifi-radar tool, was really easy.  Compare this to network manager (NM), possibly the most frustrating program ever written!

Many have already mentioned a dissatisfaction with NM, and I agree.  Removing it would be a really nice addition to Ubuntu.

Then it'd be nice to install those programs in Ubuntu.  I hope they are modular enough so that you could do so.  On a truly great OS, you could easily go get that software and install it alongside, or at worse replace your existing similar program, with your new one if you preferred it to the stock program.  Linux should be that modular OS.

> **yatt said:**
> Amarok is part of KDE, why wouldn't it be dependant on KDE? If it where not to be KDE dependent, with what should it replace all the KDE components it uses?

rant: If everything was modular and standardized APIs were used, it could use the Gnome version of those things it needs to run without having to load up the KDE versions.  It's challenges like these that I think need to be worked on to make Linux modular and improve application desktop environment and distro portability.  If things continue getting less modular, what you'll see is an continuing increase in bloatedness for the "Linux OS".  When each program you wish to run is only compatible with an extremely specific and anal undercarriage instead of being modular enough to share and recognize and play nicely with other existing systems, your OS will grind to a halt, and Linux will die.  Trying to create standards and modularity is the only way to keep Linux alive, functional, powerful, and compatible, and it would also definitely make sharing Linux programs between distros much easier, the way it should be.

Take Amarok's sound engine for example.  You should be able to load up Amarok and have it use the existing loaded engine, and only change that if you wish to do so in the options or whatnot.  Having this ability means that sound engines now get to directly compete with each other.  You can test them, figure out which one you like best and functions better, and it just helps the Linux ecosystem as a whole to have true modularity.  Using a sound system was probably not the best example, since I do believe some of them may use some standard methods of communication, which of course is good if so.

What if Open Office was integrated heavily with KDE libraries?  Can you imagine it taking even longer for it to load up in Gnome, and requiring an even bigger memory footprint?  Linux is completely customizable and transparent with open source code, and this gives us the power to do incredible things with it, but **only if we choose to do so**.  Thus we should all work together to make it a better operating system, not a worse one.  Programs should be getting more streamlined and faster, and the usability and modularity of the system allowing for incredibly easy program sharing, comparing, installing, and use in general should get better and better.  Anything that prevents that from happening ties Linux down and makes us all less free, not to mention makes it less able to compete as the best OS, so we should use our brains to try to prevent bad things like that from happening.  I don't want Linux and the programs that run on it to die.  Heck, I'd love to see Herd be completely compatible as well so that you can easily replace the Linux kernel with it, allowing the kernels to compete.

"Linux" should be a platform, and all that platform needs to have to make it a platform is a common set of APIs, a common agreement of how programs should communicate with each other.  Everything else should be fully modular and swappable around those APIs.  A good test of an OS is it's ability to stay defragmented over time.  Programs are just icing on the cake, the real power is in standard APIs so that programs *can* be created, and *can* compete, without any of this lock-in crap like packaging format problems.

My fear is that Red Hat, Suse, Ubuntu, and other big distros may not care about major problems like these as much because they don't want to see them resolved.  If they have vested business interests, which they do, they may very well like to see their distro have this or that perk that you *can't get* on other distros (or at least, is very difficult to get, especially for the average user), so they can try to make their distro more proprietary and lock in users.  A distro should not be based on the features it has, but a taste for a certain selection of programs.  [COLOR="Red"]You should not have to change distros just to get access to a particular program or feature.[/COLOR]  Sure, I can go chase down a bunch of dependencies and try to compile the damn thing from source, but I shouldn't have to.  Even if the current state of Linux hasn't reached such an extreme state of distros being very proprietary and being mostly incompatible with anything outside their overseeing business, that doesn't mean it's not heading that direction.  Everyone should make an effort in correcting these kinds of problems and should be weary of efforts to fragment Linux.  Linux companies need to have an interest in seeing *Linux* succeed, not *their Linux distro* succeed.  Think that conflicts with their business model?  If it does, they need to restructure it.  Linux should be a pool of users and developers coming together to get software they want for a standardized platform, not a business model that tries to rely on distro fragmentation.  I hope Mark Shuttleworth knows this.

/rant

---

### Post by cardinals_fan on 2008-01-12
Actually, I did install wifi-radar in Xubuntu.  It works very nicely :-)

---

### Post by Linewbie on 2008-01-13
I have a suggestion, there's Linux software for everything under the sun, why not interactive tutorials (with practice quizzes, instructional movies) for newbies. 
I think it would be really useful, especially if there was a terminal tutorial. Maybe as a standard feature on every Ubuntu release, explaining how to use new features for experienced users, too.

My $0.02

---

### Post by Yfrwlf on 2008-01-14
> **cardinals_fan said:**
> Actually, I did install wifi-radar in Xubuntu.  It works very nicely :-)

Good, and I'm not saying it's impossible because for the most part Linux is still Linux, but we need to make sure that that modularity stays in place and the biggest obstical is cross-distro package installation IMO.  You probably had to compile that program after finding dependencies, or were you lucky enough to find a package that installed itself correctly, or a binary that required no installation?

> **Linewbie said:**
> I have a suggestion, there's Linux software for everything under the sun, why not interactive tutorials (with practice quizzes, instructional movies) for newbies. 
I think it would be really useful, especially if there was a terminal tutorial. Maybe as a standard feature on every Ubuntu release, explaining how to use new features for experienced users, too.

My $0.02

Awesome idea but would require quite a lot of space for a CD so you could stream a video from YouTube or someplace else instead, or install them from the repos or something.

---

### Post by cardinals_fan on 2008-01-14
> **Yfrwlf said:**
> Good, and I'm not saying it's impossible because for the most part Linux is still Linux, but we need to make sure that that modularity stays in place and the biggest obstical is cross-distro package installation IMO.  You probably had to compile that program after finding dependencies, or were you lucky enough to find a package that installed itself correctly, or a binary that required no installation?

Actually, I think that I found it in the repositories ;).  Fortunately, I managed to get my wireless dongle working without wifi-radar, otherwise I wouldn't have been able to install it.

---

### Post by 23meg on 2008-01-14
> **Linewbie said:**
> I have a suggestion, there's Linux software for everything under the sun, why not interactive tutorials (with practice quizzes, instructional movies) for newbies. 
I think it would be really useful, especially if there was a terminal tutorial. Maybe as a standard feature on every Ubuntu release, explaining how to use new features for experienced users, too.

My $0.02

There are some websites with lots of (non-interactive) video tutorials.

[http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/)
[http://www.ubuntuvideo.com/](http://www.ubuntuvideo.com/)
[http://ubuntuclips.org/](http://ubuntuclips.org/)

---

### Post by tad1073 on 2008-02-01
> **saulgoode said:**
> The Linux kernel offers you the choice of whether to retain applications in memory versus having that memory available for caching. The value in /proc/sys/vm/swappiness will determine this. Change the value to "0" if you prefer that you huge app (and its data) are kept in memory when you switch to another process; or use "100" if you want that app transferred to swap. Or any number in between to provide a reasonable compromise.

Exactly what do I need to put in this file to use more swap and less memory. statement=value? or just value? i only have 256mb ram so I allocated 2gb to swap but am only using 1% of swap as of now.

---

### Post by roderick on 2008-02-01
> **tad1073 said:**
> Exactly what do I need to put in this file to use more swap and less memory. statement=value? or just value? i only have 256mb ram so I allocated 2gb to swap but am only using 1% of swap as of now.

Read this post:

[http://ubuntuforums.org/showpost.php?p=1255511&postcount=43](http://ubuntuforums.org/showpost.php?p=1255511&postcount=43)

---

### Post by oomingmak on 2008-02-01
> **Lord Illidan said:**
> That's because rm stands for ReMove, not delete.
So presumably rn is the command for **R**e**N**ame?

---

### Post by Lord Illidan on 2008-02-01
> So presumably rn is the command for **R**e**N**ame?

No..
rename - ```
rename
```

I know, naming conventions suck.

---

### Post by ashmew2 on 2008-02-02
Well  , I just think that priority SHOULD be given to wireless and things like Yahoo! Messenger or any other VERY Popular programs/hardware. If Wireless and the Other Major Programs work flawlessly.. There would be a large number of users running Ubuntu  , Or Linux in general And that would mean that larger companies , like ATi , Nvidia would concentrate on making Fully Compatible Linux Drivers. They might even release the source code if they found it feasible.

---

### Post by bufsabre666 on 2008-02-02
> **ashmew2 said:**
> Well  , I just think that priority SHOULD be given to wireless and things like Yahoo! Messenger or any other VERY Popular programs/hardware. If Wireless and the Other Major Programs work flawlessly.. There would be a large number of users running Ubuntu  , Or Linux in general And that would mean that larger companies , like ATi , Nvidia would concentrate on making Fully Compatible Linux Drivers. They might even release the source code if they found it feasible.

if the SEC allows microsoft to buy yahoo dont ever plan on a port of yahoo messenger, and trust me the wireless thing is getting better, even my laptops wireless card that was the demon seed of all hardware has restricted drivers now

---

### Post by ashmew2 on 2008-02-02
whats the SEC ? And are they gonna give proprietorship to soleley Microsoft ?
Even if they do , We can still make Open Source Software  like Gaim or Kopete but specifically for Yahoo and all the features .. Cant we ?

---

### Post by bufsabre666 on 2008-02-02
> **ashmew2 said:**
> whats the SEC ? And are they gonna give proprietorship to soleley Microsoft ?
Even if they do , We can still make Open Source Software  like Gaim or Kopete but specifically for Yahoo and all the features .. Cant we ?

the SEC is the united states security and exchange commission, they monitor business ethics of public companies and prevent monopolies but yes you will still be able to use the 3rd party ims cause the odds that they care ganna change their login servers is very unlikely

---

### Post by days_of_ruin on 2008-02-02
I completely agree with the removable drives.That has to be my biggest complaint about ubuntu.

---

### Post by Statix0 on 2008-02-03
Probably been mentioned, but I was really annoyed when updating from feisty to gutsy and a dialog box popped up (I don't even remember what it was) that asked me to click okay or whatever. I wasn't there at the time, and the dialog box stopped my whole update. Annoying. Should have a timeout on them or something that autoaccepts 10 seconds in.

---

### Post by stek79 on 2008-05-03
> **saulgoode said:**
> The Linux kernel offers you the choice of whether to retain applications in memory versus having that memory available for caching. The value in /proc/sys/vm/swappiness will determine this. Change the value to "0" if you prefer that you huge app (and its data) are kept in memory when you switch to another process; or use "100" if you want that app transferred to swap. Or any number in between to provide a reasonable compromise.

Hi,
  too bad the reported Vista precaching behaviour is a winner in this area, with Linux we are still behind it.

Your response is not correct in that point, since swappiness parameter does NOT address the problem of prefetching things in RAM.

It is true, with the current state of things we have not a smart prefetching kernel solution in Linux - so you can have GBs of RAM UNUSED. 

There is a nice userlevel tool to overcome this which is 'preload', that I've installed in ubuntu with great pleasure - I reccomend it to everyone.

Some months ago it was advertised that in Hardy would have been included a true solution to that problem, which is currently avalable - albeit not very tested I think - which is 'preload'. This is a kernel patch that attempts to detect IO page behaviour and to predict it - something like Vista Superfetch, I think.

Too bad that kernel patch has been removed from Hardy, so actually now the problem is still there. 

Let's hope in the future the prefetch project will gain some more attention, I really think it can enhance a lot the user experience, with great improvements regarding application performance.

---

### Post by stek79 on 2008-05-03
> **stek79 said:**
> Hi,
  too bad the reported Vista precaching behaviour is a winner in this area, with Linux we are still behind it.

Your response is not correct in that point, since swappiness parameter does NOT address the problem of prefetching things in RAM.

It is true, with the current state of things we have not a smart prefetching kernel solution in Linux - so you can have GBs of RAM UNUSED. 

There is a nice userlevel tool to overcome this which is 'preload', that I've installed in ubuntu with great pleasure - I reccomend it to everyone.

Some months ago it was advertised that in Hardy would have been included a true solution to that problem, which is currently avalable - albeit not very tested I think - which is 'preload'. This is a kernel patch that attempts to detect IO page behaviour and to predict it - something like Vista Superfetch, I think.

Too bad that kernel patch has been removed from Hardy, so actually now the problem is still there. 

Let's hope in the future the prefetch project will gain some more attention, I really think it can enhance a lot the user experience, with great improvements regarding application performance.

Errata corrige, the current kernel patch I was referring to is the 'prefetch' project, started as a Google Summer of Code in 2007 - 'preload' is the userspace tool, which is currently available in Ubuntu.

---

### Post by munky99999 on 2008-05-04
I'm rather quite impressed with ubuntu obviously or I wouldn't use it :)

First problem I had was my tv tuner. It was a cheap card which was buggy in windows to start. Apparently mythtv and such has no problem working with the tv tuner; but I didn't bother. I just bought a tv :)*FIXED*

Second problem. ATI card. I had integrated graphics up until my first video card a nvidia riva tnt card. Which worked well enough. My second video card was ATI and it performed so well for so long. So I have been loyal to ATI but DAMN ATI drivers in ubuntu are so bad. It's so sad seriously.In gutsy I had opengl support but no 3d acceleration. In hardy now I have both opengl support and 3d acceleration. However 1440x900 resolution is all messed up. Which sucks.

third problem. Firefox 3 beta 5 bookmark default folder and separator can't be changed/removed :(

Fourth problem. Gimp's setup ought to be setup similar to that of photoshop. Refinding all the different tools is going to be annoying :)

fifth problem. This one is an actual problem.Not just an annoyance. Adobe flash player doesnt work in hardy heron. I've tried many different options. Only gnash works but that's really bad quality.

---

### Post by K.Mandla on 2008-05-04
Moved to Testimonials and Experiences.

Keeping in mind, of course, that this thread is a bit out of date.

---

### Post by roderick on 2008-05-04
> **munky99999 said:**
> I'm rather quite impressed with ubuntu obviously or I wouldn't use it :)

First problem I had was my tv tuner. It was a cheap card which was buggy in windows to start. Apparently mythtv and such has no problem working with the tv tuner; but I didn't bother. I just bought a tv :)*FIXED*

Second problem. ATI card. I had integrated graphics up until my first video card a nvidia riva tnt card. Which worked well enough. My second video card was ATI and it performed so well for so long. So I have been loyal to ATI but DAMN ATI drivers in ubuntu are so bad. It's so sad seriously.In gutsy I had opengl support but no 3d acceleration. In hardy now I have both opengl support and 3d acceleration. However 1440x900 resolution is all messed up. Which sucks.

third problem. Firefox 3 beta 5 bookmark default folder and separator can't be changed/removed :(

Fourth problem. Gimp's setup ought to be setup similar to that of photoshop. Refinding all the different tools is going to be annoying :)

fifth problem. This one is an actual problem.Not just an annoyance. Adobe flash player doesnt work in hardy heron. I've tried many different options. Only gnash works but that's really bad quality.

WIth ATI and nVidia, your drivers will be suspect if you use the Open Source ones as they have a way to go yet. The Intel ones rock, though.

If you have a recent ATI or nVIdia though, you can try the proprietary drivers by enabling the restricted drivers support. No need for Intel, as the drivers for Intel are open and free and developed with Intel support - go intel.

---

### Post by munky99999 on 2008-05-04
> **roderick said:**
> WIth ATI and nVidia, your drivers will be suspect if you use the Open Source ones as they have a way to go yet. The Intel ones rock, though.

If you have a recent ATI or nVIdia though, you can try the proprietary drivers by enabling the restricted drivers support. No need for Intel, as the drivers for Intel are open and free and developed with Intel support - go intel.

I do have the restricted drivers in action.

---

### Post by starcannon on 2008-05-04
I appreciate that Canonical wanted to get Bulletproof X off the ground, I'm just not convinced it was ready yet.

A) Help is not readily available (many of us have never used BPX yet)

B) On the 4 machines I've upgraded to 8.04 the failsafe mode crashes so I do not get the nice little gui widget. If I use Ctrl-Alt-Backspace nautilus crashes.

C) I can not find documentation easily, or haven't yet found any on how to tweak the "Configured Devices" (not just the "Configured Device") I am putting options in the appropriate places anyway though, and for the most part that seems to work.

I guess what I really dislike about Bulletproof X is the lack of tutorials, or user friendly documentation, it sadly at the moment doesn't quite live up to its name, I know that it will get there, but its not there today, better documentation would be a huge plus right now. I'm also not convinced that dumbing down X is the correct course to take. But I am likely an outdated thinker on the subject, and I know that the mission is a good one, just not sure if the method is working.

---

### Post by roderick on 2008-05-05
> **starcannon said:**
> I appreciate that Canonical wanted to get Bulletproof X off the ground, I'm just not convinced it was ready yet.
...
I guess what I really dislike about Bulletproof X is the lack of tutorials, or user friendly documentation...

[https://wiki.ubuntu.com/BulletProofX](https://wiki.ubuntu.com/BulletProofX)
[https://wiki.ubuntu.com/DisplayConfigGTK](https://wiki.ubuntu.com/DisplayConfigGTK)
[http://www.madpenguin.org/cms/?m=show&id=8040](http://www.madpenguin.org/cms/?m=show&id=8040)


Google is my friend and yours too :)

Bulletproof X is simply a GUI frontend to the commandline reconfigure for generating a xorg.conf file. It runs display config in a safe way (in vesa mode). If you have buggy or poorly supported hardware, this may or may not be any help - no more than a commandline option would.

Bulletproof X is not supposed to require docs - its an automation. At least my take...

---

### Post by starcannon on 2008-05-05
> **roderick said:**
> 

Google is my friend and yours too :)



Yeah I know, me, Chuck Norris, and Al Gore invented Google :biggrin:

Seriously though, thanks for the links, I kept googling into outdated forums that were closed.

---

