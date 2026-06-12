---
title: "virt-p2v-make-disk does not work for me on bionic"
date: 2018-06-08
forum: Virtualisation
---

### Post by mdfishere on 2018-06-08
Hello all. I'm running bionic and need to get a working p2v setup.

As of reading the man pages for  virt-p2v(1) ([http://manpages.ubuntu.com/manpages/bionic/man1/virt-p2v.1.html]("http://manpages.ubuntu.com/manpages/xenial/man1/virt-p2v.1.html")) and 
virt-p2v-make-disk(1) ([http://manpages.ubuntu.com/manpages/bionic/man1/virt-p2v-make-disk.1.html]("http://manpages.ubuntu.com/manpages/xenial/man1/virt-p2v-make-disk.1.html")) I tried to make
such a bootable disk to begin the process. Quickly I ran into trouble as you'll see.

First, after installing the requisite libguestfs-tools and even virt-goodies I see this error...

[FONT=courier new]$  virt-p2v-make-disk -o p2v-bionic-bootable.img
virt-p2v-make-disk: cannot find /lib/x86_64-linux-gnu/virt-p2v/virt-p2v.xz[/FONT]

As google showed me this looks like the bug reported here  [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=897684](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=897684)
and sure enough the path isn't right...

[FONT=courier new]$ dpkg --listfiles libguestfs-tools | grep virt-p2v.xz/usr/lib/x86_64-linux-gnu/virt-p2v/virt-p2v.xz[/FONT]


to work-around I did this

[FONT=courier new]$ sudo mkdir -p /lib/x86_64-linux-gnu/virt-p2v/
$ sudo ln -s /usr/lib/x86_64-linux-gnu/virt-p2v/virt-p2v.xz /lib/x86_64-linux-gnu/virt-p2v/virt-p2v.xz[/FONT]

Trying again I get a different error...

[FONT=courier new]$  virt-p2v-make-disk -o p2v-bionic-bootable.img
virt-p2v-make-disk: cannot find dependencies file (/share/virt-p2v/dependencies.debian)[/FONT]

At this point I'm at a loss. the path of /share looks very unexpected. 

Where does this dependencies file come from? Or am I just doing it wrong?

---

### Post by FibMcGee on 2018-07-16
I managed to get virt-p2v-make-kickstart to run on bionic after installing it ( libguestfs-tools ) and making these soft links to link directories ( !! not just files ):

sudo ln -s /usr/share/ /share
sudo ln -s /usr/lib/x86_64-linux-gnu/virt-p2v/ /lib/x86_64-linux-gnu/virt-p2v

Now I have an 85k p2v.ks file but where is the livecd creator mentioned in the man pages??

---

### Post by alessandro-battilani on 2018-10-15
Is this issue still open?
I resolved it to set prefix variable in shell before execute command...

export prefix=/usr/

---

