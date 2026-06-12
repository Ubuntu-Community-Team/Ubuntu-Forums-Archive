---
title: "enable or disable deskup gui for ubuntu server 11.10"
date: 2012-02-15
forum: Server Platforms
---

### Post by snickasaurus on 2012-02-15
I have a fresh install of 11.10 with openssh, LAMP, webmin and all the latest and greatest updates/patches for the OS. I'm not entirely new to Linux but I am to a linux server. Just as a note this machine will NOT be accessible from outside my LAN and more than likely will only be running for a month before I try another distro (before ultimately coming back to ubuntu especially since I hear 12 will be coming out before long and it will have LTS)

I would like to know if there is a way for me to install a minimal desktop environment as I've found, for me, it's just easier at times to complete certain tasks. Now I have read on the few commands it would take to install 'ubuntu-desktop' and I think it was 'gdm' but for the sake of it being a server can I have the machine boot as normal to a prompt and use it command line only (I love webmin but am trying to steer away from it) with the ability to start the x environment for 20 or so mins if need be then drop back down to a command prompt only so as to free up resources. And for a little extra info about the server it's main usage once I get it setup correctly will not only allow me to gain knowledge of this powerful server but will run VMware Workstation so I can start learning it as well. Very excited about both.  :-)

Any help/directions/links would be GREATLY appreciated!!


Thanks in advance,
Snickasaurus

---

### Post by jerrrys on 2012-02-16
Im a home user so take this with a grain of salt.

I would go to /user/lib/ and comment out (#) gdm or lightdm (whichever your running)

That would get you back to tty.

Then I think, but haven't tried it so don't really know, use the "startx" command to go back to gui.

Also I don't know if your aware of this, but for a lighter server desktop you can:

sudo apt-get install --no-recommends ubuntu-desktop

[http://packages.ubuntu.com/oneiric/ubuntu-desktop](http://packages.ubuntu.com/oneiric/ubuntu-desktop)

---

### Post by aeiah on 2012-02-16
there are many ways to go about this. the simplest is probably to install lxde and then disable the login/session manager so it doesnt boot to a gui by default.

id go a slightly different way myself though, with plain openbox and a few programs as i see fit. no login / session manager. you'd start it by typing ```
startx
```

this is what id install:

```

sudo apt-get install xinit openbox thunar lxappearance obmenu obconf leafpad tint2 chromium-browser
```

xinit does the startx stuff
X server will get pulled down with openbox
thunar is a file manager
lxappearance is for setting gtk themes
obmenu and obconf are for configuring openbox menu and general settings
leafpad is a text editor
tint2 is a taskbar

---

### Post by gordintoronto on 2012-02-16
There's no reason you can't run Ubuntu Desktop full time. It will have a very slight impact on server performance, but it doesn't sound like that is an issue.

---

### Post by snickasaurus on 2012-02-16
@jerrys - Thanks for the info. I've seen that command before and I will give it a try..along with the other suggestions as well. Thanks for the reply!
    
@aeiah - I have heard of openbox but never tried it. Will definitely give it a go. Thanks for the reply!
    
@gordintoronto - It's not a question of how much performance I would lose it's a matter of wanting to learn how it's done in most IT environments.

---

### Post by gordintoronto on 2012-02-17
"Real" web servers don't have a monitor or keyboard after the OS is installed, they are controlled by SSH from another computer. This will add about six hours to your learning curve, and it's quite possible you will never need to know about it.

---

### Post by snickasaurus on 2012-02-17
Well this server is for VMware to virtualize the servers I already have in the house...totaling 6 desktops. Crazy eh? I know about SSH as I use it to run my Mac server at work. I can't see how it would be as easy to setup a virtual machine via console though I've heard you can do it. This is why I would like to run it headless but have the ability to work at it with physical kb/mouse when needed. And I do know that I can set up the vm's for remote access. Just wanted a GUI for now till I get used to things.  :-)

---

