---
title: "I need a root password"
date: 2013-12-11
forum: Security
---

### Post by wt-pm66 on 2013-12-11
OK, before anyone jumps up telling me I don't need root access, or something like that please read the question. Sorry if that sounds ugly, but I have read way too many questions this morning (about and hour and a half worth) about root password where the only answer is you don't need root instead of helping the person. I've also read the forum rules, it's not against the rules to give instruction on how to get root, it's just requested to instruct noobs to a article explaining why it's bad. I understand it's bad, and don't really want a root, but I have to have one for this. 

I am trying to install a network printer, and having problems. During my course of trying to track down the problem, I have found the need to run a diagnostic for either hplip, or cups I don't remember right now (that was yesterday, I've done too much since then). Anyway, it runs for a couple of minutes, then ask for "ROOT" password. My regular user password does not work. Since it's running in it's own window, I'm not able to do a sudo -i or whatever else you run in terminal to gain temporary access, I have to have THE ROOT password. I found instructions that said reboot into recovery, drop to root shell, and enter mount -o rw remount/, I get an error that remount is not found in etc/fstab/ or etc/mtab/. I don't really want to just start adding lines to files, unless I know what I'm doing. So does anyone know a good way for me to get a root password that I can enter in the diagnostic terminal? Any help would be appreciated.

---

### Post by steeldriver on 2013-12-11
Hello and welcome to the forum

Here are a couple of things to try

1. make sure your user is a member of the lpadmin group e.g. in a terminal

```
sudo gpasswd --add *username* lpadmin
```

then log out and back in

2. also in a terminal, run the command

```
gksu-properties
```

and make sure the 'Authentication mode' is set to **sudo** not **su**

See if that helps - your remount command has a simple syntax error, but let's not go there yet (it should not be necessary to enable the root account). It's hard to guess from your description but if the printer is being discovered using SAMBA/SMB, sometimes the SAMBA utilities ask for ROOT's password but they don't really need it and will continue if you just press 'Enter'.

---

### Post by bashiergui on 2013-12-11
There is no root password by default. you have to enable the root account password first. This tells you how. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
Once you scroll past the lecture on how you shouldn't enable the root password you'll find the instructions.

If you're still having problems setting up the metwork printer then post some error codes or problems you encounter. Chances are others have encountered the same problems and have found solutions they can share.

---

### Post by oldos2er on 2013-12-11
The correct command to mount with read/write access is ```
mount -o rw,remount /
```

---

### Post by Mark de J on 2013-12-11
If you want change the password of the root account, open a terminal (cntrl+alt+t) and enter this command:
```
sudo passwd root
```

Then you can change the password for the root account.

---

### Post by deadflowr on 2013-12-11
I don't know anything at all about hplip but if you want to know more and control cups open a browser and in a new tab enter this
```
localhost:631
```
the cups windows should show, with helpful tips and the like.

As far as needing a ROOT password, I haven't the faintest idea what program or command you're using that what demand one, which cannot use the built-in privilege escalation system(sudo) already in place on Ubuntu.

---

### Post by steeldriver on 2013-12-11
The only instances I've come across are the ones I mentioned above i.e.

1. recent incarnations of gksu seem to have defaulted to su mode - this may affect authentication popups from the CUPS web interface; running

```
gksu-properties
```

and changing the authentication mode to 'sudo' in the drop down box should fix that; and

2. running 'sudo smbtree' always asks for root's password (but proceeds happily if you just press 'Enter')

```

$ sudo smbtree
[sudo] password for steeldriver:
Enter root's password:
WORKGROUP
        \\ALICE
                \\ALICE\Public
                \\ALICE\print$          Printer Drivers
                \\ALICE\IPC$            Remote IPC
                \\ALICE\Canon MF4320-4350 (FAX) Canon MF4320-4350 (FAX)
                \\ALICE\Canon MF4320-4350       Canon MF4320-4350
                \\ALICE\C$              Default share

```

which may be an issue if the networked printer is on a remote Windows host

