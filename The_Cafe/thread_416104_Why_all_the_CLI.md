---
title: "Why all the CLI?"
date: 2007-04-20
forum: The Cafe
---

### Post by teddybairs1 on 2007-04-20
I know I'm going to take heat for this, but here it goes...

One of the things I've noticed on the forum is that generally all the help is given by using the command line. While I understand the usability of it, it may not be the most user friendly way of giving help to someone. For example, when telling someone to copy a file from one location to another as root, why no just direct them to the "Run Command" selection in the Gnome or KDE menus and enter gksu nautilus/kdesu konqueror and then copy and paste like they would otherwise? Why have them crack open the cli and start typing out the whole command?

Maybe I'm just lazy (yes, I'll admit it), but the whole point of the graphical tools like nautilus and konqueror is to use them. The cli on Linux is advanced and can run circles around the old DOS or the Windows Terminal. I can definitely appreciate it. But why have the newbie crack it open and start running commands when many times they can do it graphically?

Just a question, thought I'd throw it out there and see who bites.

---

### Post by yabbadabbadont on 2007-04-20
Everyone has the same CLI, not everyone uses the same desktop environment, or even uses one at all.  If I give directions on how to fix the issue from inside a terminal window (doesn't matter which terminal), then I know that it will work for them.  When you are asking for help for free from volunteers, you will either take what you get, or go without.  ;)

---

### Post by Hex_Mandos on 2007-04-20
The CLI is more objective: It doesn't care about what GUI you're using. It's also faster and easier for an advanced user to learn. GUI tools are good for a new user to learn on his or her own, but there's a larger margin for error than just copying and pasting.

---

### Post by Compucore on 2007-04-20
I work etherway over here. So long as it does the job andfixes the error. For me working in the command line doesn't make me more geekier. Just another way of doing things. Sometimes. The onl way of fixing it is in the command line. I know at work we are runnig two servers that are using linux on them. And they don't have the GUI installed on them. So what is the point of using the gui when you can do it in a terminal mode or in a command line mode as root or admin?I would go like what yabbedabbadont had suggest personally. 

Compucore

---

### Post by Toadmund on 2007-04-20
I guess it's easier to cut 'n' paste in the terminal, than to go find the GUI (ahhh, do I have too!), and, the person most likely to be of help is an experienced user who has rememberized the commands.

So I suppose if you've used Linux long enough to be of help, the command terminal *is* in fact easier.

---

### Post by teddybairs1 on 2007-04-20
You guys made a good point in that the command line commands don't change whether you're using terminal or konsole.

One of the criticisms, or ignorances, about linux is that people are intimidated by the CLI and think that you have to know the CLI in order to run it. Thus, MS just seems easier to them because they don't realize that there are perfectly good GUIs for Linux. Whenever I mention that I'm running Linux on my laptop, they look at me strange and say "isn't that for servers?" Then I show them my laptop running Ubuntu with KDE and Beryl.

I guess sometimes it just seems as though the constant reference to the CLI in support only serves to reinforce this ignorant assumption. I think a lot of people don't realize that in order to do something serious in windows I think you still have to open up the CLI, come to think of it. I think the misconception is that you have to use the CLI most of the time in Linux as opposed to Windows, which isn't true. I know I only pop open konsole when I have to, like following someone's support instructions ;) ; otherwise I do most of my package management now through adept, and most everything else through the gui.

---

### Post by UltraMathMan on 2007-04-20
I've found that troubleshooting in general is easier through the CLI than the GUI in many cases. For example, a while back azureus kept crashing on startup (with no GUI error message). However when I ran the program through the terminal I received detailed information which allowed me to quickly find a solution. 

While the CLI is certainly not generally necessary for normal operation, it is, as others have pointed out, an advanced tool perfectly suited to advanced tasks such as repair. Yeah it may not be the prettiest, friendliest way, but in cracking it open and exposing new users to it also serves to acclimate them to it, a sort of shove in the direction of leaving the "noob" status behind them as they are *guided* through a uniform, universal method of problem solving.

Just think - if no one ever exposed you to the terminal and guided you in it's constant use for troubleshooting, would you know and/or be able to do as much as you can now? I know I wouldn't.

---

### Post by grte on 2007-04-20
Another issue is that a lot of WMs just wont have gui tools for a lot of things.  For example, a new user trying to rejuvenate an old PC with an openbox/fluxbox/wmii/whatever window manager is, in many cases, gonna be out of luck without command line support.

---

### Post by K.Mandla on 2007-04-20
For me, giving advice is a little more predictable when I suggest the command line. I don't know much about Gnome or KDE, so trying to explain something in GUI terms ("press the button next to the slider thing and see if this pops up ...") is a little abstract.

It's generally more of a common ground to suggest commands from the terminal. :D

---

### Post by ceil420 on 2007-04-20
I don't see how "gksu thunar > navigate to the folders copyin' and pastin'" is any easier than "sudo cp /root/file ~/folder", but to each his own, I guess.

---

### Post by Toadmund on 2007-04-20
Good point!
Instead go here where it says that, then go to ____ and press ____ at the bottom, then click the ____ .

With terminal it's paste this, write that.
'ENTER'

---

### Post by teddybairs1 on 2007-04-21
Good points all.

---

### Post by saulgoode on 2007-04-21
I would add that when you work from the CLI, you are provided with error messages that often prove useful to the person helping you. While dragging files around in Nautilus might result in "it didn't work", performing a similar function from the CLI will provide a helpful message such as "cp: cannot stat `file.txt': Permission denied" *.

* an oversimplified example, and I do not use Nautilus so therefore have no idea how it might respond (a point which has already been made).

---

### Post by click4851 on 2007-04-21
I know for me, when I first dipped my toe into the CLI environment, the lack of any visual clues was ......intimidating. All that black, and what was that command?, just naviagting was an exploration project, and man pages, and ....I'm sure I'm not saying anything new....very powerful tool.

---

### Post by userundefine on 2007-04-21
I think aiysu said it best: I can tell someone how to do what they want to do with a command once, and I know it's going to be done right if they copy and paste.  Telling them to open a GUI, click here, click there, click this but DON'T click that, it's so much more prone to error.

---

### Post by jacksaff on 2007-04-21
In linux land programs tend to get made with the command line first and guis are added later as front ends. This makes the app much more portable to different systems than tying the functionality to a particular front end. It also means that the command line version is usually older and more stable, and that the gui may well not yet have all the capability of the underlying program.

---

### Post by mcduck on 2007-04-21
> **ceil420 said:**
> I don't see how "gksu thunar > navigate to the folders copyin' and pastin'" is any easier than "sudo cp /root/file ~/folder", but to each his own, I guess.

The problem there is that if the person asking the question doesn't tell which desktop environment/window manager he/she is using, you'd have to give instructions how to do that in Gnome, XFCE, KDE and perhaps some other setup. And if the instructions needed are any more complex than just opening the file manager as root it gets very complicated doing that for all possible different setups..

---

### Post by macogw on 2007-04-21
> **userundefine said:**
> I think aiysu said it best: I can tell someone how to do what they want to do with a command once, and I know it's going to be done right if they copy and paste.  Telling them to open a GUI, click here, click there, click this but DON'T click that, it's so much more prone to error.

Agreed.  I had to do a Google Image search for the C:\ properties window so i could describe what a certain button looked like and where it was located in Windows XP.  It took like 15 minutes to get the person to find the right button.  Copy and paste *that* is really easy even without seeing the screen.

---

### Post by MrHorus on 2007-04-21
> **teddybairs1 said:**
> For example, when telling someone to copy a file from one location to another as root, why no just direct them to the "Run Command" selection in the Gnome or KDE menus and enter gksu nautilus/kdesu konqueror and then copy and paste like they would otherwise? Why have them crack open the cli and start typing out the whole command?


One word - feedback.

If you just fire a command into a run box then it dies silently if there is an error. Run it in an xterm and you get the error messages - case in point when trying to get Beryl to work on my gf's machine last night.

It was dying silently when I tried to enable but when running it in a terminal it showed me the error - namely that I hadn't enabled the composite extension in xorg.conf.

---

### Post by forrestcupp on 2007-04-21
> **yabbadabbadont said:**
> Everyone has the same CLI, not everyone uses the same desktop environment, or even uses one at all.  If I give directions on how to fix the issue from inside a terminal window (doesn't matter which terminal), then I know that it will work for them.  When you are asking for help for free from volunteers, you will either take what you get, or go without.  ;)

> **saulgoode said:**
> I would add that when you work from the CLI, you are provided with error messages that often prove useful to the person helping you. While dragging files around in Nautilus might result in "it didn't work", performing a similar function from the CLI will provide a helpful message such as "cp: cannot stat `file.txt': Permission denied" *.

* an oversimplified example, and I do not use Nautilus so therefore have no idea how it might respond (a point which has already been made).

These are the two best reasons I have ever heard.  You've converted me.  I now see that for giving someone help, maybe it is the best way to explain things.

But if I'm doing things on my own, I will probably prefer to do everything I can through my gui.  About the only thing I can't do with the gui is run a program as super user.  I can open a file from nautilus as super user, but if I want to run gedit from the gnome menu, I don't think I can.  Other than that, I can do most things with gui.

---

### Post by Buffalo Soldier on 2007-04-21
I think even MS is finally acknowledging that CLI is a very powerful and productive tool.

[http://en.wikipedia.org/wiki/Windows_PowerShell](http://en.wikipedia.org/wiki/Windows_PowerShell)

---

### Post by juxtaposed on 2007-05-15
It's often useful to get help with the command line instead of GUI because instead of saying something like "copy file x from w to j, then copy p from a to v" or something, you can easily copy and paste a few commands with less effort. The poster has already done all the work, you just have to copy and paste into the terminal.

---

### Post by Jhongy on 2007-05-15
I think there are too many CLI commands in the newbie and desktop help forums here.

NOT because the CLI is a bad thing. It's not. But it scares away newbies, and they don't learn anything if they just copy & paste.

For example, I believe they will learn more if they use the Synaptic menu structure to add a repo and a gpg key than using the CLI. The CLI is 5x more efficient, but that's besides the point.

In addition, there is a bunch of comunity documentation that is not much more than a list of apt-get commands. I don't think this is encouraging for the abject newbie. If I had time, I'd reqrite it for the GUI.

---

### Post by teddybairs1 on 2007-05-16
I agree with this last post.

I am beginning to see the usefulness and efficiency of the Linux CLI, but I do think newbies would be serviced more by being taught how to use the GUI tools available to them. Not everyone wants to, or needs to, be a whiz at the CLI, and the previous post was right, cutting and pasting commands doesn't teach anyone anything. Which is better, teaching a person how to use Synaptic/Adept so he knows what to do, or just having him cut and paste an apt-get command which, to a newbie, may be completely meaningless and might as well be written in Klingon?

---

### Post by goumples on 2007-05-16
terminal fixes are quicker as in: "Just copy and paste this in your terminal" versus "click here then there, then click here and there, finally drop this menu and etc etc etc.."   see?

---

### Post by H.E. Pennypacker on 2007-05-16
All the benefits of the CLI mean nothing to people like my sister.  Sure, the CLI is more efficient, everyone has it, and whatever, but to many people, these benefits mean nothing.  They simply want to move on with their lives, and use their computers.  Using the CLI requires LEARNING SOMETHING.  

You are not born with CLI knowledge, and that's the worst thing about the CLI.  Everyone speaks the language of GUI (we all know how to point and click), but the same is not true for the CLI (some people don't even know how to open the terminal, let alone commands like mv, cd, grep, ls, etc.).

There are people who want to use their computers and not learn anything, and there are people who want to use the CLI.  When will CLI advocates learn that there are people out there who don't GIVE A DAMN?  Everything about CLI advocates is about empowering the newbie, and teaching the newbie how to fish for himself (not sure if I have the saying right).

It took me a while to learn the CLI, and I am still learning.  With my years of Windows use, I already know how to use GUI.  I had to re-learn everything, eventhough it wouldn't be necessary since Ubuntu provides GUI in most instances.  However, the language of the Linux community is often in CLI, not GUI.

I am not sure why I am whining about this.  It's not like anything will change, and the vast majority of Linux users will never share my opinion (they are too convinced of the heavenly nature of the terminal).  Go through this thread, and you'll hear the same old arguments FOR the CLI.  Unbelievable.

---

### Post by steven8 on 2007-05-16
> you'll hear the same old arguments FOR the CLI. Unbelievable

And you'll hear the same old argumants against it.  So what else is new. . .

---

### Post by juxtaposed on 2007-05-16
> Using the CLI requires LEARNING SOMETHING. 

Not really.

For example, some new person to linux asks how to install Azureus.

Then someone tells them to copy and paste this into the terminal: sudo apt-get install azureus

They do that and it is installed. They can therefore assume that they can replace azureus with other programs to install them, without even knowing what apt is.

> let alone commands like mv, cd, grep, ls, etc.).

I don't know those, yet the CLI is easier to use when people tell you how to do something.

Less chance for error if you just copy and paste what someone else wrote. It's like someone else is doing it all for you, you just have to enable it.

---

### Post by SunnyRabbiera on 2007-05-16
still my outlook is that there should be a GUI version for every CLI app out there, that way the newbie can have some relief.

---

### Post by ssam on 2007-05-16
[http://ubuntuforums.org/showpost.php?p=2268188&postcount=821](http://ubuntuforums.org/showpost.php?p=2268188&postcount=821)

---

### Post by Sunnz on 2007-05-16
To put it bluntly, people are too lazy to help others.

Not that people don't want to help people, but on forums people are doing it for free and the fact it is not in person, CLI is just a more efficient way to help people. If the Windows CLI were more powerful, you would see more help given as CLI on Windows - when I called my ISP when I had problems, if they think I need help on my computer it is almost always Start/Run/cmd; of course I then tell them I use Ubuntu. ;)

Also, with internet forums and mailing lists, it is likely other people have the same problem but on different DE or even different distro! It would be frustrating to "reverse engineer" a GUI-specific solution or having to explain the same solution all over again for a different GUI.

> **SunnyRabbiera said:**
> still my outlook is that there should be a GUI version for every CLI app out there, that way the newbie can have some relief.

I agree, Mac has quite a lot of GUI of common CLI you see on UNIX and it is nice when it is available. However developers don't always have the time and/or resource to do so, and they may want to spend more resource to make their CLI code better... but since we are living in the FLOSS world it means other developers may make a GUI for it if there is enough interest.

---

