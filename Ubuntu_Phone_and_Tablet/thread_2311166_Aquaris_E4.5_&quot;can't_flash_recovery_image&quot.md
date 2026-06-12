---
title: "Aquaris E4.5: &quot;can't flash recovery image&quot;"
date: 2016-01-25
forum: Ubuntu Phone and Tablet
---

### Post by ZICODIAN on 2016-01-25
A recent update screwed up Ubuntu Touch on my Aquaris E4.5 locking it into a boot loop. As I have done a few times previously, I set about reflashing the device with the current stable version of its operating system. I set the device into fastboot mode and ran the reflash command. When I do this, I am presented with the following message:

```

2016/01/25 11:40:38 Expecting the device to be in the bootloader... waiting
2016/01/25 11:40:41 Device is |krillin|
2016/01/25 11:40:41 Flashing version 28 from ubuntu-touch/stable/bq-aquaris.en channel and server https://system-image.ubuntu.com to device krillin
can't flash recovery image

```

Previously, this approach has worked fine, resulting in pushing of the necessary image files to the device. With this message, I don't know what to do. Does anyone have any ideas on how to proceed?

---

### Post by ZICODIAN on 2016-01-25
Ok, I was running at a directory that didn't contain the file recovery-krillin.img. With the file present, the reflash works.

---

