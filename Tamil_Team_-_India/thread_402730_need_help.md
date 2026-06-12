---
title: "need help"
date: 2007-04-06
forum: Tamil Team - India
---

### Post by ashokcz on 2007-04-06
hi all i m ashok from chennai ...... i m not sure is this the right place to ask this question but i m new to ubuntu and to this forums and so i thought like posting question in this forum would help me ..... 

i have got a problem in installing and running ubuntu edgy eft in my machine 
i have stated this in one of the threads here 

[[COLOR="Red"]http://ubuntuforums.org/showthread.php?p=2410342[/COLOR]]("http://ubuntuforums.org/showthread.php?p=2410342")

but i couldn't get any  replies is there anything wrong with this thread ...... i m totally gone 

if someone could help me

regards 

ashok

---

### Post by sarutv on 2007-04-06
&#2949;&#2999;&#3019;&#2965;&#3021;, &#2984;&#3008;&#2969;&#3021;&#2965;&#2995;&#3021;  &#2959;&#2985;&#3021; &#2990;&#2993;&#3021;&#2993; &#2980;&#3018;&#2975;&#2992;&#3007;&#2994;&#3021; &#2965;&#3015;&#2975;&#3021;&#2975; &#2965;&#3015;&#2995;&#3021;&#2997;&#3007;&#2965;&#3021;&#2965;&#3009; &#2986;&#2980;&#3007;&#2994;&#3021; &#2970;&#3018;&#2994;&#3021;&#2994;&#2997;&#3007;&#2994;&#3021;&#2994;&#3016;.

"Frequency out of range" could be caused by your X server choosing the wrong frequency for your monitor. You can restart your computer but in recovery mode. So Ubuntu starts in console mode. 

1. Then  type "sudo dpkg-reconfigure xserver-xorg". 

2. Follow the instructions on screen. When it says "Attempt Monitor Autodetection", asnwer "Yes", your screen might go blank for few seconds, then it will come up with an identifier for the monitor, mostly it will be name of the monitor but otherwise it will be something like "Generic Monitor".

3. Next  select videos modes to be used. It would have automatically selected some modes like "1024x768". Dont select modes that you know you monitor or video card can't support. If you used windows before, you can select the screen resolutions that worked there. Click ok.

4. X needs more information  about the monitor like the horizontal vertical sync, resolutions etc. But if you dont know the exact values you shouldn't risk typing random values (Cos I 've heard smoke coming out of peoples' monitors when wrong settings are used).  So choose either "Simple" or "Medium " setup and choose some monitor settings. Continue and finish the setup. 

5. Restart the computer in normal mode. Your X should work. If not retry the above steps. Otherwise you need to give us more info.

---

