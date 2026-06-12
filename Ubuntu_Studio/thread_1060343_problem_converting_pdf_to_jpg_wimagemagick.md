---
title: "problem converting pdf to jpg w/imagemagick"
date: 2009-02-04
forum: Ubuntu Studio
---

### Post by SteveNorman on 2009-02-04
I am trying to convert a pdf to jpg

I tried
```
convert chuckdfeb.pdf chuckdfeb.jpg

```

and I get

```
:~$ convert chuckdfeb.pdf chuckdfeb.jpg
Error: /rangecheck in definefont
Operand stack:
   --nostringval--   --dict:12/21(L)--   T1_0   1   FontObject   --dict:9/9(L)--   --dict:9/9(L)--   2255   --dict:9/9(L)--   --dict:5/13(L)--   --nostringval--   --nostringval--   WVVHCF+Antenna-Black   --nostringval--   WVVHCF+Antenna-Black   WVVHCF+Antenna-Black   --dict:11/40(L)--   Font
Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1905   1   3   %oparray_pop   1904   1   3   %oparray_pop   1888   1   3   %oparray_pop   --nostringval--   --nostringval--   2   1   1   --nostringval--   %for_pos_int_continue   --nostringval--   --nostringval--   false   1   %stopped_push   --nostringval--   --nostringval--   --nostringval--   %array_continue   --nostringval--   false   1   %stopped_push   --nostringval--   %loop_continue   --nostringval--   --nostringval--   --nostringval--   --nostringval--   --nostringval--   --nostringval--   1   1   0   --nostringval--   %for_pos_int_continue   1861   17   12   %oparray_pop
Dictionary stack:
   --dict:1156/1684(ro)(G)--   --dict:1/20(G)--   --dict:75/200(L)--   --dict:75/200(L)--   --dict:106/127(ro)(G)--   --dict:275/300(ro)(G)--   --dict:22/25(L)--   --dict:4/6(L)--   --dict:22/40(L)--   --dict:14/20(L)--   --dict:54/60(ro)(G)--   --dict:21/30(L)--
Current allocation mode is local
Last OS error: 2
GPL Ghostscript 8.63: Unrecoverable error, exit code 1
convert: Postscript delegate failed `chuckdfeb.pdf': No such file or directory.
convert: missing an image filename `chuckdfeb.jpg'.

```

no idea what to do

I did a successful read of the pdf, and eventually settled with the gimp solution (import save as .jpg) But I would like to configure imagemagick to work for me. Thanks in advance

---

