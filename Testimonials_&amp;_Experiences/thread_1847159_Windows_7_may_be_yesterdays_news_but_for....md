---
title: "Windows 7 may be yesterdays news but for..."
date: 2011-09-20
forum: Testimonials &amp; Experiences
---

### Post by PayPaul on 2011-09-20
I spent 2 extremely frustrating months trying to get Windows 7 to behave on my pc.  My machine is not a dinosaur by some standards; 4gb ram, Amd2 dual core, main drive hitachi 500gb and 3 external hard drives. However reboots progressively got worse with win7 hanging on startup for hours. Hitting the reset button constantly and seeing the OS capriciously start and then not start made me want to toss the whole thing out the nearest window. 

I then took the plunge, cleared out a partition on the main drive and installed Ubuntu 11. It has its learning curve and some programs don't meet my expectations and needs but .......big BUT.... It starts up every time. I did find a known glitch on startup having to do with Ubuntu or grub(?) not finding the boot drive yet one or two commands later I'm logged in. I did find the solution or multiple solutions for that problem on this site and sometime will dive into them. Yet for all that it doesn't take me a whole day and a half to get this OS to start up. That's a big difference.

Yesterday I had a program, the Wine Config utility, freeze up on me. I'm thinking, *oh I wish there was a Task Manager. *Well, there isn't and _that_ was never 100 percent reliable. So I posted the problem on this site. Didn't get a reply yet but found the answer in another thread that used a set of commands in Terminal and voilà! It worked immediately! Try that with windows! For all the geekiness and resemblance to my old friend DOS it has, Ubuntu has much more direct and immediate solutions to problems I've received no action from Microshaft on.

I do wish some Linux programs like The GIMP did more Photoshop like things such as having adjustment layers and layer styles but I've only had to alter my workflow a bit to get around that. Those improvements may come. Someone on another thread in here said they were "tired of fixing glitches". Well, maybe my time of seeing that angle will come but right this minute I'm glad I can use my machine. It doesn't crash 3 to 4 times a day anymore. In fact it only crashed once and the restart process only took about 10 minutes not 2 days.  While I may want to reinstall Windows more cleanly on the other partitions to get some of the functionality I don't get here, it can only be a fallback OS now. Ubuntu is here to stay for me.

Time to make some coffee.

:mrgreen:

---

### Post by mörgæs on 2011-09-20
Glad you liked it. Welcome aboard!

---

### Post by ugm6hr on 2011-09-20
It's nice to hear from someone who takes a positive view of the learning curve in swapping to a new OS.

And have you seen System Monitor? And Play on Linux (for Wine)?

---

### Post by haqking on 2011-09-20
> **PayPaul said:**
> I spent 2 extremely frustrating months trying to get Windows 7 to behave on my pc.  My machine is not a dinosaur by some standards; 4gb ram, Amd2 dual core, main drive hitachi 500gb and 3 external hard drives. However reboots progressively got worse with win7 hanging on startup for hours. Hitting the reset button constantly and seeing the OS capriciously start and then not start made me want to toss the whole thing out the nearest window. 

I then took the plunge, cleared out a partition on the main drive and installed Ubuntu 11. It has its learning curve and some programs don't meet my expectations and needs but .......big BUT.... It starts up every time. I did find a known glitch on startup having to do with Ubuntu or grub(?) not finding the boot drive yet one or two commands later I'm logged in. I did find the solution or multiple solutions for that problem on this site and sometime will dive into them. Yet for all that it doesn't take me a whole day and a half to get this OS to start up. That's a big difference.

Yesterday I had a program, the Wine Config utility, freeze up on me. I'm thinking, *oh I wish there was a Task Manager. *Well, there isn't and _that_ was never 100 percent reliable. So I posted the problem on this site. Didn't get a reply yet but found the answer in another thread that used a set of commands in Terminal and voilà! It worked immediately! Try that with windows! For all the geekiness and resemblance to my old friend DOS it has, Ubuntu has much more direct and immediate solutions to problems I've received no action from Microshaft on.

I do wish some Linux programs like The GIMP did more Photoshop like things such as having adjustment layers and layer styles but I've only had to alter my workflow a bit to get around that. Those improvements may come. Someone on another thread in here said they were "tired of fixing glitches". Well, maybe my time of seeing that angle will come but right this minute I'm glad I can use my machine. It doesn't crash 3 to 4 times a day anymore. In fact it only crashed once and the restart process only took about 10 minutes not 2 days.  While I may want to reinstall Windows more cleanly on the other partitions to get some of the functionality I don't get here, it can only be a fallback OS now. Ubuntu is here to stay for me.