---

### Post by BBQdave on 2013-12-11
> **wt-pm66 said:**
> ...it runs for a couple of minutes, then ask for "ROOT" password. ...I have to have THE ROOT password.

Perhaps not the issue you are facing, but I would be careful giving *root* priviledges to your network printer.

I had an issue with a Samsung ML-2955DW network printer. Had to dig for information (and printer makers came clean on problem), there is a built in program (not adjustable by consumer software) that dials home to the manufacturer. This open door was exploited, compromising networks. My home network went nuts after hooking up the printer. Mainly Windows' machines with problems (under attack).

As I could not get to the manufacturer software in the network printer (access not allowed by consumer), I solved it by pulling it from the network, and now it is a USB printer. The bigger bummer, is that from what information I could gather, most manufactures have some application built in to their network printer to dial home (and not controllable by conumer).

After cleaning the Windows' machines and fresh re-install of Ubuntu on my notebook (as precaution), I do not trust network printers. And I would not give a network printer root priviledges to your machine.

---

### Post by cariboo on 2013-12-11
> So does anyone know a good way for me to get a root password that I can enter in the diagnostic terminal? Any help would be appreciated.

You don't need a root password, but to drop to a root shell in a terminal use:

```
sudo -i
```

---

### Post by bab1 on 2013-12-11
> **steeldriver said:**
> The only instances I've come across are the ones I mentioned above i.e.

1. recent incarnations of gksu seem to have defaulted to su mode - this may affect authentication popups from the CUPS web interface; running

```
gksu-properties
```

and changing the authentication mode to 'sudo' in the drop down box should fix that; and

2. running 'sudo smbtree' always asks for root's password (but proceeds happily if you just press 'Enter')

```

$ sudo smbtree
[sudo] password for steeldriver:
Enter root's password:
WORKGROUP
        \\ALICE
                \\ALICE\Public
                \\ALICE\print$          Printer Drivers
                \\ALICE\IPC$            Remote IPC
                \\ALICE\Canon MF4320-4350 (FAX) Canon MF4320-4350 (FAX)
                \\ALICE\Canon MF4320-4350       Canon MF4320-4350
                \\ALICE\C$              Default share

```

which may be an issue if the networked printer is on a remote Windows host
The prompt is a Samba prompt for the account Samba user account for the user root.  When you hit enter it just logs you on as the guest user.  This is not an instance of needing root powers.  It is for authentication (who are you) rather than authorization (you are allowed to do that).

---

### Post by houstonbofh on 2013-12-11
OK...  Quick way to do this, and then undo it after...

sudo cp /etc/shadow /etc/shadow.bak

(This backs up your passwords.)

sudo passwd root

(This gives root a password.)

After you are done...

sudo cp /etc/shadow.bak /etc/shadow

(This removes the root password.)

---

### Post by bashiergui on 2013-12-11
The root terminal doesn't solve the op's problem because a gui window spawned by a non-root process asks for the root password.

at any rate, let's look at the big picture. The fact that installing a network printer has resulted in requiring a root password indicates that something in the process has gone awry. The question is technically solved because the op can now create a root password. However that solution is kind of like giving a course correction to a train that went off the rails 5 miles ago.

---

### Post by cariboo on 2013-12-11
> **bashiergui said:**
> The root terminal doesn't solve the op's problem because a gui window spawned by a non-root process asks for the root password.

at any rate, let's look at the big picture. The fact that installing a network printer has resulted in requiring a root password indicates that something in the process has gone awry. The question is technically solved because the op can now create a root password. However that solution is kind of like giving a course correction to a train that went off the rails 5 miles ago.

Actually the only thing that has changed, is the way gksu works. For whatever reason, the default behaviour when issuing a gksu+command is su, when it should be sudo, as has been posted earlier in this thread, the solution is fairly simple, just run:

```
gksu-properties
``` 

to change what gksu does when you run it.

As an aside, it looks like the default gksu behaviour is set to sudo in Trusty.

---

