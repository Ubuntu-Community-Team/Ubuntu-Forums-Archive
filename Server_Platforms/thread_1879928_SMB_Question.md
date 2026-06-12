---
title: "SMB Question"
date: 2011-11-12
forum: Server Platforms
---

### Post by not12listen on 2011-11-12
I've done some searching, and have found no results on my question.  If I am posting in the incorrect area, please let me know.  Thanks!

My question is as follows:
I will be setting up a new Ubuntu Server 11.04 (64bit) machine shortly, as my Windows Server is less than stable.

Within Windows I have the ability to hide a share - it is only viewable/accessible if you know the exact path.  Can this be done with SMB?

And, to add to the mix, I want to be able to browse over my network from a Windows desktop to my Ubuntu Server and NOT be able to plainly see those hidden folders.


My apologies if what I've described above does not make sense or if my description is poor.  I'll gladly explain it in more detail if necessary.

Thanks again!

---

### Post by Morbius1 on 2011-11-12
There is a parameter that you would need to add to the share definition for that particular share that makes it un-browseable:
```
browseable = no
```

---

### Post by not12listen on 2011-11-12
> **Morbius1 said:**
> There is a parameter that you would need to add to the share definition for that particular share that makes it un-browseable:
```
browseable = no
```

ah!  very nice. :)  now, as i am very unfamiliar with the Console way of setting those permissions and options, is there a way to put that into the share permissions when using the GUI (KDE) ?

if not, please do not strike me down with 'noob' fire. :)

---

### Post by SeijiSensei on 2011-11-12
You might be able to do that by using the [SWAT]("https://help.ubuntu.com/community/Swat") utility.  I'm a command-line guy myself; most of us managing Linux servers tend to be.  I manage a number of remote servers by connecting with SSH and typing commands.  GUIs are fine if you have physical access to the machine; for me, that's a rare situation.

---

### Post by not12listen on 2011-11-12
> **SeijiSensei said:**
> You might be able to do that by using the [SWAT]("https://help.ubuntu.com/community/Swat") utility.  I'm a command-line guy myself; most of us managing Linux servers tend to be.  I manage a number of remote servers by connecting with SSH and typing commands.  GUIs are fine if you have physical access to the machine; for me, that's a rare situation.

thank you very much!  i have no aversion to CLI at all (grew up with DOS 5.0 - 6.22), i just very, very little experience with Console.

in my scenario, i have 100% physical access to said Ubuntu Server, as it is in my home.

i'll give a bit of background to the situation, in hopes that it clears up a bit of confusion (due to my lack of verbage)...

i have a dedicated file server, currently Windows Server 2008.  it is unstable and enjoys rebooting randomly (despite new hardware throughout and a wipe/reload of the OS).  i wish to instead use a Linux distro (Ubuntu in this case) as my Server OS.

the majority of desktops in my home are Windows based, though the majority of laptops are dual boot (Win 7 & Kubuntu and/or BackTrack).

i have folders that are specifically setup for my access only and do NOT want them viewable by other Win clients (tools, utilities, etc).

i fully understand how to accomplish this with Windows, but want to do the same with Linux.

i hope that clears things up a bit. :)

---

### Post by Morbius1 on 2011-11-13
> **not12listen said:**
> ah!  very nice. :)  now, as i am very unfamiliar with the Console way of setting those permissions and options, is there a way to put that into the share permissions when using the GUI (KDE) ?

if not, please do not strike me down with 'noob' fire. :)
I haven't used KDE since version 3 so I can't help you much there but since it appears that you have KDE on that server all you need is a text editor.

Let's say you originally created a share on your server that allows write access to a specified number of users:
> [server-share]
path = /home/Share
valid users = bob, sally, morbius
read only = noTo make it so that it is "unbrowseable" ( I'm pretty sure that's not a word :) ) use a text editor and edit: /etc/samba/smb.conf and add the line:
> [server-share]
path = /home/Share
valid users = bob, sally, morbius
**[COLOR=Blue]browseable = no[/COLOR]**
read only = no[COLOR=Blue]BTW[/COLOR]: Be careful with SWAT. SWAT is destructive in that it doesn't edit the existing smb.conf it replaces it which means it's up to you to reconfigure the whole thing from the beginning. As I recall it doesn't make a backup copy of the original either so make a backup copy of the original just in case.

