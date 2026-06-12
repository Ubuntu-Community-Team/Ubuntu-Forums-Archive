---
title: "HOWTO: Thumbnails for Xmind mind map files"
date: 2009-01-21
forum: Tutorials
---

### Post by rolfkleef on 2009-01-21
Building heavily on an [original post by Minio and the many follow-ups explaining how to do this for OpenOffice]("http://ubuntuforums.org/showthread.php?t=76566"):

Since [Xmind (mind mapping software)]("http://www.xmind.net/") is using a file format similar to that of OpenOffice, I adapted those scripts to also create thumbnails for my Xmind mind maps. It takes a little more effort to set up, because there is no mime type for Xmind files yet.

**1. Set up a mime type for Xmind files**

Xmind files are reported as application/zip, so we need to add our own mime type:

```
sudo gedit /usr/share/mime/packages/x-xmind.xml
```

I just hacked something together quickly, to let the system report files with extension ".xmind" as mime type application/x-xmind:

```
<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
   <mime-type type="application/x-xmind">
     <comment>Xmind mindmap</comment>
     <glob pattern="*.xmind"/>
   </mime-type>
</mime-info>
```

After you save this file, update the mime type database:

```
sudo update-mime-database /usr/share/mime
```

**2. Set up the script to make thumbnails of Xmind files**

```
sudo gedit /usr/bin/xmind-thumbnailer
```

Add the following script, and **make sure to check the ICON_PATH variable**, to make sure that icon exists there.

The thumbnailer is slightly different from the OpenOffice one: Xmind stores its thumbnail as a JPEG file with big dimensions (my test file had a 2091x973 pixels image). To make the thumbnail more icon-like, I've arbitrarily selected 200px in either direction as the maximum. (The application icon is 36x37 pixels, and should be recognizable in the thumbnail.)

```
#!/usr/bin/env python

import gnomevfs
import os
import sys
import zipfile
from PIL import Image, ImageEnhance

# Alter these varibles to change thumbnail look
ICON_PATH = "/usr/local/xmind/xmind-logo-36.png" # Change this path to alter icons
ICON_OPACITY = 0.6 #Opacity of the icon (between 0.0 and 1.0)
THUMBNAIL_BACKGROUND_COLOR = "white" # Color of the background

in_file_path = gnomevfs.get_local_path_from_uri(sys.argv[1])
out_file_path = sys.argv[2]
path_without_thumbs = os.getenv("HOME")+"/Templates" 

def get_icon(thumbnail_size):
	#Load icon
	icon = Image.open(ICON_PATH).convert("RGBA")
	#Set it's opacity
	icon = set_icon_opacity(icon,ICON_OPACITY)
	#And set it's position in thumbnail
	icon_posx=thumbnail_size[0]-icon.size[0]
	icon_posy=thumbnail_size[1]-icon.size[1]
	icon_width=thumbnail_size[0]
	icon_height=thumbnail_size[1]
	return {"image":icon,"position":(icon_posx,icon_posy,icon_width,icon_height)}	
	
def get_basic_thumbnail():
	#Find out if the file is not in Templates directory
	if in_file_path.find(path_without_thumbs)!=0:
		try:
			#Extract thumbnail from Xmind file and save it
			zip=zipfile.ZipFile(in_file_path,mode="r")
			picture=zip.read("Thumbnails/thumbnail.jpg")
			zip.close()
			thumbnail=open(out_file_path,"w")
			thumbnail.write(picture)
			thumbnail.write("/n")
			thumbnail.close()
			#Open saved thumbnail
			image=Image.open(out_file_path).convert("RGBA")
			if image.size[0]>200:
				image = image.resize((200,image.size[1]*200/image.size[0]))
			if image.size[1]>200:
				image = image.resize((image.size[0]*200/image.size[1],200))
			return {"suceeded":True,"image":image,"size":(image.size[0],image.size[1])}
		
		except:
			return {"suceeded":False}
	else:
		return {"suceeded":False}

# Nicked from http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/362879
def set_icon_opacity(icon,opacity):
	#Returns an image with reduced opacity.
	assert opacity >= 0 and opacity <= 1
	if icon.mode != 'RGBA':
		icon = icon.convert('RGBA')
	else:
		icon = icon.copy()
	alpha = icon.split()[3]
	alpha = ImageEnhance.Brightness(alpha).enhance(opacity)
	icon.putalpha(alpha)
	return icon

thumbnail=get_basic_thumbnail()
if thumbnail["suceeded"]:
	background=Image.new("RGB", thumbnail["size"], THUMBNAIL_BACKGROUND_COLOR)
	icon=get_icon(thumbnail["size"])
	thumbnail=thumbnail["image"]
	# Add thumbnail
	background.paste(thumbnail, None, thumbnail)
	# Add icon
	background.paste(icon["image"],icon["position"],icon["image"])
	# Save thumbnail
	background.save(out_file_path,"PNG")
```

Make the script executable:

```
sudo chmod +x /usr/bin/xmind-thumbnailer
```

**3. Tie the mime type and thumbnailer together**

Create the schema file that defines how things fit together, by adding this schema file:

```
sudo gedit /usr/share/gconf/schemas/xmind.schemas
```

Paste in the following code:

```
<gconfschemafile>
    <schemalist>

        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@x-xmind/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@x-xmind/enable</applyto>
            <owner>xmind-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@x-xmind/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@x-xmind/command</applyto>
            <owner>xmind-thumb</owner>
            <type>string</type>
            <default>/usr/bin/xmind-thumbnailer %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>
     
    </schemalist>
</gconfschemafile>
```

**4. Activate!**

Activating this new thumbnailer can be done by rebooting, or by installing the schema and restarting Nautilus:

```
gconftool-2 --install-schema-file /usr/share/gconf/schemas/xmind.schemas
sudo killall -9 nautilus
```

Note: you run gconftool-2 as "yourself", to get it installed in the right place: your home environment.

**THANKS!** [Minio]("http://ubuntuforums.org/member.php?u=2264") for starting the OpenOffice thread and supporting it! And everyone else over there for adding their findings! :-)

---

### Post by zigx on 2009-04-25
That worked like a Charm man, thank you so much!

---

### Post by balboost on 2009-05-03
yes, thank you !

it's really nice !

---

### Post by brightthings on 2009-09-03
Very cool. Thanks a lot!

I was having trouble getting the xmind icon to appear, but this will do fine.

---

### Post by rax0 on 2010-03-16
Thank you!

---

### Post by zbeekman on 2011-10-27
Oh, baby! I can't wait to add thumbnails to our HDF5 files. At least I'll be able to do this at home.... it would be nice if I could do this at work to... on RHEL5.... without root...

I don't even need the thumbnails to be gernarated automatically, if only there was a way i could associate an image as the thumbnail of a file....

Oh well.....

---

