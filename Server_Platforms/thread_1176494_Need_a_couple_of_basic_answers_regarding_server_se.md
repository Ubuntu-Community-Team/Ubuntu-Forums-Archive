---
title: "Need a couple of basic answers regarding server setup with GUI"
date: 2009-06-02
forum: Server Platforms
---

### Post by Smartin on 2009-06-02
Hi,

I am in the process of setting up a server based on 8.04 LTS.

Don't flame me but I also installed the Ubuntu Desktop as I want to be able to run some GUI-only stuff as well (Are there such things? :-)

Questions:

1) Can I use apt-get and the Synaptic manager interchangeably or will this cause problems?

2) Is running a GUI on a server considered a major security risk?

Thanks :-)

Simon

---

### Post by Alekz_ on 2009-06-02
Hi Smartin!

You should take a look here: [http://ubuntuforums.org/showthread.php?t=1091273](http://ubuntuforums.org/showthread.php?t=1091273)

I didn't answer any of your questions, but this thread may help you! :)

[]'s

---

### Post by Smartin on 2009-06-02
> **Alekz_ said:**
> Hi Smartin!

You should take a look here: [http://ubuntuforums.org/showthread.php?t=1091273](http://ubuntuforums.org/showthread.php?t=1091273)

I didn't answer any of your questions, but this thread may help you! :)

[]'s

Alekz,

*Dammit* now I'm going to have to tear down the box and start all over again :-)

Any clue what GNU "screen" is all about? What does it do that my normal OSX terminal doesn't do?

It's hard to google for...

Simon

---

### Post by Alekz_ on 2009-06-02
Hi again!

I don't think you need to start all over again.. I've suggest you to read that thread to you think IF the X is really necessary for what you want! 
If it IS, so let it installed!

About GNU Screen, here is the Project Site: [http://www.gnu.org/software/screen/](http://www.gnu.org/software/screen/)

[]'s

---

### Post by v3xtra on 2009-06-02
To answer your first question, apt-get and synaptic are the "same", besides the fact that one is GUI and the other is CLI ( Command line interfae ).  Anything that you do in Synaptic will be transfered to apt-get, and vise versa.  You shouldn't break anything at all!

I don't believe it is a security risk, because unless someone can actually get INTO your server ( which would mean that they have passwords or some way to get in ) then they can most likely do more damage than had you not had a GUI.

An option that I will most likely be doing, is to install the GUI and use that until everything is set up and the way that I want it.  Once I put the box in the closet and don't use it again, I will remove all X-specific packages and the GUI so that it will only be able to use CLI.  If I REALLY need the GUI again, it's just a simple reinstallation of packages and removing them when I am done.  I highly suggest going this route, as you get the best of both worlds.  You can use the GUI to set everything up, but you don't have the GUI working and taking up precious memory and CPU cycles when you don't need it.

Hope that helps!

---

### Post by Smartin on 2009-06-02
> **v3xtra said:**
> To answer your first question, apt-get and synaptic are the "same", besides the fact that one is GUI and the other is CLI ( Command line interfae ).  Anything that you do in Synaptic will be transfered to apt-get, and vise versa.  You shouldn't break anything at all!

I don't believe it is a security risk, because unless someone can actually get INTO your server ( which would mean that they have passwords or some way to get in ) then they can most likely do more damage than had you not had a GUI.

An option that I will most likely be doing, is to install the GUI and use that until everything is set up and the way that I want it.  Once I put the box in the closet and don't use it again, I will remove all X-specific packages and the GUI so that it will only be able to use CLI.  If I REALLY need the GUI again, it's just a simple reinstallation of packages and removing them when I am done.  I highly suggest going this route, as you get the best of both worlds.  You can use the GUI to set everything up, but you don't have the GUI working and taking up precious memory and CPU cycles when you don't need it.

Hope that helps!

v3xtra,

Thanks for your comment.

I was thinking about just uninstalling the desktop but was worried that it might break something due to various dependencies etc.

Is it safe to just uninstall the desktop?
What would the command be? Just <sudo atp-get remove ubuntu-desktop>?

Simon

---

### Post by Smartin on 2009-06-02
> **Alekz_ said:**
> Hi again!

I don't think you need to start all over again.. I've suggest you to read that thread to you think IF the X is really necessary for what you want! 
If it IS, so let it installed!

About GNU Screen, here is the Project Site: [http://www.gnu.org/software/screen/](http://www.gnu.org/software/screen/)

[]'s

Alekz,

I found the page you linked to earlier but could honestly not understand a single word of it. *Pure* gibberish :-)

I googled for images of it as well but it just seems to be another terminal. On my Mac I can open several windows, each with a terminal. I just don't get it at all...

Simon

---

### Post by netztier on 2009-06-02
> **Smartin said:**
> 

I googled for images of it as well but it just seems to be another terminal. 


Screen's far more than that. It is "multiple virtual terminals" within a single (local or remote) terminal/shell. It helps a great deal to administer remote systems: have a single SSH connection to a server on the other side of the globe or country, but have multiple virtual terminals within that session, and switch/flip between them. 

> 
On my Mac I can open several windows, each with a terminal. 


<rant> then stay on the mac and be happy with shiny clickety things</rant>

Sure - multiple terminal windows from your Mac, and if you need to have more than one terminal to a single remote system? Are you going to do an SSH connection for each terminal/shell you need? If the network connection to the remote system is flaky, you risk losing all SSH connections at once, and the programs that are running in their shells get terminated.

Not so with screen: single SSH session to the remote system, multiple virtual terminals/shells. Whatever you run in such a virtual terminal will continue running, even if the SSH connection to the remote system is lost (or intentionally terminated). Just reconnect and re-start screen with "screen -r", and you're right where you left off, with all virtual terminals as you had them before losing the connection.

> I just don't get it at all...

<rant>Obviously. Yet another youth spoilt by the GUIs, outing himself as such by calling other people's good work (screen) "gibberish".</rant>

Sorry for sounding harsh. Servers don't have GUIs. Period. There is a design decision behind this. Servers should run only services they have to run to fulfill their jobs: Web server, DNS server, DHCP server, mail server, database server, whatever they're intended for. Running all the background services needed to run a GUI is not part of a server's job, and it increases the "surface" for possible config errors or security issues.

If you absolutely need a GUI on a server (and your next idea will be to have "remote desktop functionality" with VNC, right? And of course "secured" by SSH, please? oh well ...), install Ubuntu Desktop and then add the server kernel to it. 

Since you want to run Ubuntu Server, I suspect you'll be needing the GUI for nothing more than running multiple editors and shells to modify config files. Then you're missing the point of having a GUI entirely. 

Need multiple shells in parallel? Use screen over an SSH connection. 

Want to disconnect/reconnect while keeping applications running in a shell on the remote system? Use screen over an SSH connection.

Need to edit a config file with your favourite GUI editor (like gedit in GNOME)? Use SSHFS (like doing a samba connect to a share on the server, only via SSH; see "Places" -> "Connect to Server..." ) to mount the server's file system to your local computer and then use your preferred local graphical editor.

Need to manage files graphically? Use SSHFS or install a text-based "GUI" like **mc** (Midnight Commander, a Norton Commander clone) on the remote system. Even runs withing a virtual shell/terminal as offered by screen.

Again: GUI on a Server? What for, exactly? SSH, SSHFS, screen and a text based editor program on the remote system do it all for you.


regards

Marc

---

### Post by Alekz_ on 2009-06-02
Nice write-up Marc! I agree with you, but that's your opinion (even if we have the same :D). That's why I didn't say him: "Hey, DO NOT install a GUI into your server!"

Anyways... I think your explanation about Screen was very clear! :) I couldn't do better! 

[]'s

---

