---
title: "Challenge: what can you *not* do with the GUI"
date: 2010-05-01
forum: The Cafe
---

### Post by P4man on 2010-05-01
New users commonly complain about requiring a command line, because they dont realize its much easier for helpers to give CLI commands than describe a GUI approach (for every desktop environment) and we get results the new user can copy/paste to the forum, rather than a vague description of a "window with an arrow and a red cross and two buttons".

[COLOR="DarkRed"]Anyway, Im curious what common tasks (that you might reasonably expect your or my mother in law to need) you can come up with that can not be achieved without resorting to the CLI. [/COLOR]

Im not looking for hardcore geek stuff, but tasks that typical desktop users coming over from windows or mac might want or need.

Rules: its allowed to install programs from the official repositories to complete the task.  

Lets hear it!

**Suggested and accepted common CLI only tasks:**

- Launch a directory specific, fullscreen, timed slideshow of family photos, at a predefined time of day,remotely, to a netbook with a broken keyboard, but (obviously) working display, that sits on my coffetable.

**Suggested and rejected:**

-mac address spoofing. I will accept this if anyone can point me to a single mother in law that spoofs mac addresses on a regular basis.
-configuring sound cards (can arugably be done through gui, configuring hw is not a common task, you only do it once)
-compiling (as it turns out, mothers in law  do compile from source, but they can do so with IDE's like eclipse.)

---

### Post by jkxx on 2010-05-01
Making sound play out of more than the 2 front outs of my sound card. I had to edit /etc/pulse/daemon.conf and set the channels to 6 before that would work. As far as I know there is no way to do this from the GUI even though after editing the above file pavucontrol can be used to control all the volumes and outputs for PulseAudio.

---

### Post by Eisenwinter on 2010-05-01
I can do everything with CLI except look at pictures (I can play videos in ASCII using mplayer).

---

### Post by red_Marvin on 2010-05-01
It is the common tasks that can be put into a gui, the ones that are done the same way every time. Cli really shines for the detailed, specific cases where all options need to be available at the drop of a hat.

However anything where you want to feed the output of one program to the input of another without having to manually copy and paste, possibly reformatting each line manually the cli with pipes, sed, awk and in the tricky cases perl, is essential.

---

### Post by P4man on 2010-05-01
> **jkxx said:**
> Making sound play out of more than the 2 front outs of my sound card. I had to edit /etc/pulse/daemon.conf and set the channels to 6 before that would work. As far as I know there is no way to do this from the GUI even though after editing the above file pavucontrol can be used to control all the volumes and outputs for PulseAudio.

Configuring your pc is not a common task, you should only do it once. Even so, you can do it with a gui. Install nautilus-gksu (using synaptic, obviously :) ) , browse to the file, right click, open as administrator. 

granted, editing config files is not very graphical, but its not a cli either.

---

### Post by DeadSuperHero on 2010-05-01
Compiling using GCC or LLVM. Building things from source requires the CLI, and thank god for that.

I tend to love using the CLI for file navigation, package management, system configuration, even surfing the web occasionally. I tend to find the GUI alternatives to be somewhat cluttered and annoying.

---

### Post by P4man on 2010-05-01
> **DeadSuperHero said:**
> Compiling using GCC or LLVM. Building things from source requires the CLI, and thank god for that.


You sure you cant do that with something like eclipse? Regardless, it doesnt meet my mother-in-law benchmark :)

---

### Post by Yes on 2010-05-01
Compile and upload AVR programs.

Other than that it's not a matter of not being able to do something from a GUI, it's just that it's easier or faster to do from the CLI.

---

### Post by grief -l on 2010-05-01
The biggest problem a new user faces is hardware compatibility - drivers, firmware - and none of that can be done with the GUI. The "Hardware Drivers" gizmo in System > Admin only works if there's already a driver available, but it can't make && make install, modprobe, blacklist or any such tasks. You also can't get info in the GUI like with ifconfig, iwconfig etc and there is absolutely no way to configure say a wireless dongle or pci card through the GUI.

Of course, once a newbie has got his hardware up and running there's no longer any need to mess with it so GUI/CLI is moot.... until the next update loads a new kernel and the cussing starts all over again.

---

### Post by Bachstelze on 2010-05-01
> **Eisenwinter said:**
> I can do everything with CLI except look at pictures (I can play videos in ASCII using mplayer).

Have a look at svgalib or directfb. ASCII videos are bad for you. ;)

---

### Post by Kingsley on 2010-05-01
I can't spoof my mac address with GUI. There's probably a way to do so but I don't know it.

---

