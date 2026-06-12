---
title: "Coming from windows... many, many basic questions"
date: 2014-01-28
forum: Ubuntu, Linux and OS Chat
---

### Post by daner2 on 2014-01-28
Hi everyone,

I am new to Ubuntu and Linux in general. I am coming from windows and trying to get Ubuntu working in a VM. It's running fine but I am not really as productive as I'd like and many things are foreign. So go easy on me :). I don't know the lingo or the ins and outs. **Feel free to only answer what you know or only a few. **

So, a gigantic bunch of questions to get started:
[LIST=1]
[*]In the "home folder" (I guess explorer equivalent?), How can I see the path to the current folder? 
[*]Where are the home folder/desktop/documents/downloads located? 
[*]Is there a way to quickly type in a folder path? 
[*]Can I make a quick link or way to get to the usr folder? Like a shortcut of some kind? 
[*]What does bin stand for? what sort of files are stored there? 
[*]What does etc stand for? what sort of files are stored there? 
[*]What does var stand for? (not variable, it seems?) 
[*]What does sudo mean? 
[*]How do I find terminal commands to install programs? So far I have been doing a search every time for the proper "apt-get" command. 
[*]How can I install a program automatically with all of its dependencies? How can I install a program automatically withits recommended packages? 
[*]How do I find out what will be installed by a program? The contents of a package. 
[*]If I run apt-get install twice, what happens? Is the previous install just overwritten, or do I get a warning, or what? 
[*]How can I see file extensions? Many files do not seem to have any extensions. 
[*]A BIG usability one: Is there a way to make the scrollbar permanent? Its WAY too hard to make appear with the mouse and click on in some situations. And I do want to use a mouse. I am *really* having trouble here, I can't even navigate open windows well because the scrollbar is so hard to use. 
[*]Can I increase mouse scroll speed? 
[*]How can I open each folder in its own window? 
[*]Is a symlink (symbolic link, I think), just like a windows shortcut? If not, how does it differ? 
[*]Where can I find a list of the most handy-dany, often used terminal commends? 
[*]Where can I find a list of *all* terminal commands? 
[*]Does apt-get have a gui somewhere? 
[*]When I read terminal commands, they always begin with a $. what does this mean (if anything) and do I have to type the $ as well? (it seems the terminal already has one) 
[*]When I ran sudo apt-get php5 it seemed to install not only php, but also Apache and some other things. In addition, I got php 5.3.10, not php5.0.0 or php 5.5.8 (the current version). I pretty much did not know what I was going to get. Any help here on knowing what you will get when you run apt-get? I expected only php, but got a random version and some extra things like Apache, too. 
[*]Is there a better terminal app to use? Maybe with better copy/pasting, use a different font, syntax highlighting, etc. 
[*]Years ago i remember reading about something like a "shell history" in Linux where you could see all commands run on the system. I want to know the commands run so I can duplicate vms easily. Can someone tell me how to access this shell history, if it exists? (I am not interested in things like vagrant right now, which I have heard a lot about; I want to know the basics first and do things on my own.) 
[*]How do I know if the terminal is actually doing anything? I don't know if it is downloading sometimes. Sometimes I download something and it just seems to hang, but a few minutes later it is done. No hourglass or spinning thing to indicate loading/downloading. 
[*]Is there a way to build a list of commands for the terminal? To give it a bunch of commands, to execute in sequential order? 
[*]How can I get administrative privileges in the gui? I was so frustrated here I looked it up and eventually tried gksudo nautilus, but this is cumbersome as I only get 1 folder with privileges. Is there a way to make it global? 
[*]I know it is radically unsafe and not the Linux way, but I am just in a locked down dev environment and just want to experiment. Is there a way to just always have "sudo" or admin privileges on my account by default with no hassle? 
[*]How can you use file search on the dash board to search the contents of files, not just file names? 
[*]How can I cut down on the typing it takes to do repetitive tasks in the terminal? While installing lamp I must have restarted Apache over 100 times to test things(actually a conservative estimate) by typing "sudo service apache2 restart" 
[*]Can a shortcut be made that automatically runs a terminal command? Like restarting Apache? Or a simple script like a windows batch file that I can double click? 
[*]Which of the alternate flavors of Ubuntu is most like windows (ku,lu,gnome, etc). I'd rather work with something familiar. This environment is not that intuitive for me. 
[*]Is there a way to move the close/maximize/minimize icons at the top of windows to the right side of a window instead of the left? 
[*]How can I restore a program I have minimized? I can see a little tab on some icons indicating that there are multiple versions open, but I don't know how to actually go back to them. 
[*]I don't understand how Linux programs install. They seem to install everywhere - in usr/lib, /etc/ maybe more places. How does the typical program install and where should I look for its files? Is there a Program Files equivalent? 
[/LIST]



