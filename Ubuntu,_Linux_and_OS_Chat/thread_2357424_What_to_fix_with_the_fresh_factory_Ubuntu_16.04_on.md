---
title: "What to fix with the fresh factory Ubuntu 16.04 on a Dell XPS 13"
date: 2017-04-02
forum: Ubuntu, Linux and OS Chat
---

### Post by laluz2 on 2017-04-02
The Dell XPS 13 with the factory installed Ubuntu on 16.04 has a few shortcomings that  needed to be fixed before it is fully useful. Below are the things I had  to fix. Please feel free to add yours as well. I am moving this from the AskUbuntu, on a request from the admins because this is not just a single question and some things are opinionated.

** Cooling Fan spins up because of a faulty samba process**

  The culprit is gvfsd-smb-browse process.

  Add the statement below to [global] section of your /etc/samba/smb.conf
  name resolve order = wins lmhosts bcast
  [https://itsfoss.com/fix-gvfsd-smb-high-cpu-ubuntu/](https://itsfoss.com/fix-gvfsd-smb-high-cpu-ubuntu/)
  Remove conflicting duplicate touchpad driver

  To get things working properly, I needed to disable the second  touchpad device "SynPS/2 Synaptics TouchPad". I think it was mostly  being ignored, and syndaemon was attaching to it instead of "DLL0704:01  06CB:76AE Touchpad", which was actually managing the touchpad.

  I disabled it in the Xorg config file. I opened:

  /usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf
  and added this entry:
  Code:
  # Disable generic Synaptics device, as we're using
# "DLL0704:01 06CB:76AE Touchpad"
# Having multiple touchpad devices running confuses syndaemon
Section "InputClass"
        Identifier "SynPS/2 Synaptics TouchPad"
        MatchProduct "SynPS/2 Synaptics TouchPad"
        MatchIsTouchpad "on"
        MatchOS "Linux"
        MatchDevicePath "/dev/input/event*"
        Option "Ignore" "on"
EndSection
  [https://ubuntuforums.org/showthread.php?t=2316240](https://ubuntuforums.org/showthread.php?t=2316240)

**   Activate Touchpad Palm Detection**
copy the file /usr/share/X11/xorg.conf.d/50-synaptics.conf to /etc/X11/xorg.conf.d/50-synaptics.conf
Add  an *Option "PalmDetect" "1"* after line 13 so the overall this section looks like this:
  Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
    Option "PalmDetect" "1"
# This option is recommend on all Linux systems using evdev, but cannot be
# enabled by default. See the following link for details:
# [http://who-t.blogspot.com/2010/11/how-to-ignore-configuration-errors.html](http://who-t.blogspot.com/2010/11/how-to-ignore-configuration-errors.html)
      MatchDevicePath "/dev/input/event*"
EndSection
  [https://erik.torgesta.com/2016/11/things-to-improve-ubuntu-16-04-on-dell-xps-13-9630/](https://erik.torgesta.com/2016/11/things-to-improve-ubuntu-16-04-on-dell-xps-13-9630/)

  sudo add-apt-repository ppa:atareao/atareao
sudo apt-get update
sudo apt-get install touchpad-indicator
/opt/extras.ubuntu.com/touchpad-indicator/bin/touchpad-indicator&
  The touchipad icon should appear in the notification area. Go to  preferences, Set General Options->Autostart and Actions->Disable  Touchpad on typing. Youst  may want to adjust the delay in milliseconds  too.
**   Changing the scrolling direction of the two-finger scrolling on the touch-pad:**
EDIT: the below file doesn't seem to have any effect on the scrolling but breaks the mouse functionality. I have deleted it again but do not have the problem with the scrolling anymore.
  Alternate method from [http://askubuntu.com/a/519859/452753](http://askubuntu.com/a/519859/452753) worked for me:

  In the file /usr/share/X11/xorg.conf.d/20-natural-scrolling.conf you  have opened in your preferred text editor, paste the following:

  Section "InputClass"
        Identifier "natural scrolling for mouse wheel"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "mouse"
        Option "Device" "/dev/input/mice"
        Option "Protocol" "Auto"
        Option "ZAxisMapping" "5 4"
EndSection
  Save the file and reboot. As above, individual users can switch it  off on a per-user basis by using Ubuntu-Tweak to "turn on" natural  scrolling (it will be the reverse of the system-wide setting on a  per-user basis but will not affect the actual system setting for other  users who will want to use natural scrolling).

**   Get the F1-F12 row to function as such instead of media keys by default**

  [How to invert fn keys on Dell Laptop?]("http://askubuntu.com/questions/88063/how-to-invert-fn-keys-on-dell-laptop") Press F2 during POST (Power On Self Test) to enter the System Setup (BIOS) utility.

  In the Function Key Behavior, select Multimedia Key First or Function Key First.

  Function Key First &#8212; This is the default option. Press any function  key to perform the associated function. For multimedia action, press Fn +  the required multimedia key.
  Lacking dedicated page up/down, home/end buttons.

  The XPS 13 keyboard has these buttons combined with the arrow buttons  and so one needs two hands to access them (pressing Fn required). Here I re-purpose Print button to act as a Home button and Insert as  PgDn:
  xmodmap -e "keycode 107 = Home" # using "Print" button
xmodmap -e "keycode 118 = Next" # using "Insert" button
  Remove the Print shortcut to Screenshot in the System Settings->Keyboard ->Shortcuts->Screenshots
  Right Ctrl (with the list symbol) + up_arrow/down_arrow function as home/end as well.

**   Encrypted home directory blocks ssh key based authentication and vpn client**

  This is not strictly an XPS or 16.04 related issue, but it is helpful  to know that you need to move your authorized_keys file outside of your  encrypted home directory in order to be able to use ssh key based  authentication. [https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Troubleshooting](https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Troubleshooting)
  Here is a help entry from one of the VPN providers on the fix for their software in case you are using encrypted home directory. [URL="https://helpdesk.privateinternetaccess.com/hc/en-us/articles/227831828-Installing-the-PIA-app-on-Linux-with-encrypted-home-directories"]https://helpdesk.privateinternetaccess.com/hc/en-us/articles/227831828-Installing-the-PIA-app-on-Linux-with-encrypted-home-directories
[/URL]
**   Change Default Power Button Behaviour From Interactive to Suspend**

  gsettings set org.gnome.settings-daemon.plugins.power button-power suspend

**   Monitor Stays Blank After Suspend When External Monitor Was In Use**

  ToDo
     
Here is my list, based on recommendations from the [Arch Linux Wiki on the Dell XPS 13 (9360).]("https://wiki.archlinux.org/index.php/Dell_XPS_13_%289360%29")
  Update linux-firmware in order to get the i915 guc and huc blobs

  Manually install latest linux-firmware (at least released after 20170217).
  
[LIST=1]
[*]Go to the [Ubuntu linux-firmware package site for zesty]("https://launchpad.net/ubuntu/zesty/+package/linux-firmware"). 
[*]Click on "linux-firmware 1.xyz in amd64 (Release)", where xyz is the latest version you see on the page. (Assuming you need 64-bit packages) 
[*]Under Downloadable files click to download the .deb file. 
[*]Double-click the downloaded file to install it. 
[/LIST]
  Update to the latest kernel to get NVMe power savings

  Manually install kernel 4.11rc1 or later to get [an NVMe power savings patch]("https://github.com/damige/linux-nvme")  (download the linux-image-generic, linux-headers and  linux-headers-generic for the version you choose). This alone should net  you an idle power savings of 30%.
  
[LIST=1]
[*]Go to the [Ubuntu mainline kernel site]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/"). 
[*]Scroll to the bottom of the page and click the bottom link. 
[*]Click to download the amd64 .deb files:
[LIST]
[*]linux-headers-*.deb 
[*]linux-headers-*-generic.deb 
[*]linux-image-*-generic.deb 
[/LIST]
  
[*]Double-click the downloaded files to install them. 
[*]Run sudo update-grub. 
[/LIST]
  Improve graphics performance and power savings

  Requires above two updates first!
  Edit /etc/default/grub and include the following options after GRUB_CMDLINE_LINUX_DEFAULT="quiet splash to improve video driver power savings and performance:
  i915.modeset=1 i915.enable_rc6=1 i915.enable_fbc=1 i915.enable_guc_loading=1 i915.enable_guc_submission=1 i915.enable_huc=1 i915.enable_psr=1 i915.disable_power_well=0 i915.semaphores=1
  Run sudo update-grub.
  Note that you should be able to add these into a .conf file  for the i915 module, but Ubuntu doesn't seem to look at the file when I  create it, which is why I recommend this method instead. Also, not all  options are supported at this time (such as enable_huc and sempahores,  but may be in the future in later kernels or linux-firmware releases).
  I've tested Borderlands 2 with this and see an improvement of about 5  FPS (on an original 26 FPS). I also see a slight decrease in power  usage.
  Ensure you get the best wireless speeds

  Edit /etc/default/crda and set your country code at the end of the REGDOMAIN line.
  eg. REGDOMAIN=US
  Fix palm detection on the touchpad

  Install xserver-xorg-input-libinput.
  Create /usr/share/X11/xorg.conf.d/90-libinput.conf containing:
  Section "InputClass"
        Identifier "libinput touchpad catchall"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Driver "libinput"
        Option "Tapping" "True"
        Option "PalmDetection" "True"
        Option "TappingDragLock" "True"
EndSection
  Fix some screen tearing issues

  Create /usr/share/X11/xorg.conf.d/20-intel.conf containing:
  Section "Device"
        Identifier  "Intel Graphics"
        Driver      "intel"
        Option      "AccelMethod" "sna"
        Option      "TearFree"    "true"
EndSection
     
                   
                                            
             
** Manually Update GPU Firmware**
Follow instructions for Kabylake [https://01.org/linuxgraphics/downloads/firmware](https://01.org/linuxgraphics/downloads/firmware)

**Creating split view window keyboard shortcuts**

`sudo apt-get install compizconfig-settings-manager`
and then open CompizConfig Settings Manager, search for Grid plug-in and change the bindings for Left Maximize and Right Maximize to <kbd>Ctrl</kbd>+<kbd>Super</kbd>+<kbd>Right</kbd>/<kbd>Left</kbd>  accordingly. 
[http://askubuntu.com/questions/897089/creating-split-view-window-keyboard-shortcuts](http://askubuntu.com/questions/897089/creating-split-view-window-keyboard-shortcuts)

---

### Post by QIII on 2017-04-02
Do you have a question here?

---

### Post by laluz2 on 2017-04-02
> **QIII said:**
> Do you have a question here?

Thanks for asking, this is a post to keep these solutions in one place and profit from things other users have noticed and fixed.
This is why I have tagged it as [SOLVED] if that's fine with you guys.

Just to mention I have still things to figure out
[LIST]
[*]how to set the keyboard re-mapping permanent 
[*]the touchpad-indicator is defunct after adding Option "PalmDetect" "1" 
[*]Logitech unifying connector sees the mouse but the cursor doesn't move 
[/LIST]
while I was plannig to figure them out by myself help is always welcome.
There is a post of another XPS 13 user Andrew that we should move other here as well [http://askubuntu.com/a/897439/452753](http://askubuntu.com/a/897439/452753)

---

### Post by QIII on 2017-04-03
Moved to Ubuntu, Linux and OS Chat.  Not a support request and not a tutorial.

Also, please to not use special formatting.

---

### Post by laluz2 on 2017-11-14
I had to update the BIOS to 2.3.1 via "Ubuntu Software" application in order to use Dell Thunderbolt TB16 Docking Station. It is now functioning properly so far. 
It was **important to set the security level to "no security" in BIOS** under System configuration/USB configuration as otherwise the laptop would not boot.

Here are the helpful links from DELL (also thanks to their premier support - good job!) [https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en](https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en) [http://www.dell.com/support/home/de/de/dedhs1/drivers/driversdetails?driverId=JGCWT](http://www.dell.com/support/home/de/de/dedhs1/drivers/driversdetails?driverId=JGCWT)

Without the above update the USB ports would deactivate itself every minute or so. I have now Display Port, Ethernet, USB2/3 connected to the docking station and it is also charing the laptop via the thunderbolt connection. The charging did not work with the Elgato Thunderbolt3 docking station (but the rest worked).

---

### Post by msarro on 2017-11-21
Using libinput seems to cause the synaptics touchpad applet to crash at boot-time. However, most of the same items can be configured manually by editing /usr/share/X11/xorg.conf.d/90-libinput.conf.

Also, libinput doesn't support a palm detection option according to its manpage:

[http://manpages.ubuntu.com/manpages/xenial/man4/libinput.4.html](http://manpages.ubuntu.com/manpages/xenial/man4/libinput.4.html)

Here is my config for those who are curious:
Section "InputClass"
         Identifier "libinput touchpad catchall"
         MatchIsTouchpad "on"
         MatchDevicePath "/dev/input/event*"
         Driver "libinput"
         Option "Tapping" "True"
         Option "TappingDragLock" "True"
         Option "NaturalScrolling" "True"
         Option "AccelSpeed" "0.5"
         Option "MiddleEmulation" "True"
 EndSection

This speeds up the mouse, re-enabled middle button emulation, enables natural scrolling. Basically, it makes the touchpad largely behave like one on a macbook. The only thing I haven't figured out is how to also register an actual 2-finger click as a middle button click. Right now, tapping with 2 fingers registers as a middle click.

---

### Post by laluz2 on 2018-03-06
Here are my notes on Upgrade to 17.10

To be able to connect to the (hotel) wifi with redirection auth page
```
sudo dpkg-reconfigure resolvconf
```

On login screen click on the cog symbol (for settings) and change to the Unity option for the same experience as with factory 16.04. The other gui options were really ugly /not properly configured.

When logging in Unity session (which works more or less), I got this error :

[LIST]
[*][INDENT]   **Could not apply the stored configuration for monitors**

      required virtual size does not fit available size: requested=(1, 1), minimum=(320, 200), maximum=(8192, 8192)

 [/INDENT]
 
[/LIST]

installed ```
unity-control-center
```, ran it, and sure enough the Display panel was working and the correct (previous version) monitor.xml was being written.  After a reboot, everything worked as expected.

solution discussion here [URL="https://askubuntu.com/a/999783"]https://askubuntu.com/a/999783


[/URL]DNS was not working
```
$ sudo rm /etc/resolv.conf
$ sudo ln -s /run/resolvconf/resolv.conf /etc/resolv.conf
$ systemctl restart resolvconf
```[URL="https://askubuntu.com/a/999783"]
[https://askubuntu.com/a/967341/452753](https://askubuntu.com/a/967341/452753)
[/URL]

---

### Post by laluz2 on 2018-08-07
One more thing that still seems to affect the VPN re-connection for OpenVPN and PIA provider is this
error 

```
/usr/lib/NetworkManager/nm-openvpn-service-openvpn-helper --debug 0 5153 --bus-name org.freedesktop.NetworkManager.openvpn.Connection_16 --tun -- tun0 1500 1570 10.9.11.6 10.9.11.5 restart
WARNING: Failed running command (--up/--down): could not execute external program
Exiting due to fatal error
```

this should solve it [https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/280160/comments/19](https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/280160/comments/19)
```
                        I confirm this same bug in Ubuntu 12.04 LTS Precise Pangolin. The same workaround works:

 Steps to workaround:
 1. Change filename of  /usr/lib/NetworkManager/nm-openvpn-service-openvpn-helper
cd /usr/lib/NetworkManager/
mv nm-openvpn-service-openvpn-helper nm-openvpn-service-openvpn-helper.dist
 2. Create new file with same old name:
nano nm-openvpn-service-openvpn-helper
 3. Fill the file with variables to export and original executable. Copy and paste this:
 #!/bin/bash
 [ -z "$ifconfig_local" ] && export ifconfig_local=$4
[ -z "$ifconfig_remote" ] && export ifconfig_remote=$5
 /usr/lib/NetworkManager/nm-openvpn-service-openvpn-helper.dist $*
 4. Make the new file executable:
chmod +x nm-openvpn-service-openvpn-helper
 Now it works!

              
                                                         
```

---

### Post by laluz2 on 2018-08-08
pulseaudio complains about something in the syslog - purge and reinstall pulseaudio

```

grep pulse /var/log/syslog |less
indicator-sound[2013]: volume-control-pulse.vala:530: pa_context_connect() failed: Connection refused
indicator-sound[2013]: volume-control-pulse.vala:735: unable to get pulse unix socket: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.PulseAudio1 was not provided by any .service files

```
[https://askubuntu.com/a/435221/452753](https://askubuntu.com/a/435221/452753)

---

### Post by laluz2 on 2018-08-24
Upgraded 17.10 to 18.04.1 seemingly without fatal bugs. The docking station WD-16 is not recognized at the boot time (two yellow flashes and like eight white ones) but works fine if connected afterwards. Mapping of CapsLock to the Keyboard Layout changer is defunkt.

---

### Post by submiliand98 on 2018-10-31
Hello everyone, I received my laptop two weeks ago and run ubuntu 16.4 But during the initial install/setup, I accidentally chose the wrong wifi network.  While it was trying to connect, I hit the Stop button.  The installer then crashed and helpfully rebooted into a Guest account so I could investigate the issue.  Well, you can't do much from a guest account, in particular, you can't create a recovery USB stick.  Is there a way to restart the initial setup process?  Do I need to reinstall the OS, and if so where can I download a Dell recovery image since I can't create one from the laptop?


Thanks for your help

---

### Post by laluz2 on 2018-10-31
It’s probably better if you create a new thread with this question as it’s clearly a separate issue. 
But as a quick help try:
1. there is an option for a factory OS reset in the grub menu
2. You could try to boot into singleuser mode and set root password.

---

### Post by submiliand98 on 2018-10-31
Thanks a lot, Dear Laluz2. That's worked for me

---

### Post by oldos2er on 2018-11-01
Old thread closed.

---

