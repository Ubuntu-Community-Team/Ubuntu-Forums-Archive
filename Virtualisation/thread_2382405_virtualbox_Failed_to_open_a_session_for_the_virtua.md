---
title: "virtualbox Failed to open a session for the virtual machine"
date: 2018-01-12
forum: Virtualisation
---

### Post by dragan4 on 2018-01-12
For three days I've got problems with the VirtualBox and I can not find a solution.


For more than a year I have been working on a VirtualBox on Ubuntu host and a guest of windows7 It worked great, but of a few days ago can not run windows I get this message Failed to open a session for the virtual machine 

[https://ibb.co/jAGrNR](https://ibb.co/jAGrNR) 

Please, your help means a lot to me

---

### Post by DuckHook on 2018-01-13
Please tell us what VB version you are using.

These threads may be useful to you: [https://ubuntuforums.org/showthread.php?t=2382314](https://ubuntuforums.org/showthread.php?t=2382314)
[https://ubuntuforums.org/showthread.php?t=2382282](https://ubuntuforums.org/showthread.php?t=2382282)

The latest kernel upgrade has caused problems for some VB users. In my case, installing VB 5.2 solved them. Your mileage may vary.

---

### Post by dragan4 on 2018-01-14
thanks a lot on the answer
I installed version 5.2
but it does not seem to work for me now, I get this error  Failed to open virtual machine located in /media/dragan/5f066939-a6e8-457a-860e-2981b5c851be7/dragan/VirtualBox VMs/win 7/win 7.vbox.

[IMG]https://ibb.co/jEx2z6[/IMG]

[https://ibb.co/jEx2z6](https://ibb.co/jEx2z6)

---

### Post by DuckHook on 2018-01-14
[LIST=1]
[*]Make sure you have a backup of all your VMs. In fact, of all your important data.
[*]Try using an older kernel.
[*]If that doesn't work, try this: [https://forums.virtualbox.org/viewtopic.php?f=8&t=59357](https://forums.virtualbox.org/viewtopic.php?f=8&t=59357)
[*]You may wish to post on the VB forums. They specialize in VB recovery. Explain your whole situation with lots of detail including the host OS, guest OS, details of kernel upgrade on host, VB version, etc. Always, the more info the better.
[/LIST]

---

### Post by dragan4 on 2018-01-14
thanks very much 

failed to return on the older version karnel

---

### Post by DuckHook on 2018-01-14
Have you tried the measures in Step #3?

---

### Post by dragan4 on 2018-01-15
Yes, I did this but got this error now :(

---

### Post by dragan4 on 2018-01-15
I managed to solve this problem ... the problem seemed to be in disagreement with the version dmks 

This helped me [https://askubuntu.com/questions/900794/virtualbox-rtr3initex-failed-with-rc-1912-rc-1912](https://askubuntu.com/questions/900794/virtualbox-rtr3initex-failed-with-rc-1912-rc-1912)

thanks very much [COLOR=#000000]DuckHook for your help[/COLOR]

---

### Post by DuckHook on 2018-01-15
My input was of very limited value, but I'm very glad you solved it.

Good Luck and Happy Ubuntu-ing!

---

