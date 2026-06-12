---
title: "How do you create a custom Freedesktop menu category?"
date: 2023-11-10
forum: Ubuntu/Debian BASED
---

### Post by isuzufan on 2023-11-10
I'm trying to create a custom top-level category to appear in my openbox menu along side Accessories, System, and the other standard categories. I've done research and everyone agrees you can do it in three easy steps:



[LIST=1]
[*]Create a security.menu file at /etc/xdg/menus/applications-merged/
[*]Create a security.directory file at /usr/share/desktop-directories/
[*]Create a appName.desktop file at ~/.local/share/applications/
[/LIST]


After creating the three files, the appName.desktop entry does indeed appear in my jgmenu, but under an **Other** category and not the **Security** category I created. For whatever reason, the menu doesn't recognize my new category and just sticks my app in the Other category because it doesn't know what to do. I've double-checked the `.menu` and `.directory` files multiple times, and I'm confident that I'm formatting them correctly, at least according to what I've read. (Contents of both files appear below.)


Is there anything else I should be doing? Thanks in advance.


**security.menu**


```
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
```


**security.directory**


```
[Desktop Entry]
Type=Directory
Encoding=UTF-8
Name=Security
Icon=org.gnome.dspy
```

---

### Post by MAFoElffen on 2023-11-10
> **isuzufan said:**
> I'm trying to create a custom top-level category to appear in my openbox menu along side Accessories, System, and the other standard categories. I've done research and everyone agrees you can do it in three easy steps:


[LIST=1]
[*]Create a security.menu file at /etc/xdg/menus/applications-merged/ 
[*]Create a security.directory file at /usr/share/desktop-directories/ 
[*]Create a appName.desktop file at ~/.local/share/applications/ 
[/LIST]
 
After creating the three files, the `appName.desktop` entry does indeed appear in my jgmenu, but under an **Other** category and not the **Security** category I created. For whatever reason, the menu doesn't recognize my new category and just sticks my app in the Other category because it doesn't know what to do. I've double-checked the `.menu` and `.directory` files multiple times, and I'm confident that I'm formatting them correctly, at least according to what I've read. (Contents of both files appear below.)

Is there anything else I should be doing? Thanks in advance.

**security.menu**
```

<!DOCTYPE Menu PUBLIC "-//freedesktop//DTD Menu 1.0//EN" "http://www.freedesktop.org/standards/menu-spec/menu-1.0.dtd">
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

```
**security.directory**
```

[Desktop Entry]
     Type=Directory
     Encoding=UTF-8
     Name=Security
     Icon=org.gnome.dspy

```

I'm sorry, but I've been both working in and teaching IT for over 35 years now. I had to format and indent things to be able to read it better. Not important with XML, but much easier to read and follow the logic. As an instructor teaching programming, I held students to be neat and format their code so it was easy to read... Is also a Forum Policy to wrap all code, commands and output within code tags... (you might want to edit your first post.)

I am familiar with OpenBox menu's. In the Ama-Gi Project LiveUSB, I had to create all my menu's for the on-demand DE, which I used OpenBox.

So you know that OpenBox Menu's are constrained by this limit right?
> 
**Syntax**

 A menu file must be entirely enclosed within "<openbox_menu>" and "</openbox_menu>" tags, as well as the appropriate XML declaration like so: 

