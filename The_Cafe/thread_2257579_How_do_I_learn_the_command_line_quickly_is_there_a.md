---
title: "How do I learn the command line quickly? is there a site where it lets you practice?"
date: 2014-12-20
forum: The Cafe
---

### Post by raymond19 on 2014-12-20
I don't feel confident with the command line. I feel like there's always more than 1 way to enter a command that does the same thing and when I see this, it would literally confused the heck out of me. Like for example. I see "CD ~" used as navigating to previous directory but "CD" works as well.

---

### Post by tgalati4 on 2014-12-20
Well, cd and cd ~.  CD is not defined.

> tgalati4@Mint17 ~ $ CD
CD: command not found


Just keep at it.  In 10 years time you will be good at it.

Points for figuring out a few more:

```
cd .
cd ./
cd ./.
cd ././
cd ././.
cd ./././
cd ./././.
cd $PWD
cd /; cd $PWD


```

---

### Post by raymond19 on 2014-12-20
LOL what, 10 years? OMG NO!

---

### Post by tgalati4 on 2014-12-20
Some a little sooner.

---

### Post by raymond19 on 2014-12-20
I really want to become good, I am willing to sacrifice a whole year to just learning the command line.

---

### Post by Bashing-om on 2014-12-20
raymond19; Yepper;

