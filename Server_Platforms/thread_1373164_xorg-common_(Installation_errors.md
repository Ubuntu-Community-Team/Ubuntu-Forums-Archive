---
title: "xorg-common (Installation errors"
date: 2010-01-05
forum: Server Platforms
---

### Post by ndnd on 2010-01-05
Hi I am new to linux system. I have setup the Ubuntu server on Dell Powerdge 2900 (the latest server version 9.XX) 

I would like to install the 'minimal' X11 package so I have done the following 

Step1:
> 
$ dpkg -l x11-common
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                   Version                Description
+++-======================-======================-============================================================
ii  x11-common             1:7.4+3ubuntu7         X Window System (X.Org) infrastructure


Step2:
> :~$ sudo aptitude search x11-common
i A x11-common                                       - X Window System (X.Org) infrastructure                    
$ sudo apt-get install x11-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  x11-apps libxfixes3 xfonts-75dpi xserver-xorg-video-all xserver-xorg-video-apm xserver-xorg-video-ark
  xserver-xorg-video-ati ttf-dejavu-extra xfonts-scalable xfonts-encodings libxxf86dga1
  xserver-xorg-video-openchrome x11-utils ttf-dejavu-core xserver-xorg-video-s3virge xserver-xorg-video-v4l
  x11-xkb-utils xserver-xorg-video-mga xserver-xorg-video-chips libdrm-radeon1 xserver-xorg-core
  xserver-xorg-video-mach64 libxxf86vm1 xterm xserver-common libgl1-mesa-dri xserver-xorg-video-trident
  libgl1-mesa-glx xserver-xorg-video-sis xserver-xorg-video-siliconmotion xserver-xorg-input-vmmouse
  xfonts-utils xserver-xorg-video-savage xorg-docs-core xserver-xorg-video-tdfx x11-session-utils
  xserver-xorg-video-intel libxfont1 xinput xserver-xorg-input-all xbitmaps libdrm2 xserver-xorg-video-vmware
  libpixman-1-0 libxaw7 xserver-xorg-video-r128 xfonts-base xserver-xorg-input-evdev libxinerama1
  xserver-xorg-video-vesa x11-xfs-utils libxft2 fontconfig-config libice6 x11-xserver-utils libdrm-intel1
  xserver-xorg-video-s3 xserver-xorg libxmu6 libxtrap6 xserver-xorg-video-nv xfonts-100dpi
  xserver-xorg-video-voodoo xserver-xorg-video-fbdev xserver-xorg-input-wacom libxpm4 libxrender1 xinit libfs6
  xserver-xorg-video-neomagic libfontenc1 xserver-xorg-input-mouse ttf-dejavu libpciaccess0 libxxf86misc1
  libxtst6 libxvmc1 libfontconfig1 xserver-xorg-video-sisusb libsm6 libxdamage1 xserver-xorg-video-tseng
  xserver-xorg-video-radeon libglu1-mesa libxi6 xserver-xorg-video-cirrus libxcursor1 libxt6 libxv1 defoma
  libxrandr2 xserver-xorg-input-synaptics xserver-xorg-video-rendition libxkbfile1 xserver-xorg-video-i128
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  x11-common
1 upgraded, 0 newly installed, 0 to remove and 62 not upgraded.
Need to get 315kB of archives.
After this operation, 12.3kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main x11-common 1:7.4+3ubuntu10 [315kB]
Fetched 315kB in 0s (365kB/s)      
Preconfiguring packages ...
(Reading database ... 46213 files and directories currently installed.)
Preparing to replace x11-common 1:7.4+3ubuntu7 (using .../x11-common_1%3a7.4+3ubuntu10_all.deb) ...
Unpacking replacement x11-common ...
Processing triggers for man-db ...
Setting up x11-common (1:7.4+3ubuntu10) ...
Installing new version of config file /etc/gdm/failsafeXinit ...
Installing new version of config file /etc/gdm/failsafeXServer ...


Done with installation 

Now I try 'startx' for starting the X server
> 
$ sudo startx
xauth:  error in locking authority file /home/xxx/.Xauthority
xauth:  error in locking authority file /home/xxx/.Xauthority
xauth:  error in locking authority file /home/xxx/.Xauthority
xauth:  error in locking authority file /home/xxx/.Xauthority


X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux tango 2.6.31-14-server #48-Ubuntu SMP Fri Oct 16 15:07:34 UTC 2009 x86_64
Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.31-14-server root=UUID=9243e49d-9803-42ee-8406-e0fb27f4df7e ro quiet splash
Build Date: 26 October 2009  05:19:56PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan  5 11:43:19 2010
(==) Using default built-in configuration (30 lines)
(EE) open /dev/fb0: No such file or directory
(EE) MGA(0): Static buffer allocation failed, not initializing the DRI
(EE) MGA(0): Need at least 15360 kB video memory at this resolution, bit depth
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server




:confused:

I have used Xming on my windows machine when I ssh into the server. All the above steps are running from my ssh session. I don't think this matters but it's out there..

thanks in advance.

---

### Post by kiranmurari on 2010-01-06
Hi,

       Can you please try the following procedure.
   
On the ubuntu server add the following to the ~/.profile file:
```
 echo "X-server connection?"; read X11RESP
if [ "$X11RESP" = "y" ]
then
  DISPLAY=`echo $SSH_CONNECTION | cut -d" " -f1`  # Source IP address
  DISPLAY=$DISPLAY:0    # append display number
  export DISPLAY
  startx -t &            # start X11, will time out if no connection
fi
```On Windows, enable X11 forwarding in your SSH client (Putty). In Putty, it is present in Connection -> SSH -> X11

Create a new XLaunch Config file and choose following options in the configuration:

[LIST]
[*]Multiple Windows, Start a program, Run remote program and select using putty during the configuration phase.
[*]Enter the server IP and credentials.
[*]You can save this configuration for future use.
[*]Start Xming.
[/LIST]
Now connect to the remote server using the Putty SSH client. Once you login, you would be able to execute X11 apps and see the output on your windows machine.
   
One issue that you might encounter is:
```
xauth:  error in locking authority file /home/karmic/.Xauthority
``` This is due to stale xauth locks. Execute the following command:
```
 xauth -b quit
```Now restart your SSH connection and you would be able to execute X11 apps.

Hope this helps.

Regards,
Kiran

---

### Post by ndnd on 2010-01-06
Thanks Kiran. 

I am trying this right now. 

I also noticed one other message when I login via SSH I get the following message at login

> Last login: Tue Jan  5 12:07:10 2010 from 
xxx.xxx.xxx

/usr/bin/X11/xauth:  /home/ndnd/.Xauthority not writable, changes will be ignored


---

### Post by ndnd on 2010-01-06
I did the changes and this is what I got 


> X-server connection?
y

X: user not authorized to run the X server, aborting.
ndnd@tango:~$ giving up.
xinit:  No such file or directory (errno 2):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.

[1]+  Done                    startx -t
ndnd@tango:~$  xauth -b quit
ndnd@tango:~$ 



I tried again about the xauth-b quit command same response. 

> X: user not authorized to run the X server, aborting.
ndnd@tango:~$ giving up.
xinit:  No such file or directory (errno 2):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.



---

### Post by kiranmurari on 2010-01-06
Please check the permissions of /home/ndnd/.Xauthority. The file should be owned by user ndnd.

Regards,
Kiran

---

### Post by kiranmurari on 2010-01-07
Also can you execute the [SIZE=1]xauth -b quit[/SIZE] (there is a space after xauth) first on the server before trying to connect through XMing.

Regards,
Kiran

---

### Post by ndnd on 2010-01-07
thanks Kiran,

Yes I had noticed the file and group were 'root' so I had changed it to ndnd. 

I was able to execute the 

$xauth -b quit 

however there was no difference in the output. 

I also tried to install x11-apps and test it with xterm. It gave an error saying 

unable to display at my desktop's ip. 

I have Xwindows server running on my end - I know it works as I do connect to other other linux systems

---

