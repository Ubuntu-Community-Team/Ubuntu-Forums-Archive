---
title: "Remote Desktop (VNC) and security"
date: 2010-03-24
forum: Security
---

### Post by NertSkull on 2010-03-24
So I've read a bit and it seems that this is okay and secure.  But I wanted to double check here with everyone, because I trust here more than just about anywhere.

I've read about the hipporemote (which is pretty cool) and I have it working.  Basically I want to make sure my system is still secure.  

1.  I had to open a port on my firewall for the VNC connection.

2.  I turned on the Remote Desktop
   2a. Checked Allow other users to view....
   2b. Checked Allow other users to control....
   2c. Checked You must confirm.....
   2d. Checked for password, and put in a password
   2e. Checked Configure network automatically to accept connectios

So with doing all of that, am I ok?  I think so, especially since it says its only accessible on my local network.  But I just wanted to hear from people who know more than I do that I don't need to worry any more than normal about others accessing my machine.

I'm mainly thinking 2e,  I don't fully understand what's going on there.

So am I good with this??  Thanks all.

---

### Post by jrssystemsnet on 2010-03-24
It is NOT only accessible on your local network.  In between you manually forwarding a port through the firewall, and telling remote desktop to "configure your network" (which actually means "use UPnP to forward a port through your router for you"), you have definitely exposed VNC to the internet at large.

