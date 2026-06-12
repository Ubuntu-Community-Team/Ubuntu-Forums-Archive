---
title: "Using OpenCL in kernel"
date: 2011-03-04
forum: Ubuntu Dev Link Forum
---

### Post by lukxx on 2011-03-04
Hello,


I would like to work in the kernel with the GPU. Is it possible to use OpenCL in the kernel? Can I put and use the OpenCL libraries in the kernel?

 Thanks
lukxx

---

### Post by WRDN on 2011-03-08
From what I can tell, it sounds like you're confusing the OpenCL term "kernel", with the Linux "kernel".

The Linux kernel is the thing that manages your system, including hardware, processes and scheduling etc.

An OpenCL "kernel" is simply a function that is called on the device. It is not related to the Linux "kernel".

I am currently creating a GPU ray tracer using OpenCL, so have become rather accustomed to it. To provide a basic example, an example OpenCL kernel is:

```

__kernel void square(__global float *input, __global float *output)
{
   int gid = get_global_id(0);
   output[gid] = input[gid] * input[gid];
}

```

This could be made to execute on an OpenCL device N times, where N is the input range. For example, if the input array contains 1000 items, you could launch 1000 work items/threads on the OpenCL device, with each work item processing one element from the input array. This is as opposed to a linear function, where you would typically use a loop from 0 (typically) to N.

---

