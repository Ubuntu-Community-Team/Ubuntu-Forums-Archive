---
title: "# nvidia-smi -a | grep GPU Unable to determine the device handle for GPU 0000:04:00.0"
date: 2014-09-10
forum: Server Platforms
---

### Post by danhansendenmark on 2014-09-10
Hi,


OS: Ubuntu Server 64bit 14.04.1 + todays update
Kernel: 3.13.0-32-generic
CUDA 6.5
Boinc 7.2.42
CPU: Intel
GPU's: Nvidia GT640

I'm running a headless ubuntu server with Boinc. Using 4 GPU's and 1 CPU to do the work. Suddenly, after today/yesterday's update this happened:
```

# nvidia-smi -a | grep GPU
Unable to determine the device handle for GPU 0000:04:00.0: Unknown Error
```

Anybody who knows what this means? Anyone who has the same problem?

A little information:
I've been using Ubuntu Server 12.10 / CUDA5.5 until now because of the CUDA5.5 problem, which accoured after the 12.04.4 update. Because 12.10 no longer was serviced, I looked for another version. After trying 7 or 8 different combinations I learned that this new 14.04 worked with the new CUDA 6.5. But, now there's this problem. I also have the problem, that the system suddenly restarts. I doesent run for more than a day or two. It has nothingo do with GPU/CPU temperatures, because I've made a watchdog that protcts the system. And the temperature of the GPU's is max. 57 degrees Celsius and 72 for the CPU. Cooling is pretty good ;)


**STATUS 7:24pm**
Actually I thought the cards were running, becuse a monitor says so! BoincTasks, but they don't!!! Not all the time. The temperature of all 4 cards are below 42 degrees Celsius, which means they are doing absolutely nothing! Then it runs for a little time again. So it's not stable. Anybody who has an idea? Because I'm lost! This was the only combination of Ubuntu & CUDA that works, so I could really need some help ;)

```

# nvidia-smi -a | grep GPU
Attached GPUs                       : 4
GPU 0000:01:00.0
    GPU UUID                        : GPU-ea22ef3d-4254-dff0-2db8-86656441c
    MultiGPU Board                  : N/A
    GPU Operation Mode
        GPU Link Info
        GPU Current Temp            : 39 C   <--------------- DOING NOTHING!!!
        GPU Shutdown Temp           : N/A
        GPU Slowdown Temp           : N/A
GPU 0000:02:00.0
    GPU UUID                        : GPU-bf213a08-c3c6-346b-53ff-5ff7d82c5
    MultiGPU Board                  : N/A
    GPU Operation Mode
        GPU Link Info
        GPU Current Temp            : 40 C   <--------------- DOING NOTHING!!!
        GPU Shutdown Temp           : N/A
        GPU Slowdown Temp           : N/A
GPU 0000:03:00.0
    GPU UUID                        : GPU-d5813be2-bf30-6c90-a591-90fef7659
    MultiGPU Board                  : N/A
    GPU Operation Mode
        GPU Link Info
        GPU Current Temp            : 42 C   <--------------- DOING NOTHING!!!
        GPU Shutdown Temp           : N/A
        GPU Slowdown Temp           : N/A
GPU 0000:04:00.0
    GPU UUID                        : GPU-a9bb2423-c2ba-16cd-529f-cdcc43faf
    MultiGPU Board                  : N/A
    GPU Operation Mode
        GPU Link Info
        GPU Current Temp            : 41 C   <--------------- DOING NOTHING!!!
        GPU Shutdown Temp           : N/A
        GPU Slowdown Temp           : N/A



# nvidia-smi -a | grep GPU
Attached GPUs                       : 4
GPU 0000:01:00.0
    GPU UUID                        : GPU-ea22ef3d-4254-dff0-2db8-86656441c
    MultiGPU Board                  : N/A
    GPU Operation Mode
        GPU Link Info
        GPU Current Temp            : 46 C   <--------------- RUNNING AT 100%
        GPU Shutdown Temp           : N/A
        GPU Slowdown Temp           : N/A
GPU 0000:02:00.0
    GPU UUID                        : GPU-bf213a08-c3c6-346b-53ff-5ff7d82c5
    MultiGPU Board                  : N/A
    GPU Operation Mode
        GPU Link Info
        GPU Current Temp            : 46 C   <--------------- RUNNING AT 100%
        GPU Shutdown Temp           : N/A
        GPU Slowdown Temp           : N/A
GPU 0000:03:00.0
    GPU UUID                        : GPU-d5813be2-bf30-6c90-a591-90fef7659
    MultiGPU Board                  : N/A
    GPU Operation Mode
        GPU Link Info
        GPU Current Temp            : 51 C   <--------------- RUNNING AT 100%
        GPU Shutdown Temp           : N/A
        GPU Slowdown Temp           : N/A
GPU 0000:04:00.0
    GPU UUID                        : GPU-a9bb2423-c2ba-16cd-529f-cdcc43faf
    MultiGPU Board                  : N/A
    GPU Operation Mode
        GPU Link Info
        GPU Current Temp            : 48 C   <--------------- RUNNING AT 100%
        GPU Shutdown Temp           : N/A
        GPU Slowdown Temp           : N/A

```



Kind Regards,
Dan/Denmark

---

### Post by Locane on 2015-03-04
I was googling around and found this post.

I was typing "nvidia-smi" under CentOS 6.5 and getting the same error - a driver update from 343.22 to 346.47 solved my problem.

Hopefully this is useful to someone in the future.

---

