---
title: "Server with encrypted file system"
date: 2008-04-28
forum: Server Platforms
---

### Post by tazeat on 2008-04-28
**The goal:**
I want a server to be able to boot up on its own and allow me to remotely connect (ssh), mount the encrypted file system, and start the servers within the encrypted file system.

**What I have:**
I have 8.04 server edition installed and running.

I manually set up partition table:
/boot 200mb ext3
/     2gb   ext3

Encrypted LVM 20gb
1gb Encrypted swap
19gb mounted at /encrypted

**The problem:**
It wants to mount the encrypted file systems while its booting.
I want to wait until I am already booted up and I want to start manually.

**What I want:**
Preferably I would like to be able to just launch a script ./mountencrypted or something.

Any idea how to accomplish this?

I can't seem to figure out how to get the volumes not to mount on boot. It always asks me for the passphrase...

Thanks, any help in the right direction would be appreciated!

---

### Post by Brazen on 2008-04-28
remove the mount point from fstab (putting a '#' at the beginning of the line would suffice).

---

### Post by tazeat on 2008-04-28
I tried that, I commented out both entries in /etc/fstab and the one entry in /etc/crypttab...

Still asks when I boot.

The partitions are not mounted at least, but it still asks for the password.

---

### Post by tazeat on 2008-04-28
Once the system boots and they are not mounted you can do the normal sudo mount command and get it added and it never asks for the passphrase.

So obviously something is loaded that asks for the passphrase then it stores it... what do I need to remove from startup to save for later to start?

---

### Post by tazeat on 2008-04-28
This is driving me absolutely nuts there is nothing in init.d, there is nothing in my fstab/crypttab, but somehow someone is running "cryptsetup luksOpen /dev/sda3 sda3_crypt" on boot. I can't find it. Surely someone know how ubuntu sets it up in the installer *grr*


I cant even close it:

```
theadmin@testcomputer:~$ sudo cryptsetup status sda3_crypt
/dev/mapper/sda3_crypt is active:
  cipher:  aes-cbc-essiv:sha256
  keysize: 256 bits
  device:  /dev/sda3
  offset:  2056 sectors
  size:    34778669 sectors
  mode:    read/write
theadmin@testcomputer:~$ sudo cryptsetup luksClose sda3_crypt
Command failed: Device busy
theadmin@testcomputer:~$ mount
/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sda1 on /boot type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
```

---

### Post by tazeat on 2008-04-28
W00t fixed it, it had to do with the boot image....

Make sure your fstab and crypttab are clean of encrypted volumes.

Then change your /boot/grub/menu.lst

find the kernel line, should be:
```
kernel          /vmlinuz-2.6.24-16-server root=UUID=bunch0numbers ro quiet splash
```

Change it to
```
kernel          /vmlinuz-2.6.24-16-server root=/dev/sda2 ro quiet splash
```
(Or wherever your / is mounted to, it didnt like the uuid after this next step)

Then do:
```
sudo update-initramfs -u
```

Let it do its thing, voila, no more begging for my password :D

---

### Post by hyper_ch on 2008-04-28
is it a server you have physically access to?

---

### Post by tazeat on 2008-04-28
At the moment yes, but I won't in the future, it is going to be installed aand controlled remotely.

---

### Post by theparanoidone on 2008-04-30
We are trying to accomplish a similar setup.

I followed your instructions and now it boots without asking for the pass...

but, how do I mount these partitions easily if I had to comment them out of fstab and crypttab?

What I mean to say is... now that it has booted... how do we mount the encrypted swap sda2_crypt ... and the encrypted files on sda3_crypt  (ext3)?

---

### Post by theparanoidone on 2008-04-30
Okay... figured a few more things out... although the following script (/etc/init.d/cryptdisks start) is helpful... either I don't know how to use it properly, or it's got a small glitch.  I've split this response up into two parts... an explanation, and a solution... skip to the solution if in a hurry.

Explanation
-----------
 