---

### Post by not12listen on 2011-11-17
> **Morbius1 said:**
> I haven't used KDE since version 3 so I can't help you much there but since it appears that you have KDE on that server all you need is a text editor.

Let's say you originally created a share on your server that allows write access to a specified number of users:
To make it so that it is "unbrowseable" ( I'm pretty sure that's not a word :) ) use a text editor and edit: /etc/samba/smb.conf and add the line:
[COLOR=Blue]BTW[/COLOR]: Be careful with SWAT. SWAT is destructive in that it doesn't edit the existing smb.conf it replaces it which means it's up to you to reconfigure the whole thing from the beginning. As I recall it doesn't make a backup copy of the original either so make a backup copy of the original just in case.

thank you very much for the 'plain speak' walkthru and examples! :)  very helpful!

i'll put the changes into effect and report back with my findings.

---

### Post by not12listen on 2011-11-17
alright.  i've downloaded emacs, and editted the 'smb.conf' and created a new entry based upon a 'shared' folder that i created for this test.

i've made sure that the usernames and passwords on my Win7 desktop and Kubuntu 11.10 (64bit) laptop are the same.

unfortunately, i cannot gain access to the share on my Kubuntu laptop.

i know that in Windows, you can specify which domain you are connecting from, and i've put in the Kubuntu host machine machine and username.

this is what it looks like when i originally try to connect:
(Domain/Username)
rorschach\joel

i changed it to:
Kubuntu-LT\joel

unfortunately, neither allowed me access to the Kubuntu laptop.

i did create a 'test' user account on the Kubuntu laptop and tried connecting with it - it did work.  to be clear, the account 'test' does not exist on my Windows machine.

i've no doubt there is a small detail that i'm missing.  i did NOT uncommnent any lines of the 'smb.conf' except those specifically related to shares.

thanks for any help in advance!

---

### Post by Morbius1 on 2011-11-17
> i did create a 'test' user account on the Kubuntu laptop and tried  connecting with it - it did work.  to be clear, the account 'test' does  not exist on my Windows machine.If it works with user=test then it appears the share was defined correctly so maybe it's a authentication problem. Windows does a very odd thing in that it passes it's local Windows login user name and login password when it connects to a remote share so the user name and samba password on Kubuntu must match exactly ( and I mean exactly ) the Windows local login user name and password. Either that or you must pass the samba password you created for that Windows user.

BTW, I'm assuming that somewhere along the line you gave this Windows user a samba password:
```
sudo smbpasswd -a windows-user-name
```

---

### Post by not12listen on 2011-11-17
> **Morbius1 said:**
> If it works with user=test then it appears the share was defined correctly so maybe it's a authentication problem. Windows does a very odd thing in that it passes it's local Windows login user name and login password when it connects to a remote share so the user name and samba password on Kubuntu must match exactly ( and I mean exactly ) the Windows local login user name and password. Either that or you must pass the samba password you created for that Windows user.

BTW, I'm assuming that somewhere along the line you gave this Windows user a samba password:
```
sudo smbpasswd -a windows-user-name
```

i would agree that it is an authentication problem.

i've made 100% sure that the usernames and passwords on both machines are absolutely identical.

i do know that one thing that Windows does differently is when it connects to any share, it also passes along the machine name (Rorschach in this case) or the Domain name (if it is a member of a domain, which mine is not).

that is exactly why i tried 'tricking' it by specifying 'Kubuntu-LT' (the machine name of my Kubuntu machine) in hopes that it would accept it.

i did not perform the smbpasswd as you've noted above - i am very, very new to all things SMB related.  i will try it this evening and report back my findings.

and thank you very much for the assistance! :)

---

