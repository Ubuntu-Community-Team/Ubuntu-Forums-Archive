---
title: "Mencoder swscale"
date: 2009-03-23
forum: Ubuntu Studio
---

### Post by Nullack on 2009-03-23
Gday folks

Looking at this mencoder output:

```

VDec: vo config request - 1920 x 1080 (preferred colorspace: RGB 24-bit)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using RGB 24-bit as output csp (no 5)
Movie-Aspect is undefined - no prescaling applied.
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 9 -> 8
[swscaler @ 0xc7aec0]BICUBIC scaler, from rgb24 to yuv420p using MMX2
[swscaler @ 0xc7aec0]using 4-tap MMX scaler for horizontal luminance scaling
[swscaler @ 0xc7aec0]using 4-tap MMX scaler for horizontal chrominance scaling
[swscaler @ 0xc7aec0]using 1-tap MMX "scaler" for vertical scaling (YV12 like)
[swscaler @ 0xc7aec0]1920x1080 -> 1920x1080

```

I assume whats happening is that the png images are in rgb24 and I need to convert them to yv12?

Is there anyway to improve the quality of this process? Another filter? Some setting?

Thanks

---

