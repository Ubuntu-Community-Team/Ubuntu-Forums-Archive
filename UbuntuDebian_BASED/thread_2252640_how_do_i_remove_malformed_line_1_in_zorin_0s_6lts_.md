---
title: "how do i remove malformed line 1 in zorin 0s 6lts ultimate ubuntu?"
date: 2014-11-13
forum: Ubuntu/Debian BASED
---

### Post by Kenneth_Hagele on 2014-11-13
I am having two issues on my computer. I am new to linux. I am still learning. one problem= ubuntu one warning has been popping up on my desktop since july 2014.
other problem= computer is showing me a RED DOT, and when i click on it. it says i have: malformed line 1 in source list /etc/apt/source.list.d/dropbox.list (dist parse).
how do i remove these from linux? any info will help.

---

### Post by coffeecat on 2014-11-13
Zorin, not Ubuntu.

*Thread moved to **Ubuntu/Debian BASED**.*

Open a terminal and run this command:

```
cat /etc/apt/sources.list.d/dropbox.list
```

And post the output between [noparse]```
 and 
```[/noparse] tags to maintain formatting. You can use the # button in the advanced editor toolbar for this. If you highlight the output with the mouse, right-click -> copy, you should then be able to paste it into your post, which will avoid the tedium of typing it all out. Which is important because the path is /etc/apt/sources.list.d/dropbox.list, not /etc/apt/source.list.d/dropbox.list as you posted. That will show us what is wrong with that file, after which someone should be able to help you fix it.

---

### Post by Kenneth_Hagele on 2014-11-13
thank you for your response. Uhmm. here is everything that my terminal screen says:
kenn@kenn-latitude-e6400:~$ cat /etc/apt/sources.list.d/dropbox.list
deb [http://linux.dropbox.com/ubuntu/precise](http://linux.dropbox.com/ubuntu/precise) main
kenn@kenn-latitude-e6400:~$
I hope this helps?.... 
i can now no longer access ubuntu software either. it also gives me this error code...
this is the first thing i have tried to download to my computer. i appreciate any help on this.

---

### Post by coffeecat on 2014-11-13
There is a simple error in that one-line file. It's easily fixed with a text editor, but not knowing what GUI text editor is included in Zorin (few here will be) I can only give you instructions to use a less friendly basic terminal editor. Open a terminal, and:

```
sudo nano /etc/apt/sources.list.d/dropbox.list
```

You will be prompted for your password. You will not see it echoed to the screen, but just type it in and press enter - it is going in. If the basic terminal editor that opens doesn't have the single line that you posted earlier, then you made a typo in the command. If it does, then type in a space before the p of precise, so that line looks like:

```
deb http://linux.dropbox.com/ubuntu/ precise main
```

You can't use your mouse to move around the nano screen - you need to use the arrow keys. Once you have made the edit, double-check it and then press ctrl-o to save and ctrl-x to exit.

Now run this command to see if you get the same error:

```
sudo apt-get update
```

> **Kenneth_Hagele said:**
> 
i can now no longer access ubuntu software either. it also gives me this error code...

What error code?

By the way, Zorin is a non-official variant of Ubuntu which has its own forum, and which has been configured to look vaguely like Windows as  way of making newcomers to Linux comfortable with the desktop. Which may or may not be a successful way of making newcomers comfortable. You are welcome to post in this Other OS support section of ubuntuforums (the main sections are for the official variants) but few here will have practical experience of Zorin and how this has been modified from the parent Ubuntu. Or you can post on the far quieter Zorin forum. If you find you can't get the help you need for Zorin, you might want to think about using Ubuntu or one of the official variants and you would then be able to use the main sections here, where you are likely to get more help more quickly.

---

### Post by Kenneth_Hagele on 2014-11-13
thank you. i will try this out. 
P.S. the error code was the exact same malfunction line 1 in "etc" code. 
i did not know ZORIN OS was an off shoot of ubuntu. I thought it was another distro. like mint or redhat. thank you for the info.

---

### Post by Kenneth_Hagele on 2014-11-13
thank you!! that worked. the red warning dot is off my desktop now. 
I am going to restart my computer now. I think it should be good. I am not using dropbox on my computer.
the terminal screen finished with this stuff at the end......
reading package lists....done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: the following signatures were invalid: BADSIG FC0D5CCAEDF3D1F9 Launchpad Bleeding-Edge Openshot PPA
W: A error occurred during the signature verification. the repository is not updated and the previous index files will be used. GPG error: [http://deb.opera.com](http://deb.opera.com) stable release: the following signatures couldn't be verified because the public key is not available: NO_PUBKEY 517590D9A8492E35

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise release: the following signatures were invalid: BADSIG 12532D53BB275EE0 Launchpad PPA for Zorin OS
W: failed to fetch [http://deb.opera.com/opera/dists/stable/release](http://deb.opera.com/opera/dists/stable/release)

W: Some index files failed to download. they have been ignored, or old ones used instead.
kenn@kenn-latitude-E6400~$

thank you again for all your assistance. Kenn
- too bad there is no Linux University, the world would run so much better, with no windows in it-

---

