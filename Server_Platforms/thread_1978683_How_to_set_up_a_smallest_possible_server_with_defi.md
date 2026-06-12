---
title: "How to set up a smallest possible server with defined list of features?"
date: 2012-05-12
forum: Server Platforms
---

### Post by UlfDunkel on 2012-05-12
I am trying to set up a VPN client on the base of Ubuntu Server, with a defined list of features, but still don't succeed with all steps. I am quite sure that I have forgotten some stuff or do it the wrong way.

I don't want the following stuff to be done with Ubuntu Desktop, because it comes with too much overhead for the purpose. The whole system will be installed on a ThinClient PC hardware with smallest requirements.

Can you please check my list of features and help me through? This is, what the server should support:

Hardware requirements:
- smallest possible amount of RAM, e.g. 512 MB
- smallest possible drive space

System requirements:
- Ubuntu Server 12.04
- apache2
- php5
- openvpn
- openssh
- firefox (latest version)
- the smallest possible GUI for firefox
- probably a GUI account starter, e.g. lightdm, for autostart?

This "server" will become a VPN client later, which should be visible from a VPN server.

The VPN client "server" should behave like this when booting:
- start apache2 server with php5
- start vpn and ssh to be visible from the VPN server when the VPN client is online
- autostart the GUI with a non-root user account
- autostart Firefox in fullscreen mode
- have Firefox show a defined web page on [http://localhost/](http://localhost/)

I have already managed to set up such a machine which runs fine when I log in to the user account's CLI, then run startx, then run Firefox.

But whatever I do to add a greeter (like the now outdated gdm or lightdm), I fail to get the last three steps of my list assembled:

- autostart the GUI with a non-root user account
- autostart Firefox in fullscreen mode
- have Firefox show a defined web page on [http://localhost/](http://localhost/)

Now fire at will! :)

---

### Post by lewmnik on 2012-05-12
You have couple of options, but here is one without *DM 

You need to add the following line in your /etc/rc.local file.
```
su - <username> -c startx
```
before the line exit 0
Save and quit the file.
[Here]("http://linux.derkeiler.com/Newsgroups/comp.os.linux.x/2003-07/0373.html") is a bit more detail version.

That’s it. You are done. Now restart your system you will be magically taken right into your graphical desktop without you doing anything. Next time when your power goes up or your computer gets restarted accidentally, rest assured your system will boot nicely the way you want it to.

Autostarting firefox:
This all depend what DE you want? but LXDE or Flux are pretty small.
Command on the runlevel 5
```
firefox --fullscreen -url http://localhost
```

---

### Post by stmiller on 2012-05-12
You may be interested in the minimal cd. This is probably the absolutely most bare way to begin a custom Ubuntu install.

Installs with only minimal packages, then you can build on top of that. 

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by UlfDunkel on 2012-05-13
Thank you for your hints, [lewmnik]("http://ubuntuforums.org/member.php?u=54444"). I now managed to have the X environment start automatically after reboot, after I edited the /etc/rc.local file as recommended from you **and** after I changed /etc/X11/Xwrapper.config's parameter **allowed_users** from "console" to "anybody".

Now I don't understand what exactly I should do to do get firefox autostarting in runlevel 5 with your recommended command. As far as I understand, I should add another executable command file to /etc/init.d/ which contains this command, and which has a symbolic link in /etc/rc5.d/. Right?

I tried to create such a file but failed to have it automatically launch firefox after the X server has successfully been launched. Still stuck in the GUI CLI.

I wonder if I am on the wrong path again, or how this executable say "firefox" service file in /etc/init.d/ should look like. Can you please give me another hint?

---

### Post by UlfDunkel on 2012-05-13
@stmiller: Thank you for pointing me to MinimalCD. I will give it a try in the next instance when I have solved the other issues.

---

### Post by oldfred on 2012-05-13
I do not know much about servers, but have this in my notes. 

If running Firefox I would consider a bit more memory, especially with memory costs where they are now.

Kiosk discussions:
[http://ubuntuforums.org/showthread.php?t=1872560](http://ubuntuforums.org/showthread.php?t=1872560)
[http://ubuntuforums.org/showthread.php?t=1881141](http://ubuntuforums.org/showthread.php?t=1881141)
[http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/](http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/)
chromium kiosk using Tiny Core Linux. Talk about small and light!
[http://ubuntuforums.org/showthread.php?t=1891594](http://ubuntuforums.org/showthread.php?t=1891594)

---

### Post by UlfDunkel on 2012-05-14
@oldfred: Thanks for the links, but although they gave me a hint about  the kiosk mode which is probably something I'd have to add to my system,  I didn't find any hints about how to auto-start firefox once the X GUI  has been started with startx. @lewmnik has already recommended to put a  firefox launch service to /etc/init.d/ and nest it to runlevel 5, but I  don't really know how to.

---

### Post by UlfDunkel on 2012-05-14
I seem to have found a solution, using a command like this:

**X -ac  & firefox --display :0 & unclutter -idle 2 -display :0 & xset -display :0 -dpms s off**

When I run this command from the Terminal, X server launches Firefox as desired. But the fullscreen mode still leaves a small black border of about 30 pixels at the right and bottom of the screen. How can I run Firefox in real fullscreen mode, covering the whole screen?

---

### Post by UlfDunkel on 2012-05-16
It seems as if my setup still misses some windows management stuff,  because Firefox won't properly switch to fullscreen mode as it does in  Ubuntu Desktop. Will have to find out if adding a window manager (like  lightdm) will fix this.

---

