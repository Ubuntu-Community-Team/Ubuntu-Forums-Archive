---
title: "gpio driver not working all the time"
date: 2024-06-13
forum: Server Platforms
---

### Post by grejj on 2024-06-13
I am running Ubuntu 22.04.3 LTS server. Linux kernel version 5.15.0-94.

I have created a gpio shutdown driver that drops a gpio pin (kill0) low on shutdown to kill power the rest of my unit. It also monitors another gpio (int0) at 100ms that if goes low, will trigger poweroff.

In some rare cases the gpio pin (kill0) is not dropped at is should be in test_power_off() The only options are that the function pm_power_off/test_power_off is not being called or it is being called and for some other reason the gpio is not dropped. I have put my entire shutdown gpio kernel driver below. 

Have been scratching my head for days on this one. Works 95% of the time but I need it to work reliably all the time. Using the same kernel driver, there was no issue with Ubuntu 18.04 kernel version 4.15.

Here is the main snippet from my gpio driver
```

#include <linux/module.h>
#include <linux/reboot.h>
#include <linux/gpio.h>
#include <linux/i2c.h>
#include <linux/pm.h>
#include <linux/workqueue.h>
#include <linux/interrupt.h>
#include <linux/version.h>
#include <linux/delay.h>


#define POWTEST_VERSION_MACRO(x) #x
#define POWTEST_VERSION_BUILD(x) POWTEST_VERSION_MACRO(x)


#define POWTEST_VERSION_NUM   1.5.0
#define POWTEST_VERSION_STR   POWTEST_VERSION_BUILD(POWTEST_VERSION_NUM)


MODULE_DESCRIPTION("reset-request and power-off support");
MODULE_LICENSE("GPL"); MODULE_VERSION(POWTEST_VERSION_STR);
MODULE_SOFTDEP("pre: i2c-i801 gpio-pca953x");
MODULE_INFO(intree, "Y");


struct gpio_desc* gpiod_int0;       // input:  reset req (active low)
struct gpio_desc* gpiod_kill0;      // output: power off (active low)


static unsigned int0;      // input:  reset req (active low)
static unsigned kill0;     // output: power off (active low)


static struct delayed_work worker;


static void test_power_off(void)
{
    schedule(); /* give kernel a chance to poweroff */
    
    gpiod_set_value_cansleep(gpiod_kill0, 0);


    /* give it some time */
    mdelay( 3000 );
}


static void work(struct work_struct* work)
{
    int rc = -1;


    rc = gpiod_get_raw_value_cansleep(gpiod_int0);


    // power off if reset signal is low
    if(0 == rc) {
        pr_alert("reset request\n");
        orderly_poweroff(false);
    }
    else {
        schedule_delayed_work(&worker, msecs_to_jiffies(100));
    }
}


static struct i2c_board_info pcs9554_info = {
    .type = "pca9554",
    .addr = 0x21,
};


static int cb(struct device* dev, void* opaque)
{
    static const char prefix[] = "SMBus I801";
    struct i2c_adapter* adapter;
    struct i2c_client* client;


    adapter = to_i2c_adapter(dev);
    if(strncmp(adapter->name, prefix, sizeof prefix - 1)) {
        return 0;
    }


    client = i2c_new_client_device(adapter, &pcs9554_info);
    if(!client) {
        return 0;
    }
    return 1;
}


static int cmp(struct gpio_chip* chip, void* data)
{
    if(0 == strcmp(chip->label, data)) {
        return 1;
    }
    else if(('0' <= chip->label[0] && chip->label[0] <= '9') && (0 == strcmp(chip->label + 1, "-0021"))) { /* Workaround for kernel 5.X, when label is "X-0021" */
        return 1;
    }
    return 0;
}


static int __init powtest_init(void)
{
    struct gpio_chip* chip = NULL;


    // find i801 smbus and create device first
    i2c_for_each_dev(0, cb);


    // really "tca0408"
    chip = gpiochip_find("pca9554", cmp);
    if(!chip) {
        return -ENODEV;
    }


    kill0 = chip->base + 0;
    int0  = chip->base + 1;


    gpiod_kill0 = gpio_to_desc(kill0);
    gpiod_int0 = gpio_to_desc(int0);


    pr_info("gpio power %d reset %d\n", kill0, int0);


    // gpio interrupt support not enabled ... poll
    gpio_request(kill0, "kill0");
    gpio_request(int0, "int0");


    gpiod_direction_output_raw(gpiod_kill0, 1);
    gpiod_export(gpiod_kill0, false);


    gpiod_direction_input(gpiod_int0);
    gpiod_export(gpiod_int0, false);


    pm_power_off = test_power_off;


    // start first check now
    INIT_DELAYED_WORK(&worker, work);
    schedule_delayed_work(&worker, msecs_to_jiffies(100));


    return 0;
}


module_init(powtest_init);





```

---

### Post by ajgreeny on 2024-06-13
*Thread moved to **Server Platforms**.* which is more appropriate and a better fit.

---