/etc/init.d/cryptdisks start

The above file should parse, and it does parse:
/etc/default/cryptdisks

Inside the above file is an option to turn off cryptdisk booting:
CRYPTDISKS_ENABLE=No

Well... this is great for boot time... but now what happens after the system is booted and you want to run???:
/etc/init.d/cryptdisks start

It will not execute... why?  Because it is set to check
/etc/default/cryptdisks --> then check -->
CRYPTDISKS_ENABLE=No --> If no.. then quit.

Therefore, the script will not work for post booting easy cryptdisk setup.

Furthermore, /etc/fstab is set by default to load your encrypted file system and check (fsck) your drive for errors.  However, you can't mount an encrypted drive if the cryptsetup hasn't run... and you can't error check a drive for errors while it's encrypted.

Therefore, you must update your fstab to tell it noauto boot, and no file check if you intend to use the CRYPTDISKS_ENABLE=No option.

After you have made these changes... only then will you be able to boot without launching the encrypted drives at boot time.


SOLUTION
--------

For our purpose, we wanted the following setup
/ (ext3) 8gb
swap (encrypted) 2gb   NOPASSWORD NEEDED... JUST RANDOM
/encrypted (encrypted) 100gb   PASSWORD NEEDED


The system should boot fine without swap or the /encrypted folder... these we wanted to turn on after boot.  This is great for remote management so the system can still boot... but also protect critical database files.


## Note... we could only get the Ubuntu installer to work 
## by assigning a password to the swap... and then 
## removing it later *after* installation. So if your running
## a new install... assign a password to both swap and /encrypted

## Now... after install.. let's fix swap
## Notice the swap lines to remove the password
## /dev/urandom... again URANDOM...as in "U"... not RANDOM.
## 
cat /etc/crypttab 

```

sda2_crypt /dev/disk/by-uuid/8683c2eb-c658-4701-99bf-2a122f47774c /dev/urandom swap,size=256
sda3_crypt /dev/disk/by-uuid/7f7f9575-3494-4115-bf67-718fd0136afa none luks

```

## Next run to help remove the password and accept the new random one

update-initramfs -u



## Next Turn off crypt booting
## CRYPTDISKS_ENABLE=No

cat /etc/default/cryptdisks 

```

# Run cryptdisks at startup ?
CRYPTDISKS_ENABLE=No

# Mountpoints to mount, before starting cryptsetup. This is useful for
# keyfiles on removable media. Seperate mountpoints by space.
CRYPTDISKS_MOUNT=""

# Default check script, see /lib/cryptsetup/checks/
# Takes effect, if the 'check' option is set in crypttab without a value
CRYPTDISKS_CHECK=vol_id

# Default precheck script, see 
# Takes effect, if the 'precheck' option is set in crypttab without a value
CRYPTDISKS_PRECHECK=

# Default timeout in seconds for password prompt
# Takes effect, if the 'timeout' option is set in crypttab without a value
CRYPTDISKS_TIMEOUT=180

```


## Next update your /etc/fstab /encrypted mount point
## Add the "noauto"
## Change the ending 2 or 1 --> to 0

cat /etc/fstab

```

/dev/mapper/sda3_crypt /encrypted    ext3    defaults,noauto        0       0

```


## Make a new initscript copy for post encrypted drive booting:
## I've called it /etc/init.d/cryptdisks-post
##
## I've changed a line of code in it to point to:
##   . /lib/cryptsetup/cryptdisks.functions-post
##
## So you can use my file or update the one line yourself
##
## Make sure it's executable... but do not add to your 
## default boot startup (or that will defeat the purpose)
## TO LINK PROPERLY... Call this new file:
## /etc/init.d/cryptdisks-post

