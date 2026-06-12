---
title: "My Idea for a System Restore Equivilant"
date: 2010-03-29
forum: The Cafe
---

### Post by chessnerd on 2010-03-29
I have read one too many requests for Ubuntu to get a "System Restore Equivalent" and so I have here a modest proposal of how I think a Linux System Restore in Ubuntu *could* work. My lack of programming skills at the moment prevent me from making this a reality (without a few weeks of studying how to write effective shell scripts) but I think that anyone with an intermediate level of bash programming skill should be able to write a script that could do as I describe below...

**Ubuntu Configuration Revival** - a basic utility that will create a *"Config Flash Save"* (restore point) of vital configuration files and allows the user to restore these config files to their previous state in the event of system instability.

(Name of program and program parts could easily be changed and I wouldn't think anything of it. Just needed to give the stuff a name.)

**Step 1:** Select important configuration files for backup (Compiz, GRUB, Nautilus, etc) The hard part about this being how to choose which files to save and figuring out where in the file system they are. Also, you have to deal with the fact that not everyone is going to have all the programs installed. Any ideas for what configuration files you feel are very important, or ones that frequently cause problems, would be of help here.

**Step 2:** Make an easy to use CLI program that can make and save a Config Flash Save and will make sure that no more than 20 are ever saved at any one time (delete older ones) to save HDD space. Just a basic command like *ucr --flash* could then create a complete Flash Save.

**Step 3:** Write a program that archives the config files and can replace the existing with the old in one command. If an even older one is needed, the user should be able to specify which one. Maybe a command like *ucr --revive 10*, which would restore to Config Flash number 10 (the tenth oldest). A better way still would be to let the user pick specific programs to restore to a previous state - so *ucr --revive compiz* would restore all Compiz configs in the most recent restore and *ucr --revive 5 compiz* would go back 5 Flash Saves and restore from there. Also, before the system is revived, the current configuration should be saved as well in case the older configuration files cause worse problems. This could be undone using a command like *ucr --unrevive* that would undo the previous revival.

**Optional:** A GUI, scheduled Flash Saves, and customization that would let the user choose additional config files to back-up.


Like I said, I am not a Linux programmer. I know enough shell scripting to make *very* basic programs, but that's it. I could *probably* make a simple command that could grab the files and store them in an archive and with a lot of browsing around the net I *might* be able to actually have the configuration files be returned to a previous state, but it would take me days and the two scripts would be buggy, incomplete, and not usable by newbie users unless they want to break their system.

If no one feels that this idea is of any real worth then I guess I'll put it off until the summer and learn to do some serious shell scripting. Then, if I ever get it to a point that I feel is usable by others, I'll post it up here to share for those who do want it.
If this is the case, could you help me get started on making a list of all the config files that would need to be backed up? There are a lot of config files in Ubuntu and for this to work a good percentage would need to be backed up, but I don't know where to start.

---

### Post by cdekter on 2010-03-30
This is indeed a good idea, and off the top of my head I can't think of any technical reasons why it could not be implemented. Why don't you create an entry on the Ubuntu Brainstorm site?

The main difficulty would be in defining the requirements e.g.: which files to back up, should they be monitored and automatically backed up, user vs system config files etc etc. 

You could probably start with the dpkg conffile database which keeps track of all system config files (as opposed to user config files kept in your own home directory). Next would be navigating the quagmire of config files and other junk that is maintained under a user's home directory.

---

### Post by 23meg on 2010-03-30
Take a look at [Mound]("http://jacob.peddicord.net/2009/09/mound-data-manager.html"), and [etckeeper]("http://fnords.wordpress.com/2009/02/23/etckeeper-chronicles-1/").

---

### Post by red_Marvin on 2010-03-31
Dunno about it's current state as it was abandoned, but [sysres](https://launchpad.net/sysres) might do some of the things you want.

---

### Post by NightwishFan on 2010-03-31
Making a nice framework for this would be cool, then being open source it could be modified for any distro to use fairly easy. That would go a long way for Ubuntu on the desktop. A restore application you can actually understand and control.

---

