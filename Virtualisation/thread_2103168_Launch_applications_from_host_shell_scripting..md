---
title: "Launch applications from host shell scripting."
date: 2013-01-09
forum: Virtualisation
---

### Post by Sotafin on 2013-01-09
Hello Everyone, This is my first post :).

I am not using Ubuntu, I use elementary Os Luna beta but anyway i wanted to join the community because I find the best answers are always here.

I have for some time been working on turning my xp VM into something that I will never notice running, but will supply me with a windows layer of sorts. Before you say it, yes I do use wine and that's fine for some things, but as a developer with clients who use windows, I need that flawless runtime and a wider range of windows specific programs. hence virtualization. I design graphics, so I use Photoshop, Illustrator and inDesign CS5, which I own a master suite. I don't want a discussion about alternatives, (they are great, I agree, but the import exports always go wrong so they cant be used by other designers which is really bad in my field of work).

My virtual machine uses an .au3 scripts that hides the taskbar, so but I can still call up the start menu with the windows key. another script sticks  it into seamless mode no mater what. The third script fixes an error with refresh rates of the screen, but for good measure, my virtual machine uses the same desktop background as my host to eliminate any glitches, if the guests desktop ever did appear through the host. I also use aero snap xp to give the same snap functionality that matches my host! I also use leftsider xp to move (most) windows controls to the left. Lastly I use a gnome skin for xp to give a closer to host appearance.   

Getting to the point now, I use a shell script containing: 

```
VBoxManage guestcontrol Windows_xp execute --image "c:\WINDOWS\notepad.exe" --username ****
```

which I linked to a launcher.desktop, and an icon, (for elementary purposes I created a .dockitem that links to .desktop). 

Fantastic! with that code I can run any windows app that I like. through a launcher on my dock.

However it wont run without the virtual machine running at the same time. The short-cuts do nothing without the virtual machine, and rightly so.

But how can I improve my user experience? no Vm start up short cuts on my dock, a more fluid way of doing things. "How about this" I hear you cry, "start the Vm on start up?" thanks, but nah, because I might not need it in this session. It's the accepted way, but I have a proposed better way. 

What about incorporating into the script above, the following functions: if virtual machine is not running, start it, and echo "Talking to windows xp", with a delay of 20 secs allowing time to boot) before executing the guest control line. Also if the VM is running just run the guest control line as normal.

My problem is, I know what I must do, I just don't know how. I don't know shell scripting syntax at all. so if anyone has any ideas how to write this, I will learn from your example. 

:D please and thank you.

Sotafin - Adam  

Resources:
[https://forums.virtualbox.org/viewtopic.php?f=1&t=38125]("https://forums.virtualbox.org/viewtopic.php?f=1&t=38125")
[https://www.youtube.com/watch?v=m9FzKy7FKjg]("https://www.youtube.com/watch?v=m9FzKy7FKjg")

---

### Post by aromo on 2013-01-09
The script part is easy.  What you need to find out is how to use VBoxManage to find out if the VM is running and how to power it on if it's not.

---

### Post by Habitual on 2013-01-09
[QUOTE=]The script part is easy.  What you need to find out is how to use VBoxManage ...[/QUOTE]

[Virtualbox scripting cheats]("http://www.bournetoraiseshell.com/article.php/20121030193345437")

I abuse Slackware, so YMMV...

---

### Post by Sotafin on 2013-01-11
> **Habitual said:**
> [Virtualbox scripting cheats]("http://www.bournetoraiseshell.com/article.php/20121030193345437")

I abuse Slackware, so YMMV...

Kudos on the slackware, I love KDE, I actually left it for ellementery.

Anyway, thanks for that little snip-it that should load faster actually.

---

