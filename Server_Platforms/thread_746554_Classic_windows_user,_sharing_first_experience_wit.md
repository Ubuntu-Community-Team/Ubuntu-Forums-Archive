---
title: "Classic windows user, sharing first experience with ubuntu"
date: 2008-04-05
forum: Server Platforms
---

### Post by eriksson on 2008-04-05
_Please read the background info. below not just the question here_:

*Question: if I want to setup ubuntu server to act as a local file and print server (for windows clients) and also be able to host an intranet; is there an easier way to configure this without having to install the ubuntu desktop package on top?*

_Background info_:

**This is what I set out to do**:
Setup a dedicated server to accomplish the following and nothing else for maximum performance:
[LIST]
[*]act as a local file and printer server (for windows clients)
[*]host an intranet (apache, mysql, php)
[/LIST]

**This is what I got**:
[LIST=1]
[*]Downloaded then burnt ubuntu-7.10-server-i386.iso
[*]Ran the CD on a PC, installed everything, removed CD and rebooted. An error occurred: Invalid PBLK length
[*]Couldn't find a solution so installed ubuntu-6.06.2-server-i386.iso
[*]Booted fine, all good.
[/LIST]

My thoughts after seeing screenshots of ubuntu was that I would, after a successful complete installation, see a graphical interface with options to configure samba shares, printers, apache, php etc. But instead I was presented with a command prompt.

I read somewhere that ubuntu was for beginners, so at this point a felt tricked. So anyway I needed a graphical way to configure ubuntu so googled and ended up with this:
```
sudo apt-get install ubuntu-desktop
sudo dpkg-reconfigure xserver-xorg
```

Worked fine. Now when I boot up ubuntu it's pretty much like windows, graphically I mean. All I have to do is visually find where to configure samba shares, printers, apache, php etc. Should be easier than using the command prompt ;)

I'm happy I've gotten this far without any knowledge of linux but I do wonder if my ubuntu server installation is really a “server installation” any more since enabling a graphical interface. Tons of extra software has now been installed just to aid me to set up what I need to. It's more like a desktop computer now I guess.

*So here's another question; when I boot ubuntu and the GUI is installed but NOT loaded (just seeing the prompt) is the machine still efficient like a server rather than a desktop computer? Since the GUI is not loaded...*

Also, i wonder how on earth people keep ubuntu server up to date (security patches, new ubuntu releases) without a GUI. I mean it must be hell updating everything via a prompt, right? Hmm, maybe ubuntu server is for the hardcore people not soft people like me.

Best regards,
Eriksson

---

### Post by jpeddicord on 2008-04-05
> **eriksson said:**
> _Please read the background info. below not just the question here_:

*Question: if I want to setup ubuntu server to act as a local file and print server (for windows clients) and also be able to host an intranet; is there an easier way to configure this without having to install the ubuntu desktop package on top?*

If you want a user interface to configure it with, nope. If you don't want the desktop GUI, you'll have to edit Samba config files.

> *So here's another question; when I boot ubuntu and the GUI is installed but NOT loaded (just seeing the prompt) is the machine still efficient like a server rather than a desktop computer? Since the GUI is not loaded...*

In a way... yes. But once the GUI loads, it could be classified as a "desktop server." The only difference with the Server and Desktop CDs is the amount of preinstalled software on them. The server edition is preinstalled with a lot of web server tools, while the desktop edition has more user friendly tools.

> Also, i wonder how on earth people keep ubuntu server up to date (security patches, new ubuntu releases) without a GUI. I mean it must be hell updating everything via a prompt, right? Hmm, maybe ubuntu server is for the hardcore people not soft people like me.It's actually very easy:
```
sudo apt-get update
sudo apt-get upgrade
```
That will reload available updates, and then download and install them. Ubuntu (and Debian) are managed by packaging software called APT. Everything on your computer can be installed, removed, or upgraded with APT. Since everything is in packages, they can be grouped into repositories, which provide updates and new software off of the internet. For the desktop equivalent of APT, see System > Administration > Synaptic to install and remove packages. Applications > Add/Remove also uses APT to accomplish this, but with a friendlier interface.

