---
title: "Configure VNC to access Ubuntu GUI - connection refused"
date: 2013-11-20
forum: Virtualisation
---

### Post by prayner.basil on 2013-11-20
Hi
not sure if this is the right place for this. BTW...I am a noob.

I installed Xen Server 6.2 on a home PC. As a VM, I then installed Ubuntu 12.04 server 64bit. I can access this from a Win XP machine using the XenCentre Client.

However, the terminal and I "aren't close friends" and I'd like to be able to access the Ubuntu installation via a GUI.

Here's what I did from the terminal:

[LIST]
[*]Installed x11vnc
[*]created a script in /etc/init/x11vnc.conf[COLOR=#666666][FONT=Verdana]script[/FONT][/COLOR]
[*][COLOR=#666666][FONT=Verdana][/FONT][/COLOR][COLOR=#666666][FONT=Verdana]x11vnc -xkb -noxrecord -noxfixes -noxdamage -display :0 -auth /var/run/lightdm/root/:0 -forever -bg -o /var/log/x11vnc.log
[/FONT][/COLOR]
[COLOR=#666666][FONT=Verdana][/FONT][/COLOR][COLOR=#666666][FONT=Verdana]end script  
[/FONT][/COLOR]

[*]installed lightdm
[*]changed permission on that file [COLOR=#4E4E4E][FONT=Verdana]sudo chmod 660 /etc/x11vnc/x11vnc.pass[/FONT][/COLOR]
[*]enabled ufw
[*]enabled default ports for VNC
sudo ufw allow 5800/tcp   
sudo ufw allow 5900/tcp
sudo ufw allow 6000/tcp
[/LIST]


When I try to use VNC viewer to 192.168.1.103:0 it gives an error - Connection refused (10061).

There is a lot on the web about this problem - I've trawled through a lot of it, without resolving the issue (I know it will be operator). I've hung around the IRC channels to get assistance without luck.

I'd appreciate any advice you may be able to give.

Paul

---

### Post by steeldriver on 2013-11-20
I have no experience with Xen - is the default networking bridged or NAT? can you actually see the server form the LAN (i.e. is the VM IP address 192.168.1.103 on the same LAN segment as your host?). Can you ping it?

What actual desktop session(s) are installed (the full ubuntu-desktop?)

Personally x11vnc+lightdm sound like the wrong tools for the job - for basic GUI access to a "server" most people would do something like a simple X session (e.g. LXDE) run via vnc4server / tightvncserver / freenx. In particular, x11vnc is really aimed at desktop sharing applications (it is designed to 'allow VNC connections to real X11 displays') so may have issues in a headless situation.

---

### Post by houstonbofh on 2013-11-20
if, from the terminal, you type "sudo apt-get install ubuntu-desktop" you get the full Ubuntu desktop.  From there you can enable VNC...  I suspect you do not have VNC properly configured.

---

### Post by prayner.basil on 2013-11-21
I ran with steeldrivers observation that I may have been using the wrong tools.
Followed the instructions at [http://myhosting.com/wiki/index.php?/article/AA-04694/0/Ubuntu-VPS-Desktop-LXDE-Installation-and-VNC.html](http://myhosting.com/wiki/index.php?/article/AA-04694/0/Ubuntu-VPS-Desktop-LXDE-Installation-and-VNC.html), to install LXDE and vncserver.

At the point where I need to load LXDE when the programme loads, I used:
[COLOR=#000000][FONT=Arial][FONT=courier new]**nano ~/.vnc/xstartup**[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]# Edit the file or replace its contents so that they look like the code below and save[/FONT][/COLOR]
#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc
lxsession -s LXDE &

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
# x-window-manager &

When I go to start vncserver, the errors in my terminal look like:

root@ubuntu:~# service vncserver restart
/etc/init.d/vncserver: line 8: unset: `VNCSERVERS=': not a valid identifier
/etc/init.d/vncserver: line 8: unset: `[': not a valid identifier
/etc/init.d/vncserver: line 8: unset: `-f': not a valid identifier
/etc/init.d/vncserver: line 8: unset: `/etc/vncserver/vncservers.conf': not a valid identifier
/etc/init.d/vncserver: line 8: unset: `]': not a valid identifier
/etc/init.d/vncserver: line 9: syntax error near unexpected token `&&'
/etc/init.d/vncserver: line 9: `&& . /etc/vncserver/vncservers.conf prog=$"VNC server" start() {'


I'd appreciate any advice.

---

