---
title: "Create XAMPP Control Panel launcher on the Desktop"
date: 2016-05-17
forum: Tutorials
---

### Post by jcrcarmo on 2016-05-17
Hello everyone and greetings from Brazil!  Here's a little tutorial I've created to make a shortcut for XAMPP Control Panel on the Desktop.

To create a launcher on the Desktop: 
You need **gksu** so if you don't have it yet, run in terminal: 
> sudo apt-get install gksu 
 
Now let's create the shortcut: 
Run **gedit** (or any other text editor) and then enter the info below:

```

#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=/opt/lampp/htdocs/favicon.ico
Name[en_US]=XAMPP
Exec=gksu /opt/lampp/manager-linux-x64.run
Comment[en_US]=Start XAMPP Control Panel
Name=XAMPP
Comment=Start XAMPP Control Panel
Icon=/opt/lampp/htdocs/favicon.ico

```
 
Save the file on your Desktop as **Xampp.desktop** 
 
Once the shortcut is on the Desktop, right-click on it, go to Properties, Permissions tab, and check '**Allow executing file as program**'

That's it guys!  Have fun.  :)

JC

---

### Post by Pangestu_Apri_Seti on 2016-05-19
its not working on me, when i double click it, it open gedit again :confused: 
do i miss something?
im using the latest xampp 7.0.6

---

### Post by jcrcarmo on 2016-05-19
That's really weird...  It should work because it's exactly how I did on my system and it works perfectly.  Did you save the file as **xampp.desktop**  ?  And also you have to **allow it to run as a program**.  Follow all the steps above and it should work. :)

---

### Post by doninmedford on 2016-11-24
The instructions worked perfectly for me with just some minor changes because I am using Xubuntu. Thanks!

---

### Post by dreaddisk on 2016-12-19
Noob here, so I did everything on the instructions above. It worked. But what I can do with this right now? I can compile PHP files now?

---

### Post by ecktahab on 2017-06-06
Thanks is working perfectly n.n
This should be added by default by xampp

---

### Post by dnaldoog on 2018-05-07
Thanks for this!

This is my slightly modified version for Ubuntu 18.04.

[gksu]("https://askubuntu.com/questions/284306/why-is-gksu-no-longer-installed-by-default") is not part of **Ubuntu 18.04** as I found out and also adding *StartupWMClass=osxmanager *(See link below)  prevents the launcher adding a second window to the dock.

```
#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Type=Application
StartupWMClass=osxmanager
Terminal=false
Icon[en_US]=/opt/lampp/htdocs/favicon.ico
Name[en_US]=XAMPP
Exec=sudo -H /opt/lampp/manager-linux-x64.run
Comment[en_US]=Start XAMPP Control Panel
Name=XAMPP
Comment=Start XAMPP Control Panel
Icon=/opt/lampp/htdocs/favicon.ico
```

[https://askubuntu.com/questions/403766/duplicate-icons-for-manually-created-gnome-launcher-items](https://askubuntu.com/questions/403766/duplicate-icons-for-manually-created-gnome-launcher-items)

---

### Post by kaysar on 2018-06-23
Hi,
I use Lubuntu 18 and applied updated code but note working. It worked with gksu in previous version of lubuntu. What to do please suggest.

> **dnaldoog said:**
> Thanks for this!

This is my slightly modified version for Ubuntu 18.04.

[gksu]("https://askubuntu.com/questions/284306/why-is-gksu-no-longer-installed-by-default") is not part of **Ubuntu 18.04** as I found out and also adding *StartupWMClass=osxmanager *(See link below)  prevents the launcher adding a second window to the dock.

```
#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Type=Application
StartupWMClass=osxmanagerTerminal=false
Icon[en_US]=/opt/lampp/htdocs/favicon.ico
Name[en_US]=XAMPP
Exec=sudo -H /opt/lampp/manager-linux-x64.run
Comment[en_US]=Start XAMPP Control Panel
Name=XAMPP
Comment=Start XAMPP Control Panel
Icon=/opt/lampp/htdocs/favicon.ico
```

[https://askubuntu.com/questions/403766/duplicate-icons-for-manually-created-gnome-launcher-items](https://askubuntu.com/questions/403766/duplicate-icons-for-manually-created-gnome-launcher-items)

---

### Post by puyt on 2018-07-07
Hi,

I don't know if you've found a fix yet but in case you didn't... I got it working by replacing** `sudo -H`** with [B]`pkexec`

[/B]Thanks** @dnaldoog **for your config!

Btw my **`XAMPP.desktop`** looks like this:

```

#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Type=Application
StartupWMClass=osxmanager
Terminal=false
Icon[en_US]=/opt/lampp/htdocs/favicon.ico
Name[en_US]=XAMPP
Exec=pkexec /opt/lampp/manager-linux-x64.run
Comment[en_US]=Start XAMPP Control Panel
Name=XAMPP
Comment=Start XAMPP Control Panel
Icon=/opt/lampp/htdocs/favicon.ico

``` 

> **kaysar said:**
> Hi,
I use Lubuntu 18 and applied updated code but note working. It worked with gksu in previous version of lubuntu. What to do please suggest.

---

### Post by marcelobbt on 2018-11-19
I tried all the options above, but didn't work. I click on icon and nothing happens.

I use Ubuntu 18.04.1 LTS, GNOME 3.28.2

P.S. When I use Terminal, xampp works.

---

### Post by raorafay on 2019-06-21
> **puyt said:**
> Hi,

I don't know if you've found a fix yet but in case you didn't... I got it working by replacing** `sudo -H`** with [B]`pkexec`

[/B]Thanks** @dnaldoog **for your config!

Btw my **`XAMPP.desktop`** looks like this:

```

#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Type=Application
StartupWMClass=osxmanager
Terminal=false
Icon[en_US]=/opt/lampp/htdocs/favicon.ico
Name[en_US]=XAMPP
Exec=pkexec /opt/lampp/manager-linux-x64.run
Comment[en_US]=Start XAMPP Control Panel
Name=XAMPP
Comment=Start XAMPP Control Panel
Icon=/opt/lampp/htdocs/favicon.ico

```

I have got it working in my Ubuntu 18.04 LTS with unity desktop launcher. Please change Exec assignement with following:

```
Exec=sh -c "pkexec env DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY sudo /opt/lampp/manager-linux-x64.run"

```

The solution i found is in the link [here]("https://unix.stackexchange.com/questions/480744/xampp-launcher-does-not-open-window").

Hope it helps

---

### Post by isuru10 on 2019-06-23
I use Kubuntu 19.04 and I got it to work with following .desktop file

#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Type=Application
StartupWMClass=package
Terminal=false
Icon[en_US]=/opt/lampp/htdocs/favicon.ico
Name[en_US]=XAMPP
Exec=pkexec env DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY /opt/lampp/manager-linux-x64.run 
Comment[en_US]=Start XAMPP Control Panel
Name=XAMPP
Comment=Start XAMPP Control Panel
Icon=/opt/lampp/htdocs/favicon.ico

---

### Post by Seth-666 on 2020-06-01
hell , can anybody help me create the shutcute for Xampp ? i tried almost the hole google searched options ... 

i am using Ubuntu 20.04 last 
Is that different then the old versions od Ubuntu ? ... 

Please help

Thank You

---

