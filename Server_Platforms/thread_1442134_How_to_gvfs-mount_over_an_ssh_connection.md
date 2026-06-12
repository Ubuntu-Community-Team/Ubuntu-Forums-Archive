---
title: "How to: gvfs-mount over an ssh connection"
date: 2010-03-29
forum: Server Platforms
---

### Post by lotsofish on 2010-03-29
In Gnome desktop, you can use the "Connect to server..." option to mount a remote file system. It creates the mount in the ~/.gvfs directory.

What I've been wanting is to be able to do the same thing when I connect to my home machine remotely through ssh. I was only able to find partial bits of information, but I was finally able to get it working today, and I thought I would pass it on in the hope that it helps someone out.


Start a new dbus session, and load a new bash instance, so dbus doesn't quit until you exit bash.
```

# dbus-launch bash
```

gvfsd is the main daemon for GVFS. If you skip this step the file system doesn't get mounted to ~/.gvfs
```

# /usr/lib/gvfs/gvfsd -r &
```

Now you can mount the remote file system. Access the file system through ~/.gvfs/<name of connection>
```

gvfs-mount ftp://example.com
```
**TIP:** If you have the remote passwords saved in your keyring and you are using X forwarding, a box will popup asking to unlock your keyring. Otherwise you will be asked for username and password. (Is there a way to authenticate to gnome-keyring through ssh so you don't need X forwarding?)


There are a few other options, but gvfs is about the smoothest. I've used curlftpfs, sshfs, etc, but they tend to be slow. I can open a vnc session through ssh, but that is slow too and it's overkill when you just need to move a few files around or make a couple edits to a website, etc.

---

