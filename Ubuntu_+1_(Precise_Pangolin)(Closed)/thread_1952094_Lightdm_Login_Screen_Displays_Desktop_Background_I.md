---
title: "Lightdm Login Screen Displays Desktop Background Image"
date: 2012-04-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Trapper on 2012-04-03
U12.04 Unity

I added a custom image as my desktop image. The first time I logged out the lightdm login screen had the desktop image displayed as the background image. Making matters worse it displays it in zoom mode. The image is set for centered mode on the desktop. Now every time I start up I get my greatly enlarged desktop background image as my login screen background image. What's happening here?

---

### Post by phaed on 2012-04-04
This has been an expected change. Are you saying you don't want your desktop background as the LightDM background, or you don't like how it's being stretched out?  If it's the former, here's a work around:

[http://askubuntu.com/questions/101115/is-there-a-way-to-shut-off-showing-the-users-wallpaper-in-lightdm](http://askubuntu.com/questions/101115/is-there-a-way-to-shut-off-showing-the-users-wallpaper-in-lightdm)

---

### Post by Nick Payne on 2012-04-04
If you set access permissions for your desktop background file to None for Others, that will stop it being used on the login screen.

---

### Post by ratcheer on 2012-04-04
Hmmm. My system is doing the opposite. A week or so ago, it did show my wallpaper on the login screen (after a few seconds of the lightdm screen, purple with white dots), but now it shows the lightdm for a few seconds, then the Ubuntu default wallpaper. After I login and Unity comes up, it displays my wallpaper.

Tim

---

### Post by Trapper on 2012-04-04
> **phaed said:**
> This has been an expected change. Are you saying you don't want your desktop background as the LightDM background, or you don't like how it's being stretched out?  If it's the former, here's a work around:

[http://askubuntu.com/questions/101115/is-there-a-way-to-shut-off-showing-the-users-wallpaper-in-lightdm](http://askubuntu.com/questions/101115/is-there-a-way-to-shut-off-showing-the-users-wallpaper-in-lightdm)

Well, actually I cannot honestly answer you because I can't get a genuine look-see at my background to see if I'd like it as my lightdm background. As I originally said, it's stretched out in zoom mode or something else that expands it to the point it's totally distorted.

I will surely opt to turn the background off if I cannot figure out how to display it in centered mode in lightdm but I'd at least enjoy the opportunity to make that decision based on normal view rather than stretched. My graphic was designed for center, actual size, normal view.

---

### Post by Trapper on 2012-04-04
> **ratcheer said:**
> , but now it shows the lightdm for a few seconds, then the Ubuntu default wallpaper. After I login and Unity comes up, it displays my wallpaper.

Tim

That's the same behavior I get. A couple of seconds of the default lightdm background then a stretched and distorted version of my desktop background as the lightdm background. After login I get the desktop background in centered mode.

---

### Post by Trapper on 2012-04-05
Okay, I am sort of bumping this thread. I now have an understanding that my desktop background will be used as the lightdm background but there are ways to stop that behavior or use a different image for the lightdm background. One thing is still unresolved though.

Is there a trick to get lightdm to display the desktop background in centered mode rather than the zoom mode or whatever enlarged mode lightdm is using? Should it not be displaying in the same mode I select to display the desktop background? That sounds logical to me but it's not the logic that lightdm is following. I have my desktop background displaying in centered mode. I WANT lightdm to utilize my desktop background .... BUT ... it utilizes it in some huge zoom mode that prohibits me from allowing lightdm to use my desktop background because it looks absolutely horrid.

---

### Post by cariboo on 2012-04-05
Does the zoom happen with all desktop backgrounds, or just the custom one? What video drivers are you using? The reason I ask about video drivers, is that I just rebooted after a new kernel, and my system didn't build nvidia-current-update correctly, so it defaulted to the nouveau driver, both lightdm and the regular desktop were zoomed in my case.

---

### Post by Trapper on 2012-04-05
> **cariboo907 said:**
> Does the zoom happen with all desktop backgrounds, or just the custom one? What video drivers are you using? The reason I ask about video drivers, is that I just rebooted after a new kernel, and my system didn't build nvidia-current-update correctly, so it defaulted to the nouveau driver, both lightdm and the regular desktop were zoomed in my case.

I'm glad you asked this because it gave me a brainflash and a possible workaround if I cannot resolve this issue any other way.

No, this DOES NOT happen with all desktop backgrounds. The ones that come with U12.04 display normally. I investigated that a bit. I tried one that was 2000x1330. I gives no option for display mode. It displays properly on the desktop and with lightdm. My background is only 496x88 in size and when selected the options for various display modes come available but if I select centered it is not honored by lightdm.

That leads me to believe that if I put my background into a larger transparent background I will be able to use it okay and won't have this stretch problem. I haven't test that yet though.

I ran sudo lspci -k and 'assume' that will give me correct information in regards to the video driver in use. Here are my results for that:

```
00:0d.0 VGA compatible controller: NVIDIA Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
    Subsystem: Biostar Microtech Int'l Corp Device 1405
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current, nouveau, nvidiafb
```

I am running 3.2.0-21-generic-pae

---

### Post by Trapper on 2012-04-05
I just created a new transparent background image the same size as my 1152x864 display resolution and center pasted my previous custom background image into it. Displays properly on my desktop and also in lightdm. Actually, it was spaced exactly where I was hoping for in lightdm.

---

### Post by cariboo on 2012-04-05
Glad to see you got the problem solved Trapper.

---

### Post by Trapper on 2012-04-06
> **cariboo907 said:**
> Glad to see you got the problem solved Trapper.

Well, I did figure out a simple workaround for me, personally, but I don't see it as a solved problem. I'm sure it'll be something that's worked out over time. This thread, though, I will mark as solved.

Did you get your nvidia-current-update situation straightened out? Late last night I had an upgrade to 3.2.0-22-generic-pae  and all went well.

---

### Post by cariboo on 2012-04-06
> **Trapper said:**
> Well, I did figure out a simple workaround for me, personally, but I don't see it as a solved problem. I'm sure it'll be something that's worked out over time. This thread, though, I will mark as solved.

Did you get your nvidia-current-update situation straightened out? Late last night I had an upgrade to 3.2.0-22-generic-pae  and all went well.

All runs well here. Thanks.

---

