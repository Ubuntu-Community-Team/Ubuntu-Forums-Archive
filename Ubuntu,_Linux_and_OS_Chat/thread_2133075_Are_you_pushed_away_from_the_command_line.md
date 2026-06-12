---
title: "Are you pushed away from the command line?"
date: 2013-04-06
forum: Ubuntu, Linux and OS Chat
---

### Post by Rukiri on 2013-04-06
I'm not, I run Linux from scratch and Gentoo boxes but I'm talking about distros like Ubuntu where everything is graphical.  Now I understand the reasoning behind it and it's slogan "Linux for human beings" and why ease of use is important, but the command line should not be shoved away.
Granted I actually have to use the command line just to get past the first installer page (I think ubunter server solves this as I don't have to install it via gui, cli is better imo)

Do you think you're pushed away or closer to the command line, I always have it open or multiple depending on my workload.

---

### Post by cariboo on 2013-04-06
I still use the terminal on the desktop, when I feel like it, even though almost everything can be done using a gui app. I do the majority of my server administration remotely via the command line, as the server doesn't have a gui.

---

### Post by ibjsb4 on 2013-04-07
The complexity of the command line vs the simplicity of the GUI?

Who wouldn't push the command line away?

---

### Post by vasa1 on 2013-04-07
> **Rukiri said:**
> ..., but the command line should not be shoved away. ...
*Shoved away* by whom? I don't understand :(

---

### Post by andrewrz on 2013-04-07
I do sometime hesitate between using gui and cli . of course nothing will replace the terminal for efficiancy. also support and instructions will always fallback on cli because more systems are likely to share a cli command and you can cut and past them. so I think it's ok to take a break in the gui sometimes as long as you go back to the cli when it makes a differnce.

---

### Post by prodigy_ on 2013-04-07
> **ibjsb4 said:**
> The complexity of the command line...
...is just a perception issue. There's nothing complex about CLI.

---

### Post by buzzingrobot on 2013-04-07
> **Rukiri said:**
> ... the command line should not be shoved away.

This is something of a misnomer that is often trotted out, but isn't accurate.

I'm not aware of *any* Linux distribution that has actually removed the venerable character-based toolset. It's certainly there in Ubuntu for anyone to use, if they choose.

There is nothing in the use of command-line tools that is intrinsically virtuous. The command line is just one way of gathering user input. A GUI is another way. Once that information is acquired, the system deals with it in the same way. 

Command-line functionality is often more extensive because those tools often offer a wider range of options. However, there's nothing inherent in a GUI that prevents its inclusion of every available option.

Another factor is the ability to pipe the output of one command line tool into another. This is the much vaunted "one simple tool for one simple task" approach.  It has its limits, though, and doesn't really apply to modern applications. (Or, for that matter, to character-based applications developed soon after Unix hardware began to acquire more power and more memory.)  For example, the concept of a browser or an office suite constructed as a pipeline of simple character-based tools is silly.

Neither approach is really "closer" to the OS, as is often claimed for the command line. Learning to configure and manipulate a Linux system via the command line teaches you to do just that:  Use the command line to configure and manipulate a Linux system. It does not teach you how the system works. E.g., disabling a service in a GUI, or disabling a service by editing an init script, are just two different ways to tell the system to do something.  If a user wants to understand how services work, how the init process works, etc., the user needs to study Unix/Linux OS design.  He won't learn it from using a text editor to edit boot scripts in /etc.


My first OS was Unix, by chance, and I've used Linux and/or the BSD's since the early 1990's.  I suppose I can wing my way around the command line as well as almost anyone. And, I do when I need to.  But, most of the time I am quite happy to let the GUI tools handle the boring, mundane, grunt work. Could I partition my disks with fdisk/parted?  Sure. Done it dozens of times.  Could I write little backup shell scripts around rsync and trigger them via crontab?  Sure, I've done that.  But, if an installer's partitioning routine gets me to the same place, or a GUI wrapped around rysnc that generates its own script and plugs it into crontab works, I'm going to use them and save a bit of time for the other important things in my life.

---

### Post by glln0v on 2013-04-07
> **Rukiri said:**
> 
Do you think you're pushed away or closer to the command line, I always have it open or multiple depending on my workload.

I exclusively use Ubuntu. It's the only linux distro I've ever used. and I use the CLI all the time. I bought a book to help expand my use of it. 

I came from Windows to Ubuntu. I knew absolutely nothing about the command line when I first came to Ubuntu and even had no interest in learning how to use it. Yet I somehow learned a bunch just by virtue of using Ubuntu and I continue to grow more and more compentent with it. Ubuntu, in my experience, is a great way to transition to learning how to use the command line.

Despite my increasing use and competence with CLI, I still find that I prefer GUI for a lot of things. But it's not that I don't know the CLI way of doing it.

---

### Post by prodigy_ on 2013-04-07
> **buzzingrobot said:**
> There is nothing in the use of command-line tools that is intrinsically virtuous. The command line is just one way of gathering user input. A GUI is another way. Once that information is acquired, the system deals with it in the same way.
While in theory it's true, in practice it's wrong. GUI tools (whether Linux of Windows) tend to be less transparent as to what they *actually* do, worse documented and often unfit for scripting.

---

### Post by llanitedave on 2013-04-07
I've never had any trouble finding the terminal.  Where's the "push away"?

---

### Post by ibjsb4 on 2013-04-07
> **prodigy_ said:**
> ...is just a perception issue. There's nothing complex about CLI.

> vs the simplicity of the GUI?

Only when taken out of contents  :)

