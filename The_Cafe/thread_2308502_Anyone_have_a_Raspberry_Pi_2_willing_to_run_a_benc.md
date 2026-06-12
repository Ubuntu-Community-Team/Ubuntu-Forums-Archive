---
title: "Anyone have a Raspberry Pi 2 willing to run a benchmark?"
date: 2016-01-03
forum: The Cafe
---

### Post by pqwoerituytrueiwoq on 2016-01-03
I am considering upgrading my model B r2 so I'd like to see if the better CPU has any impact on wired network performance
the only online benchmark i found did not test dual link usage so that is why i am asking here
i would like to see the output of [FONT=courier new]iperf -c $IPERF_SERVER_IP -d[/FONT] (the [FONT=Courier New]-d[/FONT] is important)
to start the server process run [FONT=Courier New]iperf -s[/FONT] you can get the ip address from [FONT=Courier New]ifconfig[/FONT]
Please to not test over wifi, Linux box <-> Router/Switch <-> Rpi_b2
it does not matter which is server and client, if it is no better than my old model B pi i can look for a old B+ board which needs less milliamps

---

### Post by benrob0329 on 2016-01-04
I'd test it, but I'm afraid it'll have to wait until my desktop is built.

---

### Post by CharlesA on 2016-01-04
No idea what you were actually looking for but here you go:

Pi -> Host:
```
root@pi:~# iperf -c 192.168.1.200 -d
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
------------------------------------------------------------
Client connecting to 192.168.1.200, TCP port 5001
TCP window size: 70.0 KByte (default)
------------------------------------------------------------
[  5] local 192.168.1.3 port 56325 connected with 192.168.1.200 port 5001
[  4] local 192.168.1.3 port 5001 connected with 192.168.1.200 port 51918
[ ID] Interval       Transfer     Bandwidth
[  5]  0.0-10.0 sec  56.0 MBytes  46.7 Mbits/sec
[  4]  0.0-10.1 sec   105 MBytes  87.6 Mbits/sec

```

Host -> Pi:

```
iperf -c 192.168.1.3 -d
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
------------------------------------------------------------
Client connecting to 192.168.1.3, TCP port 5001
TCP window size: 98.6 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.200 port 51922 connected with 192.168.1.3 port 5001
[  5] local 192.168.1.200 port 5001 connected with 192.168.1.3 port 56330
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec   111 MBytes  92.7 Mbits/sec
[  5]  0.0-10.1 sec  51.9 MBytes  43.0 Mbits/sec

```

---

