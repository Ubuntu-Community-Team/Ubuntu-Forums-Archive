---
title: "Getting rid of command line requirements"
date: 2009-11-04
forum: The Cafe
---

### Post by alonzobots on 2009-11-04
Why can't Ubuntu get rid of the requirement to use Terminal to do tasks? This is a huge usability issue for new users. I use ubuntu for my primary desktop at home, and it never ceases to be annoying that to do basic tasks that competing OS's do in a GUI window? I believe users want a OS with a seamless interface, not one where I have to remember arcane commands with eclectic modifiers. Why do I always have to type sudo etc this or that, why can't their just be a "administrative tasks" panel where I can do these sorts of things, like editing system files, or moving files into protected directories? If I am wrong and there is a prebuilt functionality for doing this in a windowed environment, I have not found it.
In summation, I believe that moving away from requiring users to perform terminal commands is a big step towards making this OS mainstream.

---

### Post by cariboo on 2009-11-04
Everything that can be done with a terminal, can also be done using gui tools.

The reason you see people giving command line solutions, is because most of the time the poster doesn't specify what version they are using, gui solutions for Kubuntu are different from the same solution fo Ubuntu.

THis thread really doesn't belong here, it should be in recurring, but I'll move it to the Cafe for the time being.

---

### Post by NoaHall on 2009-11-04
The terminal is far easier to use, much faster, allows better control, and also gives feedback if something goes wrong. And as cariboo907 said, anything that can be done with the terminal, can also be done using the GUI.

---

### Post by RiceMonster on 2009-11-04
Not this argument again...

---

### Post by Skripka on 2009-11-04
> **alonzobots said:**
> Why can't Ubuntu get rid of the requirement to use Terminal to do tasks? This is a huge usability issue for new users. I use ubuntu for my primary desktop at home, and it never ceases to be annoying that to do basic tasks that competing OS's do in a GUI window? I believe users want a OS with a seamless interface, not one where I have to remember arcane commands with eclectic modifiers. Why do I always have to type sudo etc this or that, why can't their just be a "administrative tasks" panel where I can do these sorts of things, like editing system files, or moving files into protected directories? If I am wrong and there is a prebuilt functionality for doing this in a windowed environment, I have not found it.
In summation, I believe that moving away from requiring users to perform terminal commands is a big step towards making this OS mainstream.

Terminal commands are nearly universal across linuxes.  GUIs are NOT.  That is the simple reason.  You can be using ANY GUI, and someone else using a COMPLETELY different GUI can offer help, because the CLi is nearly constant.


Why should someone who is an E17 Ubuntu user not be able to help a KDE Ubuntu user, for example, simply because the GUI front ends are different?  Hmmmm?  You want to move away from CLi, you lose the ONE and ONLY Latin across linuxes, and you LOSE the amount of help you can get DRASTICALLY.

---

### Post by snowpine on 2009-11-04
Hi Alonzobots, 

I strongly disagree, for two reasons:

1) The command line is a *strength* of Linux, not a weakness. Being able to control your computer directly, with a few simple, unambiguous commands, is incredibly powerful. (Windows and Mac both have terminals, but most people choose not to use them for whatever reason.)

2) You *can* do almost anything in Ubuntu without ever using the terminal. However, there is one very simple reason why terminal commands are discussed and recommended so often on these forums: It is much easier to instruct another user on the forums using terminal commands instead of GUI tools. If I'm trying to help you with something, I'd rather give you a terminal command that you can copy and paste (no risk of typos that way!) than try to explain "go to the System menu, then Administration, then Printing, click here, click there, uncheck this box, click OK..." Furthermore, what if you are using Ubuntu and I'm using Kubuntu? You would not be able to help me GUI-style (because the menus and apps are different) but the terminal commands would probably be the same.

As an example, you could very easily edit your sources.list file graphically by pressing Alt+F2, typing 'gksu nautilus' (you could even add 'gksu nautilus' to your menu or create a desktop launcher, if it's a command you think you'll use often), navigating to your /etc/apt folder, and double-clicking on the sources.list icon to open it with the text editor as root. But isn't it quicker (and easier to help another user on the forums) to simply type the command 'sudo nano /etc/apt/sources.list'?

That's my main point :) but I also want to strongly disagree with your argument that "editing system files, or moving files into protected directories" should be an easily-achieved, everyday task for inexperienced users. "sudo" requires *typing only four letters!* and is the #1 reason why Linux is considered a more secure OS than Windows. Don't think of 'sudo' as an inconvenience; think of it as a valuable reminder that you are leaving the realm of everyday user tasks and escalating to root powers with the ability to hose your entire system. :)

