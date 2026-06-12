---
title: "USP user not working as it should"
date: 2007-06-05
forum: Ubuntu System Panel
---

### Post by Death_Sargent on 2007-06-05
i don't get any of the default information just a picture and the word "user" next to it. 

how do i fix this?

---

### Post by Malac on 2007-06-05
> **Death_Sargent said:**
> i don't get any of the default information just a picture and the word "user" next to it. 

how do i fix this?
please post the output of ```
who -s
```

---

### Post by Death_Sargent on 2007-06-05
```
pete     :0           2007-06-05 16:01
pete     pts/0        2007-06-05 19:14 (:1.0)

```

---

### Post by Malac on 2007-06-06
Thanks Death_Sargeant,
That looks fine.
Next stage is to try removing USP and then re-add it to the panel.
Failing that after removing USP from the panel try posting the output of ```
 usp run-in-window
``` and/or ```
usp run-in-window -v
```

Thanks.

---

### Post by Death_Sargent on 2007-06-06
```
Warning! - Icon for item not found!
Warning! - Icon for item not found!
Dir exist
Dir exist
Dir exist
Application added - /home/pete/.usp/applications/synaptic.desktop
Application added - /home/pete/.usp/applications/firefox.desktop
Application added - /home/pete/.usp/applications/frostwire.desktop
Separator added
Application added - /home/pete/.usp/applications/skype.desktop
Application added - /home/pete/.usp/applications/pidgin.desktop
Application added - /home/pete/.usp/applications/evolution.desktop
Separator added
Application added - /home/pete/.usp/applications/ooo-writer.desktop
Separator added
Application added - /home/pete/.usp/applications/freeciv.desktop
Application added - /home/pete/.usp/applications/amarok.desktop
Application added - /home/pete/.usp/applications/totem.desktop
Application added - /home/pete/.usp/applications/vlc.desktop
Place added - /home/pete/.usp/places/nautilus-home.desktop
Place added - /home/pete/.usp/places/-home-pete-Desktop.desktop
Place added - /home/pete/.usp/places/nautilus-computer.desktop
Place added - /home/pete/.usp/places/network-scheme.desktop
Place added - /home/pete/.usp/places/file:---extdrive.desktop
Place added - /home/pete/.usp/places/file:---home-pete-Pictures.desktop
Place added - /home/pete/.usp/places/file:---home-pete-Downlaods.desktop
Place added - /home/pete/.usp/places/file:---home-pete-Downloads.desktop
Place added - /home/pete/.usp/places/file:---home-pete-Torrents.desktop
Place added - /home/pete/.usp/places/file:---home-pete-Documents.desktop
Place added - /home/pete/.usp/places/file:---home-pete-Music.desktop
Place added - /home/pete/.usp/places/file:---home-pete-Shared.desktop
RuntimeError: called outside of a mainloop
Static User Image Used

```

for some reason the second command did not work

---

### Post by Death_Sargent on 2007-06-11
**push**

---

### Post by Malac on 2007-06-12
> **Death_Sargent said:**
> for some reason the second command did not work
This probably means you are not running the latest SVN copy it would be worth you updating. This second command should give a more **v**erbose output i.e. it should print out more detailed info on where the modules are failing and what they are using as "raw" data.
Certainly for uspuser using the -v option you should see something like this in the output:
```
Output User Array
[COLOR=DimGray]*username*[/COLOR]     :0           2007-06-12 10:06[COLOR=DimGray][I]
username[/I][/COLOR]     pts/0        2007-06-12 10:20 (:0.0)
```

---

