---
title: "GPU acceleration in the web browser"
date: 2010-06-26
forum: The Cafe
---

### Post by toupeiro on 2010-06-26
There's a lot of information out about the D2D gpu acceleration extensions available in browsers running on the Windows platform.  IE9 has it, Firefox 3.7+ has it, and in some tests, firefox actually outperforms IE9 in D2D accelerated web performance.  However, D2D is a proprietary framework, therefore this functionality is not portable to Linux. (I guess, MAYBE through wine.)  Does anyone know of any developments to enable the same functionality using OpenGL extensions on Linux with Linux friendly browsers?

---

### Post by WRDN on 2010-06-26
ATI now allow for better acceleration of flash content using their GPUs, I am unsure of NVIDIA. Regarding GPGPU (General Purpose Graphics Processing Unit), both OpenCL and CUDA exist at:

[http://www.khronos.org/opencl/](http://www.khronos.org/opencl/)
[http://www.nvidia.com/object/cuda_home_new.html](http://www.nvidia.com/object/cuda_home_new.html)

CUDA is more mature than OpenCL (by ~2 years), but is limited to NVIDIA hardware, so I believe, OpenCL (Open Computing Language) stands more of a chance as it can run on any platform (ATI cards from 4xxx series and above, unsure for NVIDIA though they do support OpenCL in their drivers).

VLC is using CUDA acceleration, reducing the load on the CPU significantly, they have yet to get OpenCL working with their code base.

I can see GPU acceleration being used in web browsers, it is only a matter of time.

---

### Post by toupeiro on 2010-06-26
It's already being done in Windows.  I'm familiar with CUDA and OpenCL as supportable technologies...  To repeat my question, does anyone know of any of these technologies being actively tested within a linux based web browser?

---