Like this:
```

<?xml version="1.0" encoding="utf-8"?>
<openbox_menu xmlns="http://openbox.org/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://openbox.org/ file:///usr/share/openbox/menu.xsd">

  <menu
    id="ID"
    label="TITLE"
    icon="ICON"
  >

    <!-- this is a menu item, such as a program -->
    <item
      label="LABEL"
      icon="ICON"
    >
      ACTIONS
    </item>

    <!-- this is a menu header -->
    <separator
      label="Header"
    />

    <!-- this links to a sub menu -->
    <menu
      id="ID"
    />

    <!-- this is a horizontal line -->
    <separator />

    <!-- this also links to a sub menu, which is defined inline -->
    <menu
      id="ID"
      label="TITLE"
      icon="ICON"
    >
      <item
        label="LABEL"
        icon="ICON"
      >
        ACTIONS
      </item>
    </menu>

    <separator />

    <!-- this is a menu item -->
    <item
      label="LABEL"
      icon="ICON"
    >
      ACTIONS
    </item>
  </menu>
</openbox_menu>

```
So one file, except for what is autofilled by scripts such as pipe menu items or the Debian Menu... Which by that hook, you can include other sub_menu.xml files such as this one, right? Included like on of these lines:
```

 <file>/var/lib/openbox/debian-menu.xml</file>
     <!-- OR -->
 <file>debian-menu.xml</file>

```
Within the Menu Tags... Not relly documented, but is possible. Most of the time, people so like what the doc's say, that everything is declared inline within the menu.xml file.

The that is where that menu will plug in...

So where is your main menu XML where that is pulled into?

---

### Post by MAFoElffen on 2023-11-11
Nevermind... Different layout and structure. That is not really an OpenBox menu... LOL.

