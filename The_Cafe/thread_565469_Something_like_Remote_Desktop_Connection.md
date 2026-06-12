---
title: "Something like Remote Desktop Connection"
date: 2007-10-02
forum: The Cafe
---

### Post by Black Mage on 2007-10-02
Alas there is one thing I do like in windows that I wish was in Ubuntu.

Is there something in Ubuntu like Remote Desktop Connection in windows where I can navigate another computer us Ubuntu like that was my desktop. I currently do use ssh but in ssh there isn't the advanced GUI component like in Remote Desktop Connection. I do use ssh -X but I have to know if the app is there are not.

So is there something like Remote Desktop Connection in Ubuntu?

---

### Post by jackocleebrown on 2007-10-02
There are several things that are similar to remote desktop connection.

The simplest to setup is VNC. On the machine you want to control to to "system"-"preferences"-"remote desktop" and check the boxes to "allow other users to view your desktop" and "allow other users to view your desktop" then click close. Leave this computer logged on. With the other computer that you want to be the controller open the terminal and type in the command "vncviewer" followed by the IP address of the computer you want to control e.g. "vncviewer 192.168.0.5" and you should get a remote desktop in a window.

There are two other ways that I know of:
XDMCP  which allows you to remotely log-in to a computer and have an independent session from the local user.
Nomachine-NX which is similar to XDMCP but very very fast.

Hope this helps.

Jack.

---

### Post by Insightfill on 2007-10-02
Regarding VNC, you might also want to turn off "Ask for confirmation" on the preference for "Remote Desktop Preferences" on the Ubuntu side, since you won't be there to accept!  On my home machine I also have it set to log in automatically on reboot, and have a password on the screen saver, and the vnc port is only available from within the subnet, or via SSH.  VNC suffers from sluggishness and fuzziness in the graphics at higher compressions, but you can connect from almost anywhere.

I've had pretty good luck with NoMachine-NX and FreeNX.  It's very smooth, very responsive, and even allow redirection of sound and printers.  It's essentially X-over-ssh, with stellar client-side caching.  They have Windows and Mac clients, too.  Closest thing to Windows RDC on the X side I've seen.

---

### Post by beercz on 2007-10-02
gnome-rdp - in the repos

Use it every day to access my office desktop pc and my windows 2003 servers

Works like a charm

---

