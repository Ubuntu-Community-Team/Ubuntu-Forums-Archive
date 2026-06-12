---
title: "Force-Quit"
date: 2011-11-05
forum: The Cafe
---

### Post by linuxuser12345 on 2011-11-05
Hey, I am trying to get my latest idea implemented in the next Ubuntu release! Currently, there is no force quit application usable for complete Linux newbies in Ubuntu *by default*. I created two solutions. 
Please see my rationale and solutions here:
[[IMG]http://brainstorm.ubuntu.com/idea/28840/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/28840/)


Please support! I need all the help I can get! :)

---

### Post by haqking on 2011-11-05
> **linuxuser12345 said:**
> Hey, I am trying to get my latest idea implemented in the next Ubuntu release! Currently, there is no force quit application usable for complete Linux newbies in Ubuntu by default. I created two solutions. 
Please see my rationale and solutions here:
[[IMG]http://brainstorm.ubuntu.com/idea/28840/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/28840/)


Please support! I need all the help I can get! :)

[http://www.omgubuntu.co.uk/2011/10/force-quit-applet-unity-launcher/](http://www.omgubuntu.co.uk/2011/10/force-quit-applet-unity-launcher/)

[http://ubuntuforums.org/showthread.php?p=11353918](http://ubuntuforums.org/showthread.php?p=11353918)

---

### Post by zer010 on 2011-11-05
What about the "killall" command?

"killall *process name*"

---

### Post by cariboo on 2011-11-05
Also what about xkill? Just open a terminal type:

```
xkill
```

Then click on the misbehaving application.

---

### Post by zer010 on 2011-11-05
> **cariboo907 said:**
> Also what about xkill? Just open a terminal type:

```
xkill
```

Then click on the misbehaving application.
Nice.  Never heard of that one. Learn something new everyday.

---

### Post by IWantFroyo on 2011-11-05
> **cariboo907 said:**
> Also what about xkill? Just open a terminal type:

```
xkill
```

Then click on the misbehaving application.

Seconded. I always use Alt-F2 to run this. If you need to force-quit something, I don't think you'll want to open anything heavier than xkill.

---

### Post by linuxuser12345 on 2011-11-05
> **linuxuser12345 said:**
> Currently, there is no force quit application usable for complete Linux newbies in Ubuntu **_*by default*_**.
*By default!

---

### Post by sffvba[e0rt on 2011-11-05
> **linuxuser12345 said:**
> *By default!

xkill seems pretty default to me...


404

---

### Post by 3Miro on 2011-11-05
What's wrong with the gnome system monitor. You get a list of running processes and you can right-click kill any one of them. This is very similar to the Ctr+Alt+Del task manager on windows.

---

### Post by Dry Lips on 2011-11-05
> **3Miro said:**
> What's wrong with the gnome system monitor. You get a list of running processes and you can right-click kill any one of them. This is very similar to the Ctr+Alt+Del task manager on windows.

What *I* would have loved to see be implemented, is the gnome system monitor to be
the application that opens when you hit Ctr+Alt+Del... You've got no idea how many
times I've hit Ctr+Alt+Del in vain when an application suddenly froze.

(Is there any shortcut assigned to the system monitor btw? :confused:)

---

### Post by linuxuser12345 on 2011-11-05
The System Monitor shows TMI (too much information)! The System Monitor shows all background applications, plus all open applications, but all with their actual names, not the common names. There is so much information, that the average person would think twice before clicking "end process" to a process he/she isn't entirely sure what it is.

---

### Post by IWantFroyo on 2011-11-05
> **linuxuser12345 said:**
> The System Monitor shows TMI (too much information)! The System Monitor shows all background applications, plus all open applications, but all with their actual names, not the common names. There is so much information, that the average person would think twice before clicking "end process" to a process he/she isn't entirely sure what it is.

Doesn't the Windows Task Manager do this as well? I think a newbie would rather just click on an app to kill it (xkill) than open up a whole new GUI app (further slowing the computer), and seeing a bunch of inevitable gibberish. Dependencies and background apps will get in the way, so no matter what you do, it'll stay confusing.

Also, if someone's computer freezes enough to make them think of installing something like this, they probably shouldn't be using a graphic app to kill something. If my computer suddenly froze, and I tried to open Linux-Kill-App-Something, it would probably make the computer freeze more.

---

### Post by linuxuser12345 on 2011-11-05
> **IWantFroyo said:**
> Doesn't the Windows Task Manager do this as well? I think a newbie would rather just click on an app to kill it (xkill) than open up a whole new GUI app (further slowing the computer), and seeing a bunch of inevitable gibberish. Dependencies and background apps will get in the way, so no matter what you do, it'll stay confusing.

Also, if someone's computer freezes enough to make them think of installing something like this, they probably shouldn't be using a graphic app to kill something. If my computer suddenly froze, and I tried to open Linux-Kill-App-Something, it would probably make the computer freeze more.
Yes, but the Windows task manager separates everything into tabs: All the processes in one tab, and in the default tab is shown the open applications the user can actually SEE in their everyday names.

---

### Post by Dry Lips on 2011-11-05
I've added the force-kill applet to my panel, but I miss something 
that let me shut down programs that freezes when I run them in full screen...

So I think I agree with IWantFroyo that a graphic app isn't ideal in all situations.
I guess I also agree with linuxuser12345 that system monitor could be
simplified a wee bit.

---

### Post by beew on 2011-11-05
To the command line people, what if your apps is locked up so hard that you can't start the terminal? I have encountered situation like this, couldn't bring up the terminal but the kill button still worked

---

### Post by haqking on 2011-11-05
> **beew said:**
> To the command line people, what if your apps is locked up so hard that you can't start the terminal? I have encountered situation like this, couldn't bring up the terminal but the kill button still worked

[Raising elephants]("http://en.wikipedia.org/wiki/Magic_SysRq_key")

---

### Post by beew on 2011-11-05
> **haqking said:**
> [Raising elephants]("http://en.wikipedia.org/wiki/Magic_SysRq_key")

Nice info, but  a kill applet would still be simpler if all you want is to kill the misbehaving apps and you can't remember the key combo (which depend on your keyboard layout)

---

### Post by IWantFroyo on 2011-11-05
linuxuser12345 has a point. The Windows Task Manager is simpler in some ways.

You could probably track down the team in charge of this on LaunchPad and file a bug.

---

### Post by Dry Lips on 2011-11-05
**@linuxuser12345:  **What about a solution **#3**... Tie Ctrl+Alt+Del to a
simplified version of the gnome task manager??? And I also think filing
a bug possibly would be a way to speed things up...

---

### Post by linuxuser12345 on 2011-11-05
> **IWantFroyo said:**
> linuxuser12345 has a point. The Windows Task Manager is simpler in some ways.

You could probably track down the team in charge of this on LaunchPad and file a bug.

Good idea! But everyone, please still vote! :)
I am trying to get little things like this implemented in the next releases of Ubuntu to make it better from the ground-up!

---

### Post by Dry Lips on 2011-11-05
> **linuxuser12345 said:**
> Good idea! But everyone, please still vote! :)
I am trying to get little things like this implemented in the next releases of Ubuntu to make it better from the ground-up!

