---
title: "HOWTO: Render the universal access preferences on the login screen useless"
date: 2011-06-04
forum: Tutorials
---

### Post by not_insane on 2011-06-04
Hi,
I've been trying to do this (since some of my friends can be immature at times and I don't believe myself to be visually impaired) and I just couldn't seem to find a tutorial for it. I isolated the Universal Access icon to gnome-settings-daemon, and stopping gnome-settings-daemon makes the login screen unthemed and you see artifacts on the screen where the background should be (try moving /usr/share/gdm/autostart/LoginWindow/gnome-settings-daemon.desktop someplace else and restarting gdm, and you'll see what I mean.

Anyway, this is a dirty trick we can pull off to make it useless. This will _not_ make the icon go away, instead it will force the universal access preferences dialog to close when someone tries to open it.

Step 1. We will be using a root terminal, so open up a normal terminal and enter "sudo -i" (without quotes) to get a root shell. After doing this, we will need a program called wmctrl which is not installed by default. Run the command "apt-get install wmctrl" to install it. this program allows us to control windows from terminal.

Step 2. Ok, we have the tools for the job now. Enter the command "cd /usr/share/gdm/autostart && nano nouniversal.py" This will open up a text editor. Copy the following code and paste it in the terminal by selecting the terminal and pressing ctrl+shift+v:
```
#!/usr/bin/env python
import os
from threading import Thread
import time
import commands

time.sleep(1)

while 1:
    proc = commands.getoutput('ps aux|grep gnome-settings-daemon|grep -v grep|grep gdm')
    if 'gnome-settings-daemon' in proc:
        os.system("wmctrl -F -c 'Universal Access Preferences'")
    else:
        os._exit(0)
    time.sleep(0.0001)

```Step 3. We have just created the script that will close the dialog for us if someone tries to open it. We now need to make sure it runs on the login screen. Enter the command "cd LoginWindow&&nano nouniversal.desktop" and copy and paste the following code in (ctrl+c from your browser and ctrl+shift+v into the terminal):
```
[Desktop Entry]
Type=Application
Name=Bye Bye UAP
Exec=python /usr/share/gdm/autostart/nouniversal.py
OnlyShowIn=GNOME;
X-GNOME-Autostart-Phase=Application
X-GNOME-Autostart-Notify=true
X-GNOME-AutoRestart=true
X-Ubuntu-Gettext-Domain=gdm

```I based it off one of the other scripts in that directory. It is safe to remove or move elsewhere the files gnome-mag.desktop, onboard.desktop and orca-screen-reader.desktop from that folder to strip the functionality from the universal access preferences dialog.

Step 4. We're done. Now close your programs and reboot! You should see that when you try to open the universal access preferences dialog, it should close itself before responding to any input.

Thanks for reading, I posted this to save others from the frustration of not finding anything on google! Obviously this does not actually get rid of the icon or disable the preferences dialog, it just closes it when someone tries to open it - if anyone has a better solution, please do post it!

---

### Post by afixxxer on 2011-08-06
Hi, your solution looks great and it works.

But I found another alternative solucion:

sudo mv  /usr/lib/gnome-settings-daemon-2.0/a11y-keyboard.gnome-settings-plugin /usr/lib/gnome-settings-daemon-2.0/a11y-keyboard.gnome-settings-plugin.bak

Restart gdm:
sudo service gdm stop
sudo service gdm start

This made the icon totally was disappeared.

Works on Ubuntu 10.10 and 11.04

Regards

---