(edit) I type too slow and use too many words; excellent answers above! ;)

---

### Post by bowens44 on 2009-11-04
> **alonzobots said:**
> W
In summation, I believe that moving away from requiring users to perform terminal commands is a big step towards making this OS mainstream.

If making the OS mainstream means moving away from the CLI then I hope we remain obscure. The CLI is what makes Linux so powerful, besides there is a GUI for nearly everything in Ubuntu.

If you want mainstream.... stick with windows

---

### Post by alphaniner on 2009-11-04
> Everything that can be done with a terminal, can also be done using gui tools.

Maybe if you consider xterm a GUI tool...

---

### Post by betrunkenaffe on 2009-11-04
Umm, learn to use the OS?

I go in terminal for things once in a while, sometimes because a website gave instructions which I could copy paste (I love copy paste) or because I was too lazy to learn the GUI for it.

99% of things I do are GUI based.

---

### Post by Skripka on 2009-11-04
> **snowpine said:**
> 

(edit) I type too slow and use too many words; excellent answers above! ;)

I thought of using the Search tool, and looking for Anti-CLi threads, and poasting linkies to them here...but I figured the UbuntuForums admins wouldn't appreciate my search query crashing their servers...

---

### Post by sisco311 on 2009-11-04
> **alonzobots said:**
> why can't their just be a "administrative tasks" panel where I can do these sorts of things, like editing system files, or moving files into protected directories? If I am wrong and there is a prebuilt functionality for doing this in a windowed environment, I have not found it.

If you are using nautilus as your file manager you can try  [nautilus-gksu]("apt://nautilus-gksu")(<-click to install, [apturl]("https://help.ubuntu.com/community/AptURL") link). The gksu extension for nautilus allows you to open files with administration privileges using the context menu when browsing your files with nautilus.

---

### Post by NoaHall on 2009-11-04
> **alphaniner said:**
> Maybe if you consider xterm a GUI tool...

Lol? Really, you can do everything with a GUI.

---

### Post by Paqman on 2009-11-04
> **alonzobots said:**
> If I am wrong and there is a prebuilt functionality for doing this in a windowed environment, I have not found it.

You might want to install the plugin nautilus-gksu. It'll give you a right click > "open as administrator" option for any files you want to edit.

Some other good GUI tools are startupmanager, ntfs-config and pysdm. I think all of the above should be in the default install, personally.

---

### Post by Skripka on 2009-11-04
> **NoaHall said:**
> Lol? Really, you can do everything with a GUI.

How do you start X?

---

### Post by NoaHall on 2009-11-04
> **Skripka said:**
> How do you start X?

Hehe, if you have a GUI running, then so is X :)

---

### Post by Skripka on 2009-11-04
> **NoaHall said:**
> Hehe, if you have a GUI running, then so is X :)

But if X isn't running, you cannot start X from  a GUI.  Hence being able to do "everything" with a GUI is not accurate.

---

### Post by NoaHall on 2009-11-04
> **Skripka said:**
> But if X isn't running, you cannot start X from  a GUI.  Hence being able to do "everything" with a GUI is not accurate.

.... Sigh?
It's a bit of a invalid point(while also being true).

---

### Post by Tibuda on 2009-11-04
> **Skripka said:**
> But if X isn't running, you cannot start X from  a GUI.  Hence being able to do "everything" with a GUI is not accurate.

That's why X is started on boot in Ubuntu.

---

### Post by Tibuda on 2009-11-04
> **alonzobots said:**
> Why can't Ubuntu get rid of the requirement to use Terminal to do tasks? This is a huge usability issue for new users. I use ubuntu for my primary desktop at home, and it never ceases to be annoying that to do basic tasks that competing OS's do in a GUI window? I believe users want a OS with a seamless interface, not one where I have to remember arcane commands with eclectic modifiers. Why do I always have to type sudo etc this or that, why can't their just be a "administrative tasks" panel where I can do these sorts of things, like editing system files, or moving files into protected directories? If I am wrong and there is a prebuilt functionality for doing this in a windowed environment, I have not found it.
In summation, I believe that moving away from requiring users to perform terminal commands is a big step towards making this OS mainstream.

Why do you want to edit system files or move files into protected dirs?

---

### Post by SomeGuyDude on 2009-11-04
Y'know, in some ways the terminal really is a LOT easier. There's no reason to abandon it just because the transition period is tricky.

---

### Post by Skripka on 2009-11-04
> **danielrmt said:**
> That's why X is started on boot in Ubuntu.

And sometimes things break.

---

### Post by bonfire89 on 2009-11-04
> **alonzobots said:**
> Why do I always have to type sudo etc this or that, why can't their just be a "administrative tasks" panel


