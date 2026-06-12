---
title: "Newbie questions"
date: 2007-01-02
forum: The Cafe
---

### Post by Tlacuilo on 2007-01-02
OK - Let's see if I can make contact.  First let me introduce myself. I am a 59 year-old retired Marine MGySgt, (did 33 yrs) who has been a computor for many years. Started out with big boxes (used fortran and cobal) got into home machines with a sinclair and commodore and migrated to pc's. Make my own machines. Understand and am good with windows, miss dos, always interested in unix/linux/(now ubuntu) for home application. 

My philosophy has always been to stay one step _below_ the "cutting edge" thereby letting the bugs get worked out, and being able to buy hardware/software cheaper.  Vista is coming out, and it looks like a good time to get into a better operating system.  

Here's my current idea. - keep this machine as windoze for now, and install ubuntu on an old laptop and and also a desktop. Make them work, make myself somewhat familiar with ubuntu, and then switch the main machine over.

Questions: Does this sound feasable? Are there hardware limitations? Where is a good place to start?

---

### Post by IYY on 2007-01-02
> Understand and am good with windows, miss dos, always interested in unix/linux/(now ubuntu) for home application. 

For Windows "power users" such as yourself, it's important to keep an open mind and understand that some things are done differently in Linux than in Windows. This can be frustrating at first, but the new way is often better and more comfortable once you get used to it (I don't think this will be a problem in your particular case, since you have experience not only with Windows but with other operating systems as well.)

The fact that you miss DOS is a good sign that Linux is right for you. The shell (terminal, command line interface) on modern Linux systems is far more powerful and useful than the one in DOS, and is often used. This scares some Windows users who find this way of doing things too old fashioned, but can actually make life a lot easier and faster. 

> Does this sound feasable?

Your plan makes sense, and I like your philosophy. In fact, many Linux users choose to run older software in order to make sure it's stable. If you like this idea, perhaps you should be using Debian: I believe it has three branches, all being developed at simultaneously: stable, unstable and testing. If you use the stable branch, you will be using older software, but with more confidence that it has been thoroughly tested. 

Of course, you can get a similar effect by using the Long Term Support (LTS) versions of Ubuntu. The current LTS edition is Dapper Drake.

> Are there hardware limitations? 

Ubuntu should work fine on "last generation" hardware, like a Pentium III.

> Where is a good place to start?

Be sure to ask on these forums when you need help fixing, installing or setting some thing up, or just need an explanation. 

[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) is a good site for basic command-line codes to quickly set some common things up on fresh Ubuntu installations (it won't teach you much, but will save hassles).
[http://tldp.org/](http://tldp.org/) has all sorts of instruction guides for GNU/Linux in general, and the shell.
[https://help.ubuntu.com/](https://help.ubuntu.com/) has some free help manuals for Ubuntu.

---

### Post by maniacmusician on 2007-01-02
phew, IYY covered just about everything. It's likely that your most invaluable resource will be these forums, I love them. I also find the following site helpful though it's not mentioned much:

[http://ubuntu-tutorials.com/](http://ubuntu-tutorials.com/)

It's filled with a lot of goodies. I was going to put up a similar site myself once I've written a few how-to's that aren't available in other places, but I haven't gotten around to it yet :) too many other projects. Anyways, good luck! your plan does indeed sound like a good one. make sure to ask here for help if you get stuck (though the best way to learn is to figure things out :) ), we're very helpful.

---

### Post by SoggyCornflake on 2007-01-02
> **Tlacuilo said:**
> Here's my current idea. - keep this machine as windoze for now, and install ubuntu on an old laptop and and also a desktop. Make them work, make myself somewhat familiar with ubuntu, and then switch the main machine over.

Questions: Does this sound feasable? Are there hardware limitations? Where is a good place to start?

To me, it sounds like a good approach - especially if you have some "Can't Live without" Windows programs. There are some projects to run Windows programs in Linux, but they are still bleeding edge.

If your desktop computer is fairly standard, then Unbuntu should run without much trouble.  The hardware detection program used by Unbuntu's installation is very good.  The laptop may give you  a bit more trouble since laptops generally are less standard than desktop machines.

Ubuntu is very much intended to be use by people used to GUI environments, but if you miss DOS, you can always use the command line.  There's even a Linux project that emulates DOS call dosemu so if you have some old DOS program you want to run, you might be able to get it running under Linux.  There are also projects for running Commodore programs as will.

I hope you enjoy Ubuntu.  At my house we've gone over to Ubuntu completely.  My kids sometimes wish we had a Windows box to play some games, but virus and Spam-bots are a thing of the past in our home.

---

### Post by Tlacuilo on 2007-01-02
Thanks - That gave me the warm fuzzy that I was looking for.  Now to find a spare few hours, free from honey-do's.....

---

### Post by BoyOfDestiny on 2007-01-02
> **Tlacuilo said:**
> Thanks - That gave me the warm fuzzy that I was looking for.  Now to find a spare few hours, free from honey-do's.....

You'll be fine. If you miss commandline, you'll love tab completion. Put part of a command, pressing tab will complete, if not press again, and it will list any commands that match (same goes for filenames you type)

dir still works
you can use ls instead of it
cd works as it should
instead of copy cp
mkdir still does the job
mv for move (also used for renaming, for example 
mv myfile myfilerenamed
will change myfile to myfilerenamed)

type man for a manual on any command

i.e. 

man dir

press q to quit the manual info.


Other than that, the forum folk will help you. If you are lucky,
your install will require no tweaking. 

A few things to get used to is package management (vs going to places hunting for your files...)

Anyway, have fun and best of luck.   

If you miss dos, you can try freedos + qemu, but my personal favorite is DOSBOX (it's in the ubuntu repos) runs many DOS games and apps like a charm. 

EDIT: Oh yeah, for commodore, VICE is the emulator you want.

---

### Post by seijuro on 2007-01-02
> **Tlacuilo said:**
> Here's my current idea. - keep this machine as windoze for now, and install ubuntu on an old laptop and and also a desktop. Make them work, make myself somewhat familiar with ubuntu, and then switch the main machine over.


Sounds like an outstanding plan to me. Excluding the laptop bit that is pretty much how I got into linux some 5ish years ago. Ubuntu is a really great place to start, far more newbie friendly than the distro I first learned.

---