### Post by JNowka on 2007-10-02
So far the best thing that I have found is the NX servers.  They are not only fast, and can work over the internet when setup correctly.  But you can install the client software on Mac, Linux, or Windows.  I set one of these up recently for the College I attend, and I haven't run into any problems.  You can get the proprietary NX server from [www.nomachine.com]("http://ubuntuforums.org/www.nomachine.com") or you can get the open source NX server from 
[http://freenx.berlios.de/](http://freenx.berlios.de/).  The big difference between the two is that the nomachine NX server can also let you send sound but will only let you have a maximum of two connections, and FreeNX doesn't serve sound but allows you to have more than two connections at a time.  But no matter which server you choose, you will need to download the NX Client software from nomachine.  Well, good luck.

---

### Post by JNowka on 2007-10-02
But you can only install the server on a linux computer.

---

### Post by HermanAB on 2007-10-02
Install OpenSSL.  This will give you a SSH daemon and client.  The advantage of SSH is that it is secure and can be used over the public internet.  With X forwarding, you can run any X programs provided that you  have a local X server.

From Windows, use Xming and PuTTY, then simply connect and run the gnome-panel, then clickety-click away...

Cheers,

Herman

---

### Post by MPD.JHB on 2007-10-16
KRDC works 100's for me

its installed by default in the internet folder.

to connect to a windows server using remote desktop, you will need to run

sudo apt-get install rdesktop 

then rdp:/serverip

and you are done.

---

### Post by n3tfury on 2007-10-16
> **JNowka said:**
> So far the best thing that I have found is the NX servers.  They are not only fast, and can work over the internet when setup correctly.  But you can install the client software on Mac, Linux, or Windows.  I set one of these up recently for the College I attend, and I haven't run into any problems.  You can get the proprietary NX server from [www.nomachine.com]("http://ubuntuforums.org/www.nomachine.com") or you can get the open source NX server from 
[http://freenx.berlios.de/](http://freenx.berlios.de/).  The big difference between the two is that the nomachine NX server can also let you send sound but will only let you have a maximum of two connections, and FreeNX doesn't serve sound but allows you to have more than two connections at a time.  But no matter which server you choose, you will need to download the NX Client software from nomachine.  Well, good luck.

i've heard nothing but great things about NX.  gonna have to try it out this weekend.

---

### Post by distortedecho on 2007-10-16
I don't have "Remote Desktop" in System > Preferences.

I'm also trying to setup this edubuntu laptop for remote access via VNC.

---

### Post by multidex on 2008-07-03
gnome-rdp worked great for me - thanks!

---

### Post by tr4sh on 2009-08-28
haha, fortunately I've read about this just now...

try this on terminal:

rdesktop

it'll show you a "how to use" line:
rdesktop: A Remote Desktop Protocol client.
Version 1.6.0. Copyright (C) 1999-2008 Matthew Chapman.
See [http://www.rdesktop.org/](http://www.rdesktop.org/) for more information.     

Usage: rdesktop [options] server[:port]
   -u: user name                       
   -d: domain                          
   -s: shell                           
   -c: working directory               
   -p: password (- to prompt)          
   -n: client hostname                 
   -k: keyboard layout on server (en-us, de, sv, etc.)
   -g: desktop geometry (WxH)                         
   -f: full-screen mode                               
   -b: force bitmap updates                           
   -L: local codepage                                 
   -A: enable SeamlessRDP mode                        
   -B: use BackingStore of X-server (if available)    
   -e: disable encryption (French TS)                 
   -E: disable encryption from client to server       
   -m: do not send motion events                      
   -C: use private colour map                         
   -D: hide window manager decorations                
   -K: keep window manager key bindings               
   -S: caption button size (single application mode)  
   -T: window title                                   
   -N: enable numlock syncronization                  
   -X: embed into another window with a given id.     
   -a: connection colour depth                        
   -z: enable rdp compression                         
   -x: RDP5 experience (m[odem 28.8], b[roadband], l[an] or hex nr.)
   -P: use persistent bitmap caching                                
   -r: enable specified device redirection (this flag can be repeated)                                                                    
         '-r comport:COM1=/dev/ttyS0': enable serial redirection of /dev/ttyS0 to COM1                                                    
             or      COM1=/dev/ttyS0,COM2=/dev/ttyS1                 
         '-r disk:floppy=/mnt/floppy': enable redirection of /mnt/floppy to 'floppy' share                                                
             or   'floppy=/mnt/floppy,cdrom=/mnt/cdrom'              
         '-r clientname=<client name>': Set the client name displayed
             for redirected disks                                    
         '-r lptport:LPT1=/dev/lp0': enable parallel redirection of /dev/lp0 to LPT1                                                      
             or      LPT1=/dev/lp0,LPT2=/dev/lp1                     
         '-r printer:mydeskjet': enable printer redirection          
             or      mydeskjet="HP LaserJet IIIP" to enter server driver as well                                                          
         '-r sound:[local[:driver[:device]]|off|remote]': enable sound redirection                                                        
                     remote would leave sound on server              
                     available drivers for 'local':                  
                     alsa:      ALSA output driver, default device: default                                                               
                     oss:       OSS output driver, default device: /dev/dsp or $AUDIODEV                                                  
         '-r clipboard:[off|PRIMARYCLIPBOARD|CLIPBOARD]': enable clipboard
                      redirection.
                      'PRIMARYCLIPBOARD' looks at both PRIMARY and CLIPBOARD
                      when sending data to server.
                      'CLIPBOARD' looks at only CLIPBOARD.
   -0: attach to console
   -4: use RDP version 4
   -5: use RDP version 5 (default)
   -y: use raw keyboard (default no)

since I know what username to use and I don't really like the full screen mode, I use this line:

rdesktop -u <username used to connect to> -P <destination IP>

---

