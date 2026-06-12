---
title: "system-config-lvm will work inside a kvm VM guest, but not on the host"
date: 2014-07-01
forum: Server Platforms
---

### Post by matt_fussell2 on 2014-07-01
The test system is running Ubuntu server 14.04 - aside from the basic updates, the following packages are installed:

**openbox alsa pulseaudio x2goserver x2goserver-xsession qemu-kvm libvirt-bin bridge-utils virt-manager virtinst ubuntu-vm-builder qemu libcap2-bin xterm system-config-lvm gnome-system-tools gparted**

Here's where things get strange. If I install these packages on the host, everything works except for system-config-lvm; however, if I run the same script on a guest, system-config-lvm works as expected.

What happens on the host machine is that the system-config-lvm begins to load, starts to read the initial volumes, then crashes.

---

### Post by matt_fussell2 on 2014-07-01
This is the error output as described above:


```
/usr/share/system-config-lvm/system-config-lvm.py:53: Warning: Attempt to add property GnomeProgram::sm-connect after class was initialised
  gnome.program_init (PROGNAME, VERSION)
/usr/share/system-config-lvm/system-config-lvm.py:53: Warning: Attempt to add property GnomeProgram::show-crash-dialog after class was initialised
  gnome.program_init (PROGNAME, VERSION)
/usr/share/system-config-lvm/system-config-lvm.py:53: Warning: Attempt to add property GnomeProgram::display after class was initialised
  gnome.program_init (PROGNAME, VERSION)
/usr/share/system-config-lvm/system-config-lvm.py:53: Warning: Attempt to add property GnomeProgram::default-icon after class was initialised
  gnome.program_init (PROGNAME, VERSION)
The program 'system-config-lvm.py' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 1973 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Traceback (most recent call last):
  File "/usr/share/system-config-lvm/system-config-lvm.py", line 172, in <module>
    runFullGUI()
  File "/usr/share/system-config-lvm/system-config-lvm.py", line 157, in runFullGUI
    blvm = baselvm(glade_xml, app)
  File "/usr/share/system-config-lvm/system-config-lvm.py", line 105, in __init__
    self.volume_tab_view = Volume_Tab_View(glade_xml, self.lvmm, self.main_win)
  File "/usr/share/system-config-lvm/Volume_Tab_View.py", line 136, in __init__
    self.prepare_tree()
  File "/usr/share/system-config-lvm/Volume_Tab_View.py", line 226, in prepare_tree
    self.mirror_sync_progress.initiate()
  File "/usr/share/system-config-lvm/Volume_Tab_View.py", line 593, in initiate
    if self.crank():
  File "/usr/share/system-config-lvm/Volume_Tab_View.py", line 602, in crank
    self.forked_command.fork()
  File "/usr/share/system-config-lvm/execute.py", line 134, in fork
    os.write(self.fd_write_out, out)
OSError: [Errno 32] Broken pipe
```

This is the error output when using the '--sync' option:

```
/usr/share/system-config-lvm/system-config-lvm.py:53: Warning: Attempt to add property GnomeProgram::sm-connect after class was initialised
  gnome.program_init (PROGNAME, VERSION)
/usr/share/system-config-lvm/system-config-lvm.py:53: Warning: Attempt to add property GnomeProgram::show-crash-dialog after class was initialised
  gnome.program_init (PROGNAME, VERSION)
/usr/share/system-config-lvm/system-config-lvm.py:53: Warning: Attempt to add property GnomeProgram::display after class was initialised
  gnome.program_init (PROGNAME, VERSION)
/usr/share/system-config-lvm/system-config-lvm.py:53: Warning: Attempt to add property GnomeProgram::default-icon after class was initialised
  gnome.program_init (PROGNAME, VERSION)
The program 'system-config-lvm.py' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 1887 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Traceback (most recent call last):
  File "/usr/share/system-config-lvm/system-config-lvm.py", line 172, in <module>
    runFullGUI()
  File "/usr/share/system-config-lvm/system-config-lvm.py", line 157, in runFullGUI
    blvm = baselvm(glade_xml, app)
  File "/usr/share/system-config-lvm/system-config-lvm.py", line 105, in __init__
    self.volume_tab_view = Volume_Tab_View(glade_xml, self.lvmm, self.main_win)
  File "/usr/share/system-config-lvm/Volume_Tab_View.py", line 136, in __init__
    self.prepare_tree()
  File "/usr/share/system-config-lvm/Volume_Tab_View.py", line 226, in prepare_tree
    self.mirror_sync_progress.initiate()
  File "/usr/share/system-config-lvm/Volume_Tab_View.py", line 593, in initiate
    if self.crank():
  File "/usr/share/system-config-lvm/Volume_Tab_View.py", line 602, in crank
    self.forked_command.fork()
  File "/usr/share/system-config-lvm/execute.py", line 134, in fork
    os.write(self.fd_write_out, out)
OSError: [Errno 32] Broken pipe
```

