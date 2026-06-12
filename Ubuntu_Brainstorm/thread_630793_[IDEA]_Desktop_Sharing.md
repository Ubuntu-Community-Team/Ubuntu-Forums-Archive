---
title: "[IDEA] Desktop Sharing"
date: 2007-12-03
forum: Ubuntu Brainstorm
---

### Post by wormser on 2007-12-03
[B]Vote [here]("http://brainstorm.ubuntu.com/idea/7487/") for it.

Summary[/B]

Desktop Sharing is the ability to allow a remote user to control and view your desktop.  There are a few products out there already.  Like [GoToMeeting]("http://www.gotomeeting.com/"), [WebEX]("http://www.webex.com/"), [OS X 10.5 Screen Sharing]("http://www.apple.com/macosx/features/ichat.html") and even in Vista.    

**Why**

1.  Tech support -  Desktop Sharing would allow novice users an easy way to have others to help trouble shoot remotely.
2.  Conferencing -  Multiple users can connect to review documents for meetings.
3.  Collaborating -  It would allow multiple users to work on a project together.
4.  Education    -  A great way to educate and train remotely.

I think Desktop Sharing is a killer app.  It is similar but different to VNC. Desktop Sharing would avoid having to open up firewall ports which can be difficult for novice users or impossible in a corporate setting.  To make it easier for users to connect Pidgin could be used.  OS X 10.5 does this with iChat. You would be able select a user and choose Share Desktop.  [FreeNX]("http://freenx.berlios.de/") would also be a good back bone.  It is faster than VNC and designed securely with ssh.  

**Conclusion**

Desktop Sharing is an easy way to do tech support, conference, collaborate and train others remotely.  The other 2 major operating systems have this functionality already.  This would be a great tool to add into Ubuntu.

---

### Post by daflame on 2007-12-04
> **wormser said:**
> **Summary**

Desktop Sharing is the ability to allow a remote user to control and view your desktop.  There are a few products out there already.  Like [GoToMeeting]("http://www.gotomeeting.com/"), [WebEX]("http://www.webex.com/"), [OS X 10.5 Screen Sharing]("http://www.apple.com/macosx/features/ichat.html") and even in Vista.    

**Why**

1.  Tech support -  Desktop Sharing would allow novice users an easy way to have others to help trouble shoot remotely.
2.  Conferencing -  Multiple users can connect to review documents for meetings.
3.  Collaborating -  It would allow multiple users to work on a project together.
4.  Education    -  A great way to educate and train remotely.

I think Desktop Sharing is a killer app.  It is similar but different to VNC. Desktop Sharing would avoid having to open up firewall ports which can be difficult for novice users or impossible in a corporate setting.  To make it easier for users to connect Pidgin could be used.  OS X 10.5 does this with iChat. You would be able select a user and choose Share Desktop.  [FreeNX]("http://freenx.berlios.de/") would also be a good back bone.  It is faster than VNC and designed securely with ssh.  

**Conclusion**

Desktop Sharing is an easy way to do tech support, conference, collaborate and train others remotely.  The other 2 major operating systems have this functionality already.  This would be a great tool to add into Ubuntu.

I have some minor bad news about your idea.  FreeNX is not made to share a desktop unless you want to share by VNC.  It proxies and compresses VNC in order to share desktops and it actually doesn't use the same X server when creating screens as the physical desktop.  You are right about it being encrypted though.

---

### Post by maybeway36 on 2007-12-04
You can't do this without opening ports. But I think x11vnc tunneling through SSH would work; just install SSH server and forward port 22. (SSVNC client can handle tunneling for you, or you can use SSH client + VNC client.)

---

### Post by wormser on 2007-12-04
> **daflame said:**
> I have some minor bad news about your idea.  FreeNX is not made to share a desktop unless you want to share by VNC.  It proxies and compresses VNC in order to share desktops and it actually doesn't use the same X server when creating screens as the physical desktop.  You are right about it being encrypted though.

FreeNX looks like it is not the answer then, but the point was to use something faster and more secure than VNC.  It is not really my idea, just more of a suggestion.  There are already products out there.

