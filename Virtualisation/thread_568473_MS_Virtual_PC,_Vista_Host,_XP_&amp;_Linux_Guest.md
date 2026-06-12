---
title: "MS Virtual PC, Vista Host, XP &amp; Linux Guest"
date: 2007-10-05
forum: Virtualisation
---

### Post by srobot on 2007-10-05
Okay, I think I'm going to take the jump!

I've been looking into a tri-boot for some time now, but I found MS Virtual PC!

I have a Dell Windows Home XP laptop computer, but I see that you can not use Virtual PC on Home XP. So here is my idea: what if I backup my current XP computer, get an EOM Vista Ultimate Upgrade, upgrade it, put on Virtual PC, buy a copy of Home XP, then put my back up onto the XP part. Use McAfee on Vista. Of course Linux is the easy part.

Will my computer still work as a Dell? Will my computer be "safe" with McAfee only on the Vista part?

The way I think it works is:

The computer will be Dell Vista and I can run & save Vista apps, run Dell XP as "software" and run & save XP apps on it, run Linux as "software", so with them being "software" Vista McAfee will scan them.

Is this the way it will be?

Thanks,
--Scotty

---

### Post by UbuWu on 2007-10-06
Why don't you try [VirtualBox]("http://www.virtualbox.org/") instead of virtual pc? Far easier, you won't have to upgrade anything!

---

### Post by srobot on 2007-10-06
> **UbuWu said:**
> Why don't you try [VirtualBox]("http://www.virtualbox.org/") instead of virtual pc? Far easier, you won't have to upgrade anything!

It does look good...

What is the down side of VirtualBox?

Will VirtualBox work just as good as a Tri-Boot?

Thanks,
--srobot

---

### Post by UbuWu on 2007-10-06
There aren't many downsides. The guest OS that you run inside vbox will run a little slower than when you run it natively and you need enough memory to run it. But on a modern computer these won't be big issues.

---

### Post by srobot on 2007-10-06
I have a computer with:

2 GB Ram

80 GB HDD

Should this be fine?

Thank you so much,
--Scotty

---

### Post by UbuWu on 2007-10-07
That is more than enough to run ubuntu in vbox. I would say just try it and see if you like it.

---

### Post by srobot on 2007-10-07
Cool!

Because of my 300 MB download limit perday, I will use a Live CD.

Do you think I could also run Vista Ultimate on vbox, I know vbox lets me, but is my computer good enough?

--Scotty

---

### Post by UbuWu on 2007-10-07
I don't know, it will probably run, but Vista will need a lot more resources than ubuntu, so it could be slow. I think you do have enough memory in your computer.

---

### Post by srobot on 2007-10-08
I downloaded VirtualBox, and made a place for Ubuntu 7.04.

When I went to run Ubuntu in VBox, and it went into a Ubuntu Boot mode.

I did not copy all of the options down, but I had 30 seconds to make a choice. 

I hit the X (upper right hand side in XP) to shut it down, and it shut it down.

What option of the 6 (+/-) should I chose?

--Scotty

---

### Post by jocko on 2007-10-09
Didn't you read the options? The 30s countdown stops if you use the up or down arrow keys, if you need more time to read.
I'm guessing you have got an ubuntu live cd.
In that case, the first option is to "start or install ubuntu" or something similar.
Select this option to start a live session.
Once it's started you can either try it out and get familiar with it, or start the installer from a shortcut on the desktop.

---

### Post by srobot on 2007-10-09
If I install Ubuntu, will it only install in the vBox part of the computer?

Thanks,
--Scotty

---

### Post by UbuWu on 2007-10-09
yes

---

### Post by srobot on 2007-10-09
Because I don't have a backup of my computer, I want to get this right:

Pre) I stick in the CD and hit "close"

1) I install VirtualBox

2) I setup a spot for Ubuntu by clicking "new"

3) I click on the button to "power on" Ubuntu

4) I follow the on screen steps

5) I hit the top option when I get to the Ubuntu Live CD Boot, titled "install" (or something like that)

6) [Then what? Follow on screen instructions?]

If I do this, I must go into vbox to start Ubuntu, and when I boot my computer (normally) it will still boot into Windows XP, is this correct?

Thank you for all of your help.

--Scotty

---

### Post by UbuWu on 2007-10-10
> **srobot said:**
> Because I don't have a backup of my computer, I want to get this right:

Pre) I stick in the CD and hit "close"

1) I install VirtualBox

2) I setup a spot for Ubuntu by clicking "new"

3) I click on the button to "power on" Ubuntu

4) I follow the on screen steps

5) I hit the top option when I get to the Ubuntu Live CD Boot, titled "install" (or something like that)

6) [Then what? Follow on screen instructions?]

If I do this, I must go into vbox to start Ubuntu, and when I boot my computer (normally) it will still boot into Windows XP, is this correct?

Thank you for all of your help.

--Scotty

All correct ;-)

---

### Post by drmatty on 2007-10-21
I recently did the same thing, only created a virtual XP machine on my Gutsy XPS laptop. Great idea.

---

### Post by srobot on 2007-10-27
I'm posting this from my vbox Ubuntu 7.10! :guitar:

I have a question though, when I'm not running vbox, will my computer slow down at all?

I heard that it will "split" my intel core 2 duo even when I'm not running Ubuntu!!!!!

--Scotty

---

### Post by huggies15 on 2007-10-30
ive got vmware on my ubuntu, running on a dual core. i only notice a slow down in ubuntu with xp running in the vbox, when its closed it runs fine, using both cores :)

---

### Post by drmatty on 2008-02-10
I'm running a virtualBox with XP in my Ubuntu. Ubuntu still runs pretty swiftly with VirtualBox running, but XP is a bit sluggish. With the Virtual Box off, Ubuntu is full speed.

---

