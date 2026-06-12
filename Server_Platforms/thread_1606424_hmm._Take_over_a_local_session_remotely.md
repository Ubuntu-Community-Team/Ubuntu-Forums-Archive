---
title: "hmm. Take over a local session remotely"
date: 2010-10-26
forum: Server Platforms
---

### Post by pawnrocket on 2010-10-26
Hi Everyone,

Here is the scenario; I have Ubuntu Server 10.04 64bit running on a PowerEdge 1900. I will soon flip the switch on two virtual machines (windows server 2003 & 2008) that I have virtualized in an attempt to move this organization into the Open Source world (eventually). When I start the VM's (currently manually, later as a service) I would like to be able to 'take over' the Virtual Machines window so that I can work on it using ssh -X over a remote connection. 

[COLOR="RoyalBlue"]Question; Is there a command that I can 'take over a process that was started locally as 'user1' and display that program over ssh remotely. 
[/COLOR]
[COLOR="Navy"]Reasoning; If I start a VirtualBox machine at work and need to work on the VM from home, I would log in via ssh -X and then seize the process so I can see the VM over my remote connection. [/COLOR]

Thanks,

Jason

P.S. I don't want to access it over Windows RDP

---

### Post by Lars Noodén on 2010-10-26
One way is to [tunnel VNC](http://www.cl.cam.ac.uk/research/dtg/attarchive/vnc/sshvnc.html) over SSH.  

The VM usually supports VNC, allowing you to set which VNC display is used.  Straight shell is much nicer, IMHO, once you can get that set up.  Which services do you wish to upgrade to Linux?

---

### Post by the_original_billq on 2010-10-26
> **pawnrocket said:**
> ...
P.S. I don't want to access it over Windows RDP

Any reason why not?  VirtualBox supports RDP out of the box...

I set up an ssh tunnel to my VirtualBox machine, then attach using
```

rdesktop localhost:port

```

(Which is what I'm using right now, as a matter of fact...:-))

Works like a champ from home or at work!  I've got a VirtualBox Ubuntu workstation and a VirtualBox Windows desktop running on the same server, then access them both from anywhere.  It's a beautiful thing.

---

### Post by pawnrocket on 2010-10-26
The reason for no RDP is that I want to limit the amount of ports forwarded through the firewall. I already have ssh open, and I assume this is something people do, just I don't know how. :)

---

### Post by pawnrocket on 2010-10-26
> **Lars Noodén said:**
> One way is to [tunnel VNC](http://www.cl.cam.ac.uk/research/dtg/attarchive/vnc/sshvnc.html) over SSH.  

The VM usually supports VNC, allowing you to set which VNC display is used.  Straight shell is much nicer, IMHO, once you can get that set up.  Which services do you wish to upgrade to Linux?

Eventually everything, my idea is to get windows to stop running hardware, setup 2 way file syncs and a cluster to support our crappy windows servers. 

Then I will start migrating to OpenLDAP and an Ubuntu file server. I beleive that I will leave one Windows Server - Domain Controller and Exchange. Oh and print services.

---

### Post by the_original_billq on 2010-10-26
Using the ssh tunnel will allow you to only have the single port open in the firewall.

Exactly what you are looking to do.

[http://magazine.redhat.com/2007/11/27/advanced-ssh-configuration-and-tunneling-we-dont-need-no-stinking-vpn-software/]("http://magazine.redhat.com/2007/11/27/advanced-ssh-configuration-and-tunneling-we-dont-need-no-stinking-vpn-software/")

This is the best guide I've seen on setting up ssh tunneling using your .ssh/config file.  Very useful.

---

### Post by endotherm on 2010-10-26
I agree, remoting into the guest is a lot better idea than trying to x-forward the hosts window of the guest.

---

### Post by pawnrocket on 2010-10-26
I know how to ssh into the box, and I know how to redirect the xwindow over the ssh connection if I am starting a graphical program (ssh -x) I don't know how to seize the graphical program remotely when I started it locally. 

The VM is running, but I can't interact with the interface because it was started by me when I was at work. Now I want to see the VM from home, after logging in ssh.

---

### Post by pawnrocket on 2010-10-26
> **endotherm said:**
> I agree, remoting into the guest is a lot better idea than trying to x-forward the hosts window of the guest.

Right ssh to the host -> rdesktop to the guest

Thanks.

But still doesn't answer the question... Could I seize the process running under another user (being myself in this case)?

---

### Post by endotherm on 2010-10-26
well from ubuntu, I think I woudl

```
vncviewer -via <sshuser>@<sshHostServer> <guestNameOrIP>:0
```

that should ssh you into the host, and from there, connect to the vnc (vino) instance within the guest.

---

### Post by endotherm on 2010-10-26
> **pawnrocket said:**
> Right ssh to the host -> rdesktop to the guest

Thanks.

But still doesn't answer the question... Could I seize the process running under another user (being myself in this case)?
su is about the only way I could think of, but I wonder if the user is the issue here, and not the $Display. i assume you want to see the app, and forward it over x, right?

---

### Post by pawnrocket on 2010-10-26
> **endotherm said:**
> well from ubuntu, I think I woudl

```
vncviewer -via <sshuser>@<sshHostServer> <guestNameOrIP>:0
```

that should ssh you into the host, and from there, connect to the vnc (vino) instance within the guest.

Excellent, a wonderful solution. I will make this as solved, but I would still like to know if it is possible to seize the xwindow for Virtualbox from the host.

---

### Post by the_original_billq on 2010-10-26
That's up to Windows, right?  I know that the Windows Server "administrator" account can control user accounts, but that's Win server setup, and outside my realm.

---

### Post by pawnrocket on 2010-10-26
> **the_original_billq said:**
> That's up to Windows, right?  I know that the Windows Server "administrator" account can control user accounts, but that's Win server setup, and outside my realm.

No I don't believe this has anything to do with windows. 

I apologize I thought this would be easier to explain. 

Scenario... 

I am at work, I log into my ubuntu server as the user "Goober"... 
I start a program, lets say aqemu, I finish my work and I leave aqemu running. I lock my computer. 

I head to lunch and eat a horrible steak and cheese sub, it effects my stomach. I vomit and go home. 

At home I feel better, I took some tums. I connect to an ssh session, I decide I want to work on aqemu again. It is already loaded under the session tty7. I want to use the aqemu that is already loaded. 

How do I do that?

---

### Post by the_original_billq on 2010-10-26
> **pawnrocket said:**
> No I don't believe this has anything to do with windows. 

I apologize I thought this would be easier to explain. 

Scenario... 

I am at work, I log into my ubuntu server as the user "Goober"... 
I start a program, lets say aqemu, I finish my work and I leave aqemu running. I lock my computer. 

I head to lunch and eat a horrible steak and cheese sub, it effects my stomuch. I vomit and go home. 

At home I feel better, I took some tums. I connect to an ssh session, I decide I want to work on aqemu again. It is already loaded under the session tty7. I want to use the aqemu that is already loaded. 

How do I do that?

You stop buying the horrible steak and chees subs from the greasy spoon, turn into a vegan, and live a long, healthy, happy life.

Oh, you meant the X-Session stuff!

Well

I use a Sun Ray, which allows me to connect to my X-Session from anywhere!

Other folks here use NoMachine, which works really well.
[https://help.ubuntu.com/community/FreeNX]("https://help.ubuntu.com/community/FreeNX")

You can still tunnel it all through ssh.

I thought you were trying to attach to a running Winders session running in VirtualBox?

Sorry...

-Bill

---

### Post by pawnrocket on 2010-10-26
> **the_original_billq said:**
> You stop buying the horrible steak and chees subs from the greasy spoon, turn into a vegan, and live a long, healthy, happy life.

Oh, you meant the X-Session stuff!

Well

I use a Sun Ray, which allows me to connect to my X-Session from anywhere!

Other folks here use NoMachine, which works really well.
[https://help.ubuntu.com/community/FreeNX]("https://help.ubuntu.com/community/FreeNX")

You can still tunnel it all through ssh.

I thought you were trying to attach to a running Winders session running in VirtualBox?

Sorry...

-Bill

Thanks for the reply. 

It looks like that is going to tunnel my desktop session, can't I just interact with one program like I would an redirecting an xwindow?

---

### Post by pawnrocket on 2010-10-26
> **the_original_billq said:**
> You stop buying the horrible steak and chees subs from the greasy spoon, turn into a vegan, and live a long, healthy, happy life.

Oh, you meant the X-Session stuff!

Well

I use a Sun Ray, which allows me to connect to my X-Session from anywhere!

Other folks here use NoMachine, which works really well.
[https://help.ubuntu.com/community/FreeNX]("https://help.ubuntu.com/community/FreeNX")

You can still tunnel it all through ssh.

I thought you were trying to attach to a running Winders session running in VirtualBox?

Sorry...

-Bill
 
No I just want to be able to access the VirtualBox window remotely after it was loaded locally,

---

### Post by the_original_billq on 2010-10-27
Hmmm.  You need to be able to identify the window remotely and redirect it to your $DISPLAY.  That's a challenge.

I've looked at xkibitz [http://linux.die.net/man/1/xkibitz]("http://linux.die.net/man/1/xkibitz") which will do that for an xterm, but I think only when you launch the app.

You can also use screen [http://linux.die.net/man/1/screen]("http://linux.die.net/man/1/screen") to do this "on the fly", but again, only for xterms.

So, it looks like x11vnc/vncviewer can do what you are looking to do - though I've never tried it or seen it done.  The '-id windowid' option to x11vnc is supposed to be able to do it.  I would have to wonder how well this would work.  See [http://linux.die.net/man/1/x11vnc]("http://linux.die.net/man/1/x11vnc") for the man page on x11vnc.  You may also want to visit Karl Runges site []("http://www.karlrunge.com/x11vnc/") as it will help you on this journey immensely.

Oh, and stay away from the bad steak sandwiches.

-Bill

---

### Post by serpentine on 2010-10-27
> **pawnrocket said:**
> No I don't believe this has anything to do with windows. 

I apologize I thought this would be easier to explain. 

Scenario... 

I am at work, I log into my ubuntu server as the user "Goober"... 
I start a program, lets say aqemu, I finish my work and I leave aqemu running. I lock my computer. 

I head to lunch and eat a horrible steak and cheese sub, it effects my stomach. I vomit and go home. 

At home I feel better, I took some tums. I connect to an ssh session, I decide I want to work on aqemu again. It is already loaded under the session tty7. I want to use the aqemu that is already loaded. 

How do I do that?

Really got to stay away from those steak and cheese subs, lol.  You could say:

1.  Install NoMachine NX
2.  Have your local root session with the VM's running
3.  Lock your screen but don't log out since obviously this kills that session
4.  Go home, feel better and then re-connect to the root desktop via NX where everything is really still running

or do what I do:

1.  Install NoMachine NX
2.  Start a localhost NX Connection on my machine
3.  Disconnect from that session and go home
4.  Reconnect to that session from home when I feel like working again

---

### Post by pawnrocket on 2010-12-04
okay wonderful. But can I take over a process running under myself in a different log in session.

---

### Post by CharlesA on 2010-12-05
> **pawnrocket said:**
> okay wonderful. But can I take over a process running under myself in a different log in session.
As far as I know, the only way to do that sort of thing is to use screen and the terminal, but you would have to run screen before you run whatever process you want to use.

If you are using a GUI, use FreeNX, as it supports sessions.

---