See the following link for more information:
[http://dag.wieers.com/rpm/FAQ.php#B3](http://dag.wieers.com/rpm/FAQ.php#B3)

Jacob

---

### Post by FakeOutdoorsman on 2008-04-05
> **eriksson said:**
> *Question: if I want to setup ubuntu server to act as a local file and print server (for windows clients) and also be able to host an intranet; is there an easier way to configure this without having to install the ubuntu desktop package on top?*

Yes.  You can avoid the ubuntu-desktop "metapackage" (it's a collection of a bunch of programs) and install just the components you need.  If you want a GUI, you will need to install xorg, which is the "backend" of a GUI session.  This article has some good examples: [Installation / Low Memory Systems]("https://help.ubuntu.com/community/Installation/LowMemorySystems") [Ubuntu Wiki].

> **eriksson said:**
> *So here's another question; when I boot ubuntu and the GUI is installed but NOT loaded (just seeing the prompt) is the machine still efficient like a server rather than a desktop computer? Since the GUI is not loaded...*
In my opinion it wouldn't be as efficient, but the difference would be negligible on a modern machine that doesn't have much traffic.

> **eriksson said:**
> Also, i wonder how on earth people keep ubuntu server up to date (security patches, new ubuntu releases) without a GUI. I mean it must be hell updating everything via a prompt, right? Hmm, maybe ubuntu server is for the hardcore people not soft people like me.

As jacobmp92 states, it's as easy as that.  You can have Ubuntu apply security updates on its own:
With a GUI: System -> Administration -> Software Sources -> Updates Tab -> Check for Updates: Install security updates without confirmation.

Command-line: [Automatic Security Updates]("https://help.ubuntu.com/community/AutomaticSecurityUpdates") and [Automatically update your Ubuntu system with cron-apt]("http://www.builderau.com.au/program/linux/soa/Automatically-update-your-Ubuntu-system-with-cron-apt/0,339028299,339279542,00.htm") and [Apt Get How To]("https://help.ubuntu.com/community/AptGetHowto").

I manually update because I like to see what is being installed.

I think you did quite well on your own so far as a new Linux user.

---

### Post by FakeOutdoorsman on 2008-04-05
> **jacobmp92 said:**
> The only difference with the Server and Desktop CDs is the amount of preinstalled software on them.

I believe Ubuntu Server also uses a different kernel configuration than Ubuntu Desktop.

---

### Post by dmizer on 2008-04-07
my opinion is that it is dangerous to install a gui onto a server you intend to have hosting a web site.

here's why:
on anything that is exposed to unfettered internet, you want it to have as low a profile as possible.  that is ... when you install gui, you also install a whole range of little applets, daemons, scripts, and programs.  any of which could be exploited through the web to gain access to your server as a result of a small mistake in your PHP, HTML, or MYSql code. this is to say nothing of an unpatched security hole in any of the gui apps which could be used to exploit your server.

and in case you think i'm just being paranoid, let's not forget that in the recent CanSecWest hacker contest, mac fell because of this.

THIS is why linux makes a much safer alternative over windows for hosting a website.  if you install a cli only server, and lock down all the needless tools, resources and scripts, hackers will have a hard time doing anything on your server beyond DOS attacks.

finally, most server configuration will take place in the command line anyway.  so there's really no "ease of use" to be gained by installing a gui on a server.

it's a different story though, if your server will never look past your router firewall.

---

### Post by tubasoldier on 2008-04-07
The reson that you always end up with a command prompt and not a GUI when you boot is because GDM (gnome display manager) is disabled by default on a server install. This is a good thing, you don't need it to run a server. If you want it to configure the server that is fine, but no need to run a graphical environment whilst serving. And as already previously posted, it just adds more overhead and more unneccessary security risks.

Most of the server configuration that you did through the command line is simply modifying text configuration files. This can easily be done on the command line. For instance the apache configuration file is in /etc/apache/apache.conf . 
Windows print server will be done through samba. /etc/samba/samba.conf
Command line text editors usually have a higher learning curve. Vim is great when you know all the keyboard shortcuts.
When your not familiar with Linux commands or the command line then the GUI will work fine.

---

### Post by dmizer on 2008-04-07
> **tubasoldier said:**
> The reson that you always end up with a command prompt and not a GUI when you boot is because GDM (gnome display manager) is disabled by default on a server install.

a default ubuntu server install does not have an X server (gui) installed at all.

---

### Post by eriksson on 2008-04-07
To jacobmp92, FakeOutdoorsman, tubasoldier, dmizer thank you for replying.

Your input got me going again! Yesterday I successfully installed a minimal GUI using: ```
sudo aptitude install x-window-system-core fluxbox fluxconf thunar synaptic firefox
```
I did however have to enable universe package downloads (uncomment two lines in sources.list). This was a pain because gedit reported "cannot open display: null" but using nano worked fine don't ask me why. Mixed feeling about fluxbox, kind of fell for it beeing lightweight but coming from XP takes time to adjust.

The idea is to configure my setup using a suitable GUI then uninstalling GUI when it's not needed.
*What do you think about the idea?*
```
apt-get aptitude install ubuntu-desktop
```
When I'm done configuring everything:
```
apt-get autoremove ubuntu-desktop
```
Still haven't found where to setup apache, mysql and php after installing LAMP. *Is there not a GUI configuration for LAMP installations?*

Anyho.. feeling optimistic about linux thanks to ubuntu!

Only really problem is when i read tutorials online that say "just write this at the command prompt" to do this... which sometimes works but has also resulted in errors. Errors one has no idea how to handle.

Most often the errors seem to be related to device drivers, like the graphic card for instance when i tried to run gedit. Running notepad in windows is... indeed. Makes me wonder if i will ever be able to setup a local mail system considering I failed to run gedit ;)

But I won't give up now. I'm 30 and have as you understand waited a long time before diving into the world of linux (running windows for 15 years). It's never to late right.

Thanks again for your kindly guideance in my quest.

---

### Post by cyphur on 2008-04-07
i used this link to setup a lamp server here in the office. It also has instructions on installing WebMin which is the web based admin mgmt tool. 

[link]("http://onlyubuntu.blogspot.com/2007/10/ubuntu-710-gutsy-gibbon-lamp-server.html")

It can make your life alot easier, there is a learning curve but if your using the forums here and da google for answering questions already, then you should be fine. 

then you don't have to install a GUI and just use whatever browser you like..

---

### Post by dmizer on 2008-04-07
```
apt-get autoremove ubuntu-desktop
```
will not remove the gui.  it will only remove the metapackage for ubuntu desktop and leave all the actual gui apps in place.  it is fairly difficult to get rid of the gui once it's installed.

> **eriksson said:**
> Still haven't found where to setup apache, mysql and php after installing LAMP. *Is there not a GUI configuration for LAMP installations?*

like i said in my reply before ... there is no gui for configuring server installations.  this is why there is no real advantage for installing a gui on a web server.

---

### Post by FakeOutdoorsman on 2008-04-07
> **cyphur said:**
> i used this link to setup a lamp server here in the office. It also has instructions on installing WebMin which is the web based admin mgmt tool. 

I've also used Webmin in the past and I recommend it for beginners or for those who don't want to deal with command-line as much.  It will allow you to configure most server applications through your web browser.  Kind of a middle-ground between standard server and a "desktop" server with xorg.

There is also the [eBox Platform]("https://help.ubuntu.com/community/eBox"), but I don't have any experience with it.

---