---

### Post by glln0v on 2013-04-07
The hard thing about CLI is human memory. You have to remember the command, remember the syntax, etc. If you use the command a lot, you learn it. But stuff you only have to use once in a while creates problems because you constantly have to consult the manual to remember. This is where GUI becomes a real advantage.

---

### Post by oldos2er on 2013-04-07
> **glln0v said:**
> The hard thing about CLI is human memory. 

Thankfully bash has a far better memory than I do.

---

### Post by dillonboardman on 2013-04-07
I personally find the terminal to be very natural to use. It's nice and efficient.

---

### Post by Gyokuro on 2013-04-07
I'm most of the time at the command prompt and that does not change - I have only GUI for browsing, checking emails & blogs. However I grow up with the command prompt therefore I feel  myself at home in a shell environment. Vim and some other fine tools are my daily tools.

---

### Post by Algus on 2013-04-07
CLI only looks intimidating.   It is quite easy to use though it is certainly not as intuitive as a GUI or as recognizable since Linux is way different from DOS whereas a Linux Window generally behaves the same way as an OS X Window or a Windows Window.   I used Linux for many years without really understanding the terminal and the great thing about distros like Mint and Ubuntu is that it is entirely possible to avoid the terminal and still have an excellent working environment for your computer.    

Now that I know the CLI better and enjoy tinkering a bit more I am happy to do so but I really hope we don't lose distros like Mint and *buntu.  Arch and Slackware may not be for everyone, but I do believe that Linux in some form can be an OS for everyone.

---

### Post by Moose on 2013-04-08
I actually use the Terminal whenever I can. It's just an 'ease of mind' sort of thing.

---

### Post by montag dp on 2013-04-08
Absolutely not. It's one of the things I like best about Linux. If my distro ever dumbs it down like Windows, I will switch, but I don't see that happening.

---

### Post by Irihapeti on 2013-04-08
Sometimes I use it, sometimes I use a gui - it depends on what I'm doing, and occasionally on my mood.

Definitely, the terminal is just as easy for me to find now as it was in the past - it's not like it's been mysteriously hidden in some dark corner.

---

### Post by buzzingrobot on 2013-04-08
> **prodigy_ said:**
> While in theory it's true, in practice it's wrong. GUI tools (whether Linux of Windows) tend to be less transparent as to what they *actually* do, worse documented and often unfit for scripting.

I don't see any difference between clicking in Nautilus or Dolphin versus executing, say, "ls -l'.  In both instances, an interface is collecting input from the user and then parsing and passing that input along to code that generates the (presumably responsive) data, and sends it back to the shell (both Bash and the GUI are shells) for display. Neither approach is more or less transparent than the other.

Lack of adequate documentation is a problem across Linux. It's often done late, or not at all, and often by developers writing for other developers. The command line tools that make up the basic Unix tool set are decades old, and their man entries have been tweaked over time.

Fitness for scripting is generally irrelevant unless you are working with a character-based shell like Bash. (Unless you're working in OS X using Applescript or Automator.)

Learning to use character-based shells and tool sets is certainly a fine way of expanding your horizons.  Personally, though, I don't see any reason to work harder using those tools when I can accomplish the same thing in a few seconds with a GUI tool. (I can prepare a pretty good lasagna, too, but I'd rather go out and order it at a restaurant.) 

In the end, there's no virtue attached to the use of either approach, and using the command line certainly doesn't make someone a better Linux user. It just makes them someone who uses the command line.

---

### Post by neruson on 2013-04-08
As far as package management goes I don't use it very often in my Xubuntu install on my desktop, but once it's set up I really don't mess with it very much. Just updates really which I do through a GUI. I could do it via the command line (it is faster) but honestly I'm not a huge fan of APT, I mean it works - it's never given me any problems, but the commands themselves have always felt a little awkward to me. It's a personal gripe not a knock against the system itself. I still use Aptitude with Xubuntu as opposed to apt-get. It works better for me.
 
