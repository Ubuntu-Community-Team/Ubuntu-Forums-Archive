---
title: "Task managing made easy!"
date: 2007-10-25
forum: Ubuntu Brainstorm
---

### Post by suchawato on 2007-10-25
I don't know about the rest of you,
 but how many times have I been browsing the internet -with multiple tabs, transferring files from one side of my harddrive to maybe a backup disc, modifying some photo in another desktop, when all of a sudden, I  launch another task and...OOPS it hangs, trying to do to much at once!
The only way out of this is to wait untill somthing finishes, or, to end a process with the task manager which is itself a crawl, or, reboot.

Now, wouldn't it be nice, especially with file transfers or downloads in progress, to be able to right-click on the application's tab or window and be able to Pause the task, Resume the task, or if nessicary Kill it. 
Not end. Kill.
This would allow the user to say in the case of a file transfer, to pause it, freeing up enough system resources to end something else, allowing the sytem to be unfrozen again. Or, in an emergency, to be able to Kill it simply by right clicking on it. 
The problem with using the current system that has "end process" is that "end process" requires a significantly larger  ammount of system resources than "kill", which gets top priority and is almost immidiatly effective.  There have been many times when "ending the process" took so long, that it was more effective to just reboot. The problem with rebooting, is that you loose any unsaved data. Another is that rebooting effectively kills ALL processes instead of just one or two enough to free up the system again, which is sort of like catching the crook by arresting the whole city. While killing a process is not an ideal, if the system can be unfrozen this way to save valuble data, then I would find it to be a valuble option, especially if I don't have to wait for the system monitor to load, which is very time consuming in a hanging system, and is, itself, another drain on the resources.

More ideally (and very handy) would be a "pause process" feature, which could allow a process to be continued when more resources became avalable. This would be particularly handy when doing such tasks as backing up files, which often mean running more than one file transfer process at a time.

What do you all think?
-Stu

---

### Post by smartboyathome on 2007-10-25
> **suchawato said:**
> I don't know about the rest of you,
 but how many times have I been browsing the internet -with multiple tabs, transferring files from one side of my harddrive to maybe a backup disc, modifying some photo in another desktop, when all of a sudden, I  launch another task and...OOPS it hangs, trying to do to much at once!
The only way out of this is to wait untill somthing finishes, or, to end a process with the task manager which is itself a crawl, or, reboot.

Now, wouldn't it be nice, especially with file transfers or downloads in progress, to be able to right-click on the application's tab or window and be able to Pause the task, Resume the task, or if nessicary Kill it. 
Not end. Kill.
This would allow the user to say in the case of a file transfer, to pause it, freeing up enough system resources to end something else, allowing the sytem to be unfrozen again. Or, in an emergency, to be able to Kill it simply by right clicking on it. 
The problem with using the current system that has "end process" is that "end process" requires a significantly larger  ammount of system resources than "kill", which gets top priority and is almost immidiatly effective.  There have been many times when "ending the process" took so long, that it was more effective to just reboot. The problem with rebooting, is that you loose any unsaved data. Another is that rebooting effectively kills ALL processes instead of just one or two enough to free up the system again, which is sort of like catching the crook by arresting the whole city. While killing a process is not an ideal, if the system can be unfrozen this way to save valuble data, then I would find it to be a valuble option, especially if I don't have to wait for the system monitor to load, which is very time consuming in a hanging system, and is, itself, another drain on the resources.

More ideally (and very handy) would be a "pause process" feature, which could allow a process to be continued when more resources became avalable. This would be particularly handy when doing such tasks as backing up files, which often mean running more than one file transfer process at a time.

What do you all think?
-Stu

You can use xkill to kill only a single process. Just use alt-f2 to type xkill and click on the window you want to kill. It will be killed immediately. :)

---

### Post by Martje_001 on 2007-10-25
It's already possible, so it shouldn't be too hard to develop.

---

### Post by suchawato on 2007-10-27
xkill, nice, I will use that.
Pause would still be a nice feature though.
In the case of a file transfer, If I kill it, I would have to do it all over again, loosing all the time spent already transfering the files.
It would be a nice option.
Maybe "xpause" or "xresume"?

---

### Post by WinterWeaver on 2007-10-27
You can also add the "Force Quit" applet to your Panel... when you wish to kill a app, just click the applet and click the app.

