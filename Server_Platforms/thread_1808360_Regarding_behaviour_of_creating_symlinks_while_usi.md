---
title: "Regarding behaviour of creating symlinks while using sshfs"
date: 2011-07-20
forum: Server Platforms
---

### Post by WitchCraft on 2011-07-20
Question:
The behaviour of nautilus when creating symlinks in a folder mounted via sshfs is questionable, at best.

The story that explains what's wrong goes like this:

I wanted configure multiple virtual hosts for my nginx webserver.
To do so, I mounted the root directory of the webserver (I mean the all directories root, not the wwwroot) via sshfs, so I could create/edit the config textfile on my local computer, where there is Xorg installed, using a GUI editor using the mouse and copy/paste of some samples from the webbrowser (the webserver is console only).


I mounted the root directory of the remote system (webserver) to directory
```

/mnt/sshfs

```

Then I created a nginx virtual host file (on the webserver) in folder
```

/etc/nginx/SomeSubFolderForAvailableVirtualHostConfigFiles

```


Then one still has to make nginx to actually switch this config online.


To do this, one has to make a symlink from 
```

/etc/nginx/SomeSubFolderForAvailableVirtualHostConfigFiles/somefile.cfg

```
to
```

/etc/nginx/SymlinkSubFolderForActiveVirtualHostConfigurations/somefile.cfg (symlink)

```

(on the webserver)


Now when creating such a symlink in the folder mounted via sshfs (in folder /mnt/sshfs/ on the local machine that accesses the webserver via sshfs)
,using Nautilus, in this folder (mounted in /mnt/sshfs):
```

/etc/nginx/SymlinkSubFolderForActiveVirtualHostConfigurations 

```

it creates a symlink to 
```

/mnt/sshfs/etc/nginx/SomeSubFolderForAvailableVirtualHostConfigFiles/thisfile.cfg

```

It took me something between 15 to 30 minutes to realize that the link created with sshfs was the reason my config file never got loaded. Because on the remote server, there of course is no file 
```

/mnt/sshfs/etc/nginx/SomeSubFolderForAvailableVirtualHostConfigFiles/thisfile.cfg

```
There only is
```

/etc/nginx/SomeSubFolderForAvailableVirtualHostConfigFiles/thisfile.cfg

```
...

Nautilus should prompt whether to create a link locally or remotely, when the target folder is mounted via sshfs.
Since it was a remote folder, I automatically assumed, without thinking about it (shame on me for being that stupid), that it creates a remote symlink, which it doesn't, which is why it took me so long to find that particular 'bug'.

Maybe instead of an annoying prompt every time a link has to be created, there should just be an additional option, like 'create remote symlink' & 'create local symlink', and not just 'create link' (or whatever it is called).

---

