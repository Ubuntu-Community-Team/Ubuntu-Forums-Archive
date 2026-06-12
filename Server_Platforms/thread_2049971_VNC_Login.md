---
title: "VNC Login"
date: 2012-08-29
forum: Server Platforms
---

### Post by mrbrooks on 2012-08-29
Hi all, im using 12.04 Server, I have installed the vnc4server and am also using webmin and have SSH enabled so I have more than one way in.

The problem, when I issue the command - vncserver -geometry 1024x768 to start a VNC session from webmin or from sudo/su  either from the server itself or from SSH Console and i try to login to the VNC session I just get a blank screen. Ive gone through a few posts and modify the .vnc/xstartup but this doesnt change my issue.

The issue really is this, if i issue the command directly on the server, without sudo/su and then login via the VNC client (either Remmina or SSL/SSH VNC Viewer) it works without issue. It is only when the command is issued from 'root' that problems occur.

So I figure (thought am not certain) this is most likely a permissions issue of some description, ie, service is started by 'root' but am trying to utilise it, ie, login with a non 'root' account. 

The scenario I would ideally like to get to get working, is to be able to issue the command from the comman shell within  Webmin, but of course whenever I do this, the system thinks it is 'root' and will just provide a blank screen when attempting to login via VNC.

Alternatively I could of course start a session automatically for the user in question at startup, however I would not know where to start...

Any guidance and advice is most appreciated...

mrbrooks

---

### Post by CharlesA on 2012-08-30
Why do you want to use VNC? IF you need access to the GUI remotely, check out FreeNX, or you could just forward X over SSH.

---

### Post by mrbrooks on 2012-08-30
Hi Charles, thanks for the reply, re using VNC, that was just was suggested to me by other people, the server in question is being used by someone who doesnt really know a great deal about how to admin stuff (im no expert myself either) which is why I added webmin as they need some sort of GUI for the admin stuff like adding users etc...
 
They are using it mainly as a file server with Samba running, to share files amongst 5 windows PCs, this all works great and they are pretty happy with it and I glad cos they were on a windows box and didnt really want to pay for a new version of windows server or update the hardware just yet, hence the move to Linux.
 
So re the GUI elements, i read a how to about putting on a gnome-core install, that doesnt start with the server boot, only appears on remote session, the how to used vnc4server and TightVNC for windows. They wanted a basic GUI so they could jump in there now n then to take a look at thing in a more familiar way I suppose. I am very much open to alternatives if the community members have got more thoughts on the matter and am willing to try new things out.
 
At the moment they are setting a vnc sessions via putty and then using the VNC client to login to the sessions. I just wanted to make the experience as smooth as possible for them and dont want them think its all too much trouble and just jump back to windows for the convenience factor without giving the Linux world a real go. 
 
Crazy as it sounds, they want to play music through the box, which is one of the reasons it needed a core gui, because the server is in the same room as an old windows box they were using to play the music and dont want to be logging into different machines.
 
I hope that all makes sense haha...
 
Thanks again for the input, i appreciate any offerings from the community.
 
mrbrooks

---

### Post by CharlesA on 2012-08-30
Are they only using the GUI to play music? If they have webmin installed, there shouldn't be any reason to have to do the same thing via the GUI.

---

### Post by mrbrooks on 2012-08-30
Hi Charles, how do they play music through webmin?
 
Thanks
 
mrbrooks

---

