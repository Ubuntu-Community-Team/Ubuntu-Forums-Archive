---
title: "Sudo password not working after installing Gnome"
date: 2011-03-10
forum: Server Platforms
---

### Post by GazMathias on 2011-03-10
Hi,
 
I have installed Ubuntu Server 10.10 in Virtual Box in order to evaluate it for a project.
 
I have installed Gnome and can log in fine using my password. However, whenever I am prompted for my password when doing anything SUDO I am told my password is incorrect, starting Synaptic, for example.
 
Anyone have any ideas?
 
Gaz.

---

### Post by jmacgowan on 2011-03-10
What happens when you use sudo in a terminal?

---

### Post by GazMathias on 2011-03-10
Hi,

I have installed Ubuntu Server 10.10 to evaluate it for a project.

I have installed Gnome (via sudo apt-get install ubuntu-desktop).

I can log in using my password but whenever I try to do anything that prompts my for my password (synaptic, etc) I am told my password is incorrect which it definitely isn't.

Anyone have any ideas?

Gaz

P.S I have installed Gnome to ironically prove to my boss that it is friendly enough for non technical types to perform admin tasks!

---

### Post by jmacgowan on 2011-03-10
What was wrong with your post here?
[http://ubuntuforums.org/showthread.php?t=1704250](http://ubuntuforums.org/showthread.php?t=1704250)
 
Anyway, what happens when you run a SUDO command in a terminal?
 
Also, I would look into installing Webmin for adminstrative tasks.  It's absolutely wonderful.  More info here:
[http://www.webmin.com/](http://www.webmin.com/)
 
and here are some directions for installing with apt-get:
[http://www.webmin.com/deb.html](http://www.webmin.com/deb.html)

---

### Post by matt_symes on 2011-03-10
Hi

Open a terminal and type (post results back)

```
groups
```

Kind regards

---

### Post by arrrghhh on 2011-03-10
Why did you install GNOME on ubuntu-server?

Just install ubuntu-desktop if you want GNOME - not the package, the actual iso.  server is meant to be lean-and-mean, you basically made it more like the desktop edition than the server edition by installing GNOME :p.

---

### Post by CharlesA on 2011-03-10
I merged your two threads together.

---

### Post by GazMathias on 2011-03-11
Hi everybody,

Apologies for multiple posting this thread. I could't find the first one and doubted i'd actually posted it. Admins please feel free to delete.

---

### Post by GazMathias on 2011-03-11
> **arrrghhh said:**
> Why did you install GNOME on ubuntu-server?

Just install ubuntu-desktop if you want GNOME - not the package, the actual iso.  server is meant to be lean-and-mean, you basically made it more like the desktop edition than the server edition by installing GNOME :p.

I have to prove to my boss that it is friendly enough for non admin types to do simple things. They are currently used to performing tasks such as VNC to win2003 servers to restart services by clicking batchfiles, closing and restarting Access databases running in loops, swapping backup disks, etc.

---

### Post by GazMathias on 2011-03-11
> **matt_symes said:**
> Hi

Open a terminal and type (post results back)

```
groups
```

Kind regards

Hi, groups reveals this:

adm dialout cdrom plugdev lpadmin sambashare admin

Thanks for your time.

---

### Post by GazMathias on 2011-03-11
> **jmacgowan said:**
> What happens when you use sudo in a terminal?

Sudo in terminal is fine.

Thanks.

---

### Post by CharlesA on 2011-03-11
What happens if you start synaptic from the system menu?

---

### Post by arrrghhh on 2011-03-11
> **GazMathias said:**
> I have to prove to my boss that it is friendly enough for non admin types to do simple things. They are currently used to performing tasks such as VNC to win2003 servers to restart services by clicking batchfiles, closing and restarting Access databases running in loops, swapping backup disks, etc.

Still don't see a reason for ubuntu-server... desktop you can run all the same services on, and you don't have to try and shoehorn X on there.

To each their own I guess.

---

### Post by matt_symes on 2011-03-11
Hi

Try adding yourself to the sudo group.

Kind regards

---

### Post by GazMathias on 2011-03-14
Thanks everybody. This problem was solved by using the command "gksu-properties", and selecting sudo as the authentication method.

---

