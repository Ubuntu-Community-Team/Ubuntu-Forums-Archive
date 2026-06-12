---
title: "Analogue video camera capture"
date: 2009-10-17
forum: Ubuntu Studio
---

### Post by christym on 2009-10-17
Can anyone recommend a software application for unbuntu that will perform quality capture for an anlogue video camera (Sony CCD-TRV23E).
thanks

---

### Post by bumanie on 2009-10-17
Have a look [here]("http://www.mythtv.org/wiki/Video_capture_card").

---

### Post by redxine on 2009-10-18
1. Put camera in VCR mode.
2. Open menu, navigate through the pages until you see an "A/V > DV" option and set it to on.
3. Connect component inputs and dv cable to computer.
4. Open a terminal and run: ```
sudo apt-get install dvgrab
sudo chmod 777 /dev/raw1394
dvgrab
```

---

