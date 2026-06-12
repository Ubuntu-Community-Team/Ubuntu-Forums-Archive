---
title: "Here is a good question for those who help Newbs"
date: 2008-01-19
forum: The Cafe
---

### Post by jleaker01z on 2008-01-19
I have noticed that experienced Ubuntu users who try to help new Windows converts that have problems like to say "open a terminal and type in these commands: blah blah" even when those packages are available via the add/remove programs or synaptic.  My question is, WHY?  This does several things:

1.  It reaffirms to the converts that Ubuntu is complicated and impossible to run without using a command line

2.  Reaffirms that Linux is for geeks

3.  Completely frustrates a Windows user who has possibly never used a command line in their life (I've been around since DOS days, but lots of younger people have never used anything but Windows)

It seems to me that if we would like to convert more people away from Windows, we should emphasize the GUI ways of installing packages.  I realize that for the experienced it can truly be easier to simply issue the command at the command line, but it may not be so easy to someone who has never seen a command prompt.

So again, I ask Why?

---

### Post by Perpetual on 2008-01-19
For me personally, I reference CLI because it's good to learn.  I have never had a Linux install that was 100% CLI free.  So, having a new user get their feet wet with apt-get install and at least seeing the CLI and getting acclimated to it I feel is good.

Besides, you can 'apt-get install package' must faster than you can System > Administration > Synaptic > wait > enter password > Search > wait > Mark Package > Apply...

I just think it is good to start off realizing Linux Distributions are not Windows and should not be handled like windows.  The CLI opens the flood gates to the power and flexibility of Linux and should not be intimidating.

just my opinion.

---

### Post by jleaker01z on 2008-01-19
I agree with you, except the part about getting their feet wet.  Get them hooked on the OS with the GUIs then move on to, what is for them, the more complicated way of doing it.  We have to remember that we are appealing to Windows converts and a command line is foreign to them.  If they can do it with a GUI, retention would be much better.  I say this from the standpoint of someone who switched from Windows not too long ago, and beat themselves up trying to figure out the command line when a GUI would have worked just fine.

Also I would like to add that I am not trying to be critical in a bad way.  I really do believe that using the GUIs will get more people hooked on the OS and away from Windows.

---

### Post by vanadium on 2008-01-19
Giving command line instructions is short, efficient and utterly precise. Let people discover the guis during their learning and exploring the operating system, but for helping out, the command line and the information it provides is most efficient. Pasting a few lines of text is far more efficient than posting a screen capture, that contains far fewer information, on line.

I am a windows user myself and I find myself using the command line more and more. It is a sharp swiss knife (and you can cut yourself badly!)

---

### Post by jleaker01z on 2008-01-19
I dont deny its simplicity and efficiency to an experienced user.  But to someone who just switched from Windows it LOOKS complicated.  Perception can be a much greater influence then reality.

---

### Post by jrusso2 on 2008-01-19
> **jleaker01z said:**
> I dont deny its simplicity and efficiency to an experienced user.  But to someone who just switched from Windows it LOOKS complicated.  Perception can be a much greater influence then reality.

Often times you can explain to a user a couple of commands much easier the have to write a paragraph about the steps to do the same thing with a gui tool.

---

### Post by Mateo on 2008-01-19
command line instructions work universally.  you don't have to say "now press the button X that's located in the right hand corner of the screen", etc.  you just say "type this, then type this, then type this".

---

### Post by Perpetual on 2008-01-19
> **Mateo said:**
> command line instructions work universally.  you don't have to say "now press the button X that's located in the right hand corner of the screen", etc.  you just say "type this, then type this, then type this".

After learning Ubuntu and the CLI it helps new users then go try a different Distribution and at least have an understanding of how to get going.  Say, someone uses Ubuntu for a few months, then tries Fedora, the CLI is virtually the same in concept (once they realize yum vs. apt and it's nuances).  Very few distributions seem to have the same GUI tools but as Mateo said above, the CLI is constant from distro to distro.

---

### Post by aysiu on 2008-01-19
There are several reasons people use commands instead of GUI instructions: [list][*]This is a text-based forum, and commands are text. If you're giving tech support *in person* it's a lot easier to give GUI commands, because you can point your finger at what you want people to click on. [*]Not everyone is using the same GUI, so GUI instructions are not consistent. I can't tell you how many times I've told someone to go to System > Administration > Synaptic Package Manager only to find out she's using KDE and not Gnome. [*]Terminal commands are more likely to give you a useful error message in case something goes wrong. [*]Commands do not need to be retyped. They can be copied and pasted. [*]They can often be more efficient. For example, you can install several needed software packages with one command--something that would take a lengthy set of instructions to describe how to do in the GUI.[/list] The downsides of command-line instructions are as follows (including a couple of things you've pointed out): [list][*]Since new users do not understand what they're copying and pasting in the terminal, a malicious "helper" can easily get the new user to delete her entire system or home directory. This doesn't happen often, but it has happened recently when the new user hasn't waited for other forum members to validate the command. [*]Any command using *sudo* is going to ask for a password, and many new users get confused by the [lack of visual feedback when typing passwords in the terminal](http://www.psychocats.net/ubuntu/passwordinterminal) [*]As you said in your initial post, it serves only to reinforce the notion that Linux is for geeks. [*]It can be intimidating to life-long Windows users who have never touched MS-DOS.[/list] In the end, I do a mix of terminal commands and screenshots/GUI instructions, depending on the situation and the attitude of the user I'm trying to help.

If the user seems pretty open-minded about stuff and/or the problem that needs to be fixed clearly needs to be diagnosed with an error message, then I will give a terminal command. If, however, the user makes a point of repeatedly saying that instructions should be given in plain English and/or the question is about a task easily accomplished in the GUI, I'm less inclined to give terminal commands.

Most of my Psychocats tutorials are screenshot-laden, but for online tech support, sometimes a terminal just cannot be beaten.

P.S. If this turns into yet another "CLI v. GUI" thread, I'm just going to move it to Recurring Discussions.

---

### Post by ~LoKe on 2008-01-19
It's easy and impossible to screw up if you follow the directions.

Sometimes the user can't find the thing he's supposed to click on, or something.  It's easier to say...

> Type **sudo apt-get install package**
Assuming they can read, it's almost guaranteed success.

---

### Post by aysiu on 2008-01-19
> **~LoKe said:**
> It's easy and impossible to screw up if you follow the directions.

Sometimes the user can't find the thing he's supposed to click on, or something.  It's easier to say...


Assuming they can read, it's almost guaranteed success.
I would strongly suggest copy and paste over retyping--less work and less chance of typos or miscapitalization/lowercasing.

---

### Post by jleaker01z on 2008-01-19
> **aysiu said:**
> 

P.S. If this turns into yet another "CLI v. GUI" thread, I'm just going to move it to Recurring Discussions.

Sorry, I did not mean to initiate a discussion that has already taken place.  I posted this as a result of my own experience.  I truly LOVE Ubuntu and will never use Windows again.  But I would like to see more, and by that I mean ALOT more, people make the switch.

For someone who is used to Windows, it is easier TO THEM to use a GUI.  Since I started out with DOS on my old 8088 system I was familiar (albeit out of practice with the CLI) and still had trouble understanding what was happening.

Cutting and Pasting is easy, but if the end user doesnt understand what he just did, or how it worked, it has not made the OS itself any easier for them to understand or use.  Windows users are used to looking through menus to find what they are looking for, and to carry that on to their new OS simply makes sense to me.

---

### Post by Mateo on 2008-01-19
speaking of copy/paste, another problem with using CLI instructions is that copy/paste doesn't always work the same, consistently, in Ubuntu (and probably linux in general).  I can use ctrl+c/v in epiphany or gedit or any number of gui applications, but when I load up gnome-terminal it stops working.  It prints ^V instead.  That makes it difficult for new users.  It's something else that they are going to have trouble with, come back to you, and then you have to explain to them to use Shift+Ctrl+V (or middle mouse click) instead.

I think gnome-terminal should use Ctrl+C/V instead of Shift+Ctrl+C/V

---

### Post by Lord Illidan on 2008-01-19
CTRL + C exits a running process in the terminal. Just learn to use shift-insert ,or even Edit - Paste.

I usually prefer using console to help people out with. It's faster, and they get to learn more about the terminal. You can get by in Windows without knowing about the terminal, but in Linux, you are losing an amazing amount of functionality by not knowing how to use it.

---

### Post by ~LoKe on 2008-01-19
> **Mateo said:**
> I think gnome-terminal should use Ctrl+C/V instead of Shift+Ctrl+C/V

No thanks.  Ctrl+C is far more useful for me, and is more consistent with other terminals and programs.

---

### Post by Perpetual on 2008-01-19
> **aysiu said:**
> I would strongly suggest copy and paste over retyping--less work and less chance of typos or miscapitalization/lowercasing.

The only thing I have against copy and paste is that there is no learning from it.  I generally type commands given, just because then I tend to absorb what I just did vs. blindly pasting something and not remembering it.  However, when I do type commands, I always double check for typo's.

---

### Post by Mateo on 2008-01-19
i don't know how many times i've accidentally stopped a process when trying to copy some text.

---

### Post by jleaker01z on 2008-01-19
> **Lord Illidan said:**
> CTRL + C exits a running process in the terminal. Just learn to use shift-insert ,or even Edit - Paste.

I usually prefer using console to help people out with. It's faster, and they get to learn more about the terminal. You can get by in Windows without knowing about the terminal, but in Linux, you are losing an amazing amount of functionality by not knowing how to use it.

Oh I agree totally with you...but my point is about retaining those who download and try out Ubuntu.  Use the GUIs to get them hooked, then ease them into the CLI.  There are some people who once you tell them they have to use a CLI will just reinstall Windows and tell everyone they know that Linux is simply too complicated for the average user.  Thats bad :(

---

### Post by aysiu on 2008-01-19
> **jleaker01z said:**
> 
For someone who is used to Windows, it is easier TO THEM to use a GUI.  Since I started out with DOS on my old 8088 system I was familiar (albeit out of practice with the CLI) and still had trouble understanding what was happening. I acknowledge that. My earlier post looks at pros and cons of both CLI- and GUI-based help models.

> Cutting and Pasting is easy, but if the end user doesnt understand what he just did, or how it worked, it has not made the OS itself any easier for them to understand or use. I don't know if I agree with that. Most Windows users I know do not seek to understand Windows at all. They memorize steps (Click here, click here, type this, etc.). If a computer users wants to understand, she'll make the effort to understand. I started off copying and pasting with Ubuntu, and now I understand more. You'll see this difference a lot. Some users will just be all too glad that their problems are sorted out. Others will take that extra step to say, "Thanks for helping me fix the problem. So what exactly did that command do?" or, better yet, actually Google the command to find out themselves!

If one has the inclination to learn, one will learn. If one has the inclination to avoid learning, the GUI won't be a tool to learn--only a set of memorized steps.

Frankly, if these people were so great at using GUI menus, they'd have poked around and found Add/Remove under Programs and started using that. Instead, they just go to a website to download software as a .tar.gz and expect a wizard. See? No understanding or taking advantage of discoverability in the GUI--only habits and routine: memorized steps.

If you want to learn, you'll learn (regardless of GUI or CLI). Most people who post a thread just want their problems fixed.

---

### Post by orange2k on 2008-01-19
I think that the most productive way for a Newb to learn something about computers is to start with a C64 (my own experience), where you cant do anything without typing something - there is no clicking on an icon, forget about that...

First you have to learn something about binary nubers, hexadecimal numbers, then learn something about some programming language etc...

If you are not comfortable with that, then you should just use windows or macos - you dont have to know anything at all, you just click on something and everything "just works" or not (like in some "legacy OS")...

Since Ive started using Linux, I learned many things about computer security, CLI, and Ive even started learning Python...

So yes, Im proud to be a "geek", even though I dont deserve to be called one, yet...:)

---

### Post by aysiu on 2008-01-19
> **orange2k said:**
> I think that the most productive way for a Newb to learn something about computers is to start with a C64 (my own experience), where you cant do anything without typing something - there is no clicking on an icon, forget about that...

First you have to learn something about binary nubers, hexadecimal numbers, then learn something about some programming language etc...

If you are not comfortable with that, then you should just use windows or macos - you dont have to know anything at all, you just click on something and everything "just works" or not (like in some "legacy OS")...

Since Ive started using Linux, I learned many things about computer security, CLI, and Ive even started learning Python...

So yes, Im proud to be a "geek", even though I dont deserve to be called one, yet...:)
I've been a full-time Linux user since April 2005 and know nothing about binary nubers, hexadecimal numbers, or programming languages. I am not comfortable with those things (and don't even know what a *nuber* is), yet I feel that I *should* use Ubuntu and not Windows or Mac OS.

