---
title: "Playing music on a server controlled by another computer?"
date: 2007-05-07
forum: The Cafe
---

### Post by berlandb on 2007-05-07
Hi,

I use a laptop computer and have to have my music on an external hard drive, because there is no space on the internal one.

I'm wondering, if I could buy a little server, attach the music hard drive to it and play music via the server. I would like to continue using Amarok on my laptop, but let it handle the music on the server and also play the music through the servers sound card.

Is that something, that can be done with a remote login and X11 or something?

Thanks for your help

---

### Post by Spr0k3t on 2007-05-07
Oh yeah, use MPD.  Once you set it up you can pull the music stream from the server.

---

### Post by ssam on 2007-05-07
I do this.

the server is a [via epia]("http://www.via.com.tw/en/products/mainboards/") MII6000. with ubntu installed on a 1GB compactflash, and a large IDE disk for the music.

the server has openssh-server installed, along with rhythmbox and a few X packages (you need xauth). I have public keys set up for passwordless logins. and avahi so that i can reach it by hostname.local rather than an ip address.

to run rhythmbox on the server (which is called flute), that displays on my laptop screen i run
```
ssh -X flute.local rhythmbox
```

---

### Post by berlandb on 2007-05-15
Thank you very much for your answers, guys.

---

### Post by epimer on 2007-05-15
I do this too, but differently again from the above methods (don't you love choice?).

My music and videos are on my server, and I have ~/Music and ~/Video folders on my laptop. I use the fuse kernel module and sshfs to mount the remote folders as if they were local, and then any media player (Exaile for me) can play them as if they were local files (the library is pointed at ~/Music, which is empty before I mount the remote folders).

You can find instructions for the whole shebang [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_remote_folders_into_local_Ubuntu_machine_.28sshfs.29").

---

### Post by berlandb on 2007-05-16
> **epimer said:**
> I do this too, but differently again from the above methods (don't you love choice?).

My music and videos are on my server, and I have ~/Music and ~/Video folders on my laptop. I use the fuse kernel module and sshfs to mount the remote folders as if they were local, and then any media player (Exaile for me) can play them as if they were local files (the library is pointed at ~/Music, which is empty before I mount the remote folders).

You can find instructions for the whole shebang [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_remote_folders_into_local_Ubuntu_machine_.28sshfs.29").

Hi,

thanks for sharing. I didn't have the possibility to try your solution yet, but as far as my understanding goes, it wouldn't do the job for me.

It stores the media data on a server, but then simply streams it to the laptop to play it on the laptop. This is not what I'm looking for. Instead the server is supposed to play the files through it's own soundcard, leaving the laptop as a remote control.

---

### Post by epimer on 2007-05-16
Whoops! Sorry, that's my fault entirely for misunderstanding your post.

---

