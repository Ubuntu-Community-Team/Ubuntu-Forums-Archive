---
title: "Problem with X2go (remote access) and permissions/administrator actions"
date: 2016-02-09
forum: Server Platforms
---

### Post by SomeITGuy on 2016-02-09
Hello,

I've got a problem with Ubuntu Server and remote access (using x2go at the moment), any help would be much appreciated:

I do need a GUI on top of the server because my deputy/the second admin is a windows guy and would be completely lost without a GUI (I know much more about Linux than him but I'm also not an real expert yet). Security is not really a problem here (the server will be in a physically separated/offline LAN later).

The server has to be accessible remote from different PCs (Linux & Windows) and so I first tried xrdp, but it had some issues (error message after every login, small graphical glitches and most important: A permissions problem when I tried to do administrative actions via GUI (no password box appeared as it does when logged in locally, just an error message that tells me I don't have the permissions to continue).

I'm now using x2go (works better overall) but the permissions problem is still the same! :( (running sudo commands via bash is no problem, but starting and using software like muon or synaptics via GUI is not possible (still authentification error), although the user has administrative rights and can do everything when logged in locally).


I tried different suggested solutions I found on the web (battling this issue again and again the last days):

First I tried:
```
touch ~/.Xauthority
chmod 600 ~/.Xauthority
```
[(source: ]("http://source: http://ubuntuforums.org/showthread.php?t=1138337")[http://ubuntuforums.org/showthread.php?t=1138337]("http://source: http://ubuntuforums.org/showthread.php?t=1138337") and others)

Then I tried modifying:
```
/usr/share/polkit-1/actions/org.freedesktop.NetworkManager.policy
```
(source: [http://scarygliders.net/2012/06/20/a-brief-guide-to-policykit/?PageSpeed=noscript](http://scarygliders.net/2012/06/20/a-brief-guide-to-policykit/?PageSpeed=noscript) )

Then I added these lines at top of the file /etc/X11/Xsession:
```
mcookie|sed -e 's/^/add :0 . /'|xauth -q
xinit -- -auth "$HOME/.Xauthority"
```
(source: [http://forums.linuxmint.com/viewtopic.php?f=47&t=61971](http://forums.linuxmint.com/viewtopic.php?f=47&t=61971) )

Nothing of these actions changed anything on my system/about the problem (of course I already restarted the server after each one of those, just for sure).


Any further suggestions anyone?
Is there any way to use a Linux system with GUI in the remote session with the same permissions that you have locally? :( I really hope so...
Thanks for reading!

Best Regards
SomeITGuy


System Infos:
Ubuntu Server 14.04.3 LTS
Installed Kubuntu Desktop
Installed X2go (following the X2go official documentation)

Hello again,

just noticed that there IS a difference between X2go and XRDP regarding permissions: In XRDP sessions I can't do ANY root actions (except sudo via bash), in my new X2go sessions I can now start apps like KDE Partition Manager, GParted or Gufw via GUI :) (only tried muon/synaptic the last times) but NOT muon/synaptics/update manager/software manager and all that stuff... :(
It's also not possible at the moment to install a *.deb via GUI (the dialogue appears but after clicking on "install package" nothing happens). :(

Anybody knows the specific reason why these software/packet managing tools behave different than other GUI tools that need administrative rights/root access? Personally I don't understand the difference at the moment...

Does somebody have an explanation for this behaviour?

Any help would be much appreciated!

Best Regards
SomeITGuy

---

### Post by howefield on 2016-02-09
Thread moved to the "*Server Platforms*" forum.

---

### Post by SomeITGuy on 2016-02-09
@howefield: Oh, sorry for posting in the wrong place... :(


I just noticed that it is also not possible to shutdown or restart the server via GUI (only bash+sudo), so the whole software/package management thing is not the only thing that doesn't work at the moment... :(

---

### Post by MAFoElffen on 2016-02-10
Just a few notes...
(1) a user's .Xauthority file is permission 600, but... you **must** also do #2... 
(2) Use chown to claim usership of the file by the user...

Optional- Go to post #2 of the sticky in my graphics resolution sticky in my sigline and follow the link to fixing .Xauthority files. ([Direct Link Here]("http://ubuntuforums.org/showthread.php?t=1743535&p=11404605#post11404605"))

(3) As for GUI/Windows? Secure remote admin for Windows Server can be done using ssh.  
(4) For Security, Win Service now has Win Server Core with no GUI.

Beyond that, back to Linux Servers-- I do a minimum instance of X for the admin of some of my Linux Servers. It just that some of the admin tools I use on those specific servers are vendor based GUI tools... It's also just faster and easier. I do Ubuntu Server, ... and Windows Server. So, I can translate in a way that your co-worker can relate to (LOL). Meanwhile, back at the Ranch... 

What is the error and what it it doing or not doing for you? Are you trying to do X forwarding or a remote desktop? It sounds as if you were trying to do remote desktop. Right? On Remote desktop, ensure your local user has X working on the local machine. So what do you have loaded as a desktop manager on your server? What OS is your server management console that you are connecting remotely with? Is your management console connected on it's own admin subnet? (re: network load of that segment)

We can help you make what you are trying to do, work. Or, at least, if not, get you going on alternative solutions, that will fit your requirements. I guess what that implies-- what is your basic requirements and what is your scope?

After that, we'll talk how permission work for Server admin, X, root and the admin group...

EDIT--
A little precursor on that-- You would have to go out of your way to get X to work for "root" as a user. root does not have a home directory, so does not have an .Xauthority file. It is not impossible, but also is not suggested, especially on a server. (and not suggested to allow root to log in remotely...)

For admin, you have privileged users, that can invoke administrative rights and privileges. Those users can run X, and administratively, can be tracked as a specific user in logs. Just like in many servers and domains, those users can be part of aan admin user group, to inherit those privileges.

---

### Post by SomeITGuy on 2016-02-10
Hi MAFoElffen,

thanks you for reply! :D


@(1) & (2): The user (called 'administrator' here) already is the owner of his .Xauthority file.
(I will have a look at your link later, thanks!)

@(3) & (4): Yes, I know, but a GUI is really wanted here (and there's not really a security risk here, a small LAN for a few developers/colleagues, offline/with "air gap").


Regarding your questions:
Currently I use the different platform specific "X2Go" clients to access an Ubuntu Server with installed Kubuntu/KDE Desktop and X2Go server from different clients (Windows 7 x64 and Kubuntu x64 (not the normal one but also an Ubuntu-Server-install+KDE, because of the ubuntu server RAID options...). As far as I understand, the X2Go client comes with an own local Xserver and connects to the server via NX & SSH (I'm new into this but most people seem to suggest X2Go for situations like mine).

The network load here is really not high (just the few devs in the small LAN).

> what is your basic  requirements and what is your scope?

I try to have (and offer my deputy) the exactly same user experience and administrative options like I/we would have when logged in locally on the server, also when logged in remotely (via X2Go at the moment, XRDP experience was much worse and VNC seems not to be a really good option today).

The problem now is that some(!) things which require you to type in your password for authentification work with the same user when logged in locally at the ubuntu server, but NOT when logged in remotely via X2Go (talking about starting the applications/tools via GUI/KDE menus here)! These seems to be a common problem, but I didn't found a working solution on the web.


Some examples for things that don't work:

- Shutting down or rebooting the server via KDE control panel/bar ("sudo shutdown now"... via bash works), it seems that the server will restart (you're disconnected) but it does NOT shutdown or restart.

- Creating new users (for samba...) via KDE system settings - You can open the tool, create users, but they are not saved/are gone when you go back. (It works when you use bash: "sudo systemsettings" instead of mouse clicks.)

- When trying to update or install software via muon/muon-discover, there's appearing a message which tells me that there's an authorization problem an it cannot proceed. (Works when you use "sudo apt-get upgrade" or "sudo muon" via bash and so on...)

- When trying to install a *.deb file just via mouseclick, the normal KDE window appears but you can click on the final "install package" button 1000 times and nothing happens (window does not even close).

As you see, sometimes it SEEMS to work first but in fact it does not (you're not asked for your password and your new users for example are just not created/saved), and sometimes you get immediately an permissions error message that you cannot proceed. This depends on the application/tool it seems. I think the reason is the same, and when you're logged in locally you would just get the typical password question and everything "just works".


Things that work (don't know why/where's the difference) for example - When you start them in your X2Go/remote session you're asked for your password (the normal way):
- KDE Partition Manager (KDE/Qt)
- GParted (Gtk)
- Gufw (Gtk)

I hope this explanation is somehow understandable (I noticed that sometimes former windows guys like me and Linux experts talk a different language a little bit :oops: ).


I'm not using the user "root" itself (remote or locally), I've talked about my user 'administrator' which is a "system administrator" on the server (at last that's what KDE calls an admin user). The whole thing is about starting applications/tools/commands which require "root permissions" (and therefore typing in your password). Sorry if I wasn't clear about that.

Of course, anything can be done anyhow in some different ways as I mentioned (bash + sudo + ...), but I hope and think there is a way to find the reason for the different behaviour (logged in locally vs. remote login) and truely fix this. :(

Again, thanks!


Best Regards,
SomeITGuy

---

### Post by MAFoElffen on 2016-02-10
Okay... on the understandings.

Think modules and Layers. When you install a desktop (You chose KDE) on server the server edition core, it installs XServer as a dependency. Open_SSH sevrer is a dependency of X2Go server, which is installed on your server. X2go uses bindings to these, to provide hooks to it's remote desktop.

(As as aside, Linux Software RAID (mdadm)... is available to install on any version of Ubuntu, not just on server. It's just that it happens to be on the server install diskso is very conventient.) 

So after X2go is installed, then the desktop bindings depend on which desktop package you install... for lxde, matte or plasma. You installed the plasma bindings to bind to your KDE Desktop right?

The 2 programs that you said asks for your password, do so whether remote or not. You need elevated permissions to use Gparted, KDE partition Manger, Gufw, Synaptic, and off-and-on it Ubuntu software center. 

On others... not sure "yet." I tell you what I will do. This weekend, I'll recreate what you have in one of my KVM Servers as guest VMs and try to recreate the problem. Today is my birthday. Tomorrow is my fiance's birthday... and I have give a presentation Friday... So that would be my soonest to do that.

---

### Post by SomeITGuy on 2016-02-11
> **MAFoElffen said:**
> Think modules and Layers. When you install a desktop (You chose KDE) on server the server edition core, it installs XServer as a dependency. Open_SSH sevrer is a dependency of X2Go server, which is installed on your server. X2go uses bindings to these, to provide hooks to it's remote desktop.

Okay, understood.

> **MAFoElffen said:**
> (As as aside, Linux Software RAID (mdadm)... is available to install on any version of Ubuntu, not just on server. It's just that it happens to be on the server install diskso is very conventient.)

Yes, I know I could configure mdadm manually on whatever distro I choose (after reading manpages and stuff), but using the ubuntu server setup (and installing Kubuntu-Desktop then) seemed the faster way for my Linux desktop workstation :wink: . Time's always a problem at work you know...

> **MAFoElffen said:**
> So after X2go is installed, then the desktop bindings depend on which desktop package you install... for lxde, matte or plasma. You installed the plasma bindings to bind to your KDE Desktop right?

Yes, I did ("aptitude install plasma-widget-x2go", source: [http://wiki.x2go.org/doku.php/wiki:advanced:desktopbindings](http://wiki.x2go.org/doku.php/wiki:advanced:desktopbindings) ).

> **MAFoElffen said:**
> On others... not sure "yet." I tell you what I will do. This weekend, I'll recreate what you have in one of my KVM Servers as guest VMs and try to recreate the problem. Today is my birthday. Tomorrow is my fiance's birthday... and I have give a presentation Friday... So that would be my soonest to do that.

That would be awesome, thank you very much! :D
(And no stress, really, birthdays & family first. It's also not a matter of one or two days more or less here for me in this case...) 

Best Regards,
SomeITGuy



Edit:
> **MAFoElffen said:**
> Optional- Go to post #2 of the sticky in my graphics resolution sticky  in my sigline and follow the link to fixing .Xauthority files. ([Direct Link Here]("http://ubuntuforums.org/showthread.php?t=1743535&p=11404605#post11404605"))

Tried this:
> sudo rm .Xauthority* 
touch .Xauthority 
chmod 600 .Xauthority
sudo shutdown now -r

...again, just to make sure I don't steal your time ;) . Didn't change anything as expected. :(

---

### Post by MAFoElffen on 2016-02-13
k- 

KVM VM guest x2go01 is Ubuntu Server 14.04.03 LTS, with ssh server. Updated, ppa added. Installed Kubuntu Desktop. Installed x2goserver, x2goserver-xsession, plasma-widget-x2go...

KVM VM guest x2go02 is Ubuntu Server 14.04.03 LTS, with ssh server. Updated, ppa added, Installed Kubuntu Desktop. Installed x2go-client...

Configured both. Tested. Snapshot attached... was controlling the x2go server on teh left from the x2go client on the right. Was looking at the system log viewer with no permissions problems... 

So what order did you install things?

---

### Post by MAFoElffen on 2016-02-14
Okay-

Configured it further last night and played with it both last night and this morning. Here is what I notice.

Everything fuctionally seems to work between them. At least on the surface.

There is occasional permission problems between them. This was not a handshake, keyring or X permssions problem. Nor was it a user or credential problem. It was an I/O problem. 

After using the keyboard to enter in passwords for elevated permissions, it would be denied. In the graphical kdesudo, when entring in passwords, I noticed that if I typed my password in fast, that it added too many characters. (therefore my password was incorrect.) I started up byubo and it was apparent that if I typed too quickly, that it echoed duplicate characters into the keyboard buffer of the driven session. Mouse clicks and menus where more correctly ID'ed than the keyboard.

But if I slowed down my keystrokes, everything was fine, and correct. Of course, this was not on iron. It was a remote connection to a VM Guest on my my hypervisior host, that was remotely driving another VM guest, through an x2go session...

I liked it, except for one thing... I could not see the bottom menu/status bar of the driven PC... So no KDE menus. So I had to use alternate methods to start applications (through hotkey-run) of the remote > remote'd > remote host that was in the driven session. Does it show on iron?

---

### Post by SomeITGuy on 2016-02-19
Hi MAFoElffen, thank you very much for testing! :) (and sorry for the delay, work nearly killed me the last days...)

Strange thing, I never noticed such a problem when typing in my passwords (only that the necessary window doesn't appear in some cases as explained :( ).

Were you able to create users via KDE GUI only for example? (Here they are not  really created/dissapear after leaving the window, only works via bash:  "sudo systemsettings"...).
Or did installing software via GUI/Muon discover work without problems?

> **MAFoElffen said:**
> I liked it, except for one thing... I could not see the bottom menu/status bar of the driven PC... So no KDE menus. So I had to use alternate methods to start applications (through hotkey-run) of the remote > remote'd > remote host that was in the driven session. Does it show on iron?

@X2go: I've seen exactly the same on a Windows 7 client (but if I resized the X2go window a bit, the KDE control bar appeared!), on my (K)ubuntu client it worked without this bug, all the time.
(On iron it works also here.)

> So what order did you install things?
After installing Ubuntu server:
```
sudo apt-get install kubuntu-desktop
```
(...installed some standard applications I always use on ubuntu servers, can't tell you the exact order anymore...)
(tried XRDP first at this point, but had the same permission problem (and some other issues))
-> Then decided to try X2go:
```
sudo apt-get install software-properties-common
sudo add-apt-repository ppa:x2go/stable
sudo apt-get update
sudo apt-get install x2goserver x2goserver-xsession
sudo aptitude install plasma-widget-x2go
```
(source: [http://wiki.x2go.org/doku.php/doc:installation:start](http://wiki.x2go.org/doku.php/doc:installation:start) )
-> Then I saw the permissions problems also is there on X2go... :(


Again, thanks!


Edit: I'm just thinking about a theory: Problem is not specifically Qt or GTK related... BUT: Perhaps it only applies to the basic elements of the KDE desktop (such als some system settings, user management and so on, these things don't work if started via GUI, KDE partition manager does work for example, as GParted also does...). Strange.

---

### Post by MAFoElffen on 2016-02-19
No, I did not have a problem at all... But...

Along with software-properties-common, I also installed python-software-properties... That was the on their own wiki, python-software-properties for all Ubuntu versions and software=properties-common just for Ubuntu 14.04 and beyond, 

*** Honestly... At first I left out software-properties-common (because I used someone's older instructions) and it worked fine. 

 - software-properties-common's description is: provides an abstraction of the used apt repositories. It allows you to easily manage your distribution and independent software vendor software sources. 

 - python-software-properties' description says:  provides an abstraction of the used apt repositories. It allows you to easily manage your distribution and independent software vendor software sources. 

^Notice they have the same description? See the difference? (LOL) Right now it works with 14.04 with python-software-properties because it had python 2.7 (and python 3 was introduced with that version). There is a shift to wire everything to python 3, but will get there with 16.04... software-prperties-common is the python 3 version of that, so it will be needed in 16.04, when the wiring is all done and then python 2.7 goes away...

What that means for 14.04 in the mean time, is that python-software properties is still required, So for both serve and client:
```

sudo apt-get install python-software-properties

```
Somewhere down the line, when it is not needed anymore, it will disappear in an update process...

---

### Post by SomeITGuy on 2016-02-23
Ok, interesting, wasn't aware of that...

I installed python-software-properties (and dependency pycurl) on server and client, rebooted both (two times...), but no change. :(

I think I will now give up on this specific issue and work around it somehow, it seems not resolvable at all... :( don't really get why it works for you without problems, but life (and IT) is strange sometimes. (Perhaps I should had installed these packages earlier/in a different order... who knows.)

Anyway, thank you very very much for your help and your effort! People like you make this forum an awesome place! :)

Best Regards,
SomeITGuy

---

### Post by andrew290 on 2016-03-07
Hi, as i understand, your server based on ubuntu system, and some other os based clients. For basic use  x2go you dont need any other packages, only x2go basic packages 
x2goserver x2goserver-extensions x2goserver-xsession on server system
and x2goclient on your client systems
beware of depencies of packages
so very important to use in connection options same Desktop enviroment ( if you have xfce on your server, please choose xfce in connection options)
x2go processes have nothing similar with your server access restrictions or other access managment. Simply, x2go connect via ssh, start xsession and show you picture.
In our organisation we have hybrid infrastructure with other OS (windows, ubuntu, but main is debian) and we implimented x2go for administrative and production with many additional options ( like terminal server with client-side-printing and home folder sharing).
I think, you should watch your server's account managment and your server's packages (try upgrade system, try repair package depencies, manage your sudoers file if you use it, manage your polkits, try to use common packages - for example, not to use gadmin-samba for samba configuration, use local accounts instead of any LDAP based) as i know, best performance for x2go is using KDE desktop, please check compatiblity with[ http://wiki.x2go.org/]("http://wiki.x2go.org/doku.php/doc:de-compat") , then try swich loglevel=debug in /etc/x2go/x2goserver.conf and tail -f yor syslog for any errors
ad.  what client you use? Pyhoca or x2goClient?

---

