---
title: "need to find ssh host file...but where is it?"
date: 2007-07-23
forum: Server Platforms
---

### Post by toecutter on 2007-07-23
EDIT - I remembered I had to show hidden files while typing all this out, but forgot to change the title of the thread :) Sorrry! I need to know how to correctly edit the ssh host file...


------------------

I must be missing something really obvious but I can't figure out how to properly edit the SSH hosts file at:
  /home/frank/.ssh/known_hosts


What I've done is I'm setting up a MythTV box and previously was able to SSH to it when i first installed, but there were some problems getting things installed from repositories so I did a complete re-install with a fresh download, fresh CD, etc. Now, when I try to follow these instructions: [https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend#head-77200b6dfc6bd0e2e162e9d97d3892ee0a145c35](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend#head-77200b6dfc6bd0e2e162e9d97d3892ee0a145c35) I get an error when I try to login, I get a message saying 

```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
86:xxxxxxxxxxxxxxxx.
Please contact your system administrator.
Add correct host key in /home/frank/.ssh/known_hosts to get rid of this message.
Offending key in /home/frank/.ssh/known_hosts:1
RSA host key for 192.168.1.2 has changed and you have requested strict checking.
Host key verification failed.
```

Problem is, I don't know how to properly edit /home/frank/.ssh/known_hosts (everything looks scrambled or encrypted), or at least add the RSA key through the terminal - I believe when I first did this the RSA key was added automatically. 

Can someone let me know how to add the RSA key please? when I do ifconfig on the MythTV box, do I need to add one of the numbers that comes up?

Thanks for any help!

---

### Post by bernied on 2007-07-23
The simplest way, rather than editing the file, might just be to rename it. Do this logged in as frank:
```
mv ~/.ssh/known_hosts ~/.ssh/known_hosts.old
```
You will then get a different message next time you log in, saying you don't know this host, just answer yes and you're back in business.

Just reverse the names if you want to restore it.

Or, if you want to do it a bit cleaner...
I use nano for editing these files
```
nano ~/.ssh/known_hosts
```in nano, Ctrl K deletes a line, and the line you want to delete is the first one. So, make a copy (backup), open the file, hit Ctrl K, Ctrl O (write Out), and Ctrl X (eXit).

---

### Post by toecutter on 2007-07-23
gah....

OK I tried both methods you demonstrated but both gave me this result:
```
frank@frank-linux:~$ ssh -X -Y frank@192.168.1.2
ssh: connect to host 192.168.1.2 port 22: Connection refused

```

I didn't get the message about the host when I renamed the file to '.old'

Any suggestions?

---

### Post by murraymca on 2007-07-23
Are you using public key authentication only, or do you allow password?

I would also make sure that ssh is still running on the server (sorry if is an offensive idea :().

If you don't connect elsewhere, I would delete everything in ~/ssh/known_hosts and leave the file blank...

---

### Post by toecutter on 2007-07-24
to be honest I don't really know - I'm just trying to set up my mythTV box using the 'Install Open SSH Server' instructions here: [https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend#head-77200b6dfc6bd0e2e162e9d97d3892ee0a145c35](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend#head-77200b6dfc6bd0e2e162e9d97d3892ee0a145c35)

I don't know anything about SSH but am just following the instructions word for word...

When I get home I'll try deleting the /known_hosts file completely and give that a shot...

---

