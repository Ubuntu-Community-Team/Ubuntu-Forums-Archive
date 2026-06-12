---
title: "Webcam on new Star5 not recognized by gstreamer"
date: 2011-06-05
forum: System76 Support
---

### Post by BaddestCross on 2011-06-05
The title pretty much says it all ... Webcam works with gTalk plug-in but gstreamer can't talk to it.  I'm not sure where to go from here.

From gstreamer properties video test: 

```
"Video for Linux 2 (v4l2): Failed getting controls attributes on device '/dev/video0'."
```

Any ideas?

---

### Post by isantop on 2011-06-06
Does the camera work in Cheese? I can't remember if that uses gstreamer, but I believe it does.

---

### Post by BaddestCross on 2011-06-06
> **isantop said:**
> Does the camera work in Cheese? I can't remember if that uses gstreamer, but I believe it does.

That's what brought this all to light ... Cheese, which is based on gstreamer, does not recognize the camera.

---

### Post by shadow_derf on 2011-06-07
Having the same issue here with my new Starling5 netbook. Cheese does not recognize the camera.

Video for Linux 2 (v4l2): Failed getting controls attributes on device '/dev/video0' 

within the GUI and

gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Failed getting controls attributes on device '/dev/video0'. [v4l2_calls.c(267): gst_v4l2_fill_lists (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src1:
Failed querying control 9963788 on device '/dev/video0'. (5 - Input/output error)]
 
Within the CLI.

---

### Post by isantop on 2011-06-08
What are your settings in the gstreamer-properties window set to?

---

### Post by BaddestCross on 2011-06-08
> **isantop said:**
> What are your settings in the gstreamer-properties window set to?

The default settings ... v4l2/v4l2src

---

### Post by isantop on 2011-06-09
Can you see the image from the webcam if you hit the test button under Input?

---

### Post by BaddestCross on 2011-06-09
> **isantop said:**
> Can you see the image from the webcam if you hit the test button under Input?


Uhm ... no. 

Refer to my original post to see the error message displayed when the "test" button is pressed.

---

### Post by isantop on 2011-06-10
Can you try booting into a LiveUSB of Ubuntu and seeing if it works from there? If not, then we probably have a hardware issue on our hands, and we'll need you to contact us at support...at...system76...do...com.

---

### Post by BaddestCross on 2011-06-10
> **isantop said:**
> Can you try booting into a LiveUSB of Ubuntu and seeing if it works from there? If not, then we probably have a hardware issue on our hands, and we'll need you to contact us at support...at...system76...do...com.


I don't have ready access to a USB key large enough to create one right now.  As I said earlier, the cam DOES work with flash and gTalk-plugin, just not gstreamer.  Is there another setting that we can check?

---

