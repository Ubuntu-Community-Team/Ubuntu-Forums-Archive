---
title: "Disabling gnome-keyring"
date: 2008-05-16
forum: Security
---

### Post by Zibri on 2008-05-16
How do I disable (preferably remove) the gnome keyring manager? CLI approach please. apt-get remove is a no go, since remove the gnome-keyring package removes

apturl fast-user-switch-applet gdebi gdm gksu gnome-app-install gnome-keyring gnome-netstatus-applet gparted hwtest-gtk software-properties-gtk ubufox ubuntu-desktop update-manager update-notifier

of which most i don't use, but i don't know how removing gdm would effect my system.

---

### Post by HalPomeranz on 2008-05-16
I can't speak to turning off gnome-keyring-daemon completely, but I was able to disable it for SSH via gconf-editor.  Run gconf-editor and navigate to /apps/gnome-keyring/daemon-components.  You'll see checkboxes for both SSH and PKCS11 that you can unset.

---

### Post by Zibri on 2008-05-18
> **HalPomeranz said:**
> I can't speak to turning off gnome-keyring-daemon completely, but I was able to disable it for SSH via gconf-editor.  Run gconf-editor and navigate to /apps/gnome-keyring/daemon-components.  You'll see checkboxes for both SSH and PKCS11 that you can unset.

Thank you. Unfortunately it didn't work :/.

---

### Post by HalPomeranz on 2008-05-18
> **Zibri said:**
> Thank you. Unfortunately it didn't work :/.

"Didn't work" in what sense?  It might help if you gave a bit more info about what aspects/functionality of the gnome-keyring were getting in your way.

Like you, I'd love to get rid of this application completely, but as of this point all I've been able to figure out is how to disable the functionality that makes it most annoying to me.

---

### Post by Zibri on 2008-05-18
> **HalPomeranz said:**
> "Didn't work" in what sense?  It might help if you gave a bit more info about what aspects/functionality of the gnome-keyring were getting in your way.

Like you, I'd love to get rid of this application completely, but as of this point all I've been able to figure out is how to disable the functionality that makes it most annoying to me.

Ah, sorry.. The gnome-keyring-ask app is still launched when i use ssh with RSA. What did work, though, is to kill the daemon. However, i suspect I'll have to do this every time the system is rebooted (?) - don't know where it is started from.

---

### Post by HalPomeranz on 2008-05-18
> **Zibri said:**
> The gnome-keyring-ask app is still launched when i use ssh with RSA. What did work, though, is to kill the daemon. However, i suspect I'll have to do this every time the system is rebooted (?) - don't know where it is started from.

Weird, the gconf-editor hack totally worked for me as far as disabling the annoying gnome-keyring-ask popups.  Did you log out and log back in again after changing the setting with gconf-editor?  You'd have to do that to get the keyring daemon process to restart...

You're right that you'll have to kill the keyring daemon every time you reboot the machine-- in fact, you'll have to kill it every time you log out and log back into your windowing environment.  This doesn't seem like a long-term plan to me.

---

### Post by Zibri on 2008-05-22
Sorry for the delay, and thanks for your answer. No, i didn't logout, will try that when I'll get home. And, no, it's defintley not long term :P.

---

### Post by uplinkus on 2008-11-02
Click System->Preferences->Sessions click tab "Startup programs" then uncheck "GNOME keyring deamon wr..."

---

### Post by cosmolee on 2009-01-20
I don't see it in Startup Programs on either of two Ubuntu 8.04 Hardy systems.... :(

---

### Post by uzi09 on 2009-06-08
Instead of Startup Applications, try "Sessions" and then "Startup Applications" tab

---

### Post by ElQanah on 2010-06-29
For future reference, in case someone land here, follow this good tutorial:

[http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)

to make it short:

[LIST=1]
[*]Open up your Home Folder by clicking **Places>Home Folder**
[*]Press **CTRL-H** (or click View>Show Hidden Files)
[*]Find a folder called** .gnome2** (it has a period at  the beginning of the name) and open it by double clicking on it
[*]Inside of the .gnome2 folder, there is another folder called **keyrings**.   Open it up.
[*]Delete any files you find within the keyrings folder
[*]Restart the computer
[/LIST]
When prompted for a Keyring Password again, leave it blank and click [B]CREATE

[/B]_[COLOR=DarkRed]Thanks to David Steinlage[/COLOR]_

