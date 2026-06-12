---
title: "&quot;On Demand&quot; Config GUI"
date: 2008-11-12
forum: Server Platforms
---

### Post by Nerun on 2008-11-12
Hello,

I am first time poster, long time reader. Thanks for all the questions you have already answered unknowingly in the past, maybe this great community can help me with this idea I have.

**Long story short:** I'm looking a GUI that only starts on demand to change server config settings.

**Whole story:** Until now I used the Ubuntu server as my platform and will most likely switch to JeOS on the next release, but that shouldn't change anything I guess, so JFI.

What I am doing is creating a VMWare Applicance that doesn't really need a GUI on the server at all. Most of the time noone is going to look at it, and when someone does, it's for config purpose. And there is my problem: text based config is just boring, ugly, complicated. I am a Linxu admin, I have no problem with that, but other people who fire up that server may have never used Linux before.

I thought about using Webmin, which is awsome I think, but the problem with that is that the network config would still have to be done text based, and that is one of the main parts. No my idea goes along the line of providing a minimized GUI for config that is only started on demand. Like having a command prompt to log in that runs as in a normal "non-GUI" console. Now if user "admin" logs in, he gets a normal console. If user "config" logs in the GUI is fired up and a few apps are available to make necessary settings.

I am also I'm wondering what sort of packages I will need to set up a extremely light weight GUI and what apps you can recommend to configure server settings.

Thanks for reading through and some advance /cheer for the helpers!

GzG
Nerun

---

### Post by volkswagner on 2008-11-12
I believe this can be accomplished with a server install and a login manager.

This may help.

[https://help.ubuntu.com/community/Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

---

### Post by Nerun on 2008-11-12
thanks i'm going to check that out. anyone know if it is possible to have a different login behaviour for different users. like i described above: one gets a command line and the other one is forwarded to the gui. i thought about putting that into the users startup script, but that seems more like a workaround.

i'm also interested in enhancing the login prompt. a few years ago i worked with SuSe and i believe they had something a bit more stylish. basically any hint into a direction of a framework/tool/etc. will help me.

Thanks again!

---

### Post by HermanAB on 2008-11-12
SSH of course.  You can run X applications over SSH, without having X running on the server.  So with the server in runlevel 3 (no X), you can SSH to it and do:
$ ssh -X -C -c blowfish user@server gnome-panel

and you will get a panel for the server and then go click happy as if you are sitting in front of the server with a full desktop system.  This will even work from a Windoze client, provided that it has Cygwin or Xming running.

Cheers,

Herman

---

### Post by Nerun on 2008-11-12
yah i thought about that, but the majority of people working with the system will be windows users, so that's not really an option, if not everyone can use it. thanks tho :)

---

### Post by Iowan on 2008-11-13
I haven't tried it, but have heard [ebox]("http://ebox-platform.com/") mentioned as a configuration tool.

---

### Post by hictio on 2008-11-13
I'm sorry, perhaps you have been thru this already, but why a "GUI config on demand"? Why don't you isntall and config [Webmin](http://www.webmin.com/) on your server, so those Windows users can login thru a browser, and use its GUI & menus to do what ever they have to do.

---

### Post by windependence on 2008-11-14
While things like WebMin and eBox are a good way for your Windoze users to admin the box, you should never count on them 100% on a production server. What if the web service goes down? What if you get hacked? What if your web GUI isn't configured correctly? You should still always have a way to get on to the command line and fix things and you should understand how to do it. Otherwise, you could be cursing yourself later. I have been there.

-Tim

---

### Post by Nerun on 2008-11-14
thanks all for the replies!

> **hictio said:**
> I'm sorry, perhaps you have been thru this already, but why a "GUI config on demand"? Why don't you isntall and config [Webmin](http://www.webmin.com/) on your server, so those Windows users can login thru a browser, and use its GUI & menus to do what ever they have to do.
As I said above, I don't think that's a good wtg because users will have to set up the network over that config interface. If that machine has no IP, because the network settings have not been completed, there is no webserver to connect to. Hen and Egg kinda story ;)


> **windependence said:**
> While things like WebMin and eBox are a good way for your Windoze users to admin the box, you should never count on them 100% on a production server. [...] Otherwise, you could be cursing yourself later. I have been there.
-Tim
I totally agree with you there. I would never rely on graphical frontends, whatever type. You still gotta have the tools and knowledge to use the command line.


_So here is what I have done:_
I set up the "server minimal virtual machine" variant of 8.10 server. Added openbox, pypanel and idesk as base for my graphical system. I had to strip down the services started in runelvel 2 that are only necessary with X, but that was no biggie. After that's completed, my server boots with ~60MB memory usage into normal console (note: i don't have a login manager).
Now if UserA logs in, everything stays as it's with server linux and user get's the bash. If UserB logs in, I switch the runlevel to 3 and start X (memory usage goes up to ~125MB and that's enough for me not to boot into runlevel 3 directly). If the user logs out, a script sets the runlevel back to 2 and logs out the user.

With VMWare tools and the above I'm at about 750MB df now, which is satisfying for my needs atm.

Thanks again to all that gave me ideas!

---