Time to make some coffee.

:mrgreen:

Great to hear a positive response to unfamiliar surroundings, glad you like it

---

### Post by el_koraco on 2011-09-20
> **PayPaul said:**
> 
Yesterday I had a program, the Wine Config utility, freeze up on me. I'm thinking, *oh I wish there was a Task Manager. *Well, there isn't and _that_ was never 100 percent reliable. So I posted the problem on this site. 

There's nothing as fully featured as the Windows Task Manager in Linux, but there are options. The gnome System Monitor is one, pretty similar to the TM on Win. An even better one is htop, a command line utility that you bring up in a terminal. 

of course, the easiest thing to to when an application freezes up is open a terminal window, type in 

```
xkill
```whereupon your mouse cursor will turn into a cross and then clicking on the offending application window. Just watch out not to click on the desktop, that will kill the file manager Nautilus, which is responsible for managing the desktop, and you'll be in some trouble. 

If you know the name of the misbehaving program, say Firefox, you can open a terminal and type in

```
killall firefox
```You can do a ps -ef | grep firefox, which will give you a process ID (PID), number, that can be used in conjuction with the kill command (pgrep firefox would work the same, but ps gives you a more complete picture). 

Take my current system 

```
[B][~]
>> ps -ef | grep firefox[/B]
elkoraco  1882     1 16 16:48 ?        00:01:45 /home/elkoraco/firefox/firefox
elkoraco  1883  1882  0 16:48 ?        00:00:00 [firefox] <defunct>
elkoraco  1939  1882  0 16:51 ?        00:00:00 /home/elkoraco/firefox/plugin-container /usr/lib/mozilla/plugins/libflashplayer.so -greomni /home/elkoraco/firefox/omni.jar 1882 true plugin
elkoraco  1969  1953  0 16:59 pts/0    00:00:00 grep firefox 


```This tells me that Firefox is running with the PID 1882, so I can issue a 

```
kill 1882
```or, if I want to force it against all obstacles, 

```
kill -9 1882
```Read the man pages for kill and killall for further clarification.

---

### Post by stalkingwolf on 2011-09-20
i dont know about 11 but as far as 10.10 there is an aplet you can add to your top panel to kill misbehaving applications.  

It is called force quit.  right click on the panel, click the aplet you want, click add.  bobs your uncle.

---

### Post by lancest on 2011-09-20
Glad you found a solution! Ubuntu is quite functional & trustworthy to trust one's livelyhood with. 
Dumped Win 7 on my new laptop recently.
 Everything works smoothly on Linux thanks to great developers and this forum!  11.04 64 bit- ASUS N53 - running fast and cool.

---

### Post by PayPaul on 2011-09-20
> **el_koraco said:**
> There's nothing as fully featured as the Windows Task Manager in Linux, but there are options. The gnome System Monitor is one, pretty similar to the TM on Win. An even better one is htop, a command line utility that you bring up in a terminal. 

**The task manager may be considered by some to be fully featured but I  see the benefits of direct commands over a gui interface middleman. As I  said TM in windows would periodically not give immediately results. **

of course, the easiest thing to to when an application freezes up is open a terminal window, type in 

```
xkill
```whereupon your mouse cursor will turn into a cross and then clicking on the offending application window. Just watch out not to click on the desktop, that will kill the file manager Nautilus, which is responsible for managing the desktop, and you'll be in some trouble. 

[B]Now that's a fascinating new way to kill a program. When I initially tried to close the Wine config editor, the X mark on the title bar refused to perform the action for which it was designed. I may try the above suggestion sometime. Though I do find sometimes moving the mouse and say, dragging a prog onto the launcher from the applications center can be tricky to downright impossible. There are always multiple ways of accomplishing a task in any operating system. I actually find myself preferring the command options presented here.
[/B]
If you know the name of the misbehaving program, say Firefox, you can open a terminal and type in

```
killall firefox
```You can do a ps -ef | grep firefox, which will give you a process ID (PID), number, that can be used in conjuction with the kill command (pgrep firefox would work the same, but ps gives you a more complete picture). 

[B]That ps ef command was the first I learned to get the name of the  process winecfg.exe and then of course I applied a killall command to  shut it down. 
[/B]
Take my current system 