---

### Post by tlroche on 2011-03-12
> **ElQanah said:**
> 
[LIST=1]
[*]Open up your Home Folder by clicking **Places>Home Folder**
[*]Press **CTRL-H** (or click View>Show Hidden Files)
[*]Find a folder called** .gnome2** (it has a period at  the beginning of the name) and open it by double clicking on it
[*]Inside of the .gnome2 folder, there is another folder called **keyrings**.   Open it up.
[*]Delete any files you find within the keyrings folder
[/LIST]

Easier to do that with terminal one-liner:

```
$ rm ~/.gnome2/keyrings/*

```

> **ElQanah said:**
> [LIST=6]
[*]Restart the computer
[/LIST]

... and, while you're in the terminal, provided you're in group=Administrator, you can do

```
$ sudo shutdown -r now

```

> **ElQanah said:**
> 
When prompted for a Keyring Password again, leave it blank and click **CREATE**

Hmm ... I'm running 10.10=Maverick, and ...

The bad news: I get no such button: the only ones on the dialog are "OK" and "Cancel". The good news: after doing

[LIST=1]
[*]$ rm ~/.gnome2/keyrings/*
[*]$ sudo shutdown -r now
[*](after restart) Login.
[*]Enter network key in NetworkManager dialog.
[*]Hit button=Cancel in keyring dialog.
[/LIST]

I get no further keyring prompts until I change password (with Administration>Users and Groups). But what I really want is to disable gnome-keyring :-(

---

### Post by ZombiePriest on 2011-05-13
I would really appreciate information on how to remove this abomination too. Going the GUI way doesn't seem to solve the problem, although to make it less annoying, you can click on Details whenever it shows its ugly head and choose to have it bother you less. Not unlike the comfort you get from only having to put up with inlaws over holidays.

---

### Post by apacheman on 2011-06-03
> **tlroche said:**
> Easier to do that with terminal one-liner:

```
$ rm ~/.gnome2/keyrings/*

```

... and, while you're in the terminal, provided you're in group=Administrator, you can do

```
$ sudo shutdown -r now

```

Hmm ... I'm running 10.10=Maverick, and ...

The bad news: I get no such button: the only ones on the dialog are "OK" and "Cancel". The good news: after doing

[LIST=1]
[*]$ rm ~/.gnome2/keyrings/*
[*]$ sudo shutdown -r now
[*](after restart) Login.
[*]Enter network key in NetworkManager dialog.
[*]Hit button=Cancel in keyring dialog.
[/LIST]

I get no further keyring prompts until I change password (with Administration>Users and Groups). But what I really want is to disable gnome-keyring :-(


Thank you , Thank you, Thank you. 
Solved my problem. 
After i disliked unity and gnome3, I installed KDE in 11.04. But after restart, got this keyring problem, and couldn't log into desktop. Just got terminal running, and with your guide, it's working. 
Just that firefox has ugly font in its menus, but thats another problem
Thank you, once again.

---

### Post by mredude on 2013-02-22
My solution to this problem was unique and original. YAY!!! After trying everyone elses solution and just making the gnome desktop worse, I finally discovered that it was vino-server that was loading the gnome-keyring password prompt thing. Not a function of the gnome-keyring itself. So I went to [http://ftp.gnome.org/pub/GNOME/sources/vino/2.32/](http://ftp.gnome.org/pub/GNOME/sources/vino/2.32/) and got the source code to vino and compiled it with the ./configure --disable-gnome-keyring switch. I hoped I spelled all that right. a ./configure --help | list will list the correct switch to use. But it says --enable and not --disable but disable works. But I had to install the gnome-keyring-1 development libraries anyway even though it didn't use them. So anyways after I compiled vino and installed it, oh yeah, even though I did a make install the vino-server binary didn't get installed. A fight to the bitter end. So I had to manually copy that out of the source directory and I choose to put it into /usr/local/lib dir and make a symbolic link from the old vino-server, locate vino-server will tell ya where it is, something like /usr/lib/vino I think, to the new vino-sever. Rebooted. Had to turn remote desktop on again, and... and...

IT WORKED!!! No gnome-keyring password prompt when I log in with vnc to my :0 desktop.

---

### Post by cariboo on 2013-02-22
This is an old thread, and much has changed since it first started. If you want to start a discussion about what you've done, please start a new thread, as this one is closed

---

