---
title: "How do I input video driver data?"
date: 2006-06-08
forum: The Cafe
---

### Post by fortherose on 2006-06-08
I am new to this forum and not too sure how to use it, but here goes. I don't know if I'm speaking to a group or an individual, but here is my question. How and where do I input the following data, in order to improve the performance of my ATI Radeon x700 on my laptop. I don't know much about programming, but I can follow directions well. Thank you very much...James

Section "Device"
Identifier "card0"
Driver "fglrx"
Option "no_accel" "no"
Option "no_dri" "no"
Option "DynamicClocks" "on"
Option "mtrr" "on"
Option "DesktopSetup" "Single"
Option "ScreenOverlap" "0"
Option "Capabilities" "0x00000000"
Option "CapabilitiesEx" "0x00000000"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
Option "CenterMode" "off"
Option "PseudoColorVisuals" "off"
Option "Stereo" "off"
Option "StereoSyncEnable" "1"
Option "FSAAEnable" "no"
Option "FSAAScale" "1"
Option "FSAADisableGamma" "no"
Option "FSAACustomizeMSPos" "no"
Option "FSAAMSPosX0" "0.000000"
Option "FSAAMSPosY0" "0.000000"
Option "FSAAMSPosX1" "0.000000"
Option "FSAAMSPosY1" "0.000000"
Option "FSAAMSPosX2" "0.000000"
Option "FSAAMSPosY2" "0.000000"
Option "FSAAMSPosX3" "0.000000"
Option "FSAAMSPosY3" "0.000000"
Option "FSAAMSPosX4" "0.000000"
Option "FSAAMSPosY4" "0.000000"
Option "FSAAMSPosX5" "0.000000"
Option "FSAAMSPosY5" "0.000000"
Option "UseFastTLS" "0"
Option "BlockSignalsOnLock" "on"
Option "UseInternalAGPGART" "no"
Option "ForceGenericCPU" "no"
Option "KernelModuleParm" "agplock=0"
Option "PowerState" "1"
BusID "PCI:1:0:0"
EndSection

---

