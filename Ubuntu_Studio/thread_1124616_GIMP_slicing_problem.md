---
title: "GIMP slicing problem"
date: 2009-04-13
forum: Ubuntu Studio
---

### Post by 4th guy on 2009-04-13
While trying to export a sliced image via Filters > Web > Slice in GIMP, I get the following error message. Python is installed, and I can't think of anything else that might pose a problem.
> An error occured running python-fu-slice
error: could not crop image (ID 3) to 0x152, offset 200, 0
Traceback (most recent call last):
  File "/usr/lib/gimp/2.0/python/gimpfu.py", line 685, in response
    dialog.res = run_script(params)
  File "/usr/lib/gimp/2.0/python/gimpfu.py", line 352, in run_script
    return apply(function, params)
  File "/usr/lib/gimp/2.0/plug-ins/py-slice.py", line 117, in pyslice
    left, right, top, bottom, i, j, ""))
  File "/usr/lib/gimp/2.0/plug-ins/py-slice.py", line 172, in slice
    temp_image.crop(right - left, bottom - top, left, top)
error: could not crop image (ID 3) to 0x152, offset 200, 0

> GIMP Message
Calling error for procedure 'gimp-image-crop':
Procedure 'gimp-image-crop' has been called with value '0' for argument 'new-width' (#2, type GimpInt32). This value is out of range.

---

### Post by 0cton on 2009-04-14
does this seem to be the problem with no matter what image?

---

### Post by 4th guy on 2009-04-15
I hadn't thought of that. I have just tested it and it doesn't affect other images.

---

### Post by Windsurfer619 on 2009-04-16
It sounds like gimp is trying to tell you that one of your slices has a width of 0, and it can't do that.

---

### Post by nastasache on 2013-05-04
This is happening when guidelines are doubled.

---