### Post by P4man on 2010-05-01
And mac address spoofing is something you can imagine my or your mother in law doing?

---

### Post by jkxx on 2010-05-01
The reason I posted the bit about PulseAudio is that it's a common thing that people would want to use all channels on their sound card - though I guess strictly defined it's not so common.

I was going to post another related PulseAudio one though it's not CLI-only and most can agree PA is just a pain regardless of how it has to be configured.

As for ASCII videos, vlc-nox can do that too ;)

I'll have to admit that the aforementioned PA file edit is the only strictly CLI task I've had to do since getting the latest Kubuntu (10.04). I literally have not run into a single other task requiring a trip to the terminal since installing, and kudos to the devs for that.

---

### Post by Yes on 2010-05-01
Why are you so obsessed with what my mother in law does?

You asked us what common tasks we do that we can't use the GUI for, and I'm sure a lot of stuff that has been listed like spoofing a mac address is common to that user.

If you asked "what common task does your mother in law do that she can't do from a GUI" I'd probably say nothing.  Is that the answer you're looking for?

---

### Post by P4man on 2010-05-01
> **Yes said:**
> Why are you so obsessed with what my mother in law does?

You asked us what common tasks we do that we can't use the GUI for, and I'm sure a lot of stuff that has been listed like spoofing a mac address is common to that user.

If you asked "what common task does your mother in law do that she can't do from a GUI" I'd probably say nothing.  Is that the answer you're looking for?

Mother in law is just a metaphore of course (that i mentioned in my original post), but I rephrased it a bit now.

---

### Post by nothingspecial on 2010-05-01
Launch a directory specific, fullscreen, timed slideshow of family photos, at a predefined time of day,remotely, to a netbook, with a broken keyboard, but (obviously) working display, that sits on my coffetable.

Mother in laws like photos on their coffee tables ;)

---

### Post by P4man on 2010-05-01
> **nothingspecial said:**
> Launch a directory specific, fullscreen, timed slideshow of family photos, at a predefined time of day,remotely, to a netbook, with a broken keyboard, but (obviously) working display, that sits on my coffetable.

Mother in laws like photos on their coffee tables ;)

I think we got our first entry. Unless someone comes up with a gui approach to solved that lol!

---

### Post by ibuclaw on 2010-05-01
What can you not do with GUI? To the best of my knowledge, you cannot grow or shrink an image file.


If you don't know what one is, here is the jist of creating one.
```

touch data.img
dd if=/dev/zero of=data.img bs=1 count=1 seek=10G
mkfs.ext4 data.img

```
Now, mounting is pretty much like a filesystem, with the exception of the -o loop argument.
```

sudo mount -o loop data.img /mnt
df -h

```
As for managing the image size (back to my original point), in CLI, you would use **truncate** to shrink the image and **fallocate** (or truncate again if you want it sparse) to extend it.

Regards

---

### Post by jrothwell97 on 2010-05-01
I think a better question would be "what can you not do using only well-designed, idiot-proof GUIs."

There are plenty of GUI solutions to things, but more often than not they're rather slapdash solutions or they're so out of date they make .NET look like a recent development in the world of technology.

---

### Post by mkendall on 2010-05-01
Create hard links and symbolic links.

---

### Post by ibuclaw on 2010-05-01
> **mkendall said:**
> Create hard links and symbolic links.

You can create symbolic links to items in Gnome and KDE.

---

### Post by mkendall on 2010-05-01
> **ibuclaw said:**
> You can create symbolic links to items in Gnome and KDE.

Then I modify my statement to "create hard links."

---

### Post by oldos2er on 2010-05-01
Mother-in-law != ignorant and/or inexperienced. I have done and continue to do a fair amount of compiling on Ubuntu. I've done no MAC address spoofing, but if a situation arose where I was compelled to, I would do that too.

---

### Post by P4man on 2010-05-01
> **oldos2er said:**
> Mother-in-law != ignorant and/or inexperienced. I have done and continue to do a fair amount of compiling on Ubuntu. I've done no MAC address spoofing, but if a situation arose where I was compelled to, I would do that too.

Point taken. But since compiling doesnt necessitate a CLI if you have an IDE (unless im wrong there), Im still rejecting this entry. Ill update the motivation though :)

---

### Post by swoll1980 on 2010-05-01
Delete system files :P

---

### Post by swoll1980 on 2010-05-01
> **P4man said:**
> Point taken. But since compiling doesnt necessitate a CLI if you have an IDE (unless im wrong there), Im still rejecting this entry. Ill update the motivation though :)
Why not change mother in law  to computer illiterate so people will stop trying to do that.

---

