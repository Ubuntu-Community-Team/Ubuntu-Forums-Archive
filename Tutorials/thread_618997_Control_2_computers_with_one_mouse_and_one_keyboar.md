---
title: "Control 2 computers with one mouse and one keyboard"
date: 2007-11-21
forum: Tutorials
---

### Post by jr.gotti on 2007-11-21
[B]What this guide will help you do:
[/B]This guide will help you control *two separate computers *with one mouse and one keyboard, utilizing SSH and a little known tool called x2x.

[B]What this guide will not help you do:
[/B]This guide will *not *help you set up a dual monitor system (One computer with two monitors.)

[B]Advantages of this method over a dual monitor:
[/B]As said before, you will be controlling _two separate computers._ This means that both computers can be running completely different OS's, WM's, etc. This also means that you will have the combined hard drive space of both boxes.

[B]Disadvantages of this method:
[/B]The only real downside to this is the fact that you can't drag anything from one screen to the other. (Of course there are other methods of transferring files, and I'm sure it is quite possible to set up a script that can be added to the nautilus right click menu for transferring files to the other box. However, this is beyond the scope of this guide.) If you are looking for simply a bigger desktop, with the capability to drag windows and such, then this is not for you, and you should look into a dual-monitor setup.

With all that out of the way, let me explain how this works. Basically, you establish an SSH session with the computer you wish to control with the mouse/keyboard connected to your main box. Once connected, you run a program called x2x, which allows the cursor to "jump" to the second box when you move the mouse to the edge of the first screen, and vice-versa. Theoretically, this link could continue through infinite computers, meaning you can control three, four, five computers with one mouse. (Why you would have five computers on one desk is beyond me, although I wouldn't mind =])

Okay, down to the nitty gritty.

The first thing we need is all required packages. Plunk this in a terminal;

```
sudo apt-get install openssh-server x2x
```Now we need to set up a trusted pairing of the two computers, to avoid inputting a password every time you initiate the connection.

Edit: **These packages must be on both boxes. **(Not so much x2x, but it's good to have it on both. openssh-server is a must on both.)

```

ssh-keygen -t rsa

```Press enter to accept the default file location, and then press enter twice for a null passphrase. You should now have the file "id_rsa.pub" in ~/.ssh. We need to copy this to the other computer as ~/.ssh/authorized_keys. To do this, put the following in the terminal:

```

scp ~/.ssh/id_rsa.pub user@host:/home/user/.ssh/authorized_keys

```Of course, substitute "user" with your username on the second box (unless it is the same as it is on the local machine, in that case you can just start with the host), and substitute the IP address of the remote box for "host."

Okay! Now you should be able to SSH into the remote box without a password. To test it, just run the following:

```
ssh *host*
```And it should connect without any prompts.

Everything good so far? Good. The hard parts done. Save the following two scripts in /bin:

Name the following script "startxshare".

```

#!/bin/sh
ssh -X *host* x2x -east -to :0 &

```(This is assuming that the second computer is to the right of your first. If it is not, simply change east to west.)

Name the following script "stopxshare".

```

#!/bin/sh
pid=$(ps aux | grep "ssh -X *host*" | grep S | awk {' print $2 '})
kill -9 $pid

```Naturally, you will probably want to set up a static IP on at least the second machine, if not both. If it's dynamic, then the scripts will have to be changed whenever your IP changes, rendering the script useless. (Unless of course, you write a script to automatically update the X scripts, and that, although possible, can get tricky.)

Also, it should go without saying, but I'll say it anyway, set both scripts to executable:

```

sudo chmod +x /bin/startxshare
sudo chmod +x /bin/stopxshare

```Finally, you want to make sure that X Forwarding is enabled. It should be by default, but cant be two careful.

```

cat /etc/ssh/sshd_config | grep Forwarding

```If you see "X11Forwarding yes," you're ready to go. If not, do change it.

Ready for the magic? Hit alt+f2, or open a terminal, and enter "startxshare." Now move your cursor to the desired screen edge, and all should go well. To stop it, just enter "stopxshare."

Any questions? Ask away!

-Gotti

---

### Post by kd7swh on 2007-11-25
I use Synergy, but x2x would seem to be more secure if its via ssh.

I'll have to give it a try.


___
EDIT: after a quick look on the synergy webpage, I found out that it will also work with OpenSSH. So if anyone wants an alternative to x2x. Synergy is FOSS and stable. [http://synergy2.sourceforge.net/](http://synergy2.sourceforge.net/)

---

### Post by Capricori on 2007-11-25
Thanks!
I've been looking for ways to do something similar... with a bit of messing, this might just do the job :)

Just one thing... I would get rid of the little joke at the top... some people won't find it funny... particularly previous victims with empty hard drives, and the mods who are trying to stop this kinda thing.
It would be a shame for you to get banned, since you're intent obviously isn't malicious. Just my advice :)

---

### Post by jr.gotti on 2007-11-26
> **Capricori said:**
> Thanks!
I've been looking for ways to do something similar... with a bit of messing, this might just do the job :)

Just one thing... I would get rid of the little joke at the top... some people won't find it funny... particularly previous victims with empty hard drives, and the mods who are trying to stop this kinda thing.
It would be a shame for you to get banned, since you're intent obviously isn't malicious. Just my advice :)

Eh, you're probably right...I took your advice. Oh, and I'm a victim of a similar joke. Ever see the fork bomb? It's almost impossible to resist!

---

### Post by gluonman on 2007-11-26
I've been trying to connect to the remote host by typing ssh host, but every time it comes back with Permission Denied. What do I need to do?

---

### Post by gluonman on 2007-11-26
I'm also having difficult creating the startxshare and stopxshare files in /bin. It keeps telling me that I don't have permission. I understand what it's saying, I'm just not sure how I need to go about saving the files in a way that allows me to do it as the owner. I know, I'm a newb. But please explain how I need to save those files.

---

### Post by jr.gotti on 2007-11-26
> **gluonman said:**
> I've been trying to connect to the remote host by typing ssh host, but every time it comes back with Permission Denied. What do I need to do?

You need to replace host with the IP address of your remote machine. Alternatively, you can edit /etc/hosts and add it in there. For example, I would either connect by typing:

```
ssh 192.168.2.20
```

Or by adding the following line to /etc/hosts:

```
192.168.2.20 senior
```

And connecting by typing:

```
ssh senior
```

Hope this clears up some confusion!

---

### Post by jr.gotti on 2007-11-26
> **gluonman said:**
> I'm also having difficult creating the startxshare and stopxshare files in /bin. It keeps telling me that I don't have permission. I understand what it's saying, I'm just not sure how I need to go about saving the files in a way that allows me to do it as the owner. I know, I'm a newb. But please explain how I need to save those files.

You're gonnah wannah save those somewhere in your home folder, and then move them to /bin like this:

```

sudo cp startxshare /bin
sudo cp stopxshare /bin
sudo chmod +x /bin/startxshare
sudo chmod +x /bin/stopxshare

```

---

### Post by Capricori on 2007-11-26
@gluonman - You could save them into your home directory (where you do have permission), and them copy them to /bin as root (root can do pretty much what it likes). If you save the files to /home/whatever-your-name-is/startxshare, then you can copy it by opening a terminal and typing 'sudo cp ~/startxshare /bin/' (without the quotes). Then do the same for stopxshare.
Using sudo gives you system-wide access, and the potential to damage things if you do something daft... So if you don't understand the command I just gave you, I would encourage you to investigate what it does first :) 

Edit: beat me to it :)

