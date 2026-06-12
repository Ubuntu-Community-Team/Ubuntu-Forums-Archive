---
title: "Strange bugs associated with using qemu/kvm"
date: 2016-05-11
forum: Virtualisation
---

### Post by hermes5 on 2016-05-11
Hi everyone. I recently had a scare with weird bash entries/firefox behaving strangely. I Posted it here; [http://ubuntuforums.org/showthread.php?t=2322454](http://ubuntuforums.org/showthread.php?t=2322454)

One of the problems mentioned in that thread was firefox not responding to the keyboard strokes I was inputing. I thought it was something sinister, so I decided to reinstall and upgraded to 16.04 while I was at it. But the problem seems to be back. However, I now realise it happens whenever I have my windows guest running on qemu/kvm is up and running. So basically, whenever I run qemu/kvm, firefox on my linux host stops receiving keystrokes. However the rest of the linux system is fine, I can type in to word docs, into the search bar etc. Another strange bug, whenever I press the key 'Q', my activities bar pops up. 

I have no idea what is happening, but It is very annoying because I use a dual screen setup, windows on the big screen for CAD programs and linux for my browsing etc. I also have to shutdown after I close the windows guest in order to fix the problem. It's a difficult problem to search for, and google returned no answers =/ The inner workings of how windows talks to the kernel is far too advanced for me... So I'm not quite sure how I am supposed to troubleshoot something like this.

Any advice or magic bullets would be very much appreciated.

---

### Post by KillerKelvUK on 2016-05-11
Hey, how do you access your windows guest i.e. VNC, SPICE, pci passthru of your GFX card?  Assuming its VNC or Spice which client do you use virt-manager or Remmina etc?  From your post it doesn't read like you are passing through a USB keyboard & mouse but just checking?

---

### Post by hermes5 on 2016-05-11
I use spice as the display and for the video adapter, using QXL as the model. Not doing a passthrough, and using virt-manager as the client. I'm using my macbook pro, so I use a usb connected mouse on the host and use spice to avoid locking in the mouse on the guest. Using the Virtio drivers where applicable.

---

### Post by KillerKelvUK on 2016-05-11
Okay couple of things you could try to see if they help/hinder/make no difference.  There is a keyboard layout option for the SPICE protocol in the virt-manager configuration for your guest, have you set this?

Also I've previously had issues with the IBUS input protocol, disabling this via the System Settings --> Language Support --> Keyboard Input Method System --> set this to none.  There are a few posts about IBus and Firefox so I suspect this maybe your issue... [https://bbs.archlinux.org/viewtopic.php?id=189990](https://bbs.archlinux.org/viewtopic.php?id=189990)

---

### Post by hermes5 on 2016-05-11
Ahhh thanks for the reply Kelv, but it appears to not be induced with virt-manager use. I just woke my computer from rest and it was the same problem I was having before the reinstall. Does someone know which subforum I could move this thread to? I'm not sure it belongs in this one anymore.

So when I cannot type into firefox at all, the host still recognises typing. Except for when I press 'Q' which brings up the activities bar, and when I press the 'S' key, which does nothing. I went in to terminal after looking through the thread you linked Kelv, and this similar thing popped up on my terminal

> im@vulcan2:~$ 
::1              ff02::1          ip6-allrouters   ip6-loopback     vulcan2
fe00::0          ff02::2          ip6-localhost    ip6-mcastprefix  
ff00::0          ip6-allnodes     ip6-localnet     localhost        
jim@vulcan2:~$ sisbsuspspspspsdsdspsdsdsdspsdsdsdsdsds
sisbsuspspspspsdsdspsdsdsdspsdsdsdsdsds: command not found
jim@vulcan2:~$ 
::1              ff02::1          ip6-allrouters   ip6-loopback     vulcan2
fe00::0          ff02::2          ip6-localhost    ip6-mcastprefix  
ff00::0          ip6-allnodes     ip6-localnet     localhost        
jim@vulcan2:~$ s
s: command not found
jim@vulcan2:~$ 
::1              ff02::1          ip6-allrouters   ip6-loopback     vulcan2
fe00::0          ff02::2          ip6-localhost    ip6-mcastprefix  
ff00::0          ip6-allnodes     ip6-localnet     localhost        
jim@vulcan2:~$ s
s: command not found
jim@vulcan2:~$ 
::1              ff02::1          ip6-allrouters   ip6-loopback     vulcan2
fe00::0          ff02::2          ip6-localhost    ip6-mcastprefix  
ff00::0          ip6-allnodes     ip6-localnet     localhost        
jim@vulcan2:~$ s
s: command not found
jim@vulcan2:~$ 
::1              ff02::1          ip6-allrouters   ip6-loopback     vulcan2
fe00::0          ff02::2          ip6-localhost    ip6-mcastprefix  
ff00::0          ip6-allnodes     ip6-localnet     localhost        
jim@vulcan2:~$ sdsdsfsfsysysos
sdsdsfsfsysysos: command not found
jim@vulcan2:~$ 
::1              ff02::1          ip6-allrouters   ip6-loopback     vulcan2
fe00::0          ff02::2          ip6-localhost    ip6-mcastprefix  
ff00::0          ip6-allnodes     ip6-localnet     localhost        
jim@vulcan2:~$ s
s: command not found
jim@vulcan2:~$ 
::1              ff02::1          ip6-allrouters   ip6-loopback     vulcan2
fe00::0          ff02::2          ip6-localhost    ip6-mcastprefix  
ff00::0          ip6-allnodes     ip6-localnet     localhost        
jim@vulcan2:~$ s
s: command not found
jim@vulcan2:~$ 
::1              ff02::1          ip6-allrouters   ip6-loopback     vulcan2
fe00::0          ff02::2          ip6-localhost    ip6-mcastprefix  
ff00::0          ip6-allnodes     ip6-localnet     localhost        
jim@vulcan2:~$ s
s: command not found
jim@vulcan2:~$ 
::1              ff02::1          ip6-allrouters   ip6-loopback     vulcan2
fe00::0          ff02::2          ip6-localhost    ip6-mcastprefix  
ff00::0          ip6-allnodes     ip6-localnet     localhost        
jim@vulcan2:~$ s
s: command not found
jim@vulcan2:~$ 
::1              ff02::1          ip6-allrouters   ip6-loopback     vulcan2
fe00::0          ff02::2          ip6-localhost    ip6-mcastprefix  
ff00::0          ip6-allnodes     ip6-localnet     localhost        
jim@vulcan2:~$ s
s: command not found
jim@vulcan2:~$ 
::1              ff02::1          ip6-allrouters   ip6-loopback     vulcan2
fe00::0          ff02::2          ip6-localhost    ip6-mcastprefix  
ff00::0          ip6-allnodes     ip6-localnet     localhost        
jim@vulcan2:~$ s
s: command not found
jim@vulcan2:~$ 
::1              ff02::1          ip6-allrouters   ip6-loopback     vulcan2
fe00::0          ff02::2          ip6-localhost    ip6-mcastprefix  
ff00::0          ip6-allnodes     ip6-localnet     localhost        
jim@vulcan2:~$ s
s: command not found
jim@vulcan2:~$ 
::1              ff02::1          ip6-allrouters   ip6-loopback     vulcan2
fe00::0          ff02::2          ip6-localhost    ip6-mcastprefix  
ff00::0          ip6-allnodes     ip6-localnet     localhost        
jim@vulcan2:~$ s
s: command not found
jim@vulcan2:~$ 
::1              ff02::1          ip6-allrouters   ip6-loopback     vulcan2
fe00::0          ff02::2          ip6-localhost    ip6-mcastprefix  
ff00::0          ip6-allnodes     ip6-localnet     localhost        
jim@vulcan2:~$ s
s: command not found
jim@vulcan2:~$ 
::1              ff02::1          ip6-allrouters   ip6-loopback     vulcan2
fe00::0          ff02::2          ip6-localhost    ip6-mcastprefix  
ff00::0          ip6-allnodes     ip6-localnet     localhost        
jim@vulcan2:~$ s
s: command not found
jim@vulcan2:~$ 
::1              ff02::1          ip6-allrouters   ip6-loopback     vulcan2
fe00::0          ff02::2          ip6-localhost    ip6-mcastprefix  
ff00::0          ip6-allnodes     ip6-localnet     localhost        
jim@vulcan2:~$ s
s: command not found
jim@vulcan2:~$ 



So those weird commands, like sdsdsd etc. They come from me JUST pressing d, and then the 's' is automatically placed. This **** is so weird, This is the same stuff I thought was a virus... I'm really lost. I did a clean wipe and it's back?

---

### Post by KillerKelvUK on 2016-05-11
That is weird!

Did you try the IBUS change, that will be system wide and not related to virt-manager?

You could try disabling IPv6 system-wide assuming you don't need IPv6.

Nothing to do with the keyboard mapping being altered on the host.  Have you ssh'd in for another box to see if that produces similar results?

---

### Post by hermes5 on 2016-05-11
Thanks for the reply. I'm not sure the steps about IBUS you gave me apply to kubuntu, I did find the configuration though.

> Current configuration for the input method:
 * Active configuration: missing (normally missing)
 * Normal automatic choice: none (normally ibus or fcitx or uim)
 * Override rule: zh_CN,fcitx:zh_TW,fcitx:zh_HK,fcitx:zh_SG,fcitx:ja_JP,fcitx:ko_KR,fcitx:vi_VN,fcitx
 * Current override choice:  (en_AU)
 * Current automatic choice: none
 * Number of valid choices: 1 (normally 1)
The override rule is defined in /etc/default/im-config.
The configuration set by im-config is activated by re-starting X.
Explicit selection is not required to enable the automatic configuration if the active one is default/auto/cjkv/missing.

and also 

> Keeping the user configuration /home/jim/.xinputrc as missing.
Automatic configuration selects: none
This does not set any IM from im-config.
This is the automatic configuration choice if no required IM packages are installed.
If a daemon program for the previous configuration is re-started by the X session manager, you may need to kill it manually with kill(1).
See im-config(8) and /usr/share/doc/im-config/README.Debian.gz for more.


I will do a bit of research about IPv6 and whether I need it, and haven't tried SSH from another box, I'm not completely sure what you mean by it but I will look into that as well.

---

### Post by MAFoElffen on 2016-05-16
Those ~/.xinoutrc does not exist unless you set something other than default for you display, by "some" methods (not all). 

Niether of those errors have anything to do with your display or ibus.

LOL = If you look at your addresses in those errors, they are multicast broadcast, localhost and local network... (albiet in IPv6, but that is really is a moot point). If you are getting errors in those, then you really need to confirm that the service listener you are expecting ... is really up or not. You can confirm that by:
```

nmap -sT -O localhost
netstat -anp

```

[COLOR=#ff0000]EDIT:[/COLOR]
But those are distractions to your main complaint right? (Keyboard and Mouse in Firefox on host)...

Is your host keyboard and mouse ps2 or usb? If usb, are they wireless or wired?

[COLOR=#ff0000]***-->[/COLOR] I noticed and remember this happening previously with KVM host (that at the time was 14.04.2 server) a 14.04.2 remote connection through virt-manager, VNC ... and in FireFox on that remote host. But when both remote and kvm hosts (of mine) went to point release 14.04.03 (and later to 14.04.04), it started working again. Maybe this is a case where it needs to be reported as a problem to launchpad, so that they can be made aware that the problem has reappeared, and can apply that same fix to 16.04 (if that is the same problem), so that it can be resolved/applied before the first point release of 16.04(?) Just thinking out loud.

---

### Post by houstonbofh on 2016-05-16
Note that virt-manager will steal keyboard and mouse focus, even when it is the bottom window!  Send it all the way to the task bar, and see if the problem stops.

---