### Post by oldos2er on 2010-05-01
> **P4man said:**
> Point taken. But since compiling doesnt necessitate a CLI if you have an IDE (unless im wrong there), Im still rejecting this entry. Ill update the motivation though :)

I've only compiled using CLI.

---

### Post by P4man on 2010-05-01
> **swoll1980 said:**
> Why not change mother in law  to computer illiterate so people will stop trying to do that.

Because I cant type that without making 3 spelling errors in one word. And because I think computer illiterate is too narrow. I do mean people who are quite capable of using their PCs, just not the geeks that like to peek under the hood.

Anyway, dont mean to offend anyone, its just tongue in cheek. Im not exactly a sexist, but I do have prejudice against mothers in law :)

---

### Post by DeadSuperHero on 2010-05-01
> **oldos2er said:**
> I've only compiled using CLI.

It's more comfortable that way, too.

---

### Post by P4man on 2010-05-01
> **oldos2er said:**
> I've only compiled using CLI.

Probably, but thats not the point here. You dont *have* to do it with cli. I cant remember the last time I installed something using synaptic, doesnt mean you need to use aptitude  in a cli.

---

### Post by chris200x9 on 2010-05-01
> **P4man said:**
> I think we got our first entry. Unless someone comes up with a gui approach to solved that lol!

All these rejections and this makes it?! Mother in law would buy a new netbook!

---

### Post by P4man on 2010-05-01
> **chris200x9 said:**
> All these rejections and this makes it?! Mother in law would buy a new netbook!

I actually think you can do it with a gui. remote desktop would work fine, setting up a screensaver showing those pics might work. But it was too funny to reject :)

---

### Post by ibuclaw on 2010-05-01
Actually, to be pedantic. Any terminal application that runs in X is a GUI application.

With that in mind, there is nothing you can't do in GUI that you can do in CLI - given that you have a VTE installed (ie: Gnome-Terminal, Konsole, Sakura, XTerm, Terminator, etc). :)

---

### Post by Irihapeti on 2010-05-01
Hey! I **AM** a mother-in-law! So, do you want to know what I use the CLI for?

Maybe, though, I'm just a geek who happens to be a mother-in-law, and that doesn't count.

---

### Post by samigina on 2010-05-01
sudo iwlist wlan0 scan

Theres no GUI option for scan wireless network when I want.

---

### Post by ibuclaw on 2010-05-01
> **samigina said:**
> sudo iwlist wlan0 scan

Theres no GUI option for scan wireless network when I want.

Left Click on the Network Manager Applet - though it updates once every period (20-30 seconds~) not immediately as you request it.

---

### Post by red_Marvin on 2010-05-01
Ibuclaw: a terminal however, gives the option of sorting and filtering the list by aribtrary parameters.

---

### Post by nothingspecial on 2010-05-02
> **chris200x9 said:**
> All these rejections and this makes it?! Mother in law would buy a new netbook!

