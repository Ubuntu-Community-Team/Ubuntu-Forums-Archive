---
title: "Server or Desktop"
date: 2008-04-24
forum: Server Platforms
---

### Post by deejross on 2008-04-24
I will be installing Hardy on a server soon and I'm probably going to install Webmin on it for administration, but everyone around here is afraid of having a server with no gui. So I will probably put something lightweight on it like Xfce. But my question is, should I install Xubuntu desktop version, or should I install the server version, then install Xfce?

And if the recommendation is to go server version then install Xfce, then I have one more question...Do I just install xubuntu-desktop and it starts automatically on boot or is there something special I need to do to ge Xfce to start on boot?

Thanks in advance for your input.

---

### Post by Dr Small on 2008-04-24
Will the server be headless, but accessible over the network?
If so, I would meerly install a small lightweight window manager (such as IceWM, Flux or OpenBox) and then port it all with SSH. There would be no need for Xorg, since it will be headless.

By the way, Xfce is not the *de facto standard* of being lightweight anymore.

Dr Small

---

### Post by deejross on 2008-04-24
Well, we are running Gnome on it right now, and I've heard that Xfce is lighter than both Gnome and KDE, so that's where I based by decision of Xfce on. Also, the server will be mostly headless, but it is connected to a kvm switch along with the other servers, so that's why we would need some kind of interface.

I've heard some good things about OpenBox, so maybe I'll check that out. But anyways, it sounds like the recommendation is leaning toward installing the server version, then installing the window manager of choice. So, for example, if I wanted to install OpenBox, i would > sudo apt-get install openbox and it would automatically start the window manager on boot?

And one final question...which lightweight would you choose? I don't have any experience with any of them. I would be looking for something easy to use. Remember, the gui would be used mainly by Windows admins since I know my way around the command line and they are afraid of it.

---

### Post by Oak37 on 2008-04-24
I'm not too sure if the window manager would automatically start on boot but they can be started through the terminal easily enough e.g Fluxbox is started by the startfluxbox command.

There are a few lightweight window managers listed and described [here]("https://help.ubuntu.com/community/Installation/LowMemorySystems#head-013d87a964541617a35fb741ed30ce5ec628013a")

---

### Post by Dr Small on 2008-04-24
I would choose IceWM. I am using it right now, and it works great for a desktop and is lightweight, so it would be perfect for a server.

Since you say that it is connected via KVM switch, and not SSH, you will most likely need Xserver on it too, for display of course.

It is generally not a wise idea to have a Window Manager running at startup (unless you absolutely need to), because even though it is lightweight, it will still use some small resources. If you wanted to, you could install XDM, which will load at bootup and prompt you for a Username / Password.

This can then be configured to load your Window Manager, and will allow you to Login and Logoff as you need to.

Dr Small

---

### Post by lespaul_rentals on 2008-04-24
> **deejross said:**
> everyone around here is afraid of having a server with no gui

Yikes.  If they're not comfortable using the command-line...well, whatever.

Dr Small's suggestion is spot-on.  Don't use Xfce or any other desktop environment, instead use a window manager.  My favorite is Fluxbox, but why not just use the default X.Org window manager?  Start an X11 session and use that.  That's as lightweight as you're going to get.

---

### Post by deejross on 2008-04-24
I just looked at the link provided by Oak37 which related to a few different window managers and I have to say, after looking at IceWM, I think I might go with that. It's got a theme that looks like XP, so the Windows guys would be happy with that one :)

But let me ask this because I've been doing some looking around and can't seem to find a definitive answer. IceWM is a window manager, and Xfce is a desktop environment. So correct me if I'm wrong, but from what I've read, this is the difference between the two: the window manager just manages windows. Other things like file managers, system configuration tools, a desktop with icons are all different pieces, while a desktop environment encompasses all those pieces into one product.

If that's the case, then couldn't I install Xfce (for the lightweight applications) and use IceVM as the window manager? Would that be still be efficient, or is using any of the Xfce applications a bad idea?

