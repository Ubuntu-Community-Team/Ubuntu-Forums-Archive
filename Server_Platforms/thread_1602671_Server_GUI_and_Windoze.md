---
title: "Server GUI and Windoze"
date: 2010-10-21
forum: Server Platforms
---

### Post by Trunkles on 2010-10-21
Hi folks.

I need to run a GUI on my server (To be able to run an Code::Blocks or Lazarus) and then access the server GUI via a terminal window on Windoze XP. I have SSH running on the server and PuTTY on windoze, which is fine for a shell but I need the GUI.

So... which is the best GUI for the server and which terminal software on XP?

Ta muchly.

Simon.

---

### Post by James78 on 2010-10-21
Server: sudo apt-get install ubuntu-desktop codeblocks etc etc

Windows XP: PuTTY, XMing

Remember: SSH has the ability to forward X11. That means you can run a GUI app running on your server on Windows through PuTTY. It's a really nice feature.

---

### Post by dtfinch on 2010-10-21
Xming is a good X server for Windows to use with X11 forwarding. I've also had to install the xauth package on the server, but I was installing apps individually rather than the full ubuntu-desktop package, which might also provide it.

---

### Post by arrrghhh on 2010-10-21
I would recommend just installing the actual ubuntu-desktop version instead of installing server and then desktop on top of it.

