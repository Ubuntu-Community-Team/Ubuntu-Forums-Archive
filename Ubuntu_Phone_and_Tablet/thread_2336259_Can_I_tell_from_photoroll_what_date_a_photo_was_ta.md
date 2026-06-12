---
title: "Can I tell from photoroll what date a photo was taken?"
date: 2016-09-06
forum: Ubuntu Phone and Tablet
---

### Post by naomibrown on 2016-09-06
I have some photos on photoroll but I'm not sure how to tell what date they were taken. Is there a way to find out? 

Thanks,
Naomi

---

### Post by coldraven on 2016-09-07
> **naomibrown said:**
> I have some photos on photoroll but I'm not sure how to tell what date they were taken. Is there a way to find out? 

Thanks,
Naomi
Is "photoroll" on a camera, phone or PC?

---

### Post by naomibrown on 2016-09-07
Sorry, I should have been more specific. It's on my Meizu MX4 phone running Ubuntu 15.04 (OTA-12). 

Thanks,
Naomi

---

### Post by howefield on 2016-09-08
Some time since I smashed the screen of my Ubuntu phone but if you have the terminal application installed you could try the *file* command..

```
file /path/to/image
```

will give output such as..

```
file ~/Pictures/image20150629_103401382.jpg
/home/hugh/Pictures/image20150629_103401382.jpg: JPEG image data, Exif standard: [TIFF image data, little-endian, direntries=15, description=, manufacturer=bq,
model=Aquaris E4.5, orientation=upper-left, xresolution=290, yresolution=298, resolutionunit=2, software=bq software, **datetime=2015:06:29 11:34:06**],
baseline, precision 8, 4352x2448, frames 3
```

Or copy the file to a desktop machine and right click > properties > image tab.

---

### Post by naomibrown on 2016-09-08
Fab, thanks!

---

