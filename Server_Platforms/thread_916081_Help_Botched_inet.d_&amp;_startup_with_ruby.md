---
title: "Help: Botched inet.d &amp; startup with ruby"
date: 2008-09-10
forum: Server Platforms
---

### Post by MHDSci on 2008-09-10
Hey,
  So I need a little advice. I have a headless server running ubuntu 5.10 I believe, or maybe 6.06. I also have been working in Ruby on rails, and had a webrick server I wanted to come up every-time as soon as the server boots. (We've been having a lot of power outages etc. ) 
  I wrote up a small script that works from the command line, and added it to inet.d with 
update-rc.d SCRIPT start 30 S . 
  Rebooted, and the server came up (yay!) however I realize the server keeps spitting out information and doesn't ever 'end' ... so the boot process is stuck at that point. It never loaded SSH, mysql etc. How can I regain control of my computer? even if I add a monitor to it, I'm not positive how to go about creating a script that will start my ruby server, without hanging the process. 
   Any suggestions would be appreciated.

---

### Post by LRKSFAG on 2008-09-11
[size=2]&#20804;&#24351;&#20320;&#20241;&#24687;&#19968;&#20250;&#21543;&#65292;&#25105;&#39030;&#20250;&#20799;[/size][NSK&#36724;&#25215;](http://www.nsk2008.cn/see/191.html)[TIMKEN&#36724;&#25215;](http://www.nsk2008.cn/see/194.html)[SKF&#36724;&#25215;](http://www.nsk2008.cn/see/192.html)[FAG&#36724;&#25215;](http://www.nsk2008.cn/see/190.html)

---

