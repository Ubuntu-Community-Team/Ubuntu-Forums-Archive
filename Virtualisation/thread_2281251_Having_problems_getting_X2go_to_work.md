---
title: "Having problems getting X2go to work"
date: 2015-06-05
forum: Virtualisation
---

### Post by Kourosh_Banaeianza on 2015-06-05
Hello guys,

I have a problem that I have not found the fix for after searching the webs for a week. The problem I have is that I log into X2go. After a while X2go shows the a black display screen. But shortly after this closes down and terminates the session and bring me back to the login screen. I have no idea where I can find X2go log files to show you what is happening. If you can help me it would be great.


Thanks

---

### Post by TheFu on 2015-06-05
How solid is the connection between both systems? Any wifi involved?
On the remote machine you login to, in the HOME for the user, check the .x2go/ directory.  You can also check the ssh logs.

Could the remote system be going into standby or hibernating? I don't allow that and have only been kicked out of sessions if the connection goes down.

Also - which client are you using?

---

### Post by Kourosh_Banaeianza on 2015-06-05
> **TheFu said:**
> How solid is the connection between both systems? Any wifi involved?
On the remote machine you login to, in the HOME for the user, check the .x2go/ directory.  You can also check the ssh logs.

Could the remote system be going into standby or hibernating? I don't allow that and have only been kicked out of sessions if the connection goes down.

Also - which client are you using?

So it is a wired connection. No wifi at all

this is what X2go says for the session when I can't connect in the session file.
```

Loop: WARNING! Unrecognized session type 'unix-kde-depth_32'. Assuming agent session.
Auth: WARNING! Failed to read data from the X auth command.
Auth: WARNING! Generating a fake cookie for X authentication.
Loop: WARNING! Could not retrieve the X server authentication cookie.

``` 


The ssh files has nothing other than the saved profiles.


I am 100% sure this is server side problem rather than client based problem. There is no problem with the connection as I can ssh totally fine. Just the fact that X2go does not work. 

I am also using Mate as a client.

---

### Post by TheFu on 2015-06-05
Why is KDE referenced in the error?
Have you ever run any GUI program with sudo (which is bad)?  Appears the X-auth file has the wrong owner, maybe? Try deleting that.

---

### Post by Kourosh_Banaeianza on 2015-06-05
I just tried to connect using mate and i still get the same error.
 
I have never used a Gui program with sudo. 

which are the X-auth files. Like the whole folder?  Can you also distinguish between client and server side X-auth files.

---

### Post by TheFu on 2015-06-06
Check the ownership and permissions. It is completely safe to delete them.
Is "mate" on of the supported list of DEs for x2go?  Can you try a different, supported, DE or just use a plain WM and test that? I use plain openbox or fvwm-crystal for better remote performance. But I also use LXDE when on the same LAN.

---

### Post by Kourosh_Banaeianza on 2015-06-08
I have used another type session called Gnome and have not gotten any success. I also have other Co-workers that can't connect to the server. I think that is why it is server side. 

Mate is supported by X2go. I also deleted those files and I still can't connect.

---

### Post by Kourosh_Banaeianza on 2015-06-11
> **TheFu said:**
> Check the ownership and permissions. It is completely safe to delete them.
Is "mate" on of the supported list of DEs for x2go?  Can you try a different, supported, DE or just use a plain WM and test that? I use plain openbox or fvwm-crystal for better remote performance. But I also use LXDE when on the same LAN.

Is it bad to uninstall Xorg or X11 and reinstall it? I think it may be a problem with X11 or something. IDK what else could be the problem.

---

### Post by Kourosh_Banaeianza on 2015-06-11
I also have a problem where the error is 

```

failed to get d-bus connection

```

---

### Post by TheFu on 2015-06-12
> **Kourosh_Banaeianza said:**
> Is it bad to uninstall Xorg or X11 and reinstall it? I think it may be a problem with X11 or something. IDK what else could be the problem.

Shouldn't matter if you reinstall those. x2go uses its own X11 files for the X-server. If you do remove the X11 client files, expect many of the X11 client programs to be removed thanks to dependencies.  I don't think dbus has much to do with this.  

I've seen the dbus thing. Don't remember the fix.  Think I turned off file sharing, printing and audio. It was a while ago - don't remember.

---

### Post by Kourosh_Banaeianza on 2015-06-12
> **TheFu said:**
> Shouldn't matter if you reinstall those. x2go uses its own X11 files for the X-server. If you do remove the X11 client files, expect many of the X11 client programs to be removed thanks to dependencies.  I don't think dbus has much to do with this.  

I've seen the dbus thing. Don't remember the fix.  Think I turned off file sharing, printing and audio. It was a while ago - don't remember.

So do you know anything I can do. Like do you know where to go from here?

---

### Post by Kourosh_Banaeianza on 2015-06-16
Hey man, 

I am a big newb, can you explain that in more lame terms thank you.

---

### Post by TheFu on 2015-06-16
I'm so sorry.  I mixed up 2 different threads where x2go was mentioned and replied to you when at a conference without re-reading the thread first.  In short, I was completely side-tracked there.  I'll remove that comment to prevent my confusion from harming other replies.

---

### Post by rpremuz on 2015-10-19
I had this issue while trying to connect from **X2Go Client v. 4.0.5.0** on MS Windows to **X2Go Server v. 4.0.1.19-0~1064~ubuntu14.04.1** on Linux Mint 17.2 using a MATE session.

The issue was solved by deleting **.Xauthority** files in the home directory of the user trying to connect (some of the files were owned by the root):

```
$ sudo rm ~/.Xauthority*
```

BTW, I installed X2Go from [PPA]("https://launchpad.net/~x2go/+archive/ubuntu/stable"):

```
$ sudo apt-add-repository ppa:x2go/stable
$ sudo apt-get update
$ sudo apt-get install x2goserver x2goserver-xsession x2goclient x2goserver-extensions
```

-- rpr.

---

