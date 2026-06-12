---
title: "Setting up office with 1 server 1 remote and 1 local client..."
date: 2010-09-22
forum: Server Platforms
---

### Post by gypsumwolf on 2010-09-22
I have a fast computer in my office and I want the person using the slow computer in the same office to boot up and see the login window (gdm) and log-in from there into the fast computer and be able to use their session on the fast computer the same time I am locally logged in to the fast computer as a different user and session.

Is this best done through XDMCP? Where is a good tutorial on how to set this up?

Both computers are using Ubuntu 10.04.

---

### Post by LightningCrash on 2010-09-23
Easy peasy
[http://www.zolved.com/synapse/view_content/28158/Remote_Login_via_XDMCP_on_Ubuntu](http://www.zolved.com/synapse/view_content/28158/Remote_Login_via_XDMCP_on_Ubuntu)

---

### Post by cj.surrusco on 2010-09-23
> **LightningCrash said:**
> Easy peasy
[http://www.zolved.com/synapse/view_content/28158/Remote_Login_via_XDMCP_on_Ubuntu](http://www.zolved.com/synapse/view_content/28158/Remote_Login_via_XDMCP_on_Ubuntu)

I don't think this link will work with 10.04, because it isn't there for me. 

You might want to look [here]("https://wiki.ubuntu.com/xdmcp") for more information.

---

### Post by LightningCrash on 2010-09-23
[http://ubuntuforums.org/showthread.php?t=1471703](http://ubuntuforums.org/showthread.php?t=1471703)

---

### Post by gypsumwolf on 2010-09-23
Loging in works fine with TSClient and Xnest (except its not full screen). Can I login to the server from the slow computers gdm screen? If so, how?

---

### Post by gypsumwolf on 2010-09-23
Xnest closed because of an error when I tested running a game, although it worked just fine with OpenOffice.org.

---

### Post by LightningCrash on 2010-09-23
> **gypsumwolf said:**
> Loging in works fine with TSClient and Xnest (except its not full screen). Can I login to the server from the slow computers gdm screen? If so, how?

There should be an option in the remote computer's GDM screen.

---

### Post by gypsumwolf on 2010-09-23
Hm.. I see no option for it at all. Just see regular GDM screen.

There was already a custom.conf on the computer, maybe that was because I was using xubuntu. I added the info to it. Should I leave everything out and just have the custom.conf have only the info here [https://wiki.ubuntu.com/xdmcp](https://wiki.ubuntu.com/xdmcp) in it?

---

### Post by gypsumwolf on 2010-09-23
> Should I leave everything out and just have the custom.conf have only the info here [https://wiki.ubuntu.com/xdmcp](https://wiki.ubuntu.com/xdmcp) in it?

Tried it and nothing happened.

---

### Post by cj.surrusco on 2010-09-23
The newest gdm dropped support for remote logins. You have to use a program such as tsclient.

---

### Post by gypsumwolf on 2010-09-23
I would figure since Ubuntu is a multi user operating system that it could actually support multiple users in this way. I would call this LAME but, there might be a good reason behind it.

Is there a better way I can log in remotly in the same office for 2 people to use the same (Graphical) computer and login?

I could forget GNOME on the client and have OPENBOX + feh + tsclient, but Xnest is not full screen so that will not work for me, VNC views the current session. So what should I do to enable login and full screen from client?

---

### Post by cj.surrusco on 2010-09-23
Not sure about the other ideas, but you can start a second VNC gnome session separate from the current session connect to that.

---

### Post by gypsumwolf on 2010-09-23
Is this used for what I am trying to do? [https://help.ubuntu.com/community/MultiseatX]("https://help.ubuntu.com/community/MultiseatX")

I don't really care about gdm that much so does a different desktop manager support remote logins like, KDM, XDM?

---

### Post by cj.surrusco on 2010-09-23
Yeah that should be what you're looking for. I didn't read it all but that looks like it will work.

EDIT: Now that I read deeper into it, that would not be what you are looking for. That involves hooking all of the hardware to that one computer. 

What I was suggesting is that you run a vncserver to a separate port by running 'vncserver :1'. That would start a vncserver on port 590**1**. That's the process that I use for my server's VNC.

---

### Post by scrooge_74 on 2010-09-23
The easiest path here is to install vncserver on the "fast machine" then use a client in the slow machine such as remmina or Tsclient (taking into consideration how much resources you have available in the "slow" one to have a full desktop.

So server side you install vncserver and client side install a light desktop and a vncclient so you can log into the "fast machine" and you can run apps independent of any other user in the "fast machine"

Another lazy way is to install openssh in the server and on the client ope a terminal type ssh  -XC user@serverIP then when you log in you launch apps like ooffice or gscan2pdf <-- but this is the lazy way

---

### Post by LightningCrash on 2010-09-23
> **cj.surrusco said:**
> The newest gdm dropped support for remote logins.

It's still in kdm in 10.04

OP you could also run things through ssh +X forwarding

---

### Post by gypsumwolf on 2010-09-24
I like the ssh -X option, but I would like a normal desktop for a non-techie user. I think I will attempt using KDM.

---

