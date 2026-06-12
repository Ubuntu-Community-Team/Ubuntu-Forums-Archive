---
title: "So is there any exe equivalent in Linux?"
date: 2009-03-14
forum: The Cafe
---

### Post by jaguax on 2009-03-14
I've only been using it for two days now, but it seems like you gotta jump through hoops to install stuff in Linux, utilizing the terminal and going through tricky steps depending on what you need to install.

Video drivers for instance. In Windows you just double click the EXE file and bam it's done. In Linux I had to download a *.run file, exit the GUI with CTRL ALT F1, log in as root, input a command to stop the x server, input a command to open the driver file, and finally got to the install screen. Then I had to input a command to start the x server again, and another command to get back to the GUI. That's a lot, heh.

I mean it's kind of cool that it's lower level and you get to understand the workings of the OS more, but it's a nightmare in terms of user friendliness.

Are there even standard executable files in Linux? The type of program that you just double click and it automatically installs like Windows?

---

### Post by gandaran on 2009-03-14
yes, .deb packages you just double click them to install, you can get some of these packages [here]("http://www.getdeb.net/")

---

### Post by Moop on 2009-03-14
Use Synaptic Package Manager or Applications-Add/Remove to search for and install applications. One click and there's no command line involved.

---

### Post by sisco311 on 2009-03-14
Installing applications in Ubuntu is easy. You can use [Add/Remove]("https://help.ubuntu.com/community/InstallingSoftware") or [Synaptic Package Manager]("https://help.ubuntu.com/community/SynapticHowto") to search for and install applications. 

What kind of video card you have?

Try to enable the driver for your card in  System->Administration->Hardware Drivers.

---

### Post by humphreybc on 2009-03-14
Video cards can be a bitch, yes, but I must admit for installing regular applications, the Add/Remove system works like a charm. And .deb packages aren't so bad either :)

You'll be thanking Mr Ubuntu for not incorporating .exe support because most viruses are .exes!

---

### Post by LouisZepher on 2009-03-14
> In Linux I had to download a *.run file, exit the GUI with CTRL ALT F1, log in as root, input a command to stop the x server, input a command to open the driver file, and finally got to the install screen. Then I had to input a command to start the x server again, and another command to get back to the GUI. That's a lot, heh.

You don't really need to stop X to use the command line.  (If you're running Gnome, which, if you've only been using Ubuntu for a few days, I'll assume you are.) Go to Applications>Accessories>Terminal (or, by default, you can use ALT+F1), and you'll get a windowed shell; this is almost exactly like a DOS window in old-school Win9x.  Then, when you want to use an Admin command, simply type:

```

sudo COMMAND

```

Replace COMMAND with whatever you're trying to do, you'll be prompted for your password, type it (there will be no visual output like the normal asterisks) and hit Enter.

For example:
```

sudo apt-get install PACKAGE

```
(Where PACKAGE is the name of the software you wish to install.)

The above will execute apt-get (the default Package Manager for Ubuntu), then download and install PACKAGE.

The Terminal is your friend, and, unless you need to do some really funky stuff, can be avoided for most tasks.  There are dozens of different terminal programs you can use.  I, personally, use Tilda (sudo apt-get tilda).  With Tilda, you can have it run silently in the background (very small memory footprint), and when you need to use a terminal, hit the configurable hotkey, and presto, it open much like a chat window on most online games.

If you're still afraid of the command line for installing packages, you can simply use the Add/Get package manager found under Applications on the Gnome Menu.  There's not nearly as many packages available as there would be via apt-get, but there's enough variety to the types of applications that the regular user can use to "survive" until they find something they like better.


Now, take a deep breath, and enjoy the learning experience of switching OSes.  Even if you decide to go back to your previous OS, there's pride to be found in making the attempt to learn something new.  Change is good, even if only for the act of changing.

---

### Post by mrsteveman1 on 2009-03-14
The old nvidia binary package DID require you to stop X to install it. That shouldn't be necessary anymore, Ubuntu should grab it for you and install it.

There are .exes for Linux, they are self extracting binary archives that run a shell script to install whatever they are installing, usually they have the extension .run or .bin. Those tend to be simple shell scripts for a terminal, but some of them have GUIs, for instance the package you get from truecrypt.org is a binary that brings up the license in a GUI window, when you accept it you get a choice to install or extract a .deb file. 

There are, conversely, package systems for Windows, Microsoft has that MSI thing they keep updating which isn't bad. Anything that gets us away from executing arbitrary code to install something is a good thing, and by default Linux distros stay away from doing that.

---

### Post by ad_267 on 2009-03-14
[Installing software in Ubuntu]("http://www.psychocats.net/ubuntu/installingsoftware")

