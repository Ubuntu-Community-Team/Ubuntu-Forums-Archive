---
title: "Gigantic app/dialogue windows in KVM guests when using nomodeset"
date: 2017-02-11
forum: Virtualisation
---

### Post by DuckHook on 2017-02-11
I'm trying to switch from using VBox to KVM but wrestling with the following problem:

[list]
[*]Using KVM with Virt-Manager, qxl video, spice display
[*]Host is running Ubuntu Xenial 64-bit
[*]Running 5 'buntu VMs: Mate-core, Gnome, Xubuntu-core, Lubuntu-core and Kubuntu.
[*]Guests are using *spice-vdagent*
[*]In all VMs, if KMS is enabled, both console and GUI boot only into 1024x768 resolution. Therefore, KMS is disabled with nomodeset.
[*]If nomodeset, all consoles properly boot into mode defined in GRUB_ GFXMODE=<what>x<ever>&#8230;
[*]&#8230;and all GUIs will properly autosense/autoconfigure into whatever resolution QEMU window is set at. 
[*]Mate, Xubuntu and Gnome behave well.
[*]But under nomodeset, Lubuntu & Kubuntu display gigantic system dialogue boxes and highly magnified app windows in some applications.
[*]Kubuntu is the worst: this unwanted magnification affects every app except Firefox.
[*]Lubuntu is variable: LXTerminal is gigantic, so are some other system dialogues like Monitor Settings and Screensaver Settings. But XVT is proper resolution. So is PCManFM, Desktop Preferences, Network Connections and Printers.
[*]If I enable KMS by deleting nomodeset, then manually define a modeline/add mode/set mode using xrandr, then all apps and dialogue boxes have proper resolution, but I lose the ability to resize to an arbitrary resolution by dragging the QEMU window. This is a functionality I am unwilling to give up because I use a big monitor and like my VMs in portrait mode.
[/list]
Has anyone else experienced this issue? If so, how did you solve it?

I am aware of the remote desktop/ssh workarounds, but would rather not use them because:

[list=1]
[*]I don't want to add further apps and services to my VMs, especially Lubuntu-core
[*]I am by equal measures curious and stubborn; I would like to know what is going on and want to wrestle this one to the ground.
[/list]
All input is valued.

Details follow:
```
duckhook@Kubuntu:~$ xrandr
Screen 0: minimum 320 x 200, current 1200 x 1600, maximum 8192 x 8192
qxl-0 connected primary 1200x1600+0+0 0mm x 0mm
   1024x768      60.00 +
   3840x2160     60.00  
   3200x2400     60.00  
   2800x2100     60.00  
   2560x2048     60.00  
   2048x2048     60.00  
   2560x1600     60.00  
   2000x2000     60.00  
   2560x1440     60.00  
   2048x1536     60.00  
   1920x1440     60.00  
   1920x1200     60.00  
   1920x1080     60.00  
   1600x1200     60.00  
   1680x1050     60.00  
   1400x1050     60.00  
   1600x900      60.00  
   1280x1024     60.00  
   1440x900      60.00  
   1280x960      60.00  
   1366x768      60.00  
   1360x768      60.00  
   1280x800      60.00  
   1152x870      60.00  
   1152x864      60.00  
   1280x768      60.00  
   1280x760      60.00  
   1280x720      60.00  
   1024x600      60.00  
   960x640       60.00  
   832x624       60.00  
   800x600       60.00  
   800x480       60.00  
   640x480       60.00  
   1200x1600-0    0.06*
```
```
duckhook@Kubuntu:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update                                     
# /boot/grub/grub.cfg.                                                                                
# For full documentation of the options in this file, see:                                            
#   info -f grub -n 'Simple configuration'                                                            
                                                                                                      
GRUB_DEFAULT=0                                                                                        
GRUB_HIDDEN_TIMEOUT=0                                                                                 
GRUB_HIDDEN_TIMEOUT_QUIET=true                                                                        
GRUB_TIMEOUT=10                                                                                       
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`                                      
# GRUB_CMDLINE_LINUX_DEFAULT="splash quiet"                                                           
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset consoleblank=0"                                                 
GRUB_CMDLINE_LINUX=""                                                                                 
                                                                                                      
# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1200x1600x16
GRUB_GFXPAYLOAD_LINUX=keep

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```
```
duckhook@Kubuntu:~$ lspci -vk | grep -iA8 vga
00:02.0 VGA compatible controller: Red Hat, Inc. QXL paravirtual graphic card (rev 04) (prog-if 00 [VGA controller])
        Subsystem: Red Hat, Inc QEMU Virtual Machine
        Flags: fast devsel, IRQ 10
        Memory at f4000000 (32-bit, non-prefetchable) [size=64M]
        Memory at f8000000 (32-bit, non-prefetchable) [size=64M]
        Memory at fc054000 (32-bit, non-prefetchable) [size=8K]
        I/O ports at c100 [size=32]
        Expansion ROM at fc040000 [disabled] [size=64K]
        Kernel modules: qxl
```
Nothing jumps out from guest *dmesg* but maybe I don't know what to look for. I will post *dmesg* if someone thinks it will help (it's long).

Sanitized output from host after running ```
duckhook@Prime:~$ virsh edit Kubuntu
``````
<domain type='kvm'>
  <name>Kubuntu</name>
  <uuid>xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxx</uuid>
  <memory unit='KiB'>4194304</memory>
  <currentMemory unit='KiB'>4194304</currentMemory>
  <vcpu placement='static'>2</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-xenial'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
  </features>
  <cpu mode='custom' match='exact'>
    <model fallback='allow'>SandyBridge</model>
  </cpu>
  <clock offset='utc'>
    <timer name='rtc' tickpolicy='catchup'/>
    <timer name='pit' tickpolicy='delay'/>
    <timer name='hpet' present='no'/>
  </clock>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <pm>
    <suspend-to-mem enabled='no'/>
    <suspend-to-disk enabled='no'/>
  </pm>
  <devices>
    <emulator>/usr/bin/kvm-spice</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2'/>
      <source file='/mnt/duckhook/images/Kubuntu.qcow2'/>
      <target dev='hda' bus='ide'/>
      <address type='drive' controller='0' bus='0' target='0' unit='0'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <target dev='hdb' bus='ide'/>
      <readonly/>
      <address type='drive' controller='0' bus='0' target='0' unit='1'/>
    </disk>
    <controller type='usb' index='0' model='ich9-ehci1'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x7'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci1'>
      <master startport='0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0' multifunction='on'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci2'>
      <master startport='2'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x1'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci3'>
      <master startport='4'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pci-root'/>
    <controller type='ide' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <controller type='virtio-serial' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </controller>
    <interface type='bridge'>
      <mac address='xx:xx:xx:xx:xx:xx'/>
      <source bridge='br0'/>
      <model type='rtl8139'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <serial type='pty'>
      <target port='0'/>
    </serial>
    <console type='pty'>
      <target type='serial' port='0'/>
    </console>
    <channel type='spicevmc'>
      <target type='virtio' name='com.redhat.spice.0'/>
      <address type='virtio-serial' controller='0' bus='0' port='1'/>
    </channel>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <graphics type='spice' autoport='yes'>
      <image compression='off'/>
    </graphics>
    <sound model='ich6'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </sound>
    <video>
      <model type='qxl' ram='65536' vram='65536' vgamem='16384' heads='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <redirdev bus='usb' type='spicevmc'>
    </redirdev>
    <redirdev bus='usb' type='spicevmc'>
    </redirdev>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
    </memballoon>
  </devices>
