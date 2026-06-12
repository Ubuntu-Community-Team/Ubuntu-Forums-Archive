---
title: "NoMachine NX Shadowing on Serval Pro"
date: 2010-06-04
forum: System76 Support
---

### Post by volkerbradley on 2010-06-04
My new System76 laptop has 64 bit Ubuntu 10.04 installed.  I have used NoMachine NX in the past to allow other users to view my desktop and control it as needed.  This allows both of us to see the same session. This has always worked on my 32 bit systems.
For some reason, I do not see any shadowing sessions that another user can log into on my machine.  Everything else works fine.  Just the Shadowing does not work.
Do any of you have any suggestions on how to get this to work.
Is this possibly a problem because of the NVidia X Server?
Thanks

---

### Post by thomasaaron on 2010-06-04
We've put this issue on the whiteboard for testing. We typically don't test 3rd party software, but this one seems pretty interesting.

We have a tech coming on full-time next week, and he will start on the issue on Monday or Tuesday.

---

### Post by volkerbradley on 2010-06-12
It might help the new person to know the following:
After formatting the hard drive and installing Ubuntu 10.4 without proprietary drivers on the Serval Professional, shadowing with NX worked perfectly.  
Apparently, the problem is related to the proprietary drivers.

---

### Post by volkerbradley on 2010-06-12
I'm sorry that I bothered all of you.
Initially, when I viewed my /var/log/Xorg.0.log, I found the following error messages:
(II) NVIDIA(0): Creating default Display subsection in Screen section
        "Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) May 25 07:28:50 NVIDIA(0): Enabling RENDER acceleration
(II) May 25 07:28:50 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) May 25 07:28:50 NVIDIA(0):     enabled.
(EE) May 25 07:28:50 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) May 25 07:28:50 NVIDIA(0):     system's kernel log for additional error messages and
(EE) May 25 07:28:50 NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Recently I reinstalled the entire system and then reviewed the same log.
There are no error messages in the /var/log/Xorg.0.log.  Shadowing works perfectly.

---

### Post by volkerbradley on 2010-06-12
For those of you who support Linux users and would like them to have the ability to see the same session that you see, here is one way to do this:
sudo apt-get install apache2 ssh
Go to [http://www.nomachine.com/download.php](http://www.nomachine.com/download.php) and download nxclient_3.4.0-7_x86_64.deb, nxnode_3.4.0-11_x86_64.deb, nxserver_3.4.0-12_x86_64.deb, nxmanager_3.4.0-3_x86_64.deb
sudo dpkg -i nxclient_3.4.0-7_x86_64.deb nxnode_3.4.0-11_x86_64.deb nxserver_3.4.0-12_x86_64.deb nxmanager_3.4.0-3_x86_64.deb 
sudo chmod 755 /usr/lib/cups/backend/ipp
To check if the server is running, do:
sudo /usr/NX/bin/nxserver --status
Open up ~/.bashrc using your text editor and add this line
#EXTRA PATHS
export PATH=$PATH:/usr/NX/bin
sudo vi /usr/NX/etc/manager.cfg and change ApacheHTTPDReloadCommand = "/etc/init.d/apache2 graceful" to ApacheHTTPDReloadCommand = "/etc/init.d/apache2 reload"
sudo vi /etc/apache2/apache2.conf and add the following directive before the "Global Environment" section:
Include /usr/NX/etc/manager.conf
sudo /etc/init.d/apache2 restart
sudo cp /usr/NX/share/htdocs/nxmanager/images/shared/favicon.ico /var/www/
sudo chmod 767 /usr/NX/var/db/manager
sudo /usr/NX/bin/nxmanager --update
The permissions of /usr/NX/var/db/manager resets to 760 after the last two commands
Therefore give the following command again: 
sudo chmod 767 /usr/NX/var/db/manager
Log in with [http://localhost/nxmanager](http://localhost/nxmanager) with credentials of nxmanager/nxmanager
Once logged in, click on the + in front of localhost in the upper left corner
That will open the drop down menu
Click on Servers. A new section will pop up in the same page displaying the server list
Under the Server name will be the word: localhost
On the same line as localhost, to the far right is a small grey button.
Add a dot in that grey button and then click on the Modify button which is 2 lines below the grey button
Change the port to 22000
Create an Account with Administrative Privileges on the NX Server with
sudo /usr/NX/bin/nxserver --useradd yourusername --system --administrator
to add a regular user do:
sudo /usr/NX/bin/nxserver --useradd username 
To remove an NX user, the general form of the command is:
sudo /usr/NX/bin/nxserver --userdel USERNAME 
then sudo vi /etc/ssh/sshd_config  Under the line # What ports, IPs and protocols we listen for
Port 22
add: 
Port 22000
on a line below the Port 22 line
sudo /etc/init.d/ssh restart
To allow a user to log into the session and control it, do:
sudo vi /usr/NX/etc/server.cfg
remove the # symbol in front of the following lines:
EnableSessionShadowing = "1"
EnableInteractiveSessionShadowing = "1"
EnableSessionShadowingAuthorization = "1"
Now do:
 sudo /usr/NX/bin/nxserver --restart
Now should be able to log in with username on the Linux desktop with port 22000

If you know of a simple way for a user to do this on her or his machine so that you could see the same session that the user sees, please let us know.

---