It`s my £5 digital photo frame. I picked it up at a car boot sale :)

I mount my photo collection, that is backed up on my sever under the stairs with sshfs, then use feh combined with a cron job to use it as a slideshow of photos in the evening, that turns itself off at midnight.

It`s not geekyness it`s being a cheapskate :P

I also have an 'other way round' net book, the screen is broken but the keyboard works. I use that to watch the BBC iPlayer in bed using an external monitor ---- all through the gui.

Old and broken computers can be useful.

---

### Post by Bodsda on 2010-05-02
[COLOR=darkred][/COLOR]
Use your computer efficiently or quickly.
 
£10 to the first person who can shut there computer down (cleanly) with the mouse before I can type 's' (My shutdown alias)
 
Bodsda

---

### Post by P4man on 2010-05-02
> **Bodsda said:**
> [QUOTE=P4man;9211565] 
[COLOR=darkred]Anyway, Im curious what common tasks (that you might reasonably expect your or my mother in law to need) you can come up with that can not be achieved without resorting to the CLI. [/[/COLOR]QUOTE]
 
Use your computer efficiently or quickly.
 
£10 to the first person who can shut there computer down (cleanly) with the mouse before I can type 's' (My shutdown alias)
 
Bodsda

£10  is mine! I press the power button it shuts down cleanly. well ok; its not a mouse but I could map it to a mouse button just as well

---

### Post by Bodsda on 2010-05-02
> **P4man said:**
> 
 
£10 is mine! I press the power button it shuts down cleanly. well ok; its not a mouse but I could map it to a mouse button just as well
 
You honsetly think you can move your hand down to the power button away from your hands normal resting position quicker then i can press two keys which are millimteres away from my hands resting position? 
 
Bodsda

---

### Post by P4man on 2010-05-02
> **Bodsda said:**
> You honsetly think you can move your hand down to the power button away from your hands normal resting position quicker then i can press two keys which are millimteres away from my hands resting position? 
 
Bodsda

If I map that to one of two dozen mouse buttons, then yes. [My finger, is on the button.]("http://www.youtube.com/watch?v=Ldaj7eMtHjk")  you have to press 2 keys (enter too) You have paypal?
;)

---

### Post by ibuclaw on 2010-05-02
I can clap my hands, then all power will turn itself off. :)

Also, Bodsda, you are forgetting that there is much more to it than just pressing 's' and Enter.

You need to grab the mouse, move to "Applications", Left click, then "Accessories", Left click, then "Terminal", Left Click.
Move your hand off the mouse, waiting 1-2 seconds for all bash runtime scripts to load, then press 's' and Enter on the keyboard.

btw, what does the alias command run? If it is 'sudo shutdown -h now' then you will also need to enter in your user password.

Though, IMO, if it is 'sudo shutdown -h now', you are not exactly the smartest person, as there are ways of shutting down without the need to use sudo. ;)

---

### Post by chappajar on 2010-05-02
I can't force mount/unmount a flash drive or external hard disk that has previously been removed without first being umounted.  
I have to use the CLI (which is fine, but I'd love to put an icon in a panel somewhere that does it for people scared of CLI)

---

### Post by Bodsda on 2010-05-02
> **ibuclaw said:**
> I can clap my hands, then all power will turn itself off. :)
 
Also, Bodsda, you are forgetting that there is much more to it than just pressing 's' and Enter.
 
You need to grab the mouse, move to "Applications", Left click, then "Accessories", Left click, then "Terminal", Left Click.
Move your hand off the mouse, waiting 1-2 seconds for all bash runtime scripts to load, then press 's' and Enter on the keyboard.
 
btw, what does the alias command run? If it is 'sudo shutdown -h now' then you will also need to enter in your user password.
 
Though, IMO, if it is 'sudo shutdown -h now', you are not exactly the smartest person, as there are ways of shutting down without the need to use sudo. ;)
 
I'm in tty1 so no need to open the terminal.
And no, I'm not using sudo
 
Bodsda

---

### Post by ibuclaw on 2010-05-02
> **Bodsda said:**
> I'm in tty1 so no need to open the terminal.
And no, I'm not using sudo
 
Bodsda

OK, so you are using dbus-send then?

If so, I'm pretty certain I taught you that, or you may have come across it in a link I posted in IRC. :)


PS: You are in tty1, you still need to login first. ;)

---

### Post by Bodsda on 2010-05-02
> **ibuclaw said:**
> OK, so you are using dbus-send then?

If so, I'm pretty certain I taught you that, or you may have come across it in a link I posted in IRC. :)


PS: You are in tty1, you still need to login first. ;)

I am already logged in

And yeah, I think it was you I picked that up from :)

Bodsda

---

### Post by chappajar on 2010-05-02
> **P4man said:**
> If I map that to one of two dozen mouse buttons, then yes. [My finger, is on the button.]("http://www.youtube.com/watch?v=Ldaj7eMtHjk")  you have to press 2 keys (enter too) You have paypal?
;)

You did do that remapping through the GUI only, didn't you?

What is the official count now?

---

### Post by P4man on 2010-05-02
> **chappajar said:**
> You did do that remapping through the GUI only, didn't you?

Im sure I could, using BTNX or compiz. Im not entirely sure what command I would have to send though, at worst I might have to  install xdotool (of course using synaptic package manager).

But even so, that wasnt Bodsda's challenge " £10 to the first person who can shut there computer down (cleanly) with the mouse before I can type 's' "

Im pretty sure I could shut it down faster clicking a single mouse button than him having to enter at least 2 keystrokes. Especially if he is busy in vim :p

---

### Post by sisco311 on 2010-05-02
Since everything is a file, in theory, one can accomplish any task with a GUI text & hex editor. :)


Currently we do not have GUI configuration tools for policykit and Upstart.

---

### Post by chappajar on 2010-05-02
> **chappajar said:**
> I can't force mount/unmount a flash drive or external hard disk that has previously been removed without first being umounted.  
I have to use the CLI (which is fine, but I'd love to put an icon in a panel somewhere that does it for people scared of CLI)

I should add that this passes the so called ''mother-in-law'' test (IMHO) because all she needs to do to be in a situation where she needs to do this is to pull out her flash drive without umounting it first.
Easy, common, even likely...

---

### Post by P4man on 2010-05-02
> **sisco311 said:**
> Since everything is a file, in theory, one can accomplish any task with a GUI text & hex editor. :)


You can not configure policykit or Upstart via a GUI configuration tool.

yes you can afaik. Install "authorizations"(policykit-gnome) or lockdown editor. As for upstart, it depends what you want to do, but the mother-in-law tasks Id say you certainly can.

You do have a point with the hex editor altough I would could that as a GUI. you might as well call gnome-terminal a GUI.

---

### Post by P4man on 2010-05-02
> **chappajar said:**
> I should add that this passes the so called ''mother-in-law'' test (IMHO) because all she needs to do to be in a situation where she needs to do this is to pull out her flash drive without umounting it first.
Easy, common, even likely...

But are you sure you cant do it with a GUI? Using disk-utility, mountmanager or other?

---

### Post by chappajar on 2010-05-02
> **P4man said:**
> But are you sure you cant do it with a GUI? Using disk-utility, mountmanager or other?

Force mount? Not as far as I know...

Anyway, I can't even recreate the problem to check, so maybe this has been fixed??? :p

It was certainly a problem in 8.10 and 9.04 when I was installing Ubuntu on ''mother-in-laws'' computers, but perhaps it's no longer an issue....?

---

### Post by clanky on 2010-05-02
OK, I haven't read the whole thread so I don't know if this has already been mentioned, but there are specific tools such as firmware cutters etc. which are CLI only.  

Although these aren't day to day tasks they are tasks which many people need to do in order to get there hardware working and they can be a bit daunting for a new user.

The other point to be made is that new users being forced to use a command line occasionally is not necessarily a bad thing, although it can be daunting, if the results come out right at the end then it can also feel quite reqarding especially if the instructions given are clearly explained so that people actually understand what they are doing rather than blindly copying and pasting random code into a terminal.

---

### Post by agnes on 2010-05-02
Automatically, scheduled, update her website via ftp.
Perhaps viewed as too geeky, but I can imagine some mother-in-laws having a (simple) website with family pics and stories and such, and having new stories & pics regularly, therefore wanting to automate the uploading.

---

### Post by clanky on 2010-05-02
> **Bodsda said:**
> You honsetly think you can move your hand down to the power button away from your hands normal resting position quicker then i can press two keys which are millimteres away from my hands resting position? 
 
Bodsda

The possibility of being able to shutdown the computer by *accidentally* pressing two keys which are just millimeters away from each other should be enough to convince you that this is a really bad idea.

And unless you don't want your mother / wife / girlfriend to catch you watching po, ermmm educational material, why on earth would you want the ability to shutdown your computer in a nanosecond?

---

### Post by swoll1980 on 2010-05-02
> **Bodsda said:**
> 
Use your computer efficiently or quickly.
 
£10 to the first person who can shut there computer down (cleanly) with the mouse before I can type 's' (My shutdown alias)
 
Bodsda

Couldn't I make a script and put an icon on the desktop that just had to be clicked to shut down?

---

### Post by red_Marvin on 2010-05-02
> **sisco311 said:**
> Since everything is a file, in theory, one can accomplish any task with a GUI text & hex editor. :)


Currently we do not have GUI configuration tools for policykit and Upstart.

But then you are not using the gui properties of the text editor, not *really*.

---

### Post by nothingspecial on 2010-05-05
Lock the "family pc" remotely.

My kids have spent far too long playing stupid flash games on the main box - I issue this, from my laptop.
```

ssh -X me@192.168.1.2 \"export DISPLAY=:0; gnome-screensaver; gnome-screensaver-command -l;\"
```

obviously this is mapped to an alias "lock", so all I do is type "lock" and then my password for the main pc.

Same goes for unlocking -
```

ssh -X me@192.168.1.2 \"export DISPLAY=:-0; gnome-screensaver-command -d:\"
```

haha  ;)

---

### Post by jal4568 on 2010-05-06
Ok, I'm not a CLI guru by any means so my answer is a great deal less technical than the others. Back when I first switched to Ubuntu, I didn't really get or use the CLI. That is until one weekend when I decided to install a ton of applications just because I could. Needless to say several didn't work and I wanted to know why. 

The best thing the CLI provides that GUI doesn't is _information_. Opening a malfunctioning application via the command line usually results in some sort of error message that tells you why something isn't working. This was the first consistent use I had for the CLI and it quickly became one of my favorite differences from my previous OS. For new less-technically aware users, the feedback provided by the CLI is not only a useful tool but has the potential to encourage them to further educate themselves (as it did in my case).

---

