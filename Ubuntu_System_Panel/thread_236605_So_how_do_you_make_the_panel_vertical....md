---
title: "So how do you make the panel vertical...???"
date: 2006-08-15
forum: Ubuntu System Panel
---

### Post by jason.b.c on 2006-08-15
I've been wondering how people have been making the ubuntu panel vertical...

Like an MS Windows start menu , How do i do it..??? :confused:

---

### Post by moephan on 2006-08-15
Jason,

Assuming you are using GNOME, you right click on the panel you want to move, choose properties, and then set "Orientation" to left or right. I think that's what you are asking about. HTH.

Cheers, Rick

---

### Post by Tom Brokaw on 2006-08-15
Or just right click and select new panel, and have one or two of each.

---

### Post by jason.b.c on 2006-08-15
Well i'm sure it installed , what's the terminal command to launch it..??

---

### Post by jason.b.c on 2006-08-15
> jason@Hp-Vectra-VL:~$ sudo dpkg -i /tmp/fr-seoAGq/usp_0.41-1_all.deb
(Reading database ... 60044 files and directories currently installed.)
Preparing to replace usp 0.41-1 (using .../fr-seoAGq/usp_0.41-1_all.deb) ...
Unpacking replacement usp ...
Setting up usp (0.41-1) ...
jason@Hp-Vectra-VL:~$ 



I did install , right..???   So where's the launcher..???

---

### Post by nomorewindozeforme on 2006-08-16
Right click your panel, click "add to panel" and drag USP onto your panel

enjoy

:D

---

### Post by jason.b.c on 2006-08-19
I'm still curious about something..

What is the terminal command for the **U.S.P**   ..??

I want to make a desktop shortcut to it and **"then"** drag it down to my taskbar...So that way i think i can have a custom icon for it...

---

### Post by Fass on 2006-08-19
```
$ which usp
/usr/bin/usp
```

---

### Post by jason.b.c on 2006-08-19
> **Fass said:**
> ```
$ which usp
/usr/bin/usp
```

```
jason@Hp-Vectra-VL:~$ $ which usp
bash: $: command not found
jason@Hp-Vectra-VL:~$ $ which usp
bash: $: command not found
jason@Hp-Vectra-VL:~$ /usr/bin/usp



```

I don't think that was it...:-\"

---

### Post by chanders on 2006-08-19
Jason B.C, USP is an applet. You cannot make a launcher for it. You have to right click on the panel to add it to the panel.

There is a howto in these forums telling you how to change the icon it uses..

---

### Post by Fass on 2006-08-19
> **jason.b.c said:**
> I don't think that was it...:-\"

"which" is a command that tells you where to find an executable. You're not supposed to actually insert "which" to start an app, and you're most certainly not supposed to include the "$" prompt I used to indicate that this is done in a terminal.

```
man which
```

In any case, as was previously stated, you can't create a launcher for usp.

---

