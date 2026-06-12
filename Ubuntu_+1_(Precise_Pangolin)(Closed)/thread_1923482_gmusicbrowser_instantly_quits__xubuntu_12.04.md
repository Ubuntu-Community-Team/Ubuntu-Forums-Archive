---
title: "gmusicbrowser instantly quits / xubuntu 12.04"
date: 2012-02-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by fillmont on 2012-02-10
So I have a Xubuntu desktop running. Yesterday upgraded to 12.04 to see how it was coming along. Everything has been going swimmingly, except that gmusicbrowser has been updated, and now instantly shuts down. (I know it has been updated because for the brief half second before the program quits, I can see that the layout is different.)

Any ideas on how to run a diagnostic?

---

### Post by fillmont on 2012-02-10
Here is what I get when I run gmusicbrowser in a terminal:

```
print() on closed filehandle $fifofh at /usr/bin/gmusicbrowser line 290.
GStreamer::Interfaces perl module not found -> visuals not available
Reading saved tags in /home/henry/.config/gmusicbrowser/gmbrc ...
Reading saved tags in /home/henry/.config/gmusicbrowser/gmbrc ... done
process 6873: Array or variant type requires that type boolean be written, but double was written.
The overall signature expected here was 'a{sb}' and we are on byte 4 of that signature.
process 6873: Writing an element of type array, but the expected type here is boolean
The overall signature expected here was 'a{sb}' and we are on byte 4 of that signature.
process 6873: Writing an element of type dict_entry, but the expected type here is end_dict_entry
The overall signature expected here was 'a{sb}' and we are on byte 5 of that signature.
process 6873: Array or variant type requires that type end_dict_entry be written, but begin_dict_entry was written.
The overall signature expected here was 'a{sb}' and we are on byte 5 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value string was written.
The overall signature expected here was 'a{sb}' and we are on byte 6 of that signature.
process 6873: Writing an element of type variant, but no value is expected here
The overall signature expected here was 'a{sb}' and we are on byte 7 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value variant was written.
The overall signature expected here was 'a{sb}' and we are on byte 7 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value end_dict_entry was written.
The overall signature expected here was 'a{sb}' and we are on byte 8 of that signature.
process 6873: Writing an element of type dict_entry, but the expected type here is end_dict_entry
The overall signature expected here was 'a{sb}' and we are on byte 5 of that signature.
process 6873: Array or variant type requires that type end_dict_entry be written, but begin_dict_entry was written.
The overall signature expected here was 'a{sb}' and we are on byte 5 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value string was written.
The overall signature expected here was 'a{sb}' and we are on byte 6 of that signature.
process 6873: Writing an element of type variant, but no value is expected here
The overall signature expected here was 'a{sb}' and we are on byte 7 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value variant was written.
The overall signature expected here was 'a{sb}' and we are on byte 7 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value end_dict_entry was written.
The overall signature expected here was 'a{sb}' and we are on byte 8 of that signature.
process 6873: Writing an element of type dict_entry, but the expected type here is end_dict_entry
The overall signature expected here was 'a{sb}' and we are on byte 5 of that signature.
process 6873: Array or variant type requires that type end_dict_entry be written, but begin_dict_entry was written.
The overall signature expected here was 'a{sb}' and we are on byte 5 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value string was written.
The overall signature expected here was 'a{sb}' and we are on byte 6 of that signature.
process 6873: Writing an element of type variant, but no value is expected here
The overall signature expected here was 'a{sb}' and we are on byte 7 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value variant was written.
The overall signature expected here was 'a{sb}' and we are on byte 7 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value end_dict_entry was written.
The overall signature expected here was 'a{sb}' and we are on byte 8 of that signature.
process 6873: Writing an element of type dict_entry, but the expected type here is end_dict_entry
The overall signature expected here was 'a{sb}' and we are on byte 5 of that signature.
process 6873: Array or variant type requires that type end_dict_entry be written, but begin_dict_entry was written.
The overall signature expected here was 'a{sb}' and we are on byte 5 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value string was written.
The overall signature expected here was 'a{sb}' and we are on byte 6 of that signature.
process 6873: Writing an element of type variant, but no value is expected here
The overall signature expected here was 'a{sb}' and we are on byte 7 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value variant was written.
The overall signature expected here was 'a{sb}' and we are on byte 7 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value end_dict_entry was written.
The overall signature expected here was 'a{sb}' and we are on byte 8 of that signature.
process 6873: Writing an element of type dict_entry, but the expected type here is end_dict_entry
The overall signature expected here was 'a{sb}' and we are on byte 5 of that signature.
process 6873: Array or variant type requires that type end_dict_entry be written, but begin_dict_entry was written.
The overall signature expected here was 'a{sb}' and we are on byte 5 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value string was written.
The overall signature expected here was 'a{sb}' and we are on byte 6 of that signature.
process 6873: Writing an element of type variant, but no value is expected here
The overall signature expected here was 'a{sb}' and we are on byte 7 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value variant was written.
The overall signature expected here was 'a{sb}' and we are on byte 7 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value end_dict_entry was written.
The overall signature expected here was 'a{sb}' and we are on byte 8 of that signature.
process 6873: Writing an element of type dict_entry, but the expected type here is end_dict_entry
The overall signature expected here was 'a{sb}' and we are on byte 5 of that signature.
process 6873: Array or variant type requires that type end_dict_entry be written, but begin_dict_entry was written.
The overall signature expected here was 'a{sb}' and we are on byte 5 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value string was written.
The overall signature expected here was 'a{sb}' and we are on byte 6 of that signature.
process 6873: Writing an element of type variant, but no value is expected here
The overall signature expected here was 'a{sb}' and we are on byte 7 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value variant was written.
The overall signature expected here was 'a{sb}' and we are on byte 7 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value end_dict_entry was written.
The overall signature expected here was 'a{sb}' and we are on byte 8 of that signature.
process 6873: Writing an element of type dict_entry, but the expected type here is end_dict_entry
The overall signature expected here was 'a{sb}' and we are on byte 5 of that signature.
process 6873: Array or variant type requires that type end_dict_entry be written, but begin_dict_entry was written.
The overall signature expected here was 'a{sb}' and we are on byte 5 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value string was written.
The overall signature expected here was 'a{sb}' and we are on byte 6 of that signature.
process 6873: Writing an element of type variant, but no value is expected here
The overall signature expected here was 'a{sb}' and we are on byte 7 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value variant was written.
The overall signature expected here was 'a{sb}' and we are on byte 7 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value end_dict_entry was written.
The overall signature expected here was 'a{sb}' and we are on byte 8 of that signature.
process 6873: Writing an element of type dict_entry, but the expected type here is end_dict_entry
The overall signature expected here was 'a{sb}' and we are on byte 5 of that signature.
process 6873: Array or variant type requires that type end_dict_entry be written, but begin_dict_entry was written.
The overall signature expected here was 'a{sb}' and we are on byte 5 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value string was written.
The overall signature expected here was 'a{sb}' and we are on byte 6 of that signature.
process 6873: Writing an element of type variant, but no value is expected here
The overall signature expected here was 'a{sb}' and we are on byte 7 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value variant was written.
The overall signature expected here was 'a{sb}' and we are on byte 7 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value end_dict_entry was written.
The overall signature expected here was 'a{sb}' and we are on byte 8 of that signature.
process 6873: Writing an element of type dict_entry, but the expected type here is end_dict_entry
The overall signature expected here was 'a{sb}' and we are on byte 5 of that signature.
process 6873: Array or variant type requires that type end_dict_entry be written, but begin_dict_entry was written.
The overall signature expected here was 'a{sb}' and we are on byte 5 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value string was written.
The overall signature expected here was 'a{sb}' and we are on byte 6 of that signature.
process 6873: Writing an element of type variant, but no value is expected here
The overall signature expected here was 'a{sb}' and we are on byte 7 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value variant was written.
The overall signature expected here was 'a{sb}' and we are on byte 7 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value end_dict_entry was written.
The overall signature expected here was 'a{sb}' and we are on byte 8 of that signature.
process 6873: Writing an element of type dict_entry, but the expected type here is end_dict_entry
The overall signature expected here was 'a{sb}' and we are on byte 5 of that signature.
process 6873: Array or variant type requires that type end_dict_entry be written, but begin_dict_entry was written.
The overall signature expected here was 'a{sb}' and we are on byte 5 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value string was written.
The overall signature expected here was 'a{sb}' and we are on byte 6 of that signature.
process 6873: Writing an element of type variant, but no value is expected here
The overall signature expected here was 'a{sb}' and we are on byte 7 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value variant was written.
The overall signature expected here was 'a{sb}' and we are on byte 7 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value end_dict_entry was written.
The overall signature expected here was 'a{sb}' and we are on byte 8 of that signature.
process 6873: Writing an element of type dict_entry, but the expected type here is end_dict_entry
The overall signature expected here was 'a{sb}' and we are on byte 5 of that signature.
process 6873: Array or variant type requires that type end_dict_entry be written, but begin_dict_entry was written.
The overall signature expected here was 'a{sb}' and we are on byte 5 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value string was written.
The overall signature expected here was 'a{sb}' and we are on byte 6 of that signature.
process 6873: Writing an element of type variant, but no value is expected here
The overall signature expected here was 'a{sb}' and we are on byte 7 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value variant was written.
The overall signature expected here was 'a{sb}' and we are on byte 7 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value end_dict_entry was written.
The overall signature expected here was 'a{sb}' and we are on byte 8 of that signature.
process 6873: Writing an element of type dict_entry, but the expected type here is end_dict_entry
The overall signature expected here was 'a{sb}' and we are on byte 5 of that signature.
process 6873: Array or variant type requires that type end_dict_entry be written, but begin_dict_entry was written.
The overall signature expected here was 'a{sb}' and we are on byte 5 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value string was written.
The overall signature expected here was 'a{sb}' and we are on byte 6 of that signature.
process 6873: Writing an element of type variant, but no value is expected here
The overall signature expected here was 'a{sb}' and we are on byte 7 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value variant was written.
The overall signature expected here was 'a{sb}' and we are on byte 7 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value end_dict_entry was written.
The overall signature expected here was 'a{sb}' and we are on byte 8 of that signature.
process 6873: Array or variant type wasn't expecting any more values to be written into it, but a value end_dict_entry was written.
The overall signature expected here was 'a{sb}' and we are on byte 9 of that signature.
process 6873: Array or variant type requires that type boolean be written, but string was written.
The overall signature expected here was 'a{sb}' and we are on byte 4 of that signature.
process 6873: Array or variant type requires that type boolean be written, but string was written.
The overall signature expected here was 'a{sb}' and we are on byte 4 of that signature.
```

---

### Post by Toz on 2012-02-10
See: [http://ubuntuforums.org/showthread.php?t=1878702]("http://ubuntuforums.org/showthread.php?t=1878702")

---

### Post by fillmont on 2012-02-10
> **Toz said:**
> See: [http://ubuntuforums.org/showthread.php?t=1878702](http://ubuntuforums.org/showthread.php?t=1878702)

Thanks! Worked well.

---

