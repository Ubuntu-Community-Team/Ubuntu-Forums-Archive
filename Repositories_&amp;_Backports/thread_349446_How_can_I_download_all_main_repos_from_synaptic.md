---
title: "How can I download all main repos from synaptic?"
date: 2007-01-30
forum: Repositories &amp; Backports
---

### Post by Isoss on 2007-01-30
Hello community

I want to create a DVD for the main repositories of ubuntu edgy but I don't know how to download all these ignoring dependencies! because if I want to select all the packages in the main it will automatically select dependencies which by selecting another package with dependencies that conflict with the latter they would be automatically deselected! 

So what I want is just to select all the main repos and download them (without installation) by checking the "Download Package Files Only" check box at clicking Apply in synaptic.

P.S. I know that there are torrent files for iso dvds that contain all the ubuntu repos already published online, but I am having a problem with the torrent download, it would disconnect a lot and that seems to take forever cuz it downloads a few MBs of the iso torrent and then disconnect!

Thanks in advance.

Isoss

---

### Post by aidanr on 2007-01-30
:-k perhaps use wget?

```
wget -r -np -A "*.deb" http://archive.ubuntu.com/ubuntu/pool/main/
```

---

### Post by Isoss on 2007-01-30
hmmmm ... could work! I'll try that!

But what if I got disconnected? will running it again continue the download from where it stopped?

---

### Post by az on 2007-01-30
> **Isoss said:**
> Hello community

I want to create a DVD for the main repositories of ubuntu edgy 

Doesn't the DVD already contain all of main?


[http://www.ubuntu.com/products/GetUbuntu/download#currentrelease](http://www.ubuntu.com/products/GetUbuntu/download#currentrelease)
[I]DVD Downloads
For Ubuntu 6.10, our latest release, you can download DVDs from one of the following locations: 
[/I]

---

### Post by Isoss on 2007-01-31
Alright, say I want to download the universe repos also!

---

### Post by az on 2007-01-31
[http://packages.ubuntu.com/edgy/net/apt-mirror](http://packages.ubuntu.com/edgy/net/apt-mirror)

---

### Post by hogman23 on 2007-01-31
I agree, I would use apt-mirror and only put the repo(s) that you want in your mirror.list file.

Specifically:
apt-get install apt-mirror

Then,
Edit your /etc/apt/mirror.list and add

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy main

or whatever you want to download.  I would also change the base_path to something like:
set base_path /mirror/apt-mirror

You will of course need to create the /mirror/apt-mirror directories before you run apt-mirror.

Then just type apt-mirror as root.

---