Thanks for any help here. I know these are a ton of basic questions, but I am just getting started. My first real dip into Linux.

---

### Post by malspa on 2014-01-28
Whew! That's a lot of questions! I don't mean to sound rude, but most of those questions can be answered by doing web searches, or by reading Ubuntu's documentation. 

The answer to #20 is "yes." I use Synaptic, but that's just one option.

---

### Post by Bucky Ball on 2014-01-28
[QUOTE=malspa]I don't mean to sound rude, but most of those questions can be answered by doing web searches, or by reading Ubuntu's documentation. [/QUOTE]

Please do some research. Many of the answers to your questions can be easily found online. What does sudo mean?

[https://duckduckgo.com/?q=what+does+sudo+mean](https://duckduckgo.com/?q=what+does+sudo+mean)

That search took about five seconds.

Please post back for answers to questions that you're finding elusive. 

Plenty of hits here, too:

[https://duckduckgo.com/?q=What+does+var+stand+for](https://duckduckgo.com/?q=What+does+var+stand+for)

PS: You are MUCH better off posting separate thread for each support issue rather than all in an exhaustive list like this. Might be an idea when you have answered many of these questions to post the remaining one separately. ;)

---

### Post by crazypj10 on 2014-01-28
I'm only a little bit further along coming from Win XP.
Home folder is on desktop, you can change the icons real easy (easier than Windows) just click on computer at top right of screen, system settings, My Unity and set what you want on desktop
 Path isn't difficult to find if you need it.
I'm sure there is an easier more elegant way to do it but I go through Dash Home then browse C drive
I swapped the close/minimise/expand buttons to operate more like Windoze right side but changed back to Ubuntu standard left side

---

### Post by monkeybrain20122 on 2014-01-28
Yeah a lot of questions. Here are a few answers (too lazy to answer all of them, like others say most are easily found on goole)

3. Either do ctr+l ("L", not i or 1) when you open the file manager, or install gnome-tweak tool, open it, go to "Files" and turn on "always use location entry instead of the pathbar" (here I assume you are using Ubuntu or Ubuntu-gnome)

4. yes, but it involves a bit of work (at least as far as I know)
[http://ubuntuforums.org/showthread.php?t=2200963&p=12906950#post12906950](http://ubuntuforums.org/showthread.php?t=2200963&p=12906950#post12906950)

Installing, searching, removing packages would be a lot easier by a powerful gui. I use synaptic for that. 
sudo apt-get install synaptic

---

### Post by deadflowr on 2014-01-28
24) history

that's all you need. 

Aside, I probably could answer most of these others, but why spoil the fun you can have finding and exploring it on your own.

---

### Post by andrew.46 on 2014-01-28
A lot of questions :). I have taken 1:

> 
35. I don't understand how Linux programs install. They seem to install everywhere - in usr/lib, /etc/ maybe more places. How does the typical program install and where should I look for its files? Is there a Program Files equivalent? 


There is a neat image n this page that explains the basics:

