---
title: "Problem patching files"
date: 2011-02-08
forum: Server Platforms
---

### Post by Skerit on 2011-02-08
I generated a patchfile of 2 directories using this command:

```
diff -ur source-20110125 source > mailpatch3.patch
```

Now I would like to apply the patch, doing this:

```

patch -p1 < mailpatch3.patch
```

But it then asks me for the file to patch. Why?

Something that looks strange to me in the patch file: there are a lot of "common subdirectories" lines. Like this:

```
Common subdirectories: source-20110125/ac_depository and source/ac_depository
Common subdirectories: source-20110125/ac_depository_jar and source/ac_depository_jar
Common subdirectories: source-20110125/_backoffice and source/_backoffice
Common subdirectories: source-20110125/_csvexport and source/_csvexport
Common subdirectories: source-20110125/_foundation and source/_foundation
Common subdirectories: source-20110125/_impex and source/_impex
```

And I don't really know why they're there.

The rest of the patch looks normal:

```
diff -ur source-20110125/corelio_nieuwsblad_storefront/staticfiles/cartridge/templates/default/application/ApplicationFrame.isml source/corelio_nieuwsblad_storefront/staticfiles/cartridge/templates/default/application/ApplicationFrame.isml
--- source-20110125/corelio_nieuwsblad_storefront/staticfiles/cartridge/templates/default/application/ApplicationFrame.isml	Tue Jan 25 15:25:57 2011
+++ source/corelio_nieuwsblad_storefront/staticfiles/cartridge/templates/default/application/ApplicationFrame.isml	Wed Jan 26 09:16:44 2011
@@ -24,6 +24,47 @@
 
 <html>
 <head>
+
+	<isif condition="#isDefined(Product:Attribute("Image_1")) AND (Product:Attribute("Image_1") NE '')#">
+		<isset scope="request" name="image" value="#Product:Attribute("Image_1")#" />
+		<isif condition="#isDefined(image)#">
```

---

### Post by wormyblackburny on 2011-02-08
So it appears that both directories you did the diff on are in the same folder. I'm thinking that you need to use -p0 instead of -p1 switch....?

According to Man Pages:
**-p***num* or **--strip=***num* Strip the smallest prefix containing *num* leading slashes  from each file name found in the patch file. A sequence of one or more  adjacent slashes is counted as a single slash. This controls how file names found in the  patch file are treated, in case you keep your files in a different  directory than the person who sent out the patch. For example, supposing the file name in  the patch file was **/u/howard/src/blurfl/blurfl.c** setting **-p0** gives the entire file name unmodified, **-p1** gives **u/howard/src/blurfl/blurfl.c** without the leading slash, **-p4** gives **blurfl/blurfl.c** and not specifying **-p** at all just gives you **blurfl.c**. Whatever you end up with is looked for either in the current directory, or the directory specified by the **-d** option.

---

### Post by Skerit on 2011-02-09
I had the modified "source" directory and a copy of the unmodified original one called "source-20110125". I diffed those.

But then I tried to apply the patch from within the original "source-20110125" directory. And for that I would only have to strip 1, right?

---

