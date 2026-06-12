---
title: "sudo gedit OR gedit"
date: 2009-09-30
forum: Security
---

### Post by millertime on 2009-09-30
Hey Guys

I just got into Linux the other week and have been trying to get not only LAMP but an openSSH server, I have spent a lot of time just playing with the OS and trying to figure out the whole sudo/root admin stuff.

So when I was editing my ssh_config and sshd_config files in normal gedit, I wasn't able to save it due to not being root, okay simple, I just needed to run "sudo gedit /etc/ssh/ssh_config" 

When this opened though, gedit looked different; more colors and different icons. I noticed when I run just "gedit" that I get many errors in regards to
```
/home/mt/.themes/Dust Mac/gtk-2.0/gtkrc:93: 
Murrine Configuration option "style" is not supported and will be ignored.
```Other errors are all in regards to "gtkrc:XX:" XX being different numbers.

Is gedit just not running my theme when I don't use "sudo gedit" or can someone break this down for me why they are so different in looks.

One more thing same effect with the "gksu gedit" command, and what does "gksu" do differently to run the program as a GUI intead of "sudo" and CLI.

Thanks a lot, I really wish I didn't wait this long to go Linux, I feel like I have wasted my brain power on windows, even though it got me my job.

---

### Post by Agent ME on 2009-09-30
sudo and gksu/gksudo are only different in how they ask the user for the password: sudo asks for it on the command line, gksu(do) asks for it in a gui window. You have to use sudo when at a command shell and you have no X. You have to use gksu(do) when you're launching it without a command shell, like in a menu item.

The reason 'sudo gedit' looks different is because it is running as the root account with its settings, not as your user account (that's exactly all sudo does).
If you want to run gedit as your user account and be able to edit a file that needs root permissions, try the sudoedit command. Run
```
EDITOR=gedit
sudoedit /etc/some/file
```
to edit the file. Note that if you're already running a copy of gedit as your user, this won't work because the running copy of gedit will take over the job from the newly spawned gedit (and open the file in a new tab), but sudoedit is watching the newly spawned gedit only.

I recommend using 'nano' as the editor so you don't run into this case. It's an easy to use command line text editor. Ctrl-o followed by enter saves the file, and Ctrl-x exits.
```
EDITOR=nano; sudoedit /etc/some/file
```

---

### Post by kevdog on 2009-10-01
All of those gedit errors have to do with your theme and are simply cosmetic.  They really won't effect the file you are trying to edit and save.

The command should be BTW:

gksu gedit <filename>

---

### Post by __p1n__ on 2009-10-01
Just use vi instead.  It looks the same regardless of user acl.

---

### Post by millertime on 2009-10-01
I was using the command (from terminal)

```
sudo gedit /some/file/name
```it opened gedit fine with full permissions.

But to clarify when running the same command from "Run Application" i should be using gksu like:

```
gksu gedit /some/file/name
```-------------------

I did not know that we had nano edit on Linux, I am used to it on mac, unless I just saw it in linux and thought it was a MAC at work cause of my theme, I easily mix stuff up considering I do tech support for MAC, Linux and All Windows (including servers and home servers). I even will try to use a linux command on windows cause I forget what OS its from.

I tried typing 

```
EDITOR=gedit
sudoedit /some/file/name
```and

```
EDITOR=gedit; sudoedit /some/file/name
```This just opened up nano, I am assuming that kevdog is right when he says to use

```
gksu gedit /some/file/name OR sudo gedit /some/file/name
```in order to open up gedit correctly.

-------------------------

And I broke a server at work trying to use the VI editor to edit the Hostname file using putty on SSH, I was probably doing this wrong as I think I just tried finding the hostname file in etc and than

```
sudo vi hostname
```after changing it I was kicked out of putty (this wasnt expected as I was connected via IP NOT hostname) And at that point had no way into my server which is actually a strict network NAS only accessed by putty or HP software, its a HP Media Vault Generation One running on a Linux Port either a Reiser or EXT3 filesystem with no monitor capabilites. I did a NASLoad (reload of the NAS OS) and at that point it worked, obviously.

Since then I have been scared of VI, I might stick with Nano as its pretty nice user friendly.

Thanks alot guys, I knew I would find help fast here!

---

### Post by kevdog on 2009-10-01
Never heard of the sudo vi filename error -- buts thats scary.

Possibly next time you should do a 
sudo su

Which will put you in a root prompt, and then just run vi from there.

sudo is technically for non-graphical apps
gksu is for graphical apps that use the gnome-toolkit that run as root
kdesu is for graphical apps that use the qt-toolkit that run as root

Since gedit (g=gnome edit=editor) is a gnome or gtk toolkit app, is you want to run it as root, you should technically start it with
gksu gedit <filename>

This point has been discussed for ages -- hoping to educate new users to this concept -- its not that hard!

---

### Post by Chronon on 2009-10-01
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by millertime on 2009-10-01
so when i type the 

```
gksu gedit /some/file/name
```I get the errors that I get when typing just "gedit" in terminal in regards to the themes, BUT they do all load without any problems. Where as when I just type "sudo gedit" it opens without a single error.

I understand the different uses for them but should I always run

gksu - from terminal and run application if its going to be a GUI application

and 

sudo - from terminal only if it is something like nano or vi and non GUI based application.

They seem to work interchangeably without problems other than these incorrect theme errors.

Is this just correct habit, if so I will continue to use "gksu" for GUI and "sudo" for non-GUI, I just don't get why when they seem to work interchangeably.

EDIT: I just started reading the Link provided and its giving me a complete insight as to why to use "gksu"

Thanks a ton guys for helping me understand this, I feel like I actually understand the whole root / user thing and now the whole gksu/sudo thing.

Terminal is really a beautiful thing if I do say so myself.

---