It is now - mostly - as secure as your password... however secure that is.  (Hope, for your sake, that that's pretty secure.  Weak or nonexistent VNC passwords are the #1 way right now that Ubuntu users are getting compromised.)  There is also the possibility that at some point an exploit will be discovered in VNC itself; this happened a few years ago.  If that happens, just having the service exposed at all might be enough to get you compromised, even without the attacker knowing your password.

With all that said... I have VNC exposed on my own network.  But I know how strong my password is, and I know that I keep up on vulnerabilities.  If you're going to expose VNC, you need to do the same thing. :)

---

### Post by 2hot6ft2 on 2010-03-24
VNC isn't really all that secure, it does have vulnerabilities. If you want a secure remote desktop try SSH and FreeNX using keys for both and disable password logins thru them completely.

You may find this interesting too
[Comparison of remote desktop software]("http://en.wikipedia.org/wiki/Comparison_of_remote_desktop_software")

---

### Post by OpSecShellshock on 2010-03-24
The first thing you need to decide with VNC is whether or not you really need it in order to accomplish something. Then you need to decide when, and whether you need to leave it on all the time or can disable it when you're not using it.

I imagine people will have different answers and will decide what works for them. I checked out the main site for Hipporemote, and personally don't get it. It looks as though you're supposed to be controlling your computer remotely from your own home network, probably feet away from being able to use a full keyboard. Granted, the setup described above would also allow it to be done from anywhere, provided the person logging in knows the target host and has a valid username and password. But most of the web stuff that was on the Hipporemote site can also be done directly from the iPod touch using its own browser or applications. So I don't get it. Is--is this what getting old feels like? I think I need to find a tar pit to sink into or something.

---

### Post by HermanAB on 2010-03-24
Hmm, the reality is that *every* case of someone complaining about getting his machine hacked on these forums, is due to VNC.  There are automated scripts out there that look for VNC servers - sooner or later, they will find you.

So, don't use VNC, use SSH.  Read up on it and buy the snail book.

---

### Post by movieman on 2010-03-25
> **HermanAB said:**
> So, don't use VNC, use SSH.  Read up on it and buy the snail book.

Or use ssh to forward the VNC connection, rather than opening up a VNC port in the firewall.

---

### Post by HermanAB on 2010-03-25
You don't need to run VNC at all. Running VNC through SSH is mostly redundant. Just try this:

$ ssh -X -C -c blowfish user@server gnome-panel

The result is a remote panel on tne local desktop.  Put it on the side of the screen to avoid confusion with the local panels.  Anything you launch from that panel will run remotely, transparently on the local desktop, without the need for X or VNC on the server.

---

### Post by NertSkull on 2010-03-25
Well that's all good to know.  I use SSH extensively (with keys and no passwords and different ports) so I was worried about VNC.  I'm not as familiar with it because I've done all my stuff with SSH.

The reason was for that Hipporemote, just as convenience as a remote for my HTPC.  But at this point I think it sounds safer to just spend the money for a nice wireless keyboard/mouse combo (or heaven forbid take the time to actually look into remotes and IR stuff).

Looks like no VNC for me then.  Thanks all

---

### Post by rookcifer on 2010-03-25
Someone needs to recommend to the Ubuntu development team to get rid of VNC in the default install.  Or at least put a big warning box on the screen when a user activates it for the first time.

---

### Post by Grenage on 2010-03-25
I would also recommend FreeNX - it's very secure and very responsive.

---

### Post by jhongomz on 2010-03-25
> **HermanAB said:**
> You don't need to run VNC at all. Running VNC through SSH is mostly redundant. Just try this:

$ ssh -X -C -c blowfish user@server gnome-panel

The result is a remote panel on tne local desktop.  Put it on the side of the screen to avoid confusion with the local panels.  Anything you launch from that panel will run remotely, transparently on the local desktop, without the need for X or VNC on the server.


so with this i would be able to get into and remotely administer/use the desktop of a machine without a logged in user?   

i am going nuts trying to get vnc w/ssh into a box with no user logged in and it keeps dying out after authentication...  i tried some of the tweaks mentioned around and nothing seems to be working... bargh!...  this would really help

---

### Post by movieman on 2010-03-25
> **HermanAB said:**
> You don't need to run VNC at all. Running VNC through SSH is mostly redundant.

Now try running an X application over the Internet from thousands of miles away.

Even running Thunderbird from my office PC five miles from here to display on my home PC is barely usable... whereas with VNC it's fine. X11 really, really, really, really hates latency, which is why FreeNX was developed to try to minimise round-trip messaging.

---

### Post by 2hot6ft2 on 2010-03-25
> **Grenage said:**
> I would also recommend FreeNX - it's very secure and very responsive.
+1
It's what I use and I think it works great.
> **jhongomz said:**
> so with this i would be able to get into and remotely administer/use the desktop of a machine without a logged in user?   

i am going nuts trying to get vnc w/ssh into a box with no user logged in and it keeps dying out after authentication...  i tried some of the tweaks mentioned around and nothing seems to be working... bargh!...  this would really help
I don't get it. The pc would have to be on. That doesn't mean anyone would have to be there using it. You could even use WOL (Wake-On-Lan) to turn it on (I'm sure that has it's risks too if you set it up to use from outside the LAN) and have a user automatically login in System > Administration > Login Screen
```
sudo apt-get install gdmsetup
```
if you don't have it already.

---

### Post by HermanAB on 2010-03-26
"Now try running an X application over the Internet from thousands of miles away."

My mail and web server is in the USA, while I presently live in Al Ain in the UAE, which is on the other side of the globe - if I move any further away, I would be moving closer!  SSH with X forwarding works fine provided that you are on the same planet.

The whole advantage of using X forwarding is that you do not need to run X or a desktop system on the server, so the RAM remains available for other processes.

BTW, I usually log into the internet from the UAE via a Socks proxy tunnel to a server in the USA, which is the way I'm working right now too.

---

### Post by jhongomz on 2010-03-26
> **2hot6ft2 said:**
> +1
It's what I use and I think it works great.

I don't get it. The pc would have to be on. That doesn't mean anyone would have to be there using it. You could even use WOL (Wake-On-Lan) to turn it on (I'm sure that has it's risks too if you set it up to use from outside the LAN) and have a user automatically login in System > Administration > Login Screen
```
sudo apt-get install gdmsetup
```if you don't have it already.


Yes the system is always on, doesn't get turned off.  I just don't like the idea of having a user logged in all the time...  I would rather ssh in, and create a session that way.. then when i am done doing what i am doing, log out.. done..  it's not too different from an RD session in windoze...    And it's pretty much there, except for the connection dropping as soon as I am about to log in.  I just wish I could figure out a workaround for it.. anyone?

---

### Post by movieman on 2010-03-26
> **HermanAB said:**
> SSH with X forwarding works fine provided that you are on the same planet.

Not with any program I've ever run: even xterms crawl when run remotely over ssh. The latency problems of X11 are well known and documented.

That said, I must admit that I've only tried running X11 remotely between two CentOS machines so perhaps Ubuntu's ssh is doing some magic to try to reduce latency the same way that FreeNX does?

---