```
[B][~]
>> ps -ef | grep firefox[/B]
elkoraco  1882     1 16 16:48 ?        00:01:45 /home/elkoraco/firefox/firefox
elkoraco  1883  1882  0 16:48 ?        00:00:00 [firefox] <defunct>
elkoraco  1939  1882  0 16:51 ?        00:00:00 /home/elkoraco/firefox/plugin-container /usr/lib/mozilla/plugins/libflashplayer.so -greomni /home/elkoraco/firefox/omni.jar 1882 true plugin
elkoraco  1969  1953  0 16:59 pts/0    00:00:00 grep firefox 


```This tells me that Firefox is running with the PID 1882, so I can issue a 

```
kill 1882
```or, if I want to force it against all obstacles, 

```
kill -9 1882
```Read the man pages for kill and killall for further clarification.


I have a lot of exploring to do in Ubuntu.

BTW I would ask a side question. Is it possible to run a Windows Setup disk in Ubuntu, using Wine or some other virtual program and actually have it go through all the real paces including formatting my C partition? Windows 7 would only serve as a standby OS and as it is the turdy thing doesn't act right. The only way I could ever kickstart the silly prog is to use the repair disc I made. I'm of the strong suspicion that the partition it was in would need a total reformat for Win7 to work at all. Given that would this reformat of C effect Ubuntu in any way?

---

### Post by Arthur_D on 2011-09-20
Reinstalling Windows tends to remove GRUB from the MBR, which is the startup menu where you choose what OS to boot. That is simple to fix with a LiveCD where you can just use boot-repair to reinstate GRUB as the leader of your boot sequence. :)

