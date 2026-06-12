---
title: "Support ODF Thumbnails in Ubuntu?"
date: 2009-02-08
forum: The Cafe
---

### Post by kevin11951 on 2009-02-08
Inside of every ODT, ODP, ODS, etc... is a thumbnail, but ubuntu does not show it for the icon, nor does it create its own, it just shows a generic "text file", etc...

any chance that thumbnails of ODF files will be in ubuntu soon?

(windows supports it of open office is installed :p)

---

### Post by MaxIBoy on 2009-02-08
I think that's a GNOME thing.

===some time passes===
Just found this:
[http://ubuntuforums.org/showthread.php?t=76566](http://ubuntuforums.org/showthread.php?t=76566)

I'm gonna try it out, I've been wanting this as well.

---

### Post by hanzomon4 on 2009-02-08
Come on foss you've got the source...

---

### Post by kevin11951 on 2009-02-08
WORKS FOR OOO 3

Digg it: [http://digg.com/linux_unix/Show_Live_Thumbnails_For_OO_o_3_Files_In_Ubuntu](http://digg.com/linux_unix/Show_Live_Thumbnails_For_OO_o_3_Files_In_Ubuntu)

ALSO: I got the info for this from: [http://ubuntuforums.org/showthread.php?t=76566](http://ubuntuforums.org/showthread.php?t=76566)

```
sudo gedit /usr/bin/ooo2-thumbnailer
```

Add:

```
#!/usr/bin/python

import zipfile
import sys
import os
import gnomevfs
from PIL import Image, ImageEnhance

# Alter these varibles to change thumbnail look
BaseIconPath = "/usr/share/icons/hicolor/48x48/apps/" # Change this path to alter icons

# Opacity of the icon
IconOpacity = 0.8
# Color of the background
BackgroundColor = "white"

# Two types of icons Ubuntu and Ooo2
#iconPreFix = "openofficeorg-20-" # Ooo2 Stock
iconPreFix = "openofficeorg3-" # Ubuntu

"""
Open Document Types
================
	Text 				.odt 	
	Spreadsheet 		.ods 
	Presentation 		.odp 
	Drawing 			.odg 
	Chart 			.odc
	Formula 			.odf 
	Database 			.odb 
	Image 			.odi 
	Master Document	.odm
"""

# Nicked from http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/362879
def reduce_opacity(im, opacity):
    """Returns an image with reduced opacity."""
    assert opacity >= 0 and opacity <= 1
    if im.mode != 'RGBA':
        im = im.convert('RGBA')
    else:
        im = im.copy()
    alpha = im.split()[3]
    alpha = ImageEnhance.Brightness(alpha).enhance(opacity)
    im.putalpha(alpha)
    return im

inURL=gnomevfs.get_local_path_from_uri(sys.argv[1])
outURL=sys.argv[2]
nothumbURL=os.getenv("HOME")+"/Templates"
nothumbList=nothumbURL.split(os.sep)
inList=inURL.split(os.sep)

if inList[1]==nothumbList[1] and inList[2]==nothumbList[2] and inList[3]!=nothumbList[3]:
	zip=zipfile.ZipFile(inURL,mode="r")
	picture=zip.read("Thumbnails/thumbnail.png")
	zip.close()
	thumbnail=open(outURL,"w")
	thumbnail.write(picture)
	thumbnail.write("/n")
	thumbnail.close()

	# Get File Extension    
	fileExtension = inURL[ len(inURL)-3 :].lower()

	# Select Document Type
	iconFile = "writer"
	if fileExtension == "ods":
		iconFile = "calc"
	elif fileExtension == "odp":
		iconFile = "impress"
	elif fileExtension == "odg":
		iconFile = "draw"
	elif fileExtension == "odp":
		iconFile = "calc"
	elif fileExtension == "odf":
		iconFile = "math"
	elif fileExtension == "odi":
		iconFile = "draw"
	elif fileExtension == "odi":
		iconFile = "template"

	thumbnail = Image.open(outURL).convert("RGBA")

	# Load icon
	icon = Image.open(BaseIconPath + iconPreFix+ iconFile +".png").convert("RGBA")
	icon = reduce_opacity(icon, IconOpacity)
	# Create new img with white bg
	final = Image.new("RGB", (thumbnail.size[0],thumbnail.size[1]), BackgroundColor)
	# Add thumbnail
	final.paste(thumbnail, None, thumbnail)
	# Add icon
	x = final.size[0] - icon.size[0]
	y = final.size[1]-icon.size[1]
	w = x + icon.size[0]
	h = y + icon.size[1]
	final.paste(icon, (x,y,w,h), icon)
	# Save thumbnail
	final.save(outURL, "PNG")
```

Save It:

```
sudo chmod +x /usr/bin/ooo2-thumbnailer
```

```
sudo gedit /usr/share/gconf/schemas/ooo2.schemas
```

Enter:

```
<gconfschemafile>
    <schemalist>

        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.text/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.text/enable</applyto>
            <owner>ooo2-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.text/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.text/command</applyto>
            <owner>ooo2-thumb</owner>
            <type>string</type>
            <default>/usr/bin/ooo2-thumbnailer %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>
     

        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.spreadsheet/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.spreadsheet/enable</applyto>
            <owner>ooo2-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.spreadsheet/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.spreadsheet/command</applyto>
            <owner>ooo2-thumb</owner>
            <type>string</type>
            <default>/usr/bin/ooo2-thumbnailer %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>
	<schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.graphics/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.graphics/enable</applyto>
            <owner>ooo2-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.graphics/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.graphics/command</applyto>
            <owner>ooo2-thumb</owner>
            <type>string</type>
            <default>/usr/bin/ooo2-thumbnailer %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>
	<schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.formula/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.formula/enable</applyto>
            <owner>ooo2-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.formula/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.formula/command</applyto>
            <owner>ooo2-thumb</owner>
            <type>string</type>
            <default>/usr/bin/ooo2-thumbnailer %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>
        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.presentation/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.presentation/enable</applyto>
            <owner>ooo2-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.presentation/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.presentation/command</applyto>
            <owner>ooo2-thumb</owner>
            <type>string</type>
            <default>/usr/bin/ooo2-thumbnailer %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


<schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.sun.xml.writer/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.sun.xml.writer/enable</applyto>
            <owner>ooo2-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.sun.xml.writer/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.sun.xml.writer/command</applyto>
            <owner>ooo2-thumb</owner>
            <type>string</type>
            <default>/usr/bin/ooo2-thumbnailer %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>
     

        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.sun.xml.calc/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.sun.xml.calc/enable</applyto>
            <owner>ooo2-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.sun.xml.calc/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.sun.xml.calc/command</applyto>
            <owner>ooo2-thumb</owner>
            <type>string</type>
            <default>/usr/bin/ooo2-thumbnailer %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.sun.xml.draw/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.sun.xml.draw/enable</applyto>
            <owner>ooo2-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.sun.xml.draw/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.sun.xml.draw/command</applyto>
            <owner>ooo2-thumb</owner>
            <type>string</type>
            <default>/usr/bin/ooo2-thumbnailer %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>
	
	<schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.sun.xml.math/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.sun.xml.math/enable</applyto>
            <owner>ooo2-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.sun.xml.math/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.sun.xml.math/command</applyto>
            <owner>ooo2-thumb</owner>
            <type>string</type>
            <default>/usr/bin/ooo2-thumbnailer %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>
	<schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.sun.xml.impress/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.sun.xml.impress/enable</applyto>
            <owner>ooo2-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.sun.xml.impress/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.sun.xml.impress/command</applyto>
            <owner>ooo2-thumb</owner>
            <type>string</type>
            <default>/usr/bin/ooo2-thumbnailer %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>

    </schemalist>
</gconfschemafile>
```

Save It:

Reboot or:

```
gconftool-2 --install-schema-file /usr/share/gconf/schemas/ooo2.schemas
```

```
killall -9 nautilus
```

---

### Post by zekopeko on 2009-02-08
> **kevin11951 said:**
> WORKS FOR OOO 3

Digg it: [http://digg.com/linux_unix/Show_Live_Thumbnails_For_OO_o_3_Files_In_Ubuntu](http://digg.com/linux_unix/Show_Live_Thumbnails_For_OO_o_3_Files_In_Ubuntu)

```
sudo gedit /usr/bin/ooo2-thumbnailer
```

Add:

[CODE]#!/usr/bin/python

import zipfile
import sys
import os
import gnomevfs
from PIL import Image, ImageEnhance

/cut

aaaaaaa nothing better then stealing another's work and passing it as your's then submitting it to digg.

---

### Post by kevin11951 on 2009-02-08
> **zekopeko said:**
> aaaaaaa nothing better then stealing another's work and passing it as your's then submitting it to digg.

:oops:  Thats not what im doing!  Is that what it looks like? I am just trying to help...

---

### Post by MaxIBoy on 2009-02-08
I was messing with that script for a while last night, and it didn't do anything for me...


EDIT: Okay, I now know the problem! See my post in the thread I found this script in.

---

### Post by zekopeko on 2009-02-08
> **kevin11951 said:**
> :oops:  Thats not what im doing!  Is that what it looks like? I am just trying to help...

you could have compiled your post at the end of the original thread and then link to it.

---

### Post by kevin11951 on 2009-02-08
> **MaxIBoy said:**
> I was messing with that script for a while last night, and it didn't do anything for me...

do you have open office 2 or 3, three needs to be changed a little, the above howto has that change in it.

---

