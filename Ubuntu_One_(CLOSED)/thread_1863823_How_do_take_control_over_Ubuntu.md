---
title: "How do take control over Ubuntu"
date: 2011-10-18
forum: Ubuntu One (CLOSED)
---

### Post by Judaic Christian on 2011-10-18
I recently installed Ubuntu One on a separate hard-drive. It seems that I do not have permission to do anything. How can I take control of software as owner? And without having to give a password for everything. PS. Since I installed Ubuntu One my clock in Windows 7 has stopped keeping proper time. I have reset it three times. I have Windows 7 and Ubuntu on separate hard-drives. I have also noticed that the graphics are very poor in Ubuntu One.

---

### Post by matt_symes on 2011-10-18
Hi

To fix your clock issue set Ubuntu to local time (the same that windows uses). Open a terminal and type

```
sudo hwclock --localtime
```

Enter your password. It will not be echoed to the screen.

Kind regards

---

### Post by Judaic Christian on 2011-10-18
> **matt_symes said:**
> Hi
 
To fix your clock issue set Ubuntu to local time (the same that windows uses). Open a terminal and type
 
```
sudo hwclock --localtime
```
 
Enter your password. It will not be echoed to the screen.
 
Kind regards
My computer says that my password is: login. But it does not work. I also can not find a way to enter the system for a "sudo" entry. The clock glitch is in Windows 7. It began after I installed Ubuntu One on a different hard drive.

---

### Post by matt_symes on 2011-10-18
Hi

> **Judaic Christian said:**
> My computer says that my password is: login.
Where does it say this ? Can you post a screen shot ? If you can't enter a password then that is your main problem. Are you saying you can't even login ?
>  But it does not work. I also can not find a way to enter the system for a "sudo" entry. I have never used Ubuntu One, however i would have thought you would have been able to get a console or a terminal.

Try pressing ALT and F2 together. Then type 

```
gnome-terminal
```or even

```
xterm
```You can reset your password with the command (assuming the problem is not something different)

```
passwd <your_user_name> 
```> The clock glitch is in Windows 7. It began after I installed Ubuntu One on a different hard drive.The clock issue is being caused by Ubuntu one setting the harware clock to UTC. Windows uses local time. When you boot into Windows the hardware clock is stilll set to UTC.

Kind regards

---

### Post by Judaic Christian on 2011-10-19
> **matt_symes said:**
> Hi
 
 
Where does it say this ? Can you post a screen shot ? If you can't enter a password then that is your main problem. Are you saying you can't even login ?
I have never used Ubuntu One, however i would have thought you would have been able to get a console or a terminal.
 
Try pressing ALT and F2 together. Then type 
 
```
gnome-terminal
```or even
 
```
xterm
```You can reset your password with the command (assuming the problem is not something different)
 
```
passwd <your_user_name> 
```The clock issue is being caused by Ubuntu one setting the harware clock to UTC. Windows uses local time. When you boot into Windows the hardware clock is stilll set to UTC.
 
Kind regards
[SIZE=2]I tried the  ALT and F2 and was not able to make an entry. Does the clock issue have to do with the mother board? I thought seperate drives would prevent such glitches.:confused:[/SIZE]

---

### Post by kc1di on 2011-10-19
I think he may be talking about having installed Ubuntu One (The windows version) and does not have ubuntu itself installed.

If so I believe he will have to set up a Ubuntu One account and password.  

Just guessing though

---

### Post by Judaic Christian on 2011-10-19
> **kc1di said:**
> I think he may be talking about having installed Ubuntu One (The windows version) and does not have ubuntu itself installed.
 
If so I believe he will have to set up a Ubuntu One account and password. 
 
Just guessing though
[SIZE=2]I paid a professional computer tech to install windows version of Ubuntu One on a separate hard-drive. I did it that way in hopes of preventing any clashes with Microsoft software.[/SIZE]

---

