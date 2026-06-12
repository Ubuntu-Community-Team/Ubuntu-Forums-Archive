---
title: "Ubuntu 18.4 not connecting too repositerys and having trouble insalling xubuntu-core."
date: 2018-05-26
forum: Server Platforms
---

### Post by daniel228 on 2018-05-26
Hey Gyes,

I have done a full installation of Ubuntu 18.4 and ran "sudo apt-get update" along with "sudo apt-get upgrade" in order too fully update my system.

I also done a Ping of Googles servers to check I had internet connectivity and I do.

I have ran sudo apt-get install xubuntu-core with no luck as their is error messages being returned in the forum of; archives.ubuntu.

I have installed this on my rack and looking for a lightweight GUI for system management.

Would anyone be able too provide the full path of the installation for xubuntu-core and have I missed anything can you see. I also only installed 24 new packages as of today as this is a new release I know.

Thanks gyes in advance for your time.

---

### Post by Bashing-om on 2018-05-26
daniel228; Hello;

Maybe approaching this from the wrong direction.
In terminal do:
```

apt list xubuntu-core

```
Do you see it there in the software repository ?

Now look:
```

apt show xubuntu-core

```
and we see that the dependency is on a fully installed Xubuntu desktop system.

If it is your desire for a GUI on a server .. and xfce is your choice,  -AND- you are content to run X11 rather than wayland as the Desktop Environment may I suggest to run:
```

sudo apt install xorg
sudo apt install xfce4

```
to install xfce on your system.

[INDENT][INDENT]a process of learning
[/INDENT][/INDENT]

---

### Post by daniel228 on 2018-05-26
I think this could be a problem on my home network. I am having disconnections with several Client (Desktop) PC's, and I am not able too contact Ubuntu archives what so ever.

I get the error message, "failure in resolving: Archives.Ubuntu.com

I am able too to an update but not download anything and the same does apply with "sudo apt-get install xubuntu-desktop" and any other alternative I try.

I have tried editing etc/resolv.conf too use Googles name servers: 8.8.8.8 but the file is over written when I reboot. If I do not reboot then I still encounter the same problem in regards too being unable too contact Ubuntu Archives.

I am currently running PFSense on a dedicated server in bridged mode with my ISP Box and unsure if this is causing problems with the DNS requests but also unsure about any NAT Problems on my custom firewall. I do not have a 100% understanding of this and those but found other people with similar problems threw Google.

Thanks.

---

### Post by Bashing-om on 2018-05-26
daniel228; Humm ....

Behind a proxy ?
Sorry, I have not been there and do not know what to advise in that event.

[INDENT][INDENT]a know it all I am not
[/INDENT][/INDENT]

---

### Post by daniel228 on 2018-05-26
Bashing-om I have solved the issue.

I wanted too post back and let you know it was a DNS problem with my pfSense firewall and an internal issue. I had not configured it proper after I done a new install a few days ago and I'm not sure but I also had I.PVer: 6 Enabled and accepting traffic.

I have removed the I.P.Ver: 6 from my WAN Interfaces, and I have also added custom DNS Servers too my Addresses.

Thanks.

---

### Post by Bashing-om on 2018-05-26
daniel228; Hey, hey :)

You do good work - appreciate that you provided the resolution.

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

