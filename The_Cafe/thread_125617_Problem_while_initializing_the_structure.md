---
title: "Problem while initializing the structure"
date: 2006-02-04
forum: The Cafe
---

### Post by awais on 2006-02-04
I have a problem while initializing the structure. The program containing the structure is given below.
When I complie this program like this
      gcc -c UsbDrv.c
It then gives an error like this 
      the structure "generic_usb_id_table" is not complete


#define
#define USB_VENDOR_ID 0x22FF
#define USB_PRODUCT_ID_1 0x1111
#define USB_PRODUCT_ID_2 0x2222
static struct usb_device_id generic_usb_id_table [] =
{
  {
    USB_DEVICE(USB_VENDOR_ID,USB_PRODUCT_ID_1)
  },
  {
    USB_DEVICE(USB_VENDOR_ID,USB_PRODUCT_ID_2)
  }
  {
  }
};
MODULE_DEVICE_TABLE (usb, generic_usb_id_table);

---