@jr.gotti - fork bomb? Can't say I have.. shall have to investigate :)

---

### Post by gluonman on 2007-11-26
Okay. When I said that I entered ssh host, I knew I was supposed to substitute host with the IP address. I just chose not to reveal my IP address. And I figured out how to save the startxshare and stopxshare. Only problem now is that when I run startxshare, I move my mouse to the left edge of the screen. I certainly disappears from this computer, but I don't see it pop up in the second computer. Do both computers need to be connected to internet or something? Do both need to have ssh installed?
I originally found this thread trying to find out how I can connect my desktop PC to the internet by connecting it to my laptop (which is connected to a neighbourhood wireless router) via ethernet cable.

---

### Post by jr.gotti on 2007-11-26
> **gluonman said:**
> Okay. When I said that I entered ssh host, I knew I was supposed to substitute host with the IP address. I just chose not to reveal my IP address. And I figured out how to save the startxshare and stopxshare. Only problem now is that when I run startxshare, I move my mouse to the left edge of the screen. I certainly disappears from this computer, but I don't see it pop up in the second computer. Do both computers need to be connected to internet or something? Do both need to have ssh installed?
I originally found this thread trying to find out how I can connect my desktop PC to the internet by connecting it to my laptop (which is connected to a neighbourhood wireless router) via ethernet cable.

