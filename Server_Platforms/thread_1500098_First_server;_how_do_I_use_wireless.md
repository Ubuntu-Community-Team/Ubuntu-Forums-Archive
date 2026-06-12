---
title: "First server; how do I use wireless?"
date: 2010-06-02
forum: Server Platforms
---

### Post by Arthur_D on 2010-06-02
Hi folks, while I know it's generally bad practice to use a wireless connection for a server, I would mostly use it for fairly trivial stuff, while it'd still be connected to the Internet. So I installed Ubuntu 10.04 Server Edition on a two year old laptop of mine (with a practically busted graphics card), and upon selecting which services to install, I did the classic mistake of just pressing 'Enter'. So, I would like to know how to install the other stuff from the command line, and more importantly how to connect to the Internet automatically using wireless (no Network Manager here, and while I'm not too bad at the command line, I'm not used to connecting to the net with the command line).

That's all for now, I think. Thank you for reading, and even more so if you will answer. :)

---

### Post by Bachstelze on 2010-06-02
Your network is probably using WPA, so you'll need wpa_supplicant, see:

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo#WPA%20Supplicant](https://help.ubuntu.com/community/WifiDocs/WPAHowTo#WPA%20Supplicant)

---

### Post by Arthur_D on 2010-06-03
Hmm, having trouble finding 'wpa_supplicant.conf'. I have searched for an answer, but I found mostly UbuntuForum threads from 2006-2007 stating I would have to create my own. But I don't trust that looking at how much has happened to Ubuntu in these years.

Any suggestion(s)?

---

### Post by Bachstelze on 2010-06-03
> **Arthur_D said:**
> Hmm, having trouble finding 'wpa_supplicant.conf'. I have searched for an answer, but I found mostly UbuntuForum threads from 2006-2007 stating I would have to create my own. But I don't trust that looking at how much has happened to Ubuntu in these years.

Any suggestion(s)?

It's normal that you can't find it, because it does not exist yet. ;) You have to create it with the output of wpa_passphrase.

---

### Post by Arthur_D on 2010-06-03
Okay... so I basically copy the output I get from wpa_passphrase, and paste it into a new file I name 'wpa_supplicant.conf'?

Thanks for your help dude. :D

---

### Post by Bachstelze on 2010-06-03
> **Arthur_D said:**
> Okay... so I basically copy the output I get from wpa_passphrase, and paste it into a new file I name 'wpa_supplicant.conf'?


Yes.

---

### Post by Arthur_D on 2010-06-03
Hmm, one problem... when issuing the command 'wpa_passhprase [SSID]' I get this: "passhprase must be 8..63 characters." I didn't get a chance to write the password... the SSID has spaces in it; is that the problem?

---

### Post by derrick81787 on 2010-06-03
I've done all this once, but it was a pain.  But then again, I had to deal with switching between different wireless networks, which I guess a server would not have to do.  Either way, the easier way to get wireless working would be to install wicd.  It has functionality similar to network-manager, but it also has a command line interface.  Once it's installed, it's really easy to use.

I think the packages you need are *wicd *and *wicd-curses* in Lucid.  In previous versions of Ubuntu, it was *wicd *and *wicd-client*, though.  Either way, once the packages are installed, you can run the client from the command line with the *wicd-curses* command.

Once you connect to a network, you can even tell it to remember the network.  Once it does that, it'll connect automatically when you boot up the computer with no need to run *wicd-curses*.  I think it's a great little program.

- Derrick

*****Edit:**
If you're running any kind of a GUI, even if it's just a window manager like Openbox, then you can install the *wicd-gtk* package (or just run the *wicd-gtk* command that is included in the *wicd-client* packages on earlier versions of Ubuntu).  It's a great GTK interface for wicd.  I understood that you were running a command line only server, though, and my original reply is assuming that you are only on a command line.

---

### Post by Arthur_D on 2010-06-03
Thank you for you input, [derrick81787]("http://ubuntuforums.org/member.php?u=47414"). I will look into that. :)

Yes, I'm not running any sort of GUI. As I wrote in the original post, the gfx card is almost busted and even in the terminal it's really hard to see what I'm doing... sometimes I rewrite things slowly just in case I got it wrong (when I'm not TABbing my way around). Quite painful, but I figure when I get wireless to work I can use SSH or something to control the server from my fully working desktop machine.

---

### Post by Arthur_D on 2010-06-09
Solved, thanks a lot to both of you. :D

---

### Post by hopeless8009 on 2010-07-02
how did you solve it

---

### Post by Arthur_D on 2010-07-05
Hi, I solved it by using wicd (in particular wicd-curses). :)

---

