---
title: "f-spot metadata and resize problems"
date: 2010-01-10
forum: Ubuntu Studio
---

### Post by Torrilin on 2010-01-10
I'm learning to use a new digital camera, so I'm experimenting with f-spot. My camera embeds a lot of meta-data in the image files, like the ISO, shutter speed and aperture. If I look at f-spot's tags tho, none of these bits of data are listed as tags. The date isn't a tag either. It's very confusing. The f-spot manual doesn't really cover how to fix the metadata problem. Manually retagging every damn photo with tags that are already embedded in the file and that f-stop can read doesn't count as a fix.

I also can't figure out how to resize images using f-stop. I am not going to upload a 12 megapixel photo to a forum. That's a solid 3-4 megabytes, and it will dwarf most people's monitors... including mine. Again, it's not in the manual anywhere I can find.

(yes, I know there are other tools... but I'm trying to figure out if these are actual f-stop bugs, if there's just no documentation, or if I'm an idiot who can't read.)

---

### Post by poikiloid on 2010-02-26
tags are just one type of metadata, used primarily for describing what is IN the picture, not camera specs. and there are many metadata standards. camera specs are typically recorded in EXIF. user-added descriptions should be recorded in XMP format. IPTC is becoming outdated. there are good resources online to teach you. read this: [http://www.thirdlight.com/downloads/Metadata_whitepaper.pdf](http://www.thirdlight.com/downloads/Metadata_whitepaper.pdf)

i recommend DigiWF for editing metadata. works in nautilus. it is useful in combination with digikam, which can batch-fill (under tools menu) a whole "template", or set, of field data, such as stuff that doesn't change (you name, contact info, copyright statement, etc.). then you can use digiwf to go and add stuff that is different for each picture, or which applies to a subset of images. For example, if you visit a certain city, you can add that to all of them with digiwf, more easily than with digikam, in my opinion. and then use either digiwf or digikam to add captions, etc.

---

