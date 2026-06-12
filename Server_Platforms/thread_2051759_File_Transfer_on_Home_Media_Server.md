---
title: "File Transfer on Home Media Server"
date: 2012-09-02
forum: Server Platforms
---

### Post by mitanc on 2012-09-02
I would like to figure out an easy method to transfer files from a headless home media server to a USB external hard drive.  

Normally I can mount the hard drive by SSHing into the server and then doing my normal cp commands, but I have over 2 TB of data and I need to select certain folders as I only need bits and peices of the data.  Is there any GUI interface I can use via my iMac (either web or other) where I can drag and drop folders?  If not, is there any intuitive command line programs which can make it easy for me to select and copy data?

Thanks in advance for your help!

---

### Post by 2F4U on 2012-09-02
Maybe Midnight Commander? It is a command line tool that can be used over SSH and provides a two-pane graphical interface similar to Norton Commander.

[http://tldp.org/LDP/LG/issue23/wkndmech_dec97/mc_article.html](http://tldp.org/LDP/LG/issue23/wkndmech_dec97/mc_article.html)

---

### Post by thnewguy on 2012-09-02
Midnight Commander is probably a good option. I was going to recommend Filezilla, which has a nice GUI, but I think it only moves files from one location to another on a remote machine.

---

### Post by arrrghhh on 2012-09-02
> **thnewguy said:**
> Midnight Commander is probably a good option. I was going to recommend Filezilla, which has a nice GUI, but I think it only moves files from one location to another on a remote machine.

I know OP has a MAC, but I was looking for something similar as well on Windows.  WinSCP can't do it, but the creator does have a way of scripting commands you can pass via ssh - so it would provide a GUI with the cli commands actually doing the lifting (as usual, eh?)

Perhaps Filezilla or some other MAC software has this option like WinSCP does.

Edit - [thread](http://winscp.net/forum/viewtopic.php?t=892) for reference.  The creator of WinSCP talks about the way to script it in the 14th post down.

---

### Post by lykwydchykyn on 2012-09-03
If you can run X11 on the mac, you could just install any graphical file manager like pcmanfm, nautilus, or dolphin and just run it over ssh.

Or if that's not an option, install vncserver and a lightweight desktop like LXDE.

---

### Post by arrrghhh on 2012-09-03
> **lykwydchykyn said:**
> If you can run X11 on the mac, you could just install any graphical file manager like pcmanfm, nautilus, or dolphin and just run it over ssh.

Or if that's not an option, install vncserver and a lightweight desktop like LXDE.

Ah right, not sure why I didn't think of mentioning that either.  I used to use Dolphin over SSH using XMMing on Windows ;).

---

### Post by mitanc on 2012-09-03
Thanks for all the advice.  

Its funny, all of you mentioned all the avenues I looked at.  

First of all, I started up Midnight Commander and bookmarked a website with some advice on how to use it.  Learned the shortcuts, etc.  So yes, that is a very viable option for me.

Secondly, I enabled X11 Forwarder via SSH and installed dolphin and yes, that seems to do the trick as well.

Basically, I got my huge media server with downloaded content at around 2 TB.  Now, my non tech friends want to come over and rip my media so they can watch it at their homes.. the issue comes when they bring a 500 GB hard drive and want to select what they want.  I can always hook up the hard drive via USB to the mac and they can xfer there, but its just sooo slow.  I want to hook the bad boy directly to the Linux Server and make an easy way to copy the files they want. 

I think dolphin will probably be the best bet.

If anyone knows of an even better way, please please let me know!

---

### Post by sandyd on 2012-09-03
camfrog

---

