---
title: "Someone access to my computer via vnc"
date: 2009-11-27
forum: Security
---

### Post by A1Cyber on 2009-11-27
Hello.
I'm at school now and someone is controling my computer via vncviewer(in terminal: vncviewer -shared ip) and I don't know who is. I know that there is some app that shows who is trying to control my computer, but I don't know where to find it.

Sorry for my bad English.

Thanks in advance. ;)

---

### Post by SlugSlug on 2009-11-27
forward X and run vino-preferences -- and turn it off

---

### Post by scottuss on 2009-11-27
Or just ssh in without X forwarding, type sudo killall vino-server and then gain control back.

To see who it is enter this into a console:

sudo netstat -p | grep vino

---

### Post by HermanAB on 2009-11-27
VNC is pretty much the only way in which Ubuntu machines get hacked and since Ubuntu by default doesn't activate the firewall, it is common for new users to get into trouble this way.

I think it is rather irresponsible from the Ubuntu developers to configure the system like this.  These forums are full of complaints about VNC and having machines compromised.

The bottom line is that VNC is mainly a Windows thing.  There is no good reason to use it on Linux.  Kill the VNC server and use SSH instead.  SSH is secure and is more powerful and easier to get to work than VNC.

Ferinstance:
ssh -X -C -c blowfish user@server gnome-panel

Et voila!

---

### Post by scottuss on 2009-11-27
> **HermanAB said:**
> VNC is pretty much the only way in which Ubuntu machines get hacked and since Ubuntu by default doesn't activate the firewall, it is common for new users to get into trouble this way.

I think it is rather irresponsible from the Ubuntu developers to configure the system like this.  These forums are full of complaints about VNC and having machines compromised.

The bottom line is that VNC is mainly a Windows thing.  There is no good reason to use it on Linux.  Kill the VNC server and use SSH instead.  SSH is secure and is more powerful and easier to get to work than VNC.

Ferinstance:
ssh -X -C -c blowfish user@server gnome-panel

Et voila!

The VNC server doesn't run by default. You have to enable it.

---

### Post by bodhi.zazen on 2009-11-27
> **HermanAB said:**
> VNC is pretty much the only way in which Ubuntu machines get hacked and since Ubuntu by default doesn't activate the firewall, it is common for new users to get into trouble this way.

I think it is rather irresponsible from the Ubuntu developers to configure the system like this.  These forums are full of complaints about VNC and having machines compromised.

The bottom line is that VNC is mainly a Windows thing.  There is no good reason to use it on Linux.  Kill the VNC server and use SSH instead.  SSH is secure and is more powerful and easier to get to work than VNC.

Ferinstance:
ssh -X -C -c blowfish user@server gnome-panel

Et voila!

I would tend to agree, people enable VNC with weak password and without understanding the consequences.

IMO, if the VNC connection were firewalled it would not help as they would open the port.

The only long term solution, really, is education.

---

### Post by XCan on 2009-11-27
With all these notification systems here and popups there, they should at least pop up a warning alerting a user of the importance to choose a strong password and change the default port.

---

### Post by EJeanmaire on 2009-11-27
> **bodhi.zazen said:**
> I would tend to agree, people enable VNC with weak password and without understanding the consequences.

IMO, if the VNC connection were firewalled it would not help as they would open the port.

The only long term solution, really, is education.

I feel like this is becoming quite the re-occurring discussion...

---

### Post by bodhi.zazen on 2009-11-27
> **EJeanmaire said:**
> I feel like this is becoming quite the re-occurring discussion...

As [HermanAB]("http://ubuntuforums.org/member.php?u=44990") indicated, we see VNC cracks almost daily it seems =)

---

### Post by rookcifer on 2009-11-27
Yet another VNC crack.  I think this forum needs a VNC sticky.

---

### Post by cariboo on 2009-11-27
There is bodhi.zazen's Ubuntu Security sticky at the top of the page, it deals vnc, most newbies don't even know this section exists until they have a problem and go looking for a solution. They never read stickies.

---

### Post by __p1n__ on 2009-11-27
I suggest a WINbuntu distro for transitioning users.  

Characteristics include:

