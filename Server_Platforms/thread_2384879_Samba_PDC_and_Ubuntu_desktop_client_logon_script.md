---
title: "Samba PDC and Ubuntu desktop client logon script"
date: 2018-02-13
forum: Server Platforms
---

### Post by ggrom on 2018-02-13
Hi all,

I managed to configure an UBUNTU 16.04 Server as PDC using Samba; I can successfully add Ubuntu or Windows client to the domain and all the users I created can access the network resources.

I managed to let the Windows client run the logon script, thanks to which for example I am able to mount the "H: disk" for the user that is logging in on the Windows client.

I would like the Ubuntu client to do something similar; I'd like to have a unique logon bash script in the server that the Ubuntu client fetch and execute when the user logs on the client itself.

I've been googling a lot to find a solution but I didn't make it; can you please help me out!


Thanks a lot in advance!

---

### Post by LHammonds on 2018-02-13
This sounds like something I will need to do at some point.  I'm [currently researching](http://hammondslegacy.com/forum/viewtopic.php?f=40&t=235) how to do this with my own home network...but using a Raspberry Pi as my server. ;-)

Are you using Likewise to get your Linux machines to join the domain?

LHammonds

---

### Post by ggrom on 2018-02-13
I am using a Dell workstation running Ubuntu Server; to join the domain on the Linux client I just use samba and winbind.

I suffered a bit but I made it :).

Just need to figure out how to "push" a common logon script to the Linux client as I am doing on the Windows one


Gigi

---

### Post by LHammonds on 2018-02-13
Did a bit of searching and dang near everything out there about Samba and login scripts talk ONLY about Windows PCs with a DOS-formatted "logon.bat" file with Windows-only commands in it like NET USE.

I do know that commands in ~/.profile get executed every time a user logs in but that is specific to that user and on the local machine.

I do know that commands in /etc/profile get executed every time ANY user logs in but that is also specific to the local machine.

Not currently sure how to get commands on a Samba DC to run on a Linux PC client that gets connected by simply joining and logging in.

I'm fairly ignorant with zero experience in this but if you could modify each machine that is joined to your domain by editing the /etc/profile and have it reference a script stored on your PDC, that could serve to run as a common login script (for Linux systems).  That would let you make changes to your login script that Linux PCs could pick up after each time they login rather than modifying the PCs directly.  Might need to add some error handling in there in case that machine is not connected to the network or cannot see the PDC.

**EDIT #1:** I don't run a GUI Linux PC so this may only apply to terminal sessions only.  Again, I'm out of my element here when talking about a desktop GUI. hehehe.

**EDIT #2:** [Login script when logging into Ubuntu Desktop]("http://xmodulo.com/how-to-automatically-run-script-when-logging-into-ubuntu-desktop.html")

**EDIT #3:** [Adding program to session startup]("https://help.ubuntu.com/community/AddingProgramToSessionStartup") (this might not work for 2nd person that logs into that machine though)


LHammonds

---

### Post by ggrom on 2018-02-14
Hi there!

Thanks for your time, very appreciated!

As I said, everything smooth for Windows clients; for the Ubuntu/Linux client the solution I adopted is:

- create a couple of bash script (userlogin.sh, userlogout.sh)
- edited the files .profile and .bash_logout in the folder /etc/skel so that the relevant script, userlogin.sh and userlogout.sh respectively

I was looking for something more "centralized", it's a pity that you have to update all the clients scripts when needed.

It's strange that in this case Windows is a bit better :D


Cheers!

Gigi

P.S.: I can share with you what I did if you wish, just tell me!

---

### Post by LHammonds on 2018-02-14
When you say "Ubuntu Client" are you talking about the graphical user interface or a terminal?

From what I have been reading, the .profile is not activated when someone logs into the graphical interface, only when they open a terminal.

Also, the /etc/skel (profile skeleton template) is not idea either because that is used to create the home files upon the very 1st time a person logs in and is never referenced again after that.

If you are talking about terminal logins, then the global /etc/profile would be the best place to make changes because you would only need to change that one location no matter if 1 person has already logged in once or 10,000.  It also prevents the end-user from editing out the login script (they can edit ~/.profile, they cannot edit /etc/profile)

Also, why not issue a mount command in .profile to mount a share on your PDC that contains your login script, then execute it from that centralized location, then unmount?  The only thing on the PCs would be static mount/run commands and the actual login code could be contained in a central location on your server.

LHammonds

---