Linux Directory Structure (File System Structure) Explained with Examples
[http://www.thegeekstuff.com/2010/09/linux-file-system-structure/](http://www.thegeekstuff.com/2010/09/linux-file-system-structure/)

although there are subtle differences between the various Linux distros. I guess the near-equivalent of 'Program Files' would be /usr but this would be comparing apples and oranges...

And a big Welcome to Linux!

---

### Post by RadicaX on 2014-01-28
8. Super User DO. sudo. Pretty easy to remember once you know!

9.Go to the launchpad and find the package you want and it's name. Then you can apt-get it, or add-apt-repository if it is a ppa (with the ppa's name, which again you find on the launchpad).

10. Easy with Synaptic. 

11. Should tell you if you use Synaptic, but if you are apt-getting(?) Then you will have to look it up and ask around.

20. Synaptic. 

26. Sounds like BASH scripting to me. [http://linuxcommand.org/index.php](http://linuxcommand.org/index.php) This will help you get comfortable with the Shell of Linux and tell you most of the commands.

32. Alot of people say Kubuntu is a lot like Windows out of the box. But you can make Xubuntu with ease like Windows. (I think there is a tutorial on it to make it look and pretty much act dead on like Windows, even adding a theme.) XFCE makes doing that stuff easy.

---

### Post by nothingspecial on 2014-01-28
I'll take another

> **daner2 said:**
> 
[*]Is there a way to build a list of commands for the terminal? To give it a bunch of commands, to execute in sequential order? 


That's called a script. In it's simplest form you can do what you asked. One per line or seperated with a ";"and each will be executed in order when the previous one has completed. Of course you can do really fancy things with scripts but in the case of your question

```
thing --one; thing --two; cat --in-the-hat; next command --blah --blag --thing
```

be careful, in this example even if the previous bit fails the next one will still be executed so if you do something like

```
move to some folder that doesn't exist; delete everything
```

it will delete everything in the folder you started in.

[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

Only 30 odd to go

---

### Post by EnglishElectricAndy on 2014-01-28
A mighty list of questions indeed, to which, perhaps, the generic answer is " A Windows power user doesn't become a Linux power user overnight". Having said that I will offer some pointers from what I've found so far as a fellow Linux noob.

Referencing your #s

18/19) [http://www.linuxguide.it/linux_command_list-lA_en.html](http://www.linuxguide.it/linux_command_list-lA_en.html)
A by no means exhaustive glossary of commands I found during browsing and bookmarked as 'That looks useful'.

21) $ is similar to, but not exactly the same as, the C> prompt in Windows command line.

23) Different Terminal apps are available in the Software Center. 

25) Don't understand this one. Any terminal activity on my part usually generates heaps of output. At the very least I get 'Command not found'.

28) Effectively you seem to want to run as root permanently. This is **strongly recommended against** as it nullifies a key part of the Ubuntu security protocols, I doubt if many forum members would encourage this approach.

35) [http://dev-random.net/linux-directory-structure-explained/](http://dev-random.net/linux-directory-structure-explained/)
Another from my 'That looks useful' collection.

---

### Post by slooksterpsv on 2014-01-28
> **daner2 said:**
> Hi everyone,

I am new to Ubuntu and Linux in general. I am coming from windows and trying to get Ubuntu working in a VM. It's running fine but I am not really as productive as I'd like and many things are foreign. So go easy on me :). I don't know the lingo or the ins and outs. **Feel free to only answer what you know or only a few. **

