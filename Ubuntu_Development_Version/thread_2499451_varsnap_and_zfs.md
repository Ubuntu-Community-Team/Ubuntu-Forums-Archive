---
title: "/var/snap and zfs"
date: 2024-07-27
forum: Ubuntu Development Version
---

### Post by #&amp;thj^% on 2024-07-27
So I'm the biggest snap hater here in UF and that's Ok. (No Need to comment on my usage) It just dose not suit my wants, and that's all there is to it. :P

Anyway to continue my de-snap process has now hit a speed bump, so this is more or less a heads up for folks like myself. I won't bore you with my de-snap method, but this is a big No No on 24.04 and 24.10 do not touch "/var/snap" it will leave you stuck in busybox.

My solution for just me was to reinstall kernels :
```
sudo apt install --reinstall linux-modules-6.10.0-15-generic linux-image-unsigned-6.10.0-15-generic linux-modules-extra-6.10.0-15-generic

```
Then I'm back to my normal DE.
```
 sudo dmesg|grep -e var -e snap 
[sudo] password for me: 
[    0.000000] efi: ACPI=0xcdffe000 ACPI 2.0=0xcdffe014 TPMFinalLog=0xcdf3f000 SMBIOS=0xcb70a000 SMBIOS 3.0=0xcb708000 MEMATTR=0xb530f018 ESRT=0xb5319d18 MOKvar=0xcb87f000 INITRD=0xb5318698 RNG=0xcdf9d018 TPMEventLog=0xb52ff018 
[    0.000365] MTRR map: 7 entries (4 fixed + 3 variable; max 21), built from 9 variable MTRRs
[    0.073899] 	Trampoline variant of Tasks RCU enabled.
[    0.073899] 	Rude variant of Tasks RCU enabled.
[    0.073899] 	Tracing variant of Tasks RCU enabled.
[    0.359095] efivars: Registered efivars operations
[    9.004644] systemd[1]: systemd-hibernate-clear.service - Clear Stale Hibernate Storage Info was skipped because of an unmet condition check (ConditionPathExists=/sys/firmware/efi/efivars/HibernateLocation-8cf2644b-4b0b-428f-9387-6d876050dc67).

```
Reason:
```
 df /var/snap
Filesystem                        Type  Size  Used Avail Use% Mounted on
rpool/ROOT/ubuntu_n2r3zw/var/snap zfs   421G  128K  421G   1% /var/snap

```

That's All Folks....

---

### Post by VMC on 2024-07-28
Didn't happen to me. Maybe something else going on. '/var/snap'  is gone on 24.04 Xubuntu, and gone on 24.10 on Kubuntu, without any ill effects.
I would say that busybox is from something else, but adding /var/snap' back fixes it is a real head scratcher. Maybe going over the snap removal process will reveal something.

---

### Post by #&amp;thj^% on 2024-07-28
> **VMC said:**
> Didn't happen to me. Maybe something else going on. '/var/snap'  is gone on 24.04 Xubuntu, and gone on 24.10 on Kubuntu, without any ill effects.
I would say that busybox is from something else, but adding /var/snap' back fixes it is a real head scratcher. Maybe going over the snap removal process will reveal something.

Are you on zfs? my removal is very brutal, and  i would not post it in public. (Just for others not to break things)
```
ls -la /var/snap && df /var/snap
total 10
drwxr-xr-x  2 root root  2 Jul 17 10:23 .
drwxr-xr-x 16 root root 19 Jul 27 11:15 ..
Filesystem                        Type  Size  Used Avail Use% Mounted on
rpool/ROOT/ubuntu_n2r3zw/var/snap zfs   421G  128K  421G   1% /var/snap

```
**PLEASE NOTE, This is not for everyone just my method.
First is a good source for firefox:
```
sudo install -d -m 0755 /etc/apt/keyrings

```
```
wget -q https://packages.mozilla.org/apt/repo-signing-key.gpg -O- | sudo tee /etc/apt/keyrings/packages.mozilla.org.asc > /dev/null

```
```
 echo "deb [signed-by=/etc/apt/keyrings/packages.mozilla.org.asc] https://packages.mozilla.org/apt mozilla main" | sudo tee -a /etc/apt/sources.list.d/mozilla.list > /dev/null

```
```
 echo '
   Package: *
   Pin: origin packages.mozilla.org
   Pin-Priority: 1000
  ' | sudo tee /etc/apt/preferences.d/mozilla
```
For the rest 
snap list first, then removal:
```
sudo snap remove notes
sudo snap remove gtk-common-themes
sudo snap remove gnome-42-2204
sudo snap remove thunderbird firefox
sudo snap remove firmware-updater
sudo snap remove snapd-desktop-integration
sudo snap remove snap-store
sudo snap remove bare core22
sudo snap remove bare snapd
sudo apt remove snapd
sudo rm -rf /var/snap ## you first umount/var/snap
sudo apt-mark hold snapd
```

Extra actions by me:
```
sudo umount /var/snap
sudo rm -r /var/snap 
rm -rf ~/snap/
sudo cat <<EOF | sudo tee /etc/apt/preferences.d/nosnap.pref
   Package: snapd
   Pin: release a=*
   Pin-Priority: -10
   EOF
```
One more time just for proof, I removed /var/snap and see screenshot.

```
Message: filesystem 'rpool/ROOT/ubuntu_XXX/vdb*/snap' cannot be mounted at '/root/var/snap' due to canonicalization error: No such file or directory
```

---

### Post by VMC on 2024-07-28
No, I'm on Ext4. Still though, how does zfs, var snap relate?

---

### Post by #&amp;thj^% on 2024-07-28
> **VMC said:**
> No, I'm on Ext4. Still though, how does zfs, var snap relate?

It did not on 24.04, but with 24.10 it matters now....

I'm hoping jbicha will see this and reply if it's a new addition or a bug. 
Why, because of this:
```
Message: filesystem 'rpool/ROOT/ubuntu_XXX/vdb*/snap' cannot be mounted at '/root/var/snap' 
due to canonicalization error: No such file or directory
```
And:
```
df /var/snap/
Filesystem                        Type  Size  Used Avail Use% Mounted on
rpool/ROOT/ubuntu_n2r3zw/var/snap zfs   420G  128K  420G   1% /var/snap

```

---

### Post by VMC on 2024-07-29
Can't really file a big report on this because of Snap removal issue.

---

### Post by #&amp;thj^% on 2024-08-02
They don't call it a bug now, it's the way forward now. :P
Or in my case a way backward...Still deciding on weather this stuff is worth it anymore.

If it wasn't my passion to tinker, well you know the rest.....

---

