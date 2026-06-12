---
title: "Ubuntu ZeroConf Home Sever"
date: 2006-10-26
forum: The Cafe
---

### Post by ago on 2006-10-26
What about creating a Ubuntu-ZeroConf-HomeServer package as a spin-off of edubuntu?

"ZeroConf" in the sense that it uses ZeroConf and in the sense that it will work out of the box with reasonable settings.

"Home Sever" in the sense that its main (plugin-based) functionality should cover the needs of a typical home server. Including:

[list][*] file server (indexed by tracker),
[*] printer server,
[*] multimedia streaming,
[*] DVB/capture card streaming,
[*] shared contacts,
[*] shared calendar,
[*] shared applications,
[*] net-install,
[*] thin-client server,
[*] firewall/gateway/proxy server with A/V and antispamming filters,
[*] centralized access restrictions to machines/web/applications,
[*] user profiles,
[*] backend for MythTV or equivalent,
[*] import file facilities, that will also index and encode as appropriate (appropriate = using open standards)
[*] one click backup to internal/external drive
[*] .... 
[/list]

All the above with a single, very easy to use web interface designed for inexperienced home users with only absolutely necessary options (for instance do not use groups, only users) all in plain english and well preconfigured. See Vista parental control for a good example of a nice interface. 

Users should be able to install the HomeServer package and required plugins on one machine, and simply register or netboot other clients with this server in order to have a network ready in minutes. 

The server should be modular so that it should be easy to add extra functionality. Each "plug-in" should be a deb package bundling required servers (as dependencies), good initial configuration, and web interface modules. The web interface should detect new plugins and show them in the menu. The focus of each module should always be on an extremely streamlined and intuitive user interface and good pre-configuration that should work out of the box. Advanced users can always access the daemons via webmin or directly via ssh.

This is useful today, also in homes that have clients from other OSs, or even for small businesses (a smallbusiness server package could be created as a twin project). It will become even more relevant in the near future when sub $100 machines [like these](http://www.linutop.com/) will become ubiquitous and will be used as thin/fat clients as well as set-top boxes all over the house...

Reagarding set-top-boxes, the HomeServer could be a good occasion to standardize the backend. What I mean is that freevo, elisa, mythtv, etc could be split into a "standard-compliant" backend and a separate frontend, so that the same backend could work with different frontends. A MediaServer module might take such role, taking some of the load off the shoulders of such projects and avoiding code duplication. The shared folders are a natural place to store media files, metadata and querying could be handled via filesystem indexing (tracker), epg could be centralized, capture cards could be in the server as opposed to the client to get rid of cables in the living room, lots of possibilities.... This would make it easier to penetrate the set-top-box market as soon as possible, which is important since we can then spread open codecs and be in a better position to fight DRM.

Finally there should be a small client-side application available also for windows and mac to register and configure such clients with the main server and install required open codecs.

---

### Post by diepruis on 2006-10-26
Servers for dummies, eh? Might be a good idea.

---

### Post by ago on 2006-10-26
Ideas for simplified web interfaces

**MAIN**
```
Info:
internet connection is on/off
machines connected
users connected

Menu:
General settings
Web Shield
...
```

**General Settings**
```
network name
admin password
system update
```

**Backup**
```
backup folder
scheuled backup (listbox yearly, monthly, weekly, daily)
backup now
restore all
restore individual files
```

**Web Shield**
```
Antispamming: (listbox none/mark emails/move emails)
Antivirus: (listbox none/anyfile/usualsuspects)
Blacklist:  (list of ips to block)
Open ports: (list of open ports) 
```

**Shared Folders** (only folders within /home/shared)
```
import files
Folder | Users who can access | Users who can write | Type (music/doc..) 
---------------------------------------
docs  | ago, pino | ago | docs
music | ago, pino | ago, pino | music
video | ago, pino | ago, pino | video
...
new    
```

**Shared Apps**
```
listbox (all/installed/groups) | search 
name| checkbox for add/remove | Users who can access
---------------------------------------
XYZ | X | ago
```

**Users**
```
name  | can use pc  | can use web | can use apps | reset password
---------------------------------------
ago  | green | green | green
guest | yellow | yellow | red
new
```

**User > Restrict PC Access**
```

select/unselect the time when XYZ can use the computer
ALL 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24
sun
mon
tue
wed
thu
fri
sat
```

**User > Restrict Web Access**
```
can download | filter content | black list | white list 
```

**User > Restrict Application Access**
```
Application | can use yes/no
---------------------------------------
XYZ | X
ZXY | 0

```

**Machines**
```
name | mac | allowed 
---------------------------------------
agomachine | XYZ | green
guest | * | red
```

---

### Post by mozetti on 2006-10-26
Okay, but why base it off edubuntu, versue ubuntu? Or, make it so it works on all flavors?

---

### Post by ago on 2006-10-26
> **mozetti said:**
> Okay, but why base it off edubuntu, versue ubuntu? Or, make it so it works on all flavors?

Sure it should be a package so that you can install it on top of any member of the Ubuntu family. I mentioned edubuntu because many of the technological issues have already been addressed there...

---

### Post by kopilo on 2006-10-26
I like this a lot, I do a lot of IT stuff (programming in Java, etc) however I don't want to spend a lot of my time working out how to make my system more secure as well as doing all the different configurations.

I definatly like this idea.

I'd also allow the user to choose the location of shared folders, unlike windows XP. However a default directory could be assigned just in case the user isn't that savvy. ;)