I'm sorry you feel your advanced knowledge means you have an exclusive right to use Linux and that we non-programmers should be using another OS.

---

### Post by popch on 2008-01-19
> **orange2k said:**
> I think that the most productive way for a Newb to learn something about computers is to start with a C64 (my own experience), where you cant do anything without typing something - there is no clicking on an icon, forget about that...

First you have to learn something about binary nubers, hexadecimal numbers, then learn something about some programming language etc...

If you are not comfortable with that, then you should just use windows or macos - you dont have to know anything at all, you just click on something and everything "just works" or not (like in some "legacy OS")...

Since Ive started using Linux, I learned many things about computer security, CLI, and Ive even started learning Python...

So yes, Im proud to be a "geek", even though I dont deserve to be called one, yet...:)

Quite. Just as properly using an automobile starts with mining for and smelting iron, using a lathe, harvesting and vulcanizing rubber and winding your own coils for the starter motor.

Using a computer effectively and efficiently is quite possible without knowing all those technical details you mention, even though some of them can become terribly useful once in a while.

---

### Post by M$LOL on 2008-01-19
Another point is that the people who help new users are giving up their time to do it, so demanding that they give less efficient and more long-winded instructions doesn't make sense.

As for getting people hooked on the OS, the point of people posting on the forums for help is to solve their problem, not get them hooked. Terminal commands solve the problem with more precision and a higher success rate than instructions on how to do it in the GUI, so it's better to use them.

---

### Post by orange2k on 2008-01-19
> **aysiu said:**
> I've been a full-time Linux user since April 2005 and know nothing about binary nubers, hexadecimal numbers, or programming languages. I am not comfortable with those things (and don't even know what a *nuber* is), yet I feel that I *should* use Ubuntu and not Windows or Mac OS.

I'm sorry you feel your advanced knowledge means you have an exclusive right to use Linux and that we non-programmers should be using another OS.

I dont claim to have any "advanced" knowledge (Im not even able to compile a program without instructions), but Ive learned many things about computers in my C64 time. My statement is somewhat stupid, but it is advantageous to know some basics about how computers work. And to know that, you should know that the machine basically understands only "computer language", in other words only binary/hexadecimal numbers...

Even in the windows world, with all the firewalls and antivirus programs you can get, it is good to be able to recognize things that can get your system exposed to threats and exploits, but thats another story...

I`m sorry you feel that you can ever feel comfortable with any OS if you don`t know anything about the basics...

---

### Post by aysiu on 2008-01-19
> **orange2k said:**
> 
I`m sorry you feel that you can ever feel comfortable with any OS if you don`t know anything about the basics... I guess we just have different definitions for the word *basics* in this context. I won't let your elitist attitude deter me from using Ubuntu, though.

---

### Post by p_quarles on 2008-01-19
I like to test any instructions I'm not completely certain about before recommending them. Since I use a GUI that is almost certainly not the one being used by most beginners, I can only double check terminal commands.

---

### Post by Lord Illidan on 2008-01-19
> I think that the most productive way for a Newb to learn something about computers is to start with a C64 (my own experience), where you cant do anything without typing something - there is no clicking on an icon, forget about that...

First you have to learn something about binary nubers, hexadecimal numbers, then learn something about some programming language etc...

If you are not comfortable with that, then you should just use windows or macos - you dont have to know anything at all, you just click on something and everything "just works" or not (like in some "legacy OS")...

Since Ive started using Linux, I learned many things about computer security, CLI, and Ive even started learning Python...

So yes, Im proud to be a "geek", even though I dont deserve to be called one, yet...:smile:

I learnt all that, but it didn't help me. What use are binary numbers and hexadecimal when learning about Linux? They might be of use to kernel programmers, perhaps, or to advanced programmers using assembly, but to normal users, nothing. Frankly, it will just scare them off. I can imagine...let's start using linux. First, we'll learn what binary numbers are...

Programming, ah, that's different. Shell scripts are useful, and they require a certain amount of programming skill. And I'd argue that a linux user must go out and do a script some time or other.

---

### Post by orange2k on 2008-01-19
> **aysiu said:**
> I guess we just have different definitions for the word *basics* in this context. I won't let your elitist attitude deter me from using Ubuntu, though.

Im flattered that someone calls my attitude elitist, but in this case this is wrong...
Before I read an interesting book about computers I thought that computers are actually intelligent: how can a computer play chess if they are just a piece of machinery using plain stupid logic?

Even today, people still think that machines are going to take their jobs and robots are going to replace them.

Well, let my elitist attitude talk: thats not gonna happen without some serious change in how computers work - prove me wrong if a human brain gets a simple emulation, and you can download a human mind in a form of a M.A.M.E. ROM...

---

### Post by M$LOL on 2008-01-19
Your arguments really aren't relevant to the point at hand...

---

### Post by popch on 2008-01-19
> **orange2k said:**
> Even today, people still think that machines are going to take their jobs and robots are going to replace them..

Slightly off topic, but the reason for people believing such things might be that it is actually happening.

---

### Post by Lord Illidan on 2008-01-19
> **orange2k said:**
> Im flattered that someone calls my attitude elitist, but in this case this is wrong...
Before I read an interesting book about computers I thought that computers are actually intelligent: how can a computer play chess if they are just a piece of machinery using plain stupid logic?

Even today, people still think that machines are going to take their jobs and robots are going to replace them.

Well, let my elitist attitude talk: thats not gonna happen without some serious change in how computers work - prove me wrong if a human brain gets a simple emulation, and you can download a human mind in a form of a M.A.M.E. ROM...

I sympathise with you. But, the problem is that today, computers are viewed very much like cars. How they look, what engine they've got, and how fast they work, not **how they actually work**. Whether this is bad or good, I leave up to you. I also thought the computer was "magical" before I learned how boring it really is :D

---

### Post by orange2k on 2008-01-19
> **M$LOL said:**
> Your arguments really aren't relevant to the point at hand...

Why not?
A few months ago, there was a showcase of an exposed 1kB calculator program...
Imagine that, a program of the size of 1024 bytes that features all the basic math: adding, substracting, multiplying, deviding etc...

Now you tell me: is that unneccesary? Is it enough for you just to know it is cool to use Ubuntu, or are you willing to take some extra time to even imagine how it was to be able to program the first computer game ever made: PONG?

Ok, but I think that it is basic to know the essential computer history - for example: that the first commercial hard disk drive had 5 MB capacity, and had a few tons.

We live in fortunate times and take these things for granted. Even a simplest mobile phone is basically a computer many times stronger than the best computer used in the first Pixar movies...

And now somebody tell me that this is irrelevant for a Newb...

---

### Post by wolfen69 on 2008-01-19
In 1952, A.S. Douglas wrote his PhD degree at the University of Cambridge on Human-Computer interraction. Douglas created the first graphical computer game - a version of Tic-Tac-Toe. The game was programmed on a EDSAC vaccuum-tube computer, which had a cathode ray tube display.

