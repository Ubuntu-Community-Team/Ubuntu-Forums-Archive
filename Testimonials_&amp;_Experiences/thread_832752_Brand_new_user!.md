---
title: "Brand new user!"
date: 2008-06-18
forum: Testimonials &amp; Experiences
---

### Post by highlyevolved on 2008-06-18
Ok, I was hearing a lot of hype over 'Mint' so I decided to explore Linux.

Have been a windows user all my life but really I encounter so much rubbish and errors in xp so decided to give Ubuntu a go (apparently the best for newbies).

Was very impressed that all the drivers etc worked.
When I did a fresh install of XP I had to track everything down which was a nightmare.

After intial frustration in not being able to install anything (hello add/remove program!) everything seems to running smooth.

Ubuntu has a much more polished/slick look than XP.
And its been very easy to pick up.

I have yet to see if my printer works or my ipod shuffle but hopefully they will!

Really impressed so far, glad I made the switch.

Just one quick question, is there any point in having icons on the desktop given they are only a tool bar click away?

I've noticed its easy to make programs shortcuts in the desktop but couldn't figure out how to put a folder shortcut (ie music) on there?

Thanks!

---

### Post by ad_267 on 2008-06-18
Woohoo new user! Welcome.

Yeah I find installing stuff is a lot easier in Ubuntu than in Windows. Definitely different but easier.

What kind of printer do you have? HP and Epson have very good Linux support, Canon not so much. The iPod should work fine with Rhythmbox without any problems.

To put a link to a folder you can open the file browser (called Nautilus) and right click on the folder and select "make link." Then drag this onto the desktop. I personally don't have any icons on my desktop except for removable drives.

Oh and if you need to install anything a bit more advanced, you can do it through the Synaptic package manager. Go to System - Administration - Synaptic Package Manager. This might be different if you're using Mint, I haven't used it myself.

---

### Post by iaculallad on 2008-06-18
You could use the **ln** command using your terminal to do that job for you:

Sample:

```
ln -s /mnt/sda1/My_Music_Folder /home/username/Desktop/Music
```

sda1 is your mountpoint, My_Music_Folder is where your mp3 files are located.

---

### Post by highlyevolved on 2008-06-18
I've got a HP printer so it should be ok.
:)

I don't think I really need to put anything on the desktop - I guess I'm just used to having lots and lots of files/folders from XP.
It's a refreshing change.

Thanks for the advice, looking forward to exploring the Ubuntu world - now to convince my family to convert!

---

### Post by ad_267 on 2008-06-18
Yeah a lot of people (including me) find it faster to do things with the command line in Ubuntu. That's why some people complain about having to do everything in a terminal with Linux. The truth is you can do pretty much anything without having to go near the terminal but often it's faster if you know what you're doing and if you ask for help on the forums you'll often be given commands to enter as it's easier to ask someone to enter a command than to walk them through steps.

Haha yeah I'm still working on my family. Slowly but surely.

---

### Post by barney385 on 2008-06-18
It's a personal preference thing. I like the freedom Ubuntu affords myself.

:smile:

---

### Post by Sef on 2008-06-18
> I've got a HP printer so it should be ok.

Almost all HPs work ootb (out of the box), just plug it in, and it should work.

---

### Post by lswest on 2008-06-18
Haha, nice to hear another praise of Ubuntu :P  Anyways, welcome to the community.

One more reason why you might see terminal commands being given on the forums is because they're the same for any Ubuntu version or derivative (Ubuntu, Kubuntu, Xubuntu, Fluxbuntu, etc.), and so instead of having to explain it for multiple GUI setups, one command is given.  Makes it a bit easier for those people giving help ;)

And my desktop is pretty empty too :P  Got my home folder there, my windows partition mounted, a reminders folder and a homework folder :P (haven't opened either of those folders for a while...)

And I agree with Sef, HP printers are great to have, just plug them in and print (for the majority of them at least) :P

---

### Post by Qrikko on 2008-06-18
I would like to just first of all say welcome! :)

Second (when you get more used to it and as so many others start missing *that program that was so nice in windows*) then you want to check Wine :) they made the first stable release today *gratz wine* version 1.0 and it is in the repos already (i.e. the version is in the list of packages made available for Ubuntu *blabla*)

Also talking about links and shortcuts :) I have to agree with what you said about "icons are only a tool bar click away".. I really like to just use it for shortcuts, and you can have folders and groups there as well :)

To make a shortcut to a folder you would use the "...add to panel" and choose a "custom application launcher" where as the command you could put somehting like:

nautilus /path/to/folder

Observe that I think that the path is relative to ~/ (your /home/username) folder.

and to make groups :) I love that feature you do the same: "...Add to panel" ---> Drawer

then you can drop program and shortcuts, and even other drawers to group them on it :)

well hope you have a nice experience now that you have a operating system that actually were created for modern use of computers :)

---

