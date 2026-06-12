---
title: "graphic on a cloud computer"
date: 2012-12-23
forum: Server Platforms
---

### Post by ELMIT on 2012-12-23
I need to run iMacro on a cloud computer. A database will give the data to the iMacro and firefox will fill up thousands of forms.

How to setup x to be used only for remote?

---

### Post by sandyd on 2012-12-23
You probably want a VNC server, or to run VNC over ssh (encrypted) - a good guide is available at [here]("https://help.ubuntu.com/community/VNC/Servers")

Happy Holidays!

---

### Post by littlegreiger on 2012-12-25
You could use X forwarding over SSH. Look it up on google as I can't remember if there's anything particularly special that you need to do. I've used it a couple times on my local server and it works quite well. 
Post back if you have any problems.

---

### Post by ELMIT on 2012-12-25
Thanks for your comments, but I think that both are not working as I expected:

X forwarding over SSH    e.g., at [http://www.craigryder.com/linux-ubuntudebetc/x11-forwarding-and-ssh-for-remote-linux-ubuntu-desktop/](http://www.craigryder.com/linux-ubuntudebetc/x11-forwarding-and-ssh-for-remote-linux-ubuntu-desktop/)

I found: 
> Why “ssh -X”? Because the graphic rendering job is done at your client so the data to transfer thru network is not huge. You won’t feel the screen is delayed even when you play movies. And this won’t add your server much load, as the same reason, thus a lot of job is done by your client. So, this is a high efficiency solution for remote desktop. You even can run big commercial graphic software, like Xilinx ISE or Mathworks MATLAB, remotely. And, this supports multi-client, no matter using different username or same username, since you a connecting to a server, both SSH server and X server.


My goal is that an iMacro is running within Firefox remote (unattended) and I only want to start/monitor it with graphic!

With ssh-X I assume, that you need to have a connection to the server, that the iMacro can run at all. There is no advantage to the current solution to use my desktop.


Maybe there is something available that does not need me to get a graphic environment. That is the task:

In a database are data, which should be posted to a web site. However, this web site makes a couple of time stoppers, like popup windows, time delay of 60 seconds to click on a button, click on the next page a button, ...

The easiest way was to record with iMacro and edit the script slightly and run it 24 hours a day. There are every couple of hours errors on that server and require me to restart/continue.

---

### Post by littlegreiger on 2012-12-26
Guess I should have looked up what iMacro actually is. Could you not use vnc as sandyd mentioned? Just connect over vnc (probably want to encrypt somehow i.e. ssh), start the iMacro running and disconnect the vnc then reconnect when you want to monitor it.

---