More info on that can be found here: [RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by el_koraco on 2011-09-20
I'm sorry, I have absolutely no idea with regard to Wine. If I understand you correctly, you're asking whether you can run a program from Wine and have it format the partition you're using? If that's the case, then no, the setup in Linux doesn't let you make changes to a partition while it's in use, you have to unmount it, and you can't unmount a root partition. 

If you cant to reformat a partition (in Linux, these things are called partitions, in Windows they're disks, like C, D etc) that you're not using - say, if you have Windows installed to C: and Ubuntu to D: or E: - then while you're booted to Ubuntu you can simply install the program Gparted, and do the format from there. YOu can reformat the Ubuntu partition with Gparted, but you have to do it from the Live CD/USB, on which Gparted is installed. 

But I suggest you make a separate thread in Absolute Beginners Talk, describe the situation more clearly, and make sure you understand everything that's going on before you attempt to do something.

---

### Post by PayPaul on 2011-09-20
> **Arthur_D said:**
> Reinstalling Windows tends to remove GRUB from the MBR, which is the startup menu where you choose what OS to boot. That is simple to fix with a LiveCD where you can just use boot-repair to reinstate GRUB as the leader of your boot sequence. :)

More info on that can be found here: [RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

Thank you. I thought as much. The logic here is that when Ubuntu is installed by Wubi (in my case) it recognizes the current installation of Windows. Reinstalling Windows will only confuse it because the prior installation of such will no longer be seen by Ubuntu or Grub. 

Yep. The live CD is the only logical way to do this. I will post a thread regarding reinstalling windows from Ubuntu though in the appropriate section.

---

### Post by karen729 on 2011-09-21
> I then took the plunge, cleared out a partition on the main drive and installed Ubuntu 11. It has its learning curve...I'm new to Linux, too, and yes, it does have it's learning curve. But when I think of all the hours I spent trying to learn Windows, it's not so bad. At least with Linux, I can actually find info to learn :)

> Ubuntu has much more direct and immediate solutions to problems I've received no action from Microshaft on.Agreed. Linux in general and Ubuntu specifically, have a super great support system. I have been running an XP partition since it was released, and never did find support for some issues. As soon as I figure out how to watch Netflix on Ubuntu, XP is gone forever.

> Someone on another thread in here said they were "tired of fixing glitches".I think that as long as there are so many different hardware and software configurations, there will always be glitches for some. And anyone that has ever used Windows for longer than 24 hours already knows all about glitches.

Good Luck with your Ubuntu experience! :)

---

### Post by larjan on 2011-09-21
I've been with ubuntu for a few years now and must agree. I don't recall any issues I've had that did'nt have a simple fix. I have a toshiba sattelite running windows 7, that has video driver issues. Same machine running ubuntu runs flawlessly. I use linux not because it's free or open source, ( though either one is a good enough reason ) but because if you put a fraction of the effort it takes to keep a windows install working, into finding your way around linux, you will have a much more stable, reliable, secure, and capable system.

---

### Post by prodigy_ on 2011-09-24
2 OP: Are you sure it's not because of an outdated BIOS or wrong drivers?

---

Win7 has been rock-stable for me since I first installed it 2 years ago. I almost never turn my PC off and I've seen weeks of uptime without any repercussions. Not a single BSOD or spontaneous reboot. Of course it's old news for *NIX users but it's a huge leap for Windows because even XP wasn't quite as stable.

On the other hand I've seen a laptop that was overheating while running Win7 - probably due to Aero. It could run Linux/Gnome without any problems. YMMV.

---

### Post by Paddy Landau on 2011-09-24
> **PayPaul said:**
> ... Ubuntu is installed by Wubi...
WUBI is installed "within" Wndows. As such, it is not a good long-term solution. WUBI is notoriously unstable, especially after upgrades.

If you wish to use Ubuntu long-term, I would uninstall WUBI (after making any backups, of course), and install Ubuntu properly.

Once that is done, you may find that you can run Windows in a virtual machine, e.g. using [VirtualBox]("http://www.virtualbox.org/"), within Ubuntu.

---

### Post by PayPaul on 2011-09-24
Fascinating. Install Ubuntu properly? So where do I find clear and concise instructions on how to do that and still get a dual boot setup? As I understand the term is one "installs Wubi within Windows". Yes, it's a program not installed from a CD and Wubi is operated while running windows. But will a LiveCd as it's called here provide a dual boot scenario as well? I'm not so enmeshed in this current Ubuntu installation with perhaps the exception of this Firefox and its profiles, which I've backed up. Yet where is the documentation or history of Wubi being "unstable"? It is one of the choices given on the Ubuntu site itself. I have seen a thread in here that deals with the Busybox issue and a set of commands and changes that can be done to ameliorate it. A deuced nuisance to reinstall but if there is some acknowledged merit in it...

I'll will say that some of the puported methods for using Ubuntu proved to be a bust for me. I tried running it off a USB stick. That ran out of space real fast. Oh, but that had tons of documentation on the process and a lot of people hyped it up real good. It does seem that even this Ubuntu install takes a good deal more space than I thought it would. From what I what I see of the remaining disk space on the section of the partition I allocated for it from the Wubi install, the OS is using 15gb of a 30gb space. Speaking to that I'd dearly love to know where the rest of the 300 gbs of space from this partition Ubuntu is one went. Wubi gives 30gb as a max number to use for Ubuntu on this partition. I thought that a little weird but figured with the programs it could install that might be about right. There is, like in any OS, a lot more for me to learn for sure. There are things that I want to do and things that aren't necessary and I'm sure would give great delight to others. As of now I'm still puzzling through getting all my networked computers to be seen. That process is as difficult as the same process in Windows. 

Oh well, live and learn. *When in doubt, check it out* has always been an axiom.

---

### Post by mörgæs on 2011-09-25
There is a lot of advice for installing a dual boot here:
[http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)

---

### Post by Paddy Landau on 2011-09-25
Lots of questions, Paul! Let me answer a few of them.

> **PayPaul said:**
> So where do I find clear and concise instructions on how to do that and still get a dual boot setup?
First uninstall WUBI (*after* backing up). The basic process is:

[LIST=1]
[*]Boot from the Live CD and try Ubuntu without installing. This helps you find out whether or not it will work on your hardware.
[*]**Back up your data!** Although the installation process is very well tested and established, as with any OS, there is a small risk of data loss.
[*]Boot from the Live CD and install. Follow the instructions, which will shrink Windows to fit on roughly half your hard drive, while allocating the remaining space for Ubuntu. If you hit any problems with the process or you struggle to understand the prompts, start a new thread on [Absolute Beginner Talk]("http://ubuntuforums.org/forumdisplay.php?f=326"). You'll get plenty of friendly help.
[/LIST]
You can also search the forums for further information.

The advantages of a native installation instead of WUBI are higher reliability and fewer crashes (a solid installation never crashes); greater ability to recover from fatal errors, even when self-created; faster; greater ease of upgrading; greater flexibility if you become an advanced user; you can even run Windows inside Ubuntu if your hardware is powerful enough (so you don't actually need to reboot). There is also the possibility of running a hypervisor, where you can quickly switch between Ubuntu and Windows without rebooting, but that's an advanced topic.

Your major decision is whether you want to go with LTS versions (e.g. if you are a business valuing stability), or the in-between releases (if you want to upgrade every six months at the cutting edge).

> **PayPaul said:**
> But will a LiveCd as it's called here provide a dual boot scenario as well? ... That ran out of space real fast. ... people hyped it up
No. The Live CD is a way to "play". You can also have a persistent Live USB, which can act as a portable installation. I don't know where you found people hyping it up, but I would disagree -- it's not meant for serious or large-scale work, but rather for portability between computers.

> **PayPaul said:**
> Yet where is the documentation or history of Wubi being "unstable"? It is one of the choices given on the Ubuntu site itself.
There is no such documentation. But I have come across thread after thread where WUBI has unexpectedly fatally failed, usually (but not always) after an upgrade. Ubuntu can usually be recovered from a fatal failure, but not WUBI as it is enclosed within Windows. I know that the Ubuntu website includes WUBI as an option; I strongly believe it should be made clear that WUBI is a temporary solution suitable for experimentation.

> **PayPaul said:**
> As of now I'm still puzzling through getting all my networked computers to be seen. That process is as difficult as the same process in Windows.
Once you have Ubuntu properly installed, you will need to install something called Samba. Samba emulates Windows networks, allowing you to find other Windows computers on the network. It usually works very well, but sometimes there is a little fiddling you need to do when you install Samba. If you struggle, search the forums; failing that, start a new thread, and people will help you.

> **PayPaul said:**
> *When in doubt, check it out*...
That's what Live CD and WUBI are for -- I wish the website made it clear!

---

### Post by PayPaul on 2011-09-29
> **Paddy Landau said:**
> WUBI is installed "within" Wndows. As such, it is not a good long-term solution. WUBI is notoriously unstable, especially after upgrades.

If you wish to use Ubuntu long-term, I would uninstall WUBI (after making any backups, of course), and install Ubuntu properly.

Once that is done, you may find that you can run Windows in a virtual machine, e.g. using [VirtualBox]("http://www.virtualbox.org/"), within Ubuntu.

I did find something today that explains backups of packages and settings. Soon I'll take the plunge and go full tilt into a reinstallation. I've also found a RAW processing program, Darktable, that meets most if not all of my Photo Processing requirements. The GIMP is still a little gimpy because of its lack of adjustment layers yet there are workarounds. I can't say I'd totally give up on Windows but I'm close to it. This OS has very little in the way of start up problems as opposed to that OS.

---

### Post by PayPaul on 2011-09-29
I've learned that there's a new version of Ubuntu coming out on October 13th. I think I'll wait a bit for that, get the LiveCD for it and than follow all the backup procedures then. I hope it's a good release. I wonder what they'll code name it. Galloping Giraffe?

---

### Post by mörgæs on 2011-09-29
It is Oneiric Ocelot - of all strange names... 
[http://ubuntuforums.org/forumdisplay.php?f=403](http://ubuntuforums.org/forumdisplay.php?f=403)

Like with all releases, best is to wait a month after release before installing.

---

### Post by Paddy Landau on 2011-09-30
> **PayPaul said:**
> I wonder what they'll code name it. Galloping Giraffe?
Since version 6.06, the [releases have been alphabetical]("https://wiki.ubuntu.com/Releases"). I don't know the name of the next one, which will start with P, but I have read Pleasant Pheasant (nicely alliterative).

EDIT: [A full list]("https://wiki.ubuntu.com/DevelopmentCodeNames").

---

### Post by prodigy_ on 2011-09-30
> **Paddy Landau said:**
> I have read Pleasant Pheasant
I hope they'll pick something shorter.

---

### Post by Paddy Landau on 2011-09-30
> **prodigy_ said:**
> I hope they'll pick something shorter.
Well, Pleasant Pheasant is shorter (in speech) than Oneiric Ocelot ;). But I can imagine the accidental puns when people refer to using Pleasant...

---

### Post by PayPaul on 2011-09-30
> **Paddy Landau said:**
> Well, Pleasant Pheasant is shorter (in speech) than Oneiric Ocelot ;). But I can imagine the accidental puns when people refer to using Pleasant...

Oneiric alludes to the dream state. I guess it's a case of....

To dream, the impossible dream. 
To find that my Wine is working well. 
To bear up with that Terminal sorrow. 
To run from a Narwhal that's gone... 
To fight for the right to burn a Lightscribe. 
To know all the shortcuts and commands.. 

To dream....the impossible......DREAM!!


Perhaps this can be called Ode to An Oneiric Ocelot?

---

### Post by vcrpex on 2011-10-03
Hi Paypaul,
looking at your specs of your computer, it is quite similar to mine. you definitely can use ubuntu as the main OS and use windows 7 through virtualbox. I have done it with ubuntu 10.10 64bit as main and windows 7 in virtualbox before. Though i am now using squeeze instead.

---

