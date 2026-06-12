---
title: "Wireless internet not working when dualbooting Windows 7 from Ubuntu"
date: 2014-08-15
forum: Windows
---

### Post by Rob_Williams on 2014-08-15
Hey guys,

I recently decided to dualboot windows 7 on top of my ubuntu system in order to use Itunes, but have run into some problems.

When I installed windows, no network connection could be found because I am missing drivers. I am a real noob at computers so after playing around a bit, it told me that my USB network adapter needed updating:

It is the RTL8191S WLAN Adapter. When I googled for the driver back on ubuntu and downloaded the .exe to a memory stick, and ran it on windows, it would not work as it required internet access, when that is what I'm trying to get! What do i need to do to get internet to work on my windows 7 dual boot?

Thanks in advance

Rob

---

### Post by kc1di on 2014-08-15
Hi Rob_Williams and Welcome to Ubuntu Forums,

Let me make sure I understand this correctly you have internet access via ubuntu but trying to get it working in Windows 7?
When you got your usb dongle did it come with any windows software, Drivers?  usually a CD disc. 

There could be several reason it will not connect including a physical on off switch on the machine itself.
is there any way you can connect the machine via ethernet cable?   if so try that and see if you can find the right drivers for your chipset.
then install them in windows.

---

### Post by varunendra on 2014-08-15
Welcome to the forums Rob!

Where did you download the driver from? It should always be from an authentic website, like your computer's vendor or the card's vendor.

From your description, it seems you need RTL8192SU driver for Windows which is provided by Realtek here : [http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

Anything that is supposed to install a driver, but requires you to connect to internet while/before installing, is a suspicious stuff. I wonder if you actually downloaded some malware/spamware instead of a real driver.

If you are not sure about the adapter's chip/model, please open a terminal in Ubuntu (Ctrl-Alt-T) and post the output of -
```
lsusb
```
..while the adapter is plugged in.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by QIII on 2014-08-15
... and since this is a Windows issue, moved to ***Other Operating Systems and Projects***.

But we'll still help!  ;)

---

### Post by Rob_Williams on 2014-08-15
> **QIII said:**
> ... and since this is a Windows issue, moved to ***Other Operating Systems and Projects***.

But we'll still help!  ;)

> **varunendra said:**
> Welcome to the forums Rob!

Where did you download the driver from? It should always be from an authentic website, like your computer's vendor or the card's vendor.

From your description, it seems you need RTL8192SU driver for Windows which is provided by Realtek here : [http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

Anything that is supposed to install a driver, but requires you to connect to internet while/before installing, is a suspicious stuff. I wonder if you actually downloaded some malware/spamware instead of a real driver.

If you are not sure about the adapter's chip/model, please open a terminal in Ubuntu (Ctrl-Alt-T) and post the output of -
```
lsusb
```
..while the adapter is plugged in.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.


```
 Bus 002 Device 005: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter


```

Thats the one^

---

### Post by varunendra on 2014-08-15
Then the link I gave you is correct for the driver you need. Please download from there and try installing on Windows. Let us know the result.

---

