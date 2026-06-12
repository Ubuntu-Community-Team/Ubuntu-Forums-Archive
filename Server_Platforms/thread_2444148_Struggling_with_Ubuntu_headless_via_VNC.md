---
title: "Struggling with Ubuntu headless via VNC"
date: 2020-05-25
forum: Server Platforms
---

### Post by richardi99 on 2020-05-25
[COLOR=#000000]Cannot seem to get VNC to start up at boot so I can VNC into this as a headless workstation. Have tried two things with no luck: [/COLOR][https://tecadmin.net/setup-x11vnc-se...ntu-linuxmint/]("https://tecadmin.net/setup-x11vnc-server-on-ubuntu-linuxmint/")[COLOR=#000000] and [/COLOR][https://c-nergy.be/blog/?p=10426](https://c-nergy.be/blog/?p=10426)[COLOR=#000000]. Any help appreciated.  Am using latest Ubuntu version on an Intel NUC.  All is fine - can VNC in from other PCs because I am running X11VNC server on my ubuntu box - until I reboot it, and then VNC doesn't load at boot.  So have to connect a monitor and login first, and then run x11vnc server.  Want VNC server to load at boot before logging a user in without this rigmarole.  Don't want to log into a user automatically on the ubuntu box before running X11VNC for security reasons.[/COLOR]

---

### Post by HermanAB on 2020-05-25
The simple solution is to use SSH instead.

---

### Post by TheFu on 2020-05-25
Or use **x2go**, which is a separate remote desktop tool that uses 100% virtual desktops, not tied to any hardware.  X2go is based on the NX protocol which is 2-3x faster than VNC and uses ssh tunnels as part of the NX protocol.

But i haven't tried this on either 18.04 or 20.04 ...  let me try 20.04 now.  Worked fine from a 16.04 client to a 20.04 x2go-server.  i use fvwm as the WM and it worked perfectly.

ssh is best, but there are times when a remote GUi app is needed too, just not for servers.

---

### Post by Tadaen_Sylvermane on 2020-05-25
[https://help.ubuntu.com/community/VNC/Servers](https://help.ubuntu.com/community/VNC/Servers)

This has some options. I posted about x11vnc on your other thread. I'm thinking that some options from this page may help you with it.

Also the way to autostart your server is with a systemd service. Posted one of those in your other thread as well for x11vnc.

> [COLOR=#333333][FONT=Ubuntu]To set x11vnc to continually listen for connections, include the [/FONT][/COLOR]**-forever**[COLOR=#333333][FONT=Ubuntu] option.

Didn't even know this was an option. Thanks for the question, made me look it up :).[/FONT][/COLOR]

---

### Post by richardi99 on 2020-05-26
Thanks! I already tried that with no luck - service doesn't start upon boot.  To be specific, below is the script I used.  Can you see anything wrong with this?  I also read here [http://c-nergy.be/blog/?p=12220](http://c-nergy.be/blog/?p=12220) that I need to disable Wayland Server for it to work.  Is that correct?

When I sudo systemctl status x11vnc.service, I see the following:```
x11vnc.service - Start x11vnc at startup.
     Loaded: loaded (/lib/systemd/system/x11vnc.service; enabled; vendor preset>
     Active: active (running) since Mon 2020-05-25 19:26:01 BST; 14h ago
   Main PID: 1628 (x11vnc)
      Tasks: 1 (limit: 18806)
     Memory: 15.1M
     CGroup: /system.slice/x11vnc.service
             &#9492;&#9472;1628 /usr/bin/x11vnc -auth guess -forever -loop -noxdamage -repe>
May 26 10:04:02 2SandhillHouse-NUC10i3FNK x11vnc[2735466]: 26/05/2020 10:04:02 >
May 26 10:04:02 2SandhillHouse-NUC10i3FNK x11vnc[2735482]: /tmp/fd.6ieM9s: 1: n>
May 26 10:04:02 2SandhillHouse-NUC10i3FNK x11vnc[2735511]: xauth:  unable to ge>
May 26 10:04:03 2SandhillHouse-NUC10i3FNK x11vnc[2735537]: /tmp/fd.6ieM9s: 1: n>
May 26 10:04:03 2SandhillHouse-NUC10i3FNK x11vnc[2735466]: 26/05/2020 10:04:03 >
May 26 10:04:03 2SandhillHouse-NUC10i3FNK x11vnc[2735466]: 26/05/2020 10:04:03 >
May 26 10:04:03 2SandhillHouse-NUC10i3FNK x11vnc[2735567]: /tmp/fd.gpU4FQ: 1: n>
May 26 10:04:03 2SandhillHouse-NUC10i3FNK x11vnc[2735466]: 26/05/2020 10:04:03 >
May 26 10:04:03 2SandhillHouse-NUC10i3FNK x11vnc[1628]:  --- x11vnc loop: sleep>
May 26 10:04:05 2SandhillHouse-NUC10i3FNK x11vnc[1628]:  --- x11vnc loop: 20466>
 ESCOC



```

Script:
```


# ##################################################################
# Script Name : vnc-startup.sh
# Description : Perform an automated install of X11Vnc
#               Configure it to run at startup of the machine            
# Date : Feb 2016
# Written by : Griffon 
# Web Site :[http://www.c-nergy.be](http://www.c-nergy.be) - [http://www.c-nergy.be/blog](http://www.c-nergy.be/blog)
# Version : 1.0
#
# Disclaimer : Script provided AS IS. Use it at your own risk....
#
# #################################################################


# Step 1 - Install X11VNC  
# ################################################################# 
sudo apt-get install x11vnc -y


# Step 2 - Specify Password to be used for VNC Connection 
# ################################################################# 


sudo x11vnc -storepasswd /etc/x11vnc.pass 




# Step 3 - Create the Service Unit File
# ################################################################# 


cat > /lib/systemd/system/x11vnc.service << EOF
[Unit]
Description=Start x11vnc at startup.
After=multi-user.target


[Service]
Type=simple
ExecStart=/usr/bin/x11vnc -auth guess -forever -loop -noxdamage -repeat -rfbauth /etc/x11vnc.pass -rfbport 5900 -shared


[Install]
WantedBy=multi-user.target
EOF


# Step 4 -Configure the Service 
# ################################################################ 


echo "Configure Services"
sudo systemctl enable x11vnc.service
sudo systemctl daemon-reload


sleep  5s
sudo shutdown -r now
```

---

### Post by slickymaster on 2020-05-26
*Thread moved to **Server Platforms**.*

---

### Post by richardi99 on 2020-05-27
I have tried various settings, but just cannot get this to start at boot.  I have to logon and manually start the VNC server.  Anyone?

---

### Post by richardi99 on 2020-05-29
For clarity, this is on Ubuntu desktop, not server.

---

### Post by LHammonds on 2020-05-29
I am not familiar with this particular scenario but I noticed the following in your "startup" script:

```
sudo apt-get install x11vnc -y
```

Do you really have to install the software every time you try to start it up?  Or is the script name just misleading?  The "install" should typically only happen one time.  If you are running this startup script every single time, you might be losing your previous configurations.

Have you checked the logs to see why it failed to autostart?

As an additional test, have you tried adding the startup command to root's crontab with the @reboot directive to see if it also fails from crontab start?

```

sudo crontab -u root -e

@reboot /usr/bin/systemctl start x11vnc
```

If the only time the server can start is when you are logged in, then I suspect a permissions issue.  Again, the logs might clarify this issue.

LHammonds

---

### Post by Tadaen_Sylvermane on 2020-05-29
I was just looking at your OP post again. If you intend to use this as a headless desktop then I would recommend against a full Ubuntu Gnome gui. You won't exactly get great performance with it over vnc. That and the wayland issue. I'd suggest using something simpler, Xubuntu maybe.

---