Oh! My apologies...I'll edit that in. Both need to have SSH installed so that the SSH port will be open. I don't think they need to be connected to the internet though...just connected to the network.

---

### Post by Lucho77 on 2007-11-26
Hi Jr.Gotti; what is the required set up in a windows-XP machine to access a ubuntu-server.?
Thanks for your help.

---

### Post by jr.gotti on 2007-11-26
> **Lucho77 said:**
> Hi Jr.Gotti; what is the required set up in a windows-XP machine to access a ubuntu-server.?
Thanks for your help.

[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

Your gonnah wannah download "putty.exe"

Thats to connect to your Ubuntu box, mind you. As far as the other way around...I'd have to look into it...I've never had a need to do so.

---

### Post by gluonman on 2007-11-26
Thank you, jr.gotti. I'm still trying to figure out how to access the internet with my second computer. I could always buy a wireless card for it, but it would be so much cheaper if I could figure out how to set it up so that my laptop that has internet connection can act as a "router" for my desktop. I've heard rumours from pretty much everyone that that can be done, but the how of it I've yet to read. So, once I have my desktop connected to the internet, then I can install ssh on it and probably successfully control both computer with one mouse and one keyboard.

---

### Post by fizzybrain on 2008-07-01
There aren't many thanks being expressed here - presumably because it just works so effortlessly (people are a lot more grateful if they have to wait for something...). Maybe it's late, maybe I'm overtired, but I've just jumped up and down with joy - it works! A brilliantly-written how-to, a million brilliant thanks.

A while ago I destroyed the USB controller on my laptop (a home-made ipod charger shoved 12V into the USB port - complete brain failure on my part) and had no way of using a mouse or external keyboard (no other working I/O apart from firewire and ethernet). It has a trackpad, but they are really no replacement when it comes to the real accuracy needed for video work or composition or graphics (and the keyboard is rubbish).

Now I can use my significantly lesser replacement machine as a mouse-and-keyboard-server and still have the power and big screen of the first one. Hurrah. Now I wonder what is the lowest-powered device I can use to do this.... Do you think there could be any way of using a machine which was not running X as the mouse-and-keyboard-server - say an old 386 laptop with 4MB RAM :-) ?

You can have no idea how much this will improve my life : working mouse > video editing > finally completing my 12-month project to get me back into gainful employment > gainful employment > money > life (yeah, a few stages missed out there, but y'know...).

I know you didn't write the programs and I could probably have found the info elsewhere but the how-to was just what was required, so thanks.

I'd better stop now before I start weeping....

Share and Enjoy.

---

### Post by bas.janssen on 2011-02-04
Thanks! This works like a charm! Have used synergy for this before, but this seems a lot more secure. Great tip!

---

### Post by JFizDaWiz on 2011-10-20
this is what i needed. Synergy has been nothing but a problem for me as of late and I needed other way of doing this. the setup was too simple and worked brilliantly. 

thanks for the heads up on this, even though an old thread still holds good info for now

---