So, a gigantic bunch of questions to get started:
[LIST=1]
[*]In the "home folder" (I guess explorer equivalent?), How can I see the path to the current folder?  - Not sure, normally the only files you'll deal with is in your home so it's technically /home/*username* or you may find it simpler to type in ~
[*]Where are the home folder/desktop/documents/downloads located?  - They are located in /home/*username*
[*]Is there a way to quickly type in a folder path?  - There used to be I'm not too familiar with Unity, but it used to be as simple as clicking on the top and typing it in.
[*]Can I make a quick link or way to get to the usr folder? Like a shortcut of some kind? - Yes you can either right-click and choose make link or drag it to the Unity bar on the left to make a quick link
[*]What does bin stand for? what sort of files are stored there? - bin (binary) it contains some essential programs for the bare Linux kernel/OS such as echo
[*]What does etc stand for? what sort of files are stored there? - eccetera or Editiable Text Configuration ??? I can't remember the second one, but it contains files for configuration for the X windowing systems, startup scripts, sudoers files, etc. too many to go through
[*]What does var stand for? (not variable, it seems?) - variable it means variable sized files will go here usually log files files that don't have a predetermined amount of size.
[*]What does sudo mean? - it's acting like a super user not sure exact meaning
[*]How do I find terminal commands to install programs? So far I have been doing a search every time for the proper "apt-get" command. - if you have a .deb package file you do sudo dpkg -i ./*package_name.deb* - THIS IS CASE SENSITVE - otherwise you can just do: sudo apt-get install *package_name* or for easier access, use Ubuntu Software Center which will install DEB files as well.
[*]How can I install a program automatically with all of its dependencies? How can I install a program automatically withits recommended packages? - Software center is best suited for this, there is a command but you'd need to read the man page for apt-get
[*]How do I find out what will be installed by a program? The contents of a package. - when you do apt-get it'll tell you it's installing say gimp and all the files that gimp needs like libpng, libjpeg, etc.
[*]If I run apt-get install twice, what happens? Is the previous install just overwritten, or do I get a warning, or what? - it'll say program is already installed, nothing to do
[*]How can I see file extensions? Many files do not seem to have any extensions. - Not sure in ubuntu itself. I use elementary OS
[*]A BIG usability one: Is there a way to make the scrollbar permanent? Its WAY too hard to make appear with the mouse and click on in some situations. And I do want to use a mouse. I am *really* having trouble here, I can't even navigate open windows well because the scrollbar is so hard to use. - [http://www.webupd8.org/2011/04/how-to-disable-overlay-scrollbars-in.html](http://www.webupd8.org/2011/04/how-to-disable-overlay-scrollbars-in.html)
[*]Can I increase mouse scroll speed? - Check system settings, if that doesn't work, search, usually system settings works.
[*]How can I open each folder in its own window? - skipping
[*]Is a symlink (symbolic link, I think), just like a windows shortcut? If not, how does it differ? - yes and no, research it; there are key differences between shortcuts in windows and symbolic links.
[*]Where can I find a list of the most handy-dany, often used terminal commends? - search on the web, depends on what you do
[*]Where can I find a list of *all* terminal commands?  - seearch on the web, or look through your system to see what's installed
[*]Does apt-get have a gui somewhere? - Ubuntu Software Center
[*]When I read terminal commands, they always begin with a $. what does this mean (if anything) and do I have to type the $ as well? (it seems the terminal already has one) - no the bash prompt ends with a $ which is just saying waiting for user input, if it's a variable like myFile if that was set, you'd use $myFile to get the data from that set variable, read up on terminals, if you don't know what you're doing in the terminal, read about it first
[*]When I ran sudo apt-get php5 it seemed to install not only php, but also Apache and some other things. In addition, I got php 5.3.10, not php5.0.0 or php 5.5.8 (the current version). I pretty much did not know what I was going to get. Any help here on knowing what you will get when you run apt-get? I expected only php, but got a random version and some extra things like Apache, too. - apache is a dependency it needs apache, granted it's not 5.0.0 the repositories have varying versions of the software, usually the latest that came out when Ubuntu was released. Read rolling distrobutions for more information
[*]Is there a better terminal app to use? Maybe with better copy/pasting, use a different font, syntax highlighting, etc. - you can change the settings of your terminal, research it.
[*]Years ago i remember reading about something like a "shell history" in Linux where you could see all commands run on the system. I want to know the commands run so I can duplicate vms easily. Can someone tell me how to access this shell history, if it exists? (I am not interested in things like vagrant right now, which I have heard a lot about; I want to know the basics first and do things on my own.) - learn about the terminal first, I know a command exists, where I don't know, I usually just press up or down till I find what command I needed 
[*]How do I know if the terminal is actually doing anything? I don't know if it is downloading sometimes. Sometimes I download something and it just seems to hang, but a few minutes later it is done. No hourglass or spinning thing to indicate loading/downloading. - it's a command line interface, not pretty GUIs here, you really should research your terminal stuff first, find how to do the basics. If you're downloading things look into wget, other programs it depends on how the program will output and if you told it to tell you to output information. 
[*]Is there a way to build a list of commands for the terminal? To give it a bunch of commands, to execute in sequential order? - scripts, research your terminal
[*]How can I get administrative privileges in the gui? I was so frustrated here I looked it up and eventually tried gksudo nautilus, but this is cumbersome as I only get 1 folder with privileges. Is there a way to make it global? - don't run as root, there's no reason you need access to the other folders unless you need to change a configuration, there are gui tools available to help make modifications, but be careful. Linux veterans will tell you that you can easily screw up your system if you don't know what you're doing. In GUI you don't need it simple as that.
[*]I know it is radically unsafe and not the Linux way, but I am just in a locked down dev environment and just want to experiment. Is there a way to just always have "sudo" or admin privileges on my account by default with no hassle? - No you have to be the root user to have complete unlimited access
[*]How can you use file search on the dash board to search the contents of files, not just file names? - No clue
[*]How can I cut down on the typing it takes to do repetitive tasks in the terminal? While installing lamp I must have restarted Apache over 100 times to test things(actually a conservative estimate) by typing "sudo service apache2 restart" - press up then enter when you've found the command, research your terminal, aliases would be good for this
[*]Can a shortcut be made that automatically runs a terminal command? Like restarting Apache? Or a simple script like a windows batch file that I can double click?
[*]Which of the alternate flavors of Ubuntu is most like windows (ku,lu,gnome, etc). I'd rather work with something familiar. This environment is not that intuitive for me. - Check out Zorin if you want somethiing that looks ALMOST EXACTLY like Windows. otherwise, Kubuntu is about the closest. Linux is not here to mimic, but to be it's own.
[*]Is there a way to move the close/maximize/minimize icons at the top of windows to the right side of a window instead of the left? - search it
[*]How can I restore a program I have minimized? I can see a little tab on some icons indicating that there are multiple versions open, but I don't know how to actually go back to them. - click on it or right-click and find your window title
[*]I don't understand how Linux programs install. They seem to install everywhere - in usr/lib, /etc/ maybe more places. How does the typical program install and where should I look for its files? Is there a Program Files equivalent? - Linux uses shared libraries, think of them like dlls for Windows, but they're located in their own directories and what not where programs know where to find them to use them; if you want a "Program Files" like linux check out GoboLinux
[/LIST]



Thanks for any help here. I know these are a ton of basic questions, but I am just getting started. My first real dip into Linux.

I answered a lot of the questions, but a lot will need to come with research. We'll help you find your way, but a lot of questions were related to stuff that you would need to read about. There's a PDF I found let me see if I can find the link to it that will help a lot with terminal [http://linux-training.be/files/books/LinuxFun.pdf](http://linux-training.be/files/books/LinuxFun.pdf) -it's over 200 pages but a good read, they flow quick too.

---

### Post by Elfy on 2014-01-28
I've not got my glasses on so get lost in the list ... 

What I did do though was 

*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by Bucky Ball on 2014-01-28
You might want to start the learning curve by installing Zim from Software Centre and starting a notebook to archive your findings. ;)

Or, install by opening a terminal and:

sudo apt-get install zim

Same as but without the GUI. You'll then find it in 'Accessories'. Enjoy your explorations.

---

### Post by 3rdalbum on 2014-01-28
A lot of these questions are frequently asked and are answered on this forum literally a hundred times a year. A forum search may help you, or even Google should be able to point you to the answers.

Whatever you can't find out, PM me and I will be happy to answer for you.

---

### Post by chili555 on 2014-01-28
> I know it is radically unsafe and not the Linux way, but I am just in a locked down dev environment and just want to experiment. Is there a way to just always have "sudo" or admin privileges on my account by default with no hassle?By 'locked down dev environment,' may we assume you are not connected in any way to any network? The ethernet cable is detached?

This is my pet peeve. Windows is inherently insecure, in no small part, because nobody wants to switch from MissUser to Administrator to install software that makes your mouse cursor a pink kitty, so they run as Administrator all the time. Drive-by viruses, worms, et al then install easily and without notice. 

MissUser: "Oh look, somebody lost this cool USB stick! I wonder what's on it!!"

Then they finally give up and install Linux, hopefully Ubuntu. Next, they want to know how to run as administrator all the time so that drive-by viruses, worms, et al then install easily!  Ubuntu, by default, says, 'Request Denied.' If Stuxnet wants to install on your system, a pop-up will ask for your password. 

Now if you are editing files, compiling code, testing, etc. and don't want to precede _every_ command with sudo, you can temporarily start a sudo session:```
sudo -i
edit this
edit that
make
make install
```And then withdraw:```
exit
```

---

### Post by buzzingrobot on 2014-01-28
Scrollbars: Install Unity-Tweak-Tool. Run it. Select "Legacy" scrollbar option.

Running as root all the time: No advantage, serious risk, and much hassle:  Many GUI programs will not work properly run in a root environment.

---

### Post by Don_Stahl on 2014-01-28
A personal observation -- coming from two decades of running Windows, the biggest adaptation for me was finding my way around file organization and file managers. Ubuntu is very sensible about organizing system, program, and user folders, I think. But I spent so much time using the root folder -- C:\ -- in Windows that getting used to Linux was different.

I don't find Nautilus as intuitive as I would like. I ended up using Krusader quite a bit. Other recommendations for file managers are Dolphin, Thunar. and Marlin.

---

### Post by chili555 on 2014-01-28
> **Don_Stahl said:**
> A personal observation -- coming from two decades of running Windows, the biggest adaptation for me was finding my way around file organization and file managers. Ubuntu is very sensible about organizing system, program, and user folders, I think. But I spent so much time using the root folder -- C:\ -- in Windows that getting used to Linux was different.

I don't find Nautilus as intuitive as I would like. I ended up using Krusader quite a bit. Other recommendations for file managers are Dolphin, Thunar. and Marlin.I predict that, in a year from now, you will feel quite comfortable and possibly even find Windows organization scheme a little strange.

This is not an operating system difference, it's life. After driving a BMW for a few years, I find my neighbor's Ford incomprehensible. He has some metal thingy called, if I remember correctly, a 'kee.'

---

### Post by buzzingrobot on 2014-01-28
> **Don_Stahl said:**
> A personal observation -- coming from two decades of running Windows, the biggest adaptation for me was finding my way around file organization and file managers.

As you gain an understanding of the how, and why, of the Unix file system hierarchy, things make sense.  At that point, file managers become just convenient tools, not necessities.

Windows is so wedded to the notion of "C:\" being bound to a specific physical drive that it is no wonder people think that's the only way to build a filesystem, perhaps not realizing it is a legacy of ancient DOS days sustained by Microsoft's need to avoid breaking old software. The Unix approach of spreading a filesystem over one or more physical drives has to seem foreign to new arrivals.

---

### Post by Don_Stahl on 2014-01-28
I agree, chili555 -- absolutely. I'm already pretty comfortable. Part of my discomfort is self-created -- my preference was always to set up personal folders for downloads, images, and so forth instead of using Windows' default folders. Yadda, yadda, long story short: I'm learning to use Ubuntu's defaults more effectively.

And as far as the OP goes, that would my observation as well: many things in Ubuntu are different, but it's a matter of learning and not a matter of better or worse.

---

### Post by Bucky Ball on 2014-01-28
> **Don_Stahl said:**
> ... my preference was always to set up personal folders for downloads, images, and so forth instead of using Windows' default folders. Yadda, yadda, long story short: I'm learning to use Ubuntu's defaults more effectively.

Yes, took me awhile to get over that. And it is oh, so easy to have your install with a /home directory on partition A and use symlinks to access your files on data drive B (which may be on a different drive). 

```
ln -s /media/Drive_B/Documents /home/user/Documents
```

... will produce the shortcut 'Documents' in 'user's' /home directory in / on drive A. It's target will be the 'Documents' folder on partition B.

The syntax is: ```
ln -s 'path to target' 'path and name of symlink'

```
Just thought I'd throw that in ... ;)

---

### Post by lykwydchykyn on 2014-01-28
Speaking of symlinks...

#17:  A symlink is not the same as a desktop shortcuts.  Desktop shortcuts are actual files that contain a location and various metadata about how to access it; they're interpreted by the desktop shell.  The .desktop file used by most open-source desktops is the closest analogy.  Symbolic links are file-like objects that exist at the filesystem level; they point to another file or directory and effectively create the illusion that the object exists in both places.  Windows has something analogous but they're rarely used and most users never encounter it.

---

### Post by RadicaX on 2014-01-28
28. As others have noted, it is recommended against, but I believe the command is sudo su. That means to become a super user, always. (Well, till you exit that mode.) While it is recommended against, Puppy Linux last I tried it was set up like that. Problem with it is, once a piece of malware gets control like this, it is as powerful as the user. And sadly, the internet is not the only way to spread malware, it is very easy to by USB also.

---

### Post by chili555 on 2014-01-28
[QUOTE I believe the command is sudo su. That means to become a super user, always.][/QUOTE]I was just going by this: [http://askubuntu.com/questions/331062/what-is-the-functional-difference-between-sudo-su-and-sudo-i](http://askubuntu.com/questions/331062/what-is-the-functional-difference-between-sudo-su-and-sudo-i)

---

### Post by daner2 on 2014-01-28
I just want to say a BIG THANKS to everyone for their help. (and polite replies to this new guy! :))

I went on a google quest today (6+ hours and counting) and found out a lot of answers and clarifications but the info provided here was very helpful and GREATLY shaved off my (ongoing) search time.

Trying to setup an ubuntu environment I needed, without knowing the ins and outs, took me over 14 hours. Much of that time was spent walking around a lot of obstacles that didn't have to be there. I felt like I had walked into a room with a giant machine and had been asked to make something with it without first knowing how to operate it. :) I keep thinking "if only I could do *that*, or I wonder what *that *means  or how *that *compares to windows?" So I started to keep a log of my questions, so now you know the origin of the giant list.

The linux file system diagram link was especially helpful for diving into things. Synaptic was another great recommendation; I've been trying programs out all day. I'm still doing personal research, but I have a few more questions and want to reiterate some of the questions above that I couldn't find the answer to (or weren't answered) that are particularly troubling me:


[LIST=1]
[*]Something holding back my productivity greatly is the lack of file search utility. The dash board and file manager searches do not seem to search text files for content. Can someone please recommend a search utility that does this quickly, and perhaps how to quickly access it? (I'd like it to be my Windows key if possible because that is what I am used to.) I downloaded a package called Desktop Search but it did not do what I was expecting and did not seem as effective as the built in search. I basically want something that, if I search for something like a particular bit of text (like a setting in some .ini file) it will return the .ini file.
[*]I tried to find a way to increase my mouse scroll speed but it appears there is no easy way to do this. I want to verify that there does not exist a solution for this in 12.0.4 ([http://askubuntu.com/questions/27270/increasing-scroll-speed](http://askubuntu.com/questions/27270/increasing-scroll-speed))
[*]Can someone confirm that typing ```
export HISTSIZE="999999999 
``` into the terminal will effectively make my terminal history "infinite"?
[*]Does a linux path have a drive letter? (c:\). if not, what is the  root path, if any? It seems to be just "/". I go to File System and I can see a series of files  including my home folder. I am going to guess that each of these are accessed via  something like /etc, /home, /bin. Can someone confirm this is true or elaborate? Or are the paths in some way different?
[/LIST]

(I'll post these or other questions separately if answers are elusive. I just didn't want to spam the forum with 30+ topics.)

---

### Post by chili555 on 2014-01-28
> Does a linux path have a drive letter? (c:\). if not, what is the root path, if any? It seems to be just "/". I go to File System and I can see a series of files including my home folder. I am going to guess that each of these are accessed via something like /etc, /home, /bin. Can someone confirm this is true or elaborate? Or are the paths in some way different? That's essentially correct. Please see:```
cd /
ls
```I get:> bin    dev   initrd.img      lib64       mnt   root  srv       tmp  vmlinuz
boot   etc   initrd.img.old  lost+found  opt   run   sys       usr  vmlinuz.old
cdrom  home  lib             media       proc  sbin  tftpboot  varThe wierdos tftpboot and lost+found and a few others may safely be ignored. 98% of everything I do is at /home/chili. I poke around in /var sometimes to consult a log to see what awful mistake I made so I can un-make it! As has been pointed out above, configuration files are in /etc. I've mostly looked, in order to try to answer a question here, and modified few. That's just about it.

---

### Post by lykwydchykyn on 2014-01-28
It's different, it's a little weird, but at least it's a published standard:

[http://www.pathname.com/fhs/](http://www.pathname.com/fhs/)

enjoy!

---

### Post by RadicaX on 2014-01-29
One sounds much like a Database, and if you type something, you just want it to search through everything to find a match. Hmm... I can not think of one like that, but I do not do that often. I am guessing you do some kind of special work with computers managing databases though and if you needed to, could pull up all instances of the phrase "The rabbit is a cold hearted beast."

4. I have not seen no drive letters with any work I have done in the command line. I remember once being told Linux does not really need to do that with path names like Windows does. I am pretty sure it had to do with how the file system manages things.

A note on 1.

grep looks for patterns, and sort lets you sort things in a certain way, but it does not open and check files one by one. So you might be able to write a script that would allow for this, I am sure there probably is one.

---

### Post by Bucky Ball on 2014-01-29
You can open Gparted and have a good look at your partition setup.

---

### Post by lykwydchykyn on 2014-01-29
There are a number of file search utilities available in the ubuntu repos, many of which do indexing of contents.  Recoll, swish, tracker, doodle are just a few I found in the repositories.  I know KDE comes with this functionality built-in, and I'm pretty sure there's a GNOME file search as well.  Often content-indexing is turned off by default since it requires significant CPU and HDD space, so you may need to tweak some options to get that.

I can't tell you which one works best with Ubuntu since I don't use file indexers or the default Ubuntu interface.

---

### Post by chili555 on 2014-01-29
> **Bucky Ball said:**
> You can open Gparted and have a good look at your partition setup.Or, the kwik 'n durty way:```
df -hT
```

---

### Post by daner2 on 2014-01-29
Thanks for the replies everyone. I will take a look at gparted and the file indexers mentioned. I don't know why I couldn't find one; I did a search for "search" and came up with desktop search and some that didn't meet my criteria, but did not find recoll, swish, etc.

Thanks for the pdf, too, and the information on /. I added it to the other pdfs in a folder of books to look over.

---

