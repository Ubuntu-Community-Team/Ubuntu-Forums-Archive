---
title: "How to install Real time linux in Ubuntu ?"
date: 2014-02-23
forum: Ubuntu, Linux and OS Chat
---

### Post by aashik2 on 2014-02-23
I need to install Real time linux in linux os. I am using Ubuntu 12.04, and my kernel is v3.2 with gcc 4.6. Ibhave heard that Real time linux Packages have only come for kernel 2.4 . Is there any way of installing real time linux in 3.2 kernel?
Thank You

---

### Post by tgalati4 on 2014-02-23
I believe a custom real-time kernel did stop with 2.4.  Changes in the newer 2.6 and 3.X kernels allow different scheduling policies that achieve low-level latency--with near-real-time performance.  To get a truly real-time kernel in 3.2, you probably have to make a custom kernel--which means compiling it from scratch.

This info is for 12.04, which has kernel 3.2 (among others) as its base kernel:  [https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu#Real_Time_Kernel_.26_Xruns](https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu#Real_Time_Kernel_.26_Xruns)

And:  [https://help.ubuntu.com/community/UbuntuStudioPreparation#Audio](https://help.ubuntu.com/community/UbuntuStudioPreparation#Audio)

Perhaps describe why you need a real-time kernel.

---

### Post by Bucky Ball on 2014-02-24
For 12.04 LTS you need to compile the real-time (rt) kernel manually. May I ask why you want to install the rt kernel?

If you are asking about RTLinux rather than just the rt kernel, then you may find some joy [HERE]("https://rt.wiki.kernel.org/index.php/Main_Page").

---

### Post by aashik2 on 2014-02-24
Is there any version of ubuntu which used v2.4 as its base kernel?

---

### Post by Bucky Ball on 2014-02-24
> **tgalati4 said:**
> 
Perhaps describe why you need a real-time kernel.

Could you please respond to other posters question's and posts?

There is nothing remotely viable or supported in Ubuntu that uses the 2.4 kernel. You would be going back to 10.04 LTS or 10.10 from memory, long dead, and you'd be lucky to get much help with either of those if you can still find a download. I would also avoid going online with any of these releases as they have no updates, haven't had for a year or more, and that includes security updates.

---

### Post by aashik2 on 2014-02-24
i just need it for working with real time applications and interrupts.

---

### Post by aashik2 on 2014-02-24
further I am relatively new in linux. hence building a customized kernel is very new to me.

---

### Post by aashik2 on 2014-02-24
Thanks for your replies.
according to this [https://rt.wiki.kernel.org/index.php/RT_PREEMPT_HOWTO](https://rt.wiki.kernel.org/index.php/RT_PREEMPT_HOWTO) , we just need to patch a source kernel with its rt patch. can you please confirm if thats enough? 
Thank you

---

### Post by lykwydchykyn on 2014-02-24
> **aashik2 said:**
> Thanks for your replies.
according to this [https://rt.wiki.kernel.org/index.php/RT_PREEMPT_HOWTO](https://rt.wiki.kernel.org/index.php/RT_PREEMPT_HOWTO) , we just need to patch a source kernel with its rt patch. can you please confirm if thats enough? 
Thank you

I think that's all you need; I think there's a PPA out there for a prepatched realtime kernel, see this:

[http://www.ubuntubuzz.com/2012/03/real-time-linux-installation-on-ubuntu.html](http://www.ubuntubuzz.com/2012/03/real-time-linux-installation-on-ubuntu.html)

Don't know if it works or not.

---

### Post by tgalati4 on 2014-02-24
That is what I am talking about.  So either try your application with a low-latency (software-based) kernel and see how that performs, or go through the anguish (and learning curve) of compiling 2.6.X kernel with the rt patch.  If this is for a single-core, embedded application, then use the 2.4 or 2.6 kernel that best supports your hardware.  Security is not much of an issue with 2.4.X because you won't get networking to work correctly running in true real time mode.

---

### Post by Bucky Ball on 2014-02-24
> **tgalati4 said:**
> Security is not much of an issue with 2.4.X because you won't get networking to work correctly running in true real time mode.

You might be able to get it to work, but it should be switched off for full rt performance in any case.

---

### Post by aashik2 on 2014-02-24
Thank you all for your help. Its now time for me to try them out

---

### Post by aashik2 on 2014-02-24
> **tgalati4 said:**
> That is what I am talking about.  So either try your application with a low-latency (software-based) kernel and see how that performs, or go through the anguish (and learning curve) of compiling 2.6.X kernel with the rt patch.  If this is for a single-core, embedded application, then use the 2.4 or 2.6 kernel that best supports your hardware.  Security is not much of an issue with 2.4.X because you won't get networking to work correctly running in true real time mode.

But we need gcc 3.x for compiling 2.4 or 2.6 kernel ,right ? is it possible to compile them using gcc 4.6 ?

---

### Post by aashik2 on 2014-02-25
as per the instructions in [https://rt.wiki.kernel.org/index.php/RT_PREEMPT_HOWTO](https://rt.wiki.kernel.org/index.php/RT_PREEMPT_HOWTO) , I have patched my kernel v 3.2.0 with an rt patch-3.2-rc1-52e4c2a05-rt1.patch and have then compiled the kernel successfully. Now when i try running an example program given in the above howto wiki whose codes are as given below
> #include <string.h>
#include <stdio.h>
#include <sys/utsname.h>

int main(int argc, char **argv)
{
    struct utsname u;
    int crit1, crit2 = 0;
    FILE *fd;

    uname(&u);
    crit1 = strcasestr (u.version, "PREEMPT RT");

    if ((fd = fopen("/sys/kernel/realtime","r")) != NULL) {
        int flag;
        crit2 = ((fscanf(fd, "%d", &flag) == 1) && (flag == 1));
        fclose(fd);
    }
    fprintf(stderr, "this is a %s kernel\n",
            (crit1 && crit2)  ? "PREEMPT RT" : "vanilla");
}
But I get the output as vanilla, even though I have booted through the rtl kernel. Also there is no file named realtime inside folder kernel.
Could anyone please help me with what might be the problem?

---

