---
title: "burn video dvd without k3b?"
date: 2008-05-22
forum: Ubuntu Studio
---

### Post by troupa on 2008-05-22
is there another app to burn video DVD?  k3b (any kde app) totally borks my synaptics touchpad.

---

### Post by Creative2 on 2008-05-23
try to man growisofs 

it should be 

growisofs -Z /dev/dvd -R -J 'YOURFILESHERE'

---

### Post by troupa on 2008-05-23
Thanks.  Can do.  
Ya'd think GNOME woulda stuck it in some kinda GUI by now.  DVD burning's been around for years, after all.  I thinks this is gonna send me set me to spending more time finding out why instead of burning this dvd now. :lolflag:

---

### Post by aeiah on 2008-05-23
doesnt brasero do the same is k3b? i dont use either for burning dvds though, mind. what do you mean by burning dvds? do you already have the dvd file structure with all the vobs and stuff in VIDEO_TS etc?

---

### Post by Jonie on 2008-05-24
DVD-Videos are in udf format, apps other than k3b or nero linux (commercial) will let you do data dvd (iso9660) with dvd-video compliant file structure if you provide one. So the underlying filesystem will be different than the spec. While some players will play iso9660 dvd as well as udf, some will display empty video_ts and audio_ts folders and won't play at all, some with buggy firmware will require you to reload the disc or reset the unit. YMMV.

You can always prepare an image of dvd-video udf:

mkisofs -dvd-video -udf -o dvd.iso folder_with_video_ts_subfolder/

---

### Post by zafkos on 2008-07-30
> **Jonie said:**
> DVD-Videos are in udf format, apps other than k3b or nero linux (commercial) will let you do data dvd (iso9660) with dvd-video compliant file structure if you provide one. So the underlying filesystem will be different than the spec. While some players will play iso9660 dvd as well as udf, some will display empty video_ts and audio_ts folders and won't play at all, some with buggy firmware will require you to reload the disc or reset the unit. YMMV.

You can always prepare an image of dvd-video udf:

mkisofs -dvd-video -udf -o dvd.iso folder_with_video_ts_subfolder/


I really wish I had found this post earlier; it's been almost four days that the ubuntu dummy (me!:lolflag:) I'm searching for a reply in why the iso images I've created with ISOMaster aren't displayed on my standalone DVD device - while they are very well played on ANY computer, either with Windows or with Ubuntu!...

Thank you so much! 

Just another question: 

My Hardy Heron LTS Lenovo 3000 N200 laptop doesn't seem to support udf (yesterday I tried to mount a photos CD I had written in Vista and it wouldn't! It said "unable to mount UDF device" - or so!). How can I make it support udf?

Thank you. :)

---