Try typing

```
sudo su
```

*in a sense* this puts you into an administrative mode and you wont have to type sudo in front of everything for the time being.

---

### Post by lukjad on 2009-11-04
> **alonzobots said:**
> Why can't Ubuntu get rid of the requirement to use Terminal to do tasks? This is a huge usability issue for new users. I use ubuntu for my primary desktop at home, and it never ceases to be annoying that to do basic tasks that competing OS's do in a GUI window? I believe users want a OS with a seamless interface, not one where I have to remember arcane commands with eclectic modifiers. Why do I always have to type sudo etc this or that, why can't their just be a "administrative tasks" panel where I can do these sorts of things, like editing system files, or moving files into protected directories? If I am wrong and there is a prebuilt functionality for doing this in a windowed environment, I have not found it.
In summation, I believe that moving away from requiring users to perform terminal commands is a big step towards making this OS mainstream.
With great power comes great complexity.

---

### Post by dragos240 on 2009-11-04
In all honesty, I think using the terminal is much faster than using gui tools. There are gui tools that I prefer over command line utilities too. Like firefox vs links, or nm-applet (plus networkmanager daemon) vs iwconfig & dhcpcd (and possibily wpa_supplicant). But most of the time, it's to the command line for me.

---

### Post by diesch on 2009-11-04
> **Skripka said:**
> How do you start X?

I'm sure there's a framebuffer based program starter somewhere.

---

### Post by SomeGuyDude on 2009-11-04
Is typing sudo really that hard for some people? It's... it's four characters. If typing "sudo apt-get" instead of "apt-get" is such a monumental task for you, maybe you should stick with television where your fingers won't get such a workout.

---

### Post by Pasdar on 2009-11-04
On other forums or to people I know I give ONLY gui answer, on this forum I mostly give command line...

---

### Post by SomeGuyDude on 2009-11-04
> **dragos240 said:**
> In all honesty, I think using the terminal is much faster than using gui tools. There are gui tools that I prefer over command line utilities too. Like firefox vs links, or nm-applet (plus networkmanager daemon) vs iwconfig & dhcpcd (and possibily wpa_supplicant). But most of the time, it's to the command line for me.

Same. I use Wicd, Firefox, thunar, and a bunch of GUI stuff, but for installation/update and similar tasks it's command line all the way.

---

### Post by Skripka on 2009-11-04
> **SomeGuyDude said:**
> Is typing sudo really that hard for some people? It's... it's four characters. If typing "sudo apt-get" instead of "apt-get" is such a monumental task for you, maybe you should stick with television where your fingers won't get such a workout.

Typing is too much work...they want things to be like Windows where you can click your way through life, and not be able to fix things...but at least you don't have to see a CLi prompt, gawd forbid.

---

### Post by Pasdar on 2009-11-04
by the way, you might want to learn the "TAB" button on your keyboard... try it... type in console:

su [TAB]

it will finish the command for you.. you can also do this with any folder/file name you type...

---

### Post by Skripka on 2009-11-04
> **Skripka said:**
> Typing is too much work...they want things to be like Windows where you can click your way through life, and not be able to fix things...but at least you don't have to see a CLi prompt, gawd forbid.

I still am laughing about how I had to use a DOS prompt CLi to make the Win7 ISO from archive files I downloaded-because the .EXE they provided to do it was and is still broken.

---

### Post by SunnyRabbiera on 2009-11-04
Commandline in linux is actually much less needed then it used to be, heck I have not even touched a terminal in months.
Just some people like giving out terminal instructions

---

