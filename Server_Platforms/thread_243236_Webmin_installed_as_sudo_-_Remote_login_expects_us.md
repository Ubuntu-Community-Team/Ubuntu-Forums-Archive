---
title: "Webmin installed as sudo - Remote login expects user root"
date: 2006-08-24
forum: Server Platforms
---

### Post by magicgeorge on 2006-08-24
I've downloaded webmin from sourceforge.net into /usr/local/ and installed with the command: sudo dpkg -i webmin_1.290.deb. (This a basic LAMP install of Ubuntu)

The application says to login as root with the root password.  I can get to the logon screen using Firefox on a remote workstation using the server's ip address  but cannot successfully login.  I've tried my own user name, root, admin, etc. but nothing seems to work.  After numerous failed attempts it locked me out and I reinstalled Webmin on the server to clear it.

Searching Webmin documentation hasn't yielded an answer yet. Since Webmin seems a popular choice for server administration in Ubuntu, I'm hoping someone has some advice for a work around for the missing root user to get me started.

---

### Post by simonn on 2006-08-25
Personnally, I enabled root ([https://help.ubuntu.com/community/RootSudo)](https://help.ubuntu.com/community/RootSudo)).

I also install webmin from source (to /opt or /usr/local!) - it is easier to keep upgraded this way because webmin can actually upgrade itself and IME (albeit not with the ubuntu debs) webmin packages install every module - I only use a handful oif modules.

Some other security tips for when you do this though (particularily if the server is exposed to t'interweb):

If you are using ssh, disable root login by making sure PermitRootLogin is set to no in /etc/ssh/sshd_config.

Install [denyhosts](http://denyhosts.sourceforge.net/).

If you are using gnome, make sure that root cannot log into gnome by making sure AllowRoot=false is in the [security] section of /etc/X11/gdm/gdm.conf.

In webmin, go to Webmin -> Webmin Configuration -> Authentication and "Enable password timeouts". I "Block hosts with more than 3 failed logins for 900 seconds." and log any attempts (not that there have been any in the 4 years or so I have been running webmin). It would be very time consuming to brute force if an attacker gets blocked for 15 minutes after 3 incorrect attempts. They may think they have been blocked for longer so give up and if there are continuing attacks from certian ip addresses or subnets, you can block that ip or subnet with ip tables.

Do not run any servers/daemons as root unless they NEED to be.

---

### Post by SlowYaRoll on 2006-09-19
Here's another way to install webmin, which is very simple. This should apply to all Ubuntu versions, but then again, I'm still very new to Linux.

Download the webmin DEB file from Webmin's website.
([http://www.webmin.com](http://www.webmin.com))
([http://www.webmin.com/download.html](http://www.webmin.com/download.html))

Go to the directory where you've downloaded the DEB file.
(i.e. cd /home/usernamehere/Desktop/)

Run the dpkg --install command on the DEB file you've downloaded.
(i.e. sudo dpkg --install webmin_1.290.deb)

----This will take a few moments to install----

At this point, webmin is installed and running. You may access Webmin via your web browser.
([http://localhost:10000)](http://localhost:10000)).

You'll be prompted for a username and password. By default, Webmin copies your system's root password as the Webmin root password. Since the Ubuntu installation never prompts you to set a root password, you are unable to enter the root password.

To fix this problem, run the following command:
sudo /usr/libexec/webmin/changepass.pl /etc/webmin root enterpasswordhere

You should now be able to log into Webmin with the username root and whatever you've set as the password.

---