### Post by Judaic Christian on 2011-10-19
[SIZE=2]I have been trying to make use of Ubuntu for two years without success. I tried installing on different computers, but they crashed and burned.[/SIZE]:( [SIZE=2]And so that is why I paid a computer tech to install Ubuntu.[/SIZE]

---

### Post by Judaic Christian on 2011-10-19
> **kc1di said:**
> I think he may be talking about having installed Ubuntu One (The windows version) and does not have ubuntu itself installed.
 
If so I believe he will have to set up a Ubuntu One account and password. 
 
Just guessing though
[SIZE=2]Why do I need to set up an account and password with Ubuntu One. That is why I'm trying to get away from Microsoft. I do not like being Micro managed.[/SIZE]

---

### Post by kc1di on 2011-10-19
> **Judaic Christian said:**
> [SIZE=2]Why do I need to set up an account and password with Ubuntu One. That is why I'm trying to get away from Microsoft. I do not like being Micro managed.[/SIZE]

Hi Judaic Christian,

I'm not exactly sure what you are trying to do. Ubuntu is a linux based Operating system.  Your confusing with Ubuntu One which is a cloud storage applications that comes with Ubuntu.  Ubuntu One comes in a Windows application also and I suspect that is what has been installed on your hard drive.  Ubuntu one requires you to open and account so you can acess your cloud storage.  which gives you 5 Gb for free. 

If your interested in trying Ubuntu the operating system on your machine.  you can do that by but down loading the ISO image and burning it to a CD disc or usb stick.  Then you can run it without changing anything on your Hard drive and give it a try in the live mode.  

here are some links that may be of help.[https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

[https://one.ubuntu.com/help/]("https://one.ubuntu.com/help/")

[https://wiki.ubuntu.com/BeginnersTeam]("https://wiki.ubuntu.com/BeginnersTeam")

hope this is of some help.
Dave ;)

---

### Post by matt_symes on 2011-10-19
Hi

> **kc1di said:**
> I think he may be talking about having installed  Ubuntu One (The windows version) and does not have ubuntu itself  installed.

If so I believe he will have to set up a Ubuntu One account and password.  

Just guessing though

That's an excellent call kc1di. I have no real hope of helping in this thread then as i have no idea how  the windows version operates. To be honest, i did not even know there was one.

> **Judaic Christian said:**
> [SIZE=2]I paid a professional computer tech to install windows version of Ubuntu One on a separate hard-drive. I did it that way in hopes of preventing any clashes with Microsoft software.[/SIZE]

@Judaic Christian. Can you not get tech support from the person who installed the software ? They will know what they configured for you. 

People will also help you on here of course.

Kind regards

---

### Post by Judaic Christian on 2011-10-20
> **kc1di said:**
> Hi Judaic Christian,
 
I'm not exactly sure what you are trying to do. Ubuntu is a linux based Operating system. Your confusing with Ubuntu One which is a cloud storage applications that comes with Ubuntu. Ubuntu One comes in a Windows application also and I suspect that is what has been installed on your hard drive. Ubuntu one requires you to open and account so you can acess your cloud storage. which gives you 5 Gb for free. 
 
If your interested in trying Ubuntu the operating system on your machine. you can do that by but down loading the ISO image and burning it to a CD disc or usb stick. Then you can run it without changing anything on your Hard drive and give it a try in the live mode. 
 
here are some links that may be of help.[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
 
[https://one.ubuntu.com/help/](https://one.ubuntu.com/help/)
 
[https://wiki.ubuntu.com/BeginnersTeam](https://wiki.ubuntu.com/BeginnersTeam)
 
hope this is of some help.
Dave ;)
[SIZE=2]Good grief! A computer tech could not even get it right. I'm tired of playing around. So I need to wipe the hard-drive to INSTALL what these days. No trial CD's. Remember, I have Windows 7 on my computer. Everyone needs to keep in mind that people are not familiar with Ubuntu ways of doing things. I have to use the back door even to access Ubuntu.[/SIZE]

---

### Post by nutznboltz on 2011-10-20
@Judaic Christian switch to [https://www.dropbox.com/](https://www.dropbox.com/) you'll never regret it, I'm sorry to say but it's so very true and I don't want to see you suffer with UbuntuOne which is that cause of so many people's suffering it seems obvious.

I just hope Canonical, LTD doesn't end up on the receiving end of a civil suit against them because of UbuntuOne.

---

### Post by Judaic Christian on 2011-10-20
> **nutznboltz said:**
> @Judaic Christian switch to [https://www.dropbox.com/](https://www.dropbox.com/) you'll never regret it, I'm sorry to say but it's so very true and I don't want to see you suffer with UbuntuOne which is that cause of so many people's suffering it seems obvious.
 
I just hope Canonical, LTD doesn't end up on the receiving end of a civil suit against them because of UbuntuOne.
[SIZE=2]I'm looking into it now. I just want a simple system that I can control.[/SIZE] [SIZE=2]What does a person need to do to find or get the password for Ubuntu One?[/SIZE]

---

### Post by Judaic Christian on 2011-10-20
> **nutznboltz said:**
> @Judaic Christian switch to [https://www.dropbox.com/](https://www.dropbox.com/) you'll never regret it, I'm sorry to say but it's so very true and I don't want to see you suffer with UbuntuOne which is that cause of so many people's suffering it seems obvious.
 
I just hope Canonical, LTD doesn't end up on the receiving end of a civil suit against them because of UbuntuOne.
[SIZE=2]Info storage is something that I do not need. Nor do I need a bunch of other software. I just want to be able to use my computer without having to get permission or give a password.[/SIZE]

---

### Post by ubu_dynamite on 2011-10-20
You are talking about UbuntuOne so people think you are talking about online storage.
Not setting or giving permissions and having no password to install or remove things is not really a smart thing todo.
You could set it to "Don't ask password add login" in users settings but you will still need a password to install and remove things.

---

### Post by Judaic Christian on 2011-10-20
> **ubu_dynamite said:**
> You are talking about UbuntuOne so people think you are talking about online storage.
Not setting or giving permissions and having no password to install or remove things is not really a smart thing todo.
You could set it to "Don't ask password add login" in users settings but you will still need a password to install and remove things.
[SIZE=2]OK, so how do I find or add my password. The software presumes I have a password already. There has been no such entry. Do you have to register to have a password for your software to work?[/SIZE]

---

### Post by ubu_dynamite on 2011-10-20
> **Judaic Christian said:**
> [SIZE=2]OK, so how do I find or add my password. The software presumes I have a password already. There has been no such entry. Do you have to register to have a password for your software to work?[/SIZE]

If you mean the password for the operating system ubuntu then no you don,t have to register you will have to ask the person who installed the system for the password.

If you want to use the online storage ubuntuone then yes.

---

### Post by Judaic Christian on 2011-10-20
[SIZE=4][COLOR=blue]Forgive me. The computer tech did enter a password, but failed to inform me.[/COLOR][/SIZE]

---

