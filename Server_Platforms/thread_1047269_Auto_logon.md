---
title: "Auto logon"
date: 2009-01-22
forum: Server Platforms
---

### Post by happyhacker on 2009-01-22
How do I get XP to autologon to the user share on the server? I want this to happen when the user switches on and starts their windows account. At the moment a logon screen coms up asking for the server username.

---

### Post by bluefrog on 2009-01-23
make xp ask for a password at login screen and use the same user as your samba user.

basically a user needs to enter a password at least once when switching on a computer.

If you don't bother at all about passwords (your problem), make samba share free to use and write for everybody.

---

### Post by happyhacker on 2009-01-29
I have setup passwords and now need to log on to XP for that user. But when I go to Network Places and to the share on Ubuntu, I still need to logon to that share. This also means SyncToy backups can't run because of the need to logon. The samba usernames and passwords are the same.

How do I get XP to log onto it's server shares automatically?

---

### Post by spynappels on 2009-01-29
Another option is to connect the shared folder as a Network Drive in Windows. If you go to the "Map Network Drive" tool in Windows, you will be given the option of connecting as a different user, just put in your samba user and password and tick the reconnect at logon option.

That's how mine is set up anyway.

---

### Post by happyhacker on 2009-04-27
I have now done that for XP and can get it to auto logon. BUT I cannot get Vista to auto logon. I have setup a network drive and setup the "logon as a different user" (the vista admin account logon is different from the Ubuntu user logon) so the logon is the Ubuntu share, but the notice appears after switch on that "One or two network drives are not connected".

Does the Vista User logon really have to be the same as the linux share logon if the "logon as a different user" for the network drive has been configured?

Can anyone advise?

---

### Post by Thirtysixway on 2009-04-29
If you're using Samba, I wrote a blog post about automating samba login with a script:

[http://noobbox.com/2009/04/auto-mount-samba-share-ubuntu-and-windows](http://noobbox.com/2009/04/auto-mount-samba-share-ubuntu-and-windows)

---

### Post by happyhacker on 2009-04-30
I set this up on vista and it worked a treat. One slight glitch is that when logging on I find the program which detects that the network drives have not connected is run before the task and the little window comes up announcing the failure, but going into Computer shows the zs: drive to be there and connected. Thanks.

---

### Post by Thirtysixway on 2009-04-30
> **cantthinkofanickname said:**
> I set this up on vista and it worked a treat. One slight glitch is that when logging on I find the program which detects that the network drives have not connected is run before the task and the little window comes up announcing the failure, but going into Computer shows the zs: drive to be there and connected. Thanks.

ah. Perhaps there's a way to change the startup order?  Or there might be a DOS command to pause X number of seconds.

---

