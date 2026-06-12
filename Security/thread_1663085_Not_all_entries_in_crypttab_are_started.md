---
title: "Not all entries in crypttab are started"
date: 2011-01-09
forum: Security
---

### Post by Seq on 2011-01-09
I have two disks, both have luks enabled encrypted volumes, and both (will) contain a LVM PV belonging to the same volume group. Due to this, i would like both encrypted volumes to start on boot. It seems I only seem to get one to start. My system still boots because currently the second encrypted volume is empty.

**/etc/crypttab**. The partitions I want started are Crypt_SSD and sda4_crypt. LuksData is a third partition that is opened manually via a keyscript.
```
LuksData UUID=8d5a6460-4f95-40e7-8ea5-2fa77797f8a9 none luks,noauto
Crypt_SSD UUID=a5873d1f-67f1-4e9d-9b83-ac4e21273cfd none luks,keyscript=/boot/keyscript
sda4_crypt UUID=28dc4bb5-5531-4ebe-a6e2-4f0121258376 none luks,keyscript=/boot/keyscript
```

**/boot/keyscript**. This checks if the encrypted partition called 'LuksData' is opened. If not, it opens it. It then uses `cat` to return the decrypted contents, which is used as the key to the two partitions I care about. The point of this was to avoid typing my passphrase twice.

```
#!/bin/sh

# Taken from /usr/share/initramfs-tools/scripts/local-top/cryptroot
# with minor changes by Chris Irwin <chris@chrisirwin.ca>

cryptsource=/dev/disk/by-uuid/8d5a6460-4f95-40e7-8ea5-2fa77797f8a9
crypttarget="LuksData"

crypttries=5
cryptcreate="/sbin/cryptsetup -T 1 luksOpen $cryptsource $crypttarget"

message()
{
    if [ -x /bin/plymouth ] && plymouth --ping; then
        plymouth message --text="$@"
    elif [ -p /dev/.initramfs/usplash_outfifo ] && [ -x /sbin/usplash_write ]; then
        usplash_write "TEXT-URGENT $@"
    else
        echo "$@" >&2
    fi
    return 0
}

    # Try to get a satisfactory password $crypttries times
    count=0
    while [ $crypttries -le 0 ] || [ $count -lt $crypttries ]; do
        count=$(( $count + 1 ))

        if [ $count -gt 1 ]; then
            /bin/sleep 3
        fi

        if [ $crypttries -gt 0 ] && [ $count -gt $crypttries ]; then
            message "keyscript: maximum number of tries exceeded for $crypttarget"
            return 1
        fi

        if [ ! -e /dev/mapper/$crypttarget ]; then
            # Cryptkeysys does not exist. Set it up.
            cryptkey="Unlocking the disk $crypttarget - requested by $CRYPTTAB_NAME\nEnter passphrase: "
            if [ -x /bin/plymouth ] && plymouth --ping; then
                cryptkeyscript="plymouth ask-for-password --prompt"
                cryptkey=$(echo -e "$cryptkey")
            else
                cryptkeyscript="/lib/cryptsetup/askpass"
            fi

            if ! crypttarget="$crypttarget" cryptsource="$cryptsource" \
                 $cryptkeyscript "$cryptkey" | $cryptcreate --key-file=- ; then
                message "keyscript: cryptsetup failed, bad password or options?"
                continue
            fi

            message "keyscript: $crypttarget set up successfully"
        fi

        # Hopefully mounted by now
        if [ ! -e /dev/mapper/$crypttarget ]; then
            message "keyscript: Apparently unable to access $crypttarget!"
            continue
        fi

        cat /dev/mapper/$crypttarget

        break
    done

exit 0
```

Here is the sequence of events when I boot:

* When I boot, I get the message "Unlocking the disk LuksData - requested by sda4_crypt", which is what I expect. My keyscript is run properly and is asking for input.
* I Type in my passphrase for LuksData
* I get a note saying LuksData is set up successfully (from my script).
* I get a note saying sda4_crypt is set up successfully (from whatever the initrd is using).
* Login proceeds normally, and I'm thrown into my desktop.

However, upon checking /mnt/mapper/*, it appears that LuksData is open (Which my script did), sda4_crypt is open (which used the key provided by my script), however Crypt_SSD is not. It does not seem to be a mis-configuration in /etc/crypttab since it manually starts without error:

```
$ sudo cryptdisks_start Crypt_SSD
 * Starting crypto disk...
 * Crypt_SSD (starting)..
 * Crypt_SSD (started)...                                                [ OK ]
```

I've made sure my initrd is up to date. At this point I'm out of ideas.

---

### Post by Seq on 2011-01-09
Okay, so it looks like crypttab is parsed to build the initrd but is not included. It seems like the scripts were tuned to pick out which volumes root & swap are on and start those.

Makes sense (Only start whats needed from initrd), but I don't understand why all crypttab entries are not included (I could understand deferring 'noearly' entries and omitting 'noauto' entries). It also doesn't explain why the rest of crypttab isn't started after the system boots up.

Here is the contents of **conf/conf.d/cryptroot** from my initrd.

```
target=sda4_crypt,source=UUID=28dc4bb5-5531-4ebe-a6e2-4f0121258376,key=none,rootdev,lvm=vgthinkpad-root_maverick,keyscript=/lib/cryptsetup/scripts/keyscript
target=sda4_crypt,source=UUID=28dc4bb5-5531-4ebe-a6e2-4f0121258376,key=none,lvm=vgthinkpad-swap,keyscript=/lib/cryptsetup/scripts/keyscript
```

This is starting to look like a bug to me. In theory, if I pvmove my root filesystem to my other drive I will no longer be able to boot.

---

### Post by Seq on 2011-01-09
This is [bug 490917]("https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/490917"). It has been around for a while.

---