</domain>
```
Please ask if more data needed.

---

### Post by DuckHook on 2017-02-12
Bump

---

### Post by KillerKelvUK on 2017-02-13
Hey DuckHook, I've not been able to recreate your scenario but made some observations along the way that may help...

Host is Ubuntu 16.04.2 LTS, clean kbuntu 16.10 guest.

Guest configured with and without KMS could set resolution independent to grub configuration and I had no odd magnification as you describe.

Observations...
[LIST=1]
[*]In the kbunutu Display Configuration app the primary display is shown as 'Virtual-0' when using KMS and 'qxl-0' when not.  I don't perceive this to be of any consequences, merely a confirmation of nomodeset having the desired effect.
[*]However in the same app the displayed resolution I found to be incorrect, i.e. the app always showed the resolution to be 1024x768 when in fact the display was outputting differently.  The actual display resolution was correct as per my setting but on reboot the Display Configuration app would not reflect the current value, I've screenshotted this below...
[/LIST]


[ATTACH=CONFIG]273698[/ATTACH]


Shout if you want to compare some more tests, like you the curious/stubborn driver in me would hate this!

---

### Post by DuckHook on 2017-02-13
> **KillerKelvUK said:**
> ...like you the curious/stubborn driver in me would hate this!&#8230;a kindred spirit, I see. :)

Good idea to provide screenshots. I have attached a couple from my Lubuntu guest.[ATTACH=CONFIG]273693[/ATTACH][ATTACH=CONFIG]273694[/ATTACH]

I decided not to use screenshots from my Kubuntu guest because they are all uniformly huge, thus lacking in contrast, and thus hard to convey how wonky they look. As these images show, the difference between the two dialogue boxes are significant. It's as if the *monitors* box believes it is being displayed in a 1024x768 screen and scales up to fill it, whereas the *printers* box recognizes the proper display resolution.

The login dialogue is included to show how lightdm does not recognize the resolution either and defaults to a 1024x768 box. This happens in all of my 'buntu guests, but the other three recognize the proper resolution after login, whereas Kubuntu does not, and Lubuntu does for some apps but not for others.

In some ways, the Lubuntu behaviour is even odder than Kubuntu. I can at least wrap my head around why a distro might *uniformly* misread resolution, but when some apps do while some don't, that is really weird.

Since first posting, I've further scoured Google and am no wiser.
> In the kbunutu Display Configuration app the primary display is shown as 'Virtual-0' when using KMS and 'qxl-0' when not. I don't perceive this to be of any consequences, merely a confirmation of nomodeset having the desired effect.That's my behaviour too. It may have some significance, but if so, it's lost on me.
> However in the same app the displayed resolution I found to be incorrect, i.e. the app always showed the resolution to be 1024x768 when in fact the display was outputting differently. The actual display resolution was correct as per my setting but on reboot the Display Configuration app would not reflect the current value, I've screenshotted this belowAgain, a reflection of the behaviour that I see too. However, comparing the size of the type in your screenshot, it is clear that your guest apps display at a proper resolution. In my case, they are about three times as big in the guest.

Can you drag your guest window to any arbitrary size? If so, is this possible only with the nomodeset parameter or can you do it with KMS turned on?

BTW, for the sake of those with limited bandwidths or viewing from phones/tablets, it's a good idea to either attach your large screenshots as attachments (like I did) or else link to them from an image server like imgur.

---

### Post by KillerKelvUK on 2017-02-14
> Can you drag your guest window to any arbitrary size? If so, is this possible only with the nomodeset parameter or can you do it with KMS turned on?

So first answer is no, still clean kbuntu-16.10 install.  Noticed in the virt-manager menus that 'View --> Scale Displays --> Auto resize VM with windows' was greyed out...so quick snoop around with 'apt-get update | apt-get dist-upgrade' plenty of packages to install but this didn't help.  Checked to ensure the xorg qxl driver was installed it was...then google landed me on a thread talking about the spice guest tools so I took a look.  I didn't have the spice-vdagent installed so I installed it and presto...after a reboot the virt-manager menu option is available and has a tick against it and I can resize at will.  NOTE:  Needed to disable KMS for this to work, with KMS no cigar.

> BTW, for the sake of those with limited bandwidths or viewing from phones/tablets, it's a good idea to either attach your large screenshots as attachments (like I did) or else link to them from an image server like imgur.

Gotcha, no problems...the stupid thing was I was posting them to postimg.io and using the url to embed them...daft but quickly resolved :P

I'll grab an Lbunutu iso and try to reproduce all this with that, as you say its odd you're not getting a consistent error in distro.

---

### Post by KillerKelvUK on 2017-02-14
> In some ways, the Lubuntu behaviour is even odder than Kubuntu. I can at least wrap my head around why a distro might uniformly misread resolution, but when some apps do while some don't, that is really weird.

So I grabbed the lubuntu-16.10-amd64 image, installed it, ensure it was fully updated (apt-get dist upgrade) and yet I had a different experience to Kbuntu...the culprit, Lubuntu didn't install the xserver-xorg-video-qxl driver and so video was baaaaadddd!  Not quite like your situation but it maybe the route of your evils perchance?

Anyways pop in that package plus the spice-vdagent and I can resize the window and the resolution changes as per expectation/need.  Screenshot for comparison below...

[ATTACH=CONFIG]273700[/ATTACH]

---

### Post by DuckHook on 2017-02-14
> **KillerKelvUK said:**
> …I didn't have the spice-vdagent installed so I installed it and presto...after a reboot the virt-manager menu option is available and has a tick against it and I can resize at will.I should have mentioned that spice-vdagent was installed in my guests. Have edited original post to reflect that.> Needed to disable KMS for this to work, with KMS no cigar.On this point, our experiences are identical.> …Lubuntu didn't install the xserver-xorg-video-qxl driver and so video was baaaaadddd!  Not quite like your situation but it maybe the route of your evils perchance?In my case, *xserver-xorg-video-qxl* has always been present.> Screenshot for comparison below…I'm happy for you&#8213;and just a tad envious&#8213;that everything is working properly and displaying proportionately. I'm still wrestling with the disproportionate app-level resolutions. Here's a [screenshot]("http://imgur.com/a/NUKkO") of my Kubuntu install. The giant text on the left is from the LibreOffice New Document Dialogue Box. The properly-sized text on right is from Firefox. As mentioned above, FF looks correct in *all* guest VMs.

[LIST=1]
[*]What kernel (version) are you running in your guests?
[*]What is your host video card/GPU?
[*]What driver are you using on your host?
[/LIST]

---

### Post by DuckHook on 2017-02-15
***!!SUCCESS!!***

The problem was with the DPI settings in both Kubuntu and Lubuntu. Likely due to the fact that my installs are DEs layered onto a mini.iso image, my DPIs were set at really wonky values. Only an educated guess, but I suspect that this led to some apps reading the system dpi while others read the X11 dpi. Kubuntu is more uniform in where it gets its info from, hence its more uniform behaviour. Lubuntu behaviour is all over the place because it is cobbled together from more disparate parts.

The fix in Kubuntu is simple (if obscure): force the DPI to 96 under: Settings&#8594;Fonts&#8594;Force fonts DPI.

The fix for Lubuntu is more involved. A temporary fix can be made by invoking *xvt* or *xterm*, then:```
xrandr --dpi 96x96
```A more permanent fix requires that this be invoked from a shell script using Lubuntu's autostart facility at login.

Will post the complete steps after a well-earned night's sleep. For now, just happy that I solved it.  \\:D/

---

### Post by KillerKelvUK on 2017-02-15
Well done, what a random little nugget that was!  At least the curious/stubborn angel will be sated now :popcorn:

---

### Post by DuckHook on 2017-02-15
Though solved, for the sake of posterity, here is a synopsis of the problem, followed by the solutions.

**Context:**

KVM virtual machines are most versatile if run using the qxl driver and with Spice enabled. The qxl driver is not only faster and more resource-efficient, but, in combination with spice-vdagent, it allows the guest machine to be interactively resized to any arbitrary window size and it also activates the shared clipboard between host and guests. But for unknown reasons, qxl misbehaves with KMS enabled in the guest. KMS can be turned off by setting the nomodeset kernel parameter in GRUB```
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet nomodeset"
```…but doing so will cause other problems.

**The Problem:**

Without KMS enabled, guest VMs cannot detect the true initial size of the virtualized display. Instead, they fall back to the highest VGA setting. But VGA is a primitive standard and maxes out at 1024x768. This is what causes, for example, the lightdm logon screen to boot into a 1024x768 box.

X sessions do not start until *after* the user logs in. This is a very important fact that could have saved me hours of wasted effort had I remembered it earlier. This has application later.

Once the user logs in, Spice will expand the resolution to fill the virtual display. However, with some Desktop Environments, *it will not set all DPI variables*. The gnome-based or gtk-based desktops appear to be well-integrated with their spice-modified X environments, but Kubuntu&#8213;being QT-based, and Lubuntu&#8213;being a Frankenstein's Monster of horked together bits and pieces, are not.

If DPI is not set, apps will display by polling one of two settings. If they poll the spice-controlled X settings, they will see the true size of the virtual display and set their window sizes and fonts to the proper system resolution. But if they poll the kernel settings, all they see is a 1024x768 VGA display and will balloon their output to fill out what they think is a low resolution monitor.

**Solution:**

The balky Desktop Environments must have their DPI forced-set to a specific resolution. Any resolution will do. The critical factor is forcing the setting. Somehow, this forces all apps to poll the Spice-controlled X settings and to drop the kernel settings.

**In Kubuntu Xenial:**

…the setting is simple (if somewhat unintuitive): it can be set in "System Settings"&#8594;"Fonts" and then checking the box: *Force fonts DPI*. The location of this setting is misleading: it forces your entire KDE desktop to use the new DPI value and not just your fonts. Set it to whatever DPI value you want. I found the best value to be the actual monitor DPI, calculated by simply dividing the monitor resolution by the actual dimensions of the monitor.

**In Lubuntu Xenial:**

…it's more complicated. There is no single GUI app that allows you to force DPI. Instead, this must be done using configuration files. And this is where remembering that X sessions don't start until a user logs comes into play.

Googling will return tons of results instructing you to add:```
xrandr --dpi xxx    #replace xxx with your values
```…to a variety of system files. None of these worked for me and I wasted hours in frustration and failed attempts, until I remembered that xrandr will only work *after* X is up and running. Therefore, adding this line to some file in /etc is going to fail, since almost everything in /etc is run prior to user login.

One could create the directory /.local/share/applications, then build a simple script containing the xrandr command, and then invoke it with a .desktop file. Such a method will work because apps launched in this way will only do so after the user has logged in and a working Xsession is up and running, but this also has drawbacks. It seems to change the DPI for apps, but not for LXDE itself, so system dialogues are still wrong.

The best solution, it turns out, is to recreate a file that was deprecated in Xenial, but still actually works. This is the .Xresources file in your $HOME directory.```
nano ~/.Xresources
```Fill it with:```
Xft.dpi: 106
```…or whatever DPI value you wish. Save, exit nano and reboot. Your VM desktop environment should now have consistent fonts, windows and dialogue boxes throughout.

I suspect that this method will also work with other misbehaving guest distros running in VMs. I'm going to try it on a Bodhi VM that doesn't look right.

---

### Post by KillerKelvUK on 2017-02-16
Good summary.

Did you conclude that this behaviour is linked you putting a DE ontop a minimal install as this issue didn't present for me using the full desktop iso for either distro?

---

### Post by DuckHook on 2017-02-16
> **KillerKelvUK said:**
> Good summary.

Did you conclude that this behaviour is linked you putting a DE ontop a minimal install as this issue didn't present for me using the full desktop iso for either distro?
Possibly so, but I also installed a fresh Bodhi guest and converted a Lubuntu VDI image (that was originally a fresh install) with the same results, so it's hard to think so. It may have something to do with my GPU and host Radeon driver which has required special treatment for some other apps too, but that's just more speculation. Anyhow, I hope this will help others who run into my collection of circumstances,

---