I like the web interface idea, maybe have it so the address of the webinterface is something like "config:system", not an ip address that people have trouble remembering.
**User > Restrict Drive Access**
```

Drives | Users who can access |  comment
----------------------------------------------------
C | kopilo, tux | main drive
D | kopilo, tux | cd drive

```
EDIT: I know you could do this via the folder permission, but the idea is to make it so anyone can use it, even someone who hasn't got a grasp of fstab.

---

### Post by beercz on 2006-10-26
> **ago said:**
> What about creating a Ubuntu-ZeroConf-HomeServer package as a spinf-off of edubuntu?
I think this is a superb idea!

Also include LAMP stuff as well perhaps?

---

### Post by fog on 2006-10-26
I like to see this in Ubuntu too

---

### Post by IYY on 2006-10-26
This should be a metapackage in the main repositories.

---

### Post by hkgonra on 2006-10-26
I LOVE the idea, looks very similar to what is being done by clarkconnect and SMEserver. 
Both good products but why not have one with an ubuntu base ?

---

### Post by ago on 2006-11-05
I submitted a spec

[https://wiki.ubuntu.com/ZeroConfServer](https://wiki.ubuntu.com/ZeroConfServer)

feel free to edit.

---

### Post by ago on 2007-01-08
Ok we have been beaten, but I told you so: 

**[size=5]Windows Home Server announced at CES[/size]**

A show of hands: Who here among us is storing all of their important data (media and otherwise) in a safe location where it&#8217;s constantly accessible, as well as backed up to prevent loss? Not a lot of hands here at the 10 HQ, and probably not many of the rest of you. Well thanks to CJ Saretto and the Windows Home Server team, that sort of digital responsibility is now much easier to live up to.

As a small, headless box that lives on your network and in your closet, a Windows Home Server can quickly grow the pool of storage from which all of your shared files for each of your users lives. The backup engine in Windows Home Server also silently backs up the entirety of each machine connected to it every night. And because the data is always online, using the built-in remote access abilities, you&#8217;ll also be able to access your data from any machine on the planet.

[http://on10.net/Blogs/jesse/windows-home-server-will-live-in-your-closet-simplify-your-life/](http://on10.net/Blogs/jesse/windows-home-server-will-live-in-your-closet-simplify-your-life/)

---

### Post by ButteBlues on 2007-01-08
> **ago said:**
> file server (indexed by tracker),

Why don't we use an indexer with some actual potential for growth and improvement, eh?

---

### Post by ago on 2007-01-08
[https://help.ubuntu.com/community/MetaTracker](https://help.ubuntu.com/community/MetaTracker)

---

### Post by ssam on 2007-01-08
dont forget web sharing.

linux make a good router, if you know how to set it up.

---

### Post by roderikk on 2007-01-08
I'd love to have any easy way to set up a box I can use as a main server in the house for filesharing, but also a media center. I don't know what for pc I would need at my television set but it would be great to set up such an architecture easily using mythtv backend and stuff.

Great idea!

---

### Post by bobbybobington on 2007-01-08
We absolutely need to have a home server. MS is coming out with their home server. This is a perfect opportunity to take them on.

---

### Post by ago on 2007-01-09
More details on Windows Home Server here: [http://arstechnica.com/news.ars/post/20070108-8573.html](http://arstechnica.com/news.ars/post/20070108-8573.html)

---

### Post by ago on 2007-01-12
A couple of interesting articles

1) Bubba a debian based low power server (hardware)
[http://www.linuxdevices.com/news/NS4105652894.html](http://www.linuxdevices.com/news/NS4105652894.html)

2) A nice streaming server
[http://www.slimdevices.com/su_downloads.html](http://www.slimdevices.com/su_downloads.html)

---

### Post by koenn on 2007-01-12
> **ago said:**
> 
"ZeroConf" in the sense that it uses ZeroConf and in the sense that it will work out of the box with reasonable settings..

This is the approach that Microsoft has been taking from the start, and they only way they have been able to pull it off was by
- turning everything on by default
- giving priority to "works out of the box" over security.

They have been flamed all over the place for producing inferior, resource hungry systems with terrible security because of these choices, and linux users have always pointed at the superior security and adequate use of resources of ther os of choice to make a case for linux over windows.

I think this is something to keep in mind, although, overall, this home server (& small business server ?) sounds like a good idea,

---

### Post by altonbr on 2007-06-29
Just to reverse link this thread and the new Ubuntu Home Server thread: [http://ubuntuforums.org/showthread.php?t=445675](http://ubuntuforums.org/showthread.php?t=445675)

[www.ubuntuhomeserver.org](www.ubuntuhomeserver.org)
[http://wiki.ubuntuhomeserver.org/](http://wiki.ubuntuhomeserver.org/)
[http://forums.ubuntuhomeserver.org/](http://forums.ubuntuhomeserver.org/)
[https://launchpad.net/uhs](https://launchpad.net/uhs)
#ubuntuhomeserver on irc.freenode.net:6667

---

### Post by lieuhon on 2009-08-17
I like to see this as well.  I was looking for something like this for a while.

---