```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          cryptdisks
# Required-Start:    checkroot
# Required-Stop:     umountroot
# Should-Start:      udev devfsd raid2 mdadm lvm evms
# Should-Stop:       udev devfsd raid2 mdadm lvm evms
# Default-Start:     S
# Default-Stop:      0 6
# Short-Description: Setup remaining encrypted block devices.
# Description:
### END INIT INFO

set -e 

INITSTATE="remaining"
LOUD="yes"

if [ -r /lib/cryptsetup/cryptdisks.functions ]; then
        . /lib/cryptsetup/cryptdisks.functions-post
else
        exit 0
fi

case "$1" in
start)
        do_start
        ;;
stop)
        do_stop
        ;;
restart|reload|force-reload)
        do_stop
        do_start
        ;;
*)
        echo "Usage: cryptdisks {start|stop|restart|reload|force-reload}"
        exit 1
        ;;
esac

```



## Finally, make a new lib functions file that you new
## initscript will call.  
## 
## Again, I have fixed this file... so you can copy mine,
## Or edit the CRYPTDISKS_ENABLE=Yes by loading after it loads 
## the default cryptdisks... or just use my file
##
## This new file is patched to hardcode fix
## the CRYPTDISKS_ENABLE=No... and force it to Yes for post booting
## TO LINK PROPERLY... Call this new file:
## /lib/cryptsetup/cryptdisks.functions-post

