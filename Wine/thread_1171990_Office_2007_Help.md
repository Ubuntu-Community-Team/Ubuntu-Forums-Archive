---
title: "Office 2007 Help"
date: 2009-05-27
forum: Wine
---

### Post by theiLLziLLa on 2009-05-27
I know there are a thousand topics on this but I need a little bit of help please.... So I installed the older version of wine and it seems like Office installed properly but when I click on the word icon in the folder, nothing happens. The hourglass comes up for a few seconds and then nothing.

any help is appreciated :)

---

### Post by NightMKoder on 2009-05-28
Did you install in a bottle (used WINEPREFIX)?

If so, wine tends to be (kinda) stupid about that and makes the wrong shortcuts:
```

sed -i.bak "s#/home/$USER/.wine#PUT YOUR PREFIX HERE#" ~/.local/share/applications/wine-*Microsoft\ Office*.desktop

```

So for example, I used WINEPREFIX=/home/mike/.wine_bottles/office2007 , so I used this command:

```

sed -i.bak "s#/home/$USER/.wine#/home/mike/.wine_bottles/office2007#" ~/.local/share/applications/wine-*Microsoft\ Office*.desktop

```

Now, if this is not the case, try taking the shortcut properties and sticking the command into a terminal. Then post the output here. The command will look something like:
```

env WINEPREFIX="/home/$USER/.wine" wine "C:\\Program Files\\Microsoft Office\\Office12\\WINWORD.EXE"

```

---

### Post by jhoeijao on 2009-05-30
> **theiLLziLLa said:**
> I know there are a thousand topics on this but I need a little bit of help please.... So I installed the older version of wine and it seems like Office installed properly but when I click on the word icon in the folder, nothing happens. The hourglass comes up for a few seconds and then nothing.

any help is appreciated :)

Give this a try [http://ubuntuforums.org/showthread.php?t=1173365&highlight=microsoft](http://ubuntuforums.org/showthread.php?t=1173365&highlight=microsoft)

---