With that said, [ServerGUI](https://help.ubuntu.com/community/ServerGUI) is the official Ubuntu doc on the subject.  You can certainly forward X over ssh like James78 said - just install xmming on your xp machine & forward X over ssh in your putty config.

---

### Post by Trunkles on 2010-10-22
Thankies.

I've installed desktop, code::... yada yada yada on the server. And yes, it is a server so I can't put base Ubuntu on there.

I've installed xming/xlaunch on the PC (Which already had putty on it).

All I have to do now is work out how to get an X Window on my machine. And so far I've had no success whatsoever! :biggrin:

Simon.

---

### Post by Strategist01 on 2010-10-22
Hi there, I think this little tutorial might help: [http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html](http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html)

---

### Post by oregonbob on 2010-10-22
If you have Gnome or KDE on the server, take a look at NX from nomachine.com . It uses ssh and runs great, just like you are sitting at the console. You just install the free, 2-user server on server, then run the free client on a Windows, Linux or Mac. I love it. Fast and reliable!

---

### Post by HermanAB on 2010-10-22
Howdy, the best way to control a remote machine is with SSH.  Install the GUI on the server, but then don't run it - well, run it once to make sure it works.  Don't start Xorg, you don't need to actually run Gnome on the server, you just need the Gnome/KDE applications and the libraries to be installed, but not running, so after installing it all, change the runlevel to 3.

Then from the desktop machine, connect to the server thus:
$ ssh -X -C -c blowfish user@server gnome-panel

Now you can go click happy and run any GUI application at the click of a mouse, transparently on the local machine.

You can do the same from Windows - just install Cygwin and then run the above command from a Cygwin console.  The remote programs will then run transparently on the Windows desktop.

---

### Post by Trunkles on 2010-10-22
Well... that was a disaster. I now have a usable desktop, code::blocks and lazarus but postfix, courier, apache, bind et al have stopped working.

So, how do I reverse ```
apt-get install ubuntu-desktop
``` ?

---

### Post by dtfinch on 2010-10-22
In what way did they stop working?

---

### Post by Trunkles on 2010-10-22
Just about every way. Bind still appears to work. But apache doesn't serve pages and you can't get mail. Putty no longer talks to ssh. Samba appears to be working. ISPConfig doesn't work but that's hardly surprising as apache isn't working.

I'm just praying that the major hurdles I went through to get the server working haven't been undone.

When I installed ubuntu-desktop I thought I was installing a GUI interface to the server, *not* the desktop version. :(

---

### Post by arrrghhh on 2010-10-22
Well if you used aptitude it probably wouldn't have been such a disaster...

Either way, I wouldn't recommend installing the ubuntu-desktop package on a server - why wouldn't you just install ubuntu-desktop at that point?!?

---

### Post by Trunkles on 2010-10-22
I installed it 'cos someone appeared to suggest it.

James78 said...

> Server: sudo apt-get install ubuntu-desktop codeblocks etc etc

I *thought* I was just installing the gui, not the entire desktop system.

So now I reckon I need to revert to server. Is there any way I can either remove desktop and leave what was there before or is there a way of doing a non-destructive install of the server version?

---

### Post by arrrghhh on 2010-10-22
> **Trunkles said:**
> I installed it 'cos someone appeared to suggest it.

James78 said...



I *thought* I was just installing the gui, not the entire desktop system.

So now I reckon I need to revert to server. Is there any way I can either remove desktop and leave what was there before or is there a way of doing a non-destructive install of the server version?

Psychocats to the rescue!  [PureKDE](http://www.psychocats.net/ubuntu/purekde) - Now I know it says PureKDE - just do the steps to "Remove Ubuntu" - then you should be done... I hope it works for ya, like I said if you had installed with aptitude it probably would've removed it in a much cleaner manner...

---

### Post by dtfinch on 2010-10-22
When you installed ubuntu-desktop, did it ask to uninstall a bunch of packages because of dependency issues? I usually abort when it says that, but it rarely happens unless I'm upgrading to a new release. The advantage of aptitude in this case, is rather than suggest removing all the packages who's dependencies would be broken by the new install/update as apt-get does, it tries to find an optimal middle ground to resolve the dependency issue, and gives better clues as to what that issue might be.

You can probably just reinstall the packages that were removed, if that's what happened. Most or all your settings should still be intact.

---

### Post by Trunkles on 2010-10-22
Cool, thank you. Well sorta. LOL

I ran the remove ubuntu and rebooted. I now have an attractive pale blue screen with a "desktop folder" and a "microblog" on it. Apache, courier and postfix are still fornicated. :(

Any ideas on where to go from here?

---

### Post by Trunkles on 2010-10-22
Anyone got any ideas on how to get aptitude to install a package *without* destroy all the configs? I've looked at man aptitude but can't see anything in there that tells me how.

---

### Post by oregonbob on 2010-10-22
Just exactly how did you install ubuntu-desktop? Did you use tasksel?

Look in /var/log/dpkg.log to see what it installed or removed. Even if you removed server components by accident I wouldn't panic because it is likely you can fix it all with a couple of commands, and your configuration work will still be there.

If it is not too long attach your /var/log/dpkg.log

---

### Post by Trunkles on 2010-10-22
The relevant bit of dpkg.log is ~16,000 lines, so probably not a good idea to post it. :P

The install was done by ```
apt-get install ubuntu-desktop
```
which was how james78 suggested.

If I install the missing bits via aptitude, will it overwrite the config files?

---

### Post by James78 on 2010-10-23
> **Trunkles said:**
> I installed it 'cos someone appeared to suggest it.

James78 said...



I *thought* I was just installing the gui, not the entire desktop system.

So now I reckon I need to revert to server. Is there any way I can either remove desktop and leave what was there before or is there a way of doing a non-destructive install of the server version?
Please accept my apologies. I should've put a warning on the post!!

Either way though, in technicality, installing it shouldn't stop your system from working. Only if you encounter dependency issues, and the like, and don't resolve them while you can. (Apt-get is good for this, so you'll know what you installed, and any issues. It's also a good idea to copy the list it says it'll install, makes it easy to remove them all after)

Anyways though, this guide may help you out more than "just install ubuntu-desktop". Although, if you look closely, the guide really isn't much more than I said either.
[https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

Regarding your dpkg.log. The lines are that long because it's telling you what it's configuring, etc. What you really just want though is the part that shows everything you're installing, I'm pretty sure there's a part like that, because I remember seeing it in my log once. It should be something like "apt-get install ubuntu-desktop <package> <10 million more packages>", might not have the apt-get install bit. or you might also want any parts that say "error", "dependency issue", etc. (note that my search terms aren't exactly correct, so you'll have to figure it out)

Also, using tasksel (as the guide mentions) you might be able to re-install/uninstall it.

> If I install the missing bits via aptitude, will it overwrite the config files?
If it attempts to overwrite any of your config files, it should warn you, and give you the option to keep local file, install maintainers version (packaged config file), or see the differences (great when updating packages, to keep the old config, but incorporate all the new changes).

---

### Post by Trunkles on 2010-10-23
Apology accepted James. Not a worry.

If I use apt-get to reinstall the bits that were removed by installing ubuntu-desktop, will it leave the config files alone? They're all there and I don't want to go through the nightmare of reconfiguring everything.

---

### Post by James78 on 2010-10-23
> **James78 said:**
> ... If it attempts to overwrite any of your config files, it should warn you, and give you the option to keep local file, install maintainers version (packaged config file), or see the differences (great when updating packages, to keep the old config, but incorporate all the new changes).
I was still editing and updating my post when you posted yours. ;)

---

### Post by Cosma on 2010-10-23
why do you still bother about installing/uninstalling everything?
just copy your configs and reinstall the server with just the packages that you really need.

if you can't find all configs then this is even a bigger reason to start from the beginning.

---

### Post by Trunkles on 2010-10-24
Well, I did start again from scratch and it's all working now.

Thank you everyone for all your help.

Simon.

---

### Post by oregonbob on 2010-10-28
I think there is a new bug in the package systems that now remove unrelated packaged when a user tells it to "ADD" a package. That is just plain illogical and wrong. I used to make package changes with confidence and now I am spooked expecting unintended results. Just watch the posts come in as others hit this snag.

As for a GUI on a server? I put gnome on them all at install time. But my servers are always small business multipurpose. A GUI for admin is vital.

---

