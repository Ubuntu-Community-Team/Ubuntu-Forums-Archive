---
title: "HOWTO: VNC server with resumable sessions on Xubuntu 16.04LTS"
date: 2016-11-07
forum: Tutorials
---

### Post by ebm342 on 2016-11-07
[SIZE=3]**[SIZE=3]Background[/SIZE]**
[/SIZE]
I have had a headless (without display) low power PC running ubuntu 12.04LTS for many years used mainly as a file and web server.  In order to administer the machine, I had a VNC server running with resumable sessions based mostly on this older tutorial:

[https://ubuntuforums.org/showthread.php?t=122402](https://ubuntuforums.org/showthread.php?t=122402)

This setup has always worked great for me but I figured after so many years, it was time to update the software in order to pick up new security patches and software versions.  When attempting to replicate the same configuration on 16.04LTS, I quickly discovered that the same setup that worked on 12.04LTS no longer works, and I believe it is due to the requirement that over a VNC session, the desktop runs in a 2D graphics mode, and the Unity-2D desktop was no longer available as of Ubuntu 14.04LTS.  I spent countless hours searching the web for alternate solutions, using different greeters or desktop sessions, and was never able to get a simple solution using software from the standard Ubuntu distribution.

My key requirements are that I wanted resumable sessions on a virtual display, meaning I wanted to get a GUI greeter login when the VNC session is connected, and I wanted to the session to persist across VNC disconnects and reconnects to the same port number, until the GUI session is explicitly logged out.  I also wanted the VNC session to not be the same as the local GUI session.  This allows multiple users to simultaneously connect to the server, each having their own unique resumable session.

I did note that many of the online tutorials mentioned using XFCE as the preferred desktop for VNC sessions.  But the more current online tutorials do not cover the complete topic of how to create a resumable sessions.

I finally figured out a simple way to implement what I wanted using Xubuntu 16.04LTS, and thought I’d share it in this forum.  The reason I chose to use Xubuntu is because it uses XFCE instead of Unity by default, which works fine over VNC.  There were a few little gotchas along the way that took me some time to figure out.  Hopefully, by documenting everything here, others will be able to get this working without having to go through the same headaches.

In order to keep things simple, I’ve written these instructions based on a fresh boot of a Live Xubuntu 16.04.1 environment.  [B]On a fresh hard drive installation (or existing installation) of Xubuntu 16.04.1, you can start from Step 3.
[/B]
[B][SIZE=3]Step 1: Boot into Xubuntu Live
[/SIZE][/B]
At the time of writing this, 16.04.1 is the latest LTS version of Xubuntu available, so that is the one I used.  There are many good online resources on how to get the downloaded ISO image onto a bootable USB drive.  Boot up from the USB drive and choose “Try Xubuntu without installing” to get into the Live (evaluation) desktop environment.  Get the internet connection configured (e.g. wireless) because you will need to download some packages later on.

[B][SIZE=3]Step 2: Disable Autologin on Xubuntu Live
[/SIZE][/B]
Autologin is enabled by default on Live sessions, meaning there is no authentication to get into the GUI desktop environment.  In order to set up VNC to greet you with a login window, autologin needs to be disabled.  Edit **/etc/lightdm/lightdm.conf** (e.g. sudo vi /etc/lightdm/lightdm.conf) and remove or comment out the autologin lines:

```
[SeatDefaults]
allow-guest=false
[COLOR=#0000ff]#autologin-guest=false
#autologin-user=xubuntu
#autologin-user-timeout=0[/COLOR]
```

By default, there is no password for the Xubuntu Live user, so for the sake of completion, choose a password by running “passwd”.  Restart lightdm:

```
sudo service lightdm restart
```

This will terminate the GUI session and restart it.  Verify that the greeter now prompts you for your login credentials.  The Xubuntu Live user is “xubuntu” and by default.  You can log into the desktop again.

[B][SIZE=3]Step 3: Enable XDMCP for lightdm
[/SIZE][/B]
XDMCP is the protocol that the VNC server will use to connect to the lightdm desktop manager.  Lightdm has XDMCP built-in, but it needs to be enabled.  Add a XDMCPServer section to** /etc/lightdm/lightdm.conf**.  On an Xubuntu Live session, lightdm.conf should now look like this:

```
[SeatDefaults]
allow-guest=false
#autologin-guest=false
#autologin-user=xubuntu
#autologin-user-timeout=0

[COLOR=#0000ff][XDMCPServer]
enabled=true[/COLOR]
```

Restart lightdm again for the new settings to take effect:

```
sudo service lightdm restart
```

You can log into the desktop again.

**[SIZE=3]Step 4: Install xinetd and VNC server[/SIZE]**

Ensure package indexes are up to date:

```
sudo apt-get update
```

Then install the xinetd and VNC server packages:

```
sudo apt-get install xinetd vnc4server
```

[B][SIZE=3]Step 5: Create a VNC password
[/SIZE][/B]
Create a password for the VNC connection.  This step is optional but I suggest creating a password unless you understand the implications of not having a VNC password.  The following command prompts you for the new password and stores the password in the** /root/.vncpasswd**.  You can choose to store the password in another location or have several password files (e.g., one for each user in the system), but for this tutorial, we will keep it simple with a single password.  Note that this password is used only to establish the VNC connection, but then the user will still need to login using the standard user account password.

```
sudo vncpasswd /root/.vncpasswd
```

**[SIZE=3]Step 6: Add the VNC service to xinetd[/SIZE]**

Create a new file **/etc/xinetd.d/Xvnc** and add the following contents:

```
service xvnc_1
{
    type = UNLISTED
    disable = no
    protocol = tcp
    socket_type = stream
    port = 5901
    wait = yes
    user = root
    server = /usr/bin/Xvnc
    server_args = :1 -inetd -query localhost -geometry 1280x1024 -depth 24 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
}
```

Some things to note… this creates an entry for a single resumable session.  The resolution of the virtual desktop is set by the geometry value in the server_args configuration variable.  The passwordFile value points to the VNC password file created in the previous step.

For multiple resumable sessions, the service block would be replicated, but the name “xvnc_1” would have to change (e.g. “xvnc_2”), and the port number would have to be different as well.  The port number chosen here is 5901 which is VNC display 1.  For VNC display 2, the port would be 5902, etc.  An example of a **/etc/xinetd.d/Xvnc** file configured for up to 3 simultaneous sessions is:

```
service xvnc_1
{
    type = UNLISTED
    disable = no
    protocol = tcp
    socket_type = stream
    port = 5901
    wait = yes
    user = root
    server = /usr/bin/Xvnc
    server_args = :1 -inetd -query localhost -geometry 1280x1024 -depth 24 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
}
service xvnc_2
{
    type = UNLISTED
    disable = no
    protocol = tcp
    socket_type = stream
    port = 5902
    wait = yes
    user = root
    server = /usr/bin/Xvnc
    server_args = :2 -inetd -query localhost -geometry 1280x1024 -depth 24 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
}
service xvnc_3
{
    type = UNLISTED
    disable = no
    protocol = tcp
    socket_type = stream
    port = 5903
    wait = yes
    user = root
    server = /usr/bin/Xvnc
    server_args = :3 -inetd -query localhost -geometry 1920x1080 -depth 24 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
}

```

Note that the port number and display number (:1, :2, :3) must be unique, and match up for each service.  Also, note that the resolution (geometry) can be different for each service.  You could also use a different vnc password file for each service.

Now restart xinetd to apply the new configuration file.  The proper sequence for restarting xinetd is to terminate the xinetd service, then terminate all Xvnc instances to ensure that the underlying Xvnc server restarts with the new settings, then start xinetd again.  This is accomplished with the following three commands:

```
sudo /etc/init.d/xinetd stop
sudo killall Xvnc
sudo /etc/init.d/xinetd start
```

Note that if there are no Xvnc instances running, the second command will produce a “Xvnc: no process found” message, which is OK.

**[SIZE=3]Step 7: Test the VNC connection[/SIZE]**

From another computer you should be able to VNC into your machine.  Or if you prefer to test locally, install the vncviewer:

    ```
sudo apt-get install xtightvncviewer
```

Then connect to the local machine using:

    ```
vncviewer localhost:1
```

Note the “:1” is the display VNC number.  It will prompt you for the VNC password.  If everything is working to this point, you should see the lightdm login greeter.  Login with your username and password (“xubuntu” on a Live Xubuntu system).  If the desktop appears, congratulations, you got past the major steps required to get this working.  Try logging out of the desktop.  The VNC window should close, and you can connect again.  Try logging in again...

[COLOR=#ff0000]*Wait, the VNC window just closed unexpectedly, what happened?! *[/COLOR] I discovered that on a new Xubuntu 16.04.1 system, there is possibly a bug in lightdm or one of its libraries whereby Xvnc only survives past the login greeter if it is the very first login to lightdm since lightdm restarted.  On subsequent logins, Xvnc terminates after the greeter authentication.  If this is happening to you, the fix is simple.  The version of lightdm that is included with Xubuntu 16.04.1 is version 1.18.2-0ubuntu1, and should be updated.  At the time of writing this tutorial, it can be updated to version 1.18.3-0ubuntu1.  Use the following commands to perform an upgrade of the lightdm package:

```
sudo apt-get update
sudo apt-get install lightdm
```

Now restart lightdm:

    ```
sudo service lightdm restart
```

Log into the desktop, and try connecting over vnc:

    ```
vncviewer localhost:1
```

This should bring you into the desktop environment.  Try logging out, then reconnecting over VNC again.  Everything should still work, which means the lightdm upgrade worked.  Try opening some windows in the workspace, then close the VNC connection without logging out, then connect again, and you will see that your workspace remains as you left it.

[B][SIZE=3]Step 8: Tab-autocomplete enhancement
[/SIZE][/B]
One problem I noticed is that when using XFCE over VNC, the TAB autocompletion does not work in terminal bash windows.  A bit of searching revealed the fix for this is to edit the** ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml** file.  Find the line that reads:


```
[COLOR=#ff0000]<property name="&lt;Super&gt;Tab" type="string" value="switch_window_key"/>[/COLOR]
```

and change it to:

```
[COLOR=#008000]<property name="&lt;Super&gt;Tab" type="empty"/>[/COLOR]
```

Restart the session and the TAB autocomplete in the terminal bash shell should work.

**[SIZE=3]Step 9: Lock screen enhancement[/SIZE]**

On VNC resumable sessions, it is often desirable to be able to lock the session and return to it later so that if someone else were to connect to the VNC server at your port number, and they knew the VNC password, they would still need to get past your Linux login credentials to access your session.

Starting from version 14.04, Xubuntu uses light-locker as the lock screen application.  Unfortunately, this lock screen application is not friendly to VNC sessions because in order to work, it needs to activate a new virtual terminal, which is not possible on a VNC session.  To get around this, you can disable light-locker and use gnome-screensaver instead, which doesn’t require a new virtual terminal.  I’m not familiar with the pros and cons of light-locker vs. gnome-screensaver, but the following are the steps to activate gnome-screensaver.  First install the package:

```
sudo apt-get install gnome-screensaver
```

Deactivate light-locker by doing the following.  Click on the XFCE menu, click “Settings” then open “Session and Startup”.  A “Session and Startup” window should appear.  Click on the “Application Autostart” tab.  Look for “Screen Locker (Launch screen locker program)” and uncheck it to disable “light-locker”.  Look for “Screensaver (Launch screensaver and locker program)” and check it to enable “gnome-screensaver”.  Log out and log back in.  The default lock icon should now do nothing.  To lock the screen, open a terminal and run the command:

```
gnome-screensaver-command -l 
```

*Disclaimer:* I was not able to get this to work on a Live Xubuntu system, but on a properly installed system, it did work for me.  A lightdm or system restart may be required after changing the XFCE settings.

Instead of manually running that command to lock the screen, you can create a shortcut to the command in the XFCE applications menu by creating** ~/.local/share/applications/lock_screen.desktop** with the following contents:

```
[Desktop Entry]
Version=1.0
Type=Application
Name=Lock Screen
Comment=
Exec=gnome-screensaver-command -l
Icon=changes-prevent
Path=
Terminal=false
StartupNotify=false
```


There are also other alternative methods to creating XFCE shortcuts, beyond the scope of this tutorial.

[B][SIZE=3]Conclusion
[/SIZE][/B]
I hope this tutorial has been helpful!  My apologies if there are any inaccuracies.  If you find any errors, please comment and I will try to correct them as soon as possible.

For those running a standard Ubuntu installation with Unity desktop, sorry, I only briefly tried to get that working by installing the xubuntu-desktop package and selecting the Xubuntu session from the Unity greeter, but I still got some Compiz or Unity errors that I was unable to resolve, so I gave up on it and went with the Xubuntu route instead.

Finally, if you’re running this on an untrusted network, it’s highly recommended you encrypt the VNC connection through an SSH tunnel or similar.  There are lots of online resources on how to do that as well.

---