* Kbuntu based for default kiosk mode (context menus disabled, no shell, no system pane, handful of basic apps, etc.)

* Pre-activated netfilter to drop-all unsolicited incoming.

* Automatic aptitude check/upgrade; no ability to install/de-install apps.

* No root user, no graphical sudo, etc.

* Only 1 user supported (defined at installation.)

* Desktop link to [http://ubuntuforums.org](http://ubuntuforums.org).

* Background process that does nothing but paint a shield icon with the text "A/V" on the desktop.

---

### Post by scottuss on 2009-11-27
> **cariboo907 said:**
> There is bodhi.zazen's Ubuntu Security sticky at the top of the page, it deals vnc, most newbies don't even know this section exists until they have a problem and go looking for a solution. They never read stickies.

Do we have a persistent banner or dialog box or something that tells newbies to read stickies?

We certainly should have something that tells new users to read the stickies, some users may be new to forums as well as Ubuntu and not realise what a "sticky" is

I don't think that an (ironic and pointless) sticky about stickies is a solution..

---

### Post by scottuss on 2009-11-27
> **__p1n__ said:**
> I suggest a WINbuntu distro for transitioning users.  

Characteristics include:

* Kbuntu based for default kiosk mode (context menus disabled, no shell, no system pane, handful of basic apps, etc.)

* Pre-activated netfilter to drop-all unsolicited incoming.

* Automatic aptitude check/upgrade; no ability to install/de-install apps.

* No root user, no graphical sudo, etc.

* Only 1 user supported (defined at installation.)

* Desktop link to [http://ubuntuforums.org](http://ubuntuforums.org).

* Background process that does nothing but paint a shield icon with the text "A/V" on the desktop.

I don't think that's really the answer. I think making Ubuntu much more user friendly is certainly a good idea, but yet another re-spin isn't the answer.

---

### Post by alexfish on 2009-11-27
vote for that

---

### Post by Irihapeti on 2009-11-27
I wondered briefly if it would help if vnc weren't installed by default. But then, the ftp server and sshd aren't installed by default. People go and install them and get into trouble. So would it really make much difference?

---

### Post by cariboo on 2009-11-27
The problem is most new users are so intent on finding a solution to their problem, they don't read anything but the thread they created..

I've found that the majority of users haven't read the forum rules, which you have to agree to, before registering, so expecting them to read stickies is almost impossible.Putting a banner up saying read the stickies will get ignored just like most other notices

Ubuntu has gotten so easy to setup, almost anyone can do it, and that is the problem.

---

### Post by HermanAB on 2009-11-27
I think the best solution would be if Ubuntu makes a VNC 'package' that links to the SSH package, so that if you would try to install VNC, it would install SSH instead...
;)

---

### Post by scottuss on 2009-11-27
> **HermanAB said:**
> I think the best solution would be if Ubuntu makes a VNC 'package' that links to the SSH package, so that if you would try to install VNC, it would install SSH instead...
;)

I know it was a joke but it raises a serious issue... some of us know what VNC is and how it should be used and actually need it in there. Clearly better warnings when users enable it would be a good way to go

---

### Post by rookcifer on 2009-11-27
> **HermanAB said:**
> I think the best solution would be if Ubuntu makes a VNC 'package' that links to the SSH package, so that if you would try to install VNC, it would install SSH instead...
;)

The problem is that SSH gets cracked a lot too.  There are several recent threads demonstrating this.  Of course, it isn't VNC's or SSH's fault -- people are not setting passwords or are using default passwords.  Many newbs leave their SSH server wide open to the Internet on port 22. 

One would think that any computer user who knows what SSH is would be smart enough to set a strong password (or a key).  Obviously this is not the case.  I am not sure why most of them install SSH in the first place, or what they hope to achieve by doing so.

---

### Post by OpSecShellshock on 2009-11-27
It may be reasonable to keep it in the repositories, but not install it by default. The extra barrier of people who don't know exactly what it is having to go out of their way to figure out how to put a remote console on might give some of them pause. At the very least, the how-to page could be set up with a giant warning on it.

---

### Post by VioletsPie on 2009-11-27
At the very least links to external sites should probably be blocked in signatures and whatnot.

---

