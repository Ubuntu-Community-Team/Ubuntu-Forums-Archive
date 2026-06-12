---
title: "Can't add a printer"
date: 2012-02-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by williammanda on 2012-02-23
I can't add a printer. Nothing is highlighted for me to select to add a printer.

---

### Post by cariboo on 2012-02-23
What type of printer are you trying to add? How is it connected?

---

### Post by williammanda on 2012-02-23
> **cariboo907 said:**
> What type of printer are you trying to add? How is it connected?

It's not that I can't add a specific printer I can't add at printer a all. The add printer button isn't highlighted so I can start the process. See attached photo.

---

### Post by rgerhardt on 2012-02-23
If you already installed the package cups, try install cups-pk-helper.

---

### Post by williammanda on 2012-02-24
> **rgerhardt said:**
> If you already installed the package cups, try install cups-pk-helper.

Is the cups package not installed as a part of the precise package or are you offering a fix?

---

### Post by williammanda on 2012-02-24
I re-installed from the daily builds and have the same issue

---

### Post by cariboo on 2012-02-24
Open a terminal and try:

```
sudo system-config-printer
```

---

### Post by effenberg0x0 on 2012-02-24
Working fine here for two HP printers: One local (USB) HP LaserJet and one remote (SMB) HP Multifunctional Deskjet.

[ATTACH]213228[/ATTACH]

Regards,
Effenberg

---

### Post by Tjawi on 2012-02-24
Thank you for the answer!

I worked (brought up a functional ADD PRINTER wizard after i did so on the terminal).

Tjawi

---

### Post by williammanda on 2012-02-25
> **cariboo907 said:**
> Open a terminal and try:

```
sudo system-config-printer
```

This worked! But why doesn't the intended way work...using systems settings>hardware-printers?
Now that I have a printer setup...the systems settings>hardware-printers, seems to be working (it reflects the printer I just installed ).

---

### Post by jbicha on 2012-02-25
In GNOME Shell and GNOME Classic, the printer panel embedded in System Settings is used. If you'd use Unity, you'd get system-config-printer by default when you click Printers.

---

### Post by williammanda on 2012-02-25
> **jbicha said:**
> In GNOME Shell and GNOME Classic, the printer panel embedded in System Settings is used. If you'd use Unity, you'd get system-config-printer by default when you click Printers.

I'm not sure I have made my point clear because there have been several work-a-rounds but the real issue is that when I'm presented with the "printers" located under system settings, I'm not allowed to add a printer. The add button is not highlighted so that it can be selected to start the "add a printer" process. It seems to me that this could be a bug or a isolated problem in my installation. Previously with 11.10 this wasn't an issue and up until a couple of days ago, I hadn't explored adding a printer.

---

### Post by effenberg0x0 on 2012-02-25
Out of curiosity: When you open a browser and point it to [http://localhost:631](http://localhost:631), do you see cups web interface and can you manage (add, remove, setup) printers?

Regards,
Effenberg

---

### Post by williammanda on 2012-02-25
> **effenberg0x0 said:**
> Out of curiosity: When you open a browser and point it to [http://localhost:631](http://localhost:631), do you see cups web interface and can you manage (add, remove, setup) printers?

Regards,
Effenberg

This is what I get (see attached photo).

---

### Post by williammanda on 2012-02-25
Also I wanted to note that I just completed another install and got the same result concerning the printer.

---

### Post by jbicha on 2012-02-25
Which version of gnome-shell? apt-cache policy gnome-shell will give you the answer.

Do you do anything special like not installing recommends? cups-pk-helper is a recommends of gnome-shell.

---

### Post by mdurham on 2012-02-25
Whilst on this topic, how does one **remove** a printer?
Cheers

---

### Post by williammanda on 2012-02-25
> **jbicha said:**
> Which version of gnome-shell? apt-cache policy gnome-shell will give you the answer.

Do you do anything special like not installing recommends? cups-pk-helper is a recommends of gnome-shell.

william@CI5:~$ apt-cache policy gnome-shell
gnome-shell:
  Installed: (none)
  Candidate: 3.2.2.1-0ubuntu1
  Version table:
     3.2.2.1-0ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe amd64 Packages

I'm currently playing with cairo dock. Since it uses gnome classic, I install alacarte so I can adjust the menu items. This could be where the problem comes in. Is there another way to get the alacarte "main menu" function without causing any problems? Or is there another issue?
Thanks

---

### Post by cariboo on 2012-02-25
> **mdurham said:**
> Whilst on this topic, how does one **remove** a printer?
Cheers

Go to System Settings->Printers, right click the printer you want to remove and click delete.

---

### Post by mdurham on 2012-02-26
> **cariboo907 said:**
> Go to System Settings->Printers, right click the printer you want to remove and click delete.
I have 2 printers installed, right clicking on either does nothing

---

### Post by jbicha on 2012-02-26
Once again, there's a big difference between the Printers panel in Unity & the one in GNOME Shell/GNOME Classic. In GNOME, you should just be able to click the **-** button to remove a printer.

---

### Post by kurt18947 on 2012-02-26
I've found a workaround in gnome-shell to get the 'old style' printer add/configuration app back but it could be better integrated.  I found a means to create a launcher on the Desktop:

```
gnome-desktop-item-edit ~/Desktop/ --create-new
```[INDENT]This came from 
[http://ubuntugeek.com/how-to-create-desktop-launchers-in](http://ubuntugeek.com/how-to-create-desktop-launchers-in) ubuntu-11-10oneiric.html
You may have to add the following:[/INDENT][INDENT]```
sudo apt-get-install --no-install-recommends gnome-panel

```
I did not add this on 12.04 and the create launcher app opened and worked.
[/INDENT]A 'Create Launcher' app opens.  Name it what you like then on the command line:

```
system-config-printer
```It might be nice to group this with other app launchers so it's available to all users authorized to add printers without creating a launcher for each user.  I don't know 'where they live' so to speak.

---

### Post by williammanda on 2012-02-26
> **williammanda said:**
> william@CI5:~$ apt-cache policy gnome-shell
gnome-shell:
  Installed: (none)
  Candidate: 3.2.2.1-0ubuntu1
  Version table:
     3.2.2.1-0ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe amd64 Packages

I'm currently playing with cairo dock. Since it uses gnome classic, I install alacarte so I can adjust the menu items. This could be where the problem comes in. Is there another way to get the alacarte "main menu" function without causing any problems? Or is there another issue?
Thanks

After doing another install and checking the "add a printer" before adding the alacarte. That was the problem that caused the issue.
Thanks for your help.

---

