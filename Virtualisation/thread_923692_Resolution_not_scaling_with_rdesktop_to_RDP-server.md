---
title: "Resolution not scaling with rdesktop to RDP-server of VirtualBox"
date: 2008-09-18
forum: Virtualisation
---

### Post by markba on 2008-09-18
I'm connecting with rdesktop through the builtin RDP-server in VirtualBox to a Windows session. Although this succeeds, the client-side resolution can *not* be controlled by the rdp-client (rdesktop) through several commandline options. The actual resolution is the resolution on the server it self (this is the same if the session is displayed locally by the vbox manager). The only way to control the client-side resolution is to change the resolution in the session it self (right click on Desktop, Properties, etc.).

Normally RDP should work like this: the client requests for a certain screen resolution (fullscreen or defined width/height), the RDP-server responds by actually change the resoluton server-side. It seems that my problem has to do with the fact that the vbox RDP-server does not respond to the requested resolution by the client.

The following combinations were tried:
1. Ubuntu/rdesktop -> vbox RDP-server: no resolution scaling
2. Ubuntu/tsclient -> vbox RDP-server: no resolution scaling
3. Windows/mstsc -> vbox RDP-server: resolution scaling works
4. Ubuntu/rdesktop -> Windowx XP RDP-server: resolution scaling works

At first, I was thinking it was a RDP-client problem, because both rdesktop and tsclient (combinations 1+2) did not do the resolution scaling. This seems to be confirmed when I connected with MS Terminal Server Client (standard RDP-client in Windows) from a Windows XP installation to the vbox RDP-server (combination 3): that client did change the client resolution.

Thinking it was clearly a client problem, I then did combination 4, rdesktop to a Windows XP RDP-server and rdesktop is actually capable of resolution scaling, because it worked (unexpected though).

My conclusion so far: it seems like *only* the specific combination from rdesktop/tsclient to vbox RDP-server does not do resolution scaling, all other combinations work (tried also gnome-rdp client, but as this is using rdesktop on the background, it gives the same result).

This is the error/warning when I try to connect from rdesktop to vbox RDP-server:

```
user@lin12:~$ rdesktop 192.168.0.101:3390 -g 1024x700
WARNING: Remote desktop changed from 1024x700 to 800x600.
```

It's obvious it's changing the defined resolution (1024x700) to the resolution server side (800x600). When I connect with rdesktop to a Windows RDP-server, such a warning does *not* popup.

Does anybody have a clue why rdesktop is not able to change to resolution of the vbox RDP-server session?

---

