---
title: "An unresolvable problem occurred while..."
date: 2012-04-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Libbard on 2012-04-02
Hey.. I have been try yesterday to install user theme extension and with it I have visit many site and many method to install it... after that visit update manager and click on some old source from 11.10 like caffine and Vlc.. etc

so I don't know What exactly I do before this happens except that When I click to enable the source I disable the new source I add today and within 10 minute I add one of them again through terminal.. it was 

[PHP]ppa:ferramroberto/gnome3[/PHP]and then When I heard about beta 2 I go to update manager to update and bump.. the problem came.

this message came from update manager

> An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/ferramroberto-gnome3-precise.list'and this when make update command in terminal "sudo apt-get update"

> E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/ferramroberto-gnome3-precise.list
E: The list of sources could not be read

and in Synaptic the error is

> E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/ferramroberto-gnome3-precise.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I try some solution before writing here like 

[PHP]sudo rm -vf /var/lib/apt/lists/*[/PHP]and

[PHP]sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-RENAMED sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status sudo apt-get update && sudo apt-get upgrade # or sudo apt-get dist-upgrade if no dependency issues
and nothing solve my problem[/PHP]I even clean every thing in source.list and again nothing change

I was trying to delete the ferramroberto-gnome3-precise.list from sources.list.d and even with terminal and root I can't


any help!

Thank you before anything for read and if you try for your trying :)

Regards,

Fahad.

---

### Post by plucky on 2012-04-02
> E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/ferramroberto-gnome3-precise.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report. 

Post the output from a terminal for ```
cat /etc/apt/sources.list.d/ferramroberto-gnome3-precise.list
```

You have to correct the content of the file.

Good luck

---

### Post by Libbard on 2012-04-02
> deb [http://ppa.launchpad.net/ferramroberto/gnome3/ubuntu](http://ppa.launchpad.net/ferramroberto/gnome3/ubuntu) precise main
deb-src [http://ppa.launchpad.net/ferramroberto/gnome3/ubuntu](http://ppa.launchpad.net/ferramroberto/gnome3/ubuntu) precise main
ain
ain


How can I correct it?!

:)

---

### Post by Libbard on 2012-04-02
Don't worry I understand your saying and try to Edit the

> /etc/apt/sources.list.d/ferramroberto-gnome3-precise.list

with this command

> sudo gedit /etc/apt/sources.list.d/ferramroberto-gnome3-precise.list

and this remove the ain in line 3 and 4 and then save it and run

> sudo apt-get update

and again every thing is just fain :)

Thank you :)

---

