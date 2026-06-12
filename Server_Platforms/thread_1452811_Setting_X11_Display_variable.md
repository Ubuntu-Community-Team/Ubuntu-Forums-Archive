---
title: "Setting X11 Display variable"
date: 2010-04-12
forum: Server Platforms
---

### Post by guilly on 2010-04-12
Hi Guys,

quick question. I have visudo file configured to allow certain applications run via a regular user with sudo powers. The issue I'm having is that I can not seem to get X server to forward properly. 

I think the issue is that since it's a regular user running the application with sudo powers it is sending the X11 to root's X session and not the regular users?

Has anyone had this issue before?

---

### Post by cdenley on 2010-04-12
Did you try gksudo?

---

### Post by guilly on 2010-04-12
> **cdenley said:**
> Did you try gksudo?

Unfortunately I do not have gksudo command, this is a SLES10 box. The equivalent would be sux command for SLES however we do not want to give the user access to the root password but simply allow the user to run certain applications with root power. Hence the use of visudo.

---

### Post by cdenley on 2010-04-12
> **guilly said:**
> Unfortunately I do not have gksudo command, this is a SLES10 box. The equivalent would be sux command for SLES however we do not want to give the user access to the root password but simply allow the user to run certain applications with root power. Hence the use of visudo.

Well it doesn't seem to be a problem in ubuntu. What exactly is the error you get?
```

sudo DISPLAY=:0 myguicommand

```

Perhaps posting your sudoers file will help.

---

### Post by guilly on 2010-04-12
I realize it isn't a Ubuntu issue, But I know the Ubuntu community is very well supported compare to other distro's and from what I can tell this is a common issue across distro's.

This is the error I am getting:

Exception in thread "main" java.awt.HeadlessException:
No X11 DISPLAY variable was set, but this program performed an operation which requires it.
        at java.applet.Applet.<init>(Applet.java:75)
        at javax.swing.JApplet.<init>(JApplet.java:131)
        at COM.ibm.storage.adsm.cadmin.clientgui.DDsmApplet.<init>(DDsmApplet.java:416)
        at COM.ibm.storage.adsm.cadmin.clientgui.DDsmApplet.main(DDsmApplet.java:806)
/home/userA

---

### Post by cdenley on 2010-04-12
> **guilly said:**
> I realize it isn't a Ubuntu issue, But I know the Ubuntu community is very well supported compare to other distro's and from what I can tell this is a common issue across distro's.

This is the error I am getting:

Exception in thread "main" java.awt.HeadlessException:
No X11 DISPLAY variable was set, but this program performed an operation which requires it.
        at java.applet.Applet.<init>(Applet.java:75)
        at javax.swing.JApplet.<init>(JApplet.java:131)
        at COM.ibm.storage.adsm.cadmin.clientgui.DDsmApplet.<init>(DDsmApplet.java:416)
        at COM.ibm.storage.adsm.cadmin.clientgui.DDsmApplet.main(DDsmApplet.java:806)
/home/userA

And you still get that error when setting the DISPLAY variable like with the command I gave? And once again, your sudoers file might be helpful.
```

sudo cat /etc/sudoers

```

---

### Post by guilly on 2010-04-12
> **cdenley said:**
> And you still get that error when setting the DISPLAY variable like with the command I gave? And once again, your sudoers file might be helpful.
```

sudo cat /etc/sudoers

```

I apologize I did not see your request for my sudoers file. I seem to have fixed the problem by commenting out Default always_set_home and Defaults env_reset. However, I'm not sure if this causes any risks. Any thoughts?

---

### Post by dwarfolo on 2010-04-12
If you nedd to grant access only to local users you can use xhost.

```

xhost local:root

```

---

### Post by cdenley on 2010-04-12
> **guilly said:**
> I apologize I did not see your request for my sudoers file. I seem to have fixed the problem by commenting out Default always_set_home and Defaults env_reset. However, I'm not sure if this causes any risks. Any thoughts?

Well the comments in your sudoers file gives specific examples where allowing the user's variables to be used in the sudo session can result in security problems. I think a better solution would be to keep only the variables needed. Try adding this line to your original sudoers file.
```

Defaults env_keep = "DISPLAY XAUTHORITY XDG_SESSION_COOKIE"

```

---

### Post by guilly on 2010-04-12
> **cdenley said:**
> Well the comments in your sudoers file gives specific examples where allowing the user's variables to be used in the sudo session can result in security problems. I think a better solution would be to keep only the variables needed. Try adding this line to your original sudoers file.
```

Defaults env_keep = "DISPLAY XAUTHORITY XDG_SESSION_COOKIE"

```

That created another issue, now it's complaining about Putty X11 proxy: wrong authentication protocol attempted.

I've verified that xauth list has the proper cookies set for the root account so they match my regular user

---

### Post by cdenley on 2010-04-12
> **guilly said:**
> That created another issue, now it's complaining about Putty X11 proxy: wrong authentication protocol attempted.

I've verified that xauth list has the proper cookies set for the root account so they match my regular user

Are you running these sudo commands remotely with putty?

---

### Post by guilly on 2010-04-12
> **cdenley said:**
> Are you running these sudo commands remotely with putty?

Yes, We need our users to be able to run a backup application remotely via putty.

---

### Post by dwarfolo on 2010-04-12
A quick google search has returned this

[http://froebe.net/blog/2008/11/14/getting-xlib-putty-x11-proxy-wrong-authentication-protocol-attempted-i-have-the-answer/](http://froebe.net/blog/2008/11/14/getting-xlib-putty-x11-proxy-wrong-authentication-protocol-attempted-i-have-the-answer/)

---

### Post by guilly on 2010-04-12
> **dwarfolo said:**
> A quick google search has returned this

[http://froebe.net/blog/2008/11/14/getting-xlib-putty-x11-proxy-wrong-authentication-protocol-attempted-i-have-the-answer/](http://froebe.net/blog/2008/11/14/getting-xlib-putty-x11-proxy-wrong-authentication-protocol-attempted-i-have-the-answer/)

As stated before, I've already checked this.

---

### Post by cdenley on 2010-04-12
> **guilly said:**
> As stated before, I've already checked this.

Try commenting out "Default always_set_home", but leave "Defaults env_reset". Also, I think the other line I gave you may not be needed.

---

### Post by guilly on 2010-04-12
> **cdenley said:**
> Try commenting out "Default always_set_home", but leave "Defaults env_reset". Also, I think the other line I gave you may not be needed.

I've already tried both. Thanks, I think I will leave both commented out. These servers are only being used on a secured network, I think I will trust the users not to do anything malicious to roots home environment. 

Thanks for the help!

---

### Post by ajft on 2010-05-28
> **guilly said:**
> I've already tried both. Thanks, I think I will leave both commented out. These servers are only being used on a secured network, I think I will trust the users not to do anything malicious to roots home environment. 

Thanks for the help!

I think I'm hunting for a solution to the same problem -- we've got backup operators who login via "ssh -X" as a non-privileged account, then use sudo to run ad-hoc backups and restores.  SLES10 has locked down sudo so that X11 progs. can't operate by default.

With the following three settings, sudo is now able to invoke X11 gui progs.

#Defaults always_set_home
Defaults env_reset
Defaults env_keep = "DISPLAY XAUTHORITY XDG_SESSION_COOKIE"


HTH.
  Adrian

---