### Post by markba on 2008-09-23
OK, 101 views, no reaction :-(

Just let me rephrase the question: is there anybody out there using a Ubuntu RDP-viewer (be it tsclient, rdesktop, etc.) to connect to the VirtualBox RDP-server? If so, what are your experiences?

---

### Post by Epeli on 2008-09-23
> **markba said:**
> OK, 101 views, no reaction :-(

Just let me rephrase the question: is there anybody out there using a Ubuntu RDP-viewer (be it tsclient, rdesktop, etc.) to connect to the VirtualBox RDP-server? If so, what are your experiences?
I am and I'm having exactly same the problem.

---

### Post by markba on 2008-09-23
Nice to know I'm are not alone... :)

I've made a post to the vbox forum, hoping someone has a clue:
[http://forums.virtualbox.org/viewtopic.php?p=39075#39075](http://forums.virtualbox.org/viewtopic.php?p=39075#39075)

---

### Post by Jose Catre-Vandis on 2008-11-07
It worked fine up to and including hardy, but with intrepid (using exactly the same parameters) I get the same resolution as my client desktop. Can change in right click > properties > settings of the vm, but the desktop window remains at the client resolution size. My rdesktop command is:
```
rdesktop -a 16 -g 100%+0+0 xx.xx.xx.14:3389
```
and my setting on the server side in the Xvnc file server args asks for -geometry 1152x864.

I have now changed my -g setting to 90%, and my vm resolution to 1152x864 and it fits OK.
```
rdesktop -a 16 -g 90%+0+0 xx.xx.xx.14:3389
```

---

### Post by Epeli on 2008-11-12
You can do a workaround on host-machine while your vm is running:
```

$ VBoxManage controlvm <your vm> setvideomodehint 1024 700 32

```And resolution should change to 1024x700

---

### Post by markba on 2008-11-12
> **Jose Catre-Vandis said:**
> I have now changed my -g setting to 90%, and my vm resolution to 1152x864 and it fits OK.
```
rdesktop -a 16 -g 90%+0+0 xx.xx.xx.14:3389
```

I'll try this method, seems hopefull. But in contrast to you (in Hardy it worked for you), scaling has never worked for me, not in Hardy nor in Intrepid.

[QUOTE=Epeli]You can do a workaround on host-machine while your vm is running:
```
$ VBoxManage controlvm <your vm> setvideomodehint 1024 700 32
```
And resolution should change to 1024x700[/QUOTE]

This is not workable for me, because I do not know in advance which resolution the client is using (VM's are running on a different machine/server, seperated from the client). Nevertheless, maybe in another situation this might me usesfull.

---

### Post by Epeli on 2008-11-12
> **markba said:**
> 
This is not workable for me, because I do not know in advance which resolution the client is using (VM's are running on a different machine/server, seperated from the client)..
I have also the same situation. You don't need know it in advance. Just run the command via ssh when you know it. Bit inconvenient, but it works.

---

### Post by markba on 2008-11-12
> **Epeli said:**
> I have also the same situation. You don't need know it in advance. Just run the command via ssh when you know it. Bit inconvenient, but it works.

OK, now I see. The resolution scaling can be changed on-the-fly, not only at startup (which I assumed), even if the session is running. But then there is the problem that the client should have direct contact with the VBox server, something I'm certainly not preferring. Nevertheless, I'll try this option also.

---

### Post by markba on 2008-11-12
The alternative rdesktop parameter '-g 90%+0+0' did not work for me. So I tried the second option, setting the videohint with VBoxManage: that worked. As this is somewhat impractictable, I'm thinking of setting the videohint by VBoxTool (configurable).

This is a workaround, and not quite what I want: rdesktop should be able to maximize and the desktop should scale accordingly, dynamically; other tools can do this, so why can't VirtualBox and rdesktop achieve the same?

Nevertheless, thanks all for thinking with me.

---

### Post by lumbricus on 2011-05-03
Thanks to markba's investigations I tried to use freerdp - partly with success: 

[SIZE=3]**WORKAROUND:**[/SIZE]
Use freerdp ([http://www.freerdp.com/](http://www.freerdp.com/)) instead of rdesktop. In 11.04 you can just install the package freerdp-x11. Otherwise download the latest tarball and compile it:
./autogen.sh
 ./configure
 make

Afterwards run it with your desired resolution:
xfreerdp -g 800x600 192.168.0.12

Also fullscreen is working: xfreerdp -f 192.168.0.12
(CTRL+ALT+ENTER to leave it again)


It's not excactly what I wanted, but atleast now I can make different launchers for the users to allow them to open the RDP viewer in different sizes. Using the commandline option for VBoxManage wouldn't be an easy option for me because the virtualbox machine is running as a different user. There might be a solution messing around with the sbit or so to allow normal users to run the VBoxManage command as different user, but freerdp was definitly easier and causing less troubles.


**Whats not working:**
Unfortunatly dynamically resizing the window (as you can do with Windows' RDP-Client) is not working either, it is being discussed already on the developers' maling list:
[http://www.mail-archive.com/freerdp-devel@lists.sourceforge.net/msg00756.html](http://www.mail-archive.com/freerdp-devel@lists.sourceforge.net/msg00756.html)


The packages shipped with Lucid are not working at all. I couldn't manage to get a working RDP connection, don't know why. In 11.04 and by using the compiled tar-balls from the website everything seems fine.

---