On my laptops that run Fedora & Arch Linux I always use the command line (with Arch I obviously have to, it's all CLI, which I don't mind. I find pacman to be wonderful). I use it with Fedora because yum is just so simple and even as a Fedora lover I even have to admit that Gnome PackageKit leaves a lot to be desired although it does work.

But as far as writing bash scripts I always use vi and when I'm tweaking my OS itself I always use nano when editing config files.

I do think Linux users should try to become knowledgeable of the command line. You don't need to be a guru or anything, but understanding the basics is important. There's been so many times when, due to various mistakes I made, that I couldn't even load a graphical environment. If I didn't know anything about the command line after hitting Alt-F2 to get to the CLI interface I would've been screwed and had to reinstall.

---

### Post by Giraffemonster on 2013-04-08
I wouldn't really say that I'm 'pushed away', even though I'm not so good with bash scripting. Rather, I don't mind using it. If there's a GUI which actually looks pretty nice and is quick to use, then of course I'd prefer that.

I think I used the terminal even more when I was just getting introduced to Linux. The reason was because my computer was extremely old and slow. Even GTK based programs like Ubuntu Software Center would absolutely *kill* my system, so I was pretty much forced to. I'm pretty happy with my new setup though.

---

### Post by pfeiffep on 2013-04-08
The cli and gui both have their place, I use both depending on the situation. I find it much easier to use a gui interface to search for a package that i 'loosley' remember it's name, but prefer the preciness of apt-get over synaptics. One reason I prefer Linux over Windoze is it's more transparent.

---

### Post by thiebaude on 2013-04-08
And copy and paste helps too,lol

---

### Post by deadflowr on 2013-04-08
No I'm not pushed away from the command line.

I really like having multiple tools.

We have over twenty flathead screwdrivers laying around the house, varying in different sizes.

I have, maybe, only needed to use four or five of them, but having the extras around is somewhat reassuring.

The terminal and command lines feel the same.

---

### Post by TeamRocket1233c on 2013-04-09
No way, I go into the terminal actually pretty often in Ubuntu, although the Software Center and Synaptic are still there as options as well, but no matter how GUI-centric a distro may be, you just can't get away from the command-line, as there's some stuff that doesn't give you any choice other than to get your hands dirty, case-and-point, adding PPAs, for example, if you wanna install Cinnamon, MATE, and e17 in Ubuntu, you gotta go into the terminal and add the PPAs and update a couple times first, then install the DEs.

---

### Post by buzzingrobot on 2013-04-09
> **TeamRocket1233c said:**
> ...there's some stuff that doesn't give you any choice other than to get your hands dirty, case-and-point, adding PPAs, for example...

You can add the URL's via Software Sources, as well.

The reason GUI's often offer fewer options than command line versions is because their developers choose not to include the options.  GUI's are not intrinsically less capable than their character-based cousins.  Too many people, though, incorrectly correlate ease of use with fewer options.

---

### Post by teacher.japan on 2013-04-09
It depends what kind of user you are.
Firstly, as a UNIX user, you should know your way around the command line, atleast the basics.  

However, we have to think of the general user, one of the things I would like see is Linux stepping in the Desktop market(don't fool yourself, it still hasn't).
For those individuals, we have to present some sort of GUI alternative to configuring files etc.etc.  
It's also helpful in other situations, I've seen DBA's begging for some sort of basic motif to set up oracle(11g) as things get pretty complicated and command line is something that has the possibility of inducing errors at times.

Look, it's a matter of common sense, how many of you would like to ask someone new to install Gentoo..or let's say Arch..or even Slackware as opposed to Ubuntu or Mint or Mageia etc.  Command line presents a challange to people that don't know it, it has a steep learning curve, after which it becomes a piece of cake.
It all depends on the level of comfort, hell, 90% of the times I'm seeing people editing files with gedit or pico or nano on tutorials posted here.  I use VI becasue at work, we had NOTHING but a base install, no gui, and the only text editor is VI..so I had to learn it and I'm very thankful for it now.

So it's a matter of comfort, however if you like linux and would like to understand it well, then learn how to work with the shell and that time investment will be worth it.

---

### Post by ka55o5 on 2013-04-09
> **glln0v said:**
> You have to remember the command, remember the syntax, etc.> **oldos2er said:**
> Thankfully bash has a far better memory than I do.
Right, but it would be nice if $ ***history*** had a GUI, or some kind of a bookmark system - or something (?); there are 100s of commands that I need/use and rly **no** (nice and easy) way of handling it?..