William Higinbotham created the first video game ever in 1958. His game, called "Tennis for Two," was created and played on a Brookhaven National Laboratory oscilloscope.
[http://inventors.about.com/library/inventors/blcomputer_videogames.htm](http://inventors.about.com/library/inventors/blcomputer_videogames.htm)

anyway, how hard is it to copy and paste commands?

---

### Post by p_quarles on 2008-01-19
> **orange2k said:**
> And now somebody tell me that this is irrelevant for a Newb...
No, the fact that the first commercial hard drive weighed several tons and had a 5 megabyte capacity does not really relate to the question at hand. For reference, the question is: what is the best way to deliver support to beginning Ubuntu users?

---

### Post by orange2k on 2008-01-19
> **wolfen69 said:**
> In 1952, A.S. Douglas wrote his PhD degree at the University of Cambridge on Human-Computer interraction. Douglas created the first graphical computer game - a version of Tic-Tac-Toe. The game was programmed on a EDSAC vaccuum-tube computer, which had a cathode ray tube display.

William Higinbotham created the first video game ever in 1958. His game, called "Tennis for Two," was created and played on a Brookhaven National Laboratory oscilloscope.
[http://inventors.about.com/library/inventors/blcomputer_videogames.htm](http://inventors.about.com/library/inventors/blcomputer_videogames.htm)

anyway, how hard is it to copy and paste commands?

Exactly my point. 
This is all you do when you click on some icon or some dialog box asking you to confirm if "you are sure that this program is from thrustworhty source" like in some legacy OS...
Ubuntu and Linux, on the other hand believes that you are able to determine what is good for you and what is not...

The very basic understanding of what is actually going on on your computer will never change: you will always be in danger of running malicious programs, even more if youre running some legacy OS and proprietery programs. 

If you consider your computer to be just like a TV, then everybody would be running some legacy OS and there would be no hackers, crackers or any reverse-enginering, and there would be no Neo, Trinity, Morpheus etc...:)

---

### Post by nick_h on 2008-01-19
> **M$LOL said:**
> Another point is that the people who help new users are giving up their time to do it, so demanding that they give less efficient and more long-winded instructions doesn't make sense.

Also, it can be difficult assess the ability of new users.  With the GUI I don't want to waste time describing every click when it is not necessary.

---

### Post by gn2 on 2008-01-19
I helped someone recently who had screwed up his sources.list

All I did was provide a single line of text which allowed him to use the GUI to fix the damage.

It would probably have been much more complex for someone to explain how to repair the damage with the CLI.

[http://ubuntuforums.org/showthread.php?p=4161528#post4161528](http://ubuntuforums.org/showthread.php?p=4161528#post4161528)

Whether to use GUI or CLI depends on the problem, CLI isn't always best.

---

### Post by jleaker01z on 2008-01-19
> **nick_h said:**
> Also, it can be difficult assess the ability of new users.  With the GUI I don't want to waste time describing every click when it is not necessary.

This doesnt address retention of new users tho.  I agree it may be simpler for the person providing the advice, but that in turn makes it more difficult for the new user.  So we have to ask ourselves, what is better?  Simple for me, or simple for the new guy?

And lets be honest here.  Windows users are used to seeing 'click start>programs>blah blah' therefore it stands to reason that they will be better able to understand 'click system>preferences>blah blah'.  Chances of you having to describe every click is low, as long as the new user is familiar with Windows.

Understand I am not disputing the ease of the CLI for someone experienced using it.  I am simply saying we should make it easier for the new person rather than ourselves.  It is my opinion that doing so would make retention much much higher.

As for which desktop they use, KDE, Gnome, etc...again, a new user will likely be using Gnome as that is the default Ubuntu installation.  So again, using Gnome GUI commands will work with 90%+ of the users.

---

### Post by Mateo on 2008-01-19
> **jleaker01z said:**
> This doesnt address retention of new users tho.  I agree it may be simpler for the person providing the advice, but that in turn makes it more difficult for the new user.  So we have to ask ourselves, what is better?  Simple for me, or simple for the new guy?

And lets be honest here.  Windows users are used to seeing 'click start>programs>blah blah' therefore it stands to reason that they will be better able to understand 'click system>preferences>blah blah'.  Chances of you having to describe every click is low, as long as the new user is familiar with Windows.

Understand I am not disputing the ease of the CLI for someone experienced using it.  I am simply saying we should make it easier for the new person rather than ourselves.  It is my opinion that doing so would make retention much much higher.

As for which desktop they use, KDE, Gnome, etc...again, a new user will likely be using Gnome as that is the default Ubuntu installation.  So again, using Gnome GUI commands will work with 90%+ of the users.

When you talk of retention you are no longer talking about helping the user do what the user is asking.  A user is who asks how to get xvid videos to player only wants their xvid videos to play, not to become a pawn of someone's evangelical mission.

---

### Post by popch on 2008-01-19
> **jleaker01z said:**
> This doesnt address retention of new users tho.  I agree it may be simpler for the person providing the advice, but that in turn makes it more difficult for the new user.  So we have to ask ourselves, what is better?  Simple for me, or simple for the new guy?

And lets be honest here.  Windows users are used to seeing 'click start>programs>blah blah' therefore it stands to reason that they will be better able to understand 'click system>preferences>blah blah'..

Explaining how to do something by means of the GUI might not make it simpler for the Newb. There's for instance the thread on how to thank anyone. Some users could not find the Icon to click on even if it was described in fairly plain terms. Posting a picture with the icon highlighted solved that problem.

The insistence on showing how to solve a problem by the means of a GUI also reduces the possible number of people who can contribute to solutions. I, for instance, am posting to an English language forum. However, my installation is not in English as I prefer installing the software in my native language. Therefore, I am often at a loss as to what the buttons, texts and menues might be called in the installation of the Newb asking for assistance. Even worse, the Newb's installation might not be in English, either.

Therefore, the one line instruction given earlier in this thread might give rise to much consternation when the installations are not in the same language.

---

### Post by jleaker01z on 2008-01-19
> **Mateo said:**
> When you talk of retention you are no longer talking about helping the user do what the user is asking.  A user is who asks how to get xvid videos to player only wants their xvid videos to play, not to become a pawn of someone's evangelical mission.

Evangelical mission?  Well if you thats what you want to call it who am I to dispute that. ;)  But I would think we all would want new people who try it to keep using it rather than revert back to Windows.  I'm sure there are people who really don't care if they go back to Windows or not, but if that were the case, chances that they are helping someone do anything doesnt seem likely.

And I would also like to point out, that by sending them to the GUI add/remove programs thingy to install the xvid codecs (to use your example) means they might just start looking there themselves when they need to install something and not come back to the forums so someone can give them the terminal commands.  In effect, it empowers the new user and lets them better customize their own system without as much assistance.

While not everyone would figure that out, not everyone is completely dumb either.  Theoretically, it could very well decrease the amount of requests for help, making it easier for all involved.

---

### Post by lespaul_rentals on 2008-01-19
> **Perpetual said:**
> For me personally, I reference CLI because it's good to learn.  I have never had a Linux install that was 100% CLI free.  So, having a new user get their feet wet with apt-get install and at least seeing the CLI and getting acclimated to it I feel is good.

Besides, you can 'apt-get install package' must faster than you can System > Administration > Synaptic > wait > enter password > Search > wait > Mark Package > Apply...

I just think it is good to start off realizing Linux Distributions are not Windows and should not be handled like windows.  The CLI opens the flood gates to the power and flexibility of Linux and should not be intimidating.

just my opinion.

You summed it up perfectly.  In my opinion, Linux wasn't made with the Windows user in mind.  It is an advanced operating system and as such its users must be willing to learn.  If it's an issue for someone to use the command-line I don't think they are right for Linux.

One of my favorite things about Linux is the way it encourages you to open the hood of the car and look at the engine.  Even if you don't actually know how to replace a belt or tune your transmission, at least you looked inside the hood.  When we tell people to type a command into a bash shell, we aren't giving them a toolbox and telling them to fix the car, we are simply just showing them where the toolbox is kept and how to open the hood.  If their response to that is, "I just want to click on the blue e" they are not made for Linux, seriously.  I love introducing people to the awesome distros out there, but my mom, for example, would be the last person I try to convert.  I converted my dad, though, and he now uses Linux as the sole OS on his laptop.  He is willing to edit a configuration file here and there, and he uses the command-line version of apt, and he's happy.

I know this will sound very elitist, but it annoys me when people tell me we need to make Linux easier for the noobs.  No, we don't.  With an X Server and the desktop enviroment of your choice, you have almost limitless possibilities in the GUI realm.  Sure, it's more "advanced" than Windows, but let me put it this way:

If you want a cheap PC that will let you do your work, you go with Windows.
If you want to learn about how computers work, are fascinated by the interation of hardware and software, and like power, you go with Linux or BSD.

Let's not blend them.

---

### Post by jleaker01z on 2008-01-19
> **lespaul_rentals said:**
> You summed it up perfectly.  In my opinion, Linux wasn't made with the Windows user in mind.  It is an advanced operating system and as such its users must be willing to learn.  If it's an issue for someone to use the command-line I don't think they are right for Linux.

One of my favorite things about Linux is the way it encourages you to open the hood of the car and look at the engine.  Even if you don't actually know how to replace a belt or tune your transmission, at least you looked inside the hood.  When we tell people to type a command into a bash shell, we aren't giving them a toolbox and telling them to fix the car, we are simply just showing them where the toolbox is kept and how to open the hood.  If their response to that is, "I just want to click on the blue e" they are not made for Linux, seriously.  I love introducing people to the awesome distros out there, but my mom, for example, would be the last person I try to convert.  I converted my dad, though, and he now uses Linux as the sole OS on his laptop.  He is willing to edit a configuration file here and there, and he uses the command-line version of apt, and he's happy.

I know this will sound very elitist, but it annoys me when people tell me we need to make Linux easier for the noobs.  No, we don't.  With an X Server and the desktop enviroment of your choice, you have almost limitless possibilities in the GUI realm.  Sure, it's more "advanced" than Windows, but let me put it this way:

If you want a cheap PC that will let you do your work, you go with Windows.
If you want to learn about how computers work, are fascinated by the interation of hardware and software, and like power, you go with Linux or BSD.

Let's not blend them.

I disagree.  Linux may in fact be more advanced/powerful, but it is in fact very simple to use with the GUI interfaces.  And lets face it, if all those old people and kids who just use their PC to surf the net and check email (which is the majority of PC users) were to use some flavor of Linux, the net would be a much safer place simply due to the enhanced security.  Less malware, spyware, fewer botnets, and not to mention, alot less spam emails.

---

### Post by Lord Illidan on 2008-01-19
What blindly enrages me is how some people **never read** any error messages, or try to make sense of them.

They tell you: It doesn't work.
I say: why? Did it tell you anything?
They say: Just a message. I pressed OK.

These people are educated. They **know how to read**. So why don't they know how to use a computer?

---

### Post by orange2k on 2008-01-19
Offtopic, I like when I see other people having some cool icons and thinking...
Of course, the next step would be to read something from Dan Simmons, like Hyperion...
Its so cool...

---

### Post by jleaker01z on 2008-01-19
> **Lord Illidan said:**
> What blindly enrages me is how some people **never read** any error messages, or try to make sense of them.

They tell you: It doesn't work.
I say: why? Did it tell you anything?
They say: Just a message. I pressed OK.

These people are educated. They **know how to read**. So why don't they know how to use a computer?

LOL...maybe its because they are used to getting so many errors in Windows that they dont bother anymore.  Windows error messages dont tell you alot about what the real problem is, at least not for your average user. ;)

---

### Post by lespaul_rentals on 2008-01-19
> **jleaker01z said:**
> I disagree.  Linux may in fact be more advanced/powerful, but it is in fact very simple to use with the GUI interfaces.  And lets face it, if all those old people and kids who just use their PC to surf the net and check email (which is the majority of PC users) were to use some flavor of Linux, the net would be a much safer place simply due to the enhanced security.  Less malware, spyware, fewer botnets, and not to mention, alot less spam emails.

