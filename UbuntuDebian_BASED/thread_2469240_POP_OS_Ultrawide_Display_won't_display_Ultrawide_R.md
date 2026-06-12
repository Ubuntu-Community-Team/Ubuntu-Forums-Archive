---
title: "POP OS Ultrawide Display won't display Ultrawide Resolution"
date: 2021-11-23
forum: Ubuntu/Debian BASED
---

### Post by jeje162 on 2021-11-23
Hi all, 

I have installed a clean install of PopOS on my laptop which is installed to be a dual boot, however when I connect it to my external display an LG Ultragear at the resolution 3440x1440. In the past I was running Linux Mint where I had this same issue and I was not able to find a solution to it.

In terms of hardware issues, I have tried multiple display port cables with no luck alongside verifying that it will display with the same set up in windows which it does without issue, so I am convinced it is something to do with my laptop itself in some sort of setting. 

I have this same monitor also connected to another PC with a Nividia GPU and it displays perfectly with this monitor in PopOS hence why I tried to replace my Linux mint installation with a PopOS one to try and solve this issue (I also did enjoy using PopOS)

I have a 
HP Spectre x360 Convertible 13-ap0xxx (5KF07PA#ABG)
Intel(R) Core(TM) i7-8565U CPU @ 1.80GHz which has integrated UHD Graphics

These are outputs of commands I hope will be helpful, pretty much commands I saw people ask for when I have searched for this solution in the past alongside the command I used to try and change my resolution (As it was not working through the GUI  settings page)


```
jeje162_popos@pop-os:~$ xrandr 
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384
eDP-1 connected (normal left inverted right x axis y axis)
   1920x1080     60.03 +  60.01    59.97    59.96    59.93    40.02  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1600x900      59.99    59.94    59.95    59.82  
   1280x1024     60.02  
   1440x900      59.89  
   1400x900      59.96    59.88  
   1280x960      60.00  
   1440x810      60.00    59.97  
   1368x768      59.88    59.85  
   1360x768      59.80    59.96  
   1280x800      59.99    59.97    59.81    59.91  
   1152x864      60.00  
   1280x720      60.00    59.99    59.86    59.74  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   960x540       59.96    59.99    59.63    59.82  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   864x486       59.92    59.57  
   800x512       60.17  
   700x525       59.98  
   800x450       59.95    59.82  
   640x512       60.02  
   720x450       59.89  
   700x450       59.96    59.88  
   640x480       60.00    59.94  
   720x405       59.51    58.99  
   684x384       59.88    59.85  
   680x384       59.80    59.96  
   640x400       59.88    59.98  
   576x432       60.06  
   640x360       59.86    59.83    59.84    59.32  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.63    59.82  
   400x300       60.32    56.34  
   432x243       59.92    59.57  
   320x240       60.05  
   360x202       59.51    59.13  
   320x180       59.84    59.32  
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DP-1-1 disconnected (normal left inverted right x axis y axis)
DP-1-2 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 800mm x 335mm
   3440x1440     60.00 +
   1920x1080     74.98    60.00*   60.00    50.00    59.94  
   1680x1050     59.95  
   1600x900      60.00  
   1280x1024     75.02    60.02  
   1280x800      59.81  
   1152x864      59.97  
   1280x720      60.00    50.00    59.94  
   1024x768      60.00  
   800x600       60.32  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       60.00    59.94  
DP-1-3 disconnected (normal left inverted right x axis y axis)


jeje162_popos@pop-os:~$ xrandr --output DP-1-2 --mode 3440x1440
xrandr: Configure crtc 0 failed



```
```
jeje162_popos@pop-os:~$ xrandr --verbose
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384
eDP-1 connected (normal left inverted right x axis y axis)
    Identifier: 0x42
    Timestamp:  2830126
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1 2
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    _MUTTER_PRESENTATION_OUTPUT: 0 
    EDID: 
        00ffffffffffff0006af2d5700000000
        001c0104a51d1178032ea5a5544a9b27
        0e505400000001010101010101010101
        010101010101b43780a070383e403a2a
        350025a510000018232580a070383e40
        3a2a350025a510000018000000000000
        00000000000000000000000000000002
        001430ff123cc8320614c82020200020
    scaling mode: Full aspect 
        supported: Full, Center, Full aspect
    Colorspace: Default 
        supported: Default, RGB_Wide_Gamut_Fixed_Point, RGB_Wide_Gamut_Floating_Point, opRGB, DCI-P3_RGB_D65, BT2020_RGB, BT601_YCC, BT709_YCC, XVYCC_601, XVYCC_709, SYCC_601, opYCC_601, BT2020_CYCC, BT2020_YCC
    max bpc: 12 
        range: (6, 12)
    Broadcast RGB: Automatic 
        supported: Automatic, Full, Limited 16:235
    panel orientation: Normal 
        supported: Normal, Upside Down, Left Side Up, Right Side Up
    link-status: Good 
        supported: Good, Bad
    CONNECTOR_ID: 95 
        supported: 95
    non-desktop: 0 
        range: (0, 1)
  1920x1080 (0x46) 142.600MHz -HSync -VSync +preferred
        h: width  1920 start 1978 end 2020 total 2080 skew    0 clock  68.56KHz
        v: height 1080 start 1083 end 1088 total 1142           clock  60.03Hz
  1920x1080 (0x47) 356.375MHz -HSync +VSync DoubleScan
        h: width  1920 start 2080 end 2288 total 2656 skew    0 clock 134.18KHz
        v: height 1080 start 1081 end 1084 total 1118           clock  60.01Hz
  1920x1080 (0x48) 266.500MHz +HSync -VSync DoubleScan
        h: width  1920 start 1944 end 1960 total 2000 skew    0 clock 133.25KHz
        v: height 1080 start 1081 end 1084 total 1111           clock  59.97Hz
  1920x1080 (0x49) 173.000MHz -HSync +VSync
        h: width  1920 start 2048 end 2248 total 2576 skew    0 clock  67.16KHz
        v: height 1080 start 1083 end 1088 total 1120           clock  59.96Hz
  1920x1080 (0x4a) 138.500MHz +HSync -VSync
        h: width  1920 start 1968 end 2000 total 2080 skew    0 clock  66.59KHz
        v: height 1080 start 1083 end 1088 total 1111           clock  59.93Hz
  1920x1080 (0x4b) 95.070MHz -HSync -VSync
        h: width  1920 start 1978 end 2020 total 2080 skew    0 clock  45.71KHz
        v: height 1080 start 1083 end 1088 total 1142           clock  40.02Hz
  1680x1050 (0x4c) 146.250MHz -HSync +VSync
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock  65.29KHz
        v: height 1050 start 1053 end 1059 total 1089           clock  59.95Hz
  1680x1050 (0x4d) 119.000MHz +HSync -VSync
        h: width  1680 start 1728 end 1760 total 1840 skew    0 clock  64.67KHz
        v: height 1050 start 1053 end 1059 total 1080           clock  59.88Hz
  1600x1024 (0x4e) 103.125MHz +HSync +VSync
        h: width  1600 start 1600 end 1656 total 1664 skew    0 clock  61.97KHz
        v: height 1024 start 1024 end 1029 total 1030           clock  60.17Hz
  1400x1050 (0x4f) 122.000MHz +HSync +VSync
        h: width  1400 start 1488 end 1640 total 1880 skew    0 clock  64.89KHz
        v: height 1050 start 1052 end 1064 total 1082           clock  59.98Hz
  1600x900 (0x50) 246.000MHz -HSync +VSync DoubleScan
        h: width  1600 start 1728 end 1900 total 2200 skew    0 clock 111.82KHz
        v: height  900 start  901 end  904 total  932           clock  59.99Hz
  1600x900 (0x51) 186.500MHz +HSync -VSync DoubleScan
        h: width  1600 start 1624 end 1640 total 1680 skew    0 clock 111.01KHz
        v: height  900 start  901 end  904 total  926           clock  59.94Hz
  1600x900 (0x52) 118.250MHz -HSync +VSync
        h: width  1600 start 1696 end 1856 total 2112 skew    0 clock  55.99KHz
        v: height  900 start  903 end  908 total  934           clock  59.95Hz
  1600x900 (0x53) 97.500MHz +HSync -VSync
        h: width  1600 start 1648 end 1680 total 1760 skew    0 clock  55.40KHz
        v: height  900 start  903 end  908 total  926           clock  59.82Hz
  1280x1024 (0x54) 108.000MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock  63.98KHz
        v: height 1024 start 1025 end 1028 total 1066           clock  60.02Hz
  1440x900 (0x55) 106.500MHz -HSync +VSync
        h: width  1440 start 1520 end 1672 total 1904 skew    0 clock  55.93KHz
        v: height  900 start  903 end  909 total  934           clock  59.89Hz
  1400x900 (0x56) 103.500MHz -HSync +VSync
        h: width  1400 start 1480 end 1624 total 1848 skew    0 clock  56.01KHz
        v: height  900 start  903 end  913 total  934           clock  59.96Hz
  1400x900 (0x57) 86.500MHz +HSync -VSync
        h: width  1400 start 1448 end 1480 total 1560 skew    0 clock  55.45KHz
        v: height  900 start  903 end  913 total  926           clock  59.88Hz
  1280x960 (0x58) 108.000MHz +HSync +VSync
        h: width  1280 start 1376 end 1488 total 1800 skew    0 clock  60.00KHz
        v: height  960 start  961 end  964 total 1000           clock  60.00Hz
  1440x810 (0x59) 198.125MHz -HSync +VSync DoubleScan
        h: width  1440 start 1548 end 1704 total 1968 skew    0 clock 100.67KHz
        v: height  810 start  811 end  814 total  839           clock  60.00Hz
  1440x810 (0x5a) 151.875MHz +HSync -VSync DoubleScan
        h: width  1440 start 1464 end 1480 total 1520 skew    0 clock  99.92KHz
        v: height  810 start  811 end  814 total  833           clock  59.97Hz
  1368x768 (0x5b) 85.250MHz -HSync +VSync
        h: width  1368 start 1440 end 1576 total 1784 skew    0 clock  47.79KHz
        v: height  768 start  771 end  781 total  798           clock  59.88Hz
  1368x768 (0x5c) 72.250MHz +HSync -VSync
        h: width  1368 start 1416 end 1448 total 1528 skew    0 clock  47.28KHz
        v: height  768 start  771 end  781 total  790           clock  59.85Hz
  1360x768 (0x5d) 84.750MHz -HSync +VSync
        h: width  1360 start 1432 end 1568 total 1776 skew    0 clock  47.72KHz
        v: height  768 start  771 end  781 total  798           clock  59.80Hz
  1360x768 (0x5e) 72.000MHz +HSync -VSync
        h: width  1360 start 1408 end 1440 total 1520 skew    0 clock  47.37KHz
        v: height  768 start  771 end  781 total  790           clock  59.96Hz
  1280x800 (0x5f) 174.250MHz -HSync +VSync DoubleScan
        h: width  1280 start 1380 end 1516 total 1752 skew    0 clock  99.46KHz
        v: height  800 start  801 end  804 total  829           clock  59.99Hz
  1280x800 (0x60) 134.250MHz +HSync -VSync DoubleScan
        h: width  1280 start 1304 end 1320 total 1360 skew    0 clock  98.71KHz
        v: height  800 start  801 end  804 total  823           clock  59.97Hz
  1280x800 (0x61) 83.500MHz -HSync +VSync
        h: width  1280 start 1352 end 1480 total 1680 skew    0 clock  49.70KHz
        v: height  800 start  803 end  809 total  831           clock  59.81Hz
  1280x800 (0x62) 71.000MHz +HSync -VSync
        h: width  1280 start 1328 end 1360 total 1440 skew    0 clock  49.31KHz
        v: height  800 start  803 end  809 total  823           clock  59.91Hz
  1152x864 (0x63) 81.620MHz -HSync +VSync
        h: width  1152 start 1216 end 1336 total 1520 skew    0 clock  53.70KHz
        v: height  864 start  865 end  868 total  895           clock  60.00Hz
  1280x720 (0x64) 156.125MHz -HSync +VSync DoubleScan
        h: width  1280 start 1376 end 1512 total 1744 skew    0 clock  89.52KHz
        v: height  720 start  721 end  724 total  746           clock  60.00Hz
  1280x720 (0x65) 120.750MHz +HSync -VSync DoubleScan
        h: width  1280 start 1304 end 1320 total 1360 skew    0 clock  88.79KHz
        v: height  720 start  721 end  724 total  740           clock  59.99Hz
  1280x720 (0x66) 74.500MHz -HSync +VSync
        h: width  1280 start 1344 end 1472 total 1664 skew    0 clock  44.77KHz
        v: height  720 start  723 end  728 total  748           clock  59.86Hz
  1280x720 (0x67) 63.750MHz +HSync -VSync
        h: width  1280 start 1328 end 1360 total 1440 skew    0 clock  44.27KHz
        v: height  720 start  723 end  728 total  741           clock  59.74Hz
  1024x768 (0x68) 133.475MHz -HSync +VSync DoubleScan
        h: width  1024 start 1100 end 1212 total 1400 skew    0 clock  95.34KHz
        v: height  768 start  768 end  770 total  794           clock  60.04Hz
  1024x768 (0x69) 65.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  960x720 (0x6a) 117.000MHz -HSync +VSync DoubleScan
        h: width   960 start 1024 end 1128 total 1300 skew    0 clock  90.00KHz
        v: height  720 start  720 end  722 total  750           clock  60.00Hz
  928x696 (0x6b) 109.150MHz -HSync +VSync DoubleScan
        h: width   928 start  976 end 1088 total 1264 skew    0 clock  86.35KHz
        v: height  696 start  696 end  698 total  719           clock  60.05Hz
  896x672 (0x6c) 102.400MHz -HSync +VSync DoubleScan
        h: width   896 start  960 end 1060 total 1224 skew    0 clock  83.66KHz
        v: height  672 start  672 end  674 total  697           clock  60.01Hz
  1024x576 (0x6d) 98.500MHz -HSync +VSync DoubleScan
        h: width  1024 start 1092 end 1200 total 1376 skew    0 clock  71.58KHz
        v: height  576 start  577 end  580 total  597           clock  59.95Hz
  1024x576 (0x6e) 78.375MHz +HSync -VSync DoubleScan
        h: width  1024 start 1048 end 1064 total 1104 skew    0 clock  70.99KHz
        v: height  576 start  577 end  580 total  592           clock  59.96Hz
  1024x576 (0x6f) 46.500MHz -HSync +VSync
        h: width  1024 start 1064 end 1160 total 1296 skew    0 clock  35.88KHz
        v: height  576 start  579 end  584 total  599           clock  59.90Hz
  1024x576 (0x70) 42.000MHz +HSync -VSync
        h: width  1024 start 1072 end 1104 total 1184 skew    0 clock  35.47KHz
        v: height  576 start  579 end  584 total  593           clock  59.82Hz
  960x600 (0x71) 96.625MHz -HSync +VSync DoubleScan
        h: width   960 start 1028 end 1128 total 1296 skew    0 clock  74.56KHz
        v: height  600 start  601 end  604 total  622           clock  59.93Hz
  960x600 (0x72) 77.000MHz +HSync -VSync DoubleScan
        h: width   960 start  984 end 1000 total 1040 skew    0 clock  74.04KHz
        v: height  600 start  601 end  604 total  617           clock  60.00Hz
  960x540 (0x73) 86.500MHz -HSync +VSync DoubleScan
        h: width   960 start 1024 end 1124 total 1288 skew    0 clock  67.16KHz
        v: height  540 start  541 end  544 total  560           clock  59.96Hz
  960x540 (0x74) 69.250MHz +HSync -VSync DoubleScan
        h: width   960 start  984 end 1000 total 1040 skew    0 clock  66.59KHz
        v: height  540 start  541 end  544 total  555           clock  59.99Hz
  960x540 (0x75) 40.750MHz -HSync +VSync
        h: width   960 start  992 end 1088 total 1216 skew    0 clock  33.51KHz
        v: height  540 start  543 end  548 total  562           clock  59.63Hz
  960x540 (0x76) 37.250MHz +HSync -VSync
        h: width   960 start 1008 end 1040 total 1120 skew    0 clock  33.26KHz
        v: height  540 start  543 end  548 total  556           clock  59.82Hz
  800x600 (0x77) 81.000MHz +HSync +VSync DoubleScan
        h: width   800 start  832 end  928 total 1080 skew    0 clock  75.00KHz
        v: height  600 start  600 end  602 total  625           clock  60.00Hz
  800x600 (0x78) 40.000MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  800x600 (0x79) 36.000MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock  35.16KHz
        v: height  600 start  601 end  603 total  625           clock  56.25Hz
  840x525 (0x7a) 73.125MHz -HSync +VSync DoubleScan
        h: width   840 start  892 end  980 total 1120 skew    0 clock  65.29KHz
        v: height  525 start  526 end  529 total  544           clock  60.01Hz
  840x525 (0x7b) 59.500MHz +HSync -VSync DoubleScan
        h: width   840 start  864 end  880 total  920 skew    0 clock  64.67KHz
        v: height  525 start  526 end  529 total  540           clock  59.88Hz
  864x486 (0x7c) 32.500MHz -HSync +VSync
        h: width   864 start  888 end  968 total 1072 skew    0 clock  30.32KHz
        v: height  486 start  489 end  494 total  506           clock  59.92Hz
  864x486 (0x7d) 30.500MHz +HSync -VSync
        h: width   864 start  912 end  944 total 1024 skew    0 clock  29.79KHz
        v: height  486 start  489 end  494 total  500           clock  59.57Hz
  800x512 (0x7e) 51.562MHz +HSync +VSync DoubleScan
        h: width   800 start  800 end  828 total  832 skew    0 clock  61.97KHz
        v: height  512 start  512 end  514 total  515           clock  60.17Hz
  700x525 (0x7f) 61.000MHz +HSync +VSync DoubleScan
        h: width   700 start  744 end  820 total  940 skew    0 clock  64.89KHz
        v: height  525 start  526 end  532 total  541           clock  59.98Hz
  800x450 (0x80) 59.125MHz -HSync +VSync DoubleScan
        h: width   800 start  848 end  928 total 1056 skew    0 clock  55.99KHz
        v: height  450 start  451 end  454 total  467           clock  59.95Hz
  800x450 (0x81) 48.750MHz +HSync -VSync DoubleScan
        h: width   800 start  824 end  840 total  880 skew    0 clock  55.40KHz
        v: height  450 start  451 end  454 total  463           clock  59.82Hz
  640x512 (0x82) 54.000MHz +HSync +VSync DoubleScan
        h: width   640 start  664 end  720 total  844 skew    0 clock  63.98KHz
        v: height  512 start  512 end  514 total  533           clock  60.02Hz
  720x450 (0x83) 53.250MHz -HSync +VSync DoubleScan
        h: width   720 start  760 end  836 total  952 skew    0 clock  55.93KHz
        v: height  450 start  451 end  454 total  467           clock  59.89Hz
  700x450 (0x84) 51.750MHz -HSync +VSync DoubleScan
        h: width   700 start  740 end  812 total  924 skew    0 clock  56.01KHz
        v: height  450 start  451 end  456 total  467           clock  59.96Hz
  700x450 (0x85) 43.250MHz +HSync -VSync DoubleScan
        h: width   700 start  724 end  740 total  780 skew    0 clock  55.45KHz
        v: height  450 start  451 end  456 total  463           clock  59.88Hz
  640x480 (0x86) 54.000MHz +HSync +VSync DoubleScan
        h: width   640 start  688 end  744 total  900 skew    0 clock  60.00KHz
        v: height  480 start  480 end  482 total  500           clock  60.00Hz
  640x480 (0x87) 25.175MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz
  720x405 (0x88) 22.500MHz -HSync +VSync
        h: width   720 start  744 end  808 total  896 skew    0 clock  25.11KHz
        v: height  405 start  408 end  413 total  422           clock  59.51Hz
  720x405 (0x89) 21.750MHz +HSync -VSync
        h: width   720 start  768 end  800 total  880 skew    0 clock  24.72KHz
        v: height  405 start  408 end  413 total  419           clock  58.99Hz
  684x384 (0x8a) 42.625MHz -HSync +VSync DoubleScan
        h: width   684 start  720 end  788 total  892 skew    0 clock  47.79KHz
        v: height  384 start  385 end  390 total  399           clock  59.88Hz
  684x384 (0x8b) 36.125MHz +HSync -VSync DoubleScan
        h: width   684 start  708 end  724 total  764 skew    0 clock  47.28KHz
        v: height  384 start  385 end  390 total  395           clock  59.85Hz
  680x384 (0x8c) 42.375MHz -HSync +VSync DoubleScan
        h: width   680 start  716 end  784 total  888 skew    0 clock  47.72KHz
        v: height  384 start  385 end  390 total  399           clock  59.80Hz
  680x384 (0x8d) 36.000MHz +HSync -VSync DoubleScan
        h: width   680 start  704 end  720 total  760 skew    0 clock  47.37KHz
        v: height  384 start  385 end  390 total  395           clock  59.96Hz
  640x400 (0x8e) 41.750MHz -HSync +VSync DoubleScan
        h: width   640 start  676 end  740 total  840 skew    0 clock  49.70KHz
        v: height  400 start  401 end  404 total  415           clock  59.88Hz
  640x400 (0x8f) 35.500MHz +HSync -VSync DoubleScan
        h: width   640 start  664 end  680 total  720 skew    0 clock  49.31KHz
        v: height  400 start  401 end  404 total  411           clock  59.98Hz
  576x432 (0x90) 40.810MHz -HSync +VSync DoubleScan
        h: width   576 start  608 end  668 total  760 skew    0 clock  53.70KHz
        v: height  432 start  432 end  434 total  447           clock  60.06Hz
  640x360 (0x91) 37.250MHz -HSync +VSync DoubleScan
        h: width   640 start  672 end  736 total  832 skew    0 clock  44.77KHz
        v: height  360 start  361 end  364 total  374           clock  59.86Hz
  640x360 (0x92) 31.875MHz +HSync -VSync DoubleScan
        h: width   640 start  664 end  680 total  720 skew    0 clock  44.27KHz
        v: height  360 start  361 end  364 total  370           clock  59.83Hz
  640x360 (0x93) 18.000MHz -HSync +VSync
        h: width   640 start  664 end  720 total  800 skew    0 clock  22.50KHz
        v: height  360 start  363 end  368 total  376           clock  59.84Hz
  640x360 (0x94) 17.750MHz +HSync -VSync
        h: width   640 start  688 end  720 total  800 skew    0 clock  22.19KHz
        v: height  360 start  363 end  368 total  374           clock  59.32Hz
  512x384 (0x95) 32.500MHz -HSync -VSync DoubleScan
        h: width   512 start  524 end  592 total  672 skew    0 clock  48.36KHz
        v: height  384 start  385 end  388 total  403           clock  60.00Hz
  512x288 (0x96) 23.250MHz -HSync +VSync DoubleScan
        h: width   512 start  532 end  580 total  648 skew    0 clock  35.88KHz
        v: height  288 start  289 end  292 total  299           clock  60.00Hz
  512x288 (0x97) 21.000MHz +HSync -VSync DoubleScan
        h: width   512 start  536 end  552 total  592 skew    0 clock  35.47KHz
        v: height  288 start  289 end  292 total  296           clock  59.92Hz
  480x270 (0x98) 20.375MHz -HSync +VSync DoubleScan
        h: width   480 start  496 end  544 total  608 skew    0 clock  33.51KHz
        v: height  270 start  271 end  274 total  281           clock  59.63Hz
  480x270 (0x99) 18.625MHz +HSync -VSync DoubleScan
        h: width   480 start  504 end  520 total  560 skew    0 clock  33.26KHz
        v: height  270 start  271 end  274 total  278           clock  59.82Hz
  400x300 (0x9a) 20.000MHz +HSync +VSync DoubleScan
        h: width   400 start  420 end  484 total  528 skew    0 clock  37.88KHz
        v: height  300 start  300 end  302 total  314           clock  60.32Hz
  400x300 (0x9b) 18.000MHz +HSync +VSync DoubleScan
        h: width   400 start  412 end  448 total  512 skew    0 clock  35.16KHz
        v: height  300 start  300 end  301 total  312           clock  56.34Hz
  432x243 (0x9c) 16.250MHz -HSync +VSync DoubleScan
        h: width   432 start  444 end  484 total  536 skew    0 clock  30.32KHz
        v: height  243 start  244 end  247 total  253           clock  59.92Hz
  432x243 (0x9d) 15.250MHz +HSync -VSync DoubleScan
        h: width   432 start  456 end  472 total  512 skew    0 clock  29.79KHz
        v: height  243 start  244 end  247 total  250           clock  59.57Hz
  320x240 (0x9e) 12.587MHz -HSync -VSync DoubleScan
        h: width   320 start  328 end  376 total  400 skew    0 clock  31.47KHz
        v: height  240 start  245 end  246 total  262           clock  60.05Hz
  360x202 (0x9f) 11.250MHz -HSync +VSync DoubleScan
        h: width   360 start  372 end  404 total  448 skew    0 clock  25.11KHz
        v: height  202 start  204 end  206 total  211           clock  59.51Hz
  360x202 (0xa0) 10.875MHz +HSync -VSync DoubleScan
        h: width   360 start  384 end  400 total  440 skew    0 clock  24.72KHz
        v: height  202 start  204 end  206 total  209           clock  59.13Hz
  320x180 (0xa1)  9.000MHz -HSync +VSync DoubleScan
        h: width   320 start  332 end  360 total  400 skew    0 clock  22.50KHz
        v: height  180 start  181 end  184 total  188           clock  59.84Hz
  320x180 (0xa2)  8.875MHz +HSync -VSync DoubleScan
        h: width   320 start  344 end  360 total  400 skew    0 clock  22.19KHz
        v: height  180 start  181 end  184 total  187           clock  59.32Hz
DP-1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x43
    Timestamp:  2830126
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1 2
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    HDCP Content Type: HDCP Type0 
        supported: HDCP Type0, HDCP Type1
    Content Protection: Undesired 
        supported: Undesired, Desired, Enabled
    Colorspace: Default 
        supported: Default, RGB_Wide_Gamut_Fixed_Point, RGB_Wide_Gamut_Floating_Point, opRGB, DCI-P3_RGB_D65, BT2020_RGB, BT601_YCC, BT709_YCC, XVYCC_601, XVYCC_709, SYCC_601, opYCC_601, BT2020_CYCC, BT2020_YCC
    max bpc: 12 
        range: (6, 12)
    Broadcast RGB: Automatic 
        supported: Automatic, Full, Limited 16:235
    audio: auto 
        supported: force-dvi, off, auto, on
    subconnector: Unknown 
        supported: Unknown, VGA, DVI-D, HDMI, DP, Wireless, Native
    link-status: Good 
        supported: Good, Bad
    CONNECTOR_ID: 103 
        supported: 103
    non-desktop: 0 
        range: (0, 1)
DP-2 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x44
    Timestamp:  2830126
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1 2
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    HDCP Content Type: HDCP Type0 
        supported: HDCP Type0, HDCP Type1
    Content Protection: Undesired 
        supported: Undesired, Desired, Enabled
    Colorspace: Default 
        supported: Default, RGB_Wide_Gamut_Fixed_Point, RGB_Wide_Gamut_Floating_Point, opRGB, DCI-P3_RGB_D65, BT2020_RGB, BT601_YCC, BT709_YCC, XVYCC_601, XVYCC_709, SYCC_601, opYCC_601, BT2020_CYCC, BT2020_YCC
    max bpc: 12 
        range: (6, 12)
    Broadcast RGB: Automatic 
        supported: Automatic, Full, Limited 16:235
    audio: auto 
        supported: force-dvi, off, auto, on
    subconnector: Unknown 
        supported: Unknown, VGA, DVI-D, HDMI, DP, Wireless, Native
    link-status: Good 
        supported: Good, Bad
    CONNECTOR_ID: 114 
        supported: 114
    non-desktop: 0 
        range: (0, 1)
DP-1-1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x7ca
    Timestamp:  2830126
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1 2
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    non-desktop: 0 
        supported: 0, 1
DP-1-2 connected primary 1920x1080+0+0 (0x7cf) normal (normal left inverted right x axis y axis) 800mm x 335mm
    Identifier: 0x7cb
    Timestamp:  2830126
    Subpixel:   unknown
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:    
    CRTC:       0
    CRTCs:      0 1 2
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    EDID: 
        00ffffffffffff001e6d4b773fb80a00
        011f0104b55021789ff675af4e42ab26
        0e50542109007140818081c0a9c0b300
        d1c08100d1cfdaa77050d5a034509020
        3a30204f3100001a000000fd0030a0fa
        fa5a010a202020202020000000fc004c
        4720554c545241474541520a000000ff
        003130314e544e484c4e3532370a02dd
        020330712309070747100403011f1312
        83010000e305c000e2006ae606050161
        613d6d1a0000020530a00004613d613d
        4ed470d0d0a0325030203a00204f3100
        001a0000000000000000000000000000
        00000000000000000000000000000000
        00000000000000000000000000000000
        000000000000000000000000000000de
        7012790000030128663801866f0def00
        2f801f009f054500020009004c5b0106
        6f0def008f801f009f05450002000900
        00000000000000000000000000000000
        00000000000000000000000000000000
        00000000000000000000000000000000
        00000000000000000000000000000000
        0000000000000000000000000000bc90
    _MUTTER_PRESENTATION_OUTPUT: 0 
    non-desktop: 0 
        supported: 0, 1
  3440x1440 (0x7cd) 429.700MHz +HSync -VSync +preferred
        h: width  3440 start 3584 end 4384 total 4800 skew    0 clock  89.52KHz
        v: height 1440 start 1443 end 1453 total 1492           clock  60.00Hz
  1920x1080 (0x7ce) 220.960MHz -HSync +VSync
        h: width  1920 start 2064 end 2264 total 2608 skew    0 clock  84.72KHz
        v: height 1080 start 1083 end 1088 total 1130           clock  74.98Hz
  1920x1080 (0x7cf) 148.500MHz -HSync -VSync *current
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  67.50KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  60.00Hz
  1920x1080 (0x7d0) 148.500MHz +HSync +VSync
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  67.50KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  60.00Hz
  1920x1080 (0x7d1) 148.500MHz +HSync +VSync
        h: width  1920 start 2448 end 2492 total 2640 skew    0 clock  56.25KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  50.00Hz
  1920x1080 (0x7d2) 148.352MHz +HSync +VSync
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  67.43KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  59.94Hz
  1680x1050 (0x4c) 146.250MHz -HSync +VSync
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock  65.29KHz
        v: height 1050 start 1053 end 1059 total 1089           clock  59.95Hz
  1600x900 (0x7d3) 108.000MHz +HSync +VSync
        h: width  1600 start 1624 end 1704 total 1800 skew    0 clock  60.00KHz
        v: height  900 start  901 end  904 total 1000           clock  60.00Hz
  1280x1024 (0x7d4) 135.000MHz +HSync +VSync
        h: width  1280 start 1296 end 1440 total 1688 skew    0 clock  79.98KHz
        v: height 1024 start 1025 end 1028 total 1066           clock  75.02Hz
  1280x1024 (0x54) 108.000MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock  63.98KHz
        v: height 1024 start 1025 end 1028 total 1066           clock  60.02Hz
  1280x800 (0x61) 83.500MHz -HSync +VSync
        h: width  1280 start 1352 end 1480 total 1680 skew    0 clock  49.70KHz
        v: height  800 start  803 end  809 total  831           clock  59.81Hz
  1152x864 (0x7d5) 81.768MHz -HSync +VSync
        h: width  1152 start 1216 end 1336 total 1520 skew    0 clock  53.79KHz
        v: height  864 start  867 end  871 total  897           clock  59.97Hz
  1280x720 (0x7d6) 74.250MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock  45.00KHz
        v: height  720 start  725 end  730 total  750           clock  60.00Hz
  1280x720 (0x7d7) 74.250MHz +HSync +VSync
        h: width  1280 start 1720 end 1760 total 1980 skew    0 clock  37.50KHz
        v: height  720 start  725 end  730 total  750           clock  50.00Hz
  1280x720 (0x7d8) 74.176MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock  44.96KHz
        v: height  720 start  725 end  730 total  750           clock  59.94Hz
  1024x768 (0x69) 65.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  800x600 (0x78) 40.000MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  720x576 (0x7d9) 27.000MHz -HSync -VSync
        h: width   720 start  732 end  796 total  864 skew    0 clock  31.25KHz
        v: height  576 start  581 end  586 total  625           clock  50.00Hz
  720x480 (0x7da) 27.027MHz -HSync -VSync
        h: width   720 start  736 end  798 total  858 skew    0 clock  31.50KHz
        v: height  480 start  489 end  495 total  525           clock  60.00Hz
  720x480 (0x7db) 27.000MHz -HSync -VSync
        h: width   720 start  736 end  798 total  858 skew    0 clock  31.47KHz
        v: height  480 start  489 end  495 total  525           clock  59.94Hz
  640x480 (0x7dc) 25.200MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.50KHz
        v: height  480 start  490 end  492 total  525           clock  60.00Hz
  640x480 (0x87) 25.175MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz
DP-1-3 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x7cc
    Timestamp:  2830126
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1 2
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    non-desktop: 0 
        supported: 0, 1
```

---

### Post by Frogs Hair on 2021-11-24
jeje162: 

To add code tags to your terminal output highlight the text with the cursor and select # symbol on the reply box toolbar.

---

### Post by jeje162 on 2021-11-24
Thanks, this was my first post to the forum. I will keep this in mind for future

---

### Post by Tadaen_Sylvermane on 2021-11-24
Have you tried the cable from the other machine that works? I don't know DP to be honest but I know for HDMI there are 4 classes of cable. The lower end can't break a resolution or hz wall, hence the higher types. Again for HDMI there is hdmi, hdmi with ethernet, highspeed hdmi, and highspeed hdmi with ethernet. If the cable is an older version it may just be that simple? Again assuming DP works the same way. I don't really know. I've always assumed they were the same standard as HDMI.

---

### Post by jeje162 on 2021-11-29
Yes, I have tried multiple cables which are all DP1.4 they should all be fine to use, also by verifying that it works with windows on the same laptop I can ensure that this is not the issue.

---