```

#
# This file is for inclusion with
#       . /lib/cryptsetup/cryptdisks.functions
# and should not be executed directly.

PATH="/sbin:/bin"
TABFILE=/etc/crypttab

#set -x

# Sanity checks
[ -x /sbin/cryptsetup ] || exit 0
[ -f "$TABFILE"       ] || exit 0

. /lib/lsb/init-functions

if [ -r /etc/default/cryptdisks ]; then
        . /etc/default/cryptdisks
fi

CRYPTDISKS_ENABLE="Yes"
MOUNT="$CRYPTDISKS_MOUNT"

case "$CRYPTDISKS_ENABLE" in
[Nn]*)
        exit 0
        ;;
esac

# Always output to console
stdin=`readlink /proc/self/fd/0`
if [ "${stdin#/dev/null}" != "$stdin" ] && [ "$ON_VT" != "yes" ]; then
    exec env ON_VT=yes /usr/bin/openvt -f -c `fgconsole` -w $0 "$@"
fi


# Parses the option field from the crypttab file
parse_opts () {
        local opts opt IFS PARAM VALUE

        opts="$1"
        LOUD=""
        PARAMS=""
        CHECK=""
        CHECKARGS=""
        PRECHECK=""
        TRIES="3"
        MAKETMP=""
        MAKESWAP=""
        USELUKS=""
        TIMEOUT=""
        KEYSCRIPT=""

        # Parse the options field, convert to cryptsetup parameters
        # and construct the command line
        IFS=','
        for opt in $opts; do
                PARAM=$(echo "$opt" | sed 's/=.*//')
                VALUE=$(echo "$opt" | sed '/=/!d;s/^.*=//')

                case "$PARAM" in 
                readonly)
                        PARAMS="$PARAMS -r"
                        ;;
                cipher)
                        if [ -z "$VALUE" ]; then
                                log_warning_msg "$dst: no value for cipher option, skipping"
                                return 1
                        fi
                        PARAMS="$PARAMS -c $VALUE"
                        ;;
                size)
                        if [ -z "$VALUE" ]; then
                                log_warning_msg "$dst: no value for size option, skipping"
                                return 1
                        fi
                        PARAMS="$PARAMS -s $VALUE"
                        ;;
                hash)
                        if [ -z "$VALUE" ]; then
                                log_warning_msg "$dst: no value for hash option, skipping"
                                return 1
                        fi
                        PARAMS="$PARAMS -h $VALUE"
                        ;;
                verify)
                        PARAMS="$PARAMS -y"
                        ;;
                check)
                        if [ -z "$VALUE" ]; then
                                VALUE="$CRYPTDISKS_CHECK"
                        fi
                        if [ -x "$VALUE" ]; then
                                CHECK="$VALUE"
                        elif [ -x "/lib/cryptsetup/checks/$VALUE" ]; then
                                CHECK="/lib/cryptsetup/checks/$VALUE"
                        else
                                log_warning_msg "check $VALUE is not an executable script, skipping"
                                return 1
                        fi
                        ;;
                checkargs)
                        if [ -n "$VALUE" ]; then
                                CHECKARGS="$VALUE"
                        fi
                        ;;
                precheck)
                        if [ -z "$VALUE" ]; then
                                VALUE="$CRYPTDISKS_PRECHECK"
                        fi
                        if [ -x "$VALUE" ]; then
                                PRECHECK="$VALUE"
                        elif [ -x "/lib/cryptsetup/checks/$VALUE" ]; then
                                PRECHECK="/lib/cryptsetup/checks/$VALUE"
                        else
                                log_warning_msg "precheck $VALUE is not an executable script, skipping"
                                return 1
                        fi
                        ;;
                tries)
                        if echo "$VALUE" | grep -q "^[[:digit:]]\+$" && [ "$VALUE" -gt 0 ]; then
                                TRIES="$VALUE"
                        else
                                log_warning_msg "$dst: option tries used with an incorrect argument - forced to $TRIES"
                        fi
                        PARAMS="$PARAMS --tries=$TRIES"
                        ;;
                timeout)
                        if [ -z "$VALUE" ]; then
                                TIMEOUT="$CRYPTDISKS_TIMEOUT"
                        elif echo "$VALUE" | grep -q "^[[:digit:]]\+$"; then
                                TIMEOUT="$VALUE"
                        else
                                log_warning_msg "$dst: option timeout used with an incorrect argument - forced to '$TIMEOUT'"
                        fi
                        PARAMS="$PARAMS --timeout=$TIMEOUT"
                        ;;
                swap)
                        MAKESWAP=yes
                        SWCHECK="/lib/cryptsetup/checks/un_vol_id"
                        SWCHECKARGS="swap"
                        ;;
                tmp)
                        MAKETMP=yes
                        ;;
                luks)
                        USELUKS=yes
                        ;;
                loud)
                        LOUD=yes
                        ;;
                keyscript)
                        if [ -n "$KEYSCRIPT" ]; then
                                log_warning_msg "$dst: multiple key decryption options are not allowed together, skipping"
                                return 1
                        elif [ -z "$VALUE" ]; then
                                log_warning_msg "$dst: no value for keyscript option, skipping"
                                return 1
                        fi
                        KEYSCRIPT="$VALUE"
                        ;;
                esac
        done

        return 0
}

# Set up loopback devices
lo_setup () {
        local loopdev

        if [ ! -f "$src" ]; then
                return 0
        fi

        if [ ! -x /sbin/losetup ]; then
                return 1
        fi

        if ! grep -q "[[:space:]]loop$" /proc/devices; then
                modprobe -qb loop > /dev/null 2>&1 || return 1
        fi

        loopdev=$(losetup -f 2> /dev/null) || return 1

        losetup "$loopdev" "$src" || return 1
        src="$loopdev"
        return 0
}

# Sanity check for keys
check_key () {
        local GMODE OMODE OWNER GROUP

        # If the keyscript option is set, the "key" is just an argument to
        # the keyscript and not necessarily a file
        if [ -n "$KEYSCRIPT" ]; then
                return 0
        fi

        if [ -z "$key" ] || [ "$key" = "none" ]; then
                INTERACTIVE="yes"
                return 0
        fi
        INTERACTIVE="no"

        if [ ! -e "$key" ]; then
                log_warning_msg "$dst: keyfile not found"
                return 1
        fi

        # stat is unfortunately in /usr/bin...
        OMODE=$(ls -l "$key" | sed 's/[[:space:]].*//;s/^.\{7\}//')
        GMODE=$(ls -l "$key" | sed 's/[[:space:]].*//;s/^.\{4\}\(.\{3\}\).*/\1/')
        GROUP=$(ls -l "$key" | sed 's/^.\{11\}[^[:space:]]* [^[:space:]]* \([^[:space:]]*\).*/\1/')
        OWNER=$( ls -l "$key" | sed 's/^.\{11\}[^[:space:]]* \([^[:space:]]*\).*/\1/')

        # LUKS requires a persistent key, /dev/*random is not supported
        if [ "$USELUKS" = "yes" ] && [ "$key" != "${key%random}" ]; then
                log_warning_msg "$dst: LUKS does not work with random data as key"
                return 1
        fi

        # Check owner
        if [ "$OWNER" != "root" ]; then
                log_warning_msg "$dst: INSECURE OWNER FOR $key, see /usr/share/doc/cryptsetup/README.Debian."
        fi

        # If key is random, we're done
        if [ "$key" != "${key%random}" ]; then
                return 0
        fi

        # Check group and other permissions
        if [ "$OMODE" != "---" ] || [ "$GROUP" != "root" ] && [ "$GMODE" != "---" ]; then
                log_warning_msg "$dst: INSECURE MODE FOR $key, see /usr/share/doc/cryptsetup/README.Debian."
        fi

        return 0
}

# Setup a luks mapping
do_luks () {
        local tried
        tried=0

        if ! cryptsetup isLuks "$src" >/dev/null 2>&1; then
                log_warning_msg "$dst: device '$src' is not a LUKS partition, skipping"
                return 1
        fi

        if [ -n "$KEYSCRIPT" ]; then
                PARAMS="$PARAMS --key-file=-"
                while [ "$tried" -lt "$TRIES" ]; do
                        if "$KEYSCRIPT" "$key" <&1 | cryptsetup $PARAMS luksOpen "$src" "$dst"; then
                                break
                        fi
                        tried=$(( $tried + 1 ))
                done
        elif [ "$INTERACTIVE" != "yes" ]; then
                PARAMS="$PARAMS --key-file=$key"
                while [ "$tried" -lt "$TRIES" ]; do
                        if cryptsetup $PARAMS luksOpen "$src" "$dst" <&1; then
                                break
                        fi
                        tried=$(( $tried + 1 ))
                done
        else
                if test "x$INTERACTIVE" != "xyes" ; then
                        PARAMS="$PARAMS --key-file=$key"
                        cryptsetup $PARAMS luksOpen $src $dst <&1
                else
                        if [ -x /sbin/usplash_write -a -p /dev/.initramfs/usplash_outfifo ]; then
                                /sbin/usplash_write "QUIT"
                                # saftey sleep !
                                sleep 2
                        fi
                        cryptsetup $PARAMS luksOpen $src $dst <&1
                fi
        fi

        if [ "$tried" -ge "$TRIES" ]; then
                return 1
        fi

        if [ -n "$CHECK" ] && ! "$CHECK" "/dev/mapper/$dst" $CHECKARGS; then
                log_warning_msg "$dst: the check for '/dev/mapper/$dst' failed"
                cryptsetup luksClose $dst
                return 1
        fi

        return 0
}

# Setup a regular mapping
do_noluks () {
        local pre_out tried
        tried=0

        if [ -z "$PRECHECK" ]; then
                PRECHECK="/lib/cryptsetup/checks/un_vol_id"
        fi

        if ! pre_out=$("$PRECHECK" "$src" 2> /dev/null) && \
           [ "$MAKESWAP" != "yes" ] && \
           ! /lib/cryptsetup/checks/vol_id "$src" swap >/dev/null; then
                log_warning_msg "$dst: the precheck for '$src' failed: $pre_out"
                return 1
        fi

        if [ -n "$KEYSCRIPT" ]; then
                PARAMS="$PARAMS --key-file=-"
        elif [ "$INTERACTIVE" != "yes" ]; then
                PARAMS="$PARAMS --key-file=$key"
        fi

        while [ "$tried" -lt "$TRIES" ]; do
                if [ -n "$KEYSCRIPT" ]; then
                        "$KEYSCRIPT" "$key" <&1 | cryptsetup $PARAMS create "$dst" "$src"
                else
                        cryptsetup $PARAMS create "$dst" "$src" <&1
                fi

                if [ -z "$CHECK" ] || "$CHECK" "/dev/mapper/$dst" $CHECKARGS; then
                        break
                else
                        log_warning_msg "$dst: the check for '/dev/mapper/$dst' failed - maybe the password is wrong"
                        cryptsetup remove "$dst"
                fi
                tried=$(( $tried + 1 ))
        done

        if [ "$tried" -ge "$TRIES" ]; then
                return 1
        fi

        return 0
}

# Premounts file systems
mount_fs () {
        local point
        MOUNTED=""

        for point in $MOUNT; do
                if mount "$point" >/dev/null; then
                        MOUNTED="$MOUNTED $point"
                fi
        done
}

# Postunmounts file systems
umount_fs () {
        local point

        for point in $MOUNTED; do
                umount "$point" >/dev/null
        done
}

# Prepares swap partitions using random keys
do_swap () {
        local swap_out

        if [ "$MAKESWAP" != "yes" ] || [ ! -b "/dev/mapper/$dst" ]; then
                return 0
        fi

        if swap_out=$(/lib/cryptsetup/checks/un_vol_id "/dev/mapper/$dst" 2> /dev/null) || \
           /lib/cryptsetup/checks/vol_id "/dev/mapper/$dst" swap > /dev/null 2>&1; then
                mkswap "/dev/mapper/$dst" > /dev/null 2>&1
        else
                log_warning_msg "$dst: the check for '/dev/mapper/$dst' failed. /dev/mapper/$dst contains data: $swap_out"
                do_close
                return 1
        fi

        return 0
}

# Prepares tmp partitions using random keys
do_tmp () {
        if [ "$MAKETMP" != "yes" ] || [ ! -b "/dev/mapper/$dst" ]; then
                return 0
        fi

        mke2fs "/dev/mapper/$dst" > /dev/null 2>&1 || return 1
        mount -t ext2 "/dev/mapper/$dst" /tmp || return 1
        chmod 1777 /tmp
        umount /tmp
        return 0
}

# Removes a mapping
do_close () {
        local found IFS opt

        found="no"
        IFS=','
        for opt in $opts; do
                if [ "$opt" = "luks" ]; then
                        found="yes"
                        break
                fi
        done

        if [ "$found" = "yes" ]; then
                cryptsetup luksClose "$dst"
        else
                cryptsetup remove "$dst"
        fi
        return $?
}

load_optimized_aes_module () {
        local asm_module modulesdir

        # find directory with kernel modules
        modulesdir="/lib/modules/`uname -r`"
        # Add assembly optimized AES module if it exists
        asm_module=`ls -1 "$modulesdir"/kernel/arch/*/*/aes*.ko`
        if [ $asm_module ];then
           insmod $asm_module 2>/dev/null || true
        fi
}

# Sets up all entries in crypttab
do_start () {
        local dst src key opts result

        modprobe -qb dm-mod || true
        modprobe -qb dm-crypt || true
        dmsetup mknodes > /dev/null 2>&1 || true
        log_action_begin_msg "Starting $INITSTATE crypto disks"
        load_optimized_aes_module
        mount_fs

        egrep -v "^[[:space:]]*(#|$)" "$TABFILE" | while read dst src key opts; do

                # Make sure that all fields are present
                if [ -z "$dst" ]; then
                        continue
                elif [ -z "$src" ] || [ -z "$key" ] || [ -z "$opts" ]; then
                        device_msg "$dst" "skipped, missing parameters"
                        continue
                fi

                # parse UUID= symlinks
                if [ ${src#UUID=} != $src ]; then
                        src="/dev/disk/by-uuid/${src#UUID=}"
                elif [ ${src#LABEL=} != $src ]; then
                        src="/dev/disk/by-label/${src#LABEL=}"
                fi

                # Make sure source device exists
                if [ ! -r "$src" ]; then
                        if [ "$LOUD" = "yes" ]; then
                                device_msg "$dst" "skipped, device $src does not exist"
                        fi
                        continue
                fi

                # Make sure that target device doesn't exist
                if [ -b "/dev/mapper/$dst" ]; then
                        device_msg "$dst" "running"
                        continue
                fi

                # All checks passed, do the preparatory steps
                if ! parse_opts "$opts"; then
                        device_msg "$dst" "invalid opts"
                        continue
                elif ! check_key; then
                        device_msg "$dst" "invalid key"
                        continue
                elif ! lo_setup; then
                        device_msg "$dst" "loopback failed"
                fi

                # Do the real setup
                log_progress_msg "$dst (starting)"
                result="ok"
                if [ "$USELUKS" = "yes" ]; then
                        do_luks || result="fail"
                else
                        do_noluks || result="fail"
                fi

                # Finish up
                if [ "$result" != "ok" ]; then
                        log_progress_msg "$dst (failed)"
                else
                        do_swap
                        do_tmp
                        log_progress_msg "$dst (started)"
                fi
        done

        umount_fs
        log_action_end_msg 0
}

# Removes all mappings in crypttab
do_stop () {
        local dst src key opts opencount major minor loopmajor

        dmsetup mknodes
        log_action_begin_msg "Stopping $INITSTATE crypto disks"
        loopmajor=$(grep "[[:space:]]*loop$" /proc/devices | sed 's/^[[:space:]]*//;s/[[:space:]].*//')

        egrep -v "^[[:space:]]*(#|$)" "$TABFILE" | while read dst src key opts; do
                if [ ! -b "/dev/mapper/$dst" ]; then
                        device_msg "$dst" "stopped"
                        continue
                fi

                opencount=$(dmsetup info -c --noheadings -o open "$dst" 2> /dev/null)
                if [ -z "$opencount" ]; then
                        device_msg "$dst" "error"
                        continue
                elif [ "$opencount" != "0" ]; then
                        device_msg "$dst" "busy"
                        continue
                fi

                major=$(dmsetup info -c --noheadings -o major "$dst" 2> /dev/null)
                minor=$(dmsetup info -c --noheadings -o minor "$dst" 2> /dev/null)

                if [ -z "$major" ] || [ -z "$minor" ]; then
                        device_msg "$dst" "error"
                        continue
                fi

                do_close
                log_action_cont_msg "$dst (stopping)"

                # Detach loopback device, if attached
                if [ -f "$src" ] && [ -n "$loopmajor" ] && [ "$loopmajor" = "$major" ]; then 
                        losetup -d "/dev/loop$minor" > /dev/null 2>&1 || true
                fi
        done

        log_action_end_msg 0
}

# Convenience function to handle $VERBOSE
device_msg () {
        local dst msg
        dst="$1"
        msg="$2"

        if [ "$VERBOSE" != "no" ]; then
                log_action_cont_msg "$dst ($msg)"
        fi
}

```




If done correctly... your system should boot without asking for a password.

Finally, after booting... you should be able to run as *root*:

/etc/init.d/cryptdisks-post
swapon -a
mount /encrypted


Let me know if that works for you.  Cheers!

---

### Post by tazeat on 2008-04-30
I just made the following shell script, I just log in via ssh and type ./mount which is in my home directory.

My encrypted partition has two volumes:
files which is like 19gb and swap which is 1gb

```
#!/bin/sh
cryptsetup luksOpen /dev/sda3 sda3_crypt
mount /dev/mapper/encrypted-files /home/storage
swapon -p 1 /dev/mapper/encrypted-swap
```

Yours looks like a lot more work, but I admit I didnt really follow through what you did...

---

### Post by Tomy on 2008-08-24
> **tazeat said:**
> I just made the following shell script, I just log in via ssh and type ./mount which is in my home directory.
...


Thanks, I like easy.

---

