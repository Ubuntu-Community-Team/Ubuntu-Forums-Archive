---
title: "Ubuntu 22.04 (Jammy Jellyfish) Chrome 104.0.5112.79 apparmor profile"
date: 2022-08-11
forum: Security
---

### Post by vbgf3 on 2022-08-11
> 
Chrome version 104.0.5112.79  Ubuntu version 22.04 LTS (Jammy Jellyfish) Date:2022-08-11




#include <tunables/global>




profile /opt/google/chrome/chrome {




  #include <abstractions/fonts>
  #include <abstractions/gnome>
  
  network inet  stream,
  network inet6 stream,
  network inet  dgram,
  network inet6 dgram,
  network inet  seqpacket, 
  network inet6 seqpacket, 
  
  capability sys_chroot,






  /etc/udev/udev.conf r,
  /etc/localtime      r,
  /etc/machine-id     r,
  /etc/os-release     r,
  /etc/fonts/**       r,
  /etc/gtk-3.0/settings.ini   r,
  
/lib/x86_64-linux-gnu/libdl.so.2                 mr,
/lib/x86_64-linux-gnu/libpthread.so.0            mr,
/lib/x86_64-linux-gnu/libgobject-2.0.so.0        mr,
/lib/x86_64-linux-gnu/libnss3.so                 mr,
/lib/x86_64-linux-gnu/libnssutil3.so             mr,
/lib/x86_64-linux-gnu/libsmime3.so               mr,
/lib/x86_64-linux-gnu/libnspr4.so                mr,
/lib/x86_64-linux-gnu/libatk-1.0.so.0            mr,
/lib/x86_64-linux-gnu/libatk-bridge-2.0.so.0     mr,
/lib/x86_64-linux-gnu/libgio-2.0.so.0            mr,
/lib/x86_64-linux-gnu/libdrm.so.2                mr,
/lib/x86_64-linux-gnu/libdbus-1.so.3             mr,
/lib/x86_64-linux-gnu/libexpat.so.1              mr,
/lib/x86_64-linux-gnu/libm.so.6                  mr,
/lib/x86_64-linux-gnu/libX11.so.6                mr,
/lib/x86_64-linux-gnu/libXcomposite.so.1         mr,
/lib/x86_64-linux-gnu/libXdamage.so.1            mr,
/lib/x86_64-linux-gnu/libXext.so.6               mr,
/lib/x86_64-linux-gnu/libXfixes.so.3             mr,
/lib/x86_64-linux-gnu/libXrandr.so.2             mr,
/lib/x86_64-linux-gnu/libgbm.so.1                mr,
/lib/x86_64-linux-gnu/libxcb.so.1                mr,
/lib/x86_64-linux-gnu/libxkbcommon.so.0          mr,
/lib/x86_64-linux-gnu/libpango-1.0.so.0          mr,
/lib/x86_64-linux-gnu/libcairo.so.2              mr,
/lib/x86_64-linux-gnu/libasound.so.2             mr,
/lib/x86_64-linux-gnu/libatspi.so.0              mr,
/lib/x86_64-linux-gnu/libgcc_s.so.1              mr,
/lib/x86_64-linux-gnu/libc.so.6                  mr,
/lib/x86_64-linux-gnu/libffi.so.8                mr,
/lib/x86_64-linux-gnu/libpcre.so.3               mr,
/lib/x86_64-linux-gnu/libplc4.so                 mr,
/lib/x86_64-linux-gnu/libplds4.so                mr,
/lib/x86_64-linux-gnu/libgssapi_krb5.so.2        mr,
/lib/x86_64-linux-gnu/libavahi-common.so.3       mr,
/lib/x86_64-linux-gnu/libavahi-client.so.3       mr,
/lib/x86_64-linux-gnu/libgnutls.so.30            mr,
/lib/x86_64-linux-gnu/libz.so.1                  mr,
/lib/x86_64-linux-gnu/libgmodule-2.0.so.0        mr,
/lib/x86_64-linux-gnu/libmount.so.1              mr,
/lib/x86_64-linux-gnu/libselinux.so.1            mr,
/lib/x86_64-linux-gnu/libsystemd.so.0            mr,
/lib/x86_64-linux-gnu/libXrender.so.1            mr,
/lib/x86_64-linux-gnu/libwayland-server.so.0     mr,
/lib/x86_64-linux-gnu/libstdc++.so.6             mr,
/lib/x86_64-linux-gnu/libXau.so.6                mr,
/lib/x86_64-linux-gnu/libXdmcp.so.6              mr,
/lib/x86_64-linux-gnu/libfribidi.so.0            mr,
/lib/x86_64-linux-gnu/libthai.so.0               mr,
/lib/x86_64-linux-gnu/libharfbuzz.so.0           mr,
/lib/x86_64-linux-gnu/libpixman-1.so.0           mr,
/lib/x86_64-linux-gnu/libfontconfig.so.1         mr,
/lib/x86_64-linux-gnu/libfreetype.so.6           mr,
/lib/x86_64-linux-gnu/libpng16.so.16             mr,
/lib/x86_64-linux-gnu/libxcb-shm.so.0            mr,
/lib/x86_64-linux-gnu/libxcb-render.so.0         mr,
/lib/x86_64-linux-gnu/libXi.so.6                 mr,
/lib/x86_64-linux-gnu/libkrb5.so.3               mr,
/lib/x86_64-linux-gnu/libk5crypto.so.3           mr,
/lib/x86_64-linux-gnu/libcom_err.so.2            mr,
/lib/x86_64-linux-gnu/libkrb5support.so.0        mr,
/lib/x86_64-linux-gnu/libp11-kit.so.0            mr,
/lib/x86_64-linux-gnu/libidn2.so.0               mr,
/lib/x86_64-linux-gnu/libunistring.so.2          mr,
/lib/x86_64-linux-gnu/libtasn1.so.6              mr,
/lib/x86_64-linux-gnu/libnettle.so.8             mr,
/lib/x86_64-linux-gnu/libhogweed.so.6            mr,
/lib/x86_64-linux-gnu/libblkid.so.1              mr,
/lib/x86_64-linux-gnu/libgmp.so.10               mr,
/lib/x86_64-linux-gnu/libpcre2-8.so.0            mr,
/lib/x86_64-linux-gnu/liblzma.so.5               mr,
/lib/x86_64-linux-gnu/libzstd.so.1               mr,
/lib/x86_64-linux-gnu/liblz4.so.1                mr,
/lib/x86_64-linux-gnu/libcap.so.2                mr,
/lib/x86_64-linux-gnu/libgcrypt.so.20            mr,
/lib/x86_64-linux-gnu/libbsd.so.0                mr,
/lib/x86_64-linux-gnu/libdatrie.so.1             mr,
/lib/x86_64-linux-gnu/libgraphite2.so.3          mr,
/lib/x86_64-linux-gnu/libuuid.so.1               mr,
/lib/x86_64-linux-gnu/libbrotlidec.so.1          mr,
/lib/x86_64-linux-gnu/libkeyutils.so.1           mr,
/lib/x86_64-linux-gnu/libresolv.so.2             mr,
/lib/x86_64-linux-gnu/libgpg-error.so.0          mr,
/lib/x86_64-linux-gnu/libmd.so.0                 mr,
/lib/x86_64-linux-gnu/libgtk-3.so.0              mr,
/lib/x86_64-linux-gnu/libpangocairo-1.0.so.0     mr,
/lib/x86_64-linux-gnu/libcairo-gobject.so.2      mr,
/lib/x86_64-linux-gnu/libgdk_pixbuf-2.0.so.0     mr,
/lib/x86_64-linux-gnu/libepoxy.so.0              mr,
/lib/x86_64-linux-gnu/libpangoft2-1.0.so.0       mr,
/lib/x86_64-linux-gnu/libXinerama.so.1           mr,
/lib/x86_64-linux-gnu/libXcursor.so.1            mr,
/lib/x86_64-linux-gnu/libwayland-cursor.so.0     mr,
/lib/x86_64-linux-gnu/libwayland-egl.so.1        mr,
/lib/x86_64-linux-gnu/libwayland-client.so.0     mr,
/lib/x86_64-linux-gnu/libjpeg.so.8               mr,
/lib/x86_64-linux-gnu/libX11-xcb.so.1            mr,
/lib/x86_64-linux-gnu/libsecret-1.so.0           mr,
/lib/x86_64-linux-gnu/libcanberra-gtk3.so.0      mr,
/lib/x86_64-linux-gnu/libcanberra.so.0           mr,
/lib/x86_64-linux-gnu/libvorbisfile.so.3         mr,
/lib/x86_64-linux-gnu/libtdb.so.1                mr,
/lib/x86_64-linux-gnu/libltdl.so.7               mr,
/lib/x86_64-linux-gnu/libvorbis.so.0             mr,
/lib/x86_64-linux-gnu/libogg.so.0                mr,
/lib/x86_64-linux-gnu/librsvg-2.so.2             mr,
/lib/x86_64-linux-gnu/libxml2.so.2               mr,
/lib/x86_64-linux-gnu/libicuuc.so.70             mr,
/lib/x86_64-linux-gnu/libicudata.so.70           mr,
/lib/x86_64-linux-gnu/libibus-1.0.so.5           mr,
 
  /lib64/**                   r,


  /opt/google/chrome/**         mrix,




  owner /run/user/[0-9]*/.mutter-Xwaylandauth.*    r,   
   
  /usr/share/locale         r,
  /usr/share/zoneinfo/**    r,
  /usr/share/fontconfig/**  r,
  /usr/share/fonts/**       r,
  /usr/share/icons/**       r,
  /usr/share/locale-langpack/**  r,
  /usr/share/pixmaps/**     r,
  /usr/share/ubuntu/**      r,
  /usr/share/themes/**      r,
  /usr/share/X11/**         r, 
  /usr/share/glib-2.0/**    r,
  /usr/share/dconf/**       r,
  /usr/share/mime.**        r,
  /usr/share/mime/**        r,
  /usr/local/share/**       r,
  
/usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache                     mr,
/usr/lib/x86_64-linux-gnu/gio/modules                                   mr,
/usr/lib/x86_64-linux-gnu/gio/modules/giomodule.cache                   mr,
/usr/lib/x86_64-linux-gnu/gio/modules/libgvfsdbus.so                    mr,
/usr/lib/x86_64-linux-gnu/gio/modules/libgioremote-volume-monitor.so    mr,
/usr/lib/x86_64-linux-gnu/gio/modules/libgiognutls.so                   mr,
/usr/lib/x86_64-linux-gnu/gio/modules/libgiolibproxy.so                 mr,
/usr/lib/x86_64-linux-gnu/gio/modules/libgiognomeproxy.so               mr,
/usr/lib/x86_64-linux-gnu/gio/modules/libgioenvironmentproxy.so         mr,
/usr/lib/x86_64-linux-gnu/gio/modules/libdconfsettings.so               mr,
/usr/lib/x86_64-linux-gnu/gio/modules/libgvfsdbus.so                    mr,
/usr/lib/x86_64-linux-gnu/gvfs/glibc-hwcaps/x86-64-v3/libgvfscommon.so  mr,
/usr/lib/x86_64-linux-gnu/gvfs/libgvfscommon.so                         mr,
/usr/lib/x86_64-linux-gnu/gvfs/modules                                  mr,
/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache           mr,
/usr/lib/x86_64-linux-gnu/gtk-3.0/modules/libcanberra-gtk-module.so     mr,
/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so     mr,
/usr/lib/x86_64-linux-gnu/gtk-3.0/3.0.0/immodules.cache                 mr,
/usr/lib/x86_64-linux-gnu/gtk-3.0/3.0.0/immodules/im-ibus.so            mr, 
  /usr/lib/locale/locale-archive                  r,
  /usr/lib/os-release       r,
  
  /sys/devices/system/cpu                                   r,


  /tmp/.com.google.Chrome.*/ rw,
  /tmp/.com.google.Chrome.*/Singleton* rw,  
  
 
  /dev/shm/.com.google*           rw,  


  /proc/filesystems                   r,
  /proc/self/stat                     r,
  /proc/stat                          r,
  /proc/self/exe                      r,
  /proc/self/cmdline                  r,
  /proc/sys/kernel/yama/ptrace_scope  r,
  /proc/@{pid}/oom_score_adj          w,
  /proc/@{pid}/stat                   r,
  /proc/@{pid}/status                 r,
  /proc/@{pid}/statm                  r,
  
  /var/cache/fontconfig/**            r,                    
  /var/lib/dbus/machine-id            r,
  
  owner @{HOME}/Downloads/**               rw,
  owner @{HOME}/.config/google-chrome/**   rwk,
  owner @{HOME}/.config/ibus/bus           rw,
  owner @{HOME}/.cache/google-chrome/Default/**       rw,
  
}




A minimalist apparmor profile as a profile is supposed to be.

---

