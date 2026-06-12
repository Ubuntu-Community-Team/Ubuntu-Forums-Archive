---
title: "policykit, remote connection and user's privileges"
date: 2008-03-01
forum: Security Discussions
---

### Post by frafu on 2008-03-01
Hello,

I have a computer running ubuntu hardy into which I login remotely by using nx from nomachine.com. (ubuntu hardy is running the nx server and the nx client is running on macosx) 

Is there a simple way to configure policykit to give me in the nx session the same privileges as when I log in localy? 

In fact, if I set ubuntu hardy to autologin and I connect remotely with vnc to that session, I can for example unlock the Network Settings panel, the usb sticks are mounted on the desktop,... 

However, if I open the ubuntu hardy session through nx, the unlock button of the Network Settings panel is always greyed, when inserting a usb stick I get the message that I don't have the necessary privileges to mount it,... 

I suppose that I have to edit something in System -> Administration -> Authorizations... 

Thanks in advance for any help. 

Francesco

---

### Post by frafu on 2008-03-04
bump

---

### Post by croemmich on 2008-04-14
I am having the same problem. When I run apps that use PolicyKit in a remote NX session I get errors similar to the one below.

** (time-admin:8933): CRITICAL **: Unable to lookup session information for process '8933'

I do not know exactly how NX sessions work, but the problem is probably related to that.

---

### Post by durus on 2008-04-25
I am having the same problem. Do anyone know the solution ?

---

### Post by aboutblank on 2008-04-25
Same problem here :-(

---

### Post by sylaan on 2008-04-26
Same here ...

---

### Post by aboutblank on 2008-04-26
[This guy]("https://bugs.launchpad.net/ubuntu/+bug/221363") seems to know that it was caused by NX server but doesn't provide a solution. 

I'm wondering if we should open another ticket in addition to the one above? I looked on nomachine's website and couldn't find any trouble tickets matching our problem.

---

### Post by volksman on 2008-04-27
Hey All!

I haven't found a fix to this yet either.  My comment on the bug was simply because I was/am still learning about policykit and at this time believe that the bug should actually be opened with Nomachine and not Ubuntu/Gnome.

I could be very wrong about that.  Glad I was pointed to this thread as I hope someone with more smarts than me can help out.

If you guys think this is something that the Ubuntu team should work on I will re-file the bug more appropriately.

---

### Post by whatsinaname on 2008-04-28
I am concerned about this as well.  my 7.10 box was headless and now because of upgrade I can not administer it effectively with nx  (I am kind of slow with using command line GUI is always better for me)

For now I have hooked up monitor keyboard and mouse.  That allows me to click the unlock button and use applications like normal.

If I find an answer I will post here, I am still wet behind the ears with Linux but its fun to try and figure it out :)

---

### Post by volksman on 2008-04-28
We've all been there at one point or another.  A simple solution for you right now is to run VNC (Preferences -> Remote Desktop).  Polkit works fine over VNC.  So when you need to make an admin change you can use VNC...For everything else use NX.  I know it's less than desirable but it works for now...

I will be testing Shadow sessions in NX tomorrow to see if it overcomes the problem as well...

---

### Post by volksman on 2008-04-30
Shadow sessions with NX works as well.

Bug re-opened and edited.

---

### Post by frafu on 2008-04-30
Hello volksman

Thanks for the piece of information. 

Could you please tell me how to open a shadow session with NX. I cannot find a corresponding option in the NX client on Mac OS X. 

Are shadow sessions also available with the free edition of the nx server? 

Francesco

---

### Post by volksman on 2008-04-30
I should clarify I use NomachineNX not FreeNX.  However the option is in the client where you specify the OS type.  It is set to Unix by default and if you use the dropdown the last option is 'Shadow'.

I thought FreeNX used the Nomachine client so it should be there.  Not sure if FreeNX server supports the functionality though.

---

### Post by frafu on 2008-05-01
Hello, 

Thanks for pointing me to the right spot. (I did not open the OS Type menu.) 

To be precise, I am also using the NX server from nomachine, but the [free edition]("http://www.nomachine.com/select-package.php?os=linux&id=1"); and I can confirm that it also works here, if there already is a gnome session running on the remote computer; I the remote computer is showing the gdm login screen, it tells me that gdm is not a valid user. (Adding gdm to the nx group might solve the problem, but I have not tried.) 

Cheers 

Francesco

---

### Post by crazy___cow on 2008-05-07
I have resolved this issue changing policies in System->Administration->Authorizations->org->freedesktop->policykit... and setting Console Implicit Authorizations to Yes.
You can also change Implicit Authorizations for hal->storage to mount/umount usb disk during a freeNX session....

---

### Post by gozotto on 2008-05-07
I've tried your solution but nothing happens. I test it with the users-admin tool and the unlock button is still disabled and I can change nothing.
Do you have changed anything else?

My current settings:
Anyone: No
Console: Yes
Active Console: Admin Authentication (keep indefinitely)

---

### Post by crazy___cow on 2008-05-08
The button remains greyed, but I can change permissions!Try to set Anyone=yes also and see what happen next!

---

### Post by sylaan on 2008-05-10
I tried it but it makes no difference for me. "Unlock" button stays disabled and I can't modify anything :(

---

### Post by mike3244 on 2008-05-13
I have the same issue with vncserver on an Xubuntu box connecting with TightVNC

---

### Post by spooner on 2008-05-14
I'm having the same problem with simple "ssh -X". Whats the point of an ubuntu server that you can't administer remotely? Had to resort to useradd and now I can't seem to get the right profile loaded...
grrr.

---

### Post by spooner on 2008-05-15
Sorry was being dense...
Just changed everything in policykit to "requireadmin autherisation" then it allows you to make changes... pity I can't do this remotely. You should be able to start policykit with admin rights remotely...

---

### Post by gozotto on 2008-05-29
Any news regarding this problem?

Regards
gozotto

---

### Post by spooner on 2008-06-18
Ok, gonna throw another spanner in the works...
PolicyKit works fine remotely to my other Ubuntu machine (via ssh -X). I can login run "users-admin" unlock it and add users.
If I login via putty and xming (windows ssh -X) it doesn't work. If I try and login from an Ubuntu VM on my laptop (via ssh -X) policyKit doesn't work.... the error is

** (users-admin:#####): CRITICAL **: Cannot create session bus: Failed to connect to socket /tmp/dbus-############: Connection refused

Where the process name and random string have been replaced by #'s.

Any ideas?

---

### Post by pvdploeg on 2008-07-07
Here is what I did to start an application like users-admin on my hardy server (under VMWare) from my hardy laptop. (which presented the problem of not being able to add users because the unlock button is greyed). Perhaps it helps.
1. On the hardy server (installed under VMware from the 8.04 server iso) I installed the gnome system tools, policykit and policykit-gnome via the usual apt-get commands.
2. from the laptop I log into the server using Putty. Lets say with user PPP defined on the server. X-Forwarding enabled.
3. In the Putty terminal I run 'sudo polkit-gnome-authorization'. After typing the PPP pasword, the polkit-authorization  dialog appears on the laptop.
4.In the left pane I choose Manage System Configuration (under systemtoolsbackends) and in the right pane Grant user PPP authorization. 
5. close the dialog and reboot the hardy server
6. login from the laptop with Putty again. Now I can start users-admin and the add-user button is not greyed and can be used. I ca add users on the server from my laptop using the graphical tools.

The fact that one has to grant a user permission to do some particular actions on a server via a remote connection seems to make sense to me, but I am quite new to all this so I might be mistaken.

Hope this helps.

regards
Pieter van der Ploeg

---

