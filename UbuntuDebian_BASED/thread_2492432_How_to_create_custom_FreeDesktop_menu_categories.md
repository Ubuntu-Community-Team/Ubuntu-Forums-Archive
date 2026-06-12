---
title: "How to create custom FreeDesktop menu categories?"
date: 2023-11-10
forum: Ubuntu/Debian BASED
---

### Post by isuzufan on 2023-11-10
I'm trying to create a custom top-level category to appear in my openbox menu along side Accessories, System, and the other standard categories. (I'm running Sparky Linux Minimal) I've done research and everyone agrees you can do it in three easy steps:


 1. Create a security.menu file at /etc/xdg/menus/applications-merged/
 2. Create a security.directory file at /usr/share/desktop-directories/
 3. Create a appName.desktop file at ~/.local/share/applications/


After creating the three files, the `appName.desktop` entry does indeed appear in my jgmenu, but under an **Other** category and not the **Security** category I created. For whatever reason, the menu doesn't recognize my new category and just sticks my app in the Other category because it doesn't know what to do. I've double-checked the `.menu` and `.directory` files multiple times, and I'm confident that I'm formatting them correctly, at least according to what I've read. (Contents of both files appear below.)


Is there anything else I should be doing?  Thanks in advance. 


**security.menu**


<!DOCTYPE Menu PUBLIC "-//freedesktop//DTD Menu 1.0//EN"
"http://www.freedesktop.org/standards/menu-spec/menu-1.0.dtd"> 
  <Menu> 
    <Name>Applications</Name>
    <Menu>
      <Name>Security</Name>
      <Directory>security.directory</Directory>
      <Include>
        <And>
        <Category>Security</Category>
        </And>
      </Include>
    </Menu>
  </Menu>


**security.directory**


Desktop Entry] 
Type=Directory 
Encoding=UTF-8 
Name=Security
Icon=org.gnome.dspy

---

### Post by QIII on 2023-11-11
Duplicate.  See [https://ubuntuforums.org/showthread.php?t=2492433](https://ubuntuforums.org/showthread.php?t=2492433)

Closed.

---

