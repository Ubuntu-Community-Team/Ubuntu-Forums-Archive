---
title: "[SOLVED] automatic poweroff and poweron"
date: 2008-03-28
forum: Server Platforms
---

### Post by DonThomaso on 2008-03-28
Hey,
I got problem with an automatic poweroff and poweron script. The goal is to poweroff the server at at specified time and power the system back on at another specified time.
To poweroff the server, I wrote a simple script with a "shutdown -P" which will be started via cron.
To poweron the server, I set a feature in the BIOS to power on the server at a specified time.
But the poweron via BIOS doesn't worked. I thought, that this is maybe a problem by the BIOS and I tested another way: Poweron after powerlost. I bought a clocktimer which will cut the line after the server shuts down. I tested this by shutting down the server with the powerbutton, turn off the power with the clocktimer and turn back on the power with the clocktimer: IT WORKED!
This morning, the clocktimer turned on, but the server doesn't. After pressing the power button, the server started.

This is a strange thing: If I powerdown the server with the command "shutdown -P", I can't power back on the server with the BIOS.
If I powerdown the server the power button, I can power back on the server with the BIOS.

Does someone know why and how I can resolve this problem?

Thx

---

### Post by cdenley on 2008-03-28
Are you sure your CMOS battery isn't dead? If it is, you could be losing your bios settings every time you cut the power. Some motherboards will only turn on after a power-loss if the computer was running when it lost power. In other words, if the motherboard was told to do an acpi shutdown, and turned itself off, it would stay off after a power-loss since it wasn't running to begin with.

---

### Post by DonThomaso on 2008-03-28
I'm sure, that the battery is ok, because the CMOS don't loss its data after the powercord was disconnected. I think it must be something with the powerstate. Maybe there a difference between power button and shutdown. Shutdown should be ACPI state S5, what state is the power button?

---

### Post by cdenley on 2008-03-28
If your motherboard sends the ACPI power button event to the OS, then /etc/acpi/powerbtn.sh should be getting run every time you press the button.

---

### Post by DonThomaso on 2008-03-28
Sorry, forgot to explain it right: I pressed the button before the system boots right after the BIOS-screen, disconnected the powercord and plug it back in: system starts. The BIOS is also set to "always" start system after getting power back.

---

### Post by cdenley on 2008-03-28
I think how the motherboard handles the power button before it hands over control to the OS would depend on the motherboard. If the bios options says "always" power back on, it apparently isn't working correctly, so I would check for bios updates, then contact the motherboard manufacturer.

---

### Post by DonThomaso on 2008-04-06
Well, I solved it :)
The clocktimer has 4 options, not only 2:
- ON
- OFF
- AUTO ON
- AUTO OFF
I turned the clocktimer from ON to AUTO ON and now the clocktimer is working. There was no problem with the server only the clocktimer was set wrong.:oops:
Many thanks for the help!

---

