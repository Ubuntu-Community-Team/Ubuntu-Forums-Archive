---
title: "Problems &quot;installing&quot; UbuntuOne"
date: 2012-05-25
forum: Ubuntu One (CLOSED)
---

### Post by lurker9876 on 2012-05-25
I got a new System76 laptop a few days ago.  Installed with ubuntu 12.04.  Ubuntuone is installed as per software center.  However, when I click on the ubuntuone icon in the launcher, it prompts me for my password, then it completed its installed (as per the sliding status bar) but then it hangs.  Nothing happens after that.  I don't get the control panel that asks me for my ubuntuone account information.

How do I fix this problem?

Thanks!

---

### Post by lurker9876 on 2012-05-26
Ok, let me try another explanation.

After the sliding status bar turns 100 percent orange, nothing happens after that.  It just sits there.  If I close the window, the process is repeated.  I never get the control panel with the login prompts.  Only get the control panel that says "Install" or cancel.

I don't understand that in the software center, it says that it and its control panel are installed but when I click on the shopping bag icon in the launcher, it brings up the control pane asking me to install.

So it's installed but not installed????

---

### Post by lurker9876 on 2012-05-26
Looks like not all dependencies have been resolved.

Something about python-qt4?  

The more I install something in the software center, it fails because not all of the dependencies are there.

Does someone have a PPA that has the full package of ubuntuone for 12.04 Precise with all dependencies resolved that I can install from?

---

### Post by lurker9876 on 2012-05-26
I finally ran ubuntuone-installer from CLI and got the following messages:

The following packages have unmet dependencies:

ubuntuone-control-panel-qt: Depends: python (< 2.8) but 2.7.3-0ubuntu2 is to be installed
                            Depends: python-ubuntuone-control-panel (= 3.0.0-0ubuntu1) but 3.0.0-0ubuntu1 is to be installed
                            Depends: ubuntuone-control-panel (= 3.0.0-0ubuntu1) but 3.0.0-0ubuntu1 is to be installed
                            Depends: ubuntuone-control-panel-common (= 3.0.0-0ubuntu1) but 3.0.0-0ubuntu1 is to be installed

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/ubuntuone-installer/ubuntuone/installer/gui.py", line 373, in finished
    GLib.spawn_command_line_async(CONTROL_PANEL_COMMAND)
  File "/usr/lib/python2.7/dist-packages/gi/types.py", line 43, in function
    return info.invoke(*args, **kwargs)
gi._glib.GError: Failed to execute child process "ubuntuone-control-panel-qt" (No such file or directory)

I tried to resolve all of the dependencies to no avail.  For example, I did:  sudo apt-get install ubuntuone-control-panel-qt and get:  

The following packages have unmet dependencies:
 ubuntuone-control-panel-qt : Depends: python-qt4 but it is not going to be installed
                              Depends: ubuntu-sso-client-qt (>= 2.99.92) but it is not going to be installed

---

### Post by lurker9876 on 2012-05-26
I even tried to install python-qt4 from the software center but it fails because of numerous library dependencies.  Then I'd try install some of these libraries but run into problems.

---

### Post by egeezer on 2012-06-01
I would say this tells you a lot about how much to trust Ubuntu One.

---

### Post by archimedes1981 on 2013-01-25
So anyone fixed this? I got this problem ! :(

---

### Post by besial on 2013-01-26
> **egeezer said:**
> I would say this tells you a lot about how much to trust Ubuntu One.
This is the main reason why I don't use Ubuntu One.

---

### Post by yohoho46 on 2013-02-18
I too have issues with all attempts to install the client.  Regardless of using synaptic, the installer, or the latest ppa the result is the same.  At least one dependency is impossible to resolve or the client will not start.

I would have to agree that at this point ubuntu one is crapware.  The other side of the coin dropbox is lame, and sugarsync still does not support linux.

This is the part that really craps in my nest.  I stay with the LTS verison BECAUSE I DONT WANT TO HAVE TO DEAL WITH THIS KIND OF CRAP.

---

