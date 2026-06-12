---
title: "Start Windows 7 Vmware on workplace 2"
date: 2011-06-12
forum: Virtualisation
---

### Post by andy123456 on 2011-06-12
Hello I have recently install windows 7 on vmware player. Could somebody help me out in making windows 7 boot up with my ubuntu 11.04. And could it then start up in workspace 2 in fullscreen mode. Also I have compiz installed so I tried using the place window function to start windows 7 on workspace 2 and I tried using start up application but I do not know what command to give so not just vmware starts up but windows 7. Any help appreciated!

---

### Post by GWBouge on 2011-06-13
You could try using [wmctrl]("http://tomas.styblo.name/wmctrl/").  It's available in the repo's.

VMWare would have to be launched before wmctrl can do anything with it, so you would have to set up a small script to launch it, wait a second or two, then move it.

---

### Post by andy123456 on 2011-06-13
Thank you GWBouge for replying! 
I am somewhat new to ubuntu and I don't know how to use wmctrl. I just installed it but I do not know how to use it. Also if this helps here is a thread I have found before I started this thread but in the thread the other person talks about how to open virtualbox on workspace 2. I tried to do what he did but it didn't work. Anyways here is the thread      [http://ubuntuforums.org/archive/index.php/t-685528.html](http://ubuntuforums.org/archive/index.php/t-685528.html)
Also I guess I could start vmware on workspace 2 using the place window plugin in compiz but I can't get it to work I guess I am doing something wrong being a noob...

---

### Post by GWBouge on 2011-06-13
Well, I just tried Place Windows again to make sure, and yeah, it does seem kindof buggy.  Seems to not like to remember where to put a window when you add it from a different workspace, whether or not you have 'Keep in Workarea' checked.  =o\

Ok, here's what I figured out to get wmctrl to do what I think you're asking:  Go ahead and start up your VM on your main workspace, and open up a terminal.  Do this in the terminal:

```
$ wmctrl -l
<snip>
0x05c00122  0 bummer-PC **VirtualBox OSE Manager**
```

You'll get back a list of currently open windows.  What you need is the text name of the window.  Now, find out how to refer to the Workspaces:

```
$ wmctrl -d
0  * DG: 6400x2160  VP: **0,0**  WA: 0,24 3200x1056  Workspace 1

```

This will show you the information about the current workspace.  Move the terminal to the workspace you want to move the VM and do it again:

```
$ wmctrl -d
0  * DG: 6400x2160  VP: **3200,0**  WA: 0,24 3200x1056  Workspace 1
```

Note the part that changed.  That's the top-left corner of the current workspace.  Now, if I wanted to move my VirtualBox window to that workspace and make it full screen, I would do this, where 1280x1024 is the resolution of the monitor:

```
$ wmctrl -r 'VirtualBox OSE Manager' -e 0,3200,0,1280,1024
```

Here's the relevant parts of the syntax from the help output:

```
-r <WIN> -e <MVARG>  Resize and move the window around the desktop.
                       The format of the <MVARG> argument is described below.

<MVARG>              Specifies a change to the position and size
                       of the window. The format of the argument is:

                       <G>,<X>,<Y>,<W>,<H>

                       <G>: Gravity specified as a number. The numbers are
                          defined in the EWMH specification. The value of
                          zero is particularly useful, it means "use the
                          default gravity of the window".
                       <X>,<Y>: Coordinates of new position of the window.
                       <W>,<H>: New width and height of the window.

                       The value of -1 may appear in place of
                       any of the <X>, <Y>, <W> and <H> properties
                       to left the property unchanged.

```

---

### Post by andy123456 on 2011-06-14
Sorry that I wasn't to clear in the second post. I am running vmware not virtualbox but I found a thread that sais how to move virtual machine to workspace 2 when having virtualbox. I use vmware player to be exact, I guess what you wrote will not work since you wrote the things for virtualbox. Also I used the place window function and it worked it just didn't start the virtual machine within vmware just vmware itself on workspace 2. Maybe using start up applications I could make the virtual machine start up..just a thought. What do you think should we rather stick with wmctrl?
Thanks!

---

### Post by GWBouge on 2011-06-14
Yeah, I wasn't giving you an exact command, I was describing how to find out what command *you* need to do what you want.  I can't give you a copy/paste solution, because I simply don't know what the window you want to move is called or your workspace resolutions.

And yes, you should be able to use a startup command to start the VM, but you will need to look up some of VMWare's command line solutions to do so (the VirtualBox way would be something like 'VBoxManage startvm MyVirtualMachine', but you should be able to do some searches for VMWare's tools).  You'll also need something else to move it as you desire, hence my suggestion to have Startup Applications call a small bash script that can both start the VM, and move it.

---