PS.
Hm looks like I might've found it right now, in Xubuntu, xfce4-goodies; the: xfce4-verve-plugin @
```
http://goodies.xfce.org/projects/panel-plugins/xfce4-verve-plugin
```

---

### Post by buzzingrobot on 2013-04-09
> **teacher.japan said:**
> ...how many of you would like to ask someone new to install Gentoo..or let's say Arch..or even Slackware...

Having down all that, multiple times, I'd say I'd rather use a GUI rather than put up with the tedium of the command line or curses approach, as long as the GUI lets me do what I want to do. Whether a GUI installer can or not depends on what capabilities its developers chose to leave out. As I mentioned earlier, there's nothing inherent in GUI's that make them less powerful than a command line application with the same function. GUI developers just leave options and capabilities out on the mistaken notion that doing so makes the GUI easier to use.  And that, in turn, is based on the equally false notion that GUI users are less skilled and less capable than command line users.

> Command line presents a challenge to people that don't know it, it has a steep learning curve, after which it becomes a piece of cake...


Well... I dunno.  Anything becomes easy with use and repetition. If you need to use some character-based app whose options you have not memorized, you're going to need some help, you're going to need to look things up. Just like those DBA's, who wanted help in the form of a GUI that let them simply click on the correct incantation.

As you said, if you're going to choose to use a Unix, you might as well get comfortable with the command line, because Unix is, at heart, a non-GUI, character-based, command-driven OS.

But, few people have any need or desire to confine themselves to such an environment. All the more reason to build more capable GUI's and, when they are not good enough, time to blame their developers rather than asserting that the fault is in the users.

---

### Post by tartalo on 2013-04-09
> **buzzingrobot said:**
> Too many people, though, incorrectly correlate ease of use with fewer options.
So true. I agree that having too many *elements *that you don't need in a GUI will make it more difficult to use, the problem is that if the developer decides which elements should go away she might be removing precisely what you need making it worse than "difficult" for you. The best solution, when implemented correctly, is to give *options*, to allow the user to decide which elements should be present. One example of this is Foobar2000, a music player that unfortunately only exists for Windows. By moving all the non-core functionality to plugins and by allowing the customization of the GUI it manages to be really powerful yet easy to use, because everyone can have everything needed and only what's needed.

Back to topic: Command line is great.

---

### Post by ka55o5 on 2013-04-09
.. it's [easy]("http://www.hydrogenaudio.org/forums/index.php?showtopic=54933") 2 get Foobar2000 in xUbuntu. [color=gray][PPA]("http://www.winehq.org/download/ubuntu") [@]("https://launchpad.net/~ubuntu-wine/+archive/ppa")[/color]

**Edit**: I take that back, just spent all night with Wine again and it's (still) useless; Oracle VM, or some other, with CPU virtualization is the (only) way to go.

---

### Post by vasa1 on 2013-04-09
OP hasn't come back to this thread but I came across this:
> On Ubuntu Desktop we want to discourage usage of command line =) as
there is no need for that for non-developers.
From [https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2013-April/014390.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2013-April/014390.html)

---

### Post by pinballwizard on 2013-04-09
> **vasa1 said:**
> OP hasn't come back to this thread but I came across this:

From [https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2013-April/014390.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2013-April/014390.html)

Well, then devs should stop pushing updates that bork my system and force me into the cli to fix.

Granted, it doesn't happen often, but I don't run any dodgy or pre-release repositories, and I use LTS, and still, updates break my system and there's no way but command line to repair things.

---

### Post by JayKay3OOO on 2013-04-11
Still use it a bit. Some things are just quicker with a few commands than having to hunt for the right application and then wait for it to load or re-start a massive download because the computer went to sleep because you're eco minded and the app you were using would not re-start the download wasting all that time when wget would have just woken up with the computer.

---

### Post by hainen on 2013-04-11
I like to have a graphical tool to stuff I seldom do. Like configure something I only do once. But stuff I do every time I use the computer I usually prefer the terminal. The best example is file management. To this the console is perfect. Its easy to learn and very powerful. You can filter, search modify, move, change rights etc way faster and easier than with a file manger.

---

### Post by scy on 2013-04-12
I like the command line, because it is simple and not all messy and hard to deal with like all the apps and such. I really appreciate how you can always go back to the command line, and there is usually more functionality with it.

---

### Post by BrokenKingpin on 2013-04-12
It is not like they stop you from using the Terminal. I so no harm whatsoever to make things accessible through the UI, for new and experienced Linux users. I am pretty good with the command line and use it a fair bit, but if a task can easily be done through the UI why not use it, and if you don't want to then still use the terminal.

---

### Post by scouser73 on 2013-04-15
Using the command line is brilliant, I don't shy away from it when I'm given the chance to use it.

---