---

### Post by wInddnIw on 2007-11-03
This would be very useful !
For example when you launch two big transfert or task and you'd like one of them to finish as quick as possible. Currently you can use the system monitor but sometimes you can't (too much ressources used or process not listed).

---

### Post by wInddnIw on 2007-11-03
Hence I made some searches and made this code :
xpause :  
> #!/bin/bash

wid=$(xwininfo  |grep 'Window id:' |cut -d" " -f4)
pid=$(xprop -id "$wid" |grep "^_NET_WM_PID" | cut -d" " -f3)

`kill -SIGSTOP $pid` && exit 0

exit 1xresume : 
> #!/bin/bash

wid=$(xwininfo  |grep 'Window id:' |cut -d" " -f4)
pid=$(xprop -id "$wid" |grep "^_NET_WM_PID" | cut -d" " -f3)

`kill -SIGCONT $pid` && exit 0

exit 1
It can surely be optimised a bit but it's doing its job.

wInd

---

### Post by suchawato on 2007-11-04
_Sweet!_, Do I just enter that in the command line to get it working?
Or what?
That's awesome! 
Thanks for doing that!

---

### Post by 23meg on 2007-11-04
Save them separately in a text editor, make the files executable ("chmod +x filename" or right click, Properties, Permissions) and run them.

---

### Post by suchawato on 2007-11-04
so for instance:
```
chmod +x /home/xpause
```?
where "xpause" is saved as a file-extentionless ASCII text file?

---

### Post by suchawato on 2007-11-04
so for instance:
```
chmod +x /home/xpause
```?
where "xpause" is saved as a file-extentionless ASCII text file?
Also I didn't see "permissions" in a right click window. Right click on what?

---

### Post by 23meg on 2007-11-04
Yes, put the text in an empty document and save it; afterwards, assuming you're using GNOME, right click the file, click "Properties", go to the "Permissions" tab and tick the "Allow executing file as program" box.

---