> **maybeway36 said:**
> You can't do this without opening ports. But I think x11vnc tunneling through SSH would work; just install SSH server and forward port 22. (SSVNC client can handle tunneling for you, or you can use SSH client + VNC client.)

I port forward my VNC sessions with ssh.  GoToMeeting does not need to have ports open.  I am unsure how this is done but they prove it can be done.  An individual you are doing business with is not going give you an account to ssh tunnel a session.  VNC or X11 forwarding are great but usually only an admin of a system or network will have access to this.  Desktop Sharing would allow anybody an easy way to share for meetings. 

This idea post was to show the need for Desktop Sharing and not nessecarily be a technical discussion on how to do it.  I was just putting forward suggestions to point out it should be fast and secure.  WebEX has a free trial [here]("http://www.webex.com/ft/index.php?t=x3gen&TrackID=1009496&hbxref=http%3A%2F%2Fwww.webex.com%2F&goid=choosetrial_global").  Please check it out to see how it works.

---

### Post by daflame on 2007-12-05
> This idea post was to show the need for Desktop Sharing and not nessecarily be a technical discussion on how to do it.  I was just putting forward suggestions to point out it should be fast and secure.  WebEX has a free trial [here]("http://www.webex.com/ft/index.php?t=x3gen&TrackID=1009496&hbxref=http%3A%2F%2Fwww.webex.com%2F&goid=choosetrial_global").  Please check it out to see how it works.

I agree that we need to discuss this as FreeNX could benefit from this too.  Currently FreeNX does what you mentioned above automatically.  It uses ssh to tunnel and encrypt a vnc server and client both of which it runs on the server with a hidden password.  This is double-talk for the server when desktop mirroring/sharing should be built-in to X with a similar protocol to X desktop forwarding (FreeNX can proxy this efficiently).

---

### Post by Burgundavia on 2007-12-07
Vino, the GNOME VNC server, is already there. I does need some more development work, however. The 2nd option is to build something on top of Telepathy tubes. The last option is the new Mango Lassi.

Corey

---

### Post by Kedster on 2007-12-08
sorry for posting abut windows  but the software called teamviewer is like the awsomest thingever for desktop sharing i dont no how its is done but it would be cool for something like it or a port of it or sumthin for ubuntu

---

### Post by bodhi.zazen on 2007-12-20
Umm... You can do this , "desktop sharing" , with a default ubuntu install.

Ubuntu comes with vino, a VNC server installed ....

System > Preferences > Remote Desktop 

[uwiki]VNC[/uwiki]

---

### Post by rockin_goliath on 2007-12-20
Although I do like the Remote Desktop application that already exists in Ubuntu, My issues with it are that it's not secure and it's not exactly zeroconf. I don't know anything how secure Apple's desktop sharing application is, but it is DEFINITELY as zeroconf as it gets. What about modifying out current remote desktop program to go through ssh or something, and then adding a plugin to Pidgin?

---

### Post by bodhi.zazen on 2007-12-21
You can tunnel the default VNC server (vino) )over ssh (same as any other vnc connection).

[uwiki]VNCOverSSH[/uwiki]

That guide uses vncserver, but it works with vino.

I am not sure what you are asking about Pidgin.

---

### Post by wormser on 2007-12-21
> **bodhi.zazen said:**
> You can tunnel the default VNC server (vino) )over ssh (same as any other vnc connection).  [uwiki]VNCOverSSH[/uwiki] That guide uses vncserver, but it works with vino.  I am not sure what you are asking about Pidgin.

I know about VNC over ssh and use it every day.  Are you going to give me shell access to view your desktop so we could review a document securely with VNC?  I don't think so.  

Desktop Sharing (Screen Sharing in OS X 10.5) is different than VNC.  I would consider VNC to be a Remote Desktop.  Desktop Sharing is a zeroconf app that your mom could do which has a lot more features.  Image any Ubuntu user being able to one click in Pidgin to share their desktop with others.  Here is a [list of WebEX features]("http://www.communiqueconferencing.com/webex_features.asp").

Watch this [video of OS X Screen Sharing]("http://www.youtube.com/watch?v=wf_NPeO3As8") and this [GoToMeeting video]("http://www.youtube.com/watch?v=3-2h5dQUsLU").  

