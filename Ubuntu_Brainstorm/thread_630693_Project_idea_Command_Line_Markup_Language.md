---
title: "Project idea: Command Line Markup Language"
date: 2007-12-03
forum: Ubuntu Brainstorm
---

### Post by danbh on 2007-12-03
I posted a youtube video: [http://www.youtube.com/watch?v=dxAwjwFIWIQ](http://www.youtube.com/watch?v=dxAwjwFIWIQ)

[https://launchpad.net/climl](https://launchpad.net/climl)

I would like to move discussion to launchpad, if possible

I started an IRC chat that I will hang out in from time to time:  #CLIML


Here are some commands that might help those new to linux to get it working:
wget -rnp "http://hollocher.hobby-site.org/CLIML/"
cd hollocher.hobby-site.org/CLIML
chmod +x CLIML.py
./CLIML.py tests/Using_The_Terminal.climl

and also
gedit tests/Using_The_Terminal.climl


### Package requirements ###
I've been doing some testing, it it looks like at a minimum, you need xorg and python-vte.  Most distros will give you xorg by default.  So just sudo apt-get install python-vte

---

### Post by RIchard James13 on 2007-12-03
I don't think your project goes far enough. I think it would be better to have a Wiki with lots of examples of how commands are used on it.

One of the problems I can see with your system is that it concentrates on singular commands. But most people use multiple commands. If your program could do multiple commands and string them together and show the user what was happening that would be a good tool. But I still think people learn by example. Give them lots of examples and they can understand better. 

I was actually considering writing a manual the other day about shell programming since I have an interest in this. I don't know which would be easier to understand a manual (no hypertext) or Wiki (hypertext).

Here is an example of some of the stuff I am talking about [http://slackwiki.org/Bash_Automate_Tasks]("http://slackwiki.org/Bash_Automate_Tasks")

---

### Post by smartboyathome on 2007-12-03
I think there is already an idea in the pool on this.

---

### Post by RIchard James13 on 2007-12-03
> **smartboyathome said:**
> I think there is already an idea in the pool on this.

A link would be nice :KS or some hint as to what to search for.

---

### Post by smartboyathome on 2007-12-04
I can't remember what topic it is, but try searching this forum for command line.

---

### Post by loa on 2007-12-04
I think the idea is good. I have a similar idea, in which the gui programs could teach the users about the commandline. The idea is this:

When I do some things in a gui program, that program would also at the same time tell me how do this in the cli, perhaps by having a little space in the bottom of the program window showing how to do the same thing on the command line.

Puttings my idea here into practice would then involve existing gui programs. If maybe 20-30 of the most important administration and configuration programs did this, it would be enough to teach users about the command line.

---

### Post by RIchard James13 on 2007-12-04
> **smartboyathome said:**
> I can't remember what topic it is, but try searching this forum for command line.

I already tried that search :( I think I will have to manually look through the entire section. Anyway thanks for the pointers ;)

---

### Post by RIchard James13 on 2007-12-04
> **loa said:**
> I think the idea is good. I have a similar idea, in which the gui programs could teach the users about the commandline. The idea is this:

When I do some things in a gui program, that program would also at the same time tell me how do this in the cli, perhaps by having a little space in the bottom of the program window showing how to do the same thing on the command line.

Puttings my idea here into practice would then involve existing gui programs. If maybe 20-30 of the most important administration and configuration programs did this, it would be enough to teach users about the command line.

At first I thought no that wouldn't work because the GUI just calls other scripts which do the work. But then I realized that yes that is exactly what should be done. Because it helps those who what to understand what the GUI is doing. Which is actually more important than understanding how the command line itself works.

From that point people can start upon another learning journey to see what each script in the system does and therefore understand how the system works. That other journey would take place through another system such as the one originally proposed in this thread.

---

### Post by bousozoku on 2007-12-05
I've considered something similar in the past, but in a generic fashion that could be used over any UNIX with a text-based interface.

I've used several large systems where you enter a command and press a key combination, <F4> for example, to prompt.  As you fill in the parameters, you can press <F16> (Shift-F4) to view the actual command.  Once completed, you can press the <enter> key to submit the command.

Wouldn't it be better to use Python or Ruby to make the system more flexible?

---

### Post by danbh on 2007-12-05
loa: You are thinking right along the lines that I am thinking.  I just want GUIs to teach you how to use the command line, rather than hide how the command line works.

RIchard James13:
I was trying to come up with an idea that would cover a few things. 

Here is how community behavior could change.  Right now, when people want to document how to do something on the CLI, they make a webpage, and then write an essay on what the command is, how the command works, some examples.

I'm thinking that you just come up with a data format that includes all that info, and also write a program takes that info in, and generates a useful GUI from that info.  

Thus, the GUI would serve the purpose of documenting whatever needed to be documented in the first place, and it would offer a GUI method of running the command, AND it would also be a tutorial app, teaching people how to run the command.  

The specifics of the idea are not as important as the main concept, which is to have GUIs teach you how to use the command line, instead of hiding that information.

---

### Post by danbh on 2007-12-05
"Wouldn't it be better to use Python or Ruby to make the system more flexible?"

Better to use than what? I'm not sure what you were responding to.  

 I was thinking of using Python, since python is supposedly the language of Ubuntu.  But, I dunno.  I've been thinking about hunkering down with a gtkpython tutorial, and seeing if I could come up with a demo.

Though, if there really is something like this already, hopefully someone posts a link before I start   :P

---

### Post by LaRoza on 2007-12-06
How would this be different from the man pages, besides in a window, and not in a terminal with NCurses?

---

### Post by RIchard James13 on 2007-12-06
I am also trying to create a mockup. A few mockups and we can start discussing the details. I am going to concentrate on the tar command since it is so hard.

The problem I have been having so far is that Tkinter pythons main GUI does not seem to support events from selecting an item in a drop down list box aka combo box. I can't find documentation yet for gtkpython, but I do note that on Ubuntu at least gtkpython seems to be installed. So we can use that for the interfaces.

How is this different from the man pages, well the program directly maps the options into the command string. Imagine if the man page was interactive and clicking on an option would alter say an example of how the command worked.

*Edit* Found the python gtk documentation from [http://wiki.python.org/moin/PyGtk]("http://wiki.python.org/moin/PyGtk")

---

### Post by evymetal on 2007-12-07
Interesting Idea. There was a google tech-talk recently on this kind of thing:
[http://www.youtube.com/watch?v=faJ8N0giqzw](http://www.youtube.com/watch?v=faJ8N0giqzw)

The talk is a bit wishy-washy for me, but the idea is to have a graphical equivalent to pipes. As you string applications together you "blend" their GUIs,

---

### Post by loa on 2007-12-07
I have a little expansion on my first post: Any app that changes configuration files should also simultaneosly show the the config file in text, and when you alter some option, the program would make the right changes to the  config file, and highligt the changes it just did (or maybe make a different color or something.

So just to the left of the gui part of the program (or beneath, or above, or in the middle or something), there would be a window with the text file. Preferably there should be easy access to context sensitive documentation that explains the option currently being edited, and it's syntax. It would also be nice if the program could out further documentation (this could be manpages, webpages, or perhaps custom documentation describing just those options the gui is not capable of editing) that helps to explain options the gui is not capable of doing.

I would love if an administrative program had this feature. It would enable me to learn the usage of the cli programs and config files much faster I think. And if I don't have the time to learn the it cli way, I can always just use only the gui.


There should also be an option to hide the window with the config file. Maybe this option could be turned off by default, to avoid cluttering the apps for newbies.

---

### Post by loa on 2007-12-07
An example (of my first post) would be the nautilus cd-recorder. When I double-click an ISO to burn a file, it could maybe provide an additional button that says: "Show me the commandline code for this command", and when clicking it a little text space would appear in the bottom of program window saying "instead of pressing 'Write to disc' you could execute this: cdrecord file.iso -- all the options (which I have forgotten)."

Preferably there would be some system-wide setting to enable this showing of the cli code for all programs supporting it.

I think you others are right that the cli is very powerful when you learn it, and it would be good if users were taught about it (for those wanting to learn it)  in an easy way.

---

### Post by danbh on 2007-12-07
Ioa: I had thought about that idea too for config files.  Glad to see that others are thinking of the same thing that I am thinking of.

I suppose the idea for Commandline Markup doesn't cover configs files.  I don't think it would work to try and make two separate programs, one for the CLI and one for config file editing because there are times when you need to edit config files and run commands at the same time.  

I think at first I was thinking that you would just call it commandline markup, and just support config files, but if there is a different title/name that better describes, that would be great.  I think descriptive titles are important.

---

### Post by danbh on 2007-12-07
Actually, Commandline Markup is still a good name, IMHO.

Editing config files IS the command line method of configuration.

---

### Post by RIchard James13 on 2007-12-09
I have finished a **Prototype** for you to have a look at. Note it is incomplete and is in no way meant to be what a finished project would look like. I wrote it so you could have a look at it and see if that is the sort of direction you think you should take.

[IMG]http://richardjames13.110mb.com/projects/prototype3.png[/IMG]
[http://richardjames13.110mb.com/projects/projects.html]("http://richardjames13.110mb.com/projects/projects.html")

Have pity on the untidy code, it was a rush job and I have only just in the past month learned python programming and gtk in the last week.

---

### Post by loa on 2007-12-10
Yes, it looks great, just like the kind of program I had imagined. Of course the details could be improved, but the concept looks great. Could there be a way somehow to hide the "output command"-box, to avoid confusing newbies?

---

### Post by RIchard James13 on 2007-12-10
> **loa said:**
> Yes, it looks great, just like the kind of program I had imagined. Of course the details could be improved, but the concept looks great. Could there be a way somehow to hide the "output command"-box, to avoid confusing newbies?

Yes it would be easy to do that but is the thing we are looking for?

Also I have scrounged through the Ubuntu Idea Pool looking for the other project mentioned by smartboyathome I have found the following
[ [IDEA] Linux-PAM graphical configuration utility for desktop users.]("http://ubuntuforums.org/showthread.php?t=621312")
[ Bridge-utils GUI]("http://ubuntuforums.org/showthread.php?t=625711")

Both of these ideas seem to integrate into this thread. 

I have some ideas about different concepts for the GUI.
[LIST]
[*]Have a pane on the right that shows context sensitive help for what option the user is toggling
[*]Have a console with the GUI up the top, as the user enters commands into the shell the GUI shows the options for that command
[*]Something like out of the google video where you have one main window and then smaller child windows with different commands that you can chain together
[/LIST]

Also I think we need to think about the format of the XML file in regards to commands, their options and what the GUI does. For instance most options are simple switches but some options are file arguments like the files given to the tar command. In tar there are a series of interlocking switches for example if you select Concatenate tar files then having non tar files as options is irrelevant but if you want to add files to a tarball then you only select one tar file and list other files as options. Also tar accepts two types of switches the traditional - switch and the more modern -- switch. Some features of tar do not work with the - switch like --delete has no - equivalent. These are just some of the issues to overcome in building up a decent XML standard. I think if we build a GUI for a few different commands then we might have a better understanding of how the XML file will work.

At the moment it sucks:( having to write all that GUI code by hand, dynamically building the GUI from a config file would be much easier.

---

### Post by danbh on 2007-12-15
forgive me if I'm slow in responding, as I don't know python nor pygtk

I could not access the prototype you posted.  The server is posting a 403

Here are two other pages that I'm working off of:
[http://pexpect.sourceforge.net/](http://pexpect.sourceforge.net/)
[http://docs.python.org/lib/module-pty.html](http://docs.python.org/lib/module-pty.html)


I'll post more when I come up with something cohesive  :)

---

### Post by RIchard James13 on 2007-12-16
> **danbh said:**
> forgive me if I'm slow in responding, as I don't know python nor pygtk

I could not access the prototype you posted.  The server is posting a 403

Here are two other pages that I'm working off of:
[http://pexpect.sourceforge.net/](http://pexpect.sourceforge.net/)
[http://docs.python.org/lib/module-pty.html](http://docs.python.org/lib/module-pty.html)


I'll post more when I come up with something cohesive  :)

Ok it seems that when I moved files around in my website or at some later time the web hosting provider decided in their infinite wisdom that .py files are not readable, thus a 403 forbidden error. If I changed it to .txt you could access it. Anyway I put it in a tar ball you will just have to extract the file somewhere. Have a little look at the code. please tell me if you don't understand what is happening as I can probably explain most of it.

Basically it work like this:

```

Create an array of pairs where each pair is composed of a option and a format
Build the GUI interface
Modify the interface according to the array
From the array work out the format of the command line
Print the command line at the bottom of the GUI

Loop forever until the user exits the program
    Draw the GUI and wait for user input
    If the user alters the Interface then
        Modify the array according to the interface
        From the array work out the format of the command line
        Print the command line at the bottom
End Loop

```

Some of the code is a bit complicated due to the way it has to work. For instance if you go into the archive filename and delete the entire filename you will see the f option disappear. Come to think of it I don't know if it should do that. Anyway it works simply for now.

Next we need some way to build the GUI from a config file, preferably a XML one.

---

### Post by danbh on 2008-01-01
ok!!!!
I finished my demo
I will update the front post with RIchard James13's demo and mine.

---

### Post by Tundro Walker on 2008-01-02
In using the command-line, I always thought a code-completion and intellisense would be nice to have.  Sure, you've got man pages and what-not, but it'd be nice to start typing a command, and a drop-down shows up of possible commands to choose from, then it expands to show syntax, arguments/switches, etc.

As for the OP's idea, from my days of using Acid Pro on Windows, what I really liked was the ability to chain effects modules together via GUI.  Basically, you started with a raw sound (the dry mix), and went into effects and added modules.  Each effects module had its own options, and they were laid out right in front of you, which piqued curiosity to mess with them, and you could F1 or rollover them to get more detailed help.  It was all just right there, you could shift them around so they chained together differently.  Then, play your sound and the wet mix comes out.

I could see something like this being pretty cool for "non-CLI" folks.  Essentially, you'd make a GUI frame that would show CLI commands in a menu on the side (or where ever).  The user would drag-n-drop the command into the work-space.  The work-space would have rows, and the commands on row 1 are assumed to run before the commands on row 2, etc.  But, the user could chain together commands on the same row, and it's assumed they pipe their results to the next command to the right of the chain.  So, you could do something like...

EG: On the first row, you might use a stand-alone command to make a directory.  Then, moving to row 2, you have several commands chained together to pull some data, pipe it to a couple more commands for formatting and finally echo the lot to a file in the directory you made.  On row 3, you have a command purge out some folder you were just working with.

For each command square plunked into the work-space, the user would click on it to expand the command  properties sub-window for it, letting them set properties, switches, etc for the command.  

When done, they could save the "project" for later use (maybe to feed a file into a chain of events for some kind of formatting), or perhaps have the program dump out an #!/bin/bash .sh text file that the user could toss wherever and schedule to run or something.  It would be like a GUI / visual macro-writing program, which might help some folks who are more right-brained / visual and are otherwise daunted by a basic CLI interface.

EDIT:

I guess what I'm thinking of is something like the [Scratch Programming GUI / Language concept]("http://scratch.mit.edu/") applied to Linux CLI commands.

Of course, the trick to that would be figuring out which CLI commands to do modules for.  Some CLI commands are really, really complex.  So I guess the program would need to be a bit firefox'ish, where folks have the ability to make new command modules and easily add them to their current set.  Also, they could create common-use templates for a command.  

EG: you could make a template for the ECHO command that makes a file.  "echo > filename".  The user would select that from the template drop down, and the command properties would automatically set themselves to do that (user would need to change the filename, of course).  But the same idea could be applied to other commands.


Like the Scratch thing, it'd be cool to hook in some decision-making blocks to fork commands as needed...

EG: Add an if/then block that would fork the project to a different row of commands depending on what circumstances are met.

Basically just turning the Linux CLI into a bunch of giant puzzle pieces users could mess with in a GUI.

---

### Post by danbh on 2008-01-02
Hey Tundro Walker
You should check out this post from before:
[http://ubuntuforums.org/showpost.php?p=3907581&postcount=14](http://ubuntuforums.org/showpost.php?p=3907581&postcount=14)

---

### Post by danbh on 2008-01-02
Ok, so just to say what my code does, since it is a bit of a mess.

It just tests all the apis that I need to code this project.  Python has OOP, which is good, there are buttons, containers, xml parsers and a full fledged shell which I can send text to.  

Next step is to clean up the basics of the program, and have the gui of a single command be clearer.  

THEN, I will make classes that can actually form the demo that J13 made.  

I guess in my mind, the technology selection phase of the project is done.  Next stop, alpha release.  At that point, I'll be much more curious what people think.

---

### Post by UbuWu on 2008-01-02
[Hotwire]("http://code.google.com/p/hotwire-shell/") implements some of these features. Screenshots can be found [here]("http://code.google.com/p/hotwire-shell/wiki/Screenshots").

---

### Post by Tundro Walker on 2008-01-02
This whole thread, ranging form CLI markup to Scratch-like building blocks GUI, definitely sounds like a third-party app in the making, which it sounds like you're starting to do with Python.  I don't think Ubuntu devs should be expected to create something of this magnitude.  Although, it's a great idea and would be nice to have it integrated once someone else develops it.

After thinking about it, I was tempted to crack open Gambas or Python to hock up a quickie idea of Scratch-like Linux CLI code building.  Then I talked myself out of it.  I figure folks who are non-techie can usually find very nice GUI's to do the mundane stuff they do (EG: using Nautilus or Thunar for file management).  And, the techie types will be more likely to just dig into the man pages and write complex shell scripts instead of mucking with a pseudo-GUI.

Googling around for "Scratch-like" interfaces, some folks on some discussion forum (non-Ubuntu) were talking about doing something like that for Python & PyGames.  Sounds good, but I think Python syntax is so simple that it's almost not even worth bothering.  Maybe it is...who knows.  

There's tons of folks who show interest in modifying their desktop visuals, and adding/removing programs.  It'd just be interesting to give them something like Scratch that could help to create minor useful apps for the OS and see what they come up with.

---

### Post by Tundro Walker on 2008-01-02
> **evymetal said:**
> Interesting Idea. There was a google tech-talk recently on this kind of thing:
[http://www.youtube.com/watch?v=faJ8N0giqzw](http://www.youtube.com/watch?v=faJ8N0giqzw)

The talk is a bit wishy-washy for me, but the idea is to have a graphical equivalent to pipes. As you string applications together you "blend" their GUIs,

Dude, yeah, exactly!  For programmer types, it seems pretty pointless, but for the "sit on your butt and tweak your id3 tags on your mp3" right-brainers, it's exactly the bridge they need to cross-over into some light programming.

They don't want to dive right into a programming language, because they're either lazy, it's daunting, they don't have time, or it's so technical it squelches their right-brained creativity.  They want some easy tool to facilitate their creative goal.  And a Scratch-like GUI to help build code can facilitate that.  Much like MS Access helps many non-database folks put together queries with its GUI table linking and criteria setup.

This is spot on.  As Python, SmallTalk/Squeak, etc make the higher level language easier to pickup, there will still be a huge realm of folks that just don't want to "program", if it's about typing out code.  But putting pieces together like lego's, it's right-brained...they'll get that, and it'll pique their interest.  It doesn't have to let them take over the world, it just has to let them do interesting things, like easily schedule a task that then grinds through some files or something.

Groovy.

---

### Post by RIchard James13 on 2008-01-04
I like the **lego** concept since it is similar to the way the shell is used already. Squeak does not deal with complex commands and some of the shell commands can have complex strings.
[PHP]mkisofs -o /tmp/slackware-dvd.iso \
  -R -J -A "Slackware Install" \
  -hide-rr-moved \
  -v -d -N \
  -no-emul-boot -boot-load-size 4 -boot-info-table \
  -sort isolinux/iso.sort \
  -b isolinux/isolinux.bin \
  -c isolinux/isolinux.boot \
  -V "SlackDVD" .[/PHP]

I think that is the major problem in the shell. Programming concepts such as looping are hardly used.

Also I liked the idea of **seeing** what the command does, for instance you can see the Squeak cat move backwards and forwards. For some commands such as text editing commands like cut and paste this would be possible. You could show a sample file before the command and after the command. For some commands that make use of the file system output no data, take tar for example.

I have been working with **Glade** it is a GUI builder. To use it in python you just import the glade module. Load the glade XML file and then run gtk.main() The GUI information is held in a XML file and it is possible to use that dynamically so that as the user changes the command they are using another glade file is loaded and displayed. The problems I have had with Glade are that although it is easy to create a GUI it is not easy to link events like button presses into your python program. First you have to create a dictionary of the functions it is going to call and then you have to link it then you have to write a function for every place in the GUI you want interactivity. An example of what this looks like in another program I am writing is this:
[PHP]        dic = { 
               "on_btnMore_clicked" : self.btnMore_clicked,
               "on_dtmPayment_day_selected" : self.dtmPayment_day_selected,
               "on_btnAddPayment_clicked" : self.btnAddPayment_clicked,
               "on_btnDeletePayment_clicked" : self.btnDeletePayment_clicked,
               "on_btnResetPayment_clicked" : self.btnResetPayment_clicked,
               "on_txtPaymentTotal_changed" : self.txtPaymentTotal_changed,
               "on_txtPaymentPayee_changed" : self.txtPaymentPayee_changed,
               "on_txtAmount1_changed" : self.txtAmount1_changed,
               "on_cmbCategory1_changed" : self.cmbCategory1_changed,
               "on_txtCategoryNumber_changed" : self.txtCategoryNumber_changed,
               "on_txtCategoryName_changed" : self.txtCategoryName_changed,
               "on_btnAddCategory_clicked" : self.btnAddCategory_clicked,
               "on_btnDeleteCategory_clicked" : self.btnDeleteCategory_clicked,
               "on_btnResetCategory_clicked" : self.btnResetCategory_clicked,
               "on_txtPayeeNumber_changed" : self.txtPayeeNumber_changed,
               "on_txtPayeeName_changed" : self.txtPayeeName_changed,
               "on_btnAddPayee_clicked" : self.btnAddPayee_clicked,
               "on_btnDeletePayee_clicked" : self.btnDeletePayee_clicked,
               "on_btnResetPayee_clicked" : self.btnResetPayee_clicked,
               "on_nbkAccounts_switch_page" : self.nbkAccounts_switch_page,
               "on_MainWindow_destroy" : gtk.main_quit}
        self.wTree.signal_autoconnect(dic)[/PHP]

If you where to use the glade XML file you need to take into consideration the events for the creation of the command. You could have a glade file and another XML that contains that extra info or you could combine them.

Another option is using **plugins** I am writing a RPG Game at the momemnt and I find the lack of good tools annoying so I thought I would write a 2D RPG tool environment but then I thought what if I wanted to build some other sort of Game a 2D sprite editor might not be important for a 3D game. So I thought about using a plugin based technology for this. Basically with plugins you have a framework that imports objects which are then activated within the framework and can do various things. Eclipse is an example of such a thing. I also glazed over[COLOR="Blue"]_ [this ]("http://www.ddj.com/cpp/204202899")_[/COLOR] tutorial on the DrDobbs website detailing how to do this in C++.

With the plugin concept each command would have it's own python object or file that would be imported instead of using XML. This gets over the problem of how to encode into XML things like [COLOR="SlateGray"]"this command line option should be a text box that contains a file or a list of files that the program will add to the archive, if there are no files listed then the -f switch should be removed and files should be input from stdin"[/COLOR]. Maybe I'm just bad at writing XML and I think the Plugin Object solution is easier. 

I can see that the XML solution is cleaner but the Plugin option is more programmable. Either way they could be used in a Squeak like environment or a simpler environment since they only describe the UI and what it does. They don't enforce in what way the program using them has to behave.

With the VTE widget I have successfully recreated my prototype so that it uses Glade for the UI and hides/shows the command details and puts a Terminal below the command. I have not yet connected the terminal to the command as danbh has done. Also because I used glade I need to rewrite all the signal/event code. 

I have to do some *Real Work* next week and I shall continue to work on my python skills but I will be using it to manipulate a Mysql database in a buisness context.

---

### Post by danbh on 2008-01-13
I've done some more work, check it out!!

[http://hollocher.hobby-site.org/CLIML/](http://hollocher.hobby-site.org/CLIML/)

Hey RIchard James13!  you are using GLADE?  Do you like it better than pygtk?  Is your stuff on your server?  we should definitely start working together.  I feel that I have a working demo at this point, that really shows what I'm looking for.  

My subscription to this thread is weird.  It doesn't always notify me of posts.  

Anyway, the way to run the demo is this.  Set CLIML.py to be executable.  Then, run it with the name of one of the other files as input.  The magic should happen.

RJ13, I'm gona see if I can see your stuff right now...

---

### Post by danbh on 2008-01-13
well, i don't see the glade stuff

Maybe we can chat sometime in #ubuntu-offtopic

---

### Post by RIchard James13 on 2008-01-15
Sorry about the delay, I had another days work unplanned today and my son wanted to watch steam trains on youtube on Monday

Ok I just added the GLADE version to the website. As you can see from the screenshot it embeds a VTE in the details section, basically i just copied your code and modified it work in my program. GLADE does not have a VTE widget so I used GLADE to give me the bottommost vbox called vboxMain2 and I added the VTE to the bottom of it. It is possible to load GLADE files in and add them at will to your UI. So it is theoretically possible to have a UI for each program (tar, ls, cat etc) and dynamically load the UI at runtime. However the UI does nothing without code behind it and I think it would be better to have our own XML file version that does both the UI and the coding. The coding is pretty simple it is basically some sort of logic game with switches. 

Also I can't seem to access your website. I thought it might be my connection so i tried a web proxy and still no go.

As for meeting on IRC that sounds like a good idea. But we need to arrange a time. Now I am +10 Hours GMT so even though my watch says it is 7:45pm Tue it is 2:45pm GMT right now. All I can say is I am not free on Saturday and any time that is between 12midnight (Aust EST) and 7am (Aust EST) I am usually asleep. So that makes me free from
Tue 15th 9pm GMT to Wed 16th 2pm GMT
Wed 16th 9pm GMT to Thur 17th 2pm GMT
Thur 17th 9pm GMT to Fri 18th 2pm GMT
Then it is Saturday for me and I have three birthday parties to attend to.

I hope I got that right.

Ok you gave me the channel #ubuntu-offtopic I assume that is on freenode?
Giving it a test try now ok just accidentaly created a #ubunutu-offtopic channel and had to figure out why no-one was there. Got to #ubuntu-offtopic everything seems to work.

---

### Post by danbh on 2008-01-15
Hmmm, I live in the Americas, so it looks like we live on opposite sides of the planet!

If you couldn't access my website, it means my computer is turned off, and I was probably asleep.   I will have to try and make sense of the times you gave...

---

### Post by danbh on 2008-01-15
Tue 15th 9pm GMT to Wed 16th 2pm GMT

How about 9pm tonight, GMT.

---

### Post by RIchard James13 on 2008-01-15
How about 9pm tonight, GMT.

That should be 7AM Aust Eastern Standard Time on Thursday
Will be there.

---

### Post by danbh on 2008-01-15
I noticed that you posted that message a few minutes ago.  How about now?

---

### Post by danbh on 2008-01-15
my name is danbhfive

---

### Post by mouseboyx on 2008-01-15
This would be cool if it were to integrate a terminal into every program.

---

### Post by RIchard James13 on 2008-01-16
I am on there right now and will try to be there for two hours. my ncik being RichardJames13 I will reply again on this forum when I leave the IRC channel if I don't meet you there.

I'm off the channel now. I will hopefully see you there *in the morning*

---

### Post by danbh on 2008-01-16
I'm there now, I till checkin every so often.

My nick is danbhfive

---

### Post by danbh on 2008-01-16
[https://launchpad.net/climl](https://launchpad.net/climl)

---

### Post by danbh on 2008-01-19
ok, I don't really know how to actually get code onto launchpad, but feel free to do whatever you can with the launchpad site.  

Right now, my latest code is here:
[http://hollocher.hobby-site.org/CLIML/](http://hollocher.hobby-site.org/CLIML/)

I'm using git to manage revisions, but I don't really know how that works either.

ah well!  :p

---

### Post by Shin_Gouki2501 on 2008-01-19
the idea sounds very nice i always thought about something similar 
but i thought it would be too hard  to conivce all developers
to use that but the more i thin about that the more i like it!

---

### Post by danbh on 2008-01-19
ok, so I have been able to post some code to launchpad.  If launchpad is able fulfill all our needs, then I will consider this thread closed. 

[https://launchpad.net/climl](https://launchpad.net/climl)

---

### Post by ryanVickers on 2008-01-19
interesting idea - It reminds me of things like kdialog and zenity, but if you could have the power of say, a QT .ui file, and easily hook it into somehting like a python or bash file, (I am aware or pyGTK and pyQT by the way) I think this would be most useful!  It could do things in a way that people learn though :D

---

### Post by danbh on 2008-01-19
hey ryan,
well check out what I have so far!  I've got some code posted on launchpad

---

### Post by ryanVickers on 2008-01-19
lol I just remembered something... when I first saw this, I was sure it reminded me of something, but that feeling quickly passed; it seemed rather unique.  However, I just realized that a while ago I was just sitting around thinking something almost exactly like this!  Instead of a terminal, one could choose to run a program, and it was a scrolling menu of all the currently installed stand-alone commands, like ls, cd, etc. and one could just pick one, checkoff/on or set all the options with typing and checkmarks, and then hit run! :p

---

### Post by danbh on 2008-01-19
hey ryan,
You should check out Hotwire at: [http://code.google.com/p/hotwire-shell/](http://code.google.com/p/hotwire-shell/)

That might be what you are looking for.

---

### Post by ryanVickers on 2008-01-19
I don't think it is - that could be more along the lines of my project to make the terminal fool-proof for people who tend to not think twice about pasting random commands and running them ;)

I'm thinking of just one window, graphical, with a list of every command, and when you pick a command, a bunch of options will appear, like sway, for "ls", options would include every switch, like -lt, etc etc... :p
it would be a graphical terminal where you pick and choose instead of typing!! :D

---

### Post by RIchard James13 on 2008-01-20
CLIML could be described as an intermediary between the GUI world and the shell. At the moment I see this project as pretty well summing up the poll at the start. "A set of training wheels for the shell". 

There is always going to be some sort of question of how do you do that for people? For me I came from the shell world, when I first started using Linux, X Windows was a toy, there was no word processor, no KDE, no Gnome, no games. Just a few toys (xroach) and maybe a few picture and text editors. So almost everything you did was through the shell. Of course CLIML is not aimed at me, it is aimed at people who are used to systems driven by a GUI. 

One of my aims therefore is to construct CLIML in such a way as to make the transition from GUI to shell easier. In reaching that goal I need to simplify the way I see the shell but at the same time not lose the power inherent in it.

So I want to create .climl files that are run through the CLIML program. These files might be found on wiki's or forums. Their purpose is to execute certain commands in the shell in order to do one thing. That thing varies depending on the .climl file you are using. When the CLIML program gets the .climl file it not only allows the user to just execute the commands but also shows them what commands are to be executed, also some parameters can be altered.

From there people hopefully get used to executing shell commands and eventually will remove the training wheels of CLIML and jump into the shell and start executing their own commands.

---

### Post by danbh on 2008-01-22
I located a duplicate of this idea:
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/85724](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/85724)

Though, the way I am aiming, I want this project to be a bit broader than just the basic commands.  I want a tool that people can use for a variety of purposes.

---

### Post by RIchard James13 on 2008-01-23
> **danbh said:**
> I located a duplicate of this idea:
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/85724](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/85724)


Read and Bookmarked those links.

> Though, the way I am aiming, I want this project to be a bit broader than just the basic commands.  I want a tool that people can use for a variety of purposes.

Do you have a plan of action? Or some type of program that is similar? So that we can work out the specifications to build this project. I suppose a big thing is what is the difference between our project and say the hotwire shell?

Hopefully on the weekend I can write up some specifications for this project. I have been sick since Monday but am better now.

---

### Post by danbh on 2008-01-23
yes I do.  At least in my mind.  I tried to write something up on the launchpad site.

I'm putting everything up on launchpad:  [https://launchpad.net/climl](https://launchpad.net/climl)

Any plans of action that I have, I'm putting up there.  Take your time mate.  Let me know if you need any help understanding my code.

Dan

---

### Post by Shin_Gouki2501 on 2008-01-23
i saw a utube video from hotwire.. it didnt convince me...

---

### Post by danbh on 2008-01-23
yeah, I looked briefly at hotwire before starting this project.  I consider my idea to be different from hotwire, and I'm not that interested in hotwire, and I suspect that the hotwire developer is not interested in what I'm coding up.  

To me, I knew hotwire has a different goal than what I am looking for when I read that 'rm' was nerfed such that it moved files to a trash folder, instead of deleting them.  That's bad, because on all other linux systems, rm doesn't move files to a trash folder.  It does something much more dangerous.  It deletes(removes) them.  So, if you train a person to believe that rm isn't that dangerous, you are setting them up for mistakes later on down the road, when they use something other than hotwire.

I think people compare hotwire to my idea because they are both GUI mixed with CLI.  But, hotwire is like the GUI multiplied times the CLI, where as I'm looking for just GUI plus CLI.

---

### Post by danbh on 2008-01-27
Hey RIchard James13:
I'm making ALLOT of updates to the project.  I noticed that you were going to work on some specifications this weekend.  I hope you take a look at the project, and some of the bug reports on launchpad.  I am filing features that I want as bugs, and I invite you to do the same.  (for that matter, anyone reading this thread)

Anyway, I hope you are still on board.  So far, I'm the only one who has presence on the launchpad site  :(

Dan

---

### Post by RIchard James13 on 2008-01-28
I've added a bug, it's an actual bug :eek: . I have installed the bazaar plugin for eclipse, to make working on the project easier. Tonight I will work on this bug. Might add some specifications to the project, maybe for some sample commands. I might write some sample dotcliml files and find out where the current code can't do this or that to develop specifications.

---

### Post by CTenorman on 2008-02-02
I've been giving some thought to the potential layout of a program like this. Keep in mind I say all this as someone relatively new to Linux, though perhaps this is an asset - I'm the target audience! :) Having multiple panes might really assist the user. I was thinking that one could have all the potential commands open to the user in a pane at the left side of the screen, a man/info page viewer at the right side of the screen, and the graphical command line in the middle.

The commands could be grouped by category (ie, file management, applications, etc). The user would click on a category and a selection of commands would drop down. This list would contain the name of the program and a brief description of what it does, generated from the man page. The user would click on the command they wanted to perform. This would open the man or info page at the right side of the screen in a graphical man viewer of some sort, perhaps gnome's help (it already works for that purpose). A table of contents generated at the left side of the man pane (rather like evince generates from PDF files) might be helpful, and it should be able to choose between the man and info pages.

In the middle of the screen one could have a command line generator modeled after mail filters. The command would automatically be inserted once the user clicked on the desired command in the left pane. At the right of the pane could be a button "Add Option." The user would then choose the option they wanted from a drop-down menu. This menu could be generated dynamically from the man page so it's always updated. The user could add as many options as they liked, and alter the parameters of that option where applicable. At the end of the line one could choose either to have the command executed individually, or string the output to another command. If the latter option is chosen, the user will be presented with another row of dialog boxes and so on like above. At the top of this pane might be the command as it would appear in the command line itself. The user could edit it by clicking an edit button. 

Above the command line generator could be the actual terminal out, much as we see it in most terminals today.

I think all this could be made a good deal simpler if we simply create the program out of parsing man pages. All the info is right there, and everything could be generated from them. These are just some preliminary thoughts to throw out there – if anyone could tell me where I might put them in the proper place, or how they might be refined, I'd love to hear about it. Figuring out the command line is a great experience, but learning by doing is the best tutorial of all, and this might really help with that.  All the best,

Scott

---

### Post by danbh on 2008-02-02
Hey there, this thread was started by me, based on an idea I had.  I am now coding up this idea of mine.  I love to listen to other people's feedback, which is why I started this thread in the first place.  I wanted to here other people's feedback regarding my idea.

At this point, I already have a certain base of code, and I am going in a certain direction.  So, if you want to comment on the original idea, I'm sorry, its too late for that.  

But, if you would like to comment on the direction that I am currently going, please do.  [https://launchpad.net/climl](https://launchpad.net/climl)

I don't know launchpad that well, so feel free to make use of it however you can.

If you can't figure out how to get the code from there, you can try my computer directly at [http://hollocher.hobby-site.org/CLIML/](http://hollocher.hobby-site.org/CLIML/)

It sounds like you may want to have someone from Ubuntu proper listen to your ideas.  That aint me, and in fact, I'm in the same boat.  I figure that if I code it myself, it has a much better chance of making it into ubuntu  :p

If you have trouble running the program, please post here, and I'll help.

---

### Post by CTenorman on 2008-02-02
Ok, thanks for clarifying that!

I tried running your program, but received the message "permission denied." Being somewhat new I'm not sure of the exact command, is it chmod or chown, or something like that? Thanks!

---

### Post by RIchard James13 on 2008-02-02
> **danbh said:**
> It sounds like you may want to have someone from Ubuntu proper listen to your ideas.  That aint me, and in fact, I'm in the same boat.  I figure that if I code it myself, it has a much better chance of making it into ubuntu  :p

I think we should use a wiki. That way we can have other people store .climl files. Then people who want to use the files can go there and browse and also download the CLIML program to use for their selection. If you have enough interesting .climl files then more people will use it.

Note the wiki is a future project idea, not something we should try and do until we have CLIML working as we want.

I just worked out that everytime I tried to Update the project in Eclipse it was doing it from my system. I need to use pull to get it off of your tree/branch then merge. I kept on thinking why hasn't he done any updates? but you had  :confused: The Bazaar plugin for eclipse is Beta software and it shows.

---

### Post by danbh on 2008-02-02
yeah, permissions problems would be something going wrong on your side.

I would suggest downloading the files, and then

sudo chown user:user -R climl_files_folder
where user is your user name

Then, chmod +x CLIML.py

then you should be able to run it with:
./CLIML.py name_of_file.climl

I hope someday to make this easier.

---

### Post by RIchard James13 on 2008-02-02
> **CTenorman said:**
> Ok, thanks for clarifying that!

I tried running your program, but received the message "permission denied." Being somewhat new I'm not sure of the exact command, is it chmod or chown, or something like that? Thanks!

try 
chmod a+x CLIML.py

That gives execute permission to all (owner, group, others)
ls -al CLIML.py should show something like
```

-rwxr-xr-x 1 richard richard 20014 2008-02-03 10:39 CLIML.py
  ^  ^  ^ 
  |  |  | 
  |  |  Others permissions
  |  | 
  |  Group permissions
  |
  owners permissions

r is read, w is write, x is execute

```

---

### Post by danbh on 2008-02-02
heh, ok Richard.  I don't know much about any of this stuff, either.  

Yeah, the wiki may be a good idea.  I was thinking of hooking up with the howto section of these forums.  Instead of just writing an essay for a howto, people could write a climl file.

I was also thinking of making a CLIML desktop, making a climl replacement for some of the major desktop apps, like thunar filemanager, wireless config, whatever.  


Also, I am going to try to keep the first post of this forum newbie relevant.  I added some commands that will hopefully allow people to test the project.  The only problem is that they download right from my computer, which isn't always on.

---

### Post by RIchard James13 on 2008-02-02
I want a server, not just for this project but for other ones in the future. The problem is cost. I would preferably like to have a server hosted running LAMP and dedicated Domain Names. That way it is always on and people can always find it. Because I am studying for the next 6 months and may not be able to get a job until after that time I don't have the money to afford it yet.

My other option would be to host a server on my DSL line that is always on and use dynamic DNS for the domain name. I think I might do that next weekend. I have all the hardware I just haven't loaded the software onto the machine yet.

Another question is how do we package CLIML during testing so that people can try it? Should we use a .deb package? or just the tarball? If it is a .deb package how do they get the .climl files out? Maybe we should have a test website with the .climl files on it? I have an account at 110mb hosting, maybe we can create a specific site there if I can't get the dynamic DNS working.

---

### Post by danbh on 2008-02-02
I'm running a server off of my computer myself.  I'm kinda using dynamic ip, but my ip address almost never changes.  

To all the questions that you just posted, my answer is 'I dunno'   :)

My hope is that ultimately, someone can d/l a climl file, and just double click on it.

---

### Post by danbh on 2008-02-08
a small bump for this thread, I posted a youtube vid.  

[http://www.youtube.com/watch?v=dxAwjwFIWIQ](http://www.youtube.com/watch?v=dxAwjwFIWIQ)

The link is also on the first post.

---

### Post by RIchard James13 on 2008-02-09
About the video, I am shocked, I never though we would get this far. Obviously we should keep on working.

Also OSNews has an article about someone's blog about "Why can't free software GUIs be empowering instead of limiting?"
[http://osnews.com/comments/19304]("http://osnews.com/comments/19304")
[http://www.freesoftwaremagazine.com/columns/why_cant_free_software_guis_be_empowering_instead_limiting]("http://www.freesoftwaremagazine.com/columns/why_cant_free_software_guis_be_empowering_instead_limiting")
Some of that looks very similar to our work, which shows other people are interested in such a project.

---

### Post by danbh on 2008-02-10
Just a small hint regarding the progress of the project.  I'm unemployed atm, so its either this, or computer games, for my free time.  Basically, I can put in several hours a day for the time being.  

But it always sucks to waste time.  I spent hours trying to get it onto windows, but I have yet to figure out how to get the vte widget over to windows.  

It just don't work!!  Even cygwin is failing me.  

I think that for now, I will complete the file change actions, and then maybe clean up the code a bit.  I also want to make some more vids describing the project.  Then, that will be it.

---

### Post by RIchard James13 on 2008-02-11
I'm currently trying to finish off my Diploma of IT. I finish in June and then I would like to get a job and maybe do Uni part time. So at the moment I am finding most of my time allocated to CLIML ending up on the weekends. Fortunately last semester I finished most of my programming work so I should be able to do programming on other projects instead, some of which would be CLIML.

As for porting to MS Windows, I can't really see the point since it doesn't natively have the underlying shell tools that Linux has. When I start thinking about porting the first things that come to mind are making the code portable to qt and maybe wxWidgets. That way the program could be more easily used in KDE distro's like OpenSuse and also wxWidgets might make it easier to get onto MS Windows. But with KDE now moving towards MS Windows who knows what widget set to use?

---

### Post by danbh on 2008-02-11
well, by port, I meant use cygwin ports.  It just failed though.

---

### Post by essexboyracer on 2008-02-18
I am joining the party late here and may not be drinking the same as you guys, but doesn't filezilla (or other ftp programs) do something similar, but maybe in reverse, i.e. show the CLI output from GUI interactions?

---

### Post by danbh on 2008-02-18
> **essexboyracer said:**
> I am joining the party late here and may not be drinking the same as you guys, but doesn't filezilla (or other ftp programs) do something similar, but maybe in reverse, i.e. show the CLI output from GUI interactions?

I don't know, I haven't used filezilla.  Have you checked out the youtube video?

---

### Post by danbh on 2008-04-02
Just posting a few links of some competing projects, or possibly competing projects.  I can't seem to get GUIcompletion working.

[http://linux.pte.hu/~pipas/GUIcompletion/index.html](http://linux.pte.hu/~pipas/GUIcompletion/index.html)  [http://linux.pte.hu/~pipas/CUI/index.html](http://linux.pte.hu/~pipas/CUI/index.html)

---

### Post by danbh on 2008-04-02
ok, new description for this project!!!!!!!  Wooo Whooo!

Task-oriented graphical documentation for the CLI

---

