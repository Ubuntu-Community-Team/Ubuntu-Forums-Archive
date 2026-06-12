---
title: "Ubuntu 14: Extra notes on folders and files with default emblem"
date: 2015-06-25
forum: Tutorials
---

### Post by rcruz-wild-spain on 2015-06-25
**pre-requisites:** gvfs command-set available, and emblems installed and working
**Solution tested on Ubuntu 14**

**1 -** create a void file named "Notes" with following content:

```
#!/bin/bash
for uri in "$@";
do
(Titulo="${uri#/}" # Elimina la ruta del nombre del archivo
Notas="`gvfs-info -a metadata::annotation "$uri" | tail -c +37 | head -c -1 | zenity --text-info --editable --title="$Titulo" --height=600 --width=500`"
# No actualiza las notas si se cancela
if [[ $? == 0 ]]; then
gvfs-set-attribute -t string "$uri" metadata::annotation "$Notas"
gvfs-set-attribute -t stringv "$uri" metadata::emblems "gnome-info"
fi)&
done
```

**2 -** Move the file to $HOME/.local/share/nautilus/scripts/

**3 - **Apply execution rights from command line

```
chmod a+x "$HOME/.local/share/nautilus/scripts/Notes"
```

Ready! right-click to a folder or file, and "Notes" will be available under "Scripts->Notes" (usually below "Open With" option). The emblem tagged as gnome-info will apply automaticly as a visual indicator that the file or folder has additional notes.

Another solution could be the package nautilus-notes (available on ubuntu repositories), but this don't change the emblems. I prefer a visual indicator for files with additional notes... more easy management tasks

Best regards, ):P

---