If all those old people and kids used Linux for email, Internet, etc. I could not imagine how many home IT techs would be neccesary to answer their questions.

"I can't watch videos on YouTube."
"Did you download and install the Flash plugin?"
"The what?"

And don't even talk about how there would be fewer botnets, spam attacks, etc.  If you really believe that you are naive.  The main reason few hackers or malware writers attack Linux at the moment is because they know the average Linux user is far smarter than the average Windows user.  Us Linux users know what "social engineering" means.  We know not to type "su" before checking the source.  If Grandma and Little John are using Linux and a website comes up saying "Ubuntu upgrade neccesary or you cannot continue browsing.  Click here to upgrade," well, Grandma and Little John's computers just got owned.

---

### Post by Methuselah on 2008-01-19
I agree with all the advantages of giving instruction on the command line.

I am also of the view too that creating an (false?) impression that linux is too much like windows is bound to result in disenchantment later. If you want windows you should use it. If, however, you want to do the things you can do on windows but are willing to do so a little differently, then you'll be in the right frame of mind to use linux.

Linux is not a drop-in replacement for windows (that's reactos which is far from complete). The GUI exposes information in a way that users can discover it independently. So in a sense, introducing new users to the command line is the best service forum members can give since it's the fastest, most useful way to interact with the system but harder to start doing without guidance. 

Everyone is a newb for a relatively short amount of time compared to their time as an expert. You just have to be willing to endure that phase and learn that skills that will help you through whatever endeavor.

---

### Post by jleaker01z on 2008-01-19
> **lespaul_rentals said:**
> If all those old people and kids used Linux for email, Internet, etc. I could not imagine how many home IT techs would be neccesary to answer their questions.

"I can't watch videos on YouTube."
"Did you download and install the Flash plugin?"
"The what?"

And don't even talk about how there would be fewer botnets, spam attacks, etc.  If you really believe that you are naive.  The main reason few hackers or malware writers attack Linux at the moment is because they know the average Linux user is far smarter than the average Windows user.  Us Linux users know what "social engineering" means.  We know not to type "su" before checking the source.  If Grandma and Little John are using Linux and a website comes up saying "Ubuntu upgrade neccesary or you cannot continue browsing.  Click here to upgrade," well, Grandma and Little John's computers just got owned.

You have to install flash on a Windows machine too.  Its no different.  The mp3 codec would have been a better example. ;)

And yes there would be fewer.  Why?  In Windows, all the security is in the User Layer.  In Linux, the security is built into the kernel. I'm not as naive as you may think. :P

---

### Post by p_quarles on 2008-01-19
> **jleaker01z said:**
> LOL...maybe its because they are used to getting so many errors in Windows that they dont bother anymore.  Windows error messages dont tell you alot about what the real problem is, at least not for your average user. ;)
Yes, that's absolutely true. One of the adjustments I had to make when switching from Windows was realizing that the error messages were in something much closer to plain English than they are in Windows. 

When I am aware of a good GUI fix, I usually suggest it. Problem is, I don't know the GUI methods for everything that I know how to do from the CLI. It seems to me that there are already enough unanswered posts.

---

### Post by lespaul_rentals on 2008-01-19
> **jleaker01z said:**
> You have to install flash on a Windows machine too.  Its no different.  The mp3 codec would have been a better example. ;)

And yes there would be fewer.  Why?  In Windows, all the security is in the User Layer.  In Linux, the security is built into the kernel. I'm not as naive as you may think. :P

You don't have to run a cryptic shell script or wonder whether you have YUM or RPM.  With Windows it's pretty much point-and-click.

Okay, **obviously** there would be fewer.  But it would never be eliminated as much as people say.

---

### Post by aysiu on 2008-01-19
> **lespaul_rentals said:**
> You don't have to run a cryptic shell script or wonder whether you have YUM or RPM.  With Windows it's pretty much point-and-click.

Okay, **obviously** there would be fewer.  But it would never be eliminated as much as people say.
I didn't have to run a cryptic shell script to install Flash. I just visited a site requiring Flash, and Ubuntu prompted me to install the plugin.

---

### Post by billgoldberg on 2008-01-19
In response to the Original Poster.

I agree with everything you say.

I feel that in the "absolute beginners section" it should be recommended to use the gui way of doing things.

If you have been using linux for some time, the command line interface is faster and easier. I've you just switched from a life-long xp enviroment the apt-get thing isn't easier.

From the beginners forum:
A new user asks how to install sound support.
Someone answers and the guy responds:

[I] Originally Posted by reassuringlyoffensive  View Post
I'd suggest you search 'sound compile' or 'sound how-to'.

There are many reasons why sound doesn't work for some. Try the simple things first.

sudo apt-get install alsamixer

It will install into your applications menu.

It's a shame so many are having sound issues. You could try upgrading to the Hardy kernel also. Works for some.
There's a how-to on that.

Nathan
**Sorry to sound like such a moron but I really don't understand any of that. **The "sudo apt..." is something I run in terminal right? I have no idea what Hardy kernel is. I'm trying to learn as I go but I was never very PC literate. Thanks for the reply and I appologize if its a burden to have to explain it to me further.[/I]

If he had said: go to applications -> add/remove and search for "alsamixer" the guy would have understood it.

The thing I hate the most is that in the **absolute beginners forum** when someone download a tarball and ask how to "unzip" it (or when they have to untar something to install something) they give a command. That guy/girl won't remember it and will think that linux is only for computer guru's since you even have to use the CLI to untar something. While all they have to do is right-click and "extract here" (just like with windows+winrar)

---

### Post by aysiu on 2008-01-19
> **billgoldberg said:**
> In response to the Original Poster.

I agree with everything you say.

I feel that in the "absolute beginners section" it should be recommended to use the gui way of doing things.

If you have been using linux for some time, the command line interface is faster and easier. I've you just switched from a life-long xp enviroment the apt-get thing isn't easier.

From the beginners forum:
A new user asks how to install sound support.
Someone answers and the guy responds:

[I] Originally Posted by reassuringlyoffensive  View Post
I'd suggest you search 'sound compile' or 'sound how-to'.

There are many reasons why sound doesn't work for some. Try the simple things first.

sudo apt-get install alsamixer

It will install into your applications menu.

It's a shame so many are having sound issues. You could try upgrading to the Hardy kernel also. Works for some.
There's a how-to on that.

Nathan
**Sorry to sound like such a moron but I really don't understand any of that. **The "sudo apt..." is something I run in terminal right? I have no idea what Hardy kernel is. I'm trying to learn as I go but I was never very PC literate. Thanks for the reply and I appologize if its a burden to have to explain it to me further.[/I]

If he had said: go to applications -> add/remove and search for "alsamixer" the guy would have understood it.

The thing I hate the most is that in the **absolute beginners forum** when someone download a tarball and ask how to "unzip" it (or when they have to untar something to install something) they give a command. That guy/girl won't remember it and will think that linux is only for computer guru's since you even have to use the CLI to untar something. While all they have to do is right-click and "extract here" (just like with windows+winrar)
The problem with that post isn't the use of the terminal but the total lack of explanation as to how to use it.

---

### Post by gn2 on 2008-01-19
> **aysiu said:**
> I didn't have to run a cryptic shell script to install Flash. I just visited a site requiring Flash, and Ubuntu prompted me to install the plugin.

Which tends to suggest you're not using 64-bit?

---

### Post by p_quarles on 2008-01-19
> **gn2 said:**
> Which tends to suggest you're not using 64-bit?
I've never run 64-bit Windows, but I seriously doubt it would be any easier to install Flash on that. 

64-bit isn't difficult (in Ubuntu) by any stretch, but I wouldn't recommend it for someone who doesn't know what a codec is.

---

### Post by aysiu on 2008-01-19
> **gn2 said:**
> Which tends to suggest you're not using 64-bit?
Yes. Why would you presume I'm using 64-bit?

---

### Post by gn2 on 2008-01-19
> **aysiu said:**
> Yes. Why would you presume I'm using 64-bit?

I didn't. What I was suggesting is that because you were able to install Flash by visiting a site and clicking on the "install missing plug-in" you were using 32-bit.

This just doesn't work in 64-bit and a script has to be used to correctly install Flash.

Thankfully it's easy to do.

@p_quarles, agreed, I use 64-bit Xubuntu 7.10 and I've found it's just as straightforward to use as 32-bit, with one exception and that's installing Flash.

---

### Post by fuscia on 2008-01-19
> **billgoldberg said:**
> I feel that in the "absolute beginners section" it should be recommended to use the gui way of doing things.

i totally disagree. as an end user, i feel it's safe to say that any retard can learn cli. it's far more standardized than guis and it's a waste of their time to expect someone with skill to learn the layout of some stupid app just to help you.

---

### Post by vexorian on 2008-01-19
> **jleaker01z said:**
> I have noticed that experienced Ubuntu users who try to help new Windows converts that have problems like to say "open a terminal and type in these commands: blah blah" even when those packages are available via the add/remove programs or synaptic.  My question is, WHY?  This does several things:

1.  It reaffirms to the converts that Ubuntu is complicated and impossible to run without using a command line

2.  Reaffirms that Linux is for geeks

