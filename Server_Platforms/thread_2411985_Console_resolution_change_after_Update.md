---
title: "Console resolution change after Update"
date: 2019-02-06
forum: Server Platforms
---

### Post by seifer2k on 2019-02-06
[COLOR=#000000]Logged onto my server like I do every couple of days in order to check for updates. It said I had 9 and 9 updates, so I ran two commands, like I always did when it said I have updates:[/COLOR]

[COLOR=#000000]sudo apt-get update[/COLOR]
[COLOR=#000000]sudo apt-get upgrade[/COLOR]

[COLOR=#000000]Then I rebooted the server and then, when I completely expected it to say 0 updates, I saw it still had 8 and 8 left. So I scratched my head and did it again. After a reboot, I STILL had 8 and 8.[/COLOR]

[COLOR=#000000]So I did some looking and then found out that big updates like the kernel don't get updated with the two commands I used, so I did:[/COLOR]

[COLOR=#000000]sudo apt-get dist-upgrade[/COLOR]

[COLOR=#000000]Yeah, sure enough, it installed the remaining ones, but now my native CONSOLE does not display correctly on my TV. It's a 26" Samsung LCD TV from 2006 that has a native resolution of 1366x768 that usually works really well with my Windows 98 system running at 1024x768.[/COLOR]

[COLOR=#000000]Now, all I can see is "Not supported mode" on my TV screen. I can still log into the server remotely via PUTTY, but this annoys me.[/COLOR]

[COLOR=#000000]Anyone got a fix OTHER THAN messing with /etc/default/grub ? I've tried that and several reboots and it didn't fix the native console display resolution. I'm trying to set it to 1024x768x24... or VGA mode 792 as found on this page:[/COLOR]
[https://www.pendrivelinux.com/vga-bo...en-resolution/]("https://www.pendrivelinux.com/vga-boot-modes-to-set-screen-resolution/")
[COLOR=#000000]So far, I uncommented GRUB_GFXMODE=1027x768x24 (I changed the value to this), then added GRUB_GFXPAYLOAD_LINUX=1024x768x24[/COLOR]
[COLOR=#000000]Also changed GRUB_CMDLINE_LINUX_DEFAULT="video=0x0792"[/COLOR]
[COLOR=#000000]Saved, then did sudo update-grub followed by a reboot. Didn't fix anything, so I reverted back to the original values.[/COLOR]

[COLOR=#000000]Also, I haven't had a successful reboot command go through and fully restart the system since. Sure, issuing the command kicks me off of PUTTY, and after a few seconds, I can no longer access the PLEX media service or the SAMBA shares. But I've waited over 5 minutes and no reboot of the system happens. Each time, I now have to go press the hard reset switch on the case. Linux seems to boot normally after that, but I cannot monitor any of the normal console line-reports that happen during boot or shutdown since it's no longer outputting a resolution or frequency range that the TV recognizes (60fps). Hell, I'll take 640x480 or 800x600 resolutions at this point just to be able to monitor the console.

[/COLOR]Ok, I just hooked up a Samsung SyncMaster 912N I have lying around for retro gaming on older machines (it's a 4x3 19" monitor with a native screen resolution of 1280 x 2014 with a maximum refresh rate of 75Hz).  Even IT won't show anything on the screen once it passes the spot where it used to switch screen resolutions.  What I mean is, the first few seconds of booting into LINUX, everything's running @640x480 the same as the BIOS and POST screens do.  But after a few seconds, the system used to switch to a resolution where the text was a lot smaller and finer and had colors on the screen for things that passed or something.  I wish I had screenshots.  Now, when it would switch to that smaller text, it just gives me a blank screen and I have no idea how to find out what resolution or refresh rate it's trying to push.

[COLOR=#000000]It still says[/COLOR]
[COLOR=#000000]Welcome to Ubuntu 18.10 (GNU/Linux 4.18.0-14-generic x86_64)[/COLOR]
[COLOR=#000000]If that means anything to anyone.[/COLOR]

---

### Post by #&amp;thj^% on 2019-02-06
Your running a server on a point release(9 months of support), recommend 18.04 LTS.(5 years of support)
**_Ubuntu 18.04 server it is necessary to change the configuration of the relevant GRUB boot loader settings within the /etc/default/grub_**
Reboot your system into GRUB menu. Press "c" key to enter GRUB's command line.
Obtain available console resolution information by executing the following GRUB commands:
```

grub> set pager=1
grub> vbeinfo
```
Press space bar to scroll down. Take a note of your desired resolution *example*. "1024x768"
Once you are booted in the system edit "/etc/default/grub" to include the following settings. _The below GRUB settings will set TTY console to **1024x768 **resolution. _
```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
GRUB_GFXPAYLOAD_LINUX=1024x768

```
naturally change "1024x768" to your desired and available size.
Apply the new GRUB configuration and reboot your system:
```

sudo update-grub
sudo reboot
```

---

### Post by seifer2k on 2019-02-06
I guess I shouldn't be trying to mess with things I don't actually know anything about.  Like, I know that GRUB is a bootloader.  But Ubuntu Server is the only OS installed on the entire system, so I never get any kind of prompt to select a boot image or anything like that.  It usually just goes right into starting Ubuntu Server immediately after system POST.
So I looked into it.  Do I hold down the C button during booting or something?  Somewhere else said hold down Shift, so I tried that and it did nothing.

... OOH!  I held down Escape and it worked.  I got a menu saying "UBUNTU" and "Advanced Ubuntu settings".  I pressed C and I got

```
grub> vbeinfo
List of supported video modes:
Legend: mask/position=red/green/blue/reserved
Adapter 'VESA BIOS Extension Video Driver":
  VBE info:   version: 3.0  OEM software rev: 1.0
              total memory: 32704 KiB
  0x160    0 x    0 x  0 (   0)  Text-only
  0x161    0 x    0 x  0 (   0)  Text-only
  0x162    0 x    0 x  0 (   0)  Text-only
  0x163    0 x    0 x  0 (   0)  Text-only
  0x164    0 x    0 x  0 (   0)  Text-only
  0x165    0 x    0 x  0 (   0)  Text-only
  0x166    0 x    0 x  0 (   0)  Text-only
  0x167    0 x    0 x  0 (   0)  Text-only
  0x168    0 x    0 x  0 (   0)  Text-only
  0x13c 1920 x 1440 x  8 (1920)  Paletted
  0x14d 1920 x 1440 x 16 (3840)  Direct color, mask: 5/6/5/0  pos: 11/5/0/0
  0x15c 1920 x 1440 x 32 (7680)  Direct color, mask: 8/8/8/8  pos: 16/8/0/24
  0x13a 1600 x 1200 x  8 (1600)  Paletted
  0x14b 1600 x 1200 x 16 (3200)  Direct color, mask: 5/6/5/0  pos: 11/5/0/0
  0x15z 1600 x 1200 x 32 (6400)  Direct color, mask: 8/8/8/8  pos: 16/8/0/24
  0x107 1280 x 1024 x  8 (1280)  Paletted
  0x11a 1280 x 1024 x 16 (2560)  Direct color, mask: 5/6/5/0  pos: 11/5/0/0
  0x11b 1280 x 1024 x 32 (5120)  Direct color, mask: 8/8/8/8  pos: 16/8/0/24
  0x105 1024 x  768 x  8 (1024)  Paletted
  0x117 1024 x  768 x 16 (2048)  Direct color, mask: 5/6/5/0  pos: 11/5/0/0
  0x118 1024 x  768 x 32 (4096)  Direct color, mask: 8/8/8/8  pos: 16/8/0/24
  0x112  640 x  480 x 32 (2560)  Direct color, mask: 8/8/8/8  pos: 16/8/0/24
  0x114  800 x  600 x 16 (1600)  Direct color, mask: 5/6/5/0  pos: 11/5/0/0
  0x115  800 x  600 x 32 (3200)  Direct color, mask: 8/8/8/8  pos: 16/8/0/24
  0x101  640 x  480 x  8 ( 640)  Paletted
  0x103  800 x  600 x  8 ( 832)  Paletted
  0x111  640 x  480 x 16 (1280)  Direct color, mask: 5/6/5/0  pos: 11/5/0/0
  EDID version: 1.3
    Preferred mode:  1360x768
grub>
```

Made changes as you said.  I changed
[FONT=courier new]GRUB_CMDLINE_LINUX_DEFAULT="quiet spash"[/FONT]
to
[FONT=courier new]GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
[/FONT]
And then added the line 
[FONT=courier new]GRUB_GFXPAYLOAD_LINUX=1360x768[/FONT]

And rebooted (still have to manually push the reset switch or the power button to get it to reboot).

No change.  Posting contents of /etc/default/grub

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
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
#GRUB_GFXMODE=640x480
GRUB_GFXPAYLOAD_LINUX=1360x768

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by #&amp;thj^% on 2019-02-07
A few things I noted from your given information is that your resolution (1360x768) dose not show up in the "vbeinfo" you have shown me.(BTW Thanks for posting that) It dose however show this at the bottom "Preferred mode:  1360x768" and I don't know where that came from.
So first it would be nice to see if one of the available console resolution's would work like "1280x1024x32".(Exactly like I show)
Following the above steps I mentioned earlier. (Post#2)
If that still fails then let's have a look at:
```
cat  /etc/grub.d/00_header
```
please use code tags with this one, thanks.
I have a 14 hour day today so i won't be around today but I will check back when i get a free minute.:)
Your no restart/hard reset is another matter to be continued in another thread.

---

### Post by seifer2k on 2019-02-07
EDIT:  The following post was made while you were making your reply and will be left as-is as it has lots of information.  The post after this one will address your reply directly.

Went back into the grub file this morning and made a simple change, based on what I was reading in the commented out sections - more specifically, the part that said 

[FONT=courier new]# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command 'vbeinfo'[/FONT]

Which as we'll note you told me to do and I had the output.  NOWHERE in there did it say it could put out 1360x768, so I changed the entry in grub to 

[FONT=courier new]GRUB_GFXPAYLOAD_LINUX=1024x768x32[/FONT]

And restarted.  NOW I can see something on my screen, but it's locked at a specific point.  At least I'm able to see something of the boot process of Ubuntu now.  Here's what's frozen on my console screen:
```

[    1.813500] NET: Registered protocol family 17
[    1.822247] Key type dns_resolver registered
[    1.831074] RAS: Correctable Errors collector initialized.
[    1.839670] microcode: sig=0x10676, pf=0x40, revision=0x60f
[    1.848283] microcode: Microcode Update Driver: v2.2.
[    1.848293] sched_clock: Marking stable (1848278454, 0)->(1932037642, -83759188)
[    1.865450] registered taskstats version 1
[    1.873910] Loading compiled-in X.509 certificates
[    1.885585] Loaded X.509 cert 'Build time autogenerated kernel key: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx'
[    1.894504] zswap: loaded using pool lzo/zbud
[    1.907405] Key type big_key registered
[    1.916065] tsc: Refined TSC clocksource calibration: 2999.999 MHz
[    1.920030] Key type trusted registered
[    1.924821] clocksource: rsc: mask: 0xffffffffffffffff max_cycles: 0x2b3e44b2357, max_idle_ns: 440795324996 ns
[    1.935549] Key type trusted registered
[    1.951714] clocksource: Switched to clocksource tsc
[    1.951715] AppArmor: AppArmor sha1 policy hashing enabled
[    1.951727] ima: No TPM chip found, activating TPM-bypass! (rc=-19)
[    1.978879] ima: Allocated has algorithm: sha1
[    1.987748] evm: Initialising EVM extended attributes:
[    1.996562] evm: security.selinux
[    2.005301] evm: security.SMACK64
[    2.013956] evm: security.SMACK64EXEC
[    2.022507] evm: security.SMACK64TRANSMUTE
[    2.030957] evm: security.SMACK64MMAP
[    2.039197] evm: security.apparmor
[    2.047235] evm: security.ima
[    2.055092] evm: security.capability
[    2.062847] evm: HMAC attrs: 0x1
[    2.070820]   Magic number: 7:15:586
[    2.078574] rtc_cmos 00:01: setting system clock to 2019-02-07 14:33:22 UTC (1549550002)
[    2.091003] Freeing unused kernel image memory: 2456K
[    2.112012] Write protecting the kernel read-only date: 20480k
[    2.120691] Freeing unused kernel image memory: 2008K
[    2.129005] Freeing unused kernel image memory: 1792K
[    2.148073] x86/mm: Checked W+X mappings: passed, no W+X pages found.
[    2.155692] x86/mm: Checking user space page tables
[    2.174149] x86/mm: Checked W+X mappings: passed, no W+X pages found.
Loading, please wait...
starting version 239
[    2.334257] pci 0000:00:00.0: Intel G41 Chipset
[    2.336029] usb 5-1: new full-speed USB device number 2 using uhci_hcd
[    2.344059] pci 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    2.358307] gpio_ich: GPIO from 462 to 511 on gpio_ich
[    2.358517] pci 0000:00:00.0: detected 32768K stolen memory
[    2.359100] ATL1E 0000:01:00.0 enp1s0: renamed from eth0
[    2.380583] fb: switching to inteldrmfb from VESA VGA

```

I can still log into the system through PUTTY and it still runs SAMBA and PLEX just fine.  It just worries me that I cannot access the direct console, as I use this to monitor the server during startup and shutdown.  I've hit the keyboard's enter key a bunch of times and it changes nothing on that screen.  Maybe that last line is a clue as to what's happening.

[FONT=courier new][    2.380583] fb: switching to inteldrmfb from VESA VGA

[/FONT]

---

### Post by seifer2k on 2019-02-07
Ok, so yeah, we both noticed that vbeinfo stuff.  The native resolution of the Samsung HDTV, which I bought back in 2006 is a 1080i/720p TV that just happens to have a VGA (15-pin DSUB) input on the back so I can use it in PC mode.  The NATIVE resolution of the TV screen is 1360x768 and I can verify that by hooking up an older Windows XP system and that's the highest screen resolution that the card detects it can put out to the TV natively.  The video card in use there is an ATI Radeon 9550xl.

In the server's case, it's a built-in G41 Express graphics chip.  Since the system isn't exactly going to be doing anything graphically, I saw no need to install a discrete graphics card.  So with that Samsung TV hooked up to the system, of course it would report back that its native resolution is 1360x768, as reported by vbeinfo.

But since you asked for it, here's the contents of that file [FONT=courier new]/etc/grub.d/00_header[/FONT]
And I can see why you wanted me to put it in a code window, both for font reasons and because it's so long...

```
#! /bin/sh
set -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009,2010  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

prefix="/usr"
exec_prefix="/usr"
datarootdir="/usr/share"
grub_lang=`echo $LANG | cut -d . -f 1`
grubdir="`echo "/boot/grub" | sed 's,//*,/,g'`"
quick_boot="1"

export TEXTDOMAIN=grub
export TEXTDOMAINDIR="${datarootdir}/locale"

. "$pkgdatadir/grub-mkconfig_lib"

# Do this as early as possible, since other commands might depend on it.
# (e.g. the `loadfont' command might need lvm or raid modules)
for i in ${GRUB_PRELOAD_MODULES} ; do
  echo "insmod $i"
done

if [ "x${GRUB_DEFAULT}" = "x" ] ; then GRUB_DEFAULT=0 ; fi
if [ "x${GRUB_DEFAULT}" = "xsaved" ] ; then GRUB_DEFAULT='${saved_entry}' ; fi
if [ "x${GRUB_TIMEOUT}" = "x" ] ; then GRUB_TIMEOUT=5 ; fi
if [ "x${GRUB_GFXMODE}" = "x" ] ; then GRUB_GFXMODE=auto ; fi

if [ "x${GRUB_DEFAULT_BUTTON}" = "x" ] ; then GRUB_DEFAULT_BUTTON="$GRUB_DEFAUL$
if [ "x${GRUB_DEFAULT_BUTTON}" = "xsaved" ] ; then GRUB_DEFAULT_BUTTON='${saved$
if [ "x${GRUB_TIMEOUT_BUTTON}" = "x" ] ; then GRUB_TIMEOUT_BUTTON="$GRUB_TIMEOU$

cat << EOF
if [ -s \$prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
EOF
cat <<EOF
if [ "\${initrdfail}" = 2 ]; then
   set initrdfail=
elif [ "\${initrdfail}" = 1 ]; then
   set next_entry="\${prev_entry}"
   set prev_entry=
   save_env prev_entry
   if [ "\${next_entry}" ]; then
      set initrdfail=2
   fi
fi
EOF
if [ "x$GRUB_BUTTON_CMOS_ADDRESS" != "x" ]; then
    cat <<EOF
if cmostest $GRUB_BUTTON_CMOS_ADDRESS ; then
   set default="${GRUB_DEFAULT_BUTTON}"
elif [ "\${next_entry}" ] ; then
   set default="\${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="${GRUB_DEFAULT}"
fi
EOF
else
    cat <<EOF
if [ "\${next_entry}" ] ; then
   set default="\${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="${GRUB_DEFAULT}"
fi
EOF
fi
cat <<EOF

if [ x"\${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "\${prev_saved_entry}" ]; then
  set saved_entry="\${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "\${boot_once}" ]; then
    saved_entry="\${chosen}"
    save_env saved_entry
  fi
}
EOF

cat <<"EOF"
function initrdfail {
    if [ -n "${have_grubenv}" ]; then if [ -n "${partuuid}" ]; then
      if [ -z "${initrdfail}" ]; then
        set initrdfail=1
        if [ -n "${boot_once}" ]; then
          set prev_entry="${default}"
          save_env prev_entry
        fi
      fi
      save_env initrdfail
    fi; fi
}
EOF

if [ "$quick_boot" = 1 ]; then
    cat <<EOF
function recordfail {
  set recordfail=1
EOF

  check_writable () {
    abstractions="$(grub-probe --target=abstraction "${grubdir}")"
    for abstraction in $abstractions; do
      case "$abstraction" in
        diskfilter | lvm)
          cat <<EOF
  # GRUB lacks write support for $abstraction, so recordfail support is disable$
EOF

        return 1
        ;;
    esac

    cat <<EOF
  if [ -n "\${have_grubenv}" ]; then if [ -z "\${boot_once}" ]; then save_env r$
EOF
  }

  if ! check_writable; then
    recordfail_broken=1
  fi

  cat <<EOF
}
EOF
fi

cat <<EOF
function load_video {
EOF
if [ -n "${GRUB_VIDEO_BACKEND}" ]; then
    cat <<EOF
  insmod ${GRUB_VIDEO_BACKEND}
EOF
else
# If all_video.mod isn't available load all modules available
# with versions prior to introduction of all_video.mod
cat <<EOF
  if [ x\$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
EOF
fi
cat <<EOF
}

EOF

serial=0;
gfxterm=0;
for x in ${GRUB_TERMINAL_INPUT} ${GRUB_TERMINAL_OUTPUT}; do
    if [ xserial = "x$x" ]; then
        serial=1;
    fi
    if [ xgfxterm = "x$x" ]; then
        gfxterm=1;
    fi
done

if [ "x$serial" = x1 ]; then
    if [ "x${GRUB_SERIAL_COMMAND}" = "x" ] ; then
        grub_warn "$(gettext "Requested serial terminal but GRUB_SERIAL_COMMAND$
        GRUB_SERIAL_COMMAND=serial
    fi
    echo "${GRUB_SERIAL_COMMAND}"
fi

if [ "x$gfxterm" = x1 ]; then
    if [ -n "$GRUB_FONT" ] ; then
       # Make the font accessible
       prepare_grub_to_access_device `${grub_probe} --target=device "${GRUB_FON$
    cat << EOF
if loadfont `make_system_path_relative_to_its_root "${GRUB_FONT}"` ; then
EOF
    else
        for dir in "${pkgdatadir}" "`echo '/boot/grub' | sed "s,//*,/,g"`" /usr$
            for basename in unicode unifont ascii; do
                path="${dir}/${basename}.pf2"
                if is_path_readable_by_grub "${path}" > /dev/null ; then
                    font_path="${path}"
                else
                    continue
                fi
                break 2
            done
        done
        if [ -n "${font_path}" ] ; then
    cat << EOF
if [ x\$feature_default_font_path = xy ] ; then
   font=unicode
else
EOF
                # Make the font accessible
                prepare_grub_to_access_device `${grub_probe} --target=device "$$
    cat << EOF
    font="`make_system_path_relative_to_its_root "${font_path}"`"
fi


if loadfont \$font ; then
EOF
            else
    cat << EOF
if loadfont unicode ; then
EOF
            fi
        fi

    cat << EOF
  set gfxmode=${GRUB_GFXMODE}
  load_video
  insmod gfxterm
EOF

# Gettext variables and module
if [ "x${LANG}" != "xC" ] &&  [ "x${LANG}" != "x" ]; then
  cat << EOF
  set locale_dir=\$prefix/locale
  set lang=${grub_lang}
  insmod gettext
EOF
fi

cat <<EOF
fi
EOF
fi

case x${GRUB_TERMINAL_INPUT} in
  x)
    # Just use the native terminal
  ;;
  x*)
    cat << EOF
terminal_input ${GRUB_TERMINAL_INPUT}
EOF
  ;;
esac

if [ "x$gfxterm" = x1 ]; then
    if [ "x$GRUB_THEME" != x ] && [ -f "$GRUB_THEME" ] \
        && is_path_readable_by_grub "$GRUB_THEME"; then
        gettext_printf "Found theme: %s\n" "$GRUB_THEME" >&2

        prepare_grub_to_access_device `${grub_probe} --target=device "$GRUB_THE$
        cat << EOF
insmod gfxmenu
EOF
        themedir="`dirname "$GRUB_THEME"`"
        for x in "$themedir"/*.pf2 "$themedir"/f/*.pf2; do
            if [ -f "$x" ]; then
                cat << EOF
loadfont (\$root)`make_system_path_relative_to_its_root $x`
EOF
            fi
        done
        if [ x"`echo "$themedir"/*.jpg`" != x"$themedir/*.jpg" ] || [ x"`echo "$
            cat << EOF
insmod jpeg
EOF
        fi
        if [ x"`echo "$themedir"/*.png`" != x"$themedir/*.png" ]; then
            cat << EOF
insmod png
EOF
        fi
        if [ x"`echo "$themedir"/*.tga`" != x"$themedir/*.tga" ]; then
            cat << EOF
insmod tga
EOF
        fi
[][][][][][] #(<-- a green block is here for some reason)
        cat << EOF
set theme=(\$root)`make_system_path_relative_to_its_root $GRUB_THEME`
export theme
EOF
    elif [ "x$GRUB_BACKGROUND" != x ] && [ -f "$GRUB_BACKGROUND" ] \
            && is_path_readable_by_grub "$GRUB_BACKGROUND"; then
        gettext_printf "Found background: %s\n" "$GRUB_BACKGROUND" >&2
        case "$GRUB_BACKGROUND" in
            *.png)         reader=png ;;
            *.tga)         reader=tga ;;
            *.jpg|*.jpeg)  reader=jpeg ;;
            *)             gettext "Unsupported image format" >&2; echo >&2; ex$
        esac
        prepare_grub_to_access_device `${grub_probe} --target=device "$GRUB_BAC$
        cat << EOF
insmod $reader
background_image -m stretch `make_system_path_relative_to_its_root "$GRUB_BACKG$
EOF
    fi
fi

make_timeout ()
{
    cat << EOF
if [ "\${recordfail}" = 1 ] ; then
  set timeout=${GRUB_RECORDFAIL_TIMEOUT:-30}
else
EOF
    if [ "x${3}" != "x" ] ; then
        timeout="${2}"
        style="${3}"
    elif [ "x${1}" != "x" ] && \
         ([ "$quick_boot" = 1 ] || [ "x${1}" != "x0" ]) ; then
        # Handle the deprecated GRUB_HIDDEN_TIMEOUT scheme.
        timeout="${1}"
        if [ "x${2}" != "x0" ] ; then
            grub_warn "$(gettext "Setting GRUB_TIMEOUT to a non-zero value when$
        fi
        if [ "x${GRUB_HIDDEN_TIMEOUT_QUIET}" = "xtrue" ] ; then
            style="hidden"
            verbose=
        else
            style="countdown"
            verbose=" --verbose"
        fi
    else
        # No hidden timeout, so treat as GRUB_TIMEOUT_STYLE=menu
        timeout="${2}"
        style="menu"
    fi
    cat << EOF
  if [ x\$feature_timeout_style = xy ] ; then
    set timeout_style=${style}
    set timeout=${timeout}
EOF
    if [ "x${style}" = "xmenu" ] ; then
        cat << EOF
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=${timeout}
EOF
    else
        cat << EOF
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep${verbose} --interruptible ${timeout} ; then
    set timeout=0
EOF
    fi
    cat << EOF
  fi
fi
EOF
if [ "$recordfail_broken" = 1 ]; then
  cat << EOF
if lsefi; then
  set timeout=${GRUB_RECORDFAIL_TIMEOUT:-30}
  if [ x\$feature_timeout_style = xy ] ; then
    set timeout_style=menu
  fi
fi
EOF
fi
}

if [ "x$GRUB_BUTTON_CMOS_ADDRESS" != "x" ]; then
    cat <<EOF
if cmostest $GRUB_BUTTON_CMOS_ADDRESS ; then
EOF
make_timeout "${GRUB_HIDDEN_TIMEOUT_BUTTON}" "${GRUB_TIMEOUT_BUTTON}" "${GRUB_T$
echo else
make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}" "${GRUB_TIMEOUT_STYLE}"
echo fi
else
make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}" "${GRUB_TIMEOUT_STYLE}"
fi

if [ "x$GRUB_BUTTON_CMOS_ADDRESS" != "x" ] && [ "x$GRUB_BUTTON_CMOS_CLEAN" = "x$
    cat <<EOF
cmosclean $GRUB_BUTTON_CMOS_ADDRESS
EOF
fi

# Play an initial tune
if [ "x${GRUB_INIT_TUNE}" != "x" ] ; then
  echo "play ${GRUB_INIT_TUNE}"
fi

if [ "x${GRUB_BADRAM}" != "x" ] ; then
  echo "badram ${GRUB_BADRAM}"
fi

```

---

### Post by #&amp;thj^% on 2019-02-08
I have no doubts that your TV has a NATIVE resolution of "1360x768", but we are in the linux world now and have to play by those rules. ;)
This may prove to be a bit trial and error for a bit till we hit the sweet spot.
but before we go on, can I see one more slice of info from:
```
cat /boot/grub/grub.cfg
```

---

### Post by seifer2k on 2019-02-09
I'll give you everything you want, but in the process of logging into the server to get the contents of that file, there were
[FONT=courier new]8 packages can be updated.
0 updates are security updates.
***System Restart Required***[/FONT]

So, I'll put the contents of the file down in this post for reference, but I ran the updates with
[FONT=courier new]sudo apt-get update
sudo apt-get upgrade[/FONT]

And after a hard reboot, I have NO IDEA what changed, but now the console is working.  And not only is it working properly, but the text was all squished in 4:3 display mode, so I switched the TV to 16:9 display mode and it looks proper.  I've attached a picture showing the console available now.  The TV reports it's getting a signal at 1360x768 now, so that explains that.

```
heath@ubuntusrvr:~$ cat /boot/grub/grub.cfg#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${initrdfail}" = 2 ]; then
   set initrdfail=
elif [ "${initrdfail}" = 1 ]; then
   set next_entry="${prev_entry}"
   set prev_entry=
   save_env prev_entry
   if [ "${next_entry}" ]; then
      set initrdfail=2
   fi
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function initrdfail {
    if [ -n "${have_grubenv}" ]; then if [ -n "${partuuid}" ]; then
      if [ -z "${initrdfail}" ]; then
        set initrdfail=1
        if [ -n "${boot_once}" ]; then
          set prev_entry="${default}"
          save_env prev_entry
        fi
      fi
      save_env initrdfail
    fi; fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

terminal_input console
terminal_output console
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
        set gfxpayload="${1}"
        if [ "${1}" = "keep" ]; then
                set vt_handoff=vt.handoff=1
        else
                set vt_handoff=
        fi
}
set linux_gfx_mode=1024x768x32
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-a41195c9-1ac7-45b0-bac4-3268b17f342e' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  a41195c9-1ac7-45b0-bac4-3268b17f342e
        else
          search --no-floppy --fs-uuid --set=root a41195c9-1ac7-45b0-bac4-3268b17f342e
        fi
        linux   /boot/vmlinuz-4.18.0-15-generic root=UUID=a41195c9-1ac7-45b0-bac4-3268b17f342e ro  maybe-ubiquity
        initrd  /boot/initrd.img-4.18.0-15-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-a41195c9-1ac7-45b0-bac4-3268b17f342e' {
        menuentry 'Ubuntu, with Linux 4.18.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.18.0-15-generic-advanced-a41195c9-1ac7-45b0-bac4-3268b17f342e' {
                recordfail
                load_video
                gfxmode $linux_gfx_mode
                insmod gzio
                if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
                insmod part_gpt
                insmod ext2
                set root='hd0,gpt2'
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  a41195c9-1ac7-45b0-bac4-3268b17f342e
                else
                  search --no-floppy --fs-uuid --set=root a41195c9-1ac7-45b0-bac4-3268b17f342e
                fi
                echo    'Loading Linux 4.18.0-15-generic ...'
                linux   /boot/vmlinuz-4.18.0-15-generic root=UUID=a41195c9-1ac7-45b0-bac4-3268b17f342e ro  maybe-ubiquity
                echo    'Loading initial ramdisk ...'
                initrd  /boot/initrd.img-4.18.0-15-generic
        }
        menuentry 'Ubuntu, with Linux 4.18.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.18.0-15-generic-recovery-a41195c9-1ac7-45b0-bac4-3268b17f342e' {
                recordfail
                load_video
                insmod gzio
                if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
                insmod part_gpt
                insmod ext2
                set root='hd0,gpt2'
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  a41195c9-1ac7-45b0-bac4-3268b17f342e
                else
                  search --no-floppy --fs-uuid --set=root a41195c9-1ac7-45b0-bac4-3268b17f342e
                fi
                echo    'Loading Linux 4.18.0-15-generic ...'
                linux   /boot/vmlinuz-4.18.0-15-generic root=UUID=a41195c9-1ac7-45b0-bac4-3268b17f342e ro recovery nomodeset
                echo    'Loading initial ramdisk ...'
                initrd  /boot/initrd.img-4.18.0-15-generic
        }
        menuentry 'Ubuntu, with Linux 4.18.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.18.0-14-generic-advanced-a41195c9-1ac7-45b0-bac4-3268b17f342e' {
                recordfail
                load_video
                gfxmode $linux_gfx_mode
                insmod gzio
                if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
                insmod part_gpt
                insmod ext2
                set root='hd0,gpt2'
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  a41195c9-1ac7-45b0-bac4-3268b17f342e
                else
                  search --no-floppy --fs-uuid --set=root a41195c9-1ac7-45b0-bac4-3268b17f342e
                fi
                echo    'Loading Linux 4.18.0-14-generic ...'
                linux   /boot/vmlinuz-4.18.0-14-generic root=UUID=a41195c9-1ac7-45b0-bac4-3268b17f342e ro  maybe-ubiquity
                echo    'Loading initial ramdisk ...'
                initrd  /boot/initrd.img-4.18.0-14-generic
        }
        menuentry 'Ubuntu, with Linux 4.18.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.18.0-14-generic-recovery-a41195c9-1ac7-45b0-bac4-3268b17f342e' {
                recordfail
                load_video
                insmod gzio
                if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
                insmod part_gpt
                insmod ext2
                set root='hd0,gpt2'
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  a41195c9-1ac7-45b0-bac4-3268b17f342e
                else
                  search --no-floppy --fs-uuid --set=root a41195c9-1ac7-45b0-bac4-3268b17f342e
                fi
                echo    'Loading Linux 4.18.0-14-generic ...'
                linux   /boot/vmlinuz-4.18.0-14-generic root=UUID=a41195c9-1ac7-45b0-bac4-3268b17f342e ro recovery nomodeset
                echo    'Loading initial ramdisk ...'
                initrd  /boot/initrd.img-4.18.0-14-generic
        }
        menuentry 'Ubuntu, with Linux 4.18.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.18.0-13-generic-advanced-a41195c9-1ac7-45b0-bac4-3268b17f342e' {
                recordfail
                load_video
                gfxmode $linux_gfx_mode
                insmod gzio
                if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
                insmod part_gpt
                insmod ext2
                set root='hd0,gpt2'
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  a41195c9-1ac7-45b0-bac4-3268b17f342e
                else
                  search --no-floppy --fs-uuid --set=root a41195c9-1ac7-45b0-bac4-3268b17f342e
                fi
                echo    'Loading Linux 4.18.0-13-generic ...'
                linux   /boot/vmlinuz-4.18.0-13-generic root=UUID=a41195c9-1ac7-45b0-bac4-3268b17f342e ro  maybe-ubiquity
                echo    'Loading initial ramdisk ...'
                initrd  /boot/initrd.img-4.18.0-13-generic
        }
        menuentry 'Ubuntu, with Linux 4.18.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.18.0-13-generic-recovery-a41195c9-1ac7-45b0-bac4-3268b17f342e' {
                recordfail
                load_video
                insmod gzio
                if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
                insmod part_gpt
                insmod ext2
                set root='hd0,gpt2'
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  a41195c9-1ac7-45b0-bac4-3268b17f342e
                else
                  search --no-floppy --fs-uuid --set=root a41195c9-1ac7-45b0-bac4-3268b17f342e
                fi
                echo    'Loading Linux 4.18.0-13-generic ...'
                linux   /boot/vmlinuz-4.18.0-13-generic root=UUID=a41195c9-1ac7-45b0-bac4-3268b17f342e ro recovery nomodeset
                echo    'Loading initial ramdisk ...'
                initrd  /boot/initrd.img-4.18.0-13-generic
        }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
heath@ubuntusrvr:~$
```
[ATTACH=CONFIG]282443[/ATTACH]

I guess one of the updates updated the graphics driver or something?  Maybe it was a bug that cropped up in a previous update that just got fixed?  I don't know.  I'm just glad it's back up and working again.  NOW we can begin the process of tracking down the shutdown problem.  Thanks a bunch!

---

### Post by #&amp;thj^% on 2019-02-09
Yes! we like it when things auto-magically fix them self.
I can see why it wasn't previously working though:
```

function gfxmode {
        set gfxpayload="${1}"
        if [ "${1}" = "keep" ]; then
                set vt_handoff=vt.handoff=1
        else
                set vt_handoff=
        fi
}
**set linux_gfx_mode=1024x768x32**
```
with this "set linux_gfx_mode=1024x768x32" is fighting your native "1360x768"
Where yours shows:
```
set gfxpayload="${1}"
        if [ "${1}" = "keep" ]; then
```
It would have shown a change of:
```

**set gfxpayload=1360x768**
        if [ "${1}" = "keep" ]; then
```
these are things just to "note", do not change anything now it's working.
Glad things are working now. :)

---

### Post by seifer2k on 2019-02-09
Well, all the lines that reference gfx (Graphics) confused me, as this is Ubuntu Server using only a command-line interface, so in theory it's text-only and usually the term "graphics" only applies to non-text stuff, like a GUI.  I mean, the name itself, Graphical User Interface kinda implies it.
But even if that wasn't the case, the TV accepts 1024x768x32 from all of my Windows PCs just fine, so why would that be any kind of issue?  I've verified it will accept 1360x768, 1024x768, 800x600, and 640x480 via VGA in PC mode, as well as standard 1080i, 720p, 480p, and 480i signals via HDMI from my PS3.
And besides that, I never messed with, or even knew anything about, these GRUB configuration files or settings.  The system was working prior to an update, then wasn't working.  Now, with another update, it's working again.  I'm under the impression it was a driver issue or an underlying problem I'm not aware of inside the graphics subsystem, judging from how the system ran right up to the point where it said it was handing over video control to [COLOR=#000000][FONT=&quot]inteldrmfb from VESA VGA[/FONT][/COLOR].  I guess I should read up on what inteldrmfb is and what it does.

---