---

### Post by mikewhatever on 2009-03-14
> **jaguax said:**
> 
Video drivers for instance. In Windows you just double click the EXE file and bam it's done. In Linux I had to download a *.run file, exit the GUI with CTRL ALT F1, log in as root, input a command to stop the x server, input a command to open the driver file, and finally got to the install screen. Then I had to input a command to start the x server again, and another command to get back to the GUI. That's a lot, heh.


You can always go the hard way, sometimes even need to, for example if using Ubuntu 6.06. In my case, all I had to do was a few clicks in System->Admin->Hardware Drivers.

---

### Post by sisco311 on 2009-03-14
If you are new to Ubuntu, then I would suggest to read [this]("http://psychocats.net/ubuntu/index.php") tutorials and
the [community documentations]("https://help.ubuntu.com/community/").

The Linux CLI is very powerful and if you are not afraid of it, you will find it useful, 
but Ubuntu comes with an easy to use GUI. Of course, you need a little time to learn how it works.

Enjoy your new OS and if you need help, feel free to ask for it.
We will be glad to help you. :)

---

### Post by jaguax on 2009-03-14
> **LouisZepher said:**
> 
Now, take a deep breath, and enjoy the learning experience of switching OSes.  Even if you decide to go back to your previous OS, there's pride to be found in making the attempt to learn something new.  Change is good, even if only for the act of changing.

Oh I definitely like it, it's just a big change coming from Windows where everything is done for you.

Actually the reason I'm trying it out is because I went to a job fair recently for a software engineering position and they asked me if I had any Linux experience. Unfortunately I had to say no, but I was recommended to download it and tinker around with it since that is what they use in the company. But I'm not too sure what exactly I should be "tinkering" with. I'm guessing I should be learning the basic command line stuff, perhaps installing C++ and writing a few small programs, compiling them and whatnot? What's good for that? Dev-C++?

---

### Post by sisco311 on 2009-03-14
> **jaguax said:**
> Oh I definitely like it, it's just a big change coming from Windows where everything is done for you.

Actually the reason I'm trying it out is because I went to a job fair recently for a software engineering position and they asked me if I had any Linux experience. Unfortunately I had to say no, but I was recommended to download it and tinker around with it since that is what they use in the company. But I'm not too sure what exactly I should be "tinkering" with. I'm guessing I should be learning the basic command line stuff, perhaps installing C++ and writing a few small programs, compiling them and whatnot? What's good for that? Dev-C++?

The Community Documentation is a good starting point:
[uhelp]community/UsingTheTerminal[/uhelp]

and read the Stickies in the Programming Talk sub-forum.

---

### Post by mikewhatever on 2009-03-14
> **jaguax said:**
> Oh I definitely like it, it's just a big change coming from Windows where everything is done for you.


In that case, can you tell me why does Windows on my laptop ignores the fact that the mic in Skype hasn't been working since veersion 2.5-something? Windows should have taken care of that right? However not even editing Skype's config files as per forum suggestions worked. :lolflag:
It so cracks me up when someone says 'Windows just works' etc.

---

### Post by ad_267 on 2009-03-14
> **jaguax said:**
> I'm guessing I should be learning the basic command line stuff, perhaps installing C++ and writing a few small programs, compiling them and whatnot? What's good for that? Dev-C++?

If you want to learn how to program in Linux I'd recommend staying away from an IDE at first, although there are many available (Anjuta, Code::Blocks, Eclipse, NetBeans, KDevelop, Qt Creator), and try things the command line way.

Learn how to use gcc and g++ for compiling and how to use makefiles. You can use the man command to find out how to use different programs, eg "man gcc". The man pages can be confusing at first until you get used to reading them. You'll need to install the "build-essential" package first and that should give you everything you need for compiling simple C and C++ applications. You can get a plugin for the default text editor Gedit that gives you a terminal in the bottom pane which I find useful.

---

### Post by sgosnell on 2009-03-14
The most important thing to do is just [b]use it[/].  That's how you learn an OS, by using it every day, for everything.  You didn't learn all you know about Windows in a day, or a week, and you won't learn everything about Linux in a day or a week, but it won't take that long to be reasonably proficient.  Different distros have different ways of doing things, and Linux is not one OS, although the kernel is the same.  The desktops, the look and feel, the default programs, are all different in different distros.  You won't use apt-get in Fedora, for example, or in openSUSE.  There are equivalents, but they're not the same.  Be prepared to relearn lots of things if you switch from Ubuntu to something else.  But once you learn the basics of Linux, it's easier to learn another distro.

---

