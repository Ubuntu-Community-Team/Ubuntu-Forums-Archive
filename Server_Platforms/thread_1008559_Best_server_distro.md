---
title: "Best server distro?"
date: 2008-12-11
forum: Server Platforms
---

### Post by SqueakyDK on 2008-12-11
Hey everyone,

I recently dumped Win2k as my server OS and chose Ubuntu instead. The server specs are as follows:

Dell Optiplex
PIII 1.0Ghz
256 MB ram

All the other stuff isn't important. Btw i'm not and adept linux user but definitely not a newbie either.

Now for the questions.

Should i choose Xubuntu over Ubuntu? Right now i've got Ubuntu installed but it ain't speedy. I sometimes use daemon tools from my laptop (Windows) to mount some dvd images i've got on the server. It takes like forever to browse the g**d*** thing and when i finally get it mounted it won't run without choking (yes it's a movie image). With the Win2k server i managed to make it stream the image faster and without chokes. The funny thing is that when i log on to the server with VNC it's not choppy at all :confused:.

I am basicly looking for the ultimate server distro available for my specs.

Must-have-features include:

* FTP Access
* Remote control
* Webmin support
* Remote bittorrent control

I don't want it to be a NAS server or anything else.


Bandwith available for the box:

Speedtest.net reports:
Fastest Download:
    64425 kb/s
Fastest Upload:
    36033 kb/s
Average Download:
    19583 kb/s
Average Upload:
    12939 kb/s


Any suggestions appreciated.

Thanks :KS

---

### Post by hrod beraht on 2008-12-11
> **SqueakyDK said:**
> Should i choose Xubuntu over Ubuntu?

There's only one *buntu server distro. And as a server distro it doesn't have a GUI, as the GUI display is handled by any desktop connecting to the server. So the X,U,K-buntu distinction is irrelevant.

Bob

---

### Post by SqueakyDK on 2008-12-11
> **hrod beraht said:**
> There's only one *buntu server distro. And as a server distro it doesn't have a GUI, as the GUI display is handled by any desktop connecting to the server. So the X,U,K-buntu distinction is irrelevant.

Bob

But if i used a server distro i would have had to set everything up manually right? Maybe i should consider the *buntu server distro with webmin installed then.

Will it solve my harddisk chokes?

---

### Post by hrod beraht on 2008-12-11
> **SqueakyDK said:**
> Will it solve my harddisk chokes?

When you say you are 'mounting' the stuff on the server, how exactly are you doing that? That is, via what protocol? SaMBa, NFS, SSHFS, HTTP, etc?

Bob

---

### Post by tuxxy on 2008-12-11
YOu could remove/install the necessary packages to your Ubuntu install and use that, saves installing another :)

---

### Post by SqueakyDK on 2008-12-11
> **hrod beraht said:**
> When you say you are 'mounting' the stuff on the server, how exactly are you doing that? That is, via what protocol? SaMBa, NFS, SSHFS, HTTP, etc?

Bob

I guess it's samba since I'm browsing the server using windows explorer. I guess the problem is that daemon tools isn't caching what it transfers from the server. It downloads it when it needs it which causes latency problems. If it could just prefetch the data...

---

### Post by Iowan on 2008-12-11
> **SqueakyDK said:**
> But if i used a server distro i would have had to set everything up manually right?  Maybe i should consider the *buntu server distro with webmin installed then.
The server distro comes with several selectable options - you can build a LAMP server, include SSH, DHCP or a few other "servers"  easily and let them come "pre-installed". [This]("https://help.ubuntu.com/community/WebMin") help page (that discourages Webmin) or [this]("https://help.ubuntu.com/community/WebminWithoutARootAccount") one (with more info) may/not be helpful.

---

### Post by handy on 2008-12-21
You may find the information on the following thread about file systems very interesting too.

It may help you choose which file system is most suitable for the type of work you want your server to do.

***_[http://ubuntuforums.org/showthread.php?t=1016435](http://ubuntuforums.org/showthread.php?t=1016435) _***

---

