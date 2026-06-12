---
title: "Swftools, flash and searchable swf"
date: 2009-04-24
forum: Ubuntu Studio
---

### Post by developpef on 2009-04-24
Hi all,

I'm new in Ubuntu Forum and Windows user so excuse me in advance if I post an already answered question.

Here is the matter :
I'm developping a search engine for Flash. I already have it working with manually created swf, containing dynamic text fields and embedded fonts.
The problem is I now have to deal with generated swf files, from swftools (pdf2swf).
I already know that swftools generates texts in StaticText objects... And I would like it to generate DynamicText instead.

So I decided to get swftools source files, modify it and recompile to have a working pdf2swf as I want.
But not so easy!! I'm Flex/Java developer so I don't really understand C++. Besides, I really losed my hairs trying to correctly compile the sources under Windows!! :P
For now, I only have replaced all "StaticText" occurences in source by "DynamicText", but nothing happened (verified decompiling generated swf). 

So my question is : Did anybody try to modify swftools code to make this kind of customization? Any idea how I could get it generate DynamicText?

Thanks folks!

---