### Post by CharlesA on 2012-08-30
I don't think you can, but you might want to look at Subsonic:
[http://www.subsonic.org/pages/index.jsp](http://www.subsonic.org/pages/index.jsp)

---

### Post by mrbrooks on 2012-08-30
Hi Charles, thanks for the reply, I just looked at subsonic and the Ubuntu software centre on my box said this package is of bad quality, etc etc, breaks the rules...Is this package safe to install?
 
I may be showing my ignorance here but also, how will this help the folks in the office to play their music from the server box (the music folder is on the fileserver as a shared folder so they wish to play it direct from there, with a speaker set attatched to the server)...
 
Thanks again
 
mrbrooks
 
-- EDIT
 
What would be ideal is if there was some music player that has a web interface, that will play music on the server box, if this is indeed possible...

---

### Post by mozkill on 2012-08-30
Why does everyone on this forum suggest things that aren't part of the default Ubuntu install?  To me it sounds like, after installing VNC on his Ubuntu system, he just failed to configure the VNC port service for the user he is connecting as.  He doesn't need some other software to do it, just configure default Ubuntu as expected:  

[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

---

### Post by mrbrooks on 2012-08-30
Hi mozkill, vnc works fine, if we start the session from putty or other ssh client and then login via the TightVNC client, what my original question was about, if the comman to start the session is issued from webmin, then the VNC just shows a blank screen and doesnt fire up, why i am not sure...It sets the session up as 'root' as opposed to the 'user' who is logged in as the account user when setting up Ubuntu.
 
What I was hoping to do was to be able to bypass the putty connection and issue the command from Webmin but like i say, when you do this is doesnt show the session.
 
I apologise for my lack of knowledge in this area and am hoping to get pointed in the right direction, I will take a read of the link you have posted and hopefully glean some more info and maybe I can figure out how to make it work this way. If not then I suppose we will just have to continue on with using the Putty client to issue the vncserver command.
 
thanks again
 
mrbrooks

---

### Post by CharlesA on 2012-08-30
> **mrbrooks said:**
> Hi Charles, thanks for the reply, I just looked at subsonic and the Ubuntu software centre on my box said this package is of bad quality, etc etc, breaks the rules...Is this package safe to install?
 
I may be showing my ignorance here but also, how will this help the folks in the office to play their music from the server box (the music folder is on the fileserver as a shared folder so they wish to play it direct from there, with a speaker set attatched to the server)...
 
Thanks again
 
mrbrooks
 
-- EDIT
 
What would be ideal is if there was some music player that has a web interface, that will play music on the server box, if this is indeed possible...

I haven't tried SubSonic in a while, what messages did it give you?

I was recommended moc but you would need ssh access to the box in order to play music.

> **mozkill said:**
> Why does everyone on this forum suggest things that aren't part of the default Ubuntu install?  To me it sounds like, after installing VNC on his Ubuntu system, he just failed to configure the VNC port service for the user he is connecting as.  He doesn't need some other software to do it, just configure default Ubuntu as expected:  

[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)
Cuz a lot has changed since 2006?

Ubuntu no longer uses gdm, it uses lightdm. VNC is a *bad* idea for anything other than local access, and even then there are better tools for remote access to a GUI than VNC.

@mrbrooks: It is likely the vnc service is launched as root, but if it works when launched as the user, just launch it as the user. ;)

---

### Post by Elfy on 2012-08-30
> **mozkill said:**
> Why does everyone on this forum suggest things that aren't part of the default Ubuntu install?  To me it sounds like, after installing VNC on his Ubuntu system, he just failed to configure the VNC port service for the user he is connecting as.  He doesn't need some other software to do it, just configure default Ubuntu as expected:  

[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

Why refer to a thread that in 2009 was marked with this ?

> Warning!
This howto is old, unsupported, and relies on a broken package. This should be used as reference only.

---

### Post by mrbrooks on 2012-08-30
Charles, hi buddy, thats what weve been doing today, the issue I wanted to get cleared up was, when you login to webmin as the user we first setup when installing Ubuntu, lets say bigboss, webmin logs you in as a 'root' from what I can tell, and thus the session wont work properly. I beleive it is started as 'root' and this is in part the problem because the user, bigboss is not really 'root' (please correct me if wrong here)
 
The box has SSH access and is LOCAL ONLY it has no purpose outside the lan.
 
I supose maybe its just something we will have to work around and just use the SSH Client to issue the command as we have done previously. Just wanted to see if there was a work around for the Webmin thing.
 
As for the outdated info, yeah, I did follow the how to for Ubuntu 12.04 and like I say, it works without a hitch (apart from the 'root' confusion) and I even heard the music playing :) ... So in a sense it works ok but was keen to see if there was a way to cut out the need to use the Putty SSH client to kick it off, leaving them with only needing to use webmin and VNC...
 
Thanks again for all the input, i very much appreciate it...
 
mrbrooks
 
-- EDIT
 
Re the music and login into a VNC session , I had to auto login the 'root' before any music would play once the box had gone headless, i couldnt figure it out at first but once I realised it worked when logged in directly to the box as opposed to via SSH, it worked, so I set the accout to auto login and hey presto...Why this worked I have no idea...

---

### Post by mrbrooks on 2012-08-30
Also wanted to add, Im going to try out tomorrow to see if its possible to get another user logged into webmin (have to set them up as currently only the 'root' has a webmin account) and see if the command to start a vnc session works and allows the user to login to the session...
 
thanks guys/gals...

---

### Post by CharlesA on 2012-08-30
Worse case you can just set the vnc server to launch a vnc session on reboot by throwing it in the user's crontab with a time of @reboot

You shouldn't really log into a GUI as root either, it can cause issues, not to mention it is a bit of a security risk.

---

### Post by mrbrooks on 2012-08-30
Hi Charles, yeah I agree re logging in as the bigboss ('root') account, but it was at the time the only account running as the one created at install and to be honest, I wouldnt have logged in at all apart from the fact at the time it was the only way to get any music to play, haha...and of course to do the admin stuff from Webmin I suppose, just to be a little safer I have changed the defaul settings on WM, ie port numbers and set a list of allowed addresses etc etc...and also set up SSH with Certs and 'root' is only able to login for commands (I used to use this setting with webmin on Debian but not sure it applies on Ubuntu due to the lack of an actual 'root' but set it anyway)
 
Apart from that, I will setup some additional users for both the system and webmin and get them to use those. I will take a look at the option you put forward as this sounds like a good plan to me and hopefully fairly easy to get set up.
 
I know its an odd combo the way this box is being used, but then i suppose each group of folks has their own idea of what they want and need their machines to do...
 
Anyway, thanks so much for the input, it def has got me thinking a little more about it, just need to get the simplest solution for a good all round outcome.
 
mrbrooks

---

