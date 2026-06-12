---
title: "No write permission in recovery mode"
date: 2012-02-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by williammanda on 2012-02-15
I'm trying to edit my fstab file in recovery mode using root user but I get a message " no write permission" using nano. I tried loging in as my user and using sudo but the same result.
Please advise.
Thanks

---

### Post by dino99 on 2012-02-15
/etc/fstab might be own by root:root with -rw-r--r-- rights

---

### Post by williammanda on 2012-02-15
> **dino99 said:**
> /etc/fstab might be own by root:root with -rw-r--r-- rights

So how can I change fstab?

---

### Post by dino99 on 2012-02-15
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by sisco311 on 2012-02-15
Make sure that the root partition is mounted read/write:```
mount -o remount,rw /
```

---

### Post by williammanda on 2012-02-15
> **dino99 said:**
> [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Sorry but after reiviewing the links I see no reference on how to edit a file as root in recovery mode. It use to work before...I used it. Please see my 1st post.

---

### Post by williammanda on 2012-02-15
> **sisco311 said:**
> Make sure that the root partition is mounted read/write:```
mount -o remount,rw /
```

This worked! I wonder why it isn't setup this way to start out with?

---

### Post by cariboo on 2012-02-15
There is a mount partition option in the recovery mode menu, use it before selecting Drop to netprompt.

---

### Post by effenberg0x0 on 2012-02-15
> **williammanda said:**
> I'm trying to edit my fstab file in recovery mode using root user but I get a message " no write permission" using nano. I tried loging in as my user and using sudo but the same result.
Please advise.
Thanks

OBS: This is not related to Precise Pangolin. If a mod could move it back to the Total Beginners area it would be nice.

It has always been like this. When you select recovery mode on Grub your boot must proceed to a point in which you are presented with options. You should see something like this: [http://www.trumanellis.com/wp-content/uploads/2011/11/IMG_8122.jpg](http://www.trumanellis.com/wp-content/uploads/2011/11/IMG_8122.jpg)

Eventually you can remount it rw, with something like...
```
mount -f -o remount,rw -t ext3 /dev/sda1 /
```...but you shouldn't have to.

But this is wrong in many ways. I really don't know if your '/' is really RO and why it is RO. And not even if it is really /dev/sda1 or /dev/sda(n). Ideally, I would prefer to run something like this:

```
#!/bin/bash
#Save as ~/remount_rw.sh, run chmod +x ~/remount_rw.sh and execute with ~/./remount_rw.sh
#
ROOT_PARTITION=$(sudo mount | grep -i "on / type" | awk '{ print $1}') && ROOT_FS=$(sudo mount | grep -i "on / type" | awk '{ print $5}') 
ROOT_WRITE=$(sudo mount | grep -i "on / type" | awk '{ print $6 }' | sed 's|(||g' | sed -e 's|)||g' | awk 'BEGIN {FS=","} {print $1}')
FIX_USER=$(sudo cat /etc/passwd | grep 1000 | awk 'BEGIN { FS=":" }; {print $1}')

if [ ${ROOT_WRITE} == "ro" ]; then 
  echo -e "ROOT PARTITION:${ROOT_PARTITION}\nROOT_FS:${ROOT_FS}\nROOT_WRITE:${ROOT_WRITE}\nUSER:${FIX_USER}\nROOT is RO - Remounting as RW" 
  sudo mount -f -o remount,rw -t ${ROOT_FS} ${ROOT_PARTITION} / 
else 
  echo -e "\nROOT PARTITION:${ROOT_PARTITION}\nROOT_FS:${ROOT_FS}\nROOT_WRITE:${ROOT_WRITE}\nUSER:${FIX_USER}\nROOT is RW - No action needed"; 
fi
```EDIT: When you change fstab, think twice about removing "-errors=*remount*-*ro*" since you clearly don't know what you're doing. It's there to protect you.

EDIT2: Sorry guys, I picked up the phone while was writing the script and hadn't seen your previous answers :)
Regards,
Effenberg

---

### Post by paul_in_london on 2012-02-15
I can't remember how long ago the recovery mode behaviour changed, but unless my memory's playing tricks on me recovery mode used to boot to run-level **[COLOR="Red"]1[/COLOR]** and now it's **[COLOR="Red"]S[/COLOR]** (or **[COLOR="Red"]s[/COLOR]**) where:

```
**[COLOR="Red"][B]S** (or **[COLOR="Red"]s[/COLOR]**)[/COLOR][/B] : single-user, with only root filesystem mounted (as read-only)

**[COLOR="Red"]1[/COLOR]** : single-user with local filesystems mounted (read-write)
```

Leaving aside the fact that **[COLOR="Red"]S[/COLOR]** (or **[COLOR="Red"]s[/COLOR]**) arguably isn't really a run-level, an extra step may be required to get into run-level **[COLOR="Red"]1[/COLOR]**. For example, choosing **[COLOR="Red"]root[/COLOR]** immediately from the recovery menu doesn't change the run-level to run-level **[COLOR="Red"]1[/COLOR]**. From there you either need to remount manually or exit to the recovery menu and choose something else (e.g. **[COLOR="Red"]fsck[/COLOR]** or **[COLOR="Red"]network[/COLOR]**) to be promptd that "**[COLOR="Red"]Continuing will remount your / filesystem in read/write mode[/COLOR]**" etc. and then be returned to the revised recovery menu.

---

### Post by mc4man on 2012-02-15
At some point in PP the "remount" option on the initial recovery screen was removed via a friendly-recovery upgrade for whatever reason

---

### Post by effenberg0x0 on 2012-02-15
@mc4man

Weird, I have it in the Recovery Menu for PP. 
See the screenshot for fully updated OOxPP (x86_64). 
[ATTACH]212714[/ATTACH]

Regards,
Effenberg

---

### Post by williammanda on 2012-02-15
> **effenberg0x0 said:**
> @mc4man

Weird, I have it in the Recovery Menu for PP. 
See the screenshot for fully updated OOxPP (x86_64). 
[ATTACH]212714[/ATTACH]

Regards,
Effenberg

That not what I had using 12.4. There were 5 entries, possibly.

---

### Post by MacUntu on 2012-02-15
...

---

### Post by mc4man on 2012-02-15
> **effenberg0x0 said:**
> @mc4man

Weird, I have it in the Recovery Menu for PP. 
See the screenshot for fully updated OOxPP (x86_64). 
[ATTACH]212714[/ATTACH]

Regards,
Effenberg

Seems odd you've 'retained' something?
The menu change occurred in the current friendly package, 2.23, the last to have the old style was 2.21, 2.22 was a mistake

If I was to downgrade & then up to current I do get the new menu

(was glad to see something positive happen to our 'tilt' friend..

---

### Post by effenberg0x0 on 2012-02-15
> **williammanda said:**
> That not what I had using 12.4. There were 5 entries, possibly.
> **mc4man said:**
> Seems odd you've 'retained' something?
The menu change occurred in the current friendly package, 2.23, the last to have the old style was 2.21, 2.22 was a mistake

If I was to downgrade & then up to current I do get the new menu

(was glad to see something positive happen to our 'tilt' friend..
I see what happened here. For some reason both OO and PP were running friendly-recovery package version 0.2.18. PP should be running 0.2.23. 

It's unexpected, because both show no packages on hold and 0 possible upgrades. But I think this brings us (again!) to apt-get/aptitude/synaptic/update-manager/software-center/repos_sync reliability&&differences issues, which were reported more than enough in OO cycle and won't be checked or fixed. So I'll leave it at this.

Anyway, I have just diffed /etc/init/friendly-recovery.conf for 0.2.18 and 0.2.23. Here's the patch if anyone is interested in giving it a try.
[B]
EDIT: [/B]The remount-rw option **is** still available in friendly-recovery 0.2.23 under the Network menu option. To test it without rebooting into recovery, just run /lib/recovery-mode/recovery-menu in a console. I have diffed it from OO's version at the end of this post so one can understand the differences between the versions.


$ cat ~/dev/ubuntu/pp/friendly-recovery/friendly-recovery.patch
```
# Patches PP friendly-recovery.conf so it equals OO version. Will it blend?
# Alvaro "Effenberg0x0" Leal, Feb.15 - 19:00
--- /etc/init/friendly-recovery.conf
+++ /etc/init/friendly-recovery.conf
@@ -5,30 +5,17 @@
 console owner
 task
 
-emits recovery
-emits startup
-emits mounted
-
 pre-start script
     if plymouth --ping; then
-        plymouth hide-splash || true
+        plymouth hide-splash
     fi
 
     # Try to set the hostname and initialize the console
-    start hostname || true
-    start console-setup || true
-    start setvtrgb || true
-
-    # Emit the mounted event to trigger resolvconf and mounted-run
-    initctl emit mounted MOUNTPOINT=/run || true
-
-    # Finally start udev
-    start udev || true
-    udevadm trigger --action=add || true
-    udevadm settle || true
-
-    # And turn off kernel messages (to avoid corrupting the menu)
-    dmesg --console-off || true
+    # use --no-wait to avoid hanging here. The menu itself doesn't
+    # depend on any of these two so it's fine to have them start
+    # in the background
+    start -n hostname || true
+    start -n console-setup || true
 end script
 
 script
@@ -50,4 +37,3 @@
     fi
     initctl emit startup
 end script
-
```

**EDIT:**  I had forgot to diff recovery-menu itself. Quite a bit of change, so it's interesting anyway.

$ cat ~/dev/ubuntu/pp/friendly-recovery/recovery-menu.patch
```
# Patches PP recovery-menu so it equals OO version. Will it blend?
# Alvaro "Effenberg0x0" Leal, Feb.15 - 19:32
--- /lib/recovery-mode/recovery-menu
+++/lib/recovery-mode/recovery-menu
@@ -11,16 +11,12 @@
 . /lib/recovery-mode/l10n.sh
 
 # main
+menu_text=$(eval_gettext "Recovery Menu (limited read-only menu)")
 READONLY=true
+export READONLY
 
 while true; do
   unset items
-
-  if [ "$READONLY" = "true" ]; then
-    menu_text=$(eval_gettext "Recovery Menu (filesystem state: read-only)")
-  else
-    menu_text=$(eval_gettext "Recovery Menu (filesystem state: read/write)")
-  fi
 
   items[c++]="resume"
   items[c++]=$(eval_gettext "   Resume normal boot")
@@ -29,82 +25,35 @@
     if [ -x "$i" ]; then
       name="`"$i" test`"
       if [ $? -eq 0 ]; then
-        items[c++]="${i##*/}"
+        items[c++]="`basename "$i"`"
         items[c++]="   $name"
       fi
     fi
   done
 
-  choice="$(whiptail --nocancel --menu "$menu_text" 16 70 7 \
+  choice="$(whiptail --menu "$menu_text" 15 70 6 \
                              "${items[@]}" \
                              3>&1 1>&2 2>&3 3>&-)"
 
-  if [ -z "$choice" ]; then
-    continue
+  if [ $? -ne 0 ]; then
+    choice="resume"
   fi
 
   if [ "$choice" = "resume" ]; then
-    box_text=$(eval_gettext "You are now going to exit the recovery mode and continue the boot sequence. Please note that some graphic drivers require a full graphical boot and so will fail when resuming from recovery.
-If that's the case, simply reboot from the login screen and then perform a standard boot.")
-    whiptail --msgbox "$box_text" 12 70
     clear
     exit
   fi
 
-  /lib/recovery-mode/options/$choice test mode >/dev/null 2>&1
+  "/lib/recovery-mode/options/$choice"
   retval=$?
 
-  # Hack for the fsck case (needs to be cosidered read/write only when
-  # in read-only mode and read-only only when in read/write mode)
-  if [ "$choice" = "fsck" ] && [ "$READONLY" = "false" ]; then
-    retval=1
+  if [ "$choice" = "remount" ] || [ "$choice" = "fsck" ]; then
+    menu_text=$(eval_gettext "Recovery Menu")
+    READONLY=false
   fi
 
-  case "$retval" in
-    0)
-      # 0 => requires read/write
-      if [ "$READONLY" = "true" ]; then
-        box_text=$(eval_gettext "Continuing will remount your / filesystem in read/write mode and mount any other filesystem defined in /etc/fstab.
-Do you wish to continue?")
-        whiptail --yesno "$box_text" 10 70 || continue
-
-        if [ "$choice" = "fsck" ]; then
-            FSCHECK="true"
-        fi
-
-        # Code mostly taken from mountall upstart job
-        . /etc/default/rcS
-        [ "$FSCHECK" = "true" ] || [ -f /forcefsck ] && force_fsck="--force-fsck"
-        [ "$FSCKFIX" = "yes" ] && fsck_fix="--fsck-fix"
-        mountall $force_fsck $fsck_fix --no-events
-        rm -f /forcefsck 2>dev/null || true
-
```

Regards,
Clippy

PS: @mc4man (tilt-wise) Yea, just saw it a couple hours ago. I was really cheering for him. Sad story.

---

### Post by Elfy on 2012-04-15
I have no mount drive option here - [https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/982134](https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/982134)

---