### Post by suchawato on 2007-11-05
So I tried ```
chmod +x /home/xpause
```
and also ```
sudo chmod +x /home/xpause
```
after settingup the files as you suggested and putting them in /home/*the files*
It didn't seem to do anything.
I tried clicking on the window of a movie that was playing, and nothing happened.
Am I missing some parameter?
-Stu

---

### Post by 23meg on 2007-11-05
1) /home isn't your home folder; /home/yourusername is. Don't put stuff in /home.

2) Delete all those files, start from scratch and do what I said in post #12. Don't touch the command line at all.

3) After doing what I said in post #12, double click on the files, and choose "Run".

---

### Post by suchawato on 2007-11-05
Holey Cow,
It works Great!
Thanks Meg!
And thank *you* Wind!
This is really great.
I made a custom application launcher in my taskbar for them so I don't have to dig for them if I need them.
They work Great!
We should definetely have these be an option in Hardy!
Thanks so much!

---

### Post by suchawato on 2007-11-05
So I made some icons for them.
These are .png's. I will work on SVG versions.

---

### Post by suchawato on 2007-11-05
Here is a full set of PNG icons from 16 - 128 pixels.

---

### Post by suchawato on 2007-11-05
Here are the executable files for anyone who wants to use them:
23Meg, do you think it would be possible to add these to the "Add to Panel" menu in Hardy?
Maybe add xkill along with them?

---

### Post by suchawato on 2007-11-05
Opps! they didn't attach:

---

### Post by 23meg on 2007-11-05
> 23Meg, do you think it would be possible to add these to the "Add to Panel" menu in Hardy?
Maybe add xkill along with them?

No, since they're not panel applets. That dialog is used to add applets. An equivalent of xkill is already there: Force Quit.

---

### Post by suchawato on 2007-11-05
I don't mean as they are currently.
I made a custom application launcher for each of them,
But I would imagine it would be easy enough to mod them in such a way that they would be panel applets.
That's what I am wondering, if we made them in a way that they were panel applets could we do it?
I mean a panel applet is just a "application launcher" with a pre determined shortcut and icon am I right?
With the actual app in a designated location in the file system yes?
we could easily make these that.

---

### Post by suchawato on 2007-11-05
I mean there's some stuff in that menu like "system monitor" and "address book search" and "show desktop" that are nothing but shortcuts to small or not so small applications.
they use SVG icons stored in a specific area, and presumbably all we'd need to do to get this to work would be to ammend the "add to panel" sytem file(s) (wherever that is) to include the appropreate shortcuts and icon links so that they show up in the menu yes? 
As well as create an appropreate svg icon.
True?

---

### Post by 23meg on 2007-11-06
> I mean a panel applet is just a "application launcher" with a pre determined shortcut and icon am I right?

It's not. You may want to look up the GNOME panel applet specifications. In any case, these scripts are quite hackish for default inclusion.

---

### Post by suchawato on 2007-11-07
So what would be nessicary for considration for inclusion?
a clean, working prototype?

---

### Post by 23meg on 2007-11-07
The question would be: is default inclusion in GNOME or Ubuntu really necessary? Why not just have the applet in Universe, for people who have a genuine need for it?

---

### Post by suchawato on 2007-11-07
That would be fine too, I suppose, but how would people know it exists if it was not included by default?
I mean, especially new users.
Besides, it's not as though this would take up a lot of memory, and it is genuinely useful and solves a practical problem. I'm sure most users have run across this problem before, and this makes it easy for them to solve it without rebooting.
I suppose if it were included in the "Add/Remove..." installer list under "System Tools", that could work, as it would be easily able to find, so that they could read a description about it and what it did.
That is, as far as I'm concerned, an acceptable possibility for the programs for the programs to be implemented with.
Is this what you are referring to?
Because that would be fine with me.
It would be a perfect solution for those who would really need it as you say, and that would make it easy to find for those who are new users especially.

---

### Post by wInddnIw on 2007-11-07
> **suchawato said:**
> _Sweet!_, Do I just enter that in the command line to get it working?
Or what?
That's awesome! 
Thanks for doing that!
You're welcome, I was looking for something like that too. Thanks for the icons !

As for adding them as default, it could be useful. Even if they are hackish and lack the elegance of an executable, they rely on fine working programs.

wInd

---

### Post by smartboyathome on 2007-11-07
By the way, I found on the system monitor you can "stop" and "continue" a process. So it is already included in GNOME. :)

---

### Post by coolen on 2007-11-08
The point is that, when you're lagging and your system is struggling to find resources, launching another application just to pause a misbehaving one can be rather time consuming, and compounds the problem.
For those using the scripts, adding them to a path directory (/usr/local/bin would be a good idea) makes it accessible to all users, means less typing from the command line/run dialog, and is just nicer.
I also imagine that setting up a keybinding would be useful, too. Compiz doesn't seem to want to respect mine, though...

---

### Post by coolen on 2007-11-08
By the way, thanks for the scripts. They seem to be working just fine :)
Of interest: Compiz thinks that windows I pause are unresponsive after a few seconds. Nothing that can really be done from our end, just thought it was worth mentioning.

If Compiz could recognise tasks that have been intentionally paused, that'd be great. I'd support this in Hardy 100%. It's great being friendly to newbs, but we want the power users to feel at home, too (in fact, many Ubuntu users are just that).

---

### Post by wInddnIw on 2007-11-08
> **smartboyathome said:**
> By the way, I found on the system monitor you can "stop" and "continue" a process. So it is already included in GNOME. :)Of course it's already included, and of course the system monitor can do it. But the fact is sometimes you can't launch the system monitor :).

---

### Post by smartboyathome on 2007-11-08
> **coolen said:**
> The point is that, when you're lagging and your system is struggling to find resources, launching another application just to pause a misbehaving one can be rather time consuming, and compounds the problem.
For those using the scripts, adding them to a path directory (/usr/local/bin would be a good idea) makes it accessible to all users, means less typing from the command line/run dialog, and is just nicer.
I also imagine that setting up a keybinding would be useful, too. Compiz doesn't seem to want to respect mine, though...

Compiz uses its own keybindings. I think there was a GNOME-to-compiz keybinding plugin being written for compiz, but until then you will have to use the General Options.

---

### Post by suchawato on 2007-11-08
>  Originally Posted by smartboyathome  View Post
By the way, I found on the system monitor you can "stop" and "continue" a process. So it is already included in GNOME. 

> **wInddnIw said:**
> Of course it's already included, and of course the system monitor can do it. But the fact is sometimes you can't launch the system monitor :).

The other thing is that sometimes you can't tell which process belongs to which window. An example of this would be running three different file transfer boxes at the same time. They show up in the system monitor as one process. Clicking on an object directly leaves no question.

---

### Post by coolen on 2007-11-08
I haven't tried it since I started using Gutsy, but in Feisty, Compiz would inherit the Metacity keybindings by default. Quite a few people mentioned similar behaviour.

Additionally, I was using the general options to set it.

---

### Post by smartboyathome on 2007-11-09
> **coolen said:**
> I haven't tried it since I started using Gutsy, but in Feisty, Compiz would inherit the Metacity keybindings by default. Quite a few people mentioned similar behaviour.

Additionally, I was using the general options to set it.

This doesn't seem to be the case with Gutsy, when I try making Metacity key bindings, Compiz doesn't use them. :(

EDIT: Are you using Trevino's repo? If so, then it has the GNOME keybinding bridge included, while gutsy doesn't.

---

### Post by coolen on 2007-11-09
Ahh, no, I'm using the ones from Canonical. Perhaps they feel that, with Compiz enabled by default, there's no reason to inherit changes from Metacity. The settings for Compiz are certainly easier to get at *grumbles about Gnome a bit*

---

### Post by Keith Hedger on 2007-11-11
Hi, I found the scripts quite useful (more so than the system montior and force quit applet) so I combined them into one script and added a gui (via zenity) and a launcher to allow you to stop/resume/kill and also bring up a list that allows you to select multiple processes to control (stopping a window does not always stop the offending process)

---

### Post by coolen on 2007-11-12
Nice. A rather useful script. I'd love to see something like this in a panel applet.

---

### Post by diaa on 2008-02-20
Hi,
I've been working for 2 days on a project called *xsignal*, it's similar to xkill except that instead of killing, it  pops up a menu allowing the user to choose what signal to send to the application.
I was already half way through when I saw this thread and all the nice ( hackish :P) scripts you've made, the last one is significantly powerful... but I decided to continue anyway :)
I'm going to add support for changing the priority via a submenu, but that'll be added later.
Please check the attached screenshot to see *xsignal* in action
Tell me what you think about *xsignal*  and any ideas you have to make it better.

---

### Post by Keith Hedger on 2008-02-20
If its not to big why not zip the whole thing up and post it, after all you can never have too much control and renicing an app from the terminal is a bit tedious at the best of times!

---

### Post by diaa on 2008-02-20
> **Keith Hedger said:**
> If its not to big why not zip the whole thing up and post it!

Actually it's tiny, several kbs.

[SIZE=4]**Use at your own risk**[/SIZE]

it works good for me but I don't know about you so don't blame me, I don't think it'll crash you system but don't try it on sensitive apps(unless you have nothing to lose :))

I didn't send the source because it's not ready at all.

---

### Post by Keith Hedger on 2008-02-21
Well it works fine but lots of gtk errors when run from a commandline ie```
(xsig:7823): Gdk-WARNING **: Error converting from UTF-8 to STRING: Could not open converter from 'UTF-8' to 'ISO-8859-1'
```
like to se the renice bit though

---

### Post by coolen on 2008-02-21
Just tried it out, and it seems to work well. I didn't get the gdk warning mentioned above...it just spits out the pid, the word deactivated (even when continuing a process) and the signal used.

Nice work :)

---

### Post by diaa on 2008-02-21
Thanks for the comments coolen and Keith :) 

> **Keith Hedger said:**
> Well it works fine but lots of gtk errors when run from a commandline ie```
(xsig:7823): Gdk-WARNING **: Error converting from UTF-8 to STRING: Could not open converter from 'UTF-8' to 'ISO-8859-1'
```like to se the renice bit though

Like coolen, I don't get any warnings, I guess it's your system encoding, can you provide more details?

> **coolen said:**
> Just tried it out, and it seems to work well. I didn't get the gdk warning mentioned above...it just spits out the pid, the word deactivated (even when continuing a process) and the signal used.

Nice work :)

The word deactivated has nothing to do with the process, it means that the menu was deactivated.
I hope it'll mature into a useful, open-source application soon.

 I added the priority submenu but it's still not functional, you can see it in the screenshot.
In a - hopefully successful - attempt to decrease the number of items in the priority submenu without descreasing functionality, I came out with the following design:
The number between square brackets is the current priority for the process, the items above the separator in the submenu adjust the priority relatively(-2 -> +2), but those below the separator set the process priority directly(absolutely).

---

### Post by diaa on 2008-02-21
The new binary, with functional priorities submenu :)

---

### Post by Keith Hedger on 2008-02-22
just tried the new one it works but gives the same errors it could be that im running a 64 bit gutsy with a load of 32 bit libs from my old gutsy install so that i can run 32 bit apps (which this is)

---

### Post by coolen on 2008-02-23
The priority only sets properly for me when I'm increasing it. Doesn't work for lowering it, either directly or relatively.

---

### Post by coolen on 2008-02-23
Also, a bug: when at either 18 or 19, if I try to increase the value above 19, the command line output indicates success, although the menu indicator the next time 'round correctly indicates a value of 19.


Oh, and I'd just like to add that I do like the work you're doing on this. It's a small program, but very useful. I'd love to see this incorporated into Ubuntu somehow.

---

### Post by diaa on 2008-02-23
Thanks for the feedback everyone :)

> **Keith Hedger said:**
> just tried the new one it works but gives the same errors it could be that im running a 64 bit gutsy with a load of 32 bit libs from my old gutsy install so that i can run 32 bit apps (which this is)

I guess that's the reason then, probably a 64-bit build will make the warnings go away.

> **coolen said:**
> The priority only sets properly for me when I'm increasing it. Doesn't work for lowering it, either directly or relatively.

Yes, you must be root to decrease the niceness of any process(you can try it with gnome system monitor)... it doesn't make much sense to me either but this is the way Linux works.

> **coolen said:**
> Also, a bug: when at either 18 or 19, if I try to increase the value above 19, the command line output indicates success, although the menu indicator the next time 'round correctly indicates a value of 19.


Yes, I know about this, it's not a bug.
The maximum nice value(which is the same as the least priority) in Ubuntu is 19, anyway I'll try to change this to make it less confusing.

---

### Post by coolen on 2008-02-23
Ahh, fair enough. I would've thought if it's one of your applications, it'd let you.

Perhaps you'd be able to work with PolicyKit (upon Hardy's release) to prompt for a password when attempting to decrease it? I don't know how PolicyKit works, but it's a possibility.

Perhaps you could get it to check whether the new setting is above 19, spit out a warning, and either abort the attempt, or simply set it to 19 anyway.

---

### Post by diaa on 2008-02-23
> **coolen said:**
> Ahh, fair enough. I would've thought if it's one of your applications, it'd let you.

Perhaps you'd be able to work with PolicyKit (upon Hardy's release) to prompt for a password when attempting to decrease it? I don't know how PolicyKit works, but it's a possibility.

Nice idea, but for now I think I'll use libgksu which will be similar to what happens in *gnome system monitor* when you try to increase the priority of an application

> **coolen said:**
> 
Perhaps you could get it to check whether the new setting is above 19, spit out a warning, and either abort the attempt, or simply set it to 19 anyway.

I'll see what I can do

---

### Post by diaa on 2008-07-30
Sorry for the delay, you know one has to earn a living.
I think xsig is ready for release, so I'll simply put it at googlecode, unfortunately I'm not sure how to license it, I've used some code from xprop and I'm not sure which of the licenses at googlecode is it compatible with...
Only the following licenses are available at googlecode:

[LIST]
[*]Apache License 2.0
[*]Artistic License/GPL
[*]GNU General Public License v2
[*]GNU General Public License v3
[*]GNU Lesser General Public License
[*]MIT License
[*]New BSD License
[/LIST]
and the following code is found at the beginning of the file I used from xprop source code:
```

Copyright 1993, 1998  The Open Group

Permission to use, copy, modify, distribute, and sell this software and its
documentation for any purpose is hereby granted without fee, provided that
the above copyright notice appear in all copies and that both that
copyright notice and this permission notice appear in supporting
documentation.

The above copyright notice and this permission notice shall be included
in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS
OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE OPEN GROUP BE LIABLE FOR ANY CLAIM, DAMAGES OR
OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE,
ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR
OTHER DEALINGS IN THE SOFTWARE.

Except as contained in this notice, the name of The Open Group shall
not be used in advertising or otherwise to promote the sale, use or
other dealings in this Software without prior written authorization
from The Open Group.

```

Can someone give me a hand with this?

---

