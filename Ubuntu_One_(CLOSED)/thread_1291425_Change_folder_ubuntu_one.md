---
title: "Change folder ubuntu one"
date: 2009-10-14
forum: Ubuntu One (CLOSED)
---

### Post by Sashin on 2009-10-14
Anyone know how to change the folder ubuntu one uses from ~/ubuntu one to ~/.ubuntu one or something less in the way?

---

### Post by osomphane on 2009-10-14
They are currently working on the ability to use different folders.

---

### Post by Sashin on 2009-10-14
Will it be done by Karmic, seems like a pretty basic feature to be honest.

---

### Post by joshuahoover on 2009-10-15
> **Sashin said:**
> Will it be done by Karmic, seems like a pretty basic feature to be honest.

We will not provide the ability to sync folders outside the ~/Ubuntu One/ folder for Karmic. We have this on our to-do list for Lucid and will make it available in our beta PPA for those interested in testing out the functionality before Lucid is released.

---

### Post by venik212 on 2010-01-10
1--I think others have this problem: I have karmic running on my computer, and have registered for ubuntu one, but I cannot find the folder (like the dropbox folder).  Where is it?  It is NOT in my home folder.  I know it exists since I have moved files into it with a browser.

2-- Moving or copying one file at a time renders the whole thing nearly useless.  When will we be able to move folders into the ubuntu one space?

---

### Post by thebear78 on 2010-01-12
> **venik212 said:**
> 1--I think others have this problem: I have karmic running on my computer, and have registered for ubuntu one, but I cannot find the folder (like the dropbox folder).  Where is it?  It is NOT in my home folder.  I know it exists since I have moved files into it with a browser.

Have you run the desktop client (Applications >> Internet >> Ubuntu One) to authenticate your computer to sync with the Ubuntu One cloud?

---

### Post by venik212 on 2010-01-12
I tried to run that program from the terminal, but it kept telling me that the program is not found.  I certainly have an ubuntu one account, but I still have been unable to run the program.
I am not surprised, though-- I find karmic to be rather buggy and unstable

---