Sorry about all the questions, but I'm so used to using either Gnome or KDE where it's all built-in, I've never really messed with window managers before, so I don't know the details, but I'm interested!

---

### Post by eriqjaffe on 2008-04-24
> **deejross said:**
> So, for example, if I wanted to install OpenBox, i would> sudo apt-get install openbox and it would automatically start the window manager on boot?Not exactly, since you'll still need X to handle that.

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal) has some good information on setting up command-line systems, most of it will apply to a server install as well.

Technically, XFCE is just a window manager.  If you want to install the XFCE-based DE, you'd just ```
apt-get install xubuntu-desktop
```

---

### Post by Dr Small on 2008-04-24
> **deejross said:**
> I just looked at the link provided by Oak37 which related to a few different window managers and I have to say, after looking at IceWM, I think I might go with that. It's got a theme that looks like XP, so the Windows guys would be happy with that one :)

But let me ask this because I've been doing some looking around and can't seem to find a definitive answer. IceWM is a window manager, and Xfce is a desktop environment. So correct me if I'm wrong, but from what I've read, this is the difference between the two: the window manager just manages windows. Other things like file managers, system configuration tools, a desktop with icons are all different pieces, while a desktop environment encompasses all those pieces into one product.

If that's the case, then couldn't I install Xfce (for the lightweight applications) and use IceVM as the window manager? Would that be still be efficient, or is using any of the Xfce applications a bad idea?

Sorry about all the questions, but I'm so used to using either Gnome or KDE where it's all built-in, I've never really messed with window managers before, so I don't know the details, but I'm interested!
Well, Desktop Environments usually come as a kit with it to make everything work. The whole 9 yards.

But even if you install a Window Manager, you can seperately install what other application you want, such as a file manager (PcManFM, thunar) and whatever else you need seperately.

Dr Small

---

### Post by urukrama on 2008-04-24
> **eriqjaffe said:**
> Technically, XFCE is just a window manager.  If you want to install the XFCE-based DE, you'd just ```
apt-get install xubuntu-desktop
```

That is incorrect. Xfce is a desktop environment (DE), that includes a window manager (xfwin4). You can replace the window manager in Xfce; I sometimes use it with Openbox.

Xubuntu-desktop is a metapackage that installs not just xfce (the DE itself) but also a whole host of gnome stuff and applications that come with a full Xubuntu install (if you get the recommended packages). Compare the dependencies of [xubuntu-desktop]("http://packages.ubuntu.com/hardy/xubuntu-desktop") with those of [xfce4]("http://packages.ubuntu.com/hardy/xfce4").

I generally install xfce4 rather than xubuntu-desktop, as it gives me a much faster and leaner desktop environment.

---

### Post by eriqjaffe on 2008-04-25
> **urukrama said:**
> That is incorrect. Xfce is a desktop environment (DE), that includes a window manager (xfwin4). You can replace the window manager in Xfce; I sometimes use it with Openbox.

Xubuntu-desktop is a metapackage that installs not just xfce (the DE itself) but also a whole host of gnome stuff and applications that come with a full Xubuntu install (if you get the recommended packages). Compare the dependencies of [xubuntu-desktop]("http://packages.ubuntu.com/hardy/xubuntu-desktop") with those of [xfce4]("http://packages.ubuntu.com/hardy/xfce4").

I generally install xfce4 rather than xubuntu-desktop, as it gives me a much faster and leaner desktop environment.Thank you for the correction on that.

---

### Post by deejross on 2008-04-25
Thanks for the great information guys. I think I'm going to do what urukrama mentioned and install xfce4. Then from there I'll prolly install IceWM as Dr Small mentioned. But who knows, there's just so many window managers to choose from :)

Thanks to everyone for their input!

---

### Post by gxbacher on 2008-04-25
I'd like to interject if I may - what would people recommend I install (Server or Desktop) if the box will be used fairly evenly as both server and workstation? (kind of the opposite of the original poster) I've seen older posts that recommend either way.

More detail - the server will be on 24/7 hosting mostly personal but some non-critical business apps. LAMP, Bugzilla, Samba, SSH. It will be used on a daily basis as a workstation, potentially by multiple users. Lastly, I'd like it to run green (power saving, quiet), so if the base install makes a difference in that regard, it would be helpful.

Thanks, and let me know if I posted in the wrong place. I'm new to the forum, but not Linux or Ubuntu.

---

### Post by lespaul_rentals on 2008-04-25
> **gxbacher said:**
> I'd like to interject if I may - what would people recommend I install (Server or Desktop) if the box will be used fairly evenly as both server and workstation? (kind of the opposite of the original poster) I've seen older posts that recommend either way.

More detail - the server will be on 24/7 hosting mostly personal but some non-critical business apps. LAMP, Bugzilla, Samba, SSH. It will be used on a daily basis as a workstation, potentially by multiple users. Lastly, I'd like it to run green (power saving, quiet), so if the base install makes a difference in that regard, it would be helpful.

Thanks, and let me know if I posted in the wrong place. I'm new to the forum, but not Linux or Ubuntu.

I would recommend the server kernel.  You could install Server 8.04 if you wanted to, as it has LTS.

---

### Post by deejross on 2008-04-25
Actually, since the question was asked, I am kind of curious myself about the difference between the server and desktop versions. Is there anything extra you get by installing the server version over the desktop security-wise, like app-armor? Or do you get all that stuff with desktop, the only difference being that desktop installs a gui?

---

### Post by Oak37 on 2008-04-25
> **deejross said:**
> Actually, since the question was asked, I am kind of curious myself about the difference between the server and desktop versions. Is there anything extra you get by installing the server version over the desktop security-wise, like app-armor? Or do you get all that stuff with desktop, the only difference being that desktop installs a gui?

I think app-armor is included in both versions, there's a list of kernel specific optimisations for the server edition [here.]("http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel") There are far less packages installed by default on the server version too.

---

### Post by OrionJZ on 2008-04-26
Good day,

About the question ¿Server or Desktop?, let me share my experience like IT Director:

We use Ubuntu Server for specific web applications. Alfresco, OpenFire, SugarCRM, our Wiki, Blogs and Java developments.

**Why Server?**

-(1) Because the Server edition is light,safe and we want that our users and customers(WAN, LAN, Extranet) had the best experience with the services that we put online.

-(2) Because we can control all the components without compromise security. We only install that we need.



CONS: You must know the commands.
THE BEST: You must think.!!! You can learn more.!!! You are not linked to license issues.\\:D/\\:D/\\:D/.!!!

**When Desktop?**

When you want to have a good experience for the end users with compromise your company. When you want to use excellent applications. Easy to configure, easy to use.

We proof Fedora, RedHat, Suse, Oracle Linux, but nothing like Ubuntu.

---

### Post by windependence on 2008-04-30
> **OrionJZ said:**
> Good day,

About the question ¿Server or Desktop?, let me share my experience like IT Director:

We use Ubuntu Server for specific web applications. Alfresco, OpenFire, SugarCRM, our Wiki, Blogs and Java developments.

**Why Server?**

-(1) Because the Server edition is light,safe and we want that our users and customers(WAN, LAN, Extranet) had the best experience with the services that we put online.

-(2) Because we can control all the components without compromise security. We only install that we need.



CONS: You must know the commands.
THE BEST: You must think.!!! You can learn more.!!! You are not linked to license issues.\\:D/\\:D/\\:D/.!!!

**When Desktop?**

When you want to have a good experience for the end users with compromise your company. When you want to use excellent applications. Easy to configure, easy to use.

We proof Fedora, RedHat, Suse, Oracle Linux, but nothing like Ubuntu.

I must agree. You don't *need* a GUI to manage a server, in fact, the cli is much easier and faster to use if you just simply learn a few basic commands. 

The reason "everybody" says load a GUI is because they come from a Windows world and have been duped into thinking you need a GUI to do everything. I challenge you to be different. There is nothing you can do in a GUI that you can't do from the command line and more. 

You can load Webmin and admin everything from there. Make sure you set it up to use secure https. It's agreat tool and visual too, but don't forget, the best admin toool of them all - ssh.

-Tim

---

### Post by hyper_ch on 2008-04-30
All configuration is done through text files... and text files look the same in the cli as they do in a gui...

so, why would you want to install a gui on there?

---

### Post by deejross on 2008-04-30
Just to let you all know, I am perfectly happy using the command line. It's the other Windows folk around here I'm worried about. Their mentality is *"if it doesn't have a GUI, I ain't using it"*. If you have ever worked with a Windows Admin before, you know exactly what I'm talking about. They don't like change, and they certainly don't like the CLI. They are like spoiled children in that they will simply **refuse** to use it.

If they see a server sitting at the command line, they think it's broken. So simply telling them to "man up and just get f'ing used to it" will not fly. That's why we need a GUI, because the Windows guys "think" they need it.

btw, OrionJZ, Thanks for the great information on the difference between desktop and server versions. That really helped me decide to use the server version, then add the GUI later for the Windows guys.

While writing this post, I had an interesting idea on how to make the Windows guys happy without actually installing a GUI. I'll install and set up Webmin (since that seems to be the most favored admin tool) and set them up with WinSCP (SSH/SFTP) so they can do file management using a GUI. They like all the servers to have front-ends, but if I tell them to treat this server like a network appliance, I might be able to get away with making it a headless server.

I really want to thank everyone for their input on this so far.

---

### Post by mam00th on 2008-04-30
> **hyper_ch said:**
> All configuration is done through text files... and text files look the same in the cli as they do in a gui...

so, why would you want to install a gui on there?

Indeed, I second that

---

### Post by lespaul_rentals on 2008-05-05
Actually, to all the people talking about the differences between the server and desktop kernels, you're really not addressing the important differences.  Sure, the server version comes without a GUI and has fewer packages, but that really is just scratching the surface.

It's all in the way the kernel is compiled.  The desktop kernel is compiled in such a way that it gives the best experience for the average PC user.  The desktop kernel actually *hurts* performance under the surface, believe it or not.  However, to the end user, the computing experience actually seems better because the kernel gives priority to the applications that the user is directly interacting with.  DMA, devices, background processes, daemons, and the like are not given full priority.  The server kernel, on the other hand, is compiled to favor background processes, daemons, memory allocations, I/O tasks, data read/write, and the like.

Is the difference substantial?  For a home server, probably not.  But for anything enterprise, I would never consider running a server on the desktop kernel.  When you need to get every last drop of performance out of a machine, you want a kernel that can handle multiple users accessing NFS shares, mission-critical services, etc..

So please, learn about the differences underneath the surface before you type.  :)

---

### Post by exaviorn on 2008-05-05
Basically if you have KDE/Gnome you are wasting committed memory
lightweight GUI's eg:Icewin take less
LTS takes virtually none :)
If you need a totally committed server go LTS,you like your GUI but want  committed server install webmin:It has module configuration and a GUI java filemanager:)

---

### Post by lespaul_rentals on 2008-05-05
> **exaviorn said:**
> lightweight GUI's eg:Icewin take less
LTS takes virtually none :)

LTS has nothing to do with the window manager.  It means "Long Term Support," which has to do with the length of time that Ubuntu promises to release security updates.

---

### Post by stream303 on 2008-05-05
The following might be helpful:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

It is geared towards getting a minimal gui up and running for those with low memory by purposely using the server install as a base.

In my case, I used the server image for installation, and only added xorg, and lwm as my window manager - and No login manager.

I only use startx to bring up my window manager, do my edits, and then drop out of X.  The server underneath still runs.  (using startx means that you'll probably want to configure your own .xinitrc file)

This might help if you absolutely need some sort of graphical interface - even just to show it off. :)

---