3.  Completely frustrates a Windows user who has possibly never used a command line in their life (I've been around since DOS days, but lots of younger people have never used anything but Windows)

It seems to me that if we would like to convert more people away from Windows, we should emphasize the GUI ways of installing packages.  I realize that for the experienced it can truly be easier to simply issue the command at the command line, but it may not be so easy to someone who has never seen a command prompt.

So again, I ask Why?

GUI is great for self-learners.

However, the CLI is perfect for solving someone else's solution remotedly or passing instructions in a non-ambiguous way.

Try explaining a total windows newb how to move the contents of a folder to another by just text, it is hard, you need to write a whole *tutorial* with images and perhaps animations so he can get it.

Edit: You say "2.  Reaffirms that Linux is for geeks" as if it was either false or a bad thing that Linux is for geeks. It is a kernel made by geeks for geeks. Things like gnome or KDE or whatever are the ones that are supposed to allow to make it a little more inclusive. But you'll always need to be a geek to use a computer, it is not different for windows or Mac OS/X.

Edit III: I recommend CLI for the absolute beginners forum, because newbs don't really want to learn, they almost always want solutions, not learning. You may give those guys that, mistakenly, think the CLI makes Ubuntu less friendly or that it is a thing of the past (ignorance allows you to say quite a bunch of false things like that) but it is simply more convenient to tell them a CLI command.

---

### Post by kelvin spratt on 2008-01-19
I came from windows if it hadn't been for GUI I would of gone back thats for sure. Linux is a learning curve a very steep learning curve. And needs time to learn most 1st time users do not know what a package manager is let alone how to use CLI.  That's what I thought the absolute beginners section was for? Instead half written CLI commands are  thrown at them that don't work half the time because they are not spelled or laid out exactly as it should be or sudo is missing? Just give New users some time you never know down the line they just might help you?

---

### Post by Lostincyberspace on 2008-01-19
yes cli should be banned from the beginners help section unless it is also explained out precisely how to do it in a gui form too.

---

### Post by broekskw on 2008-01-19
i am a new beginner again tried it about 11/2 years ago. found that the command line from terminal was very hard to use but with all the help here got up and running. but i did screwup my system 3 times so installed win xp again.

but back at it with ubuntu 7.10 dual boot xp and ubuntu, have to say that this time got everything going much faster right from live cd install (every update gets better and better was using 6.10) 

would like to learn how to install everything from a terminal instead of add/remove, that makes ubuntu very interesting ( also free has a lot to do with the switch)

what dose cli and gui stand for??

without this site i think i would never have switched again, i have 3 computer 1 with ubuntu and xp and the others with xp,but in the next month will switch all over to ubuntu and xp dual boot,

hats off to all here that keep helping the new people convert over:lolflag:
hope in time to also convert family and friends to ubuntu:lolflag:

---

### Post by SunnyRabbiera on 2008-01-19
me i always try to introduce someone to a GUI alterntative as CLI can be intimidating.

I wish people telling others to open up terminals would stop to be honest

---

### Post by nick_h on 2008-01-19
> **popch said:**
> I, for instance, am posting to an English language forum. However, my installation is not in English as I prefer installing the software in my native language. Therefore, I am often at a loss as to what the buttons, texts and menues might be called in the installation of the Newb asking for assistance. Even worse, the Newb's installation might not be in English, either.

Good point.  Perhaps people using these forums should be encouraged to fill in the location section of their profile if they use Ubuntu in language other than English.  I also tend not to mind bad English when the user is from a non English speaking location.

Filling in the Ubuntu versions is also helpful when answering questions - especially when GUI answers are required.

---

### Post by p_quarles on 2008-01-19
> **SunnyRabbiera said:**
> me i always try to introduce someone to a GUI alterntative as CLI can be intimidating.

I wish people telling others to open up terminals would stop to be honest
What is dishonest about asking someone to open a terminal? 

If you have read this thread carefully, you'll see that there are several very valid and so-far unrefuted reasons for answering support questions with terminal commands.

---

### Post by SunnyRabbiera on 2008-01-19
> **p_quarles said:**
> What is dishonest about asking someone to open a terminal? 

If you have read this thread carefully, you'll see that there are several very valid and so-far unrefuted reasons for answering support questions with terminal commands.

Its not likes its dishonest, but its confusing for newcommers...
teach people more simple things first like using synaptic or something, don tell them just to open up a terminal otherwise it gives us a bad rep...

---

### Post by nick_h on 2008-01-19
> **jleaker01z said:**
> And lets be honest here.  Windows users are used to seeing 'click start>programs>blah blah' therefore it stands to reason that they will be better able to understand 'click system>preferences>blah blah'.  Chances of you having to describe every click is low, as long as the new user is familiar with Windows.

True, it is easy to direct users to Synaptic and assume that they can search for the name of the suggested package.  Also most new users will be using Gnome.

I tend to assume that users who appear more experienced prefer the CLI.  Perhaps this assumption is wrong?

---

### Post by orange2k on 2008-01-19
> **fuscia said:**
> i totally disagree. as an end user, i feel it's safe to say that any retard can learn cli. it's far more standardized than guis and it's a waste of their time to expect someone with skill to learn the layout of some stupid app just to help you.

Hehe, thats really true...
Its much easier to type some commands in the terminal than to navigate through cryptic menus of a gui, especially if you cant get the gui to show up properly, anyways...

CLI, on the other hand, is like a portal to another dimension where you only need some magic words...

---

### Post by p_quarles on 2008-01-19
> **SunnyRabbiera said:**
> Its not likes its dishonest, but its confusing for newcommers...
teach people more simple things first like using synaptic or something, don tell them just to open up a terminal otherwise it gives us a bad rep...
How is opening a terminal any more confusing than opening Synaptic?

Seriously, there have been many reasons given in this thread. If you really believe what you are saying (no terminal commands should be given) then how would you respond to these problems:
[LIST]
[*] We often don't know what desktop environment the user is running
[*] Not everyone who posts here has an English language installation -- the buttons are different, but the commands are the same
[*] Some people (like myself) don't use Gnome, KDE *or *Xfce -- we can tell people what to do from the command line, but may get mixed up or misremember how to do things from Gnome GUI tools, leading only to more confusion
[*] It takes a long time to explain the steps that go into working with a GUI tool
[*] Screenshots being posted to answer every question in ABT (or even 1/8th of them) would tax an already busy server.
[*] These are busy forums, and enough questions go completely unanswered as it is[/LIST]

---

### Post by SunnyRabbiera on 2008-01-19
> **nick_h said:**
> True, it is easy to direct users to Synaptic and assume that they can search for the name of the suggested package.  Also most new users will be using Gnome.

I tend to assume that users who appear more experienced prefer the CLI.  Perhaps this assumption is wrong?


yes, as they are used to it.
this is something way too common, me i only say open a terminal when I see it might be needed but most hardcore linux fans rely on the terminal heavily.

---

### Post by plun on 2008-01-19
Perhaps its time to learn all users about the help file...
[B]
Menu System >  Help & Support[/B]

About packages (included in every dist)

[https://help.ubuntu.com/7.10/add-applications/C/add-applications-introduction.html](https://help.ubuntu.com/7.10/add-applications/C/add-applications-introduction.html)

:)

---

### Post by jleaker01z on 2008-01-19
> **p_quarles said:**
> How is opening a terminal any more confusing than opening Synaptic?

Seriously, there have been many reasons given in this thread. If you really believe what you are saying (no terminal commands should be given) then how would you respond to these problems:
[LIST]
[*] We often don't know what desktop environment the user is running
[*] Not everyone who posts here has an English language installation -- the buttons are different, but the commands are the same
[*] Some people (like myself) don't use Gnome, KDE *or *Xfce -- we can tell people what to do from the command line, but may get mixed up or misremember how to do things from Gnome GUI tools, leading only to more confusion
[*] It takes a long time to explain the steps that go into working with a GUI tool
[*] Screenshots being posted to answer every question in ABT (or even 1/8th of them) would tax an already busy server.
[*] These are busy forums, and enough questions go completely unanswered as it is[/LIST]

Its not confusing to YOU...to a new user who has never seen a command prompt it is a completely foreign language.

For your points:

1.  A new user is likely using the default desktop, Gnome
2.  Perhaps someone with the same language installation would be willing to help
3.  Give someone who is familiar with GUIs the chance to respond if you dont know.  CLI should be a fallback solution for new users, not the primary one.  Giving someone a CLI solution just means the next time they run into a problem they come back so someone can tell them the CLI solution.
4.  Saying click applications>add/remove is something someone familiar with windows can understand with no problems.
5.  Who needs screenshots.  Saying click System>Administration>Synaptic then search for what you are looking for is easy to understand...this is like a continuation of #4
6.  If the new users become aware of the GUIs and how to search for what they are looking for, they post less and fewer questions go unanswered as they can figure it out for themselves.

Does a GUI solution work for everyone?  Absolutely not.  Are there really stupid people out there who, when prompted to press any key, have to ask someone where the 'any' key is located?  Yes, but there arent that many of them.  Empower the new user and they wont need help nearly as often.  Most people arent that dumb.  But suggesting CLI solutions makes the new user feel that they HAVE to learn the CLI to use Ubuntu, which is not true.

---

### Post by gn2 on 2008-01-19
> **broekskw said:**
> what dose cli and gui stand for??

Graphical User Interface (= Point-and-click does the trick :))

Command Line Interface  (= Good for emergencies but useless if you don't know or can't remember the commands)

---

### Post by p_quarles on 2008-01-19
> **jleaker01z said:**
> 1.  A new user is likely using the default desktop, Gnome
What if they're not? What if they're using Kubuntu or Xubuntu, and weren't even aware that things worked differently in them? 

> 2.  Perhaps someone with the same language installation would be willing to help
How do you know what language the user requesting help is using? 

> 3.  Give someone who is familiar with GUIs the chance to respond if you dont know.  CLI should be a fallback solution for new users, not the primary one.  Giving someone a CLI solution just means the next time they run into a problem they come back so someone can tell them the CLI solution.
Okay, so let's say I'm going to help someone properly configure a root-writable text file. What you're suggesting, is that instead of saying "open a terminal and type 'gksudo gedit /etc/apt/sources.list'," I should instead say the following:
> Open your menu editor by right-clicking on the Ubuntu logo. Add a new item, and call it "Root Text Editor." In the "command" field, enter "gksudo gedit." Now, save this, and open that application from your menu. Now, use the "open" dialogue, and browse to the root filesystem, where you'll find a directory called "etc." Go there, and then enter the "apt" sub-directory. Now click on the file called "sources.list."
This takes far more of my time, and is *far more likely to confuse the person requesting help*. Plus, in order to give this advice, I would have needed to confirm that the person was using Gnome. So, there's an example of a terminal-free solution that I am qualified to give, but wouldn't unless specifically asked. 

> 4.  Saying click applications>add/remove is something someone familiar with windows can understand with no problems.
Absolutely. When that's relevant to the problem and I sense that the user is very new, that's what I say. Not all problems are fixed by installing things, however.

> 5.  Who needs screenshots.  Saying click System>Administration>Synaptic then search for what you are looking for is easy to understand...this is like a continuation of #4Same as my response to #4.

> 6.  If the new users become aware of the GUIs and how to search for what they are looking for, they post less and fewer questions go unanswered as they can figure it out for themselves.
Some of the GUI configuration tools can be just as if not more complex than the command line. A user's awareness of gconf-editor or the CUPS web config page isn't going to make their questions go away.

---

### Post by vexorian on 2008-01-19
I find some posts fun since they seem to imply beginners have the right not to be confused :) , My pack of suggestion is:

- We get a generic manual/tutorial about the CLI.
- Whenever you help someone and CLI is required we post a link to it as a prerequisite.

---