---

### Post by sandyd on 2014-07-01
> **matt_fussell2 said:**
> The error was 'BadAlloc (insufficient resources for operation)'.

What video card are you using?

---

### Post by matt_fussell2 on 2014-07-01
In the case of this test server, it's an intel, however it doesn't seem restricted to a given architecture, as our other server has a low-end nvidia card and it's experiencing the same issue. In continued testing, I did just have KVPM work, so I'm going to try it on our other server and see if I can duplicate the results. This wouldn't be the first time I've had the solution to a problem end up being "use something else".

---

### Post by sandyd on 2014-07-01
Try [http://forums.opensuse.org/showthread.php/389147-X-Error-of-failed-request-BadAlloc-(insufficient-resources](http://forums.opensuse.org/showthread.php/389147-X-Error-of-failed-request-BadAlloc-(insufficient-resources)

---

### Post by matt_fussell2 on 2014-07-02
> **sandyd said:**
> Try [http://forums.opensuse.org/showthread.php/389147-X-Error-of-failed-request-BadAlloc-(insufficient-resources](http://forums.opensuse.org/showthread.php/389147-X-Error-of-failed-request-BadAlloc-(insufficient-resources)

By default, Ubuntu doesn't have an xorg.conf file. I was able to force the server to generate one for me to modify by executing

```
sudo X :1 -configure
```

After modification and a server restart, I'm still getting the same errors out of system-config-lvm. Here's the config file.

```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "Backlight"              # <str>
        #Option     "DRI"                    # <str>
        #Option     "ColorKey"               # <i>
        #Option     "VideoKey"               # <i>
        #Option     "Tiling"                 # [<bool>]
        #Option     "LinearFramebuffer"      # [<bool>]
        #Option     "VSync"                  # [<bool>]
        #Option     "PageFlip"               # [<bool>]
        #Option     "SwapbuffersWait"        # [<bool>]
        #Option     "TripleBuffer"           # [<bool>]
        #Option     "XvPreferOverlay"        # [<bool>]
        #Option     "HotPlug"                # [<bool>]
        #Option     "ReprobeOutputs"         # [<bool>]
        #Option     "XvMC"                   # [<bool>]
        #Option     "ZaphodHeads"            # <str>
        #Option     "VirtualHeads"           # <i>
        #Option     "TearFree"               # [<bool>]
        #Option     "PerCrtcPixmaps"         # [<bool>]
        #Option     "FallbackDebug"          # [<bool>]
        #Option     "DebugFlushBatches"      # [<bool>]
        #Option     "DebugFlushCaches"       # [<bool>]
        #Option     "DebugWait"              # [<bool>]
        #Option     "BufferCache"            # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    BusID       "PCI:0:2:0"
    Option "Videoram" "65536"
    Option "Cachelines" "1980"
    Option "AccelMethod" "XAA"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "kmsdev"                 # <str>
        #Option     "ShadowFB"               # [<bool>]
    Identifier  "Card1"
    Driver      "modesetting"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


```

---

