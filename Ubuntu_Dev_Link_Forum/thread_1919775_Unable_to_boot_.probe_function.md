---
title: "Unable to boot .probe function"
date: 2012-02-03
forum: Ubuntu Dev Link Forum
---

### Post by dennisdd on 2012-02-03
Can anyone help/advise me why I unable to boot my .probe file?(Thanks in advance)

here is my code. Compile no error. i am using devkit8000. linux2.6.32.9

During boot, I can only see this from the serial terminal:

################################
>>>>>test_module_init!<<<<<<<<<<

I don't see why system didn't call my test_gpio_probe function.
My android os able to boot just fine too. I assume there is no problem with the kernel.
The following is my code:

#include <linux/module.h>
#include <linux/init.h>
#include <linux/interrupt.h>
#include <linux/kthread.h>
#include <linux/irq.h>
#include <linux/gpio.h>
#include <linux/platform_device.h>
#include <linux/slab.h>

//added by dennis
#include <plat/mux.h> 
#include <linux/time.h> 
#include <linux/delay.h>


#define    GPIO_130    130
#define    HIGH        1
#define    LOW        0

struct test_gpio_platform_data {
    int (*init)(void);
    void (*exit)(void);
};

struct test_gpio_data {
    struct test_gpio_platform_data *pdata;
};

static int __devinit test_gpio_probe(struct platform_device *pdev)
{
    struct test_gpio_platform_data *pdata = pdev->dev.platform_data;
    struct test_gpio_data *gpio_data;
       int status;
    int ret = 0;
 
    printk(KERN_INFO "\n*****************************************\n");
    printk(KERN_INFO "test_PROBE!\n");
    printk(KERN_INFO "*****************************************\n\n");


    if (!pdata) 
    {
        ret = -EBUSY;
        goto err0;
    }

    gpio_data = kzalloc(sizeof(struct test_gpio_data), GFP_KERNEL);
    if (!gpio_data) 
    {
        ret = -ENOMEM;
        goto err0;
    }

    status = omap_cfg_reg(AE2_34XX_GPIO130_OUT);

    printk(KERN_INFO "omap_cfg_reg of status %d, %d\n",status,AE2_34XX_GPIO130_OUT  );

    if (gpio_request(GPIO_130, "AE2_34XX_GPIO130_OUT") == 0)
    {
        if(gpio_direction_output(GPIO_130, HIGH)==0)
        {
            printk(KERN_INFO "IO_EXPANDER: WORKs!\n");
            printk(KERN_INFO "Starts Bit Banging Test!\n");
            gpio_set_value(GPIO_130, HIGH);
            mdelay(1000);
            gpio_set_value(GPIO_130, LOW);
            mdelay(1000);
            gpio_set_value(GPIO_130, HIGH);
            mdelay(1000);
            gpio_set_value(GPIO_130, LOW);
            mdelay(1000);
            gpio_set_value(GPIO_130, HIGH);
            printk(KERN_INFO "End of Bit Banging Test!\n");

        }
        else
        {
            printk(KERN_INFO "IO_EXPANDER: Not WORKs!\n");
            gpio_free(GPIO_130);
            goto err0;
        }
    }
    else
    {
        printk(KERN_INFO "IO_EXPANDER: Not WORKs!\n");
        gpio_free(GPIO_130);
        goto err0;
    }
       return 0;

err0:
    return ret;
}

static int __devexit test_gpio_remove(struct platform_device *pdev)
{
    struct test_gpio_platform_data *pdata = pdev->dev.platform_data;
    gpio_free(GPIO_130);
    return 0;
}

MODULE_ALIAS("platform:test-gpio");
static struct platform_driver test_gpio_driver = {
    .driver.name    = "test-gpio",
    .driver.owner    = THIS_MODULE,
    .probe        = test_gpio_probe,
    .remove        = __devexit_p(test_gpio_remove),
};

static int __init test_module_init(void)
{
    printk(KERN_INFO "################################\n");
    printk(KERN_INFO ">>>>>test_module_init!<<<<<<<<<<\n");
    return platform_driver_register(&test_gpio_driver);
}
module_init(test_module_init);
static void __exit test_module_exit(void)
{
    platform_driver_unregister(&test_gpio_driver);
}
module_exit(test_module_exit);


MODULE_AUTHOR("Dennis");
MODULE_DESCRIPTION("Test GPIO interface");
MODULE_LICENSE("GPL");

---