### Post by thebear78 on 2010-01-12
Try this to re-install Ubuntu One: [https://answers.edge.launchpad.net/ubuntuone-client/+faq/778](https://answers.edge.launchpad.net/ubuntuone-client/+faq/778)

---

### Post by syntaxer on 2010-01-31
I guess I've found a way to change the U1's folder, although I didn't test it properly (so keep in mind you can loose your files etc.).

In **~/.config/ubuntuone** there is a file **syncdaemon.conf**.
Just add the following code at the beginning of the file (above [bandwidth_throttling]):
```

[__main__]
root_dir = ~/new/folder

```
Of course, replace ~/new/folder by the desired location, e.g. ~/.ubuntuone

---

### Post by DouglasAdams on 2010-02-13
i don't seem to have the folder
~/.config/ubuntuone
referred to above on my karmic/gnome system.
i can see lots of other basic stuff there, such as tomboy, plus things i've added like google chrome.
so i did a reinstall of the four items shown by a synaptic search for ubuntuone plus i even added the client tools.
yet the folder still isn't there.
any thoughts please?

---

### Post by syntaxer on 2010-02-15
> **DouglasAdams said:**
> i don't seem to have the folder
~/.config/ubuntuone
referred to above on my karmic/gnome system.

The folder is created once you run and configure Ubuntu One. Connect your machine, exit Ubuntu One and check the configuration.

---

### Post by DouglasAdams on 2010-02-15
thanks syntaxer

---

### Post by Rig'dzin Dorje on 2010-10-12
[FONT=Times New Roman][SIZE=4]I appreciate being able to sync folders other than Ubuntu One. But I find there is no option to do this on an external hard drive. Is there anything I can tweak so as to make the sync option work on the external drive? I'd like to be able to do that so I can keep archived material off the hard disk and back it up to the cloud. It would be in Ubuntu's interest to make this possible as I'd buy more online storage space![/SIZE][/FONT]

---

### Post by mr.interested on 2010-12-31
> **syntaxer said:**
> In **~/.config/ubuntuone** there is a file **syncdaemon.conf**.
Just add the following code at the beginning of the file (above [bandwidth_throttling]):
```

[__main__]
root_dir = ~/new/folder

```

It doesn't work in Ubuntu 10.10. The client restores "syncdaemon.conf" file to its original form whenever I close the file. I guess the file is generated automatically by the client; therefore, you can't edit it.

---

### Post by syntaxer on 2011-01-01
> **mr.interested said:**
> It doesn't work in Ubuntu 10.10. The client restores "syncdaemon.conf" file to its original form whenever I close the file. I guess the file is generated automatically by the client; therefore, you can't edit it.

Have you killed the client (e.g. using [FONT="monospace"]u1sdtool -q[/FONT]) and then edited the file? It's common that configuration is being overriden by the running daemon.

---

### Post by suffice on 2011-03-16
This worked perfectly for me on my home computer into ~/SYNC. Easy no hassles.

It is not working at all on my work computer.

I tried the uninstall and purged everything.  Re-installed.  Changed the file.

The file is correct, with the main section but it still is syncing the to ~/Ubuntu One. (from ~/SYNC at my house.

Any other tricks to force it to use the directory mentioned in ~/.config/syncdaemon.conf?

Strange that it completely worked on one computer and not the other. Generally they are configured pretty much the exact same.

---

### Post by Kleenux on 2011-05-23
Using Ubuntu 11.04

Note that the global file is```
/etc/xdg/ubuntuone/syncdaemon.conf
```but (didn't try) the local file mentioned above```
~/.config/ubuntuone/syncdaemon.conf
```may override the global settings.

---

### Post by richaustin on 2011-07-29
Hi

By far the easiest way to change the Ubuntu One folder to anywhere you want is to use a symlink. For example, I just moved my Ubuntu One from /home/richard/Ubuntu One to /data/Ubuntu One - where /data references a partition on my hard drive.

All I did was:
1) Disconnect Ubuntu One - its an option in the main Ubuntu One panel.

2) Move the original Ubuntu One folder from my home folder to the /data partition. 
Of course this could be an external drive or whatever you want to use. Quite feasible I would think to use the same Ubuntu One on a number of different machines by using a symlink to the external drive.

3) Right click on the new /data/Ubuntu One folder and select "Make Link". Move the symlink to the home folder and rename it to "Ubuntu One". 

4) Reconnect Ubuntu One.

So now I have the following:

/data/Ubuntu One - the real Ubuntu One folder on a partition.
/home/richard/Ubuntu One - A symlink to the /data/Ubuntu One folder.

Very simple and works perfectly.

Hope this helps someone.
Rich

---

### Post by VcDeveloper on 2011-07-29
I have not read all the post, but is the ability to map more than just the default folder available?  I would like to sync my Drupal documents folder.

Or would I have to create a folder under it and symlink them or could this even work?

....well, it seems the linking a folder from the folder doesn't work, so this means I have to move all my folders that I want to sync to this folder?

---

### Post by richaustin on 2011-07-30
> **VcDeveloper said:**
> I have not read all the post, but is the ability to map more than just the default folder available?  I would like to sync my Drupal documents folder.

Or would I have to create a folder under it and symlink them or could this even work?

....well, it seems the linking a folder from the folder doesn't work, so this means I have to move all my folders that I want to sync to this folder?

I'm not at all sure why but it doesn't work when you add a link into Ubuntu One. Something to do with permissions maybe?

However, it works perfectly in Dropbox - much the same thing as Ubuntu One if you haven't tried it. I just did a test by creating a symlink from my apache installation to Dropbox (same sort of thing as you want to do with Drupal I think) and it synchronised straight away. Ubuntu One wouldn't let me do the same thing.

Dropbox is excellent and free up to 2GB. 

[https://www.dropbox.com/downloading?os=lnx](https://www.dropbox.com/downloading?os=lnx)

By the way, I always use repositories to backup things like Drupal. Check out [http://unfuddle.com/](http://unfuddle.com/) which is free, handles Git and Subversion repositories and you can have as many as you like. I use it for all my code, websites and document backups. I use RapidSVN as my front end GUI and RabbitVCS support in Nautilus (so you can update folders etc. in the Nautilus file manager). Subversion is pretty easy to use, and I guess Git is as wel but I haven't used it.

Rich

---

### Post by ionutneicu on 2012-06-18
Another way that may be helpful if you want to save some space from home partition is to move the entire Ubuntu One folder to another location then create symlink to it's original location.  Worked for me in Ubuntu 10.10:

The steps are :

1. Stop Ubuntu One sync daemon

 [FONT=Courier New]u1sdtool --quitu1sdtool --quit[/FONT]

2. Copy te ~/Ubuntu\ One folder elsewhere

 [FONT=Courier New]mv ~/Ubuntu\ One  [otherdirectory][/FONT]

3. Create symbolic link from new location back to its default location

  [FONT=Courier New]ln -s [otherdirectory] ~/Ubuntu\ One[/FONT]

4. Restart Ubuntu One sync daemon
    
[FONT=Courier New]u1sdtool --start[/FONT]

---

### Post by archeryguru2000 on 2012-07-23
> **syntaxer said:**
> I guess I've found a way to change the U1's folder, although I didn't test it properly (so keep in mind you can loose your files etc.).

In **~/.config/ubuntuone** there is a file **syncdaemon.conf**.
Just add the following code at the beginning of the file (above [bandwidth_throttling]):
```

[__main__]
root_dir = ~/new/folder

```
Of course, replace ~/new/folder by the desired location, e.g. ~/.ubuntuone

In case anybody is still searching for a solution to the original post, this method worked seamlessly for me.

First I disconnected my U1 synchronization:

[IMG]https://dl.dropbox.com/u/92330982/2012-07-23-104233_400x516_scrot.png[/IMG]

Next added the above line to the above config file.  And finally I restarted the U1 daemon and voila!

[IMG]https://dl.dropbox.com/u/92330982/2012-07-23-104421_400x516_scrot.png[/IMG]

You may have to restart after you chose to connect to apply the new settings.  Good luck.

---

### Post by archeryguru2000 on 2012-07-23
Just as a side note, from the above post, you may also use the cli to quit/start/connect/etc. the U1 daemon.

To disconnect:
```

$: u1sdtool --disconnect

```

To Connect:
```

$: u1sdtool --connect

```

To quit:
```

$: u1sdtool --quit

```

To restart:
```

$: u1sdtool --start

```

Other option are available as well.  Just check the man pages with
```

$: man u1sdtool

```

---

### Post by chmegr on 2013-01-23
I just got a new bonobo extreme with a 2nd internal hard drive. I am looking to put all my files (UB1 & dropbox, etc) on one (240GB) and just leave the other for the OS. 

How would I go about doing this, so UB1 and dropbox can sync from the 2nd hard drive that the OS is not on?

Thanks in advance

---

### Post by archeryguru2000 on 2013-01-24
> **chmegr said:**
> I just got a new bonobo extreme with a 2nd internal hard drive. I am looking to put all my files (UB1 & dropbox, etc) on one (240GB) and just leave the other for the OS. 

How would I go about doing this, so UB1 and dropbox can sync from the 2nd hard drive that the OS is not on?

Thanks in advance

For me, DropBox was extremely easy to move to a different location. Here's a link to some information on DropBox's help pages.

[[COLOR="Blue"]_DropBox Migration_[/COLOR]]("https://www.dropbox.com/help/89/en")

[COLOR="Red"]AS A NOTE OF CAUTION[/COLOR]: make sure you do not disconnect (unmount, etc.) your drive without first disconnecting (or unsyncing) your DropBox account.  Otherwise you may inadvertently delete your online documents since DropBox always tries to keep its synchronization up to date.

As for UbuntuOne, I had many challenges with syncing my new (non-home drive) location with my online account.  I must admit that I've recently switched to putting my UbuntuOne folder *back* into my home drive.  I have not tried to sym-link as many others have suggested.  However, there seems to be some "issues" with this method as well.  Sorry I couldn't be of more assistance.

---

### Post by chmegr on 2013-01-24
> **archeryguru2000 said:**
> For me, DropBox was extremely easy to move to a different location. Here's a link to some information on DropBox's help pages.

[[COLOR=Blue]_DropBox Migration_[/COLOR]]("https://www.dropbox.com/help/89/en")

[COLOR=Red]AS A NOTE OF CAUTION[/COLOR]: make sure you do not disconnect (unmount, etc.) your drive without first disconnecting (or unsyncing) your DropBox account.  Otherwise you may inadvertently delete your online documents since DropBox always tries to keep its synchronization up to date.

As for UbuntuOne, I had many challenges with syncing my new (non-home drive) location with my online account.  I must admit that I've recently switched to putting my UbuntuOne folder *back* into my home drive.  I have not tried to sym-link as many others have suggested.  However, there seems to be some "issues" with this method as well.  Sorry I couldn't be of more assistance.

Thanks....yeah, UbuntuOne seems like a pain and I have a lot more space in my dropbox folder anyway.

---

### Post by chmegr on 2013-01-24
> **archeryguru2000 said:**
> For me, DropBox was extremely easy to move to a different location. Here's a link to some information on DropBox's help pages.

[[COLOR=Blue]_DropBox Migration_[/COLOR]]("https://www.dropbox.com/help/89/en")

[COLOR=Red]AS A NOTE OF CAUTION[/COLOR]: make sure you do not disconnect (unmount, etc.) your drive without first disconnecting (or unsyncing) your DropBox account.  Otherwise you may inadvertently delete your online documents since DropBox always tries to keep its synchronization up to date.

As for UbuntuOne, I had many challenges with syncing my new (non-home drive) location with my online account.  I must admit that I've recently switched to putting my UbuntuOne folder *back* into my home drive.  I have not tried to sym-link as many others have suggested.  However, there seems to be some "issues" with this method as well.  Sorry I couldn't be of more assistance.

So I gave this a try and even though the original dropbox folder is in home/username/dropbox and my new location (2nd internal hard drive) is media/username/2nd hard drive it will not work. It tells me that my target folder is my current dropbox folder.

I tried creating another differently named folder on my second hard drive to put the dropbox folder in, and this also did not work. :confused:

---