2 years to become comfortable is the rule of thumb.
10 years is the rite of passage.
Good place to start:
[http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz) <=advanced command line tutorial
[https://sites.google.com/site/beginnersearch/](https://sites.google.com/site/beginnersearch/) <-Linux Beginner Search Engine
[http://tille.garrels.be/training/tldp/index.html](http://tille.garrels.be/training/tldp/index.html) <-Introduction to Linux A Hands on Guide
[http://www.er.uqam.ca/nobel/r10735/unixcomm.html](http://www.er.uqam.ca/nobel/r10735/unixcomm.html) <-summary of useful Linux abbreviations, directories, files, and commands.
[http://linux.chrissweeney.co.uk/index.php](http://linux.chrissweeney.co.uk/index.php) <-things I've learnt over time about linux from a beginners point of view.
[http://tldp.org/LDP/intro-linux/html/sect_05_02.html](http://tldp.org/LDP/intro-linux/html/sect_05_02.html)
[http://linuxcommand.org/lts0060.php](http://linuxcommand.org/lts0060.php) --learnng the shell


And last but not least, you will find it 1st:
[https://help.ubuntu.com/community/PopularPages](https://help.ubuntu.com/community/PopularPages)

[INDENT][INDENT]in this fast moving target
[INDENT][INDENT][INDENT]the Command Line Interface remains a constant
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by WinEunuchs2Unix on 2014-12-20
Seems little point in studying the command line.  You use it as you need it and google the command and parameters required as the need arises.

I imagine 90% of the commands in the Linuxverse you will never need to learn.

Others in the 10% like grep, dmesg, cat, ls, find, etc. you will probably never use all the parameters and command line switches on them.

Something you google might lead you to use "blkid" with a certain parameter which you'll only use once to get the UUID of a hard disk for example.  Then 6 months later you'll google it again and use it again but can you say you ever learned it when you only used it twice and forgot about it between those two times?

---

### Post by raymond19 on 2014-12-20
How about I come up with situations where I use them more often as a way to practice and cement them into my mind. I know I won't use them but I want to know the situations when I do need to use them.

---

### Post by raymond19 on 2014-12-20
how flexible do you think those resources are? I intend to go into more advacned linux distros later in the future such as archlinux or slackware.

---

### Post by flaymond on 2014-12-20
Im using Linux for 2 months, and just know that Terminal is just like a programming language. You give it instruction, and it will do. Well, it is not really a programming language since it use for managing your OS. You can make infinity command, loop or anything, but I don't know if you can create a mini software from it since we using Bourne-Again Shell. I know some basics, you will learn it by time and when you need it. 10 years for bash shell? Yup, I think you really need 10,000 hours to be a shell expert. I don't know if my opinion was relevance or logic.

Here is the link that I'm glad to share with you -

[http://linux-training.be/files/books/LinuxFun.pdf](http://linux-training.be/files/books/LinuxFun.pdf) - well, it just tell you some useful basics. But, for me..this is the place to start to learn Bash and Linux as well.

---

### Post by DuckHook on 2014-12-21
> **WinEunuchs2Unix said:**
> Seems little point in studying the command line...People may want to explore the command line just because it's in their nature to explore. Some of us are like that. It's not a chore or a negative to us.

@OP

The way I learned was by running a command-line-only minimal install of Ubuntu in a VM inside Ubuntu. Then I would take a snapshot of the pristine system right after install, and break the VM all I wanted, without pain or bother. I could get back to a good system just by reverting to the last known good snapshot. After all these years, it's still how I experiment and explore, and it's as painless as I can make it.

*Bashing-om*'s suggestions are good ones. At the risk of overwhelming you, [here]("https://help.ubuntu.com/community/CommandLineResources") is another link that contains some easy stuff and some advanced stuff. Specifically, I have found [this]("http://linuxcommand.org/tlcl.php") guide to be excellent.

---

### Post by raymond19 on 2014-12-21
This sounds like a very good idea but I have no idea what you mean by ubuntu in VM yet.

---

### Post by raymond19 on 2014-12-21
Wow thanks for the book.

---

### Post by DuckHook on 2014-12-21
> **raymond19 said:**
> This sounds like a very good idea but I have no idea what you mean by ubuntu in VM yet.My bad. Must stop using abbreviations with new users.

VM is a Virtual Machine. It is awesome technology that allows you to run another full operating system inside of a "make-believe" computer that is hosted on your physical computer. Ergo, "virtual" computer, or "Virtual Machine". The one I use is VirtualBox, but there are others. Many advanced users take advantage of this technology to host, say, MSWindows inside their Ubuntu computer. MSWindows then runs within a window on Ubuntu, and can be used for whatever residual MSWindows programs that one might still need. You can install any number of other operating systems in a virtual machine, so long as you don't run them all simultaneously.

Since virtual machines work by creating a second make-believe computer inside your actual computer, they obviously use a lot of resources and cannot run as fast or as efficiently as a real physical machine. After all, you are now running two operating systems plus the overhead of the virtual machine itself. Therefore, the primary drawback of a VM (I'll abbreviate now) is that it needs a goodly amount of horsepower to work effectively for high-resource operating systems like MSWindows. But if you are planning on running just a command-line minimal Linux installation, then the VM does not require a lot of resources. A duo-core machine with min 2GB of RAM should do it. I've run VMs on even less quite effectively.

A further advantage of a VM for learning is that you can have both your command-line VM running in a window, and a browser on your primary operating system open at the same time. This allows you to look things up and execute them on your nicely sandboxed VM.

[Here]("https://help.ubuntu.com/community/VirtualMachines") is a link to a discussion of the VMs available for Ubuntu. There are actually a few more, but stick with the easy ones for now. The two easiest seem to be VMWare and VirtualBox, both of which are free. VirtualBox is available in the Software Centre and can be downloaded easily. There is also a subforum on this site dedicated solely to helping with virtualization.

---

### Post by coldraven on 2014-12-21
DuckHook has the best advice. I would install VirtualBox and then install Ubuntu server as a VM. 
Ubuntu server comes by default with no GUI (Graphical User Interface) it is all command line driven.
VirtualBox has a "Take a snapshot" button which saves the current status of your VM.
You can play away to your hearts content and when you break it just roll it back to the original snapshot. 
You can go through the process of downloading and installing from here:
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

Or you can download ready-made VirtualBox VM imagesfrom here:
[http://virtualboxes.org/images/](http://virtualboxes.org/images/)
When even your snaphot is borked you can start over in seconds by creating yet another VM from the original image.

---

### Post by tgalati4 on 2014-12-21
I find that learning the command line is a continuous process.  Describe something that you want to do.  List out the steps--one-by-one.  Write out a crude BASH script to accomplish it.  Run it and find that it works (or doesn't work).  Then do a web search and see how others have done it.  Then make changes to your script to improve it.

Make it work.
Make it work well.
Make it work elegantly.

You will find there are at least a dozen ways to perform the same thing in the command line.

---

### Post by tgalati4 on 2014-12-21
I find that learning the command line is a continuous process.  Describe something that you want to do.  List out the steps--one-by-one.  Write out a crude BASH script to accomplish it.  Run it and find that it works (or doesn't work).  Then do a web search and see how others have done it.  Then make changes to your script to improve it.

Make it work.
Make it work well.
Make it work elegantly.

You will find there are at least a dozen ways to perform the same thing in the command line.  

Here's an example:  [http://ubuntuforums.org/showthread.php?t=2017284&highlight=rename+mp3+tracks](http://ubuntuforums.org/showthread.php?t=2017284&highlight=rename+mp3+tracks)

Learning the command line is easier when you have a real problem to work with.

---

### Post by Habitual on 2014-12-22
> **tgalati4 said:**
> I find that learning the command line is a continuous process.  Describe something that you want to do.  List out the steps--one-by-one.  Write out a crude BASH script to accomplish it.  Run it and find that it works (or doesn't work).  Then do a web search and see how others have done it. 

And there's plenty of examples!
If the OP wants to, he can check what he's written (or copied) at [http://www.shellcheck.net/](http://www.shellcheck.net/) 

If it hasn't been suggested: [https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

---

### Post by bfmetcalf on 2014-12-23
> **raymond19 said:**
> how flexible do you think those resources are? I intend to go into more advacned linux distros later in the future such as archlinux or slackware.


You say you want to learn the command line to jump into some more advanced distros.  I think that a great way to learn the command line is to just install and use ArchLinux for a while, it will force you to use the command line at least at the beginning.  If you read the [beginners guide]("https://wiki.archlinux.org/index.php/Beginners%27_guide") on their wiki through until you understand (for the most part) what it is telling you to do, then work through installing it with the beginners guide open and you make sure you work to _understand_ all of the commands it is telling you to run as you are doing it, you will learn a lot.  I would say to install a virtual machine such as the guy above told you about and try to install Arch in the virtual machine.  I wouldn't be too afraid of the "advanced distros" like Arch.  They require a lot more command line stuff, but they also have awesome documentation, I got a working install quite quickly with only 2 months of Ubuntu experience in Linux, so it is very possible.

Another good thing that will give you some insight into the commands you are running is the man pages.  if you run ```
man cd
``` it will give you a list of all the options and what they do as well as some usage examples.  Man pages can be kind of cryptic until you are somewhat used to them, but can help a lot in understanding stuff.

---

### Post by Andika_Demas_Riyan on 2014-12-23
thank you for the books... it helps me a lot to learn command line...
I think expert in command line is cool lol

---

