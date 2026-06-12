---
title: "8 Gigs, useable?"
date: 2008-10-21
forum: System76 Support
---

### Post by theorysavage on 2008-10-21
I am interested in a System 76 Wild Dog for Blender and audio/video editing. I have been wondering if 8 Gigs can be actually utilized by the system or is it overkill?

---

### Post by wizard10000 on 2008-10-21
> **theorysavage said:**
> I am interested in a System 76 Wild Dog for Blender and audio/video editing. I have been wondering if 8 Gigs can be actually utilized by the system or is it overkill?

With a 64-bit OS and the 64 bit version of Blender all 8g should be available, but...

[http://www.blendernation.com/2006/03/07/64-or-32-bits-that-is-the-question](http://www.blendernation.com/2006/03/07/64-or-32-bits-that-is-the-question)

> Recently a real usability issue for 64 bit version of Blender was pointed out on the Bf-committers list: actually a file created on such a version cannot be opened at all on 32 bit machines; this goes ways ahead from the old library-append incompatibility meaning that some real work is needed to have 64 bit versions ready for some real production works.

[I]"For now just be extremely cautious with the 64 bits version" - Ton commented - "there's actually no real reason to use a 64 bits build, unless you use projects that demand a lot of memory (>2 GB).
Blender also stores a lot of pointers in its data structures, which means that memory consumption for editing and rendering will increase in 64 bits with like 25-30%. So if your system has less than 2 GB of memory you'll be better off using 32 bits.
For tests it is interesting to check on speed benefits though!"[/I]

So, ladies and gentlemen, you're aware of the problem now, simply think about pros and cons before going the 64 bit way.

---

### Post by theorysavage on 2008-10-21
thanks, I didn't realize 64 bits had to do with RAM usage.

However, that post is from 2006 and as of blender 2.44 (2007) it seems there has been some improvement : 

[http://www.blender.org/development/release-logs/blender-244/64-bits-support/]("http://www.blender.org/development/release-logs/blender-244/64-bits-support/")

[INDENT]"Blender Files + Libraries

Blender's famous "struct DNA", which ensures backwards and even upwards compatibility for files, had to be tested and fixed for full (mixed!) 32 and 64 bits compliancy. Files saved in 32 bits should be readable in 64 bits, and vice versa. Also for appending data and for dynamic linked data (libraries) you should be able to use mixed 32 and 64 files.

Luckily the errors in previously saved 64 bits files were minimal, so those who already were using Blender 64 bits can still read data with this version. Note that it is possible these files will crash with 32 bits, so don't spread this!" [/INDENT]

So, perhaps it's not so much of a problem anymore... Either way, cool, and thanks.

---