Dang...You are actually talking about this: [https://specifications.freedesktop.org/menu-spec/menu-spec-1.0.html](https://specifications.freedesktop.org/menu-spec/menu-spec-1.0.html)
> 
$XDG_CONFIG_DIRS/menus/applications-merged/               The default merge directories included in the               <DefaultMergeDirs> element.  By convention, third parties               may add new <Menu> files in this location to create their               own sub-menus.             
               Note that a system that uses either gnome-applications.menu or               kde-applications.menu depending on the desktop environment in               use must still use applications-merged as the default merge               directory in both cases.             
               Implementations may chose to use .menu files with names other               than application.menu for tasks or menus other than the main               application menu. In that case the first part of the name of               the default merge directory is derived from the name of the               .menu file.              
               For example in a system that uses a preferences.menu file to               describe an additional menu, the default merge directories               included in the <DefaultMergeDirs> element in the               preferences.menu file would become               $XDG_CONFIG_DIRS/menus/preferences-merged/             

And this: [https://specifications.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html](https://specifications.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html)

Let me look at that tomorrow...

---

### Post by isuzufan on 2023-11-11
@MAFoElffen
  
Thank you very much for the reply. Sorry about the formatting of my original post.  I tried, but the code formatting options weren't there.  I just discovered that they're visible if I click Go Advanced, so I'm good now.  I'm a new forum member, so thanks for the patience.

 I've worked with creating my own openbox menus in the past, but it was a while ago and I'm not even close to being an expert. The info you provided is great. I should clarify that I'm not trying to create an entire primary menu of my own.  Rather, I want to add custom top-level categories to the existing menu structure created by the developers of my distro (Sparky Linux). I want to work within their existing framework rather than start from scratch.

Below is a crude mockup of how my current jgmenu appears when I invoke it. I want to create a new Security category that appears between Internet and Settings.

> [Prepend Items]
Accessories
Graphics
Multimedia
Internet
Settings
System
...other standard FreeDesktop categories
 [Append Items] 

 
From my research in various forums (here and elsewhere), everyone agrees that I need to create a new security.menu file (in ~/.local/share/menus/applications-merged/) and a new security.directory file (in ~/.local/share/desktop-directories/). Then, for applications I want to have appear inside that Security category, I create a .desktop file (in ~/.local/share/applications) and populate the Category= key to Security. 

No one has ever said I need to modify the distro's default menus.  Is that what I'm missing? Do I need to do that?  

In /etc/xdg/menus/ I have three menus that came with the distro:

[LIST]
[*]applications.menu
[*]debian-menu.menu
[*]lxde-applications.menu
[/LIST]

I "think" that lxde-applications.menu is the primary menu since it has <MergeFile> links to  debian-menu.menu and also has the <DefaultMergedDirs/> tag which tells the menu to look for custom user menus (in either /etc/xdg/menus/applications-merged/ or ~/.local/share/menus/applications-merged/).  

If I understand your instructions correctly, do I need to add a <menu> entry for my custom Security category in the lxde-applications.menu file?  Something like below? You also mentioned a <File> link; where would that appear -- below the <Directory> tag or inside the <Include>? 

```
    <!-- Security -->
    <Menu>
        <Name>Security</Name>
        <Directory>security.directory</Directory>
        <Include>
            <And>
                <Category>security</Category>
            </And>
        </Include>
    </Menu> 
    <!-- End Security -->
```


Again, thanks very much for your time.

---

### Post by isuzufan on 2023-11-11
Ah!  Forgive me.  I didn't see your second reply before I submitted my response above.

---

### Post by MAFoElffen on 2023-11-11
Yes. My first reply was for OpenBox, with the format OpenBox uses for their menu XML.. 

After I posted that, I reread your first post, and figured out something... LOL. I had figured out, that OpenBox wasn't what you were doing... But hte confusion continued after that(?)

You keep saying "OpenBox"... Even in post #4. What you posted was more what Gnome & KDE do, which follows more of the standards set by freedesktop, then later in #4, you mentioned LXDE...

But the last version of Lubuntu that used LXDE was 18.04. Lubuntu 20.04 used LXQT, but still had the same menu system.

So what flavor and version are you using?

---

### Post by isuzufan on 2023-11-12
I'm using Sparky Linux (based on Debian testing).  I only use Openbox, no KDE or Gnome. 

Sorry if I'm using confusing terminology.  I don't know what to call this menu.  It's the right-click menu that appears in Openbox.  I explored the /etc/xdg/menus folder and found the three menus I mentioned above in #4. I assume that the Sparky devs are calling their primary menu lxde-application.menu.

---

### Post by MAFoElffen on 2023-11-12
Is the desktop LXDE with the menu in the lower left? Or does it have menu.xml files ~/.config/openbox" (user-specific directory) and/or at "/etc/xdg/openbox/?
```

ls ~/.config/openbox/*
/etc/xdg/openbox/

```
Or do you have freedesktop menus?
```

printenv | grep -E 'XDG_CONFIG_DIRS|XDG_DATA_DIRS'

```

If you do have OpenBox, there is a tool called 'obmenu' which is a GUI OpenBox Menu editor... I usually just edit those with an editor, because that was the last tool that was updated to work with newer versions of Linux (so for awhile it wasn't available)... That tool makes that easier. For freedesktop menu's, the GUI menu editor is called 'alacarte'...

---

### Post by isuzufan on 2023-11-13
No, I don't have LXDE at all; just Openbox.  Sparky Linux also offers an edition using LXQT, so I can only assume that they created their "minimalGUI" edition using packages from LXQT or LXDE(?)  

Therefore, there is no menu icon in the panel. (I'm using tint2 for the panel.)  And, no, there are no menu-related .xml files in the ~/.config/openbox/ directory. Just the rc.xml and also the autostart.sh.  

Running your other command ( [COLOR=#000000][FONT=&amp]printenv | grep -E 'XDG_CONFIG_DIRS|XDG_DATA_DIRS' )[/FONT][/COLOR] returns the following: 

```
XDG_DATA_DIRS=/home/jeff/.local/share/flatpak/exports/share:/var/lib/flatpak/exports/share:/usr/local/share:/usr/share
```

---

### Post by coffeecat on 2023-11-13
> **isuzufan said:**
> I'm using Sparky Linux (based on Debian testing).

Not Ubuntu or an Ubuntu flavour. *Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by MAFoElffen on 2023-11-14
See if your distro has 'obmenu' and use it to modify your menu... Even when I do what I do, to edit it myself in program editors, I would use that to verify it followed OpenBox's formating rules.

---