### Post by fuscia on 2008-01-19
> **orange2k said:**
> CLI, on the other hand, is like a portal to another dimension where you only need some magic words...

i like that. as an end user, and knowing mostly end users, i know that guis aren't all that clear either. if they were so wonderful, no one would ever need any help. they'd just stumble stupidly through life until they got hit by a car, or something.

---

### Post by jleaker01z on 2008-01-19
> **p_quarles said:**
> What if they're not? What if they're using Kubuntu or Xubuntu, and weren't even aware that things worked differently in them? 


How do you know what language the user requesting help is using? 


Okay, so let's say I'm going to help someone properly configure a root-writable text file. What you're suggesting, is that instead of saying "open a terminal and type 'gksudo gedit /etc/apt/sources.list'," I should instead say the following:

This takes far more of my time, and is *far more likely to confuse the person requesting help*. Plus, in order to give this advice, I would have needed to confirm that the person was using Gnome. So, there's an example of a terminal-free solution that I am qualified to give, but wouldn't unless specifically asked. 


Absolutely. When that's relevant to the problem and I sense that the user is very new, that's what I say. Not all problems are fixed by installing things, however.

Same as my response to #4.


Some of the GUI configuration tools can be just as if not more complex than the command line. A user's awareness of gconf-editor or the CUPS web config page isn't going to make their questions go away.

1.  Ask.  Or if you give the default (Gnome) you will know when they say, that's not on my screen.

2.  Same as 1

3.  Give the command line way.  Im not referring to things like that.  I am referring to things like installing the mp3 codecs which are within add/remove, changing user passwords, simple things.

6.  I am saying use the GUI for things like Add/Remove, Synaptic, Print Manager, User/Group manager and the archive manager.  These are simple, self explanatory (once the newb realizes they exist), and in at least some cases will work just like the windows equivalent.  

When you give a CLI solution to what can be simply done with a GUI, it confuses, frustrates, and does nothing to help the new person learn how to use Ubuntu, nor does it encourage them to keep using it.  It only makes them dependent on others, and more likely to revert back to Windows.

Ubuntu is not hard at all to use, and rarely is the command line essential for something a NEW user wants to do.

---

### Post by gn2 on 2008-01-19
> **jleaker01z said:**
> When you give a CLI solution to what can be simply done with a GUI, it confuses, frustrates, and does nothing to help the new person learn how to use Ubuntu, nor does it encourage them to keep using it.  It only makes them dependent on others, and more likely to revert back to Windows.

I agree. Lack of GUI configuration tools in Ubuntu 6.06 and getting complex and confusing CLI based help drove me to switch to PCLinuxOS.

Now I have more knowledge of Linux, Ubuntu has improved and I use it again.

---

### Post by p_quarles on 2008-01-19
> **jleaker01z said:**
> I am saying use the GUI for things like Add/Remove, Synaptic, Print Manager, User/Group manager and the archive manager.  These are simple, self explanatory (once the newb realizes they exist), and in at least some cases will work just like the windows equivalent.
The fact that they exist is also pretty self-explanatory. They are all easily accessible via menus in the default installation. I would say that the *vast* majority of support questions to which I respond would not be resolved through the exclusive use of the tools you mentioned. In some cases, such as installing the restricted extras, yes: all you would need is Synaptic. The question, though, 9 times out of 10, is about the name of the package (what to search for) rather than a failure to notice the package manager GUIs. In such cases, I would normally say "use your preferred package manager to install 'ubuntu-restricted-extras'," followed by the optional command-line instructions. 

Yes, you could respond to every post by first asking people what version of Ubuntu they are using, and which language localization settings they are using. Or, the new users could ask -- upon receiving a command they find confusing -- if a GUI alternative exists. 

This is a friendly community, and most of us respond well to follow-up questions. But it is a community and not a help desk. If I have a solution that will work, I'm happy to share it. I'm not going to fall all over myself to ensure that no one encounters something unfamiliar.

> When you give a CLI solution to what can be simply done with a GUI, it confuses, frustrates, and does nothing to help the new person learn how to use Ubuntu, nor does it encourage them to keep using it.  It only makes them dependent on others, and more likely to revert back to Windows.
I just don't agree. If it fixes the difficulty they were having, why would they become confused, frustrated, or stop using Ubuntu? I would think it would allow them to get more out of it, and to continue to use it long enough to learn how to do things independently. 

Many people do precisely what you are asking already, and I think that's a good thing. I encourage you and anyone else who wants to do this as well. But please don't tell me that I shouldn't use my own judgment in choosing a method of offering support to new users.

---

### Post by Espreon on 2008-01-19
There are many good reasons to not use 100% GUI

1. Being 100% GUI is like living in your parent's house forever

2. CLI is usually faster than GUI, for example if I install package XYZ with GUI it has to install the package and render the GUI on your monitor while with CLI it only has to install the package and optionally echo things

3. GUIs can sometimes be confusing especially when dancing from distro to distro

4. All the cool kids are using the CLI

Also I am a young person (9th grader) and the CLI is not confusing, you just need to learn it.

Infact if you took a person whom never used a comp and gave them a 100% CLI setup (then they learn how to use it competently) as most Winblows users are 100% GUI then that person could find GUIs confusing as Windows users mostly find the CLI confusing...

---

### Post by MNICY on 2008-01-19
Same as everyone else said.

It is simply easier for both the helper and the person being helped.

you may think it is harder, but really, its not.

And remember, Linux is NOT windows.

---

### Post by amadeus266 on 2008-01-19
> **orange2k said:**
> Even today, people still think that machines are going to take their jobs and robots are going to replace them.

You wouldn't think that is so funny if it happens to you. I was replaced in my last job by A ROBOT!!! Me and 8 other people replaced by a single machine!!! O.K. done ranting.:lolflag:

But just to put my two cents in on this topic... I happen to be a network administrator so dropping to the CLI even in Windows is sometimes an absolute necessity. When I have asked for help here in these forums, most of the responses I got were using the terminal and I have to agree that it is the most "efficient" way of helping someone solve a problem. It probably also helps that I have developed a habit of taking extensive notes when I discover a problem and include all the information I can find about how to solve said problem. When I assist people using Windows the first thing I do is hand them a notepad and tell them to write down what the problem was and how I helped them fix it whether it was at the "command prompt" or using the GUI. So I don't get called back for the same problem over and over again. I know very little about linux CLI commands and what they do but I am learning more from the help I get from suggestions that use them.

---

### Post by kelvin spratt on 2008-01-20
[quote=Espreon;4169686]There are many good reasons to not use 100% GUI
2. CLI is usually faster than GUI, for example if I install package XYZ with GUI it has to install the package and render the GUI on your monitor while with CLI it only has to install the package and optionally echo things

So if you use CLI the package does not need to be downloaded its just sitting their waiting in the terminal? I also use Arch which is all CLI but like many others I use jacman to find things I want to install using pacman. Try typing sudo apt-get install media player what do you get. So add/remove does make sense  to a new user and older user for programs. Patience is what you need with a new user, Till they find their feet nobody knows it all, Lots of people think they know it all after 58 years I really know nothing just a bit of this and that and a lot about life, that does not make me an expert? When you teach a child to read you start with the ABC you don't just throw a dictionary at them, Linux is the  same GUI then you can move on to the Command line and terminal.

---

### Post by macogw on 2008-01-20
> **Lord Illidan said:**
> CTRL + C exits a running process in the terminal. Just learn to use shift-insert ,or even Edit - Paste.

I usually prefer using console to help people out with. It's faster, and they get to learn more about the terminal. You can get by in Windows without knowing about the terminal, but in Linux, you are losing an amazing amount of functionality by not knowing how to use it.
> It was a mistake to think that GUIs ever would, could, or even should, eliminate CLIs.
– Jeffrey Snover (Architect of Windows PowerShell)


Apparently Windows' full functionality requires a terminal too.  I've no idea how one would do a ping test in Windows without cmd.exe.

---

### Post by macogw on 2008-01-20
> **Espreon said:**
> ]
Infact if you took a person whom never used a comp and gave them a 100% CLI setup (then they learn how to use it competitively) as most Winblows users are 100% GUI then that person could find GUIs confusing as Windows users mostly find the CLI confusing...

You just described my mother.  She used to use the machines with the gigantic tape drives and she had to type numbers in and they'd go into the computer so they'd calculate measurements for an engineering company.  About 15 years later we tried to get her to use Windows.  It confused her to no end...left click, right click, double click...all these extra things to remember!  She knew how to type, but what's with all this sliding things around on tables?

Heh....she uses Ubuntu now, and only from the GUI.  She doesn't know bash now, if she ever did know it (I'm guessing she only knew how to use some single text-based program).  Windows's GUI was too complicated for her.  I mean, text-based programs give you maybe 5 or 6 options at a time usually, and they're also usually designed to use categories so it's easy to find what you want.  The GNOME Menu does that too.  The Start Menu in Windows defaults to completely illogical ordering of menus and showing about 50 options at once instead of a few and allowing the user to drill down, as a text-based interface usually would.

---

### Post by gn2 on 2008-01-20
> **macogw said:**
>  I've no idea how one would do a ping test in Windows without cmd.exe.

Download and install the free version of Ping Plotter.

---

### Post by theDaveTheRave on 2008-01-20
Hello All.

Firstly forgive me if I repeat anything already said, I feel a need to write to this post even though I have only read the first page.

To make a few points on some other posts first.

Understanding the working of computers! No NOT REQUIRED TO BE A USER, I don't understand much about brain neurology, but I do know that somehow it controls my breathing! And computers getting faster! 

They will only match us for pure processing power when you can throw a ball (maybe a tennis ball) and strike it whilst it travels at something like 80 mph with a stick that is half the size of the ball - an activity that most 5 or 6 year old are able to accomplish without know how they do it - see above paragraph.

onto the main point, CLI or GUI.

Does anyone really care?? I have a neighbour who although close to his septegenarian decade is more than happy with windows and the GUI - if he asks me for help I point him through the steps. The main problem is that I don't have the same "programs" on my system as he does, and so can't ensure that I am pointing to the right place when I do screen shots (highlighting them with boxes),

When I do help out anyone else (admittedly I am only a fair newb myself), I will try to give explanations of what I am doing to impart knowledge.

Possibly there is a case for all of the major howtos to have a GUI equivalent, is this an opportunity for the creation of a new group in the forum staff - "the GUI Group", their remit would be to hunt down any forums that are "popular" howtos and convert them into a child thread that gives the same instructions in GUI format?

Or perhaps a reward system for any newb who has used a howto and then been able to convert it into a GUI instruction (for instance the allowance of animated avatars - something that was removed not long ago).

