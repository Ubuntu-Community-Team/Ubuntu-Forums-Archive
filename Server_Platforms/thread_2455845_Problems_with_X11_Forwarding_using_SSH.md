---
title: "Problems with X11 Forwarding using SSH"
date: 2020-12-29
forum: Server Platforms
---

### Post by lelolelo on 2020-12-29
Hello, I am new to Linux and I am trying to have some fun with SSH just to learn how it works. I configured my laptop to run a SSH server on Ubuntu 20.04 and I'm trying to use X11 Forwarding with another 20.04 desktop and it has been partially successful because I can open images and some applications like Nautilus just fine, but when I try to open videos and text files using xdg-open they do not open in the client computer but in the server. I also get these kind of messages when trying to open apps like Firefox and Thunderbird: 
> X11 connection rejected because of wrong authentication.
X11 connection rejected because of wrong authentication.
Unable to init server: Broadway display type not supported: localhost:11.0
Error: cannot open display: localhost:11.0

I enabled X11 Forwarding in /etc/ssh/sshd_config
I'm using authentication keys

Anyone knows how to solve this?

---

### Post by TheFu on 2020-12-29
exact command used?

Video processing can ignore X11 settings and may try to use the local GPU instead. Try using a different video player.  Not all programs can work over remote X.

Regardless, remote X11 is not the efficient way to get video playing. Much better to use a streaming protocol like dlna, or even networked file system, like NFS. These are much more efficient than bit copies of uncompressed video.

---

### Post by lelolelo on 2020-12-29
> **TheFu said:**
> exact command used? 

For videos I'm using xdg-open and for Firefox I just type Firefox in the terminal.

---

### Post by ajgreeny on 2020-12-30
So what is your default to play videos in the client system; that is what will be trying to play the video over remote X11.

---

### Post by TheFu on 2020-12-30
> **lelolelo said:**
> For videos I'm using xdg-open and for Firefox I just type Firefox in the terminal.

That doesn't always run remote. Also, firefox has an automatic mode that always uses the exsting FF window, unless  specifically asked not to do that. It is a pain.

I've never found xdg-open useful. Easier to run the program I want. Check the FF manpage for the available options.
```
       -no-remote
              Don't connect to any other running  instances  of  firefox.  Use
              this  if  you want to run firefox in an entirely new process. By
              default, firefox will delegate a command to an  already  running
              instance.
```

If you want to stream a video using remote X11, use
```
ssh -X thefu@regulus  /usr/bin/mpv  /path/to/vdeo.mkv
```audio won't play locally and may refuse to play on the remote system if you don't setup some things.

---