### Post by pqwoerituytrueiwoq on 2016-01-04
I was wondering if the cpu was bottlenecking the net I/O
thanks [**[COLOR=#C61919][B]CharlesA**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=923868")

i have my pi acting as a reverse proxy, looks marginally better than i get on my pi, well before i updated the linux 4.1
[https://github.com/raspberrypi/linux/issues/1248](https://github.com/raspberrypi/linux/issues/1248)
happen to know how to revert it?

you running the 3.18 or 4.1 kernel?

---

### Post by CharlesA on 2016-01-04
> **pqwoerituytrueiwoq said:**
> i have my pi acting as a reverse proxy, looks marginally better than i get on my pi, well before i updated the linux 4.1
[https://github.com/raspberrypi/linux/issues/1248](https://github.com/raspberrypi/linux/issues/1248)
happen to know how to revert it?

Not sure exactly. Do you still have the older kernel installed?

> you running the 3.18 or 4.1 kernel?

```
Linux pi 4.1.7-v7+ #817 SMP PREEMPT Sat Sep 19 15:32:00 BST 2015 armv7l GNU/Linux
```

I've been using this: [https://minibianpi.wordpress.com/](https://minibianpi.wordpress.com/)

If it matters, that box is being used for DNS.

---

### Post by pqwoerituytrueiwoq on 2016-01-04
running 4.1.13+
it was installed via apt-get upgrade, i was not expecting a kernel update out of it, im sure the unattended-upgrades package would not install it since i was still running 3.12 for the past 180 days
```
pi@raspberrypi:~$ tree /boot
/boot
&#9500;&#9472;&#9472; bcm2708-rpi-b.dtb
&#9500;&#9472;&#9472; bcm2708-rpi-b-plus.dtb
&#9500;&#9472;&#9472; bcm2708-rpi-cm.dtb
&#9500;&#9472;&#9472; bcm2709-rpi-2-b.dtb
&#9500;&#9472;&#9472; bootcode.bin
&#9500;&#9472;&#9472; cmdline.txt
&#9500;&#9472;&#9472; config.txt
&#9500;&#9472;&#9472; COPYING.linux
&#9500;&#9472;&#9472; fixup_cd.dat
&#9500;&#9472;&#9472; fixup.dat
&#9500;&#9472;&#9472; fixup_db.dat
&#9500;&#9472;&#9472; fixup_x.dat
&#9500;&#9472;&#9472; issue.txt
&#9500;&#9472;&#9472; kernel7.img
&#9500;&#9472;&#9472; kernel.img
&#9500;&#9472;&#9472; LICENCE.broadcom
&#9500;&#9472;&#9472; LICENSE.oracle
&#9500;&#9472;&#9472; overlays
&#9474;   &#9500;&#9472;&#9472; ads7846-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; at86rf233-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; bmp085_i2c-sensor-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; dht11-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; enc28j60-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; gpio-poweroff-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; hifiberry-amp-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; hifiberry-dac-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; hifiberry-dacplus-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; hifiberry-digi-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; hy28a-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; hy28b-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; i2c-gpio-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; i2c-rtc-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; i2s-mmap-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; iqaudio-dac-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; iqaudio-dacplus-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; lirc-rpi-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; mcp2515-can0-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; mcp2515-can1-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; mmc-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; mz61581-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; piscreen2r-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; piscreen-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; pitft28-capacitive-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; pitft28-resistive-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; pps-gpio-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; pwm-2chan-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; pwm-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; raspidac3-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; README
&#9474;   &#9500;&#9472;&#9472; rpi-backlight-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; rpi-dac-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; rpi-display-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; rpi-ft5406-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; rpi-proto-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; rpi-sense-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; sdhost-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; sdio-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; smi-dev-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; smi-nand-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; smi-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; spi-bcm2708-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; spi-bcm2835-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; spi-dma-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; tinylcd35-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; uart1-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; vga666-overlay.dtb
&#9474;   &#9500;&#9472;&#9472; w1-gpio-overlay.dtb
&#9474;   &#9492;&#9472;&#9472; w1-gpio-pullup-overlay.dtb
&#9500;&#9472;&#9472; start_cd.elf
&#9500;&#9472;&#9472; start_db.elf
&#9500;&#9472;&#9472; start.elf
&#9492;&#9472;&#9472; start_x.elf

1 directory, 71 files
```
i'm still on wheezy, ill upgrade to the [b+ i ordered on ebay](http://www.ebay.com/itm/131687047427) (link in case anyone wants a cheap b+)
i have a larger sd card and i want to upgrade some stuff in my diy case, probally a full days worth of work, ill put off the psu upgrade plans till i get a new one, hoping to gut 2 wallorts sand get them in the case

---

### Post by CharlesA on 2016-01-05
Huh. I wonder how you are running a newer kernel than I am.

In any case, it looks like it's a bit complicated to downgrade the kernel. :(
[http://raspberrypi.stackexchange.com/questions/34339/install-older-kernel-3-6-11-on-raspberry-pi-2](http://raspberrypi.stackexchange.com/questions/34339/install-older-kernel-3-6-11-on-raspberry-pi-2)

---

### Post by pqwoerituytrueiwoq on 2016-01-05
a very very long time ago i used raspi-update get get a kernel that was not officially stable, cause it fixed a stability issue with the network interface
that reboot was the 1st i ever gave it, all others were a result of power failure, aside from when i changed out the power block

---

### Post by pqwoerituytrueiwoq on 2016-01-05
so how does minibian compare to raspbian jessie lite? only ask cause raspbian jessie lite has a newer release date

---

### Post by CharlesA on 2016-01-05
> **pqwoerituytrueiwoq said:**
> so how does minibian compare to raspbian jessie lite? only ask cause raspbian jessie lite has a newer release date

No idea, I wasn't even aware they had an official minimal build of Jessie. I'll have to check it out. I do not believe it was there when I was looking for a minimal install of Jessie for my Pi.

---

### Post by pqwoerituytrueiwoq on 2016-01-05
> **CharlesA said:**
> I do not believe it was there when I was looking for a minimal install of Jessie for my Pi. and there in lies what i was wondering

---

### Post by CharlesA on 2016-01-05
This might help:
[https://blog.adafruit.com/2015/12/01/new-official-raspbian-jessie-lite-os-image/](https://blog.adafruit.com/2015/12/01/new-official-raspbian-jessie-lite-os-image/)

[https://minibianpi.wordpress.com/features/](https://minibianpi.wordpress.com/features/)

---

