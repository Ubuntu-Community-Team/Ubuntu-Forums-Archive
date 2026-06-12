---
title: "Is using the command line a dying art?"
date: 2010-10-06
forum: The Cafe
---

### Post by Zanthir on 2010-10-06
I just want to discuss the reality that virtually everyone my age and younger (25) has never really had to use the command line. Sure, when I was a little boy, I used to have to type things like
```
run win
run doom
```
or whatever program I wanted to launch from DOS, but even before that I was free from the command line on my Atari ST, where I would put a disk in the drive, browse to the B folder/drive, and open my game from 3.5" floppy.

My point is, I feel scared every time I am forced to do something new from the command line. Today, I spent hours trying to solve a problem that in the end was only a problem because I was trying to use a GUI on my Ubuntu Server machine, and the GUI was displaying users as groups, but they were really users and groups. If I had just used the command line in the first place, instead of running XFCE or Gnome, I wouldn't have even had a problem.

So, I'm getting used to it, a little bit, but I still really like my desktop environment. But I think I could learn to like the command line.

I used to be an avid ROM (Rivers of Mud) player. I still miss that game. It closed because the admin said its time had come to an end. So why is Ubuntu Server releasing a command line only distribution? (And, unrelated, why is there no [ubuntu_server] prefix?)

It's a really hard spot to be in, because I am a programmer, and very computer savvy. But I don't know the Linux command line. I'd like to learn. I'm working very hard on it. But it's hard, when I am so used to doing things the Windows way. I only had one teacher that said, "experiment with other operating systems. Use Linux."

I really believe in Ubuntu. I believe in free-software. I believe that it is good for humanity. I want everyone to support it, and get behind it. But it is hard to convince people that it is a good idea when I can't even convince myself that it is a superior product.

Anyone mind if I pray? I don't consider myself religious at all. In fact, of any religion I would most likely consider myself a Druid (recently recognized as a religion in England I heard). But, "please, God, please, show me why Ubuntu is better. I want to believe it is better. Just give me a reason."

Ah. There it is. Why do I want to believe it is better? Because it is. Because it helps humanity. It is a gift to everyone in the entire world. 

If I program for Ubuntu, can I count that as a tax deduction? I would love that.

```
:wq
```

---

### Post by Locke_99GS on 2010-10-07
> **Zanthir said:**
> Today, I spent hours trying to solve a problem that in the end was only a problem because I was trying to use a GUI on my Ubuntu Server machine, and the GUI was displaying users as groups, but they were really users and groups.

[...]

So why is Ubuntu Server releasing a command line only distribution?


Because servers aren't generally intended to run with GUI's. A GUI is a horrible waste of resources; it is there for the convenience of the user. The typical user of a server would be people using their services, (http, mail, ftp, &c...) services that have nothing to do with a GUI.

Typically, a server is administered via a ssh tunnel, sometimes through a direct console.

"Joe-the-closet-server" is a machine I have running in my closet, serving files to the network, and running a few other services. This machine has no keyboard or monitor installed. I don't even think it has video capabilities. I administer it sometimes through a webmin service (which is nice) and usually over a ssh tunnel.


My desktops and laptops are running various Linuxes, mostly Ubuntu Desktop. I program and compile on these machines, as well as all my schoolwork. I believe you unknowingly installed the wrong edition of Ubuntu. (BTW, you can run servers off a Desktop install also)

---

### Post by PapaNerd on 2010-10-07
Sometime next year (and I can't remember the exact day), I will pass the 25-year mark of using some flavor or another of unix.  The notion that a server ONLY has a CLI and not a GUI is simply nonsense.  Even though I currently do 99% of my server admin through the CLI (via ssh on a back door LAN), there is always something that needs to be checked and verified using a GUI on the local box, or an application that needs a tweak that cannot be accomplished through the CLI.  

You can either build your server with the server distro and then add the GUI of your choice, or build it with a desktop distro and then add the server components you want.  I usually do the latter.  Don't let the CLI learning curve discourage you.  To do it right, it will take several years to become proficient.

---

### Post by Locke_99GS on 2010-10-07
> **PapaNerd said:**
> [...] The notion that a server ONLY has a CLI and not a GUI is simply nonsense. [...]

Notice my use of the word *typical(ly)* :) Most administration tasks can be done without the GUI. Actually, I can't think of any that cannot be done with CLI, but I'm not the master admin.

---

### Post by PapaNerd on 2010-10-07
> **Locke_99GS said:**
> Notice my use of the word *typical(ly)* :) Most administration tasks can be done without the GUI.

