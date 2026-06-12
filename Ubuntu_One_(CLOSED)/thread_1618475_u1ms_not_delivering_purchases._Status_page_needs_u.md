---
title: "u1ms not delivering purchases. Status page needs updating to reflect this."
date: 2010-11-10
forum: Ubuntu One (CLOSED)
---

### Post by QwUo173Hy on 2010-11-10
I've checked the Status page and the Music feature is reported to be running smoothly. But nothing I have purchased in the last few weeks has downloaded - only "Transferring to your Ubuntu One storage".

I understand they may be available via the web interface, but there is a problem here, it should be on the status page.

I'm curious whether I am the only person experiencing this problem?

Regards,
Jarlath

---

### Post by rtg on 2010-11-11
Hello,

Could you please check whether the songs are available in the web interface?

In case they are, please check whether the download can be triggered by running the following script - [ubuntuone-rescan-music.py]("http://people.canonical.com/~roman.yepishev/us/ubuntuone-rescan-music.py"). Basically that's u1sdtool --rescan-from-scratch=$volume_id_for_purchased_files.

---

### Post by QwUo173Hy on 2010-11-11
> **rtg said:**
> Hello,

Could you please check whether the songs are available in the web interface?

In case they are, please check whether the download can be triggered by running the following script - [ubuntuone-rescan-music.py]("http://people.canonical.com/~roman.yepishev/us/ubuntuone-rescan-music.py"). Basically that's u1sdtool --rescan-from-scratch=$volume_id_for_purchased_files.

Hi,

The files are available from the web interface. So I downloaded your script (thank you) and on the terminal:

```
jarlath@jarlath-laptop:~$ chmod +x ubuntuone-rescan-music.py 
jarlath@jarlath-laptop:~$ ./ubuntuone-rescan-music.py 
Successfully requested rescan of ~/.ubuntuone/Purchased from Ubuntu One

```

I then quit Rhythmbox and restarted it. But as of yet, nothing has changed.

---

### Post by QwUo173Hy on 2010-11-11
Update: The songs are in /home/jarlath/.local/share/ubuntuone/Purchased from Ubuntu One

But I don't know how long they have been there. They may have just appeared or they may have always been there. But the music store still tells me it is "Transferring".

---