### Post by ZankerH on 2009-11-04
I think ubuntu should include a short tutorial on bash that launches the first time you boot into it (possibly with a way out such as "send a keyboard interrupt to skip this tutorial). Nothing much, but it should guide the users through some simple steps such as file management, basic flow control statements, writing a script and making it executable, using aptitude and a basic text editor like nano. That would cut down a lot on the number of the people complaining about the "terminal" because they don't know bash. Once you know the basic syntax, it's a lot easier to place the commands people are telling you to run in the context of what you already know, or use that added knowledge to help you automate repetitive tasks.

And no, more redundant GUI frontends isn't a solution. People are complaining because they want a more unified interface for GNU/Linux, well, the bash shell is as unified as you get. Most of the time, I don't even bother checking out or learning whatever new "GUI breakthrough" has been made by the flavour of the month DE, because it's 1. incompatible with the rest of them, 2. resource-heavy and 3. likely to be obsolete in a few months. If you want to learn an interface and gain knowledge that will likely be useful for decades to come, learn Bash scripting. If you want to re-learn using your computer every time there's a major update to the DE/WM you use, feel free to do so, but don't complain about non-standard interfaces, because there is a standard interface, and it's called bash.

---

### Post by SomeGuyDude on 2009-11-04
> **Skripka said:**
> Typing is too much work...they want things to be like Windows where you can click your way through life, and not be able to fix things...but at least you don't have to see a CLi prompt, gawd forbid.

There's this unbelievable assumption that computers should be usable without reading ANYTHING. People are willing to read user manuals for friggin' WATCHES, but a computer must be so idiot-proof that grandma can have it up and running as soon as she sits down. It's unbelievable.

It's like demanding that cars be so easy to use you don't need to take a test.

---

### Post by marchwarden on 2009-11-04
> **SomeGuyDude said:**
> There's this unbelievable assumption that computers should be usable without reading ANYTHING.

I think we have Microsoft to blame for that, in particular the slogan "I'm a PC and I am 8 years old".  With marketing like this Microsoft is insisting that using a PC is effortless, implying (or so I believe) that you need very little education, if any at all, to use one.

---

### Post by aysiu on 2009-11-04
> **alonzobots said:**
> Why can't Ubuntu get rid of the requirement to use Terminal to do tasks? This is a huge usability issue for new users. I use ubuntu for my primary desktop at home, and it never ceases to be annoying that to do basic tasks that competing OS's do in a GUI window? Can you give an example? I can't think of a single everyday task that **requires** me to use the terminal. There are plenty of tasks I accomplish using the terminal because I **prefer** the terminal for those tasks, but none of those tasks **requires** the terminal.

How about some examples? > Why do I always have to type sudo etc this or that, You don't have to. Again, give an example. > why can't their just be a "administrative tasks" panel where I can do these sorts of things, like editing system files, or moving files into protected directories? If I am wrong and there is a prebuilt functionality for doing this in a windowed environment, I have not found it. Why don't you ask for help, then, instead of just assuming it doesn't exist? Here's a guide to creating a browse-as-root launcher:
[http://www.psychocats.net/ubuntucat/rootlauncher/](http://www.psychocats.net/ubuntucat/rootlauncher/)

So it can be done.

Really, though, you're editing system files every day? That's an everyday task? It shouldn't be. Maybe you edit a few system files in the beginning when you're setting up your installation, but you shouldn't have to edit or move system files to browse the web, edit photos, organize music, check your email, or create documents.

> In summation, I believe that moving away from requiring users to perform terminal commands is a big step towards making this OS mainstream. I disagree, since it's already been done.

---

### Post by Eddie Wilson on 2009-11-04
> **alonzobots said:**
> Why can't Ubuntu get rid of the requirement to use Terminal to do tasks? This is a huge usability issue for new users. I use ubuntu for my primary desktop at home, and it never ceases to be annoying that to do basic tasks that competing OS's do in a GUI window? I believe users want a OS with a seamless interface, not one where I have to remember arcane commands with eclectic modifiers. Why do I always have to type sudo etc this or that, why can't their just be a "administrative tasks" panel where I can do these sorts of things, like editing system files, or moving files into protected directories? If I am wrong and there is a prebuilt functionality for doing this in a windowed environment, I have not found it.
In summation, I believe that moving away from requiring users to perform terminal commands is a big step towards making this OS mainstream.

Using the terminal is not a requirement but is better overall. The mainstream operating systems you speak of still use a terminal for mostly repair work. If you have not found a way to do everything via Gui then you have not looked enough. There is a way to do everything you speak of via gui.

---

### Post by Viva on 2009-11-04
There are certain things that are not supposed to be done using a GUI. For everything else, there is a GUI alternative.

---

### Post by cariboo on 2009-11-04
> **Viva said:**
> There are certain things that are not supposed to be done using a GUI. For everything else, there is a GUI alternative.

Please tell us some of things a normal user (if there is such a thing) can't do without resorting to using a terminal.

---

### Post by betrunkenaffe on 2009-11-05
> **ZankerH said:**
> I think ubuntu should include a short tutorial on bash that launches the first time you boot into it (possibly with a way out such as "send a keyboard interrupt to skip this tutorial).

This is an awesome idea, get cracking on it!

If when people launch terminal or konsole for first time it helped guide them through basic usage of it (even if links were just left in bookmarks to sites with tutorials on it), I think we'd see more people that while maybe not power users, wouldn't be scared of it.

---

### Post by Irihapeti on 2009-11-05
There's already quite a good beginner's guide for the terminal in the Help documents (you know, that blue question-mark or life-buoy thing at the top of the screen :) ) under Advanced topics. I used it to get started with the terminal and found it very helpful.

Maybe that could somehow be made more accessible or obvious to first-time users.

---

