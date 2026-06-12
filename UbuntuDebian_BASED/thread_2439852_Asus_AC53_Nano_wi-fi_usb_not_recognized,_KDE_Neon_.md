---
title: "Asus AC53 Nano wi-fi usb not recognized, KDE Neon 5.18 LTS"
date: 2020-04-02
forum: Ubuntu/Debian BASED
---

### Post by pedrotallon on 2020-04-02
> **chili555 said:**
> Please try this:```
cd ~
git clone https://github.com/FomalhautWeisszwerg/rtl8822bu.git
cd rtl8822bu
nano os_dep/linux/usb_intf.c
```Change this section at about line 222, from this:```
#ifdef CONFIG_RTL8822B
    /*=== Realtek demoboard ===*/
    {USB_DEVICE(0x0B05, 0x1812), .driver_info = RTL8812}, /* ASUS - Edimax */
    {USB_DEVICE(0x7392, 0xB822), .driver_info = RTL8822B}, /* Edimax - EW-7822ULC */
    {USB_DEVICE(0x7392, 0xC822), .driver_info = RTL8822B}, /* Edimax - EW-7822UTC */
    {USB_DEVICE(0x13B1, 0x0043), .driver_info = RTL8822B}, /* Linksys - WUSB6400M */
    {USB_DEVICE(0x0BDA, 0xB812), .driver_info = RTL8822B},
    {USB_DEVICE_AND_INTERFACE_INFO(USB_VENDER_ID_REALTEK, 0xB82C, 0xff, 0xff, 0xff), .driver_info = RTL8822B}, /* Default ID */
#endif /* CONFIG_RTL8822B */
```To this:```
#ifdef CONFIG_RTL8822B
        /*=== Realtek demoboard ===*/
        {USB_DEVICE(0x0B05, 0x1812), .driver_info = RTL8812}, /* ASUS - Edimax */
        {USB_DEVICE(0x7392, 0xB822), .driver_info = RTL8822B}, /* Edimax - EW-7822ULC */
        {USB_DEVICE(0x7392, 0xC822), .driver_info = RTL8822B}, /* Edimax - EW-7822UTC */
        {USB_DEVICE(0x13B1, 0x0043), .driver_info = RTL8822B}, /* Linksys - WUSB6400M */
       [COLOR=#FF0000]{USB_DEVICE(0x0B05, 0x184C), .driver_info = RTL8822B}, /* ASUS USB AC53 */[/COLOR]
        {USB_DEVICE(0x0BDA, 0xB812), .driver_info = RTL8822B},
        {USB_DEVICE_AND_INTERFACE_INFO(USB_VENDER_ID_REALTEK, 0xB82C, 0xff, 0xff, 0xff), .driver_info = RTL8822B}, /* Default ID */
#endif /* CONFIG_RTL8822B */
```I have highlighted the line you will add.

Spacing, indentation, etc. are crucial and must be perfect. Proofread carefully twice. Save (Ctrl+o followed by Enter) and exit (Ctrl+x) the text editor. 

Now back to the terminal:```
make
sudo make install
sudo modprobe 8822bu
```Any improvement?


Hi, I'm dealing with the same issue (but KDE Neon) and I'm trying to fix it. Following your steps I could handle to get to the last step: sud modprobe 8822bu. But at first time it was suddenly killed. I thought it was OK so I reboot my computer but didn't work. I am running sud modprobe 8822b again but I'm still waiting for some prompt or some return... 

Any advice? Or info about what is happening or how to fix it?

I have a Asus AC53 Nano and KDE Neon (5.18 LTS). 


thank you in advance

---

### Post by howefield on 2020-04-02
Moved to the "*Ubuntu/Debian BASED*" forum.

---

