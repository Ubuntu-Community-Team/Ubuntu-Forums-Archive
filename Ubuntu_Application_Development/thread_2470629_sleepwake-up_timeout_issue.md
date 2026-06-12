---
title: "sleep/wake-up timeout issue"
date: 2022-01-06
forum: Ubuntu Application Development
---

### Post by fjdklajiels on 2022-01-06
I have a unexpected issue that related in sleep/wake-up timeout for task, while device driver develop.
my code use kernel function 'wait_for_completion_interruptible_timeout' when there is a reason for task sleep, this function parameter need input 'want timeout in jiffies', so i have try that input any value like "msecs_to_jiffies(255 * 1000)" for sleep task 255seconds.
I expected this function 'wait_for_completion_interruptible_timeout' return zero when after almost exactly 255seconds. but I measured the actual time, it was additionally delayed maximum almost 11 seconds(final time 266 seconds) in my test case.
so result of have additional test, the additionally delayed time is different, but the result is the same.
additionally delayed time range was random in 1ms ~ 11seconds.
this issue occur in kernel function 'msleep(255 * 1000)' too... because schedule_timeout() used in 'wait_for_completion_interruptible_timeout' and msleep.

**&#8251;A additionally delayed time occurs even if a different number is entered like 1ms or 1seconds..**

I think it "additionally delayed time" was mean that wake-up task but time to task racing until active run in cpu. am i guessing right? or not am i doing something wrong?
If my thoughts are right, How do I get the correct time?

Below is the sample code I tested.

```

struct completion cmp;
static long g_jiffies = 0;

static int _open(struct inode *inode, struct file *file)
{    
    init_completion(&cmp);
    g_jiffies = 0;
    return 0;
}

static ssize_t _read(struct file *filp, char __user *buffer, size_t count, loff_t *ppos)
{
    long sch = 0;
    reinit_completion(&cmp);

    printk(KERN_NOTICE "start checking\n");
    g_jiffies = jiffies; 
    sch = wait_for_completion_interruptible_timeout(&cmp,  msecs_to_jiffies(255 * 1000));
    //msleep(255 * 1000)

    printk(KERN_NOTICE "delay time = %ld\n", jiffies_to_msecs(jiffies - g_jiffies));
    return 0;
}

```

```

result dmesg : 
[&#47785;  1&#50900;  6 13:05:30 2022] start checking
[&#47785;  1&#50900;  6 13:09:52 2022] delay time = 261808

```

---