Anyway, GUI instructions would be good, but often more difficult to trouble shoot when things don't work the way that you expect!

Dave

---

### Post by K.Mandla on 2008-01-20
> **jleaker01z said:**
> My question is, WHY?  
Because in some cases, the command line is the only commonality between interfaces. I use Openbox, maybe you use KDE and somebody else uses Gnome. How do I help you fix something? By pointing you at the one tool we all have on hand and can expect to behave the same way.

---

### Post by Christmas on 2008-01-20
This has already been discussed many times before.

1. It's faster
It's faster to say "Open Terminal/Konsole and type 'sudo apt-get install app_name' than "Go there, click there under that button which looks like that, finally click on the right button (the one in that tab). Screenshot included!"

2. It saves bandwidth (for those who care)

3. Console is usually faster and more powerful than CLI
Think of working on very large directories with many types of files, mass moving or renaming only certain kind of files etc, not to mention that once you have a program which runs in text mode you can build a GUI for it easily.

4. I can think of the output of some commands. Some poorly designed GUI tools don't offer an output if they fail. So you click on something, nothing happens and you ask why? Running the same application in the shell usually shows you output so you can troubleshoot problems.

Also, there are several desktop environments and GUI tools to do one thing. A person helping another person would have to ask what DE he uses, what program, eventually install it itself to troubleshoot the other's problem. In CLI, he could only point to several universally available commands.

---

### Post by ice60 on 2008-01-20
when everyone was new to linux they would have been given CLI commands, and it didn't stop any of us did it?

i probably use gui tools about 60% of the time, but if i'm using a term i'll just stay there. i'm probably odd because i find a lot of tasks take the same time to do with a GUI as a term :|

---

### Post by armandh on 2008-01-20
about the only thing I remember from dos commands was copying the whole hard drive with "xcopy C:\ D:\ /h/e/c/k/r" I am soooo happy to have found a linux distro that is 99.44% gui. at least when I do have to use the CL I stick to copy/paste from trusted sources because [unlike the gui] I can powerfully screw it up too. most of my reloads have come after some CL work. but mostly because reloading is much easer than fixing [for me]

---

### Post by billgoldberg on 2008-01-20
Another good reason to give newcomers the gui way of doing things is that they will be able to help themselves the next time.

I someone asks how to install program xxx and they get the cli way of doing things, they will have no idea how to install another program. If they are redirected to synaptic of add/remove they will know how to do it the next time and they will discover other software, thus they don't have to ask for a program that can do xxx.

This goes for other things too.

Like adding repositories. The cli way is easy, but you give that way in the absolute beginners forum, they won't know how to do it again a couple of days/hours later, thus they will have to search for their previous post and this will frustrate them. If you tell them synaptic -> settings -> repositories -< third party software -> add. They will remember that and will never forget.

You see the point i'm trying to make.

Once someone gets use to the gui way and they are intrested in a faster/other way of doing things, they have to option to use the cli, but it shouldn't be forced on them by the experienced users.

(i noticed someone asked what cli and gui was:
cli: command line interface (terminal)
gui: graphical user interface )

---

### Post by billgoldberg on 2008-01-20
> **ice60 said:**
> when everyone was new to linux they would have been given CLI commands, and it didn't stop any of us did it?

i probably use gui tools about 60% of the time, but if i'm using a term i'll just stay there. i'm probably odd because i find a lot of tasks take the same time to do with a GUI as a term :|

True, but ubuntu is trying to gain a bigger market share and the cli has the "nerd" image attached to it.

---

### Post by vanderwaltenator on 2008-01-20
i am as new as it gets and have been using my ubuntu box only for evolution as an email/contact machine for the last 6 months.
not too long ago i felt a bit adventurous and shared folders on my windows box to show on my ubuntu box.  took me a while but i figured it out eventually.
two days ago i felt brave and decided to share a folder on ubuntu to show on windows - let's just say i took a blind leap of faith and fumbled my way through [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) 
(great thread BTW, thnx stormbringer)
and got it working.  excellent!!!
till i get to my desk this morning to find that it doesn't work anymore.  bummer.
the short of it all is that even though i get excited about trying out new things, like ubuntu, i don't have the time or CLI experience or inclination to be fiddling with commands all the time.  all i want really is an alternative to windows that works; i want to get on with my REAL job and don't necessarily want to spend my sunday evening trying to fix something that should not have been broken because of curiosity...

---

### Post by sajro on 2008-01-20
I was a GUI junkie befor eI moved to Linux. Now, I'm quite technical for a 13-year-old, but I'd always shied away from the command line. Then I wanted to play my MP3s in Amarok but the "Install codec" window was all weirded up.

Then I opened an xterm, and. par instructions, type "sudo apt-get install libxine-extracodecs". Since then, I've been hooked on the CLI. It's so fast and powerful. Much easier than digging through the add/remove programs search function.

In fact, when I dumped the WinME on my "craptop" (Thinkpad 380XD) for Damn Small Linux, I stopped using file managers. No Nautilus, no Dolphin, no Emelfm, no Midnight Commander. My file manager consists of: ls, cd, mv, cp, rn, and a couple other commands.

So, even someone who was literally afraid of the command line when using Windows can fall in love with the command line in Linux.

---

### Post by jleaker01z on 2008-01-20
Heck with it nm

---

### Post by Lord Illidan on 2008-01-21
> **macogw said:**
> – Jeffrey Snover (Architect of Windows PowerShell)


Apparently Windows' full functionality requires a terminal too.  I've no idea how one would do a ping test in Windows without cmd.exe.

Indeed, that was the only reason some Windows users used to use CLI, I believe. I remember telling my friends to open the terminal and type ipconfig.

---

### Post by vanderwaltenator on 2008-01-21
here is another question along the same line of thought:
how many hours/days/weeks did it take for you to work comfortably and with confidence within the CLI environment.  put this into context with how user friendly a GUI environment is for a newb vs CLI...

as a person with no programming back ground the visual representation of where you are and what you are doing, in a GUI,  helps me understand what i'm supposed to achieve where as with CLI i kinda just take who ever is willing to help's word and follow instructions like a parrot without really understanding what i'm doing...

i'm sure i will also be a happy larry one day when i'm fluent in ubuntu/linux/CLI but in the meanwhile it's more of an effort than a pleasure.  something i am willing to do to help stop the monopoly that is windows!  but this is not my day job or my favourite past time but merely an interest.  it would be easier to try and convince my friends and colleagues to try out ubuntu if it was easier/less time consuming to get one's way around in the CLI environment.

viva open source, viva!

---

### Post by banewman on 2008-01-21
Isn't the recovery console in windows cli? Just working on heresay for that comment. :)

---

### Post by mdsmedia on 2008-01-21
> **jleaker01z said:**
> I have noticed that experienced Ubuntu users who try to help new Windows converts that have problems like to say "open a terminal and type in these commands: blah blah" even when those packages are available via the add/remove programs or synaptic.  My question is, WHY?  This does several things:

1.  It reaffirms to the converts that Ubuntu is complicated and impossible to run without using a command line

2.  Reaffirms that Linux is for geeks

3.  Completely frustrates a Windows user who has possibly never used a command line in their life (I've been around since DOS days, but lots of younger people have never used anything but Windows)

It seems to me that if we would like to convert more people away from Windows, we should emphasize the GUI ways of installing packages.  I realize that for the experienced it can truly be easier to simply issue the command at the command line, but it may not be so easy to someone who has never seen a command prompt.

So again, I ask Why?Once again, as a Windows user and Linux Noob, the command line response is easier...and it's universal. GUI depends on so many irregularities, while CLI doesn't.

CLI is simple in that you copy and paste a command.

GUI is not universal. It depends on versions, distros.

CLI is so much easier to give to the questioner. It is much simpler than trying to explain where to go in the GUI.

In a way I think if Windows converts want to convert they need to know about the CLI. I don't know that we're that desperate that we have to stoop to Windows levels just to accomodate Windows converts.

I'm a Windows convert and I accept CLI. I embrace CLI. I'm an ex-DOS user and hate that it's so hard sometimes to use the keyboard solely in Windows. My mouse died today and it was only my knowledge of pre-mouse days that allowed me to recover it. It turned out to be a battery problem, but it could have been a software, or even a hardware, problem. The GUI is too reliant on the mouse. Knowledge of CLI isn't a bad thing, and though it's become a thing of the past in Windows, I love that it's still around in Linux.

CLI, in some ways, is simpler than GUI. Windows users think GUI is simpler....but only when it works. Then they have techs coming in and using the Windows CLI to solve problems. Ask any Windows tech if they can get by without CLI. And I say this as a non-IT professional.

---

### Post by rosegarden78 on 2008-01-21
> **jleaker01z said:**
> I have noticed that experienced Ubuntu users who try to help new Windows converts that have problems like to say "open a terminal and type in these commands: blah blah" even when those packages are available via the add/remove programs or synaptic.  My question is, WHY?  This does several things:

...

So again, I ask Why?

Most interesting ... I seem to find myself even guilty of this.  I think it's because Linux doesn't seem like one flavor.  So while you have GUI like kde and gnome and nautilus, sometimes you have to launch nautilus from Xterm when you're using Blackbox Ubuntu.  So it's a case-by-case basis but I think as a whole the many flavors confound those accustomed solely to GUI.  I raised the issue of intellectual de-fragmentation in an earlier thread.

---

### Post by hyper_ch on 2008-01-21
> **vanderwaltenator said:**
> how many hours/days/weeks did it take for you to work comfortably and with confidence within the CLI environment.

I might ask the same:

"hwo many hours/days/weeks did it take for you to work comfortably and with confidence within the GUI environment?"

---

### Post by Flyingjester on 2008-01-21
well, i've got to say, when i was a linux noob (now there are stil LOADS of things I don't know) i had no problem getting CLI instructions, they were simple and to the point. and like previously stated i could even copy and paste them.

---

### Post by red_Marvin on 2008-01-21
I cut my teeth on ms dos, so I have never feared the cli way of doing things, it might explain mi wiewpoint.

What I can't understand is why some thinks that the cli way is inhererently more confusing than the gui way. As a reference, read [this]("http://ubuntuforums.org/showthread.php?t=637146") thread which illustrates a couple of the problems that can appear when helping gui configuration from a remote position:
- Language (translating from A to B -if neither of A or B is english theres two translation steps with possible misunderstandings).
- Bandwidth (images sometimes neccesary).

Imagine a problem more complex than this and the postcount will grow.

