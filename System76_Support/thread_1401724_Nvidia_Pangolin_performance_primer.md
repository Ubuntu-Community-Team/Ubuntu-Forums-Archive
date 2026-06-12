---
title: "Nvidia Pangolin performance primer"
date: 2010-02-08
forum: System76 Support
---

### Post by miniyak on 2010-02-08
*Keep in mind that this information is just from my experience w/ the panp5, feel free to add anything on other models of the pangolin series, I assume this will cover most of the models w/ an Nvidia gpu*

 **A little backstory**- When I first got my panp5, almost immediately i hooked it up to a large 40inch 1080p display wanting to using it as a second independent screen. Unfortunately i ran into a few issues. Here ill go over how i easily got around these issues just by bringing a different understanding to the table as i slowly tinkered w/ things over the past months.

  **Terms-** some of these i found counter intuitive, i'm going to just break them down to lame terms
[LIST=1]
[*]   **X**- this the total screen space that shows up on the monitors and thus the mouse can move over. The gpu is driving something called the x server and the nvidia-setting interface is just telling the gpu how to do it. (again...lame terms, you can correct me on the details below) 

[*]   **TwinView**- This stretches x to a second monitor and trims the excess resolution of the smaller (optimal set up imho) 

[*]   **Separate X screen**- This option makes a separate x screen on the second monitor of the same resolution. Meaning the mouse pans the screen on the smaller monitor. Requires restart an admin privileges to set. (pointless imho)
[/LIST]
  
  **My optimal set-up- **
 
 [LIST]
[*] first Plug-in second monitor
[*] open nvidia-settings
[*] X sever display cofig
[*] detect monitor (if only one is found)
[*] select the disabled monitor
[*] select configure button
[*] select TwinView
[*] you can move the position of the screen by grabbing the picture representation in the "layout" box and orienting it the way it is set-up
[*] select apply
[/LIST]
In most case this should be a great way to set-up a good work station, as opposed to using the "fn-f7" shortcut which only sets up a "Mirrored" second screen which typically looks awful in my personal experience. Also note that I have only tested this relatively simple set-up in karmic, because i thought TwinView meant the same as mirrored before recently. (doh!)

 **Other Road-Blocks-** 

Overscan- this is when the x screen gets expanded beyond the edge of the screen. It happens on many TVs and sometimes it can be fixed through the tvs setting and sometimes another option will show up in the nvidia-setting interface under "gpu-0" after selecting the monitor in question. There sometimes is an option allowing overscan to be adjusted.

HDMI not working- The only practical advantage that HDMI has over VGA is the size of the cable and sound compatibility(sometimes). Anyhow, this issue sometimes occurs with sets using an older hdmi standard. My advice is use VGA if you can, and save the headache. HDMI to DVI should typically work however.

Insignificant Privileges in Nvidia-settings- open the terminal and type
```
sudo nvidia-settings
```

---

### Post by samalex on 2010-02-08
I still haven't had any luck getting HDMI to work well, plus I don't know of anyone that has audio working with the PanP5 and Ubuntu 9.04, which is what I'm running.

For me I use my PanP5 with our HDTV all the time via the VGA cable.  I just use the NVidia settings under the System Preferences section by enabling the second display at 1920×1080 and disabling the LCD display.  Once I click Accept the LCD display goes off and TV comes on with full 1080 resolution with no distortion.

Sam

---

### Post by miniyak on 2010-02-08
good point bringing up distortion, w/ hdmi in 9.04 i noticed actual distortion issues. because of overscan i think.. 

Another thing to note: In the dual screen set-up the desktop seems to distort giving the illusion that something messed up because the current wallpaper in memory gets stretched. Changing the wallpaper refreshes the image giving a crisper look. (depending on the image)

---

### Post by Lee_Machine on 2010-02-08
> **samalex said:**
> I still haven't had any luck getting HDMI to work well, plus I don't know of anyone that has audio working with the PanP5 and Ubuntu 9.04, which is what I'm running.


For me audio over HDMI didn't work until 9.10. That was on a Panp4

---