Here is a list of other Desktop Sharing products:
WebEx, GotoMeeting, LiveMeeting, Adobe Connect, WebDialogs, Central Desktop, DimDim, LiveLook, CrossLoop, InstaColl, Yugma, CoPilot, OS X 10.5 Screen Sharing, Yuuguu, Glance, ReadyTalk, NetViewer, OnSync, InterCall, RHUB, ON24 Webcast Center and probably few others.  Why would all these companies waste money building these products if they can do the same for free with VNC.   Desktop Sharing is a killer app which Ubuntu needs and should do it better by making it faster and secure.

---

### Post by rockin_goliath on 2007-12-22
> **bodhi.zazen said:**
> You can tunnel the default VNC server (vino) )over ssh (same as any other vnc connection).

[uwiki]VNCOverSSH[/uwiki]

That guide uses vncserver, but it works with vino.

I am not sure what you are asking about Pidgin.

I'm saying that a plugin for Pidgin could be written that allows you to easily  start a remote desktop session with whoever you are chatting with. Pidgin would basically only collect the information it needs to access a computer remotely, and then send it over to the *secure* remote desktop application.

---

### Post by maybeway36 on 2007-12-22
It would pretty much be launching reverse SSH w/ port forwarding, then x11vnc. That might work even without setting up the router.
Thing is, it might not work with all IM protocols (maybe XMPP, since it's open-source.)

---

### Post by amoore on 2007-12-28
I think that DimDim would be nice to have in the repos. "DimDim is the world´s first free web meeting service based on the open source platform. dimdim is a browser-based web 2.0 service that allows anybody to share their desktop, show slides, as well as talk, listen, chat, and broadcast via webcam."


[http://www.dimdim.com/](http://www.dimdim.com/)

---

### Post by pavel989 on 2007-12-31
yes this would be an awesome app. maybe not make it come with the os but definetly a feature. for example I could def use this since ima help my dad come over to ubuntu.

however, would this only work for ubuntu? maybe give it support for what XP and OSX already have.

also there should be security restrictions, I mean its pretty easy to break a system from the terminal

---

### Post by wormser on 2008-03-11
> **pavel989 said:**
> yes this would be an awesome app. maybe not make it come with the os but definetly a feature. for example I could def use this since ima help my dad come over to ubuntu.

however, would this only work for ubuntu? maybe give it support for what XP and OSX already have.

also there should be security restrictions, I mean its pretty easy to break a system from the terminal

I think it should come default in the system.  That way a noob like your mom can be a few clicks away from being helped.  

I am really disappointed that Desktop Sharing is not getting more talk.  Every other major OS has it by default because it is a killer app.

---

### Post by BlizzofOZ on 2008-03-20
An app such as this that can be fast, but more importantly easy to setup.  At the moment, as a noob to Ubuntu and linux, I'm finding it rather difficult to get an type of VNC to work outside my network.

My reason for wanting to remote desktop would not only be able to control my desktop functions, but to additional stuff like surf the internet.  An example is that at work, I'm limited to visiting sites (no, NOT porn).  I would think that I would be able to do this via remote desktop.

---

### Post by Parsec01 on 2008-03-22
Most of you more advanced Linux users are completely missing the point that the thread starter is trying to make. I myself am an OSX user and very content with it. OSX is second to none when it comes to ease of use. The screen sharing app is very advanced. You can choose to only encrypt username/password or encrypt the complete connection (which suffers a speed decrease).

I install Linux regularly on other ppl's computers/laptops. I know how to tunnel VNC over SSH, but that is not the point het is trying to make. His point is to make it as easy to connect to a remote machine's desktop as it is in OSX Leopard.

It would look kind of like this:

If you are both logged into Pidgin, you can request another user to share your screen. The other side gives you permission to share the screen and you are connected. A minimized version of your own screen is displayed in one of the screen's corners (movable image). When you click it, you see your own display and see the remote display in a corner.

In Leopard (through ichat) there is no port-forwarding needed, no configuring needed (no router config/no firewall config). Even noobs can do this normally advanced feature right out-of-the-box! If you use the normal screen sharing app you will need to configure much the same as any other VNC sort of application (with port-forwarding and firewall config).

I was about to propose this idea myself!

I know a lot of Linux users don't want it to become mainstream, but I think it is the goal of Canonical to have as many Ubuntu users as possible. A feature like this will greatly improve user experience when they have a possibility to have someone help them remotely easily.

I think this is a must-have feature for Ubuntu!

---

### Post by jvin248 on 2008-06-27
I've used DimDim with corporate customers of mine.  As long as the "server" or active screen that is being shared is Windows then all clients can see and interact with it through Linux/Windows/whatever browser they normally use.

Two real scenarios that are needed:

1) Presentation Desktop: sharing like WebEx/DimDim/etc for meetings with one server and many viewers/clients.

2) Road Warrior desktop: sharing for one user.  You're traveling and you need to access your home and/or office server where most of your real work is located - either from your own laptop or from an internet cafe or borrowing a friend's pc that may be inside a corporate network (such as you're at a client site and you need files off your server at your own office).

Both options need to be easy and quick to setup (no router port forwarding, ssh tunneling protection, works through corporate firewalls, etc).

Challenging but possible as evidenced by the numerous commercial examples already out there.

---

### Post by srix on 2008-08-01
There's a new Webex/Gotomeeting/Yugma-like collaboration suite out called [Openmeetings]("http://code.google.com/p/openmeetings/"). I've set it up on an internal server, and it really works like a charm. It uses OpenLaszlo and Red5, and works with IE and Firefox on Windows and Linux (sorry, haven't tried it on a Mac yet). While it has its quirks and small flaws, I found that it works pretty well and its feature set is pretty good - audio/video conference, desktop sharing, file upload and online review mechanism, etc. Definitely worth a look.

---

### Post by Timon&amp;Pumba on 2008-08-01
I use the (free, but closed source) version of FreeNX (see: [http://www.nomachine.com]("http://www.nomachine.com")). I always irritated myself with the poor performance of VNC. I use the commercial version because I had trouble with FreeNX before, but that may be solved in the meantime.

**One of the most important things is the availability of clients for other platforms, so one can use their awesome configured Ubuntu setup from anywhere.**
So, this solutions provides "Remote desktop connectivity", as with windows and with vino in gnome.
Either what technology is to be chosen, it has to be customized to allow for the previous mentioned functionality (pidgin etc.).

---

### Post by lieryan on 2008-09-09
> **maybeway36 said:**
> It would pretty much be launching reverse SSH w/ port forwarding, then x11vnc. That might work even without setting up the router.
Thing is, it might not work with all IM protocols (maybe XMPP, since it's open-source.)

I think it doesn't matter what protocols to use, the main important point is for the two computers to be able to exchange information on how to configure the connection, i.e. the two computers must exchange the necessary information to configure firewall, router, port-forwarding, etc automatically. At worst, they could do it by sending plain chat messages encoded in a special way. After this the job of Pidgin is finished, Pidgin would pass that information to a VNC client/server (or any other desktop sharing protocol).

PS: AFAIK, Apple's Screen Sharing is actually a modified version of VNC.

---

### Post by vishalrao on 2008-12-07
Is there a way to connect remotely to your desktop so that the *current session* is locked on the real monitor and you operate remotely... like how Windows remote desktop works...

So far, if I connect to my Linux box and work on it remotely, the local/actual display is also visible for all to see.

---

### Post by smartboyathome on 2008-12-07
How about trying [NX]("http://www.nomachine.com/")?

---

### Post by vishalrao on 2008-12-07
i believe NX also does not behave like windows (a coworker uses it) where you can connect to the current session and continue working remotely while the actual local monitor shows a locked screen...

---

### Post by smartboyathome on 2008-12-07
> **vishalrao said:**
> i believe NX also does not behave like windows (a coworker uses it) where you can connect to the current session and continue working remotely while the actual local monitor shows a locked screen...

Thats correct. There really isn't much else for Linux ATM, since those are the two biggest ones. There *is* SSH tunnelling, and then starting a session locally through the SSH tunnel, but other than that, theres nothing else that I know of.

---

### Post by meastp on 2008-12-07
> **Burgundavia said:**
> [...] build something on top of **Telepathy tubes**. [...]

Yes. Fixing tubes and building something on top of it would benefit a lot of applications.

---

