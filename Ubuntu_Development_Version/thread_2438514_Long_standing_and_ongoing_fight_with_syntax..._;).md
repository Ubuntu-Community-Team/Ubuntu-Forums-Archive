---
title: "Long standing and ongoing fight with syntax... ;)"
date: 2020-03-13
forum: Ubuntu Development Version
---

### Post by zika on 2020-03-13
```
Setting up python3 (3.8.2-0ubuntu2) ...
running python rtupdate hooks for python3.8...
/usr/share/hplip/base/utils.py:2060: SyntaxWarning: "is" with a literal. Did you mean "=="?
  if weburl is "" or weburl is None:
/usr/share/hplip/check-plugin.py:116: SyntaxWarning: "is" with a literal. Did you mean "=="?
  if log_level is 'debug':
/usr/share/hplip/check.py:685: SyntaxWarning: "is not" with a literal. Did you mean "!="?
  if 'getfacl' not in g and '' is not g and 'file' not in g:
/usr/share/hplip/installer/core_install.py:2037: SyntaxWarning: "is" with a literal. Did you mean "=="?
  if home_dir is "":
/usr/share/hplip/ui5/devmgr_ext.py:15: SyntaxWarning: "is not" with a literal. Did you mean "!="?
  if self.latest_available_version is not "":
/usr/share/hplip/ui5/devmgr_ext.py:37: SyntaxWarning: "is not" with a literal. Did you mean "!="?
  if self.latest_available_version is not "":
running python post-rtupdate hooks for python3.8...
```

---

### Post by EuclideanCoffee on 2020-03-13
Yikes.

---

### Post by amano on 2020-03-14
My Python packages throw a lot of errors as well currently. 

Even AppStream is unhappy these days:

```
sudo appstreamcli refresh-cache --force --verbose
** (appstreamcli:6500): DEBUG: 15:05:15.103: Opening cache file: /tmp/appstream-cache-QFUHH0.mdb
(appstreamcli:6500): GLib-GIO-DEBUG: 15:05:15.106: _g_io_module_get_default: Found default implementation local (GLocalVfs) for &#8216;gio-vfs&#8217;
** (appstreamcli:6500): DEBUG: 15:05:15.107: Added /usr/share/app-info/xmls to XML metadata search path.
** (appstreamcli:6500): DEBUG: 15:05:15.107: Added /var/lib/app-info/yaml to YAML metadata search path.
** (appstreamcli:6500): DEBUG: 15:05:15.107: Added /var/cache/app-info/xmls to XML metadata search path.
(appstreamcli:6500): GLib-DEBUG: 15:05:15.391: posix_spawn avoided (fd close requested) 
(appstreamcli:6500): GLib-DEBUG: 15:05:15.427: posix_spawn avoided (fd close requested) 
(appstreamcli:6500): GLib-DEBUG: 15:05:15.679: posix_spawn avoided (fd close requested) 
(appstreamcli:6500): GLib-DEBUG: 15:05:15.832: posix_spawn avoided (fd close requested) 
(appstreamcli:6500): GLib-DEBUG: 15:05:16.109: posix_spawn avoided (fd close requested) 
(appstreamcli:6500): GLib-DEBUG: 15:05:16.127: posix_spawn avoided (fd close requested) 
** (appstreamcli:6500): DEBUG: 15:05:16.153: Refreshing AppStream cache
** (appstreamcli:6500): DEBUG: 15:05:16.153: Opening cache file: /var/cache/app-info/cache/de_DE.cache
** (appstreamcli:6500): DEBUG: 15:05:16.156: Cache set to floating mode.
** (appstreamcli:6500): DEBUG: 15:05:16.156: Searching for data in: /usr/share/app-info/xmls
** (appstreamcli:6500): DEBUG: 15:05:16.156: Searching for data in: /var/cache/app-info/xmls
** (appstreamcli:6500): DEBUG: 15:05:16.156: Searching for data in: /var/lib/app-info/yaml
** (appstreamcli:6500): DEBUG: 15:05:16.156: Reading: /usr/share/app-info/xmls/org.gnome.Software.Featured.xml
** (appstreamcli:6500): DEBUG: 15:05:16.159: Reading: /var/lib/app-info/yaml/archive.ubuntu.com_ubuntu_dists_focal_main_dep11_Components-amd64.yml.gz
** (appstreamcli:6500): DEBUG: 15:05:16.325: Reading: /var/lib/app-info/yaml/archive.ubuntu.com_ubuntu_dists_focal_universe_dep11_Components-amd64.yml.gz
** (appstreamcli:6500): DEBUG: 15:05:17.586: Reading: /var/lib/app-info/yaml/archive.ubuntu.com_ubuntu_dists_focal_multiverse_dep11_Components-amd64.yml.gz
** (appstreamcli:6500): DEBUG: 15:05:17.607: Replacing invalid component 'system/os/package/org.gnome.Todo.desktop' with new one.
** (appstreamcli:6500): DEBUG: 15:05:17.608: Replacing invalid component 'system/os/package/transmission-gtk.desktop' with new one.
** (appstreamcli:6500): DEBUG: 15:05:17.609: Replacing invalid component 'system/os/package/org.kde.kdenlive' with new one.
** (appstreamcli:6500): DEBUG: 15:05:17.609: Replacing invalid component 'system/os/package/org.gnome.Boxes.desktop' with new one.
** (appstreamcli:6500): DEBUG: 15:05:17.609: Replacing invalid component 'system/os/package/org.stellarium.Stellarium' with new one.
** (appstreamcli:6500): DEBUG: 15:05:17.610: Replacing invalid component 'system/os/package/org.gnome.FeedReader' with new one.
** (appstreamcli:6500): DEBUG: 15:05:17.610: Replacing invalid component 'system/os/package/org.gnome.SoundRecorder.desktop' with new one.
** (appstreamcli:6500): DEBUG: 15:05:17.611: Replacing invalid component 'system/os/package/org.gnome.Maps.desktop' with new one.
** (appstreamcli:6500): DEBUG: 15:05:17.611: Replacing invalid component 'system/os/package/org.gnome.Tetravex' with new one.
** (appstreamcli:6500): DEBUG: 15:05:17.611: Metadata ignored: Detected colliding IDs: system/os/package/fonts-nanum was already added with the same priority.
** (appstreamcli:6500): DEBUG: 15:05:17.612: Replacing invalid component 'system/os/package/org.gimp.GIMP' with new one.
** (appstreamcli:6500): DEBUG: 15:05:17.614: Replacing invalid component 'system/os/package/org.gnome.Polari.desktop' with new one.
** (appstreamcli:6500): DEBUG: 15:05:17.615: Stemming language is: de
** (appstreamcli:6500): DEBUG: 15:05:17.629: WARNING: Ignored component 'com.spotify.Client': The component is invalid.
** (appstreamcli:6500): DEBUG: 15:05:17.922: WARNING: Ignored component 'org.videolan.VLC': The component is invalid.
** (appstreamcli:6500): DEBUG: 15:05:17.962: WARNING: Ignored component 'com.github.calo001.fondo': The component is invalid.
** (appstreamcli:6500): DEBUG: 15:05:18.110: WARNING: Ignored component 'com.github.fabiocolacio.marker': The component is invalid.
** (appstreamcli:6500): DEBUG: 15:05:18.390: WARNING: Ignored component 'mypaint.desktop': The component is invalid.
** (appstreamcli:6500): DEBUG: 15:05:18.773: WARNING: Ignored component 'com.valvesoftware.Steam': The component is invalid.
** (appstreamcli:6500): DEBUG: 15:05:19.170: WARNING: Ignored component 'com.calibre_ebook.calibre': The component is invalid.
** (appstreamcli:6500): DEBUG: 15:05:19.280: WARNING: Ignored component 'org.gnome.Podcasts': The component is invalid.
** (appstreamcli:6500): DEBUG: 15:05:19.340: WARNING: Ignored component 'com.bitwarden.desktop': The component is invalid.
** (appstreamcli:6500): DEBUG: 15:05:19.585: WARNING: Ignored component 'de.wolfvollprecht.UberWriter': The component is invalid.
** (appstreamcli:6500): DEBUG: 15:05:19.786: WARNING: Ignored component 'net.sourceforge.Klavaro': The component is invalid.
** (appstreamcli:6500): DEBUG: 15:05:19.909: WARNING: Ignored component 'com.github.johnfactotum.Foliate': The component is invalid.
** (appstreamcli:6500): DEBUG: 15:05:19.991: WARNING: Ignored component 'com.slack.Slack': The component is invalid.
** (appstreamcli:6500): DEBUG: 15:05:20.030: WARNING: Ignored component 'inkscape.desktop': The component is invalid.
** (appstreamcli:6500): DEBUG: 15:05:20.226: WARNING: Ignored component 'fr.free.Homebank': The component is invalid.
** (appstreamcli:6500): DEBUG: 15:05:20.252: WARNING: Ignored component 'com.dropbox.Client': The component is invalid.
** (appstreamcli:6500): DEBUG: 15:05:20.273: WARNING: Ignored component 'com.github.junrrein.PDFSlicer': The component is invalid.
** (appstreamcli:6500): DEBUG: 15:05:20.476: WARNING: Ignored component 'org.darktable.Darktable': The component is invalid.
** (appstreamcli:6500): DEBUG: 15:05:20.989: Cache returned from floating mode (all changes are now persistent)
** (appstreamcli:6500): DEBUG: 15:05:20.991: Not clearing user cache: The cache was already empty.
The AppStream system cache was updated, but some components were ignored. Refer to the verbose log for more information.

```

---

