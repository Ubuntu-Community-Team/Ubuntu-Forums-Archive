---
title: "Server GUI &quot;On Demand&quot;"
date: 2013-04-20
forum: Server Platforms
---

### Post by jpaytoncfd on 2013-04-20
I have seen this question many times. "Should I install a desktop on a server" It always ends in no, performance issues. 

I would like to find a way to have the desktop software available through RDC so I can login from a Windows Client and use the desktop. But only have the desktop process running when the user is logged in. The console should still only be terminal. 

Thanks,
Joe

---

### Post by Roswebnet on 2013-04-21
Hi
I never used it by myself, but I think it might be helpful:
[http://www.karlrunge.com/x11vnc/](http://www.karlrunge.com/x11vnc/)
[https://help.ubuntu.com/community/VNC/Servers#x11vnc](https://help.ubuntu.com/community/VNC/Servers#x11vnc)
[http://www.thefanclub.co.za/sites/default/files/images/howto/UltraVNC.jpg](http://www.thefanclub.co.za/sites/default/files/images/howto/UltraVNC.jpg)
[http://www.thefanclub.co.za/how-to/how-setup-ubuntu-business-box-server-ubb-part-2](http://www.thefanclub.co.za/how-to/how-setup-ubuntu-business-box-server-ubb-part-2)
Regards

---

### Post by jpaytoncfd on 2013-04-21
Thanks, I know what remote server I am going to use. What I want to know is how can I keep the desktop elements from running until I login to the Remote. And then close them when I log out.

---

### Post by Lars Noodén on 2013-04-21
> **jpaytoncfd said:**
> Thanks, I know what remote server I am going to use. What I want to know is how can I keep the desktop elements from running until I login to the Remote. And then close them when I log out.

You have to disable lightdm to stop the GUI from loading on boot.  You could do this by editing /etc/init/lightdm.conf but that risks error.  You can also set a manual override in /etc/init

```

sudo sh -c 'echo "manual" > /etc/init/lightdm.override'

```

Then when you want the graphical interface you can start it manually. 

```

sudo service lightdm start

```

Same goes for stopping it.

```

sudo service lightdm stop

```

You don't have to give users full sudo access, you can put a single line in a file in /etc/sudoers to let a group start and stop lightdm.

```

%ldmusers  ALL=(ALL:ALL) NOPASSWD: /usr/sbin/service lightdm start, /usr/sbin/service lightdm stop

```

Then add those users to the group ldmusers and they can start and stop the GUI.  (After you've created the group, of course.)

In the long run you might want to try to also learn the shell.  You can do that a little at a time as you go along.  There are some good reasons for it.  It is more flexible and far more powerful than the graphical tools.  It is similar, if not nearly identical, across versions and even distros making it learn once, run anywhere.  It works better over poor network connections.  And the shell  is scriptable.

---

### Post by jpaytoncfd on 2013-04-21
I use the shell a lot over SSH. I mostly want the GUI for a few app's that cant be used from shell or file manupliation / cleaning. That method I think will work. I will give it a try.

---

### Post by Lars Noodén on 2013-04-21
If you just want to run graphical application on your server but have them displayed locally on your desktop, then you can set X11 forwarding on when you connect with ssh.   That will forward ouptput from X11 (graphical) apps from your server to your X server (desktop)

```

ssh **-X** *xx.yy.zz.aa*

```

That way you don't need any desktop environment or window manager on the server, just the apps.  You just type the name of the app you want to run and it shows up locally.  It can be a bit sluggish over connections with a lot of latency, though.

---

### Post by ally_uk on 2013-04-22
Why not just run a GUI and remote into in using vnc? this whole GUI vs CLI argument is pointless use what you are comfortable with. GUI effects performance? what kind of hardware are these people using Pentium 2's :P
this isn't the 80s whack a GUI on it and get the best of the both worlds I say.

---

### Post by tgalati4 on 2013-04-22
The xorg (X11) windows server used about 9% of CPU on a 1 GHz, Celeron.  On newer computers you are looking at 1 or 2%, so install the desktop and be happy.  Yes, you can install the desktop and simply logout or Control-Alt-F1 to get to a console--putting the window server to sleep essentially.  This still allows you to log in remotely will ssh (I use ssh -2 -Y username@computername) then start a program or window manager such as gnome-panel or mate-panel (if you are running Linux Mint Mate) and you will get a full desktop of the remote machine.  Works pretty well.

I don't run Unity, so I'm not sure how Unity handles remote desktops.

As you can see from these responses, there are a dozen ways to accomplish this.

---

### Post by ally_uk on 2013-04-22
Exactly 1% or 2% performance hit is your Dual Core / Quad core system really going to feel this? :P GUI and Cli is the best combination Sure some Linux / basement / nerds will slate you if you don't use the command line only but hey use whatever you feel comfortable with and whatever gets the job done :)

---

### Post by MAFoElffen on 2013-04-22
I'm at home in commndline... But I install min X on my servers. I can click, cut and paste faster than I type. 

Not that it matters, but here's how I do it and why (below):
```

#!/bin/bash


  ## Mike Ferreira: <MAFoElffen@ubuntu.com>
   
  ## Setup/Install Minimum X on Debian based Server (Ubuntu)
  # -- Server monitoring software needs a minimal X config for remote 
  # -- graphical admin consoles to use X enabled monitoring tools to  
  # -- display.
  # --
  # -- I like this config so far...
  # -- 
  # -- This install adds a minimal X config that allows an "instance" load of X that 
  # -- server admin tools from a remote graphical X console needs to get working 
  # -- over X enabled ssh.
  # --
  # -- This X instance does not load by default (local on server) and unloads X on exit.


## Installs a Minimal X Server Core
echo "# Installing the XServer core"
echo "#"
echo " "
# Install minimal
sudo aptitude install --without-recommends xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-video-vesa xserver-xorg-video-fbdev xinit


## Installs basic drivers. Uncomment for proper driver if you have one of these
# These are just basic xorg video drivers to drive low-end server GPU's
 # ATI, on most my server boards, Radeon Rage XL.
   sudo aptitude install xserver-xorg-video-ati


 ## Intel    
 # sudo aptitude install xserver-xorg-video-intel


 ## Sis    
 # sudo aptitude install xserver-xorg-video-sis


 ## Nvidia    
 # sudo aptitude install xserver-xorg-video-nv


# Installs a minimal window environment with a few utils to manage it 
 # After, this can be started locally using "startX" or
 # remotely using "ssh -X username@servername", then load program... 
 # Program will load in an X window on the remote console.
 # 
 # Same is through if I have scripts calling xmessage to display 
 # graphical console error measages...
sudo aptitude install openbox obconf obmenu openbox-themes


# Installs a few graphical apps. To tie into the WE  
sudo aptitude install leafpad synaptic python-software-properties
sudo aptitude install pcmanfm chromium-browser xvidtune gnome-nettool
# sudo aptitude install gmrun wicd


# Add an .Xuthority file to user home
 # If you use ssh with "-X" to enable X over shh, 
 # it needs to see the .Xauthority file of the user.
rm ~/.Xauthority
touch ~/.Xauthority
chmod ~/.Xauthority


# Replaces the menu.xml with with all the edits to add the above app's to the OpenBox menu.
cat << _EOT_ > ~/.config/openbox/menu.xml
<?xml version="1.0" encoding="utf-8"?>
<openbox_menu xmlns="http://openbox.org/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://openbox.org/                 file:///usr/share/openbox/menu.xsd">
    <!-- This file created by MAFoElffen 2013.03.25 -->
        <menu id="root-menu" label="Openbox 3">
        <item label="Byobu">
            <action name="Execute">
                <execute>xterm byobu-launcher</execute>
            </action>
        </item>
        <item label="Terminal Emulator">
            <action name="Execute">
                <execute>x-terminal-emulator</execute>
            </action>
        </item>
        <item label="Web Browser">
            <action name="Execute">
                <execute>x-www-browser</execute>
            </action>
        </item>
        <!-- This requires the presence of the 'menu' package to work -->
        <menu id="applications-menu" label="Applications">
            <item label="Leafpad">
                <action name="Execute">
                    <execute>leafpad</execute>
                </action>
            </item>
            <item label="Leafpad as Root">
                <action name="Execute">
                    <execute>gksudo leafpad</execute>
                </action>
            </item>
            <item label="File Manager">
                <action name="Execute">
                    <execute>pcmanfm</execute>
                </action>
            </item>
        </menu>
        <separator/>
        <menu id="/Debian"/>
        <separator/>
        <menu id="client-list-menu"/>
        <separator/>
        <menu id="system-menu-" label="System Utils">
            <item label="X Video Tune">
                <action name="Execute">
                    <execute>xvidtune</execute>
                </action>
            </item>
            <item label="Synaptic">
                <action name="Execute">
                    <execute>gksudo synaptic</execute>
                </action>
            </item>
            <item label="Network Tools">
                <action name="Execute">
                    <execute>gnome-nettools</execute>
                </action>
            </item>
        </menu>
        <item label="ObMenu">
            <action name="Execute">
                <execute>obmenu</execute>
            </action>
        </item>
        <item label="ObConf">
            <action name="Execute">
                <execute>obconf</execute>
            </action>
        </item>
        <item label="Reconfigure">
            <action name="Reconfigure"/>
        </item>
        <item label="Restart">
            <action name="Restart"/>
        </item>
        <separator/>
        <item label="Exit">
            <action name="Exit"/>
        </item>
    </menu>
</openbox_menu>


```

Note: Anyone that knows me... I specialize in Unix and Linux graphics layer support. So "this" is tweaked a bit to automate the install of minimum X on my servers. 

Here's what the script installs- it installs a minimum of files for Xserver, plus a few Xserver util's I use. Then it installs a light Desktop Environment. In this case OpenBox. It installs a few light app's for editing, terminal, filemanager, synaptic, etc... with a custom openbox menu with all those app's. It configures an Xauthority file for me.

Note what it doesn't install*** It does not install a Desktop Manager. Because of this, it boots like a server to the console. I want this behavior in my servers. That way, for some reason if it boots, it boots the kernel completely to the console. As it is an instance, I find it secure and has hardly any overhead at all, for what I do. After login, you don't need another graphical login through a DM. From the commandline, you start it by just typing in 
```

sudo startx

```
When you exit the Desktop Environment... it returns to the console prompt. My servers are servers. My priority on servers is servers based services, so I don't allocate priorities to "graphics."

It's light and it works... Locally, from the server... Or over ssh through X forwarding, and Xserver/Xclient, by app instance... not desktop forwarding. I have cron job scripts that if a problem, starts a temp instance of Xserver, returns Xmessage graphical messagebox prompts to my console, then ends the X instance... Even though I have these scripts sent me SMTP emails, I find these prompts more useful and timely than keeping an eye on my "service" email account.

---

### Post by tgalati4 on 2013-04-22
That is a very helpful script indeed.  Bookmarked for future reference.

---

