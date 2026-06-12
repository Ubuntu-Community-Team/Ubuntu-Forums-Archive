---
title: "HowTo configure 8.04 for Jack part 3"
date: 2009-10-15
forum: Ubuntu Studio
---

### Post by llwdtp on 2009-10-15
[SIZE=5]**Autospawn**[/SIZE]
Next we make sure autospawn is turned off. Execute the following command in a terminal window as shown:

[IMG]http://docs.google.com/File?id=dhjrjpnc_21m949chfm_b[/IMG]

Edit the file and make sure autospawn=no

[LEFT][IMG]http://docs.google.com/File?id=dhjrjpnc_20grqmq8zm_b[/IMG]



[SIZE=5]**Default.pa**[/SIZE]
Open the file default.pa as shown below.

[LEFT][IMG]http://docs.google.com/File?id=dhjrjpnc_22fcv66fhs_b[/IMG]

Add the following 2 lines to the file.

[LEFT][IMG]http://docs.google.com/File?id=dhjrjpnc_23hbvk3mdm_b[/IMG][/LEFT]

[/LEFT]

[/LEFT]

[SIZE=5]**Stop CD polling**[/SIZE]
[SIZE=2]
On my computer HAL polls the computer every 2 seconds to see if a CD has been inserted. This can cause a problem with Jack. To see a list of items use
[/SIZE][FONT=Courier New][I][B]ps ax|grep hald-addon-storage|grep polling

[LEFT][IMG]http://docs.google.com/File?id=dhjrjpnc_10ghzh3mff_b[/IMG][/LEFT]

[/B][/I][/FONT][FONT=Courier New]execute the command *sudo hal-disable-polling --device /dev/scd0*
[/FONT]
[LEFT][IMG]http://docs.google.com/File?id=dhjrjpnc_11d2rp63cw_b[/IMG]

Check to see that the poling is disabled.
[FONT=Courier New]***ps ax|grep hald-addon-storage|grep polling***[/FONT]
[/LEFT]

[SIZE=2][LEFT][IMG]http://docs.google.com/File?id=dhjrjpnc_12jpfsj3gm_b[/IMG][/LEFT]

Restart the computer and you should be ready to setup Jack.

[SIZE=5][B]Setup jack
[/B][SIZE=2]You should now be ready to setup jack. See this [article]("http://www.linuxjournal.com/content/judgement-day-studio-dave-tests-ubuntu-studio-904") by Studio Dave to help with the jack setup. By the way, with all this I continued to get xruns using my Sound blaster live until I changed jack to playback only. 

[SIZE=5]**In the End**[/SIZE]
I did get it to work. I tried hard to setup 9.04. But I could never get of xruns while trying to run jack. Others said that there were known problems in the associated reat time kernal that could be the issue. So I went back a version and did get it to work.

[/SIZE][/SIZE]
[/SIZE][I][SIZE=2][B]Search terms
[/B][/SIZE][/I][SIZE=2]How do I set up jack
I get many xruns with jack
whci is the best ubuntu studio for audio work.

[/SIZE]

---