Can I log in via my launchpad-account, or do I have to create a new account?

---

### Post by linuxuser12345 on 2011-11-05
Bug officially reported! [https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/886620](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/886620)

Thanks :)

---

### Post by linuxuser12345 on 2011-11-05
> **Dry Lips said:**
> **@linuxuser12345:  **What about a solution **#3**... Tie Ctrl+Alt+Del to a
simplified version of the gnome task manager??? And I also think filing
a bug possibly would be a way to speed things up...

Please submit a third solution! :) [http://brainstorm.ubuntu.com/idea/28840/](http://brainstorm.ubuntu.com/idea/28840/)

---

### Post by linuxuser12345 on 2011-11-05
> **Dry Lips said:**
> Can I log in via my launchpad-account, or do I have to create a new account?

Yes, I am pretty sure you can log in with your OpenID from Launchpad. [http://brainstorm.ubuntu.com/idea/28840/](http://brainstorm.ubuntu.com/idea/28840/)

---

### Post by Dry Lips on 2011-11-05
> **linuxuser12345 said:**
> Please submit a third solution! :) [http://brainstorm.ubuntu.com/idea/28840/](http://brainstorm.ubuntu.com/idea/28840/)

I'm just thinking about how different such a solution would be from
your original suggestion #1. A simplified version of the system monitor
would come close to what you originally suggested... The thing is that
I haven't used OS since OS9, so I don't know what the OSX force quit
app is like... Could you just use a simplified version of the system monitor,
to achieve what you suggested, or would you have to create a new application
from scratch? 

Of course I could add a suggestion, but I'm thinking that it is more natural
that you add another one, especially since you've already filed a bug and everything...
:P

---

### Post by duke.tim on 2011-11-05
I agree that this would be a very good thing to implement. Especially for new users. If it is I would suggest giving the program/app a high priority in case of High CPU load etc...

---

### Post by linuxuser12345 on 2011-11-05
Here is the bug report:
[https://bugs.launchpad.net/gnome-system-monitor/+bug/886620](https://bugs.launchpad.net/gnome-system-monitor/+bug/886620)

Everyone, please help me out here! Thank you for all your support.

---

### Post by Legendary_Bibo on 2011-11-05
I personally never needed a force quit because nothing has crashed on me.

---

### Post by jwbrase on 2011-11-06
> **linuxuser12345 said:**
> *By default!

Both the Alt-F2 run dialog and xkill are available by default. An easier and more obvious method of bringing up xkill might be desirable, though, given that it is not obvious to new users that xkill exists or that Alt-F2 can be used to run programs by name.

> **Dry Lips said:**
> What *I* would have loved to see be implemented, is the gnome system monitor to be
the application that opens when you hit Ctr+Alt+Del... You've got no idea how many
times I've hit Ctr+Alt+Del in vain when an application suddenly froze.

(Is there any shortcut assigned to the system monitor btw? :confused:)

I don't believe there's any shortcut assigned to System Monitor by default, but I've used CCSM on my Lucid install to bind System Monitor to ctrl-alt-del (and System Monitor with gksudo to shift-ctrl-alt-del). I'm not sure if ctrl-alt-del is set to anything by default, you may need to go to the keyboard shortcuts dialog and disable any actions on ctrl-alt-del before you go to CCSM and bind the System Monitor to it.

> **linuxuser12345 said:**
> The System Monitor shows TMI (too much information)! The System Monitor shows all background applications, plus all open applications, but all with their actual names, not the common names. There is so much information, that the average person would think twice before clicking "end process" to a process he/she isn't entirely sure what it is.

The "Applications" tab on the Windows task manager shows the *window title*, not the "everyday name" of the processes that appear on the taskbar. It might be nice to at least have a "Window title" field in the System Monitor.

You can go to Edit -> Preferences in the System Monitor and uncheck boxes under "Information fields" that you find to be unnecessary information. (You might, for example, want to set it up to show only Process Name, Status, % CPU, and Memory).

> **Dry Lips said:**
> I've added the force-kill applet to my panel, but I miss something 
that let me shut down programs that freezes when I run them in full screen...

System Monitor on Ctrl-Alt-Del will *sometimes* handle this, but there are a fair number ill-behaved applications that grab all keyboard input (except keystrokes that interact with the kernel, like Ctrl-Alt-F1 to switch to a virtual terminal, or any of the magic sysreq hooks), and X is ill behaved enough to let them. (I generally like X+Gnome+Compiz better than the Windows GUI, but the fact that full-screen applications are even allowed to intercept keystrokes meant for your desktop is a big pain). For applications that usurp the keyboard when full screen, you can, however, switch to a VT and use kill. That's not really newbie friendly though...

---

### Post by 3rdalbum on 2011-11-06
If you set the System Monitor to Control-Alt-Delete, people will complain that it's preventing them from changing the "kill X" key combination to that.

How about binding xkill to Super-Escape?

---

### Post by Dry Lips on 2011-11-08
**@linuxuser12345**:
I finally ended up promoting your original #1 solution, which *possibly* could 
be built upon a simplified version of the System monitor. I did also support
your bug report, but perhaps these two issues ought to be linked to each other. 
Worst case scenario is that both the Ubuntu team as well as the Gnome team
works on something similar. But at least you've managed to draw attention 
to this issue. Well done! :)

--

 Issues like this is something that I definitively think is important to address:
 > **jwbrase said:**
> 
System Monitor on Ctrl-Alt-Del will *sometimes* handle this, but there  are a fair number ill-behaved applications that grab all keyboard input  (except keystrokes that interact with the kernel, like Ctrl-Alt-F1 to  switch to a virtual terminal, or any of the magic sysreq hooks), and X  is ill behaved enough to let them. 

--

Sorry, but I had to create a new account:
> **linuxuser12345 said:**
> Yes, I am pretty sure you can log in with your OpenID from Launchpad. [http://brainstorm.ubuntu.com/idea/28840/](http://brainstorm.ubuntu.com/idea/28840/)

---

### Post by Triblaze on 2011-11-08
I have xkill hotkeyed. But for new users, that'd probably be pretty helpful.

---

### Post by Thewhistlingwind on 2011-11-08
Anyone who mentions Xkill doesn't get it. 

How is a new user (Who hasn't browsed the forums, or googled.) going to know to use Xkill? Besides, directing people to a terminal program to *kill a window *is silly. 

There's already an applet, I see no reason why this can't be included in some bag of system goodies somewhere. Heck, a python wrapper with a GTK interface around Xkill would suffice.

---

### Post by duke.tim on 2011-11-08
default keybinding (ctrl+alt+del) + xkill = newuser easy

---

### Post by linuxuser12345 on 2011-11-09
> **Thewhistlingwind said:**
> Anyone who mentions Xkill doesn't get it. 

How is a new user (Who hasn't browsed the forums, or googled.) going to know to use Xkill? Besides, directing people to a terminal program to *kill a window *is silly. 

There's already an applet, I see no reason why this can't be included in some bag of system goodies somewhere. Heck, a python wrapper with a GTK interface around Xkill would suffice.

OMG thank you!

---

### Post by BrokenKingpin on 2011-11-09
If I get a complete UI lockup I use Ctrl + Alt + F1 to switch to command line, then just kill the application causing issues. Then I can switch back with Ctrl + Alt + F7 and everything is fine.

---

### Post by HiImTye on 2011-11-09
> **BrokenKingpin said:**
> If I get a complete UI lockup I use Ctrl + Alt + F1 to switch to command line, then just kill the application causing issues. Then I can switch back with Ctrl + Alt + F7 and everything is fine.
this is what I do and if it is bad enough I just ```
killall -9 gnome-session
``` and it drops me to the login screen

and also there's the reisub

---

