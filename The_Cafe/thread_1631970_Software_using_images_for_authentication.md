---
title: "Software using images for authentication ?"
date: 2010-11-27
forum: The Cafe
---

### Post by Shpongle on 2010-11-27
Hey all, Im doing research for my thesis in the area of image based authentication and designing a mobile application around it. Part of the research involves looking at existing technologies / implementations relating to the topic. While my research so far has found many different methods used for implementation , I have found it difficult to find software utilizing image based authentication. so far I have only found one [https://addons.mozilla.org/en-US/firefox/addon/12651/](https://addons.mozilla.org/en-US/firefox/addon/12651/)

just wondering if you's know of or have used any image based authentication software ?.

Thanks

---

### Post by Oxwivi on 2010-11-27
If I understood you right, isn't CAPTCHA one of those image authentication systems you're looking for?

---

### Post by Shpongle on 2010-11-27
Yes it is but im trying to see if there is any applications which use the image itself rather than user input based on the image. Thanks for the suggestion all the same . I suppose I can add it to the list .

---

### Post by matthewbpt on 2010-11-27
Does this count? [http://www.omgubuntu.co.uk/2010/09/login-to-ubuntu-using-your-face/](http://www.omgubuntu.co.uk/2010/09/login-to-ubuntu-using-your-face/)

It uses your webcam to log you into the desktop, so it is basically comparing your face to an image.

---

### Post by Oxwivi on 2010-11-27
> **matthewbpt said:**
> Does this count? [http://www.omgubuntu.co.uk/2010/09/login-to-ubuntu-using-your-face/](http://www.omgubuntu.co.uk/2010/09/login-to-ubuntu-using-your-face/)

It uses your webcam to log you into the desktop, so it is basically comparing your face to an image.
This one's interesting, and I'm sure a similar system for mobile will be popular.

---

### Post by Shpongle on 2010-11-27
Well its video but Il see If I can use it , My application is relative to images only for now.  Im looking for stuff along the lines of either user authentication or anti-phishing involving images. It can be anything , windows , linux , android or web based . Just so I can mess with it and assess it and get some screenshots showing its implementation. Thanks for your responses and time.:D

---

### Post by Sporkman on 2010-11-27
I made a captcha-esque check myself - check out this sporkapp:

[http://sporkforge.com/sporkapps/app.php?n=10113adc0e570013f1](http://sporkforge.com/sporkapps/app.php?n=10113adc0e570013f1)

& click on the "email" link to discover the author's email.

---

### Post by Shpongle on 2010-11-27
> **Sporkman said:**
> I made a captcha-esque check myself - check out this sporkapp:

[http://sporkforge.com/sporkapps/app.php?n=10113adc0e570013f1](http://sporkforge.com/sporkapps/app.php?n=10113adc0e570013f1)

& click on the "email" link to discover the author's email.

thats pretty cool , do you mind if I reference it ? .

---

### Post by Sporkman on 2010-11-27
> **Shpongle said:**
> thats pretty cool , do you mind if I reference it ? .

Sure, no problem. I can send you the source code too if you're interested.

---

### Post by Shpongle on 2010-11-27
> **Sporkman said:**
> Sure, no problem. I can send you the source code too if you're interested.
Thanks I appreciate it , theres no need for the source code as I have to assess the pro's and con's in regards to usability and security. For example I tried lots of refreshes to check how dynamic the images were to see if they could be gathered in a set to be used to try guess the images. In regards to usability off the top of my head , the images are blue on white  so it should be easily distinguishable for people with colorblindness.

---

### Post by Sporkman on 2010-11-27
> **Shpongle said:**
> Thanks I appreciate it , theres no need for the source code as I have to assess the pro's and con's in regards to usability and security. For example I tried lots of refreshes to check how dynamic the images were to see if they could be gathered in a set to be used to try guess the images. As its blue on white it should also be distinguishable for people with colorblindness.

Note the changing sizes of the squares & circles as well, otherwise a bot could just take the ratio of blue to white pixels to guess the answers.

---

### Post by Shpongle on 2010-11-27
> **Sporkman said:**
> Note the changing sizes of the squares & circles as well, otherwise a bot could just take the ratio of blue to white pixels to guess the answers.

I didn't notice that the first time round , but good job.

---

### Post by Old_Grey_Wolf on 2010-11-27
> **Shpongle said:**
> Hey all, Im doing research for my thesis in the area of image based authentication and designing a mobile application around it. Part of the research involves looking at existing technologies / implementations relating to the topic. While my research so far has found many different methods used for implementation , I have found it difficult to find software utilizing image based authentication. so far I have only found one [https://addons.mozilla.org/en-US/firefox/addon/12651/](https://addons.mozilla.org/en-US/firefox/addon/12651/)

just wondering if you's know of or have used any image based authentication software ?.

Thanks

I assume that 3D barcode authentication falls within the scope of your thesis. Google search on 3D barcode security. An example 3D barcode is attached.

Edit: why it is called 3D is beyond me, it looks like 2D to me. LOL

If this is a thesis for a PHD, then I hope you do not find a lot of existing implementations; otherwise, what is the point of the thesis.

---

