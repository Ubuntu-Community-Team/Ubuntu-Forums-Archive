---
title: "how to change back the icon of pdf files after installing adobe reader"
date: 2008-02-16
forum: The Cafe
---

### Post by htor on 2008-02-16
here:

> for icon_size in 16 22 24 32 48 64 128; do
sudo xdg-icon-resource uninstall --novendor --context apps --size $icon_size "/opt/Adobe/Reader8/Resource/Icons/${icon_size}x${icon_size}/AdobeReader8.png"
sudo xdg-icon-resource uninstall --novendor --context apps --size $icon_size "/opt/Adobe/Reader8/Resource/Icons/${icon_size}x${icon_size}/adobe.pdf.png"
sudo xdg-icon-resource uninstall --novendor --context mimetypes --size $icon_size "/opt/Adobe/Reader8/Resource/Icons/${icon_size}x${icon_size}/adobe.pdf.png" 'application-pdf'
sudo xdg-icon-resource uninstall --novendor --context apps --size $icon_size "/opt/Adobe/Reader8/Resource/Icons/${icon_size}x${icon_size}/vnd.fdf.png"
sudo xdg-icon-resource uninstall --novendor --context mimetypes --size $icon_size "/opt/Adobe/Reader8/Resource/Icons/${icon_size}x${icon_size}/vnd.fdf.png" 'application-fdf'
sudo xdg-icon-resource uninstall --novendor --context apps --size $icon_size "/opt/Adobe/Reader8/Resource/Icons/${icon_size}x${icon_size}/vnd.adobe.pdx.png"
sudo xdg-icon-resource uninstall --novendor --context mimetypes --size $icon_size "/opt/Adobe/Reader8/Resource/Icons/${icon_size}x${icon_size}/vnd.adobe.pdx.png" 'application-pdx'
sudo xdg-icon-resource uninstall --novendor --context apps --size $icon_size "/opt/Adobe/Reader8/Resource/Icons/${icon_size}x${icon_size}/vnd.adobe.xdp+xml.png"
sudo xdg-icon-resource uninstall --novendor --context mimetypes --size $icon_size "/opt/Adobe/Reader8/Resource/Icons/${icon_size}x${icon_size}/vnd.adobe.xdp+xml.png" 'application-xdp+xml'
sudo xdg-icon-resource uninstall --novendor --context apps --size $icon_size "/opt/Adobe/Reader8/Resource/Icons/${icon_size}x${icon_size}/vnd.adobe.xfdf.png"
sudo xdg-icon-resource uninstall --novendor --context mimetypes --size $icon_size "/opt/Adobe/Reader8/Resource/Icons/${icon_size}x${icon_size}/vnd.adobe.xfdf.png" 'application-xfdf'
done

---

### Post by hhhhhx on 2008-02-16
wait, what do you want?

---

### Post by htor on 2008-02-16
when you install adobe reader in ubuntu, it changes the defaut pdf file icon from the gnome's icon to adobe's icon (that looks like in windows).   
I  mentioned the solution.

---

### Post by htor on 2008-02-16
look at the attached picture if you don't understand what I mean.

---

