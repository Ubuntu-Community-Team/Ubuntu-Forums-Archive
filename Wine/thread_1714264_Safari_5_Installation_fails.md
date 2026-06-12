---
title: "Safari 5 Installation fails"
date: 2011-03-25
forum: Wine
---

### Post by twistle on 2011-03-25
Hello,

I tried installing Safari 5 through Wine on Ubuntu 10.04 with these instructions: [http://www.jonathanmoeller.com/screed/?p=1792](http://www.jonathanmoeller.com/screed/?p=1792)
But when I try to open Safari for the first time I get this error message:
"Your copy of safari is missing important software resources. Please reinstall Safari."
(reinstalling doesn't help)

I'm very desperate, because I need CSS3 Transform 3D support before Monday. So I'd appreciate any help! Thank you~

---

### Post by An Sanct on 2011-03-25
Welcome!

Have you tried running safari from the terminal?

Press Alt+F2, enter "gnome-terminal" and run it, then run safari from there. I don't know the exact location of the file or the exe name, so I guess it should be "wine safari"

After that, you will get a listing of errors and warnings, these might help us determine the problem.

---

### Post by twistle on 2011-03-25
Thank you for your fast reply!

Running "wine safari" in the terminal returned: 
wine: cannot find L"C:\\windows\\system32\\safari.exe"

So I just copied the safari.exe into that folder and it returned these errors:
~$ wine safari

fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:msvcrt:_controlfp_s ((nil) 65536 196608) semi-stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:msvcr90:__clean_type_info_names_internal (0x10004340) stub

and the same error message popped up.

I also tried running the safari.exe from the original location which was
~$ wine C:\\"Program Files"\\Safari\\safari.exe

and it returned even more errors:
[http://www.filedropper.com/errors](http://www.filedropper.com/errors)

Does this help?

---

### Post by uRock on 2011-03-25
Moved to Wine

---

### Post by twistle on 2011-04-13
Well, thanks for all the helpful replies. Luckily I didn't completely get rid of Windows.

---

