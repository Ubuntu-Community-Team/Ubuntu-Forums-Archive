---
title: "vmware 64bit no server console"
date: 2007-12-23
forum: Virtualisation
---

### Post by falieson on 2007-12-23
I just instaled vmware server x86_64 (followin the great tutorial in the tutorials section) but "VMware Server Console" is not available under applications -> System Tools . There is no such 'system tools' folder under the applications menu. 

going to the terminal:
#vmware
Try 'man vmware' for more information


:-/ How do I get a gui interface so I can setup my vmware?

I installed ubuntu a couple days ago on the latest 7.X version.

---

### Post by fjgaude on 2007-12-23
Right click on Applications, then Edit Menus. From there you can activate the Systems Tools menu.

---

### Post by scxtt on 2007-12-23
what does **whereis vmware** return?
```
:> whereis vmware
vmware: /usr/bin/vmware /etc/vmware /usr/lib/vmware /usr/lib64/vmware /usr/share/man/man4/vmware.4.gz /usr/share/man/man1/vmware.1.gz
```

---

### Post by fjgaude on 2007-12-23
Usually in /var/lib/vmware

You have to install it first.

---

### Post by falieson on 2007-12-27
I returned the same result for 
:> whereis vmware
```

:> whereis vmware
vmware: /usr/bin/vmware /etc/vmware /usr/lib/vmware /usr/lib64/vmware /usr/share/man/man4/vmware.4.gz /usr/share/man/man1/vmware.1.gz
```


Is there a command just to start the server console?

---

### Post by fjgaude on 2007-12-27
For me it is simply "vmware". I have an icon in the Applications/System Tools menu in Gnome. It got put there automatically when I installed the Server.

---

### Post by skroops on 2007-12-27
I'm having the same issue, the vmware command just returns "Try 'man vmware" for more information"

---

### Post by skroops on 2007-12-27
Is there any chance you are using the vmware server beta 2?  that's why I was having the problem, if so take a look at this page for some help: [http://ubuntu-tutorials.com/2007/11/19/install-vmware-server-20-beta-on-ubuntu-710-gutsy/]("http://ubuntu-tutorials.com/2007/11/19/install-vmware-server-20-beta-on-ubuntu-710-gutsy/")

---

### Post by sf_basilix on 2007-12-29
I am getting the same problem as those above:

I installed the latest version of Ubuntu Desktop (just downloaded two days ago), and then installed VMWare server, which was successful, but when I run vmware from the command line as such:

$ vmware
or
$ sudo vmware

all I get is this:

"Try 'man vmware' for more information"

I cannot find the icon for VMWare in the System Tools menu, because my installation (default for everything) does not show a System Tools menu (version is the latest Ubuntu Desktop). I even patched the entire Ubuntu system, but cannot find the System Tools menu under Applications.

Is there an option or another way to pull up the vmware console so I can install windows on vmware?

Also - how can I show the System Tools menu in my Ubuntu Desktop version?

Thanks in advance!

---

### Post by scxtt on 2007-12-29
what happens if you type **/usr/bin/vmware** into a terminal window? (assuming **whereis vmware** returns something sensible).

---

### Post by sf_basilix on 2007-12-30
as stated in my last post, running vmware in the terminal returns the error: "Try 'man vmware' for more information" and then gives me the command prompt again.

But in any event, I seemed to have gotten this to work - unfortunately it's not as nice as I would have liked it to be, but I guess this will have to do for now as "free" software..... :P

Apparently, because I was using the 64 bit version of Ubuntu, VMWare does not ship (or compile) a 64bit version of it's GUI - they only have a 32 bit version which installs in the sub-menus.  I did come across another blog which illustrated the files needed to install 32 bit libraries to get it to run, but that just seemed silly once I found out the other way.

So, instead of typing vmware, you would just open a browser and put in [http://localhost](http://localhost) (you may need to add a port at the end, if needed - this is specified during the install, if the port is anything other than 80).  Once you connect locally, you will need to login as root.  If you do not have a password set for root, you will need to change it through the command line before proceeding.  Then after logging in, you'll need to install a firefox plugin - which a link is available through the web-gui.

Not as nice as having a console, but it seems to work about the same way.  The only thing I haven't been able to do is run full-screen with the hidden-menu bar at the top - like the older server had.  I really miss that!

---

### Post by scxtt on 2007-12-30
that seems like vmware v2.0 (BETA!) ... i'm using 1.0.4 on a 64-bit system and i don't have any of your issues ... i have installed v2.0 in windows, didn't care for it - but i reserve any type of "final" judgment.

v2.0 is strictly web-based ...

as far as using "vmware" in a 64-bit OS ... you do have to have the **ia32-libs** installed ...

---

