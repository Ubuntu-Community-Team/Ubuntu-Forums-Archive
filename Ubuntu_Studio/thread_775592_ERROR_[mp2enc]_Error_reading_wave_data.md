---
title: "ERROR: [mp2enc] Error reading wave data"
date: 2008-04-30
forum: Ubuntu Studio
---

### Post by ricemark20 on 2008-04-30
I get this error while trying to export video in kino.

```
Kino experienced a segmentation fault.
Dumping stack from the offending thread

Obtained 10 stack frames.
kino [0x8078861]
[0xffffe420]
/usr/lib/libdv.so.4(dv_decode_full_audio+0xa4) [0xb7f60644]
kino(_ZNK5Frame12ExtractAudioEPv+0x4f) [0x80aabcf]
kino(_ZN18AsyncAudioResampleIssE8callbackEPvPPf+0x72) [0x80cd5e2]
/usr/lib/libsamplerate.so.0(src_callback_read+0x12f) [0xb753be7f]
kino(_ZN6Export21calculateAdjustedRateEP8PlayListdiii+0x217) [0x80cc067]
kino(_ZN11ExportMJPEG8doExportEP8PlayListiiib+0xac6) [0x80d51a6]
kino(_ZN6Export11startExportEb+0x271) [0x80cd161]
kino(_ZN10PageExport11startExportEv+0x40) [0x80c93a0]

Done dumping - exiting.
**ERROR: [mp2enc] Error reading wave data

```

this happened when I tried to export to mpeg.
I am using Gutsy, and the kino version is 1.1.0

---

