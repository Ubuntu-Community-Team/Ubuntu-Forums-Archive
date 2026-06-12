---
title: "Sakis3G"
date: 2010-09-23
forum: Sudan Team
---

### Post by zero-n on 2010-09-23
**What is sakis3G?**
[Sakis3G]("http://www.sakis3g.org/") is a tweaked shell script which is supposed to work out-of-the-box                                     for establishing a 3G connection with any combination of modem or operator.                                     It automatically setups your USB or Bluetooth&#8482; modem,                                     and may even detect operator settings. You should try it when anything else fails! 


You can download sakis3g with or without usb_modeswitch included. I already have usb_modeswitch so i will choose sakis3g package that  doesn't contain usb_modeswitch.


For information about usb_modeswitch installation check [this]("http://ubuntuforums.org/showthread.php?t=1578311") guide.



**sakis3g installation:**


1- Install dependences:
```

sudo apt-get install libusb-dev 


```2- Download sakis3g:
```

wget http://www.sakis3g.org/versions/latest/i386/sakis3g.gz

```3- Check data integrity:
```

echo "dda70fd95fb952dbb979af88790d3f6e  sakis3g.gz" | md5sum -c

```4- Extract data:
```

gunzip sakis3g.gz

```5- Give sakis3g execution permission
```

sudo chmod +x sakis3g

```6- Copy sakis3g to /usr/bin
```

sudo cp sakis3g /usr/bin/  

```Now you have sakis3g installed.



**Add sakis3g to desktop:**
from your terminal run:
```

sakis3g

```1- select[COLOR=Red] more options[/COLOR] & click ok
2- select [COLOR=Red]Create dekstop shortcut[/COLOR] & click ok

---