Please note that I have no problem with helping people with gui problems, I just want to challenge the view of gui as being the easiest way and cli as a neccesary evil for special tasks.

---

### Post by vanderwaltenator on 2008-01-21
> **hyper_ch said:**
> I might ask the same:

"hwo many hours/days/weeks did it take for you to work comfortably and with confidence within the GUI environment?"

fair enough, it did take me some time as i am not a IT professional.

I agree that CLI (for the basic stuff that i have attempted so far) was easy to understand but there are a lot of things that are not as intuitive as with a good GUI.  not that the GUI environment is perfect... hey no way!

---

### Post by lespaul_rentals on 2008-01-22
Which is more simple:

"Please type the following into Terminal:"

```
sudo apt-get install bridge_utils
```

OR:

"Please go into Add/Remove Programs, enter your password, search for bridge_utils.  Oh yeah, now I remember, it's not there.  Okay, close it, go into Synaptic Package Manager.  Search for it there.  Go buy some food at the store while it installs."

---

### Post by gn2 on 2008-01-22
> **lespaul_rentals said:**
> Which is more simple:

"Please type the following into Terminal:"

```
sudo apt-get install bridge_utils
```

OR:

"Please go into Add/Remove Programs, enter your password, search for bridge_utils.  Oh yeah, now I remember, it's not there.  Okay, close it, go into Synaptic Package Manager.  Search for it there.  Go buy some food at the store while it installs."

One method will teach how to copy and paste a command to install a known package name, the other will teach how to look for and install all manner of software.
And a walk to the store will be good excercise!

---

### Post by insineratehymn on 2008-01-22
Gotta say, I agree aysiu on just about everything they said.

Wanna add a few points:
-Linux is NOT Windows, no matter what GUI you put on it or what it looks like. You can say that the bash(c/ksh/bsh) is for geeks, and you would probably be right. I'm a geek and damn proud of it.

-The CLI is the most efficient way of getting anything done, as aysiu said the GUI is really only helpful if you are standing right next to the user, and even then it can get frustrating if you are a native gnome'r and they are a kde monster. 

- If you want to use any *ux system, you will have to use the CLI; it is unavoidable. I say, the earlier you can introduce them to it, with simple commands of course, the better. Thank god we have programs like aptitude that can let them get use to the whole syntax/symantics of the bash, and we don't have to "get their feet wet" doing something like mounting a CD drive, or editing their vhosts file, or doing some major system recovery.

Bottom line; the earlier you learn how to use the bash efficiently the better *ux user you will be. Sure its possible to get around and do (pretty much) everything you want to do without it, but if your system goes down and you have sensetive data on it and a format is not an option, it would be easir to do so if you knew what the ls command did, or the cd command, or the ln command, etc....

---

### Post by hyper_ch on 2008-01-23
> **gn2 said:**
> One method will teach how to copy and paste a command to install a known package name, the other will teach how to look for and install all manner of software.
And a walk to the store will be good excercise!

Most people don't want to learn anything at the moment they have a problem, they just want a solution for that problem.

Posting a cli command solves that problem, the person is happy...

If that person however wants to learn, this person will then ask what that command does. If he doesn't want to learn, then he won't ask and just be happy that the problem is solved.

Let's face it, most people don't care how a problem gets solved, as long as it gets solved and that they can go doing whatever they want on their computer.

---

### Post by gn2 on 2008-01-23
> **hyper_ch said:**
> 
Let's face it, most people don't care how a problem gets solved, as long as it gets solved and that they can go doing whatever they want on their computer.

That's certainly true of the majority.

I'm of the opinion that there is no "best method" for providing assistance, sometimes CLI will be best, in other circumstances, like the one I mentioned earlier in the thread, GUI is easier.

---

### Post by ktmom on 2009-04-05
As a Newb, I prefer the answer to my question in CLI.  It's quicker and gets me going.  One reason I have worked so hard to become competent in Ubuntu is the opportunity to run a less bloated OS.  There are plenty of tutorials for general things like installing programs in GUI.  If you are posting before spending the time reading through those, and you still want help, then be thankful for what help you get CLI or GUI.

I installed dual boot so I could do what I had to when I had to in the OS I already knew.  I spend almost no time there these days.  Only for the scanner which is not supported (yet?) and because I just haven't had time to figure out how to get my 537EP modem working (although I've bookmarked a how to). 


> **Mateo said:**
> When you talk of retention you are no longer talking about helping the user do what the user is asking.  A user is who asks how to get xvid videos to player only wants their xvid videos to play, not to become a pawn of someone's evangelical mission.

+1

Ultimately, whether someone switches from some other operating system to a Linux based one will not be determined by the support being based on GUI or CLI.  The way you have to think to be comfortable in Linux is different than in non-Linux/Unix based OS.

It requires that you be willing to "start over" even though it's not starting over from no knowledge at all if your coming from some computer experience.  But often people find it harder to unlearn their habits than the value *they* get from the new OS.

With all of the car metaphors that float around here, consider the following;

A decade or so ago, a car manufacturer arrive in the US.  They produced extremely low cost cars, with a then unheard of 10 year warranty.  People bought these vehicles and then had different experiences.  Some felt that in spite of the warranty and loaner vehicles being provided, the time they spent trying to deal with the lack of reliability wasn't worth the savings.  Others felt the savings in $$ was a bigger deal than the time to go drop the car off at the dealer time and again.  The net result is that particular manufacture is still around, and still serving it's client base, and slowly gathering additional clients as they work the bugs out.  

Will they take over the world?  Never.  There is to much competition and to many drivers whose personal image is based on the brand they drive.  We might think those people shallow, and maybe some are, but you'll also find that when they tried a new brand of car, their experience was different and they went back to tried and true because getting used to something different wasn't worth the effort.

My point is, please don't assume that if only assistance was provided in a GUI style, that all users would be happy.  There are plenty of people who try out Linux, find it doesn't suit for whatever reason and switch back.  If they are ever to return though, their experience with the patience and friendliness of people trying to help them, will be remembered.  

Any time we allow our personal enthusiasm to become overwhelming, we run the risk of sounding like we are on an "evangelical mission".  Humanity would be well served in developing the ability to allow slow change.  Maybe our short life spans preclude that patience, but only time can win people over.

> **popch said:**
> 
Therefore, the one line instruction given earlier in this thread might give rise to much consternation when the installations are not in the same language.

... and therefore impact the number of people available to help me.  Thanks to all of the English as a 2nd language people who help!  IMHO, it's one of the beauties of open source.

> **Lord Illidan said:**
> What blindly enrages me is how some people **never read** any error messages, or try to make sense of them.


The same people who can not or will not search before they post a question.  Critical thinking is not common place, and the need for instant gratification is.


> **jleaker01z said:**
> Its not confusing to YOU...to a new user who has never seen a command prompt it is a completely foreign language.

Thus the challenges of learning something new.  It does have to be learned after all.  It's been said many times on this forum, even those comfortable in Windows had to learn.  It's a mind set, and it's different than the current way of doing things in Windows.

> **p_quarles said:**
> 
This is a friendly community, and most of us respond well to follow-up questions. But it is a community and not a help desk. If I have a solution that will work, I'm happy to share it. I'm not going to fall all over myself to ensure that no one encounters something unfamiliar.

+1

If the help provided isn't helpful, then the original poster can always ask for clarification.  But to ask that every volunteer here think in GUI terms I believe is unrealistic.

I'm not in any way elitist, so don't go there.  But to ask for help then gripe because it wasn't the help you wanted seems ungrateful to me.  If it was easy, everyone would do it.  If it's worth the work to you, then you'll probably get something from it.


> **amadeus266 said:**
> ...so dropping to the CLI even in Windows is sometimes an absolute necessity....It probably also helps that I have developed a habit of taking extensive notes when I discover a problem and include all the information I can find about how to solve said problem. When I assist people using Windows the first thing I do is hand them a notepad and tell them to write down what the problem was and how I helped them fix ...

+1

> **kelvin spratt said:**
> Patience is what you need with a new user, 

And that sums it up.

---

### Post by Brunellus on 2009-04-06
I give command-line directions because they're faster.  If the GUI were so obvious, well, the newb would have figured it out on his own.  But if he's asking for help, I want to get him up and running as quickly as possible, while simultaneously minimizing the chance that he damages his system further.

There's zero chance he gets a copy-and-paste wrong.  There's every chance that he executes the wrong sequence of steps in the GUI.

When ambiguity means death, nothing gets the job done like words.

---

### Post by Newuser1111 on 2009-04-06
> **Perpetual said:**
> For me personally, I reference CLI because it's good to learn.  I have never had a Linux install that was 100% CLI free.So far on 9.04 beta on my laptop I haven't had to open the terminal.

---

### Post by Gryphon-ni on 2009-04-06
As an ubuntu newb I prefer command lines, as so many people have pointed out it aids in learning, its quick, and quite importantly if things screw up normally its pretty easy to get your machine booted into some kind of terminal, where you only have the command line.

but and its a big but...

There are people out there who have zero interest in knowing these things, they just want "Technology to work" for them. Not all users coming here are young computer enthusiasts.

I would love to move my Mum over to ubuntu, it would breath life into her old dell too. Does she have any interest in doing command lines, completely not. Would they scare the life out of her rather than being told go to "Add/Remove", I think it would.

Do we want to retain and encourage these users too?

Basically I think the answer is simple. If someone has gone to the effort to answer the problem I am eternally grateful and am not going to dictate to them how they describe it to me. If people have time the answer is to do both, GUI answer through to completion and CL answer.

On a side note:

A lot of people really like the fact that ubuntu is a bit more geeky, and that's part of the attraction. If it became mainstream even a little bit, I bet they would be out there trying to find the next project to be apart of. That's fine too as those new projects need the help and in the early days need the more technical community. It will be interesting to see how this community evolves. Currently the ubuntu community is doing a fantastic job.

---

### Post by 3rdalbum on 2009-04-06
I prefer to give as many GUI-based directions as possible, but I don't hold the user's hand through it (I don't say "Go to the Packages menu and then come down to Find, type the word 'backports' into the box and change the popup to read 'name', then click Okay, then right-click on the package and choose 'Apply for installation'). I'd just say "Open Synaptic Package Manager, do a find for 'backports' and install the package that appears".

Most people can find their way through a reasonable GUI. Also, GUIs prevent the user from being able to completely ******** everything up; how many times have you seen "I get an error message telling me that there's an error on line 30 of /etc/apt/sources.list" and finding that the user has been trying to type commands into the sources.list? There's a perfectly good GUI that doesn't let that sort of thing happen!

---

