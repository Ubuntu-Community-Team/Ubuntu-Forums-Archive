---
title: "vbox 4.0 gives VERR_SUPLIB_OWNER_NOT_ROOT"
date: 2011-02-25
forum: Virtualisation
---

### Post by bjamesv on 2011-02-25
Why is /usr not owned by root:root in Maverick?


ls -ld /usr shows:
```
drwxr-xr-x 1 2402 dip 80 2009-09-27 23:15 /usr
```

The problem is upgrading from VirtualBox 3.2 to 4.0.4 on maverick vm's wont launch with the following error:
(looks exactly like [http://www.virtualbox.org/ticket/7889](http://www.virtualbox.org/ticket/7889))

[SIZE="2"][COLOR="DimGray"]00:00:01.752 pdmR3LoadR0U: pszName="VMMR0.r0" rc=VERR_SUPLIB_OWNER_NOT_ROOT [COLOR="Red"]szErr="The owner is not root: '/usr'"[/COLOR]
00:00:01.752 VMSetError: /home/vbox/vbox-4.0.4/src/VBox/VMM/VMMR3/VM.cpp(579) int vmR3CreateU(UVM*, uint32_t, int (*)(VM*, void*), void*); rc=VERR_SUPLIB_OWNER_NOT_ROOT
00:00:01.752 VMSetError: Failed to load VMMR0.r0
00:00:01.752 VMSetError: /home/vbox/vbox-4.0.4/src/VBox/VMM/VMMR3/VM.cpp(350) int VMR3Create(uint32_t, const VMM2USERMETHODS*, void (*)(VM*, void*, int, const char*, unsigned int, const char*, const char*, char*), void*, int (*)(VM*, void*), void*, VM**); rc=VERR_SUPLIB_OWNER_NOT_ROOT
00:00:01.752 VMSetError: Unknown error creating VM
00:00:01.752 ERROR [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={515e8e8d-f932-4d8e-9f32-79a52aead882} aComponent={Console} aText={Failed to load VMMR0.r0 (VERR_SUPLIB_OWNER_NOT_ROOT).
00:00:01.752 Unknown error creating VM (VERR_SUPLIB_OWNER_NOT_ROOT)}, preserve=false
00:00:02.337 Power up failed (vrc=VERR_SUPLIB_OWNER_NOT_ROOT, rc=NS_ERROR_FAILURE (0X80004005))[/COLOR][/SIZE]

---

### Post by bjamesv on 2011-02-25
user does not seem to exist anymore
```
cat /etc/passwd | grep 2402
```

---

### Post by oregonbob on 2011-05-26
On my Ubuntu 11.04, somehow I was owner of folder "/usr/lib". I changed the owner to "chown root:root /usr/lib", note it is NOT recursive. That solved my errors after upgrading to 4.0.8.

---

### Post by ryoohki on 2011-08-29
This is not a vbox bug.

I had untared a tar file to usr/ while in / on purpose but files in the tar file were owned by a user not on my system and not root either.  I had expected the file alone to wind up in their respective directories but as it turned out, it changed the owners and perms all the way down the directory structure.

---

