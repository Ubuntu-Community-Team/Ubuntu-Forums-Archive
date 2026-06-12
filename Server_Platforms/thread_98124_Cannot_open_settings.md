---
title: "Cannot open settings"
date: 2005-12-02
forum: Server Platforms
---

### Post by don_samji on 2005-12-02
I read the reply to my last posts.....thanks to all the helping hands.

Well, I reinstalled Ubuntu 5.10. I gave the same password for both root and User. After I login, when I click on Synaptic Manager, Disk Manager, etc., I am asked for my root password. It accepts it, but nothing comes at all even after waiting for quite a long time.
I have 1 GB RAM so I have no swap file (truth is there was no swap file partition option in the partition manager of the expert installation level), could that in any way pose a problem to my regular using? I know the use of swap file, like virtual memory, page file in windows.
Also when I type   su    in terminal, followed by the right password, then the prompt changes. But when I close the terminal and open it again, the prompt is the same as before, like this "don@55~#:"
Why is that and is that a problem?
Also, how do I access my windows partition from Linux, shown as hda1, hda5, hda6, please I need an answer for this query.

---

### Post by don_samji on 2005-12-02
I am a newbie in Linux.....so please speak at a level of newbie to me, thanks.

---

### Post by aysiu on 2005-12-02
First of all, Ubuntu isn't made for root. You can enable root if you want, but then you run into all sorts of problems. For more on sudo, read this:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

In the meantime, to see what may be the problem, try these two things:

1. Run the command ```
gksudo synaptic
``` from the terminal. See what output is. If you just run the command (not from the terminal), you see the dialogue disappear but have no idea what's going on. If you launch it from the terminal, you can see the output of what happens. Post that output here.

Oh, and Synaptic wants your sudo password, not your root password.

2. Can you apt-get install stuff? Synaptic is just a pretty graphical version of apt-get. Type ```
sudo apt-get update
``` Any luck?

---

### Post by don_samji on 2005-12-03
Firstly I tried the sudo command and managed to see the window of synaptic. Also I installed some packages as super user. Then I enabled root login. I logged out and logged in again as root. I could do all I wanted in it then. 
But I have a query, is it possible to write into the windows partitions?
One more, will Synaptic only search among the packages you have copied onto your hard disk or can it also search from the internet, if yes, how?
I will post the output you asked soon.

---

