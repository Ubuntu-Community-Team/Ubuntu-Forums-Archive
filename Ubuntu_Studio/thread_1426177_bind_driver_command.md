---
title: "bind_driver command"
date: 2010-03-09
forum: Ubuntu Studio
---

### Post by Sikandar on 2010-03-09
there is a command called **bind_driver** which gives the list of all USB devices attached to that PC.
it is working in same linux(ubuntu) version (2.6.30)of one PC but not other.
the error was coming command not found.
so i located the file by locate bind_driver.
got the location then by going to that path wrote the **./bind_driver**, but still it's just giving the description of command and not actual working of it.


[LIST=1]
[*]usbip@usbip-desktop:~/usbip-0.1.7 /src/cmd/.libs$ sudo  ./bind_driver
[*][sudo] password for usbip:
[*]Usage:  bind-driver [OPTION]
[*]Change driver binding for USB/IP.
[*]   --usbip busid        make a device exportable
[*]  --other busid        use a device by a local driver
[*]   --list               print usb devices and their drivers
[*]   --allusbip           make all devices exportable
[/LIST]


[LIST=1]
[*]usbip@usbip-desktop:~/usbip-0.1.7  /src/cmd/.libs$ sudo ./bind_driver --list
[*]List USB devices
[/LIST]

[LIST=1]
[*]usbip@usbip-desktop:~/usbip-0.1.7  /src/cmd/.libs$ sudo bind_driver --list
[*]sudo: bind_driver:  command not found
[/LIST]

---

### Post by catterpillar on 2010-03-13
I am not an expert but following thing worked for me. :) 
Actually if you have installed usbip through command line then bind_driver will work. But if you have installed it through command "sudo apt-get install usbip" you have to do

server:# usbipd -D
      - Start usbip daemon.

server:# usbip_bind_driver --list
      - List driver assignments for usb devices.

server:# usbip_bind_driver --usbip 1-2
      - Bind usbip.ko to the device of busid 1-2.
      - A usb device 1-2 is now exportable to other hosts!
      - Use ’usbip_bind_driver --other 1-2’ when you want to shutdown
       exporting and use the device locally.
see this link for more info : [http://http://manpages.ubuntu.com/manpages/lucid/man8/usbipd.8.html]("http://http//manpages.ubuntu.com/manpages/lucid/man8/usbipd.8.html")

---

