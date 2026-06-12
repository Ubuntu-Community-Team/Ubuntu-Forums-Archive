---
title: "Wifi in Virtualbox"
date: 2013-07-15
forum: Virtualisation
---

### Post by Shishimaru on 2013-07-15
Hello people!
I'm using Ubuntu 13.04 and I installed the latest version of Virtualbox with virtualbox extension and guest additions. Then I created a virtual machine and installed my old copy of Windows XP. Now I wonder if I can use the Windows' drivers for my wifi and connect with Windows. I had issues with wifi that I didn't solve (I opened another thread for that, and I thank you again for your support) and now I'd like to try with Windows. I don't want to mess my partition table, so I decided to try Virtualbox. I hope you can help once again. Wish you a nice day/a good night.

---

### Post by snowpine on 2013-07-15
You need to resolve the networking issues in your Linux "host." The Windows "guest" cannot see your actual physical wireless card; it only sees a generic wired network. :)

---

### Post by Shishimaru on 2013-07-15
Seems that I better install Windows in a physical primary partition then :(
I was hoping Windows doesn't have issues with wifi, so I could reboot in WinXP to reboot router for wifi.

---

### Post by newbie-user on 2013-07-16
The Windows virtual machine will use the host's network connection by default (NAT connection) and it will be seamless to the Windows virtual machine. You won't have to worry about wifi drivers for Windows.

---

### Post by varunendra on 2013-07-17
> **snowpine said:**
> You need to resolve the networking issues in your Linux "host." The Windows "guest" cannot see your actual physical wireless card; it only sees a generic wired network. :)

+1

However, even some internal cards are attached to a USB bus, thus appearing as a USB adapter. In that case, you maybe able to add it as a USB device in virtualbox and use it from within the guest OS.

If your wireless card appears in 'lsusb', it is on a usb bus, there is a chance. If it appears in 'lspci', there is no chance, not yet at least.

Of course you can always use an external USB wireless adapter inside the vm by attaching it to the guest.

---

### Post by Shishimaru on 2013-07-17
It's not in lsusb unfortunately :(
I really need to try Windows and its drivers, so I do have to worry about it as I mentioned in the first post. Seems that I have to install it and find a primary partition for it.

---

### Post by newbie-user on 2013-07-17
You don't need wifi drivers for Windows. There are two main ways to give your virtual machine an Internet connection in Virtualbox: NAT or bridged. With NAT, your virtual machine works as if it is behind a virtual router. Internet connections are done through network address translation. With bridged networking, windows has a virtual connection that connects directly to your physical network via the physical network card on your computer. I know for sure that Windows XP networking works with the PCnet-FAST III virtual network adapter that Virtualbox provides.

Again, you don't need to load wifi drivers into your XP virtual machine. It wouldn't do anything anyway because you don't have that specific piece of hardware directly available to the virtual machine.

---

### Post by varunendra on 2013-07-18
> **newbie-user said:**
> You don't need wifi drivers for Windows. There are two main ways to give your virtual machine an Internet connection in Virtualbox:....
Nice explanation newbie-user. Unfortunately, it doesn't apply to OP. They don't have a working wireless in Ubuntu and that is the very reason why they're trying to make it work with windows or its driver -

> **Shishimaru said:**
> ..I had issues with wifi that I didn't solve (I opened another thread for that, and I thank you again for your support) and now I'd like to try with Windows...

---

