---
title: "Gparted works fine in Wayland"
date: 2019-05-25
forum: Ubuntu Development Version
---

### Post by corradoventu on 2019-05-25
Today forgetting to be in wayland session I started gparted and ... it works
```
corrado@corrado-p7-ee-0507:~$ inxi -Gx
Graphics:  Device-1: Intel HD Graphics 630 vendor: ASRock driver: i915 v: kernel 
           bus ID: 00:02.0 
           Display: wayland server: X.Org 1.20.4 driver: i915 resolution: 1920x1080~60Hz 
           OpenGL: renderer: Mesa DRI Intel HD Graphics 630 (Kaby Lake GT2) v: 4.5 Mesa 19.0.2 
           direct render: Yes 
corrado@corrado-p7-ee-0507:~$ gparted
localuser:root being added to access control list
Unit tmp.mount does not exist, proceeding anyway.
Gtk-Message: 21:49:41.721: Failed to load module "canberra-gtk-module"
======================
libparted : 3.2
======================
localuser:root being removed from access control list
corrado@corrado-p7-ee-0507:~$ 

```
due to this trick in /usr/sbin/gparted
	```
# Interim workaround to allow GParted run by root access to the
	# X11 display server under Wayland.  If configured with
	# './configure --enable-xhost-root', the xhost command is
	# available and root has not been granted access to the X11
	# display via xhost, then grant access.
	#
	ENABLE_XHOST_ROOT=yes
	GRANTED_XHOST_ROOT=no
	if test "x$ENABLE_XHOST_ROOT" = 'xyes' && xhost 1> /dev/null 2>&1; then
		if ! xhost | grep -qi 'SI:localuser:root$'; then
			xhost +SI:localuser:root
			GRANTED_XHOST_ROOT=yes
		fi
	fi

	#
	# Run gparted as root.
	#
	pkexec --disable-internal-agent '/usr/sbin/gparted' "$@"
	status=$?

	#
	# Revoke root access to the X11 display, only if we granted it.
	#
	if test "x$GRANTED_XHOST_ROOT" = 'xyes'; then
		xhost -SI:localuser:root
	fi
	exit $status
```

---