Certainly no offense intended with the "nonsense" comment.  I think I confirmed the "typical" admin method with my "99%" observation.

> **Locke_99GS said:**
> Actually, I can't think of any that cannot be done with CLI, but I'm not the master admin.

The GUI on older Sun and MIPS servers has bailed me out more than once in troubleshooting deep system problems.  More recently, I've also seen a few cases where Synaptic Package Manager circumvents apt-get problems (and, of course, the other way around).  Using a GUI to prototype web pages in a non-production sandbox directory, especially when tinkering with the apache2 config comes in handy. 

All that said, the GUI should not be a crutch for avoiding the CLI, but merely available as another tool a server admin has at their disposal.

---

### Post by CharlesA on 2010-10-07
Moved to Cafe since this isn't really a support question.

+1 to the GUI not being a crutch, but a tool.

I originally had my server running a full GUI that I'd access over VNC. Then I moved to using Webmin and now I just admin it over SSH.

You can install a GUI on a server, but I wouldn't recommend Gnome or KDE.

See [here]("https://help.ubuntu.com/community/ServerGUI") as to why.

---

### Post by Spice Weasel on 2010-10-07
I tried teaching my Mum (who is completely computer illiterate by the way, can't even save using OpenOffice or Word... I have to do it for her) to use the command line and she's actually much better at using it than a GUI. Apparently she used a ZX-81 when she was younger and finds the command line easier... I let her use GNU Nano for a bit and she got on very well with it.

---

### Post by nikefalcon on 2010-10-07
[QUOTE=[Zanthir]("http://ubuntuforums.org/member.php?u=1151189")]
....the reality that virtually everyone my age and younger (25) has never really had to use the command line.
[/QUOTE]
There are kids out there using *nix. I switched to Ubuntu about 1 year ago(had enough trouble with windows.....) in utter desperation. And I never knew anything about how any OS worked; one year down the line and I think I can consider myself as an intermediate 
CLI user.(I'm just 16 and barely know the nuts and bolts of programming) CLI is a really efficient way of doing things- once you get used to it that is. Just don't get overwhelmed by the number of possibilities....they are endless. And as you learn about Ubuntu(and GNU/Linux) you'll realize why its more secure, better and efficient! 
Good luck with the learning.

---

### Post by Dustin2128 on 2010-10-07
I think that fewer and fewer people per year are learning the arcane arts of the CLI, but its not going away any time soon luckily. Its mostly because the terminal is inherently more powerful than most GUIs; the software maintainer will remove some settings for user friendliness, but user friendliness is pretty much level with the command line. Its also because its easier to use in some settings; wget [ftp://file.tgz](ftp://file.tgz) versus browsing to it in firefox.

---

### Post by msandoy on 2010-10-07
There are quite a few good tutorials and e-books around. I'm administering my own little headless server, via a really slow connection. Sometimes it's down to medium modem speed. Then you can forget GUI. But CLI works like a charm. Via SSH you can do everything you can do with a GUI, and more. Takes some time to learn, but it is definately worth it.

---

### Post by 98cwitr on 2010-10-07
nope...use it all the time

---

### Post by beew on 2010-10-07
Yes, and good riddance.  

There are many things you can only do with the cli especially when you want to do tweaking, trouble shooting and configuring, so it is good to know those things. If you want to be a Linux pro then at some point you need to learn it.

But at the same time many more routine and standard tasks can definitely be done with the GUI and it is a lot easier, more intuitive and makes a lot more sense too (except for one line commands like sudo apt-get install, which are easy enough) 

There are some who insist that the CLI is more efficient for the same task that can be done by the GUI, there are a few caveats that are not spelled out 1) you have to be able to remember the arcane commands, which most people can't unless you are a geek 2) you have to type fast and accurate (no typos) and this has nothing to do with conceptual understanding of computers or Linux, the secretary in the office can kick my *** on this even though she doesn't know anything about Linux commands. The problem is these commands really are poorly designed in that they don't make any sense to the normal human minds and you have to more or less learn them by rote if you want to be proficient (at least in the beginning, once you have built your vocabulary you would have an easier time to permute and combine them in ways that you want)

The command lines should only be used for necessity, not as an "art". One of my pet peeves with people giving advice to beginners is that they tend to throw some nonsensical gibberish in the form of command lines at newbies seeking help without any explanation of what the commands do (just cut and paste into the terminal) while there is a perfectly good way to do the job in the GUI which is actually not only "easier" to the beginner, but also conceptually makes a lot more sense than to cut and paste some magical incarnation into the terminal because you can kind of intuit the logic of what you are doing. I consider this abuse of the command lines and it is not even good for learning.

End of rant.

---

### Post by limestone on 2010-10-07
Ubuntu's working towards a more graphical desktop, so yes. If you're using ubuntu, then the terminal is a dying art.
But it's up to you how much you'll use it. Because you still can :)

---

### Post by conundrumx on 2010-10-07
I'm younger than you OP, and I use the CLI all the time.  SCP, quick file edits, restarting services, the list goes on and on...

If it's worth doing in a Linux or BSD system it can almost definitely be done from the command line.

---

### Post by Locke_99GS on 2010-10-07
@beew

I mostly agree with your rant, except for this:

> **beew said:**
> 
The command lines should only be used for necessity, not as an "art". One of my pet peeves with people giving advice to beginners is that they tend to throw some nonsensical gibberish in the form of command lines at newbies seeking help without any explanation of what the commands do (just cut and paste into the terminal) while there is a perfectly good way to do the job in the GUI which is actually not only "easier" to the beginner, but also conceptually makes a lot more sense than to cut and paste some magical incarnation into the terminal because you can kind of intuit the logic of what you are doing. I consider this abuse of the command lines and it is not even good for learning.

End of rant.

Linux isn't Windows, in the sense that there is no once single desktop environment, and there is a decent chance that even those running the same desktop environment may have them set up completely differently.

When somebody has issues connecting to a wireless network (for instance) we could provide detailed (click this, then this, then this) instructions for each of the various popular desktop environments and package sets, or just give them a couple of CLI statements. 

Yes, most basic and essential tasks can be handled from a GUI nowadays, and this is great. I use the GUI for most tasks on the desktop PC, and I can understand that a new Linux user would prefer detailed click-here-then-here instructions. Oftentimes, when the DE is known and the issue is simple, help might be provided in this fashion. For more complex issues, or where the DE is unknown, guigin a person through the GUI can be very time consuming and aggravating. Less help, as a whole, could be distributed.

---

### Post by donkyhotay on 2010-10-07
I use both, they both have their advantages and disadvantages. I use the GUI for tasks that are easier to use with a GUI (like finding a specific picture I can't remember the name of but know what it looks like) and the CLI for tasks that are easier to use with the CLI (like copying all files with "dog" somewhere within name to another folder).

---

### Post by dtfinch on 2010-10-07
I can't go a day without the CLI on Linux or Windows. Though I can see that for a large number of consumers, anything that not either browser based or a game seems to be falling out of common use.

---

### Post by gcndavidmn on 2010-10-07
I'm 17 and pretty new to linux. So I use the command line whenever I can just so I can learn. It's not dying in my house.

---

### Post by Rubi1200 on 2010-10-07
The funny thing is this:

When I used Windows I was neither inclined towards nor interested in using the command line.

In Linux, I find myself using it more and more to the point where I can now accomplish certain tasks exclusively from the terminal.

Long live the terminal!

---

### Post by CharlesA on 2010-10-07
> **Rubi1200 said:**
> The funny thing is this:

When I used Windows I was neither inclined towards nor interested in using the command line.

In Linux, I find myself using it more and more to the point where I can now accomplish certain tasks exclusively from the terminal.

Long live the terminal!

I've noticed that as well. Power shell is decent but no where near as mature as BASH.

---

### Post by Naiki Muliaina on 2010-10-07
I always used to used command line, nowdays I avoid it completely. I do a long hard day of work, I am up at 5:30 am, I get home 6ish in the evening, the middle 12 ish hours are tiring and hard. When I get home I want to switch off, use the least brain power as possible. Ubuntu + GUI's are lub for that.

---

### Post by Old_Grey_Wolf on 2010-10-07
I use the cli to interface with servers at work. I mostly ssh to the server. I can also use the blade chassis OBA/ILO to get to the console. I was using Remote Desktop at home until my grandchildren started living with me. When I used Remote Desktop to update the computers while they were using them, they would close the window I had open, take control of the cursor, or reboot. I began to use ssh and cli to do the updates since they don't see, nor can the interfere with the update. I prefer ssh; because, it is safer for me than trying to walk over all the junk in their rooms. I'll describe their rooms as disaster areas. :)

---

### Post by bouncingwilf on 2010-10-07
I tend to use the GUI most of the time these days but every now and then something odd happens and I find myself reaching for the terminal - which is strange because, although once upon a very longtime ago I was a sys admin on a SCO unix box, I've forgotten virtually everything I knew! However, when the prompt appears, somehow unbidden, my poor little arthritic fingers seem to remember things the rest of me has forgotten and bingo! problem is usually solved. Long live CLI

bouncingwilf

---

### Post by Old_Grey_Wolf on 2010-10-07
> **bouncingwilf said:**
> ...I've forgotten virtually everything I knew! However, when the prompt appears, somehow unbidden, my poor little arthritic fingers seem to remember things the rest of me has forgotten and bingo! problem is usually solved. Long live CLI...

I have found that it doesn't take long to remember those commands. Even the ability to use the VI editor came back quickly. 

What I really like about the cli is the fact that it works the same way even if the GUI interface has changed the location of the objects. You don't have to be familiar with the changes to menus or graphic layout of the windows.

---

### Post by bouncingwilf on 2010-10-07
vi or vile as we used to call it may be just a step too far! I know it's very powerful, as was teco ( could edit disc sectors directly with that) but in my dotage, I'll try and forget vi and slip quietly off into the arms of gedit.


bouncingwilf :q!

---

### Post by Zanthir on 2010-10-07
Thanks for all of the support and suggestions. 
 
I am installed Ubuntu Server, which ran no GUI, and then installed XFCE, but when using gconf-editor I was seeing gnome-system-tools, and thought that meant I needed to use Gnome to have these settings apply. So I began looking for the XFCE equivalent to gnome-system-tools.
 
There is no equivalent. The gnome-system-tools settings DO apply to XFCE. The problem was that in Ubuntu Server, hidden users do not show up properly (such as www-data which you need to add to the subversion group when installing subversion) in either XFCE or Gnome. As far as I could tell the only way to manage these hidden users was through the command line. Which is what I did. Took about a minute to look up the command and type it in. 
 
In the mean time I had lost hours looking up how to do this through a GUI, bugging people about users being groups instead of users and other nonsense. It was really thanks to the good people on the Ubuntu Server IRC channel that I discovered these entities that were showing up as groups in the XFCE and Gnome GUIs were also users, and I could treat them as such from the command line.
 
Thanks again twb and demonspork.

---

### Post by Joeb454 on 2010-10-07
In response to some of the earlier comments in the thread - I don't think the CLI is dying at all. I admit, a GUI can be more than useful on a server, though I personally have a VPS which is CLI only, largely because of the RAM limitations, but also because I rarely have need for it.

Perhaps the main reason, for me, is that having no GUI means that I **have** to learn the CLI way of doing things, and I don't think it would harm any career opportunities if you can put 'familiar with linux CLI' or something like that on your CV :)

---

### Post by Primefalcon on 2010-10-07
I dont think it is, because you can line up a bunch of commands and scripting into one command and run that single command.

it's a lot more flexible as well

for example since I am running beta Ubuntu

I've basically setup the following script

```
#!/bin/bash
apt-get update; apt-get -y upgrade; apt-get autoclean; shutdown -P now

```
I then dump this script into /usr/local/bin and make an icon on the taskbar that says to run the following command in terminal sudo ScriptName

And then I just click that at the end of each day, enter my password (I could add it to sudoers so I don't need password but I like that as an are you sure prompt) and go to bed, and the computer will just do a full upgrade and shutdown without needing my input.

So no the command line is not a dying art, it's as powerful as ever, and sysadmins and power users know this and leverage it

---

### Post by rhcm123 on 2010-10-07
i use an acient IBM desky as my file server. 80 MB ram, 100mhz processor, 4 250gb HDDs in a raid 1 array (it works speedy quick). If i had a GUI on this thing, there would be such long delay in between streaming my HD movies that it would be unusable. So i had to teach myself the CLI. I had no problem learning it - the GUI is just a nice face over something being done in the CLI. it executes things much more quickly and doesn't sugar-coat the output.

i also enjoy doing things my own way. while the GUI package manager uses aptitude, i prefer apt-get. its also alot faster to admin over SSH than VLC. Also, while GUI's make things much simpler to setup (they already know all the options and such), any good install guide will give you a near holding-hand walkthrough as well.

---

### Post by sideaway on 2010-10-08
> **Zanthir said:**
> ...

```
:wq
```

Just had to comment, nice touch :P

---

### Post by beew on 2010-10-08
> **rhcm123 said:**
> i use an acient IBM desky as my file server. 80 MB ram, 100mhz processor, 4 250gb HDDs in a raid 1 array (it works speedy quick). If i had a GUI on this thing, there would be such long delay in between streaming my HD movies that it would be unusable. So i had to teach myself the CLI. 

I am sure using a thing like that is even more of a dying art,-- if not already dead,-- so the fact that you can only use the CLI on it only confirms the idea that the cli is dying for the average user (well unless you're a power user who frequently looks under the hood of course).:lolflag:

---

### Post by foxmulder881 on 2010-10-08
I don't think it's a dying art. The advanced and power-users of Linux are always going to prefer and dabble in the command line.

I consider myself a bit of a Linux veteran these days as I've been usng it since Novell Suse 8. And I am well aware that the command line is always going to be more powerful than any gui. I use it for everything.

---

### Post by rhcm123 on 2010-10-11
> **beew said:**
> I am sure using a thing like that is even more of a dying art,-- if not already dead,-- so the fact that you can only use the CLI on it only confirms the idea that the cli is dying for the average user (well unless you're a power user who frequently looks under the hood of course).:lolflag:

repourposing old computers? I think thats a great art that more should practice... maybe i wont be able to use really ram/graphics intensive features in it, but thats besides the point. it is a server, after all (and no home should be without).

---

### Post by toupeiro on 2010-10-11
Far from it.

There is, however, a generational gap of computer users now who never used a computer before where there was an underlying CLI beneath them which they had to run their GUI on top of.  To many, the CLI is foreign, but to say it's a dying art is far from the truth.

GUI's generally make simple tasks simpler, and hard tasks harder.  And so, there will always be a CLI in linux for even GUI enthusiasts to use in the face of a GUI's shortcomings.  That is, once they stop being afraid of it and stop thinking because they have to type, rather than mouse, that it's a *bad* thing...

---

### Post by Drenriza on 2010-10-11
> **PapaNerd said:**
> there is always something that needs to be checked and verified using a GUI on the local box, or an application that needs a tweak that cannot be accomplished through the CLI. 

 
If their is something you only can do with a GUI then. You're just not skille enough to do it through the CLI.
 
And thats the way it is, since their arent anything that cant be done through the CLI if you know how to (experience/skills)
 
It can in some rare situations be more convinient / faster to do it with a GUI, but thats another matter.

---

### Post by PapaNerd on 2010-10-11
> **Drenriza said:**
> If their is something you only can do with a GUI then. You're just not skille enough to do it through the CLI.
 
And thats the way it is, since their arent anything that cant be done through the CLI if you know how to (experience/skills)

I sure hope you are not serious with that comment.  Please re-read my experience level and comments about percentage of admin time using the CLI.  However, for anyone to categorically state that there is a 100% CLI equivalent for all GUI features remains nonsense.

---

### Post by CharlesA on 2010-10-11
> **PapaNerd said:**
> I sure hope you are not serious with that comment.  Please re-read my experience level and comments about percentage of admin time using the CLI.  However, for anyone to categorically state that there is a 100% CLI equivalent for all GUI features remains nonsense.

+1 to this. Sometimes the CLI options are such a pain in the butt that it's just easier to use a GUI.

I've not bothered to run VMs in VBox via commandline, since there is only so much stuff you can do by using aliases.

It's way easier to set up a GUI, forward X over SSH, or even use a web frontend.

---

### Post by rhcm123 on 2010-10-11
> **CharlesA said:**
> +1 to this. Sometimes the CLI options are such a pain in the butt that it's just easier to use a GUI.

I've not bothered to run VMs in VBox via commandline, since there is only so much stuff you can do by using aliases.

It's way easier to set up a GUI, forward X over SSH, or even use a web frontend.

i disagree. it is very difficult to setup a GUI. i use webmin for basic management tasks on my server, and i find it slow and it was very difficult to get running properly. while when it's running fine it's easy, i find that using a gui is also very time-consuming. 

for instance, in webmin, to restart proftp (example server process), i have load a browser, log in, load the proftpd module, press the apply changes button. to do that via a CLI, i click the terminal launcher on the dock above, type ssh root@192.168.1.193 /etc/init.d/proftpd restart, type my password, and im done. I think the CLI is much more direct than a GUI.

just an opinion though.

---

### Post by t0p on 2010-10-11
I am a big fan of bash and the cli in general.  I nearly always have at least one terminal window open.  I love learning new commands.  The intricacy of using pipes and flags makes me sizzle with delight! [Ooh-err, steady on there!]

But I think using the command line probably *is* a dying art.  As more and more users migrate from Windows to Linux, they bring their love for/dependence on the GUI.  And it is possible to do just about anything via the GUI.

There will always be *some* users who like using the command line.  But they are an ever-decreasing percentage of all users.  So, while command line use will never die, it will certainly *look* like it's dying.  Let's just hope no one ever decides to put it out of its misery and puts a bullet through its brain.  :p

---

### Post by NCLI on 2010-10-11
If you have a server, the terminal is essential. 

You don't need it on the desktop anymore, but being able to use it does make your life easier.

---

