---
title: "Need help debuging I2C on Libre AML-S905X SBC with Ubuntu image."
date: 2022-08-22
forum: Ubuntu Application Development
---

### Post by MR.UNOWEN on 2022-08-22
I'm working on a project where I display the IP address on a 2x16 LCD communicating via I2C. Unfortunately most guides are written for RaspberryPi running with their OS, so there's been some steps skipped as I don't know their equivalent with Ubuntu. For one I don't know what things are disabled and need enabling from the ubuntu side. When running i2cdetect I only see 0x30 and 0x50 when I'm expecting ox27. As for pin connections, they're pins 3(SDA) and 5(SCK) of the GPIO. As for the board, it's the AML-S905X. Let me know what I need to do to get this working.

---

